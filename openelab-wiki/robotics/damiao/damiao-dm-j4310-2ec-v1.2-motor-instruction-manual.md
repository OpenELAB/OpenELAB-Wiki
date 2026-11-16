# DAMIAO DM-J4310-2EC V1.2 Motor Instruction Manual

> DAMIAO DM-J4310-2EC V1.2 Motor User Guide

[**DAMIAO DM-J4310-2EC Motor**DAMIAO DM-J4310-2EC: 7N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons. Motor for OpenArm.openelab.io](https://openelab.io/products/damiao-brushless-servo-dm-j4310)

## Safety Precautions <a href="#block-348d4c79856d80efb957c85781a8628e" id="block-348d4c79856d80efb957c85781a8628e"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.

## **Motor Features** <a href="#block-33fd4c79856d80cab383f7b78bc48ae3" id="block-33fd4c79856d80cab383f7b78bc48ae3"></a>

1. Dual encoders provide single-turn absolute position feedback at the output shaft, ensuring position information is retained even after power loss.
2. Integrated motor and driver design offers compact structure with high integration.
3. Supports PC-based configuration, monitoring, and firmware upgrades.
4. Provides real-time feedback of motor Velocity, position, torque, and temperature via CAN bus.
5. Features dual temperature protection mechanisms.
6. Supports trapezoidal acceleration and deceleration profiles in position mode.

## **Naming Specification** <a href="#block-33fd4c79856d802a813ed9738747894d" id="block-33fd4c79856d802a813ed9738747894d"></a>

**For example：DM - J4310 X - 2EC VX.X (48V)**

| DM    | DAMIAO Technology                                                                                                                                                                                                                                                                                                                                      |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| J     | **J**：Joint Motor Series **S：**&#x44;iscrete Motor Series                                                                                                                                                                                                                                                                                              |
| 43    | Stator Diameter 35、43、60、62、80、100（mm）                                                                                                                                                                                                                                                                                                                 |
| 10    | Reduction Ratio 06、07、09、10、19、40、48                                                                                                                                                                                                                                                                                                                   |
| X -   | Output Bearing /Special Versions X represents letters such as L,P,etc **-By default：** Deep Groove Ball Bearing. **-P：** Crossed Roller Bearing. **-L：** Lite version (not related to bearing type).                                                                                                                                                   |
| 2EC   | Encoder **-By default：** Represents a single encoder. **-1EC：** Single encoder, CAN communication. **-2EC：** Dual encoder (single-turn absolute position on the output shaft),CAN communication. **-1EE：** Single encoder, EtherCAT communication. **-2EE：** Dual encoder (single-turn absolute position on the output shaft), EtherCAT communication. |
| VX.X  | Motor Version **VX.X：** Upgrade version(X=0-9),Version omitted=V1.0                                                                                                                                                                                                                                                                                    |
| （48V） | Driver Rated Voltage **-By default：**&#x32;4V drive voltage **-48V ：**&#x34;8V drive voltage                                                                                                                                                                                                                                                           |

## Specifications <a href="#block-33fd4c79856d809981cfc2139cb87954" id="block-33fd4c79856d809981cfc2139cb87954"></a>

Please operate the motor within the specifications listed below.

| Type                        | Characteristic Parameters    | DM-J4310-2EC V1.2（24V）                                                                                                        | DM-J4310-2EC V1.2（48V）                                                                                                        |
| --------------------------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Motor parameters            | Rated Voltage                | 24V                                                                                                                           | 48V                                                                                                                           |
|                             | Rated Phase / Supply Current | 4.9A/3.1A@24V                                                                                                                 | 4.8A/1.6A@48V                                                                                                                 |
|                             | Peak Phase / Supply Current  | 20A/16.44A@24V                                                                                                                | 20A/12.8A@48V                                                                                                                 |
|                             | Rated Torque                 | 3.5NM                                                                                                                         | 3.5NM                                                                                                                         |
|                             | Peak Torque                  | 12.5NM                                                                                                                        | 12.5NM                                                                                                                        |
|                             | Rated speed                  | 120rpm                                                                                                                        | 120rpm                                                                                                                        |
|                             | Maximum No-Load Speed        | 200rpm                                                                                                                        | 450rpm                                                                                                                        |
| Motor Characteristic Values | Reduction Ratio              | 10: 1                                                                                                                         | 10: 1                                                                                                                         |
|                             | Number of Pole Pairs         | 14                                                                                                                            | 14                                                                                                                            |
|                             | Phase Inductance             | 320uH                                                                                                                         | 320uH                                                                                                                         |
|                             | Phase Resistance             | 580mΩ                                                                                                                         | 580mΩ                                                                                                                         |
| Structure and Weight        | Outer Diameter               | 57mm                                                                                                                          | 57mm                                                                                                                          |
|                             | Height                       | 46mm                                                                                                                          | 46mm                                                                                                                          |
|                             | Motor Weight                 | 325g                                                                                                                          | 325g                                                                                                                          |
| Encoder                     | Encoder Resolution           | 16bit                                                                                                                         | 16bit                                                                                                                         |
|                             | Number of Encoders           | 2                                                                                                                             | 2                                                                                                                             |
|                             | Encoder Type                 | Magnetic Encoder (Single-Turn)                                                                                                | Magnetic Encoder (Single-Turn)                                                                                                |
| Communication Method        | Control interface type       | CAN@1Mbps                                                                                                                     | CAN@1Mbps                                                                                                                     |
|                             | Parameter Tuning Interface   | UART@921600bps                                                                                                                | UART@921600bps                                                                                                                |
| Control and Protection      | Control Mode                 | MIT Mode                                                                                                                      | MIT Mode                                                                                                                      |
|                             |                              | Velocity Mode                                                                                                                 | Velocity Mode                                                                                                                 |
|                             |                              | Position Mode                                                                                                                 | Position Mode                                                                                                                 |
|                             |                              | Force-Position Hybrid Control Mode                                                                                            | Force-Position Hybrid Control Mode                                                                                            |
|                             | Protection                   | Drive over-temperature protection: shutdown at 120° C; the motor exits Enable Mode when triggered.                            | Drive over-temperature protection: shutdown at 120° C; the motor exits Enable Mode when triggered.                            |
|                             |                              | Motor over-temperature protection (configurable, recommended ≤ 100° C); the motor exits Enable Mode when triggered.           | Motor over-temperature protection (configurable, recommended ≤ 100° C); the motor exits Enable Mode when triggered.           |
|                             |                              | Over-voltage protection(configurable, recommended ≤ 32V); exits Enable Mode when triggered.                                   | Over-voltage protection(configurable, recommended ≤ 60V); exits Enable Mode when triggered.                                   |
|                             |                              | Communication Loss Protection: the motor exits Enable Mode if no CAN command is received within the specified timeout period. | Communication Loss Protection: the motor exits Enable Mode if no CAN command is received within the specified timeout period. |
|                             |                              | Over-current protection (configurable, recommended ≤ 9.8A); exits Enable Mode when triggered.                                 | Over-current protection (configurable, recommended ≤ 9.8A); exits Enable Mode when triggered.                                 |
|                             |                              | Under-voltage protection: the motor exits Enable Mode if supply voltage falls below the threshold (recommended ≥ 15V).        | Under-voltage protection: the motor exits Enable Mode if supply voltage falls below the threshold (recommended ≥ 15V).        |

### **Operating Voltage** <a href="#block-33fd4c79856d808eb447e5357d32956a" id="block-33fd4c79856d808eb447e5357d32956a"></a>

The operating voltage range for the 24V motor driver is 24V–28V, with a minimum operating voltage of 20V and a maximum of 28V.

For the 48V motor driver, the operating voltage range is 24V–48V, with a minimum operating voltage of 20V and a maximum of 58V.Hot-plugging is recommended to be avoided when the voltage exceeds 36V.

### **Maximum Phase Current** <a href="#block-33fd4c79856d8036af67cb428a31d98b" id="block-33fd4c79856d8036af67cb428a31d98b"></a>

💡

**Correction:** The baud rate in the communication settings in the PC software shown in the screenshot below has been updated to 921600.

The maximum phase current of the driver can be obtained from the startup serial output:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/83385d1f-afef-42a2-8d9b-8a390804e8d1/image/w=1920,quality=90,fit=scale-down" alt="image" height="448.11161118993215" width="737.5750122070312">

The maximum phase current percentage can be limited by setting a percentage in the configuration tool. The default value is 0.8 (i.e., 80% of the measurable maximum current). It is recommended that this value not exceed 98%.

### **Maximum Rotational Speed** <a href="#block-340d4c79856d808eb756cd942bdc2cef" id="block-340d4c79856d808eb756cd942bdc2cef"></a>

The maximum rotational speed is limited by multiple factors, including the power supply voltage (VBUS), rotor flux linkage (ψf), and gear ratio (GR). An upper limit can typically be calculated using the following formula:

VMAX(rad/s)=0.57735∗VBUSNpp×GR×ψf(rad/s)VMAX​(rad/s)=0.57735∗Npp​×GR×ψf​VBUS​​(rad/s)

where VBUS is the supply voltage, Npp is the number of pole pairs, and ψf is the rotor flux linkage.

### **Torque Constant** <a href="#block-340d4c79856d800fb62cc7c233c9899e" id="block-340d4c79856d800fb62cc7c233c9899e"></a>

The torque constant of the motor can be considered constant within its rated range. With a gearbox, it can be calculated using the following formula:

Kt=1.5∗Npp∗ψf∗GR∗GREFKt​=1.5∗Npp​∗ψf​∗GR∗GREF

Where Npp is the number of pole pairs, ψf is the rotor flux linkage, GR is the gear ratio, and GREF is the gearbox torque transmission coefficient.

## Torque–Speed (T–N) Curve <a href="#block-340d4c79856d8080b8bbcbeec0c927a3" id="block-340d4c79856d8080b8bbcbeec0c927a3"></a>

The following curve shows the measured performance at 24 V, a constant speed of 36 rpm, and an ambient temperature of 25° C:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c2715ff5-7f23-4f01-a4d7-6f4e34b08e01/4310_/w=1920,quality=90,fit=scale-down" alt="image" height="1800" width="3000">

## **Packing List** <a href="#block-340d4c79856d8012a8d7ed584044d0ad" id="block-340d4c79856d8012a8d7ed584044d0ad"></a>

1. Motor (with integrated driver) ×1
2. Power cable (with CAN interface) : XT30(2+2)-F connector, single-ended(100mm)×1
3. Debug serial cable: GH1.25 3-pin cable (reverse-side connector, 300mm) ×1

## Interface & Pin Description <a href="#block-340d4c79856d8034ae5cd98009f8e1ab" id="block-340d4c79856d8034ae5cd98009f8e1ab"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0164321b-0442-4465-bb6a-72a583ed4f34/image/w=1920,quality=90,fit=scale-down" alt="image" height="243.49920760697304" width="528">

| Interface / Pin No.                   | Instruction                                                                                                                                                                                                                                                                                                                                                                      |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power Interface-1(with CAN interface) | 1. Connect the power supply via the XT30(2+2)-F cable. The rated voltage is 24 V. 2. Connect external controller via the CAN communication interface to receive CAN control commands and transmit motor status feedback. 3. The motor features two power interfaces. Either interface can be used independently , or multiple motors can be daisy-chained for convenient wiring. |
| Power Interface-2(with CAN interface) | 1. Connect the power supply via the XT30(2+2)-F cable. The rated voltage is 24 V. 2. Connect external controller via the CAN communication interface to receive CAN control commands and transmit motor status feedback. 3. The motor features two power interfaces. Either interface can be used independently , or multiple motors can be daisy-chained for convenient wiring. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a753714f-ba5c-4b2f-bdb2-df5dff644028/image/w=1920,quality=90,fit=scale-down" alt="image" height="307.13286713286715" width="576">

| Interface / Pin No.            | Instruction                                                                                                                                         |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debug Serial Interface(Port 3) | Connect to a PC via the GH1.25 3-pin cable using a USB-to-CAN adapter (or USB-to serial module) for parameters configuration and firmware upgrades. |

## Motor Dimensions and Mounting <a href="#block-340d4c79856d80bf9fbef7a52f0eeecb" id="block-340d4c79856d80bf9fbef7a52f0eeecb"></a>

Please install the motor onto the target equipment according to the motor mounting hole dimensions and layout.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/577602c9-e3c2-45ea-b0c4-e29fd1e1dad7/image/w=1920,quality=90,fit=scale-down" alt="image" height="1096" width="2304">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5bf37ca8-46a7-4f2a-a76d-1333461cec96/image/w=1920,quality=90,fit=scale-down" alt="image" height="1002" width="2238">

## **Motor wiring diagram** <a href="#block-340d4c79856d80faab9fca3b89ae3c75" id="block-340d4c79856d80faab9fca3b89ae3c75"></a>

### **Main wiring diagram** <a href="#block-340d4c79856d803eadb4f894c04a631e" id="block-340d4c79856d803eadb4f894c04a631e"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f0477e99-400f-4e3c-95a2-05b692417594/image/w=1920,quality=90,fit=scale-down" alt="image" height="559.8540034280118" width="737.5625">

### **USB-to-CAN module wiring diagram** <a href="#block-340d4c79856d8010844ae874c027b60d" id="block-340d4c79856d8010844ae874c027b60d"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/dc24b1ef-084e-4313-924f-347c56ae6c8e/image/w=1920,quality=90,fit=scale-down" alt="image" height="398.86204722496007" width="629.9874877929688">

### **Power adapter board wiring diagram** <a href="#block-340d4c79856d80c2bdcac128218e51d8" id="block-340d4c79856d80c2bdcac128218e51d8"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b4f24767-f384-4700-bd4f-a6d3d03ead01/image/w=1920,quality=90,fit=scale-down" alt="image" height="521.1329746198294" width="737.5750122070312">

## LED Status <a href="#block-340d4c79856d804c9d6ed09d5e84e0d2" id="block-340d4c79856d804c9d6ed09d5e84e0d2"></a>

| Normal Status | Solid Green  | Enable Mode (ERR = 1), normal operation                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|               | Solid Red    | Disable Mode (ERR = 0)（Default state after power-on）                                                                                                                                                                                                                                                                                                                                                                                                     |
| Fault Status  | Flashing Red | Fault codes and fault conditions: **3** – Output shaft calibration error; **4** – Sensor output error; **5** – Motor encoder calibration error; **8** – Over-voltage; **9** – Under-voltage; **A** – Over-current; **B** – MOS over-temperature; **C** – Motor winding over-temperature; **D** – Communication loss; **E** – Overload; Fault conditions can be identified via the feedback frames or displayed in the the Damiao configuration software. |

## Operating Modes <a href="#block-340d4c79856d8080b6acd7633d1ff1d8" id="block-340d4c79856d8080b6acd7633d1ff1d8"></a>

### MIT Mode <a href="#block-340d4c79856d80bd824dc171c6ea6f9b" id="block-340d4c79856d80bd824dc171c6ea6f9b"></a>

The MIT mode is compatible with the standard MIT control method, enabling seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX).

