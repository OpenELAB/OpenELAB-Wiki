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

# M5Stack 1 to 3 HUB Expansion

{% hint style="info" %}
[**View M5Stack 1 to 3 HUB Expansion Unit on OpenELAB**](https://openelab.io/products/m5stack-1-to-3-hub)

**Store SKU / option:** `M5-U006`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack 1 to 3 HUB Expansion Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-1-to-3-hub" %}

### Description <a href="#description" id="description"></a>

**HUB** is a unit that is used in order to expand the GROVE ports over the M5Stack device. For example, if we want sensors with different I2C addresses or output to 3 devices at the same time. (M5Stack device usually can output one device at a time to to limited amount of grove ports)

Notice: **HUB** is just a hardware expander, if you are looking for hardware and software (standard protocol) expander like I2C, Single-bus, please check **PaHUB** or **PbHUB**.

If you are connecting two I2C slave devices onto **HUB** that share the same address, you will have problem getting I2C data from both. The I2C addresses of the devices must be different, they can be changed manually by changing the resistor values.

### Features <a href="#features" id="features"></a>

* GROVE Expander
* Two Lego-compatible holes

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter     |
| ------------ | ------------- |
| Net weight   | 5g            |
| Gross weight | 17g           |
| Product Size | 32\*24\*12mm  |
| Package Size | 136\*92\*13mm |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/hub/hub_sch_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Hub](https://docs.m5stack.com/en/unit/Unit_Hub) for the manufacturer's model information, dimensions and applicable connection instructions. The official product code is **`U006`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need       | Model-specific reference                                                                                                         |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U006_Unit_Hub/Structures)              |
| Mechanical / CAD files | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U006_Unit_Hub/Structures/Unit_Hub.stl) |

Check the accessory's physical fit and any electrical connections against the exact host. Firmware and software instructions belong to that host; do not treat a passive part as a separately programmable controller. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
