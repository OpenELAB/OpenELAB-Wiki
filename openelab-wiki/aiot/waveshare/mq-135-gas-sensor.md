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

# MQ-135 Gas Sensor

{% hint style="info" %}
[**View Waveshare MQ-135 Gas Sensor | AOUT/DOUT | 2.5-5V on OpenELAB**](https://openelab.io/products/mq-135-gas-sensor)

**Store SKU / option:** `Waveshare-9528`. Match the purchased model and revision to the official reference below.
{% endhint %}

### MQ-135 Gas Sensor

***

### Product Link

{% embed url="https://openelab.io/products/mq-135-gas-sensor?_pos=1&_sid=2dc0afd8f&_ss=r" %}

### **Introduction**

The MQ-135 gas sensor is a popular sensor used to detect a wide range of gases including ammonia, sulfide, and benzene steam, as well as smoke and other harmful gases. It is commonly used in air quality monitoring systems and various industrial applications due to its high sensitivity and fast response time.

<figure><img src="../../.gitbook/assets/image (552).png" alt=""><figcaption></figcaption></figure>

### **Features**

* High Sensitivity: Detects a wide range of gases with high accuracy.
* Fast Response Time: Quick response to changes in gas concentrations.
* Wide Detection Range: Suitable for detecting ammonia, sulfide, benzene steam, smoke, and other harmful gases.
* Stable and Long Life: Provides stable readings over a long period.
* Simple Interface: Easy to connect to microcontrollers like Arduino and Raspberry Pi.

### **Specifications**

* Operating Voltage: 5V
* Detecting Range: 10-1000 ppm (Ammonia, Benzene, Alcohol)
* Preheat Time: Over 24 hours
* Sensitivity: Adjustable via onboard potentiometer
* Output: Analog (0-5V) and Digital (TTL logic)

### **Pinout**

* VCC: Power supply pin (5V)
* GND: Ground pin
* AO: Analog output pin
* DO: Digital output pin (High/Low signal based on threshold)

### **Dimensions**

* Size: 40.0mm \* 21.0mm
* Weight: 5g

### **How to Use**

1. Power the Sensor: Connect the VCC pin to the 5V power supply and the GND pin to the ground.
2. Read Analog Values: Connect the AO pin to an analog input of your microcontroller to read the gas concentration values.
3. Set Threshold: Adjust the onboard potentiometer to set the threshold for the digital output.
4. Read Digital Values: Connect the DO pin to a digital input of your microcontroller to receive high/low signals based on the gas concentration exceeding the set threshold.
5. Code Example: Write a simple program to read the analog and digital values from the sensor and take appropriate actions based on the readings. For example, you can trigger an alarm if the gas concentration exceeds a certain limit.

```cpp
// Example code for Arduino

int analogPin = A0; // Analog pin connected to AO
int digitalPin = 2; // Digital pin connected to DO

void setup() {
  Serial.begin(9600);
  pinMode(digitalPin, INPUT);
}

void loop() {
  int analogValue = analogRead(analogPin);
  int digitalValue = digitalRead(digitalPin);

  Serial.print("Analog Value: ");
  Serial.println(analogValue);

  if (digitalValue == HIGH) {
    Serial.println("Gas detected!");
  } else {
    Serial.println("No gas detected.");
  }

  delay(1000); // Wait for a second before taking another reading
}

```

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/MQ-135_Gas_Sensor) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need     | Model-specific reference                                                                             |
| -------------------- | ---------------------------------------------------------------------------------------------------- |
| Electrical schematic | [Read electrical schematic](https://files.waveshare.com/upload/6/62/MQ-135-Gas-Sensor-Schematic.pdf) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
