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

# M5Stack Ultrasonic

{% hint style="info" %}
[**View M5Stack Ultrasonic Distance Unit I/O on OpenELAB**](https://openelab.io/products/ultrasonic-distance-unit-1)

**Store SKU / option:** `M5-U098-B2`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Ultrasonic Distance Unit I/O

***

### Product Link

{% embed url="https://openelab.io/products/ultrasonic-distance-unit-1" %}

### Description <a href="#description" id="description"></a>

**UNIT SONIC IO** is a **GPIO** interface ultrasonic range sensor. This module features an RCWL-9620 ultrasonic distance measurement chip with a 16mm probe, which the ranging accuracy can reach **2cm-450cm** (accuracy up to ±2%). This sensor determines the distance to a target by measuring time lapses between the transmitting and receiving of the pulse signal, users can directly obtain the distance value through IO control mode. It is ideal to apply in robotics obstacle avoidance, fluid level detection, and other applications that require you to perform measurements.

Note: When the measurement is more than 3.5m, there will be a slight delay in the response of the distance measurement data.

### Features <a href="#features" id="features"></a>

* RCWL-9620
* GPIO communication interface
* Measuring range: 2cm-450cm
* Protective housing
* Built-in temperature compensation, reduce the temperature drift
* Support UIFlow platform

### Applications <a href="#applications" id="applications"></a>

* Robot Obstacle Avoidance
* Fluid Level Detection
* Sitting Posture Detection

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                        | Parameters       |
| -------------------------------- | ---------------- |
| Ultrasonic Ranging Single Chip   | RCWL-9620        |
| Range                            | 2cm-450cm        |
| Probe Specifications             | 16mm             |
| Receiving/Transmitting Frequency | 40KHz            |
| Receiving sensitivity            | -65dB            |
| Pointing angle                   | 60°              |
| Measurement accuracy             | ±2%              |
| Measurement period               | 50ms             |
| Working current                  | 3mA              |
| Product Size                     | 56 \* 24 \* 15mm |
| Package Size                     | 76 \* 47 \* 29mm |
| Product Weight                   | 11.5g            |
| Package Weight                   | 26g              |

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%20SONIC%20IO/pinMap-e03e37c7-2747-4fb7-b35d-8f0cc742734d.png" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/UNIT%20SONIC%20IO/img-fd699d62-1a87-41ce-b251-bae03bccbec0.png" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Unit Ultrasonic-IO](https://docs.m5stack.com/en/unit/Unit_Ultrasonic-IO) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U098-B2`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                                | Model-specific reference                                                                                                                                                     |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files                          | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U098-B2_Unit_Ultrasonic-IO/Structures)                                             |
| Mechanical / CAD files                          | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U098-B2_Unit_Ultrasonic-IO/Structures/Unit_Ultrasonic-IO.stl)                      |
| Example source: Unit\_SonicIO\_M5Atom.ino       | [Read example source: unit\_sonicio\_m5atom.ino](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5Atom/Unit_SonicIO_M5Atom.ino)                   |
| Example source: Unit\_SonicIO\_M5Core.ino       | [Read example source: unit\_sonicio\_m5core.ino](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5Core/Unit_SonicIO_M5Core.ino)                   |
| Example source: Unit\_SonicIO\_M5Core2.ino      | [Read example source: unit\_sonicio\_m5core2.ino](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5Core2/Unit_SonicIO_M5Core2.ino)                |
| Example source: Unit\_SonicIO\_M5StickC.ino     | [Read example source: unit\_sonicio\_m5stickc.ino](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5StickC/Unit_SonicIO_M5StickC.ino)             |
| Example source: Unit\_SonicIO\_M5StickCPlus.ino | [Read example source: unit\_sonicio\_m5stickcplus.ino](https://github.com/m5stack/M5Unit-Sonic/blob/master/examples/Unit_SonicIO_M5StickCPlus/Unit_SonicIO_M5StickCPlus.ino) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
