---
title: Custom Fields API - Introduction
category: 628c96a84164f50225dd1f14
---

Adding relevant information beyond standard metadata like brand and model is important to help catalogue your assets. With our Custom Fields offering, Trackunit Iris can host all the data that you need. Custom Fields will enable you to capture and organize additional metadata that holds significant contextual value, thereby facilitating more robust data categorization and retrieval processes for you and your end-customers.

# Additional standard fields for commom metadata
Trackunit provides a number a number of standard fields for common metadata, that can be used by all customers to extend the available data model.

| Field name | Description | Type (UoM) | Related domain |
| -------- | ------- |-------- | ------- |
| AC Input Voltage | The input voltage of an alternating current input, could either be to operate directly or to charge a battery. | text (V) | asset |
| Engine manufaturer | The manufaturer of the engine. | dropdown, single-select | asset |
| Engine model | The model of the engine. | text | asset |
| Engine serial number | The serial number of the engine. | text | asset |
| Engine fuel type | The fuel type the main combustion engine consumes. | dropdown, single-select (Diesel, Petrol, CNG, LPG, HVO100, Hydrogen, Bio-diesel) | asset |
| Fuel tank capacity (total) | The total fuel capacity, summed over all tanks. | number (L / US Liquid Gallon) | asset |
| Rated battery voltage | The rated voltage of the traction battery. | text (V) | asset |
| Rated combustion engine power | Power output of engine in kilo-Watts | text (kW) | asset |
| Rated electric motor power | Power output of the electric motor in kilo-Watts | text (kW) | asset |
| Total rated battery capacity | Total rated capacity summed (only if batteries in parallel) over all traction batteries, in ampere-hours. | text (Ah) | asset |
| Total rated battery power capacity | Total rated energy capacity summed over all traction batteries, in kilo-watt-hours  | text (kWh) | asset |
| Warranty end date |  | date | asset |


# Define your own custom fields

Custom fields provide a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. Currently we support **extending the data model of assets, accounts, groups and sites with new fields**.

> 📘 Subscription requirement
> 
> IrisX is required to create and change custom field definitions. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)


## Get Started
Explore how to create custom fields by:
1. To define a custom field, you first need to [add a definition using the API.](/reference/custom-field-definitions)
2. Use the [Custom Fields Values API](/reference/custom-field-values) to set values on your defined custom fields.


## Changing Custom Field Definitions

When changing custom field definitions, you need to follow the following general rules and type-specific rules:

### General Rules
-   You cannot change a Custom Field Definition `type` after creation (e.g., changing a string field to a number field).
-   The Definition `key` (if specified) must be unique (within your account).

### Type Rules
Each field type has special rules:

-   **Drop-down:**
    
	-   If an option is removed from a drop-down list, you must provide a valid replacement value.
	    
	-   Any existing value that contains the deleted value will be changed to the replacement value.
	    
	-   If the replacement value is already selected, a duplicate value will not be created.
	    
	-   When changing a multi-select field to a single-select field, any value with more than one option will be cleared.
	    
	-   The existing value will be saved for retrieval in the API in the `lastIncompatibleValue` field.
    
-   **Number**
    
	-   Any existing value outside the new min/max range will be set to null.
	    
	-   The existing value will be saved for retrieval in the API in the `lastIncompatibleValue` field.
    
-   **String**
    
	-   If an existing value is longer than the new maximum length, the value will be truncated.
	    
	-   The existing value will be saved for retrieval in the API in the `lastIncompatibleValue` field.

	- Regex patterns can be changed, but be warned that existing data can become uncompliant with the new pattern.
