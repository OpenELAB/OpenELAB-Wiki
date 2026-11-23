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

# M5Stack 8-Encoder Unit

{% hint style="info" %}
[**View M5Stack 8Encoder Unit with 8 Rotary Encoders and RGB LEDs on OpenELAB**](https://openelab.io/products/8-encoder-unit)

**Store SKU / option:** `M5-U153`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack 8-Encoder Unit (STM32F030)

***

### Product Link

{% embed url="https://openelab.io/products/8-encoder-unit" %}

### Description <a href="#description" id="description"></a>

UNIT 8EnCoder is a set of 8 rotary encoders as one of the input unit, the internal use of STM32 single-chip microcomputer as the acquisition and communication processor, and the host computer using I2C communication interface, each rotary encoder corresponds to 1 RGB LED light, encoder in addition to left and right rotation, but also radially pressed, in addition to a physical toggle switch and its corresponding RGB LED light, including 5V->3V3 DCDC circuit. The unit can be used for the input of multi-channel relative control values, the corresponding RGB lamp can display different statuses, and the toggle switch can be used for the input of multi-channel switching quantities. It can be used as a multi-degree-of-freedom robot or music equalization application.

### Features <a href="#features" id="features"></a>

* 8-channel Rotary encoder
* 8 channels correspond to RGB lights
* I2C communication
* Toggle switches can be used for multi-channel switching inputs
* Radial press function
* HY2.0-4P interface
* 2x LEGO compatible holes

### Applications <a href="#applications" id="applications"></a>

* Multi-degree-of-freedom robot joint control
* Music equalization control aspects
* Multi-channel light control

### Specification <a href="#specification" id="specification"></a>

| Resources                 | Parameters             |
| ------------------------- | ---------------------- |
| MCU                       | STM32F030C8T6          |
| RGB                       | WS2812C-2020           |
| Input voltage             | 5v                     |
| I2C communication address | 0x41                   |
| Product Size              | 128mm × 24mm ×22.7mm   |
| Package Size              | 130mm × 27.7mm ×27.7mm |
| Product Weight            | 42.8g                  |
| Package Weight            | 52.4g                  |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/img-f58d98c0-09a8-4f57-b884-b75fee80c118.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/img-d69a78f9-230b-44cc-be35-09c2b50060f9.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/img-421a38df-45cc-478f-9501-7aba4e9fc29a.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/img-8dd7a2f6-b40d-4782-a012-4dd6927011f2.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/img-3f5f0005-ea48-4ab7-9dbc-4f864e935cbc.webp) ![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/img-878d09f7-aab2-4fda-a1f6-ecaab4a6cbf6.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [STM32F030C8T6](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/Unit%208Encoder/STM32F030C8T6.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/img-78aeb50b-01fe-4e48-81a4-e38bb31711bf.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/img-55ebb676-2b3c-4b9a-a192-b85bf0d1a87c.png" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [Arduino Example](https://github.com/m5stack/M5Unit-8Encoder)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/arduinoCase-1668582336160map.png" alt=""><figcaption></figcaption></figure>

* [I2C timing diagram](https://docs.m5stack.com/en/unit/UNIT%208EnCoder)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/arduinoCase-1668596208234i2c1.png" alt=""><figcaption></figcaption></figure>

* [Compared to the standard I2C's ReStart, 8EnCoder has an additional stop bit, which is identified as shown in the following figure:](https://docs.m5stack.com/en/unit/UNIT%208EnCoder)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/arduinoCase-1668596502197image.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/arduinoCase-1668596399708i2c2.png" alt=""><figcaption></figcaption></figure>

* [Firmware](https://github.com/m5stack/M5Unit-8Encoder-Internal-FW)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [Uiflow Example](https://flow.m5stack.com/?examples=unit_8encoder_demo)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/uiflowCase-1668078573571image.png" alt=""><figcaption></figcaption></figure>

### UIFlow Blocks <a href="#uiflow-blocks" id="uiflow-blocks"></a>

* Init I2C address

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-ab7443d9-fa83-4a0a-a6c9-fb656032ab88.png" alt=""><figcaption></figcaption></figure>

* Get counter value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-01a75ba3-df33-42aa-8303-b3a507fb32e3.png" alt=""><figcaption></figcaption></figure>

* Get increment value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-2e8aad3a-111c-40c4-8607-57f1e71bb50a.png" alt=""><figcaption></figcaption></figure>

* Get button status

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-30bea225-3c38-4382-935b-f616ccf83344.png" alt=""><figcaption></figcaption></figure>

* Get switch status

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-b049d4d2-ac4a-47bf-80a9-9ccba259e24a.png" alt=""><figcaption></figcaption></figure>

* Get device FW version or I2C address

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-e784a50f-ffba-46c9-8728-8428af236325.png" alt=""><figcaption></figcaption></figure>

* Set counter value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-0fdf945e-a493-490a-96ee-e84e4d02c0fd.png" alt=""><figcaption></figcaption></figure>

* Reset counter value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-2c08827a-2cac-461c-84ca-7232c44dac48.png" alt=""><figcaption></figcaption></figure>

* Set single RGB LED color

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-5865ca4f-b15c-455f-b989-53dbf4627311.png" alt=""><figcaption></figcaption></figure>

* Set multiple RBG LED color

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208EnCoder/blockIntro-c416f8fa-c405-4440-8a8f-4bcf61880e9d.png" alt=""><figcaption></figcaption></figure>

* Set I2C address

<figure><img src="../../.gitbook/assets/image (417).png" alt=""><figcaption></figcaption></figure>

<br>

## Official documentation and development resources

Use [Unit 8Encoder](https://docs.m5stack.com/en/unit/Unit_8Encoder) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U153`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                             | Model-specific reference                                                                                                                   |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Electrical schematic                         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/607/SCH_UNIT_8Encoder_V1.01.pdf)                              |
| Mechanical / CAD files                       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U153_Unit_8Encoder/Structures)                   |
| Mechanical / CAD files                       | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U153_Unit_8Encoder/Structures/Unit_8Encoder.stl) |
| Official source: M5Unit-8Encoder             | [Read official source: m5unit-8encoder](https://github.com/m5stack/M5Unit-8Encoder)                                                        |
| Official source: M5Unit-8Encoder-Internal-FW | [Read official source: m5unit-8encoder-internal-fw](https://github.com/m5stack/M5Unit-8Encoder-Internal-FW)                                |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
