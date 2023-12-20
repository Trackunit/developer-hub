---
title: Alert API - Introduction
category: 6569a2143ad2da00291b594f
---
The Trackunit Alert API is a REST API that enables customers to create & manage alert configurations for their assets.

> 📘 Subscription requirement 
>
> Accessibility of different capabilities within the Alert API depends on which alert types are included in the customer account's subscription plan.

Alerts allow you to set up powerful notifications based on different trigger conditions. You can use Alerts to notify yourself and others by e-mail or via [Webhooks](https://developers.trackunit.com/docs/webhooks-overview) on important asset events. Overall alerts make it possible to be notified in a timely manner if anything happens to your assets. This is very important as taking timely action on urgent matters can make the difference on a good or a bad resolution.

## Interface & Concepts
For the first release of the public alerts API you will be able to manage your alert configurations with the Create, Read, Update and Delete operations.

Alert configurations are the rules that determine when alerts are generated for your assets. All [alert types] (https://helpcenter.trackunit.com/s/article/How-do-I-work-with-alerts-in-Trackunit-Manager?language=en_US) are available for configuration via this API.

> 🚧 Handling of enums when generating a client
> 
> Be aware when integrating with this API that the enums specified in the [OpenAPI Spec](https://developers.trackunit.com/openapi/6569a2143ad2da00291b594f) should be expected to expand without it being treated as a breaking change.
> 
> This means that when generating a client for this API you should ensure that the client can handle unknown enum values by e.g. defaulting to an unknown enum value.
> 
> An example of how to handle this is how the OpenApi java client generator with the configuration parameter ```enumUnknownDefaultCase``` does it [documentation](https://openapi-generator.tech/docs/generators/java/).

The alert configuration object structure make use of a pattern where for some fields only one of several fields should be set to a non-null value.
When this is the case there will be a ```***Type``` field that is set to indicate which of the field is expected to have a value.
An example of using this structure is the ```configurationDetails``` field which has an object value with several different fields. 
Here only the field that is indicated by the ```alertType```  should be non-null. 
A good way to get a feel for the object structure might be to get your existing alerts through the get all endpoint, and inspect the response.

## Rate Limiting




