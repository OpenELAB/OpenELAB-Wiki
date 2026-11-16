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

# 3D MKS Gen V1.4 Printer

### 3D MKS Gen V1.4 Printer Motherboard Control Board

### Product Link

{% embed url="https://openelab.io/products/3d-mks-gen-printer-motherboard?srsltid=AfmBOoqTn-lZb_EY9tjQ9mN7q2fdhXahLGNbObAlbjq0MHOARUwfzbDx" %}

### Intruduction

OpenELAB 3D MKS Gen V1.4 printer motherboard control board combines and improves the assets solutionof the RAMPS 1.4 and Arduino Mega 2560 board on a fantastic single board.\
OpenELAB 3D MKS Gen V1.4 printer motherboard control board is an optimal 3D printer controller solution for your Reprap 3D printer.

### Features

* Integrate 2560 and ramps1.4 in a board, to solve thecomplicated interfaces and broken problem of Ramps1.4 combination.
* Replaceable motor driver, support 4988 driver and 8825 driver.
* Circuit board using high-quality 4-layer board, and specially dealing with thermal optimization; ramps is a 2-layer board.
* Using high-quality MOSFET tube, with better heat dissipation.
* Using a dedicated power chip to support 12V-24V power input, to solve the problem of Ramps voltage converted into chip heating.
* To accept 24V input, hot bed current can be reduced to 1/4 under the same system power, effectively solve the heating problem of hot bed MOS tube.
* Firmware can use open-source firmware Marlin, and its configuration is exactly the same as ramps1.4, which can directly replace Ramps1.4.
* Can directly connect to Ramps1.4,2004LCD control board and 12864LCD control board.
* Set aside the motor pulse and direction output port, convenient to facilitate external high current to connect external high current (such as 2A, 5A) motor drive circuit.
* Reserve the Servos, AUX-1, AUX-2 interfaces on Ramps1.4, providing three 5V output, three 12V output interface.
* This board is an upgrade part of the MKS Gen V1.2 board, improving the performance of power protection and USB communication stability.

### Interface Explanation

<figure><img src="https://wiki.keyestudio.com/images/thumb/0/0b/Ks0282-1.png/700px-Ks0282-1.png" alt=""><figcaption></figcaption></figure>

### Shipping List

* OpenELAB MKS BaseV1.4 3D Printer Controller Board<br>
* USB Cable

<figure><img src="https://wiki.keyestudio.com/images/9/98/Ks0282-2.png" alt=""><figcaption></figcaption></figure>

### Using Method

#### Install Diver Software

* Connect the main board with computer, and then right click “Computer” to enter “Device Manage”

{% embed url="https://wiki.keyestudio.com/images/1/14/Ks0089_5-1.png?20170526030007" %}

* Double click “Other devices”, appearing “USB Serial Port”.

{% embed url="https://wiki.keyestudio.com/images/1/11/Ks0089_5-2.png" %}

* Then, right click “USB Serial Port” and select “Update Driver Software” to install driver software.

{% embed url="https://wiki.keyestudio.com/images/7/73/Ks0089_5-3.png" %}

* After that, select “Browse my computer for driver software” to find the file.

{% embed url="https://wiki.keyestudio.com/images/e/e7/Ks0089_5-4.png" %}

* Browse to search for driver software.

{% embed url="https://wiki.keyestudio.com/images/7/71/Ks0089_5-5.png" %}

* After your driver software updated, click “Close” to finish.

{% embed url="https://wiki.keyestudio.com/images/4/4d/Ks0089_5-6.png" %}

* Finally, installation is done, and double click “Ports”in “Device Manager”, you can see “USB Serial Port”.

{% embed url="https://wiki.keyestudio.com/images/8/8c/Ks0089_5-7.png" %}

<br>

#### Install development environment software IDE

* Double click arduino-1.5.6-r2-windows to start.
* Select “I Agree”to accept license agreement.

{% embed url="https://wiki.keyestudio.com/images/3/34/Ks0089_5-8.png" %}

* Select components to install and click “Next”.

{% embed url="https://wiki.keyestudio.com/images/6/62/Ks0089_5-9.png" %}

* Click “Browse” and select another folder. Click “Install” to start the installation.

{% embed url="https://wiki.keyestudio.com/images/e/e2/Ks0089_5-10.png" %}

* Finally, wait for a few minutes to finish.

{% embed url="https://wiki.keyestudio.com/images/6/6f/Ks0089_5-11.png" %}

#### Install Firmware for Main Board

* You must close Arduino IDE firstly, and then place three libraries LiquidCrystal, SPI and U8glib from Marlin\_Marlin\_v1 → ArduinoAddons → Arduino\_1.x.x → libraries into Arduino/libraries.

