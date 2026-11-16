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

# Mesh Node T114 nRF52840 SX1262 GPS Meshtastic LoRaWAN

### HELTEC Mesh Node T114 nRF52840 SX1262 GPS Meshtastic LoRaWAN 868Mhz

***

### Product Link

{% embed url="https://openelab.io/products/heltec-mesh-node-t114-nrf52840-sx1262-gps-meshtastic-lorawan-868mhz?variant=44692588757190" %}

### Description

{% embed url="https://www.youtube.com/watch?v=TGNeAgeDcaE" %}

Mesh Node T114 is a **Low Power Consumption** development board based on nRF52840 and SX1262 and supports LoRa and Bluetooth 5.0. which integrates various power interfaces (5V USB, lithium battery, and solar panel), an optional 1.14-inch TFT display, and a GPS module as accessories, and has powerful long-distance communication capabilities, scalability, and low power design.

With Heltec nRF52 development environment and libraries. you can use it for LoRa/LoRaWAN development work, and also use it to run some open source projects, such as Meshtastic.

**Mesh Node T114 has been upgraded to the Rev2.0 version with the following changes made :**

* &#x20;The circuit board was changed from 4 layers to 6 layers so that both the RF part and the crystal oscillator part can obtain a more complete ground.
* The circuit was changed from lead-free to immersion gold process, which is more friendly to signal transmission.
* The position of some components was adjusted.
* &#x20;The RF path was optimized according to the six-layer board structure.
* The direction of the 2.4GHz Bluetooth antenna and IPEX LoRa antenna interface was changed to make them farther away.
* Now the high-frequency Mesh node T114 can stably send long data packets in the “Long\_Fast” channel of Meshtastic.

### Feature

<figure><img src="../../.gitbook/assets/image (247).png" alt=""><figcaption></figcaption></figure>

* MCU nRF52840 (Bluetooth), LoRa chipset SX1262.
* Powerful display function (optional), onboard 1.14 inch TFT-LCD display contains 135(H)RGB x240(V) dots and can display up to 262k colors.
* Low power consumption, 11 uA in deep sleep.
* Operation condition: -20 \~ 70℃, 90%RH(No condensing).
* Type-C USB interface with a complete voltage regulator, ESD protection, short circuit protection, RF shielding, and other protection measures.
* Compatible with Arduino, we provide development frameworks and libraries.
* Various Interfaces: 1.25\*2P LiPo connector, 1.25\*2P Solar panel connector, 1.25\*8P GNSS module connector, which greatly increase the extensibility of the board.

### Specification

| Parameters                 | Description                                                                                                                                                        |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| MCU                        | nRF52840                                                                                                                                                           |
| LoRa Node Chip             | SX1262                                                                                                                                                             |
| Frequency                  | <p>470~510MHz;<br>863~870MHz;<br>902~928MHZ.</p>                                                                                                                   |
| Max. TX Power              | 21±1dBm                                                                                                                                                            |
| Max. Receiving sensitivity | -135dBm@SF12 BW=125KHz                                                                                                                                             |
|                            |                                                                                                                                                                    |
| Bluetooth                  | Bluetooth LE: Bluetooth 5, Bluetooth mesh                                                                                                                          |
| Hardware Resource          | USB 2.0, 4 \* SPI, 2 \* TWI, 2 \* UART, 4 \* PWM, QPSI, 12S, PDM, QDEC Etc.                                                                                        |
| Memory                     | <p>1M ROM<br>256KB SRAM</p>                                                                                                                                        |
| Interface                  | <p>Type-C USB<br>2*1.25 lithium battery connector<br>2*1.25 solar panel connector<br>LoRa ANT (IPEX1.0)<br>8*1.25 GPS module connector<br>2*13*2.54 Header Pin</p> |
| Battery                    | 3\~4.2V battery power supply and charge.                                                                                                                           |
| Operating Temperature      | -20 \~ 70 ℃                                                                                                                                                        |
| Dimensions                 | 50.80\*22.86mm                                                                                                                                                     |
| Electrical characteristics | <p>Deep Sleep: ~11uA<br>Tracker mode sleep: ~22uA<br>GPS OFF, TFT OFF: ~9mA<br>GPS OFF, TFT ON: ~20mA<br>GPS ON, TFT ON: ~51mA</p>                                 |
| Display                    | onboard 1.14 inch TFT-LCD display                                                                                                                                  |

### Pin Map

<figure><img src="../../.gitbook/assets/image (248).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Low Power Consumption " %}
Meshtastic enter low power consumption mode, the current is only 23 uA.

