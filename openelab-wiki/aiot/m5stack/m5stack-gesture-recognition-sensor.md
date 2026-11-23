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

# M5Stack Gesture recognition sensor

{% hint style="info" %}
[**View M5Stack Gesture Unit with PAJ7620U2 3D Gesture Sensor on OpenELAB**](https://openelab.io/products/gesture-recognition-sensor)

**Store SKU / option:** `M5-U127`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Gesture recognition sensor

***

### Product Link

{% embed url="https://openelab.io/products/gesture-recognition-sensor" %}

### Description <a href="#description" id="description"></a>

**PAJ7620U2 touchless Gesture Moving Recognition Sensor Recognize up to 9 Gestures** It's a touchless 3D gesture recognition sensor via the `I2C` interface that integrates with `PAJ7620U2`. You could feel the charm of `9 kinds of gesture recognition` by default program. In addition to adding more complex gestures, the recognition rate is up to 240Hz with higher anti-interference capability. This sensor is reliable for its recognition process is intuitive and has low power consumption (operating current only 2.2mA) that allows you to control a robot in accordance with your hand's movement. This is particularly useful in interactive applications.

* `Support 9 gestures:`
  * `Up`, `Down`, `Left`, `Right`, `Front`, `Back`, `Clockwise`, `Counterclockwise`, `Quick wave`

### Features <a href="#features" id="features"></a>

* PAJ7620U2 gesture sensor / I2C interface
* Recognizable gestures up to 9 kinds
* Faster, more accurate.
* Support for customizing and adding recognition gesture combinations (support developing)
* Effective recognition distance: 5cm-15cm
* Embedded infrared LED and optical lens, be able to work in low-light even dark environment
* Development Platform: Arduino, UIFlow

### Applications <a href="#applications" id="applications"></a>

* Touchless remote control
* Robot interaction
* Human-Computer Interaction
* Gesture light control

### Specification <a href="#specification" id="specification"></a>

| Resources                      | Parameters                                                                |
| ------------------------------ | ------------------------------------------------------------------------- |
| Gesture recognition frequency  | Typical value: 120Hz, maximum 240Hz                                       |
| Support gestures               | 9 built-in + 4 software extensions + support software algorithm expansion |
| Effective recognition distance | 5cm-15cm                                                                  |
| R Ambient light immunity       | <100k Lux                                                                 |
| Communication interface        | I2C, addr: 0x73                                                           |
| Working current                | 2.2mA                                                                     |
| Product Size                   | 24\*32\*8mm                                                               |
| Package Size                   | 136\* 92\* 13mm                                                           |
| Product Weight                 | 4.3g                                                                      |
| Package Weight                 | 16.4g                                                                     |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/img-b7f9f0d1-68b3-470a-8072-f942cd6ce13e.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/img-441d6677-53f0-4a56-98a1-8c63fb988678.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/img-c330684a-d6ec-485e-b392-f8e22b14dfd0.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [PAJ7620U2 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/gesture/paj7620u2_datasheet.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/img-023620e1-ce53-412b-a928-eb79681e0af6.webp" alt=""><figcaption></figcaption></figure>

### EasyLoader <a href="#easyloader" id="easyloader"></a>

* **Windows**
  * [Gesture Unit](https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/ezLoader-b244c14c-9556-4e26-8a6f-f98f3324c02e.exe)

### Pinout <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/pinMap-b8fd14bf-5e61-41e8-91a7-2ecd422c90df.png" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [GESTURE\_PAJ7620U2 - with M5Core](https://github.com/m5stack/M5Stack/blob/master/examples/Unit/GESTURE_PAJ7620U2/GESTURE_PAJ7620U2.ino)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [UIFlow Unit Example](https://flow.m5stack.com/?examples=unit_gesture_demo)

### UIFlow Blocks <a href="#uiflow-blocks" id="uiflow-blocks"></a>

* init

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/blockIntro-ce8f8bf2-8e5a-48c6-86a3-1d36cede1545.png)

* get gesture

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/blockIntro-8c67b769-ed91-4136-b7d5-a715b967e0ad.png)

* get description(value of get gesture)

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/blockIntro-90693f43-c736-4c0c-b028-06a293c6f5bf.png)

* set highrate(True or False)

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/blockIntro-9db36775-8ad7-46f0-8b77-bec0c0e07aff.png)

* gesture value Returns the value of the selected Gesture. Mainly used in logical operations.

![image](https://static-cdn.m5stack.com/resource/docs/products/unit/Gesture/blockIntro-d20437ac-17eb-4e9f-9b4c-107b36b4cf73.png)

## Official documentation and development resources

Use [Unit Gesture](https://docs.m5stack.com/en/unit/Unit_Gesture) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U127`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                       | Model-specific reference                                                                                                                            |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files                 | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U127_Unit_Gesture/Structures)                             |
| Mechanical / CAD files                 | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U127_Unit_Gesture/Structures/Unit_Gesture.stl)            |
| Example source: GESTURE\_PAJ7620U2.ino | [Read example source: gesture\_paj7620u2.ino](https://github.com/m5stack/M5Stack/blob/master/examples/Unit/GESTURE_PAJ7620U2/GESTURE_PAJ7620U2.ino) |
| UIFlow1 workflow                       | [Read uiflow1 workflow](https://docs.m5stack.com/en/uiflow/blockly/unit/gesture)                                                                    |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
