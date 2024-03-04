# 2.4GHz Slim Tx

This is basically the same PCB as the DIY 2.4GHz JR module but in a smaller form factor. The PCB works in both the slim enclosure and the JR enclosure.

For info on the prebuilt versions, go to the wiki page for [Nuclear Super Slim TX](https://github.com/ExpressLRS/ExpressLRS/wiki/Nuclear-Super-Slim-TX).

### PCB manufacturing

Upload the Gerber file to https://jlcpcb.com/RAT.  Check the price for 5, 10, and 30 pieces.  It is sometimes cheaper to order 30 than 10 and only a minor increase in price compared to 5.

*PCB Thickness: 1mm*
*Remove Order Number: Specify a location*

### BOM

- E28-2G4M27S SX1280 Wireless module 2.4G 27dBm https://www.aliexpress.com/item/33004335921.html
- 3.3V DC-DC Step Down Power Supply https://www.aliexpress.com/item/32880983608.html
- 10k 0402 resistor https://www.aliexpress.com/item/4000049692396.html
- SMA or RPSMA pigtail https://www.aliexpress.com/item/4000848776660.html https://www.aliexpress.com/item/4000848776660.html
- WROOM32 module https://www.aliexpress.com/item/ESP32-ESP-32S-WIFI-Bluetooth-Module-240MHz-Dual-Core-CPU-MCU-Wireless-Network-Board-ESP-WROOM/4000230070560.html
- 10uF 3528 Cap https://www.aliexpress.com/item/32666405364.html?algo_pvid=365ae59d-9e6c-46b7-9792-2656b0961f70&algo_expid=365ae59d-9e6c-46b7-9792-2656b0961f70-6&btsid=0bb0623116027669252885518ea610&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_
- 8 Way header https://www.aliexpress.com/item/3pcs-1X40PIN-2-54MM-1x40-Pin-2-54-Round-Female-Pin-Header-connector/32847506950.html?spm=a2g0s.9042311.0.0.27424c4dOfOrhZ
- 4 M3 screws 4-7mm (use leftover motor/frame screws)
- 2.4GHz antenna
- A few wires
- 3D printed case

### Build order

Here is a video of an older version of this module being built:

https://youtu.be/sNQbWaVPUCc

0. Print both STLs in the orientation shown in the image below, use light support (15%)
1. Move 0 ohm resistor on E28 to make it use the external antenna
2. Set the regulator voltage to 3.45V by rotating the potentiometer on the top fully clockwise, and jumper both the 5V and 12V pads on the back
3. Solder ESP32 and E28 to PCB
4. Solder 10k resistor
6. Solder capacitor with stripe closer to the ESP32
5. Bridge the boot pads near the E28
7. Solder 4 pin header to ESP32 side of PCB
8. Put voltage regulator on the pin header UPSIDE DOWN and solder
9. Clip extra length of header pins
10. Connect serial adapter to with the 6 pins (SET POWER TO 3.3V OR YOU WILL KILL THE ESP!)
11. Upload your build (if it doesn't work, check for shorts, add flux and heat to solder joints)
12. Remove bridge over boot pads near E28 again (otherwise the ESP won't start correctly later)
13. Solder wires to G, +, S on E28 side of board (If they're on the ESP side they might get in the way of the board fitting all the way inside the enclosure)
14. Insert antenna pigtail
15. Insert header to back of enclosure (I don't have the correct header so I had to trim mine a bit)
16. Solder wires to the three pins on the right +, G, S from left to right
17. Insert PCB and attach antenna pigtail
18. Connect to handset and verify voltage from regulator is 3.3V
19. Bridge vreg en pads
20. Screw down cover
21. Make sure LUA script can communicate with module

### STLs

[Slim enclosure onshape link](https://cad.onshape.com/documents/2cffc645d8696d047935ac89/w/6acaaaa832f4b23c1c8ac47e/e/49ad20ba4b7d79ea1d683a18)
[JR enclosure onshape link](https://cad.onshape.com/documents/50ada7dd7257b3b4cfa71d02/w/741afccb437d7d488507c71b/e/4760c734ca4584832616ed85)

### Pics

<img src="https://github.com/ExpressLRS/ExpressLRS-Hardware/blob/master/PCB/2400MHz/TX_SX1280_Super_Slim/img/printlayout.png?raw=true" width="300">
<img src="https://github.com/ExpressLRS/ExpressLRS-Hardware/blob/master/PCB/2400MHz/TX_SX1280_Super_Slim/img/antennaswitch.png?raw=true" width="300">
<img src="https://github.com/ExpressLRS/ExpressLRS-Hardware/blob/master/PCB/2400MHz/TX_SX1280_Super_Slim/img/exploded.jpg?raw=true" width="300">
<img src="https://github.com/ExpressLRS/ExpressLRS-Hardware/blob/master/PCB/2400MHz/TX_SX1280_Super_Slim/img/compacted.jpg?raw=true" width="300">
<img src="https://github.com/ExpressLRS/ExpressLRS-Hardware/blob/master/PCB/2400MHz/TX_SX1280_Super_Slim/img/ftdi.png?raw=true" width="300">

### Schematic and PCB layout

<img src="https://github.com/ExpressLRS/ExpressLRS-Hardware/blob/master/PCB/2400MHz/TX_SX1280_Super_Slim/img/brd.png?raw=true" width="300">


###  Adding an I2C OLED for super slim
Your DIY module must be running master. I2C OLED is not supported under v2.0.1.

This is tested with an I2C SSD1306 OLED display.

Attach wires to SDA, SCK, GND and 3.3v.
Add -DUSE_OLED_I2C to your defines.
The module should activate on boot.

<img width="494" alt="image" src="https://user-images.githubusercontent.com/43392862/157010894-05f176a0-af13-4dab-b7fc-4191f4f429aa.png">

