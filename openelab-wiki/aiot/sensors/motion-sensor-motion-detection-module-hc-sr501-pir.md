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

# Motion Sensor Motion Detection Module HC-SR501 PIR

### Motion Sensor Motion Detection Module HC-SR501 PIR

***

### Product Link

{% embed url="https://openelab.io/products/motion-sensor?_pos=1&_sid=732e91fe8&_ss=r" %}

### **Introduction**

The HC-SR501 PIR (Passive Infrared) Motion Sensor Module is widely used for motion detection applications. It detects motion by measuring the infrared (IR) light radiating from objects in its field of view. When an object, such as a human, passes within its range, the sensor detects the change in infrared radiation and triggers a signal. This module is commonly used in security systems, automation projects, and lighting control systems.

<figure><img src="../../.gitbook/assets/image (551).png" alt=""><figcaption></figcaption></figure>

### **Features**

* High Sensitivity: Detects motion up to 7 meters away.
* Adjustable Delay Time: User can set the delay time from 5 seconds to 5 minutes.
* Wide Range Detection: Covers an angle of 120 degrees.
* Low Power Consumption: Efficient and consumes minimal power when idle.
* Easy Integration: Simple to connect with microcontrollers like Arduino and Raspberry Pi.

### **Specifications**

* Operating Voltage: 5V to 20V
* Detection Range: Up to 7 meters
* Detection Angle: 120 degrees
* Delay Time: Adjustable from 5 seconds to 5 minutes
* Output: High/Low (3.3V TTL)

### **Pinout**

* VCC: Power supply pin (5V to 20V)
* GND: Ground pin
* OUT: Digital output pin (High when motion is detected, Low otherwise)

### **Dimensions**

* Size: 33 x 25 x 30mm
* Weight: 25g

### **How to Use**

1. Power the Sensor: Connect the VCC pin to a power supply (5V to 20V) and the GND pin to ground.
2. Connect the Output: Connect the OUT pin to a digital input pin of your microcontroller to receive the motion detection signal.
3. Adjust Sensitivity and Delay: Use the onboard potentiometers to adjust the sensitivity and delay time as per your requirement.
4. Code Example: Write a simple program to read the digital output from the sensor and perform actions based on motion detection. For instance, you can trigger an LED or an alarm when motion is detected.



```cpp
// Example code for Arduino

int pirPin = 2; // Digital pin connected to OUT

void setup() {
  Serial.begin(9600);
  pinMode(pirPin, INPUT);
  pinMode(LED_BUILTIN, OUTPUT);
}

void loop() {
  int pirValue = digitalRead(pirPin);

  if (pirValue == HIGH) {
    Serial.println("Motion detected!");
    digitalWrite(LED_BUILTIN, HIGH); // Turn on the LED
  } else {
    Serial.println("No motion.");
    digitalWrite(LED_BUILTIN, LOW); // Turn off the LED
  }

  delay(1000); // Wait for a second before taking another reading
}

```

