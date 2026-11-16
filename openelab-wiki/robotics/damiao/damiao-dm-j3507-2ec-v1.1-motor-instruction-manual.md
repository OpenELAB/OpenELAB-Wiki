# DAMIAO DM-J3507-2EC V1.1 Motor Instruction Manual

> DAMIAO DM-J3507-2EC V1.1 Motor User Guide

[**DAMIAO DM-J3507-2EC Motor**DAMIAO DM-J3507-2EC: 3N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.openelab.io](https://openelab.io/products/damiao-brushless-servo-dm-j3507)

## Safety Precautions <a href="#block-34ad4c79856d81d7856cc60f3804d5e5" id="block-34ad4c79856d81d7856cc60f3804d5e5"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.

## **Motor Features** <a href="#block-34ad4c79856d8176aba6d19926b1e687" id="block-34ad4c79856d8176aba6d19926b1e687"></a>

1. Dual encoders provide single-turn absolute position feedback at the output shaft, ensuring position information is retained even after power loss.
2. Integrated motor and driver design offers compact structure with high integration.
3. Supports PC-based configuration, monitoring, and firmware upgrades.
4. Supports CAN FD, with a maximum baud rate of 5Mbps.
5. Provides real-time feedback of motor Velocity, position, torque, and temperature via CAN bus.
6. Features dual temperature protection mechanisms.
7. Low-speed, high-torque performance.
8. Multiple control modes with flexible switching.

## **Naming Specification** <a href="#block-34ad4c79856d8121aab6fad339358758" id="block-34ad4c79856d8121aab6fad339358758"></a>

**For example：DM - J3507 X - 2EC VX.X (48V)**

| DM    | DAMIAO Technology                                                                                                                                                                                                                                                                                                                                      |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| J     | **J**：Joint Motor Series **S：**&#x44;iscrete Motor Series                                                                                                                                                                                                                                                                                              |
| 35    | Stator Diameter 35、43、60、62、80、100（mm）                                                                                                                                                                                                                                                                                                                 |
| 07    | Reduction Ratio 06、07、09、10、19、40、48                                                                                                                                                                                                                                                                                                                   |
| X -   | Output Bearing /Special Versions X represents letters such as L,P,etc **-By default：** Deep Groove Ball Bearing. **-P：** Crossed Roller Bearing. **-L：** Lite version (not related to bearing type).                                                                                                                                                   |
| 2EC   | Encoder **-By default：** Represents a single encoder. **-1EC：** Single encoder, CAN communication. **-2EC：** Dual encoder (single-turn absolute position on the output shaft),CAN communication. **-1EE：** Single encoder, EtherCAT communication. **-2EE：** Dual encoder (single-turn absolute position on the output shaft), EtherCAT communication. |
| VX.X  | Motor Version **VX.X：** Upgrade version(X=0-9),Version omitted=V1.0                                                                                                                                                                                                                                                                                    |
| （48V） | Driver Rated Voltage **-By default：**&#x32;4V drive voltage **-48V ：**&#x34;8V drive voltage                                                                                                                                                                                                                                                           |

## Specifications <a href="#block-34ad4c79856d81f0be2aec537f85563d" id="block-34ad4c79856d81f0be2aec537f85563d"></a>

Please operate the motor within the specifications listed below.

| Type                        | Characteristic Parameters    | DM-J3507-2EC（24V）                                                                                                             | DM-J3507-2EC（48V）                                                                                                             |
| --------------------------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Motor parameters            | Rated Voltage                | 24V                                                                                                                           | 48V                                                                                                                           |
|                             | Rated Phase / Supply Current | 3.0A/1.2A                                                                                                                     | 3.0A /0.6A                                                                                                                    |
|                             | Peak Phase / Supply Current  | 8.3A/4A                                                                                                                       | 8.3A/2A                                                                                                                       |
|                             | Rated Torque                 | 0.8NM                                                                                                                         | 0.8NM                                                                                                                         |
|                             | Peak Torque                  | 3NM                                                                                                                           | 3NM                                                                                                                           |
|                             | Rated speed                  | 150rpm                                                                                                                        | 150rpm                                                                                                                        |
|                             | Maximum No-Load Speed        | 460rpm                                                                                                                        | 910rpm                                                                                                                        |
| Motor Characteristic Values | Reduction Ratio              | 1: 7                                                                                                                          | 1: 7                                                                                                                          |
|                             | Number of Pole Pairs         | 14                                                                                                                            | 14                                                                                                                            |
|                             | Phase Inductance             | 235uh                                                                                                                         | 235uh                                                                                                                         |
|                             | Phase Resistance             | 0.8Ω                                                                                                                          | 0.8Ω                                                                                                                          |
| Structure and Weight        | Outer Diameter               | 46mm                                                                                                                          | 46mm                                                                                                                          |
|                             | Height                       | 37.9mm                                                                                                                        | 37.9mm                                                                                                                        |
|                             | Motor Weight                 | \~ 150g                                                                                                                       | \~ 150g                                                                                                                       |
| Encoder                     | Encoder Resolution           | 14 bits                                                                                                                       | 14 bits                                                                                                                       |
|                             | Number of Encoders           | 2                                                                                                                             | 2                                                                                                                             |
|                             | Encoder Type                 | Magnetic Encoder (Single-Turn)                                                                                                | Magnetic Encoder (Single-Turn)                                                                                                |
| Communication Method        | Control interface type       | CAN                                                                                                                           | CAN                                                                                                                           |
|                             | Parameter Tuning Interface   | UART@921600bps                                                                                                                | UART@921600bps                                                                                                                |
| Control and Protection      | Control Mode                 | MIT Mode                                                                                                                      | MIT Mode                                                                                                                      |
|                             |                              | Velocity Mode                                                                                                                 | Velocity Mode                                                                                                                 |
|                             |                              | Position Mode                                                                                                                 | Position Mode                                                                                                                 |
|                             |                              | Force-Position Hybrid Control Mode                                                                                            | Force-Position Hybrid Control Mode                                                                                            |
|                             | Protection                   | Drive over-temperature protection: shutdown at 120° C; the motor exits Enable Mode when triggered.                            | Drive over-temperature protection: shutdown at 120° C; the motor exits Enable Mode when triggered.                            |
|                             |                              | Motor over-temperature protection (configurable, recommended ≤ 100° C); the motor exits Enable Mode when triggered.           | Motor over-temperature protection (configurable, recommended ≤ 100° C); the motor exits Enable Mode when triggered.           |
|                             |                              | Over-voltage protection(configurable, recommended ≤ 30V); exits Enable Mode when triggered.                                   | Over-voltage protection(configurable, recommended ≤ 54V); exits Enable Mode when triggered.                                   |
|                             |                              | Communication Loss Protection: the motor exits Enable Mode if no CAN command is received within the specified timeout period. | Communication Loss Protection: the motor exits Enable Mode if no CAN command is received within the specified timeout period. |
|                             |                              | Over-current protection (configurable, recommended ≤ 9.8A); exits Enable Mode when triggered.                                 | Over-current protection (configurable, recommended ≤ 9.8A); exits Enable Mode when triggered.                                 |
|                             |                              | Under-voltage protection: the motor exits Enable Mode if supply voltage falls below the threshold (recommended ≥ 15V).        | Under-voltage protection: the motor exits Enable Mode if supply voltage falls below the threshold (recommended ≥ 15V).        |

### **Operating Voltage** <a href="#block-34ad4c79856d8158b42afd4510ac1176" id="block-34ad4c79856d8158b42afd4510ac1176"></a>

The operating voltage range for the 24V motor driver is 24V–28V, with a minimum operating voltage of 15V and a maximum of 30V.

For the 48V motor driver, the operating voltage range is 24V–48V, with a minimum operating voltage of 15V and a maximum of 54V.Hot-plugging is recommended to be avoided when the voltage exceeds 36V.

### **Maximum Phase Current** <a href="#block-34ad4c79856d8163b0f8ff765f92461d" id="block-34ad4c79856d8163b0f8ff765f92461d"></a>

The maximum phase current of the driver can be obtained from the startup serial output:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/83385d1f-afef-42a2-8d9b-8a390804e8d1/image/w=1920,quality=90,fit=scale-down" alt="image" height="448.11161118993215" width="737.5750122070312">

The maximum phase current percentage can be limited by setting a percentage in the configuration tool. The default value is 0.8 (i.e., 80% of the measurable maximum current). It is recommended that this value not exceed 98%.

### **Maximum Rotational Speed** <a href="#block-34ad4c79856d81d592d6cc9e70ddec2f" id="block-34ad4c79856d81d592d6cc9e70ddec2f"></a>

The maximum rotational speed is limited by multiple factors, including the power supply voltage (VBUS), rotor flux linkage (ψf), and gear ratio (GR). An upper limit can typically be calculated using the following formula:

VMAX(rad/s)=0.57735∗VBUSNpp×GR×ψf(rad/s)VMAX​(rad/s)=0.57735∗Npp​×GR×ψf​VBUS​​(rad/s)

where VBUS is the supply voltage, Npp is the number of pole pairs, and ψf is the rotor flux linkage.

### **Torque Constant** <a href="#block-34ad4c79856d81f3b062db6362fdfa84" id="block-34ad4c79856d81f3b062db6362fdfa84"></a>

The torque constant of the motor can be considered constant within its rated range. With a gearbox, it can be calculated using the following formula:

Kt=1.5∗Npp∗ψf∗GR∗GREFKt​=1.5∗Npp​∗ψf​∗GR∗GREF

Where Npp is the number of pole pairs, ψf is the rotor flux linkage, GR is the gear ratio, and GREF is the gearbox torque transmission coefficient.

## Torque–Speed (T–N) Curve <a href="#block-34ad4c79856d814baf88cdeef8d4efea" id="block-34ad4c79856d814baf88cdeef8d4efea"></a>

From left to right are the performance curves measured for the 24V motor and 48V motor respectively at ambient temperature of 25℃ .

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/aaaa871d-3e3e-49c9-8e56-d9b68b38a18b/image/w=1920,quality=90,fit=scale-down" alt="image" height="317.51041554642404" width="566.5875244140625">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0f82cf75-437f-45a7-a415-8141809a7264/image/w=1920,quality=90,fit=scale-down" alt="image" height="305.63277229845625" width="566.5625">

## **Packing List** <a href="#block-34ad4c79856d81fb8e8ee02571f49a4b" id="block-34ad4c79856d81fb8e8ee02571f49a4b"></a>

1. Motor (with integrated driver) ×1
2. Power cable (with CAN interface) : SH1.0 cable 3-pin (200mm) ×1
3. Debug serial cable: SH1.0 cable 8-pin (200mm) ×1

💡

**Note:** It is recommended to purchase the adapter board separately: Adapter board (SH1.0 3-pin + 8-pin to XT30 + GH1.25). This accessory is not included with the motor.

## Interface & Pin Description <a href="#block-34ad4c79856d81fdaca9e0e887ec4e58" id="block-34ad4c79856d81fdaca9e0e887ec4e58"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7cb9ec0f-6b64-432c-98ad-349ecc234251/image/w=1920,quality=90,fit=scale-down" alt="image" height="195.1102732884065" width="638.9861450195312">

| Interface / Pin No.                 | Instruction                                                                                                                                                                                     |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power + CAN Communication Interface | 1. Connect the power supply using the SH1.0 8-pin cable. 2. Connect external controller via the CAN communication interface to receive CAN control commands and transmit motor status feedback. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/04de7ee5-20af-4550-9e50-b467596abbfa/image/w=1920,quality=90,fit=scale-down" alt="image" height="159.5679012345679" width="470">

| Interface / Pin No.    | Instruction                                                                                                                                                                                                        |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Debug Serial Interface | Connect to a PC via the GH1.25 3-pin cable with an adapter board (SH1.0 3-pin + 8-pin to XT30 + GH1.25),use a USB2CAN debugging tool (or USB-to-serial module) for parameters configuration and firmware upgrades. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/82b21181-7175-4d3d-a372-16f4e247c086/image/w=1920,quality=90,fit=scale-down" alt="image" height="121.57457867405445" width="566.5375366210938">

| Interface / Pin No.      | Instruction                                                          |
| ------------------------ | -------------------------------------------------------------------- |
| Terminal Resistor Switch | The motor is equipped with a terminal resistor, disabled by default. |

💡

Note: When inserting the connector into the motor port, ensure correct orientation to avoid bending or damaging the pins.

## Motor Dimensions and Mounting <a href="#block-34ad4c79856d8169be17eec3568890a0" id="block-34ad4c79856d8169be17eec3568890a0"></a>

Please install the motor onto the target equipment according to the motor mounting hole dimensions and layout.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1fea9023-1497-49b9-93b1-363a94b2e39f/image/w=1920,quality=90,fit=scale-down" alt="image" height="255.33647315698033" width="651.5694580078125">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/54370b50-ab2c-431c-87b8-9256e570adb5/image/w=1920,quality=90,fit=scale-down" alt="image" height="281.88740716170537" width="651.5555419921875">

## LED Status <a href="#block-34ad4c79856d81d8a21ffdf69e824550" id="block-34ad4c79856d81d8a21ffdf69e824550"></a>

| Normal Status | Solid Green  | Enable Mode (ERR = 1), normal operation                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|               | Solid Red    | Disable Mode (ERR = 0)（Default state after power-on）                                                                                                                                                                                                                                                                                                                                                                                                     |
| Fault Status  | Flashing Red | Fault codes and fault conditions: **3** – Output shaft calibration error; **4** – Sensor output error; **5** – Motor encoder calibration error; **8** – Over-voltage; **9** – Under-voltage; **A** – Over-current; **B** – MOS over-temperature; **C** – Motor winding over-temperature; **D** – Communication loss; **E** – Overload; Fault conditions can be identified via the feedback frames or displayed in the the Damiao configuration software. |

## Operating Modes <a href="#block-34ad4c79856d8116a401c514df15ac85" id="block-34ad4c79856d8116a401c514df15ac85"></a>

### MIT Mode <a href="#block-34ad4c79856d81e7b029fe0a43f91578" id="block-34ad4c79856d81e7b029fe0a43f91578"></a>

The MIT mode is compatible with the standard MIT control method, enabling seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX).

