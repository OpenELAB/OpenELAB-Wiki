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

# XIAO RA4M1 Smallest Dev Board

{% hint style="info" %}
[**View Seeed Studio XIAO RA4M1 Smallest Dev Board on OpenELAB**](https://openelab.io/products/seeed-studio-xiao-ra4m-smallest-dev-board-based)

**Store SKU / option:** `Seeed-102010551`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Seeed Studio XIAO RA4M1 Smallest Dev Board

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-ra4m-smallest-dev-board-based" %}

### Description

The XIAO RA4M1 integrates Renesas' RA4M1 chip (32-bit ARM® Cortex®-M4 MCU up to 48 MHz) into the classic XIAO form factor. This development board offers 256KB Flash, 32KB SRAM, 8KB EEPROM, a USB 2.0 connector, reset and boot buttons, 3 LEDs, a 14-bit A/D converter, a 12-bit D/A converter, and a CAN BUS interface. With onboard charging circuitry and low-power modes (as low as 45μA), it’s ideal for battery-powered applications. Sharing the same 32-bit R7FA4M1AB3CFM microcontroller as the Arduino Uno R4, it's natively compatible with Arduino IDE and the extensive XIAO accessories, making it the perfect starting point for electronics projects.

### Features[​](https://wiki.seeedstudio.com/getting_started_xiao_ra4m1/#features) <a href="#features" id="features"></a>

* **Popular Microcontroller Onboard:** Powered by Renesas RA4M1, an 32-bit ARM® Cortex®-M4 R7FA4M1AB3CFM MCU operating at up to 48 MHz, 256 KB of Flash memory, and 32 KB of SRAM.
* **Highlighted Onboard Resources:** Equipped with a 14-bit ADC, 12-bit DAC, CAN BUS, USB 2.0, and an onboard RGB LED.
* **Expanded 8 New IOs:** Adds 8 new IO pins on the back compared to previous XIAO boards (19 GPIOs in total), enabling more complex applications.
* **Powerful Security Features:** Built-in hardware encryption, secure boot, key storage, and other functions to ensure application security.
* **Software Compatibility:** Fully compatible with Arduino IDE for seamless project development and prototyping.
* **Efficient Power Design:** Offers 4 operating modes with power consumption as low as 45μA in deep sleep, and supports lithium battery charge management.
* **Compact Thumb-Sized Design:** Measuring 21 x 17.8mm, adopting Seeed Studio's classic XIAO form factor, ideal for space-conscious applications.
* **Production-Friendly:** Surface Mount Device (SMD) design with all components on the front and stamp holes on both sides, facilitating efficient mass production.

### Specification[​](https://wiki.seeedstudio.com/getting_started_xiao_ra4m1/#specification) <a href="#specification" id="specification"></a>

| Product                     | XIAO RA4M1                                                                                                                                                                                       |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Processor                   | [Renesas RA4M1](https://www.renesas.com/us/en/products/microcontrollers-microprocessors/ra-cortex-m-mcus/ra4m1-32-bit-microcontrollers-48mhz-arm-cortex-m4-and-lcd-controller-and-cap-touch-hmi) |
| 48-MHz Arm® Cortex®-M4 Core |                                                                                                                                                                                                  |
| RAM                         | 32 KB SRAM                                                                                                                                                                                       |
| Flash                       | 256 KB                                                                                                                                                                                           |
| LEDs                        | 1 User LED, 1 Power LED, 1 RGB LED                                                                                                                                                               |
| Interfaces                  | 19 Pins:14x Analog,19x Digital, 2x IIC, 2x UART, 2x SPI                                                                                                                                          |
| Buttons                     | 1 RESET Button, 1 BOOT Button                                                                                                                                                                    |
| Security                    | AES128/256                                                                                                                                                                                       |
| Low Power                   | 45μA                                                                                                                                                                                             |
| Software Compatibility      | Arduino IDE                                                                                                                                                                                      |
| Working Temperature         | -20°C-70°C                                                                                                                                                                                       |
| Dimensions                  | 21x17.8 mm                                                                                                                                                                                       |
| Power                       | <p>Type-C: 5V<br>BAT: 3.8V</p>                                                                                                                                                                   |

### Hardware[​](https://wiki.seeedstudio.com/getting_started_xiao_ra4m1/#hardware-overview) <a href="#hardware-overview" id="hardware-overview"></a>

Before everything starts, it is quite essential to have some basic parameters of the product. The following table provides information about the characteristics of Seeed Studio XIAO RA4M1.

![](https://files.seeedstudio.com/wiki/XIAO-R4AM1/img/XIAO-RA4M1-components.png)

\
<br>

![](https://files.seeedstudio.com/wiki/XIAO-R4AM1/img/XIAO-RA4M1-pinout.png)

### BootLoader Mode[​](https://wiki.seeedstudio.com/getting_started_xiao_ra4m1/#bootloader-mode) <a href="#bootloader-mode" id="bootloader-mode"></a>

Sometimes, using the wrong program can cause the XIAO to lose its port or not function correctly. Common issues include:

* The XIAO is connected to the computer, but no port number is found.
* The XIAO is connected, and a port number appears, but the program upload fails.

When you encounter the above two situations, you can try to put XIAO into BootLoader mode, which can solve most of the problems of unrecognized devices and failed uploads. The specific method is:

* **Method 1.** Press and hold the `BOOT` button on the XIAO RA4M1 without releasing it.
* **Method 2.** Keep the `BOOT` button pressed and then connect to the computer via the data cable. Release the BOOT button after connecting to the computer.

### Reset[​](https://wiki.seeedstudio.com/getting_started_xiao_ra4m1/#reset) <a href="#reset" id="reset"></a>

When the program runs abnormally, you can press `Reset` once during power-up to let XIAO re-execute the uploaded program. When you press and hold the `BOOT` key while powering up and then press the `Reset` key once, you can also enter BootLoader mode.

## Official documentation and development resources

Use [Getting Started with Seeed Studio XIAO RA4M1](https://wiki.seeedstudio.com/getting_started_xiao_ra4m1/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                    |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://files.seeedstudio.com/arduino/package_renesas_1.2.0_index.json) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
