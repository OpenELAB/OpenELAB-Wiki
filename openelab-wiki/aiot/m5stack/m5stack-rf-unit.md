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

# M5Stack RF Unit

{% hint style="info" %}
[**View M5Stack RF UNIT 433MHz Transmitter on OpenELAB**](https://openelab.io/products/m5stack-rf-unit)

**Store SKU / option:** `M5-U114`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack RF UNIT 433MHz Transmitter

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-rf-unit" %}

### Description <a href="#description" id="description"></a>

**RF433T** is a radio frequency (RF) transmitter, using SYN115 radio frequency transmitter IC, working frequency is 433.92MHz (using ASK modulation) commonly used by wireless controllers, built-in PCB antenna, stable signal transmission distance up to 10M, The output power reaches 10dBm. The exquisite and compact housing design can be embedded in a variety of radio frequency remote control applications. It is suitable for security alarm, wireless automatic meter reading, home and industrial automation, remote remote control, wireless data transmission and other system fields.

### Features <a href="#features" id="features"></a>

* Working frequency: 433.92MHz
* Data transmission rate 10kbps (ASK modulation)
* Output power 10dBm
* PCB antenna

### Applications <a href="#applications" id="applications"></a>

* Building Automation
* Security alarm
* Home and industrial automation
* Remote control
* Wireless data transmission and other system fields

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                     | Parameter     |
| ----------------------------- | ------------- |
| Transmitter IC                | SYN115        |
| Working current               | 12mA          |
| Stable communication distance | 10M           |
| Output Power                  | 10dBm         |
| Antenna type                  | PCB antenna   |
| Net weight                    | 6g            |
| Gross weight                  | 21g           |
| Product Size                  | 48\*24\*8mm   |
| Package Size                  | 136\*92\*12mm |

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core ( PORT B ) | GPIO26 | 5V | GND |
| ----------------- | ------ | -- | --- |
| RF433T            | TX     | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/rf433_t/rf433_t_sch_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit RF433T](https://docs.m5stack.com/en/unit/Unit_RF433T) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U114`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need          | Model-specific reference                                                                                                               |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U114_Unit_RF433T/Structures)                 |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U114_Unit_RF433T/Structures/Unit_RF433T.stl) |
| Example source: RF433.ino | [Read example source: rf433.ino](https://github.com/m5stack/M5Stack/blob/master/examples/Unit/RF433/RF433.ino)                         |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
