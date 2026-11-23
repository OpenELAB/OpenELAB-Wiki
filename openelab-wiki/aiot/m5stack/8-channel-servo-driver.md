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

# 8-Channel Servo Driver

{% hint style="info" %}
[**View M5Stack 8-Channel Servo Driver Unit STM32F030 Multi Servo Controller on OpenELAB**](https://openelab.io/products/m5stack-servo-driver-unit)

**Store SKU / option:** `M5-U165`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack 8-Channel Servo Driver Unit (STM32F030)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-servo-driver-unit" %}

### Description <a href="#description" id="description"></a>

**8Servos Unit** is an 8-channel servo driver unit that uses the **STM32F030F4** master control to generate multiple PWM signals for servo drive and communicate with the M5 host through I2C (addr: 0x25). Built-in total power MOSTUBE switch circuit, support programming dynamic control motor release/lock;Built-in total current acquisition circuit, the total circuit parameters can be known. Supports two sets of power inputs (9-24V / 5V). This product is suitable for servo control, robot control, intelligent toys, etc.

### Features <a href="#features" id="features"></a>

* 8-channel servo drive
* Programmable motor power supply
* I2C Protocol Control (0x25)
* Reverse power supply protection
* Total current harvesting function

### Applications <a href="#applications" id="applications"></a>

* Servo controller
* Robot control

### Specification <a href="#specification" id="specification"></a>

<table><thead><tr><th width="276">Resources</th><th>Parameters</th></tr></thead><tbody><tr><td>Current acquisition chip</td><td>INA199A1DCKR</td></tr><tr><td>Servo drive channel</td><td>8-channel</td></tr><tr><td>Maximum drive load capacity</td><td>8-channel maximum load capacity: DC5V@1.3A</td></tr><tr><td>I2C Address</td><td>0x25</td></tr><tr><td>Product Size</td><td>55*24*11.5mm</td></tr><tr><td>Package Size</td><td>136* 92* 13mm</td></tr><tr><td>Product Weight</td><td>10.1g</td></tr><tr><td>Package Weight</td><td>17.6g</td></tr></tbody></table>

![](https://static-cdn.m5stack.com/resource/docs/products/unit/8Servos%20Unit/img-609b7c35-e340-46c3-9eb8-3d2f3e4d3cb7.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/8Servos%20Unit/img-8ababac7-87dd-4141-bff9-7846e1e4a754.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/8Servos%20Unit/img-b6355b6b-fb6b-4e69-80e2-a77ea7396ca9.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/8Servos%20Unit/img-bec39611-f510-4f83-b347-a4b2734c07fe.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/8Servos%20Unit/img-884ad9cd-e07b-4cbd-8f36-eb00b6ae5898.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/8Servos%20Unit/img-d8a37910-b392-470e-a43a-48cbb401a9f9.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [INA199A1DCKR](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/8Servos%20Unit/INA199A1DCKR.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/8Servos%20Unit/img-67ccf3fa-9113-4cca-bb67-f0a8f49cf10d.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/8Servos%20Unit/img-2eae2b86-5d70-4245-9511-36a8efa3098f.jpg" alt=""><figcaption></figcaption></figure>

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/8Servos%20Unit/arduinoCase-1691131676758ptotocol.png" alt=""><figcaption></figcaption></figure>

### COMPATIBLE <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (407).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit 8Servos](https://docs.m5stack.com/en/unit/Unit_8Servos) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U165`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                                 | Model-specific reference                                                                                                                 |
| ------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic                             | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/620/SCH_UNIT_8Servos_V1.01.pdf)                             |
| Mechanical / CAD files                           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U165_Unit_8Servos/Structures)                  |
| Mechanical / CAD files                           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U165_Unit_8Servos/Structures/Unit_8Servos.stl) |
| Official source: M5Unit-8Servos2-I2C             | [Read official source: m5unit-8servos2-i2c](https://github.com/m5stack/M5Unit-8Servos2-I2C)                                              |
| Official source: M5Unit-8Servos2-I2C-Internal-FW | [Read official source: m5unit-8servos2-i2c-internal-fw](https://github.com/m5stack/M5Unit-8Servos2-I2C-Internal-FW)                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
