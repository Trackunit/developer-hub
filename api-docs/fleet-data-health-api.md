---
title: Fleet Data Health API - Introduction
category:
  uri: "/branches/1.0/categories/reference/Fleet Data Health Issues (Beta)"
---

_Fleet Data Health Issues REST API_ is your foundation for insight into telematics data integrity, enabling proactive health tracking and resolution planning.

Monitor the health of your fleet’s telematics data via a RESTful API that surfaces analytic-driven issues.

This Beta release gives you programmatic access to real-time and historical asset-level data health concerns,
such as installation misconfigurations, battery anomalies, or connectivity issues.

> ➡️ [OpenAPI Specification for the Fleet Data Health API domain](https://developers.trackunit.com/openapi/fleet-data-health-issues-beta.json)
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/fleet-data-health-issues-beta.json).


## Beta Limitations & Scope
  - The API is marked `v1beta1`; interfaces and schemas may evolve.
  - Rate limits, pagination, and error semantics follow the standard Iris REST API behavior.


## Use Cases

- **Health Monitoring**
  Query all active (`OPEN`) issues to identify assets needing attention.

- **Issue Investigation**
  Drill into a specific issue by its `issueId` to understand its type, timing, and resolution status.

- **Bulk Analysis**
  List issues across multiple assets and aggregate by category, type, or state to gain fleet-wide visibility.


## Concepts & Data Model

### Issue Categories & Types
Issues are organized into categories, each with specific types that describe the detected problem:
- `INSTALL_AND_CONFIGURATION_HEALTH` - configuration or installation-related issues.
  - `OPERATING_HOURS` - No operating hours data available or other issues that can cause incorrect operations hours value.
  - `NO_CAN_DATA_WIRING` - CAN wiring problem detected, no CAN data received.
  - `NO_CAN_DATA_CONFIGURATION` - CAN configuration issue, preventing data reporting.
  - `DIGITAL_KEY_DISABLED` - Digital Key feature disabled, preventing expected data.
  - `BLUETOOTH_DISABLED` - Bluetooth feature disabled, preventing expected data.
  - `INSTALLATION_VALIDATION_MISSING` - Device installation has not been validated.

- `COVERAGE_ISSUES` - problems with GPS or cellular network connectivity.
  - `LOW_CELLULAR_COVERAGE` - Poor or missing cellular coverage.
  - `LOW_GPS_COVERAGE` - Poor or missing GPS signal.

- `DEVICE_BATTERY_ISSUES` - issues related to device power supply or battery health.
  - `LOW_DEVICE_BATTERY_VOLTAGE` - Low internal device battery voltage.
  - `LOW_DEVICE_INPUT_VOLTAGE` - Low external power supply/input voltage.

- `NON_REPORTING_UNIT` - units that fail to send any data.
  - `DATA_NOT_RECEIVED` - No data received from the device; asset not reporting.

*(Categories and types will expand over time as more analytics are introduced.)*

### Lifecycle States
Each issue is assigned a state:
- `OPEN` - Active or unresolved issue.
- `RESOLVED` - Previously flagged issue, now addressed.

### Asset Association
  Every issue is tied to a specific asset via its unique identifier.

### Fields Returned
A typical issue object includes:
- `id` (string) - Unique issue identifier.
- `assetId` (string) - Asset identifier the issue is associated with.
- `category` (string) - High-level classification.
- `type` (string) - Specific type under the category.
- `state` (string) - `OPEN` or `RESOLVED`.
- `createdAt` (ISO 8601 string) - Timestamp when the issue was created.
- `resolvedAt` (ISO 8601 string) - Timestamp when the issue was resolved, if applicable.
