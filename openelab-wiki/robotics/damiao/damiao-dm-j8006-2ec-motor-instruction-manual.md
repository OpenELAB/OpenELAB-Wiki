# DAMIAO DM-J8006-2EC Motor Instruction Manual

> DAMIAO DM-J8006-2EC Motor User Guide

[**DAMIAO DM-J8006-2EC V1.1 Motor**DAMIAO DM-J8006-2EC: 20N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.mdmbot.com](https://www.mdmbot.com/index.php?c=show\&id=103)

## Safety Precautions <a href="#block-347d4c79856d80f6ab9de4ee9f89a4f0" id="block-347d4c79856d80f6ab9de4ee9f89a4f0"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.

## **Motor Features** <a href="#block-347d4c79856d80d3bc94c115dc611c0f" id="block-347d4c79856d80d3bc94c115dc611c0f"></a>

1. Dual encoders provide single-turn absolute position feedback at the output shaft, ensuring position information is retained even after power loss.
2. Integrated motor and driver design offers compact structure with high integration.
3. Supports PC-based configuration, monitoring, and firmware upgrades.
4. Provides real-time feedback of motor Velocity, position, torque, and temperature via CAN bus.
5. Features dual temperature protection mechanisms.
6. Supports trapezoidal acceleration and deceleration profiles in position mode.

## Naming Conventions <a href="#block-347d4c79856d80588b74dd8abd8b8c4a" id="block-347d4c79856d80588b74dd8abd8b8c4a"></a>

**For example：DM - J8006 X - 2EC VX.X (48V)**

| DM    | (Brand)DAMIAO Technology                                                                                                                                                                                                                                                                                                         |
| ----- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| J     | **J：**&#x4A;oint Motor Series **S：**&#x53;eparable Motor Series                                                                                                                                                                                                                                                                  |
| 80    | Stator Diameter 35、43、60、62、80、100（mm）                                                                                                                                                                                                                                                                                           |
| 06    | Reduction Ratio 06、07、09、10、19、40、48                                                                                                                                                                                                                                                                                             |
| X -   | Output Bearing /Special Versions X represents letters such as L,P,etc **-By default：** Deep Groove Ball Bearing. **-P：** Crossed Roller Bearing. **-L：** Lite version (not related to bearing type).                                                                                                                             |
| 2EC   | Encoder **-By default：**&#x73;ingle encoder. **-1EC：**&#x53;ingle encoder, CAN communication. **-2EC：**&#x44;ual encoders (single-turn absolute, output shaft),CAN communication. **-1EE：**&#x53;ingle encoder, EtherCAT communication. **-2EE：**&#x44;ual encoder (single-turn absolute, output shaft), EtherCAT communication. |
| VX.X  | Motor Version **VX.X：** Upgrade version(X=0-9),Version omitted=V1.0                                                                                                                                                                                                                                                              |
| （48V） | Driver Rated Voltage **-By default：**&#x32;4V drive voltage **-48V ：**&#x34;8V drive voltage                                                                                                                                                                                                                                     |

## Torque–Speed (T–N) Curve <a href="#block-347d4c79856d8047b5c6c03b10ff7001" id="block-347d4c79856d8047b5c6c03b10ff7001"></a>

For the 24V version, at a constant speed of 120 rpm and room temperature of 25°C, the measured performance curve is shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1be0d50c-41a0-416a-acc0-93a2bbe1f5ec/24v_120rpm_8006/w=1920,quality=90,fit=scale-down" alt="image" height="1800" width="3000">

For the 48V version, at a constant speed of 120 rpm and room temperature of 25°C, the measured performance curve is shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a339c3e0-582f-4298-9a68-5a3002b2d04d/48v_120rpm_8006/w=1920,quality=90,fit=scale-down" alt="image" height="1800" width="3000">

## **Packing List** <a href="#block-347d4c79856d8091a1c1d95ccd92caf7" id="block-347d4c79856d8091a1c1d95ccd92caf7"></a>

1. Motor (with integrated driver) ×1
2. Power cable: XT30 male-to-female cable (200 mm) × 1
3. CAN interface: GH1.25 2-Pin Cable (300mm) × 1
4. Debug serial cable: GH1.25 3-pin cable (300mm) × 1

## **Interface & Pin Description** <a href="#block-347d4c79856d80529073d271f55d0b63" id="block-347d4c79856d80529073d271f55d0b63"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c97713d6-062a-472b-bc29-a02caf51f32f/image/w=1920,quality=90,fit=scale-down" alt="image" height="353.7798570736434" width="713.0875244140625">

| Specific Name - No. | Description                                                                                              |
| ------------------- | -------------------------------------------------------------------------------------------------------- |
| Power Interface-1   | Connect the power supply using the XT30 male-to-female cable. The rated voltage is 24V（supports 24–48 V） |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7bb0bd4e-0f83-4fc8-82d0-b5c97f965be5/image/w=1920,quality=90,fit=scale-down" alt="image" height="283.5206403655761" width="606.9874877929688">

| Specific Name - No. | Description                                                                                                                         |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| CAN interface-1     | Connect external controller via the CAN communication interface to receive CAN control commands and transmit motor status feedback. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2c2a2c2c-3b79-42a8-a40b-b232b8dc17eb/image/w=1920,quality=90,fit=scale-down" alt="image" height="315.27277295834546" width="518.9874877929688">

| Specific Name - No.           | Description                                                                                                                                         |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debug Serial Interface(Port3) | Connect to a PC via the GH1.25 3-pin cable using a USB-to-CAN adapter (or USB-to-serial module) for parameters configuration and firmware upgrades. |

## Motor Dimensions and Mounting <a href="#block-347d4c79856d809c9e8cd304928f09bf" id="block-347d4c79856d809c9e8cd304928f09bf"></a>

Please install the motor onto the target equipment according to the motor mounting hole dimensions and layout.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0c166b62-1b0f-48c2-9955-c978ab840c19/image/w=1920,quality=90,fit=scale-down" alt="image" height="432.6557334175323" width="737.5750122070312">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8b14c134-b918-4b73-9c9d-8f06c4e4d871/image/w=1920,quality=90,fit=scale-down" alt="image" height="488.88479866706894" width="737.5750122070312">

## **LED Status** <a href="#block-347d4c79856d801b9efce6689ca73eb5" id="block-347d4c79856d801b9efce6689ca73eb5"></a>

| Normal Status | Solid Green  | Enable Mode (ERR = 1), normal operation                                                                                                                                                                                                                                                                                                    |
| ------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|               | Solid Red    | Disable Mode (ERR = 0)（Default state after power-on）                                                                                                                                                                                                                                                                                       |
| Fault Status  | Flashing Red | Fault codes and fault conditions: **8** – Over-voltage; **9** – Under-voltage; **A** – Over-current; **B** – MOS over-temperature; **C** – Motor winding over-temperature; **D** – Communication loss; **E** – Overload; Fault conditions can be identified via the feedback frames or displayed in the the Damiao configuration software. |

## Operating Modes <a href="#block-347d4c79856d80f68c78e9505fc016bc" id="block-347d4c79856d80f68c78e9505fc016bc"></a>

### MIT Mode <a href="#block-347d4c79856d80468499d09dcb605aa2" id="block-347d4c79856d80468499d09dcb605aa2"></a>

The MIT mode is compatible with the standard MIT control method, enabling seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX).

