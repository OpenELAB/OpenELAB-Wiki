# DAMIAO DM-H3510 V1.0 Motor Instruction Manual

> DAMIAO DM-H3510 Motor User Guide

[**DAMIAO DM-H3510 Motor**DAMIAO DM-H3510: 0.45N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.openelab.io](https://openelab.io/products/damiao-brushless-servo-dm-h3510)

## Safety Precautions <a href="#block-34ed4c79856d816f803fc2d727aba2ac" id="block-34ed4c79856d816f803fc2d727aba2ac"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.

## **Motor Features** <a href="#block-34fd4c79856d80b9a98ec0276adefc91" id="block-34fd4c79856d80b9a98ec0276adefc91"></a>

1. Integrated design of motor and driver, compact structure, and high integration.
2. Motor speed, position, torque, and temperature can be fed back via the CAN bus.
3. Dual temperature protection.
4. Visual parameter tuning via host computer software; ready to use after simple configuration.
5. Supports CAN FD, with a maximum baud rate of up to 5 Mbps.
6. Low speed, high torque.
7. Flexible switching between multiple control modes.

## **Packing List** <a href="#block-34fd4c79856d8043aca9c365e5fec224" id="block-34fd4c79856d8043aca9c365e5fec224"></a>

| Type                               | List                                                                                                                                                                                                                                                                                                                                                                                               |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor (including driver)           | 1. Motor (including driver) ×1 2. Power + CAN communication terminal connector cable: SH1.0 connector cable - 8pin (200mm) ×1 3. Debugging serial port signal cable: SH1.0 connector cable - 3pin (200mm) ×1 It is recommended to purchase the adapter board separately: Adapter board (SH1.0 3pin + 8pin to XT30 + GH1.25), as it is not included with the motor.                                 |
| Motor + USB-to-CAN                 | 1. Motor (including driver) ×1 2. Power + CAN communication terminal connector cable: SH1.0 connector cable - 8pin (200mm) ×1 3. Debugging serial port signal cable: SH1.0 connector cable - 3pin (200mm) ×1 4. USB-to-CAN debugging tool ×1 It is recommended to purchase the adapter board separately: Adapter board (SH1.0 3pin + 8pin to XT30 + GH1.25), as it is not included with the motor. |
| Motor + USB-to-CAN + adapter board | 1. Motor (including driver) ×1 2. Power + CAN communication terminal connector cable: SH1.0 connector cable - 8pin (200mm) ×1 3. Debugging serial port signal cable: SH1.0 connector cable - 3pin (200mm) ×1 4. USB-to-CAN debugging tool ×1 5. Adapter board (SH1.0 3pin + 8pin to XT30 + GH1.25)                                                                                                 |
| Motor + adapter board              | 1. Motor (including driver) ×1 2. Power + CAN communication terminal connector cable: SH1.0 connector cable - 8pin (200mm) ×1 3. Debugging serial port signal cable: SH1.0 connector cable - 3pin (200mm) ×1 4. Adapter board (SH1.0 3pin + 8pin to XT30 + GH1.25)                                                                                                                                 |

## Interface & Pin Description <a href="#block-34fd4c79856d80dbaa75d4766e888e6d" id="block-34fd4c79856d80dbaa75d4766e888e6d"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f0b8328c-bbbe-48be-bb4c-92915e0d6b77/image/w=1920,quality=90,fit=scale-down" alt="image" height="206.84685114503816" width="531.3125">

| Interface / Pin No.                | Instruction                                                                                                                                                                                                                                                                  |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power + CAN communication terminal | 1. Connect the power supply via the SH1.0 8-pin power cable. The rated voltage is 24V (supports 24-30V) to power the motor. 2. Connect to external control devices via the CAN communication terminal to receive CAN control commands and feedback motor status information. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3fc2676a-1611-424f-b1a2-7851375a4f6f/image/w=1920,quality=90,fit=scale-down" alt="image" height="253.84930555555556" width="531.3125">

| Interface / Pin No.    | Instruction                                                                                                                                                                                                                                                                            |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debug Serial Interface | Connect the SH1.0 3-pin cable to the adapter board (SH1.0 3pin+8pin to XT30+GH1.25), then use the USB-to-CAN debugging tool (or a general USB-to-serial module) to connect to a PC. Use Damiao Technology Debug Assistant to configure motor parameters and perform firmware upgrades. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9776f560-b6a6-4161-94de-7a1aea901ba9/image/w=1920,quality=90,fit=scale-down" alt="image" height="160.06040641712465" width="531.2999877929688">

| Interface / Pin No.      | Instruction                                                                  |
| ------------------------ | ---------------------------------------------------------------------------- |
| Terminal resistor switch | The motor is equipped with a terminal resistor, which is enabled by default. |

💡

**Note:** When inserting the connector cable into the motor port, pay attention to the correct orientation of the connector to avoid bending or damaging the pins.

## Motor Dimensions and Mounting <a href="#block-34fd4c79856d80d18c33fb75e18bd8b4" id="block-34fd4c79856d80d18c33fb75e18bd8b4"></a>

Please install the motor onto the target equipment according to the motor mounting hole dimensions and layout.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a9a0bf9f-59f6-4215-946c-00cf0aeb15f5/image/w=1920,quality=90,fit=scale-down" alt="image" height="215.10742849818055" width="531.3375244140625">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2127cd0a-b0c8-41d3-8181-79ebede1117d/image/w=1920,quality=90,fit=scale-down" alt="image" height="289.6558906516184" width="531.3375244140625">

## Operating Modes <a href="#block-34fd4c79856d80d7ad4bd2c8e47daafa" id="block-34fd4c79856d80d7ad4bd2c8e47daafa"></a>

### MIT Mode <a href="#block-34fd4c79856d8078b965c0429867116c" id="block-34fd4c79856d8078b965c0429867116c"></a>

The MIT mode is compatible with the standard MIT control method, enabling seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX).

