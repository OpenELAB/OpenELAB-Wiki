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

# Waveshare 5inch HDMI Touch Screen LCD with Bicolor Case

{% hint style="info" %}
[**View Waveshare 5 inch HDMI Resistive Touch Screen LCD with Bicolor Case on OpenELAB**](https://openelab.io/products/5inch-touch-screen-lcd)

**Store SKU / option:** `Waveshare-10898`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare 5inch HDMI Touch Screen LCD with Bicolor Case

***

### Product Link

{% embed url="https://openelab.io/products/5inch-touch-screen-lcd" %}

### Introduction

5-inch Resistive Touch Screen LCD, with a resolution of 800 × 480, supports Raspberry Pi and can also be used as a computer monitor.

### Features

* 800 x 480 hardware resolution.
* Resistive touch control.
* Using Raspberry Pi, it supports Raspberry Pi OS / Ubuntu / Kali and Retropie system.
* Using as a computer monitor, it supports Windows 11/ 10 / 8.1 / 8 / 7.
* Support backlight control, more power saving.

### Video

{% embed url="https://youtu.be/rZtAvrfVTD0" %}

### Working with PC

This LCD can support Windows 7 /8 /8.1 /10 /11 system.

1\) Turn on the backlight switch on the back of the LCD.

2\) Connect the Touch interface of the LCD to the USB interface of the PC. Wait for a while, the windows will automatically recognize the touch function.

3\) Connect the HDMI interface of the LCD to the HDMI interface of the PC.

Normally you can see an interface similar to the following figure. (Some PCs may need to be restarted to display.)

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=5inch-HDMI-LCD-B-Rev2.1-00.jpg&#x26;width=400" alt=""><figcaption></figcaption></figure>

### Calibration touch on Win 10 PC

Take the windows10 system as an example:

* 1\. Enter the Windows settings of the system, type in the search bar, and click "Calibrate the screen for pen or touch input" (as shown in the picture below).

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch02.png&#x26;width=300" alt=""><figcaption></figcaption></figure>

* 2\. Click "Setup" in the pop-up "Tablet PC Settings" interface:
* 3\. The following text prompt will appear on the screen. Please tap the touch screen with your finger, and the computer will recognize it as a touch screen.

【Note】If the touch screen is blank, press the "Enter" key, and the text prompt will switch to the touch screen. (The screen which displays the text prompt will be used as a touch screen!)

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch03.png&#x26;width=800" alt=""><figcaption></figcaption></figure>

### Working with Raspberry Pi

This LCD can support Raspberry Pi OS / Ubuntu / Kali / Retropie systems. When the LCD works on systems such as Raspberry Pi, the resolution must be set manually, otherwise, it will cause an abnormal display. There is no such problem when the LCD works on the PC version of Windows.

