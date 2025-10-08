---
title: Asset Event API - Introduction
category:
  uri: /branches/1.0/categories/reference/Asset Event API
---
The Trackunit Asset Event API is a REST API that enables customers to manage their asset events.

## Key Features

### Asset Events Query:

The /asset-event endpoint returns all events given a set of filtering criteria. It supports filtering by:
- Filtering for assets based on asset IDs, group IDs, site IDs, or customer IDs.
- Filtering for event types including ALERT, CAN_ERROR, MACHINE_FAULT, CLASSIC_SERVICE, SERVICE_MANAGEMENT, INSPECTION, DAMAGE_REPORT, PRE_CHECK
- Filtering for criticality levels including CRITICAL, LOW and NONE
- Filtering for event status including OPEN, RESOLVED, DISMISSED and CLOSED
- Filtering on date ranges

### Active Asset Events Query:

The /asset-event/active endpoint returns active asset events. It supports filtering by:
- Filtering for assets based on asset IDs, group IDs, site IDs, or customer IDs.
- Filtering for event types including ALERT, CAN_ERROR, MACHINE_FAULT, CLASSIC_SERVICE, SERVICE_MANAGEMENT, INSPECTION, DAMAGE_REPORT, PRE_CHECK
- Filtering for criticality levels including CRITICAL, LOW

## Base URL

All API calls are made against the following base URL:

`https://iris.trackunit.com/public/api/eventlog/v3/`

## Example Usage

An example cURL command to get critical MACHINE_FAULT events:

```curl
curl --location 'https://iris.trackunit.com/public/api/eventlog/v3/asset-event' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <your-token>' \
--data '{
    "fromTime": "2025-01-01T00:00:000Z",
    "toTime": "2025-01-01T00:00:000Z",
    "eventTypes": ["MACHINE_FAULT"],
    "criticality": ["CRITICAL"]
}'
```

An example cURL command to get active ALERT events for an asset:

```curl
curl --location 'https://iris.trackunit.com/public/api/eventlog/v3/asset-event/active' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <your-token>' \
--data '{
    "assetIds": ["00000000-0000-0000-0000-000000123456"],
    "eventTypes": ["ALERT"]
}'
```

### Summary

The API offers capabilities to query asset events and retrieve active events.
This allows managing asset events e.g. fault, alerts, making it a powerful tool for monitoring and maintaining asset health.

## Rate Limiting

Rate limiting on this API is currently specified as a maximum of 2 requests in 30 minutes per API user.
