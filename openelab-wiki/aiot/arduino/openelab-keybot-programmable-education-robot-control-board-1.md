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

# OpenELAB KEYBOT Programmable Education Robot Control Board

### OpenELAB KEYBOT Programmable Education Robot Control Board

***

### Product Link

{% embed url="https://openelab.io/products/robot-control-board" %}

### Description

The OpenELAB KEYBOT Coding Robot Control Board is particularly designed for car robot control.\
This control board has integrated the UNO R3 control board and a motor drive board into one circuit board, which can directly drive two DC motors.\
For the convenience of car design, this control board comes with a Bluetooth interface (fully compatible with HC-06 Bluetooth module), 2 servo interfaces and a passive buzzer. For easy car control, this control board also comes with 2 slide switches and a reset button. The large slide switch is used for an external power supply control. While the small switch is used for the serial port communication of Bluetooth module.\
For simple connection, it extends all the digital and analog ports out as RJ11 sockets. It also comes with a power interface. The RJ11 socket integrates the digital and analog ports together, so you just need a cable to connect it with sensor modules, pretty simple and convenient.

### Technical Details

* Main control chip: ATMEGA328P-AU
* Motor drive chip: TB6612FNG
* USB to serial chip: ATMEGA16U2-MU
* Input voltage: DC 7-12V
* Motor drive current: 1.2A (ave) / 3.2A (peak)
* Standby current: 47mA
* Comes with a passive buzzer: D13 control
* Motor direction interface: D4 (motor A) and D7 (motor B)
* Motor speed interface: D5 (motor A) and D6 (motor B)
* Comes with 2 slide switches: power control switch (large one) and Bluetooth serial communication control switch (small one)
* Comes with a Bluetooth interface: suitable for HC-06 Bluetooth, fixed direction, can not be connected if reversed.
* Comes with 2 servo interfaces: D9 and D10 control respectively
* Comes with a reset button
* Comes with a power input interface
* 2 DC motor connection interfaces (labeled MA and MB)
* It has 8 telephone sockets for external sensors and modules (internal with power interface). The control terminals are: D3 and D8, D9 and D10, D11, D12, D2 and A0, A1 A2 and A3, A4 and A5, A6 and A7.

### Dimensions

*   105mm\*64mm\*18mm<br>

    <figure><img src="https://wiki.keyestudio.com/images/a/a1/KS0350-1.png" alt=""><figcaption></figcaption></figure>

    <figure><img src="https://wiki.keyestudio.com/images/0/0f/KS0350-2.png" alt=""><figcaption></figcaption></figure>

### Element and Interfaces

Here is an explanation of what every element and interface of the board does:

<figure><img src="https://wiki.keyestudio.com/images/thumb/e/e9/KS0350_-pinout2.jpg/800px-KS0350_-pinout2.jpg" alt=""><figcaption></figcaption></figure>

### Schematic Diagram<br>

<figure><img src="https://wiki.keyestudio.com/images/7/75/KS0350-4.png" alt=""><figcaption></figcaption></figure>

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
We will take WINDOWS system as an example here. There are also two options under Windows system, one is installed version, the other is non-installed version. For simple installed version, first click Windows Installer, you will get the following page.<br>

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

Wait for the installing process, if appear the interface of Window Security, just continue to click Install to finish the installation.<br>

<figure><img src="https://wiki.keyestudio.com/images/4/49/Arduino1.5.6-_setup_5.png" alt=""><figcaption></figcaption></figure>

**Installing Driver**

The driver installation may have slight differences in different computer systems. So in the following let’s move on to the driver installation in the WIN 7 system.\
The Arduino folder contains both the Arduino program itself and the drivers that allow the Arduino to be connected to your computer by a USB cable. Before we launch the Arduino software, you are going to install the USB drivers.

<figure><img src="https://wiki.keyestudio.com/images/5/5f/KS0001-1.jpg" alt=""><figcaption></figcaption></figure>

Plug one end of your USB cable into the KEYBOT Coding Robot Control Board, and the other into a USB socket on your computer. When you connect KEYBOT Coding Robot Control Board to your computer at the first time, right click the icon of your “Computer” —>for “Properties”—> click the “Device manager”, under “Other Devices”, you should see an icon for “Unknown device” with a little yellow warning triangle next to it.

<figure><img src="https://wiki.keyestudio.com/images/thumb/0/04/Driver_1.png/600px-Driver_1.png" alt=""><figcaption></figcaption></figure>

Then right-click on the device and select the top menu option (Update Driver Software...) shown as the figure below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/6/67/Driver_2.png/600px-Driver_2.png" alt=""><figcaption></figcaption></figure>

It will then be prompted to either “Search Automatically for updated driversoftware” or “Browse my computer for driver software”. Shown as below. In this page, select “Browse my computer for driver software”.

<figure><img src="https://wiki.keyestudio.com/images/thumb/d/d1/Driver_3.png/600px-Driver_3.png" alt=""><figcaption></figcaption></figure>

After that, select the option to browseand navigate to the “drivers” folder.

<figure><img src="https://wiki.keyestudio.com/images/thumb/5/50/Driver_4.png/600px-Driver_4.png" alt=""><figcaption></figcaption></figure>

Click “Next” and you may get a security warning, if so, allow the software to be installed. Shown as below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/3/3b/Driver_5.png/600px-Driver_5.png" alt=""><figcaption></figcaption></figure>

Once the software has been installed, you will get a confirmation message. Installation completed, click “Close”.