CAN commands are converted into torque values. The torque is then used as the reference for current control. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Based on the MIT model, various control strategies can be derived. For instance, when kp = 0 and kd ≠ 0, a constant rotational speed can be achieved by setting v\_des. When kp = 0 and kd = 0, a torque output is applied directly by setting t\_ff (feedforward torque).

💡

**Note:** When controlling position, kd must not be set to zero, as this may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-347d4c79856d80788693e6d12f55b092" id="block-347d4c79856d80788693e6d12f55b092"></a>

This mode uses three control loops: position, velocity, and current(torque). The position loop sets the target for the velocity loop. The velocity loop then sets the target for the current loop. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** represents the target position, while **v\_des** limits the maximum absolute velocity during motion.

When tuned using recommended parameters from the configuration tool, this mode provides high accuracy and smooth motion, at the cost of slower response time.

In addition to **v\_des**, acceleration and deceleration can also be configured. If additional oscillations occur, increasing acceleration/deceleration may help stabilize the system.

💡

**Note:** The units of p\_des and v\_des are rad and rad/s respectively, and both are of type float. The damping factor must be set to a non-zero positive value. Refer to the notes for velocity mode.

### Velocity Mode <a href="#block-347d4c79856d80c895ddef5f56303c1f" id="block-347d4c79856d80c895ddef5f56303c1f"></a>

This mode keeps the motor running at the target velocity. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

Note: The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

### **Force-Position Hybrid Control Mode** <a href="#block-347d4c79856d80b3a22bc43bea5acd1b" id="block-347d4c79856d80b3a22bc43bea5acd1b"></a>

