---
title: Available events
category: /branches/1.0/categories/guides/Integrations & Connectors
---
The Event Catalog offers a list of events to which developers can subscribe using webhooks. It encompasses comprehensive documentation for each event, providing both a detailed schema definition and examples.

Find it in the Trackunit Manager by navigating to Administration > Webhooks > Event Catalog or [here on developer hub](https://developers.trackunit.com/page/webhook-event-catalog).

> 🚧 Available to administrators
>
> Only admin users can access and view the event catalog in the webhooks section

Available events encompass different domains within the Trackunit Iris platform and therefore enable you to create numerous synergies within your business ecosystem.

## How are events created in Trackunit?

### Alert events
Alert configurations are the rules that determine when alert events are generated for your assets. Learn how to create alerts either via [Trackunit Manager](https://help.trackunit.com/en/articles/137636-how-do-i-work-with-alerts-in-trackunit-manager) or via the [Alert Configuration API](https://developers.trackunit.com/reference/alerts). During the configuration of the alert you can choose to specify subscribers for email notifications or save the alert configurations without subscribers. Afterwards you can then set up a webhooks subscription to get all alert events on your account.

> ℹ️ Trigger settings: critical alert vs. log
>
> Be aware that some alert types have different trigger settings, which causes different event types to be produced. Choosing the trigger type "critical alert" will create an alerts.asset.on as well as an alerts.assets.off event once the alert has been resolved. The trigger type "log" will only create an alerts.assets.off event, because "log " is to be understood as a mechanism to register that an event was “triggered”, but it is not important to keep the machine in a critical state by registering an alerts.asset.on event.

### Fault Code / Diagnostic Trouble Code events
You can subscribe to the same fault code events that you can see on your tracked assets in Trackunit Manager.

### Service Management events
If you have acquired a license for [Trackunit's Service Management module](https://help.trackunit.com/en/articles/139653-what-is-service-management), then you can set up service plans and assign them to your assets. Events are being created whenever the service status of an asset gets updated.

### Site events
By creating [sites](https://help.trackunit.com/en/articles/138504-how-do-i-work-with-sites-in-trackunit-manager) you can gain an up-to-the-minute view of equipment location and status for your construction sites, depots, workplaces or otherwise defined areas. Once you have defined sites in Trackunit, events get created whenever an asset enters or leaves a site.
