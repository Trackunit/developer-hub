---
title: Compaction App API v1
type: added
---

Released stable version v1 of Compaction API. For more information, see the documentation and introduction of the endpoints.

# REST

Below is a list of all available REST endpoints:

## Filter:

> ➕ GET: `/api/compaction/v1/compactions/trips/{tripId}/filter`

[Get Trip Filter](ref:gettripfilter)

> ➕ PUT: `/api/compaction/v1/compactions/trips/{tripId}/filter`

[Update Trip Filter](ref:updatetripfilter)

> ➕ DELETE: `/api/compaction/v1/compactions/trips/{tripId}/filter`

[Delete Trip Filter](ref:deletetripfilter)

## Searches:

> ➕ POST: `/api/compaction/v1/compactions/searches`

[Create Saved Search](ref:createsavedsearch)

> ➕ GET: `/api/compaction/v1/compactions/searches`

[Get All Saved Searches](ref:getallsavedsearches)

> ➕ GET: `/api/compaction/v1/compactions/searches/{searchUUID}`

[Get Saved Search](ref:getsavedsearch)

> ➕ PUT: `/api/compaction/v1/compactions/searches/{searchUUID}`

[Update Saved Search](ref:updatesavedsearch)

> ➕ DELETE: `/api/compaction/v1/compactions/searches/{searchUUID}`

[Delete Saved Search](ref:deletesavedsearch)

## Trips:

> ➕ GET: `/api/compaction/v1/compactions/trips/{tripId}`

[Get Compaction Trip](ref:getcompactiontrip)

> ➕ DELETE: `/api/compaction/v1/compactions/trips/{tripId}`

[Delete Compaction Trip](ref:deletecompactiontrip)

> ➕ GET: `/api/compaction/v1/compactions/trips/{tripId}/compactions`

[Get Compaction Datapoints](ref:getcompactiondatapoints)

> ➕ GET: `/api/compaction/v1/compactions/trips/{tripId}/compactions/summarized`

[Get Summarized Compaction](ref:getsummarizedcompaction)

> ➕ POST: `/api/compaction/v1/compactions/trips`

[Get Compaction Trips](ref:getcompactiontrips)