CAN commands are converted into torque values. The torque is then used as the reference for current control. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Based on the MIT model, various control strategies can be derived. For instance, when kp=0 and kd ≠ 0, a constant rotational speed can be achieved by setting v\_des. When kp=0 and kd=0, a torque output is applied directly by setting t\_ff (feedforward torque).

💡

**Note:** When controlling position, kd must not be set to zero, as this may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-34fd4c79856d80c882addc051ea6427c" id="block-34fd4c79856d80c882addc051ea6427c"></a>

This mode uses three control loops: position, velocity, and current(torque). The position loop sets the target for the velocity loop. The velocity loop then sets the target for the current loop. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** represents the target position, while **v\_des** limits the maximum absolute velocity during motion.

When tuned using recommended parameters from the configuration tool, this mode provides high accuracy and smooth motion, at the cost of slower response time.

In addition to **v\_des**, acceleration and deceleration can also be configured. If additional oscillations occur, increasing acceleration/deceleration may help stabilize the system.

💡

**Note:** The units of p\_des and v\_des are rad and rad/s respectively, and both are of type float. The damping factor must be set to a non-zero positive value.Refer to the notes for velocity mode.

### Velocity Mode <a href="#block-34fd4c79856d807bafd0d71f8923ebb7" id="block-34fd4c79856d807bafd0d71f8923ebb7"></a>

This mode keeps the motor running at the target velocity. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

**Note:** The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

### **Force-Position Hybrid Mode** <a href="#block-34fd4c79856d804bb807ffed9d801ecb" id="block-34fd4c79856d804bb807ffed9d801ecb"></a>

The force-position hybrid control mode is based on position-velocity control, with additional torque adjustment. Allows control of both position and output torque at the same time. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4876b2d6-b47f-47a9-9dc7-20de651abc12/29e55681073b4ab3acd8adaf9b17c02e/w=1920,quality=90,fit=scale-down" alt="在这里插入图片描述" height="1000" width="1000">

A current command saturation stage is added after the velocity loop output command. This limits the current loop reference within the specified range.

## **Instruction Manual** <a href="#block-34fd4c79856d80d9bb89e6a7cce5752d" id="block-34fd4c79856d80d9bb89e6a7cce5752d"></a>

Control uses the CAN standard frame format with a fixed baud rate of 1 Mbps. Frames can be divided into receive frames and feedback frames based on their function. Receive frames are the received control data used to command the motor; feedback frames are the status data sent from the motor to the higher-level controller. Depending on the selected mode of the motor, the frame format definition and frame ID of the receive frames vary, but the feedback frames are the same across all modes.

