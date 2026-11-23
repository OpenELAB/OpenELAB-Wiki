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

# M5Stack JoyC Omni-directional Controller

{% hint style="info" %}
[**View M5Stack JoyC (W/O M5StickC) Omni-directional Controller on OpenELAB**](https://openelab.io/products/m5stack-joyc-controller)

**Store SKU / option:** `M5-U079`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack JoyC (W/O M5StickC) Omni-directional Controller

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-joyc-controller" %}

### Description <a href="#description" id="description"></a>

**JoyC** is a rocker module designed for the M5StickC.It supports two-hand operation. Embedded STM32F030F4 main control chip, using I2C communication protocol and host M5StickC for data transmission. The range of the joystick is 0\~200, there are 12 RGB LEDs under the left and right joysticks, and the bottom of the joystick is equipped with a 16340/18350 battery base for continuous battery life.

### Features <a href="#features" id="features"></a>

* STM32F030F4 inside
* communication protocol: I2C (address: 0x38)
* support omni-directional movement/button press

### Applications <a href="#applications" id="applications"></a>

* Game Handle
* Wireless Joystick Device

### Specifications <a href="#specifications" id="specifications"></a>

| Resources              | Parameter     |
| ---------------------- | ------------- |
| Communication protocol | I2C:0x38      |
| Net weight             | 81g           |
| Gross weight           | 117g          |
| Product Size           | 200\*55\*50mm |
| Package Size           | 119\*89\*65mm |

### Protocol <a href="#protocol" id="protocol"></a>

* Protocol type I2C
* I2C Address: **0x38**

[RoverC-Pro User Manual](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/hat/hat-joyc/U079_I2C_PROTOCOL_EN.pdf)

## Official documentation and development resources

Use [Hat JoyC](https://docs.m5stack.com/en/hat/Hat_JoyC) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U079`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                    |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Hat/JoyC/Arduino/JoyC)    |
| Example source: M5-RoverC    | [Read example source: m5-roverc](https://github.com/m5stack/M5-RoverC/tree/master/examples/RoverC_M5StickC/JoyC_%26_RoverC) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
