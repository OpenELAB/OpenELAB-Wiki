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

# Waveshare 7 inch Capacitive Touch Screen HDMI

{% hint style="info" %}
[**View Waveshare 7 inch Capacitive Touch Screen LCD 800\*480 HDMI Low Power on OpenELAB**](https://openelab.io/products/7-inch-capacitive-touch-screen-1)

**Store SKU / option:** `Waveshare-10829`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Waveshare 7 inch Capacitive Touch Screen HDMI

***

### Product Link

{% embed url="https://openelab.io/products/7-inch-capacitive-touch-screen-1" %}

### Introduction

7inch Capacitive Touch Screen LCD, HDMI interface, with a resolution of 800 × 480 and a capacitive touch panel, which supports Raspberry Pi and can also be used as a computer monitor.

### Features

* 800 × 480 hardware resolution.
* 5-point capacitive touch control.
* When used with Raspberry Pi, supports Raspberry Pi OS/Ubuntu/Kali and Retropie.
* When used as a computer monitor, supports Windows 11/10/8.1/8/7.
* Support backlight control, saving more power.

### Working with PC

This LCD can support Windows 7/8/8.1/10/11 system.

How to use:

1\) Turn on the backlight switch on the back of the LCD.

2\) Connect the Touch interface of the LCD to the USB interface of the PC. Wait for a while, the windows will automatically recognize the touch function.

3\) Connect the HDMI interface of the LCD to the HDMI interface of the PC.

Note:\
1\) When the computer is connected to several different displays at the same time, only this LCD can be used to control the cursor on the main display, so we recommended to set this LCD as the main display.\
2\) Some PCs do not support plug-and-play with HDMI devices. Generally, they can be used normally after restarting the system.\
3\) Some PCs may cause LCD flickering due to insufficient power supply through the USB interface. Generally, they can be used normally after connecting to an external 5V/2A power supply through the DC interface.

### Working with Raspberry Pi

This LCD can support Raspberry Pi OS / Ubuntu / Kali and Retropie systems. When the LCD works on systems such as Raspberry Pi OS, the resolution must be set manually, otherwise, it will cause an abnormal display.

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

5\) Insert the TF card into the Raspberry Pi

6\) Turn on the backlight switch on the back of the LCD.

7\) Connect the Touch interface of the LCD to the USB interface of the Raspberry Pi.

8\) Connect the HDMI interface of the LCD to the HDMI interface of the Raspberry Pi, power on the Raspberry Pi, and wait for a few seconds until the LCD displays normally.

### EDID Sequence Parameters

If the system of the main control board can automatically recognize the EDID for display, there is no need to additionally set related timing parameters.

Otherwise, you can refer to the following EDID settings:

| Pixel Clock | H Addressable | H Blanking | V Addressable | V Blanking | H Front Porch | H Sync Width | V Front Porch | V Sync Width | H Image Size | V Image Size | H Border | V Border |
| ----------- | ------------- | ---------- | ------------- | ---------- | ------------- | ------------ | ------------- | ------------ | ------------ | ------------ | -------- | -------- |
| 32.00       | 800           | 128        | 480           | 45         | 40            | 48           | 13            | 3            | 108          | 68           | 0        | 0        |

### Resources

#### 3D Drawings

