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

# M5Stack Single-phase DC SSR

### M5Stack Single-phase DC SSR Unit

***

### Description <a href="#description" id="description"></a>

**Unit DCSSR** is a `DC to DC` single phase solid state relay controller kit, comes with a single phase solid state relay + ESP32C3 controller board. Supports `key control`, `I2C slave`, and `Modbus networking` modes of operation. Integrated programmable full-color RGB LED for for state indication, clear to operate.This kit is contactless and adopts semiconductor switching elements. It has several advantages such as high switching speed, extremely long life, low switching noise, no switching spark and ultra-reliable than most mechanical relays. Widely used in digital program control devices, motor control devices, temperature control, data processing systems and computer peripheral interface devices. `It is specially designed for harsh environments with corrosion, humidity or explosion-proof requirements and frequent turn-on/off requirements`.

### Features <a href="#features" id="features"></a>

* Single-phase solid state relay
* Three operating modes. - Push button control - I2C slave (support device I2C address configuration) - Modbus networking (supports device ID configuration)
* Programmable full color RGB LED
* RS485PWR interface (support input 9-24V to power the device)

### Applications <a href="#applications" id="applications"></a>

* DC line interrupting
* Motor equipment control
* Temperature control devices

### Specifications <a href="#specifications" id="specifications"></a>

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

### Usage/Communication protocol <a href="#usage-communication-protocol" id="usage-communication-protocol"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/DCSSR%20Unit/img-0d11d11d-b289-4409-89cd-931402d0c28c.png" alt=""><figcaption></figcaption></figure>

* Connection sample diagram

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/DCSSR%20Unit/connect_example.png" alt=""><figcaption></figcaption></figure>

### Model Size <a href="#model-size" id="model-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/unit/DCSSR%20Unit/img-b2a53bb8-4cbb-49bd-9daa-b5ed0f490271.png" alt=""><figcaption></figcaption></figure>

### Compatible

<figure><img src="../../.gitbook/assets/image (390).png" alt=""><figcaption></figcaption></figure>
