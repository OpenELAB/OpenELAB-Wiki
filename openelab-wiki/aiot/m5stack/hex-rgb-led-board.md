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

# HEX RGB LED Board

### HEX RGB LED Board

***

### Product Link

{% embed url="https://openelab.io/products/hex-rgb-led-board" %}

### Description <a href="#description" id="description"></a>

**HEX** is a hexagon RGB LED panel that integrates a total of 37 RGB LEDs. The HEX board includes an input port and an output port, you can have multiply of them in series connection.

### Features <a href="#product-features" id="product-features"></a>

* 37 integrated LEDs
* Software development platform: Arduino, UIFlow (Blockly & python)

### Specification <a href="#specification" id="specification"></a>

| Resources    | Parameter    |
| ------------ | ------------ |
| RGB LED      | SK6812 x 37  |
| Net weight   | 8g           |
| Gross weight | 10g          |
| Product Size | 30\*35\*8mm  |
| Package Size | 50\*80\*10mm |

This is how LEDs layout in the panel, Pay attention to the sequence in your code:

![](https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_05.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a concise and fast program writer, which has a built-in case program related to the product. It can be burned to the main control by simple steps to perform a series of function verification.

[Download Windows Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/UNIT/For%20M5Core/EasyLoader_HEX_UNIT_With_M5Core.exe) [Download MacOS Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/MacOS/UNIT/EasyLoader_HEX_UNIT_With_M5Core.dmg)

**Description:**\
The HEX Unit light board displays a rainbow gradient.

### Pinout <a href="#pinmap" id="pinmap"></a>

**If HEX connectors to GROVE A**

| M5Core(GROVE A) | GPIO22 | GPIO21   | 5V | GND |
| --------------- | ------ | -------- | -- | --- |
| HEX Unit In     |        | Data Pin | 5V | GND |

**If HEX connectors to GROVE B**

| M5Core(GROVE B) | GPIO36 | GPIO26   | 5V | GND |
| --------------- | ------ | -------- | -- | --- |
| HEX Unit In     |        | Data Pin | 5V | GND |

**If HEX connectors to GROVE C**

| M5Core(GROVE C) | GPIO16 | GPIO17   | 5V | GND |
| --------------- | ------ | -------- | -- | --- |
| HEX Unit In     |        | Data Pin | 5V | GND |

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_04.webp" alt=""><figcaption></figcaption></figure>

### Learn <a href="#learn" id="learn"></a>

<figure><img src="https://hackster.imgix.net/uploads/attachments/851579/1554694803602-tim20190408113933-resized_C6QBOyrepz.png?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[Simple Watch Device](https://www.hackster.io/merryq/simple-watch-device-018600)[Simple Watch Device](https://www.hackster.io/merryq/simple-watch-device-018600)Make a simple watch device using UIFlow.

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

FastLED library on Arduino presents excellent and colorful lighting effects. Before compile, it is require to install the FastLED library and connect HEX to GROVE A.

RGB LED Library on Arduino

* [**FastLED Library**](https://github.com/FastLED/FastLED/wiki/Overview)
* [**FastLED Reference(Chinese version)**](http://www.taichi-maker.com/homepage/reference-index/arduino-library-index/fastled-library/)

To get the complete code, please click [here](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/HEX_SK6812)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_06.webp" alt=""><figcaption></figcaption></figure>

#### UIFlow <a href="#uiflow" id="uiflow"></a>

To get the complete code, please click [here](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/HEX/UIFlow)

![](https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_uiflow_01.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_uiflow_02.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_uiflow_03.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_uiflow_04.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/hex/hex_uiflow_05.webp)

