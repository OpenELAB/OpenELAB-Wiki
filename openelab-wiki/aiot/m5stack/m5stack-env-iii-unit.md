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

# M5Stack ENV III Unit

### M5Stack ENV III Unit

***

### Product Link

{% embed url="https://openelab.io/products/env-iii-unit" %}

### Description <a href="#description" id="description"></a>

**ENV III** is an environmental sensor that integrates SHT30 and QMP6988 internally to detect temperature, humidity, and atmospheric pressure data. SHT30 is a high-precision and low-power digital temperature and humidity sensor, and supports I2C interface (SHT30:0x44 , QMP6988:0x70).QMP6988 is an absolute air pressure sensor specially designed for mobile applications, with high accuracy and stability, suitable for environmental data collection and detection types of projects.

### Features <a href="#product-features" id="product-features"></a>

* Simple and easy to use
* High accuracy
* I2C communication interface
* HY2.0-4P interface, support platform [UIFlow ](http://flow.m5stack.com/), [Arduino](http://www.arduino.cc/)
* 2x LEGO compatible holes

### Applications <a href="#applications" id="applications"></a>

* Weather station
* Storage barn environment monitoring

### Specification <a href="#specification" id="specification"></a>

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

![](https://static-cdn.m5stack.com/resource/docs/products/unit/envIII/envIII_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/envIII/envIII_06.webp)

### ENV version scheme comparison <a href="#env-version-scheme-comparison" id="env-version-scheme-comparison"></a>

| ENV I        | ENV II       | ENV III       | ENV IV       | ENV PRO |
| ------------ | ------------ | ------------- | ------------ | ------- |
| DHT12+BMP280 | SHT30+BMP280 | SHT30+QMP6988 | SHT40+BMP280 | BME688  |

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(PORT A) | GPIO22 | GPIO21 | 5V | GND |
| -------------- | ------ | ------ | -- | --- |
| ENV III Unit   | SCL    | SDA    | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/envIII/envIII_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* **Datasheet**
  * [QMP6988](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/enviii/QMP6988%20Datasheet.pdf)
  * [SHT30](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/SHT3x_Datasheet_digital.pdf)

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/envIII/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### COMPATIBLE <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (404).png" alt=""><figcaption></figcaption></figure>
