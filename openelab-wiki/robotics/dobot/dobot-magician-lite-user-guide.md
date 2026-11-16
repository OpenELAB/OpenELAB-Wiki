---
description: >-
  DobotLab-based user guide for the DOBOT Magician Lite educational robot,
  covering safety, robot fundamentals, setup, teaching, graphical programming,
  Python programming, firmware, calibration, and acc
---

# DOBOT Magician Lite User Guide

## DOBOT Magician Lite Educational Robot Arm

{% embed url="https://openelab.io/products/dobot-magician-lite-education-robot" %}

## DOBOT Magician Lite Sensor Kit for STEM Robotics

{% embed url="https://openelab.io/products/dobot-magician-lite-sensor-kit" %}

## Contents

* Preface
* Security Precautions
* Introduction
* Robot Connection
* Interface Description
* Operation

Copyright © ShenZhen Yuejiang Technology Co., Ltd 2022. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without prior written consent of Yuejiang Technology Co., Ltd. Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. Yuejiang makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non- infringement of third party rights. In no event will Yuejiang be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robotic arm is used on the premise of fully understanding the robotic arm and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. Dobot shall not be considered as a guarantee regarding to all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robotic arm. Shenzhen Yuejiang Technology Co., Ltd Address: Floor 9-10, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: en.dobot.cn

## Preface

Purpose This Document describes the working principle, technical specifications, connection and functions of Dobot Magician Lite, making it easy for users to fully understand and use Magician Lite. Intended Audience This document is intended for:

* Customer Engineer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Change History Date Change Description 2022/12/06 Added:

1. Added 10Pin communication cable wiring instructions in Chapter 3.
2. Added 12V 4Pin interface pin function description in Chapter 4.
3. Added AI camera usage tutorial in Chapter 5.

Modified: Updated the screenshots and instructions of the DobotLab software interface in Chapter 5. 2020/06/08 The first release Symbol Convention The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could

**DANGER**

result in death or serious injury Indicates a hazard with a medium level or low level of risk which, if not

**WARNING**

avoided, could result in minor or moderate injury, robotic arm damage Indicates a potentially hazardous situation which, if not avoided, can

**NOTICE result in robotic arm damage, data loss, or unanticipated result**

**NOTE Provides additional information to emphasize or supplement important**

points in the main text

## Security Precautions

This chapter describes the security precautions that should be noticed when using this product. Please read this document carefully before using the robotic arm for the first time. This product needs to be used in an environment meeting design specifications. You cannot remold the product without authorization, otherwise, it could lead to product failure, and even personal injury, electric shock, fire, etc. The installation personnel, operators, teaching personnel, and programmers must read this document carefully and use the robotic arm strictly according to the regulations of this document strictly.

### 1.1 General Security

**DANGER**

The robotic arm is electrical equipment. Non-professional technicians cannot modify the wire, otherwise, it is vulnerable to injury the device or the person. The following security rules should be followed when using the robotic arm.

* You should comply with local laws and regulations when operating the robotic arm. The security precautions in this document are only supplemental to local laws and regulations.
* The DANGER, WARNING, and NOTICE marks in this document are only supplemental to the security precautions.
* Please use the robotic arm in the specified environment scope. If not, exceeding the specifications and load conditions will shorten the service life of the product even damage the equipment.
* Before operating and maintaining the robotic arm, the personnel responsible for the installation, operation, and maintenance must be trained to understand the various security precautions and to master the correct methods of operation and maintenance.
* Highly corrosive cleaning is not suited to cleaning the robotic arm. The anodized components are not suitable for immersion cleaning.
* People cannot repair and disassemble the robotic arm without professional training. If there is a problem with the robotic arm, please contact Dobot technical support engineer in time.
* Please comply with the relevant laws to deal with the product which is scrapped, and protect the environment.
* There are small parts in the packing box. Please keep them away from children, to avoid any accidents.
* DO NOT let children play with the robotic arm alone. All processes need to be monitored while running. After processes have finished, please turn off the equipment promptly.
* DO NOT put hands into the workspace of the robotic arm while running, to avoid bruising
* Be careful during the robotic arm carrying or installing. Please follow the instructions on the packing box to put down the robotic arm gently and place it correctly in direction of the arrow.
* Commissioning of the incomplete machine is prohibited until it has been installed in a machine and the whole machine complies with the provisions of the Machinery Directive (2006/42/EC).
* It is prohibited to modify or remove the nameplates, instructions, icons, and marks on the robotic arm and the related equipment.
* Please refer to Magician Lite Quick Start along with the packing box before using it.

### Precautions

* Magician Lite was calibrated at the factory. By default, the coordinate of J1 axis is 0° after Magician Lite moving to the default homing point, i.e. The forearm is in the middle of the front of the base of Magician Lite.
* If the LED indicator turns red after starting up, it indicates that the Magician Lite is at a limited position. Please make the Magician Lite in the workspace.
* Magician Lite will move slowly to the specific position when shutdown. DO NOT put hands into the workspace of Magician Lite while running, to avoid bruising or pinching. Only once the LED indicator completely turns off, Magician Lite can be powered down.
* If the Magician Lite coordinate reading is abnormal during use, please press the forearm unlock button to correct the reading.
* Please turn off Magician Lite completely first before connecting or disconnecting external equipment, such as infrared sensor, color sensor, etc. Otherwise, it causes damage to your device.

## Introduction

### Overview

Magician Lite is a multifunctional desktop robotic arm for practical training education, supporting teaching and playback, blockly programming, script programming, writing and drawing, etc. It also supports secondary development by various extensible I/O interfaces in Magic Box, an external controller of Magician Lite. Magic Box separates motion control algorithm and user tasks, allowing more convenience for programming and creation. Magician Lite supports offline function, and it has 2 controllable power interfaces with 12V, 2 multi-functional communication interfaces, 6 universal IO interfaces, 2 stepper motor interfaces and several I2C interfaces. You can expand a wide range of sensors and related accessories to achieve more functions.

### Appearance

Magician Lite consists of a base, rear arm, forearm, and end-effector, etc., as shown in Figure 2.1.

_Figure 2.1 Appearance of Magician Lite_

### Working Principle

This section describes the workspace, principle, size and technical specifications of Magician Lite.

#### Workspace

_Figure 2.2 and Figure 2.3 shows the workspace of Magician Lite._

