---
title: Board.txt Configurables Applicable to LPC and STM32
tags: []
keywords: 
last_updated: 21/01/2021
summary: "Board.txt Configurables Applicable to LPC and STM32"
sidebar: mydoc_sidebar
permalink: board_txt.html
folder: mydoc
comments: false
toc: false
datatable: true
---

Below is a list of items that can be configured using the /sys/board.txt file.

Anything entered in the board.txt file takes precidence over what is set in the firmware.

Examples are given using LPC pins.

<div class="datatable-begin"></div>

|Item Name|Alternative Name from 3.2_4|Example|Description|LPC Comments|STM32 Comments|
| :------------- |:-------------| :---------------|:---|:---|:---|
|8266wifi.csPin||8266wifi.csPin = 0.16|Allow use of non standard CS pin|||
|8266wifi.espDataReadyPin||example 8266wifi.espDataReadyPin = 0.28| used to indicate that data is available from the ESP8266|One pin from port 0 or 2 of the MCU should be used||
|8266wifi.espResetPin||8266wifi.espResetPin = 1.31|This sets the reset pin to use when connecting an ESP8266|||
|8266wifi.lpcTfrReadyPin|8266wifi.TfrReadyPin|8266wifi.lpcTfrReadyPin = 1.30 or 8266wifi.TfrReadyPin = 1.30|This sets the transfer ready pin when connecting an ESP8266|||
|8266wifi.serialRxTxPins||8266wifi.serialRxTxPins = {0.3, 0.2}|This sets the pin numbers to use for RX and TX when connecting an ESP8266. See table below for allowable RX and TX pins|||
|adc.prefilter.enable||adc.prefilter.enable = true|This enables or disables the analogue to digital converter filter. Can be either true or false|||
|adc.preFilter.numberSamples||adc.preFilter.numberSamples = 8|This sets the number of samples to be used to get each value. The larger the value, the smoother the value but lag may also be introduced. The default is 8|||
|adc.preFilter.sampleRate||adc.preFilter.sampleRate = 10000|This sets the analogue to digital converter sample rate in Hz|||
|atx.initialPowerOn||atx.initialPowerOn = 1|This sets the ATX power pin as on as soon as the board powers up rather than having to wait for M80 to be ran. The default is true|||
|atx.powerPin||atx.PowerPin = 2.12|This sets the pin to be used for controlling an ATX power supply|||
|atx.powerPinInverted||atx.powerPinInverted = 0|Some ATX power supplies are active low for off and some are active high. This allows that to be set. Use either 0 or 1|||
|heat.spiTempSensorChannel||heat.spiTempSensorChannel = 255|this selects which SPI channel is used to communicate with the temperature sensor board. Can be set to 255 to indicate no channel to be used|LPC has three SPI interfaces (two channels 0 and 1 are hardware based - SSP0 and SSP1 and channel 2 is software| STM32 has six SPI interfaces (three channels 0, 1 and 3 are hardware based although only 1 and 2 are implemented - SSP0 and SSP1 and channel 3, 4 and 5 are software|
|heat.spiTempSensorCSPins||heat.spiTempSensorCSPins = {1.21, NoPin}|Sets the SPI temperature sensor chip select pin. Can be set to 255 to indicate no channel to be used|LPC accepts a maximum of 2 sensors|STM32 accepts a maximum of 2 sensors|
|heat.tempSensePins||heat.tempSensePins = {0.25,0.23}|Sets the temperature sensor pins starting with the bed|LPC Accepts a maximum of 3 entries|STM32 accepts a maximum of 9 entries|
|lcd.encoderPinA||lcd.encoderPinA = 3.25|Sets the pin for connection A of the encoder|Not supported on LPC||
|lcd.encoderPinB||lcd.encoderPinB = 3.26|Sets the pin for connection B of the encoder|Not supported on LPC||
|lcd.encoderPinSw||lcd.encoderPinSw = 1.30|Sets the pin to be used for the encoder click|Not supported on LPC||
|lcd.lcdBeepPin||lcd.lcdBeepPin = 1.31|Sets the pin to be used to control the display beeper|Not supported on LPC||
|lcd.lcdCSPin||lcd.lcdCSPin = 0.16|Sets the LCD chip select pin|Not supported on LPC||
|lcd.lcdDCPin||lcd.lcdDCPin = 2.11|Sets the data control pin (A0)|Not supported on LPC||
|lcd.panelButtonPin||lcd.panelButtonPin = 2.11|For use when a connected display has an extra button|Not supported on LPC||
|lcd.spiChannel||lcd.spiChannel = 255|This selects which SPI channel is used to communicate with the LCD. Can be set to 255 to indicate no channel to be used|Not supported on LPC| STM32 has six SPI interfaces (three channels 0, 1 and 3 are hardware based although only 1 and 2 are implemented - SSP0 and SSP1 and channel 3, 4 and 5 are software|
|led.neopixelPin||led.neopixelPin = 1.24|This sets the output pin for neopixel control|||
|leds.diagnostic||leds.diagnostic = 1.18|This would set the correct pin for controlling a diagnostic pin|||
|lpc.board|board|lpc.board = fly_e3 or board = fly_e3|This sets the correct board pin mapping to load. See table below for current list|||
|sbc.csPin||sbc.csPin = 0.16|Allow use of non standard CS pin|||
|sbc.lpcTfrReadyPin|sbc.TfrReadyPin|sbc.lpcTfrReadyPin = 0.28 or sbc.TfrReadyPin = 0.28|This sets the transfer ready pin when attaching an SBC|||
|sdCard.external.cardDetectPin||externalSDCard.cardDetectPin|Sets the external SD card detect pin|||
|sdCard.external.csPin||externalSDCard.csPin|Sets the external SD card chip select pin|||
|sdCard.external.spiChannel||sdCard.external.spiChannel = 255|this selects which one is used for the external SD card, can also be set to 255 to indicate no channel is used|||
|sdCard.external.spiFrequencyHz||sdCard.external.spiFrequencyHz = 4000000|Sets the SPI speed for an external SD card in Hz|||
|sdCard.internal.spiFrequencyHz||sdCard.internal.spiFrequencyHz = 4000000|Sets the SPI speed for the internal SD card in Hz|||
|serial.aux.rxTxPins||serial.aux.rxTxPins = {0.3, 0.2}|This sets the pin numbers to use for RX and TX on AUX1. Typically uses UART0. See table below for allowable RX and TX pins|||
|serial.aux2.rxTxPins||serial.aux2.rxTxPins = {0.11, 0.10}|This sets the pin numbers to use for RX and TX on AUX2. Typically uses UART2. See table below for allowable RX and TX pins|||
|softwareSPI.pins||softwareSPI.pins = {0.15,0.17,0.16}|Sets the software SPI pins in the order SCK, MISO, MOSI|||
|softwareSPI1.pins||softwareSPI1.pins = {0.15,0.17,0.16}|Sets the software SPI pins in the order SCK, MISO, MOSI|Not supported on LPC||
|softwareSPI2.pins||softwareSPI2.pins = {0.15,0.17,0.16}|Sets the software SPI pins in the order SCK, MISO, MOSI|Not supported on LPC||
|SSP0.pins||SSP0.pins = {0.15,0.17,1.24,0.16}|Sets the pins to be used for SSP0 in the order SCK, MISO, MOSI, CS|||
|stepper.digipotFactor||stepper.digipotFactor = 113.33|Sets the output current for a built in driver as a factor of 255 against max current|||
|stepper.directionPins||stepper.directionPins = { 0.5,0.11,0.20,0.22,2.13}|Sets the driver direction pins in the order 0, 1, 2, 3 and so on|LPC supports a maximum of 7 drivers|STM32 supports a maximum of 11 drivers|
|stepper.enablePins||stepper.enablePins = {0.4,0.10,0.19,0.21,4.29}|Sets the driver enable pins in the order 0, 1, 2, 3 and so on|LPC supports a maximum of 7 drivers|STM32 supports a maximum of 11 drivers|
|stepper.numSmartDrivers||stepper.numSmartDrivers = 3|Sets the number of TMC22XX drivers installed between 1 and 11. Drivers must be installed from drive 0|||
|stepper.stepPins||stepper.stepPins = {2.0,2.1,2.2,2.3,2.8}|Sets the driver step pins in the order 0, 1, 2, 3 and so on|LPC supports a maximum of 7 drivers|STM32 supports a maximum of 11 drivers|
|stepper.TmcDiagPins||stepper.TmcDiagPins = {1.29, 1.28}|Sets the stall detection diag pins. Typically same pin as the endstop pin|||
|stepper.TmcUartPins||stepper.TmcUartPins = {1.10,1.9,1.8,1.4,1.1}|Sets the pin numbers used for communications with TMC22XX drivers using a UART interface||LPC supports a maximum of 7 drivers|STM32 supports a maximum of 11 drivers|

<div class="datatable-end"></div>

## lpc.board Types

Current preprogrammed boards

<div class="datatable-begin"></div>

|Variable|Board|Type|
| :------------- |:-------------|:---|
|azsmzmini|Azsmz Mini|LPC|
|azteegx5mini1.1|Azteeg X5 Mini v1.1|LPC|
|azteegx5mini2|Azteeg X5 Mini v2|LPC|
|azteegx5mini3|Azteeg X5 Mini v3|LPC|
|biqugtr_1.0|SKR GTR v1.0|STM32|
|biquskr_1.1|SKR v1.1|LPC|
|biquskr_1.3|SKR v1.3|LPC|
|biquskr_1.4|SKR v1.4|LPC|
|biquskr_e3t|SKR E3 Turbo|LPC|
|biquskrpro_1.1|SKR Pro v1.1 and 1.2|STM32|
|fly_407zg|Fly-407ZG|STM32|
|fly_cdy|Fly-CDY|LPC|
|fly_E3|Fly-E3|STM32|
|generic|maps all pins as available by pin number. Not recommended for normal use||
|mbed|For the mbed developer board|LPC|
|mkssbase_1.3|MKS Sbase v1.3|LPC|
|mkssgenl_1.0|MKS SGen L v1.0|LPC|
|mkssgenl_2.0|MKS SGen L v2.0|LPC|
|rearm|ReArm|LPC|
|smoothieboard|Smoothieboard|LPC|

<div class="datatable-end"></div>

## UART Useable Pins - LPC Based Boards

There are 4 UARTS and each can use a selection of pins

<div class="datatable-begin"></div>

|UART Number|RX Pins|TX Pins|
| :------------- |:-------------|:-------------|
|UART0|0.3|0.2|
|UART1|0.16, 0.21|0.15, 2.0|
|UART2|0.11, 2.9| 0.10, 2.8|
|UART3|0.1, 0.26, 4.29|0.0, 0.25, 4.28|

<div class="datatable-end"></div>

## UART Useable Pins - STM32 Based Boards

There are 3 UARTS and each can use a selection of pins

<div class="datatable-begin"></div>

|UART Number|RX Pins|TX Pins|
| :------------- |:-------------|:-------------|
|UART1|PA.10|PA.9|
|UART3|PD.9|PD.8|
|UART6|PC.7|PC.6|

<div class="datatable-end"></div>