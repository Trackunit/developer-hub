---
title: Data Model
category: 6295ae369ba4b1001464c9e5
---
Trackunit's data model is semantically defined datapoints called machine insights, each of them capturing some insight into a machine or asset. This means that no matter the connectivity of the machine (be it directly through Trackunit or e.g. an ISO feed) the data model is the same, whereas the datapoints available for each machine may vary.

Each machine insight has a distinct definition, such that machine insights can be used across an entire fleet. Each machine insight is always normalised to a specific unit of measurement, typically an SI-unit.

## Machine Insights

### CumulativeOperatingHours

 The cumulative operating hours of the asset. For machines this corresponds to the engine hour meter.  
Unit of measurement: _hours._

### EngineFuelRate

 Fuel rate of engine fuel consumption.  
Unit of measurement: _litres per hour._

### EngineSpeed

 Engine speed as measured in revolutions per minute of the engine crankshaft.  
Unit of measurement: _revolutions per minute._

### EngineOilPressure

 The pressure of the oil inside the engine.  
Unit of measurement: _kilopascal._

### EngineOilTemperature

 The temperature of the oil inside the engine.  
Unit of measurement: _degrees Celsius._

### EngineCoolantTemperature

 The temperature of the coolant fluid inside the engine.  
Unit of measurement: _degrees Celsius._

### EngineCoolantLevel

 The relative fill level of the coolant fluid used in the engine.  
Unit of measurement: _percent._

### EngineExhaustTemperature

 The temperature of the exhaust as measured inside the engine.  
Unit of measurement: _degrees Celsius._

### FuelLevel

 The relative fill level of the fuel tank of the machine.  
Unit of measurement: _percent._

### WaterInFuelIndicator

 Whether water is present in the fuel or not.  
Unit of measurement: _Boolean._

### HydraulicTemperature

 The temperature of the hydraulic system.  
Unit of measurement: _degrees Celsius._

### HydraulicOilLevel

 The relative fill level of the oil used in the hydraulic system.  
Unit of measurement: _percent._

### BatteryPotential

 The electric potential available in the machine's battery, typically the starter battery.  
Unit of measurement: _volt._

### SeatBeltSwitch

 Whether the seat belt is buckled in or not.  
Unit of measurement: _Boolean._

### EnginepercentLoadAtCurrentSpeed

 The relative load of the engine at the current engine speed.  
Unit of measurement: _percent._

### PitchAngle

 The pitch angle of the asset, typically as measured from front to back of the asset. Perpendicular to the roll angle.  
Unit of measurement: _degrees._

### RollAngle

 The roll angle of the asset, typically as measured from side to side of the asset. Perpendicular to the pitch angle.  
Unit of measurement: _degrees._

### EngineTotalFuelUsed

 The total amount of fuel used by the machine's engine in its lifetime.  
Unit of measurement: _litres._

### AfterTreatmentDieselParticulateFilterSootLoadpercent

 The relative load of soot in the machine's diesel particulate filter.  
Unit of measurement: _percent._

### AfterTreatmentDieselParticulateFilterAshLoadpercent

 The relative load of ash in the machine's diesel particulate filter.  
Unit of measurement: _percent._

### AfterTreatmentDieselParticulateFilterTimeSinceLastActiveRegeneration

 The time since the last active regeneration of the machine's diesel particulate filter.  
Unit of measurement: _seconds._

### AfterTreatmentDieselParticulateFilterPassiveRegenerationStatus

 Whether passive regeneration of the machine's diesel particulate filter is happening, or not.  
Unit of measurement: _Boolean._

### AfterTreatmentDieselParticulateFilterActiveRegenerationStatus

 Whether active regeneration of the machine's diesel particulate filter is happening (or possibly inhibited), or not.  
Unit of measurement: _Boolean._

### AfterTreatmentDieselParticulateFilterStatus

 Whether regeneration of the machine's diesel particulate filter is needed, or not.  
Unit of measurement: _Boolean._

### AfterTreatmentDieselExhaustFluidTankLevel

 The relative fill level of the machine's diesel exhaust fluid tank.  
Unit of measurement: _percent._

### AfterTreatmentDieselExhaustFluidTankTemperature

 The temperature of the machine's diesel exhaust fluid tank.  
Unit of measurement: _degrees Celsius._

### AfterTreatmentDieselExhaustFluidConcentration

 The relative concentration of the fluid in the machine's diesel exhaust fluid tank.  
