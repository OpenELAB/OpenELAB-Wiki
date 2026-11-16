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

# Servo Motor (SG90)

### Servo Motor (SG90)

***

### Product Link

{% embed url="https://openelab.io/products/servo-motor-sg90?variant=43474520375494" %}

### Introduction

The Servo Motor (SG90) is a small analog servo motor widely used in devices requiring precise angular control, such as robots, drones, model cars, aircraft models, and more. Its small size, light weight, simple structure, and ease of control make it a popular choice for DIY electronic projects and educational experiments.

### Features

1. **Precise Control**: The SG90 servo motor achieves precise angular control through PWM signals, meeting various precision control requirements.
2. **Fast Response Time**: The servo motor responds quickly, reaching the specified position within a short time.
3. **Moderate Torque**: Despite its small size, the SG90 servo motor still provides sufficient torque for general application needs.
4. **Easy Integration**: With simple wiring and wide compatibility, the SG90 servo motor is easy to integrate into various systems.
5. **Cost-Effective**: Compared to other high-precision servo motors, the SG90 servo motor offers a more affordable price, suitable for large-scale applications.

### Specifications

| Specification        | Value                                                               |
| -------------------- | ------------------------------------------------------------------- |
| Operating Voltage    | 4.8V - 6V (typically 5V)                                            |
| Operating Angle      | 0° - 180° (some models support 360°)                                |
| Torque               | 1.6kg/cm - 1.8kg/cm (data may vary slightly from different sources) |
| Response Time        | 0.12 - 0.13 seconds/60°                                             |
| Temperature Range    | -30°C - +60°C                                                       |
| PWM Signal Period    | 20ms                                                                |
| PWM Signal High Time | 0.5ms - 2.5ms                                                       |
| Dimensions (LxWxH)   | 21.5mm x 11.8mm x 22.7mm                                            |
| Weight               | 9 grams                                                             |

### Pinout

The SG90 servo motor typically has three pins:

1. **Red (VCC)**: Power positive, usually connected to a 5V power source.
2. **Brown (GND)**: Power negative, grounded.
3. **Orange (Signal)**: Receives PWM control signals from the microcontroller.

### Dimensions

The specific dimensions of the SG90 servo motor may vary slightly by manufacturer, but generally, the dimensions are approximately:

* Length: 21.5mm
* Width: 11.8mm
* Height: 22.7mm

### How to Use

**1. Connect the Circuit**

Connect the three pins of the SG90 servo motor to the corresponding pins of the microcontroller (such as Arduino, STM32, etc.). Typically, the red wire is connected to the power positive, the brown wire is grounded, and the orange wire is connected to the PWM output pin of the microcontroller.

**2. Write the Control Program**

Use the programming language of the microcontroller (e.g., C/C++ for Arduino, C for STM32) to write the control program. The program needs to generate a PWM signal with a period of 20ms and control the rotation angle of the servo motor by changing the duty cycle (i.e., the duration of the high level) of the PWM signal.

**3. Debug and Test**

Upload the written program to the microcontroller and observe the rotation of the SG90 servo motor. By adjusting the duty cycle of the PWM signal, test the performance of the servo motor at different angles.

**4. Practical Application**

Integrate the SG90 servo motor into actual projects, such as robot joint control, drone flight control, model car steering control, etc. Adjust the control parameters of the servo motor according to specific requirements to achieve the desired functions.

#### Precautions

* When using the SG90 servo motor, ensure that the power supply voltage is within the recommended range to avoid damaging the servo motor.
* The rotation angle and speed of the servo motor are affected by the duty cycle of the PWM signal. Adjust them according to actual needs.
* When connecting the circuit, carefully check whether the pin connections are correct to avoid short circuits or reversed power connections.
* In practical applications, consider the load capacity and working environment of the servo motor to ensure its stable and reliable operation.
