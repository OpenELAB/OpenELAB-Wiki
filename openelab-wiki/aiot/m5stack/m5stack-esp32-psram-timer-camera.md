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

# M5Stack ESP32 PSRAM Timer Camera

### M5Stack ESP32 PSRAM Timer Camera

***

### Product Link

{% embed url="https://openelab.io/products/psram-timer-camera" %}

### Description <a href="#description" id="description"></a>

**Timer Camera** is a camera module based on the ESP32 with 8MB of integrated with PSRAM. The 3 million (3MP) pixel camera (ov3660) ,DFOV 66.5 ° and can shoot a maximum of 2048x1536 resolution photos. There is a LED status indicator and reset button on the board. Timer Camera is designed to have ultra-low power consumption. Through the use of the RTC (BM8563), timing, sleep and wake-up functions can be utilized.

In sleep mode, the current consumption of the whole machine is only 2μA. After the scheduled photo taking function(one photo per hour) is turned on, the battery can work continuously for more than one month. The module supports Wi-Fi image transmission and USB port debugging. The bottom HY2.0-4P port output can be connected to other peripherals. In order to facilitate DIY, the battery interface is reserved on the board. Using the M5Burner firmware burning tool, time-cam can be set directly with the Camera-Tool, and TimerCamera data can be processed in UIFlow.

The low-power power management solution adopted by the Timer Camera series is different from the CORE and StickC devices. When in use, the PWR button is used as a power-on button(long press 2s). If you need to shut down the device, you need to use the software API or press the Reset button on the PCB.When using external power supply, the device will remain powered on.

### Features <a href="#features" id="features"></a>

* Design based on ESP32
* Wi-Fi image/video transmission
* Timed sleep wake up
* Status indicator
* Ultra low power design
* Programming platform:ESP-IDF/Arduino/UIFlow

### Applications <a href="#applications" id="applications"></a>

* Take pictures regularly
* Remote video monitoring

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                        | Parameter                                         |
| -------------------------------- | ------------------------------------------------- |
| PSRAM                            | 8MB                                               |
| Flash                            | 4M                                                |
| Image Sensor                     | OV3660                                            |
| Maximum resolution               | 3M pixels                                         |
| Output format                    | 8-/10-Bit RAW, RGB and YCbCr output, compression. |
| DFOV                             | 66.5°                                             |
| Battery Interface Specifications | SH1.0-2P                                          |
| Net Weight                       | 6g                                                |
| Gross Weight                     | 17g                                               |
| Product Size                     | 45\*20\*12mm                                      |
| Package Size                     | 60\*60\*15mm                                      |

### Driver Installation <a href="#driver-installation" id="driver-installation"></a>

TimerCAM may not work without drive in some systems. Users can manually install [FTDI Driver ](https://ftdichip.com/drivers/vcp-drivers/)to fix this problem. Take the win10 environment as an example, download the driver file that matches the operating system, unzip it, and install it through the device manager. (Note: In some system environments, the driver needs to be installed twice for the driver to take effect. The unrecognized device name is usually `M5Stack` or `USB Serial`. Windows recommends using the driver file to install directly in the device manager (custom Update), the executable file installation method may not work properly).

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc/ftdi_01.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (967).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (968).png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

**Camera Interface PinMap**

| Interface            | Camera Pin | TimerCamera |
| -------------------- | :--------: | :---------: |
| SCCB Clock           |    SIOC    |     IO23    |
| SCCB Data            |    SIOD    |     IO25    |
| System Clock         |    XCLK    |     IO27    |
| Vertical Sync        |    VSYNC   |     IO22    |
| Horizontal Reference |    HREF    |     IO26    |
| Pixel Clock          |    PCLK    |     IO21    |
| Pixel Data Bit 0     |     D0     |     IO32    |
| Pixel Data Bit 1     |     D1     |     IO35    |
| Pixel Data Bit 2     |     D2     |     IO34    |
| Pixel Data Bit 3     |     D3     |     IO5     |
| Pixel Data Bit 4     |     D4     |     IO39    |
| Pixel Data Bit 5     |     D5     |     IO18    |
| Pixel Data Bit 6     |     D6     |     IO36    |
| Pixel Data Bit 7     |     D7     |     IO19    |
| Camera Reset         |    RESET   |     IO15    |
| Camera Power Down    |    PWDN    |      -1     |
| Power Supply 3.3V    |     3V3    |     3V3     |
| Ground               |     GND    |     GND     |

**HY2.0-4P**

| HY2.0-4P | TimerCamera |
| :------: | :---------: |
|    SCL   |     G13     |
|    SDA   |      G4     |
|    5V    |      5V     |
|    GND   |     GND     |

**LED**

|    LED   | TimerCamera |
| :------: | :---------: |
| LED\_Pin |      G2     |

**BUTTON**

| BUTTON | TimerCamera |
| :----: | :---------: |
| BUTTON |     G37     |

**BM8563**

| BM8563 | TimerCamera |
| :----: | :---------: |
|   SCL  |     G14     |
|   SDA  |     G12     |

**BAT**

|       BAT      | TimerCamera |
| :------------: | :---------: |
|  BAT\_ADC\_Pin |     G38     |
| BAT\_HOLD\_Pin |     G33     |

### Schematics <a href="#schematics" id="schematics"></a>

[TimerCAM](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/schematic/TimerCAM/Sch_M5TimerCAM.pdf)

### Datasheets <a href="#datasheets" id="datasheets"></a>

* [ESP32](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/esp32_datasheet_cn.pdf)
* [OV3660](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/OV3660_CSP3_DS_1.3_sida.pdf)
