---
title: Extending the data model
category: 61fcd8e1a448f5004215317c
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

To help Iris app developers easily store extra data we allow an app to define custom fields on an asset or an account. When a field has been defined, a value can be set for an asset using the Iris App runtime.


### The benefits of using custom fields
Before diving into how to use custom fields, it is helpful to understand what the benefits are and in which scenarios to consider using the feature. Here are a few examples:


 1. **Fleet Management and Monitoring**: You might want to use custom fields to store additional information about vehicles in your fleet, such as fuel consumption, tire pressure, or custom vehicle attributes. This data can then be used to optimize routes, monitor vehicle health, and schedule preventative maintenance, ultimately reducing operating costs and improving fleet efficiency.

2.  **Asset Utilization and Allocation**: Custom fields can be used to store data about asset usage, such as hours of operation, idle time, or custom performance metrics. This data can help your organization optimize asset allocation, identify underutilized equipment, and make data-driven decisions about purchasing or leasing new assets.

 3. **Driver Performance and Safety**: Custom fields can be added to store information about driver behavior, such as average speed, braking patterns, or safety violations. You can use this data to identify areas for improvement, provide targeted training, and promote safe driving practices within your organization.

As a rule of thumb, whenever you find the need to store additional information about your fleet, you should consider declaring a new custom field to store it in. They are a good place to store notes and additional datapoints.

> 📘 Nice to know
> 
> The definition is created when the Iris App SDK is approved and shared across all assets. The value is set on each asset by the Iris App developer.