CAN commands are converted into torque values. The torque is then used as the reference for current control. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Based on the MIT model, various control strategies can be derived. For instance, when kp=0 and kd ≠ 0, a constant rotational speed can be achieved by setting v\_des. When kp=0 and kd=0, a torque output is applied directly by setting t\_ff (feedforward torque).

💡

**Note:** When controlling position, kd must not be set to zero, as this may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-340d4c79856d808faa9ee67aa92ab04f" id="block-340d4c79856d808faa9ee67aa92ab04f"></a>

This mode uses three control loops: position, velocity, and current(torque). The position loop sets the target for the velocity loop. The velocity loop then sets the target for the current loop. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** represents the target position, while **v\_des** limits the maximum absolute velocity during motion.

When tuned using recommended parameters from the configuration tool, this mode provides high accuracy and smooth motion, at the cost of slower response time.

In addition to **v\_des**, acceleration and deceleration can also be configured. If additional oscillations occur, increasing acceleration/deceleration may help stabilize the system.

💡

**Note:** The units of p\_des and v\_des are rad and rad/s respectively, and both are of type float. The damping factor must be set to a non-zero positive value.Refer to the notes for velocity mode.

### Velocity Mode <a href="#block-340d4c79856d80aa83d5dd5c2c7d5b4e" id="block-340d4c79856d80aa83d5dd5c2c7d5b4e"></a>

