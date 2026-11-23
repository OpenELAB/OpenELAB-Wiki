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

# M5Stack ATOMIC PoE Base W5500

{% hint style="info" %}
[**View M5Stack ATOMIC PoE Base W5500 Ethernet Controller Driver Chip on OpenELAB**](https://openelab.io/products/atomic-poe-base-w5500)

**Store SKU / option:** `M5-A091`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack ATOMIC PoE Base W5500

***

### Product Link

{% embed url="https://openelab.io/products/atomic-poe-base-w5500" %}

### Introduction

**Atomic PoE Base** is an Ethernet controller base specifically designed for the ATOM series main controller. It is equipped with an Ethernet (PoE) module, allowing it to receive power directly from a PoE hub or switch. This eliminates the need for a separate power supply, reducing infrastructure costs and simplifying setup.

The base features the embedded W5500 Ethernet controller, which integrates the TCP/IP protocol stack. This controller provides 8 independent hardware sockets, allowing for simultaneous communication with multiple devices or services. The Ethernet data link layer (MAC) and physical layer (PHY) support 10/100M Ethernet, ensuring reliable and fast network connectivity.

With its capabilities, Atomic PoE Base offers a convenient internet connectivity solution for embedded systems. It meets the wired network access requirements in practical production environments, making it suitable for a wide range of applications.

<figure><img src="../../.gitbook/assets/image (542).png" alt=""><figcaption></figcaption></figure>

### Features

* Applicable to Atom Lite/Atom Matrix/AtomS3/AtomS3 Lite
* Supports PoE IEEE802.3 AF
* Wired Ethernet Access
* 8 independent hardware sockets
* Supports TCP、UDP、ICMP、IPv4、ARP、IGMP、PPPoE
* Integrated 10BaseT / 100Base-T Ethernet PHY

### Specifications

| Resources             | Parameters                                                       |
| --------------------- | ---------------------------------------------------------------- |
| Ethernet Chip         | W5500                                                            |
| Supported Protocols   | TCP、UDP、ICMP、IPv4、ARP、IGMP、PPPoE                                 |
| PoE Power Supply      | Idle pin power supply(10M/100M Ethernet),J4\&J5(VC-),J7\&J8(VC+) |
| PoE Spec              | IEEE802.3 AF                                                     |
| Operating temperature | 0-40°C                                                           |
| Product Size          | 64\*18\*18mm                                                     |
| Package Size          | 136\*92\*20mm                                                    |
| Product Weight        | 17g                                                              |
| Package Weight        | 20.5g                                                            |

### Pinout

<figure><img src="../../.gitbook/assets/image (539).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (541).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Connection**: Connect the ATOMIC PoE Base to your M5Stack core using the M-Bus interface.
* **Ethernet Cable**: Plug an Ethernet cable into the RJ45 port of the ATOMIC PoE Base.
* **PoE Switch/Injector**: Connect the other end of the Ethernet cable to a PoE switch or injector.
* **Library Installation**: Install the necessary libraries for Ethernet communication, such as `Ethernet2` for Arduino.
* **Initialization**: Initialize the Ethernet controller in your code using the appropriate library functions.
* **Data Transmission**: Use the library functions to send and receive data over the Ethernet connection.

### FAQ

<details>

<summary>What applications can the ATOMIC PoE Base be used for?</summary>

The ATOMIC PoE Base is ideal for IoT applications, smart home systems, industrial automation, and any project requiring stable Ethernet connectivity and centralized power management.

</details>

<details>

<summary>How do I connect the ATOMIC PoE Base to my M5Stack core?</summary>

Use the M-Bus interface to connect the ATOMIC PoE Base to the M5Stack core.

</details>

<details>

<summary>Can I use the ATOMIC PoE Base with a non-PoE Ethernet connection?</summary>

Yes, but you will need to supply power to the M5Stack core separately since PoE will not be available.

</details>

<details>

<summary>What is the data transfer rate supported by the ATOMIC PoE Base?</summary>

The ATOMIC PoE Base supports 10/100 Mbps data transfer rates.

</details>

<details>

<summary>How do I install the necessary libraries?</summary>

Use the Arduino Library Manager to install the `Ethernet2` library or other compatible Ethernet libraries for your project.

</details>

## Official documentation and development resources

Use [Atomic PoE Base](https://docs.m5stack.com/en/atom/Atomic_PoE_Base) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`A091`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/465/Sch_AtomicPoE_v1.2.pdf)                |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/atomic/atomic_poe_base)                |
| Example source: M5Atom       | [Read example source: m5atom](https://github.com/m5stack/M5Atom/tree/master/examples/ATOM_BASE/ATOM_PoE)                |
| Example source: M5AtomS3     | [Read example source: m5atoms3](https://github.com/m5stack/M5AtomS3/tree/main/examples/AtomicBase/AtomicPoE/HTTP)       |
| Example source: M5AtomS3     | [Read example source: m5atoms3](https://github.com/m5stack/M5AtomS3/tree/main/examples/AtomicBase/AtomicPoE/LinkStatus) |
| Example source: M5AtomS3     | [Read example source: m5atoms3](https://github.com/m5stack/M5AtomS3/tree/main/examples/AtomicBase/AtomicPoE/MQTT)       |
| Example source: M5AtomS3     | [Read example source: m5atoms3](https://github.com/m5stack/M5AtomS3/tree/main/examples/AtomicBase/AtomicPoE/WebServer)  |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
