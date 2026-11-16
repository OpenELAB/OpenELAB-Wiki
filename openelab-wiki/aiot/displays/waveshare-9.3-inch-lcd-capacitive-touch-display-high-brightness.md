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

# Waveshare 9.3 inch LCD Capacitive Touch Display High Brightness

### Waveshare 9.3 inch LCD Capacitive Touch Display High Brightness

***

### Product Link

{% embed url="https://openelab.io/products/9-3-inch-lcd-capacitive-touch-display" %}

### Introduction

The 9.3-inch 1600x600 LCD is a small, high-resolution universal capacitive touch screen compatible with most standard HDMI devices. Featuring a small, thin body, toughened glass panel, excellent display performance, and smooth multi-touch effect. The baseboard comes with its own fixing nuts for integrated projects.

### Feature

* 9.3-inch IPS screen with 1600x600 hardware resolution.
* 10-point capacitive touch with up to 6H hardness toughened glass panel.
* Optical bonding technique for better display.
* Supports Raspberry Pi OS/Ubuntu/Kali and Retropie when used with Raspberry Pi.
* Supports Windows 11/10/8.1/8/7 when used as a computer monitor.
* Multi-language OSD menu support (can be used for power control, adjusting brightness/contrast, etc.)
* Supports HDMI audio output, onboard 3.5mm headphone jack, and 4PIN header.

<figure><img src="https://www.waveshare.com/w/upload/d/d7/9.3inch_1600x600_LCD02.png" alt=""><figcaption></figcaption></figure>

### Specification

| Item                      | Description                    | Unit   |
| ------------------------- | ------------------------------ | ------ |
| Model                     | 9.3inch 1600 × 600 LCD         | /      |
| Dimensions                | 9.3                            | Inch   |
| Viewing angle             | 178                            | Deg    |
| Resolution                | 1600x600                       | Pixels |
| Touch screen dimensions   | 239.00(H) × 94.00(V) × 1.45(D) | mm     |
| Display screen dimensions | 231.00(H) × 89.00(V) × 4.6(D)  | mm     |
| Display area              | 221.18(H) × 82.94(V)           | mm     |
| Pixel pitch               | 0.04608(H) × 0.13824(V)        | mm     |
| Color gamut               | 51%                            | NTSC   |
| Brightness (Max)          | 800                            | cd/m²  |
| Contrast                  | 1200                           | /      |
| Backlight                 | OSD menu dimming               | /      |
| Refresh rate              | 60                             | Hz     |
| Display interface         | Standard HDMI port             | /      |
| Power port                | 5V Type-C interface            | /      |
| Power consumption         | 4.2                            | Watt   |
| Weight                    | 280                            | g      |

### Electrical Parameters

| Parameter             | Min. Value | Standard Value | Max. Value | Unit | Note   |
| --------------------- | ---------- | -------------- | ---------- | ---- | ------ |
| Input Voltage         | 4.75       | 5.00           | 5.25       | V    | Note 1 |
| Input Current         | 800        | 850            | TBD        | mA   | Note 2 |
| Operating Temperature | 0          | 25             | 60         | ℃    | Note 3 |
| Storage Temperature   | -10        | 25             | 70         | ℃    | Note 3 |

•Note 1: Input voltage exceeding the maximum value or improper operation may cause permanent damage to the device.\
•Note 2: The input current should be ≥800mA, otherwise, it will lead to start-up failure or abnormal display, and a long time in an abnormal state may cause permanent damage to the device.\
•Note 3: Please do not put the display in a high-temperature and high-humidity storage environment for a long time, the display needs to work within the limit value, otherwise it will be possible to damage the display.

### EDID Sequence Parameters

If the system of the main control board can automatically identify the EDID for display, there is no need to set the relevant timing parameters additionally.

Otherwise, you can refer to the following EDID settings:

