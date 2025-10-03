---
title: Getting started with IrisX Analytics
category:
  uri: Analytics & Insights
---

If you are new to IrisX Analytics, this section provides guidance on a few areas to explore as you begin leveraging your fleet data. The main goal is to help you understand the data and introduce some basic tools for creating actionable insights from your telematics data. While this covers the basics, IrisX Analytics offers much more to tailor solutions to your specific use cases.

## Catalog
To get started with IrisX Analytics, begin by exploring the data available in your catalog. This is where all data is stored, mainly you will find:

1. **IrisX:** This is where you will find all the data that you need for your analytics work. You can for instance find data on your account, advanced sensors and error occurrences (machine faults and CAN errors). Most importantly, you will see your insights there. This is the telematics data that has been prepared by Trackunit so you can easily get started at creating dashboards, ML models, workflows and much more. For detailed explanations of each insight, visit the [Trackunit data model reference](https://developers.trackunit.com/reference/data-model).
2. A folder with your name, such as a **dev, test and prod folder.** This is where you can store your tables after having worked with the data from the IrisX folder. You can use the dev environment when creating your data, the test environment to see if your code works as expected and then the prod environment for your finalised code.

## Dashboards
Navigate to the "Dashboards" section in the left-side menu to build intuitive dashboards that track your data over time. After creating a new dashboard, select one or more source tables in the "Data" tab. To customize further (for example, to focus on a specific machine type), use the SQL editor to add custom tables to your dashboard. In the "Canvas" tab, you can create various visualizations from your data to provide your team with actionable insights.

:arrow_right: Learn more about [Databricks Dashboards](https://docs.databricks.com/aws/en/dashboards/)

## SQL Editor
The SQL editor is an effective way to familiarize yourself with your data in depth. This tool allows you to query all insights, join tables, and perform aggregations. It's an excellent starting point when exploring options and determining where you can gain the most value from your data for your specific use cases.

:arrow_right: Learn more about [Databricks SQL Editor](https://docs.databricks.com/aws/en/sql/user/sql-editor/)

## Workspace and Notebooks
While the SQL editor is great for initial data exploration, notebooks allow you to perform more complex calculations on your data. Notebooks can be used to create new tables from existing data and can be written in SQL, Python, or PySpark. They can be found in your workspace.

**Here are some example tasks you might tackle in your first notebook:**

- Calculate equipment utilization rates across different job sites to identify underutilized machinery
- Analyze fuel consumption patterns to detect potential maintenance issues or operator behavior affecting efficiency
- Develop geographic heat maps showing equipment distribution and utilization across multiple projects
- Compare actual equipment runtime against project schedules to improve resource allocation and planning

:arrow_right: Learn more about [Databricks Notebooks](https://docs.databricks.com/aws/en/notebooks/)
