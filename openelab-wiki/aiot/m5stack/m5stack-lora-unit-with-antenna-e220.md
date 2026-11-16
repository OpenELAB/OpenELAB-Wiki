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

# M5Stack LoRa Unit with Antenna(E220)

### M5Stack LoRa Unit with Antenna(E220)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-lora-unit" %}

### Introduction

The **LoRaE220-433 Unit** is a 433MHz LoRa communication module released by M5Stack, utilizing the LLCC68 chip solution. Compared to the traditional SX1278 solution, the LLCC68 offers advantages such as longer transmission distance, faster speed, and lower power consumption. This unit supports features like over-the-air wake-up, carrier sensing, and communication keys. It achieves point-to-point and broadcast transmission modes through convenient serial communication. The module includes an onboard DIP switch that allows users to switch between four different operating modes, enabling easy data transmission and reception without complex configurations. It is suitable for various applications, including home security alarms, building automation, smart homes, and the automotive industry.

<figure><img src="../../.gitbook/assets/image (544).png" alt=""><figcaption></figcaption></figure>

### Features

* Utilizes LLCC68 chip solution
* Maximum transmission power of 22dBm, software adjustable
* Supports user-defined communication keys
* Supports over-the-air wake-up
* Supports point-to-point transmission, broadcast transmission, and channel monitoring
* Communication frequency: Supports 433MHz frequency band (410.125 \~ 493.125MHz)
* Onboard DIP switch to adjust communication modes
* Serial communication

### Specifications

<table><thead><tr><th width="302">Resources</th><th>Parameters</th></tr></thead><tbody><tr><td>Lora Module</td><td>E220-400T22S@LLCC68</td></tr><tr><td>Supported Frequency Band</td><td>Default 433MHz (supports 410.125 ~ 493.125MHz)</td></tr><tr><td>Maximum Transmission Power</td><td>22dBm, software adjustable</td></tr><tr><td>Receive Sensitivity</td><td>-129 dBm</td></tr><tr><td>Power Supply Voltage</td><td>5V</td></tr><tr><td>Communication Method</td><td>Serial communication (115200)</td></tr><tr><td>Operating Modes</td><td>Transmission mode、WOR transmit mode、WOR receive mode、Sleep mode</td></tr><tr><td>Antenna</td><td>Rubber antenna (@2.5dBi, total length 110mm, SMA male connector)</td></tr><tr><td>Working temperature</td><td>0-40°C</td></tr><tr><td>Product Size</td><td>71.4*24*8mm</td></tr><tr><td>Package Size</td><td>136*92*13mm</td></tr><tr><td>Product Weight</td><td>19.4g</td></tr><tr><td>Package Weight</td><td>24.8g</td></tr></tbody></table>

### Pinout

* **VCC**: Power supply (2.3V to 5.2V)
* **GND**: Ground
* **TXD**: UART Transmit
* **RXD**: UART Receive
* **AUX**: Auxiliary (used for waking up the module)
* **M0**: Mode control pin 0
* **M1**: Mode control pin 1
* **SET**: Configuration pin

### Dimensions

<figure><img src="../../.gitbook/assets/image (545).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Power Connection**: Connect VCC and GND to a suitable power source.
* **UART Communication**: Connect TXD to the RX of your microcontroller and RXD to the TX.
* **Mode Setting**: Use M0 and M1 pins to set the operation mode (e.g., Normal, Wake-up, Power-saving, Sleep).
* **Configuration**: Use the SET pin and appropriate commands to configure the module's settings.
* **Antenna Connection**: Attach the provided antenna to ensure optimal performance.

### FAQ

<details>

<summary><strong>What is the maximum communication range of the M5Stack LoRa Unit?</strong> </summary>

The unit can communicate over distances up to 10 km, depending on the environment and antenna setup.

</details>

<details>

<summary><strong>Can the M5Stack LoRa Unit operate on different frequency bands?</strong> </summary>

Yes, it supports 868 MHz and 915 MHz frequency bands.

</details>

<details>

<summary><strong>How do I configure the module?</strong> </summary>

Configuration can be done using UART commands and the SET pin. Refer to the datasheet for detailed command instructions.

</details>

<details>

<summary><strong>What are the power consumption levels?</strong></summary>

In sleep mode, it consumes less than 2µA, standby mode consumes 2.5mA, and in transmit mode, it can consume up to 120mA.

</details>

<details>

<summary><strong>Is the M5Stack LoRa Unit suitable for battery-powered applications?</strong></summary>

Yes, due to its low power consumption, it is ideal for battery-powered projects.

</details>
