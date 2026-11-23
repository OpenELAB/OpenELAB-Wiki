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

# M5Stack PIR Motion Sensor

{% hint style="info" %}
[**View M5Stack PIR Motion Sensor on OpenELAB**](https://openelab.io/products/pir-motion-sensor)

**Store SKU / option:** `M5-U004`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack PIR Motion Sensor

***

### Product Link

{% embed url="https://openelab.io/products/pir-motion-sensor" %}

### Description <a href="#description" id="description"></a>

**PIR** is a human body infrared unit. It belongs to the "passive pyroelectric infrared detector". It detects the infrared radiation emitted and reflected by the human body or object. When infrared is detected, the output level is high and it takes a while. Delay (high during the period and allow repeated triggers) until the trigger signal disappears (restores low).

This Unit communicates with the M5Core via the GROVE B.

\*Notice: This Unit has 2s delay time.\*

### Features <a href="#features" id="features"></a>

* Detects the distance: 500cm
* latency time: 2s
* Sensing range: < 100°
* Quiescent current: < 60uA
* Operating temperature: -20 - 80 °C
* GROVE interface, support UIFlow and Arduino
* Two Lego installation holes

### Applications <a href="#applications" id="applications"></a>

* Human body Induction Lamp
* Security Product
* Automatic Induction Appliance Settings

### Specification <a href="#specification" id="specification"></a>

| Resources      | Parameters   |
| -------------- | ------------ |
| Product Size   | 32\*24\*12mm |
| Package Size   | 60\*57\*17mm |
| Product Weight | 5g           |
| Package Weight | 20g          |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/PIR/img-958951eb-482b-443b-9e98-fb752819607b.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/PIR/img-d3d367ff-4aa0-43f5-bff0-c32d9fe9e45c.webp)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/PIR/img-648f0917-5412-406c-8672-b5c864f8b505.webp" alt=""><figcaption></figcaption></figure>

### EasyLoader <a href="#easyloader" id="easyloader"></a>

* **Windows**
  * [EasyLoader\_PIR\_UNIT\_With\_M5Core](https://static-cdn.m5stack.com/resource/docs/products/unit/PIR/ezLoader-a38c38d2-c621-4dc0-8401-48b53d12f16a.exe)

### Pinout <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/PIR/pinMap-a538414c-8694-4db1-a5bc-01857eb26f7f.png" alt=""><figcaption></figcaption></figure>

### Dimensions <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/PIR/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [Click here to download the Arduino example](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/PIR)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/uiflow2/guide/uiflow2_cover.png" alt=""><figcaption></figcaption></figure>

[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)This tutorial will show you how to initialize the configuration using the UIFlow2.0 graphical programming platform

[PIR Unit Programming Guide](https://uiflow-micropython.readthedocs.io/en/latest/units/pir.html)

<figure><img src="https://static-cdn.m5stack.com/mpy_docs/unit/pir/example.svg" alt=""><figcaption></figcaption></figure>

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/PIR/UIFlow)

### UIFlow Blocks <a href="#uiflow-blocks" id="uiflow-blocks"></a>

* I/O type sensor for detecting infrared signals from humans or animals

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/PIR/blockIntro-cca57dd5-203b-497f-83cd-dd3182c5d230.png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit PIR](https://docs.m5stack.com/en/unit/Unit_PIR) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U004`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                         |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U004_Unit_PIR/Structures)              |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U004_Unit_PIR/Structures/Unit_PIR.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
