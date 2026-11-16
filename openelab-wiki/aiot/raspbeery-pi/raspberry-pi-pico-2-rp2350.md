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

# Raspberry Pi Pico 2 RP2350

### Raspberry Pi Pico 2 RP2350

***

{% embed url="https://openelab.io/products/raspberry-pi-pico-2-rp2350" %}

### Introduction

The Raspberry Pi Pico 2 RP2350 is the latest iteration of the popular Raspberry Pi Pico series, designed to bring even more power and versatility to your projects. Building on the success of its predecessor, the Pico 2 RP2350 features the new RP2350 microcontroller, offering enhanced processing capabilities and additional features for makers, hobbyists, and engineers. The board is compact, affordable, and designed for a wide range of applications, from simple hobby projects to more complex embedded systems. As of now, the Raspberry Pi Pico 2 RP2350 is available for pre-order, providing an exciting opportunity to be among the first to explore its capabilities.

### Features

* Optional boot signing, enforced by on-chip mask ROM, with key fingerprint in OTP
* Protected OTP storage for optional boot decryption key
* Global bus filtering based on Arm or RISC-V security/privilege levels
* Peripherals, GPIOs, and DMA channels individually assignable to security domains
* Hardware mitigations for fault injection attacks
* Hardware SHA-256 accelerator

### Specifications

* Dual Arm Cortex-M33 or dual Hazard3 processors @ 150MHz
* 520 KB on-chip SRAM
* Software- and hardware-compatible with Raspberry Pi Pico 1
* Drag-and-drop programming using mass storage over USB
* Castellated module allows soldering direct to carrier boards
* 2 × UART
* 2 × SPI controllers
* 2 × I2C controllers
* 24 × PWM channels
* 4 x ADC channels
* 1 × USB 1.1 controller and PHY, with host and device support
* 12 × PIO state machines
* Open source C/C++ SDK, MicroPython support
* Operating temperature -20°C to +85°C
* Supported input voltage 1.8–5.5V DC

### Pinout

<figure><img src="../../.gitbook/assets/image (874).png" alt=""><figcaption></figcaption></figure>

### Dimensions

* **Board Size**: 21 x 51 mm
* **Thickness**: 3.5 mm
* **Weight**: 4 grams

### How to Use

* **Setup the Development Environment**:
  * Install the latest version of the Arduino IDE or use the official Raspberry Pi Pico SDK.
  * Add the RP2350 board support package to your environment.
  * Select the Raspberry Pi Pico 2 RP2350 from the tools menu and the appropriate COM port.
* **Powering the Board**:
  * Connect the board to your computer or a power source using a USB Type-C cable.
  * The board will power up, and you can start programming.
* **Programming**:
  * Write your code in C/C++ using the Pico SDK or use MicroPython for rapid prototyping.
  * Upload your code to the board and test it.
* **Interfacing with External Components**:
  * Use the GPIO pins to connect sensors, LEDs, motors, and other peripherals.
  * Take advantage of the available interfaces (SPI, I2C, UART) for more complex connections.
* **Debugging**:
  * Utilize the onboard debugging features for step-by-step debugging to troubleshoot your code.
  * Access the debug pins if additional debugging tools are required.

### FAQ

<details>

<summary><strong>What is the difference between the RP2350 and the RP2040?</strong></summary>

&#x20;The RP2350 is an upgraded version of the RP2040, featuring enhanced processing power with dual Arm Cortex-M33 cores, more GPIOs, and additional functionalities like PIO.

</details>

<details>

<summary><strong>Can I use Raspberry Pi Pico accessories with the Pico 2 RP2350?</strong></summary>

Yes, the Raspberry Pi Pico 2 RP2350 is designed to be compatible with existing Raspberry Pi Pico accessories.

</details>

<details>

<summary><strong>How do I power the Raspberry Pi Pico 2 RP2350?</strong></summary>

You can power it via the USB Type-C connector or through an external 3.3V power supply.

</details>

<details>

<summary><strong>Is the Raspberry Pi Pico 2 RP2350 suitable for battery-powered projects?</strong></summary>

Yes, the board's low power consumption makes it well-suited for battery-powered and portable applications.

</details>

<details>

<summary><strong>When will the Raspberry Pi Pico 2 RP2350 be available?</strong></summary>

The board is currently available for pre-order, with an expected shipping date depending on production and availability.

</details>

&#x20;
