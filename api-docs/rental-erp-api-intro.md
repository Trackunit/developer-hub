---
title: Rental API - Introduction
category:
  uri: /branches/1.0/categories/reference/Rental API
---

The Rental API is designed to facilitate seamless integration between the IrisX platform and any Enterprise Resource Planning (ERP) system. Building an ERP integration enables your organizations to streamline data flow, enhance operational efficiency, and ensure real-time access to critical business information. Specifically use this API for data synchronization, so that data between IrisX and ERP systems gets automatically synchronized to maintain up-to-date information across platforms.

> 📘 IrisX Subscription needed
>
> The Rental ERP API is only available to customers on IrisX. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)

## Concepts

The ERP integrations are built on the following concepts

- **Asset** is a trackable piece of equipment e.g. a machine or an accessory.
- **Contract item** is an entry in a **contract** that contains information about when an asset is rented out to a customer.
- **Contract** is linked to a **customer** and therefore it connects an asset to a customer.
- **Customer** is the customer of the business that can rent (and therefore get access to) an asset (see the [Customer API](https://developers.trackunit.com/reference/customers-api-intro)).

> 💡 Learn more in our [ERP Integration Guide](https://developers.trackunit.com/docs/custom-erp-integration-guide)
>
> Get a detailed overview of the Trackunit Rental Data Model in our guide and plan your implementation.

![Trackunit Rental Data Model](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/integrations-connectors/erp-rental-data-model.png)

> ➡️ [OpenAPI Specification for the Rental API domain](https://developers.trackunit.com/openapi/rental-api.json)
>
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/rental-api.json).

## Extending the Data Model

Custom fields provide a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. Currently we support **extending the data model of assets, accounts, groups, sites, customers and rental contracts with new fields**.
Learn more in the [Custom Fields API -Introduction](https://developers.trackunit.com/reference/custom-field-intro#define-your-own-custom-fields).

## Constraints

- Only assets owned by the account can can be updated with data from the ERP system.

- **externalReference** represents an identifier from the ERP system and has to be unique.
