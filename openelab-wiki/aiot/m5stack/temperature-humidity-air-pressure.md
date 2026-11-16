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

# Temperature Humidity Air Pressure

### M5Stack Temperature Humidity Air Pressure Sensor (SHT40+BMP280)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-sensor-1" %}

### Description <a href="#description" id="description"></a>

**ENV IV** is an environmental sensor that integrates the SHT40 and BMP280 sensors, designed for measuring **temperature, humidity, and atmospheric pressure data**. The SHT40 is a high-precision, low-power digital temperature and humidity sensor, supporting the I2C interface (SHT40 address: 0x44). The BMP280, on the other hand, is an absolute pressure sensor known for its high accuracy in atmospheric pressure measurements, with an I2C address of 0x76. This sensor unit finds applications in various fields, including meteorological monitoring, indoor environmental control, agriculture and horticulture, and industrial automation.

### Features <a href="#features" id="features"></a>

* Integrated sensors (temperature and humidity sensor SHT40, pressure sensor BMP280)
* High precision and low power consumption
* I2C communication interface (SHT40 I2C address: 0x44, BMP280 I2C address: 0x76)
* real-time monitor
* Multi platform programming Arduino UIFlow

### Applications <a href="#applications" id="applications"></a>

* meteorological monitoring
* Indoor environmental monitoring
* Agriculture and Horticulture
* Industrial automation field

### Specification <a href="#specification" id="specification"></a>

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

![](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/img-7cfc7eaf-c497-4012-9b6c-2a6676e22e9e.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/img-ab796899-2634-4e32-8cc5-03528cb76ffd.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/img-f46cac07-2bb1-4abd-849e-16d935d8ada6.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/img-6694f5e2-d5d0-4276-bbd7-29e5f80fb81b.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [BMP280 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/BMP280.pdf)
* [SHT40 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/SHT40.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/img-1f34d13c-33f1-43e2-8674-833615858955.png" alt=""><figcaption></figcaption></figure>

### EasyLoader <a href="#easyloader" id="easyloader"></a>

* **Windows**
  * [ENVIV Unit Demo](https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/ezLoader-a0c7ef88-87ce-4149-a1ca-f7c39e652502.exe)

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/pinMap-f025af0a-f2fc-42d7-99ce-c67b81800a46.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/img-3a3fce36-48d8-4335-a67f-ed93f11bedbb.jpg" alt=""><figcaption></figcaption></figure>

### Video <a href="#video" id="video"></a>

* Measure Tem./Hum./Presure Demo

{% embed url="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/ENV%E2%85%A3%20Unit/34f2dcf2563f4fa8aa9039250fadc90b.mp4" %}

### ENV version scheme comparison <a href="#env-version-scheme-comparison" id="env-version-scheme-comparison"></a>

| ENV I        | ENV II       | ENV III       | ENV IV       | ENV PRO |
| ------------ | ------------ | ------------- | ------------ | ------- |
| DHT12+BMP280 | SHT30+BMP280 | SHT30+QMP6988 | SHT40+BMP280 | BME688  |

### COMPATIBLE <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (937).png" alt=""><figcaption></figcaption></figure>
