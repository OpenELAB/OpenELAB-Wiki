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

# M5Stack 8-Channel Servo Driver Unit (STM32F030)

{% hint style="info" %}
[**View M5Stack 8-Channel Servo Driver Unit STM32F030 Multi Servo Controller on OpenELAB**](https://openelab.io/products/m5stack-servo-driver-unit)

**Store SKU / option:** `M5-U165`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack 8-Channel Servo Driver Unit (STM32F030)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-servo-driver-unit" %}

### Introduction

**8Servos Unit** is an 8-channel servo driver unit that uses the **STM32F030F4** master control to generate multiple PWM signals for servo drive and communicate with the M5 host through I2C (addr: 0x25). Built-in total power MOSTUBE switch circuit, support programming dynamic control motor release/lock;Built-in total current acquisition circuit, the total circuit parameters can be known. Supports two sets of power inputs (9-24V / 5V). This product is suitable for servo control, robot control, intelligent toys, etc.

<figure><img src="../../.gitbook/assets/image (860).png" alt=""><figcaption></figcaption></figure>

### Features

* 8-channel servo drive
* Programmable motor power supply
* I2C Protocol Control (0x25)
* Reverse power supply protection
* Total current harvesting function

### Specifications

| Resources                   | Parameters                                                     |
| --------------------------- | -------------------------------------------------------------- |
| Current acquisition chip    | INA199A1DCKR                                                   |
| Servo drive channel         | 8-channel                                                      |
| Maximum drive load capacity | 8-channel maximum load capacity: [DC5V@1.3A](mailto:DC5V@1.3A) |
| I2C Address                 | 0x25                                                           |
| Product Size                | 55\*24\*11.5mm                                                 |
| Package Size                | 136\* 92\* 13mm                                                |
| Product Weight              | 10.1g                                                          |
| Package Weight              | 17.6g                                                          |

### Pinout

* **VCC**: 5V power supply
* **GND**: Ground
* **SDA**: I2C data line
* **SCL**: I2C clock line
* **Servo 1-8**: Connections for up to 8 servo motors

### Dimensions

<figure><img src="../../.gitbook/assets/image (535).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Connect to a Microcontroller**: Use the I2C interface to connect the Servo Driver Unit to your microcontroller (e.g., Arduino, ESP32).
* **Install Necessary Libraries**: Ensure you have the correct libraries installed in your development environment to communicate with the Servo Driver Unit.
* **Initialize the Unit**: Write initialization code to set up the Servo Driver Unit and configure the servo control parameters.
* **Connect Servos**: Attach up to 8 servo motors to the designated servo pins.
* **Control Servos**: Use provided functions to control the position and movement of the connected servos.
* **Monitor and Adjust**: Utilize feedback and adjust settings as necessary to ensure precise control of the servos.

### FAQ

<details>

<summary><strong>Can I use the M5Stack Servo Driver Unit with any microcontroller?</strong></summary>

Yes, as long as the microcontroller supports I2C communication, you can integrate the Servo Driver Unit.

</details>

<details>

<summary><strong>How do I power the unit?</strong></summary>

The unit operates at 5V, so ensure your power supply matches this requirement.

</details>

<details>

<summary><strong>What types of servos can I control with this unit?</strong></summary>

The Servo Driver Unit is designed for standard hobby servos operating at 4.8V to 6V.

</details>

<details>

<summary><strong>What libraries are needed to operate the unit with Arduino?</strong></summary>

You will need the appropriate I2C servo control libraries compatible with the STM32F030 microcontroller.

</details>

<details>

<summary><strong>Can the unit handle high-current servos?</strong></summary>

The unit can handle up to 2A per channel, depending on the power supply. Ensure your power supply can deliver sufficient current for all connected servos.

</details>

<details>

<summary><strong>How precise is the servo control?</strong></summary>

The unit provides high precision with a PWM frequency range of 50Hz to 330Hz, suitable for most standard servos.

</details>

## Official documentation and development resources

Use [Unit 8Servos](https://docs.m5stack.com/en/unit/Unit_8Servos) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U165`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need                                 | Model-specific reference                                                                                                                 |
| ------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Electrical schematic                             | [Read electrical schematic](https://m5stack-doc.oss-cn-shenzhen.aliyuncs.com/620/SCH_UNIT_8Servos_V1.01.pdf)                             |
| Mechanical / CAD files                           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U165_Unit_8Servos/Structures)                  |
| Mechanical / CAD files                           | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U165_Unit_8Servos/Structures/Unit_8Servos.stl) |
| Official source: M5Unit-8Servos2-I2C             | [Read official source: m5unit-8servos2-i2c](https://github.com/m5stack/M5Unit-8Servos2-I2C)                                              |
| Official source: M5Unit-8Servos2-I2C-Internal-FW | [Read official source: m5unit-8servos2-i2c-internal-fw](https://github.com/m5stack/M5Unit-8Servos2-I2C-Internal-FW)                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
