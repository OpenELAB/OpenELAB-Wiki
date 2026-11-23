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

# M5Stack PIR Hat

{% hint style="info" %}
[**View M5Stack Hat PIR Human Body Infrared Sensor for M5StickC on OpenELAB**](https://openelab.io/products/m5stickc-pir-hat)

**Store SKU / option:** `M5-U054`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack M5StickC PIR Hat (AS312)

***

### Product Link

{% embed url="https://openelab.io/products/m5stickc-pir-hat" %}

### Description <a href="#description" id="description"></a>

**PIR HAT** is an M5StickC compatible human body induction sensor, it belongs to "Passive pyroelectric infrared detector", that detect the infrared come from the human body. When the infrared is detected, the sensor will output HIGH and last for two seconds until the next detecting round.

\*Notice: There exist 2 seconds delay\*

### Features <a href="#product-features" id="product-features"></a>

* Detecting Range: 500cm
* Delay time: 2s
* Induction Angle: < 100°
* IDDQ : < 60uA
* Op.T: -20 - 80 °C

### Applications <a href="#applications" id="applications"></a>

* Human body induction lamp
* Security product
* Auto-induction

### Specification <a href="#specification" id="specification"></a>

| Resources    | Parameter     |
| ------------ | ------------- |
| Net weight   | 5g            |
| Gross weight | 12g           |
| Product Size | 24\*25\*20mm  |
| Package Size | 136\*92\*21mm |

![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat-pir/hat-pir_03.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/hat/hat-pir/hat-pir_06.webp)

#### Pin Map <a href="#pin-map" id="pin-map"></a>

| M5StickC | GPIO36 | 5V | GND |
| -------- | ------ | -- | --- |
| HAT PIR  | OUT    | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat-pir/hat-pir_sch_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Hat PIR](https://docs.m5stack.com/en/hat/Hat_PIR) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U054`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need         | Model-specific reference                                                                                                       |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Electrical schematic     | [Read electrical schematic](https://github.com/m5stack/M5-Schematic/blob/master/Hat/StickHat_PIR.pdf)                          |
| Mechanical / CAD files   | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U054_Hat_PIR/Structures)             |
| Mechanical / CAD files   | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U054_Hat_PIR/Structures/Hat_PIR.stl) |
| Example source: M5StickC | [Read example source: m5stickc](https://github.com/m5stack/M5StickC/tree/master/examples/Hat/PIR)                              |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
