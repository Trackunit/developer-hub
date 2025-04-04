---
title: Best Practices for Customizing Data
category: 66c49b0049fa5200312dc835
---

The IrisX folder in your catalog contains all provided base data. While you can't modify this original data or add customized tables directly to the **IrisX catalog**, you can create new tables derived from this data for your specific use cases.
Store your custom tables in catalogs labeled with your name, following the dev/test/prod environment structure for proper development progression.

## Add new data to your environment:

1. Write code in a notebook that performs your desired calculations.
2. Save results in your designated catalog.
3. Choose the appropriate storage format.
4. For regular updates to your custom tables, create a workflow to run your notebooks automatically on a schedule.

## Different storage formats: 

A **table** is a structured dataset that physically stores data. Choose this when:

- You need to query or modify the dataset repeatedly
- Performance is critical for frequently accessed data
- The dataset serves as input for other analytics processes

For example, Trackunit provides its base data as tables to ensure optimal performance and reliability.

A **view** is a virtual table defined by a SQL query that doesn't store physical data. Views are ideal when:

- You need a consistent interface to dynamically generated results
- The underlying data changes frequently
- You want to simplify complex queries for business users
- Storage efficiency is important

**Materialized views** combine aspects of both tables and views by:

- Storing the results of a query physically (like tables)
- Maintaining a connection to the source query for refreshes
- Offering improved query performance while ensuring data currency
