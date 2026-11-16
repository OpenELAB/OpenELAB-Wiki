---
description: >-
  User guide for the DOBOT CRA/CRV welding process package, covering welder
  connections, software setup, arc and laser welding, process functions, seam
  tracking, intelligent welding assistance, template
---

# DOBOT Welding Process Package User Guide

## DOBOT Collaborative Robot Welding Solution Without Robot Arm

{% embed url="https://openelab.io/products/dobot-welding-platform-robot-excluded" %}

## DOBOT Intelligent Welding Assistant for CR5A / CR10A

{% embed url="https://openelab.io/products/dobot-intelligent-welding-assistant" %}

## Contents

* Preface
* 1\. Introduction
* 2\. Welder Connection
* 3\. Software Installation and Configuration
* 4\. Basic Welding (Arc Welding)
* 5\. Basic Welding (Laser Welding)
* 6\. Weaving Process
* 7\. Multi-Station Welding
* 8\. Intermittent Welding
* 9\. Laser Positioning and Tracking
* 10\. Touch Positioning
* 11\. Multi-layer Multi-pass Welding
* 12\. Through-Arc Seam Tracking (TAST)
* 13\. Fast Programming
* 14\. Welding Control Box
* 15\. Intelligent Welding Assistant
* 16\. Welding Template
* 17\. External Axis
* Appendix A Script Programming
* Appendix B Modbus Register Data

## Preface

Purpose This manual describes the operation process of CRA/CRV robot arm welding process package, so that users can understand and use CRA/CRV robot arm for welding operation. Intended audience This document is intended for:

* Customer Engineer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Supporting version Product Version V4 welding plugin Weld\_v2.4.1-stable For PC: DobotStudioPro4.6-4.6.2.1-Weld-stable and above For App: DobotStudioPro-App-4.6.2.1-weld-stable or above DobotStudio Pro For Teach Pendent: DobotStudioPro-4.6.2.1-weld-TP-stable and above Controller firmware 4.6.2.2-weld-stable

**NOTICE**

To upgrade the plugin and operating software using the teach pendant, you'll need a USB drive. For details on how to upgrade the controller, please refer to the DOBOT Robot Maintenance Tool User Guide.

Related documents Document NOTE Download link Explores the features and operation of DobotStudio Pro User DobotStudio Pro, the control software Download Center Guide designed for Dobot collaborative robots. Explains how to use the Teach DOBOT Cobot Teach Pendant that accompanies the Download Center Pendant User Guide collaborative robot. Describes how to perform firmware DOBOT Robot upgrades, controller file backups, and Contact technical Maintenance Tool User restorations for DOBOT robots using support for access. Guide the maintenance tool. ForceControl Plugin Describes how to use the six-axis Contact technical User Guide force sensor plugin for the CRA robot. support for access. Describes how to use the secondary DOBOT TCP\_IP development interface based on Remote Control Contact technical TCP/IP protocol. You can also find Interface Guide support for access. development DEMOs in various (Welding) languages on GitHub. Introduces the functions, technical DOBOT CRA Series specifications, and installation Download Center Hardware User Guide instructions for DOBOT CRA series collaborative robots. Introduces the functions, technical DOBOT CRV Series specifications, and installation Contact technical Hardware User Guide instructions for DOBOT CRV series support for access. collaborative robots. Revised content Date Version Revised content 2026/08/11 V2.4.1 Add a description of EWM configuration parameters Corresponding to welding process package plug-in version 2026/04/09 V2.4.1 V2-4-1 Corresponding to welding process package plug-in

* version V2-4-0 Added Fast Programming feature
*

2025/09/05 V2.4.0 Optimized arc welding template

*

Optimized intermittent welding, TAST, and multi-pass

* welding functions

Date Version Revised content 2025/05/08 V2.3.0 The fourth release, corresponding to the plugin V2-3-0 2024/10/25 V2.2.0 The third release, corresponding to the plugin V2-2-0 2024/05/16 V2.1.1 The second release, corresponding to the plugin V2-1-1 2023/12/20 V2.0.0 The first release, corresponding to the plugin V2-0-0 Symbol conventions The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided,

**DANGER**

could result in death or serious injury. Indicates a hazard with a medium level or low level of risk which, if

**WARNING not avoided, could result in minor or moderate injury, robot arm**

damage. Indicates a potentially hazardous situation which, if not avoided,

**NOTICE**

could result in robot arm damage, data loss, or unanticipated result. Provides additional information to emphasize or supplement

**NOTE**

important points in the main text.

## 1. Introduction

The DOBOT collaborative robot welding process package is primarily designed to be used in conjunction with the CRA/CRV series robots for welding operations. The package integrates the underlying control algorithm, allows users to quickly implement various welding applications by combining with different ecological components. The package is compatible with multiple mainstream welders, enabling users to build their own welding system based on their actual needs. With easy-to-operate software interface, users can achieve flexible and efficient welding production with only a few steps. The welding process package is designed as a plugin for use with DobotStudio Pro. For instructions on using DobotStudio Pro, please refer to its help document. Most of the functions described in this document can be programmed through both Blockly programming and Script programming.

* Blockly programming is recommended as it is simple and has a low learning threshold.
* Script programming offers greater flexibility and is suitable for users with some programming background.

## 2. Welder Connection

Dobot supports robot system supports four communication modes: Modbus, DeviceNet, I/O analog, and EtherNet/IP. Users can view the supported communication modes on the Welder Configuration page in the plugin and choose the appropriate mode for connection. For details on the operation of the welder, refer to the welder's manual. This document describes general operating procedures only.

### 2.1 Modbus TCP communication

Steps:

1. Configure the welder: Refer to the welder's manual to complete the Modbus

TCP communication settings of the welder.

2. Connect the devices: Use a network cable to connect the welder to the LAN1

interface of the robot controller.

3. Set the IP: Adjust the IP addresses of the welder and the robot controller to be in

the same network segment. For instructions on changing the IP of the robot controller, please refer to the help document of DobotStudio Pro.

### 2.2 DeviceNet communication

#### 2.2.1 Preparation

This solution uses the ENC-313 gateway (purchased from Dobot; please confirm with technical support that the gateway has been flashed with the appropriate welder version before use) as an adapter module, which converts Modbus signals into DeviceNet signals. Consequently, the connection methods for different welders mainly vary based on the configuration of the welder's communication module.

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGGfkMkxYAHRjApVRoE4M%2Fwelding-p011-img02.jpg?alt=media)

Prepare the following items before making the connection:

* Gateway x 1
* Network cable x 1
* I/O cable:

◦ DeviceNet cable for welder x 1 ◦ Two independent IO cables for powering the gateway.

#### 2.2.2 Gateway connection

The overall connection diagram is shown below. Refer to the welder manual to configure the welder's DeviceNet communication. After setting the welder communication module, refer to the following to connect the gateway module.

1. Connect the DeviceNet bus provided by the welder manufacturer to the ENC-313

module, and set the DIP switch for the terminating resistor to ON. Connect the gateway module's GND to the 0V interface of the power supply, and V+ to the 24V interface of the power supply.

![Official manual figure, page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F02dL8cpynTQLdEN09sQ2%2Fwelding-p012-img02.jpg?alt=media)

2. Connect the network interface A or B on the ENC-313 module to the LAN1 interface

on the controller with the network cable.

![Official manual figure, page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5kRg74VxDDX72b9JV6fb%2Fwelding-p013-img02.jpg?alt=media)

![Official manual figure, page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVgiRdZMIeIiXWz74UP7M%2Fwelding-p013-img03.jpg?alt=media)

**NOTICE**

If you are using an older version of the gateway with DIP switches, the following steps are required:

1. Install a 120 terminating resistor on the DeviceNet port, as shown

Ω in the figure below.

2. Set the gateway's DIP switches to operation mode (i.e., 1: OFF, 2:

OFF).

3. Set the IP addresses of the robot arm and computer, keeping them in the same

network segment as the gateway without conflict. For the modification method, please refer to the DobotStudio Pro User Guide. Example:

* Gateway IP: 192.168.5.101 (default)
* Robot arm IP: 192.168.5.1
* Computer IP: 192.168.5.10

4. Restart the welder and controller (no need to restart if the DIP switch has not been

changed). Taking the OTC welder as an example, the connection results are as follows:

![Official manual figure, page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzhG4g4zdD4QQqdblHPSp%2Fwelding-p014-img03.jpg?alt=media)

![Official manual figure, page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSu2SJb6rsrZ0OzgQHcYy%2Fwelding-p014-img04.jpg?alt=media)

Please connect the cables between the welder communication module and the gateway according to the interface definitions displayed on the device.

#### 2.2.3 Connection verification

After hardware connection is complete, perform Welder configuration in the welding plugin, then use the Manual wire feed / retract function to verify that communication is working properly.

### 2.3 Analog communication

#### 2.3.1 Preparation

The figure below shows the I/O signals to be configured in the welding plugin, please plan according to the site requirements first: Controller signal: Required. Touch positioning signal / Other signal / Arc welding template signal: Configure ① as needed. ② ③ ④ For signal definitions, refer to Basic welding signal configuration and Touch positioning signal configuration.

![Official manual figure, page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F01jrWDEdizBFUIqikwyD%2Fwelding-p015-img02.jpg?alt=media)

![Official manual figure, page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNnVQPhqhttNOZrkF1rxT%2Fwelding-p015-img03.jpg?alt=media)

Then, prepare the signal cables as planned.

* Analog signal cables x 3. To improve the accuracy of the analog signal, it is recommended to use shielded or twisted pair cable.
* Digital signal cables, the quantity is determined by the I/O planning.

#### 2.3.2 I/O wiring

Connect the analog signal interface of the controller to the corresponding analog communication interface of the welder.

**NOTE**

For Cloos welder, there is no need to connect analog signals, but it is necessary to connect DO1 to DO8 to the welder to specify the Job No. For detailed wiring instructions, please refer to the following section: Cloos Welder. In addition, you need to connect the digital communication interface. You can configure the digital interface of the controller in the plugin. The wiring method shown below is for reference only.

![Official manual figure, page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMtSOEsiY79RSbbK3qxdL%2Fwelding-p016-img02.png?alt=media)

For the wiring of welder, please refer to the welder manual. Here takes the Aotai AMIG PR series welder as an example. The analog communication interface and pin number of the Aotai AMIG PR series welder are shown in the figure below.

![Official manual figure, page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLkfgpbUbu72tlVxyCc3g%2Fwelding-p017-img02.png?alt=media)

The pin definitions and corresponding controller interfaces are listed in the table below (all digital signals are in NPN type). Pin Definition Controller interface 4 External 24V power supply 5 Voltage reference signal ⑤ 6 Current reference signal ③ 7 Wire feed signal ② 8 Gas detection switch signal ⑦ 9 Arc start signal ⑨ 10 Manual wire retract signal ⑥ 11 Analog signal ground (0V) ⑧ 12/13 Arc start successful signal ① 14/15 Touch positioning successful signal ④Any DI 18/19 Touch positioning enable signal Any DO The connection diagram is as follows (for reference only), and the number on the red line indicates the pin number on the welder.

![Official manual figure, page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8xP3i3bdV8iNgaNCTE3m%2Fwelding-p018-img02.png?alt=media)

![Official manual figure, page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbeMyvt0lqjTUQv9UtXM0%2Fwelding-p019-img02.png?alt=media)

#### 2.3.3 Modifying the IO configuration

AO configuration When using analog communication, ensure that the controller's AO is set to voltage mode. Follow the steps below to verify:

1. Open DobotStudio Pro and connect it to the robot.
2. Click the "Monitor" panel on the top toolbar to enter the "Controller AI/AO" page, and

confirm that AO\_1 and AO\_2 are both set to "Voltage".

3. If AO\_1 or AO\_2 is not set to Voltage", click "Modify" on the right of the "Analog output",

set both AO\_1 and AO\_2 to "Voltage" and click "Confirm modification". DI/DO configuration Since the digital IO of most welders is NPN type, while the digital IO of the robot arm controller is PNP type by default, the following settings need to be made to modify the digital IO type of the controller.

* For DI, refer to the wiring diagram in I/O wiring and connect the COM interface in the column corresponding to the DI connected to the welder to I/O 24V.
* DO: Set the type of DO in DobotStudio Pro as follows.

1. Open DobotStudio Pro and connect it to the robot.
2. Click the "Monitor" panel on the top toolbar to enter the "Controller DI/DO" page.

![Official manual figure, page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4pknAwm2GrTlEL8pxmzR%2Fwelding-p020-img02.png?alt=media)

3. Click "Settings > Advanced settings" to set the DO mode to "NPN", and click

"Save".

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBKw15ikqaZw8f7obQBIz%2Fwelding-p021-img02.jpg?alt=media)

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxrIfbXfeSrPDIHFp9TKd%2Fwelding-p021-img03.jpg?alt=media)

### 2.4 EIP communication

The current version supports EIP communication with only certain welders. For details, refer to Welder configuration. Connection method:

* Connect the welder that supports EtherNet/IP (EIP) communication to the LAN1 port on the robot controller using an Ethernet cable.
* Interface details: The welder's interface uses an aviation connector, while the robot's interface uses an RJ45 connector. Prepare the appropriate network cable for the connection.
* IP settings: Set the robot's IP address within the same subnet as the welder and set the robot's "Bus communication" to "Off".

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7PsCTXZhdbQNQExsslUT%2Fwelding-p022-img02.jpg?alt=media)

## 3. Software Installation and Configuration

### 3.1 Plugin installation

1. Open the software installation package and double-click the welding plugin

installation.exe to enter the installation interface.

2. Click "Start Installation". In the pop-up interface, you can click custom to select the

installation path or "One click installation" to start the installation.

3. After the installation is complete, you will automatically enter the main interface of the

welding plug-in.

**NOTE**

If the intelligent welding assistant is used to assist in point teaching, the intelligent welding assistant needs to be turned on; Please refer to the DOBOT Intelligent Welding Assistant User Guide for specific instructions on how to use this assistant.

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuYpjKeCkM2UM1Epdk4SX%2Fwelding-p023-img03.png?alt=media)

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkwElICLyo7WK3f9awpAT%2Fwelding-p023-img04.png?alt=media)

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FurbBIWG7dNtoUx7EiVkQ%2Fwelding-p023-img05.jpg?alt=media)

### 3.2 Setting the tool coordinate system

Once the welding torch is mounted on the end of robot arm, it is necessary to calibrate the tool coordinate system of the welding torch to ensure accurate welding operations. The tool coordinate system for welding torch is generated using the six-point teaching method (TCP+ZX): After the tool is mounted on the end of the robot arm, adjust the tool's posture so that the welding torch tip is aligned with the same point in space (reference point) from three different directions ( ) to obtain the tool’s position offset. Then, obtain the tool’s posture offset based on three additional points ( ), where aligns with the same point as. ①②③ ④⑤⑥ ④ ①②③ Go to "Settings > Coordinate System > Tool Coordinate System" page, click "Add".

1. Click "Six-point setting" on the "Add tool coordinate system" page.
2. Refer to the software interface diagram, move the robot to the designated point, and

click "Obtain".

![Official manual figure, page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHWJFG1CXs3T0SwfckVu7%2Fwelding-p024-img02.jpg?alt=media)

![Official manual figure, page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBwMJYlrEDf3uEOLUVEZa%2Fwelding-p024-img03.jpg?alt=media)

![Official manual figure, page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNufiDGb45eeolQenLUsP%2Fwelding-p024-img04.png?alt=media)

**NOTE**

Long-press "Run to" to move the robot to the obtained point.

3. Click "Confirm" to return to the tool coordinate system addition page, where the

coordinate system values are updated to the calibrated values.

4. Click "Save", and this coordinate system is added to the tool coordinate system list.

After adding the coordinate system, it is recommended to validate the accuracy of the tool coordinate system using the Fixed-Point Posture Variation Method. Here are the steps: ①. In the "Jog" panel, set the "Tool coordinate system" to the welding torch’s tool coordinate system. ②. Aim the tip of the welding torch at a visible marked point (e.g., the tip of a calibration needle). ③. Change the arm’s posture (RX/RY/RZ) and observe whether the welding torch rotates around the marked point.

![Official manual figure, page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXIKr9uMNOzSlfrk9eaVh%2Fwelding-p025-img02.jpg?alt=media)

If there is a significant deviation between the tip and the marked point when the torch rotates, it indicates a large calibration error. It is recommended to recalibrate the tool coordinate system. If laser positioning/tracking is required, complete the tool coordinate system calibration first. Then ensure that the wire stick-out length remains the same (wire stick-out length refers to the distance from the tip of the welding wire to the end of the contact tip, which means keeping the welding torch tip used during calibration unchanged) before performing Laser Calibration.

![Official manual figure, page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F42o9VeEgPBDrR38gr6pI%2Fwelding-p026-img02.jpg?alt=media)

## 4. Basic Welding (Arc Welding)

### 4.1 Introduction

This chapter introduces how to perform basic arc welding. After calibrating the welding torch's coordinate system and configuring the relevant parameters of the welder, you can realize automatic welding with the robot through Blockly or Script programming, which supports linear, arc, and circle welding. The welding process package also provides arc-welding template blocks, allowing for simple programming with just one block by teaching points and configuring parameters, significantly reducing the difficulty and time involved in programming.

### 4.2 Welder configuration

In DobotStudio Pro, navigate to the "Welding settings" page. After opening the welding plugin, first select the brand of the welder based on the actual device in use, then click "Configuration". Communication mode No. Welder brand Analog I/O DeviceNet Modbus Ethernet/IP Fronius TPS Fronius (Austria) √ Fronius TPSI Fronius (Austria) √ √ Fronius iwave Fronius (Austria) √

![Official manual figure, page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2NnLNGwwrEKAXtEJYZva%2Fwelding-p027-img02.png?alt=media)

Communication mode No. Welder brand Analog I/O DeviceNet Modbus Ethernet/IP Fronius TPS5000CMT Fronius (Austria) √ Kemppi DCM Kemppi (Finland) √ Kemppi RCM Kemppi (Finland) √ 7 EWM (Germany) √ √ √ 8 Cloos (Germany) √ ESAB Aristo 9 500ix/U5000w/5000iw √ √ ESAB (Sweden) ESAB Transming DP/P/H ESAB (Sweden) √ ESAB Aristo dege ESAB (Sweden) √ √ 12 Lorch (Germany) √ 13 SKS (Germany) √ 14 Cebora (Italy) √ 15 GYS (France) √ 16 Telwin (Italy) √ 17 Böhler (Austria) √ Kolarc XM series Kolarc (Turkey) √

Communication mode No. Welder brand Analog I/O DeviceNet Modbus Ethernet/IP Kolarc MX series Kolarc (Turkey) √ Lincoln Digiwave Lincoln (USA) √ Lincoln Powerwave Lincoln (USA) √ √ Miller Auto-continuum Miller (USA) √ √ Miller Auto-Deltaweld Miller (USA) √ √ OTC MIG/MAG/CO2 (Japan) √ √ OTC TIG (Japan) √ √ Panasonic Panasonic (Japan) √ √ √ 27 Megmeet (China) √ √ √ √ Aotai MIG-LST Aotai (China) √ √ √ Aotai MIG-PLUS Aotai (China) √ √ √ 30 Flama (China) √ √ 31 YaoLi √ 312 Other welder √

* The welders listed in the table all support analog communication. If you cannot directly select analog communication under "Communication mode", please choose "Other welder".
* If the brand of welder you are using is not shown here, please select "Other welder"

(only analog communication is supported). Go to the "Welder configuration" page (no welder configuration page for Cloos welder), choose the communication mode according to the one selected when connecting to the welder. The communication modes supported vary by welder brand. For communication modes not currently supported, the corresponding options will not be displayed.

**NOTICE**

When connecting to a Megmeet welder, you need to start the robot first (you can use DobotStudio Pro to connect) and then the welder, so as to ensure proper communication between the robot and the welder.

#### 4.2.1 Modbus

After selecting the communication mode as Modbus, enter the IP of the welder Modbus TCP module and click Connect.

#### 4.2.2 DeviceNet

After selecting the communication method as DeviceNet, enter the IP of the gateway and click Connect.

#### 4.2.3 I/O analog

When selecting I/O analog as the communication mode, you need to set up a match between analog voltage (V) and welder current (A) or between analog voltage (V) and welder voltage (V) (i.e. V-A curve and V-V curve). The setting method is as follows.

![Official manual figure, page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwCw88v4nub660dwinHLW%2Fwelding-p030-img02.png?alt=media)

Setting the V-A curve:

1. Set the initial voltage value:

* Enter 0 in the input box under the Output voltage AO\_1 analog (hereinafter referred to as "position "), and click Confirm. ①
* Record the actual curre ① nt value displayed on the welder.

2. Gradually increase the voltage and observe the current change:

* Gradually increase the voltage value entered in position (e.g., 0.1V each time).
* After each voltage increase, click Confirm and observe ① the actual current value displayed on the welder.
* If the current value does not change, continue increasing the voltage until the current changes.

3. Enter the current value:

Enter the changed current value into the "Welder current" on the right of position.

4. Set the maximum voltage value:

①

* Enter 10 in the input box under the Output voltage AO\_1 analog (hereinafter referred to as "position "), and click Confirm. ②
* Record the actual curre ② nt value displayed on the welder.

5. Gradually decrease the voltage and observe the current change:

* Gradually decrease the voltage value entered in position (e.g., 0.1V each time). ②
* After each voltage decrease, click Confirm and observe the actual current value displayed on the welder.
* If the current value does not change, continue decreasing the voltage until the current changes.

6. Enter the current value and confirm the curve:

Enter the changed current value into the "Welder current" on the right of position to complete the settings of V-A curve. ② Setting the V-V curve:

* Follow the same steps to set the V-V curve.
* The only difference is that the values to be viewed and entered are the actual voltage values displayed on the welder.

![Official manual figure, page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FirCbEKsVQz4r0a1SbaWJ%2Fwelding-p031-img02.jpg?alt=media)

#### 4.2.4 EIP

The current version supports EIP communication with only certain welders. For details, refer to Welder configuration. The configuration parameters for different welders are shown in the table below. Enter the corresponding parameters based on the welder currently connected, and then click "Connect". EIP param Config Output Output Input Input component component component component component Welder brand ID ID Size ID Size EWM (Germany) 151 150 224 100 246 ESAB Aristo 500ix/U5000w/5000iw 197 150 16 100 16 ESAB (Sweden) ESAB Aristo dege 0 150 16 100 16 ESAB (Sweden) Cebora 0 150 24 100 20 Cebora (Italy) Telwin (Italy) 0 150 100 28 20 Böhler (Austria) 197 150 100 28 28 Lincoln Powerwave 5 150 12 100 12 Lincoln (USA) Miller (USA) 128 112 26 100 20

![Official manual figure, page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff2egO5FcbVhjt6wcO5Y6%2Fwelding-p032-img02.jpg?alt=media)

EIP param Config Output Output Input Input component component component component component Welder brand ID ID Size ID Size Panasonic (Japan) 0 150 18 100 16 Megmeet 1 150 37 100 37 Megmeet (China)

### 4.3 Welding parameter configuration

In the left navigation window of the welding plugin, select "Welding parameter" to access the welding parameter configuration page. The parameters vary depending on the specific welder model. Please ensure the parameters displayed match the actually connected welder. You can click "Re-select" at the bottom of the left navigation window to enter the welder brand selection interface and choose a different welder brand.

![Official manual figure, page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6DfrsDqo1seLUPILHeSV%2Fwelding-p033-img02.png?alt=media)

#### 4.3.1 Fronius welder

TPS/TPSI/iwave models Fronius welders support TPS/TPSI/iwave models, and the parameters that need to be configured for each model of welders are the same. Currently, only calling existing parameter files via Job number is supported. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions. TPS5000CMT model Supports InternalParam welding mode and invokes existing parameter files of welders through Job Number (welder process number) and Program Number (welding parameter number). To use the manual spot welding function, you need to check "Manual-spot welding" and set the welding voltage/current and "Duration" of the spot welding. For details on additional functions, see Welding process functions.

![Official manual figure, page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUlSNtIPUkHuhEZxRFIAc%2Fwelding-p034-img02.png?alt=media)

![Official manual figure, page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1AQuSMvFc42eNhwqq571%2Fwelding-p034-img03.png?alt=media)

#### 4.3.2 EWM welder

Currently, it only supports calling the existing parameter files of the welder via "Job No." (welder process index) and "Program No." (welding parameter index). You can select the "Welding method" (Conventional welding/Pulse welding) and "Operation mode" (2-Step/Special 2-Step). For detailed definitions, please refer to the welder's manual. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No.", "Program No.", and "Duration". For details on additional functions, see Welding process functions.

**NOTE**

For some EWM welding machines, the parameters for JOB No. and program No. must be adjusted using the following method. For detailed operating instructions, please refer to the welding machine's manual: If the called program number is empty, enter the JOB No. and program No., then click "Save". At this point, the JOB No. and program No. on the welding machine will be updated to the ones we have set. You can then adjust the parameters within the welding program directly via the welding machine's control panel.

#### 4.3.3 Flama welder

![Official manual figure, page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeyRmD8PnzfN9TavSOFId%2Fwelding-p035-img02.png?alt=media)

![Official manual figure, page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdkZaBp4IZ8yBXibXcMXi%2Fwelding-p035-img03.png?alt=media)

It supports the following welding methods:

* DC synergy
* Single-pulse synergy
* Call Job
* Proximity mode

Among these, “Call Job” uses the “Job No.” to call up pre-existing parameter files of the welder, while “Proximity mode” allows welding parameters to be set through the welder’s display panel. The settable parameters for other modes are listed in the table below. Parameter Description The index of the current welding parameter group, used in Custom param No. programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. Arc end current The current when the welder stops the arc and fills the crater. The current used during the normal welding process (after the Welding current arc starts). Arc start / Arc stop / Welding arc voltage Adjust the arc length within the range of -10 10. – compensation The action time of the arc start current. It starts counting as soon Arc start time as the welder receives the feedback signal that the arc is started successfully. Arc stop time The action time of the arc end current/voltage. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the welding parameters and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.4 Aotai welder

The difference between the two Aotai welder models mainly lies in the different welding methods supported, and the rest of the setting parameters are the same. The Aotai MIG-LST welder supports the following welding methods (setting is not supported when using analog communication):

* Flat
* Pulse program
* Call Job
* Low splash mode
* Flat spot welding
* Low splash spot welding

The Aotai MIG-PLUS welder supports the following welding methods (setting is not supported when using analog communication):

* Flat
* Pulse program
* Call Job
* Big penetration
* Fast pulse

Where, "Call Job" means calling the existing parameter files of the welder via "Job No.". If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For the other welding methods, you need to set the "Welder working mode" and enter specific parameters. Please set the "Welder working mode" (Synergy/Separation) according to the actual working mode of the welder. The parameters to be set in the two modes are slightly different, see the table below for details.

![Official manual figure, page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHjDcBcwerk8HOLUkpHZ3%2Fwelding-p037-img02.png?alt=media)

Parameter Description The index of the current welding parameter group, used in Custom param No. programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. Arc end current The current when the welder stops the arc and fills the crater. The current used during the normal welding process (after the Welding current arc starts). Arc start / Arc stop / Required to be set when the "Working mode" is "Synergy". Welding arc voltage Adjust the arc length within the range of -5–5. compensation Arc start / Arc stop / Required to be set when the "Working mode" is "Separation". Welding voltage The voltage during arc start/arc stop/normal welding process. The action time of the arc start current. It starts counting as Arc start time soon as the welder receives the feedback signal that the arc is started successfully. Arc stop time The action time of the arc end current/voltage. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Arc voltage compensation" (Synergy), "Voltage" (Separation), "Current" and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.5 Megmeet welder

![Official manual figure, page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdqjLZCzbKb1r1Z1k2ta9%2Fwelding-p038-img02.jpg?alt=media)

It supports the following welding methods:

* DC synergy
* Pulse synergy
* Call Job
* Proximity mode
* Separation

Among these, "Call Job" uses the "Job No." to call up pre-existing parameter files of the welder, while “Proximity mode” allows welding parameters to be set through the welder’ s display panel. The adjustable parameters for other modes are listed in the table below. Parameter Description The index of the current welding parameter group, used in Custom param No. programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. Arc end current The current when the welder stops the arc and fills the crater. The current used during the normal welding process (after the Welding current arc starts). Arc start / Arc stop / Required for "DC synergy / Pulse synergy". Adjust the arc Welding arc voltage length within the range of -30 30. compensation – Arc start / Arc stop / Required for "Separation". The voltage during arc start/arc Welding voltage stop/normal welding process. The action time of the arc start current. It starts counting as soon Arc start time as the welder receives the feedback signal that the arc is started successfully. Arc stop time The action time of the arc end current/voltage. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the welding parameters and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.6 Lorch welder

Currently, it only supports calling the existing parameter files of the welder via "Job No.". If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.7 GYS welder

Currently, it only supports calling the existing parameter files of the welder via "Job No.". After connecting the welder, the GYS welder's panel is locked by default. To via Modbus enable adjustments through the welder's panel after connecting it to the robot, you need to set the "Welder parameter panel" switch to "ON" in this interface and save the changes. This will allow you to modify welding parameters directly from the welder's panel. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.8 Lincoln welder

