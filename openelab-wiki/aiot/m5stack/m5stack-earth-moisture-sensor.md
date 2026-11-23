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

# M5Stack Earth Moisture Sensor

{% hint style="info" %}
[**View M5Stack Earth Moisture Sensor Unit Analog and Digital Output on OpenELAB**](https://openelab.io/products/earth-moisture-sensor-unit)

**Store SKU / option:** `M5-U019`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Earth Moisture Sensor Unit Analog and Digital Output

***

### Product Link

{% embed url="https://openelab.io/products/earth-moisture-sensor-unit" %}

### Description <a href="#description" id="description"></a>

**EARTH** unit is a Soil Moisture Sensor for measuring the moisture in soil and similar materials.

The soil moisture sensor usage is pretty straight forward, the two large exposed pads function as probes for the sensor, together acting as a variable resistor.

The higher moisture that is in the soil means the better the conductivity between the two so that the sensor will result in a lower resistance, and a higher SIG out.

You can read the moisture in soil by using the ADC. Inside this Unit we've added an extra potentiometers to change the measurement range.

### Features <a href="#features" id="features"></a>

* Adjustable threshold, including 10K adjustable resistor
* Analog & Digital output
* GROVE interface, support [UIFlow ](http://flow.m5stack.com/)and [Arduino](http://www.arduino.cc/)
* Two Lego-compatible holes

### Applications <a href="#applications" id="applications"></a>

* Potted soil moisture monitoring

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter         |
| ------------ | ----------------- |
| Net weight   | 5g                |
| Gross weight | 18g               |
| Product Size | 64.4\*24.1\*8.1mm |
| Product Size | 136\*92\*12mm     |

### PinMap

| M5Core(GROVE B) | GPIO36           | GPIO26            | 5V | GND |
| --------------- | ---------------- | ----------------- | -- | --- |
| EARTH Unit      | AnalogSignal Pin | DigitalSignal Pin | 5V | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/earth/earth_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Mdouel Size <a href="#mdouel-size" id="mdouel-size"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/earth/%E5%B0%BA%E5%AF%B8%E5%9B%BE.jpg" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (962).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Earth](https://docs.m5stack.com/en/unit/Unit_Earth) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U019`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                                             |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U019_Unit_Earth/Structures)                |
| Mechanical / CAD files  | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U019_Unit_Earth/Structures/Unit_Earth.stl) |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/EARTH)                                   |
| UIFlow1 workflow        | [Read uiflow1 workflow](https://docs.m5stack.com/en/uiflow/blockly/unit/earth)                                                       |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
