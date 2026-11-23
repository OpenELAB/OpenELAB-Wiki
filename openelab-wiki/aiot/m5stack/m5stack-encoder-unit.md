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

{% hint style="info" %}
[**View M5Stack Encoder Unit on OpenELAB**](https://openelab.io/products/m5stack-encoder-unit)

**Store SKU / option:** `M5-U135`. Match the purchased model and revision to the official reference below.
{% endhint %}

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

## Official documentation and development resources

Use [Unit Encoder](https://docs.m5stack.com/en/unit/Unit_Encoder) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U135`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                           | Model-specific reference                                                                                                                                        |
| ------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files                     | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U135_Unit_Encoder/Structures)                                         |
| Mechanical / CAD files                     | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U135_Unit_Encoder/Structures/Unit_Encoder.stl)                        |
| Official source: UNIT\_ENCODER             | [Read official source: unit\_encoder](https://github.com/m5stack/UNIT_ENCODER)                                                                                  |
| Example source: Unit\_Encoder\_M5Core.ino  | [Read example source: unit\_encoder\_m5core.ino](https://github.com/m5stack/M5Unit-Encoder/blob/master/examples/Unit_Encoder_M5Core/Unit_Encoder_M5Core.ino)    |
| Example source: Unit\_Encoder\_M5Core2.ino | [Read example source: unit\_encoder\_m5core2.ino](https://github.com/m5stack/M5Unit-Encoder/blob/master/examples/Unit_Encoder_M5Core2/Unit_Encoder_M5Core2.ino) |
| Official source: M5UnitEncoder\_Firmware   | [Read official source: m5unitencoder\_firmware](https://github.com/m5stack/M5UnitEncoder_Firmware)                                                              |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