Lincoln welders support the Digiwave and Powerwave series, both of which have identical "Welding parameter" configuration pages, as shown in the figure below:

![Official manual figure, page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS3dkE2qcZMljH4Fs6FnH%2Fwelding-p040-img02.png?alt=media)

![Official manual figure, page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOizlj6nXSVZrC1HIDtzh%2Fwelding-p040-img03.png?alt=media)

Currently, it only supports calling the existing parameter files of the welder via "Job No.". If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.9 OTC welder

MAG/MIG/CO2 It supports the following welding methods:

* DC pulse
* DC
* DC low sputter
* DC wave pulse
* AC pulse
* AC wave pulse
* D-Arc
* MS-MIG
* Call Job

![Official manual figure, page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNb6KqUePl9bdyFJvkAQA%2Fwelding-p041-img02.png?alt=media)

![Official manual figure, page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhmVBdQlcjAtCL18IWXWA%2Fwelding-p041-img03.jpg?alt=media)

Please set the "Welder working mode" (Synergy/Separation) according to the actual working mode of the welder. The parameters to be set in the two modes are slightly different, see the table below for details. Parameter Description The index of the current welding parameter group, used in Custom param No. programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. Arc end current The current when the welder stops the arc and fills the crater. The current used during the normal welding process (after the Welding current arc starts). Range: 20A – 500A. Arc start / Arc stop / Required for Synergy mode. Adjust the arc length within the Welding arc voltage range of -10 – 10, and precision supported to one decimal compensation place. Arc start / Arc stop / Required for "Separation" mode. Adjust the voltage within the Welding voltage range of -10V – 50V. The action time of the arc start current. It starts counting as soon Arc start time as the welder receives the feedback signal that the arc is started successfully. Arc stop time The action time of the arc end current/voltage. The time gas is supplied before arc start, with a range of 0 to 10 Pre-flow time seconds, and precision supported to one decimal place. The time delay for turning off the gas after arc end, with a range Post-flow time of 0 to 10 seconds, and precision supported to one decimal place. Gas Gas for welding, select according to the actual situation The material of the welding wire, select according to the actual Material situation The diameter of the welding wire, select according to the actual Wire diameter situation

Parameter Description When this function is ON, the welder can automatically control the wire feed speed to maintain the welding current. This function is only effective in the following scenarios:

* The welding method is either DC or DC pulse.

Penetration control

* The material is Carbon Steel Solid, Carbon Steel Core,

Stainless Steel Solid, or Stainless Steel Core.

* The welding process (not effective during arc start, arc end, or spot welding). If a water-cooled welding torch is being used on-site, enable this function. This allows you to monitor the water circulation of the Water-cooled torch torch through the welder. When the welder detects that the cooling water is not circulating, it will trigger an E500 alarm. This setting adjusts the softness or hardness of the arc, with a range of -10 to 10 (from soft to hard), without units. Arc control In general, for better welding results, it is recommended to set the arc to hard when the welding current is low, and to soft when the welding current is high. When the "Welding method" is "DC pulse", this parameter can create a fish-scale weld pattern. It achieves the fish-scale effect by adjusting the wire feed speed and pulse frequency. The higher the frequency setting, the denser the fish-scale pattern. Waving frequency Range: 0.5 – 32 Hz. When the frequency exceeds 3Hz, the variation in wire feed speed becomes smaller. When the frequency exceeds 5Hz, the wire feed speed no longer changes, and only the pulse frequency varies. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Arc voltage compensation" (Synergy), "Voltage" (Separation), "Current" and "Duration". For details on additional functions, see Welding process functions.

TIG It supports the following welding methods:

* DC TIG
* AC TIG
* AC-DC TIG
* Call Job

Parameter Description The index of the current welding parameter group, used in Custom param No. programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. The action time of the arc start current. It starts counting as Arc start time soon as the welder receives the feedback signal that the arc is started successfully. Arc end current The current when the welder stops the arc and fills the crater. Arc stop time The action time of the arc end current/voltage. The current used during the normal welding process (after the Welding current arc starts).

![Official manual figure, page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBWZLlKfq84QFOUSl4y5V%2Fwelding-p044-img02.jpg?alt=media)

Parameter Description Pre-flow time The time for pre-gas at arc start Post-flow time The time for post-gas at arc end Adjust the positive and negative width of the square wave output (typically used in TIG AC aluminum welding to remove the oxide layer from aluminum plates). The larger the value, Clean width the wider and shallower the weld pass; while the smaller the value, the narrower and deeper the weld pass. Range: -20 –

20. For more information on this function, refer to the user

manual of OTC welder. If a water-cooled welding torch is being used on-site, enable this function. This allows you to monitor the water circulation Water-cooled torch of the torch through the welder. When the welder detects that the cooling water is not circulating, it will trigger an E500 alarm. Select the type of AC waveform to be used: "Standard", "Soft", or "Hard". Standard: Outputs a rectangular waveform where the peak currents of positive polarity and negative polarity are equal. This is a commonly used waveform type, offering a broad welding application range. Soft: Outputs a sinusoidal waveform where the peak currents AC waveform of positive polarity and negative polarity are equal. It produces a smoother arc, making it suitable for butt welding thin sheets, etc. The welding current setting should be below 200A. Hard: Outputs a rectangular waveform where the peak currents of positive polarity and negative polarity differ. Ideal for fillet welding of thin sheets and the root pass in groove welding. The welding current setting should be below 200A. Wire feed delay The delay time before wire feeding, minimum: 0.1s Set the wire feed time in the intermittent case, e.g. 0.5s for Wire feed time (interval) wire feed and 0.5s for stop. Range: 0 – 50, minimum: 0.1s Set the stop time of wire feed in the intermittent case, e.g. 0.5s Wire feed stop (interval) for wire feed and 0.5s for stop. Range: 0 – 50, minimum: 0.1s Wire feed speed Set the wire feed speed Pulse setting With pulse / No pulse Pulse frequency Set the pulse frequency when there is a pulse

Parameter Description Set the peak current when there is a pulse (the pulse TIG welder operates with two current states: peak current and low Peak current current. The alternating frequency and working period of the two currents can be adjusted respectively) AC frequency Set the AC frequency AC-DC switching Set the switching frequency between alternating current (AC) frequency and direct current (DC) If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Current" and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.10 SKS welder

Currently, it only supports calling the existing parameter files of the welder via "Job No." and "Program No.". If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No.", "Program No.", and "Duration". For details on additional functions, see Welding process functions.

![Official manual figure, page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ1Xfg24PlGzgjvREIMTG%2Fwelding-p046-img02.png?alt=media)

#### 4.3.11 Cloos welder

The Cloos welder uses digital I/O to specify the Job number. The user needs to connect DO1 through DO8 on the robot controller to the corresponding D-IN terminals on the welder side. See the table below for details. Robot DO Welder D-IN DO1 D-IN 5 DO2 D-IN 22 DO3 D-IN 7 DO4 D-IN 8 DO5 D-IN 9 DO6 D-IN 10 DO7 D-IN 11 DO8 D-IN 12 Since DO1 to DO8 are already in use, the digital signals that need to be configured in the Signal configuration cannot be assigned to DO1 – DO8. Once the cable connections are completed, the robot can call the welder's pre-existing parameter files using the Job No. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions

![Official manual figure, page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOQxKrmv15mLQnUj5ga6r%2Fwelding-p047-img02.png?alt=media)

#### 4.3.12 Kemppi welder

When using Kemppi welders with the DCM and RCM modules, the parameters that need to be configured are the same. Currently, it only supports calling the pre-existing parameter files of the welder via "Job No.". The diagram for the DCM module is The diagram for the RCM module is shown shown below: below: If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions.

![Official manual figure, page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMcg3JnKbANSbDHMIaWF5%2Fwelding-p048-img02.jpg?alt=media)

![Official manual figure, page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIl4ADmdSuhy51U887n0R%2Fwelding-p048-img03.jpg?alt=media)

![Official manual figure, page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F48dcVhyQpBGMK2zcOZtP%2Fwelding-p048-img04.png?alt=media)

Online control refers to the ability to modify process parameters while the robot arm is calling the welder parameters via the Job number. Calling the modified parameter via the online control parameter number; In the online control mode, the following parameters can be adjusted: whether to turn on the online control mode, whether to turn on the hot arc start function, whether to turn on the arc end filling function, current, wire feed speed, plate thickness, voltage, fine adjustment, dynamic characteristics, and arc end current.

#### 4.3.13 ESAB welder

The ESAB welder supports Aristo 500ix, U5000w, 5000iw, Transmig DP/P/H, and Aristo Edge models. The parameters to be configured are the same across all models. Currently, only calling existing parameter files via Job number is supported. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.14 Kolarc welder

MX series The Kolarc welder MX series currently only supports calling existing parameter files via Job number. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions.

![Official manual figure, page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQmkarvNrw37KESsplhqm%2Fwelding-p049-img02.png?alt=media)

XM series The Kolarc Welder XM series supports the welding modes including InternaIParam, Smart2Trigger, Call Job, and TwoTriger. Among them, Call Job is to call the existing parameter file of the welder through the Job number, and the InternaIParam mode only sets whether to turn on high-voltage positioning. The settable parameters for other modes are listed in the table below. Parameter Description High voltage positioning Whether to turn on high-voltage positioning. switch The index of the current welding parameter group, used Custom param No. in programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. Arc start voltage Voltage at arc start of the welder The action time of the arc start current. It starts counting Arc start time as soon as the welder receives the feedback signal that the arc is started successfully. The current when the welder stops the arc and fills the Arc end current crater. The voltage when the welder stops the arc and fills the Arc end voltage crater. Arc stop time The action time of the arc end current/voltage. The current used during the normal welding process Welding current (after the arc starts).

![Official manual figure, page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCF70sgQZ52gBiHTYsbGD%2Fwelding-p050-img02.png?alt=media)

Parameter Description The voltage used during the normal welding process Welding voltage (after the arc starts). Inductance Inductance during welding If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Voltage", "Current" and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.15 Miller welder

Auto-continuum models The Miller welder Auto-Continuum model currently only supports calling existing parameter files via Job number. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions. Auto-Deltaweld model

![Official manual figure, page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDIN4nhyfN4Y8OtYSXBAx%2Fwelding-p051-img02.jpg?alt=media)

![Official manual figure, page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3xwXp4DNIAkIykoh6mED%2Fwelding-p051-img03.png?alt=media)

The Miller welder Auto-Deltaweld model supports following welding modes:

* CvMig
* AccuPulse
* HdMig
* Rmd

The setting parameters are shown in the following table. Parameter Description The index of the current welding parameter group, used in Custom param No. programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. The current when the welder stops the arc and fills the Arc end current crater. The current used during the normal welding process (after Welding current the arc starts). Arc start voltage Voltage at arc start of the welder The voltagewhen the welder stops the arc and fills the Arc end voltage crater. The voltageused during the normal welding process (after Welding voltage the arc starts). The action time of the arc start current. It starts counting as Arc start time soon as the welder receives the feedback signal that the arc is started successfully. Arc stop time The action time of the arc end current/voltage. Gas type number Select the type of welding gas. Range: 0 16 – Wire type number Select the type of welding wire. Range: 0 7 – Wire diameter No. Select the diameter of the wire. Range: 0 8 – Pre-flow time Pre-air time before welding Post-flow time Post-flow time after welding Wire retraction distance wire retraction distance after welding after welding

If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Voltage", "Current" and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.16 Panasonic welder

It supports the following welding methods:

* Separation
* Synergy
* Call Job

Where, "Call Job" means calling the existing parameter files of the welder via "Job No.". The configurable parameters for other modes are listed in the table below. Parameter Description The index of the current welding parameter group, used Custom param No. in programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. The current when the welder stops the arc and fills the Arc end current crater. The current used during the normal welding process Welding current (after the arc starts). Required to be set when the "Welding method" is Arc start / Arc stop / Welding "Synergy". Adjust the arc length within the range of -30 arc voltage compensation – 30.

![Official manual figure, page 53](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrOiuqGhSmaE5irSzHVfn%2Fwelding-p053-img02.jpg?alt=media)

Parameter Description Required to be set when the "Welding method" is Arc start / Arc stop / Welding "Separation". The voltage during arc start/arc stop/normal voltage welding process. The action time of the arc start current. It starts counting Arc start time as soon as the welder receives the feedback signal that the arc is started successfully. Arc stop time The action time of the arc end current / voltage. Required to be set when the "Welding method" is Program No. "Synergy" or "Separation". It refers to the welding parameter index that will be called. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Arc voltage compensation" (Synergy), "Voltage" (Separation), "Current" and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.17 Cebora welder

The Cebora welder currently only supports calling existing parameter files via Job number. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions.

![Official manual figure, page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fg7dlpSgyOtOr6bR6hYZj%2Fwelding-p054-img02.jpg?alt=media)

#### 4.3.18 YaoLi welder

The YaoLi welder supports the following welding methods:

* DC synergy
* Pulse synergy
* Call Job
* Proximity mode
* Separation

Among these, "Call Job" uses the "Job No." to call up pre-existing parameter files of the welder, while “Proximity mode” allows welding parameters to be set through the welder’ s display panel. The adjustable parameters for other modes are listed in the table below. Parameter Description The index of the current welding parameter group, used in Custom param No. programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. Arc end current The current when the welder stops the arc and fills the crater. The current used during the normal welding process (after Welding current the arc starts). Arc start / Arc stop / Required for "DC synergy / Pulse synergy". Adjust the arc Welding arc voltage length within the range of -30 30. compensation – Arc start / Arc stop / Required for "Separation". The voltage during arc start/arc Welding voltage stop/normal welding process.

![Official manual figure, page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOjfgUJeZ8qRBYNtSo1Sf%2Fwelding-p055-img02.png?alt=media)

Parameter Description The action time of the arc start current. It starts counting as Arc start time soon as the welder receives the feedback signal that the arc is started successfully. Arc stop time The action time of the arc end current/voltage. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the welding parameters and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.19 Telwin welder

The Telwin welder currently only supports calling the existing parameter files of the welder through the Job number. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.20 Böhler welder

The Telwin welder currently only supports calling the existing parameter files of the welder through the Job number. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Job No." and "Duration". For details on additional functions, see Welding process functions.

#### 4.3.21 Other welders (I/O analog)

Other welders only support I/O analog communication. Parameter Description The index of the current welding parameter group, used in Custom param No. programming to reference the corresponding parameter group. The alias of the current welding parameter group. It is Parameter alias recommended to set it to a name that is easy to remember. Arc start current The current when the welder starts the arc. Arc end current The current when the welder stops the arc and fills the crater. The current used during the normal welding process (after the Welding current arc starts). Arc start / Arc stop / The voltage during arc start/arc stop/normal welding process. Welding voltage The action time of the arc start current. It starts counting as Arc start time soon as the welder receives the feedback signal that the arc is started successfully. Arc stop time The action time of the arc end current/voltage. If you need to use the manual-spot welding function, check the "Manual-spot welding" option, set the "Voltage", "Current" and "Duration". For details on additional functions, see Welding process functions.

![Official manual figure, page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdCWpYzQXWQt1r9WZnD4e%2Fwelding-p057-img02.png?alt=media)

#### 4.3.22 Welding process functions

Arc retry When this function is enabled, in case of arc failure due to insulation material such as oil stains or rust on the surface of the welding base metal, the robot will automatically retry the arc according to the set parameters. The process is as follows: (Take the second successful arc retry as an example)

1. The robot arm checks whether the remaining “Number of retries” is 0 (the "retry

count" ranges from 0 to 9, with a default of 1).

* If the "Number of retries" is 0, the system will report an error and stop the project.
* If the "Number of retries" is not 0, proceed to the next step.

2. The welder retracts the wire according to the “Wire retract time” setting (range: 0–

5000 ms; default: 1000 ms).

3. The robot calculates whether the accumulated movement exceeds the length of the

weld seam after it advances a specified distance along the seam from the current position ("Re-arc movement", range: 0mm – 99mm, default 5mm).

* If the accumulated movement distance exceeds the length of the weld seam, the system will report an error and stop the project.
* If the accumulated movement distance does not exceed the length of the weld seam, proceed to the next step.

4. The robot advances the specified distance along the weld seam, and then attempts to

retry the arc again.

* If arc start fails, the remaining “Number of retries” is decreased by 1, and the process returns to step 1.
* If arc start succeeds, proceed to the next step.

![Official manual figure, page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3sEPkVvZ2QRzDdLzJt7Z%2Fwelding-p058-img02.png?alt=media)

5. After a successful arc start, the robot arm returns to the initial arc start point and begins

welding. Arc restart When this function is enabled, if an arc break occurs abnormally during welding (e.g., due to wire or gas depletion, or foreign matter on the workpiece surface), the process enters a paused state and waits for the user to manually address the cause of the arc break (e.g., replenish wire or gas, clean the workpiece surface). While the project is paused, the user can manually jog or drag the robot to a position convenient for handling the problem. After the user has manually addressed the issue and resumes the process, the robot will automatically return to the specified return point via linear motion. Ensure that the linear motion does not cause a collision with the workpiece. (The point when the operation is paused is retracted along the weld seam by the "overlap distance" to obtain a new point. The "Overlap distance" ranges from 0 to 99 mm, with a default of 5 mm.) The arc restarts again; after successful arc start, welding continues along the trajectory direction. If arc restart fails, it will try to start the arc again based on the "Number of retries" (range: 0 – 9, default 1). If all retry attempts are exhausted without successfully restarting the arc, an error is reported and the script is stopped. Wire stick removal

**NOTE**

This function is only applicable to Aotai welders operating in DeviceNet and Modbus communication modes and utilizing welding methods other than “Call Job”.

![Official manual figure, page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYqRL6xzQXT6V6FkRE4L9%2Fwelding-p059-img02.png?alt=media)

![Official manual figure, page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZr8wGE1bUEm3LriYbgJh%2Fwelding-p059-img03.png?alt=media)

When this function is enabled, if the wire sticks to the base material (weld bead) during arc end, the robot commands the welder to output a pulse current to forcibly burn through the wire and release the sticking. You can set "Voltage" (or "Arc voltage compensation"), "Current", and "Duration" for the pulse current.

#### 4.3.23 Welding parameter library

The welding parameter library is designed to display the custom parameter sets saved by the user. Within this page, users can view parameter indexes and key parameters, as well as edit the alias, plate thickness, and material type for each parameter set. This helps users quickly locate the desired parameter set. After configuring the welding parameters on the "Welding parameter" page and clicking the "Save" button, a "Preview" button will appear. Clicking "Preview" allows to access the welding parameter library. If the welder only supports the "Call Job" function, the welding parameter library feature will not be available.

### 4.4 Signal configuration

Select "Signal Configuration" in the left navigation window of the welding plug-in to enter the signal configuration page.

![Official manual figure, page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fsrduu77wj2GsrMbepC5i%2Fwelding-p060-img02.png?alt=media)

![Official manual figure, page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlBPDu5ciU0xAg7SujVe7%2Fwelding-p060-img03.jpg?alt=media)

Other signals

* The anti-collision detection signal can be configured as an interface to connect the anti-collision detection signal cable of the welding torch, which is used to prevent the torch from colliding with the workpiece or other objects.
* The Teach point signal is used to save the current robot arm pose as a new point by triggering a specified DI while the project is open, improving the efficiency of point teaching. Arc-welding template signal
* This signal is used to quickly save points in the block. When the

“Welding point” page of the block is open, the corresponding signal is triggered to quickly save the point. See Block description for details. When the communication mode is “I/O analog”, the controller signal and touch positioning signal must also be configured.

![Official manual figure, page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRogMLyD68mHpUIctkBUA%2Fwelding-p061-img02.jpg?alt=media)

![Official manual figure, page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgQcJC4VhPYOrKRvrbCq0%2Fwelding-p061-img04.png?alt=media)

Controller signal  Arc start signal: Used for the robot to notify the welder to start the arc.  Arc-start detection signal: Used for the welder to feed back the successful arc start signal to the robot. The remaining signals are used for Manual debugging:  ◦ Wire feed signal: Control the welder to feed the wire. ◦ Wire retract signal: Control the welder to retract the wire. ◦ Gas detection switch signal: Control the welder to open the gas valve. For touch positioning signal, please refer to the Signal configuration instructions of the touch positioning function. Please configure according to the actual wiring between the controller and the welder. If you want to trigger the robot drag function using an external signal, click "Monitor" on the top toolbar to enter the "Controller DI/DO" page. Then click "Settings > IO settings", set the corresponding DI function (Enter drag/Exit drag) according to the actual wiring and click "Save". The figure below is only an example for reference.

![Official manual figure, page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAzZnOnR0ixcZuI4m1Pe7%2Fwelding-p062-img02.jpg?alt=media)

![Official manual figure, page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzQix2aIDB5C6PGTtTIoW%2Fwelding-p063-img02.jpg?alt=media)

### 4.5 Welding shortcut bar

On the toolbar icon at the top of the software interface, click to open the welding shortcut bar. When the welder is not connected, the panel will appear as follows: When the welder is connected, the panel will appear as follows:

1. Welding Parameter No./Job No.: Displays the custom parameter number or Job

number (and program number) currently in effect.

2. Virtual welding: To prevent the welding defects caused by problems such as point

deviation during actual welding, you can perform virtual welding before formal welding to verify the accuracy of the teaching points. When "Virtual welding" is selected: No welder: No need to connect to the welder. During the running process, none  of the functions related to the welder will not take effect, the virtual welding is mainly used to confirm the robot trajectory. Welder connected: Need to connect to the welder. During the running process,  the welder will not arc, but all other actions will be identical to actual welding (welding parameters will be sent to the welder).

![Official manual figure, page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHOleJWeAqFigsC2JIu3q%2Fwelding-p064-img03.jpg?alt=media)

![Official manual figure, page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVH7yhqRKj8GdgX54GbhZ%2Fwelding-p064-img04.jpg?alt=media)

3. Welding status: Display the current welding status, including the following states:

◦ Standby: Welding has not started or has been completed. ◦ Welding: Welding is currently in progress. ◦ Welding error: An error occurred during welding (e.g., alarm, emergency stop), and the error needs to be resolved.

4. Welding time: Display the total runtime of the project after the welding plugin has

been installed. Clicking while the project is stopped will reset the time to zero.

5. Welding current: Display the current welding current.

Welding voltage: Display the current welding voltage.

6. Wire stick status: Display the current wire sticking status.
7. Wire feed status: Display the current wire feed speed.

 For OTC welder, this value can be manually adjusted and represents the set manual wire feed speed.  For other welders, it displays the real-time wire feed speed during the welding process.

8. Manual wire retract: Press this button to retract the wire when fine-tuning the wire

length. Do not retract too much to avoid loose wire. Wire feed: Click or long press the button according to the wire length when you need to install or replace the welding wire. Gas detection switch: Long press the button to open the gas valve, release it to close the gas valve.

9. Manual-spot welding: Before formal welding, if you need to fix some workpieces by

spot welding, you can select Manual-spot welding and set the relevant parameters in Welding Parameter to use this function.

**NOTICE**

Spot welding function will be triggered immediately after the button is pressed, please pay attention to safety when using it.

### 4.6 Welding assistant

With a force control sensor installed and welding assistant enabled, when the robot is enabled and stationary, pressing Fast Drag or Slow Drag on the Intelligent Welding Assistant immediately enters force-control dragging mode. Click the icon in the top navigation bar of the software interface to open the force- control drag panel, where you can view real-time changes or switch force-control dragging modes.

* Start dragging: The status of the "Fast Drag" and "Slow Drag" buttons on the intelligent welding assistant is synchronously displayed. Press the "Fast Drag" or "Slow Drag" button to automatically activate the switch; release the "Fast Drag" or "Slow Drag" button to automatically deactivate the switch.

**NOTICE**

* Force-control dragging cannot be enabled if the sensor is not calibrated or if the calibration fails.
* Force-control dragging cannot be performed when the sensor is offline or in an error status.
* When force-control dragging is enabled, the Jog panel will be disabled.
* Be careful when using the force-control dragging function. If the sensor calibration result is incorrect, enabling the force-control dragging function might result in the robot moving on its own or the dragging becoming uncontrollable.
* When dragging, it is recommended that the holding point be about 200mm from the center of the six-axis force sensor. The farther the distance, the more obvious the leverage effect on the posture, and jitter may occur.
* During dragging, if you approach the joint limits or the boundaries of the safety wall/safety area, the dragging resistance will significantly increase. Then, you should change the dragging direction to avoid triggering an alarm.
* Coordinate system: Set the reference coordinate system for force-control dragging, with the welding torch's tool coordinate system used by default. If the reference coordinate system is a user coordinate system, select the user coordinate system index here.

![Official manual figure, page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMhjFbVyjPLe3wEQBy7C3%2Fwelding-p066-img02.png?alt=media)

* Drag mode:

Drag mode Description Long-press the "Quick Drag" button on the intelligent welding assistant to enter joint dragging mode under Force-controlled joints force control. In this mode, all axis directions can be freely dragged. Long-press the "Slow Drag" button on the intelligent welding assistant to freely drag the tool along any axis. All directions The center point of posture rotation is the flange center point. Only translate within space along the axes of the Translation reference coordinate system. Equivalent to enabling X, Y and Z directions in custom mode. Only translate in the direction of the XY plane of the XY plane reference coordinate system. Equivalent to enabling X and Y directions in custom mode. Only rotate within space. Equivalent to enabling RX, RY and RZ directions in custom mode. The center point of Posture rotation is the origin of the current tool coordinate system. Restrict movement in one or several directions. When all directions are enabled, it differs from All directions Custom mode as the center point of posture rotation is the origin of the current tool coordinate system.

**NOTE**

To set the drag mode to "Translation, XY Plane, Posture, or Custom", first select the desired drag mode on the force control drag panel, and manually toggle the "Start dragging" to ON. Then, simply drag the robot's end effector directly (no need to use the "Fast Drag" or "Slow Drag" buttons on the intelligent welding assistant).

* Drag speed: Set the speed for force-control dragging. The higher the speed, the lighter the drag sensation.

**NOTE**

The maximum speed for force-control dragging in X/Y/Z directions is 0.3 m/s, and in RX/RY/RZ directions is 1.5 rad/s. When the maximum speed is reached, the drag sensation becomes heavier to prevent over-speeding.

* Force control curve: You can view the force control curve chart.

Real-time switch: Turning on the real-time switch automatically obtains the current controller time and updates the curve in real-time. When turned off, the updates pause, allowing you to check the curve. Direction switch: Tick the direction (Fx, Fy, Fz, Mx, My, Mz) to display the corresponding force control curve for that direction. By default, all curves are displayed.

**NOTE**

For other force sensor configurations, such as setting the maximum allowable force/torque values, I/O configuration, impedance settings, and viewing real- time force curves, please refer to the user guide for the corresponding force control plugin.

### 4.7 Basic welding programming

This section introduces the blocks/commands related to basic arc welding and provides corresponding DEMO.

* Please refer to the Block Description and Block DEMO in this chapter when using blockly programming.
* When using script programming, refer to Script Command Description and Script

DEMO in Appendix A.1.

![Official manual figure, page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFSjQg5HaJx7qvr3zhEzd%2Fwelding-p068-img02.jpg?alt=media)

#### 4.7.1 Quick point-saving

Welding programming often requires multiple points. You can quickly add teaching points using the following point saving methods to improve programming efficiency. Method 1 When using the arc welding template block, you can save points by triggering the arc- welding template signal. For details, refer to the Blockly description below. Method 2 While the project is open, triggering the teach point signal will save the robot's current posture as a new point. For more details, see the Signal configuration section. Method 3 When using the motion block, click "Add current point" in the dropdown menu of the point selection box to save the robot's current posture as a new point and automatically select it. This eliminates the need to switch back and forth between the programming page and the points page. Method 4 After installing the Intelligent Welding Assistant on DOBOT CR5A / 10A / 20A / 6AL and CR5V / 10V / 20V series robot arms, points can be quickly saved using the Fast Programming interface. For details, refer to Fast Programming.

#### 4.7.2 Blockly description

Welding motion block 1. Description: Control the robot to move from the current position to the target point. Drag the block into the programming area and click to open the motion block configuration page. For detailed information about this block, refer to the DobotStudio Pro User Guide. 2. Description: Control the robot to perform a full-circle interpolation motion and return to the current position after completing the specified number of rotations. The coordinates of the current position must not lie on the straight line determined by the intermediate point and the end point. Drag the block into the programming area and click to open the motion block configuration page. For detailed information about this block, refer to the DobotStudio Pro User Guide.

![Official manual figure, page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq4NuGRyZt8yX1Q0vZUWh%2Fwelding-p069-img02.jpg?alt=media)

3. Description: Set the robot's motion speed during the welding process (from arc start to arc end). This speed is an absolute value and is not affected by the global speed ratio of the robot. Parameter: The motion speed of the robot during welding. The unit can be selected from three options: mm/s, mm/min, and cm/min. Arc welding blocks 1. Description: Set the welding solution using templates. Drag the block into the programming area and click to open the configuration page. Parameter configuration: The parameters to be configured vary depending on the welder model. The figure below takes the Aotai welder as an example.

* Welding speed: Set the running speed during the welding process, which is an absolute value and is not affected by the global speed ratio of the robot arm.
* Welding Method: Only EWM, OTC, Panasonic, Megmeet, Aotai, Flama, and YaoLi welders require a welding method selection. For other welders, this selection is not required. Refer to Welding parameters for details.
* Welding parameter No.: When setting welding parameters in non-Job mode, select a predefined custom parameter number.
* Job No.: When using Job mode, select the Job Number of the welder (welder process number).
* Online control parameter No.: This must be set for Kemppi welders.
* Program No.: Fronius (TPS5000CMT), EWM, SKS welders need to set program number (welding parameter number) in addition to Job number.

![Official manual figure, page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZuhZFiabpLHbIWxjsCjb%2Fwelding-p070-img04.png?alt=media)

* Weaving parameter No.: Check this option and set the parameter index for the robot arm to incorporate weaving motion during the welding process based on the configured parameter. See Weaving Process for details.

**NOTICE**

* If the "Parameter configuration" page is incomplete, entry into the

"Welding point" page is not allowed.

* Changing the "Welding method" will uncheck previously selected welding parameters in the "Welding point" page. Welding point Enter the "Welding point" page and click "Point description" to view illustrated explanations for various arc-welding template points.

![Official manual figure, page 71](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ9amKSI4X5o1Lp1OkKw1%2Fwelding-p071-img02.png?alt=media)

![Official manual figure, page 71](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F78M1SKEyOEuCBnfNySGE%2Fwelding-p071-img03.jpg?alt=media)

All points can be selected from the point list of the current project or set as the current position of the robot arm. Long-press "Run to" to control the robot arm to move to the currently set point. An alias can be set for the robot's current point, which will be displayed in the point list on the left. Points in the project list cannot have aliases set again.

* Approach point: A starting safety point before welding begins, which is recommended to be set at a position above the arc start point. If an "approach point signal" is configured in the Signal configuration, the software automatically acquires the current point of the robot arm as the approach point when the signal is triggered. "Advanced settings" allows configuring the robot arm's Speed/Acceleration/CP ratio when moving to this point. If unchecked, the robot arm will use the global settings. For details on motion-related advanced parameters, refer to the general description in

## Appendix C of the DobotStudio Pro help document.

* Arc start point: The point at which the welder starts the arc and begins to weld.

If the "Arc-start point signal" is configured in Signal configuration, triggering this signal will automatically record the robot arm's current position as the "Arc start point".

![Official manual figure, page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbK6jUA3aiBkWPQOr7l3L%2Fwelding-p072-img02.jpg?alt=media)

![Official manual figure, page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ftr6zsgjv1nyYRtVQQ3xj%2Fwelding-p072-img03.jpg?alt=media)

* Intermediate point: A path point during the welding process. Multiple intermediate points can be set. Click "+ Intermediate point" to add an intermediate point, or click the icon on the right of an intermediate point to delete it. After adding an intermediate point, you need to select the motion mode for the intermediate point. a. Line motion: Only one point needs to be set for this motion mode. If the "Intermediate point-line signal" is configured in Signal configuration, triggering the signal will automatically add a linear Intermediate point and record the robot arm's current position. b. Arc motion: Two points must be set for this motion mode. If the "Intermediate point-line signal" is configured in Signal configuration, triggering this signal for the first time will automatically add an arc Intermediate point and record the robot arm's current position as P1. Triggering again will record the current position as arc P2.

![Official manual figure, page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUKXqHqsRFxgtKbscUPRQ%2Fwelding-p073-img03.jpg?alt=media)

![Official manual figure, page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyLnn3a2YUPsaP5tKQdje%2Fwelding-p073-img04.jpg?alt=media)

**NOTE**

If the "Intermediate point-line signal" is triggered before triggering the "Intermediate point-arc signal" for the second time, the current through point will be overwritten as the linear through point, and a new intermediate point will be created after the "Intermediate point-arc signal" is triggered again. Triggering the signal of the other DI point will not affect the through point, and the through point will continue to acquire the arc P2 after the "Intermediate point-arc signal" is triggered again. Advanced settings  Transition radius: It is recommended to select it and set it to a value within the range of 1 mm to 5 mm, which can make the motion smoother.  Welding current/Welding voltage: Modify the current or voltage during the welding process after moving to the Intermediate point. It is only effective for the welding method in non-Job mode. If unselected, plugin-configured parameters will be used.  Job No./Program No.: Modify the Job No. or Program No., effective only for the welding method in Job mode.  Welding speed: Modify the welding speed during the welding process after moving to the Intermediate point. If unselected, use the values set in the "Parameter configuration" page of the block will be used.

![Official manual figure, page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfnJvY8IWfokU6mnmh8kc%2Fwelding-p074-img02.jpg?alt=media)

![Official manual figure, page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeIv4tDJWsNRJrtJa72eg%2Fwelding-p074-img03.png?alt=media)

 Weaving parameter No.: Modify the weaving parameter during the welding process after moving to the Intermediate point.

* Arc end point: The point at which the welder ends the arc and completes the welding process. If the "Arc-end point signal" is configured in Signal configuration, triggering this signal will automatically record the robot arm's current position as the "Arc end point". Advanced settings for the arc end point are displayed only for welding methods that use Job mode (wait time is in milliseconds).
* Departure point: The end safety point after the welding is completed, more than one can be set. Due to residual heat in the welding torch after welding, it is recommended to set this to a hanging position. Click "+ Departure point" to add a departure point, or click the icon on the right of a departure point to delete it. If the "Departure point signal" is configured in Signal configuration, triggering this signal will automatically record the robot arm's current position as the "Departure point". "Advanced settings" allows configuring the robot arm's Speed/Acceleration/CP ratio when moving to this point. If unchecked, the robot arm will use the global settings.

![Official manual figure, page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlgWue697VrXGz8YVUeaF%2Fwelding-p075-img02.jpg?alt=media)

![Official manual figure, page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0uKmQMBXWUbyBE6TUWkz%2Fwelding-p075-img04.jpg?alt=media)

2. Description: Set the welder working mode. Parameter: Working mode of the welder, with different options depending on the welder model.

* For EWM welder, this block can be used to set a combination of the welding method and operation mode.
* OTC / Panasonic / Megmeet / Aotai / Flama / YaoLi welders can use this block to set welding method.
* For other welders, this block is not required.

If the block is not called, the welder working mode set in the plugin will be used by default. 3. Description: When setting welding parameters using Job mode, modify the Job number to be called. Parameter: The Job No. (welder process index) configured on the welder. If the block is not called, the Job No. set in the plugin will be used by default. 4. Description: This block is required for EWM/SKS/Panasonic welders only. You need to modify the called Program number. Parameter: The Program number (welding parameter index) configured on the welder. If the block is not called, the Program No. set in the plugin will be used by default. 5. Description: Modify the called arc start parameter No. when setting the welding parameters in non-Job mode. Parameter: The custom parameter number configured in welding parameters page. If the block is not called, the Custom parameter number set in the plugin will be used by default. 6. Description: Notify the welder to start the arc.

7. Description: Notify the welder to end the arc. 8. Description: When setting the welding parameters, you can use this in non-Job mode block to modify the current and voltage (or Arc voltage compensation) values for subsequent welding. Parameter: 1) Current: The current value for subsequent welding. 2) Voltage: The voltage value (Separation mode) or Arc voltage compensation value (Synergy mode) for the subsequent welding process. If the block is not called, the welding parameter set in the plugin will be used by default. 9. Description: Control the welder to perform actions such as wire feed, wire retract, or gas feed. Parameter: 1) Select the action to be performed: wire feed / wire retract / gas feed. 2) Set the duration.

