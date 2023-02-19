# ESPHome configuration for SmartPusher

This is a proof of concept of a [ESPHome](https://esphome.io/) based firmware for the [SmartPusher](https://github.com/Blueforcer/SmartPusher) hardware.


## Get started
- Copy the file `secrets.example.yaml` to `secrets.yaml` and adjust the credentials (e.g. wifi settings)
- Adjust your device name and settings in the file `SmartPusher.yaml`
- Flash your SmartPusher via `esphome run SmartPusher.yaml`


## Home Assistant
Add your new ESPHome device as new Home Assistant integration. You should see the device with 8 buttons as binary sensors, 8 LEDs as light entities and the wifi signal sensor.

The buttons also trigger the event `esphome.smartpusher`. It has following event data:
- device (the device name, default is "smartpusher")
- button (number of the pressed button, 1-8)
- event (click, long_click, double_click)

Example automation:
```
alias: SmartPusher Button 2
description: "Toggle light1 when button 2 gets double clicked"
trigger:
  - platform: event
    event_type: esphome.smartpusher
    event_data:
      button: "2"
      event: double_click
condition: []
action:
  - service: light.toggle
    target:
      entity_id: light.light1
mode: single
```
