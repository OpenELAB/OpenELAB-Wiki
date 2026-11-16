# DAMIAO DM-G6220 Motor Instruction Manual

> DAMIAO DM-G6220 Motor User Guide

[**DAMIAO DM-G6220 Motor**DAMIAO DM-G6220: 1.3N·m rated, 2.7N·m peak torque. Hollow-shaft servo motor with built-in drive & encoder. For quad/humanoid robots & exoskeletons.openelab.io](https://openelab.io/products/damiao-brushless-servo-dm-g6220)

## Safety Precautions <a href="#block-34ed4c79856d819c9a87d20224da74a9" id="block-34ed4c79856d819c9a87d20224da74a9"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.

## **Motor Features** <a href="#block-34ed4c79856d80229cbeebb8676b2703" id="block-34ed4c79856d80229cbeebb8676b2703"></a>

1. The motor features a hollow design, which facilitates cable routing and reduces the weight of the unit.
2. Integrated design of motor and driver, compact structure, and high integration.
3. Supports host computer visual debugging and firmware upgrade.
4. Provides real-time feedback of motor Velocity, position, torque, and temperature via CAN bus.
5. Features dual temperature protection mechanisms.

For the 48V version, at a constant speed of 120 rpm and room temperature of 25°C, the measured performance curve is shown below:

## **Packing List** <a href="#block-34ed4c79856d80f4a8eccfe8be812c4f" id="block-34ed4c79856d80f4a8eccfe8be812c4f"></a>

1. Motor (with integrated driver) ×1
2. Power cable: XT30 male-to-female cable (200 mm) × 1
3. CAN interface: GH1.25 2-Pin Cable (300mm，Different planes) × 1
4. Debug serial cable: GH1.25 3-pin cable (300mm，Different planes) × 1

## **Interface & Pin Description** <a href="#block-34ed4c79856d80ba8503f256e8eabb6e" id="block-34ed4c79856d80ba8503f256e8eabb6e"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c97713d6-062a-472b-bc29-a02caf51f32f/image/w=1920,quality=90,fit=scale-down" alt="image" height="353.7798570736434" width="713.0875244140625">

| Specific Name - No. | Description                                                                                                                |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Power Interface-1   | Connect the power supply using an XT30 male-to-female power cable. The rated voltage is 24V, supplying power to the motor. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7bb0bd4e-0f83-4fc8-82d0-b5c97f965be5/image/w=1920,quality=90,fit=scale-down" alt="image" height="283.5206403655761" width="606.9874877929688">

| Specific Name - No. | Description                                                                                                                                     |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| CAN interface-1     | Connect to external control devices via CAN communication terminals. It can receive CAN control commands and feedback motor status information. |
| CAN interface-2     |                                                                                                                                                 |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2c2a2c2c-3b79-42a8-a40b-b232b8dc17eb/image/w=1920,quality=90,fit=scale-down" alt="image" height="315.27277295834546" width="518.9874877929688">

| Specific Name - No.           | Description                                                                                                                                                                                                          |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debug Serial Interface(Port3) | Connect to a PC via a GH1.25 3-pin cable using a USB-to-CAN debugging tool (or a generic USB-to-UART module). Use the Damiao Technology Debug Assistant to configure motor parameters and perform firmware upgrades. |

## Motor Dimensions and Mounting <a href="#block-34ed4c79856d80c1b251e70b5e8c4da3" id="block-34ed4c79856d80c1b251e70b5e8c4da3"></a>

Please install the motor onto the target equipment according to the motor mounting hole dimensions and layout.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f1254278-3a6e-4317-aba6-78bdbeb8299f/image/w=1920,quality=90,fit=scale-down" alt="image" height="463.17614026063103" width="743.734375">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fd08266b-23ec-4583-8d18-d894abb58ef4/image/w=1920,quality=90,fit=scale-down" alt="image" height="373.8569392296092" width="492.9875183105469">

## Operating Modes <a href="#block-34ed4c79856d80d09e8bccb72fafa376" id="block-34ed4c79856d80d09e8bccb72fafa376"></a>

### MIT Mode <a href="#block-34ed4c79856d80fc9b29f70b0417b43c" id="block-34ed4c79856d80fc9b29f70b0417b43c"></a>

The MIT mode is compatible with the standard MIT control method, enabling seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX).

CAN commands are converted into torque values. The torque is then used as the reference for current control. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="262.11989574283234" width="754.25">

Based on the MIT model, various control strategies can be derived. For instance, when kp = 0 and kd ≠ 0, a constant rotational speed can be achieved by setting v\_des. When kp = 0 and kd = 0, a torque output is applied directly by setting t\_ff (feedforward torque).

💡

**Note:** When controlling position, kd must not be set to zero, as this may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-34ed4c79856d80bca6bcc8953ea8f113" id="block-34ed4c79856d80bca6bcc8953ea8f113"></a>

This mode uses three control loops: position, velocity, and current(torque). The position loop sets the target for the velocity loop. The velocity loop then sets the target for the current loop. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="228.67546063651594" width="754.25">

**p\_des** represents the target position, while **v\_des** limits the maximum absolute velocity during motion.

When tuned using recommended parameters from the configuration tool, this mode provides high accuracy and smooth motion, at the cost of slower response time.

In addition to **v\_des**, acceleration and deceleration can also be configured. If additional oscillations occur, increasing acceleration/deceleration may help stabilize the system.

💡

