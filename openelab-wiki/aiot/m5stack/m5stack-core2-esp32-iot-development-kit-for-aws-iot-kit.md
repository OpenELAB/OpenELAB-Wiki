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

# M5Stack Core2 ESP32 IoT Development Kit for AWS IoT Kit

### M5Stack Core2 ESP32 IoT Development Kit for AWS IoT Kit

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Introduction

**Core2 for AWS** is the reference hardware kit for AWS IoT Kit – a prescriptive learning program from AWS which makes it easy and cost effective to learn how to build IoT applications using AWS services. It comes equipped with a Microchip ATECC608 [Trust\&GO ](https://www.microchip.com/design-centers/security-ics/trust-platform/trust-go)pre-provisioned secure element, in addition to the existing features of the standard M5Stack Core2 and M5GO Bottom2. The Core2 for AWS is a feature rich, plug and play extensible, and secure hardware kit for learning and building a wide range of IoT applications.

To learn more about the Core2 for AWS IoT Kit program, visit [https://core2-for-aws-docs.m5stack.com](https://core2-for-aws-docs.m5stack.com/).

The Core2 for AWS comes with an [ESP32](https://shop.m5stack.com/products/esp32-ethernet-unit-with-poe)-D0WDQ6-V3 micro controller, which features dual Xtensa 32-bit LX6 cores and a main frequency up to 240Mhz, with 2.4GHz Wi-Fi. Comes with 8MB PSRAM and 16MB flash on board.

The main unit is equipped with a 2.0-inch capacitive touch screen that provides a smooth and responsive human machine interface. The built-in vibration motor can be used to provide haptic feedback or alerts. Onboard RTC module provides accurate time of day. Power is supplied through an AXP192 power management chip, to monitor and control power attributes of the device. The included TF card slot supports microSD cards up to 16GB. The on-board speaker is paired with an I2S digital audio interface power amplifier chip to reduce signal distortion and provide clearer audio output. There are independent physical power and reset (RST) buttons on the sides of Core2 for AWS, with 3 programmable touch buttons on the front of the screen.

<figure><img src="../../.gitbook/assets/image (676).png" alt=""><figcaption></figcaption></figure>

**The M5GO Bottom2 for AWS adds additional features and security for IoT applications. The MPU6886 provides 6-axis internal IMU and temperature, the SPM1423 digital microphone captures audio for recording or creating voice applications, 10 individually programmable RGB LEDs via SK6812 to create customized and animated light effects, a 500mAh lithium-ion battery provides power on the go, the onboard Microchip ATECC608 Trust\&GO crypto-authentication chip is pre-provisioned with secure keys to simplify connectivity to AWS and accelerate cryptographic computation.The CP2104 chip interface is reserved on the PCB of Core2 for AWS to interface with the lithium battery.**

### Features

* Reference hardware kit for use with AWS IoT Kit
* ESP32-D0WDQ6-V3, supports 2.4GHz Wi-Fi
* 16M Flash, 8M PSRAM
* Built-in ATECC608 hardware encryption chip
* Capacitive touch screen
* Built-in PDM microphone, power indicator, 6-Axis IMU, vibration motor, I2S codec, Amplifier, Speaker, RTC, power button, reset button, 10 x RGB LEDs
* TF card slot (support up to 16GB)
* Built-in 500mAh Lithium ion battery, equipped with power management chip
* Validated through AWS Device Qualification Program

### Specification <a href="#specification" id="specification"></a>

| Resources                  | Parameter                                            |
| -------------------------- | ---------------------------------------------------- |
| ESP32-D0WDQ6-V3            | 240MHz dual core, 600 DMIPS, 520KB SRAM, Wi-Fi       |
| Flash                      | 16MB                                                 |
| PSRAM                      | 8MB                                                  |
| Hardware encryption chip   | ATECC608B-TNGTLSU-G (addr 0x35)                      |
| Input voltage              | 5V @ 500mA                                           |
| Host interface             | TypeC x1, POGO PIN x1, I2C x1, GPIO x1, UART x1      |
| Programmable LED light     | SK6812\*10                                           |
| Button                     | Power button, RST button, virtual screen button \* 3 |
| Vibration reminder         | Vibration motor                                      |
| IPS LCD screen             | 2.0"@320\*240 ILI9342C                               |
| Capacitive touch screen IC | FT6336U                                              |
| Speaker                    | 1W-0928                                              |
| Microphone                 | SPM1423                                              |
| I2S power amplifier        | NS4168                                               |
| IMU                        | MPU6886                                              |
| RTC                        | BM8563                                               |
| PMU                        | AXP192                                               |
| USB chip                   | CP2104                                               |
| DC-DC boost                | SY7088                                               |
| TF card slot               | Support up to 16G                                    |
| Lithium battery            | 500mAh @ 3.7V                                        |
| Antenna                    | 2.4G 3D antenna                                      |
| Working temperature        | 32°F to 104°F (0°C to 40°C )                         |
| Net weight                 | 101g                                                 |
| Gross weight               | 108g                                                 |
| Product size               | 54 x 54 x 24mm                                       |
| Package size               | 90 x 60 x 27mm                                       |
| Shell material             | Plastic (PC )                                        |

### Pinout

<figure><img src="../../.gitbook/assets/image (678).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (677).png" alt=""><figcaption></figcaption></figure>

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

<figure><img src="../../.gitbook/assets/image (686).png" alt=""><figcaption></figcaption></figure>
