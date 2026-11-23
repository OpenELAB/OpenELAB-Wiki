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

# M5Stack Single-phase DC SSR Unit (CDG1. 1DD-10A)

{% hint style="info" %}
[**View M5Stack Unit DCSSR M5-U140 ESP32-C3 Single-phase DC SSR Relay on OpenELAB**](https://openelab.io/products/single-phase-dc-ssr-unit)

**Store SKU / option:** `M5-U140`. Match the purchased model and revision to the official reference below.
{% endhint %}

### M5Stack Single-phase DC SSR Unit (CDG1. 1DD-10A)

***

### Product Link

{% embed url="https://openelab.io/products/single-phase-dc-ssr-unit" %}

### Introduction

ACSSR Unit is an all-inclusive DC to DC single-phase solid-state relay controller kit that offers exceptional performance and versatility. It consists of a single-phase solid-state relay and an ESP32C3 controller board, providing a comprehensive solution for various applications.\
\
With support for key control, I2C slave, and Modbus networking modes, this kit offers flexible operation options to suit different requirements. The integrated programmable full-color RGB LED serves as a visual indicator, providing clear state indication for easy monitoring and operation. By utilizing semiconductor switching elements, the Unit ACSSR ensures high-speed switching, extended lifespan, low switching noise, and eliminates issues such as switching sparks. It offers superior reliability compared to traditional mechanical relays.\
\
Unit ACSSR finds wide application in digital program control devices, motor control devices, temperature control systems, data processing systems, and computer peripheral interface devices. It is specifically designed to withstand harsh environments with corrosion, humidity, or explosion-proof requirements, making it suitable for challenging industrial settings.

<figure><img src="../../.gitbook/assets/image (510).png" alt=""><figcaption></figcaption></figure>

### Features

* Single-phase solid state relay
* Three operating modes. - Push button control - I2C slave (support device I2C address configuration) - Modbus networking (supports device ID configuration)
* Programmable full color RGB LED
* RS485PWR interface (support input 9-24V to power the device)

### Specifications

| Resources                       | Parameters                                |
| ------------------------------- | ----------------------------------------- |
| Main Controller                 | ESP32C3                                   |
| Programmable RGB LED            | SK6812                                    |
| Load Current                    | 10A                                       |
| Input Control Voltage           | 3-32VDC                                   |
| Load Voltage                    | 24\~220VDC                                |
| Input Control Current           | 5mA\~20mA                                 |
| Breakdown Leakage Current       | ≤5mA                                      |
| On-state Buck                   | ≤1.6V                                     |
| Operating current safety series | resistive load: 50% Inductive load: 50%   |
| Electrical life time            | ≥1 million times                          |
| Indicator Light                 | Red (Lighted: Closed / Off: Disconnected) |
| Product Size                    | 80 \* 45 \* 31mm                          |
| Package Size                    | 147 \* 90 \* 40mm                         |
| Product Weight                  | 112.6g                                    |
| Package Weight                  | 137.8g                                    |

### Dimensions

<figure><img src="../../.gitbook/assets/image (523).png" alt=""><figcaption></figcaption></figure>

### How to Use

* **Connect to M5Stack Core**:
  * Connect the M5Stack Single-phase DC SSR Unit to your M5Stack Core using the GROVE port. Ensure the connections are secure.
* **Wiring the Load**:
  * Connect the load (such as a DC motor, light, or other DC devices) to the SSR Unit's output terminals.
  * Connect the power supply for the load to the SSR Unit's input terminals.

## Official documentation and development resources

Use [Unit DCSSR](https://docs.m5stack.com/en/unit/Unit_DCSSR) for the manufacturer's complete model reference, diagrams and maintained examples. The official product code is **`U140`**; match the board/Unit label before choosing a firmware or host example. The references below complement this guide's local instructions.

| Development need               | Model-specific reference                                                                                                             |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| Arduino development tutorial   | [Read arduino development tutorial](https://docs.m5stack.com/en/arduino/projects/unit/unit_acssr)                                    |
| Mechanical / CAD files         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/tree/master/Products/U140_Unit_DCSSR/Structures)                |
| Mechanical / CAD files         | [Read mechanical / cad files](https://github.com/m5stack/M5_Hardware/blob/master/Products/U140_Unit_DCSSR/Structures/Unit_DCSSR.stl) |
| Official source: M5Unit-ACSSR  | [Read official source: m5unit-acssr](https://github.com/m5stack/M5Unit-ACSSR)                                                        |
| Official source: ArduinoRS485  | [Read official source: arduinors485](https://github.com/m5stack/ArduinoRS485)                                                        |
| Official source: ArduinoModbus | [Read official source: arduinomodbus](https://github.com/m5stack/ArduinoModbus)                                                      |

Keep the example's host model, interface pins and dependency versions together when reproducing a result. A schematic or SDK link does not establish that another revision uses the same wiring. Official model pages and accessible tutorial links reviewed **23 November 2026**. Other downloads above are manufacturer-listed resources; listing a file is not a test of its contents. Compilation, firmware flashing and hardware operation were **not performed** in this review.
