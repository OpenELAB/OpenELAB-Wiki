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

# Wireless Tracker ESP32S3 SX1262 GPS Meshtastic LoRaWAN

### HELTEC Wireless Tracker ESP32S3 SX1262 GPS Meshtastic LoRaWAN 868Mhz

***

### Product Link

{% embed url="https://openelab.io/products/heltec-wireless-tracker-esp32s3-gps" %}

### Description

Wireless Tracker is a development kit based on ESP32-S3FN8. It integrates both SX1262 and UC6580 to provide fast GNSS solution for IoT. It can track any object and then upload that data wirelessly by Wi-Fi, Bluetooth, LoRa, and has been widely used in Meshtastick.

Wireless Tracker supports L1 + L5/L2, and supports GPS, GLONASS, BDS, Galileo, NAVIC, QZSS multi-system joint positioning. It is perfectly compatible with Arduino, can be widely used in development such as bicycle sharing services, tracking pets or livestock, locating vehicles, tracking children, etc.

<figure><img src="../../.gitbook/assets/image (278).png" alt=""><figcaption></figcaption></figure>

### Features

* ESP32-S3FN8+SX1262+UC6580 Chipset, supports Wi-Fi, LoRa, Bluetooth, GNSS.
* Low power design of dual-frequency multi-system based on 22nm technology.
* Supports L1 + L5/L2, supports GPS, GLONASS, BDS, Galileo, NAVIC, QZSS multi-system joint positioning.
* Type-C USB interface with a complete voltage regulator, ESD protection, short circuit protection, RF shielding, and other protection measures.
* Onboard SH1.25-2 battery interface, integrated lithium battery management system (charge and discharge management, overcharge protection, battery power detection, USB / battery power automatic switching).
* Onboard Wi-Fi, Bluetooth dedicated 2.4GHz metal spring antenna, reserved IPEX (U.FL) interface for LoRa and GNSS use.
* Onboard 0.96-inch 160\*80 dot matrix LCD display, which can be used to display debugging information, battery power, and other information.
* Support the Arduino development environment.

### Specifications

| Parameters                 | Description                                                                                           |
| -------------------------- | ----------------------------------------------------------------------------------------------------- |
| Master Chip                | ESP32-S3FN8 (Xtensa®32-bit lx7 dual core processor)                                                   |
| LoRa Chipset               | SX1262                                                                                                |
| GNSS Chipset               | UC6580                                                                                                |
| Frequency                  | <p>470~510MHz,<br>863~928MHz</p>                                                                      |
| Max. TX Power              | 21±1dBm                                                                                               |
| Max. Receiving Sensitivity | -134dBm                                                                                               |
| Wi-Fi                      | 802.11 b/g/n, up to 150Mbps                                                                           |
| Bluetooth LE               | <p>Bluetooth 5,<br>Bluetooth mesh</p>                                                                 |
| Hardware Resource          | <p>7*ADC1 + 2*ADC2; 7*Touch;<br>3*UART;<br>2*I2C; 2*SPI; etc.</p>                                     |
| Interface                  | <p>Type-C USB;<br>2*1.25 lithium battery interface;<br>LoRa ANT(IPEX1.0);<br>2*18*2.54 Header Pin</p> |
| Battery                    | 3.7V lithium battery power supply and charging                                                        |
| Operating Temperature      | -20 \~ 70 ℃                                                                                           |
| Dimensions                 | 65.48 \* 28.06\* 13.52mm                                                                              |

### Pin Map

<figure><img src="../../.gitbook/assets/image (279).png" alt=""><figcaption></figcaption></figure>

### Resource

* [Heltec ESP32 framework and lib installation](https://docs.heltec.org/en/node/esp32/esp32_general_docs/quick_start.html)&#x20;
* [Hardware Update Logs](https://docs.heltec.org/en/node/esp32/wireless_tracker/hardware_update_log.html)
* [Datasheet](https://resource.heltec.cn/download/Wireless_Tracker/Wireless%20Tracker1.1.pdf)
* [Schematic\_Diagram](https://resource.heltec.cn/download/Wireless_Tracker/Wireless_Tacker1.1/HTIT-Tracker_V0.5.pdf)
* [User Manual Document](https://docs.heltec.org/en/node/esp32/wireless_tracker/index.html)
* [Heltec LoRaWAN test server based on SnapEmu](https://platform.snapemu.com/dashboard/)

### Get Start

<figure><img src="../../.gitbook/assets/image (280).png" alt=""><figcaption></figcaption></figure>

* [**How to make heltec wireless tracker battery last longer**](https://www.hackster.io/ashley15/heltec-tracker-meshtastic-low-power-setting-d34f0a)

<figure><img src="../../.gitbook/assets/image (281).png" alt=""><figcaption></figcaption></figure>

* [**Monitor Heart Rate on SnapEmu with a Wireless Tracker**](https://www.hackster.io/ashley15/monitor-heart-rate-on-snapemu-with-a-wireless-tracker-c5cd2b)

### FAQ

{% stepper %}
{% step %}
#### If you encounter an issue where your device is unable to download a program, you can follow these steps to resolve it.

1\. Check if the USB cable supports data transfer by verifying if the connected cell phone supports file transfer.

2\. Connect the USB cable, press and hold the ‘USER’ key, then press the ‘RST’ key once. Finally, release the ‘USER’ key to initiate the code download.
{% endstep %}

{% step %}
#### Upon downloading the code, if the screen does not respond?

Connect the serial port and check whether the node is activated. If the node is not activated, refer to this link to activate it: [https://docs.heltec.org/general/how\_to\_use\_license.html.](https://docs.heltec.org/general/how_to_use_license.html)
{% endstep %}

{% step %}
#### GNSS data is displayed as ‘0,0,0’ ?

1. Confirm your hardware version, V1.1 has changed the power control pin of the GNSS chip (GPIO 3 is set to HIGH on). Please carefully review the [schematic](https://resource.heltec.cn/download/Wireless_Tracker) or refer to the corresponding hardware version’s example program.
2. GNSS requires open outdoor environments or try with an external antenna.
{% endstep %}

{% step %}
#### How can LoRa be useful in your home automation projects?

Imagine that you want to measure the moisture in your field. Although, it is not far from your house, it probably doesn’t have Wi-Fi coverage. So, you can build a sensor node with an ESP32 and a moisture sensor, that sends the moisture readings once or twice a day to another ESP32 using LoRa.The later ESP32 has access to Wi-Fi, and it can run a web server that displays the moisture readings.This is just an example that illustrates how you can use the LoRa technology in your ESP32 projects.
{% endstep %}
{% endstepper %}
