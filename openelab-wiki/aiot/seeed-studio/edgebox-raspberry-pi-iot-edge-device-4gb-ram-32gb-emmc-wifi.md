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

# EdgeBox Raspberry Pi IoT Edge Device 4GB RAM 32GB eMMC WiFi

{% hint style="info" %}
[**View EdgeBox Raspberry Pi IoT Edge Device 4GB RAM 32GB eMMC WiFi on OpenELAB**](https://openelab.io/products/edgebox-raspberry-pi-iot-edge-device)

**Store SKU / option:** `240808002241`. Match the purchased model and revision to the official reference below.
{% endhint %}

### EdgeBox Raspberry Pi IoT Edge Device 4GB RAM 32GB eMMC WiFi

***

### Product Link

{% embed url="https://openelab.io/products/edgebox-raspberry-pi-iot-edge-device" %}

### Introduction

The EdgeBox-RPI-200 series controllers offer versatile solutions for enhancing edge automation and industrial control. Compact yet powerful, they support real-time operations and multi-process control for various industrial applications,serving as PLC, IIoT Gateway, OPC UA Server, and Industry PC.

For a detailed comparison and to find the best fit for your projects, you can check our [EdgeBox Series Comparision Table](https://docs.google.com/spreadsheets/d/1CnAFMLsuO8-6G7YmSglvGcRsvctRz9mj/edit#gid=882805391), or directly email us at edge@seeed.cc.

### Features

* **All-in-one IIoT Edge Gateway**

More than just a PLC, PAC, also an IoT edge Gateway, edge computing controller and Industry PC.

* **Powerful and Flexible Processors**

Powered by Raspberry Pi CM4, equipped up to 8GB RAM and 32GB eMMC

* **Multiple Communication Capabilities**

Support multiple industrial iot protocols and standards on phoenix connector and a RJ45 Gigabit Ethernet; Carry full-featured wireless interconnectivity with both cecullar and LoRa, supported by AWS, Azure cloud services

* **Rugged Industrial-grade Hardware Design**

Integrated thermal management with full Aluminum heatsink enclosure, supporting 35mm DIN rail and wall mounting

* **Supported with Rich Industrial Software Ecosystem**

Support rich industrial platforms and also fleet management, including Codesys, N3uron, balena, Node Red, Ignition and etc.

### Specifications

<table data-header-hidden><thead><tr><th width="349"></th><th></th></tr></thead><tbody><tr><td>Parameter</td><td>Description</td></tr><tr><td><strong>Basic</strong></td><td></td></tr><tr><td>CPU</td><td>Raspberry Pi CM4, Quad-core Cortex-A72@ 1.5GHz</td></tr><tr><td>RAM</td><td>1GB/2GB/4GB/8GB</td></tr><tr><td>eMMC</td><td>Lite/8GB/16GB/32GB</td></tr><tr><td>Operating System</td><td>Raspbian, Debian</td></tr><tr><td><strong>Wireless</strong></td><td></td></tr><tr><td>WiFi</td><td>2.4 GHz, 5.0 GHz IEEE 802.11 b/g/n/ac equipped*</td></tr><tr><td>Bluetooth</td><td>Bluetooth 5.0, BLE equipped*</td></tr><tr><td>Cellular</td><td>Mini-PCIe support 4G LTE(Quectel EC20/EC25 tested)*</td></tr><tr><td>LoRa®</td><td><a href="https://www.seeedstudio.com/WM1302-LoRaWAN-Gateway-Module-SPI-EU868-p-4889.html">Mini-PCIe support LoRaWAN®</a></td></tr><tr><td><strong>Interface</strong></td><td></td></tr><tr><td>Ethernet</td><td>1 x 1000M RJ45</td></tr><tr><td>HDMI</td><td>HDMI 2.0 up to 4k@60fps</td></tr><tr><td>USB</td><td>2 x USB2.0 A</td></tr><tr><td>RS Serial</td><td>1 x RS485 (isolated)</td></tr><tr><td>1 x RS232</td><td></td></tr><tr><td>M.2 socket</td><td>2242 NVME SSD card</td></tr><tr><td>DI</td><td>2 x isolated DI ports</td></tr><tr><td>Input Voltage: 24V DC; Current: 1000mA</td><td></td></tr><tr><td>DO</td><td>2 x isolated DO ports</td></tr><tr><td>Output voltage: &#x3C;60 V; Current: 500 mA</td><td></td></tr><tr><td><strong>Extra features</strong></td><td></td></tr><tr><td>Power Supply</td><td>DC 12V - 36V</td></tr><tr><td>RTC</td><td>RTC</td></tr><tr><td>Watchdog Timer</td><td>Stand alone</td></tr><tr><td>Encryption Chip</td><td>ATECC608A*</td></tr><tr><td>Uninterrupted Power Supply</td><td>UPS*</td></tr><tr><td>Operation temperature</td><td>-20 ~ 60 °C</td></tr><tr><td>Certification</td><td>RoHS, CE, FCC, TELEC, UKCA</td></tr></tbody></table>

### Pinout

<figure><img src="../../.gitbook/assets/image (884).png" alt=""><figcaption></figcaption></figure>

### Dimensions

124mm x 76mm x 35mm

### FAQ

<details>

<summary><strong>How can I get started with EdgeBox?</strong></summary>

Edgeboxes, pre-loaded with Debian Buster, can be powered up with HDMI and ethernet for first boot. Also you can access it remotely with SSH for initial configuration without a monitor. Once set up, switch to VNC for a graphical interface.

</details>

<details>

<summary><strong>What kinds of 4G and LoRa modules can I use?</strong></summary>

You can input Quectel EC20/EC25 module for 4G LTE usage.

You can use Seeed WM1302 module for LoRaWAN® applications.

</details>

<details>

<summary><strong>Can I use 4G and LoRa at the same time?</strong></summary>

Sorry, this box does not support 4G and LoRa® use at the same time.

</details>

<details>

<summary><strong>How to reflash OS?</strong></summary>

When you need to install your preferred OS, you will need some additional hardware to burn it. Remove the CM4 from the Edge box and place it on the [Dual Gigabit Ethernet Carrier Board](https://www.seeedstudio.com/Rapberry-Pi-CM4-Dual-GbE-Carrier-Board-p-4874.html) to burn your OS. Then, remount the CM4

</details>

<details>

<summary><strong>What are the software we can communicate with external world ?</strong></summary>

The Edge box is an open-source hardware solution for industries. It supports protocols such as RS485, RS282 Modbus, Ethernet/IP, TCP/IP, and wireless networks. Therefore, you can interact with the external world using third-party software such as Codesys, Node-RED, N3uron, and Ignition Edge, as well as cloud services like AWS and Azure.

Discover our range of edge devices powered by Raspberry Pi, including all-in-one edge computing controllers and versatile HMIs. They are open source and adaptable to your specific requirements. Explore the complete series of [Raspberry Pi-based edge devices](https://wiki.seeedstudio.com/raspberry-pi-devices/) today.

</details>

## Official documentation and development resources

Use [Getting Started Edge Box RPI-200](https://wiki.seeedstudio.com/Edge_Box_introduction/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/Edge_Box/EdgeBox_RPi_200_3D_file.stp) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
