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
