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

# DS18B20 digital temperature sensor

### DS18B20 digital temperature sensor

***

### Product Link

{% embed url="https://openelab.io/products/ds18b20digitaltemperaturesensor?_pos=1&_sid=6490091a7&_ss=r" %}

### Introduction

The DS18B20 is a digital temperature sensor that provides highly accurate temperature readings over a wide range. It communicates via the 1-Wire protocol, allowing multiple sensors to be connected on the same data line, which simplifies wiring and reduces the number of I/O pins needed on the microcontroller. The sensor is commonly used in environmental monitoring, HVAC systems, and various industrial applications due to its precision and ease of use.

<figure><img src="../../.gitbook/assets/image (547).png" alt=""><figcaption></figcaption></figure>

### **Features**

* High Accuracy: Accurate temperature measurements with a precision of ±0.5°C over a wide range.
* Wide Temperature Range: Measures temperatures from -55°C to +125°C.
* 1-Wire Interface: Allows multiple sensors to be connected on a single bus.
* Programmable Resolution: User-selectable resolution from 9 to 12 bits.
* Unique 64-bit Serial Code: Each sensor has a unique code, enabling multiple sensors to be identified on the same bus.
* Low Power Consumption: Suitable for battery-powered applications.
* Parasitic Power Mode: Can operate without an external power supply by drawing power from the data line.

### **Specifications**

* Operating Voltage: 3.0V to 5.5V
* Temperature Range: -55°C to +125°C
* Accuracy: ±0.5°C (from -10°C to +85°C)
* Resolution: 9 to 12 bits (programmable)
* Interface: 1-Wire protocol
* Conversion Time: 93.75ms (9-bit) to 750ms (12-bit)
* Unique Serial Code: 64-bit

### **Pinout**

* VDD: Power supply pin (3.0V to 5.5V) - optional if using parasitic power mode
* GND: Ground pin
* DQ: Data line (1-Wire interface)

### **Dimensions**

* **TO-92 Package Size**: 4.9mm x 4.0mm x 5.9mm

### **How to Use**

1. Power the Sensor: Connect the VDD pin to a power supply (3.0V to 5.5V) and the GND pin to ground. If using parasitic power mode, connect a 4.7kΩ pull-up resistor between the DQ pin and the power supply.
2. Connect the Data Line: Connect the DQ pin to a digital I/O pin on your microcontroller.
3. Initialize the Sensor: Use a suitable library to initialize and communicate with the sensor. The following example demonstrates how to use the DS18B20 sensor with an Arduino.



```cpp
// Example code for Arduino

#include <OneWire.h>
#include <DallasTemperature.h>

#define ONE_WIRE_BUS 2 // Data wire is connected to pin 2

OneWire oneWire(ONE_WIRE_BUS);
DallasTemperature sensors(&oneWire);

void setup() {
  Serial.begin(9600);
  sensors.begin();
}

void loop() {
  sensors.requestTemperatures();
  float temperatureC = sensors.getTempCByIndex(0);
  Serial.print("Temperature: ");
  Serial.print(temperatureC);
  Serial.println(" °C");

  delay(1000); // Wait for a second before taking another reading
}

```
