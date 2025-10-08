---
title: Pagination in GraphQL
category:
  uri: "/branches/1.0/categories/reference/GRAPHQL API"
---

Trackunit's GraphQL API supports [relay-style cursor-based pagination](https://relay.dev/graphql/connections.htm), which is a technique commonly used in GraphQL APIs to efficiently paginate through large datasets. This type of pagination offers improved performance and reliability for applications dealing with large datasets, making it a valuable choice for GraphQL implementations.

To implement it, you first need to define a unique cursor for each item in your dataset. This cursor typically combines information about the item's position and other attributes, ensuring its uniqueness. You start with an initial query, requesting a set number of items and receiving a list of edges, each containing a cursor and the associated node. To retrieve the next page, you then use the cursor of the last item in the current page as a starting point for the next query. This approach eliminates the need for costly offset-based pagination and provides a more predictable and scalable way to paginate through data.

**For best performance we recommend to use between 50 and 100 records per page.**
