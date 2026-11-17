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

# Waveshare 5.5inch 2K Touch LCD Display HDMI

### Waveshare 5.5inch 2K Touch LCD Display HDMI

***

### Product Link

{% embed url="https://openelab.io/products/2k-touch-lcd-display" %}

### Introduction

This product is a general-purpose 5.5-inch IPS display with an HDMI port and a resolution of 1440 × 2560, which is an optical bonding capacitive touch panel.\
Supports Raspberry Pi 4B and CM4, and can also be used as a computer monitor.

### Video

{% embed url="https://youtu.be/-TySrg3fG64" %}

### Feature

* 5.5-inch IPS display with a hardware resolution of 1440 × 2560
* 10-point capacitive touch control with toughened glass panel, hardness up to 6H
* Adopts the optical bonding touch technique for better use
* Supports Raspberry Pi OS / Ubuntu / Kali and Retropie when working with Raspberry Pi 4B
* Supports Windows 11/10/8.1/8/7 when working as a computer monitor
* Supports HDMI audio output with 3.5mm jack and 4PIN header

### Onboard Resources

<figure><img src="https://www.waveshare.com/w/upload/9/91/5.5inch_1440x2560_LCD_Spe1.png" alt=""><figcaption></figcaption></figure>

### Working With Raspberry Pi 4B

