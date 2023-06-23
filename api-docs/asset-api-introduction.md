---
title: Introduction
category: 63170aaed72d5f00a36a8afe
---
Assets are core entities that represent various machines, equipment, tools and attachments on the Iris platform. The handles provided in the APIs allow for easy asset management intended for system-to-system integration.

# Concepts
Assets have the following properties:

- An **asset** is a trackable piece of equipment divided into several subtypes; machine, equipment, tool or attachment.
- **Assets** can have zero to many **telematics devices** associated with them

# Asset Types

| Type       | Description                                                                                                                |
| :--------- | :------------------------------------------------------------------------------------------------------------------------- |
| Equipment  | A non-powered asset.                                                                                                       |
| Tool       | A small powered asset.                                                                                                     |
| Attachment | A thing which can be added/attached to something else (machine or equipment) in order to make it more useful or versatile. |
| Other      | Anything not fitting into the other asset types.                                                                           |


```json Example Asset Object
{
    "assetType": "OTHER",
    "brand": "string",
    "createdAt": "2023-06-23T09:26:24.279Z",
    "externalReference": "string",
    "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "model": "string",
    "name": "string",
    "ownerAccountId": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "permissions": {
    "edit": true
    },
    "productionYear": 0,
    "serialNumber": "string",
    "telematicsDevices": [
    {
        "id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
        "serialNumber": "string"
    }
    ],
    "type": "string"
}
```


# Asset Workflows
The Asset API supports the following workflows, to manage assets:

| Workflow | Description |
| :------- | :---------- |
| [Share Assets](https://developers.trackunit.com/reference/shareassets) | Share assets with other Account |
another Account |
| [Unshare Assets](https://developers.trackunit.com/reference/unshareassets) | Unshare Asset visibility from other Trackunit Accounts |
| [Transfer Assets](https://developers.trackunit.com/reference/transferassets) | Transfer asset ownership to another Trackunit Account |
| [Onboard Assets](https://developers.trackunit.com/reference/onboardassets) | Onboard new Asset to your Trackunit Account|
| [Offboard Assets](https://developers.trackunit.com/reference/offboardassets) | Remove Asset from your Trackunit Account |