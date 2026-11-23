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

# M5Stack Proto Module

{% hint style="info" %}
[**View M5Stack Proto Module with Extension & Bus Socket on OpenELAB**](https://openelab.io/products/proto-module)

**Store SKU / option:** `M5-M001`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Proto Module with Extension & Bus Socket

***

### Product Link <a href="#description" id="description"></a>

{% embed url="https://openelab.io/products/proto-module" %}

### Description <a href="#description" id="description"></a>

**PROTO** is a pure universal prototype perboard. You can have the total freedom to make your own project as you want it, with prototyping perboards that allows laying out customized circuit to interact with the M5 core via M-BUS.

### Features <a href="#features" id="features"></a>

* Hole Size: 0.039" 1mm (CNC Drilled)
* Hole Pitch: 0.1 in - (2.54 mm)
* Entire Hole Quantity: 260 Holes

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter          |
| ------------ | ------------------ |
| Net weight   | 12g                |
| Gross weight | 22g                |
| Product Size | 54.2\*54.2\*12.8mm |
| Package Size | 60\*57\*17mm       |

### MBUS PinMap <a href="#mbus-pinmap" id="mbus-pinmap"></a>

|       LINE0      |      LINE1      |
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

### MBUS PinMap <a href="#mbus-pinmap" id="mbus-pinmap"></a>

<figure><img src="../../.gitbook/assets/image (360).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Module Proto](https://docs.m5stack.com/en/module/Module_Proto) for the manufacturer's model information, dimensions and applicable connection instructions. The official product code is **`M001`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                                       |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/M001_Module_Proto/Structures)                        |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/M001_Module_Proto/Structures/Module_Proto_Board.stl) |

Check the accessory's physical fit and any electrical connections against the exact host. Firmware and software instructions belong to that host; do not treat a passive part as a separately programmable controller. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
