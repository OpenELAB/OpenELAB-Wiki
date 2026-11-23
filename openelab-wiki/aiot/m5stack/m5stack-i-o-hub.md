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

# M5Stack I/O Hub

{% hint style="info" %}
[**View M5Stack I/O Hub 1 to 6 Expansion Unit on OpenELAB**](https://openelab.io/products/m5stack-i-o-hub)

**Store SKU / option:** `M5-U041-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack I/O Hub 1 to 6 Expansion Unit

***

### Product Link <a href="#description" id="description"></a>

{% embed url="https://openelab.io/products/m5stack-i-o-hub" %}

### Description <a href="#description" id="description"></a>

**PbHUB Unit** is a 6-channel expansion Unit with I2C control. Each Port B interface is capable of GPIO, PWM, Servo control, ADC sampling, RGB light control and other functions. Adopts STM32F030 for internal control.

### Features <a href="#features" id="features"></a>

* 6 x GPIO Ports Expansion
* 1 x I2C Input
* Internal STM32F030 control
* 2 x Brick holes

### Specifications <a href="#specifications" id="specifications"></a>

| Spec                   | Parameter                      |
| ---------------------- | ------------------------------ |
| Communication protocol | I2C:0x61(Modified by register) |
| Net weight             | 6.7g                           |
| Gross weight           | 11.8g                          |
| Product Size           | 48\*24\*12mm                   |
| Package Size           | 136\*92\*12mm                  |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pbhub_1.1/pbhub_1.1_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pbhub_1.1/pbhub_1.1_sch_02.webp" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (385).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit PbHub v1.1](https://docs.m5stack.com/en/unit/Unit_PbHub_v1.1) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U041-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                          | Model-specific reference                                                                                                                         |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files                    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U041-B_Unit_PbHub_v1.1/Structures)                     |
| Mechanical / CAD files                    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U041-B_Unit_PbHub_v1.1/Structures/Unit_PbHub_v1.1.stl) |
| Example source: M5Unit-PbHub              | [Read example source: m5unit-pbhub](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/analog_read)                                      |
| Example source: M5Unit-PbHub              | [Read example source: m5unit-pbhub](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/digital_write_read)                               |
| Example source: M5Unit-PbHub              | [Read example source: m5unit-pbhub](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/pwm)                                              |
| Example source: M5Unit-PbHub              | [Read example source: m5unit-pbhub](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/rgb_led)                                          |
| Example source: M5Unit-PbHub              | [Read example source: m5unit-pbhub](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/servo)                                            |
| Official source: M5Unit-PbHub-Internal-FW | [Read official source: m5unit-pbhub-internal-fw](https://github.com/m5stack/M5Unit-PbHub-Internal-FW)                                            |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
