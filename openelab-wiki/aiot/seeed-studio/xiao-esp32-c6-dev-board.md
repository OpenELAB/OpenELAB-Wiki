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

# XIAO ESP32-C6 Dev Board

### Seeed Studio XIAO ESP32-C6 RISC-V 2.4GHz WIFI 6 BLE 5 Dev Board 160MHz

***

### Product Link

{% embed url="https://openelab.io/products/seeed-studio-xiao-esp32c6" %}

### Description <a href="#description" id="description"></a>

Seeed Studio XIAO ESP32C6 is powered by the highly-integrated ESP32-C6 SoC, built on two 32-bit RISC-V processors, with a high-performance (HP) processor with running up to 160 MHz, and a low-power (LP) 32-bit RISC-V processor, which can be clocked up to 20 MHz. There are 512KB SRAM and 4 MB Flash on the chip, allowing for more programming space, and binging more possibilities to the IoT control scenarios.

XIAO ESP32C6 is Matter native thanks to its enhanced wireless connectivity. The wireless stack supports 2.4 GHz WiFi 6, Bluetooth® 5.3, Zigbee, and Thread (802.15.4). As the first XIAO member compatible with Thread, it's a perfect fit for building Matter-compliant projects, thus achieving interoperability in smart-home.

### Features <a href="#features" id="features"></a>

* **Enhanced Connectivity**: Integrates **2.4** GHz Wi-Fi 6 (802.11ax), Bluetooth 5(LE), and IEEE 802.15.4 radio connectivity, allowing for the application of **Thread** and **Zigbee** protocols.
* **Matter Native**: Supports the building of Matter-compliant smart home projects, ensuring interoperability among different smart devices.
* **Security Encrypted on Chip**: Utilizes the ESP32-C6 to provide secure boot, encryption, and Trusted Execution Environment (TEE) features, enhancing the security of smart home projects.
* **Outstanding RF Performance**: Features an on-board antenna with up to _80m_ BLE/Wi-Fi range and offers an interface for connecting an external UFL antenna, ensuring reliable connectivity.
* **Leveraging Power Consumption**: Offers four working modes, including a deep sleep mode with consumption as low as _15_ μA, along with support for lithium battery charge management.
* **Dual RISC-V Processors**: Incorporates two 32-bit RISC-V processors, with the high-performance processor capable of running up to 160 MHz and the low-power processor up to _20 MHz_.
* **Classic XIAO Designs**: Maintains the thumb-size form factor of 21 x 17.8mm and single-sided mount design, ideal for space-limited projects like wearable devices.

### Specifications[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#specifications) <a href="#specifications" id="specifications"></a>

| Products                                                                                                                       | XIAO ESP32C6                                                                                       | XIAO ESP32C3                                                 | XIAO ESP32S3                                                                      |          |
| ------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------------------------------------------- | -------- |
| Processor                                                                                                                      | Espressif ESP32-C6 SoC                                                                             | Espressif ESP32-C3 SoC                                       | Espressif ESP32-S3R8                                                              |          |
| Two 32-bit RISC-V processors, with the high-performance one running up to 160 MHz, and the low-power one clocking up to 20 MHz | RISC-V single-core 32-bit chip processor with a four-stage pipeline that operates at up to 160 MHz | Xtensa LX7 dual-core, 32-bit processor running up to 240 MHz |                                                                                   |          |
| Wireless                                                                                                                       | Complete 2.4GHz **Wi-Fi 6** subsystem                                                              | Complete 2.4GHz Wi-Fi subsystem                              |                                                                                   |          |
| BLE: Bluetooth 5.0, Bluetooth Mesh                                                                                             | BLE: Bluetooth 5.0, Bluetooth Mesh                                                                 | BLE: Bluetooth 5.0, Bluetooth Mesh                           |                                                                                   |          |
| **Zigbee,Thread,IEEE 802.15.4**                                                                                                | /                                                                                                  | /                                                            |                                                                                   |          |
| On-chip Memory                                                                                                                 | 512KB SRAM & 4MB Flash                                                                             | 400KB SRAM & 4MB Flash                                       | 8M PSRAM & 8MB Flash                                                              |          |
| Interface                                                                                                                      | 1x UART,1x LP\_UART, 1x IIC, 1x LP\_IIC, 1x SPI,11x GPIO(PWM), 7x ADC, 1xSDIO 2.0 Slave            | 1x UART, 1x IIC, 1x SPI,11x GPIO(PWM), 4x ADC                | 1x UART, 1x IIC, 1x IIS, 1x SPI,11x GPIO(PWM), 9x ADC, 1x User LED, 1x Charge LED |          |
| 1x Reset button, 1x Boot button                                                                                                |                                                                                                    |                                                              |                                                                                   |          |
| Dimensions                                                                                                                     | 21 x 17.8 mm                                                                                       |                                                              |                                                                                   |          |
| Power                                                                                                                          | Input voltage                                                                                      | <p>Type-C: 5V<br>BAT: 4.2V</p>                               |                                                                                   |          |
| Circuit operating Voltage (ready to operate)                                                                                   | <p>USB:5V@9mA<br>BAT:3.8V@9mA</p>                                                                  | <p>Type-C: 5V@19mA<br>BAT: 3.8V@22mA</p>                     |                                                                                   |          |
| Charging battery current                                                                                                       | 100mA                                                                                              | 350mA                                                        | 100mA                                                                             |          |
| Power Consumption Model(Supply Power: 3.8V)                                                                                    | Modem-sleep Model                                                                                  | \~ 30 mA                                                     | \~ 24 mA                                                                          | \~ 25 mA |
| Light-sleep Model                                                                                                              | \~ 2.5 mA                                                                                          | \~ 3 mA                                                      | \~ 2 mA                                                                           |          |
| Deep Sleep Model                                                                                                               | \~ 15 μA                                                                                           | \~ 44 μA                                                     | \~ 14 μA                                                                          |          |
| Working Temperature                                                                                                            | -40°C \~ 85°C                                                                                      | -40°C \~ 65°C                                                |                                                                                   |          |