The force-position hybrid control mode is based on position-velocity control, with additional torque adjustment. Allows control of both position and output torque at the same time. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4876b2d6-b47f-47a9-9dc7-20de651abc12/29e55681073b4ab3acd8adaf9b17c02e/w=1920,quality=90,fit=scale-down" alt="在这里插入图片描述" height="1000" width="1000">

A current command saturation stage is added after the velocity loop output command. This limits the current loop reference within the specified range.

### **Mode modification** <a href="#block-347d4c79856d80d99181f652d2b67781" id="block-347d4c79856d80d99181f652d2b67781"></a>

Mode switching can be configured via the host computer using the serial port. Simply select the desired mode and click "**Write Parameters**". After successful configuration using this method, the motor will automatically reset, and the mode will be stored inside the motor driver without being lost after power cycling.

Additionally, mode switching can also be performed via the CAN interface by modifying the content of the mode register. For details, refer to the "**Mode Switching**" section in the next chapter.

When using the CAN method, the motor will not reset, but the following five variables will be cleared to zero:

1. Position command value
2. Velocity command value
3. Torque command value (MIT mode)
4. kp (MIT mode)
5. kd (MIT mode)

💡

**Note:**&#x49;f the"Save Parameters" command is not issued, the mode will not be stored. It will be lost after power loss and will load the last saved mode upon power-up.

## **CAN communication** <a href="#block-347d4c79856d80cbbc41cba4dec42b4f" id="block-347d4c79856d80cbbc41cba4dec42b4f"></a>

The motor can be used after completing calibration, parameter setting, and configuration. Control uses the CAN standard frame (STD) format, with a default baud rate of 1 Mbps. The baud rate can be changed using commands; _**see the CAN baud rate modification section for details**_**.** Functionally, frames can be divided into receive frames and feedback frames. Receive frames are the control data received, used to send commands to the motor. Feedback frames are the status data sent by the motor to the upper controller. The feedback mechanism is query-based: whenever a received frame ID matches the motor's configured CAN ID (the lower 8 bits are checked, the upper 3 bits are ignored), the driver sends the current status data to the bus. The receive frame format and frame ID vary depending on the selected motor mode, but the feedback frame is the same across all modes.

### **Modify baud rate** <a href="#block-347d4c79856d80d2a06af125f43104c8" id="block-347d4c79856d80d2a06af125f43104c8"></a>

The baud rate can be modified via the host computer using the serial port. Simply select the desired baud rate and click "Write Parameters". After successful configuration using this method, the motor will automatically reset, and the baud rate will be stored inside the motor driver without being lost after power cycling.

Another method is to modify the baud rate via the CAN interface by writing to the baud rate register. For details, see the _**"CAN Baud Rate Modification"**_ subsection in this chapter.

💡

**Note:** Modifying the baud rate via CAN will fail if there are multiple devices on the bus. Therefore, proceed with caution. It is strongly recommended to configure the baud rate before use.

### Feedback Frame <a href="#block-347d4c79856d804a8700c5c169b6ec5a" id="block-347d4c79856d804a8700c5c169b6ec5a"></a>

The feedback frame ID is set via the configuration tool (Master ID), with a default value of 0. It primarily reports the motor position, velocity, and torque with the frame format defined as follows:

| Feedback Message | D\[0]      | D\[1]      | D\[2]     | D\[3]      | D\[4]                 | D\[5]   | D\[6]  | D\[7]    |
| ---------------- | ---------- | ---------- | --------- | ---------- | --------------------- | ------- | ------ | -------- |
| MST\_ID          | ID\|ERR<<4 | POS\[15:8] | POS\[7:0] | VEL\[11:4] | VEL\[3:0] \| T\[11:8] | T\[7:0] | T\_MOS | T\_Rotor |

Where:

1. **ID:** Controller ID, using the lower 8 bits of CAN\_ID
2. **ERR :** Status code, with the following meanings

**0** – Disabled（Default state after power-on）

**1** – Enabled

**8** — Over-voltage

**9** — Under-voltage

**A** — Over-current

**B** — MOSFET over-temperature

**C** — Motor coil over-temperature

**D** — Communication loss

**E** — Overload

1. **POS** : Motor position
2. **VEL** : Motor velocity
3. **T** : Motor torque
4. **T\_MOS** : Average MOSFET temperature on the driver (℃ )
5. **T\_Rotor** : Average motor coil temperature (℃ )

Position, velocity, and torque use a linear mapping relationship to convert floating-point data into signed fixed-point data. Position uses 16-bit data, while velocity and torque both use 12-bit data.

💡

**Note:**

