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

# WiFi LoRa ESP32 SX1262 LoRa Node Meshtastic LoRaWAN V2

### HELTEC WiFi LoRa ESP32 SX1262 LoRa Node Meshtastic LoRaWAN 868Mhz V2

***

### Product Link

{% embed url="https://openelab.io/products/heltec-wifi-lora-esp32-v2" %}

### Description

WiFi LoRa 32 is a classic IoT dev-board designed & produced by Heltec Automation(TM), it’s a highly integrated product based on ESP32 + SX127x, it has Wi-Fi, BLE, LoRa functions, Li-Po battery management system and 0.96 OLED. It’s the best choice for smart cities, smart farms, smart home, and IoT makers.

### Feature

* Microprocessor: ESP32(dual-core 32-bit MCU + ULP core), with LoRa node chip SX1276/SX1278.
* Micro USB interface with a complete voltage regulator, ESD protection, short circuit protection, RF shielding, and other protection measures.
* Onboard SH1.25-2 battery interface, integrated lithium battery management system (charge and discharge management, overcharge protection, battery power detection, USB / battery power automatic switching).
* Onboard 0.96-inch 128\*64 dot matrix OLED display can be used to display debugging information, battery power, and other information.
* Integrated WiFi, LoRa, Bluetooth three network connections, onboard Wi-Fi, Bluetooth dedicated 2.4GHz metal spring antenna, reserved IPEX (U.FL) interface for LoRa use.
* Integrated CP2102 USB to serial port chip, convenient for program downloading, and debugging information printing.
* Support the Arduino development environment.
* With good RF circuit design and basic low-power design(sleep current ≤ 800uA).

### Specification

| Parameters            | Description                                                         |
| --------------------- | ------------------------------------------------------------------- |
| Master Chip           | ESP32 (240MHz Tensilica LX6 dual-core+1 ULP, 600 DMIPS)             |
| LoRa Node Chip        | SX1276/SX1278                                                       |
| USB to Serial Chip    | CP2102                                                              |
| Frequency             | <p>470~510MHz,<br>863~923MHz</p>                                    |
| Max. TX Power         | 19±1dBm                                                             |
| Receiving sensitivity | -135dBm                                                             |
| Wi-Fi                 | 802.11 b/g/n, up to 150Mbps                                         |
| Bluetooth             | Bluetooth V4.2 BR/EDR and Bluetooth LE specification                |
| Hardware Resource     | <p>22*GPIO;<br>3*UART;<br>2*I2C;<br>2*SPI;</p>                      |
| Memory                | <p>520KB internal SRAM;<br>8MB Spi Flash</p>                        |
| Interface             | <p>Micro USB x 1;<br>LoRa ANT(IPEX1.0);<br>2*18*2.54 Header Pin</p> |
| Battery               | 3.7V lithium (SH1.25 x 2 socket)                                    |
| Operating Temperature | -20 \~ 70 ℃                                                         |
| Dimensions            | 51 \* 25.5\* 10.6 mm                                                |

### Pin Map

<figure><img src="../../.gitbook/assets/image (240).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="USB Type C" %}
The power supply, firmware download, and debugging interfaces adopt a more universal USB Type C interface, making development work more convenient.

<figure><img src="../../.gitbook/assets/image (241).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Platic Shell" %}
We also made a plastic shell as an optional accessory. Which provide basic protection for the development board.

<figure><img src="../../.gitbook/assets/image (242).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Onboard OLED Display" %}
The integrated OLED display can be used to show some information such as system status and parameters, making it convenient for user to directly use the entire development board for their own product design.

<figure><img src="../../.gitbook/assets/image (243).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

### Resource

* [Heltec ESP (ESP32\&ESP8266) framework](https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series) (Include LoRaWAN library)
* [Heltec ESP32 special library](https://github.com/HelTecAutomation/Heltec_ESP32)
* [Hardware Update Logs](https://docs.heltec.cn/en/node/esp32/wifi_lora_32/hardware_update_log.html)
* [Schematic diagram](https://resource.heltec.cn/download/WiFi_LoRa_32/V2)
* [Datasheet](https://resource.heltec.cn/download/WiFi_LoRa_32/WiFi%20Lora32.pdf)
* [User manual and related documents](https://docs.heltec.org/en/node/esp32/wifi_lora_32/index.html)
* [Downloadable Resources](https://resource.heltec.cn/download/WiFi_LoRa_32)&#x20;

### FAQ

{% stepper %}
{% step %}
Can the onboard 2.4GHz antenna be replaced?

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
* Platform.io
* Espressif IDE

We strongly recommend using Arduino. We have complete technical support and provide complete [LoRaWAN code for ESP32 Arduino framework](https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series/tree/master/esp32/libraries/LoraWan102).
{% endstep %}

{% step %}
What’s the battery socket type?

You can find this type of socket by search “SH1.25 x 2”.
{% endstep %}

{% step %}
Can I order a version without the OLED display?

Of course, you can contact our [sales staff](mailto:saige@heltec.cn) and provide your ideas.
{% endstep %}

{% step %}
Is V2 code compatible with V3?

No, the MCU is different.
{% endstep %}
{% endstepper %}
