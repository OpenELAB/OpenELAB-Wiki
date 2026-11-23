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

# M5Stack Flashlight Unit

{% hint style="info" %}
[**View M5Stack Flashlight Unit White LED Lighting Module on OpenELAB**](https://openelab.io/products/m5stack-flashlight-unit)

**Store SKU / option:** `M5-U152`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Flashlight Unit

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-flashlight-unit" %}

### Introduction

FlashLight UNIT is an I/O Unit with built-in flash, including AW3641 driver and a white LED, with a color temperature of 5000-5700K. There is a mode selection switch on the board, which can set the flash mode and the constant lighting mode. The communication interface is GPIO. This Unit can be used as a flash or lighting applications.

<figure><img src="../../.gitbook/assets/image (861).png" alt=""><figcaption></figcaption></figure>

### Features

* PWM Brightness Adjustment Method
* Over-Temperature Protection
* Over-Voltage and Short-Circuit Protection

### Specifications

| Resources                              | Parameters          |
| -------------------------------------- | ------------------- |
| Driver chip                            | AW3641EDNR          |
| Adjustment Mode                        | PWM                 |
| AW3641EDNR Operation Temperature Range | -40℃ to +85℃        |
| Unit Operation Temperature             | 0℃ to +40℃          |
| Color Temperature                      | 6000K\~6500K（Kevin） |
| Product Size                           | 32mm × 24mm × 8mm   |
| Package Size                           | 67mm × 53mm × 12mm  |
| Product Weight                         | 4.7g                |
| Package Weight                         | 9.8g                |

### Pinout

<figure><img src="../../.gitbook/assets/image (863).png" alt=""><figcaption></figcaption></figure>

### Dimensions

<figure><img src="../../.gitbook/assets/image (862).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Connect to M5Stack**: Plug the Flashlight Unit into an M5Stack development board using the appropriate port.
* **Power Up**: Supply power to the M5Stack board (3.3V - 5V).
* **Control**: Use GPIO pins to control the flashlight. Send a high signal to the CTRL pin to turn on the flashlight and adjust the brightness as needed.

### FAQ

<details>

<summary><strong>What is the maximum brightness of the flashlight?</strong></summary>

The maximum brightness depends on the input voltage and the control signal. It can reach up to 1W of power consumption.

</details>

<details>

<summary><strong>Can I use this flashlight with other microcontroller boards?</strong></summary>

Yes, you can use it with other microcontroller boards as long as they support 3.3V - 5V power supply and GPIO control.

</details>

<details>

<summary><strong>Is the flashlight waterproof?</strong></summary>

No, the Flashlight Unit is not waterproof. It should be used in dry environments.

</details>

<details>

<summary><strong>How do I adjust the brightness?</strong></summary>

Adjust the brightness by varying the PWM signal sent to the CTRL pin from the microcontroller.

</details>

<details>

<summary><strong>What is the lifespan of the LED?</strong></summary>

The LED has an estimated lifespan of around 50,000 hours under normal operating conditions.

</details>

## Official documentation and development resources

Use [Unit FlashLight](https://docs.m5stack.com/en/unit/Unit_FlashLight) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U152`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                   | Model-specific reference                                                                                                                       |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Mechanical / CAD files             | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U152_Unit_FlashLight/Structures)                     |
| Mechanical / CAD files             | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U152_Unit_FlashLight/Structures/Unit_FlashLight.stl) |
| Official source: M5Unit-FlashLight | [Read official source: m5unit-flashlight](https://github.com/m5stack/M5Unit-FlashLight)                                                        |
| Arduino development tutorial       | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_flashlight)                                         |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
