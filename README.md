# ESP-360-REMOTE
An all-in-one remote based on the ESP32-WROOM-32E

The project on Hackaday: https://hackaday.io/project/188353-esp-360-remote

Pre-launch page on CrowdSupply: https://www.crowdsupply.com/aaelectronics/esp-360-remote

This board features 433MHz transmitter and receiver. IR leds are placed in circle to cover all the directions. It includes a temperature & humidity and an ambient light sensor. Furthermore you can power and program it through the USB TYPE-C, ESD protected. This board is based around the ESP32-WROOM-32E, so it's super easy to set everything up with ESPHOME and controlling it from Home Assistant.
I think the form factor it's nice.

In the end, the project also as the OSHWA certification, so it's completely open source!


<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/photo_5945308819246659897_y.jpg" width=500/>

There are two stackable layers. 
The bottom one includes the power circuitry, the ESP32 and the temperature, humidity and the light sensors. In the top one there are the IR leds, IR receiver and the RF modules.


The first layer of the board includes the ESP32, the two sensors, the buck converter and the USB circuitry.

<img src="https://raw.githubusercontent.com/ale1800/ESP-360-REMOTE/main/Images/bottom.jpg" width=300/>

The second layer of the board features the IR leds and receiver and the RF modules.

<img src="https://raw.githubusercontent.com/ale1800/ESP-360-REMOTE/main/Images/top.jpg" width=300/>

Inside the enclosure just stack the two layers using the x8 female header near the ESP:

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/assembled_bottom.jpg" width=300/><img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/assembled_both.jpg" width=300/>

The screw the top part and turn the board on!

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/assembled.jpg" width=300/>

Now you can also program the board with the USB-C. I suggest to use ESPHOME beacuse it's super easy to setup and to integrate with Home Assistant

# Dimensions

The board is really small. It fits everywhere It is only 5cm (diameter) x 3cm (height) without the enclosure. This is the comparison against the broadlink rm3 mini, the only device I have as reference

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/vs_broadlink.jpeg" width=500/>


# Enclosure

In this repo you can also file the two stl files of the enclosure, so you can print it yourself choosing the color according to where you want to place it!
The already designed one has some openings near the usb-c and the two built-in sensors, to improve the air flow to cool down the temperature sensor. The top part is screwable, so you don't need screws or other components

<img src="https://github.com/ale1800/ESP-360-REMOTE/blob/main/Images/without_top.jpeg" width=500/>



License:

![oshw_facts](https://user-images.githubusercontent.com/53172176/206875932-d16693e5-e856-4ef7-ab06-4ac33c069df0.jpg)


