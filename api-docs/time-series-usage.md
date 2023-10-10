---
title: Time Series API - Usage guide
category: 6492ae1582247100472ad7c5
---
# Instant Query Examples
## Example 1: Fetching the Metric at a Specific Timestamp

Suppose we want to retrieve the "cumulative operating hours" metric at 2023-05-01 00:00:00 UTC. We can make the following API request:

```curl
curl -G 'https://iris.trackunit.com/api/time-series/v1/assets/00000000-0000-0000-0000-000001569258/prometheus/api/v1/query' \
--data-urlencode 'query=machine_insight_cumulative_operating_hours' \
--data-urlencode 'time=2023-05-01T00:00:00.000Z' -H 'Authorization: Bearer ACCESS_TOKEN'
```

If there is no data ingested for the specified timestamp and a default 5-minute look-behind window, the API response will indicate an empty result.

```json
{
    "status": "success",
    "isPartial": false,
    "data": {
        "resultType": "vector",
        "result": []
    },
    "stats": {
        "seriesFetched": "1"
    }
}
```

## Example 2: Expanding the Look-Behind Window

To retrieve data within a larger time range, we can expand the look-behind window. In this case, we extend it to one day (24 hours) by adding [1d] to the query expression. The following API request demonstrates this:

```curl
curl -G 'https://iris.trackunit.com/api/time-series/v1/assets/00000000-0000-0000-0000-000001569258/prometheus/api/v1/query' \
--data-urlencode 'query=machine_insight_cumulative_operating_hours[1d]' \
--data-urlencode 'time=2023-05-01T00:00:00.000Z' -H 'Authorization: Bearer ACCESS_TOKEN'
```

Now, the API response will include all the ingested "cumulative operating hours" metrics from the last day of April 2023.

```json JSON
{
    "status": "success",
    "data": {
        "resultType": "matrix",
        "result": [
            {
                "metric": {
                    "__name__": "machine_insight_cumulative_operating_hours",
                    "asset_id": "00000000-0000-0000-0000-000001569258",
                    "version": "1"
                },
                "values": [
                    [
                        1682812837,
                        "648.6666666666"
                    ],
                    [
                        1682866779,
                        "648.9333333333"
                    ],
                    [
                        1682866788,
                        "648.95"
                    ],
                    [
                        1682898622,
                        "649.3333333333"
                    ]
                ]
            }
        ]
    }
}
```

## Example 3: Aggregating Metrics

Suppose we are interested in calculating the increase in cumulative operating hours over the last day of April 2023. We can utilize the `increase()` function in the query expression. The following API request demonstrates this:

```curl
curl -G 'https://iris.trackunit.com/api/time-series/v1/assets/00000000-0000-0000-0000-000001569258/prometheus/api/v1/query' \
--data-urlencode 'query=increase(machine_insight_cumulative_operating_hours[1d])' \
--data-urlencode 'time=2023-05-01T00:00:00.000Z' -H 'Authorization: Bearer ACCESS_TOKEN'
```

The API response will provide the increase in operating hours for the given day.

```json
{
    "status": "success",
    "isPartial": false,
    "data": {
        "resultType": "vector",
        "result": [
            {
                "metric": {
                    "asset_id": "00000000-0000-0000-0000-000001569258",
                    "version": "1"
                },
                "value": [
                    1682899200,
                    "0.666666666699939"
                ]
            }
        ]
    },
    "stats": {
        "seriesFetched": "1"
    }
}
```

## Example 4: Retrieving the Latest Metric Value

If you are only interested in the latest value at the specified timestamp (2023-05-01 00:00:00 UTC), you can use the `last_over_time()` function in the query expression. The following API request demonstrates this:

```curl
curl -L -g -G 'https://iris.trackunit.com/api/time-series/v1/assets/00000000-0000-0000-0000-000001569258/prometheus/api/v1/query' \
--data-urlencode 'query=last_over_time(machine_insight_cumulative_operating_hours[1d])' \
--data-urlencode 'time=2023-05-01T00:00:00.000Z' -H 'Authorization: Bearer ACCESS_TOKEN'
```

The API response will provide the latest operating hours value for the given day.

