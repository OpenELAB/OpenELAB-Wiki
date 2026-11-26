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

# Wireless Paper ESP32S3 SX1262 E-paper Meshtastic LoRaWAN

### HELTEC Wireless Paper ESP32S3 SX1262 E-paper Meshtastic LoRaWAN 868Mhz

***

### Product Link

{% embed url="https://openelab.io/products/heltec-wireless-paper-esp32s3-meshtastic" %}

### Description

Wireless Paper is an E-Ink development kit with multiple wireless drive methods. Collaborate with the sample programs and development tools we provide, users can operate the display via Bluetooth, Wi-Fi and LoRa.

This board is equipped with a default 2.13-inch black and white E-Ink display screen, continuous display for 180 days after power outage. It can be used to develop applications such as electronic tags and identity tags.

### Feature

* ESP32-S3FN8 + SX1262 Chipset, device can be driven via Wi-Fi, BLE and LoRa;
* Default 250 x 122 pixels black-white display, it can also be used to drive E-Ink screens of other sizes;
* High contrast, high reflectance, ultra-wide viewing angle;
* Low power consumption, 20uA in deep sleep;
* Internal integrated display screen refresh page function, users can drag and drop BMP images to achieve refresh;
* Operation condition: 0\~50℃, 35\~70%RH;
* Onboard USB-UART bridge, facilitate user secondary development.

### Specification

| Parameters            | Description                      |
| --------------------- | -------------------------------- |
| MCU                   | ESP32-S3FN8                      |
| LoRa Chipset          | SX1262                           |
| Frequency             | <p>470~510MHz,<br>863~928MHz</p> |
| Power Supply          | lithium battery, USB Type-C      |
| Supply Voltage        | 3\~5v                            |
| Operating Temperature | 0\~50℃                           |
| Operating Humidity    | 35\~70%                          |
| Display Resolution    | 122(H)x250(V) Pixel              |
| Connection Method     | Wi-Fi, LoRa,BLE                  |
| Screen Size           | 2.13 Inch                        |
| Active Area           | 23.705×48.55                     |
| Pixel Pitch           | 0.1942X0.1942                    |
| Pixel Configuration   | Square                           |

{% tabs %}
{% tab title="USB Type C" %}
The power supply, firmware download, and debugging interfaces adopt a more universal USB Type C interface, making development work more convenient.

<figure><img src="../../.gitbook/assets/image (289).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Acrylic protective plate" %}
Transparent acrylic protection plate provide basic protection for the development board.

<figure><img src="../../.gitbook/assets/image (290).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="E-Ink Display" %}
The integrated E-Ink display can be used to show some information such as system status and parameters, making it convenient for users to directly use the entire development board for their own product design.

<figure><img src="../../.gitbook/assets/image (291).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Resource

* [Heltec ESP32 framework and lib installation](https://docs.heltec.org/en/node/esp32/esp32_general_docs/quick_start.html)&#x20;
* [Hardware Update Logs](https://docs.heltec.org/en/node/esp32/wireless_paper/hardware_update_log.html)
* [Datasheet](https://resource.heltec.cn/download/Wireless_Paper/Wireless-Paper.pdf)
* [Schematic\_Diagram](https://resource.heltec.cn/download/Wireless_Paper/Wireless_Paper_V0.4_Schematic_Diagram.pdf)
* [E-Ink Datasheet](https://resource.heltec.cn/download/Wireless_Paper/E-Ink%20Datasheet)
* [User Manual Document](https://docs.heltec.cn/en/node/esp32/wireless_paper/index.html)
* [Heltec LoRaWAN test server based on SnapEmu](https://platform.snapemu.com/dashboard/)

### FAQ

{% stepper %}
{% step %}
#### What is E ink price tag?

E Ink price tag is a **price tag that is very suitable for retail**. It is simple to operate and more convenient to use. Compared with ordinary paper price tags, it is faster to change prices and can save a lot of human resources.
{% endstep %}

{% step %}
#### Does it have WiFi functionality?

Yes.
{% endstep %}

{% step %}
How to use it?

You can refer to the [Quickstart](https://wiki.heltec.org/docs/devices/open-source-hardware/esp32-series/esp32-quick-start).&#x20;
{% endstep %}
{% endstepper %}
