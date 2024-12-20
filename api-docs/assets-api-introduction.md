---
title: Assets API - Introduction
category: 63170aaed72d5f00a36a8afe
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
