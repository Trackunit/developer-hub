---
title: Machine Insights Streaming Dataformat
category: 62fbabf8d9095e057cc1cd2c
parentDocSlug: streaming-api
---
The Machine Insights based streaming dataformat provides high-level semantic information about machines. This means that e.g. information about "Operating Hours", "Fuel Remaining in Tank", "DEF Level" and "Battery Voltage" are immediately present in a normalized format - no matter the input source. This is perfectly tailored towards usage in a datalake or in AI-based analytics.

> 📘 All datafields are optional
>
> For the same machine some might be filled out in one message while others are filled out in the next message; which fields are filled out depends on the technical details of the datacollection. The interpretation should always be that the individual datapoint was provided at that individual timestamp.

Data is in general in-order, that is most recent datapoint last, but this is not guaranteed. If the most recent data is needed the timestamps should be compared. Any processing of historic data should be prepared to receive and handle data out of order.

## Header and Metadata information

Metadata about the machine itself is contained in the field EquipmentHeader, with the following fields:

| Field               | Example             | Description                                                                                                                                |
|:--------------------|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| UnitInstallDateTime | 1604042795000       | [Unix timestamp](https://en.wikipedia.org/wiki/Unix_time) in milliseconds at which point the telematics unit was installed on the machine. |
| OEMName             | "Red Tractors"      | The brand name of the machine.                                                                                                             |
| Model               | "F6000"             | The model name of the machine.                                                                                                             |
| EquipmentID         | "My Red F6000"      | The name given to the machine by the customer account.                                                                                     |
| SerialNumber        | "1GCHC33N7RJ376544" | The serial number given to the machine - currently the same as the PIN.                                                                    |
| PIN                 | "1GCHC33N7RJ376544" | The PIN given to the machine.                                                                                                              |

Metadata about the telematics device, and further links into the Trackunit APIs is given in the field Metadata:

| Field                   | Example                                | Description                                                                     |
|:------------------------|:---------------------------------------|:--------------------------------------------------------------------------------|
| TelematicSerialNumber   | "1234568"                              | The serial number of the telematics device.                                     |
| MachineId               | "60b1b9ab-1902-4e43-adfd-fc8f29acd838" | The UUID assigned to the machine within Trackunit's systems.                    |
| UnitId                  | 87654321                               | The UnitID assigned to the telematics unit within Trackunit's systems.          |
| ExternalReferenceNumber | Customer-assigned                      | The external reference number assigned to this machine by the customer account. |

In general the MachineId is used to navigate to the various [Iris APIs]([https://dev.trackunit.com/docs/introduction-1]), while the UnitId can be used to access the [Classic APIs](https://dev.trackunit.com/docs/trackunit-api).

## Location and LocationAddress

The fields Location and LocationAddress contain the position, and the approximate street address of the machine at the given time.

## Location

| Field                    | Example       | Description                                                                                                     |
|:-------------------------|:--------------|:----------------------------------------------------------------------------------------------------------------|
| Latitude                 | 57.048273     | Latitude of the location.                                                                                       |
| Longitude                | 9.947384      | Longitude of the location.                                                                                      |
| Altitude (optional)      | 17            | Altitude of the location, or null.                                                                              |
| Altitudeunits (optional) | "metres"      | Units of the altitude (always normalized to "metres"), or null.                                                 |
| datetime                 | 1604042795000 | [Unix timestamp](https://en.wikipedia.org/wiki/Unix_time) in milliseconds, for when this location was recorded. |

## LocationMetadata

Contains additional information about the Location.

| Field                     | Example | Description                                                                                                                     |
|:--------------------------|:--------|:--------------------------------------------------------------------------------------------------------------------------------|
| AccuracyRadius (optional) | 10.0    | Accuracy of the location defined as a radius in metres. Corresponds to the Estimated Horizontal Position Error (EHPE) from GPS. |
| HighAccuracy (optional)   | true    | The location in com.aemp20.Location has high accuracy                                                                           |

## LocationAddress

Contains the approximate street address of the given Location.

| Field              | Example          | Description                                                          |
|:-------------------|:-----------------|:---------------------------------------------------------------------|
| Country (optional) | "Denmark"        | Country of the location.                                             |
| Zipcode (optional) | "9000"           | Zipcode of the location.                                             |
| City (optional)    | "Aalborg"        | City of the location.                                                |
| Address (optional) | "Gasværksvej 24" | Street address of the location.                                      |
| GeoHash (optional) | "u4phd376qbg5"   | [GeoHash](https://en.wikipedia.org/wiki/Geohash) of the location.    |
| datetime           | 1604042795000    | Unix timestamp in milliseconds, for when this location was recorded. |

## AccessControlKeyUsage

> 📘 Coming soon to Streaming API
> 
> This field will be available in Streaming API in July 2023.

The field AccessControlKeyUsage contains information about an access operation for a machine. Relaying information about who initiated the operation, which key was used and if the operation was succesful.

[block:parameters]
{
  "data": {
    "h-0": "Field",
    "h-1": "Example",
    "h-2": "Description",
    "0-0": "OperatorId (optional)",
    "0-1": "\"60b1b9ab-1902-4e43-adfd-fc8f29acd838\"",
    "0-2": "Id of the operator performing the operation, if identifiable.",
    "1-0": "KeyId (optional)",
    "1-1": "\"84c63030-00a2-4b90-81bd-e63ee18751e8\"",
    "1-2": "Id of the key used in the operation, if identifiable.",
    "2-0": "Operation",
    "2-1": "\"LOCK\"  \n\"UNLOCK",
    "2-2": "The type of operation performed.",
    "3-0": "AccessType",
    "3-1": "\"DIGITAL_KEY\"  \n\"ROLLING_PIN",
    "3-2": "The type of access used for the operation. This can be on of DIGITAL_KEY, ROLLING_PIN, STATIC_PIN, KEY_CARD, KEYPAD_USE",
    "4-0": "Success",
    "4-1": "true",
    "4-2": "Boolean value for whether the operation was successful.",
    "5-0": "datetime",
    "5-1": "1604042795000",
    "5-2": "[Unix timestamp](https://en.wikipedia.org/wiki/Unix_time) in milliseconds, for when this operation was recorded."
  },
  "cols": 3,
  "rows": 6,
  "align": [
    "left",
    "left",
    "left"
  ]
}
[/block]

## Hours: CumulativeOperatingHours, CumulativeIdleHours, ...

In general, the field CumulativeOperatingHours is the most interesting: this is the total amount of hours for the machine. Other fields might be present as well, if those datapoints are available for this machine, such as CumulativeIdleHours, CumulativeIdleNonOperatingHours, CumulativeProductiveHours, CumulativeMovingHours, etc. The general format of the Hours fields is:

| Field    | Example       | Description                                                                                                      |
|:---------|:--------------|:-----------------------------------------------------------------------------------------------------------------|
| Hour     | 42.12         | Decimal amount of hours.                                                                                         |
| datetime | 1604042795000 | [Unix timestamp](https://en.wikipedia.org/wiki/Unix_time) in milliseconds, for when this datapoint was recorded. |

## Machine Insights

The main fields (around 80 in total) all describe some aspect of semantic data about a machine: FuelRemaining, EngineStatus, Distance travelled, etc. The availability of these datapoints will vary depending on the source of the telematic data (be it GPS, CAN-bus, ISO feed, etc.). The unit of measurement for each datapoint will always be the same, i.e., the unit for Distance will always be "km" for kilometres. The general format of the machine insights is, with varying field names:

[block:parameters]
{
"data": {
"h-0": "Field",
"h-1": "Example",
"h-2": "Description",
"0-0": "Field with value (naming varies)",
"0-1": "13.8  \ntrue",
"0-2": "The value of the datapoint itself. Floating point or boolean.",
"1-0": "unit (naming sometimes varies)",
"1-1": "\"km\"  \n\"volt\"",
"1-2": "The unit of measurement for this dataseries. Will always stay the same for the same field.",
"2-0": "datetime",
"2-1": "1604042795000",
"2-2": "[Unix timestamp](https://en.wikipedia.org/wiki/Unix_time) in milliseconds, for when this datapoint was recorded."
},
"cols": 3,
"rows": 3,
"align": [
"left",
"left",
"left"
]
}
[/block]

For the exact semantics and availability of these datapoints, please see the [data model description.](https://dev.trackunit.com/docs/trackunit-data-model)

## CANMessages

> 📘 This is probably not the data you are looking for
>
> In general most of the CAN data has been interpreted to Machine Insights by Trackunit, and it should only be necessary to look at the CANMessages themselves if something particular is needed. CANMessages are not normalized, and not data cleansed to the same degree.  
> You are probably looking for one of the other fields.

CAN messages is data directly from the CAN bus of the machine. In general a working knowledge of the CAN bus, and sometimes the specific CAN bus of a machine, is needed to interpret this data. The CANMessages field is an array, where each element has the following format:

[block:parameters]
{
"data": {
"h-0": "Field",
"h-1": "Example",
"h-2": "Description",
"0-0": "datetime",
"0-1": "1604042795000",
"0-2": "[Unix timestamp](https://en.wikipedia.org/wiki/Unix_time) in milliseconds, for when this datapoint was recorded.",
"1-0": "UnitOfMeasurement",
"1-1": "\"%\"  \n\"rpm\"",
"1-2": "The unit of measurement, as specified in the CAN profile; not normalized.",
"2-0": "VariableId",
"2-1": "212",
"2-2": "The internal Trackunit VariableId for this dataitem.",
"3-0": "VariableName",
"3-1": "\"Engine Speed\"",
"3-2": "The name corresponding to the VariableId.",
"4-0": "ParsedValue",
"4-1": "1234.5678  \n\"the value\"",
"4-2": "The parsed value; either a double or a string."
},
"cols": 3,
"rows": 5,
"align": [
"left",
"left",
"left"
]
}
[/block]

More detail about the value collected is available in the "CanMessageValues" field which can be one of these types:

[block:parameters]
{
"data": {
"h-0": "Type",
"h-1": "Fields",
"h-2": "Description",
"0-0": "CanMessageValue",
"0-1": "value",
"0-2": "A single value was picked up in the capturing interval.",
"1-0": "CanMessageMinMax",
"1-1": "MinValue  \nMaxValue",
"1-2": "A minimum and maximum value was picked up in the capturing interval.",
"2-0": "CanMessageAccumulated",
"2-1": "value",
"2-2": "The sum of all observed values in the capturing interval was picked up."
},
"cols": 3,
"rows": 3,
"align": [
"left",
"left",
"left"
]
}
[/block]

More details about how the data was picked is available in the "CanMessageData" field, which has the following subfields:

[block:parameters]
{
"data": {
"h-0": "Field",
"h-1": "Example",
"h-2": "Description",
"0-0": "CanId",
"0-1": "217056257",
"0-2": "The CAN identifier of the data that was picked up.",
"1-0": "SourceAddress",
"1-1": "0",
"1-2": "The CAN source address of the data that was picked up.",
"2-0": "BinaryValue",
"2-1": "-",
"2-2": "The bits themselves that was picked up.",
"3-0": "Counter",
"3-1": "1234",
"3-2": "The number of data items that where seen in the capturing period matching this CAN data item.",
"4-0": "CapturingPeriod",
"4-1": "120",
"4-2": "The number of seconds the capturing period lasted.",
"5-0": "CanType",
"5-1": "\"Can A\"  \n\"Can B\"",
"5-2": "The type of CAN bus."
},
"cols": 3,
"rows": 6,
"align": [
"left",
"left",
"left"
]
}
[/block]

## FaultCodes

FaultCodes contain an array of faults that occured on a machine; typically because it was present on the CAN bus, but could also be imported from an ISO feed, or similar. Each element has the following fields:

[block:parameters]
{
"data": {
"h-0": "Field",
"h-1": "Example",
"h-2": "Description",
"0-0": "CodeIdentifier",
"0-1": "\"1234-56\"  \n\"Free text\"",
"0-2": "The identifier for the fault; for CAN errors this will normally be \"SPN-FMI\", but for other sources this is entirely free text.",
"1-0": "CodeDescription",
"1-1": "\"Engine Fuel Delivery Pressure too low\"",
"1-2": "The interpretation of the fault that Trackunit knows and shows in Manager.",
"2-0": "CodeSeverity",
"2-1": "\"67\"  \n\"Low\", \"High\", \"Free text\"",
"2-2": "The severity of the fault; if originating from a Trackunit device it will be between 0 and 100; from other sources this can be free text.",
"3-0": "CodeSource",
"3-1": "\"0\"  \n\"Engine\"",
"3-2": "The source where the fault originates from; for CAN errors this will normally be the CAN source address; from other sources this can be free text.",
"4-0": "datetime",
"4-1": "1604042795000",
"4-2": "[Unix timestamp](https://en.wikipedia.org/wiki/Unix_time) in milliseconds, for when this fault started appearing.",
"5-0": "datetimeCleared",
"5-1": "null  \n1604046795000",
"5-2": "[Unix timestamp](https://en.wikipedia.org/wiki/Unix_time) in milliseconds, for when this fault stopped appearing, or null if still present or unknown.  \nFor CAN errors there will normally be one message with datetimeCleared = null, followed at a later time by a message with datetimeCleared != null. From outher sources, this behaviour is not guaranteed."
},
"cols": 3,
"rows": 6,
"align": [
"left",
"left",
"left"
]
}
[/block]

## Trackunit Kin

For messages related to Trackunit Kin tags, EquipmentHeader contains asset data on which the Kin tag is onboarded. Metadata consists of Kin serial number and asset ID (as MachineId field).
