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

{% hint style="info" %}
[**View Waveshare Rotation Sensor | Encoder | Push Button on OpenELAB**](https://openelab.io/products/rotation-sensor)

**Store SKU / option:** `Waveshare-9533`. Match the purchased model and revision to the official reference below.
{% endhint %}

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

weight:15g

deimension:32x15x15mm

### How to Use

In the case of working with a MCU:

* VCC ↔ 3.0V \~ 5.3V
* GND ↔ power supply ground
* SW ↔ MCU.IO (encoder button status)
* SIB ↔ MCU.IO (output status)
* SIA ↔ MCU.IO (output status)

## Official documentation and development resources

Use [Overview](https://www.waveshare.com/wiki/Rotation_Sensor) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need                             | Model-specific reference                                                                                        |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Official source: Pico\_MircoPython\_Examples | [Read official source: pico\_mircopython\_examples](https://github.com/waveshareteam/Pico_MircoPython_Examples) |
| Electrical schematic                         | [Read electrical schematic](https://files.waveshare.com/upload/2/25/Rotation-Sensor-Schematic.pdf)              |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
