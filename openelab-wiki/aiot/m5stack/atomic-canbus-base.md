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

# ATOMIC CANBus Base

{% hint style="info" %}
[**View M5Stack Atomic CAN Base Isolated CAN Bus Communication Module on OpenELAB**](https://openelab.io/products/atomic-canbus-base)

**Store SKU / option:** `M5-A103`. Match the purchased model and revision to the official reference below.
{% endhint %}

### ATOMIC CANBus Base

***

### Product Link <a href="#description" id="description"></a>

{% embed url="https://openelab.io/products/atomic-canbus-base" %}

### Description <a href="#description" id="description"></a>

ATOMIC CAN Base is a CAN bus communication unit designed to be compatible with the ATOM series controllers. It adopts the CA-IS3050G transceiver solution and features a built-in DC-DC isolated power chip that effectively isolates interference and prevents damage to sensitive circuits. It is intended for use with Atom Matrix, Atom Lite, AtomS3, and AtomS3 Lite, making it suitable for applications such as vehicle transportation and security systems.

The communication bus of ATOMIC CAN Base supports up to 110 nodes, allowing for excellent scalability in large-scale systems. It offers a signal transmission rate of up to 1Mbps, providing high-speed and reliable data transfer capabilities.

ATOMIC CAN Base also incorporates various electrical circuit protection features. It meets a common-mode voltage range of -12V to +12V and includes characteristics such as over-voltage protection, failure protection, and over-temperature protection. These features effectively defend against electromagnetic interference, overvoltage, current peaks, and other unfavorable factors, ensuring the stability and reliability of communication signals.

### Features <a href="#features" id="features"></a>

* Fits ATOM Matrix/ATOM Lite/ATOMS3/ATOMS3 Lite
* CAN bus multipoint communication
* Built-in isolation DC-DC
* Signal rates up to 1Mbps
* Signal rates up to 1Mbps
* Protection function

### Applications <a href="#applications" id="applications"></a>

* CAN bus communication
* Vehicle equipment control
* Industrial site control

### Specification <a href="#specification" id="specification"></a>

| Resources                 | Parameters     |
| ------------------------- | -------------- |
| External port             | VH-3.96-4P     |
| CAN transceiver type      | CA-IS3050G     |
| Highest rate              | 1Mbps          |
| Number of supported nodes | 110            |
| Low loop delay            | 150ns          |
| common mode voltage       | -12V \~ 12V    |
| Operating temperature     | 0-40°C         |
| Shell material            | Plastic ( PC ) |
| Product Size              | 24\*48\*18mm   |
| Package Size              | 136\* 92\*20mm |
| Product Weight            | 11.1g          |
| Package Weight            | 15.6g          |

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/Atomic%20CAN%20Base/img-fa481a72-f110-4866-9266-b67369f6ff2a.webp" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/Atomic%20CAN%20Base/pinMap-34359801-b635-49e7-8b00-61bf09e7b4d1.png" alt=""><figcaption></figcaption></figure>

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/atom/Atomic%20CAN%20Base/img-702afe76-5d06-4b5f-bffb-da2fd534c659.jpg" alt=""><figcaption></figcaption></figure>

## Official documentation and development resources

Use [Atomic CAN Base](https://docs.m5stack.com/en/atom/Atomic_CAN_Base) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`A103`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need             | Model-specific reference                                                                                 |
| ---------------------------- | -------------------------------------------------------------------------------------------------------- |
| Arduino development tutorial | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/atomic/atomic_can_base) |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
