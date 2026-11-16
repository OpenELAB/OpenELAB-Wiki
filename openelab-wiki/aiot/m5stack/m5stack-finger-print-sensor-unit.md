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

# M5Stack Finger Print Sensor Unit

### M5Stack Finger Print Sensor Unit

***

### Product Link

{% embed url="https://openelab.io/products/finger-print-sensor-unit" %}

### Description <a href="#description" id="description"></a>

**FINGER** Unit is a fingerprint sensor based on the FPC1020A chipset.

This all-in-one fingerprint sensor makes fingerprint adding, verification and managing super simple.

Operated by the UART protocol, Compact size and ultra-low power consumption makes it very attractive to use around M5Stack series product. it performs fast fingerprint matching with highest security level and optimal user convenience. You can program to set the fingerprint recognition comparison level and different security level . if you ever consider secure your project with biometrics, don't forget to include this M5unit **FINGER**.

**This unit communicate with M5Core by UART protocol connected via PORTC**

UART settings:

* Baudrate(**default: 19200bps**)
* Start bits(1 bit)
* Stop bits(1 bit)
* Parity(no)

### Features <a href="#product-features" id="product-features"></a>

* Use capacitive area array semiconductor fingerprint sensor
* Each pixel of the sensor has a pixel quality of 256 gray levels
* 1: N recognition and 1: 1 verification function
* Support finger 360 rotation recognition
* Fingerprint comparison and search function

### Applications <a href="#applications" id="applications"></a>

* Fingerprint Attendance Machine
* Fingerprint Locker

### Specification <a href="#specification" id="specification"></a>

| Resources                 | Parameter                       |
| ------------------------- | ------------------------------- |
| Fingerprint capacity      | 150                             |
| Security level            | 0-9, default 5                  |
| Output format             | User name, image, feature value |
| Characteristic value size | 193Byte                         |
| Communication method      | UART (9600-115200)              |
| Working temperature       | -10 °C-60 °C                    |
| Relative humidity         | 20% -80%                        |
| Net weight                | 7g                              |
| Gross weight              | 20g                             |
| Product Size              | 48\*24\*8mm                     |
| Package Size              | 136\*93\*12mm                   |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/finger/finger_05.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/finger/finger_06.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/finger/finger_07.webp)

### EasyLoader <a href="#easyloader" id="easyloader"></a>

EasyLoader is a concise and fast program writer, which has a built-in case program related to the product. It can be burned to the main control by simple steps to perform a series of function verification.

[Download Windows Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Windows/UNIT/For%20M5Core/EasyLoader_Finger_UNIT_With_M5Core.exe) [Download MacOS Version Easyloader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/MacOS/UNIT/EasyLoader_Finger_UNIT_With_M5Core.dmg)

**Description:**\
FINGER UNIT use case: Press the left button to enter the fingerprint input mode. Press the middle button to enter the fingerprint identification mode.

### Pinout <a href="#pinmap" id="pinmap"></a>

| M5Core(GROVE C) | U2RXD | U2TXD | 5V | GND |
| --------------- | ----- | ----- | -- | --- |
| FINGER Unit     | TXD   | RXD   | 5V | GND |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/finger/finger_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* Protocol [**FINGER series communication protocol**](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/biovo_fingerprint_Protocol.pdf)
* Datasheet [**FPC1020A**](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/hat/1020A_datasheet_cn.pdf)

### Learn <a href="#learn" id="learn"></a>

<figure><img src="https://hackster.imgix.net/uploads/attachments/850196/wechat_image_20190408212425_K1g4UuFc1o.jpg?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[M5 Mini Hackathon](https://www.hackster.io/shasha-liu/m5-mini-hackathon-70225f)[M5 Mini Hackathon](https://www.hackster.io/shasha-liu/m5-mini-hackathon-70225f)A inner maker competition of M5Stack.

<figure><img src="https://hackster.imgix.net/uploads/attachments/929109/maxresdefault_BtLwZudGwx.jpg?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[M5Stack X Micro:bit](https://www.hackster.io/saltygood/m5stack-x-micro-bit-927101)[M5Stack X Micro:bit](https://www.hackster.io/saltygood/m5stack-x-micro-bit-927101)M5Stack and Micro:bit can control each other, thanks to the M5:Bit[M5Stack Based Anti-COVID Security Gate (Proof of Concept)](https://www.hackster.io/liemph/m5stack-based-anti-covid-security-gate-proof-of-concept-8a1724)[M5Stack Based Anti-COVID Security Gate (Proof of Concept)](https://www.hackster.io/liemph/m5stack-based-anti-covid-security-gate-proof-of-concept-8a1724)Gate/door fingerprint security system with body temperature checks for the anti-COVID measure.

<figure><img src="https://hackster.imgix.net/uploads/attachments/1193448/_mf5hDwJlzN.blob?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [M5Unit-Finger with M5Atom](https://github.com/m5stack/M5-FPC1020A/blob/master/examples/Unit_Finger_M5Atom/Unit_Finger_M5Atom.ino)
* [M5Unit-Finger with M5Core](https://github.com/m5stack/M5-FPC1020A/blob/master/examples/Unit_Finger_M5Core/Unit_Finger_M5Core.ino)
* [M5Unit-Finger with M5Core2](https://github.com/m5stack/M5-FPC1020A/blob/master/examples/Unit_Finger_M5Core2/Unit_Finger_M5Core2.ino)
* [M5Unit-Finger with M5StickC](https://github.com/m5stack/M5-FPC1020A/blob/master/examples/Unit_Finger_M5StickC/Unit_Finger_M5StickC.ino)
* [M5Unit-Finger with M5StickCPlus](https://github.com/m5stack/M5-FPC1020A/blob/master/examples/Unit_Finger_M5StickCPlus/Unit_Finger_M5StickCPlus.ino)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

**Feature Introduction**

Identify fingerprint information

* **get state** Read sensor status
* **get access** Return access
* **get id** Return ID
* **removeAll** Remove all fingerprint information
* **remove id** Remove fingerprint ID
* **add user id access** Add ID and access rights
* **read user with id access** The id and permission match do the following
* **getUnknown** Unknown id and permission to perform the following operations

**Usage**

* [Click here to download the UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/FINGER/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/finger/finger_uiflow_01.webp" alt=""><figcaption></figcaption></figure>
