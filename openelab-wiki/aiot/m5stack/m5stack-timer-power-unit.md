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

# M5Stack Timer Power Unit

{% hint style="info" %}
[**View M5Stack Timer Power Unit with OLED Display (INA3221) on OpenELAB**](https://openelab.io/products/m5stack-timer-power-unit-with-oled-display-ina3221)

**Store SKU / option:** `M5-U189`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Timer Power Unit with OLED Display (INA3221)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-timer-power-unit-with-oled-display-ina3221?_pos=1&_psq=Unit-Timer&_ss=e&_v=1.0" %}

### Description <a href="#description" id="description"></a>

The **TimerPWR Unit** is a timed power supply unit whose main functions are "**charging & discharging + timed switching + screen display + boost output.**" It features an internal STM32 microcontroller that implements RTC and overall control, allowing users to set automatic power on/off times as needed. It is powered via the **Type-C** interface and can be connected to an external rechargeable battery via a 1.25-2P interface. The unit includes a built-in battery charging circuit supporting a charging current of 330mA. It also features an integrated **DCDC boost** circuit that provides a 5V/800mA (1400mA @ 1C battery power) power output to external devices via the Grove port. Additionally, the **INA3221 sensor** is built-in, allowing real-time monitoring of power input and output current and voltage. The unit is equipped with a 0.66-inch **OLED** display and two side buttons for user interaction, making it easy to view real-time system status and modify settings. Users can set parameters such as power on/off using the side buttons or via the I2C bus through the Grove interface with I2C commands. This product is suitable for smart homes, industrial automation, and timed control devices.

### Features <a href="#features" id="features"></a>

* RTC cycle timing control
* Battery power supply
* Built-in DCDC boost circuit
* Current/voltage monitoring
* OLED display
* Grove interface
* Button-controlled power on/off mode

### Applications <a href="#applications" id="applications"></a>

* Timed control devices
* Portable electronic devices
* Powering sensor nodes

### Specifications <a href="#specifications" id="specifications"></a>

<table><thead><tr><th width="271">Specification</th><th>Parameters</th></tr></thead><tbody><tr><td>MCU</td><td>STM32G031G8U6</td></tr><tr><td>Input Voltage</td><td>Supports 5V DC input (via Type-C interface)</td></tr><tr><td>Output Voltage</td><td>Built-in DCDC boost circuit, output 5V for external devices</td></tr><tr><td>Battery Power Supply</td><td>3.7V Polymer Lithium Battery</td></tr><tr><td>Display Screen</td><td>0.66-inch OLED display, resolution 64x48, SPI communication</td></tr><tr><td>Interfaces</td><td>Type-C interface: for battery charging (cannot power Grove port directly)<br>Grove interface: for external sensors and modules, supports communication and power output<br>Battery interface: 1.25mm@2P</td></tr><tr><td>I2C Communication Address</td><td>0x56</td></tr><tr><td>Current Sensor</td><td>INA3221</td></tr><tr><td>Charging Current</td><td>DC5V@330mA</td></tr><tr><td>Charging Chip</td><td>LGS4056H</td></tr><tr><td>Charging Temperature</td><td>55°C</td></tr><tr><td>Grove Port Max Current Output</td><td>Dependent on battery capacity and discharge ability, e.g.:<br>1400mAh@1C 3.7V: DC4.96V@800mA<br>500mAh@1C 3.7V: DC4.97V@700mA<br>110mAh@1C 3.7V: DC5.03V@400mA</td></tr><tr><td>Standby Current</td><td>DC4.2V@36.67uA</td></tr><tr><td>Operating Temperature</td><td>0-40°C</td></tr><tr><td>Product Dimensions</td><td>40*24*11mm</td></tr><tr><td>Package Dimensions</td><td>136*92*14mm</td></tr><tr><td>Product Weight</td><td>7.6g</td></tr><tr><td>Package Weight</td><td>12.9g</td></tr></tbody></table>

![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/5.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/6.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/7.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/8.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/9.webp) ![](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/12.webp)

### Related Links <a href="#related-links" id="related-links"></a>

* [INA3221](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/ina3221.pdf)
* [LGS4056H](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/LGS4056H.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Unit-TimerPWR/img-9799cacb-c522-422d-a3d8-f38f278a739b.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

* PORT A Interface

| PORT A                  | SCL | SDA | VCC | GND |
| ----------------------- | --- | --- | --- | --- |
| Core (Basic)            | G22 | G21 | 5V  | GND |
| Core2                   | G33 | G32 | 5V  | GND |
| CoreS3                  | G1  | G2  | 5V  | GND |
| Atom Lite / Atom Matrix | G21 | G25 | 5V  | GND |
| AtomS3 / AtomS3 Lite    | G1  | G2  | 5V  | GND |
| StickC PLUS / PLUS2     | G33 | G32 | 5V  | GND |

* I2C\LED\BUTTON

| STM32G031G8U6           | PB6  | PB7  | PA11 | PA12 | PB4  | PA0    | PA4    |
| ----------------------- | ---- | ---- | ---- | ---- | ---- | ------ | ------ |
| I2C1(GROVE)             | SCL1 | SDA1 |      |      |      |        |        |
| I2C2(INA3221)           |      |      | SCL2 | SDA2 |      |        |        |
| LED(Charging indicator) |      |      |      |      | CHAG |        |        |
| Button A                |      |      |      |      |      | BTN\_A |        |
| Button B                |      |      |      |      |      |        | BTN\_B |

* OLED

| STM32G031G8U6 | PA2        | PA1       | PA6      | PA7       | PB0      | PB1    |
| ------------- | ---------- | --------- | -------- | --------- | -------- | ------ |
| OLED          | OLED\_MOSI | OLED\_SCK | OLED\_DC | OLED\_RST | OLED\_CS | BL\_EN |

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/%E5%8D%8F%E8%AE%AE.png" alt=""><figcaption></figcaption></figure>

* [TimerPWR Unit I2C Communication Protocol](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-TimerPWR/U189_UnitTimerPwr_I2C_Protocol_V1_20241018.pdf)

## Official documentation and development resources

Use [Unit TimerPWR](https://docs.m5stack.com/en/unit/Unit_TimerPWR) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U189`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                             | Model-specific reference                                                                                                                   |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files                       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U189_Unit_TimerPWR/Structures)                   |
| Mechanical / CAD files                       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U189_Unit_TimerPWR/Structures/Unit_TimerPWR.stl) |
| Official source: M5Unit-TimerPWR             | [Read official source: m5unit-timerpwr](https://github.com/m5stack/M5Unit-TimerPWR)                                                        |
| Arduino development tutorial                 | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_timer_pwr)                                      |
| Official source: M5Unit-TimerPWR-Internal-FW | [Read official source: m5unit-timerpwr-internal-fw](https://github.com/m5stack/M5Unit-TimerPWR-Internal-FW)                                |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
