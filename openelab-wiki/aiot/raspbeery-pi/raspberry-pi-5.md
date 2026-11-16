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

# Raspberry Pi 5

### Raspberry Pi 5

***

### Product Link

{% embed url="https://openelab.io/products/raspberry-pi-5-options?_pos=1&_sid=6e797a505&_ss=r&variant=43338348855494" %}

### Introduction

Raspberry Pi 5 is the latest generation flagship product in the Raspberry Pi series, following the success of the Raspberry Pi 4. It provides a 2-3x increase in CPU performance over the previous generation. Boasting rich multimedia, multiple memory versions, and superior connectivity, it also integrates with RP1 I/O controller with broader bandwidth USB3 and additional PCIe interfaces for faster data transmission.

<figure><img src="../../.gitbook/assets/image (773).png" alt=""><figcaption></figcaption></figure>

### Features

* Broadcom BCM2712 (Arm Cortex A76)
  * 64-bit 2.4GHz quad-core processor with 512KB of L2 cache and 2MB of shared L3 cache
* RAM
  * PI5-1GB: 1GB
  * PI5-2GB: 2GB
  * PI5-4GB: 4GB
  * PI5-8GB: 8GB
* Gigabit Ethernet
* 2.4GHz/5GHz dual-frequency 802.11ac Wi-Fi
* Bluetooth 5.0, BLE
* USB 3.0 x 2 (supporting simultaneous 5Gbps operation), USB 2.0 x 2
* micro HDMI x 2 (support 4Kp60)
* Gigabit Ethernet (PoE support)
* MicroSD card slot
* 40PIN GPIO header
* 2 × 4-lane MIPI DSI/CSI interface
* USB Type C（5V/5A）
* Power button
* RTC, powered by external batteries
* PCIe 2.0 x1 interface
* UART header

### Dimensions

<figure><img src="../../.gitbook/assets/image (709).png" alt=""><figcaption></figcaption></figure>

### How to Use

1\. Preparation: SD card, card reader.

