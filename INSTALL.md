# Introduction

If you know ESPHome, you can skip most of this document and just use the template in the [ESPHome Configuration](ESPHome Configuration/esp360-default-1.yaml) folder.

If you don't know much about ESPHome this document will guide you through the installation process. If you need more information you can head to [Discord](https://discord.gg/PsrK3KDkRy) and if you see something that is not clear enough, do not hesitate to make a pull request and improve the documentation for everybody.

there are three way to use your device :
* standalone : good if you plan to setup the device once and forget about it, interract with your device using a webpage
* ESPhome : good if you plan to change the configuration often and add more esphome device, interract with your device using a webpage
* home assistant : if you use it aldready, it has a ESPhome plugin and the step are close the the ESPhome one. interract through home assistant
you also need to follow the next step no matter what setup you choose and finnish with the template step.

# Universal first step
for this step you will require a USB-C cable that has power + data (a normal cable should but some cheap aliexpress cable only have the power wire and no data wire) and a computer with chrome or edge browser (no firefox)
open the following [link](https://web.esphome.io/) in your browser once the device is connected to your computer using the USB-C cable
you need to click on "connect"

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/d5390c21-c24f-41e1-a038-98f9d171800e)

and select the USB-Serial device, if no USB serial device appear, ensure your USB cable is good and that you have the CH240X driver (the tool give you the link to install the driver if needed)

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/8a85914c-d865-4ee3-bd17-9f1b856367f2)

once you are conencted you should be able to click there : 

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/2bd723f7-c853-4a67-82dd-09b676650a08)

the process takes a few minutes and ask for your wifi credentials toward the end so that the device can connect to your network.
once it's done you should be able to access the webpage hosted by the ESP 360 Remote

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/29d30c93-fc50-4dd9-8d0a-e4df338b7313)

as you can see it's empty. this is only the generic ESPHome configuration. follow to the next section to compile the firmware with the IR, RF and sensors feature

# Standalone
first follow this guide that will help you install the compiler for the ESPhome firmware
[ESPHome tool desktop installation](https://esphome.io/guides/installing_esphome.html)
once the tools are installed you can follow this guide to compile the template provided here for your device :
[ESPHome tool desktop usage](https://esphome.io/guides/getting_started_command_line)
you can now jump to the template section

# ESPhome
this option require docker but allow you to manage you fleet of esphome device

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/54c6994f-20ff-47d3-a7e6-2f1cb4a1465a)

I assume you know the docker basics, here is a docker-compose.yml that you can use to run the ESPhome "fleet manager"
```
version: '3'
services:
  esphome:
    container_name: esphome
    image: ghcr.io/esphome/esphome
    volumes:
      - /path/to/esphome/config:/config
      - /etc/localtime:/etc/localtime:ro
    restart: always
    privileged: true
    network_mode: host
    environment:
      - USERNAME=test
      - PASSWORD=ChangeMe
```

edit the username + password and the path to your configuration (just an empty folder is good, we will create the file from the web interface)

once it's running you can can access it on http://127.0.0.1:6052/
from there you can create a new device

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/c529b5d6-154f-40f2-a201-60daa0c56e23)

once done, click on skip for the install and click "edit" instead from the main menu : 

remplace the text with the one found in the [ESPHome Configuration](ESPHome Configuration/esp360-default-1.yaml) folder.
as explained in the template section of this file
once happy with your config you can compile by clicking save then come back to the main menu and click the "..." then install

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/d8344466-55ab-4160-86c9-c3f37f18ba89)

choose manual download

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/e6ae26cc-6eb6-4dc1-970b-3d262d75b06b)

the file will be compiled to a .bin that you will be able to download. you need to download the legacy format :

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/dbe9ecfa-dd81-4144-9331-9234900aaab9)


![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/e6f7382d-27fc-405e-8511-8cb5cea83d2e)

from there, give it a name and choose ESP32

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/8dd688a1-7d29-4f24-bf66-537c23cb7060)

now return to the webpage of the ESP 360 Remote and under OTA Update browse for the file you previously downloaded and click update
once the device as rebooted, you should see the value from the sensors and your switch

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/e66aeed3-7168-4010-b728-6675b3e7b089)



you are done :)
# home assistant
TODO, please write this section if you did it

# template (universal last step)

here is what the template looks like. you can edit the name field and the wifi ssid + password with your
```
esphome:
  name: esp360-default-1
  friendly_name: ESP360-default-1

esp32:
  board: esp32dev
  framework:
    type: arduino

# Enable logging
logger:

api:
  encryption:
    ...
```
you can add your own action.
this is an example that send an IR code that turn ON and OFF a fan.
you will need to adapt the transmit_nec function to your protocol and replace the address and command field accordingly
```
  - platform: template
    name: "fan"
    turn_on_action:
      remote_transmitter.transmit_nec:
        transmitter_id: IR_TX
        address: 0xFE01
        command: 0xE21D
    turn_off_action:
      remote_transmitter.transmit_nec:
        transmitter_id: IR_TX
        address: 0xFE01
        command: 0xE21D
```
if you dont know theses, you can start by compilling the base template and go to the webpage of the ESP 360 remote, you should see a terminal that display the data from the sensors and the IR + RF transceiver
just point the remote you want to clone toward the ESP 360  remote and look at the code display in the terminal.
it should looks like something like this :

![image](https://github.com/nathmo/ESP-360-REMOTE/assets/15912256/0b4145c7-22b1-4e91-9b0d-4f6a9d262afe)

the line that we care about is the following
```
Received NEC: address=0xFE01, command=0xE21D
```
this line give you the protocol (NEC) the address and the command. if you have another protocol lookup in the ESPhome documentation the specific syntax.

Edit the example template with your value and add as many as you need for every function of your remote you want to clone and use from the ESP 360 Remote.

(dont hesitate to read the ESPhome documentation as it will give you more detailled info and more options to configure your actions)
