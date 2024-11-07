---
title: Rental API / ERP integration - Introduction
category: 668640cd587364001eaccdc7
---

> 📘 IrisX Subscription needed
> 
> The Rental ERP API is only available to customers on IrisX. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)

## Concepts

The ERP integrations are built on the following concepts

- An **asset** is a trackable piece of equipment e.g. a machine or an accessory.
- **Contract item** is an entry in a **contract** that contains information about when an asset is rented out to a customer.
- **Contract** is linked to a **customer** and therefore it connects an asset to a customer.
- **Customer** is the customer of the business that can rent (and therefore get access to) an asset.

![](https://files.readme.io/7664f41-image.png)

## Constraints

- Only assets owned by the account can can be updated with data from the ERP system.

- **externalReference** represents an identifier from the ERP system and has to be unique.
