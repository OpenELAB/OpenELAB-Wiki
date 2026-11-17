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

# OpenELAB RJ11 EASY Plug Main Control Upgrade Board V2.0

### OpenELAB RJ11 EASY Plug Main Control Upgrade Board V2.0

***

### Product Link

{% embed url="https://openelab.io/products/rj11-control-upgrade-board-v2-0" %}

### Introduction

The processor used in OpenELAB EASY plug control board V2.0 is ATmega328.\
It has 5 single Digital ports labeled D5 to D9 (of which 3 can be used as PWM outputs), 1 dual-digital interface (D3-D4), 4 analog inputs (A0-A3), a Joystick interface (D2-A6-A7), a SPI communication, a serial port communication and an IIC communication interface. Also with a USB connection, a power jack, two ICSP headers and a reset button. It breaks out the IO ports with RJ11 6P6C plug.\
Simply connect it to a computer with a USB cable or power it via a DC jack to get started. For convenience of wire connection, we simplify the pins GND and VCC into each plug, so you only need one RJ11 6P6C connector wire to connect an external sensor or module, no need to separately connect the VCC and GND. So don't worry that the wrong wiring will damage the external products.

### Specification

| Microcontroller             | ATmega328P-AU                                       |
| --------------------------- | --------------------------------------------------- |
| Operating Voltage           | 5V                                                  |
| Input Voltage (recommended) | DC7-12V                                             |
| Single Digital Ports        | 5 (D5-D9) (of which 3 provide PWM output)           |
| PWM Digital Ports           | D5, D6, D9                                          |
| Analog Input Pins           | 4 (A0-A3)                                           |
| DC Current per I/O Pin      | 20 mA                                               |
| Flash Memory                | 32KB (ATmega328) of which 0.5 KB used by bootloader |
| SRAM                        | 2KB                                                 |
| EEPROM                      | 1 KB                                                |
| Clock Speed                 | 16 MHz                                              |

### Details

* PCB Dimensions: 100mm x 65mm x 18mm
* Weight: 55.5g

<figure><img src="https://wiki.keyestudio.com/images/thumb/2/2c/KS0240%E5%9B%BE%E7%89%872.png/700px-KS0240%E5%9B%BE%E7%89%872.png" alt=""><figcaption></figcaption></figure>

### Element and Interfaces

Here is an explanation of what every element and interface of the board does:&#x20;

<figure><img src="https://wiki.keyestudio.com/images/thumb/8/8b/PINOUT.jpg/800px-PINOUT.jpg" alt=""><figcaption></figcaption></figure>

### Detailed Use with ARDUINO Software as follows:

#### Step1 | Download the Arduino environment (IDE)

