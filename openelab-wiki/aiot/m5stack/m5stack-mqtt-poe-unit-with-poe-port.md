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

# M5Stack MQTT PoE Unit with PoE Port&#x20;

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
