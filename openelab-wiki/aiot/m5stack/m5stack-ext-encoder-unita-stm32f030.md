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

# M5Stack Ext Encoder Unita (STM32F030)

{% hint style="info" %}
[**View M5Stack Unit ExtEncoder M5-U161 STM32F030 Rotary Encoder Module on OpenELAB**](https://openelab.io/products/m5stack-ext-encoder-unit)

**Store SKU / option:** `M5-U161`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Ext Encoder Unita (STM32F030)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-ext-encoder-unit" %}

### Introduction

ExtEncode unit is a versatile acquisition unit designed for external rotary encoders. It seamlessly supports AB/ABZ signal input, allowing for accurate and reliable encoding. Powered by the STM32F030 main control chip, this unit incorporates firmware that enables efficient acquisition and decoding of encoder signals.

Users can easily access the encoded value by performing I2C reading operations, simplifying the integration process. This makes it an ideal solution for various applications, including robot arm position control, automatic cutting in industrial automation, and meter wheel applications.

ExtEncode unit empowers engineers and professionals to achieve precise position control and measurement in their projects. With its robust firmware and compatibility with external rotary encoders, it provides a reliable and efficient solution for acquiring and utilizing encoded data.

<figure><img src="../../.gitbook/assets/image (511).png" alt=""><figcaption></figcaption></figure>

### Features

* Supports signal acquisition with external rotary encoders
* Support AB/ABZ signal input
* Built-in STM32F030 main control, integrated encoder signal acquisition and decoding firmware
* The encoded value can be obtained directly through the I2C read operation

### Specifications

| Resources         | Parameters   |
| ----------------- | ------------ |
| Sampling accuracy | 12 bit       |
| Signal input type | AB/ABZ       |
| I2C Address       | 0x59         |
| Product Size      | 40\*24\*14mm |
| Package Size      | 67\*53\*12mm |
| Product Weight    | 8g           |
| Package Weight    | 21g          |

### Dimensions

Size:40\*24\*14mm

weight:8g

### How to Use

Connect the M5Stack Ext Encoder Unita to your M5Stack Core using the appropriate GROVE port. Ensure the connections are secure.

## Official documentation and development resources

Use [Unit ExtEncoder](https://docs.m5stack.com/en/unit/Unit_ExtEncoder) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U161`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                               | Model-specific reference                                                                                                                       |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic                           | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/616/SCH_UNIT_EXTEncoder.pdf)                                      |
| Mechanical / CAD files                         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U161_Unit_ExtEncoder/Structures)                     |
| Mechanical / CAD files                         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U161_Unit_ExtEncoder/Structures/Unit_ExtEncoder.stl) |
| Official source: M5Unit-ExtEncoder             | [Read official source: m5unit-extencoder](https://github.com/m5stack/M5Unit-ExtEncoder)                                                        |
| Official source: M5Unit-ExtEncoder-Internal-FW | [Read official source: m5unit-extencoder-internal-fw](https://github.com/m5stack/M5Unit-ExtEncoder-Internal-FW)                                |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