CAN commands are converted into torque values. The torque is then used as the reference for current control. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Based on the MIT model, various control strategies can be derived. For instance, when kp=0 and kd ≠ 0, a constant rotational speed can be achieved by setting v\_des. When kp=0 and kd=0, a torque output is applied directly by setting t\_ff (feedforward torque).

💡

**Note:**

1. When controlling position, kd must not be set to zero, as this may cause motor oscillation or even loss of control.
2. In this mode, the current loop response speed can be improved by increasing the current loop band width.

### Position-Velocity Mode <a href="#block-34ad4c79856d8133891dfa23bd32a069" id="block-34ad4c79856d8133891dfa23bd32a069"></a>

This mode uses three control loops: position, velocity, and current(torque). The position loop sets the target for the velocity loop. The velocity loop then sets the target for the current loop. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** represents the target position, while **v\_des** limits the maximum absolute velocity during motion.

When tuned using recommended parameters from the configuration tool, this mode provides high accuracy and smooth motion, at the cost of slower response time.

In addition to **v\_des**, acceleration and deceleration can also be configured. If additional oscillations occur, increasing acceleration/deceleration may help stabilize the system.

💡

**Note:** The units of p\_des and v\_des are rad and rad/s respectively, and both are of type float. The damping factor must be set to a non-zero positive value.Refer to the notes for velocity mode.

