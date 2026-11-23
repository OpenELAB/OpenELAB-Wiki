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

# M5Stack ESP32 Core Ink

{% hint style="info" %}
[**View M5Stack CoreInk ESP32 E-Ink Development Kit E-paper on OpenELAB**](https://openelab.io/products/m5stack-esp32-core)

**Store SKU / option:** `M5-K048`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack ESP32 Core Ink Development Kit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-esp32-core" %}

### Description <a href="#description" id="description"></a>

**CoreInk** is a brand new E-ink display in the M5Stack cores range. Controlled by the ESP32-PICO-D4 This new device includes a 200x200 1.54" Black and White E-ink Display. Compared to a regular LCD,E-ink displays are easier on the eyes, which makes them a great choice for reading or viewing for longer periods. Other benefits are the low power consumption and the ability to retain the image even if power to the display is terminated。For control the CoreInk integrates an multi-function button,A physical button, integrated status LED and buzzer.The device also includes a 390mAh lithium polymer battery,RTC(BM8563)for controlling accurate timing and deep sleep functionality. CoreInk features independent reset and power buttons,expansion ports(HY2.0-4P,M-BUS,HAT expansion)for attaching external sensors to expand functionality,for unlimited possibilities。

Precautions |Please avoid long-time high-frequency refresh when using it. The recommended refresh interval is (15s/time). Do not expose to ultraviolet rays for a long time, otherwise it may cause irreversible damage to the ink screen. The low-power power management solution adopted by CoreInk is different from that of CORE and StickC devices. When in use, the PWR button is used as a power-on button(long press 2s). If you need to shut down the device, you need to use the software API or press the reset button on the back.

### Features <a href="#product-features" id="product-features"></a>

* ESP32 Standard wireless functions Wi-Fi
* Internal 4M Flash
* Low Power Display
* 180 degree viewing angle
* Expansion ports
* Built-in Magnet
* Internal Battery
* Expandable

### Application <a href="#application" id="application"></a>

* IoT Terminal
* E-Book
* Industrial Control Panel
* Electronic Tag

### Specification <a href="#specification" id="specification"></a>

| Resources        | Parameter                                                                                                                                                                                           |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ESP32-PICO-D4    | 240MHz dual core, 600 DMIPS, 520KB SRAM, Wi-Fi                                                                                                                                                      |
| Flash            | 4MB Flash                                                                                                                                                                                           |
| Input Voltage    | 5V @ 500mA                                                                                                                                                                                          |
| Ports            | TypeC\*1, HY2.0-4P\*1 , M-BUS Female Connector,Pin Array/ Hat Expansion                                                                                                                             |
| Screen           | GDEW0154M09 \| SPI Port \| 200\*200@1.54" \| Dpi:184 \| 1-bit Black & White(Grayscale:2) \ Viewing Area(mm):27.6x27.6 \| Dot pitch(mm) 0.138x0.138 \| Refresh Time（s） 0.82 /Partial refresh（s） 0.24 |
| Physical Buttons | Programmable \*1 , Reset \*1, Power \*1                                                                                                                                                             |
| LED              | Green LED x 1                                                                                                                                                                                       |
| RTC              | BM8563                                                                                                                                                                                              |
| Buzzer           | Passive Buzzer\*1                                                                                                                                                                                   |
| Wifi             | 2.4G 3D Antenna                                                                                                                                                                                     |
| PINS             | G25, G26, G36, G23, G34, G18, G21, G22, G14, G13                                                                                                                                                    |
| Battery          | 390mAh@3.7V                                                                                                                                                                                         |
| Working Temp     | 0°C to 60°C                                                                                                                                                                                         |
| Net Weight       | 32g                                                                                                                                                                                                 |
| Gross Weight     | 55g                                                                                                                                                                                                 |
| Dimensions       | 56\*40\*16mm                                                                                                                                                                                        |
| Package Size     | 82\*46\*20mm                                                                                                                                                                                        |
| Case Material    | Plastic ( PC )                                                                                                                                                                                      |

### Pin Map <a href="#pin-mapping" id="pin-mapping"></a>

**E-Ink Display**

Screen Resolution:200x200

| ESP32 Chip  | GPIO4 | GPIO0 | GPIO15 | GPIO9 | GPIO18 | GPIO23 |
| ----------- | ----- | ----- | ------ | ----- | ------ | ------ |
| GDEW0154M09 | BUSY  | RST   | D/C    | CS    | SCK    | MOSI   |

**Multi-function button & Physical Button & LED & Buzzer**

| ESP32 Chip            | GPIO37        | GPIO38       | GPIO39         | GPIO5           | GPIO10 | GPIO2  | GPI12 |
| --------------------- | ------------- | ------------ | -------------- | --------------- | ------ | ------ | ----- |
| Multi-function button | Left position | Button press | Right position | /               | /      | /      | /     |
| Physical Button       | /             | /            | /              | Physical Button | /      | /      | /     |
| LED                   | /             | /            | /              | /               | LED    | /      | /     |
| Buzzer                | /             | /            | /              | /               | /      | Buzzer | /     |
| Power Control         | /             | /            | /              | /               | /      | /      | MOS   |

**USB Serial**

| ESP32 Chip | GPIO1 | GPIO3 |
| ---------- | ----- | ----- |
| CP2104     | RXD   | TXD   |

**Internal I2C Connection**

| ESP32 Chip | GPIO21 | GPIO22 |
| ---------- | ------ | ------ |
| BM8563     | SDA    | SCL    |

### Coreink-HY2.0 4P Port <a href="#coreink-hy2.0-4p-port" id="coreink-hy2.0-4p-port"></a>

| PORT     | PIN    | Protocol |
| -------- | ------ | -------- |
| EXT-PORT | G32/33 | I2C      |

#### ESP32 ADC/DAC Mappable Pins <a href="#esp32-adc-dac-mappable-pins" id="esp32-adc-dac-mappable-pins"></a>

| ADC1      | ADC2               | DAC1      | DAC2      |
| --------- | ------------------ | --------- | --------- |
| 8 Channel | 10 Channel         | 2 Channel | 2 Channel |
| G32-39    | G0/2/4/12-15/25-27 | G25       | G26       |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/core/coreink/coreink_sch_02.webp" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/core/coreink/%E5%B0%BA%E5%AF%B8%E5%9B%BE.png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [CoreInk](https://docs.m5stack.com/en/core/CoreInk) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`K048`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                       |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/m5coreink/program)                                     |
| Electrical schematic         | [Read electrical schematic](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/schematic/Core/coreink/coreink_sch.pdf) |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/K048_CoreInk/Structures)             |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/K048_CoreInk/Structures/CoreInk.stl) |
| Official source: M5Unified   | [Read official source: m5unified](https://github.com/m5stack/M5Unified)                                                        |
| Official source: M5GFX       | [Read official source: m5gfx](https://github.com/m5stack/M5GFX)                                                                |
| Example source: M5Core-Ink   | [Read example source: m5core-ink](https://github.com/m5stack/M5Core-Ink/tree/master/examples/Basics/FactoryTest)               |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
