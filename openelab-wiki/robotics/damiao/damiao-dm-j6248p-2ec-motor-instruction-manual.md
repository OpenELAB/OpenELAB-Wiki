# DAMIAO DM-J6248P-2EC Motor Instruction Manual

> DAMIAO DM-J6248P-2EC Motor User Guide

[**DAMIAO DM-J6248P-2EC Motor**DAMIAO DM-J6248P-2EC: 97N·m high-performance MIT-compatible brushless servo robotic joint motor. For quadrupeds, humanoids & exoskeletons.mdmbot.com](https://www.mdmbot.com/index.php?c=show\&id=110)

## Safety Precautions <a href="#block-344d4c79856d80939e51ebc87fe25b22" id="block-344d4c79856d80939e51ebc87fe25b22"></a>

1. Operate the motor strictly within the specified environmental conditions and maximum winding temperature limits. Failure to do so may result in permanent damage.
2. Prevent foreign objects from entering the rotor. Otherwise, abnormal operation may occur.
3. Inspect all components before use. Do not operate the motor if any components are missing, wom, or damaged.
4. Ensure correct wiring and proper, secure motor installation.
5. Do not touch the rotating or energized parts during operation to avoid injury. High torque operation may generate heat. Avoid contact to prevent burns.
6. Do not disassemble the motor. Unauthorized disassembly may affect control accuracy or cause malfunction.

## **Motor Features** <a href="#block-344d4c79856d8028a2e0e0026396d5dc" id="block-344d4c79856d8028a2e0e0026396d5dc"></a>

1. Dual encoders provide single-turn absolute position feedback at the output shaft, ensuring position information is retained even after power loss.
2. Integrated motor and driver design offers compact structure with high integration.
3. Supports PC-based configuration, monitoring, and firmware upgrades.
4. Provides real-time feedback of motor Velocity, position, torque, and temperature via CAN bus.
5. Features dual temperature protection mechanisms.
6. Supports trapezoidal acceleration and deceleration profiles in position mode.
7. Supports firmware upgrade via CAN.

## Naming Conventions <a href="#block-348d4c79856d80cb8da9d55269cda90c" id="block-348d4c79856d80cb8da9d55269cda90c"></a>

**For example：DM - J4340 X - 2EC VX.X (48V)**

| DM    | (Brand)DAMIAO Technology                                                                                                                                                                                                                                                                                                     |
| ----- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| J     | **J：**&#x4A;oint Motor Series **S：**&#x53;eparable Motor Series                                                                                                                                                                                                                                                              |
| 43    | Stator Diameter 35、43、60、62、80、100（mm）                                                                                                                                                                                                                                                                                       |
| 40    | Reduction Ratio 06、07、09、10、19、40、48                                                                                                                                                                                                                                                                                         |
| X -   | Output Bearing /Special Versions X represents letters such as L,P,etc **-By default：** Deep Groove Ball Bearing. **-P：** Crossed Roller Bearing. **-L：** Lite version (not related to bearing type).                                                                                                                         |
| 2EC   | Encoder **-By default：** single encoder. **-1EC：**&#x53;ingle encoder, CAN communication. **-2EC：**&#x44;ual encoders (single-turn absolute, output shaft),CAN communication. **-1EE：**&#x53;ingle encoder, EtherCAT communication. **-2EE：**&#x44;ual encoder (single-turn absolute, output shaft), EtherCAT communication. |
| VX.X  | Motor Version **VX.X：** Upgrade version(X=0-9),Version omitted=V1.0                                                                                                                                                                                                                                                          |
| （48V） | Driver Rated Voltage **-By default：**&#x32;4V drive voltage **-48V ：**&#x34;8V drive voltage                                                                                                                                                                                                                                 |

## Specifications <a href="#block-344d4c79856d8054b815e9ecc69505fe" id="block-344d4c79856d8054b815e9ecc69505fe"></a>

Please operate the motor within the specifications listed below.

| Type                        | Characteristic Parameters    | Description                                                                                                                   |
| --------------------------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Motor parameters            | Rated Voltage                | 24V-48V                                                                                                                       |
|                             | Rated Phase / Supply Current | 11.3A/7A@24V 11.3A/3.7A@48V                                                                                                   |
|                             | Peak Phase / Supply Current  | 38.7A/16A@24V 38.7A/8A@48V                                                                                                    |
|                             | Rated Torque                 | 30NM                                                                                                                          |
|                             | Peak Torque                  | 97NM                                                                                                                          |
|                             | Rated speed                  | 40rpm                                                                                                                         |
|                             | Maximum No-Load Speed        | 60rpm                                                                                                                         |
| Motor Characteristic Values | Reduction Ratio              | 48 : 1                                                                                                                        |
|                             | Number of Pole Pairs         | 14                                                                                                                            |
|                             | Phase Inductance             | 85uh(@25℃)                                                                                                                    |
|                             | Phase Resistance             | 0.17Ω(@25℃)                                                                                                                   |
| Structure and Weight        | Outer Diameter               | 76mm                                                                                                                          |
|                             | Height                       | 62.5mm                                                                                                                        |
|                             | Motor Weight                 | 628g                                                                                                                          |
| Encoder                     | Encoder Resolution           | 16bit                                                                                                                         |
|                             | Number of Encoders           | 2                                                                                                                             |
|                             | Encoder Type                 | Magnetic Encoder (Single-Turn)                                                                                                |
| Communication Method        | Control interface type       | CAN@5Mbps(Max)                                                                                                                |
|                             | Parameter Tuning Interface   | UART@921600bps                                                                                                                |
| Control and Protection      | Control Mode                 | MIT Mode                                                                                                                      |
|                             |                              | Velocity Mode                                                                                                                 |
|                             |                              | Position Mode                                                                                                                 |
|                             |                              | Force-Position Hybrid Control Mode                                                                                            |
|                             | Protection                   | Drive over-temperature protection: shutdown at 120° C; the motor exits Enable Mode when triggered.                            |
|                             |                              | Motor over-temperature protection (configurable, recommended ≤ 100° C); the motor exits Enable Mode when triggered.           |
|                             |                              | Over-voltage protection(configurable, recommended ≤ 65V); exits Enable Mode when triggered.                                   |
|                             |                              | Communication Loss Protection: the motor exits Enable Mode if no CAN command is received within the specified timeout period. |
|                             |                              | Over-current protection (configurable, recommended ≤ 0.98A); exits Enable Mode when triggered.                                |
|                             |                              | Under-voltage protection: the motor exits Enable Mode if supply voltage falls below the threshold (recommended ≥ 20V).        |

### **Operating Voltage** <a href="#block-344d4c79856d807a87d3f137bd67a637" id="block-344d4c79856d807a87d3f137bd67a637"></a>

The operating voltage range for the driver is 24V to 48V. Hot-swapping is not recommended above 36V. The minimum operating voltage is 20V, and the maximum operating voltage is 65V.

### **Maximum Phase Current** <a href="#block-344d4c79856d80ae8969e1267811c2aa" id="block-344d4c79856d80ae8969e1267811c2aa"></a>

The maximum phase current of the driver can be obtained from the startup serial output:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/83385d1f-afef-42a2-8d9b-8a390804e8d1/image/w=1920,quality=90,fit=scale-down" alt="image" height="448.11161118993215" width="737.5750122070312">

The maximum phase current percentage can be limited by setting a percentage in the configuration tool. The default value is 0.8 (i.e., 80% of the measurable maximum current). It is recommended that this value not exceed 98%.

### **Maximum Rotational Speed** <a href="#block-344d4c79856d8099baddc3ad97c173b6" id="block-344d4c79856d8099baddc3ad97c173b6"></a>

The maximum rotational speed is limited by multiple factors, including the power supply voltage (VBUS), rotor flux linkage (ψf), and gear ratio (GR). An upper limit can typically be calculated using the following formula:

VMAX(rad/s)=0.57735∗VBUSNpp×GR×ψf(rad/s)VMAX​(rad/s)=0.57735∗Npp​×GR×ψf​VBUS​​(rad/s)

where VBUS is the supply voltage, Npp is the number of pole pairs, and ψf is the rotor flux linkage.

### **Torque Constant** <a href="#block-344d4c79856d8039b0dfe59a84958103" id="block-344d4c79856d8039b0dfe59a84958103"></a>

The torque constant of the motor can be considered constant within its rated range. With a gearbox, it can be calculated using the following formula:

Kt=1.5∗Npp∗ψf∗GR∗GREFKt​=1.5∗Npp​∗ψf​∗GR∗GREF

Where Npp is the number of pole pairs, ψf is the rotor flux linkage, GR is the gear ratio, and GREF is the gearbox torque transmission coefficient.

## Torque–Speed (T–N) Curve <a href="#block-348d4c79856d80948b96f08ce3741ab0" id="block-348d4c79856d80948b96f08ce3741ab0"></a>

The following curve shows the measured performance at 24 V and an ambient temperature of 25° C:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/514c92a9-e7dd-4dd7-bf44-de93e6f61d53/image/w=1920,quality=90,fit=scale-down" alt="image" height="522.1392463235295" width="946.8125">

## **Packing List** <a href="#block-344d4c79856d80539229db8de93ae700" id="block-344d4c79856d80539229db8de93ae700"></a>

1. Motor (with integrated driver) ×1
2. Power cable (with CAN interface) : XT30(2+2)-F connector, single-ended(100mm)×1
3. Debug serial cable: GH1.25 3-pin cable (reverse-side connector, 300mm) ×1

## Interface & Pin Description <a href="#block-344d4c79856d8000b76bfbc0a1428649" id="block-344d4c79856d8000b76bfbc0a1428649"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0164321b-0442-4465-bb6a-72a583ed4f34/image/w=1920,quality=90,fit=scale-down" alt="image" height="243.49920760697304" width="528">

| Interface / Pin No.                   | Instruction                                                                                                                                                                                                                                                                                                                                                                      |
| ------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power Interface-1(with CAN interface) | 1. Connect the power supply via the XT30(2+2)-F cable. The rated voltage is 24 V. 2. Connect external controller via the CAN communication interface to receive CAN control commands and transmit motor status feedback. 3. The motor features two power interfaces. Either interface can be used independently , or multiple motors can be daisy-chained for convenient wiring. |
| Power Interface-2(with CAN interface) | 1. Connect the power supply via the XT30(2+2)-F cable. The rated voltage is 24 V. 2. Connect external controller via the CAN communication interface to receive CAN control commands and transmit motor status feedback. 3. The motor features two power interfaces. Either interface can be used independently , or multiple motors can be daisy-chained for convenient wiring. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a753714f-ba5c-4b2f-bdb2-df5dff644028/image/w=1920,quality=90,fit=scale-down" alt="image" height="307.13286713286715" width="576">

| Interface / Pin No.            | Instruction                                                                                                                                         |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debug Serial Interface(Port 3) | Connect to a PC via the GH1.25 3-pin cable using a USB-to-CAN adapter (or USB-to serial module) for parameters configuration and firmware upgrades. |

## Motor Dimensions and Mounting <a href="#block-344d4c79856d800a8612dab4b895fc4e" id="block-344d4c79856d800a8612dab4b895fc4e"></a>

Please install the motor onto the target equipment according to the motor mounting hole dimensions and layout.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e566120e-5016-4ded-95d1-150a52843d88/image/w=1920,quality=90,fit=scale-down" alt="image" height="536.1547882427307" width="737.5625">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e0cc6c42-68e9-4ccf-a64e-20cd35b28142/image/w=1920,quality=90,fit=scale-down" alt="image" height="446.7947584312381" width="638.9750366210938">

## LED Status <a href="#block-344d4c79856d805f9842de93c2d058dd" id="block-344d4c79856d805f9842de93c2d058dd"></a>

| Normal Status | Solid Green  | Enable Mode (ERR = 1), normal operation                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|               | Solid Red    | Disable Mode (ERR = 0)（Default state after power-on）                                                                                                                                                                                                                                                                                                                                                                                                     |
| Fault Status  | Flashing Red | Fault codes and fault conditions: **3** – Output shaft calibration error; **4** – Sensor output error; **5** – Motor encoder calibration error; **8** – Over-voltage; **9** – Under-voltage; **A** – Over-current; **B** – MOS over-temperature; **C** – Motor winding over-temperature; **D** – Communication loss; **E** – Overload; Fault conditions can be identified via the feedback frames or displayed in the the Damiao configuration software. |

## Operating Modes <a href="#block-344d4c79856d8048afd9e2c7a38b4418" id="block-344d4c79856d8048afd9e2c7a38b4418"></a>

### MIT Mode <a href="#block-344d4c79856d80f29a3fcd0618185fec" id="block-344d4c79856d80f29a3fcd0618185fec"></a>

The MIT mode is compatible with the standard MIT control method, enabling seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX).

