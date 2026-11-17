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

# OpenELAB  EASY PLUG RGB TCS34725 Color Sensor Module I2C

### OpenELAB EASY PLUG RGB TCS34725 Color Sensor Module I2C

***

### Product Link

{% embed url="https://openelab.io/products/rgb-tcs34725-color-sensor-module" %}

### Introduction

This module needs to be used with the EASY plug Control board V2.0 and control board (KS0240). When in use, you can use a special telephone line (RJ11 crystal head) to connect with the control board.

### Features

* Working voltage: DC 3.3-5V&#x20;
* Working current: 65uA&#x20;
* Detection distance: 3-10mm&#x20;
* Clock frequency: 0-400KHZ&#x20;
* Interface: I2C interface and RJ11interface&#x20;
* Temperature range: -30 ° C \~ +70 ° C&#x20;
* Size: 4&#x30;_&#x32;&#x30;_&#x31;9mm&#x20;
* Weight: 5.6g

### Specifications

* **Sensor Model**: TCS34725
* **Operating Voltage**: 3.3V to 5V
* **Communication Interface**: I2C
* **I2C Address**: 0x29
* **Measurement Range**: Detects red, green, blue, and clear light
* **Connector Type**: RJ11 4P4C
* **LED**: Integrated white LED with control pin
* **Dimensions**: 32mm x 24mm x 7mm (L x W x H)

### Pinout

* **GND**: Ground connection.
* **VCC**: Power supply (3.3V to 5V).
* **SDA**: I2C data line.
* **SCL**: I2C clock line.
* **INT**: Interrupt pin (optional, used for advanced features).
* **LED**: Control pin for the onboard LED.

### Dimensions

Size: 40\*_20\*_&#x31;9 mm&#x20;

Weight: 5.6 g

### How to Use

<figure><img src="../../.gitbook/assets/image (452).png" alt=""><figcaption></figcaption></figure>

### FAQ

<details>

<summary><strong>Can this module detect colors in low-light conditions?</strong></summary>

Yes, the module includes an onboard white LED to provide consistent lighting, ensuring accurate color detection even in low-light environments.

</details>

<details>

<summary><strong>What is the typical I2C communication speed for this module?</strong></summary>

The TCS34725 sensor typically operates at standard I2C speeds (100kHz), but it can also work at higher speeds depending on the microcontroller used.

</details>

<details>

<summary><strong>Is this module compatible with other platforms besides Arduino?</strong></summary>

Yes, it can be used with any microcontroller that supports I2C communication, such as Raspberry Pi, ESP32, and more.

</details>

<details>

<summary><strong>How accurate is the color detection?</strong></summary>

The TCS34725 sensor is known for its high accuracy, capable of detecting subtle differences in color, which makes it suitable for a wide range of applications.

</details>
