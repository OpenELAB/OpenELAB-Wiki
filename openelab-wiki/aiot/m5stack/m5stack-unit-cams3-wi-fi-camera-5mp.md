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

# M5Stack Unit CamS3 Wi-Fi Camera 5MP

{% hint style="info" %}
[**View M5Stack Unit CamS3 5MP ESP32-S3 Wi-Fi Camera on OpenELAB**](https://openelab.io/products/unit-cams3-wifi-camera-5mp)

**Store SKU / option:** `M5-U174-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Unit CamS3 Wi-Fi Camera 5MP

***

### Product Link

{% embed url="https://openelab.io/products/unit-cams3-wifi-camera-5mp" %}

### Description <a href="#description" id="description"></a>

**CAMS3 5MP Unit** is a streamlined camera module based on the ESP32S3, supporting WiFi cloud image transmission. It features 8M PSRAM and 16M Flash memory, paired with a custom 5-megapixel camera (PY260) that has a DFOV of 88° and can capture photos at a maximum resolution of 2592x1944. The unit includes a built-in Micro SD card slot for storing images and other data. An integrated PDM microphone allows for sound recording. The HY2.0-4P port at the bottom exposes the S3 internal D+/D- pins, supporting firmware updates or USB serial communication through the M5Grove2USB-C module. Two 1x3 pin headers on the board allow for ESP32S3 program downloading. The factory firmware provides a complete image capture and upload function called `EZData`, enabling users to achieve remote, free image monitoring through simple configuration. This product is suitable for remote monitoring, time-lapse photography, industrial automation, and various other applications.

To download the program: When using the [Grove2USB-C ](https://docs.m5stack.com/en/accessory/Grove2USB-C)provided with the product packaging, before powering on, short-circuit the G0 and GND pins of the pin header with the provided male-to-male breadboard wire to enter download mode. Then, you can use Grove2USB-C to connect and download.

<figure><img src="../../.gitbook/assets/image (451).png" alt=""><figcaption></figcaption></figure>

[M5CamS3 5MP Getting Started Tutorial](https://docs.m5stack.com/en/guide/wifi_camera/m5cams3/m5cams3)[M5CamS3 5MP Getting Started Tutorial](https://docs.m5stack.com/en/guide/wifi_camera/m5cams3/m5cams3)This tutorial will show you how to burn firmware and features to an M5CAMS3 5MP device using Burner

### Features <a href="#features" id="features"></a>

* Based on the ESP32-S3-WROOM-1-N16R8 module, supports WiFi.
* WiFi cloud EZDATA or single-port image data transmission.
* Equipped with a 5-megapixel camera (PY260).
* Built-in Micro SD card slot.
* Built-in PDM microphone, supports audio recording function.
* Built-in programmable indicator light.

### Includes <a href="#includes" id="includes"></a>

* 1x CAMS3 5MP Unit
* 1x Grove2USB-C
* 2x Male-to-Male Breadboard Wires
* 1x HY2.0-4P Grove Cable (20cm)
* 1x LEGO-Compatible Component

### Applications <a href="#applications" id="applications"></a>

* Remote Monitoring
* Time-lapse Photography
* Industrial Automation

### Specification <a href="#specification" id="specification"></a>

| Resources                  | Parameters                                                   |
| -------------------------- | ------------------------------------------------------------ |
| ESP32-S3-WROOM-1-N16R8     | Dual-core 240 MHz @ Supports WiFi, module antenna integrated |
| PSRAM                      | 8M PSRAM                                                     |
| Flash                      | 16M Flash                                                    |
| Camera                     | 5M Pixel @ PY260                                             |
| Supported Output Formats   | JPEG                                                         |
| DFOV                       | 88°                                                          |
| MIC                        | PDM Microphone @ MSM1261D4030HCPM                            |
| Supports memory card types | Micro SD card                                                |
| Operating Temperature      | 0-40°C                                                       |
| Product Size               | 40\*24\*11mm                                                 |
| Package Size               | 136\*92\*20mm                                                |
| Product Weight             | 10.8g                                                        |
| Package Weight             | 18.9g                                                        |

![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-CAMS3%205MP/3.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-CAMS3%205MP/5.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-CAMS3%205MP/7.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-CAMS3%205MP/8.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-CAMS3%205MP/9.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-CAMS3%205MP/11.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a simple and fast program burner, it has a product related case program built in, through simple steps to burn it to the master, you can carry out a series of functional verification.

[Download Windows Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-CAMS3%205MP/CAMS3%205MP%20Unit%20Firmware.exe)

After burning the firmware, the computer or mobile phone is connected to the hot spot of "UnitCAMS3-WiFi", enter 192.168.4.1 in the browser, and click "Steam" to view the image. Built-in EZData cloud remote viewing, recording, SD card storage and other practical functions.

### Related Link <a href="#related-link" id="related-link"></a>

* [ESP32-S3-WROOM-1-N16R8](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-CamS3/ESP32-S3-WROOM-1-N16R8.pdf)
* [MSM1261D4030HCPM(PDM Datasheet)](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-CamS3/MSM1261D4030HCPM.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-CAMS3%205MP/img-4556c40c-8606-4e17-a392-d8d9b29b531a.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

**Camera Interface PinMap**

| \*Interface\*        | \*Camera Pin\* | \*ESP32CAM-PSRAM\* |
| -------------------- | :------------: | :----------------: |
| SCCB Clock           |      SIOC      |        IO41        |
| SCCB Data            |      SIOD      |      **IO17**      |
| System Clock         |      XCLK      |        IO11        |
| Vertical Sync        |      VSYNC     |      **IO42**      |
| Horizontal Reference |      HREF      |        IO18        |
| Pixel Clock          |      PCLK      |        IO12        |
| Pixel Data Bit 0     |       D2       |         IO6        |
| Pixel Data Bit 1     |       D3       |        IO15        |
| Pixel Data Bit 2     |       D4       |        IO16        |
| Pixel Data Bit 3     |       D5       |         IO7        |
| Pixel Data Bit 4     |       D6       |         IO5        |
| Pixel Data Bit 5     |       D7       |        IO10        |
| Pixel Data Bit 6     |       D8       |         IO4        |
| Pixel Data Bit 7     |       D9       |        IO13        |
| Camera Reset         |      RESET     |        IO21        |
| Camera Power Down    |      PWDN      |         GND        |
| Power Supply 3.3V    |       3V3      |         3V3        |
| Ground               |       GND      |         GND        |

| CAMS3 5MP Unit   | TX/D+ | RX/D- | CS | MOSI | CLK | MISO | LED | MIC\_CLK | MIC\_DATA |
| ---------------- | ----- | ----- | -- | ---- | --- | ---- | --- | -------- | --------- |
| GROVE            | G20   | G19   |    |      |     |      |     |          |           |
| SD Card Socket   |       |       | G9 | G38  | G39 | G40  |     |          |           |
| Programmable LED |       |       |    |      |     |      | G14 |          |           |
| MIC              |       |       |    |      |     |      |     | G47      | G48       |

### Dimensions

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-CAMS3%205MP/img-92a0b5bb-a0c6-4604-8e2b-ca7856313280.jpg" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [CamS3 5MP Unit factory firmware](https://github.com/m5stack/UnitCamS3-UserDemo/tree/unitcams3-5mp)

## Official documentation and development resources

Use [Unit CamS3-5MP](https://docs.m5stack.com/en/unit/Unit_CamS3-5MP) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U174-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                                       |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5unitcams3_5mp/program)                                                               |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/1050/SCH_UNIT_CAMS3_V1.0.pdf)                                                     |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U174%E2%80%91B_Unit_CamS3%E2%80%915MP/Structures)                    |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U174%E2%80%91B_Unit_CamS3%E2%80%915MP/Structures/Unit_CamS3-5MP.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
