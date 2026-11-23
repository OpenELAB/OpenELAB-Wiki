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

# M5Stack Red 7-Segment Digit Clock

{% hint style="info" %}
[**View M5Stack Red 7-Segment Digit Clock Unit M5-U146 TM1637 I2C Display on OpenELAB**](https://openelab.io/products/m5stack-digit-clock-unit)

**Store SKU / option:** `M5-U146`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Red 7-Segment Digit Clock Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-digit-clock-unit" %}

### Description <a href="#description" id="description"></a>

**UNIT-Digi-Clock** is a 2.1 inch 4-digit 7-segment display module. There are decimal points on each digit and an extra wire for colon-dots in the center, which can display Decimals and Clock. This module adopts TM1637 as the driver IC, and STM32F030 as I2C communication. I2C address can be modified per 4-bit dip switch. The red LED supports 8 brightness. And we have reserved 4 fixing holes there.

### Features <a href="#features" id="features"></a>

* 4-digit red dislpay
* I2C port, adjustable I2C address
* 8 brightness
* Low power consumption
* 4 fixing holes for multiple installations

### Applications <a href="#applications" id="applications"></a>

* Clock display
* Data display
* Stop watch

### Specifications <a href="#specifications" id="specifications"></a>

| Spec              | Parameters        |
| ----------------- | ----------------- |
| MCU               | STM32F030         |
| Driver IC         | TM1637            |
| Communication     | I2C, addr: 0x30   |
| Power Supply      | 5V DC             |
| Net Weight        | 12.5g             |
| Gross Weight      | 17.8g             |
| Product Dimension | 50 \* 31 \* 14mm  |
| Package Dimension | 136 \* 92 \* 15mm |

### Power Consumption Testing <a href="#power-consumption-testing" id="power-consumption-testing"></a>

| Environments          | Current on DC5V |
| --------------------- | --------------- |
| Standby Mode(All off) | 2.5mA           |
| SG1                   | 6.6mA           |
| SG2                   | 10.3mA          |
| SG3                   | 17.5mA          |
| SG4                   | 38.7mA          |
| SG5                   | 42.0mA          |
| SG6                   | 45.7mA          |
| SG7                   | 49.2mA          |
| SG8(All on)           | 52.5mA          |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/digi_clock/digi_clock_sch_01.webp" alt=""><figcaption></figcaption></figure>

### I2C Register Table <a href="#i2c-register-table" id="i2c-register-table"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/digi_clock/digi_clock_sch_02.webp" alt=""><figcaption></figcaption></figure>

### Character cross-reference table <a href="#character-cross-reference-table" id="character-cross-reference-table"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/digi_clock/digi_clock_sch_03.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit DigiClock](https://docs.m5stack.com/en/unit/Unit_DigiClock) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U146`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                  | Model-specific reference                                                                                  |
| --------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Electrical schematic              | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/601/Sch_UNIT_Digi-Clock.pdf) |
| Official source: M5Unit-DigiClock | [Read official source: m5unit-digiclock](https://github.com/m5stack/M5Unit-DigiClock)                     |
| Arduino development tutorial      | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_digiclock)     |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
