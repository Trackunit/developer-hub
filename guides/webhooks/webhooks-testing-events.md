---
title: Testing Events
category:
  uri: /branches/1.0/categories/guides/Integrations & Connectors
---
The easiest way to gain confidence in your endpoint configuration is to start receiving events as quickly as possible.

To send a test event, navigate to your endpoint by clicking it.
![Endpoint overview](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/webhooks/webhooks-endpoint-overview.png)

Next, go to the "Testing" tab. This tab enables you to send an example event to your endpoint to verify that it is connected correctly. Choose the event you want to test and click "Send example."
![Testing-tab](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/webhooks/webhooks-endpoint-testing.png)

The delivery attempt should now appear in the "Attempted Messages" section. If it doesn't, press the refresh button to the right of the "Attempted Messages" title.
![Attempted Messages](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/webhooks/webhooks-endpoint-attempted-delivery.png)

Now, you can check whether the delivery attempt was successful or not. In this case, the specified endpoint does not exist, so the attempt was unsuccessful. By clicking on the "attempted delivery," you can find more details about the failed attempt.
![Unsuccessful Delivery Log](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/webhooks/webhooks-endpoint-unsuccessful-delivery.png)
