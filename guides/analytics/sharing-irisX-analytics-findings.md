---
title: Sharing IrisX Analytics Findings
category:
  uri: "/branches/1.0/categories/guides/Analytics & Insights"
---

## How can I share my IrisX Analytics Dashboard with others?

If you want to share the dashboards you created on IrisX Analytics, you have several options:

1. If the person has access to IrisX Analytics, you can easily share it with them using the IrisX interface.
2. If the person does not have access to IrisX Analytics, you can contact us and we can add them (this does not infer additional costs). We are also working on a self-service function so that you can give access to IrisX yourself in the future.
3. You can download the dashboard as html and share that to provide a one-time view.

## How to share findings with people not having access to IrisX Analytics?

Not everyone in your organization has the same technical background or needs, so providing multiple access methods outside of IrisX Analytics ensures everyone can leverage the data effectively. Here are several approaches to make your data accessible:

### BI Tools Integration
For analysts and business users who prefer visual data exploration, connecting popular business intelligence tools directly to your Databricks environment provides a familiar interface:

- **Power BI** offers native Databricks connectors, allowing users to create dashboards and reports without writing SQL. See our [IrisX Analytics to Power BI guide](https://developers.trackunit.com/docs/analytics-powerbi)
- Other tools such as **Tableau** or **Qlik** can also be connected using the partner connectors on the Databricks Marketplace.

### Excel Export
For users who need to work directly with the data or conduct one-time analyses on smaller datasets you can export tables or query results as Excel or CSV files directly from the IrisX Analytics interface.

### REST API Access
For programmatic access or integration with custom applications:

- Expose critical tables as online tables in Databricks
- Enable REST API access to the table with proper authentication
- Allow applications and services to query these tables directly

This method is ideal for developers building custom applications, data scientists working in different environments, or when you need to integrate with third-party systems that support API connectivity.
