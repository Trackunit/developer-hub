---
title: Custom Fields API - Introduction
category: 628c96a84164f50225dd1f14
---

With our Custom Fields offering, Trackunit Iris can host all the data that you need. Custom Fields will enable you to capture and organize additional metadata that holds significant contextual value, thereby facilitating more robust data categorization and retrieval processes for you and your end-customers.

# Additional standard fields for commom metadata
Trackunit provides a number of standard fields for common metadata, that can be used by all customers to extend the available data model.

| Field name | Description | Type (UoM) | Key | Applies to |
| -------- | ------- |-------- | ------- | ------- |
| Engine manufacturer | Manufacturer of the engine | dropdown, single-select | engineManufacturer | asset |
| Engine model | Model of the engine | text | engineModel | asset |
| Engine serial number | Serial number of the engine | text | engineSerialNumber | asset |
| Engine Fuel Type | The fuel type the main combustion engine consumes. | dropdown, single-select (Diesel, Petrol, CNG, LPG, HVO100, Hydrogen, Bio-diesel) | engineFuelType | asset |
| Fuel Tank Capacity (Total) | The total fuel capacity, summed over all tanks. | number (L / US Liquid Gallon) | fuelTankCapacityTotal | asset |
| Input Voltage AC | The input voltage of an alternating current input, could either be to operate directly or to charge a battery. | number (V) | inputVoltageAC | asset |
| Battery System Rated Capacity | Total rated capacity summed (only if batteries in parallel) over all traction batteries, in ampere-hours. | number (Ah) | batterySystemRatedCapacity | asset |
| Battery System Rated Voltage | The rated voltage of the traction battery. | number (V) | batterySystemRatedVoltage | asset |
| Battery System Rated Power Capacity | Total rated energy capacity summed over all traction batteries, in kilo-watt-hours | number (kWh) | batterySystemRatedPowerCapacity | asset |
| Engine Power Electric | Power output of the electric motor in kilo-Watts | number (kW) | enginePowerElectric | asset |
| Engine Power Combustion | Power output of the combustion motor in kilo-Watts | number (kW) | enginePowerCombustion | asset |
| Pending telematics devices | Asset is marked for installment of telematics devices. | boolean | pendingTelematicsDevices | asset |
| Warranty end date | Date the current warranty of the machine expires. | date | warrantyEndDate | asset |
| OEM licensed | Is the machine OEM licensed? | boolean | oem-licensed | asset |
| License Plate | Assigned by a governmental authority for identification and registration purposes. | text | licensePlate | asset |
| OEM Subscription End Date | Date the asset owner's telematics subscription with the OEM expires. | date | oemSubscriptionEndDate | asset |
| OEM Subscription Start Date | Start date of the asset owner's telematics subscription with the OEM. | date | oemSubscriptionStartDate | asset |
| QR Codes | List of QR codes' data attached to the asset for identification purposes. | text | qrCodeIdentifiers | asset |
| RFID tags | List of RFID tag IDs attached to the asset. | text | rfidTags | asset |
| OEM Subscription Type | Used for internal purposes to identify the type of OEM subscription. Not visible in the UI. | text | oemSubscriptionType | asset |
| Billing Reference | Used for Trackunit billing purposes to set the billing reference used for invoices. | text | billingReference | asset |
| Purchase Date | Date the asset was purchased. | date | purchaseDate | asset |

## How to set values on standard fields

1. Use the [Custom Fields Values API](/reference/custom-fields-get-values) to get all available fields. Specify the `entityId` for your query, which is an assetId for any fields listed above.
2. Use the `Create`, `Update` or `Delete value` endpoints for any futher operations on the available fields.

# Define your own custom fields

Custom fields provide a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. Currently we support **extending the data model of assets, accounts, groups, sites, customers and rental contracts with new fields**.

> 📘 Subscription requirement
> 
> IrisX is required to create and change custom field definitions. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)


## Get started with creating custom fields

1. To define a custom field, you first need to [add a definition using the API.](/reference/custom-field-definitions)
2. Use the [Custom Fields Values API](/reference/custom-field-values) to set values on your defined custom fields. Specify the `entityId` for your query. Depending on which domain type you are interested in, this can be an assetId, accountId, groupId, siteId, customerId or rentalContractId.

## Changing custom field definitions

When changing custom field definitions, you need to follow the following general rules and type-specific rules:

### General rules
-   You cannot change a Custom Field Definition `type` after creation (e.g., changing a string field to a number field).
-   The Definition `key` (if specified) must be unique (within your account).

### Type rules
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
