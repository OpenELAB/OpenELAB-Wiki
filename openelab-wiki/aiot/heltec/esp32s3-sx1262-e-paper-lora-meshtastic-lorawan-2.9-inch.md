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

# ESP32S3 SX1262 E-Paper LoRa Meshtastic LoRaWAN 2.9 inch

### HELTEC ESP32S3 SX1262 E-Paper LoRa Meshtastic LoRaWAN 2.9 inch 868Mhz

***

### Product Link

{% embed url="https://openelab.io/products/heltec-esp32s3-paper-2-9" %}

### Description

Vision Master E290 (HT-VME290) is an E-Ink development kit with multiple wireless drive methods. Collaborate with the sample programs and development tools we provide, users can operate the display via Bluetooth, Wi-Fi and LoRa.

This board is equipped with a default 2.90-inch black-white E-Ink display screen, continuous display for 180 days after power outage. It is compatible with Arduino, PlatformIO, Micpython and other development frameworks, can be used to develop applications such as electronic tags and identity tags, it is also possible to run open source projects like Meshtastic.

<figure><img src="../../.gitbook/assets/image (265).png" alt=""><figcaption></figcaption></figure>

### Feature

* ESP32-S3R8 MCU, support Wi-Fi and BLE.
* LoRa module is optional, compatible with Mashtastic.
* Low power consumption, 18uA in deep sleep, continuous display for 180 days after power outage.
* Onboard SH1.25-2 battery interface, integrated lithium battery management system (charge and discharge management, overcharge protection, battery power detection, USB / battery power automatic switching).
* Onboard 2.90 inch 296 x 128 pixels display, support for partial refresh.
* Storage condition: -25 \~ 70℃, ≤45%RH.
* Optimal operating condition：0\~50℃, 55±10%RH.
* SH2.0-4P sensor interface is perfectly compatible with QuickLink series sensors.
* 2\*20 Pin Female Header, perfectly compatible with Raspberry PI.
* Compatible with Arduino, we provide development frameworks and libraries.

### Specification

| Parameters                 | Description                                                                                                                                                  |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Master Chip                | ESP32-S3R8                                                                                                                                                   |
| LoRa Node Chip             | SX1262                                                                                                                                                       |
| Frequency                  | <p>470~510MHz,<br>863~928MHz</p>                                                                                                                             |
| Max. TX Power              | 21±1dBm                                                                                                                                                      |
| Max. Receiving sensitivity | -136dBm@SF12 BW=125KHz                                                                                                                                       |
| Wi-Fi                      | 802.11 b/g/n, up to 150Mbps                                                                                                                                  |
| Bluetooth                  | Bluetooth 5 (LE)                                                                                                                                             |
| Hardware Resource          | 6\*ADC\_1, 1\*ADC\_2, 6\*Touch, 8M\*PSRAM, 3\*UART; 2\*I2C; 2\*SPI. Etc                                                                                      |
| Memory                     | <p>384KB ROM;<br>512KB SRAM;<br>16KB RTC SRAM;<br>16MB SiP Flash</p>                                                                                         |
| Interface                  | <p>Type-C USB;<br>2*1.25 lithium battery interface;<br>LoRa ANT(IPEX1.0);<br>Wi-Fi ANT(IPEX1.0);<br>2*20 Pin Famle Header;<br>SH2.0-4P sensor interface.</p> |
| Battery                    | 3.7V lithium battery power supply and charging                                                                                                               |
| Operating Temperature      | -20 \~ 70 ℃                                                                                                                                                  |
| E-Ink                      | 2.90 Inch, 128(H)x296(V) Pixel, 29x67mm,                                                                                                                     |
| Display Color              | Black\&White(2 Grayscale)                                                                                                                                    |
| Dimensions                 | 87.96\*36.63\*12mm                                                                                                                                           |
| Display                    | 2.90 Inch Black and White E-Ink Display Screen                                                                                                               |

### Pin Map

<figure><img src="../../.gitbook/assets/image (266).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Highly extensible" %}
Vision Master E213 has a rich set of pins and hardware resources, which will allow you to expand widely.

The SH2.0-4P interface can be directly connected to the QuickLink series sensors.

2\*20 Pin Female Header, perfectly compatible with Raspberry PI.

<figure><img src="../../.gitbook/assets/image (267).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="High Resolution&Easy to Use" %}
The integrated E-Ink display has a high resolution of128 \* 296 pixels, and can show system status and parameters, making it convenient for users to use the development board for their own product design.

<figure><img src="../../.gitbook/assets/image (268).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="LoRa module is optional" %}
LoRa modules are optional and can reduce a lot of costs if you don't need a LoRa module.

<figure><img src="../../.gitbook/assets/image (269).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Resource

* [Heltec ESP (ESP32\&ESP8266) framework](https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series) (Include LoRaWAN library)
* [Heltec ESP32 special library](https://github.com/HelTecAutomation/Heltec_ESP32)
* [Schematic diagram](https://resource.heltec.cn/download/HT-VME290/HT-VME290_Schematic_Diagram_V0.3.1.pdf)
* [Datasheet](https://resource.heltec.cn/download/HT-VME290/HT-VME290-Datasheet.pdf)
* [E-Ink Datasheet](https://resource.heltec.cn/download/HT-VME290/DEPG0290BNS800F6_V2.1.pdf)
* [User manual and related documents](https://docs.heltec.cn/en/node/esp32/ht_vme290/index.html)
* [Downloadable Resources](https://resource.heltec.cn/download/HT-VME290)&#x20;

### FAQ

{% stepper %}
{% step %}
#### Can the onboard 2.4GHz antenna be replaced?

The 2.4GHz antenna is a spring antenna, and there is no additional interface on the board for 2.4GHz wireless signals.
{% endstep %}

{% step %}
Can ESP32’s WiFi and Bluetooth be used at the same time?

No, the WiFi LoRa 32 don’t have an external PSRAM, if your application need use Bluetooth and Wi-Fi at the same time, you can look into this product: [Heltec Wireless Bridge](https://heltec.org/project/wireless-bridge/).
{% endstep %}

{% step %}
What development methods does it support?

* Arduino
* Micro Python
* PlatformIO
* Espressif IDE

We strongly recommend using Arduino. We have complete technical support and provide complete [Official Heltec ESP32 LoRaWAN examples](https://github.com/HelTecAutomation/Heltec_ESP32/tree/master/examples/LoRaWAN).

These maintained examples use the Heltec ESP32 package and its supported board/framework version; they are not a drop-in copy of the retired LoraWan102 package.
{% endstep %}

{% step %}
What’s the battery socket type?

You can find this type of socket by search “SH1.25 x 2”.
{% endstep %}

{% step %}
How to Strat the Development Board.

Press and hold the Boot key, press RST once, and then release the Boot key. Among them 21 button can be customized by user.

<figure><img src="../../.gitbook/assets/image (270).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}
