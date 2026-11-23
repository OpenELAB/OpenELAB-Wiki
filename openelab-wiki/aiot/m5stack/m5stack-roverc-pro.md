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

{% hint style="info" %}
[**View M5Stack RoverC Pro(W/O M5StickC) on OpenELAB**](https://openelab.io/products/roverc-pro)

**Store SKU / option:** `M5-K036-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

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

## Official documentation and development resources

Use [RoverC-Pro](https://docs.m5stack.com/en/hat/RoverC-Pro) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K036-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need          | Model-specific reference                                                                                                                                                  |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K036-B_RoverC-Pro/Structures)                                                   |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K036-B_RoverC-Pro/Structures/RoverC-Pro_L_Part.stl)                             |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K036-B_RoverC-Pro/Structures/RoverC-Pro_Servo_Clamp_Support_Bracket.stl)        |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K036-B_RoverC-Pro/Structures/RoverC-Pro_Servo_Claw_B_Version_Left_Arm.stl)      |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K036-B_RoverC-Pro/Structures/RoverC-Pro_Servo_Claw_B_Version_Right_Arm.stl)     |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K036-B_RoverC-Pro/Structures/RoverC-Pro_Servo_Claw_B-Type_Front_Shell.stl)      |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K036-B_RoverC-Pro/Structures/RoverC-Pro_Servo_Kit_Building_Block_Pendant-A.stl) |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K036-B_RoverC-Pro/Structures/RoverC-Pro_Shell.stl)                              |
| Example source: M5-RoverC | [Read example source: m5-roverc](https://github.com/m5stack/M5-RoverC/tree/master/examples/RoverC_M5StickC/JoyC_%26_RoverC)                                               |
| Example source: M5-RoverC | [Read example source: m5-roverc](https://github.com/m5stack/M5-RoverC/tree/master/examples/RoverC_M5StickCPlus/JoyC_%26_RoverC)                                           |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
