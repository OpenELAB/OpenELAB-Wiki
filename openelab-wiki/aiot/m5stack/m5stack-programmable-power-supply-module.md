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

# M5Stack Programmable Power Supply Module

{% hint style="info" %}
[**View M5Stack Programmable Power Supply Module 13.2 on OpenELAB**](https://openelab.io/products/programmable-power)

**Store SKU / option:** `M5-M137`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Programmable Power Supply Module 13.2

***

### Product Link

{% embed url="https://openelab.io/products/programmable-power" %}

### Description <a href="#description" id="description"></a>

**PPS Module 13.2** is a programmable power supply module. This module employs STEP-DOWN buck technology, supports a wide DC 9-36V input voltage, and integrates an STM32 control processor and AD8418 high-resolution current amplifier. Through high-precision closed-loop control, it achieves a rated output power of 100W (peak 150W) with high-precision current and voltage output, capable of delivering 0.5\~30V/0\~5A, with a read-back accuracy of ±30mV/5mA. Additionally, the module incorporates isolation chips CA-IS3020S and B0505S-1WR3, providing electrical isolation for both the power supply and the communication bus. The output interface uses standard 4MM banana plug sockets, with a positive and negative pole spacing of 19mm. Each module is calibrated for full-range accuracy before leaving the factory, and users will need to separately purchase a compatible DC power adapter. This module is suitable for use in scientific research experiments, industrial automation, embedded system development, and DIY projects requiring an adjustable power supply.

NOTESIf you use PPS Module 13.2, connect an external 12VDC power supply. Otherwise, the system displays a message indicating that no I2C device is available and the device does not work. The maximum output depends on the output capacity of the input DC power supply.Power detectionpower input detection interface (5-24V@5A):\
\- USB PD power input\
\- Relay Base power input

### Features <a href="#features" id="features"></a>

* DC 9-36V wide voltage input, output 0.5\~30V/0\~5A
* High precision rated output power 100W (peak 150W)
* With electrical isolation safety performance
* Standard 4mm banana socket, positive and negative electrode spacing 19mm
* Works with Core/Core2/CoreS3 series hosts

### Includes <a href="#includes" id="includes"></a>

* 1x Module13.2-PPS

### Applications <a href="#applications" id="applications"></a>

* Scientific research experiment
* Automation in industry
* Embedded system development
* Adjustable power supply DIY project

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                                  | Parameters                 |
| ------------------------------------------ | -------------------------- |
| MCU                                        | STM32G030F6P6              |
| Power and communication bus isolation chip | CA-IS3020S and B0505S-1WR3 |
| Current amplifier chip                     | AD8418                     |
| Input voltage                              | DC 9-36V                   |
| Output power                               | 100W (Peak 150W)           |
| Output current voltage                     | 0.5\~30V/0\~5A             |
| Accuracy                                   | ±30mV/5mA                  |
| Standby current                            | Avg:DC36V/12mA             |
| Working current                            | Avg:DC36V/32mA             |
| Banana head size (spacing)                 | 4MM (pitch 19mm)           |
| I2C communication address                  | 0x35                       |
| Operating temperature                      | 0-40°C                     |
| Product Size                               | 68.5\*54\*19.7mm           |
| Package Size                               | 130\*95\*24mm              |
| Product Weight                             | 43.6g                      |
| Package Weight                             | 64.5g                      |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/Module13.2-PPS/img-f67041ca-943d-4f1f-b3e5-f50f2242ab16.png" alt=""><figcaption></figcaption></figure>

* [Schematic diagram of main PCB](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/M137%20Module13.2-PPS/Sch_M5PPS_V1.3.pdf)
* [Isolation part schematic diagram](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/module/M137%20Module13.2-PPS/Sch_M5PPS_ISO_V1.3.pdf)

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/Module13.2-PPS/pinMap-eacec569-2c56-4341-b89d-6ab47fd07324.png" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/Module13.2-PPS/img-44fd167e-cfab-4a22-8ad4-675ee9cbf907.jpg" alt=""><figcaption></figcaption></figure>

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/module/Module13.2-PPS/protocol-c7f69a58-d308-4913-bd62-a32b04ccd12e.png" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (373).png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Module13.2 PPS](https://docs.m5stack.com/en/module/Module13.2_PPS) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`M137`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                          | Model-specific reference                                                                                 |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| Electrical schematic                      | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/563/Sch_M5PPS_V1.3.pdf)     |
| Electrical schematic                      | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/563/Sch_M5PPS_ISO_V1.3.pdf) |
| Official source: M5Module-PPS             | [Read official source: m5module-pps](https://github.com/m5stack/M5Module-PPS)                            |
| Arduino development tutorial              | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/module/module13.2_pps)  |
| Official source: M5Module-PPS-UserDemo    | [Read official source: m5module-pps-userdemo](https://github.com/m5stack/M5Module-PPS-UserDemo)          |
| Official source: M5Module-PPS-Internal-FW | [Read official source: m5module-pps-internal-fw](https://github.com/m5stack/M5Module-PPS-Internal-FW)    |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
