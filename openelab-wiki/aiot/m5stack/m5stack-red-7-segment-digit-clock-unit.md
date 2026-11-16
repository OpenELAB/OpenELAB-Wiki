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

# M5Stack Red 7-Segment Digit Clock Unit

### M5Stack Red 7-Segment Digit Clock Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-digit-clock-unit" %}

### Introduction

Digi-Clock unit is a 2.1-inch 4-digit 7-segment display module designed to display decimal numbers and act as a clock. Each digit on the display has a decimal point, and there is an additional wire for displaying colon-dots in the center, allowing for clock functionality.\
The unit utilizes the TM1637 as the driver IC, which controls the display and facilitates easy communication with the connected microcontroller or system. The I2C communication protocol is employed, and the unit incorporates an STM32F030 microcontroller for I2C communication.\
To provide flexibility, the I2C address of the Digi-Clock unit can be modified using a 4-bit dip switch, allowing multiple modules to be connected and addressed individually. This feature simplifies the integration and control of multiple display modules within a system. The red LED display supports eight levels of brightness, providing options for optimal visibility in different environments or applications. Users can adjust the brightness level to meet their specific requirements.\
Additionally, the unit includes four fixing holes, which allow for secure mounting and integration into various projects or installations. This ensures stability and ease of use when incorporating the Digi-Clock unit into different applications or systems.



<figure><img src="../../.gitbook/assets/image (469).png" alt=""><figcaption></figcaption></figure>

### Features

* 4-digit red dislpay
* I2C port, adjustable I2C address
* 8 brightness
* Low power consumption
* 4 fixing holes for multiple installations

### Specifications

| Spec              | Parameters        |
| ----------------- | ----------------- |
| MCU               | STM32F030         |
| Driver IC         | TM1637            |
| Communication     | I2C, addr: 0x30   |
| Power Supply      | 5V DC             |
| Net Weight        | 12.5g             |
| Gross Weight      | 17.8g             |
| Product Dimension | 50 \* 31 \* 14mm  |
| Package Dimension | 136 \* 92 \* 15mm |

### Pinout

![](<../../.gitbook/assets/image (475).png>)

### Dimensions

size:50 \* 31 \* 14mm

weight:12.5g



### How to Use

#### Arduino <a href="#arduino" id="arduino"></a>

* [M5Unit-Digi\_Clock Lib](https://github.com/m5stack/M5Unit-DigiClock)

```cpp
#include "Wire.h"
#include "M5UNIT_DIGI_CLOCK.h"

/* For M5Stack Basic */
#define SDA 21
#define SCL 22
#define ADD 0x30

/* For M5Atom Lite/Matrix */
// #define SDA 26
// #define SCL 32
// #define ADD 0x30

M5UNIT_DIGI_CLOCK Digiclock;

void setup() 
{
    delay(2000);
    Serial.begin(115200);
    Wire.begin(SDA, SCL);

    /* Digital clock init */
    if (Digiclock.begin(&Wire, SDA, SCL, ADD)) 
    {
        Serial.println("Digital clock init successful");
    } 
    else 
    {
        Serial.println("Digital clock init error");
        while (1);
    }
    char buff[] = "    ";
    Digiclock.setString(buff);
    delay(2000);
}

void loop() 
{
    char buff[] = "8.8.:8.8.";
    Digiclock.setString(buff);

    for (int i = 0; i < 5; i++) 
    {
        Digiclock.setBrightness(9);
        delay(150);
        Digiclock.setBrightness(0);
        delay(150);
    }
    delay(100);

    for (int i = 0; i < 4; i++) 
    {
        for (uint8_t i = 0; i < 9; i++) 
        {
            Digiclock.setBrightness(i);
            delay(20);
        }
        for (uint8_t i = 8; i > 0; i--) 
        {
            Digiclock.setBrightness(i);
            delay(20);
        }
    }
    delay(100);

    Digiclock.setBrightness(9);
    for (int j = 0; j < 3; j++) 
    {
        for (int i = 0; i < 10; i++) 
        {
            sprintf(buff, "%d.%d.:%d.%d.", i, i, i, i);
            Digiclock.setString(buff);
            Serial.println(buff);
            delay(200);
        }
    }
    delay(100);

    Digiclock.setBrightness(9);
    for (;;) 
    {
        char buff2[] =  "12:00";
        Digiclock.setString(buff2);
        Serial.printf(buff2);
        delay(1000);
        char buff3[] =  "1200";
        Digiclock.setString(buff3);
        Serial.printf(buff3);
        delay(1000);
    }
    delay(100);
}

```
