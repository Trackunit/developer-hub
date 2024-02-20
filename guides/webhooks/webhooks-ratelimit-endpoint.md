---
title: Rate Limiting Endpoints
category: 652e408346c8860073a6bd12
---

When setting up a webhook endpoint to listen to events you might be concerned about the management of incoming requests on your system's end. Therefore we offer a rate limiting mechanism for your webhook endpoints. Rate limiting involves controlling the number of requests received within a specified timeframe from a particular source, preventing excessive traffic that could overwhelm the receiving server or degrade system performance.

## How do rate limits on webhook endpoints work?

The rate limit is defined as a limit for the number of messages per second to send to a specific webhook endpoint. After the limit is reached, requests will get throttled so to keep a consistent rate under the limit.

Due to the nature of distributed systems the actual rate of messages can sometimes be slightly above the enforced rate limit. So for example, if you set a rate limit of 1,000 per seconds, an endpoint may potentially get messages at a rate of 1,050 or even higher. Therefore we recommend to set rate limits slightly lower than what yous system might be able to handle.
