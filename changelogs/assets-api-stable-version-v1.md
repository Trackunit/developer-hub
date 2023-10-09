---
title: Assets API v1
---

Released stable version v1 of Assets API.

Discover the power of our Assets API, your key to manage asset domain. By leveraging the Assets API, developers can easily onboard, offboard assets to Iris, get assets fleet and update asset specification. API also allows to manage assets by share, transfer, unshare and remove visibility. For more information, see the documentation of the endpoints.

Below all available endpoints.

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
