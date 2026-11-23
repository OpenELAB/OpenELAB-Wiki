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

# M5Stack ATOM TailBat - Battery Accessory for ATOM

{% hint style="info" %}
[**View M5Stack ATOM TailBat - Battery Accessory for ATOM on OpenELAB**](https://openelab.io/products/m5stack-atom-tailbat)

**Store SKU / option:** `M5-T001`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack ATOM TailBat - Battery Accessory for ATOM

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-atom-tailbat" %}

### Introduction

**TailBat** is an external battery accessory designed for ATOM. It can be inserted into the tail of ATOM to provide power, making it convenient for users in mobile scenarios. The front of TailBat features a power switch button. It contains a 190mAh battery controlled by the power management chip IP5303. When the power is turned on, a red indicator light illuminates.\
The usage method is similar to that of the M5Stack Core: a single click to turn on the power and a double click to turn off the power. During charging, the indicator light flashes, and once fully charged, the indicator light remains on.

<figure><img src="../../.gitbook/assets/image (634).png" alt=""><figcaption></figcaption></figure>

TailBat is designed with a pass-through interface, which means it doesn't interfere with the original wiring and interface functionality since it adds a battery. The built-in battery can only be charged through the Type-C interface and cannot be charged through the GROVE interface.

### Features

* Adapted for ATOM Matrix/ATOM Lite form factor
* Plug and play
* Built in rechargeable lithium battery
* LED indicator
* M5Stick/M5StickC/M5StickV/M5Camera compatible

### Specification <a href="#specification" id="specification"></a>

| Specification    | Parameter      |
| ---------------- | -------------- |
| External port    | 1x GROVE       |
| LED              | 1x RED LED     |
| USB port         | TypeC          |
| Battery capacity | 190mAh         |
| Net weight       | 10g            |
| Gross weight     | 10g            |
| Product Size     | 55\*22\*14mm   |
| Package Size     | 75\*22\*14mm   |
| Case material    | Plastic ( PC ) |

### Pinout

<figure><img src="../../.gitbook/assets/image (635).png" alt=""><figcaption></figcaption></figure>

### How to Use

<figure><img src="../../.gitbook/assets/image (636).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Tail Bat](https://docs.m5stack.com/en/atom/Tail_Bat) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`T001`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
