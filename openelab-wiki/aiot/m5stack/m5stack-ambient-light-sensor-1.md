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
[**View M5Stack DLight HAT BH1750FVI Ambient Light Sensor for M5StickC on OpenELAB**](https://openelab.io/products/m5stickc-light-sensor)

**Store SKU / option:** `M5-U134`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack M5StickC HAT - Ambient Light Sensor

***

### Product Link

{% embed url="https://openelab.io/products/m5stickc-light-sensor" %}

### Description <a href="#description" id="description"></a>

**DLight HAT** Digital Ambient Light Sensor extends M5StickC/C Plus to have ambient light sensing capability. Adopts BH1750FVI sensor (I2C interface), integrates 16-bit ADC, supports wide-range LUX and high resolution (1 - 65535 LX). Compact in size, and low power consumption. Suitable for various light sensing applications.

### Features <a href="#product-features" id="product-features"></a>

* Compatible with M5StickC/C Plus
* Support I2C interface (addr: 0x23)
* Illumination digital conversion
* Support light source variations (incandescent, fluorescent, halogen, white LED, sunlight, etc)
* Wide Range LUX (1-65535 lx)

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
| Working current                     | <3.3V@0.3mA                              |
| AD conversion depth                 | 16bit                                    |
| Net weight                          | 4.8g                                     |
| Gross weight                        | 6.8g                                     |
| Product Size                        | 25 \* 24 \* 14mm                         |
| Package Size                        | 93 \* 138mm                              |

![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat_dlight/hat_dlight_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat_dlight/hat_dlight_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat_dlight/hat_dlight_06.webp)

### PinMap <a href="#pinmap" id="pinmap"></a>

* HAT DLight

| M5StickC   | G0  | G26 | 3.3V | GND |
| ---------- | --- | --- | ---- | --- |
| HAT DLight | SDA | SCL | VCC  | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat_dlight/hat_dlight_sch_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Hat DLight](https://docs.m5stack.com/en/hat/Hat_DLight) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U134`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                              | Model-specific reference                                                                                                                                            |
| --------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files                        | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U134_Hat_DLight/Structures)                                               |
| Mechanical / CAD files                        | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U134_Hat_DLight/Structures/Hat_DLight.stl)                                |
| Official source: M5-DLight                    | [Read official source: m5-dlight](https://github.com/m5stack/M5-DLight)                                                                                             |
| Example source: Hat\_DLight\_M5StickC.ino     | [Read example source: hat\_dlight\_m5stickc.ino](https://github.com/m5stack/M5-DLight/blob/master/examples/Hat_DLight_M5StickC/Hat_DLight_M5StickC.ino)             |
| Example source: Hat\_DLight\_M5StickCPlus.ino | [Read example source: hat\_dlight\_m5stickcplus.ino](https://github.com/m5stack/M5-DLight/blob/master/examples/Hat_DLight_M5StickCPlus/Hat_DLight_M5StickCPlus.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
