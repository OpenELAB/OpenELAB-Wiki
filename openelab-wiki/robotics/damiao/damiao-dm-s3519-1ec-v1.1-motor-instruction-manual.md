# DAMIAO DM-S3519-1EC V1.1 Motor Instruction Manual

> DAMIAO DM-S3519-1EC Motor User Guide

[**DAMIAO DM-S3519-1EC Motor**DAMIAO DM-S3519-1EC: 7.8N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.openelab.io](https://openelab.io/products/damiao-brushless-servo-dm-s3519)

## Safety Precautions <a href="#block-352d4c79856d80429a13db95116b4815" id="block-352d4c79856d80429a13db95116b4815"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.

## Product Features <a href="#block-352d4c79856d806bb055eb5c7584755f" id="block-352d4c79856d806bb055eb5c7584755f"></a>

1. Intelligent driver design with plug-and-play capability. No recalibration or parameter tuning is required after motor replacement.
2. Supports firmware upgrades.
3. Supports PC-based visual parameter configuration, enabling easy setup through simple adjustments.
4. Supports CAN FD communication with a maximum baud rate of up to 5 Mbps.
5. Provides feedback of motor speed, position, torque, motor temperature, and other information via the CAN bus.
6. Equipped with dual temperature protection functions.
7. Low speed and high torque performance.
8. Supports flexible switching among multiple control modes.

## **Packing List** <a href="#block-352d4c79856d80339a88d31e08059f34" id="block-352d4c79856d80339a88d31e08059f34"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/26161f75-fbb4-450f-abc4-779bb1d8f530/image/w=1920,quality=90,fit=scale-down" alt="image" height="323.57217090069287" width="416.984375">

| Category  | Items                                                                                                                                                                                                                                                                                             |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor Kit | 1. Driver ×1 2. Geared Motor ×1 3. XT30 Power Cable (both ends, 200 mm) ×1 4. 3-Pin Serial Cable (opposite-end type, 300 mm) ×1 5. 2-Pin CAN Cable (opposite-end type, 300 mm) ×1 6. 4-pin encoder cable (opposite-end type, 250 mm) ×1 7. 3-pin motor phase cable (opposite-end type, 200 mm) ×1 |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d721a20c-e562-4364-8c24-3df901f34b05/image/w=1920,quality=90,fit=scale-down" alt="image" height="284.94535765895955" width="156.9921875">

| Category   | Items              |
| ---------- | ------------------ |
| Motor Only | 1. Geared Motor ×1 |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e41dc5f4-5042-4577-8a10-990f7c3961c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="283.07498816287875" width="379.9921875">

| Category    | Items                                                                                                                                                                                                                                                                          |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Driver Only | 1. Driver ×1 2. XT30 power cable (both ends, 200 mm) ×1 3. 3-pin serial cable (opposite-end type, 300 mm) ×1 4. 2-pin CAN cable (opposite-end type, 300 mm) ×1 5. 4-pin encoder cable (opposite-end type, 250 mm) ×1 6. 3-pin motor phase cable (opposite-end type, 200 mm) ×1 |

## Interface & Pin Description <a href="#block-352d4c79856d80d9be3cfd9fe7f05aa1" id="block-352d4c79856d80d9be3cfd9fe7f05aa1"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/261f9f86-280e-4bb7-b90f-489290386346/image/w=1920,quality=90,fit=scale-down" alt="image" height="128.73301630434784" width="328.984375">

| Interface / Pin No. | Description                                                                                                             |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Power Interface     | Connect to the power supply via an XT30-F connector cable. The rated voltage is 24V, used to supply power to the motor. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/789150d2-9b82-4c4f-8717-f7402b27fce9/image/w=1920,quality=90,fit=scale-down" alt="image" height="191.66915760869563" width="328.984375">

| Interface / Pin No. | Description                                                                     |
| ------------------- | ------------------------------------------------------------------------------- |
| Serial Port         | Used for serial communication, including debugging and parameter configuration. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fdc970f3-159d-4925-95c6-1dff46a711d6/image/w=1920,quality=90,fit=scale-down" alt="image" height="181.7628634818731" width="314.9921875">

| Interface / Pin No. | Description                 |
| ------------------- | --------------------------- |
| CAN Interface       | Used to control the driver. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7179503a-de67-46a5-b77a-e1168f9fa941/image/w=1920,quality=90,fit=scale-down" alt="image" height="157.23150275735293" width="323.9921875">

| Interface / Pin No. | Description                                                                                 |
| ------------------- | ------------------------------------------------------------------------------------------- |
| Encoder Interface   | Used to connect to the DM-S3519-1EC motor via the matching 4-pin cable (opposite-end type). |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bae0c6de-5b58-49ef-a4b7-c469d2935f5b/image/w=1920,quality=90,fit=scale-down" alt="image" height="108.98399203431373" width="289.9921875">

| Interface / Pin No.   | Description                                                           |
| --------------------- | --------------------------------------------------------------------- |
| Three-Phase Interface | Used to connect the motor’s three-phase wires via the matching cable. |

## **Geared Motor & Driver Dimensions and Installation** <a href="#block-352d4c79856d8056942cd09e7de4e470" id="block-352d4c79856d8056942cd09e7de4e470"></a>

Please refer to the driver’s mounting hole dimensions and positions to install the driver onto the corresponding equipment.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bef5bdf1-cb95-4a7f-81c1-915619a8d7a6/image/w=1920,quality=90,fit=scale-down" alt="image" height="604.7179466049678" width="677.9874877929688">

DM-S3519-2EC Geared Motor Dimension Drawing

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/91a05454-9a7f-49c6-894a-68cea3064ed9/image/w=1920,quality=90,fit=scale-down" alt="image" height="320.35911602209944" width="724.8125">

DM-S3519-2EC Driver Dimension Drawing

## **Operating Modes** <a href="#block-352d4c79856d80558052c2e4521dae6c" id="block-352d4c79856d80558052c2e4521dae6c"></a>

### **MIT Mode** <a href="#block-352d4c79856d80f5b07be94de14306c9" id="block-352d4c79856d80f5b07be94de14306c9"></a>

MIT mode is designed for compatibility with the original MIT control scheme. It enables seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX). The driver converts received CAN data into control variables, computes the torque value, and uses it as the current reference for the current loop. The current loop then regulates accordingly to achieve the commanded torque current.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f00d9819-c597-44be-a39d-2dcd28aab6ee/image/w=1920,quality=90,fit=scale-down" alt="image" height="199.14872548584418" width="544.9874877929688">

