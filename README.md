# ESP-360-REMOTE
## An all-in-one remote based on the ESP32-WROOM-32E


- ## ESP 360 Remote on [CrowdSupply](https://www.crowdsupply.com/aaelectronics/esp-360-remote)

- ## ESP 360 Remote on [Discord](https://discord.gg/PsrK3KDkRy)


This board boasts a RF transmitter and receiver, while IR LEDs are arranged in a circle to provide omnidirectional coverage. Additionally, it comes equipped with a temperature and humidity sensor, as well as an ambient light sensor. To top it off, the board can be powered and programmed through a USB Type-C port, which is ESD protected. Based on the ESP32-WROOM-32E, this board can be effortlessly configured with ESPHome, allowing for seamless control via Home Assistant.
You can swap the 433MHz modules with 315MHz ones because the SRX/STX882 modules come in both version with the same pinout, so you can choose which one fit your needs the best

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/photo_5945308819246659897_y.jpg" width=500/>


I think the form factor it's nice because there are two round stackable layers. 

The first layer of the board includes the ESP32, the two sensors, the buck converter and the USB circuitry.

<img src="https://raw.githubusercontent.com/ale1800/ESP-360-REMOTE/main/Images/bottom.jpg" width=300/>

The second layer of the board features the IR leds and receiver and the RF modules.

<img src="https://raw.githubusercontent.com/ale1800/ESP-360-REMOTE/main/Images/top.jpg" width=300/>

Inside the enclosure just stack the two layers using the x8 female header near the ESP:

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/assembled_bottom.jpg" width=300/><img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/assembled_both.jpg" width=300/>

Then screw the top part and turn the board on!

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/assembled.jpg" width=300/>

Now you can also program the board with the USB-C. I suggest to use ESPHOME beacuse it's super easy to setup and to integrate with Home Assistant

# Installation
Once you receive the ESP 360 Remote you will need to flash ESPHome on it and configure the remote commands you want to clone.
[INSTALL.md](INSTALL.md) has detailed instructions to follow.

# Home Assistant Integration

ESP 360 REMOTE is designed to be fully integrated into Home Assistant and leverage the capabilities provided by ESPHome. If you decide to use the configuration file provided in this repo, you will see these exposed entities:

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/esp-360-Home-Assistant.jpg" width=500/>

## Transmitting signals

Thanks to the ease of use of ESPHome, you can create custom switches or integrate existing components (see https://esphome.io/components/climate/climate_ir.html) by directly modifying the yaml file, and all of this will be immediately visible on Home Assistant. Alternatively, if you want to take an even simpler route, you can use two integrated services to send raw IR and RF signals:

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/services.png" width=500/>

This way you won't need to tinker with the ESPHome configuration and you'll be able to send signals directly from your automations!

## Receiving signals

When the board receives an RF signal, the **esphome.rf_code_received** event will be triggered in Home Assistant. From there, you can directly see the protocol and code of the received signal. The same feature will soon be available for the infrared receiver as well.

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/event.jpg" width=800/>

In this case, I received the code 721136 (10110000000011110000 in binary) and protocol 2

## SmartIR Integration

ESPHome ensures compatibility with the widely-used SmartIR custom component for Home Assistant, thanks to its built-in support for transmitting raw signals. If you already have a SmartIR configuration in place, all you need to do is specify the appropriate service for transmitting signals and a code that is compatible with ESPHome. Here's an example of what your configuration.yaml file could look like:

```
smartir:

climate:
  - platform: smartir
    name: Livingroom AC
    unique_id: livingroom_ac
    device_code: 7065
    controller_data: esp360remote_send_ir_raw
    temperature_sensor: sensor.living_room_temperature
```
For more information, check out the [SmartIR repo](https://github.com/smartHomeHub/SmartIR).

# Dimensions

The board is remarkably compact, measuring just 5cm in diameter and 3.5cm in height without the enclosure. This small form factor makes it a perfect fit for any space. To put its size into perspective, it's smaller than the Broadlink RM3 Mini, which is the only device I have available for comparison.

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/vs_broadlink.jpeg" width=500/>


# Enclosure

Within this repository, you can also access the two STL files for the enclosure, which enables you to print it in your preferred color to match its intended location. The pre-designed enclosure includes openings near the USB-C port and two built-in sensors to optimize airflow and cool down the temperature sensor. The top part of the enclosure can be screwed on, so there's no need for additional screws or components. I've only tested printing with light-colored PLA, and the IR transmission was not impacted at all. However, I can't make any claims about other materials or dark colors.

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/without_top.jpeg" width=500/>

# OSHWA Certification
In the end, the project also has the OSHWA certification with UID IT000012, so it's completely open source!

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/oshwa.jpeg" width=500/>


License:

![oshw_facts](https://user-images.githubusercontent.com/53172176/206875932-d16693e5-e856-4ef7-ab06-4ac33c069df0.jpg)


