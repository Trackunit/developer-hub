---
title: Customer API - Introduction
category: 65c1ea0e0bf60400104f7c68
---
The Trackunit Customer API is a REST API that enables customers of Trackunit to create & manage information about their own customers inside the Trackunit system.

> 📘 Also access data connected to Customer(s) via the GraphQL API
> 
> Via the Public GraphQL API, you can utilize query capabilities to fetch data connected to customer(s) and other domains which would be multiple separate calls in the REST APIs. Additionally you can perform mutations to modify data associated with customer(s). Explore the GraphQL schema through our [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/).

The Customer API is designed to facilitate the seamless management of customer data within the Trackunit ecosystem. This API empowers developers to interact with customer information, including details about customers, their associated contacts and asset assignments.

Customer in this context, is defined as the customer of Trackunit's customer, which opens up another dimension for businesses to model not only their relationship with their own customers but also those customers contacts and asset assignments.

## Concepts

The customer API is built on the following concepts

- A customer is a registration of a business relationship with another legal entity.
- A customer contact is a registration of a way to get in contact with this entity. It is not necessarily a person, as it can also be a call center or a department.
- A customer asset is represents a relationship between the customer and the asset. Fx. an asset being rented to that customer or an asset assign to undergo service by a service provider.
