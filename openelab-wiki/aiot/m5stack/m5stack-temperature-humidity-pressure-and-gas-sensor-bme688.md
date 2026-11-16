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

# M5Stack Temperature, Humidity, Pressure and Gas Sensor (BME688)

### M5Stack Temperature, Humidity, Pressure and Gas Sensor (BME688)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-sensor" %}

### Introduction

**ENV Pro Unit** is an environmental sensor that utilizes the BME688 sensor solution, supporting the measurement of various environmental parameters such as volatile organic compounds (VOCs), indoor air quality (IAQ), temperature, humidity, and atmospheric pressure. It features a compact size, wide operating range, simple communication interface (I2C), excellent performance, and low power consumption, making it suitable for weather stations, indoor environmental monitoring, and air quality detection applications.

ENV Pro Unit can operate in environments ranging from 300hPa to 1100hPa of pressure, 0% to 100% humidity, and -40°C to 85°C temperature, covering sea-level to high-altitude regions, and is resistant to dryness, humidity, cold, and heat in various extreme conditions.

<figure><img src="../../.gitbook/assets/image (528).png" alt=""><figcaption></figcaption></figure>

Compared to the previous ENV series products, the ENV Pro Unit measures temperature, humidity, and atmospheric pressure and includes the capability to measure VOCs and perform gas scanning. It offers outstanding sensitivity with a detection range down to parts per billion (ppb) level. Based on specific application requirements, the gas scanning functionality can be customized for sensitivity, selectivity, data rate, and power consumption.

Users can utilize the BME AI-Studio tool to train the ENV Pro Unit for specific applications such as home appliances, IoT products, or smart homes. It allows for digital output of various data parameters such as air quality index (IAQ), volatile organic compounds (VOC) and CO2 equivalent (ppm), gas scanning results (%), and intensity level (%), facilitating AI data analysis.

### Features

* Highly integrated sensors
* I2C Communication
* High precision and low power consumption
* real-time monitoring
* Multi-platform programming Arduino UIFlow

### Specifications

<table><thead><tr><th width="338">Resources</th><th>Parameters</th></tr></thead><tbody><tr><td>Key parameters of gas sensor</td><td>Standard scanning speed: 10.8s</td></tr><tr><td>Key parameters of humidity sensing</td><td>Response time（τ 0-63%）: 8 seconds<br>Accuracy: ±3%R.H<br>measuring range：0 ~ 100% R.H.</td></tr><tr><td>Key parameters of atmospheric pressure sensing</td><td>Square root noise value: 0.12Pa, equal to 1.7cm altitude<br>Offset temperature coefficient: ± 1.3Pa /K, equal to ± 10.9cm altitude (1°C temperature change)<br>measuring range：300 ~ 1100 hPa</td></tr><tr><td>Key parameters of temperature sensing</td><td>Absolute accuracy: ±0.5 °C (0-65 °C)<br>measuring range：-40 ~ +85 °C</td></tr><tr><td>Product Size</td><td>32*24*8mm</td></tr><tr><td>Package Size</td><td>136* 92*8mm</td></tr><tr><td>Product Weight</td><td>3.9g</td></tr><tr><td>Package Weight</td><td>9.5g</td></tr></tbody></table>

### Pinout

<figure><img src="../../.gitbook/assets/image (529).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (531).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Connect to a Microcontroller**: Use the I2C interface to connect the BME688 sensor to your microcontroller (e.g., Arduino, ESP32).
* **Install Necessary Libraries**: Ensure you have the correct libraries installed in your development environment to communicate with the sensor.
* **Initialize the Sensor**: Write initialization code to set up the sensor and start measurements.
* **Read Sensor Data**: Use provided functions to read temperature, humidity, pressure, and gas levels from the sensor.
* **Process and Display Data**: Process the data as needed for your application and display it on a screen or send it to a cloud service for analysis.

### FAQ

<details>

<summary><strong>Can I use the M5Stack BME688 with any microcontroller?</strong> </summary>

Yes, as long as the microcontroller supports I2C communication, you can integrate the BME688 sensor.

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

<summary><strong>What libraries are needed to operate the sensor with Arduino?</strong></summary>

You will need the Adafruit BME680 library, which supports the BME688 sensor.

</details>

<details>

<summary><strong>Can the sensor detect specific gases?</strong></summary>

The BME688 sensor can detect a range of volatile organic compounds (VOCs) but is not specific to individual gases. It provides general air quality assessment.

</details>

<details>

<summary><strong>How accurate are the sensor readings?</strong> </summary>

The sensor provides high accuracy for temperature (±0.5°C), humidity (±3% RH), and pressure (±1 hPa).

</details>
