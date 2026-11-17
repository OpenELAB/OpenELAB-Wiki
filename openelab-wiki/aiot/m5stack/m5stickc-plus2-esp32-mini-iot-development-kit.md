---
coverY: 0
layout:
  width: default
  cover:
    visible: false
    size: full
    mask: none
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

# M5StickC PLUS2 ESP32 Mini IoT Development Kit

### M5StickC PLUS2 ESP32 Mini IoT Development Kit

***

### Product Link

#### M5StickC Plus2

No matching current OpenELAB.io listing was found for the product version documented here.

#### M5StickC Plus2 with Watch

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**M5StickC PLUS2** is an iterative version of M5StickC PLUS, featuring the ESP32-PICO-V3-02 chip as the main controller with built-in WiFi functionality. The compact device integrates a wealth of hardware resources within its small form factor, including infrared, RTC, microphone, LED, IMU, buttons, buzzer, and more. It boasts a 1.14-inch TFT screen with a resolution of 135\*240, driven by the ST7789V2. The battery capacity has been increased to 200mAh, and the interface also supports HAT and Unit series products. This compact and versatile development tool is designed to spark limitless creative possibilities.

**M5StickC PLUS2** facilitates the rapid prototyping of IoT products, streamlining the entire development process. Even beginners in programming can easily build interesting applications and apply them to real-life scenarios using M5StickC PLUS2.

<figure><img src="../../.gitbook/assets/image (743).png" alt=""><figcaption></figcaption></figure>

Power on:\
Wake up can be started by pressing "BUTTON C" for more than 2 seconds, or IRQ signal triggered by RTC regularly. After triggering the wake up signal, the hold(G4) pin needs to be set to a high level (1) in program initialization to maintain the power supply, otherwise the device will enter the shutdown state again.\
Power off:\
When there is no USB external power supply, press "BUTTON C" for more than 6 seconds; Or when there is no USB external power supply, set HOLD(GPIO4)=0 in the program operation, that is, to achieve power off.

### Features <a href="#features" id="features"></a>

* ESP32-­PICO-­V3-­02-Base，support WiFi
* Built-in 6-Axis IMU
* IR transmitter
* Microphone
* RTC
* Buttons, LCD(1.14 inch)
* Built-in Lithium Polymer Battery@200mAh
* Extendable Socket
* Built-in Passive Buzzer
* Wearable & Wall mounted
* Compatible with multi-platform development:
  * [UIFlow](http://flow.m5stack.com/)
  * [MicroPython](http://micropython.org/)
  * [Arduino](http://www.arduino.cc/)
  * [.NET nanoFramework](https://github.com/nanoframework/nanoFramework.M5Stack)

### Includes <a href="#includes" id="includes"></a>

* 1x M5StickC Plus2

### Applications <a href="#applications" id="applications"></a>

* Internet of things terminal controller
* Wearable devices
* Stem education product
* DIY creation

### Specification <a href="#specification" id="specification"></a>

| Resources             | Parameters                                                                             |
| --------------------- | -------------------------------------------------------------------------------------- |
| ESP32                 | <p>ESP32-PICO-V3-02<br>240MHz dual core,support wifi,2 MB SPI PSRAM,8 MB SPI flash</p> |
| PSRAM                 | 2 MB PSRAM                                                                             |
| Flash                 | 8 MB flash                                                                             |
| Power Input           | 5V @ 500mA                                                                             |
| Port                  | TypeC x 1, GROVE(I2C+I/0+UART) x 1                                                     |
| LCD screen            | 1.14 inch, 135\*240 Colorful TFT LCD, ST7789v2                                         |
| Button                | Custom button x 3                                                                      |
| LED                   | GREEN LED                                                                              |
| MEMS                  | MPU6886                                                                                |
| Buzzer                | built-in buzzer                                                                        |
| MIC                   | SPM1423                                                                                |
| RTC                   | BM8563                                                                                 |
| Battery               | 200mAh @ 3.7V                                                                          |
| Antenna               | 2.4G 3D Antenna                                                                        |
| PIN port              | G0, G25/G36, G26, G32, G33                                                             |
| Operating Temperature | 0°C to 60°C                                                                            |
| Case Material         | Plastic ( PC )                                                                         |
| Product Size          | 48\*25\*13mm                                                                           |
| Package Size          | 114\*64\*23mm                                                                          |
| Product Weight        | 17g                                                                                    |
| Package Weight        | 24.8g                                                                                  |

### How to Use

#### 1. Preparations

* Arduino IDE Installation: Refer to the [Arduino IDE Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_ide)to complete the IDE installation.
* Board Manager Installation: Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/en/arduino/arduino_board)to complete the IDE, M5Stack Board Manager installation, and select the development board `M5StickCPlus2`.
* Dependency Library Installation: Refer to the [Library Management Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_library)to complete the installation of the `M5StickCPlus2` driver library.

#### 2. USB Driver Installation

Click the link below to download the driver program matching your operating system. CP34X (for `CH9102`) driver package. After extracting the package, choose the installation package corresponding to your system's bitness for installation. If you encounter issues with downloading the program (timeout or "Failed to write to target RAM" error), try reinstalling the device driver.

| Driver Name                  | Applicable Chip | Download Link                                                                                        |
| ---------------------------- | --------------- | ---------------------------------------------------------------------------------------------------- |
| CH9102\_VCP\_SER\_Windows    | CH9102          | [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/CH9102_VCP_SER_Windows.exe) |
| CH9102\_VCP\_SER\_MacOS v1.7 | CH9102          | [Download](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/drivers/CH9102_VCP_MacOS_v1.7.zip)  |

#### 3. Download Control Board

Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/en/arduino/arduino_board)to complete the IDE, M5Stack Board Manager installation, and select the development board `M5StickCPlus2`.

<figure><img src="../../.gitbook/assets/image (668).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (669).png" alt=""><figcaption></figcaption></figure>

#### 4. Install Library Files

Dependency Library Installation: Refer to the [Library Management Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_library)to complete the installation of the `M5StickC` driver library.

<figure><img src="../../.gitbook/assets/image (670).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (671).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (672).png" alt=""><figcaption></figcaption></figure>

#### 5. Port Selection

Connect the device to the computer via USB cable. After completing the driver installation, you can select the corresponding device port in the Arduino IDE.

<figure><img src="../../.gitbook/assets/image (673).png" alt=""><figcaption></figcaption></figure>

#### 6. Program Compilation & Burning

Open the example program "display" in the driver library. Click the upload button to automatically compile and burn the program.

<figure><img src="../../.gitbook/assets/image (674).png" alt=""><figcaption></figcaption></figure>

The effect is as shown below:

<figure><img src="../../.gitbook/assets/image (675).png" alt=""><figcaption></figcaption></figure>
