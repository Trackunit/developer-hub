---
title: Telematics Device API - Introduction
category: /branches/1.0/categories/reference/Telematics Device
---

The Telematics Device API offers seamless access to a rich array of features meticulously crafted to facilitate device information retrieval and configuration management, enabling effortless maintenance and oversight of a fleet of telematic devices. By leveraging the Telematics Device API, developers gain the ability to programmatically manage their devices, effortlessly update configurations, and track the progress of desired configurations on each device. Moreover, the API provides developers with access to detailed device state documentation, empowering them to identify and explore untapped configuration opportunities

The document is intended for developers, who wants to integrate systems, write client libraries or other interactions on an API-level.

## Example use cases

- Keep an overview of device distribution on your assets --> see [GET list of devices identity](https://developers.trackunit.com/reference/getdeviceidentity)
- Build a UI to change CAN profiles of your devices --> see [GET reported state](https://developers.trackunit.com/reference/getdevicestate) and [UPDATE device state](https://developers.trackunit.com/reference/updatedesiredstate)
- View device state documentation to explore configuration options --> see [GET device documentation](https://developers.trackunit.com/reference/getdocumentation)

## Interface

### Device Identity endpoints

The Device identity endpoints deliver all data related to identity, type, capabilities, and birth certificate of a device. It is typically data that only changes in the start and end of a device lifecycle. It does not include states, configurations or any other device data insights that frequently change (see [Device state](https://developers.trackunit.com/reference/devices-state) endpoints for that).

The Device Identity is a natural starting point for entering the Telematics Device domain.
It currently includes:

- ID
- Serial Number
- Device type
- Production date

### Device State endpoints

The Device state endpoints provide insights about the current state and the desired state after a configuration change for a telematics device. It further enables updating certain device configuration elements to create a new desired state.

The following configuration elements are currently included:

- Bluetooth advertising
- CAN profile
- Input filtering
- Output1 mode

#### Get device state

The telematics device state data includes both **a reported and a desired state**:

- The reported state represents how the device is actually configured.
- Latest configuration attempts of a telematics device will be visible in the desired state. Currently it includes configuration states for the following:
  - Bluetooth advertising
  - CAN profile
  - Input filtering
  - Output1 mode
- The desired and reported state might not show the same. This indicates that the desired state is being synchronised to the telematics device.
- Reported state might also include additional information like:
  - Activity Detection for canbus. This indicates if the Telematics Device has been wired to the canbus and is capable of sending CAN data.

**Illustrative example**

Following is some examples on how the state can be interpreted for a CAN Profile configuration.

```json
{
    "reported": {
        "canbus": {
            "profile": {
                "name": "Profile 1",
                "id": 123
            }
        }
    },
    "desired": {
        "canbus": {
            "profile": {
                "name": "Profile 1",
                "id": 123
            }
        }
    }
}
```

Both the desired and reported state shows the same CAN Profile. This means that the last configured CAN Profile has been successfully deployed to the telematics device.

```json
{
    "reported": {
        "canbus": {
            "profile": {
                "name": "Profile 1",
                "id": 123
            }
        }
    },
    "desired": {
        "canbus": {
            "profile": {
                "name": "Profile 2",
                "id": 456
            }
        }
    }
}
```

The desired and reported state shows a different CAN Profile. This means that the last configured CAN Profile is not the same as the actual CAN Profile on the telematics device. The desired state is still being synchronised and will eventually be deployed to the telematics device.

Be aware that telematics devices might be in areas with no network connectivity or in an operational state where it would be inappropriate to update. In these cases, synchronisations might take hours or even days. There’s no timeout and the telematics device will be updated when possible.

#### Update desired state

Partially update the state of a telematics device by setting a desired state. Partially update means that only configurations in the update will be changed. Any configurations not set will be ignored and remain unchanged. Multiple configurations can be changed in one update.

Currently the configurations are limited to the following but will be expanded over time:

- CAN Profile configuration
- Input filtering configuration
- Set output mode
- Setup Bluetooth advertising

The states that are available for a given telematics device vary by device type, customer and firmware versions. See the [Get desired state documentation](https://developers.trackunit.com/reference/getdocumentation) endpoint to fetch the list of available states for a given telematics device.

**Examples on how to update a desired state of a telematics device**

Configure the CAN Profile to “Profile 1” with id 123:

```json
{
    "desired": {
        "canbus": {
            "profile": {
                "id": 123
            }
        }
    }
}
```

Configure both the CAN Profile and inputFiltering in one update:

```json
{
    "desired": {
        "canbus": {
            "profile": {
                "name": "MPV test 2",
                "id": 329
            }
        },
        "io": {
            "inputFiltering": {
                "enabled": "true"
            }
        }
    }
}
```

Use the [Get device state](https://developers.trackunit.com/reference/getdevicestate) to follow up on the execution.

#### Get desired state

The states that are available for a given telematics device vary by device type, customer and firmware versions. This endpoint can be used to fetch the list of available states for a given telematics device.

It also includes preconditions and available parameters. Below is an example of how to configure the inputFiltering of a Trackunit telematics device:

```json
{
    "io": {
        "inputFiltering": {
            "preconditions": {
                "minimumFirmwareVersion": 62.14
            },
            "parameters": [
                {
                    "name": "enabled",
                    "allowedValues": [
                        false,
                        true
                    ]
                }
            ]
        }
    }
}
```

The required minimum firmware version is 62.14. The configuration has only one property “enabled” that can be set to either “false” or “true”.

Enabling inputFiltering using the template will be to update the desired state with the following:

```json
{
    "desired": {
        "io": {
            "inputFiltering": {
                "enabled": "true"
            }
        }
    }
}
```

See [Update desired state](https://developers.trackunit.com/reference/updatedesiredstate) for more information.

### Device Telemetry endpoint

The Device telemetry endpoint delivers information about the internal state of the device. The details are gathered through multiple channels on the device itself. Telemetry contains values that changes frequently. All metrics regarding power supply, physically wired inputs/outputs and wireless technologies are all considered telemetry. The telemetry provided is always the latest values received from the device.

The following pieces of telemetry is currently supported:

- Power (External, Internal)
- Connectivity (GPS, GSM, Bluetooth)
  - Bluetooth available only for `KIN`, `KIN2`, and `BLUETOOTH_TAG` devices
- IO (Inputs, Output)
- Sensors (External sensor information)

**Example**

Below is an example response from the telemetry endpoint:

```json

{
    "id": "cc11a6ac-3758-44ce-9cb0-b9414be36b7e",
    "power": {
       "external": {
           "supply": 12000
       },
       "internal": {
           "supply": 4145,
           "percentage": 95,
           "charging": false
       }
    },
    "connectivity": {
       "gps": {
           "satellites": 8,
           "signalQuality": 32,
           "latestFixTime": "2023-08-02T19:07:40Z"
       },
       "gsm": {
           "signalQuality": 4,
           "networkTechnology": "NW_TECH_4G"
       },
       "transmissions": {
           "latestReceptionTime": "2023-08-02T19:08:50Z"
       },
       "bluetooth": {
         "rssi": -65,
         "latestBluetoothReceptionTime": "2023-08-02T19:09:20Z"
       }
    },
    "io": {
       "input1": {
           "active": true,
           "voltage": 12108
       },
       "input2": {
           "active": true,
           "voltage": 12056
       },
       "input3": {
           "active": false,
           "voltage": 0
       },
       "input4": {
           "active": false,
           "voltage": 0
       },
       "output1": {
           "active": false,
           "loadDetect": true
       }
    },
    "sensor": {
       "temperature1": {
          "value": 20.5
       },
       "temperature2": {
          "value": 12.7
       },
       "light": {
           "active": false
       }
    }
}
```
