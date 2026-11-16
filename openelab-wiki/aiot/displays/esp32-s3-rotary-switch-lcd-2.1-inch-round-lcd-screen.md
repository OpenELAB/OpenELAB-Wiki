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

# ESP32-S3 Rotary Switch LCD 2.1 inch Round LCD Screen

### ESP32-S3 Rotary Switch LCD 2.1 inch Round LCD Screen

***

### Product Link

{% embed url="https://openelab.io/products/rotaryswitchscreen?_pos=1&_sid=bd023398d&_ss=r" %}

### Introduction

WT32S3-21S is a development board based on ESP32-S3 for visuall player temostat washing machine mirowawe ove.erste ! touch sreen. The solution is s often aplied to knob sren control of car

### Features

* Support rapid prototyping

### Pinout

* LCD interface

<figure><img src="../../.gitbook/assets/image (488).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (489).png" alt=""><figcaption></figcaption></figure>

* FPC interface

<figure><img src="../../.gitbook/assets/image (490).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (491).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (492).png" alt=""><figcaption></figcaption></figure>

### How to Use

#### Firmware Burning:

1. Connect the downloader (ZXACC-ESPDB) via a USB-Type C cable. And then connect the WT32S3-21S board with the downloader (ZXACC-ESPDB) through an MX1.25-7P cable. As the downloader (ZXACC-ESPDB) has automatic data flow processing capabilities, the firmware can be downloaded automatically through the ESP32 Flash Download Tools.

<figure><img src="../../.gitbook/assets/image (493).png" alt=""><figcaption></figcaption></figure>

2. As shown in Fig. 4: Select the firmware path at mark 1, and then fill in the burning address, usually 0X00. Note that this checkbox must be checked; Set the crystal frequency to be 40MHz at mark 2; Select 32Mbit for Flash size at mark 3; Select DIO for SPI MODE at mark 4; Select the COM port number recognized by the computer at mark 5; Select the baud rate at mark 6 (the higher the value is, the faster the firmware will be downloaded. Max. 1152000bps).&#x20;
3. &#x20;After the previous configuration, click START at mark 7 to start burning the firmware.&#x20;
4. Complete the above steps, and then press the reset button on the back of the development board to start running the firmware

<figure><img src="../../.gitbook/assets/image (494).png" alt=""><figcaption></figcaption></figure>

### Official Manual

{% file src="../../.gitbook/assets/WT32S3-21S(ZX2D10GE01R-W4848#B)+Datasheet-V1.5+EN.pdf" %}
