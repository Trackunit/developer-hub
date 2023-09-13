---
title: Sustainability API Introduction 
category: 64c280b4cab95c006f9359e3
---

The Trackunit Sustainability API is a REST API that enables customers to access emissions data for their assets.

> 📘 Available with the Emissions Reporting app 
>
> This API is available for customers that have acquired a license for the Emissions Reporting capability.

## Interface

The API expose an OpenAPI JSON REST interface that you can call directly using your OAuth 2.0 access token. See [Access IRIS APIs](../reference/access-token) for further details on how to obtain an access token.

#### There are 3 endpoints currently available:
1. Monthly: Aggregated 12 values per asset, 1 for each of the last 12 months
2. Lifetime: Aggregated 1 value per asset representing the total accumulation since the machine was originally put in use. This value is updated once a day
3. Daily: This is a non-aggregated limited set of most recent values (ex. 60 days). It provides one value per day for each of the recent days.

## Concepts

### Equipment and Energy Consumption
The energy consumption of construction equipment is separated in 2 broad categories for the purpose of emissions calculations:

* Fuel Consumption (l)
* Electric Consumption (kWh)

A third category is introduced to include (3) Plug-in Hybrid Electric equipment. This category will have both fuel consumption and electric consumption being tracked simultaneously, and the associated emissions will be totaled for both.
Fuel consumption by itself is a broad category that includes all kinds of fuel, for example:

* Diesel
* Biodiesel
* Gasoline
* Propane (LPG)
* Hydrogen

#### All the most commonly used fuel types can and will be measured in litres (l) as default.

Electric-powered machines consumption also exist with more than one type, and their consumption is always tracked in kWh consumed:

* Battery-electric (rechargeable with plug-in)
* Direct Plug-in (no batteries)

We have built our data structure and API to allow tracking of all types of consumption described above.

## Use-Cases

1. The number 1 use-case is one within the contractor segment. Contractors need to estimate total and broken down emissions for each of a group of machines at a location (branch, yard, site, etc.), within a category, or for comparisons between categories. The Daily endpoint provides the broken down values per machine per day for the set of recent days. This broken down data can also be used upstream by OEMs and Rental Houses to provide contractor-specific insights to their end-customers. Including emissions on invoices is an example of how contractors can consume this information.


2. Many companies have set targets for emissions. The Monthly endpoint provides the dashboard needed to track baselines, progress, impact of emissions reduction initiatives, etc. It provides a long term view of where we come from and can be used to make predictions for the future. This type of information is useful for periodic reporting to the board, for internal awareness, for reporting to investors, and to regulators if needed.


3. Understanding trends of changing use and emissions rate as machines age is an important insight within a fast-changing commercial and regulatory environment. The Lifetime endpoint can provide a big picture view at the asset level to course adjustments in purchasing and dispatching to meet the marketplace where the needs are.

## Constraints

- Visibility of emissions data is limited to asset visibility 
- Emissions Data is updated daily at 04:00 UTC
- API Rate Limiting: 200 requests per 15 minutes per user
