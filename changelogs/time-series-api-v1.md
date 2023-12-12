---
title: Time Series API v1
type: added
---

Released stable version v1 of Time Series API - Supercharge your data exploration with advanced querying capabilities using PromQL!

Discover the power of our new Time Series REST API, your gateway to a wealth of machine insights and advanced sensor data. Designed to empower your exploration of time series data, our new API offers seamless access to endpoints that can be queried using PromQL.

Below a list of all available endpoints:

> ➕ GET: /time-series/v1/assets/{assetId}/prometheus/api/v1/query

[Get for instant queries](ref:getquery)

> ➕ POST: /time-series/v1/assets/{assetId}/prometheus/api/v1/query

[Post for instant queries](ref:getqueryusingpost)

> ➕ GET: /time-series/v1/assets/{assetId}/prometheus/api/v1/query_range

[Get for range queries](ref:getqueryrange)

> ➕ POST: /time-series/v1/assets/{assetId}/prometheus/api/v1/query_range

[Post for range queries](ref:getqueryrangeusingpost)

> ➕ GET: /time-series/v1/assets/{assetId}/metrics

[Get metrics](ref:getmetrics)
