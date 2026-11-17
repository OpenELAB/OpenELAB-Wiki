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

# Waveshare 1.8inch colorful display module for micro:bit

### Waveshare 1.8inch colorful display module for micro:bit

***

### Product Link

{% embed url="https://openelab.io/products/waveshare-colorful-display-module-bit" %}

### Introduction

This is a colorful display module designed for the BBC micro: bit, 1.8inch diagonal, 160 x 128 pixels, capable of displaying 65K colors.

Tired of the 5 x 5 LED matrix? Time to get a tiny monitor for your micro: bit, this one would be the ideal choice.

### Feature

* micro:bit edge connector, directly pluggable
* Embedded driver ST7735S, supports 65K colors
* Onboard SRAM 23LC1024, used as display cache, no more out of memory
* SPI interface, takes up only a few IO pins
* Backlight adjustment via PWM
* Reserved solder pads for control interface, make it easy to connect with Arduino/Nucleo boards
* Comes with development resources (micro:bit graphical demo/user manual, etc.)

### Specification

* Driver: ST7735S
* Resolution: 160 x 128
* Display color: RGB, 65K colors
* Operating voltage: 3.3V
* Dimension: 61mm x 51.5mm

### Pinouts

<table><thead><tr><th width="137">PIN</th><th width="244">micro:bit PIN</th><th>Description</th></tr></thead><tbody><tr><td>Vcc</td><td>3V3</td><td>Power</td></tr><tr><td>GND</td><td>GND</td><td>Ground</td></tr><tr><td>MISO</td><td>P14</td><td>SPI data master input/slave output</td></tr><tr><td>MOSI</td><td>P15</td><td>SPI data master output/slave input</td></tr><tr><td>SCK</td><td>P13</td><td>SPI clock input</td></tr><tr><td>LCD_CS</td><td>P16</td><td>LCD chip selection</td></tr><tr><td>RAM_CS</td><td>P2</td><td>SRAM chip selection</td></tr><tr><td>DC</td><td>P12</td><td>LCD data/command</td></tr><tr><td>RST</td><td>P8</td><td>LCD reset</td></tr><tr><td>BL</td><td>P1</td><td>LCD backlight</td></tr></tbody></table>

### Programming Guide

Micor:bit has variety of programming methods like mbed, micropython, typescript and other programming methods, as well as code online websites which are abundant.

The official recommendation are two programming methods: typescript and micropython. Typescript is the graphical programming language.

Note:For this LCD, we only provide demo code of typescript

#### Typescript

