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

# M5Stack Encoder

### M5Stack Encoder Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-encoder-unit" %}

### Description <a href="#description" id="description"></a>

**Unit Encoder** is a `rotary encoder` expansion unit with I2C interface, integrated with 30-bit pulse encoding knob (with button function) + 2 x SK6812 programmable RGB LEDs. The built-in STM32F030 flashed with the encoder pulse acquisition firmware, allowing users to obtain the encoded value directly via I2C. Suitable for scale value control/volume adjustment and other control scenarios.

### Features <a href="#features" id="features"></a>

* 30-bit pulse encoding knob (30 pulses per rotation)
* 2x SK6812 programmable RGB LEDs
* 1x Button input

### Applications <a href="#applications" id="applications"></a>

* Human Machine Interaction (HMI)
* Volume knob

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications       | Parameters                                 |
| -------------------- | ------------------------------------------ |
| Pulse encoder knob   | 30-bit pulse encoder knob (with key input) |
| Programmable RGB LED | 2x SK6812                                  |
| Working current      | Encoder working (DC-5V@17mA)               |
| Net weight           | 7.4g                                       |
| Gross weight         | 12.3g                                      |
| Product size         | 32 \* 24 \* 22mm                           |
| Packing size         | 93 \* 138mm                                |

### PinMap <a href="#pinmap" id="pinmap"></a>

* Unit Encoder

| M5Core(PORT A) | GPIO22 | GPIO21 | 5V | GND |
| -------------- | ------ | ------ | -- | --- |
| Unit Encoder   | SCL    | SDA    | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/encoder/encoder_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (382).png" alt=""><figcaption></figcaption></figure>
