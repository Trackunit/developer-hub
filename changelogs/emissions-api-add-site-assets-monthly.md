---
title: Emissions API Site Assets Update
type: added
---

Introducing four new endpoints to the Emissions API that allow a breakdown of assets emissions values by site summed up on a monthly basis.

These endpoints provide emissions values for the period they have been on the site.  These endpoints are different from the existing monthly endpoints that provide emissions values for the period they have been in use.

Only admin users will have access to assets emissions values by site if the asset has been deleted or removed from the account.

To retrieve a list of site ids use the Sites API.

## New Endpoints

> ➕ GET: `/v2/sites/{siteId}/emissions/monthly`

[Get Assets by Site Monthly](ref:getsiteemissionsmonthlybysiteid)

> ➕ POST: `/v2/sites/{siteId}/emissions/monthly`

[Filter Assets by Site Monthly](ref:filtersiteemissionsmonthlybysiteid)

> ➕ GET: `/v2/sites/{siteId}/emissions/monthly/summary`

[Get Assets by Site Monthly Summary](ref:getsiteemissionsmonthlysummarybysiteid)

> ➕ POST: `/v2/sites/{siteId}/emissions/monthly/summary`

[Filter Assets by Site Monthly Summary](ref:filtersiteemissionsmonthlysummarybysiteid)