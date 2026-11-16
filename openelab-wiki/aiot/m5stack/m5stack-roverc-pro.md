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

# M5Stack RoverC Pro

### M5Stack RoverC Pro(W/O M5StickC)

***

### Product Link

{% embed url="https://openelab.io/products/roverc-pro" %}

### Description <a href="#description" id="description"></a>

**RoverC-Pro** is a programmable Mecanum wheel omnidirectional mobile robot base. Compatible with M5StickC/M5StickC PLUS, it can be initialized by just inserting M5StickC/M5StickC PLUS. The main control chip is STM32F030C6T6, and it incorporates four N20 worm gear motors to drive the wheels directly by the motor driver.

The PRO version provides a gripping mechanism controlled by a servo for gripping objects. The base provides two dedicated servo control drivers. In addition, it also provides two Grove-compatible I2C connectors to facilitate the expansion of other modules. The base is compatible with Lego and can be expanded structurally. There is an 16340 (700mAh) battery on the back, from which the battery can be replaced. It can be recharged through M5StickC/M5StickC PLUS. The power of the base is controlled by an independent switch.

### Features <a href="#features" id="features"></a>

* I2C Address 0x38
* Remote Control
* Gripping mechanism
* Programmable
* Four-channel motor driver
* LEGO compatible
* Extra Grove ports for expansion
* Equipped with 16340(700mAh) battery holder
* Flexible movement in all directions

### Applications <a href="#applications" id="applications"></a>

* Autonomous Rover
* Mini RC surveillance car
* Smart and cognitive toys

### Specifications <a href="#specifications" id="specifications"></a>

| Resources              | Parameter       |
| ---------------------- | --------------- |
| Communication protocol | I2C:0x38        |
| Net weight             | 187g            |
| Gross weight           | 245g            |
| Product Size           | 120 x 75 x 58mm |
| Package Size           | 115 x 85 x 65mm |

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat_roverc_pro/hat_roverc_pro_010.webp" alt=""><figcaption></figcaption></figure>

### RoverC PRO and RoverC comparison <a href="#roverc-pro-and-roverc-comparison" id="roverc-pro-and-roverc-comparison"></a>

| /              | RoverC PRO | RoverC        |
| -------------- | ---------- | ------------- |
| Servo Gripper  | x1         | /             |
| Servo Ext Port | x2         | /             |
| Battery        | Removable  | Non-removable |

### Pin Map <a href="#pin-map" id="pin-map"></a>

| M5StickC   | GPIO26 | GPIO0 | 5V | GND |
| ---------- | ------ | ----- | -- | --- |
| RoverC HAT | SCL    | SDA   | 5V | GND |
| I2C①       | SCL    | SDA   | 5V | GND |
| I2C②       | SCL    | SDA   | 5V | GND |

