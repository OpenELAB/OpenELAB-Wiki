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

# M5Stack RF UNIT 433MHz Transmitter

### M5Stack RF UNIT 433MHz Transmitter

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-rf-unit" %}

### Description <a href="#description" id="description"></a>

**RF433T** is a radio frequency (RF) transmitter, using SYN115 radio frequency transmitter IC, working frequency is 433.92MHz (using ASK modulation) commonly used by wireless controllers, built-in PCB antenna, stable signal transmission distance up to 10M, The output power reaches 10dBm. The exquisite and compact housing design can be embedded in a variety of radio frequency remote control applications. It is suitable for security alarm, wireless automatic meter reading, home and industrial automation, remote remote control, wireless data transmission and other system fields.

### Product Features <a href="#product-features" id="product-features"></a>

* Working frequency: 433.92MHz
* Data transmission rate 10kbps (ASK modulation)
* Output power 10dBm
* PCB antenna

### Applications <a href="#applications" id="applications"></a>

* Building Automation
* Security alarm
* Home and industrial automation
* Remote control
* Wireless data transmission and other system fields

### Specification <a href="#specification" id="specification"></a>

| Resources                     | Parameter     |
| ----------------------------- | ------------- |
| Transmitter IC                | SYN115        |
| Working current               | 12mA          |
| Stable communication distance | 10M           |
| Output Power                  | 10dBm         |
| Antenna type                  | PCB antenna   |
| Net weight                    | 6g            |
| Gross weight                  | 21g           |
| Product Size                  | 48\*24\*8mm   |
| Package Size                  | 136\*92\*12mm |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/rf433_t/rf433_t_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/rf433_t/rf433_t_06.webp)

### Pinout <a href="#pinmap" id="pinmap"></a>

| M5Core ( PORT B ) | GPIO26 | 5V | GND |
| ----------------- | ------ | -- | --- |
| RF433T            | TX     | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/rf433_t/rf433_t_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* **Datasheet**
  * [SYN115](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/rf433/C105184_SYN115_2019-08-28.PDF)

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [RF433 T/R Example](https://github.com/m5stack/M5Stack/blob/master/examples/Unit/RF433/RF433.ino)
