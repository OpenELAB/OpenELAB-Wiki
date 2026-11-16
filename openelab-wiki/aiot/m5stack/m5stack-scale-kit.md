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

# M5Stack Scale Kit

### M5Stack Scale Kit with Weight Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-scale-kit" %}

### Description <a href="#description" id="description"></a>

Scales Kit is a high precision low-cost weighing kit. This digital Scales kit is consist of four pieces of half-bridge resistive strain gauges, with a total weighing range of `200kgs`. It is equipped with a 24-bit A/D converter chip `HX711`, specially designed for the high precision electronic scale. The built-in low-noise programmable amplifier supports `32`/`64`/`128` times gain adjustment. With the help of M5Stack core for programming, you can create IoT based Weighing Scale in just a few minutes!

NOTE: The Scale Kit will need a cover plate to work with, and the size of the cover plate should not exceed 50cm on one side.

### Features <a href="#features" id="features"></a>

* Total weighing range of 200kgs
* HX711:
  * High precision 24bit ADC
  * Programmable gain amplification 32, 64 and 128
  * 10SPS output data rate
* Half-bridge resistive strain gauge.
  * Output sensitivity: 1.0±0.1mV/V
  * Non-linearity: 0.3% F.S
  * Integrated Accuracy: 0.3%F.S
  * Zero output: ±0.3mv/V
  * Difference between upper and lower impedance of each strain gauge: 0.8Ω
  * Output (in) impedance: 1000±5Ω
* Development platform:
  * [UIFlow ](http://flow.m5stack.com/)(To be supported soon)
  * [Arduino](http://www.arduino.cc/)

### Applications <a href="#applications" id="applications"></a>

* Electronic weighing

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications                      | Parameters                                                                                                                                                                                                                                                  |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| HX711                               | <p>Output Sensitivity: High Precision 24bit ADC<br>Programmable Gain Amplification 32, 64, 128<br>10SPS Output Data Rate</p>                                                                                                                                |
| Half-Bridge Resistance Strain Gauge | <p>Output Sensitivity: 1.0±0.1mV/V<br>Nonlinearity: 0.3%FS<br>Comprehensive Accuracy: 0.3%FS<br>Zero Output: ±0.3mv/V<br>Each The difference between the upper and lower impedance of the gauge strain gauge: 0.8Ω<br>Output (input) impedance: 1000±5Ω</p> |
| Gross Weight                        | 92.5g                                                                                                                                                                                                                                                       |
| Net Weight                          | 126.3g                                                                                                                                                                                                                                                      |
| Packing Size                        | 105mm x 65mm x 40mm                                                                                                                                                                                                                                         |

### PinMap <a href="#pinmap" id="pinmap"></a>

* WEIGHT UNIT

| M5CORE - PORT B | G36            | G26             | 5V  | GND |
| --------------- | -------------- | --------------- | --- | --- |
| WEIGHT UNIT     | DATA Pin (DAT) | CLOCK Pin (CLK) | VCC | GND |

### Schematics <a href="#schematics" id="schematics"></a>

* WEIGHT UNIT

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/app/scales_kit/scales_kit_sch_01.webp" alt=""><figcaption></figcaption></figure>

### **Datasheet**

* [HX711](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/HX711_en.pdf)
