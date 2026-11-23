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

# M5Stack LoRa

{% hint style="info" %}
[**View M5Stack LoRa Unit with Antenna E220 920MHz on OpenELAB**](https://openelab.io/products/m5stack-lora-unit)

**Store SKU / option:** `M5-U170`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack LoRa Unit with Antenna(E220)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-lora-unit" %}

### Description <a href="#description" id="description"></a>

The **LoRaE220 Unit** is a LoRa communication module introduced by M5Stack, designed for the **920MHz** frequency band. It utilizes convenient serial communication. It supports point-to-point transmission and broadcast modes, as well as wireless wake-up, carrier monitoring, and communication key features. It can switch between four different operating modes using onboard dip switches, allowing for configuration of data transmission and reception functions, catering to various communication needs. It is suitable for applications in home security alarms, building automation, smart homes, and the automotive industry, among others.

### Features <a href="#features" id="features"></a>

* Rich communication functions: support Wake on Radio (wireless wake up), carrier monitoring, communication key and other functions.
* Onboard DIP switch: Toggle the switch to configure the working mode and configure the data sending and receiving functions.
* Communication frequency band: Supports the 920MHz band(920.6〜928.0MHz).
* High performance: A new generation of LoRa solutions with longer transmission distances, faster speeds and lower power consumption.
* Serial communication: Supports serial communication to provide a high degree of flexibility and reliability for iot applications.

### Applications <a href="#applications" id="applications"></a>

* Agriculture, industrial automation
* Home security
* Automotive industries

### Specification <a href="#specification" id="specification"></a>

| Resources                  | Parameters                               |
| -------------------------- | ---------------------------------------- |
| Lora Module                | E220-900T22S(JP) @ Telec(001-P01730)     |
| Module Chip                | LLCC68                                   |
| Support band               | 920MHz(920.6〜928.0MHz)                   |
| Maximum transmitting power | 13dBm（About20mW）                         |
| Communication distance     | The communication distance is up to 5 km |
| Service voltage            | 5V                                       |
| Communication mode         | Serial port communication                |
| Product Size               | 71.4\*24\*8mm                            |
| Package Size               | 136\*92\*13mm                            |
| Product Weight             | 19.5g                                    |
| Package Weight             | 25.1g                                    |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/LoRaE220-JP%20Unit/img-85255c68-fda4-414e-bcb0-99fb0e97e571.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

LoRaE220-JP Working Mode

| WORKING MODE(0-3)    | M0, M1         | Description                                                                                                    |
| -------------------- | -------------- | -------------------------------------------------------------------------------------------------------------- |
| 0:Transmission Mode  | M0:OFF, M1:OFF | Normal data packet sending and receiving mode                                                                  |
| 1:WOR Sending Mode   | M0:ON, M1:OFF  | Send WOR data packets, this mode also supports data receiving                                                  |
| 2:WOR Receiving Mode | M0:OFF, M1:ON  | Disable data transmission. This mode only supports WOR data packet receiving.                                  |
| 3:Configuration Mode | M0:ON, M1:ON   | Switch to configuration mode to configure the module's transmit power, channel, address, and other information |

The "ON" in the table above stands for "0" in the datasheet;" "OFF" stands for "1" in the datasheet.

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/LoRaE220-JP%20Unit/3.jpg" alt=""><figcaption></figcaption></figure>

PORT C

| UNIT-LoRaE220-JP             | TXD | RXD  | 5V  | GND |
| ---------------------------- | --- | ---- | --- | --- |
| M5Core(PORT C)               | G16 | G17  | VCC | GND |
| M5Core2(PORT C)              | G13 | G14  | VCC | GND |
| M5CoreS3(PORT C)             | G18 | G17  | VCC | GND |
| M5CoreMP135(PORT C)          | PH8 | PF11 | VCC | GND |
| M5ATOM Lite/ATOM Matrix      | G32 | G26  | VCC | GND |
| M5ATOMS3/ATOMS3 Lite         | G1  | G2   | VCC | GND |
| M5StickC/M5StickC plus/plus2 | G33 | G32  | VCC | GND |

### ![](<../../.gitbook/assets/image (394).png>)Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/LoRaE220-JP%20Unit/img-14d3d8e7-2987-4184-a5be-6cb1d492082d.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (395).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit LoRaE220-920](https://docs.m5stack.com/en/unit/Unit_LoRaE220-920) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U170`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                 | Model-specific reference                                                                                                                           |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic             | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/623/SCH_UNIT_LoraE220.pdf)                                            |
| Mechanical / CAD files           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U170_Unit_LoRaE220-920/Structures)                       |
| Mechanical / CAD files           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U170_Unit_LoRaE220-920/Structures/Unit_LoRaE220-920.stl) |
| Official source: M5-LoRa-E220-JP | [Read official source: m5-lora-e220-jp](https://github.com/m5stack/M5-LoRa-E220-JP)                                                                |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
