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

# BME280 Humidity Pressure Temperature Sensors

### BME280 Humidity Pressure Temperature Sensors

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Introduction

The BME280 is a high-performance sensor that measures humidity, pressure, and temperature with high precision and low power consumption. It is widely used in environmental monitoring, weather stations, IoT applications, and other projects requiring accurate environmental data. The sensor is integrated into a compact package, making it easy to incorporate into various devices and systems.

<figure><img src="../../.gitbook/assets/image (546).png" alt=""><figcaption></figcaption></figure>

### **Features**

* Multi-sensor Functionality: Measures humidity, pressure, and temperature.
* High Precision: Provides accurate measurements for all three parameters.
* Low Power Consumption: Ideal for battery-operated devices.
* Compact Size: Small form factor suitable for a variety of applications.
* Flexible Interface: Supports both I2C and SPI communication protocols.
* Fast Response Time: Quick measurement updates for dynamic environments.
* Wide Operating Range: Operates effectively in a broad range of environmental conditions.

### **Specifications**

* Operating Voltage: 1.8V to 3.6V
* Humidity Range: 0% to 100% RH
* Humidity Accuracy: ±3% RH
* Pressure Range: 300 hPa to 1100 hPa
* Pressure Accuracy: ±1 hPa
* Temperature Range: -40°C to +85°C
* Temperature Accuracy: ±1°C
* Interface: I2C and SPI
* Power Consumption: 3.6µA (in normal mode)

### **Pinout**

* VCC: Power supply pin (1.8V to 3.6V)
* GND: Ground pin
* SDA: I2C data line / SPI MOSI
* SCL: I2C clock line / SPI SCK
* CSB: Chip select for SPI (connect to GND for I2C)
* SDO: SPI MISO / I2C address selection

### **Dimensions**

* Size:9 x 11 x 2mm

### **How to Use**

1. Power the Sensor: Connect the VCC pin to a power supply (1.8V to 3.6V) and the GND pin to ground.
2. Choose Communication Protocol:
   * For I2C: Connect the SDA and SCL pins to the corresponding I2C lines on your microcontroller. Connect the CSB pin to GND.
   * For SPI: Connect the SDA (MOSI), SCL (SCK), CSB, and SDO (MISO) pins to the corresponding SPI lines on your microcontroller.
3. Initialize the Sensor: Use an appropriate library to initialize and configure the sensor. The following example demonstrates how to use the BME280 sensor with an Arduino.



{% code collapsedlinecount="10" %}
```cpp
// Example code for Arduino

#include <Wire.h>
#include <Adafruit_Sensor.h>
#include <Adafruit_BME280.h>

#define SEALEVELPRESSURE_HPA (1013.25)

Adafruit_BME280 bme; // I2C

void setup() {
  Serial.begin(9600);
  if (!bme.begin(0x76)) { // Address 0x76 or 0x77
    Serial.println("Could not find a valid BME280 sensor, check wiring!");
    while (1);
  }
}

void loop() {
  Serial.print("Temperature = ");
  Serial.print(bme.readTemperature());
  Serial.println(" *C");

  Serial.print("Pressure = ");
  Serial.print(bme.readPressure() / 100.0F);
  Serial.println(" hPa");

  Serial.print("Humidity = ");
  Serial.print(bme.readHumidity());
  Serial.println(" %");

  Serial.println();
  delay(2000); // Wait for 2 seconds before the next reading
}

```
{% endcode %}
