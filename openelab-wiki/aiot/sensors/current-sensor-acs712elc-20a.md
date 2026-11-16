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

# Current Sensor ACS712ELC-20A

### Current Sensor ACS712ELC-20A

***

### Product Link

{% embed url="https://openelab.io/products/currentsensoracs712elc-20a?_pos=1&_sid=799cd1d29&_ss=r#images-1" %}

### Introduction

The ACS712ELC-20A is a hall-effect-based current sensor that can measure both AC and DC currents. It provides accurate and reliable current measurement and is widely used in various applications such as motor control, load detection, over-current fault detection, and more. The sensor is designed to be easy to use with microcontrollers like Arduino and Raspberry Pi, making it a popular choice for electronics hobbyists and professionals alike.

<figure><img src="../../.gitbook/assets/image (550).png" alt=""><figcaption></figcaption></figure>

### **Features**

* Bidirectional Current Measurement: Measures both AC and DC currents.
* High Accuracy: Provides precise current measurement with minimal error.
* Integrated Hall Sensor: Utilizes hall-effect technology for non-intrusive current sensing.
* Wide Current Range: Capable of measuring up to ±20A.
* Analog Output: Outputs a voltage proportional to the current flowing through the sensor.
* Isolation: Electrically isolates the measured current path from the sensor's signal output, enhancing safety.

### **Specifications**

* Operating Voltage: 5V
* Current Range: ±20A
* Sensitivity: 100mV/A
* Output Voltage: 2.5V (at 0A current)
* Bandwidth: 80kHz
* Response Time: 5μs
* Accuracy: ±1.5%

### **Pinout**

* VCC: Power supply pin (5V)
* GND: Ground pin
* OUT: Analog output pin (voltage proportional to the current)

### **Dimensions**

* Size: 31mm x 13mm x 15mm
* Weight: 3g

### **How to Use**

1. Power the Sensor: Connect the VCC pin to a 5V power supply and the GND pin to ground.
2. Connect the Output: Connect the OUT pin to an analog input pin of your microcontroller to read the voltage corresponding to the current measurement.
3. Calibrate the Sensor: At 0A current, the output voltage should be around 2.5V. Use this as the reference point for calibration.
4. Measure Current: Write a program to read the analog voltage from the sensor and convert it to current using the sensitivity (100mV/A). The following example demonstrates how to use the ACS712ELC-20A sensor with an Arduino.

```cpp
// Example code for Arduino

const int sensorPin = A0; // Analog pin connected to OUT
const float sensitivity = 100.0; // Sensitivity in mV/A

void setup() {
  Serial.begin(9600);
}

void loop() {
  int sensorValue = analogRead(sensorPin);
  float voltage = sensorValue * (5.0 / 1023.0); // Convert to voltage
  float current = (voltage - 2.5) * 1000.0 / sensitivity; // Convert to current in A

  Serial.print("Current: ");
  Serial.print(current);
  Serial.println(" A");

  delay(1000); // Wait for a second before taking another reading
}


```
