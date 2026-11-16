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

# M5Stack Temperature Humidity Air Pressure Sensor (SHT40+BMP280)

### M5Stack Temperature Humidity Air Pressure Sensor (SHT40+BMP280)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-sensor-1" %}

### Introduction

**ENV IV** is an environmental sensor that integrates the SHT40 and BMP280 sensors, designed for measuring **temperature, humidity, and atmospheric pressure data**. The SHT40 is a high-precision, low-power digital temperature and humidity sensor, supporting the I2C interface (SHT40 address: 0x44). The BMP280, on the other hand, is an absolute pressure sensor known for its high accuracy in atmospheric pressure measurements, with an I2C address of 0x76. This sensor unit finds applications in various fields, including meteorological monitoring, indoor environmental control, agriculture and horticulture, and industrial automation.

### Features

* Integrated sensors (temperature and humidity sensor SHT40, pressure sensor BMP280)
* High precision and low power consumption
* I2C communication interface (SHT40 I2C address: 0x44, BMP280 I2C address: 0x76)
* real-time monitor
* Multi platform programming Arduino UIFlow

### Specifications

| Resources                                | Parameters                   |
| ---------------------------------------- | ---------------------------- |
| SHT40 measure range(Temperture/Humidity) | -40 \~ 125 °C，0 \~ 100 %RH   |
| BMP280 measure range(Presure)            | 300 \~ 1100hPa               |
| SHT40 measure accuracy                   | ±0.1 °C，±1.5 %RH             |
| BMP280 measure accuracy                  | ±0.12hPa                     |
| communication protocol                   | I2C:SHT30(0x44),BMP280(0x76) |
| Shell material                           | Plastic ( PC )               |
| Product Size                             | 32\*24\*8mm                  |
| Package Size                             | 136\* 92\*13mm               |
| Product Weight                           | 3.9g                         |
| Package Weight                           | 9.3g                         |

### Pinout

<figure><img src="/broken/files/d8uVMYvpd79JC76sHAHq" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (532).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Connect to a Microcontroller**: Use the I2C interface to connect the sensor unit to your microcontroller (e.g., Arduino, ESP32).
* **Install Necessary Libraries**: Ensure you have the correct libraries installed in your development environment to communicate with the SHT40 and BMP280 sensors.
* **Initialize the Sensors**: Write initialization code to set up the sensors and start measurements.
* **Read Sensor Data**: Use provided functions to read temperature, humidity, and pressure data from the sensors.
* **Process and Display Data**: Process the data as needed for your application and display it on a screen or send it to a cloud service for analysis.

### FAQ

<details>

<summary><strong>Can I use the M5Stack SHT40+BMP280 sensor with any microcontroller?</strong></summary>

Yes, as long as the microcontroller supports I2C communication, you can integrate the SHT40+BMP280 sensor.

</details>

<details>

<summary><strong>How do I power the sensor?</strong></summary>

The sensor operates at 3.3V, so ensure your power supply matches this requirement.

</details>

<details>

<summary><strong>Is the sensor suitable for outdoor use?</strong></summary>

The sensor is designed for indoor use. If using it outdoors, ensure it is protected from extreme weather conditions.

</details>

<details>

<summary><strong>What libraries are needed to operate the sensor with Arduino?</strong> </summary>

You will need the Adafruit SHT4x library and the Adafruit BMP280 library.

</details>

<details>

<summary><strong>How accurate are the sensor readings?</strong></summary>

The sensor provides high accuracy for temperature (±0.2°C), humidity (±1.8% RH), and pressure (±1 hPa).

</details>

<details>

<summary><strong>Can the sensor detect specific weather patterns?</strong></summary>

The sensor provides data on temperature, humidity, and air pressure, which can be used to infer weather patterns, but it does not directly detect specific weather conditions.

</details>