This mode keeps the motor running at the target velocity. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

**Note:** The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

### **Force-Position Hybrid Mode** <a href="#block-340d4c79856d805b963df8b6d61d1da2" id="block-340d4c79856d805b963df8b6d61d1da2"></a>

The force-position hybrid control mode is based on position-velocity control, with additional torque adjustment. Allows control of both position and output torque at the same time. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4876b2d6-b47f-47a9-9dc7-20de651abc12/29e55681073b4ab3acd8adaf9b17c02e/w=1920,quality=90,fit=scale-down" alt="在这里插入图片描述" height="1000" width="1000">

A current command saturation stage is added after the velocity loop output command. This limits the current loop reference within the specified range.

### **Mode Switching** <a href="#block-340d4c79856d809d974be1158ddb479d" id="block-340d4c79856d809d974be1158ddb479d"></a>

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

## **CAN communication** <a href="#block-340d4c79856d80929d7fe83a052bc4ea" id="block-340d4c79856d80929d7fe83a052bc4ea"></a>

After calibration, parameter identification, and parameter configuration are completed, the motor is ready for operation.

Control is performed using CAN standard frames (STD). The default baud rate is 1 Mbps, which can be modified via commands. Refer to the "CAN Baud Rate" section for details.

**Frame Types:**

CAN communication is divided into two types:

