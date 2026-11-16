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

# Waveshare SIM7600CE-CNSE 4G HAT for Raspberry Pi 4G 3G 2G GNSS

### Waveshare SIM7600CE-CNSE 4G HAT for Raspberry Pi 4G 3G 2G GNSS

***

### Product Link

{% embed url="https://openelab.io/products/sim7600ce-cnse4ghat" %}

### Introduction

The SIM7600CE-CNSE 4G HAT is a hardware accessory designed for use with compatible development boards or microcontrollers. It is a communication module that provides 4G connectivity, allowing devices to access the internet and cellular networks. The "HAT" in its name stands for "Hardware Attached on Top," which indicates that it is designed to be easily attached to the top of a development board, such as a Raspberry Pi, providing additional functionality. The SIM7600CE-CNSE specifically refers to the model of the 4G module, which is manufactured by SIMCom, a company that specializes in wireless communication modules. This particular module supports various cellular network standards and can be used for a wide range of applications, including IoT devices, remote monitoring systems, and more.

<figure><img src="../../.gitbook/assets/image (889).png" alt=""><figcaption></figcaption></figure>

### Features

* 40PIN GPIO extension header for connecting Jetson Nano.
* Supports dial-up, telephone calls, SMS, mail, TCP, UDP, DTMF, HTTP, FTP, etc.
* Supports GPS, BeiDou, Glonass, and LBS base station positioning.
* Onboard USB interface, to test AT Commands, get GPS positioning data, and so on.
* Breakout UART control pins, to connect with host boards like Arduino/STM32.
* Onboard CP2102 USB to UART converter, for serial debugging.
* SIM card slot, supports 1.8V/3V SIM card.
* Onboard TF card slot, which can be used to store files, text messages, and other data.
* Onboard audio jack and audio decoder chip, for making telephone calls.
* 2 x LED indicators, easy to monitor the working status.
* Onboard voltage translator, the operating voltage can be configured to 3.3V or 5V via jumper.
* Baudrate: 300bps \~ 4Mbps (default: 115200bps)
* Autobauding baudrate: 9600bps \~ 115200bps.
* Comes with online resources and manuals (example demos such as Raspberry/Jetson Nano/Arduino/STM32).

### Specifications

<figure><img src="../../.gitbook/assets/image (885).png" alt=""><figcaption></figcaption></figure>

### Pinout

<figure><img src="../../.gitbook/assets/image (886).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (887).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (888).png" alt=""><figcaption></figcaption></figure>

### How to Use

#### RPi Demo

**Hardware Connection**

pin connection diagram with Raspberry Pi

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7600-PIN.png&#x26;width=300" alt=""><figcaption></figcaption></figure>

SIM7600X 4G HAT has onboard Raspberry Pi GPIO interface, which can be directly inserted into various versions of Raspberry Pi; the following table shows the connection between Raspberry Pi pins and module pins (Raspberry Pi 3rd Generation B+):

| SIM7600X 4G HAT | Raspberry Pi                                                        |
| --------------- | ------------------------------------------------------------------- |
| 5V              | 5V                                                                  |
| GND             | GND                                                                 |
| RXD             | TXD (corresponding to 14 of BCM)                                    |
| TXD             | RXD (corresponding to 15 of BCM)                                    |
| PWR             | P22 (corresponding to P6 of BCM)                                    |
| FLIGHTMODE      | P7 (corresponding to P4 of BCM), enter flight mode when pulled high |

\* FLIGHTMODE is wired to pull up and will enter into flight mode.

#### Raspberry Pi initialization settings

To ensure that the SIM7600X 4G HAT can work normally after being connected to the Raspberry Pi, it is necessary to initialize the level output of some pins of the Raspberry Pi. The specific operations are as follows:

