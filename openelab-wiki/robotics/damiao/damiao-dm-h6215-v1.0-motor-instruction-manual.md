# DAMIAO DM-H6215 V1.0 Motor Instruction Manual

> DAMIAO DM-H6215 Motor User Guide

[**DAMIAO DM-H6215 Motor**DAMIAO DM-H6215: 2N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.openelab.io](https://openelab.io/products/damiao-brushless-servo-dm-h6215)

## Safety Precautions <a href="#block-350d4c79856d80209697c5b0d936b176" id="block-350d4c79856d80209697c5b0d936b176"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.

## **Motor Features** <a href="#block-350d4c79856d80a2b740e26c96503660" id="block-350d4c79856d80a2b740e26c96503660"></a>

1. Integrated design of motor and driver, compact structure, high integration.
2. Supports firmware upgrade.
3. Capable of providing feedback on motor speed, position, torque, and motor temperature via CAN bus.
4. Dual temperature protection function.
5. Low speed, high torque.

## **Packing List** <a href="#block-350d4c79856d80d68c28ef3a803855ad" id="block-350d4c79856d80d68c28ef3a803855ad"></a>

1. Motor (including driver, power interface with 240 mm cable outlet) × 1

## Interface & Pin Description <a href="#block-350d4c79856d802abdb6c1c8c2b249ec" id="block-350d4c79856d802abdb6c1c8c2b249ec"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f99b0cd0-d498-43e0-89ae-df7a06a555f1/image/w=1920,quality=90,fit=scale-down" alt="image" height="183.3186813186813" width="439">

| Interface / Pin No.        | Instruction                                                                                                                                                                                                                                                                         |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power connection interface | 1. Connect the power supply via the power cable with XT30(2+2)-F connector. The rated voltage is 24V, which powers the motor. 2. Connect to external control devices via the CAN communication terminal. It can receive CAN control commands and feedback motor status information. |

## Motor Dimensions and Mounting <a href="#block-350d4c79856d8020b03fe9d0af82f1cd" id="block-350d4c79856d8020b03fe9d0af82f1cd"></a>

Please install the motor onto the target equipment according to the motor mounting hole dimensions and layout.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/285e4546-ead7-4f4b-a0bc-31ffc60f25ef/image/w=1920,quality=90,fit=scale-down" alt="image" height="381.1825" width="560.5625">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a12e61f6-5920-43f0-8a7e-3831dbd77d55/image/w=1920,quality=90,fit=scale-down" alt="image" height="370.443678448914" width="560.5750122070312">

## Operating Modes <a href="#block-350d4c79856d806898a1e5d2d3d4b245" id="block-350d4c79856d806898a1e5d2d3d4b245"></a>

### MIT Mode <a href="#block-350d4c79856d80f69037fa3fc0f425f3" id="block-350d4c79856d80f69037fa3fc0f425f3"></a>

The MIT mode is compatible with the standard MIT control method, enabling seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX),CAN commands are converted into torque values. The torque is then used as the reference for current control. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Based on the MIT model, various control strategies can be derived. For instance, when kp=0 and kd ≠ 0, a constant rotational speed can be achieved by setting v\_des. When kp=0 and kd=0, a torque output is applied directly by setting t\_ff (feedforward torque).

💡

**Note:** When controlling position, kd must not be set to zero, as this may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-350d4c79856d8038a2d5deeafd880ade" id="block-350d4c79856d8038a2d5deeafd880ade"></a>

This mode uses three control loops: position, velocity, and current(torque). The position loop sets the target for the velocity loop. The velocity loop then sets the target for the current loop. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** represents the target position, while **v\_des** limits the maximum absolute velocity during motion.

When tuned using recommended parameters from the configuration tool, this mode provides high accuracy and smooth motion, at the cost of slower response time.

In addition to **v\_des**, acceleration and deceleration can also be configured. If additional oscillations occur, increasing acceleration/deceleration may help stabilize the system.

💡

**Note:**

1. After power-on, the motor position is fixed at 0.0 rad.
2. The units of **p\_des** and **v\_des** are rad and rad/s respectively, and the data type is float. The damping factor must be set to a non-zero positive number. Refer to the precautions for velocity mode for further details.

### Velocity Mode <a href="#block-350d4c79856d80f2904ad7615eef4c15" id="block-350d4c79856d80f2904ad7615eef4c15"></a>

This mode keeps the motor running at the target velocity. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

**Note:**

