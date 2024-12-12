---
title: Values
category: 628c96a84164f50225dd1f14
---

> ➡️ [OpenAPI Specification for the Custom Fields API domain](https://developers.trackunit.com/openapi/628c96a84164f50225dd1f13)
> 
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/628c96a84164f50225dd1f13).

# Use Cases

## Set values on additional standard fields

Trackunit provides a number a number of standard fields for common metadata, that can be used by all customers to extend the available data model. These fields can exists across different domains of Trackunit's data model and currently can extend assets, accounts, groups or sites.

1. Use the [Custom Fields Values API](/reference/custom-fields-get-values) to get all available fields.
- Specify the `entityId` for your query. Depending on which domain type you are interested in, this can be an assetId, accountId, groupId or siteId.
- Specify which System Of Measurement you would like to use (SI or US customary)

2. Use the `Create`, `Update` or `Delete value` endpoints for any futher operations on the available fields.

# Set values on your own custom fields

Custom fields provide a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. Currently we support **extending the data model of assets, accounts, groups and sites with new fields**.

> 📘 Subscription requirement
> 
> IrisX is required to create and change custom field definitions. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)

Use the custom field values API to set values on fields defined using the [custom fields definitions API](/reference/custom-field-definitions).

Before calling this API a custom field should be defined using the definitions API. Once a field is defined you will need to create a value on an entity.
