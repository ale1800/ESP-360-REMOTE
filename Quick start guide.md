# QUICK START GUIDE FOR THE ESP 360 REMOTE

## INSTALLATION

**Step 1**: Insert the base of the ESP 360 Remote into the case and make sure that all the openings align, as well as the 3 holes in the PCB with the 3 plastic pins.

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/99e91d97-18c2-4bf4-88d3-ab5241038916" alt="drawing" width="400" align="center"/>.

**Step 2**: Insert the RF modules into the upper part of the PCB as shown in the picture and manually raise the infrared LEDs to a 45° angle. They are currently bent horizontally for transportation safety reasons.

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/396fba9e-86de-4aee-8a98-dd8b8ffd69ef" alt="drawing" width="400"/>.

**Step 3**: Insert the top PCB all the way into the base through the 8-pin connector.

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/96065d77-3f68-4a1e-b87b-ad6fbb03f758" alt="drawing" width="400"/>.

**Step 4**: Close the case by screwing the top part, plug in the power cable, and wait for the board’s hotspot called Esp360Remote or Esp360Remote2 (if you ordered the teo pack) to appear!

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/febf8f96-023a-4d50-a6e5-ef75f0398531" alt="drawing" width="400"/>.

## CONNECTION TO HOME ASSISTANT

**Step 1**: When the fallback hotspot is available, connect to it with Esp360Remote as password (for both of the AP’s name)

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/5ca4367c-1ca0-4e2a-a59f-f606ede298c7" alt="drawing" width="400"/>.

**Step 2**: After connecting to its hotspot, go to ip: 192.168.4.1 on your web browser, connect to your WiFi and you are done! Home Assistant should have now discovered your Esp 360 Remote!

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/5ade3c7b-8f48-4860-b651-d4625bd73d51" alt="drawing" width="400"/>.

**Step 3**: Now you can go to the ESPHome dahsboard on your Home Assistant instance and create a new project clicking on the bottom-right "+" icon. Choose the name you want.

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/202101e2-e16d-4908-aceb-5c41ed75bcdf" alt="drawing" width="400"/>.

**Step 4**: Now click on "skip this step" and then select the ESP32 in the next window.

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/c361c84b-4058-4781-9b0f-ae696dba9763" alt="drawing" width="400"/>
<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/f2d7bb5e-a06d-423c-be3f-4172b2f9533b" alt="drawing" width="400"/>.

**Step 5**: Now it will appear your new encryption key. You can save it somewhere and use it to modify the one in the default template, then click "SKIP".

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/5fa2eec3-4202-4461-b8c8-7544f42d72a0" alt="drawing" width="400"/>.

**Step 6**: At this point, you should have your new project in the dashboard. Then click "EDIT", remove everything inside and copy and paste the [default configuration](https://github.com/ale1800/ESP-360-REMOTE/blob/main/ESPHome%20Configuration/esp360-default-1.yaml). Use both the yaml files if have two boards. Then you can change the encryption key if with the one you saved before and **be sure to change the WiFi settings with your credentials**, otherwise it will create again its own hotspot. After you've done that, you can click "SAVE", then "INSTALL" and select "WIRELESSLY". If you've done everything correctly, you should be see your device online in the dashboard and should be able to modify their configuration!

<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/2b5fa883-c945-4bc4-8c61-ecc69476cf29" alt="drawing" width="400"/>
<img src="https://github.com/ale1800/ESP-360-REMOTE/assets/53172176/01b314e5-98f3-45a8-b04b-0e657858d824" alt="drawing" width="400"/>.





