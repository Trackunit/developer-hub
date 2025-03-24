---
title: CAN Faults API v1
type: added
---

Released stable version v1 of CAN Faults API. For more information, see the documentation and introduction of the endpoints.

# REST

Below is a list of all available REST endpoints:

## Faults:

> ➕ POST: /public/api/can-faults/faults

[Get faults](ref:getfaults)

## Faults Summary:

> ➕ POST: /public/api/can-faults/faults-summary

[Get faults summary](ref:getfaultssummary)

## Simulated Fault:

> ➕ GET: /public/api/can-faults/simulated-faults/list

[Get simulatable faults](ref:getsimulatablefaults)

> ➕ GET: /public/api/can-faults/simulated-faults/list/simulated

[Get simulated faults](ref:getsimulatedfaults)

> ➕ POST: /public/api/can-faults/simulated-faults/resolve

[Resolve simulated fault](ref:resolvesimulatedfault)

> ➕ POST: /public/api/can-faults/simulated-faults/send

[Send simulated fault](ref:sendsimulatedfault)

> ➕ GET: /public/api/can-faults/simulated-faults/summary

[Get simulated faults summary](ref:getsimulatedfaultssummary)

## Unit ActiveFault:

[Get unit active faults](ref:getunitactivefaultsbyrequestparams)

> ➕ GET: /public/api/can-faults/get-unit-active-faults

[Get unit active faults](ref:getunitactivefaultsbyrequestbody)

> ➕ POST: /public/api/can-faults/get-unit-active-faults