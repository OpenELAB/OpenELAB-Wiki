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

# M5Stamp ESP32S3

### M5Stack M5Stamp ESP32S3 Module

***

### Product Link

Current OpenELAB.io listing: M5StampS3 versions with 1.27 mm or 2.54 mm header pins. Select the required connector option.

{% embed url="https://openelab.io/products/m5stack-m5stamps3" %}

### Description <a href="#description" id="description"></a>

STAMPS3 is a highly integrated embedded controller designed for IoT applications. It utilizes the Espressif ESP32-S3FN8 main control chip and features 8MB of SPI flash memory. Powered by a high-performance Xtensa 32-bit LX7 dual-core processor, STAMPS3 delivers impressive processing power with a main frequency of up to 240MHz. This module is specifically designed to meet the demands of IoT projects that require embedded main control modules.

STAMPS3 comes equipped with a built-in highly integrated 5V to 3.3V circuit, ensuring stable power supply for reliable operation. It features an RGB status indicator and a programmable button for enhanced user control and visual feedback. The module conveniently leads out 23 GPIOs on the ESP32-S3, allowing for extensive expansion capabilities. The GPIOs are accessible through 1.27mm/2.54mm spacing leads, supporting various usage methods such as SMT, DIP row, and jump wire connections. STAMPS3 offers a compact form factor, delivering strong performance, rich expansion IO, and low power consumption.

STAMPS3 is the ideal choice for IoT application scenarios that require the integration of embedded controllers. Its compact volume and powerful features make it suitable for a wide range of projects, providing reliable performance and flexible expansion options.

### Features <a href="#features" id="features"></a>

* ESP32-S3FN8(2.4GHz Wi-Fi)
* Minimal system board
* Multi-IO lead-out, support multiple application forms (SMT, DIP, flying wire)
* Integrated programmable RGB LEDs and buttons
* Support UIFlow graphical programming

### Applications <a href="#applications" id="applications"></a>

* Smart home
* Wearables
* Medical equipment

### Specification <a href="#specification" id="specification"></a>

<table><thead><tr><th width="243">Resources</th><th>Parameters</th></tr></thead><tbody><tr><td>MCU</td><td>ESP32-S3FN8</td></tr><tr><td>DCDC</td><td>Highly integrated MUN3CAD01-SC</td></tr><tr><td>Flash</td><td>8MB</td></tr><tr><td>Input voltage</td><td>5V</td></tr><tr><td>Interactive</td><td>Programmable physical buttons x 1, programmable RGB LED (WS2812B-2020) x 1</td></tr><tr><td>Antenna type</td><td>2.4G 3D antenna</td></tr><tr><td>Module resource interface</td><td>Touch sensor, SD/SDIO/MMC master controller, SPI, SDIO/SPI slave controller, EMAC, motor PWM, LED PWM, UART, I2C, I2S, GPIO, pulse counter</td></tr><tr><td>IO interface x23</td><td>G0/G1/G2/G3/G4/G5/G6/G7/G8/G9/G10/G11/G12/G13/G14/G15/G39/G40/G41/G42/G43/G44/G46</td></tr><tr><td>Connection method</td><td>SMT/DIP (pitch 2.54mm and 1.27mm)/Jump Wire</td></tr><tr><td>IO interface spacing</td><td>2.54mm和1.27mm</td></tr><tr><td>lcd interface spacing</td><td>0.5mm@12pin or 8pin</td></tr><tr><td>Operating temperature</td><td>0°C to 40°C</td></tr><tr><td>Product Size</td><td>26mm × 18mm × 4.6mm</td></tr><tr><td>Package Size</td><td>136mm × 92mm × 13mm</td></tr><tr><td>Product Weight</td><td>3.2g</td></tr><tr><td>Package Weight</td><td>7.5g</td></tr></tbody></table>

![](https://static-cdn.m5stack.com/resource/docs/products/core/StampS3/img-a8f7e59f-bd84-470a-99f3-172b38d3ec6f.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/StampS3/img-4fe7e00d-6a3e-414c-bd03-805fb0089f0d.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/StampS3/img-f2652c40-0376-468d-9c2f-a9bc4fdee211.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/StampS3/img-4aaf7195-c36f-4576-aba4-e30405195f3b.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/StampS3/img-c69bd4fd-8ca3-43b5-b8cb-aa9c6e1b941e.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/StampS3/img-75d61153-2094-4567-8076-dc60a6d02c72.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [ESP32-S3](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/atombase/ATOMS3/esp32-s3_datasheet_cn.pdf)
* [MUN3CAD01-SC](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/Stamp/S007%20StampS3/MUN3CAD01-SC.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/StampS3/img-b18b0819-2154-4bb3-9389-88e5df2ac7ca.png" alt=""><figcaption></figcaption></figure>

* [Schematic pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/Stamp/S007%20StampS3/Sch_M5StampS3_v0.2.pdf)

Bottom of PCB reserved TFT screen SPI interface，FPC connector check [8PIN ](https://so.szlcsc.com/global.html?k=C2919492\&hot-key=ADM3053BRWZ-REEL7)和 [12PIN ](https://so.szlcsc.com/global.html?k=C2919494\&hot-key=ADM3053BRWZ-REEL7)specification。

### PCB package <a href="#pcb-package" id="pcb-package"></a>

* [kicad PCB package](https://github.com/m5stack/M5_Hardware/tree/master/KiCAD/M5KiCad/M5KiCad.pretty)

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/StampS3/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [StampS3 Arduino Example](https://github.com/m5stack/STAMP-S3/blob/main/examples/Led/Led.ino)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/StampS3/arduinoCase-1673423464987M5PPT.png" alt=""><figcaption></figcaption></figure>

### Compare <a href="#compare" id="compare"></a>

<figure><img src="../../.gitbook/assets/image (409).png" alt=""><figcaption></figcaption></figure>
