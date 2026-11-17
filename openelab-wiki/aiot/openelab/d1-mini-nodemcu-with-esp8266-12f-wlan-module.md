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

# D1 Mini Nodemcu with ESP8266-12F WLAN module

### D1 Mini Nodemcu with ESP8266-12F WLAN module

***

### Product Link

{% embed url="https://openelab.io/products/d1mininodemcu?variant=43509584396486" %}

### Introduction

The WeMos D1 Mini is an inexpensive ESP8266-based WiFi board that is low-profile but just as powerful as any NodeMCU or ESP8266-based microcontroller. The D1 Mini is incredibly versatile because it is inexpensive, WiFi-enabled, and fully compatible with the Arduino platform. In this tutorial, the ESP8266 library and board manager will be introduced in order to get the D1 Mini acting as an Arduino board. Then, a simple web page will be introduced with the intention of harnessing the WiFi capabilities of the module. The D1 Mini will act as a web server, allowing any WiFi-connected device to interact with the board and control its pins wirelessly.

### Features

| Board                           | ESP8266 WeMos D1 Mini                 |
| ------------------------------- | ------------------------------------- |
| Microcontroller                 | ESP8266                               |
| Processor                       | Tensilica Xtensa Diamond 32-bit       |
| Operating Voltage               | 3.3V                                  |
| Minimum Operating Voltage       | 2.58V                                 |
| Maximum Operating Voltage       | 3.6V                                  |
| Arduino IDE Board               | LOLIN(WEMOS) D1 R2 & mini             |
|                                 |                                       |
| Power Supply via VIN,VCC        | 4V...6V                               |
| VIN,VCC output USB power supply | 4.67V                                 |
|                                 |                                       |
| Digital I/O Pins (with PWM)     | 11 (11)                               |
| Analog Input Pins               | 1                                     |
| Resolution ADC                  | 10 bit (0...1023)                     |
| Analog Output Pins              | 0                                     |
| SPI/I2C/I2S/UART                | 1/1/1/1                               |
| Max DC Current per I/O Pin      | 12 mA                                 |
|                                 |                                       |
| Flash Memory                    | 4 MB                                  |
| SRAM                            | 64 KB                                 |
| EEPROM                          | 512 bytes                             |
| Clock Speed                     | 80/160 MHz                            |
|                                 |                                       |
| Length x Width                  | 34mm x 26mm                           |
| Fits on standard breadboard     | yes                                   |
|                                 |                                       |
| WIFI                            | IEEE 802.11 b/g/n                     |
| Bluetooth                       | no                                    |
| Touch sensor                    | no                                    |
| CAN                             | no                                    |
| Ethernet MAC Interface          | no                                    |
| Temperature Sensor              | no                                    |
| Hall effect sensor              | no                                    |
|                                 |                                       |
| Power jack                      | no                                    |
| USB connection                  | yes                                   |
| Battery Connection              | no                                    |
|                                 |                                       |
| Programmable                    | Arduino IDE, LuaNode SDK, Micropython |
|                                 |                                       |
| 3.3V Voltage Regulator          | ME6211                                |
| Output Voltage                  | 3.3V                                  |
| Maximum Input Voltage           | 6V                                    |
| Minimum Input Voltage           | 4.3V                                  |
| Maximum Output Current          | 500mA                                 |
| Maximum Voltage Dropout         | 680mV @ 500mA                         |
| Typical Quiescent Current       | 0.1µA                                 |
|                                 |                                       |
| Power Consumption @ 5V          |                                       |
| Reference WiFi Scan Mean \[mA]  | 68                                    |
| Reference Empty Script \[mA]    | 72                                    |
| Light Sleep \[mA]               | 0.68                                  |
| Deep Sleep \[mA]                | 0.17                                  |

### Pinout

<figure><img src="../../.gitbook/assets/image (739).png" alt=""><figcaption></figcaption></figure>

The ESP8266 WeMos D1 Mini has only one 3.3V output pin and also only one ground pin to power an external circuit. Today it is easy to create custom PCBs that are not expensive. If your project is ready for action you could put the WeMos D1 Mini on this custom PCB and more than one 3.3V pin and one ground for the PCB is not necessary. During the creation of the project, you can connect the 3.3V and ground pin with the rails of the breadboard to supply different electronic components.

The 5V pin has either the function as a power supply for the ESP8266 with voltages between 4V and 6 or can be used as 4.67V output when the ESP8266 WeMos D1 Mini is powered via USB. Therefore, you might also supply electronic components that need a supply voltage of 5V, because these components should also work with a supply voltage of 4.67V.

The ESP8266 WeMos D1 Mini has in total 9 digital input / output pins. All these 9 pins can create [PWM](https://diyi0t.com/arduino-pwm-tutorial/) signals and have a maximum output current of 12mA. You could also use the two UART pins that are not labeled as digital pins to get even 12 digital pins.

Unfortunately, the ESP8266 has only 1 analog input A0 that is connected internally with a 10-bit analog-to-digital converter (ADC) to convert the analog voltage into 1024 digital values between 0 and 1023.

### Dimensions

<figure><img src="../../.gitbook/assets/image (740).png" alt=""><figcaption></figcaption></figure>

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
