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

# M5Stack Ext Encoder

{% hint style="info" %}
[**View M5Stack Unit ExtEncoder M5-U161 STM32F030 Rotary Encoder Module on OpenELAB**](https://openelab.io/products/m5stack-ext-encoder-unit)

**Store SKU / option:** `M5-U161`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Ext Encoder Unit (STM32F030)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-ext-encoder-unit" %}

### Description <a href="#description" id="description"></a>

`ExtEncoder unit` is an acquisition unit for `external rotary encoder`, supporting `AB/ABZ signal input`, using `STM32F030` main control integrated encoder signal acquisition and decoding firmware, users can directly obtain the encoded value through the `I2C` reading operation, suitable for example, `robot arm position control, automatic cutting in the field of industrial automation, meter wheel`, etc.

### Features <a href="#features" id="features"></a>

* Supports signal acquisition with external rotary encoders
* Support AB/ABZ signal input
* Built-in STM32F030 main control, integrated encoder signal acquisition and decoding firmware
* The encoded value can be obtained directly through the I2C read operation

### Applications <a href="#applications" id="applications"></a>

* Meter counting applications
* encoder
* Automated cutting

### Specifications <a href="#specifications" id="specifications"></a>

| Resources         | Parameters   |
| ----------------- | ------------ |
| Sampling accuracy | 12 bit       |
| Signal input type | AB/ABZ       |
| I2C Address       | 0x59         |
| Product Size      | 40\*24\*14mm |
| Package Size      | 67\*53\*12mm |
| Product Weight    | 8g           |
| Package Weight    | 21g          |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ExtEncoder%20Unit/img-28f25de7-d6f8-4b1a-8688-d88bd597c403.png" alt=""><figcaption></figcaption></figure>

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ExtEncoder%20Unit/arduinoCase-1683862277316pinmap.png" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (388).png" alt=""><figcaption></figcaption></figure>

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
