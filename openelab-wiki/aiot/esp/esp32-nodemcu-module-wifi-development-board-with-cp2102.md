---
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# ESP32 NODEMCU Module WiFi Development Board with CP2102

### ESP32 NODEMCU Module WiFi Development Board with CP2102

### Description

The  ESP32 NODEMCU Module was designed By Espressif to provide an easy introduction to programming the new ESP32 dual-core processor. With a variety of new sensors and functions, this board represents the next step in IoT development.

### Special features

* As with the predecessor model ESP8266, the WLAN functionality is implemented directly in the SoC, but with additional Bluetooth function (incl. BLE).
* The ESP32 processor used combines a CPU with 2 Tensilica LX6 cores, clocked at up to 240 MHz, and 512 kiloBytes of SRAM in a single microcontroller chip.
* It also integrates a radio unit for WLAN (according to 802.11bgn) and Bluetooth (Classic and LE).

### Technical specifications

| Power supply voltage (USB) | 5V                                    |
| -------------------------- | ------------------------------------- |
| Input/output voltage       | 3.3V                                  |
| Required operating current | Min. 500mA                            |
| Soc                        | ESP32-Wroom 32                        |
| Clock frequency range      | 80 MHz / 240MHz                       |
| R.A.M.                     | 512kb                                 |
| External flash memory      | 4MB                                   |
| I/o pins                   | 34                                    |
| Interfaces                 | SPI, I2C, I2S, Can, Uart              |
| Wi-fi protocols            | 802.11 b/g/n (802.11n up to 150 Mbps) |
| Wi-Fi frequency            | 2.4 GHz - 2.5 GHz                     |
| Bluetooth                  | V4.2 - BLE and Classic Bluetooth      |
| Wireless antenna           | PCB                                   |
| Dimensions                 | 56x28x13mm                            |

### Install the drivers on the computer

Usually, a new device installs its drivers at the first connection. When this is not the case, it is possible, as with the NodeMCU, that the device is not recognized. There are two main families of drivers in the Arduino world:

* CP2102
* CH340

If you bought an Arduino compatible board, there is a good chance that one of these two drivers is needed to communicate with the microcontroller.

In this case, there are two methods to get the drivers. The first one is to find and download them on the internet ([NodeMCU drivers](https://github.com/nodemcu/nodemcu-devkit/tree/master/Drivers) and [CP2102](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)).

The second is to use the device manager. The microcontrollers connected to the computer are found under the tab “Ports (COM and LPT)”.

<figure><img src="https://www.aranacorp.com/wp-content/uploads/nodemcu-esp32-cp2102-driver.jpg" alt="" height="215" width="419"><figcaption></figcaption></figure>

Double-click on the device and the properties window will appear. Under the “Driver” tab, you will find the option “update” the driver.

<figure><img src="https://www.aranacorp.com/wp-content/uploads/nodemcu-esp32-cp2102-driver-update.jpg" alt="" height="473" width="408"><figcaption></figcaption></figure>

Select the “Automatically search for the driver” option.

<figure><img src="https://www.aranacorp.com/wp-content/uploads/device-manager-update-driver-opt.jpg" alt="" height="450" width="614"><figcaption></figcaption></figure>

Depending on the version of the microcontroller you have and the manufacturer, it may use different drivers CP2102 (Normally installed with Arduino) and CH340.

Once the driver is installed, it will be possible to communicate with the device.

### Add JSON handlers

To be able to program other microcontrollers with the Arduino IDE, it is necessary to install on the Arduino board managers containing all the tools necessary for their programming. To get the managers you have to find the corresponding URL. In the case of the NodeMCU ESP32, [https://dl.espressif.com/dl/package\_esp32\_index.json](https://dl.espressif.com/dl/package_esp32_index.json).

> UPDATE: For Arduino IDE 2.0 or higher : https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package\_esp32\_index.json

N.B.: If you encounter compilation problems, check if a previous version of ESP32 is installed. If it is the case, delete it manually (C:\Users\\\AppData\Local\Arduino15\packages\esp32\hardware\esp32).

Then open the File>Preferences window of the Arduino software. At the bottom of the page you will find a text box in which to enter the URL: “Additional board manager URL”. (don’t forget to separate the URLs with a comma “,”)

<figure><img src="https://www.aranacorp.com/wp-content/uploads/nodemcu-esp32-ide-configuration.jpg" alt="" height="479" width="802"><figcaption></figcaption></figure>

### Install the managers

Under the “Tools” tab, follow the path “BoardType > Board Manager”. The IDE will load the board catalog from the URL.

<figure><img src="https://www.aranacorp.com/wp-content/uploads/arduino-ide-board-manager.jpg" alt="" height="308" width="646"><figcaption></figcaption></figure>

If you search for the microcontroller in the search bar, the package to be installed should appear.

<figure><img src="https://www.aranacorp.com/wp-content/uploads/nodemcu-esp32-board-manager.jpg" alt="" height="443" width="786"><figcaption></figcaption></figure>

### Select the configuration

Once the management package is installed, the microcontroller should appear in the available card types.

For NodeMCU ESP32 (ESP-WROOM-32S), select “ESP32 Dev Module

<figure><img src="https://www.aranacorp.com/wp-content/uploads/nodemcu-esp32-ide-board-type-dev.jpg" alt="" height="466" width="670"><figcaption></figcaption></figure>

You will then need to know the characteristics of your card to select the right settings. However, except in exceptional cases, the default settings will work without problem.
