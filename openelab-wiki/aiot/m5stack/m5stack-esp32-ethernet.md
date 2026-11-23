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

# M5Stack ESP32 Ethernet

{% hint style="info" %}
[**View M5Stack ESP32 Ethernet Unit with PoE on OpenELAB**](https://openelab.io/products/esp32-ethernet-unit)

**Store SKU / option:** `M5-U138`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack ESP32 Ethernet Unit with PoE

***

### Product Link

{% embed url="https://openelab.io/products/esp32-ethernet-unit" %}

### Description <a href="#description" id="description"></a>

**PoESP32 Unit** is an ESP32 lan Ethernet Unit supports PoE (Power Over Ethernet). This module adopts ESP32 as built-in MCU, and IP101G as physical layer transceiver. Default firmware with `ESP-AT`, supports TCP,MQTT, HTTP protocols. It can connect to server with simple AT commands through serial port, achieving data transmission and remote control functions. This module simplify wiring and saves labor cost with PoE power supply, and It reserves the ability for secondary development to meet your requirement.

### Features <a href="#features" id="features"></a>

* Embedded ESP32 main controller
* PHY solution:
  * Transceiver model IP101G
  * IEEE 802.3/802.3u standard
* Ethernet Interface.
  * PoE standard: PoE IEEE802.3 AF / Support maximum load power 6W
  * RJ45 network port 10/100Mbps
* Communication / download interface:
  * Default firmware is ESP-AT / Support secondary development to implement TCP Client/HTTP/CoAP and other protocols
  * Programmable / support secondary development, reserve program download interface
* Power supply.
  * HY2.0-4P interface 5V DC power supply
  * PoE power supply (PoE IEEE802.3 AF)
* Development method.
  * AT command, UART: 9600bps default
  * Development Platform: UIFlow(coming soon), Arduino, ESP-IDF

### Applications <a href="#applications" id="applications"></a>

* Ethernet Controller
* TCP Client data passthrough

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications                    | Parameters                                                                                                       |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| ESP32-WROOM-32U                   | 240MHz dual core, 600 DMIPS, 520KB SRAM (without integrated 3D antenna, does not support WiFi wireless function) |
| Flash                             | 4MB                                                                                                              |
| PHY                               | IP101G: IEEE 802.3/802.3u                                                                                        |
| MAC-PHY Interface Type            | RMII                                                                                                             |
| PoE Specifications                | PoE IEEE802.3 AF Specifications / Maximum Power 6W / Voltage DC 37-57V                                           |
| Ethernet Interface Specifications | RJ45 10/100Mbps                                                                                                  |
| Reserved interface                | 1x HY2.0-4P interface, 1x program download interface                                                             |
| Communication interface           | UART 9600bps 8N1 AT command control                                                                              |
| Communication logic level         | 3.3V                                                                                                             |
| Net Weight                        | 26.2g                                                                                                            |
| Gross Weight                      | 32.8g                                                                                                            |
| Product size                      | 72 \* 26 \* 19.2mm                                                                                               |
| Packing Size                      | 75 \* 36 \* 20.5mm                                                                                               |

### PinMap <a href="#pinmap" id="pinmap"></a>

* **IP101G (ETH\_ADDR = 1)**

| IPG101G (RMII PHY) | ESP32 |
| ------------------ | ----- |
| TX\_EN             | G21   |
| TX0                | G19   |
| TX1                | G22   |
| RX0                | G25   |
| RX1                | G26   |
| CRS\_DV            | G27   |

| IPG101G (SMI) | ESP32 |
| ------------- | ----- |
| MDC           | G23   |
| MDIO          | G18   |

* **HY2.0-4P**

| PoESP32 | RXD | TXD |
| ------- | --- | --- |
| M5CORE  | G16 | G17 |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/poesp32/poesp32_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (381).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit PoESP32](https://docs.m5stack.com/en/unit/Unit_PoESP32) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U138`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                 | Model-specific reference                                                                                                                                   |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic             | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/597/SCH_UNIT-PoESP32.pdf)                                                     |
| Mechanical / CAD files           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U138_Unit_PoESP32/Structures)                                    |
| Mechanical / CAD files           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U138_Unit_PoESP32/Structures/Unit_PoESP32.stl)                   |
| Example source: TCP\_CLIENT.ino  | [Read example source: tcp\_client.ino](https://github.com/m5stack/M5Unit-PoESP32/blob/master/examples/Unit_PoESP32_M5Core/TCP_CLIENT/TCP_CLIENT.ino)       |
| Example source: TCP\_CLIENT.ino  | [Read example source: tcp\_client.ino](https://github.com/m5stack/M5Unit-PoESP32/blob/master/examples/Unit_PoESP32_M5Core2/TCP_CLIENT/TCP_CLIENT.ino)      |
| Example source: TCP\_CLIENT.ino  | [Read example source: tcp\_client.ino](https://github.com/m5stack/M5Unit-PoESP32/blob/master/examples/Unit_PoESP32_M5Atom/TCP_CLIENT/TCP_CLIENT.ino)       |
| Example source: TCP\_CLIENT.ino  | [Read example source: tcp\_client.ino](https://github.com/m5stack/M5Unit-PoESP32/blob/master/examples/Unit_PoESP32_M5StickC/TCP_CLIENT/TCP_CLIENT.ino)     |
| Example source: TCP\_CLIENT.ino  | [Read example source: tcp\_client.ino](https://github.com/m5stack/M5Unit-PoESP32/blob/master/examples/Unit_PoESP32_M5StickCPlus/TCP_CLIENT/TCP_CLIENT.ino) |
| Example source: HTTP\_CLIENT.ino | [Read example source: http\_client.ino](https://github.com/m5stack/M5Unit-PoESP32/blob/master/examples/Unit_PoESP32_M5Core/HTTP_CLIENT/HTTP_CLIENT.ino)    |
| Example source: HTTP\_CLIENT.ino | [Read example source: http\_client.ino](https://github.com/m5stack/M5Unit-PoESP32/blob/master/examples/Unit_PoESP32_M5Core2/HTTP_CLIENT/HTTP_CLIENT.ino)   |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
