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

# M5Stack Weight

{% hint style="info" %}
[**View M5Stack Weight I2C Unit HX711 24-Bit Load Cell Measurement Module on OpenELAB**](https://openelab.io/products/m5stack-weight-i2c-unit)

**Store SKU / option:** `M5-U180`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Weight I2C Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-weight-i2c-unit" %}

### Description <a href="#description" id="description"></a>

The **Weight I2C Unit** is a weight acquisition transducer unit that employs the "STM32+HX711 chip" solution, achieving precision weight measurement with 24-bit accuracy through I2C communication. It supports the parallel connection of multiple devices on the same I2C bus, providing users with greater flexibility in terms of a wider range and more data collection points. It is suitable for various applications such as industrial production, healthcare, logistics, laboratory research, and food processing.

### Features <a href="#features" id="features"></a>

* STM32F030F4P6+HX711
* 24Bit measurement accuracy
* I2C serial communication
* Program platform: Arduino, UIFlow, etc

### Applications <a href="#applications" id="applications"></a>

* Microgravimeter
* Food Processing
* Logistics Transportation
* Laboratory Investigation

### Specification <a href="#specification" id="specification"></a>

| Resources             | Parameters        |
| --------------------- | ----------------- |
| Resolution            | 24Bit             |
| Communication Mode    | I2C（0x26）         |
| Operating Temperature | 0-40°C            |
| Product Size          | 32\*24\*11.3mm    |
| Package Size          | 136\* 92\* 13.7mm |
| Product Weight        | 5.2g              |
| Package Weight        | 12.9g             |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-Weight%20I2C/img-a4d8bc9a-3926-4265-b108-6501b25fcf3d.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-Weight%20I2C/img-da7c0ae5-b2ca-4371-9d0a-1b7e06b262f5.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-Weight%20I2C/img-d890ef48-fe47-4ae6-bc79-4e920f913e53.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-Weight%20I2C/img-f0cbbc11-3f81-4d72-8080-b4ad1eacdb7a.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-Weight%20I2C/img-c6a9d8b4-a856-4eb1-9590-456113a5f7ff.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-Weight%20I2C/img-a34e63d1-fb5a-4f49-bf40-94e4c287b700.webp)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-Weight%20I2C/img-ea9760d2-6da4-4d32-b79e-9ee08a78375b.png" alt=""><figcaption></figcaption></figure>

* Connection Schematic Diagram

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-Weight%20I2C/en.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-Weight%20I2C/pinMap-345d1407-778c-4b6f-99ca-7ecb5a21e48e.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-Weight%20I2C/img-c48c5579-3111-4266-8f9b-9e748e4bccef.jpg" alt=""><figcaption></figcaption></figure>

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-Weight%20I2C/protocol-d35ec78e-c48e-44ae-93b5-ddb10418ce88.png" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (946).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Weight-I2C](https://docs.m5stack.com/en/unit/Unit_Weight-I2C) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U180`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                  | Model-specific reference                                                                                                                       |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic              | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/632/SCH_UNIT_WEIGHT_I2C.pdf)                                      |
| Mechanical / CAD files            | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U180_Unit_Weight-I2C/Structures)                     |
| Mechanical / CAD files            | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U180_Unit_Weight-I2C/Structures/Unit_Weight-I2C.stl) |
| Official source: M5Unit-WeightI2C | [Read official source: m5unit-weighti2c](https://github.com/m5stack/M5Unit-WeightI2C)                                                          |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