Based on MIT mode, multiple control strategies can be derived. For example:when kp = 0 and kd ≠ 0, setting v\_des enables constant-speed rotation.When kp = 0 and kd = 0, setting t\_ff enables direct torque output.

💡

**Notes:**

1. After power-on, the motor position is initialized to 0.0 rad.
2. When performing position control, kd must not be set to 0; otherwise, it may cause oscillation or even loss of control.

### **Position-Velocity Mode** <a href="#block-352d4c79856d80789a9acb95273f4d71" id="block-352d4c79856d80789a9acb95273f4d71"></a>

The position cascade mode adopts a three-loop cascade control structure. The position loop acts as the outermost loop, whose output serves as the reference for the velocity loop, while the velocity loop output serves as the reference for the inner current loop to regulate the actual current output.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c18fcb8f-028a-4950-b93c-eb932415dce9/image/w=1920,quality=90,fit=scale-down" alt="image" height="165.42499651227678" width="578.9874877929688">

* **p\_des:** target position
* **v\_des:** maximum absolute velocity during motion

When using the recommended control parameters from the tuning tool, this mode can achieve high control accuracy with relatively smooth motion, although the response time is longer. In addition to **v\_des**, acceleration and deceleration parameters can also be configured. If additional oscillations occur during control, increasing the acceleration/deceleration values may help stabilize the system.

💡

**Notes:**

1. After power-on, the motor position is initialized to 0.0 rad.
2. The units of **p\_des** and **v\_des** are rad and rad/s respectively, and both are of type float.

### **Velocity Mode** <a href="#block-352d4c79856d8057a5eac02c4d662b83" id="block-352d4c79856d8057a5eac02c4d662b83"></a>

