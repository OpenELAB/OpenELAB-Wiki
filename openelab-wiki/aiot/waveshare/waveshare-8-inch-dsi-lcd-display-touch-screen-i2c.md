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

# Waveshare 8 inch DSI LCD Display Touch Screen I2C

### Waveshare 8 inch DSI LCD Display Touch Screen I2C

***

### Product Link

{% embed url="https://openelab.io/products/dsi-lcd-display-touch-screen" %}

### Features

* 8inch capacitive touch display screen, 800 x 480 hardware resolution.
* Capacitive touch panel, support 5-point touch.
* Toughened glass capacitive touch panel, hardness up to 6H.
* Supports Pi5/4B/CM4/3B+/3A+/3B/CM3/CM3+/2B/B+/A+.
* Directly drive the LCD by the DSI interface on the Raspberry Pi, with up to 60Hz refreshing rate.
* When working with Raspberry Pi, support Raspberry Pi OS / Ubuntu / Kali / Volumio and Retropie, driver-free.
* When working with VisionFive, support Debian, single-point touch control, and driver-free.
* When working with Tinker Board 2, support Linux/Android, five-point touch control, and driver-free.
* When working with Core3566, support Debian/Ubuntu, five-point touch control, and driver-free.
* Support backlight brightness adjustable through software control.

## Featured Design

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=8inch-DSI-LCD-Manual-design.jpg&#x26;width=600" alt=""><figcaption></figcaption></figure>

1. LCD FFC cable anti-interference design, more stable for industrial applications.
2. VCOM voltage adjustment for optimizing display effect.
3. Power supply via pogo pins, eliminating messy cables connection.
4. Two types of 5V output headers, for connecting cooling fans or other low-power devices.
5. Reversed the camera hole on the touch panel for the external camera.
6. Large front panel design, makes it easy to match user-defined cases or to be integrated into sorts of devices.
7. Adopts SMD nuts for holding and fixing the board, a more compact structure.

### Hardware Connection

#### Working with Pi 4B/3B+/3A+/3B/2B/B+/A+

1\) Using the FFC cable, connect the 8inch DSI LCD to the 15PIN DSI interface of the Raspberry Pi board.\
2\) For convenience, you can fix the Raspberry Pi on the back of the 8inch DSI LCD with screws, and assemble the copper column.\
The connection is as below: (The Raspberry Pi will power the LCD through the Pogo pin).

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=8inch-DSI-LCD-Manual-02.jpg&#x26;width=700" alt=""><figcaption></figcaption></figure>

#### Working with Pi 5/CM4/CM3+/CM3

1\. Use a DSI-Cable-12cm cable to connect the 8inch DSI LCD to the 22-pin DSI1 interface on the Raspberry Pi board.\
2\. For convenience, you can fix the Raspberry Pi on the back of the 8inch DSI LCD with screws, and assemble the copper column.\
The installation effect is shown in the diagram below: (The Raspberry Pi will power the LCD through pogo pins)<br>

<figure><img src="https://www.waveshare.com/w/upload/2/25/8inch_DSI_LCD_RPI5.jpg" alt=""><figcaption></figcaption></figure>

### Software Setting

#### Raspberry Pi OS Imager Installation

For Raspberry Pi OS/Ubuntu/Kali/Volumio and Retropie system:

