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

# Hall Effect Unit

### Hall Effect Unit (A3144E Hall Sensor)

***

### Product Link

{% embed url="https://openelab.io/products/hall-effect-unit" %}

### Description <a href="#description" id="description"></a>

**Hall effect Unit** integrated with three A3144E Hall sensor switches which are processed by 74HC series gate integrated circuits.

Low-level signal can be generated when the magnet S pole is close to the top of the sensor or the N pole is close to the back, and the internal LED indicator will light up.

It is widely used in applications such as door sensor alarms, proximity sensors, rotation speed measurement and so on. The front side is the North pole, and the low level is output when the south pole signal of the magnetic field is sensed.

### Feature <a href="#product-feature" id="product-feature"></a>

* Unipolar Hall switch sensor
* Fast response and high sensitivity
* Status indicator
* Low-level output
* Lego compatible

### Application <a href="#application" id="application"></a>

* Door sensor alarm
* Magnetic field proximity sensing
* Speed measurement

### Specification <a href="#specification" id="specification"></a>

| Specification     | Parameter     |
| ----------------- | ------------- |
| Hall sensor       | A3144E \* 3   |
| Logic IC          | 74HC08D       |
| Status indication | RED LED       |
| Output Level      | Active Low    |
| Net weight        | 4g            |
| Gross weight      | 17g           |
| Product Size      | 24\*32\*8mm   |
| Package Size      | 136\*92\*11mm |

<figure><img src="../../.gitbook/assets/QQ_1728700241455.png" alt=""><figcaption></figcaption></figure>

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a concise and fast program writer, which has a built-in case program related to the product. It can be burned to the main control by simple steps to perform a series of function verification.&#x20;

[Download Windows Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/UNIT/For%20M5Core/EasyLoader_HALL_UNIT_With_M5Core.exe) [Download MacOS Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/MacOS/UNIT/EasyLoader_HALL_UNIT_With_M5Core.dmg)

{% embed url="https://m5stack.oss-cn-shenzhen.aliyuncs.com/video/Product_example_video/Unit/HALL_Unit.mp4" %}

**Description:**\
The screen displays the state of magnetic induction, low-level effective

### PinMap <a href="#pinmap" id="pinmap"></a>

| M5Core (PORT B)  | GPIO26 | GPIO36 | 5V | GND |
| ---------------- | ------ | ------ | -- | --- |
| Hall effect Unit |        | INPUT  | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="../../.gitbook/assets/image (423).png" alt=""><figcaption></figcaption></figure>

### Related Links <a href="#related-links" id="related-links"></a>

* **Datasheet**
  * [A3144E](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/3141Thru3144E_HALL.PDF)
