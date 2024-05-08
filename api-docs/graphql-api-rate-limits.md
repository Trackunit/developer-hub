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

## Consuming GraphQL API in a rate limit safe way

If doing multiple calls we recommend clients to proactive query the `rateLimit` field in the graph to obtain the current status and adjust call rate accordingly.

Assuming we have a query that retrieves some assets after a certain cursor:

```graphql
query MyQuery($afterCursor: Cursor!) { 
    assets(first: 50, after: $afterCursor) {
        ...
    }
    rateLimit {
        cost
        remaining
        resetIn
    }
}
```

Comparing the `remaining` value to the current `cost` of the query will allow you to slow down if remaining become low and then use `resetIn` to wait until the rate limit is reset.

In code it would look something like this:

```js
while (hasNextPage) {
  const result = executeQuery(... afterCursor ...);

  // Check if we hit the rate limit
  if (result.errors?.find((error) => error.extensions.code === "RATE_LIMITED")) {
      // Rate limit exceeded. Wait for reset
      sleet(resetIn);
      continue;
  }

  // Process data

  // Get relay parameters
  hasNextPage = result.data.assets.pageInfo.hasNextPage;
  afterCursor = result.data.assets.pageInfo.endCursor;
}
```

In the above example we continue until we hit the rate limit. The rate limit is per user/API token so it could potentially break other clients. If the credentials is used for multiple queries consider stopping a bit before hitting the limit:

```js
  // Check rate limit
  remaining = result.data.rateLimit.remaining;
  resetIn = result.data.rateLimit.resetIn;
  cost = result.data.rateLimit.cost;
  if (remaining < cost * 10) {
    // Rate limit exceeded. Wait for reset
    sleep(resetIn);
  }
```

In the above example we use 10 times the cost as a safety buffer.

If you expect to always hit the rate limit it is better to simply reduce the call rate up front like this:

```js
  // Check rate limit
  remaining = result.data.rateLimit.remaining;
  resetIn = result.data.rateLimit.resetIn;
  cost = result.data.rateLimit.cost;
  maxCalls = Math.floor(remaining / cost);
  sleepBetweenCalls = Math.ceiling(resetIn / maxCalls);
  sleep(Math.min(resetIn, sleepBetweenCalls));
}
```

This will spread out the calls such that it will not break the rate limit.
