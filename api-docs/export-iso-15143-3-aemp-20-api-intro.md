---
title: Export ISO 15143-3 (AEMP 2.0) - Introduction
category:
  uri: /branches/1.0/categories/reference/AEMP ISO API
---

Our ISO Export API follows the ISO 15143-3 standard. It provides fleet-wide equipment information.

To ease system integration, additional equipment metadata is available as an optional addition to the ISO standard.

> 📘 Subscription requirement
>
> The snapshot endpoints of the Export ISO 15143-3 API are available to all customers, while the time series endpoints are only available to customers on the **Evolve & Expand** or the **Link, Lift & Leap** subscription packages. Data retention limits follow the chosen subscription package.

## Interface

The API exposes a simple REST interface serving XML or JSON as output formats. You can choose the format by sending your accept header with either application/xml or application/json. XML is the default format.

> ➡️ [OpenAPI Specification for the Export ISO 15143-3 (AEMP 2.0) domain](https://developers.trackunit.com/openapi/aemp-iso-api.json)
>
> Get the OpenAPI Specification (formerly Swagger), which is a standardized format that describes the functionalities, endpoints, parameters, and data models of this API in a JSON file [here](https://developers.trackunit.com/openapi/aemp-iso-api.json).

## Rate Limiting

Requests are rate limited to one request per url (for time series endpoints: per datapoint and equipment) every 15 minutes.

To ease development and support general troubleshooting, a pool of 50 additional requests per url is available on top of the usual rate limit rules.
Each request in the pool becomes available again 30 calendar days after use.

There are also limits on allowed requests per second per customer (ie. includes all API accounts for the same customer):

- 50 requests / 1s to fleet snapshot pages,
- 500 requests / 1s to single-element snapshot endpoint,
- 500 requests / 1s to all time-series endpoints counted together.

## Pagination

The AEMP ISO 15143-3 API implements pagination as described in the ISO15143-3 standard. Response collections are limited to 100 per page. The page number of the first page is always one. Each response contains "Links", which provides navigation to self, prev, next and last page.

```xml
<Links>
  <rel>self</rel>
  <href>https://iris.trackunit.com/public/api/aemp/v2/15143/-3/Fleet/2</href>
</Links>
<Links>
  <rel>next</rel>
  <href>https://iris.trackunit.com/public/api/aemp/v2/15143/-3/Fleet/3</href>
</Links>
<Links>
  <rel>prev</rel>
  <href>https://iris.trackunit.com/public/api/aemp/v2/15143/-3/Fleet/1</href>
</Links>
<Links>
  <rel>last</rel>
  <href>https://iris.trackunit.com/public/api/aemp/v2/15143/-3/Fleet/993</href>
</Links>
```

﻿

## Additional Metadata

As an extension to the ISO standard the client can, by adding addMetadata=true as URL param, request additional metadata containing equipment related IDs used to ease system integration.

```xml
<Metadata>
  <TelematicSerialNumber>927096</TelematicSerialNumber>
  <MachineId>035c52d4-a533-4a83-8687-a5a7489a5af4</MachineId>
  <UnitId>958947</UnitId>
  <ExternalReferenceNumber>ref-927096</ExternalReferenceNumber>
</Metadata>
```

﻿

## Additional Machine Insights

As an extension to the ISO standard Trackunit offers a collection of elements that represent Machine Insights that do not fit in the standard schema. The client can request it by adding addExtendedData=true URL param. _Value_ is deprecated and may be removed in future releases. Specific values like _BatteryPotential_ should instead be used.

```xml XML - Example Elements
<BatteryPotential datetime="2021-01-02T12:22:00Z">
  <BatteryPotential>13.3</BatteryPotential>
  <Value>13.3</Value>
</BatteryPotential>
<CumulativeMovingHours datetime="2021-01-02T12:30:52Z">
  <Hour>21.05</Hour>
  <Value>21.05</Value>
</CumulativeMovingHours>
```
```xml Extension Schema
<xs:complexType name="ExtendedEquipment">
    <xs:sequence>
      <xs:element name="EngineFuelRate" type="EngineFuelRateExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineSpeed" type="SpeedExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineOilPressure" type="PressureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineOilTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineCoolantTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineCoolantLevel" type="LevelExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineExhaustTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="WaterInFuelIndicator" type="WaterInFuelIndicatorExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="HydraulicTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="HydraulicOilLevel" type="LevelExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="BatteryPotential" type="BatteryPotentialExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="SeatBeltSwitch" type="SeatBeltSwitchExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EnginePercentLoadAtCurrentSpeed" type="PercentageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="ActualEnginePercentTorque" type="PercentageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="PitchAngle" type="AngleExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="RollAngle" type="AngleExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselParticulateFilterSootLoadPercent" type="PercentageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselParticulateFilterAshLoadPercent" type="PercentageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselParticulateFilterTimeSinceLastActiveRegeneration" type="AftertreatmentDieselParticulateFilterTimeSinceLastActiveRegenerationExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselParticulateFilterPassiveRegenerationStatus" type="StatusExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselParticulateFilterStatus" type="StatusExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselParticulateFilterActiveRegenerationStatus " type="StatusExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselExhaustFluidTankTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentScrOperatorInducementSeverity" type="AfterTreatmentScrOperatorInducementSeverityExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselExhaustFluidConcentration" type="AftertreatmentDieselExhaustFluidConcentrationExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="DieselParticulateFilterActiveRegenerationInhibitedDueToInhibitSwitch" type="DieselParticulateFilterActiveRegenerationInhibitedDuetoInhibitSwitchExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="PayloadPercentage" type="PercentageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="GeneratorTotalKwHoursExport" type="GeneratorTotalkWHoursExportExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="HydraulicOilFilterRestrictionSwitch" type="HydraulicOilFilterRestrictionSwitchExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="ServiceComponentIdentification" type="ServiceComponentIdentificationExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineFuelDeliveryPressure" type="PressureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineCoolantPressure" type="PressureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="WheelBasedVehicleSpeed" type="SpeedExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="BarometricPressure" type="PressureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AmbientAirTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineIntakeAirTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="RoadSurfaceTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineIntakeManifoldTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineAirFilterDifferentialPressure" type="PressureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="BatteryChargerState" type="StateExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="BatteryChargerPowerLineState" type="StateExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="BatteryChargerOutputVoltage" type="BatteryChargerOutputVoltageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="BatteryChargerOutputCurrent" type="BatteryChargerOutputCurrentExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineTripFuel" type="EngineTripFuelExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselParticulateFilterDifferentialPressure" type="PressureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentDieselParticulateFilterIntakeTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AfterTreatmentExhaustTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AmberWarningLamp" type="StateExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="DieselParticulateFilterLampCommand" type="StateExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineFuelTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineIntakeAirPressure" type="PressureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineIntakeManifoldPressure" type="PressureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineIntercoolerTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineOilLevel" type="PercentageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="EngineTotalIdleFuelUsed" type="FuelUsedExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="ExhaustSystemHighTemperatureLampCommand" type="StateExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="HydraulicPressure" type="PressureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="MalfunctionIndicatorLamp" type="StateExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="ProtectLamp" type="StateExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="RedStopLamp" type="StateExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="TransmissionOilTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="CumulativeProductiveHours" type="CumulativeHoursExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="CumulativeMovingHours" type="CumulativeHoursExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="Speed" type="SpeedExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="OperationStatus" type="StatusExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="CumulativeEngineHours" type="CumulativeHoursExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="PlatformHeightPercent" type="PercentageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="PlatformHeight" type="LengthExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="PlatformElevated" type="StatusExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="Payload" type="PayloadTotalsExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="BatteryStateOfChargePercent" type="PercentageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="BatteryCurrent" type="CurrentExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="BatteryTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL1NeutralRMSVoltage" type="VoltageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL2NeutralRMSVoltage" type="VoltageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL3NeutralRMSVoltage" type="VoltageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL1Frequency" type="FrequencyExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL2Frequency" type="FrequencyExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL3Frequency" type="FrequencyExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL1RMSCurrent" type="CurrentExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL2RMSCurrent" type="CurrentExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL3RMSCurrent" type="CurrentExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL1L2RMSVoltage" type="VoltageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL2L3RMSVoltage" type="VoltageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL3L1RMSVoltage" type="VoltageExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcTotalActivePower" type="PowerExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL1ActivePower" type="PowerExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL2ActivePower" type="PowerExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcPhaseL3ActivePower" type="PowerExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcTotalApparentPower" type="PowerExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcTotalPowerFactor" type="FactorExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="AcTotalReactivePower" type="PowerExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
      <xs:element name="PayloadTemperature" type="TemperatureExtended" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation></xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
  </xs:complexType>

  <xs:complexType name="EngineFuelRateExtended">
    <xs:sequence>
      <xs:element name="EngineFuelRate" minOccurs="0" maxOccurs="1" type="xs:decimal">
      </xs:element>
      <xs:element name="Value" minOccurs="0" maxOccurs="1" type="xs:decimal">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use EngineFuelRate value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="SpeedExtended">
    <xs:sequence>
      <xs:element name="SpeedUnits" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Speed" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Speed value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="PressureExtended">
    <xs:sequence>
      <xs:element name="Pressure" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Pressure value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="TemperatureExtended">
    <xs:sequence>
      <xs:element name="Temperature" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Temperature value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="LevelExtended">
    <xs:sequence>
      <xs:element name="Level" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Level value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="WaterInFuelIndicatorExtended">
    <xs:sequence>
      <xs:element name="WaterInFuelIndicator" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:string" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use WaterInFuelIndicator value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="BatteryPotentialExtended">
    <xs:sequence>
      <xs:element name="BatteryPotential" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use BatteryPotential value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="SeatBeltSwitchExtended">
    <xs:sequence>
      <xs:element name="SeatBeltSwitch" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:string" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use SeatBeltSwitch value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="PercentageExtended">
    <xs:sequence>
      <xs:element name="Percentage" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Percentage value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="AngleExtended">
    <xs:sequence>
      <xs:element name="Angle" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Angle value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="AftertreatmentDieselParticulateFilterTimeSinceLastActiveRegenerationExtended">
    <xs:sequence>
      <xs:element name="AftertreatmentDieselParticulateFilterTimeSinceLastActiveRegeneration" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use AftertreatmentDieselParticulateFilterTimeSinceLastActiveRegeneration value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="StatusExtended">
    <xs:sequence>
      <xs:element name="Status" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:string" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Status value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="AfterTreatmentScrOperatorInducementSeverityExtended">
    <xs:sequence>
      <xs:element name="AfterTreatmentScrOperatorInducementSeverity" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:string" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use AfterTreatmentScrOperatorInducementSeverity value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="AftertreatmentDieselExhaustFluidConcentrationExtended">
    <xs:sequence>
      <xs:element name="AftertreatmentDieselExhaustFluidConcentration" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use AftertreatmentDieselExhaustFluidConcentration value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="DieselParticulateFilterActiveRegenerationInhibitedDuetoInhibitSwitchExtended">
    <xs:sequence>
      <xs:element name="DieselParticulateFilterActiveRegenerationInhibitedDuetoInhibitSwitch" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:string" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use DieselParticulateFilterActiveRegenerationInhibitedDuetoInhibitSwitch value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="GeneratorTotalkWHoursExportExtended">
    <xs:sequence>
      <xs:element name="GeneratorTotalkWHoursExport" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use GeneratorTotalkWHoursExport value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="HydraulicOilFilterRestrictionSwitchExtended">
    <xs:sequence>
      <xs:element name="HydraulicOilFilterRestrictionSwitch" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:string" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use HydraulicOilFilterRestrictionSwitch value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="ServiceComponentIdentificationExtended">
    <xs:sequence>
      <xs:element name="ServiceComponentIdentification" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:string" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use ServiceComponentIdentification value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="StateExtended">
    <xs:sequence>
      <xs:element name="State" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:string" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use State value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="BatteryChargerOutputVoltageExtended">
    <xs:sequence>
      <xs:element name="BatteryChargerOutputVoltage" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use BatteryChargerOutputVoltage value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="BatteryChargerOutputCurrentExtended">
    <xs:sequence>
      <xs:element name="BatteryChargerOutputCurrent" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use BatteryChargerOutputCurrent value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="EngineTripFuelExtended">
    <xs:sequence>
      <xs:element name="EngineTripFuel" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use BatteryChargerOutputCurrent value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="FuelUsedExtended">
    <xs:sequence>
      <xs:element name="FuelUnits" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="FuelConsumed" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use FuelConsumed value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="CumulativeHoursExtended">
    <xs:sequence>
      <xs:element name="Hour" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Hour value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="LocationMetadataExtended">
    <xs:sequence>
      <xs:element name="HighAccuracy" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="AccuracyRadius" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use AccuracyRadius value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="LengthExtended">
    <xs:sequence>
      <xs:element name="Length" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Length value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="PayloadTotalsExtended">
    <xs:sequence>
      <xs:element name="PayloadUnits" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Payload" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Payload value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="CurrentExtended">
    <xs:sequence>
      <xs:element name="Current" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Current value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="VoltageExtended">
    <xs:sequence>
      <xs:element name="Voltage" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Voltage value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="FrequencyExtended">
    <xs:sequence>
      <xs:element name="Frequency" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Frequency value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="PowerExtended">
    <xs:sequence>
      <xs:element name="Unit" type="xs:string" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Power" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Power value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>

  <xs:complexType name="FactorExtended">
    <xs:sequence>
      <xs:element name="Factor" type="xs:decimal" minOccurs="0" maxOccurs="1">
      </xs:element>
      <xs:element name="Value" type="xs:decimal" minOccurs="0" maxOccurs="1">
        <xs:annotation>
          <xs:documentation>This value is deprecated and may be removed in future versions. Please use Factor value instead.</xs:documentation>
        </xs:annotation>
      </xs:element>
    </xs:sequence>
    <xs:attribute name="datetime" type="xs:dateTime" use="required">
    </xs:attribute>
  </xs:complexType>
```

## Constraints

> 🚧 Serial Number
>
> If the equipment's serial number is unavailable then the telematic device's serial number will be inserted into the equipment serial number field. This is subject to change in the future as we apply to the standard.
>
> Please obtain telematic device's serial number from additional metadata to avoid being impacted by future changes.
