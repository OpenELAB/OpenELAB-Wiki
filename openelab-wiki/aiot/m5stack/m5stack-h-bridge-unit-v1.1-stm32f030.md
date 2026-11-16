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

# M5Stack H-bridge Unit v1.1 (STM32F030)

### M5Stack H-bridge Unit v1.1 (STM32F030)

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-h-bridge-unit" %}

### Introduction

Meet the **HBridge v1.1 Unit** – a state-of-the-art DC motor drive module that redefines motor control. Powered by the **"STM32F030+RZ7899"** scheme, this module enables seamless **I2C** communication with the M5 host, offering precise **PWM** control for speed adjustment, as well as easy management of forward, reverse, and braking functions.

Safety and reliability take center stage with built-in safeguards against over-current, over-voltage, and over-temperature situations. The module's total power MOSTUBE switch circuit allows dynamic motor control through programming, while the integrated total current acquisition circuit ensures safe motor operation.

<figure><img src="../../.gitbook/assets/image (533).png" alt=""><figcaption></figcaption></figure>

Adapting to diverse needs, the module incorporates a smart 6-12V and 5V switching circuit. It's a perfect fit for a range of applications, from robotics, motor drives, and industrial automation to smart homes. Elevate your projects with the HBridge v1.1 Unit – where cutting-edge technology meets simplicity and versatility.

### Features

* Overcurrent, overvoltage, overtemperature protection
* Power switching
* I2C address: Default 0x20
* current detech
* Programming platform: Arduino, UIFlow

### Specifications

| Resources                          | Parameters                                                      |
| ---------------------------------- | --------------------------------------------------------------- |
| MCU                                | STM32F030F4P6                                                   |
| DC bidirectional motor driver chip | RZ7899                                                          |
| Current acquisition chip           | INA199A1DCKR                                                    |
| External access DC voltage         | MAX 12V                                                         |
| I2C mailing address                | Default 0x20 (can be modified by toggle of the encoding switch) |
| Maximum allowable current          | 3A                                                              |
| Use temperature                    | 0-40°C                                                          |
| Product Size                       | 48mm\* 24mm\*8mm                                                |
| Package Size                       | 136mm\* 92mm\*13mm                                              |
| Product Weight                     | 9.1g                                                            |
| Package Weight                     | 14g                                                             |

### Pinout

* **VCC**: 3.3V to 5V power supply
* **GND**: Ground
* **SDA**: I2C data line
* **SCL**: I2C clock line
* **Motor A+**: Positive terminal for Motor A
* **Motor A-**: Negative terminal for Motor A
* **Motor B+**: Positive terminal for Motor B
* **Motor B-**: Negative terminal for Motor B

### Dimensions

<figure><img src="../../.gitbook/assets/image (534).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Connect to a Microcontroller**: Use the I2C interface to connect the H-bridge Unit to your microcontroller (e.g., Arduino, ESP32).
* **Install Necessary Libraries**: Ensure you have the correct libraries installed in your development environment to communicate with the H-bridge Unit.
* **Initialize the Unit**: Write initialization code to set up the H-bridge Unit and configure motor control parameters.
* **Control Motors**: Use provided functions to control the speed and direction of connected motors.
* **Monitor and Protect**: Utilize built-in protection features to ensure safe operation of the motors.

### FAQ

<details>

<summary><strong>Can I use the M5Stack H-bridge Unit with any microcontroller?</strong></summary>

Yes, as long as the microcontroller supports I2C communication, you can integrate the H-bridge Unit.

</details>

<details>

<summary><strong>How do I power the unit?</strong></summary>

The unit operates between 3.3V and 5V, so ensure your power supply matches this requirement.

</details>

<details>

<summary><strong>What types of motors can I control with this unit?</strong></summary>

The H-bridge Unit is designed for controlling DC motors.

</details>

<details>

<summary><strong>What libraries are needed to operate the unit with Arduino?</strong></summary>

You will need appropriate motor control libraries compatible with the STM32F030 microcontroller.

</details>

<details>

<summary><strong>How do the protection features work?</strong></summary>

The unit includes overcurrent and thermal protection to prevent damage to the unit and connected motors. These features automatically engage if the current exceeds the safe limit or if the unit overheats.

</details>

<details>

<summary><strong>Can the unit handle high-current motors?</strong></summary>

The unit can handle up to 1.2A continuous current per channel. For higher current requirements, additional external drivers may be needed.

</details>
