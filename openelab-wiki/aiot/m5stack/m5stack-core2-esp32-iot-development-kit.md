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

# M5Stack Core2 ESP32 IoT Development Kit

### M5Stack Core2 ESP32 IoT Development Kit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-core2-esp32-iot-development-kit" %}

### Introduction

**M5Core2** is the second generation core device in the M5Stack [iot development kit](https://shop.m5stack.com/products/m5stack-core2-esp32-iot-development-kit-for-aws-iot-edukit) series, which further enhances the functions of the original generation of cores.

The MCU is an[ ESP32 kits ](https://shop.m5stack.com/) model D0WDQ6-V3 and has dual core Xtensa® 32-bit 240Mhz LX6 processors that can be controlled separately. Wi-Fi are supported as standard and it includes an on board 16MB Flash and 8MB PSRAM, USB TYPE-C interface for charging, downloading of programs and serial communication, a 2.0-inch integrated capacitive touch screen, and a built-in vibration motor.

M5Core2 also features a built-in RTC module which can provide accurate timing. The power supply is managed by an AXP192 power management chip, which can effectively control the power consumption of the base and a built-in green LED power indicator helps to notify the user of battery level. The battery capacity has been upgraded to 390mAh, which can power the core for much longer than the previous model.

<figure><img src="../../.gitbook/assets/image (745).png" alt=""><figcaption></figcaption></figure>

The M5Core2 retains the TF-card(microSD) slot and speakers. However, in order to ensure higher quality sound output, the I2S digital audio interface power amplifier chip is used to effectively prevent signal distortion. There are independent power and reset buttons on the left side and bottom of the base.

The 3 icons on the front of the screen are capacitive buttons which are programmable. There is a small expansion board on the back of the base with a 6-axis IMU sensor and microphone. The development platform and programming language supported by M5Stack Core2: Arduino, [UIFlow ](http://flow.m5stack.com/)(using Blockly, MicroPython language) No matter what level of your development and programming skills, M5Stack will help You gradually turn your ideas into reality.

### Features

* ESP32-based, built-in Wi-Fi
* 16M Flash,8M PSRAM
* Built-in speaker, power indicator, vibration motor, RTC, I2S amplifier, capacitive touch screen, power button, reset button
* TF card slot (16G Maximum size)
* Built-in lithium battery, equipped with power management chip
* Independent small board built-in 6-axis IMU, PDM microphone
* M-Bus Socket & Pins

### Specification <a href="#specification" id="specification"></a>

| Resources                             | Parameter                                                                                            |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| ESP32-D0WDQ6-V3                       | 240MHz dual core, 600 DMIPS, 520KB SRAM, Wi-Fi, Bluetooth                                            |
| Flash                                 | 16MB                                                                                                 |
| PSRAM                                 | 8MB                                                                                                  |
| Input Voltage                         | 5V @ 500mA                                                                                           |
| Interface                             | TypeC x 1, GROVE(I2C+I/0+UART) x 1                                                                   |
| IPS LCD Screen                        | 2.0"@320\*240 ILI9342C                                                                               |
| Touch Screen                          | FT6336U                                                                                              |
| Speaker                               | 1W-092                                                                                               |
| LED                                   | Green power indicator light                                                                          |
| Button                                | Power button, RST button, Virtual screen button\*3                                                   |
| Vibration reminder                    | Vibration motor                                                                                      |
| MIC                                   | SPM1423                                                                                              |
| I2S Power Amplifier                   | NS4168                                                                                               |
| 6-axis IMU                            | MPU6886                                                                                              |
| RTC                                   | BM8563                                                                                               |
| PMU                                   | AXP192                                                                                               |
| USB Chip                              | CP2104/CH9102F (two chip versions, there is no difference in function and use)                       |
| DC-DC Boost                           | SY7088                                                                                               |
| TF card slot                          | 16G Max                                                                                              |
| Lithium Battery                       | 390mAh @ 3.7V                                                                                        |
| Antenna                               | 2.4G 3D antenna                                                                                      |
| Operating temperature                 | 0°C to 60°C                                                                                          |
| Base screw specifications             | Hexagon socket countersunk head M3                                                                   |
| Internal PCB board reserved interface | <p>Battery interface (specification: 1.25mm-2P)<br>USB line interface (specification: 1.25mm-4P)</p> |
| Net Weight                            | 52g                                                                                                  |
| Gross Weight                          | 70g                                                                                                  |
| Product Size                          | 54 x 54 x 16mm                                                                                       |
| Package Size                          | 75 x 60 x 20mm                                                                                       |
| Case Material                         | Plastic ( PC )                                                                                       |

### Pinout

<figure><img src="../../.gitbook/assets/image (746).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (747).png" alt=""><figcaption></figcaption></figure>

### How to Use

#### 1. Preparation

* **Arduino IDE Installation:** Refer to the [Arduino IDE Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_ide)to complete the IDE installation.
* **Board Manager Installation:** Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/en/arduino/arduino_board)to complete the IDE and M5Stack board manager installation, and select the `M5Core2` development board.
* **Dependency Library Installation:** Refer to the [Library Management Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_library)to complete the installation of the `M5Core2` driver library.

#### 2. USB Driver Installation

Click the link below to download the driver for your operating system. There are currently two driver chip versions, CP210X (for `CP2104` version) and CP34X (for `CH9102` version). After decompressing the package, select the installer corresponding to your operating system's bit version. (If you are unsure which USB chip your device uses, you can install both drivers. Note that during the installation of `CH9102_VCP_SER_MacOS v1.7`, an error may occur, but the installation is actually complete, and this can be ignored.)

| Driver Name                  | Applicable Chip | Download Link                                                                                        |
| ---------------------------- | --------------- | ---------------------------------------------------------------------------------------------------- |
| CP210x\_VCP\_Windows         | CP2104          | [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/CP210x_VCP_Windows.zip)     |
| CP210x\_VCP\_MacOS           | CP2104          | [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/CP210x_VCP_MacOS.zip)       |
| CP210x\_VCP\_Linux           | CP2104          | [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/CP210x_VCP_Linux.zip)       |
| CH9102\_VCP\_SER\_Windows    | CH9102          | [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/CH9102_VCP_SER_Windows.exe) |
| CH9102\_VCP\_SER\_MacOS v1.7 | CH9102          | [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/CH9102_VCP_MacOS_v1.7.zip)  |

#### 3. Download the Control Board

Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/en/arduino/arduino_board)to complete the IDE and M5Stack board manager installation, and select the `M5Core2` development board.

<figure><img src="../../.gitbook/assets/image (679).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (680).png" alt=""><figcaption></figcaption></figure>

#### 4. Install Library Files

**Dependency Library Installation:** Refer to the [Library Management Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_library)to complete the installation of the `M5Core2` driver library.

<figure><img src="../../.gitbook/assets/image (681).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (683).png" alt=""><figcaption></figcaption></figure>

#### 5. Port Selection

Connect the device to your computer via a USB cable. After completing the driver installation, select the corresponding device port in the Arduino IDE.

<figure><img src="../../.gitbook/assets/image (684).png" alt=""><figcaption></figcaption></figure>

#### 6. Program Compilation & Upload

Open the example program “Helloworld” from the driver library, and click the upload button to automatically compile and upload the program.

<figure><img src="../../.gitbook/assets/image (685).png" alt=""><figcaption></figcaption></figure>

The result is shown below:

<figure><img src="../../.gitbook/assets/image (749).png" alt=""><figcaption></figcaption></figure>
