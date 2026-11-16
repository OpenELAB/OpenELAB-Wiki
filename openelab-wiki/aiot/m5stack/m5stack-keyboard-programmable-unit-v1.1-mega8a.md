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

# M5Stack Keyboard Programmable Unit V1.1 (MEGA8A)

### M5Stack Keyboard Programmable Unit V1.1 (MEGA8A)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-cardkb-keyboard" %}

### Introduction

**CardKB v1.1** is a card-size '50 key' QWERTY keyboard. Adpots `ATMega8A` as the MCU, communication port `I2C`, and one 'RGB-LED' indicator.

<figure><img src="../../.gitbook/assets/image (486).png" alt=""><figcaption></figcaption></figure>

### Features

* Full-function keyboard, multi-key combination
* GROVE interface, support [UIFlow ](http://flow.m5stack.com/)and [Arduino](http://www.arduino.cc/)
* Two Lego compatible holes

### Specifications

| Resources            | Parameter |
| -------------------- | --------- |
| MCU                  | ATMega8A  |
| Number of keys       | 50        |
| RGB LED              | 1 piece   |
| Communication method | I2C       |
| Net weight           | 17g       |
| Gross weight         | 18g       |

### Pinout

**ATMega8A ISP**Download interface Pin foot definition

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat-cardkb/mega328_isp_sch_01.webp" alt="" width="375"><figcaption></figcaption></figure>

| M5Core(GROVE A) | GPIO22 | GPIO21 | 5V | GND |
| --------------- | ------ | ------ | -- | --- |
| CardKB          | SCL    | SDA    | 5V | GND |

### Dimensions

| Product Size | 88\*54\*5mm  |
| ------------ | ------------ |
| Package Size | 136\*92\*5mm |

### How to Use

#### Arduino <a href="#arduino" id="arduino"></a>

To get the code, please click [here](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/CardKB)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/cardkb/cardkb_arduino_01.webp" alt="" width="563"><figcaption></figcaption></figure>

#### UIFlow <a href="#uiflow" id="uiflow"></a>

**Feature Introduction**

Enter information via the keyboard

* **Get key** Return ASIIC value
* **Get string** Return character
* **Get pressed** Detect button, press to return true

**Usage**

To get the complete code, please click [here](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/CARDKB/UIFlow)

<figure><img src="../../.gitbook/assets/image (487).png" alt="" width="563"><figcaption></figcaption></figure>
