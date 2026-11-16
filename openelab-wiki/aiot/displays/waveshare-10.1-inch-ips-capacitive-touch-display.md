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

# &#x20;Waveshare 10.1 inch IPS Capacitive Touch Display

### Waveshare 10.1 inch IPS Capacitive Touch Display

***

### Product Link

{% embed url="https://openelab.io/products/101inchipscapacitivetouchdisplay" %}

### Introduction

#### Overview

The 10.1HP-CAPLCD Monitor is a small, high-resolution, wide-color gamut general-purpose capacitive touch monitor compatible with most standard HDMI devices. Comes with an aluminum alloy case, toughed glass panel, excellent display performance, and smooth multi-touch effect.

### Features

* 10.1-inch wide color gamut IPS panel, 1280 x 800 hardware resolution.
* Supports standard HDMI and full-featured Type-C display signals
* 10-point capacitive touch, toughened glass panel with 6H hardness.
* Adopts optical bonding technique for better display.
* Supports Raspberry Pi OS / Ubuntu / Kali and Retropie when used with Raspberry Pi.
* Supports Windows 11 / 10 / 8.1 / 8 / 7 when used as a computer monitor.
* Multi-language OSD menu support (for power control, adjusting brightness/contrast, etc.)
* Supports HDMI/Type-C audio output, onboard 3.5mm headphone jack, and 4PIN speaker jack.

<figure><img src="https://www.waveshare.com/w/upload/7/78/10.1HP-CAPLCD_Monitor01.png" alt=""><figcaption></figcaption></figure>

### Specification

| Item                 | Description                      | Unit   |
| -------------------- | -------------------------------- | ------ |
| Model                | 10.1HP-CAPLCD Monitor            | /      |
| Dimensions           | 10.1                             | Inch   |
| Viewing Angle        | 178                              | Deg    |
| Resolution           | 1280 x 800                       | Pixels |
| Overall Dimensions   | 241.00(H) × 149.00(V) × 11.80(D) | mm     |
| Display Dimensions   | 228.6(H) × 143.0(V)              | mm     |
| Display Area         | 135.36(H) × 216.58(V)            | mm     |
| Pixel Pitch          | 0.1175(H) x 0.1088(V)            | mm     |
| Color Gamut          | 82%                              | NTSC   |
| Max. Brightness      | 350                              | cd/m²  |
| Contrast             | 800:1                            | /      |
| Backlight Adjustment | OSD Menu                         | /      |
| Refreshing Rate      | 60                               | Hz     |
| Display Interface    | Standard HDMI Interface          | /      |
| Power Port           | 5V Type-C                        | /      |
| Power Consumption    | 4                                | Watt   |
| Weight               | 809                              | g      |

### Electrical Parameters

| Parameter             | Min. Value | Standard Value | Max. Value | Unit | Note   |
| --------------------- | ---------- | -------------- | ---------- | ---- | ------ |
| Input Voltage         | 4.75       | 5.00           | 5.25       | V    | Note 1 |
| Input Current         | 750        | 800            | TBD        | mA   | Note 2 |
| Operating Temperature | 0          | 25             | 60         | ℃    | Note 3 |
| Storage Temperature   | -10        | 25             | 70         | ℃    | Note 3 |

•Note 1: Input voltage exceeding the maximum value or improper operation may cause permanent damage to the device.\
•Note 2: The input current should be ≥750mA, otherwise it will lead to start-up failure or abnormal display, and a long time in an abnormal state may cause permanent damage to the device.\
•Note 3: Please do not put the display in a high temperature and high humidity storage environment for a long time, the display needs to work within the limit value, otherwise it will be possible to damage the display.

### EDID Sequence Parameters

If the system of the main control board can automatically identify the EDID for display, there is no need to set the relevant timing parameters additionally.

Otherwise, you can refer to the following EDID settings:

| Pixel Clock | H Addressable | H Blanking | V Addressable | V Blanking | H Front Porch | H Sync Width | V Front Porch | V Sync Width | H Image Size | V Image Size | H Border | V Border |
| ----------- | ------------- | ---------- | ------------- | ---------- | ------------- | ------------ | ------------- | ------------ | ------------ | ------------ | -------- | -------- |
| 77.00       | 1280          | 232        | 800           | 56         | 160           | 32           | 20            | 6            | 294          | 165          | 0        | 0        |

### Onboard Interface

<figure><img src="https://www.waveshare.com/w/upload/8/84/8DP-CAPLCD10.jpg" alt=""><figcaption></figcaption></figure>

### User Manual

#### Working with PC

#### Support Windows 11/10/8.1/8/7

How to Use

