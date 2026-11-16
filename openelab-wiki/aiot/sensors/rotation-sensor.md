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

# Rotation Sensor

### Rotation Sensor

***

### Product Link

{% embed url="https://openelab.io/products/rotation-sensor?_pos=1&_sid=17bef05ab&_ss=r" %}

### Introduction

Principle: An incremental encoder is a rotary sensor that converts rotational displacement into a series of digital pulse signals. The number of pulses output during forward and reverse rotation can be counted by rotation. Unlike potentiometers, there is no limit to the number of rotations that can be counted. Together with the keypad on the rotary encoder, it can be reset to the initial state, i.e. counting from 0.

Uses: Solving positioning problems in industrial control

<figure><img src="../../.gitbook/assets/image (576).png" alt=""><figcaption></figcaption></figure>

### Specifications

* Pulses per lap: 20
* Power: 3.0V \~ 5.3V
* Dimension: 32.1mm \* 15.4mm
* Mounting holes size: 2.0mm

### Pinout

<figure><img src="../../.gitbook/assets/image (849).png" alt=""><figcaption></figcaption></figure>



### Dimensions

weight:15g&#x20;

deimension:32x15x15mm

### How to Use

In the case of working with a MCU:

* VCC ↔ 3.0V \~ 5.3V
* GND ↔ power supply ground
* SW ↔ MCU.IO (encoder button status)
* SIB ↔ MCU.IO (output status)
* SIA ↔ MCU.IO (output status)
