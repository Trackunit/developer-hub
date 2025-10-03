---
title: Assets API - Introduction
category:
  uri: Assets
---

Discover the power of our Assets API, your key to managing your fleet. By leveraging the Assets API, developers can easily get all assets in a fleet as well as update specifications for an asset. For more information, see the documentation of the endpoints. If you are looking to manage assets across accounts via share, transfer, unshare and remove visibility actions, then visit the [Ownership & Visibility API](https://developers.trackunit.com/reference/ownership-visibility-api-intro).

> 📘 IrisX customers can also access data connected to Asset(s) via the GraphQL API
>
> Via the Public GraphQL API, you can utilize query capabilities to fetch data connected to asset(s) and other domains which would be multiple separate calls in the REST APIs. Additionally you can perform mutations to modify data associated with asset(s). Explore the GraphQL schema through our [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/). Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview).

> 🚧 No onboarding / offboarding support of machine type assets
>
> The Assets API currently does not support onboarding or offboarding assets with the MACHINE asset type. Furthermore, the telematics devices are currently limited to Bluetooth telematics devices. See the [Machine APIs](https://developers.trackunit.com/reference/machine-apis-intro) for those operations for now.

## Concepts

Assets are core entities that represent various machines, equipment, tools and attachments on the Iris platform. The handles provided in the API's endpoints allow for easy asset management intended for system-to-system integration.

Assets have the following properties:

- An **asset** is a trackable piece of equipment divided into several subtypes; machine, equipment, tool or attachment.
- **Assets** can have zero to many **telematics devices** associated with them

> ➡️ [OpenAPI Specification for the Assets API domain](https://developers.trackunit.com/openapi/assets.json)
>
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/assets.json).

## Asset Types

| Type       | Description                                                                                                                |
| :--------- | :------------------------------------------------------------------------------------------------------------------------- |
| Machine    | A large powered asset.                                                                                                     |
| Vehicle	   | Heavy assets used for transporting people or goods, especially on land. (V2 Beta only)                                     |
| Gateway	   | Serve as a communication managers between bluetooth tags and the Iris platform.                                            |
| Equipment  | A non-powered asset.                                                                                                       |
| Tool       | A small powered asset.                                                                                                     |
| Attachment | A thing which can be added/attached to something else (machine or equipment) in order to make it more useful or versatile. |
| Other      | Anything not fitting into the other asset types.                                                                           |

## Additional standard fields for commom metadata on Assets

Trackunit provides a number of standard fields for common metadata, that can be used by all customers to extend the available data model. See a [list of all available standard fields in the Custom Fields API introduction](/reference/custom-field-intro).

**How to set values on standard fields**
1. Use the [Custom Fields Values API](/reference/custom-fields-get-values) to get all available fields. Specify the `entityId` for your query, which is an assetId for any fields listed above.
2. Use the `Create`, `Update` or `Delete value` endpoints for any futher operations on the available fields.

## Extending the Data Model

Missing any specific fields needed to define assets in your business context? Custom fields provide a way to define new fields in the Trackunit data model. Allowing to extend and customize Trackunit Manager. Currently we support **extending the data model of assets, accounts, groups, sites, customers and rental contracts with new fields**.

> 📘 Subscription requirement
>
> IrisX is required to create and change custom field definitions. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)

1. To define a custom field, you first need to [add a definition using the Custom Fields Definitions API.](/reference/custom-field-definitions)
2. Use the [Custom Fields Values API](/reference/custom-field-values) to set values on your defined custom fields.
- Specify the `entityId` for your query. Depending on which domain type you are interested in, this can be an assetId, accountId, groupId, siteId, customerId or rentalContractId.
