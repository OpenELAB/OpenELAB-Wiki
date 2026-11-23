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

# M5Stack ATOMS3 Dev Kit w/ 0.85-inch Screen

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5Stack ATOMS3 Dev Kit w/ 0.85-inch Screen

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Introduction

AtomS3 is a highly integrated programmable controller that harnesses the power of the ESP32-S3 chip. This compact controller boasts a range of features, including integrated WiFi functionality and 8MB of on-chip FLASH memory. With the **ESP32-S3** chip, AtomS3 delivers exceptional performance and versatility for a variety of applications.\
\
AtomS3 features a sleek **0.85-inch IPS** screen, providing clear visual feedback and user interaction. The bottom of the screen is equipped with programmable buttons, allowing for customizable functions and enhanced user control. It comes with a built-in 5V to 3.3V circuit, ensuring stable power supply for reliable operation. The controller incorporates a 6-axis gyro sensor **MPU6886**, enabling precise motion detection and orientation tracking. On-board Type-C interface facilitates both power supply and firmware download processes. Additionally, AtomS3 offers one HY2.0-4P expansion port, six GPIOs, and power pins reserved at the bottom for seamless integration and expansion of various applications.

<figure><img src="../../.gitbook/assets/image (651).png" alt=""><figcaption></figcaption></figure>

AtomS3 is designed with compactness in mind, measuring at only 24\*24\*13 mm in size. Its small form factor makes it suitable for a wide range of embedded smart device applications. Whether it's robotics, IoT devices, or other embedded systems, AtomS3 provides a powerful and flexible solution to meet the project requirements.

### Features

* Developed based on ESP32-S3FN8
* Comes with USB download function
* Built-in 3-axis gyroscope and 3-axis accelerometer (MPU6886)
* Programmable keys
* 0.85 inch LCD screen
* Infrared emission function
* Expandable pins and interfaces
* Development platform: Arduino, UIFlow

### Specification <a href="#specification" id="specification"></a>

| Resources                     | Parameters           |
| ----------------------------- | -------------------- |
| MCU                           | ESP32-S3FN8          |
| DCDC                          | SY8089               |
| IMU                           | MPU6886              |
| LCD                           | N085-1212TBWIG06-C08 |
| Operating temperature         | 0°C \~ 40°C          |
| Resolution                    | 128(H)RGB x 128(V)   |
| support voltage               | 5V                   |
| Power supply mode             | TYPE C               |
| output voltage                | 3.3V                 |
| IO interface × 6              | G5/G6/G7/G8/G38G39   |
| Screen communication protocol | SPI                  |
| Product Size                  | 24mm × 24mm × 13mm   |
| Package Size                  | 65mm × 44.5mm × 14mm |
| Product Weight                | 6.8g                 |
| Package Weight                | 10.9g                |

### Pinout

<figure><img src="../../.gitbook/assets/image (652).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (653).png" alt=""><figcaption></figcaption></figure>

### How to Use

### 1. Preparations <a href="#preparations" id="preparations"></a>

* Arduino IDE Installation: Refer to the [Arduino IDE Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_ide)to complete the IDE installation.
* Board Manager Installation: Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/en/arduino/arduino_board)to complete the IDE, M5Stack Board Manager installation, and select the development board `M5AtomS3`.
* Dependency Library Installation: Refer to the [Library Management Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_library)to complete the installation of the `M5AtomS3` driver library.

### 2. Download Mode <a href="#download-mode" id="download-mode"></a>

* Press and hold the reset button (about 2 seconds) until the internal green LED lights up, then release it. The device is now in download mode, ready for burning.

#### M5AtomS3 / M5AtomS3 Lite <a href="#m5atoms3--m5atoms3-lite" id="m5atoms3--m5atoms3-lite"></a>

<figure><img src="../../.gitbook/assets/image (655).png" alt=""><figcaption></figcaption></figure>

### 3. Download Control Board <a href="#download-control-board" id="download-control-board"></a>

Refer to the [Basic Environment Setup Guide ](https://docs.m5stack.com/en/arduino/arduino_board)to complete the IDE, M5Stack Board Manager installation, and select the development board `M5AtomS3`.

<figure><img src="../../.gitbook/assets/image (755).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (756).png" alt=""><figcaption></figcaption></figure>

### 4. Install Library Files <a href="#install-library-files" id="install-library-files"></a>

Dependency Library Installation: Refer to the [Library Management Installation Guide ](https://docs.m5stack.com/en/arduino/arduino_library)to complete the installation of the `M5AtomS3` driver library.

<figure><img src="../../.gitbook/assets/image (757).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (758).png" alt=""><figcaption></figcaption></figure>

### 5. Port Selection <a href="#port-selection" id="port-selection"></a>

Connect the device to the computer via USB cable. After completing the driver installation, you can select the corresponding device port in the Arduino IDE.

<figure><img src="../../.gitbook/assets/image (759).png" alt=""><figcaption></figcaption></figure>

### 6. Program Compilation & Burning <a href="#program-compilation-burning" id="program-compilation-burning"></a>

Open the example program “LEDDisplay” in the driver library. Click the upload button to automatically compile and burn the program.

<figure><img src="../../.gitbook/assets/image (657).png" alt=""><figcaption></figcaption></figure>

The effect is as shown below:

<figure><img src="../../.gitbook/assets/image (658).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [AtomS3](https://docs.m5stack.com/en/core/AtomS3) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`C123`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                   | Model-specific reference                                                                                                     |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial       | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5atoms3/program)                                    |
| Electrical schematic               | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/472/Sch_M5_AtomS3_v1.0.pdf)                     |
| Electrical schematic               | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/472/Sch_AtomS3_IMU.pdf)                         |
| Mechanical / CAD files             | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/C123_AtomS3/Structures)            |
| Mechanical / CAD files             | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/C123_AtomS3/Structures/AtomS3.stl) |
| Official source: M5AtomS3          | [Read official source: m5atoms3](https://github.com/m5stack/M5AtomS3)                                                        |
| Official source: M5AtomS3-UserDemo | [Read official source: m5atoms3-userdemo](https://github.com/m5stack/M5AtomS3-UserDemo)                                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