Unit of measurement: _percent._

### DieselParticulateFilterActiveRegenerationInhibitedDueToInhibitSwitch

 Whether regeneration of the machine's diesel particulate filter is being inhibited by an operator switch.  
Unit of measurement: _Boolean._

### Payloadpercentage

 The relative payload of the machine, relative to the rated limit.  
Unit of measurement: _percent._

### GeneratorTotalKwHoursExport

 Cumulative exported energy of a generator.  
Unit of measurement: _kilowatt-hours._

### HydraulicOilFilterRestrictionSwitch

 Whether the flow of oil in the hydraulic system is restricted by a clogged oil filter.  
Unit of measurement: _Boolean._

### TotalVehicleDistance

 The total distance travelled by the machine.  
Unit of measurement: _Kilometre._

### TotalPowerTakeOffHours

 The cumulative time the machine has been driving an implement through a power take-off.  
Unit of measurement: _seconds._

### Altitude

 The altitude of the asset above mean sea level.  
Unit of measurement: _metres._

### EngineFuelDeliveryPressure

 The pressure with which fuel is being delivered to the engine.  
Unit of measurement: _kilopascal._

### EngineCoolantPressure

 The pressure of coolant fluid inside the engine.  
Unit of measurement: _kilopascal._

### WheelBasedVehicleSpeed

 The speed of the machine as calculated at the wheels.  
Unit of measurement: _kilometres per hour._

### BarometricPressure

 The pressure of the ambient atmosphere.  
Unit of measurement: _kilopascal._

### AmbientAirTemperature

 The temperature of the ambient atmosphere.  
Unit of measurement: _degrees Celsius._

### EngineIntakeAirTemperature

 The temperature of the air as measured at the engine intake.  
Unit of measurement: _degrees Celsius._

### RoadSurfaceTemperature

 The temperature of the road surface.  
Unit of measurement: _degrees Celsius._

### EngineIntakeManifoldTemperature

 The temperature of the air as measured at the engine intake manifold.  
Unit of measurement: _degrees Celsius._

### EngineAirFilterDifferentialPressure

 The difference in air pressure as measured across the engine air filter.  
Unit of measurement: _kilopascal._

### CumulativeIdleHours

 The cumulative hours hours the machine has been idle.  
Unit of measurement: _hours._

### BatteryChargerState

 Whether the battery charger is charging the machine's battery or not.  
Unit of measurement: _Boolean._

### BatteryChargerPowerLineState

 Whether the battery charger is connected to a powerline or not.  
Unit of measurement: _Boolean._

### BatteryChargerOutputvoltage

 The output voltage of the battery charger.  
Unit of measurement: _volt._

### BatteryChargerOutputCurrent

 The output current of the battery charger.  
Unit of measurement: _ampere._

### EngineTripFuel

 Fuel consumed by the engine since last trip reset.  
Unit of measurement: _litres._

### AfterTreatmentDieselParticulateFilterDifferentialPressure

 The difference in air pressure as measured across the machine's diesel particulate filter.  
Unit of measurement: _kilopascal._

### AfterTreatmentDieselParticulateFilterIntakeTemperature

 The temperature of the air as measured at the intake of the machine's diesel particulate filter.  
Unit of measurement: _degrees Celsius._

### AfterTreatmentExhaustTemperature

 The temperature of the exhaust air of the machine's diesel particulate filter.  
Unit of measurement: _degrees Celsius._

### EngineFuelTemperature

 The temperature of the fuel inside the engine.  
Unit of measurement: _degrees Celsius._

### EngineIntakeAirPressure

 The pressure of the air as measured at the engine intake.  
Unit of measurement: _kilopascal._

### EngineIntakeManifoldPressure

 The pressure of the air as measured at the engine intake manifold.  
Unit of measurement: _kilopascal._

### EngineIntercoolerTemperature

 The temperature of the engine intercooler.  
Unit of measurement: _degrees Celsius._

### EngineOilLevel

 The relative fill level of the oil used in the engine.  
Unit of measurement: _percent._

### EngineTotalIdleFuelUsed

 The total amount of fuel used by the machine while idling.  
Unit of measurement: _litres._

### ExhaustSystemHighTemperatureLampCommand

 Whether the exhaust temperature is too high.  
Unit of measurement: _Boolean._

### HydraulicPressure

 The pressure delivered by the hydraulic system.  
