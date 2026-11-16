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

# GY-521 MPU-6050 3-axis gyroscope and acceleration sensor

### GY-521 MPU-6050 3-axis gyroscope and acceleration sensor

***

### Product Link

{% embed url="https://openelab.io/products/gy-521-mpu-6050?_pos=1&_sid=b3e616b2c&_ss=r" %}

### Introduction

The GY-521 module integrates the MPU-6050 sensor, which combines a 3-axis gyroscope and a 3-axis accelerometer. It is widely used in motion-tracking devices, drones, robotics, and various other applications that require precise measurement of movement and orientation. The sensor communicates with microcontrollers via the I2C interface, making it easy to integrate into various projects.

<figure><img src="../../.gitbook/assets/image (859).png" alt=""><figcaption></figcaption></figure>

### **Features**

* 6-axis Motion Tracking: Combines a 3-axis gyroscope and a 3-axis accelerometer.
* High Precision: Provides accurate measurements of angular velocity and linear acceleration.
* Digital Motion Processing (DMP): On-chip algorithms for sensor fusion and calibration.
* I2C Interface: Simplifies communication with microcontrollers.
* Low Power Consumption: Suitable for battery-powered applications.
* Embedded Temperature Sensor: Monitors the ambient temperature.

### **Specifications**

* Operating Voltage: 3V to 5V
* Gyroscope Range: ±250, ±500, ±1000, ±2000°/s
* Accelerometer Range: ±2g, ±4g, ±8g, ±16g
* Sampling Rate: Up to 1kHz
* Communication Interface: I2C (address 0x68)
* Temperature Sensor Range: -40°C to 85°C
* Current Consumption: 3.9mA (gyro) and 500µA (accel)

### **Pinout**

* VCC: Power supply pin (3V to 5V)
* GND: Ground pin
* SCL: I2C clock line
* SDA: I2C data line
* INT: Interrupt pin (optional, for advanced functionalities)
* XDA: Auxiliary I2C data line (optional)
* XCL: Auxiliary I2C clock line (optional)
* ADO: Address pin (can be used to change I2C address)

### **Dimensions**

* Size: 21x16mm

### **How to Use**

1. Power the Sensor: Connect the VCC pin to a power supply (3V to 5V) and the GND pin to ground.
2. Connect I2C Lines: Connect the SCL and SDA pins to the corresponding I2C lines of your microcontroller.
3. Optional Connections: Connect the INT pin to a GPIO pin for interrupt functionalities if required.
4. Initialize the Sensor: Use an appropriate library to initialize and configure the sensor. The following example demonstrates how to use the MPU-6050 sensor with an Arduino.



```cpp
// Example code for Arduino

#include <Wire.h>
#include <MPU6050.h>

MPU6050 sensor;

void setup() {
  Serial.begin(9600);
  Wire.begin();

  sensor.initialize();
  if (!sensor.testConnection()) {
    Serial.println("MPU6050 connection failed!");
    while (1);
  }
}

void loop() {
  // Read accelerometer and gyroscope values
  int16_t ax, ay, az, gx, gy, gz;
  sensor.getMotion6(&ax, &ay, &az, &gx, &gy, &gz);

  // Print accelerometer values
  Serial.print("aX = "); Serial.print(ax);
  Serial.print(" | aY = "); Serial.print(ay);
  Serial.print(" | aZ = "); Serial.println(az);

  // Print gyroscope values
  Serial.print("gX = "); Serial.print(gx);
  Serial.print(" | gY = "); Serial.print(gy);
  Serial.print(" | gZ = "); Serial.println(gz);

  delay(500); // Wait for half a second before taking another reading
}

```
