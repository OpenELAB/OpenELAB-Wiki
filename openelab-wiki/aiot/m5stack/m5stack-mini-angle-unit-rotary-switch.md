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

# M5Stack Mini Angle Unit Rotary Switch

{% hint style="info" %}
[**View M5Stack Unit Angle Potentiometer Knob Analog Input Module on OpenELAB**](https://openelab.io/products/mini-angle-unit)

**Store SKU / option:** `M5-U005`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Mini Angle Unit Rotary Switch

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

| Resources      | Parameter    |
| -------------- | ------------ |
| Output voltage | 0 \~ 2500mV  |
| Net weight     | 6g           |
| Gross weight   | 23g          |
| Product Size   | 32\*24\*22mm |
| Package Size   | 73\*46\*30mm |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_06.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_07.webp)

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

### Pinout <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE B) | GPIO36     | GPIO26 | 5V | GND |
| --------------- | ---------- | ------ | -- | --- |
| ANGLE Unit      | Sensor Pin |        | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Learn <a href="#learn" id="learn"></a>

<figure><img src="https://hackster.imgix.net/uploads/attachments/937726/screen_shot_2019-07-11_at_6_10_33_pm_GJ5JxJ7826.png?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[DIY Protractor with M5StickC](https://www.hackster.io/shasha-liu/diy-protractor-with-m5stickc-e67e88)[DIY Protractor with M5StickC](https://www.hackster.io/shasha-liu/diy-protractor-with-m5stickc-e67e88)M5StickC + Angle unit = Protractor (detecting range: 0-180 degrees）

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

The code below is incomplete. To get the complete code, please click [here](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/ANGLE)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_arduino_01.webp" alt=""><figcaption></figcaption></figure>

#### UIFlow <a href="#uiflow" id="uiflow"></a>

[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)[UIFlow2.0](https://docs.m5stack.com/en/uiflow2/uiflow_web)This tutorial will show you how to initialize the configuration using the UIFlow2.0 graphical programming platform

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/uiflow2/guide/uiflow2_cover.png" alt=""><figcaption></figcaption></figure>

[ANGLE Unit Programming Guide](https://uiflow-micropython.readthedocs.io/en/latest/unit/angle.html)

<figure><img src="https://static-cdn.m5stack.com/mpy_docs/unit/angle/example.svg" alt=""><figcaption></figcaption></figure>

**Feature Introduction**

Read the output value of the knob potentiometer

* **Get value** Return potentiometer value

**Usage**

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/ANGLE/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/angle/angle_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Angle](https://docs.m5stack.com/en/unit/Unit_Angle) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U005`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                             |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U005_Unit_Angle/Structures)                |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U005_Unit_Angle/Structures/Unit_Angle.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
