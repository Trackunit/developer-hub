---
title: Asset Event API - Introduction
category:
  uri: /branches/1.0/categories/reference/Asset Event API
---
The Trackunit Asset Event API is a REST API that enables customers to manage their asset events.

## Key Features

### Asset Events Query:

The `/asset-event/log` endpoint returns all events given a set of filtering criteria. It supports filtering by:
- **Required parameters**: `fromTime` and `toTime` indicate the time range for querying asset events.
- Filtering for assets based on asset IDs, group IDs, site IDs, or customer IDs.
- Filtering for event types including ALERT, MACHINE_FAULT, CLASSIC_SERVICE, SERVICE_MANAGEMENT, INSPECTION, DAMAGE_REPORT, PRE_CHECK
- Filtering for criticality levels including CRITICAL, LOW and NONE
- Filtering for event status including OPEN, RESOLVED, DISMISSED and CLOSED

### Active Asset Events Query:

The `/asset-event/active endpoint returns active asset events. Active events are those that are currently ongoing or unresolved. It supports filtering by:
- Filtering for assets based on asset IDs, group IDs, site IDs, or customer IDs.
- Filtering for event types including ALERT, MACHINE_FAULT, CLASSIC_SERVICE, SERVICE_MANAGEMENT, INSPECTION, DAMAGE_REPORT, PRE_CHECK
- Filtering for criticality levels including CRITICAL, LOW

## Base URL

All API calls are made against the following base URL:

`https://iris.trackunit.com/public/api/eventlog/v3/`

## Example Use Cases

### Monitoring on which ALERT events were triggered on a Site last week 

```curl
curl --location 'https://iris.trackunit.com/public/api/eventlog/v3/asset-event/log' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <your-token>' \
--data '{
    "fromTime": "2025-01-01T00:00:000Z",
    "toTime": "2025-01-07T00:00:000Z",
    "siteIds": ["00000000-0000-0000-0000-000000123456"],
    "type": ["ALERT"],
    "status": ["OPEN"]
}'
```

### Monitoring all Critical Machine Fault events happened on the Fleet:

```curl
curl --location 'https://iris.trackunit.com/public/api/eventlog/v3/asset-event/log' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <your-token>' \
--data '{
    "fromTime": "2025-01-01T00:00:000Z",
    "toTime": "2025-01-07T00:00:000Z",
    "type": ["MACHINE_FAULT"],
    "criticality": ["CRITICAL"],
    "status": ["OPEN"],
}'
```

### Monitoring all open SERVICE MANAGEMENT events for a specific group:

```curl
curl --location 'https://iris.trackunit.com/public/api/eventlog/v3/asset-event/active' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <your-token>' \
--data '{
    "groupIds": ["00000000-0000-0000-0000-000000123456"],
    "type": ["SERVICE_MANAGEMENT"]
}'
```

## Constraints

- Visibility of asset event data is limited to asset visibility
- API Rate Limiting: 2 requests per 30 minutes per api user


## Summary

The API offers capabilities to query historical asset events and retrieve active events.
This allows managing asset events e.g. fault, alerts, making it a powerful tool for monitoring and maintaining asset health.
