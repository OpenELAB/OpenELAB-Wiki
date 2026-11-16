# DAMIAO DM-JH11-2EC V1.0 Motor Instruction Manual

> DAMIAO DM-JH11-2EC V1.0 Motor User Guide

[**DAMIAO DM-JH11-2EC Motor**DAMIAO DM-JH11-2EC High-Perf Joint Module: 10.5/7.8N.m peak torque, harmonic reducer, dual encoders. For quadrupeds, humanoids & exoskeletons.mdmbot.com](https://www.mdmbot.com/index.php?c=show\&id=120)

## Safety Precautions <a href="#block-34dd4c79856d81a3b40bf1f4b10623a2" id="block-34dd4c79856d81a3b40bf1f4b10623a2"></a>

1. Strictly use the motor within the specified operating environment and maximum allowable winding temperature range; failure to do so may cause permanent and irreversible damage to the product.
2. Prevent foreign objects from entering the rotor interior; otherwise, abnormal rotor operation may occur.
3. Before use, check that all components are intact. If any part is missing, aged, damaged, etc., stop using the product.
4. Ensure correct wiring and that the motor is installed correctly and securely.
5. Do not touch the electronic rotor parts during operation to avoid accidents. The motor may heat up during high-torque output; be careful to avoid burns.
6. Do not disassemble the motor without authorization, as this may affect the control accuracy of the motor or even cause abnormal operation.
7. When using a host computer to control cyclic synchronous position, speed, or torque modes, the new host computer version 2.0.3.6 or higher is required.
8. Service life note: The service life of the harmonic reducer mainly depends on the wear of the wave generator bearing and the flexspline, as expressed by the formula.The theoretical service life of the reducer can be calculated using the formula:
9. Lav=Ln×(TrTav)×(NrNav)Lav​=Ln​×(Tav​Tr​​)×(Nav​Nr​​)
10. Where:
11. **Tr：**&#x69;s the rated torque of the reducer,
12. **Tav ：**&#x69;s the actual average load torque of the reducer,
13. **Nr：**&#x69;s the rated speed of the reducer,
14. **Nav：**&#x69;s the actual average operating speed of the reducer,
15. **Ln：**&#x69;s the design life of the reducer (theoretical value: 7000 hours).Torque overload behavior has a very serious impact on the service life of the reducer.
16. The harmonic reducer is a high-precision transmission component, and its flexspline and flexible bearing are extremely sensitive to load conditions. Any overload operation exceeding the rated parameters may lead to increased fatigue and shortened service life. Ensure that the harmonic joint module is used within the rated operating conditions. Damage to the flexspline or flexible bearing caused by prolonged overload or unexpected impact conditions is not covered under the company’s warranty.

## **Motor Features** <a href="#block-34dd4c79856d81299049f2e3dafb8419" id="block-34dd4c79856d81299049f2e3dafb8419"></a>

1. Dual encoders provide single-turn absolute position feedback at the output shaft, ensuring position information is retained even after power loss.
2. Integrated motor and driver design offers compact structure with high integration.
3. Supports PC-based configuration, monitoring, and firmware upgrades.
4. Supports CAN FD, with a maximum baud rate of 5Mbps.
5. Provides real-time feedback of motor Velocity, position, torque, and temperature via CAN bus.
6. Features dual temperature protection mechanisms.
7. CAN upgrade is supported.

## Specifications <a href="#block-34dd4c79856d81e29a01f0d1118df16b" id="block-34dd4c79856d81e29a01f0d1118df16b"></a>

Please operate the motor within the specifications listed below.

| Type                        | Characteristic Parameters    | DM-JH11-51-2EC                                                                                                                | DM-JH11-101-2EC                                                                                                               |
| --------------------------- | ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Motor parameters            | Rated Voltage                | 24V-48V                                                                                                                       | 24V-48V                                                                                                                       |
|                             | Rated Phase / Supply Current | 2.23A/1.19A@24V； 2.23A/0.54A@48V；                                                                                             | 2.3A/1.0A@24V； 2.3A/0.5A@48V；                                                                                                 |
|                             | Peak Phase / Supply Current  | 4.26A/4.25A@24V； 4.26A/1.85A@48V；                                                                                             | 3.6A/2.2A@24V； 3.6A/1.0A@48V；                                                                                                 |
|                             | Rated Torque                 | 3.2NM                                                                                                                         | 4.8NM                                                                                                                         |
|                             | Peak Torque                  | 7.8NM                                                                                                                         | 10.5NM                                                                                                                        |
|                             | Rated speed                  | 40rpm                                                                                                                         | 20rpm                                                                                                                         |
|                             | Maximum No-Load Speed        | 60rpm                                                                                                                         | 30rpm                                                                                                                         |
| Motor Characteristic Values | Reduction Ratio              | 51 : 1                                                                                                                        | 101：1                                                                                                                         |
|                             | Number of Pole Pairs         | 7                                                                                                                             | 7                                                                                                                             |
|                             | Phase Inductance             | 538uH(@25℃)                                                                                                                   | 538uH(@25℃)                                                                                                                   |
|                             | Phase Resistance             | 1.1Ω(@25℃)                                                                                                                    | 1.1Ω(@25℃)                                                                                                                    |
| Structure and Weight        | Outer Diameter               | 52mm                                                                                                                          | 52mm                                                                                                                          |
|                             | Height                       | 60mm                                                                                                                          | 60mm                                                                                                                          |
|                             | Central hole size            | 8.5mm                                                                                                                         | 8.5mm                                                                                                                         |
|                             | Motor Weight                 | 345g                                                                                                                          | 345g                                                                                                                          |
| Encoder                     | Encoder Resolution           | 17bit                                                                                                                         | 17bit                                                                                                                         |
|                             | Number of Encoders           | 2                                                                                                                             | 2                                                                                                                             |
|                             | Encoder Type                 | Double editor (single circle)                                                                                                 | Double editor (single circle)                                                                                                 |
| Communication Method        | Control interface type       | CAN@5Mbps(Max)                                                                                                                | CAN@5Mbps(Max)                                                                                                                |
|                             | Parameter Tuning Interface   | UART@921600bps                                                                                                                | UART@921600bps                                                                                                                |
| Control and Protection      | Control Mode                 | MIT Mode                                                                                                                      | MIT Mode                                                                                                                      |
|                             |                              | Velocity Mode                                                                                                                 | Velocity Mode                                                                                                                 |
|                             |                              | Position Mode                                                                                                                 | Position Mode                                                                                                                 |
|                             |                              | Force-Position Hybrid Control Mode                                                                                            | Force-Position Hybrid Control Mode                                                                                            |
|                             |                              | Periodic Synchronous Position Mode                                                                                            | Periodic Synchronous Position Mode                                                                                            |
|                             |                              | Cycle Synchronization Speed Mode                                                                                              | Cycle Synchronization Speed Mode                                                                                              |
|                             |                              | periodic synchronous torque mode                                                                                              | periodic synchronous torque mode                                                                                              |
|                             | Protection                   | Drive over-temperature protection: shutdown at 100° C; the motor exits Enable Mode when triggered.                            | Drive over-temperature protection: shutdown at 100° C; the motor exits Enable Mode when triggered.                            |
|                             |                              | Motor over-temperature protection (configurable, recommended ≤ 90° C); the motor exits Enable Mode when triggered.            | Motor over-temperature protection (configurable, recommended ≤ 90° C); the motor exits Enable Mode when triggered.            |
|                             |                              | Over-voltage protection(configurable, recommended ≤ 54V); exits Enable Mode when triggered.                                   | Over-voltage protection(configurable, recommended ≤ 54V); exits Enable Mode when triggered.                                   |
|                             |                              | Communication Loss Protection: the motor exits Enable Mode if no CAN command is received within the specified timeout period. | Communication Loss Protection: the motor exits Enable Mode if no CAN command is received within the specified timeout period. |
|                             |                              | Over-current protection (configurable, recommended ≤ 0.98A); exits Enable Mode when triggered.                                | Over-current protection (configurable, recommended ≤ 0.98A); exits Enable Mode when triggered.                                |
|                             |                              | Under-voltage protection: the motor exits Enable Mode if supply voltage falls below the threshold (recommended ≥ 20V).        | Under-voltage protection: the motor exits Enable Mode if supply voltage falls below the threshold (recommended ≥ 20V).        |

### **Operating Voltage** <a href="#block-34dd4c79856d8154afb3f4f7f728e5d0" id="block-34dd4c79856d8154afb3f4f7f728e5d0"></a>

The operating voltage range of the drive is 24V to 48V. It is recommended to reduce hot-plugging when the voltage exceeds 36V. The minimum operating voltage is 20V, and the maximum operating voltage is 54V.

### **Maximum Phase Current** <a href="#block-34dd4c79856d8138abace7f2737ba4aa" id="block-34dd4c79856d8138abace7f2737ba4aa"></a>

The maximum phase current of the driver can be obtained from the startup serial output:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8c1e7b92-0660-4935-90aa-7ef1530cf889/image/w=1920,quality=90,fit=scale-down" alt="image" height="350.8720292650172" width="466.07501220703125">

The maximum phase current percentage can be limited by setting a percentage in the configuration tool. The default value is 0.8 (i.e., 80% of the measurable maximum current). It is recommended that this value not exceed 98%.

### **Encoder version** <a href="#block-34dd4c79856d80fd9b9bd762fa038be7" id="block-34dd4c79856d80fd9b9bd762fa038be7"></a>

The encoder version currently used by the motor can be queried through the serial port print information during power-on. “isensor” represents the encoder at the motor rotor side, “osensor” represents the encoder at the output shaft side, “app” indicates the version number, and “boot” refers to the bootloader serial number.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/25efe49f-f004-4c75-a94e-77946f7a3a27/image/w=1920,quality=90,fit=scale-down" alt="image" height="390.4247770167109" width="466.07501220703125">

### **Maximum Rotational Speed** <a href="#block-34dd4c79856d814dae5bdd14510d3074" id="block-34dd4c79856d814dae5bdd14510d3074"></a>

The maximum rotational speed is limited by multiple factors, including the power supply voltage (VBUS), rotor flux linkage (ψf), and gear ratio (GR). An upper limit can usually be calculated using the formula below. During operation, the speed is limited to 2000 rpm (rotor side).

VMAX(rad/s)=0.57735∗VBUSNpp×GR×ψf(rad/s)VMAX​(rad/s)=0.57735∗Npp​×GR×ψf​VBUS​​(rad/s)

where VBUS is the supply voltage, Npp is the number of pole pairs, and ψf is the rotor flux linkage.

### **Torque Constant** <a href="#block-34dd4c79856d8179aa20f30e5340fdb8" id="block-34dd4c79856d8179aa20f30e5340fdb8"></a>

The torque constant of the motor can be considered constant within its rated range. With a gearbox, it can be calculated using the following formula:

Kt=1.5∗Npp∗ψf∗GR∗GREFKt​=1.5∗Npp​∗ψf​∗GR∗GREF

Where Npp is the number of pole pairs, ψf is the rotor flux linkage, GR is the gear ratio, and GREF is the gearbox torque transmission coefficient.

## **Packing List** <a href="#block-800850789a974b13a0aab345a499abf1" id="block-800850789a974b13a0aab345a499abf1"></a>

1. Motor (with integrated driver) ×1
2. Power cable (with CAN interface) : SH1.0 cable 8-pin (200mm) ×1
3. Debug serial cable: SH1.0 cable 3-pin (200mm) ×1

## Interface & Pin Description <a href="#block-34dd4c79856d815da6a0e6efed75f41b" id="block-34dd4c79856d815da6a0e6efed75f41b"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5fcd84eb-ae66-4879-ba2d-0bf5afb975a1/image/w=1920,quality=90,fit=scale-down" alt="image" height="228.94912880345393" width="466.07501220703125">

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d39364c2-6b13-4026-9128-1cef8e1fbfb4/image/w=1920,quality=90,fit=scale-down" alt="image" height="224.33403414212742" width="633.9874877929688">

| Interface / Pin No.                       | Instruction                                                                                                                                                                                                                                                                          |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Power + CAN Communication Terminal(1) (2) | 1. Connect the power supply using an SH1.0 8-pin power cable. The rated voltage is 24V (supports 24–48V) to supply power to the motor. 2. Connect external control devices via the CAN communication terminal to receive CAN control commands and feedback motor status information. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/05e7b5fb-819a-42fe-b992-1787a82984e2/image/w=1920,quality=90,fit=scale-down" alt="image" height="272.22080287441315" width="642.9874877929688">

| Interface / Pin No.            | Instruction                                                                                                                                                                                                                                                                                                         |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Debug Serial Interface(Port 3) | Connect using an SH1.0 3-pin cable and an intermediate adapter board (SH1.0 3-pin + 8-pin to XT30 + GH1.25). Use a USB-to-CAN debugging tool (or a general-purpose USB-to-serial module) to connect to a PC. Use the Damiao Technology Debug Assistant to configure motor parameters and perform firmware upgrades. |

| Interface / Pin No.      | Instruction                                                                                                                                                                                                                                                                                                                                                                         |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Motor Indicator Light(5) | **Red light always on:** Motor is in the disabled state. **Green light always on:** Motor is in the enabled state. **Red light flashing:** Motor has reported an error. Check the feedback frame to determine the specific error type. **Green light flashing:** Motor power-on self-test failed. Take a screenshot of the power-on print information and contact customer service. |

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cdc1188d-16d7-4d47-b563-aff46a9dc2c5/image/w=1920,quality=90,fit=scale-down" alt="image" height="109.64696262904575" width="403.9624938964844">

| Interface / Pin No.            | Instruction                                                                     |
| ------------------------------ | ------------------------------------------------------------------------------- |
| Termination Resistor Switch(4) | The motor is equipped with a termination resistor, which is enabled by default. |

💡

## Motor Dimensions and Mounting <a href="#block-34dd4c79856d811bb12ce4f06e619ff4" id="block-34dd4c79856d811bb12ce4f06e619ff4"></a>

Please install the motor onto the target equipment according to the motor mounting hole dimensions and layout.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/15cd30d9-1b8e-4bf5-97d6-fe90610efb52/image/w=1920,quality=90,fit=scale-down" alt="image" height="228.8100683510709" width="466.07501220703125">

## LED Status <a href="#block-34dd4c79856d8158b2b6c4f2bf00c19c" id="block-34dd4c79856d8158b2b6c4f2bf00c19c"></a>

| Normal Status | Solid Green  | Enable Mode (ERR = 1), normal operation                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|               | Solid Red    | Disable Mode (ERR = 0)（Default state after power-on）                                                                                                                                                                                                                                                                                                                                                                                                                      |
| Fault Status  | Flashing Red | Fault codes and fault conditions: **2** – Motor-side encoder not recognized **3** – Output shaft encoder not recognized **5** – Motor encoder calibration error; **8** – Over-voltage; **9** – Under-voltage; **A** – Over-current; **B** – MOS over-temperature; **C** – Motor winding over-temperature; **D** – Communication loss; **E** – Overload; Fault conditions can be identified via the feedback frames or displayed in the the Damiao configuration software. |

## Operating Modes <a href="#block-34dd4c79856d81eda2afc3dd3e63f08f" id="block-34dd4c79856d81eda2afc3dd3e63f08f"></a>

### MIT Mode <a href="#block-34dd4c79856d81e88189e2138f8f783a" id="block-34dd4c79856d81e88189e2138f8f783a"></a>

The MIT mode is compatible with the standard MIT control method, enabling seamless switching while allowing flexible configuration of control limits (P\_MAX, V\_MAX, T\_MAX).The electronic speed controller (ESC) converts the received CAN data into control variables and calculates a torque value, which is used as the current reference for the current loop. The current loop then follows its regulation scheme to ultimately achieve the given torque current.

(This motor features a newly added speed limiter, which prevents the motor from exceeding the maximum allowable speed.) The control block diagram is shown below:

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/00117941-abb0-4c2d-a480-b0a9f2c67cde/image/w=1920,quality=90,fit=scale-down" alt="image" height="800" width="2302">

Based on the MIT model, various control strategies can be derived. For instance, when kp=0 and kd ≠ 0, a constant rotational speed can be achieved by setting v\_des. When kp=0 and kd=0, a torque output is applied directly by setting t\_ff (feedforward torque).

💡

**Note:** When controlling position, kd must not be set to zero, as this may cause motor oscillation or even loss of control.

### Position-Velocity Mode <a href="#block-34dd4c79856d816b8627c91940454650" id="block-34dd4c79856d816b8627c91940454650"></a>

This mode uses three control loops: position, velocity, and current(torque). The position loop sets the target for the velocity loop. The velocity loop then sets the target for the current loop. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/56b13752-f58a-45bb-b4fa-65c97c1907dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="724" width="2388">

**p\_des** represents the target position, while **v\_des** limits the maximum absolute velocity during motion.

When tuned using recommended parameters from the configuration tool, this mode provides high accuracy and smooth motion, at the cost of slower response time.

In addition to **v\_des**, acceleration and deceleration can also be configured. If additional oscillations occur, increasing acceleration/deceleration may help stabilize the system.

💡

**Note:** The units of p\_des and v\_des are rad and rad/s respectively, and both are of type float. The damping factor must be set to a non-zero positive value.Refer to the notes for velocity mode.

### Velocity Mode <a href="#block-34dd4c79856d81aebc6ddcda945d7398" id="block-34dd4c79856d81aebc6ddcda945d7398"></a>

This mode keeps the motor running at the target velocity. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f62dd1a2-b3e2-475b-adc3-36a96bf967c6/image/w=1920,quality=90,fit=scale-down" alt="image" height="246.74509803921566" width="624">

💡

**Note:** v\_des is in rad/s, and the data type is float.

### **Force-Position Hybrid Mode** <a href="#block-34dd4c79856d81d3ab10c3be4b77665b" id="block-34dd4c79856d81d3ab10c3be4b77665b"></a>

The force-position hybrid control mode is based on position-velocity control, with additional torque adjustment. Allows control of both position and output torque at the same time. See block diagram below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/4876b2d6-b47f-47a9-9dc7-20de651abc12/29e55681073b4ab3acd8adaf9b17c02e/w=1920,quality=90,fit=scale-down" alt="在这里插入图片描述" height="1000" width="1000">

A current command saturation stage is added after the velocity loop output command. This limits the current loop reference within the specified range.

### **Cyclic Synchronous Position Mode (CSP)** <a href="#block-19f4c345952046719c75b6fc4cdea6cc" id="block-19f4c345952046719c75b6fc4cdea6cc"></a>

In this mode, absolute position preset values are sent to the controller via the fieldbus at fixed time intervals (referred to as the “cycle”). In this case, the controller no longer calculates the ramp; it simply follows the preset values to execute motion. The control block diagram is shown in the figure below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/43f1bf56-c8e4-4b0d-94b6-41991d8fc3d2/image/w=1920,quality=90,fit=scale-down" alt="image" height="140.34836647727272" width="466.0625">

In this mode, position commands should be issued in a gradually progressive manner. Avoid sending abrupt or sudden position commands; otherwise, motor vibration may occur (this mode has input parameter limits). Upper-level trajectory planning should be performed, and the planned trajectory should be sent to the motor incrementally.

### **Cyclic Synchronous Velocity Mode (CSV)** <a href="#block-cf2d7603c5784aeb908cc18f8bfd8e38" id="block-cf2d7603c5784aeb908cc18f8bfd8e38"></a>

In Cyclic Synchronous Velocity Mode (CSV), the host controller periodically and synchronously sends the calculated target velocity to the servo drive. The velocity and torque regulation are executed internally by the servo drive. The control block diagram is shown in the figure below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/16a7385a-c3e1-42c8-bc91-68d00113f5e1/image/w=1920,quality=90,fit=scale-down" alt="image" height="187.13617914373222" width="466.07501220703125">

In this mode, position commands should be issued in a gradually progressive manner. Avoid sending abrupt or sudden position commands; otherwise, motor vibration may occur (this mode has input parameter limits). Upper-level trajectory planning should be performed, and the planned trajectory should be sent to the motor incrementally.

### **Cyclic Synchronous Torque Mode (CST)** <a href="#block-1c470aba7eaa47249f47fbdb9e0ef9ae" id="block-1c470aba7eaa47249f47fbdb9e0ef9ae"></a>

In Cyclic Synchronous Torque Mode (CST), the host controller periodically and synchronously sends the calculated target torque to the servo drive. Torque regulation is executed internally by the servo drive. When the speed reaches the limit value, the drive enters the speed regulation phase. The control block diagram is shown in the figure below.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a51215c1-904d-4b16-84de-3138cfd95623/image/w=1920,quality=90,fit=scale-down" alt="image" height="149.20913164400494" width="466.0625">

In this mode, torque commands should be issued in a gradually progressive manner. Avoid sending abrupt or sudden torque commands; otherwise, motor vibration may occur (this mode has input parameter limits). Upper-level trajectory planning should be performed, and the planned trajectory should be sent to the motor incrementally.

### **Mode Switching** <a href="#block-34dd4c79856d811cb4ebd9da0e8897fc" id="block-34dd4c79856d811cb4ebd9da0e8897fc"></a>

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

## **CAN communication** <a href="#block-34dd4c79856d81f8b08bcc76aabdb877" id="block-34dd4c79856d81f8b08bcc76aabdb877"></a>

The motor can be used after completing calibration, parameter setting, and configuration. Control uses the CAN standard frame (STD) format, with a default baud rate of 1 Mbps. The baud rate can be changed using commands; refer to the CAN Baud Rate Modification section for details. Functionally, frames can be divided into receive frames and feedback frames. Receive frames are the control data received for commanding the motor. Feedback frames are the status data sent by the motor to the host controller. The feedback mechanism is query-based: whenever the drive receives a frame whose ID matches the motor’s configured CAN ID (the lower 8 bits are checked for matching, while the upper 3 bits are ignored), the drive transmits the current status data onto the bus. Depending on the selected mode of the motor, the receive frame format and frame ID vary, but the feedback frame is the same across all modes.

### **CAN Baud Rate Configuration** <a href="#block-34dd4c79856d81618bdcf3314b97e90e" id="block-34dd4c79856d81618bdcf3314b97e90e"></a>

The baud rate can be modified using the host computer via the serial port. Simply select the desired baud rate and click “Write Parameter”. After successful configuration using this method, the motor will automatically reset, and the baud rate will be stored inside the motor driver. The setting will not be lost after power cycling.

Another method is to modify the baud rate via the CAN interface by writing to the baud rate register. Refer to the “CAN Baud Rate Modification” subsection in this chapter for details.

💡

**Note:** Modifying the baud rate via CAN may fail when multiple devices are present on the bus. Therefore, proceed with caution. It is strongly recommended to configure the baud rate before system integration.

Use this method with caution. It is strongly recommended to configure the baud rate before connecting multiple devices.

### Feedback Frame <a href="#block-34dd4c79856d817fa852f2484606649a" id="block-34dd4c79856d817fa852f2484606649a"></a>

The feedback frame ID is set via the configuration tool (Master ID), with a default value of 0. It primarily reports the motor position, velocity, and torque with the frame format defined as follows:

| Feedback Message | D\[0]      | D\[1]      | D\[2]     | D\[3]      | D\[4]                 | D\[5]   | D\[6]  | D\[7]    |
| ---------------- | ---------- | ---------- | --------- | ---------- | --------------------- | ------- | ------ | -------- |
| MST\_ID          | ID\|ERR<<4 | POS\[15:8] | POS\[7:0] | VEL\[11:4] | VEL\[3:0] \| T\[11:8] | T\[7:0] | T\_MOS | T\_Rotor |

Where:

1. **ID:** Controller ID, using the lower 8 bits of CAN\_ID
2. **ERR :** Status code, with the following meanings
3. **0** – Disabled（Default state after power-on）
4. **1** – Enabled
5. **2** – Motor-side encoder not recognized **3** – Output shaft encoder not recognized
6. **5** – Motor encoder calibration error;
7. **8** — Over-voltage
8. **9** — Under-voltage
9. **A** — Over-current
10. **B** — MOSFET over-temperature
11. **C** — Motor coil over-temperature
12. **D** — Communication loss
13. **E** — Overload
14. **POS** : Motor position
15. **VEL** : Motor velocity
16. **T** : Motor torque
17. **T\_MOS** : Average MOSFET temperature on the driver (℃ )
18. **T\_Rotor** : Average motor coil temperature (℃ )

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

### Control Frame in MIT Mode <a href="#block-34dd4c79856d81768453ff389eb22390" id="block-34dd4c79856d81768453ff389eb22390"></a>

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

Position, velocity, and torque are preset to ±12.5, ±10, and ±12. These values can be adjusted according to the motor specifications. When sending control commands, the scaling ranges must remain consistent with the configured values.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/fbf8154a-c38a-4db9-8720-59a0f33c2f96/image/w=1920,quality=90,fit=scale-down" alt="image" height="303.9765245325425" width="323.9875183105469">

### Control Frame in Position-Velocity Mode <a href="#block-34dd4c79856d8169a8dbce25fe4ac1f3" id="block-34dd4c79856d8169a8dbce25fe4ac1f3"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x100+ID        | p\_des |       |       |       | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x100.
* **p\_des**: Desired position, float type, little-endian (low byte first, high byte last).
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x100 + ID. The velocity command represents the maximum velocity during trapezoidal acceleration, i.e., the constant velocity segment.

### Control Frame in Velocity Mode <a href="#block-34dd4c79856d81a89f0df09a28a7efd4" id="block-34dd4c79856d81a89f0df09a28a7efd4"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x200+ID        | v\_des |       |       |       |

* **Frame ID**: equals the configured CAN ID plus an offset of 0x200.
* **v\_des**: Desired velocity, float type, little-endian (low byte first, high byte last).

The CAN ID used to send commands here is 0x200 + ID.

### **Control Frame in Force-Position Hybrid Control Mode** <a href="#block-34dd4c79856d81988c85d395f9e9ad1d" id="block-34dd4c79856d81988c85d395f9e9ad1d"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6]  | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ------ | ----- |
| 0x300+ID        | p\_des |       |       |       | v\_des |       | i\_des |       |

* **P\_des**: Desired position, in radians, float type, little-endian (low byte first, high byte last).
* **V\_des**: Velocity limit, in rad/s, scaled by 100, unsigned 16-bit, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual velocity limit range of 0-100 rad/s.
* **I\_des**: Torque current limit (per-unit), scaled by 10000, unsigned 16-bit type, little-endian (low byte first, high byte last). Valid range: 0-10000. Values exceeding 10000 are capped at 10000, corresponding to an actual current limit amplitude of 0-1.0.
* **Per-unit current:** Actual current divided by the maximum phase current.

### **Control Frame in Cyclic Synchronous Velocity-Position Mode** <a href="#block-c237f253d61e4e949be5e057082b7cc8" id="block-c237f253d61e4e949be5e057082b7cc8"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] | D\[4]  | D\[5] | D\[6] | D\[7] |
| --------------- | ------ | ----- | ----- | ----- | ------ | ----- | ----- | ----- |
| 0x400+ID        | p\_des |       |       |       | v\_des |       |       |       |

The frame ID is the configured CAN ID value plus an offset of 0x400.

* **p\_des:** Position command, floating-point type, little-endian (low byte first, high byte after).
* **v\_des:** Velocity command, floating-point type, little-endian (low byte first, high byte after).

The CAN ID for sending commands here is 0x400 + ID. The velocity command is the maximum speed limit during operation.

### **Control Frame in Cyclic Synchronous Velocity Mode (CSV)** <a href="#block-d18ac28bd7554f88a221cf89612bb615" id="block-d18ac28bd7554f88a221cf89612bb615"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x500+ID        | v\_des |       |       |       |

The frame ID is the configured CAN ID value plus an offset of 0x500.

* **v\_des:** Velocity command, floating-point type, little-endian (low byte first, high byte after).

The CAN ID for sending commands here is 0x500 + ID.

### **Control Frame in Cyclic Synchronous Torque Mode (CST)** <a href="#block-82155383d8034420aa38fe7a61ee35f4" id="block-82155383d8034420aa38fe7a61ee35f4"></a>

| Control Message | D\[0]  | D\[1] | D\[2] | D\[3] |
| --------------- | ------ | ----- | ----- | ----- |
| 0x600+ID        | t\_des |       |       |       |

The frame ID is the configured CAN ID value plus an offset of 0x600.

* **t\_des:** Torque command, floating-point type, little-endian (low byte first, high byte after).

The CAN ID for sending commands here is 0x600 + ID.

### **Enable** <a href="#block-34dd4c79856d8178872cd2348fa84fa0" id="block-34dd4c79856d8178872cd2348fa84fa0"></a>

After power-up self-test, an "Enable" command must be sent to allow motor control. The "Enable" frame is a control frame, with the frame ID as described above. The data payload is identical across all modes as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFC  |

### **Disable** <a href="#block-34dd4c79856d8125a635f08db78d222b" id="block-34dd4c79856d8125a635f08db78d222b"></a>

The default power-on state of the motor is "Disable." In this state, the three-phase terminal voltages are identical, each being a 50% modulation of the power supply voltage. The "Disable" frame is a control frame, with the frame ID as described above. The data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFD  |

### **Set Zero Position** <a href="#block-34dd4c79856d815caa71cd043e26d44c" id="block-34dd4c79856d815caa71cd043e26d44c"></a>

The "Set Zero Position" frame is a control frame. This command sets the current output shaft position as the zero reference and resets the position command value to 0. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFE  |

### **Clear Faults** <a href="#block-34dd4c79856d81e69607e7b7469085a2" id="block-34dd4c79856d81e69607e7b7469085a2"></a>

When faults such as overheating, sending a "Clear" can be sent to reset the fault state. The "Clear" frame is a control frame. The frame ID follows the definition above, and the data payload is defined as follows:

| D\[0] | D\[1] | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFF  | 0xFB  |

### **Read parameters** <a href="#block-34dd4c79856d8139ab4ff1cff937faf7" id="block-34dd4c79856d8139ab4ff1cff937faf7"></a>

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

### **Write parameters** <a href="#block-34dd4c79856d81f886acd6100f4c0be4" id="block-34dd4c79856d81f886acd6100f4c0be4"></a>

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| 0x7FF      | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

RID is defined as above. Upon successful write, the written value is returned. The frame format is identical to the transmitted frame.

| Message ID | Attribute | D\[0]    | D\[1]    | D\[2] | D\[3] | D\[4] | D\[5] | D\[6] | D\[7] |
| ---------- | --------- | -------- | -------- | ----- | ----- | ----- | ----- | ----- | ----- |
| MST\_ID    | STD       | CANID\_L | CANID\_H | 0x55  | RID   | data  |       |       |       |

Writing register data takes effect immediately but are not stored; They will be lost upon power-off unless a "Save Parameters" command is issued to store them in internal memory

### **Save parameters** <a href="#block-34dd4c79856d81a08675ce0021a68569" id="block-34dd4c79856d81a08675ce0021a68569"></a>

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

### Mode Switching <a href="#block-34dd4c79856d81268c15ff45ffc33654" id="block-34dd4c79856d81268c15ff45ffc33654"></a>

Multiple control modes are supported and can be switched as follows:

| **Encoding** | **Mode**                           |
| ------------ | ---------------------------------- |
| 1            | MIT                                |
| 2            | Position-Velocity Mode             |
| 3            | Velocity Mode                      |
| 4            | Force-Position Hybrid Control Mode |
| 5            | Cyclic Synchronous Position Mode   |
| 6            | Cyclic Synchronous Velocity Mode   |
| 7            | Cyclic Synchronous Torque Mode     |

The mode can be changed by modifying the mode register (0x0A). During switching, the motor resets all command values to zero, including position, velocity, and torque feed-forward, KP, and KD in MIT mode.

When switching to a position control mode, to avoid impact, it is recommended to first read the precise position (value in register 0x50) and perform the switch when the motor is at zero speed whenever possible.

Mode changes are not saved to flash memory and will be lost after power-off. Upon restart, the motor loads the last mode stored in flash.

### **CAN Baud Rate Configuration** <a href="#block-34dd4c79856d810fb5d4e44f9ee0d922" id="block-34dd4c79856d810fb5d4e44f9ee0d922"></a>

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

### **Register Map** <a href="#block-34dd4c79856d8119b3aee3ac3e2363cc" id="block-34dd4c79856d8119b3aee3ac3e2363cc"></a>

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
| 0x25         | 37           | Boot\_ver  | Boot Version                      | RO  | /               | uint32 |
| 0x36         | 54           | x\_off     | Output shaft angle deviation      | RO  | /               | float  |
| 0x37         | 55           | dir        | Direction                         | RO  | /               | float  |
| 0x38         | 56           | m\_off     | Motor-side Angle Offset           | RO  | /               | float  |
| 0x3C         | 60           | VBus       | Bus Voltage                       | RO  | /               | float  |
| 0x50         | 80           | p\_m       | Motor Position                    | RO  | /               | float  |
| 0x51         | 81           | xout       | Output Shaft Position             | RO  | /               | float  |

💡

**Note:**

1. **RW:** Read/Write.
2. **RO:** Read-only.

## Host Computer Guide <a href="#block-34dd4c79856d8179b2abcd42e7e366ae" id="block-34dd4c79856d8179b2abcd42e7e366ae"></a>

[DAMIAO Host Computer User Manual](https://wiki.openelab.io/damiao/damiao-host-computer-user-manual)
