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

# M5Stack M5StickC ADC Hat

{% hint style="info" %}
[**View M5Stack M5StickC ADC Hat ADS1110 V1.1 on OpenELAB**](https://openelab.io/products/m5stickc-adc-hat)

**Store SKU / option:** `M5-U069-V11`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack M5StickC ADC Hat ADS1110 V1.1

***

### Product Link

{% embed url="https://openelab.io/products/m5stickc-adc-hat" %}

### Description <a href="#description" id="description"></a>

**ADC HAT V1.1** is another type of C-HAT specifically design for M5StickC controller. Same as ADC unit, this is an ADC converter component for stickc. Packed with an ADC converter chip ADS1110, which is a fully differential, 16-bit, self-calibrating, delta-sigma A/D converter. Extremely easy to design with and configure, the ADS1110 allows you to obtain precise measurements with a minimum of effort.\
The ADS1100 consists of a delta-sigma A/D converter core with adjustable gain, a clock generator, and an I2C interface.\
ADS1110 itself is able to accept a differential input from -5 \~ +5 V, but we have limited the input to 0\~12V by adding on the peripheral circuit design of this IC.

### Features <a href="#product-features" id="product-features"></a>

* Input: 0-12V
* Software Development Platform: Arduino, UIFlow(Blockly, Python)
* ADS1110
  * 16-bits Resolution
  * CONTINUOUS SELF-CALIBRATION
  * SINGLE-CYCLE CONVERSION
  * PROGRAMMABLE GAIN AMPLIFIER GAIN = 1, 2, 4, OR 8
  * PROGRAMMABLE DATA RATE: 15SPS to 240SPS
  * INTERNAL SYSTEM CLOCK
  * I2C INTERFACE: address 0x48

### Applications <a href="#applications" id="applications"></a>

* Analog Signal Capture

### Specification <a href="#specification" id="specification"></a>

| Resources    | Parameter    |
| ------------ | ------------ |
| Net weight   | 6g           |
| Gross weight | 14g          |
| Product Size | 24\*25\*13mm |
| Package Size | 40\*42\*30mm |

![](https://static-cdn.m5stack.com/resource/docs/products/hat/U069-B%20HAT-ADC/hat-adc_04.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/hat/U069-B%20HAT-ADC/hat-adc_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/hat/U069-B%20HAT-ADC/hat-adc_06.webp)

### Pin Map <a href="#pin-map" id="pin-map"></a>

| M5StickC     | GPIO0 | GPIO26 | 5V | GND |
| ------------ | ----- | ------ | -- | --- |
| ADC HAT V1.1 | SDA   | SCL    | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/hat/u069-v11%20HAT%20ADC/u069-v11-sch-01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Hat ADC v1.1](https://docs.m5stack.com/en/hat/Hat_ADC_v1.1) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U069-V11`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                      | Model-specific reference                                                                                                                       |
| ------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Example source: ADC\_M5StickC.ino     | [Read example source: adc\_m5stickc.ino](https://github.com/m5stack/M5-ADS1100/blob/master/examples/ADC_M5StickC/ADC_M5StickC.ino)             |
| Example source: ADC\_M5StickCPlus.ino | [Read example source: adc\_m5stickcplus.ino](https://github.com/m5stack/M5-ADS1100/blob/master/examples/ADC_M5StickCPlus/ADC_M5StickCPlus.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
