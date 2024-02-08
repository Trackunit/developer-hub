---
title: Event Catalog
category: 652e408346c8860073a6bd12
---
The Event Catalog offers a list of events to which developers can subscribe using webhooks. It encompasses comprehensive documentation for each event, providing both a detailed schema definition and examples.

Find it in the Trackunit Manager by navigating to Administration > Webhooks > Event Catalog

> 🚧 Available to administrators
> 
> Only admin users can access and view the event catalog in the webhooks section

Available events encompass different domains within the Trackunit Iris platform and therefore enable you to create numerous synergies within your business ecosystem.

## Example events available via Webhooks
- alerts.asset.on
- alerts.asset.off
- faults.asset.on
- faults.asset.off
- service-management.service-status.updated
- sites.asset.enter
- sites.asset.leave

![Event Catalog In Manager](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/webhooks/webhooks-event_catalog.png)

## How are events created in Trackunit?

### Alert events
Alert configurations are the rules that determine when alert events are generated for your assets. Learn how to create alerts either via [Trackunit Manager](https://helpcenter.trackunit.com/s/article/How-do-I-work-with-alerts-in-Trackunit-Manager?language=en_US) or via the [Alert Configuration API](https://developers.trackunit.com/reference/alerts). During the configuration of the alert you can choose to specify subscribers for email notifications or save the alert configurations without subscribers. Afterwards you can then set up a webhooks subscription to get all alert events on your account.

### Fault Code / Diagnostic Trouble Code events
You can subscribe to the same fault code events that you can see on your tracked assets in Trackunit Manager.

### Service Management events
If you have acquired a license for [Trackunit's Service Management module](https://helpcenter.trackunit.com/s/article/What-is-Service-Management?language=en_US), then you can set up service plans and assign them to your assets. Events are being created whenever the service status of an asset gets updated.

### Site events
By creating [sites](https://helpcenter.trackunit.com/s/article/How-do-I-work-with-Sites-in-Trackunit-Manager?language=en_US) you can gain an up-to-the-minute view of equipment location and status for your construction sites, depots, workplaces or otherwise defined areas. Once you have defined sites in Trackunit, events get created whenever an asset enters or leaves a site.
