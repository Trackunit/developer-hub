---
title: MSA Test API
---

Released stable version v1 of Assets API.

Discover the power of our Assets API, your key to manage asset domain. By leveraging the Assets API, developers can easily onboard, offboard assets to Iris, get assets fleet and update asset specification. API also allows to manage assets by share, transfer, unshare and remove visibility. For more information, see the documentation of the endpoints.

Below all available endpoints.

> ➕ GET: /asset/v1/asset

[Get asset](ref:getasset_v1)

> ➕ GET: /asset/v1/assets

[Get assets](ref:getassets_v1)

> ➕ POST: /asset/v1/assets/onboard

[Onboard asset](ref:onboardasset_v1)

> ➕ POST: /asset/v1/assets/{assetId}/offboard

[Offboard asset](ref:offboardasset_v1)

> ➕ GET: /asset/v1/assets/{assetId}/shares

[List asset shares](ref:getassetshares_v1)

> ➕ PATCH: /asset/v1/assets/{assetId}

[Update asset](ref:patchasset_v1)

> ➕ POST: /asset/v1/assets/remove-visibility

[Remove visibility](ref:removevisibilityforassets_v1)

> ➕ POST: /asset/v1/assets/share

[Share assets](ref:shareassets_v1)

> ➕ POST: /asset/v1/assets/transfer

[Transfer assets](ref:transferassets_v1)

> ➕ POST: /asset/v1/assets/unshare

[Unshare assets](ref:unshareassets_v1)