### Velocity Mode <a href="#block-34ad4c79856d81d39f13f34d5c88c215" id="block-34ad4c79856d81d39f13f34d5c88c215"></a>

This mode keeps the motor running at the target velocity. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

**Note:** The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

### **Force-Position Hybrid Mode** <a href="#block-34ad4c79856d81dfb349ce9e546e81e0" id="block-34ad4c79856d81dfb349ce9e546e81e0"></a>

The force-position hybrid control mode is based on position-velocity control, with additional torque adjustment. Allows control of both position and output torque at the same time. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4876b2d6-b47f-47a9-9dc7-20de651abc12/29e55681073b4ab3acd8adaf9b17c02e/w=1920,quality=90,fit=scale-down" alt="在这里插入图片描述" height="1000" width="1000">

A current command saturation stage is added after the velocity loop output command. This limits the current loop reference within the specified range.

### **Mode Switching** <a href="#block-34ad4c79856d8196a94eed5d792adb06" id="block-34ad4c79856d8196a94eed5d792adb06"></a>

Mode switching can be configured via the host computer using the serial port. Simply select the desired mode and click "**Write Parameters**". After successful configuration using this method, the motor will automatically reset, and the mode will be stored inside the motor driver without being lost after power cycling.

Additionally, mode switching can also be performed via the CAN interface by modifying the content of the mode register. For details, refer to the "**Mode Switching**" section in the next chapter.

