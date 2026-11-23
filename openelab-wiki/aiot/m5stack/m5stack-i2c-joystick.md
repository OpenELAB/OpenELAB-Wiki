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

{% hint style="info" %}
[**View M5Stack I2C Joystick Unit V1.1 on OpenELAB**](https://openelab.io/products/i2c-joystick-unit)

**Store SKU / option:** `M5-U024-C`. Match the purchased model and revision to the official reference below.
{% endhint %}

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

## Official documentation and development resources

Use [Unit Joystick v1.1](https://docs.m5stack.com/en/unit/Unit_Joystick_v1.1) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U024-C`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                                               |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U024-C_Unit_Joystick_v1.1/Structures)                        |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U024-C_Unit_Joystick_v1.1/Structures/Unit_Joystick_v1.1.stl) |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/JOYSTICK)                                                  |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