Velocity mode allows the motor to operate steadily at a specified speed.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/906578d9-ec98-453f-a274-25bad2e97c6a/image/w=1920,quality=90,fit=scale-down" alt="image" height="178.25805489676338" width="368.9750061035156">

💡

**Notes:**

1. The unit of **v\_des** is rad/s, and the data type is float.

## Control Protocol Description <a href="#block-352d4c79856d80c687dbfa934b54dfc5" id="block-352d4c79856d80c687dbfa934b54dfc5"></a>

Control uses the CAN standard frame format. The default baud rate is 1 Mbps, and it can be switched to different baud rates via commands (see the baud rate modification section for details).According to function, frames are divided into **receive frames** and **feedback frames**. Receive frames contain control data used to command the motor. Feedback frames are used by the motor to send status data to the upper-level controller. The feedback behavior is query-based: as long as the frame ID received by the driver matches the motor’s configured CAN ID (the lower 8 bits are checked, and the upper 3 bits are ignored), the driver will transmit the current status data onto the bus.Depending on the selected motor mode, the definition of the receive frame format and frame ID differs, while the feedback frame format and data are the same across all modes.

### **Feedback Frame** <a href="#block-352d4c79856d804cb6acd0dce1363ff6" id="block-352d4c79856d804cb6acd0dce1363ff6"></a>

The feedback frame ID is set by the debugging tool (Master ID), with a default value of 0. It mainly reports the motor’s position, velocity, and torque information. The frame format is defined as follows:

| Feedback Frame | D\[0]        | D\[1]      | D\[2]     | D\[3]      | D\[4]                 | D\[5]   | D\[6]  | D\[7]    |
| -------------- | ------------ | ---------- | --------- | ---------- | --------------------- | ------- | ------ | -------- |
| MST\_ID        | ID \| ERR<<4 | POS\[15:8] | POS\[7:0] | VEL\[11:4] | VEL\[3:0] \| T\[11:8] | T\[7:0] | T\_MOS | T\_Rotor |

**Where:**

* **ID:** indicates the controller ID and takes the lower 4 bits of CAN\_ID.
* **ERR:** indicates the status, with corresponding types as follows:
* **0** — Disabled
* **1** — Enabled
* **5** — Sensor read error
* **6** — Motor parameter read error
* **8** — Overvoltage
* **9** — Undervoltage
* **A** — Overcurrent
* **B** — MOS overtemperature
* **C** — Motor winding overtemperature
* **D** — Communication loss
* **E** — Overload
* **POS:** indicates the motor position information\*.
* **VEL:** indicates the motor velocity information\*.
* **T:** indicates the motor torque information\*.
* **T\_MOS:** indicates the average temperature of the MOS on the driver, unit: °C.
* **T\_Rotor:** indicates the average temperature of the internal motor windings, unit: °C.

Position, velocity, and torque use a linear mapping relationship to convert floating-point data into signed fixed-point data. Among them, position uses 16-bit data, while velocity and torque both use 12-bit data.

💡

**Notes:**

1. After power-on, the motor position is fixed at 0.0 rad.
2. The unit of position is rad (radians), and it represents the position of the output shaft, i.e., the position after reduction. The following descriptions of position all follow this definition and will not be repeated.
3. The unit of velocity is rad/s (radians per second), and it represents the velocity of the output shaft, i.e., the velocity after reduction. The following descriptions of velocity all follow this definition and will not be repeated.
4. The unit of torque is Nm, and it represents the torque of the output shaft, i.e., the torque after reduction. The following descriptions of torque all follow this definition and will not be repeated.

### Control Frame in MIT Mode <a href="#block-352d4c79856d80d18a73d50b9279506a" id="block-352d4c79856d80d18a73d50b9279506a"></a>

| Control Frame | D\[0]         | D\[1]        | D\[2]         | D\[3]                     | D\[4]    | D\[5]     | D\[6]                    | D\[7]       |
| ------------- | ------------- | ------------ | ------------- | ------------------------- | -------- | --------- | ------------------------ | ----------- |
| ID            | p\_des\[15:8] | p\_des\[7:0] | v\_des\[11:4] | v\_des\[3:0] \| Kp\[11:8] | Kp\[7:0] | Kd\[11:4] | Kd\[3:0] \| t\_ff\[11:8] | t\_ff\[7:0] |