#### 4.7.3 Block DEMO

You can create a project by using arc welding templates or calling motion commands. This DEMO uses welding an arc as an example. Please create a project first, and teach the following points on the point list page (if you use an arc welding template, you can also teach it directly in the template; it is recommended to use an intelligent welding assistant to cooperate with the Fast programming page to quickly teach points):

* P1: Approach point, the safety point before starting welding, which is recommended to be set at a position above the arc start point.
* P2: Arc start point, the point at which welding begins.
* P3: The first arc intermediate point. Together with P2 and P4, it defines the shape of an arc.
* P4: The second arc intermediate point (also the arc end point). This is the point where welding ends.
* P5: Departure point, the end safety point after the welding is completed. Due to residual heat in the welding torch after welding, it is recommended to set this to a hanging position.

Using arc welding template When using the Arc welding template block, you need to set the welding points and parameters. Click to enter the Parameter configuration page, and refer to Welding Plugin Block to configure the welding parameters. Enter the Welding point page, refer to the above point description and Welding Plugin Block to configure 5 welding points and parameters.

* Set the Approach point to P1.
* Set the Arc start point to P2.
* Add an intermediate point (arc motion) and set it as P3 and P4.
* The arc end point is P4 (i.e., the second arc intermediate point).
* Set the departure point to P5.

Calling motion command When the arc welding template is not used, you need to control the robot motion by programming (calling motion commands). The welding parameters used in the DEMO are the parameters that are finally saved on the Welding parameter configuration page.

![Official manual figure, page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuwrQIiMfabXCLq5aDNbN%2Fwelding-p078-img02.jpg?alt=media)

![Official manual figure, page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3fddcFeCa54MtIbArCqU%2Fwelding-p078-img04.jpg?alt=media)

![Official manual figure, page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7MEqP1s0MQzvkmeTzhEz%2Fwelding-p079-img02.png?alt=media)

## 5. Basic Welding (Laser Welding)

### 5.1 Introduction

This chapter introduces how to perform basic laser welding. After calibrating the welding torch's coordinate system and configuring the relevant parameters of the welder, you can realize automatic welding with the robot through Blockly or Script programming, which supports linear, arc, and circle welding. The welding process package also provides laser-welding template blocks, allowing for simple programming with just one block by teaching points and configuring parameters, significantly reducing the difficulty and time involved in programming.

### 5.2 Welder configuration

Open the plugin, select "Laser welding", and click "Configuration". Laser welding only supports "I/O analog" communication. You need to set up a match between the controller's analog output voltage and the welder's power (i.e., the V-W curve). The setting method is as follows

![Official manual figure, page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq7KFGBU9ug9zQ0bJE9qn%2Fwelding-p080-img02.png?alt=media)

![Official manual figure, page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjePWghiJKi069je3yd3I%2Fwelding-p080-img03.png?alt=media)

1. Set the initial voltage value:

* Enter 0 in the input box under the Output voltage AO\_1 analog (hereinafter referred to as "position "), and click Confirm. ①
* Record the actual powe ① r value displayed on the welder.

2. Gradually increase the voltage and observe the power change:

* Gradually increase the voltage value entered in position (e.g., 0.1V each time). ①
* After each voltage increase, click "Confirm" and observe the actual power value displayed on the welder.
* If the power value does not change, continue increasing the voltage until the power changes.

3. Enter the power value:

Enter the changed power value into the "Welder power" on the right of position.

4. Set the maximum voltage value:

①

* Enter 10 in the input box under the Output voltage AO\_1 analog

(hereinafter referred to as "position "), and click Confirm. ②

* Record the actual power value displ ② ayed on the welder.

5. Gradually decrease the voltage and observe the power change:

* Gradually decrease the voltage value entered in position (e.g., 0.1V each time). ②
* After each voltage decrease, click "Confirm" and observe the actual power value displayed on the welder.
* If the power value does not change, continue decreasing the voltage until the power changes.

6. Input the power value and determine the V-W curve:

Fill in the changed power value in the "Power Corresponding to Welder" on the right side of position to determine the V-W curve. ②

### 5.3 Welding parameter configuration

![Official manual figure, page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3X3TmbdCaPBl31hoBv2k%2Fwelding-p081-img02.png?alt=media)

Parameter Description Custom param No. The index of the current welding parameter group, used in programming to reference the corresponding parameter group. Parameter alias The alias of the current welding parameter group. It is recommended to set it to a name that is easy to remember. Arc start power The power when the welder starts the arc. Welding power The power during the normal welding process after a successful arc start. Arc end power The power when the welder ends the arc and fills the crater Arc start time The duration for which the arc start power is applied. It starts counting as soon as the welder receives the feedback signal that the arc is started successfully. Arc stop time The action time of arc end power

### 5.4 Signal configuration

![Official manual figure, page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fsw7hbmIiu9bDH8y04FpI%2Fwelding-p082-img02.png?alt=media)

Controller signal

* Arc start signal: Used for the robot to notify the welder to start the arc.
* The remaining signals are used for Manual debugging:

 Wire feed signal: Control the welder to feed the wire.  Wire retract signal: Control the welder to retract the wire.  Gas detection switch signal: Control the welder to open the gas valve. Please configure according to the actual wiring between the controller and the welder. Other signals

* The Anti-collision detection signal can be configured as an interface to connect the anti-collision detection signal cable of the welding torch, which is used to prevent the torch from colliding with the workpiece or other objects.
* The Teach point signal is used to save the current robot arm pose as a new point by triggering a specified DI while the project is open, improving the efficiency of point teaching. Laser-welding template signal
* This signal is used to quickly save points in the block. When the

"Welding point" page of the "Laser welding template" block is open, the corresponding signal is triggered to quickly save the point. See Basic welding block description for details. If you want to trigger the robot drag function using an external signal, click "Monitor" on the top toolbar to enter the "Controller DI/DO" page.

![Official manual figure, page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fdu45mgQCLKZkJUVFh08Q%2Fwelding-p083-img03.jpg?alt=media)

Then click "Settings > IO settings", set the corresponding DI function (Enter drag/Exit drag) according to the actual wiring and click "Save". The figure below is only an example for reference.

### 5.5 Manual debugging

Click the icon in the top toolbar of the welding plugin to open the debugging panel. ① Welding param No.: Display the active custom parameter index. ② Virtual welding: To prevent the welding defects caused by problems such as point deviation during actual welding, you can perform virtual welding before formal welding to verify the accuracy of the teaching points. When "Virtual welding" is selected: No welder: No need to connect to the welder. During the running process, none  of the functions related to the welder will not take effect, the virtual welding is mainly used to confirm the robot trajectory.

![Official manual figure, page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6h8Csg21aTUiXXLr7kX3%2Fwelding-p084-img02.jpg?alt=media)

![Official manual figure, page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyGh8fXfV2e2EGDm1LHxr%2Fwelding-p084-img04.jpg?alt=media)

Welder connected: Need to connect to the welder. During the running process,  the welder will not arc, but all other actions will be identical to actual welding (welding parameters will be sent to the welder). ③ Welding status: Display the current welding status, including the following states: Standby: Welding has not started or has been completed.  Welding: Welding is currently in progress.  Welding error: An error occurred during welding (e.g., alarm, emergency stop),  and the error needs to be resolved. ④ Welding time: Display the total runtime of the project after the welding plugin has been installed. Clicking while the project is stopped will reset the time to zero. ⑤ Manual wire retract: Press this button to retract the wire when fine-tuning the wire length. Do not retract too much to avoid loose wire. Wire feed: Click or long press the button according to the wire length when you need to install or replace the welding wire. Gas detection switch: Long press the button to open the gas valve, release it to close the gas valve.

### 5.6 Basic welding programming

This section introduces the blocks/commands related to basic laser welding and provides corresponding DEMO.

* Please refer to the Blockly description and Block DEMO in this chapter when using blockly programming.
* When using script programming, refer to Script command description and Script

DEMO in Appendix A.2.

#### 5.6.1 Quick point-saving

Welding programming often requires multiple points. You can quickly add teaching points using the following point saving methods to improve programming efficiency. Method 1 When using the laser welding template block, you can save points by triggering the laser- welding template signal. For details, refer to the Blockly description below. Method 2 While the project is open, triggering the teach point saving signal will save the robot's current posture as a new point. For more details, see the Signal configuration section. Method 3 When using the motion block, click "Add current point" in the dropdown menu of the point selection box to save the robot's current posture as a new point and automatically select it. This eliminates the need to switch back and forth between the programming page and the points page.

Method 4 After installing the Intelligent Welding Assistant on Dobot CR5A / 10A / 20A / 6AL and CR5V / 10V / 20V series robot arms, points can be quickly saved on the Fast Programming interface. For details, refer to Fast Programming.

#### 5.6.2 Blockly description

Welding motion block The welding motion block is a universal module. For detailed instructions on its usage, refer to the Welding motion block description in the Arc Welding Function section. Laser welding block 1. Description: Set the welding solution using templates. Drag the block into the programming area and click to open the configuration page. Parameter configuration:

* Welding speed: Set the running speed during the welding process, which is an absolute value and is not affected by the global speed ratio of the robot arm.
* Welding parameter No.: Select the saved custom parameter index.
* Weaving parameter No.: Check this option and set the parameter index for the robot arm to incorporate weaving motion during the welding process based on the configured parameter. See Weaving Process for details.

![Official manual figure, page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBwiMjzDv15Fq7Q19KcAu%2Fwelding-p086-img02.jpg?alt=media)

![Official manual figure, page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fir3MOlLWmTBGybMMfXDW%2Fwelding-p086-img04.jpg?alt=media)

Welding point Enter the "Welding point" page and click "Point description" to view illustrated explanations for various template points. All points can be selected from the point list of the current project or set as the current position of the robot arm. Long-press "Run to" to control the robot arm to move to the currently set point. An alias can be set for the robot's current point, which will be displayed in the point list on the left. Points in the project list cannot have aliases set again.

* Approach point: A starting safety point before welding begins, which is recommended to be set at a position above the arc start point. If an "approach point signal" is configured in the Signal configuration, the software automatically acquires the current point of the robot arm as the approach point when the signal is triggered. "Advanced settings" allows configuring the robot arm's Speed/Acceleration/CP ratio when moving to this point. If unchecked, the robot arm will use the global settings. For details on motion-related advanced parameters, refer to the general description in

## Appendix C of the DobotStudio Pro help document.

* Arc start point: The point at which welding begins.

![Official manual figure, page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8MeasyqhYK3TJTpxm60N%2Fwelding-p087-img02.jpg?alt=media)

![Official manual figure, page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FujvlgtUhXWLz59FUNHwV%2Fwelding-p087-img03.jpg?alt=media)

If the "Arc-start point signal" is configured in Signal configuration, triggering this signal will automatically record the robot arm's current position as the "Arc start point".

* Intermediate point: A path point during the welding process. Multiple intermediate points can be set. Click "+Intermediate point" to add an intermediate point, or click the icon on the right of an Intermediate point to delete it. After adding an intermediate point, you need to select the motion mode for the Intermediate point. a. Line motion: Only one point needs to be set for this motion mode. If the "Intermediate point-line signal" is configured in Signal configuration, triggering the signal will automatically add a linear Intermediate point and record the robot arm's current position. b. Arc motion: Two points must be set for this motion mode.

![Official manual figure, page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw6sYdk4oKqbROmQMsMv5%2Fwelding-p088-img02.jpg?alt=media)

![Official manual figure, page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBo9xyTPmernMPPj8kDOc%2Fwelding-p088-img04.jpg?alt=media)

If the "Intermediate point-line signal" is configured in Signal Configuration, triggering this signal for the first time will automatically add an arc intermediate point and record the robot arm's current position as P1. Triggering again will record the current position as arc P2.

**NOTE**

If the "Intermediate point-line signal" is triggered before triggering the "Intermediate point-arc signal" for the second time, the current intermediate point will be overwritten as the linear intermediate point, and a new intermediate point will be created after the "Intermediate point-arc signal" is triggered again. Triggering the signal of the other DI point will not affect the intermediate point, and the intermediate point will continue to acquire the arc P2 after the "Intermediate point-arc signal" is triggered again. Advanced settings

![Official manual figure, page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0avgDuMrSI7GmxgTUtnI%2Fwelding-p089-img02.jpg?alt=media)

![Official manual figure, page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnfipxpyuRUwp7WP0dcKd%2Fwelding-p089-img03.jpg?alt=media)

Transition radius: It is recommended to select it and set it to a value within the  range of 1 mm to 5 mm, which can make the motion smoother. Welding speed: Modify the welding speed during the welding process after  moving to the Intermediate point. If unselected, use the values set in the "Parameter configuration" page of the block will be used. Welding parameter No.: Modify the welding parameter during the welding  process after moving to the Intermediate point. Weaving parameter No.: Modify the weaving parameter during the welding  process after moving to the Intermediate point.

* Arc end point: The point at which welding ends.

If the "Arc-end point signal" is configured in Signal configuration, triggering this signal will automatically record the robot arm's current position as the "Arc end point".

* Departure point: The end safety point after the welding is completed, more than one can be set. Due to residual heat in the welding torch after welding, it is recommended to set this to a hanging position. Click "+Departure point" to add a departure point, or click the icon on the right of a departure point to delete it.

![Official manual figure, page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVdJ8funHFOh8Y87Zu7fL%2Fwelding-p090-img03.jpg?alt=media)

If the "Departure point signal" is configured in Signal configuration, triggering this signal will automatically record the robot arm's current position as the "Departure point". "Advanced settings" allows configuring the robot arm's Speed / Acceleration / CP ratio when moving to this point. If unchecked, the robot arm will use the global settings. 2. Description: Modify the called laser welding parameter number. Parameter: Custom parameter number that configured in Welding paramters page. If the block is not called, the custom parameter number set in the plugin will be used by default. 3. Description: Notify the welder to start the welding. 4. Description: Notify the welder to stop the welding. 5. Description: Control the welder to perform actions such as wire feed, wire retract, or gas feed. Parameter: 1) Select the action to be performed: wire feed / wire retract / gas feed. 2) Set the duration.

![Official manual figure, page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqNs5Cx77I0gqP65Xsxh9%2Fwelding-p091-img02.jpg?alt=media)

**NOTE**

In this document, all subsequent DEMOs for other functions use arc welding as an example. To use laser welding, replace the "Call arc start param", "Arc start" and "Arc end" blocks with the "Call laser welding param", "Laser welding start" and "Laser welding end" blocks accordingly.

#### 5.6.3 Block DEMO

You can create a project by using laser welding templates or calling motion commands. This DEMO uses welding an arc as an example. Please create a project first, and teach the following points on the point list page (if you use an laser welding template, you can also teach it directly in the template; it is recommended to use an intelligent welding assistant to cooperate with the Fast programming page to quickly teach points):

* P1: Approach point, the safety point before starting welding, which is recommended to be set at a position above the arc start point.
* P2: Arc start point, the point at which welding begins.
* P3: The first arc intermediate point. Together with P2 and P4, it defines the shape of an arc.
* P4: The second arc intermediate point (also the arc end point). This is the point where welding ends.
* P5: Departure point, the end safety point after the welding is completed. Due to residual heat in the welding torch after welding, it is recommended to set this to a hanging position. Using the laser welding template When using the Laser welding template block, you need to set the welding points and parameters. Click to enter the Parameter configuration page, and refer to Block Description to configure the welding parameters. Enter the Welding point page, refer to the above point description and Block Description to configure 5 welding points and welding parameters.
* Set the Approach point to P1.
* Set the Arc start point to P2.
* Add an Intermediate point (arc motion) and set it as P3 and P4.
* Set the Arc end point to P4 (i.e., the second arc intermediate point).

![Official manual figure, page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fwdch4i2DAnbrtJ47Kwvf%2Fwelding-p092-img02.jpg?alt=media)

* Set the Departure point to P5.

![Official manual figure, page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO3F1CXISO5i5oTkYiwVd%2Fwelding-p093-img02.jpg?alt=media)

Calling motion command When the laser welding template is not used, you need to control the robot motion by programming. The welding parameters used in the DEMO are those finally saved on the Welding Parameter Configuration page.

![Official manual figure, page 94](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXXSNNBYTJwB7WcWUx5DA%2Fwelding-p094-img02.png?alt=media)

## 6. Weaving Process

### 6.1 Introduction

Weaving is a welding technique where the welding torch oscillates from side to side at specific angles and intervals relative to the welding direction during the welding process, aiming to enhance the welding strength. Users can configure the weaving method and specific parameters at the plugin page, then call it during programming to add weaving motion onto the designated welding trajectory. To use this function, you need to complete the configuration for weaving process parameters. Afterward, you can create the welding program using either Blockly programming or Script programming.

### 6.2 Weaving process parameter

Set the weaving mode and relevant parameters in the Weaving parameter page.

* Weaving parameter No.: The index of the current welding parameter group, which is used to reference the corresponding parameter group during programming.
* Parameter alias: The alias of the current welding parameter group. It is recommended to set it to a name that is easy to remember.
* Weaving mode: The weaving mode for welding, and the parameters to be set are different for different modes.  Line: No parameter.  Spiral: See figure below.

![Official manual figure, page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaMMrz9IDxoNOAGnPwfqO%2Fwelding-p095-img02.png?alt=media)

![Official manual figure, page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv6sbK2uuUP3361h5WKPS%2Fwelding-p095-img03.jpg?alt=media)

Parameter Description It indicates the direction in which the weaving starts (relative Weave start direction to the forward direction). It indicates the number of weaving cycles completed within 1 Waving frequency second. The higher the frequency, the denser the weaving. Range: (0, 20], recommended to be less than 3 Hz. The amplitude and radius together determine the shape of the Amplitude pattern.

* Amplitude range: \[0, 50], recommended to be less than 6 mm. The greater the frequency, the smaller the amplitude Radius should be.
* Radius unit: mm, range: \[0, 50].

Zigzag/Trapezoid/Sine: The parameters for these three weaving welding modes  are basically the same. The following takes Zigzag as an example. Parameter Description It indicates the direction in which the weaving starts Weaving start direction (relative to the forward direction). It indicates the number of weaving cycles completed within 1 second. The higher the frequency, the denser Waving frequency the weaving. Range: (0, 20], recommended to be less than 3 Hz. Set the maximum amplitude for left and right wave Left amplitude respectively. Range: \[0, 50], recommended to be less than 6 mm. Right amplitude The greater the frequency, the smaller the amplitude should be. For Zigzag weave only. You can set it to Weave stop or Robot stop. Stop mode

* Robot stop: When the robot moves to each specific point (P1 – P4), it stays at that point

![Official manual figure, page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxdCO3Bklis3cPH5ZMIIN%2Fwelding-p096-img02.jpg?alt=media)

Parameter Description for a specified welding time, and then resumes weaving.

* Weave stop: When the robot moves to each specific point (P1 – P4), it pauses weaving, moves along the line from the welding start point to the end point for a specified time, and then resumes weaving. Crescent: see below.  Parameter Description It indicates the direction in which the weaving Weaving start direction starts (relative to the forward direction). It indicates the number of weaving cycles completed within 1 second. The higher the Waving frequency frequency, the denser the weaving. Range: (0, 20], recommended to be less than 3 Hz.

![Official manual figure, page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4Zz0Pqnuz9P3G1Z5Cn2c%2Fwelding-p097-img02.jpg?alt=media)

![Official manual figure, page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvGsYd6HBzEd4mO5fp6Jt%2Fwelding-p097-img03.jpg?alt=media)

![Official manual figure, page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKpfOdeGw83izhfVJ45o1%2Fwelding-p097-img04.jpg?alt=media)

Parameter Description The amplitude and arc depth together determine Amplitude the shape of a weaving cycle.

* Amplitude range: \[0, 50], recommended to be less than 6 mm. The greater the frequency, the smaller the amplitude should be.
* Arc depth unit: %, range: (-100, 100). Positive

Arc depth and negative values determine the direction of crescent bending. If the value is negative, the crescent will bend in the opposite direction. It supports setting dwell time at the two points of the crescent (P1 and P3).

* Robot stop: When the robot moves to the specific point, it stays there for a specified welding time, and then resumes weaving. Stop mode
* Weave stop: When the robot moves to the specific point, it pauses weaving, moves along the line from the welding start point to the end point for a specified time, and then resumes weaving. Triangle: see below. 

![Official manual figure, page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNmsOTD3HwBA6FCcTAdym%2Fwelding-p098-img02.jpg?alt=media)

Parameter Description It indicates the direction in which the weaving Weaving start direction starts (relative to the forward direction). It indicates the number of weaving cycles completed within 1 second. The higher the Waving frequency frequency, the denser the weaving. Range: (0, 20], recommended to be less than 3 Hz. Left amplitude Set the maximum amplitude for left and right wave respectively. Range: \[0, 50], recommended to be less than 6 Right amplitude mm. The greater the frequency, the smaller the amplitude should be. The angle between the workpieces on both sides Angle of the weld seam, unit: °, range: (0, 180). It supports setting dwell time at the three vertices (P1 to P3) of the triangle.

* Robot stop: When the robot moves to the specific point, it stays there for a specified welding time, and then resumes weaving. Stop mode
* Weave stop: When the robot moves to the specific point, it pauses weaving, moves along the line from the welding start point to the end point for a specified time, and then resumes weaving.

### 6.3 Programming

This section introduces the blocks/commands related to weaving and provides corresponding DEMO. Please refer to the Block description and Block DEMO in this chapter when using  blockly programming. Please refer to the Script command and Script DEMO in Appendix A.3 when using  script programming.

#### 6.3.1 Blockly description

Welding motion block The welding motion block is a universal module. For detailed instructions on its usage, refer to the Welding motion block description in the Arc Welding Function section.

