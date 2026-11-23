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

# M5Stack Mini Infrared Emitter

{% hint style="info" %}
[**View M5Stack Mini Infrared Emitter & Receiver Unit on OpenELAB**](https://openelab.io/products/mini-infrared-emitter-receiver-unit)

**Store SKU / option:** `M5-U002`. Match the purchased model and revision to the official reference below.
{% endhint %}

## M5Stack Mini Infrared Emitter & Receiver Unit

***

### Product Link

{% embed url="https://openelab.io/products/mini-infrared-emitter-receiver-unit" %}

### Description <a href="#description" id="description"></a>

**IR** is a pair of infrared photoelectric sensors from the M5Go Kit family. Contains 1x infrared emitter and 1x receiver.

IR remote control is widely used in consumer electronics, it can be used to operate devices such as a television set, DVD player, or other home appliance, from a short distance. Since this unit comes with emitter and receiver, you can practice not only on IR encode but also on IR decode.

### Product Features <a href="#product-features" id="product-features"></a>

* 1x infrared emitter(wavelength:940nm)
* 1x infrared receiver
* Distance range: < 5m
* Software Development Platform: Arduino, UIFlow(Blockly,Python)
* Two Lego-compatible holes

### Specification <a href="#specification" id="specification"></a>

| Resources                   | Parameter    |
| --------------------------- | ------------ |
| infrared emitter wavelength | 940nm        |
| Net weight                  | 4g           |
| Gross weight                | 17g          |
| Product Size                | 32\*24\*8mm  |
| Package Size                | 67\*53\*12mm |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/ir/ir_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/ir/ir_06.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

[download EasyLoader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Unit/EasyLoader_IR.exe)

What is EasyLoader?1.EasyLoader is a simple and fast program burner. Every product page in EasyLoader provides a product-related case program. It can be burned to the master through simple steps, and a series of function verification can be performed. .

After downloading the software, double-click to run the application, connect the M5 device to the computer through the data cable, select the port parameters, click **"Burn"** to start burning. (**For M5StickC burning, please Set the baud rate to 750000 or 115200**)

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE B) | GPIO36       | GPIO26          | 5V | GND |
| --------------- | ------------ | --------------- | -- | --- |
| IR Unit         | Receiver Pin | Transmitter Pin | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/ir/ir_sch_01.webp" alt=""><figcaption></figcaption></figure>

### COMPATIBLE <a href="#compatible" id="compatible"></a>

## Official documentation and development resources

Use [Unit IR](https://docs.m5stack.com/en/unit/Unit_IR) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U002`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U002_Unit_IR/Structures)             |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U002_Unit_IR/Structures/Unit_IR.stl) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