![Figure 2.1 Appearance of Magician Lite](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGYDtDkIWZbTiFWSbfkPB%2Fmagician-lite-p007-img06.jpg?alt=media)

_Figure 2.2 Workspace of Magician Lite (1)_

_Figure 2.3 Workspace of Magician Lite (2)_

#### Coordinate System

![Figure 2.2 Workspace of Magician Lite (1)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgHO18UB4UduJhB6570Id%2Fmagician-lite-p008-img02.jpg?alt=media)

![Figure 2.3 Workspace of Magician Lite (2)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsGzQutDhPVx2MoDMIZXl%2Fmagician-lite-p008-img03.png?alt=media)

Magician Lite has two types of coordinate systems, the joint one and the Cartesian one, as shown in Figure 2.4 and Figure 2.5 respectively.

_Figure 2.4 Joint coordinate system_

_Figure 2.5 Cartesian coordinate system_

Joint coordinate system: The coordinates are determined by the motion joints.

* If the end-effector with servo is installed, such as suction cup kit, gripper kit,

Magician Lite contains four joints: J1, J2, J3, and J4, which are all rotating joints. The positive direction of these joints is counter-clockwise. Cartesian coordinate system: The coordinates are determined by the base.

* The origin is the center of the three motors (rear arm, forearm, base).
* The direction of the X-axis is perpendicular to the base forward.
* The direction of the Y-axis is perpendicular to the base leftward.

![Figure 2.4 Joint coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBTkOjbfB1Po8TNNNNdXF%2Fmagician-lite-p009-img01.jpg?alt=media)

![Figure 2.5 Cartesian coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZ1YNGyYkOTOLiUf304hv%2Fmagician-lite-p009-img02.png?alt=media)

* The direction of the Z-axis is vertical upward, which is based on the right-hand rule.
* The R-axis is the posture of the servo center relative to the origin of the robotic arm, of which the positive direction is counter-clockwise. The R-axis only exists once the end-effector with servo is installed.

#### Motion Mode

The motion modes of Magician Lite include Jogging, Point to Point (PTP) and ARC.

**2.3.3.1 Jogging Mode**

Jogging mode is jogging Magician Lite to a point in Cartesian coordinate system or Joint coordinate system when teaching. Cartesian coordinate system mode:

* Click X+, X- and Magician Lite will move along X-axis in a positive or negative direction.
* Click Y+, Y- and Magician Lite will move along Y-axis in a positive or negative direction.
* Click Z+, Z- and Magician Lite will move along Z-axis in a positive or negative direction.
* Click R+, R- and Magician Lite will rotate along R-axis in a positive or negative direction.

**NOTICE**

If the end-effector with servo is installed on the Magician Lite, the R-axis will move together with Y-axis to make sure that the terminal posture relative to the origin stays constant. Joint coordinate system mode:

* Click J1+, J1- and control the base motor to rotate in a positive or negative direction.
* Click J2+, J2- and control the Rear Arm motor to rotate in a positive or negative direction.
* Click J3+, J3- and control the Forearm motor to rotate in a positive or negative direction.
* Click J4+, J4- and control the servo to rotate in a positive or negative direction.

**2.3.3.2 Point to Point (PTP)**

PTP mode, which means point to point movement, supports MOVJ, MOVL and JUMP. The trajectory of playback depends on the motion mode.

* MOVJ: Joint movement. From point A to point B, each joint will run from an initial angle

_Figure 2.6 MOVL/MOVJ mode_

* MOVL: Rectilinear movement. The joints will perform a straight line trajectory from point A to point B, as shown in Figure 2.6.
* JUMP: From point A to point B, the joints will move in MOVJ mode, of which the trajectory looks like a door, as shown in Figure 2.7. Move up to the lifting Height in MOVJ mode. Move horizontally to a point above B by Height. Move down to point B.

_Figure 2.7 JUMP mode_

**2.3.3.3 ARC**

The trajectory of ARC mode is an arc, which is determined by three points (the current point, any point on the arc and the end point), as shown in Figure 2.8.

**NOTICE**

In ARC mode, it is necessary to confirm the three points with other motion modes, and the three points cannot be in a line.

![Figure 2.6 MOVL/MOVJ mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4lTgKwMzAFrBZgf4cjFT%2Fmagician-lite-p011-img04.jpg?alt=media)

![Figure 2.7 JUMP mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlzxBdB8HdAW5zgIRPstx%2Fmagician-lite-p011-img05.png?alt=media)

_Figure 2.8 ARC mode_

**2.3.3.4 Application Scenarios**

The application scenario depends on the trajectory in a motion mode, as shown in Table 2.1.

_Table 2.1 Application scenario_

Motion mode Application scenario MOVL If the trajectory of playback is required as a straight line, you can choose MOVL MOVJ If the trajectory of playback is not required but high speed is required, you can choose MOVJ JUMP If the movement of two points is required to lift upwards by amount of height, such as sucking up, grabbing, you can choose JUMP ARC If the trajectory of playback is required as an arc, you can choose ARC

### Technical Specifications

#### Technical Parameters

_Table 2.2 Magician Lite technical parameters_

Name Magician Lite Maximum payload 250g Maximum reach 340mm J1 -135°\~135° J2 -5°\~80° Motion range J3 -10°\~85° J4 -145°~~145° Repeated positioning accuracy ±0.2 mm Power supply 100V~~240V AC, 50/60Hz

Power input 12V/5A DC Communication USB virtual serial /serial Software DobotLab Working temperature -5°C\~+45°C

_Table 2.3 Magic Box technical parameters_

Name Magic Box Control chip ARM 32-bit Cortex-M4 Frequency 168 MHz Power supply 100V~~240V AC, 50/60Hz Power in 12V/5A DC Working Temperature -5°C-45°C Capacity 60W Max Communication mode USB virtual serial/serial/Bluetooth Program language MicroPython Software DobotLab Weight 98g Size 95 mm×80 mm×21.5 mm Power interface 4 PIN, 12V/3A DC Multifunctional 10PIN, serial port communication interface Communication Interface General I/O expand Green port, 4PIN, 3.3V/5V-IO, 5V/1A-VCC, multiplexing interface interface Self-define I/O, AD, PWM output, I2C etc. Stepper motor expand Yellow port, 4PIN, 12V 1A Interface 12V power interface Red port, 2PIN, 12V, 3A max PWM Value range: 20Hz~~100KHz Value range: 0V\~5V ADC Accuracy: 12bit