Weaving welding block 1. Description: Modify the called weaving parameter number. Parameter: The weaving parameter number configured in Weaving process parameters. If the block is not called, use the weaving process parameter set in the plugin by default. 2. Description: After calling this block, the robot enters the weaving mode, and weaving motion will be added when performing linear or arc motion. 3. Description: Robot exits the weaving mode.

#### 6.3.2 Block DEMO

Using arc welding template Based on the Arc welding block DEMO, check and select "Weaving parameter No." in the configuration page of the arc welding template. Calling motion command Based on the Arc welding block DEMO, add the Weave start block after the Arc start block, and the Weave end block before the Arc end block. The welding parameters used in this DEMO are the final saved parameters from the Welding Parameter Configuration page.

**NOTICE**

The "Weave start" block must be placed after the "Arc start" block, and the "Weave end" block must be placed before the "Arc end" block. As shown in the figure below.

![Official manual figure, page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPm9cLIa3Mdl6D9meQ35N%2Fwelding-p101-img02.jpg?alt=media)

## 7. Multi-Station Welding

### 7.1 Introduction

If you need a robot to execute multiple welding programs in real-time based on on-site requirements, such as welding different workpieces at multiple stations, you can use the Station order block to achieve this.

### 7.2 Multi-station welding programming

#### 7.2.1 Blockly description

Description: By nesting welding programs within this block, different welding programs can be executed based on DI signals. Drag the block into the programming area and click to open the configuration page. You can configure the following signals for 3 stations in the configuration page:

* Station order signal: Triggering this signal will reserve the specified station. Once the robot completes the current welding program, it will continue with the welding program for the reserved station. If multiple station order signals are triggered, the system will add them to the queue in the order they were triggered.
* Station order-cancel signal: Triggering this signal cancels the reservation for the corresponding station.
* Station ready-status output: This signal outputs the status of the corresponding

![Official manual figure, page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuVyt5MzU2hVEdsUwsGO2%2Fwelding-p102-img02.jpg?alt=media)

![Official manual figure, page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhcdSuskayIo1wZQ7AEEz%2Fwelding-p102-img03.png?alt=media)

station, typically used to connect to indicator lights.

1. When the station is free and can be reserved, the output status alternates

continuously (indicator light flashes).

2. When the station is reserved, the output remains ON (indicator light stays on).
3. When the robot is working at the station, the output remains OFF (indicator light

is off).

#### 7.2.2 Block DEMO

First, assume that a control panel like the one shown below, with three station areas. Each station has a reservation button and a cancel button, and each reservation button has an indicator light to show the station's status. Connect the control panel's signal lines to the corresponding I/O interfaces of the robot controller. In this DEMO, the connections are shown in the table below. Station control panel Robot I/O interface Station 1 Reservation button DI\_10 Cancel button DI\_11 Indicator DO\_10 Station 2 Reservation button DI\_12 Cancel button DI\_13 Indicator DO\_11 Station 3 Reservation button DI\_14 Cancel button DI\_15 Indicator DO\_12 Next, write the following program in Blockly programming. Set the "Arc welding template" block based on the actual welding needs of each station.

![Official manual figure, page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU4I9pYE9H76olpHvgrCF%2Fwelding-p103-img02.png?alt=media)

Click the "Station order" block and configure it according to the I/O connections described above.

![Official manual figure, page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsfnenvAdEu5XNvxErjcU%2Fwelding-p104-img02.jpg?alt=media)

![Official manual figure, page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEGIRb92oGK0uKDjfeY3k%2Fwelding-p104-img03.png?alt=media)

![Official manual figure, page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FT8kpseNsAyxgo8PJpJ0l%2Fwelding-p104-img04.png?alt=media)

After saving and running the project, the robot will wait for reservation signals. At this point, all three station indicator lights will be flashing. Then, based on on-site needs, you can make reservations. For example:

1. When the user presses the reservation button of the station 1, the robot starts to

perform the welding procedure of the station 1. At this point, the indicator light for station 1 turns off, while the indicator lights for stations 2 and 3 continue to flash.

2. During welding, you press the reservation button for Station 2.

Now, the indicator light for Station 2 stays on, while the other lights remain unchanged.

3. After the robot completes welding at station 1, it comes to station 2 to perform

welding. At this point, the indicator light for station 2 turns off, while the indicator lights for stations 1 and 3 flash.

4. The user sequentially presses the reservation buttons of the station 1 and the

station 3. According to the normal process, after completing the welding of station 2, the robot will first go to station 1 for welding, and then go to station 3 for welding. At this point, the indicator light for station 2 turns off, while the indicator lights for stations 1 and 3 remain steady on.

5. Before the welding of station 2 is completed, the user presses the cancel button

of station 1 to cancel the reservation of station 1. At this point, the indicator light for station 2 turns off, the indicator light for station 1 flashes, and the indicator light for station 3 remains steady on.

6. After the robot completes welding at station 2, it goes directly to station 3 to start

welding.

## 8. Intermittent Welding

### 8.1 Introduction

Intermittent welding refers to the robot performing welding in a discontinuous manner along a weld seam. It is mainly used for:

* Long weld-seams where full welding is unnecessary for non-critical connections.
* Welding methods that reduce welding deformation by leaving space for movement.

### 8.2 Intermittent welding configuration

Open the welding plugin, connect to the welder, and go to the Intermittent Welding page to set the intermittent welding parameter number. Click Modify to enter the edit page. You can click to add or click to delete intermittent welding parameter numbers next to Intermittent Welding Parameter Number. The parameters of intermittent welding are described as follows: Weld length During intermittent welding, the robot performs the length of a single-section weld. Number of welding The number of sections continuously welded by the robot segments during intermittent welding. After setting Weld Length and Number of welding segments, the system automatically calculates based on the total workpiece length to ensure that the continuous welding sections are evenly distributed across the workpiece. Indentation of the head This is an optional parameter. When enabled, set the distance of the head indentation, which is not included in the total length of the welded workpiece. That is, the starting point of the actual start of welding is after the "Indentation of the head". Indentation of the end Optional parameter, after checking, sets the distance of

![Official manual figure, page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjt191H8BwKtW6kaZH4UZ%2Fwelding-p106-img02.png?alt=media)

effector the end indentation, which is not included in the length of the welded workpiece. The actual end welding point is before the "End indentation". Intermittent welding diagram (excluding head / end indentation) Intermittent welding diagram (including head / end indentation)

### 8.3 Intermittent welding programming

#### 8.3.1 Blockly description

Description: Configure the intermittent welding plan. Drag the block into the programming area and click to open the configuration page.

![Official manual figure, page 107](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzgmBEbHobDX78aio9tnR%2Fwelding-p107-img02.png?alt=media)

![Official manual figure, page 107](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1MVP1bzkEuCwqXnhu0pR%2Fwelding-p107-img03.png?alt=media)

Parameter configuration:

* Intermittent welding parameter number: Select the saved intermittent welding parameter number. For configuration methods of the intermittent welding parameter number, see Intermittent welding configuration.
* Welding method: You need to select the welding method only for Flama / Aotai /

Megmeet / OTC / Panasonic / YaoLi welders, while other welders do not necessitate this step. See Welding parameters for details.

* Welding param No.: During intermittent welding process, select the saved custom welding parameter number when setting welding parameters in non-Job mode.
* Job No.: Select the Job number of the welder (welder process number) when using the Job mode during intermittent welding.
* Online control parameter No.: This must be set for Kemppi welders.
* Program No.: For Fronius (TPS5000CMT), EWM, and SKS welders, a program number (welding parameter number) must be set in addition to the Job number.

![Official manual figure, page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI2ZOHPis4bJOkm5fRlNn%2Fwelding-p108-img02.png?alt=media)

* Weaving parameter No.: Check this option and set the weaving parameter index for the robot arm to incorporate weaving motion during the welding process based on the configured parameter. See Weaving Process for details.
* Welding Speed: The speed during the welding segments of intermittent welding. This speed is an absolute value and is not affected by the global speed ratio of the robot arm. The speed during the non-weld segments will follow the robot's global speed settings.
* Transition radius: If a smoother trajectory is required, it can be set to 5mm (it is not recommended to exceed 10mm, as this may cause significant trajectory deformation and the molten pool cannot fit the weld seam); if there is no requirement for trajectory smoothness, this parameter does not need to be set.

**NOTICE**

1. If the "Parameter configuration" page is incomplete, entry into the

"Welding point" page is not allowed.

2. Changing the "Welding method" will uncheck previously selected welding

parameters in the "Welding point" page. Welding point Go to the Welding Point page and click Point Description to view the illustrated explanation of each point in the intermittent welding template.

![Official manual figure, page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcnpFiDVnGXcF2PviNMPJ%2Fwelding-p109-img02.png?alt=media)

All points can be selected from the point list of the current project or set as the current position of the robot arm. Long-press "Run to" to control the robot arm to move to the currently set point. An alias can be set for the robot's current point, which will be displayed in the point list on the left. Points in the project list cannot have aliases set again.

* Approach point: A starting safety point before welding begins, which is recommended to be set at a position above the arc start point. If an "approach point signal" is configured in the Signal configuration, the software automatically acquires the current point of the robot arm as the approach point when the signal is triggered. "Advanced settings" allows configuring the robot arm's Speed/Acceleration/CP ratio when moving to this point. If unchecked, the robot arm will use the global settings. For details on motion-related advanced parameters, refer to the general description in

## Appendix C of the DobotStudio Pro help document.

![Official manual figure, page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwdYIWmjJAGTpPxvBsXQU%2Fwelding-p110-img02.png?alt=media)

![Official manual figure, page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM7DuxNmtM59ZJed4FvhN%2Fwelding-p110-img03.png?alt=media)

* Arc start point: The point at which the welder starts an arc and starts welding. If

"indentation of the head" is set in the welding parameter number, the torch will travel this specified distance before actual welding. If the "Arc-start point signal" is configured in Signal configuration, triggering this signal will automatically record the robot arm's current position as the "Arc start point".

* Intermediate point: A path point during the welding process. Multiple intermediate points can be set. Click "+Intermediate point" to add an Intermediate point, or click the icon on the right of an Intermediate point to delete it. After adding an Intermediate point, you need to select the motion mode for the Intermediate point. a. Line motion: Only one point needs to be set for this motion mode.

![Official manual figure, page 111](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwTbaktfHVO3OGblD5D60%2Fwelding-p111-img02.png?alt=media)

![Official manual figure, page 111](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRdad93trAnQ0COc4KzoV%2Fwelding-p111-img04.png?alt=media)

If the "Intermediate point-line signal" is configured in Signal Configuration, triggering the signal will automatically add a linear Intermediate point and record the robot arm's current position. b. Arc motion: Two points must be set for this motion mode. If the "Intermediate point-line signal" is configured in Signal configuration, triggering this signal for the first time will automatically add an arc Intermediate point and record the robot arm's current position as P1. Triggering again will record the current position as arc P2.

**NOTE**

If the " Intermediate point-line signal" is triggered before triggering the "Intermediate point-arc signal" for the second time, the current intermediate point will be overwritten as the linear intermediate point, and a new intermediate point will be created after the "Intermediate point-arc signal" is triggered again. Triggering the signal of the other DI point will not affect the intermediate point, and the intermediate point will continue to acquire the arc P2 after the " Intermediate point-arc signal" is triggered again.

* Arc end point: The point at which the welder ends the arc and completes the welding process. If an “end indentation” is set in the welding parameter number, the torch will stop welding before reaching “end indentation”.

![Official manual figure, page 112](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7uwARaoM2v53X4raHzZA%2Fwelding-p112-img02.png?alt=media)

If the "Arc-end point signal" is configured in Signal configuration, triggering this signal will automatically record the robot arm's current position as the "Arc end point".

* Departure point: The end safety point after the welding is completed, more than one can be set. Due to residual heat in the welding torch after welding, it is recommended to set this to a hanging position. Click "+Departure point" to add a departure point, or click the icon on the right of a departure point to delete it. If the "Departure point signal" is configured in Signal configuration, triggering this signal will automatically record the robot arm's current position as the "Departure point". "Advanced settings" allows configuring the robot arm's Speed/Acceleration/CP ratio when moving to this point. If unchecked, the robot arm will use the global settings.

![Official manual figure, page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYEzdrAx1dkYKSjcN88tc%2Fwelding-p113-img02.png?alt=media)

![Official manual figure, page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLfv5EzJxxwTyaAhJO5ZV%2Fwelding-p113-img04.png?alt=media)

#### 8.3.2 Block DEMO

After running the intermittent welding DEMO as shown in the figure above, the robot arm moves as shown in the figure below: Firstly, move from the approach point P1 to the arc start point P2. According to the set head indentation of 10 mm, advance along the teaching trajectory ① to P2’ to start the arc. ② Then, following the settings of intermittent welding parameter number 1, it completes three weld seams, each 20 mm in length, at a speed of 10 mm/s. Based on the set ③ end indentation of 10 mm, it finally reaches the actual arc end point P3'. It then moves forward along the trajectory to the taught arc end point P3. Finally move to departure point P4. ④ ⑤

![Official manual figure, page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYoa1wfedKsjripnqWFVr%2Fwelding-p114-img03.png?alt=media)

![Official manual figure, page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fy8bbpmasBhuTugmwKfoU%2Fwelding-p114-img04.png?alt=media)

![Official manual figure, page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQdVtQa3cPuQufPaJ0xtl%2Fwelding-p114-img05.png?alt=media)

![Official manual figure, page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FopWILZiVGY0tL8uPWWtT%2Fwelding-p114-img06.png?alt=media)

## 9. Laser Positioning and Tracking

### 9.1 Introduction

The laser positioning function scans the position of the weld seam on the workpiece using a laser sensor mounted on the end of the robot arm. Once the actual point corresponding to the weld seam is obtained:

* Save the point or directly move to the point (absolute positioning).
* Calculate the offset between the point and the datum point, thereby correcting the welding trajectory (relative positioning). The laser tracking function involves real-time scanning and correcting the welding trajectory during the welding process. To use the laser positioning and tracking functions, you need to install and configure the laser sensor, perform laser calibration, and then choose either Blockly programming or Script programming to write the welding program.

**NOTE**

This document mainly introduces the operation method on the robot (DobotStudio Pro). For operation method on the sensor (e.g., CUTEWELDER by Intelligent Laser), please refer its user manual.

### 9.2 Laser sensor installation

Take the laser sensor produced by Intelligent Laser as an example (host control: IL- HOST03, sensor: IL-LSP-150SD02), the wiring method is as follows:

1. Connect the sensor to the control host with the FUNCTION and LAN cables.
2. Connect the host control unit to the LAN1 interface of the robot controller with the

communication cable.

3. Connect the host control unit to the mains power supply with the power adapter.
4. Connect the keyboard and mouse to the USB interfaces of the host control unit, and

connect the monitor to the HDMI or DVI interface of the host control unit. These peripherals are used to operate the laser sensor's control software, CUTEWELDER.

5. Set the IP addresses of the host control unit, robot arm and computer, keeping them

in the same network segment without conflict. For the IP modification method, please refer to DobotStudio Pro help document. Example: Host control IP: 192.168.5.10 Robot arm IP: 192.168.5.1 Computer IP: 192.168.5.100

6. If you need to use the laser sensor in high-temperature environment, connect to the

air cooling system. Connect the sensor vent and air compressor through the air tube and triplet, and adjust the air pressure to 100Kpa.

**NOTE**

* Operating temperature for the sensor: 5 C – 40 C.

° °

* Ensure that the cooling air source is dry and free from oil.
* The host control unit must be grounded separately.

No. Description No. Description No. Description a Host control unit b Laser sensor c FUNCTION cable Communication d LAN cable e f Power adapter cable Mouse & g h Monitor (optional) i Robot controller Keyboard Optional parts for high-temperature environments: No. Description No. Description No. Description j Air tube k Triplet l Air compressor When installing the laser sensor, first adjust the welding torch to the correct welding posture and move it to the welding point, and then adjust the mounting angle of the laser sensor so that it forms an angle of 5° – 15° with the plane of the workpiece. The ideal distance between the laser beam and the tip of the welding torch is 35mm – 60mm, as shown in the figure below.

![Official manual figure, page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FANwn4cvKjYQbjCY8xSZd%2Fwelding-p116-img02.jpg?alt=media)

If the sensor is correctly installed and the welding torch is in the proper welding posture, launching the laser sensor's control software CUTEWELDER should display the TP point as a central feature within the image, as shown in the figure below.

![Official manual figure, page 117](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWrEspmKqKa3gmDbuxzVy%2Fwelding-p117-img02.jpg?alt=media)

![Official manual figure, page 117](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fs4UOaSbGmHnLGLGnuIgo%2Fwelding-p117-img03.jpg?alt=media)

### 9.3 Laser sensor configuration

Please configure the laser sensor related parameters in the "Laser sensor configuration" page of the welding plugin.

* Laser manufacturer: SmartImage AI (positioning function only, no tracking function) and Intelligent Laser. This document takes Intelligent Laser as an example to describe the use of the laser sensor.
* IP address: IP address of the sensor's host control unit.
* Port: The port number of the sensor's host control unit, the default port for Intelligent

Laser is 5020. When the laser manufacturer is Intelligent Laser and the page is in non-editing status, the Laser switch will be displayed. The laser switch can be turned on or off when no project is running.

![Official manual figure, page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9jjwUutzJfu4CuUpvXJL%2Fwelding-p118-img02.png?alt=media)

![Official manual figure, page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmLGDJkBHVvKUyx9tX7DU%2Fwelding-p118-img03.png?alt=media)

### 9.4 Laser calibration

After configuring the laser sensor, you need to calibrate the laser sensor to determine the positional relationship between the laser sensor and the torch tip. The welding process package offers blocks and scripts for laser calibration. You can create and run projects containing laser calibration blocks or script commands for calibration according to your needs.

**NOTICE**

When calibrating the laser sensor, the wire stick-out length should be the same as it was when Setting the tool coordinate system.

**NOTE**

The calibration steps for Full-V lasers and Intelligent lasers are essentially the same. This section uses Intelligent lasers as an example. When using the Full-V laser, replace block with (for script programming, replace the YLLaserCalibrate command with FullVLaserCalibrate), and replace the Intelligent Laser's CUTEWELDER software with the Full-V laser's control software.

#### 9.4.1 Calibrating via blockly programming

1. Create a new blockly project, drag the Intelligent laser calibration block under Start

block.

![Official manual figure, page 119](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjEgCT6p56a3dA9i3i3Kj%2Fwelding-p119-img02.jpg?alt=media)

2. Click the Intelligent laser calibration block to open the "Laser calibration parameter

configuration" page.

3. Refer to the diagram above and the description below, go to the Points page to teach

and save 5 points.

* Workpiece feature point: Move the robot arm to align the welding torch tip with the marked feature point on the sample, save the point and select it here.
* Photo point 1: Move the robot arm to align the laser beam with the feature point, ensuring that the feature point is stable and displayed at the upper part of the CUTEWELDER software screen (refer to the following figure). Save the point and select it here.
* Photo point 2: Move the robot arm to raise the welding torch vertically, keeping the

![Official manual figure, page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2FhFpzpQyjiMBsSCQ2lL%2Fwelding-p120-img02.png?alt=media)

![Official manual figure, page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwOHxBoYgyHZNm8Wzlez2%2Fwelding-p120-img03.png?alt=media)

![Official manual figure, page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEOI6baOA48X4XAE0ccBe%2Fwelding-p120-img04.jpg?alt=media)

laser beam aligned with the feature point, and ensuring that the feature point is centered on the screen (refer to the following figure). Save the point and select it here.

* Photo point 3: Move the robot arm to translate the welding torch along the direction of the laser beam, keeping the laser beam aligned with the feature point, and ensuring that the feature point is in the bottom left corner of the screen (refer to the following figure). Save the point and select it here.
* Photo point 4: Move the robot arm to translate the welding torch in the opposite direction along the laser beam, keeping the laser beam aligned with the feature point, and ensuring that the laser point is in the bottom right corner of the screen (refer to the following figure). Save the point and select it here. To ensure calibration accuracy, it is recommended that the position of each feature point displayed in the CUTEWELDER software be far away from each other.

4. Go back to the programming page in DobotStudio Pro, select these 5 points in turn in

the "Laser calibration parameter configuration" page, then set the Speed and Acceleration ratio for the robot to move to each point according to the actual needs. If speed or acceleration is not set, the default value is 50%.

5. Save the configuration and run the project.
6. After running the project, you can verify the calibration accuracy through absolute

positioning (see Laser absolute positioning). The accuracy error between the torch tip and the marked point is not more than 1mm by visual inspection, as shown in the figure below.

![figure below.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzxpAmQe5TouXFKU3MQja%2Fwelding-p121-img02.jpg?alt=media)

![Official manual figure, page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVeOE7NK9Wr3U1zNX8nz0%2Fwelding-p121-img03.jpg?alt=media)

#### 9.4.2 Calibrating via script programming

1. Create a new script project. Following the description of the five points in

Calibration via blockly programming, teach and save five points (P1–P5).

2. Insert the following scripts in the programming page.

laser\_autocaliPointArr = {P1,P2,P3,P4,P5} -- P1 to P5 are the 5 points taught in Step 1. YLLaserCalibrate(laser\_autocaliPointArr, {v = 50, a = 50}) -- Modify the speed (v) and acceleration (a) according to actual needs.

3. Save and run the project.
4. After running the project, you can verify the calibration accuracy through absolute

positioning (see Laser absolute positioning). The accuracy error between the torch tip and the marked point is not more than 1mm by visual inspection.

### 9.5 Laser positioning programming

This section introduces the blocks/commands related to laser positioning and provides corresponding DEMO.

* Please refer to the Block description and Block DEMO in this chapter when using blockly programming.
* When using script programming, refer to Script command description and Script

DEMO in Appendix A.4.

#### 9.5.1 Blockly description

Laser absolute positioning 1. Description: Find the target point through the laser sensor and move to the target point. Parameter: 1) Photo point: The point of the robot arm when the laser beam is aligned with the point to be positioned (arc start point, arc end point, etc.). 2) Waiting time: The waiting time after the robot arm moves to the photo point. It is recommended to keep the default value (2000ms) if you do not have special requirements. 3) Job: The seam type index (Job No.) set in the CUTEWELDER software. 4) Welding torch posture reference: The posture reference point when the robot arm moves to the target point obtained by positioning. That is, the X/Y/Z of the target point is obtained through laser positioning, while RX/RY/RZ, as well as the user and tool coordinate systems are obtained through the reference point.

2. Description: Find the target point through the laser sensor and save the target point. Parameter: 1) Photo point: The point of the robot arm when the laser beam is aligned with the point to be positioned (arc start point, arc end point, etc.). 2) Waiting time: The waiting time after the robot arm moves to the photo point. It is recommended to keep the default value (2000ms) if you do not have special requirements. 3) Job: The seam type index (Job No.) set in the CUTEWELDER software. 4) Welding torch posture reference: The posture reference point when the robot arm moves to the target point obtained by positioning. That is, the X/Y/Z of the target point is obtained through laser positioning, while RX/RY/RZ, as well as the user and tool coordinate systems are obtained through the reference point. 5) Target point: Select the target point. 3. Description: Move to the saved target point. Parameter: 1) Positioning target: Select the saved target point. 2) Speed: The speed when moving to the target point. Laser relative positioning 1. Description: Find the target point, calculate the offset between the target point and the datum point, then save it. Parameter: 1) Datum point No.: The corresponding index of the datum point for positioning. You need to run this block once first to get the benchmark. See Laser relative positioning DEMO for details. 2) Offset No.: The saved index of the calculated offset value.

Drag the block into the programming area and click to open the configuration page. Laser relative positioning supports the following "positioning method".

* Point positioning: Supports finding the offset of a single point from up to three directions (X/Y/Z).
* Surface positioning: Determines a plane through three non-collinear points and calculates the offset of the origin of the coordinate system. It is suitable for regular workpieces with right-angle sides.
* Inner and outer diameter positioning: Determines a circle through three non- collinear points and calculates the offset of the center of the circle. It is suitable for regular workpieces with circular inner or outer diameters.

![Official manual figure, page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FB2DPhSvIJvhJUyn0pryb%2Fwelding-p124-img02.png?alt=media)

![Official manual figure, page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpUIP0joaNTJFh5QCKunN%2Fwelding-p124-img03.png?alt=media)

![Official manual figure, page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwAmIThrQPI5WCjXMnN3K%2Fwelding-p124-img04.png?alt=media)

Different positioning methods require different parameters to be set. The following section first introduces the common parameters among these positioning methods, followed by the parameters specific to each positioning method. Common parameters:

* Photo waiting time: The waiting time after the robot arm moves to the photo point.

Value range: 0 to 10000. Unless otherwise required, it is recommended to keep the default value of 2000 ms.

* Update the datum point: When you use this block for the first time, please select this option, then place the workpiece at the standard position and perform positioning. The positioning result will be saved as the datum point. The next time you use the block, select the same Datum point No. and leave this option unselected, and the offset will be calculated based on the saved datum point. If you need to update the datum point, select this option again and run the block. The datum point is saved globally, and the saved datum point can be used in other projects. Click "Check" to view the current X/Y/Z values of the datum point, and set an alias for the datum point. After selecting the "Welding torch posture reference" (used for referencing RX/RY/RZ values as well as the user and tool coordinate systems), the robot can move to the specified datum point.
* Speed/Acceleration: You can tick it and set the ratio of speed or acceleration when the robot arm moves to each photo point.
* Transition point CP: After adding transition points, you can tick it and set the CP ratio of the motion between/among transition points to make the motion between/among transition points smoother.

![Official manual figure, page 125](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJFEXKsgtyfJgvRWx7pOo%2Fwelding-p125-img03.jpg?alt=media)

Point positioning parameters:

* Photo Point 1/2/3: Support 1 to 3 photo points, point the laser at the point to be located from different directions. Click the "+" on the right of "Positioning method" to add a photo point, or click the "-" to remove a photo point.
* Offset direction: Select the offset direction (X/Y/Z) corresponding to the current photo point (select one only). The offset direction of each photo point cannot be repeated.
* Job: The seam type index (Job No.) set in the CUTEWELDER software.
* Incremental positioning: This function can be selected for Photo point 2 and Photo point 3. After selecting, the photo point will be offset according to the positioning results of the previous photo points before taking photos. For example: ◦ The photo point 1 is offset in the X direction. ◦ The photo point 2 is offset in the Y direction. ◦ The photo point 3 is offset in the Z direction. ◦ Incremental positioning is enabled for both camera points 2 and 3. When running: ◦ The photo point 2 will be offset in the X direction according to the positioning result of the photo point 1. ◦ The photo point 3 will be offset in the X and Y directions according to the positioning results of the photo points 1 and 2.
* Transition point: You can add 0–5 transition point(s) for each group of positioning start points to avoid obstacles.

![Official manual figure, page 126](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0p46oqAfRAO71ltSCAXg%2Fwelding-p126-img03.png?alt=media)

Surface positioning parameters:

* Photo point 1/2/3: Photo point 1 and 2 are any two points on any perpendicular edge of the workpiece (where the laser line aligns with the marked point, same below); Photo point 3 is any point on the adjacent perpendicular edge.
* Job: The seam type index (Job No.) set in the CUTEWELDER software.
* Transition point: You can add 0–5 transition point(s) for each group of positioning start points to avoid obstacles.

![Official manual figure, page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLnb9PL2S3kx7h8vJE35f%2Fwelding-p127-img02.png?alt=media)

![Official manual figure, page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBF08nW40OrmYHXpYckZs%2Fwelding-p127-img03.png?alt=media)

Inner and outer diameter positioning parameters:

* Photo point 1/2/3: Photo point 1, 2, and 3 are three non-collinear points on the inner or outer diameter of the arc of the workpiece (the point when the laser beam is aligned with the marked point).
* Job: The seam type index (Job No.) set in the CUTEWELDER software.
* Transition point: You can add 0–5 transition point(s) for each group of positioning start points to avoid obstacles. 2. Description: Add the saved offset value onto the subsequent robot motion trajectory (only linear, arc, and circle motion commands are supported). Calling this block repeatedly before calling the block will update the compensated offset value. Parameter: The saved index of the offset value. 3. Description: Stop adding the trajectory offset values.

![Official manual figure, page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcHBaKHPHQb2IVh1jBcqK%2Fwelding-p128-img02.png?alt=media)

![Official manual figure, page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIrgJgTJ3rVasu5lqVzZ5%2Fwelding-p128-img03.png?alt=media)

Laser offset compensation Description: Provide real-time offset adjustment for the target point of laser positioning or the trajectory of laser tracking. This block is used before the laser positioning/laser tracking block. Parameter: 1) X, Y, Z: The offset compensation values in three-dimensional space. You can enter positive or negative values, with the unit in millimeters (mm). The system will adjust the welding position based on the set values. 2) User: Select the user coordinate system to determine which coordinate system the compensation is applied to.

#### 9.5.2 Block DEMO

Laser absolute positioning The following two DEMOs have similar effects. The main difference is that DEMO2 can set the speed of moving to the target point, and can insert other blocks before moving to the target point, which makes it more flexible to use. DEMO1:

DEMO2: Laser relative positioning (Point positioning) This demo shows point positioning in X and Y directions. Get datum point Place the workpiece in the standard position, P1 and P2 align the laser beam from different directions to the point to be positioned, run the above project, the robot arm will run to P1 and P2 in turn to search for the point, and save the point obtained as datum point.

