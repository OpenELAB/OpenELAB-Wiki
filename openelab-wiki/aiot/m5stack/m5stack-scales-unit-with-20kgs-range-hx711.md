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

{% hint style="info" %}
[**View M5Stack Scales Unit with 20kgs Range on OpenELAB**](https://openelab.io/products/scales-unit)

**Store SKU / option:** `M5-U108`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Scales Unit with 20kgs Range (HX711)

***

### Product Link

{% embed url="https://openelab.io/products/scales-unit" %}

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

## Official documentation and development resources

Use [Unit Scales](https://docs.m5stack.com/en/unit/Unit_Scales) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U108`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                           | Model-specific reference                                                                                                               |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic                       | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/592/Sch_UNIT-Scales.pdf)                                  |
| Mechanical / CAD files                     | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U108_Unit_Scales/Structures)                 |
| Mechanical / CAD files                     | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U108_Unit_Scales/Structures/Unit_Scales.stl) |
| Official source: M5Unit-Scales             | [Read official source: m5unit-scales](https://github.com/m5stack/M5Unit-Scales)                                                        |
| Arduino development tutorial               | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_scales)                                     |
| Example source: SCALES\_TEST.ino           | [Read example source: scales\_test.ino](https://github.com/m5stack/M5Unit-Scales/blob/main/examples/SCALES_TEST/SCALES_TEST.ino)       |
| Official source: M5Unit-Scales-Internal-FW | [Read official source: m5unit-scales-internal-fw](https://github.com/m5stack/M5Unit-Scales-Internal-FW)                                |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
