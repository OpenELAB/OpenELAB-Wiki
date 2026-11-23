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

# M5Stack RS485 to TTL Converter

{% hint style="info" %}
[**View M5Stack RS485 to TTL Converter Unit on OpenELAB**](https://openelab.io/products/m5stack-rs485)

**Store SKU / option:** `M5-U034`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack RS485 to TTL Converter Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-rs485" %}

### Description <a href="#description" id="description"></a>

**RS485** is a TTL to RS485 convertor.

RS485 is a standard defining the electrical characteristics of drivers and receivers for use in serial communications systems, widely used in industrial field. multi-point systems are supported.

It's used to convert the TTL standard to the RS485 standard. If the outside serial device is RS485 standard, you can attach this unit onto M5stack, therefore, to implement the communication with RS485 device by TTL protocol.

### Features <a href="#features" id="features"></a>

* Built in MAX485/SP485EEN
* input DC 12V
* Program Platform: Arduino, UIFlow (Blockly, Python)
* Two Lego-compatible holes

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter     |
| ------------ | ------------- |
| Net weight   | 8g            |
| Gross weight | 21g           |
| Product Size | 40\*24\*14mm  |
| Package Size | 136\*92\*12mm |

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE C) | U2RXD(GPIO16) | U2TXD(GPIO17) | 5V | GND |
| --------------- | ------------- | ------------- | -- | --- |
| RS485 Unit      | RS485 RXD     | RS485 TXD     | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/rs485/rs485_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Datasheets <a href="#datasheets" id="datasheets"></a>

* **Datasheet** - [SP485EEN](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/hat/SP485EEN_en.pdf)

### Compatible

<figure><img src="../../.gitbook/assets/image (368).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit RS485](https://docs.m5stack.com/en/unit/Unit_RS485) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U034`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                             |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U034_Unit_RS485/Structures)                |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U034_Unit_RS485/Structures/Unit_RS485.stl) |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/RS485_SP485EEN)                          |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
