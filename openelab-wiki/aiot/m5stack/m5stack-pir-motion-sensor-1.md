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

| Resources      | Parameters    |
| -------------- | ------------- |
| Product Size   | 32\*24\*12mm  |
| Package Size   | 136\*92\*13mm |
| Product Weight | 5g            |
| Package Weight | 20g           |

<figure><img src="../../.gitbook/assets/QQ_1728442668186.png" alt=""><figcaption></figcaption></figure>

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="../../.gitbook/assets/image (920).png" alt=""><figcaption></figcaption></figure>

### EasyLoader <a href="#easyloader" id="easyloader"></a>

* **Windows**
  * [EasyLoader\_PIR\_UNIT\_With\_M5Core](https://static-cdn.m5stack.com/resource/docs/products/unit/PIR/ezLoader-a38c38d2-c621-4dc0-8401-48b53d12f16a.exe)

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="../../.gitbook/assets/image (921).png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="../../.gitbook/assets/image (922).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit PIR](https://docs.m5stack.com/en/unit/Unit_PIR) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U004`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                         |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U004_Unit_PIR/Structures)              |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U004_Unit_PIR/Structures/Unit_PIR.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
