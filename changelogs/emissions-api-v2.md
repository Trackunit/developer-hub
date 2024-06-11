---
title: Emissions API v2 Update
type: added
---

Introduced new version 2 Emissions API endpoints that removed the field 'estimationConfidence' from the response, in favour of 'dataSourceScore' for individual assets.

Added two new fields to v2 KPI endpoints 'averageDataSourceScore' and 'dataSourceScoreCompilation'.
* averageDataSourceScore: The average score of the data source for the fleet or filtered assets.
* dataSourceScoreCompilation: Sums the total of each score into a bucket.

Data Source Score is a new field that provides a score for the data source of the emissions data per asset. The score is a value between 0 and 100, where 0 is the lowest score and 100 is the highest score.
The Data Source Score documentation can be found [here](https://help.trackunit.com/en/articles/170775-what-is-the-data-source-score-in-emissions-reporting).

## New Endpoints

> ➕ GET: /v2/emissions/period

[Get period](ref:getemissionsV2)

> ➕ POST: /v2/emissions/period

[Filter period](ref:filteremissionsV2)

> ➕ GET: /v2/emissions/period/kpis

[Get period KPIs](ref:getemissionskpisV2)

> ➕ POST: /v2/emissions/period/kpis

[Filter period KPIs](ref:filteremissionskpisV2)

> ➕ POST: /v2/emissions/monthly

[Filter monthly](ref:filtermonthlyemissionsV2)

> ➕ GET: /v2/emissions/monthly/summary

[Get monthly summary](ref:getmonthlyemissionsaggregatedV2)

> ➕ POST: /v2/emissions/monthly/summary

[Filter monthly summary](ref:filtermonthlyemissionsaggregatedV2)

> ➕ POST: /v2/emissions/lifetime

[Filter lifetime](ref:filterlifetimeemissionsV2)

> ➕ GET: /v2/emissions/lifetime/kpis

[Get Lifetime KPIs](ref:getlifetimeemissionskpisV2)

> ➕ POST: /v2/emissions/lifetime/kpis

[Filter Lifetime KPIs](ref:filterlifetimeemissionskpisV2)

> ➕ POST: /v2/emissions/daily

[Filter daily](ref:filterdailyemissionsV2)

> ➕ GET: /v2/emissions/daily/summary

[Get daily summary](ref:getdailyemissionsaggregatedV2)

> ➕ POST: /v2/emissions/daily/summary

[Filter daily summary](ref:filterdailyemissionsaggregatedV2)

> ➕ GET: /v2/emissions/daily/kpis

[Get daily KPIs](ref:getdailyemissionskpisV2)

> ➕ POST: /v2/emissions/daily/kpis

[Filter daily KPIs](ref:filterdailyemissionskpisV2)

> ➕ GET: /v2/sites/{siteId}/emissions

[Get site](ref:getsiteemissionsbysiteidV2)