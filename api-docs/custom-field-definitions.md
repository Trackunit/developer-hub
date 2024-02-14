---
title: Definitions
category: 628c96a84164f50225dd1f14
---

> 🚧 Beta
>
> This is a beta version and subject to change without notice.

To define a custom field, you first need to add a definition using the API.

| Field type   | Description                                                                                |
| ------------ | ------------------------------------------------------------------------------------------ |
| Boolean      | Boolean value that can store true or false.                                                |
| Date         | Date field.                                                                                |
| Dropdown     | A predefined list of options. Supports both single and multi selects.                      |
| E-mail       | Email field. Will be rendered with a mailto link in the UI.                                |
| Number       | Numeric values. Supports unit conversion between metric and US customary units.            |
| Phone number | Phone number. Validates the format but does not validate the phone number actually exists. |
| Text string  | Free text field. Supports limiting length.                                                 |
| Web address  | Web address. Will be shown as a link to open a new window in the UI.                       |

It is possible to control if new fields should show up in appropriate places in the user interface or be an API only field.

Once a definition has been created values can be set using the [values API](custom-field-values).