* Command Frames

Frames received by the driver, used to send control commands to the motor.

* Feedback Frames

Frames transmitted by the driver to the upper-level controller, containing motor status data.

**Feedback Mechanism:**

Feedback operates in a request-response manner. When the driver receives a CAN frame whose ID matches the configured motor CAN ID:

1. The lower 8 bits are used for validation.
2. The upper 3 bits are ignored.

Once a match is detected, the driver will transmit the current motor status to the CAN bus.

**Frame Format:**

The command frame format and frame ID vary depending on the selected control mode. The feedback frame format remains the same across all control modes.

### **CAN Baud Rate Configuration** <a href="#block-340d4c79856d80839b57e7b7aab96797" id="block-340d4c79856d80839b57e7b7aab96797"></a>

The CAN baud rate can be configured in two ways:

1. Configuration via Serial Interface,.
2. The baud rate can be set through the host PC software via the serial interface.
3. Select the desired baud rate.
4. Click "Write Parameters" to apply.
5. After the setting is successfully written:
6. The motor will automatically reboot.
7. The baud rate will be stored in the driver.
8. The setting will persist after power cycling.
9. Configuration via CAN Interface The baud rate can also be modified via the CAN interface by writing to the corresponding baud rate register. See "**CAN Baud Rate**" in this chapter for details.

