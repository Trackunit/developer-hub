---
title: Assets API - Introduction
category: 63170aaed72d5f00a36a8afe
---

Discover the power of our Assets API, your key to manage the asset domain. By leveraging the Assets API, developers can easily get all assets in a fleet as well as update specifications for an asset. This API also allows to manage assets across accounts by enabling the share, transfer, unshare and remove visibility actions. For more information, see the documentation of the endpoints.

> 🚧 No onboarding / offboarding support of machine type assets
> 
> The Assets API currently does not support onboarding or offboarding assets with the MACHINE asset type. Furthermore, the telematics devices are currently limited to Bluetooth telematics devices. See the [Machine Onboarding API](https://app.swaggerhub.com/apis-docs/trackunit.com/machine-onboarding/1.0.46) for those operations for now.

## Concepts

Assets are core entities that represent various machines, equipment, tools and attachments on the Iris platform. The handles provided in the API's endpoints allow for easy asset management intended for system-to-system integration.

Assets have the following properties:

- An **asset** is a trackable piece of equipment divided into several subtypes; machine, equipment, tool or attachment.
- **Assets** can have zero to many **telematics devices** associated with them

## Asset Types

| Type       | Description                                                                                                                |
| :--------- | :------------------------------------------------------------------------------------------------------------------------- |
| Machine    | A large powered asset.                                                                                                     |
| Equipment  | A non-powered asset.                                                                                                       |
| Tool       | A small powered asset.                                                                                                     |
| Attachment | A thing which can be added/attached to something else (machine or equipment) in order to make it more useful or versatile. |
| Other      | Anything not fitting into the other asset types.                                                                           |
