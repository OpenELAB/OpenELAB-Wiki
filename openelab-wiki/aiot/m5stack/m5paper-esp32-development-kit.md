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

# M5Paper ESP32 Development Kit

### M5Paper ESP32 Development Kit V1.1

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**M5Paper v1.1** is M5Stacks latest core device with a touch enabled [E-ink ](https://en.wikipedia.org/wiki/E_Ink)display. Powered by the ESP32-D0WDQ6-V3 this is our first device to integrate a super sized 540\*960 @4.7" [E-ink ](https://en.wikipedia.org/wiki/E_Ink)display,which supports 16 gray scale levels. The display is a GT911 capacitive touch screen,which supports two point touch and a variety of gesture controls . Compared to a regular LCD,E-ink displays are easier on the eyes, which makes them a great choice for reading or viewing for longer periods. Other benefits are the low power consumption and the ability to retain the image even if power to the display is terminated. Integrated in the CoreInk are an multi-function button for operation, SHT30 temperature and moisture sensor, physical buttons and an TF-card(microSD) port for data storage.

Additionally the FM24C02 internal eeprom chip provided 2K-bit(256x8)-EEPROM can be used to store vital data even when the device is off. A 1150mAh lithium polymer battery keeps the device going for long periods and battery life can be further preserved by using the RTC(BM8563)to set the device into deep sleep and wake it up again when needed。Three HY2.0-4P expansion ports are included which allow for building complex projects using the existing sensors in the M5Stack ecosystem.

Warning:&#x20;

1\. Do not expose to ultraviolet rays for a long time, otherwise it may cause irreversible damage to the ink screen.&#x20;

2\. The low-power power management solution adopted by M5Paper is different from CORE and StickC devices. When using it, the PWR button is used as the power-on button (long press for 2s). If you need to shut down the device, you need to use the software API or It is realized by pressing the reset button on the back. When using USB power supply, it cannot be shut down.&#x20;

3\. During use, if the program cannot be downloaded normally (the prompt is overtime or Failed to write to target RAM), you can try to reinstall the device driver.&#x20;

### Features <a href="#product-features" id="product-features"></a>

* ESP32 Standard wireless functions Wi-Fi
* Internal 16M Flash
* Low Power Display
* Multi-Point touch screen
* 180 degree viewing angle
* Built-in Magnet
* Internal 1150mAh Battery
* Expandable - HY2.0-4P 3 x external expansion ports

### Applications <a href="#applications" id="applications"></a>

* IoT Terminal
* E-Book
* Industrial Control Panel
* Smart Home Panel

### Version distinction <a href="#version-distinction" id="version-distinction"></a>

| M5Paper            | M5Paper v1.1           |
| ------------------ | ---------------------- |
| Hard display panel | Flexible display panel |

### Specification <a href="#specification" id="specification"></a>

| Resources                    | Parameter                                                                                                                           |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| ESP32-D0WDQ6-V3              | 240MHz dual core, 600 DMIPS, 520KB SRAM, Wi-Fi                                                                                      |
| Flash                        | 16MB                                                                                                                                |
| PSRAM                        | 8MB                                                                                                                                 |
| Input Voltage                | 5V @ 500mA                                                                                                                          |
| Ports                        | TypeC\*1, HY2.0-4P\*3 , TF-card(microSD) slot                                                                                       |
| Sleep mode Power consumption | 3.7V@10uA (RTC only)                                                                                                                |
| E-Ink Display                | Model Number:EPD\_ED047TC1 \| 540\*960@4.7" \| Gray scale : 16 Levels \| Display area : 58.32\*103.68mm \| Display Driver : IT8951E |
| Physical Button              | Multi-function button\*1 , Reset Button\*1                                                                                          |
| RTC                          | BM8563                                                                                                                              |
| Antenna                      | 2.4G 3D Antenna                                                                                                                     |
| PINS                         | G25, G32, G26, G33, G18, G19                                                                                                        |
| Battery                      | 1150mAh@3.7V                                                                                                                        |
| Working Temp                 | 0°C to 60°C                                                                                                                         |
| Net Weight                   | 86g                                                                                                                                 |
| Gross Weight                 | 100g                                                                                                                                |
| Product Dimension            | 118\*66\*10mm                                                                                                                       |
| Packaging Dimension          | 120\*70\*14mm                                                                                                                       |
| Casing Material              | Plastic ( PC )                                                                                                                      |

### Refresh Mode Comparison <a href="#refresh-mode-comparison" id="refresh-mode-comparison"></a>

* Speed Comparison

![module size](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/m5paper/Mode_fastest.gif) ![module size](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/m5paper/Mode_fast.gif) ![module size](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/m5paper/Mode_text.gif) ![module size](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/m5paper/Mode_quality.gif)

* Quality Comparison

<img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/m5paper/edp_mode.png" alt="module size" width="80%">

| Mode         | Advantages                                                                                                         | Disadvantages                                                                                     |
| ------------ | ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------- |
| epd\_quality | Best display quality, suitable for high-precision image and text display, detailed and smooth grayscale transition | Slow refresh rate, unsuitable for fast updates                                                    |
| epd\_text    | Suitable for text display, fast refresh rate, energy-efficient, high text clarity                                  | Limited grayscale support, not ideal for complex images                                           |
| epd\_fast    | Faster refresh rate, suitable for frequent updates, maintains a certain level of image quality                     | Lower image quality, grayscale transition less smooth than high-quality mode                      |
| epd\_fastest | Fastest refresh rate, ideal for quick-response scenarios                                                           | Lowest image quality, poor grayscale transition, unsuitable for high-quality display requirements |

### PinMap <a href="#pinmap" id="pinmap"></a>

**E-INK & TF-card(microSD)**

Resolution:540\*960

| ESP32 Chip       | GPIO13 | GPIO12 | GPIO14 | GPIO15 | GPIO4 |
| ---------------- | ------ | ------ | ------ | ------ | ----- |
| IT8951E          | MISO   | MOSI   | SCK    | CS     | /     |
| TF-card(microSD) | MISO   | MOSI   | SCK    | /      | CS    |

**Multi-function button & PWR**

| ESP32 Chip            | GPIO37 | GPIO38  | GPIO39 | GPIO2 |
| --------------------- | ------ | ------- | ------ | ----- |
| Multi-function button | Right  | BTN/PWR | Left   | /     |
| Power Control         | /      | /       | /      | MOS   |

**Internal I2C Connection**

| ESP32 Chip | GPIO21 | GPIO22 | GPIO36 |
| ---------- | ------ | ------ | ------ |
| GT911      | SDA    | SCL    | INT    |
| SHT30      | SDA    | SCL    | /      |
| BM8563     | SDA    | SCL    | /      |
| FM24C02    | SDA    | SCL    | /      |

**USB Serial**

| ESP32 Chip      | GPIO1 | GPIO3 |
| --------------- | ----- | ----- |
| CP2104 / Ch9102 | RXD   | TXD   |

### M5Paper-HY2.0 4P Port <a href="#m5paper-hy2.0-4p-port" id="m5paper-hy2.0-4p-port"></a>

| PORT   | PIN     | Protocol: |
| ------ | ------- | --------- |
| PORT.A | G25,G32 | I2C       |
| PORT.B | G26,G33 | DAC/ADC   |
| PORT.C | G18,G19 | UART      |

#### ESP32 ADC/DAC Mappable Pins <a href="#esp32-adc-dac-mappable-pins" id="esp32-adc-dac-mappable-pins"></a>

| ADC1      | ADC2               | DAC1      | DAC2      |
| --------- | ------------------ | --------- | --------- |
| 8 Channel | 10 Channel         | 2 Channel | 2 Channel |
| G32-39    | G0/2/4/12-15/25-27 | G25       | G26       |

### Schematic <a href="#schematic" id="schematic"></a>

* [M5 PAPER Schematic](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/schematic/Core/m5paper/M5_PAPER_SCH.pdf)

### Module Size <a href="#module-size" id="module-size"></a>

![module size](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/m5paper_v1.1/paper%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg)