Typescript is a kind of graphical programming, its website is that: [https://makecode.microbit.org/#](https://makecode.microbit.org)

* Open a browser and input the next URL

<figure><img src="https://www.waveshare.com/w/upload/5/59/Open_make.gif" alt=""><figcaption></figcaption></figure>

* Create a new empty project

Click Project->New Project to create an empty project. Rename the project as LCD or any one you like to.

<figure><img src="https://www.waveshare.com/w/upload/2/2d/1_Createnewproject_LCD.gif" alt=""><figcaption></figcaption></figure>

* Add Packeage

You can get the package of 1.8inch LCD for micro;bit from github. Click More..->Add Package, then copy the URL to the Edittext.

If you have the old Micro bit

[https://github.com/waveshare/WSLCD1in8](https://github.com/waveshare/WSLCD1in8)

If you have the Micro bit V2

[https://github.com/waveshare/PXT-WSLCD1in8](https://github.com/waveshare/PXT-WSLCD1in8)

Note: add a space follow the address

<figure><img src="https://www.waveshare.com/w/upload/7/7b/2_getgithubpackage_LCD.gif" alt=""><figcaption></figcaption></figure>

#### The Blocks

* Initiation

You need to initial LCD module first.

<figure><img src="https://www.waveshare.com/w/upload/f/f9/3_initiallcd_LCD.gif" alt=""><figcaption></figcaption></figure>

* Clear the screen

Clear the screen to white. Create an buffer on RAM with the resolution size 160\*128 and initial it to white.

<figure><img src="https://www.waveshare.com/w/upload/6/6f/4_clearlcdtowhite_LCD.gif" alt=""><figcaption></figcaption></figure>

* Set the backlight

<figure><img src="https://www.waveshare.com/w/upload/8/86/5_Setbacklight_LCD.gif" alt=""><figcaption></figcaption></figure>

* Send display data

With this block, it will send one frame of buffer to the LCD and display. Note: it is always following drawing operation

<figure><img src="https://www.waveshare.com/w/upload/5/5d/6_senddisplaydata_LCD.gif" alt=""><figcaption></figcaption></figure>

* Draw point

<figure><img src="https://www.waveshare.com/w/upload/c/c4/7_drwapoint_LCD.gif" alt=""><figcaption></figcaption></figure>

Place the block before send display data. You can choose the position, color and size. For the screen, (1,1) is on top-left, and (160,128) is on bottom-right

There are tow way to set the color, the one is use the color block as above, another is to set the value (RGB565) by drag the slider.

* Draw line

You can choose the the line's position, color, size and its sytle

solid line:

<figure><img src="https://www.waveshare.com/w/upload/a/a2/8_drawsolidline_LCD.gif" alt=""><figcaption></figcaption></figure>

dotted line: just need to change the Style

<figure><img src="https://www.waveshare.com/w/upload/8/89/9_drawdottedline_LCD.gif" alt=""><figcaption></figcaption></figure>

* Draw frame

Draw empty rectange:

<figure><img src="https://www.waveshare.com/w/upload/9/95/10_drawemptyrectange_LCD.gif" alt=""><figcaption></figcaption></figure>

Draw full rectange:

<figure><img src="https://www.waveshare.com/w/upload/9/94/11_drawfullrectange_LCD.gif" alt=""><figcaption></figcaption></figure>

* Draw circle

Draw empty circle:

<figure><img src="https://www.waveshare.com/w/upload/3/37/12_drawemptycircle_LCD.gif" alt=""><figcaption></figcaption></figure>

Draw full circle:

<figure><img src="https://www.waveshare.com/w/upload/b/b6/13_drawfullcircle_LCD.gif" alt=""><figcaption></figcaption></figure>

* Draw string

<figure><img src="https://www.waveshare.com/w/upload/4/4a/14_drawstring_LCD.gif" alt=""><figcaption></figcaption></figure>

* Partial refresh

You can set display windows and refresh it on LCD instead of full refresh

Initialize LCD, set the backlight and then draw a rectangle from (30, 30) to (80, 80)

<figure><img src="https://www.waveshare.com/w/upload/1/15/Partial-refresh.gif" alt=""><figcaption></figcaption></figure>

Then set the display windows block and set its position

<figure><img src="https://www.waveshare.com/w/upload/1/1b/14_drawstring_LCD_2.gif" alt=""><figcaption></figcaption></figure>

### Resources

#### Document

* [Schematic](https://files.waveshare.com/upload/e/ea/1.8inch_LCD_for_microbit_Schematic.pdf)

#### Programs

* [Sample Program](https://files.waveshare.com/upload/0/0c/1.8inch_LCD_for_microbit_Code.7z)

#### Datasheet

* [23LC1024](https://files.waveshare.com/upload/8/89/23LC1024.pdf)
* [ST7735S](https://files.waveshare.com/upload/e/e2/ST7735S_V1.1_20111121.pdf)

#### Software

* [Zimo221.7z](https://files.waveshare.com/upload/c/c6/Zimo221.7z)
* [Image2Lcd.7z](https://files.waveshare.com/upload/3/36/Image2Lcd.7z)
* [makecode website](https://makecode.microbit.org/v0)
* [Image\_Extraction](https://www.waveshare.com/wiki/Image_Extraction)

#### Certification information

* [CE RoHS](https://files.waveshare.com/upload/c/ca/1.8inch_LCD_for_microbit_certification.rar)

### FAQ

<details>

<summary><a href="https://www.waveshare.com/wiki/1.8inch_LCD_for_micro:bit#accordion1"><strong>Can the screen refresh the picture?</strong></a></summary>

You cannot refresh the picture, but only write data to the display.

</details>
