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

# ESP32-S3-Nano - Development Board

{% hint style="info" %}
[**View Waveshare ESP32-S3-Nano - Development Board on OpenELAB**](https://openelab.io/products/esp32-s3-nano)

**Store SKU / option:** `Waveshare-26745`, `Waveshare-26752`. Match the purchased model and revision to the official reference below.
{% endhint %}

### ESP32-S3-Nano - Development Board

***

### Product Link

{% embed url="https://openelab.io/products/esp32-s3-nano?variant=43458946433222" %}

### Introduction

ESP32-S3-Nano adopts ESP32-S3R8 as the main controller, compatible with Arduino Nano ESP32, and is suitable for applications such as IoT or MicroPython. Compact in size while with powerful performance, it is applicable for the standalone project.

### Features

* Adopting ESP32-S3R8 as the main controller with Xtensa® 32-bit LX7 dual-core processor, capable of running at 240 MHz
* Integrated 512KB SRAM, 384KB ROM, 8MB PSRAM, 16MB Flash memory.
* Integrated 2.4GHz Wi-Fi and Bluetooth LE dual-mode wireless communication, with superior RF performance.
* Supports seamless switching between Arduino and Micro Python programming, offering greater flexibility.
* Compatible with Arduino IoT Cloud, enabling users to monitor and control their projects from anywhere with Arduino Internet of Things (IoT) cloud applications.
* Supports HID (Human Interface Device), emulating Human Interface Devices such as keyboards or mice via USB port for easier interaction with PC.

### Version Options

<figure><img src="https://www.waveshare.com/w/upload/5/5a/ESP32-S3-Nano_Version.png" alt=""><figcaption></figcaption></figure>

### Product Parameters Comparison

<figure><img src="../../.gitbook/assets/image (725).png" alt=""><figcaption></figcaption></figure>

### Hardware Description

<figure><img src="https://www.waveshare.com/w/upload/3/39/ESP32-S3-Nano_Version2.png" alt=""><figcaption></figcaption></figure>

### Pinout Definition

<figure><img src="https://www.waveshare.com/w/upload/2/2d/ESP32-S3-Nano_Version3.jpg" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="https://www.waveshare.com/w/upload/4/49/ESP32-S3-Nano_Version4.jpg" alt=""><figcaption></figcaption></figure>

### User Guide

#### Environment Setting

The software framework for ESP32 series development boards is mature, and you can use CircuitPython, MicroPython and C/C++ (Arduino, ESP-IDF) for rapid prototyping of product development. Here's a brief introduction to these three development approaches:

* CircuitPython is a programming language designed to simplify coding tests and learning on low-cost microcontroller boards. It is an open-source derivative of the MicroPython programming language, primarily aimed at students and beginners. CircuitPython development and maintenance are supported by Adafruit Industries.
  * You can refer to [development documentation](https://docs.circuitpython.org/en/latest/shared-bindings/index.html) for CircuitPython-related applications development.
  * The [GitHub](https://github.com/adafruit/Adafruit_CircuitPython_Bundle) library for CircuitPython allows for recompilation for custom development.
* MicroPython is an efficient implementation of the Python 3 programming language. It includes a small subset of the Python standard library and has been optimized to run on microcontrollers and resource-constrained environments.
  * You can refer to [development documentation](https://docs.micropython.org/en/latest/) for MicroPython-related application development.
  * The [GitHub library](https://github.com/micropython/micropython) for MicroPython allows for recompilation for custom development.
* The official libraries and support from Espressif Systems for C/C++ development make it convenient for rapid installation.
  * [Arduino development manual](https://docs.espressif.com/projects/arduino-esp32/en/latest/installing.html) for ESP32 series
  * [ESP-IDF development manual](https://docs.espressif.com/projects/esp-idf/en/stable/esp32s2/get-started/index.html) for ESP32 series
* The environment is set up under Windows 10, users can choose to use Arduino or Visual Studio Code (ESP-IDF) as IDE for development. For Mac/Linux OS users please refer to the [official instructions](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html).

#### Arduino

**Install Arduino IDE**

* The following development system is Windows.

1\. Open [the official software download webpage](https://www.arduino.cc/en/software), and according to the corresponding system and system bits to download.

<figure><img src="https://www.waveshare.com/w/upload/f/f0/ESP32-S3-Pico_35.jpg" alt=""><figcaption></figcaption></figure>

2\. You can choose "Just Download", or "Contribute & Download".

<figure><img src="https://www.waveshare.com/w/upload/8/80/ESP32-S3-Pico_36.jpg" alt=""><figcaption></figcaption></figure>

3\. Run to install the program and install it all by default.

**Install Nano ESP32 Package**

* Install Nano ESP32: Open Boards Manger -> Search "Nano ESP32" and install the latest version (or the version to use).

<figure><img src="https://www.waveshare.com/w/upload/7/79/ESP32-S3-Nano_TEST_01.png" alt=""><figcaption></figcaption></figure>

**Create Example**

* The following example is about how to make LED blinking. (File -> examples -> Blink under 01.Basics)

<figure><img src="https://www.waveshare.com/w/upload/3/36/R7FA4_PLUS_B_Example.jpg" alt=""><figcaption></figcaption></figure>

* Select the development board and COM ports.

Search "Nano ESP32", select "Arduino Nano ESP32", and then click on OK (the following picture is for reference only, you need to select the corresponding board.)

<figure><img src="https://www.waveshare.com/w/upload/a/a0/ESP32-S3-Nano_TEST_12.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (726).png" alt=""><figcaption></figcaption></figure>

* Click ✓ in the menu bar to compile and → to burn the compiled demo to the board.

<figure><img src="https://www.waveshare.com/w/upload/8/82/R7FA4_PLUS_B_Example3.jpg" alt=""><figcaption></figcaption></figure>

**Open Example**

* Open the existing example, it is easier to operate. Directly run the ".ino" demo and refer to the operation above, and select the corresponding board and COM port to compile, download and burn.

<figure><img src="https://www.waveshare.com/w/upload/f/f0/R7FA4_PLUS_A_Open.jpg" alt=""><figcaption></figcaption></figure>

* ESP32-S3-Nano opens the Arduino demo: Open File -> Examples. These demos can be directly used without other external libraries.

<figure><img src="https://www.waveshare.com/w/upload/b/bf/ESP32-S3-Nano_01.png" alt=""><figcaption></figcaption></figure>

#### MicroPython

1\. Download and install the latest [Thonny](https://thonny.org/) IDE, open Thonny IDE -> Configure interpreter... as shown below:

![](<../../.gitbook/assets/image (732).png>)\
2\. Press the BOOT key on the board, connect to the USB cable, and find the Device Manager or the corresponding COM port. Download or run the demo, and you can see the Hardware Description chapter for more details.\
3\. According to the steps below, download the online MPY firmware of the ESP32 series, and clean the Flash content of the development board before downloading, and the whole download process lasts about 1 minute.

![](<../../.gitbook/assets/image (731).png>)\
4\. If the Tonny IDE needs to download the local firmware, you can operate it by following the steps below. Select Step 3 or Step 4, and Step 4 is recommended.\
[![ESP32-C3-Zero 09.jpg](https://www.waveshare.com/w/upload/4/41/ESP32-C3-Zero_09.jpg)](https://www.waveshare.com/wiki/File:ESP32-C3-Zero_09.jpg)\
5\. Please refer to [MicroPython Documentation](https://github.com/micropython/micropython/releases/tag/v1.18), [releases note](https://github.com/micropython/micropython/releases/tag/v1.18) for programming.

### Sample Demo

* For the Arduino example demo, please refer to [arduino-esp32](https://github.com/espressif/arduino-esp32) or File -> examples in Arduino IDE, these examples can be used directly without external libraries.

<figure><img src="https://www.waveshare.com/w/A6Y79bcq/Kdy80nYY.php?f=ESP32-S3-Nano_01.png&#x26;width=1000" alt=""><figcaption></figcaption></figure>

* for mpy example, you can refer to [MicroPython documentation](https://docs.micropython.org/en/latest/) and sample demo.

### Resource

#### Document

* [Schematic](https://files.waveshare.com/wiki/ESP32-S3-Nano/ESP32-S3-Nano-Schematic.pdf)
* [MicroPython documentation](https://docs.micropython.org/en/latest/)
* [ESP32 Arduino Core's documentation](https://docs.espressif.com/projects/arduino-esp32/en/latest/index.html)
* [arduino-esp32](https://github.com/espressif/arduino-esp32)

#### Demo

* [Arduino sample demo](https://files.waveshare.com/wiki/ESP32-S3-Nano/ESP32-S3-Nano-Demo-Code.zip)

#### Software

* [Sscom5.13.1.zip](https://www.waveshare.com/w/upload/b/b3/Sscom5.13.1.zip)
* [Thonny Python IDE](https://thonny.org/)
* [Arduino IDE](https://www.arduino.cc/en/software)
* [mpy firmware](https://files.waveshare.com/wiki/ESP32-S3-Nano/Esp32-s3-zero-mpy.zip)

#### Datasheet

* [ESP32-S3 Datasheet](https://www.espressif.com/en/support/documents/technical-documents?keys=\&field_type_tid%5B%5D=842)
* [WS2812B](https://files.waveshare.com/wiki/ESP32-S3-Nano/XL-0807RGBC-WS2812B.pdf)

## Official documentation and development resources

Use [ESP32-S3-Nano](https://docs.waveshare.com/ESP32-S3-Nano) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need                         | Model-specific reference                                                                                          |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Schematics, downloads and model examples | [Read schematics, downloads and model examples](https://docs.waveshare.com/ESP32-S3-Nano/Resources-And-Documents) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
