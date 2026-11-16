# DAMIAO DM-J4310-2EC V1.1 Motor Instruction Manual

> DAMIAO DM-J4310-2EC V1.1 Motor User Guide

[**DAMIAO DM-J4310-2EC Motor**DAMIAO DM-J4310-2EC: 7N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons. Motor for OpenArm.openelab.io](https://openelab.io/products/damiao-brushless-servo-dm-j4310)

## **Precautions** <a href="#block-339d4c79856d803f8430f008a18f87ce" id="block-339d4c79856d803f8430f008a18f87ce"></a>

1. Please strictly operate the motor within the specified working environment and the maximum allowable winding temperature range. Failure to do so may result in permanent and irreversible damage to the product.
2. Prevent foreign objects from entering the rotor; otherwise, abnormal rotor operation may occur.
3. Before use, check whether all components are intact. Do not use the product if any parts are missing, aged, or damaged.
4. Ensure correct wiring and that the motor is installed properly and securely.
5. Do not touch the electronic rotor section during operation to avoid accidents. The motor may become hot during high-torque output; be cautious to prevent burns.
6. Users must not disassemble the motor without authorization, as this may affect control accuracy or lead to abnormal operation.

## **Motor Features** <a href="#block-339d4c79856d809eae7bd8f1e24603a7" id="block-339d4c79856d809eae7bd8f1e24603a7"></a>

1. Dual encoders provide single-turn absolute position output on the output shaft, retaining position data even in the event of power loss.
2. Integrated motor and driver design with a compact and highly integrated structure.
3. Supports upper-computer visual debugging and firmware upgrades.
4. Capable of providing feedback on motor speed, position, torque, and temperature via CAN bus.
5. Equipped with dual temperature protection.
6. Supports trapezoidal acceleration and deceleration in position control mode.

## Interface & Pin Description <a href="#block-339d4c79856d80f5887fefdc7325bab3" id="block-339d4c79856d80f5887fefdc7325bab3"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4cbe61ed-86a9-495b-9ec5-6fff7326daad/image/w=1920,quality=90,fit=scale-down" alt="image" height="265.635499207607" width="576">

| Specific Name - No.                                      | Description                                                                                                                                                                                                                                                                                                                                                                                                           |
| -------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power Interface – 1 (include CAN communication terminal) | 1. Connect the power supply using the XT30 (2+2)-F connector cable. The rated voltage is 24V, supplying power to the motor. 2. Connect the CAN communication terminal to external control equipment to receive CAN control commands and send motor status feedback. 3. The motor includes two power interfaces, either of which can be used independently or daisy-chained for multi-motor setups to simplify wiring. |
| Power Interface – 2 (include CAN communication terminal) | 1. Connect the power supply using the XT30 (2+2)-F connector cable. The rated voltage is 24V, supplying power to the motor. 2. Connect the CAN communication terminal to external control equipment to receive CAN control commands and send motor status feedback. 3. The motor includes two power interfaces, either of which can be used independently or daisy-chained for multi-motor setups to simplify wiring. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4d3e9ba4-1298-46f9-8261-f95e73ecfaf6/image/w=1920,quality=90,fit=scale-down" alt="image" height="307.13286713286715" width="576">

| Specific Name - No.   | Description                                                                                                                                                                                                    |
| --------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debug Serial Port – 3 | Connect via GH1.25 3-pin cable. Use a USB to CAN debugging tool (or a general USB-to-serial module) to connect to a PC for parameter configuration and firmware upgrades via the debugging assistant software. |

## Motor Dimensions and Mounting <a href="#block-33ad4c79856d8042a6c5e914abf19bdf" id="block-33ad4c79856d8042a6c5e914abf19bdf"></a>

Please refer to the motor mounting hole dimensions and positions to install the motor onto the corresponding equipment.

![image](https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4ee774c7-2cdb-4fd3-a384-f501dc0ab45e/image/w=1920,quality=90,fit=scale-down)

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b9cfd605-fb55-4daf-a13d-bcc41b8b06d6/image/w=1920,quality=90,fit=scale-down" alt="image" height="365.34048257372655" width="816">

## **Motor wiring diagram** <a href="#block-33ed4c79856d809ab1e1f3160e04d9c9" id="block-33ed4c79856d809ab1e1f3160e04d9c9"></a>

### **Main wiring diagram** <a href="#block-33ed4c79856d80298adef966d4cddbdc" id="block-33ed4c79856d80298adef966d4cddbdc"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/44bcbc8b-4e3e-4ef7-9c38-ef83651964b2/1db0c673-8eab-48cb-94eb-36b696e27dfa/w=1920,quality=90,fit=scale-down" alt="image" height="572.0084568662578" width="753.5750122070312">

### **USB-to-CAN module wiring diagram** <a href="#block-33ed4c79856d8018beaacc8c4f241ac2" id="block-33ed4c79856d8018beaacc8c4f241ac2"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f8473d0a-8963-4b78-887e-e42bfdb7677b/image/w=1920,quality=90,fit=scale-down" alt="image" height="398.8650227360681" width="629.9921875">

### **Power adapter board wiring diagram** <a href="#block-33ed4c79856d80f7a4f0eb6e250ddfb1" id="block-33ed4c79856d80f7a4f0eb6e250ddfb1"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/55f0284b-0628-4027-9291-43c250eba6a9/image/w=1920,quality=90,fit=scale-down" alt="image" height="440.8866498740554" width="624">

## **Indicator Light Status** <a href="#block-33ad4c79856d80af8adff2c01fae6801" id="block-33ad4c79856d80af8adff2c01fae6801"></a>

| Normal Status   | Green-Solid On | Enabled mode, normal operating status                                                                                                                                                                                                                                                                                           |
| --------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                 | Red-Solid On   | Disabled mode                                                                                                                                                                                                                                                                                                                   |
| Abnormal Status | Red – Blinking | Indicates a fault. Corresponding fault types include: **8** – Overvoltage **9** – Undervoltage **A** – Overcurrent **B** – MOS Overtemperature **C** – Motor Coil Overtemperature **D** – Communication Loss **E** – Overload You can check the fault type via the feedback frame or through the debugging assistant interface. |

## Operating Modes <a href="#block-33ad4c79856d807ab607ef29468a2780" id="block-33ad4c79856d807ab607ef29468a2780"></a>

### MIT Mode <a href="#block-33bd4c79856d80bea489fb3c14cc06ce" id="block-33bd4c79856d80bea489fb3c14cc06ce"></a>

MIT mode is designed to be compatible with the original MIT mode. It allows seamless switching while enabling flexible configuration of control ranges (P\_ MAX, V\_MAX, T\_MAX). The ESC converts received CAN data into control variables to calculate the torque value, which serves as the current reference for the current loop. The current loop then regulates to achieve the specified torque current. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Derived from the MIT mode, various control modes can be implemented. For example: When kp = 0 and kd ≠ 0, setting v\_des enables constant speed rotation; When kp = 0 and kd = 0, setting t\_ff enables constant torque output.

💡

Note: When controlling position, kd must not be set to **0**,  otherwise it may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-33ad4c79856d8026bf22c49929cde0b3" id="block-33ad4c79856d8026bf22c49929cde0b3"></a>

The position cascade mode adopts a three loop series control mode, where the position loop serves as the outermost loop and its output serves as the given value for the velocity loop, while the output of the velocity loop serves as the given value for the inner loop current loop, used to control the actual current output. The control schematic diagram is shown in the following figure:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** is the target position for control, and **v\_des** is used to limit the maximum absolute velocity during motion.

When the position cascade mode is controlled using the recommended control parameters from the debugging assistant, it can achieve good control accuracy. The control process is relatively smooth, but the response time is comparatively longer. In addition to **v\_des**, the configurable related parameters also include acceleration/deceleration settings. If additional oscillations occur during the control process, increasing the acceleration/deceleration can help mitigate them.

💡

**Note:** The units of **p\_des** and **v\_des** are **rad** and **rad/s**, respectively, and their data type is float. The damping factor must be set to a **positive non-zero number**. Please refer to the precautions for the velocity mode.

### Velocity Mode <a href="#block-33ad4c79856d807bb07dc327ceaa924d" id="block-33ad4c79856d807bb07dc327ceaa924d"></a>

Velocity mode allows the motor to run steadily at the set speed. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

Note: The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

## Usage <a href="#block-33ad4c79856d8097adcfc60565b9246f" id="block-33ad4c79856d8097adcfc60565b9246f"></a>

The control uses the CAN standard frame format with a fixed baud rate of 1 Mbps. Based on functionality, the frames can be divided into receive frames and feedback frames. The receive frames are the control data received, used to achieve command control of the motor. The feedback frames are the motor's status data sent by the motor to the higher-level controller. Depending on the selected mode of the motor, the frame format definition and frame ID of the receive frames vary, but the feedback frames are the same across all modes.

### Feedback Frame <a href="#block-33ad4c79856d808b9225e33c3af3aeca" id="block-33ad4c79856d808b9225e33c3af3aeca"></a>

The feedback frame ID is set via the debugging assistant (MasterID), with a default value of 0. It primarily returns information about the motor’s position, speed, and torque. The frame format is defined as follows:

| Feedback Message | D\[0]      | D\[1]      | D\[2]     | D\[3]      | D\[4]                 | D\[5]   | D\[6]  | D\[7]    |
| ---------------- | ---------- | ---------- | --------- | ---------- | --------------------- | ------- | ------ | -------- |
| MST\_ID          | ID\|ERR<<4 | POS\[15:8] | POS\[7:0] | VEL\[11:4] | VEL\[3:0] \| T\[11:8] | T\[7:0] | T\_MOS | T\_Rotor |

Where:

1. ID indicates the controller ID, taking the lower 8 bits of the CAN\_ID.
2. ERR indicates a fault, with the corresponding fault types as follows:
3. **8** — Overvoltage
4. **9** — Undervoltage
5. **A** — Overcurrent
6. **B** — MOS overtemperature
7. **C** — Motor coil overtemperature
8. **D** — Communication loss
9. **E** — Overload
10. POS indicates the position information of the motor.
11. VEL indicates the velocity information of the motor.
12. T indicates the torque information of the motor.
13. T\_MOS indicates the average temperature of the MOS on the driver, in °C.
14. T\_Rotor indicates the average temperature of the motor's internal coil, in °C.

Position, velocity, and torque use a linear mapping relationship to convert floating-point data into signed fixed-point data. Position uses 16-bit data, while velocity and torque both use 12-bit data.

### Control Frame in MIT Mode <a href="#block-33ad4c79856d802c8f63d13fab93cb20" id="block-33ad4c79856d802c8f63d13fab93cb20"></a>

| Control Message | D\[0]          | D\[1]         | D\[2]          | D\[3]                     | D\[4]     | D\[5]      | D\[6]                    | D\[7]       |
| --------------- | -------------- | ------------- | -------------- | ------------------------- | --------- | ---------- | ------------------------ | ----------- |
| ID              | p\_des \[15:8] | p\_des \[7:0] | v\_des \[11:4] | v\_des\[3:0] \| Kp\[11:8] | Kp \[7:0] | Kd \[11:4] | Kd\[3:0] \| t\_ff\[11:8] | t\_ff\[7:0] |

Frame ID = configured CAN ID value

* **p\_des**: Position command
* **v\_des**: Velocity command
* **Kp**: Position proportional gain
* **Kd**: Position derivative gain
* **T\_ff**: Torque reference value

All parameters conform to the mapping relationship described in the previous section, where the ranges of p\_des, v\_des, and t\_ff can be configured using the debugging assistant, and the range of Kp is \[0, 500] and the range of Kd is \[0, 5].

A standard CAN data frame contains only 8 bytes. The MIT control command format combines five parameters — Position, Velocity, Kp, Kd, and Torque — into 8 bytes through bit-packing. Among them: Position occupies 2 bytes (16 bits), Velocity occupies 12 bits, Kp occupies 12 bits, and Kd occupies 12 bits.

### Control Frame in Position-Velocity Mode <a href="#block-33ad4c79856d80b88760d28a747c7999" id="block-33ad4c79856d80b88760d28a747c7999"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

Frame ID = configured CAN ID value + 0x100

* **p\_des**: Position command, float, little-endian (low byte first, high byte last)
* **v\_des**: Velocity command, float, little-endian (low byte first, high byte last)

In this mode, the CAN ID used to send commands is 0x100 + ID. The velocity command (v\_des) defines the maximum speed during the movement to the target position—i.e., the speed during the constant-velocity phase.

### Control Frame in Velocity Mode <a href="#block-33ad4c79856d800ca71de1c5ae759a11" id="block-33ad4c79856d800ca71de1c5ae759a11"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

The frame ID is the set CAN ID value plus an offset of 0x200.

* **v\_des**: Velocity reference value, floating point, little-endian (low byte first, high byte last).

The CAN ID for sending the command here is 0x200 + ID.

## Using the Debugging Assistant <a href="#block-33ad4c79856d8095b340efc00d2f7e3f" id="block-33ad4c79856d8095b340efc00d2f7e3f"></a>

Use the USB to CAN debugging tool to connect the motor to the PC, and perform parameter configuration and firmware upgrade via the debugging assistant.

The motor's debug serial port is connected to the PC using a GH1.25 3-pin cable.

Through the debugging assistant, you can configure motor parameters and perform firmware upgrades.

Once the serial port, CAN interface, and power interface of the motor are all properly connected, open the debugging assistant software on the PC, select the corresponding serial device, and open the serial port.

At this point, power on the motor. The serial port will output information, and the Control Mode will indicate the current drive mode.

## Characteristic Curve <a href="#block-33ad4c79856d80c9a90fece563e3391b" id="block-33ad4c79856d80c9a90fece563e3391b"></a>

At a constant speed of 120 rpm and room temperature of 25°C, the performance curve was measured as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a8b187fd-3029-46ae-8265-e6803e9f89f1/image/w=1920,quality=90,fit=scale-down" alt="image" height="387.1616516436904" width="737.5625">

## Key Parameters <a href="#block-33ad4c79856d80bc8664ce29bda88de9" id="block-33ad4c79856d80bc8664ce29bda88de9"></a>

Please refer to the following parameters for proper motor usage:

| **Motor Parameters**            | Rated Voltage              | 24V                                                                                                                                                                                               |
| ------------------------------- | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                                 | Rated Current              | 2.5A                                                                                                                                                                                              |
|                                 | Peak Current               | 7.5A                                                                                                                                                                                              |
|                                 | Rated Torque               | 3NM                                                                                                                                                                                               |
|                                 | Peak Torque                | 7NM                                                                                                                                                                                               |
|                                 | Rated Speed                | 120rpm                                                                                                                                                                                            |
|                                 | Maximum No-Load Speed      | 200rpm                                                                                                                                                                                            |
| **Motor Characteristic Values** | Reduction Ratio            | 10: 1                                                                                                                                                                                             |
|                                 | Pole pairs                 | 14                                                                                                                                                                                                |
|                                 | Phase Inductance           | 340uH                                                                                                                                                                                             |
|                                 | Phase Resistance           | 650mΩ                                                                                                                                                                                             |
| **Structure and Weight**        | Outer Diameter             | 57mm                                                                                                                                                                                              |
|                                 | Height                     | 46mm                                                                                                                                                                                              |
|                                 | Motor Weight               | About 300g                                                                                                                                                                                        |
| **Encoder**                     | Encoder Resolution         | 14 bit                                                                                                                                                                                            |
|                                 | Number of Encoders         | 2                                                                                                                                                                                                 |
|                                 | Encoder Type               | Magnetic Encoder (Single-Turn)                                                                                                                                                                    |
| **Communication**               | Control Interface          | CAN@1Mbps                                                                                                                                                                                         |
|                                 | Parameter Tuning Interface | UART@921600bps                                                                                                                                                                                    |
| **Control and Protection**      | Control Mode               | MIT Mode                                                                                                                                                                                          |
|                                 |                            | Velocity Mode                                                                                                                                                                                     |
|                                 |                            | Position Mode                                                                                                                                                                                     |
|                                 | Protection                 | Driver over-temperature protection: Protection temperature: 120°C. If over-temperature occurs, the motor will exit the "Enable Mode".                                                             |
|                                 |                            | Motor over-temperature protection: set according to usage requirements. It is recommended not to exceed 100°C. If over-temperature occurs, the motor will exit the "Enable Mode".                 |
|                                 |                            | Motor overvoltage protection: set according to usage requirements. It is recommended not to exceed 32 V. If overvoltage occurs, the motor will exit the "Enable Mode".                            |
|                                 |                            | Communication loss protection: If no CAN command is received within the set period, the motor will automatically exit the "Enable Mode".                                                          |
|                                 |                            | Motor overcurrent protection: set according to usage requirements. It is recommended not to exceed 9.8 A. If overcurrent occurs, the motor will exit the "Enable Mode".                           |
|                                 |                            | Motor undervoltage protection: If the power supply voltage falls below the set value, the motor will exit the "Enable Mode". It is recommended that the power supply voltage not fall below 15 V. |
