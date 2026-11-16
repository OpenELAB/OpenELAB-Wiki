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

# LCD Display 1602 I2C

### LCD Display 1602 I2C

***

### Product Link

{% embed url="https://openelab.io/products/lcddisplay1602?variant=43490562244806" %}

### Introduction

The module Matrix-I2C\_LCD1602 is used for LCD display, which consists of two parts: LCD1602, an LCD module, and PCF8574, a GPIO expansion module. LCD1602 is an LCD display that can show 16x2 characters, which itself is a parallel interface and requires more IO resources to communicate with it. PCF8574 can be extended out of 8 general-purpose GPIO pins, it can be communicated with the main control through I2C, the data information sent by the main control will be converted into parallel signals and then forwarded to the LCD1602, so as to realize the display of the LCD1602 and the backlight adjustment function, to achieve the purpose of saving IO resources and simplify the control.

<figure><img src="../../.gitbook/assets/image (772).png" alt=""><figcaption></figcaption></figure>

### Features

* I2C communication, display and backlight can be controlled&#x20;
* 2.54mm row pin interface, easy wiring, strong versatility&#x20;
* IIC module PCB size (mm): 16x42&#x20;
* LCD1602 PCB size (mm): 36x80

### Pinout

| name | descriptive     |
| ---- | --------------- |
| SDA  | I2C SDA         |
| SCL  | I2C SCL         |
| 5V   | Power supply 5V |
| GND  | GND             |

### Dimensions

<figure><img src="../../.gitbook/assets/image (771).png" alt=""><figcaption></figcaption></figure>

### How to Use

#### Preliminary

Make sure your Arduino board can download and run the programme properly, here we are using an Arduino uno board.

#### Hardware Connection

Make sure your Arduino board can download and run the programme properly, refer to: [https://www.arduino.cc/en/Guide/HomePage](https://www.arduino.cc/en/Guide/HomePage) Here we are using an Arduino uno board.\
[![matrix-i2c\_lcd1602\_arduino](https://wiki.friendlyelec.com/wiki/images/6/64/Matrix-i2c_lcd1602_arduino.jpg)](https://wiki.friendlyelec.com/wiki/index.php/File:Matrix-i2c_lcd1602_arduino.jpg)

#### Compile and run the test program

Since the arduino development board does not run Linux, the matrix for arduino code is managed by a separate repository:[git://github.com/friendlyarm/matrix-arduino.git](git://github.com/friendlyarm/matrix-arduino.git)Clone matrix-arduino code repository

```
$ git clone git://github.com/friendlyarm/matrix-arduino.git
```

When the cloning is complete you will get a matrix-arduino directory that holds all the code that the Matrix accessory uses to support arduino. Copy the matrix-i2c\_lcd1602 directory to the libraries directory of the Arduino IDE.

```
$ cd matrix-arduino
$ cp matrix-i2c_lcd1602 Arduino_IDE/libraies -r
```

Start Arduino IDE Click File->Examples->matrix-i2c\_lcd1602->displaychar to open the test program. Click upload to run the test program.

#### Code Showcase

```
#include <Wire.h> 
#include <LiquidCrystal_I2C.h>
 
// set the LCD address to 0x27 for a 16 chars and 2 line display
LiquidCrystal_I2C lcd(0x27,16,2);  
 
void setup()
{
  lcd.init();                        
  lcd.backlight();
  lcd.setCursor(2, 0);
  lcd.print("B&G Char LCD"); 
  lcd.setCursor(0, 1);
  lcd.println("--by FriendlyARM");
}
 
void loop()
{ }
```
