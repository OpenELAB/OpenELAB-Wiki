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

# M5Stack Limit Switch

{% hint style="info" %}
[**View M5Stack Limit Switch Unit Mechanical Endstop Sensor Module on OpenELAB**](https://openelab.io/products/m5stack-limit-switch-unit)

**Store SKU / option:** `M5-U145`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Limit Switch Unit

***

Product Link

{% embed url="https://openelab.io/products/m5stack-limit-switch-unit" %}

### Description <a href="#description" id="description"></a>

The Unit Limit is a travel switch unit that provides a limit trigger signal to the MCU or other master peripherals by pulling the digital signal interface from 3.3V high to 0V low when the switch handle is closed by an external force. It is suitable for all kinds of moving machinery and equipment to control its stroke and carry out terminal limit protection.

### Features <a href="#features" id="features"></a>

* Contact limit switch
* Long durability, upto 400K times lifetime
* Multiple installation methods

### Applications <a href="#applications" id="applications"></a>

* Stop switch/Limit switch
* 3D printer limit switch

### Specification <a href="#specification" id="specification"></a>

| Resources             | Parameters          |
| --------------------- | ------------------- |
| Switch Bar Length     | 16mm                |
| Mechnical Lifetime    | 400K Times          |
| Power Supply          | DC 5V               |
| Output Logical Signal | DC 3.3V             |
| Standby Current       | DC5V@2mA            |
| Operation Current     | DC5V@3mA            |
| Product Size          | 32mm × 24mm × 9.5mm |
| Package Size          | 67mm × 53mm × 12mm  |
| Product Weight        | 6.3g                |
| Package Weight        | 11.4g               |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit%20Limit/img-233adf9a-007d-4fd4-ac39-c9496e4e2b0f.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit%20Limit/img-f4bd733d-dfb7-47c8-9c51-7d029f83a252.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit%20Limit/img-a29416df-6194-4961-908b-1035a06fb498.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit%20Limit/img-3e647b89-c78a-47ce-8f6a-d5df3effcac9.webp)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit%20Limit/img-f1ed372d-c586-4ee1-b665-45cc8ba2a571.webp" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit%20Limit/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (403).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Limit](https://docs.m5stack.com/en/unit/Unit_Limit) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U145`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                             |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Electrical schematic    | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/600/SCH_unitLimit_V1.0.pdf)                             |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U145_Unit_Limit/Structures)                |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U145_Unit_Limit/Structures/Unit_Limit.stl) |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/LIMIT)                                   |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
