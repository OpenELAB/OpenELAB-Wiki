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

# M5Stack 8-Angle Unit

### M5Stack 8-Angle Unit with Potentiometer

***

### Product Link

{% embed url="https://openelab.io/products/8-angle-unit" %}

### Description <a href="#description" id="description"></a>

UNIT 8Angle is an input unit integrating 8 adjustable potentiometers, internal STM32F030 microcomputer as acquisition and communication processor, and the host computer adopts I2C communication interface, each adjustable potentiometer corresponds to 1 RGB LED light, and there is also a physical toggle switch and its corresponding RGB LED light, containing 5V->3V3 DCDC circuit. The unit can be used for multi-channel absolute control value input, the corresponding RGB lamp can display different states, and the toggle switch can be used for multi-channel switching input. Can be used as a multi-degree-of-freedom robot or an application in music equalization.

### Features <a href="#features" id="features"></a>

* 8-channel adjustable potentiometer
* 8 channels correspond to RGB lights
* I2C communication
* Toggle switches can be used for multi-channel switching inputs

### Applications <a href="#applications" id="applications"></a>

* Multi-degree-of-freedom robot joint control
* Music equalization control aspects

### Specification <a href="#specification" id="specification"></a>

| Resources                 | Parameters             |
| ------------------------- | ---------------------- |
| MCU                       | STM32F030F4P6          |
| LDO                       | ME6210A33M3G           |
| RGB                       | SK6812-3535            |
| Input voltage             | 5v                     |
| I2C communication address | 0x43                   |
| Product Size              | 128mm × 24mm ×22.7mm   |
| Package Size              | 130mm × 27.7mm ×27.7mm |
| Product Weight            | 34.9g                  |
| Package Weight            | 44.3g                  |

![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/img-0429282b-d8cb-42f0-84f4-2191a6685622.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/img-d1261679-1f72-4615-8d83-b5bc6be59502.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/img-75a3647b-6ed6-44ff-8a6b-f15b6c77f0ae.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/img-55f9289a-53b8-4708-a0f0-86fc7566419a.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/img-1fa89582-f023-4500-bd24-6893270d9e33.webp)![](https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/img-dad0216e-e1c3-4258-b84e-4b70cbb6d5b2.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [STM32F030F4P6](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/STM32F030F4P6.pdf)
* [LDO:ME6210A33M3G](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/unit/Unit%208Angle/ME6210A33M3G.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/img-f3c3ca5d-30f7-456c-a6c5-d40d0beca790.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/img-4b39398e-5590-43b9-8dfe-84eb4aec5312.png" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [Arduino Example](https://github.com/m5stack/M5Unit-8Angle)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/arduinoCase-1668070916820Address.png" alt=""><figcaption></figcaption></figure>

* [8Angle Firmware](https://github.com/m5stack/M5Unit-8Angle-Internal-FW)

#### UIFlow <a href="#uiflow" id="uiflow"></a>

* [Uiflow Example](https://flow.m5stack.com/?examples=unit_8angle_demo)

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/uiflowCase-1668078544524image.png" alt=""><figcaption></figcaption></figure>

### UIFlow Blocks <a href="#uiflow-blocks" id="uiflow-blocks"></a>

* Init I2C address

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/blockIntro-169813e4-c5d9-447d-b908-39add675f823.png" alt=""><figcaption></figcaption></figure>

* Get ADC 12bit value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/blockIntro-6866d489-d034-4b24-b6df-f6845d2c3167.png" alt=""><figcaption></figcaption></figure>

* Get ADC 8bit value

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/blockIntro-595efd0b-ab27-4ebb-a4c8-b4bd4e0fa00c.png" alt=""><figcaption></figcaption></figure>

* Get button status

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/blockIntro-dd0249e4-670e-4ae1-afdc-a62c6f61c20e.png" alt=""><figcaption></figcaption></figure>

* Get FW version or I2C address

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/blockIntro-3177e999-3df8-4de6-a7c3-ac0da6f49311.png" alt=""><figcaption></figcaption></figure>

* Set single RGB LED color

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/blockIntro-eac7a93a-3769-4200-9a0d-41f9de5ce0ba.png" alt=""><figcaption></figcaption></figure>

* Set multiple RGB LED color

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%208Angle/blockIntro-c0105e25-f183-4ba7-bd06-855ca44779be.png" alt=""><figcaption></figcaption></figure>

* Set I2C address

<figure><img src="../../.gitbook/assets/image (933).png" alt=""><figcaption></figcaption></figure>
