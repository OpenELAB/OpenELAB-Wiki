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

# M5Stack RF UNIT 433MHz Receiver (SYN513R)

{% hint style="info" %}
[**View M5Stack RF UNIT 433MHz Receiver (SYN513R) on OpenELAB**](https://openelab.io/products/rf-unit)

**Store SKU / option:** `M5-U113`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack RF UNIT 433MHz Receiver (SYN513R)

***

### Product Link

{% embed url="https://openelab.io/products/rf-unit" %}

### Description

**Unit RF433R** is an RF wireless receiver that uses the SYN531R RF receiver, operating at the commonly used frequency of 433.92MHz for wireless controllers (using ASK modulation). It features a built-in PCB antenna, providing stable signal reception up to 10 meters, with a typical reception sensitivity of -109dBm. Its compact and sleek design allows it to be embedded into various RF remote control applications. It is suitable for security alarms, wireless automatic meter reading, home and industrial automation, remote control, wireless data transmission, and other system fields.

### Features

* Operating frequency: 433.92MHz
* High sensitivity of -109dBm, with a reception rate of 1Kbps (ASK modulation)
* PCB antenna
* Excellent selectivity and noise suppression

### Specifications

| Specification                 | Parameter            |
| ----------------------------- | -------------------- |
| Receiver IC                   | SYN531R              |
| Operating current             | 8mA                  |
| Stable communication distance | 10M                  |
| Typical reception sensitivity | -109dBm              |
| Antenna type                  | PCB antenna          |
| Product Size                  | 48.0 x 24.0 x 8.0mm  |
| Product Weight                | 6.7g                 |
| Package Size                  | 138.0 x 93.0 x 9.0mm |
| Gross Weight                  | 12.1g                |

### Applications

* Building automation
* Security alarms
* Home and industrial automation
* Remote control
* Wireless data transmission and other system fields

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="../../.gitbook/assets/image (1011).png" alt=""><figcaption></figcaption></figure>

### Pin map

Unit RF433R

| HY2.0-4P | Black | Red | Yellow | White |
| -------- | ----- | --- | ------ | ----- |
| PORT.B   | GND   | 5V  | NC     | RX    |

### Model Size

<figure><img src="../../.gitbook/assets/image (1012).png" alt=""><figcaption></figcaption></figure>

### Documents

* [SYN531R](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/rf433/C77785_SYN531R_2018-06-20.PDF)

## Official documentation and development resources

Use [Unit RF433R](https://docs.m5stack.com/en/unit/Unit_RF433R) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U113`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need          | Model-specific reference                                                                                                               |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U113_Unit_RF433R/Structures)                 |
| Mechanical / CAD files    | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U113_Unit_RF433R/Structures/Unit_RF433R.stl) |
| Example source: RF433.ino | [Read example source: rf433.ino](https://github.com/m5stack/M5Stack/blob/master/examples/Unit/RF433/RF433.ino)                         |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
