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

# OV2640 Camera Board (1622x1200)

### OV2640 Camera Board (1622x1200)

***

### Product Link

{% embed url="https://openelab.io/products/ov2640-camera-board" %}

### Introduction

The OV2640 is the world’s first 1/4 inch 2 megapixel sensor. It’s a fully integrated CameraChip™ built on OmniVision’s latest 2.2 micron OmniPixel2™ architecture and can be assembled in the very popular 8 x 8 mm sockets with a building height as low as 5 mm, essentially thinner than today’s 1.3 megapixel camera modules. This optimal sensor size, coupled with an embedded compression engine, allows customers to use the same camera interface bandwidth as they have used with their 1.3 mega pixel sensors, making it very easy to upgrade their current platforms to the OV2640’s 2 megapixel solution without hardware or mechanical changes.

<figure><img src="../../.gitbook/assets/image (565).png" alt=""><figcaption></figcaption></figure>

### Features

* 2 Megapixel
* Array size: UXGA 1622X1200
* Power supply: 3.3V
* IO voltage level: 1.7V\~3.3V DC
* Output formats:
  * YUV(422/420)/YCnCr422
  * RGB565/555
  * 8-bit compressed data
* Max image transfer rate:
  * UXGA/SXGA 15fps
  * UXGA/SXGA 30fps
  * SVGA 30fps
  * CIF 60fps

### Dimensions

<figure><img src="../../.gitbook/assets/image (566).png" alt=""><figcaption></figcaption></figure>

### brochure

* [OV2640](https://www.waveshare.net/w/upload/a/af/OV2640.pdf)
* [OV2640\_DS](https://www.waveshare.net/w/upload/6/6b/OV2640_DS\(1.6\).pdf)

### FAQ

<details>

<summary><strong>该模块的视场角是多少？</strong></summary>

约65度

</details>

<details>

<summary><strong>通过杜邦线飞线到STM32等设备时不能使用？</strong></summary>

1、请确认接线准确无误

2、请确认杜邦线都能导通

3、杜邦线尽量短，建议10cm以内（OV2340没有板载晶振，用的是主控给的时钟信号）

</details>
