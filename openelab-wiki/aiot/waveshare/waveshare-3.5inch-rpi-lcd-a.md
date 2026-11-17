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

# Waveshare 3.5inch RPi LCD (A)

### Waveshare 3.5inch RPi LCD (A)

***

### Product Link

{% embed url="https://openelab.io/products/3-5inch-rpi-lcd" %}

### Introduction

3.5 inch Touch Screen TFT LCD is designed for Raspberry Pi.

### Features

* 480 × 320 hardware resolution.
* Resistive touch control.
* It is compatible and can be directly inserted into any version of Raspberry Pi.
* Provides drivers (works with your own Raspbian/Ubuntu/Kali and Retropie system directly).
* Support FBCP software driver, which can set the software resolution and dual-screen display.
* Its size is the same as your Raspberry Pi.
* Immersion gold design, fine carving.

### Getting Started

#### Hardware Connection

* There are 40 pins on Raspberry Pi, but there are 26 pins on the LCD, so you should pay attention to connecting the pins to your Pi accordingly.

#### Install the Touch Driver

The RPi LCD can be driven in two ways: Method 1. Install a driver to your Raspbian OS. Method 2. Use the Ready-to-use image file of which the LCD driver was pre-installed.

Method 1. Driver installation

Please download the bullseye 32bit version of the image on the [Raspberry Pi official website.](https://www.raspberrypi.org/downloads/) (Raspbian/Ubuntu Mate/Kali or Retropie).

1\) Download the compressed image file to the PC, and unzip it to get the .img file.

2\) Connect the TF card to the PC, open the [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip) software, select the system image downloaded in step 1, and click 'Write' to write the system image. (How to write an image to a micro SD card for your Pi? See [RPi Image Installation Guides](https://www.waveshare.com/wiki/RPi-Image-Installation-Guides) for more details).

3\) Connect the TF card to the Raspberry Pi, and start the Raspberry Pi. The LCD will display after booting up, and then log in to the Raspberry Pi terminal, (You may need to connect a keyboard and HDMI LCD to Pi for driver installation, or log in remotely with SSH).

4\) Then open the terminal of Raspberry Pi to install the touch driver.

```
git clone https://github.com/waveshare/LCD-show.git
cd LCD-show/
```

Note: The Raspberry Pi must be connected to the network, or else the touch driver won't be successfully installed.

```
chmod +x LCD35-show
 ./LCD35-show
```

