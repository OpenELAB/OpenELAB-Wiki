# RobStride 03 Instruction Manual

> 60N.M Quasi-Direct Drive Integrated Motor Module User Manual

[**ROBSTRIDE 03 Motor**ROBSTRIDE03:60Nm quasi-direct drive with advanced motor controller\&closed-loop thermal control.Engineered for industrial robots,cobots and automation systems.openelab.io](https://openelab.io/products/robstride03-qdd-60n-m-integrated-joint-motor-module)

## Precautions <a href="#block-33cd4c79856d813692d4ee380197fd3f" id="block-33cd4c79856d813692d4ee380197fd3f"></a>

1. Please use according to the working parameters specified in this article, otherwise it may cause serious damage to the product!
2. Do not switch the control mode when the joint is running. If you need to switch, send the command to stop the operation before switching.
3. Check whether the parts are in good condition before use. If the parts are missing or damaged, contact technical support in time.
4. Do not disassemble the motor at will, so as to avoid unrecoverable failure.
5. Ensure that there is no short circuit when the motor is connected, and the interface is correctly connected as required.

## 1. Motor specification <a href="#block-33cd4c79856d81c1910fec45e93390b4" id="block-33cd4c79856d81c1910fec45e93390b4"></a>

### 1.1 Outline and mounting dimensions <a href="#block-33cd4c79856d810a9b0ac5bad2852dfd" id="block-33cd4c79856d810a9b0ac5bad2852dfd"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/cc4686e7-cbb5-4946-a5ee-75f2a71549d9/image/w=1920,quality=90,fit=scale-down" alt="image" height="956" width="2488">

When fixing, the screw depth should not exceed the depth of the casing thread.

### 1.2 Standard service condition <a href="#block-33cd4c79856d8140be2aeb95362caf38" id="block-33cd4c79856d8140be2aeb95362caf38"></a>

1. Rated voltage: 48 VDC
2. Operating voltage range: 24V-60 VDC
3. Rated load (CW) : 20 N.m (Heat sink dimensions: 215mm × 220mm)
4. Operation direction: CW/CCW from the direction of the exit shaft
5. Use posture: the direction of the exit axis is horizontal or vertical
6. Standard operating temperature: 25±5℃
7. Operating temperature range: -20 \~ 50℃
8. Standard operating humidity: 65%
9. Humidity range: 5 \~ 85%, no condensation
10. Storage temperature range: -30 \~ 70℃
11. Insulation Class: Class B

### 1.3 Electrical characteristic <a href="#block-33cd4c79856d81b581bcf0e01b8df840" id="block-33cd4c79856d81b581bcf0e01b8df840"></a>

1. No load speed: 200 rpm±10%
2. No-load current: 2 Arms
3. Rated load: 20 N.m
4. Rated load speed: 100rpm±10%
5. Rated load phase current (peak) : 13Apk±10%
6. Peak load: 60 N.m
7. Maximum load phase current (peak) : 43Apk±10%
8. Insulation resistance/stator winding: DC 500VAC, 100M Ohms
9. High voltage/stator and housing: 600 VAC, 1s, 2mA
10. Motor back potential: 17Vrms/krpm±10%
11. Torque constant(Valid value): 2.36N.m/Arms
12. T-N curve (36V)
13.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/02fde610-4bf2-4d9f-9708-94870be1fa5c/image/w=1920,quality=90,fit=scale-down" alt="image" height="302.86586695747" width="528">
14. Maximum overload curve
15. Test conditions: Ambient temperature: 25℃ Winding limit temperature: 135℃ (this is the constraint temperature, the actual is 180 degrees) Speed: 24rpm
16.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a5aab53c-16c2-4519-86e8-f20955ab9392/image/w=1920,quality=90,fit=scale-down" alt="image" height="249.94988610478362" width="576">
17. Test data
18.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9c38b587-5127-4275-9859-d4820118bc81/image/w=1920,quality=90,fit=scale-down" alt="image" height="156.85714285714283" width="288">
19. Thermal testing Test Conditions:
20. Heat sink size: 215mm x 220mm Ambient temperature: 25℃ Winding protection temperature: 145℃
21. Test condition 1: Motor rotates at 100rpm, monitor the motor thermistor temperature, and record the time it takes for the motor thermistor temperature to rise from 25℃ to 145℃.
22.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/04929037-fc2d-441a-a7f2-5bef46d08360/image/w=1920,quality=90,fit=scale-down" alt="image" height="157.41935483870967" width="288">
23. Motor locked-rotor condition 2: According to the current formula, the average phase current during locked-rotor is approximately 1.414 times that of rotation. This is used to obtain the overload time table for the locked-rotor condition.
24.

    <img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/2f439a84-3068-40af-80a6-00f1269e7eb0/image/w=1920,quality=90,fit=scale-down" alt="image" height="159.47540983606558" width="288">

### 1.4 Mechanical characteristic <a href="#block-33cd4c79856d81f5a83afa63db5ed0ee" id="block-33cd4c79856d81f5a83afa63db5ed0ee"></a>

1. Weight: 880g±20g
2. Number of poles: 42
3. Phase number: 3 phases
4. Drive mode: FOC
5. Deceleration ratio: 9:1

## 2. Driver Product Information <a href="#block-33cd4c79856d81b4a506f7c26033449b" id="block-33cd4c79856d81b4a506f7c26033449b"></a>

### 2.1 Driver product Specifications <a href="#block-33cd4c79856d819fbce5fe0a1c6dc3e8" id="block-33cd4c79856d819fbce5fe0a1c6dc3e8"></a>

| project                                                | data                  |
| ------------------------------------------------------ | --------------------- |
| The rated working voltage                              | 48VDC                 |
| The maximum allowable voltage                          | 60VDC                 |
| Rated working phase current                            | 12Apk                 |
| Maximum allowable phase current                        | 43Apk                 |
| Standby power                                          | ≤40mA                 |
| CAN bus bit rate                                       | 1Mbps                 |
| Dimensions                                             | Φ70mm                 |
| Working environment temperature                        | -20℃ to 50℃           |
| The maximum allowable temperature of the control board | 145℃                  |
| encoder resolution                                     | 14bit (absolute turn) |

### 2.2 Driver interface definition <a href="#block-33cd4c79856d811b8e05db7ca39437df" id="block-33cd4c79856d811b8e05db7ca39437df"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/594ce317-44f2-4588-9388-4bdf0b71fcac/image/w=1920,quality=90,fit=scale-down" alt="image" height="163.93653634361232" width="826.96875">

### 2.3 Driver interface recommended brand and model <a href="#block-33fd4c79856d80d7bc02d0e9378b5c7e" id="block-33fd4c79856d80d7bc02d0e9378b5c7e"></a>

| board end model | brand manufacturer | line end model | brand manufacturer |
| --------------- | ------------------ | -------------- | ------------------ |
| XT30APW-M       | AMASS (Ams)        | XT30UW-F       | AMASS (AMS)        |
| GH1.25-2PWT     | any                | GH1.25-T       | any                |

### 2.4 Driver function pin and device description <a href="#block-33cd4c79856d811897b4f08573e28c3c" id="block-33cd4c79856d811897b4f08573e28c3c"></a>

1. Power supply and CAN communication
2. Download port
3. Indicator light
4. Driver function pin and device description

| **Pin** | **description**     |
| ------- | ------------------- |
| 1       | SWDIO (data)        |
| 2       | SWCLK (clock)       |
| 3       | 3V3 (positive 3.3V) |
| 4       | GND                 |

| **Pin** | **description**                                |
| ------- | ---------------------------------------------- |
| 1       | The positive electrode of the power supply (+) |
| 2       | Negative electrode of the power supply (-)     |
| 3       | CAN CAN\_L                                     |
| 4       | CAN the high side of the communication CAN\_H  |

## 3. Upper computer instructions <a href="#block-33cd4c79856d81178220fe0ae042f4bf" id="block-33cd4c79856d81178220fe0ae042f4bf"></a>

Please go to [www.robstride.com](http://www.robstride.com/) website download center

### 3.1 Hardware disposition <a href="#block-33cd4c79856d81798d23c5295a3f25e1" id="block-33cd4c79856d81798d23c5295a3f25e1"></a>

The articulated motor uses the CAN communication mode and has two communication cables. It is connected to the debugger through the can to USB tool. The debugger needs to be installed with the ch340 driver in advance and works in AT mode by default.

It should be noted that we are based on the specific can to USB tool development of the debugger, so we need to use our recommended serial port tool to debug the debugger, if you want to transplant to other debugger platform can refer to the third chapter of the instructions for development.

The CAN to USB tool is recommended to use the official USB-to-CAN module of RobStride. The frame header of the corresponding serial port protocol is 4154, and the frame tail is 0D 0A.

When using the CAN-to-USB module, pay attention to the settings of the DIP switches on the module: When DIP switch 1 is in the ON position, the module enters Boot mode and cannot establish a connection with the host computer. When DIP switch 2 is in the ON position, a 120Ω terminal resistor is connected to the module port, allowing normal communication with the host computer.

### 3.2 Upper computer interface and description <a href="#block-33cd4c79856d815eb751c0d73f80a750" id="block-33cd4c79856d815eb751c0d73f80a750"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9072c1f0-5a05-45ee-bd7d-6c7ab2a5fe23/image/w=1920,quality=90,fit=scale-down" alt="image" height="1514" width="2460">

Mainly includes:

1. Motor Connection Module
2. Refreshing the Serial Port
3. Opening the Serial Port
4. Testing the Device
5. Motor Configuration Module
6. Starting the Upgrade
7. Opening a File
8. Starting the Upgrade
9. Modifying the Motor CAN ID
10. Setting the Motor's Mechanical Zero Position
11. Motor Upgrade Module
12. Magnetic Encoder Calibration
13. Motor Active Reporting Switch
14. Setting the Motor Active Reporting Time
15. Modifying the Motor CAN ID
16. Setting the Motor's Mechanical Zero Position
17. Motor Main Interface
18. Parameter Settings
19. Motor Oscilloscope
20. Run and Debug Area
21. Parameter Debugging Buttons
22. Motor Mode Configuration and Parameter Modification
23. Sine Signal Testing

### 3.3 Motor settings <a href="#block-33cd4c79856d81868227e328381a605b" id="block-33cd4c79856d81868227e328381a605b"></a>

#### 3.3.1 Motor connection settings <a href="#block-33cd4c79856d8182bb53f2807b878ed2" id="block-33cd4c79856d8182bb53f2807b878ed2"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b850fc1e-d6a1-40c0-bf33-d97df6819365/image/w=1920,quality=90,fit=scale-down" alt="image" height="345.59999999999997" width="288">

Connect the CAN to USB tool (install the ch340 driver, which works in AT mode by default), click Refresh Serial Port, open the serial port, and click Detect Device to detect the corresponding motor. The green text below is the motor type.

#### 3.3.2 Motor configuration module <a href="#block-33cd4c79856d812a9237d00a6bba7575" id="block-33cd4c79856d812a9237d00a6bba7575"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/430fdfe5-5fc1-4b32-b4b8-4eaf6fd71bfb/image/w=1920,quality=90,fit=scale-down" alt="image" height="352.3404255319149" width="288">

1. Recalibrate the motor magnetic encoder. Reinstalling the motor board and motor, or reconnecting the motor's three-phase wiring requires recalibrating the magnetic encoder.
2. Enable active motor reporting. Click Start Reporting to enable active motor reporting in communication type 2. You can set the interval below, with a minimum of 10ms.
3. Set ID: Set the motor's CAN ID.
4. Set Zero Position: Set the current position to 0.

#### 3.3.3 Motor upgrade module <a href="#block-33cd4c79856d81a7b288f541a06bbeb4" id="block-33cd4c79856d81a7b288f541a06bbeb4"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/b365de8b-b2ef-478f-84e1-0880611ec65a/image/w=1920,quality=90,fit=scale-down" alt="image" height="343.644908616188" width="288">

1\. Click to open the file and select the firmware to upgrade. The rs-0x in the firmware name is the selected motor type.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1e0cecaf-d8df-47eb-ba3a-91709366098d/image/w=1920,quality=90,fit=scale-down" alt="image" height="329.78238341968915" width="288">

2. Click Start Upgrade, and the motor will enter the upgrade preparation stage.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/d66027c6-c687-4e81-9ccb-27b2957af15f/image/w=1920,quality=90,fit=scale-down" alt="image" height="347.96915167095113" width="288">

3. When the green text "Device has entered upgrade mode" pops up, click to start the upgrade

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1254900e-0b3f-4e72-b74b-a6a29ef7b7c3/image/w=1920,quality=90,fit=scale-down" alt="image" height="346.96062992125985" width="288">

4. When the green text "Upgrade Successfully" pops up, the upgrade is complete.
5. If the green progress bar gets stuck halfway through the upgrade, you can click to stop the upgrade, or re-power on and re-enter the upgrade process. The internal program of the motor will not be lost after the upgrade fails. Please check whether the communication environment is good before upgrading again.

#### 3.3.4 Parameter settings <a href="#block-33cd4c79856d817a8824f97eb1b9c176" id="block-33cd4c79856d817a8824f97eb1b9c176"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/83fd5db5-0ba6-4b8a-b6b5-454a13792e94/image/w=1920,quality=90,fit=scale-down" alt="image" height="548.535120412844" width="832.9921875">

After successfully connecting to the motor,

1. Click Refresh Parameter Table. "Updated Parameter Table Successfully" will appear at the top, indicating that the motor parameters have been successfully read (Note: The parameter table must be configured while the motor is in standby mode. If the motor is running, the parameter table refresh cannot be performed). The interface will display the motor's parameters. Parameters in blue are stored internally in the motor and can be modified in the Current Value field following the corresponding parameter.
2. Click Read Parameters to upload the motor parameters to the debugger. Parameters in light blue are observed parameters, which are collected and can be observed in real time.
3. Click Write Parameters to download the debugger parameters to the motor.
4. Click Restore Factory to restore the motor's default parameters for the latest firmware.
5. Click Export to export the current motor parameters in the parameter table.
6. Click Open Multi-Device Connection to connect the host computer to multiple motors. Note that because the parameter interfaces for different motor types vary, multi-device connection is only used for upgrades. After upgrading and debugging the motor, close multi-device connection and search for the motor again.
7. **Note: Please do not change the torque limit, protection temperature and over temperature time of the motor. Our company will not bear any legal responsibility for any damage to human body or irreversible damage to joints caused by illegal operation of this product.**

| function code | name                 | parameter type | attribute   | Maximum value | Minimum value | Current value (for reference) | note                                          |
| ------------- | -------------------- | -------------- | ----------- | ------------- | ------------- | ----------------------------- | --------------------------------------------- |
| 0X0000        | Name                 | String         | Read/Write  |               |               | ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ              |                                               |
| 0X0001        | BarCode              | String         | Read/Write  |               |               | ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ              |                                               |
| 0X1000        | BootCodeVersion      | String         | Read only   |               |               | 0.1.5                         |                                               |
| 0X1001        | BootBuildDate        | String         | Read only   |               |               | Mar 16 2022                   |                                               |
| 0X1002        | BootBuildTime        | String         | Read only   |               |               | 20:22:09                      |                                               |
| 0X1003        | AppCodeVersion       | String         | Read only   |               |               | 0.0.0.1                       | Motor program version number                  |
| 0X1004        | AppGitVersion        | String         | Read only   |               |               | 7b844b0fM                     |                                               |
| 0X1005        | AppBuildDate         | String         | Read only   |               |               | Apr 14 2022                   |                                               |
| 0X1006        | AppBuildTime         | String         | Read only   |               |               | 20:30:22                      |                                               |
| 0X1007        | AppCodeName          | String         | Read only   |               |               | Lingzu\_motor                 |                                               |
| 0X2000        | echoPara1            | uint16         | disposition | 74            | 5             | 5                             |                                               |
| 0X2001        | echoPara2            | uint16         | disposition | 74            | 5             | 5                             |                                               |
| 0X2002        | echoPara3            | uint16         | disposition | 74            | 5             | 5                             |                                               |
| 0X2003        | echoPara4            | uint16         | disposition | 74            | 5             | 5                             |                                               |
| 0X2004        | echoFreHz            | uint32         | Read/Write  | 10000         | 1             | 500                           |                                               |
| 0X2005        | MechOffset           | float          | Settings    | 7             | -7            | 4.619583                      | Motor magnetic encoder Angle offset           |
| 0X2006        | MechPos\_init        | float          | Read/Write  | 50            | -50           | 4.52                          | Reserved parameter                            |
| 0X2007        | limit\_torque        | float          | Read/Write  | 17            | 0             | 17                            | Torque limitation                             |
| 0X2008        | I\_FW\_MAX           | float          | Read/Write  | 33            | 0             | 0                             | Weak magnetic current value, default 0        |
| 0X2009        | motor\_baud          | uint8          | Settings    | 20            | 0             | 1                             | Baud rate flag bit                            |
| 0X200a        | CAN\_ID              | uint8          | Settings    | 127           | 0             | 1                             | id of this object                             |
| 0X200b        | CAN\_MASTER          | uint8          | Settings    | 127           | 0             | 0                             | can host id                                   |
| 0X200c        | CAN\_TIMEOUT         | uint32         | Read/Write  | 100000        | 0             | 0                             | can timeout threshold. The default value is 0 |
| 0X200d        | status2              | int16          | Read/Write  | 1500          | 0             | 800                           | Reserved parameter                            |
| 0X200e        | status3              | uint32         | Read/Write  | 1000000       | 1000          | 20000                         | Reserved parameter                            |
| 0X200f        | status1              | float          | Read/Write  | 64            | 1             | 7.75                          | Reserved parameter                            |
| 0X2010        | Status6              | uint8          | Read/Write  | 1             | 0             | 1                             | Reserved parameter                            |
| 0X2011        | cur\_filt\_gain      | float          | Read/Write  | 1             | 0             | 0.9                           | Current filtering parameter                   |
| 0X2012        | cur\_kp              | float          | Read/Write  | 200           | 0             | 0.025                         | Current kp                                    |
| 0X2013        | cur\_ki              | float          | Read/Write  | 200           | 0             | 0.0258                        | Current ki                                    |
| 0X2014        | spd\_kp              | float          | Read/Write  | 200           | 0             | 2                             | Velocity kp                                   |
| 0X2015        | spd\_ki              | float          | Read/Write  | 200           | 0             | 0.021                         | Speed ki                                      |
| 0X2016        | loc\_kp              | float          | Read/Write  | 200           | 0             | 30                            | Position kp                                   |
| 0X2017        | spd\_filt\_gain      | float          | Read/Write  | 1             | 0             | 0.1                           | Velocity filter parameter                     |
| 0X2018        | limit\_spd           | float          | Read/Write  | 200           | 0             | 2                             | Location mode speed limit                     |
| 0X2019        | limit\_cur           | float          | Read/Write  | 23            | 0             | 23                            | Position, Velocity mode current limit         |
| 0X201a        | loc\_ref\_filt\_gain | float          | Read/Write  | 100           | 0             | 0                             | Reserved parameter                            |
| 0X201b        | limit\_loc           | float          | Read/Write  | 100           | 0             | 0                             | Reserved parameter                            |
| 0X201c        | position\_offset     | float          | Read/Write  | 27            | 0             | 0                             | High speed segment offset                     |
| 0X201d        | chasu\_angle\_offset | float          | Read/Write  | 27            | 0             | 0                             | The low end is offset                         |
| 0X201e        | spd\_step\_value     | float          | Read/Write  | 150           | 0             |                               | Velocity-mode acceleration                    |
| 0X201f        | vel\_max             | float          | Read/Write  | 20            | 0             |                               | PP mode speed                                 |
| 0X2020        | acc\_set             | float          | Read/Write  | 1000          | 0             |                               | PP mode acceleration                          |
| 0X2021        | zero\_sta            | float          | Read/Write  | 100           | 0             | 0                             | Zero marker                                   |
| 0X2022        | protocol\_1          | uint8          | Read/Write  |               |               | 0                             | Protocol flag                                 |
| 0X2023        | damper               | uint8          | Read/Write  | 0             | 20            | 0                             | Damping switch                                |
| 0X2024        | add\_offset          | float          | Read/Write  | -7            | 7             | 0                             | Position offset parameter                     |
| 0X3000        | timeUse0             | uint16         | Read only   |               |               | 5                             |                                               |
| 0X3001        | timeUse1             | uint16         | Read only   |               |               | 0                             |                                               |
| 0X3002        | timeUse2             | uint16         | Read only   |               |               | 10                            |                                               |
| 0X3003        | timeUse3             | uint16         | Read only   |               |               | 0                             |                                               |
| 0X3004        | encoderRaw           | int16          | Read only   |               |               | 11396                         | Magnetic encoder sampling value               |
| 0X3005        | mcuTemp              | int16          | Read only   |               |               | 337                           | mcu internal temperature, \*10                |
| 0X3006        | motorTemp            | int16          | Read only   |               |               | 333                           | Motor ntc temperature, \*10                   |
| 0X3007        | vBus(mv)             | uint16         | Read only   |               |               | 24195                         | Bus voltage                                   |
| 0X3008        | adc1Offset           | int32          | Read only   |               |               | 2084                          | adc sampling channel 1 Zero current bias      |
| 0X3009        | adc2Offset           | int32          | Read only   |               |               | 2084                          | adc sampling channel 2 Zero current bias      |
| 0X300a        | adc1Raw              | uint16         | Read only   |               |               | 1232                          | adc sampling value1                           |
| 0X300b        | adc2Raw              | uint16         | Read only   |               |               | 1212                          | adc sampling value2                           |
| 0X300c        | VBUS                 | float          | Read only   |               |               | 36                            | Bus voltage V                                 |
| 0X300d        | cmdId                | float          | Read only   |               |               | 0                             | id ring instruction, A                        |
| 0X300e        | cmdIq                | float          | Read only   |               |               | 0                             | iq ring command, A                            |
| 0X300f        | cmdlocref            | float          | Read only   |               |               | 0                             | Position loop command, rad                    |
| 0X3010        | cmdspdref            | float          | Read only   |               |               | 0                             | Speed loop command, rad/s                     |
| 0X3011        | cmdTorque            | float          | Read only   |               |               | 0                             | Torque instruction, nm                        |
| 0X3012        | cmdPos               | float          | Read only   |               |               | 0                             | mit Protocol Angle instruction                |
| 0X3013        | cmdVel               | float          | Read only   |               |               | 0                             | mit Protocol Speed instruction                |
| 0X3014        | rotation             | int16          | Read only   |               |               | 1                             | Number of turns                               |
| 0X3015        | modPos               | float          | Read only   |               |               | 4.363409                      | Motor uncounted coil mechanical Angle, rad    |
| 0X3016        | mechPos              | float          | Read only   |               |               | 0.777679                      | Load end loop mechanical Angle, rad           |
| 0X3017        | mechVel              | float          | Read only   |               |               | 0.036618                      | Load speed: rad/s                             |
| 0X3018        | elecPos              | float          | Read only   |               |               | 4.714761                      | Electrical Angle                              |
| 0X3019        | ia                   | float          | Read only   |               |               | 0                             | U-wire current, A                             |
| 0X301a        | ib                   | float          | Read only   |               |               | 0                             | V-wire current, A                             |
| 0X301b        | ic                   | float          | Read only   |               |               | 0                             | W-wire current, A                             |
| 0X301c        | timeout              | uint32         | Read only   |               |               | 31600                         | Timeout counter value                         |
| 0X301d        | phaseOrder           | uint8          | Read only   |               |               | 0                             | Directional marking                           |
| 0X301e        | iqf                  | float          | Read only   |               |               | 0                             | iq filter value，A                             |
| 0X301f        | boardTemp            | int16          | Read only   |               |               | 359                           | Plate temperature，\*10                        |
| 0X3020        | iq                   | float          | Read only   |               |               | 0                             | iq Original value，A                           |
| 0X3021        | id                   | float          | Read only   |               |               | 0                             | id Original value，A                           |
| 0X3022        | faultSta             | uint32         | Read only   |               |               | 0                             | Fault status value                            |
| 0X3023        | warnSta              | uint32         | Read only   |               |               | 0                             | Warning status value                          |
| 0X3024        | drv\_fault           | uint16         | Read only   |               |               | 0                             | The driver chip fault value is 1              |
| 0X3025        | drv\_temp            | int16          | Read only   |               |               | 48                            | The driver chip fault value is 2              |
| 0X3026        | Uq                   | float          | Read only   |               |               | 0                             | Q-axis voltage                                |
| 0X3027        | Ud                   | float          | Read only   |               |               | 0                             | D-axis voltage                                |
| 0X3028        | dtc\_u               | float          | Read only   |               |               | 0                             | The duty cycle of the U-phase output          |
| 0X3029        | dtc\_v               | float          | Read only   |               |               | 0                             | The duty cycle of the V-phase output          |
| 0X302a        | dtc\_w               | float          | Read only   |               |               | 0                             | The duty cycle of the W-phase output          |
| 0X302b        | v\_bus               | float          | Read only   |               |               | 24.195                        | Vbus in the closed loop                       |
| 0X302c        | torque\_fdb          | float          | Read only   |               |               | 0                             | Torque feedback value, nm                     |
| 0X302d        | rated\_i             | float          | Read only   |               |               | 8                             | Rated current of motor                        |
| 0X302e        | limit\_i             | float          | Read only   |               |               | 27                            | The motor limits the maximum current          |
| 0X302f        | spd\_ref             | float          | Read only   |               |               | 0                             | Motor speed expectation                       |
| 0X3030        | spd\_reff            | float          | Read only   |               |               | 0                             | Motor speed expectation 2                     |
| 0X3031        | zero\_fault          | float          | Read only   |               |               | 0                             | Motor position determination parameters       |
| 0X3032        | chasu\_coder\_raw    | float          | Read only   |               |               | 0                             | Motor position determination parameters       |
| 0X3033        | chasu\_angle         | float          | Read only   |               |               | 0                             | Motor position determination parameters       |
| 0X3034        | as\_angle            | float          | Read only   |               |               | 0                             | Motor position determination parameters       |
| 0X3035        | vel\_max             | float          | Read only   |               |               | 0                             | Motor position determination parameters       |
| 0X3036        | judge                | float          | Read only   |               |               | 0                             | Motor position determination parameters       |
| 0X3037        | position             | float          | Read only   |               |               | 0                             | Position value                                |
| 0X3038        | chasu\_angle\_init   | float          | Read only   |               |               | -0.002301                     | Angle initialization                          |
| 0X3039        | chasu\_angle\_out    | float          | Read only   |               |               | -0.23012                      | Motor position determination parameters       |
| 0X303a        | motormechinit        | float          | Read only   |               |               | -0.000383                     | Motor position determination parameters       |
| 0X303b        | mech\_angle\_init2   | float          | Read only   |               |               | -0.000115                     | Motor position determination parameters       |
| 0X303c        | mech\_angle\_rotat   | float          | Read only   |               |               | 0                             | Motor position determination parameters       |
| 0X303d        | fault1               | uint32         | Read only   |               |               | 0                             | Log failure                                   |
| 0X303e        | fault2               | uint32         | Read only   |               |               | 0                             | Log failure                                   |
| 0X303f        | fault3               | uint32         | Read only   |               |               | 0                             | Log failure                                   |
| 0X3040        | fault4               | uint32         | Read only   |               |               | 0                             | Log failure                                   |
| 0X3041        | fault5               | uint32         | Read only   |               |               | 0                             | Log failure                                   |
| 0X3042        | fault6               | uint32         | Read only   |               |               | 0                             | Log failure                                   |
| 0X3043        | fault7               | uint32         | Read only   |               |               | 0                             | Log failure                                   |
| 0X3044        | fault8               | uint32         | Read only   |               |               | 0                             | Log failure                                   |
| 0X3045        | ElecOffset           | float          | Read only   |               |               | 0                             | electrical Angle offset                       |
| 0X3046        | mcOverTemp           | int16          | Read only   |               |               | 0                             | Overtemperature threshold                     |
| 0X3047        | Kt\_Nm/Amp           | float          | Read only   |               |               | 0                             | Moment coefficient                            |
| 0X3048        | Tqcali\_Type         | uint8          | Read only   |               |               | 0                             | Motor type                                    |

#### 3.3.5 Oscilloscope <a href="#block-33cd4c79856d8130a265e992ebdce80f" id="block-33cd4c79856d8130a265e992ebdce80f"></a>

The interface supports viewing and observing the graph generated by realtime data, including motor Id/Iq current, temperature, real-time speed at the output end, rotor (encoder) position, output end position, etc.

Click on the oscilloscope module in the analysis module, select the appropriate parameters in the channel (parameter meaning can be referred to the parameter table), set the output frequency, click on the start plot to observe the data graph, stop the plot to stop the observation graph.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/e60922ae-c4dc-44fa-aba4-9b40bbab8541/image/w=1920,quality=90,fit=scale-down" alt="image" height="1492" width="2190">

The command sent is in the communication command box below

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ccf2ed0c-dbe1-49c7-b93c-7900c7a42409/image/w=1920,quality=90,fit=scale-down" alt="image" height="1376" width="2212">

Communication box instruction example:

41 54 90 07 e8 0c 08 05 70 00 00 01 00 00 00 0d 0a

The meaning is as follows

| 41 54        | 90 07 e8 0c         | 08             | 05 70 00 00 01 00 00 00 | 0d 0a      |
| ------------ | ------------------- | -------------- | ----------------------- | ---------- |
| frame header | Number of data bits | extended frame | data frame              | frame tail |

The translation of extended frame canid into real canid requires the following transformations:

90 07 e8 0c converts to binary as 1001 0000 0000 0111 1110 1000 0000 1100, shift three positions to the right and it becomes 1 0010 0000 0000 1111 11010000 0001, convert it to hexadecimal, It is 12 00 FD 01. According to the communication protocol, the meaning is as follows:

| 12 in hexadecimal                       | 0          | FD      | 1            |
| --------------------------------------- | ---------- | ------- | ------------ |
| Communication type 18 (in decimal base) | No meaning | host id | motor CAN ID |

#### 3.3.6 can communication failure protection <a href="#block-33cd4c79856d811e9c8dc7636f8d7bc7" id="block-33cd4c79856d811e9c8dc7636f8d7bc7"></a>

When the value of CAN\_TIMEOUT is 0, this function is disabled When the CAN\_TIMEOUT value is non-0, when the motor does not receive the can command within a certain period of time, the motor enters the reset mode, and 20000 is 1s

#### 3.3.7 Motor fault instructions <a href="#block-33cd4c79856d81c084eff29341a45f89" id="block-33cd4c79856d81c084eff29341a45f89"></a>

Function code 0x3022 indicates the fault code, where Bit 16: Motor current fault: A-phase current sampling overcurrent Bit 14: Motor stall overload algorithm protection Bit 9: Position initialization fault Bit 8: Hardware identification fault Bit 7: Encoder uncalibrated: Motor encoder not calibrated Bit 5: Motor current fault: C-phase current sampling overcurrent Bit 4: Motor current fault: B-phase current sampling overcurrent Bit 3: Overvoltage fault: the motor voltage exceeds the protection voltage by 60V Bit 2: Undervoltage fault: the motor voltage is lower than the protection voltage of 12V Bit 1: Driver chip failure: Motor driver chip failure reported Bit 0: Motor overtemperature fault: motor thermistor temperature exceeds 145 degrees Function code 0x3024 is driver chip fault code 1. The specific faults are as follows

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/ca1c7ac2-4369-4027-bb8f-10c3cc898b9e/image/w=1920,quality=90,fit=scale-down" alt="image" height="958" width="2242">

Function code 0x3025 is driver chip fault code 2. The specific faults are as follows

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/03c5eaf3-40af-4ab9-b587-c56e9ed3d682/image/w=1920,quality=90,fit=scale-down" alt="image" height="1078" width="2364">

### 3.4 Control Demo <a href="#block-33cd4c79856d819f82bbdc132ae5baaa" id="block-33cd4c79856d819f82bbdc132ae5baaa"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/5a1065ba-20cb-400a-8aaa-bb3547295b26/image/w=1920,quality=90,fit=scale-down" alt="image" height="793.1964809384165" width="336">

Jog Run

Click JOG +/- to run the motor forward and reverse at a speed of 1 rad/s. Control Mode Switching

Select the desired control mode in the command box to the right of the run mode.

#### 3.4.1 Operation and control mode <a href="#block-33cd4c79856d817daa04f1e92e6fd2a9" id="block-33cd4c79856d817daa04f1e92e6fd2a9"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a60892ff-7fc0-409e-8fb9-48d8b7a4b91e/image/w=1920,quality=90,fit=scale-down" alt="image" height="469.1014492753623" width="336">

1. Switch the control mode to operation mode.
2. The motor starts running and enters motor\_mode.
3. Set five parameter values and click Start or Send continuously. The motor will return feedback frames and run according to the target command.
4. Click Stop to stop the motor and terminate the continuous sending of commands.

#### 3.4.2 Current Mode <a href="#block-33cd4c79856d81d0a671cc40b4816e51" id="block-33cd4c79856d81d0a671cc40b4816e51"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7bbca233-8fe0-4393-925f-5b3c5c822f5a/image/w=1920,quality=90,fit=scale-down" alt="image" height="476.3943661971831" width="336">

1. Switch the control mode to current mode.
2. The motor starts running and enters motor\_mode.
3. Set the current command value for Iq Command 1 (A). Click the >>button on the right. The motor will follow the current command.
4. Click Stop to stop the motor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/228d9d90-1ec3-45bb-823f-a66f77968ec1/image/w=1920,quality=80,fit=scale-down" alt="image" width="100%">

Motor Current Sine Test

1. Switch the control mode to current mode.
2. The motor starts running and enters motor\_mode.
3. Set the amplitude and frequency, click OK, and then click Start. The corresponding mode target command will be planned according to the sine law.
4. Click Stop to stop the motor.

#### 3.4.3 Speed Mode <a href="#block-33cd4c79856d817aa6bec435324ccfbb" id="block-33cd4c79856d817aa6bec435324ccfbb"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/58aac5d5-bc43-46df-81f5-b213c82e764c/image/w=1920,quality=90,fit=scale-down" alt="image" height="466.1621621621622" width="336">

1. Switch the control mode to speed mode.
2. The motor starts running and enters motor\_mode.
3. First, set the current limit (maximum phase current) and speed step value(motor acceleration). If no settings are made, the motor will operate at the default values. Finally, set the speed command (target speed). The motor will follow the command.
4. Click Stop to stop the motor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/f91ffac0-7179-4807-bd0c-3243dd6f1e25/image/w=1920,quality=90,fit=scale-down" alt="image" height="172.11581291759467" width="336">

Motor Speed Sine Test

1. Switch the control mode to speed mode.
2. The motor starts running and enters motor\_mode.
3. Set the amplitude and frequency, click OK, and then click Start. The corresponding mode target command will be planned according to the sine law.
4. Click Stop to stop the motor.

#### 3.4.4 Position Mode (PP) <a href="#block-33cd4c79856d810aa62edcfc0deaddf6" id="block-33cd4c79856d810aa62edcfc0deaddf6"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/0ba4a66c-7552-43ac-aad9-2dc7ba2af0dc/image/w=1920,quality=90,fit=scale-down" alt="image" height="464.25" width="336">

1. Switch the control mode to interpolation position mode.
2. Start the motor and enter motor\_mode.
3. First, set the speed and acceleration. If not set, the motor will operate at the default values. Finally, set the position command (target position). The motor will follow the command.
4. Set the speed to 0 to stop the motor at the current position. To continue operation, re-issue the speed and position.
5. Click Stop to stop the motor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/bb4c3b10-2dcc-49ee-a548-5c2306e2307d/image/w=1920,quality=90,fit=scale-down" alt="image" height="170.24" width="336">

Motor Position Sine Test

1. Switch the control mode to interpolation position mode.
2. Start the motor and enter motor\_mode.
3. Set the amplitude and frequency, click OK, and then click Start. The corresponding mode target command will be planned according to the sine law.
4. Click Stop to stop the motor.

#### 3.4.5 Location Mode (CSP) <a href="#block-33cd4c79856d81e5b139d5bc6d225d99" id="block-33cd4c79856d81e5b139d5bc6d225d99"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/9695776f-918b-4032-8339-ed4f6f48a105/image/w=1920,quality=90,fit=scale-down" alt="image" height="471.7808219178082" width="336">

1. Switch the control mode to position mode.
2. The motor starts running and enters motor\_mode.
3. Set the speed first. If no speed setting is made, the motor will run at the default value. Finally, set the position command (target position). The motor will follow the command.
4. Click Stop to stop the motor.

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/8645a7f3-4c56-4499-bcd8-c8e727e4d994/image/w=1920,quality=90,fit=scale-down" alt="image" height="170.25" width="336">

Motor position sinusoidal test

1. Switch the control mode to position mode.
2. The motor starts running and enters motor\_mode.
3. Set the amplitude and frequency, click OK, and then click Start. The corresponding mode target command is then sinusoidally planned.
4. Click Stop to stop the motor.

## 4. Driver protocol and instructions <a href="#block-33cd4c79856d8130b6dfcfccdb0c31c2" id="block-33cd4c79856d8130b6dfcfccdb0c31c2"></a>

The motor communication is the CAN 2.0 communication interface, the baud rate is 1Mbps, and the extended frame format is adopted as follows:

| data field  | 29-bit ID          |             |                     | 8Byte data field |
| ----------- | ------------------ | ----------- | ------------------- | ---------------- |
| Size        | Bit28\~bit24       | bit23\~8    | bit7\~0             | Byte0\~Byte7     |
| Description | Communication type | data area 2 | Destination address | data area 1      |

The control modes supported by the motor include:

* Operation control mode: set 5 parameters of motor operation control;
* Current mode: the specified Iq current of the given motor;
* Velocity mode: the specified running speed of the given motor;
* Position mode: Given the specified position of the motor, the motor will run to the specified position;

### 4.1 Description of the communication protocol type <a href="#block-33cd4c79856d81eea179e80766467c24" id="block-33cd4c79856d81eea179e80766467c24"></a>

#### 4.1.1 Communication type 0: Get device ID <a href="#block-33cd4c79856d811b98d1f5cc4e07da91" id="block-33cd4c79856d811b98d1f5cc4e07da91"></a>

Gets the device's ID and 64-bit MCU unique identifier

| data field  | 29-bit ID    |                                   |                      | 8Byte data field |
| ----------- | ------------ | --------------------------------- | -------------------- | ---------------- |
| Size        | Bit28\~bit24 | bit23\~8                          | bit7\~0              | Byte0\~Byte7     |
| Description | 0x0          | bit15\~8: identifies host CAN\_ID | target motor CAN\_ID | 0                |

Response frame:

| data field  | 29-bit ID    |                      |         | 8Byte data field             |
| ----------- | ------------ | -------------------- | ------- | ---------------------------- |
| Size        | Bit28\~bit24 | bit23\~8             | bit7\~0 | Byte0\~Byte7                 |
| Description | 0x0          | target motor CAN\_ID | 0XFE    | 64-bit MCU unique identifier |

#### 4.1.2 Communication Type 1: operation control mode motor control instruction <a href="#block-33cd4c79856d8182bb87c5f92832ba95" id="block-33cd4c79856d8182bb87c5f92832ba95"></a>

| data field  | 29-bit ID    |                                                           |                      | 8Byte data field                                                                                                                                                                                                                                                                                                                                                |
| ----------- | ------------ | --------------------------------------------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                                  | bit7\~0              | Byte0\~Byte7                                                                                                                                                                                                                                                                                                                                                    |
| Description | 0x1          | **Byte2**: Torque (0\~65535) corresponds to (-17Nm\~17Nm) | target motor CAN\_ID | **Byte0\~1**: target Angle \[0\~65535] corresponds to (-4π\~4π) **Byte2\~3**: Target angular velocity \[0\~65535] corresponds to (-20rad/s\~20rad/s) **Byte4\~5**: Kp \[0\~65535] corresponds to (0.0\~500.0) **Byte6\~7**: Kd \[0 to 65535] corresponds to the above data (0.0 to 5.0). After the conversion, the high byte is in front and the low byte is in |

Response frame: Response motor feedback frame (see communication type2)

#### Communication Type 2: motor feedback data <a href="#block-33cd4c79856d8177a8dec8199d630dba" id="block-33cd4c79856d8177a8dec8199d630dba"></a>

| data field  | 29-bit ID    |                                                                                                                                                                                                                                                                                                                                                                                                                      |              | 8Byte data field                                                                                                                                                                                                                                                                                                                                                         |
| ----------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Size        | Bit28\~bit24 | bit23\~8                                                                                                                                                                                                                                                                                                                                                                                                             | bit7\~0      | Byte0\~Byte7                                                                                                                                                                                                                                                                                                                                                             |
| Description | 0x2          | **Bit8\~Bit15**: CAN ID of the current motor **bit21\~16**: fault information (0 none 1 has) **bit21**: uncalibrated **bit20**: Uncalibrated **bit20**: Gridlock overload fault **bit19**: magnetic coding fault **bit18**: overtemperature **bit17**: Three-phase overcurrent fault **bit16**: undervoltage fault **bit22\~23**:Mode status 0: Reset mode \[reset] 1: Cali mode \[calibration] 2: Motor mode \[Run] | host CAN\_ID | **Byte0\~1**: The current Angle \[0\~65535] Corresponding to(-4π\~4π) **Byte2\~3**: Current angular velocity \[0\~65535] corresponds to (-20rad/s\~20rad/s) **Byte4\~5**: Current torque \[0\~65535] corresponds to (- 60Nm\~60Nm) **Byte6\~7**: Current temperature: Temp(Celsius) \*10 If the value is higher than 10, the high byte is first and the low byte is last |

#### 4.1.3 Communication Type 3: Motor enabled to run <a href="#block-33cd4c79856d81a887e3ee56966dd248" id="block-33cd4c79856d81a887e3ee56966dd248"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field |
| ----------- | ------------ | ------------------------------------- | -------------------- | ---------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7     |
| Description | 0x3          | bit15\~8: identifies the main CAN\_ID | target motor CAN\_ID |                  |

Response frame: Response motor feedback frame (see communication type 2)

#### 4.1.4 Communication Type 4: Motor stops running <a href="#block-33cd4c79856d813f8aa0f8bb28c7f6e4" id="block-33cd4c79856d813f8aa0f8bb28c7f6e4"></a>

| data field  | 29-bit ID    |                                             |                      | 8Byte data field                                                                                           |
| ----------- | ------------ | ------------------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                    | bit7\~0              | Byte0\~Byte7                                                                                               |
| Description | 0x4          | bit15\~8: used to identify the main CAN\_ID | target motor CAN\_ID | When the motor is running normally, 0 must be cleared in the data field. Byte\[0]=1: The fault is cleared. |

Response frame: Response motor feedback frame (see communication type2)

#### 4.1.5 Communication type 6: Set motor mechanical zero <a href="#block-33cd4c79856d8119a24aee8786a8591b" id="block-33cd4c79856d8119a24aee8786a8591b"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field |
| ----------- | ------------ | ------------------------------------- | -------------------- | ---------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7     |
| Description | 0x6          | bit15\~8: Identifies the main CAN\_ID | target motor CAN\_ID | Byte\[0]=1       |

Response frame: Response motor feedback frame (see communication type2)

#### Communication type 7: Set motor CAN\_ID <a href="#block-33cd4c79856d813fb0e6f5d5544376be" id="block-33cd4c79856d813fb0e6f5d5544376be"></a>

Change the current motor CAN\_ID, effective immediately.

| data field  | 29-bit ID    |                                                                           |                      | 8Byte data field |
| ----------- | ------------ | ------------------------------------------------------------------------- | -------------------- | ---------------- |
| Size        | Bit28\~bit24 | bit23\~8                                                                  | bit7\~0              | Byte0\~Byte7     |
| Description | 0x7          | **bit15\~8**: used to identify main CAN\_ID **Bit16\~23**: preset CAN\_ID | target motor CAN\_ID |                  |

Response frame: Answer motor broadcast frame (see communication type 0)

#### 4.1.6 Communication type 17: Single parameter read <a href="#block-33cd4c79856d81af9631c9efa9e4a64e" id="block-33cd4c79856d81af9631c9efa9e4a64e"></a>

| data field  | 29-bit ID    |                                             |                      | 8Byte data field                                                                                                                                                              |
| ----------- | ------------ | ------------------------------------------- | -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                    | bit7\~0              | Byte0\~Byte7                                                                                                                                                                  |
| Description | 0x11         | bit15\~8: Used to identify the main CAN\_ID | target motor CAN\_ID | **Byte0\~1**: index. For details, see the read ability parameter table below **Byte2\~3**:00 **Byte4\~7**: In data above00, the low byte is first and the high byte is second |

Response frame:

| data field  | 29-bit ID    |                                                                                                                                                               |                                                                                                                                              | 8Byte data field |
| ----------- | ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ---------------- |
| Size        | Bit28\~bit24 | bit23\~8                                                                                                                                                      | bit7\~0                                                                                                                                      | Byte0\~Byte7     |
| Description | 0x11         | **bit15\~8**: indicates that the master CAN\_ID **Bit23\~16**:00 indicates that the master CAN\_ID is successfully read. 01 indicates that the master can\_ID | **Byte0\~1**: **Byte2\~3**:00 **Byte4\~7**:Parameter data. 1 byte of data above Byte4 is preceded by low bytes and followed by high bytes at |                  |

#### 4.1.7 Communication type 18: Single parameter write (lost in power failure) <a href="#block-33cd4c79856d81669bb7fddc73cbc7f2" id="block-33cd4c79856d81669bb7fddc73cbc7f2"></a>

With type 22, the parameter starting with function code 0x20 of the parameter table in the upper computer module can be saved

| data field  | 29-bit ID    |                                             |                      | 8Byte data field                                                                                                                                                                                                |
| ----------- | ------------ | ------------------------------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                    | bit7\~0              | Byte0\~Byte7                                                                                                                                                                                                    |
| Description | 0x12         | bit15\~8: Used to identify the main CAN\_ID | target motor CAN\_ID | **Byte0\~1**: index. For details, see the read ability parameter table below **Byte2\~3**: 00 **Byte4\~7**: Parameter data In the preceding data, the low byte is in the front and the high byte is in the rear |

Response frame: Response motor feedback frame (see communication type2)

#### 4.1.8 Communication type 21: Fault feedback frame <a href="#block-33cd4c79856d81a1bb0ae67803996433" id="block-33cd4c79856d81a1bb0ae67803996433"></a>

| data field  | 29-bit ID    |                         |                             | 8Byte data field                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ----------- | ------------ | ----------------------- | --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                | bit7\~0                     | Byte0\~Byte7                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Description | 0x15         | bit15\~8: motor CAN\_ID | identifies the main CAN\_ID | **Byte0\~3**: fault value (non-0: faulty; 0:faulty). Normal) **Bit 16**: A-phase current sampling overcurrent **Bit 14**: Motor stall overload algorithm protection **Bit 9**: Position initialization fault **Bit 8**: Hardware identification fault **Bit 7**: Encoder uncalibrated: Motor encoder not calibrated **Bit 5**: C-phase current sampling overcurrent **Bit 4**: B-phase current sampling overcurrent **bit 3**: overvoltage fault **bit 2**: undervoltage fault **bit 1**: driver chip fault **bit 0**: motor overtemperature fault, Default 145 °C **Byte4\~7**: warning Value **bit 0**: motor overtemperature warning, the default is 135°C |

#### 4.1.9 Communication type 22: Motor data save frame <a href="#block-33cd4c79856d81c1be0fc6007e946802" id="block-33cd4c79856d81c1be0fc6007e946802"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field        |
| ----------- | ------------ | ------------------------------------- | -------------------- | ----------------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7            |
| Description | 0x16         | bit15\~8: identifies the main CAN\_ID | target motor CAN\_ID | 01 02 03 04 05 06 07 08 |

Response frame: Response motor feedback frame (see communication type2)

#### 4.1.10 Communication type 23: Motor baud rate modification frame (re-power-on effect) <a href="#block-33cd4c79856d816f86cbcd6e63cd5675" id="block-33cd4c79856d816f86cbcd6e63cd5675"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field                                                                                                                  |
| ----------- | ------------ | ------------------------------------- | -------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7                                                                                                                      |
| Description | 0x17         | bit15\~8: identifies the main CAN\_ID | target motor CAN\_ID | 01 02 03 04 05 06 F\_CMD Among them, the F\_CMD byte is the motor baud rate Among them, 01 is 1M 02 is 500K 03 is 250K 04 is 125K |

Response frame: Response motor feedback frame (see communication type0)

#### 4.1.11 Communication type 24: The motor actively reports frames <a href="#block-33cd4c79856d81388553ea082144314b" id="block-33cd4c79856d81388553ea082144314b"></a>

| data field  | 29-bit ID    |                                       |                      | 8Byte data field                                                                                                                                                                                     |
| ----------- | ------------ | ------------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                              | bit7\~0              | Byte0\~Byte7                                                                                                                                                                                         |
| Description | 0x18         | bit15\~8: identifies the main CAN\_ID | target motor CAN\_ID | 01 02 03 04 05 06 F\_CMD Among them, the F\_CMD byte is the motor reporting switch 00 is to disable active reporting (default) 01 To enable active reporting, the default reporting interval is 10ms |

Response frame:

| data field  | 29-bit ID    |                                                                                                                                                                                                                                                                                                                                                                                           |                      | 8Byte data field                                                                                                                                                                                                                                                                                                                                                       |
| ----------- | ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                                                                                                                                                                                                                                                                                                                                                                  | bit7\~0              | Byte0\~Byte7                                                                                                                                                                                                                                                                                                                                                           |
| Description | 0x18         | **Bit8\~Bit15**: CAN ID of the current motor **bit21\~16**: fault information (0 none 1 has) **bit21**: uncalibrated **bit20**: Gridlock overload fault **bit19**: magnetic coding fault **bit18**: overtemperature **bit17**: Three-phase current fault **bit16**: undervoltage fault **bit22\~23**: Mode status 0: Reset mode \[reset] 1: Cali mode \[calibration] 2: Motor mode \[Run] | target motor CAN\_ID | **Byte0\~1**: The current Angle \[0\~65535] Corresponding to(-4π\~4π) **Byte2\~3**: Current angular velocity \[0\~65535] corresponds to (-20rad/s\~20rad/s) **Byte4\~5**: Current torque \[0\~65535] corresponds to (-60Nm\~60Nm) **Byte6\~7**: Current temperature: Temp(Celsius) \*10If the value is higher than 10, the high byte is first and the low byte is last |

#### 4.1.12 Communication type 25: Motor protocol modification frame (re-power-on effect) <a href="#block-33cd4c79856d81e9a371cc8f3a187c53" id="block-33cd4c79856d81e9a371cc8f3a187c53"></a>

| data field  | 29-bit ID    |                                             |                      | 8Byte data field                                                                                                                                                             |
| ----------- | ------------ | ------------------------------------------- | -------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                    | bit7\~0              | Byte0\~Byte7                                                                                                                                                                 |
| Description | 0x19         | bit15\~8: used to identify the main CAN\_ID | target motor CAN\_ID | 01 02 03 04 05 06 F\_CMD Among them, the F\_CMD byte is themotor protocol type Among them, 0 is a private protocol (default) 1 is the Canopen protocol 2 is the MIT protocol |

Response frame: Response motor feedback frame (see communication type0)

#### 4.1.13 Communication type 26：Version number read frame <a href="#block-33cd4c79856d81dc9db1c698a9a17ae2" id="block-33cd4c79856d81dc9db1c698a9a17ae2"></a>

| data field  | 29-bit ID    |                                             |                      | 8Byte data field            |
| ----------- | ------------ | ------------------------------------------- | -------------------- | --------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                    | bit7\~0              | Byte0\~Byte7                |
| Description | 0x4          | bit15\~8: used to identify the main CAN\_ID | target motor CAN\_ID | Byte\[0]=0x00 Byte\[1]=0xC4 |

Response frame:

| data field  | 29-bit ID    |                                                                                                                                                                                                                                                                                                                                                                                          |                      | 8Byte data field                                                                                      |
| ----------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- | ----------------------------------------------------------------------------------------------------- |
| Size        | Bit28\~bit24 | bit23\~8                                                                                                                                                                                                                                                                                                                                                                                 | bit7\~0              | Byte0\~Byte7                                                                                          |
| Description | 0x4          | **Bit8\~Bit15**: CAN ID of the current motor **bit21\~16**:fault information (0 none 1 has) **bit21**: uncalibrated **bit20**: Gridlock overload fault **bit19**: magnetic coding fault **bit18**: overtemperature **bit17**: Three-phase current fault **bit16**: undervoltage fault **bit22\~23**: Mode status 0: Reset mode \[reset] 1: Cali mode \[calibration] 2: Motor mode \[Run] | target motor CAN\_ID | **Byte0**=0x00 **Byte1**=0xC4 **Byte2**=0x56 **Byte3\~6**:Motor version number Order from high to low |

#### 4.1.14 Read and write a single parameter list <a href="#block-33cd4c79856d81e495d2fabfaeb64f89" id="block-33cd4c79856d81e495d2fabfaeb64f89"></a>

| **index** |                 | **Description**                                                                                                   | **Type** | **Number of bytes** |                                    | **R/W Read and write permission** |
| --------- | --------------- | ----------------------------------------------------------------------------------------------------------------- | -------- | ------------------- | ---------------------------------- | --------------------------------- |
| 0X7005    | run\_mode       | 0: operation mode 1: position mode (PP) 2: Velocity mode 3: Operation mode 4: Current mode 5: Position mode (CSP) | uint8    | 1                   |                                    | W/R                               |
| 0X7006    | iq\_ref         | Current mode Iq command                                                                                           | float    | 4                   | -43 to 43A                         | W/R                               |
| 0X700A    | spd\_ref        | Rotational Velocity mode Rotational speed command                                                                 | float    | 4                   | -20 to 20 rad/s                    | W/R                               |
| 0X700B    | limit\_torque   | torque limit                                                                                                      | float    | 4                   | 0 to 60Nm                          | W/R                               |
| 0X7010    | cur\_kp         | Kp                                                                                                                | float    | 4                   | The default value is 0.17          | W/R                               |
| 0X7011    | cur\_ki         | Ki                                                                                                                | float    | 4                   | The default value is 0.012         | W/R                               |
| 0X7014    | cur\_filt\_gain | filt\_gain                                                                                                        | float    | 4                   | 0 to 1.0, The default value is 0.1 | W/R                               |
| 0X7016    | loc\_ref        | Position Mode Angle instruction                                                                                   | float    | 4                   | rad                                | W/R                               |
| 0X7017    | limit\_spd      | Location mode (CSP) speed limit                                                                                   | float    | 4                   | 0 to 20rad/s                       | W/R                               |
| 0X7018    | limit\_cur      | Velocity position mode Current limitation                                                                         | float    | 4                   | 0 to 43A                           | W/R                               |
| 0X7019    | mechPos         | Mechanical Angle of the loading coil                                                                              | float    | 4                   | rad                                | R                                 |
| 0X701A    | iqf             | iq Filter                                                                                                         | float    | 4                   | -43 to 43A                         | R                                 |
| 0X701B    | mechVel         | Speed of the load                                                                                                 | float    | 4                   | -20 to 20rad/s                     | R                                 |
| 0X701C    | VBUS            | Bus voltage                                                                                                       | float    | 4                   | V                                  | R                                 |
| 0X701E    | loc\_kpkp       | at                                                                                                                | float    | 4                   | The default is 40                  | W/R                               |
| 0X701F    | spd\_kp         | Indicates the speed kp                                                                                            | float    | 4                   | The default is 6                   | W/R                               |
| 0x7020    | spd\_ki         | ki                                                                                                                | float    | 4                   | The default value is 0.02          | W/R                               |
| 0x7021    | spd\_filt\_gain | Speed filter value                                                                                                | float    | 4                   | The default value is 0.1           | W/R                               |
| 0x7022    | acc\_rad        | velocity mode acceleration                                                                                        | float    | 4                   | The default value is 20rad/s^2     | W/R                               |
| 0x7024    | vel\_max        | Location mode (PP) speed                                                                                          | float    | 4                   | The default value is 10rad/s       | W/R                               |
| 0x7025    | acc\_set        | Location mode (PP) acceleration                                                                                   | float    | 4                   | The default value is 10rad/s^2     | W/R                               |
| 0x7026    | EPScan\_time    | Indicates the report time. 1 indicates 10ms. Plus 1 increments by 5ms                                             | uint16   | 2                   | The default value is 1             | W/R                               |
| 0x7028    | canTimeout      | can The timeout threshold, 20000 is 1s                                                                            | uint32   | 4                   | The default is 0                   | W/R                               |
| 0x7029    | zero\_sta       | Indicates the zero flag bit, 0 means 0-2π and 1 means -π-π                                                        | uint8    | 1                   | The default is 0                   | W/R                               |
| 0x702A    | damper          | Damping switch                                                                                                    | uint8    | 1                   | The default is 0                   | W/R                               |
| 0x702B    | add\_offset     | Zero offset                                                                                                       | float    | 4                   | The default is 0                   | W/R                               |

#### 4.1.15 Read example <a href="#block-33cd4c79856d81a49878f977ef408768" id="block-33cd4c79856d81a49878f977ef408768"></a>

Take reading loc\_kp as an example:

| Size        | Bit28\~bit24 | bit23\~8     | bit7\~0                 | Byte0\~Byte7                              |
| ----------- | ------------ | ------------ | ----------------------- | ----------------------------------------- |
|             | 0x11         | 0x00FD       | 0x7F                    | 1E 70 00 00 00 00 00 00                   |
| Description | Type 1       | Host id 0xFD | Target motor CAN\_ID 7F | Byte0\~1: index, corresponding to loc\_kp |

The feedback instruction is

| Size        | Bit28\~bit24 | bit23\~8                          | bit7\~0      | Byte0\~Byte7                                                                                                                                                                |
| ----------- | ------------ | --------------------------------- | ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|             | 0x11         | 0x00FD                            | 0x7F         | 1E 70 00 00 00 00 00 00                                                                                                                                                     |
| Description | Type 1       | bit15\~8: Target motor CAN\_ID 7F | Host id 0xFD | **Byte0\~1**: index, corresponding to loc\_kp **Byte4\~7**: loc\_kp value 30, highright byte, (32-bit single precision) hexadecimal IEEE-754 standard floating point number |

### 4.2 Motor Function Description <a href="#block-33cd4c79856d81f1972efb46deb97382" id="block-33cd4c79856d81f1972efb46deb97382"></a>

_(If the following features are unavailable, please upgrade to the latest version via the official Git repository.)_

#### 4.2.1 Active Reporting <a href="#block-33cd4c79856d81fbbbbeef19078f4b6a" id="block-33cd4c79856d81fbbbbeef19078f4b6a"></a>

* **Disabled by default**. Enable via **Type 24**.
* Report type: **Type 2** (default interval: **10ms**). Adjust interval by modifying EPScan\_time via **Type 18**.

#### 4.2.2 Zero-Point Flag (zero\_sta) <a href="#block-33cd4c79856d819a9f40f0591c9616db" id="block-33cd4c79856d819a9f40f0591c9616db"></a>

* Modify via:
* **Host computer (software)**
* **Type 18** _(requires saving via **Type 22** for communication)_
* **Default flag**: 0 → Power-on position range: **0–2π**.
* **If set to 1**: Power-on position range: **π–π**.

#### 4.2.3 Type 2 Update <a href="#block-33cd4c79856d811caaabc52a0d4742a2" id="block-33cd4c79856d811caaabc52a0d4742a2"></a>

* Updated to **periodic looping within -4π–4π** (enables cycle counting).
* **Note**: Position interface parameters must be adjusted:
* P\_MIN: -**12.57f**
* P\_MAX: **12.57f**

#### 4.2.4 Protocol Switching (Requires CAN adapter) <a href="#block-33cd4c79856d81feb4fbef11cc548f3d" id="block-33cd4c79856d81feb4fbef11cc548f3d"></a>

* Methods:
* Modify protocol\_1 via host computer.
* Send **Type 25** command.
* **Reboot required** after switching.
* **Post-switch CAN commands:**
* **CANopen**: Send extended frame (protocol switch frame).
* **MIT Protocol**: Send standard frame (**Command 8**).

#### 4.2.5 Post-Power-Off Anti-Backdrive Protection <a href="#block-33cd4c79856d81c4b7a9c080044d0aae" id="block-33cd4c79856d81c4b7a9c080044d0aae"></a>

* **Default**: Motor imposes damping if rotated rapidly while poweredoff (prevents surge).
* Disable: Set damper = 1.

#### 4.2.6 Zero Calibration Rules <a href="#block-33cd4c79856d812581a7ffceef2818d8" id="block-33cd4c79856d812581a7ffceef2818d8"></a>

* **Supported modes: CSP** and **Motion Control**.
* **PP Mode**: Zero calibration is **blocked**.
* **Old vs. New Versions**:
* **Old**: Zero calibration causes large deviation → motor immediately moves to target
* **New (CSP/Motion Control)**: Target updates to 0 instantly →motor remains stationary.

#### 4.2.7 Position Offset (add\_offset) <a href="#block-33cd4c79856d8128beb3f19705b2a123" id="block-33cd4c79856d8128beb3f19705b2a123"></a>

* Example: If offset = 1, the current zero shifts to (**current position +1rad**).
* **Use case**: Bypass mechanical limits (e.g., set zero at 1 rad →power-on treats 1 rad as new zero).

#### 4.2.8 CANopen ID <a href="#block-33cd4c79856d8102b63ce07b42a7c2b9" id="block-33cd4c79856d8102b63ce07b42a7c2b9"></a>

* **Old version**: Fixed to 1.
* **New version**: Matches the **private protocol CAN ID**.

#### 4.2.9 Notes for Implementation <a href="#block-33cd4c79856d817aadafc0c8ef0fc02f" id="block-33cd4c79856d817aadafc0c8ef0fc02f"></a>

* Always **save settings** (e.g., Type 22 for zero\_sta).
* Verify **CAN adapter compatibility** for protocol switching.
* For zero offsets, ensure mechanical safety limits are respected.

### 4.3 Control mode instructions <a href="#block-33cd4c79856d81baaa03dbb1e89d8262" id="block-33cd4c79856d81baaa03dbb1e89d8262"></a>

#### 4.3.1 Operation control mode <a href="#block-33cd4c79856d8199a6e6cc85161c9d86" id="block-33cd4c79856d8199a6e6cc85161c9d86"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/34dd5fa7-ae19-40e3-a173-f6e81e763515/image/w=1920,quality=90,fit=scale-down" alt="image" height="608" width="2582">

The motor is in operation control mode by default after power-on.

Send motor Enable Run frame (communication type 3) --> Send operation mode motor control command (communication type 1) --> Receive motor feedback frame (communication type 2)

Operation control mode description: The control logic of the operation and control mode is t\_ref=Kd \* (v\_vset-v\_actual)+Kp \* (p\_set-p\_actual)+t\_ff. Tref is converted to the expected iq current through an internal formula and output through the current loop Simple control demonstration: Set t\_ff to 0, v\_vset to1, Kd to 1, p\_set to 0, Kp to 0. If there is no external load on the motor, it will run at a speed of 1rad/s. If there is an external load, kd needs to be increased to resist the external load Set t\_ff to 0, v\_vset to 0, Kd to 1, p\_set to 0, Kp to 0, the motor is in damping mode. When the motor is externally rotated, a damping is applied, which increases with the increase of kd. It should be noted that the motor generates electricity under this condition and requires power supply to prevent overvoltage Set t\_ff to 0, v\_vset to 0, Kd to 1, p\_set to5, Kp to 1. If there is no external load on the motor, it will run to the target position of 5. Increasing kp will increase the force required to maintain the target position, and kd is damping. Without kd, the motor will sway to the target position

#### 4.3.2 Current mode <a href="#block-33cd4c79856d814bbddbc3d0c1a3f504" id="block-33cd4c79856d814bbddbc3d0c1a3f504"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/1959b9c2-fc2f-45c2-b317-796093a41b6b/image/w=1920,quality=90,fit=scale-down" alt="image" height="722" width="2474">

Send motor mode parameter write command (communication type 18) Set the runmode parameter to 3 --> Send motor Enable run frame (communication type 3) --> Send motor mode parameter write command (communication type 18) set the iq\_ref parameter to the default current instruction

#### 4.3.3 Velocity mode <a href="#block-33cd4c79856d81d38297f44aff0e9e7f" id="block-33cd4c79856d81d38297f44aff0e9e7f"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/a19898ea-15a6-42e4-a571-e30ca122c741/image/w=1920,quality=90,fit=scale-down" alt="image" height="524" width="2576">

Send motor mode parameter write command (communication type 18) Set the runmode parameter to 2 --> Send motor Enable run frame (communication type 3) --> Send motor mode parameter write command (communication type 18) set limit\_cur parameter as default maximum current instruction-->Send motor mode parameter write command (communication type 18) Set acc\_rad parameter as default acceleration instruction --> Send motor mode parameter write command (communication type 18) Set spd\_ref parameter as default speed instruction

#### 4.3.4 Location Mode (CSP) <a href="#block-33cd4c79856d81fb98dee6ea9114d244" id="block-33cd4c79856d81fb98dee6ea9114d244"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/39753d84-20fa-4f01-93a1-e8b7e7017569/image/w=1920,quality=90,fit=scale-down" alt="image" height="464" width="2592">

Send motor mode parameter write command (communication type 18) Set the runmode parameter to 5 --> Send motor Enable run frame (communication type 3) --> Send motor mode parameter write command (communication type 18) set limit\_spd parameter as default maximum speed instruction -->Send motor mode parameter write command (communication type 18) Sets loc\_ref parameter as default position instruction

#### 4.3.5 Location Mode (PP) <a href="#block-33cd4c79856d81c687e6f564af31b496" id="block-33cd4c79856d81c687e6f564af31b496"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/7a59549c-7803-4ed5-acd3-60b14c7346e2/image/w=1920,quality=90,fit=scale-down" alt="image" height="554" width="2562">

Send motor mode parameter write command (communication type 18) Set the runmode parameter to 1 --> Send motor Enable run frame (communication type 3) --> Send motor mode parameter write command (communication type 18) set The vel\_max parameter is the default maximum speed instruction--> Send motor mode parameter write command (communication type 18) Set the acc\_set parameter to the default acceleration instruction -->Send motor mode parameter write command (communication type 18) Set the loc\_ref parameter to the default position instruction

**Note: This mode does not support changing the speed and acceleration during operation. If you want to make an emergency stop, you can change vel\_max to 0 during the process, and it will stop at the current speed and acceleration plan**

#### 4.3.6 Stop running <a href="#block-33cd4c79856d81dc9cebe358812c3427" id="block-33cd4c79856d81dc9cebe358812c3427"></a>

Sending motor stop frame (communication type 4)

### 4.4 Program sample <a href="#block-33cd4c79856d81e7b1f8c6add98f8cba" id="block-33cd4c79856d81e7b1f8c6add98f8cba"></a>

Examples of various mode control motors are provided below (take gd32f303as an example)

The following are library, function, and macro definitions for the various instances

Copy

```cpp
#define P_MIN -12.57f //0.0.2.6 is 12.5 before and 12.57 after
#define P_MAX 12.57f //0.0.2.6 is 12.5 before and 12.57 after
#define V_MIN 33.0f
#define V_MAX 33.0f
#define KP_MIN 0.0f
#define KP_MAX 500.0f
#define KD_MIN 0.0f
#define KD_MAX 5.0f
#define T_MIN -14.0f
#define T_MAX 14.0f

struct exCanIdInfo {
  uint32_t id:8;
  uint32_t data:16;
	uint32_t mode:5;
  uint32_t res:3;
};

can_receive_message_struct rxMsg;
can_trasnmit_message_struct txMsg = {
  .tx_sfid = 0,
  .tx_efid = 0xff,
  .tx_ft = CAN_FT_DATA,
  .tx_ff = CAN_FF_EXTENDED,
  .tx_dlen = 8, 
};

#define txCanIdEx (*((struct exCanIdInfo*)&(txMsg.tx_efid)))
#define rxCanIdEx (*((struct exCanIdInfo*)&(rxMsg.rx_efid))) //Parses the extended frame id into a custom data structure

int float_to_uint(float x, float x_min, float x_max, int bits) {
  float span = x_max - x_min;
  float offset = x_min;
  if(x > x_max) x = x_max;
  else if(x < x_min) x = x_min;
  return (int) ((x-offset)*((float)((1<<bits)-1))/span);
}

#define can_txd() can_message_transmit(CAN0, &txMsg)
#define can_rxd() can_message_receive(CAN0, CAN_FIFO1, &rxMsg)
```

The following lists the common types of communication sent:

#### 4.4.1 Motor Enabled Run frame (communication type 3) <a href="#block-33cd4c79856d8135979cd30aa5781bf8" id="block-33cd4c79856d8135979cd30aa5781bf8"></a>

Copy

```cpp
void motor_enable(uint8_t id, uint16_t master_id) {
  txCanIdEx.mode = 3;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = master_id;
  txMsg.tx_dlen = 8;
  txCanIdEx.data = 0;
  can_txd();
}
```

#### 4.4.2 Operation control mode Motor control instruction (communication type 1) <a href="#block-33cd4c79856d81ff8e54cf39ac087958" id="block-33cd4c79856d81ff8e54cf39ac087958"></a>

Copy

```cpp
void motor_controlmode(uint8_t id, float torque, float MechPosition, float
speed, float kp, float kd) {
  txCanIdEx.mode = 1;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = float_to_uint(torque,T_MIN,T_MAX,16);
  txMsg.tx_dlen = 8;
  txMsg.tx_data[0]=float_to_uint(MechPosition,P_MIN,P_MAX,16)>>8;
  txMsg.tx_data[1]=float_to_uint(MechPosition,P_MIN,P_MAX,16);
  txMsg.tx_data[2]=float_to_uint(speed,V_MIN,V_MAX,16)>>8;
  txMsg.tx_data[3]=float_to_uint(speed,V_MIN,V_MAX,16);
  txMsg.tx_data[4]=float_to_uint(kp,KP_MIN,KP_MAX,16)>>8;
  txMsg.tx_data[5]=float_to_uint(kp,KP_MIN,KP_MAX,16);
  txMsg.tx_data[6]=float_to_uint(kd,KD_MIN,KD_MAX,16)>>8;
  txMsg.tx_data[7]=float_to_uint(kd,KD_MIN,KD_MAX,16);
  can_txd();
}
```

#### 4.4.3 Motor stop frame (communication type 4) <a href="#block-33cd4c79856d8125bb43cc7e9b27ae9b" id="block-33cd4c79856d8125bb43cc7e9b27ae9b"></a>

Copy

```cpp
void motor_reset(uint8_t id, uint16_t master_id) {
  txCanIdEx.mode = 4;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = master_id;
  txMsg.tx_dlen = 8;
  for(uint8_t i=0; i<8; i++) {
    txMsg.tx_data[i]=0;
  }
  can_txd();
}
```

#### 4.4.4 Motor mode parameter write command (communication type 18, running mode switch) <a href="#block-33cd4c79856d81d586f2fac5378b02f6" id="block-33cd4c79856d81d586f2fac5378b02f6"></a>

Copy

```cpp
uint8_t runmode;
uint16_t index;
void motor_modechange(uint8_t id, uint16_t master_id) {
  txCanIdEx.mode = 0x12;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = master_id;
  txMsg.tx_dlen = 8;
  for(uint8_t i=0; i<8; i++) {
    txMsg.tx_data[i] = 0;
  }
  memcpy(&txMsg.tx_data[0], &index, 2);
  memcpy(&txMsg.tx_data[4], &runmode, 1);
  can_txd();
}
```

#### 4.4.5 Motor mode parameter write command (communication type 18, control parameter write) <a href="#block-33cd4c79856d81b48210ebde7990d3c0" id="block-33cd4c79856d81b48210ebde7990d3c0"></a>

Copy

```cpp
uint16_t index;
float ref;
void motor_write(uint8_t id, uint16_t master_id) {
  txCanIdEx.mode = 0x12;
  txCanIdEx.id = id;
  txCanIdEx.res = 0;
  txCanIdEx.data = master_id;
  txMsg.tx_dlen = 8;
  for(uint8_t i=0;i<8;i++) {
    txMsg.tx_data[i]=0;
  }
  memcpy(&txMsg.tx_data[0],&index,2);
  memcpy(&txMsg.tx_data[4],&ref,4);
  can_txd();
}
```

## 5. Explanation of Canopen Communication Protocol Types <a href="#block-33cd4c79856d813987a1cadfa9bcbc99" id="block-33cd4c79856d813987a1cadfa9bcbc99"></a>

### 5.1 Introduction to CANopen Communication <a href="#block-33cd4c79856d817b823ef99d0fa402bb" id="block-33cd4c79856d817b823ef99d0fa402bb"></a>

CANopen is a "higher-level protocol" based on the CAN bus. This means that theCAN bus (ISO 11898) acts like a container truck, serving as the "transportation vehicle" for CANopen information. CAN simply implements the transmission of frames with an 11-bit CAN ID, a Remote Transmission (RTR) bit, and 64 data bits(related to higher-level protocols). The CAN bus plays the same role in CANopen as it does in the J1939 protocol. CANopen implements Layer 7 of the OSI model and is compatible with other data link layer protocols besides CAN.Please download the necessary EDS files for CANopen from the official website download center at [www.robstride.com](http://www.robstride.com/).

### 5.2 Canopen Protocol Message Classification <a href="#block-33cd4c79856d81878822c9cfd8965084" id="block-33cd4c79856d81878822c9cfd8965084"></a>

| Classification                     | Function                                                                                                                                                                                                                                                                                                    |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NMT Network Management Messages    | Manage the network and switch node states. NMT network management messages are typically sent by the master station                                                                                                                                                                                         |
| SDO Service Data Object Message    | Used for setting device parameters or transmitting critical data. Typically, the master station initiates an SDO message, and the slave station responds. However, a slave station canal so initiate an SDO message, with the master station responding, for example, in the transmission of critical data. |
| PDO (Process Data Object) messages | Transmit process data from various devices, such as temperature and speed. Both the master and slave stations send these messages.                                                                                                                                                                          |
| EMCY Emergency Message             | Transmits fault information about the transmission equipment. Both the master and slave stations send this message.                                                                                                                                                                                         |
| SYNC Synchronization Message       | Synchronization data, used to synchronize TPDO data on the slave station. Generally sent by the master station.                                                                                                                                                                                             |
| NODE GUARDING Message              | The master station requests the slave station's status; the master station queries, and the slave station responds.                                                                                                                                                                                         |
| Heartbeat Message                  | A device actively sends a heartbeat to indicate that it is online. Both the master and slave devices can send heartbeats.                                                                                                                                                                                   |

### 5.3 State Machine Description <a href="#block-33cd4c79856d81dea5d1f6f3ed6cfc14" id="block-33cd4c79856d81dea5d1f6f3ed6cfc14"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/48518d23-ee01-42f7-b334-e40407d69dab/image/w=1920,quality=90,fit=scale-down" alt="image" height="961.4701378254211" width="720">

**Motor Enable:**

When initially powered on, the motor defaults to the **SWITCH\_ON\_DISABLED** state. To transition to **OPERATION\_ENABLE**, modify the **Controlword(6040H)** to **6, 7, or 15** (step-by-step transition), or directly set it to **15** for immediate enablement.

**Stopping the Motor:**

If the motor is in **OPERATION\_ENABLE** state and needs to stop normally, modify the **Controlword (6040H)** to **1**. The motor will return to the disabled state (**SWITCH\_ON\_DISABLED**).

**Emergency Stop (Use with Caution—Risk of Voltage Surge):**

During operation, an emergency stop can be triggered by setting the **Controlword (6040H)** to **11**.

**Fault Clearance:**

If the motor enters a **FAULT** state due to protection mechanisms, modifying the **Controlword (6040H)** can clear standard errors.

**Important Note:**

Mode changes for this motor must be performed in the **disabled state** (**SWITCH\_ON\_DISABLED**). Ensure the desired mode is configured **before** enabling **OPERATION\_ENABLE** to avoid unexpected behavior.

### 5.4 Status Feedback Parameters <a href="#block-33cd4c79856d810697a9cc707fe1f9cc" id="block-33cd4c79856d810697a9cc707fe1f9cc"></a>

| **Index** | **Name**                      | **Attribute** | **Type**   | **Unit**                       |
| --------- | ----------------------------- | ------------- | ---------- | ------------------------------ |
| 603F      | Error\_code                   | Read-only     | UINTEGER16 | /                              |
| 6041      | Statusword                    | Read-only     | UINTEGER16 | /                              |
| 6061      | Modes\_of\_operation\_display | Read-only     | INTEGER8   | /                              |
| 6062      | Position\_demand\_value       | Read-only     | INTEGER32  | Pulses (1 rev =16,384 pulses)  |
| 6064      | Position\_actual\_value       | Read-only     | INTEGER32  | Pulses (1 rev =16,384 pulses)  |
| 606B      | Velocity\_demand\_value       | Read-only     | INTEGER32  | 0.1 rpm                        |
| 606C      | Velocity\_actual\_value       | Read-only     | INTEGER32  | 0.1 rpm                        |
| 6077      | Torque\_actual\_value         | Read-only     | INTEGER16  | 0.1% load ratio (1000= 20 N·m) |
| 6078      | Current\_actual\_value        | Read-only     | INTEGER16  | mA                             |
| 6079      | DC\_link\_circuit\_voltage    | Read-only     | INTEGER32  | mV                             |

### 5.5 Homing Mode (Zero Position Setting) <a href="#block-33cd4c79856d811a8d80d782868078f6" id="block-33cd4c79856d811a8d80d782868078f6"></a>

| **Index** | **Name**           | **Attribute** | **Type**   | **Unit** |
| --------- | ------------------ | ------------- | ---------- | -------- |
| 6040      | Controlword        | Read-write    | UINTEGER16 | /        |
| 6060      | Modes of operation | Read-write    | INTEGER8   | /        |

**Homing method:**

* Set **Modes of operation to 6** while the motor is in the **disabled state (SWITCH\_ON\_DISABLED)**. The motor will then define the current position as the zero point.
* To **hold the zero position**, modify the **Controlword to 15**, and the motor will maintain its position at the home location.

### 5.6 Position Mode (PP - Profile Position) <a href="#block-33cd4c79856d8115bfd8f4574b8d7f53" id="block-33cd4c79856d8115bfd8f4574b8d7f53"></a>

| **Index** | **Name**               | **Attribute** | **Type**   | **Unit**                       |
| --------- | ---------------------- | ------------- | ---------- | ------------------------------ |
| 6040      | Controlword            | Read-write    | UINTEGER16 | /                              |
| 6060      | Modes of operation     | Read-write    | INTEGER8   | /                              |
| 6067      | Position\_window       | Read-write    | UINTEGER32 | Pulses (1 rev =16,384 pulses)  |
| 6068      | Position\_window\_time | Read-write    | UINTEGER16 | ms                             |
| 6071      | Target\_torque         | Read-write    | INTEGER16  | 0.1% load ratio (1000= 20 N·m) |
| 607A      | Target\_position       | Read-write    | INTEGER32  | Pulses (1 rev =16,384 pulses)  |
| 6081      | Profile\_velocity      | Read-write    | UINTEGER32 | 0.1 rpm                        |
| 6083      | Profile\_acceleration  | Read-write    | UINTEGER32 | 0.1 rpm/s                      |

**Steps to Configure Position Mode (PP):**

1. While the motor is in the **disabled state** (**SWITCH\_ON\_DISABLED**), set **Modes of operation to 1**.
2. **Mandatory parameters:**
3. **Target\_torque** (absolute max torque in position mode)
4. **Profile\_velocity** (absolute speed in position mode)
5. **Profile\_acceleration** (absolute acceleration in position mode)
6. **Optional parameters:**
7. **Position\_window** (if not set, window check is disabled)
8. **Position\_window\_time** (if not set, window check is disabled)
9. Set **Controlword (6040) to 15** to enable operation.
10. Set **Target\_position (absolute position)** to move the motor to the desired position.

### 5.7 Position Mode (CSP - Cyclic Synchronous Position) <a href="#block-33cd4c79856d81a592abe3f15bd5ef5c" id="block-33cd4c79856d81a592abe3f15bd5ef5c"></a>

| **Index** | **Name**               | **Attribute** | **Type**   | **Unit**                       |
| --------- | ---------------------- | ------------- | ---------- | ------------------------------ |
| 6040      | Controlword            | Read-write    | UINTEGER16 | /                              |
| 6060      | Modes of operation     | Read-write    | INTEGER8   | /                              |
| 6067      | Position\_window       | Read-write    | UINTEGER32 | Pulses (1 rev =16,384 pulses)  |
| 6068      | Position\_window\_time | Read-write    | UINTEGER16 | ms                             |
| 6071      | Target\_torque         | Read-write    | INTEGER16  | 0.1% load ratio (1000= 20 N·m) |
| 607A      | Target\_position       | Read-write    | INTEGER32  | Pulses (1 rev =16,384 pulses)  |
| 6081      | Profile\_velocity      | Read-write    | UINTEGER32 | 0.1 rpm                        |

**Steps to Configure Position Mode (CSP):**

1. While the motor is in the disabled state (SWITCH\_ON\_DISABLED), set Modes of operation to 5.
2. **Mandatory parameters:**
3. **Target\_torque** (absolute max torque in position mode)
4. **Profile\_velocity** (absolute speed in position mode)
5. **Optional parameters:**
6. **Position\_window** (0 = disabled)
7. **Position\_window\_time** (0 = disabled)
8. Set **Controlword (6040) to 15** to enable operation.
9. **Set Target\_position** (absolute position) to move the motor to the desired position.

### 5.8 Velocity Mode <a href="#block-33cd4c79856d8103822be3b2729dab10" id="block-33cd4c79856d8103822be3b2729dab10"></a>

| **Index** | **Name**           | **Attribute** | **Type**   | **Unit**                       |
| --------- | ------------------ | ------------- | ---------- | ------------------------------ |
| 6040      | Controlword        | Read-write    | UINTEGER16 | /                              |
| 6060      | Modes of operation | Read-write    | INTEGER8   | /                              |
| 6071      | Target\_torque     | Read-write    | INTEGER16  | 0.1% load ratio (1000= 20 N·m) |
| 60FF      | Target\_velocity   | Read-write    | INTEGER32  | 0.1 rpm                        |

**Steps to Configure Velocity Mode:**

1. While the motor is in the **disabled state (SWITCH\_ON\_DISABLED)**, set **Modes of operation to 3**.
2. **Mandatory parameter:**
3. **Target\_torque** (absolute max torque in velocity mode)
4. Set **Controlword (6040) to 15** to enable operation.
5. **Set Target\_velocity** to reach the desired speed.

### 5.9 Torque Mode <a href="#block-33cd4c79856d81ecb05ec3683614358e" id="block-33cd4c79856d81ecb05ec3683614358e"></a>

| **Index** | **Name**           | **Attribute** | **Type**   | **Unit**                       |
| --------- | ------------------ | ------------- | ---------- | ------------------------------ |
| 6040      | Controlword        | Read-write    | UINTEGER16 | /                              |
| 6060      | Modes of operation | Read-write    | INTEGER8   | /                              |
| 6071      | Target\_torque     | Read-write    | INTEGER16  | 0.1% load ratio (1000= 20 N·m) |

**Steps to Configure Torque Mode:**

1. While the motor is in the **disabled state (SWITCH\_ON\_DISABLED)**, set **Modes of operation to 4**.
2. Set **Controlword (6040) to 15** to enable operation.
3. **Set Target\_torque** to output the desired torque.

### 5.10 Protocol Switching (Extended Frame): SwitchMotor Protocol (Takes Effect After Power Cycle) <a href="#block-33cd4c79856d817190f3d6d70770e75f" id="block-33cd4c79856d817190f3d6d70770e75f"></a>

| Data Field  | 29-bit ID | 8-Byte Data Area         |
| ----------- | --------- | ------------------------ |
| Size        | Bit 28\~0 | Byte 0\~6                |
| Description | 0xFFF     | 01 02 03 04 05 06 F\_CMD |

* **F\_CMD** (Byte 6) defines the motor protocol:
* **0:** Private protocol (default)
* **1:** CANopen protocol
* **2:** MIT protocol

**Response Frame:**

| Data Field  | 11-bit ID | 8-Byte Data Area             |
| ----------- | --------- | ---------------------------- |
| Size        | Bit 10\~0 | Byte 0\~7                    |
| Description | Motor ID  | 64-bit MCU unique identifier |

## 6. MIT Communication Protocol Description <a href="#block-33cd4c79856d819cb512d6956224f854" id="block-33cd4c79856d819cb512d6956224f854"></a>

The motor communication adopts the CAN 2.0 interface with a default baud rate of 1 Mbps. The baud rate can be modified by switching to the private protocol. The standard frame format is as follows:

| Data Field  | 11-bit ID |          | 8-byte Data Area |
| ----------- | --------- | -------- | ---------------- |
| Size        | Bit 10\~8 | Bit 7\~0 | Byte 0\~7        |
| Description | Mode type | ID       |                  |

Supported Control Modes:

* **MIT Mode**: Provides five motion control parameters to the motor.
* **Velocity Mode**: Specifies the target speed for the motor.
* **Position Mode**: Specifies the target position and speed, allowing the motor to run to the designated position at the configured speed.

### 6.1 Response Command 1: Data Feedback(Motor Status) <a href="#block-33cd4c79856d8197b63df13668cdb99b" id="block-33cd4c79856d8197b63df13668cdb99b"></a>

| Data Field  | 11-bit ID | 8-byte Data Area                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ----------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Size        | Bit 10\~0 | Byte 0\~7                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| Description | Host ID   | **Byte 0**: Motor CAN ID **Byte 1\~2**: The current angle \[0\~65535], corresponds to (-12.57rad \~ 12.57 rad) **Byte 3** (high 8 bits), **Byte 4** \[7-4] (low 4 bits): The current speed\[0\~4096], corresponds to (-33 rad/s \~ 33 rad/s) **Byte 4** \[3-0] (high 4 bits), **Byte 5** (low 8 bits): The current torque\[0\~4096], corresponds to (-60 N·m \~ 60 N·m) **Byte 6\~7**: Winding temperature (in degrees)：Temp(Celsius) \*10 |

### 6.2 Response Command 2: MCU Identification <a href="#block-33cd4c79856d81dea7c6d5339eb7e01e" id="block-33cd4c79856d81dea7c6d5339eb7e01e"></a>

| Data Field  | 11-bit ID | 8-byte Data Area             |
| ----------- | --------- | ---------------------------- |
| Size        | Bit 10\~0 | Byte 0\~7                    |
| Description | Motor ID  | 64-bit MCU unique identifier |

### 6.3 Command 1: Enable Motor Operation <a href="#block-33cd4c79856d81a8933fc1ef5c6326c1" id="block-33cd4c79856d81a8933fc1ef5c6326c1"></a>

| Data Field  | 11-bit ID           | 8-byte Data Area        |
| ----------- | ------------------- | ----------------------- |
| Size        | Bit 10\~0           | Byte 0\~7               |
| Description | Target motor CAN ID | FF FF FF FF FF FF FF FC |

**Response**: Response Command 1

### 6.4 Command 2: Stop Motor Operation <a href="#block-33cd4c79856d8102b37cf6ddbe04b44d" id="block-33cd4c79856d8102b37cf6ddbe04b44d"></a>

| Data Field  | 11-bit ID           | 8-byte Data Area        |
| ----------- | ------------------- | ----------------------- |
| Size        | Bit 10\~0           | Byte 0\~7               |
| Description | Target motor CAN ID | FF FF FF FF FF FF FF FD |

**Response**: Response Command 1

### 6.5 Command 3: MIT Dynamic Parameters <a href="#block-33cd4c79856d8138a6caf98fdf995d2d" id="block-33cd4c79856d8138a6caf98fdf995d2d"></a>

| Data Field | 11-bit ID | 8-byte Data Area                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size       | Bit 10\~0 | **Byte 0\~1**: Target angle \[0\~65535], (-12.57 rad \~ 12.57 rad) **Byte 2 (high 8 bits), Byte 3\[7-4] (low 4 bits)**: Target speed \[0\~4096], (-33 rad/s \~ 33 rad/s) **Byte 3\[3-0] (high 4 bits), Byte 4 (low 8 bits)**: Kp\[0\~4096], (0\~500) **Byte 5 (high 8 bits), Byte 6\[7-4] (low 4 bits)**: Kd\[0\~4096], (0\~5) **Byte 6\[3-0] (high 4 bits), Byte 7 (low 8 bits)**: Target torque \[0\~4096], (-60 N·m \~ 60 N·m) |

**Response**: Response Command 1

### 6.6 Command 4: Set Zero Position (Non-Position Mode) <a href="#block-33cd4c79856d81bbb613c1dd7e887bff" id="block-33cd4c79856d81bbb613c1dd7e887bff"></a>

| Data Field  | 11-bit ID           | 8-byte Data Area        |
| ----------- | ------------------- | ----------------------- |
| Size        | Bit 10\~0           | Byte 0\~7               |
| Description | Target motor CAN ID | FF FF FF FF FF FF FF FE |

**Response**: Response Command 1

### 6.7 Command 5: Clear Errors \&Read Fault Status <a href="#block-33cd4c79856d81f19e16c5c79e966c04" id="block-33cd4c79856d81f19e16c5c79e966c04"></a>

| Data Field | 11-bit ID | 8-byte Data Area                                                                                                                |
| ---------- | --------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Size       | Bit 10\~0 | FF FF FF FF FF FF F\_CMD FBF\_CMD:- 0xFF → Clear current fault- Any other value → Returns fault value in Byte 1 of the response |

**Response (Fault Clear)**: Response Command 1

**Fault Status Response:**

| Data Field | 11-bit ID | 8-byte Data Area                                                                                                                                                                                                                                                                                                       |
| ---------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Size       | Bit 10\~0 | **Byte 0**: Motor CAN ID **Byte 1\~4**: Fault value (Non-zero: Fault present; 0: Normal) **Bit 14**: Stall/I²t overload fault **Bit 7**: Encoder not calibrated **Bit 3**: Overvoltage fault **Bit 2**: Undervoltage fault **Bit 1**: Driver IC fault **Bit 0**: Motor overtemperature fault (Default threshold:145°C) |

### 6.8 Command 6: Set Operation Mode <a href="#block-33cd4c79856d81bcba6ef6e4897ed059" id="block-33cd4c79856d81bcba6ef6e4897ed059"></a>

| Data Field | 11-bit ID | 8-byte Data Area                                                                                        |
| ---------- | --------- | ------------------------------------------------------------------------------------------------------- |
| Size       | Bit 10\~0 | FF FF FF FF FF FF F\_CMD FCF\_CMD: Mode type- 0: MIT mode (default)- 1: Position mode- 2: Velocity mode |

**Response**: Response Command 1

### 6.9 Command 7: Modify Motor CAN ID <a href="#block-33cd4c79856d811281cbe55071880b24" id="block-33cd4c79856d811281cbe55071880b24"></a>

| Data Field | 11-bit ID | 8-byte Data Area                                                      |
| ---------- | --------- | --------------------------------------------------------------------- |
| Size       | Bit 10\~0 | Size Bit 10\~0 FF FF FF FF FF FF F\_CMD FAF\_CMD: Target motor CAN ID |

**Response**: Response Command 2

### 6.10 Command 8: Change Communication Protocol (Takes Effect After Power Cycle) <a href="#block-33cd4c79856d81c59f77ea5a75f0b7d2" id="block-33cd4c79856d81c59f77ea5a75f0b7d2"></a>

| Data Field | 11-bit ID | 8-byte Data Area                                                                                          |
| ---------- | --------- | --------------------------------------------------------------------------------------------------------- |
| Size       | Bit 10\~0 | FF FF FF FF FF FF F\_CMD FDF\_CMD: Protocol type 0: Private protocol (default) 1: CANopen 2: MIT protocol |

**Response**: Response Command 2

### 6.11 Command 9: Modify Host CAN ID <a href="#block-33cd4c79856d81da9cbbd0c12aa373ef" id="block-33cd4c79856d81da9cbbd0c12aa373ef"></a>

| Data Field | 11-bit ID | 8-byte Data Area                               |
| ---------- | --------- | ---------------------------------------------- |
| Size       | Bit 10\~0 | FF FF FF FF FF FF F\_CMD 01F\_CMD: Host CAN ID |

**Response**: Response Command 2

### 6.12 Command 10: Position Mode Control Command <a href="#block-33cd4c79856d815cacbdf03ce6d52f9c" id="block-33cd4c79856d815cacbdf03ce6d52f9c"></a>

| Data Field  | 11-bit ID |                     | 8-byte Data Area                                                                                     |
| ----------- | --------- | ------------------- | ---------------------------------------------------------------------------------------------------- |
| Size        | Bit 10\~8 | Bit 7\~0            | **Byte 0\~3**: Target position (rad, 32-bit float) **Byte 4\~7**: Target speed (rad/s, 32-bit float) |
| Description | 1         | Target motor CAN ID | Target motor CAN ID                                                                                  |

**Response**: Response Command 1

### 6.13 Command 11: Velocity Mode Control Command <a href="#block-33cd4c79856d81859bf0d82e3e52e2d0" id="block-33cd4c79856d81859bf0d82e3e52e2d0"></a>

| Data Field  | 11-bit ID |                     | 8-byte Data Area                                                                                                        |
| ----------- | --------- | ------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Size        | Bit 10\~8 | Bit 7\~0            | **Byte 0\~3**: Target speed (rad/s, 32-bit float) **Byte 4\~7**: Current limit in speed/position mode (A, 32-bit float) |
| Description | 2         | Target motor CAN ID | Target motor CAN ID                                                                                                     |

**Response**: Response Command 1

### 6.14 Motion Control Mode <a href="#block-33cd4c79856d81d8aafee5c45dcb2e97" id="block-33cd4c79856d81d8aafee5c45dcb2e97"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/3f91e610-4eb3-447e-ad66-11452905aa86/image/w=1920,quality=90,fit=scale-down" alt="image" height="568" width="2526">

The motor defaults to Motion Control Mode upon power-up.

1. Send the _Motor Enable Command_ (Command 1).
2. Send the _Motion Control Command_ (Command 3) to activate dynamic parameter control.
3. Send the _Motor Stop Command_ (Command 2) to halt operation when needed.

### 6.15 Velocity Mode <a href="#block-33cd4c79856d8116b0e8f5dda1f6401b" id="block-33cd4c79856d8116b0e8f5dda1f6401b"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/25f04a1b-775a-4cd5-a24e-1cf738021636/image/w=1920,quality=90,fit=scale-down" alt="image" height="528" width="2514">

1. Configure the motor's operation mode by sending _Set Operation Mode Command_ (Command 6) with **Mode = 2 (Velocity Mode).**
2. Send the _Motor Enable Command_ (Command 1) to activate the motor.
3. Send the _Velocity Mode Control Command_ (Command 11) to set the **maximum current (absolute value)** and **target speed**.
4. To stop, send the _Motor Stop Command_ (Command 2).

### 6.16 Position Mode (CSP - Cyclic Synchronous Position) <a href="#block-33cd4c79856d81d7822ac322bd1d7717" id="block-33cd4c79856d81d7822ac322bd1d7717"></a>

<img src="https://images.spr.so/cdn-cgi/imagedelivery/j42No7y-dcokJuNgXeA0ig/6bc2d8f3-920c-4ac1-81ef-6db4de105119/image/w=1920,quality=90,fit=scale-down" alt="image" height="489.99999999999994" width="2586">

1. Configure the motor's operation mode by sending Set _Operation Mode Command_ (Command 6) with **Mode = 1 (Position Mode)**.
2. Send the _Motor Enable Command_ (Command 1) to activate the motor.
3. Send the _Position Mode Control Command_ (Command 10) to set the **maximum speed (absolute value)** and **target position**.
4. To stop, send the _Motor Stop Command_ (Command 2).
