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

[Get period](ref:getemissionsperiodv2)

> ➕ POST: /v2/emissions/period

[Filter period](ref:filteremissionsperiodv2)

> ➕ GET: /v2/emissions/period/kpis

[Get period KPIs](ref:getemissionsperiodkpisv2)

> ➕ POST: /v2/emissions/period/kpis

[Filter period KPIs](ref:filteremissionsperiodkpisv2)

> ➕ POST: /v2/emissions/monthly

[Filter monthly](ref:filtermonthlyemissionsv2)

> ➕ GET: /v2/emissions/monthly/summary

[Get monthly summary](ref:getmonthlyemissionssummaryv2)

> ➕ POST: /v2/emissions/monthly/summary

[Filter monthly summary](ref:filtermonthlyemissionssummaryv2)

> ➕ POST: /v2/emissions/lifetime

[Filter lifetime](ref:filterlifetimeemissionsv2)

> ➕ GET: /v2/emissions/lifetime/kpis

[Get Lifetime KPIs](ref:getlifetimeemissionskpisv2)

> ➕ POST: /v2/emissions/lifetime/kpis

[Filter Lifetime KPIs](ref:filterlifetimeemissionskpisv2)

> ➕ POST: /v2/emissions/daily

[Filter daily](ref:filterdailyemissionsv2)

> ➕ GET: /v2/emissions/daily/summary

[Get daily summary](ref:getdailyemissionssummaryv2)

> ➕ POST: /v2/emissions/daily/summary

[Filter daily summary](ref:filterdailyemissionssummaryv2)

> ➕ GET: /v2/emissions/daily/kpis

[Get daily KPIs](ref:getdailyemissionskpisv2)

> ➕ POST: /v2/emissions/daily/kpis

[Filter daily KPIs](ref:filterdailyemissionskpisv2)

> ➕ GET: /v2/sites/{siteId}/emissions

[Get site](ref:getsiteemissionsbysiteidv2)