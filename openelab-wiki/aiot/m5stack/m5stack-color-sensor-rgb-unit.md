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

# M5Stack Color Sensor RGB Unit

{% hint style="info" %}
[**View M5Stack Color Sensor RGB Unit with TCS3472 Color Recognition on OpenELAB**](https://openelab.io/products/color-sensor-rgb-unit)

**Store SKU / option:** `M5-U009`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Color Sensor RGB Unit

***

### Product Link

{% embed url="https://openelab.io/products/color-sensor-rgb-unit" %}

### Description <a href="#description" id="description"></a>

**COLOR** is color recognition unit integrated with **TCS3472** chipset. As the name says, **COLOR** is able to detect color value and return RGB data as response.

### Features <a href="#features" id="features"></a>

* Detection range: -40℃\~85℃
* GROVE interface, support [UIFlow ](http://flow.m5stack.com/)and [Arduino](http://www.arduino.cc/)
* Two Lego-compatible holes

### Applications <a href="#applications" id="applications"></a>

* Product Color Verification
* Color tracking robot

### Specification <a href="#specification" id="specification"></a>

| Resources                 | Parameters        |
| ------------------------- | ----------------- |
| IC                        | TCS3472           |
| Working temperature range | -40°C\~85°C       |
| Communication protocol    | I2C:0x29          |
| Product Size              | 32.2\*24.2\*8.2mm |
| Package Size              | 136\* 92\* 13mm   |
| Product Weight            | 4g                |
| Package Weight            | 17g               |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/COLOR/img-91e53454-e42d-4f33-87a2-2fa2f78c453a.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/COLOR/img-8a6ebbb4-f768-466a-b7d4-53ae5318f8ed.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [Datasheet - TCS3472](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/TCS3472_en.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/COLOR/img-ba549913-ddbd-4b74-ba3a-211ec698c1f7.webp" alt=""><figcaption></figcaption></figure>

### EasyLoader <a href="#easyloader" id="easyloader"></a>

* **Windows**
  * [EasyLoader\_Color\_UNIT\_With\_M5Core](https://static-cdn.m5stack.com/resource/docs/products/unit/COLOR/ezLoader-8b2c7c7b-0391-4f39-9ade-c27aae193a13.exe)

### Pinout <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/COLOR/pinMap-a5ecacce-b6d7-44eb-9efc-76067fa1662b.png" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [The code below is incomplete. To get the complete code, please click here After burning this example firmware, PC serial terminal will print original value RGBC (red, green, blue, clear).](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/COLOR_TCS3472)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/COLOR/arduinoCase-1690885555515color_arduino_01.png" alt=""><figcaption></figcaption></figure>

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/COLOR/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/COLOR/uiflowCase-1690885569743color_uiflow_01.png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Color](https://docs.m5stack.com/en/unit/Unit_Color) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U009`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                             |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U009_Unit_Color/Structures)                |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U009_Unit_Color/Structures/Unit_Color.stl) |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_color)                                    |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
