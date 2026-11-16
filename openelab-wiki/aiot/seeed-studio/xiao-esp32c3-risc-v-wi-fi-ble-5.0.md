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

# XIAO ESP32C3 RISC-V Wi-Fi BLE 5.0

### Seeed Studio XIAO ESP32C3 RISC-V Wi-Fi BLE 5.0 Battery Charge Supported

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-esp32c3" %}

### Description

**Seeed Studio XIAO ESP32C3** is an IoT mini development board based on the Espressif **ESP32-C3** WiFi/Bluetooth dual-mode chip, featuring a **32-bit RISC-V CPU** that delivers powerful computing performance with its efficient architecture. It has excellent radio frequency performance, supporting **IEEE 802.11 b/g/n WiFi**, and **Bluetooth 5 (BLE)** protocols. This board comes included with an external antenna to increase the signal strength for your wireless applications. It also has a **small and exquisite form-factor** combined with a **single-sided surface-mountable design**. It is equipped with rich interfaces and has **11 digital I/O** that can be used as **PWM pins** and **3 analog I/O** that can be used as **ADC pins**. It supports four serial interfaces such as **UART, I2C and SPI**. There is also a small **reset button** and a **bootloader mode button** on the board. XIAO ESP32C3 is fully compatible with the Grove Shield for Seeeduino XIAO and Seeeduino XIAO Expansion board except for the Seeeduino XIAO Expansion board, the SWD spring contacts on the board will not be compatible.

With regard to the features highlighted above, XIAO ESP32C3 is positioned as a **high-performance, low-power, cost-effective IoT mini development board**, suitable for **low-power IoT applications and wireless wearable applications**.[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#specifications)

### Specifications <a href="#specifications" id="specifications"></a>

| Item                  | Seeed Studio XIAO ESP32C3      | Seeeduino XIAO         | Seeed XIAO RP2040                   | Seeed XIAO nRF52840                    | Seeed XIAO nRF52840 Sense               |
| --------------------- | ------------------------------ | ---------------------- | ----------------------------------- | -------------------------------------- | --------------------------------------- |
| Processor             | ESP32-C3 32-bit RISC-V @160MHz | SAMD21 M0+@48MHz       | RP2040 Dual-core M0+@133Mhz         | nRF52840 M4F@64MHz                     | nRF52840 M4F@64MHz                      |
| Wireless Connectivity | WiFi and Bluetooth 5 (BLE)     | N/A                    | N/A                                 | Bluetooth 5.0/BLE/NFC                  | Bluetooth 5.0/BLE/NFC                   |
| Memory                | 400KB SRAM, 4MB onboard Flash  | 32KB SRAM 256KB FLASH  | 264KB SRAM 2MB onboard Flash        | 256KB RAM, 1MB Flash 2MB onboard Flash | 256KB RAM,1MB Flash 2MB onboard Flash   |
| Built-in Sensors      | N/A                            | N/A                    | N/A                                 | N/A                                    | 6 DOF IMU (LSM6DS3TR-C), PDM Microphone |
| Interfaces            | I2C/UART/SPI                   | I2C/UART/SPI           | I2C/UART/SPI                        | I2C/UART/SPI                           | I2C/UART/SPI                            |
| PWM/Analog Pins       | 11/4                           | 11/11                  | 11/4                                | 11/6                                   | 11/6                                    |
| Onboard Buttons       | Reset/ Boot Button             | N/A                    | Reset/ Boot Button                  | Reset Button                           | Reset Button                            |
| Onboard LEDs          | Charge LED                     | N/A                    | Full-color RGB/ 3-in-one LED        | 3-in-one LED/ Charge LED               | 3-in-one LED/ Charge LED                |
| Battery Charge Chip   | ETA4054S2F                     | N/A                    | N/A                                 | BQ25101                                | BQ25101                                 |
| Programming Languages | Arduino/ MicroPython           | Arduino/ CircuitPython | Arduino/ MicroPython/ CircuitPython |                                        |                                         |

### Hardware <a href="#hardware-overview" id="hardware-overview"></a>

<figure><img src="../../.gitbook/assets/image (987).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (988).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (989).png" alt=""><figcaption></figcaption></figure>

[​](https://wiki.seeedstudio.com/XIAO_ESP32C3_Getting_Started/#power-pins)

### Power Pins

* 5V - This is 5v out from the USB port. You can also use this as a voltage input but you must have some sort of diode (schottky, signal, power) between your external power source and this pin with anode to battery, cathode to 5V pin.
* 3V3 - This is the regulated output from the onboard regulator. You can draw 700mA
* GND - Power/data/signal ground

### Strapping Pins <a href="#strapping-pins" id="strapping-pins"></a>

According to the chip manual of ESP32C3, **GPIO2**, **GPIO8** and **GPIO9** in the chip are Strapping Pins, the high and low level configurations of these pins may allow the chip to enter into different Boot modes, please pay attention to this point when you use these pins, otherwise it may prevent your XIAO from uploading or executing the program all the time.

<div align="center"><img src="https://files.seeedstudio.com/wiki/XIAO_WiFi/20.png" alt=""></div>
