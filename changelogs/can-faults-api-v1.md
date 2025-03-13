---
title: CAN Faults API v1
type: added
---

Released stable version v1 of CAN Faults API. For more information, see the documentation and introduction of the endpoints.

# REST

Below is a list of all available REST endpoints:

## Faults:

> ➕ POST: /public/api/can-faults/faults

[Get faults](ref:getFaults)

## Faults Summary:

> ➕ POST: /public/api/can-faults/faults-summary

[Get faults summary](ref:getFaultsSummary)

## Simulated Fault:

> ➕ GET: /public/api/can-faults/simulated-faults/list

[Get simulatable faults](ref:getSimulatableFaults)

> ➕ GET: /public/api/can-faults/simulated-faults/list/simulated

[Get simulated faults](ref:getSimulatedFaults)

> ➕ POST: /public/api/can-faults/simulated-faults/resolve

[Resolve simulated fault](ref:resolveSimulatedFault)

> ➕ POST: /public/api/can-faults/simulated-faults/send

[Send simulated fault](ref:sendSimulatedFault)

> ➕ GET: /public/api/can-faults/simulated-faults/summary

[Get simulated faults summary](ref:getSimulatedFaultsSummary)

## Unit ActiveFault:

[Get unit active faults](ref:getUnitActiveFaultsByRequestParams)

> ➕ GET: /public/api/can-faults/get-unit-active-faults

[Get unit active faults](ref:getUnitActiveFaultsByRequestBody)

> ➕ POST: /public/api/can-faults/get-unit-active-faults