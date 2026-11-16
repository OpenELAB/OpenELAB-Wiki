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

# M5Stack Encoder Unit

### M5Stack Encoder Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-encoder-unit" %}

### Introduction

Unit Encoder is a rotary encoder expansion unit with I2C interface, integrated with 30-bit pulse encoding knob (with button function) + 2 x SK6812 programmable RGB LEDs. The built-in STM32F030 flashed with the encoder pulse acquisition firmware, allowing users to obtain the encoded value directly via I2C. Suitable for scale value control/volume adjustment and other control scenarios.



<figure><img src="../../.gitbook/assets/image (473).png" alt=""><figcaption></figcaption></figure>

### Features

* 30-bit pulse encoding knob (30 pulses per rotation)
* 2x SK6812 programmable RGB LEDs
* 1x Button input

### Specifications

| Specifications       | Parameters                                 |
| -------------------- | ------------------------------------------ |
| Pulse encoder knob   | 30-bit pulse encoder knob (with key input) |
| Programmable RGB LED | 2x SK6812                                  |
| Working current      | Encoder working (DC-5V@17mA)               |
| Net weight           | 7.4g                                       |
| Gross weight         | 12.3g                                      |
| Product size         | 32 \* 24 \* 22mm                           |
| Packing size         | 93 \* 138mm                                |

### Pinout

| M5Core(PORT A) | GPIO22 | GPIO21 | 5V | GND |
| -------------- | ------ | ------ | -- | --- |
| Unit Encoder   | SCL    | SDA    | 5V | GND |

<figure><img src="../../.gitbook/assets/image (468).png" alt=""><figcaption></figcaption></figure>

### Dimensions

size:7.4g

weight:32 \* 24 \* 22mm

### How to Use

#### Arduino <a href="#arduino" id="arduino"></a>

* Libraries
  * [Unit Encoder Library](https://github.com/m5stack/UNIT_ENCODER)
  * [Unit Encoder Test With M5Core](https://github.com/m5stack/UNIT_ENCODER/blob/master/examples/GET_VALUE/GET_VALUE.ino)
* Firmware
  * [M5UnitEncoder\_Firmware](https://github.com/m5stack/M5UnitEncoder_Firmware)

<figure><img src="../../.gitbook/assets/image (870).png" alt=""><figcaption></figcaption></figure>