#### Dimensions

_Figure 2.9 shows the size of Magician Lite and Figure 2.10 shows the size of the end mounting_

hole.

_Figure 2.9 Size of Magician Lite_

_Figure 2.10 Size of end mounting hole_

![Figure 2.9 Size of Magician Lite](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fup2wpwXkckh0raqoUAqp%2Fmagician-lite-p014-img01.png?alt=media)

![Figure 2.10 Size of end mounting hole](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlMcecprneLIXmbZbybqH%2Fmagician-lite-p014-img02.png?alt=media)

## Robot Connection

This section describes how to connect Magician Lite, and power it on/off.

### Connecting Cables to Magician Lite

When using Magician Lite without Magic Box, connect Magician Lite as below.

_Figure 3.1 Connect Magician Lite to your computer_

_Figure 3.2 Connect Magician Lite to the electrical outlet_

When using Magician Lite with Magic Box, connect the devices as below.

![Figure 3.1 Connect Magician Lite to your computer](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fk0o2pVGWN4Qy34WQEusY%2Fmagician-lite-p015-img19.jpg?alt=media)

![Figure 3.2 Connect Magician Lite to the electrical outlet](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYGX4nrUMtcXp60TJY7zy%2Fmagician-lite-p015-img20.jpg?alt=media)

_Figure 3.3 Connect Magician Lite to Magic Box_

**NOTICE**

When connecting the 10PIN communication cable, align the raised part of the plug with the groove on the interface to avoid reverse insertion. Figure 3.1 Connect the 10PIN communication cable

_Figure 3.4 Connect Magician Lite to electrical outlet_

![Figure 3.3 Connect Magician Lite to Magic Box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpqVeMkyT5nCHGp8yvEPK%2Fmagician-lite-p016-img03.jpg?alt=media)

![Figure 3.4 Connect Magician Lite to electrical outlet](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgpwG8hB3lo2tMIosuOfi%2Fmagician-lite-p016-img05.jpg?alt=media)

![Official manual figure, page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5uWTaLswoh0No98CMPAV%2Fmagician-lite-p016-img06.jpg?alt=media)

_Figure 3.5 Connect power adapter_

### Powering on/off Magician Lite

* Power on: Press the power button on Magician Lite or Magic Box, as shown in Figure

3.6. Once Magician Lite is powered on, all the stepper motors will be locked. You will hear a short beep sound, and the LED indicator turns green. Now Magician Lite is powered on.

![Figure 3.5 Connect power adapter](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkLVuo1bizBOV0jBBDNCC%2Fmagician-lite-p017-img04.jpg?alt=media)

![Figure 3.6 Power on Magician Lite](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2TTHzY5Ew1ZvMwxzUrmn%2Fmagician-lite-p017-img05.jpg?alt=media)

**NOTICE**

If the LED indicator is red after you power on Magician Lite, it means that Magician Lite reaches its limited position. To go back to the workspace, press and hold the Unlock button on the Forearm to move Magician Lite to another desired position After releasing the button the LED indicator turns green.

* Power off: When the LED indicator is green, press the power button to turn off Magician

Lite. In this case, the forearm moves slowly to the rear arm while the angle between them becomes small. Finally, the two arms reach a specific position.

**WARNING**

Watch your hand during the shutdown process.

## Interface Description

### Magician Lite Interface Description

The interfaces of Magician Lite are located on the back of the base. Figure 4.1 shows the interfaces on the back of the base, and Table 4.1 lists the description on the interfaces.

_Figure 4.1 Interfaces in the base_

_Table 4.1 Interface description_

No. Description 1 Power switch

* Short press: Power on Magician Lite
* Long press (>3s): Power off Magician Lite

2 Key

* Short press: Start running playback program in offline mode. For details about offline mode, refer to 5.9 Working in Offline Mode
* Long press (>2s): Start homing procedure. For details about homing, refer to 5.8 Homing

3 Power interface: Connect to power adaptor 4 12V power interface: Supply power to Magician Lite The 4 pins from left to right are external charging positive, GND, 12V, ON/OFF control 5 USB: Connect Magician Lite and PC 6 10PIN communication interface: Serial communication. For pin definitions, see 4.3

### Multiplexed I/O Interface Description

When wiring, pay attention to align the raised part of the plug with the groove on the interface to avoid reverse insertion The LED indicator is located on the base, Table 4.2 lists the description on its status.

![Figure 4.1 Interfaces in the base](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLAqSVtovsCquNk3KIutK%2Fmagician-lite-p019-img03.png?alt=media)

_Table 4.2 LED indicator description_

State Description Green on Magician Lite works normally Yellow on Magician Lite is in the starting status Blue on Magician Lite is in the offline mode Blue flashing Magician Lite is running homing procedure Red on • Magician Lite is at the limited position

* An alarm is not cleared

### Magic Box Interface Description

The Magic Box interface consists of 24 I/O multiplexing interfaces as well as communication interfaces that connect sliding rail, conveyor belts, joystick, sensors, etc., as shown in the figure below. The pin definition of the 12V power interface is the same as that of Magician Lite.

_Figure 4.2 Magic Box interfaces_

### Multiplexed I/O Interface Description

The addresses of the I/O interfaces in Magic Box are unified. Most of I/O interfaces have multiple functions to control the peripheral equipment.

_Figure 4.3 shows the communication interface of Magic Box, and Table 4.3 lists the description_

on multiplexed I/O.

![Table 4.2 LED indicator description](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5SIa4LiutK9PI00KPRO5%2Fmagician-lite-p020-img03.jpg?alt=media)

_Figure 4.3 Communication Interface 1_

_Figure 4.4 Communication Interface 2_

_Table 4.3 Magic Box multiplexed I/O description_

Level Whether Interface Pin Description PWM Level Input ADC Output Pulling undefined - - - - - - GND ground - - - - - General I/O 3.3V\_10mA 3.3V/5V\_10 EIO1 - - No pulling interface output mA input Communication Interface 1 General I/O 3.3V\_10mA 3.3V/5V\_10 EIO2 - - No pulling interface output mA input Pull up Firmware 3.3V\_10mA 3.3V\_10mA Reset 430R to reset output input 3.3V

