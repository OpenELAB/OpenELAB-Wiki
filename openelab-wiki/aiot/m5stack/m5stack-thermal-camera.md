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

# M5Stack Thermal Camera

{% hint style="info" %}
[**View M5Stack Thermal Camera 2 Unit M5-U149 MLX90640 Infrared Thermal Imaging Sensor on OpenELAB**](https://openelab.io/products/thermal-camera-2-unit)

**Store SKU / option:** `M5-U149`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Thermal Camera 2 Unit

***

### Product Link

{% embed url="https://openelab.io/products/thermal-camera-2-unit" %}

### Description <a href="#description" id="description"></a>

UNIT Thermal2 is a data processing MCU-equipped MLX90640 thermal imaging acquisition unit. It has 32x24 imaging pixels, a field of view of 110°x75°, and a temperature measurement range of -40°C to 300°C. The MCU uses ESP32, which is capable of high and low temperature alarms, average, maximum and minimum values reading, and data caching via data processing. The board integrates with a buzzer, RGB indicator, function and reset buttons, and communicates with the host computer through I2C. This product can be used together with the host computer or separately, and is applicable for temperature measurement and abnormal alarms.

### Features <a href="#features" id="features"></a>

* MCU:ESP32-PICO-D4
* MLX90640 Infrared (IR) Sensor
* Reset buttom
* Passive buzzer
* Integrated programmable RGB LED
* GROVE I2C/HY2.0-4Pinterface
* Programming platform: Arduino/UIFlow

### Applications <a href="#applications" id="applications"></a>

* High-precision non-contact temperature measurement
* Motion detection
* Visual infrared thermometer
* DIY Projects

### Specifications <a href="#specifications" id="specifications"></a>

| Resources             | Parameters          |
| --------------------- | ------------------- |
| MCU                   | ESP32-PICO-D4       |
| SENSOR                | MLX90640            |
| POWER                 | 5V @ 0.5A           |
| Field of View         | 110°×75°            |
| Measurement Range     | -40°C \~ 300°C      |
| Resolution            | 32 x 24             |
| Refresh Rate          | 0.5Hz-64Hz          |
| Operating temperature | 0°C \~ 40°C         |
| Housing material      | ABS+Plastic ( PC )  |
| Product Size          | 48mm × 24mm ×8mm    |
| Package Size          | 136mm × 92mm × 13mm |
| Product Weight        | 4.9g                |
| Package Weight        | 10.7g               |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/img-d9961e22-fb5e-4eb0-9b5e-cbe4a49611fb.png" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Thermal2%20Unit/img-6960aad1-5b8c-41aa-9fae-fee7abaf2cb5.png" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (393).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Thermal2](https://docs.m5stack.com/en/unit/Unit_Thermal2) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U149`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                             | Model-specific reference                                                                                                                      |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic                         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/603/SCH_UNIT-THERMAL2.pdf)                                       |
| Mechanical / CAD files                       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U149_Unit_Thermal2/Structures)                      |
| Mechanical / CAD files                       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U149_Unit_Thermal2/Structures/Unit_Thermal2.stl)    |
| Official source: M5Unit-Thermal2             | [Read official source: m5unit-thermal2](https://github.com/m5stack/M5Unit-Thermal2)                                                           |
| Example source: FactoryTest.ino              | [Read example source: factorytest.ino](https://github.com/m5stack/M5Unit-Thermal2-Internal-FW/blob/main/examples/FactoryTest/FactoryTest.ino) |
| Official source: M5Unit-Thermal2-Internal-FW | [Read official source: m5unit-thermal2-internal-fw](https://github.com/m5stack/M5Unit-Thermal2-Internal-FW)                                   |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
