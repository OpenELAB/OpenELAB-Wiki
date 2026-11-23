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

# Waveshare 5 inch LCD Touch Screen Display for Raspberry Pi

{% hint style="info" %}
[**View Waveshare 5 inch Resistive LCD Touch Screen 800\*480 for Raspberry Pi on OpenELAB**](https://openelab.io/products/5inch-lcd-touch-screen)

**Store SKU / option:** `Waveshare-10563`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare 5 inch LCD Touch Screen Display for Raspberry Pi

***

### Product Link

{% embed url="https://openelab.io/products/5inch-lcd-touch-screen" %}

### Introduction

5-inch Capacitive Touch Screen LCD, with a resolution of 800 × 480 and a capacitive touch panel, supports Raspberry Pi and can also be used as a computer monitor.

### Features

* 5-inch capacitive touch screen with a hardware resolution of 800 × 480.
* 5-point capacitive touch control, tempered glass panel, hardness up to 6H.
* When works with Raspberry Pi, supports Raspberry Pi OS/Ubuntu/Kali and Retropie systems.
* When working as a computer monitor, supports Windows 11/10/8.1/8/7, 10-point touch.
* Support backlight control, more power saving.

### Working with PC

This product supports Windows 11/10/8.1/8/7 OS.

1\. Turn on the backlight switch on the back of the LCD.2. Connect the TOUCH interface of the LCD to the USB interface of the PC. Wait for a while, the windows will automatically recognize the touch function.3. Connect the HDMI interface of the LCD to the HDMI port of the PC. About 10s later, you can see the LCD display properly.

Note:

* 1\) When the computer is connected to several different displays at the same time, only this LCD can be used to control the cursor on the main display, so we recommend setting this LCD as the main display.
* 2\) Some of the PCs cannot support the HDMI screen Hot Plug. In this case, restarting the PC can solve.
* 3\) Sometimes LCD will flicker because of undersupplying from the USB cable of the PC. You need to connect an external power supply (5V/2A) to the DC port.

### Working with Raspberry Pi

This LCD can support Raspberry Pi OS / Ubuntu / Kali / Retropie systems.

Please download the latest version of the image on the [Raspberry Pi official website.](https://www.raspberrypi.com/software/operating-systems/)

1\) Download the compressed file to the PC, and unzip it to get the .img file.

2\) Connect the TF card to the PC, and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) software to format the TF card.

3\) Open the [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip) software, select the system image downloaded in step 1, and click 'Write' to write the system image.

4\) After the image has finished writing, open the config.txt file in the root directory of the TF card, add the following code at the end of config.txt, then save and quit the TF card safely.

```
hdmi_group=2
hdmi_mode=87
hdmi_cvt 800 480 60 6 0 0 0  
hdmi_drive=1
```

You must make sure that there are no spaces on either side of the equal sign.

5\) Insert the TF card into the Raspberry Pi.

6\) Connect the Touch interface of the LCD to the USB interface of the Raspberry Pi.

7\) Connect the HDMI interface of the LCD to the HDMI interface of the Raspberry Pi, power on the Raspberry Pi, and wait for a few seconds until the LCD displays normally.

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion1"><strong>How to remove the colored squares during GPU self-test on Raspberry Pi boot-up?</strong></a></summary>

Add the following command to /boot/config.txt:

```
disable_splash=1
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion2"><strong>How to replace the Raspberry Pi startup logo image?</strong></a></summary>

Replace the custom image with the image in this directory /usr/share/plymouth/themes/pix/splash.png.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion3"><strong>How to set long press touch on Raspberry Pi capacitive touch screen?</strong></a></summary>

Test environment: 2022-04-04-raspios-bullseye-armhf 32-bit system\
Supported models: Support Waveshare DSI LCD, DPI LCD, and HDMI LCD capacitive touch screen series.64bit system does not support by default

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

Run after reboot (no sudo needed at this point).

```
evdev-rce
```

After running, you can touch and long press to realize the right-click function.<br>

**Set Startup**

Enter the terminal:

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

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion4"><strong>How to replace the Raspberry Pi boot logo image?</strong></a></summary>

Replace the custom image with the image in this directory /usr/share/plymouth/themes/pix/splash.png

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion5"><strong>Do I need an external power supply when I use a 5-inch HDMI LCD (H) V4 with Raspberry Pi?</strong></a></summary>

When the Raspberry Pi is powered by a 5V 2A power adapter and connects to a 5-inch HDMI LCD (H), it doesn’t require an external power supply by default. However, if the user uses the Raspberry Pi to drive other high-power devices at the same time, the USB interface on the Raspberry Pi may be insufficiently powered, at this time an external power supply is required.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion6"><strong>How to use the touch function when connected to a Linux PC that is non-designated?</strong></a></summary>

You can try to compile the universal touch driver "hid-multitouch" into the kernel, which generally can make the touch function work.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion7"><strong>What is the refresh rate of this screen?</strong></a></summary>

60Hz

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion8"><strong>Does this screen not automatically rest, or must the command be executed to rest the screen?</strong></a></summary>

Depending on the system, if the system has hibernation, the screen will also be black. If it is the official Raspberry Pi system, the default ten minutes or so without action is to have hibernation.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion9"><strong>Does the 5-inch HDMI LCD (H) V4 need an external power supply to connect to the Raspberry Pi?</strong></a></summary>

When the Raspberry Pi is powered by a 5V 3A power adapter, no external power supply is required by default. However, if users use Raspberry Pi to drive other high-power peripherals at the same time, it may cause an insufficient power supply to the USB port on Raspberry Pi, and then an external power supply is required.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion10"><strong>How do I use the touch function when connected to a PC or other non-specified mini PC with a Linux system?</strong></a></summary>

You can try to compile the generic touch driver "hid-multitouch" into the kernel, usually it can support touch.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/5inch_HDMI_LCD_(H)_V4#accordion11"><strong>Does this screen support PWM dimming?</strong></a></summary>

No

</details>

### Anti-Piracy

Since the first-generation Raspberry Pi released, Waveshare has been working on designing, developing, and producing various fantastic touch LCDs for the Pi. Unfortunately, there are quite a few pirated/knock-off products in the market. They're usually some poor copies of our early hardware revisions, and comes with none support service.

To avoid becoming a victim of pirated products, please pay attention to the following features when purchasing:

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=RPi-LCD-Anti-Piracy.jpg&#x26;width=600" alt=""><figcaption></figcaption></figure>

### Beware of knock-offs

Please note that we've found some poor copies of this item in the market. They are usually made of inferior materials and shipped without any testing.

You might be wondering if the one you're watching or you've purchased in other non-official stores is original, feel free to contact us.

## Official documentation and development resources

Use [Introduction](https://www.waveshare.com/wiki/5inch_HDMI_LCD_\(H\)_V4) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