![Figure 4.3 Communication Interface 1](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeW2EnBTnZE6NmwBHO0MX%2Fmagician-lite-p021-img01.png?alt=media)

![Figure 4.4 Communication Interface 2](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPgAJrA3DkJUK1Tp3gDUY%2Fmagician-lite-p021-img02.png?alt=media)

3.3V\_10mA Pull up General I/O 3.3V\_10mA EIO3 output - - 10K to interface input 3.3V General I/O 3.3V\_10mA 3.3V/5V\_10 EIO4 - - No pulling interface output mA input General I/O 3.3V\_10mA 3.3V/5V\_10 EIO5-No pulling interface output mA input 5V/1A 5V power - - - - output GND ground - - - - - undefined - - - - - - GND ground - - - - - General I/O 3.3V\_10mA 3.3V/5V\_10 EIO6 - - No pulling interface output mA input General I/O 3.3V\_10mA 3.3V/5V\_10 EIO7 - - No pulling interface output mA input Pull up Firmware 3.3V\_10mA 3.3V\_10mA Reset - - 430R to reset output input 3.3V Communication Pull up Interface 2 General I/O 3.3V\_10mA 3.3V\_10m EIO8 - - 10K to interface output input 3.3V General I/O 3.3V\_10mA 3.3V/5V\_10 EIO9 - - No pulling interface output mA input General I/O 3.3V\_10mA 3.3V/5V\_10 EIO10 - - No pulling interface output mA input 5V/1A 5V power - - - - output GND ground - - - - -

_Figure 4.5 Peripheral interface_

_Table 4.4 Peripheral multiplexed I/O description_

Whether Interface Pin Description Level Output PWM Level Input ADC Pulling Controlled 8V~~12.6V\_3A EIO12 - - - - power output SW1 GND Ground - - - - - Controlled 8V~~12.6V\_3A EIO11 - - - - power output SW2 GND Ground - - - - - 2\_1A - - - - 2\_1B - - - - STP1 8V\~12.6V/0.9A 2\_2A - - - - - output 2\_2B - - - - STP2 1\_1A - - - -

![Figure 4.5 Peripheral interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh5hh19dk3LG2d1xygmSO%2Fmagician-lite-p023-img01.png?alt=media)

1\_1B - - - - 1\_2A - - - - 1\_2B - - - - GND Ground - - - - - 5V Power 5V/1A - - - - General I/O 3.3V\_10m 3.3V\_10mA Pull up 51K Port1 EIO16 √ - interface output input to 3.3V General I/O 3.3V\_10m 3.3V\_10mA Pull up 51K EIO15 - - interface output input to 3.3V GND Ground - - - - - 5V Power 5V/1A - - - - General I/O 3.3V\_10mA 3.3V\_10mA Pull up 51K Port2 EIO13 √ - interface output input to 3.3V General I/O 3.3V\_10mA 3.3V\_10mA Pull up 51K EIO14 - - interface output input to 3.3V GND Ground - - - - - 5V Power - - - - - General I/O 3.3V\_10mA 3.3V\_10mA Port3 EIO23 √ - No pulling interface output input General I/O 3.3V\_10mA 3.3V\_10mA EIO24 - √ No pulling interface output input GND Ground - - - - - 5V Power - - - - - General I/O 3.3V\_10mA 3.3V\_10mA Port4 EIO21 √ - No pulling interface output input General I/O 3.3V\_10mA 3.3V\_10mA EIO22 - √ No pulling interface output input GND Ground - - - - - 5V Power 5V/1A output - - - - General I/O 3.3V\_10mA 3.3V\_10mA Pull up 51K Port5 EIO20 √ - interface output input to 3.3V General I/O 3.3V\_10mA 3.3V\_10mA Pull up 51K EIO19 √ - interface output input to 3.3V

5V Power 5V/1A output - - - - General I/O 3.3V\_10mA 3.3V\_10mA Pull up 51K EIO18 √ - interface output input to 3.3V General I/O 3.3V\_10mA 3.3V\_10mA Pull up 51K EIO17 √ - interface output input to 3.3V

## Operation

### Introduction on DobotLab

Dobot Magician Lite has multiple functions including teaching and playback, writing and drawing, blockly programming, script control, etc., which can be realized through DobotLab, an integrated software platform specially designed for artificial intelligence (AI) education. You can enter DobotLab through https://dobotlab.dobot.cc/. The main interface of DobotLab is shown in Figure 5.1, and its specific modules are described in Table 5.1.

_Figure 5.1 The function modules on the DobotDobotLab page_

_Table 5.1 The function modules on the DobotLab page_

No. Modules Description 1 Main page Click to return DobotLab main page 2 Menu Currency: View the guidance for the main page Help: View and download documents related to DobotLab Feedback: Enter your feedback about using DobotLab About: View the basic information of DobotLab

![Figure 5.1 The function modules on the DobotDobotLab page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fo7bjE9aUtZjmJ9j2Fggb%2Fmagician-lite-p026-img03.png?alt=media)

No. Modules Description 3 Language Choose a language (Chinese or English) 4 Login It supports new user registration. A registered user can log in using the account and password 5 My Course Provide free online courses 6 Personal Works View and edit the saved project 7 DobotBlock Lab Control the Dobot Magician Lite using blockly programming 8 Python Lab Control the Dobot Magician Lite using the script commands 9 Writing and Drawing Lab Control the Dobot Magician Lite to write and draw 10 Laser Engraving Lab Engrave a bitmap image on an object using a laser (only for Dobot Magician) 11 Teaching and Playback Lab Teach the Dobot Magician Lite how to move and then record the movement to make Dobot Magician Lite accomplish the recorded movements 12 3D Printing Lab Perform 3D printing (only for Dobot Magician) 13 Virtual Simulation Lab Simulate robot movements through programming, combined with a virtual scene and robot model

**NOTE**

DobotLink is the driver software of DobotLab hardware devices, which can achieve firmware upgrading and machine calibration. You need to install and run DobotLink before using the hardware devices. For details, see 5.2DobotLink.

### DobotLink Installation

As DobotLink is the driver software of DobotLab hardware devices, you need to install and run DobotLink before using the hardware devices. When DobotLab is started, if DobotLink is not installed or started, the “DobotLink is not started” window will be displayed, as shown below.

_Figure 5.2 Start DobotLink_

