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

# XIAO SAMD21 Arduino Microcontroller

### Seeed Studio XIAO SAMD21 Arduino Microcontroller

***

### Product Link

{% embed url="https://openelab.io/products/xiao-samd21-arduino-microcontroller" %}

### Description <a href="#description" id="description"></a>

The Seeed Studio XIAO SAMD21, which used to be named Seeeduino XIAO, is the first debut of the Seeed Studio XIAO family, a series of powerful thumb-size dev boards compatible with Arduino. It carries the powerful ATSAMD21G18A-MU which is a low-power microcontroller. On the other hand, this little board has good performance in processing but needs less power. It is designed in a tiny size and can be used for wearable devices and small projects.

Seeed Studio XIAO SAMD21 has 14 PINs, which can be used for 11 digital interfaces, 11 mock interfaces, 10 PWM interfaces (d1-d10), 1 DAC output pin D0, 1 SWD pad interface, 1 I2C interface, 1 SPI interface, 1 UART interface, Serial communication indicator (T/R), Blink light (L) through pin multiplexing. The colors of LEDs(Power, L,RX,TX) are green, yellow, blue, and blue. Moreover, Seeed Studio XIAO SAMD21 has a Type-C interface that can supply power and download code. There are two reset buttons, you can short-connect them to reset the board.

### **Documentations** <a href="#documentations" id="documentations"></a>

There are two documents on the usage of **Seeed Studio XIAO SAMD21** which focus on different areas, check the table below for reference:

| [**Documentation by Seeed**](https://wiki.seeedstudio.com/Seeeduino-XIAO/) | [**Documentation by Nanase**](https://wiki.seeedstudio.com/Seeeduino-XIAO-by-Nanase/) |
| -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| Pinout Digram                                                              | Interface                                                                             |
| Seeed Studio XIAO SAMD21 Getting Started                                   | Seeed Studio XIAO SAMD21 with MicroSD Card(SPI)                                       |
| Seeed Studio XIAO SAMD21 GPIO Usage                                        | Seeed Studio XIAO SAMD21 with GPS(UART)                                               |
| Seeed Studio XIAO SAMD21 Resources                                         | Single Cycle IOBUS                                                                    |

#### **CircuitPython on Seeed Studio XIAO SAMD21**[​](https://wiki.seeedstudio.com/Seeeduino-XIAO/#circuitpython-on-seeed-studio-xiao-samd21) <a href="#circuitpython-on-seeed-studio-xiao-samd21" id="circuitpython-on-seeed-studio-xiao-samd21"></a>

* Get started with [**CircuitPython on Seeed Studio XIAO SAMD21** ](https://wiki.seeedstudio.com/Seeeduino-XIAO-CircuitPython).

### Features <a href="#features" id="features"></a>

* Powerful CPU: ARM® Cortex®-M0+ 32bit 48MHz microcontroller(SAMD21G18) with 256KB Flash,32KB SRAM.
* Flexible compatibility: Compatible with Arduino IDE.
* Easy project operation: Breadboard-friendly.
* Small size: As small as a thumb(21x17.8mm) for wearable devices and small projects.
* Multiple development interfaces: 11 digital/analog pins, 10 PWM Pins, 1 DAC output, 1 SWD Bonding pad interface, 1 I2C interface, 1 UART interface, 1 SPI interface.

### Specifications <a href="#specifications" id="specifications"></a>

| Item                                   | Value                                                |
| -------------------------------------- | ---------------------------------------------------- |
| CPU                                    | ARM Cortex-M0+ CPU(SAMD21G18) running at up to 48MHz |
| Flash Memory                           | 256KB                                                |
| SRAM                                   | 32KB                                                 |
| Digital I/O Pins                       | 11                                                   |
| Analog I/O Pins                        | 11                                                   |
| I2C interface                          | 1                                                    |
| SPI interface                          | 1                                                    |
| QTouch                                 | 7 (A0,A1,A6,A7,A8,A9,A10)                            |
| UART interface                         | 1                                                    |
| Power supply and downloading interface | Type-C                                               |
| Power                                  | 3.3V/5V DC                                           |
| Dimensions                             | 21×17.8×3.5mm                                        |

### **Hardware** <a href="#schematics" id="schematics"></a>

<img src="https://files.seeedstudio.com/wiki/Seeeduino-XIAO/img/Seeeduino-XIAO-pinout-1.jpg" alt="pir" width="600">

<img src="https://files.seeedstudio.com/wiki/Seeeduino-XIAO/img/new1.png" alt="pir" width="600">

<img src="https://files.seeedstudio.com/wiki/Seeeduino-XIAO/img/Seeeduino%20XIAO%20pinout%202.png" alt="pir" width="600">

<img src="https://files.seeedstudio.com/wiki/Seeeduino-XIAO/img/regulator_to_3.3v.png" alt="pir" width="600">

For general I/O pins: Working voltage of MCU is 3.3V. Voltage input connected to general I/O pins may cause chip damage if it' higher than 3.3V .

For power supply pins: The built-in DC-DC converter circuit able to change 5V voltage into 3.3V allows to power the device with a 5V supply via VIN-PIN and 5V-PIN.

XIAO SAMD21 currently only supports battery power supply and **cannot connect to Type-C while a battery is connected**, as it may pose a safety risk.

Please pay attention to use, do not lift the shield cover.
