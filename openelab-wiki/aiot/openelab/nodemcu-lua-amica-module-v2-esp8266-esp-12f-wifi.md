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

# NodeMCU Lua Amica Module V2 ESP8266 ESP-12F WIFI

### NodeMCU Lua Amica Module V2 ESP8266 ESP-12F WIFI

***

### Product Link

{% embed url="https://openelab.io/products/nodemculuaamicamodule?_pos=1&_sid=d21d38587&_ss=r" %}

### Introduction

The NodeMCU Amica V2 is the classic ESP developer board. Especially breadboard-friendly and equipped with a powerful ESP8266-12F processor from Espressif and integrated WLAN, this controller offers an easy entry into IoT development.

<figure><img src="../../.gitbook/assets/image (554).png" alt=""><figcaption></figcaption></figure>

### Specifications

| Supply voltage (USB)  | 5V DC                              |
| --------------------- | ---------------------------------- |
| Input/output voltage  | 3.3V DC                            |
| Clock frequency       | 80 MHz / 160MHz                    |
| Instructions RAM      | 32kb                               |
| Data ram              | 96kb                               |
| External flash memory | 4MB                                |
| GPIO digital pins     | 17 (configurable as a PWM at 3.3V) |
| ADC analog PIN        | 1 (but voltage area is: 0 - 1v)    |
| Uart                  | 2                                  |

### Pinout

<figure><img src="../../.gitbook/assets/image (553).png" alt=""><figcaption></figcaption></figure>

### How to Use

Arduino core for ESP8266 WiFi chip

[https://github.com/esp8266/Arduino](https://github.com/esp8266/Arduino)

ESP8266 Arduino core comes with libraries to communicate over WiFi using TCP and UDP, set up HTTP, mDNS, SSDP, and DNS servers, do OTA updates, use a file system in flash memory, and work with SD cards, servos, SPI and I2C peripherals.

* Start Arduino and open the Preferences window.
* Enter [https://arduino.esp8266.com/stable/package\_esp8266com\_index.json](https://arduino.esp8266.com/stable/package_esp8266com_index.json) into the Additional Board Manager URLs field. You can add multiple URLs.
* Open Boards Manager from Tools > Board menu and install esp8266 platform (and don't forget to select your ESP8266 board from Tools > Board menu after installation).

![](https://hackster.imgix.net/uploads/attachments/1205691/image_gcrWOrzwWl.png?auto=compress%2Cformat\&w=740\&h=555\&fit=max)

Documentation: [https://arduino-esp8266.readthedocs.io/](https://arduino-esp8266.readthedocs.io/en/2.7.4_a/)

Then go to the board manager and install esp8266:

![](https://hackster.imgix.net/uploads/attachments/1205850/image_2Oei2xPCQC.png?auto=compress%2Cformat\&w=740\&h=555\&fit=max)

Select your board:

Tools > Board > NodeMCU 1.0 (ESP - 12E Module)

![](https://hackster.imgix.net/uploads/attachments/1205852/image_FmOtCMnQV8.png?auto=compress%2Cformat\&w=740\&h=555\&fit=max)

To upload the sketch code to the NodeMCU board, first select port on which you connected the board.
