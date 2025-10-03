---
title: Customer API - Introduction
category:
  uri: Customer API
---
The Trackunit Customer API is a REST API that enables customers of Trackunit to create & manage information about their own customers inside the Trackunit system.

> 📘 IrisX subscription needed
>
> Both the Customer REST API and GraphQL API are only available on IrisX. Via the Public GraphQL API, IrisX customers can utilize query capabilities to fetch data connected to customer(s) and other domains which would be multiple separate calls in the REST APIs. Additionally they can perform mutations to modify data associated with customer(s). Explore the GraphQL schema through our [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/). Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview).

The Customer API is designed to facilitate the seamless management of customer data within the Trackunit ecosystem. This API empowers developers to interact with customer information, including details about customers, their associated contacts and asset assignments.

Customer in this context, is defined as the customer of Trackunit's customer, which opens up another dimension for businesses to model not only their relationship with their own customers but also those customers' contacts and asset assignments.

## Concepts

The customer API is built on the following concepts:

- A **customer** is a registration of a business relationship with another legal entity.
- A **customer contact** is a registration of a way to get in contact with this entity. It is not necessarily a person, as it can also be a call center or a department.
- A **customer asset** represents a relationship between the customer and the asset. Fx. an asset being rented to that customer or an asset assigned to undergo service by a service provider.

> ➡️ [OpenAPI Specification for the Customers API domain](https://developers.trackunit.com/openapi/customer-api.json)
>
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/customer-api.json).

## Extending the Data Model

Missing any fields needed to define your customers perfectly? Custom fields provide a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. Currently we support **extending the data model of assets, accounts, groups, sites, customers and rental contracts with new fields**. Learn more in the [Custom Fields API -Introduction](https://developers.trackunit.com/reference/custom-field-intro#define-your-own-custom-fields).
