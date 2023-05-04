---
title: GraphQL API Documentation
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

## Introduction
To create integrations and retrieve data, use the GraphQL API.
It offers more flexible queries than the TrackUnit REST API and only retrieves the data needed.
With GraphQL, you construct queries and mutations to fetch or modify data.
Unlike REST APIs, which use multiple endpoints, GraphQL uses a single endpoint to handle all requests.
If you haven't worked with GraphQL before, learn how to by following [the official GraphQL documentation](https://graphql.org/learn/).

The next step is to go through our guide on how to interact with the GraphQL API using the SDK: 
- [Calling Trackunit GraphQL API using the Iris App SDK](https://developers.trackunit.com/docs/graphql-api)

If you want to query the API without using the SDK, you have to fetch your authentication token first:
- [Obtain a token outside an Iris App](https://developers.trackunit.com/reference/access-token)

 The GraphQL explorer is an interactive way to familiarize yourself with the available data models:
- [GraphQL Explorer and Query builder](./graphql-explorer)

Click below to download the public schema if you need it:
- [Public schema](https://apps.iris.trackunit.com/graphql-public-viewer/schema.gql)


> 📘 Nice to know
>
> The most important datatypes are `assets` and `sites` as most other datatypes are child properties on these main ones.
Some fields are in a preview state and may change without notice.
To indicate you accept these terms pass the HTTP header `TU-PREVIEW:<codeword>` with your query requests.
The codeword differs for each preview field and you can find it by looking in the GQL schema (or explorer) above.