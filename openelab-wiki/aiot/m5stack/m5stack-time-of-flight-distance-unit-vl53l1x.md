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

# M5Stack Time-of-Flight Distance Unit (VL53L1X)

### M5Stack Time-of-Flight Distance Unit (VL53L1X)

***

### Product Link

{% embed url="https://openelab.io/products/time-of-flight-distance-unit" %}

### Introduction

**ToF** that employs time-of-flight techniques to resolve distance between the emit point and the reach point of a subject, measuring the round trip time of an artificial light signal provided by a laser.

This unit integrated a distance measuring sensor VL53L0x providing accurate distance measurement whatever the target reflectance, unlike conventional technologies. It can measure absolute distances up to 2m in less than 30ms.

This unit communicates with M5Core via I2C(0x29).

* In this case, make sure you use the 3.3V on SDA and SCL, M5Core GROVE provide 3.3V to data pins, 5V to power pin. only 3.3v allowed on VL53L0x.

<figure><img src="../../.gitbook/assets/image (543).png" alt=""><figcaption></figcaption></figure>

### Features

* Measure absolute distances up to 2m
* Measurement accuracy ±3%
* The wavelength of laser: 940nm
* Program Platform: Arduino, UIFlow
* Two Lego-compatible holes

### Specifications

| Resources            | Parameters          |
| -------------------- | ------------------- |
| Sensor               | VL53L0X             |
| Measuring distance   | 0.3-2M              |
| Measurement accuracy | ±3%                 |
| Product Size         | 32mm × 24mm × 8mm   |
| Package Size         | 136mm × 92mm × 13mm |
| Product Weight       | 4g                  |
| Package Weight       | 17g                 |

### Pinout

* **VCC:** Power supply (3.3V - 5V)
* **GND:** Ground
* **SDA:** I2C Data Line
* **SCL:** I2C Clock Line

### How to Use

#### Arduino <a href="#arduino" id="arduino"></a>

* [Click here to download the Arduino example](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/ToF_VL53L0X)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/TOF/UIFlow)<br>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/TOF/uiflowCase-1689302874150UIFLOW.png" alt=""><figcaption></figcaption></figure>

### FAQ

<details>

<summary>What is the maximum range of the VL53L1X sensor?</summary>

The sensor can measure distances up to several meters depending on environmental conditions.

</details>

<details>

<summary>Can it be used with Arduino or Raspberry Pi?</summary>

Yes, it supports both Arduino and Raspberry Pi via the I2C interface.

</details>

<details>

<summary>How accurate is the distance measurement?</summary>

The VL53L1X sensor offers high accuracy in distance measurement, suitable for precise applications.

</details>