CAN commands are converted into torque values. The torque is then used as the reference for current control. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="262.11989574283234" width="754.25">

Based on the MIT model, various control strategies can be derived. For instance, when kp=0 and kd ≠ 0, a constant rotational speed can be achieved by setting v\_des. When kp=0 and kd=0, a torque output is applied directly by setting t\_ff (feedforward torque).

💡

**Note:** When controlling position, kd must not be set to zero, as this may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-344d4c79856d802c9256c1cb9c7140fc" id="block-344d4c79856d802c9256c1cb9c7140fc"></a>

This mode uses three control loops: position, velocity, and current(torque). The position loop sets the target for the velocity loop. The velocity loop then sets the target for the current loop. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="228.67546063651594" width="754.25">

**p\_des** represents the target position, while **v\_des** limits the maximum absolute velocity during motion.

When tuned using recommended parameters from the configuration tool, this mode provides high accuracy and smooth motion, at the cost of slower response time.

In addition to **v\_des**, acceleration and deceleration can also be configured. If additional oscillations occur, increasing acceleration/deceleration may help stabilize the system.

💡

**Note:** The units of p\_des and v\_des are rad and rad/s respectively, and both are of type float. The damping factor must be set to a non-zero positive value.Refer to the notes for velocity mode.

### Velocity Mode <a href="#block-344d4c79856d809284c8efa65964b3be" id="block-344d4c79856d809284c8efa65964b3be"></a>

