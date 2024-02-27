---
title: Custom Fields API - Introduction
category: 628c96a84164f50225dd1f14
---

Adding relevant information beyond standard metadata like brand and model is important to help catalogue your assets. With our Custom Fields offering, Trackunit Iris can host all the data that you need. Custom Fields will enable you to capture and organize additional metadata that holds significant contextual value, thereby facilitating more robust data categorization and retrieval processes for you and your end-customers.

Custom fields provide a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. Currently we support **extending the data model of assets, accounts, groups and sites with new fields**. Apart from defining your own custom fields we also provide a number of standard fields for common metadata.

> 📘 Subscription requirement
> 
> The Custom Fields API is only available to customers on the **Evolve & Expand** or the **Lift & Leap** subscription packages.

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
