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

# M5Stack I2C Hub

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5Stack I2C Hub 1 to 6 Expansion Unit

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**PaHUB2**, is an I2C Expandable Hub, which can expand a single I2C HY2.0-4P interface and connects up to 6 I2C channels. It allows you to mount slave devices with the same I2C address (by polling control the different channels to achieve in-device coexistence). Embedded PCA9548AP-I2C multi-channel switch IC, Save you worries with insufficient I2C interface of the expansion.

### Features <a href="#features" id="features"></a>

* I2C HY2.0-4P PORTA expansion
* 2x LEGO compatible holes
* Support multiple nesting
* 1-6 expansion

### Applications <a href="#applications" id="applications"></a>

* I2C device expansion

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications         | Parameters                                           |
| ---------------------- | ---------------------------------------------------- |
| Channel Control IC     | PCA9548AP                                            |
| Communication protocol | I2C: 0x70 (can be modified by resistance A0, A1, A2) |
| Net weight             | 7g                                                   |
| Gross weight           | 19g                                                  |
| Product size           | 48 \* 24 \* 12mm                                     |
| Packing size           | 136\*92\*12mm                                        |

Note: When it's connected, the PaHUB2 will be polling control the different channels to achieve in-device coexistence. Please pay attention to the order of channels when programming.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pahub/pahub_08.webp" alt=""><figcaption></figcaption></figure>

3 Position of Welding patch are reserved on the PCB board of the Unit, A0-A2 respectively, as shown in the figure below.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pahub/pahub_09.webp" alt=""><figcaption></figcaption></figure>

After welding the 0 ohm resistor, the corresponding pin will change from low level to high level. The pin level combination and its corresponding I2C address are shown in the table below.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pahub/pahub_10.webp" alt=""><figcaption></figcaption></figure>

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pahub/pahub_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (953).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit PaHub v2.0](https://docs.m5stack.com/en/unit/Unit_PaHub_v2.0) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U040-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                         |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U040-B_Unit_PaHub_v2.0/Structures)                     |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U040-B_Unit_PaHub_v2.0/Structures/Unit_PaHub_v2.0.stl) |
| Official source: M5Unit-HUB  | [Read official source: m5unit-hub](https://github.com/m5stack/M5Unit-HUB)                                                                        |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_pahub_v2)                                             |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
