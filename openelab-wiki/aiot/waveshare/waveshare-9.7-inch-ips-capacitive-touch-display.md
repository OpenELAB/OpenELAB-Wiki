---
coverY: 0
layout:
  width: default
  cover:
    visible: false
    size: full
    mask: none
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

# Waveshare 9.7 inch IPS Capacitive Touch Display

{% hint style="info" %}
[**View Waveshare 9.7 inch IPS Capacitive Touch Display 768×1024 HDMI 10-Point Touch on OpenELAB**](https://openelab.io/products/9-7-inch-ips-capacitive-touch-display)

**Store SKU / option:** `Waveshare-26698`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare 9.7 inch IPS Capacitive Touch Display

***

### Product Link

{% embed url="https://openelab.io/products/9-7-inch-ips-capacitive-touch-display" %}

### Introduction

The 9.7-inch 768x1024 LCD is a high-resolution universal capacitive touch screen compatible with most standard HDMI devices.\
Featuring a small, thin body, toughened glass panel, excellent display performance, and smooth multi-point touch control effect.\
The baseboard comes with fixing nuts for integrated projects.

### Feature

* 9.7-inch IPS screen with 768x1024 hardware resolution.
* 10-point capacitive touch, up to 6H hardness toughened glass panel.
* Supports Raspberry Pi OS / Ubuntu / Kali and Retropie when used with Raspberry Pi.
* Supports Windows 11 / 10 / 8.1 / 8 / 7 when used as a computer monitor.
* Supports HDMI audio output, onboard 3.5mm headphone jack and 4PIN header.

### Specification

| Item                    | Description          | Unit   |
| ----------------------- | -------------------- | ------ |
| Model                   | 9.7inch 768x1024 LCD | /      |
| Dimensions              | 9.7                  | Inch   |
| Viewing angle           | 178                  | Deg    |
| Resolution              | 768x1024             | Pixels |
| Touch screen dimensions | 177.18(H)×226.15(V)  | mm     |
| Display area            | 147.64(H)×196.61(V)  | mm     |
| Pixel pitch             | 0.192(H)×0.192(V)    | mm     |
| Color gamut             | 70%                  | NTSC   |
| Brightness (Max)        | 400                  | cd/m²  |
| Contrast                | 900:1                | /      |
| Backlight               | OSD menu dimming     | /      |
| Refresh rate            | 60                   | Hz     |
| Display interface       | Standard HDMI port   | /      |
| Power port              | 5V Type-C interface  | /      |
| Power consumption       | 4                    | Watt   |

### Electrical Parameters

| Parameter             | Min. | Standard | Max. | Unit | Note   |
| --------------------- | ---- | -------- | ---- | ---- | ------ |
| Input Voltage         | 4.75 | 5.00     | 5.25 | V    | Note 1 |
| Input Current         | 750  | 800      | TBD  | mA   | Note 2 |
| Operating Temperature | 0    | 25       | 50   | ℃    | Note 4 |
| Storage Temperature   | -20  | 25       | 60   | ℃    | Note 4 |

•Note 1: Input voltage exceeding the maximum value or improper operation may cause permanent damage to the device.\
•Note 2: The input current should be ≥800mA, otherwise, it will lead to start-up failure or abnormal display, and a long time in an abnormal state may cause permanent damage to the device.\
•Note 3: Please do not put the display in a high-temperature and high-humidity storage environment for a long time, the display needs to work within the limit value, otherwise it will be possible to damage the display.<br>

### Onboard Interface

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=9.7inch-768x1024-LCD-details-21.jpg&#x26;width=800" alt=""><figcaption></figcaption></figure>

### User Manual

#### Working with Raspberry Pi

#### Hardware Connection

1\. Connect the Touch port to the USB port of the Raspberry Pi.\
2\. Connect the HDMI port to the HDMI port of the Raspberry Pi.<br>

<figure><img src="https://www.waveshare.com/w/upload/7/77/9.7inch-768x1024-LCD-01.jpg" alt=""><figcaption></figcaption></figure>

#### Software Setting

```
Raspberry Pi OS / Ubuntu / Kali and Retropie systems are supported for Raspberry Pi.
When the LCD works on these systems of Raspberry Pi, the resolution must be set manually, otherwise, it will result in incorrect display resolution and affect the experience.
```

1\. Please download the newest image from [the Official Raspberry Pi website](https://www.raspberrypi.com/software/operating-systems/).\
2\. Download the compressed file on the PC and unzip it to get the .img file.\
3\. Connect the TF card to the PC and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card. 4. Open [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip), choose the image prepared in the first step, and click "Write" to write the system image.\
5\. After programming, open the config.txt file in the root directory of the TF card and enter the following codes at the end of config.txt. Then, save and safely eject the TF card.<br>

```
hdmi_group=2
hdmi_mode=87
hdmi_force_hotplug=1
hdmi_timings=768 0 80 32 60 1024 0 10 10 10 0 0 0 60 0 59400000 0
```

6\. Insert the TF card into the Raspberry Pi, power on the Raspberry Pi, wait for a few seconds normally, and then it will display normally.

### Working with PC

#### Support Windows 11/10/8.1/8/7

1. Connect the Touch interface of the LCD to the USB interface of the PC, and Windows will automatically recognize the touch function.
2. Connect the HDMI interface of the LCD to the HDMI interface of the PC, and Windows will automatically recognize the display function.

* Note:
* Some PCs do not support HDMI devices plug-and-play, usually after rebooting the system can be used normally.
* If the power supply of the USB interface is insufficient, the LCD will flicker, after connecting the external 5V 1A power adapter to the LCD's Power interface, it can be restored to normal use.

#### Windows Touch Calibration

Take Windows 10 as an example:<br>

* 1\. Enter the Windows Settings of the system, type in the search bar, and click "Calibrate the screen for pen or touch input" (as shown in the picture below):

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* 2\. Click "Setup" in the pop-up "Tablet PC Settings" interface:

<figure><img src="https://www.waveshare.com/w/upload/9/99/Win10_touch02.png" alt=""><figcaption></figcaption></figure>

* 3\. The following text prompt will appear on the screen. Please tap the touch screen with your finger, and the computer will recognize it as a touch screen.

【Note】If the touch screen is blank, press the "Enter" key, and the text prompt will switch to the touch screen. (The screen which displays the text prompt will be used as a touch screen!)

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch03.png&#x26;width=800" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/9.7inch_768x1024_LCD) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                                                |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.waveshare.com/wiki/9.7inch%20768x1024%20LCD/9.7inch%20768x1024%20LCD_3D%20Drawing/9_7inch-768x1024-LCD.stp) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
