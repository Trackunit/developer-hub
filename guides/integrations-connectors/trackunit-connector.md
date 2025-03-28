---
title: Trackunit Connector
category: 652e408346c8860073a6bd12
parentDocSlug: connectors
---

The Trackunit Connector is a powerful tool that integrates all Trackunit APIs and webhooks within [Automation Studio](https://developers.trackunit.com/docs/automation-studio-overview), enabling users to automate workflows and set up alerts based on real-time data. This documentation provides detailed information on how to utilize the Trackunit Connector effectively.

## Getting Started
The Trackunit Connector comes pre-connected in Automation Studio and is immediately availabe to be used in workflow automation recipes.

![Preinstalled Trackunit Connector](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/integrations-connectors/TU-connector-preinstalled.png)

![Trackunit Connector inside workflow automation recipe](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/integrations-connectors/TU-connector-recipe.png)

The Trackunit Connector serves a dual purpose within Automation Studio, functioning as **both a trigger and an action facilitator.** Here’s how each aspect works:

### Trigger

1. **Event-Based Automation:** The Trackunit Connector can listen for specific events or conditions from Trackunit APIs and webhooks. For example, it can trigger workflows based on real-time data changes such as:
 - Equipment location updates (e.g. entering or leaving a site).
 - Alerts for maintenance requirements or fault notifications.
 - Usage thresholds being exceeded (e.g. hours of operation).

2. **Real-Time Response:** This capability allows users to automate responses immediately when predefined conditions are met, ensuring timely actions without manual intervention.

![Trackunit Connector triggers](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/integrations-connectors/TU-connector-triggers.png)

3. **Technical foundation:** The full [Webhooks event catalog](https://developers.trackunit.com/docs/webhooks-event-catalog) is available as triggers in the Trackunit Connector.


### Actions

1. **Executing Tasks**: In addition to triggering workflows, the Trackunit Connector can perform actions based on the data retrieved from Trackunit APIs. Examples include:
 - Automatically updating data records inside Trackunit to remove manual workflows.
 - Updating records in a database or external system based on the information received from Trackunit APIs.
 - Initiating follow-up processes, such as scheduling maintenance or additional alerts when specific conditions arise.

![Trackunit Connector actions](https://cdn.statically.io/gh/trackunit/developer-hub/master/guides/integrations-connectors/TU-connector-actions.png)

2. **Workflow Integration**: Users can design comprehensive workflows that combine multiple actions in response to triggers, enhancing operational efficiency and enabling complex automation scenarios.

3. **Technical foundation:** The full [Iris API suite](https://developers.trackunit.com/reference/iris-api-overview) is available as actions in the Trackunit Connector. For detailed information on individual actions you can review the detailed documentation of each available API endpoint, including request/response structures.

By utilizing the Trackunit Connector as both a trigger and an action facilitator, users can create robust, automated workflows that respond dynamically to their operational needs.
