---
title: Defining a Custom Field
category: 61fcd8e1a448f5004215317c
parentDocSlug: save-data-from-your-app
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

To define a custom field, you need to add a `customFieldDefinitions` array to your iris app manifest:

```json
  customFieldDefinitions: [
    {
      type: 'STRING',
      entityType: 'ASSET',
      key: 'myKey',
      title: 'String Field',
      uiEditable: true,
      uiVisible: true
    }
  ]
```



1. `type` defines the custom field type (see [below](#custom-field-types) for all options).

2. `entityType` defines what type of entity a custom field can be used on. The following types are available:
  - `ACCOUNT`
  - `ASSET`
  - `GROUP`
  - `SITE`

3. `key` defines the programmatic name of the field and cannot be changed after it has been created.

4. `title` defines the UI visible name of the field.

5. `uiEditable` / `uiVisible` controls how the field will be shown in the Manager UI. This does not limit how the field is used inside the Iris App.

  Apart from the these standard properties, some field types have [extra properties defined below](#type-specific-properties).

  **All custom fields defined by an Iris App will be owned by the Iris App, and the Iris App developer should consider existing data when changing field definitions.**

# Custom field types

| Field type   | Description                                                                                                             | Extra properties                                        |
|--------------|-------------------------------------------------------------------------------------------------------------------------| ------------------------------------------------------- |
| BOOLEAN      | Boolean value that can store true or false.                                                                             |                                                         |
| DATE         | Date stored in ISO8601 format.                                                                                          |                                                         |
| DROPDOWN     | A predefined list of options. Supports both single and multi selects.                                                   | `allValues`, `multiSelect`, `dropDownValueReplacements` |
| EMAIL        | Email field. Will be rendered with a mailto link in the UI.                                                             |                                                         |
| NUMBER       | Numeric values                                                                                                          | `minimum`, `maximum`, `isInteger`                       |
| PHONE_NUMBER | Phone number stored in E.164 format. Validated using [Google libphonenumber](https://github.com/google/libphonenumber). |                                                         |
| STRING       | Free text field                                                                                                         | `minimumLength`, `maximumLength`, `pattern`             |
| WEB_ADDRESS  | Web address. Will be shown as a link to open a new window in the UI.                                                    |                                                         |
| JSON         | JSON values.                                                                                                            |                                                         |
| MONETARY     | Monetary values with currency in ISO 4217 standard.                                                                     | `minimum`, `maximum`                                    |

# Type specific properties

| Property                    | Field type | Required | Description                                                                                             |
|-----------------------------|------------|----------|---------------------------------------------------------------------------------------------------------|
| `maximum`           | NUMBER     | No       | Maximum numeric value |
| `minimum`           | NUMBER     | No       | Minimum numeric value |
| `unitSi`            | NUMBER     | No       | Unit used for users using SI Customary system of measurement |
| `unitUs`            | NUMBER     | No       | Unit used for users using US Customary system of measurement |
| `isInteger`         | NUMBER     | No       | Disallow decimal values. Can't be true if `unitSi` or `unitUs` is specified |
| `maximumLength`     | STRING     | No       | Maximum length of the text |
| `minimumLength`     | STRING     | No       | Minimum length of the text |
| `pattern`           | STRING     | No       | The allowed regular expression. Syntax is documented [here](https://github.com/google/re2/wiki/Syntax). |
| `allValues`         | DROPDOWN   | Yes      | All allowed values |
| `multiSelect`       | DROPDOWN   | No       | Allow multiple options to be selected. Default `false`                                                  |
| `valueReplacements` | DROPDOWN   | No       | Map from old values no longer allowed to new values. Used for updating existing data                    |
| `currency`          | MONETARY   | yes      | Currency in ISO 4217 standard |

> 📘 Nice to know
> 
> All custom fields defined by an app will be owned by the app, and the app developer should consider existing data when changing field definitions.
