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

# M5Stack 8-Angle Unit with Potentiometer

{% hint style="info" %}
[**View M5Stack 8Angle Unit with 8 Potentiometers and RGB Feedback on OpenELAB**](https://openelab.io/products/8-angle-unit)

**Store SKU / option:** `M5-U154`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack 8-Angle Unit with Potentiometer

***

### Product Link

{% embed url="https://openelab.io/products/8-angle-unit" %}

### Introduction

8Angle unit is an input unit that combines eight adjustable potentiometers to provide precise control functionality. It utilizes an internal STM32F030 microcomputer as the acquisition and communication processor, enabling efficient data processing and communication. The unit communicates with the host computer using the I2C communication interface, ensuring seamless integration into various systems.

Each adjustable potentiometer is accompanied by a corresponding RGB LED light, allowing for visual feedback and state indication. The unit also includes a physical toggle switch and its corresponding RGB LED light, providing an additional input method.

To ensure proper functionality, the UNIT 8Angle incorporates a 5V to 3.3V DCDC circuit, allowing for reliable power supply and compatibility with different systems. With this unit, users can input multi-channel absolute control values, with each corresponding RGB lamp displaying different states. The toggle switch enables multi-channel switching input, further enhancing the control capabilities.

8Angle unit finds applications in various fields, such as multi-degree-of-freedom robots or music equalization systems. Its adjustable potentiometers provide precise and granular control, allowing users to fine-tune parameters or settings. The visual feedback from the RGB LED lights enhances the user experience and enables quick recognition of different states. Whether it's controlling robot joints or adjusting music equalization parameters, the UNIT 8Angle unit offers a versatile and intuitive input solution.

<figure><img src="../../.gitbook/assets/image (521).png" alt=""><figcaption></figcaption></figure>

### Features

* 8-channel adjustable potentiometer
* 8 channels correspond to RGB lights
* I2C communication
* Toggle switches can be used for multi-channel switching inputs

### Specifications

| Resources                 | Parameters             |
| ------------------------- | ---------------------- |
| MCU                       | STM32F030F4P6          |
| LDO                       | ME6210A33M3G           |
| RGB                       | SK6812-3535            |
| Input voltage             | 5v                     |
| I2C communication address | 0x43                   |
| Product Size              | 128mm × 24mm ×22.7mm   |
| Package Size              | 130mm × 27.7mm ×27.7mm |
| Product Weight            | 34.9g                  |
| Package Weight            | 44.3g                  |

### Pinout

<figure><img src="../../.gitbook/assets/image (504).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (505).png" alt=""><figcaption></figcaption></figure>

### How to Use

* [Arduino Example](https://github.com/m5stack/M5Unit-8Angle)

<figure><img src="../../.gitbook/assets/image (507).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit 8Angle](https://docs.m5stack.com/en/unit/Unit_8Angle) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U154`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                           | Model-specific reference                                                                                                               |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic                       | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/608/SCH_UNIT_8Angle_V1.01.pdf)                            |
| Mechanical / CAD files                     | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U154_Unit_8Angle/Structures)                 |
| Mechanical / CAD files                     | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U154_Unit_8Angle/Structures/Unit_8Angle.stl) |
| Official source: M5Unit-8Angle             | [Read official source: m5unit-8angle](https://github.com/m5stack/M5Unit-8Angle)                                                        |
| Arduino development tutorial               | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_8angle)                                     |
| Official source: M5Unit-8Angle-Internal-FW | [Read official source: m5unit-8angle-internal-fw](https://github.com/m5stack/M5Unit-8Angle-Internal-FW)                                |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
