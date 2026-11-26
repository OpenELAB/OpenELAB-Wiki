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

# ESP32S3 SX1262 E-Paper LoRa Meshtastic LoRaWAN 2.13 inch

### HELTEC ESP32S3 SX1262 E-Paper LoRa Meshtastic LoRaWAN 2.13 inch 868Mhz

***

### Product Link

{% embed url="https://openelab.io/products/heltec-esp32s3-sx1262-e-paper" %}

### Description

Vision Master E213 (HT-VME213) is an E-Ink development kit with multiple wireless drive methods. Collaborate with the sample programs and development tools we provide, users can operate the display via Bluetooth, Wi-Fi and LoRa.

This board is equipped with a default 2.13-inch black and white E-Ink display screen, continuous display for 180 days after power outage. It is compatible with Arduino, PlatformIO, Micpython and other development frameworks, can be used to develop applications such as electronic tags and identity tags, it is also possible to run open source projects like Meshtastic.

### Feature

<figure><img src="../../.gitbook/assets/image (258).png" alt=""><figcaption></figcaption></figure>

* ESP32-S3R8 MCU, support Wi-Fi and BLE.
* LoRa module is optional, compatible with Mashtastic.
* Low power consumption, 20uA in deep sleep, continuous display for 180 days after power outage.
* Onboard SH1.25-2 battery interface, integrated lithium battery management system (charge and discharge management, overcharge protection, battery power detection, USB / battery power automatic switching).
* Onboard 2.13 inch 250 x 122 pixels display, support for partial refresh.
* Storage condition: -25 \~ 70℃, ≤45%RH.
* Optimal operating condition：0\~50℃, 55±10%RH.
* 2\*SH2.0-4P sensor interface is perfectly compatible with QuickLink series sensors.
* Compatible with Arduino, we provide development frameworks and libraries.

### Specification

| Parameters                 | Description                                                                                                                                                   |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Master Chip                | ESP32-S3R8                                                                                                                                                    |
| LoRa Node Chip             | SX1262                                                                                                                                                        |
| Frequency                  | <p>470~510MHz,<br>863~928MHz</p>                                                                                                                              |
| Max. TX Power              | 21±1dBm                                                                                                                                                       |
| Max. Receiving sensitivity | -136dBm@SF12 BW=125KHz                                                                                                                                        |
| Wi-Fi                      | 802.11 b/g/n, up to 150Mbps                                                                                                                                   |
| Bluetooth                  | Bluetooth 5 (LE)                                                                                                                                              |
| Hardware Resource          | 6\*ADC\_1, 1\*ADC\_2, 6\*Touch, 8M\*PSRAM, 3\*UART; 2\*I2C; 2\*SPI. Etc                                                                                       |
| Memory                     | <p>384KB ROM;<br>512KB SRAM;<br>16KB RTC SRAM;<br>16MB SiP Flash</p>                                                                                          |
| Interface                  | <p>Type-C USB;<br>2*1.25 lithium battery interface;<br>LoRa ANT(IPEX1.0);<br>Wi-Fi ANT(IPEX1.0);<br>2*18*2.54 Header Pin;<br>2*SH2.0-4P sensor interface.</p> |
| Battery                    | 3.7V lithium battery power supply and charging                                                                                                                |
| Operating Temperature      | -20 \~ 70 ℃                                                                                                                                                   |
| Dimensions                 | 66.75\*30.41\*10mm                                                                                                                                            |
| Display                    | 2.13 Inch Black and White E-Ink Display Screen                                                                                                                |

### Pin Map

<figure><img src="../../.gitbook/assets/image (259).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (260).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Highly extensible" %}
Vision Master E213 has a rich set of pins and hardware resources, which will allow you to expand widely. The SH2.0-4P interface can be directly connected to QuickLink series sensors.

<figure><img src="../../.gitbook/assets/image (261).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Plastic support plate" %}
A transparent plastic support platform is installed between the PCB and the display frequency, which can protect the electronic components on the board and enhance the heat dissipation function of the board.

<figure><img src="../../.gitbook/assets/image (262).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="LoRa module is optional" %}
LoRa modules are optional and can reduce a lot of costs if you don't need a LoRa module.

<figure><img src="../../.gitbook/assets/image (264).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Resource

* [Heltec ESP (ESP32\&ESP8266) framework](https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series) (Include LoRaWAN library)
* [Heltec ESP32 special library](https://github.com/HelTecAutomation/Heltec_ESP32)
* [Schematic diagram](https://resource.heltec.cn/download/HT-VME213/HT-VME213_Schematic_Diagram_V1.0.pdf)
* [Datasheet](https://resource.heltec.cn/download/HT-VME213/HT-VME213%20Datasheet.pdf)
* [E-Ink Datasheet](https://resource.heltec.cn/download/HT-VME213/LCMEN2R13EFC1.pdf)
* [User manual and related documents](https://docs.heltec.cn/en/node/esp32/ht_vme213/index.html)
* [Downloadable Resources](https://resource.heltec.cn/download/HT-VME213)&#x20;

### FAQ

{% stepper %}
{% step %}
Can the onboard 2.4GHz antenna be replaced?

The 2.4GHz antenna is a spring antenna, and there is no additional interface on the board for 2.4GHz wireless signals.
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
I can not find serial port.

1. Please reinsert your USB cable, or try another cable.
2. If you use USB adapters, try to skip them and connect directly to the USB port on your PC.
3. Open your DEVICE MANAGER, select the port, and if prompted, try to install the [CP210X driver](https://resource.heltec.cn/download/tools/CP210x_Universal_Windows_Driver.zip)
4. Try another computer or a different system
{% endstep %}

{% step %}
The serial port does not exist.

1. Open your DEVICE MANAGER, check to see if the device port can be found. If not, please refer to the previous topic “I can’t find serial port”.
2. Please check if your serial port is opened elsewhere.
3. Enter the BootLoader mode to upload, there are two ways to enter the mode:
   * connect the USB cable, hold down the User (or ORG or Boot) key, press RST once, and then release the User (or ORG or Boot) key.
   * Hold down the User (or ORG or Boot) key, then connect the USB cable.
{% endstep %}

{% step %}
How to Strat the Development Board.

Press and hold the Boot key, press RST once, and then release the  Boot key. Among them 21 button can be customized by user.

&#x20;

<img src="https://heltec.org/wp-content/uploads/2024/08/213button-1.jpg" alt="" height="417" width="500">
{% endstep %}
{% endstepper %}