This mode keeps the motor running at the target velocity. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

**Note:** The unit of **v\_des** is **rad/s** and its data type is **float**. To use the automatic parameter calculation function of the debugging assistant, the damping factor must be set to a **positive non-zero number**. Typically, its value ranges from **2.0 to 10.0**. A damping factor that is too small will cause velocity oscillations and large overshoot, while a damping factor that is too large will result in a long rise time. The recommended setting value is **4.0**.

### **Force-Position Hybrid Mode** <a href="#block-344d4c79856d80bb882be157bf9860a2" id="block-344d4c79856d80bb882be157bf9860a2"></a>

The force-position hybrid control mode is based on position-velocity control, with additional torque adjustment. Allows control of both position and output torque at the same time. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4876b2d6-b47f-47a9-9dc7-20de651abc12/29e55681073b4ab3acd8adaf9b17c02e/w=1920,quality=90,fit=scale-down" alt="在这里插入图片描述" height="1000" width="1000">

A current command saturation stage is added after the velocity loop output command. This limits the current loop reference within the specified range.

### **Mode Switching** <a href="#block-344d4c79856d809d943fde53d11a31ea" id="block-344d4c79856d809d943fde53d11a31ea"></a>

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

## **CAN communication** <a href="#block-344d4c79856d801ab116c9ba796fe05f" id="block-344d4c79856d801ab116c9ba796fe05f"></a>

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

