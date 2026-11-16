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

# M5StickC DAC 2 Hat

### M5Stack M5StickC DAC 2 Hat

***

### Product Link <a href="#description" id="description"></a>

{% embed url="https://openelab.io/products/m5stack-m5stickc-dac-2-hat?_pos=1&_sid=d9d28206f&_ss=r" %}

### Description <a href="#description" id="description"></a>

**DAC2 Hat** is an I2C digital-to-analog signal conversion unit designed to be compatible with the StickC series controllers. It offers high precision and accuracy in its performance by using the GP8413 solution. This chip can linearly convert a 15-bit digital value into two independent analogue voltages of 0-5V or 0-10V. The output voltage error is only 0.2%, with a linearity of up to 0.01%.

For scalability, the circuit design supports a 3-bit hardware address, allowing up to 8 devices to be connected and operated simultaneously. The DAC2 Hat also incorporates safety features such as output short-circuit protection. In the event of a short circuit between the output pins and ground, it automatically enters a protective mode and shuts down the output to prevent damage.

DAC2 Hat is suitable for a variety of applications including general signal conversion, motor speed control, LED dimming, inverters, power supplies and industrial analogue signal isolation. It provides a reliable solution for converting digital signals to analogue, offering high accuracy, expandability and safety.and safety performance.

### Features <a href="#features" id="features"></a>

* Adapted StickC/StickC PLUS/StickC PLUS2
* I2C communication (default address 0x59)
* Supports multiple parallel connections
* Short-circuit protection
* High precision, small error

### Includes <a href="#includes" id="includes"></a>

* 1x DAC2 Hat
* 1x VH3.96-4P
* 1x Sticker

### Applications <a href="#applications" id="applications"></a>

* Universal signal conversion
* Motor speed regulation, LED dimming
* Inverter, power supply
* Industrial analog signal isolation

### Specification <a href="#specification" id="specification"></a>

| Resources                      | Parameters        |
| ------------------------------ | ----------------- |
| DAC Chip                       | GP8413            |
| Resolution Ratio               | 15Bit             |
| I2C Serial Communication       | 0x59 (default)    |
| Maximum Output Voltage         | 10V               |
| Output Voltage Error           | <0.2%             |
| Output Voltage Linearity error | 0.01%             |
| Operating Temperature          | 0-40°C            |
| Product Size                   | 35\* 24\* 13.7mm  |
| Package Size                   | 136\* 92\* 13.7mm |
| Product Weight                 | 6.7g              |
| Package Weight                 | 15g               |