The touch function will work after restarting. For ease of use, you can set the screen orientation, see: [#Screen orientation settings](https://www.waveshare.com/wiki/3.5inch_RPi_LCD_\(A\)#Screen_orientation_settings).

Notes:

* 1\. Executing apt-get upgrade will cause the LCD to fail to work properly. In this case, you need to edit the config.txt file in the SD card and delete this sentence: dtoverlay=ads7846.
* 2\. Using Raspbian-lite, the command of the touch driver installation should be:

```
 ./LCD35-show lite
```

For bullseye 64bit and Bookworm systems, manual configuration is required as follows: [3.5inch RPi LCD (A) Manual Configuration](https://www.waveshare.com/wiki/3.5inch_RPi_LCD_\(A\)_Manual_Configuration).

Method 2. Using Ready-to-use image

The image file with the pre-installed driver is located in the IMAGE directory of the CD, or you can download it from [#Image](https://www.waveshare.com/wiki/3.5inch_RPi_LCD_\(A\)#Image). Extract the .7z file and you will get a .img file. Write the image to your micro SD card (How to write an image to a micro SD card for your Pi? See [RPi Image Installation Guides](https://www.waveshare.com/wiki/RPi-Image-Installation-Guides) for more details). Then insert the card into your Pi, power up, and enjoy it.

### Screen Orientation Settings

After installing the touch driver, you can modify the screen rotation direction by running the following commands.

```
cd LCD-show/
#X can be 0, 90, 180, and 270. Indicates that the LCD rotates 0 degrees, 90 degrees, 180 degrees, and 270 degrees, respectively.
sudo ./LCD35-show X
```

The rotation command under Raspbian-lite is as follows:

```
cd LCD-show/
#X can be 0, 90, 180, and 270. Indicates that the LCD rotates 0 degrees, 90 degrees, 180 degrees, and 270 degrees, respectively.
sudo ./LCD35-show lite X
```

### Touch Screen Calibration

This LCD can be calibrated through the xinput-calibrator demo. Note: The Raspberry Pi must be connected to the network, or else the demo won't be successfully installed.

* Run the following command to install:

```
sudo apt-get install xinput-calibrator 
```

* Click the "Menu" button on the taskbar, and choose "Preference" -> "Calibrate Touchscreen".
* Finish the touch calibration following the prompts. Maybe rebooting is required to make calibration active.
* You can create a 99-calibration.conf file to save the touch parameters (not necessary if the file exists).

```
sudo nano /etc/X11/xorg.conf.d/99-calibration.conf
```

* Save the touch parameters (may differ depending on LCD) to 99-calibration.conf, as shown in the picture:

<figure><img src="https://www.waveshare.com/w/upload/f/f8/5inch_HDMI_LCD_FAQ1.jpg" alt=""><figcaption></figcaption></figure>

### Install Virtual Keyboard

1\. Install matchbox-keyboard.

```
sudo apt-get install update
sudo apt-get install matchbox-keyboard
sudo nano /usr/bin/toggle-matchbox-keyboard.sh
```

2\. Copy the statements below to toggle-matchbox-keyboard.sh and save.

```
#!/bin/bash
#This script toggle the virtual keyboard
PID=`pidof matchbox-keyboard`
if [ ! -e $PID ]; then
killall matchbox-keyboard
else
matchbox-keyboard -s 50 extended&
fi
```

3\. Execute the commands:

```
sudo chmod +x /usr/bin/toggle-matchbox-keyboard.sh
sudo mkdir /usr/local/share/applications
sudo nano /usr/local/share/applications/toggle-matchbox-keyboard.desktop
```

4\. Copy the statements to toggle-matchbox-keyboard.desktop and save.

```
[Desktop Entry]
Name=Toggle Matchbox Keyboard
Comment=Toggle Matchbox Keyboard`
Exec=toggle-matchbox-keyboard.sh
Type=Application
Icon=matchbox-keyboard.png
Categories=Panel;Utility;MB
X-MB-INPUT-MECHANSIM=True
```

5\. Execute commands as below. Note that you need to use "Pi " user permission instead of root to execute this command.

```
sudo nano /etc/xdg/lxpanel/LXDE-pi/panels/panel
```

6\. Find the statement which is similar to below: (It may be different in a different version.)

```
Plugin {
    type = launchbar
    Config {
        Button {
            id=lxde-screenlock.desktop
        }
        Button {
            id=lxde-logout.desktop
        }
    }
}
```

7\. Append these statements to add a button option:

```
Button {
    id=/usr/local/share/applications/toggle-matchbox-keyboard.desktop
}
```

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=RPILCD-INSTALL-KEYBOARD01.png&#x26;width=400" alt=""><figcaption></figcaption></figure>

8\. Reboot your Raspberry Pi. If the virtual keyboard is installed correctly, you can find that there is a keyboard icon on the left of the bar.

```
sudo reboot
```

### Interface Definition

The pins marked as "NC" below indicate that the pins are not occupied by the LCD and can be used by the user for other applications.

<table><thead><tr><th width="170">Pin Number</th><th width="167">Identification</th><th>Description</th></tr></thead><tbody><tr><td>1</td><td>3.3V</td><td>Power (3.3V input)</td></tr><tr><td>2</td><td>5V</td><td>Power (5V input)</td></tr><tr><td>3</td><td>NC</td><td>NC</td></tr><tr><td>4</td><td>5V</td><td>Power (5V input)</td></tr><tr><td>5</td><td>NC</td><td>NC</td></tr><tr><td>6</td><td>GND</td><td>Ground</td></tr><tr><td>7</td><td>NC</td><td>NC</td></tr><tr><td>8</td><td>NC</td><td>NC</td></tr><tr><td>9</td><td>GND</td><td>Ground</td></tr><tr><td>10</td><td>NC</td><td>NC</td></tr><tr><td>11</td><td>TP_IRQ</td><td>The touch panel is interrupted, and it is low when it is detected that the touch panel is pressed</td></tr><tr><td>12</td><td>NC</td><td>NC</td></tr><tr><td>13</td><td>NC</td><td>NC</td></tr><tr><td>14</td><td>GND</td><td>Ground</td></tr><tr><td>15</td><td>NC</td><td>NC</td></tr><tr><td>16</td><td>NC</td><td>NC</td></tr><tr><td>17</td><td>3.3V</td><td>Power (3.3V input)</td></tr><tr><td>18</td><td>LCD_RS</td><td>Command/Data Register Select</td></tr><tr><td>19</td><td>LCD_SI / TP_SI</td><td>LCD display / SPI data input of touch panel</td></tr><tr><td>20</td><td>GND</td><td>Ground</td></tr><tr><td>21</td><td>TP_SO</td><td>SPI data output of touch panel</td></tr><tr><td>22</td><td>RST</td><td>Reset</td></tr><tr><td>23</td><td>LCD_SCK / TP_SCK</td><td>SPI clock signal for LCD display/touch panel</td></tr><tr><td>24</td><td>LCD_CS</td><td>LCD chip select signal, low level selects LCD</td></tr><tr><td>25</td><td>GND</td><td>Ground</td></tr><tr><td>26</td><td>TP_CS</td><td>Touch panel chip select signal, low level selects touch panel</td></tr></tbody></table>

### Resource

#### User Manual

* [RPi LCD User Manual](https://files.waveshare.com/upload/1/1e/RPi_LCD_User_Manual_EN.pdf)

#### Preinstall-image

Description: if you felt hard to install the driver, try the image with the driver pre-installed.

* [3.5inch RPi LCD (A)\_20220404\_32bit\_bullusye](https://drive.google.com/file/d/1imrfzcxzSjnNLcWMAivFNQF_kZm0zPJT/view?usp=sharing)
* [RPi LCD Bookworm\_32bit only for pi5\&pi4](https://drive.google.com/file/d/17dls9ELa56DOLbXwMvXkaDLHeyv0wMp7/view?usp=sharing)
* [RPi LCD Bookworm\_32bit Applicable to non-pi5 versions](https://drive.google.com/file/d/1MGnNenLvqMCeE6485gqrqQjKLc6sBqRr/view?usp=sharing)
* [RPi LCD Bookworm\_64bit For all versions](https://drive.google.com/file/d/1lRd8lm0jmgZTvVwz2DSRgBI26hah56VX/view?usp=sharing)

#### Driver

The driver can be downloaded from github

```
git clone 
```

#### Software

* [Panasonic SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip)
* [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip)
* [PuTTY](https://files.waveshare.com/upload/5/56/Putty.zip)

#### LCD Panel Dimension

* [3.5inch RPi LCD (A) panel dimension](https://files.waveshare.com/upload/0/0c/3.5inch-rpi-lcd-a-panel-dimension.pdf)

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/3.5inch_RPi_LCD_(A)#accordion1"><strong>Why can not the LCD be used normally when using the official image provided by the Raspberry Pi?</strong></a></summary>

The LCD must have a driver installed for normal use. For details, please refer to the relevant introduction in the user manual.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/3.5inch_RPi_LCD_(A)#accordion2"><strong>Why can not the LCD be used normally when using the Raspberry Pi image provided by Waveshare?</strong></a></summary>

Since the Raspberry Pi image and version are frequently updated, if you encounter a situation where the LCD cannot be used normally, please download the latest version of the image provided by us or from the official website of Raspberry Pi and install the latest driver provided by us.

* Make sure the hardware connection is correct and the contact is good.
* Make sure that TF card programming is normal.
* When the Raspberry Pi starts normally, the PWR light is always on, and the ACT light is flashing. If it is found that both lights are always on, it may be that the TF card is not successfully programmed to the image or the TF card is in poor contact with the Raspberry Pi.
* It is recommended to use a 5V 2.5A power adapter for the Raspberry Pi. If the Raspberry Pi is powered by the USB port of the PC, the Raspberry Pi may not be able to start normally due to an insufficient power supply.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/3.5inch_RPi_LCD_(A)#accordion3"><strong>What is the operating temperature of the 3.5inch RPi LCD (C)?</strong></a></summary>

Commercial grade (0\~70 degrees Celsius).

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/3.5inch_RPi_LCD_(A)#accordion4"><strong>What are the power requirements?</strong></a></summary>

When working with 5V input, the current is about 200mA.

</details>
