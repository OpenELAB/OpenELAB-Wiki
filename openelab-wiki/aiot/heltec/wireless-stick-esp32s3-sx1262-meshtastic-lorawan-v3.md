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

# Wireless Stick ESP32S3 SX1262 Meshtastic LoRaWAN V3

### HELTEC Wireless Stick ESP32S3 SX1262 Meshtastic LoRaWAN 868Mhz V3

***

### Product Link

{% embed url="https://openelab.io/products/heltec-wireless-stick-esp32s3-sx1262" %}

### Description

In order to meet the user’s requirements for high performance and small size, we designed this product. On the basis of WiFi LoRa 32, it’s has a smaller size, 0.49″ OLED display, and better RF characteristics.

### Feature

<figure><img src="../../.gitbook/assets/image (284).png" alt=""><figcaption></figcaption></figure>

* Microprocessor: ESP32-S3FN8 (Xtensa® 32-bit LX7 dual core processor, five stage pipeline rack Structure, main frequency up to 240 MHz).
* SX1262 LoRa node chip.
* Type-C USB interface with a complete voltage regulator, ESD protection, short circuit protection, RF shielding, and other protection measures.
* Onboard SH1.25-2 battery interface, integrated lithium battery management system (charge and discharge management, overcharge protection, battery power detection, USB / battery power automatic switching).
* Integrated WiFi, LoRa, Bluetooth three network connections, onboard Wi-Fi, Bluetooth dedicated 2.4GHz metal spring antenna, reserved IPEX (U.FL) interface for LoRa use.
* Onboard 0.49-inch 64\*32 dot matrix OLED display, which can be used to display debugging information, battery power, and other information.
* Integrated CP2102 USB to serial port chip, convenient for program downloading, debugging information printing.
* Support the Arduino development environment.
* We provide ESP32 + LoRaWAN protocol Arduino® library, this is a standard LoRaWAN protocol that can communicate with any LoRa gateway running the LoRaWAN protocol. In order to make this code running, a unique license is needed.
* With good RF circuit design and low-power design.

### Specifications

| Parameters                 | Description                                                                                           |
| -------------------------- | ----------------------------------------------------------------------------------------------------- |
| Master Chip                | ESP32-S3FN8 (Xtensa®32-bit lx7 dual core processor)                                                   |
| LoRa Node Chip             | SX1262                                                                                                |
| USB to Serial Chip         | CP2102                                                                                                |
| Frequency                  | <p>470~510MHz,<br>863~928MHz</p>                                                                      |
| Max. TX Power              | 21 ± 1 dBm                                                                                            |
| Max. Receiving Sensitivity | -134dBm                                                                                               |
| Wi-Fi                      | 802.11 b/g/n, up to 150Mbps                                                                           |
| Bluetooth                  | Bluetooth LE: Bluetooth 5, Bluetooth mesh                                                             |
| Hardware Resource          | <p>7*ADC1 + 2*ADC2;<br>7*Touch;<br>3*UART;<br>2*I2C;<br>2*SPI; etc.</p>                               |
| Display                    | 0.49-inch OLED                                                                                        |
| Memory                     | <p>384KB ROM; 512KB SRAM;<br>16KB RTC SRAM; 8MB SiP Flash</p>                                         |
| Battery                    | 3.7V lithium battery power supply and charging                                                        |
| Operating temperature      | -20 \~ 70 ℃                                                                                           |
| Dimensions                 | 58.08 \* 22.6\* 8.2 mm                                                                                |
| Interface                  | <p>Type-C USB;<br>2*1.25 lithium battery interface;<br>LoRa ANT(IPEX1.0);<br>2*17*2.54 Header Pin</p> |

### Pin Map

<figure><img src="../../.gitbook/assets/image (285).png" alt=""><figcaption></figcaption></figure>

### Resource

* [Heltec ESP32 framework and lib installation](https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series)&#x20;
* [Hardware Update Logs](https://docs.heltec.org/en/node/esp32/wireless_stick/hardware_update_log.html)
* [Datasheet](https://resource.heltec.cn/download/Wireless_Stick_Lite_V3/HTIT-WSL_V3\(Rev1.1\).pdf)
* [Schematic\_Diagram](https://resource.heltec.cn/download/Wireless_Stick/Wireless_Stick_sch_V2.1.PDF)
* [User Manual Document](https://docs.heltec.org/en/node/esp32/wireless_stick/index.html)
* [Heltec LoRaWAN test server based on SnapEmu](https://platform.snapemu.com/dashboard/)

### FAQ

{% stepper %}
{% step %}
#### Is wireless stick V3 compatible with V2 code?

If you want to use the new ESP32-S3 processor and the SX1262 LoRa chip, you may need to use new libraries that support them. You should check that the libraries you are using are compatible with these new components.

As far as my experience with the Wireless Stick Lite is concerned, the only library I had to change when switching from V1 to V3 was the LoRa library. The Sandeep Mistry LoRa library that I used earlier doesn’t work with the new SX1262 LoRa chip. To make my code work with the V3, I had to migrate to the Heltec LoRaWan\_APP library. This was a true migration because the two libraries don’t use identical calls.
{% endstep %}

{% step %}
#### Meshtastick firmware for Wireless Stick

Due to the small screen of the board, it does not support Meshtastick’s screen display at present. You can download the firmware of the **Wireless Stick Lite** directly.
{% endstep %}

{% step %}
#### How can LoRa be useful in your home automation projects?

Imagine that you want to measure the moisture in your field. Although, it is not far from your house, it probably doesn’t have Wi-Fi coverage. So, you can build a sensor node with an ESP32 and a moisture sensor, that sends the moisture readings once or twice a day to another ESP32 using LoRa.The later ESP32 has access to Wi-Fi, and it can run a web server that displays the moisture readings.This is just an example that illustrates how you can use the LoRa technology in your ESP32 projects.
{% endstep %}
{% endstepper %}
