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

# M5Stack ESP32 Fisheye Camera

### M5Stack ESP32 Fisheye Camera Module with PSRAM (OV2640)

***

### Product Link

{% embed url="https://openelab.io/products/esp32-camera-module" %}

### Description <a href="#description" id="description"></a>

**ESP32CAM-PSRAM** is a development board for image recognition. It features an ESP32(4MB Flash + 520KB RAM + 4MB PSRAM) chip and 2-Megapixel camera (OV2640).

The module offers plenty of storage with an extra 4 Mbyte PSRAM. It also supports image transmission via Wi-Fi and debugging through USB Type-C port.

The hardware comes with preloaded software, programmed by ESP-IDF. It is an application to run Wi-Fi camera. The output image resolution is 600\*800, since it's 2MP camera, you sure can optimize the software to output a better resolution image.

Using processes:

* Power the board via USB type-C or GROVE
* Use your phone to Wi-Fi scan an AP name start with 'm5stack-' and click to connect this AP.
* Open up web browser on your phone and visit 192.168.4.1
* Then here comes the picture. Video is about 5-6 frames per seconds. not super fast.

### Features <a href="#features" id="features"></a>

* CP2104 USB-to-TTL converter
* ESP32-WROVER (PCB Antenna)
* WIFI image transmission
* OV2640 Camera
* Camera Field of View : 150 degree

### Applications <a href="#applications" id="applications"></a>

* DIY
* Time-lapse photography
* IoT monitoring

### Specifications <a href="#specifications" id="specifications"></a>

| Resources          | Parameters                                                                    |
| ------------------ | ----------------------------------------------------------------------------- |
| Flash/RAM          | 4MB/500K                                                                      |
| PSRAM              | 4M PSRAM                                                                      |
| Image Sensor       | OV2640                                                                        |
| Maximum resolution | 2M pixel                                                                      |
| Output format      | YUV(422/420)/YCbCr422,RGB565/555,8-bit compressed data,8-/10-bit Raw RGB data |
| FOV                | 150°                                                                          |
| CCD Size           | 1/4 inch                                                                      |
| Product Size       | 47\*20\*10mm                                                                  |
| Package Size       | 136\* 92\* 13mm                                                               |
| Product Weight     | 9.4g                                                                          |
| Package Weight     | 11.8g                                                                         |

### PinMap <a href="#pinmap" id="pinmap"></a>

**Camera Interface PinMap**

| \*Interface\*        | \*Camera Pin\* | \*ESP32CAM-PSRAM\* |
| -------------------- | :------------: | :----------------: |
| SCCB Clock           |      SIOC      |        IO23        |
| SCCB Data            |      SIOD      |      **IO22**      |
| System Clock         |      XCLK      |        IO27        |
| Vertical Sync        |      VSYNC     |      **IO25**      |
| Horizontal Reference |      HREF      |        IO26        |
| Pixel Clock          |      PCLK      |        IO21        |
| Pixel Data Bit 0     |       D2       |        IO32        |
| Pixel Data Bit 1     |       D3       |        IO35        |
| Pixel Data Bit 2     |       D4       |        IO34        |
| Pixel Data Bit 3     |       D5       |         IO5        |
| Pixel Data Bit 4     |       D6       |        IO39        |
| Pixel Data Bit 5     |       D7       |        IO18        |
| Pixel Data Bit 6     |       D8       |        IO36        |
| Pixel Data Bit 7     |       D9       |        IO19        |
| Camera Reset         |      RESET     |        IO15        |
| Camera Power Down    |      PWDN      |   \*see Note 1\*   |
| Power Supply 3.3V    |       3V3      |         3V3        |
| Ground               |       GND      |         GND        |

**GROVE Interface**

| \*Grove\* | \*ESP32CAM-PSRAM\* |
| :-------: | :----------------: |
|    SCL    |      **IO13**      |
|    SDA    |       **IO4**      |
|     5V    |         5V         |
|    GND    |         GND        |

**LED Interface**

|    LED   | \*ESP32CAM-PSRAM\* |
| :------: | :----------------: |
| LED\_Pin |        IO14        |

**NOTE:**

**Camera Power Down** pin does not need to be connected to ESP32 GPIO. Instead it may be pulled down to ground with 10 kOhm resistor.

### Datasheets <a href="#datasheets" id="datasheets"></a>

* [ESP32 ](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/esp32_datasheet_en.pdf)- [OV2640](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/OV2640DS_en.pdf)

### Schematics <a href="#schematics" id="schematics"></a>

#### Power circuit <a href="#power-circuit" id="power-circuit"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/image/m5-docs_schematic/unit/m5camera_sch_01.webp" alt=""><figcaption></figcaption></figure>

#### Chip peripheral circuit <a href="#chip-peripheral-circuit" id="chip-peripheral-circuit"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/image/m5-docs_schematic/unit/m5camera_sch_02.webp" alt=""><figcaption></figcaption></figure>

#### USB to serial port part of the circuit <a href="#usb-to-serial-port-part-of-the-circuit" id="usb-to-serial-port-part-of-the-circuit"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/image/m5-docs_schematic/unit/m5camera_sch_03.webp" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/ESP32CAM-PSRAM/%E5%B0%BA%E5%AF%B8%E5%9B%BE.png" alt=""><figcaption></figcaption></figure>