### Feedback Frame <a href="#block-34fd4c79856d801d971cd40d6d029b73" id="block-34fd4c79856d801d971cd40d6d029b73"></a>

The feedback frame ID is set via the configuration tool (Master ID), with a default value of 0. It primarily reports the motor position, velocity, and torque with the frame format defined as follows:

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

Position, velocity, and torque are are converted from floating-point data to signed fixed-point data using a linear mapping:

1. **Position**: 16-bit signed fixed-point representation.
2. **Velocity**: 12-bit signed fixed-point representation.
3. **Torque**: 12-bit signed fixed-point representation.

### Control Frame in MIT Mode <a href="#block-34fd4c79856d80d7b42ac9cf7062f63c" id="block-34fd4c79856d80d7b42ac9cf7062f63c"></a>

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

### Control Frame in Position-Velocity Mode <a href="#block-34fd4c79856d809f8911f9db0def5394" id="block-34fd4c79856d809f8911f9db0def5394"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Desired position, float type, little-endian (low byte first, high byte last).
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x100 + ID. The velocity command represents the maximum velocity during trapezoidal acceleration, i.e., the constant velocity segment.

### Control Frame in Velocity Mode <a href="#block-34fd4c79856d802b9782fea9ffe8d473" id="block-34fd4c79856d802b9782fea9ffe8d473"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x200 + ID.

### **Control Frame in Force-Position Hybrid Mode** <a href="#block-34fd4c79856d80669748e321c2acf21e" id="block-34fd4c79856d80669748e321c2acf21e"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6]  | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ------ | ----- |
| 0x300+ID        | p\_des |       |       |       | v\_des |       | i\_des |       |

* **P\_des**: Desired position, in radians, float type, little-endian (low byte first, high byte last).
* **V\_des**: Velocity limit, in rad/s, scaled by 100, unsigned 16-bit, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual velocity limit range of 0-100 rad/s.
* **I\_des**: Torque current limit (per-unit), scaled by 10000, unsigned 16-bit type, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual current limit amplitude of 0-1.0.
* **Per-unit current:** Actual current divided by the maximum phase current.

### **Enable** <a href="#block-34fd4c79856d80c88af2ed701b833d0a" id="block-34fd4c79856d80c88af2ed701b833d0a"></a>

After power-up self-test, an "Enable" command must be sent to allow motor control. The "Enable" frame is a control frame, with the frame ID as described above. The data payload is identical across all modes as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFC  |

### **Disable** <a href="#block-34fd4c79856d8017be4af2c9153cd4f9" id="block-34fd4c79856d8017be4af2c9153cd4f9"></a>

The default power-on state of the motor is "Disable." In this state, the three-phase terminal voltages are identical, each being a 50% modulation of the power supply voltage. The "Disable" frame is a control frame, with the frame ID as described above. The data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFD  |

### **Set Zero Position** <a href="#block-34fd4c79856d808d9891e607614645e2" id="block-34fd4c79856d808d9891e607614645e2"></a>

The "Set Zero Position" frame is a control frame. This command sets the current output shaft position as the zero reference and resets the position command value to 0. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFE  |

### **Clear Faults** <a href="#block-34fd4c79856d803bba5afd4e430836c7" id="block-34fd4c79856d803bba5afd4e430836c7"></a>

When faults such as overheating, sending a "Clear" can be sent to reset the fault state. The "Clear" frame is a control frame. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFB  |

### **Read parameters** <a href="#block-34fd4c79856d807b847ae6a08246a4c3" id="block-34fd4c79856d807b847ae6a08246a4c3"></a>

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

### **Write parameters** <a href="#block-34fd4c79856d8020bfd1c74a0c09e486" id="block-34fd4c79856d8020bfd1c74a0c09e486"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

RID is defined as above. Upon successful write, the written value is returned. The frame format is identical to the transmitted frame.

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

Writing register data takes effect immediately but are not stored; They will be lost upon power-off unless a "Save Parameters" command is issued to store them in internal memory

### **Save parameters** <a href="#block-34fd4c79856d800f8dbae288143d9e63" id="block-34fd4c79856d800f8dbae288143d9e63"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0xAA  | 0x01  |