### **CAN Baud Rate Configuration** <a href="#block-344d4c79856d80aa825dd19f55563004" id="block-344d4c79856d80aa825dd19f55563004"></a>

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

### Feedback Frame <a href="#block-344d4c79856d80d39409fbcde9863da0" id="block-344d4c79856d80d39409fbcde9863da0"></a>

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

### Control Frame in MIT Mode <a href="#block-344d4c79856d8007a8cde951b9fcfbce" id="block-344d4c79856d8007a8cde951b9fcfbce"></a>

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

Position, velocity, and torque are preset to ±12.566, ±20, and ±120. These values can be adjusted according to the motor specifications. When sending control commands, the scaling ranges must remain consistent with the configured values.

Otherwise, the commands will be scaled incorrectly.

### Control Frame in Position-Velocity Mode <a href="#block-344d4c79856d80acbb19f865dab7c130" id="block-344d4c79856d80acbb19f865dab7c130"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Desired position, float type, little-endian (low byte first, high byte last).
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x100 + ID. The velocity command defines the maximum allowable velocity during operation.

### Control Frame in Velocity Mode <a href="#block-344d4c79856d8098b331dbe160154b39" id="block-344d4c79856d8098b331dbe160154b39"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x200 + ID.

### **Control Frame in Force-Position Hybrid Control Mode** <a href="#block-344d4c79856d8093b196f4008c2a5737" id="block-344d4c79856d8093b196f4008c2a5737"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6]  | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ------ | ----- |
| 0x300+ID        | p\_des |       |       |       | v\_des |       | i\_des |       |