If you do not download DobotLink, click, and install it as prompted. If you have downloaded DobotLink, click. Now you will see two pop-up windows: “DobotLink failed to start” and “Open DobotLink?”, as shown below.

_Figure 5.3 DobotLink failed to start_

_Figure 5.4 Open DobotLink_

You need to click Open DobotLink. Now “DobotLink started successfully” is displayed.

![Figure 5.2 Start DobotLink](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd69KeAnIdez51ZStq2WR%2Fmagician-lite-p028-img01.jpg?alt=media)

![Figure 5.3 DobotLink failed to start](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiNaQm7wiUHzfSaUdz07E%2Fmagician-lite-p028-img04.png?alt=media)

![Figure 5.4 Open DobotLink](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9gjLPbenNHDBEzZre6um%2Fmagician-lite-p028-img05.png?alt=media)

_Figure 5.5 DobotLink started successfully_

### Blockly Programming

DobotBlock Lab is specially designed for beginners in programming. You can program by dragging blocks to control the movement of Dobot Magician Lite.

**Prerequisites**

Dobot Magician Lite has been powered on, and connected to DobotLab. Procedure

_Figure 5.6 Choose Magician Lite_

![Figure 5.5 DobotLink started successfully](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPy6GacvSyDKflChhwp5l%2Fmagician-lite-p029-img18.jpg?alt=media)

![Figure 5.6 Choose Magician Lite](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZbhAUeF6SbCpA6GFRwWA%2Fmagician-lite-p029-img21.png?alt=media)

_Figure 5.7 Add an extension_

**NOTE**

If you need to connect Magic Box when using Magician Lite, choose Magic Box in Step 2 after clicking. In addition, you need to choose Magician Lite in Step 3, as shown below.

_Figure 5.8 Choose Magic Box_

_Figure 5.9 Add Magician Lite_

![Figure 5.7 Add an extension](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsAlkqAkWgupTleVbg1m1%2Fmagician-lite-p030-img01.jpg?alt=media)

![Figure 5.8 Choose Magic Box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuimjREA8Ae7fb8R7o4hT%2Fmagician-lite-p030-img03.png?alt=media)

![Figure 5.9 Add Magician Lite](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5MCedX1zU9VSAPvZrpve%2Fmagician-lite-p030-img04.png?alt=media)

_Figure 5.10 Connect device_

_Figure 5.11 Device connected_

* Set parameters corresponding to each block based on actual requirements.
* The program written with blocks requires triggering conditions to run.

Therefore, you need to select a command from the event block as the triggering condition. For example, means the program starts to run once you click.

![Figure 5.10 Connect device](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3b0mVNbR4whll7SITgs9%2Fmagician-lite-p031-img15.png?alt=media)

![Figure 5.11 Device connected](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW4CyTlozOw09ij7o8aX2%2Fmagician-lite-p031-img16.jpg?alt=media)

_Figure 5.12 Blockly programming_

If you need to set sprites and stages in the program, follow Step 7\~ Step 10.

_Figure 5.13 Sprite list_

![Figure 5.12 Blockly programming](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1jJUgUK7lyib3Y9gcNDs%2Fmagician-lite-p032-img09.png?alt=media)

![Figure 5.13 Sprite list](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOUdfU2TAg49I3iaEZTok%2Fmagician-lite-p032-img11.jpg?alt=media)

_Figure 5.14 Sprite extension kit_

_Figure 5.15 Choose stage_

_Figure 5.16 Sprite programming_

![Figure 5.14 Sprite extension kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOB1C627NRN1TSLPuiJcx%2Fmagician-lite-p033-img06.png?alt=media)

![Figure 5.15 Choose stage](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtYFj49ED2e1YrpjzZldE%2Fmagician-lite-p033-img08.jpg?alt=media)

![Figure 5.16 Sprite programming](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCUQaS2WJGk2X6QLbJIez%2Fmagician-lite-p033-img09.png?alt=media)

### AI Camera Tutorial

#### Installing the camera

#### Image recognition

_Figure 5.17 New classification data_

![Figure 5.17 New classification data](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLm9Y0ekvPdHHvI73R3Zu%2Fmagician-lite-p034-img15.png?alt=media)

![Official manual figure, page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8V7TajwnSuSlbzTg39l6%2Fmagician-lite-p034-img16.png?alt=media)

_Figure 5.18 Get pictures and name them_

_Figure 5.19 Matching red_

![Figure 5.18 Get pictures and name them](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFfeMNKg3lkdr2uEFcBYh%2Fmagician-lite-p035-img08.jpg?alt=media)

![Figure 5.19 Matching red](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIv8vXkGBmAbSP5JJJDFB%2Fmagician-lite-p035-img09.jpg?alt=media)

_Figure 5.20 Matching blue_

_Figure 5.21 Matching yellow_

![Figure 5.20 Matching blue](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFJqpbL8RZ34ILHSIJCE7%2Fmagician-lite-p036-img09.jpg?alt=media)

![Figure 5.21 Matching yellow](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq2XMPmVOQ6vju4adWFpr%2Fmagician-lite-p036-img10.jpg?alt=media)

_Figure 5.22 Image recognition program_

**NOTICE**

* Classification points A, B, C can be set by the user according to the actual situation.
* To ensure that the suction cup holds the object accurately, please press and hold the unlock button on the forearm and drag the end until the suction cup is lightly pressed on the object, then fill the coordinates of the target point into the commands. Click to run the program, put wooden cubes of different colors under the camera, and observe the operation of the robotic arm.

![Figure 5.22 Image recognition program](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJs1ONhBj1x4D8zbW0B6h%2Fmagician-lite-p037-img01.png?alt=media)

#### Face recognition

_Figure 5.23 New face data_

_Figure 5.24 Get face pictures and name them_

![Figure 5.23 New face data](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK1gSzLHYRgY4vE4AyQJA%2Fmagician-lite-p038-img20.png?alt=media)

![Figure 5.24 Get face pictures and name them](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiJqv5d0Yww66qHz9joJc%2Fmagician-lite-p038-img22.jpg?alt=media)

_Figure 5.25 Finish training_

_Figure 5.26 Face recognition program_

#### OCR text/ID card recognition

OCR text recognition does not require model training, just put the text under the camera for recognition. According to the identification result of the ID card, if the name is "Sam", then recognize the text and move to a different position according to the text. The sample program is as follows.

