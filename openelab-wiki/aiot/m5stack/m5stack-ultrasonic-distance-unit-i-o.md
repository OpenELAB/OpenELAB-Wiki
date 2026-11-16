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

# M5Stack Ultrasonic Distance Unit I/O

### M5Stack Ultrasonic Distance Unit I/O

***

### Product Link

{% embed url="https://openelab.io/products/ultrasonic-distance-unit-1" %}

### Description <a href="#description" id="description"></a>

**UNIT SONIC IO** is a `GPIO` interface ultrasonic range sensor. This module features an RCWL-9620 ultrasonic distance measurement chip with a 16mm probe, which the ranging accuracy can reach `2cm-450cm` (accuracy up to ±2%). This sensor determines the distance to a target by measuring time lapses between the transmitting and receiving of the pulse signal, users can directly obtain the distance value through IO control mode. It is ideal to apply in robotics obstacle avoidance, fluid level detection, and other applications that require you to perform measurements.

Note: When the measurement is more than 3.5m, there will be a slight delay in the response of the distance measurement data.

### Features <a href="#product-features" id="product-features"></a>

* RCWL-9620
* GPIO communication interface
* Measuring range: 2cm-450cm
* Protective housing
* Built-in temperature compensation, reduce the temperature drift
* Support UIFlow platform

### Application <a href="#application" id="application"></a>

* Robot Obstacle Avoidance
* Fluid Level Detection
* Sitting Posture Detection

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications                   | Parameters       |
| -------------------------------- | ---------------- |
| Ultrasonic Ranging Single Chip   | RCWL-9620        |
| Range                            | 2cm-450cm        |
| Probe Specifications             | 16mm             |
| Receiving/Transmitting Frequency | 40KHz            |
| Receiving sensitivity            | -65dB            |
| Pointing angle                   | 60°              |
| Measurement accuracy             | ±2%              |
| Measurement period               | 50ms             |
| Working current                  | 3mA              |
| Net weight                       | 11.5g            |
| Gross weight                     | 26g              |
| Product size                     | 56 \* 24 \* 15mm |
| Packing size                     | 76 \* 47 \* 29mm |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/sonic.io/sonic.io_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/sonic.io/sonic.io_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/sonic.io/sonic.io_06.webp)

### Pinout <a href="#pin-mapping" id="pin-mapping"></a>

* UNIT SONIC IO

| M5CORE - PORT B | G26  | G32  | 5V  | GND |
| --------------- | ---- | ---- | --- | --- |
| UNIT SONIC IO   | TRIG | ECHO | VCC | GND |

### Dimensions <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/UNIT%20SONIC%20IO/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [M5Unit-Sonic with M5Atom](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5Atom/Unit_SonicIO_M5Atom.ino)
* [M5Unit-Sonic with M5Core](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5Core/Unit_SonicIO_M5Core.ino)
* [M5Unit-Sonic with M5Core2](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5Core2/Unit_SonicIO_M5Core2.ino)
* [M5Unit-Sonic with M5StickC](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5StickC/Unit_SonicIO_M5StickC.ino)
* [M5Unit-Sonic with M5StickCPlus](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5StickCPlus/Unit_SonicIO_M5StickCPlus.ino)
