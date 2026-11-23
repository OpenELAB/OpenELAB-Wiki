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

# M5Stack Dial - ESP32-S3 Smart Rotary Knob

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5Stack Dial - ESP32-S3 Smart Rotary Knob

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description

As a versatile embedded development board, **M5Dial** integrates the necessary features and sensors for various smart home control applications. It features a 1.28-inch round TFT touchscreen, a rotary encoder, an RFID detection module, an RTC circuit, a buzzer, and under-screen buttons, enabling users to easily implement a wide range of creative projects.

The main controller of M5Dial is M5StampS3, a micro module based on the ESP32-S3 chip known for its high performance and low power consumption. It supports Wi-Fi, as well as various peripheral interfaces such as SPI, I2C, UART, ADC, and more. M5StampS3 also comes with 8MB of built-in Flash, providing sufficient storage space for users.

The standout feature of M5Dial is its rotary encoder, which accurately records the position and direction of the knob, delivering a better interactive experience. Users can adjust settings such as volume, brightness, and menu options using the knob, or control home applications like lights, air conditioning, and curtains. The device's built-in display screen allows for displaying different interaction colors and effects.

<figure><img src="../../.gitbook/assets/image (742).png" alt=""><figcaption></figcaption></figure>

With its compact size and lightweight design, M5Dial is suitable for various embedded applications. Whether it's controlling home devices in the smart home domain or monitoring and controlling systems in industrial automation, M5Dial can be easily integrated to provide intelligent control and interaction capabilities.

M5Dial also features RFID detection, enabling the recognition of RFID cards and tags operating at 13.56MHz. Users can utilize this function for applications such as access control, identity verification, and payments.Furthermore, M5Dial is equipped with an RTC circuit to maintain accurate time and date. Additionally, it includes an onboard buzzer and a physical button for device sound prompts and wake-up operations.

M5Dial provides versatile power supply options to cater to various needs. It accommodates a wide range of input voltages, accepting 6-36V DC input. Additionally, it features a battery port with a built-in charging circuit, enabling seamless connection to external Lithium batteries. This adaptability allows users to power M5Dial via USB-C, the DC interface, or an external battery for on-the-go convenience. M5Dial also reserves two PORTA and PORTB interfaces, supporting the expansion of I2C and GPIO devices. Users can connect various sensors, actuators, displays, and other peripherals through these interfaces, adding more functionality and possibilities.

Power-on: WAKE up can be started by pressing the "Wake" button and IRQ signal triggered by RTC periodically. After triggering the wake up signal, the hold(G46) pin needs to be set to a high level (1) during program initialization to maintain the power supply, otherwise the device will enter the sleep state again.\
Shutdown: When no USB external power supply, press the RST key to achieve; Or when there is no USB external power supply, set HOLD(GPIO46)=0 in the program operation, that is, to achieve power off.

### Features

* Circular TFT touch screen
* M5StampS3
* Encoder
* RFID
* 6-36V voltage input
* Interface extension: reserved PORTA and PORTB interfaces
* Programming platform: Arduino, UIFlow、ESP-IDF

### Includes

* 1x M5Dial

### Applications

* Smart home control
* Internet of Things Project
* Access control system
* industrial control

### Specification

| Resources                                         | Parameters                                                                                                      |
| ------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| MCU                                               | ESP32-S3@Xtensa LX7 ,8M-FLASH,WIFI,OTG\CDC Function                                                             |
| Voltage input range                               | 6-36V                                                                                                           |
| Screen driver                                     | <p>GC9A01<br>1.28 Inch 240x240px</p>                                                                            |
| Touch driver                                      | FT3267                                                                                                          |
| RFID                                              | WS1850S                                                                                                         |
| Standby current (battery-powered standby current) | DC4.2V/1.9uA                                                                                                    |
| Working current                                   | <p>DC6V power supply : DC6V/140.6mA<br>DC12V power supply: DC12V/82.5mA<br>DC36V power supply: DC36V/28.1mA</p> |
| Product Size                                      | 45\*45\*32.3mm                                                                                                  |
| Package Size                                      | 163\*120\*59mm                                                                                                  |
| Product Weight                                    | 46.6g                                                                                                           |
| Package Weight                                    | 83.83g                                                                                                          |

## Official documentation and development resources

Use [Dial](https://docs.m5stack.com/en/core/Dial) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K130`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                 | Model-specific reference                                                                                                 |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Arduino development tutorial     | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5dial/program)                                  |
| Electrical schematic             | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/499/Sch_M5Dial.pdf)                         |
| Mechanical / CAD files           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K130_Dial/Structures)          |
| Mechanical / CAD files           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K130_Dial/Structures/Dial.stl) |
| Official source: M5Dial          | [Read official source: m5dial](https://github.com/m5stack/M5Dial)                                                        |
| Official source: M5Dial-UserDemo | [Read official source: m5dial-userdemo](https://github.com/m5stack/M5Dial-UserDemo)                                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
