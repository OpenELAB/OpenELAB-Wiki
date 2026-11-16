# DAMIAO DM-S2325-1EC V1.0 Motor Instruction Manual

> DAMIAO DM-S2325 Motor User Guide

[**DAMIAO DM-2325 Motor**DAMIAO DM-2325: 5N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.mdmbot.com](https://www.mdmbot.com/index.php?c=show\&id=123)

## Safety Precautions <a href="#block-351d4c79856d80c99a5dd93ffe79c481" id="block-351d4c79856d80c99a5dd93ffe79c481"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.
7. Do not apply force to the motor’s three-phase wires or the 4-pin cable outlet, as this may cause permanent and irreversible damage to the product.
8. If the motor operates continuously under load (rated or above), it is recommended to replace the lubricant grease every seven hours to prevent gear wear on the motor side due to grease degradation.

## Product Features <a href="#block-351d4c79856d80c6a74cc91dcc5bf811" id="block-351d4c79856d80c6a74cc91dcc5bf811"></a>

1. Intelligent driver design with plug-and-play capability. No recalibration or parameter tuning is required after motor replacement.
2. Supports firmware upgrades.
3. Supports PC-based visual parameter configuration, enabling easy setup through simple adjustments.
4. Supports CAN FD communication with a maximum baud rate of up to 5 Mbps.
5. Provides feedback of motor speed, position, torque, motor temperature, and other information via the CAN bus.
6. Equipped with dual temperature protection functions.
7. High speed and high torque performance.
8. Supports flexible switching among multiple control modes.

## **Packing List** <a href="#block-351d4c79856d806f9738fafc315c0993" id="block-351d4c79856d806f9738fafc315c0993"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e27d6d29-a589-47ca-8771-bcb9a4596388/image/w=1920,quality=90,fit=scale-down" alt="image" height="244.91871839652035" width="443.57501220703125">

| Category  | Items                                                                                                                                                                     |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor Kit | 1. Driver ×1 2. Geared Motor ×1 3. XT30 Power Cable (both ends, 200 mm) ×1 4. 3-Pin Serial Cable (opposite ends, 300 mm) ×1 5. 2-Pin CAN Cable (opposite ends, 300 mm) ×1 |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1e820791-fb3f-42a2-ba14-5b13806abc5a/image/w=1920,quality=90,fit=scale-down" alt="image" height="235.82822085889572" width="310">

| Category   | Items              |
| ---------- | ------------------ |
| Motor Only | 1. Geared Motor ×1 |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f943b944-96ca-4e70-8b95-a1b928bbc280/image/w=1920,quality=90,fit=scale-down" alt="image" height="269.5732677371003" width="413.9875183105469">

| Category    | Items             |
| ----------- | ----------------- |
| Driver Only | 1. Motor Rotor ×1 |

## Interface & Pin Description <a href="#block-351d4c79856d802d9985e225b6df973b" id="block-351d4c79856d802d9985e225b6df973b"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9b7611bb-0fa7-45f2-a287-4d457c9cf189/image/w=1920,quality=90,fit=scale-down" alt="image" height="154.29863891601562" width="368.9750061035156">

| Interface / Pin No. | Description                                                                                                             |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Power Interface     | Connect to the power supply via an XT30-F connector cable. The rated voltage is 24V, used to supply power to the motor. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f9759c28-031f-4d90-89c9-cc251adb58dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="238.7686577430138" width="373.9750061035156">

| Interface / Pin No. | Description                                                                     |
| ------------------- | ------------------------------------------------------------------------------- |
| Serial Port         | Used for serial communication, including debugging and parameter configuration. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ac4a3ba9-c65e-4f19-8228-463f7138a4e8/image/w=1920,quality=90,fit=scale-down" alt="image" height="201.18110236220474" width="365">

| Interface / Pin No. | Description                 |
| ------------------- | --------------------------- |
| CAN Interface       | Used to control the driver. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8b7595af-1e46-4eeb-87fe-4d3723c9aa88/image/w=1920,quality=90,fit=scale-down" alt="image" height="172.6153846153846" width="374">

| Interface / Pin No. | Description                                                                                 |
| ------------------- | ------------------------------------------------------------------------------------------- |
| Encoder Interface   | Used to connect to the DM-S2325-1EC motor via the matching 4-pin cable (opposite-end type). |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2b7e64aa-d851-4bf0-bf75-efe1d13e8eeb/image/w=1920,quality=90,fit=scale-down" alt="image" height="125.32185594713366" width="353.9624938964844">

| Interface / Pin No.   | Description                                    |
| --------------------- | ---------------------------------------------- |
| Three-Phase Interface | Used to connect the motor’s three-phase wires. |

## **Geared Motor & Driver Dimensions and Installation** <a href="#block-351d4c79856d80d58952c56c1c5de1e0" id="block-351d4c79856d80d58952c56c1c5de1e0"></a>

Please refer to the driver’s mounting hole dimensions and positions to install the driver onto the corresponding equipment.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2c4b124a-182d-426e-af2a-c87e4240b7f8/image/w=1920,quality=90,fit=scale-down" alt="image" height="722.4749999999999" width="624">

DM-S2325-1EC Geared Motor Dimension Drawing

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/30985594-39f6-451c-b422-ef5483416ec7/image/w=1920,quality=90,fit=scale-down" alt="image" height="371.99371693121697" width="724.8125">

DM3520-1EC Driver Dimension Drawing

## **Operating Modes** <a href="#block-351d4c79856d80bd8941ea5ed6f35188" id="block-351d4c79856d80bd8941ea5ed6f35188"></a>

### **MIT Mode** <a href="#block-351d4c79856d80209b46e3db98c60a69" id="block-351d4c79856d80209b46e3db98c60a69"></a>

MIT mode is designed for compatibility with the original MIT control scheme. It enables seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX). The driver converts received CAN data into control variables, computes the torque value, and uses it as the current reference for the current loop. The current loop then regulates accordingly to achieve the commanded torque current.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f00d9819-c597-44be-a39d-2dcd28aab6ee/image/w=1920,quality=90,fit=scale-down" alt="image" height="199.14872548584418" width="544.9874877929688">

