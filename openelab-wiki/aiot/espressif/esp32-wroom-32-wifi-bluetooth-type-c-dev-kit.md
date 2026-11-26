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

# ESP32-WROOM-32 Wifi Bluetooth Type-C Dev Kit

### ESP32-WROOM-32 Wifi Bluetooth Type-C Dev Kit

***

### Product Link

{% embed url="https://openelab.io/products/esp32-wroom-32-wifi-bluetooth?_pos=1&_psq=ESP32-WROOM-32%20Wifi%20Bluetooth%20Type-C%20Dev%20Kit&_ss=e&_v=1.0" %}

### Introduction

ESP32-DevKitC V4 is a small-sized ESP32-based development board produced by [Espressif](https://espressif.com/). Most of the I/O pins are broken out to the pin headers on both sides for easy interfacing. Developers can either connect peripherals with jumper wires or mount ESP32-DevKitC V4 on a breadboard.

### Functional Description

The following figure and the table below describe the key components, interfaces and controls of the ESP32-DevKitC V4 board.

<figure><img src="https://raw.githubusercontent.com/espressif/esp-idf/v3.3/docs/_static/esp32-devkitc-functional-overview.jpg" alt="ESP32-DevKitC V4 with ESP-WROOM-32 module soldered"><figcaption><p>ESP32-DevKitC V4 with ESP32-WROOM-32 module soldered</p></figcaption></figure>

| Key Component      | Description                                                                                                                                                                                                                                                       |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ESP32-WROOM-32     | A module with ESP32 at its core. For more information, see [ESP32-WROOM-32 Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-wroom-32_datasheet_en.pdf).                                                                               |
| EN                 | Reset button.                                                                                                                                                                                                                                                     |
| Boot               | Download button. Holding down **Boot** and then pressing **EN** initiates Firmware Download mode for downloading firmware through the serial port.                                                                                                                |
| USB-to-UART Bridge | Single USB-UART bridge chip provides transfer rates of up to 3 Mbps.                                                                                                                                                                                              |
| Micro USB Port     | USB interface. Power supply for the board as well as the communication interface between a computer and the ESP32-WROOM-32 module.                                                                                                                                |
| 5V Power On LED    | Turns on when the USB or an external 5V power supply is connected to the board. For details see the schematics in [Related Documents](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#related-documents). |
| I/O                | Most of the pins on the ESP module are broken out to the pin headers on the board. You can program ESP32 to enable multiple functions such as PWM, ADC, DAC, I2C, I2S, SPI, etc.                                                                                  |

### Power Supply Options

There are three mutually exclusive ways to provide power to the board:

* Micro USB port, default power supply
* 5V and GND header pins
* 3V3 and GND header pins

<mark style="color:orange;">Warning</mark>

The power supply must be provided using **one and only one of the options above**, otherwise the board and/or the power supply source can be damaged.

### Header Block

The two tables below provide the **Name** and **Function** of I/O header pins on both sides of the board, as shown in [ESP32-DevKitC V4 with ESP32-WROOM-32 module soldered](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#get-started-esp32-devkitc-board-front).

#### J2

| No. | Name | Type [1](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id11) | Function                                                                                                                      |
| --- | ---- | ---------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1   | 3V3  | P                                                                                                                      | 3.3 V power supply                                                                                                            |
| 2   | EN   | I                                                                                                                      | CHIP\_PU, Reset                                                                                                               |
| 3   | VP   | I                                                                                                                      | GPIO36, ADC1\_CH0, S\_VP                                                                                                      |
| 4   | VN   | I                                                                                                                      | GPIO39, ADC1\_CH3, S\_VN                                                                                                      |
| 5   | IO34 | I                                                                                                                      | GPIO34, ADC1\_CH6, VDET\_1                                                                                                    |
| 6   | IO35 | I                                                                                                                      | GPIO35, ADC1\_CH7, VDET\_2                                                                                                    |
| 7   | IO32 | I/O                                                                                                                    | GPIO32, ADC1\_CH4, TOUCH\_CH9, XTAL\_32K\_P                                                                                   |
| 8   | IO33 | I/O                                                                                                                    | GPIO33, ADC1\_CH5, TOUCH\_CH8, XTAL\_32K\_N                                                                                   |
| 9   | IO25 | I/O                                                                                                                    | GPIO25, ADC2\_CH8, DAC\_1                                                                                                     |
| 10  | IO26 | I/O                                                                                                                    | GPIO26, ADC2\_CH9, DAC\_2                                                                                                     |
| 11  | IO27 | I/O                                                                                                                    | GPIO27, ADC2\_CH7, TOUCH\_CH7                                                                                                 |
| 12  | IO14 | I/O                                                                                                                    | GPIO14, ADC2\_CH6, TOUCH\_CH6, MTMS                                                                                           |
| 13  | IO12 | I/O                                                                                                                    | GPIO12, ADC2\_CH5, TOUCH\_CH5, MTDI                                                                                           |
| 14  | GND  | G                                                                                                                      | Ground                                                                                                                        |
| 15  | IO13 | I/O                                                                                                                    | GPIO13, ADC2\_CH4, TOUCH\_CH4, MTCK                                                                                           |
| 16  | D2   | I/O                                                                                                                    | GPIO9, D2 [2](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id12)   |
| 17  | D3   | I/O                                                                                                                    | GPIO10, D3 [2](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id12)  |
| 18  | CMD  | I/O                                                                                                                    | GPIO11, CMD [2](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id12) |
| 19  | 5V   | P                                                                                                                      | 5 V power supply                                                                                                              |

#### J3

| No. | Name | Type [1](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id11) | Function                                                                                                                     |
| --- | ---- | ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| 1   | GND  | G                                                                                                                      | Ground                                                                                                                       |
| 2   | IO23 | I/O                                                                                                                    | GPIO23                                                                                                                       |
| 3   | IO22 | I/O                                                                                                                    | GPIO22                                                                                                                       |
| 4   | TX   | I/O                                                                                                                    | GPIO1, U0TXD                                                                                                                 |
| 5   | RX   | I/O                                                                                                                    | GPIO3, U0RXD                                                                                                                 |
| 6   | IO21 | I/O                                                                                                                    | GPIO21                                                                                                                       |
| 7   | GND  | G                                                                                                                      | Ground                                                                                                                       |
| 8   | IO19 | I/O                                                                                                                    | GPIO19                                                                                                                       |
| 9   | IO18 | I/O                                                                                                                    | GPIO18                                                                                                                       |
| 10  | IO5  | I/O                                                                                                                    | GPIO5                                                                                                                        |
| 11  | IO17 | I/O                                                                                                                    | GPIO17 [3](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id13)     |
| 12  | IO16 | I/O                                                                                                                    | GPIO16 [3](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id13)     |
| 13  | IO4  | I/O                                                                                                                    | GPIO4, ADC2\_CH0, TOUCH\_CH0                                                                                                 |
| 14  | IO0  | I/O                                                                                                                    | GPIO0, ADC2\_CH1, TOUCH\_CH1, Boot                                                                                           |
| 15  | IO2  | I/O                                                                                                                    | GPIO2, ADC2\_CH2, TOUCH\_CH2                                                                                                 |
| 16  | IO15 | I/O                                                                                                                    | GPIO15, ADC2\_CH3, TOUCH\_CH3, MTDO                                                                                          |
| 17  | D1   | I/O                                                                                                                    | GPIO8, D1 [2](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id12)  |
| 18  | D0   | I/O                                                                                                                    | GPIO7, D0 [2](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id12)  |
| 19  | CLK  | I/O                                                                                                                    | GPIO6, CLK [2](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/hw-reference/esp32/get-started-devkitc.html#id12) |

\[1] (1,2) &#x20;

P: Power supply; I: Input; O: Output.

\[2] (1,2,3,4,5,6)

The pins D0, D1, D2, D3, CMD and CLK are used internally for communication between ESP32 and SPI flash memory. They are grouped on both sides near the USB connector. Avoid using these pins, as it may disrupt access to the SPI flash memory/SPI RAM.

\[3] (1,2)

The pins GPIO16 and GPIO17 are available for use only on the boards with the modules ESP32-WROOM and ESP32-SOLO-1. The boards with ESP32-WROVER modules have the pins reserved for internal use.

<figure><img src="../../.gitbook/assets/image (720).png" alt=""><figcaption></figcaption></figure>

### Note on C15

The component C15 may cause the following issues on earlier ESP32-DevKitC V4 boards:

* The board may boot into Download mode
* If you output clock on GPIO0, C15 may impact the signal

In case these issues occur, please remove the component. The figure below shows the location of C15 highlighted in yellow.

<figure><img src="../../.gitbook/assets/image (722).png" alt=""><figcaption></figcaption></figure>

### Start Application Development

Before powering up your ESP32-DevKitC V4, please make sure that the board is in good condition with no obvious signs of damage.

After that, proceed to [Get Started](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html), where Section [Installation](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html#get-started-step-by-step) will quickly help you set up the development environment and then flash an example project onto your board.
