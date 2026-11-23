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

# Waveshare 8DP-CAPLCD 8 inch Capacitive Touch Display

{% hint style="info" %}
[**View Waveshare 8 inch IPS Capacitive Touch Display 1280×800 HDMI on OpenELAB**](https://openelab.io/products/8-inch-capacitive-touch-display)

**Store SKU / option:** `Waveshare-23741`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare 8DP-CAPLCD 8 inch Capacitive Touch Display

***

### Product Link

{% embed url="https://openelab.io/products/8-inch-capacitive-touch-display" %}

### Introduction

8DP-CAPLCD is a mini universal capacitive touch screen with HD resolution and is compatible with most standard HDMI devices.\
It boasts a toughened glass capacitive touch panel that results in a smooth multi-touch effect while being thin and lightweight.\
The baseboard comes with fixed nuts, which enables users to integrate it into an all-in-one project more conveniently.

### Features

* 8-inch IPS screen with a hardware resolution of 1280 x 800.
* 10-point capacitive touch, with toughened glass panel, hardness up to 6H.
* Adopting optical bonding touch technology, the display effect is better.
* Supports Raspberry Pi OS / Ubuntu / Kali and Retropie when used with Raspberry Pi.
* Supports Windows 11 / 10 / 8.1 / 8 / 7 when used as a computer monitor.
* Support multi-language OSD menu (can be used for power control, adjusting brightness/contrast, etc.)
* Support HDMI audio output, onboard 3.5mm headphone jack, and 4PIN speaker jack.

<figure><img src="https://www.waveshare.com/w/upload/5/5f/8DP-CAPLCD110.png" alt=""><figcaption></figcaption></figure>

### Parameters

| Item                    | Description                       | Unit   |
| ----------------------- | --------------------------------- | ------ |
| Model                   | 8DP-CAPLCD                        | /      |
| Size                    | 8.0                               | Inch   |
| Viewing Angle           | 178                               | Deg    |
| Resolution              | 1280 x 800                        | Pixels |
| Touch screen dimensions | 194.00 (H) × 119.00 (V) × 2 (D)   | mm     |
| Display dimensions      | 114.66 (H) × 184.16 (V) × 2.6 (D) | mm     |
| Display area            | 107.64 (H) × 172.22 (V)           | mm     |
| Pixel pitch             | 0.13455 (H) × 0.13455 (V)         | mm     |
| Color gamut             | 62%                               | NTSC   |
| Maximum brightness      | 400                               | cd/m²  |
| Contrast                | 1200:1                            | /      |
| Backlight adjustment    | OSD menu dimming                  | /      |
| Refresh Rate            | 60                                | Hz     |
| Display port            | Standard HDMI port                | /      |
| Power port              | 5V Type-C power supply            | /      |
| Power Consumption       | 4                                 | Watt   |
| Weight                  | 406                               | g      |

### Electrical Specifications

| Parameter             | Minimum Value | Standard | Maximum Value | Unit | Note   |
| --------------------- | ------------- | -------- | ------------- | ---- | ------ |
| Input Voltage         | 4.75          | 5.00     | 5.25          | V    | Note 1 |
| Input Current         | 750           | 800      | TBD           | mA   | Note 2 |
| Operating Temperature | 0             | 25       | 60            | ℃    | Note 3 |
| Storage Temperature   | -10           | 25       | 70            | ℃    | Note 3 |

•Note 1: Input voltage exceeding the maximum value or improper operation may cause permanent damage to the device.\
•Note 2: The input current must be ≥750mA, otherwise, it will cause startup failure or abnormal display, and it may cause permanent damage to the device if it is in an abnormal state for a long time.\
•Note 3: Please do not store the display in a high-temperature and high-humidity environment for a long time. The display must work within the limited value range, otherwise, the display may be damaged.

### EDID Sequence Parameter

If the system of the main control board can automatically identify the EDID for display, there is no need to additionally set related sequence parameters.\
Otherwise, you can refer to the following EDID settings:

| Pixel Clock | H Addressable | H Blanking | V Addressable | V Blanking | H Front Porch | H Sync Width | V Front Porch | V Sync Width | H Image Size | V Image Size | H Border | V Border |
| ----------- | ------------- | ---------- | ------------- | ---------- | ------------- | ------------ | ------------- | ------------ | ------------ | ------------ | -------- | -------- |
| 77.00       | 1280          | 232        | 800           | 56         | 160           | 32           | 20            | 6            | 294          | 165          | 0        | 0        |

### Interface Introduction

<figure><img src="https://www.waveshare.com/w/upload/8/84/8DP-CAPLCD10.jpg" alt=""><figcaption></figcaption></figure>

### User Guide

#### Working With Raspberry Pi

Hardware Connection

1. Connect the Touch port of the display to the USB port of the Raspberry Pi.
2. Connect the display to the Raspberry Pi via the HDMI interface.

<figure><img src="https://www.waveshare.com/w/upload/9/92/8DP-CAPLCD010.png" alt=""><figcaption></figcaption></figure>

Software Setting

```
Support Raspberry Pi OS/Ubuntu/Kali and Retropie system.
When LCD works with the Raspberry Pi systems, you must set the resolution manually. Otherwise, the resolution will be wrong and it will affect your experience.
```

1\. Please download the latest image in the [official Raspberry Pi website](https://www.raspberrypi.com/software/operating-systems/).\
2\. Download the compressed file on the PC and unzip it to get the ".img" file.\
3\. Connect the TF card to the PC and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.\
4\. Open [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip), select the system image prepared in the first step and click "write" to program the system image.\
5\. After programming, you can open the "config.txt" file in the TF card root directory. Add the following code at the end of "config.txt", save it, and then safely remove the TF card.

```
hdmi_group=2
hdmi_mode=87
hdmi_cvt 1280 800 60 6 0 0 0
hdmi_drive=1
```

6\. Insert the TF card into the Raspberry Pi, power on the Raspberry Pi, and wait for a few seconds for a normal display.

#### Linux Software Brightness Adjustment

Using the DDC/CI program, here is an example of the [ddcutil tool](http://www.ddcutil.com/).

```
#Install ddcutil tool:
sudo apt-get install ddcutil -y
#Detect DDC/CI monitor support:
sudo ddcutil detect
#Adjust monitor brightness, <value> should be modified to 0-100 
sudo ddcutil setvcp 10 <value>
```

For more information about ddcutil function commands, please click [here](http://www.ddcutil.com/commands/).

### Working With PC

#### Support Windows 11/10/8.1/8/7

**How To Use**

1. Connect the Touch port of the LCD to the USB port of the PC, and Windows will automatically identify the touch function.
2. Connect the LCD to the PC via the HDMI interface, and Windows will automatically identify the display function.

* Note:
* Some PCs do not support the plug-and-play function of the HDMI device, but it can be used normally after restarting the system.
* If the power supply of the USB port is insufficient, the LCD will flicker. After connecting an external 5V 1A power adapter to the Power interface of the LCD, it can be operated normally.

#### Windows Touch Calibration

Take Windows 10 as an example:

* 1\. Enter the Windows settings of the system, type in the search bar, and click "Calibrate the screen for pen or touch input" (as shown in the picture below):

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* 2\. Click "Setup" in the pop-up "Tablet PC Settings" interface:

<figure><img src="https://www.waveshare.com/w/upload/9/99/Win10_touch02.png" alt=""><figcaption></figcaption></figure>

* 3\. The following text prompt will appear on the screen. Please tap the touch screen with your finger, and the computer will recognize it as a touch screen.

【Note】If the touch screen is blank, press the "Enter" key, and the text prompt will switch to the touch screen. (The screen which displays the text prompt will be used as a touch screen!)

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch03.png&#x26;width=800" alt=""><figcaption></figcaption></figure>

#### Windows Software Brightness Adjustment

* 1\. Download and install DDC/CI applications, such as the open-source [Twinkle Tray](https://twinkletray.com/).
* 2\. Open the software dimming icon, it will recognize the Waveshare monitor and adjust the monitor backlight brightness by sliding the scroll bar.

<figure><img src="https://www.waveshare.com/w/upload/b/b9/8HP-CAPLCD_Monitor04.png" alt=""><figcaption></figcaption></figure>

* 3\. You can also enter the DDC/CI application settings screen to enable contrast adjustment, volume adjustment, and other functions.

<figure><img src="https://www.waveshare.com/w/upload/e/e3/8HP-CAPLCD_Monito03.png" alt=""><figcaption></figcaption></figure>

### Outline Dimensions

<figure><img src="https://www.waveshare.com/w/upload/b/b8/8DP-CAPLCD_90.jpg" alt=""><figcaption></figcaption></figure>

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/8DP-CAPLCD#accordion1"><strong>How to realize PWM dimming for 8DP-CAPLCD?</strong></a></summary>

Disconnect the resistor in the red box shown below and solder the external PWM to the pads indicated by the arrow

<img src="https://www.waveshare.com/w/upload/8/89/8DP-CAPLCD_FAQ01.png" alt="" data-size="original">

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/8DP-CAPLCD#accordion2"><strong>What speaker is compatible with the speaker header of 8DP-CAPLCD, and what is the output power consumption?</strong></a></summary>

4PIN PH1.25 speaker connector, wiring order: ＋ - - +, up to 2 x 2.3W power consumption.

</details>

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/8DP-CAPLCD) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
