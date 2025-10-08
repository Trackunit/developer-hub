---
title: Data Ingest API - Introduction
category:
  uri: "/branches/1.0/categories/reference/Data Ingestion"
---

The Data Ingest API provides a streamlined method for ingesting asset data into the Trackunit Iris platform.
This RESTful API is designed for efficient time-series data transmission, prioritizing accuracy for both historical and real-time asset information within the Iris ecosystem.

Supports ingestion of multiple data types:
- Machine Insights
- Locations
- Advances Sensors

> 📘 Subscription requirement
>
> The Data Ingest API is only available to customers on IrisX. Learn more about the [IrisX subscription](https://developers.trackunit.com/docs/irisx-overview)

> 🚧 Early access
>
> Please be aware that Data Ingest API is currently in an early access, available only upon request.

## Use Cases

The Data Ingest API is particularly valuable for:

- Systems requiring minimal data latency
- Recovery scenarios requiring backfilling of data
- Migration projects involving bulk historical data import
- Telematics data integrations where [data feeds](https://new.manager.trackunit.com/marketplace?q=&c=DATA_FEEDS) are insufficient

## Concepts

### Assets

Assets are the core entities in the Trackunit ecosystem, representing various machines, equipment, tools, and attachments:

 - Each asset has a unique identifier in the system
 - Assets can have zero to many telematics devices associated with them
 - Learn more [about assets](https://developers.trackunit.com/reference/intro-asset-administration-apis)

### Machine Insights

Machine Insights are standardized metrics that provide comprehensive operational data about assets:

- Conform to ISO 15143-3 standards plus Trackunit-specific extensions
- Provide normalized data across different asset types, enabling standardized reporting and analytics
- Support both real-time monitoring and historical trend analysis
- Learn more about [Machine Insights](https://developers.trackunit.com/reference/data-model)

### Advanced Sensors

Advanced Sensors represent custom, non-standardized metrics that capture equipment-specific data points:

- Identified by unique sensor IDs within the Trackunit platform
- Designed to accommodate proprietary or specialized measurements not covered by standard Machine Insights
- Ideal for capturing manufacturer-specific CAN bus data or equipment-specific readings

### Locations

Geographical position information for assets:

- Includes latitude, longitude, and accuracy radius
- Timestamped for tracking movement history

## Requirements

- User's account has visibility access of the assets
- All assets already exists within Trackunit Iris Platform
- Advanced Sensors already exists within Trackunit Iris Platform
