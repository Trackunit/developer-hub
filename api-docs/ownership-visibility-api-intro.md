---
title: Ownership & Visibility - Introduction
category:
  uri: /branches/1.0/categories/reference/Ownership & Visibility
---

Ownership & Visibility API requests are used to manage assets' visibility and ownership on the Trackunit platform.

> ➡️ [OpenAPI Specification for the Ownership & Visibility API domain](https://developers.trackunit.com/openapi/ownership-visibility.json)
>
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/ownership-visibility.json).

## Concepts & Definitions

**Visibility** of an asset determines which accounts can see it in Trackunit Manager, Trackunit Go and the APIs.

**Ownership** of an asset grants additional permissions across the Trackunit platform to owning account.

For the purpose of managing ownership and visibility, the account that is granting, or revoking, the visibility or ownership is called the **caller.**

The account that is receiving the visibility or ownership, or from which visibility is removed, is called the **recipient.**

## Connections & Partnerships

In order to grant visibility or ownership, prior relationship between the caller and the recipient must be established. Relationships within the same organization are called connections. Relationships to accounts outside the organization are called partnerships.

Connections are created automatically when an account is created within the same organization. Partnerships are created manually by Trackunit support.

## Account Authority

For the purpose of managing ownership and visibility, we distinguish between regular and administrative accounts:

- By default, a top-level account is an administrative account for the entire organization.
- Regular accounts are only allowed to manage ownership and visibility of assets that they own.
- Administrative accounts are allowed to manage ownership and visibility of all assets within the organization.
