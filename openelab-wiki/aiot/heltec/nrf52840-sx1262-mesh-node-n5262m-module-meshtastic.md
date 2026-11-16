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

# nRF52840 SX1262 Mesh Node N5262M Module Meshtastic

### HELTEC nRF52840 SX1262 Mesh Node N5262M Module Meshtastic 868Mhz

***

### Product Link

{% embed url="https://openelab.io/products/heltec-mesh-node-n5262m-module" %}

### Description

**Mesh Node 5262M** is a module based on the nRF52840 and SX1262, supporting both Bluetooth and LoRa communication modes. It offers a rich set of pins and interfaces, featuring a 1.27mm pitch stamp hole design, making it compact and easy to integrate into your PCB. Having powerful long-distance communication capabilities, scalability, and low power design, which make it excellent in a wide range of application scenarios such as smart cities, agricultural monitoring, logistics tracking, etc.  It can be programmed via the Arduino IDE, PlatformIO, or MicroPython. You can directly use it for LoRa/LoRaWAN development with [Heltec nRF52 framework and libraries](https://github.com/HelTecAutomation/Heltec_nRF52), as well as to run some open source projects like Meshtastic.&#x20;

### Feature

* nRF52840 (Bluetooth)+SX1262(LoRa).
* 1.27mm pitch stamp hole design, making it compact and easy to integrate.
* Offer a rich set of pins and interfaces.
* Long transmission range, up to 3\~10km in open environments\[ Depends on the environment and noise interference.].
* The IPEX1.0 antenna connector provides a more flexible and efficient integration solution.
* Low power consumption, 9 uA in deep sleep.
* Operation condition: -40\~85℃, 90%RH(No condensing).
* Compatible with Arduino-IDE/PlatformIO/MicroPython, and we provide Arduino development frameworks and libraries.

### Specification

| Parameters            | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| MCU                   | nRF52840                                                   |
| LoRa Chip             | SX1262                                                     |
| Memory                | 1M ROM; 256kB SRAM                                         |
| Bluetooth             | Bluetooth 5, Bluetooth mesh, BLE.                          |
| Operating temperature | -40\~85℃                                                   |
|                       |                                                            |
| Operating Humidity    | 90%(No condensing)                                         |
| Power Supply          | 3.3V                                                       |
| Hardware Resource     | 3\*SPI, 2\*I2C, 2\*UART, 4\*PWM, QPSI, I2S, PDM, QDEC, Etc |
| Interface             | 2\*ANT (IPEX1.0)), 54\*1.27 stamp hole pin headers         |
| Dimensions            | 30\*20\*3.2 m3                                             |

### Pin Map

<figure><img src="../../.gitbook/assets/image (244).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Powerful communication capability" %}
* based on the nRF52840 and SX1262
* supports LoRa and Bluetooth
{% endtab %}

{% tab title="Powerful hardware support" %}
* offers a rich set of pins and interfaces
* featuring a 1.27mm pitch stamp hole design, making it compact and easy to integrate into your PCB.
{% endtab %}
{% endtabs %}

<figure><img src="../../.gitbook/assets/image (246).png" alt=""><figcaption></figcaption></figure>

### Resource&#x20;

* [User Manual](https://docs.heltec.cn/en/node/nrf/ht-n5262m/index.html)
* [Heltec nRF52 framework and Lib](https://github.com/HelTecAutomation/Heltec_nRF52)
* [SnapEmu IoT Platform](https://platform.snapemu.com/user/login)
* [Shematic Diagram](https://resource.heltec.cn/download/HT-N5262M/HT-N5262M_Schematic_Diagram.pdf)
* [Reference design](https://resource.heltec.cn/download/Mesh_Node_N5262M/Reference_design)
* [Datasheet](https://resource.heltec.cn/download/HT-N5262M/Datasheet/HT-N5262M_V1.0.pdf)
* [Related Resources](https://resource.heltec.cn/download/HT-N5262M)&#x20;

### FAQ

{% stepper %}
{% step %}
#### Definition of pins?

About SPI, I2C, UART, QPSI, I2S, PDM, QDEC: Each IO pin is preconfigured with IO\_MUX functionality, which means you can use any GPIO as peripheral pins. You just need to define these pins in your SDK. However, it’s important to note that once a pin is used, it may affect other functions associated with that pin.
{% endstep %}

{% step %}
What development methods does it support?

* Arduino
* PlatformIO
* MicroPython

In addition to [Meshtastic](https://meshtastic.org/) support, we have also developed a complete LoRaWAN protocol in the [nRF52 Arduino framework](https://github.com/HelTecAutomation/Heltec_nRF52).
{% endstep %}

{% step %}
Which pins does HT-N5262M support outputting PWM signals through?

These pins can also be used for other functions like I2C, SPI, etc., but need to be properly configured when used for PWM output:

**GPIO 0 – GPIO 31**: Most of these pins can be used as PWM outputs, but the specific pins that support PWM depend on the timer and channel configuration. Most of the pins can be configured as regular GPIOs and support timer output.

For certain PWM frequency and duty cycle requirements, the software can typically control which timer channel is mapped to which GPIO pin.
{% endstep %}
{% endstepper %}
