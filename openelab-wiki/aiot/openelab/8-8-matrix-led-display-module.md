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

# 8\*8 Matrix LED Display Module

### 8\*8 Matrix LED Display Module

***

### Product Link

{% embed url="https://openelab.io/products/88matrixleddisplaymodule?_pos=1&_sid=44a9d2124&_ss=r" %}

### Introduction

8\*8 LED RGB Matrix is a tri-colour multi-colour LED display matrix module that can be arbitrarily cascaded in XY axis, which can be used for displaying pictures and text, and supports multi-layers and various panning effects of each layer.

Theoretically, it supports any cascade of up to 4096 modules in X-axis horizontal and 4096 modules in Y-axis vertical, without hardware design. Of course, if you want to cascade them into a large matrix display, then you need a high-speed controller and a high-power power supply.

In practice, the number of cascades depends on the data storage space of your MCU and the maximum current allowed through the modules.

<figure><img src="../../.gitbook/assets/image (784).png" alt=""><figcaption></figcaption></figure>

### Features

* Operating power: +5V to +5.3V
* Operating current: Maximum 300mA (single)
* Allowable pass-through current: Maximum 2000mA
* Operating temperature range: -10℃～＋50℃
* Support multiple arbitrary cascade, no need to set up hardware.
* Support RGB three single-color display and mixed-color display.
* Dot matrix sequence adopts plane right-angle coordinate system, easy to understand.
* Support arduino development board power supply or external independent power supply.
* Support hardware SPI mode and software SPI mode. Software SPI mode can be directly plugged into Interface Shield's Shiftout interface.
* Software SPI supports up to &#x32;_&#x32; or &#x31;_&#x35;, hardware SPI supports more than 10.
* When multiple cascades are used, if the color is too dark, the power supply voltage can be increased to about 5.2V, not more than 5.4V.
* When multiple cascades are used, the data line is always connected to the No.1 daughter board (the daughter board where the origin (0,0) is located is the No.1 daughter board).

### Pinout

<figure><img src="../../.gitbook/assets/image (779).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (780).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (782).png" alt=""><figcaption></figcaption></figure>

### How to Use

This 8×8 LED Matrix Library module will be interfaced with Arduino for displaying alphabets, characters & logos. First, we need to download a library specifically designed for LED MATRIX.

[8×8 LED Matrix Library](https://github.com/shaai/Arduino_LED_matrix_sketch/archive/master.zip)

After downloading the Zip file, extract the content. Put the folder in library folder inside Libraries –>>>— Arduino –>>>>>–Document

{% embed url="https://how2electronics.com/wp-content/uploads/2020/01/1-min.gif" %}

```
#include "LedControlMS.h"
 
 //pin 12 is connected to the DataIn
// pin 11 is connected to the CLK
 //pin 10 is connected to LOAD
 
#define NBR_MTX 1 //number of matrices attached is one
LedControl lc=LedControl(12,11, 10, NBR_MTX);//
 
void setup()
{
  for (int i=0; i< NBR_MTX; i++)
  {
    lc.shutdown(i,false);
  /* Set the brightness to a medium values */
    lc.setIntensity(i,8);
  /* and clear the display */
    lc.clearDisplay(i);
                delay(500);
  }
}
 
void loop()
 
{
     lc.writeString(0,"HOW2ELECTRONICS");//sending characters to display
     lc.clearAll();//clearing the display
     delay(1000);
}
```
