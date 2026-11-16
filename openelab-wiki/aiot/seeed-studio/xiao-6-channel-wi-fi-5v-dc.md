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

# XIAO 6-Channel Wi-Fi 5V DC

### Seeed Studio XIAO 6-Channel Wi-Fi 5V DC Relay

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-6-channel-wifi-5v-dc-relay" %}

### Description

The **6-Channel Wi-Fi Relay Module** is a smart device from Seeed Studio designed for control within a safe DC voltage range, not for AC-powered appliances. Its six-channel configuration supports independent control of up to six loads, making it an excellent choice for automating a variety of devices in smart home environments.

In addition to its six relay channels, this module also features two extra Grove expansion interfaces, allowing users to integrate additional sensors or actuators for more advanced automation scenarios.

This guide provides a detailed walkthrough, including setup, integration, and advanced configuration for users ranging from beginners to smart-home enthusiasts.

### Key Features and Specifications[​](https://wiki.seeedstudio.com/6_channel_wifi_relay/#key-features-and-specifications) <a href="#key-features-and-specifications" id="key-features-and-specifications"></a>

| Feature              | Details                                                |
| -------------------- | ------------------------------------------------------ |
| Input Voltage        | DC 5V(For XIAO)                                        |
| DC withstand voltage | DC 0\~30V                                              |
| Maximum Load         | 10A per channel                                        |
| Channels             | 6 (independent control for each channel)               |
| Connection Type      | Wi-Fi                                                  |
| Electrical port      | NO (Normally Open), COM (Common), NC (Normally Closed) |
| Grove extension      | IIC×1, UART×1                                          |

**Safety Warning:**

This relay module is designed for low-voltage DC operation. Do not connect it to AC power to avoid electrical hazards. Always disconnect the power supply before wiring the relay to prevent short circuits and electric shock.

Voltages exceeding 24V may cause electric shock or burns, especially in cases of broken skin or in moist environments. Exercise caution when handling electrical devices to avoid injury.

### Physical Layout and Connections[​](https://wiki.seeedstudio.com/6_channel_wifi_relay/#physical-layout-and-connections) <a href="#physical-layout-and-connections" id="physical-layout-and-connections"></a>

![](https://files.seeedstudio.com/wiki/XIAO/Gadgets/6_channel_wifi_relay/simplified_diagram_with_con.png)

* **NO (Normally Open)**: The normally open terminal. By default, this terminal is not connected to the common terminal (COM). When the relay is activated, the NO terminal connects to the COM terminal. It is typically used to control a load's switch.
* **COM (Common)**: The common terminal of the relay, shared as a connection point to one side of the circuit.
*   **NC (Normally Closed)**: The normally closed terminal. By default, this terminal is connected to the common terminal (COM). When the relay is activated, the connection between the NC terminal and the COM terminal is broken. It is typically used for scenarios requiring disconnection control.

    | XIAO GPIO | Relay Channel |
    | --------- | ------------- |
    | GPIO2     | Relay 1       |
    | GPIO21    | Relay 2       |
    | GPIO1     | Relay 3       |
    | GPIO0     | Relay 4       |
    | GPIO19    | Relay 5       |
    | GPIO18    | Relay 6       |