![Figure 5.25 Finish training](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOYfkXbxGGv8tRndu6jAV%2Fmagician-lite-p039-img05.jpg?alt=media)

![Figure 5.26 Face recognition program](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhVm9W7Lx0rUcY6FUFs6X%2Fmagician-lite-p039-img06.png?alt=media)

_Figure 5.27 OCR recognition program_

### Python Programming

You can control Dobot Magician Lite through script. Magic Box provides various APIs, such as velocity/acceleration setting, motion mode setting, and I/O configuration, which uses Python language for secondary development. The main interface of Python Lab is shown in Figure 5.28, and the specific description is listed in Table 5.2.

_Figure 5.28 Python main page_

![Figure 5.27 OCR recognition program](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMwjuR1VvH9bJoPYQSqui%2Fmagician-lite-p040-img02.png?alt=media)

![Figure 5.28 Python main page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxQaoexHiWmkXXsHGkc6g%2Fmagician-lite-p040-img03.png?alt=media)

_Table 5.2 Python Lab main interface_

No. Function Description 1 Menu Currency: View the guidance for Python Lab Help: View the documents related to DobotLab and devices Feedback: Enter your feedback about DobotLab experience About: View the basic information on DobotLab 2 Home Back to DobotLab main page 3 File It includes functions such as new, open, save as, upload from local, etc. Import and Upload from Local can be used to open script files in Python Lab, but for Import, the file should be in.py format, and for Upload from Local, the file should be in.json format. The format requirements for Export and Save to Local are the same as Import and Upload from Local respectively. 4 Project name Display the name of the current project 5 Save Save the current project to My Works 6 Program control: Start to run the program in the code area: Download the current program in the code area to Magic Box (there is no such button when MagicianLite is connected separately): Install the Python extension library, after which you can call the functions in the extension library 7 Running: Display alarm information and logs. information: Display running process.: Clear all alarms. It has the same function as the "Clear Alarm" button in the alarm pop-up window.: Undo or redo an operation. 8 Device control: Select a target device and establish a communication connection with the device: Set common device types (only checked devices will be displayed in the drop-down box on the left when they are searched): Emergency stop button, press it to stop the robot in an emergency.: Click to open the control panel of the robotic arm, which can be used to control the movement of the robotic arm. 9 Command list Provide programming commands. You can double click the commands to display their corresponding codes in code area. Click to view the help documentation for the command. 10 Code area Edit programs using Python

**Prerequisites**

Dobot Magician Lite has been powered on and connected to DobotLab. Procedure

_Figure 5.29 Connect device_

_Figure 5.30 Device connected_

_Figure 5.31 Write Python programs_

![Figure 5.29 Connect device](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQg0v4dMd78V3QpLlO04s%2Fmagician-lite-p042-img17.png?alt=media)

![Figure 5.30 Device connected](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0jZfNDD3oe9yishhNm8x%2Fmagician-lite-p042-img19.png?alt=media)

_Figure 5.32 Save the project_

**NOTE**

The script can be downloaded from DobotLab to Magic Box only in wired control mode.

### Writing and Drawing

_Figure 5.33 shows the process of writing and drawing._

_Figure 5.33 The process of writing and draw_

![Figure 5.32 Save the project](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYxdm95je3egbTQldwqoT%2Fmagician-lite-p043-img13.png?alt=media)

![Figure 5.33 shows the process of writing and drawing.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyWwJMqqqZhHXtWUwS2qU%2Fmagician-lite-p043-img15.png?alt=media)

#### Installing a Writing and Drawing Kit

A writing and drawing kit consists of a pen and a pen holder. The specific installation steps are shown below.

_Figure 5.34 Install a writing and drawing kit_

**NOTE**

* If you need to change the ink tube, unscrew the suction tube inside the pen, and then replace it with the ink tube that came with the box. After replacement, keep the pen straight down for 2 minutes before using it, as shown in Figure 5.35.

_Figure 5.35 Change ink-straw_

* If you want to absorb ink, please remove pen-cap and rotate suction tube to absorb ink as shown in Figure 5.36.

![Figure 5.34 Install a writing and drawing kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgmJ6a80IBWY99ipGF2tY%2Fmagician-lite-p044-img09.jpg?alt=media)

![Figure 5.35 Change ink-straw](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIxHD1vsD7imX7OZI7fhD%2Fmagician-lite-p044-img10.jpg?alt=media)

![Official manual figure, page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgVlRLhIGprOxh1EjUgkQ%2Fmagician-lite-p044-img11.jpg?alt=media)

![Official manual figure, page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkPIUwf4rbNKLtnSrqVQP%2Fmagician-lite-p044-img12.jpg?alt=media)

_Figure 5.36 Absorb ink_

#### Drawing Operations (Without Sliding Rail)

**5.6.2.1 Connecting DobotLab**

_Figure 5.37 Connect device_

_Figure 5.38 Device connected_

**5.6.2.2 Importing Image Files and Setting Writing Parameters**

Before the Magician Lite starts to write and draw, you need to import an image or enter characters as the target model.

![Figure 5.36 Absorb ink](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F398ATJ9U9HbTzMSd8Qch%2Fmagician-lite-p045-img16.jpg?alt=media)

_Figure 5.39 Add text_

**NOTE**

The image in the drawing area should be placed within the annular area. If not, the robot arm reaches its limited position and cannot draw or write. In this case, the image is highlighted with a red border, as shown below.

_Figure 5.40 Image beyond bound_

![Figure 5.39 Add text](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3YzUaNpp20WYVAeKoBZj%2Fmagician-lite-p046-img11.png?alt=media)

![Figure 5.40 Image beyond bound](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzWdPd5aOx29vNna1tMQA%2Fmagician-lite-p046-img13.png?alt=media)

_Figure 5.41 Set pen lifting height, descent height and speed_

**NOTE**

Generally, you can set the pen lifting height and descent height to 20 by default.

_Figure 5.42_

_Figure 5.42 Adjust the pen nib_

**NOTE**

If you do not click Synchronize before running, the image can also be drawn normally.

![Figure 5.41 Set pen lifting height, descent height and speed](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FedIY6ETn6zXLCzQAF83u%2Fmagician-lite-p047-img11.png?alt=media)

![Figure 5.42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBJW9UmVG5yoo9DbS5Kb2%2Fmagician-lite-p047-img13.jpg?alt=media)

