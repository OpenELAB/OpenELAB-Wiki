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

# M5Stack Voltage and Amperage Meter

{% hint style="info" %}
[**View M5Stack Voltage and Amperage Meter with M5StampS3 on OpenELAB**](https://openelab.io/products/m5stack-meter)

**Store SKU / option:** `M5-K136`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Voltage and Amperage Meter with M5StampS3

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-meter" %}

### Description <a href="#description" id="description"></a>

**VA Meter** is a professional programmable high-precision power meter designed for accurate voltage and current measurement. This product is based on the **M5StampS3** main control module, supporting WiFi functionality. It features two serially connected **INA226** current and voltage measurement circuits, providing current detection resolutions of 2.5uA and 250uA, and supports a measurement range of 0-5A and 5-24V (1-24V in isolation mode). The product can be powered through a USB-C interface or Base terminal input and includes built-in power and signal isolation. Users can select between isolated measurement via USB power or non-isolated measurement using direct power through a toggle switch, catering to different application needs. The accompanying expansion BASE includes relay on/off control and a Grove port for secondary development.

Additionally, the instrument supports OTA firmware upgrades and USB MSC/OTG functionality, allowing users to edit and view data and configuration files stored in the main control file system on a PC. M5 also provides a free online data API interface, enabling users to upload test data to the **EZData** platform for remote access and browsing, significantly simplifying IoT application development. The VA Meter is a versatile and developer-friendly instrument, ideal for engineering projects requiring precise current and voltage measurements, as well as fields such as industrial automation, equipment monitoring, and smart grids.

### Features <a href="#features" id="features"></a>

* High precision current detection (2.5uA/250uAResolution switching)
* Wide voltage input (5-24V)
* Cloud (EZData) data display
* PD input (internal does not contain PD decoy)
* Multiple power supply modes (PD INPUT/StampS3/External terminal)
* Power is isolated from signal
* USB MSC/OTG function
* Open source hardware and software
* OTA Upgrade

### Applications <a href="#applications" id="applications"></a>

* Industrial Automation
* Equipment Monitoring
* Power Testing and Analysis
* Internet of Things (IoT) Devices
* Remote Monitoring and Data Collection

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                            | Parameters                                                                                                                                       |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Power detection chip                 | INA226                                                                                                                                           |
| SoC                                  | ESP32S3FN8@Xtensa® 32-bit LX7 dual-core processor up to 240 MHz                                                                                  |
| Flash                                | 8MB Flash                                                                                                                                        |
| PSRAM                                | N/A                                                                                                                                              |
| Wi-Fi                                | IEEE 802.11 b/g/n (2.4 GHz Wi-Fi)                                                                                                                |
| Screen                               | 1.3 Inch@ 240\*240 Pixel                                                                                                                         |
| Screen Driver                        | ST7789                                                                                                                                           |
| PD Input Power                       | 5-24V@0-5A                                                                                                                                       |
| Current detection resolution         | 2.5uA/250uA                                                                                                                                      |
| Current sampling error               | <p>Small current (1-100mA) sampling error: 1.01%<br>Large current (100mA-5A) Sampling error: 0.94%<br>uA-level current sampling error: 0.69%</p> |
| Power Consumption (factory firmware) | <p>STAMPS3 USB power supply: DC5V/123.5mA<br>PD INPUT power supply: DC5V/118mA DC12V/66.8mA DC24V/26mA</p>                                       |
| PD OUTPUT capability                 | <p>DC24V/3A 68℃<br>DC24V/5A 92℃</p>                                                                                                              |
| USER interaction                     | Rotary encoder switch, reset button, boot button and board                                                                                       |
| INA226 Communication Address         | Two detection chips INA226:0x40/0x41                                                                                                             |
| Relay                                | DC 5-24V @5A                                                                                                                                     |
| Operating Temperature                | 0-40°C                                                                                                                                           |
| Product Size                         | <p>VAMeter 36<em>36</em>14.7mm<br>VAMeter 36<em>36</em>20.3mm<br>Rail Fastening 51.5<em>48</em>5.5mm</p>                                         |
| Package Size                         | 150 x 93 x 30mm                                                                                                                                  |
| Product Weight                       | <p>VAMeter:17.7g VAMeter Base:25.8g<br>Rail Fastening 4g</p>                                                                                     |
| Package Weight                       | 68.1g                                                                                                                                            |

### M5 EZData Cloud Platform example <a href="#m5-ezdata-cloud-platform-example" id="m5-ezdata-cloud-platform-example"></a>

<figure><img src="../../.gitbook/assets/image (356).png" alt=""><figcaption></figcaption></figure>

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="../../.gitbook/assets/image (358).png" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="../../.gitbook/assets/image (359).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [VAMeter](https://docs.m5stack.com/en/core/VAMeter) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K136`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                  | Model-specific reference                                                                                                                  |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic              | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/518/Sch_VAMeter_V1.2.pdf)                                    |
| Electrical schematic              | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/518/Sch_VAMeter_base_V1.0.pdf)                               |
| Mechanical / CAD files            | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K136_VAMeter/Structures)                        |
| Mechanical / CAD files            | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K136_VAMeter/Structures/VAMeter.stl)            |
| Mechanical / CAD files            | [Read mechanical / cad files](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/VAMeter_base_board.dxf) |
| Official source: VAMeter-Firmware | [Read official source: vameter-firmware](https://github.com/m5stack/VAMeter-Firmware)                                                     |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
