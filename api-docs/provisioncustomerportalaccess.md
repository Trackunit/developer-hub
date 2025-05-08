---
title: Provision Customer Portal Access with SSO
category: 65c1ea0e0bf60400104f7c68
---

This guide explains how to provision customer portal access for your customers using Single Sign-On (SSO).

## Overview

After creating a customer and assigning assets to them, you can provision access to the customer portal. This portal provides customers with visibility into all their assigned assets.

## Prerequisites

- An SSO connection must be configured in advance
- Contact your Trackunit representative for SSO setup instructions
- This API is only available for IrisX customers

## Process Flow

1. Create a customer and assign assets to them
2. When a customer user needs access to their telematics data, call this API to provision their access
3. The API will return a URL - redirect the user's browser to this URL
4. If additional setup is required, a waiting screen will be displayed to the user
5. The user will be authenticated using the preconfigured SSO connection
6. Upon successful authentication, the user will see a branded version of Trackunit Manager with their assets

![Provisioning process](https://cdn.statically.io/gh/trackunit/developer-hub/master/api-docs/provisioncustomerportalaccess.drawio.png)

The API endpoint is idempotent, so may be called each time a user logs in. This also ensures that any changes in user details will be synchronized.

> 📘 Subscription Requirement
> 
> This API is exclusively available for IrisX customers. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview).

> ⚠️ Beta API
> 
> This API is currently in beta testing and may be subject to changes.