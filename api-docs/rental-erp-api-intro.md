---
title: Rental API / ERP integration - Introduction
category: 668640cd587364001eaccdc7
---

The Rental API is designed to facilitate seamless integration between the IrisX platform and any Enterprise Resource Planning (ERP) system. Building an ERP integration enables your organizations to streamline data flow, enhance operational efficiency, and ensure real-time access to critical business information. Specifically use this API for data synchronization, so that data between IrisX and ERP systems gets automatically synchronized to maintain up-to-date information across platforms.

> 📘 IrisX Subscription needed
> 
> The Rental ERP API is only available to customers on IrisX. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)

## Concepts

The ERP integrations are built on the following concepts

- An **asset** is a trackable piece of equipment e.g. a machine or an accessory.
- **Contract item** is an entry in a **contract** that contains information about when an asset is rented out to a customer.
- **Contract** is linked to a **customer** and therefore it connects an asset to a customer.
- **Customer** is the customer of the business that can rent (and therefore get access to) an asset (see the [Customer API](https://developers.trackunit.com/reference/customers-api-intro)).

![Trackunit Iris Rental Model](https://cdn.statically.io/gh/trackunit/developer-hub/master/api-docs/rental-model-diagram.png)

## Constraints

- Only assets owned by the account can can be updated with data from the ERP system.

- **externalReference** represents an identifier from the ERP system and has to be unique.
