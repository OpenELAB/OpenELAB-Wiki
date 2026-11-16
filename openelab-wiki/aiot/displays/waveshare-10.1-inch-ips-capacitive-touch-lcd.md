# Waveshare 10.1 inch IPS Capacitive Touch LCD

### Waveshare 10.1 inch IPS Capacitive Touch LCD

***

### Product Link

{% embed url="https://openelab.io/products/10-1-inch-ips-capacitive-touch" %}

### Feature

* 10.1-inch IPS screen with 1024 × 600 resolution
* 10-point capacitive touch control, tempered glass panel with a hardness up to 6H
* When used with Raspberry Pi, it supports Raspberry Pi OS / Ubuntu / Kali and Retropie
* When used as a computer monitor, it supports Windows 11/10/8.1/8/7
* When used with Tinker Board 2, it supports Android / Debian
* Ubuntu is supported when used with Jetson Nano
* Support common game consoles such as Microsoft XBOX360 and Nintendo switch
* Support various video input interfaces: HDMI, VGA, and AV (CVBS)
* Support multi-language OSD menu (can be used for power control, adjusting brightness/contrast, etc.)

### Working with RPI

#### Software Setting

Supports Raspberry Pi OS / Ubuntu / Kali and Retropie systems on Raspberry Pi.

