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

# Waveshare 5inch IPS Round Touch DisplayHDMI

{% hint style="info" %}
[**View Waveshare 5 inch IPS Round Touch Display 1080x1080 HDMI on OpenELAB**](https://openelab.io/products/5inch-ips-round-touch-display)

**Store SKU / option:** `Waveshare-24369`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare 5inch IPS Round Touch DisplayHDMI

***

### Product Link

{% embed url="https://openelab.io/products/5inch-ips-round-touch-display" %}

### Feature

* 5-inch IPS round screen, 1080 x 1080 hardware resolution.
* 10-point capacitive touch, with toughened glass panel, hardness up to 6H.
* Adopting optical bonding technology, the display effect is better.
* Supports Raspberry Pi OS / Ubuntu / Kali and Retropie when used with Raspberry Pi.
* Supports Windows 11 / 10 / 8.1 / 8 / 7 when used as a computer monitor.
* Supports HDMI audio output with 3.5mm jack and 4PIN header.

<figure><img src="https://www.waveshare.com/w/upload/d/d8/5inch_1080x1080_LCD.png" alt=""><figcaption></figcaption></figure>

### Specification

| Item                 | Description                     | Unit   |
| -------------------- | ------------------------------- | ------ |
| Model                | 5inch 1080 x 1080 LCD           | /      |
| Dimensions           | 5.0                             | Inch   |
| Viewing Angle        | 160                             | Deg    |
| Resolution           | 1080 x 1080                     | Pixels |
| Overall Size         | 150.00(H) × 150.00(V) × 7.00(D) | mm     |
| Display Area         | 127.60(H) × 127.60(V)           | mm     |
| Pixel Pitch          | 0.1176(H) x 0.1176(V)           | mm     |
| Color Gamut          | 70%                             | NTSC   |
| Maximum Brightness   | 300                             | cd/m²  |
| Contrast             | 1300:1                          | /      |
| Backlight Adjustment | Button dimming                  | /      |
| Refresh Rate         | 60                              | Hz     |
| Display Interface    | Standard HDMI port              | /      |
| Power Port           | 5V Type-C power supply          | /      |
| Power Consumption    | 2                               | Watt   |

### Electrical Specifications

| Parameter             | Minimum | Standard | Maximum | Unit | Note   |
| --------------------- | ------- | -------- | ------- | ---- | ------ |
| Input Voltage         | 4.75    | 5.00     | 5.25    | V    | Note 1 |
| Input Current         | 300     | 400      | TBD     | mA   | Note 2 |
| Operating Temperature | 0       | 25       | 60      | ℃    | Note 3 |
| Storage Temperature   | -10     | 25       | 70      | ℃    | Note 3 |

•Note 1: Input voltage exceeding the maximum value or improper operation may cause permanent damage to the device.\
•Note 2: The input current must be ≥300mA, otherwise, it will cause booting failure or abnormal display, and it may cause permanent damage to the device if it is in an abnormal state for a long time.\
•Note 3: Please do not store the display in a high-temperature and high-humidity environment for a long time. The display must work within the limited value range, otherwise, it may be damaged.

### EDID Sequence Parameters

If the system of the main control board can automatically recognize the EDID for display, there is no need to additionally set related timing parameters.

Otherwise, you can refer to the following EDID settings:

| Pixel Clock | H Addressable | H Blanking | V Addressable | V Blanking | H Front Porch | H Sync Width | V Front Porch | V Sync Width | H Image Size | V Image Size | H Border | V Border |
| ----------- | ------------- | ---------- | ------------- | ---------- | ------------- | ------------ | ------------- | ------------ | ------------ | ------------ | -------- | -------- |
| 85.50       | 1080          | 200        | 1080          | 32         | 68            | 32           | 16            | 4            | 203          | 270          | 0        | 0        |

### Onboard Interface

<figure><img src="https://www.waveshare.com/w/upload/9/92/5inch_1080x1080_LCD02.jpg" alt=""><figcaption></figcaption></figure>

### User Guide

#### Working with Raspberry Pi

Hardware Connection

1. Connect the touch port of the LCD to the USB interface of the Raspberry Pi.
2. Connect the HDMI port of the LCD to the HDMI port of the Raspberry Pi.

<figure><img src="https://www.waveshare.com/w/upload/6/67/5inch_1080x1080_LCD03.jpg" alt=""><figcaption></figcaption></figure>

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
hdmi_pixel_freq_limit=356000000
hdmi_timings=1080 0 68 32 100 1080 0 12 4 16 0 0 0 60 0 85500000 0
```

6\. Insert the TF card into the Raspberry Pi, power on the Raspberry Pi, and wait for a few seconds for a normal display.

Due to the circular screen feature, it is recommended to use [the Raspberry Pi remote login tutorial](https://www.waveshare.com/wiki/Raspberry_Pi_Documentation#Login) for power on setup.

#### Working with PC

Support Windows 11/10/8.1/8/7

**How to Use**

1. Connect the touch port of the LCD to the USB port of the PC, and Windows will automatically identify the touch function.
2. Connect the HDMI port of the LCD to the HDMI port of the PC, and Windows will automatically identify the display function.

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

<figure><img src="https://www.waveshare.com/w/upload/3/3f/5inch_1080x1080_LCD09.jpg" alt=""><figcaption></figcaption></figure>

### Resource

#### 3D Drawing

* [5inch 1080x1080 LCD 3D Preview](https://files.waveshare.com/upload/9/9b/5inch_1080x1080_LCD_3D_preview.zip)
* [5inch 1080x1080 LCD 3D Drawing](https://files.waveshare.com/upload/c/c9/5inch_1080x1080_LCD_3D.zip)

## Official documentation and development resources

Use [Feature](https://www.waveshare.com/wiki/5inch_1080x1080_LCD) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