| Pixel Clock | H Addressable | H Blanking | V Addressable | V Blanking | H Front Porch | H Sync Width | V Front Porch | V Sync Width | H Image Size | V Image Size | H Border | V Border |
| ----------- | ------------- | ---------- | ------------- | ---------- | ------------- | ------------ | ------------- | ------------ | ------------ | ------------ | -------- | -------- |
| 71.00       | 1600          | 260        | 600           | 36         | 130           | 32           | 10            | 10           | 220          | 89           | 0        | 0        |

### Onboard Interface

<figure><img src="https://www.waveshare.com/w/upload/1/19/9.3inch_1600x600_LCD09.jpg" alt=""><figcaption></figcaption></figure>

### User Manual

#### Working with Raspberry Pi

#### Hardware Connection

1. Connect the Touch port to the USB interface of the Raspberry Pi.
2. Connect the HDMI port to the Raspberry Pi HDMI port.

<figure><img src="https://www.waveshare.com/w/upload/0/0f/9.3inch_1600x600_LCD10.jpg" alt=""><figcaption></figcaption></figure>

#### Software Setting

```
Raspberry Pi OS/Ubuntu/Kali and Retropie systems are supported for Raspberry Pi.
When the LCD works on these systems of Raspberry Pi, the resolution must be set manually, otherwise, it will result in incorrect display resolution and affect the experience.
```

1\. Please download the newest image from the [Official Raspberry Pi website](https://www.raspberrypi.com/software/operating-systems/).\
2\. Download the compressed file on the PC and unzip it to get the .img file.\
3\. Connect the TF card to the PC and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.\
4\. Open [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip), choose the image prepared in the first step, and click "Write" to write the system image.\
5\. After programming, open the config.txt file in the root directory of the TF card and enter the following codes at the end of config.txt. Then, save and safely eject the TF card.

```
hdmi_group=2
hdmi_mode=87
hdmi_cvt 1600 600 60 6 0 0 0
```

6\. Insert the TF card into the Raspberry Pi, power on the Raspberry Pi, wait for a few seconds normally, and then it will display normally.

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

### Working with PC

#### Support Windows 11/10/8.1/8/7

How to use:

1. Connect the Touch port of the LCD to the USB interface of the PC, and Windows will automatically recognize the touch function.
2. Connect the HDMI interface of the LCD to the HDMI interface of the PC, and Windows will automatically recognize the display function.

* Note:
* Some PCs do not support HDMI devices plug-and-play, usually after rebooting the system can be used normally.
* If the power supply of the USB interface is insufficient, the LCD will flicker, after connecting the external 5V 1A power adapter to the LCD's Power interface, it can be restored to normal use.

#### Windows Touch Calibration

Take Windows 10 as an example:<br>

* 1\. Enter the Windows setting of the system, type in the search bar, and click "Calibrate the screen for pen or touch input" (as shown in the picture below):

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* 2\. Click "Setup" in the pop-up "Tablet PC Settings" interface:

<br>

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

### Dimensions

<figure><img src="https://www.waveshare.com/w/upload/8/8a/9.3inch_1600x600_LCD11.jpg" alt=""><figcaption></figcaption></figure>

### Resource

* [9.3inch 1600x600 LCD 3D Drawing](https://files.waveshare.com/upload/5/58/9.3inch_1600x600_LCD_3D_Drawing.zip)
* [9.3inch 1600x600 LCD 3D Preview](https://files.waveshare.com/upload/b/bb/9.3inch_1600x600_LCD_3D_Preview.zip)

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/9.3inch_1600x600_LCD#accordion1"><strong>How to achieve PWM dimming for the 9.3-inch 1600x600 LCD?</strong></a></summary>

Remove the resistor in the red-boxed area as shown in the diagram, and externally solder the PWM to the solder pad at the arrow.

<img src="https://www.waveshare.com/w/upload/d/d7/9.3inch_1600x600_LCD-FAQ.png" alt="" data-size="original">

</details>
