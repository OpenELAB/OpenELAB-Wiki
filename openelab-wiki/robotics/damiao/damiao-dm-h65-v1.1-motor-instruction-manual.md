# DAMIAO DM-H65 V1.1 Motor Instruction Manual

> DAMIAO DM-H65 V1.1 Motor User Guide(including DM6540-1EC driver)&#x20;

[**DAMIAO DM-H65-1EC Motor**DAMIAO DM-H65-1EC Motor: BLDC hub motor with built-in inductive encoder. 6N·m rated, 21.5N·m peak torque. For embodied intelligence & versatile uses.openelab.io](https://openelab.io/products/damiao-brushless-servo-dm-h65)

## **Precautions** <a href="#block-34ed4c79856d80d9bf6ae0fa5efa51b4" id="block-34ed4c79856d80d9bf6ae0fa5efa51b4"></a>

1. Please strictly operate the motor within the specified working environment and the maximum allowable winding temperature range. Failure to do so may result in permanent and irreversible damage to the product.
2. Prevent foreign objects from entering the rotor; otherwise, abnormal rotor operation may occur.
3. Before use, check whether all components are intact. Do not use the product if any parts are missing, aged, or damaged.
4. Ensure correct wiring and that the motor is installed properly and securely.
5. Do not touch the electronic rotor section during operation to avoid accidents. The motor may become hot during high-torque output; be cautious to prevent burns.
6. Users must not disassemble the motor without authorization, as this may affect control accuracy or lead to abnormal operation.
7. The motor has a relatively large moment of inertia. It is recommended not to disable it directly when operating at high speeds. Instead, stop the motor by turning off the power or adjusting the control parameters.

## **Motor Features** <a href="#block-34ed4c79856d80e6b86cfa07e80b2b26" id="block-34ed4c79856d80e6b86cfa07e80b2b26"></a>

1. High-precision / high-resolution encoder.
2. Separate design of motor and driver. When replacing the driver, it can be used directly without the need for recalibration or parameter reconfiguration.
3. Supports host computer visual debugging and CAN parameter read/write.
4. Supports CAN FD with a maximum baud rate of 5 Mbps.
5. Can feedback motor speed, position, torque, motor temperature, and other information via the CAN bus.
6. Dual temperature protection function.
7. Supports CAN firmware upgrade.

## Specifications <a href="#block-34ed4c79856d80d89f7ccb043a47d517" id="block-34ed4c79856d80d89f7ccb043a47d517"></a>

Please operate the motor within the specifications listed below.

| Type                        | Characteristic Parameters    | Description                                                                                                                   |
| --------------------------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Motor parameters            | Rated Voltage                | 24V/36V/48V                                                                                                                   |
|                             | Rated Phase / Supply Current | 9.4A/5.10A@24V 9.4A/3.45A@36V 9.4A/2.56A@48V                                                                                  |
|                             | Peak Phase / Supply Current  | 33.6A/21.55A@24V 33.6A/14.00A@36V 33.6A/10.40A@48V                                                                            |
|                             | Rated Torque                 | 6.0Nm                                                                                                                         |
|                             | Peak Torque                  | 21.5Nm                                                                                                                        |
|                             | Rated speed                  | 120rpm                                                                                                                        |
|                             | Maximum No-Load Speed        | 260rpm@24V 395rpm@36V 480rpm@48V                                                                                              |
| Motor Characteristic Values | Number of slots              | 27                                                                                                                            |
|                             | Number of Pole Pairs         | 15                                                                                                                            |
|                             | Phase Inductance             | 750uH(@25℃)                                                                                                                   |
|                             | Phase Resistance             | 420Ω(@25℃)                                                                                                                    |
| Structure and Weight        | Outer Diameter               | 171mm                                                                                                                         |
|                             | Height                       | 66.3mm                                                                                                                        |
|                             | Motor Weight                 | 3150g                                                                                                                         |
| Encoder                     | Encoder Resolution           | 17bit                                                                                                                         |
|                             | Encoder accuracy             | ±0.05 degrees                                                                                                                 |
|                             | Number of Encoders           | 1                                                                                                                             |
| Communication Method        | Control interface type       | CAN@5Mbps(Max                                                                                                                 |
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

### **Operating Voltage** <a href="#block-34ed4c79856d80e58a7ad78826fc9d9e" id="block-34ed4c79856d80e58a7ad78826fc9d9e"></a>

The driver's operating voltage range is 24V to 48V. It is recommended to reduce hot-swapping when the voltage exceeds 36V. The minimum operating voltage is 20V, and the maximum operating voltage is 65V.

### **Maximum Phase Current** <a href="#block-34ed4c79856d80828856ccc622461771" id="block-34ed4c79856d80828856ccc622461771"></a>

The maximum phase current of the driver can be obtained from the startup serial output:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5e93d5f7-6b9b-4d0c-98f2-bff332a17fc8/image/w=1920,quality=90,fit=scale-down" alt="image" height="300.80816842388634" width="587.9874877929688">

The maximum phase current percentage can be limited by setting a percentage in the configuration tool. The default value is 0.8 (i.e., 80% of the measurable maximum current). It is recommended that this value not exceed 98%.

### **Sensor version** <a href="#block-34ed4c79856d801ca3a4f581a0b64bff" id="block-34ed4c79856d801ca3a4f581a0b64bff"></a>

You can check the encoder version currently used by the motor through the serial port print information when powering on. 'isensor' indicates the motor encoder, 'app' is the version number, and 'boot' refers to the bootloader serial number.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ed3ced03-b8db-4924-a8c2-0936b1cebd01/image/w=1920,quality=90,fit=scale-down" alt="image" height="472.0799221921515" width="737.5625">

### **Maximum Rotational Speed** <a href="#block-34ed4c79856d801d92bcea0d6591a409" id="block-34ed4c79856d801d92bcea0d6591a409"></a>

The maximum rotational speed is limited by multiple factors, including the supply voltage (V\_BUS) and the flux linkage (ψ\_f). An upper limit can typically be calculated using the following formula：

VMAX(rad/s)=0.57735×VBUSNpp×ψf(rad/s)VMAX​(rad/s)=0.57735×Npp​×ψf​VBUS​​(rad/s)

Where:

**V\_BUS：**&#x69;s the supply voltage,

**N\_pp：**&#x69;s the number of motor pole pairs,

**ψ\_f：**&#x72;epresents the rotor flux linkage.

### **Torque Constant** <a href="#block-34ed4c79856d80ebaadfdfb153cda6f1" id="block-34ed4c79856d80ebaadfdfb153cda6f1"></a>

The motor's torque coefficient can be considered constant within the rated range. After adding a gearbox, it can be calculated using the following formula:

K=15×Npp×ψfK=15×Npp​×ψf​

Where:

**N\_pp:** number of pole pairs

**ψ\_f:** rotor flux linkage

## **Packing List** <a href="#block-34ed4c79856d8020b4d8e68b0e062e9f" id="block-34ed4c79856d8020b4d8e68b0e062e9f"></a>

1\. Motor × 1

2\. Power connection cable: XT30 single-ended connector cable (200mm) × 1

3\. Debugging serial signal cable: GH1.25 3-pin cable (non-coplanar, 300mm) × 1

4\. CAN communication terminal: GH1.25 2-pin cable (non-coplanar, 300mm) × 1

5\. Driver × 1

## Interface & Pin Description <a href="#block-34ed4c79856d803bb6dcf85861291c51" id="block-34ed4c79856d803bb6dcf85861291c51"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8ab0af5f-378e-4303-a0ba-10ae52378dfe/image/w=1920,quality=90,fit=scale-down" alt="image" height="334.8575613474766" width="737.5499877929688">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1f283659-6611-4833-be12-0604a3146bc0/image/w=1920,quality=90,fit=scale-down" alt="image" height="178.03529411764706" width="409">

| Interface / Pin No.   | Instruction                                                                    |
| --------------------- | ------------------------------------------------------------------------------ |
| Encoder interface (1) | Used to connect the DM-H65 motor, using the matching 4-pin non-coplanar cable. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d433a117-54ec-4740-b38f-621e57a3a856/image/w=1920,quality=90,fit=scale-down" alt="image" height="143.32401802987215" width="404.9624938964844">

| Interface / Pin No.       | Instruction                                                           |
| ------------------------- | --------------------------------------------------------------------- |
| Three-phase interface (2) | Connect the three-phase wires from the motor to the driver interface. |

| Interface / Pin No.       | Instruction                                                                                                                                                                                                             |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor indicator light (3) | Red light constantly on: Motor is in a disabled state Green light constantly on: Motor is in an enabled state Red light flashing: Motor has reported an error — check the feedback frame to determine the specific type |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a9305d25-8b37-4763-90f0-398b6963fbcd/image/w=1920,quality=90,fit=scale-down" alt="image" height="306.82777855880465" width="372.9875183105469">

| Interface / Pin No.       | Instruction                                                                                                                                                                                                                 |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debugging Serial Port (4) | Connect to the PC via a GH1.25 cable (3-pin) using a USB-to-CAN debugging tool (or a general-purpose USB-to-serial module). Use the Damiao Tech Debug Assistant to configure motor parameters and perform firmware updates. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b177da98-0606-422d-94c4-311ad29e0da2/image/w=1920,quality=90,fit=scale-down" alt="image" height="299.49911823228655" width="416.9875183105469">

| Interface / Pin No. | Instruction                                                                                                                           |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Debug CAN Port (5)  | Connect to an external control device via a GH1.25 2-pin cable to receive CAN control commands and feedback motor status information. |
| Debug CAN Port (8)  |                                                                                                                                       |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/c74a8e1f-cb01-4bc3-8914-d6aad6a99fdb/image/w=1920,quality=90,fit=scale-down" alt="image" height="241.41527446300717" width="403">

| Interface / Pin No. | Instruction                                                                                                                                                                                                                                                                                                                      |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power Interface (6) | 1. Connect a power supply (rated voltage 24V) to the motor using a power cable with an XT30 connector to power the motor. 2. The motor driver includes two power interfaces. Either interface can be used independently for a single connection, or multiple units can be daisy-chained together, making wiring more convenient. |
| Power Interface (7) |                                                                                                                                                                                                                                                                                                                                  |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2b06874c-ac2b-4321-8744-e670b61a2714/image/w=1920,quality=90,fit=scale-down" alt="image" height="150.10861522746535" width="407.9875183105469">

| Interface / Pin No.             | Instruction                                                                       |
| ------------------------------- | --------------------------------------------------------------------------------- |
| Termination Resistor Switch (9) | The motor is configured with a termination resistor, which is enabled by default. |

## Motor Dimensions and Mounting <a href="#block-34ed4c79856d80458c7cd274ef5db5ac" id="block-34ed4c79856d80458c7cd274ef5db5ac"></a>

Please install the motor onto the target equipment according to the motor mounting hole dimensions and layout.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56287f4a-aaa2-48f7-835a-44eee38b22b9/image/w=1920,quality=90,fit=scale-down" alt="image" height="256.6474619684993" width="737.5499877929688">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d5810e4e-6d70-4651-9610-bc79ff290727/image/w=1920,quality=90,fit=scale-down" alt="image" height="382.31186572989856" width="737.5625">

## LED Status <a href="#block-34ed4c79856d807c970de2fbc1889cbc" id="block-34ed4c79856d807c970de2fbc1889cbc"></a>

| Normal Status | Solid Green  | Enable Mode (ERR = 1), normal operation                                                                                                                                                                                                                                                                                                                                                                 |
| ------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|               | Solid Red    | Disable Mode (ERR = 0)（Default state after power-on）                                                                                                                                                                                                                                                                                                                                                    |
| Fault Status  | Flashing Red | Indicates a fault. Corresponding fault types include: 5 – Motor encoder calibration abnormality 6 — Motor parameter read error; 7 — Sensor read exception 8 – Overvoltage 9 – Undervoltage A – Overcurrent B – MOS Overtemperature C – Motor Coil Overtemperature D – Communication Loss E – Overload You can check the fault type via the feedback frame or through the debugging assistant interface. |

## Operating Modes <a href="#block-34ed4c79856d80b0a755e0295dd017ce" id="block-34ed4c79856d80b0a755e0295dd017ce"></a>

### MIT Mode <a href="#block-34ed4c79856d80fca522ef9ba0f3ed25" id="block-34ed4c79856d80fca522ef9ba0f3ed25"></a>

MIT mode is designed to be compatible with the original MIT mode. It allows seamless switching while enabling flexible configuration of control ranges (P\_ MAX, V\_MAX, T\_MAX). The ESC converts received CAN data into control variables to calculate the torque value, which serves as the current reference for the current loop. The current loop then regulates to achieve the specified torque current. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Derived from the MIT mode, various control modes can be implemented. For example: When kp = 0 and kd ≠ 0, setting v\_des enables constant speed rotation; When kp = 0 and kd = 0, setting t\_ff enables constant torque output.

💡

Note: When controlling position, kd must not be set to **0**,  otherwise it may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-34ed4c79856d80c08401e1dff8b7c557" id="block-34ed4c79856d80c08401e1dff8b7c557"></a>

The position cascade mode adopts a three loop series control mode, where the position loop serves as the outermost loop and its output serves as the given value for the velocity loop, while the output of the velocity loop serves as the given value for the inner loop current loop, used to control the actual current output. The control schematic diagram is shown in the following figure:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** is the target position for control, and **v\_des** is used to limit the maximum absolute velocity during motion.

When the position cascade mode is controlled using the recommended control parameters from the debugging assistant, it can achieve good control accuracy. The control process is relatively smooth, but the response time is comparatively longer. In addition to **v\_des**, the configurable related parameters also include acceleration/deceleration settings. If additional oscillations occur during the control process, increasing the acceleration/deceleration can help mitigate them.

💡

**Note:** The units of **p\_des** and **v\_des** are **rad** and **rad/s**, respectively, and their data type is float. The damping factor must be set to a **positive non-zero number**. Please refer to the precautions for the velocity mode.

### Velocity Mode <a href="#block-34ed4c79856d80518a5af1ba0e1017c2" id="block-34ed4c79856d80518a5af1ba0e1017c2"></a>

Velocity mode allows the motor to run steadily at the set speed. The control block diagram is as follows:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

**Note:** v\_des is in rad/s, and its data type is float.

### **Force-Position Hybrid Control Mode** <a href="#block-34ed4c79856d80bf9a02df72a81c6e88" id="block-34ed4c79856d80bf9a02df72a81c6e88"></a>

The force-position hybrid control mode dynamically controls the output torque based on position-velocity mode control. Its control block diagram is shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4876b2d6-b47f-47a9-9dc7-20de651abc12/29e55681073b4ab3acd8adaf9b17c02e/w=1920,quality=90,fit=scale-down" alt="在这里插入图片描述" height="1000" width="1000">

A current command saturation stage is added after the output command of the speed loop, so that the input to the current loop is limited within the specified range.

### **Mode modification** <a href="#block-34ed4c79856d805c8480ff61271930a0" id="block-34ed4c79856d805c8480ff61271930a0"></a>

Mode switching can be configured via the host computer using the serial port. Simply select the desired mode and click "**Write Parameters**". After successful configuration using this method, the motor will automatically reset, and the mode will be stored inside the motor driver without being lost after power cycling.

Additionally, mode switching can also be performed via the CAN interface by modifying the content of the mode register. For details, refer to the "**Mode Switching**" subsection in the next chapter. When configured using this method, the motor will not reset, but the following five variables will be reset to zero:

1. Position command value
2. Velocity command value
3. Torque command value (MIT mode)
4. kp (MIT mode)
5. kd (MIT mode)

Without sending the "**Save Parameters**" command, the mode will not be stored and will be lost after power-off. When powered on again, the previously saved mode will be loaded.

## **CAN communication** <a href="#block-34ed4c79856d8044aae9d6d830041870" id="block-34ed4c79856d8044aae9d6d830041870"></a>

The motor can be used after completing calibration, parameter setting, and configuration. Control uses the CAN standard frame (STD) format, with a default baud rate of 1 Mbps. The baud rate can be changed using commands; _**see the CAN baud rate modification section for details**_**.** Functionally, frames can be divided into receive frames and feedback frames. Receive frames are the control data received, used to send commands to the motor. Feedback frames are the status data sent by the motor to the upper controller. The feedback mechanism is query-based: whenever a received frame ID matches the motor's configured CAN ID (the lower 8 bits are checked, the upper 3 bits are ignored), the driver sends the current status data to the bus. The receive frame format and frame ID vary depending on the selected motor mode, but the feedback frame is the same across all modes.

### **Modify baud rate** <a href="#block-34ed4c79856d8064861cf6295d2f4734" id="block-34ed4c79856d8064861cf6295d2f4734"></a>

The baud rate can be modified via the host computer using the serial port. Simply select the desired baud rate and click "Write Parameters". After successful configuration using this method, the motor will automatically reset, and the baud rate will be stored inside the motor driver without being lost after power cycling.

Another method is to modify the baud rate via the CAN interface by writing to the baud rate register. For details, see the _**"CAN Baud Rate Modification"**_ subsection in this chapter.

💡

**Note:** Modifying the baud rate via CAN will fail if there are multiple devices on the bus. Therefore, proceed with caution. It is strongly recommended to configure the baud rate before use.

### Feedback Frame <a href="#block-34ed4c79856d8098869be703f8b48987" id="block-34ed4c79856d8098869be703f8b48987"></a>

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

### Control Frame in MIT Mode <a href="#block-34ed4c79856d80f186b6d9f9e8183cc5" id="block-34ed4c79856d80f186b6d9f9e8183cc5"></a>

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

Position, velocity, and torque are preset to ±12.566, ±100, and ±40. These values can be adjusted according to the motor specifications. When sending control commands, the scaling ranges must remain consistent with the configured values.

### Control Frame in Position-Velocity Mode <a href="#block-34ed4c79856d801fbb20f8ae1d7b1c9c" id="block-34ed4c79856d801fbb20f8ae1d7b1c9c"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Desired position, float type, little-endian (low byte first, high byte last).
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x100 + ID. The velocity command represents the maximum velocity during trapezoidal acceleration, i.e., the constant velocity segment.

### Control Frame in Velocity Mode <a href="#block-34fd4c79856d8024acd1f5a58a4b2837" id="block-34fd4c79856d8024acd1f5a58a4b2837"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x200 + ID.

### **Control Frame in Force-Position Hybrid Control Mode** <a href="#block-34fd4c79856d805d87d9cc265d690fd4" id="block-34fd4c79856d805d87d9cc265d690fd4"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6]  | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ------ | ----- |
| 0x300+ID        | p\_des |       |       |       | v\_des |       | i\_des |       |

* **P\_des**: Desired position, in radians, float type, little-endian (low byte first, high byte last).
* **V\_des**: Velocity limit, in rad/s, scaled by 100, unsigned 16-bit, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual velocity limit range of 0-100 rad/s.
* **I\_des**: Torque current limit (per-unit), scaled by 10000, unsigned 16-bit type, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual current limit amplitude of 0-1.0.
* **Per-unit current:** Actual current divided by the maximum phase current.（See the electrical print above）

### **Enable** <a href="#block-34ed4c79856d80dfbb90e4c94937904b" id="block-34ed4c79856d80dfbb90e4c94937904b"></a>

After power-up self-test, an "Enable" command must be sent to allow motor control. The "Enable" frame is a control frame, with the frame ID as described above. The data payload is identical across all modes as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFC  |

### **Disable** <a href="#block-34fd4c79856d80648f29e4cc856a4eed" id="block-34fd4c79856d80648f29e4cc856a4eed"></a>

The default power-on state of the motor is "Disable." In this state, the three-phase terminal voltages are identical, each being a 50% modulation of the power supply voltage. The "Disable" frame is a control frame, with the frame ID as described above. The data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFD  |

### **Set Zero Position** <a href="#block-34fd4c79856d80ae9191db400e37dc75" id="block-34fd4c79856d80ae9191db400e37dc75"></a>

The "Set Zero Position" frame is a control frame. This command sets the current output shaft position as the zero reference and resets the position command value to 0. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFE  |

### **Clear Faults** <a href="#block-34fd4c79856d8021ba34e69e10f16831" id="block-34fd4c79856d8021ba34e69e10f16831"></a>

When faults such as overheating, sending a "Clear" can be sent to reset the fault state. The "Clear" frame is a control frame. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFB  |

### **Read parameters** <a href="#block-34fd4c79856d8084b255ef630dbea230" id="block-34fd4c79856d8084b255ef630dbea230"></a>

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

### **Write parameters** <a href="#block-34fd4c79856d80ad9ba4e541b507c7cc" id="block-34fd4c79856d80ad9ba4e541b507c7cc"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

RID is defined as above. Upon successful write, the written value is returned. The frame format is identical to the transmitted frame.

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

Writing register data takes effect immediately but are not stored; They will be lost upon power-off unless a "Save Parameters" command is issued to store them in internal memory

### **Save parameters** <a href="#block-34fd4c79856d803bbbd6e70ea8c7e496" id="block-34fd4c79856d803bbbd6e70ea8c7e496"></a>

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

### Mode Switching <a href="#block-34fd4c79856d80509481dba145ee6a30" id="block-34fd4c79856d80509481dba145ee6a30"></a>

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

### **CAN Baud Rate Configuration** <a href="#block-34fd4c79856d80fcba4dea336a9a832b" id="block-34fd4c79856d80fcba4dea336a9a832b"></a>

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

💡

**Note：**&#x4D;odifying the baud rate using CAN may fail when there are multiple devices on the bus. Therefore, proceed with caution. It is strongly recommended to configure the baud rate before assembling the system.

### **Register Map** <a href="#block-34fd4c79856d80f3a6e5f9f5ddd54f85" id="block-34fd4c79856d80f3a6e5f9f5ddd54f85"></a>

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
| 0x3F         | 63           | Iu\_off    | Phase U Current Offset            | RO  | /               | float  |
| 0x40         | 64           | Iv\_off    | Phase V Current Offset            | RO  | /               | float  |
| 0x41         | 65           | lw\_off    | Phase W Current Offset            | RO  | /               | float  |
| 0x50         | 80           | p\_m       | Motor Position                    | RO  | /               | float  |

💡

**Note:**

1. **RW:** Read/Write.
2. **RO:** Read-only.
