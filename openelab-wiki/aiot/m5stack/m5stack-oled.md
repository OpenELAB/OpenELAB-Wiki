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

# M5Stack OLED

{% hint style="info" %}
[**View M5Stack OLED Unit 1.3" 128 × 64 Display on OpenELAB**](https://openelab.io/products/m5stack-oled-unit-display)

**Store SKU / option:** `M5-U119`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack OLED Unit 1.3" 128 × 64 Display

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-oled-unit-display" %}

### Description <a href="#description" id="description"></a>

**Unit OLED** is a 1.3-inch OLED expansion screen unit. It adopts SH1107 drive scheme, supports black/white display, and the resolution is 128\*64. The driver chip selects the I2C communication interface, and the user can mount it to the I2C bus of the existing device when in use, which saves IO. The back of the screen is integrated with a magnetic design, which can easily be fixed on the metal surface by adsorption. The OLED screen extension is suitable for being embedded in various instruments or control devices that need to display simple content as a display panel.

### Features <a href="#features" id="features"></a>

* OLED display panel
* SH1107 drive scheme
* Display color: black/white
* I2C communication interface
* 128\*64 resolution
* Viewing angle: full viewing angle
* Magnetic back design

### Applications <a href="#applications" id="applications"></a>

* Information display

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications         | Parameter         |
| ---------------------- | ----------------- |
| Working current        | 58mA              |
| Communication protocol | I2C address: 0x3C |
| Display size           | 14.7 × 29.42（mm）  |
| Pixel pitch            | 0.17×0.17（mm）     |
| Pixel size             | 0.15×0.15（mm）     |
| Viewable               | Full view         |
| Operating temperature  | 0°C to 60°C       |
| Net weight             | 9.3g              |
| Gross weight           | 20g               |
| Product Size           | 24\*56\*8mm       |
| Package Size           | 67\*53\*12mm      |
| Case material          | Plastic ( PC )    |

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(PORT A) | GPIO22 | GPIO21 | 5V | GND |
| -------------- | ------ | ------ | -- | --- |
| Unit OLED      | SCL    | SDA    | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/oled/oled_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/oled/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (957).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit OLED](https://docs.m5stack.com/en/unit/Unit_OLED) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U119`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                           |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/594/Sch_UNIT_OLED_v1.1.pdf)                           |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U119_Unit_OLED/Structures)               |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U119_Unit_OLED/Structures/Unit_OLED.stl) |
| Official source: M5GFX       | [Read official source: m5gfx](https://github.com/m5stack/M5GFX)                                                                    |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_oled)                                   |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
