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

# XIAO RP2350 Raspberry Pi

{% hint style="info" %}
[**View Seeed Studio XIAO RP2350 Raspberry Pi RISC-V 19 GPIOs Onboard RGB LED on OpenELAB**](https://openelab.io/products/xiao-rp2350)

**Store SKU / option:** `Seeed-102010550`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Seeed Studio XIAO RP2350 Raspberry Pi RISC-V 19 GPIOs Onboard RGB LED

***

### Product Link

{% embed url="https://openelab.io/products/xiao-rp2350" %}

### Description

The XIAO RP2350 packs the power of the Raspberry Pi RP2350 (dual Cortex-M33 cores running at 150MHz with FPU, enhanced security and encryption) into the classic XIAO form factor. Measuring just 21x17.8mm, it features 19 multifunction GPIOs, an RGB LED, and a Battery Management System with ultra-low power consumption of 50μA, battery power supply, and direct battery voltage measurement. Thanks to the XIAO ecosystem, the XIAO RP2350 is compatible with a wide range of add-ons, including displays, LED matrix, Grove modules, CAN Bus, Vision AI sensors, and mmWave sensors. With native support for MicroPython, C, and C++, the XIAO RP2350 is perfect for developers of all levels looking to create compact, battery-powered applications for smart control, wearables, DIY keyboards, and more.

### Features[​](https://wiki.seeedstudio.com/getting-started-xiao-rp2350/#features) <a href="#features" id="features"></a>

* **Powerful MCU Board:** Equipped with a Raspberry Pi RP2350 chip featuring symmetric dual Arm Cortex-M33 @ 150MHz with FPU.
* **Enhanced Security Features:** Built-in secure boot and encrypted bootloader ensure application security.
* **Software Support:** Compatible with C/C++ and MicroPython, ensuring easy project development and prototyping.
* **Rich Onboard Resources:** Integrates an RGB LED, 2MB Flash, 520kB SRAM, and 19 multifunction GPIOs(Analog, Digital, I²C, UART, SPI, PWM).
* **Expanded 8 New IOs:** Compared to previous XIAO MCUs, the addition of 8 IO pins on the back supports more complex applications.
* **Efficient Power Design:** Ultra-low power consumption of just 50μA in sleep mode, enabling battery power supply. Direct battery voltage measurement via internal IO enhances the battery management system (BMS).
* **Compact Thumb-Sized Design:** Measuring 21 x 17.8mm, adopting Seeed Studio's classic XIAO form factor, ideal for space-conscious applications.
* **Production-friendly:** Surface Mount Device (SMD) design with all components on the front and stamp holes on both sides, facilitating efficient mass production.

### Specification[​](https://wiki.seeedstudio.com/getting-started-xiao-rp2350/#specification) <a href="#specification" id="specification"></a>

| Product                  | XIAO RP2040                                                     | XIAO RP2350                                                     |
| ------------------------ | --------------------------------------------------------------- | --------------------------------------------------------------- |
| Processor                | Raspberry Pi RP2040                                             | Raspberry Pi RP2350                                             |
| Dual Cortex-M0+ @ 133MHz | Dual Cortex-M33 @ 150MHz, FPU                                   |                                                                 |
| RAM                      | 264kB SRAM                                                      | 520kB SRAM                                                      |
| Flash                    | 2MB Onboard                                                     | 2MB Flash                                                       |
| LEDs                     | 1 user LED(3 colors), 1 power LED, 1 RGB LED                    | 1 user LED, 1 charge LED(Battery Charging Indicator)，1 RGB LED  |
| Interface                | 11 Pins:4x Analog,11x Digital, 1x I²C, 1x UART, 1x SPI, All PWM | 19 Pins:3x Analog,19x Digital, 2x I²C, 2x UART, 2x SPI, All PWM |
| Button                   | 1 RESET button, 1 BOOT button                                   |                                                                 |
| Security                 | -                                                               | OTP, Secure Boot, Arm TrustZone                                 |
| Low power                | -                                                               | 4.2V/50uA                                                       |
| Software compatibility   | Arduino, PlatformIO, MicroPython, CircuitPython, Zephyr         | Arduino, PlatformIO, MicroPython, CircuitPython                 |
| Working Temperature      | -20°C\~70°C                                                     |                                                                 |
| Dimensions               | 21x17.8 mm                                                      |                                                                 |

### Hardware <a href="#hardware-overview" id="hardware-overview"></a>

| XIAO RP2350 Front Pinout                                                                                                                    |
| ------------------------------------------------------------------------------------------------------------------------------------------- |
| <img src="https://files.seeedstudio.com/wiki/XIAO-RP2350/img/XIAO-RP2350-front.png" alt="XIAO RP2350 Front Pinout" data-size="original">    |
| XIAO RP2350 Back Pinout                                                                                                                     |
| <img src="https://files.seeedstudio.com/wiki/XIAO-RP2350/img/XIAO-RP2350-back.png" alt="XIAO RP2350 Back Pinout" data-size="original">      |
| XIAO RP2350 Components                                                                                                                      |
| <img src="https://files.seeedstudio.com/wiki/XIAO-RP2350/img/XIAO-RP2350-components.png" alt="XIAO RP2350 Components" data-size="original"> |

## Official documentation and development resources

Use [Seeed Studio XIAO RP2350 With MicroPython](https://wiki.seeedstudio.com/getting-started-xiao-rp2350/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need                  | Model-specific reference                                                                   |
| --------------------------------- | ------------------------------------------------------------------------------------------ |
| Official source: OSHW-XIAO-Series | [Read official source: oshw-xiao-series](https://github.com/Seeed-Studio/OSHW-XIAO-Series) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
