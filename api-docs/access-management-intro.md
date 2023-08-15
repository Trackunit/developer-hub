---
title: Access Management Introduction
category: 62ea3a0fef042a063b8717c7
---
Our Access Management API provides a list of APIs enabling machine owners to assign access to machines for operators.

The document is intended for developers, who wants to integrate systems, write client libraries or other interactions on an API-level.

## Interface

The API expose an OpenAPI JSON REST interface that you can call directly using your OAuth 2.0 access token. See [Access IRIS APIs](../reference/access-token) for further details on how to obtain an access token.

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

- To be able to use bluetooth keys and rolling pins the operator needs to have access to Trackunit On.
