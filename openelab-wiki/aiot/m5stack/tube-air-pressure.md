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

# Tube/Air Pressure

{% hint style="info" %}
[**View M5Stack Tube Air Pressure Unit Positive and Negative Pressure Gauge on OpenELAB**](https://openelab.io/products/tube-air-pressure-unit)

**Store SKU / option:** `M5-U130`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Tube/Air Pressure Unit

***

### Product Link

{% embed url="https://openelab.io/products/tube-air-pressure-unit" %}

### Description <a href="#description" id="description"></a>

Tube pressure is a wide range `air pressure sensor` that supports `-100 ~ 200Kpa`. You can connect one end of the tube to the gas inlet. This sensor transmitted onto mapping value `-100 ~ 200Kpa` and `0.1 ~ 3.1V` voltage output. Also having a protective housing for long term stability. It’s an accessory that your industrial use cannot live without.

### Features <a href="#product-features" id="product-features"></a>

* Includes Integrated piezo-resistive pressure sensor with wide temperature compensation
* Linear output, easy to use
* Measurement range: -100 \~ 200Kpa
* Output: 0.1 \~ 3.1V
* Precision: 1.5Kpa
* 2x LEGO compatible holes
* Support UIFlow graphical programming

### Application <a href="#application" id="application"></a>

* Air pressure measurement

### Specification <a href="#specification" id="specification"></a>

| Specifications    | Parameters         |
| ----------------- | ------------------ |
| Sensor Model      | MCP-H10-B200KPPN   |
| Detections        | Gas                |
| Measurement range | -100 \~ 200Kpa     |
| Output            | 0.1 \~ 3.1V        |
| Precision         | 1.5Kpa (0 \~ 85°C) |
| Supply voltage    | 5V                 |
| Net weight        | 4.8g               |
| Gross weight      | 10g                |
| Product size      | 24 \* 32 \* 12mm   |
| Packing size      | 93 \* 138mm        |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_06.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_07.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_08.webp)

### Output voltage and pressure value conversion <a href="#output-voltage-and-pressure-value-conversion" id="output-voltage-and-pressure-value-conversion"></a>

```cpp
//P: Actual test pressure value, unit (Kpa)
//Vout: sensor voltage output value
P = (Vout-0.1)/3.0*300.0-100.0
 
```

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_linear_01.webp" alt=""><figcaption></figcaption></figure>

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/tube_pressure/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

```cpp

#include <Arduino.h>

int sensorPin = 32; // Sensor Pin

void setup() {
  Serial.begin(115200);
  pinMode(sensorPin, INPUT);  //Sets the specified pin to input mode.  设置指定引脚为输入模式
}

void loop() {
  float raw = analogRead(sensorPin);  // read the value from the sensor.  读取当前传感器的值
  float Vout = raw/4095*3.6; 
  float P = (Vout-0.1)/3.0*300.0-100.0;
  Serial.printf("pressure: %f.2 Kpa\r\n", P);
  delay(100);
}
 
```

#### UIFlow <a href="#uiflow" id="uiflow"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

### COMPATIBLE

<figure><img src="../../.gitbook/assets/image (411).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Tube Pressure](https://docs.m5stack.com/en/unit/Unit_Tube_Pressure) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U130`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                                             |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U130_Unit_Tube_Pressure/Structures)                        |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U130_Unit_Tube_Pressure/Structures/Unit_Tube_Pressure.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