Please download the latest version of the image from the [Raspberry Pi official website](https://www.raspberrypi.com/software/operating-systems/).

1\. Download the compressed file to the PC, and extract the img file.\
2\. Connect the TF card to the PC and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.\
3\. Open the [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip) software, select the system image prepared in step 1, and click write to burn the system image.\
4\. After the programming is completed, open the config.txt file in the root directory of the TF card, add the following code at the end of config.txt, and save it.

```
hdmi_group=2
hdmi_mode=87
hdmi_cvt 800 480 60 6 0 0 0
hdmi_drive=1
```

You must ensure that there are no spaces around the equal sign.\
5\. Insert the TF card into the Raspberry Pi and turn on the backlight switch on the back of the LCD.\
6\. Connect the Touch port of the LCD to the USB port of the Raspberry Pi.\
7\. Connect the HDMI port of the LCD to the HDMI port of the Raspberry Pi, power on the Raspberry Pi, and wait for a few seconds to display normally.

#### Calibration in Raspbian

Install related software:

```
sudo apt-get install xinput-calibrator
sudo apt-get install xserver-xorg-input-evdev
sudo cp -rf /usr/share/X11/xorg.conf.d/10-evdev.conf /usr/share/X11/xorg.conf.d/45-evdev.conf
sudo reboot
```

* There will be an additional Calibrate Touchscreen in Menu->Preferences, run the demo to calibrate.
* Perform touch calibration according to the displayed prompt. After calibration, there should be a good touch effect (if the error is relatively large, you can re-run the calibration procedure).
* If you want to save these touch values, you need to create a new 99-calibration.conf file in the following path:

```
/etc/X11/xorg.conf.d/99-calibration.conf
```

* Save information similar to the following to 99-calibration.conf.

<figure><img src="https://www.waveshare.com/w/upload/f/f8/5inch_HDMI_LCD_FAQ1.jpg" alt=""><figcaption></figcaption></figure>

### Resources

#### Software

* [Panasonic SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip)
* [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip)
* [PuTTY](https://files.waveshare.com/upload/5/56/Putty.zip)

#### Resources

* [5inch-HDMI-LCD-B-Bicolor-Holder-LCD-assemble.jpg](https://files.waveshare.com/upload/7/7a/5inch-HDMI-LCD-B-Bicolor-Holder-LCD-assemble.jpg)
* [CE RoHS2.0](https://files.waveshare.com/upload/5/56/5inch_HDMI_LCD_\(B\)_Certification.zip)
* [5inch HDMI LCD (B) panel dimension](https://files.waveshare.com/upload/e/e6/5inch-hdmi-lcd-%26-5inch-hdmi-lcd-b-panel-dimension.pdf)
* [3D drawing of 5inch HDMI LCD (B)](https://files.waveshare.com/upload/9/93/5inch_HDMI_LCD_\(B\)_3D_drawing.zip)
* [PWM control brightness of LCD](https://files.waveshare.com/upload/5/56/PWM_control_backlight_manual.pdf)

Note: We don't recommend you do any hardware modification, which may damage the LCD if you are not good at it. So be careful when you follow this manual.

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion1"><strong>How could I disable the rainbow screen?</strong></a></summary>

Answer:Please add the following command to /boot/config.txt

```
disable_splash=1
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion2"><strong>How to change the splash screen of Pi</strong></a></summary>

You can replace the splash.png from the path /usr/share/plymouth/themes/pix/splash.png to yours.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion3"><strong>How to set long press touch on Raspberry Pi capacitive touch screen?</strong></a></summary>

#### Raspberry Pi Long-press Right-click Software Installation

Test environment: 2022-04-04-raspios-bullseye-armhf 32-bit system\
Supported models: Support Waveshare DSI LCD, DPI LCD, and HDMI LCD capacitive touch screen series.

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

After running, you can touch and long press to realize the right-click function.<br>

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

#If you want to modify the sensitivity, you can modify the size of the two parameters, LONG_CLICK_INTERVAL=1000 LONG_CLICK_FUZZ=200.
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion4"><strong>Do I need an external power supply when I use a 5-inch HDMI LCD (B) connect to Raspberry Pi?</strong></a></summary>

When the Raspberry Pi is powered by a 5V 2A power adapter and connects to 5-inch HDMI LCD (H), it doesn’t require an external power supply by default. However, if the user uses the Raspberry Pi to drive other high-power devices at the same time, the USB interface on the Raspberry Pi may be insufficiently powered, at this time an external power supply is required.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion6"><strong>How to use the touch function when connected to a Linux PC that is non-designated?</strong></a></summary>

You can try to compile the universal touch driver "hid-multitouch" into the kernel, which generally can make the touch function work.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion5"><strong>What can I do if the thin red lines appear on the edge of the screen?</strong></a></summary>

* Edit the config.txt and add this line at the end of the config.txt file:

```
hdmi_drive=1
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion7"><strong>What is the consumption of 5inch HDMI LCD (B)?</strong></a></summary>

With 5V power input, the working current is about 385mA when the backlight is on, and 195mA when the backlight is off.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion8"><strong>Can the brightness of 5-inch HDMI LCD (B) be adjusted by modifying the resistance?</strong></a></summary>

The screen brightness can be changed by modifying the resistance of the resistor in the figure below, the default resistance is 2.7 ohms.

[![5inch HDMI LCDB FAQ2.png](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=5inch_HDMI_LCDB_FAQ2.png\&width=400)](https://www.waveshare.com/wiki/File:5inch_HDMI_LCDB_FAQ2.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion9"><strong>What is the refresh rate of this screen?</strong></a></summary>

60Hz.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(B)#accordion10"><strong>Does the screen not automatically rest, or do I have to execute a command to rest the screen?</strong></a></summary>

It depends on the system, if the system has hibernation, the screen will also be black. If it is the official system of Raspberry Pi, the default is about ten minutes without action to have hibernation.

</details>

### Anti-Piracy

Since the first-generation Raspberry Pi released, Waveshare has been working on designing, developing, and producing various fantastic touch LCDs for the Pi. Unfortunately, there are quite a few pirated/knock-off products in the market. They're usually some poor copies of our early hardware revisions, and comes with none support service.

To avoid becoming a victim of pirated products, please pay attention to the following features when purchasing:

[![RPi-LCD-Anti-Piracy.jpg](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=RPi-LCD-Anti-Piracy.jpg\&width=600)](https://www.waveshare.com/w/upload/6/6d/RPi-LCD-Anti-Piracy-l.jpg)

([Click to enlarge](https://www.waveshare.com/w/upload/6/6d/RPi-LCD-Anti-Piracy-l.jpg))

### Beware of knock-offs

Please note that we've found some poor copies of this item in the market. They are usually made of inferior materials and shipped without any testing.

You might be wondering if the one you're watching or you've purchased in other non-official stores is original, feel free to contact us.

## Official documentation and development resources

Use [Introduction](https://www.waveshare.com/wiki/5inch_HDMI_LCD_\(B\)) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
