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

# M5Stack Proto Pegboard Module

{% hint style="info" %}
[**View M5Stack Proto Pegboard Module - 13.2 on OpenELAB**](https://openelab.io/products/proto-pegboard-module)

**Store SKU / option:** `M5-M032`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Proto Pegboard Module - 13.2

***

### Product Link

{% embed url="https://openelab.io/products/proto-pegboard-module" %}

### Description <a href="#description" id="description"></a>

**PROTO 13.2** is a universal DIY proto module in the m5stack stack module series, with a height of 13.2mm. You can easily build your own custom circuits by using this module. You can design and build the prototype circuit according to your own needs, and interact with the M5 Core on the top layer through M-BUS. There are HY2.0 4P, DC power socket, VH3.96 and other common openings on the board, so it is very simple to use.

### Features <a href="#features" id="features"></a>

* Main Hole Size: 0.039" 1mm (CNC Drilled)
* Hole Pitch: 0.1" - (2.54 mm)
* Entire Hole Quantity: 169 Holes

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter          |
| ------------ | ------------------ |
| Net weight   | 24g                |
| Gross weight | 49g                |
| Product Size | 54.2\*54.2\*13.2mm |
| Package Size | 93\*64\*20mm       |

### MBUS PinMap <a href="#mbus-pinmap" id="mbus-pinmap"></a>

|       LEFT       |      RIGHT      |
| :--------------: | :-------------: |
|        GND       |    IO35(ADC1)   |
|        GND       |    IO36(ADC2)   |
|        GND       |        EN       |
|    IO23(MOSI)    |    IO25(DAC0)   |
|    IO19(MISO)    |    IO26(DAC1)   |
|  IO18(EXT/\_SCK) |       3V3       |
|   IO3(U1/\_RX)   |   IO1(U1/\_TX)  |
|   IO16(U2/\_RX)  |  IO17(U2/\_TX)  |
|  IO21(I2C/\_SDA) | IO22(I2C/\_SCL) |
|        IO2       |       IO5       |
| IO12(I2S/\_SCLK) |       IO13      |
|  IO15(I2S/\_OUT) |       IO0       |
|       HPOWR      |       IO34      |
|       HPOWR      |        5V       |
|       HPOWR      |       BAT       |

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/module_bus.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Module13.2 Proto](https://docs.m5stack.com/en/module/Module13.2_Proto) for the manufacturer's model information, dimensions and applicable connection instructions. The official product code is **`M032`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

Check the accessory's physical fit and any electrical connections against the exact host. Firmware and software instructions belong to that host; do not treat a passive part as a separately programmable controller. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