Frame ID is equal to the configured CAN ID value.

* **p\_des**: position command
* **v\_des**: velocity command
* **Kp**: position proportional gain
* **Kd**: position derivative gain
* **t\_ff**: torque command

All parameters follow the mapping relationship described in the previous section. The ranges of _p\_des_, _v\_des_, and _t\_ff_ can be configured via the debugging tool. The range of **Kp** is \[0, 500], and the range of **Kd** is \[0, 5].

A standard CAN frame contains only 8 bytes. In MIT mode, the control command packs five parameters—Position, Velocity, Kp, Kd, and Torque—into these 8 bytes. Specifically:Position occupies 2 bytes (16 bits)、Velocity occupies 12 bits、Kp occupies 12 bits、Kd occupies 12 bits.

### Control Frame in Position-Velocity Mode <a href="#block-352d4c79856d80e18fbcfc63f7b092c6" id="block-352d4c79856d80e18fbcfc63f7b092c6"></a>

| Control Frame | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| ------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID      | p\_des |       |       |       | v\_des |       |       |       |

Frame ID is equal to the configured CAN ID value plus an offset of 0x100.

* **p\_des**: position command, float type, little-endian (low byte first, high byte last)
* **v\_des**: velocity command, float type, little-endian (low byte first, high byte last)

The CAN ID used to send the command here is _0x100 + ID_. The velocity command defines the maximum speed during motor operation.

**Example:**

To move a motor with CAN ID = 5 to a position of 180° (3.14159 rad) at a maximum speed not exceeding 10 rad/s, the command is:

| Frame ID | D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| -------- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x105    | 0xCF  | 0x0F  | 0x49  | 0x40  | 0x00  | 0x00  | 0x20  | 0x42  |

### Control Frame in Velocity Mode <a href="#block-352d4c79856d80e4a38dce81c3441de6" id="block-352d4c79856d80e4a38dce81c3441de6"></a>

| Control Frame | D\[0]  | D\[1] | D\[2] | D\[3] |
| ------------- | ------ | ----- | ----- | ----- |
| 0x200+ID      | v\_des |       |       |       |

Frame ID is equal to the configured CAN ID value plus an offset of 0x200.

* **v\_des**: velocity command, float type, little-endian (low byte first, high byte last)

The CAN ID used to send the command here is _0x200 + ID_.

**Example:**

To rotate a motor with CAN ID = 3 at a speed of 60 rpm (6.283 rad/s), the command is:

| Frame ID | D\[0] | D\[1] | D\[2] | D\[3] |
| -------- | ----- | ----- | ----- | ----- |
| 0x203    | 0x56  | 0x0E  | 0xC9  | 0x40  |

## Instructions for Use <a href="#block-352d4c79856d8008a7a5cb2202456237" id="block-352d4c79856d8008a7a5cb2202456237"></a>

The motor has been calibrated and characterized before leaving the factory, and the parameters are stored inside the motor. Under normal conditions, it can be used directly without recalibration or re-characterization. The following provides the calibration procedure, which can be skipped if no abnormal conditions are present.

### CAN Configuration Commands <a href="#block-352d4c79856d806cb834e8db831e3211" id="block-352d4c79856d806cb834e8db831e3211"></a>

Motor parameters can be configured not only via the host computer (serial communication), but also through the CAN bus. In addition to basic parameter configuration, mode switching and baud rate modification are supported.

#### 1. Read Parameters <a href="#block-353d4c79856d80198e13d2ab47a41988" id="block-353d4c79856d80198e13d2ab47a41988"></a>

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4]          | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | -------------- | ----- | ----- | ----- |
| 0x7FF    | STD       | CANID\_L | CANID\_H | 0x33  | RID   | xx(don’t care) |       |       |       |

* **RID**: Register address (refer to Section 6).

After a successful read, the register data will be returned in the following format:

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID  | STD       | CANID\_L | CANID\_H | 0x33  | RID   | Data  |       |       |       |