When using the CAN method, the motor will not reset, but the following five variables will be cleared to zero:

1. Position command value
2. Velocity command value
3. Torque command value (MIT mode)
4. kp (MIT mode)
5. kd (MIT mode)

💡

**Note:** If the "Save Parameters" command is not issued, the mode will not be stored. It will be lost after power loss and will load the last saved mode upon power-up.

## **CAN communication** <a href="#block-34ad4c79856d818eb6baffe2181ba004" id="block-34ad4c79856d818eb6baffe2181ba004"></a>

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

### **CAN Baud Rate Configuration** <a href="#block-34ad4c79856d8119b2cfc6d649473e87" id="block-34ad4c79856d8119b2cfc6d649473e87"></a>

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

### Feedback Frame <a href="#block-34ad4c79856d818bb59fe4f399905356" id="block-34ad4c79856d818bb59fe4f399905356"></a>

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

**See the figures below:**

1. **Position linear mapping**
2.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/431c621a-5279-408d-9e05-f0d8db807d1b/image/w=1920,quality=90,fit=scale-down" alt="image" height="190.53269919370993" width="337.76251220703125">
3. **Velocity linear mapping**
4.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/97754654-f924-46e1-b508-eca5a88bf98d/image/w=1920,quality=90,fit=scale-down" alt="image" height="208.4341560132576" width="337.7749938964844">
5. Torque Linear Mapping
6.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d4a9111f-265c-4c96-b2e0-927acd75db98/image/w=1920,quality=90,fit=scale-down" alt="image" height="186.0857142857143" width="334">