1. Connect the Touch port of the LCD to the USB interface of the PC, and Windows will automatically identify the touch function.
2. Connect the LCD's HDMI interface to the PC's HDMI interface, and Windows will automatically identify the display function.

* Note:
* Some PCs do not support HDMI devices plug-and-play, usually after rebooting the system can be used normally.
* If the power supply of the USB interface is insufficient, the LCD will flicker, after connecting the external 5V 1A power adapter to the LCD's Power interface, it can be restored to normal use.

#### Windows Software Brightness Adjustment

* 1\. Download and install DDC/CI applications, such as the open-source [Twinkle Tray](https://twinkletray.com/).
* 2\. Open the software dimming icon, it will recognize the Waveshare monitor and adjust the monitor backlight brightness by sliding the scroll bar.

<figure><img src="https://www.waveshare.com/w/upload/b/b9/8HP-CAPLCD_Monitor04.png" alt=""><figcaption></figcaption></figure>

* 3\. You can also enter the DDC/CI application settings screen to enable contrast adjustment, volume adjustment, and other functions.

<figure><img src="https://www.waveshare.com/w/upload/e/e3/8HP-CAPLCD_Monito03.png" alt=""><figcaption></figcaption></figure>

#### Windows Touch Calibration

Take Windows 10 as an example:

* 1\. Enter the Windows setting of the system, type in the search bar, and click "Calibrate the screen for pen or touch input" (as shown in the picture below):

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* 2\. Click "Setup" in the pop-up "Tablet PC Settings" interface:

<figure><img src="https://www.waveshare.com/w/upload/9/99/Win10_touch02.png" alt=""><figcaption></figcaption></figure>

* 3\. The following text prompt will appear on the screen. Please tap the touch screen with your finger, and the computer will recognize it as a touch screen.

【Note】If the touch screen is blank, press the "Enter" key, and the text prompt will switch to the touch screen. (The screen which displays the text prompt will be used as a touch screen!)<br>

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch03.png&#x26;width=800" alt=""><figcaption></figcaption></figure>

### Working with Raspberry Pi

#### Hardware Connection

1. Connect the Touch port to the USB interface of the Raspberry Pi.
2. Connect the HDMI interface to the HDMI interface of the Raspberry Pi.

<figure><img src="https://www.waveshare.com/w/upload/4/43/8HP-CAPLCD_Monitor05.jpg" alt=""><figcaption></figcaption></figure>

#### Software Setting

```
Raspberry Pi OS / Ubuntu / Kali and Retropie systems are supported for Raspberry Pi.
When the LCD works on these systems of Raspberry Pi, the resolution must be set manually, otherwise, it will result in incorrect display resolution and affect the experience.
```

1\. Please download the newest image from the [Official Raspberry Pi website](https://www.raspberrypi.com/software/operating-systems/).\
2\. Download the compressed file on the PC and unzip it to get the .img file.\
3\. Connect the TF card to the PC and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.\
4\. Open [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip), choose the image prepared in the first step, and click "Write" to program the system image.\
5\. After programming, open the config.txt file in the root directory of the TF card and enter the following codes at the end of config.txt. Then, save and safely eject the TF card.<br>

```
hdmi_group=2
hdmi_mode=87
hdmi_cvt 1280 800 60 6 0 0 0
hdmi_drive=1
```

6\. Insert the TF card into the Raspberry Pi, power up the Raspberry Pi, wait for a few seconds normally and then it will display normally.

#### Linux Software Brightness Adjustment

Using the DDC/CI program, here is an example of the [ddcutil tool](http://www.ddcutil.com/).

```
#Install ddcutil tool:
sudo apt-get install ddcutil -y
#Detection support for DDC/CI monitors:
sudo ddcutil detect
#Adjust the monitor brightness, <value> should be modified to 0-100 value
sudo ddcutil setvcp 10 <value>
```

For more information about ddcutil function commands, please check [http://www.ddcutil.com/commands/](http://www.ddcutil.com/commands/).

### One Cable Connection

Using the matching dual-plug Type-C cable, connect the monitor's DISPLAY\&TOUCH connector to the master's full-featured Type-C connector. Wait for a few seconds to enter the display interface.\
\
Note: Please make sure your main control supports a full-featured Type-C interface and your phone needs to support the wired projection function.

<figure><img src="https://www.waveshare.com/w/upload/e/e6/8HP-CAPLCD_Monitor_06.jpg" alt=""><figcaption></figcaption></figure>

## Dimensions

<figure><img src="https://www.waveshare.com/w/upload/c/c7/10.1HP-CAPLCD_Monitor09.jpg" alt=""><figcaption></figcaption></figure>