**5.6.2.3 Drawing**

_Figure 5.43 Drawing progress_

_Figure 5.44 Save the project_

**NOTE**

You can click Download to download the file to Magic Box to perform in offline mode. For details, refer to 5.9Working in Offline Mode.

#### Installing a Sliding Rail Kit

When the workspace of Dobot Magician Lite is not enough, you can extend the space with a

![Figure 5.43 Drawing progress](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjquw7wTsO76Yr7ISvjjY%2Fmagician-lite-p048-img18.jpg?alt=media)

![Figure 5.44 Save the project](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVLHJJHBAKoOM54U764Nb%2Fmagician-lite-p048-img19.png?alt=media)

Procedure

_Figure 5.45 Fix plate a_

_Figure 5.46 Fix Magician Lite_

![Figure 5.45 Fix plate a](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjzJpjNZid61crzQ2F3p9%2Fmagician-lite-p049-img18.jpg?alt=media)

_Figure 5.47 Connect to wire set_

_Figure 5.48 Connect to Magic Box_

_Figure 5.49 Interfaces on the other end of the wire set_

![Figure 5.47 Connect to wire set](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2T1luVSCFOzq4d7xuwWR%2Fmagician-lite-p050-img09.jpg?alt=media)

![Figure 5.48 Connect to Magic Box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FB8TJvN4ZFDuWgYgXzB79%2Fmagician-lite-p050-img10.png?alt=media)

![Figure 5.49 Interfaces on the other end of the wire set](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMkAn4scfvDhTROSyAHJi%2Fmagician-lite-p050-img11.png?alt=media)

_Figure 5.50 Connect sliding rail and wire set_

#### Drawing Operations (with a Sliding Rail)

This section describes how to use a sliding rail for writing.

**Prerequisites**

* The sliding rail kit has been installed and connected to the Dobot Magician Lite through

Magic Box.

* Dobot Magician Lite has been powered on and connected to DobotLab successfully.
* The writing kit has been installed.

**5.6.4.1 Connecting DobotLab**

_Figure 5.51 Connect device_

![Figure 5.50 Connect sliding rail and wire set](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKoxhjwRqrNEJRIIUvzZH%2Fmagician-lite-p051-img11.jpg?alt=media)

_Figure 5.52 Device connected_

**5.6.4.2 Connecting Sliding Rail**

_Figure 5.53 Enable sliding rail_

![Figure 5.52 Device connected](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQWBJJdf1WxFkk1c43Tuw%2Fmagician-lite-p052-img12.png?alt=media)

![Figure 5.53 Enable sliding rail](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS2s1cee5leMFHI38NWPI%2Fmagician-lite-p052-img13.png?alt=media)

**NOTICE**

Before you click Home, please take the pen off or raise the Dobot Magician Lite arm up.

**5.6.4.3 Importing Image/Text and Setting Parameters**

_Figure 5.55 Add image_

If you need to insert an image, click to select an image from local. If the image format is not SVG, the SVG Format Conversion prompt box will pop up. In this case, select the conversion scale and click OK.

**NOTE**

* The image in the drawing area should be placed within the rectangular area and should not touch the boundary line or any separator line. Otherwise, the robot arm reaches its limited position and cannot draw or write. In this case, the image is highlighted with a red border.

![Figure 5.55 Add image](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI8v8zXYkJnfnNWljs3PC%2Fmagician-lite-p053-img18.png?alt=media)

_Figure 5.56 Touch separator line_

* If the coordinate system of the imported image and the drawing area are set differently, the imported image will be displayed in an inverted direction. In this case, you can flip the image to the correct direction.
* If you want to write the text in a certain order, you need to import an image with a defined point order. If you enter the text through Add Text, the Magician will write the text overall from left to right.

_Figure 5.57 Set pen lifting height, descent height and speed_

![Figure 5.56 Touch separator line](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6tkx7lcBphBMaRH5whF9%2Fmagician-lite-p054-img12.png?alt=media)

_Figure 5.58 Height of brush pen_

**NOTICE**

If you want to set an action to dip the pen into the ink, you can press Unlock key and drag the Magician Lite to a point, and then release the key to get this position.

1. Right-click a position on the drawing area and select Add Trigger Line, as

shown in Figure 5.59.

_Figure 5.59 Add trigger line_

A blue trigger line appears in the drawing area. Move the trigger line to a proper position, as shown in Figure 5.60.

![Figure 5.58 Height of brush pen](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FigfReeCvSDb7Ykcjy69z%2Fmagician-lite-p055-img05.jpg?alt=media)

![Figure 5.59 Add trigger line](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkwuHL3bb3dYXZBA4gZvs%2Fmagician-lite-p055-img08.png?alt=media)

_Figure 5.60 Move trigger line_

2. Click to enter the “Trigger Trajectory” page for setting ink

dipping actions, as shown in Figure 5.61.

_Figure 5.61 Trigger line page_

3. Press the Unlock key on the forearm, move the forearm over the drawing area,

and release the Unlock key to record the first point. as shown in Figure 5.62.

_Figure 5.62 Save the first point_

![Figure 5.60 Move trigger line](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuyaUsBxEUnNCDPYV6epI%2Fmagician-lite-p056-img01.jpg?alt=media)

![Figure 5.61 Trigger line page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgvVVaJLemeKwGy1wvkoU%2Fmagician-lite-p056-img03.png?alt=media)

![Figure 5.62 Save the first point](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxmH2zO3TJPUmgp4sxX9t%2Fmagician-lite-p056-img04.jpg?alt=media)

**NOTICE**

Make this point higher within the workplace of Magician Lite to prevent the writing brush from touching the inkstone.

4. Move the forearm to the inkstone positions shown in Figure 5.63, and record

these points on the “Trigger Trajectory” page.

_Figure 5.63 Simulate the actions of ink dipping_

5. Drag the forearm to raise the writing brush up, for avoiding touching the

inkstone.

**NOTICE**

As the inkstone has its own height, you need to set a suitable rising height to prevent the writing brush from touching the inkstone. Click Settings to set the height that is recommended as 50mm to 70mm.

**NOTE**

If you do not click Synchronize before running, the text can also be written normally. After you click Run, the robot arm moves directly over the starting point to draw.

**5.6.4.4 Drawing**

