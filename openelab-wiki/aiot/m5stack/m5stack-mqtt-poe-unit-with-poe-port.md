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

# M5Stack MQTT PoE Unit with PoE Port

{% hint style="info" %}
[**View M5Stack MQTT PoE Unit with PoE Port on OpenELAB**](https://openelab.io/products/m5stack-mqtt-poe-unit)

**Store SKU / option:** `M5-U129-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack MQTT PoE Unit with PoE Port

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-mqtt-poe-unit" %}

### Introduction

UNIT MQTT PoE is an Ethernet MQTT communication module, supports PoE power and embedded W5500 Ethernet chip, as well as the UART communication interface (AT command control). The module is also equipped with an integrated RJ45 10 / 100 Mb network port, supports subscription of four topics (topic). With extremely low network latency and high stability, it is designed for industrial automation, security monitoring system, automation measurement, and equipment data on the cloud applications.

<figure><img src="../../.gitbook/assets/image (474).png" alt=""><figcaption></figcaption></figure>

### Features

* Embedded W5500 Ethernet chip
* RJ45 network port 10/100Mbps
* PoE power supply: 1.2A@5V(6W)
* Ethernet MQTT communication
* Support 4x Topic subscription
* Low latency
* Development method.
  * AT command, UART: 9600bps, default
  * Development Platform: UIFlow, Arduino

### Specifications

| Specifications              | Parameters                                       |
| --------------------------- | ------------------------------------------------ |
| Module Processor            | ARM Cortex-M3                                    |
| Communication interface     | UART: baud 9600bps 8N1 default                   |
| MQTT                        | Support 4x Topic subscription, not support MQTTS |
| Network port                | RJ45 adaptive 10/100M network port               |
| Delay                       | Delay \`10ms                                     |
| PoE power supply capability | 1.2A@5V(6W) / Voltage DC 37-57V                  |
| Working current             | 190mA                                            |
| Standby current             | 130mA                                            |
| Net weight                  | 27.0g                                            |
| Gross weight                | 34.2g                                            |
| Product size                | 72 \* 26 \* 19 mm                                |
| Packing size                | 73 \* 35 \* 20 mm                                |

### Pinout

| M5Core    | TX(GPIO17) | RX(GPIO16) | VCC | GND |
| --------- | ---------- | ---------- | --- | --- |
| UNIT MQTT | RX         | TX         | VCC | GND |

<figure><img src="../../.gitbook/assets/image (467).png" alt=""><figcaption></figcaption></figure>

### Dimensions

size:27.0g

weight:72 \* 26 \* 19 mm

### How to Use

#### Arduino <a href="#arduino" id="arduino"></a>

* [MQTT TEST](https://github.com/m5stack/UNIT_MQTT)

## Official documentation and development resources

Use [Unit MQTT-PoE](https://docs.m5stack.com/en/unit/Unit_MQTT-PoE) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U129-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need            | Model-specific reference                                                 |
| --------------------------- | ------------------------------------------------------------------------ |
| Official source: UNIT\_MQTT | [Read official source: unit\_mqtt](https://github.com/m5stack/UNIT_MQTT) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
