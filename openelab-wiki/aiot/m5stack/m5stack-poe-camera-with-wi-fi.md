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

# M5Stack PoE Camera with Wi-Fi

### M5Stack PoE Camera with Wi-Fi

***

### Product Link

{% embed url="https://openelab.io/products/poe-camera" %}

### Description <a href="#description" id="description"></a>

**M5PoECAM-W V1.1** is a programmable PoE camera based on the "ESP32+W5500" solution, featuring a 3-megapixel OV3660 image sensor with a 66.5° field of view. It integrates PoE (power over Ethernet, max power consumption 6W) and Wi-Fi functionality. Equipped with 16MB Flash and 8MB PSRAM, programs can be downloaded via the Micro-USB interface. This camera offers a variety of interfaces and functional modules, including a G37 button, LED indicator light (G0), Grove interface (EXT\_PORT), and expansion pins. It also comes with a camera mounting clip and LEGO-compatible clip. Suitable for image monitoring, remote acquisition, smart home, industrial automation, and scenarios requiring devices powered through PoE cabling.

### Features <a href="#features" id="features"></a>

* Built-in ESP32-D0WDQ6-V3(Support 2.4G Wi-Fi)
* 3 million pixel camera OV3660
* Ethernet chip W5500
* LAN speeds up to 10M or 100M (depending on the line provided)
* PoE IEEE802.3 AF specification(Maximum power 6W)
* Built-in prompt LED light
* Ethernet standard interface RJ45
* Standard LEGO interface and camera mount
* Development platform:Arduino、ESP-IDF

### Applications <a href="#applications" id="applications"></a>

* Warehouse monitoring
* Timed photograph
* Machine vision
* Smart home monitoring

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                           | Parameters                                                                                                                                                                              |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SoC                                 | ESP32-D0WDQ6-V3                                                                                                                                                                         |
| Camera Module                       | OV3660 @3 Megapixel                                                                                                                                                                     |
| DFOV                                | 66.5°                                                                                                                                                                                   |
| Ethernet Chip                       | W5500                                                                                                                                                                                   |
| FLASH                               | 16MB                                                                                                                                                                                    |
| PSRAM                               | 8MB                                                                                                                                                                                     |
| Wi-Fi                               | 802.11 b/g/n                                                                                                                                                                            |
| Pixel Size                          | 1.75µm x 1.75µm                                                                                                                                                                         |
| Output Format                       | <p>RAW<br>RGB565/555/444<br>YUV422/420<br>YCbCr422<br>JPEG</p>                                                                                                                          |
| Automatic image control functions   | <p>Automatic Exposure Control (AEC)<br>Automatic Gain Control (AGC)<br>Automatic White Balance (AWB)<br>Automatic Band Filter (ABF)<br>and Automatic Black-Level Calibration (ABLC)</p> |
| FOV                                 | 65°                                                                                                                                                                                     |
| Supports Hardwired TCP/IP Protocols | TCP、UDP、ICMP、IPv4、ARP、IGMP、PPPoE                                                                                                                                                        |
| Ethernet interface specifications   | RJ45                                                                                                                                                                                    |
| PoE                                 | PoE IEEE802.3AF specification (Max power 6w)                                                                                                                                            |
| Product Size                        | 64\*24\*18mm                                                                                                                                                                            |
| Package Size                        | 80\*37\*32mm                                                                                                                                                                            |
| Product Weight                      | 38g                                                                                                                                                                                     |
| Package Weight                      | 45g                                                                                                                                                                                     |

### Datasheets <a href="#datasheets" id="datasheets"></a>

* [OV3660](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/OV3660_CSP3_DS_1.3_sida.pdf)
* [W5500](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/base/W5500_datasheet_v1.0.2_1_en.pdf)

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/M5PoECAM-W%20V1.1/img-82938e99-c979-4c12-bdeb-5c504c75aa76.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

* Grove interface & key \&led warning lamp

| ESP32-D0WDQ6-V3 | GPIO33 | GPIO25 | 5V  | GND | GPIO37 | GPIO0 |
| --------------- | ------ | ------ | --- | --- | ------ | ----- |
| Grove           | SCL    | SDA    | VCC | GND |        |       |
| Button          |        |        |     |     | Button |       |
| LED(Blue)       |        |        |     |     |        | LED   |

* Expansion pin (download pin)

| ESP32-D0WDQ6-V3 | CHIP\_UP | GPIO0 | GND | VCC  | GPIO1 | GPIO3 |
| --------------- | -------- | ----- | --- | ---- | ----- | ----- |
| Expansion pin   | EN       | G0    | G   | 3.3V | G1    | G3    |

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/M5PoECAM-W%20V1.1/img-40419f43-5f2d-40e8-92e9-bceec6908475.png" alt=""><figcaption></figcaption></figure>