1. After power-on, the motor position is fixed at 0.0 rad.
2. The unit of v\_des is rad/s, and the data type is float. If you need to use the debugging assistant to automatically calculate parameters, you must set the damping factor to a non-zero positive number. Typically, the value ranges from 2.0 to 10.0. A damping factor that is too small will cause velocity oscillation and a large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting is 4.0.

## **Control Protocol Description** <a href="#block-350d4c79856d80d2aa7dc0c8f3d2709a" id="block-350d4c79856d80d2aa7dc0c8f3d2709a"></a>

The control uses the CAN standard frame format, with a default baud rate of 1 Mbps, which can be changed via commands. Based on functionality, frames can be divided into receive frames and feedback frames. Receive frames are the received control data used to issue commands to the motor. Feedback frames are the status data sent by the motor to the host controller. Depending on the selected mode of the motor, the definition of the receive frame format and the frame ID vary, but the feedback frames are the same across all modes.

### Feedback Frame <a href="#block-350d4c79856d80ae874fe20ed3920bdc" id="block-350d4c79856d80ae874fe20ed3920bdc"></a>

The feedback frame ID is set via the configuration tool (Master ID), with a default value of 0. It primarily reports the motor position, velocity, and torque with the frame format defined as follows:

| Feedback Message | D\[0]      | D\[1]      | D\[2]     | D\[3]      | D\[4]                 | D\[5]   | D\[6]  | D\[7]    |
| ---------------- | ---------- | ---------- | --------- | ---------- | --------------------- | ------- | ------ | -------- |
| MST\_ID          | ID\|ERR<<4 | POS\[15:8] | POS\[7:0] | VEL\[11:4] | VEL\[3:0] \| T\[11:8] | T\[7:0] | T\_MOS | T\_Rotor |

Where:

1. **ID:** Controller ID, using the lower 8 bits of CAN\_ID
2. **ERR :** Status code, with the following meanings
3. **0** – Disabled
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

### Control Frame in MIT Mode <a href="#block-350d4c79856d80989e4ce8fc34ffc5ea" id="block-350d4c79856d80989e4ce8fc34ffc5ea"></a>

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

### Control Frame in Position-Velocity Mode <a href="#block-350d4c79856d80cc908bebbcb03181f2" id="block-350d4c79856d80cc908bebbcb03181f2"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Desired position, float type, little-endian (low byte first, high byte last).
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID for sending commands here is 0x100 + ID. The speed reference is the maximum speed allowed during motor operation.

### Control Frame in Velocity Mode <a href="#block-350d4c79856d809dade4ff7110b32a94" id="block-350d4c79856d809dade4ff7110b32a94"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x200 + ID.

## **User Manual** <a href="#block-350d4c79856d80279efbdd60f6d6f4d4" id="block-350d4c79856d80279efbdd60f6d6f4d4"></a>

### Motor Calibration <a href="#block-436fdc4cc3644f6e8e93baf307bf37e8" id="block-436fdc4cc3644f6e8e93baf307bf37e8"></a>

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4]          | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | -------------- | ----- | ----- | ----- |
| 0x7FF    | STD       | CANID\_L | CANID\_H | 0x66  | 0x00  | xx(don't care) |       |       |       |

After calibration is completed, the motor will actively return a calibration completion status frame. Its frame format is as follows:

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| -------- | --------- | -------- | -------- | ----- | ----- |
| MST\_ID  | STD       | CANID\_L | CANID\_H | 0x66  | 0x01  |

### Parameter Calibration <a href="#block-40e3713f18f14ea8a561ceccf28b9334" id="block-40e3713f18f14ea8a561ceccf28b9334"></a>

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4]          | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | -------------- | ----- | ----- | ----- |
| 0x7FF    | STD       | CANID\_L | CANID\_H | 0x99  | 0x00  | xx(don't care) |       |       |       |

After parameter calibration is completed, the motor will actively return a calibration completion command. Its frame format is as follows:

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| -------- | --------- | -------- | -------- | ----- | ----- |
| MST\_ID  | STD       | CANID\_L | CANID\_H | 0x99  | 0x01  |

### Read Parameter <a href="#block-d21e30ef653f4ff49c9920095f2d10bd" id="block-d21e30ef653f4ff49c9920095f2d10bd"></a>

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4]          | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | -------------- | ----- | ----- | ----- |
| 0x7FF    | STD       | CANID\_L | CANID\_H | 0x33  | RID   | xx(don’t care) |       |       |       |

RID is the register address.

