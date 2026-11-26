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

# WiFi LoRa ESP32 SX1262 LoRa Node Meshtastic LoRaWAN

### HELTEC WiFi LoRa ESP32 SX1262 LoRa Node Meshtastic LoRaWAN 868Mhz V3

***

### Product Link

{% embed url="https://openelab.io/products/heltec-wifi-lora-esp32-v3?variant=44687822225606" %}

### Description

WiFi LoRa 32 is a classic IoT dev-board designed & produced by Heltec Automation. Since its launch in 2017, it has been loved by developers and makers. The newly launched V3 version has the same pin sequence as the V2 version and retains Wi-Fi, BLE, LoRa, OLED display, and other functions.

It is the best option for smart cities, farms, homes, industrial control, house security, wireless meter reading, and IoT developers.

{% embed url="https://www.youtube.com/watch?v=DkC0MzqCrs0" %}

### Feature

* Microprocessor: ESP32-S3FN8 (Xtensa® 32-bit LX7 dual-core processor, five-stage pipeline rack Structure, frequency up to 240 MHz).
* SX1262 LoRa node chip.
* Type-C USB interface with a complete voltage regulator, ESD protection, short circuit protection, RF shielding, and other protection measures.
* Onboard SH1.25-2 battery interface, integrated lithium battery management system (charge and discharge management, overcharge protection, battery power detection, USB / battery power automatic switching).
* Onboard 0.96-inch 128\*64 dot matrix OLED display can be used to display debugging information, battery power, and other information.
* Integrated WiFi, LoRa, Bluetooth three network connections, onboard Wi-Fi, Bluetooth dedicated 2.4GHz metal spring antenna, reserved IPEX (U.FL) interface for LoRa use.
* Integrated CP2102 USB to serial port chip, convenient for program downloading, and debugging information printing.
* Support the Arduino development environment.
* With good RF circuit design and low-power design.

<figure><img src="../../.gitbook/assets/image (292).png" alt=""><figcaption></figcaption></figure>

### Specification

| Parameters                 | Description                                                                                           |
| -------------------------- | ----------------------------------------------------------------------------------------------------- |
| Master Chip                | ESP32-S3FN8 (Xtensa®32-bit lx7 dual core processor)                                                   |
| LoRa Node Chip             | SX1262                                                                                                |
| USB to Serial Chip         | CP2102                                                                                                |
| Frequency                  | <p>470~510MHz,<br>863~928MHz</p>                                                                      |
| Max. TX Power              | 21±1dBm                                                                                               |
| Max. Receiving sensitivity | -134dBm@SF12 BW=125KHz                                                                                |
| Wi-Fi                      | 802.11 b/g/n, up to 150Mbps                                                                           |
| Bluetooth                  | Bluetooth 5 (LE)                                                                                      |
| Hardware Resource          | <p>7*ADC1 + 2*ADC2;<br>7*Touch;<br>3*UART;<br>2*I2C;<br>2*SPI; etc.</p>                               |
| Memory                     | <p>384KB ROM;<br>512KB SRAM;<br>16KB RTC SRAM;<br>8MB SiP Flash</p>                                   |
| Interface                  | <p>Type-C USB;<br>2*1.25 lithium battery interface;<br>LoRa ANT(IPEX1.0);<br>2*18*2.54 Header Pin</p> |
| Battery                    | 3.7V lithium battery power supply and charging                                                        |
| Operating Temperature      | -20 \~ 70 ℃                                                                                           |
| Dimensions                 | 50.2 \* 25.5\* 10.2 mm                                                                                |

### Pin Map

<figure><img src="../../.gitbook/assets/image (293).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="USB Type C" %}
The power supply, firmware download, and debugging interfaces adopt a more universal USB Type C interface, making development work more convenient.

<figure><img src="../../.gitbook/assets/image (294).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Plastic Shell" %}
We also made a plastic shell as an optional accessory. Which provide basic protection for the development board.

<figure><img src="../../.gitbook/assets/image (295).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Onboard OLED Display" %}
The integrated OLED display can be used to show some information such as system status and parameters, making it convenient for users to directly use the entire development board for their own product design.

<figure><img src="../../.gitbook/assets/image (296).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

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

We strongly recommend using Arduino. We have complete technical support and provide complete [Official Heltec ESP32 LoRaWAN examples](https://github.com/HelTecAutomation/Heltec_ESP32/tree/master/examples/LoRaWAN).

These maintained examples use the Heltec ESP32 package and its supported board/framework version; they are not a drop-in copy of the retired LoraWan102 package.
{% endstep %}

{% step %}
#### What’s the battery socket type?

You can find this type of socket by search “SH1.25 x 2”.
{% endstep %}

{% step %}
#### Can I order a version without the OLED display?

Of course, you can contact our [sales staff](mailto:saige@heltec.cn) and provide your ideas.
{% endstep %}

{% step %}
#### Is V2 code compatible with V3?

No, the MCU is different.
{% endstep %}

{% step %}
#### Meshtastic screen has a digital front-end issue?

It’s caused by the meshtastic setting. Changing the default screen to SSD1306 can solve the problem.

The specific steps are as follows:

“Radio configuration”→”Display”→”Override OLED auto-detect”→”SSD1306”

<figure><img src="../../.gitbook/assets/image (297).png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

### Resource

* [Heltec ESP (ESP32\&ESP8266) framework](https://github.com/Heltec-Aaron-Lee/WiFi_Kit_series) (Include LoRaWAN library)
* [Heltec ESP32 special library](https://github.com/HelTecAutomation/Heltec_ESP32)
* [Hardware Update Logs](https://docs.heltec.cn/en/node/esp32/wifi_lora_32/hardware_update_log.html)
* [Schematic diagram](https://resource.heltec.cn/download/WiFi_LoRa_32_V3/HTIT-WB32LA\(F\)_V3.1_Schematic_Diagram.pdf)
* [Schematic diagram](https://resource.heltec.cn/download/WiFi_LoRa_32_V3/HTIT-WB32LA\(F\)_V3.1_Schematic_Diagram.pdf)
* [Datasheet](https://resource.heltec.cn/download/WiFi_LoRa_32_V3/HTIT-WB32LA_V3.2.pdf)
* [User manual and related documents](https://docs.heltec.org/en/node/esp32/wifi_lora_32/index.html)
* [Downloadable Resources](https://resource.heltec.cn/download/WiFi_LoRa_32_V3/)&#x20;

### Get Start&#x20;

![](https://heltec.org/wp-content/uploads/2023/09/1.png)

[**WiFi LoRa 32 & Hall Sensor Door Detection LoRaWAN System**](https://www.hackster.io/ashley15/wifi-lora-32-hall-sensor-door-detection-lorawan-system-57febb)