![Official manual figure, page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrkMJwoxefxoW3y7TWe0k%2Fwelding-p130-img02.jpg?alt=media)

![Official manual figure, page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm1dezSHzuoiuLJ63YmWt%2Fwelding-p130-img03.jpg?alt=media)

Point positioning After running the Get datum point DEMO before running this DEMO, the datum point numbers of both demos need to be consistent. Points during the welding process can be taught as needed. This DEMO does not provide detailed instructions. The welding parameters used in the DEMO are those finally saved on the Welding parameter configuration page.

![Official manual figure, page 131](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNmEUoIpy7xP3u39xaUIG%2Fwelding-p131-img02.png?alt=media)

Laser relative positioning (Surface positioning) Here demonstrates how to perform surface positioning. Get datum point Place the workpiece in the standard position, refer to the diagram, align the laser beam with two points on any right-angled side of the workpiece, and teach P1 and P2. Then align the laser beam with any point on the adjacent right-angle side and teach P3. Run the above project. The robot arm will move to P1, P2, and P3 in sequence to perform positioning, and save the points obtained from positioning as datum points.

![Official manual figure, page 132](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3pUsCpWFPWdw0yQZoCDH%2Fwelding-p132-img02.jpg?alt=media)

Surface positioning After running the Get datum point DEMO before running this DEMO, the datum point numbers of both demos need to be consistent. Points during the welding process can be taught as needed. This DEMO does not provide detailed instructions. The welding parameters used in the DEMO are those finally saved on the Welding parameter configuration page.

![Official manual figure, page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvOQJVzzTsB4GURYo9egD%2Fwelding-p133-img02.png?alt=media)

### 9.6 Laser tracking programming

This section introduces the blocks/commands related to laser tracking and provides corresponding DEMO.

* Please refer to the Block Description and Block DEMO in this chapter when using blockly programming.
* When using script programming, refer to Script Command Description and Script

DEMO in Appendix A.5.

#### 9.6.1 Blockly description

1. Description: Start laser weld seam tracking (compatible with various laser sensors). Repeated calling of this block is not allowed before calling. The trajectory of the robot after starting tracking (only linear, arc, and circle motion commands are supported) will be automatically corrected based on the tracking results. Parameter: 1) The seam type number (Job No.) set in the laser sensor's control software. 2) The tool coordinate system used when selecting the taught welding points. 2. Description: Stop laser seam tracking (compatible with various laser sensors).

**NOTICE**

* To ensure that tracking starts normally, the tracking start point (where the laser beam is located at the arc start point), the arc start point and the first transition point should be kept in a straight line as far as possible. See the following DEMO for details.
* When teaching the welding point, the distance between the teaching point and the seam should not exceed 10mm to avoid affecting the welding quality.
* During tracking, the motion command must specify the transition radius (5 mm or more). For paths with a large turning radius such as S-curves, it is recommended to set a larger transition radius (10mm or more).
* Weaving is not supported during tracking.
* Laser positioning is not supported after laser tracking is turned on. If you need to use the laser positioning and laser tracking function together, you can get the positioning target first, turn on the tracking function, and then move to the positioning target. See Laser Absolute Positioning + Tracking (DEMO) for details.
* In case the seam trajectory is a curve, it is recommended to weld at a speed of less than or equal to 10mm/s to ensure the seam forming effect. If you need to weld at a faster speed, you can use Intelligent Laser's misalignment compensation function. Consult Intelligent Laser's technical support for details.
* If there is a sudden change in the seam trajectory (e.g. the direction of the curve changes significantly when a straight line is connected to a curve, refer to the trajectory in the figure below), it is recommended to weld at a speed of less than or equal to 10mm/s to ensure the seam forming effect.

![Official manual figure, page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvy0kwf4WrOZQAmesClDE%2Fwelding-p135-img03.png?alt=media)

![Official manual figure, page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsDIBdJr5eOQy25gQ3qFV%2Fwelding-p135-img04.jpg?alt=media)

* If you need to use Intelligent Laser's offset setting function (see the figure below), it is recommended to set the offset to no more than 5mm. If the offset is greater than 5mm, it means that the calibration error of the welding torch or laser is too large, and recalibration is recommended.

#### 9.6.2 Block DEMO

Taking the workpiece in the above figure as an example, the user needs to teach the points 1, 3, 4, and 5 in the figure, and obtain the point 2 by absolute positioning. Point 1 is the tracking start point, point 2 is the arc start point, points 3 and 4 are transition points (if using the common laser tracking block, transition points do not need to be taught), and point 5 is the arc end point. In addition, you need to teach the safety point P6 after welding is finished. When teaching P1, please try to ensure that P1, P2 and P3 are close to a straight line (as shown in the figure above). If the direction of P2 changes a lot (as shown in the figure below, the angle of the three points is close to or less than a right angle), it may cause the laser to fail to track properly.

![Official manual figure, page 136](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAkcxAXNDSyYIms2qs3S2%2Fwelding-p136-img03.jpg?alt=media)

The distance between points 2 to 5 and the real weld seam should not exceed 10mm, otherwise it will affect the welding effect. When teaching the arc end point (P5), it is recommended to advance a certain distance relative to the end of the weld seam to avoid alarms due to failure to scan the seam when the welding is about to end. The welding parameters used in the DEMO are those finally saved on the Welding parameter configuration page.

![Official manual figure, page 137](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7qVYMzdomGmI1p4LnFuh%2Fwelding-p137-img02.jpg?alt=media)

![Official manual figure, page 137](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2nCHgLJd38uwBAoOXlLP%2Fwelding-p137-img03.png?alt=media)

### 9.7 Laser absolute positioning + Tracking (DEMO)

#### 9.7.1 Block DEMO

Take the workpiece in the above figure as an example, you need to teach two points. P1 is the photo point of the arc start point, teach P1 after aligning the laser to the start point. P2 is the photo point of the arc end point, teach P2 after aligning the laser to the start point. Then teach P3 as the posture reference point, which is used for referencing the welding torch posture as well as the user and tool coordinate system during welding. Teach P4 as the safety point after finishing the welding. For requirements such as the positional relationship between points and seams, please refer to the previous DEMO.

![Official manual figure, page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5TMzjM3eofxemz5jnQ4m%2Fwelding-p138-img02.jpg?alt=media)

![Official manual figure, page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNwCysP0jLIfZXEQgL4rA%2Fwelding-p138-img03.jpg?alt=media)

## 10. Touch Positioning

### 10.1 Introduction

The touch positioning function uses the welding wire to make contact with the workpiece to obtain its actual position. This helps calculate the offset between the actual weld-seam position and the taught position, allowing for precise correction and compensation. The welders and communication modes that support the touch sensing function are as follows: Communication mode No. Welder brand Analog I/O DeviceNet Modbus Ethernet/IP Fronius TPS 1 √ Fronius (Austria) Fronius TPSI 2 √ √ Fronius (Austria) Fronius iwave 3 √ Fronius (Austria) Kemppi DCM 4 √ Kemppi (Finland) Kemppi RCM 5 √ Kemppi (Finland) 6 EWM (Germany) √ √ ESAB 7 Aristo 500ix/U5000w/5000iw √ √ ESAB (Sweden) ESAB Transming DP/P/H 8 √ ESAB (Sweden) ESAB 9 Aristo dege √ √ ESAB (Sweden) 10 GYS (France) √ 11 Megmeet (China) √ √ √ √

Communication mode No. Welder brand Analog I/O DeviceNet Modbus Ethernet/IP Aotai MIG-LST 12 √ √ √ Aotai (China) Aotai MIG-PLUS 13 √ √ √ Aotai (China) The touch positioning process for a specific point is as follows:

1. The robot sends a positioning enable signal to the welder. After the positioning function

of the welder is enabled, a positioning success signal will be output when the welding wire touches the workpiece.

2. The robot moves to the specified starting point for positioning and then moves along

the specified direction until it receives the positioning success signal from the welder or exceeds the specified positioning distance.

3. When positioning is successful, the robot records the current point, calculates its offset

from the datum point, and adjusts the taught trajectory accordingly to obtain the real target trajectory.

**NOTICE**

When positioning, the wire stick-out length should be the same as it was when Setting the tool coordinate system. To use this function, you need to complete the configuration of signals related to touch positioning and create the welding program via Blockly programming.

### 10.2 Signal configuration

Before using the touch positioning function, you need to configure the relevant signals in "Signal configuration" page.

**NOTE**

For Aotai MIG-LST, Aotai MIG-PLUS, or Megmeet welders using Analog I/O communication, the touch positioning signal needs to be set. In other cases, there is no need to configure the touch positioning signal.

* Positioning enable signal: DO signal that controls the welder to enable the touch positioning function.
* Positioning success signal: DI signal that indicates the touch positioning is successful.
* Positioning failure signal: DO signal that indicates the touch positioning failed.

If there is no need to output a positioning failure signal, it can be set to "Not configured".

### 10.3 Touch positioning programming

This section introduces the blocks related to touch positioning and the corresponding DEMOs. Script programming is not supported at the moment.

#### 10.3.1 Blockly description

1. Description: Find the target point through touch positioning, calculate the offset between the target point and the datum point, then save it. Parameter: 1) Datum point No.: The corresponding index of the datum point for positioning. You need to run this block once to get the datum point, as detailed in the following DEMO. 2) Offset No.: The saved index of the calculated offset value. Parameter configuration: Drag the block into the programming area and click it to open the configuration page. Then, click the "Parameter configuration" page and set the common parameters for the touch positioning function.

![Official manual figure, page 141](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYMYe4iASLkh9uH4RUuSY%2Fwelding-p141-img02.jpg?alt=media)

**NOTE**

If the welder does not support the touch positioning function, a message will appear when the "Touch positioning" block is opened, stating that "This function is not yet available for this welder".

* Positioning distance: The maximum motion distance from the start point in the positioning direction. If the target is not detected within this distance, the positioning operation is considered a failure. In such cases, the robot will report an error and trigger the designated DO signal (the "Positioning failure signal" needs to be configured in the "Signal configuration" tab). Range: 1mm – 1000mm.
* Positioning speed: The motion speed during positioning. A faster speed may cause deformation of the wire when it touches the workpiece, increasing the error. A slower speed results in higher positioning accuracy but lower efficiency. Range: 1mm/s – 20mm/s.
* Auto return: When this option is selected, the robot will automatically return along the original path after successful positioning. The return distance and return speed can be set. If the return distance is greater than the distance from the successful positioning point to the start point, the robot will stop moving after returning to the start point. Return distance range: 1mm – 1000mm. Return speed range: 1mm/s – 1000mm/s.

![Official manual figure, page 142](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA2KnNLGb5xYPjsXIF0U3%2Fwelding-p142-img02.png?alt=media)

![Official manual figure, page 142](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FizDcV4pj0RwEH2ezRKXV%2Fwelding-p142-img04.png?alt=media)

Positioning method: Switch to the "Touch point" page, and select the "Positioning method".

* 1D positioning: Locates a point in one direction, used in scenarios where the workpiece only translates in one direction relative to the reference position.
* 2D positioning: Locates a point in two perpendicular directions, used in scenarios where the workpiece translates in two directions relative to the reference position.
* 3D positioning: Locates a point in three perpendicular directions, used in scenarios where the workpiece translates in three directions relative to the reference position.
* 2D+ positioning: Determines a plane through three non-collinear points and calculates the offset of the origin of the coordinate system. It is used for scenarios where a workpiece with right-angle sides shifts and rotates on a plane relative to the reference position.

![Official manual figure, page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fypxv0Ss11oV0N15HVFnq%2Fwelding-p143-img02.jpg?alt=media)

![Official manual figure, page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMLUm1WUA5NYjpTyOQzVM%2Fwelding-p143-img03.jpg?alt=media)

![Official manual figure, page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmapwGvFfXHF6CUBe3E0Y%2Fwelding-p143-img04.png?alt=media)

* 3D+ positioning: It requires teaching six points: three on the workpiece surface to determine the offset relative to the placement plane, and three on two adjacent sides of that surface. It is similar to 2D+ positioning and is used to determine the offset and rotation of the workpiece parallel to the plane.
* Inner and outer diameter positioning: Determines a circle through three non- collinear points and calculates the offset of the center of the circle. It is suitable for regular workpieces with circular inner or outer diameters. Different positioning methods require different parameters to be set. The following section first introduces the common parameters among these positioning methods, followed by the parameters specific to each positioning method.

![Official manual figure, page 144](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUx8OZSMw2dJcpd6UCaps%2Fwelding-p144-img02.png?alt=media)

![Official manual figure, page 144](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwXHb8JjW0wRjBEKBPKvI%2Fwelding-p144-img03.png?alt=media)

![Official manual figure, page 144](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzrcYwdRn6IOrxcuEML8o%2Fwelding-p144-img04.png?alt=media)

Common parameters:

* Update the datum point: When you use this block for the first time, please select this option, then place the workpiece at the standard position and perform positioning. The positioning result will be saved as the datum point. The next time you use the block, select the same Datum point No. and leave this option unselected, and the offset will be calculated based on the saved datum point. If you need to update the datum point, select this option again and run the block. The datum point is saved globally, and the saved datum point can be used in other projects. Click "Check" to view the current X/Y/Z values of the datum point, and set an alias for the datum point. After selecting the "Welding torch posture reference" (used for referencing RX/RY/RZ values as well as the user and tool coordinate systems), the robot can move to the specified datum point.
* Positioning start point / transition point speed: You can tick it and set the speed ratio when the robot moves the positioning start point and transition point.
* Positioning start point / transition point acceleration: You can tick it and set the acceleration ratio when the robot moves the positioning start point and transition point.
* Transition point CP: After adding transition points, you can tick it and set the CP ratio of the motion between/among transition points to make the motion between/among transition points smoother.

![Official manual figure, page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fr9ohe02JgBiY2RXJPXQL%2Fwelding-p145-img03.jpg?alt=media)

1D positioning parameters

* Positioning start point 1: The point from which positioning begins. It is recommended to first determine the positioning direction, then set the start point in the opposite direction, at a certain distance from the workpiece edge.
* Positioning direction: The motion direction during positioning. The reference coordinate system is the user coordinate system.
* Transition point: 0 to 5 transition points can be added for each positioning start point to avoid obstacles. 2D positioning parameters

![Official manual figure, page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fcy792muhft0UNTdKyFuA%2Fwelding-p146-img05.png?alt=media)

* Positioning start point 1/2: The point where positioning begins. It is recommended to first determine the positioning direction, then set the start point in the opposite direction, at a certain distance from the workpiece edge.
* Positioning direction: The motion direction during positioning. The reference coordinate system is the user coordinate system. The two positioning directions must be perpendicular to each other (e.g. X + and Y +).
* Incremental positioning: When this option is selected, the Positioning start point

(hereinafter referred to as "Point") 2 will be offset based on the positioning result of Point 1. For example, point 1 (P1) is offset in the X+ direction, and incremental positioning is enabled for point 2 (P2). During operation, P2 will be offset to P2i in the X+ direction based on the positioning result of P1, as shown in the figure below.

* Transition point: 0 to 5 transition points can be added for each positioning start point to avoid obstacles. 3D positioning parameters

![Official manual figure, page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIKhaUUn2yXq387u1Agka%2Fwelding-p147-img02.jpg?alt=media)

![Official manual figure, page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMqg7s9hTqGSd5mv1EmT8%2Fwelding-p147-img04.png?alt=media)

* Positioning start point 1/2/3: The point where positioning begins. It is recommended to first determine the positioning direction, then set the start point in the opposite direction, at a certain distance from the workpiece edge.
* Positioning direction: The motion direction during positioning. The reference coordinate system is the user coordinate system. The three locating directions must be perpendicular to each other (e.g. X +, Y + and Z +).
* Incremental positioning: When this option is selected, the corresponding positioning start point (hereinafter referred to as "Point") will be offset based on the positioning result of the previous point. For example, point 1 (P1) is offset in the X+ direction, point 2 (P2) is offset in the Y+ direction (with incremental positioning enabled), and point 3 (P3) is offset in the Z+ direction (with incremental positioning enabled). During operation, P2 will be offset to P2i in the X + direction according to the positioning results of P1, and P3 will be offset to P3i according to the positioning results of P1 and P2, as shown in the following figure.
* Transition point: 0 to 5 transition points can be added for each positioning start point to avoid obstacles. 2D + positioning parameters

![Official manual figure, page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6YDTLDIQGN2YQwaf2KKv%2Fwelding-p148-img02.jpg?alt=media)

![Official manual figure, page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fk7GXhSa5vNAfcricQ0cR%2Fwelding-p148-img04.png?alt=media)

* Positioning start point 1/2/3: The point where positioning begins. It is recommended to first determine the positioning direction, then set the start point in the opposite direction, at a certain distance from the workpiece edge. Positioning start points (hereinafter referred to as points) 1 and 2 correspond to the same right-angled edge of the workpiece, and point 3 corresponds to adjacent right-angled edges.
* Positioning direction: The motion direction during positioning. The reference coordinate system is the user coordinate system. The two positioning directions must be perpendicular to each other (e.g. X + and Y +).
* Incremental positioning: When this option is selected, the corresponding point will be offset based on the positioning result of the previous point. The logic is as follows: 1) First, perform positioning at points 1 and 2 to calculate the linear offset value. 2) If "Incremental positioning" for Point 3 is selected, it will be offset based on the calculation result. Positioning is then performed for the offset Point 3.
* Transition point: 0 to 5 transition points can be added for each positioning start point to avoid obstacles. 3D + positioning parameters

![Official manual figure, page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAh9jZdV9M3jxhlLOpRiR%2Fwelding-p149-img03.png?alt=media)

![Official manual figure, page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQRUPHOo2BNIBGmeux6Qe%2Fwelding-p149-img04.png?alt=media)

* Positioning start point 1 / 2 / 3 / 4 / 5 / 6: The point at which positioning begins. It is recommended to first determine the positioning direction, then set the start point in the opposite direction, at a certain distance from the workpiece edge. Positioning start points (referred to as points below) 1, 2, and 3 correspond to the same plane of the workpiece. Points 4, 5, and 6 are configured in the same way as 2D+Positioning. Refer to the diagram above for the specific positional relationship.
* Positioning direction: The motion direction during positioning. The reference coordinate system is the user coordinate system. The three locating directions must be perpendicular to each other (e.g. X +, Y + and Z +).
* Incremental positioning: When this option is selected, the corresponding point will be offset based on the positioning result of the previous point. The logic is as follows: 1) First, perform positioning at points 1, 2, and 3 to calculate the plane offset value. 2) Based on the calculation results, offset points 4 and 5, then perform positioning at the offset points 4 and 5 to calculate the linear offset value. 3) Offset point 6 based on the offset values calculated from the previous two sets of points, then perform positioning at the offset point 6.
* Transition point: 0 to 5 transition points can be added for each positioning start point to avoid obstacles. Inner and outer diameter positioning parameters

![Official manual figure, page 150](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3gGOm6baRIrVEtgUo0kd%2Fwelding-p150-img04.png?alt=media)

* Positioning start point 1/2/3: The point where positioning begins. It is recommended to first determine the positioning direction, then set the start point in the opposite direction, at a certain distance from the workpiece edge.
* Positioning direction: The motion direction during positioning. The reference coordinate system is the user coordinate system. The three points to be positioned should be located on the inner or outer diameter of the arc of the workpiece.
* Transition point: 0 to 5 transition points can be added for each positioning start point to avoid obstacles. 2. Description: Add the saved offset value onto the subsequent robot motion trajectory (only linear, arc, and circle motion commands are supported). Calling this block repeatedly before calling the block will update the compensated offset value. Parameter: The saved index of the offset value. 3. Description: Stop adding the trajectory offset values.

#### 10.3.2 Block DEMO

Here's a typical DEMO for the touch positioning function.

1. Place the workpiece in the standard position.
2. Create the following blockly project to get the datum point.
3. Run the project.
4. After the project completes, create a new project or modify the existing one for actual

![Official manual figure, page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoVJuohftuMuKp5TKKImi%2Fwelding-p151-img05.jpg?alt=media)

welding. a) The configuration of the touch positioning block is basically the same as the configuration for getting the datum point. Just unselect "Update the datum point". b) Write a welding program and add a "Positioning compensation start" block before moving to the arc start point. The welding parameters used in the DEMO are those finally saved on the Welding parameter configuration page. c) Add a "Positioning compensation end" block after the arc end. Positioning point configuration:

* 1D

Take the workpiece will only offset along the X+ direction of the user coordinate system as an example. In the figure below, the dashed lines indicate the reference position of the workpiece, while the solid lines indicate the position of the workpiece after offset.

![Official manual figure, page 152](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FriSjo18k8yBwdFAOJe3j%2Fwelding-p152-img02.png?alt=media)

* 3D

Take the workpiece will only offset in three directions along the user coordinate system as an example. In the figure below, the dashed lines indicate the reference position of the workpiece, while the solid lines indicate the position of the workpiece after offset.

* 3D+

Take the workpiece will offset and rotate in space as an example. First, perform positioning at the first three points to define a plane and determine the Z-axis offset and rotation of the workpiece. Then, use the remaining three positioning points to determine the workpiece’s X- and Y-axis offsets. In the figure below, the dashed lines indicate the reference position of the workpiece, while the solid lines indicate the position of the workpiece after offset.

![Official manual figure, page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHJNJMu30KemN2lzSZcdD%2Fwelding-p153-img03.png?alt=media)

![Official manual figure, page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fqs8Rgp8hCucY7faXWAZG%2Fwelding-p153-img04.png?alt=media)

![Official manual figure, page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fk178Sg6yooif0ooVtjPj%2Fwelding-p154-img03.png?alt=media)

![Official manual figure, page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRkSEkhMm5TfL9aBZUIAp%2Fwelding-p154-img04.png?alt=media)

## 11. Multi-layer Multi-pass Welding

### 11.1 Introduction

In welding applications, multiple layers of welding may be required for the same area, with successive weld beads overlapping each other. With the multi-layer and multi-pass welding function, users only need to teach the first weld pass and then set the offset values for each subsequent pass relative to the first one, significantly reducing teaching time. To use this function, after completing the multi-layer and multi-pass welding configuration, you need to write the welding program using either blockly programming or script programming.

### 11.2 Multi-layer multi-pass welding configuration

Configure the offset parameters for the weld passes on the "Multi-layer multi-pass welding configuration" page of the welding plugin. Click the "Channel" drop-down menu to select a channel index. Click to add a channel. Click to delete a channel. Click "Modify" to configure the channel parameters. Before proceeding, define the first weld pass and then follow the steps below to configure the channel parameters.

1. Define the user coordinate system ( Plane). This coordinate system serves as the

reference for calculating weld pass offsets. The positive X-axis indicates the robot's forward movement during welding, t⑦he positive Z-axis is defined based on the given user coordinate system (specified via the Plane parameter), and the Y-axis is determined by the right-hand rule.

![Official manual figure, page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2bWTo5hBP3KHl8Id3YWI%2Fwelding-p155-img02.jpg?alt=media)

![Official manual figure, page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F17qKwpkHsyD1Ek9va50e%2Fwelding-p155-img03.png?alt=media)

* If the weld pass is parallel to the robot's mounting surface, set Plane to 0 (base coordinate system).
* If the weld pass is not parallel to the robot's mounting surface, create a user coordinate system where the Z-axis is perpendicular to the plane of the weld pass, and set Plane to the index of this coordinate system.

2. Define the second weld pass and calculate its offset relative to the first weld pass. Fill

in the following parameters: ① StartX: The offset distance of the start point along the X-axis of the taught weld pass. Unit: mm. Range: -200–200 ② Y: The offset distance of the trajectory along the Y-axis of the taught weld pass. Unit: mm. Range: -200–200 ③ Z: The offset distance of the trajectory along the Z-axis of the taught weld pass. Unit: mm. Range: -200–200 ④ WorkAngle: The rotation angle of the welding torch around the X-axis of the user coordinate system ( Plane) relative to the taught posture. A positive value indicates a clockwise rotation about the positive direction of the X-axis. Unit: °. Range: -90–90 ⑦ ⑤ TravelAngle: The rotation angle of the welding torch around the Y-axis of the user coordinate system ( Plane) relative to the taught posture. A positive value indicates a clockwise rotation around the positive direction of the Y-axis. Unit: °. Range: -90–90 ⑦ ⑥ EndX: The offset distance of the end point along the X-axis of the taught weld pass. Unit: mm. Range: -200–200

3. Set an "Alias" to this channel (optional), then click "Save" on the upper-right corner of

the page.

4. Click on the right of the "Channel" to add a new channel. Then refer to the

steps above to configure the parameters for the third weld pass.

5. Repeat the steps above until all weld pass parameters are configured.

**NOTE**

The first weld pass (the one taught by the user) must remain on the same plane. Ensure that the Plane parameter is configured correctly as described above; otherwise, offset anomalies may occur in subsequent weld passes. Click Preview to view all configured channels in a table format and configure channel combination indices.

### 11.3 Channel combination index configuration

On the Preview interface, click Modify to edit channel parameters, or add or delete channel combination indices.

* Directly double-click the channel "Alias, StartX, Y, Z, WorkAngle, TravelAngle, EndX" to modify it. See Multi-layer Multi-pass Welding Configuration for the description of each parameter.
* Check "Dwell Time" to set the pause time for the current weld pass. The pause time applies to the following scenarios: When the number of welded layers increases, the program pauses to allow the  workpiece to cool down before resuming welding. Reduce heat input at the starting position of multi-layer multi-pass welding. 
* Click the "Plane" drop-down box to select the user coordinate system.
* Click the “Channel combination index” drop-down box to select the channel combination index (you need to add a new channel combination index before you can select it for the first time you use it).  Click to add channel combination index.  Click to delete channel combination index.  Click Edit to modify the currently selected channel combination index.

![Official manual figure, page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIjlV1RRFcUufl1gbioTo%2Fwelding-p157-img02.png?alt=media)

![Official manual figure, page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw6PKVtsDLR8Du0hQVmT9%2Fwelding-p157-img03.png?alt=media)

The procedure for adding a channel combination index is as follows:

1. Click to open the “Channel combination index configuration” page as shown

below.

2. Click the Pass 1 dropdown to select a channel number (the channel numbers

displayed here are those shown on the Preview interface). Check “Adjust Welding Parameters” to modify the welding parameter number or Job number, online control parameter number (Kemppi only), weaving parameter number, and welding absolute speed (If this option is not checked, the parameters saved on the Welding parameter configuration page will be used).

3. Click to add Pass 2 and Pass 3, select the channel number, and adjust the

welding parameters.

![Official manual figure, page 158](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6HkS4K5tpM7uFygCUHUm%2Fwelding-p158-img02.png?alt=media)

![Official manual figure, page 158](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAwLxnvWvnXu8HG46TUwH%2Fwelding-p158-img04.jpg?alt=media)

4. After configuring all passes sequentially, click "Save" to return to the "Preview"

interface. The sequence of channel combinations for channel combination index 1 is displayed above the table (as shown in the figure below: 1 → 2 → 3).

5. Click Save in the upper-right corner of the Preview interface to complete the

configuration of channel combination index 1.

6. Follow the above procedure to continue adding channel combination index 2, or return

to the Multi-Layer Multi-Pass Welding Configuration page.

7. When calling the Channel combination index block

in a welding project, you can select a configured channel combination index number.

![Official manual figure, page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKQAl5CODGrzP6tmKFkY5%2Fwelding-p159-img02.png?alt=media)

![Official manual figure, page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIKGv3XTT9DAXDdS039WX%2Fwelding-p159-img03.jpg?alt=media)

![Official manual figure, page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU4g1u6GYmXlgc9beyPNe%2Fwelding-p159-img04.jpg?alt=media)

![Official manual figure, page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUJLHSG3bzCzau7UFfEfr%2Fwelding-p159-img05.jpg?alt=media)

### 11.4 Multi-layer multi-pass welding programming

This section introduces the blocks/commands related to multi-layer multi-pass welding and the corresponding DEMO.

* Please refer to the Block Description and Block DEMO in this chapter when using blockly programming.
* When using script programming, refer to Script command description and Script

DEMO in Appendix A.7.

#### 11.4.1 Blockly description

1. Description: Starts multi-layer multi-pass welding. The target point of the motion block between this block and will be offset according to the parameters of the specified channel. Parameter: The channel number set in Multi-Layer multi-pass welding configuration. 2. Description: Ends multi-layer multi-pass welding. 3. Description: Used for multi-layer multi-pass welding applications. Performs multi-layer multi-pass welding on the taught welding trajectory based on the set index parameter (channel combination index). Parameter: 1) Enter the channel combination index set in Channel combination index configuration. 2) Select the approach point. 3) Select the departure point.

#### 11.4.2 Block DEMO

This DEMO uses a three-layer linear-to-arc welding as an example.

Create a project and teach the following points in the Points page:

* P1: Safety point before starting the welding.
* P2: Arc start point for the initial weld pass.
* P3: Straight section end point of the initial weld seam
* P4: Arc intermediate point of the initial weld seam
* P5: Arc end point of the initial weld seam (arc end point)
* P6: Safety point after ending the welding.

