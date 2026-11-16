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

# M5Stack CardKB Mini Keyboard

### M5Stack CardKB Mini Keyboard Programmable Unit V1.1 (MEGA8A)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-cardkb-keyboard" %}

### Description <a href="#description" id="description"></a>

**CardKB v1.1** is a card-size '50 key' QWERTY keyboard. Adpots `ATMega8A` as the MCU, communication port `I2C`, and one 'RGB-LED' indicator.

### Features <a href="#features" id="features"></a>

* Full-function keyboard, multi-key combination
* GROVE interface, support [UIFlow ](http://flow.m5stack.com/)and [Arduino](http://www.arduino.cc/)
* Two Lego compatible holes

### Applications <a href="#applications" id="applications"></a>

* Keyboard peripherals for M5Stack Core

### Specifications <a href="#specifications" id="specifications"></a>

| Resources            | Parameter    |
| -------------------- | ------------ |
| MCU                  | ATMega8A     |
| Number of keys       | 50           |
| RGB LED              | 1 piece      |
| Communication method | I2C          |
| Net weight           | 17g          |
| Gross weight         | 18g          |
| Product Size         | 88\*54\*5mm  |
| Package Size         | 136\*92\*5mm |

### Docs <a href="#docs" id="docs"></a>

* **Single button pressed**, keyboard will output the first key value (the letter button will output in a lower case form). E.g if "Q" was pressed, keyboard will output "q" (lower cased).
* **Sym+key**, keyboard will output the second key value. E.g if "Sym" was pressed and then "Q" was pressed, the keyboard will output "{". If "Sym" was double pressed, then the keyboard will lock this function, all key pressed will output it's second key value.
* **Shift+key**, if a letter button was pressed, it'll output upper case form. E.g if "Shift" was pressed and then "Q" was pressed, the keyboard will output "Q". If "Shift" was double pressed, then the keyboard will lock this function, all letter key pressed will output it's upper case form.
* **Fn+key(custom function key combination)**, keyboard will output the third key value. You can customize what function the key presses corresponds to.&#x20;

<figure><img src="../../.gitbook/assets/image (974).png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

**ATMega8A ISP**Download interface Pin foot definition

<figure><img src="../../.gitbook/assets/image (975).png" alt=""><figcaption></figcaption></figure>

| M5Core(GROVE A) | GPIO22 | GPIO21 | 5V | GND |
| --------------- | ------ | ------ | -- | --- |
| CardKB          | SCL    | SDA    | 5V | GND |

### Protocol <a href="#protocol" id="protocol"></a>

* Protocol type I2C
* I2C Address: **0x5F**

```cpp
/*--------------------------------------------------------------------------------------------------*/
| KEYBOARD REG       | 0x5F
| ------------------------------------------------------------------------------------------------
| keyboard_value_reg[0] 0x5F        |  R |  KEYBOARD VALUE
/*----------------------------------------------------------------------------------------------------
```

### Compatible <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (976).png" alt=""><figcaption></figcaption></figure>
