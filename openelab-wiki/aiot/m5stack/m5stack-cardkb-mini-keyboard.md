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

{% hint style="info" %}
[**View M5Stack CardKB v1.1 I2C Mini Keyboard Unit (ATMega8A) on OpenELAB**](https://openelab.io/products/m5stack-cardkb-keyboard)

**Store SKU / option:** `M5-U035-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack CardKB Mini Keyboard Programmable Unit V1.1

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-cardkb-keyboard" %}

### Description <a href="#description" id="description"></a>

**CardKB v1.1** is a card-size '50 key' QWERTY keyboard. Adpots `ATMega8A` as the MCU, communication port `I2C`, and one 'RGB-LED' indicator.

### Features <a href="#features" id="features"></a>

* Full-function keyboard, multi-key combination
* GROVE interface, support UIFlow and Arduino
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
* **Fn+key(custom function key combination)**, keyboard will output the third key value. You can customize what function the key presses corresponds to.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/cardkb/cardkb_02.webp" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

**ATMega8A ISP**Download interface Pin foot definition

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat-cardkb/mega328_isp_sch_01.webp" alt=""><figcaption></figcaption></figure>

| M5Core(GROVE A) | GPIO22 | GPIO21 | 5V | GND |
| --------------- | ------ | ------ | -- | --- |
| CardKB          | SCL    | SDA    | 5V | GND |

### Protocol <a href="#protocol" id="protocol"></a>

* Protocol type I2C
* I2C Address: **0x5F**

### **Compatible**

<figure><img src="../../.gitbook/assets/image (386).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit CardKB v1.1](https://docs.m5stack.com/en/unit/Unit_CardKB_v1.1) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U035-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                            |
| ----------------------- | --------------------------------------------------------------------------------------------------- |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/CardKB) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
