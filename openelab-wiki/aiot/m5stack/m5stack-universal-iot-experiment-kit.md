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

# M5Stack Universal IOT Experiment Kit

{% hint style="info" %}
[**View M5Stack Universal IOT Experiment Kit for ESP32 on OpenELAB**](https://openelab.io/products/universal-iot-experiment-kit)

**Store SKU / option:** `M5-K024-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Universal IOT Experiment Kit for ESP32

***

### Product Link

{% embed url="https://openelab.io/products/universal-iot-experiment-kit" %}

### Description <a href="#description" id="description"></a>

**Demo Board**. This is a feast of IoT stuff, powered by M5Stack. It is an all-in-one Learning board powered by ESP32, which includes anything you can imagine in an IoT + industrial application scenarios. Let's see what you can do with it: Robotic movement, the most commonly used serial communication port(RS485 RS232), Relay control, all different types of Button control, RF reader, speaker, Microphone and more all able to develope by an M5stack core device, so you can program this board with Blockly(UIFlow), Arduino, and Micropython. Based on application scenarios, we've partitioned them into different functional parts with the good-looking layout and full-function performance. Here comes the most powerful IIoT learning board.

### Features <a href="#features" id="features"></a>

* Fully Compatible with the M5Stack stackable and extendable system
* Protoboard, M5-BUS extension
* Each module comes with an individual power switch.
* Environment Sensor set ( Temperature, Humility, barometric pressure, light intensity, and Microphone )
* Joystick Controller
* 8 Channel of Relay output
* 4x DAC,4x ADC
* 4x4 button matrix
* 8x8 RGB LED matrix
* Encoder
* 1x Servo
* DC-Motor(with feedback encoder)
* step motor with four-phase five-wire
* Radio frequency identification Reader
* RS-485,RS232 series communication

### Applications <a href="#applications" id="applications"></a>

* IOT teaching experiment board
* Multi function test board

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter      |
| ------------ | -------------- |
| Net weight   | 1120g          |
| Gross weight | 1120g          |
| Product Size | 330\*210\*95mm |
| Package Size | 330\*210\*95mm |

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/app/demo-board_sht30/demo-board_sht30_09.webp" alt=""><figcaption></figcaption></figure>

### Module parameters <a href="#module-parameters" id="module-parameters"></a>

| **Module Name** | **working Voltage** |                   **Parameter**                   |
| :-------------: | :-----------------: | :-----------------------------------------------: |
|       ADC       |          5V         |                4x ADC port/ADS1115                |
|       DAC       |          5V         |                4x DAC port/DAC6574                |
|     Joystick    |         3.3V        | axis-X/Y potentiometer input, axis-Z button input |
|      SHT30      |         3.3V        |                  I2C address 0x44                 |
|     QMP6988     |         3.3V        |                  I2C address 0x76                 |
|      Light      |         3.3V        |    A/D sampling supported, adjustable threshold   |
|    Microphone   |         3.3V        |    A/D sampling supported, adjustable threshold   |
|      Relay      |          5V         |          8 channels /3A-220V-AC/3A-30V-DC         |
|     RGB LED     |          5V         |                   8x8 LED matrix                  |
|      Servo      |          5V         |                    10KG torsion                   |
|     DC-Motor    |          5V         |             feedback encoder/LV8548MC             |
|    Stepmotor    |          5V         |              4-phase 5 wires LV8548MC             |
|       RFID      |         3.3V        |       Read & Write distance: < 8 cm/ MFRC522      |
|      RS485      |          5V         |                   SP485EEN-L/TR                   |
|      RS232      |          5V         |                     MAX232ESE                     |
|      Encode     |                     |                   Encoder button                  |
|      Proto      |                     |                     170x holes                    |
|     Keyboard    |                     |                 4x4 button matrix                 |

### **Datasheets**

* [ADS1115](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/application/ads1115_en.pdf)
* [DAC6574](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/application/dac6574_en.pdf)
* [LV8548MC](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/application/LV8548MC_en.pdf)
* [TPS54360](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/application/tps54360_en.pdf)
* [MRC522](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/MFRC522_en.pdf)
* [MAX232ESE](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/application/MAX232ESE_en.pdf)
* [MAX4466](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/application/MAX4466_datasheet_en.pdf)
* [SP485EEN](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/hat/SP485EEN_en.pdf)
* [BMP280](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/hat/BMP280-DS001-11_en.pdf)
* [SHT30](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/SHT3x_Datasheet_digital.pdf)

### Schematics <a href="#schematics" id="schematics"></a>

* [M5IoT-kit](https://github.com/m5stack/M5-Schematic/tree/master/Applications/M5IoT-kit)

## Official documentation and development resources

Use [Demo Board-SHT30](https://docs.m5stack.com/en/app/Demo_Board-SHT30) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K024-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need            | Model-specific reference                                                                                   |
| --------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Electrical schematic        | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/634/Sch_Demo_Board-SHT30.pdf) |
| Official source: DEMO-BOARD | [Read official source: demo-board](https://github.com/m5stack/DEMO-BOARD)                                  |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