| Register Address | Variable   | Description                       | R/W | Data Type |
| ---------------- | ---------- | --------------------------------- | --- | --------- |
| 0                | UV\_Value  | Under-voltage protection value    | RW  | float     |
| 1                | KT\_Value  | Torque coefficient                | RW  | float     |
| 2                | OT\_Value  | Over-temperature protection value | RW  | float     |
| 3                | OC\_Value  | Over-current protection value     | RW  | float     |
| 4                | ACC        | Acceleration                      | RW  | float     |
| 5                | DEC        | Deceleration                      | RW  | float     |
| 6                | MAX\_SPD   | Maximum speed                     | RW  | float     |
| 7                | MST\_ID    | Feedback ID                       | RW  | uint32    |
| 8                | ESC\_ID    | Receive ID                        | RW  | uint32    |
| 9                | TIMEOUT    | Timeout alarm time                | RW  | uint32    |
| 10               | CTRL\_MODE | Control mode                      | RW  | uint32    |
| 11               | Damp       | Motor viscous damping coefficient | RO  | float     |
| 12               | Inertia    | Motor moment of inertia           | RO  | float     |
| 13               | Rsv1       | Reserved parameter 1              | RO  | uint32    |
| 14               | sw\_ver    | Software version number           | RO  | uint32    |
| 15               | Rsv2       | Reserved parameter 2              | RO  | uint32    |
| 16               | NPP        | Number of motor pole pairs        | RO  | uint32    |
| 17               | Rs         | Motor phase resistance            | RO  | float     |
| 18               | Ls         | Motor phase inductance            | RO  | float     |
| 19               | Flux       | Motor flux linkage value          | RO  | float     |
| 20               | Gr         | Gear reduction ratio              | RO  | float     |
| 21               | PMAX       | Position mapping range            | RW  | float     |
| 22               | VMAX       | Speed mapping range               | RW  | float     |
| 23               | TMAX       | Torque mapping range              | RW  | float     |
| 24               | I\_BW      | Current loop control bandwidth    | RW  | float     |
| 25               | KP\_ASR    | Speed loop Kp                     | RW  | float     |
| 26               | KI\_ASR    | Speed loop Ki                     | RW  | float     |
| 27               | KP\_APR    | Position loop Kp                  | RW  | float     |
| 28               | KI\_APR    | Position loop Ki                  | RW  | float     |
| 29               | OV\_Value  | Over-voltage protection value     | RW  | float     |
| 30               | GREF       | Gear torque efficiency            | RW  | float     |
| 31               | Beta       | Speed loop damping factor         | RW  | float     |
| 32               | V\_BW      | Speed loop filter bandwidth       | RW  | float     |
| 33               | IQ\_cl     | Current enhancement coefficient 1 | RW  | float     |
| 34               | VL\_cl     | Speed enhancement coefficient 1   | RW  | float     |
| 35               | can\_br    | CAN baud rate code                | RW  | uint32    |
| 36               | sub\_ver   | Sub-version number                | RO  | uint32    |
| 50               | u\_off     | U-phase offset                    | RO  | float     |
| 51               | v\_off     | V-phase offset                    | RO  | float     |
| 52               | k1         | Compensation factor 1             | RO  | float     |
| 53               | k2         | Compensation factor 2             | RO  | float     |
| 54               | e\_off     | Electrical angle offset           | RO  | float     |
| 55               | p\_m       | Motor position                    | RO  | float     |

After a successful read, the data from the register will be returned. The frame format is as follows:

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID  | STD       | CANID\_L | CANID\_H | 0x33  | RID   | Data  | Data  | Data  | Data  |

The data is of floating-point type, with D\[4] as the low byte and D\[7] as the high byte. The same applies below.

### Write Parameter <a href="#block-ada7b0c6a7ed4e74965abef56771e131" id="block-ada7b0c6a7ed4e74965abef56771e131"></a>

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | Data  |       |       |       |

RID is as described above. After a successful write, the written data will be returned, and the frame format is the same as the one sent.

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID  | STD       | CANID\_L | CANID\_H | 0x33  | RID   | Data  |       |       |       |

The written register data takes effect immediately but cannot be stored. **It will be lost after power-off. To retain the changes, the command to store parameters must be sent, which will write all modified parameters into the internal memory.**

### Save Parameters <a href="#block-442fee640e63464e9f3ae9a2a8baf67d" id="block-442fee640e63464e9f3ae9a2a8baf67d"></a>

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4]           | D\[5] | D\[6] | D\[7] |
| -------- | --------- | -------- | -------- | ----- | ----- | --------------- | ----- | ----- | ----- |
| 0x7FF    | STD       | CANID\_L | CANID\_H | 0xAA  | RID   | xx (don’t care) |       |       |       |