* [7inch HDMI LCD B/C Drawings](https://files.waveshare.com/upload/f/f4/7inch_cad.zip)
* [7inch HDMI LCD (B) panel dimension](https://files.waveshare.com/upload/3/34/7inch-hdmi-lcd-b-panel-dimension.pdf)
* [Assembly tutorial with 7inch HDMI LCD (B) (with bicolor case)](https://www.waveshare.com/img/devkit/accessories/7inch-HDMI-LCD-Bicolor-Holder/7inch-HDMI-LCD-C-assemble.jpg)
* [PWM control brightness of LCD](https://files.waveshare.com/upload/5/56/PWM_control_backlight_manual.pdf)

Note: We don't recommend you do any hardware modification, which may damage the LCD if you are not good at it. So be careful when you follow this manual.

#### Software

* [Panasonic SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip)
* [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip)
* [PuTTY](https://files.waveshare.com/upload/5/56/Putty.zip)

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion1"><strong>How to remove the colored squares from the GPU self-test when booting the Raspberry Pi?</strong></a></summary>

Add the following commands at /boot/config.txt:

```
disable_splash=1
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion2"><strong>How to replace the Raspberry Pi start-up logo?</strong></a></summary>

Replace it with the picture in /usr/share/plymouth/themes/pix/splash.png.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion3"><strong>How to set long press touch on Raspberry Pi capacitive touch screen?</strong></a></summary>

Test environment: 2022-04-04-raspios-bullseye-armhf 32-bit system\
Supported models: Support Waveshare DSI LCD, DPI LCD and HDMI LCD capacitive touch screen series.

#### Software Installation

```
wget https://www.waveshare.com/w/upload/1/18/Evdev-right-click-emulation.zip
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

Add in 99-uinput.rules file.<br>

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
#If you want to modify the sensitivity, you can modify the size of the two parameters, LONG_CL
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion4"><strong>What is the refresh rate of this screen?</strong></a></summary>

60hZ

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion5"><strong>Does this screen not automatically rest, or do I have to execute a command to rest the screen?</strong></a></summary>

Depending on the system, if there's a sleep function, the screen might go black when it activates. The official Raspberry Pi OS typically enters sleep mode after around ten minutes of inactivity.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion6"><strong>What can I do if the thin red lines appear on the edge of the screen?</strong></a></summary>

* Edit the config.txt and add this line at the end of the config.txt file:

```
hdmi_drive=1
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion7"><strong>How to use the touch function when connected to a Linux PC that is non-designated?</strong></a></summary>

You can try to compile the universal touch driver "hid-multitouch" into the kernel, which generally can make the touch function work.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion8"><strong>What is the working current for the 7inch HDMI LCD (B) when it works normally?</strong></a></summary>

Using 5V power supply, the working current of turning on the backlight is about 490mA, and the working current of turning off the backlight is about 90mA.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion9"><strong>7inch HDMI LCD (B) how to use PWM to control the backlight?</strong></a></summary>

As shown in the figure below, change serial number 2 to 68K resistor, serial number 3 to 5.1K resistor, and remove serial number 1 resistor.\
Then connect the PWM pad to the P1 pin of the Raspberry Pi.\
Execute the following command on the Raspberry Pi terminal:

```
 gpio -g pwm 18 0
 gpio -g mode 18 pwm (occupied pins are PWM pins)
 gpio pwmc 1000
 gpio -g pwm 18 X (X ranges from 0 to 1024), 0 is the brightest, 1024 is the darkest
```

[![7inch HDMI LCD (B) PWM .png](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=7inch_HDMI_LCD_%28B%29_PWM_.png\&width=600)](https://www.waveshare.com/wiki/File:7inch_HDMI_LCD_\(B\)_PWM_.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/7inch_HDMI_LCD_(B)#accordion10"><strong>How to control the backlight with PWM on 7inch HDMI LCD (B)?</strong></a></summary>

As shown in the diagram below, solder R80 to a 68K resistor instead, R59 to a 5.1K resistor, and remove the R56 resistor.\
Then connect the PWM pad to the P1 pin of the Raspberry Pi.\
Execute the following command in the Raspberry Pi terminal:

```
gpio -g pwm 18 0
gpio -g mode 18 pwm (occupied pins are PWM pins)
gpio pwmc 1000
gpio -g pwm 18 X (X value between 0 and 1024), 0 is the brightest, and 1024 is the darkest.
```

[![7inch HDMI LCD (B)-faq.png](https://www.waveshare.com/w/upload/b/b6/7inch_HDMI_LCD_\(B\)-faq.png)](https://www.waveshare.com/wiki/File:7inch_HDMI_LCD_\(B\)-faq.png)\
[![7inch HDMI LCD (B)-faq2.png](https://www.waveshare.com/w/upload/9/92/7inch_HDMI_LCD_\(B\)-faq2.png)](https://www.waveshare.com/wiki/File:7inch_HDMI_LCD_\(B\)-faq2.png)

#### Anti-Piracy

Since the first-generation Raspberry Pi released, Waveshare has been working on designing, developing, and producing various fantastic touch LCDs for the Pi. Unfortunately, there are quite a few pirated/knock-off products in the market. They're usually some poor copies of our early hardware revisions, and comes with none support service.

To avoid becoming a victim of pirated products, please pay attention to the following features when purchasing:

[![RPi-LCD-Anti-Piracy.jpg](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=RPi-LCD-Anti-Piracy.jpg\&width=600)](https://www.waveshare.com/w/upload/6/6d/RPi-LCD-Anti-Piracy-l.jpg)

#### Beware of knock-offs

Please note that we've found some poor copies of this item in the market. They are usually made of inferior materials and shipped without any testing.

You might be wondering if the one you're watching or you've purchased in other non-official stores is original, feel free to contact us.

</details>

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/7inch_HDMI_LCD_\(B\)) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                  |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.waveshare.com/wiki/7inch%20HDMI%20LCD%20\(B\)/7inch%20HDMI%20LCD%20\(B\).stp) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