```json
{
    "status": "success",
    "isPartial": false,
    "data": {
        "resultType": "vector",
        "result": [
            {
                "metric": {
                    "__name__": "machine_insight_cumulative_operating_hours",
                    "asset_id": "00000000-0000-0000-0000-000001569258",
                    "version": "1"
                },
                "value": [
                    1682899200,
                    "649.3333333333"
                ]
            }
        ]
    },
    "stats": {
        "seriesFetched": "1"
    }
}
```

#Range Query Examples
## Example 1: Fetching the Metric at a Specific Time Range

Suppose we want to retrieve the daily "cumulative operating hours" metrics for May 2023. We can make the following API request:

```curl
curl -G 'https://iris.trackunit.com/api/time-series/v1/assets/00000000-0000-0000-0000-000001569258/prometheus/api/v1/query_range' \
--data-urlencode 'query=machine_insight_cumulative_operating_hours' \
--data-urlencode 'start=2023-05-01T00:00:00.000Z' \
--data-urlencode 'end=2023-06-01T00:00:00.000Z' \
--data-urlencode 'step=1d' \
-H 'Authorization: Bearer ACCESS_TOKEN'
```

The range query will follow the given time range and step interval regardless of whether they match the time of ingest metrics. Therefore, the API response will provide the operating hours at the start of each day.

```json
{
    "status": "success",
    "isPartial": false,
    "data": {
        "resultType": "matrix",
        "result": [
            {
                "metric": {
                    "__name__": "machine_insight_cumulative_operating_hours",
                    "asset_id": "00000000-0000-0000-0000-000001569258",
                    "version": "1"
                },
                "values": [
                    [
                        1682899200,
                        "649.3333333333"
                    ],
                    [
                        1682985600,
                        "651.1166666666"
                    ],
                    [
                        1683072000,
                        "652.5833333333"
                    ],
                    [
                        1683158400,
                        "654.55"
                    ],
                    [
                        1683244800,
                        "655.3"
                    ],
                    [
                        1683331200,
                        "657.2666666666"
                    ],
                    [
                        1683417600,
                        "658.0333333333"
                    ],
                    [
                        1683504000,
                        "658.5833333333"
                    ],
                    [
                        1683590400,
                        "660.0333333333"
                    ],
                    [
                        1683676800,
                        "660.75"
                    ],
                    [
                        1683763200,
                        "662.4333333333"
                    ],
                    [
                        1683849600,
                        "663.5666666666"
                    ],
                    [
                        1683936000,
                        "665.5333333333"
                    ],
                    [
                        1684022400,
                        "668.2166666666"
                    ],
                    [
                        1684108800,
                        "668.6166666666"
                    ],
                    [
                        1684195200,
                        "670.2166666666"
                    ],
                    [
                        1684281600,
                        "671.9"
                    ],
                    [
                        1684368000,
                        "672.6166666666"
                    ],
                    [
                        1684454400,
                        "673.1833333333"
                    ],
                    [
                        1684540800,
                        "677.7833333333"
                    ],
                    [
                        1684627200,
                        "677.7833333333"
                    ],
                    [
                        1684713600,
                        "682.9666666666"
                    ],
                    [
                        1684800000,
                        "685.3833333333"
                    ],
                    [
                        1684886400,
                        "688.0833333333"
                    ],
                    [
                        1684972800,
                        "688.9333333333"
                    ],
                    [
                        1685059200,
                        "690.7166666666"
                    ],
                    [
                        1685145600,
                        "691.3833333333"
                    ],
                    [
                        1685232000,
                        "691.8333333333"
                    ],
                    [
                        1685318400,
                        "693.6166666666"
                    ],
                    [
                        1685404800,
                        "695.6166666666"
                    ],
                    [
                        1685491200,
                        "697.4333333333"
                    ],
                    [
                        1685577600,
                        "697.8833333333"
                    ]
                ]
            }
        ]
    },
    "stats": {
        "seriesFetched": "1"
    }
}
```

## Example 2: Calculating The Daily Increase In Engine Hours

