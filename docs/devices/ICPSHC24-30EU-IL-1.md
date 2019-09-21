---
title: "IKEA ICPSHC24-30EU-IL-1 control via MQTT"
description: "Integrate your IKEA ICPSHC24-30EU-IL-1 via Zigbee2mqtt with whatever smart home
 infrastructure you are using without the vendors bridge or gateway."
---

*To contribute to this page, edit the following
[file](https://github.com/Koenkk/zigbee2mqtt.io/blob/master/docs/devices/ICPSHC24-30EU-IL-1.md)*

# IKEA ICPSHC24-30EU-IL-1

| Model | ICPSHC24-30EU-IL-1  |
| Vendor  | IKEA  |
| Description | TRADFRI driver for wireless control (30 watt) |
| Supports | on/off, brightness |
| Picture | ![IKEA ICPSHC24-30EU-IL-1](../images/devices/ICPSHC24-30EU-IL-1.jpg) |

## Notes


### Pairing
To factory reset the TRADFRI drivers use a
small pin or paperclip to push the reset button once.


### Device type specific configuration
*[How to use device type specific configuration](../configuration/device_specific_configuration.md)*


* `transition`: Controls the transition time (in seconds) of brightness,
color temperature (if applicable) and color (if applicable) changes. Defaults to `0` (no transition).
Note that this value is overridden if a `transition` value is present in the MQTT command payload.


## Manual Home Assistant configuration
Although Home Assistant integration through [MQTT discovery](../integration/home_assistant) is preferred,
manual integration is possbile with the following configuration:


{% raw %}
```yaml
light:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    brightness: true
    schema: "json"
    command_topic: "zigbee2mqtt/<FRIENDLY_NAME>/set"

sensor:
  - platform: "mqtt"
    state_topic: "zigbee2mqtt/<FRIENDLY_NAME>"
    availability_topic: "zigbee2mqtt/bridge/state"
    unit_of_measurement: "-"
    value_template: "{{ value_json.linkquality }}"
```
{% endraw %}


