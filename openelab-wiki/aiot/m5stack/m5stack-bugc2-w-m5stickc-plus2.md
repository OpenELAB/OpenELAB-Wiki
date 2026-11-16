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

# M5Stack BugC2 w/ M5StickC PLUS2

### M5Stack BugC2 w/ M5StickC PLUS2

***

### Product Link

{% embed url="https://openelab.io/products/m5stack-bugc2-w" %}

### Description <a href="#description" id="description"></a>

**BugC2** is a programmable robot base compatible with the M5StickC series controllers. This base integrates four L9110S motor drivers and DC gear motors, utilizes the STM32F030F4 as its core control chip, and comes equipped with two flexible programmable RGB LEDs, an infrared encoder, and a dedicated battery holder. Through its top slot, BugC2 can closely connect with the M5StickC controller, precisely receiving control commands via the I2C protocol (address 0x38). Beyond providing basic mobility capabilities, BugC2 also features a Type-C charging port, battery reverse connection protection, and voltage detection for enhanced safety and convenience. Its built-in 700mAh 16340 rechargeable lithium battery ensures long-lasting battery life, making it a multifunctional and efficient programmable robot platform suitable for various educational and innovative applications.

### Features <a href="#features" id="features"></a>

* Programmable robot
* Remote control
* Four-way motor driver (L9110S)
* 2xRGB LED
* Infrared remote control decoding
* Battery voltage detection
* Onboard Typec port battery charging
* Battery anti-reverse connection

### Applications <a href="#applications" id="applications"></a>

* Remote motor control
* Robot control
* Intelligent toy

### Specifications <a href="#specifications" id="specifications"></a>

| Resources                           | Parameters                                                                                                       |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| Motor drive                         | L9110S                                                                                                           |
| Infrared receiver                   | SL0038GD                                                                                                         |
| RGB                                 | WS2812C-2020                                                                                                     |
| Battery capacity                    | 700(specification:16340)                                                                                         |
| Standby current                     | Avg:DC4.2V/20.8uA                                                                                                |
| 2orking current                     | Avg:DC4.2V/285.1mA                                                                                               |
| IR detection distance(StickC Plus2) | <p>Infrared emission distance (linear distance) at 180° : 560CM<br>Infrared emission distance at 90° : 400CM</p> |
| Operating temperature               | 0-40°C                                                                                                           |
| Product Size                        | 55\*40\*25mm                                                                                                     |
| Package Size                        | 71.7\*70\*58mm                                                                                                   |
| Product Weight                      | 74,5g                                                                                                            |
| Package Weight                      | 87.9g                                                                                                            |

### Schematics <a href="#schematics" id="schematics"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/app/BUGC2/img-b1fe147a-c4f4-44ad-9ac4-d66ad79eac2e.png" alt=""><figcaption></figcaption></figure>

### PinMap <a href="#pinmap" id="pinmap"></a>

| STM32F030F4P6       | PA1 | PA2 | PA3 | PA4 | PA1 | PB1 | PA5 | PA6 | PA7 | PA0          |
| ------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | ------------ |
| Motor1(left front)  |     |     | 1B  | 1A  |     |     |     |     |     |              |
| Motor2(Left Rear)   | 1B  |     |     |     |     |     |     |     | 1A  |              |
| Motor3(Right Rear)  |     |     |     |     |     |     | 1A  | 1B  |     |              |
| Motor4(Right front) |     | 1A  |     |     |     | 1B  |     |     |     |              |
| BAT\_Detect(WS2812) |     |     |     |     |     |     |     |     |     | BAT\_ADC/RGB |

| STICKC PLUS2(ESP32-PICO-V3-02) | G36   |
| ------------------------------ | ----- |
| IR(SL0038GD)                   | IR\_R |

### Protocol <a href="#protocol" id="protocol"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/app/BUGC2/protocol-b0d34b3d-3154-465e-810e-5cfd6ba909ee.png" alt=""><figcaption></figcaption></figure>
