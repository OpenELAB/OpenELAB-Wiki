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

# M5Stack Core2

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5Stack Core2 ESP32 IoT Development Kit

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**M5Core2** is the second generation core device in the M5Stack development kit series, which further enhances the functions of the original generation of cores.

The MCU is an ESP32 model D0WDQ6-V3 and has dual core Xtensa® 32-bit 240Mhz LX6 processors that can be controlled separately. Wi-Fi are supported as standard and it includes an on board 16MB Flash and 8MB PSRAM, USB TYPE-C interface for charging, downloading of programs and serial communication, a 2.0-inch integrated capacitive touch screen, and a built-in vibration motor.

M5Core2 also features a built-in RTC module which can provide accurate timing. The power supply is managed by an AXP192 power management chip, which can effectively control the power consumption of the base and a built-in green LED power indicator helps to notify the user of battery level. The battery capacity has been upgraded to 390mAh, which can power the core for much longer than the previous model.

The M5Core2 retains the TF-card(microSD) slot and speakers. However, in order to ensure higher quality sound output, the I2S digital audio interface power amplifier chip is used to effectively prevent signal distortion. There are independent power and reset buttons on the left side and bottom of the base.

The 3 icons on the front of the screen are capacitive buttons which are programmable. There is a small expansion board on the back of the base with a 6-axis IMU sensor and microphone. The development platform and programming language supported by M5Stack Core2: Arduino, [UIFlow ](http://flow.m5stack.com/)(using Blockly, MicroPython language) No matter what level of your development and programming skills, M5Stack will help You gradually turn your ideas into reality.

**Operations:**\
Power on: One click the power button on the left

Power off: Long press the left power button for 6 seconds

Reset: Click the RST button on the bottom side

### Features <a href="#product-features" id="product-features"></a>

* ESP32-based, built-in Wi-Fi
* 16M Flash,8M PSRAM
* Built-in speaker, power indicator, vibration motor, RTC, I2S amplifier, capacitive touch screen, power button, reset button
* TF card slot (16G Maximum size)
* Built-in lithium battery, equipped with power management chip
* Independent small board built-in 6-axis IMU, PDM microphone
* M-Bus Socket & Pins

### Applications <a href="#applications" id="applications"></a>

* Internet of things terminal controller
* Stem education product
* DIY creation
* Smart home equipment

### Specification <a href="#specification" id="specification"></a>

| Resources                             | Parameter                                                                                            |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| ESP32-D0WDQ6-V3                       | 240MHz dual core, 600 DMIPS, 520KB SRAM, Wi-Fi                                                       |
| Flash                                 | 16MB                                                                                                 |
| PSRAM                                 | 8MB                                                                                                  |
| Input Voltage                         | 5V @ 500mA                                                                                           |
| Interface                             | TypeC x 1, GROVE(I2C+I/0+UART) x 1                                                                   |
| IPS LCD Screen                        | 2.0"@320\*240 ILI9342C                                                                               |
| Touch Screen                          | FT6336U                                                                                              |
| Speaker                               | 1W-092                                                                                               |
| LED                                   | Green power indicator light                                                                          |
| Button                                | Power button, RST button, Virtual screen button\*3                                                   |
| Vibration reminder                    | Vibration motor                                                                                      |
| MIC                                   | SPM1423                                                                                              |
| I2S Power Amplifier                   | NS4168                                                                                               |
| 6-axis IMU                            | MPU6886                                                                                              |
| RTC                                   | BM8563                                                                                               |
| PMU                                   | AXP192                                                                                               |
| USB Chip                              | CP2104/CH9102F (two chip versions, there is no difference in function and use)                       |
| DC-DC Boost                           | SY7088                                                                                               |
| TF card slot                          | 16G Max                                                                                              |
| Lithium Battery                       | 500mAh @ 3.7V                                                                                        |
| Antenna                               | 2.4G 3D antenna                                                                                      |
| Operating temperature                 | 0°C to 60°C                                                                                          |
| Base screw specifications             | Hexagon socket countersunk head M3                                                                   |
| Internal PCB board reserved interface | <p>Battery interface (specification: 1.25mm-2P)<br>USB line interface (specification: 1.25mm-4P)</p> |
| Net Weight                            | 52g                                                                                                  |
| Gross Weight                          | 76g                                                                                                  |
| Product Size                          | 54 x 54 x 16.5mm                                                                                     |
| Package Size                          | 75 x 60 x 20mm                                                                                       |
| Case Material                         | Plastic ( PC )                                                                                       |

![](https://static-cdn.m5stack.com/resource/docs/products/core/core2/core2_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/core/core2/core2_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/core/core2/core2_06.webp)

### PinMap <a href="#pinmap" id="pinmap"></a>

**LCD & TF card**

LCD :320x240 TF card Maximum size 16GB

| ESP32 Chip  | GPIO38 | GPIO23 | GPIO18 | GPIO5 | GPIO15 |          |          |           |
| ----------- | ------ | ------ | ------ | ----- | ------ | -------- | -------- | --------- |
| AXP192 Chip |        |        |        |       |        | AXP\_IO4 | AXP\_DC3 | AXP\_LDO2 |
| ILI9342C    | MISO   | MOSI   | SCK    | CS    | DC     | RST      | BL       | PWR       |

| ESP32 Chip | GPIO38 | GPIO23 | GPIO18 | GPIO4 |
| ---------- | ------ | ------ | ------ | ----- |
| TF Card    | MISO   | MOSI   | SCK    | CS    |

**CAP.TOUCH (I2C Addr: 0x38)**

| ESP32 chip | GPIO21 | GPIO22 | GPIO39 |          |
| ---------- | ------ | ------ | ------ | -------- |
| AXP192     |        |        |        | AXP\_IO4 |
| FT6336U    | SDA    | SCL    | INT    | RST      |

**Mic & NS4168(Speaker)**

| ESP32 Chip | GPIO12 | GPIO0 | GPIO2 | AXP\_IO2 | GPIO34 |
| ---------- | ------ | ----- | ----- | -------- | ------ |
| NS4168     | BCLK   | LRCK  | DATA  | SPK\_EN  |        |
| Mic        |        | CLK   |       |          | DATA   |

**AXP Power Indicator Light**

| AXP192          | AXP\_IO1 | AXP\_LDO3 |
| --------------- | -------- | --------- |
| Green LED       | Vcc      |           |
| Vibration motor |          | Vcc       |

**RTC**

| ESP32 Chip | GPIO21 | GPIO22 |          |
| ---------- | ------ | ------ | -------- |
| AXP192     |        |        | AXP\_PWR |
| BM8563     | SDA    | SCL    | INT      |

**IMU(3-axis gyroscope & 3-axis accelerometer)**

| ESP32 Chip | GPIO21 | GPIO22 |
| ---------- | ------ | ------ |
| MPU6886    | SDA    | SCL    |

**USB to serial chip**

| ESP32 Chip     | GPIO1 | GPIO3 |
| -------------- | ----- | ----- |
| CP2104/CH9102F | RXD   | TXD   |

**Internal I2C connection**

| ESP32 Chip | GPIO21 | GPIO22 |
| ---------- | ------ | ------ |
| MPU6886    | SDA    | SCL    |
| AXP192     | SDA    | SCL    |
| BM8563     | SDA    | SCL    |
| FT6336U    | SDA    | SCL    |

#### M5Core2 M-BUS Schematic diagram <a href="#m5core2-m-bus-schematic-diagram" id="m5core2-m-bus-schematic-diagram"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/core2/core2_mbus_01.webp" alt=""><figcaption></figcaption></figure>

#### M5Core2 BUS(compared to M5Stack) <a href="#m5core2-bus-compared-to-m5stack" id="m5core2-bus-compared-to-m5stack"></a>

<figure><img src="https://www.gwendesign.com/kb/m5stack/img/M5StackM5Core2GPIO.png" alt=""><figcaption></figcaption></figure>

**M5PORT DEFINE**

| PORT          | PIN   | Note:  |
| ------------- | ----- | ------ |
| PORT-A(Red)   | 32/33 | I2C    |
| PORT-B(Black) | 26/36 | DAC/AD |
| PORT-C(Blue)  | 13/14 | UART   |

#### ESP32 ADC/DAC <a href="#esp32-adc-dac" id="esp32-adc-dac"></a>

| ADC1       | ADC2               | DAC1       | DAC2       |
| ---------- | ------------------ | ---------- | ---------- |
| 8 channels | 10 channels        | 2 channels | 2 channels |
| G32-39     | G0/2/4/12-15/25-27 | G25        | G26        |

**Charging current measured value**

| charging current | Fully charged current(Power OFF) | Fully charged current(Power ON） |
| ---------------- | -------------------------------- | ------------------------------- |
| 0.219A           | 0.055A                           | 0.147A                          |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/core2/core2_sch_01.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/core2/core2_sch_02.webp" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/core2/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Core2](https://docs.m5stack.com/en/core/Core2) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K010`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                   |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5core2/program)                                   |
| Official source: M5Tools     | [Read official source: m5tools](https://github.com/m5stack/M5Tools)                                                        |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K010_Core2/Structures)           |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K010_Core2/Structures/Core2.stl) |
| Official source: M5Core2     | [Read official source: m5core2](https://github.com/m5stack/M5Core2)                                                        |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5core2/button)                                    |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
