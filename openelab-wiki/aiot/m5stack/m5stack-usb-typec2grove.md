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

# M5Stack USB TypeC2Grove

{% hint style="info" %}
[**View M5Stack USB TypeC2Grove Unit M5-U151 5V 3A Grove Power Hub on OpenELAB**](https://openelab.io/products/usb-typec2grove-unit)

**Store SKU / option:** `M5-U151`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack USB TypeC2Grove Unit

***

### Product Link

{% embed url="https://openelab.io/products/usb-typec2grove-unit" %}

### Description <a href="#description" id="description"></a>

**UNIT TypeC2Grove** is one Grove hub Unit with **USB TypeC** 5V DC input. Powered through USB-C port, the first channel is Singal Input, the second and third channels are Power and Singal Output. Applied for the Units which need external 5V DC power.

### Applications <a href="#applications" id="applications"></a>

* RGB LED Unit power-up
* Sensor power-up
* Actuator power-up
* DIY

### Specifications <a href="#specifications" id="specifications"></a>

| Spec         | Parameters    |
| ------------ | ------------- |
| Power Supply | MAX 5V@3A     |
| Net Weight   | 4.9g          |
| Gross Weight | 10.7g         |
| Product Size | 32\*24\*12mm  |
| Package Size | 136\*92\*13mm |

### PinMap <a href="#pinmap" id="pinmap"></a>

| PORT | WHITE  | YELLOW | RED  | BLACK |
| ---- | ------ | ------ | ---- | ----- |
| CN2  | SCL/RX | SDA/TX | NULL | GND   |
| CN3  | SCL/RX | SDA/TX | +5V  | GND   |
| CN4  | SCL/RX | SDA/TX | +5V  | GND   |

![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/typec2grove/typec2grove_10.webp)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/typec2grove/typec2grove_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#size" id="size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/typec2grove/typec2grove_size_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit TypeC to Grove](https://docs.m5stack.com/en/unit/Unit_TypeC_to_Grove) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U151`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                                                 |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U151_Unit_TypeC_to_Grove/Structures)                           |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U151_Unit_TypeC_to_Grove/Structures/Unit_TypeC%20to_Grove.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