<figure><img src="https://wiki.keyestudio.com/images/thumb/6/6a/Driver_6.png/600px-Driver_6.png" alt=""><figcaption></figcaption></figure>

Up to now, the driver is installed well. Then you can right click “Computer” —>“Properties”—>“Device manager”, you should see the device as the figure shown below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/d/de/Driver_7.png/600px-Driver_7.png" alt=""><figcaption></figcaption></figure>

**Introduction for Arduino IDE Toolbar**

Double-click the icon of Arduino software downloaded well, you will get the interface shown below.\
[![Ks0313图片1.png](https://wiki.keyestudio.com/images/4/4f/Ks0313%E5%9B%BE%E7%89%871.png)](https://wiki.keyestudio.com/File:Ks0313%E5%9B%BE%E7%89%871.png)\
(Note: if the Arduino software loads in the wrong language, you can change it in the preferences dialog. See [the environment page](https://www.arduino.cc/en/Guide/Environment-Languages) for details.)

<figure><img src="https://wiki.keyestudio.com/images/5/5d/717.png" alt=""><figcaption></figcaption></figure>

The functions of each button on the Toolbar are listed below:\
[![IDE.png](https://wiki.keyestudio.com/images/d/dd/IDE.png)](https://wiki.keyestudio.com/File:IDE.png)<br>

| [![IDE 1.png](https://wiki.keyestudio.com/images/0/0e/IDE_1.png)](https://wiki.keyestudio.com/File:IDE_1.png) Verify/Compile | Check the code for errors                           |
| ---------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| [![IDE 2.png](https://wiki.keyestudio.com/images/6/67/IDE_2.png)](https://wiki.keyestudio.com/File:IDE_2.png) Upload         | Upload the current Sketch to the Arduino            |
| [![IDE 3.png](https://wiki.keyestudio.com/images/9/9d/IDE_3.png)](https://wiki.keyestudio.com/File:IDE_3.png) New            | Create a new blank Sketch                           |
| [![IDE 4.png](https://wiki.keyestudio.com/images/a/a1/IDE_4.png)](https://wiki.keyestudio.com/File:IDE_4.png) Open           | Show a list of Sketches                             |
| [![IDE 5.png](https://wiki.keyestudio.com/images/b/b2/IDE_5.png)](https://wiki.keyestudio.com/File:IDE_5.png) Save           | Save the current Sketch                             |
| [![IDE 6.png](https://wiki.keyestudio.com/images/e/ef/IDE_6.png)](https://wiki.keyestudio.com/File:IDE_6.png) Serial Monitor | Display the serial data being sent from the Arduino |

#### Step2| Driving Two DC Motors

Below is an example code, you can copy and paste it on [Arduino IDE](http://wiki.keyestudio.com/index.php/Download_Arduino_IDE).

```
const int PWMA = 5;  // define the left motor speed control of pin D5
const int PWMB = 6;  // define the right motor speed control of pin D6 
const int INT_A = 4;  // define the left motor control of pin D4 
const int INT_B = 7;  // define the right motor control of pin D7  
void setup() 
{  
   pinMode(PWMA,OUTPUT);  // set the pin of motor control as output
   pinMode(PWMB,OUTPUT);
   pinMode(INT_A,OUTPUT);
   pinMode(INT_B,OUTPUT);
}
void loop() 
{
  digitalWrite(INT_A,HIGH);  // the left motor rotates forward
  digitalWrite(INT_B,HIGH);   // the right motor rotates forward
  analogWrite(PWMA,200);   // the speed of left motor（PWM=200)
  analogWrite(PWMB,200);   // the speed of right motor（PWM=200)
  delay(2000);
  analogWrite(PWMA,0);   // the speed of left motor（PWM=0)
  analogWrite(PWMB,0);   // the speed of right motor（PWM=0)
  delay(2000);
  digitalWrite(INT_A,LOW);   // the left motor rotates backward
  digitalWrite(INT_B,LOW);  // the right motor rotates backward
  analogWrite(PWMA,200);   // the speed of left motor（PWM=200)
  analogWrite(PWMB,200);   // the speed of right motor（PWM=200)
  delay(2000);
}

```

#### Step3| Upload the Code

Open the Arduino IDE, you’ll need to click the “Tools”, then select the Board that corresponds to your Arduino and the serial port.

<figure><img src="https://wiki.keyestudio.com/images/9/99/Ks0350-%E5%9B%BE%E7%89%871.png" alt=""><figcaption></figcaption></figure>

\
Then click the compile button, if compiling successfully, the message "Done compiling." will appear in the status bar. Shown below.<br>

<figure><img src="https://wiki.keyestudio.com/images/0/06/Ks0350-%E5%9B%BE%E7%89%872.png" alt=""><figcaption></figcaption></figure>

After that, click the “Upload” button, if the upload is successful, the message "Done uploading." will appear in the status bar.

<figure><img src="https://wiki.keyestudio.com/images/7/75/Ks0350-%E5%9B%BE%E7%89%873.png" alt=""><figcaption></figcaption></figure>

#### Step4| What You Should See

Done uploading, connect two DC motors to the control board, then supply DC 7-12V power for the control board. Turn on the large slide switch, you should see the two motors rotate forward for 2 seconds, stop 2 seconds then backward for 2 seconds, circularly.<br>

<figure><img src="https://wiki.keyestudio.com/images/d/d5/KS0350-5.png" alt=""><figcaption></figcaption></figure>
