---
title: Custom Fields API
type: added
---

Released stable version v1 of Custom Fields API.

The Custom Fields API provides a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. In this version 1 we support extending the data model of assets, accounts, groups and sites with new fields.

Below all available endpoints:

To define a custom field, you first need to [add a definition using the API.](/reference/custom-field-definitions)

> ➕ GET: /custom-fields/v1/definitions
[Get definitions](ref:custom-fields-get-definitions)

> ➕ POST: /custom-fields/v1/definitions
[Create definition](ref:custom-fields-create-definition)

> ➕ PATCH: /custom-fields/v1/definitions/{definitionId}
[Update definition](ref:custom-fields-patch-definition)

> ➕ DELETE: /custom-fields/v1/definitions/{definitionId}
[Delete definition](ref:custom-fields-delete-definition)

Use the [Custom Fields Values API](/reference/custom-field-values) to set values on your defined custom fields

> ➕ GET: /custom-fields/v1/values
[Get values](ref:custom-fields-get-values)

> ➕ POST: /custom-fields/v1/values
[Create value](ref:custom-fields-create-value)

> ➕ PATCH: /custom-fields/v1/values/{valueId}
[Update value](ref:custom-fields-patch-value)

> ➕ DELETE: /custom-fields/v1/values/{valueId}
[Delete value](ref:custom-fields-delete-value)
