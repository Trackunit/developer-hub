---
title: Streaming API
category: 62fbabf8d9095e057cc1cd2c
---
The Trackunit Streaming API is a near-realtime, low latency API, that enables customers to create their own data lake and services, leveraging Trackunit as Telematics Data Service Provider. This document describes the overall design and how to connect to the Streaming API.

> 📘 Available by request
>
> The Streaming API is only available by request as an add-on service. Customers need to be on an "Expand" subscription level and set-up costs/API license pricing will be handled by the account manager. Once commercials are agreed upon, Trackunit support can be contacted to set up the Streaming API functionality.

## Design

The Trackunit Streaming API is not a REST API, but instead implemented as a [Kafka](https://kafka.apache.org/)-based solution, backed by [Confluent Cloud](https://confluent.cloud/) and AWS infrastructure, in order to be highly available and performant. When a customer signs up for access to the Streaming API, a Kafka topic is created and a [Flink](https://flink.apache.org/) job starts forwarding data, related to the customer's machines, to that topic. Data is then available for the customer to consume. The data is kept on the topic for 14 days.  
Only the data related to the customer's machines will be made available for the customer.

Data is available in the Streaming API with low latency after it enters the Trackunit Iris platform. There can be delays between the telematic devices (or 3rd party integrations such as ISO feeds) and the Iris platform due to network connectivity or similar. The common case is however that data is available with near-realtime delays.

## Data Formats and Compatibility

Data is available in two formats:

- **Machine Insights-based**: High-level semantic information about machines, normalized and cleansed. Immediately ready to ingest into a data-lake, or for use in AI-based analytics.
- **RAW data**: As a direct replacement for the classic Unit APIs, this format is a direct migration path from those.

We recommend the Machine Insights based topic for any future integrations.

Technically, the data is provided in the [binary Avro data format](http://avro.apache.org/) which is highly efficient, while simultaneously enabling us to extend the data format in the future with additional data points. A Schema Registry is utilized to facilitate the evolution of producers and consumers while preserving compatibility. We will exclusively make compatible changes to the data formats and ensure compatibility with the previous version of the schemas, while also providing notifications about any changes. We strongly advise staying up to date and promptly implementing these schema changes to access all the available data points.

## How to connect

The technical solution is a Kafka cluster with Avro messages using a Schema Registry. Confluent provides a [number of examples in various programming languages](https://github.com/confluentinc/examples/tree/7.4.0-post/clients/cloud#with-schema-registry). We provide a customized and complete example of how to connect through Java.

As part of the introductory package we provide the following parameters to get started:

| Name                           | Description                                                                                             |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------|
| Bootstrap servers              | The hostname of the Kafka cluster to connect to.                                                        |
| SASL configuration             | Username and password to authenticate to the Kafka cluster and be granted access to the topics.         |
| Topic name                     | The Kafka topic name to consume data from.                                                              |
| Schema Registry URL            | The URL of the schema registry; this is used for ensuring compatibility when updating the Avro schemas. |
| Schema Registry authentication | Username and password to authenticate to the Schema Registry.                                           |
