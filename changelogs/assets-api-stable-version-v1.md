---
title: Added: Assets API v1
---
October 10, 2023
Released stable version v1 of Assets API.

Discover the power of our Assets API, your key to manage the asset domain. By leveraging the Assets API, developers can easily onboard and offboard assets to Trackunit Iris and get all assets in a fleet as well as update specifications for an asset. This API also allows to manage assets across accounts by enabling the share, transfer, unshare and remove visibility actions. For more information, see the documentation of the endpoints.

Below a list of all available endpoints:

> ➕ GET: /asset/v1/assets

[Get asset](ref:getasset)

> ➕ GET: /asset/v1/assets

[Get assets](ref:getassets)

> ➕ POST: /asset/v1/assets/onboard

[Onboard asset](ref:onboardasset)

> ➕ POST: /asset/v1/assets/{assetId}/offboard

[Offboard asset](ref:offboardasset)

> ➕ GET: /asset/v1/assets/{assetId}/shares

[List asset shares](ref:getassetshares)

> ➕ PATCH: /asset/v1/assets/{assetId}

[Update asset](ref:patchasset)

> ➕ POST: /asset/v1/assets/remove-visibility

[Remove visibility](ref:removevisibilityforassets)

> ➕ POST: /asset/v1/assets/share

[Share assets](ref:shareassets)

> ➕ POST: /asset/v1/assets/transfer

[Transfer assets](ref:transferassets)

> ➕ POST: /asset/v1/assets/unshare

[Unshare assets](ref:unshareassets)
