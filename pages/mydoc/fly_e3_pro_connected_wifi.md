---
title: Connecting a Fly-E3-Pro via Wifi
tags: []
keywords: 
last_updated: 11/03/2021
summary: "Connecting a Fly-E3-Pro via Wifi"
sidebar: mydoc_sidebar
permalink: fly_e3_pro_connected_wifi.html
folder: mydoc
comments: false
toc: false
datatable: true
---

## Overview

The Fly-E3-Pro is an STM32F407ZGT6 based board with onboard drivers.  
This board is very unique in that it has been created as a reprapfirmware board first and foremost.  
That means than unlike other boards, an ESP8266 has been provided on board, no adapter required.  

## Flashing the board firmware

Choose the correct corresponding firmware (firmware-stm43f4-esp8266wifi.bin) from [here](https://github.com/gloomyandy/RepRapFirmware/releases). Remember to rename it to firmware.bin. Put it in the root of a FAT32 formatted SD card. The board is supported from 3.3b1_5 onwards.    

## WiFi firmware preparation
Choose the correct corresponding firmware (DuetWiFiServer-stm32f4.bin) from [here](https://github.com/gloomyandy/DuetWiFiSocketServer/releases). Remember to rename it to DuetWiFiServer.bin. Put it in the sys folder on the SD card.  

### Prepare the SD Card

Follow the instructions on [Getting Started with RRF3](getting_started.html)

### Board.txt file

You will also need a board.txt file in the sys folder. Below are the contents that should be used.

```
//Config for fly-E3
board = fly_e3_pro
//wifi pins
8266wifi.espDataReadyPin = E.13;
8266wifi.TfrReadyPin = E.14;
8266wifi.espResetPin = E.15;
8266wifi.serialRxTxPins = { D.9, D.8 } ;
heat.tempSensePins = { A.3 , A.4, A.1 }
stepper.numSmartDrivers = 5
```

#### Sensorless Homing

If using sensorless homing/stall detection, the following line must be added to the board.txt file.
```
stepper.TmcDiagPins = {A.2, B.10, C.4, D.0, D.1}
```
Please only include the diag pin numbers where you intend to use sensorless homing on that axis. For example, if you only intend to use sensorless homing/stall detection on driver 0 and driver 1, only include A.2 and A.1 in your board.txt file.  
Also, the diag pin jumpers need to be installed for each driver that you intend to use sensorless homing with.
For more information about setting up sensorless homing, please read [this](sensorless.html).  

### Board.txt Location

Place the *board.txt* file in a directory called "sys" on the SD card and install the SD card in the Fly-E3-Pro.   

### Config.g adjustments

The Fly-E3-Pro board is delivered without any firmware on the wifi chip so as part of that process we need to set it up.  
Open the config.g file that has been placed in the sys folder of the SD card and comment out any M552 commands that are there using ; e.g. ;M552 S1.  

### Final Setup

Once connected, power up the board using 12-24v and connect to the USB port on the board. Using a program such as [putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/), connect to the board.  
Then type in the following

```
M997 S1
```
Wait for the uploading of the wifi firmware to finish. Then send the following
```
M552 S0
M587 S"your SSID" P"your password"
M552 S1
```

{% include warning.html content="**DO NOT USE PRONTERFACE** it will convert all text to upper case. If you really must, please do the following. <br/>  If you wanted to use “PassWord”, you would write P”P’a’s’sW’o’r’d” with the ‘ indicating the following letter should be lower case. Explanation [here](https://duet3d.dozuki.com/Wiki/Gcode#Section_M587_Add_WiFi_host_network_to_remembered_list_or_list_remembered_networks)." %}

The blue light on the wifi chip shoould then flash blue and will go solid when a connection has been established. The ip address will be shown on the serial connection. It is also possible to type just M552 to get the current ip address reported back.

The final thing to do is add the line “M552 S1” to your config file. This can be done through the web interface. This just ensures that the wifi connection is started at start up. There is no need to add the M587 command as this is written permanently to the flash of the ESP chip.