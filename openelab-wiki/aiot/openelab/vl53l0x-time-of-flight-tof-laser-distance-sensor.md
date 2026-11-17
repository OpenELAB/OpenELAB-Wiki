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

# VL53L0X Time-of-Flight (TOF) Laser distance sensor

### VL53L0X Time-of-Flight (TOF) Laser distance sensor

***

### Product Link

{% embed url="https://openelab.io/products/vl53l0x-tof-sensor?_pos=1&_psq=VL53L0&_ss=e&_v=1.0#images-1" %}

### Introduction

The VL53L0X is a state-of-the-art Time-of-Flight (TOF) laser-ranging sensor that provides highly accurate distance measurements. It is capable of measuring absolute distances up to 2 meters, independent of the target reflectance. The sensor integrates an advanced laser-ranging module with a single-photon avalanche diode (SPAD) array, which allows for precise distance measurement in a compact form factor. This makes it suitable for applications such as obstacle detection, presence sensing, and proximity measurements in robotics, drones, and IoT devices.

<figure><img src="../../.gitbook/assets/image (857).png" alt=""><figcaption></figcaption></figure>

### **Features**

* High Accuracy: Provides precise distance measurements with millimeter accuracy.
* Long Range: Capable of measuring distances up to 2 meters.
* Fast Measurement Time: Quick response time suitable for dynamic applications.
* Compact Size: Small form factor for easy integration into various applications.
* Low Power Consumption: Ideal for battery-powered applications.
* I2C Interface: Simple communication with microcontrollers and other I2C devices.
* Ambient Light Immunity: Operates effectively in various lighting conditions.

### **Specifications**

* Operating Voltage: 2.8V to 3.5V
* Current Consumption: 10mA typical
* Measurement Range: 30mm to 2000mm
* Measurement Accuracy: ±3%
* Output Data Rate: Up to 50Hz
* Interface: I2C (address 0x29)
* Field of View (FOV): 25 degrees
* Operating Temperature: -20°C to 70°C

### **Pinout**

* VIN: Power supply pin (2.8V to 5V)
* GND: Ground pin
* SDA: I2C data line
* SCL: I2C clock line
* XSHUT: Shutdown pin (active low)
* GPIO1: Interrupt pin (optional, can be used for advanced functionalities)

### **Dimensions**

* Size:25.0x10.7mm

### **How to Use**

1. Power the Sensor: Connect the VIN pin to a power supply (2.6V to 5V) and the GND pin to ground.
2. Connect I2C Lines: Connect the SDA and SCL pins to the corresponding I2C lines of your microcontroller.
3. Optional Connections: Connect the XSHUT pin to a GPIO pin for enabling/disabling the sensor, and GPIO1 for interrupt functionalities if required.
4. Initialize the Sensor: Use a suitable library to initialize and configure the sensor. The following example demonstrates how to use the VL53L0X sensor with an Arduino.



```cpp
// Example code for Arduino

#include <Wire.h>
#include <VL53L0X.h>

VL53L0X sensor;

void setup() {
  Serial.begin(9600);
  Wire.begin();

  sensor.init();
  sensor.setTimeout(500);

  if (!sensor.init()) {
    Serial.println("Failed to detect and initialize sensor!");
    while (1);
  }
}

void loop() {
  // Read the distance
  uint16_t distance = sensor.readRangeSingleMillimeters();
  
  // Check for out of range errors
  if (sensor.timeoutOccurred()) { 
    Serial.print("Timeout!");
  } else {
    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println(" mm");
  }

  delay(500); // Wait for half a second before the next reading
}

```
