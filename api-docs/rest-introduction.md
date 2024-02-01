---
title: REST APIs - Introduction
category: 6295ae369ba4b1001464c9e5
---

Part of the Trackunit Iris APIs are based and organised around the [RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer) paradigm. These REST APIs have resource oriented URLs, that use the HTTP method conventions to expose our domain capabilities. We use standardised HTTP response codes to indicate errors, and JSON as our data-interchange format for both requests and responses.

## Conventions

### Base URL

Trackunits base URL for all APIs is `<https://iris.trackunit.com`>

### JSON conventions

- Trackunit uses JSON for both request and response data-interchange format. 
- All field names are in camelCase
- A response body will always return a JSON object as the top level element.

### HTTP request method conventions

HTTP (Hypertext Transfer Protocol) defines a set of request methods, each serving a specific purpose in web communication. The most common methods include GET, POST, PUT, DELETE, and others. 
- The GET method is used for retrieving data from a specified resource, and it appends parameters to the URL.
- POST, on the other hand, is employed for submitting data to be processed to a specified resource, often used for form submissions.
- PATCH is a method that supports making full or partial updates to a resource.
- DELETE is employed to request the removal of a specified resource.

These methods help standardize communication between clients and servers, allowing for a well-defined and structured interaction in web applications.

## REST APIs vs. GraphQL API

Our REST APIs are designed to only expose a single domain within the Trackunit data model. If you need data from different parts of the Trackunit data model, consider using the public GraphQL API instead of the individual REST APIs. [Read more](https://developers.trackunit.com/reference/graphql-api-vs-rest)