Suppose we are interested in calculating the daily increase in operating hours (total operating hours) for May 2023. To achieve this, we can utilize the `increase()` function in combination with expanding the look-behind window. In this case, we extend the window to one day (24 hours) by adding [1d] in the query expression. Since we added the window looking back one day, we need to start our time range from the 2nd of May; otherwise, the first value would represent the increase for the last day of April. The following API request demonstrates this:

```curl
curl -G 'https://iris.trackunit.com/api/time-series/v1/assets/00000000-0000-0000-0000-000001569258/prometheus/api/v1/query_range' \
--data-urlencode 'query=increase(machine_insight_cumulative_operating_hours[1d])' \
--data-urlencode 'start=2023-05-02T00:00:00.000Z' \
--data-urlencode 'end=2023-06-01T00:00:00.000Z' \
--data-urlencode 'step=1d' \
-H 'Authorization: Bearer ACCESS_TOKEN'
```

The API response will provide the daily increase in operating hours for May 2023.

```json
{
    "status": "success",
    "isPartial": false,
    "data": {
        "resultType": "matrix",
        "result": [
            {
                "metric": {
                    "asset_id": "00000000-0000-0000-0000-000001569258",
                    "version": "1"
                },
                "values": [
                    [
                        1682985600,
                        "1.7833333333001065"
                    ],
                    [
                        1683072000,
                        "1.4666666666998935"
                    ],
                    [
                        1683158400,
                        "1.9666666667000072"
                    ],
                    [
                        1683244800,
                        "0.75"
                    ],
                    [
                        1683331200,
                        "1.9666666666000765"
                    ],
                    [
                        1683417600,
                        "0.7666666666999618"
                    ],
                    [
                        1683504000,
                        "0.5499999999999545"
                    ],
                    [
                        1683590400,
                        "1.4500000000000455"
                    ],
                    [
                        1683676800,
                        "0.7166666667000072"
                    ],
                    [
                        1683763200,
                        "1.68333333329997"
                    ],
                    [
                        1683849600,
                        "1.1333333333000155"
                    ],
                    [
                        1683936000,
                        "1.9666666667000072"
                    ],
                    [
                        1684022400,
                        "2.68333333329997"
                    ],
                    [
                        1684108800,
                        "0.40000000000009095"
                    ],
                    [
                        1684195200,
                        "1.599999999999909"
                    ],
                    [
                        1684281600,
                        "1.6833333334000145"
                    ],
                    [
                        1684368000,
                        "0.7166666666000765"
                    ],
                    [
                        1684454400,
                        "0.5666666666999163"
                    ],
                    [
                        1684540800,
                        "4.600000000000023"
                    ],
                    [
                        1684627200,
                        "0"
                    ],
                    [
                        1684713600,
                        "5.18333333329997"
                    ],
                    [
                        1684800000,
                        "2.4166666667000527"
                    ],
                    [
                        1684886400,
                        "2.699999999999932"
                    ],
                    [
                        1684972800,
                        "0.8500000000000227"
                    ],
                    [
                        1685059200,
                        "1.7833333332999928"
                    ],
                    [
                        1685145600,
                        "0.6666666667000527"
                    ],
                    [
                        1685232000,
                        "0.4499999999999318"
                    ],
                    [
                        1685318400,
                        "1.7833333333001065"
                    ],
                    [
                        1685404800,
                        "2"
                    ],
                    [
                        1685491200,
                        "1.8166666666999163"
                    ],
                    [
                        1685577600,
                        "0.4500000000000455"
                    ]
                ]
            }
        ]
    },
    "stats": {
        "seriesFetched": "0"
    }
}
```

By analyzing the response and comparing it to the response of Example 1, we can verify that the response is returning the daily increase. For example, on the 1st of May, the machine had operated 649.333 hours at the beginning of the day and 651.117 hours at the end, resulting in an increase of 1.78 hours, which matches our "increase" response.

## Example 3: Combining metrics to find days with high fuel consumption and engine idle hours

In this example, we are interested in finding the daily fuel consumption higher than thirteen and more than four engine idle hours.

First, we find the daily fuel consumption for days with a higher consumption than thirteen using the greater than (`>`) operator, which works as a filter on the metrics.

