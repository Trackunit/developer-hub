---
title: REST APIs vs. GraphQL API
category: 652e3a8e279c3f001f9acdc3
---

## When to use REST APIs and when to use the GraphQL API?

> 📘 TL;DR
>
> Our REST APIs are designed to only expose a single domain within the Trackunit data model. If you need data from different parts of the Trackunit data model, consider using the public GraphQL API instead of the individual REST APIs.

REST (Representational State Transfer) APIs and GraphQL APIs are both used for building web services. 
They allow to interact with a server and retrieve or manipulate data. 
However, they have different characteristics and are better suited for different use cases. 
Here's a comparison of when to use each:

**Use REST APIs when:**

1. Simple Data Retrieval: If your application primarily involves simple data retrieval and CRUD (Create, Read, Update, Delete) operations, REST APIs can be a good choice. REST's fixed endpoints map well to these types of operations.
2. Bulk data extraction: REST's focus on caching, pagination, and parallel requests can be beneficial to extracting larger volumes of data.

**Use GraphQL APIs when:**

1. Flexible Data Retrieval: GraphQL is designed to give clients more control over the data they retrieve. Clients can request only the specific fields they need, reducing over-fetching or under-fetching of data.
2. Efficient Data Retrieval: In scenarios where bandwidth is a concern (e.g., mobile apps), GraphQL's ability to retrieve all required data in a single request can reduce the number of round-trips between the client and server.
3. Complex Relationships: When dealing with complex relationships between entities, GraphQL's nested queries and efficient data loading can simplify data fetching on the client side.
4. Avoiding Over-Fetching and Under-Fetching: GraphQL allows clients to request exactly the data they need, reducing the chances of over-fetching (retrieving more data than necessary) or under-fetching (not getting enough data).
5. Aggregating Data: GraphQL can aggregate data from multiple sources and present it as a single unified API, making it a good choice for applications that pull data from different services.

In summary, use REST APIs when simplicity and compatibility with a variety of clients are your main concerns. 
Use GraphQL APIs when you need more flexibility in data retrieval, retrieve complex data relationships, and want to optimize data fetching for e.g. app development.
