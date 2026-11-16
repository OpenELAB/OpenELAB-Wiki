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

# M5Stack 8-Angle Unit with Potentiometer

### M5Stack 8-Angle Unit with Potentiometer

***

### Product Link

{% embed url="https://openelab.io/products/8-angle-unit" %}

### Introduction

8Angle unit is an input unit that combines eight adjustable potentiometers to provide precise control functionality. It utilizes an internal STM32F030 microcomputer as the acquisition and communication processor, enabling efficient data processing and communication. The unit communicates with the host computer using the I2C communication interface, ensuring seamless integration into various systems.

Each adjustable potentiometer is accompanied by a corresponding RGB LED light, allowing for visual feedback and state indication. The unit also includes a physical toggle switch and its corresponding RGB LED light, providing an additional input method.

To ensure proper functionality, the UNIT 8Angle incorporates a 5V to 3.3V DCDC circuit, allowing for reliable power supply and compatibility with different systems. With this unit, users can input multi-channel absolute control values, with each corresponding RGB lamp displaying different states. The toggle switch enables multi-channel switching input, further enhancing the control capabilities.

8Angle unit finds applications in various fields, such as multi-degree-of-freedom robots or music equalization systems. Its adjustable potentiometers provide precise and granular control, allowing users to fine-tune parameters or settings. The visual feedback from the RGB LED lights enhances the user experience and enables quick recognition of different states. Whether it's controlling robot joints or adjusting music equalization parameters, the UNIT 8Angle unit offers a versatile and intuitive input solution.



<figure><img src="../../.gitbook/assets/image (521).png" alt=""><figcaption></figcaption></figure>

### Features

* 8-channel adjustable potentiometer
* 8 channels correspond to RGB lights
* I2C communication
* Toggle switches can be used for multi-channel switching inputs

### Specifications

| Resources                 | Parameters             |
| ------------------------- | ---------------------- |
| MCU                       | STM32F030F4P6          |
| LDO                       | ME6210A33M3G           |
| RGB                       | SK6812-3535            |
| Input voltage             | 5v                     |
| I2C communication address | 0x43                   |
| Product Size              | 128mm × 24mm ×22.7mm   |
| Package Size              | 130mm × 27.7mm ×27.7mm |
| Product Weight            | 34.9g                  |
| Package Weight            | 44.3g                  |

### Pinout

<figure><img src="../../.gitbook/assets/image (504).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (505).png" alt=""><figcaption></figcaption></figure>

### How to Use

* [Arduino Example](https://github.com/m5stack/M5Unit-8Angle)

<figure><img src="../../.gitbook/assets/image (507).png" alt=""><figcaption></figcaption></figure>
