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

# M5Stack RCA Audio/Video Module

{% hint style="info" %}
[**View M5Stack RCA Audio/Video Composite Module 13.2 on OpenELAB**](https://openelab.io/products/rca-video-composite-module)

**Store SKU / option:** `M5-M125`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack RCA Audio/Video Composite Module 13.2

***

### Product Link

{% embed url="https://openelab.io/products/rca-video-composite-module" %}

### Description <a href="#description" id="description"></a>

Module RCA is a composite signal expansion module for audio and video, using the common S-terminal RCA connector, divided into two (left and right channels) audio and one video output. The audio part adopts the I2S power amplifier chip PCM5102APWR scheme, which can realize 32-bit stereo audio signal output; In terms of video, the DAC analog video signal function of the main control ESP32 is applied, which can generate analog video signals with a resolution of no more than 864 x 576 (PAL, PAL\_M); The module contains a DC socket and a 9-24V to 5V DCDC circuit to supply power to the whole machine. This product is suitable for audio and video equipment that drives the S-terminal interface.

### Features <a href="#features" id="features"></a>

* RCA composite video audio output(Left and right channel audio interface)
* RCA female jack terminals
* 1 CVBS video output interface (GPIO25\&GPIO26 switch between two choices)
* 3.5mm headphone jack audio output
* Port C interface
* PCM5102 audio stereo DAC
* DC 9-24V to 5V Output (<5V, 3A)

### Applications <a href="#applications" id="applications"></a>

* RCA stereo output
* Composite video and audio output

### Specifications <a href="#specifications" id="specifications"></a>

| Resources             | Parameters                                                                |
| --------------------- | ------------------------------------------------------------------------- |
| Audio stereo DAC chip | Audio stereo DAC chip                                                     |
| interface             | RCA female seat                                                           |
| channel               | 1 CVBS video output interface (GPIO25\&GPIO26 switch between two choices) |
| Output signal         | Audio and video (3.5mm headphone jack output optional)                    |
| DCDC                  | MP1584EN                                                                  |
| Audio stereo DAC chip | PCM5102APWR                                                               |
| Product Size          | 54mm × 54mm × 19.7mm(外壳高13.2mm)                                           |
| Package Size          | 93mm × 63mm × 25mm                                                        |
| Product Weight        | 22.5g                                                                     |
| Package Weight        | 41.7g                                                                     |

### Related Link <a href="#related-link" id="related-link"></a>

* [MP1584EN\_LF\_Z](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/RCA%20Module%2013.2/MP1584EN_LF_Z.pdf)
* [PCM5102APWR](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/datasheet/module/RCA%20Module%2013.2/PCM5102APWR.pdf)

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/RCA%20Module%2013.2/img-89128e3c-87b6-4799-87f4-fcab5afbb59c.png" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/RCA%20Module%2013.2/img-58ddfb1e-695e-4db0-9f0a-7f5872e247e7.png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Module13.2 RCA](https://docs.m5stack.com/en/module/Module13.2_RCA) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`M125`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need        | Model-specific reference                                                                                  |
| ----------------------- | --------------------------------------------------------------------------------------------------------- |
| Electrical schematic    | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/552/SCH_Module_RCA_V1.0.pdf) |
| Example source: M5Stack | [Read example source: m5stack](https://github.com/m5stack/M5Stack/tree/master/examples/Unit/RCA)          |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