Then, in Multi-Layer multi-pass welding configuration, configure the channels for the second and third passes, with indices 1 and 2 respectively. The following figure shows a simple configuration example. The block DEMO is as follows. The welding parameters used in the DEMO are those finally saved on the Welding parameter configuration page.

![Official manual figure, page 161](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjRJEyDf0ZnxLYuSCZTxK%2Fwelding-p161-img02.jpg?alt=media)

![Official manual figure, page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW42ZnLWJDaAGfn0ALSvD%2Fwelding-p162-img02.jpg?alt=media)

**NOTICE**

If the welding parameters are set in the multi-layer multi-pass welding channel combination index, see the description of Channel combination index configuration for details; Then, when creating the blockly project, it is necessary to place the welding parameter/weaving parameter/welding speed blocks outside the multi-layer and multi-pass welding channel combination index block. If placed inside, the welding parameters set in the multi-layer multi-pass welding channel combination index will be overwritten and will not take effect.

![Official manual figure, page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIfT9YO4ZgVK0LLQUDLZx%2Fwelding-p163-img02.jpg?alt=media)

## 12. Through-Arc Seam Tracking (TAST)

### 12.1 Introduction

The Through-Arc Seam Tracking (TAST) function achieves accurate seam tracking by maintaining a stable current between the welding wire and the workpiece. It is commonly applied in welding scenarios involving thick plates and long straight welds. The TAST function allows compensation in both vertical and horizontal directions. Horizontal compensation must be used in conjunction with a Weaving process. Vertical compensation: When the height between the welding wire and the workpiece changes, the current fluctuates. The robot continuously monitors the welding current and adjusts its vertical motion to keep the current near the set reference value, ensuring the proper distance between the wire and the workpiece. Horizontal compensation: During the weaving process, the robot collects current data from both sides of the weld. If it detects an asymmetry in the current, it adjusts its horizontal position to make the current values symmetrical, ensuring the welding line stays centered in the groove.

**NOTE**

The TAST function only supports linear and arc motion, with weaving methods such as Zigzag or Sine weaving. Currently, TAST function is supported only on Fronius, Kemppi, EWM, GYS, Megmeet, and Aotai welders. Recommended conditions for using TAST:

* Workpiece thickness: ≥ 3mm (without weaving); ≥ 8mm (with weaving).
* Weaving technique: Use Zigzag or Sine weaving.
* Groove angle: Recommended to be set at 90° to ensure consistency.
* Weaving frequency: 1.5 Hz – 2.5 Hz
* Weaving amplitude: ≥ 2mm.
* Gas: MAG.
* Wire diameter: ≥1.0mm
* Stick-out length: 15mm – 25mm
* Welding conditions: When weaving is not used, there are no strict current requirements; ensure a stable welding process. When weaving is used, a current of 240 A (DC) or higher is recommended. When using pulsed welding, the full current range is applicable.
* Welding joint types: T-joint fillet, V-groove butt joint

![Official manual figure, page 164](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDAFyKULx2xieOmz1uSYH%2Fwelding-p164-img02.png?alt=media)

* Arc start position: At the start of welding, the welding wire should be positioned at the center of the seam, with equal distance between the wire and both sides of the seam. It is recommended to use the Touch positioning function to locate the arc start point.
* Teaching angle deviation: The deviation of the welding torch angle in the Z-direction relative to the center of the weld seam should be less than 10°.
* Base material and welding wire requirements: Applicable for common materials such as carbon steel, stainless steel, and steel alloys.

### 12.2 TAST configuration

Please open the welding plug-in, select the welder, enter the Arc sensor configuration page, configure the TAST parameters and view the real-time data. Parameter Description TAST param No. The index of the current TAST parameter group, used in programming to reference the corresponding parameter group. Alias The alias of the current TAST parameter group. It's recommended to set an easy to remember name. Delay time Set the delay for current. Unit: ms, Range: \[0, 100]. The default delay time for current is 38 ms.

![Official manual figure, page 165](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp9OejLJmeQdJQaCMDeNc%2Fwelding-p165-img02.jpg?alt=media)

Parameter Description Current collection mode Current acquisition method for the current TAST parameter set.

* Welder feedback (default): Actively acquires current via protocol.
* Hall sensor: Acquires current via an external sensor.

For detailed instructions on using the Hall sensor, refer to the DOBOT TAST User Guide.

#### 12.2.1 Vertical tracking parameters

Parameter Description Compensation switch Turn the vertical compensation function on or off. Compensation coordinates When weaving is not used, a reference coordinate (for non-weaving) system for vertical compensation must be specified. You can specify a user coordinate system, tool coordinate system, or weld seam coordinate system. The effective coordinate system is the global coordinate system used when the welding project is running (the default for both is coordinate system 0, which can be modified using the Set User Coordinate System and Set Tool Coordinate System blocks/script commands). When weaving is used, the system uses the weaving trajectory as a reference. The X-axis positive direction corresponds to the welding forward direction, and the Z- axis is perpendicular to the weaving plane and points upward. Reference setting Select the method to obtain the reference current for vertical compensation.

* Feedback: Use the current feedback value sampled at the start of welding as the reference value (see related sampling parameters below).
* Constant: Use a fixed value set by the user as the reference value. Reference setting value When reference setting is set to constant, the system uses the value set here as the reference value. Reference feedback value When reference setting is set to feedback, set this parameter as the coefficient for the algorithm's sampled feedback value. The default is 0. After running the project, click Refresh to get it.

Parameter Description Sampling time (for non- Set the time for one data sampling period without weaving) weaving. Range: (0, 10 000]. When weaving is used, the sampling period is the same as the weaving period. The gain coefficient for vertical compensation. Increasing this value will cause the same feedback Sensitivity current to correspond to a larger compensation amount, and vice versa. Range: \[0, 999]. Adaptive gain The adaptive gain for vertical compensation. This parameter adjusts the correction amount based on the trend of error changes: increases correction when error changes rise and reduces correction when error changes decrease. If the value is too high, it may cause oscillation in the weld seam. The initial value can be set to 10% of the gain coefficient (i.e., sensitivity) for vertical compensation. Value range: \[0, 1000]. Compensation offset The system calculates the compensation amount based on the feedback current and applies a proportional offset. It is used in scenarios where the compensation needs to be consistently increased or decreased slightly. Positive values correspond to upward compensation (away from the workpiece), while negative values correspond to downward compensation (toward the workpiece). Range: \[-100, 100]. Minimum compensation per The minimum compensation amount applied per cycle sampling cycle. If the calculated compensation amount is less than this value, the system will not apply compensation. It is generally used to filter out noise. Range: \[0, 999]. Maximum compensation per The maximum compensation amount applied per cycle sampling cycle. If the calculated compensation amount is greater than this value, the system will only apply compensation to this value. Range: \[0, 9999]. Maximum cumulative The maximum cumulative vertical compensation. If the compensation cumulative compensation exceeds this value, the robot will stop compensating and continue welding. Range: \[0, 9999]. Compensation start count The cycle count at which vertical compensation starts. This value must be greater than or equal to (Feedback reference current sampling start count + Feedback reference current sampling count).

Parameter Description Feedback reference current When the reference current is set to "Feedback", this sampling start count defines the cycle count at which the system starts sampling, avoiding unstable current values at the start of welding from being used as the reference. For example, if this value is set to 4, the system will begin sampling feedback current from the 4th sampling cycle. Feedback reference current When the reference current is set to "Feedback", this sampling count defines the number of cycles for sampling. For example, if this value is set to 2, the system will use the average value from two sampling cycles as the reference current.

#### 12.2.2 Horizontal tracking parameter

Parameter Description Compensation switch Turn the horizontal compensation function on or off. Reference setting Select the method for obtaining the reference current for horizontal compensation.

* Feedback: Use the current feedback value sampled at the start of welding as the reference value (see related sampling parameters below).
* Constant: Use a fixed value set by the user as the reference value. Reference setting value When reference setting is set to constant, the system uses the value set here as the reference value. Reference feedback value When reference setting is set to feedback, set this parameter as the coefficient for the algorithm's sampled feedback value. The default is 0. After running the project, click Refresh to get it. The gain coefficient for horizontal compensation. Increasing this value will cause the same feedback Sensitivity current to correspond to a larger compensation amount, and vice versa. Range: \[0, 999]. The adaptive gain for horizontal compensation. This parameter adjusts the correction amount based on the trend of error changes: increases correction when error changes rise and reduces correction when error changes Adaptive gain decrease. Setting this value excessively high may result in weld track oscillation. The initial value can be set to 10% of the gain coefficient (sensitivity) for horizontal compensation. Range: \[0, 1000].

Parameter Description The system calculates the compensation amount based on the feedback current and applies a proportional offset. It is used in scenarios where the compensation needs to be consistently increased or decreased slightly. When set Compensation offset to a positive value, compensation is applied to the right in the forward direction. When set to a negative value, compensation is applied to the left in the forward direction. Range: \[-100, 100]. The minimum compensation amount applied per sampling cycle for horizontal motion. If the calculated Minimum compensation per compensation amount is less than this value, the system cycle will not apply compensation. It is generally used to filter out noise. Range: \[0, 999]. The maximum compensation amount applied per sampling cycle for horizontal motion. If the calculated Maximum compensation compensation amount is greater than this value, the per cycle system will only apply compensation to this value. Range: \[0, 9999]. Maximum cumulative compensation for horizontal Maximum cumulative motion. If the cumulative compensation exceeds this compensation value, the robot will stop compensating and continue welding. Range: \[0, 9999]. The cycle count at which horizontal compensation starts. This value must be greater than or equal to (Feedback Compensation start count reference current sampling start count + Feedback reference current sampling count). When the reference current is set to "Feedback", this defines the cycle count at which the system starts Feedback reference current sampling, avoiding unstable current values at the start of sampling start count welding from being used as the reference. For example, if this value is set to 4, the system will begin sampling feedback current from the 4th sampling cycle. When the reference current is set to "Feedback", this Feedback reference current defines the number of cycles for sampling. For example, sampling count if this value is set to 2, the system will use the average value from two sampling cycles as the reference current.

#### 12.2.3 Real-time data

Kemppi welder: Displays the current value and tracking correction amount for each cycle. Other welders: Displays the current value and tracking correction amount for each cycle. Click "Real-time Data" to enter the TAST real-time graph interface, click "Refresh" to refresh the real-time data, and drag the time length control below to set the time length of the graph.

### 12.3 TAST programming

#### 12.3.1 Blockly description

1. Description: Start through\_arc seam tracking. Repeated calling of this block is not allowed before calling. After starting tracking, the robot's trajectory (supports only linear and arc motion) will automatically be adjusted based on the tracking results. Parameter: TAST parameter index. 2. Description: End through\_arc seam tracking.

![Official manual figure, page 170](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKsTWJeBvhOf3mX4vo3RR%2Fwelding-p170-img02.png?alt=media)

#### 12.3.2 Block DEMO

### 12.4 Precautions

#### 12.4.1 Prerequisites

* The workpiece should be accurately calibrated using the six-point teaching method

(TCP+ZX).

* Hardware devices for "Gas feed" and "Wire feed" should remain stable.
* The welding torch should be positioned near the centerline of the weld seam and not too close to the workpiece. The stick-out length of the welding wire should be approximately 15mm – 25mm; otherwise, the torch may easily collide with the workpiece during welding.

#### 12.4.2 Parameter recommendations

Parameter Recommended value The initial value can be set to 50. If there is an overall tilt in the weld seam, adjust the "Sensitivity" of both up-down tracking and left-right Sensitivity tracking by increments of "+10". If the weld seam is centered but shows oscillations, adjust by increments of "-5". Set to 10% of the "Sensitivity" value, and further Adaptive gain adjustments are not recommended. Compensation offset It is recommended to maintain consistent left-right offset amplitudes. If inconsistencies occur and

![Official manual figure, page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSuDwA8hJfVldGumQJ44e%2Fwelding-p172-img02.jpg?alt=media)

![Official manual figure, page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZfxyqilrNu4rM710o3WU%2Fwelding-p172-img03.jpg?alt=media)

Parameter Recommended value oscillations are observed under the current parameter settings, adjust the "Compensation offset". Adjustment method: First, determine whether the side with the larger amplitude is on the left or right in the forward direction. If it is on the left, set the "Compensation offset" to a negative value. If it is on the right, set it to a positive value. The adjustment incremented for the "Compensation offset" should not exceed 2. Compensation start count ≥ 7 (Compensation should only occur once the welding current stabilizes). Feedback reference current ≥ 4 sampling start count Feedback reference current ≥ 3 sampling count

### 12.5 Testing recommendations

The weld seam length used for testing should be ≥ 80mm. Additionally, ensure accurate current within the sampling range of the reference current. If significant offset occurs within this range, it will result in a large error in the reference current and the entire weld seam will be offset. For example: When teaching the start and end points, if an intermediate point is also taught, the intermediate point should fall directly on the weld seam, with the length between the start point and the Intermediate point being ≥ 30mm. The offset can be set to 10% of the remaining weld seam length.

![Official manual figure, page 173](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz0kfjxf1DpNOhIRaeRbD%2Fwelding-p173-img02.png?alt=media)

## 13. Fast Programming

### 13.1 Introduction

For DOBOT CRA / CRV series robot arms, we have developed a dedicated welding —the DOBOT Intelligent Welding Assistant. It features an integrated six-axis accessory force sensor and six physical buttons, and is quickly compatible with DOBOT CR5A / 10A / 20A / 6AL and CR5V / 10V / 20V models. When paired with the DOBOT Welding Process Package, this assistant enables compliant dragging and rapid point-saving functions. If you need to use the "Fast Programming" function, refer to the DOBOT Intelligent Welding Assistant User Guide to complete the hardware installation and sensor calibration before you can perform quick points saving in the welding plugin.

![Official manual figure, page 174](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F06GtHFIksw5N8haxszl4%2Fwelding-p174-img02.jpg?alt=media)

Once the sensor calibration is completed, compliant drag Six-axis force sensor can be achieved.

* Blue (Quick flash): The robot is starting up (flashing may be delayed on some models)
* Blue (Steady on): The robot is powered on but not enabled
* Green (Steady on): The robot is enabled but not running project
* Green (Slow flash):

Automatic running status (project  debugging/running/pause, motion commands except TCP jog mode, trajectory playback) Press the "Slow Drag" button on the intelligent  welding assistant

* Green (Quick flash):

Single running status (Jog / "RunTo" function in  software) / Trajectory recording status Light strip Press the "Fast Drag" button on the intelligent  welding assistant

* White (Flash once): Press the "Line/Circ" button or

"TAST" button on the intelligent welding assistant

* Red (Slow flash): Joint brake switched on in disabled status
* Red (Steady on): Robot error status (If the "Enable" button on the intelligent welding assistant is pressed at this time, the light strip will change from red to blue, then to green)
* Yellow (Steady on): Collision detected

**NOTE**

The quick flashing frequency is 5Hz (0.2s per cycle), and the slow flashing frequency is 1.25Hz (0.8s per cycle). Displays the arc switching status: the light (steady on) on Indicator indicates the arc is ON, while the light (turns off) indicates the arc is OFF. When pressed, all subsequent recorded points will be arc- start welding points (light steady on). Press again, and all Arc-ON/OFF subsequent recorded points will be non-arc-starting points (light turns off). Line Used to record linear points. Circ Used to record circular points.

Press to drag and release to stop. Suitable for quick and Drag-Fast wide-range robot dragging. Press to drag and release to stop. Suitable for precise point Drag-Slow adjustments. When an error occurs, pressing it will clear the error and Enable enable the robot.

### 13.2 Set a welding project

1. In the left navigation panel of the welding plugin, select "Fast programming" to

navigate to the Fast programming page.

2. Click the "Open" button to create a new project or open an existing one.
3. If you create a new project, the project name input box will pop up first. Enter the

project name and save it, and then directly enter the editing interface. A new project will have "Weld 1" added by default. You can delete it or modify its alias. Additionally, you can click "Add welds" to add new weld seams.

4. If you open an existing project, you need to click the "Modify" button to access the

project editing interface.

![Official manual figure, page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSRjatXoxQ7pHzWhhzWmN%2Fwelding-p176-img02.png?alt=media)

![Official manual figure, page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaVkdLHRzSuv7k40gAZzs%2Fwelding-p176-img03.jpg?alt=media)

![Official manual figure, page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgRT4Yl1HBQlhVHRNjecV%2Fwelding-p176-img04.png?alt=media)

5. Next, you can configure the welding process number for the current project and use

the intelligent welding assistant to quickly teach weld-seam points.

### 13.3 Configuring welding process

1. Click the "Setting" button next to the Welding process number to enter the welding

process configuration page.

2. When entering for the first time, a blank page will be displayed. Click + to create a new

welding process number.

3. In the new welding process file, double-click to enter the "Alias, Plate Thickness,

and Material". Then, use the dropdown menus to select “Welding Parameters, Multi- Layer Multi-Pass Combination Index, Intermittent Welding Index, and Weaving Index”.

![Official manual figure, page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJHgGHNIbYeK7wqCGUhaJ%2Fwelding-p177-img02.png?alt=media)

![Official manual figure, page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn1BkzazkatKlZwFPRpoe%2Fwelding-p177-img03.png?alt=media)

![Official manual figure, page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWJBezBYgXRxcl8wK4ljf%2Fwelding-p177-img04.png?alt=media)

**NOTE**

* After selecting a multi-layer multi-pass combination index or an intermittent welding index, the weld seam using this process file number will adopt the corresponding multi-layer multi-pass welding or intermittent welding method.
* When the multi-layer combined index or intermittent welding index is set to 0, it indicates that this function is disabled.
* The multi-layer multi-pass combination index and the intermittent welding index are mutually exclusive; only one parameter can be enabled (i.e., when one parameter is set to a non-zero value, the other is forced to 0).
* When the online control parameter number is 0, this function is turned off.
* For detailed instructions on configuring the multi-layer multi-pass combination index and the intermittent welding index, refer to Channel Combination Index Configuration and Intermittent Welding Configuration.

4. You can click the "+" button at the bottom of the page to add a new blank process file

number, or click to copy current process file number. Click to clear the settings of the current process file number (this will only clear the settings and will not delete the process file).

5. After configuring the process file, return to the "Fast programming" page and select

the welding process number.

### 13.4 Fast teaching points

![Official manual figure, page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEHqyBPrIr9bOjA2I2ElR%2Fwelding-p178-img02.png?alt=media)

![Official manual figure, page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7HrJvI5sSYkLp51O1WFQ%2Fwelding-p178-img05.png?alt=media)

The following takes the example of teaching a simple straight weld seam using the intelligent welding assistant for illustration: A. Saving approach point: Press the "Fast Drag" button on the intelligent welding assistant to drag the ① welding torch near Point A (approach point), then press the "Slow Drag" button to fine-tune the precise position of the torch. Press the "Line" button. The white light strip will flash once, and the current point ② will be automatically saved. At the same time, the "Fast programming" page pops up the P1 point information. Double-click the P1 alias to modify it to "Approach point". ③ B. Save arc start point: Use the "Fast Drag" and "Slow Drag" buttons on the intelligent welding ① assistant to drag the welding torch to Point B (Arc Start Point). Press the "Arc" switch on the intelligent welding assistant. The indicator light ② on the button will stay illuminated. Press the "Line" button. The white light strip will flash once, and the current ③ point will be automatically saved. At the same time, the "Fast programming" page pops up the P2 point information. Double-click the P2 alias to change it to “Arc start point” ④

![Official manual figure, page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0DrVT9FzgtAU2YVbdOoH%2Fwelding-p179-img02.jpg?alt=media)

![Official manual figure, page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3pCLKvj5ooRMBwDD0p4z%2Fwelding-p179-img03.png?alt=media)

C. Save intermediate point: Use the Fast Drag and Slow Drag buttons on the intelligent welding assistant to move the welding torch to point C (intermediate point). ① Press the "Line" button. The white light strip will flash once, and the current point will be automatically saved. At the same time, the "Fast programming" page pops ② up the P3 point information. Double-click the P3 alias to modify it to "Intermediate point". ③

**NOTE**

* If the intermediate point is circular, the "Circ" button on the intelligent welding assistant needs to be pressed twice.
* When pressing the "Circ" button at the first circular intermediate point, the

"Fast Programming" page only displays the message "Arc intermediate set. Press again to generate arc command", but no circular point is shown.

* When pressing the "Circ" button at the second circular intermediate point, the "Fast Programming" page displays information for two circular middle points. D. Save arc end point:

![Official manual figure, page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F09P5kyxl7DVVxdAN8Qc5%2Fwelding-p180-img02.png?alt=media)

![Official manual figure, page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9WCUtmL0u6wqOIrIA0jS%2Fwelding-p180-img03.png?alt=media)

![Official manual figure, page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKq4Rfq3slM4sKlRkfyG3%2Fwelding-p180-img05.png?alt=media)

Use the "Fast Drag" and "Slow Drag" buttons on the intelligent welding assistant to drag the welding torch to point D (Arc end point). ① Press the "Arc" button on the intelligent welding assistant. The indicator light on the button will turn off. ② Press the "Line" button. The white light strip will flash once, and the current point will be automatically saved. At the same time, the "Fast programming" page pops ③ up the P4 point information. Double-click the P4 alias to change it to "Arc end point". ④

**NOTICE**

Before pressing the "Line" button to save the "Arc end point", ensure the "Arc" switch is turned off. E. Save departure point: Use the "Fast Drag" and "Slow Drag" buttons on the intelligent welding assistant ① to drag the welding torch to point E (Departure point). Press the "Line" button. The white light strip will flash once, and the current point ② will be automatically saved. Simultaneously, the "Fast Programming" page will display the information for Point P5. Double-click the P5 alias to modify it to "Departure point". ③

![Official manual figure, page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaYCoOlIpn2WMEnHy5mEH%2Fwelding-p181-img02.png?alt=media)

![Official manual figure, page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0raTLodMD6w11ucGKdAr%2Fwelding-p181-img03.png?alt=media)

At this point, the teaching of a simple linear weld seam is complete. You can adjust points based on actual requirements or click "Add welds" to create a new weld seam and teach points for the new seam. In addition to using the "Fast Programming" page, you can also complete rapid point teaching through the "Welding Programming > Blockly programming" page. On the "Welding Programming > Blockly programming" page, after dragging the welding torch to the target position, press the "Line" or "Arc" key on the intelligent welding assistant will automatically generate a corresponding block command in the programming area. Meanwhile, the current point information will be automatically saved in Points page.

**NOTE**

The block building described above is merely a demonstration of how the intelligent welding assistant can be used for quick point saving. For an actual demo, additional blocks should be incorporated based on the specific application scenario.

### 13.5 Adjusting points

* Click to delete the current point;
* Long-press the button to move the welding torch to the specified point;

![Official manual figure, page 182](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7QqFvoTDwbiuv5MWInlN%2Fwelding-p182-img02.png?alt=media)

release to stop the motion. After adjusting the welding torch position, click to update the point;

* Click / to toggle the arc status for the current point.
* Click next to the “Approach point” or “Departure point” to switch the motion mode to either linear motion or joint motion when moving to the "Approach point" or "Departure point".

**NOTE**

The motion mode can only be adjusted for the "Approach point" and "Departure point".

* After configuring the weld seam point, click the “Save” button next to the project name. Once the project is saved, the "Add welds" option and the point list will be grayed out and become non-editable.

### 13.6 Running the project

1. Click on the top navigation bar in the control software to enter the welding

plugin panel, then check the "Virtual welding" option.

![Official manual figure, page 183](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsYjcJFHGVu2oT86l4rnw%2Fwelding-p183-img06.png?alt=media)

![Official manual figure, page 183](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAx153OZauIzIPZ0UHomC%2Fwelding-p183-img07.jpg?alt=media)

2. Enter the "Fast Programming" page of the welding plugin and click

to run current project. The log bar at the bottom of the page will display detailed runtime information. If an error occurs, the project will automatically stop running.

![Official manual figure, page 184](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPCPjHmem8yTADifBf13y%2Fwelding-p184-img02.jpg?alt=media)

![Official manual figure, page 184](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F37nGriql9kfZMQ1xKfPm%2Fwelding-p184-img04.png?alt=media)

## 14. Welding Control Box

The CRA/CRV series welding process package is equipped with a welding control box, providing users with a convenient control method for welding operations. It supports various mode switching, welding parameter adjustment, and troubleshooting.

### 14.1 Hardware wiring

After unpacking the welding control box, you need to connect the power cable from the welding control box to the robot controller. The pin definitions of the control box and corresponding robot controller interfaces are detailed in the table below: Control box pin Controller interface Pin definition Color 485+ Green 485 A 485-04/12 Blue 485B E-Stop A Yellow-Green SI 24V E-Stop B White SI 1 +24 V Red I/O 24V GND Black I/O 0V

![Official manual figure, page 185](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNzttQjFkQeUEk4HbzgkN%2Fwelding-p185-img02.jpg?alt=media)

![Official manual figure, page 186](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkYPQyUa01oQyP3MI0j8w%2Fwelding-p186-img02.png?alt=media)

### 14.2 Control box panel

The appearance of the welding control box is illustrated below:

#### 14.2.1 Emergency stop button

Function: Used to immediately halt all welding operations to ensure safety. Usage: Press the emergency stop button when the system alarms or in case of an emergency, and the robot arm will stop moving immediately. After resolving the problem, turn the emergency stop button clockwise to release it, then press the "Clear" button to return to normal working mode. Troubleshooting: After pressing the emergency stop button, perform fault handling based on the alarm code displayed on the digital tube (e.g., ALARM or ERR).

#### 14.2.2 Mode knob

Mode Operation method Default mode. Turn the "Mode" knob to adjust the parameter value in normal mode. Normal mode Press and hold the Mode knob for 5 seconds to clear the project (after clearing is complete, the digital tube displays 0100). Short-press the "Mode" knob to enter extended-function Extended-function mode mode, and short-press again to exit this mode.

![Official manual figure, page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FY9Bh3yt3mpQSxVKrLGLD%2Fwelding-p187-img02.jpg?alt=media)

Mode Operation method In the extended-function mode, short-press the F1 button for mode switching and turn the "Mode" knob to adjust the parameter value.

**NOTE: For a description of extended function mode,**

refer to the Digital tube display section.

#### 14.2.3 Digital tube display

The letters/numbers represented by the symbols displayed on the digital tube are shown in the figure below: "Normal mode" and "Extended-function mode" status description: Digital tube 1st digit 2nd digit 3rd digit 4th digit Mode Welding parameter 1 Weaving parameter 0 99, set Normal mode – – 99, set using the knob using the knob Extended-function mode Set the global jog speed ratio (1 100), using the J – Jog speed setting knob (J) 1: Joint Extended-function 2: Cartesian (default) mode J o G 3: Tool. Jog type settings The default is 2, set (JoG) using the knob, and the last value set is

![Official manual figure, page 188](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbLgykYmeXVy42LzoXfFZ%2Fwelding-p188-img02.png?alt=media)

Digital tube 1st digit 2nd digit 3rd digit 4th digit Mode retained after a restart. Extended-function mode Set the absolute speed during welding (1 20 S – Welding absolute mm/s), using the knob speed (S) Extended-function mode Set the global speed ratio for script execution (1 G – Script speed 100), using the knob. setting (G) Extended-function mode d b G Null Debugging (dbG) Extended-function mode S P o t Spot welding (Spot) Extended-function Channel combination index number mode 0 99, set using the knob. 0 indicates M Null – Multi-pass setting that multi-layer multi-pass welding is (M) disabled. Extended-function Intermittent welding mode index 0 – 9, default is I n t 0. Intermittent welding (Int) Set using the knob. Extended-function mode Seam index Point index L Arc index 1/2 Trajectory change 1 – 9 1 – 9 (L) Other status description: Digital tube 1st digit 2nd digit 3rd digit 4th digit Mode Alarm status A L A M Script error E R R Null Clear project 0 1 0 0

**NOTE**

* When the digital tube displays ALAM, it indicates a system alarm.
* When the digital tube displays ERR, it indicates a script error.
* When the digital tube displays 0100, it indicates that the project has been cleared.
* Short press the Mode knob to enter extended function mode. Short press the Mode knob again to exit extended function mode, and the digital tube will return to normal mode display.

#### 14.2.4 Status indicators

Indicator (Run/Pause) indicator (Stop) indicator Project status Run ON OFF Pause Alternating flashing Alternating flashing Stop OFF ON

#### 14.2.5 Joystick function

The "Joystick / F3" button allows toggling between XYZ and RxRyRz jog control.

* When the "Joystick / F3" button's indicator is OFF, the joystick can be used for jog control in the XYZ directions.  Left/Right: X-axis direction.  Up/Down: Y-axis direction.  Joystick rotation: Z-axis direction.
* Press the "Joystick / F3" button (light on) for jog control in the RxRyRz directions.

 Left/Right: Rx-axis direction.  Up/Down: Ry-axis direction.  Joystick rotation: Rz-axis direction.

#### 14.2.6 Button functions