**Note:** The units of p\_des and v\_des are rad and rad/s respectively, and both are of type float. The damping factor must be set to a non-zero positive value. Refer to the notes for velocity mode.

### Velocity Mode <a href="#block-34ed4c79856d8062aa2dd6f6d6ee4004" id="block-34ed4c79856d8062aa2dd6f6d6ee4004"></a>

This mode keeps the motor running at the target velocity. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

Note: The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

## Usage <a href="#block-34ed4c79856d8088aa4bcc806d909cfe" id="block-34ed4c79856d8088aa4bcc806d909cfe"></a>

The control uses the CAN standard frame format with a fixed baud rate of 1 Mbps. Based on functionality, the frames can be divided into receive frames and feedback frames. The receive frames are the control data received, used to achieve command control of the motor. The feedback frames are the motor's status data sent by the motor to the higher-level controller. Depending on the selected mode of the motor, the frame format definition and frame ID of the receive frames vary, but the feedback frames are the same across all modes.

### Feedback Frame <a href="#block-34ed4c79856d8077a6cae2301b8cfada" id="block-34ed4c79856d8077a6cae2301b8cfada"></a>

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

### Control Frame in MIT Mode <a href="#block-34ed4c79856d8098a4bde6c6488f2a25" id="block-34ed4c79856d8098a4bde6c6488f2a25"></a>

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

### Control Frame in Position-Velocity Mode <a href="#block-34ed4c79856d80ca8c95fa82c702f6a1" id="block-34ed4c79856d80ca8c95fa82c702f6a1"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Position command, float, little-endian (low byte first, high byte last)
* **v\_des**: Velocity command, float, little-endian (low byte first, high byte last)

In this mode, the CAN ID used to send commands is 0x100 + ID. The velocity command (v\_des) defines the maximum speed during the movement to the target position—i.e., the speed during the constant-velocity phase.

### Control Frame in Velocity Mode <a href="#block-34ed4c79856d802ab666e9ae1815ca78" id="block-34ed4c79856d802ab666e9ae1815ca78"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Velocity reference value, floating point, little-endian (low byte first, high byte last).

The CAN ID for sending the command here is 0x200 + ID.

## Specifications <a href="#block-34ed4c79856d80f69c96f359db501e78" id="block-34ed4c79856d80f69c96f359db501e78"></a>

Please use the motor properly according to the following parameters.

| Type                        | Characteristic Parameters    | Description                                                                                                                                                                                        |
| --------------------------- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor parameters            | Rated Voltage                | 24V                                                                                                                                                                                                |
|                             | Rated Phase / Supply Current | 2.3A                                                                                                                                                                                               |
|                             | Peak Phase / Supply Current  | 5.3A                                                                                                                                                                                               |
|                             | Rated Torque                 | 1.3NM                                                                                                                                                                                              |
|                             | Peak Torque                  | 2.7NM                                                                                                                                                                                              |
|                             | Rated speed                  | 110rpm                                                                                                                                                                                             |
|                             | Maximum No-Load Speed        | 300rpm                                                                                                                                                                                             |
| Motor Characteristic Values | Reduction Ratio              | 1: 1                                                                                                                                                                                               |
|                             | Number of Pole Pairs         | 14                                                                                                                                                                                                 |
|                             | Phase Inductance             | 2900uh                                                                                                                                                                                             |
|                             | Phase Resistance             | 3.5Ω                                                                                                                                                                                               |
| Structure and Weight        | Outer Diameter               | 68mm                                                                                                                                                                                               |
|                             | Height                       | 41.5mm                                                                                                                                                                                             |
|                             | Motor Weight                 | 493.5g                                                                                                                                                                                             |
| Encoder                     | Encoder Type                 | Magnetic Encoder                                                                                                                                                                                   |
| Communication Method        | Control interface type       | CAN@1Mbps                                                                                                                                                                                          |
|                             | Parameter Tuning Interface   | UART@921600bps                                                                                                                                                                                     |
| Control and Protection      | Control Mode                 | MIT Mode                                                                                                                                                                                           |
|                             |                              | Velocity Mode                                                                                                                                                                                      |
|                             |                              | Position Mode                                                                                                                                                                                      |
|                             | Protection                   | Driver over-temperature protection: Protection temperature: 120°C. If over-temperature occurs, the motor will exit the "Enable Mode".                                                              |
|                             |                              | Motor over-temperature protection: set according to usage requirements. It is recommended not to exceed 100°C. If over-temperature occurs, the motor will exit the "Enable Mode".                  |
|                             |                              | Motor overvoltage protection: set according to usage requirements. It is recommended not to exceed 32 V. If overvoltage occurs, the motor will exit the "Enable Mode".                             |
|                             |                              | Communication loss protection: If no CAN command is received within the set period, the motor will automatically exit the "Enable Mode".                                                           |
|                             |                              | Motor overcurrent protection: set according to usage requirements. It is recommended not to exceed 9.8 A. If overcurrent occurs, the motor will exit the "Enable Mode".                            |
|                             |                              | Motor under-voltage protection: If the power supply voltage falls below the set value, the motor will exit the "Enable Mode". It is recommended that the power supply voltage not fall below 15 V. |

## Host Computer Guide <a href="#block-34ed4c79856d80a39d84de0b88a32400" id="block-34ed4c79856d80a39d84de0b88a32400"></a>

[DAMIAO Host Computer User Manual](https://wiki.openelab.io/damiao/damiao-host-computer-user-manual)<br>
