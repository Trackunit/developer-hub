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