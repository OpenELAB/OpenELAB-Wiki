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

# M5Stack I2C Hub 1 to 6 Expansion Unit

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5Stack I2C Hub 1 to 6 Expansion Unit

***

### Product Link

No matching current OpenELAB.io listing was found for the product version documented here.

### Description <a href="#description" id="description"></a>

**PaHUB2**, is an I2C Expandable Hub, which can expand a single I2C HY2.0-4P interface and connects up to 6 I2C channels. It allows you to mount slave devices with the same I2C address (by polling control the different channels to achieve in-device coexistence). Embedded PCA9548AP-I2C multi-channel switch IC, Save you worries with insufficient I2C interface of the expansion.

### Features <a href="#product-features" id="product-features"></a>

* I2C HY2.0-4P PORTA expansion
* 2x LEGO compatible holes
* Support multiple nesting
* 1-6 expansion

### Application <a href="#application" id="application"></a>

* I2C device expansion

### Specification <a href="#specification" id="specification"></a>

| Specifications         | Parameters                                           |
| ---------------------- | ---------------------------------------------------- |
| Channel Control IC     | PCA9548AP                                            |
| Communication protocol | I2C: 0x70 (can be modified by resistance A0, A1, A2) |
| Net weight             | 7g                                                   |
| Gross weight           | 19g                                                  |
| Product size           | 48 \* 24 \* 12mm                                     |
| Packing size           | 67 \* 53 \* 12mm                                     |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/pahub2/pahub2_05.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/pahub2/pahub2_06.webp)

Note: When it's connected, the PaHUB2 will be polling control the different channels to achieve in-device coexistence. Please pay attention to the order of channels when programming.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pahub/pahub_08.webp" alt=""><figcaption></figcaption></figure>

Please refer to the schematic and PCA9548AP data manual, the Unit can modify the I2C address of the device by adapting the level combination of A0\~A2 pins. (The default address is 0x70)

3 Position of Welding patch are reserved on the PCB board of the Unit, A0-A2 respectively, as shown in the figure below.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pahub/pahub_09.webp" alt=""><figcaption></figcaption></figure>

After welding the 0 ohm resistor, the corresponding pin will change from low level to high level. The pin level combination and its corresponding I2C address are shown in the table below.

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pahub/pahub_10.webp" alt=""><figcaption></figcaption></figure>

### EasyLoader <a href="#easyloader" id="easyloader"></a>

[Click to download EasyLoader](https://m5stack.oss-cn-shenzhen.aliyuncs.com/EasyLoader/Unit/EasyLoader_PaHUB.exe)

1.EasyLoader is a concise and fast program burner, which contains the test program used by Pahub2 & M5Core.

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pahub/pahub_sch_01.webp" alt=""><figcaption></figcaption></figure>

### Related Link <a href="#related-link" id="related-link"></a>

* **Datasheet**
  * [**PCA9548AP**](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/pahub2/pca9548a.pdf)

### Learn <a href="#learn" id="learn"></a>

<figure><img src="https://hackster.imgix.net/uploads/attachments/1006384/1571711554666761_CjW8O5vLl6.gif?auto=format%2Ccompress&#x26;gifq=35&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[Smart Planting System](https://www.hackster.io/sophiaxue/smart-planting-system-a842d7)[Smart Planting System](https://www.hackster.io/sophiaxue/smart-planting-system-a842d7)Building a smart planting system using M5Stack to monitor the lights, humidity, temperature, watering your plant automatically.

<figure><img src="https://hackster.imgix.net/uploads/attachments/1255281/_RVOgnVLgPg.blob?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[Q-Bot](https://www.hackster.io/team_4/q-bot-f58530)[Q-Bot](https://www.hackster.io/team_4/q-bot-f58530)We aim to build a robot that is effective in sanitizing surfaces without putting cleaners in harm's way.

<figure><img src="https://hackster.imgix.net/uploads/attachments/1264431/_UMWGX284gA.blob?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[3 in 1 Sanitizer Dispenser](https://www.hackster.io/386917/3-in-1-sanitiser-dispenser-d18432)[3 in 1 Sanitizer Dispenser](https://www.hackster.io/386917/3-in-1-sanitiser-dispenser-d18432)We have devised with an innovation that dispenses hand sanitizer, measures the temperature of user, shows the count of people in vicinity.

<figure><img src="https://hackster.imgix.net/uploads/attachments/1257840/_Wl3Zxp4yYH.blob?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[Hand Hygienics](https://www.hackster.io/e1-team-2/hand-hygienics-5e04a9)[Hand Hygienics](https://www.hackster.io/e1-team-2/hand-hygienics-5e04a9)Hand Hygienics aims to reduce spread of Covid-19 through contact.[SEAM \[Safe-Entry Access Machine\]](https://www.hackster.io/seam/seam-safe-entry-access-machine-de834d)

<figure><img src="https://hackster.imgix.net/uploads/attachments/1255277/_zELd2Tpa8J.blob?auto=compress%2Cformat&#x26;w=400&#x26;h=300&#x26;fit=min" alt=""><figcaption></figcaption></figure>

[SEAM \[Safe-Entry Access Machine\]](https://www.hackster.io/seam/seam-safe-entry-access-machine-de834d)An automatic system to perform the tasks of Safe Entry. It consist an adjustable Thermometer, RFID / QR Code Check in and Counting.

### Example <a href="#example" id="example"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [Arduino Test example](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/PaHUB_TCA9548A)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

**Feature Introduction**

![](https://static-cdn.m5stack.com/resource/docs/static/image/Units/Pa.HUB.webp)

* **set pos state** Set designated port I2C
* **set pos open** Set the port to enable I2C
* **set port value** Set up port I2C

**Usage**

* [UIFlow example](https://github.com/m5stack/M5-ProductExampleCodes/tree/master/Unit/PaHUB/UIFlow)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/pahub/pahub_uiflow_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit PaHub v2.0](https://docs.m5stack.com/en/unit/Unit_PaHub_v2.0) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U040-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                                         |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U040-B_Unit_PaHub_v2.0/Structures)                     |
| Mechanical / CAD files       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U040-B_Unit_PaHub_v2.0/Structures/Unit_PaHub_v2.0.stl) |
| Official source: M5Unit-HUB  | [Read official source: m5unit-hub](https://github.com/m5stack/M5Unit-HUB)                                                                        |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_pahub_v2)                                             |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