Entering LoRaWAN deep sleep mode, the current is only 11 uA.

<figure><img src="../../.gitbook/assets/image (249).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Powerful communication capability" %}
supports LoRa and Bluetooth 5.0.

optional 1.14 inch TFT display and GPS module as accessories.

<figure><img src="../../.gitbook/assets/image (250).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Plastic support plate" %}
A transparent plastic support platform is installed between the PCB and the monitor.

Protect the electronic components of the board and enhance its heat dissipation.

<figure><img src="../../.gitbook/assets/image (251).png" alt=""><figcaption></figcaption></figure>
{% endtab %}

{% tab title="Highly extensible" %}
integrate multiple power interfaces, 5V USB, lithium battery, solar panel.

provid abundant pins and hardware resources.

<figure><img src="../../.gitbook/assets/image (252).png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}

<figure><img src="../../.gitbook/assets/image (253).png" alt=""><figcaption></figcaption></figure>

### Resource

* [User Manual](https://docs.heltec.org/en/node/nrf/index.html)
* [Heltec nRF52 framework and Lib](https://github.com/HelTecAutomation/Heltec_nRF52)
* [SnapEmu IoT Platform](https://platform.snapemu.com/user/login)
* [Shematic diagram](https://resource.heltec.cn/download/Mesh_Node_T114/schematic_diagram.pdf)
* [Schematic diagram](https://resource.heltec.cn/download/Mesh_Node_T114/MeshNode-T114_V2.0_SCH\(2\).pdf)
* [Datasheet](https://resource.heltec.cn/download/Mesh_Node_T114/Datasheet.pdf)
* [TFT-LCD Datasheet](https://resource.heltec.cn/download/Mesh_Node_T114/1.14inch%20LH114T-IF03%20VER%20C.pdf)
* [Related Resources](https://resource.heltec.cn/download/Mesh_Node_T114)&#x20;

### FAQ

{% stepper %}
{% step %}
Can the onboard 2.4GHz antenna be replaced?

The 2.4GHz antenna is a multilayer ceramic antenna for BlueTooth communications, it can’t be replaced.
{% endstep %}

{% step %}
What development methods does it support?

* Arduino
* PlatformIO

In addition to [Meshtastic](https://meshtastic.org/) support, we have also developed a complete LoRaWAN protocol in the [nRF52 Arduino framework](https://github.com/HelTecAutomation/Heltec_nRF52).
{% endstep %}

{% step %}
What’s the battery socket type?

You can find this type of socket by search “SH1.25 x 2”.
{% endstep %}

{% step %}
What is the maximum size of battery supported by the default casing?

The maximum capacity of the shell for carrying batteries is 42 \* 2&#x38;_&#x31;1mm, and the default 3.7V lithium battery size is 40 \* 2&#x35;_&#x31;0mm
{% endstep %}

{% step %}
How to enter meshtastic on the screenless version of mesh node 114?

Just download the [screenless version](https://resource.heltec.cn/download/Mesh_Node_T114/firmware/nrf-mestastic-V242-no-screen.uf2) firmware and enter the 123456 password.
{% endstep %}

{% step %}
What is the acceptable battery range for the solar panel connected to mesh node 114?

5V\~6.5V, it is recommended to connect solar panels with a voltage of around 5V.
{% endstep %}

{% step %}
Regarding the long chars send issue

Not time ago, customer reports that some of the Mesh Node T114 works as a Meshtastic device and tries to send long strings (>50 chars) **ONLY** in Long-Fast mode (SF11, 250K BW), sometimes sending messages may fail.

* For a detailed description of this matter, please refer to this [link](https://github.com/meshtastic/firmware/issues/4723#issuecomment-2369336696)
* For a detailed report, Heltec solution, and compensation regarding this matter, please refer to this [link](https://github.com/meshtastic/firmware/issues/4723#issuecomment-2404889735)
{% endstep %}

{% step %}
Does 433MHz and 470MHz version has long chars sending issue?

With our detailed and long time testing, there is **NO issue** with long packet transmission in versions 433MHz and 470MHz, so they are not included in the compensation list.

But in response to users’ demand for the 433 and 470 hardware V2 versions, our engineers are debugging the corresponding hardware. It will be released soon.
{% endstep %}
{% endstepper %}

### Project

<figure><img src="../../.gitbook/assets/image (254).png" alt=""><figcaption></figcaption></figure>

[**Ultrasonic Sensor Distance Measurement with LoRaWAN**](https://www.hackster.io/ashley15/ultrasonic-sensor-distance-measurement-with-lorawan-78c30d)
