---
title: CAN Faults API - Introduction 
category: 67e55097c5aa85004b6f011e
---

The Can Faults API is a robust solution designed to simplify fault monitoring, diagnostics, and simulation for connected assets. It provides a range of endpoints that cater to both historical analysis and fault management, making it an essential tool for fleet operators, maintenance teams, and system integrators.

> ➡️ [OpenAPI Specification for the CAN Faults API domain](https://developers.trackunit.com/openapi/67e55097c5aa85004b6f011c)
> 
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/67e55097c5aa85004b6f011c).

## Key Features

### Fault Retrieval:

The /faults endpoint returns detailed fault records based on machine IDs and date ranges, with optional filtering by suspect parameter number (SPN), failure mode indicator (FMI), and source address (SA). This granular approach facilitates rapid isolation of issues and comprehensive historical trend analysis.

The /get-unit-active-faults endpoints—available via both GET and POST methods—offer a legacy interface for retrieving fault records using a unit ID and date range. These endpoints return all faults (identical to /faults), supporting customers transitioning from classic Unit Active Faults API.

### Fault Summaries:

The /faults-summary endpoint aggregates fault data to provide summarized insights grouped by fault codes and time periods. This enables identification of recurring issues and offers an overall view of fleet health at a glance.

### Simulated Fault Operations:

Simulated fault operations are available through endpoints including /simulated-faults/list, /simulated-faults/send, /simulated-faults/resolve, and /simulated-faults/summary. These endpoints enable simulation of fault conditions, execution of fault resolution, and retrieval of simulated fault summaries, which are valuable for system testing and training support teams.

## Base URL

All API calls are made against the following base URL:

`https://iris.trackunit.com/public/api/can-faults/`

## Example Usage

Below is an example cURL command to retrieve fault data:

```curl
curl -X POST "https://iris.trackunit.com/public/api/can-faults/faults" \
  -H "Authorization: Bearer <your_token>" \
  -H "Content-Type: application/json" \
  -d '{
    "canFaultsRequest": {
      "machineIds": [0, 0],
      "interval": {
        "from": "1970-01-01T00:00:00.000Z",
        "to": "1970-01-01T00:00:00.000Z"
      }
    }
}'
```

This command retrieves fault records for the specified machine IDs over the given date range, providing insights into machine performance and historical fault trends.

### Summary

The Can Faults API offers a comprehensive suite of tools for fault management—from detailed fault retrieval and summarization to simulated fault operations. Its robust security, flexible query options, and detailed responses streamline fault diagnostics for optimal machine performance.

It also supports a legacy interface through the /get-unit-active-faults endpoints, which return the same fault data as /faults, enabling a smooth transition for customers migrating from classis Unit Active Faults API.

This API utilizes the unit and machine concepts. Learn more about them in the [Machine APIs Introduction](https://developers.trackunit.com/reference/machine-apis-intro).
