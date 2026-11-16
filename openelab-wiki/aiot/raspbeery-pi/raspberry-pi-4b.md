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

# Raspberry Pi 4B

### Raspberry Pi 4B

***

### Product Link

{% embed url="https://openelab.io/products/raspberrypi45" %}

### Introduction

I am a Raspberry Pi 4 Model B. Compared to the 3B+, my processor speed has significantly increased with rich multimedia capabilities, multiple memory versions, and superior connectivity. Integrated with a PCIe link connecting USB 2 and USB 3 ports, along with a native Ethernet controller. It features greatly improved GPU functionality, resulting in faster input/output speeds.

<figure><img src="../../.gitbook/assets/image (710).png" alt=""><figcaption></figcaption></figure>

### Features

* BCM2711B0 (ARM Cortex-A72)
  * 64-bit 1.5GHz quad-core
* Choice of RAM
  * PI4B-1GB: 1GB
  * PI4B-2GB: 2GB
  * PI4B-4GB: 4GB
* Gigabit Ethernet
* 802.11ac 2.4GHz/5GHz dual-band NIC
* Bluetooth 5.0, BLE
* USB 3.0 x 2, USB 2.0 x 2
* micro HDMI x 2 (supports 4Kp60)
* PoE header (supports PoE HAT)
* MicroSD slot
* 3.5 mm audio jack
* 40PIN GPIO header
* CSI camera interface
* DSI display interface
* USB Type C power supply (5V/3A or above)

### Product Size

<figure><img src="https://www.waveshare.com/w/upload/7/7d/PI4-07.jpg" alt=""><figcaption></figcaption></figure>

### How to use

1. Prepare an SD card and card reader.
2. Download the system [(click me to download)](https://www.raspberrypi.org/downloads/raspberry-pi-os/) Raspberry Pi 4 needs to download the latest released system (or the following version as shown in the figure) before it can be used.
3. Format the SD card: Use a card reader to insert the SD card into the computer, and use the SDFormatter.exe software to format the SD card. [Click here to download SDFormatter.exe](https://files.waveshare.com/upload/6/60/SDCardFormatterv5_WinEN.zip), and click to format the SD card.
4. Burn the image: use Win32DiskImager.exe to burn the image. Select the image to be burned, and click "Write" to burn, [(click here to download Win32DiskImager.exe)](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip). After the burning is completed, you will be prompted whether you want to format, here you need to click Cancel.
5. Start RPI4B: Insert the SD card after programming into the Raspberry Pi, and connect the adapter with the Type-C interface of 5V 3A to start the Raspberry Pi. Normally, you can see that the Power light is always on red, and the ACT green light is flashing.
6. Connect peripherals such as an on-screen mouse and keyboard to start your Raspberry Pi journey.<br>

<figure><img src="https://www.waveshare.com/w/upload/9/92/PI4-02.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/2/20/SDFormatter.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/3/38/Win32DiskImager.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/b/b2/PI4-05.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://www.waveshare.com/w/upload/7/7d/PI4-06.jpg" alt=""><figcaption></figcaption></figure>

### Resource

* [Raspberry Pi Hardware Resouces (official)](https://www.raspberrypi.org/documentation/hardware/raspberrypi/README.md)
* [Help Center](http://www.raspberrypi.org/help/)
* [Panasonic\_SDFormatter](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip)
* [Win32DiskImager](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip)
* [putty](https://files.waveshare.com/upload/5/56/Putty.zip)
* [wiringPi & bcm2835 C LIB](https://www.waveshare.com/wiki/File:RPi_software.zip)
* [Image](http://www.raspberrypi.org/downloads/)

### General Tutorial Series

* [Raspberry Pi Tutorial Series](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series)
* [Raspberry Pi Tutorial Series: Access your Pi](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_Access_your_Pi)
* [Raspberry Pi Tutorial Series: Getting Started with lighting up an LED](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_Getting_Started_with_lighting_up_an_LED)
* [Raspberry Pi Tutorial Series: External Button](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_External_Button)
* [Raspberry Pi Tutorial Series: I2C](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_I2C)
* [Raspberry Pi Tutorial Series: I2C Programming](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_I2C_Programming)
* [Raspberry Pi Tutorial Series: 1-Wire DS18B20 Sensor](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_1-Wire_DS18B20_Sensor)
* [Raspberry Pi Tutorial Series: Infrared Remote Control](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_Infrared_Remote_Control)
* [Raspberry Pi Tutorial Series: RTC](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_RTC)
* [Raspberry Pi Tutorial Series: PCF8591 AD/DA](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_PCF8591_AD/DA)
* [Raspberry Pi Tutorial Series: SPI](https://www.waveshare.com/wiki/Raspberry_Pi_Tutorial_Series:_SPI)

### FAQ

<details>

<summary><mark style="color:green;"><strong>Question:How to assign the touch to the main screen of the Raspberry Pi 4 dual-screen display?</strong></mark></summary>

Answer:

1\. Enter xrandr on the Raspberry Pi terminal to check the HDMI-ID where the main screen is located (mostly HDMI-1);

[![Pi4-specified touch-1.png](https://www.waveshare.com/w/upload/f/fa/Pi4-specified_touch-1.png)](https://www.waveshare.com/wiki/File:Pi4-specified_touch-1.png)

2\. Enter xinput in the Raspberry Pi terminal to check the touch ID where the main screen is located (there are 2 touch IDs, if you don't know which one is the main screen, you can try both);

[![Pi4-designated touch-2.png](https://www.waveshare.com/w/upload/c/c7/Pi4-designated_touch-2.png)](https://www.waveshare.com/wiki/File:Pi4-designated_touch-2.png)

3\. Run the command: xinput map-to-output \<touch ID> \<HDMI-ID>

(After matching the ID value, run the command to specify the touch to the main screen, such as: xinput map-to-output 7 HDMI-1 )

[![Pi4-Specify touch-3.png](https://www.waveshare.com/w/upload/6/6e/Pi4-Specify_touch-3.png)](https://www.waveshare.com/wiki/File:Pi4-Specify_touch-3.png)

4\. Since the command needs to be re-entered every time the boot is turned on, this command can be added to the boot auto-start:

sudo nano /etc/xdg/lxsession/LXDE-pi/autostart

Add: xinput map-to-output 7 HDMI-1 (remember to change to your own corresponding ID), then restart.

[![Pi4-boot-start-4.png](https://www.waveshare.com/w/upload/a/ab/Pi4-boot-start-4.png)](https://www.waveshare.com/wiki/File:Pi4-boot-start-4.png)

</details>

&#x20;
