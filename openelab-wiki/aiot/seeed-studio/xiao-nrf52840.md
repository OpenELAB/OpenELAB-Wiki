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

# XIAO nRF52840

### Seeed Studio XIAO nRF52840 Supports Arduino Micro/CircuitPython Ble

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-nrf52840-supports-arduino-circuitpython-bluetooth5-0" %}

### Description

**Seeed Studio XIAO nRF52840** is equipped with a powerful **Nordic nRF52840 MCU** which integrates **Bluetooth 5.0** connectivity. Meanwhile, it has a **small and exquisite form-factor** which can be used for wearable devices and Internet of Things projects. The **single-sided surface-mountable design** and the onboard **Bluetooth antenna** can greatly facilitate the rapid deployment of IoT projects.

In addition, there is an advanced version of this board, **Seeed Studio XIAO nRF52840 Sense**. It is integrated with two extra onboard sensors. One of them is a **Pulse Density Modulation (PDM) Digital Microphone**. It can receive audio data in real-time which allows it to be used for audio recognition. The other one is a **6-axis Inertial Measurement Unit (IMU)**, this IMU can be very useful in TinyML projects like gesture recognition. These onboard sensors provide a great convenience for users while the board is ultra-small.

The newly upgraded **XIAO nRF52840 Plus and XIAO nRF52840 Sense Plus** provide considerable increases in functionality and usability. The number of multifunctional pins has been increased to **20**, **I2S** and **SPI** resources have been added to support more complex projects, **NFC pins** have been exposed for easier integration into IoT and smart card applications, and the **BAT pin** has been repositioned for better soldering convenience, resulting in a more user-friendly hardware experience.

Compared to Seeed Studio XIAO RP2040, Seeed Studio XIAO nRF52840 contains **richer interfaces**. The first thing to note is that the **Near Field Communication (NFC) interface** is functional on the board. Secondly, there is a tiny **reset button** on the side of the Type-C interface. On the other side, there is a **3-in-one LED (User LED)** along with a **Charge LED** to indicate the charging status when a battery is connected. There are **11 digital I/O** that can be used as **PWM pins** and **6 analog I/O** that can be used as **ADC pins**. It supports all three common serial interfaces such as **UART, I2C, and SPI**. Same as Seeed Studio XIAO RP2040, it has an **onboard 2 MB flash** which means it can also be programmed using **Arduino, MicroPython, CircuitPython, or other programming languages**.

Seeed Studio XIAO nRF52840 Sense is compatible to the Seeed Studio XIAO expansion board.

### &#xD;Features

* Powerful wireless capabilities: Bluetooth 5.0 with onboard antenna
* Powerful CPU: Nordic nRF52840, ARM® Cortex®-M4 32-bit processor with FPU, 64 MHz
* Ultra-Low Power: Standby power consumption is less than 5μA
* Battery charging chip: Supports lithium battery charge and discharge management
* Onboard 2 MB flash
* Onboard PDM microphone (only in Seeed Studio XIAO nRF52840 Sense)
* Onboard 6-axis LSM6DS3TR-C IMU (only in Seeed Studio XIAO nRF52840 Sense)
* Ultra Small Size: 21 x 17.8mm, Seeed Studio XIAO series classic form-factor for wearable devices
* Rich interfaces: 1xUART, 1xI2C, 1xSPI, 1xNFC, 1xSWD, 11xGPIO(PWM), 6xADC in XIAO nRF52840 (Sense); and 2xUART, 1xI2C, 2xSPI, 1xI2S, 1xNFC, 1xSWD, 18xGPIO(PWM), 6xADC in XIAO nRF52840 (Sense) Plus
* Single-sided components, surface mounting design

### &#xD;Specifications

| Item                  | Seeed Studio XIAO nRF52840                                         | Seeed Studio XIAO nRF52840 Sense        | Seeed Studio XIAO nRF52840 Plus | Seeed Studio XIAO nRF52840 Sense Plus   |
| --------------------- | ------------------------------------------------------------------ | --------------------------------------- | ------------------------------- | --------------------------------------- |
| Processor             | Nordic nRF52840, ARM® Cortex®-M4 32-bit processor with FPU, 64 MHz |                                         |                                 |                                         |
| Wireless Connectivity | Bluetooth 5.0/BLE/NFC                                              |                                         |                                 |                                         |
| Memory                | 256 KB RAM,1MB Flash 2MB onboard Flash                             |                                         |                                 |                                         |
| Built-in Sensors      | N/A                                                                | 6 DOF IMU (LSM6DS3TR-C), PDM Microphone | N/A                             | 6 DOF IMU (LSM6DS3TR-C), PDM Microphone |
| Interfaces            | 1xI2C, 1xUART, 1xSPI                                               | 1xI2C, 2xUART, 2xSPI, 1xI2S             |                                 |                                         |
| PWM/Analog Pins       | 11/6                                                               | 20/6                                    |                                 |                                         |
| Onboard Buttons       | Reset Button                                                       |                                         |                                 |                                         |
| Onboard LEDs          | 3-in-one LED/ Charge LED                                           |                                         |                                 |                                         |
| Battery Charge Chip   | BQ25101                                                            |                                         |                                 |                                         |
| Programming Languages | Arduino/ MicroPython/ CircuitPython                                |                                         |                                 |                                         |

### Hardware <a href="#hardware-overview" id="hardware-overview"></a>

<figure><img src="../../.gitbook/assets/image (352).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (354).png" alt=""><figcaption></figcaption></figure>

<div align="center"><figure><img src="../../.gitbook/assets/image (355).png" alt=""><figcaption></figcaption></figure></div>

### Two Arduino Libraries

Seeed Studio XIAO nRF52840 assembles many functions in one tiny board and sometimes may not perform the best of them. Hence, Seeed has published two Arduino libraries to let it **maximum the power of each function**. Therefore:

* It is recommanded to use the Seeed nRF52 Boards library if you want to apply **Bluetooth function** and "**Low Energy Cost Function**".
* It is recommanded to use the Seeed nRF52 mbed-enabled Boards library if you want to use it in **embedded Machine Learning Applications** or apply "**IMU & PDM advanced function**".
* Both libraries support very well when it comes to the basic usage, such as **LED, Digital, Analog, Serial, I2C, SPI**.

The Pin definition supported by these two libraries might be a little different and Seeed will keep update the wiki until it is clear.

**tip:**

1. If you use the onboard package of Seeed nRF52 Boards, the Serial function may not compile. The solution is to add the line "#include \<Adafruit\_TinyUSB.h>" in your code. You can download this package from: [https://github.com/adafruit/Adafruit\_TinyUSB\_Arduino](https://github.com/adafruit/Adafruit_TinyUSB_Arduino)
2. If you prefer a simpler approach, you can choose Seeed nRF52 mbed-enabled Boards from the beginning. It supports the compilation of the Serial function without the need for additional modifications.
