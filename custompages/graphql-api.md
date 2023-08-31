---
title: GraphQL API Documentation
---

> 🚧 Beta
> 
> This is a beta version and subject to change without notice. Pricing, terms, conditions and availability may change in the final version.

[block:embed]
{
  "html": "<iframe class=\"embedly-embed\" src=\"//cdn.embedly.com/widgets/media.html?src=https%3A%2F%2Fwww.youtube.com%2Fembed%2FK3brU076DsI%3Ffeature%3Doembed&display_name=YouTube&url=https%3A%2F%2Fwww.youtube.com%2Fwatch%3Fv%3DK3brU076DsI&image=https%3A%2F%2Fi.ytimg.com%2Fvi%2FK3brU076DsI%2Fhqdefault.jpg&key=7788cb384c9f4d5dbbdbeffd9fe4b92f&type=text%2Fhtml&schema=youtube\" width=\"854\" height=\"480\" scrolling=\"no\" title=\"YouTube embed\" frameborder=\"0\" allow=\"autoplay; fullscreen\" allowfullscreen=\"true\"></iframe>",
  "url": "https://www.youtube.com/watch?v=K3brU076DsI",
  "title": "Mastering GraphQL in Trackunit Iris Apps: An In-Depth Introduction",
  "favicon": "https://www.google.com/favicon.ico",
  "image": "https://i.ytimg.com/vi/K3brU076DsI/hqdefault.jpg",
  "provider": "youtube.com",
  "href": "https://www.youtube.com/watch?v=K3brU076DsI",
  "typeOfEmbed": "youtube"
}
[/block]

## Introduction

The GraphQL API offers more flexible queries than the Trackunit REST API and only retrieves the data needed. Making it easier to quickly retrieve the data needed for your application.

With GraphQL, you construct queries and mutations to fetch or modify data.
Unlike REST APIs, which use multiple endpoints, GraphQL uses a single endpoint to handle all requests.
If you haven't worked with GraphQL before, learn how to by following [the official GraphQL documentation](https://graphql.org/learn/).

The next step is to go through our guide on how to interact with the GraphQL API using the SDK: 
- [Calling Trackunit GraphQL API using the Iris App SDK](https://developers.trackunit.com/docs/graphql-api)

If you want to query the API without using the SDK, you have to:
- [Obtain a token outside an Iris App](https://developers.trackunit.com/reference/access-token)
- Point you GQL client to ```https://iris.trackunit.com/api/graphql/```

 The GraphQL explorer is an interactive way to familiarize yourself with the available data models:
- [GraphQL Explorer and Query builder](./graphql-explorer)

Click below to download the public schema if you need it:
- [Public schema](https://apps.iris.trackunit.com/graphql-public-viewer/schema.gql)


> 📘 Nice to know
>
> The most important datatypes are `assets` and `sites` as most other datatypes are child properties on these main ones.
Some fields are in a preview state and may change without notice.
To indicate you accept these terms pass the HTTP header `TU-PREVIEW:<codeword>` with your query requests.
The codeword differs for each preview field and you can find it by looking in the GQL schema (or explorer) above.