💡

**Note:** When modifying the baud rate via CAN, the operation may fail if multiple devices are present on the bus.

Use this method with caution. It is strongly recommended to configure the baud rate before connecting multiple devices.

### Feedback Frame <a href="#block-340d4c79856d80abba03c465ad8333d3" id="block-340d4c79856d80abba03c465ad8333d3"></a>

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

### Control Frame in MIT Mode <a href="#block-340d4c79856d80b7b32ac8280ad816f6" id="block-340d4c79856d80b7b32ac8280ad816f6"></a>

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

### Control Frame in Position-Velocity Mode <a href="#block-340d4c79856d80de8fdef1db31ed8d24" id="block-340d4c79856d80de8fdef1db31ed8d24"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Desired position, float type, little-endian (low byte first, high byte last).
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x100 + ID. The velocity command represents the maximum velocity during trapezoidal acceleration, i.e., the constant velocity segment.

### Control Frame in Velocity Mode <a href="#block-340d4c79856d80e1b25be905a61c9ef9" id="block-340d4c79856d80e1b25be905a61c9ef9"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x200 + ID.

### **Control Frame in Force-Position Hybrid Control Mode** <a href="#block-340d4c79856d8000ab9af63a7cdb5c69" id="block-340d4c79856d8000ab9af63a7cdb5c69"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6]  | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ------ | ----- |
| 0x300+ID        | p\_des |       |       |       | v\_des |       | i\_des |       |

* **P\_des**: Desired position, in radians, float type, little-endian (low byte first, high byte last).
* **V\_des**: Velocity limit, in rad/s, scaled by 100, unsigned 16-bit, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual velocity limit range of 0-100 rad/s.
* **I\_des**: Torque current limit (per-unit), scaled by 10000, unsigned 16-bit type, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual current limit amplitude of 0-1.0.
* **Per-unit current:** Actual current divided by the maximum phase current.

### **Enable** <a href="#block-340d4c79856d807d8e86f4d6ddd568aa" id="block-340d4c79856d807d8e86f4d6ddd568aa"></a>