1. After power-on, the motor position output is limited to the range of \[-π, π] rad.
2. The unit of position is rad (radians), and it represents the position of the output shaft, i.e., the position after gear reduction. All subsequent descriptions of position follow this definition and will not be repeated.
3. The unit of speed is rad/s (radians per second), and it represents the speed of the output shaft, i.e., the speed after gear reduction. All subsequent descriptions of speed follow this definition and will not be repeated.
4. The unit of torque is Nm, and it represents the torque of the output shaft, i.e., the torque after gear reduction. All subsequent descriptions of torque follow this definition and will not be repeated.

### Control Frame in MIT Mode <a href="#block-347d4c79856d803187f4d09342f5e521" id="block-347d4c79856d803187f4d09342f5e521"></a>

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

### Control Frame in Position-Velocity Mode <a href="#block-347d4c79856d8075b60dd39e117ea374" id="block-347d4c79856d8075b60dd39e117ea374"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Position command, float, little-endian (low byte first, high byte last)
* **v\_des**: Velocity command, float, little-endian (low byte first, high byte last)

In this mode, the CAN ID used to send commands is 0x100 + ID. The velocity command (v\_des) defines the maximum speed during the movement to the target position—i.e., the speed during the constant-velocity phase.

### Control Frame in Velocity Mode <a href="#block-347d4c79856d807e8396eae1b5c6e86a" id="block-347d4c79856d807e8396eae1b5c6e86a"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Velocity reference value, floating point, little-endian (low byte first, high byte last).

The CAN ID for sending the command here is 0x200 + ID.

### **Control Frame in Force-Position Hybrid Control Mode** <a href="#block-347d4c79856d80f6a512d0e5fef3fb39" id="block-347d4c79856d80f6a512d0e5fef3fb39"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6]  | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ------ | ----- |
| 0x300+ID        | p\_des |       |       |       | v\_des |       | i\_des |       |

* **P\_des**: Desired position, in radians, float type, little-endian (low byte first, high byte last).
* **V\_des**: Velocity limit, in rad/s, scaled by 100, unsigned 16-bit, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual velocity limit range of 0-100 rad/s.
* **I\_des**: Torque current limit (per-unit), scaled by 10000, unsigned 16-bit type, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual current limit amplitude of 0-1.0.
* Per-unit current: Actual current divided by the maximum phase current.

### **Enable** <a href="#block-347d4c79856d80a99c46e458c4559e04" id="block-347d4c79856d80a99c46e458c4559e04"></a>

After the power-on self-test is completed, the "Enable" command must be sent before control can be performed. The "Enable" frame is a control frame, with the frame ID as described previously. The difference lies in the data field. Regardless of which mode the motor is in, the data definition for "Enable" is the same, as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFC  |

### **Disable** <a href="#block-347d4c79856d801f80b1f29e12dfbbec" id="block-347d4c79856d801f80b1f29e12dfbbec"></a>

The default power-on state of the motor is "Disable." In this state, the three-phase terminal voltages are identical, each being a 50% modulation of the power supply voltage. The "Disable" frame is a control frame, with the frame ID as described above. The data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFD  |

### **Set Zero Position** <a href="#block-347d4c79856d8025bdb2f4bb831d044e" id="block-347d4c79856d8025bdb2f4bb831d044e"></a>

The "Set Zero Position" frame is a control frame. This command sets the current output shaft position as the zero reference and resets the position command value to 0. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFE  |

### **Clear Faults** <a href="#block-347d4c79856d805fa7aae21c1d4892e3" id="block-347d4c79856d805fa7aae21c1d4892e3"></a>

When faults such as overheating, sending a "Clear" can be sent to reset the fault state. The "Clear" frame is a control frame. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFB  |

### **Read parameters** <a href="#block-347d4c79856d809388cfc0c35f69a286" id="block-347d4c79856d809388cfc0c35f69a286"></a>

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

### **Write parameters** <a href="#block-347d4c79856d8003a232c24ba26503ab" id="block-347d4c79856d8003a232c24ba26503ab"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

RID is defined as above. Upon successful write, the written value is returned. The frame format is identical to the transmitted frame.

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

Writing register data takes effect immediately but are not stored; They will be lost upon power-off unless a "Save Parameters" command is issued to store them in internal memory

### **Save parameters** <a href="#block-347d4c79856d80e0b1d8cd2297282abc" id="block-347d4c79856d80e0b1d8cd2297282abc"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0xAA  | 0x01  |

**After a successful write, the return format is:**

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| ---------- | --------- | -------- | -------- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0xAA  | 0x01  |

💡

**【Note】:**

