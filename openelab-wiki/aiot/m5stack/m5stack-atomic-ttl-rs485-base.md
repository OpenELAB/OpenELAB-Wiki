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

# M5Stack ATOMIC TTL-RS485 Base

### M5Stack ATOMIC TTL-RS485 Base

***

### Product Link

{% embed url="https://security.feishu.cn/link/safety?target=https%3A%2F%2Fopenelab.io%2Fproducts%2Fm5stack-ttl-rs485&scene=ccm&logParams=%7B%22location%22%3A%22ccm_sheet%22%7D&lang=zh-CN&from=from_parent_sheet" %}

### Introduction

ATOMIC is a DIY Proto Kit designed specially for the Atom series, which makes it convenient for users to design small circuits or external hardware by themselves. It can be stacked with Atom directly via the 9 pins on the base. Two blank proto boards are provided in the kit, each of which provides more than 60 hole positions to meet the spatial layout requirements of users. A pair of 3.96 4 pin connectors are contained to make the external electrical connection more reliable. The shell incorporates a series of ventilation holes which allow heat dissipation and allows for more accurate temperature and humidity readings from sensors. The product provides a variety of attachment methods, such as mounting hole, Lego connection, screw mounting, etc. If you want to make a mini controller with customized characteristics, ATOMIC should be the best choice.

<figure><img src="../../.gitbook/assets/image (509).png" alt=""><figcaption></figcaption></figure>

### Features

* Compatible with Atom Matrix/Atom Lite
* Compact design
* DIY Style
* Built-in Infra-red
* Open design

### Specifications

| Specification | Parameter    |
| ------------- | ------------ |
| External port | VH-3.96 4P   |
| Gross weight  | 42g          |
| Product Size  | 24\*48\*18mm |
| Package Size  | 50\*50\*20mm |
| Case material | Plastic (PC) |

### Pinout

* GND: Ground
* DC: 12V
* A: RS485 Differential Signal Positive
* B: RS485 Differential Signal Negative

### Dimensions

Size:2&#x34;_\*48\*_&#x31;8mm

weight:20g

### How to Use

* **Connect the Module**:
  * Connect the M5Stack ATOMIC TTL-RS485 Base to your M5Stack core using the appropriate port, typically the GROVE port.
* **Wiring**:
  * Connect the RS485 device to the A and B pins on the ATOMIC TTL-RS485 Base.
  * If needed, connect the 5V and GND pins to power the RS485 device.
  * Use the TX and RX pins for UART communication with your M5Stack core.
* **Install Software Libraries**:
  * Ensure you have the M5Stack library installed in your Arduino IDE or other development environments. You can install it via the Library Manager in the Arduino IDE.
* **Coding**:
  * Open the Arduino IDE and create a new sketch.
  * Include the necessary libraries for M5Stack and RS485 communication. For example:

```cpp
#include <M5Stack.h>
#include <Wire.h>
```

Initialize the M5Stack and set up the RS485 communication in the `setup()` function:

```cpp
void setup() {
    M5.begin();
    Serial.begin(115200);
    Serial2.begin(9600, SERIAL_8N1, 16, 17); // Example pins, check your module's pin configuration
}

```

Write your logic for sending and receiving data over RS485 in the `loop()` function:

```cpp
void loop() {
    // Example of sending data
    Serial2.write("Hello RS485");

    // Example of receiving data
    if (Serial2.available()) {
        String received = Serial

```
