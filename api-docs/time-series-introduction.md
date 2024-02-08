---
title: Time Series API - Introduction
category: 65097f10ed04fd0047f22d48
---
Welcome to the Time Series API documentation. This REST API enables you to retrieve time series metrics for specific assets, categorized as machine insights and advanced sensors.

Machine insights provide a comprehensive list of conformed metrics, prefixed with `machine_insight_`, including ISO 15143-3 standard insights and additional insights.

Advanced sensors capture metrics originating from various sources, often derived from CAN. Advanced sensors are not conformed and allow for capturing metrics that are uniquely defined for specific equipment. The metrics are prefixed with `advanced_sensor_`. When querying advanced sensor data, you can specify a unique sensor ID to retrieve metrics for a particular sensor mapping.

> 📘 Also access 'Time Series' data for an Asset via the GraphQL API
> 
> Via the Public GraphQL API, you can utilize query capabilities to fetch 'Time Series' data connected to an asset. Explore the GraphQL schema through our [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/). Follow the 'asset' entry point and select 'timeSeries' to perform instant queries and range queries. 

The Time Series API follows the standards of [Prometheus](https://prometheus.io/), an open-source monitoring and time series database system. By adhering to Prometheus specifications, our API ensures compatibility with Prometheus clients and tooling, facilitating integration with existing Prometheus ecosystems. E.g. [Grafana](https://prometheus.io/docs/visualization/grafana/) supports querying Prometheus, which enables you to create dashboards to visualize, alert on and understand your metrics.
 
With our query endpoints, you can leverage PromQL, the powerful and expressive Prometheus query language, to retrieve and analyze time series data. PromQL offers a range of functions and operators for complex queries and calculations. The query responses adhere to Prometheus result formats for easy consumption and compatibility.

In addition to Prometheus endpoints, we provide a metrics endpoint for retrieving metrics in their original ingested form. This gives you access to the raw time series data without aggregation or modifications. Retrieve precise values and timestamps for detailed analysis or integration with external systems.

This documentation guides you through the functionality of the Time Series API, including retrieving machine insights and advanced sensor data. It also provides resources for learning PromQL and formulating effective queries.

Explore the available endpoints and interact with the Time Series API to retrieve valuable time series metrics for analysis and monitoring purposes.


> 🚧 Alignment between the asset and telematics device counters
> 
> In certain situations, such as retrofitting a telematics device, compensating values are applied to synchronize the readings between the asset and the telematics device's odometer and run counters.
> 
> The implementation of these value adjustments is pending and therefore NOT applied. Compensating values for the affected metrics can be obtained from **Time Series API -> Metrics -> Get metric offsets**, and applied manually.
> 
> The following metrics may be affected:
> * machine_insight_cumulative_operating_hours
> * machine_insight_engine_total_idle_hours
> * machine_insight_total_vehicle_distance
> * advanced_sensor_run_1
> * advanced_sensor_run_2
> 
> Implementation updates will be communicated through developer hub.

> 📘 Subscription requirement
>
> The Time Series API is only available to customers on the **Evolve & Expand** or the **Link, Lift & Leap** subscription packages. Data retention limits follow the chosen subscription package.

## Rate Limiting

* Advanced Querying - max 100 requests per second
* Metrics - max 20 requests per second

## Series names and labels

To retrieve or analyze any time series data you specify the name of the series or label.

There are 3 main sources of the series:
1. **Machine insights** - for example: `machine_insight_cumulative_operating_hours`.  
   Their names consist of `machine_insight_` prefix followed by lowercase insight name separated with underscores (`_`). See [Data Model](data-model) for list of possible machine insights.
2. **Standard CAN inputs and outputs** - for example `advanced_sensor_input_1` or `advanced_sensor_run_1`.  
   Their names start with `advanced_sensor_` prefix followed by input number (1-10) or run number (1-6).
3. **Other sensors** originating from various sources capturing metrics that are uniquely defined for specific equipment. For example: `advanced_sensor_work_light_switch_front_left_status`.  
   If applicable, the unit of measurement can be read from `unit_of_measurement` label.  
   Some of the sensors might generate multiple series with minimum, maximum and average values. In such case the series name will contain suffix `_min`, `_max` or `_avg`.

When querying advanced sensor data, you can specify a unique sensor ID to retrieve metrics for a particular sensor mapping. For example: `{sensor_id="run_1"}` or `{sensor_id="variable_11231"}`.

Every asset has its own combination of available series and labels depending on type of the equipment and its configuration. It is not possible to list all the names in this documentation, however the API provides 3 endpoints to list [time series names](getlistoftimeseries), [label names](getlistoflabelnames) and [label values](getlistoflabelvalues) for specific asset.

## Instant Query

The instant query endpoint allows you to evaluate an instant query for a specific asset and a given point in time. You provide a PromQL query string that defines the metric or calculation you want to perform. The result of the query will be a single value or a set of values for the specified timestamp.

The response from the instant query endpoint includes the result of the query, which can be of different types such as matrix, vector, scalar, or string. The format of the result depends on the type and may include additional metadata such as labels or timestamps.

Result types:

- Matrix: A two-dimensional data structure representing multiple entries per time series data. Enables working with multiple data series simultaneously.
- Vector: A one-dimensional data structure representing a single entry per time series.
- Scalar: A single value, typically a number or boolean. Used when the query produces a single aggregated value or a specific metric attribute.
- String: Text-based information. Used for retrieving metadata, labels, or descriptive information related to a metric.

These result types allow for flexibility in representing and working with different types of data in an instant query. Choose the appropriate result type based on your specific use case to extract the desired information or perform calculations on the returned data.

[Explore the our Instant Query examples](../reference/time-series-usage#instant-query-examples)

## Range Query

The range query endpoint allows you to perform time series analysis of data within a specified time range.

Here's a breakdown of how a range query works:

1. Query Expression: You provide a PromQL (Prometheus Query Language) expression that specifies the metrics, aggregations, or transformations you want to apply to the time series data. This query expression can include metric names, labels, operators, and functions.
2. Step: The step parameter determines the resolution or interval at which data points are returned within the specified time range. It represents the time duration between consecutive data points in the query result.
3. Time Range: The range query selects all the data points or time series that fall within the specified time range. The start time and end time of the range are determined based on the time range for which the data is available in the Prometheus time series database.
4. Data Retrieval: Time Series API retrieves the data points or time series within the defined range from its time series database, considering the specified step interval.
5. Result Format: The result of the range query is returned in a matrix format. Each data point consists of a timestamp and its corresponding value. The matrix format allows for efficient representation of multiple time series data points over the specified time range.

By adjusting the step parameter, you can control the granularity or level of detail in the returned data. Smaller step values result in more fine-grained data points.

[Explore the our Range Query examples](../reference/time-series-usage#range-query-examples)

## Metrics

The metrics endpoint allows you to retrieve metrics as they were ingested. It provides a way to access historical metric data for analysis, debugging, or offline processing.

To use the metrics endpoint, you construct a request URL with parameters such as the time range and metric filters. The system retrieves the relevant metrics from its database and returns them in JSON format.

Additionally, if the `Accept-Encoding` header in your request is set to `gzip`, the response will be compressed using gzip encoding. This allows you to reduce the response time and size for efficient data transfer.

## PromQL Documentation and Tutorials

For more information on how to formulate queries using PromQL, refer to the official Prometheus documentation:

- [PromQL Basics](https://prometheus.io/docs/prometheus/latest/querying/basics/)
- [PromQL Functions](https://prometheus.io/docs/prometheus/latest/querying/functions/)
- [PromQL Operators](https://prometheus.io/docs/prometheus/latest/querying/operators/)
- [PromQL Examples](https://prometheus.io/docs/prometheus/latest/querying/examples/)

Additionally, here are some tutorials and guides to help you get started with PromQL:

- [PromQL Cheat Sheet](https://promlabs.com/promql-cheat-sheet/)
- [PromQL Training Course by Promlabs](https://training.promlabs.com/training/understanding-promql)
- [PromQL tutorial for beginners and humans](https://valyala.medium.com/promql-tutorial-for-beginners-9ab455142085)

These resources should provide you with a solid foundation for utilizing PromQL to query the Time Series API.
