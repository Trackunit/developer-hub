---
title: Securing Webhooks
category:
  uri: /branches/1.0/categories/guides/Integrations & Connectors
---
Due to the nature of webhooks, attackers can potentially impersonate services by sending fake webhooks to an endpoint. Consider this: it's simply an HTTP POST from an unknown source. This poses a security risk for many applications or, at the very least, introduces potential issues.

To address this, every webhook, along with its metadata, is signed with a unique key for each endpoint. This signature can be used to verify that the webhook indeed originates from us, and it should only be processed if valid.

Another security concern is the possibility of replay attacks. A replay attack occurs when an attacker intercepts a valid payload (including the signature) and retransmits it to your endpoint. This payload would pass signature validation and, therefore, be acted upon.

To mitigate this, a timestamp indicating when the webhook attempt occurred is included. Our libraries automatically reject webhooks with timestamps more than five minutes away (past or future) from the current time. This requires your server's clock to be synchronized and accurate, and we recommend using NTP to achieve this.

Trackunit utilizes the Svix webhooks platform to manage and send your webhooks. Svix is a leading webhooks platform that ensures the secure and reliable delivery of your webhooks.

For detailed information on how to use Svix libraries to verify incoming webhooks, please refer to their documentation [here](https://docs.svix.com/receiving/verifying-payloads/how).
