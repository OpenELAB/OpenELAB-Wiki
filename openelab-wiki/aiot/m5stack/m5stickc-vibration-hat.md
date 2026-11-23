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

# M5StickC Vibration HAT

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5StickC Vibration HAT

***

### Product Link

{% embed url="https://security.feishu.cn/link/safety?target=https%3A%2F%2Fopenelab.io%2Fproducts%2Fm5stickc-vibration-hat&scene=ccm&logParams=%7B%22location%22%3A%22ccm_sheet%22%7D&lang=zh-CN&from=from_parent_sheet" %}

### Introduction

HAT-Vibrator is a specialized vibrating motor designed specifically for the M5StickC/C-Plus series. Featuring a cylindrical iron core patch Z3OC1T8219731 motor, it operates at a speed of 12000 RPM. This product offers a wide range of vibration effects, including adjustable vibration levels, "click" effects, various buzzer effects, and synchronization with music or audio input. Its versatility makes it suitable for integration into a variety of electronic devices, serving as an effective information prompt and providing tactile feedback.

With HAT-Vibrator, electronic products can benefit from enhanced user interaction and engagement. It can be utilized as a means of conveying important information or alerts, such as notifications, alarms, or reminders. Additionally, the vibration motor can be used to provide haptic feedback, allowing users to experience tactile sensations and responses in touch-based applications. Its compatibility with the M5StickC/C-Plus series ensures seamless integration and ease of use.

<figure><img src="../../.gitbook/assets/image (515).png" alt=""><figcaption></figcaption></figure>

### Features

* The motor rotates clockwise
* Rotational speed: 12000RPM
* Compatible with StickC/C-PLUS
* Supported platforms UIFlow, Arduino .

### Specifications

| Resources                    | Parameters                         |
| ---------------------------- | ---------------------------------- |
| Vibrator                     | Z3OC1T8219731 motor                |
| Motor construction           | 4mm×3mm cylindrical core SMT motor |
| Motor Number of magnet poles | 2-poles（inner magnet type）         |
| Quota voltage                | 3.0V                               |
| Rated current                | 85mA                               |
| Rated speed                  | 12000RPM                           |
| Using voltage                | 2.3V-4.5V                          |
| Operating conditions         | 0\~95%RH , 0-40℃                   |
| Vibration Frequency          | 10 to 55Hz                         |
| Product Size                 | 24mm × 21mm × 14mm                 |
| Package Size                 | 136mm × 92mm × 14mm                |
| Product Weight               | 4.7g                               |
| Package Weight               | 7.1g                               |

### Pinout

<figure><img src="../../.gitbook/assets/image (495).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (496).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Hat Vibrator](https://docs.m5stack.com/en/hat/Hat_Vibrator) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U159`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                     |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/614/Sch_HAT-Vibrator.pdf)                       |
| Example source: VIBRATOR.ino | [Read example source: vibrator.ino](https://github.com/m5stack/M5StickC-Plus/blob/master/examples/Hat/VIBRATOR/VIBRATOR.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