The data is either floating-point or unsigned integer, occupying 32 bits (4 bytes). The lowest byte is D\[4], and the highest byte is D\[7]. The same applies hereinafter.

#### 2. Write Parameters <a href="#block-353d4c79856d80618e42d0b07dfd7343" id="block-353d4c79856d80618e42d0b07dfd7343"></a>

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | Data  |       |       |       |

RID is as defined above. After writing data, the driver performs range validation. If the value is within the specified range, the write is successful. The driver immediately applies the corresponding parameters and returns the written data. The frame format is the same as the transmitted frame.

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID  | STD       | CANID\_L | CANID\_H | 0x33  | RID   | Data  |       |       |       |

If the value is out of range, the write fails, and the driver returns the original register data.

💡

**Note:**

Register writes take effect immediately but are not stored. Data will be lost after power-off. To retain parameters, a save command must be sent to write them into internal memory.

#### 3. Save Parameters <a href="#block-353d4c79856d80e39c27d17cc964dbab" id="block-353d4c79856d80e39c27d17cc964dbab"></a>

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| -------- | --------- | -------- | -------- | ----- | ----- |
| 0x7FF    | STD       | CANID\_L | CANID\_H | 0xAA  | xx    |

After successful writing, the return format is:

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| -------- | --------- | -------- | -------- | ----- | ----- |
| MST\_ID  | STD       | CANID\_L | CANID\_H | 0xAA  | 01    |

💡

**Notes:**

1. Saving parameters is only valid in the disabled state.
2. All parameters are saved at once.
3. This operation writes parameters into internal flash memory. The maximum operation time is 30 ms; ensure sufficient time is reserved.
4. Flash erase/write endurance is approximately 10,000 cycles. Do not send the “save parameters” command frequently.

#### 4. Mode Switching <a href="#block-353d4c79856d803fab77df29d755270f" id="block-353d4c79856d803fab77df29d755270f"></a>

Multiple control modes are supported for switching between each other. The currently supported control modes are as follows:

| Code | Mode              |
| ---- | ----------------- |
| 1    | MIT               |
| 2    | Position-Velocity |
| 3    | Velocity          |

By modifying the mode register (**0x0A**), the control mode can be changed. During switching, the motor command values will first be cleared, including position, velocity, and in MIT mode also torque feedforward, Kp, and Kd.

When switching to position control mode, to avoid impact, it is recommended to first read the accurate position and perform switching at zero speed whenever possible.

Mode changes are not stored in flash and will be lost after power-off. After power-on, the mode defaults to the last mode stored in flash.

#### 5. Baud Rate Configuration <a href="#block-353d4c79856d80fba273fc234d307b3b" id="block-353d4c79856d80fba273fc234d307b3b"></a>

By writing specific data to the baud rate register (address **0x23**), the CAN communication baud rate can be modified. Supported baud rates are as follows:

| Code | Baud Rate |
| ---- | --------- |
| 0    | 125K      |
| 1    | 200K      |
| 2    | 250K      |
| 3    | 500K      |
| 4    | 1M        |
| 5    | 2M        |
| 6    | 2.5M      |
| 7    | 3.2M      |
| 8    | 4M        |
| 9    | 5M        |

After the baud rate is successfully modified, the driver first communicates using the original baud rate and then switches to the new baud rate for communication.Upon power-up, the motor first checks the stored baud rate. If it is greater than 5 Mbps, it will automatically default to 1 Mbps. If it is greater than 1 Mbps (excluding 1 Mbps), the system will automatically switch to CAN FD mode. If the baud rate is less than or equal to 1 Mbps, it will automatically switch to CAN 2.0B mode.A motor configured in CAN FD mode can still receive CAN 2.0B data frames; however, feedback frames are transmitted using CAN FD. As a result, the upper-level controller will not be able to receive feedback data, and the driver will continuously report errors.For a controller operating in CAN 2.0B mode, even if an incorrect ID is set, the baud rate can still be restored by using the baud rate modification command.

#### 6. Register Address Table <a href="#block-353d4c79856d80798fb8e6bf7b247d36" id="block-353d4c79856d80798fb8e6bf7b247d36"></a>

