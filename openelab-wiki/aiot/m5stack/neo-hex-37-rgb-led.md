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

# Neo HEX 37 RGB LED

{% hint style="info" %}
[**View M5Stack Neo HEX 37 RGB LED Board on OpenELAB**](https://openelab.io/products/m5stack-neo-hex)

**Store SKU / option:** `M5-A045-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Neo HEX 37 RGB LED Board

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-neo-hex" %}

### Description <a href="#description" id="description"></a>

**NeoHEX** is a hexagonal board with 37 RGB LED flexible beads and will be sure to 'WOW' plenty. Use single BUS control, and support multiple boards connecting. Two sets of different angle input connectors are provided for independent power supply + signal control. External structure with fixing ears for easy installation. With its opal light sheet, the diffusion creates a gentle glow and provides innovative solutions to transform your living spaces into unique pieces of functional art.

### Features <a href="#product-features" id="product-features"></a>

* WS2812C-2020-V1
* Number of LEDs: 37
* Support multiple boards connection
* 6x fixing ears (removable)
* Comes with opal light sheet
* Single pixel support 256 levels of brightness display, can be combined for 16777216 kinds of full color display

### Applications <a href="#applications" id="applications"></a>

* Lighting decoration

### Specifications <a href="#specifications" id="specifications"></a>

<table><thead><tr><th width="209">Specification</th><th>Parameters</th></tr></thead><tbody><tr><td>LED Bead Model</td><td>WS2812C-2020-V1</td></tr><tr><td>Number of light beads</td><td>37</td></tr><tr><td>Voltage supply</td><td>3.7 ~ 5.3V</td></tr><tr><td>Logic input level</td><td>-0.3V ~ VDD+0.7</td></tr><tr><td>Output/output interface</td><td>HY2.0-4P interface: 2x input (signal, power), 1x output (extension)</td></tr><tr><td>Refresh Rate</td><td>30 frames (1024 cascades)</td></tr><tr><td>Power consumption</td><td>Actual measurement of power consumption (37 lights are fully lit, brightness 100%)：Red Light：DC5V@207mAGreen Light：DC5V@109mABlue Light：DC5V@208mAWhite light：DC5V@568mA</td></tr><tr><td>Adjustable brightness</td><td>Level 256</td></tr><tr><td>Support Colors</td><td>16777216 kinds of colors</td></tr><tr><td>Fixing hole diameter</td><td>2mm</td></tr><tr><td>Net Weight</td><td>3.7g</td></tr><tr><td>Gross Weight</td><td>9g</td></tr><tr><td>Product Size</td><td>40*36*7mm</td></tr><tr><td>Package Size</td><td>93*138mm</td></tr></tbody></table>

![](https://static-cdn.m5stack.com/resource/docs/products/unit/neohex/neohex_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/neohex/neohex_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/neohex/neohex_06.webp)

### Brightness/Power consumption reference <a href="#brightness-power-consumption-reference" id="brightness-power-consumption-reference"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/neohex/neohex_07.webp" alt=""><figcaption></figcaption></figure>

### Drive conditions <a href="#drive-conditions" id="drive-conditions"></a>

Different M5 main control in the USB power supply conditions of the light board drive for reference.

* Actual drive conditions：
  * ATOM: White light brightness is 82% normal drive（>Unable to light up at 86%）
  * CORE: White light brightness is 100% normal drive
  * CORE2: White light brightness is 100% normal drive
  * M5StickC: White light brightness is 86% normal drive（>Unable to light up at 90%）
  * M5StickCPlus: White light brightness 78% normal drive（>Unable to light up at 86%）

### Structure Diagram <a href="#structure-diagram" id="structure-diagram"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/neohex/neohex_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Pin Mapping <a href="#pin-mapping" id="pin-mapping"></a>

* M5GO PORT-A

| M5Core(PORT A) | GPIO22 | GPIO21   | 5V | GND |
| -------------- | ------ | -------- | -- | --- |
| Unit NeoHEX    | /      | Data Pin | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

![](https://static-cdn.m5stack.com/resource/docs/products/unit/neohex/neohex_sch_02.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/neohex/neohex_sch_03.webp)

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [NeoHEX Example](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/HEX_SK6812)
* [FastLED Library](https://github.com/FastLED/FastLED/wiki/Overview)
* [FastLED API Reference](http://www.taichi-maker.com/homepage/reference-index/arduino-library-index/fastled-library/)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [UNIT NeoHEX UIFlow TEST](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/HEX/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_uiflow_02.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_uiflow_03.webp" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_uiflow_04.webp" alt=""><figcaption></figcaption></figure>

### COMPATIBLE <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (412).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit NeoHEX](https://docs.m5stack.com/en/unit/Unit_NeoHEX) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`A045-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                              |
| ---------------------------- | ----------------------------------------------------------------------------------------------------- |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/532/Sch_NeoHex_V1.1.pdf) |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_hex)       |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
