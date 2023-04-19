---
title: Designing a custom report
category: 61fcd8e1a448f5004215317c
parentDocSlug: custom-reports
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

## Calling GraphQL API
When you create a report you should use the GraphQL Data Adapter and set the language to "WebServiceQuery". Use the following settings for the request

```
Base URL: /public/api/graphql/manager/ or /public/api/graphql/manager/
Authorization header: $P{token}
Content-Type header: application/json
```

The request is added to the large text area in the dialog, remember to replace new lines with `\n`.

"Image goes here"

In the Fields tabs it is important to set the Root Path correct and then add the different fields returned by the GraphQL query (like shown in the picture above).

The $P{token} in the authorization header is auto filled out during report execution. But you need to add two parameters to the report with the following names, types and expressions:

| Name | Type | Prompting | Expression |
|-|-|-|-|
| _manualToken | String | True | |
| token | String | False | $P{TOKEN_SCRIPTLET}.obtainToken() |

When running the report you will get prompted to fill out the _manualToken. Set it to Bearer <TOKEN> where the <TOKEN> is obtainable through any requests to our DEV Manager.

## Special report parameters
To streamline our UI and make it easy for the customer to filter the report based on some standard filters, we have made a list of "special" parameters. If you use these parameter names we will create the following widgets in the UI and populate them with the correct data:

| Parameter name | Description | UI widget |
|-|-|-|
| `fromDate` and `toDate` | If you create two parameters with these names you will get a date range widget, allowing the user to set a specific date range or use one of the quick selects in the top |
| `filterByAssets` OR `filterByClients` OR `filterByGroups` OR `filterByZones` | With these parameters you get two widgets; a drop- down with the filters you want to have available for the user, and another widget that will allow the user to select the specific assets, clients, groups or zones, based on the selection in the first drop-down |