Unit of measurement: _kilopascal._

### TransmissionOilTemperature

 The temperature of the oil inside the transmission.  
Unit of measurement: _degrees Celsius._

### AverageLoadFactorLast_24Hours

 The average load factor of the asset over the last 24 hours, compared to the rated output.  
Unit of measurement: _percent._

### CumulativeActiveRegenerationHours

 The cumulative hours the machine has spent actively regenerating the machine's diesel particulate filter from soot particles.  
Unit of measurement: _hours._

### CumulativeIdleNonOperatingHours

 The cumulative hours the machine has spent with the engine running, but without any operator inputs.  
Unit of measurement: _hours._

### CumulativeLoadCount

 The cumulative number of loads the machine has performed.  
Unit of measurement: _count._

### CumulativePayloadTotals

 The cumulative total of all payloads the machine has performed.  
Unit of measurement: _kilogram._

### EngineStatus

 Whether the engine is running, or not.  
Unit of measurement: _Boolean._

### FuelUsedLast_24Hours

 The total amount of fuel used by the machine in the last 24 hours.  
Unit of measurement: _litres._

### MaximumSpeedLast_24Hours

 The maximum speed the machine attained in the last 24 hours.  
Unit of measurement: _kilometres per hour._

### FuelTankCapacity

 The total capacity of the machine's fuel tank.  
Unit of measurement: _litres._

### CumulativeProductiveHours

 Cumulative number of hours the Machine has been productive.  
Unit of measurement: _hours._

### CumulativeMovingHours

 Cumulative number of hours where the Equipment has been moving/driving, e.g. as registered by the Gps unit.  
Unit of measurement: _hours._

### Speed

 Speed of the machine (car/vehicle,equipment,boat,etc) regardless of moving by its own power or something else is moving it.  
Unit of measurement: _kilometres per hour._

### OperationStatus

 Whether the machine/asset is operating, or not.  
Unit of measurement: _Boolean_.

### CumulativeEngineHours

 The cumulative hours the engine of the asset has been running.  
Unit of measurement: _hours_.

### PlatformHeightPercent

 The relative height of the platform or implement of the machine.  
Unit of measurement: _percent_.

### PlatformHeight

 The absolute height of the platform or implement of the machine.  
Unit of measurement: _metres_.

### PlatformElevated

 Whether the platform or implement of the machine is up from the bottom-most position or not.  
Unit of measurement: _Boolean_.

### Payload

 The absolute payload weight on the platform or implement of the machine.  
Unit of measurement: _kilogram_.

### BatteryStateOfChargePercent

 The relative state of charge of the battery.  
Unit of measurement: _percent_.

### BatteryCurrent

 The amount of charge going into (if positive) or out of (if negative) the battery.  
Unit of measurement: _ampere_.

### BatteryTemperature

 The temperature of the battery.  
Unit of measurement: _degrees Celcius_.

### AcPhaseL1NeturalRMSVoltage

 The root mean square (RMS) Voltage measured between phase L1 and neutral.  
Unit of measurement: _volt_.

### AcPhaseL2NeturalRMSVoltage

 The root mean square (RMS) Voltage measured between phase L2 and neutral.  
Unit of measurement: _volt_.

### AcPhaseL3NeturalRMSVoltage

 The root mean square (RMS) Voltage measured between phase L3 and neutral.  
Unit of measurement: _volt_.

### AcPhaseL1Frequency

 The frequency of L1.  
Unit of measurement: _hertz_.

### AcPhaseL2Frequency

 The frequency of L2.  
Unit of measurement: _hertz_.

### AcPhaseL3Frequency

 The frequency of L3.  
Unit of measurement: _hertz_.

### AcPhaseL1RMSCurrent

 The root mean square (RMS) current of L1.  
Unit of measurement: _ampere_.

### AcPhaseL2RMSCurrent

 The root mean square (RMS) current of L2.  
Unit of measurement: _ampere_.

### AcPhaseL3RMSCurrent

 The root mean square (RMS) current of L3.  
Unit of measurement: _ampere_.

### AcPhaseL1L2RMSVoltage

 The root mean square (RMS) Voltage measured between phase L1 and L2.  
Unit of measurement: _volt_.

### AcPhaseL2L3RMSVoltage

 The root mean square (RMS) Voltage measured between phase L2 and L3.  
Unit of measurement: _volt_.