![](https://static-cdn.m5stack.com/resource/docs/products/hat/Hat-DAC2/img-289dfe58-0972-4f00-9bb7-908eff81fbf6.webp)![](https://static-cdn.m5stack.com/resource/docs/products/hat/Hat-DAC2/img-2513a25e-2e38-41cb-a630-8715f3a8a56f.webp)![](https://static-cdn.m5stack.com/resource/docs/products/hat/Hat-DAC2/img-c66a4a27-da26-406f-82d7-461da413d14a.webp)

### Related Link <a href="#related-link" id="related-link"></a>

* [GP8413 Datasheet](https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/unit/Unit-DAC2/GP8413.pdf)

### Schematic <a href="#schematic" id="schematic"></a>

<figure><img src="../../.gitbook/assets/image (416).png" alt=""><figcaption></figcaption></figure>

### Address Select <a href="#address-select" id="address-select"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/products/hat/Hat-DAC2/98d93ea4c395cf6f97bce53fb1448d8.png" alt=""><figcaption></figcaption></figure>

|  A2 |  A1 |  A0 | I2C Address（7 Bit） |
| :-: | :-: | :-: | :----------------: |
|  0  |  0  |  0  |        0x58        |
|  0  |  0  |  1  |    0x59(Default)   |
|  0  |  1  |  0  |        0x5A        |
|  0  |  1  |  1  |        0x5B        |
|  1  |  0  |  0  |        0x5C        |
|  1  |  0  |  1  |        0x5D        |
|  1  |  1  |  0  |        0x5E        |
|  1  |  1  |  1  |        0x5F        |

Address SelectBy setting the A0, A1, A2 pins to high (1) or low (0), you get eight different I2C addresses from 0x58 to 0x5F. \*If the resistance is connected, it is regarded as high(1), and if the resistance is not connected, it is low(0) .

### PinMap <a href="#pinmap" id="pinmap"></a>

| StickC   | SDA | SCL | VCC | GND |
| -------- | --- | --- | --- | --- |
| DAC2 Hat | G0  | G26 | 5V  | GND |

### Module Size <a href="#module-size" id="module-size"></a>

<figure><img src="https://static-cdn.m5stack.com/resource/docs/products/hat/Hat-DAC2/img-6af530a5-400b-41b9-8ade-f3d275fdc03a.jpg" alt=""><figcaption></figcaption></figure>

### Examples <a href="#examples" id="examples"></a>

#### Arduino <a href="#arduino" id="arduino"></a>

* [DAC2 Hat For StickC](https://github.com/m5stack/M5StickC/tree/master/examples/Hat/DAC2_GP8413)
* [DAC2 Hat For StickC PLUS](https://github.com/m5stack/M5StickC-Plus/tree/master/examples/Hat/DAC2_GP8413)
* [DAC2 Hat For StickCPlus2](https://github.com/m5stack/M5StickCPlus2/tree/master/examples/Hat/DAC2_GP8413)

### UIFlow <a href="#uiflow" id="uiflow"></a>

<figure><img src="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/static/assets/img/uiflow/uiflow1.0_banner_01.png" alt=""><figcaption></figcaption></figure>

[UIFlow1.0 Blockly dac2 Instructions for use](https://docs.m5stack.com/en/uiflow/blockly/hat/dac2)[UIFlow1.0 Blockly dac2 Instructions for use](https://docs.m5stack.com/en/uiflow/blockly/hat/dac2)How to use Blockly dac2 on the UIFlow 1.0 graphical programming platform and related API instructions

### FAQ <a href="#faq" id="faq"></a>

#### Difference between Hat-DAC2 and Hat-DAC？ <a href="#question-difference-between-hat-dac2-and-hat-dac" id="question-difference-between-hat-dac2-and-hat-dac"></a>

| Product  | Communication | Chip    | EEPROM  | Resolution | Output Voltage | I2C Address                                         | Channel        |
| -------- | ------------- | ------- | ------- | ---------- | -------------- | --------------------------------------------------- | -------------- |
| DAC2 Hat | I2C           | GP8413  | /       | 15Bit      | 0-10V          | Adjustable A0/A1/A2(8 I2C addresses) (default 0x59) | Two-Channel    |
| DAC Hat  | I2C           | MCP4725 | Support | 12Bit      | VDD（0-3.3V）    | The default is 0x60, unchangeable                   | Singal-Channel |

<details>

<summary><strong>Unit RFID(U031),Unit RFID2(U031-B) program is compatible?</strong></summary>

Unit RFID(U031),Unit RFID2(U031-B) program is totally compatible

</details>

<details>

<summary><strong>What are the voltage levels of the RS485 network?</strong></summary>

Generally, the voltage difference between A and B is around -7 to 13V. The high and low logic levels on the AB lines in the RS-485 standard are as follows: 1. High: A - B ≥ 200mV; 2. Low: A - B ≤ -200mV. Pulling A up to 3.3V and pulling B down to GND provides an initial state for the bus, which is a High level.

</details>

<details>

<summary><strong>RoverC, JoyC battery charge</strong></summary>

RoverC, JoyC, 's battery is in parallel connection with the M5StickC controller, you can connect the USB cable to the M5StickC to charge the battery of RoverC, JoyC. Also, When charging the M5StickC and RoverC, JoyC power switch can be turned off.

</details>