1. The "Save Parameters" command is only effective in Disabled Mode.
2. All parameters are stored simultaneously during this operation.
3. This operation writes parameters to the on-chip flash memory. The maximum execution time is 30ms; please allow sufficient time.
4. The flash memory supports approximately 10,000 erase/write cycles. Avoid frequent execution of the "Save Parameters" command.

### Mode Switching <a href="#block-347d4c79856d80689844c981358a1ef1" id="block-347d4c79856d80689844c981358a1ef1"></a>

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

### CAN Baud Rate Modification <a href="#block-347d4c79856d80e9a4b4ec2c445d60db" id="block-347d4c79856d80e9a4b4ec2c445d60db"></a>

By writing specific value to the baud rate register (address 0x23), the current CAN communication baud rate can be modified. Supported baud rates are listed below:

| Encoding | Baud Rate |
| -------- | --------- |
| 0        | 125K      |
| 1        | 200K      |
| 2        | 250K      |
| 3        | 500K      |
| 4        | 1M        |

## Specifications <a href="#block-347d4c79856d80c09606ef4a340cec53" id="block-347d4c79856d80c09606ef4a340cec53"></a>

Please use the motor properly according to the following parameters.

| Type                        | Characteristic Parameters    | Description                                                                                                                                                                                       |
| --------------------------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor parameters            | Rated Voltage                | 24V-48V                                                                                                                                                                                           |
|                             | Rated Phase / Supply Current | 9A                                                                                                                                                                                                |
|                             | Peak Phase / Supply Current  | 21A                                                                                                                                                                                               |
|                             | Rated Torque                 | 8NM                                                                                                                                                                                               |
|                             | Peak Torque                  | 20NM                                                                                                                                                                                              |
|                             | Rated speed                  | 120rpm                                                                                                                                                                                            |
|                             | Maximum No-Load Speed        | 190rpm@24V 390rpm@24V                                                                                                                                                                             |
| Motor Characteristic Values | Reduction Ratio              | 6: 1                                                                                                                                                                                              |
|                             | Number of Pole Pairs         | 21                                                                                                                                                                                                |
|                             | Phase Inductance             | 215uh                                                                                                                                                                                             |
|                             | Phase Resistance             | 0.4Ω                                                                                                                                                                                              |
| Structure and Weight        | Outer Diameter               | 96mm                                                                                                                                                                                              |
|                             | Height                       | 40mm                                                                                                                                                                                              |
|                             | Motor Weight                 | 559g                                                                                                                                                                                              |
| Encoder                     | Encoder Resolution           | 14bit                                                                                                                                                                                             |
|                             | Number of Encoders           | 2                                                                                                                                                                                                 |
|                             | Encoder Type                 | Magnetic Encoder (Single-Turn)                                                                                                                                                                    |
| Communication Method        | Control interface type       | CAN@1Mbps                                                                                                                                                                                         |
|                             | Parameter Tuning Interface   | UART@921600bps                                                                                                                                                                                    |
| Control and Protection      | Control Mode                 | MIT Mode                                                                                                                                                                                          |
|                             |                              | Velocity Mode                                                                                                                                                                                     |
|                             |                              | Position Mode                                                                                                                                                                                     |
|                             |                              | Force-Position Hybrid Control Mode                                                                                                                                                                |
|                             | Protection                   | Driver over-temperature protection: Protection temperature: 120°C. If over-temperature occurs, the motor will exit the "Enable Mode".                                                             |
|                             |                              | Motor over-temperature protection: set according to usage requirements. It is recommended not to exceed 100°C. If over-temperature occurs, the motor will exit the "Enable Mode".                 |
|                             |                              | Motor overvoltage protection: set according to usage requirements. It is recommended not to exceed 32V@24V,52V@48V. If overvoltage occurs, the motor will exit the "Enable Mode".                 |
|                             |                              | Communication loss protection: If no CAN command is received within the set period, the motor will automatically exit the "Enable Mode".                                                          |
|                             |                              | Motor overcurrent protection: set according to usage requirements. It is recommended not to exceed 9.8 A. If overcurrent occurs, the motor will exit the "Enable Mode".                           |
|                             |                              | Motor undervoltage protection: If the power supply voltage falls below the set value, the motor will exit the "Enable Mode". It is recommended that the power supply voltage not fall below 15 V. |

## Host Computer Guide <a href="#block-347d4c79856d80ca9c44c9ac20e2a6ff" id="block-347d4c79856d80ca9c44c9ac20e2a6ff"></a>

[DAMIAO Host Computer User Manual](https://wiki.openelab.io/damiao/damiao-host-computer-user-manual)
