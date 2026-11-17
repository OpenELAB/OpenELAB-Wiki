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

# DHT11 Temperature-Humidity Sensor

### DHT11 Temperature-Humidity Sensor

***

### Product Link

{% embed url="https://openelab.io/products/dht11-temperature-humidity-sensor?_pos=1&_sid=b70209eea&_ss=r" %}

### **Introduction**

The DHT11 Temperature-Humidity Sensor is a low-cost, easy-to-use digital sensor for measuring temperature and humidity. It is widely used in environmental monitoring, home automation, and weather stations. The sensor consists of a thermistor and a capacitive humidity sensor to measure the surrounding air and provides calibrated digital output.

<figure><img src="../../.gitbook/assets/image (856).png" alt=""><figcaption></figcaption></figure>

### **Features**

* Low Cost: Affordable solution for temperature and humidity measurement.
* Easy to Use: Simple interface with microcontrollers such as Arduino and Raspberry Pi.
* Calibrated Digital Output: Provides accurate and reliable measurements.
* Wide Range of Applications: Suitable for various applications including HVAC, weather stations, and environmental monitoring.
* Stable Performance: Provides stable readings with long-term reliability.

### **Specifications**

* Operating Voltage: 3.3V to 5.5V
* Temperature Range: 0°C to 50°C
* Humidity Range: 20% to 90% RH
* Temperature Accuracy: ±2°C
* Humidity Accuracy: ±5% RH
* Output: Digital signal via a single-bus interface
* Sampling Rate: 1 Hz (one reading per second)

### **Pinout**

* VCC: Power supply pin (3.3V to 5.5V)
* GND: Ground pin
* DATA: Serial data pin for digital output

### **Dimensions**

* Size: 29.1x18.03mm
* Weight:8g

### **How to Use**

1. Power the Sensor: Connect the VCC pin to a power supply (3.3V to 5.5V) and the GND pin to ground.
2. Connect the Data Pin: Connect the DATA pin to a digital input pin of your microcontroller to read the temperature and humidity data.
3. Library and Code Example: Use an appropriate library to read data from the sensor. The following example demonstrates how to use the DHT11 sensor with an Arduino.



```cpp
// Example code for Arduino

#include "DHT.h"

#define DHTPIN 2     // Digital pin connected to the DHT sensor
#define DHTTYPE DHT11   // DHT11 sensor type

DHT dht(DHTPIN, DHTTYPE);

void setup() {
  Serial.begin(9600);
  dht.begin();
}

void loop() {
  // Wait a few seconds between measurements
  delay(2000);

  // Read temperature as Celsius
  float t = dht.readTemperature();
  // Read humidity
  float h = dht.readHumidity();

  // Check if any reads failed and exit early (to try again).
  if (isnan(t) || isnan(h)) {
    Serial.println("Failed to read from DHT sensor!");
    return;
  }

  // Print the results
  Serial.print("Humidity: ");
  Serial.print(h);
  Serial.print(" %\t");
  Serial.print("Temperature: ");
  Serial.print(t);
  Serial.println(" *C");
}

```
