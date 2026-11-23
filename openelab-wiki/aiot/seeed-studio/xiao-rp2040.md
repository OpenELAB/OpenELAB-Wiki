---
description: >-
  Program standard XIAO RP2040 with Arduino Blink, bootloader recovery and
  correct standard-versus-Plus scope.
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

# XIAO RP2040

{% hint style="info" %}
[**View Seeed Studio XIAO RP2040 on OpenELAB**](https://openelab.io/products/xiao-rp2040-supports-arduino)

**Model:** standard XIAO RP2040 · **OpenELAB SKU:** `Seeed-102010428` · This guide does not cover the RP2040 Plus power-management hardware.
{% endhint %}

## Product overview

### Description

The standard XIAO RP2040 is a small RP2040 microcontroller board for USB-connected development and compact embedded projects. The official documentation now includes **RP2040 Plus** on the same page; its additional GPIO and battery-management features must not be transferred to this standard board. [Official series guide](https://wiki.seeedstudio.com/XIAO-RP2040/).

## Applications

Start with USB programming and the onboard user LED, then add one digital, analog or bus peripheral. For a custom carrier, distinguish XIAO pin labels such as D0 from the RP2040 GPIO number used by a library. Put that mapping in the project configuration so code review can catch a wrong pin before connection.

## Specifications

### Features

| Integration item    | Standard XIAO RP2040                       |
| ------------------- | ------------------------------------------ |
| Controller          | RP2040, dual Cortex-M0+, up to 133 MHz     |
| Memory              | 264 KB SRAM; 2 MB flash                    |
| Exposed digital I/O | 11; four also provide analog input         |
| Interfaces          | I2C, UART, SPI and SWD                     |
| Footprint           | 21 × 17.8 mm                               |
| GPIO logic          | 3.3 V; do not apply a higher input voltage |
| USB supply          | 5 V                                        |

Manufacturer values and standard/Plus comparison: [series specifications and hardware overview](https://wiki.seeedstudio.com/XIAO-RP2040/).

## Hardware and connections

Use a USB-C **data** cable initially. Disconnect external wiring for the first upload. The standard model does not acquire the Plus model's charger, extra pads or BAT\_EN connection because both use RP2040. Consult the exact board diagram before designing battery power or attaching a 5 V peripheral. [Power and GPIO cautions](https://wiki.seeedstudio.com/XIAO-RP2040/).

## Software and development resources

The current [official Arduino tutorial](https://wiki.seeedstudio.com/XIAO-RP2040-with-Arduino/) uses the `Raspberry Pi Pico/RP2040/RP2350` board package and the **Seeed Studio XIAO RP2040** target. Record the installed package release; the source requests the current package and does not establish one permanently fixed version. The official series also links MicroPython, CircuitPython, PlatformIO and other routes. Start with one working environment before comparing language implementations.

## Getting started

### Enter bootloader mode

1. Hold **BOOT** while connecting USB. Confirm that the computer exposes the **RPI-RP2** drive. This tests the bootloader connection, not the application.
2. In Arduino IDE preferences, add the manufacturer's documented board index:

```
https://github.com/earlephilhower/arduino-pico/releases/download/global/package_rp2040_index.json
```

3. In Boards Manager install `Raspberry Pi Pico/RP2040/RP2350`; select **Seeed Studio XIAO RP2040** and the connected board's port.
4. Open **File → Examples → 01.Basics → Blink**, build and upload. Keep peripherals disconnected while isolating upload/board-selection faults.

**Expected result:** the green user LED on GPIO25 blinks at the example's one-second cadence. If upload fails, hold BOOT and press RUN to return to boot mode, then select the resulting device again. [Arduino setup and expected result](https://wiki.seeedstudio.com/XIAO-RP2040-with-Arduino/). **Observed result:** not run.

### Proceed to interfaces

The [Arduino interface tutorial](https://wiki.seeedstudio.com/XIAO-RP2040-with-Arduino/) continues through digital input, ADC, PWM, I2C, UART and SPI. For each next task, write down the XIAO label, MCU GPIO, supply and expected value before wiring. Save a working Blink project as the host baseline. If a new peripheral fails, restore that baseline and reintroduce one connection at a time; this separates firmware, bus and sensor faults.

## Troubleshooting and FAQs

**Power light but no boot drive or upload port:** compare the cable, USB port and BOOT sequence before changing libraries. Check enumeration once with external wiring removed.

**Upload works but a peripheral fails:** compare the actual board diagram with the code's pin numbers and voltage levels. A package containing both standard and Plus targets does not mean the extra Plus pads exist on the standard board.

**An old project behaves differently after a package update:** record the previous and new package versions and build output. Re-test Blink before migrating the peripheral code. Keep expected behavior separate from observations made on the actual unit.

### Reset

Reset and bootloader entry serve different purposes. For upload recovery use the documented BOOT/RUN sequence above; keep the selected board and resulting port in the project record.

## Downloads and technical documents

### Schematics

| Reference                                                                              | What it covers                                                                                |
| -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| [Series guide and resources](https://wiki.seeedstudio.com/XIAO-RP2040/)                | Model differences, front/back diagrams, power limits, hardware documents and language choices |
| [Arduino setup and interfaces](https://wiki.seeedstudio.com/XIAO-RP2040-with-Arduino/) | Board package, BOOT/RUN, Blink and peripheral examples                                        |
| [MicroPython](https://wiki.seeedstudio.com/XIAO-RP2040-with-MicroPython/)              | Separate language/firmware route; verify its exact board support                              |
| [CircuitPython](https://wiki.seeedstudio.com/XIAO-RP2040-with-CircuitPython/)          | Separate runtime and module workflow                                                          |

## References and validation

Manufacturer pages reviewed **23 November 2026**. This is the main OpenELAB guide for the standard `Seeed-102010428` board. Earlier guide URLs remain available and link here. No build, firmware upload or physical test was performed. The official references retain the complete interface examples and diagrams; this guide adds the standard-versus-Plus boundary and a staged diagnostic workflow.

## Existing illustrations

Original page illustrations are retained below. Use the exact-model pin map and revision notes in this guide when interpreting them.

<figure><img src="../../.gitbook/assets/image (351).png" alt=""><figcaption></figcaption></figure>

<img src="https://files.seeedstudio.com/wiki/XIAO-RP2040/img/xinpin.jpg" alt="pir" width="600">

&#x20;

<img src="https://files.seeedstudio.com/wiki/XIAO-RP2040/img/xinfront.jpg" alt="pir" width="600">
