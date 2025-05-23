---
title: Bluetooth tag configuration API v1
type: added
---

Released stable version v1 of Bluetooth tag configuration API. For more information, see the documentation and introduction of the endpoints.

# REST

Below is a list of all available REST endpoints:

## KIN Challenge

> ➕ POST: /v1/kin-challenge/sign

[Sign KIN Challenge](ref:signkinchallenge)


## Utilization Profiles

> ➕ POST: /v1/utilization-profiles/search

[Search Utilization Profiles](ref:getutilizationprofiles)

> ➕ GET: /v1/utilization-profiles/{profileId}

[Get Utilization Profile](ref:getutilizationprofile)

> ➕ PUT: /v1/utilization-profiles/{profileId}/acknowledge-desired/{deviceId}

[Acknowledge Desired Utilization Profile](ref:acknowledgebluetoothtagdesiredconfiguration)

> ➕ PUT: /v1/utilization-profiles/{profileId}/acknowledge-reported/{deviceId}

[Acknowledge Reported Utilization Profile](ref:acknowledgebluetoothtagreportedconfiguration)
