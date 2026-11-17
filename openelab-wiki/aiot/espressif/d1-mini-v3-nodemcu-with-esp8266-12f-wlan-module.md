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

# D1 Mini V3 Nodemcu with ESP8266-12F WLAN module

### D1 Mini V3 Nodemcu with ESP8266-12F WLAN module

***

### Product Link

{% embed url="https://openelab.io/products/d1-mini-v3-nodemcu?_pos=1&_sid=ada81805c&_ss=r" %}

### Introduction

The WeMos D1 Mini is an inexpensive ESP8266-based WiFi board that is low-profile but just as powerful as any NodeMCU or ESP8266-based microcontroller. The D1 Mini is incredibly versatile because it is inexpensive, WiFi-enabled, and fully compatible with the Arduino platform. In this tutorial, the ESP8266 library and board manager will be introduced in order to get the D1 Mini acting as an Arduino board. Then, a simple web page will be introduced with the intention of harnessing the WiFi capabilities of the module. The D1 Mini will act as a web server, allowing any WiFi-connected device to interact with the board and control its pins wirelessly.

### Features

* 11 digital IO, interrupt/pwm/I2C/one-wire supported(except D0)
* 1 analog input(3.2V max input)
* a Micro USB connection
* Compatible with MicroPython, Arduino, nodemcu

### Pinout

| Pin | Function                      | ESP-8266 Pin |
| --- | ----------------------------- | ------------ |
| TX  | TXD                           | TXD          |
| RX  | RXD                           | RXD          |
| A0  | Analog input, max 3.2V        | A0           |
| D0  | IO                            | GPIO16       |
| D1  | IO, SCL                       | GPIO5        |
| D2  | IO, SDA                       | GPIO4        |
| D3  | IO, 10k Pull-up               | GPIO0        |
| D4  | IO, 10k Pull-up, BUILTIN\_LED | GPIO2        |
| D5  | IO, SCK                       | GPIO14       |
| D6  | IO, MISO                      | GPIO12       |
| D7  | IO, MOSI                      | GPIO13       |
| D8  | IO, 10k Pull-down, SS         | GPIO15       |
| G   | Ground                        | GND          |
| 5V  | 5V                            | -            |
| 3V3 | 3.3V                          | 3.3V         |
| RST | Reset                         | RST          |

### Technical specs

| Operating Voltage | 3.3V         |
| ----------------- | ------------ |
| Digital I/O Pins  | 11           |
| Analog Input Pins | 1(3.2V Max)  |
| Clock Speed       | 80/160MHz    |
| Flash             | 4M Bytes     |
| Size              | 34.2\*25.6mm |
| Weight            | 3g           |

### How to Use

#### How to flash your Code on the ESP8266 WeMos D1 Mini

You can create your program script with the Arduino IDE and use the Arduino IDE to flash your code to the ESP8266 WeMos D1 Mini. There is only a small change in the Arduino IDE that is described in the following steps:

* In the Arduino IDE menu click on File → Preferences
* Insert the following URL in the field “Additional Boards Manager URLs:”: http://arduino.esp8266.com/stable/package\_esp8266com\_index.json

The following picture shows the result in the preferences menu.

<figure><img src="https://diyi0t.com/wp-content/uploads/2021/03/Arduino-IDE-ESP8266-NodeMCU-Preferences.jpg" alt=""><figcaption></figcaption></figure>

The second step is to install the necessary packages for the ESP8266 module:

* Click in the Arduino IDE on Tools → Board → Board Manager.
* Now search for NodeMCU or ESP8266 and you will find the esp8266 by ESP8266 Community. Install the latest version of the board.

<figure><img src="https://diyi0t.com/wp-content/uploads/2021/03/Arduino-IDE-Boards-Manager-ESP8266-NodeMCU.jpg" alt=""><figcaption></figcaption></figure>

After the installation you can select the ESP8266 WeMos D1 Mini that has the name “LOLIN(WEMOS) D1 R2 & mini” under Tools → Board.

<figure><img src="https://diyi0t.com/wp-content/uploads/2021/04/Arduino-IDE-Select-ESP8266-WeMos-D1-Mini.jpg" alt=""><figcaption></figcaption></figure>
