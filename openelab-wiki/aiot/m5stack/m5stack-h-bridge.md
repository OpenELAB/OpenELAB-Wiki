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

# M5Stack H-bridge

{% hint style="info" %}
[**View M5Stack H-bridge Unit v1.1 STM32F030 DC Motor Driver on OpenELAB**](https://openelab.io/products/m5stack-h-bridge-unit)

**Store SKU / option:** `M5-U160-V11`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack H-bridge Unit v1.1

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-h-bridge-unit" %}

### Description <a href="#description" id="description"></a>

Meet the **HBridge v1.1 Unit** – a state-of-the-art DC motor drive module that redefines motor control. Powered by the **"STM32F030+RZ7899"** scheme, this module enables seamless **I2C** communication with the M5 host, offering precise **PWM** control for speed adjustment, as well as easy management of forward, reverse, and braking functions.

Safety and reliability take center stage with built-in safeguards against over-current, over-voltage, and over-temperature situations. The module's total power MOSTUBE switch circuit allows dynamic motor control through programming, while the integrated total current acquisition circuit ensures safe motor operation.

Adapting to diverse needs, the module incorporates a smart 6-12V and 5V switching circuit. It's a perfect fit for a range of applications, from robotics, motor drives, and industrial automation to smart homes. Elevate your projects with the HBridge v1.1 Unit – where cutting-edge technology meets simplicity and versatility.

### Features <a href="#features" id="features"></a>

* Overcurrent, overvoltage, overtemperature protection
* Power switching
* I2C address: Default 0x20
* current detech
* Programming platform: Arduino, UIFlow

### Applications <a href="#applications" id="applications"></a>

* robot
* Motor driven
* Industrial automation
* Smart home

### Specification <a href="#specification" id="specification"></a>

| Resources                          | Parameters                                                      |
| ---------------------------------- | --------------------------------------------------------------- |
| MCU                                | STM32F030F4P6                                                   |
| DC bidirectional motor driver chip | RZ7899                                                          |
| Current acquisition chip           | INA199A1DCKR                                                    |
| External access DC voltage         | MAX 12V                                                         |
| I2C mailing address                | Default 0x20 (can be modified by toggle of the encoding switch) |
| Maximum allowable current          | 3A                                                              |
| Use temperature                    | 0-40°C                                                          |
| Product Size                       | 48mm\* 24mm\*8mm                                                |
| Package Size                       | 136mm\* 92mm\*13mm                                              |
| Product Weight                     | 9.1g                                                            |
| Package Weight                     | 14g                                                             |

### Schematic <a href="#schematic" id="schematic"></a>

Turn the switch to the corresponding position based on the input power supply.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/HBridge%20v1.1%20Unit/img-ddfb73bb-760f-41b5-9ba9-adc4db9945d2.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/HBridge%20v1.1%20Unit/img-7c7a12ff-76ad-4ec0-ae1c-d75c85454130.png" alt=""><figcaption></figcaption></figure>

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/HBridge%20v1.1%20Unit/1c0f2f06b03b7b55265dfb4d4902827.png" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (398).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit HBridge v1.1](https://docs.m5stack.com/en/unit/Unit_HBridge_v1.1) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U160-V11`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                            | Model-specific reference                                                                                                                               |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Electrical schematic                        | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/615/SCH_UNIT_HBridge_V1.1.pdf)                                            |
| Mechanical / CAD files                      | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U160-V11_Unit_HBridge_v1.1/Structures)                       |
| Mechanical / CAD files                      | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U160-V11_Unit_HBridge_v1.1/Structures/Unit_HBridge_v1.1.stl) |
| Official source: M5Unit-Hbridge             | [Read official source: m5unit-hbridge](https://github.com/m5stack/M5Unit-Hbridge)                                                                      |
| Arduino development tutorial                | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_hbridge)                                                    |
| Official source: M5Unit-Hbridge-Internal-FW | [Read official source: m5unit-hbridge-internal-fw](https://github.com/m5stack/M5Unit-Hbridge-Internal-FW)                                              |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