After a successful write, the return format is as follows:

| Frame ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] |
| -------- | --------- | -------- | -------- | ----- | ----- |
| MST\_ID  | STD       | CANID\_L | CANID\_H | 0xAA  | 01    |

### Mode Switching <a href="#block-350d4c79856d80bfba45f601aa416340" id="block-350d4c79856d80bfba45f601aa416340"></a>

Multiple control modes are supported and can be switched as follows:

| Code/ID | Mode              |
| ------- | ----------------- |
| 1       | MIT               |
| 2       | Position-Velocity |
| 3       | Velocity          |

The mode can be changed by modifying the mode register (0x0A). During switching, the motor resets all command values to zero, including position, velocity, and torque feed-forward, KP, and KD in MIT mode.

When switching from one mode to position control mode, to prevent impact, it is recommended to first read the precise position before considering the switch, and to perform the switch when the motor speed is zero.

After the mode is changed, it will not be stored in flash and will be lost after power-off. Upon re-powering, the control mode will be set to the mode last stored in flash.

### Baud Rate Modification <a href="#block-c2088fa5adb040cabcd822e7d507194c" id="block-c2088fa5adb040cabcd822e7d507194c"></a>

Specific baud rate modification is supported. The currently supported baud rates are as follows:

| Code | Baud Rate |
| ---- | --------- |
| 0    | 125K      |
| 1    | 200K      |
| 2    | 250K      |
| 3    | 500K      |
| 4    | 1M        |

After the baud rate is modified, the CAN bus will automatically reinitialize and feedback data at the new baud rate.

## **Characteristic Parameters** <a href="#block-361d4c79856d80e0a2ffd2e48c5f804a" id="block-361d4c79856d80e0a2ffd2e48c5f804a"></a>

Please use the motor properly according to the following parameters.

| Type                        | Characteristic Parameters    | Description                                                                                                                                                                                       |
| --------------------------- | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor parameters            | Rated Voltage                | 24V                                                                                                                                                                                               |
|                             | Rated Phase / Supply Current | 2.5A                                                                                                                                                                                              |
|                             | Peak Phase / Supply Current  | 4.3A                                                                                                                                                                                              |
|                             | Rated Torque                 | 1NM                                                                                                                                                                                               |
|                             | Peak Torque                  | 2NM                                                                                                                                                                                               |
|                             | Rated speed                  | 120rpm                                                                                                                                                                                            |
|                             | Maximum No-Load Speed        | 320rpm                                                                                                                                                                                            |
| Motor Characteristic Values | Reduction Ratio              | 1: 1                                                                                                                                                                                              |
|                             | Number of Pole Pairs         | 14                                                                                                                                                                                                |
|                             | Phase Inductance             | 2000uH                                                                                                                                                                                            |
|                             | Phase Resistance             | 2.5Ω                                                                                                                                                                                              |
| Structure and Weight        | Outer Diameter               | 68mm                                                                                                                                                                                              |
|                             | Height                       | 44.5mm                                                                                                                                                                                            |
|                             | Motor Weight                 | 360g                                                                                                                                                                                              |
| Encoder                     | Encoder Type                 | Hall                                                                                                                                                                                              |
| Communication Method        | Control interface type       | CAN                                                                                                                                                                                               |
|                             | Parameter Tuning Interface   | CAN                                                                                                                                                                                               |
| Control and Protection      | Control Mode                 | MIT Mode                                                                                                                                                                                          |
|                             |                              | Velocity Mode                                                                                                                                                                                     |
|                             |                              | Position Mode                                                                                                                                                                                     |
|                             | Protection                   | Driver over-temperature protection: Protection temperature: 120°C. If over-temperature occurs, the motor will exit the "Enable Mode".                                                             |
|                             |                              | Motor over-temperature protection: set according to usage requirements. It is recommended not to exceed 100°C. If over-temperature occurs, the motor will exit the "Enable Mode".                 |
|                             |                              | Motor overvoltage protection: set according to usage requirements. It is recommended not to exceed 32 V. If overvoltage occurs, the motor will exit the "Enable Mode".                            |
|                             |                              | Communication loss protection: If no CAN command is received within the set period, the motor will automatically exit the "Enable Mode".                                                          |
|                             |                              | Motor overcurrent protection: set according to usage requirements. It is recommended not to exceed 9.8 A. If overcurrent occurs, the motor will exit the "Enable Mode".                           |
|                             |                              | Motor undervoltage protection: If the power supply voltage falls below the set value, the motor will exit the "Enable Mode". It is recommended that the power supply voltage not fall below 15 V. |
