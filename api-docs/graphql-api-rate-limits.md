---
title: GraphQL Rate Limits
category: 652e3a8e279c3f001f9acdc3
---

## Query Complexity & Rate Limiting in our GraphQL API

Query complexity in GraphQL refers to the measure of computational resources required to execute a specific GraphQL query. It takes into account factors such as the depth of the query, the number of requested fields, and any potential nested or recursive structures. Query complexity is a crucial aspect for optimizing GraphQL performance and preventing resource-intensive or potentially malicious queries from overloading a server. 

By setting query complexity thresholds, Trackunit aims to establish limits on the computational load a single query can impose, helping to maintain the stability and efficiency of our GraphQL API. This concept enables us to strike a balance between offering powerful and flexible queries to clients while ensuring the server's responsiveness and resource consumption remain manageable.

The rate limiting rules of our GraphQL API are connected to the calculated complexity scores of your queries. A GraphQL query can be arbitrarily complex, therefore we parse all incoming queries, calculate their complexity scores in points and subtract those from the rate limit for your API user.

**Currently the Rate Limits for our GraphQL API are:**

- A single query is limited to 50000 complexity points.
- All queries within a 10 minute window are limited to 500000 complexity points per API user.

If the single query limit is reached we will return a GraphQL error with the `extensions.code` field set to `QUERY_COMPLEXITY_REACHED`:

```json
{
    "errors": [
        {
            "message": "The query is too complex. The estimated complexity of the query is 480011, which is greater than the maximum allowed complexity limit of 50000.",
            "extensions": {
                "code": "QUERY_COMPLEXITY_REACHED"
            }
        }
    ]
}
```

If the 10 minute rate limit is reached we will return a GraphQL error with the `extensions.code` field set to `RATE_LIMITED` and `extensions.resetIn` will indicate the number of milliseconds until the rate limit is reset and the client will be able to make a call again. We recommend clients to use `extensions.resetIn` to wait until making more calls.

```json
{
    "errors": [
        {
            "message": "The rate limit has been exceeded given the current estimated query complexity of 49011. Please wait 9 minutes, 46 seconds, 351 milliseconds before retrying.",
            "extensions": {
                "code": "RATE_LIMITED",
                "cost": 49011,
                "resetIn": 586351
            }
        }
    ]
}
```

If doing multiple calls we recommend clients to proactive query the `rateLimit` field in the graph to obtain the current status and adjust call rate accordingly:

```
query { 
    rateLimit {
        cost
        remaining
        resetIn
    }
}
```