When you get the board, first you should install the Arduino software and driver.\
We usually use the Windows software Arduino 1.5.6 version. You can download it from the link below:\
[https://www.arduino.cc/en/Main/OldSoftwareReleases#1.5.x](https://www.arduino.cc/en/Main/OldSoftwareReleases#1.5.x)\
Or you can browse the ARDUINO website to download the latest version from this link, [https://www.arduino.cc](https://www.arduino.cc/), pop up the following interface.

<figure><img src="https://wiki.keyestudio.com/images/thumb/2/2d/KS0313-1.png/600px-KS0313-1.png" alt=""><figcaption></figcaption></figure>

Then click the SOFTWARE on the browse bar, you will have two options ONLINE TOOLS and DOWNLOADS.

<figure><img src="https://wiki.keyestudio.com/images/thumb/9/9b/KS0313-2.png/600px-KS0313-2.png" alt=""><figcaption></figcaption></figure>

Click DOWNLOADS, it will appear the latest software version of ARDUINO 1.8.5 shown as below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/5/5b/KS0313-3.png/600px-KS0313-3.png" alt=""><figcaption></figcaption></figure>

In this software page, on the right side you can see the version of development software for different operating systems. ARDUINO has a powerful compatibility. You should download the software that is compatible with the operating system of your computer.\
We will take WINDOWS system as an example here. There are also two options under Windows system, one is installed version, the other is non-installed version. For simple installed version, first click Windows Installer, you will get the following page.

<figure><img src="https://wiki.keyestudio.com/images/0/08/KS0313-4.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/f/f8/KS0313-5.png/600px-KS0313-5.png" alt=""><figcaption></figcaption></figure>

This way you just need to click JUST DOWNLOAD, then click the downloaded file to install it.\
For non-installed version, first click Windows ZIP file, you will also get the pop-up interface as the above figure.\
Click JUST DOWNLOAD, and when the ZIP file is downloaded well to your computer, you can directly unzip the file and click the icon of ARDUINO software to start it.

**Installing Arduino (Windows)**

Install Arduino with the exe. Installation package downloaded well.

<figure><img src="https://wiki.keyestudio.com/images/6/67/Arduino_Setup_1.jpg" alt=""><figcaption></figcaption></figure>

Click“I Agree”to see the following interface.

<figure><img src="https://wiki.keyestudio.com/images/7/7c/Arduino_Setup_2.jpg" alt=""><figcaption></figcaption></figure>

Click “Next”. Pop up the interface below.

<figure><img src="https://wiki.keyestudio.com/images/f/fb/Arduino_Setup_3.jpg" alt=""><figcaption></figcaption></figure>

You can press Browse… to choose an installation path or directly type in the directory you want.\
Then click “Install” to initiate installation.

<figure><img src="https://wiki.keyestudio.com/images/d/da/Arduino_Setup_4.jpg" alt=""><figcaption></figcaption></figure>

Wait for the installing process, if appear the interface of Window Security, just continue to click Install to finish the installation.

<figure><img src="https://wiki.keyestudio.com/images/4/49/Arduino1.5.6-_setup_5.png" alt=""><figcaption></figcaption></figure>

**Introduction for Arduino IDE Toolbar**

Double-click the icon of Arduino software downloaded well, you will get the interface shown below.\
[![Ks0313图片1.png](https://wiki.keyestudio.com/images/4/4f/Ks0313%E5%9B%BE%E7%89%871.png)](https://wiki.keyestudio.com/File:Ks0313%E5%9B%BE%E7%89%871.png)\
\
(Note: if the Arduino software loads in the wrong language, you can change it in the preferences dialog. See [the environment page](https://www.arduino.cc/en/Guide/Environment-Languages) for details.)

<figure><img src="https://wiki.keyestudio.com/images/5/5d/717.png" alt=""><figcaption></figcaption></figure>

The functions of each button on the Toolbar are listed below:\
[![IDE.png](https://wiki.keyestudio.com/images/d/dd/IDE.png)](https://wiki.keyestudio.com/File:IDE.png)

| [![IDE 1.png](https://wiki.keyestudio.com/images/0/0e/IDE_1.png)](https://wiki.keyestudio.com/File:IDE_1.png) Verify/Compile | Check the code for errors                           |
| ---------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| [![IDE 2.png](https://wiki.keyestudio.com/images/6/67/IDE_2.png)](https://wiki.keyestudio.com/File:IDE_2.png) Upload         | Upload the current Sketch to the Arduino            |
| [![IDE 3.png](https://wiki.keyestudio.com/images/9/9d/IDE_3.png)](https://wiki.keyestudio.com/File:IDE_3.png) New            | Create a new blank Sketch                           |
| [![IDE 4.png](https://wiki.keyestudio.com/images/a/a1/IDE_4.png)](https://wiki.keyestudio.com/File:IDE_4.png) Open           | Show a list of Sketches                             |
| [![IDE 5.png](https://wiki.keyestudio.com/images/b/b2/IDE_5.png)](https://wiki.keyestudio.com/File:IDE_5.png) Save           | Save the current Sketch                             |
| [![IDE 6.png](https://wiki.keyestudio.com/images/e/ef/IDE_6.png)](https://wiki.keyestudio.com/File:IDE_6.png) Serial Monitor | Display the serial data being sent from the Arduino |

**Installing Driver**

Next, we will introduce the driver installation of board. The driver installation may have slight differences in different computer systems. So in the following let’s move on to the driver installation in the WIN 7 system.\
The Arduino folder contains both the Arduino program itself and the drivers that allow the Arduino to be connected to your computer by a USB cable. Before we launch the Arduino software, you are going to install the USB drivers.\
\
[![KS0001-1.jpg](https://wiki.keyestudio.com/images/5/5f/KS0001-1.jpg)](https://wiki.keyestudio.com/File:KS0001-1.jpg)\
Plug one end of your USB cable into the board and the other into a USB socket on your computer. When you connect the board to your computer at the first time, right click the icon of your “Computer” —>for “Properties”—> click the “Device manager”, under “Other Devices”, you should see an icon for “Unknown device” with a little yellow warning triangle next to it. This is your Arduino.\
Then right-click on the device and select the top menu option (Update Driver Software...) shown as the figure below..

<figure><img src="https://wiki.keyestudio.com/images/thumb/6/67/Driver_2.png/600px-Driver_2.png" alt=""><figcaption></figcaption></figure>

It will then be prompted to either “Search Automatically for updated driversoftware” or “Browse my computer for driver software”. Shown as below. In this page, select “Browse my computer for driver software”.

<figure><img src="https://wiki.keyestudio.com/images/thumb/d/d1/Driver_3.png/600px-Driver_3.png" alt=""><figcaption></figcaption></figure>

After that, select the option to browseand navigate to the “drivers” folder of Arduino installation.

<figure><img src="https://wiki.keyestudio.com/images/thumb/5/50/Driver_4.png/600px-Driver_4.png" alt=""><figcaption></figcaption></figure>

Click “Next” and you may get a security warning, if so, allow the software to be installed. Shown as below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/3/3b/Driver_5.png/600px-Driver_5.png" alt=""><figcaption></figcaption></figure>

Once the software has been installed, you will get a confirmation message. Installation completed, click “Close”.

<figure><img src="https://wiki.keyestudio.com/images/thumb/6/6a/Driver_6.png/600px-Driver_6.png" alt=""><figcaption></figcaption></figure>

Up to now, the driver is installed well. Then you can right click “Computer” —>“Properties”—>“Device manager”, you should see the device as the figure shown below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/d/de/Driver_7.png/600px-Driver_7.png" alt=""><figcaption></figcaption></figure>

#### Step2| Connect the board

Connect the board to your computer using the USB cable. The power LED should go on.\
<br>

<figure><img src="https://wiki.keyestudio.com/images/e/ec/KS0240%E5%9B%BE%E7%89%871.png" alt=""><figcaption></figcaption></figure>

Open the Arduino IDE, you’ll need to click the “Tools”, then select the Board that corresponds to your Arduino.

<figure><img src="https://wiki.keyestudio.com/images/8/8c/Step3.jpg" alt=""><figcaption></figcaption></figure>

#### Step4| Select the Serial Port

Select the serial device of the Arduino board from the Tools | Serial Port menu.\
Note: to avoid errors, the COM Port should keep the same as the Ports shown on Device Manager.

<figure><img src="https://wiki.keyestudio.com/images/4/45/Step4-1.jpg" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/5/55/Step4.jpg" alt=""><figcaption></figcaption></figure>

#### Step5| Upload the Code

Below is an example code for displaying the Hello World! Copy and paste the code to the Arduino environment IDE.

```
int val;
int ledpin=13;
void setup()
{
Serial.begin(9600);
pinMode(ledpin,OUTPUT);
}
void loop()
{
val=Serial.read();
if(val=='R')
{
digitalWrite(ledpin,HIGH);
delay(500);
digitalWrite(ledpin,LOW);
delay(500);
Serial.println("Hello World!");
}
}
Then click verify button to check the errors. If compiling successfully, the message "Done compiling." will appear in the status bar.
After that, click the “Upload” button to upload the code. If the upload is successful, the message "Done uploading." will appear in the status bar. (Note: If you have an Arduino Mini, NG, or other board, you'll need to physically present the reset button on the board immediately before pressing the upload button.)
```

#### Step6| Open the Serial Monitor

After that, click the serial monitor button to open the serial monitor.

<figure><img src="https://wiki.keyestudio.com/images/d/d0/UNO_monitor.png" alt=""><figcaption></figcaption></figure>

Then set the baud rate as 9600, enter an “R” and click Send, you should see the RX led on the board blink once, and then D13 led blink once, finally "Hello World!" is showed on the monitor, the TX led blink once. Congrats!

<figure><img src="https://wiki.keyestudio.com/images/thumb/5/50/Ks0248_monitor_2.png/700px-Ks0248_monitor_2.png" alt=""><figcaption></figcaption></figure>

### Resource Links

You can download the datasheet from the link:\
[https://drive.google.com/open?id=1bb2duubVflWG2dXIBHSjNAtQ8ngSsRTz](https://drive.google.com/open?id=1bb2duubVflWG2dXIBHSjNAtQ8ngSsRTz)

You might also want to look at:\
[the reference](http://arduino.cc/en/Reference/HomePage) for the Arduino language;

Download ARDUINO Software:\
[https://www.arduino.cc/en/Main/OldSoftwareReleases#1.5.x](https://www.arduino.cc/en/Main/OldSoftwareReleases#1.5.x)

### Package Included

* OpenELAB Easy plug control board V2 \* 1pcs
* Acrylic panel\* 2pcs
* 30cm blue RJ11 cable \* 1pcs
* 1m black USB cable \* 1pcs
* M3\*15mm copper pillar \* 4pcs
* M3\*10mm round-head screw \* 8pcs\
  <br>

<figure><img src="https://wiki.keyestudio.com/images/thumb/c/c6/KS0240_(1).jpg/500px-KS0240_(1).jpg" alt=""><figcaption></figcaption></figure>

### Extension Experiment

<figure><img src="https://wiki.keyestudio.com/images/e/e7/KS0240%E5%9B%BE%E7%89%873.png" alt=""><figcaption></figcaption></figure>
