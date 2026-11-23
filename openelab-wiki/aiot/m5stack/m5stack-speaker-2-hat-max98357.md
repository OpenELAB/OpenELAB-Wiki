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

# M5Stack Speaker 2 Hat (MAX98357)

{% hint style="info" %}
**Manufacturer reference.** A matching current OpenELAB global-store listing has not been verified for this model/revision. Use the hardware label and the exact official reference below; do not select firmware or wiring from a similar store product.
{% endhint %}

### M5Stack Speaker 2 Hat (MAX98357)

***

### Product Link

{% embed url="https://security.feishu.cn/link/safety?target=https%3A%2F%2Fopenelab.io%2Fproducts%2Fm5stack-speaker-2-hat&scene=ccm&logParams=%7B%22location%22%3A%22ccm_sheet%22%7D&lang=zh-CN&from=from_parent_sheet" %}

### Introduction

HAT-SPK2 is a speaker designed specifically for the M5SticKC PLUS platform. It features a built-in MAX98357 digital audio I2S amplifier IC and a 1W speaker, providing high-quality audio output. The speaker supports audio input with a sample rate ranging from 16-bit, 32kHz to 192kHz, ensuring excellent audio reproduction.\
HAT-SPK2 is equipped with built-in short circuit protection, which safeguards the speaker and the connected devices in case of a short circuit. Additionally, it includes over-temperature protection, preventing overheating and ensuring safe operation even during extended use.\
This speaker module is suitable for a wide range of audio applications. Whether you're building a portable music player, a sound effects generator, or any other project that requires clear and amplified audio output, the HAT-SPK2 provides a reliable and convenient solution.

<figure><img src="../../.gitbook/assets/image (513).png" alt=""><figcaption></figcaption></figure>

### Features

* HIGH-QUALITY AUDIO OUTPUT: SUPPORTS 16-BIT, 32KHZ TO 192KHZ SAMPLE RATE AUDIO INPUT
* Multiple output modes: including mono and stereo, as well as audio input formats such as I2S, left-justified, and right-justified
* Stability and reliability: Built-in short-circuit protection and over-temperature protection
* Programming platforms: Arduino, uiflow

### Specifications

| Resources                   | Parameters                       |
| --------------------------- | -------------------------------- |
| Power output                | Maximum 20W                      |
| Signal-to-noise ratio       | 103dB                            |
| Distortion rate             | 0.1%                             |
| Supply voltage              | 4.5v-5.5v                        |
| Operating temperature range | 0-40°C                           |
| Enter the audio format      | I2S, left-aligned, right-aligned |
| Sample rate                 | 32kHz to 192kHz                  |
| Control interface           | I2C、SPI、GPIO                     |
|                             |                                  |
| Product Size                | 24mm × 18.6mm ×13.7mm            |
| Package Size                | 136mm × 92mm ×13mm               |
| Product Weight              | 4.6g                             |
| Package Weight              | 8.1g                             |

### Dimensions

<figure><img src="../../.gitbook/assets/image (524).png" alt=""><figcaption></figcaption></figure>

### How to Use

Attach the M5Stack Speaker 2 Hat to the top of your M5Stack Core. Ensure the hat is securely connected to the core's GPIO pins.

## Official documentation and development resources

Use [Hat SPK2](https://docs.m5stack.com/en/hat/Hat_SPK2) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U055-B`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                                     |
| ---------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic         | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/580/Sch_Hat_SPK2.pdf)                           |
| Example source: SPEAKER2.ino | [Read example source: speaker2.ino](https://github.com/m5stack/M5StickC-Plus/blob/master/examples/Hat/SPEAKER2/SPEAKER2.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