After power-up self-test, an "Enable" command must be sent to allow motor control. The "Enable" frame is a control frame, with the frame ID as described above. The data payload is identical across all modes as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFC  |

### **Disable** <a href="#block-340d4c79856d80e39a0af018965ef055" id="block-340d4c79856d80e39a0af018965ef055"></a>

The default power-on state of the motor is "Disable." In this state, the three-phase terminal voltages are identical, each being a 50% modulation of the power supply voltage. The "Disable" frame is a control frame, with the frame ID as described above. The data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFD  |

### **Set Zero Position** <a href="#block-340d4c79856d80c284d1ca4e63b11e39" id="block-340d4c79856d80c284d1ca4e63b11e39"></a>

The "Set Zero Position" frame is a control frame. This command sets the current output shaft position as the zero reference and resets the position command value to 0. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFE  |

### **Clear Faults** <a href="#block-340d4c79856d801db544ff7e5b88a1ce" id="block-340d4c79856d801db544ff7e5b88a1ce"></a>

When faults such as overheating, sending a "Clear" can be sent to reset the fault state. The "Clear" frame is a control frame. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFB  |

### **Read parameters** <a href="#block-340d4c79856d80ceac06f3008c39c4e4" id="block-340d4c79856d80ceac06f3008c39c4e4"></a>

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

### **Write parameters** <a href="#block-340d4c79856d8082af1bdbab54378d45" id="block-340d4c79856d8082af1bdbab54378d45"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

RID is defined as above. Upon successful write, the written value is returned. The frame format is identical to the transmitted frame.

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

Writing register data takes effect immediately but are not stored; They will be lost upon power-off unless a "Save Parameters" command is issued to store them in internal memory

### **Save parameters** <a href="#block-340d4c79856d807b83f5c6b6e77e2330" id="block-340d4c79856d807b83f5c6b6e77e2330"></a>

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

### Mode Switching <a href="#block-340d4c79856d806fbb99e3a31cfcb326" id="block-340d4c79856d806fbb99e3a31cfcb326"></a>

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

### **CAN Baud Rate Configuration** <a href="#block-340d4c79856d80f1ac51c25187e855d7" id="block-340d4c79856d80f1ac51c25187e855d7"></a>

By writing specific value to the baud rate register (address 0x23), the current CAN communication baud rate can be modified. Supported baud rates are listed below:

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

### **Register Map** <a href="#block-340d4c79856d8085b70cf68b6762234b" id="block-340d4c79856d8085b70cf68b6762234b"></a>

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
| 0x25         | 37           | Boot\_ver  | Boot Version                      | RO  | /               | uint32 |
| 0x37         | 55           | dir        | Direction                         | RO  | /               | float  |
| 0x38         | 56           | m\_off     | Motor-side Angle Offset           | RO  | /               | float  |
| 0x3B         | 59           | Imax       | Driver Current Limit              | RO  | /               | float  |
| 0x3C         | 60           | VBus       | Bus Voltage                       | RO  | /               | float  |
| 0x3D         | 61           | Tpcb       | PCB Temperature                   | RO  | /               | float  |
| 0x3E         | 62           | Tmtr       | Motor Temperature                 | RO  | /               | float  |
| 0x3F         | 63           | I\_U\_OFF  | Phase U Current Offset            | RO  | /               | float  |
| 0x40         | 64           | I\_V\_OFF  | Phase V Current Offset            | RO  | /               | float  |
| 0x41         | 65           | I\_W\_OFF  | Phase W Current Offset            | RO  | /               | float  |
| 0x50         | 80           | p\_m       | Motor Position                    | RO  | /               | float  |
| 0x51         | 81           | xout       | Output Shaft Position             | RO  | /               | float  |

💡

**Note:**

1. **RW:** Read/Write.
2. **RO:** Read-only.
3. Motor output shaft position is calculated form the rotor position, in radians (rad)
4. Output shaft position refers is measured directly by the output shaft encoder, in radians (rad).

## Host Computer Guide <a href="#block-340d4c79856d80958cb0f9769a59bc93" id="block-340d4c79856d80958cb0f9769a59bc93"></a>

[DAMIAO Host Computer User Manual](https://wiki.openelab.io/damiao/damiao-host-computer-user-manual)
