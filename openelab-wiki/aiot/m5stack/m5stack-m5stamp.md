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

# M5Stack M5Stamp

### M5Stack M5Stamp C3U Mate with Pin Headers

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-m5stamp-c3u" %}

### Description <a href="#description" id="description"></a>

The newly M5Stamp C3U featuring ESPRESSIF ESP32-C3 RISC-V MCU, with Wi-Fi 5 (LE) connectivity, applicable for home appliances and Industrial Automation. By combining RSA-3072-based secure boot and the AES-128-XTS-based flash encryption. The compact size and powerful functions, make it applicable for multiple IoT scenarios.

The M5Stamp C3U is based on 32-bit RISC-V micro controller, and operates at a maximum clock frequency of 160 MHz. With 400 KB of internal RAM and 4 MB Flash, it can facilitate many different use cases, involving connected devices. The M5Stamp C3U provides, Furthermore, the exceptional heat resistance plastic enclosure is sustained at a higher operating temperature.

### Features <a href="#product-features" id="product-features"></a>

* MULTIPLE STYLE:
  * Three types soldering options are available (SMT, DIP, fly wire);
  * High-temperature resistant plastic enclosure, Peak temperature = 230℃;
* HIGH INTEGRATION:
  * M5Stamp C3 contains 5V->3.3V DC/DC design, GPIOx14;
  * USB Type C port;
  * Programmable RGB LED x1, Reset button x1, button x1;
  * 3D antenna, providing stable and reliable wireless communication.
* DEVELOPMENT PLATFORM:
  * Arduino, ESP32-IDF (UIFlow support coming soon)

### Application <a href="#application" id="application"></a>

* DIY, Prototyping
* Industrial Automation
* Smart Home
* Wearable Devices
* Medical Devices
* Consumer Electronics

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications                        | Parameters                                                                                              |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| ESP32-C3                              | 32bit RISC-V single-core processor, clocked at 160 MHz                                                  |
| Storage                               | 384KB ROM, 400KB SRAM, 8KB RTC SRAM, 4MB FLASH                                                          |
| Wi-Fi                                 | 2.4 GHz band supports 20 MHz and 40 MHz bandwidth, IEEE 802.11 b/g/n protocol, data rate up to 150 Mbps |
| Input voltage                         | 5V @ 500mA                                                                                              |
| HMI                                   | Programmable physical button x 1, reset debugging button x 1, programmable RGB LED (SK6812) x 1         |
| USB interface                         | TypeC x1                                                                                                |
| Antenna Type                          | 2.4G 3D Antenna                                                                                         |
| Module peripheral interface resources | ADC, GPIO, SPI, UART, I2C, I2S, PWM, RMT, DMA, USB serial port, TWAI                                    |
| IO interface x14                      | G0, G1, G3, G4, G5, G6, G7, G8, G9, G10, G18, G19, G21, G22                                             |
| IO interface spacing                  | 2.54mm                                                                                                  |
| Fixing screw specifications           | M2\*4 countersunk head hexagon socket mechanical teeth                                                  |
| Net weight                            | 3.8g                                                                                                    |
| Product size                          | 34 \* 20 \* 4.6mm                                                                                       |
| Packing size                          | 85\*55mm sealing bag (translucent)                                                                      |

![](https://static-cdn.m5stack.com/resource/docs/products/core/stamp_c3u/stamp_c3u_06.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/stamp_c3u/stamp_c3u_07.webp)![](https://static-cdn.m5stack.com/resource/docs/products/core/stamp_c3u/stamp_c3u_08.webp)

### product comparison <a href="#product-comparison" id="product-comparison"></a>

| Model     | Master   | IO quantity | Button IO | USB chip | USB interface function       |
| --------- | -------- | ----------- | --------- | -------- | ---------------------------- |
| STAMP-C3  | ESP32-C3 | 13          | G3        | CH9102   | Download / Serial            |
| STAMP-C3U | ESP32-C3 | 14          | G9        | /        | Download / JTAG / CDC Serial |

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/stamp_c3u/stamp_c3u_09.webp" alt=""><figcaption></figcaption></figure>

**SK6812 (RGB LED) and Button**

| ESP32  | GPIO2 | GPIO9 |
| ------ | ----- | ----- |
| SK6812 | DI    | /     |
| Button | /     | SW    |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/stamp_c3u/stamp_c3u_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Module size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/stamp_c3u/stamp_c3&#x26;c3u_size_01.webp" alt=""><figcaption></figcaption></figure>
