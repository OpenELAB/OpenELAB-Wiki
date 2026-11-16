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

# M5Stack BaseX EV3 motor

### M5Stack BaseX EV3 motor compatible base RJ11 interface

***

### Product Link

{% embed url="https://openelab.io/products/basex-ev3-motor" %}

### Description <a href="#description" id="description"></a>

**BaseX** is a special base compatible with LEGO EV3 motor. The structure design is similar to base26, supporting multiple ways of fixation, and an additional LEGO connection base is provided. When building the LEGO structure, Basex can be easily embedded in the work. Basex can be connected to 4-way (RJ11) LEGO motor at the same time, supporting angle / speed reading and control, and perfectly compatible with the original motor functions. In addition, the base provides two servo interfaces, which can directly control the rotation angle of the servo.There is a motherboard PDM microphone for sound collection. In order to adapt to different use scenarios, a UART interface (16 / 17) and a GPIO interface (26 / 36) are provided to make access to various sensors more flexible. A 950mAh battery is built in the base, which can be charged through the usb-c interface of m5core to extend the endurance. In order to improve the driving ability of the interface, the base is equipped with a DC power socket, which can be powered by an external 9-12v power supply to provide a stable power supply for the motor.

### Features <a href="#features" id="features"></a>

* 4-way RJ12 LEGO motor interface (total maximum output current 2A)
* 2-way servo interface (total maximum output current 2A)
* 1-way UART
* 1-way GPIO
* On board PDM microphone (GOIO 34)
* On board DC-DC conversion (9 \~ 12V,independent power supply for the motor only)
* Built in 950mAh battery
* Multiple fixing methods / LEGO hole connection support

### Applications <a href="#applications" id="applications"></a>

* Encoder motor / servo controller
* LEGO DIY intelligent control

### Specifications <a href="#specifications" id="specifications"></a>

| Resources    | Parameter     |
| ------------ | ------------- |
| Net weight   | 59g           |
| Gross weight | 110g          |
| Product Size | 54\*54\*26mm  |
| Package Size | 150\*65\*40mm |

### I2C Control instructions <a href="#i2c-control-instructions" id="i2c-control-instructions"></a>

I2C Slave address: 0x22

| Function                | Register address | Value                 |
| ----------------------- | ---------------- | --------------------- |
| SERVO1\_ANGLE\_ADDR     | 0X00             | 0\~180                |
| SERVO2\_ANGLE\_ADDR     | 0x01             | 0\~180                |
| SERVO1\_PULSE\_ADDR     | 0x10             | (uint16\_t) 500\~2500 |
| SERVO2\_PULSE\_ADDR     | 0x12             | (uint16\_t)500\~2500  |
| MOTOR1\_PWM\_DUTY\_ADDR | 0x20             | -127\~127             |
| MOTOR2\_PWM\_DUTY\_ADDR | 0x21             | -127\~127             |
| MOTOR3\_PWM\_DUTY\_ADDR | 0x22             | -127\~127             |
| MOTOR4\_PWM\_DUTY\_ADDR | 0x23             | -127\~127             |
| MOTOR1\_ENCODER\_ADDR   | 0x30             | int32\_t              |
| MOTOR2\_ENCODER\_ADDR   | 0x34             | int32\_t              |
| MOTOR3\_ENCODER\_ADDR   | 0x38             | int32\_t              |
| MOTOR4\_ENCODER\_ADDR   | 0x3C             | int32\_t              |
| MOTOR1\_SPEED\_ADDR     | 0x40             | -127\~127             |
| MOTOR2\_SPEED\_ADDR     | 0x41             | -127\~127             |
| MOTOR3\_SPEED\_ADDR     | 0x42             | -127\~127             |
| MOTOR4\_SPEED\_ADDR     | 0x43             | -127\~127             |

I2C Motor address:

| Motor number | Motor Address |
| ------------ | ------------- |
| MOTOR1       | 0x50          |
| MOTOR2       | 0x60          |
| MOTOR3       | 0x70          |
| MOTOR4       | 0x80          |

Mode config method: Motor address + nByte

| Byte | Value              |
| ---- | ------------------ |
| 0    | Run mode           |
| 1    | position-p(3)      |
| 2    | position-i(1)      |
| 3    | position-d(15)     |
| 4    | 5                  |
| 8    | position-max-speed |
| 9    | speed-p            |
| 10   | speed-i            |
| 11   | speed-d            |
| 12   | speed-point        |