Button description Button name Function description Press to initiate virtual welding (dry run) to observe the Simulate robot's welding trajectory. Press again to pause the simulation. Press to stop the robot's current operation or teaching Stop process. Press to start real welding, press again to pause Weld welding. Key welding point buttons. When the button light is on, the system enters the Approach point corresponding welding point teaching mode. Use the joystick to move the robot to the target position, then Arc start point press the button to save the current point (the button Arc end point light will turn off, and the light for the next point will illuminate). Follow the sequence to save the positions Departure point for "Approach point, Arc start point, Arc end point, Intermediate·Line Intermediate point (Linear), Intermediate point (Arc), and Departure point" in order. Refer to the operation Intermediate·Arc logic and teaching flow outlined in the Operational Logic Between Key Welding Points, Teaching Point sections. Control enabling/disabling of the robot. Normal When the Enable button's light is on, mode the robot is enabled. When the Disable button's light is off, the robot is disabled. Enable / Retract Short press the Mode knob to enter Extended- extended function mode, then press F1 function to switch to debug mode (the digital

![Official manual figure, page 191](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBBYFkq3tLvtzumQ47FSf%2Fwelding-p191-img02.jpg?alt=media)

Button name Function description mode (dbG) tube displays dbG), and finally press this button to retract the wire. Press this button to clear alarms:

1. When an alarm occurs, the light turns

Normal on and the digital tube displays ALAM. mode

2. When no alarm is present, the light

turns off and the digital tube returns to Clear / Feed its previous value. In extended function mode, press F1 to Extended- switch to debug mode (the digital tube function displays dbG), then press this button to mode (dbG) feed the wire. In the robot-enabled status, press this Normal button to enter the drag mode. Press mode this button again to exit the drag mode. Drag / Gas In extended-function mode, press F1 to Extended- switch to debug mode (digital display function shows "dbG") and press this button to mode (dbG) perform Gas detection switch. Press this button to enter the welding parameter settings. Adjust welding parameters using the "Mode" knob. This button and F2 are mutually exclusive. When this button's light is on, it is not Normal possible to configure the weaving mode parameters. Note: To configure the welding parameters, you must first press the "Approach" button to save the approach point (at this time, the "Approach" Welding parameter / F1 button's light will turn off). First press the Mode knob to enter extended function mode, then press F1 to cycle through the modes. The digital tube will cycle through the following Extended- displays: J → JoG → S → G → dbG function mode → Spot → M → Int → L → J...

**NOTE: For the extended function**

modes represented by each letter, refer to Digital tube display. Press this button to enter the weaving Normal Weaving parameter / F2 parameter settings. Adjust weaving mode parameters using the "Mode" knob. This button and F1 are mutually exclusive.

Button name Function description When this button's light is on, it is not possible to configure the welding parameters. Note: To configure the weaving parameters, you must first press the "Approach" button to save the approach point (at this time, the "Approach" button's light will turn off). Extended- First press the Mode knob to enter function extended function mode, then press F1 mode to switch to spot welding (the digital Spot welding tube displays Spot), and finally press F2 (Spot) to trigger the spot welding operation. First press the Mode knob to enter extended function mode, then press F1 Extended- to switch to trajectory modification mode function (the digital tube displays L), and finally press F2 to cycle through the digital mode tube displays. For the meaning of Trajectory different digital tube displays in change (L) Trajectory Modification Mode, refer to Trajectory modification mode introduction.

1. Short press to switch between jog control in XYZ

and RxRyRz directions. For details, refer to Joystick function section. Joystick Switch / F3 2. While holding down F3, press the Teach Point button once to overwrite the original point. Release F3 to exit. For details, refer to F3 Key Point Modification. Operational Logic Between Key Welding Points Arc Intermediate Approach Intermediate Intermediate Arc end Departure Status start-Arc point-Line-Arc (First) point point point (Second) Approach point ○ ◉ ○ ○ ○ ○ ○ Arc start point ○ ○ ◉ ◉ ◉ ◉ ○ Intermediate - Line ○ ○ ◉ ◉ ◉ ◉ ○ Intermediate - Arc ○ ○ ○ ○ ◉ ○ ○ (First)

Arc Intermediate Approach Intermediate Intermediate Arc end Departure Status start-Arc point-Line-Arc (First) point point point (Second) Intermediate - Arc ○ ○ ◉ ◉ ◉ ◉ ○ (Second) Intermediate end point ○ ○ ○ ○ ○ ○ ◉ Departure point ◉ ○ ○ ○ ○ ○ ◉

**NOTE:**

## ◦

When the "Approach point" button is pressed, " " (indicator ON) indicates an active ◉ and operable state, while " " (indicator OFF) indicates an inactive and inoperable ○ state.

## ◦

After teaching the first point of the arc, you must proceed to teach the second point of the arc.

## ◦

Once the first departure point is successfully saved, the indicators for both "Departure point" and "Approach point" light up simultaneously. At this stage, the following options are available: Press the "Departure point" button to save another departure point. Press the "Approach point" button to teach the next weld-seam point. Press the "Stop" button to exit the point teaching process. Troubleshooting alarms

## ◦

When an alarm occurs, the light turns on and the digital tube displays ALAM. Press the Clear button to clear the alarm.

## ◦

If a script error occurs (e.g., welding index out of range), the digital tube displays ERR. After pressing the Clear button to clear the alarm, the digital tube returns to its previous value.

## ◦

When both ALAM and ERR appear, handle ALAM first.

### 14.3 Control box quick start

1. Create a new welding param No.: Open the welding plugin and go to the Welding

Parameters page to customize the welding parameter number. For welding parameter configuration for different welders, refer to Welding Parameter Configuration.

2. Enable the welding control box function:

On the "Control box configuration" page in the welding plugin, toggle the “Welding Control Box” switch to ON. ① The following prompt appears. Click Confirm to automatically enable I/O or Modbus control and create a new script project named "Arc\_Box\_Template". ②

![Official manual figure, page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKycxoXpst4XDfMbYLLak%2Fwelding-p195-img02.png?alt=media)

![Official manual figure, page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvlhE1naDRZWd1r1BqOsk%2Fwelding-p195-img03.png?alt=media)

![Official manual figure, page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaaVzTx33kuh1TKab4SeB%2Fwelding-p195-img04.png?alt=media)

**NOTE**

When using the welding control box, ensure that I/O or Modbus control remains enabled. If I/O or Modbus control is disabled due to other operations, you can toggle the I/O or Modbus configuration switch back to ON on the DobotStudio Pro home page. If the "Arc\_Box\_Template" project already exists, the following prompt box will appear: ③ Select "Overwrite" or "Don't Overwrite" an existing project to enter the following interface: ④

![Official manual figure, page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjqAgv3SyjbCYoSs0hz4u%2Fwelding-p196-img02.png?alt=media)

![Official manual figure, page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FssEMoGgsRN3twnEXJo2F%2Fwelding-p196-img04.png?alt=media)

3. Teach points using the control cox: Below is a sample workflow for teaching a

simple straight weld seam using the control box. Operation procedure System response / Button status Step 1 Long-press the "Mode" knob to The display tube shows 0100. - clear the project. The "Approach point" light turns ON. - Step 2 Press the "Enable" button. The robot is enabled. - Step 3 Press the "Drag" button. Drag the robot to the "Approach The robot enters drag mode. - - point" position. Step 4 Press the "Approach point" The "Approach point" light turns OFF. - button. The "Arc start point" light turns ON. - Step 5 Adjust welding parameters. Press F1 to enter welding The first two digits of the digital tube - parameter settings. - display indicate the welding parameter number Rotate the "Mode" knob to adjust - welding parameters. The "Arc start point" light turns OFF. Step 6 Use the joystick to move the robot - to the "Arc start point". Lights for "Intermediate point Line", - · Press the "Arc start point" button. "Intermediate point Arc", and "Arc - · end point" turn ON. Step 7 Use the joystick to move the robot The "Arc end point" light turns OFF to the "Arc end point". - The "Departure point" light turns ON Press the "Arc end point" button - -

![Official manual figure, page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoqN1AXWbFcBm2qW19xZ6%2Fwelding-p197-img02.jpg?alt=media)

Step 8 Use the joystick to move the robot to the "Departure point". Lights for "Departure point" and - Press the "Departure point" "Approach point" both turn ON. - button. Step 9 Select follow-up actions Lights for "Departure point" and Return to Step 8 and continue - "Approach point" both turn ON. - saving the departure point. Lights for "Departure point" and - Return to Step 4 and continue "Approach point" both turn OFF. - teaching the next weld seam. The "Arc start point" light turns ON. - Press the "Stop" button to exit All button lights turn OFF, and the - - teaching mode. robot returns to standby status.

### 14.4 Control box extended function

#### 14.4.1 Managing control box projects

After turning on the welding control box switch on the "Control box Configuration" page in the welding plugin, the project list displays the project name and creation time. Click "New Project" to create a new project. Project names will use the prefix "Arc\_Box\_" and can be up to 20 characters long. Click the icon next to the project name to rename the project. Select a project from the list and click "Set as Default Project" to make it the currently active project for the control box. Click "Delete Project" to remove it.

![Official manual figure, page 198](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0jHUT7TRqKAtIwDG8gGZ%2Fwelding-p198-img02.png?alt=media)

#### 14.4.2 Weld seam management

Manage weld seams via the welding control box

* Add weld seams

After completing the point teaching process for one weld seam according to the Control Box Quick Start, and with both the "Departure point" and "Approach point" button lights illuminated, press the "Approach point" button to continue recording the points for the next weld seam.

* Select weld seams

1. Press the "Mode" knob to enter "Extended-function mode".
2. Then press F1 again to switch to trajectory modification mode (the digital tube

displays L 1 1 1).

3. Press F2 to toggle between the decimal points on the current digital tube page

and switch between different pages. Use the Mode knob to adjust the value. The meaning of the decimal points on the current page or different pages is as follows (○ = decimal point OFF, = decimal point ON): ◉

![Official manual figure, page 199](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKqWv11p4pZr6Wnju1EkI%2Fwelding-p199-img02.jpg?alt=media)

Digital tube 1st Decimal 2nd digit Decimal 3rd digit Decimal 4th digit Decimal digit point point point point Operation Trajectory modification mode-Page 1 (Default Page): Press F2 to sequentially toggle the decimal points in the 2nd, 3rd, and 4th digits. Enter L 1 1 1 trajectory ○ ○ ○ change mode ◉ Selection for L 1 – 9, 1 1 multiple weld select weld seams ○ seam index ○ ○ using the "Mode" knob ◉ Selection for L 1 1 – 9, 1 multiple select point points ○ ○ index using ○ ① the "Mode" knob ◉ Selection for L 1 1 1/2, select arc points arc point ② ○ ○ ○ index using ◉ the "Mode" knob Toggle to the 4th decimal point, then press F2 again to enter Page 2 of Trajectory modification mode: Selection for Select the welding index using Weaving parameter index welding the "Mode" knob ○ parameter index ◉ Selection for Welding parameter index Select the weaving parameter index using weaving ○ the "Mode" knob parameter index ◉ Press F2 to enter the third page of Trajectory modification mode on the digital tube: Welding LS Select the welding absolute speed (1–20 absolute ○ mm/s) using the "Mode" knob speed ◉ 1) Only one point corresponds to the "approach point, arc start point, and arc end point", so the set values for the 3rd and 4th segments of the digital tube are ineffective. Multiple points correspond to the "Departure point and intermediate line point", so the 3rd segment of the digital tube indicates which point in the line it is, while the 4th segment is ineffective. 2) For "intermediate arc points", the 3rd segment of the digital tube indicates which arc segment it is (two points represent one arc segment), and the 4th segment indicates which point within that arc segment (the value is only 1 or 2).

Manage weld seams via DobotStudio Pro After turning on the welding control box switch on the "Welding Control Box Configuration" page of the welding plug-in, click to select a project in the project list (e.g., the default project): Click "+ Add weld seam" to add a new weld seam for the current project; Click the icon under the action bar to delete the current weld seam. After adding a weld seam, you can teach points for the new weld seam and set the welding parameter number/Job number, weaving parameter number, absolute speed, as well as the multi-layer multi-pass welding combination index number and intermittent welding parameter number.

**NOTE**

The multi-layer multi-pass welding combination index number and intermittent welding parameter number are set for the entire project rather than a single weld seam.

![Official manual figure, page 201](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGX0U0Oh2c5GpjvSgrhnU%2Fwelding-p201-img03.jpg?alt=media)

#### 14.4.3 Managing points

Manage points via the welding control box

* View point

Long-press the point-teaching button on the welding control box (the button light will flash continuously). The robot will move to the saved point; releasing the button will stop the motion.

* Modify point

Long-press the point-teaching button to move the robot to the specified point (e.g., the ① arc start point). Use the joystick to move the robot to the new position for the arc start point. ② Long-press the F3 button, and simultaneously press the "Arc start point" button once. ③ The new position will overwrite the original arc start point (ensure the F3 button remains pressed during the entire process). If the point is successfully modified, the indicator for the point-teaching button will flash once.

**NOTE**

* In normal mode, what you modified is the point of the last weld seam in the current project.
* In Trajectory Modification Mode, you can modify the point of the selected weld seam. Manage points via DobotStudio Pro

1. After turning on the welding control box switch on the Welding Control Box

Configuration page in the welding plugin, click the project name to display all weld seams in the project. Then, click the View Points button for the desired weld seam to navigate to the point information page.

2. The point information page is shown in the figure below. The approach point, arc start

point, and arc end point cannot be deleted. Intermediate points and departure points can be deleted, but each weld seam must have at least one departure point.

![Official manual figure, page 202](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKEL2q1UZjgsOF3UDIRok%2Fwelding-p202-img02.jpg?alt=media)

3. Click "Obtain" to get the current position of a specified point. The "Obtain" button will

then change to "Re-obtain", allowing you to re-obtain the position information. Use the Motion Mode drop-down at the top of the list to select whether the robot moves via linear or joint motion. Long press the "Move to" button to move the robot from the current position to the selected point.

4. Double-click the values for X, Y, Z, RX, RY, RZ to directly modify the current point's

information.

5. Click "Add Intermediate point" to add an intermediate point via linear motion or arc

motion.

* Select the "Linear motion" option and click "Obtain" to get the position of the intermediate linear point. The "Obtain" button will then change to "Re-obtain", allowing you to re-obtain the position information. Click "Add" to complete the addition of the intermediate linear point.

![Official manual figure, page 203](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWOUQHQjfyGAewKHa4Lgp%2Fwelding-p203-img02.jpg?alt=media)

![Official manual figure, page 203](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7H287ql12hsvr42NI97t%2Fwelding-p203-img03.jpg?alt=media)

* Select the "Arc motion" option and click "Obtain" to get the positions of two points (P1 and P2) for the arc. The "Obtain" button will then change to "Re-obtain", allowing you to re-obtain the position information. Click "Add" to complete the addition of the intermediate arc point.

**NOTE**

* When adding intermediate arc points, if only the first point P1 is obtained, clicking "Add" will treat it as an intermediate linear point by default.
* When adding intermediate arc points, if only the second point P2 is obtained, clicking "Add" will prompt the message: "Cannot add Arc P2 alone".

6. Click "Add departure point", and the departure point will appear directly in the point

information list.

![Official manual figure, page 204](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FF6vjzlx1vSwXEWezhvnH%2Fwelding-p204-img02.jpg?alt=media)

![Official manual figure, page 204](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFg950NdypEnGi0cKnuCb%2Fwelding-p204-img03.jpg?alt=media)

7. After adding points, click the "Save" button in the upper-right corner of the page to

save the point information and synchronize it with the welding control box.

### 14.5 Application case

This section will demonstrate how to apply the welding control box to multipass welding scenarios, using the parameter configuration, point teaching, and debugging as an example.

#### 14.5.1 Parameter configuration

1. Create a new welding param No.: Open the welding plugin and go to the

Welding Parameters page to customize the welding parameter number. For welding parameter configuration for different welders, refer to Welding parameter configuration.

2. Create a new weaving parameter No.: Customize the weaving parameter

number on the Weaving Process Parameters page in the welding plugin. Refer to Weaving process parameters for details.

![Official manual figure, page 205](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmCSTqFo1n7YSJ31TLhUZ%2Fwelding-p205-img02.png?alt=media)

![Official manual figure, page 205](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrVvmx4zDMdnxKhsOtFFa%2Fwelding-p205-img03.png?alt=media)

3. Create a new channel combination index: Follow the instructions in Multi-Layer

Multi-Pass Welding Configuration and Channel Combination Index Configuration to complete the configuration of multi-layer multi-pass welding channels and channel combination indices on the Multi-Layer Multi-Pass Welding Configuration page. The following uses channel combination index 1 (channel combination sequence 1 → 2 → 3) as an example.

4. Enable welding control box function: On the Welding Control Box

Configuration page in the welding plugin, toggle the Welding Control Box switch to ON.

![Official manual figure, page 206](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCW3cZN5oe5up8xlNVyeH%2Fwelding-p206-img02.png?alt=media)

![Official manual figure, page 206](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUH4wAQtRwAWLayAOYGEW%2Fwelding-p206-img03.png?alt=media)

![Official manual figure, page 206](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzwNbSeTGMvcSdob2VFNB%2Fwelding-p206-img04.png?alt=media)

#### 14.5.2 Point teaching

Take multipass welding with the control box as an example. The shape of the intermediate point is an arc. During the teaching process, parameters such as global speed, welding absolute speed, welding parameter index, and weaving parameter index can be modified. Operation procedure System response / Button status The display tube shows "0100". Step 1 Long-press the "Mode" knob to - clear the project. The "Approach point" light turns - ON. Step 2 Press the "Enable" button. The robot is enabled. - Step 3 Press the "Drag" button. Drag the robot to the "Approach The robot enters drag mode. - - point" position. The "Approach point" light turns - Step 4 Press the "Approach point" OFF. button. The "Arc start point" light turns - ON. Step 5 Adjust speed Short-press the "Mode" knob - → Press F1 to switch to global jog The first digit of the digital tube speed adjustment mode. - displays Rotate the "Mode" knob to adjust - global speed. Press F1 to switch to welding - absolute speed adjustment The first digit of the digital tube mode. - displays Rotate the "Mode" knob to adjust - welding absolute speed. Step 6 Adjust the multi-layer multi-pass welding channel combination index Press F1 to switch to the - multipass welding mode. The first digit of the digital tube - Rotate the Mode knob to adjust displays - the channel combination index number. Short-press the "Mode" knob to - exit the extended-function mode.

Step 7 Parameter settings Press F1 → enter welding - parameter settings. The first two digits of the digital - tube display indicate the welding Rotate the "Mode" knob to adjust parameter number - welding parameters. Press F2 enter weaving - → parameter settings. The last two digits of the digital - tube display indicate the weaving Rotate the "Mode" knob to adjust parameter number - weaving parameters. The "Arc start point" light turns - OFF. Step 8 Use the joystick to move the robot to the "Arc start point". Lights for "Intermediate - point Line", "Intermediate Press the "Arc start point" button. · - point Arc", and "Arc end point" · turn ON. Lights for "Intermediate - Step 9 Use the joystick to move the robot point Line", "Intermediate · to the " Intermediate point ". point Arc", and "Arc end point" · turn ON. Lights for "Intermediate - point Line" and "Arc end point" · Press the "Intermediate turn OFF. - point Arc" button a first time. · Light for "Intermediate - point Arc" turns OFF. · Lights for "Intermediate - Press the " Intermediate Arc" point Line", "Intermediate - · · button a second time. point Arc", and "Arc end point" · turn ON. The "Arc end point" light turns Step 10 Use the joystick to move the robot - OFF to the "Arc end point". The "Departure point" light turns Press the "Arc end point" button - - ON Step 11 Use the joystick to move the robot to the "Departure point". Lights for "Departure point" and - "Approach point" both turn ON. Press the "Departure point" -

button. Step 12 Select follow-up actions Lights for "Departure point" and Return to Step 11 and continue - "Approach point" both turn ON. - saving the departure point. Lights for "Departure point" and - "Approach point" both turn OFF. Return to Step 4 and continue - teaching the next weld seam. The "Arc start point" light turns - ON. Press the "Stop" button to exit All button lights turn OFF, and the - - teaching mode. robot returns to standby status.

**NOTE**

* Welding absolute speed: If the "Approach point" button is pressed, the settings for welding absolute speed will apply to the next weld seam (i.e., the one to be taught). If the "Approach point" button has not been pressed, the absolute speed of the last weld seam (i.e., the one that has just been taught) will be modified.
* Multi-layer multi-pass welding channel combination index number: Applies to all weld seams in the current project and only needs to be set once.
* Welding/weaving parameters: Welding and weaving parameters can be set only after the approach point is saved (when the "Approach point" button light is OFF). Otherwise, pressing the F1 or F2 buttons has no response.
* If there are multiple weld seams with different welding and weaving parameter sets, modify the parameters in Trajectory modification mode. First, select the desired weld seam, then navigate to the second page of the digital tube to adjust the welding and weaving parameters for the selected weld seam. After parameter modification is complete, return to normal operation mode. The digital tube will display the parameters of the last weld seam. To verify if all weld seam parameters are correctly modified, use the Weld Seam Management page in DobotStudio Pro for review.

#### 14.5.3 Debugging and running

After completing the point teaching for multi-layer multi-pass welding, you can use the "Weld" button on the welding control box or the "Welding Programming" function in DobotStudio Pro to start the specified welding project. If modifications to weld seams or points are required during operation, refer to the Weld Seam Management and Point Management sections to make the necessary adjustments.

## 15. Intelligent Welding Assistant

### 15.1 Introduction

The robot arm supports an optional six-axis force sensor. Force control functions can be enabled and configured via the software. Force-control drag is a drag-teaching function based on end-effector force analysis. When the user applies force to the six-axis force sensor at the robot's end, the robot moves in the direction of the applied force. The robot's motion speed is proportional to the magnitude of the applied force within a certain range. In practical applications, users can also constrain the robot's motion direction, making it to move only along one or several specified directions. The CRAF series is ideal for high- precision applications requiring "tactile interaction", such as precision assembly, surgical assistance, and flexible polishing. To use the force-control dragging function, after completing sensor installation, calibration, and software settings, you can enter force-control dragging mode via the plugin interface, controller DI, or by calling the secondary development interface, and then perform dragging. For sensor installation and calibration, as well as software settings, please refer to the ForceControl Plugin User Guide.

### 15.2 Calibrating the sensor

Sensor calibration is required the first time you use the force control function.

*

After disassembling and reassembling the sensor, recalibration is required.

*

If the robot's installation posture changes (e.g., from upright mounting to inverted

* mounting), recalibration is required.

1. Click the "Jog" button of the software to enter the Jog panel, and set the user

coordinate system and tool coordinate system to 0.

2. Click the "Start Calibration" button on the Intelligent Welding Assistant page of the

software.

3. Jog the robot to a suitable position so that the X+ on the six-axis force sensor is facing

downward (the diagram on the interface takes the robot base parallel to the ground as an example, the sensor mark should be facing the ground in the case of side mounting or upright mounting).

![Official manual figure, page 211](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAEGIfpM9P2VLXlzdQxua%2Fwelding-p211-img02.jpg?alt=media)

![Official manual figure, page 211](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9jMCOWl6bVcN93KKfGwR%2Fwelding-p211-img03.png?alt=media)

4. Click "X + is facing down, next step" on the software page.
5. Fine-tune the robot's J6 axis based on the last posture, so that the Y+ on the sensor

is facing downward, then click "Y+ is facing down, next step".

6. Adjust the robot's J5 axis so that the Z+ on the sensor is vertically downward, then

![Official manual figure, page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft0b23px5JjRU9sOQyjS9%2Fwelding-p212-img02.jpg?alt=media)

![Official manual figure, page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWGzSdSxaxWhU88yZlJ8H%2Fwelding-p212-img03.jpg?alt=media)

![Official manual figure, page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUKmQlQIaSpPOJ21vPLMy%2Fwelding-p212-img04.jpg?alt=media)

click "Z+ is facing down, complete".

7. After successful calibration, the result will be displayed on the interface. Click "OK" to

complete the calibration.

8. You can verify the accuracy of the calibration results by performing a Zeroing operation.

![Official manual figure, page 213](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAWQHrCxxyqF3wGPFhIPX%2Fwelding-p213-img02.jpg?alt=media)

![Official manual figure, page 213](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FglE9kZab48znyNMNqXas%2Fwelding-p213-img03.jpg?alt=media)

### 15.3 Real-time data

Real-time data means (the value read by the force sensor) - (Force variations caused by load parameters). It is recommended to configure the load parameters using the automatic load identification function, with specific operations referenced in the DobotStudio Pro help documentation.

**NOTICE**

After completing the load parameter configuration, you can freely change the robot's end posture and check via the software interface whether the real-time data shows significant changes to determine the accuracy of the load identification results. You can modify the reference coordinate system for the real-time data via the drop-down box. Sensor coordinate system: Displays force and torque values based on the six-axis

* force sensor coordinate system. The six-axis force coordinate system coincides with the TCP, with its origin located at the flange center point of the TCP. The force/torque directions follow the right-hand rule. Tool coordinate system: Displays force and torque values based on the current tool
* coordinate system. To change the tool coordinate system, set it in the Jog panel.

![Official manual figure, page 214](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcUH1yuXGHrSaCBqmu8Pg%2Fwelding-p214-img02.jpg?alt=media)

### 15.4 View curve

Click the "View curve" button to display real-time force control curves for each direction. The force control curve displays up to 100 sets of data, with an update frequency of 200ms. Clicking any data point on the curve allows you to view the corresponding force and torque values.

![Official manual figure, page 215](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyBmc75Jw3naPRMS97aUC%2Fwelding-p215-img02.jpg?alt=media)

![Official manual figure, page 215](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCvMzSnyTHoQaPeBNG4cj%2Fwelding-p215-img03.png?alt=media)

Real-time switch: Turning on the real-time switch automatically obtains the current controller time and updates the curve in real-time. When turned off, the updates pause, allowing you to check the curve. Direction switch: Tick the direction (Fx, Fy, Fz, Mx, My, Mz) to display the corresponding force control curve for that direction. By default, all curves are displayed. After reconnecting the robot to the welding plug-in software, resume the default switch state (OFF).

### 15.5 Drag settings

You can click the "Drag settings" button to enter the sensor dragging configuration page.

![Official manual figure, page 216](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9YFpdjC9leVZNmftGI7l%2Fwelding-p216-img02.jpg?alt=media)

![Official manual figure, page 216](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqpcPO8K4LlPHcss45jYU%2Fwelding-p216-img03.jpg?alt=media)

#### 15.5.1 Sensor limit

You can set the maximum safe force value and torque value for the sensor limit as needed. During force-control drag, if the absolute value of the force or torque detected by the sensor exceeds the user-set threshold, the robot will trigger an alarm and stop moving.

![Official manual figure, page 217](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzKB18SvwOQhYHKGxKDRl%2Fwelding-p217-img02.jpg?alt=media)

#### 15.5.2 I/O configuration

After configuration, users can activate various force-control drag mode or exit force-control drag by triggering the controller DI. For descriptions of each mode, please refer to the Drag mode section.

#### 15.5.3 Impedance settings

![Official manual figure, page 218](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fyakv7ITEQAObuZcbUoCG%2Fwelding-p218-img02.png?alt=media)

![Official manual figure, page 218](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtdKrwGdrVf6N6n0jsGdq%2Fwelding-p218-img03.png?alt=media)

Set the impedance values for force-control drag. Inertia: Parameter range: \[0, 1000]. Damping: Parameter range \[0, 1000]. Minimum force: The parameter range is \[0, 200]. If the dragging feels heavy, the minimum force value can be adjusted downward. However, it is recommended that the minimum force should not be set below 2N, as lower values may pose risks during operation. Click Restore Defaults to reset to the factory default recommended impedance values.

**NOTICE**

* It is not recommended to modify the inertia and damping parameters. Simply select either "Default Impedance" or "Welding Impedance" based on your application scenario to apply the preset values.
* Parameters on the "Impedance Settings" page cannot be modified while the robot is in motion.

### 15.6 Zeroing

Zeroing refers to the operation where the robot compensates for the initial offset value of the force sensor, enabling the system to identify the "mechanical reference zero point" under the current load parameter configuration. Drift in temperature and zero offset are inevitable phenomena in force sensors. It is recommended to check whether the displayed force and torque values are accurate before using the force control feature. If the values are incorrect, it is necessary to execute the zeroing command to ensure the accuracy of subsequent sensor data.

![Official manual figure, page 219](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhvSqdbwysez1XEdknvV0%2Fwelding-p219-img02.jpg?alt=media)

Click "Zeroing" to set the current force and torque values of the sensor to 0 (it is recommended to keep the Z-axis facing downward). After zeroing, you can change the robot's posture in any manner and observe whether there are noticeable changes in the real-time data. Under normal circumstances, without dragging the robot, the force value should not exceed 10N and the torque value should not exceed 2N·m. Otherwise, recalibration is required.

**NOTE**

* Zeroing is not allowed if there is no calibration result.
* Zeroing is not allowed if the sensor is offline.
* After restarting the robot, you need to re-zero the sensor before using the force control function again.

## Appendix A Script Commands

### A.1 Basic Welding Programming (Arc Welding)

A.1.1 Script commands

1. Command: WeldAbsSpeed(speed,unit)

