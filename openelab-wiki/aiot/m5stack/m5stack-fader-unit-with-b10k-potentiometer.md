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

# M5Stack Fader Unit with B10K Potentiometer

{% hint style="info" %}
[**View M5Stack Fader Unit with B10K Potentiometer on OpenELAB**](https://openelab.io/products/m5stack-fader-unit)

**Store SKU / option:** `M5-U123`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Fader Unit with B10K Potentiometer

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-fader-unit" %}

### Description <a href="#description" id="description"></a>

**UNIT FADER** is a Slide Potentiometer with color indicator, `employ a 35mm slide potentiometer` + `14x SK6812 programmable RGB lights`. The fader has its own `center point positioning`, and excellent slide appliances for stable, reliable performance and precise control. The integrated beads support digital addressing, which means you can adjust the brightness and color of each LED light. The product is suitable for lighting, music control, and other applications.

### Features <a href="#product-features" id="product-features"></a>

* With center point positioning
* Excellent damping
* Single connection 1OkΩ adjustable resistor
* Programmable RGB lights
* GROVE interface
* Development Platform:
  * Arduino, UIFlow

### Application <a href="#application" id="application"></a>

* Human–machine interaction
* Light and music control
* Adjustment switch
* Potentiometer level signal input

### Specification <a href="#specification" id="specification"></a>

| Specification       | Parameter                                                             |
| ------------------- | --------------------------------------------------------------------- |
| Fader stroke        | 35mm                                                                  |
| Fader handle length | 10mm                                                                  |
| Single resistor     | 1OkΩ                                                                  |
| Output voltage      | 0-3.3V (under 5V power supply)                                        |
| RGB LED             | 14x SK6812 Programmable RGB Lamp                                      |
| Working current     | 90.04mA (Lighting brightness configuration 50%, fader maximum output) |
| Net weight          | 15.5g                                                                 |
| Gross weight        | 30g                                                                   |
| Product size        | 64 \* 24 \* 24mm                                                      |
| Packing size        | 136 \* 92 \* 24mm                                                     |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/fader_03.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/fader_06.webp)

### Pinout <a href="#pinmap" id="pinmap"></a>

| M5Core(PORT B) | G36         | G26           | 5V  | GND |
| -------------- | ----------- | ------------- | --- | --- |
| UNIT FADER     | VALUE-INPUT | SK6812-SIGNAL | VIN | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/fader/fader_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Links <a href="#related-links" id="related-links"></a>

* [**ESP32 ADC DOCS**](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/peripherals/adc.html)
* [**FastLED Github**](https://github.com/FastLED/FastLED)

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [FADER UNIT TEST](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/FADER)

#### UIFlow example <a href="#uiflow-example" id="uiflow-example"></a>

![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/unit_fader_uiflow_01.webp)

### UIFlow <a href="#uiflow" id="uiflow"></a>

* set led color(RGB565)

![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/unit_fader_uiflow_02.webp)

* set led color(R, G, B)

![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/unit_fader_uiflow_03.webp)

* set brightness

![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/unit_fader_uiflow_04.webp)

* set color POT led num<br>

![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/unit_fader_uiflow_05.webp)

* set bright POT

![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/unit_fader_uiflow_06.webp)

* read raw value of 12bit

![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/unit_fader_uiflow_07.webp)

* read raw value of 16bit

![](https://static-cdn.m5stack.com/resource/docs/products/unit/fader/unit_fader_uiflow_08.webp)

## Official documentation and development resources

Use [Unit Fader](https://docs.m5stack.com/en/unit/Unit_Fader) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U123`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                             |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U123_Unit_Fader/Structures)                |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U123_Unit_Fader/Structures/Unit_Fader.stl) |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/FADER)                                   |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
