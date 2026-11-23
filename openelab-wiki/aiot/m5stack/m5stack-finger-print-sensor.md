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

# M5Stack Finger Print Sensor

{% hint style="info" %}
[**View M5Stack Finger Print Sensor Unit on OpenELAB**](https://openelab.io/products/finger-print-sensor-unit)

**Store SKU / option:** `M5-U008`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Finger Print Sensor Unit

***

### Product Link

{% embed url="https://openelab.io/products/finger-print-sensor-unit" %}

### Description <a href="#description" id="description"></a>

**FINGER** Unit is a fingerprint sensor based on the FPC1020A chipset.

This all-in-one fingerprint sensor makes fingerprint adding, verification and managing super simple.

Operated by the UART protocol, Compact size and ultra-low power consumption makes it very attractive to use around M5Stack series product. it performs fast fingerprint matching with highest security level and optimal user convenience. You can program to set the fingerprint recognition comparison level and different security level . if you ever consider secure your project with biometrics, don't forget to include this M5unit **FINGER**.

**This unit communicate with M5Core by UART protocol connected via PORTC**

UART settings:

* Baudrate(**default: 19200bps**)
* Start bits(1 bit)
* Stop bits(1 bit)
* Parity(no)

### Features <a href="#features" id="features"></a>

* Use capacitive area array semiconductor fingerprint sensor
* Each pixel of the sensor has a pixel quality of 256 gray levels
* 1: N recognition and 1: 1 verification function
* Support finger 360 rotation recognition
* Fingerprint comparison and search function

### Applications <a href="#applications" id="applications"></a>

* Fingerprint Attendance Machine
* Fingerprint Locker

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                 | Parameter                       |
| ------------------------- | ------------------------------- |
| Fingerprint capacity      | 150                             |
| Security level            | 0-9, default 5                  |
| Output format             | User name, image, feature value |
| Characteristic value size | 193Byte                         |
| Communication method      | UART (9600-115200)              |
| Working temperature       | -10 °C-60 °C                    |
| Relative humidity         | 20% -80%                        |
| Net weight                | 7g                              |
| Gross weight              | 20g                             |
| Product Size              | 48\*24\*8mm                     |
| Package Size              | 136\*93\*12mm                   |

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE C) | U2RXD | U2TXD | 5V | GND |
| --------------- | ----- | ----- | -- | --- |
| FINGER Unit     | TXD   | RXD   | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/finger/finger_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/finger/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (378).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Finger](https://docs.m5stack.com/en/unit/Unit_Finger) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U008`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                               |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U008_Unit_Finger/Structures)                 |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U008_Unit_Finger/Structures/Unit_Finger.stl) |
| Official source: M5-FPC1020A | [Read official source: m5-fpc1020a](https://github.com/m5stack/M5-FPC1020A)                                                            |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_finger)                                     |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
