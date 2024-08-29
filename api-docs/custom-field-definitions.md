---
title: Definitions
category: 628c96a84164f50225dd1f14
---

> 📘 Subscription requirement
> 
> IrisX is required to create and change custom field definitions. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)


> ➡️ [OpenAPI Specification for the Custom Fields API domain](https://developers.trackunit.com/openapi/628c96a84164f50225dd1f13)
> 
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/628c96a84164f50225dd1f13).

# Create a field definition

To define a custom field, you first need to add a definition using the API.

| Field type   | Description                                                                                |
| ------------ | ------------------------------------------------------------------------------------------ |
| Boolean      | Boolean value that can store true or false.                                                |
| Date         | Date field.                                                                                |
| Dropdown     | A predefined list of options. Supports both single and multi selects.                      |
| E-mail       | Email field. Will be rendered with a mailto link in the UI.                                |
| Monetary     | Monetary values with currency in ISO 4217 standard.                                        |
| Number       | Numeric values. Supports unit conversion between metric and US customary units.            |
| Phone number | Phone number. Validates the format according to country specific rules, but does not validate wheter the phone number actually exists. |
| Text string  | Free text field. Supports limiting length.                                                 |
| Web address  | Web address. Will be shown as a link to open a new window in the UI.                       |

It is possible to control if new fields should show up in appropriate places in the user interface or be an API only field using the `uiVisible` / `uiEditable` fields.

Once a definition has been created values can be set using the [values API](custom-field-values).

# Field definition ownership

Custom field definitions can be owned by one of these:

- **Customer account** - Customer defined fields will be owned by the customer account and require admin permission in that account to change.
- **IrisX App** - An app may contribute field definitions when it is installed
- **Trackunit** - Trackunit defines a number of standard fields to aid interoperability.

When creating a definition using this API it will always be owned by your customer account. It is however possible to retrieve all 3 types using the API.

## Data sharing

Regardless of who owns the definition of a field the values in a field may be shared between accounts.

| Scope type                | Description | 
|---------------------------|-------------------------------|
| ACCOUNT                   | Values with account scope will be shared within a single account |
| ACCOUNT_WRITE_GLOBAL_READ | Updating values will be possible within a single account and visible to all accounts (read) with access to the entity. |
| GLOBAL                    | Values with global scope will be shared between all accounts with access to the entity |

So that means that if you create a new field definition for an Asset and mark it as scope `ACCOUNT_WRITE_GLOBAL_READ` then you can add the field to an asset and you are allowed to update the value but in case you share it to other accounts they will only be able to see the value but not change it.

On the other hand if you select the `ACCOUNT` scope only users within your account will be able to see the values in that field.
