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

# M5Stack 8-Encoder Unit (STM32F030)

### M5Stack 8-Encoder Unit (STM32F030)

***

### Product Link

{% embed url="https://openelab.io/products/8-encoder-unit/" %}

### Introduction

UNIT 8Encoder is a set of 8 rotary encoders as one of the input unit, the internal use of STM32 single-chip microcomputer as the acquisition and communication processor, and the host computer using I2C communication interface, each rotary encoder corresponds to 1 RGB LED light, encoder in addition to left and right rotation, but also radially pressed, in addition to a physical toggle switch and its corresponding RGB LED light, including 5V->3V3 DCDC circuit. The unit can be used for the input of multi-channel relative control values, the corresponding RGB lamp can display different statuses, and the toggle switch can be used for the input of multi-channel switching quantities. It can be used as a multi-degree-of-freedom robot or music equalization application.

<figure><img src="../../.gitbook/assets/image (871).png" alt=""><figcaption></figcaption></figure>

### Features

* 8-channel Rotary encoder
* 8 channels correspond to RGB lights
* I2C communication
* Toggle switches can be used for multi-channel switching inputs
* Radial press function
* HY2.0-4P interface
* 2x LEGO compatible holes

### Specifications

| Resources                 | Parameters             |
| ------------------------- | ---------------------- |
| MCU                       | STM32F030C8T6          |
| RGB                       | WS2812C-2020           |
| Input voltage             | 5v                     |
| I2C communication address | 0x41                   |
| Compression life          | ＞50000 times           |
| Product Size              | 128mm × 24mm ×22.7mm   |
| Package Size              | 130mm × 27.7mm ×27.7mm |
| Product Weight            | 42.8g                  |
| Package Weight            | 52.4g                  |

### Pinout

* **GND**: 接地引脚，用于电源负极。
* **3V3**: 3.3V 电源引脚，用于为模块供电。
* **SCL**: I2C 时钟信号引脚，用于数据传输同步。
* **SDA**: I2C 数据信号引脚，用于数据传输。

### Dimensions

<figure><img src="../../.gitbook/assets/image (872).png" alt=""><figcaption></figcaption></figure>
