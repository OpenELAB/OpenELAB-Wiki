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

# XIAO ESP32S3 & Wio-SX1262 Kit for Meshtastic

{% hint style="info" %}
[**View XIAO ESP32S3 & Wio-SX1262 Kit for Meshtastic on OpenELAB**](https://openelab.io/products/seeed-studio-xiao-esp32s30-wio-sx1262-kit-for-meshtastic)

**Model/kit:** XIAO ESP32S3 & Wio-SX1262 Kit for Meshtastic · **OpenELAB SKU:** `Seeed-102010611`
{% endhint %}

## Seeed Studio XIAO ESP32S3 & Wio-SX1262 Kit for Meshtastic

***

## Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-esp32s30-wio-sx1262-kit-for-meshtastic" %}

## Description

This thumb-sized LoRa development kit, which consists of the XIAO ESP32S3 and the Wio-SX1262 LoRa module, is an ideal starter kit for Meshtastic and LoRa/LoRaWAN projects. Supporting WiFi, BLE, and LoRa, it includes a built-in power management chip and can be extended via IIC, UART, and other GPIO interfaces, and is compatible with Arduino development. The XIAO ESP32S3 & Wio-SX1262 Kit is a single-channel LoRaWAN LoRa module with a low price and high cost performance. It is suitable for application scenarios with long distance, low power consumption, and small data volume. It supports more than 30 node devices (depending on upload interval, data payload, etc.).

applications:

* Using Meshtastic for network communication
* Configuring as LoRaWAN node
* Configuring as LoRaWAN gateway

## Features

* **Meshtactic works out of the box**: Pre-flashed with Meshtastic firmware, it is ready to work once powered on.
* **Outstanding RF performance**: Supports LoRa(862-930MHz) 2.4GHz Wi-Fi and BLE 5.0 dual wireless communication, support 2\~5km(LoRa) and 100m+(Wi-Fi/BLE) remote communication when connected with U.FL antenna.
* **Thumb-sized Compact Design**: 21 x 18mm, adopting the classic form factor of XIAO, suitable for space-limited projects like wearable devices.
* **Powerful MCU Board**: Incorporate the ESP32S3 32-bit, dual-core, Xtensa processor running at up to 240MHz, mounted multiple development ports, Arduino / MicroPython supported.
* **Elaborate Power Design**: Includes a Type-C USB interface and lithium battery charge management.

## Specification

| Feature                | Details                                                                                                                               |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| ESP32S3                | ESP32-S3R8, Xtensa LX7 dual-core, 32-bit processor running up to 240 MHz                                                              |
| LoRa                   | Based on Semtech SX1262, supports 862-930MHz                                                                                          |
| BLE                    | Bluetooth 5.0, Bluetooth mesh                                                                                                         |
| Wi-Fi                  | Complete 2.4GHz Wi-Fi subsystem                                                                                                       |
| Interface (ESP32S3)    | 1x UART, 1x IIC, 1x IIS, 1x SPI(connect to SX1262),11x GPIO(PWM), 9x ADC, 1x User LED, 1x Charge LED, 1x Reset button, 1x Boot button |
| Interface (Wio-SX1262) | 1x User button, 1x SPI(connect to ESP32S3)                                                                                            |
| Power                  | <p>Input voltage (Type-C): 5V<br>Input voltage (BAT): 4.2V<br>Charging battery current: 100mA</p>                                     |
| Working Temperature    | -40°C \~ 65°C                                                                                                                         |
| Dimensions             | 21 x 17.8mm                                                                                                                           |

## Hardware

Wio-SX1262 extension board diagram

<figure><img src="../../.gitbook/assets/image (298).png" alt=""><figcaption></figcaption></figure>

XIAO ESP32S3 front indication diagram

<figure><img src="../../.gitbook/assets/image (299).png" alt=""><figcaption></figcaption></figure>

XIAO ESP32S3 back indications diagram

<figure><img src="../../.gitbook/assets/image (300).png" alt=""><figcaption></figcaption></figure>

XIAO ESP32S3 Pin List

<figure><img src="../../.gitbook/assets/image (301).png" alt=""><figcaption></figcaption></figure>

Video Instruction

{% embed url="https://www.youtube.com/watch?v=AGPZ9xnX3gs" %}

## Resource

* [Wio-SX1262 Module Datasheet](https://files.seeedstudio.com/products/SenseCAP/Wio_SX1262/Wio-SX1262_Module_Datasheet.pdf)
* [Wio-SX1262 Schemetic Diagram](https://files.seeedstudio.com/products/SenseCAP/Wio_SX1262/Schematic_Diagram_Wio-SX1262_for_XIAO.pdf)
* [Wio-SX1262 for XIAO 3D file](https://files.seeedstudio.com/products/SenseCAP/Wio_SX1262/Wio-SX1262_for_XIAO_3D_file.step)

## Official documentation and development resources

Use [XIAO ESP32S3 & Wio-SX1262 Kit Introduction](https://wiki.seeedstudio.com/wio_sx1262_with_xiao_esp32s3_kit/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                          |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic   | [Read electrical schematic](https://files.seeedstudio.com/products/SenseCAP/Wio_SX1262/Schematic_Diagram_Wio-SX1262_for_XIAO.pdf) |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/products/SenseCAP/Wio_SX1262/Wio-SX1262_for_XIAO_3D_file.step)        |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
