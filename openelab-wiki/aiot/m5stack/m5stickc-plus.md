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

# M5StickC PLUS

{% hint style="info" %}
[**View M5StickC PLUS ESP32-PICO Mini IoT Development Kit on OpenELAB**](https://openelab.io/products/m5stickc-plus-esp32-pico)

**Store SKU / option:** `M5-K016-P`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5StickC PLUS ESP32-PICO Mini IoT Development Kit

***

### Product Link

{% embed url="https://openelab.io/products/m5stickc-plus-esp32-pico" %}

### Description <a href="#description" id="description"></a>

**M5StickC PLUS** is powered by ESP32-PICO-D4 with Wi-Fi and is an upgrade of the original M5StickC with a bigger screen .It is a portable, easy-to-use, open source, IoT development board. This tiny device will enable you to realize your ideas, enrich your creativity, and speed up your IoT prototyping. Developing with M5StickC PLUS takes away a lot of the pains from the development process. M5StickC Plus is one of the core devices in M5Stacks product series. The compact body is integrated with rich hardware resources, such as infrared, RTC, Microphone, LED, IMU, Buttons, PMU,etc. Improvements from the regular StickC are a buzzer, bigger screen (1.14-inch, 135 \* 240 resolution LCD Screen) and more stable hardware design. This revision increases the display area by 18.7%, and the battery capacity from 95mAh to 120mAh. It also supports the HAT and Unit family of products.

**Power switch operation:**

* Power on :Press power button for 2 seconds
* Power off :Press power button for 6 seconds

### Features <a href="#product-features" id="product-features"></a>

* ESP32-based support Wi-Fi
* Built-in 6-Axis IMU
* Red LED
* IR transmitter
* Microphone
* RTC
* Buttons, LCD(1.14 inch)
* Built-in Lithium Polymer Battery
* Extendable Socket
* Built-in Passive Buzzer
* Wearable & Wall mounted
* Compatible with multi-platform development:
  * UIFlow
  * MicroPython
  * Arduino
  * .NET nanoFramework

### Applications <a href="#applications" id="applications"></a>

* Internet of things terminal controller
* Wearable devices
* Stem education product
* DIY creation

### Specification <a href="#specification" id="specification"></a>

| Resources             | Parameter                                      |
| --------------------- | ---------------------------------------------- |
| ESP32                 | 240MHz dual core, 600 DMIPS, 520KB SRAM, Wi-Fi |
| Flash Memory          | 4MB                                            |
| Power Input           | 5V @ 500mA                                     |
| Port                  | TypeC x 1, GROVE(I2C+I/0+UART) x 1             |
| LCD screen            | 1.14 inch, 135\*240 Colorful TFT LCD, ST7789v2 |
| Button                | Custom button x 2                              |
| LED                   | RED LED                                        |
| MEMS                  | MPU6886                                        |
| Buzzer                | built-in buzzer                                |
| IR                    | Infrared transmission                          |
| MIC                   | SPM1423                                        |
| RTC                   | BM8563                                         |
| PMU                   | AXP192                                         |
| Battery               | 120 mAh @ 3.7V                                 |
| Antenna               | 2.4G 3D Antenna                                |
| PIN port              | G0, G25/G36, G26, G32, G33                     |
| Operating Temperature | 0°C to 60°C                                    |
| Net weight            | 15g                                            |
| Gross weight          | 21g                                            |
| Product Size          | 48\*24\*13.5mm                                 |
| Package Size          | 114\*64\*22mm                                  |
| Case Material         | Plastic ( PC )                                 |

![](https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc_plus/m5stickc_plus_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc_plus/m5stickc_plus_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc_plus/m5stickc_plus_06.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc_plus/m5stickc_plus_07.webp)

### PinMap <a href="#pinmap" id="pinmap"></a>

**RED LED & IR Transmitter & BUTTON A & BUTTON B**

| ESP32          | GPIO10  | GPIO9           | GPIO37     | GPIO39     | GPIO2      |
| -------------- | ------- | --------------- | ---------- | ---------- | ---------- |
| RED LED        | LED Pin |                 |            |            |            |
| IR Transmitter |         | Transmitter Pin |            |            |            |
| BUTTON A       |         |                 | Button Pin |            |            |
| BUTTON B       |         |                 |            | Button Pin |            |
| Buzzer         |         |                 |            |            | Buzzer Pin |

**TFT LCD**

Driver IC:ST7789v2

Resolution:135 \* 240

| ESP32   | GPIO15    | GPIO13   | GPIO23  | GPIO18   | GPIO5   |
| ------- | --------- | -------- | ------- | -------- | ------- |
| TFT LCD | TFT\_MOSI | TFT\_CLK | TFT\_DC | TFT\_RST | TFT\_CS |

**GROVE PORT**

| ESP32      | GPIO33 | GPIO32 | 5V | GND |
| ---------- | ------ | ------ | -- | --- |
| GROVE port | SCL    | SDA    | 5V | GND |

**MIC (SPM1423)**

| ESP32      | GPIO0 | GPIO34 |
| ---------- | ----- | ------ |
| MICROPHONE | CLK   | DATA   |

**6-Axis posture sensor (MPU6886) & power management IC (AXP192)**

| ESP32               | GPIO22 | GPIO21 |
| ------------------- | ------ | ------ |
| 6-Axis IMU sensor   | SCL    | SDA    |
| Power management IC | SCL    | SDA    |

**AXP192**

| Microphone | RTC  | TFT backlight | TFT IC | ESP32/3.3V MPU6886 | 5V GROVE |
| ---------- | ---- | ------------- | ------ | ------------------ | -------- |
| LDOio0     | LDO1 | LDO2          | LDO3   | DC-DC1             | IPSOUT   |

**Power structure block diagram**

![](https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc_plus/m5stickc_plus_sch_01.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc_plus/m5stickc_plus_sch_02.webp)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc_plus/m5stickc_plus_sch_03.webp" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/m5stickc_plus/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [StickC-Plus](https://docs.m5stack.com/en/core/StickC-Plus) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K016-P`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need               | Model-specific reference                                                                                                                 |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial   | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5stickc_plus/program)                                           |
| Mechanical / CAD files         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K016-P_StickC-Plus/Structures)                 |
| Mechanical / CAD files         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K016-P_StickC-Plus/Structures/StickC-Plus.stl) |
| Official source: M5StickC-Plus | [Read official source: m5stickc-plus](https://github.com/m5stack/M5StickC-Plus)                                                          |
| Example source: M5StickC-Plus  | [Read example source: m5stickc-plus](https://github.com/m5stack/M5StickC-Plus/tree/master/examples/FactoryTest)                          |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
