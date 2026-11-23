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

# M5Stack Watering Unit with Mositure Sensor and Pump

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

### Features <a href="#product-features" id="product-features"></a>

* Capacitive measuring plate (corrosion resistant)
* Integrated 5W power water pump
* LEGO compatible holes

### Application <a href="#application" id="application"></a>

* Plant cultivation
* Soil moisture detection
* Smart irrigation

### Specification <a href="#specification" id="specification"></a>

| Resources    | Parameter       |
| ------------ | --------------- |
| Pump power   | 5W              |
| Net Weight   | 78g             |
| Gross Weight | 103g            |
| Product Size | 192.5\*24\*33mm |
| Package Size | 200\*35\*45mm   |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/watering/watering_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/watering/watering_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/watering/watering_06.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/watering/watering_07.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

* **Windows**
  * [Watering Test](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/UNIT/For%20M5Core/EasyLoader_WATERING_UNIT_With_M5Core.exe)
* **MacOS**
  * [Watering Test](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/MacOS/UNIT/EasyLoader_Watering_UNIT_With_M5Core.dmg)

### Pinout <a href="#pinmap" id="pinmap"></a>

| M5Core(PORT B) | GPIO26 | GPIO36 | 5V | GND |
| -------------- | ------ | ------ | -- | --- |
| Watering Unit  | PUMP   | INPUT  | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/watering/watering_sch_01.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/watering/watering_sch_02.webp" alt=""><figcaption></figcaption></figure>

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [Click here to download the Arduino example](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/WATERING)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/WATERING/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/watering/watering_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Watering](https://docs.m5stack.com/en/unit/Unit_Watering) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U101`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                                   |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U101_Unit_Watering/Structures)                   |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U101_Unit_Watering/Structures/Unit_Watering.stl) |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/WATERING)                                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
