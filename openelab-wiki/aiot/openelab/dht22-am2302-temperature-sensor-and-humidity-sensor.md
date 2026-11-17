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

# DHT22 AM2302 Temperature sensor and humidity sensor

### DHT22 AM2302 Temperature sensor and humidity sensor

***

### Product Link

{% embed url="https://openelab.io/products/dht22am2302temperatureandhumiditysensor?variant=43505968677062" %}

### Introduction

The DHT22 (also known as the AM2302) is a highly accurate digital temperature and humidity sensor. It is widely used in applications requiring precise environmental measurements, such as weather stations, HVAC systems, and smart home devices. The sensor uses a capacitive humidity sensor and a thermistor to measure the surrounding air, providing calibrated digital output.

<figure><img src="../../.gitbook/assets/image (548).png" alt=""><figcaption></figcaption></figure>

### **Features**

* High Accuracy: Accurate temperature and humidity readings.
* Wide Measurement Range: Supports a broad range of temperature and humidity measurements.
* Stable and Reliable: Provides stable performance and long-term reliability.
* Digital Output: Easy to interface with microcontrollers and other digital systems.
* Low Power Consumption: Efficient design suitable for battery-powered applications.

### **Specifications**

* Operating Voltage: 3.3V to 6V
* Temperature Range: -40°C to 80°C
* Humidity Range: 0% to 100% RH
* Temperature Accuracy: ±0.5°C
* Humidity Accuracy: ±2% RH
* Output: Digital signal via a single-bus interface
* Sampling Rate: 0.5 Hz (one reading every 2 seconds)

### **Pinout**

* VCC: Power supply pin (3.3V to 6V)
* GND: Ground pin
* DATA: Serial data pin for digital output
* NC: Not connected (some versions may have this pin)

### **Dimensions**

* Size: 15.1mm x 25mm x 7.7mm
* Weight: 2.4g

### **How to Use**

1. Power the Sensor: Connect the VCC pin to a power supply (3.3V to 6V) and the GND pin to ground.
2. Connect the Data Pin: Connect the DATA pin to a digital input pin of your microcontroller to read temperature and humidity data.
3. Use Pull-up Resistor: Place a 4.7kΩ pull-up resistor between the DATA and VCC pins to ensure proper communication.
4. Library and Code Example: Use an appropriate library to read data from the sensor. The following example demonstrates how to use the DHT22 sensor with an Arduino.

```cpp
// Example code for Arduino
```
