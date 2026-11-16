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

# M5Stack I/O Hub 1 to 6 Expansion Unit (STM32F0)

### M5Stack I/O Hub 1 to 6 Expansion Unit (STM32F0)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-i-o-hub" %}

### Introduction

**PbHUB Unit** is a 6-channel expansion Unit with I2C control. Each Port B interface is capable of GPIO, PWM, Servo control, ADC sampling, RGB light control and other functions. Adopts STM32F030 for internal control.

<figure><img src="../../.gitbook/assets/image (484).png" alt=""><figcaption></figcaption></figure>

### Features

* 6 x GPIO Ports Expansion
* 1 x I2C Input
* Internal STM32F030 control
* 2 x Brick holes

### Specifications

| Spec                   | Parameter                      |
| ---------------------- | ------------------------------ |
| Communication protocol | I2C:0x61(Modified by register) |
| Net weight             | 6.7g                           |
| Gross weight           | 11.8g                          |

### Pinout

<figure><img src="../../.gitbook/assets/image (485).png" alt=""><figcaption></figcaption></figure>

### Dimensions

| Product Size | 48\*24\*12mm    |
| ------------ | --------------- |
| Package Size | 13.6\*9.1\*12mm |

### How to Use

#### UIFlow <a href="#uiflow" id="uiflow"></a>

**Feature Introduction**

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pbhub_1.1/pbhub_1.1_uiflow_01.webp" alt="" width="375"><figcaption></figcaption></figure>

* **Servo CH IO angle** Set rotation angle of the servo
* **Servo CH IO pulse** Write digital values to IOs
* **read status** Read firmware version/I2C address
* **init I2C address** Initialize I2C address
* **set I2C address** Set I2C address

#### Example <a href="#example" id="example"></a>

* Case study: Controlling repeated rotation of the servo
* Communication protocols: I2C
* I2C address: 0x61

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pbhub_1.1/pbhub_1.1_uiflow_02.webp" alt="" width="375"><figcaption></figcaption></figure>

#### Arduino <a href="#arduino" id="arduino"></a>

* [analog\_read](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/analog_read)
* [digital\_write\_read](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/digital_write_read)
* [pwm](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/pwm)
*   [rgb\_led](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/rgb_led)

    Here, the RGB driver can only be WS2812, not sk6812.
* [servo](https://github.com/m5stack/M5Unit-PbHub/tree/main/examples/servo)
