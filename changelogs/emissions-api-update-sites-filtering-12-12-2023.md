---
title: Emissions API v1 Update
type: added
---

Added new Endpoints to the Emissions API to enable filtering by asset Ids, as well as getting emissions value for sites.

Below is a list of all the new endpoints:

> ➕ GET: `/emissions/period`

Get period

> ➕ POST: `/emissions/period`

Filter period

> ➕ GET: `/emissions/period/kpis`

Get period KPIs

> ➕ POST: `/emissions/period/kpis`

Filter period KPIs

> ➕ POST: `/emissions/monthly`

Filter monthly

> ➕ GET: `/emissions/monthly/summary`

Get monthly summary

> ➕ POST: `/emissions/monthly/summary`

Filter monthly summary

> ➕ POST: `/emissions/lifetime`

Filter lifetime

> ➕ GET: `/emissions/lifetime/kpis`

Get Lifetime KPIs

> ➕ POST: `/emissions/lifetime/kpis`

Filter Lifetime KPIs

> ➕ POST: `/emissions/daily`

Filter daily

> ➕ GET: `/emissions/daily/summary`

Get daily summary

> ➕ POST: `/emissions/daily/summary`

Filter daily summary

> ➕ GET: `/emissions/daily/kpis`

Get daily KPIs

> ➕ POST: `/emissions/daily/kpis`

Filter daily KPIs

> ➕ GET: `/sites/{siteId}/emissions`

Get site

