---
title: Alerts
category: 6569a2143ad2da00291b594f
---
Alerts is one of the areas of the domain that makes it possible to be notified in a timely manner if anything happens to your assets.
This is very important as taking timely action on urgent matters can make the difference on a good or a bad resolution.

For the first release of the public alerts API you will be able to manage your alert configurations with the Create, Read, Update and Delete operations.

Alert configurations are the rules that determine when alerts are generated for your assets. 
Active alerts can be seen on the event page of asset home, where it is also possible to either dismiss the alert event (this will make it disappear from the attention list),
or resolve the alert event (this will make the asset return to a good criticality state if there are no other active events on the asset).

__NB: Be aware when integrating with this API that the enums specified in the OpenApi spec should be expected to expand without it being treated as a breaking change.__
__This means that when generating a client for this API you should ensure that the client can handle unknown enum values by e.g. defaulting to an unknown enum value.
An example of how to handle this is how the OpenApi java client generator with the configuration parameter ```enumUnknownDefaultCase```.__

The alert configuration object structure make use of a pattern where for some fields only one of several fields should be set to a non-null value.
When this is the case there will be a ```***Type``` field that is set to indicate which of the field is expected to have a value.
An example of using this structure is the ```configurationDetails``` field which has an object value with several different fields. 
Here only the field that is indicated by the ```alertType```  should be non-null. 
A good way to get a feel for the object structure might be to get your existing alerts through the get all endpoint, and inspect the response.