Description: Sets the robot arm motion speed during the welding process (from arc start to arc end). This speed is absolute and is not affected by the robot's global speed ratio. Parameter: "speed": The speed value. "unit": The unit of speed, supporting "mm/s", "mm/min", and "cm/min". Example: WeldAbsSpeed(10, "mm/s")

2. Command: WeldMethod(method)

Description: Set the welding method. For EWM welder, this command can be used to set a combination of the welding method and operation mode. For OTC, Panasonic, Megmeet, Aotai, Flama, and YaoLi welders, the welding method can be set using this command. For other welders, this command is not required. If the command is not called, the welder working mode set in the plugin will be used by default. Parameter: EWM welder supports the following parameters:

* twoStepDCWeld
* specialTwoStepDCWeld
* twoStepPulseWeld
* specialTwoStepPulseWeld

Flama welder supports the following parameters:

* monizationDC: DC synergy
* singlePulseMonization: Single-pulse synergy
* proximityMode
* Job: Call the job number

Aotai MIG-LST welder supports the following parameters:

* flat
* pulseProcess
* Job: Call the job number
* lowSplash
* flatSpotWeld
* lowSplashSpotWeld

Aotai MIG-PLUS welder supports the following parameters:

* flat
* pulseProcess
* Job: Call the job number
* bigPenetration
* fastPulse

Megmeet welder supports the following parameters:

* monizationDC: DC synergy
* pulseMonization: Pulse synergy
* proximityMode
* respectivelyMode: Separation mode
* Job: Call the job number

The OTC MAG / MIG / CO2 welder supports the following parameters:

* dcPulse
* dc
* dcLowSplash
* dcWavePulse
* acPulse
* acWavePulse
* dArc
* msMig
* Job: Call the job number

OTC TIG welder supports the following parameters:

* dcTig: DC TIG
* acTig: AC TIG
* adcTig: AC-DC TIG
* Job: Call the job number

The Panasonic welder supports the following parameters:

* respectivelyMode: Separation mode
* monization: Synergy
* Job: Call the job number

YaoLi welder supports the following parameters:

* monizationDC: DC synergy
* pulseMonization: Pulse synergy
* proximityMode
* respectivelyMode: Separation mode

Example: WeldMethod('flat')

3. Command: WeldJobNumber(jobNum)

Description: When setting welding parameters using Job mode, modify the Job number (welder process number) to be called. If this command is not called, the Job number set in the plugin is used by default. Parameter: Job No. Example: WeldJobNumber(1)

4. Command: WeldProcessNumber(processNum)

Description: This instruction is only required for EWM/SKS/Panasonic welders. You need to modify the called Program No. (Welding parameter index). If the command is not called, use the Program No. set in the plugin by default. Parameter: Program No. Example: WeldProcessNumber(1)

5. Command: WeldArcParams(arcParams)

Description: When setting welding parameters in non-Job mode, you can use this command to modify the called Custom parameter number. If the command is not called, the custom parameter number set in the plugin will be used by default. Parameter: Custom param. No. Example: WeldArcParams(1)

6. Command: WeldArcStart()

Description: Notify the welder to start the arc. Example: WeldArcStart()

7. Command: WeldArcEnd()

Description: Notify the welder to end the arc. Example: WeldArcEnd()

8. Command: WeldThroughArc(current, voltage)

Description: When setting the welding parameters in non-Job mode, you can use this command to modify the current and voltage (or Arc voltage compensation) values for subsequent welding. Parameter: "current": Current value, unit: A. "voltage": Voltage (or Arc voltage compensation) value. The unit of voltage: V; no unit for Arc voltage compensation. Example: WeldThroughArc(10, 10)

9. Command: WeldWireFeed(time)

Description: Wire feed. Parameter: Wire feed time, unit: ms.

Example: WeldWireFeed(1000)

10. Command: WeldWireBack(time)

Description: Manual wire retract. Parameter: Wire retract time, unit: ms. Example: WeldWireBack(1000)

11. Command: WeldGasFeed(time)

Description: Gas feed. Parameter: Gas feed time, unit: ms. Example: WeldGasFeed(1000) A.1.2 Script DEMO Here takes the arc welding as an example. Create a project and teach the following points in the Points page:

* P1: Approach point, the safety point before starting welding, which is recommended to be set at a position above the arc start point.
* P2: Arc start point, the point at which welding begins.
* P3: Arc intermediate point. Together with P2 and P4, it defines the shape of the arc.
* P4: Arc end point, the point at which welding ends.
* P5: Departure point, the end safety point after the welding is completed. Due to residual heat in the welding torch after welding, it is recommended to set this to a hanging position. Example script is as follows. The welding parameters used in the DEMO are those finally saved on the Welding Parameter Configuration page. MovL(P1) -- Move to the approach point. MovL(P2) -- Move to the arc start point. WeldArcSpeed(10) -- Set the welding speed. WeldArcStart() -- Arc start. Arc(P3 P4) -- Start arc motion., WeldArcEnd() -- Arc end. MovL(P5) -- Move to the departure point.

### A.2 Basic Welding Programming (Laser Welding)

A.2.1 Script commands

1. Command: WeldAbsSpeed(speed,unit)

Description: Sets the robot arm motion speed during the welding process (from arc start to arc end). This speed is absolute and is not affected by the robot's global speed ratio. Parameter: "speed": The speed value. "unit": The unit of speed, supporting "mm/s", "mm/min", and "cm/min". Example: WeldAbsSpeed(10, "mm/s")

2. Command: WeldLaserParams(params)

Description: Modify the called custom parameter number. If the command is not called, the custom parameter number set in the plugin will be used by default. Parameter: Custom param. No. Example: WeldLaserParams(1)

3. Command: WeldLaserStart()

Description: Notify the welder to start the welding. Example: WeldLaserStart()

4. Command: WeldLaserEnd()

Description: Notify the welder to stop the welding. Example: WeldLaserEnd()

5. Command: WeldWireFeed(time)

Description: Wire feed. Parameter: Wire feed time, unit: ms. Example: WeldWireFeed(1000)

6. Command: WeldWireBack(time)

Description: Manual wire retract. Parameter: Wire retract time, unit: ms. Example: WeldWireBack(1000)

7. Command: WeldGasFeed(time)

Description: Gas feed. Parameter: Gas feed time, unit: ms. Example: WeldGasFeed(1000)

**NOTE**

In the subsequent sections of this document, all other function DEMOs use arc welding as an example. To use the laser welding function, replace the WeldArcParams, WeldArcStart and WeldArcEnd commands with the WeldLaserParams, WeldLaserStart and WeldLaserEnd commands accordingly. A.2.2 Script DEMO This DEMO uses welding an arc as an example. Create a project and teach the following points in the Points page:

* P1: Approach point, the safety point before starting welding, which is recommended to be set at a position above the arc start point.
* P2: Arc start point, the point at which welding begins.
* P3: Arc intermediate point. Together with P2 and P4, it defines the shape of the arc.
* P4: Arc end point, the point at which welding ends.
* P5: Departure point, the end safety point after the welding is completed. Due to residual heat in the welding torch after welding, it is recommended to set this to a hanging position. Example script is as follows. The welding parameters used in the DEMO are those finally saved on the Welding Parameter Configuration page. MovL(P1) -- Move to the approach point. MovL(P2) -- Move to the arc start point. WeldArcSpeed(10) -- Set the welding speed. WeldLaserStart() -- Start welding. Arc(P3 P4) -- Start arc motion., WeldLaserEnd() -- Stop welding. MovL(P5) -- Move to the departure point.

### A.3 Weaving Welding Programming

A.3.1 Script commands

1. Command: WeldWeaveParams(weaveParams)

Description: Modify the called weaving parameter number. If the command is not called, the weaving process parameter set in the plugin will be used by default. Parameter: Weaving parameter No. Example: WeldWeaveParams(1)

2. Command: WeldWeaveStart()

Description: After calling this block, the robot enters the weaving mode, and weaving motion will be added when performing linear or arc motion. Example: WeldWeaveStart()

3. Command: WeldWeaveEnd()

Description: Robot exits the weaving mode. Example: WeldWeaveEnd() A.3.2 Script DEMO Based on the Arc Welding Script DEMO, simply add the weaving start and stop commands after arc start and before arc end. The welding parameters used in the DEMO are those finally saved on the Welding Parameter Configuration page. MovL(P1) MovL(P2) WeldAbsSpeed(6, “mm/s”) WeldArcParams(1) WeldWeaveParams(1) WeldArcStart() -- Arc start. WeldWeaveStart() -- Enter the weaving mode. ArcTrackStart(1) MovL(P3) ArcTrackEnd() WeldWeaveStart() -- Exit the weaving mode. WeldArcEnd() -- Arc end. MoveL(P4)

### A.4 Laser Positioning Programming

A.4.1 Script commands

1. Command: LaserPositioning(point, job)

Description: Perform laser positioning and obtain the target point by positioning. Parameter: "point": The photo point. "job": The weld-seam type index (Job No.) set in the CUTEWELDER software. Return: The spatial coordinates (XYZ) of the target point obtained by positioning, which need to be used with the posture reference point. See DEMO for details. Example: local laser\_pos1 = LaserPositioning(P1, 10)

2. Command: CalcOffset(laser\_table)

Description: Calculate the offset between the datum point and the measurement point for relative positioning. Parameter: laser\_table:

* offsetType: Positioning method. 1: Point positioning, 2: Inner and outer diameter positioning, 3: Surface positioning.
* datumPointX: Datum point for calculating the offset value. X represents 1 to 3.
* measurePointX: Measurement point, the offset point for calculating the offset value. X represents 1 to 3. Return: The calculated offset value. Example: local laser\_table = {} laser\_table\["offsetType"] = 1 laser\_table\["datumPoint1"'] = {0,0,0,0,0,0} laser\_table\["measurePoint1"] ={0,0,0,0,0,0} local offset = CalcOffset(laser\_table)

3. Command: OffsetStart(offset)

Description: Add the saved offset value onto the subsequent robot motion trajectory (only linear, arc, and circle motion commands are supported). Repeated calling of this command before calling OffsetEnd() will update the compensated offset value. Parameter: offset: the offset value calculated by CalcOffset. Example: OffsetStart(offset)

4. Command: OffsetEnd()

Description: Stop adding the trajectory offset values. Example: OffsetEnd()

A.4.2 Script DEMO Laser absolute positioning local takePhoto1 = P1 -- Photo point local posRef1 = P2 -- Posture reference point -- Move to the photo point MovL(takePhoto1) -- Wait for 2s Wait(2000) -- Get coordinates of the positioning point local laser\_pos = LaserPositioning(takePhoto1,1) -- Use the coordinates of the positioning point and the posture of the posture reference point to splice into an absolute positioning point local laser\_absPos = {point = {pose = {laser\_pos\[1], laser\_pos\[2], laser\_pos\[3], posRef1.pose\[4], posRef1.pose\[5], posRef1.pose\[6]\}}, user= posRef1.user, tool= posRef1.tool} -- Move to the absolute positioning point MovL(laser\_absPos.point, {user=laser\_absPos.user, tool=laser\_absPos.tool}) Laser relative positioning (Point positioning) Here demonstrates how to perform point positioning in the XY direction. The welding parameters used in this DEMO are the final saved parameters from the Welding Parameter Configuration page. Project 1: Get datum point -- Please create two global variables “globalPoint1” and “globalPoint2” in the “Monitor > Global Variables” page in advance -- Please place the workpiece at the standard position first and run the following code to get the datum point MovL(P1) -- Photo point 1, position the arc start point from the X direction Wait(2000) -- Get datum point coordinates local g1 = LaserPositioning(P1,1) SetGlobalVariable("globalPoint1 ", g1) -- Please create the global variable “globalPoint1” first. MovL(P2) -- Photo point 2, position the arc start point from the Y direction Wait(2000) -- Get datum point coordinates local g2 = LaserPositioning(P2,1) SetGlobalVariable("globalPoint2 ", g2) -- Please create the global variable “globalPoint2” first. Project: Point positioning -- Get the datum point and run the following code -- Get measurement points and calculate the offset values MovL(P1) -- Photo point 1 Wait(2000) -- Get coordinates of the positioning point local pos1 = LaserPositioning(P1,1)

my\_table = {} my\_table\["offsetType"] = 1 -- Point positioning my\_table\["datumPoint1"] = globalPoint1 -- Datum point 1 my\_table\["measurePoint1"] = {pos1\[1], pos1\[2], pos1\[3], pos1\[4], pos1\[5], pos1\[6]} -- Measurement point 1 offset1 = CalcOffset(my\_table) -- Calculate offset 1 local pp2=RelPointUser(P2,{offset1\[1],0,0,0,0,0}) -- Photo point 2, offset in the X direction based on the result of Photo point 1 MovL(pp2,{user = P2.user,tool = P2.tool }) Wait(2000) local pos2 = LaserPositioning(pp2,1) my\_table = {} my\_table\["offsetType"] = 1 -- Point positioning my\_table\["datumPoint1"] = globalPoint2 -- Datum point 2 my\_table\["measurePoint1"] = {pos2\[1], pos2\[2], pos2\[3], pos2\[4], pos2\[5], pos2\[6]} -- Measurement point 2 offset2 = CalcOffset(my\_table) -- Calculate offset 2 local offset ={offset2\[1], offset1\[2],0,0,0,0} -- Combined offset MovL(P10) OffsetStart(offset) -- The trajectory starts offsetting -- Welding process, written according to actual needs MovL(P11) WeldArcSpeed(5) WeldArcParams(1) WeldArcStart() MovL(P12, {r=5}) MovL(P13, {r=5}) WeldArcEnd() MovL(P14) OffsetEnd() -- Close trajectory offset MovL(P15) -- Safety point Laser relative positioning (Surface positioning) Here demonstrates how to perform surface positioning. The welding parameters used in the DEMO are those finally saved on the Welding Parameter Configuration page. Project 1: Get datum point -- Please create three global variables “globalPoint1”, “globalPoint2” and “globalPoint3” in the “Monitor > Global Variables” page in advance -- Please place the workpiece at the standard position first and run the following code to get the datum point MovL(P1) -- Photo point 1, aim the laser at a point on the right-angled side of the workpiece Wait(2000) -- Get datum point coordinates local g1 = LaserPositioning(P1,1) SetGlobalVariable("globalPoint1 ", g1) -- Please create the global variable “globalPoint1” first.

MovL(P2) -- Photo point 2, aim the laser at another point on the same right-angled side Wait(2000) -- Get datum point coordinates local g2 = LaserPositioning(P2,1) SetGlobalVariable("globalPoint2 ", g2) -- Please create the global variable “globalPoint2” first. MovL(P3) -- Photo point 3, aim the laser at a point on the adjacent right-angled side. Wait(2000) -- Get datum point coordinates local g3 = LaserPositioning(P3,1) SetGlobalVariable("globalPoint3 ", g3) -- Please create the global variable “globalPoint3” first. Project 2: Surface positioning -- Get the datum point and run the following code -- Get measurement points and calculate the offset values MovL(P1) -- Photo point 1 Wait(2000) -- Get coordinates of the positioning point local pos1 = LaserPositioning(P1,1) MovL(P2) -- Photo point 2 Wait(2000) -- Get coordinates of the positioning point local pos2 = LaserPositioning(P2,1) MovL(P3) -- Photo point 3 Wait(2000) -- Get coordinates of the positioning point local pos3 = LaserPositioning(P3,1) my\_table = {} my\_table\["offsetType"] = 3 -- Surface positioning my\_table\["datumPoint1"] = globalPoint1 -- Datum point 1 my\_table\["datumPoint2"] = globalPoint2 -- Datum point 2 my\_table\["datumPoint3"] = globalPoint3 -- Datum point 3 my\_table\["measurePoint1"] = {pos1\[1], pos1\[2], pos1\[3], pos1\[4], pos1\[5], pos1\[6]} -- Measurement point 1 my\_table\["measurePoint2"] = {pos2\[1], pos2\[2], pos2\[3], pos2\[4], pos2\[5], pos2\[6]} -- Measurement point 2 my\_table\["measurePoint3"] = {pos3\[1], pos3\[2], pos3\[3], pos3\[4], pos3\[5], pos3\[6]} -- Measurement point 3 offset = CalcOffset(my\_table) -- Calculate offset MovL(P10) OffsetStart(offset) -- The trajectory starts offsetting -- Welding process, written according to actual needs MovL(P11) WeldArcSpeed(5) WeldArcParams(1) WeldArcStart() MovL(P12, {r=20})

MovL(P13, {r=20}) WeldArcEnd() MovL(P14) OffsetEnd() -- Close trajectory offset MovL(P15) -- Safety point

### A.5 Laser Tracking Programming

A.5.1 Script commands

1. Command: CommonLaserTrackStart(job, user, tool)

Description: Start laser weld seam tracking (compatible with various laser sensors). Repeated calling of this command is not allowed before calling CommonLaserTrackEnd(). The trajectory of the robot after starting tracking (only linear, arc, and circle motion commands are supported) will be automatically corrected based on the tracking results. Parameter: "job": The weld seam type number (Job number) set in the laser sensor software. "user": The user coordinate system index, which should be the same as the one used when teaching the welding points. "tool": The tool coordinate system index, which should be the same as the one used when teaching the welding points. Example: CommonLaserTrackStart(1,0,1)

2. Command: CommonLaserOffset(x,y,z,user)

Description: Provide real-time offset adjustment for the target point of laser positioning or the trajectory of laser tracking. Parameter: "x, y, z": The offset compensation values in three-dimensional space. You can enter positive or negative values, with the unit in millimeters (mm). The system will adjust the welding position based on the set values. "user": The user coordinate system index, which should be the same as the one used when teaching the welding points. Example CommonLaserOffset(1,1,1,0):

3. Command: FullVLaserCalibrate(laser\_autocaliPointArr, {v = value, a = value})

Description: Full-V laser calibration. Parameter: "laser\_autocaliPointArr": A collection of points in the format "laser\_autocaliPointArr = {P1, P2, P3, P4, P5}", representing workpiece feature points and the positions of photo points 1, 2, 3, and 4. "v": The motion speed. "a": The motion acceleration. Example: laser\_autocaliPointArr = {P1,P2,P3,P4,P5}

YLLaserCalibrate(laser\_autocaliPointArr, {v = 50, a = 50})

4. Command: YLLaserCalibrate(laser\_autocaliPointArr, {v = value, a = value})

Description: Intelligent laser calibration. Parameter: "laser\_autocaliPointArr": A collection of points in the format "laser\_autocaliPointArr = {P1, P2, P3, P4, P5}", representing workpiece feature points and the positions of photo points 1, 2, 3, and 4. "v": The motion speed. "a": The motion acceleration. Example: laser\_autocaliPointArr = {P1,P2,P3,P4,P5} YLLaserCalibrate(laser\_autocaliPointArr, {v = 50, a = 50})

5. Command: CommonLaserTrackEnd()

Description: Stop laser seam tracking (compatible with various laser sensors). Example: CommonLaserTrackEnd()

**NOTICE**

* To ensure that tracking starts normally, the tracking start point (where the laser beam is located at the arc start point), the arc start point and the first transition point should be kept in a straight line as far as possible. See the following DEMO for details.
* When teaching the welding point, the distance between the teaching point and the seam should not exceed 10mm to avoid affecting the welding quality.
* During tracking, the motion command must specify the transition radius through the optional parameter r. Example: MovL(P1, {r=5}). For paths with a large turning radius such as S-curves, it is recommended to set a larger transition radius (10mm or more).
* Weaving is not supported during tracking.
* Laser positioning is not supported after laser tracking is turned on. If you need to use the laser positioning and laser tracking function together, you can get the positioning target first, turn on the tracking function, and then move to the positioning target. See Laser Absolute Positioning + Tracking (DEMO) for details.
* In case the seam trajectory is a curve, it is recommended to weld at a speed of less than or equal to 10mm/s to ensure the seam forming effect. If you need to weld at a faster speed, you can use Intelligent Laser's misalignment compensation function. Consult Intelligent Laser's technical support for details.
* If there is a sudden change in the seam trajectory (e.g. the direction of the curve changes significantly when a straight line is connected to a curve, refer to the trajectory in the figure below), it is recommended to weld at a speed of less than or equal to 10mm/s to ensure the seam forming effect.
* If you need to use Intelligent Laser's offset setting function, it is recommended to set the offset to no more than 5mm. If the offset is greater than 5mm, it means that the calibration error of the welding torch or laser is too large, and recalibration is recommended. A.5.2 Script DEMO Taking the workpiece in the above figure as an example, the user needs to teach the points 1, 3, 4, and 5 in the figure, and obtain the point 2 by absolute positioning. Point 1 is the tracking start point, point 2 is the arc start point, points 3 and 4 are transition points (if using the common laser tracking block, transition points do not need to be taught), and point 5 is the arc end point. In addition, you need to teach the safety point P6 after welding is finished. When teaching P1, please try to ensure that P1, P2 and P3 are close to a straight line (as shown in the figure above). If the direction of P2 changes a lot (as shown in the figure below, the angle of the three points is close to or less than a right angle), it may cause the laser to fail to track properly.

![Official manual figure, page 234](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8TehScX5Gg8dsj5FjNvi%2Fwelding-p234-img03.jpg?alt=media)

![Official manual figure, page 234](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAvP6FAYiQUSXT0SvE7fm%2Fwelding-p234-img04.jpg?alt=media)

When teaching the welding point (P2-P5), the distance between the teaching point and the seam should not be more than 10mm, otherwise the welding effect will be affected. When teaching the arc end point (P5), it is recommended to advance a certain distance relative to the end of the weld seam to avoid alarms due to failure to scan the seam when the welding is about to end. The welding parameters used in the DEMO are those finally saved on the Welding Parameter Configuration page. MovL(P1) -- Track the starting point WeldArcSpeed(10) WeldArcParams(1) CommonLaserTrackStart(1,0,1) -- Open the laser and start tracking MovL(P2,{speed=10}) -- Arc start point WeldArcStart() -- Start welding MovL(P3,{r=20}) -- Teach the seam trajectory, add "r" transition to ensure smooth trajectory MovL(P4,{r=20}) MovL(P5) WeldArcEnd() -- End welding CommonLaserTrackEnd() -- Close the laser and end tracking MovL(P6) -- Safety point

### A.6 Laser Positioning + Tracking (DEMO)

A.6.1 Script DEMO Take the workpiece in the above figure as an example, you need to teach two points. P1 is the photo point of the arc start point, teach P1 after aligning the laser to the start point. P2 is the photo point of the arc end point, teach P2 after aligning the laser to the start point. Then teach P3 as the posture reference point, which is used for referencing the welding torch posture as well as the user and tool coordinate system during welding. Teach P4 as the safety point after finishing the welding. For requirements such as the positional relationship between points and seams, please refer to the previous DEMO. MovL(P1) -- Aim the laser at the arc start point Wait(2000) -- Get coordinates of the positioning point local pos1 = LaserPositioning(P1,1) -- Use the coordinates of the positioning point and the posture of the posture reference point to splice into an absolute positioning point local absPos1 = {point = {pose = {pos1\[1], pos1\[2], pos1\[3], P3.pose\[4], P3.pose\[5], P3.pose\[6]\}}, user= P3.user, tool= P3.tool} MovL(P2) -- Laser aligns with arc end point Wait(2000) -- Get coordinates of the positioning point local pos2 = LaserPositioning(P2,1) -- Use the coordinates of the positioning point and the posture of the posture reference point to splice into an absolute positioning point local absPos2 = {point = {pose = {pos2\[1], pos2\[2], pos2\[3], P3.pose\[4], P3.pose\[5], P3.pose\[6]\}}, user= P3.user, tool= P3.tool} MovL(P1) CommonLaserTrackStart(1,0,1) -- Open the laser and start tracking -- Move to the arc start point MovL(absPos1.point, {user= absPos1.user, tool= absPos1.tool}) WeldArcSpeed(10) WeldArcParams(1) WeldArcStart() -- Start welding MovL(absPos2.point, {user= absPos2.user, tool= absPos2.tool}) -- Arc end point WeldArcEnd() -- End welding CommonLaserTrackEnd() -- Close the laser and end tracking MovL(P4) -- Safety point

### A.7 Multi-layer Multi-pass Welding Programming

A.7.1 Script commands

1. Command: WeldMultiPassStart(pass)

Description: Starts multi-layer multi-pass welding. The target point of the motion command between this command and WeldMultiPassEnd() will be offset based on the parameters of the specified pass. Parameter: “pass”: The channel number set in Multi-Layer Multi-Pass Welding Configuration. Example: WeldMultiPassStart(1)

2. Command: WeldMultiPassEnd()

Description: Ends multi-layer multi-pass welding. Example: WeldMultiPassEnd()

3. Command: PreMovL(P)

Description: If the welding trajectory after arc-start is linear, this command must be called to offset the arc-start point after calling the "WeldMultiPassStart" command and before moving to the arc-start point. For specific usage, refer to the DEMO below. Only when this command is correctly called will the robot move to the arc-start point for the corresponding weld pass. Otherwise, the robot will move to the arc-start point of the initial weld pass. Parameter: Target point for linear motion after the arc starts. Example: PreMovL(P1)

4. Command: PreArc(P1, P2)

Description: When the welding trajectory after arc-start is an arc, this command must be called to offset the arc-start point after calling the "WeldMultiPassStart" command and before moving to the arc-start point. For specific usage, refer to the DEMO below. Only when this command is correctly called will the robot move to the arc-start point for the corresponding weld pass. Otherwise, the robot will move to the arc- start point of the initial weld pass. Parameter: P1: The Intermediate point of the arc motion after arc-start. P2: The end point of the arc motion. Example: PreArc(P1, P2) A.7.2 Script DEMO This DEMO uses a three-layer linear-to-arc welding as an example. Create a project and teach the following points in the Points page:

* P1: Safety point before starting the welding.
* P2: Arc start point for the initial weld pass.
* P3: End point of the straight line for the initial weld pass.
* P4: Arc intermediate point of the initial weld seam
* P5: Arc end point of the initial weld seam (arc end point)
* P6: Safety point after ending the welding.

Then, in Multi-Layer Multi-Pass Welding Configuration, configure the channels for the second and third passes, with indices 1 and 2 respectively. The following figure shows a simple configuration example. Example: The welding parameters used in the DEMO are those finally saved on the Welding Parameter Configuration page. -- Initial weld pass, with weaving MovJ(P1) MovL(P2) WeldArcSpeed(10) WeldWeaveStart() WeldArcStart() MovL(P3) Arc(P4, P5) WeldArcEnd() WeldWeaveEnd() MoveL(P6) -- Second weld pass, without weaving MovJ(P1) WeldMultiPassStart(1) PreMovL(P3) -- Offset the arc start point MovL(P2) WeldArcStart() MovL(P3) Arc(P4, P5) WeldArcEnd() WeldMultiPassEnd() MoveL(P6) -- Third weld pass, without weaving MovJ(P1) WeldMultiPassStart(2)

PreMovL(P3) -- Offset the arc start point MovL(P2) WeldArcStart() MovL(P3) Arc(P4, P5) WeldArcEnd() WeldMultiPassEnd() MoveL(P6)

### A.8 TAST Programming

A.8.1 Script commands

1. Command: ArcTrackStart(index)

Description: Start through\_arc seam tracking. Repeated calling of this command is not allowed before calling ArcTrackEnd(). After starting tracking, the robot's trajectory (supports only linear and arc motion) will automatically be adjusted based on the tracking results. Parameter: "index": TAST parameter index. Example: ArcTrackStart(1)

2. Command: ArcTrackEnd()

Description: End through\_arc seam tracking. Example: ArcTrackEnd() A.8.2 Script DEMO MovL(P1) -- Approach point WeldArcSpeed(10) WeldArcParams(1) MovL(P2) -- Arc start point WeldWeaveStart() -- Enter the weaving mode, only supports Zigzag, Trapezoidal, Sine, or Crescent weaving. ArcTrackStart(1) -- Start through\_arc seam tracking WeldArcStart() -- Start welding MovL (P3) Arc End Point – WeldArcEnd() -- End welding ArcTrackEnd() -- End through\_arc seam tracking WeldWeaveStart() -- Exit the weaving mode. MovL(P4) -- Safety point

## Appendix B Modbus Register Data

The robot provides welding state and its own state information through Modbus communication protocol, which can be read and used by external equipment. An external device (e.g., a PLC or a client of a client system) acts as a Modbus master station, connected to a robot (slave station), and obtains the following two types of data by reading a specified Modbus register:

* Welding process data:

Including welding current, welding voltage and other information, regularly collected and updated in the holding register.

* Robot data:

After updating the welding process data, call the callback interface of the controller, trigger the controller to calculate the TCP (tool center point) speed of the robot, and update the result to the input register. Register Register Data length Stored data Description type address Welding voltage (voltage value fed V (one decimal 2400 int16 back in real time by place accuracy) the welder) Welding current (current value fed A (one decimal 2401 int16 Holding back by welder in place accuracy) register real time) Total welding time uint64 (accumulated welding time since 2402 – 2405 Read in little- the robot started ms endian operation; it can be reset). double Robot speed (end 2400 2403 Read in little- mm/s – speed) endian Power-on time uint64 Input (accumulated time register 1020–1023 Read in little- since the robot was ms endian powered on) int8 0 No alarm 1514 The high byte of Alarm Type 1 Alarm the register
