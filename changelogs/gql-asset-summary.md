---
title: GraphQL Asset Summary
type: added
---

Released asset summaries in the GraphQL API.

The new `assetSummary` field supports obtaining unique counts of commonly used asset fields like brand, model, criticality, types, etc.
It accepts the same `AssetFiltersInput` as the `assets` search field, so they can easily be combined if needed.

> ➕ GQL: `Query.assetSummary`

[See all relevant GQL documentation](https://developers.trackunit.com/reference/graphql-api-introduction)

