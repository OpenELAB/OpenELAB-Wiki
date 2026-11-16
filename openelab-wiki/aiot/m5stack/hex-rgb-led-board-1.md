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

# HEX RGB LED Board

### HEX RGB LED Board

***

### Product Link

{% embed url="https://openelab.io/products/hex-rgb-led-board" %}

### Description <a href="#description" id="description"></a>

**HEX** is a hexagon RGB LED panel that integrates a total of 37 RGB LEDs. The HEX board includes an input port and an output port, you can have multiply of them in series connection.

### Features <a href="#features" id="features"></a>

* 37 integrated LEDs
* Software development platform: Arduino, UIFlow (Blockly & python)

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter    |
| ------------ | ------------ |
| RGB LED      | SK6812 x 37  |
| Net weight   | 8g           |
| Gross weight | 10g          |
| Product Size | 30\*35\*8mm  |
| Package Size | 50\*80\*10mm |

This is how LEDs layout in the panel, Pay attention to the sequence in your code:

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_05.webp" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

**If HEX connectors to GROVE A**

| M5Core(GROVE A) | GPIO22 | GPIO21   | 5V | GND |
| --------------- | ------ | -------- | -- | --- |
| HEX Unit In     |        | Data Pin | 5V | GND |

**If HEX connectors to GROVE B**

| M5Core(GROVE B) | GPIO36 | GPIO26   | 5V | GND |
| --------------- | ------ | -------- | -- | --- |
| HEX Unit In     |        | Data Pin | 5V | GND |

**If HEX connectors to GROVE C**

| M5Core(GROVE C) | GPIO16 | GPIO17   | 5V | GND |
| --------------- | ------ | -------- | -- | --- |
| HEX Unit In     |        | Data Pin | 5V | GND |

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_04.webp" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (369).png" alt=""><figcaption></figcaption></figure>
