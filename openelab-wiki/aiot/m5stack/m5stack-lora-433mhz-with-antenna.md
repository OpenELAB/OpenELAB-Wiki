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

# M5Stack LoRa 433MHz with Antenna

{% hint style="info" %}
[**View M5Stack LoRa Unit 433MHz with Antenna on OpenELAB**](https://openelab.io/products/m5stack-lora-unit-1)

**Store SKU / option:** `M5-U170-433`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack LoRa Unit 433MHz with Antenna

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-lora-unit-1" %}

### Description <a href="#description" id="description"></a>

The **LoRaE220-433 Unit** is a 433MHz LoRa communication module released by M5Stack, utilizing the LLCC68 chip solution. Compared to the traditional SX1278 solution, the LLCC68 offers advantages such as longer transmission distance, faster speed, and lower power consumption. This unit supports features like over-the-air wake-up, carrier sensing, and communication keys. It achieves point-to-point and broadcast transmission modes through convenient serial communication. The module includes an onboard DIP switch that allows users to switch between four different operating modes, enabling easy data transmission and reception without complex configurations. It is suitable for various applications, including home security alarms, building automation, smart homes, and the automotive industry.

### Features <a href="#features" id="features"></a>

* Utilizes LLCC68 chip solution
* Maximum transmission power of 22dBm, software adjustable
* Supports user-defined communication keys
* Supports over-the-air wake-up
* Supports point-to-point transmission, broadcast transmission, and channel monitoring
* Communication frequency: Supports 433MHz frequency band (410.125 \~ 493.125MHz)
* Onboard DIP switch to adjust communication modes
* Serial communication

### Applications <a href="#applications" id="applications"></a>

* Home security alarm and remote keyless entry
* Smart home and industrial sensors
* Wireless alarm security systems
* Building automation solutions
* Wireless industrial remote controllers
* Medical and health products
* Advanced Metering Infrastructure (AMI)
* Automotive applications

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                  | Parameters                                                                      |
| -------------------------- | ------------------------------------------------------------------------------- |
| Lora Module                | E220-400T22S@LLCC68                                                             |
| Supported Frequency Band   | Default 433MHz (supports 410.125 \~ 493.125MHz)                                 |
| Maximum Transmission Power | 22dBm, software adjustable                                                      |
| Receive Sensitivity        | -129 dBm                                                                        |
| Power Supply Voltage       | 5V                                                                              |
| Communication Method       | Serial communication (115200)                                                   |
| Operating Modes            | <p>Transmission mode<br>WOR transmit mode<br>WOR receive mode<br>Sleep mode</p> |
| Antenna                    | Rubber antenna (@2.5dBi, total length 110mm, SMA male connector)                |
| Working temperature        | 0-40°C                                                                          |
| Product Size               | 71.4\*24\*8mm                                                                   |
| Package Size               | 136\*92\*13mm                                                                   |
| Product Weight             | 19.4g                                                                           |
| Package Weight             | 24.8g                                                                           |

### Datasheets <a href="#datasheets" id="datasheets"></a>

* [LORA Module\_E220-400T22S](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/UNIT_LoraE220\(433MHz\)/E220-400T22S_UserManual_EN_v1.4.pdf)

### Schematics <a href="#schematics" id="schematics"></a>

note that the power supply voltage should not exceed 5.5v, otherwise more than 5.5v May permanently burn the module.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit%20LoRaE220-433/img-9ded71c5-4ab0-4a78-83fb-1b5b1417b2da.png" alt=""><figcaption></figcaption></figure>

### Operating Mode Configuration <a href="#operating-mode-configuration" id="operating-mode-configuration"></a>

LoRaE220-433 Operating Modes

| Operating Mode (0-3)  | M0, M1         | Description                                                                                      |
| --------------------- | -------------- | ------------------------------------------------------------------------------------------------ |
| 0: Transmission Mode  | M0:OFF, M1:OFF | Normal data packet transmission and reception mode                                               |
| 1: WOR Transmit Mode  | M0:ON, M1:OFF  | Send WOR data packets, this mode also supports data reception (support for over-the-air wake-up) |
| 2: WOR Receive Mode   | M0:OFF, M1:ON  | Disable data transmission, this mode only supports WOR data packet reception                     |
| 3: Configuration Mode | M0:ON, M1:ON   | Switch to configuration mode, used for configuring module transmit power, channel, address, etc. |

The "ON" in the table above stands for "0" in the datasheet;" "OFF" stands for "1" in the datasheet.

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/UNIT_LoraE220(433MHz)/5.jpg" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

| UNIT LoRaE220-433            | TXD | RXD  | 5V  | GND |
| ---------------------------- | --- | ---- | --- | --- |
| M5Core(PORT C)               | G16 | G17  | VCC | GND |
| M5Core2(PORT C)              | G13 | G14  | VCC | GND |
| M5CoreS3(PORT C)             | G18 | G17  | VCC | GND |
| M5CoreMP135(PORT C)          | PH8 | PF11 | VCC | GND |
| M5Atom Lite/M5Atom Matrix    | G32 | G26  | VCC | GND |
| M5Atom S3/M5Atom S3 Lite     | G1  | G2   | VCC | GND |
| M5StickC/M5StickC Plus/Plus2 | G33 | G32  | VCC | GND |

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit%20LoRaE220-433/img-675ca98f-ee4c-4acf-8a83-540ce2ab7336.jpg" alt=""><figcaption></figcaption></figure>

### Comparison of LoRa Solutions <a href="#comparison-of-lora-solutions" id="comparison-of-lora-solutions"></a>

#### LoRa Unit <a href="#lora-unit" id="lora-unit"></a>

| Product Name        | SKU      | Chip Solution       | Frequency | Max Transmit Power | Receiver Sensitivity | Data Transfer Rate | Theoretical Communication Distance | Antenna Interface      | Protocol Type | Typical Applicable Regions                                                                                      |
| ------------------- | -------- | ------------------- | --------- | ------------------ | -------------------- | ------------------ | ---------------------------------- | ---------------------- | ------------- | --------------------------------------------------------------------------------------------------------------- |
| LoRaE220-433 Unit   | U170-433 | E220-400T22S@LLCC68 | 433 MHz   | 22 dBm             | -129 dBm             | 2.4k-62.5 kbps     | 5 km                               | External Stick Antenna | LoRa          | EU countries, Canada, USA, China, Japan, Australia, New Zealand, South America, South Africa, Middle East, etc. |
| LoRa-e220-JP Unit   | U170     | E220-900T22S@LLCC68 | 920 MHz   | 13 dBm             | -124 dBm             | 1.7k-62.5 kbps     | 5 km                               | External Stick Antenna | LoRa          | Japan, Korea, USA, Brazil, Australia, New Zealand, Europe, etc.                                                 |
| LoRaWAN Unit 868MHz | U117     | ASR6501@SX1262      | 868 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRaWAN       | EU countries, Russia, Middle East, India, etc.                                                                  |
| Unit LoRaWAN915     | U115     | ASR6501@SX1262      | 915 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRaWAN       | USA, Canada, Australia, New Zealand, Brazil, Argentina, Taiwan, Japan, Israel, etc.                             |
| Unit LoRaWAN470     | U116     | ASR6501@SX1262      | 470 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRaWAN       | China                                                                                                           |

#### LoRa Module <a href="#lora-module" id="lora-module"></a>

| Product Name         | SKU      | Chip Solution  | Frequency | Max Transmit Power | Receiver Sensitivity | Data Transfer Rate | Theoretical Communication Distance | Antenna Interface      | Protocol Type | Typical Applicable Regions                                                                                      |
| -------------------- | -------- | -------------- | --------- | ------------------ | -------------------- | ------------------ | ---------------------------------- | ---------------------- | ------------- | --------------------------------------------------------------------------------------------------------------- |
| Module-LoRa868\_V1.1 | M029-V11 | Ra-01H@SX1276  | 868 MHz   | 19 dBm             | -148 dBm             | UP to 300 kbps     | 2-5 km                             | External Stick Antenna | LoRa          | EU countries, Russia, Middle East, India, etc.                                                                  |
| Module-LoRa433\_V1.1 | M005-V11 | Ra-02@SX1278   | 433 MHz   | 18 dBm             | -141 dBm             | UP to 300 kbps     | 2-5 km                             | External Stick Antenna | LoRa          | EU countries, Canada, USA, China, Japan, Australia, New Zealand, South America, South Africa, Middle East, etc. |
| Module LoRa 433MHz   | M005     | Ra-02@SX1278   | 433 MHz   | 18 dBm             | -141 dBm             | UP to 300 kbps     | 2-5 km                             | FPC Antenna            | LoRa          | EU countries, Canada, USA, China, Japan, Australia, New Zealand, South America, South Africa, Middle East, etc. |
| Module LoRa868       | M029     | Ra-01H@SX1276  | 868 MHz   | 19 dBm             | -148 dBm             | UP to 300 kbps     | 2-5 km                             | FPC Antenna            | LoRa          | EU countries, Russia, Middle East, India, etc.                                                                  |
| COM.LoRaWAN 868      | M031-C   | ASR6501@SX1262 | 868 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRaWAN       | EU countries, Russia, Middle East, India, etc.                                                                  |
| COM.LoRaWAN470       | M031-C2  | ASR6501@SX1262 | 470 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRaWAN       | China                                                                                                           |
| COM.LoRaWAN868 v2.0  | M031-C4  | ASR6501@SX1262 | 868 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRaWAN       | EU countries, Russia, Middle East, India, etc.                                                                  |
| COM.LoRaWAN915       | M031-C3  | ASR6501@SX1262 | 915 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRa/LoRaWAN  | USA, Canada, Australia, New Zealand, Brazil, Argentina, Taiwan, Japan, Israel, etc.                             |

#### LoRa Atom DTU <a href="#lora-atom-dtu" id="lora-atom-dtu"></a>

| Product Name        | SKU  | Chip Solution  | Frequency | Max Transmit Power | Receiver Sensitivity | Data Transfer Rate | Theoretical Communication Distance | Antenna Interface      | Protocol Type | Typical Applicable Regions                                                          |
| ------------------- | ---- | -------------- | --------- | ------------------ | -------------------- | ------------------ | ---------------------------------- | ---------------------- | ------------- | ----------------------------------------------------------------------------------- |
| ATOM DTU LoRaWAN915 | K061 | ASR6501@SX1262 | 915 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRaWAN       | USA, Canada, Australia, New Zealand, Brazil, Argentina, Taiwan, Japan, Israel, etc. |
| ATOM DTU LoRaWAN868 | K063 | ASR6501@SX1262 | 868 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRaWAN       | EU countries, Russia, Middle East, India, etc.                                      |
| ATOM DTU LoRaWAN470 | K062 | ASR6501@SX1262 | 470 MHz   | 21 dBm             | -136 dBm             | 0.3k-37.5 kbps     | 2-5 km                             | External Stick Antenna | LoRaWAN       | China                                                                               |

### Compatible

<figure><img src="../../.gitbook/assets/image (371).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit LoRaE220-433](https://docs.m5stack.com/en/unit/Unit_LoRaE220-433) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U170-433`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need              | Model-specific reference                                                                                                                           |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic          | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/624/SCH_UNIT_LoraE220_433MHz.pdf)                                     |
| Mechanical / CAD files        | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U170_Unit_LoRaE220_433/Structures)                       |
| Mechanical / CAD files        | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U170_Unit_LoRaE220_433/Structures/Unit_LoRaE220-433.stl) |
| Official source: M5-LoRa-E220 | [Read official source: m5-lora-e220](https://github.com/m5stack/M5-LoRa-E220)                                                                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
