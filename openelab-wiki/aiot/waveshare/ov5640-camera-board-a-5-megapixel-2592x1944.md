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

# OV5640 Camera Board (A), 5 Megapixel (2592x1944)

{% hint style="info" %}
[**View Waveshare OV5640 Camera Board A 5MP Image Sensor Module on OpenELAB**](https://openelab.io/products/ov5640camera)

**Store SKU / option:** `Waveshare-13926`. Match the purchased model and revision to the official reference below.
{% endhint %}

### OV5640 Camera Board (A), 5 Megapixel (2592x1944)

***

### Product Link

{% embed url="https://openelab.io/products/ov5640camera?_pos=1&_sid=b7b8b9517&_ss=r" %}

### Introduction

OV5640 Camera Board (A) is a CMOS camera uses sensor OV5640, takes 5 Megapixel image in QSXGA mode (2592x1944), uses DVP data interface and SCCB control interface. It supports RGB565\RGB555\RGB444, YUV (422/420), YCbCr422 and JPEG pixel/image formats. The module can adjust white balance, saturation, hue, sharpness, and gamma correction. The resolution and frame rate are adjustable as well

<figure><img src="../../.gitbook/assets/image (806).png" alt=""><figcaption></figcaption></figure>

### Features

* Pixels: 5M
* Resolution: 2592x1944
* CCD: OV5640
* uses 1.4 x 1.4 um pixels OmniBSI technology, high sensitivity, low crosstalk and noise
* supports automatic exposure, white balance, elimination of light stripes, black level calibration, band pass filter, and so on.
* supports adjustment of saturation, hue, gamma correction, sharpness, and lens calibration, etc
* supports image zoom, shifting and window settings
* Camera:
  * CCD size: 1/4 inches
  * Aperture (F): 3.0
  * Focal Length: 3.8mm
  * View angle (diagonal): 60 degrees
* Output modes:
  * YUV (422/420)/YCbCr422
  * RGB565/555/444
  * CCIR656
  * RAW RGB
  * Compressed Data
* Operating voltage: 3.3V
* Control interface: SCCB (compatible with I2C)
* Data interface: DVP 8-bits
* Size: 35.70 mm × 23.90 mm

### Pinout

<figure><img src="../../.gitbook/assets/image (805).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (804).png" alt=""><figcaption></figcaption></figure>

### How to Use

#### USAGE DESCRIPTION

This module provides STM32F407\429\746 routines, here are demonstration examples for Waveshare Open746I-C development board:

1. Connect the module to DCMI port of the development board, connect USB-to-serial adapter to USART1 serial port on the board and to USB port on computer.
2. Open UartDisplay (camera data receiving software) on your computer, set number of port and its rate 921600, and the open the port.
3. Download the program into the board, push RESET button and after some initialization period it shows following data:
4. Push WAKE UP button and the board will start to sent continuously JPEG images via serial port and UartDisplay will show them
5. Push middle key of the board’s joystick and OV5640 module will keep image on LCD screen in RGB565 mode continuously.

<figure><img src="../../.gitbook/assets/image (807).png" alt=""><figcaption><p>Open756I-C+7inch LCD</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (808).png" alt=""><figcaption><p>Open746I-C+4.3inch LCD</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (809).png" alt=""><figcaption><p>Open407V-C+3.2inch LCD</p></figcaption></figure>

## Official documentation and development resources

Use [Introduction](https://www.waveshare.com/wiki/OV5640_Camera_Board_\(A\)) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need     | Model-specific reference                                                                               |
| -------------------- | ------------------------------------------------------------------------------------------------------ |
| Electrical schematic | [Read electrical schematic](https://files.waveshare.com/upload/1/1e/OV5640-Camera-Board-Schematic.pdf) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
