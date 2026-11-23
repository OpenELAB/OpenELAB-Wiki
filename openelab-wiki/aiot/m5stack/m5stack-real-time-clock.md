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

# M5Stack Real Time Clock

{% hint style="info" %}
[**View M5Stack Real Time Clock (RTC) Unit on OpenELAB**](https://openelab.io/products/real-time-clock-rtc-unit)

**Store SKU / option:** `M5-U126`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Real Time Clock (RTC) Unit

***

### Product Link

{% embed url="https://openelab.io/products/real-time-clock-rtc-unit" %}

### Description <a href="#description" id="description"></a>

**UNIT RTC** is a programmable real-time clock module, integrated HYM8563 low-power CMOS real-time clock/calendar chip, using I2C communication interface, full-coverage case can effectively protect the circuit, making its operation more stable. Applicable to a variety of embedded devices, instruments and instruments as a system clock.

### Features <a href="#features" id="features"></a>

* Support second/minute/hour/day/month/year. time data reading and writing
* 32.768kHz high-precision clock crystal, greatly reducing the time error
* Low power consumption, coin battery can work continuously for years
* With century mark
* I2C communication interface

### Applications <a href="#applications" id="applications"></a>

* Clock, alarm clock
* Power down time synchronization

### Specifications <a href="#specifications" id="specifications"></a>

| Resources               | Parameters                             |
| ----------------------- | -------------------------------------- |
| Clock chip              | HYM8563                                |
| Crystal Frequency       | 32.768kHz                              |
| Communication interface | I2C, addr: 0x51, bus max speed 400Kbps |
| Power supply voltage    | 5V DC                                  |
| Product Size            | 48 \* 24 \* 8mm                        |
| Package Size            | 136\* 92\* 13mm                        |
| Product Weight          | 4.1g                                   |
| Package Weight          | 8.3g                                   |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%20RTC/img-6f0baa97-c15f-4c85-be56-12078e7a7dd2.webp" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/UNIT%20RTC/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (956).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit RTC](https://docs.m5stack.com/en/unit/Unit_RTC) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U126`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                            | Model-specific reference                                                                                                                                       |
| ------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files                      | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U126_Unit_RTC/Structures)                                            |
| Mechanical / CAD files                      | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U126_Unit_RTC/Structures/Unit_RTC.stl)                               |
| Example source: Unit\_RTC\_M5Series.ino     | [Read example source: unit\_rtc\_m5series.ino](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5Series/Unit_RTC_M5Series.ino)             |
| Example source: Unit\_RTC\_M5Atom.ino       | [Read example source: unit\_rtc\_m5atom.ino](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5Atom/Unit_RTC_M5Atom.ino)                   |
| Example source: Unit\_RTC\_M5Core.ino       | [Read example source: unit\_rtc\_m5core.ino](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5Core/Unit_RTC_M5Core.ino)                   |
| Example source: Unit\_RTC\_M5Core2.ino      | [Read example source: unit\_rtc\_m5core2.ino](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5Core2/Unit_RTC_M5Core2.ino)                |
| Example source: Unit\_RTC\_M5StickC.ino     | [Read example source: unit\_rtc\_m5stickc.ino](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5StickC/Unit_RTC_M5StickC.ino)             |
| Example source: Unit\_RTC\_M5StickCPlus.ino | [Read example source: unit\_rtc\_m5stickcplus.ino](https://github.com/m5stack/M5Unit-RTC/blob/master/examples/Unit_RTC_M5StickCPlus/Unit_RTC_M5StickCPlus.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
