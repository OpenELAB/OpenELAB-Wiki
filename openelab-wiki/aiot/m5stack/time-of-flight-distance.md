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

# Time-of-Flight Distance

### M5Stack Time-of-Flight Distance Unit (VL53L1X)

***

### Product Link

{% embed url="https://openelab.io/products/time-of-flight-distance-unit" %}

### Description <a href="#description" id="description"></a>

**ToF4M Unit** is a high-precision distance sensor module that utilizes the VL53L1CXV0FY/1 sensor and employs Time-of-Flight (ToF) technology. It is capable of measuring object height, detecting object presence, and tracking object movement within a range of 4mm to 4000mm. It finds applications in robotics, autonomous vehicles, drones, security systems, and more.

**ToF4M Unit** offers exceptional accuracy, with measurements as precise as 0.1mm. This level of accuracy enables it to detect even the smallest distance variations and capture surface details of objects. With its fast response time, ToF4M Unit can perform measurements within milliseconds. This real-time feedback of distance information makes it suitable for scenarios that require quick responsiveness.

**ToF4M Unit** communicates using the I2C protocol, providing advantages such as simplified connectivity, support for multi-master and multi-slave topologies, and high reliability. It can be easily integrated with existing sensor buses, effectively saving IO resources. The module features a standard Grove interface, ensuring reliable and stable signal transmission. When used with the M5Stack hardware ecosystem, it supports plug-and-play functionality, enabling rapid project development.

### Features <a href="#features" id="features"></a>

* High accuracy: ToF4M Unit has a very high accuracy, up to 0.1 mm. The measuring distance is about 4 meters.
* Fast response time: ToF4M Unit has a fast response time and is able to complete a measurement in milliseconds.
* Multi-field applications: robots, autonomous vehicles, drones, security and other fields. Tasks such as measuring the height, presence, and movement of objects demonstrate its versatility.
* Programming platform: Arduino, UIFlow, etc.

### Includes <a href="#includes" id="includes"></a>

* 1x ToF4M Unit
* 1x HY2.0-4P Cable（20cm）

### Applications <a href="#applications" id="applications"></a>

* robots
* automatic pilot
* drone
* construction of security

### Specification <a href="#specification" id="specification"></a>

| Resources                   | Parameters          |
| --------------------------- | ------------------- |
| Sensor                      | VL53L1CXV0FY/1      |
| Measurement range           | 4mm-4000mm          |
| Resolution ratio            | Millimeter scale    |
| Measuring speed             | Millisecond level   |
| FoV                         | 15-27°              |
| Light source                | Laser (ToF)         |
| I²C address                 | The default is 0x29 |
| Operating temperature range | 0°C to +40°C        |
| Product Size                | 32\*24\*8mm         |
| Package Size                | 136\* 92\*20mm      |
| Product Weight              | 4.4g                |
| Package Weight              | 8.8g                |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-ToF4M/img-71b71b77-67c9-4627-bc97-49017d1f4542.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-ToF4M/img-06538272-4432-4bff-8a33-d06e7c7cbb6b.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-ToF4M/img-a19a8345-fd99-44d1-8fb5-3af26261688a.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [VL53L1CXV0FY/1](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-ToF4M/VL53L1CXV0FY.PDF)

### Schematic <a href="#schematic" id="schematic"></a>

![schematics](https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-ToF4M/img-bdfb4e64-779f-4991-8b12-0b94dbc7f4da.png)

### The difference between M5 ToF4M Unit and M5 ToF Unit <a href="#the-difference-between-m5-tof4m-unit-and-m5-tof-unit" id="the-difference-between-m5-tof4m-unit-and-m5-tof-unit"></a>

| Unit       | Sensor   | Measuring Distance | Address | Size        | Light source |
| ---------- | -------- | ------------------ | ------- | ----------- | ------------ |
| ToF4M Unit | VL53L1CX | 4mm-4000mm         | 0x29    | 32\*24\*8mm | Laser        |
| ToF Unit   | VL53L0X  | 25mm-1000mm        | 0x29    | 32\*24\*8mm | Laser        |

### PinMap <a href="#pinmap" id="pinmap"></a>

| PORT A(RED) | SCL | SDA | VCC | GND |
| ----------- | --- | --- | --- | --- |
| Core(Basic) | G22 | G21 | 5V  | GND |
| Core2       | G33 | G32 | 5V  | GND |
| CoreS3      | G1  | G2  | 5V  | GND |

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-ToF4M/img-0c360975-630d-412d-a109-8f9f7e672f85.jpg" alt=""><figcaption></figcaption></figure>

### Version comparison <a href="#version-comparison" id="version-comparison"></a>

<figure><img src="../../.gitbook/assets/image (413).png" alt=""><figcaption></figcaption></figure>

### COMPATIBLE <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (414).png" alt=""><figcaption></figcaption></figure>
