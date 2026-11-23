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

# M5Stack ATOM Matrix ESP32 Development Kit

{% hint style="info" %}
[**View M5Stack ATOM Matrix ESP32 Development Kit on OpenELAB**](https://openelab.io/products/m5stackatommatrix)

**Store SKU / option:** `M5-C008-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack ATOM Matrix ESP32 Development Kit

***

### Product Link

{% embed url="https://openelab.io/products/m5stackatommatrix" %}

### Introduction

**ATOM Matrix** is a compact development board in the M5Stack development kit series. With its small size of only 24 \* 24mm, this board is perfect for handy and miniature embedded device development. It offers an increased number of GPIO pins, providing ample flexibility for your projects.\
The main control of ATOM Matrix is powered by the [ESP32](https://shop.m5stack.com/)-PICO-D4 chip, which integrates Wi-Fi technologies and includes 4MB of SPI flash memory. This ensures seamless connectivity and sufficient storage capacity for your applications.ATOM Matrix features an Infra-Red LED and a 5 \* 5 RGB LED matrix on the panel, allowing for vibrant visual displays. Additionally, it comes equipped with a built-in IMU sensor (MPU6886) and a HY2.0 interface, expanding its capabilities for motion sensing and communication with other devices.

<figure><img src="../../.gitbook/assets/image (637).png" alt=""><figcaption></figcaption></figure>

To enhance user interaction, a programmable button is conveniently placed below the RGB LED matrix, enabling easy input integration into various projects. The on-board USB interface (Type-C) facilitates fast program uploading and execution, simplifying the development process. With its compact size, powerful features, and convenient mounting options with the M2 screw hole on the back, ATOM Matrix is the ideal choice for developers seeking a versatile and compact solution for embedded device development.

### Features

* ESP32 PICO-based
* Programmable button
* 5 \* 5 RGB LED matrix panel(WS2812C)
* Built-in Infra-red LED
* Built-in MPU6886 Inertial Sensor
* Extendable Pins & Holes
* Program Platform: [Arduino ](http://www.arduino.cc/)[UIFlow](http://flow.m5stack.com/)

### Specification <a href="#specification" id="specification"></a>

| Resources             | Parameter                                      |
| --------------------- | ---------------------------------------------- |
| ESP32                 | 240MHz dual core, 600 DMIPS, 520KB SRAM, Wi-Fi |
| Flash                 | 4MB                                            |
| Power Input           | 5V @ 500mA                                     |
| Port                  | TypeC x 1, GROVE(I2C+I/0+UART) x 1             |
| PIN Port              | G19, G21,G22,G23,G25, G33                      |
| RGB LED               | WS2812C 2020 x 25                              |
| MEMS                  | MPU6886                                        |
| IR                    | Infrared transmission                          |
| Button                | Custom button x 1                              |
| Antenna               | 2.4G 3D Antenna                                |
| Operating Temperature | 0°C to 60°C                                    |
| Net weight            | 3g                                             |
| Gross weight          | 14g                                            |
| Product Size          | 24\*24\*14mm                                   |
| Package Size          | 43\*43\*20mm                                   |
| Case Material         | Plastic ( PC )                                 |

### Pinout

<figure><img src="../../.gitbook/assets/image (638).png" alt=""><figcaption></figcaption></figure>

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="../../.gitbook/assets/image (639).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Atom-Matrix](https://docs.m5stack.com/en/core/Atom-Matrix) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`C008-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                 |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5atom/program)                                                  |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/C008-B_Atom-Matrix/Structures)                 |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/C008-B_Atom-Matrix/Structures/Atom-Matrix.stl) |
| Official source: M5Atom      | [Read official source: m5atom](https://github.com/m5stack/M5Atom)                                                                        |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