Please download the latest version of the image from the [Raspberry Pi official website](https://www.raspberrypi.com/software/operating-systems/).

1\. Download the compressed file to the PC, and extract the img file.\
2\. Connect the TF card to the PC and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.\
3\. Open the [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip) software, select the system image prepared in step 1, and click write to burn the system image.\
4\. After the programming is completed, open the config.txt file in the root directory of the TF card, add the following code at the end of config.txt and save it.

```
hdmi_group=2
hdmi_mode=87
hdmi_cvt 1024 600 60 6 0 0 0
```

#### Hardware connection

1. Connect the HDMI main control board to the RGB interface of the 10.1inch Capacitive Touch LCD (F) with a 40pin FFC cable.
2. Connect the HDMI port of the board to the Raspberry Pi.
3. Connect the Touch interface of the board to the USB interface of the Raspberry Pi.
4. Connect the board to the 12V power adapter.
5. Insert the TF card into the Raspberry Pi and connect the power adapter with 5V/3A.

The hardware connection is shown in the following figure:

<figure><img src="https://www.waveshare.com/w/upload/3/38/10.1inch_HDMI_LCD_(F)01.png" alt=""><figcaption></figcaption></figure>

#### Using Steps

1. Power on the main control board first. Generally, you can see that the upper left corner of the LCD will display the signal source. Here you need to choose HDMI.
   * If the displayed signal source is VGA or AV, you need to press the "Source" button to choose one of them.
   * If there is no signal in the LCD, please check the hardware connection, especially the FFC cable.
2. Power on the Raspberry Pi, please wait for a few seconds, and you can see the LCD display normally.

### Working with PC

Supports PC Windows 11/10/8.1/8/7.&#x20;

#### Hardware Connection

1. Connect the HDMI main control board to the RGB interface of the 10.1inch Capacitive Touch LCD (F) with a 40pin FFC cable.
2. Connect the HDMI port of the LCD to the PC.
3. Connect the Touch interface of the LCD to the USB interface of the PC.
4. Connect the main control board to the 12V power adapter.

#### Using Steps

1. Power on the main control board first. Generally, you can see that the upper left corner of the LCD will display the signal source of the board. Here you need to choose HDMI.
   * If the displayed signal source is VGA or AV, you need to press the "Source" button to choose one of them.
   * If there is no signal in the LCD, please check the hardware connection, especially the FFC cable.
2. Power on the Raspberry Pi, wait a few seconds, and you can see the LCD display normally.

Notice:

1\) When the PC is connected to multiple monitors at the same time, the touch effect works on the main screen by default. If you need to specify the touch to the other screen, see [#Calibrate Touch on Win 10 PC](https://www.waveshare.com/wiki/10.1inch_HDMI_LCD_\(F\)#Calibrate_Touch_on_Win_10_PC).2) Some PCs do not support plug-and-play with HDMI devices. Generally, they can be used normally after restarting the system.

#### Calibrate Touch on Win 10 PC

Take the windows10 system as an example:

* 1\. Enter the Windows settings of the system, type in the search bar and click "Calibrate the screen for pen or touch input" (as shown in the picture below)

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch011.png&#x26;width=700" alt=""><figcaption></figcaption></figure>

* 2\. Click "Setup" in the pop-up "Tablet PC Settings" interface:

<figure><img src="https://www.waveshare.com/w/upload/9/99/Win10_touch02.png" alt=""><figcaption></figcaption></figure>

* 3\. The following text prompt will appear on the screen. Please tap the touch screen with your finger, and the computer will recognize it as a touch screen.

【Note】If the touch screen is blank, press the "Enter" key, and the text prompt will switch to the touch screen. (The screen which displays the text prompt will be used as a touch screen!)

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Win10_touch03.png&#x26;width=800" alt=""><figcaption></figcaption></figure>

### Working with Tinker Board 2

#### Hardware Connection

1. Connect the HDMI host control board to the RGB interface of the 10.1inch Capacitive Touch LCD (F) with a 40pin FFC cable.
2. Connect the HDMI port of the LCD to the PC.
3. Connect the Touch interface of the LCD to the USB interface of the PC.
4. Connect the board to the 12V power adapter.

The hardware connection is shown in the following figure:

<figure><img src="https://www.waveshare.com/w/upload/5/50/10.1inch_HDMI_LCD_(F)04.png" alt=""><figcaption></figcaption></figure>

#### Software Setting

Supports Android and Debian systems for Tinker Board 2.\
1\. Please download the latest version of the image from the [Tinker Board official website](https://tinker-board.asus.com/download-list.html?product=tinker-board-2s). 2. Connect the TF card to PC, and use [SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip) to format the TF card.\
3\. Open the [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip) software, select the system image prepared in step 1, and click write to burn the system image.\
4\. After the programming is completed, insert the TF card to Tinker Board 2 and power on. You can see it display normally after waiting for a few seconds.

### Key Function

<figure><img src="https://www.waveshare.com/w/upload/b/b9/10.1inch_HDMI_LCD_(F)05.png" alt=""><figcaption></figcaption></figure>

* Source button: When using it for the first time, you need to configure the corresponding signal source (when using the menu, this button also has a "return" function).
* Right button: Arrow keys.
* Left button: Arrow keys.
* Menu button: open the menu (when using the menu, this button also has the "OK" function).
* Power button: turn on or off the LCD display.

### Resource

* [Panasonic\_SDFormatter](https://files.waveshare.com/upload/c/c2/Panasonic_SDFormatter_\(10\).zip)
* [Win32DiskImager](https://files.waveshare.com/upload/4/4e/Win32DiskImager_\(6\).zip)
* [putty](https://files.waveshare.com/upload/5/56/Putty.zip)

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/10.1inch_HDMI_LCD_(F)#accordion1"><strong>What is the dimension of the HDMI main control board of the 10.1inch HDMI LCD (F)?</strong></a></summary>

<img src="https://www.waveshare.com/w/upload/8/86/10.1inch_HDMI_LCD_(F)06.png" alt="" data-size="original">

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/10.1inch_HDMI_LCD_(F)#accordion2"><strong>What is the use of the red and blue interfaces on the main control board?</strong></a></summary>

Blue is for the 4PIN speaker interface, and red for is the 4PIN power input (no need to use under normal circumstances).

<img src="https://www.waveshare.com/w/upload/0/04/10.1inch_HDMI_LCD_(F)FAQ01.png" alt="" data-size="original">

The interface definition is shown in the figure below (both are PH2.0 interface specifications):

![](<../../.gitbook/assets/image (873).png>)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/10.1inch_HDMI_LCD_(F)#accordion3"><strong>How to realize PWM dimming for 10.1inch HDMI LCD (F)?</strong></a></summary>

Rotate the 10K resistor shown below 180 degrees. Then the PWM input signal is connected to the NC end of the rotated 10K resistor (indicated by the yellow arrow).

<img src="https://www.waveshare.com/w/upload/0/0e/10.1inch_HDMI_LCD_(F)FAQ02.png" alt="" data-size="original">

</details>

<br>
