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

# Mateksys GNSS M9N-5883

### Mateksys GNSS M9N-5883

***

### Product Link

{% embed url="https://openelab.io/products/mateksys-gnss-m9n" %}

### Introduction

The Matek M9N-5883 is multi-constellation GPS module with integrated compass (QMC5883L). The GPS is the [u-blox NEO-M9N](https://www.u-blox.com/en/product/neo-m9n-module) which supporst simultaneous reception of four GNSS (GPS, GLONASS, Galileo, Beidou). It offers exceptional sensitivity and acquisition time for all GNSS L1 signals. Its built-in patch antenna provides the best balance between performance and small size. It offers great RF sensitivity and can improve the dynamic position accuracy even in non-line-of-sight scenarios.

<figure><img src="../../.gitbook/assets/image (608).png" alt=""><figcaption></figcaption></figure>

### Specifications

* GNSS NEO-M9N (GPS, GLONASS, Galileo and BeiDou)
* Magnetic Compass QMC5883L
* Patch antenna 25\*25\*4mm
* Input voltage range: 4\~5.5V (5V pad/pin)
* Power consumption: 50mA
* UART baudrate: 38400 default
* Operating Temperatures: -20\~80 °C
* UART(TX, RX) interface for GNSS NEO-M9N
* I2C(DA, CL) interface for Compass QMC5883L
* JST-GH-6P connector
* 3.3V Power LED, Red
* GNSS PPS LED, Green, blinking(1Hz) when GNSS has 3D fixed
* 32mm\*32mm\*10mm
* 14.5g

### Pinout

<figure><img src="../../.gitbook/assets/image (607).png" alt=""><figcaption></figcaption></figure>

* 5V to Flight controller 4\~5.5V
* RX to Flight controller UART\_TX
* TX to Flight controller UART\_RX
* CL to Flight controller I2C\_SCL
* DA to Flight controller I2C\_SDA
* G  to Flight controller GND

### Dimensions

<figure><img src="../../.gitbook/assets/image (606).png" alt=""><figcaption></figcaption></figure>
