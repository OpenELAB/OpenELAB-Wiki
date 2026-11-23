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

# Seeed Studio XIAO ESP32S3 WIFI Dev Board

{% hint style="info" %}
[**View Seeed Studio XIAO ESP32S3 chip 2.4GHz WiFi BLE 5.0 BT Dev Board on OpenELAB**](https://openelab.io/products/seeed-studio-xiao-esp32s3)

**Store SKU / option:** `Seeed-113991114`. Match the purchased model and revision to the official reference below.
{% endhint %}

### Seeed Studio XIAO ESP32S3 WIFI Dev Board

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-esp32s3" %}

### Introduction

The Seeed Studio XIAO ESP32S3 WIFI Dev Board is a compact and powerful development board designed for IoT projects. It integrates the ESP32-S3 microcontroller, which offers Wi-Fi connectivity and various peripherals in a small form factor. This board is ideal for developers looking for a reliable and efficient platform for building connected devices and applications.

### Features

* **Powerful MCU Board:** Incorporate the ESP32S3 32-bit, dual-core, Xtensa processor running at up to 240MHz, mounted multiple development ports, Arduino / MicroPython supported
* **Outstanding RF performance:** Supports 2.4GHz WiFi and BLE 5.0 dual wireless communication, support 100m+ remote communication when connected with U.FL antenna
* **Elaborate Power Design:** Lithium battery charge management capability, offer 4 power consumption model which allows for deep sleep mode with power consumption as low as 14μA
* **Thumb-sized Compact Design:** 21 x 17.5mm, adopting the classic form factor of XIAO, suitable for space limited projects like wearable devices
* **Perfect for Production:** Breadboard-friendly & SMD design, no components on the back

### Specifications

| Parameter                                                                                           | Seeed Studio XIAO ESP32S3                                                                          | [Seeed Studio XIAO ESP32C3](https://www.seeedstudio.com/Seeed-XIAO-ESP32C3-p-5431.html)           |
| --------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Processor                                                                                           | ESP32-S3R8                                                                                         | ESP32-C3 SoC                                                                                      |
| Xtensa LX7 dual-core, 32-bit processor running up to 240 MHz                                        | RISC-V single-core 32-bit chip processor with a four-stage pipeline that operates at up to 160 MHz |                                                                                                   |
| Wireless                                                                                            | Complete 2.4GHz WiFi subsystem                                                                     |                                                                                                   |
| BLE: Bluetooth 5.0, Bluetooth mesh                                                                  |                                                                                                    |                                                                                                   |
| On-chip Memory                                                                                      | 8M PSRAM & 8MB Flash                                                                               | 400KB SRAM & 4MB Flash                                                                            |
| Interface                                                                                           | 1x UART, 1x IIC, 1x IIS, 1x SPI,11x GPIO(PWM), 9x ADC, 1x User LED, 1x Charge LED                  | 1x UART, 1x IIC, 1x SPI,11x GPIO(PWM), 4x ADC                                                     |
| 1x Reset button, 1x Boot button                                                                     |                                                                                                    |                                                                                                   |
| Dimensions                                                                                          | 21 x 17.5mm                                                                                        |                                                                                                   |
| Power                                                                                               | <p>Input voltage (Type-C): 5V</p><p>Input voltage (BAT): 4.2V</p>                                  | <p>Input voltage (Type-C): 5V</p><p>Input voltage (BAT): 4.2V</p>                                 |
| <p>Circuit operating Voltage (ready to operate):</p><p>- Type-C: 5V@19mA</p><p>- BAT: 3.8V@22mA</p> | <p>Circuit operating Voltage (ready to operate):</p><p>- USB:5V@9mA</p><p>- BAT:3.8V@9mA</p>       |                                                                                                   |
| Charging battery current: 100mA                                                                     | Charging battery current: 350mA                                                                    |                                                                                                   |
| <p>Low Power Consumption Model</p><p>(Supply Power: 3.8V)</p>                                       | <p>Modem-sleep Model: ~ 25 mA</p><p>Light-sleep Model: ~ 2mA</p><p>Deep Sleep Model: ~ 14 μA</p>   | <p>Modem-sleep Model: ~ 24 mA</p><p>Light-sleep Model: ~ 3 mA</p><p>Deep Sleep Model: ~ 44 μA</p> |
| WiFi Enabled Power Consumption                                                                      | Active Model: \~ 100 mA                                                                            | Active Model: <75 mA                                                                              |
| BLE Enabled Power Consumption                                                                       | Active Model: \~ 85 mA                                                                             | Modem-sleep Model: <27 mA                                                                         |
| Working Temperature                                                                                 | -40°C \~ 65°C                                                                                      | -40°C \~ 85°C                                                                                     |

### Pinout

<figure><img src="../../.gitbook/assets/image (462).png" alt=""><figcaption></figcaption></figure>

### Dimensions

* **Board Size**: 21 x 17.5 mm
* **Thickness**: 3.5 mm
* **Weight**: 3 grams

### How to Use

* **Setup the Development Environment**:
  * Install the latest version of Arduino IDE or PlatformIO.
  * Add the ESP32 board library to your environment.
  * Select the correct board and port from the tools menu.
* **Powering the Board**:
  * Connect the board to your computer using a USB Type-C cable.
  * The board will be powered, and you can start uploading your code.
* **Programming**:
  * Write your code in Arduino IDE or PlatformIO.
  * Use the predefined functions to control GPIOs, Wi-Fi, and other peripherals.
  * Upload the code to the board and observe the results.
* **Connecting to Wi-Fi**:
  * Use the `WiFi.h` library to connect the board to a Wi-Fi network.
  * Monitor the connection status via serial output.
* **Interfacing with Sensors and Actuators**:
  * Utilize the GPIO pins to connect sensors and actuators.
  * Use the analog and digital pins for reading sensor data and controlling devices.

### FAQ

<details>

<summary><strong>How do I reset the board?</strong></summary>

You can reset the board by pressing the onboard reset button.

</details>

<details>

<summary><strong>Can I use this board for battery-powered applications?</strong></summary>

Yes, the board's low power consumption makes it suitable for battery-powered projects.

</details>

<details>

<summary><strong>How do I connect to Wi-Fi?</strong></summary>

Use the `WiFi.h` library in your code to connect to a Wi-Fi network by specifying the SSID and password.

</details>

<details>

<summary><strong>What programming languages can I use?</strong></summary>

You can program the XIAO ESP32S3 using C/C++ in the Arduino IDE, or with MicroPython.

</details>

<details>

<summary><strong>Is the XIAO ESP32S3 compatible with Grove sensors?</strong></summary>

Yes, the board is compatible with Grove sensors through the Grove connectors, or by wiring them to the appropriate GPIO pins.

</details>

## Official documentation and development resources

Use [Getting Started with Seeed Studio XIAO ESP32-S3 Series](https://wiki.seeedstudio.com/xiao_esp32s3_getting_started/) for the manufacturer's complete model reference, diagrams and maintained examples. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                                       |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32S3/res/XIAO_ESP32S3_v1.1_Dimensioning.dxf)              |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32S3/res/XIAO_ESP32S3_ExpBoard_v1.0_top.dxf)              |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32S3/res/XIAO_ESP32S3_ExpBoard_v1.0_bot.dxf)              |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32S3/res/XIAO-ESP32S3-Sense-housing-design\(top\).stp)    |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32S3/res/XIAO-ESP32S3-Sense-housing-design\(bottom\).stp) |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32S3/res/TOP.dxf)                                         |
| Mechanical / CAD files | [Read mechanical / cad files](https://files.seeedstudio.com/wiki/SeeedStudio-XIAO-ESP32S3/res/BOTTOM.dxf)                                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
