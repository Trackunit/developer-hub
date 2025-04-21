---
title: Compaction API - Introduction 
category: 
---

Trace Compaction for your Equipment: Compaction APIs helps you to monitor performance, improve efficiency, and stay in control of your projects. 
This APIs supports you in your daily work, as you can trace your vibratory plates’ compaction at any time from your desk and obtain seamless documentation. 
With traceable compaction progress, you can access completely documented quality control.

> ➡️ [OpenAPI Specification for the Compaction API domain](https://developers.trackunit.com/openapi/680143f4d89fc8005c634539)
> 
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/680143f4d89fc8005c634539).


### Trips
A trip is a collection of compaction datapoints that are captured at a given time period. Trips are automatically being created when a period of datapoints are started and stopped. 

A trip or a set of trips can be selected and their compaction values can be shown - so it is possible to see where the soil is under or over compacted.

A trip can be edited - by adjusting the time of the trip - or by offsetting the gps coordinates of the entire trip. 

To learn more about Compaction, visit:
https://www.wackerneuson.de/en/services/equipcare


## Base URL

All API calls are made against the following base URL:

`https://iris.trackunit.com/api/Compaction/v1/compactions/`
