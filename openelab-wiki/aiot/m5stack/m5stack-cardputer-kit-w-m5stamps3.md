---
layout:
  width: default
  title:
    visible: true
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

# M5Stack Cardputer Kit w /M5StampS3

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5Stack Cardputer Kit w /M5StampS3

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

Cardputer is a card-sized portable computer that is perfect for engineers. At the heart of Cardputer is the M5StampS3, a mini development board based on the ESP32-S3 chip. Cardputer features a powerful dual-core processor, supports Wi-Fi functionality and integrates various peripherals and sensors, making it ideal for rapid functional verification, industrial control and home automation systems.

The 56-key keyboard and 1.14" TFT screen allow users to easily enter and view information. The on-board SPM1423 digital MEMS microphone and built-in speaker enable voice operations such as recording, wake-up and audio playback. The infrared emitter allows infrared control interaction with external devices such as TVs or air conditioners. And Cardputer offers a HY2.0-4P interface for expanding I2C sensors such as temperature and humidity sensors, light sensors and pressure sensors, which allows users to add different functional modules according to their needs and unleash their creativity. Cardputer also includes a Micro SD card slot for expanding storage space. Users can store program code, data files, images, audio and other resources on the Micro SD card.

<figure><img src="../../.gitbook/assets/image (744).png" alt=""><figcaption></figcaption></figure>

The device is powered by an internal 120mAh+1400mAh (in the base) lithium battery solution, eliminating concerns about battery life. In addition, Cardputer has built-in battery charging and voltage regulation circuits that automatically adjust voltage and current to protect the battery and the device. The base of the Cardputer incorporates a magnet, allowing it to be attached to metal surfaces such as fridges or whiteboards. What’s more, Cardputer's structure is compatible with Lego hole extensions, allowing users to create even more interesting designs using Lego bricks.

### Features <a href="#features" id="features"></a>

* M5StampS3 Microcontroller.
* 56 key keyboard.
* 1.14 Inch TFT Screen.
* Cavity speaker and SPM1423 digital MEMS microphone.
* Infrared emission tube is used for infrared control interaction.
* HY2.0-4P port for connecting and expanding I2C sensors.
* Micro SD card slot for expanding storage space.
* The built-in 120mAh and 1400mAh lithium battery in the base provide long battery life.
* Base with magnet, compatible with Lego hole expansion.

### Includes <a href="#includes" id="includes"></a>

* 1x Cardputer
* 1x Hex Key

### Applications <a href="#applications" id="applications"></a>

* Fast functional verification and prototyping
* Industrial control and automation
* Home Control System
* Data acquisition and sensor monitoring
* Embedded system development and learning
* Wireless communication and Internet of Things (IoT) projects

### Specification <a href="#specification" id="specification"></a>

| Resources                  | Parameters                                                                                                                                                                  |
| -------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| StampS3                    | ESP32-S3@Xtensa LX7 ,8M-FLASHWIFI,OTG\CDC Function                                                                                                                          |
| Battery Capacity           | 120mAh+1400mAh                                                                                                                                                              |
| Screen                     | ST7789V2@1.14 Inch、240\*135px                                                                                                                                               |
| Infrared emission distance | <p>Infrared emission distance (linear distance) of ∠180° : 410cm<br>Infrared emission distance of &#x3C; 90° : 66cm<br>Infrared emission distance of &#x3C; 45° : 170cm</p> |
| Standby current            | DC4.2V/0.26uA                                                                                                                                                               |
| Operating current          | <p>IR emission mode :DC4.2V/ 255.6mA<br>Key mode :DC4.2V/165.7mA</p>                                                                                                        |
| Speaker                    | 8Ω@1W                                                                                                                                                                       |
| Product Size               | 84\*54\*17mm                                                                                                                                                                |
| Package Size               | 149\*94\*18mm                                                                                                                                                               |
| Product Weight             | 92.8g                                                                                                                                                                       |
| Package Weight             | 114g                                                                                                                                                                        |

### How to Use

#### 1. Preparation

* **Arduino IDE Installation**: Refer to the [Arduino IDE Installation Guide ](https://docs.m5stack.com/zh_CN/arduino/arduino_ide)to complete the IDE installation.
* **Board Manager Installation**: Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/zh_CN/arduino/arduino_board)to complete the IDE and M5Stack board manager installation and select the `M5Cardputer` development board.
* **Library Installation**: Refer to the [Library Manager Installation Guide ](https://docs.m5stack.com/zh_CN/arduino/arduino_library)to install the `M5Cardputer` driver library.

#### 2. Download Mode

* Press and hold the G0 button on the M5Cardputer before powering it on, then connect the USB cable to enter download mode.

<figure><img src="../../.gitbook/assets/image (660).png" alt=""><figcaption></figcaption></figure>

#### 3. Download Control Board

Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/zh_CN/arduino/arduino_board)to complete the IDE and M5Stack board manager installation and select the `M5Cardputer` development board.

<figure><img src="../../.gitbook/assets/image (661).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (662).png" alt=""><figcaption></figcaption></figure>

#### 4. Install Library Files

Library Installation: Refer to the [Library Manager Installation Guide ](https://docs.m5stack.com/zh_CN/arduino/arduino_library)to install the `M5Cardputer` driver library.

<figure><img src="../../.gitbook/assets/image (663).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (664).png" alt=""><figcaption></figcaption></figure>

#### 5. Port Selection

Connect the device to the computer via USB cable. After completing the driver installation, you can select the corresponding device port in the Arduino IDE.

<figure><img src="../../.gitbook/assets/image (665).png" alt=""><figcaption></figcaption></figure>

#### 6. Program Compilation & Uploading

Open the example program “display” from the driver library, click the upload button to automatically compile and upload the program.

<figure><img src="../../.gitbook/assets/image (666).png" alt=""><figcaption></figcaption></figure>

The effect is shown in the following image:

<figure><img src="../../.gitbook/assets/image (667).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Cardputer](https://docs.m5stack.com/en/core/Cardputer) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K132`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                      | Model-specific reference                                                                                                           |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial          | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5cardputer/program)                                       |
| Electrical schematic                  | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/481/Sch_M5Cardputer.pdf)                              |
| Electrical schematic                  | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/481/Sch_M5cardputer_Base.pdf)                         |
| Electrical schematic                  | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/522/Sch_M5StampS3_v0.2.pdf)                           |
| Mechanical / CAD files                | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K132_Cardputer/Structures)               |
| Mechanical / CAD files                | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K132_Cardputer/Structures/Cardputer.stl) |
| Official source: M5Cardputer          | [Read official source: m5cardputer](https://github.com/m5stack/M5Cardputer)                                                        |
| Official source: M5Cardputer-UserDemo | [Read official source: m5cardputer-userdemo](https://github.com/m5stack/M5Cardputer-UserDemo)                                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
