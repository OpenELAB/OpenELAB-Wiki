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

# M5Stack Ultrasonic

### M5Stack Ultrasonic Distance Unit I2C

***

### Product Link

{% embed url="https://openelab.io/products/ultrasonic-distance-unit" %}

### Description <a href="#description" id="description"></a>

**UNIT SONIC I2C** is an `I2C` interface ultrasonic distance sensor. This allows for easy I2C integration and multi-sensor operation using a single BUS, to save I/O resources. The module features an RCWL-9620 ultrasonic distance measurement chip with a 16mm probe, which the ranging accuracy can reach `2cm-450cm` (accuracy up to ±2%). It is ideal to apply in robotics obstacle avoidance, fluid level detection, and other applications that require you to perform measurements.

Note: When the measurement is more than 3.5m, there will be a slight delay in the response of the distance measurement data.

### Features <a href="#product-features" id="product-features"></a>

* RCWL-9620 Chip
* I2C communication interface (addr: 0x57)
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
| Working current                  | 2mA              |
| Net weight                       | 10g              |
| Gross weight                     | 25g              |
| Product size                     | 56 \* 24 \* 15mm |
| Packing size                     | 76 \* 47 \* 29mm |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/sonic.i2c/sonic.i2c_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/sonic.i2c/sonic.i2c_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/sonic.i2c/sonic.i2c_06.webp)

### Pin mapping <a href="#pin-mapping" id="pin-mapping"></a>

* UNIT SONIC I2C

| M5CORE - PORT A | G21 | G22 | 5V  | GND |
| --------------- | --- | --- | --- | --- |
| UNIT SONIC I2C  | SDA | SCL | VCC | GND |

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/UNIT%20SONIC%20I2C/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>
