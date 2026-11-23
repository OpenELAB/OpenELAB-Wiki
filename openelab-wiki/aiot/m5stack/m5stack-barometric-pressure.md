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

# M5Stack Barometric Pressure

{% hint style="info" %}
[**View M5Stack Barometric Pressure 2 Unit QMP6988 Atmospheric Pressure Sensor on OpenELAB**](https://openelab.io/products/barometric-pressure-2-unit)

**Store SKU / option:** `M5-U090-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Barometric Pressure 2 Unit (QMP6988)

***

### Product Link <a href="#description" id="description"></a>

{% embed url="https://openelab.io/products/barometric-pressure-2-unit" %}

### Description <a href="#description" id="description"></a>

Barometric Pressure Unit is a barometer unit that uses QMP6988 barometric pressure sensor to measure atmospheric pressure and altitude estimation, with a relative accuracy of ±0.039hPa (±0.12hPa, equivalent to ±1m height difference), a wide measurement range, and an integrated temperature sensor inside the chip, while the Absolute temperature accuracy is 2°C.

### Features <a href="#features" id="features"></a>

* Built-in temperature and pressure sensors
* High precision (pressure accuracy: ±0.039hPa; Absolute Temperature accuracy: 2°C)
* Low current consumption: 21.4uA
* Development platform: Arduino, UIFlow (Blockly, Python)
* 2x LEGO™ compatible holes

### Applications <a href="#applications" id="applications"></a>

* Indoor navigation (floor detection)
* Altimeter
* Weather forecast

### Specification <a href="#specification" id="specification"></a>

| Resources                     | Parameters             |
| ----------------------------- | ---------------------- |
| Sensor                        | QMP6988                |
| LDO                           | HT7533                 |
| Operating Pressure Range      | 30kPa to 110kPa        |
| Relative Pressure Accuracy    | ±3.9                   |
| Pressure Resolution           | Temperature Resolution |
| Temperature Resolution        | 0.0002°C               |
| Temperature measurement range | -40-80°C               |
| I2C Address                   | 0x56                   |
| voltage support               | 5v                     |
| Product Size                  | 24mm × 24mm ×8.1mm     |
| Package Size                  | 136mm × 92mm × 13mm    |
| Product Weight                | 3.3g                   |
| Package Weight                | 6.9g                   |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/BPS(QMP6988)/img-4e77d8e1-09d6-43d6-a0da-d7e15d171c79.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/BPS(QMP6988)/img-b2c73882-6358-4799-bec0-c5ca736dfc20.png" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (400).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Mini BPS v1.1](https://docs.m5stack.com/en/unit/Unit_Mini_BPS_v1.1) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U090-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                               |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U090-B_Unit_Mini_BPS_v1.1/Structures)                        |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U090-B_Unit_Mini_BPS_v1.1/Structures/Unit_Mini_BPS_v1.1.stl) |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/mini_unit_bps)                                                   |
| Example source: M5Unit-ENV   | [Read example source: m5unit-env](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Unit_BPS1.1_M5Core)                                       |
| Example source: M5Unit-ENV   | [Read example source: m5unit-env](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Unit_BPS1.1_M5Atom)                                       |
| Example source: M5Unit-ENV   | [Read example source: m5unit-env](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Unit_BPS1.1_M5AtomS3)                                     |
| Example source: M5Unit-ENV   | [Read example source: m5unit-env](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Unit_BPS1.1_M5AtomS3Lite)                                 |
| Example source: M5Unit-ENV   | [Read example source: m5unit-env](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Unit_BPS1.1_M5Core2)                                      |
| Example source: M5Unit-ENV   | [Read example source: m5unit-env](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Unit_BPS1.1_M5StickC)                                     |
| Example source: M5Unit-ENV   | [Read example source: m5unit-env](https://github.com/m5stack/M5Unit-ENV/tree/master/examples/Unit_BPS1.1_M5StickCPlus)                                 |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
