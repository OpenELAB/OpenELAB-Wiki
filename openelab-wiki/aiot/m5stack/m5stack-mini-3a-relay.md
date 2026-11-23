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

# M5Stack Mini 3A Relay

{% hint style="info" %}
[**View M5Stack Mini 3A Relay Unit on OpenELAB**](https://openelab.io/products/mini-3a-relay-unit)

**Store SKU / option:** `M5-U023`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Mini 3A Relay

***

### Product Link

{% embed url="https://openelab.io/products/mini-3a-relay-unit" %}

### Description <a href="#description" id="description"></a>

**RELAY** as it says is an M5Unit that implement a Relay functions. Relay can be used as an electrically operated switch, uses an electromagnet to mechanically operate a switch, where it is necessary to control a large power load circuit by a separate low-power signal such as digital signal output from a microprocessor.

The Relay support input voltage of up to 30V DC and 220V AC.

There are 3 pins named: ON, OFF, COM. You can program to make COM connect to ON or OFF, just by high and low out put of a digital GPIO.

### Features <a href="#features" id="features"></a>

* Single-BUS control
* Up to 3A @ 30 V DC or 220 V AC
* Software Development Platform: Arduino, UIFlow (Blockly, Python)
* Two Lego-compatible holes

### Applications <a href="#applications" id="applications"></a>

* Remote control of high-power appliances, such as refrigerators, air conditioners, TVs, etc.

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                      | Parameter    |
| ------------------------------ | ------------ |
| Single relay power consumption | 5V@40mA      |
| Coil operating time            | 6ms          |
| Coil release time              | 4ms          |
| Net weight                     | 12g          |
| Gross weight                   | 26g          |
| Product Size                   | 48\*24\*21mm |
| Package Size                   | 60\*57\*17mm |

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE B) | GPIO36 | GPIO26                | 5V | GND |
| --------------- | ------ | --------------------- | -- | --- |
| RELAY Unit      |        | RELAY Controlling Pin | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/relay/relay_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (380).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Relay](https://docs.m5stack.com/en/unit/Unit_Relay) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U023`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                             |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U023_Unit_Relay/Structures)                |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U023_Unit_Relay/Structures/Unit_Relay.stl) |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_relay)                                    |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
