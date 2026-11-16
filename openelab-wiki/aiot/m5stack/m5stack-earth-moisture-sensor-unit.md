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

# M5Stack Earth Moisture Sensor Unit

### M5Stack Earth Moisture Sensor Unit

***

### Product Link

{% embed url="https://openelab.io/products/earth-moisture-sensor-unit" %}

### Description <a href="#description" id="description"></a>

**EARTH** unit is a Soil Moisture Sensor for measuring the moisture in soil and similar materials.

The soil moisture sensor usage is pretty straight forward, the two large exposed pads function as probes for the sensor, together acting as a variable resistor.

The higher moisture that is in the soil means the better the conductivity between the two so that the sensor will result in a lower resistance, and a higher SIG out.

You can read the moisture in soil by using the ADC. Inside this Unit we've added an extra potentiometers to change the measurement range.

### Features <a href="#product-features" id="product-features"></a>

* Adjustable threshold, including 10K adjustable resistor
* Analog & Digital output
* GROVE interface, support [UIFlow ](http://flow.m5stack.com/)and [Arduino](http://www.arduino.cc/)
* Two Lego-compatible holes

### Applications <a href="#applications" id="applications"></a>

* Potted soil moisture monitoring

### Specification <a href="#specification" id="specification"></a>

| Resources    | Parameter         |
| ------------ | ----------------- |
| Net weight   | 5g                |
| Gross weight | 18g               |
| Product Size | 64.4\*24.1\*8.1mm |
| Product Size | 67\*53\*12mm      |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/earth/earth_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/earth/earth_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/earth/earth_06.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/earth/earth_08.webp)

Electrode of the unit is not anti-corrosive, or waterproof, for POC purpose only. Pls do NOT put it in humidity environment for a long while.

### EasyLoader <a href="#easyloader" id="easyloader"></a>

[download EasyLoader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Unit/EasyLoader_Earth.exe)

What is EasyLoader?1.EasyLoader is a simple and fast program burner. Every product page in EasyLoader provides a product-related case program. It can be burned to the master through simple steps, and a series of function verification can be performed. .

2. After downloading the software, double-click to run the application, connect the M5 device to the computer through the data cable, select the port parameters, click **"Burn"** to start burning. (**For M5StickC burning, please Set the baud rate to 750000 or 115200**)

### Pinout <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE B) | GPIO36           | GPIO26            | 5V | GND |
| --------------- | ---------------- | ----------------- | -- | --- |
| EARTH Unit      | AnalogSignal Pin | DigitalSignal Pin | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/earth/earth_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Learn <a href="#learn" id="learn"></a>

<figure><img src="https://hackster.imgix.net/uploads/attachments/1006384/1571711554666761_CjW8O5vLl6.gif?auto=format%2Ccompress&#x26;gifq=35&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[Smart Planting System](https://www.hackster.io/sophiaxue/smart-planting-system-a842d7)[Smart Planting System](https://www.hackster.io/sophiaxue/smart-planting-system-a842d7)Building a smart planting system using M5Stack to monitor the lights, humidity, temperature, watering your plant automatically.

<figure><img src="https://hackster.imgix.net/uploads/attachments/1257840/_Wl3Zxp4yYH.blob?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[Hand Hygienics](https://www.hackster.io/e1-team-2/hand-hygienics-5e04a9)[Hand Hygienics](https://www.hackster.io/e1-team-2/hand-hygienics-5e04a9)Hand Hygienics aims to reduce spread of Covid-19 through contact.

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

The code below is incomplete. To get the complete code, please click [here](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/EARTH)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

<figure><img src="https://static-cdn.m5stack.com/mpy_docs/unit/earth/example.png" alt=""><figcaption></figcaption></figure>

[UIFlow2.0 EARTH Unit instructions](https://uiflow-micropython.readthedocs.io/zh-cn/latest/units/earth.html)[UIFlow2.0 EARTH Unit instructions](https://uiflow-micropython.readthedocs.io/zh-cn/latest/units/earth.html)How to use Unit EARTH and related API instructions in the UIFlow2.0 graphical programming platform

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/static/assets/img/uiflow/blockly/unit/earth/uiflow_block_earth_demo.svg" alt=""><figcaption></figcaption></figure>

[UIFlow1.0 EARTH Unit instructions](https://docs.m5stack.com/en/uiflow/blockly/unit/earth)[UIFlow1.0 EARTH Unit instructions](https://docs.m5stack.com/en/uiflow/blockly/unit/earth)How to use Unit EARTH and related API instructions in the UIFlow1.0 graphical programming platform

**Feature Introduction**

Measuring soil moisture

* **Get Analog value** Return analog value
* **Get Digital value** Return numeric value

**Usage**

To get the complete code, please click [here](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/EARTH/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/earth/earth_uiflow_01.webp" alt=""><figcaption></figcaption></figure>