**Upon successful execution, the return frame format is:**

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0xAA  | 0x01  |

💡

**【Note】:**

1. The "Save Parameters" command is only effective in Disabled Mode.
2. All parameters are stored simultaneously during this operation.
3. This operation writes parameters to the on-chip flash memory. The maximum execution time is 30ms; please allow sufficient time.
4. The flash memory supports approximately 10,000 erase/write cycles. Avoid frequent execution of the "Save Parameters" command.

### Mode Switching <a href="#block-34fd4c79856d800eac1bc93658bfb190" id="block-34fd4c79856d800eac1bc93658bfb190"></a>

Multiple control modes are supported and can be switched as follows:

| Code/ID | Mode                          |
| ------- | ----------------------------- |
| 1       | MIT                           |
| 2       | Position-Velocity             |
| 3       | Velocity                      |
| 4       | Force-Position Hybrid Control |

The mode can be changed by modifying the mode register (0x0A). During switching, the motor resets all command values to zero, including position, velocity, and torque feed-forward, KP, and KD in MIT mode.

When switching to a position control mode, to avoid impact, it is recommended to first read the precise position (value in register 0x50) and perform the switch when the motor is at zero speed whenever possible.

Mode changes are not saved to flash memory and will be lost after power-off. Upon restart, the motor loads the last mode stored in flash.

### **CAN Baud Rate Configuration** <a href="#block-34fd4c79856d804fb41bcb0a90d1b901" id="block-34fd4c79856d804fb41bcb0a90d1b901"></a>

By writing specific value to the baud rate register (address 0x23), the current CAN communication baud rate can be modified. Supported baud rates are listed below:

| Code/ID | Baud Rate |
| ------- | --------- |
| 0       | 125K      |
| 1       | 200K      |
| 2       | 250K      |
| 3       | 500K      |
| 4       | 1M        |
| 5       | 2M        |
| 6       | 2.5M      |
| 7       | 3.2M      |
| 8       | 4M        |
| 9       | 5M        |

Baud Rate Switching Behavior:

After a successful update, the driver first transmits feedback using the original baud rate and then switch to communication using the new baud rate.

Baud Rate Handling at Power-Up:

At power-up, the driver determines the communication mode based on the stored baud rate.

* If the stored baud rate exceeds 5Mbps, the baud rate is reset to 1Mbps by default.
* If the baud rate is greater than 1 Mbps (excluding 1 Mbps), the driver operates in CAN FD mode.
* If the baud rate is ≤ 1 Mbps, the driver operates in CAN 2.0B mode.

💡

**CAN FD Compatibility Note:** A motor configured in CAN FD mode can still receive CAN 2.0B data frames. However, feedback frames are transmitted using CAN FD. As a result, if the upper-level controller only supports CAN 2.0B, it will not receive feedback data, the driver may continuously report communication errors.

💡

**Recovery Note:** For controllers operating in CAN 2.0B mode, even if the CAN ID is incorrectly configured, the baud rate can still be restored by sending a baud rate configuration command.

### **Register Map** <a href="#block-34fd4c79856d80eab85bef71127f48c5" id="block-34fd4c79856d80eab85bef71127f48c5"></a>

