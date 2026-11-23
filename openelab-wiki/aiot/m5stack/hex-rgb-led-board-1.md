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

{% hint style="info" %}
[**View HEX RGB LED Board on OpenELAB**](https://openelab.io/products/hex-rgb-led-board)

**Store SKU / option:** `M5-A045`. Match the purchased model and revision to the official reference below.
{% endhint %}

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

## Official documentation and development resources

Use [Unit HEX](https://docs.m5stack.com/en/unit/Unit_HEX) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`A045`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                        |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_hex) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
