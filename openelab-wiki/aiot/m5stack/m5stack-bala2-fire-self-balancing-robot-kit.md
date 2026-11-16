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

# M5Stack BALA2 Fire Self-balancing Robot Kit

### M5Stack BALA2 Fire Self-balancing Robot Kit

***

### Product Link

{% embed url="https://openelab.io/products/self-balancing-robot-kit" %}

### Description <a href="#description" id="description"></a>

**BALA2Fire** is short for 'Balance', as its name suggests, it is the second generation of M5Stack balancing robot series. **BALA2Fire** is a Self Balancing Robot consisting of M5Stack Fire and two wheels(DC motors).The base uses STM32F030C8T6 as the main control and has a two-way encoding motor driver and built-in 1200mAh battery.

This robotics product comes with preloaded software. A self-balancing robot application which balances the robot vertically using a closed-loop algorithm. You can program it to automatically move around through programming, or you can combine Wi-Fi to develop remote control functions.

This Robot is controllable by a Smartphone device or a Transmitter. The BALA2 base contains a wealth of interfaces. In addition to the conventional PortB and PortC, it also supports 8-channel servos, of which 4 channels can be directly connected, and the remaining 4 channels need to be connected from the inside of the base. Even if you have never attempted such a balancing robot program, you can quickly get the hang of it and control it through UIFlow. The self balancing robot uses data from the Accelerometer and Gyroscope to correct its orientation and position.The 2 DC driver module communicates with M5Stack Fire through I2C(0x3A).

Caution: While using `PSRAM`, you `cannot` use `PortC`

### Features <a href="#features" id="features"></a>

* 6-DOF IMU
* Two-wheel drive, PID control balance
* Grove extension ports
* 8-channel servo drive, 4-channel external connection, 4-channel built-in
* Support Wi-Fi programmable
* Built-in speaker
* TF Card Support
* LEGO™ Compatible
* Programming Support
  * Python
  * UIFlow (Blockly)
  * Arduino

### Applications <a href="#applications" id="applications"></a>

* Balancing car

### Specifications <a href="#specifications" id="specifications"></a>

| Resources          | Parameter                                                    |
| ------------------ | ------------------------------------------------------------ |
| ESP32              | 240MHz Dual Core,600 DMIPS,520KB SRAM,Wi-Fi                  |
| Flash              | 16MB Flash                                                   |
| PSRAM              | 8MB PSRAM                                                    |
| LCD                | 2.0 inch, 320x240 Color TFT LCD, ILI9342C                    |
| Speaker            | 1W-0928                                                      |
| MEMS               | MPU6886                                                      |
| Motor Driver       | HR8833                                                       |
| Base Controller    | STM32F030C8T6                                                |
| Ports              | GROVE I2C\*1/UART\*1/GPIO\*1/SERVO\*4(+4 Extendable Channel) |
| Battery Capacity   | 1200mAh                                                      |
| Net Weight         | 153.9g                                                       |
| Gross Weight       | 260.0g                                                       |
| Product Size       | 54\*54\*65\*mm                                               |
| Package dimensions | 170\*110\*66mm                                               |
| Case Material      | Plastic                                                      |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/app/bala2/bala2_sch_01.webp" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

**GROVE Port A & B & C**

| ESP32 Chip | GPIO22 | GPIO21 | GPIO26 | GPIO36 | GPIO16 | GPIO17 |
| ---------- | ------ | ------ | ------ | ------ | ------ | ------ |
| PORT A     | SCL    | SDA    |        |        |        |        |
| PORT B     |        |        | DAC    | ADC    |        |        |
| PORT C     |        |        |        |        | RX     | TX     |
