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

# M5Stack Station ESP32 IoT

{% hint style="info" %}
[**View M5Stack Station-485 ESP32 Industrial IoT Controller RS485 Development Kit on OpenELAB**](https://openelab.io/products/m5stack-station-esp32)

**Store SKU / option:** `M5-K123`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Station ESP32 IoT Development Kit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-station-esp32" %}

### Description <a href="#description" id="description"></a>

**M5Station-485** is a multi-purpose `industrial level` programmable embedded controller with Espressif `ESP32` SOC, integrated `Wi-Fi` solution, dual core low-power `Xtensa® 32-bit LX6` microprocessor, main frequency up to `240MHz`. Onboard `16M FLASH`, integrated `240*135 1.14" full colour HD IPS display` + `physical keypad` + `rich peripherals, two sets of six expansion ports`+ `Low-power sleep/wakeup function`. Multiple power supply options `USB Type-C, PWR485, External Battery (battery socket reserved on board)`. The integrated high power density boost DC/DC converter SCT12A0DHKR on board ensures the `stability` of the electrical equipment even in complex applications. This device is suitable for industrial control, intelligent buildings, multi-channel data acquisition nodes and prototyping applications.

* **HMI**:
  * 1.14" IPS display
  * 3 physical programmable keys
  * 1 ON/OFF button
  * 7 programmable RGB LEDs
* **Power supply**:
  * Input:
    * Integrated 9\~24V->5V DC/DC `SY8303` Buck circuit
    * `AXP192` power management chip
  * Output:
    * Each interface (6 Grove, 1 USB-A) is electronically switched on/off by `SGM2553D`.
    * `INA3221` for voltage/current acquisition for Grove interfaces, and `INA199` for current acquisition for the USB-A
    * Integrated high power density boost DC/DC converter `SCT12A0DHKR`
  * Low power consumption:
    * Integrated RTC `BM8563` to achieve low power sleep/wakeup function
* **Port Design**:
  * 6 way Grove expansion interface
    * Port A1/A2 shared the same power and signal pins
    * Port B1/B2/C1/C2 have separate power and signal pins
  * `PWR485` interface (4-wire - VH3.96)
    * RS485
    * 9\~24V power input
  * USB Tpye-A power supply output only, no signal pins
* **Mechnical Design**:
  * `Din rail`
  * `Magnet`
  * `Wall Mount`
  * `Screws`
  * `Ribbon`
* **Programming development**:
  * Supports `UIFlow graphical programming platform`, scripting, compile-free, cloud push
  * Fully compatible with Arduino, ESP32-IDF and other mainstream development platforms
  * Support FreeRTOS, with the help of dual-core and multitasking mechanism, efficient organization of task logic, optimize the execution efficiency of the program.

### Applications <a href="#applications" id="applications"></a>

* Industrial Controller
* Multi-channel data acquisition
* IoT product prototyping
* DIY/Prototyping

### Specification <a href="#specification" id="specification"></a>

| Spec                            | Parameters                                                                            |
| ------------------------------- | ------------------------------------------------------------------------------------- |
| ESP32-D0WDQ6-V3                 | 240MHz dual core, 600 DMIPS, 520KB SRAM, Wi-Fi                                        |
| Flash                           | 16MB                                                                                  |
| USB powered                     | 5V@1A                                                                                 |
| RS485 power supply              | 9\~24V@1A                                                                             |
| Interface                       | Type-C \* 1, GROVE(I2C+I/0+UART) \* 6, Full-Size USB Type-A(OUTPUT),PWR485            |
| LEDs                            | SK6812 \* 7                                                                           |
| Pushbuttons                     | Power Button, Physical Button \ 3                                                     |
| IPS LCD Screen                  | 1.14"@240\*135 ST7789V2                                                               |
| RTC                             | BM8563                                                                                |
| PMU                             | AXP192                                                                                |
| Voltage/Current Collector       | INA3221 + INA199                                                                      |
| USB Chips                       | CH9102F                                                                               |
| TTL-RS485                       | SP3485                                                                                |
| Step-Down Chips                 | SY8303                                                                                |
| DC/DC Boost                     | SCT12A0DHKR                                                                           |
| Power Distribution Switch       | SGM2553D                                                                              |
| Antenna                         | 2.4G 3D Antenna                                                                       |
| Operating Temperature           | 0°C to 60°C                                                                           |
| Base Screw Specification        | Hexagon socket cup head M2\*8 screw                                                   |
| Internal PCB reserved interface | Battery interface(Specification:1.25mm-4P)USB line interface(Specification:1.25mm-4P) |
| Net Weight                      | 63.1g                                                                                 |
| Gross Weight                    | 108.1g                                                                                |
| Product Dimensions              | 92 x 64.5 x 35 mm                                                                     |
| Package Size                    | 104.5 x 70.5 x 50mm                                                                   |
| Case Material                   | ABS+PC                                                                                |

### PinMap <a href="#pinmap" id="pinmap"></a>

**key BUTTON A & key BUTTON B & key BUTTON C & power button**

| ESP32 Chip | GPIO37   | GPIO38   | GPIO39   |
| ---------- | -------- | -------- | -------- |
| Key Pins   | BUTTON A | BUTTON B | BUTTON C |

**Color TFT screen**

Driver chip:ST7789v2 Resolution:135 \* 240 @1.14"

| ESP32 Chip  | GPIO5 | GPIO15 | GPIO18 | GPIO19 | GPIO23 |           |
| ----------- | ----- | ------ | ------ | ------ | ------ | --------- |
| AXP192 Chip |       |        |        |        |        | AXP\_LDO3 |
| LCD         | CS    | RESET  | SCK    | RS     | MOSI   | LCD\_BL   |

**RTC**

| ESP32 Chip | GPIO21 | GPIO22 |          |
| ---------- | ------ | ------ | -------- |
| BM8563     | SDA    | SCL    | INT      |
| AXP192     |        |        | AXP\_PWR |

**Current and Voltage Monitor**

| ESP32 Chip    | GPIO21 | GPIO22 | Control Channel                  |
| ------------- | ------ | ------ | -------------------------------- |
| INA3221(0x40) | SDA    | SCL    | AXP\_GPIO0,AXP\_GPIO1            |
| INA3221(0x41) | SDA    | SCL    | AXP\_GPIO2,AXP\_GPIO3,AXP\_GPIO4 |

**Internal I2C connection**

| ESP32 Chip | GPIO21 | GPIO22 |
| ---------- | ------ | ------ |
| AXP192     | SDA    | SCL    |
| BM8563     | SDA    | SCL    |
| INA3221    | SDA    | SCL    |

**PWR485**

| Chip   | GPIO3 | GPIO1 | GPIO2                                   | (DCDC 9\~24->5V) | GND |
| ------ | ----- | ----- | --------------------------------------- | ---------------- | --- |
| SP3485 | TXD   | RXD   | Send - High Level / Receive - Low Level |                  | GND |
| SY8303 |       |       |                                         | VIN\_12V         |     |

**Power Management Chips (AXP192)**

| RTC  | LCD BackLight | ESP32-3.3V SK6812,INA3221,CH902F |
| ---- | ------------- | -------------------------------- |
| LDO1 | LDO3          | DC-DC1                           |

**USB to Serial Port**

| ESP32 Chip | GPIO3 | GPIO1 |
| ---------- | ----- | ----- |
| CH9102F    | TXD   | RXD   |

M5Station Port Description

| PORT           | PIN             | Metering Port | Notes:  |
| -------------- | --------------- | ------------- | ------- |
| PORT-A1(red)   | G32/33(SDA/SCL) | AXP\_GPIO0    | I2C     |
| PORT-A2(red)   | G32/33(SDA/SCL) | AXP\_GPIO0    | I2C     |
| PORT-B1(black) | G25/35(OUT/IN)  | AXP\_GPIO1    | DAC/ADC |
| PORT-B2(black) | G26/36(OUT/IN)  | AXP\_GPIO2    | DAC/ADC |
| PORT-C1(blue)  | G14/13(TX/RX)   | AXP\_GPIO3    | UART    |
| PORT-C2(blue)  | G17/16(TX/RX)   | AXP\_GPIO4    | UART    |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/station_485/station_sch_04.webp" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/station_485/module%20size.jpg" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Station-485](https://docs.m5stack.com/en/core/Station-485) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K123`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                               |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5station/program)                                             |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/521/Sch_M5Station_v1.3.pdf)                               |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K123_Station-485/Structures)                 |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K123_Station-485/Structures/Station-485.stl) |
| Official source: M5Station   | [Read official source: m5station](https://github.com/m5stack/M5Station)                                                                |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
