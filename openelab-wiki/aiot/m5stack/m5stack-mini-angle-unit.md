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

# M5Stack Mini Angle Unit

{% hint style="info" %}
[**View M5Stack Unit Angle Potentiometer Knob Analog Input Module on OpenELAB**](https://openelab.io/products/mini-angle-unit)

**Store SKU / option:** `M5-U005`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Mini Angle Unit Rotary Switch with Potentiometer

***

### Product Link

{% embed url="https://openelab.io/products/mini-angle-unit" %}

### Description <a href="#description" id="description"></a>

**ANGLE** is a rotary switch Unit which simply includes a **10K** Ohm potentiometer inside. This unit can be used for Continuous signal rotatory control for applications such as volume, brightness, or motor speed.

A potentiometer is a manually adjustable variable resistor with three terminals: Two terminals are connected to a resistive element, the third terminal is connected to an adjustable wiper. The position of the wiper determines the output voltage.

The out voltage is captured and converted by AD on ESP32 on portB.

### Features <a href="#product-features" id="product-features"></a>

* Output voltage range: 0 \~ 2500mV
* GROVE interface, support [UIFlow ](http://flow.m5stack.com/)and [Arduino](http://www.arduino.cc/)
* Two Lego-compatible holes

### Specification <a href="#specification" id="specification"></a>

| Resources      | Parameter     |
| -------------- | ------------- |
| Output voltage | 0 \~ 2500mV   |
| Net weight     | 6g            |
| Gross weight   | 23g           |
| Product Size   | 32\*24\*22mm  |
| Package Size   | 136\*92\*22mm |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_06.webp)

\*In M5Stack product system, Normally the Grove color indicates the type of communications.\*

* Black: Single BUS (AD ,DA ,GPIO)
* Red: I2C
* Blue:UART
* White: Others(depends)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_sch_02.webp" alt=""><figcaption></figcaption></figure>

The Unit's Grove interface is black, specify it is an analog interface that should be connected to the M5Core's GROVE B interface.

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a concise and fast program writer, which has a built-in case program related to the product. It can be burned to the main control by simple steps to perform a series of function verification.

[Download Windows Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/UNIT/For%20M5Core/EasyLoader_Angle_UNIT_With_M5Core.exe) [Download MacOS Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/MacOS/UNIT/EasyLoader_Angle_UNIT_With_M5Core.dmg)

**Description:**\
Display knob analog value data.

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE B) | GPIO36     | GPIO26 | 5V | GND |
| --------------- | ---------- | ------ | -- | --- |
| ANGLE Unit      | Sensor Pin |        | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_sch_01.webp" alt=""><figcaption></figcaption></figure>

### COMPATIBLE <a href="#compatible" id="compatible"></a>

<figure><img src="../../.gitbook/assets/image (408).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Angle](https://docs.m5stack.com/en/unit/Unit_Angle) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U005`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                             |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U005_Unit_Angle/Structures)                |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U005_Unit_Angle/Structures/Unit_Angle.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
