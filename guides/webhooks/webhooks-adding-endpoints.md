---
title: Adding Endpoints
category: 652e408346c8860073a6bd12
---
To get started listening to events on the Iris Platform, all you have to do is configure your endpoints. 

Adding an endpoint is as simple as providing a URL that you control and a list of event types that you want to listen to.

> 🚧 Available to administrators
>
> Only admin users can access and add endpoints through the webhooks section

## Basic Steps

Follow these basic steps to add a new webhook endpoint.

Find the "Webhooks" page under Administration → Webhooks.
![Administration menu](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/webhooks/webhooks-administration-menu.png)

Create a new endpoint by clicking "Add endpoint"
![Add Endpoint](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/webhooks/webhooks-add-endpoint.png)

Enter the URL for your callback endpoint and specify the events you want to subscribe to. If no filters are added, all events will be sent to the endpoint.
![New Endpoint](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/webhooks/webhooks-new-endpoint.png)

The final step is to click "Create", and then you've successfully set up your first webhook subscription.