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

# M5Stack CoreS3 ESP32S3 loT Development

{% hint style="info" %}
[**View M5Stack CoreS3 (ESP32-S3) on OpenELAB**](https://openelab.io/products/m5stack-cores3-esp32s3)

**Model/option:** M5Stack CoreS3 (ESP32-S3) · **Top-200 SKU:** `M5-K128`
{% endhint %}

## M5Stack CoreS3 ESP32S3 loT Development Kit

***

## Product Link

{% embed url="https://openelab.io/products/m5stack-cores3-esp32s3" %}

## Description <a href="#description" id="description"></a>

CoreS3 is the third generation of the M5Stack Core series. Powered by the ESP32-S3 solution, this kit features a dual-core Xtensa LX7 processor running at 240MHz. CoreS3 comes equipped with built-in Wi-Fi functionality, enabling seamless connectivity. It boasts 16MB of onboard flash memory and 8MB of PSRAM, providing ample space for program storage.

CoreS3 offers convenient programming options through its TYPE-C interface, supporting OTG and CDC functions. This allows for easy connection with external USB devices and hassle-free firmware flashing. CoreS3 features a 2.0-inch capacitive touch IPS screen, protected by high-strength glass material. Additionally, a 30W pixel camera GC0308 is integrated at the bottom of the screen, accompanied by a proximity sensor LTR-553ALS-WA for enhanced functionality. Power management is handled by the AXP2101 power management core chip, employing a 4-way power flow control loop for efficient power distribution. The overall design emphasizes low power consumption. CoreS3 also features a 6-axis attitude sensor BMI270 and a magnetometer BMM150 for precise motion detection. With the onboard TF-card (microSD) card slot and BM8563 RTC chip, accurate timing and sleep-timer wake-up functions are readily available.

Sound output on CoreS3 is optimized with the high-fidelity 16-bit I2S power amplifier chip AW88298, accompanied by a built-in 1W speaker for clear audio playback. For sound input, the kit incorporates the ES7210 audio decoding chip and dual-microphone input. The side of the device includes an independent power button and restart (RST) button, complemented by a self-built delay circuit. By long-pressing the reset button, users can easily enter the program download mode. The CoreS3 kit comes with the DinBase Base, providing convenient options for Din rail, wall, and screw fixing. It can be powered by an external DC 12V (supports 9\~24V) or an internal 500mAh lithium battery. The DinBase also offers multiple proto locations for users to customize and expand their projects. CoreS3 is an ideal choice for IoT development, various DIY project development, smart home control systems, and industrial automation control systems.

## Features <a href="#features" id="features"></a>

* Developed based on ESP32, support WiFi @16M Flash, 8M PSRAM
* Built-in camera, proximity sensor, speaker, power indicator, RTC, I2S amplifier, dual microphone, condenser touch screen, power button, reset button, gyroscope
* TF card slot
* High-strength glass
* Support OTG and CDC functions
* AXP2101 power management, low power design
* Supported programming platforms: Arduino, UIFlow

## Applications <a href="#applications" id="applications"></a>

* IoT development
* Various DIY project development
* Smart home control system
* Industrial automation control system

## Specifications <a href="#specifications" id="specifications"></a>

| Resources                | Parameters                                                                           |
| ------------------------ | ------------------------------------------------------------------------------------ |
| SoC                      | ESP32-S3@Xtensa LX7, 16MFLASH AND 8M-PSRAM, WIFI, OTG\CDC functions                  |
| Touch the IPS LCD screen | 2.0"@320\*240 ILI9342C                                                               |
| Camera                   | GC0308@300000 pixels                                                                 |
| Proximity sensors        | LTR-553ALS-WA                                                                        |
| Power management chip    | AXP2101                                                                              |
| Six-axis attitude sensor | BMI270                                                                               |
| Three-axismagnetometer   | BMM150                                                                               |
| RTC                      | BM8563                                                                               |
| Speaker                  | 16bits-I2S power amplifier chip AW88298@1W                                           |
| Audio decoding chip      | ES7210, dual microphone inputs                                                       |
| Product Size             | 54 x 54 x 16mm                                                                       |
| Product Size             | <p>Full Assembly Kit(CoreS3+DinBase):54 * 54 * 31.5mm<br>CoreS3:54 * 54 * 15.5mm</p> |
| Package Size             | 101\*64\*34mm                                                                        |
| Product Weight           | 73.3g                                                                                |
| Package Weight           | 97.8g                                                                                |

## I2C Address <a href="#i2c-address" id="i2c-address"></a>

| Chip         | ADDRESS |
| ------------ | ------- |
| GC0308 ADDR  | 0X21    |
| LTR553 ADDR  | 0x23    |
| AXP2101 ADDR | 0x34    |
| AW88298 ADDR | 0x36    |
| FT6336 ADDR  | 0x38    |
| ES7210 ADDR  | 0x40    |
| BM8563 ADDR  | 0x51    |
| AW9523 ADDR  | 0x58    |
| BMI270 ADDR  | 0x69    |
| BMM150 ADDR  | 0x10    |

## PinMap <a href="#pinmap" id="pinmap"></a>

**LCD Screen & TF Card**

LCD Pixel:320x240 TF cards support up to 16GB

| ESP32S3 Chip | GPIO37    | GPIO36   | GPIO3 | GPIO35    |                |                |              | GPIO4  |
| ------------ | --------- | -------- | ----- | --------- | -------------- | -------------- | ------------ | ------ |
| AW9523B      |           |          |       |           | AW9523B\_P1\_1 |                |              |        |
| AXP2101      |           |          |       |           |                | AXP2101\_DLDO1 | AXP2101\_LX1 |        |
| ILI9342C     | MOSI      | SCK      | CS    | DC        | RST            | BL             | PWR          |        |
| TF Card      | SPI\_MOSI | SPI\_SCK |       | SPI\_MISO |                |                |              | TF\_CS |

**Camera & Proximity sensors LTR-553ALS-WA**

| ESP32S3 Chip  | GPIO12        | GPIO11        | AW9523B\_P1\_0 | GPIO45    | GPIO46     | GPIO38    |
| ------------- | ------------- | ------------- | -------------- | --------- | ---------- | --------- |
| GC0308        | I2C\_SYS\_SDA | I2C\_SYS\_SCL | CAM\_RST       | CAM\_PCLK | CAM\_VSYNC | CAM\_HREF |
| LTR-553ALS-WA | I2C\_SYS\_SDA | I2C\_SYS\_SCL |                |           |            |           |

The LTR-553ALS-WA proximity sensor and camera are integrated in a single line, using I2C for communication, and the detailed communication address is shown in the table above.

**CAP.TOUCH (I2C Addr: 0x38)**

| ESP32S3 chip | GPIO12        | GPIO11        | AW9523B\_P1\_2 | AW9523B\_P0\_0 |
| ------------ | ------------- | ------------- | -------------- | -------------- |
| FT6336U      | I2C\_SYS\_SDA | I2C\_SYS\_SCL | TOUCH\_INT     | TOUCH\_RST     |

**Microphone & amplifier**

| ESP32S3 Chip  | GPIO12        | GPIO11        | GPIO34   | GPIO33   | GPIO13    | GPIO14    | GPIO0     | AW9523B\_P1\_3 | AW9523B\_P0\_2 |
| ------------- | ------------- | ------------- | -------- | -------- | --------- | --------- | --------- | -------------- | -------------- |
| ES7210(0x40)  | I2C\_SYS\_SDA | I2C\_SYS\_SCL | I2S\_BCK | I2S\_WCK | I2S\_DATO |           | I2S\_MCLK |                |                |
| AW88298(0x36) | I2C\_SYS\_SDA | I2C\_SYS\_SCL | I2S\_BCK | I2S\_WCK |           | I2S\_DAT1 |           | AW\_INT        | AW\_RST        |

**AXP Power Led**

| AXP2101 | AXP\_CHG\_LED |
| ------- | ------------- |
| Red LED | RTC\_VDD      |

**RTC**

| ESP32S3 Chip | GPIO12        | GPIO11        | AXP2101\_IRQ |
| ------------ | ------------- | ------------- | ------------ |
| BM8563       | I2C\_SYS\_SDA | I2C\_SYS\_SCL | AXP\_WAKEUP  |

**IMU (6-axis gyroscope + 3-axis accelerometer)**

| ESP32S3 Chip   | GPIO12        | GPIO11        |
| -------------- | ------------- | ------------- |
| BMI270\&BMM150 | I2C\_SYS\_SDA | I2C\_SYS\_SCL |

**Internal I2C connection**

| ESP32S3 Chip   | GPIO12        | GPIO11        |
| -------------- | ------------- | ------------- |
| BMI270\&BMM150 | I2C\_SYS\_SDA | I2C\_SYS\_SCL |
| AXP2101        | I2C\_SYS\_SDA | I2C\_SYS\_SCL |
| BM8563         | I2C\_SYS\_SDA | I2C\_SYS\_SCL |
| ES7210         | I2C\_SYS\_SDA | I2C\_SYS\_SCL |
| AW88298        | I2C\_SYS\_SDA | I2C\_SYS\_SCL |

**PORT**

| Port          | Pin     | NOTE        |
| ------------- | ------- | ----------- |
| PORT-A(RED)   | G2/G1   | I2C         |
| PORT-B(BLACK) | G9/G8   | GPIO        |
| PORT-C(BLUE)  | G18/G17 | UART(RX/TX) |

## M5CoreS3 M-BUS Schematic diagram <a href="#m5cores3-m-bus-schematic-diagram" id="m5cores3-m-bus-schematic-diagram"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/M5CORES3%20SE/c9024cfa50b8d7c31ca7505668770ee.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (969).png" alt=""><figcaption></figcaption></figure>

## Power Management <a href="#power-management" id="power-management"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/CoreS3/%E7%94%B5%E6%BA%90.png" alt=""><figcaption></figcaption></figure>

## Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/CoreS3/img-513d30d4-3378-44b9-9d75-4f3f3ac6fb1f.png" alt=""><figcaption></figcaption></figure>

* [Complete schematic pdf](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/Sch_M5_CoreS3_v1.0.pdf)

## Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/CoreS3/%E5%B0%BA%E5%AF%B8%E5%9B%BE.png" alt=""><figcaption></figcaption></figure>

## Related Link <a href="#related-link" id="related-link"></a>

* [LTR-553ALS-WA](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/LTR-553ALS-WA.PDF)
* [GC0308](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/GC0308.PDF)
* [ES7210](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/ES7210.PDF)
* [BMM150](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/BMM150.PDF)
* [BMI270](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/BMI270.PDF)
* [AXP2101](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/AXP2101_Datasheet_V1.0_en.pdf)
* [AW88298](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/core/K128%20CoreS3/AW88298.PDF)
* [AW9523B](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/CoreS3/AW9523B-EN.pdf)

## Official documentation and development resources

Use [CoreS3](https://docs.m5stack.com/en/core/CoreS3) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K128`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                     |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5cores3/program)                                    |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5cores3/power)                                      |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/490/Sch_M5_CoreS3_v1.0.pdf)                     |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/559/SCH_DinBase_V1.1.pdf)                       |
| Mechanical / CAD files       | [Read mechanical / cad files](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/CoreS3/cores3.dxf)    |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K128_CoreS3/Structures)            |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K128_CoreS3/Structures/CoreS3.stl) |
| Official source: M5CoreS3    | [Read official source: m5cores3](https://github.com/m5stack/M5CoreS3)                                                        |
| Official source: M5Unified   | [Read official source: m5unified](https://github.com/m5stack/M5Unified)                                                      |
| Official source: M5GFX       | [Read official source: m5gfx](https://github.com/m5stack/M5GFX)                                                              |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
