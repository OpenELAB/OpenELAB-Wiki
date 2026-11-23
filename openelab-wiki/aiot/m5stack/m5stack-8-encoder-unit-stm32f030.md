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

{% hint style="info" %}
[**View M5Stack 8Encoder Unit with 8 Rotary Encoders and RGB LEDs on OpenELAB**](https://openelab.io/products/8-encoder-unit)

**Store SKU / option:** `M5-U153`. Match the purchased model and revision to the official reference below.
{% endhint %}

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

## Official documentation and development resources

Use [Unit 8Encoder](https://docs.m5stack.com/en/unit/Unit_8Encoder) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U153`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                             | Model-specific reference                                                                                                                   |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Electrical schematic                         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/607/SCH_UNIT_8Encoder_V1.01.pdf)                              |
| Mechanical / CAD files                       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U153_Unit_8Encoder/Structures)                   |
| Mechanical / CAD files                       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U153_Unit_8Encoder/Structures/Unit_8Encoder.stl) |
| Official source: M5Unit-8Encoder             | [Read official source: m5unit-8encoder](https://github.com/m5stack/M5Unit-8Encoder)                                                        |
| Official source: M5Unit-8Encoder-Internal-FW | [Read official source: m5unit-8encoder-internal-fw](https://github.com/m5stack/M5Unit-8Encoder-Internal-FW)                                |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
