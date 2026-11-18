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

# M5Stack AtomS3 Lite ESP32S3 Dev Kit

{% hint style="info" %}
[**View M5Stack AtomS3 Lite ESP32S3 Dev Kit on OpenELAB**](https://openelab.io/products/m5stack-atoms3-lite)

**Model/kit:** M5Stack AtomS3 Lite ESP32S3 Dev Kit · **OpenELAB SKU:** `M5-C124`
{% endhint %}

## M5Stack AtomS3 Lite ESP32S3 Dev Kit

***

## Product Link

{% embed url="https://openelab.io/products/m5stack-atoms3-lite" %}

## Introduction

ATOM S3 Lite is a versatile programmable controller that belongs to the Atom Series in the M5Stack Development Kit lineup. Powered by the [ESP32 S3](https://shop.m5stack.com/products/m5stamp-esp32s3-module) FN8 scheme, this compact controller measures only 24x24x9.5mm, making it an ideal choice for space-constrained projects. It boasts an impressive 8MB SPI flash memory, providing ample storage capacity for your applications. With integrated Wi-Fi functionality and a built-in 3D antenna, the ATOM S3 Lite ensures seamless connectivity and reliable wireless communication.\
\
Equipped with a 5V to 3.3V power circuit, the ATOM S3 Lite offers stable and efficient power management. It features useful components such as infrared emitting light, RGB status indicators, a programmable button, and versatile GROVE/HY2.0-4P interfaces. These features enable easy integration with various sensors, actuators, and external devices, expanding the possibilities for your projects. The product also includes a power supply and 6 GPIO headers on the bottom, facilitating convenient and flexible expansion applications.

<figure><img src="../../.gitbook/assets/image (659).png" alt=""><figcaption></figcaption></figure>

With a convenient Type-C interface, the ATOM S3 Lite allows hassle-free program downloading and seamless serial port communication. The device also comes with an M2 screw hole on the back, providing a secure mounting option for your projects. Whether you're working on embedded smart devices, IoT applications, or prototyping projects, the ATOM S3 Lite is a reliable and compact solution that empowers your creativity and enables endless possibilities.

## Features

* Developed based on ESP32-S3FN8
* Comes with USB download function
* Programmable button
* Infrared emission function
* Expandable pins and interfaces
* Development platform: Arduino, UIFlow

## Specification <a href="#specification" id="specification"></a>

| Resources             | Parameters           |
| --------------------- | -------------------- |
| MCU                   | ESP32-S3FN8          |
| RGB                   | WS2812B-2020         |
| DCDC                  | SY8089               |
| Operating temperature | 0°C \~ 40°C          |
| Supply voltage        | 5V                   |
| Power supply mode     | TYPE C               |
| Output voltage        | 3.3V                 |
| IO interface × 6      | G5/G6/G7/G8/G38/G39  |
| Product Size          | 24mm × 24mm ×9.5mm   |
| Package Size          | 65mm × 44.5mm × 14mm |
| Product Weight        | 5.3g                 |
| Package Weight        | 9.5g                 |

## Pinout

<figure><img src="../../.gitbook/assets/image (753).png" alt=""><figcaption></figcaption></figure>

## Dimensions

<figure><img src="../../.gitbook/assets/image (752).png" alt=""><figcaption></figcaption></figure>

## How to Use

## 1. Preparations <a href="#preparations" id="preparations"></a>

* Arduino IDE Installation: Refer to the [Arduino IDE Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_ide)to complete the IDE installation.
* Board Manager Installation: Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/en/arduino/arduino_board)to complete the IDE, M5Stack Board Manager installation, and select the development board `M5AtomS3`.
* Dependency Library Installation: Refer to the [Library Management Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_library)to complete the installation of the `M5AtomS3` driver library.

## 2. Download Mode <a href="#download-mode" id="download-mode"></a>

* Press and hold the reset button (about 2 seconds) until the internal green LED lights up, then release it. The device is now in download mode, ready for burning.

#### M5AtomS3 / M5AtomS3 Lite <a href="#m5atoms3--m5atoms3-lite" id="m5atoms3--m5atoms3-lite"></a>

<figure><img src="../../.gitbook/assets/image (754).png" alt=""><figcaption></figcaption></figure>

## 3. Download Control Board <a href="#download-control-board" id="download-control-board"></a>

Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/en/arduino/arduino_board)to complete the IDE, M5Stack Board Manager installation, and select the development board `M5AtomS3`.

<figure><img src="../../.gitbook/assets/image (755).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (756).png" alt=""><figcaption></figcaption></figure>

## 4. Install Library Files <a href="#install-library-files" id="install-library-files"></a>

Dependency Library Installation: Refer to the [Library Management Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_library)to complete the installation of the `M5AtomS3` driver library.

<figure><img src="../../.gitbook/assets/image (757).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (758).png" alt=""><figcaption></figcaption></figure>

## 5. Port Selection <a href="#port-selection" id="port-selection"></a>

Connect the device to the computer via USB cable. After completing the driver installation, you can select the corresponding device port in the Arduino IDE.

<figure><img src="../../.gitbook/assets/image (759).png" alt=""><figcaption></figcaption></figure>

## 6. Program Compilation & Burning <a href="#program-compilation-burning" id="program-compilation-burning"></a>

Open the example program “LEDDisplay” in the driver library. Click the upload button to automatically compile and burn the program.

<figure><img src="../../.gitbook/assets/image (760).png" alt=""><figcaption></figcaption></figure>

<br>