* **P\_des**: Desired position, in radians, float type, little-endian (low byte first, high byte last).
* **V\_des**: Velocity limit, in rad/s, scaled by 100, unsigned 16-bit, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual velocity limit range of 0-100 rad/s.
* **I\_des**: Torque current limit (per-unit), scaled by 10000, unsigned 16-bit type, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual current limit amplitude of 0-1.0.
* **Per-unit current**: Actual current divided by the maximum phase current.

### **Enable** <a href="#block-344d4c79856d8047b377c191b5627952" id="block-344d4c79856d8047b377c191b5627952"></a>

After the power-on self-test is completed, the "Enable" command must be sent before control can be performed. The "Enable" frame is a control frame, with the frame ID as described previously. The difference lies in the data field. Regardless of which mode the motor is in, the data definition for "Enable" is the same, as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFC  |

### **Disable** <a href="#block-344d4c79856d80aab774cb31433c5117" id="block-344d4c79856d80aab774cb31433c5117"></a>

The default power-on state of the motor is "Disable." In this state, the three-phase terminal voltages are identical, each being a 50% modulation of the power supply voltage. The "Disable" frame is a control frame, with the frame ID as described above. The data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFD  |

### **Set Zero Position** <a href="#block-344d4c79856d8052befef858ea341770" id="block-344d4c79856d8052befef858ea341770"></a>

The "Set Zero Position" frame is a control frame. This command sets the current output shaft position as the zero reference and resets the position command value to 0. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFE  |

### **Clear Faults** <a href="#block-344d4c79856d8090b87ae5b347e309ac" id="block-344d4c79856d8090b87ae5b347e309ac"></a>

When faults such as overheating, sending a "Clear" can be sent to reset the fault state. The "Clear" frame is a control frame. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFB  |

### **Read parameters** <a href="#block-344d4c79856d8014beb4c9743cbcd85a" id="block-344d4c79856d8014beb4c9743cbcd85a"></a>

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

### **Write parameters** <a href="#block-344d4c79856d80e89d0fe3368542ab07" id="block-344d4c79856d80e89d0fe3368542ab07"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

RID is defined as above. Upon successful write, the written value is returned. The frame format is identical to the transmitted frame.

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

Writing register data takes effect immediately but are not stored; They will be lost upon power-off unless a "Save Parameters" command is issued to store them in internal memory

### **Save parameters** <a href="#block-344d4c79856d8092a032c1e7c98fd154" id="block-344d4c79856d8092a032c1e7c98fd154"></a>

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

### Mode Switching <a href="#block-344d4c79856d8092860ef526368eb161" id="block-344d4c79856d8092860ef526368eb161"></a>

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

### CAN Baud Rate Modification <a href="#block-344d4c79856d80df91a4e298d928cf88" id="block-344d4c79856d80df91a4e298d928cf88"></a>

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

### Register List and Range <a href="#block-344d4c79856d809a9e11c05429142797" id="block-344d4c79856d809a9e11c05429142797"></a>

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
3. Motor output shaft position is calculated form the rotor position, in radians (rad)
4. Output shaft position refers is measured directly by the output shaft encoder, in radians (rad).

## Host Computer Guide <a href="#block-344d4c79856d80ff870fc0f5b3e5898d" id="block-344d4c79856d80ff870fc0f5b3e5898d"></a>

[DAMIAO Host Computer User Manual](https://wiki.openelab.io/damiao/damiao-host-computer-user-manual)