```curl
curl -G 'https://iris.trackunit.com/api/time-series/v1/assets/00000000-0000-0000-0000-000001569258/prometheus/api/v1/query_range' \
--data-urlencode 'query=increase(machine_insight_engine_total_fuel_used[1d]) > 13' \
--data-urlencode 'start=2023-05-02T00:00:00.000Z' \
--data-urlencode 'end=2023-06-01T00:00:00.000Z' \
--data-urlencode 'step=1d' \
-H 'Authorization: Bearer ACCESS_TOKEN'
```

The API response will return only days with a fuel consumption higher than thirteen.

```json
{
    "status": "success",
    "isPartial": false,
    "data": {
        "resultType": "matrix",
        "result": [
            {
                "metric": {
                    "asset_id": "00000000-0000-0000-0000-000000135346",
                    "version": "1"
                },
                "values": [
                    [
                        1678320000,
                        "14"
                    ],
                    [
                        1679443200,
                        "22"
                    ],
                    [
                        1679529600,
                        "16"
                    ],
                    [
                        1680134400,
                        "16"
                    ],
                    [
                        1680220800,
                        "17"
                    ]
                ]
            }
        ]
    },
    "stats": {
        "seriesFetched": "1"
    }
}
```

Next, we find days with more than four engine idle hours.

```curl
curl -G 'https://iris.trackunit.com/api/time-series/v1/assets/00000000-0000-0000-0000-000001569258/prometheus/api/v1/query_range' \
--data-urlencode 'query=increase(machine_insight_engine_total_idle_hours[1d]) > 4' \
--data-urlencode 'start=2023-05-02T00:00:00.000Z' \
--data-urlencode 'end=2023-06-01T00:00:00.000Z' \
--data-urlencode 'step=1d' \
-H 'Authorization: Bearer ACCESS_TOKEN'
```

The API response will return only days with more than four engine idle hours.

```json
{
    "status": "success",
    "isPartial": false,
    "data": {
        "resultType": "matrix",
        "result": [
            {
                "metric": {
                    "asset_id": "00000000-0000-0000-0000-000000135346",
                    "version": "1"
                },
                "values": [
                    [
                        1678233600,
                        "4.350000000000364"
                    ],
                    [
                        1678665600,
                        "4.149999999999636"
                    ],
                    [
                        1679443200,
                        "4.350000000000364"
                    ],
                    [
                        1679616000,
                        "4.149999999999636"
                    ],
                    [
                        1679875200,
                        "4.200000000000728"
                    ],
                    [
                        1680134400,
                        "4.299999999999272"
                    ]
                ]
            }
        ]
    },
    "stats": {
        "seriesFetched": "0"
    }
}
```

At this point, we have enough data to determine which days meet the criteria. However, we can also combine the two query expressions into one and have the API do the heavy lifting. We are interested in the fuel consumption but only for days with high engine idle hours. Therefore, we use the AND operator, which combines the two filters into one on the left-side time series.

```curl
curl -G 'https://iris.trackunit.com/api/time-series/v1/assets/00000000-0000-0000-0000-000001569258/prometheus/api/v1/query_range' \
--data-urlencode 'query=(increase(machine_insight_engine_total_fuel_used[1d]) > 13) and (increase(machine_insight_engine_total_idle_hours[1d]) > 4)' \
--data-urlencode 'start=2023-05-02T00:00:00.000Z' \
--data-urlencode 'end=2023-06-01T00:00:00.000Z' \
--data-urlencode 'step=1d' \
-H 'Authorization: Bearer ACCESS_TOKEN'
```

The API response will return fuel consumption for days with fuel consumption higher than thirteen and engine idle hours higher than four.

```json
{
    "status": "success",
    "isPartial": false,
    "data": {
        "resultType": "matrix",
        "result": [
            {
                "metric": {
                    "asset_id": "00000000-0000-0000-0000-000000135346",
                    "version": "1"
                },
                "values": [
                    [
                        1679443200,
                        "22"
                    ],
                    [
                        1680134400,
                        "16"
                    ]
                ]
            }
        ]
    },
    "stats": {
        "seriesFetched": "1"
    }
}
```
