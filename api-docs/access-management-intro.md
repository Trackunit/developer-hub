---
title: Access Management - Introduction
category: /branches/1.0/categories/reference/Access Management
---
Our Access Management API provides a list of APIs enabling machine owners to assign access to machines for operators.

> 📘 Subscription requirement
>
> This API is available for customers that have acquired a license for the Access Control API capability, and have been migrated to IRIS Access Control.

The document is intended for developers, who wants to integrate systems, write client libraries or other interactions on an API-level.

## Concepts

Access Management is built on the following concepts

- An **asset** is a trackable piece of equipment e.g. a machine or an accessory.
- A **key** is something that gives access to an asset. These types of keys exists:
  - **Key card**
  - **Static pin** a pin that doesn't change
  - **Rolling pin** a pin that changes regularly
  - **Bluetooth key** A key that can unlock a machine through bluetooth.
- An **operator** is a person that operates assets and exists in the **operator registry**.

Constraints

- To be able to use bluetooth keys and rolling pins the operator needs to have access to the mobile app Trackunit On.

## Rate Limiting

* Fetching key-usage - max 1 call per operator/asset per minute
