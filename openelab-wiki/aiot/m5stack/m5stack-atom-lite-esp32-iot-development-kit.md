---
description: >-
  Connect Atom-Lite C008 over USB, configure UIFlow2 and distinguish Grove pins
  from header I2C.
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

# M5Stack ATOM Lite ESP32 IoT Development Kit

{% hint style="info" %}
[**View M5Stack Atom Lite on OpenELAB**](https://openelab.io/products/m5stackatomliteesp32)

**Model:** Atom-Lite · **Manufacturer code:** `C008` · **OpenELAB SKU:** `M5-C008` · ESP32-PICO-D4; not AtomS3-Lite or Atom-Matrix.
{% endhint %}

## Product overview

Atom-Lite is a compact ESP32 controller with one RGB LED, a button, infrared output and expansion connections. Establish USB communication and a small local program before adding a peripheral or cloud service. The original Atom-Lite, Matrix and S3 models have different hardware. [Official C008 guide](https://docs.m5stack.com/en/core/Atom-Lite).

## Applications

Suitable first projects include a status indicator, button input, infrared controller or a host for a compatible sensor Unit. A compact connector is not proof that a Unit has the correct supply or that its default host pins match Atom-Lite.

## Specification

| Item                | C008 Atom-Lite               |
| ------------------- | ---------------------------- |
| Controller          | ESP32-PICO-D4, up to 240 MHz |
| Flash / SRAM        | 4 MB / 520 KB                |
| Wireless            | 2.4 GHz Wi-Fi                |
| USB input reference | 5 V, 500 mA                  |
| Dimensions          | 24 × 24 × 9.5 mm             |

Manufacturer values: [specifications, pin map and power reference](https://docs.m5stack.com/en/core/Atom-Lite).

## Hardware and connections

Start with the USB-C data cable alone. The Grove socket carries **GND, 5 V, GPIO26 and GPIO32** in black/red/yellow/white order. This differs from the header I2C mapping **SDA25/SCL21**. Choose one physical connection and configure that bus explicitly. Built-in RGB, button and IR use GPIO27, GPIO39 and GPIO12 respectively. These mappings are for C008. [Official pin map](https://docs.m5stack.com/en/core/Atom-Lite).

## Software and development resources

The manufacturer provides Arduino via [M5Atom](https://github.com/m5stack/M5Atom), UIFlow1, UIFlow2, PlatformIO and other development routes. Use examples for **Atom-Lite**; the M5Atom repository also includes Matrix examples with a 5 × 5 LED pattern that cannot be displayed on Lite's single pixel. The [official guide](https://docs.m5stack.com/en/core/Atom-Lite) includes a PlatformIO configuration using `m5stack-atom` and `espressif32@6.7.0`; retain that version when reproducing that configuration rather than silently replacing it with an arbitrary current platform.

## Getting started

### UIFlow2: establish a real device connection

1. Prepare C008, a USB data cable and the [official UIFlow2 setup guide](https://docs.m5stack.com/en/uiflow2/atomlite/program). Save any existing application/settings before replacing firmware.
2. If the serial device is absent, install the FTDI driver for the actual operating system through the manufacturer's linked driver source. Check which port appears when C008 is connected.
3. In M5Burner select **Atom-Lite** UIFlow2 firmware, download it, choose that port and complete Burn. Retain the firmware version. Other Atom models are different targets.
4. In the [UIFlow2 Web IDE](https://uiflow2.m5stack.com/), select **Atom-Lite** under Controller. Open WebTerminal, select its port and connect.
5. Use a short program that prints a recognisable message. Select **Run Once** for a trial; use **Run Always** only when ready to store it on the device.

**Expected result:** WebTerminal reports a serial connection and the submitted program produces its chosen output. Connection alone is not a sensor or Wi-Fi test. The [manufacturer procedure](https://docs.m5stack.com/en/uiflow2/atomlite/program) also describes wireless connection through an Access Code shown in WebTerminal. Software and hardware were not run for this review.

### Add one sensor after the host works

For a Grove I2C sensor, use the C008 socket's SDA26/SCL32 configuration supported by the selected example, not header SDA25/SCL21 or CoreS3's Port A pins. Record the sensor model, address and expected units. Check one device before adding another with the same address. For ENV-III, use the [ENV-III integration guide](m5stack-env-iii-unit-with-temperature-humidity-air-pressure-sensor.md).

## Troubleshooting and FAQs

**The board powers up but no port appears:** test another data cable and USB port, inspect FTDI enumeration and install the appropriate driver if needed. Close other applications holding the serial connection. [Driver and connection instructions](https://docs.m5stack.com/en/uiflow2/atomlite/program).

**UIFlow2 cannot find the device:** confirm Atom-Lite firmware and controller selection, then prove the USB path before diagnosing the network/Access Code route. Run Once and Run Always serve different purposes; a temporary run is not persistent deployment.

**A connected sensor never responds:** compare the physical socket/header with the configured I2C pins before changing the sensor library. Check supply, common ground and address conflicts with power removed before reconnecting.

## Downloads and technical documents

| Resource                                                                                                       | Use                                                                                         |
| -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [C008 official guide](https://docs.m5stack.com/en/core/Atom-Lite)                                              | Schematic, pin map, dimensions, datasheet, PlatformIO configuration and factory-loader link |
| [UIFlow2 setup](https://docs.m5stack.com/en/uiflow2/atomlite/program)                                          | Drivers, target firmware, USB/network connection and program deployment                     |
| [M5Atom library](https://github.com/m5stack/M5Atom)                                                            | Arduino source; choose the example for the actual Atom variant                              |
| [C008 mechanical files](https://github.com/m5stack/M5_Hardware/tree/master/Products/C008_Atom-Lite/Structures) | Model-specific mounting and enclosure source                                                |

## References and validation

Sources reviewed **23 November 2026**. No firmware flashing, compilation or physical test was performed. Save the selected SDK/firmware versions and observed results with the board. The links above provide the full official instructions; this guide separates host, connector, firmware and peripheral checks.

## Existing illustrations

Original page illustrations are retained below. Use the exact-model pin map and revision notes in this guide when interpreting them.

<figure><img src="../../.gitbook/assets/image (640).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (641).png" alt=""><figcaption></figcaption></figure>
