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

# XIAO RP2350 Onboard RGB LED, Arm Cortex-M33 and Hazard3 RISC-V(Pre-Order)

{% hint style="info" %}
[**View Seeed Studio XIAO RP2350 Raspberry Pi RISC-V 19 GPIOs Onboard RGB LED on OpenELAB**](https://openelab.io/products/xiao-rp2350)

**Store SKU / option:** `Seeed-102010550`. Match the purchased model and revision to the official reference below.
{% endhint %}

### XIAO RP2350 Onboard RGB LED, Arm Cortex-M33 and Hazard3 RISC-V(Pre-Order)

***

### Product Link

{% embed url="https://openelab.io/products/xiao-rp2350" %}

### Introduction

The XIAO RP2350 is an innovative development board that combines the power of the Arm Cortex-M33 and the Hazard3 RISC-V cores, offering a versatile platform for developers interested in both traditional and RISC-V architectures. This board is particularly appealing for projects that require low power consumption, advanced processing capabilities, and a compact form factor. Additionally, it features an onboard RGB LED, which can be used for various indications and effects in your projects.

### Features

* **Powerful MCU Board:** Equipped with a Raspberry Pi RP2350 chip featuring dual-core, dual-architecture capability, allowing developers to switch between the dual industry-standard Arm Cortex-M33 cores @ 150MHz with FPU, and a pair of open-hardware Hazard3 RISC‑V cores
* **Enhanced Security Features:** Built-in secure boot and encrypted bootloader ensure application security.
* **Software Support:** Compatible with C/C++ and MicroPython, ensuring easy project development and prototyping.
* **Rich Onboard Resources:** Integrates an RGB LED, 2MB Flash, 520kB SRAM, and 19 multifunction GPIOs(Analog, Digital, I²C, UART, SPI, PWM).
* **Expanded 8 New IOs:** Compared to previous XIAO MCUs, the addition of 8 IO pins on the back supports more complex applications.
* **Efficient Power Design**: Ultra-low power consumption of just 27μA in sleep mode, enabling battery power supply. Direct battery voltage measurement via internal IO enhances the battery management system (BMS).
* **Compact Thumb-Sized Design:** Measuring 21 x 17.5mm, adopting Seeed Studio's classic XIAO form factor, ideal for space-conscious applications.
* **Production-friendly:** Surface Mount Device (SMD) design with all components on the front and stamp holes on both sides, facilitating efficient mass production.

### Specifications

| **Product**              | XIAO RP2040                                                                   | XIAO RP2350                                                                   |
| ------------------------ | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- |
| Processor                | Raspberry Pi RP2040                                                           | Raspberry Pi RP2350                                                           |
| Dual Cortex-M0+ @ 133MHz | Dual Cortex-M33 @ 150MHz, FPU                                                 |                                                                               |
| RAM                      | 264kB SRAM                                                                    | 520kB SRAM                                                                    |
| Flash                    | 2MB Onboard                                                                   | 2MB PSRAM                                                                     |
| LEDs                     | 1 user LED, 1 power LED, two LEDs for serial port downloading, 1 RGB LED      | 1 user LED, 1 power LED，1 RGB LED                                             |
| Interface                | <p>11 Pins:</p><p>4x Analog,11x Digital, 1x I²C, 1x UART, 1x SPI, All PWM</p> | <p>19 Pins:</p><p>3x Analog,19x Digital, 2x I²C, 2x UART, 2x SPI, All PWM</p> |
| Button                   | 1 RESET button, 1 BOOT button                                                 | 1 RESET button, 1 BOOT button                                                 |
| Security                 | -                                                                             | OTP, Secure Boot, Arm TrustZone                                               |
| Low power                | -                                                                             | 27μA                                                                          |
| Software compatibility   | Support Micropython / Arduino / CircuitPython                                 | Support Micropython / C,C++                                                   |
| Working Temperature      | -20°C-70°C                                                                    | -20°C-70°C                                                                    |
| Dimensions               | 21x17.5 mm                                                                    | 21x17.5 mm                                                                    |

### Pinout

<figure><img src="../../.gitbook/assets/image (463).png" alt=""><figcaption></figcaption></figure>

### Dimensions

* **Board Size**: 21 x 17.5 mm
* **Thickness**: 3.5 mm
* **Weight**: 3 grams

### How to Use

* **Setup the Development Environment**:
  * Install the latest version of Arduino IDE or PlatformIO.
  * Add the RP2350 board library to your environment.
  * Select the correct board and port from the tools menu.
* **Powering the Board**:
  * Connect the board to your computer using a USB Type-C cable.
  * The board will be powered, and you can start uploading your code.
* **Programming**:
  * Write your code in Arduino IDE or PlatformIO.
  * Utilize the dual-core architecture by assigning tasks to either the Cortex-M33 or the Hazard3 RISC-V core.
  * Upload the code to the board and observe the results.
* **Controlling the RGB LED**:
  * Use the dedicated LED pins or predefined functions to control the onboard RGB LED.
  * Set the LED to different colors to indicate various statuses or effects.
* **Interfacing with Sensors and Actuators**:
  * Utilize the GPIO pins to connect sensors and actuators.
  * Use the analog and digital pins for reading sensor data and controlling devices.

### FAQ

<details>

<summary><strong>How do I switch between the Cortex-M33 and Hazard3 RISC-V cores?</strong></summary>

You can assign specific tasks to each core through your code, utilizing the libraries that support dual-core processing.

</details>

<details>

<summary><strong>How do I control the onboard RGB LED?</strong></summary>

The RGB LED can be controlled via the dedicated pins or using predefined functions in the board's library.

</details>

<details>

<summary><strong>What power supply options are available?</strong></summary>

The board can be powered through the USB Type-C connector or an external 3.3V supply.

</details>

<details>

<summary><strong>Is the XIAO RP2350 suitable for battery-powered applications?</strong></summary>

Yes, the board's low power consumption makes it ideal for battery-operated projects.

</details>

<details>

<summary><strong>When will the XIAO RP2350 be available for purchase?</strong></summary>

The board is currently available for pre-order, with shipping dates dependent on production schedules.

</details>

## Official documentation and development resources

Use [Seeed Studio XIAO RP2350 With MicroPython](https://wiki.seeedstudio.com/getting-started-xiao-rp2350/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need                  | Model-specific reference                                                                   |
| --------------------------------- | ------------------------------------------------------------------------------------------ |
| Official source: OSHW-XIAO-Series | [Read official source: oshw-xiao-series](https://github.com/Seeed-Studio/OSHW-XIAO-Series) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
