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

# OpenELAB EASY PLUG Ultimate Starter Kit for Arduino

Windows version：\
We will take Mixly1.0 (Windows version) as example.\
Install Software：\
You will get installation package after downloading. As shown below:\
[![图片1。0.0.png](https://wiki.keyestudio.com/images/a/a9/%E5%9B%BE%E7%89%871%E3%80%820.0.png)](https://wiki.keyestudio.com/File:%E5%9B%BE%E7%89%871%E3%80%820.0.png)

Unzip the package, you will see “Mixly 1.0 for keyestudio.exe”

<figure><img src="https://wiki.keyestudio.com/images/thumb/c/c6/%E5%9B%BE%E7%89%871%E3%80%820.1.png/600px-%E5%9B%BE%E7%89%871%E3%80%820.1.png" alt=""><figcaption></figcaption></figure>

Double-click ”Mixly 1.0 for keyestudio.exe”, the following interface pops up.

<figure><img src="https://wiki.keyestudio.com/images/7/78/%E5%9B%BE%E7%89%871%E3%80%820.2.png" alt=""><figcaption></figcaption></figure>

\
We have to choose correct Arduino development board and name, as shown below:

<figure><img src="https://wiki.keyestudio.com/images/thumb/b/b5/20201228110445.png/800px-20201228110445.png" alt=""><figcaption></figcaption></figure>

Select correct COM port(the corresponding port will be shown after installing driver successfully)

<figure><img src="https://wiki.keyestudio.com/images/thumb/a/aa/20201228110446.png/800px-20201228110446.png" alt=""><figcaption></figcaption></figure>

You have to know the function of every area and interface on Mixly software before uploading program on Arduino development board.

<figure><img src="https://wiki.keyestudio.com/images/c/cf/%E5%9B%BE%E7%89%871%E3%80%820.3.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/f/f4/QQ%E5%9B%BE%E7%89%8720200707142747.png/800px-QQ%E5%9B%BE%E7%89%8720200707142747.png" alt=""><figcaption></figcaption></figure>

#### Install the driver of the development board

Next, we will introduce the driver of the development board. The driver installation may have slight differences in different computer systems. So in the following let’s take an example of the driver installation in the WINDOWS system.

Mixly 1.0 for OpenELAB folder contains its software and driver files. Before we launch the Mixly software, you only need to install the USB drivers.

Double-click the Mixly 1.0 for OpenELAB folder—> arduino—>drivers

The driver files are shown below:

<figure><img src="https://wiki.keyestudio.com/images/e/ee/20201228110449.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/1/1e/044602.png" alt=""><figcaption></figcaption></figure>

Connect the EASY Plug control board V2.0 to the computer with a USB cable.\
Right click the icon of your“Computer”—>“Properties”—>“Device manager”.

If your computer is Windows10, the USB Serial Device(COM8) will be shown. That indicates that the USB driver is installed. But for other systems like Windows 7 or 8, you may have to install the USB driver manually.

<figure><img src="https://wiki.keyestudio.com/images/1/11/%E5%9B%BE%E7%89%871jhfgjf-4.png" alt=""><figcaption></figcaption></figure>

Right-click USB Serial Device(COM8) to select Update driver\
<br>

<figure><img src="https://wiki.keyestudio.com/images/2/21/%E5%9B%BE%E7%89%871jhfgjf-5.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/1/11/%E5%9B%BE%E7%89%871jhfgjf-6.png" alt=""><figcaption></figcaption></figure>

Click “browse my computer for updated driver software”, find out the drivers folder and enter “driver” to search in rectangular box.\
Click “Next”, the driver will be installed successfully

<figure><img src="https://wiki.keyestudio.com/images/9/92/%E5%9B%BE%E7%89%871jhfgjf-7.png" alt=""><figcaption></figcaption></figure>

Click Install to wait for the installation

<figure><img src="https://wiki.keyestudio.com/images/6/6b/%E5%9B%BE%E7%89%871jhfgjf-8.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/1/13/%E5%9B%BE%E7%89%871jhfgjf-9.png" alt=""><figcaption></figcaption></figure>

Click Close and you can see the following device in the Device Manager.

If your computer is Windows7/8, please follow our instruction.

When you connect the board to your computer at the first time, right-click the icon of your “Computer” —>for “Properties”—> click “Device manager”, under “Other Devices”, you should see an icon for “Unknown device” with a little yellow warning triangle next to it.

<figure><img src="https://wiki.keyestudio.com/images/b/b2/%E5%9B%BE%E7%89%871jhfgjf-11.png" alt=""><figcaption></figcaption></figure>

Then right-click on the device and select the top menu option (Update Driver Software...) shown as the figure below.

<figure><img src="https://wiki.keyestudio.com/images/8/85/%E5%9B%BE%E7%89%871jhfgjf-12.png" alt=""><figcaption></figcaption></figure>

It will then be prompted to either “Search Automatically for updated driver software” or “Browse my computer for driver software”. Shown as below. In this page, select “Browse my computer for driver software”.

<figure><img src="https://wiki.keyestudio.com/images/a/a3/%E5%9B%BE%E7%89%871jhfgjf-13.png" alt=""><figcaption></figcaption></figure>

Click “Browse”, then find out the drivers folder and enter “driver” to search in rectangular box. Click “Next”, the driver will be installed successfully. (I place Arduino software folder on the desktop, you could follow my way)

<figure><img src="https://wiki.keyestudio.com/images/8/89/%E5%9B%BE%E7%89%871jhfgjf-14.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/5/5f/%E5%9B%BE%E7%89%871jhfgjf-15.png" alt=""><figcaption></figcaption></figure>

The driver of your device is already installed.

Click“Close”

<figure><img src="https://wiki.keyestudio.com/images/3/3e/%E5%9B%BE%E7%89%871jhfgjf-16.png" alt=""><figcaption></figcaption></figure>

Up to now, the driver is installed well. Then you can right click “Computer” —>“Properties”—>“Device manager”, you should see the device as the figure shown below.

<figure><img src="https://wiki.keyestudio.com/images/c/c8/%E5%9B%BE%E7%89%871jhfgjf-17.png" alt=""><figcaption></figcaption></figure>

#### Start the first program

Click “Open”→ sample → arduino→ Arduino → 01 IN-OUT→01-LED Blink.mix<br>

<figure><img src="https://wiki.keyestudio.com/images/thumb/1/1f/%E5%9B%BE%E7%89%871jhfgjf-18.png/800px-%E5%9B%BE%E7%89%871jhfgjf-18.png" alt=""><figcaption></figcaption></figure>

We have to choose correct Arduino development board and name, as shown below:

<figure><img src="https://wiki.keyestudio.com/images/thumb/f/fb/%E5%9B%BE%E7%89%871jhfgjf-19.png/800px-%E5%9B%BE%E7%89%871jhfgjf-19.png" alt=""><figcaption></figcaption></figure>

The corresponding board and COM port will be shown after setting board and COM port.

<figure><img src="https://wiki.keyestudio.com/images/6/6a/%E5%9B%BE%E7%89%871jhfgjf-20.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/4/4a/%E5%9B%BE%E7%89%871jhfgjf-21.png/800px-%E5%9B%BE%E7%89%871jhfgjf-21.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/0/08/%E5%9B%BE%E7%89%871jhfgjf-22.png/800px-%E5%9B%BE%E7%89%871jhfgjf-22.png" alt=""><figcaption></figcaption></figure>

Click Upload to upload the program

<figure><img src="https://wiki.keyestudio.com/images/thumb/3/31/%E5%9B%BE%E7%89%871jhfgjf-23.png/800px-%E5%9B%BE%E7%89%871jhfgjf-23.png" alt=""><figcaption></figcaption></figure>

Upload successfully. After uploading the program successfully, the onboard LED lights up for 1s, lights off for 1s.

### Import the Library

Open Mixly 1.0 for OpenELAB software, click“Import”then select“Local import”, as shown below:

<figure><img src="https://wiki.keyestudio.com/images/thumb/6/6d/%E5%9B%BE%E7%89%871jhfgjf-24.png/800px-%E5%9B%BE%E7%89%871jhfgjf-24.png" alt=""><figcaption></figcaption></figure>

\
Double-click the folder“KS\_EasyPulg”and select“KS\_EasyPulg”library file

<figure><img src="https://wiki.keyestudio.com/images/thumb/a/a2/%E5%9B%BE%E7%89%871jhfgjf-25.png/800px-%E5%9B%BE%E7%89%871jhfgjf-25.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/7/77/%E5%9B%BE%E7%89%871jhfgjf-26.png/800px-%E5%9B%BE%E7%89%871jhfgjf-26.png" alt=""><figcaption></figcaption></figure>

After importing it, you will see it in the blocks list. Also, the interface will show “import custom library successfully!”

<figure><img src="https://wiki.keyestudio.com/images/thumb/d/db/%E5%9B%BE%E7%89%871jhfgjf-27.png/800px-%E5%9B%BE%E7%89%871jhfgjf-27.png" alt=""><figcaption></figcaption></figure>

### Installing Arduino Software

When you get the control board, first you should install the Arduino software and driver. We usually use the software Arduino 1.5.6 version. You can download it from the link below: [https://www.arduino.cc/en/Main/OldSoftwareReleases#1.5.x](https://www.arduino.cc/en/Main/OldSoftwareReleases#1.5.x) Or you can browse the ARDUINO website to download the latest version from this link, [https://www.arduino.cc](https://www.arduino.cc/), pop up the following interface.

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

**Installing Driver**

Next, we will introduce the driver installation of UNO R3 development board. The driver installation may have slight differences in different computer systems. So in the following let’s move on to the driver installation in the WIN 7 system.\
The Arduino folder contains both the Arduino program itself and the drivers that allow the Arduino to be connected to your computer by a USB cable. Before we launch the Arduino software, you are going to install the USB drivers.\
\
[![KS0001-1.jpg](https://wiki.keyestudio.com/images/5/5f/KS0001-1.jpg)](https://wiki.keyestudio.com/File:KS0001-1.jpg)\
Plug one end of your USB cable into the Arduino and the other into a USB socket on your computer. When you connect UNO board to your computer at the first time, right click the icon of your “Computer” —>for “Properties”—> click the “Device manager”, under “Other Devices”, you should see an icon for “Unknown device” with a little yellow warning triangle next to it. This is your Arduino.

<figure><img src="https://wiki.keyestudio.com/images/thumb/0/04/Driver_1.png/600px-Driver_1.png" alt=""><figcaption></figcaption></figure>

Then right-click on the device and select the top menu option (Update Driver Software...) shown as the figure below..

<figure><img src="https://wiki.keyestudio.com/images/thumb/6/67/Driver_2.png/600px-Driver_2.png" alt=""><figcaption></figcaption></figure>

It will then be prompted to either “Search Automatically for updated driversoftware” or “Browse my computer for driver software”. Shown as below. In this page, select “Browse my computer for driver software”.

<figure><img src="https://wiki.keyestudio.com/images/thumb/d/d1/Driver_3.png/600px-Driver_3.png" alt=""><figcaption></figcaption></figure>

After that, select the option to browseand navigate to the “drivers” folder of Arduino installation.

<figure><img src="https://wiki.keyestudio.com/images/3/3f/KS0286-4.png" alt=""><figcaption></figcaption></figure>

Click “Next” and you may get a security warning, if so, allow the software to be installed. Shown as below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/3/3b/Driver_5.png/600px-Driver_5.png" alt=""><figcaption></figcaption></figure>

Once the software has been installed, you will get a confirmation message. Installation completed, click “Close”.

<figure><img src="https://wiki.keyestudio.com/images/thumb/6/6a/Driver_6.png/600px-Driver_6.png" alt=""><figcaption></figcaption></figure>

Up to now, the driver is installed well. Then you can right click “Computer” —>“Properties”—>“Device manager”, you should see the device as the figure shown below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/d/de/Driver_7.png/600px-Driver_7.png" alt=""><figcaption></figcaption></figure>

### Let’s Get Started With Your Projects

#### Project 1: Hello World Overview

[![Arduino quickstart.jpg](https://wiki.keyestudio.com/images/thumb/0/06/Arduino_quickstart.jpg/200px-Arduino_quickstart.jpg)](https://wiki.keyestudio.com/File:Arduino_quickstart.jpg)

This project is very simple. You can use only a main board and a USB cable to display the “Hello World!”. It is a communication experiment between the EASY Plug control board and PC. This is an entry experiment for you to enter the Arduino programming world.\
Note that need to use a serial communication software, Arduino IDE. In the above part, you can check the detailed use of Arduino IDE.\
Component Required:

* EASY plug control board\*1
* USB cable\*1\
  Component Introduction:

<figure><img src="https://wiki.keyestudio.com/images/b/b2/Ks0397-1.jpg" alt=""><figcaption></figcaption></figure>

The processor used in OpenELAB EASY plug control board V2.0 is ATmega328. It has 5 single Digital ports labeled D5 to D9 (of which 3 can be used as PWM outputs), 1 dual-digital interface (D3-D4), 4 analog inputs (A0-A3), a Joystick socket (D2-A6-A7), a SPI, a serial port and an IIC communication interface. Also with a USB connection, a power jack, two ICSP headers and a reset button. It breaks out the IO ports with RJ11 6P6C plug.\
Connect It Up\
Connect the control board to your computer via a micro USB cable.\
<br>

<figure><img src="https://wiki.keyestudio.com/images/thumb/d/dc/0397Connect1.png/500px-0397Connect1.png" alt=""><figcaption></figcaption></figure>

Upload the Code\
Below is an example code for displaying the Hello World!

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
Select the Arduino Board
Open the Arduino IDE, you’ll need to click the “Tools”, then select the Board that corresponds to your Arduino.
```

<figure><img src="https://wiki.keyestudio.com/images/thumb/9/9d/Arduino_Board.png/500px-Arduino_Board.png" alt=""><figcaption></figcaption></figure>

Select your serial port\
Select the serial device of the Arduino board from the Tools | Serial Port menu.\
Note: to avoid errors, the COM Port should keep the same as the Ports shown on Device Manager.\
\
[![thumb](https://wiki.keyestudio.com/images/thumb/e/ea/Serial_port.jpg/600px-Serial_port.jpg)](https://wiki.keyestudio.com/File:Serial_port.jpg) ![thumb](https://wiki.keyestudio.com/images/thumb/e/ea/Serial_port2.jpg/400px-Serial_port2.jpg)<br>

\
Then click verify button to check the errors. If compiling successfully, the message "Done compiling" will appear in the status bar.

<figure><img src="https://wiki.keyestudio.com/images/thumb/f/f7/Serial_port3.png/700px-Serial_port3.png" alt=""><figcaption></figcaption></figure>

After that, click the “Upload” button to upload the code. If the upload is successful, the message "Done uploading" will appear in the status bar.

<figure><img src="https://wiki.keyestudio.com/images/thumb/1/14/Serial_port4.png/700px-Serial_port4.png" alt=""><figcaption></figcaption></figure>

Open the Serial Monitor\
After that, click the monitor button to open the serial monitor.

<figure><img src="https://wiki.keyestudio.com/images/thumb/9/94/Serial_Monitor.png/500px-Serial_Monitor.png" alt=""><figcaption></figcaption></figure>

Then set the baud rate to 9600, enter an “R” and click Send, you should see the RX led on the board blink once, and then D13 led blink once, finally "Hello World!" is showed on the monitor, and TX led blink once.\
Congrats! Your first simple program is complete.

<figure><img src="https://wiki.keyestudio.com/images/thumb/2/22/Hello_World1.png/500px-Hello_World1.png" alt=""><figcaption></figcaption></figure>

Note: In this project, we take Arduino code as an example to show Hello World. But in the following projects, we will take Mixly Code as example to start the experiments. It will be more simple and easier for you to get understand of the program.

**How To Get Started With Mixly Projects**

* Import the Library

1\) Begin with the Mixly projects, the first step you should import the corresponding library.\
Open the Mixly 0.998 software, click Import. Shown below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/f/f0/Mixly_01.png/500px-Mixly_01.png" alt=""><figcaption></figcaption></figure>

2\) Open the folder we provided, you can double-click to open the library KS\_EasyPulg

<figure><img src="https://wiki.keyestudio.com/images/thumb/f/fd/Mixly_02.png/500px-Mixly_02.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/b/bc/Mixly_03.png/500px-Mixly_03.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/c/cf/Mixly_04.png/500px-Mixly_04.png" alt=""><figcaption></figcaption></figure>

3\) If import the custom library successfully, you should see it on the Mixly blocks interface. Shown below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/c/c5/Mixly_05.png/500px-Mixly_05.png" alt=""><figcaption></figcaption></figure>

**Start with Mixly Project - Saying Hello World**

1\) Hookup Guide\
Connect the control board to your computer via a micro USB cable.

<figure><img src="https://wiki.keyestudio.com/images/thumb/d/dc/0397Connect1.png/500px-0397Connect1.png" alt=""><figcaption></figcaption></figure>

2\) Open the Program\
Click Open to open your first program Hello World. Follow the steps below.

<figure><img src="https://wiki.keyestudio.com/images/thumb/5/5a/0397hello_1.png/500px-0397hello_1.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/0/07/0397hello_2.png/500px-0397hello_2.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/9/97/0397hello_3.png/500px-0397hello_3.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/2/24/0397hello_4.png/500px-0397hello_4.png" alt=""><figcaption></figcaption></figure>

In fact, you can double click or directly drag the program to open Hello World. Then you should see the Blocks code, shown below.<br>

<figure><img src="https://wiki.keyestudio.com/images/thumb/9/93/0397hello_5.png/500px-0397hello_5.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/3/36/0397hello_6.png/500px-0397hello_6.png" alt=""><figcaption></figcaption></figure>

After that, select the proper Board and Port. Upload the code to your EASY Plug control board.\
3\) Displaying Hello World\
Finally, upload the code successfully, open the monitor and set the baud rate to 9600, you should be able to see the Hello World is showed on the monitor. Congrats! You make it !

<figure><img src="https://wiki.keyestudio.com/images/thumb/5/5a/0397hello_7.png/500px-0397hello_7.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://wiki.keyestudio.com/images/thumb/c/c0/0397hello_8.png/500px-0397hello_8.png" alt=""><figcaption></figcaption></figure>

4\) Check Arduino Code\
What’ more, you can also click to check the Arduino code on the right side. Amazing! So powerful the Mixly blocks code is!

<figure><img src="https://wiki.keyestudio.com/images/thumb/f/f6/0397hello_9.png/500px-0397hello_9.png" alt=""><figcaption></figcaption></figure>

Is it more easy and simple to play the Mixly projects? Try your first Mixly blocks projects right now. Begin with the following projects to motivate your creations!
