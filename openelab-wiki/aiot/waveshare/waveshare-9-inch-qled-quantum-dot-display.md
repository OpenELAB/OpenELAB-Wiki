# Waveshare 9 inch QLED Quantum Dot Display

{% hint style="info" %}
[**View Waveshare 9 inch QLED Quantum Dot Display,1280×720 HDMI on OpenELAB**](https://openelab.io/products/9-inch-qled-quantum-dot-display)

**Store SKU / option:** `Waveshare-24864`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare 9 inch QLED Quantum Dot Display

***

{% embed url="https://openelab.io/products/9-inch-qled-quantum-dot-display" %}

### Introduction

9HP-CAPQLED-B is a universal 9" HDMI QLED quantum dot display with 1280 x 720 resolution. With a capacitive touch panel, it supports Raspberry Pi and can also be used as a computer monitor.

### Features

* 9-inch QLED quantum dot display with the advantages of high color gamut, pure chromaticity, long color life, and so on.
* The hardware resolution is 1280×720, which can be adjusted via the software.
* 10-point touch control, toughened glass panel with up to 6H hardness.
* When working with Raspberry Pi, supports Raspberry Pi OS, Ubuntu, Kali, and Retropie systems.
* When working with Core3566, it supports Linux.
* When working with Jetson Nano, it supports Ubuntu.
* When working with Windows PC, support Windows 11/10/8.1/8/7.
* Support mainstream game consoles such as Microsoft Xbox 360, Sony PS4, Nintendo SWITCH, etc.
* Multi-languages OSD menu, for power management, brightness/contrast adjustment, etc.
* Support HDMI audio output with a 3.5mm headphone jack and 4PIN speaker.

<figure><img src="https://www.waveshare.com/w/upload/4/40/9HP-CAPQLED-B01.png" alt=""><figcaption></figcaption></figure>

### Specification

| Item                    | Description                 | Unit   |
| ----------------------- | --------------------------- | ------ |
| Model                   | 9HP-CAPQLED-B               |        |
| Size                    | 9.0                         | Inch   |
| Viewing Angle           | 178                         | Deg    |
| Resolution              | 1280×720                    | Pixels |
| Touch Screen Size       | 222.51(H)×139.95(V)×7.00(D) | mm     |
| Display Area            | 196.61(H)×114.05(V)         | mm     |
| IPS Color Gamut         | 92%NTSC                     |        |
| Brightness              | 450                         | cd/m²  |
| Brightness Adjustment   | DDC/CI Software Dimming     |        |
| Contrast                | 1000:1                      |        |
| Color Depth             | 16.7M                       |        |
| Refresh Rate            | 60                          | Hz     |
| Communication Interface | HDMI Port                   |        |

### Electrical Parameters

| Parameter             | Min. Value | Standard Value | Max. Value | Unit | Note   |
| --------------------- | ---------- | -------------- | ---------- | ---- | ------ |
| Input Voltage         | 4.75       | 5.00           | 5.25       | V    | Note 1 |
| Input Current         | 1200       | 1500           | TBD        | mA   | Note 2 |
| Operating Temperature | 0          | 25             | 60         | ℃    | Note 3 |
| Storage Temperature   | -10        | 25             | 70         | ℃    | Note 3 |

•Note 1: Input voltage exceeding the maximum value or improper operation may cause permanent damage to the device.\
•Note 2: The input current should be ≥1200mA, otherwise it will lead to start-up failure or abnormal display, and a long time in an abnormal state may cause permanent damage to the device.\
•Note 3: Please do not put the display in a high temperature and high humidity storage environment for a long time, the display needs to work within the limit value, otherwise it will be possible to damage the display.

### EDID Sequence Parameters

If the system of the main control board can automatically identify the EDID for display, there is no need to set the relevant timing parameters additionally.\
Otherwise, you can refer to the following EDID settings:

| Pixel Clock | H Addressable | H Blanking | V Addressable | V Blanking | H Front Porch | H Sync Width | V Front Porch | V Sync Width | H Image Size | V Image Size | H Border | V Border |
| ----------- | ------------- | ---------- | ------------- | ---------- | ------------- | ------------ | ------------- | ------------ | ------------ | ------------ | -------- | -------- |
| 70.40       | 1280          | 232        | 720           | 56         | 160           | 32           | 20            | 6            | 294          | 165          | 0        | 0        |

### Onboard Interface

<figure><img src="https://www.waveshare.com/w/upload/c/c0/9HP-CAPQLED_inter.jpg" alt=""><figcaption></figcaption></figure>

### User Guide

#### Working with Raspberry Pi

1. Connect the 5V 3A power adapter to the Power port.
2. Connect the Touch port to the USB port of the Raspberry Pi.
3. Connect the HDMI port to the HDMI port of the Raspberry Pi.

[![9HP-CAPQLED-B023.jpg](https://www.waveshare.com/w/upload/e/ec/9HP-CAPQLED-B023.jpg)](https://www.waveshare.com/wiki/File:9HP-CAPQLED-B023.jpg)

#### Software Setting

```
Raspberry Pi OS / Ubuntu / Kali and Retropie systems are supported for Raspberry Pi.
When the LCD works on these systems of Raspberry Pi, the resolution must be set manually, otherwise, it will result in incorrect display resolution and affect the experience.
```

1\. Please download the newest image from the [Official Raspberry Pi website](https://www.raspberrypi.com/software/operating-systems/).\
2\. Download the compressed file on the PC and unzip it to get the .img file.\
3\. Connect the TF card to the PC and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.\
4\. Open [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip), choose the image prepared in the first step, and click "Write" to program the system image.\
5\. After programming, open the config.txt file in the root directory of the TF card and enter the following codes at the end of config.txt. Then, save and safely eject the TF card.

```
hdmi_group=2 
hdmi_mode=87 
hdmi_timings=1280 0 160 32 40 720 0 20 6 30 0 0 0 60 0 70400000 3
```

6\. Insert the TF card into the Raspberry Pi, power up the Raspberry Pi, wait for a few seconds normally and then it will display normally.

#### Linux Software Brightness Adjustment

Using the DDC/CI program, here is an example of the [ddcutil tool](http://www.ddcutil.com/).

```
#Install ddcutil tool:
sudo apt-get install ddcutil -y
#Support DDC/CI monitors for detection
sudo ddcutil detect
#Adjust the monitor brightness, <value> should be modified to 0-100 value
sudo ddcutil setvcp 10 <value>
```

For more information about ddcutil function commands, please see: [http://www.ddcutil.com/commands/](http://www.ddcutil.com/commands/)

### Working with PC

#### Support Windows 11/10/8.1/8/7

How to Use

1. Connect the 5V 3A power adapter to the Power interface.
2. Connect the Touch interface to the USB interface of the PC, and Windows will automatically recognize the touch function.
3. Connect the HDMI interface to the HDMI interface of the PC, and Windows will automatically recognize the display function.

* Note:
* Some PCs do not support HDMI devices plug-and-play, usually after rebooting the system can be used normally.

#### Windows Touch Calibration

Take Windows 10 as an example:

* 1\. Enter the Windows setting of the system, type in the search bar, and click "Calibrate the screen for pen or touch input" (as shown in the picture below):

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

### Dimensions

<figure><img src="https://www.waveshare.com/w/upload/a/ad/9HP-CAPQLED-B09.png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/9HP-CAPQLED-B) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
