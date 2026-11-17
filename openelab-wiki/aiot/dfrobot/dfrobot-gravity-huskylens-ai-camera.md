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

# DFRobot Gravity Huskylens AI Camera

### DFRobot Gravity Huskylens AI Camera

***

### Product Link

{% embed url="https://openelab.io/products/huskylens-ai-camera" %}

### Overview

HuskyLens V1.0 is an advanced AI vision sensor that simplifies AI development with its easy-to-use features. It comes with 7 built-in AI functionalities, including face recognition, object tracking, object recognition, line tracking, color detection, tag recognition, and object classification. These features allow users to quickly implement AI into their projects without needing to write complex algorithms or perform extensive data training.

Designed for both beginners and professionals, HuskyLens integrates seamlessly with popular development platforms such as Arduino, LattePanda, and micro:bit, thanks to its onboard UART and I2C interfaces. The sensor outputs recognition data directly to the controller, enabling rapid prototyping and reduced development time.

<figure><img src="../../.gitbook/assets/image (575).png" alt=""><figcaption></figcaption></figure>

### Key Features

* **Easy AI Training**: AI training can be performed with just a single button press, making it simple to switch between various recognition functions.
* **Built-in 7 AI Functions**:
  * Face recognition
  * Object tracking
  * Object recognition
  * Line tracking
  * Color recognition
  * Tag recognition
  * Object classification
* **Hardware Integration**: Supports UART and I2C interfaces for easy communication with other microcontrollers, such as Arduino, LattePanda, and micro.
* **Real-time Data Output**: Directly outputs recognition results to the connected controller, bypassing the need for complex coding.

### Specifications

* **Processor**: Kendryte K210
* **Image Sensor**:
  * _SEN0305_: OV2640 (2MP)
  * _SEN0336 PRO_: OV5640 (5MP)
* **Display**: 2.0-inch IPS, 320x240 resolution
* **Supply Voltage**: 3.3V - 5.0V
* **Power Consumption**:
  * 320mA @ 3.3V
  * 230mA @ 5.0V _(Values based on face recognition mode, 80% screen brightness, fill light off)_
* **Interfaces**: UART, I2C
* **Size**: 52mm x 44.5mm
* **Operating Temperature**: -20°C to 70°C

### Pin Definitions

* **USB Port**: Used for powering the HuskyLens or for firmware upgrades when connected to a PC.
* **4-Pin UART Interface**:
  * VCC (3.3V - 5.0V): Power supply
  * GND: Ground
  * TX: Data transmission pin
  * RX: Data reception pin
* **4-Pin I2C Interface**:
  * VCC (3.3V - 5.0V): Power supply
  * GND: Ground
  * SCL: Serial clock line
  * SDA: Serial data line

### Application Scenarios

The HuskyLens AI vision sensor is versatile, making it suitable for a variety of applications:

* **Robotics**: Enhance robots with visual recognition capabilities, enabling them to recognize faces, track objects, or follow lines.
* **Smart Home Devices**: Implement face recognition for personalized user experiences in home automation systems.
* **STEM Education**: Great for introducing students to AI and machine learning in a hands-on way, allowing them to quickly build functional AI-powered projects.
* **Industrial Use**: Use object recognition or classification in automated quality control systems.

### Quick Start Guide

1. **Connecting HuskyLens**: Connect HuskyLens to your controller using either the UART or I2C interface. Ensure the correct wiring for VCC, GND, TX/RX (for UART), or SCL/SDA (for I2C).
2. **Powering On**: Supply HuskyLens with a 3.3V or 5V power source through the VCC and GND pins or the USB interface.
3. **Selecting an AI Function**: Use the onboard button to toggle between the 7 AI functions. The display will show the selected function.
4. **Training the AI**: To train HuskyLens, point the camera at an object or face and press the button to store the data. The sensor will learn and recognize the object in future frames.
5. **Receiving Data**: Once trained, HuskyLens will output recognition data through the UART or I2C interface, which can be processed by the connected controller.

### Firmware Upgrades

To ensure optimal performance, DFRobot regularly releases firmware updates for HuskyLens. Firmware can be upgraded via the USB interface by connecting HuskyLens to a PC and following the update instructions provided on the DFRobot website.

### Troubleshooting

* **No Display Output**: Check if the power supply is connected properly and if the screen brightness is adequate.
* **Unstable Recognition**: Ensure the object is well-lit and within a reasonable distance from the sensor for better recognition accuracy.
* **Connection Issues**: Verify that the correct pins (TX/RX for UART or SCL/SDA for I2C) are connected securely to the controller.

### Conclusion

The HuskyLens V1.0 is an excellent tool for integrating AI into projects effortlessly. Its combination of built-in AI functions, simple training, and versatile hardware interfaces makes it suitable for everything from beginner DIY projects to more advanced industrial applications.

### Full Usage Instructions

{% embed url="https://wiki.dfrobot.com/HUSKYLENS_V1.0_SKU_SEN0305_SEN0336" %}
