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

# Wireless Stick Lite ESP32S3 SX1262 Meshtastic LoRaWAN V3

{% hint style="info" %}
[**View Wireless Stick Lite ESP32S3 SX1262 Meshtastic LoRaWAN V3 on OpenELAB**](https://openelab.io/products/heltec-wireless-stick-lite-esp32s3)

**Model/option:** Wireless Stick Lite ESP32S3 SX1262 Meshtastic LoRaWAN V3 · **Top-200 SKU:** `HT-WS-Lite-V3`
{% endhint %}

## HELTEC Wireless Stick Lite ESP32S3 SX1262 Meshtastic LoRaWAN 868Mhz V3

***

## Product Link

{% embed url="https://openelab.io/products/heltec-wireless-stick-lite-esp32s3" %}

## Description

HTIT-WSL is a development board for Wi-Fi, Bluetooth and LoRa. Because some customers do not need OLED screen when using WiFi Lora32, we launched this product.

The HTIT-WSL is composed up of an MCU (ESP32-S3FN8) and Semtech LoRa Transceivers (SX1262), perfectly support Arduino®. Users can easily carry out secondary development and application.

<figure><img src="../../.gitbook/assets/image (282).png" alt=""><figcaption></figcaption></figure>

## Features

* Microprocessor: ESP32-S3FN8 (Xtensa® 32-bit LX7 dual core processor, five stage pipeline rack Structure, main frequency up to 240MHz).
* SX1262 LoRa node chip.
* Type-C USB interface with a complete voltage regulator, ESD protection, short circuit protection, RF shielding, and other protection
* Onboard SH1.25-2 battery interface, integrated lithium battery management system (charge and discharge management, overcharge protection, battery power detection, USB / battery power automatic switching).
* Integrated WiFi, LoRa, Bluetooth three network connections, onboard Wi-Fi, Bluetooth dedicated 2.4GHz metal spring antenna, reserved IPEX (U.FL) interface for LoRa
* Integrated CP2102 USB to serial port chip, convenient for program downloading, debugging information printing.
* Support the Arduino development environment;
* With good RF circuit design and basic low-power design (sleep current ≤800uA), it is convenient for IoT application vendors to quickly verify solutions and deploy applications;

## Specification

| Parameters                 | Description                                                                                                                                                   |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Master Chip                | ESP32-S3FN8 (Xtensa®32-bit lx7 dual core processor)                                                                                                           |
| LoRa Chipset               | SX1262                                                                                                                                                        |
| USB to Serial Chip         | CP2102                                                                                                                                                        |
| Frequency                  | <p>470<del>510MHz,</del><br><del>863</del>928MHz</p>                                                                                                          |
| Max. TX Power              | 21d B ± 1d B                                                                                                                                                  |
| Max. Receiving sensitivity | -134dBm                                                                                                                                                       |
| Wi-Fi                      | 802.11 b/g/n, up to 150Mbps                                                                                                                                   |
| Bluetooth LE               | Bluetooth 5, Bluetooth mesh                                                                                                                                   |
| Hardware Resource          | <p>7<em>ADC1 + 9</em>ADC2;<br>8<em>Touch;</em><br><em>3</em>UART;<br>2<em>I2C;</em><br><em>2</em>SPI; etc.</p>                                                |
| Memory                     | <p>384KB ROM;<br>512KB SRAM;<br>16KB RTC SRAM;<br>8MB SiP Flash</p>                                                                                           |
| Battery                    | 3.7V lithium battery power supply and charging                                                                                                                |
| Operating temperature      | -20 \~ 70 ℃                                                                                                                                                   |
| Dimensions                 | 58.08 \* 22.6\* 8.2 mm                                                                                                                                        |
| Interface                  | <p>Type-C USB;<br>2<em>1.25 lithium battery interface;</em><br><em>LoRa ANT(IPEX1.0);</em><br><em>2.4G ANT(IPEX1.0);</em><br><em>2</em>20*2.54 Header Pin</p> |

## Pin Map

<figure><img src="../../.gitbook/assets/image (283).png" alt=""><figcaption></figcaption></figure>

## Resource

* [Heltec ESP32 framework and lib installation](https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series)
* [Hardware Update Logs](https://docs.heltec.org/en/node/esp32/wireless_stick/hardware_update_log.html)
* [Datasheet](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3\(Rev1.1\).pdf)
* [Schematic\_Diagram](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3_Schematic_Diagram.pdf)
* [User Manual Document](https://docs.heltec.org/en/node/esp32/wireless_stick/index.html)
* [Heltec LoRaWAN test server based on SnapEmu](https://platform.snapemu.com/dashboard/)

## FAQ

{% stepper %}
{% step %}
#### Is wireless stick V3 compatible with V2 code?

If you want to use the new ESP32-S3 processor and the SX1262 LoRa chip, you may need to use new libraries that support them. You should check that the libraries you are using are compatible with these new components.

As far as my experience with the Wireless Stick Lite is concerned, the only library I had to change when switching from V1 to V3 was the LoRa library. The Sandeep Mistry LoRa library that I used earlier doesn’t work with the new SX1262 LoRa chip. To make my code work with the V3, I had to migrate to the Heltec LoRaWan\_APP library. This was a true migration because the two libraries don’t use identical calls.
{% endstep %}

{% step %}
#### How can LoRa be useful in your home automation projects?

Imagine that you want to measure the moisture in your field. Although, it is not far from your house, it probably doesn’t have Wi-Fi coverage. So, you can build a sensor node with an ESP32 and a moisture sensor, that sends the moisture readings once or twice a day to another ESP32 using LoRa.The later ESP32 has access to Wi-Fi, and it can run a web server that displays the moisture readings.This is just an example that illustrates how you can use the LoRa technology in your ESP32 projects.
{% endstep %}

{% step %}
#### How to get the License?

Refer to this link: [How to Use License — main latest documentation (heltec.org)](https://docs.heltec.org/general/how_to_use_license.html)
{% endstep %}
{% endstepper %}