{% embed url="https://wiki.keyestudio.com/images/d/d9/Ks0089_5-12.png" %}

* Enter Marlin\_Marlin\_RAMPS\_2004\_Ver1 this folder, double click Marlin\_Marlin\_RAMPS\_2004\_Ver1.ino this file, finally click “Tools” to set “Board”and “Port”.

{% embed url="https://wiki.keyestudio.com/images/5/5b/Ks0089_5-13.png" %}

{% embed url="https://wiki.keyestudio.com/images/3/3e/Ks0089_5-14.png" %}

* After verifying, write code.

{% embed url="https://wiki.keyestudio.com/images/a/ae/Ks0089_5-15.png" %}

* Done uploading.

{% embed url="https://wiki.keyestudio.com/images/c/ce/Ks0089_5-16.png" %}

* After upload the firmware the LCD will display some parameter as shown below:

{% embed url="https://wiki.keyestudio.com/images/6/66/Ks0089_5-17.png" %}

#### Install Slicer Software Repetier-Host

* First, run this application\
  [![thumb](https://wiki.keyestudio.com/images/f/fc/Ks0089_5-18.png)](https://wiki.keyestudio.com/File:Ks0089_5-18.png)<br>

{% embed url="https://wiki.keyestudio.com/images/1/18/Ks0089_5-19.png" %}

* Click “Next” to continue.

{% embed url="https://wiki.keyestudio.com/images/5/5d/Ks0089_5-20.png" %}

* Check “I accept the agreement”, and click “Next” to continue.

{% embed url="https://wiki.keyestudio.com/images/8/8b/Ks0089_5-21.png" %}

* Select destination location, and click “Next” to continue.

{% embed url="https://wiki.keyestudio.com/images/5/55/Ks0089_5-22.png" %}

* Check components that should be installed, and click “Next” to continue.

{% embed url="https://wiki.keyestudio.com/images/1/1c/Ks0089_5-23.png" %}

* Select star menu folder, and click “Next” to continue.

{% embed url="https://wiki.keyestudio.com/images/5/5d/Ks0089_5-24.png" %}

* Click “Next” to continue.

{% embed url="https://wiki.keyestudio.com/images/c/c7/Ks0089_5-25.png" %}

* Click “Install” to install.

{% embed url="https://wiki.keyestudio.com/images/b/bc/Ks0089_5-26.png" %}

{% embed url="https://wiki.keyestudio.com/images/2/23/Ks0089_5-27.png" %}

* Click “Finish” to exit Setup.

{% embed url="https://wiki.keyestudio.com/images/8/85/Ks0089_5-28.png" %}

### Application of Slicer Software

* a. Run Repiter-Host,click Load to open a printing model.

{% embed url="https://wiki.keyestudio.com/images/6/63/Ks0089_6-1.png" %}

* b. Click Printer Settings to complete some setup, referring to below figure.

{% embed url="https://wiki.keyestudio.com/images/a/a8/Ks0089_6-2.png" %}

* c. Enter Object Placement to set placing position, printing size and so on.

{% embed url="https://wiki.keyestudio.com/images/3/31/Ks0089_6-3.png" %}

* d. Click Slicer to set slicer, like printing speed. After setting slicer, click Start Slicing to begin slicing.

{% embed url="https://wiki.keyestudio.com/images/3/35/Ks0089_6-4.png" %}

* e. After slicing, go to Preview→G-Code Editor, copy G-Code to SD card, and then insert the card into the main board. It is time to kick off the print! Though the LCD screen go to: Print from SD→Desired File. Or you can connect your 3D printer to computer using a USB cable to start the print.

{% embed url="https://wiki.keyestudio.com/images/9/97/Ks0089_6-5.png" %}

* f. Click “Connect”and then click “Start Print” to begin the print. After some time, your printer gets ready and the buzzer rings, then you should press the button on LCD to start.

{% embed url="https://wiki.keyestudio.com/images/0/04/Ks0089_6-6.png" %}

* g. We just introduce a simple method about printing. Thanks to selling only main board by us, you should design your own structure and outlook of your 3D printer, and you should also set your own configuration to meet your need. After you assembling your printer, the printer need to be leveled, so you can make some setup in Preview and Manual Control, and surf the internet for further information.

{% embed url="https://wiki.keyestudio.com/images/2/27/Ks0089_6-7.png" %}

* h. We have a G-Code to test the main board. Power it on, open limit switch and stepper motor, drive three motors; put a Fnbduino.gco file to Preview, click Start Print, if the motors rotate, X/Y/Z value in Manual Control changes, the main board works as shown below:

{% embed url="https://wiki.keyestudio.com/images/4/41/Ks0089_6-8.png" %}

<br>