2\. Download the system ([Click here to download](https://www.raspberrypi.com/software/operating-systems/)), Raspberry Pi 4 requires the latest system before using (or later version as shown below):

<br>

<figure><img src="https://www.waveshare.com/w/upload/9/92/PI4-02.jpg" alt=""><figcaption></figcaption></figure>

3\. Format the SD card: Insert the SD card into the PC with a card reader, and format the SD card through SDFormatter.exe. [Click here to download SDFormatter.exe](https://files.waveshare.com/upload/d/d7/Panasonic_SDFormatter.zip), and click to format the SD card.<br>

<br>

<figure><img src="https://www.waveshare.com/w/upload/2/20/SDFormatter.png" alt=""><figcaption></figcaption></figure>

4\. Program the image: use Win32DiskImager.exe to burn the image. Select the image to be burned, and click "Write" to program, ([click here to download Win32DiskImager.exe](https://files.waveshare.com/upload/7/76/Win32DiskImager.zip)). After the programming is completed, you will be prompted whether you want to format, here you need to click Cancel.<br>

<br>

<figure><img src="https://www.waveshare.com/w/upload/3/38/Win32DiskImager.png" alt=""><figcaption></figcaption></figure>

5\. Start RPI5: Insert the SD card after programming into the Raspberry Pi, and connect to the adapter with the Type-C interface of 5V 5A to boot the Raspberry Pi. Normally, you can see that the Power light is always on red, and the ACT green light is flashing.\
6\. Connect peripherals such as screen, mouse, and keyboard to start your Raspberry Pi journey.

#### UART Login

The Raspberry Pi 5 has a dedicated connector for debugging UART, supports a maximum baud rate of 921,600bps, and is configurable via EEPROM parameters. It is always active and enabled, and supports direct access to early boot and firmware information; as well as the Linux console after booting.<br>

<figure><img src="https://www.waveshare.com/w/upload/a/ad/Raspberry_Pi_5_-uart.jpg" alt=""><figcaption></figcaption></figure>

The UART connector has three pins.

<figure><img src="https://www.waveshare.com/w/upload/6/63/Raspberry_Pi_5_-uart2.png" alt=""><figcaption></figcaption></figure>

#### RTC (Real-time Clock)

[Official documentation link](https://www.raspberrypi.com/documentation/computers/raspberry-pi-5.html#real-time-clock-rtc)

**Hardware**

The RTC is powered by adding a backup battery using the J5 (BAT) connector and will work without a connection as long as the PI5 is kept powered on. Optionally, you can purchase a dedicated RTC battery for the PI5.

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Raspberry_Pi_5_-uart3.png&#x26;width=600" alt=""><figcaption></figcaption></figure>

**Siftware Debug**

The default device is /dev/rtc0.As for the time, you can see the current time by typing "date" in the command line, connecting to the network Raspberry Pi system will automatically network timing, if the default RTC device has a connection and is working properly, then the RTC time will be updated after the automatic network timing.\
"sudo hwclock -r" for reading the RTC time, if there are many RTC devices, you can use "-f" to select the corresponding device (such as "sudo hwclock -f /dev/rtc1 -r").

**Hwclock**

System clock -> hardware clock (RTC)

```
sudo hwclock -w
```

Synchronize hardware clock (RTC) -> system clock

```
sudo hwclock  -s
 #You need to turn off the network, or turn off network timing, otherwise it will be changed back
```

Set hardware clock time (RTC):

```
sudo hwclock --set --date="9/8/2023 16:45:05"
```

View the hardware clock (RTC)

```
sudo hwclock -r
```

Display version information

```
sudo hwclock --verbose
```

**Auto Wakeup**

To support low-power mode for wake-up alerts, add the configuration:

```
sudo -E rpi-eeprom-config --edit
#Add the following two lines:
POWER_OFF_ON_HALT=1
WAKE_ON_GPIO=0
#Reboot the device after adding (you can connect to the serial port log to view more update log)
sudo reboot
#You can use the following method to test the function: 
echo +600 | sudo tee /sys/class/rtc/rtc0/wakealarm
sudo halt or sudo poweroff
#Will wake up and reboot after 10 minutes
```

**RTC Battery Charging**

Note: Please check whether your RTC battery supports charging and the maximum input voltage before adding the following commands.

```
sudo nano /boot/firmware/config.txt
#Add
dtparam=rtc_bbat_vchg=3000000
#3000000 indicates the maximum voltage, charging to 3V will disable charging, and the voltage lower than 3V will start to trickle charging
```

## FAQ



<details>

<summary><mark style="color:green;"><strong>Question:How to configure the touchscreen with dual displays?</strong></mark></summary>

Answer:

1\. Input "xrandr" on the Raspberry Pi terminal to view the HDMI-ID of the main display (most are HDMI-1);

<img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Pi4-conf-touch-1.png&#x26;width=600" alt="" data-size="original">

2\. Input "xinput" on the Raspberry Pi terminal to view the touch ID of the main display; (there are two touch IDs. If you do not know which one is for the main display, you can try them both.)

<img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Pi4-conf-touch-2.png&#x26;width=600" alt="" data-size="original">

3.Run the command: xinput map-to-output \<touch ID> \<HDMI-ID>;

(The ID value should be changed according to the actual ID checked, for example xinput map-to-output 7 HDMI-1 )

<img src="https://www.waveshare.com/w/upload/d/d8/Pi4-conf-touch-3.png" alt="" data-size="original">

4\. Each time you start Raspberry Pi, you need to re-enter the command to configure the touchscreen, so you can add this command to the auto-start:\
sudo nano /etc/xdg/lxsession/LXDE-pi/autostart

Add the line: xinput map-to-output 7 HDMI-1 (Note that you need to change the ID corresponding to yours), then reboot Raspberry Pi.

<img src="https://www.waveshare.com/w/upload/f/f2/Pi4-auto-start-4.png" alt="" data-size="original">

</details>

<details>

<summary><mark style="color:green;"><strong>Question:Can the old version of the Raspberry Pi operating system be used with the Raspberry Pi 5?</strong></mark></summary>

&#x20;Answer:

No, Raspberry Pi 5 requires the latest version of Raspberry Pi OS Bookworm.

</details>

<details>

<summary><mark style="color:green;"><strong>Question:Does the Raspberry Pi 5 need active cooling?</strong></mark></summary>

&#x20;Answer:

The Raspberry Pi 5 is faster and more powerful than the previous generation Raspberry Pi, and like most general-purpose computers, it performs best with active cooling. Raspberry Pi cases and integrated fans designed for the Raspberry Pi 5 are one way to provide this functionality.

</details>

<details>

<summary><mark style="color:green;"><strong>Question:Can my Raspberry Pi 4 power supply be used with the Raspberry Pi 5?</strong></mark></summary>

&#x20;Answer:

Raspberry Pi 5 is more powerful compared to the Raspberry Pi 4, and using an inadequate power supply may lead to issues. We recommend a high-quality 5V 5A USB-C power supply for optimal performance.

</details>