| Addr (HEX) | Addr (DEC) | Variable   | Description                 | R/W | Range           | Type   |
| ---------- | ---------- | ---------- | --------------------------- | --- | --------------- | ------ |
| 0x00       | 0          | UV\_Value  | Undervoltage protection     | RW  | (10.0, fmax]    | float  |
| 0x01       | 1          | KT\_Value  | Torque constant             | RW  | \[0.0, fmax]    | float  |
| 0x02       | 2          | OT\_Value  | Overtemperature protection  | RW  | \[80.0, 200)    | float  |
| 0x03       | 3          | OC\_Value  | Overcurrent protection      | RW  | (0.0, 1.0)      | float  |
| 0x04       | 4          | ACC        | Acceleration                | RW  | (0.0, fmax)     | float  |
| 0x05       | 5          | DEC        | Deceleration                | RW  | (-fmax, 0.0)    | float  |
| 0x06       | 6          | MAX\_SPD   | Maximum speed               | RW  | (0.0, fmax]     | float  |
| 0x07       | 7          | MST\_ID    | Feedback ID                 | RW  | \[0, 0x7FF]     | uint32 |
| 0x08       | 8          | ESC\_ID    | Receive ID                  | RW  | \[0, 0x7FF]     | uint32 |
| 0x09       | 9          | TIMEOUT    | Timeout alarm               | RW  | \[0, 2³²-1]     | uint32 |
| 0x0A       | 10         | CTRL\_MODE | Control mode                | RW  | \[0, 4]         | uint32 |
| 0x0B       | 11         | Damp       | Viscous coefficient         | RO  | /               | float  |
| 0x0C       | 12         | Inertia    | Inertia                     | RO  | /               | float  |
| 0x0D       | 13         | hw\_ver    | Reserved                    | RO  | /               | uint32 |
| 0x0E       | 14         | sw\_ver    | Software version            | RO  | /               | uint32 |
| 0x0F       | 15         | SN         | Reserved                    | RO  | /               | uint32 |
| 0x10       | 16         | NPP        | Pole pairs                  | RO  | /               | uint32 |
| 0x11       | 17         | Rs         | Phase resistance            | RO  | /               | float  |
| 0x12       | 18         | Ls         | Phase inductance            | RO  | /               | float  |
| 0x13       | 19         | Flux       | Flux linkage                | RO  | /               | float  |
| 0x14       | 20         | Gr         | Gear ratio                  | RO  | /               | float  |
| 0x15       | 21         | PMAX       | Position mapping range      | RW  | (0.0, fmax]     | float  |
| 0x16       | 22         | VMAX       | Velocity mapping range      | RW  | (0.0, fmax]     | float  |
| 0x17       | 23         | TMAX       | Torque mapping range        | RW  | (0.0, fmax]     | float  |
| 0x18       | 24         | I\_BW      | Current loop bandwidth      | RW  | \[100.0, 1.0e4] | float  |
| 0x19       | 25         | KP\_ASR    | Speed loop Kp               | RW  | \[0.0, fmax]    | float  |
| 0x1A       | 26         | KI\_ASR    | Speed loop Ki               | RW  | \[0.0, fmax]    | float  |
| 0x1B       | 27         | KP\_APR    | Position loop Kp            | RW  | \[0.0, fmax]    | float  |
| 0x1C       | 28         | KI\_APR    | Position loop Ki            | RW  | \[0.0, fmax]    | float  |
| 0x1D       | 29         | OV\_Value  | Overvoltage protection      | RW  | TBD             | float  |
| 0x1E       | 30         | GREF       | Gear torque efficiency      | RW  | (0.0, 1.0]      | float  |
| 0x1F       | 31         | Deta       | Speed loop damping          | RW  | \[1.0, 30.0]    | float  |
| 0x20       | 32         | V\_BW      | Speed loop filter bandwidth | RW  | (0.0, 500.0)    | float  |
| 0x21       | 33         | IQ\_c1     | Current loop enhancement    | RW  | \[100.0, 1.0e4] | float  |
| 0x22       | 34         | VL\_c1     | Speed loop enhancement      | RW  | (0.0, 1.0e4]    | float  |
| 0x23       | 35         | can\_br    | CAN baud rate code          | RW  | \[0, 9]         | uint32 |
| 0x24       | 36         | sub\_ver   | Sub-version                 | RO  | /               | uint32 |
| 0x32       | 50         | u\_off     | Phase U offset              | RO  | /               | float  |
| 0x33       | 51         | v\_off     | Phase V offset              | RO  | /               | float  |
| 0x34       | 52         | k1         | Compensation factor 1       | RO  | /               | float  |
| 0x35       | 53         | k2         | Compensation factor 2       | RO  | /               | float  |
| 0x36       | 54         | m\_off     | Angle offset                | RO  | /               | float  |
| 0x37       | 55         | dir        | Direction                   | RO  | /               | float  |
| 0x50       | 80         | p\_m       | Current motor position      | RO  | /               | float  |
| 0x51       | 81         | xout       | Output shaft position       | RO  | /               | float  |

