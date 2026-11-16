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

# M5Stack Tube/Air Pressure Unit

### M5Stack Tube/Air Pressure Unit

***

### Product Link

{% embed url="https://openelab.io/products/tube-air-pressure-unit" %}

### Description <a href="#description" id="description"></a>

Tube pressure is a wide range `air pressure sensor` that supports `-100 ~ 200Kpa`. You can connect one end of the tube to the gas inlet. This sensor transmitted onto mapping value `-100 ~ 200Kpa` and `0.1 ~ 3.1V` voltage output. Also having a protective housing for long term stability. It’s an accessory that your industrial use cannot live without.

### Product Features <a href="#product-features" id="product-features"></a>

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

![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_06.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_07.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_08.webp)

### Output voltage and pressure value conversion <a href="#output-voltage-and-pressure-value-conversion" id="output-voltage-and-pressure-value-conversion"></a>

```cpp
//P: Actual test pressure value, unit (Kpa)
//Vout: sensor voltage output value
P = (Vout-0.1)/3.0*300.0-100.0
 
```

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_linear_01.webp" alt=""><figcaption></figcaption></figure>

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/tube_pressure/tube_pressure_sch_01.webp" alt=""><figcaption></figcaption></figure>

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
