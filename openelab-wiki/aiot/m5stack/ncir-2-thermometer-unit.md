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

# NCIR 2 Thermometer Unit

### M5Stack NCIR 2 Thermometer Unit (MLX90614)

***

### Product Link

{% embed url="https://openelab.io/products/ncir-2-thermometer-unit" %}

### Description <a href="#description" id="description"></a>

Living through this pandemic has made contactless temperature sensing a must! The NCIR 2 Thermometer Unit utilizes the MLX90614 temperature sensor, and take ambient and object temperature readings with No Contact. Great for socially-distant reality.

The MLX90614 sensor is factory calibrated in wide temperature range, -40 to 125 ˚C for the ambient temperature and -70 to 380 ˚C for the object temperature. The embedded MCU - STM32 can process the data to achieve high/low temperature alert function. There are also buzzer, RGB LED, function button and reset button on board.

This Unit can either work with M5Core through I2C protocol, or work alone. Suitable for medical, environmental monitoring and home automation applications.

### Features <a href="#features" id="features"></a>

* STM32F030F4P6
* MLX90614 IR Sensor
* HY2.0-4P Connector (I2C)
* Program platform: Arduino, UIFlow
* Two brick-compatible holes

### Applications <a href="#applications" id="applications"></a>

* High-precision non-contact temperature measurement
* Motion detection
* Home Automation

### Specification <a href="#specification" id="specification"></a>

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

![](https://static-cdn.m5stack.com/resource/docs/products/unit/NCIR2/img-77bc1f8d-bedb-4081-b74a-000d5d6e36d5.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/NCIR2/img-a8932041-3ca1-45eb-89a4-0c3a2763f339.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/NCIR2/img-53c5aa20-4ecd-411d-af33-57af9896c06f.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/NCIR2/img-fd84b907-a693-4934-8135-08b21885b8d7.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/NCIR2/img-bd85f23f-8075-447c-85b0-27dffaf35dfc.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/NCIR2/img-162ae4fb-2013-42e2-8321-0c136d29c71f.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [STM32F030F4P6 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/STM32F030F4P6.PDF)
* [MLX90614 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/hat/MLX90614-Datasheet-Melexis_en.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/NCIR2/img-0997fcc9-2488-456a-b815-08a21af044e1.webp" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/NCIR2/img-2917ac6d-78f5-414a-a3a5-dc3e10b4068a.png" alt=""><figcaption></figcaption></figure>

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/NCIR2/protocol.png" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [Arduino Example （Core）](https://github.com/m5stack/M5Unit-NCIR2)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/NCIR2/arduinoCase-1665570359798%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20221012180333.png" alt=""><figcaption></figcaption></figure>

* [UNIT NCIR2 firmware](https://github.com/m5stack/M5Unit-NCIR2-Internal-FW)

### COMPATIBLE <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (421).png" alt=""><figcaption></figcaption></figure>
