# ESPHome configuration for SmartPusher

This is a proof of concept of a [ESPHome](https://esphome.io/) based firmware for the [SmartPusher](https://github.com/Blueforcer/SmartPusher) hardware.


## Get started
- Copy the file `secrets.example.yaml` to `secrets.yaml` and adjust the credentials (e.g. wifi settings)
- Adjust your device name and settings in the file `SmartPusher.yaml`
- Flash your SmartPusher via `esphome run SmartPusher.yaml`


## Home Assistant
Add you new ESPHome device in your Home Assistant settings. You should see the device with 8 buttons as binary_sensors, 8 LEDs as light entities and the wifi signal sensor.

The buttons also trigger the event `esphome.smartpusher`. It has following event data:
- device (the device name, default is "smartpusher")
- button (number of the pressed button, 1-8)
- event (click, long_click, double_click)