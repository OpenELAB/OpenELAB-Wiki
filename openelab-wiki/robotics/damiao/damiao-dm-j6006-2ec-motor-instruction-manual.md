# DAMIAO DM-J6006-2EC Motor Instruction Manual

> DAMIAO DM-J6006-2EC Motor User Guide

[**DAMIAO DM-J6006-2EC Motor**DAMIAO DM-J6006-2EC: 12N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.mdmbot.com](https://www.mdmbot.com/index.php?c=show\&id=102)

## **Precautions** <a href="#block-343d4c79856d81728515d282d714d38e" id="block-343d4c79856d81728515d282d714d38e"></a>

1. Please strictly operate the motor within the specified working environment and the maximum allowable winding temperature range. Failure to do so may result in permanent and irreversible damage to the product.
2. Prevent foreign objects from entering the rotor; otherwise, abnormal rotor operation may occur.
3. Before use, check whether all components are intact. Do not use the product if any parts are missing, aged, or damaged.
4. Ensure correct wiring and that the motor is installed properly and securely.
5. Do not touch the electronic rotor section during operation to avoid accidents. The motor may become hot during high-torque output; be cautious to prevent burns.
6. Users must not disassemble the motor without authorization, as this may affect control accuracy or lead to abnormal operation.

## **Motor Features** <a href="#block-343d4c79856d81018d6df1bcbf9f5822" id="block-343d4c79856d81018d6df1bcbf9f5822"></a>

1. Dual encoders provide single-turn absolute position output on the output shaft, retaining position data even in the event of power loss.
2. Integrated motor and driver design with a compact and highly integrated structure.
3. Supports upper-computer visual debugging and firmware upgrades.
4. Capable of providing feedback on motor speed, position, torque, and temperature via CAN bus.
5. Equipped with dual temperature protection.
6. Supports trapezoidal acceleration and deceleration in position control mode.

## T-N Curve <a href="#block-343d4c79856d81049444e97a3a7692c0" id="block-343d4c79856d81049444e97a3a7692c0"></a>

For the 24V version, at a constant speed of 150 rpm and room temperature of 25°C, the measured performance curve is shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ee435ee9-6e5e-4ea7-a1f4-b902dc842671/24v_150rpm_6006/w=1920,quality=90,fit=scale-down" alt="image" height="1800" width="3000">

For the 48V version, at a constant speed of 150 rpm and room temperature of 25°C, the measured performance curve is shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/64bb89b4-d137-4a5e-b276-93f6299b9544/48v_150rpm_6006/w=1920,quality=90,fit=scale-down" alt="image" height="1800" width="3000">

## **Packing List** <a href="#block-343d4c79856d8104bcd5e92ad6fe9537" id="block-343d4c79856d8104bcd5e92ad6fe9537"></a>

1. Motor (including driver) × 1
2. Power connection cable: XT30 male-to-female power cable × 1
3. CAN communication terminal: GH1.25 connecting cable - 2-pin × 1
4. Debugging serial port signal cable: GH1.25 connecting cable - 3-pin × 1

## Interface & Pin Description <a href="#block-343d4c79856d8129a342d7f4859cfca3" id="block-343d4c79856d8129a342d7f4859cfca3"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c97713d6-062a-472b-bc29-a02caf51f32f/image/w=1920,quality=90,fit=scale-down" alt="image" height="353.7798570736434" width="713.0875244140625">

| Specific Name - No.            | Description                                                                                                                        |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| Power Connection Interface - 1 | Connect the power supply using the XT30 male-to-female power cable. The rated voltage is 24V (supports 24-48V) to power the motor. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7bb0bd4e-0f83-4fc8-82d0-b5c97f965be5/image/w=1920,quality=90,fit=scale-down" alt="image" height="283.5206403655761" width="606.9874877929688">

| Specific Name - No.            | Description                                                                                                                                     |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| CAN Communication Terminal - 2 | Connect to an external control device via the CAN communication terminal to receive CAN control commands and feedback motor status information. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2c2a2c2c-3b79-42a8-a40b-b232b8dc17eb/image/w=1920,quality=90,fit=scale-down" alt="image" height="315.27277295834546" width="518.9874877929688">

| Specific Name - No.       | Description                                                                                                                                                                                                                               |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debugging Serial Port - 3 | Connect to a PC via the GH1.25 3-pin cable using a USB-to-CAN debugging tool (or a general-purpose USB-to-serial module). Use the Damiao Technology Debugging Assistant to configure motor parameters and perform firmware upgrades, etc. |

## Motor Dimensions and Mounting <a href="#block-343d4c79856d81928331ee3d8705b2e7" id="block-343d4c79856d81928331ee3d8705b2e7"></a>

Please refer to the motor mounting hole dimensions and positions to install the motor onto the corresponding equipment.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f2167492-4b01-4219-8254-62774ef1c9ac/image/w=1920,quality=90,fit=scale-down" alt="image" height="385.34861770784016" width="713.0750122070312">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2c7bf4ce-1e4c-484e-ae6c-172ae682ed79/image/w=1920,quality=90,fit=scale-down" alt="image" height="545.2999887935451" width="593.9874877929688">

## **Indicator Light Status** <a href="#block-343d4c79856d817ba362fd3f89aa6d00" id="block-343d4c79856d817ba362fd3f89aa6d00"></a>

| Normal Status   | Green-Solid On | Enabled mode, normal operating status                                                                                                                                                                                                                                                                                           |
| --------------- | -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                 | Red-Solid On   | Disabled mode                                                                                                                                                                                                                                                                                                                   |
| Abnormal Status | Red – Blinking | Indicates a fault. Corresponding fault types include: **8** – Overvoltage **9** – Undervoltage **A** – Overcurrent **B** – MOS Overtemperature **C** – Motor Coil Overtemperature **D** – Communication Loss **E** – Overload You can check the fault type via the feedback frame or through the debugging assistant interface. |

## Operating Modes <a href="#block-343d4c79856d81e2a7e6c5874c0c7ea5" id="block-343d4c79856d81e2a7e6c5874c0c7ea5"></a>

### MIT Mode <a href="#block-343d4c79856d81f09247c45b479d8c57" id="block-343d4c79856d81f09247c45b479d8c57"></a>

MIT mode is designed to be compatible with the original MIT mode. It allows seamless switching while enabling flexible configuration of control ranges (P\_ MAX, V\_MAX, T\_MAX). The ESC converts received CAN data into control variables to calculate the torque value, which serves as the current reference for the current loop. The current loop then regulates to achieve the specified torque current. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Derived from the MIT mode, various control modes can be implemented. For example: When kp = 0 and kd ≠ 0, setting v\_des enables constant speed rotation; When kp = 0 and kd = 0, setting t\_ff enables constant torque output.

💡

Note: When controlling position, kd must not be set to **0**,  otherwise it may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-343d4c79856d81dc8a49d5c6f99a1358" id="block-343d4c79856d81dc8a49d5c6f99a1358"></a>

The position cascade mode adopts a three loop series control mode, where the position loop serves as the outermost loop and its output serves as the given value for the velocity loop, while the output of the velocity loop serves as the given value for the inner loop current loop, used to control the actual current output. The control schematic diagram is shown in the following figure:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** is the target position for control, and **v\_des** is used to limit the maximum absolute velocity during motion.

When the position cascade mode is controlled using the recommended control parameters from the debugging assistant, it can achieve good control accuracy. The control process is relatively smooth, but the response time is comparatively longer. In addition to **v\_des**, the configurable related parameters also include acceleration/deceleration settings. If additional oscillations occur during the control process, increasing the acceleration/deceleration can help mitigate them.

💡

**Note:** The units of **p\_des** and **v\_des** are **rad** and **rad/s**, respectively, and their data type is float. The damping factor must be set to a **positive non-zero number**. Please refer to the precautions for the velocity mode.

### Velocity Mode <a href="#block-343d4c79856d81cc9c44eb8da9b7062e" id="block-343d4c79856d81cc9c44eb8da9b7062e"></a>

Velocity mode allows the motor to run steadily at the set speed. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

Note: The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

### **Force-Position Hybrid Control Mode** <a href="#block-343d4c79856d8106a784da99eaef089a" id="block-343d4c79856d8106a784da99eaef089a"></a>

The force-position hybrid control mode dynamically controls the output torque based on position-velocity mode control. Its control block diagram is shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4876b2d6-b47f-47a9-9dc7-20de651abc12/29e55681073b4ab3acd8adaf9b17c02e/w=1920,quality=90,fit=scale-down" alt="在这里插入图片描述" height="1000" width="1000">

A current command saturation stage is added after the output command of the speed loop, so that the input to the current loop is limited within the specified range.

### **Mode modification** <a href="#block-343d4c79856d8166be71cef1e6325cad" id="block-343d4c79856d8166be71cef1e6325cad"></a>

Mode switching can be configured via the host computer using the serial port. Simply select the desired mode and click "**Write Parameters**". After successful configuration using this method, the motor will automatically reset, and the mode will be stored inside the motor driver without being lost after power cycling.

Additionally, mode switching can also be performed via the CAN interface by modifying the content of the mode register. For details, refer to the "**Mode Switching**" subsection in the next chapter. When configured using this method, the motor will not reset, but the following five variables will be reset to zero:

1. Position command value
2. Velocity command value
3. Torque command value (MIT mode)
4. kp (MIT mode)
5. kd (MIT mode)

Without sending the "**Save Parameters**" command, the mode will not be stored and will be lost after power-off. When powered on again, the previously saved mode will be loaded.

## **CAN communication** <a href="#block-343d4c79856d81e782fac76f4ace2c27" id="block-343d4c79856d81e782fac76f4ace2c27"></a>

The motor can be used after completing calibration, parameter setting, and configuration. Control uses the CAN standard frame (STD) format, with a default baud rate of 1 Mbps. The baud rate can be changed using commands; _**see the CAN baud rate modification section for details**_**.** Functionally, frames can be divided into receive frames and feedback frames. Receive frames are the control data received, used to send commands to the motor. Feedback frames are the status data sent by the motor to the upper controller. The feedback mechanism is query-based: whenever a received frame ID matches the motor's configured CAN ID (the lower 8 bits are checked, the upper 3 bits are ignored), the driver sends the current status data to the bus. The receive frame format and frame ID vary depending on the selected motor mode, but the feedback frame is the same across all modes.

### **Modify baud rate** <a href="#block-343d4c79856d8195809ee5bd1459f520" id="block-343d4c79856d8195809ee5bd1459f520"></a>

The baud rate can be modified via the host computer using the serial port. Simply select the desired baud rate and click "Write Parameters". After successful configuration using this method, the motor will automatically reset, and the baud rate will be stored inside the motor driver without being lost after power cycling.

Another method is to modify the baud rate via the CAN interface by writing to the baud rate register. For details, see the _**"CAN Baud Rate Modification"**_ subsection in this chapter.

💡

**Note: Modifying the baud rate via CAN will fail if there are multiple devices on the bus. Therefore, proceed with caution. It is strongly recommended to configure the baud rate before use.**

### Feedback Frame <a href="#block-343d4c79856d81af98d3e310a9e42f26" id="block-343d4c79856d81af98d3e310a9e42f26"></a>

The feedback frame ID is set via the debugging assistant (MasterID), with a default value of 0. It primarily returns information about the motor’s position, speed, and torque. The frame format is defined as follows:

| Feedback Message | D\[0]      | D\[1]      | D\[2]     | D\[3]      | D\[4]                 | D\[5]   | D\[6]  | D\[7]    |
| ---------------- | ---------- | ---------- | --------- | ---------- | --------------------- | ------- | ------ | -------- |
| MST\_ID          | ID\|ERR<<4 | POS\[15:8] | POS\[7:0] | VEL\[11:4] | VEL\[3:0] \| T\[11:8] | T\[7:0] | T\_MOS | T\_Rotor |

Where:

1. **ID** indicates the controller ID, taking the lower 8 bits of the CAN\_ID.
2. **ERR** indicates a fault, with the corresponding fault types as follows:
3. **0** – Disabled
4. **1** – Enabled
5. **8** — Overvoltage
6. **9** — Undervoltage
7. **A** — Overcurrent
8. **B** — MOS overtemperature
9. **C** — Motor coil overtemperature
10. **D** — Communication loss
11. **E** — Overload
12. **POS** indicates the position information of the motor.
13. **VEL** indicates the velocity information of the motor.
14. **T** indicates the torque information of the motor.
15. **T\_MOS** indicates the average temperature of the MOS on the driver, in °C.
16. **T\_Rotor** indicates the average temperature of the motor's internal coil, in °C.

Position, velocity, and torque use a linear mapping relationship to convert floating-point data into signed fixed-point data. Position uses 16-bit data, while velocity and torque both use 12-bit data.

### Control Frame in MIT Mode <a href="#block-343d4c79856d816ea065e7eacc1a5352" id="block-343d4c79856d816ea065e7eacc1a5352"></a>

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

### Control Frame in Position-Velocity Mode <a href="#block-343d4c79856d81e8a7cdc720871048ee" id="block-343d4c79856d81e8a7cdc720871048ee"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

Frame ID = configured CAN ID value + 0x100

* **p\_des**: Position command, float, little-endian (low byte first, high byte last)
* **v\_des**: Velocity command, float, little-endian (low byte first, high byte last)

In this mode, the CAN ID used to send commands is 0x100 + ID. The velocity command (v\_des) defines the maximum speed during the movement to the target position—i.e., the speed during the constant-velocity phase.

### Control Frame in Velocity Mode <a href="#block-343d4c79856d813c8ebbcb782fe9663c" id="block-343d4c79856d813c8ebbcb782fe9663c"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

The frame ID is the set CAN ID value plus an offset of 0x200.

* **v\_des**: Velocity reference value, floating point, little-endian (low byte first, high byte last).

The CAN ID for sending the command here is 0x200 + ID.

### **Control Frame in Force-Position Hybrid Control Mode** <a href="#block-343d4c79856d814a8c68e2963479996e" id="block-343d4c79856d814a8c68e2963479996e"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6]  | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ------ | ----- |
| 0x300+ID        | p\_des |       |       |       | v\_des |       | i\_des |       |

* **P\_des**: Position reference, unit: rad, floating-point type, little-endian (low byte first, high byte last).
* **V\_des**: Speed limit value, unit: rad/s, scaled by a factor of 100, unsigned 16-bit integer type, little-endian (low byte first, high byte last). Range: 0–10000. Values exceeding 10000 are clamped to 10000. Therefore, the corresponding actual speed limit amplitude is 0–100 rad/s.
* **I\_des**: Torque current limit per-unit value, scaled by a factor of 10000, unsigned 16-bit integer type, little-endian (low byte first, high byte last). Range: 0–10000. Values exceeding 10000 are clamped to 10000. The corresponding actual current limit per-unit amplitude is 0–1.0.

💡

**Current per-unit value:** Actual current value divided by the maximum phase current value.

### **Enable** <a href="#block-343d4c79856d81b89920dbb7311424b9" id="block-343d4c79856d81b89920dbb7311424b9"></a>

After the power-on self-test is completed, the "Enable" command must be sent before control can be performed. The "Enable" frame is a control frame, with the frame ID as described previously. The difference lies in the data field. Regardless of which mode the motor is in, the data definition for "Enable" is the same, as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFC  |

### **Disable** <a href="#block-343d4c79856d816794c7de74b3b2b4f1" id="block-343d4c79856d816794c7de74b3b2b4f1"></a>

Disable is the default state of the motor upon power-up. In this state, the voltage waveforms at the three-phase terminals of the motor are identical, all being 50% modulated waves of the supply voltage. The "Disable" frame is a control frame, with the frame ID as described previously. The data field is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFD  |

### **Save position zero point** <a href="#block-343d4c79856d8133bcb2c40523c1a2aa" id="block-343d4c79856d8133bcb2c40523c1a2aa"></a>

The "Save Position Zero Point" frame is a control frame. This command sets the current output shaft position as the zero point and sets the position command value to 0. The frame ID is as described previously. The data field is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFE  |

### **Clear error** <a href="#block-343d4c79856d81748db3c204ca2348bd" id="block-343d4c79856d81748db3c204ca2348bd"></a>

When the motor experiences an error such as overheating, sending the "Clear" command can clear the error. The "Clear" frame is a control frame, with the frame ID as described previously. The data field is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFB  |

### **Read parameters** <a href="#block-343d4c79856d81a6938ce795f81d3839" id="block-343d4c79856d81a6938ce795f81d3839"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x33  | RID   |

RID is the register address. See the appendix "Register List and Range".

After a successful read, the data of the register will be returned. The frame format is as follows:

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x33  | RID   | data  |       |       |       |

The data is of floating-point type or unsigned integer type, occupying 32 bits (4 bytes). The low byte is D4, and the highest byte is D7. The same applies below.

### **Write parameters** <a href="#block-343d4c79856d81199ef6ec34cf48fe59" id="block-343d4c79856d81199ef6ec34cf48fe59"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

RID is as above. After a successful write, the written data will be returned. The frame format is the same as that of the transmitted frame.

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

The register data takes effect immediately after being written, but cannot be stored and will be lost after power-off. The "Save Parameters" command needs to be sent to write all modified parameters into the flash memory.

### **Save parameters** <a href="#block-343d4c79856d817e88a3ddd1c55bc4d0" id="block-343d4c79856d817e88a3ddd1c55bc4d0"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0xAA  | 0x01  |

**After a successful write, the return format is:**

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0xAA  | 0x01  |

💡

**【Note】:**

1. Save parameters only takes effect in disabled mode.
2. Saving parameters will retain all parameters at once.
3. This operation writes the parameters to the internal flash memory. Each operation takes up to 30 ms; please ensure sufficient time is allowed.
4. The flash memory has an erase/write endurance of approximately 10,000 cycles. Do not send the "Save Parameters" command frequently.

### Mode Switching <a href="#block-343d4c79856d81548bead3d3dba3d1b3" id="block-343d4c79856d81548bead3d3dba3d1b3"></a>

Multiple modes can be switched between each other. The currently supported control modes are as follows:

| Encoding | Mode                               |
| -------- | ---------------------------------- |
| 1        | MIT                                |
| 2        | Position-Velocity Mode             |
| 3        | Velocity Mode                      |
| 4        | Force-Position Hybrid Control Mode |

By modifying the value of the mode register (0x0A), the mode can be changed. When switching modes, the motor first clears the command values, including position, velocity, as well as the torque feedforward, Kp, and Kd values in MIT mode.

When switching from one mode to a position control mode, to prevent impact, it is recommended to first read the accurate position (value of register 0x50) before switching, and perform the switch when the motor is at zero speed whenever possible.

After the mode is changed, it will not be stored in flash memory and will be lost after power-off. Upon power-on, the control mode will be set to the mode previously stored in flash memory.

### CAN Baud Rate Modification <a href="#block-343d4c79856d8188817ec18356613a76" id="block-343d4c79856d8188817ec18356613a76"></a>

By writing specific data to the baud rate register (address 0x23), the current CAN communication baud rate can be modified. Specific baud rate modifications are supported. The currently supported baud rates are as follows:

| Encoding | Baud Rate |
| -------- | --------- |
| 0        | 125K      |
| 1        | 200K      |
| 2        | 250K      |
| 3        | 500K      |
| 4        | 1M        |
| 5        | 2M        |
| 6        | 2.5M      |
| 7        | 3.2M      |
| 8        | 4M        |
| 9        | 5M        |

After successfully modifying the baud rate, the driver will first send a feedback frame at the original baud rate, and then communicate at the new baud rate. Upon power-on, the motor first checks the stored baud rate. If it is greater than 5 Mbps, it will automatically default to 1 Mbps. For baud rates greater than 1 Mbps (excluding 1 Mbps), the CAN FD function will be automatically enabled. If the baud rate is less than or equal to 1 Mbps, it will automatically operate as CAN 2.0B.

A motor configured for CAN FD can still receive CAN 2.0B data frames, but will transmit feedback frames using CAN FD. Therefore, the upper-level controller will not be able to receive the feedback data, and the driver will continuously report errors.

If a controller using CAN 2.0B has set an incorrect ID, it can still revert the baud rate by sending a baud rate modification command.

## **Characteristic Parameters** <a href="#block-343d4c79856d80c78f03d25d5faea008" id="block-343d4c79856d80c78f03d25d5faea008"></a>

Please use the motor properly according to the following parameters.

| Type                        | Characteristic Parameters    | Description                                                                                                                                                                                       | DM-J4310-2EC V1.2（48V）                                                                                                                                                                            |
| --------------------------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor parameters            | Rated Voltage                | 24V-48V                                                                                                                                                                                           | 48V                                                                                                                                                                                               |
|                             | Rated Phase / Supply Current | 4A                                                                                                                                                                                                | 4.8A/1.6A@48V                                                                                                                                                                                     |
|                             | Peak Phase / Supply Current  | 13A                                                                                                                                                                                               | 20A/12.8A@48V                                                                                                                                                                                     |
|                             | Rated Torque                 | 4NM                                                                                                                                                                                               | 3.5NM                                                                                                                                                                                             |
|                             | Peak Torque                  | 12NM                                                                                                                                                                                              | 12.5NM                                                                                                                                                                                            |
|                             | Rated speed                  | 150rpm                                                                                                                                                                                            | 120rpm                                                                                                                                                                                            |
|                             | Maximum No-Load Speed        | 240rpm                                                                                                                                                                                            | 450rpm                                                                                                                                                                                            |
| Motor Characteristic Values | Reduction Ratio              | 6: 1                                                                                                                                                                                              | 10: 1                                                                                                                                                                                             |
|                             | Number of Pole Pairs         | 14                                                                                                                                                                                                | 14                                                                                                                                                                                                |
|                             | Phase Inductance             | 305uH                                                                                                                                                                                             | 320uH                                                                                                                                                                                             |
|                             | Phase Resistance             | 0.33Ω                                                                                                                                                                                             | 580mΩ                                                                                                                                                                                             |
| Structure and Weight        | Outer Diameter               | 76mm                                                                                                                                                                                              | 57mm                                                                                                                                                                                              |
|                             | Height                       | 36.5mm                                                                                                                                                                                            | 46mm                                                                                                                                                                                              |
|                             | Motor Weight                 | 335g                                                                                                                                                                                              | 325g                                                                                                                                                                                              |
| Encoder                     | Encoder Resolution           | 14bit                                                                                                                                                                                             | 16bit                                                                                                                                                                                             |
|                             | Number of Encoders           | 2                                                                                                                                                                                                 | 2                                                                                                                                                                                                 |
|                             | Encoder Type                 | Magnetic Encoder (Single-Turn)                                                                                                                                                                    | Magnetic Encoder (Single-Turn)                                                                                                                                                                    |
| Communication Method        | Control interface type       | CAN@1Mbps                                                                                                                                                                                         | CAN@1Mbps                                                                                                                                                                                         |
|                             | Parameter Tuning Interface   | UART@921600bps                                                                                                                                                                                    | UART@921600bps                                                                                                                                                                                    |
| Control and Protection      | Control Mode                 | MIT Mode                                                                                                                                                                                          | MIT Mode                                                                                                                                                                                          |
|                             |                              | Velocity Mode                                                                                                                                                                                     | Velocity Mode                                                                                                                                                                                     |
|                             |                              | Position Mode                                                                                                                                                                                     | Position Mode                                                                                                                                                                                     |
|                             |                              | Force-Position Hybrid Control Mode                                                                                                                                                                | Force-Position Hybrid Control Mode                                                                                                                                                                |
|                             | Protection                   | Driver over-temperature protection: Protection temperature: 120°C. If over-temperature occurs, the motor will exit the "Enable Mode".                                                             | Driver over-temperature protection: Protection temperature: 120°C. If over-temperature occurs, the motor will exit the "Enable Mode".                                                             |
|                             |                              | Motor over-temperature protection: set according to usage requirements. It is recommended not to exceed 100°C. If over-temperature occurs, the motor will exit the "Enable Mode".                 | Motor over-temperature protection: set according to usage requirements. It is recommended not to exceed 100°C. If over-temperature occurs, the motor will exit the "Enable Mode".                 |
|                             |                              | Motor overvoltage protection: set according to usage requirements. It is recommended not to exceed 32 V. If overvoltage occurs, the motor will exit the "Enable Mode".                            | Motor overvoltage protection: set according to usage requirements. It is recommended not to exceed 32 V. If overvoltage occurs, the motor will exit the "Enable Mode".                            |
|                             |                              | Communication loss protection: If no CAN command is received within the set period, the motor will automatically exit the "Enable Mode".                                                          | Communication loss protection: If no CAN command is received within the set period, the motor will automatically exit the "Enable Mode".                                                          |
|                             |                              | Motor overcurrent protection: set according to usage requirements. It is recommended not to exceed 9.8 A. If overcurrent occurs, the motor will exit the "Enable Mode".                           | Motor overcurrent protection: set according to usage requirements. It is recommended not to exceed 9.8 A. If overcurrent occurs, the motor will exit the "Enable Mode".                           |
|                             |                              | Motor undervoltage protection: If the power supply voltage falls below the set value, the motor will exit the "Enable Mode". It is recommended that the power supply voltage not fall below 15 V. | Motor undervoltage protection: If the power supply voltage falls below the set value, the motor will exit the "Enable Mode". It is recommended that the power supply voltage not fall below 15 V. |

## Host Computer Guide <a href="#block-343d4c79856d818d97f1d4468388d8cc" id="block-343d4c79856d818d97f1d4468388d8cc"></a>

[DAMIAO Host Computer User Manual](https://wiki.openelab.io/damiao/damiao-host-computer-user-manual)
