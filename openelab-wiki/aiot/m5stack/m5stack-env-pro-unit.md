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

# M5Stack ENV Pro Unit

### M5Stack Temperature, Humidity, Pressure and Gas Sensor (BME688)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-sensor" %}

### Description <a href="#description" id="description"></a>

**ENV Pro Unit** is an environmental sensor that utilizes the BME688 sensor solution, supporting the measurement of various environmental parameters such as volatile organic compounds (VOCs), indoor air quality (IAQ), temperature, humidity, and atmospheric pressure. It features a compact size, wide operating range, simple communication interface (I2C), excellent performance, and low power consumption, making it suitable for weather stations, indoor environmental monitoring, and air quality detection applications.

ENV Pro Unit can operate in environments ranging from 300hPa to 1100hPa of pressure, 0% to 100% humidity, and -40°C to 85°C temperature, covering sea-level to high-altitude regions, and is resistant to dryness, humidity, cold, and heat in various extreme conditions.

Compared to the previous ENV series products, the ENV Pro Unit measures temperature, humidity, and atmospheric pressure and includes the capability to measure VOCs and perform gas scanning. It offers outstanding sensitivity with a detection range down to parts per billion (ppb) level. Based on specific application requirements, the gas scanning functionality can be customized for sensitivity, selectivity, data rate, and power consumption.

Users can utilize the BME AI-Studio tool to train the ENV Pro Unit for specific applications such as home appliances, IoT products, or smart homes. It allows for digital output of various data parameters such as air quality index (IAQ), volatile organic compounds (VOC) and CO2 equivalent (ppm), gas scanning results (%), and intensity level (%), facilitating AI data analysis.

### Features <a href="#features" id="features"></a>

* Highly integrated sensors
* I2C Communication
* High precision and low power consumption
* real-time monitoring
* Multi-platform programming Arduino UIFlow

### Applications <a href="#applications" id="applications"></a>

* Indoor and outdoor air quality measurement
* Detect leaks or fires
* Agricultural temperature and humidity detection

### Specification <a href="#specification" id="specification"></a>

| Resources                                      | Parameters                                                                                                                                                                                           |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Key parameters of gas sensor                   | Standard scanning speed: 10.8s                                                                                                                                                                       |
| Key parameters of humidity sensing             | <p>Response time（τ 0-63%）: 8 seconds<br>Accuracy: ±3%R.H<br>measuring range：0 ~ 100% R.H.</p>                                                                                                        |
| Key parameters of atmospheric pressure sensing | <p>Square root noise value: 0.12Pa, equal to 1.7cm altitude<br>Offset temperature coefficient: ± 1.3Pa /K, equal to ± 10.9cm altitude (1°C temperature change)<br>measuring range：300 ~ 1100 hPa</p> |
| Key parameters of temperature sensing          | <p>Absolute accuracy: ±0.5 °C (0-65 °C)<br>measuring range：-40 ~ +85 °C</p>                                                                                                                          |
| Product Size                                   | 32\*24\*8mm                                                                                                                                                                                          |
| Package Size                                   | 136\* 92\*8mm                                                                                                                                                                                        |
| Product Weight                                 | 3.9g                                                                                                                                                                                                 |
| Package Weight                                 | 9.5g                                                                                                                                                                                                 |

<figure><img src="../../.gitbook/assets/image (422).png" alt=""><figcaption></figcaption></figure>

### Related Link

* [BME688 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/ENV%20Pro%20Unit/bst-bme688-ds000.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/img-5ab9e3c4-8c39-4289-aff2-7205ebc8fa7b.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/pinMap-60baf1b7-0c77-4689-8dcc-4463f0091851.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/img-c3e64d4b-35aa-4a1c-9473-cc743ad0c5ef.jpg" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [ENV PRO UNIT Arduino Demo（Read temperature, humidity, pressure and indoor air quality values）](https://github.com/m5stack/M5Unit-ENV/blob/master/examples/ENV_PRO/ENV_PRO.ino)
* [Bosch BME688 Official library document](https://github.com/boschsensortec/Bosch-BSEC2-Library)
* [Bosch BME688 Official detection and analysis of upper computer tools](https://www.bosch-sensortec.com/software-tools/software/bme688-software/)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [ENV PRO UNIT UIFlow case (read temperature and humidity, pressure, gas, etc.)](https://flow.m5stack.com/?examples=unit_env_pro_demo)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/uiflowCase-1694139868137image.png" alt=""><figcaption></figcaption></figure>

### UIFlow Blocks <a href="#uiflow-blocks" id="uiflow-blocks"></a>

![UIFlow2.0](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/static/assets/img/uiflow2/uiflow2.0_banner_01.png)

[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)

This tutorial will show you how to initialize the configuration using the UIFlow2.0 graphical programming platform

[ENV PRO Programming Guide](https://uiflow-micropython.readthedocs.io/zh-cn/latest/units/env.html)

![](https://static-cdn.m5stack.com/mpy_docs/unit/env/example.svg)

* Update data

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-39f88f19-8858-43bb-81c4-95bceef418c9.png)

* Set ( Temperature / Pressure / Humidity ) oversampling rate

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-bfab0947-6c42-4ab5-aef0-c608d0f7dfb8.png)

* Set IIR filter coefficient

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-3729391f-65f3-4b97-9933-3314f0c72a6e.png)

* Get temperature

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-5f21e45c-2e18-43bf-a3a0-79a94a8f7dd4.png)

* Get pressure

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-08a17f84-f78f-4566-839f-958e02142eee.png)

* Get humidity

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-2d3f4c5c-42fc-45a3-9c9c-59eb41e71641.png)

* Get gas resistance

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-1409bf85-d9e8-414a-bff0-ac9493c6f5af.png)

* Get altitude

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-ef0eba23-64e7-419b-94d1-3e3ceeb97c9b.png)

* Get IIR filter coefficient

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-9d666b02-fd46-4279-8a61-86a0f8617e9b.png)

* Get (Temperature / Pressure / Humidity) oversampling rate

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%20Pro%20Unit/blockIntro-28868792-34b8-4935-bacc-9be0493ee6a9.png)

### Video <a href="#video" id="video"></a>

* ENV PRO UNIT Demo（Read temperature, humidity, pressure and indoor air quality values）

{% embed url="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/ENV%20Pro%20Unit/ENV%20PRO%20UNIT.mp4" %}

* ENV PRO UNIT UIFlow Demo（Read temperature, humidity, pressure and indoor air quality values）

{% embed url="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/ENV%20Pro%20Unit/ENV_PRO_UIFLOW.mp4" %}

### ENV version scheme comparison <a href="#env-version-scheme-comparison" id="env-version-scheme-comparison"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/ENV%20Pro%20Unit/m5%E5%AF%B9%E6%AF%94.png" alt=""><figcaption></figcaption></figure>

### COMPATIBLE <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (925).png" alt=""><figcaption></figcaption></figure>
