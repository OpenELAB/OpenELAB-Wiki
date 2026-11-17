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

# NRF24L01 with 2.4 GHz

### NRF24L01 with 2.4 GHz Wireless Module

***

### Product Link

{% embed url="https://openelab.io/products/nrf24l01?_pos=1&_sid=b1c0f41c8&_ss=r" %}

### **Introduction**

The **NRF24L01** is a highly integrated, ultra-low-power wireless transceiver module designed by Nordic Semiconductor. Operating in the 2.4 GHz ISM (Industrial, Scientific, and Medical) band, it enables wireless data communication between microcontroller-based devices such as Arduino, Raspberry Pi, and ESP modules. The NRF24L01 is particularly popular in applications such as remote control systems, sensor networks, and IoT projects, thanks to its cost-effectiveness and ease of use

### **Features**

* Operates in the 2.4 GHz ISM band.
* Multi-channel capability with 125 selectable channels.
* Data rates of 250 Kbps, 1 Mbps, and 2 Mbps.
* Range up to 100 meters in open spaces without obstacles.
* Automatic packet handling, including auto-retransmission and auto-acknowledgment.
* Multiceiver function: can handle up to 6 data pipelines (addresses) simultaneously.
* SPI interface for easy integration with microcontrollers.
* Low power consumption (idle mode: 900nA).
* Onboard 32-byte FIFO buffers for TX and RX

### **Specifications**

* **Operating Voltage**: 1.9V to 3.6V (3.3V is optimal).
* **Frequency Range**: 2.4 GHz to 2.525 GHz.
* **Maximum Data Rate**: 2 Mbps.
* **Communication Channels**: 125 selectable.
* **Power Consumption**:
  * TX at 0 dBm: 11.3 mA.
  * RX in receiving mode: 12.3 mA.
  * Power down mode: 900 nA.
* **Range**: Up to 100 meters (line of sight).
* **Max Payload Size**: 32 bytes per packet

### **Pinout**

| Pin  | Function            | Description                                                          |
| ---- | ------------------- | -------------------------------------------------------------------- |
| GND  | Ground              | Connect to system ground.                                            |
| VCC  | Power Supply        | 1.9V to 3.6V (3.3V recommended).                                     |
| CE   | Chip Enable         | Controls TX/RX modes. High = active.                                 |
| CSN  | Chip Select         | Active low. Controls SPI communication.                              |
| SCK  | Serial Clock        | Clock signal for SPI interface.                                      |
| MOSI | Master Out Slave In | Data line for SPI communication (data input).                        |
| MISO | Master In Slave Out | Data line for SPI communication (data output).                       |
| IRQ  | Interrupt Request   | Signals when new data is available (optional)【29†source】【31†source】. |

### **Dimensions**

* **Module Size**: Approximately 15 mm x 29 mm.
* Compact and easy to integrate into a wide range of projects with space constraints【30†source】.

### **How to Use**

To use the NRF24L01 module, connect it to a microcontroller (such as Arduino) via the SPI interface. Libraries like **RF24** are available for Arduino, simplifying communication between devices. Typical usage involves:

1. Setting the module in either transmitter or receiver mode.
2. Sending or receiving data packets using the **radio.write()** and **radio.read()** functions.
3. Adjusting the module settings, such as data rate, power level, and channels, for optimal performance.

### Example setup for Arduino:

* Connect the **VCC** to 3.3V and **GND** to ground.
* Use digital pins for **CE**, **CSN**, **MOSI**, **MISO**, and **SCK** connections.
* Implement code to configure the module and establish wireless communication

### **FAQ**

<details>

<summary><strong>How far can the NRF24L01 communicate?</strong></summary>

In ideal conditions (line of sight and minimal interference), the range can reach up to 100 meters. Indoors or in cluttered environments, the range may be reduced due to interference and obstacles【27†source】.

</details>

<details>

<summary><strong>What is the maximum data rate?</strong></summary>

The NRF24L01 can achieve a maximum data rate of 2 Mbps. Lower data rates, such as 250 Kbps and 1 Mbps, can be used for longer range and better reliability

</details>

<details>

<summary><strong>Can I use multiple NRF24L01 modules in one project?</strong></summary>

Yes, the NRF24L01 supports a multiceiver function, allowing up to 6 devices to communicate with one receiver using different data pipelines

</details>

<details>

<summary><strong>Why is my NRF24L01 module not working?</strong></summary>

Common issues include insufficient power from the 3.3V line of your microcontroller or interference from nearby devices. Consider using a decoupling capacitor (10uF to 100uF) and an external 3.3V power supply

</details>
