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

# M5Stack Glass Unit w/ 1.51inch Transparent OLED

{% hint style="info" %}
[**View M5Stack Unit Glass M5-U158 1.51inch Transparent OLED Display on OpenELAB**](https://openelab.io/products/glass-unit-w-transparent-oled)

**Store SKU / option:** `M5-U158`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Glass Unit w/ 1.51inch Transparent OLED

***

### Product Link

{% embed url="https://openelab.io/products/glass-unit-w-transparent-oled" %}

### Introduction

Glass Unit is a transparent OLED expansion screen unit with a size of 1.51 inches. It is designed to provide a monochrome display with a resolution of 128x64 pixels. The transparent area of the screen measures 128x56 pixels, allowing for creative integration with other components or surfaces.

Glass Unit utilizes the STM32+SSD1309 driver scheme for efficient control and operation. The microcontroller unit (MCU) employed is the STM32F030F4P6, which not only drives the display but also integrates two input buttons and a buzzer, enabling user interaction and feedback.

The communication interface for control and firmware upgrades is I2C, with the module's address set to 0x3C. This facilitates easy integration and control of the transparent OLED screen extension. Glass Unit is well-suited for embedding in various home products or control devices as a display panel. Its transparent nature allows for unique visual effects and integration possibilities. With its compact size and versatile features, it can enhance the user experience and provide valuable information in different applications.

<figure><img src="../../.gitbook/assets/image (514).png" alt=""><figcaption></figcaption></figure>

### Features

* 128x56 transparent pixels (128x64 total pixels)
* Display area 35.5 x 18mm
* Glass area 42mm x 27.16mm
* 1-bit color depth
* I2C operation
* I2C Addresses: 0x3C
* Support for programming platforms：Arduino、UIFlow

### Specifications

| Resources             | Parameters                 |
| --------------------- | -------------------------- |
| MCU                   | STM32F030F4P6              |
| Screen                | 1.51 inch transparent OLED |
| resolution            | 128\*64                    |
| Display color         | blue                       |
| Display area          | 35.05\*18（mm）              |
| Panel size            | 42.04\*27.16\*1.25（mm）     |
| Perspective direction | Full view                  |
| Operating temperature | 0-40°C                     |
| Logic voltage         | 3.3V                       |
| I2C address           | 0x3C                       |
| Product Size          | 53\*42\*2.3mm              |
| Package Size          | 136mm × 92mm ×13mm         |
| Product Weight        | 10g                        |
| Package Weight        | 15.2g                      |

### Pinout

V：VCC

G：GND

C：SCL

D：SDA

### Dimensions

Size:10g

weight:53\*42\*2.3mm

## Official documentation and development resources

Use [Unit Glass](https://docs.m5stack.com/en/unit/Unit_Glass) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U158`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                          | Model-specific reference                                                                              |
| ----------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Electrical schematic                      | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/612/Sch_UNIT-GLASS.pdf)  |
| Arduino development tutorial              | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_glass)     |
| Official source: M5Unit-GLASS-Internal-FW | [Read official source: m5unit-glass-internal-fw](https://github.com/m5stack/M5Unit-GLASS-Internal-FW) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
