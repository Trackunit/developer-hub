---
title: Values
category:
  uri: Custom Fields API
---

> ➡️ [OpenAPI Specification for the Custom Fields API domain](https://developers.trackunit.com/openapi/custom-fields-api.json)
>
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/custom-fields-api.json).

# Use Cases

## Set values on additional standard fields

Trackunit provides a number a number of standard fields for common metadata, that can be used by all customers to extend the available data model.

1. Use the [Custom Fields Values API](/reference/custom-fields-get-values) to get all available fields. Specify the `entityId` for your query, which is an assetId for the current list of standard fields.

2. Use the `Create`, `Update` or `Delete value` endpoints for any futher operations on the available fields.

# Set values on your own custom fields

Custom fields provide a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. Currently we support **extending the data model of assets, accounts, groups, sites, customers and rental contracts with new fields**.

> 📘 Subscription requirement
>
> IrisX is required to create and change custom field definitions. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)

Use the custom field values API to set values on fields defined using the [custom fields definitions API](/reference/custom-field-definitions).

Before calling this API a custom field should be defined using the definitions API. Once a field is defined you will need to create a value on an entity.
