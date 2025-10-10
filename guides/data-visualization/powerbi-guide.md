---
title: PowerBI Guide
category:
  uri: /branches/1.0/categories/guides/Data Visualization
---

## Introduction

This guide will walk you through creating a custom data source in PowerBI that connects to the Iris GraphQL API.

This guide assumes you are experienced in connecting to custom data sources through PowerBI. We also recommend familiarizing yourself with the [Iris GraphQL API](https://developers.trackunit.com/reference/graphql-api-introduction).

For this guide, we will build a PowerBI visualization showing the average operating hours by asset type. For simplicity, we will limit our query to 100 assets.

> 📘 Extended GraphQL information:
>
> - [Rate & complexity limits](https://developers.trackunit.com/reference/graphql-api-rate-limits)
> - [How to use pagination with GraphQL](https://developers.trackunit.com/reference/graphql-api-pagination)

In order to build the visualization, we need the following:

1. Credentials for a Trackunit Manager API User. Please follow the first step of the guide [here](https://developers.trackunit.com/reference/access-token) to obtain credentials, if you do not already have them
2. Design a GraphQL query that retrieves the data we are interested in. In this case, the operating hours and asset type.
3. Create a custom PowerBI data source that
   1. Requests an Iris API token using the API User credentials
   2. Posts the GraphQL query to the Iris GraphQL API using the API token
   3. Converts the query response to the correct PowerBI data format
4. Create the desired visualization using the custom data source

## Creating an API User

Please see [this page](https://developers.trackunit.com/reference/access-token) for how to create an API user. For this guide, you will need the OAuth 2.0 credentials. We will then configure the PowerBI data source to request an access token using the credentials.

## Designing the GraphQL query

Before diving in to designing your query, we recommend familiarizing yourself with the Iris GraphQL API. A good starting point is this [GraphQL API introduction](https://developers.trackunit.com/reference/graphql-api-introduction).

Once you feel comfortable with the basic workings of the GraphQL API, you can use the [GraphQL Explorer](https://apps.iris.trackunit.com/graphql-public-viewer/) to design and test your query.

![](https://paper-attachments.dropboxusercontent.com/s_1B420E96A783D9410490925A5F80B2699E64CA79C5FCE645252EEA38D98A57CF_1701773925264_image.png)

The GraphQL explorer allows you to click your way through the GraphQL graph and build up a query. In the screenshot above, you can see that we are using the 'assets' subgraph to gather the 'id', 'type', and 'totalRunningHours'. On the right, you can see the response from the query.

Once you have a working query that gathers the data you are interested in, it’s time to build it into a PowerBI data source.

## Building the PowerBI data source

Now that you have your GraphQL query and your API credentials, you are ready to create the PowerBI data source.

To do this, open a new PowerBI report and go to the Transform Data dialog. Here you add a new source of the type 'blank query'. Open your new source in the Advanced Editor. This is the dialog where we will enter the code to connect to the Iris GraphQL API.

![](https://paper-attachments.dropboxusercontent.com/s_0103981BCC2FDE987007E02840AB13EADF7AC69622662739269EA91233F203D6_1701863678608_Skrmbillede+2023-12-06+kl.+12.54.34.png)

You can structure the code to connect to the Iris GraphQL API into three steps:

1. Request an Iris API token using the API User credentials
2. Post the GraphQL query to the Iris GraphQL API using the API token
3. Convert the query response to the correct PowerBI data format

ℹ️ The [complete data source code](https://developers.trackunit.com/docs/powerbi-guide#example-data-source-code)of this example is available at the bottom of this article.

### Request an Iris API token using the API User credentials

You start by using the API credentials to get an API token. Remember to use your own API credentials. For more information on this API call see [this guide](https://developers.trackunit.com/reference/access-token).

![](https://paper-attachments.dropboxusercontent.com/s_0103981BCC2FDE987007E02840AB13EADF7AC69622662739269EA91233F203D6_1701863739676_Skrmbillede+2023-12-06+kl.+12.55.35.png)

### Post the GraphQL query to the Iris GraphQL API using the API token

Now you are able to call the GraphQL API using the token obtained in the previous step.

![](https://paper-attachments.dropboxusercontent.com/s_0103981BCC2FDE987007E02840AB13EADF7AC69622662739269EA91233F203D6_1701863768509_Skrmbillede+2023-12-06+kl.+12.56.04.png)

ℹ️ Be aware, that when you copy the GraphQL query from the Iris GraphQL Explorer, it may not include all necessary quotation marks. See the code above for correct use of quotation marks.

You may also need to add some additional header fields. In this case, we need to add "TU-PREVIEW": "TIME-EXCAVATORS” to the headers, as we are using a preview feature in the GraphQL query. Read more about preview states in the GraphQL AOI [here](https://developers.trackunit.com/reference/graphql-api-introduction#overview-of-graphql-data-sources).

### Convert the query response to the correct PowerBI data format

Depending on your query, this step will vary. You can use the usual PowerBI tools to have PowerBI automatically generate the transformation code once you have the GraphQL query working.

![](https://paper-attachments.dropboxusercontent.com/s_0103981BCC2FDE987007E02840AB13EADF7AC69622662739269EA91233F203D6_1701863787193_Skrmbillede+2023-12-06+kl.+12.56.22.png)

### Example data source code

You can copy the code below to get started quicker, but remember to use your own API credentials.

```
let
  //
  // Request an Iris API token using the API User credentials
  //
  username = username,
  password = password,
  authorization_token = authorization_token,
  url_access = "https://auth.trackunit.com/token",
  body = "grant_type=" & Uri.EscapeDataString("password") & "&username=" & Uri.EscapeDataString(username) & "&password=" & Uri.EscapeDataString(password) & "&scope=" & Uri.EscapeDataString("api"),
  headers = [
      #"Content-Type" = "application/x-www-form-urlencoded",
      #"Authorization" = authorization_token
      ],
  Source_access = Json.Document(Web.Contents(url_access, [Content = Text.ToBinary(body), Headers = headers])),
  access_token = Source_access[access_token],
  //
  // Post the GraphQL query to the Iris GraphQL API using the API token
  //
  url_data = "https://iris.trackunit.com/api/graphql/",
  query = "{""query"": ""query MyQuery { assets(first: 100) { edges { node { insights {totalRunningHours} id type} } } }""}",
  Source_data = Web.Contents(
    url_data,
    [
      Headers = [
        #"Method"       = "POST",
        #"Content-Type" = "application/json",
        #"Authorization" = "Bearer " & access_token,
        #"TU-PREVIEW" = "TIME-EXCAVATORS"
      ],
      Content = Text.ToBinary(query)
    ]
  ),
  //
  // Convert the query response to the correct PowerBI data format
  //
  JSON = Json.Document(Source_data),
  dataRecord = JSON[data],
  assetsRecord = dataRecord[assets],
  edgesList = assetsRecord[edges],
  convertedToTable = Table.FromList(edgesList, Splitter.SplitByNothing(), null, null, ExtraValues.Error),
  expandedColumns = Table.ExpandRecordColumn(convertedToTable, "Column1", {"node"}, {"Node"}),
  expandedNode = Table.ExpandRecordColumn(expandedColumns, "Node", {"insights", "id", "type"}, {"Insights", "ID", "Type"}),
  expandedInsights = Table.ExpandRecordColumn(expandedNode, "Insights", {"totalRunningHours"}, {"TotalRunningHours"}),
  changeType = Table.TransformColumnTypes(expandedInsights,{{"TotalRunningHours", type number}})
in
    changeType
```

## Creating the desired visualization

From here you can use your GraphQL powered data source in the same way as any other data source in PowerBI to create visualizations, reports and dashboards.

Here you can see the final visualization for this example:

![](https://paper-attachments.dropboxusercontent.com/s_1B420E96A783D9410490925A5F80B2699E64CA79C5FCE645252EEA38D98A57CF_1701863184018_image.png)
