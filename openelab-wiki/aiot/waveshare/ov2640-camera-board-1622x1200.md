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

{% hint style="info" %}
[**View Waveshare OV2640 Camera Board (1622x1200) on OpenELAB**](https://openelab.io/products/ov2640-camera-board)

**Store SKU / option:** `Waveshare-8532`. Match the purchased model and revision to the official reference below.
{% endhint %}

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

## Resolution scope

The [current manufacturer overview](https://www.waveshare.com/wiki/OV2640_Camera_Board) identifies a **2-megapixel** module. Sensor-array dimensions and a selected output frame are different quantities. Confirm both in the linked OV2640 datasheet before configuring capture buffers; the older array-size label is retained here and was not independently established by the overview.

## Official documentation and development resources

Use [Introduction](https://www.waveshare.com/wiki/OV2640_Camera_Board) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need     | Model-specific reference                                                                               |
| -------------------- | ------------------------------------------------------------------------------------------------------ |
| Electrical schematic | [Read electrical schematic](https://files.waveshare.com/upload/9/99/OV2640-Camera-Board-Schematic.pdf) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