Based on MIT mode, multiple control strategies can be derived. For example:when kp = 0 and kd ≠ 0, setting **v\_des** enables constant-speed rotation.When kp = 0 and kd = 0, setting t\_ff enables direct torque output.

💡

**Notes:**

1. After power-on, the motor position is initialized to 0.0 rad.
2. When performing position control, kd must not be set to 0; otherwise, it may cause oscillation or even loss of control.

### **Position-Velocity Mode** <a href="#block-351d4c79856d80c6b4e8f12776eb496c" id="block-351d4c79856d80c6b4e8f12776eb496c"></a>

The position cascade mode adopts a three-loop cascade control structure. The position loop acts as the outermost loop, whose output serves as the reference for the velocity loop, while the velocity loop output serves as the reference for the inner current loop to regulate the actual current output.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c18fcb8f-028a-4950-b93c-eb932415dce9/image/w=1920,quality=90,fit=scale-down" alt="image" height="165.42499651227678" width="578.9874877929688">

* **p\_des:** target position
* **v\_des:** maximum absolute velocity during motion

When using the recommended control parameters from the tuning tool, this mode can achieve high control accuracy with relatively smooth motion, although the response time is longer. In addition to **v\_des**, acceleration and deceleration parameters can also be configured. If additional oscillations occur during control, increasing the acceleration/deceleration values may help stabilize the system.

💡

**Notes:**

1. After power-on, the motor position is initialized to 0.0 rad.
2. The units of **p\_des** and **v\_des** are rad and rad/s respectively, and both are of type float.

### **Velocity Mode** <a href="#block-351d4c79856d800a99fece254e6bdaf7" id="block-351d4c79856d800a99fece254e6bdaf7"></a>

Velocity mode allows the motor to operate steadily at a specified speed.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/906578d9-ec98-453f-a274-25bad2e97c6a/image/w=1920,quality=90,fit=scale-down" alt="image" height="178.25805489676338" width="368.9750061035156">

💡

**Notes:**

1. The unit of **v\_des** is rad/s, and the data type is float.

## Control Protocol Description <a href="#block-351d4c79856d803dab38e61ce1b23cf5" id="block-351d4c79856d803dab38e61ce1b23cf5"></a>

