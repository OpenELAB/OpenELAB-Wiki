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

# Waveshare 8 inch 2K IPS Capacitive Touch Display

{% hint style="info" %}
[**View Waveshare 8 inch 2K IPS Capacitive 1536×2048 Touch Display on OpenELAB**](https://openelab.io/products/2k-ips-capacitive-touch-display)

**Store SKU / option:** `Waveshare-23740`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare 8 inch 2K IPS Capacitive Touch Display

***

{% embed url="https://openelab.io/products/2k-ips-capacitive-touch-display" %}

### Introduction

This product is a general-purpose 8-inch HDMI display with a resolution of 1536 x 2048 and a capacitive touch panel. Support Raspberry Pi, and it also can be used as a computer monitor.

### Feature

* 8-inch IPS screen, 1536 x 2048 hardware resolution.
* 10-point capacitive touch, with toughened glass panel, hardness up to 6H.
* Adopting optical bonding technology, the display effect is better.
* Supports Raspberry Pi OS / Ubuntu and Kali when used with Raspberry Pi4B.
* Supports Windows 11 /10 /8.1 / 8 / 7 when used as a computer monitor.
* Built-in high-fidelity speakers with 3.5mm audio, support HDMI audio output.
* Full metal CNC alloy enclosure.

### Parameters

| Item                 | Description                      | Unit   |
| -------------------- | -------------------------------- | ------ |
| Model                | 8inch 1536 x 2048 LCD            | /      |
| Size                 | 8.0                              | Inch   |
| Viewing Angle        | 178                              | Deg    |
| Resolution           | 1536 x 2048                      | Pixels |
| Dimensions           | 190.00 (H) × 128.00 (V) × 11 (D) | mm     |
| Display area         | 159.74 (H) × 119.80 (V)          | mm     |
| Pixel Pitch          | 0.026 (V) x 0.078 (H)            | mm     |
| Color Gamut          | 66%                              | NTSC   |
| Maximum Brightness   | 470                              | cd/m²  |
| Contrast             | 1000:1                           | /      |
| Backlight Adjustment | Button dimming                   | /      |
| Refresh Rate         | 60                               | Hz     |
| Display Port         | Standard HDMI port               | /      |
| Power Port           | 5V Type-C power supply           | /      |
| Power Consumption    | 4                                | Watt   |
| Weight               | 311                              | g      |

### Electrical Specifications

| Parameter             | Minimum | Standard | Maximum | Unit | Note   |
| --------------------- | ------- | -------- | ------- | ---- | ------ |
| Input Voltage         | 4.75    | 5.00     | 5.25    | V    | Note 1 |
| Input Current         | 750     | 800      | TBD     | mA   | Note 2 |
| Operating Temperature | 0       | 25       | 60      | ℃    | Note 3 |
| Storage Temperature   | -10     | 25       | 70      | ℃    | Note 3 |

•Note 1: Input voltage exceeding the maximum value or improper operation may cause permanent damage to the device.\
•Note 2: The input current must be ≥750mA, otherwise, it will cause booting failure or abnormal display, and it may cause permanent damage to the device if it is in an abnormal state for a long time.\
•Note 3: Please do not store the display in a high-temperature and high-humidity environment for a long time. The display must work within the limited value range, otherwise, it may be damaged.

### EDID Sequence Parameters

If the system of the main control board can automatically recognize the EDID for display, there is no need to additionally set related timing parameters.

Otherwise, you can refer to the following EDID settings:

| Pixel Clock | H Addressable | H Blanking | V Addressable | V Blanking | H Front Porch | H Sync Width | V Front Porch | V Sync Width | H Image Size | V Image Size | H Border | V Border |
| ----------- | ------------- | ---------- | ------------- | ---------- | ------------- | ------------ | ------------- | ------------ | ------------ | ------------ | -------- | -------- |
| 295.00      | 1536          | 724        | 2048          | 80         | 200           | 64           | 60            | 10           | 294          | 165          | 0        | 0        |

### Interface Introduction

<figure><img src="https://www.waveshare.com/w/upload/9/98/8inch_1536x2048_LCD01.jpg" alt=""><figcaption></figcaption></figure>

#### USER Guide

Hardware Connection

1. Connect the Touch port to the USB port of the Raspberry Pi.
2. Connect the HDMI port to the HDMI port of the Raspberry Pi.

<figure><img src="https://www.waveshare.com/w/upload/3/34/8inch_1536x2048_LCD02.jpg" alt=""><figcaption></figcaption></figure>

Software Setting

```
Raspberry Pi OS / Ubuntu / Kali and Retropie systems are supported.
When the LCD works on systems such as Raspberry Pi, the resolution must be manually set, otherwise, it will cause incorrect display resolution and affect the experience.
```

1\. Please download the newest image from [Raspberry Pi official website](https://www.raspberrypi.com/software/operating-systems/).\
2\. Download the compressed file to the PC and decompress it to get the .img file.\
3\. Connect the TF card to the PC, and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.\
4\. Open the [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip) software, select the system image prepared in step 1, and click write to burn the system image.\
5\. After the programming is completed, open the config.txt file in the root directory of the TF card, add the following code at the end of config.txt, save and eject the TF card safely.

```
hdmi_group=2
hdmi_mode=87
config_hdmi_boost=4
hdmi_pixel_freq_limit=356000000
hdmi_timings=1536 0 500 66 158 2048 0 60 10 10 0 0 0 60 0 295000000 3
max_framebuffer_width=1536
max_framebuffer_height=2048
framebuffer_width=1536
framebuffer_height=2048
```

6\. Insert the TF card into the Raspberry Pi, power on the Raspberry Pi, and wait for a few seconds for a normal display.

**Display Rotation**

If you're using a Pi4, you can rotate it by the following method:

* 1\. Open Screen Configuration.

<figure><img src="https://www.waveshare.com/w/upload/3/3b/8inch_1536x2048_LCD05.jpg" alt=""><figcaption></figcaption></figure>

* 2\. Set the rotation as shown below:

<figure><img src="https://www.waveshare.com/w/upload/3/31/8inch_1536x2048_LCD06.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/0/0e/8inch_1536x2048_LCD07.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/c/c3/8inch_1536x2048_LCD08.jpg" alt=""><figcaption></figcaption></figure>

* 3\. After rotating and touching, it can be used normally.

If you're using a Pi3+, or older, rotate it via:

* 1\. Add statements to the config.txt file (the config file is located in the root directory of the TF card, ie /boot):

```
display_rotate=1 #1：90；2: 180； 3: 270
```

* 2\. Save and restart the Raspberry Pi:

```
sudo reboot
```

**Rotate Touch**

After rotating the display, the touch position is wrong because the touch does not change with the display angle. So you need to modify the touch. By taking a card pin or tweezers, press the following positions to touch and rotate.\
(In order to avoid accidental touch, we hide the Rotate Touch button inside the case.)

<figure><img src="https://www.waveshare.com/w/upload/9/90/8inch_1536x2048_LCD70.png" alt=""><figcaption></figcaption></figure>

### Working With PC

#### Support Windows 11/10/8.1/8/7 System

**How to Use**

1\. Connect the Touch port of the LCD to the USB port of the PC, and Windows will automatically identify the touch function.\
2\. Connect the HDMI port of the LCD to the HDMI port of the PC, and Windows will automatically identify the display function.<br>

<figure><img src="https://www.waveshare.com/w/upload/2/27/8inch_1536x2048_LCD71.jpg" alt=""><figcaption></figcaption></figure>

* Note:
* Some PCs do not support the plug-and-play function of HDMI devices, and it can be normal after rebooting the system.
* If there is no sufficient power for the USB port, the LCD screen may flash. After connecting the 5V 1A power adapter to the Power port of the LCD, it can be normally used.

#### Windows Touch Calibration

Take Windows 10 as an example:

* 1\. Enter the Windows settings of the system, type in the search bar and click "Calibrate the screen for pen or touch input" (as shown in the picture below):

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* 2\. Click "Setup" in the pop-up "Tablet PC Settings" interface:

<figure><img src="https://www.waveshare.com/w/upload/9/99/Win10_touch02.png" alt=""><figcaption></figcaption></figure>

* 3\. The following text prompt will appear on the screen. Please tap the touch screen with your finger, and the computer will recognize it as a touch screen.

【Note】If the touch screen is blank, press the "Enter" key, and the text prompt will switch to the touch screen. (The screen which displays the text prompt will be used as a touch screen!)

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch03.png&#x26;width=800" alt=""><figcaption></figcaption></figure>

### Outline Dimensions

<figure><img src="https://www.waveshare.com/w/upload/5/52/8inch_1536x2048_LCD780.jpg" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/8inch_1536x2048_LCD) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
