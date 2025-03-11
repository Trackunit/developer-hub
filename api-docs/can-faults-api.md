---
title: CAN Faults API - Introduction 
category: 67c9a5624e7dbc00103d8836
---

The Can Faults API is a robust solution designed to simplify fault monitoring, diagnostics, and simulation for connected assets. It provides a range of endpoints that cater to both historical analysis and real-time fault management, making it an essential tool for fleet operators, maintenance teams, and system integrators.

## Key Features

### Fault Retrieval:

Detailed fault records are returned by the /faults endpoint. Queries can be performed using machine IDs and date ranges, with optional filtering by parameters such as suspect parameter number (SPN), failure mode indicator (FMI), and source address (SA). This granular approach facilitates rapid isolation of issues and comprehensive historical trend analysis.

### Fault Summaries:

The /faults-summary endpoint aggregates fault data to provide summarized insights grouped by fault codes and time periods. This enables identification of recurring issues and offers an overall view of fleet health at a glance.

### Active Fault Monitoring:

The /get-unit-active-faults endpoint supports real-time diagnostics through both GET and POST methods. It provides active fault monitoring for a specific unit based on unit ID and date range, facilitating prompt troubleshooting and proactive maintenance.

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

The Can Faults API offers a comprehensive suite of tools for fault management—from detailed retrieval and summarization of fault data to real-time monitoring and simulation. Its robust security, flexible query options, and detailed responses streamline fault diagnostics for optimal machine performance.