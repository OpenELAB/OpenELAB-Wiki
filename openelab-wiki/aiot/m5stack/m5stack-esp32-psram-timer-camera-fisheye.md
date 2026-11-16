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

# M5Stack ESP32 PSRAM Timer Camera Fisheye

### M5Stack ESP32 PSRAM Timer Camera Fisheye

***

### Product Link

{% embed url="https://openelab.io/products/psram-timer-camera-fisheye" %}

### Description <a href="#description" id="description"></a>

The **Timer Camera F** is a fisheye camera module based on ESP32-D0WDQ6-V3 with 8M PSRAM and 4M Flash on board. 3.0 megapixel camera (OV3660) with DFOV 120° and a maximum resolution of 2048x1536 photos can be captured. The camera features an ultra-low-power design, and the internal integrated RTC (BM8563) draws out the IRQ signal, which can be used for sleep and timer wake-up (sleep current down to 2μA). The built-in 270mAh battery provides more than one month of battery life with timed pictures (one per hour) enabled. The module supports Wi-Fi image transfer and USB port debugging, and the HY2.0-4P output on the bottom can be used to expand other peripherals. The on-board LED status indicator and reset button facilitate program development and debugging. In terms of application, M5Stack provides a number of simple and efficient application development methods and interfaces for the TimerCAM series, making it easy for users to use and develop their applications. (including PC/Mobile photo shooting APP, cloud image HTTP interface for timer shooting, cloud AI recognition interface (not online yet), etc.)

### Features <a href="#features" id="features"></a>

* Design based on esp32
* Wi-Fi image transmission
* Timed sleep wake up
* Status indicator
* Ultra low power design
* Built-in 270mAh battery
* Programming platform:ESP-IDF/Arduino/UIFlow

### Applications <a href="#applications" id="applications"></a>

* Take pictures regularly
* Remote video monitoring

### Specifications <a href="#specifications" id="specifications"></a>

| Resources          | Parameter                                         |
| ------------------ | ------------------------------------------------- |
| PSRAM              | 8MB                                               |
| Flash              | 4M                                                |
| Battery            | 270mAh                                            |
| Image Sensor       | OV3660                                            |
| Maximum resolution | 3M pixels                                         |
| Output format      | 8-/10-Bit RAW, RGB and YCbCr output, compression. |
| DFOV               | 120°                                              |
| Net weight         | 21g                                               |
| Gross weight       | 44g                                               |
| Product Size       | 48\*24\*22.6mm                                    |
| Package Size       | 75\*45\*30mm                                      |

The low-power power management solution adopted by the Timer Camera series is different from the CORE and StickC devices. When in use, the PWR button is used as a power-on button(long press 2s). If you need to shut down the device, you need to use the software API or press the Reset button on the PCB.When using external power supply, the device will remain powered on.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/timercam_x/timercam_x_10.webp" alt=""><figcaption></figcaption></figure>

### Driver Installation <a href="#driver-installation" id="driver-installation"></a>

TimerCAM may not work without drive in some systems. Users can manually install [FTDI Driver ](https://ftdichip.com/drivers/vcp-drivers/)to fix this problem. Take the win10 environment as an example, download the driver file that matches the operating system, unzip it, and install it through the device manager. (Note: In some system environments, the driver needs to be installed twice for the driver to take effect. The unrecognized device name is usually `M5Stack` or `USB Serial`. Windows recommends using the driver file to install directly in the device manager (custom Update), the executable file installation method may not work properly).

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc/ftdi_01.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (965).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (966).png" alt=""><figcaption></figcaption></figure>

### FISH EYE LENS Comparison Normal LENS <a href="#fish-eye-lens-comparison-normal-lens" id="fish-eye-lens-comparison-normal-lens"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/timercam_f/timercam_f_10.webp" alt=""><figcaption></figcaption></figure>

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

[TimerCAM\_F](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/schematic/TimerCAM/Sch_M5TimerCAM.pdf)

### Datasheets <a href="#datasheets" id="datasheets"></a>

* [ESP32](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/esp32_datasheet_en.pdf)
* [OV3660](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/OV3660_CSP3_DS_1.3_sida.pdf)

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/timercam_f/186b42f289721cf96daafc4bb82737b.png" alt=""><figcaption></figcaption></figure>