![Figure 5.63 Simulate the actions of ink dipping](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F79lx1K1PfcriypsyhrLN%2Fmagician-lite-p057-img10.png?alt=media)

_Figure 5.64 Start writing text_

_Figure 5.65 Save the file_

### Teaching and Playback

This section introduces how to perform a teaching & playback task to suck or grab an object.

#### Installing a Suction Cup Kit

Magician Lite has a built-in air pump, and its end-effector is suction cup by default, as shown in Figure 5.66.

![Figure 5.64 Start writing text](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHdb6CJUgr9kcS3kSfi17%2Fmagician-lite-p058-img12.png?alt=media)

_Figure 5.66 Suction cup kit_

Procedure

_Figure 5.67 Install a suction cup kit_

![Figure 5.66 Suction cup kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPQKLdy4nmuYGKuoFImuP%2Fmagician-lite-p059-img11.png?alt=media)

![Figure 5.67 Install a suction cup kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fk0UMgq6zTSZiQ8fQbzjK%2Fmagician-lite-p059-img12.jpg?alt=media)

_Figure 5.68 Install an air tube_

#### Installing a Gripper Kit

An air pump should be used with the gripper kit, as shown in Figure 5.69, to open or close the gripper.

_Figure 5.69 Gripper kit_

Install the gripper kit to Magician Lite in the same way as the suction cup kit is installed. For details, refer to 5.7.1 Installing a Suction Cup Kit. Figure 5.70 shows the effect of the gripper kit installation.

![Figure 5.68 Install an air tube](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRM6Vcy8BLc065D1B9iNM%2Fmagician-lite-p060-img02.jpg?alt=media)

![Figure 5.69 Gripper kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff8X8an4uQ0wP5oDB0JHc%2Fmagician-lite-p060-img03.jpg?alt=media)

_Figure 5.70 Effect of the gripper kit installation_

#### Teaching & Playback Operation

The main interface of Teaching and Playback Lab is shown in Figure 5.71, and the specific description is listed in Table 5.3.

_Figure 5.71 Teaching and Playback Lab interface_

_Table 5.3 Description on Teaching and Playback Lab_

No. Modules Description 1 Menu Currency: View the guidance for Python Lab Help: View the documents related to DobotLab and devices Feedback: Enter your feedback about DobotLab experience

![Figure 5.70 Effect of the gripper kit installation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3bErxkCVjQ3OFjBQSjG1%2Fmagician-lite-p061-img02.jpg?alt=media)

![Figure 5.71 Teaching and Playback Lab interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvOFJliiozXHo3aUtaFuH%2Fmagician-lite-p061-img03.png?alt=media)

No. Modules Description About: View the basic information on DobotLab 2 Home Back to DobotLab main page 3 File It includes functions such as new, open, save as, upload from local, etc. 4 Project name Display the name of the current project 5 Save Save the current project to My Works 6 Program control: Start to run the program in the code area: Download the current program in the code area to Magic Box (there is no such button when MagicianLite is connected separately) 7 Running Settings: Set speed and acceleration settings Loop: Set the number of times the commands run. Value range: 1\~999999 8 Log & Undo: Display alarm information and logs.: Undo an operation. 9 Device control: Select a target device and establish a communication connection with the device: Set common device types (only checked devices will be displayed in the drop- down box on the left when they are searched): Emergency stop button, press it to stop the robot in an emergency.: Click to open the control panel of the robotic arm, which can be used to control the movement of the robotic arm. 10 Command area Display added commands. You can right-click a command to copy, paste, or delete it 11 Command panel Set motion mode, save points, pause time, end effector, lost-step detection, and I/O trigger Procedure

_Figure 5.72 Connect device_

_Figure 5.73 Device connected_

![Figure 5.72 Connect device](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwfUmjvxDiPwDQ2qz34sU%2Fmagician-lite-p063-img25.png?alt=media)

![Figure 5.73 Device connected](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbMST5iiHY2Yh9Odcb5ON%2Fmagician-lite-p063-img27.png?alt=media)

_Figure 5.75 Jump parameter setting_

_Figure 5.76 Arc point setting_

![Figure 5.75 Jump parameter setting](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FN6YyXPe0wKfI1uAoKkat%2Fmagician-lite-p064-img08.png?alt=media)

![Figure 5.76 Arc point setting](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ffh3frPdpQC6LAduKCVyD%2Fmagician-lite-p064-img09.png?alt=media)

_Figure 5.77 Arc point saving command_

**NOTICE**

Note the following rules when saving points to prevent the robotic arm from working outside its normal workspace.

* Any two points cannot coincide.
* The three points cannot be in the same straight line.
* The arc trajectory cannot exceed the normal workspace of Dobot Magician

Lite.

_Figure 5.78 Save the project_

### Homing

When Magician Lite executes homing operation, it just returns to the home position without calibrating the accuracy. If Magician Lite has been hit or the motor has lost steps, you need to press the Unlock button on the forearm to restore the encoder value and improve the positioning accuracy.

**Prerequisites**

Dobot Magician Lite has been powered on, and connected to DobotLab. Procedure Click Home on the Arm Control Panel of DobotLab, as shown in Figure 5.79..

_Figure 5.79 Click Home_

![Figure 5.78 Save the project](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzBQXiJf1AxXpz50oKqlR%2Fmagician-lite-p066-img12.jpg?alt=media)

**NOTICE**

* Please remove the end-effector from Magician Lite before homing.
* Please ensure that there are no obstacles within the workspace during homing.

Magician Lite will rotate to the default homing point automatically and the LED indicator on the base flashes blue. After the homing is successful, there is a beep sound and the LED indicator turns green. The homing point can also be user-defined. You can right-click a saved point in the command area of Teaching and Playback Lab and click Set Home to set this saved point as the homing point, as shown in Figure 5.80.

_Figure 5.80 Set homing point_

### Working in Offline Mode

Offline mode allows the Magician Lite to perform the points in the Save points list that you have downloaded from DobotLab to Magic Box, without keeping the USB connection established.

**Prerequisites**

* Magic Box + Magician Lite has been powered on.
* Magic Box + Magician Lite has been connected to DobotLab.
* The points have been saved.

Procedure

![Figure 5.80 Set homing point](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVaFPZ9mxSERAZfBdYVY4%2Fmagician-lite-p067-img07.png?alt=media)

_Figure 5.81 Confirm whether returning to the home point_
