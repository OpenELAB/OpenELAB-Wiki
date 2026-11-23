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

# Waveshare 10.1 inch QLED Touch Display

{% hint style="info" %}
[**View Waveshare 10.1 inch QLED Touch Display, 1280×720 HDMI on OpenELAB**](https://openelab.io/products/10-1-inch-qled-touch-display)

**Store SKU / option:** `Waveshare-19905`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare 10.1 inch QLED Touch Display

***

### Product Link

{% embed url="https://openelab.io/products/10-1-inch-qled-touch-display" %}

### Features

* 10.1-inch QLED quantum dot display, wider color gamut, more pure chroma, and longer lifetime.
* 1280 x 720 hardware resolution, support software resolution (up to 1920 x 1080).
* 10-point capacitive touch control.
* Toughened glass capacitive touch panel, 6H hardness (case version only).
* When used with Raspberry Pi, supports Raspberry Pi OS / Ubuntu / Kali and Retropie.
* Ubuntu is supported when used with Jetson Nano.
* When used as a computer monitor, supports Windows 11/10/8.1/8/7.
* Support popular Game Consoles like Xbox360, PS4, and SWITCH.
* Multi-languages OSD menu, for power management, brightness/contrast adjustment, etc.
* Onboard a 3.5mm audio jack and supports HDMI audio output.

### What's On Board

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Exterior-Size.jpg&#x26;width=700" alt=""><figcaption></figcaption></figure>

### Working with PC

This product supports Windows 11/10/8.1/8/7 OS：

1\. Connect the 5V power supply to the Power port of the LCD, and you can see that the LCD backlight is on normally.\
2\. Connect the TOUCH interface of the LCD to the USB interface of the PC. Wait for a while, the windows will automatically recognize the touch function.\
3\. Connect the HDMI interface of the LCD to the HDMI port of the PC. About 5s later, you can see the LCD display properly. If you need the audio, you can insert 3.5mm earphones into HP ports.

Note:

1\) When the computer is connected to several different displays at the same time, only this LCD can be used to control the cursor on the main display, so we recommended setting this LCD as the main display.\
2\) Some of PC cannot support the HDMI screen Hot Plug. In this case, restarting the PC can solve.

### Working with Raspberry Pi

Support Raspberry Pi OS / Ubuntu / Kali and Retropie systems for Raspberry Pi.

When working with Raspberry Pi, you should set the resolution of the LCD by yourself, otherwise, the LCD screen will not work. For more detailed information, please read the following section.

Please download the latest version of the image on the [Raspberry Pi official website.](https://www.raspberrypi.com/software/operating-systems/)

1\) Download the compressed file to the PC, and unzip it to get the .img file.2) Connect the TF card to the PC, and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) software to format the TF card.3) Open the [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip) software, select the system image downloaded in step 1, and click "write" to write the system image.4) After the image has finished writing, open the config.txt file in the root directory of the TF card.5) Add the following code at the end of config.txt, then save and quit the TF card safely.

```
hdmi_group=2 
hdmi_mode=87 
hdmi_timings=1280 0 160 32 48 720 0 10 10 12 0 0 0 60 0 77000000 3
```

You must make sure that there are no spaces on either side of the equal sign.

6\) Save and connect the TF card to your Pi then power up.7) Connect the 5V power supply to the Power port of the LCD, and you can see that the LCD backlight is lit normally.8) Connect the Touch interface of the LCD to the USB port of Raspberry Pi.9) Connect the HDMI interface of LCD to the HDMI port of Raspberry Pi and then power on the Raspberry Pi.

After about a few seconds, you can see the LCD display normally.

### Working with Jetson Nano

Using Jetson Nano doesn't require software configuring.

1\) Connect the 5V power supply to the Power port of the LCD, and you can see that the LCD backlight is on normally.2) Connect the TOUCH interface of the display to the USB port of the Jetson Nano.3) Connect the HDMI interface of the display to the HDMI port of Jetson Nano.4) Wait for seconds and the display will work normally. If you need to get the audio, you need to connect 3.5mm earphones to the HP port of the display.

Note:\
When using the HP audio interface, you may need to set the sound output settings in the system.

### Resources

#### Relevant Information

* [PCB Dimensions](https://files.waveshare.com/upload/1/1b/9HP%3D10.1HP-PCBA.png)
* [10.1HP-CAPQLED 3D Drawing](https://files.waveshare.com/upload/3/3e/10.1HP-CAPLCD_3D_Drawing.zip)
* [10.1HP-CAPQLED 3D Preview](https://files.waveshare.com/upload/1/10/10.1HP-CAPLCD_3D_Preview.zip)

#### Software

* [Panasonic SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip)
* [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip)
* [PuTTY](https://files.waveshare.com/upload/5/56/Putty.zip)

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/10.1HP-CAPQLED#accordion1"><strong>How to remove the colored squares during GPU self-test on Raspberry Pi boot-up?</strong></a></summary>

Add the following command to /boot/config.txt:

```
disable_splash=1
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/10.1HP-CAPQLED#accordion2"><strong>How to replace the Raspberry Pi startup logo image?</strong></a></summary>

Replace the custom image with the image in this directory /usr/share/plymouth/themes/pix/splash.png.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/10.1HP-CAPQLED#accordion3"><strong>How to set long press touch on Raspberry Pi capacitive touch screen?</strong></a></summary>

Test environment: 2022-04-04-raspios-bullseye-armhf 32-bit system\
Supported models: Support Waveshare DSI LCD, DPI LCD, and HDMI LCD capacitive touch screen series.64bit system does not support by default

</details>

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

Enter the command:<br>

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

Add in 99-uinput.rules file.<br>

```
KERNEL=="uinput", MODE="0660", GROUP="input"
```

save it and run it in the terminal.<br>

```
sudo udevadm control --reload-rules
sudo udevadm trigger
```

Then reboot:<br>

```
sudo reboot
```

Run after reboot (no sudo needed at this point).<br>

```
evdev-rce
```

After running, you can touch and long press to realize the right-click function.<br>

**Set Startup**

Enter the terminal:<br>

```
sudo mkdir ~/.config/autostart
sudo nano ~/.config/autostart/right_click.desktop
```

Add the following in right\_click.desktop.<br>

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

<details>

<summary><a href="https://www.waveshare.com/wiki/10.1HP-CAPQLED#accordion4"><strong>What is the refresh rate of this screen?</strong></a></summary>

60Hz

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/10.1HP-CAPQLED#accordion5"><strong>Does this screen not automatically rest, or do I have to execute a command to rest the screen?</strong></a></summary>

It depends on the system, if the system has hibernation, then the screen will also be black. If it's the official Raspberry Pi system, the default ten minutes or so without action is to have hibernation.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/10.1HP-CAPQLED#accordion6"><strong>How does 10.1 HP-CAPQLED realize PWM dimming?</strong></a></summary>

Remove the resistor in the red box shown below, and then solder the PWM signal pin to the right pad to realize PWM dimming. Dimming frequency is 4k.

<img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=10.1HP-CAPQLED-faq.png&#x26;width=500" alt="" data-size="original">

</details>

<br>

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/10.1HP-CAPQLED) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