For Raspberry Pi OS / Ubuntu / Kali and Retropie systems.\
When the LCD works on systems such as Raspberry Pi, the resolution must be manually set, otherwise, it will cause an abnormal display.\
1\. Please download the latest version of the image from the [Raspberry Pi official website](https://www.raspberrypi.com/software/operating-systems/). Download the compressed file to your PC, and unzip the ".img" file.\
2\. Connect the TF card to the PC and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.\
3\. Open the [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip) software, select the system image prepared in step 1, and click "write" to program the system image.\
4\. After the programming is completed, open the config.txt file in the root directory of the TF card, add the following code at the end of config.txt, save and safely eject the TF card, and insert the TF card into the Raspberry Pi.

```
hvs_priority=0x32ff
gpu_mem=256
config_hdmi_boost=10
hdmi_force_hotplug=1
hdmi_group=2
hdmi_mode=87
hdmi_drive=2
hdmi_pixel_freq_limit=268500000
#pi4:
hdmi_timings=1440 0 10 10 140 2560 0 11 2 2 0 0 0 50 0 206000000 3
#3B/ZERO needs to change to the following line of timings configuration and block dtoverlay=vc4-kms-v3d or dtoverlay=vc4-fkms-v3d
#hdmi_timings=1440 0 10 10 140 2560 0 11 2 2 0 0 0 50 0 180000000 3
disable_overscan=1
framebuffer_width=1440
framebuffer_height=2560
max_framebuffer_width=1440
max_framebuffer_height=2560
extra_transpose_buffer=2
```

5\. Connect the Touch port of the display to the USB port of the Raspberry Pi.\
6\. Connect the HDMI port of the display screen to the HDMI port of the Raspberry Pi, power on the Raspberry Pi, and wait for a few seconds to display normally.\
The screen is displayed vertically by default. For convenience, you can adjust the display orientation of the screen, see [#Display Rotation](https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#Display_Rotation).

#### Display Rotation

Note: Only the Raspberry Pi 4th generation controller supports display rotation. Limited by hardware, Raspberry Pi 3rd generation or zero only supports the default vertical screen display, and cannot support rotation.

**Update Software Version**

Raspberry Pi OS Bullseye branch needs to update the software version, other systems can skip this step.

```
sudo apt-get update
sudo apt-get full-upgrade
```

**Raspberry Pi OS & Kail Display Rotation**

First, check whether the KMS or FKMS driver is loaded on the system you are using.\
How to check: In /boot/config.txt, check whether the corresponding board has turned on "dtoverlay=vc4-kms-v3d" or "dtoverlay=vc4-fkms-v3d".

Load KMS Or FKMS Driver\
Use the following command for display rotation:

```
sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
#Enter the command corresponding to the display rotation angle at the end of the autostart file, and it will take effect after restarting
#0: rotate 0 degrees; 1: rotate 270 degrees; 2: rotate 180 degrees; 3: rotate 90 degrees
xrandr -o 1
```

No KMS Or FKMS Driver Loaded\
Use the following command for display rotation:

```
sudo nano /boot/config.txt
#Enter the command corresponding to the display rotation angle at the end of the config.txt file, and it will take effect after restarting
#0: rotate 0 degrees; 1: rotate 90 degrees; 2: rotate 180 degrees; 3: rotate 270 degrees
display_rotate=3
```

### Touch To Rotate

After the display rotation is performed, the touch position is not correct because the touch does not change with the display angle. Hence, we need to modify the touch.

* Hardware Touch Rotate: Short press the Touch Rotate button on the bottom panel, and each short press will rotate the touch direction by 90 degrees.

<figure><img src="https://www.waveshare.com/w/upload/5/55/5.5inch_1440x2560_LCD_Spec05.png" alt=""><figcaption></figcaption></figure>

* If there are special circumstances that cannot be rotated by hardware, please refer to the following software to rotate the touch:

1\. Install libinput.

```
sudo apt-get install xserver-xorg-input-libinput
```

If you installed the Ubuntu system or Jetson Nano. The installation instructions are:

```
sudo apt install xserver-xorg-input-synaptics
```

2\. Create the Xorg.conf.d directory under /etc/X11/ (if the directory already exists, this goes directly to step 3).

```
sudo mkdir /etc/X11/xorg.conf.d
```

3\. Copy the 40-libinput-conf file to the directory just created.

```
sudo cp /usr/share/X11/xorg.conf.d/40-libinput.conf /etc/X11/xorg.conf.d/
```

4\. Edit the file.

```
sudo nano /etc/X11/xorg.conf.d/40-libinput.conf 
```

Find the touchscreen part, add the following statement to it, and save it.

```
Option "CalibrationMatrix" "0 1 0 -1 0 1 0 0 1"
```

Similar to the picture below:

<figure><img src="https://www.waveshare.com/w/upload/b/b1/Touch_roate.jpg" alt=""><figcaption></figcaption></figure>

5\. Reboot the Raspberry Pi.

```
sudo reboot
```

Complete the above steps to perform a 90-degree rotation.\
Note:\
90-degree rotation: Option "CalibrationMatrix" "0 1 0 -1 0 1 0 0 1"

180-degree rotation: Option "CalibrationMatrix" "-1 0 1 0 -1 1 0 0 1"

270-degree rotation: Option "CalibrationMatrix" "0 -1 1 1 0 0 0 0 1"

### Interface Optimization

Due to the high resolution of the screen, it is recommended to modify the theme to a larger size for enjoying a better touching experience. This feature is not supported on all systems. The following mainly uses the Raspbian system to describe the relevant operations, and other systems are similar.

* Select Menu -> Preferences -> Appearance Settings -> Defaults -> For large screens: Set Defaults -> OK.

<figure><img src="https://www.waveshare.com/w/upload/3/39/5.5inch_1440x2560_LCD_Spec07.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/6/6f/5.5inch_1440x2560_LCD_Spec08.jpg" alt=""><figcaption></figcaption></figure>

* Set the font size of the System.

<figure><img src="https://www.waveshare.com/w/upload/9/9b/5.5inch_1440x2560_LCD_Spec09.jpg" alt=""><figcaption></figcaption></figure>

* Right-click on the taskbar -> "Panel Preferences" -> "Geometry" -> "Size".

<figure><img src="https://www.waveshare.com/w/upload/b/b2/5.5inch_1440x2560_LCD_Spec10.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/2/26/5.5inch_1440x2560_LCD_Spec11.jpg" alt=""><figcaption></figcaption></figure>

### Set The Screen Always On

Some users want to display without being affected by the screen saver function, and can be set it as follows. Turn off the screen saver function.\
Open lightdm.conf.

```
sudo nano /etc/lightdm/lightdm.conf
```

Modify lightdm.conf to find "xserver-command" under the \[SeatDefaults] section, uncomment it, and modify it as follows:

```
#xserver-command=X
```

change into

```
xserver-command=X -s 0 -dpms
```

* -s # – set screen saver not enabled.
* dpms - turn off power saving management.

Reboot

```
sudo reboot
```

### Working With PC

Support Windows 11/10/8.1/8/7 system. How to use:\
1\) Connect the Touch interface of the display screen to the USB interface of the PC. After a while, Windows will automatically recognize the touch function.\
2\) Connect the HDMI interface of the display to the HDMI interface of the PC, and wait for about 10 seconds to see that the display is displayed normally. If you need to output sound, you can connect 3.5mm headphones through the HP audio output interface.\
Note 1: When the computer is connected to multiple monitors at the same time, the touch effect works on the main screen by default. If you need to specify the touch to the secondary screen, see [#Calibration touch on Windows](https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#Calibration_touch_on_Windows).\
Note 2: The USB interface of some PCs may cause insufficient power supply due to aging. In this case, you can use the USB interface on the back of the PC host, or connect an external 5V 2A power adapter to the "power" interface.\
Note 3: This product defaults to vertical display, and the resolution (H×V) is 1440 × 2560. You can enter the display settings of the windows system and rotate it to landscape display.

#### Calibration touch on Windows

Take the windows10 system as an example:

* 1\. Enter the Windows settings of the system, type in the search bar and click "Calibrate the screen for pen or touch input" (as shown in the picture below).

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch02.png&#x26;width=300" alt=""><figcaption></figcaption></figure>

* 2\. Click "Setup" in the pop-up "Tablet PC Settings" interface:
* 3\. The following text prompt will appear on the screen. Please tap the touch screen with your finger, and the computer will recognize it as a touch screen.

【Note】If the touch screen is blank, press the "Enter" key, and the text prompt will switch to the touch screen. (The screen which displays the text prompt will be used as a touch screen!)&#x20;

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch03.png&#x26;width=800" alt=""><figcaption></figcaption></figure>

### Working With Tinker Board 2

#### Hardware Connection

1. Connect the Touch interface of the LCD to the USB connector of Tinker Board 2.
2. Connect the HDMI port of the LCD to the HDMI port of Tinker Board 2.

#### Software Setting

Android and Debian systems for Tinker Board 2.

1. Please download the newest image from [Tinker Board official website](https://tinker-board.asus.com/download-list.html?product=tinker-board-2s). Download the compressed file to the PC and then unzip it to get the "img" file.
2. Connect the TF card to the PC and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.
3. Open the [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip) software and select the system image prepared in the first step, and click "write" to program the system image.
4. After programming, you can insert the TF card into Tinker Board 2 and power on it,

### Resource

#### Related Software

* [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip)
* [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip)
* [Putty](https://files.waveshare.com/upload/5/56/Putty.zip)

#### 3D Drawing

* [5.5inch 1440x2560 LCD 3D Drawing](https://files.waveshare.com/upload/7/7a/5.5inch_1440x2560_LCD.zip)

#### 2D Drawing

* [5.5inch 1440x2560 LCD 2D Drawing](https://files.waveshare.com/upload/9/9e/5.5inch_1440x2560_LCD_2D.zip)

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion1"><strong>How do remove the colored squares of the GPU self-check when the Raspberry Pi is powered on?</strong></a></summary>

Add the following command to /boot/config.txt:

```
disable_splash=1
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion2"><strong>How to replace the Raspberry Pi startup logo image?</strong></a></summary>

Replace the custom image with the image in this directory /usr/share/plymouth/themes/pix/splash.png.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion3"><strong>How to set long press touch on Raspberry Pi capacitive touch screen?</strong></a></summary>

Test environment: 2022-04-04-raspios-bullseye-armhf 32-bit system\
Supported models: Support Waveshare DSI LCD, DPI LCD and HDMI LCD capacitive touch screen series.

#### Software Installation

```
wget https://files.waveshare.com/upload/1/18/Evdev-right-click-emulation.zip
unzip Evdev-right-click-emulation.zip
cd evdev-right-click-emulation
sudo apt install build-essential libevdev2 libevdev-dev
cd 'evdev-right-click-emulation'
sudo cp 'out/evdev-rce' '/usr/local/bin/'
sudo chmod +x '/usr/local/bin/evdev-rce'
```

Enter the command:

```
sudo evdev-rce
```

After running, you can touch and long press to realize the right-click function.

**Set IP**

```
sudo usermod -G 'input' -a pi
echo 'uinput' | sudo tee -a /etc/modules
sudo nano  /etc/udev/rules.d/99-uinput.rules
```

Add in 99-uinput.rules file.

```
KERNEL=="uinput", MODE="0660", GROUP="input"
```

save it and run it in the terminal.

```
sudo udevadm control --reload-rules
sudo udevadm trigger
```

Then reboot:

```
sudo reboot
```

Run after reboot (no sudo needed at this point)

```
evdev-rce
```

After running, you can touch and long press to realize the right-click function.

**Set Startup**

Enter the terminal

```
sudo mkdir ~/.config/autostart
sudo nano ~/.config/autostart/right_click.desktop
```

Add the following in right\_click.desktop.

```
[Desktop Entry]
Version=1.0
Type=Application
Name=evdev-rce
GenericName=Enable long-press-to-right-click gesture
Exec=env LONG_CLICK_INTERVAL=1000 LONG_CLICK_FUZZ=200  /usr/local/bin/evdev-rce
Terminal=true
StartupNotify=false

#If you want to change the sensitivity, you can modify the size of two parameters, that is, "LONG_CLICK_INTERVAL=1000 LONG_CLICK_FUZZ=200".
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion4"><strong>I use a 5.5-inch 1440x2560 LCD to connect to the PC, but it cannot display normally. How to solve it?</strong></a></summary>

* Make sure that the HDMI port of the PC can output normally.
* The PC only connects the LCD as a display device and does not connect other monitors.
* Connect the power cable first and then the HDMI cable.
* Some PCs also need to be restarted to display properly.

Note: Windows system must be used.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion5"><strong>What is the refresh rate of this screen?</strong></a></summary>

60Hz.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion6"><strong>Does the screen not automatically rest, or do I have to execute a command to rest the screen?</strong></a></summary>

It depends on the system, if the system has hibernation, the screen will also be black. If it is the official system of Raspberry Pi, the default is about ten minutes without action to have hibernation.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion7"><strong>How to implement PWM dimming?</strong></a></summary>

Modify the hardware as shown in the figure below, and then connect the PWM signal to the pad pointed by the yellow arrow

<img src="https://www.waveshare.com/w/upload/e/ea/5.5inch_1440x2560_LCD_PWM.png" alt="" data-size="original">

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion8"><strong>Using 5.5inch 1440x2560 LCD to connect to PC, how to specify touch screen?</strong></a></summary>

Take windows10 system as an example:

1\. Open Windows Settings, enter "calibration" in the search bar, and select "Calibrate screen for pen and touch input"\
[![Win10 touch011.png](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png\&width=700)](https://www.waveshare.com/wiki/File:Win10_touch011.png)\
Click "Setting" in the "Display"\
[![Win10 touch02.png](https://www.waveshare.com/w/upload/9/99/Win10_touch02.png)](https://www.waveshare.com/wiki/File:Win10_touch02.png)\
3\. The following text prompt will appear on the screen. Please tap the touch screen with your finger, and the computer will recognize it as a touch screen.\
[![Win10 touch03.png](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch03.png\&width=800)](https://www.waveshare.com/wiki/File:Win10_touch03.png)<br>



</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion9"><strong>H</strong></a><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion9"><strong>ow can I rotate the touch?</strong></a></summary>

Briefly press the "Touch Rotate" button on the back of the display. (each press touch will rotate 90°)

<img src="https://www.waveshare.com/w/upload/a/af/800px-5.5-new5.png" alt="" data-size="original">

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion10"><strong>What is the working current of the 5.5inch 1440x2560 LCD module?</strong></a></summary>

5V 440mA

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion11"><strong>What is the brightness of the 5.5inch 1440x2560 LCD module?</strong></a></summary>

260cd/m²

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5.5inch_1440x2560_LCD#accordion12"><strong>What is the color gamut of the 5.5inch 1440x2560 LCD module?</strong></a></summary>

70%NTSC

</details>
