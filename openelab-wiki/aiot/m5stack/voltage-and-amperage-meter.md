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

# Voltage and Amperage Meter

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

### Tutorial <a href="#tutorial" id="tutorial"></a>

![VAMeter](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/M5PPT%20\(524%20x%20395%20%E5%83%8F%E7%B4%A0\)%20\(4\).png)

[Quick Start](https://docs.m5stack.com/en/guide/iot_tools/vameter/usage)[Quick Start](https://docs.m5stack.com/en/guide/iot_tools/vameter/usage)

This tutorial will introduce you to the VA Meter device tutorial & Get started quicklyDownload ModeIf you want to enter download mode, press and hold the G0 button on StampS3 before turning it on, then release it after powering it on.\
![schematics](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/M5PPT%20\(1135%20x%201080%20%E5%83%8F%E7%B4%A0\).gif)

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

### Specification <a href="#specification" id="specification"></a>

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
| Package Size                         | 150\*93\*30mm                                                                                                                                    |
| Product Weight                       | <p>VAMeter:17.7g VAMeter Base:25.8g<br>Rail Fastening 4g</p>                                                                                     |
| Package Weight                       | 68.1g                                                                                                                                            |

![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/5.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/6.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/7.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/9.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/13.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/16.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a concise and fast program writer, which has a built-in case program related to the product. It can be burned to the main control by simple steps to perform a series of function verification.

[Download VA Meter Factory Firmware Easyloader](https://static-cdn.m5stack.com/resource/docs/products/core/VA%20Meter/ezLoader-478cc662-c125-4135-a15e-9fcebbfc4e6d.exe)

### M5 EZData Cloud Platform example <a href="#m5-ezdata-cloud-platform-example" id="m5-ezdata-cloud-platform-example"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/c12028ed506f1fa2ad551f468d89ab2.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

* VAMeter(INA226 & BUZZER)

NoteINA226(0x40) and INA226(0x41) are used for measurements of different resolutions and sizes

| M5STAMPS3    | G5   | G6   | G41    | G40    | G14      |
| ------------ | ---- | ---- | ------ | ------ | -------- |
| INA226(0x40) | FSDA | FSCL | ALERT1 |        |          |
| INA226(0x41) | FSDA | FSCL |        | ALERT2 |          |
| BUZZER       |      |      |        |        | BUZ\_PWM |

* VAMeter Extra output pin

| M5STAMPS3        | G10      | G9      | G8      | G42      |
| ---------------- | -------- | ------- | ------- | -------- |
| Extra output pin | EXT\_G10 | EXT\_G9 | EXT\_G8 | EXT\_G42 |

* VAMeter Base

| M5STAMPS3 | G10         |
| --------- | ----------- |
| Relay     | GPIO10\_REL |

* Grove

| M5STAMPS3 | G9    | G8    | VCC     | GND  |
| --------- | ----- | ----- | ------- | ---- |
| Grove     | GPIO9 | GPIO8 | SYS\_5V | FGND |

### VAMeter compared to other brands <a href="#vameter-compared-to-other-brands" id="vameter-compared-to-other-brands"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/bee092896d7696d76da369b27cbab69.png" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* [INA226](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/ina226.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

* VAMeter

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/VA%20Meter/img-ffd4beca-765d-4036-9f5b-11c0536422c8.png" alt=""><figcaption></figcaption></figure>

* VAMeter Base

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/09c585009cf477ba9c7ca90976167cc.png" alt=""><figcaption></figcaption></figure>

* VAMeter internal circuit logic diagram

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/01.png" alt="" width="375"><figcaption></figcaption></figure>

[VA Meter Schematic PDF](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/Sch_VAMeter_V1.2.pdf)

[VA Meter Base Schematic PDF](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/Sch_VAMeter_base_V1.0.pdf)

[VAMeter Base PCB Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/VAMeter_base_board.dxf)

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/VA%20Meter/7658e330231814126dd64b55760eaea.png" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [VA Meter factory firmware](https://github.com/m5stack/VAMeter-Firmware)

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
