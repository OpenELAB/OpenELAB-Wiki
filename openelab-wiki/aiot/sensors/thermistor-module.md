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

# Thermistor Module

### Thermistor Module

***

### Product Link

{% embed url="https://openelab.io/products/thermistor-module?_pos=1&_sid=e323377f4&_ss=r" %}

### Introduction

Through the adjustment of the potentiometer, you can change the temperature detection threshold , such as the need to control the ambient temperature of 50 degrees, the module is adjusted to the corresponding ambient temperature of the green light, DO is output low level, lower than the set temperature value, the output of the high level, the green light does not light; module digital output D0 can be directly connected to the MCU, through the MCU to detect the high level, and thus detect The module digital output D0 can be directly connected to the microcontroller, through the microcontroller to detect the high and low levels, so as to detect the temperature change of the environment; small board digital output DO can be directly driven by the relay module, which can be composed of a temperature control switch, control the working temperature of the relevant equipment, can also be connected to the fan used to dissipate the heat and so on; small board analog output AO can be connected to the AD module, through the AD converter, the ambient temperature can be obtained by a more accurate value. This module can also be replaced by a temperature sensor with a wire, for water temperature, water tank control. Connect VCC and GND, the module power indicator will be on, place the module on the desktop, adjust the blue potentiometer on the board until the board switching indicator is on, then adjust it back a little bit so that the switching indicator is off, and then find a way to make the temperature of the thermistor rise, at this time the module switching indicator will be on. If the temperature of the thermistor is lowered again, the switching indicator will come back to the off state. This phenomenon suggests that the ambient temperature can trigger the module to light up the switching indicator.



<figure><img src="../../.gitbook/assets/image (560).png" alt=""><figcaption></figcaption></figure>

### Features

* Using the NTC thermistor sensor , good sensitivity
* The comparator output signal clean waveform is good , driving ability, than 15mA.
* &#x20;Adjust the temperature distribution bit detection threshold&#x20;
* Working voltage 3.3V-5V&#x20;
* The output format : Digital switching output (0 and 1)&#x20;
* With bolt holes for easy installation&#x20;
* A small board PCB size : 3.2cm x 1.4cm
* Using a wide voltage LM393 comparator

### Pinout

* VCC:3.3V-5V
* DO:0/1
* AO:Analog Output Interface
* GND:Ground

### Dimensions

PCB dimensions: 32mm x 14mm
