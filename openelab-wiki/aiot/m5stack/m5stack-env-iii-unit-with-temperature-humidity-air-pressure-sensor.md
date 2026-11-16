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

# M5Stack ENV III Unit with Temperature Humidity Air Pressure Sensor

### M5Stack ENV III Unit with Temperature Humidity Air Pressure Sensor

***

### Product Link

{% embed url="https://openelab.io/products/env-iii-unit" %}

### Introduction

**ENV III** is an environmental sensor that integrates SHT30 and QMP6988 internally to detect temperature, humidity, and atmospheric pressure data. SHT30 is a high-precision and low-power digital temperature and humidity sensor, and supports I2C interface (SHT30:0x44 , QMP6988:0x70).QMP6988 is an absolute air pressure sensor specially designed for mobile applications, with high accuracy and stability, suitable for environmental data collection and detection types of projects.

<figure><img src="../../.gitbook/assets/image (536).png" alt=""><figcaption></figcaption></figure>

### Features

* **High Precision Sensors**: Equipped with SHT30 (temperature and humidity) and BMP280 (air pressure) sensors.
* **Wide Measurement Range**: Accurate measurements of temperature, humidity, and air pressure across a broad range.
* **I2C Communication**: Utilizes I2C protocol for easy integration with M5Stack core and other microcontrollers.
* **Plug-and-Play**: Compatible with M5Stack core devices, enabling quick setup and deployment.
* **Compact Design**: Small form factor suitable for space-constrained applications.

### Specifications

| Resources                                               | Parameter                        |
| ------------------------------------------------------- | -------------------------------- |
| Maximum temperature measurement range                   | -40 \~ 120 ℃                     |
| Highest measurement accuracy                            | 0 \~ 60 ℃/±0.2℃                  |
| Humidity measurement range/error                        | 10 \~ 90 %RH / ±2%               |
| Maximum measured value of air pressure/resolution/error | 300 \~ 1100hPa / 0.06Pa / ±3.9Pa |
| Communication protocol                                  | I2C: SHT30(0x44), QMP6988(0x70)  |
| Working temperature                                     | 32°F to 104°F (0°C to 40°C )     |
| Net weight                                              | 5g                               |
| Gross weight                                            | 17g                              |
| Product Size                                            | 24\*32\*8mm                      |
| Package Size                                            | 136\*92\*13mm                    |
| Case Material                                           | Plastic ( PC )                   |

### Pinout

* **GND**: Ground
* **VCC**: 3.3V/5V Power Supply
* **SCL**: I2C Clock
* **SDA**: I2C Data

### Dimensions

* **Length**: 32mm
* **Width**: 24mm
* **Height**: 8mm

### How to Use

1. **Connection**: Connect the ENV III Unit to the M5Stack core using a Grove cable.
2. **Library Installation**: Install the necessary libraries (`M5Stack`, `Wire`, `Adafruit_Sensor`, `Adafruit_BMP280`, `Adafruit_SHT31`).
3. **Initialization**: Initialize the sensors in your code using the appropriate library functions.
4. **Data Reading**: Use the library functions to read temperature, humidity, and air pressure data.
5. **Display/Use Data**: Display the data on the M5Stack screen or use it in your application logic.

### FAQ

<details>

<summary> <strong>What applications can the ENV III Unit be used for?</strong></summary>

The ENV III Unit is ideal for weather stations, HVAC systems, environmental monitoring, and smart home applications.

</details>

<details>

<summary><strong>How do I connect the ENV III Unit to my M5Stack core?</strong></summary>

Use a Grove cable to connect the ENV III Unit to the Grove port on the M5Stack core.

</details>

<details>

<summary><strong>Can I use the ENV III Unit with other microcontrollers?</strong></summary>

Yes, as long as the microcontroller supports I2C communication, you can use the ENV III Unit with it.

</details>

<details>

<summary><strong>What is the accuracy of the sensors?</strong></summary>

The temperature sensor has an accuracy of ±0.2°C, the humidity sensor ±2% RH, and the air pressure sensor ±1 hPa.

</details>

<details>

<summary><strong>How do I install the necessary libraries?</strong></summary>

Use the Arduino Library Manager to install the `M5Stack`, `Wire`, `Adafruit_Sensor`, `Adafruit_BMP280`, and `Adafruit_SHT31` libraries.

</details>
