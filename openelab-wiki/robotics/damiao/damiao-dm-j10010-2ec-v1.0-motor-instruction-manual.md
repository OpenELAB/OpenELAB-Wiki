# DAMIAO DM-J10010-2EC V1.0 Motor Instruction Manual

> DAMIAO DM-J10010-2EC V1.0 Motor User Guide

[**DAMIAO DM-J10010-2EC Motor**DAMIAO DM-J10010-2EC: 150N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.mdmbot.com](https://www.mdmbot.com/index.php?c=show\&id=107)

## **Precautions** <a href="#block-34ad4c79856d8185bd04f44d1d43000b" id="block-34ad4c79856d8185bd04f44d1d43000b"></a>

1. Please strictly operate the motor within the specified working environment and the maximum allowable winding temperature range. Failure to do so may result in permanent and irreversible damage to the product.
2. Prevent foreign objects from entering the rotor; otherwise, abnormal rotor operation may occur.
3. Before use, check whether all components are intact. Do not use the product if any parts are missing, aged, or damaged.
4. Ensure correct wiring and that the motor is installed properly and securely.
5. Do not touch the electronic rotor section during operation to avoid accidents. The motor may become hot during high-torque output; be cautious to prevent burns.
6. Users must not disassemble the motor without authorization, as this may affect control accuracy or lead to abnormal operation.

## **Motor Features** <a href="#block-34ad4c79856d81a5a881f8dbf165dd1f" id="block-34ad4c79856d81a5a881f8dbf165dd1f"></a>

1. Dual encoders provide single-turn absolute position output on the output shaft, retaining position data even in the event of power loss.
2. Integrated motor and driver design with a compact and highly integrated structure.
3. Supports upper-computer visual debugging and firmware upgrades.
4. Capable of providing feedback on motor speed, position, torque, and temperature via CAN bus.
5. Equipped with dual temperature protection.
6. Supports trapezoidal acceleration and deceleration in position control mode.

## **Packing List** <a href="#block-34ad4c79856d80a8bfefd9672661cddc" id="block-34ad4c79856d80a8bfefd9672661cddc"></a>

1. Motor (with integrated driver) ×1
2. Power cable: XT60 male-to-female cable (200 mm) × 1
3. CAN interface: GH1.25 2-Pin Cable (skew，300mm) × 1
4. Debug serial cable: GH1.25 3-pin cable (skew，300mm) × 1

## Interface & Pin Description <a href="#block-34ad4c79856d81ed905ffeec84bc7b59" id="block-34ad4c79856d81ed905ffeec84bc7b59"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ebbf6951-63ce-4806-9816-ae22caed9fa7/image/w=1920,quality=90,fit=scale-down" alt="image" height="270.81335429529986" width="603.9722290039062">

| Specific Name - No.          | Description                                                                                                                       |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Power Connection Interface-1 | Connect the power supply using an XT60 male-to-female power cable. The rated voltage is 48V (supports 24–48V) to power the motor. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4d618596-a407-4e97-acf6-dacb501dc767/image/w=1920,quality=90,fit=scale-down" alt="image" height="249.3606644417476" width="601.9722290039062">

| Specific Name - No.          | Description                                                                                                                                        |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| CAN Communication Terminal-2 | Connect to external control devices via the CAN communication terminal. It can receive CAN control commands and feedback motor status information. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4d3e9ba4-1298-46f9-8261-f95e73ecfaf6/image/w=1920,quality=90,fit=scale-down" alt="image" height="307.13286713286715" width="576">

| Specific Name - No.   | Description                                                                                                                                                                                                                       |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debug Serial Port – 3 | Use a GH1.25 3-pin cable to connect a USB-to-CAN debugging tool (or a general-purpose USB-to-serial module) to a PC. Then, use the Damiao Technology Debug Assistant to configure motor parameters and perform firmware upgrades. |

## Motor Dimensions and Mounting <a href="#block-34ad4c79856d816b8818ced38e1027d0" id="block-34ad4c79856d816b8818ced38e1027d0"></a>

Please refer to the motor mounting hole dimensions and positions to install the motor onto the corresponding equipment.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/47bda46f-640a-4c9d-b83a-cdf97b5a806b/image/w=1920,quality=90,fit=scale-down" alt="image" height="481.0576023723925" width="651.5694580078125">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/aabad16b-2827-4ae8-a2ab-287694f99ce4/image/w=1920,quality=90,fit=scale-down" alt="image" height="503.64003839099337" width="492.9861145019531">

## **Indicator Light Status** <a href="#block-34ad4c79856d81b49cbcffa57e969d67" id="block-34ad4c79856d81b49cbcffa57e969d67"></a>

| Normal Status   | Green-Solid On | Enabled mode, normal operating status                                                                                                                                                                                                                                                                                           |
| --------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                 | Red-Solid On   | Disabled mode                                                                                                                                                                                                                                                                                                                   |
| Abnormal Status | Red – Blinking | Indicates a fault. Corresponding fault types include: **8** – Overvoltage **9** – Undervoltage **A** – Overcurrent **B** – MOS Overtemperature **C** – Motor Coil Overtemperature **D** – Communication Loss **E** – Overload You can check the fault type via the feedback frame or through the debugging assistant interface. |

## Operating Modes <a href="#block-34ad4c79856d81ce8de6d74c0ce7e807" id="block-34ad4c79856d81ce8de6d74c0ce7e807"></a>

### MIT Mode <a href="#block-34ad4c79856d816dbd70c481f953d9b2" id="block-34ad4c79856d816dbd70c481f953d9b2"></a>

MIT mode is designed to be compatible with the original MIT mode. It allows seamless switching while enabling flexible configuration of control ranges (P\_ MAX, V\_MAX, T\_MAX). The ESC converts received CAN data into control variables to calculate the torque value, which serves as the current reference for the current loop. The current loop then regulates to achieve the specified torque current. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Derived from the MIT mode, various control modes can be implemented. For example: When kp = 0 and kd ≠ 0, setting v\_des enables constant speed rotation; When kp = 0 and kd = 0, setting t\_ff enables constant torque output.

💡

Note: When controlling position, kd must not be set to **0**,  otherwise it may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-34ad4c79856d8167b737c2dcae9fd395" id="block-34ad4c79856d8167b737c2dcae9fd395"></a>

The position cascade mode adopts a three loop series control mode, where the position loop serves as the outermost loop and its output serves as the given value for the velocity loop, while the output of the velocity loop serves as the given value for the inner loop current loop, used to control the actual current output. The control schematic diagram is shown in the following figure:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** is the target position for control, and **v\_des** is used to limit the maximum absolute velocity during motion.

When the position cascade mode is controlled using the recommended control parameters from the debugging assistant, it can achieve good control accuracy. The control process is relatively smooth, but the response time is comparatively longer. In addition to **v\_des**, the configurable related parameters also include acceleration/deceleration settings. If additional oscillations occur during the control process, increasing the acceleration/deceleration can help mitigate them.

💡

**Note:** The units of **p\_des** and **v\_des** are **rad** and **rad/s**, respectively, and their data type is float. The damping factor must be set to a **positive non-zero number**. Please refer to the precautions for the velocity mode.

### Velocity Mode <a href="#block-34ad4c79856d81e49516d30e90f3bb58" id="block-34ad4c79856d81e49516d30e90f3bb58"></a>

Velocity mode allows the motor to run steadily at the set speed. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

Note: The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

## Usage <a href="#block-34ad4c79856d811bbca6cb5a88174f60" id="block-34ad4c79856d811bbca6cb5a88174f60"></a>

The control uses the CAN standard frame format with a fixed baud rate of 1 Mbps. Based on functionality, the frames can be divided into receive frames and feedback frames. The receive frames are the control data received, used to achieve command control of the motor. The feedback frames are the motor's status data sent by the motor to the higher-level controller. Depending on the selected mode of the motor, the frame format definition and frame ID of the receive frames vary, but the feedback frames are the same across all modes.

### Feedback Frame <a href="#block-34ad4c79856d816ca351c3054e98f4ce" id="block-34ad4c79856d816ca351c3054e98f4ce"></a>

The feedback frame ID is set via the debugging assistant (MasterID), with a default value of 0. It primarily returns information about the motor’s position, speed, and torque. The frame format is defined as follows:

| Feedback Message | D\[0]      | D\[1]      | D\[2]     | D\[3]      | D\[4]                 | D\[5]   | D\[6]  | D\[7]    |
| ---------------- | ---------- | ---------- | --------- | ---------- | --------------------- | ------- | ------ | -------- |
| MST\_ID          | ID\|ERR<<4 | POS\[15:8] | POS\[7:0] | VEL\[11:4] | VEL\[3:0] \| T\[11:8] | T\[7:0] | T\_MOS | T\_Rotor |

Where:

1. ID indicates the controller ID, taking the lower 8 bits of the CAN\_ID.
2. ERR indicates a fault, with the corresponding fault types as follows:
3. **0** – Disabled（Default state after power-on）
4. **1** – Enabled
5. **8** — Overvoltage
6. **9** — Undervoltage
7. **A** — Overcurrent
8. **B** — MOS overtemperature
9. **C** — Motor coil overtemperature
10. **D** — Communication loss
11. **E** — Overload
12. POS indicates the position information of the motor.
13. VEL indicates the velocity information of the motor.
14. T indicates the torque information of the motor.
15. T\_MOS indicates the average temperature of the MOS on the driver, in °C.
16. T\_Rotor indicates the average temperature of the motor's internal coil, in °C.

Position, velocity, and torque use a linear mapping relationship to convert floating-point data into signed fixed-point data. Position uses 16-bit data, while velocity and torque both use 12-bit data.

### Control Frame in MIT Mode <a href="#block-34ad4c79856d8118aaf8da77024af683" id="block-34ad4c79856d8118aaf8da77024af683"></a>

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

### Control Frame in Position-Velocity Mode <a href="#block-34ad4c79856d816282a0d8c5f405091e" id="block-34ad4c79856d816282a0d8c5f405091e"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

Frame ID = configured CAN ID value + 0x100

* **p\_des**: Position command, float, little-endian (low byte first, high byte last)
* **v\_des**: Velocity command, float, little-endian (low byte first, high byte last)

In this mode, the CAN ID used to send commands is 0x100 + ID. The velocity command (v\_des) defines the maximum speed during the movement to the target position—i.e., the speed during the constant-velocity phase.

### Control Frame in Velocity Mode <a href="#block-34ad4c79856d81c7a2e8dec984a08675" id="block-34ad4c79856d81c7a2e8dec984a08675"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

The frame ID is the set CAN ID value plus an offset of 0x200.

* **v\_des**: Velocity reference value, floating point, little-endian (low byte first, high byte last).

The CAN ID for sending the command here is 0x200 + ID.

## Using the Debugging Assistant <a href="#block-34ad4c79856d81c88963f5e8581c5b71" id="block-34ad4c79856d81c88963f5e8581c5b71"></a>

Use the USB to CAN debugging tool to connect the motor to the PC, and perform parameter configuration and firmware upgrade via the debugging assistant.

The motor's debug serial port is connected to the PC using a GH1.25 3-pin cable.

Through the debugging assistant, you can configure motor parameters and perform firmware upgrades.

Once the serial port, CAN interface, and power interface of the motor are all properly connected, open the debugging assistant software on the PC, select the corresponding serial device, and open the serial port.

At this point, power on the motor. The serial port will output information, and the Control Mode will indicate the current drive mode.

## Specifications <a href="#block-34ad4c79856d81a792f6e17a97c6b2fb" id="block-34ad4c79856d81a792f6e17a97c6b2fb"></a>

Please refer to the following parameters for proper motor usage:

| **Motor Parameters**            | Rated Voltage              | 48V                                                                                                                                                                                               |
| ------------------------------- | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                                 | Rated Current              | 20A                                                                                                                                                                                               |
|                                 | Peak Current               | 70A                                                                                                                                                                                               |
|                                 | Rated Torque               | 40NM                                                                                                                                                                                              |
|                                 | Peak Torque                | 150NM                                                                                                                                                                                             |
|                                 | Rated Speed                | 100rpm                                                                                                                                                                                            |
|                                 | Maximum No-Load Speed      | 150rpm                                                                                                                                                                                            |
| **Motor Characteristic Values** | Reduction Ratio            | 10: 1                                                                                                                                                                                             |
|                                 | Pole pairs                 | 21                                                                                                                                                                                                |
|                                 | Phase Inductance           | 100uH                                                                                                                                                                                             |
|                                 | Phase Resistance           | 0.13Ω                                                                                                                                                                                             |
| **Structure and Weight**        | Outer Diameter             | 112mm (The fuselage is not a standard cylinder; the maximum outer dimension is 120mm.)                                                                                                            |
|                                 | Height                     | 62mm                                                                                                                                                                                              |
|                                 | Motor Weight               | About 1485g                                                                                                                                                                                       |
| **Encoder**                     | Encoder Resolution         | 14 bit                                                                                                                                                                                            |
|                                 | Number of Encoders         | 2                                                                                                                                                                                                 |
|                                 | Encoder Type               | Magnetic encoder (single-turn, absolute position of the output shaft per revolution)                                                                                                              |
| **Communication**               | Control Interface          | CAN@1Mbps                                                                                                                                                                                         |
|                                 | Parameter Tuning Interface | UART@921600bps                                                                                                                                                                                    |
| **Control and Protection**      | Control Mode               | MIT Mode                                                                                                                                                                                          |
|                                 |                            | Velocity Mode                                                                                                                                                                                     |
|                                 |                            | Position Mode                                                                                                                                                                                     |
|                                 | Protection                 | Driver over-temperature protection: Protection temperature: 120°C. If over-temperature occurs, the motor will exit the "Enable Mode".                                                             |
|                                 |                            | Motor over-temperature protection: set according to usage requirements. It is recommended not to exceed 100°C. If over-temperature occurs, the motor will exit the "Enable Mode".                 |
|                                 |                            | Motor overvoltage protection: set according to usage requirements. It is recommended not to exceed 52V. If overvoltage occurs, the motor will exit the "Enable Mode".                             |
|                                 |                            | Communication loss protection: If no CAN command is received within the set period, the motor will automatically exit the "Enable Mode".                                                          |
|                                 |                            | Motor overcurrent protection: set according to usage requirements. It is recommended not to exceed 90 A. If overcurrent occurs, the motor will exit the "Enable Mode".                            |
|                                 |                            | Motor undervoltage protection: If the power supply voltage falls below the set value, the motor will exit the "Enable Mode". It is recommended that the power supply voltage not fall below 15 V. |

## Host Computer Guide <a href="#block-34ad4c79856d81eb88d2c7889291b27a" id="block-34ad4c79856d81eb88d2c7889291b27a"></a>

[DAMIAO Host Computer User Manual](https://wiki.openelab.io/damiao/damiao-host-computer-user-manual)