* 1\. Connect the TF card to the PC, download and use [Raspberry Pi Imager](https://www.raspberrypi.com/software/) to program the corresponding system image.

<figure><img src="https://www.waveshare.com/w/upload/7/7c/Pan-Tilt_Camera_WRITEIMAGE01.png" alt=""><figcaption></figcaption></figure>

* 2\. After installing the imager, open the "config.txt" file on the TF card root directory, add the following codes at the end of "config.txt", and then save and safely remove the TF card.

```
dtoverlay=vc4-kms-v3d
#DSI1 Use
dtoverlay=vc4-kms-dsi-7inch
#DSI0 Use (Only Pi5/CM4)
#dtoverlay=vc4-kms-dsi-7inch,dsi0
```

* 3\. Insert the TF card into the Raspberry Pi, power on the Raspberry Pi, wait for a few seconds normally, and then you can enter the display, and the system can be touched normally after booting.
* Note: For the Bookworm system on the Raspberry Pi 5, it is recommended to manually update to the latest system version and reboot (network connection is required).

```
#Update the system
sudo apt-get update
sudo apt-get full-upgrade -y
#Reboot the system
sudo reboot
```

#### Backlight Control

WaveShare provides the corresponding demo for the application (only supports Bookworm and Bullseye systems). Users can install it by the following commands:

```
wget 
unzip Brightness.zip
cd Brightness
sudo chmod +x install.sh
./install.sh
```

After installation, you can open it: Menu -》Accessories -》Brightness:

<figure><img src="https://www.waveshare.com/w/upload/6/6a/43H-800480-IPS07.GIF" alt=""><figcaption></figcaption></figure>

In addition, you can also input the following commands to control the backlight brightness in the terminal:

```
echo X | sudo tee /sys/class/backlight/*/brightness
```

X indicates any number from 0 to 255. 0 means the backlight is the darkest, and 255 means the backlight is the brightest. For example:

```
echo 100 | sudo tee /sys/class/backlight/*/brightness
echo 0 | sudo tee /sys/class/backlight/*/brightness
echo 255 | sudo tee /sys/class/backlight/*/brightness
```

#### Bookworm Touchscreen Rotation

1\. Open "Screen Configuration" application:

<figure><img src="https://www.waveshare.com/w/upload/6/65/DSI-LCD-Bookworm-Rotate-01.png" alt=""><figcaption></figcaption></figure>

2\. Enter "Screen" -> "DSI-1" -> "Orientation", select the rotation orientation and click on "Apply". Then, the touch can be rotated aligning with the display.<br>

<figure><img src="https://www.waveshare.com/w/upload/3/35/DSI-LCD-Bookworm-Rotate-04.png" alt=""><figcaption></figcaption></figure>

Note: Only the Bookworm system supports the above synchronous rotation method, for Bullseye and Butser systems, after the display rotates, you need to set the touch rotation additionally.

### Bullseye/Buster Display Rotation

* 1\. Open "Screen Configuration" application:

<figure><img src="https://www.waveshare.com/w/upload/d/d4/DSI-LCD-Bullseye-Rotate-02.png" alt=""><figcaption></figcaption></figure>

* 2\. Enter "Screen"->"DSI-1"->"Orientation", select the rotation direction, and then click on "Apply" to complete the display rotation.

<figure><img src="https://www.waveshare.com/w/upload/a/ae/DSI-LCD-Bullseye-Rotate-03.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/3/3b/DSI-LCD-Bullseye-Rotate-04.png" alt=""><figcaption></figcaption></figure>

#### Stretch/Jessie Display Rotation

For some older systems, which do not use the vc4-kms-v3d or vc4-fkms-v3d driver modes, the display rotation method is as follows:

* 1\. Add statements to the config.txt file (the config file is located in the root directory of the TF card, i.e. /boot)：

```
display_rotate=1 #1：90；2: 180； 3: 270
```

* 2\. Just save and reboot the Raspberry Pi:

```
sudo reboot
```

#### lite Version Display Rotation

① For Bookworm system, you need to modify the ".config/wayfire.ini" file:

```
sudo nano .config/wayfire.ini
#Edit [output:<device>] in wayfire.ini file, if it cannot be found, then you need to manually add [output:DSI-1]
mode = 800x480@60049
position = 0,0
transform = normal
```

Modify the transform value to change the rotation angle. You can change it to normal and rotate 90, 180 or 270 degrees. For systems with kernel version 6.6.20 or higher, touch will follow the rotation after the change.\
② For Bullseye or Buster system, you need to modify the "/boot/cmdline.txt" file:

```
sudo nano /boot/cmdline.txt
#Add the command to display the rotation angle at the beginning of the cmdline.txt file, save and reboot to take effect
#Display rotates 90°
video=DSI-1:800x480M@60,rotate=90
#Display rotates 180°
video=DSI-1:800x480M@60,rotate=180
#Display rotates 270°
video=DSI-1:800x480M@60,rotate=270
```

#### Touch Rotation

For some systems, as the touch direction is different after display rotation, you need to rotate the touch as shown below:\
1\. Install libinput:

```
sudo apt-get install xserver-xorg-input-libinput
```

* If the system you installed is an Ubuntu system, or Jetson Nano, the installation command is:

```
sudo apt install xserver-xorg-input-synaptics
```

2\. Create the xorg.conf.d directory under /etc/X11/ (if this directory already exists, go directly to step 3):

```
sudo mkdir /etc/X11/xorg.conf.d
```

3\. Copy "40-libinput-conf" file to the directory just created:

```
sudo cp /usr/share/X11/xorg.conf.d/40-libinput.conf /etc/X11/xorg.conf.d/
```

4\. Edit:

```
sudo nano /etc/X11/xorg.conf.d/40-libinput.conf 
```

Find the touchscreen part, add the following sentence, and then save.

```
#Find the touchscreen part, add the corresponding rotation Angle command, and then save:  
#90°Right touch rotation: 
Option "CalibrationMatrix" "0 1 0 -1 0 1 0 0 1"
#180° Inverted touch rotation:
#Option "CalibrationMatrix" "-1 0 1 0 -1 1 0 0 1"
#270° Left rotation:
#Option "CalibrationMatrix" "0 -1 1 1 0 0 0 0 1"
```

As shown below:\
\
5\. Reboot the Raspberry Pi:

<figure><img src="https://www.waveshare.com/w/upload/b/b1/Touch_roate.jpg" alt=""><figcaption></figcaption></figure>

```
sudo reboot
```

The touch will be rotated after completing the above steps.

#### Sleep

Run the following commands on the Raspberry Pi terminal, and the screen will enter sleep mode:

```
xset dpms force off
```

Note: The above command is only for Bullseye and Buster systems.

#### Disable touch

At the end of the config.txt file, add the following command corresponding to disabling touch (the config file is located in the root directory of the TF card and can also be accessed via the command: sudo nano /boot/config.txt):

```
disable_touchscreen=1
```

Note: Reboot to take effect after adding the command.

### Resource

#### Software

* [Raspberry Pi Imager](https://www.raspberrypi.com/software/)

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/8inch_DSI_LCD#accordion1"><strong>What is the corner radius of the 8inch DSI LCD?</strong></a></summary>

8.88mm

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/8inch_DSI_LCD#accordion2"><strong>What is the full white brightness of the screen?</strong></a></summary>

300cd/㎡

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/8inch_DSI_LCD#accordion3"><strong>Does it support OrangePi (Rockchip RK3566)?</strong></a></summary>

This screen currently only supports Raspberry Pi and the official OS of Raspberry Pi. For OrangePi (Rockchip RK3566), we have no driver support for the time being.\
It is recommended that you use our driver-free DSI screen, such as an 8-inch DSI LCD, we can provide the RK3288 demo that lights up the screen for you to transplant.

</details>





&#x20;Answer:

