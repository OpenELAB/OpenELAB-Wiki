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

# M5Stack Watering Unit

{% hint style="info" %}
[**View M5Stack Watering Unit with Mositure Sensor and Pump on OpenELAB**](https://openelab.io/products/m5stack-watering-unit)

**Store SKU / option:** `M5-U101`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Watering Unit with Mositure Sensor and Pump

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-watering-unit" %}

### Description <a href="#description" id="description"></a>

**Watering** is a capacitive soil moisture detection and adjustment unit. The product integrates water pump and measuring plates for soil moisture detection and pump water control. It can be used for intelligent plant breeding scenarios and can easily achieve humidity detection and Irrigation control. The measurement electrode plate uses the capacitive design, which can effectively avoid the corrosion problem of the electrode plate in actual use compared with the resistive electrode plate.

### Features <a href="#features" id="features"></a>

* Capacitive measuring plate (corrosion resistant)
* Integrated 5W power water pump
* LEGO compatible holes

### Applications <a href="#applications" id="applications"></a>

* Plant cultivation
* Soil moisture detection
* Smart irrigation

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter       |
| ------------ | --------------- |
| Pump power   | 5W              |
| Net Weight   | 78g             |
| Gross Weight | 103g            |
| Product Size | 192.5\*24\*33mm |
| Package Size | 200\*35\*45mm   |

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(PORT B) | GPIO26 | GPIO36 | 5V | GND |
| -------------- | ------ | ------ | -- | --- |
| Watering Unit  | PUMP   | INPUT  | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="../../.gitbook/assets/image (958).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (959).png" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/watering/module_size.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (960).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Watering](https://docs.m5stack.com/en/unit/Unit_Watering) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U101`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                                   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U101_Unit_Watering/Structures)                   |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U101_Unit_Watering/Structures/Unit_Watering.stl) |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/WATERING)                                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
