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

# M5Stack M5Stamp C3 (5pcs)

{% hint style="info" %}
[**View M5Stack Stamp-C3 ESP32-C3 RISC-V IoT Module (5pcs) on OpenELAB**](https://openelab.io/products/m5stamp-c3)

**Store SKU / option:** `M5-C056-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack M5Stamp C3 (5pcs)

***

### Product Link

{% embed url="https://openelab.io/products/m5stamp-c3" %}

### Description <a href="#description" id="description"></a>

M5Stack just added a new family to its popular series of modules with the Stamp-C3. the new Stamp-C3 featuring ESPRESSIF ESP32-C3 `RISC-V` MCU with `Wi-Fi` connectivity for IoT edge devices such as home appliances and Industrial Automation. By combining RSA-3072-based secure boot and the AES-128-XTS-based flash encryption, while also make it optimal for industrial IoT equipment collecting sensor data within a factory or a building.

The Stamp-C3 is based on `32-bit RISC-V` micro controller and operates at a maximum clock frequency of `160 MHz`. With 400 KB of internal RAM and `4 MB Flash`, it can facilitate many different use-cases involving connected devices. Furthermore, the exceptional heat resistance plastic enclosure is sustained at a higher operating temperature.

### Features <a href="#features" id="features"></a>

* MULTIPLE STYLE:
  * Three types soldering options are available(SMT, DIP, fly wire), with a high-temperature resistant plastic enclosure, Peak temperature = 230℃
* HIGH INTEGRATION:
  * Stamp-C3 contains 5V->3.3V DC/DC design, GPIOx13, programmable RGB LED x1, Reset button x1, button x1, 3D antenna,providing stable and reliable wireless communication.
* LOW-CODE DEVELOPMENT:
  * Stamp-C3 fully compatible with Arduino, ESP32-IDF, and other mainstream development platforms to quickly build various applications. (UIFlow support coming soon)

### Applications <a href="#applications" id="applications"></a>

* DIY Prototyping
* Home Appliances
* Industrial Automation

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
| IO interface x13                      | G21, G20, G9, G18, G19, G1, G0, G10, G8, G7, G6, G5, G4                                                 |
| IO interface spacing                  | 2.54mm                                                                                                  |
| Fixing screw specifications           | M2\*4 countersunk head hexagon socket mechanical teeth                                                  |
| Net weight                            | 3.8g                                                                                                    |
| Product size                          | 34 x 20 x 4.6mm                                                                                         |
| Packing size                          | 136 x 92 x 5mm                                                                                          |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="../../.gitbook/assets/image (977).png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="../../.gitbook/assets/image (980).png" alt=""><figcaption></figcaption></figure>

**SK6812 (RGB LED) and Button**

| ESP32  | GPIO2 | GPIO3 |
| ------ | ----- | ----- |
| SK6812 | DI    | /     |
| Button | /     | SW    |

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="../../.gitbook/assets/image (981).png" alt=""><figcaption></figcaption></figure>

### The shell supports Reflow Profile <a href="#the-shell-supports-reflow-profile" id="the-shell-supports-reflow-profile"></a>

<figure><img src="../../.gitbook/assets/image (982).png" alt=""><figcaption></figcaption></figure>

### Product Comparison <a href="#product-comparison" id="product-comparison"></a>

<figure><img src="../../.gitbook/assets/image (983).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Stamp-C3](https://docs.m5stack.com/en/core/Stamp-C3) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`C056-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                           |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5stampc3/program)                                         |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/C056-B_Stamp-C3/Structures)              |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/C056-B_Stamp-C3/Structures/Stamp-C3.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
