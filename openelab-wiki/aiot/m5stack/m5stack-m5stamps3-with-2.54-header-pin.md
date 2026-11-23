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

# M5Stack M5StampS3 with 2.54 Header Pin

{% hint style="info" %}
[**View M5Stack M5StampS3 ESP32-S3 Module with 1.27 / 2.54 Header Pin on OpenELAB**](https://openelab.io/products/m5stack-m5stamps3)

**Store SKU / option:** `M5-S007-PIN127`, `M5-S007-PIN254`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack M5StampS3 with 1.27/2.54 Header Pin

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-m5stamps3?variant=43959542546630" %}

### Description <a href="#description" id="description"></a>

**M5StampS3 PIN2.54** is a highly integrated embedded main control core module, using Espressif **ESP32-S3FN8** chip,included **8MSPI flash memory**, equipped with high-performance Xtensa 32-bit LX7 dual-core processor, main frequency up to 240MHz. Built-in highly integrated 5V to 3.3V circuit, **RGB status indicator**, **programmable button**, module leads out **10 GPIOs on ESP32-S3**, and it leads out in the form of **2.54MM** spacing needle; The product features compact volume, strong performance, rich expansion IO and low power consumption. The module is suitable for **IoT application scenarios with embedded main control modules**.

If you want to enter download mode, press and hold the G0 button on StampS3 before turning it on, then release it after powering it on.GPIO46 is drop-down by default.

### Features <a href="#features" id="features"></a>

* ESP32-S3FN8(2.4GHz Wi-Fi)
* Integrated programmable RGB LED and button
* 2.54mm pin header
* Support UIFlow graphical programming

### Applications <a href="#applications" id="applications"></a>

* Smart home
* Wearables
* Medical equipment

### Specification <a href="#specification" id="specification"></a>

| Resources                 | Parameters                                                                                                                                 |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| MCU                       | ESP32-S3FN8                                                                                                                                |
| DCDC                      | Highly integrated MUN3CAD01-SC                                                                                                             |
| Flash                     | 8MB                                                                                                                                        |
| Input voltage             | 5V                                                                                                                                         |
| Interactive               | Programmable physical buttons x 1, programmable RGB LED (WS2812B-2020) x 1                                                                 |
| Antenna type              | 2.4G 3D antenna                                                                                                                            |
| Module resource interface | Touch sensor, SD/SDIO/MMC master controller, SPI, SDIO/SPI slave controller, EMAC, motor PWM, LED PWM, UART, I2C, I2S, GPIO, pulse counter |
| IO interface x23          | G0/G1/G2/G3/G4/G5/G6/G7/G8/G9/G10/G11/G12/G13/G14/G15/G39/G40/G41/G42/G43/G44/G46                                                          |
| Pin header spacing        | 2.54mm                                                                                                                                     |
| lcd interface spacing     | 0.5mm@12pin or 8pin                                                                                                                        |
| Operating temperature     | 0°C to 40°C                                                                                                                                |
| Product Size              | 26\*18\*4.6mm                                                                                                                              |
| Package Size              | 74\*48\*13mm                                                                                                                               |
| Product Weight            | 3.5g                                                                                                                                       |
| Package Weight            | 6.3g                                                                                                                                       |

![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/M5StampS3%20PIN2.54/9.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/M5StampS3%20PIN2.54/14.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/M5StampS3%20PIN2.54/15.webp)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/M5StampS3%20PIN2.54/img-9adafa51-bd7b-4f8a-b479-9871d98140f2.png" alt=""><figcaption></figcaption></figure>

### LABEL <a href="#label" id="label"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/M5StampS3%20PIN2.54/254.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/StampS3/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Stamp-S3 PIN1.27](https://docs.m5stack.com/en/core/Stamp-S3_PIN1.27) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`S007-PIN127`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                                |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5stamps3/program)                                                              |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/509/Sch_M5StampS3_v0.2.pdf)                                                |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/KiCad/3D/M5Stack.3dshapes/Stamp-S3.step)                               |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/S007-PIN127_Stamp-S3_PIN1.27/Structures)                      |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/S007-PIN127_Stamp-S3_PIN1.27/Structures/Stamp-S3_PIN1.27.stl) |
| Example source: Led.ino      | [Read example source: led.ino](https://github.com/m5stack/STAMP-S3/blob/main/examples/Led/Led.ino)                                                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