* Download [sample demo](https://files.waveshare.com/upload/2/29/SIM7600X-4G-HAT-Demo.7z), after decompression, rename the c folder under the Raspberry folder to SIM7600X, Then copy the entire SIM7600X folder to the Raspberry Pi /home/pi directory.
* The command line enters the /home/pi/SIM7600X directory and executes the command.

```
chmod 777 sim7600_4G_hat_init
```

* Set the boot initialization script, and run the command:

```
sudo nano /etc/rc.local
```

* Add before exit 0 (as shown below):

```
sh /home/pi/SIM7600X/sim7600_4G_hat_init
```

<figure><img src="https://www.waveshare.com/w/upload/4/4f/Sim7600CE-28.png" alt=""><figcaption></figcaption></figure>

#### Raspberry Pi serial port configuration

Since the Raspberry Pi serial port is used for terminal debugging by default, if you need to use the serial port, you need to modify the Raspberry Pi settings. Execute the following command to enter the Raspberry Pi configuration:<br>

```
sudo raspi-config
```

Select Interfacing Options -> Serial -> no -> yes to disable serial debugging.\
\
Open the /boot/config.txt file, and find the following configuration statement to enable the serial port, if not, add it at the end of the file:<br>

<figure><img src="https://www.waveshare.com/w/upload/8/82/Interface18.png" alt=""><figcaption></figcaption></figure>

```
enable_uart=1
```

Restart to take effect.

#### Raspberry Pi minicom serial port debugging

1\. Insert the module into the Raspberry Pi.\
2\. Install minicom, which is a serial debugging tool for the Linux platform:<br>

```
sudo apt-get install minicom
```

3\. Execute minicom -D /dev/ttyS0 (ttyS0 is the serial port of Raspberry Pi 3B/3B+/4B).\
The default baud rate is 115200.\
Raspberry Pi 5/2B/zero, the user serial device number is ttyAMA0, and the Raspberry Pi 3B/3B+/4B serial device number is ttyS0.\
4\. Take the AT synchronization test as an example, and send relevant commands, as shown in the following figure:\
\
\* minicom can enter setting mode by pressing Ctrl+A, then Z, and select X to exit.\
5\. Raspberry Pi 5 configures the ttyS0 serial port:

<figure><img src="https://www.waveshare.com/w/upload/9/93/Sim7600CE-20.png" alt=""><figcaption></figcaption></figure>

* Edit config.txt file:

```
 sudo nano /boot/config.txt
```

* Add the following and the statement at the end.

```
 dtoverlay=disable-bt
```

* You can see ttyS0 after restarting.

#### Sample Demo

1\. Insert the module into the Raspberry Pi.\
2\. Download the sample demo to the /home/pi/ path:

```
wget https://files.waveshare.com/upload/2/29/SIM7600X-4G-HAT-Demo.7z
sudo apt-get install p7zip-full
7z x SIM7600X-4G-HAT-Demo.7z -r -o/home/pi
sudo chmod 777 -R /home/pi/SIM7600X-4G-HAT-Demo
```

3\. Go to the bcm2835 directory, compile, and install it.

```
chmod +x configure && ./configure && sudo make && sudo make install
```

Note: If there is a problem with the compilation, please refer to the instructions in the FAQ.\
4\. Go to the corresponding instance directory, compile, and run the demo. The relevant instructions are as follows (take the PhoneCall demo as an example):

```
sudo make clean //Clear the original executable file
sudo make //recompile
sudo ./PhoneCall //Run the demo
```

Use a combination of the above commands:<br>

```
sudo make clean && sudo make && sudo ./PhoneCall
```

**PHONECALL Call Demo**

<figure><img src="https://www.waveshare.com/w/upload/5/59/Pnonecall.png" alt=""><figcaption></figcaption></figure>

**SMS Text Message Sending and Receiving Demo**

<figure><img src="https://www.waveshare.com/w/upload/e/ea/SMS.png" alt=""><figcaption></figcaption></figure>

**GPS Positioning Demo**

<figure><img src="https://www.waveshare.com/w/upload/b/b7/GPSPOSTION3.png" alt=""><figcaption></figcaption></figure>

**TCP Network Communication Demo**

<figure><img src="https://www.waveshare.com/w/upload/8/8e/Tcp-network-3.png" alt=""><figcaption></figcaption></figure>

**FTP Download and Upload Demos**

<figure><img src="https://www.waveshare.com/w/upload/7/7d/FTP-DOWNLOAD3.png" alt=""><figcaption></figcaption></figure>

#### Arduino Demo

**Hardware Connection**

Hardware connection to the development board UNO PLUS/Arduino UNO:<br>

| SIM7600X 4G HAT | UNO PLUS/Arduino UNO |
| --------------- | -------------------- |
| 5V              | 5V                   |
| GND             | GND                  |
| TXD             | 0 (RX)               |
| RXD             | 1 (TX)               |
| PWR             | 2                    |

#### Install Arduino library

Download the decompression sample demo.\
Copy the Waveshare\_SIM7600X\_Arduino\_Library folder to the Library directory under the Arduino IDE installation path.\
Open Arduino IDE --> File --> Examples --> Waveshare SIM7600X, and then choose to run the corresponding example demo:<br>

<figure><img src="https://www.waveshare.com/w/upload/3/37/Sim.png" alt=""><figcaption></figcaption></figure>

#### Sample Demo

**PHONECALL Call Demo**

<figure><img src="https://www.waveshare.com/w/upload/2/2f/ARDUINO_demo.png" alt=""><figcaption></figcaption></figure>

**SMS Text Message Sending and Receiving Demo**

<figure><img src="https://www.waveshare.com/w/upload/9/95/ARDUINO_demo2.png" alt=""><figcaption></figcaption></figure>

**GPS Positioning Demo**

<figure><img src="https://www.waveshare.com/w/upload/7/7c/ARDUINO_demo3.png" alt=""><figcaption></figcaption></figure>

**TCP Network Communication Demo**

<figure><img src="https://www.waveshare.com/w/upload/2/2b/ARDUINO_demo4.png" alt=""><figcaption></figcaption></figure>

**FTP Download and Upload Demo**

<figure><img src="https://www.waveshare.com/w/upload/d/d2/ARDUINO_demo5.png" alt=""><figcaption></figcaption></figure>

#### Jetson Nano Demo

**Hardware Connections**

Connection diagram

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Sim7600CE-Jetson_Nano1.png&#x26;width=300" alt=""><figcaption></figcaption></figure>

Jetson Nano has an onboard RaspberryPi 40Pin GPIO interface, SIM7600X 4G HAT can be directly connected and used, and Jetson Nano's terminal access the serial port does not affect serial communication with SIM7600X 4G HAT (ie. Pin10 and Pin8).

<br>

| SIM7600X 4G HAT | Jetson Nano         |
| --------------- | ------------------- |
| 5V              | 5V                  |
| GND             | GND                 |
| TXD             | 10 (Board encoding) |
| RXD             | 8 (Board encoding)  |
| PWR             | 31 (Board code)     |

#### Jetson Nano minicom serial port debugging

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Sim7600CE-Jetson_Nano2.png&#x26;width=300" alt=""><figcaption></figcaption></figure>

1\. Connect the SIM7600X 4G HAT to the Jetson Nano, press the PWRKER button for three seconds, and then turn it on.\
2\. [Use SERIAL to log in to the Jetson Nano terminal](https://www.waveshare.com/wiki/Use_SERIAL_to_log_in_to_the_Jetson_Nano_terminal), install minicom, and enter:

```
sudo apt-get install minicom
```

3\. Run minicom to debug the serial port, and enter in the terminal.

```
sudo minicom -D /dev/ttyTHS1 -b 115200
```

4\. Send the AT command to test, press the PWRKEY button for three seconds to start the shutdown, exit the minicom and press Ctrl+A, then X, and finally press ENTER.<br>

#### Python Demos

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Sim7600CE-Jetson_Nano3.png&#x26;width=300" alt=""><figcaption></figcaption></figure>

After installing the library:<br>

```
sudo apt-get install python3-pip
sudo pip3 install pyserial
sudo apt-get install p7zip
```

Use the wget tool to download the source code to the specified folder of Jetson Nano, and copy the following command:

```
mkdir -p ~/Documents/SIM7600X_4G_HAT
wget -P ~/Documents/SIM7600X_4G_HAT/ 
```

Enter the directory where the source code was just created and downloaded, and use the p7zip tool to unzip it to the current directory.

```
cd ~/Documents/SIM7600X_4G_HAT/
sudo p7zip --uncompress SIM7600X-4G-HAT-Demo.7z
```

AT

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Sim7600CE-Jetson_Nano4.png&#x26;width=300" alt=""><figcaption></figcaption></figure>

SIM7600X\_4G\_HAT is connected to Jetson Nano, connected to the antenna, the demo uses the software to power on and off, there is no need to press the button to power on and off, and when you exit, press Ctrl+C to power off the software. Enter the Jetson Nano/AT directory and execute the command:

```
cd ~/Documents/SIM7600X_4G_HAT/Jetson\ nano/AT/
sudo python3 AT.py
```

GPS

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Sim7600CE-Jetson_Nano5.png&#x26;width=300" alt=""><figcaption></figcaption></figure>

SIM7600X\_4G\_HAT is connected to the Jetson Nano and GNSS antenna. The routine uses software to power on and off. There is no need to press the button to power on and off. When exiting, press Ctrl+C to power off the software. Enter the Jetson Nano/GPS directory and execute the command:

```
cd ~/Documents/SIM7600X_4G_HAT/Jetson\ nano/GPS/
sudo python3 GPS.py
```

PhoneCall

SIM7600X\_4G\_HAT is connected to Jetson Nano, the main antenna, and the earphone. The demo uses software to power on and off, no need to press the button to switch on and off. This demo uses the mobile card to automatically dial 10086. Press Ctrl+C when exiting, and the software will start to Shut down. Enter the Jetson Nano/PhoneCall directory and execute the command:

```
cd ~/Documents/SIM7600X_4G_HAT/Jetson\ nano/PhoneCall/
sudo python3 PhoneCall.py
```

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Sim7600CE-Jetson_Nano-51.png&#x26;width=400" alt=""><figcaption></figcaption></figure>

SMS

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Sim7600CE-Jetson_Nano-52.png&#x26;width=300" alt=""><figcaption></figcaption></figure>

The SIM7600X\_4G\_HAT is connected to the Jetson Nano and the main antenna. The demo uses the software to turn it on and off, and there is no need to press the button to turn it on and off. This demo will automatically shut down the software after sending the information www.waveshare.com to the specified number. When users use SMS routines, they must first use tools such as vim to change the number in line 10 of the SMS.py file, replace \* with a number, and keep the ' symbol.\
Enter the Jetson Nano/SMS directory and execute the command:

```
cd ~/Documents/SIM7600X_4G_HAT/Jetson\ nano/SMS/
sudo python3 SMS.py
```

TCP

The SIM7600X\_4G\_HAT is connected to the Jetson Nano and the main antenna. The demo uses the software to turn it on and off, and there is no need to press the button to turn it on and off.\
Enter the Jetson Nano/TCP directory and execute the command:

```
cd ~/Documents/SIM7600X_4G_HAT/Jetson\ nano/TCP/
sudo python3 TCP.py
```

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=Sim7600CE-Jetson_Nano-53.png&#x26;width=400" alt=""><figcaption></figcaption></figure>

\
More sample demos are continuously updated... &#x20;

### FAQ



<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion35"><strong>When compiling the BCM2835 library, Makefile:327:recipe for target 'aclocal.m4' failed ?</strong><br></a><a href="https://www.waveshare.com/wiki/File:Bcm2835-make-error.jpg"><img src="https://www.waveshare.com/w/upload/8/83/Bcm2835-make-error.jpg" alt="Bcm2835-make-error.jpg"></a></summary>



* Execute autoreconf -vfi, and then recompile, see the figure below:

[![Motor-faq.png](https://www.waveshare.com/w/upload/4/43/Motor-faq.png)](https://www.waveshare.com/wiki/File:Motor-faq.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion34"><strong>When executing the chmod 777 sim7600_4G_hat_init command, an error is reported: "chmod: cannot access 'sim7600_4G_hat_init': No such file or directory"How to deal with it?</strong><br></a><a href="https://www.waveshare.com/wiki/File:2019-10-11_18-59-32.jpg"><img src="https://www.waveshare.com/w/upload/d/d3/2019-10-11_18-59-32.jpg" alt="2019-10-11 18-59-32.jpg"></a></summary>

Please confirm that there is a sim7600\_4G\_hat\_init file in the current path\
[![2019-10-11 19-15-04.jpg](https://www.waveshare.com/w/upload/a/a8/2019-10-11_19-15-04.jpg)](https://www.waveshare.com/wiki/File:2019-10-11_19-15-04.jpg)\
The general operation is: download the sample program, after decompression, rename the c folder under the Raspberry folder to SIM7600X, and then copy the entire SIM7600X folder to the Raspberry Pi /home/pi directory, Enter the command line into the /home/pi/SIM7600X directory, and then execute the chmod 777 sim7600\_4G\_hat\_init command.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion33"><strong>SIM7600 firmware upgrade failed, the prompt is shown below, how to solve?</strong></a></summary>

[![SIM7600X-FAQ (6).png](https://www.waveshare.com/w/upload/8/89/SIM7600X-FAQ_\(6\).png)](https://www.waveshare.com/wiki/File:SIM7600X-FAQ_\(6\).png)<br>

1\. Pay attention to check the device manager, the upgrade process will prompt the new device inserted, and the first upgrade will not have a device driver;\
2\. Pay attention to the USB cable, the USB cable rate is high during the upgrade process, so you need to choose a better quality USB cable to avoid poor contact.\
3\. Need to run the upgrade tool with administrator privilege (SIM7500\_SIM7600\_QDL V1.41 only for Update).\
4\. Uninstall and reinstall the update tool (SIM7500\_SIM7600\_QDL V1.41 only for Update).

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion32"><strong>SIM7600X connected to Raspberry Pi, how to open hotspot without burning Openwrt image?</strong></a></summary>

You can refer to two ways, the detailed steps refer to the following:

* [How to turn a Raspberry Pi Zero W into a 3G 4G router](https://www.waveshare.com/wiki/How_to_set_up_Raspberry_Pi_Zero_W_as_a_3G_4G_router)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion31"><strong>Use the WIN7 system, what should I do if the driver installation fails?</strong></a></summary>

The new driver may not be compatible with some WIN7 systems, you can try the old driver:<br>

* [SIM7600 old driver](https://files.waveshare.com/upload/e/e6/SIM7600-Driver.7z)
* [SIM7600 new driver](https://files.waveshare.com/upload/1/12/SIM7600X-Driver.7z)
* 1\. Download the driver.
* 2\. Connect the 4G HAT to a Windows computer as shown in the hardware connection diagram above (Windows 10 OS is used as an example below)
* 3\. Make sure the module has been powered on properly: refer to the previous section "Switching on and off the module"
* 4\. Open Device Manager->Other Devices->"SimTech, Incorporated "-> Update Driver -> Browse My Computer to find the driver file -> According to the system, select the path where the driver file is stored -> Installation is complete.
* 5\. Install all the recognized devices and drivers:

[![SIM7600G-H 4G09.jpg](https://www.waveshare.com/w/upload/8/82/SIM7600G-H_4G09.jpg)](https://www.waveshare.com/wiki/File:SIM7600G-H_4G09.jpg)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion30"><strong>SIM7600X module NDIS dialing failure, what should I do if the driver cannot be installed?</strong></a></summary>

* Make sure your system kernel is above 5.4. Do not use sudo update to upgrade the Raspberry Pi to the latest version, otherwise, the kernel version will be upgraded to a version higher than the current firmware and will not be recognized.
* It is recommended to use the more convenient [RNDIS dial](https://www.waveshare.com/wiki/Raspberry_Pi_networked_via_RNDIS)
* You can burn the latest Raspberry Pi Raspbian system and reconfigure the NDIS dial-up
* Or use the image that has been configured with the driver [NDIS dial-up self-starting Raspbian system image (driver installed)](https://pan.baidu.com/s/1hnRjIM0NDG5cS6ObaQMXig)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion29"><strong>No response when using SIM7600X on Arduino or other masters?</strong></a></summary>

Generally, it is the problem of baud rate, TTL level, and wiring, the details are as follows:\
[7600X\_connect\_Arduino](https://www.waveshare.com/wiki/7600X_connect_Arduino)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion28"><strong>How to initialize the switch control pins of SIM7600?</strong></a></summary>

Use the following commands:

```
echo "4" > /sys/class/gpio/export
echo "out" > /sys/class/gpio/gpio4/direction
echo "0" > /sys/class/gpio/gpio4/value
echo "6" > /sys/class/gpio/export
echo "out" > /sys/class/gpio/gpio6/direction
echo "0" > /sys/class/gpio/gpio6/value
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion27"><strong>What is the function of the com port for ttyUSB0-ttyUSB5 that appears under the Linux system?</strong></a></summary>

&#x20;Answer:As shown below:

```
1) /dev/ttyUSB0-diag port for output developing messages
2) /dev/ttyUSB1- NMEA port for GPS NMEA data output
3) /dev/ttyUSB2-AT port for AT commands
4) /dev/ttyUSB3-Modem port for ppp-dial
5) /dev/ttyUSB4-Audio port
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion26"><strong>How can I realize the module is recognized when using it in a Linux system?</strong></a></summary>

The following command can be used to detect the presence of Qualcomm Qualcomm devices, and if a COM driver has been loaded (the Raspberry Pi system generally comes with it), a series of ttyUSB\* will also appear:

```
lsusb
ls /dev/ttyUSB*
```

[![SIM7600G-H 4G DTU FQA16.png](https://www.waveshare.com/w/upload/4/46/SIM7600G-H_4G_DTU_FQA16.png)](https://www.waveshare.com/wiki/File:SIM7600G-H_4G_DTU_FQA16.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion25"><strong>What is the role of the AUX antenna, can not connect the MAIN antenna, only connect the AUX antenna?</strong></a></summary>

1. The AUX auxiliary antenna is a diversity antenna, the main antenna signal is not good enough to receive the signal with the receiving antenna, and the physical location is not the same, there is always a better, diversity antenna connected to the bandwidth and rate sensitivity will be increased by about 20%.
2. No diversity antenna can make the receiver obtain a maximum of not more than 3db diversity gain, but the diversity does not line any transmitting function, so to connect to the main antenna, transmit the signal to the base station registered to the network, the auxiliary antenna will only work.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion24"><strong>How to debug SIM7600X via USB TO UART serial port?</strong></a></summary>

Please put the jumper cap on C and connect the USB TO UART interface of SIM7600X to the USB port of a computer or Linux board such as Raspberry Pi through USB type to micro USB to send commands to debug:<br>

[![SIM7600G-H 90.png](https://www.waveshare.com/w/upload/d/da/SIM7600G-H_90.png)](https://www.waveshare.com/wiki/File:SIM7600G-H_90.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion23"><strong>What are the antenna parameters of SIM7600CE 4G HAT?</strong></a></summary>

* Frequency: 700m 800m 900m 1710-1920M 2010-2100M 2300-2400M 2500-2690M-5800MHZ
* Gain: 9dbi ± 0.7db

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion22"><strong>What is the power consumption of SIM7600CE 4G HAT when it loads 4g and gps at the same time?</strong></a></summary>

Open at the same time, average: 110\~170mA

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion21"><strong>What is the working current when connected to the Internet?</strong></a></summary>

Using a USB 5V power supply, after successful networking, the current is generally in the range of 50\~300mA, and the average is about 150mA (for reference only, depending on the network environment and networking status.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion20"><strong>Why can I access the Internet with a regular cell phone SIM card that can make phone calls, but not with an IoT card (traffic card)?</strong></a></summary>



* Confirm whether the frequency band supported by the IoT card covers the frequency band supported by the module.
* APN is not set, please use the following command to configure APN.
* Note: Different operators' APNs is different, here the APN is changed to the corresponding operator.
* It may be blocked, high traffic (real-name IoT) cards are going to be machine card binding, and can only be used on a device (the State Ministry of Industry and Information Technology, Ministry of Public Security, issued to the operator must be so); you can let the IoT card operator check the status of the card and unlock the next.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion19"><strong>When sending AT+CPIN?, return ERROR</strong></a></summary>

This problem is generally caused by poor contact between the SIM card and the SIM card holder of the module.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion18"><strong>What's the type of SIM card ?</strong></a></summary>

Support SIM standard (Standard) card, as shown in the figure below, if it is a Micro or Nano card, you need to add a card sleeve.\
[![SIM card size.png](https://www.waveshare.com/w/upload/a/ac/SIM_card_size.png)](https://www.waveshare.com/wiki/File:SIM_card_size.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion17"><strong>SIM7600X SMS transmission failure, prompt +CMS ERROR? or CME ERROR and other errors?</strong></a></summary>

* Confirming that the SIM7600X is registered to the network and that the SIM card can send and receive SMS messages properly on devices such as cell phones;
* Setting the correct SMS center number;
* Initialize the SMS settings with the following command:

```
AT+CSCS="IRA"
AT+CSMP=17,167,
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion16"><strong>How to set up SMS center number? (SMS center number is a kind of short message server. The SMS messages sent by cell phones need to be sent to the SMS center number first, and then forwarded to the other phone by the SMS center number, which is equivalent to an SMS relay station.)</strong></a></summary>

```
AT+CSCA="+8613800755500"
```

The command should be added + enter to return OK.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion15"><strong>How many SMS messages can the SIM7600CE 4G HAT save?</strong></a></summary>

If the short message is stored in the SIM card, the limit is generally 50. You can use the command: AT+CPMS? make an inquiry.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion14"><strong>The command for SIM7600Xcall recording and playback is?</strong></a></summary>



```
SIM7600X makes a call and the phone answers
ATD131xxxxx816.

Record SIM7600 and phone sound to module memory E disk (record to memory card read D)
AT+CREC=3, "e:/rec.wav"   

End recording
AT+CREC=0

Play sound to the phone side to listen
AT+CCMXPLAYWAV="E:/rec.wav",1

Play sound to SIM7600
AT+CCMXPLAYWAV="E:/rec.wav",2

End playback
AT+CCMXSTOP
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion13"><strong>Some SIM card carriers require a VOLTE function to make calls, how to turn on or off the VOLTE function?</strong></a></summary>

The VOLTE function can be enabled with the following command:

```
at+voltesetting=1
at+cnv=/nv/item_files/modem/mmode/ue_usage_setting,1,01,1
```

The VOLTE function can be disabled with the following command:

```
at+voltesetting=0
at+cnv=/nv/item_files/modem/mmode/ue_usage_setting,0,01,1
```

Note: The difference between Volte calls and regular phone calls: The network of Microsoft calls goes on a packet-switched Internet network. And ordinary phone calls take the circuit-switched (PSTN network) communication network. There is a fundamental difference between the two. By the time of 4G LTE, the packet network can control the delay to low enough, and ordinary phones can make calls directly through VOLTE with the packet network. However, in places where the network is poor, circuit-switched networks are still inseparable.

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion12"><strong>How to locate the base station for SIM7600X, what is the command?</strong></a></summary>



Common commands for the LBS base station positioning function of SIM7600X are as follows:

```
AT+CLBS=? //View the range of parameters that can be set
AT+CNETSTART//Open the network; if it fails to open the network, you can use the command AT+CNETSTOP to close and then open
AT+CLBS=1 //Get the current latitude and longitude
AT+CLBS=2 //Get the detailed address
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion11"><strong>Why is the positioning inaccurate and the coordinates obtained are different from those found online?</strong></a></summary>



After turning on the GPS in the AT debug serial port, turn on the NMEA port to get the dynamic information.<br>

[![SIM7600E-H 4G DTU GNSS.png](https://www.waveshare.com/w/upload/4/47/SIM7600E-H_4G_DTU_GNSS.png)](https://www.waveshare.com/wiki/File:SIM7600E-H_4G_DTU_GNSS.png)\
For more detailed steps, please refer to the following link.\
SIM7600X gets the latitude and longitude in units, we commonly use degrees as the unit, please see below for more details.

* [SIM7600X Positioning\_via\_uSTAR](https://www.waveshare.com/wiki/GPS_L76X_Positioning_via_uSTAR)
* [SIM7600G-H\_4G\_for\_Jetson\_Nano\_Precisely\_Locates\_in\_Gaode\_Map\_API](https://www.waveshare.com/wiki/SIM7600G-H_4G_for_Jetson_Nano_Precisely_Locates_in_Gaode_Map_API)
* [SIMXXX\_Locates\_My\_Location\_on\_Gaode\_Map](https://www.waveshare.com/wiki/SIMXXX_Locates_My_Location_on_Gaode_Map)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion10"><strong>AT PORT does not get the location information, HS-USB NMEA port can get it, what is the problem?</strong></a></summary>



GNSS parameter problem, after restarting the module, initialize the GNSS parameters with the following command can be;

```
AT+CGPSNMEA=197119
```

Or you can use the following commands to obtain the position information.

```
AT+CGPSINFOCFG=10,31
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion9"><strong>What should I do if I can't receive a GPS signal and don't get the location information?</strong></a></summary>

Insert the GPS antenna into the GNSS antenna holder and place the receiver label side down in the open outdoors (note that the rainy weather test can not), the power needs to wait about 1 minute to receive the positioning signal;\
[![SIM7600G-H 4G DTU FQA06.png](https://www.waveshare.com/w/upload/5/5b/SIM7600G-H_4G_DTU_FQA06.png)](https://www.waveshare.com/wiki/File:SIM7600G-H_4G_DTU_FQA06.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion8"><strong>What does the positioning information obtained by SIM7600X via AT+CGPSINFO represent respectively?</strong></a></summary>

From left to right, they are (1) dimension, (2) longitude, (3) date, (4) time, (5) altitude, (6) speed, and (7) heading angle.\
[![SIM7600 GNSS FAQ (1234567).png](https://www.waveshare.com/w/upload/c/ce/SIM7600_GNSS_FAQ_\(1234567\).png)](https://www.waveshare.com/wiki/File:SIM7600_GNSS_FAQ_\(1234567\).png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion7"><strong>Why is my dial-up internet connection so slow?</strong></a></summary>



* Generally, the default configuration of SIM7600 is to automatically select the network standard, and it is likely to choose 2G Internet access; if you need to force the use of 4G mode, you need to enter the following AT command configuration:<br>

```
AT+CNMP=38    //Fixed 4G LTE, if there is no local 4G coverage, you may not be able to register to the network
```

[![Firm 4G LTE.png](https://www.waveshare.com/w/upload/3/30/Firm_4G_LTE.png)](https://www.waveshare.com/wiki/File:Firm_4G_LTE.png)

* If 4G has been fixed and the speed is still not ideal, it may be a frequency band problem;

```
AT+CNBP?  //Backup the current band (the returned band information can be copied to Notepad, etc.)
```

```
AT+CNBP=0x0002000000400183,0x000001E000000000,0x0000000000000021    //After returning to OK, measure the speed
```

```
AT+CNBP=0x0002000004400180,0x000001E000000000,0x000000000000003F   //If the speed doesn't improve, try this
```

[![SIM7600 band speed.png](https://www.waveshare.com/w/upload/d/d0/SIM7600_band_speed.png)](https://www.waveshare.com/wiki/File:SIM7600_band_speed.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion6"><strong>Why does it return NO CARRIER after the computer NDIS dials?</strong></a></summary>

[AT$QCRMCALL=1,1](https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion6)[![SIM7600 dial up no.png](https://www.waveshare.com/w/upload/0/00/SIM7600_dial_up_no.png)](https://www.waveshare.com/wiki/File:SIM7600_dial_up_no.png)

&#x20;Answer:

* Under normal circumstances, SIM7600X has already dialed automatically when it is connected to the Windows system, no need to repeat the dialing, the repeated dialing will return NO CARRIER
*   If you still cannot dial up, please use the following command to change to the Windows default dial-up mode

    ```
    AT+CUSBPIDSWITCH=9001,1,1 
    ```
* The display is turned off and the mobile network is not enabled, you can ignore it and go online directly;

[![SIM7600X rndis dial-up .png](https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=SIM7600X_rndis_dial-up_.png\&width=800)](https://www.waveshare.com/wiki/File:SIM7600X_rndis_dial-up_.png)

* You can also install the driver [SIM7600X dial-up Driver](https://www.waveshare.net/wiki/File:SIM7600X_dial-up_Driver.zip) to update the network card

[![SIM7600 NET work driver.png](https://www.waveshare.com/w/upload/2/22/SIM7600_NET_work_driver.png)](https://www.waveshare.com/wiki/File:SIM7600_NET_work_driver.png)

* After installing the driver, the network card shows that it is enabled

[![SIM7600 dial up succeed.png](https://www.waveshare.com/w/upload/b/bf/SIM7600_dial_up_succeed.png)](https://www.waveshare.com/wiki/File:SIM7600_dial_up_succeed.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion5"><strong>How to get SIM7600X to switch to IPV6 after dial-up?</strong></a></summary>



Set up as below:

```
AT+CGDCONT=1, "IPV6", "APN" //Switch to IPV6, different operators APN is different, pay attention to distinguish the settings
AT+CGDCONT=1, "IP", "APN" //Switch back to IPV4
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion4"><strong>Why can't I control the module with UART on Raspberry Pi, can't open ttyS0 through minicom, prompting any ttyS0?</strong></a></summary>



* Open the Raspberry Pi terminal and input the following commands:

```
sudo raspi-config
Select Interfacing Options -> Serial to turn off shell access and turn on the hardware serial port
```

[![L76X GPS Module rpi serial.png](https://www.waveshare.com/w/upload/3/31/L76X_GPS_Module_rpi_serial.png)](https://www.waveshare.com/wiki/File:L76X_GPS_Module_rpi_serial.png)\
Raspberry Pi 2B/zero, the user serial device number is ttyAMA0; you can use the following command line to confirm that serial0 is the selected serial device number, as follows:<br>

```
ls -l /dev/serial*
```

[![RM520n-gl faq90.png](https://www.waveshare.com/w/upload/6/63/RM520n-gl_faq90.png)](https://www.waveshare.com/wiki/File:RM520n-gl_faq90.png)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion3"><strong>Why is the command sent not displayed after sending an AT command and returning OK?</strong></a></summary>



The SIM7600X can send the following command plus carriage return, and successfully turn on the display after displaying OK.

```
ATE1
```

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion2"><strong>What is the difference between RNDIS, NDIS, PPP, and ECM dialing methods?</strong></a></summary>



Differences as shown below:\
[![Dial-PPP-ECM-RNDIS.png](https://www.waveshare.com/w/upload/a/a8/Dial-PPP-ECM-RNDIS.png)](https://www.waveshare.com/wiki/File:Dial-PPP-ECM-RNDIS.png)<br>

* Linux dial-up:
  * [Raspberry\_Pi\_networked\_via\_RNDIS](https://www.waveshare.com/wiki/Raspberry_Pi_networked_via_RNDIS)
  * [A7600X\_RNDIS\_Dail-up\_Networking](https://www.waveshare.com/wiki/A7600X_RNDIS_Dail-up_Networking)
  * [SIM7600X\_ECM\_Dail-up](https://www.waveshare.com/wiki/SIM7600X_ECM_Dail-up)
  * [SIM820X\_RNDIS\_Dial-Up](https://www.waveshare.com/wiki/SIM820X_RNDIS_Dial-Up)
  * [NDIS\_Dial-Up](https://www.waveshare.com/wiki/NDIS_Dial-Up)
* Windows dial-up:
  * [Windows\_NDIS\_Dail-Up](https://www.waveshare.com/wiki/Windows_NDIS_Dail-Up)
  * [Windows RNDIS\_Dial-Up](https://www.waveshare.com/wiki/SIM7600X_RNDIS_Dial-Up_on_Windows_10)

</details>

<details>

<summary><a href="https://www.waveshare.com/wiki/SIM7600CE-CNSE_4G_HAT#accordion1"><strong>What should I do if the network is abnormal?</strong></a></summary>

In this case, it may be that you have not successfully connected to the network, you can follow the steps below to troubleshoot：\
1\. First check the hardware connection:

* Check if the MAIN antenna is connected properly；<br>
* Whether the connected SIM card can communicate and surf the Internet normally on mobile phones and other devices：<br>
* If the Raspberry Pi is connected, whether the module enters airplane mode;<br>

2\. After confirming that there is no problem with the hardware, the software can use these instructions：<br>

* Check if the sim card is in good contact: AT+CPIN?<br>
* Check if the network mode setting is correct: AT+CNMP?<br>
* Check the signal quality of the current environment: AT+CSQ<br>
* Check carrier access：AT+COPS?<br>
* Check internet connection：AT+CPSI?<br>
* Check for successful registration to the network: AT+CGREG?<br>

[![SIM7600X network check.png](https://www.waveshare.com/w/upload/d/df/SIM7600X_network_check.png)](https://www.waveshare.com/wiki/File:SIM7600X_network_check.png)

</details>