💡

**Note:**

1. After power-on, the reported position is limited to the range \[-π, π] rad.
2. The unit of position is rad (radians), representing the output shaft position (after gear reduction). All references to position below follow this definition.
3. The unit of velocity is rad/s, representing the output shaft velocity (after gear reduction). All references to velocity below follow this definition.
4. The unit of torque is Nm, representing the output shaft torque (after gear reduction). All references to torque below follow this definition.

### Control Frame in MIT Mode <a href="#block-34ad4c79856d811a8f55ecf112b1ba1e" id="block-34ad4c79856d811a8f55ecf112b1ba1e"></a>

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

MIT commands are transmitted by linearly scaling floating-point values into integer representations. The driver converts the received integers back into floating-point values using the same scaling. Two conversion functions are used: float\_to\_uint, uint\_to\_float.

Conversion Method:

Copy

```c
float uint_to_float(int x_int, float x_min, float x_max, int bits)
{
	/// converts unsigned int to float, given range and number of bits ///
	float span = x_max - x_min;
	float offset = x_min;
	return ((float)x_int)*span/((float)((1<<bits)-1)) + offset;
}

int float_to_uint(float x, float x_min, float x_max, int bits)
{
	/// Converts a float to an unsigned int, given range and number of bits ///
	float span = x_max - x_min;
	float offset = x_min;
	return (int) ((x-offset)*((float)((1<<bits)-1))/span);
}
```

The conversion requires predefined minimum and maximum values for each variable, which can be configured on the parameter setting page. Default ranges: KP: 0.0 \~ 500.0, KD: 0.0 \~ 5.0.

Position, velocity, and torque are preset to ±12.566, ±100, and ±5. These values can be adjusted according to the motor specifications. When sending control commands, the scaling ranges must remain consistent with the configured values.

### Control Frame in Position-Velocity Mode <a href="#block-34ad4c79856d8174a94ef13de5267db7" id="block-34ad4c79856d8174a94ef13de5267db7"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Desired position, float type, little-endian (low byte first, high byte last).
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x100 + ID. The velocity defines the maximum allowable velocity during operation.