Control uses the CAN standard frame format. The default baud rate is 1 Mbps, and it can be switched to different baud rates via commands (see the baud rate modification section for details).According to function, frames are divided into **receive frames** and **feedback frames**. Receive frames contain control data used to command the motor. Feedback frames are used by the motor to send status data to the upper-level controller. The feedback behavior is query-based: as long as the frame ID received by the driver matches the motor’s configured CAN ID (the lower 8 bits are checked, and the upper 3 bits are ignored), the driver will transmit the current status data onto the bus.Depending on the selected motor mode, the definition of the receive frame format and frame ID differs, while the feedback frame format and data are the same across all modes.

### **Feedback Frame** <a href="#block-351d4c79856d8084b8d1eb8c988322d6" id="block-351d4c79856d8084b8d1eb8c988322d6"></a>

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

### Control Frame in MIT Mode <a href="#block-351d4c79856d80c5bed6df883f842902" id="block-351d4c79856d80c5bed6df883f842902"></a>

| Control Frame | D\[0]         | D\[1]        | D\[2]         | D\[3]                     | D\[4]    | D\[5]     | D\[6]                    | D\[7]       |
| ------------- | ------------- | ------------ | ------------- | ------------------------- | -------- | --------- | ------------------------ | ----------- |
| ID            | p\_des\[15:8] | p\_des\[7:0] | v\_des\[11:4] | v\_des\[3:0] \| Kp\[11:8] | Kp\[7:0] | Kd\[11:4] | Kd\[3:0] \| t\_ff\[11:8] | t\_ff\[7:0] |

Frame ID is equal to the configured CAN ID value.

* **p\_des**: position command
* **v\_des**: velocity command
* **Kp**: position proportional gain
* **Kd**: position derivative gain
* **t\_ff**: torque command

All parameters follow the mapping relationship described in the previous section. The ranges of **p\_des** **v\_des**, and **t\_ff** can be configured via the debugging tool. The range of **Kp** is \[0, 500], and the range of **Kd** is \[0, 5].

A standard CAN frame contains only 8 bytes. In MIT mode, the control command packs five parameters—Position, Velocity, Kp, Kd, and Torque—into these 8 bytes. Specifically:Position occupies 2 bytes (16 bits)、Velocity occupies 12 bits、Kp occupies 12 bits、Kd occupies 12 bits.

### Control Frame in Position-Velocity Mode <a href="#block-352d4c79856d80a8969fcfb9e6841ab3" id="block-352d4c79856d80a8969fcfb9e6841ab3"></a>

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

### Control Frame in Velocity Mode <a href="#block-c78c9ef61bc047cb9362a6531a41accd" id="block-c78c9ef61bc047cb9362a6531a41accd"></a>

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

## Instructions for Use <a href="#block-352d4c79856d8030b74ac338cecdcbe3" id="block-352d4c79856d8030b74ac338cecdcbe3"></a>

The motor has been calibrated and characterized before leaving the factory, and the parameters are stored inside the motor. Under normal conditions, it can be used directly without recalibration or re-characterization. The following provides the calibration procedure, which can be skipped if no abnormal conditions are present.

### CAN Configuration Commands <a href="#block-352d4c79856d807b9764c78cd3335c8c" id="block-352d4c79856d807b9764c78cd3335c8c"></a>

Motor parameters can be configured not only via the host computer (serial communication), but also through the CAN bus. In addition to basic parameter configuration, mode switching and baud rate modification are supported.

#### 1. Read Parameters <a href="#block-352d4c79856d8047b67ec31be9fc6cea" id="block-352d4c79856d8047b67ec31be9fc6cea"></a>

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4]          | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | -------------- | ----- | ----- | ----- |
| 0x7FF    | STD       | CANID\_L | CANID\_H | 0x33  | RID   | xx(don’t care) |       |       |       |

* **RID**: Register address (refer to Section 6).

After a successful read, the register data will be returned in the following format:

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID  | STD       | CANID\_L | CANID\_H | 0x33  | RID   | Data  |       |       |       |

The data is either floating-point or unsigned integer, occupying 32 bits (4 bytes). The lowest byte is D\[4], and the highest byte is D\[7]. The same applies hereinafter.

#### 2. Write Parameters <a href="#block-352d4c79856d80a195bcef93dfd8e671" id="block-352d4c79856d80a195bcef93dfd8e671"></a>

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

#### 3. Save Parameters <a href="#block-0df4eceb84b343c59784e165356de457" id="block-0df4eceb84b343c59784e165356de457"></a>

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

#### 4. Mode Switching <a href="#block-352d4c79856d80008123e1bf355be936" id="block-352d4c79856d80008123e1bf355be936"></a>