**RW**: Read/Write

**RO:** Read Only

## **Characteristic Curves** <a href="#block-352d4c79856d80e8afdefeaf211e13c8" id="block-352d4c79856d80e8afdefeaf211e13c8"></a>

Test Environment: Room temperature at 25°C, laboratory conditions.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/db5eba92-a398-4e61-ab68-5a943ed983fa/image/w=1920,quality=90,fit=scale-down" alt="image" height="303.69585396039605" width="562.8125">

## Characteristic Parameters <a href="#block-352d4c79856d81d885ccd8e3042aead1" id="block-352d4c79856d81d885ccd8e3042aead1"></a>

Please use the motor appropriately according to the following parameters.

| Motor Parameters            | Rated Voltage                       | 24V (driver supports 15–52V power supply)                                                                                                         |
| --------------------------- | ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
|                             | Rated phase current (power current) | 9.2 A (8.6 A)                                                                                                                                     |
|                             | Peak phase current (power current)  | 20.5 A (16.1 A)                                                                                                                                   |
|                             | Rated Torque                        | 3.5Nm                                                                                                                                             |
|                             | Peak Torque                         | 7.8Nm                                                                                                                                             |
|                             | Rated Speed                         | 395rpm                                                                                                                                            |
|                             | No-load Maximum Speed               | 435rpm                                                                                                                                            |
| Motor Characteristic Values | Gear Ratio                          | 3591/187(1:19.2)                                                                                                                                  |
|                             | Pole Pairs                          | 7                                                                                                                                                 |
|                             | Phase Inductance                    | 55uH                                                                                                                                              |
|                             | Phase Resistance                    | 0.2Ω                                                                                                                                              |
| Structure & Weight          | Outer Diameter                      | Motor 42mm                                                                                                                                        |
|                             | Height                              | Motor 91.5mm                                                                                                                                      |
|                             | Motor Weight                        | Approx. 396g                                                                                                                                      |
| Encoder                     | Encoder Type                        | Incremental encoder                                                                                                                               |
| Communication               | Control Interface                   | CAN                                                                                                                                               |
|                             | Tuning Interface                    | UART @ 921600bps                                                                                                                                  |
| Control & Protection        | Control Modes                       | MIT Mode                                                                                                                                          |
|                             |                                     | Velocity Mode                                                                                                                                     |
|                             |                                     | Position Mode                                                                                                                                     |
|                             | Protection                          | Protection temperature: 120℃. When exceeded, the motor will exit “Enabled Mode”.                                                                  |
|                             |                                     | Configurable based on application requirements. Recommended not to exceed 100℃. When exceeded, the motor will exit “Enabled Mode”.                |
|                             |                                     | Configurable based on application requirements. Recommended not to exceed 60V. When exceeded, the motor will exit “Enabled Mode”.                 |
|                             |                                     | If no CAN command is received within the configured period, the motor will automatically exit “Enabled Mode”.                                     |
|                             |                                     | Configurable based on application requirements. Recommended not to exceed 20A (phase current). When exceeded, the motor will exit “Enabled Mode”. |
|                             |                                     | If the supply voltage is lower than the set threshold, the motor will exit “Enabled Mode”. Minimum operating voltage is 15V.                      |
