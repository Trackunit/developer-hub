---
title: Changing Custom Field Definitions
category: 61fcd8e1a448f5004215317c
parentDocSlug: save-data-from-your-app
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.


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
