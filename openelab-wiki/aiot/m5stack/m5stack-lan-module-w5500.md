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

# M5Stack LAN Module W5500

### M5Stack LAN Module W5500 with PoE V12

***

### Product Link

{% embed url="https://openelab.io/products/lan-module-w5500" %}

### Description <a href="#description" id="description"></a>

**LAN PoE BASE V12** is an `Ethernet control module` that integrates `PoE` (Power Over Ethernet) function. Adopt `W5500` full hardware TCP/IP embedded Ethernet controller (SPI communication interface) scheme, support multiple communication protocols (TCP, UDP, IPv4, ICMP, ARP, IGMP and PPPoE, etc.) Network packet processing.

Internally reserved expansion pads can be used to expand `RS485`/`RS232`/`CAN` communication adapter modules or add custom designs, support PoE power supply and standard rail fixing accessories, no need for additional power supply wires and structural design. It can be easily deployed on industrial sites. With both performance and expansion flexibility, `LAN PoE BASE V12` can provide you with a more compact embedded Ethernet connection solution.

### Features <a href="#features" id="features"></a>

* W5500:
  * Support 8 independent hardware sockets for simultaneous communication
  * Support TCP, UDP, ICMP, IPv4, ARP, IGMP, PPPoE protocols
  * Integrated 10BaseT / 100Base-T Ethernet PHY
* Wired Ethernet access
  * RJ45 adaptive 10/100M network port
* Power input method:
  * Support PoE IEEE802.3 AF / Voltage DC 37-57V
  * Support input power voltage: 9-24V
  * Support MBUS 5V power supply (when used with M5CORE)
* Slide rail or magnetic fixation
* RS485/RS232/CAN communication expansion board

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications            | Parameters                                                                                                                                                                                                                                              |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| W5500 Ethernet Controller | <p>Supports Hardwired TCP/IP Protocols : TCP, UDP, ICMP, IPv4, ARP, IGMP, PPPoE<br>Supports 8 independent sockets simultaneously<br>Supports High Speed ​​Serial Peripheral Interface(SPI MODE 0, 3 )<br>Internal 32Kbytes Memory for TX/RX Buffers</p> |
| RS485-To-TTL              | SP485EEN-L/TR                                                                                                                                                                                                                                           |
| RS232-To-TTL              | MAX232ESE                                                                                                                                                                                                                                               |
| CAN-To-TTL                | CA-IS3050G                                                                                                                                                                                                                                              |
| Ethernet port             | RJ45 adaptive 10/100M Ethernet port                                                                                                                                                                                                                     |

### Applications <a href="#applications" id="applications"></a>

* M5Core + LAN implements the belt controller

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/base/lan_base/lan_base_07.webp" alt=""><figcaption></figcaption></figure>

* Cable transmission of video data between PC and Core

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/base/lan_base/lan_base_08.webp" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

* W5500 Ethernet chip

| W5500 | ESP32 Chip |
| ----- | ---------- |
| MOSI  | GPIO23     |
| MISO  | GPIO19     |
| CLK   | GPIO18     |
| CS    | GPIO26     |
| RST   | GPIO13     |
| INTn  | GPIO34     |

* RS485/RS232/CAN adapter board

| ESP32 Chip | RS485/RS232 |
| ---------- | ----------- |
| RX         | GPIO5       |
| TX         | GPIO15      |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="../../.gitbook/assets/image (374).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (375).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (376).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (377).png" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/base/lan_poe_v12/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Expanded board welding position <a href="#expanded-board-welding-position" id="expanded-board-welding-position"></a>

LAN BASE V12 comes standard with two adapter boards, TTL-RS485 + TTL-RS232, which are used to adapt to different communication interfaces. The welding positions are as follows. Please refer to the pin mapping table for the actual connection to GPIO.

* **RS232** adapter board welding position or **RS485** adapter board welding position

<div><img src="https://static-cdn.m5stack.com/resource/docs/products/base/lan_v12/lan_v12_07.webp" alt="" width="70%"> <img src="https://static-cdn.m5stack.com/resource/docs/products/base/lan_v12/lan_v12_08.webp" alt="" width="70%"></div>

### Related Link <a href="#related-link" id="related-link"></a>

* **Datasheet** - [W5500](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/base/W5500_datasheet_v1.0.2_1_en.pdf)