### AcPhaseL3L1RMSVoltage

 The root mean square (RMS) Voltage measured between phase L3 and L1.  
Unit of measurement: _volt_.

### AcTotalActivePower

 The actual total Active Power (W) output on all 3 phases. Active Power (a.k.a. Real Power) is measured (not calculated) and reflects the actual energy consumption per time unit (1W = 1Joule/s), for a purely resistive load it is the same as Volt \* Amp, but for many AC systems it is NOT.  
Unit of measurement: _watt_.

### AcPhaseL1ActivePower

 The Active Power (W) output on phase L1. Active Power (a.k.a. Real Power) is measured (not calculated) and reflects the actual energy consumption per time unit (1W = 1Joule/s), for a purely resistive load it is the same as Volt \* Amp, but for many AC systems it is NOT.  
Unit of measurement: _watt_.

### AcPhaseL2ActivePower

 The Active Power (W) output on phase L2. Active Power (a.k.a. Real Power) is measured (not calculated) and reflects the actual energy consumption per time unit (1W = 1Joule/s), for a purely resistive load it is the same as Volt \* Amp, but for many AC systems it is NOT.  
Unit of measurement: _watt_.

### AcPhaseL3ActivePower

 The Active Power (W) output on phase L3. Active Power (a.k.a. Real Power) is measured (not calculated) and reflects the actual energy consumption per time unit (1W = 1Joule/s), for a purely resistive load it is the same as Volt \* Amp, but for many AC systems it is NOT.  
Unit of measurement: _watt_.

### AcTotalApparentPower

 The actual total apparent power (VA) output on all 3 phases. Apparent Power is calculated by multiplying phase-to-neutral-Voltage by Current, and if the load is NOT purely resistive the result will be larger than the actual power (W)  
Unit of measurement: _volt-ampere_.

### AcTotalPowerFactor

 The power factor of the total output across all 3 power phases, is typically calculated as total-active-power/total-apparent-power. Power Factor is the relation between Active Power (W) and Apparent Power (VA). For a purely resistive load it is 1, otherwise it is less than 1, but larger than zero.  
Unit of measurement: _not applicable_.

### AcTotalReactivePower

 The actual total Reactive Power (VAr) output on all 3 phases. Is an imaginary number representing then part of Apparent power which does not do any work, or more precisely VAr = sqrt(sqr(VA) - sqr(W)).  
Unit of measurement: _volt-ampere reactive_.

### PayloadTemperature

 The temperature of the payload, e.g. in a cargo compartment.  
Unit of measurement: _degrees Celcius_.

### AcTotalRelativeActivePowerLoadPercentage

Total active power (W) consumption (of the connected load) as a percentage of the rated active power output capability.  
Unit of measurement: _percent_,

### AcTotalRelativeApparentPowerLoadPercentage

Total apparent power (VA) consumption (of the connected load) as a percentage of the rated apparent output capability.  
E.g. a generator is rated to a max continuous power delivery of 120kVA and the actual load is 45kVA then this percentage is 37.5.  
Unit of measurement: _percent_.

### AcTotalRelativeLoadPercentage

Total power load (taking both Actual (W) and Apparent (VA) consumption into consideration) as a percentage of the rated output capability.  
Maximum of `AcTotalRelativeApparentPowerLoadPercentage` and `AcTotalRelativeActivePowerLoadPercentage`, which might not be available when this parameter is available. E.g. a generator is rated to a max continuous power delivery of 100kW/120kVA and the actual load is 40kW/45VA then this percentage is 40.  
Unit of measurement: _percent_.

### AcAveragePhaseToNeutralRmsVoltage

Average of the 3 phase-to-neutral voltages. This is an average of actual values and not an average over time.  
Unit of measurement: _volt_.

### AcAveragePhaseToPhaseRmsVoltage

Average of the 3 phase-to-phase voltages. This is an average of actual values and not an average over time.  
Unit of measurement: _volt_.

### AcAverageRmsCurrent

Average of the 3 individual phase (L1, L2, and L3) currents. This is an average of actual values and not an average over time.  
Unit of measurement: _ampere_.

### Accelerometer_X_Axis

Acceleration (or g-force) measured on the x-axis of an accelerometer (typically placed inside a telematics device).  
Notice: The direction/axis relates to the accelerometer and not the machine, that is, the x-axis of the machine could be something different.  
Unit of measurement: _g-force_.

