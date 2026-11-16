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

# Shock Sensor Module

### Shock Sensor Module

***

### Product Link

{% embed url="https://openelab.io/products/shock-sensor-module?_pos=1&_sid=fe251ddc5&_ss=r" %}

### Introduction

Used for all kinds of vibration triggering effect, burglar alarm, intelligent car, electronic building blocks and so on. Please note that this module in the sense of a small vibration trigger time will be very short, not enough to drive the relay, some people's information shows that can be directly connected to the relay module, the actual use of the effect is not good, we do not want to mislead the majority of consumers, if you need to vibrate and trigger the relay, please buy the module with a time delay function!

<figure><img src="../../.gitbook/assets/image (559).png" alt=""><figcaption></figcaption></figure>

### Features

* Adopt the high sensitivity vibration switch produced by our company, default with SW-18010P vibration sensor.&#x20;
* Comparator output, clean signal, good waveform, strong driving ability, more than 15mA.&#x20;
* Operating voltage 3.3V-5V&#x20;
* Output form: digital switch output (0 and 1)
* with fixed bolt holes, easy to install&#x20;
* small board PCB size: 3.2cm × 1.4cm&#x20;
* the use of wide voltage LM393 comparator

### Pinout

* VCC:3.3V-5V
* DO:0/1
* AO:Analog Output Interface
* GND:Ground

### Dimensions

dimension:32x14(mm)

### How to Use

1. When the product is not vibrating, the vibration switch is disconnected, the output terminal outputs high level, and the green indicator does not light up. The green indicator does not light up.&#x20;
2. When the product is vibrating, the vibration switch is on momentarily, the output terminal outputs low level, and the green indicator light is on. green indicator light.
3. Output can be directly connected to the microcontroller, through the microcontroller to detect the high and low levels, so as to detect whether there is vibration in the environment. The output can be directly connected to the microcontroller to detect the high and low levels through the microcontroller to detect whether there is vibration in the environment and play an alarm role.
