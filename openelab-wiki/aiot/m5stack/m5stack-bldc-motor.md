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

# M5Stack BLDC Motor

### M5Stack BLDC Motor Driver Unit (STM32)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-bldc-motor-driver" %}

### Description <a href="#description" id="description"></a>

The **Unit-BLDC Driver** is a driving unit specifically designed for Brushless DC Motors (BLDC), utilizing an STM32 as the primary control chip. It enables precise control over the DRV11873PWPR motor drive chip through I2C communication, facilitating PWM speed control adjustment, monitoring, and direction switching functionalities. This drive chip features a simplified control interface and integrated stall protection, ensuring efficient and low-noise operation of three-phase small brushless DC motors. The onboard STM32 upgrade interface facilitates firmware updates and functional expansions, making it suitable for applications in industrial automation, smart robotics, precision instruments, and other fields.

### Features <a href="#features" id="features"></a>

* STM32 Main Control
* I2C Communication (0x65)
* DRV11873 Drive control
* BLDC（brushless DC motor）
* PWM speed configuration, control, direction switching and other functions
* Blocking rotation protection
* Firmware upgradable

### Applications <a href="#applications" id="applications"></a>

* Automation in industry
* Intelligent robot
* Precise instrument

### Specification <a href="#specification" id="specification"></a>

| Resources                 | Parameters                                                             |
| ------------------------- | ---------------------------------------------------------------------- |
| Motor driver chip         | DRV11873PWPR                                                           |
| Type of motor             | Three-phase sensorless, brushless direct current (BLDC) motor          |
| Motor drive voltage       | 5V(Powered by Grove port)                                              |
| I2C communication address | 0x65                                                                   |
| Output load capacity      | DC5V/508mA                                                             |
| Power dissipation         | <p>Standby current :DC5V/ 10.62mA<br>Working current :DC5V/13.20mA</p> |
| Operating temperature     | 0-40°C                                                                 |
| Product Size              | 32\*24\*11.3mm                                                         |
| Package Size              | 136\* 92\* 13.7mm                                                      |
| Product Weight            | 4.3g                                                                   |
| Package Weight            | 12.5g                                                                  |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-BLDC%20Driver/img-5cb8951d-04a1-4685-a209-402bd3d4d350.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-BLDC%20Driver/img-f04bc991-460e-4f62-985d-f1e9e174b415.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-BLDC%20Driver/img-5bc039cf-d654-4fb8-9c46-675a45ea43be.webp)

### PinMap <a href="#pinmap" id="pinmap"></a>

| PORT A(Red) | SCL | SDA | VCC | GND |
| ----------- | --- | --- | --- | --- |
| Core(Basic) | G22 | G21 | 5V  | GND |
| Core2       | G33 | G32 | 5V  | GND |
| CoreS3      | G1  | G2  | 5V  | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-BLDC%20Driver/img-187ece1c-22e8-4c3e-931d-2fa4964860e8.png" alt=""><figcaption></figcaption></figure>

* Indicator LED (Green)

| STM32                 | PB3/PB4/PB5/PB6 |
| --------------------- | --------------- |
| Indicator LED (Green) | SYS\_LED        |

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-BLDC%20Driver/img-d749b649-9eec-4d72-9cf0-c80a878d4d55.jpg" alt=""><figcaption></figcaption></figure>

### Compatible <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (941).png" alt=""><figcaption></figcaption></figure>

