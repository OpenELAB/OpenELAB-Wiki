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

# M5Stack 8-Channel Servo Driver

{% hint style="info" %}
[**View M5Stack M5StickC 8-Channel Servo Driver HAT on OpenELAB**](https://openelab.io/products/8-channel-servo-driver-hat)

**Store SKU / option:** `M5-U076-B`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack M5StickC 8-Channel Servo Driver HAT

***

### Product Link

{% embed url="https://openelab.io/products/8-channel-servo-driver-hat" %}

### Description <a href="#description" id="description"></a>

**8Servos HAT v1.1** is an 8-channel servo driver module that works with the `M5StickC/C Plus` series. Adopt STM32F030F4 as main controller to drive servos with `PWM` (Pulse Width Modulation) signal. I2C communication. Embedded power management circuit to control servo ON/OFF with programming. With the rechargeable 16340 lithium battery (with the capacity of `700mAh`),It also supports 18350 lithium batteries, it can support Maximum `1.3A` load. Applied for robotic and DIY projects.

### Product Comparison <a href="#product-comparison" id="product-comparison"></a>

| Specifications             | 8Servos HAT | 8Servos HAT v1.1              |
| -------------------------- | ----------- | ----------------------------- |
| Motor power control        | /           | MOS tube control power on/off |
| Reverse Battery Protection | /           | With circuit protection       |
| Fixing hole                | /           | 4x fixing holes               |
| Programmable RGB LEDs      | SK6812      | /                             |
| I2C ADDR                   | 0x38        | 0x36                          |

### Features <a href="#features" id="features"></a>

* 8-channel servo driver
* Programmable servo power control
* 16340 lithium battery
* I2C protocol control (0x36)
* Reverse Battery Protection

### Applications <a href="#applications" id="applications"></a>

* Servo controller
* Robot control

### Specifications <a href="#specifications" id="specifications"></a>

| Specifications                 | Parameters                                   |
| ------------------------------ | -------------------------------------------- |
| Lithium Battery                | Specifications: 16340, Capacity: 700mAh      |
| Servo drive channel            | 8-channel                                    |
| Maximum drive load capacity    | 8-channel maximum load capacity: DC4.2V@1.3A |
| Driver no-load standby current | DC4.2V@2.2uA                                 |
| Fixing hole                    | M3                                           |
| Communication Protocol         | I2C:0x36                                     |
| Net weight                     | 28.3g                                        |
| Gross weight                   | 39.7g                                        |
| Product Size                   | 52\*38\*19mm                                 |
| Package Size                   | 75\*46\*29mm                                 |

### Pin Mapping <a href="#pin-mapping" id="pin-mapping"></a>

| M5StickC         | GPIO0 | GPIO26 | 3.3V | GND |
| ---------------- | ----- | ------ | ---- | --- |
| 8Servos HAT v1.1 | SDA   | SCL    | Vin  | GND |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/hat_8servos_1.1/hat_8servos_1.1_sch_01.webp" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Hat 8Servos v1.1](https://docs.m5stack.com/en/hat/Hat_8Servos_v1.1) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U076-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                                  | Model-specific reference                                                                                                                                                            |
| ------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic                              | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/583/Sch_8ServoV1.1.pdf)                                                                                |
| Official source: M5Hat-8Servos                    | [Read official source: m5hat-8servos](https://github.com/m5stack/M5Hat-8Servos)                                                                                                     |
| Example source: Hat\_8Servos1.1\_M5StickC.ino     | [Read example source: hat\_8servos1.1\_m5stickc.ino](https://github.com/m5stack/M5Hat-8Servos/blob/master/examples/Hat_8Servos1.1_M5StickC/Hat_8Servos1.1_M5StickC.ino)             |
| Example source: Hat\_8Servos1.1\_M5StickCPlus.ino | [Read example source: hat\_8servos1.1\_m5stickcplus.ino](https://github.com/m5stack/M5Hat-8Servos/blob/master/examples/Hat_8Servos1.1_M5StickCPlus/Hat_8Servos1.1_M5StickCPlus.ino) |
| Official source: HAT\_8Servos\_v1.1\_Firmware     | [Read official source: hat\_8servos\_v1.1\_firmware](https://github.com/m5stack/HAT_8Servos_v1.1_Firmware)                                                                          |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
