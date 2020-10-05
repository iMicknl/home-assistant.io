---
title: Somfy TaHoma
description: Instructions on how to integrate Somfy Tahoma devices with Home Assistant.
ha_category:
  - Hub
  - Alarm
  - Binary Sensor
  - Cover
  - Climate
  - Lock
  - Scene
  - Switch
  - Sensor
ha_release: 0.117
ha_config_flow: true
ha_iot_class: Cloud Polling
ha_codeowners:
  - '@philklei'
  - '@tetienne'
  - '@imicknl'
  - '@vlebourl'
ha_domain: tahoma
---

The `Somfy TaHoma` integration platform is used as an interface to the [tahomalink.com](https://www.tahomalink.com) website. It adds multiple devices from the Somfy TaHoma platform.

## Supported Somfy gateways

- Somfy TaHoma Box
- Somfy Connexoon IO
- Somfy Connexoon RTS

Have a look at the list of [supported Somfy devices](#Supported-Somfy-devices) if you would like to understand which specific devices are supported and how they are mapped in Home Assistant.

## Configuration

Home Assistant offers the Somfy TaHoma integration through Configuration -> Integrations -> Somfy TaHoma. Enter your email address and password for tahomalink.com to configure this integration.

Alternatively, Home Assistant will also load Somfy TaHoma via the configuration.yaml. Add the following to your configuration.yaml file:

```yaml
# Example configuration.yaml entry
tahoma:
  username: YOUR_USERNAME
  password: YOUR_PASSWORD
```

{% configuration %}
username:
  description: Your username for tahomalink.com.
  required: true
  type: string
password:
  description: Your password for tahomalink.com.
  required: true
  type: string
{% endconfiguration %}

## Options

Somfy TaHoma options are configured via Configuration -> Integrations -> Somfy TaHoma -> Options.

### Update Interval

The Somfy TaHoma integration periodically retrieves new events. Change the update interval to a lower value if you want more frequent updates, for example when you also control your devices outside Home Assistant.

## Supported Somfy devices

This integrations doesn't use a hardcoded list of supported devices, but relies on the device category in combination with the available states and commands. The table below shows all supported device types and their mapping in Home Assistant.

| Somfy ui_class / widget      | Home Assistant platform |
| ---------------------------- | ----------------------- |
| AdjustableSlatsRollerShutter | cover                   |
| Alarm                        | alarm_control_panel     |
| AtlanticElectricalHeater     | climate                 |
| AirFlowSensor                | binary_sensor           |
| AirSensor                    | sensor                  |
| Awning                       | cover                   |
| CarButtonSensor              | binary_sensor           |
| ConsumptionSensor            | sensor                  |
| ContactSensor                | binary_sensor           |
| Curtain                      | cover                   |
| DimmerExteriorHeating        | climate                 |
| DoorLock                     | lock                    |
| ElectricitySensor            | sensor                  |
| ExteriorScreen               | cover                   |
| ExteriorVenetianBlind        | cover                   |
| GarageDoor                   | cover                   |
| GasSensor                    | sensor                  |
| Gate                         | cover                   |
| Generic                      | cover                   |
| GenericSensor                | sensor                  |
| HumiditySensor               | sensor                  |
| Light                        | light                   |
| LightSensor                  | sensor                  |
| MotionSensor                 | binary_sensor           |
| MyFoxSecurityCamera          | cover                   |
| OccupancySensor              | binary_sensor           |
| OnOff                        | switch                  |
| Pergola                      | cover                   |
| RainSensor                   | binary_sensor           |
| RollerShutter                | cover                   |
| Screen                       | cover                   |
| Shutter                      | cover                   |
| Siren                        | switch                  |
| SirenStatus                  | binary_sensor           |
| SmokeSensor                  | binary_sensor           |
| SomfyThermostat              | climate                 |
| SunIntensitySensor           | sensor                  |
| SunSensor                    | sensor                  |
| SwimmingPool                 | switch                  |
| SwingingShutter              | cover                   |
| TemperatureSensor            | sensor                  |
| ThermalEnergySensor          | sensor                  |
| VenetianBlind                | cover                   |
| WaterDetectionSensor         | binary_sensor           |
| WaterSensor                  | sensor                  |
| WeatherSensor                | sensor                  |
| WindSensor                   | sensor                  |
| Window                       | cover                   |
| WindowHandle                 | binary_sensor           |

If your device is not visible in the device list of Home Assistant (/config/devices/dashboard), you need to turn on [debug logging](https://www.home-assistant.io/integrations/logger/). Copy the debug string and create a [new issue](https://github.com/home-assistant/core/issues).

`DEBUG (MainThread) [custom_components.tahoma] Unsupported TaHoma device (io:DimmableLightIOComponent - Light - DimmerLight).`

If your device is listed in Home Assistant but not working correctly, copy the device info from the devices page and create a [new issue](https://github.com/home-assistant/core/issues). (e.g. DimmerLight
by Somfy, io:DimmableLightIOComponent)
