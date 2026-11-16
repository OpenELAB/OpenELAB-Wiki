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

# HT-CT62 ESP32C3 SX1262 LoRa Node Meshtastic LoRaWAN

### HELTEC HT-CT62 ESP32C3 SX1262 LoRa Node Meshtastic LoRaWAN 868Mhz

***

### Product Link

{% embed url="https://openelab.io/products/heltec-htct62-esp32c3-sx1262-lorawan" %}

### Description

HT-CT62 is a LoRa/LoRaWAN node module with a long communication range, low power consumption, high sensitivity, and low cost. The module is composed of ESP32-C3FN4 (32-bit microprocessor based on RISC-V architecture) and Semtech LoRa Transceivers (SX1262). The module integrates 2.4 GHz Wi-Fi and LoRa two-mode wireless communication. HT-CT62 is a small volume, stamp hole package module, it’s the best choice for smart cities, smart farms, smart homes, and IoT makers.

### Feature

* Microprocessor: ESP32-C3FN4 (RISC-V architecture 32-bit, main frequency up to 160 MHz)
* Integrated WiFi/BLE network connection, onboard IPEX1.0 socket.
* Support the Arduino development environment;
* LoRaWAN 1.0.2support;
* Ultra low power design, 10uA in deep sleep;
* 1.27 stamp edge design for SMT;
* Good impendence matching and long communication

### Specification

| Parameters                 | Description                                                                     |
| -------------------------- | ------------------------------------------------------------------------------- |
| Master Chip                | ESP32-C3FN4(32-bit@RISC-V architecture)                                         |
| WiFi                       | 802.11 b/g/n, up to 150Mbps                                                     |
| LoRa Chipset               | Chipset SX1262                                                                  |
| Frequency                  | <p>470~510MHz,<br>863~928MHz</p>                                                |
| Max. TX Power              | 21±1dBm                                                                         |
| Max. Receiving Sensitivity | -134dBm                                                                         |
| Hardware Resource          | <p>5*ADC1+1*ADC2;<br>2*UART;<br>1*I2C;<br>3*SPI;<br>15*GPIO; etc.</p>           |
| Memory                     | <p>384KB ROM;<br>400KB SRAM;<br>8KB RTC SRAM;<br>4MB SiP Flash</p>              |
| Interface                  | <p>2.4G ANT (IPEX1.0);<br>LoRa ANT(IPEX1.0);<br>2*11*1.27 spacing Stamp hol</p> |
| Power Consumption          | Deep Sleep 10uA                                                                 |
| Operating Temperature      | -40\~85 ℃                                                                       |
| Dimensions                 | 17.78 \* 17.78\* 2.8mm                                                          |

### Pin Map

<figure><img src="../../.gitbook/assets/image (255).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Arduino-Compatible" %}
We have done a lot of migration and development, made it perfectly support Arduino, can run the LoRaWAN protocol stablly.

<figure><img src="../../.gitbook/assets/image (257).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Stamp edge design" %}
1.27 stamp edge design, can be directly integrated into the application circuit

<figure><img src="../../.gitbook/assets/image (256).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Resource

* [Datasheet](https://resource.heltec.cn/download/HT-CT62/HT-CT62\(Rev1.1\).pdf)
* [Schematic Diagram](https://resource.heltec.cn/download/HT-CT62/HT-CT62_Schematic_Diagram.pdf)
* [Recommend hardware design](https://resource.heltec.cn/download/HT-CT62/HT-CT62_Reference_Design.pdf)
* [User Manual(Development framework and library installation)](https://docs.heltec.cn/en/node/esp32/ht_ct62/index.html)
* [Pin map](https://resource.heltec.cn/download/HT-CT62/HT-CT62.png)
* [Footprint](https://resource.heltec.cn/download/Heltec_Module_Footprint)
* [Downloadable Resources](https://resource.heltec.cn/download/HT-CT62)&#x20;

### FAQ

{% stepper %}
{% step %}
My serial port does not print informatio.

When you use the USB to Serial tool, you need to connect the serial port pins 20/21 of the device, and 17/18 when you connect directly via USB.
{% endstep %}

{% step %}
My LoRa signal became very bad after welding.

The high temperature may cause the shielding shell of the device to shift, resulting in a short circuit.
{% endstep %}

{% step %}
I can’t find the board in the board manager.

Please select **Wireless Mini Shell.**
{% endstep %}
{% endstepper %}
