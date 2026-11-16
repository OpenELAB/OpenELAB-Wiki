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

# M5Stack GRBL Module Stepmotor Driver

### M5Stack GRBL Module 13.2 Stepmotor Driver

***

### Product Link

{% embed url="https://openelab.io/products/grbl-module-stepmotor-driver" %}

### Description <a href="#description" id="description"></a>

**GRBL 13.2** is a three-axis stepper motor driver module in the M5Stack stacking module series. It uses an ATmega328P-AU controller with three sets of DRV8825PWPR stepper motor driver chip control ways, which can drive three bipolar steppers at the same time.

Using the I2C communication interface (default address:0x70) and integrated DIP switch for adjusting motor step subdivision (maximum support of 1/32 step subdivision) and I2C address adjustment (support dual address adjustment 0x70, 0x71), You can achieve six-axis control by stacking two **GRBL 13.2** modules.

The power input interface is DC/9-24V, the motor drive current can reach 1.5A, and three sets of limit switch signal interfaces are open, which can be used to connect an external limit switch (active low) to realize the motor braking function. Suitable for a variety of stepping motor motion control scenarios, such as printers, robotic arms, etc.

### Features <a href="#features" id="features"></a>

* ATmega328P-AU controller
* Three-axis DRV8825PWPR stepper motor driver
* Drive current up to 1.5A
* Drive bipolar stepper motor
* Maximum 1/32 mode STEP subdivision
* Limit switch interface (active low)

### Applications <a href="#applications" id="applications"></a>

* Printer
* scanner
* Office automation machine
* Factory automation
* robot technology

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                               | Parameter          |
| --------------------------------------- | ------------------ |
| Motor driver chip                       | DRV8825PWPR        |
| Controller chip                         | ATmega328P-AU      |
| Maximum drive current of single channel | 1.5A               |
| Support maximum step subdivision        | 1/32               |
| Interface                               | XT2.54-4P          |
| Net weight                              | 22.5g              |
| Gross weight                            | 42.3g              |
| Product size                            | 54.2\*54.2\*13.2mm |
| Package size                            | 95\*65\*25mm       |

### Related Link <a href="#related-link" id="related-link"></a>

* [DRV8825 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/DRV8825_en.pdf)
* [GRBL-Firmware](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/GRBL13.2-Module-Arduino-Library.zip)
* [GRBL v0.8-Configuration reference document](https://github.com/grbl/grbl/wiki/Configuring-Grbl-v0.8)

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE A) | GPIO21 | GPIO22 | 5V  | GND |
| --------------- | ------ | ------ | --- | --- |
| GRBL 13.2       | SDA    | SCL    | VCC | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/grbl13.2/grbl13.2_sch_01.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (963).png" alt=""><figcaption></figcaption></figure>

### Step subdivision adjustment <a href="#step-subdivision-adjustment" id="step-subdivision-adjustment"></a>

| MODE2 | MODE1 | MODE0 | STEP MODE                                       |
| ----- | ----- | ----- | ----------------------------------------------- |
| 0     | 0     | 0     | Full step (2-phase excitation) with 71% current |
| 0     | 0     | 1     | 1/2 step (1-2 phase excitation)                 |
| 0     | 1     | 0     | 1/4 step (W1-2 phase excitation)                |
| 0     | 1     | 1     | 1/8 step                                        |
| 1     | 0     | 0     | 1/16 step                                       |
| 1     | 0     | 1     | 1/32 step                                       |
| 1     | 1     | 0     | 1/32 step                                       |
| 1     | 1     | 1     | 1/32 step                                       |

### I2C address adjustment <a href="#i2c-address-adjustment" id="i2c-address-adjustment"></a>

| Switch | Address |
| ------ | ------- |
| 0      | 0x70    |
| 1      | 0x71    |