### Hardware <a href="#hardware-overview" id="hardware-overview"></a>

| XIAO ESP32C6 indication diagram                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------ |
| <p><img src="https://wdcdn.qpic.cn/MTY4ODg1Nzc0ODUwMjM3NA_556525_Slxs4ARdyuXRrJK-_1711096256?w=9854&#x26;h=3367&#x26;type=image/png" alt=""></p> |
| XIAO ESP32C6 Pin List                                                                                                                            |
| <p><img src="https://wdcdn.qpic.cn/MTY4ODg1Nzc0ODUwMjM3NA_318648_dMoXitoaQiq2N3-a_1711678067?w=1486&#x26;h=1228" alt=""></p>                     |

RF Switch

The **RF Switch** feature allows you to toggle between the built-in ceramic antenna and an external antenna by configuring `GPIO14`. To enable this function, _you must first set `GPIO3` to a low level_, as this activates the RF switch control.

* **GPIO14 Low Level (Default Setting)**: The device uses the built-in ceramic antenna.
* **GPIO14 High Level**: The device switches to the external antenna.

By default, `GPIO14` is set to a low level, enabling the built-in antenna. To use an external antenna, set `GPIO14` to a high level. Refer to the example code below for guidance on configuring `GPIO3` and `GPIO14` to activate the external antenna:

```c
void setup() {
  pinMode(WIFI_ENABLE, OUTPUT); // pinMode(3, OUTPUT);
  digitalWrite(WIFI_ENABLE, LOW); // digitalWrite(3, LOW); // Activate RF switch control

  delay(100);

  pinMode(WIFI_ANT_CONFIG, OUTPUT); // pinMode(14, OUTPUT);
  digitalWrite(WIFI_ANT_CONFIG, HIGH); // digitalWrite(14, HIGH); // Use external antenna
}
```

### Battery Usage[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#battery-usage) <a href="#battery-usage" id="battery-usage"></a>

The XIAO ESP32C6 series features a built-in power management chip, allowing it to be powered independently by a battery or to charge the battery through its USB port.

For connecting a battery to your XIAO, we recommend using a qualified rechargeable 3.7V lithium battery. When soldering the battery, carefully distinguish between the positive and negative terminals. The negative electrode pad should be located on the left side near the silk screen marking "D8," while the positive electrode pad should be located on the right side near the silk screen marking "D5."

## **caution:**

When using battery power, no voltage will be present on the 5V pin.

Red Indicator Light

The XIAO ESP32C6 has a red indicator light for battery charging, similar to the [XIAO ESP32S3](https://wiki.seeedstudio.com/xiao_esp32s3_getting_started/#battery-usage):

The red light behavior for the XIAO ESP32C6 is as follows:

* When no battery is connected:
  * The red light turns on when the Type-C cable is connected and turns off after 30 seconds.
* When a battery is connected and the Type-C cable is plugged in for charging:
  * The red light flashes.
* When the battery is fully charged via the Type-C connection:
  * The red light turns off.

### Reading Battery Voltage[​](https://wiki.seeedstudio.com/xiao_esp32c6_getting_started/#reading-battery-voltage) <a href="#reading-battery-voltage" id="reading-battery-voltage"></a>

To monitor the battery voltage on the XIAO ESP32C6, similar to the XIAO ESP32C3, you'll need to solder a 200k resistor in a 1:2 configuration. This setup reduces the voltage by half, allowing safe monitoring through the A0 analog port.
