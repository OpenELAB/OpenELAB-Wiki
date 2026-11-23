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

# M5Stack LAN Module

{% hint style="info" %}
[**View M5Stack LAN Module 13.2 on OpenELAB**](https://openelab.io/products/m5stack-lan-module)

**Store SKU / option:** `M5-M136`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack LAN Module 13.2

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-lan-module" %}

### Description <a href="#description" id="description"></a>

**LAN Module 13.2** is a powerful Ethernet controller module that integrates the W5500 hardware TCP/IP embedded Ethernet controller (via SPI communication interface). It supports multiple communication protocols and is suitable for various applications such as industrial automation, Internet of Things (IoT), data acquisition, and remote monitoring.

LAN Module 13.2 features the built-in **W5500** hardware TCP/IP embedded Ethernet controller, which supports TCP, UDP, IPv4, and other communication protocols to meet the requirements of different application scenarios. Additionally, the module integrates a storage buffer area to handle Ethernet data packets efficiently. Equipped with a signal-isolated gigabit transformer, LAN Module 13.2 converts the input signals from the RJ45 interface to the appropriate output signals, achieving electrical isolation and preventing electromagnetic interference. This enhances system stability and reliability.

LAN Module 13.2 supports a DC-JACK interface (9-24V) and a DC-DC buck circuit, simplifying power management and providing a reliable power supply for the entire device. The module includes a built-in jumper pin for chip selection, allowing two modules to be stacked simultaneously for dual Ethernet connectivity. It also provides a VH3.96 interface for easy integration of additional expansion devices, offering greater flexibility to meet specific application requirements.

In addition to its application as an Ethernet controller, LAN Module 13.2 can be widely used in various scenarios such as Ethernet-to-AP conversion, lightweight web server, and RS485-to-Ethernet data transmission unit (DTU). It enables diverse data transfer and interconnection, providing flexible solutions for users.

### Features <a href="#features" id="features"></a>

* Signal isolation: built-in 100 megabit transformer to achieve signal isolation.
* Power supply: 9-24V DC-JACK interface and DC-DC Buck circuit are provided.
* Expansibility: Reserved VH3.96 port, allowing users to add expansion devices.
* Support a variety of protocols: built-in W5500 full hardware TCP/IP embedded Ethernet controller, protocol support, including TCP, UDP, IPv4 and so on.

### Applications <a href="#applications" id="applications"></a>

* Industrial Automation
* IoT
* Network communication equipment
* Data acquisition and remote monitoring

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                     | Parameters                         |
| ----------------------------- | ---------------------------------- |
| Ethernet Controller           | W5500                              |
| Network Interface             | RJ45 Adaptive 10/100M network port |
| External power supply voltage | 9-24V                              |
| Operating temperature         | 0-40°C                             |
| Communication Mode            | SPI                                |
| Product Size                  | 54\*54\*13.2mm                     |
| Package Size                  | 132\*95\*21mm                      |
| Product Weight                | 29.6g                              |
| Package Weight                | 40.7g                              |

### Related Link <a href="#related-link" id="related-link"></a>

* [Datasheet - W5500](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/base/W5500_datasheet_v1.0.2_1_en.pdf)

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/LAN%20Module%2013.2/img-5f5a8003-626f-4c29-88ce-e080b67a65b0.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/LAN%20Module%2013.2/pinMap-09a7a2e4-0811-45d2-b4ae-970afd8ce97e.png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Module13.2 LAN](https://docs.m5stack.com/en/module/Module13.2_LAN) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`M136`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                  | Model-specific reference                                                                                            |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic              | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/562/Sch_Module13.2_LAN.pdf)            |
| Example source: M5Module-LAN-13.2 | [Read example source: m5module-lan-13.2](https://github.com/m5stack/M5Module-LAN-13.2/tree/main/examples/HTTP)      |
| Example source: M5Module-LAN-13.2 | [Read example source: m5module-lan-13.2](https://github.com/m5stack/M5Module-LAN-13.2/tree/main/examples/MQTT)      |
| Example source: M5Module-LAN-13.2 | [Read example source: m5module-lan-13.2](https://github.com/m5stack/M5Module-LAN-13.2/tree/main/examples/WebServer) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
