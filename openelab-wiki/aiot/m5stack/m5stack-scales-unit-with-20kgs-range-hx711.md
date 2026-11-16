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

# M5Stack Scales Unit with 20kgs Range (HX711)

### M5Stack Scales Unit with 20kgs Range (HX711)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-scales-unit" %}

### Introduction

**UNIT Scales** is a high precision low-cost I2C port weighing sensor, with a total weighing range of 20kgs. Adopt **STM32F030** as the controller, **HX711** as sampling chip and 20 kgs weighing sensor. With tare button and programable **RGB** LED. This Unit offers the customer with a highly integrated weighing solution, suitable for the applications of weighing, item counting, item movement Checking and so on.

<figure><img src="../../.gitbook/assets/image (482).png" alt=""><figcaption></figcaption></figure>

### Features

* HX711:
  * High precision 24bit ADC
  * Programmable gain amplification 32, 64 and 128
  * 10SPS output data rate
* I2C port
* Development platform: Arduino, UIFlow(To be supported soon)

### Specifications

| Spec               | Parameters     |
| ------------------ | -------------- |
| MCU                | STM32F030      |
| ADC                | HX711          |
| Communication      | I2C:0x26       |
| LED                | SK6812(PA7)    |
| Function Button    | Tare (PA2)     |
| Gross Weight       | 96g            |
| Net Weight         | 87g            |
| Package Size       | 56\*40\*41mm   |
| Product Size       | 42\*43\*58mm   |
| Enclosure Material | Plastic ( PC ) |

### Pinout

| Scales Unit           | SCL    | SDA    | 5V | GND |
| --------------------- | ------ | ------ | -- | --- |
| M5Core(PORT A)        | GPIO22 | GPIO21 | 5V | GND |
| M5Core2(PORT A)       | GPIO22 | GPIO21 | 5V | GND |
| M5Atom(PORT A)        | GPIO32 | GPIO26 | 5V | GND |
| M5StickC/Plus(PORT A) | GPIO33 | GPIO32 | 5V | GND |
| M5Station(PORT A1,A2) | GPIO33 | GPIO32 | 5V | GND |

### Dimensions

<figure><img src="../../.gitbook/assets/image (483).png" alt=""><figcaption></figcaption></figure>

### How to Use

#### Arduino <a href="#arduino" id="arduino"></a>

* [Config Scales Unit I2C Address](https://github.com/m5stack/M5Unit-Scales/blob/main/examples/ADDR_CONFIG/ADDR_CONFIG.ino)
* [Scales Demo](https://github.com/m5stack/M5Unit-Scales/blob/main/examples/SCALES_TEST/SCALES_TEST.ino)
* [Scales Demo for ATOM](https://github.com/m5stack/M5Unit-Scales/blob/main/examples/SCALES_TEST/SCALES_TEST.ino)

After using ATOM to power on with Demo, you need to press the button to return to zero, otherwise the measurement is inaccurate.

#### UIFlow <a href="#uiflow" id="uiflow"></a>

![UIFlow2.0](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/uiflow2/guide/uiflow2_cover.png)

[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)This tutorial will show you how to initialize the configuration using the UIFlow2.0 graphical programming platform

[Scale Unit Programming Guide](https://uiflow-micropython.readthedocs.io/en/latest/units/miniscale.html)

<figure><img src="https://static-cdn.m5stack.com/mpy_docs/unit/miniscales/example.svg" alt=""><figcaption></figcaption></figure>

#### UIFlow example <a href="#uiflow-example" id="uiflow-example"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/scales/scales_uiflow_01.webp" alt=""><figcaption></figcaption></figure>
