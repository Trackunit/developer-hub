---
title: Retry Schedule
category: 652e408346c8860073a6bd12
---

A retry schedule for webhooks is a predefined strategy that governs how and when failed webhook delivery attempts are retried. When a webhook delivery fails due to factors such as network issues, server errors, or timeouts, the retry schedule determines the timing and frequency of subsequent retry attempts.

## Trackunit's Retry Schedule
Trackunit attempts to deliver each webhook message based on a retry schedule with exponential backoff.
Each message is therefore attempted based on the following schedule, where each period is started following the failure of the preceding attempt:

- Immediately
- 5 seconds
- 5 minutes
- 30 minutes
- 2 hours
- 5 hours
- 10 hours
- 10 hours (in addition to the previous)

As an example, this means that an attempt that fails three times before eventually succeeding will be delivered roughly 35 minutes and 5 seconds following the first attempt.

## Failed delivery handling & manual retries

After the conclusion of the above attempts the message will be marked as 'Failed' for this endpoint, and you will get a webhook of type 'message.attempt.exhausted' notifying you of this error.

You can then use the interface under Administration → Webhooks in the Trackunit Manager to [manually replay each message](https://developers.trackunit.com/docs/webhooks-replaying-messages) at any time, or automatically retry / recover all failed messages starting from a given date.