### Control Frame in Velocity Mode <a href="#block-34ad4c79856d8143a556c7732aef46b8" id="block-34ad4c79856d8143a556c7732aef46b8"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x200 + ID.

### **Control Frame in Force-Position Hybrid Control Mode** <a href="#block-34ad4c79856d810eadacf575927ff8df" id="block-34ad4c79856d810eadacf575927ff8df"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6]  | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ------ | ----- |
| 0x300+ID        | p\_des |       |       |       | v\_des |       | i\_des |       |

* **P\_des**: Desired position, in radians, float type, little-endian (low byte first, high byte last).
* **V\_des**: Velocity limit, in rad/s, scaled by 100, unsigned 16-bit, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual velocity limit range of 0-100 rad/s.
* **I\_des**: Torque current limit (per-unit), scaled by 10000, unsigned 16-bit type, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual current limit amplitude of 0-1.0.
* **Per-unit current:** Actual current divided by the maximum phase current,DM-J3507-2EC maximum current is 10.26 A.

### **Enable** <a href="#block-34ad4c79856d813b9e0cc96253234194" id="block-34ad4c79856d813b9e0cc96253234194"></a>

After power-up self-test, an "Enable" command must be sent to allow motor control. The "Enable" frame is a control frame, with the frame ID as described above. The data payload is identical across all modes as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFC  |

### **Disable** <a href="#block-34ad4c79856d816c8148ec3ea5cd6cc2" id="block-34ad4c79856d816c8148ec3ea5cd6cc2"></a>

The default power-on state of the motor is "Disable." In this state, the three-phase terminal voltages are identical, each being a 50% modulation of the power supply voltage. The "Disable" frame is a control frame, with the frame ID as described above. The data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFD  |

### **Set Zero Position** <a href="#block-34ad4c79856d81d0a77ffcca2406c613" id="block-34ad4c79856d81d0a77ffcca2406c613"></a>

The "Set Zero Position" frame is a control frame. This command sets the current output shaft position as the zero reference and resets the position command value to 0. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFE  |

### **Clear Faults** <a href="#block-34ad4c79856d816abf18c9158dc1012b" id="block-34ad4c79856d816abf18c9158dc1012b"></a>

When faults such as overheating, sending a "Clear" can be sent to reset the fault state. The "Clear" frame is a control frame. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFB  |

### **Read parameters** <a href="#block-34ad4c79856d813296f0cac1d2aaa9ee" id="block-34ad4c79856d813296f0cac1d2aaa9ee"></a>

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

### **Write parameters** <a href="#block-34ad4c79856d814aba7ff686056a91b8" id="block-34ad4c79856d814aba7ff686056a91b8"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

RID is defined as above. Upon successful write, the written value is returned. The frame format is identical to the transmitted frame.

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

Writing register data takes effect immediately but are not stored; They will be lost upon power-off unless a "Save Parameters" command is issued to store them in internal memory

### **Save parameters** <a href="#block-34ad4c79856d81ad8ed3d52f1b5a388d" id="block-34ad4c79856d81ad8ed3d52f1b5a388d"></a>

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

### Mode Switching <a href="#block-34ad4c79856d813992d8e2e9a602c9fd" id="block-34ad4c79856d813992d8e2e9a602c9fd"></a>

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

### **CAN Baud Rate Configuration** <a href="#block-34ad4c79856d81269cc8f22cd9669b91" id="block-34ad4c79856d81269cc8f22cd9669b91"></a>

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

### **Register Map** <a href="#block-34ad4c79856d810fbe8cf9e3f0d7d4a1" id="block-34ad4c79856d810fbe8cf9e3f0d7d4a1"></a>

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
| 0x19         | 25           | KP\_ASR    | Velocity Loop Kp                  | RW  | \[0.0,fmax]     | float  |
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

## Host Computer Guide <a href="#block-34ad4c79856d81158f89cd044481bc9b" id="block-34ad4c79856d81158f89cd044481bc9b"></a>

[DAMIAO Host Computer User Manual](https://wiki.openelab.io/damiao/damiao-host-computer-user-manual)