| Address(HEX) | Address(DEC) | Variable   | Description                       | R/W | Range           | Type   |
| ------------ | ------------ | ---------- | --------------------------------- | --- | --------------- | ------ |
| 0x00         | 0            | UV\_Value  | Undervoltage Threshold            | RW  | (10.0,fmax]     | float  |
| 0x01         | 1            | KT\_Value  | Torque Constant                   | RW  | \[0.0,fmax]     | float  |
| 0x02         | 2            | OT\_Value  | Over-temperature Threshold        | RW  | \[80.0,200)     | float  |
| 0x03         | 3            | OC\_Value  | Overcurrent Threshold             | RW  | (0.0,1.0)       | float  |
| 0x04         | 4            | ACC        | Acceleration                      | RW  | (0.0,fmax)      | float  |
| 0x05         | 5            | DEC        | Deceleration                      | RW  | \[-fmax,0.0)    | float  |
| 0x06         | 6            | MAX\_SPD   | Max Velocity                      | RW  | (0.0,fmax]      | float  |
| 0x07         | 7            | MST\_ID    | Master ID                         | RW  | \[0,0x7FF]      | uint32 |
| 0x08         | 8            | ESC\_ID    | Command CAN ID                    | RW  | \[0,0x7FF]      | uint32 |
| 0x09         | 9            | TIMEOUT    | Timeout Threshold                 | RW  | \[0,2^32-1]     | uint32 |
| 0x0A         | 10           | CTRL\_MODE | Control Mode                      | RW  | \[0,4]          | uint32 |
| 0x0B         | 11           | Damp       | Viscous Damping                   | RO  | /               | float  |
| 0x0C         | 12           | Inertia    | Rotor Inertia                     | RO  | /               | float  |
| 0x0D         | 13           | hw\_ver    | Reserved                          | RO  | /               | uint32 |
| 0x0E         | 14           | sw\_ver    | Firmware Version                  | RO  | /               | uint32 |
| 0x0F         | 15           | SN         | Reservd                           | RO  | /               | uint32 |
| 0x10         | 16           | NPP        | Number of Pole Pairs              | RO  | /               | uint32 |
| 0x11         | 17           | Rs         | Phase Resistance                  | RO  | /               | float  |
| 0x12         | 18           | Ls         | Phase Inductance                  | RO  | /               | float  |
| 0x13         | 19           | Flux       | Flux Linkage                      | RO  | /               | float  |
| 0x14         | 20           | Gr         | Gear Reduction Ratio              | RO  | /               | float  |
| 0x15         | 21           | PMAX       | Position Mapping Range            | RW  | (0.0,fmax]      | float  |
| 0x16         | 22           | VMAX       | Velocity Mapping Range            | RW  | (0.0,fmax]      | float  |
| 0x17         | 23           | TMAX       | Torque Mapping Range              | RW  | (0.0,fmax]      | float  |
| 0x18         | 24           | I\_BW      | Current-loop Bandwidth            | RW  | \[100.0,1.0e4]  | float  |
| 0x19         | 25           | KP\_ASR    | Velocity Loop  Kp                 | RW  | \[0.0,fmax]     | float  |
| 0x1A         | 26           | KI\_ASR    | Velocity Loop Ki                  | RW  | \[0.0,fmax]     | float  |
| 0x1B         | 27           | KP\_APR    | Position Loop Kp                  | RW  | \[0.0,fmax]     | float  |
| 0x1C         | 28           | KI\_APR    | Position Loop Ki                  | RW  | \[0.0,fmax]     | float  |
| 0x1D         | 29           | OV\_Value  | Overvoltage Threshold             | RW  | TBD             | float  |
| 0x1E         | 30           | GREF       | Gear Torque Efficiency            | RW  | (0.0,1.0]       | float  |
| 0x1F         | 31           | Deta       | Velocity Loop Damping Coefficient | RW  | \[1.0,30.0]     | float  |
| 0x20         | 32           | V\_BW      | Velocity Loop Filter Bandwidth    | RW  | (0.0,500.0)     | float  |
| 0x21         | 33           | IQ\_c1     | Iq Gain                           | RW  | \[100.0, 1.0e4] | float  |
| 0x22         | 34           | VL\_c1     | Velocity Loop Gain Factor         | RW  | (0.0,1.0e4]     | float  |
| 0x23         | 35           | can\_br    | CAN Baud Rate                     | RW  | \[0,9]          | uint32 |
| 0x24         | 36           | sub\_ver   | Sub-version                       | RO  | /               | uint32 |
| 0x32         | 50           | u\_off     | Phase U Current Offset            | RO  | /               | float  |
| 0x33         | 51           | v\_off     | Phase V Current Offset            | RO  | /               | float  |
| 0x34         | 52           | k1         | Compensation Coefficient 1        | RO  | /               | float  |
| 0x35         | 53           | k2         | Compensation Coefficient 2        | RO  | /               | float  |
| 0x36         | 54           | m\_off     | Angle Offset                      | RO  | /               | float  |
| 0x37         | 55           | dir        | Direction                         | RO  | /               | float  |
| 0x50         | 80           | p\_m       | Motor Position                    | RO  | /               | float  |
| 0x51         | 81           | xout       | Output Shaft Position             | RO  | /               | float  |

💡

**Note:**

1. **RW:** Read/Write.
2. **RO:** Read-only.
