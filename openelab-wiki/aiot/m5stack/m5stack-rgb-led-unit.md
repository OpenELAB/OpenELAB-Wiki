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

# M5Stack RGB LED Unit

{% hint style="info" %}
[**View M5Stack RGB LED Unit on OpenELAB**](https://openelab.io/products/m5stack-rgb-led-unit)

**Store SKU / option:** `M5-U003`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack RGB LED Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-rgb-led-unit" %}

### Description <a href="#description" id="description"></a>

**RGB** is LED Unit include 3 individual LEDs. It is also one of the Unit from M5GO Kit. Each one can display any color based on the RGB spectrum. One feature of this Unit is that it's extendable, which means you can have multiple of them wired together.

This is a very useful piece of hardware for a STEM class, students can program it to realize some of cool applications, for example a traffic light.

### Features <a href="#product-features" id="product-features"></a>

* Program Platform: Arduino, UIFlow(Blockly, Python)
* Two Lego-compatible holes

### Specification <a href="#specification" id="specification"></a>

| Resources       | Parameter     |
| --------------- | ------------- |
| Lamp bead model | SK6812(3535)  |
| Net weight      | 4g            |
| Gross weight    | 17g           |
| Product Size    | 32\*24\*8mm   |
| Package Size    | 136\*92\*12mm |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rgb/rgb_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/rgb/rgb_06.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a concise and fast program writer, which has a built-in case program related to the product. It can be burned to the main control by simple steps to perform a series of function verification.

[Download Windows Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/UNIT/For%20M5Core/EasyLoader_RGB_UNIT_With_M5Core.exe) [Download MacOS Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/MacOS/UNIT/EasyLoader_RGB_UNIT_With_M5Core.dmg)

**Description:**\
Drive RGB LED to light up different colors.

### Pinout <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE B) | GPIO36 | GPIO26     | 5V | GND |
| --------------- | ------ | ---------- | -- | --- |
| RGB Unit        |        | Signal Pin | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/rgb/rgb_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Learn <a href="#learn" id="learn"></a>

<figure><img src="https://hackster.imgix.net/uploads/attachments/1256124/_JUQxx3QiJk.blob?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[CovidStop](https://www.hackster.io/hans-angelo_/covidstop-e9e64b)[CovidStop](https://www.hackster.io/hans-angelo_/covidstop-e9e64b)A technology which increases efficiency in signing in or out during peak hour areas when entering the campus while the SafeEntry implies.

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [M5Unit-RGB with M5Core](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/RGB_SK6812)
* [M5Unit-RGB with M5CoreS3](https://github.com/m5stack/M5CoreS3/blob/49580074f79832a9929b6b58c28aa7db1b01f7d3/examples/Unit/Unit_RGB_U003/Unit_RGB_U003.ino)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/uiflow2/guide/uiflow2_cover.png" alt=""><figcaption></figcaption></figure>

[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)tutorial will show you how to initialize the configuration using the UIFlow2.0 graphical programming platform

[RGB Unit Programming Guide](https://uiflow-micropython.readthedocs.io/zh-cn/latest/unit/rgb.html)

<figure><img src="https://static-cdn.m5stack.com/mpy_docs/unit/rgb/example.svg" alt=""><figcaption></figcaption></figure>

**Feature Introduction**

Three indicator led

* **Set index RGB color** Specify the color of a serial number light
* **Set form to RGB color** Set the color of multiple RGB LEDs
* **Set all RGB color** Set all of RGB color
* **Set brightness** Set brightness of LED

**Usage**

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/RGB/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/rgb/rgb_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit RGB](https://docs.m5stack.com/en/unit/Unit_RGB) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U003`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                    | Model-specific reference                                                                                                                                                    |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files              | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U003_Unit_RGB/Structures)                                                         |
| Mechanical / CAD files              | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U003_Unit_RGB/Structures/Unit_RGB.stl)                                            |
| Example source: M5Stack             | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/RGB_SK6812)                                                                     |
| Example source: Unit\_RGB\_U003.ino | [Read example source: unit\_rgb\_u003.ino](https://github.com/m5stack/M5CoreS3/blob/49580074f79832a9929b6b58c28aa7db1b01f7d3/examples/Unit/Unit_RGB_U003/Unit_RGB_U003.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
