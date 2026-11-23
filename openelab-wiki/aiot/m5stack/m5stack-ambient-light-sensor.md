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

# M5Stack Ambient Light Sensor

{% hint style="info" %}
[**View M5Stack DLight Unit BH1750FVI Ambient Light Sensor Module on OpenELAB**](https://openelab.io/products/m5stack-dlight-unit)

**Store SKU / option:** `M5-U136`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Dlight Unit - Ambient Light Sensor

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-dlight-unit" %}

### Description <a href="#description" id="description"></a>

**DLight Unit** is a Digital Ambient Light Sensor. Adopts BH1750FVI sensor (I2C interface), integrates 16-bit ADC, supports wide-range LUX and high resolution (1 - 65535 LX). Compact in size, and low power consumption. Suitable for various light sensing applications.

### Features <a href="#product-features" id="product-features"></a>

* Support I2C interface (addr: 0x23)
* Illumination digital conversion
* Support light source variations (incandescent, fluorescent, halogen, white LED, sunlight, etc)
* Wide Range LUX (1-65535 lx)
* HY2.0-4P interface

### Applications <a href="#applications" id="applications"></a>

* Smart Factory
* Home Automation
* Ambient light Sensing Scenario

### Specification <a href="#specification" id="specification"></a>

| Specifications                      | Parameters                               |
| ----------------------------------- | ---------------------------------------- |
| Sensor Model                        | BH1750FVI                                |
| Illumination detection range        | 1-65535 lx                               |
| Communication interface             | I2C communication interface (addr: 0x23) |
| Typical peak sensitivity wavelength | 560nm                                    |
| Working current                     | < 5V@143uA                               |
| AD conversion depth                 | 16bit                                    |
| Net weight                          | 4.8g                                     |
| Gross weight                        | 10g                                      |
| Product Size                        | 32 \* 24 \* 8mm                          |
| Package Size                        | 93 \* 138mm                              |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/dlight/dlight_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/dlight/dlight_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/dlight/dlight_06.webp)

### PinMap <a href="#pinmap" id="pinmap"></a>

* DLight Unit

| M5Core(PORT A) | G21 | G22 | 5V  | GND |
| -------------- | --- | --- | --- | --- |
| DLight Unit    | SDA | SCL | VCC | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/dlight/dlight_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/DLight%20Unit/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit DLight](https://docs.m5stack.com/en/unit/Unit_DLight) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U136`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                               | Model-specific reference                                                                                                                                               |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files                         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U136_Unit_DLight/Structures)                                                 |
| Mechanical / CAD files                         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U136_Unit_DLight/Structures/Unit_DLight.stl)                                 |
| Official source: M5-DLight                     | [Read official source: m5-dlight](https://github.com/m5stack/M5-DLight)                                                                                                |
| Arduino development tutorial                   | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_dlight)                                                                     |
| Example source: Unit\_DLight\_M5Atom.ino       | [Read example source: unit\_dlight\_m5atom.ino](https://github.com/m5stack/M5-DLight/blob/master/examples/Unit_DLight_M5Atom/Unit_DLight_M5Atom.ino)                   |
| Example source: Unit\_DLight\_M5Core.ino       | [Read example source: unit\_dlight\_m5core.ino](https://github.com/m5stack/M5-DLight/blob/master/examples/Unit_DLight_M5Core/Unit_DLight_M5Core.ino)                   |
| Example source: Unit\_DLight\_M5Core2.ino      | [Read example source: unit\_dlight\_m5core2.ino](https://github.com/m5stack/M5-DLight/blob/master/examples/Unit_DLight_M5Core2/Unit_DLight_M5Core2.ino)                |
| Example source: Unit\_DLight\_M5StickC.ino     | [Read example source: unit\_dlight\_m5stickc.ino](https://github.com/m5stack/M5-DLight/blob/master/examples/Unit_DLight_M5StickC/Unit_DLight_M5StickC.ino)             |
| Example source: Unit\_DLight\_M5StickCPlus.ino | [Read example source: unit\_dlight\_m5stickcplus.ino](https://github.com/m5stack/M5-DLight/blob/master/examples/Unit_DLight_M5StickCPlus/Unit_DLight_M5StickCPlus.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
