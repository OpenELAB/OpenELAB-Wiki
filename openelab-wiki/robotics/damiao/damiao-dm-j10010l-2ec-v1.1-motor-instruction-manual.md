# DAMIAO DM-J10010L-2EC V1.1 Motor Instruction Manual

> DAMIAO DM-J10010L-2EC V1.1 Motor User Guide

[**DAMIAO DM-J10010L-2EC Motor**DAMIAO DM-J10010L-2EC: 120N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.openelab.io](https://openelab.io/products/damiao-brushless-servo-dm-j10010l)

## Safety Precautions <a href="#block-34bd4c79856d800ba145ccc368be7e69" id="block-34bd4c79856d800ba145ccc368be7e69"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.

## **Motor Features** <a href="#block-34bd4c79856d807f86a8c87e93a43b9c" id="block-34bd4c79856d807f86a8c87e93a43b9c"></a>

1. Dual encoders provide single-turn absolute position feedback at the output shaft, ensuring position information is retained even after power loss.
2. Integrated motor and driver design offers compact structure with high integration.
3. Supports PC-based configuration, monitoring, and firmware upgrades.
4. Provides real-time feedback of motor Velocity, position, torque, and temperature via CAN bus.
5. Features dual temperature protection mechanisms.

## **Packing List** <a href="#block-34cd4c79856d8054bf1ae21b92f27ab4" id="block-34cd4c79856d8054bf1ae21b92f27ab4"></a>

1. Motor (with integrated driver) ×1
2. Power cable: XT60 male-to-female cable × 1
3. CAN interface: GH1.25 2-Pin Cable × 1
4. Debug serial cable: GH1.25 3-pin cable × 1

## Interface & Pin Description <a href="#block-34cd4c79856d809e99c4f57c8707edcf" id="block-34cd4c79856d809e99c4f57c8707edcf"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7efdb2c1-a407-40a6-83d8-8c77052018e6/image/w=1920,quality=90,fit=scale-down" alt="image" height="224.10256410256412" width="608">

| Specific Name - No.          | Description                                                                                                                                                                                                                                                                                                                                                                                        |
| ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power Connection Interface-1 | 1. Connect the power supply using an XT30 male-to-female power extension cable. The rated voltage is 24V (supports 24-48V), providing power to the motor. 2. The motor includes two power interfaces. Either interface can be used individually for a single motor, or multiple motors can be connected in daisy‑chain for convenient cabling. It is recommended not to exceed 2 motors in series. |
| Power Connection Interface-2 | 1. Connect the power supply using an XT30 male-to-female power extension cable. The rated voltage is 24V (supports 24-48V), providing power to the motor. 2. The motor includes two power interfaces. Either interface can be used individually for a single motor, or multiple motors can be connected in daisy‑chain for convenient cabling. It is recommended not to exceed 2 motors in series. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4d618596-a407-4e97-acf6-dacb501dc767/image/w=1920,quality=90,fit=scale-down" alt="image" height="249.3606644417476" width="601.9722290039062">

| Specific Name - No.          | Description                                                                                                                                                           |
| ---------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CAN Communication Terminal-1 | 1. Connect to external control device via CAN communication cable. Receives CAN control commands and feedback motor status. 2. Two CAN terminals; either can be used. |
| CAN Communication Terminal-2 | 1. Connect to external control device via CAN communication cable. Receives CAN control commands and feedback motor status. 2. Two CAN terminals; either can be used. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4d3e9ba4-1298-46f9-8261-f95e73ecfaf6/image/w=1920,quality=90,fit=scale-down" alt="image" height="307.13286713286715" width="576">

| Specific Name - No.   | Description                                                                                                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Debug Serial Port – 1 | Connect to PC via GH1.25 3-pin cable and a USB-to-CAN tool (or general USB-to-serial module). Use DAMIAO debugging assistant for parameter setting and firmware upgrade. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0869e46d-0d9e-49d6-a5d8-824fbb2cc340/image/w=1920,quality=90,fit=scale-down" alt="image" height="257.54146341463417" width="394">

| Specific Name - No.          | Description                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| Terminal Resistor DIP Switch | 3 - 485 120Ω Terminal Resistor 4 - CAN 120Ω Terminal Resistor 1,2 – Reserved (currently unused) |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bd30e124-70c9-4ebe-a4d6-9424d51b18ca/image/w=1920,quality=90,fit=scale-down" alt="image" height="326.68992248062017" width="629">

| Specific Name - No.            | Description                               |
| ------------------------------ | ----------------------------------------- |
| RS485 Communication Terminal 1 | RS485 communication is not yet available. |
| RS485 Communication Terminal 2 | RS485 communication is not yet available. |

## Motor Dimensions and Mounting <a href="#block-34cd4c79856d80dc93edd592c924a9ce" id="block-34cd4c79856d80dc93edd592c924a9ce"></a>

Please refer to the motor mounting hole dimensions and positions to install the motor onto the corresponding equipment.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ec9e5977-9d39-4a09-b8e1-efaaf09d6a68/image/w=1920,quality=90,fit=scale-down" alt="image" height="354.9214496871465" width="713.0694580078125">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ca440901-5f63-4929-abde-b673f468b690/image/w=1920,quality=90,fit=scale-down" alt="image" height="393.84958185159934" width="753.5750122070312">

## **Indicator Light Status** <a href="#block-34cd4c79856d801b935fda070460571a" id="block-34cd4c79856d801b935fda070460571a"></a>

| Normal Status   | Green-Solid On | Enabled mode, normal operating status                                                                                                                                                                                                                                                                                           |
| --------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                 | Red-Solid On   | Disabled mode                                                                                                                                                                                                                                                                                                                   |
| Abnormal Status | Red – Blinking | Indicates a fault. Corresponding fault types include: **8** – Overvoltage **9** – Undervoltage **A** – Overcurrent **B** – MOS Overtemperature **C** – Motor Coil Overtemperature **D** – Communication Loss **E** – Overload You can check the fault type via the feedback frame or through the debugging assistant interface. |

## Operating Modes <a href="#block-34cd4c79856d80489c73feb0b76f5592" id="block-34cd4c79856d80489c73feb0b76f5592"></a>

### MIT Mode <a href="#block-34cd4c79856d8004bc76cc60f86f53f8" id="block-34cd4c79856d8004bc76cc60f86f53f8"></a>

MIT mode is designed to be compatible with the original MIT mode. It allows seamless switching while enabling flexible configuration of control ranges (P\_ MAX, V\_MAX, T\_MAX). The ESC converts received CAN data into control variables to calculate the torque value, which serves as the current reference for the current loop. The current loop then regulates to achieve the specified torque current. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Derived from the MIT mode, various control modes can be implemented. For example: When kp = 0 and kd ≠ 0, setting v\_des enables constant speed rotation; When kp = 0 and kd = 0, setting t\_ff enables constant torque output.

💡

Note: When controlling position, kd must not be set to **0**,  otherwise it may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-34cd4c79856d80b5899ac20ad611f0d7" id="block-34cd4c79856d80b5899ac20ad611f0d7"></a>

The position cascade mode adopts a three loop series control mode, where the position loop serves as the outermost loop and its output serves as the given value for the velocity loop, while the output of the velocity loop serves as the given value for the inner loop current loop, used to control the actual current output. The control schematic diagram is shown in the following figure:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** is the target position for control, and **v\_des** is used to limit the maximum absolute velocity during motion.

When the position cascade mode is controlled using the recommended control parameters from the debugging assistant, it can achieve good control accuracy. The control process is relatively smooth, but the response time is comparatively longer. In addition to **v\_des**, the configurable related parameters also include acceleration/deceleration settings. If additional oscillations occur during the control process, increasing the acceleration/deceleration can help mitigate them.

💡

**Note:** The units of **p\_des** and **v\_des** are **rad** and **rad/s**, respectively, and their data type is float. The damping factor must be set to a **positive non-zero number**. Please refer to the precautions for the velocity mode.

### Velocity Mode <a href="#block-34cd4c79856d8070894bfc3e602895dd" id="block-34cd4c79856d8070894bfc3e602895dd"></a>

Velocity mode allows the motor to run steadily at the set speed. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

Note: The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

### **Force-Position Hybrid Mode** <a href="#block-34cd4c79856d80779cfbfe25a63c5851" id="block-34cd4c79856d80779cfbfe25a63c5851"></a>

The force-position hybrid control mode is based on position-velocity control, with additional torque adjustment. Allows control of both position and output torque at the same time. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4876b2d6-b47f-47a9-9dc7-20de651abc12/29e55681073b4ab3acd8adaf9b17c02e/w=1920,quality=90,fit=scale-down" alt="在这里插入图片描述" height="1000" width="1000">

A current command saturation stage is added after the velocity loop output command. This limits the current loop reference within the specified range.

## Usage <a href="#block-34bd4c79856d8003ade2d79b77b9cdf8" id="block-34bd4c79856d8003ade2d79b77b9cdf8"></a>

The control uses the CAN standard frame format with a default baud rate of 1 Mbps. Functionally, the frames can be divided into receive frames and feedback frames. Receive frames are the control data received, used to implement functions such as motor command control, parameter read/write, etc. Feedback frames are the status data and motor parameters sent from the motor to the host controller.

### **Read parameters** <a href="#block-34cd4c79856d80b2b563e80be4f944a7" id="block-34cd4c79856d80b2b563e80be4f944a7"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x33  | RID   |

RID represents the register address; refer to the "Register Map" section for details in this manual.

Upon successful read, the value of the register is returned. The frame format is as follows:

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x33  | RID   | data  |       |       |       |

The data is either a floating-point value or an unsigned integer, occupying 32 bits (4 bytes) in total.

The least significant bit is D4, and the most significant bit is D7. The same convention applies below.

### **Write parameters** <a href="#block-34cd4c79856d800489e2ed192ccca3b0" id="block-34cd4c79856d800489e2ed192ccca3b0"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

RID is defined as above. Upon successful write, the written value is returned. The frame format is identical to the transmitted frame.

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

Writing register data takes effect immediately but are not stored; They will be lost upon power-off unless a "Save Parameters" command is issued to store them in internal memory

### **Save parameters** <a href="#block-34cd4c79856d800ba979e9b50f68819b" id="block-34cd4c79856d800ba979e9b50f68819b"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0xAA  | 0x01  |

**Upon successful execution, the return frame format is:**

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0xAA  | 0x01  |

### Mode Switching <a href="#block-34cd4c79856d8097af93e139ac7b2129" id="block-34cd4c79856d8097af93e139ac7b2129"></a>

Multiple control modes are supported and can be switched as follows:

| Encoding | Mode                               |
| -------- | ---------------------------------- |
| 1        | MIT                                |
| 2        | Position-Velocity Mode             |
| 3        | Velocity Mode                      |
| 4        | Force-Position Hybrid Control Mode |

The mode can be changed by modifying the mode register (0x0A). During switching, the motor resets all command values to zero, including position, velocity, and torque feed-forward, KP, and KD in MIT mode.

When switching to a position control mode, to avoid impact, it is recommended to first read the precise position (value in register 0x50) and perform the switch when the motor is at zero speed whenever possible.

Mode changes are not saved to flash memory and will be lost after power-off. Upon restart, the motor loads the last mode stored in flash.

### **CAN Baud Rate Configuration** <a href="#block-34cd4c79856d80a59a9dc455b2376435" id="block-34cd4c79856d80a59a9dc455b2376435"></a>

The current CAN communication baud rate can be modified. Supported baud rates are listed below:

| Encoding | Baud Rate |
| -------- | --------- |
| 0        | 125K      |
| 1        | 200K      |
| 2        | 250K      |
| 3        | 500K      |
| 4        | 1M        |

After the baud rate is modified, the CAN automatically initializes and feeds back data at the new baud rate.

### Feedback Frame <a href="#block-34cd4c79856d80f499c8cc7853870a95" id="block-34cd4c79856d80f499c8cc7853870a95"></a>

The feedback frame ID is set by the debug assistant (Master ID), with a default value of 0. It primarily feeds back the motor's position, speed, and torque information. Its frame format is defined as follows:

| Feedback Message | D\[0]      | D\[1]      | D\[2]     | D\[3]      | D\[4]                 | D\[5]   | D\[6]  | D\[7]    |
| ---------------- | ---------- | ---------- | --------- | ---------- | --------------------- | ------- | ------ | -------- |
| MST\_ID          | ID\|ERR<<4 | POS\[15:8] | POS\[7:0] | VEL\[11:4] | VEL\[3:0] \| T\[11:8] | T\[7:0] | T\_MOS | T\_Rotor |

Where:

1. **ID:** Controller ID, using the lower 8 bits of CAN\_ID
2. **ERR :** Status code, with the following meanings
3. **0** – Disabled（Default state after power-on）
4. **1** – Enabled
5. **8** — Over-voltage
6. **9** — Under-voltage
7. **A** — Over-current
8. **B** — MOSFET over-temperature
9. **C** — Motor coil over-temperature
10. **D** — Communication loss
11. **E** — Overload
12. **POS** : Motor position
13. **VEL** : Motor velocity
14. **T** : Motor torque
15. **T\_MOS** : Average MOSFET temperature on the driver (℃ )
16. **T\_Rotor** : Average motor coil temperature (℃ )

Position, velocity, and torque use a linear mapping relationship to convert floating-point data into signed fixed-point data. Specifically, position uses 16-bit data, while both velocity and torque use 12-bit data.

### Control Frame in MIT Mode <a href="#block-34cd4c79856d80feae76feec725d84f8" id="block-34cd4c79856d80feae76feec725d84f8"></a>

| Control Message | D\[0]          | D\[1]         | D\[2]          | D\[3]                     | D\[4]     | D\[5]      | D\[6]                    | D\[7]       |
| --------------- | -------------- | ------------- | -------------- | ------------------------- | --------- | ---------- | ------------------------ | ----------- |
| ID              | p\_des \[15:8] | p\_des \[7:0] | v\_des \[11:4] | v\_des\[3:0] \| Kp\[11:8] | Kp \[7:0] | Kd \[11:4] | Kd\[3:0] \| t\_ff\[11:8] | t\_ff\[7:0] |

* **Frame ID:** Equals the configured CAN ID
* **p\_des**: Desired position
* **v\_des**: Desired velocity
* **Kp**: Position proportional gain
* **Kd**: Position derivative gain
* **T\_ff**: Feedforward torque

All parameter follows the mapping rules described in the previous section. The ranges for p\_des, v\_des, and t\_ff can be configured via the configuration tool. Kp range: \[0,500], Kd range: \[0,5].

A standard CAN frame contains 8 bytes. In MIT mode, the control command packs Position, Velocity,Kp, Kd, and Torque into these 8 bytes:

* Position: 16 bits (2 bytes)
* Velocity: 12 bits
* Kp: 12 bits
* Kd: 12 bits

### Control Frame in Position-Velocity Mode <a href="#block-34cd4c79856d80fd8855e746487b9813" id="block-34cd4c79856d80fd8855e746487b9813"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Desired position, float type, little-endian (low byte first, high byte last).
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x100 + ID. The velocity command represents the maximum velocity during trapezoidal acceleration, i.e., the constant velocity segment.

### Control Frame in Velocity Mode <a href="#block-34cd4c79856d80f1a589c8e39d5a06a8" id="block-34cd4c79856d80f1a589c8e39d5a06a8"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x200 + ID.

### **Control Frame in Force-Position Hybrid Control Mode** <a href="#block-34cd4c79856d80718d1df86a61ed7540" id="block-34cd4c79856d80718d1df86a61ed7540"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6]  | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ------ | ----- |
| 0x300+ID        | p\_des |       |       |       | v\_des |       | i\_des |       |

* **P\_des**: Desired position, in radians, float type, little-endian (low byte first, high byte last).
* **V\_des**: Velocity limit, in rad/s, scaled by 100, unsigned 16-bit, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual velocity limit range of 0-100 rad/s.
* **I\_des**: Torque current limit (per-unit), scaled by 10000, unsigned 16-bit type, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual current limit amplitude of 0-1.0.
* **Per-unit current:** Actual current divided by the maximum phase current.

## Host Computer Guide <a href="#block-34bd4c79856d8147ae81d88297aad934" id="block-34bd4c79856d8147ae81d88297aad934"></a>

[DAMIAO Host Computer User Manual](https://wiki.openelab.io/damiao/damiao-host-computer-user-manual)
