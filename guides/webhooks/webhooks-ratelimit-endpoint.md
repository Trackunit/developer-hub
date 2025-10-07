---
title: Rate Limiting Endpoints
category: /branches/1.0/categories/guides/Integrations & Connectors
---

When setting up a webhook endpoint to listen to events you might be concerned about the management of incoming requests on your system's end. Therefore we offer a rate limiting mechanism for your webhook endpoints. Rate limiting involves controlling the number of requests received within a specified timeframe from a particular source, preventing excessive traffic that could overwhelm the receiving server or degrade system performance.

## How do rate limits on webhook endpoints work?

The rate limit is defined as a limit for the number of messages per second to send to a specific webhook endpoint. After the limit is reached, requests will get throttled so to keep a consistent rate under the limit.

Due to the nature of distributed systems the actual rate of messages can sometimes be slightly above the enforced rate limit. So for example, if you set a rate limit of 1,000 per seconds, an endpoint may potentially get messages at a rate of 1,050 or even higher. Therefore we recommend to set rate limits slightly lower than what your system might be able to handle.

> 🚧 Please be mindful when setting rate limits
>
> The rate limit is intended to be used as a sort of a fuse to protect your servers from sudden peaks in message traffic that they may not be able to withstand. With the rate limiting, this peak is smoothened and spread over multiple seconds, sending messages at a rate your servers can handle. One important thing to remember with rate limiting, is that if you are limiting to 1,000 messages per second and are consistently scheduled to receive messages above that limit (e.g. 2,000 per second), the queue will get congested and you might receive messages with infinitely increasing delays.

## Setting endpoint rate limits

You can set the rate limit when [creating or updating a webhook endpoint](https://developers.trackunit.com/docs/webhooks-adding-endpoints) it under Administration → Webhooks in the Trackunit Manager.
The settings are located in the "Advanced Configuration" section and the value is the number of messages per second.
