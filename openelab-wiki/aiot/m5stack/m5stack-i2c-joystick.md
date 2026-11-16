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

# M5Stack I2C Joystick

### M5Stack I2C Joystick Unit V1.1

***

### Product Link

{% embed url="https://openelab.io/products/i2c-joystick-unit" %}

### Description <a href="#description" id="description"></a>

**Joystick** is a joystick control input unit, adopts I2C communication interface, supports three-axis control signal input (X/Y-axis offset analog input, Z-axis key digital input). Suitable for application scenarios such as games/robot control.

### Features <a href="#features" id="features"></a>

* Three-axis input:
  * X/Y axis offset analog input
  * Z-axis key digital input
* 2x LEGO compatible holes
* Development platform: Arduino, UIFlow(Blockly, Python)

### Applications <a href="#applications" id="applications"></a>

* Game Controller
* Robot remote control

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications                | Parameters       |
| ----------------------------- | ---------------- |
| MCU                           | MEGA8A           |
| Communication protocol        | I2C: 0x52        |
| X, Y axis offset output value | 0-255            |
| Z axis button output value    | 0/1              |
| Net weight                    | 11g              |
| Gross weight                  | 27g              |
| Product size                  | 48 \* 24 \* 32mm |
| Packing size                  | 75 \* 45 \* 30mm |

### PinMap <a href="#pinmap" id="pinmap"></a>

* JOYSTICK

| M5CORE - PORT A | G21 | G22 | 5V  | GND |
| --------------- | --- | --- | --- | --- |
| JOYSTICK        | SDA | SCL | VCC | GND |

### Protocol <a href="#protocol" id="protocol"></a>

* Protocol type I2C
* I2C Address: **0x52**

JOYSTICK REG 0x52

|  REG | len | description          |                    return values                    |
| :--: | :-: | -------------------- | :-------------------------------------------------: |
| 0x52 |  3  | Read joystick status | <p>[0] X VALUE<br>[1] Y VALUE<br>[2] BTN STATUS</p> |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/joystick_1.1/joystick_1.1_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (951).png" alt=""><figcaption></figcaption></figure>