Multiple control modes are supported for switching between each other. The currently supported control modes are as follows:

| Code | Mode              |
| ---- | ----------------- |
| 1    | MIT               |
| 2    | Position-Velocity |
| 3    | Velocity          |

By modifying the mode register (**0x0A**), the control mode can be changed. During switching, the motor command values will first be cleared, including position, velocity, and in MIT mode also torque feedforward, Kp, and Kd.

When switching to position control mode, to avoid impact, it is recommended to first read the accurate position and perform switching at zero speed whenever possible.

Mode changes are not stored in flash and will be lost after power-off. After power-on, the mode defaults to the last mode stored in flash.

#### 5. Baud Rate Configuration <a href="#block-352d4c79856d80528024f0e563462819" id="block-352d4c79856d80528024f0e563462819"></a>

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

#### 6. Register Address Table <a href="#block-352d4c79856d8066a69dd96c6602fdc9" id="block-352d4c79856d8066a69dd96c6602fdc9"></a>

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

💡

**RW**: Read/Write

**RO:** Read Only

## **Characteristic Curves** <a href="#block-352d4c79856d8014b86fc642e44cecff" id="block-352d4c79856d8014b86fc642e44cecff"></a>

Test Environment: Room temperature at 25°C, laboratory conditions.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b245a771-595c-4a32-9370-a07e4eb7249b/image/w=1920,quality=90,fit=scale-down" alt="image" height="398.646875" width="724.8125">

## Characteristic Parameters <a href="#block-352d4c79856d80b3a438d7f94e146d14" id="block-352d4c79856d80b3a438d7f94e146d14"></a>

Please use the motor appropriately according to the following parameters.

| Motor Parameters            | Rated Voltage                      | 24V (driver supports 24–48V power supply)                                                                                                         |
| --------------------------- | ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
|                             | Rated Phase/Power Current          | 5A / 3.2A                                                                                                                                         |
|                             | Peak Phase/Power Current           | 13A / 7.5A                                                                                                                                        |
|                             | Rated Torque                       | 1.35Nm                                                                                                                                            |
|                             | Peak Torque                        | 5Nm                                                                                                                                               |
|                             | Rated Speed                        | 380rpm                                                                                                                                            |
|                             | No-load Maximum Speed              | 560rpm                                                                                                                                            |
| Motor Characteristic Values | Gear Ratio                         | 1:25                                                                                                                                              |
|                             | Pole Pairs                         | 7                                                                                                                                                 |
|                             | Phase Inductance                   | 75uH                                                                                                                                              |
|                             | Phase Resistance                   | 0.2915Ω                                                                                                                                           |
|                             | Maximum Radial Load (Dynamic Load) | 395N                                                                                                                                              |
| Structure & Weight          | Outer Diameter                     | Motor 28mm                                                                                                                                        |
|                             | Height                             | Motor 77.6mm                                                                                                                                      |
|                             | Motor Weight                       | Approx. 172.2g                                                                                                                                    |
| Encoder                     | Encoder Type                       | Incremental encoder                                                                                                                               |
| Communication               | Control Interface                  | CAN @ 1Mbps (Max), CAN FD @ 5Mbps (Max)                                                                                                           |
|                             | Tuning Interface                   | UART @ 921600bps                                                                                                                                  |
| Control & Protection        | Control Modes                      | MIT Mode                                                                                                                                          |
|                             |                                    | Velocity Mode                                                                                                                                     |
|                             |                                    | Position Mode                                                                                                                                     |
|                             | Protection                         | Protection temperature: 120℃. When exceeded, the motor will exit “Enabled Mode”.                                                                  |
|                             |                                    | Configurable based on application requirements. Recommended not to exceed 100℃. When exceeded, the motor will exit “Enabled Mode”.                |
|                             |                                    | Configurable based on application requirements. Recommended not to exceed 60V. When exceeded, the motor will exit “Enabled Mode”.                 |
|                             |                                    | If no CAN command is received within the configured period, the motor will automatically exit “Enabled Mode”.                                     |
|                             |                                    | Configurable based on application requirements. Recommended not to exceed 13A (phase current). When exceeded, the motor will exit “Enabled Mode”. |
|                             |                                    | If the supply voltage is lower than the set threshold, the motor will exit “Enabled Mode”. Minimum operating voltage is 15V.                      |
