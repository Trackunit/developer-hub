---
title: Operator Registry - Introduction
category:
  uri: "/branches/1.0/categories/reference/Operators"
---
Our Operator API provides a list of APIs enabling management of operators.

> 📘 Subscription requirement
>
> This API is available for customers that have acquired a license for the Access Control API capability, and have been migrated to IRIS Access Control.

The document is intended for developers, who wants to integrate systems, write client libraries or other interactions on an API-level.

## Concepts

The operator registry is built on the following concepts

- An **asset** is a trackable piece of equipment e.g. a machine or an accessory.
- An **operator** is a user that operates assets. Operators can sign in to the Trackunit On app if invited.

### Operator

#### Inviting Operator

- An operator can be invited to your organization. The invitation is distributed through a text message.
- When an operator is invited and the invitation is accepted the metadata of the operator can no longer be updated through the API. The operator can update the metadata through the Trackunit On app.
- Be aware that when accepting the invite the following changes will happen:
  - The **id** of the operator changes.
  - The metadata is updated with the information provided by the operator through the Trackunit On app.
  - The **accountId** field is cleared.

#### Deleting an operator

- When deleting an operator that has accepted and invite the operator will still be able to sign in to the Trackunit On app but will loose access to all data shared with the operator.

## Rate Limiting

* Fetching operators - max 60 requests per minute
