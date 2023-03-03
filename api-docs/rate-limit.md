---
title: Rate & Size Limiting
category: 6295ae369ba4b1001464c9e5
---
## Rate Limits

To ensure a consistant experience for all consumers of the Trackunit REST APIs, a basic rate limit and page size limit is enforced

> 🚧 Rate Limits may change
> 
> Trackunit might adjust the rate limits to balance our demand and reliability.

Requests that are rate limited will get an error with a HTTP response code `429` back.

The specific API rate limit are specified in their documentation.

## Size Limits

In addition to limiting number of calls, a limit is also put on the max number of elements returned from our collection resources.

Unless other limits are specified in the API documentation the page size is

| Page Size         |      |
| :---------------- | :--- |
| Default page size | 20   |
| Max Page Size     | 1000 |