### Accelerometer_Y_Axis

Acceleration (or g-force) measured on the y-axis of an accelerometer (typically placed inside a telematics device).  
Notice: The direction/axis relates to the accelerometer and not the machine, that is, the y-axis of the machine could be something different.  
Unit of measurement: _g-force_.

### Accelerometer_Z_Axis

Acceleration (or g-force) measured on the z-axis of an accelerometer (typically placed inside a telematics device).  
Notice: The direction/axis relates to the accelerometer and not the machine, that is, the z-axis of the machine could be something different.  
Unit of measurement: _g-force_.

### Impact

Impact (g-force) - could be calculated as the vector length of the three axis accelerometer values (always a positive number), but might come from other sources.  
Unit of measurement: _g-force_.

### AftertreatmentDieselParticulateFilterTimeToNextActiveRegeneration

Time until the next active regeneration of the machine's diesel particulate filter.  
Unit of measurement: _seconds_,

### AftertreatmentSCRTimeSinceLastCleaningEvent

The time since the last cleaning of the machine's Selective Catalytic Reduction unit (SCR).  
Unit of measurement: _seconds_.

### EngineFuelFilterDifferentialPressure

Pressure drop across the fuel filter, which affects the pressure with which fuel is being delivered to the engine.  
Unit of measurement: _kilopascal_.

### EngineOilFilterDifferentialPressure

Pressure drop across the oil filter.  
Unit of measurement: _kilopascal_.

### AcAverageFrequency

Average of the individual phase frequencies. This is an average of actual values and not an average over time.  
Unit of measurement: _hertz_.

### StabilizersDeployed

Whether stabilizing equipment of the machine is deployed or not, examples could be all outrigger legs is lowered to the point where they stabilize/levels the machine, or a pothole protection system is in place.  
Unit of measurement: _Boolean_.

### PlatformStowed

Whether the platform or implement of the machine is stowed, for example, an articulated boom lift has both booms lowered and detracted.  
This is often seen as a safety feature, since some machines are only allowed to drive or transported when the platform is in a stowed position. Other machines has a "high speed" drive which is only enabled when the platform is stowed.  
Unit of measurement: _Boolean_.

### RescueModeActive

Whether the machine is operated in rescue mode or not.  
For instance, a boom lift is turned off but (in order to rescue an operator positioned on the platform) the platform is lowered using the ground control emergency rescue mode.  
Unit of measurement: _Boolean_.

### BatteryStateOfHealthPercent

The relative state of health (SOH) of the battery.   
Actual maximum capacity of the battery (when fully charged) as a percentage of the initial (nominal) capacity.  
Unit of measurement: _percent_.

### BatteryRemainingRunTime

Estimated (actual) remaining run time on battery with respect to the actual charge level and load.  
Also known as "residual time of battery usage"  
Unit of measurement: _seconds_.

### BatteryChargeCyclesCount

The total number of charge cycles the battery has undergone.  
Unit of measurement: _count_.

### BatteryCumulativeDischargedEnergy

Total amount of energy delivered by the battery.  
Unit of measurement: _kilowatt-hours_.

### BatteryRemainingChargeTime

Estimate of how long it will take before the battery is fully charged.  
Unit of measurement: _seconds_.

### BatteryChargerInputVoltage

The input voltage of the battery charger.  
Unit of measurement: _volt_.

### BatteryChargerInputCurrent

The input current of the battery charger.  
Unit of measurement: _ampere_.

### BatteryChargerOutputCurrentLimit

Maximum allowed battery charging current, based on actual operating condition.  
Unit of measurement: _ampere_.

### BatteryChargerInputCurrentLimit

Maximum allowed battery charger input current draw, based on actual operating condition.  
Unit of measurement: _ampere_.

### CumulativeCO2Emissions

The cumulative CO2 emissions (by weight in kg) generated by the asset, either directly emissions by burning fuel or indirectly by consuming electricity (causing emission when generated).  
Unit of measurement: _kilogram_.

### AfterTreatmentDieselParticulateFilterActiveRegenerationState

Indicates the status of diesel particulate filter(s) active regeneration, is a system status and not individual bank status.  
Unit of measurement: _not applicable_.

### AfterTreatmentDieselParticulateFilterState

Indicates the state of the diesel particulate filter(s) regeneration need and urgency, is a system status and not individual bank status.  
Unit of measurement: _not applicable_.
