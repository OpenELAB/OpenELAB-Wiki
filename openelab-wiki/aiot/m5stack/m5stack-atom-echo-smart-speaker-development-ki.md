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

# M5Stack ATOM Echo Smart Speaker Development Ki

{% hint style="info" %}
[**View M5Stack ATOM Echo Smart Speaker Development Ki on OpenELAB**](https://openelab.io/products/m5stackatomecho)

**Product model/family:** M5Stack ATOM Echo Smart Speaker Development Ki · **OpenELAB SKU:** `M5-C008-C`
{% endhint %}

## M5Stack ATOM Echo Smart Speaker Development Ki

***

## Product Link

{% embed url="https://openelab.io/products/m5stackatomecho" %}

## Introduction

**ATOM ECHO** is a Programmable Smart Speaker based on the M5ATOM design. With its compact form factor measuring only 24 \* 24 \* 17 mm, this speaker delivers impressive capabilities. Easily play music wirelessly using the BT capabilities of the [ESP32 ](https://shop.m5stack.com/)from your mobile phone or tablet.\
What sets ATOM ECHO apart is its programmability and integration with cloud platforms such as AWS and Baidu. Utilizing the built-in microphone and speaker, it enables voice interaction and AI functionality. Experience voice control, story-telling, and seamless integration with the Internet of Things (IoT).

<figure><img src="../../.gitbook/assets/image (761).png" alt=""><figcaption></figcaption></figure>

The speaker is equipped with an embedded RGB LED (SK6812), allowing for visual display of connection status. Beyond its role as a Bluetooth speaker, ATOM ECHO retains the control abilities of the Atom series. The convenient screw hole on the back facilitates easy installation for users.\
With ATOM ECHO, you have a powerful, programmable smart speaker that combines compact design, AI capabilities, and seamless IoT integration for an enhanced audio experience in any setting

## Features

* Light and compact
* Support STT services
* Based on [ESP32 arduino](https://shop.m5stack.com/), Support A2DP
* 2.4G Wi-Fi IEEE 802.11b/g/n
* Built-in microphone and speaker
* RGB LED status display indication
* Grove extension interface
* Record and playback
* Programmable key
* Programming platform:Arduino, ESP-IDF/ADF

## Specification <a href="#specification" id="specification"></a>

| Resources     | Parameter                                   |
| ------------- | ------------------------------------------- |
| SoC           | ESP-PICO-D4, 240MHz, Dual Core, Wi-Fi       |
| Flash         | 4MB                                         |
| Interface     | 1x IR-TX,1x Function Button,1x Reset Button |
| PinOut        | G21/G25/5V/GND, 3V3/G22/G19/G23/G33         |
| RGB LED       | SK6812                                      |
| Speaker       | 0.5W/NS4168 I2S                             |
| Microphone    | SPM1423 PDM                                 |
| Net weight    | 5g                                          |
| Gross weight  | 10g                                         |
| Product Size  | 24\*24\*17mm                                |
| Package Size  | 63\*63\*12mm                                |
| Case Material | Plastic ( PC )                              |

## Pinout

| DataOut | BCLK | DataIn | LRCK | RGB | Btn |
| ------- | ---- | ------ | ---- | --- | --- |
| G22     | G19  | G23    | G33  | G27 | G39 |

<figure><img src="../../.gitbook/assets/image (642).png" alt=""><figcaption></figcaption></figure>

## How to Use

## Driver Installation <a href="#driver-installation" id="driver-installation"></a>

Connect the device to the PC, open the device manager to install [FTDI driver ](https://ftdichip.com/drivers/vcp-drivers/)for the device. Take the win10 environment as an example, download the driver file that matches the operating system, unzip it, and install it through the device manager. (Note: In some system environments, the driver needs to be installed twice for the driver to take effect. The unrecognized device name is usually `M5Stack` or `USB Serial`. Windows recommends using the driver file to install directly in the device manager (custom Update), the executable file installation method may not work properly). [Click here to download FTDI driver](https://ftdichip.com/drivers/vcp-drivers/)

![](https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc/ftdi_01.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc/ftdi_02.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/core/m5stickc/ftdi_03.webp)

For MacOS users, please tick `System Preferences` -> `Security and Privacy` -> `General` -> `Allow downloadable apps from the following locations` -> `App Store and Approved Developer Options`.

## BT Speaker <a href="#bt-speaker" id="bt-speaker"></a>

The factory firmware is configured as a BT speaker by default. Users can connect devices such as mobile phones, tablets, PCs and so on with ATOM ECHO to output audio to ATOM ECHO for playback.

#### Firmware <a href="#firmware" id="firmware"></a>

To burn the firmware, download the corresponding easyloader according to the operating system

{% embed url="https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/ATOM_BASE/EasyLoader_ECHO_Bluetooth_Speaker.exe" %}

#### How to use BT speakers <a href="#how-to-use-bt-speakers" id="how-to-use-bt-speakers"></a>

Turn on the power, the indicator light is red at this time, turn on the device BT, search for nearby devices, the BT device named M5\_SPEAKER\_T1 is ATOM ECHO. After clicking connect or pairing, ATOM ECHO will send out a BT pairing request. Confirm pairing to establish a BT connection. At this time, the indicator light turns green to indicate that the connection is normal. Once the connection is established, ATOM ECHO can be used as an audio playback device. (Currently the firmware does not support making and receiving calls as a hands-free device)
