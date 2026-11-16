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

# M5Stack NCIR 2 Thermometer Unit (MLX90614)

### M5Stack NCIR 2 Thermometer Unit (MLX90614)

***

### Product Link

{% embed url="https://openelab.io/products/ncir-2-thermometer-unit" %}

### Introduction

Living through this pandemic has made contactless temperature sensing a must! The NCIR 2 Thermometer Unit utilizes the MLX90614 temperature sensor, and take ambient and object temperature readings with No Contact. Great for socially-distant reality.

The MLX90614 sensor is factory calibrated in wide temperature range, -40 to 125 ˚C for the ambient temperature and -70 to 380 ˚C for the object temperature. The embedded MCU - STM32 can process the data to achieve high/low temperature alert function. There are also buzzer, RGB LED, function button and reset button on board.

<figure><img src="../../.gitbook/assets/image (865).png" alt=""><figcaption></figcaption></figure>

This Unit can either work with M5Core through I2C protocol, or work alone. Suitable for medical, environmental monitoring and home automation applications.

### Features

* STM32F030F4P6
* MLX90614 IR Sensor
* HY2.0-4P Connector (I2C)
* Program platform: Arduino, UIFlow
* Two brick-compatible holes

### Specifications

| Resources                            | Parameters          |
| ------------------------------------ | ------------------- |
| MCU                                  | STM32F030F4P6       |
| Sensor                               | MLX90614ESF-BAA     |
| Object Measurement Temperature Range | -70°C \~ 380°C      |
| Calibrated Sensor Temperature        | -40°C \~ 125˚C      |
| Unit Operation Temperature           | 0°C \~ 40°C         |
| Accuracy                             | ±0.5°C              |
| Program Platform                     | Arduino, UIFlow     |
| I2C Address                          | 0x5A                |
| Product Size                         | 48mm × 24mm ×8mm    |
| Package Size                         | 136mm × 92mm × 13mm |
| Product Weight                       | 7.3g                |
| Package Weight                       | 12.8g               |

### Pinout

<figure><img src="../../.gitbook/assets/image (866).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (867).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Connect to M5Stack**: Plug the NCIR 2 Thermometer Unit into an M5Stack development board using the appropriate port.
* **Power Up**: Supply power to the M5Stack board (3.3V - 5V).
* **Initialize Sensor**: Use the M5Stack library and example code to initialize the MLX90614 sensor.
* **Read Temperature**: Access the temperature data through the I2C interface using the provided example code or custom scripts.

### FAQ

<details>

<summary><strong>What is the maximum distance for accurate temperature measurement?</strong></summary>

The sensor can accurately measure temperature up to a few centimeters, depending on the size and emissivity of the object.

</details>

<details>

<summary><strong>Can the sensor measure the temperature of liquids?</strong></summary>

Yes, it can measure the surface temperature of liquids, provided the liquid surface is stable and not reflective.

</details>

<details>

<summary><strong>Is the sensor suitable for outdoor use?</strong></summary>

The sensor operates in a wide temperature range but should be protected from direct exposure to harsh environmental conditions like rain or dust.

</details>

<details>

<summary><strong>How do I calibrate the sensor?</strong></summary>

The MLX90614 comes pre-calibrated from the factory. For recalibration, specialized equipment and software are required.

</details>

<details>

<summary><strong>Can I use this sensor with other microcontroller platforms?</strong></summary>

Yes, it is compatible with any microcontroller that supports I2C communication, including Arduino, Raspberry Pi, and ESP32.

</details>
