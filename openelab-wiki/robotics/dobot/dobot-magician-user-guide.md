---
description: >-
  User guide for the DOBOT Magician desktop robot, covering safety, setup,
  DobotStudio operation, teaching and playback, writing and drawing, laser
  engraving, 3D printing, Blockly, scripting, and access
---

# DOBOT Magician User Guide

## DOBOT Magician Desktop Robot Arm for Education

{% embed url="https://openelab.io/products/dobot-magician-education-robot-arm" %}

## DOBOT Magician Sensor Kit for Robotics Education

{% embed url="https://openelab.io/products/dobot-magician-sensor-education-kit" %}

## Contents

* Preface
* Security Precautions
* Quick Start
* Introduction
* Interface Description
* Operation
* operation
* Appendix A Dobot Magician Homing Operation

Copyright © ShenZhen Yuejiang Technology Co., Ltd 2020. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without prior written consent of Yuejiang Technology Co., Ltd Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. Yuejiang makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non- infringement of third party rights. In no event will Yuejiang be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robotic arm is used on the premise of fully understanding the robotic arm and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, Damages or losses will be happen in the using process, Dobot shall not be considered as a guarantee regarding to all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robotic arm. Shenzhen Yuejiang Technology Co., Ltd Address: 3F, Building NO.3, Tongfuyu Industrial Town, Nanshan District, Shenzhen, China Website: www.dobot.cc

## Preface

Purpose This Document describes the functions, technical specifications, installation guide and system commissioning of Dobot Magician, making it easy for users to fully understand and use it. Intended Audience This document is intended for:

* Customer Engineer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Change History Date Change Description 2020/07/22 Delete Sliding chapter Update pictures based on V2 Dobot Magician 2018/09/11 Update the connection figure between Dobot Magician and sliding rail 2018/06/12 The first release Symbol Conventions The symbols that may be founded in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not

**DANGER avoided, could result in death or serious injury**

Indicates a hazard with a medium level or low level of

**WARNING risk which, if not avoided, could result in minor or**

moderate injury, robotic arm damage Indicates a potentially hazardous situation which, if not

**NOTICE avoided, can result in robotic arm damage, data loss, or**

unanticipated result

**NOTE Provides additional information to emphasize or**

supplement important points in the main text

## Security Precautions

This topic describes the security precautions that should be noticed when using this product. Please read this document carefully before using the robotic arm for the first time. This product need to be carried out in an environment meeting design specifications, you cannot remold the product without authorization, otherwise it could lead to product failure, and even personal injury, electric shock, fire, etc. The installation personnel, operators, teaching personnel, and programmers of the robotic arm must read this document carefully and use the robotic arm strictly according to the regulations of this document strictly.

### 1.1 General Security

**DANGER**

Robotic arm is an electrical equipment. Non-professional technicians cannot modify the wire, otherwise it is vulnerable to injury the device or the person. The following security rules should be followed when using the robotic arm.

* You should comply with local laws and regulations when operating the robotic arm. The security precautions in this document are only supplemental to local laws and regulations.
* The DANGER, WARNING, and NOTICE marks in this document are only supplemental to the security precautions.
* Please use the robotic arm in the specified environment scope. If not, exceeding the specifications and load conditions will shorten the service life of the product even damage the equipment.
* Before operating and maintaining the robotic arm, the personnel responsible for the installation, operation and maintenance must be trained to understand the various security precautions and to master the correct methods of operation and maintenance.
* Highly corrosive cleaning is not suited to cleaning the robotic arm. The anodized components are not suitable for immersion cleaning.
* People cannot repair and disassemble the robotic arm without professional training. If there is a problem with the robotic arm, please contact Dobot technical support engineer in time.
* Please comply with the relevant laws to deal with the product which is scrapped, and protect the environment.
* There are small parts in the packing box, Please keep them away from children, to avoid any accidents.
* DO NOT let children play with the robotic arm alone. All processes need to be monitored while running. After processes have finished, please turn off the equipment promptly.
* DO NOT put hands into the workspace of the robotic arm while running, to avoid bruising or pinching.
* Be careful during the robotic arm carrying or installing. Please follow the instructions on the packing box to put down the robotic arm gently and place it correctly in direction of arrow.
* Commissioning of the incomplete machine is prohibited until it has been installed in a machine and the whole machine complies with the provisions of the Machinery Directive (2006/42/EC).
* It is prohibited to modify or remove the nameplates, instructions, icons and marks on the robotic arm and the related equipment.
* Please refer to Dobot Magician User Guide along with the packing box before using.

### Precautions

* Please make the Dobot Magician in the workspace with a 45° angle between the Forearm and Rear Arm (as shown in Figure 1.1) before starting up. If the LED indicator turns red after starting up, it indicates that the Dobot Magician is at a limited position. Please make the Dobot Magician in the workspace.

_Figure 1.1 The Forearm and Rear Arm position_

* Dobot Magician will move slowly to the specific position when shutdown. DO NOT put hands into the workspace of the Dobot while running, to avoid bruising or pinching. Only once the LED indicator completely turns off, the Dobot Magician can be powered down.
* If the coordinates of the Dobot Magician shown on the DobotStudio are abnormal, please press the Reset button on the back of the base to reset Dobot Magician or click Home on the DobotStudio page to perform homing.
* During resetting, Dobot Magician will disconnect from the PC automatically and the

LED indicator on the base turns yellow. About 5 seconds later, if the LED indicator turns green, it indicates that the reset is successful.

* During homing, Dobot Magician will rotate clockwise to the limited position and then return to the homing point automatically, and the LED indicator on the base turns blue and is blinking. After homing, if there is a beep sound and the LED indicator turns green, it indicates that the homing is successful.
* Please turn off the Dobot Magician completely first before connecting or disconnecting external equipment, such as Bluetooth, WIFI, stick controller, infrared sensor, color sensor, etc. Or, it causes damage to your device.

![Figure 1.1 The Forearm and Rear Arm position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FR3EgrOc1vVVKG8g9KwiG%2Fmagician-p007-img02.jpg?alt=media)

* Please wear the lasing protective eyeglass when using the laser module. Please protect your eyes and skin from the laser.
* The heating rod will produce high temperature up to 250℃ when using the 3D printing module, please be careful.
* Please DO NOT operate or turn off Dobot Magician when burning firmware, to avoid machine damage.

## Quick Start

This topic briefly describes how to operate the Dobot Magician with the software DobotStudio, allowing you to quickly know and use the robotic arm. Figure 2.1 shows the process of getting started with the Dobot Magician.

_Figure 2.1 The process of getting started with the Dobot Magician_

### Connecting Cables to the Dobot Magician

![Figure 2.1 The process of getting started with the Dobot Magician](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fg0ANbOkWC9steptDKD9d%2Fmagician-p009-img08.png?alt=media)

_Figure 2.2 Connect the Dobot Magician to your computer_

### Installing the DobotStudio

You can control Dobot Magician by DobotStudio to implement functions such as Teaching & Playback, fully programmable applications, and 3D printing. This topic introduces Teaching & Playback.

#### System Requirements

The DobotStudio supports the following Windows and macOS versions.

* Windows 7, Windows 8, and Windows 10 (This manual is explained based on this version)
* macOS 10.10, macOS 10.11, and macOS 10.12

#### Obtaining the DobotStudio Package

Before using Dobot Magician, download the Windows DobotStudio package from https://www.dobot.cc/downloadcenter.html. The macOS version is also downloadable in this URL.

### Installing the DobotStudio

Prerequisites The DobotStudio package has been obtained. Procedure

![Figure 2.2 Connect the Dobot Magician to your computer](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fr3PAePm3ML51SVOOylNX%2Fmagician-p010-img11.png?alt=media)

For example, this directory is Installation Directory\DobotStudio. You can install the DobotStudio to another location based on site requirements. In the installation directory double-click DobotStudioSetup.exe. The Select Setup Language dialog box is displayed, as shown in Figure 2.3.

_Figure 2.3 The Select Setup Language dialog box_

_Figure 2.4 Select English_

During the installation, the Driver Installation dialog box is displayed,, two drivers needs to be installed, as shown in Figure 2.5.

![Figure 2.3 The Select Setup Language dialog box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd5JcKVT0JhdzHOuItsHh%2Fmagician-p011-img16.jpg?alt=media)

When the drivers are installed successfully, the Completing the Device Driver Installation Wizard dialog box is displayed. Click Finish,as shown in Figure 2.6.

_Figure 2.6 The Completing the Device Driver Installation Wizard dialog box_

When the installation is complete, the Completing the DobotStudio Setup Wizard dialog box is displayed. Click Finish, as shown in Figure 2.7.

_Figure 2.7 The Completing the DobotStudio Setup Wizard dialog box_

#### Verifying the Installation

![Figure 2.6 The Completing the Device Driver Installation Wizard dialog box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMJQCzTJHTtQAA1BoRLRp%2Fmagician-p012-img17.png?alt=media)

![Figure 2.7 The Completing the DobotStudio Setup Wizard dialog box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKSq83co9xPx4IPCCNOTV%2Fmagician-p012-img18.png?alt=media)

**2.2.4.1 Verifying the DobotStudio**

If the DobotStudio is launched and runs properly by double-clicking the desktop shortcut to this program, it means that it is installed successfully.

**2.2.4.2 Verifying the Dobot Magician Driver**

If an available COM port is displayed on the upper left corner of the DobotStudio page after the robotic arm is powered on, as shown in Figure 2.8, the Dobot Magician driver is installed successfully.

_Figure 2.8 An available COM port is displayed_

If no COM port is available, check whether the robotic arm driver is successfully installed by following the steps below.

![Figure 2.8 An available COM port is displayed](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FabknsLuqhPW0v8yWbjh5%2Fmagician-p013-img19.jpg?alt=media)

_Figure 2.9 The V2 robotic arm driver in Device Manager window_

_Figure 2.10 The V1 robotic arm driver in Device Manager window_

**NOTE**

* To reinstall the Dobot Magician driver after uninstalling it, install the driver corresponding to the Windows version in the directory Installation Directory\DobotStudio\attachment\Drive\HardwareV1.0.0. For example, install the 64-bit driver on a 64-bit Windows 10, as shown in Figure 2.11.

![Figure 2.9 The V2 robotic arm driver in Device Manager window](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOKEyzpF1uWGYz2OyRidr%2Fmagician-p014-img01.png?alt=media)

![Figure 2.10 The V1 robotic arm driver in Device Manager window](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGHO1COyNe5PaQiaVPmlF%2Fmagician-p014-img02.png?alt=media)

_Figure 2.11 Install the 64-bit driver on a 64-bit Windows 10_

* If the DobotStudio hardware version is 0.0.0, install the driver matching the

Windows version in the directory: Installation Directory\DobotStudio\attachment\Drive\HardwareV0.0.0. Please connect the DobotStudio to the robotic arm and then click to check the hardware version.

### Powering On/Off the Dobot Magician

* Power on: align the Dobot Magician into its neutral position with its Forearm and

Rear Arm constructing a 45-degree angle, and press down the power button in the base, as shown in Figure 2.12. Once the robotic arm is powered on, the LED indicator turns yellow, and all the stepper motors lock. And then wait about seven seconds, a short beep sound will be heard, and the LED indicator turns from yellow to green. Now the Dobot Magician is ready to use.

**NOTICE**

If the LED indicator is red after powering on the Dobot Magician, it means that the robotic arm reaches its limited position. To go back to the workspace, press and hold the unlock button on the Forearm to move the robotic arm to another desired position After releasing the button the LED indicator turns green.

![Figure 2.11 Install the 64-bit driver on a 64-bit Windows 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPFhUsrmKWeJnceNBLHsD%2Fmagician-p015-img02.png?alt=media)

_Figure 2.12 The gesture of Dobot Magician before power-on_

* Power off: When the LED indicator is green, press down the power button to turn off the robotic arm. In this case, the Forearm moves slowly to the Rear Arm while the angle between them becomes small. Finally, the two arms reach a specific position.

**WARNING**

During the shutdown process, watch your hand.

### Getting Started

This topic describes how to use the Dobot Magician to complete the teaching & playback function by saving three points in the MOVJ mode, allowing you to get the basic knowledge of the usage of the robotic arm. Prerequisites

* The DobotStudio has been installed. For details, see 2.2 Installing the DobotStudio.
* The Dobot Magician is powered on. For details, see 2.3 Powering On/Off the Dobot

Magician. Procedure The DobotStudio page with its beginner guide is displayed, as shown in Figure 2.13.

![Figure 2.12 The gesture of Dobot Magician before power-on](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkmfwwG0nnCeoyVR7hsnG%2Fmagician-p016-img04.jpg?alt=media)

_Figure 2.13 The DobotStudio page with a beginner guide_

**NOTE**

After reading the beginner guide of the DobotStudio, click to close it. The Question dialog box is displayed, as shown in Figure 2.15.

_Figure 2.14 Click Connect_

_Figure 2.15 The Question dialog box_

![Figure 2.13 The DobotStudio page with a beginner guide](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTGeyyvng6GF5azr2y5Zh%2Fmagician-p017-img10.jpg?alt=media)

![Figure 2.14 Click Connect](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F919oaQPieEouqyYRObpM%2Fmagician-p017-img14.png?alt=media)

Because this section is for quick access to the Dobot Magician only and no high accuracy is required. When Connect changes to Disconnect, it means that the DobotStudio is connected to the Dobot Magician.

**NOTE**

To achieve a high accuracy of the robotic arm, click Wait Link.

1. Click Teaching & Playback, as shown in Figure 2.16.

_Figure 2.16 Click Teaching & Playback_

**NOTE**

After reading a beginner guide on the Teaching & Playback page, as shown in Figure 2.17, click to close it.

![Figure 2.16 Click Teaching & Playback](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTZRoHzaxLZUycumjbOLH%2Fmagician-p018-img03.jpg?alt=media)

_Figure 2.17 Teaching & Playback page_

2. Select PTP Point > MOVJ mode in the Save Point area, as shown in Figure

2.18.

_Figure 2.18 Select MOVJ motion mode_

3. Press and hold the unlock button on the Forearm to move the robotic arm

to a position such as point A, and then release the button. In this case, the DobotStudio will save the Cartesian coordinate of point A, as shown in Figure 2.19.

![Figure 2.17 Teaching & Playback page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQuAqAzlvWesUkaTxfd3o%2Fmagician-p019-img02.jpg?alt=media)

_Figure 2.19 The Cartesian coordinate of point A_

**NOTE:**

Apart from hand-guided teaching, you can accomplish a teaching task by jogging the Dobot Magician in the Cartesian or Joint coordinate system, as shown in Figure 2.20.

_Figure 2.20 Jog the Dobot Magician in the Cartesian or Joint coordinate system_

![Figure 2.19 The Cartesian coordinate of point A](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFP85OW384BncfNyYK6Z4%2Fmagician-p020-img01.jpg?alt=media)

![Figure 2.20 Jog the Dobot Magician in the Cartesian or Joint coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOF1R0FqNcfezUOdd82FU%2Fmagician-p020-img02.jpg?alt=media)

4. Move the robotic arm to other two locations such as points B and C by referring

to the method of creating point A above, as shown in Figure 2.21. The robotic arm will save the Cartesian coordinates corresponding to these two points.

_Figure 2.21 The Cartesian coordinates of points B and C_

5. Enter 3 in Loop text box.

The robotic arm will repeat the sequence of movements for three times, as shown in Figure 2.22.

_Figure 2.22 Enter 3 in the Loop text box_

6. Click Start to perform the motions taught above, as shown in Figure 2.23.

The robotic arm will stop after playing back the steps for three times.

![Figure 2.21 The Cartesian coordinates of points B and C](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FY9SKXHaWotAkCjhIcF0L%2Fmagician-p021-img01.png?alt=media)

![Figure 2.22 Enter 3 in the Loop text box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIAxlYgkxckbXQtMsoBbq%2Fmagician-p021-img02.png?alt=media)

_Figure 2.23 Click Start_

7. Click to exit the Teaching & Playback page.

![Figure 2.23 Click Start](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjfdE4vkXMucYU8qjdN4Y%2Fmagician-p022-img01.png?alt=media)

## Introduction

### Overview

Dobot Magician is a multifunctional desktop robotic arm for practical training education, supporting teaching and playback, blockly graphic programming, script, etc. Installed with different end-effectors, Dobot Magician can realize interesting functions such as 3D printing, laser engraving, writing and drawing. It also supports secondary development by various extensible I/O interfaces, which really makes your creativity and imagination increase without any limitation.

### Appearance and Constitute

Dobot Magician consists of Abase, Rear Arm, Forearm, and end-effector, etc. Figure 3.1 shows the appearance.

_Figure 3.1 The appearance of Dobot Magician_

### Working Principle

This topic describes the workspace, principle, size and technical specifications of Dobot Magician.

#### Workspace

_Figure 3.2 and Figure 3.3 shows the workspace._

![Figure 3.1 The appearance of Dobot Magician](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDPzY2MztAJb6NzP5etbs%2Fmagician-p023-img06.png?alt=media)

_Figure 3.2 Workspace of Dobot Magician (1)_

_Figure 3.3 Workspace of Dobot Magician (2)_

![Figure 3.2 Workspace of Dobot Magician (1)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvMb0u7wvlWxeCkmJZLbi%2Fmagician-p024-img01.png?alt=media)

![Figure 3.3 Workspace of Dobot Magician (2)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwY8fRQBBqy0DOHIUJym5%2Fmagician-p024-img02.png?alt=media)

#### Coordinate System

Dobot Magician has two types of coordinate system, the joint one and the Cartesian one, as shown in Figure 3.4 and Figure 3.5 respectively.

_Figure 3.4 Joint coordinate system_

_Figure 3.5 Cartesian coordinate system_

* Joint coordinate system: The coordinates are determined by the motion joints.
* If the end-effector is not installed, Dobot Magician contains three joints: J1, J2, and

J3, which are all the rotating joints. The positive direction of these joints is counter- clockwise.

* If the end-effector with servo is installed, such as suction cup kit, gripper kit, Dobot

Magician contains four joints: J1, J2, J3 and J4, which are all the rotating joints. The positive direction of these joints is counter-clockwise.

* Cartesian coordinate system: The coordinates are determined by the base.
* The origin is the center of the three motors (Rear Arm, Forearm, base).
* The direction of X-axis is perpendicular to the base forward.

![Figure 3.4 Joint coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUkoRW9sOt9mXUN8LVe4y%2Fmagician-p025-img02.png?alt=media)

![Figure 3.5 Cartesian coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkvimCrqnQF9Ic8MYv77M%2Fmagician-p025-img03.png?alt=media)

* The direction of Y-axis is perpendicular to the base leftward.
* The direction of Z-axis is vertical upward, which is based on the right hand rule.
* The R-axis is the attitude of the servo center relative to the origin of the robotic arm, of which the positive direction is counter-clockwise. The R-axis only exists once the end-effector with servo is installed.

#### Motion Function

The motion modes of Dobot Magician include Jogging, Point to Point (PTP), ARC.

**3.3.3.1 Jogging Mode**

Jogging mode is the mode jogging Dobot Magician along the Cartesian coordinate system or Joint coordinate system when teaching.

**NOTE**

This topic describes jogging mode by the GUI operation of DobotStudio.

* Cartesian coordinate system mode
* Click X+, X- and Dobot Magician will move along X-axis in the negative or positive direction.
* Click Y+, Y- and Dobot Magician will move along Y-axis in the negative or positive direction.
* Click Z+, Z- and Dobot Magician will move along Z-axis in the negative or positive direction.
* Click R+, R- and Dobot Magician will rotate along R-axis in the positive or negative direction.

**NOTICE**

If the end-effector with servo is installed on the Dobot Magician, the R-axis will move together with Y-axis, to make sure that the terminal posture relative to the origin stays constant.

* Joint coordinate system mode
* Click J1+, J1- and control the base motor to rotate in the negative or positive direction.
* Click J2+, J2- and control the Rear Arm motor to rotate in the negative or positive direction.
* Click J3+, J3- and control the Forearm motor to rotate in the negative or positive direction.
* Click J4+, J4- and control the servo to rotate in the negative or positive direction.

**3.3.3.2 Point to Point (PTP)**

PTP mode supports MOVJ, MOVL, and JUMP, which means point to point movement. The

* MOVJ: Joint movement. From point A to point B, each joint will run from initial angle to its target angle, regardless of the trajectory, as shown in Figure 3.6.

_Figure 3.6 MOVL/MOVJ mode_

* MOVL: Rectilinear movement. The joints will perform a straight line trajectory from point A to point B, as shown in Figure 3.6.
* JUMP: From point A to point B, the joints will move in MOVJ mode, of which the trajectory looks like a door, as shown in Figure 3.7. Move up the lifting Height in MOVJ mode. Move horizontally to a point that is above B by height. Move down to point B.

_Figure 3.7 JUMP mode_

**3.3.3.3 ARC**

The trajectory of ARC mode is an arc, which is determined by three points (the current point, any point and the end point on the arc), as shown in Figure 3.8.

**NOTICE**

In ARC mode, it is necessary to confirm the three points with other motion modes, and the three points cannot be in a line.

![Figure 3.6 MOVL/MOVJ mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiFpANpRhWPMZh7SobJ6W%2Fmagician-p027-img04.jpg?alt=media)

![Figure 3.7 JUMP mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTqNs2Bta1yc5NPrjQr48%2Fmagician-p027-img05.png?alt=media)

_Figure 3.8 ARC mode_

**3.3.3.4 Application Scenarios**

The application scenario depends on the trajectory in motion mode, as shown in Table 3.1.

_Table 3.1 Application scenario_

Motion mode Application scenario MOVL If the trajectory of playback is required as a straight line, you can choose MOVL MOVJ If the trajectory of playback is not required but high speed is required, you can choose MOVJ JUMP If the movement of two points is required to lift upwards by amount of height, such as sucking up, grabbing, you can choose JUMP ARC If the trajectory of playback is required as an arc, such as dispensing, you can choose ARC

### Technical Specifications

#### Technical Parameters

Name Dobot Magician Maximum 500g payload Maximum reach 320mm Motion range Base ﹣90°~~+90° Rear Arm 0°85° Forearm ﹣10°+90° End-effector ﹣90°~~+90° rotation

Maximum speed Rotational 320°/s (with 250g speed of payload) Rear arm, Forearm and base Rotational 480°/s speed of servo Repeated 0.2mm positioning accuracy Power supply 100V-240V AC, 50/60Hz Power in 12V/7A DC Communication USB, WIFI, Bluetooth I/O 20 extensible I/O interfaces Software DobotStudio Working -10°C\~60°C temperature

#### Sizes

_Figure 3.9 shows the size of Dobot Magician and Figure 3.10 shows the size of the end_

mounting hole.

_Figure 3.9 Size of Dobot Magician_

_Figure 3.10 Size of end mounting hole_

![Figure 3.9 Size of Dobot Magician](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMBlsmSZGSDUB6yM0BLs3%2Fmagician-p030-img01.png?alt=media)

![Figure 3.10 Size of end mounting hole](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD2RtqTD6tuf3grtsEK8F%2Fmagician-p030-img02.png?alt=media)

## Interface Description

### Interface Board

The interfaces of Dobot Magician are located on the back of the base and the Forearm respectively. Figure 4.1 shows the interfaces on the back of the base, and Table 4.1 lists the description.

_Figure 4.1 Interfaces in the base_

_Table 4.1 Interface Description_

No. Description 1 Reset key: Reset MCU program During resetting, the LED indicator on the base turns yellow. About 5 seconds later, if the LED indicator turns green, it indicates that the reset is successful 2 Functional key:

* Short press: Start running offline program
* Long press for 2 seconds: Starting homing procedure

3 Communication interface/UART interface: Connect with Bluetooth, WIFI and so on The Dobot protocol is adopted. 4 USB interface: Connect with PC 5 Power interface: Connect with power adaptor 6 Peripheral interface: Connect with air pump, extruder, sensor and other peripheral equipment. For details about peripheral interfaces, please see Table 4.2

_Table 4.2 lists the peripheral interface description._

![Figure 4.1 Interfaces in the base](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6ucRPOsC8P1z0K07lvgw%2Fmagician-p031-img03.png?alt=media)

_Table 4.2 Peripheral interface description_

SW1 Power interface of air pump; output 12V of controllable power SW2 Output 12V of controllable power Stepper1 User-defined stepper interface; extruder interface (3D printing mode) Stepper2 User-defined stepper interface GP1 Signal interface of air pump; color sensor interface; infrared sensor interface; user-defined general interface GP2 User-defined general interface

_Figure 4.2 shows the peripheral interface on the Forearm, and Table 4.3 lists the description of_

the peripheral interfaces.

_Figure 4.2 Peripheral interface in the Forearm_

_Table 4.3 Peripheral interface description_

No. Description 1 GP3, End-effector interface; R-axis servo interface; user-defined general interface 2 GP4, Auto levelling interface, user-defined general interface 3 GP5, Signal interface of laser engraving; user-defined general interface 4 SW3, Hot end interface (3D printing mode); Output 12V of controllable power 5 SW4, Fan interface (3D printing mode); Power interface of laser engraving; Output 12V of controllable power 6 ANALOG, Thermistor interface (3D printing mode)

![Table 4.2 Peripheral interface description](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsYhlaCx9Xe7hiLC7qS5y%2Fmagician-p032-img01.png?alt=media)

### LED Indicator

The LED indicator is located on the base, Table 4.4 lists the status description.

_Table 4.4 LED indicator description_

Status Description Green On Dobot Magician works normally Yellow On Dobot Magician is in the starting status Blue On Dobot Magician is in the offline mode Blue Blinking Dobot Magician is running homing procedure or auto levelling Red On • Dobot Magician is at the limited position

* Alarm is not cleared
* Connection of 3D printing kit is abnormal

### Multiplexed I/O Interface Description

The addresses of the I/O interfaces in Dobot Magician are unified. Most of I/O interfaces have multiple functions, to control the peripheral equipment.

#### Multiplexed Base I/O Interface Description

**4.3.1.1 Multiplexed UART Interface Description**

_Figure 4.3 shows the UART interface on the base, Table 4.5 lists the multiplexed I/O_

description.

_Figure 4.3 UART interface_

![Table 4.4 LED indicator description](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJuPkMQfmTIRA6wa3BoA0%2Fmagician-p033-img04.png?alt=media)

_Table 4.5 Multiplex I/O Description_

I/O addressing Voltage Level Output PWM Level Input ADC 18 3.3V √ - - - 19 3.3V - - √ - 20 3.3V - - √ -

**4.3.1.2 Multiplexed Peripheral Interface Description**

_Figure 4.4 shows the peripheral interface on the base, and Table 4.6 lists the multiplexed I/O_

description.

_Figure 4.4 Peripheral Interface_

_Table 4.6 Multiplexed I/O Description_

I/O addressing Voltage Level Output PWM Level Input ADC 10 5V √ - - - 11 3.3V √ √ - - 12 3.3V - - √ - 13 5V √ - - - 14 3.3V √ √ √ - 15 3.3V √ - √ √ 16 12V √ - - - 17 12V √ - - -

![Table 4.5 Multiplex I/O Description](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FR9ftQCwTfKSctmnnatlr%2Fmagician-p034-img01.png?alt=media)

#### Multiplexed Forearm I/O Interface Description

_Figure 4.5 shows the peripheral interface on the Forearm, Table 4.7 lists the multiplexed I/O_

description.

_Figure 4.5 Peripheral interface in the Forearm_

_Table 4.7 Multiplexed I/O description_

I/O addressing Voltage Level Output PWM Level Input ADC 1 12V - - √ - 2 12V √ - - - 3 12V √ - - - 4 3.3V √ √ - - 5 3.3V - - √ - 6 3.3V √ √ - - 7 3.3V - - √ - 8 3.3V √ √ - - 9 3.3V - - √ √

![Figure 4.5 shows the peripheral interface on the Forearm, Table 4.7 lists the multiplexed I/O](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj3CNfNF6HhsSxdBMRudV%2Fmagician-p035-img02.png?alt=media)

## Operation

### Introduction to the DobotStudio

#### Function Modules

You can use the DobotStudio to control the Dobot Magician to accomplish multiple functions such as Teaching & Playback, Write & Draw, Blockly graphic programming, and Script control, as shown in Figure 5.1. For details, see Table 5.1.

_Figure 5.1 The function modules on the DobotStudio page_

_Table 5.1 The function modules on the DobotStudio page_

Function Modules Description Teaching & Playback Teach the Dobot Magician how to move and then record the movement to make Dobot Magician accomplish the recorded movements Write & Draw Control the robotic arm to write, draw, or engrave an object using a laser Blockly Use Blockly to program the robotic arm in a graphic programming environment. It allows the users to drag and drop the blocks onto a workplace to generate execute code just as intuitive and easy as a block puzzle Script Control the robotic arm using the script commands Leap Motion Support hand motions as input to control the robotic arm via a Leap Motion controller Mouse Control the robotic arm using a mouse LaserEngraving Engrave a bitmap image on an object using a laser 3DPrinter Capable of 3D printing Add More Add more custom functions to manipulate the robotic arm.

![Figure 5.1 The function modules on the DobotStudio page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkDlEWtJoMZnY83Ivisj5%2Fmagician-p036-img04.jpg?alt=media)

You can also set the Dobot Magician by clicking Setting on the DobotStudio page, for example, implement general settings, base calibration, manual levelling, and auto levelling, as shown in

_Figure 5.2. For details, see Table 5.2._

_Figure 5.2 The General Setting page_

_Table 5.2 The General Setting page_

Items Description General Set tutorial open or close, show console when startup, device name, use Linear rail V2 Firmware Switch firmware For example, you can switch to the 3D printer firmware to implement 3D printing from the currently selected Dobot firmware Sensor and Base Set the Base Encoder and the angle sensors on the Forearm and Rear Arm Base Calibration Calibrate the base Encoder Manual Levelling Manually calibrate the angle sensors on the Forearm and Rear Arm Auto Levelling Automatically calibrate the angle sensors on the Forearm and Rear Arm. Initial Pos Set the initial pose of the robotic arm. Jog Set the jogging speed and acceleration in the Joint coordinate system and Cartesian coordinate system Playback Set the joint parameters, coordinate parameters, Jump parameters, handhold teaching and LostStepParam. Write Draw Set the Write & Draw function, such as speed, Junction velocity, linear acceleration, acceleration, pen up offset and pen down position.

![Figure 5.2. For details, see Table 5.2.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVN5wVoNCGASkm4rbDtzF%2Fmagician-p037-img01.jpg?alt=media)

Items Description Leap Motion Set the parameters such as speed, scale, and performance for hand gesture control. Mouse Set the parameters such as speed, scale, and performance for mouse control. LaserEngraving Set the parameters such as junction velocity, linear acceleration, acceleration, pen down position, and DPI for laser engraving.

#### Common Areas of DobotStudio Page

The DobotStudio offers the following common areas shared by all the function modules to control the robotic arm.

* You can select the liner rail or an end-effector on the DobotStudio page, as shown in

_Figure 5.3._

_Figure 5.3 The linear rail and end-effector drop-down list_

_Table 5.3 The linear rail and end-effector drop-down list_

Items Description Linear rail When the robotic arm is connected to a linear rail, click this item to enable the rail End-effector When the end-effector is a suction cup kit, gripper kit, laser kit or writing and drawing drop-down list kit, select the corresponding kit in this list

* You can also perform other operations on the DobotStudio page such as Setting, Home,

Emergency Stop, and viewing the versions, as shown in Figure 5.4.

_Figure 5.4 Setting, Home, Emergency Stop, and viewing the versions_

_Table 5.4 Setting, Home, Emergency Stop, and viewing the versions_

Items Description Set the robotic arm such as firmware upgrade, sensor and base setup. For details, please Setting refer to Table 5.2 Set the Dobot Magician back to its home position to get a correct reference position Home When the Dobot Magician is moving, if its movement is hindered by an obstacle or the stepper motors lost steps, perform the homing operation Emergency Stop Stop the robotic arm if an emergency occurs

Items Description View the version information such as DobotStudio version, firmware version, and hardware version Switch system language With the Operation Panel on the DobotStudio page, you can teach the robotic arm to perform a specific task such as jogging the robotic arm in the Cartesian or joint coordinate system, or controlling a gripper, suction cup, or laser, as shown in Figure 5.5. For details, please refer to Table 5.5.

_Figure 5.5 Setting the Operation Panel_

_Table 5.5 Setting the Operation Panel_

Items Description Coordinate Jog the Dobot Magician by clicking X (X+/-), Y (Y+/-), Z (Z+/-), or R (R+/-) in the jogging Cartesian coordinate system Jog the Dobot Magician by clicking J1+/-, J2+/-, J3+/-, or J4+/- in the Joint coordinate Joint jogging system

![Figure 5.5 Setting the Operation Panel](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvkgNQ0mdRQWgJMCj75la%2Fmagician-p039-img03.jpg?alt=media)

Items Description When the linear rail is enabled (see Table 5.3), click L+/- to move the robotic arm along Linear control the rail. Value range: 0 mm-1000 mm When the end-effector is chosen as a Gripper, you can set the gripper to open, close, or Gripper control disable in the Gripper drop-down box Suction cup When the end-effector is chosen as a Suction Cup, select SuctionCup to power on the air control pump. If unselected, the air pump is powered off When the end-effector is chosen as a Laser, select Laser to turn on the laser. If Laser control unselected, the laser is turned off Set the jogging speed percentage Jogging speed Default value: 50% control Value range: 1% - 100%

### Performing Teaching & Playback Tasks

This topic introduces how to perform a teaching & playback task to suck or grab a small cube. Because a suction cup kit or a gripper kit is required, we will explain them first.

#### Installing a Suction Cup Kit

A suction cup kit is the default end-effector shipped with the Dobot Magician. When using the suction cup kit, an air pump is necessary, as shown in Figure 5.6.

_Figure 5.6 A suction cup kit_

Procedure Please install a suction cup kit based on Figure 5.7.

![Figure 5.6 A suction cup kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXGubx3crnJmDrOMoPoMl%2Fmagician-p040-img03.png?alt=media)

_Figure 5.7 Connect the air pump to the Dobot Magician_

#### Installing a Gripper Kit

An air pump should be used with the gripper kit, as shown in Figure 5.8, to open or close the gripper.

_Figure 5.8 A gripper kit_

Procedure

![Figure 5.7 Connect the air pump to the Dobot Magician](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd7709h5zbVKdWWFNFMns%2Fmagician-p041-img02.png?alt=media)

![Figure 5.8 A gripper kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7HLqJimHFr5Qyokcy1fQ%2Fmagician-p041-img03.jpg?alt=media)

_Figure 5.9 Dismantle the suction cup_

_Figure 5.10 Install a gripper kit_

![Figure 5.9 Dismantle the suction cup](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUWw0fuyD4tFkgJOmehk2%2Fmagician-p042-img18.jpg?alt=media)

![Figure 5.10 Install a gripper kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FX402ieJCNQyLKRTscOeE%2Fmagician-p042-img19.jpg?alt=media)

_Figure 5.11 The effect of the gripper kit installation_

#### Teaching & Playback Page

The Teaching & Playback page is shown in Figure 5.12. To access it, select Connect > Teaching & Playback on the DobotStudio page.

_Figure 5.12 The Teaching & Playback page_

* In both Easy and Pro modes, you can switch between Easy and Pro modes, set loop, speed percentage, and acceleration percentage, as shown in Figure 5.13.

_Figure 5.13 Set Easy/Pro, Loop, Speed and Acceleration (Acc)_

![Figure 5.11 The effect of the gripper kit installation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdkracZrsIykWhKDUUZXj%2Fmagician-p043-img02.jpg?alt=media)

![Figure 5.12 The Teaching & Playback page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Figy6M4MOIM4gKHrRbP69%2Fmagician-p043-img03.jpg?alt=media)

_Table 5.6 Set Easy/Pro, Loop, Speed and acceleration (Acc)_

Items Description Click this slider to switch between Easy and Pro modes. The default is the Easy mode Easy/Pro Apart from all the functions in the Easy mode, the Pro mode offers multiple features such as the offline mode and multiplexed I/O interface Set the loop that the robotic arm plays back the recorded steps Loop Default value: 1 Value range: 1-999999 Set the speed ratio when doing playback Speed Default value: 50% Value range: 0% - 100% Set the acceleration ratio when doing playback acceleration Default value: 50% (Acc) Value range: 0-100% Exit Exit the current Teaching & Playback page to return to the DobotStudio page

* In both Easy and Pro modes, you can save points, set the motion mode and the pause time for a save point, as shown in Figure 5.14.

_Figure 5.14 Set the save points, motion modes and pause time_

_Table 5.7 Set the save points, motion modes, and pause timess_

Items Description +Point Click to create a new save point in the Save points list Choose a PTP (point to point) Point mode or ARC Point mode. In the PTP Point mode, you can select MOVJ, MOVL, or JUMP mode while the ARC Point mode requires a Motion mode second point cirPoint and a finish point toPoint as well as the start point set via the PTP Point mode Pause time Set the pause time for a save point

* In both Easy and Pro modes, you can edit a highlighted save point such as copy, paste, cut,

![Table 5.6 Set Easy/Pro, Loop, Speed and acceleration (Acc)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fko8CjHA6YmtXtskgyIjq%2Fmagician-p044-img01.jpg?alt=media)

switch between motion modes, modify name and coordinates, as shown in Figure 5.15.

_Figure 5.15 The Save points list_

_Table 5.8 The Save points list_

Items Description A right-click mouse In the right-click popup menu you can edit a highlighted save point such as copy, operation paste, cut, insert, and delete, as shown in Figure 5.15 A double-click mouse Double-clicking a cell to modify its value

* Pro mode: To enter the Pro mode from the current Easy mode, click the Easy/Pro slider, as shown in Figure 5.16. Apart from all the functions in the default Easy mode, the Pro mode allows the robotic arm to run a save point each time, detect lost-steps, work in offline mode, and perform the multiplexed I/O interface. For details, see Table 5.9.

_Figure 5.16 The Pro mode of the Teaching & Playback function_

![Figure 5.15 The Save points list](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZh37oEs9favqdcvYLP7g%2Fmagician-p045-img01.png?alt=media)

![Table 5.8 The Save points list](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq5VH0lbA88mBFwZjNQoL%2Fmagician-p045-img02.png?alt=media)

_Table 5.9 The Pro mode of the Teaching & Playback function_

No. Description StepRun: run a save point each time in the Save points list. Before clicking StepRun, please select a saved point. Download: download the Save points list to the Dobot Magician for working in offline mode. For details, see 5.3 Working in Offline Mode Check Lost Step: the Dobot Magician detects if lost-steps occur in its movements. The default threshold is 5 degrees. It should be at least 0.5 degrees. You can set the threshold by selecting Setting > Playback > LostStepParam. 3 If Check Lost Step is selected, the robotic arm detects if the stepper motors lose steps when moving. If unselected, no detection is performed If the Dobot Magician detects lost-steps, it stops working, and its LED indicator turns red. In this case, click Home to get a correct reference position Multiplexed I/O interface: control the Dobot Magician via the I/O interfaces such as turning on or off the air pump

#### ARC Motion Mode

**Application Scenarios**

The ARC motion mode requires three points in an arc to complete the arc movement process. In the ARC motion mode, only the second point and end point are saved while the start point is determined by the other modes. Prerequisites The Dobot Magician has been powered on and connected to your computer. Procedure

**NOTICE**

Note the following rules when saving points to prevent the robotic arm from working outside its normal workspace.

* Any two points cannot coincide.
* The three points cannot be in the same straight line.
* The arc trajectory cannot exceed the Dobot Magician’s normal workspace.

For example the points A, B, and C are on the arc. Point A is the start point; Point B is the second point; Point C is the end point, as shown in Figure 5.17.

_Figure 5.17 The arc trajectory_

The Teaching & Playback page is displayed.

1. Select MOVJ motion mode in the Save Point area.
2. Set the jogging speed percentage to 50 on the Operation Panel.
3. Jog the Dobot Magician in the Cartesian or Joint coordinate system to move the

robotic arm to a location called position A.

4. Click +Point to save the coordinate corresponding to the position A, as shown

in Figure 5.18.

_Figure 5.18 Save the start position A_

Select cirPoint to save the second point in the Save Point area. Jogging the Dobot Magician in the Cartesian or Joint coordinate system to move the robotic arm to the second position B as required. Click +Point to save the coordinate corresponding to the position B. In this case, the DobotStudio automatically changes the motion mode to toPoint to get ready to save the end position.

![Figure 5.17 The arc trajectory](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9LMlulvJgUiU15j0PAHT%2Fmagician-p047-img12.png?alt=media)

![Figure 5.18 Save the start position A](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQLj9g6FUpGMXRwMIK1aQ%2Fmagician-p047-img13.png?alt=media)

Jogging the Dobot Magician in the Cartesian or Joint coordinate system to move the robotic arm to the end position C as needed. Click +Point to save the coordinates corresponding to the positions B and C, as shown in Figure 5.19. s

_Figure 5.19 Save the second position B and the end position C_

Set the percentage of both speed and acceleration for playback, for example 50. Set Loop to 2. Click Start. The Dobot Magicin perfrom the sequence of ARC trajectory as taught from its memory system, moving from positions A to C.

#### Teaching & Playback Example

**Application Scenarios**

You can use Teaching & Playback function module to manipulate the Dobot Magician to accomplish different tasks such as transportation or intelligent sort. This topic introduces how to move small cubes from position A to B in the JUMP motion mode. Prerequisites

* The Dobot Magician has been powered on and connected to your computer.
* A suction cup kit has been installed. For details, see 5.2.1 Installing a Suction Cup Kit.

Procedure

_Figure 5.20 Choose SuctionCup as the end-effector_

The Teaching & Playback page is displayed.

![Figure 5.19 Save the second position B and the end position C](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxuvM3LdCLE4HKYxB5C0k%2Fmagician-p048-img18.png?alt=media)

**NOTE**

After reading the beginner guide of the DobotStudio, click to close it.

1. Put a small cube on the work surface near the suction cup kit.
2. Select the MOVJ motion mode in the Save Point area.
3. Set the jogging speed percentage to 50 on the Operation Panel.

**NOTE**

To change the jogging speed, select Setting > Jog to set the speed and acceleration of the joints, linear rail, or the Cartesian coordinate system, as shown in Figure 5.21.

_Figure 5.21 Adjust the jogging speed_

**NOTICE**

Regarding the jogging speed and acceleration in the Joint coordinate system and Cartesian coordinate system, we recommend that it should be less than 500mm/s if loaded and that less than 800mm/s if not loaded.

4. Jog the Dobot Magician in the Cartesian or Joint coordinate system to move the

suction cup close enough to the small cube for picking-up. For example, the

![Figure 5.21 Adjust the jogging speed](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4XWhfYaOtBhi9m76bZ6w%2Fmagician-p049-img04.png?alt=media)

suction cup reaches this location called position A.

5. Select SuctionCup on the Operation Panel to turn on the air pump to pick up

the small cube.

6. Set the PauseTime to 1 second in the Save Point area.
7. Click +Point to save the coordinate corresponding to the position A, as shown

in Figure 5.22.

_Figure 5.22 Save the start position A_

Select the JUMP motion mode in the Save Point area.

**NOTE**

To change the jogging speed percentage, drag the speed slider. Set the lifting height (JumpHeight) and the maximum lifting height (Z Limit) by selecting Setting > Playback > JumpParam, as shown in Figure 5.23.

![Figure 5.22 Save the start position A](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcXfR31xp0hgRayUaKrJt%2Fmagician-p050-img05.jpg?alt=media)

_Figure 5.23 Jump parameters_

Jogging the Dobot Magician in the Cartesian or Joint coordinate system to move the small cube to the end position B as required. Unselect SucktionCup to turn off the air pump to release the small cube. Click +Point to save the coordinate corresponding to the position B, as shown in Figure 5.24.

_Figure 5.24 Save the end position B_

**NOTE**

To change the speed and acceleration of playback, select Setting > Playback >

![Figure 5.23 Jump parameters](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAOLBqgI3UzICZjTfr8vP%2Fmagician-p051-img06.png?alt=media)

![Figure 5.24 Save the end position B](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpgnywPWYqkE2uMNbl8C5%2Fmagician-p051-img07.png?alt=media)

Joint coordinate system, as shown in Figure 5.25. For details, see Table 5.10.

_Figure 5.25 Set the speed and acceleration of the playback_

_Table 5.10 Set the Playback_

Items Description JointParam Set the speed and acceleration of the joints CoordinateParam Set the speed and acceleration in the Cartesian coordinate system JumpParam Set the Jump height and Z limit, which are required in the JUMP motion mode Enable or disable the handhold teaching. Handhold Teaching Automatically save a point when releasing the unlock button or pressing this button LostStepParam Set the lost-step checking threshold

**NOTICE**

We recommend that the motion range of Joint 1 should be 60° to -90°, the motion range of Joint 2 should be 0°to 85°, the motion range of Joint 3 is -5°to 85°, and the motion range of Joint 4 is -90°to 90°。

![Figure 5.25 Set the speed and acceleration of the playback](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj7tBc40sMb14WzDKtNeE%2Fmagician-p052-img12.png?alt=media)

### Working in Offline Mode

Offline mode allows the Dobot Magician to perform the points in the Save points list previously downloaded from the DobotStudio without keeping the USB connection established. Prerequisites

* The Dobot Magician has been powered on.
* The Dobot Magician has been connected to the DobotStudio.
* The points have been saved.

Procedure The Question dialog box is displayed, asking if you want the Dobot Magician to automatically to go back to its homing point before performing the save points in the offline mode, as shown in Figure 5.26.

_Figure 5.26 Click Download_

When the process bar at the bottom of the DobotStudio page shows 100% and then disappears, it means that the download is complete.

**NOTICE**

* Before using offline mode, Dobot Magician needs to be reset by clicking

Home to make Dobot Magician more accurate. For the details please refer to

![Figure 5.26 Click Download](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FR2gI8ToP6uj4ocd8TESb%2Fmagician-p053-img27.jpg?alt=media)

* If press down Key button for long time, Dobot Magician will execute homing operation directly.

_Figure 5.27 Base panel_

### Writing and Drawing

_Figure 5.28 shows the process of writing and drawing._

_Figure 5.28 The process of writing and draw_

#### Installing a Writing and drawing kit

A writing and drawing kit consists of a pen and a pen holder. For detailed steps, see below.

![Figure 5.27 Base panel](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FE1uSjy0SnoWEOqDHknKS%2Fmagician-p054-img10.png?alt=media)

_Figure 5.29 Install a writing and drawing kit_

**NOTE**

To change to a new pen, unfasten the four M3\*5 set screws in the pen holder with a 1.5mm hexagon wrench, as shown in Figure 5.30.

_Figure 5.30 Change to a new pen_

#### Connecting the DobotStudio

If the current firmware of the Dobot Magician is the 3D Printing firmware instead of the Dobot firmware, the Select tool dialog box is displayed, asking if you want to switch to the Dobot firmware. In this case, perform the following steps to switch to this firmware. Select DobotStudio to upgrade the Dobot firmware, as shown in Figure 5.31.

![Figure 5.29 Install a writing and drawing kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5gcFIVjUIDisCqxtRpRz%2Fmagician-p055-img10.jpg?alt=media)

![Figure 5.30 Change to a new pen](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FveZTVjyz87WGZnkHrPQ9%2Fmagician-p055-img11.png?alt=media)

The dialog box is displayed.

_Figure 5.31 Select the DobotStudio to upgrade the Dobot firmware_

Click OK, as shown in Figure 5.32. The Dobot firmware upgrade window is displayed.

_Figure 5.32 Confirm the firmware upgrade_

Click Confirm to upgrade the Dobot firmware, as shown in Figure 5.33. When the upgrade process bar shows 100%, and a short beep sound is heard, it means that the firmware is upgraded successfully, as shown in Figure 5.34. In this case, the LED indicator turns from red to green. Then click Quit to exit.

_Figure 5.33 Click Confirm_

![Figure 5.31 Select the DobotStudio to upgrade the Dobot firmware](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv5lCHTTowBfF5ScVm0MO%2Fmagician-p056-img03.png?alt=media)

![Figure 5.32 Confirm the firmware upgrade](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdDNaFBHqbhQ7HBnikh37%2Fmagician-p056-img05.png?alt=media)

_Figure 5.34 The firmware upgrade is successful_

**WARNING**

During the firmware upgrade, do not stop it. Otherwise, errors occur.

_Figure 5.35 Click Write & Draw_

![Figure 5.34 The firmware upgrade is successful](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0PPdcuukwdiNZVFkpwmZ%2Fmagician-p057-img16.png?alt=media)

![Figure 5.35 Click Write & Draw](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtJt2AL8PzLCBZNR7i1aZ%2Fmagician-p057-img18.jpg?alt=media)

_Figure 5.36 Choose Pen as the end-effector_

#### Importing Image Files and Setting Writing Parameters

When performing a write & draw task, a built-in or custom image file is required. Only a PLT or SVG image can be used. The built-in file is located in the directory Installation Directory \DobotStudio\config\prefab\system\source. Prerequisites A PLT or SVG image file has been created. Procedure

_Figure 5.37 Click Write & Draw_

**NOTICE**

The imported image should be placed within the annular area on the Write & Draw page, as shown in Figure 5.38. If not, the robotic arm reaches its limited position and cannot draw or write. In this case, the image is highlighted with a red border, as shown in Figure

5.39.

_Figure 5.38 The PLT or SVG image is located within the annular area_

_Figure 5.39 The PLT or SVG image is located outside the annular area_

* Click Open on the Write & Draw page to import a built-in PLT or SVG image file from the DobotStudio installation directory InstallatonDirectory\DobotStudio\config\prefab\system\source, as shown in Figure 5.40. You can also import your custom PLT or SVG image file.

![Figure 5.38 The PLT or SVG image is located within the annular area](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FafoXVRqPqJg78BQu3Xzw%2Fmagician-p059-img01.png?alt=media)

![Figure 5.39 The PLT or SVG image is located outside the annular area](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnRITyORTNJXbBMQ3sqsu%2Fmagician-p059-img02.png?alt=media)

_Figure 5.40 Open a PLT or SVG system image file_

* Click a shape in the Input Shapes area, as shown in Figure 5.41.

_Figure 5.41 Insert a system image file_

* Click Input Texts on the Write & Draw page to input texts, and set its style, and then click

OK to display the text on the annular area, as shown in Figure 5.42.

![Figure 5.40 Open a PLT or SVG system image file](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmlVQVcHN05P4RdcVMkcZ%2Fmagician-p060-img01.png?alt=media)

![Figure 5.41 Insert a system image file](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW6p6i2SzbHGdbxHQ5CKs%2Fmagician-p060-img02.png?alt=media)

_Figure 5.42 Input text_

* Click Open to import an image file such as BMP, JEPG, or PNG to convert this image to its corresponding SVG file that the DobotStudio supports. Once this image is imported, the SVG Converter dialog box is displayed, as shown in Figure 5.43. In this dialog box, drag the slider to set the black and white threshold, and click Convert Bitmap To SVG to perform the conversion, and then click Plot to Main Scene to display the converted SVG file on the annular area of the Write & Draw page.

_Figure 5.43 Convert an image to SVG_

**NOTICE**

After image is converted to SVG,if there are single colors and fewer lines in image, you need to adjust threshold, otherwise picture can’t be uploaded to DobotStudio.

![Figure 5.42 Input text](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FejAsZE7bb0Col9P79YuH%2Fmagician-p061-img01.png?alt=media)

![Figure 5.43 Convert an image to SVG](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfRsA5C4RcdRws9Zxsa11%2Fmagician-p061-img02.png?alt=media)

_Figure 5.44 Error tip_

**NOTE**

We recommend to set the Velocity in the range of 0mm/s to 500mm/s and to adjust the acceleration between 0mm/s2 and 500mm/s2.

_Figure 5.45 Setting the parameters of the Write & Draw function_

#### Adjust the Position of the Pen Nib

![Figure 5.44 Error tip](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5xDWtCEcnsW6qSxxbrmp%2Fmagician-p062-img25.png?alt=media)

![Figure 5.45 Setting the parameters of the Write & Draw function](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNgcc02637ST9iN2rx7ol%2Fmagician-p062-img26.png?alt=media)

Procedure Press and hold the unlock button on the Forearm to move the Dobot Magician to raise and lower the pen nib until it slightly squeezes the paper. You can also jog the robotic arm in the Cartesian or Joint coordinate system to slowly pull the Z axis down to a suitable vertical position for writing, as shown in Figure 5.46.

_Figure 5.46 Adjust the position of the pen nib_

**NOTE**

The point marked by a red box, as shown in Figure 5.47, corresponds to the position of the writing and drawing kit of the Dobot Magician. This point changes its position only within the annular area when the robotic arm moves.

_Figure 5.47 The point corresponding to the laser kit of the robotic arm_

![Figure 5.46 Adjust the position of the pen nib](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6x3U8W7JRfa7WvMlcLT0%2Fmagician-p063-img12.jpg?alt=media)

![Figure 5.47 The point corresponding to the laser kit of the robotic arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkRVeBrz8RAIBpfuhOcmN%2Fmagician-p063-img13.png?alt=media)

_Figure 5.48 Lock the height of writing_

**NOTE**

The value of the Z axis is the PenDown parameter. This parameter can be set by selecting Setting > Write Draw > PenDown on the Write & Draw page, as shown in Figure 5.49. If the effect of writing is not satisfactory, slightly raise and lower the height of the writing and drawing kit or directly change the value of PenDown.

_Figure 5.49 The PenDown parameter_

![Figure 5.48 Lock the height of writing](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTiT7yXVZKAZeZBGRJrGa%2Fmagician-p064-img10.png?alt=media)

![Figure 5.49 The PenDown parameter](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDPIJL2AB6C8aQ9Ag4sCi%2Fmagician-p064-img11.png?alt=media)

The Dobot Magician automatically moves above the position (PenDown) of the start point of the text. Click Start to start writing on the paper. When writing, click Pause to pause the writing and Stop to halt the writing.

### Performing Laser Engraving Tasks

_Figure 5.50 shows the process of laser engraving._

_Figure 5.50 The process of laser engraving_

**NOTICE**

The LaserEngraving is different is from the grayscale engraving. The former uses the same firmware and DobotStudio function module as those of the Write & Draw function, and it can only engrave a vector graphics by drawing lines while the latter can engrave a grayscale image. For more information about the grayscale engraving, see 5.6

#### Installing a Laser Kit

Procedure A laser kit includes a laser. For detailed steps, see below.

_Figure 5.51 Fasten the laser with clamp fixing screw_

#### Connecting the DobotStudio

If the current firmware of the Dobot Magician is the 3D Printing firmware instead of the Dobot firmware, the Select tool dialog box is displayed, asking if you want to switch to the Dobot firmware. In this case, perform the following steps to switch to this firmware. Select DobotStudio to upgrade the Dobot firmware, as shown in Figure 5.52. The Question dialog box is displayed.

_Figure 5.52 Select the DobotStudio to upgrade the Dobot firmware_

Click OK, as shown in Figure 5.53.

![Figure 5.51 Fasten the laser with clamp fixing screw](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcdScQAwPSr1IHTFIE9xy%2Fmagician-p066-img15.jpg?alt=media)

The Dobot firmware upgrade window is displayed.

_Figure 5.53 Confirm the firmware upgrade_

Click Confirm to upgrade the Dobot firmware, as shown in Figure 5.54. When the upgrade process bar shows 100% and a short beep sound is heard, it means that the firmware is upgraded successfully, as shown in Figure 5.55. In this case, the LED indicator turns from red to green. Then click Complete to exit.

_Figure 5.54 Click Confirm_

![Figure 5.53 Confirm the firmware upgrade](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJwJgp8dcSlytjJBgANw6%2Fmagician-p067-img03.png?alt=media)

_Figure 5.55 The firmware upgrade is successful_

**WARNING**

During the firmware upgrade, do not stop it. Otherwise, errors occur.

_Figure 5.56 Click Write & Draw_

_Figure 5.57 Choose Laser as the end-effector_

#### Importing Image Files and Setting Engraving Parameters

When performing a laser-engraving task, a built-in or a custom image file is required. Only a PLT or SVG image can be used. The built-in image file is located in the directory: Installation Directory\DobotStudio\config\prefab\system\source. Prerequisites A PLT or SVG image file has been created. Procedure

_Figure 5.58 Click Write & Draw_

![Figure 5.57 Choose Laser as the end-effector](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuFFXWE5Zctx2k4LPgNQG%2Fmagician-p069-img17.png?alt=media)

![Figure 5.58 Click Write & Draw](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff36M6mXtWUpZKNQJIgsj%2Fmagician-p069-img18.jpg?alt=media)

**NOTICE**

The imported image should be placed within the annular area on the Write & Draw page, as shown in Figure 5.59. If not, the robotic arm reaches its limited position and thus cannot engrave on an object. In this case, the image is highlighted with a red border, as shown in Figure 5.60.

_Figure 5.59 The PLT or SVG image is located within the annular area_

_Figure 5.60 The PLT or SVG image is located outside the annular area_

* Click Open on the Write & Draw page to import a built-in PLT or SVG image file from the DobotStudio installation directory InstallatonDirectory\DobotStudio\config\prefab\system\source, as shown in Figure 5.61. You can also import your custom PLT or SVG image file.

_Figure 5.61 Open a PLT or SVG file_

* Click a shape in the Input Shapes area to directly import a system image file, as shown in

_Figure 5.62._

_Figure 5.62 Insert a system image file_

* Click Input Texts on the Write & Draw page to input texts, and set its style, and then click

OK to display the text on the annular area, as shown in Figure 5.63.

_Figure 5.63 Input text_

* Click Open to import an image file such as BMP, JEPG, or PNG to convert this image to its corresponding SVG file that the DobotStudio supports.ssss Once this image is imported, the SVG Converter dialog box is displayed, as shown in Figure 5.64. In this dialog box, drag the slider to set the black and white threshold, and click Convert Bitmap To SVG to perform the conversion, and then click Plot to Main Scene to display the converted SVG file on the annular area of the Write & Draw page.

_Figure 5.64 Convert Bitmap to SVG_

**NOTE**

We recommend to set the Velocity in the range of 0mm/s to 500mm/s and to adjust the acceleration between 0mm/s2 and 500mm/s2.

![Figure 5.63 Input text](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9dDQW1JHwFzkDYoPn1O1%2Fmagician-p072-img24.png?alt=media)

_Figure 5.65 Setting the parameters of the Write & Draw function_

#### Adjust the Laser Focus and Start to Grave

Procedure

_Figure 5.66 Choose Laser as the end-effector_

_Figure 5.67 Turn on the laser_

![Figure 5.65 Setting the parameters of the Write & Draw function](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F32L5MPEk2YAmEpR475VS%2Fmagician-p073-img20.png?alt=media)

![Figure 5.66 Choose Laser as the end-effector](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcLw2Ra7Pan1LpF2ciYw9%2Fmagician-p073-img23.jpg?alt=media)

Danger

* When using a laser, wear lasing protective eyeglass.
* Never aim the laser at a person’s eye and clothes or stare at the laser from within the beam.
* In the central laser focus, a high temperature heat is created and can burn materials such as papers and wooden boards.
* Never aim the laser at a person and their clothes.
* Do not allow the children to play with the Dobot Magician. Monitor the robotic arm while it is running and power off it once the movement is complete.

_Figure 5.68 Unselect the Lasers_

**NOTICE**

* If you cannot set the laser to be at its minimum focus, it’s probably because the focal length is long. To shorten the focal length, slightly turn the sliver lens screw (as shown in Figure 5.69) on the bottom of the laser kit.

![Figure 5.68 Unselect the Lasers](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwjgCm5y42AOlFKLre58I%2Fmagician-p074-img14.jpg?alt=media)

_Figure 5.69 Adjust the laser focus_

* The point marked by a red box, as shown in Figure 5.70, corresponds to the position of the end-effector of the Dobot Magician. This point changes its position only within the annular area when the robotic arm moves.

_Figure 5.70 The point corresponding to the end-effector of the robotic arm_

Once this step is complete, the next time you start to engrave, directly import a PLT or SVG image file without adjusting the position of the laser kit, and click SyncPos, and then click Start to start engraving on the paper, as shown in Figure 5.71.

![Figure 5.69 Adjust the laser focus](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fch2oPCPayypLB5sThhCC%2Fmagician-p075-img09.jpg?alt=media)

![Figure 5.70 The point corresponding to the end-effector of the robotic arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfloenL2SfMRlMe0PFrdy%2Fmagician-p075-img10.jpg?alt=media)

_Figure 5.71 Lock the height of engraving_

**NOTE**

The value of the Z axis is the PenDown parameter. This parameter can be set by selecting Setting > Write Draw > PenDown on the Write & Draw page, as shown in Figure 5.72. If the effect of engraving is not satisfactory, slightly raise and lower the height of the laser kit or directly change the value of PenDown.

_Figure 5.72 Set the PenDown parameters_

![Figure 5.71 Lock the height of engraving](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZbkpLubJ7TlNX31rCL6S%2Fmagician-p076-img01.jpg?alt=media)

![Figure 5.72 Set the PenDown parameters](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJvibmojH9rH3I1jMUIEt%2Fmagician-p076-img02.png?alt=media)

The Dobot Magician automatically moves above the position (PenUpOffset) of the start point of the laser-engraving. When engraving, click Pause to pause the engraving and Stop to halt the engraving.

_Figure 5.73 shows the effect of the laser-engraving._

_Figure 5.73 The effect of the laser-engraving_

### Engraving a Grayscale Image

_Figure 5.74 shows the process of engraving a grayscale image._

![Figure 5.73 shows the effect of the laser-engraving.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FceQbLsiT9780JEM6XCTf%2Fmagician-p077-img09.jpg?alt=media)

_Figure 5.74 The process of engraving a grayscale image_

#### Installing a Grayscale-engraving Kit

Both grayscale-engraving and laser-engraving use the laser kit as the end-effector. For the installation method, see 5.5.1 Installing a Laser Kit.

#### Connecting the DobotStudio

If the current firmware of the Dobot Magician is the 3D Printing firmware instead of the Dobot firmware, the Select tool dialog box is displayed, asking if you want to switch to the Dobot firmware. In this case, perform the following steps to switch to this firmware. Select DobotStudio to upgrade the Dobot firmware, as shown in Figure 5.75. The Question dialog box is displayed.

![Figure 5.74 The process of engraving a grayscale image](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ5BmybuW9e4HNA8p4E7t%2Fmagician-p078-img08.png?alt=media)

_Figure 5.75 Select the DobotStudio to upgrade the Dobot firmware_

Click OK, as shown in Figure 5.76. The Dobot firmware upgrade window is displayed.

_Figure 5.76 Confirm the firmware upgrade_

Click Confirm to upgrade the Dobot firmware, as shown in Figure 5.77. When the upgrade process bar shows 100%, and a short beep sound is heard, it means that the firmware is upgraded successfully, as shown in Figure 5.78. In this case, the LED indicator turns from red to green. Then click Complete to exit.

_Figure 5.77 Click Confirm_

_Figure 5.78 The firmware upgrade is successful_

**WARNING**

During the firmware upgrade, do not stop it. Otherwise, errors occur.

_Figure 5.79 Click LaserEngraving_

#### Importing Image Files and Setting Engraving Parameters

Prerequisites An image file has been created. You can also import system image, the importing path is Installation Directory\DobotStudio\attachment\grbrMode\source.

![Figure 5.78 The firmware upgrade is successful](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3lemSiKSQPBQ62jzj75V%2Fmagician-p080-img10.jpg?alt=media)

Procedure

**NOTICE**

The imported image should be placed within the annular area on the LaserEngraving page, as shown in Figure 5.80. If not, the robotic arm reaches its limited position and thus cannot engrave on an object. In this case, the image is highlighted with a red border, as shown in Figure 5.81.

_Figure 5.80 The image file is located within the annular area_

_Figure 5.81 The image file is located outside the annular area_

![Figure 5.80 The image file is located within the annular area](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUkVzCwzDZmidDmqfkBHP%2Fmagician-p081-img02.png?alt=media)

![Figure 5.81 The image file is located outside the annular area](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEoQJvM45w2MTSBBgUfbF%2Fmagician-p081-img03.png?alt=media)

_Figure 5.82 Choose Laser as the end-effector_

_Figure 5.83 Import an image file_

_Figure 5.84 Set the grayscale range, laser power range, and border_

![Figure 5.82 Choose Laser as the end-effector](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFkVxQhg40EHf0gcGf7N8%2Fmagician-p082-img30.png?alt=media)

![Figure 5.83 Import an image file](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8ALprahpnebZcD0J9FKJ%2Fmagician-p082-img31.jpg?alt=media)

_Table 5.11 Laser engraving parameters_

Items Description Grayscale range Set the grayscale range Range: 0-255 Default value: 20-240 Laser power range Set the laser power range Range: 2-100 Default value: 20-90 Border Set the border width. Unit: pixel Range: 0-50 Default value: 4 Click Setting on the LaserEngraving page. Set the JunctionVel (junction velocity), PlanAcc (linear acceleration), and Acc (acceleration), for example, set all to 5, as shown in Figure 5.85.

_Figure 5.85 Set the parameters of laser engraving_

#### Adjust the Laser Focus and Start to Engrave

![Table 5.11 Laser engraving parameters](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPOJmrK9VtkxRnQsefHA9%2Fmagician-p083-img06.png?alt=media)

Danger

* When using a laser, wear lasing protective eyeglass.
* Never aim the laser at a person’s eye and clothes or stare at the laser from within the beam.
* In the central laser focus, a high-temperature heat is created and can burn materials such as papers and wooden boards.
* Never aim the laser at a person and their clothes.
* Do not allow the children to play with the Dobot Magician. Monitor the robotic arm while it is running and power off it once the movement is complete.

_Figure 5.86 Select the Laser_

Press and hold the unlock button on the Forearm to move the robotic arm to raise and lower the height of the laser kit until the laser is the brightest with a smallest possible spot size. When the laser power level is high enough, the laser beam can burn and cut the paper. After getting a pretty good focus, unselect Laser on the Operation Panel page to turn off the laser, as shown in Figure 5.87.

![Figure 5.86 Select the Laser](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZwQJGGxQIZdB6SK2l95N%2Fmagician-p084-img14.jpg?alt=media)

_Figure 5.87 Unselect the Laser_

**NOTICE**

* If you cannot set the laser to be at its minimum focus, it’s probably because the focal length is long. To shorten the focal length, slightly turn the sliver lens screw (as shown in Figure 5.88) on the bottom of the laser kit.

_Figure 5.88 Adjust the focus_

* The point marked by a red box, as shown in Figure 5.89, corresponds to the position of the laser kit of the Dobot Magician. This point changes its position only within the annular area when the robotic arm moves.

![Figure 5.87 Unselect the Laser](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8XXJi5PAqBTgxy0ye5iB%2Fmagician-p085-img01.jpg?alt=media)

_Figure 5.89 The point corresponding to the laser kit of the robotic arm_

_Figure 5.90 Lock the height of engraving_

**NOTE**

The value of Z axis is the PenDown parameter. This parameter can be set by selecting Setting > LaserEngraving > PenDown, as shown in Figure 5.91. If the effect of engraving is not satisfactory, slightly raise and lower the height of the laser kit or directly

![Figure 5.89 The point corresponding to the laser kit of the robotic arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6AcA3s97fmRiVNiR5m0L%2Fmagician-p086-img18.png?alt=media)

![Figure 5.90 Lock the height of engraving](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3hzbsJnzO8S41NXDpfZ7%2Fmagician-p086-img19.png?alt=media)

_Figure 5.91 Set the PenDown parameters_

The Dobot Magician automatically moves above the position of the start point of the laser-engraving. When engraving, click Pause to pause the engraving and Stop to halt the engraving.

_Figure 5.92 shows the effect of the laser-engraving._

_Figure 5.92 The effect of laser-engraving_

![Figure 5.91 Set the PenDown parameters](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrW73iw1idTA7iQRETJlg%2Fmagician-p087-img09.png?alt=media)

![Figure 5.92 shows the effect of the laser-engraving.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FylOqTzreDEOdTFmSohET%2Fmagician-p087-img10.jpg?alt=media)

### Controlling with your Hand Gesture

You can use the LeapMotion function module of the DobotStudio to perform tasks, for example, grab or suck an object with your hand gesture.

#### Installing a Leap Motion Controller

Prerequisites

* The Leap Motion controller (a hand gesture controller) has been obtained.
* The Leap Motion driver software has been obtained. Download the Windows version, as shown in Figure 5.93, from the https://www.leapmotion.com/setup/desktop/windows.

_Figure 5.93 Download the Leap Motion driver software for Windows_

Procedure

_Figure 5.94 Connect the Leap Motion controller to your computer_

![Figure 5.93 Download the Leap Motion driver software for Windows](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCQQhanF83pSifXgm1hzp%2Fmagician-p088-img12.png?alt=media)

![Figure 5.94 Connect the Leap Motion controller to your computer](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMeyMOQ5u9o1TFFKSlaeF%2Fmagician-p088-img13.jpg?alt=media)

_Figure 5.95 The Leap Motion Installation Interface_

#### Leap Motion Demo

You can move or sort an object with the LeapMotion function. This topic introduces how to move a small cube with a hand gesture. Prerequisites

* The Dobot Magician is powered on and connected to your computer.
* The suction cup kit has been installed. For details, see 5.2.1 Installing a Suction Cup Kit.

Procedure

_Figure 5.96 Click LeapMotion_

![Figure 5.95 The Leap Motion Installation Interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2Y9NShpOUKUdtVPSQ0Ey%2Fmagician-p089-img12.png?alt=media)

![Figure 5.96 Click LeapMotion](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZejIed5hyjPEX6Q8RQnq%2Fmagician-p089-img13.jpg?alt=media)

_Figure 5.97 Click Setting_

_Figure 5.98 Set the parameters of the Leap Motion function_

![Figure 5.97 Click Setting](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFDJN5hQjUZymvSxqNdhO%2Fmagician-p090-img18.jpg?alt=media)

![Figure 5.98 Set the parameters of the Leap Motion function](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F843gwYvRR5negG7tVIJP%2Fmagician-p090-img19.jpg?alt=media)

_Table 5.12 Set the parameters of the Leap Motion function_

Items Description Speed The velocity percentage of the Dobot Magician: Unit: % Value range: 1-100 Default value: 50 Scale The scale of the Dobot Magician: Unit: % Value range: 1-100 Default value: 100 High performance/Low Choose a performance mode suitable for your computer. Select the Low performance performance (default) for the low configuration computer to prevent video delay

**NOTE**

Move your hand in the workspace of the Leap Motion controller to control the Dobot Magician to perform a particular task, as shown in Table 5.13.

_Table 5.13 The robotic arm’s movement created with your hand gesture_

Hand gesture Robotic arm’s movement Move your palm up, down, front, The robotic arm moves accordingly back, right, or left Clench your fist Control the air pump to suck air Unclench your fist Turn off the air pump

### Controlling with your Mouse

You can use the Mouse function module of the DobotStudio to perform tasks, for example, grab or suck an object with your mouse. This topic introduces how to move a small cube with a mouse. Prerequisites

* The Dobot Magician is powered on and connected to your computer.
* The suction cup kit has been installed. For details, see 5.2.1 Installing a Suction Cup Kit.

Procedure

_Figure 5.99 Click Mouse_

_Figure 5.100 Choose SuctionCup as the end-effector_

![Figure 5.99 Click Mouse](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1oWF4HWTxdMBAD6bbT29%2Fmagician-p092-img22.jpg?alt=media)

_Figure 5.101 Set the parameters of mouse control_

_Table 5.14 Set the parameters of mouse control_

Parameters Description Speed The velocity percentage of the Dobot Magician: Unit: % Value range: 1-100 Default value: 50 Scale The scale of the Dobot Magician: Unit: % Value range: 1-100 Default value: 100 High Choose a performance mode suitable for your computer. Select Low performance/Low performance (default) for the low configuration computer to prevent video delay performance

![Figure 5.101 Set the parameters of mouse control](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3HhtkWz5oST4Ui8wxHYW%2Fmagician-p093-img12.jpg?alt=media)

**NOTICE**

Do not move the mouse outside the annular area. If not, the robotic arm reaches its limited position. In this case, drag the mouse to into the annular area.

_Figure 5.102 Move the robotic arm in the red annular area_

**NOTE**

For details on how to use the mouse to control the robotic arm on the Mouse page, see

_Table 5.15._

_Table 5.15 The robotic arm’s movement created with your mouse_

Mouse action Robotic arm’s movement Move your mouse front, The robotic arm moves accordingly back, right, or left Scroll the mouse wheel The robotic arm moves accordingly up or down Press and hold the left Suction cup: the air pump sucks air in mouse button Gripper: increase holding force Release the left mouse Suction cup: the air pump is powered off button Gripper: open Right-click the mouse Gripper: close button

![Figure 5.102 Move the robotic arm in the red annular area](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtuHVSecAsID0NTdpSZ2U%2Fmagician-p094-img05.jpg?alt=media)

### Operating 3D Printing

After installing 3D printing kit, you can import 3D module into the 3D printing software for 3D printing. Figure 5.103 shows the 3D printing process.

_Figure 5.103 3D printing process_

During 3D printing, the 3D printing control software is required. You can use Repetier Host or Cura software for 3D printing.

* Reptier-Host: Reptier-Host can slice with the third party slicing (such as CuraEngine,

Slic3r, etc), check and modify G-Code, control 3D printing manually. More parameter settings make Reptier-Host very flexible.

* Cure: The slicing of Cura is fast and stable. It has strong inclusiveness to 3D model structure and less parameter settings.

**NOTICE**

This section uses Windows as an example to describe how to perform 3D printing with Repetier Host and Cura. For Mac OS, only Cura is supported.

#### Installing 3D Printing Kit

3D printing kit contains extruder, hot end, motor cable, filament, and filament holder as shown in Figure 5.104.

_Figure 5.104 3D printing kit_

Procedure

![Figure 5.104 3D printing kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS2gw2WNgER86WVLuj05R%2Fmagician-p096-img07.jpg?alt=media)

_Figure 5.105 Push down the filament_

_Figure 5.106 Connect extruder and hot end_

**NOTICE**

Please make sure that the PTFE tube has been pushed down to the bottom of the hot end. Otherwise, it will cause abnormal discharge.

![Figure 5.105 Push down the filament](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3cm2btkfkY7h42t8b3oF%2Fmagician-p097-img06.jpg?alt=media)

![Figure 5.106 Connect extruder and hot end](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9hRkCajfLBT9trZXSwGC%2Fmagician-p097-img07.jpg?alt=media)

_Figure 5.107 Fix hot end_

![Figure 5.107 Fix hot end](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyLrlvKcGw1saGR5RA7S7%2Fmagician-p098-img16.jpg?alt=media)

_Figure 5.108 Connect hot end to the Forearm_

_Figure 5.109 Connect with extruder_

![Figure 5.108 Connect hot end to the Forearm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTzyf6lydaKGEfxh3z6f5%2Fmagician-p099-img11.jpg?alt=media)

![Figure 5.109 Connect with extruder](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzsHxdzqRSTZ8NrRNrfpG%2Fmagician-p099-img12.png?alt=media)

_Figure 5.110 Place filament and extruder to the Filament holder_

#### Operating Repetier Host

Repeiter Host has been built into DobotStudio. After burning 3D printing firmware, the Repetier Host page will be displayed automatically. Prerequisites

* The 3D printing model has been prepared.
* The printing platform has been prepared and please place it in the workspace of the Dobot

Magician.

* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully (Only USB connection is supported).
* The 3D printing kit has been installed.

**5.9.2.1 Burning Firmware**

Procedure The 3D Printing FM page is displayed, as shown in Figure 5.111.

![Figure 5.110 Place filament and extruder to the Filament holder](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FROcW09DQSAkLaLQJcS4y%2Fmagician-p100-img07.jpg?alt=media)

_Figure 5.111 Burn firmware_

After burning 3D printing firmware, the Repetier Host page is displayed automatically, as shown in Figure 5.112. If the LED indicator on the base turns red, it indicates that the connection of the 3D printing kit is abnormal.

**WARNING**

Please DO NOT operate or turn off Dobot Magician when burning firmware, to avoid machine damage.

![Figure 5.111 Burn firmware](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwWjmemRHtDM3tpi5M4Jr%2Fmagician-p101-img05.png?alt=media)

_Figure 5.112 Repetier Host page_

**NOTICE**

If the current firmware is set for 3D printing when operating 3D printing, you can click Connect directly on the DobotStudio page. And then Click OK on the Select tool page to switch to Repetier Host, as shown in Figure 5.113.

_Figure 5.113 Switch into 3D printing automatically_

**5.9.2.2 Performing 3D Printing**

Procedure Printing parameters only need to be set for the first time.

![Figure 5.112 Repetier Host page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F347wGqcpKsArcBqdxq2D%2Fmagician-p102-img03.png?alt=media)

![Figure 5.113 Switch into 3D printing automatically](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXFqCnTA7M8o4ahJmAMtg%2Fmagician-p102-img05.jpg?alt=media)

Click Printer Settings on the top right corner of the Pepetier Host page. The Printer Settings page is displayed. Set the corresponding parameters on the Connection tab as shown in the red box of Figure 5.114. The other parameters are set by default.

_Figure 5.114 Connection setting_

Click Apply. Unselect the corresponding options on the Printer tab as shown in the red box of, Figure 5.115 and the other parameters are set by default. Then, click Apply.

![Figure 5.114 Connection setting](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD6c3xTCAxLzoA4PqAwRz%2Fmagician-p103-img05.png?alt=media)

_Figure 5.115 Unselect options_

Set the corresponding parameters on the Extruder tab as shown in the red box of

_Figure 5.116, the other parameters are set by default. Then, Click Apply._

![Figure 5.115 Unselect options](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAmeZR7zGciJd0tkdcp3Q%2Fmagician-p104-img02.png?alt=media)

_Figure 5.116 Extruder settings_

Set the corresponding parameters on the Printer Shape tab as shown in the red box of Figure 5.117, the other parameters are set by default. Then, Click Apply.

![Figure 5.116 Extruder settings](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiKmOBigK54EvRLuvVZPy%2Fmagician-p105-img02.png?alt=media)

_Figure 5.117 Printer shape settings_

Click OK After the connection is successful, the current heating temperature will be shown on the below of the Repetier Host page, as shown in Figure 5.118.

_Figure 5.118 Connect to Dobot Magician_

![Figure 5.117 Printer shape settings](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSirSrug8vPQewG8Vi2VQ%2Fmagician-p106-img08.png?alt=media)

![Figure 5.118 Connect to Dobot Magician](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fie71wDFnmMHU7hyR8A74%2Fmagician-p106-img09.png?alt=media)

Before printing, you need to test the extruder to check whether the melted filament flows from the nozzle of the extruder. The temperature of the extruder should be above 170℃. Dobot Magician will not start 3D printing until the filament is in the melting state. So you need to heat the extruder first. Set the heating temperature to 200℃ on the Manual Control tab of the Repetier Host page and click, as shown in Figure 5.119.

**DANGER**

The heating rod will produce high temperature up to 250℃, please be careful. Do not let children play with it alone. The process needs to be monitored when it is running. After the process is completed, please turn off the equipment promptly.

_Figure 5.119 Heat the extruder_

Click the extruder feeder when the heating temperature is up to 200℃ and feed up to10mm-30mm, as shown in Figure 5.120.

![Figure 5.119 Heat the extruder](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYBTxuqthFt78U0OB2Qo2%2Fmagician-p107-img07.jpg?alt=media)

_Figure 5.120 Extrude filament_

If the melted filament flows from the nozzle of the extruder, the extruder is working properly.

**NOTICE**

If the filament extrusion is in the opposite direction. Please remove the filament, and turn the extruder around, then re-push down the filament.

**NOTE**

During printing, if the distance from Dobot Magician to the printing platform is too large or too small to paste the first layer, it can lead to the nozzle blockage. For increasing the stickiness of the first layer, placing a masking paper on the platform is recommended. Press the Unlock key on the Forearm and drag Dobot Magician to make the printing head contact the surface of the masking paper (The distance between the printing head and the surface of the masking paper is the thickness of a sheet of A4 paper), then release the Unlock key. Input command M415 on the G-Code command window and press Enter to get

![Figure 5.120 Extrude filament](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrVkZMFlK2QDTGMJWrTzP%2Fmagician-p108-img05.png?alt=media)

Also, you can press the Key button on the bace of the base to get the current coordinates.

_Figure 5.121 Input M415_

**NOTE**

If you cannot find the G-Code command window, please click EASY to close Easy Mode, as shown in Figure 5.122.

_Figure 5.122 Easy mode_

![Figure 5.121 Input M415](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOVk6FT3PWWwf8vMWWGro%2Fmagician-p109-img08.png?alt=media)

![Figure 5.122 Easy mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA1BWJjgf4EuZPI7XEHv9%2Fmagician-p109-img09.png?alt=media)

_Figure 5.123 Import 3D printing Model_

After importing the model, you can center, zoom, or rotate the model on the Object Placement page, as shown in Figure 5.124.

![Figure 5.123 Import 3D printing Model](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKfan9WlcMNt5hVR5pHZo%2Fmagician-p110-img08.png?alt=media)

![Figure 5.124 Model operation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq1B8HSvqtGwegYUkJJDO%2Fmagician-p110-img09.png?alt=media)

You need to set the slicing parameters before first printing. Select Slic3r from Slicer on the Slicer tab of the Repetier Host page, and click Configuration, as shown in Figure 5.125.

_Figure 5.125 Select slicer_

The Slic3r page is displayed, as shown in Figure 5.126.

![Figure 5.125 Select slicer](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdStVJDUJGBUPf28NKPuf%2Fmagician-p111-img04.png?alt=media)

_Figure 5.126 Slic3r page_

Set the slicing parameters on the Slic3r page. The 3D printing effect depends on the slice parameters. This topic provides a configuration sample, you can select File > Load Config on the Slic3r page to import it directly for printing. The path of the configuration sample is Installation directory\DobotStudio\attachment, as shown in Figure 5.127.

_Figure 5.127 Configuration sample_

![Figure 5.126 Slic3r page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp6NQLs2YAMqY9Cl3Dpui%2Fmagician-p112-img02.png?alt=media)

![Figure 5.127 Configuration sample](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqjaitJdvvQldqbjQwwEk%2Fmagician-p112-img03.png?alt=media)

is used for the filling, the filling rate is 20%. Save the Printing Settings, Filament Settings and Printer Settings tabs respectively after importing configuration sample, as shown in Figure 5.128.

_Figure 5.128 Save configuration file_

Click Slici with Slic3r on the Slicer tab of the Repetier Host page, as shown in

_Figure 5.129._

_Figure 5.129 Start to slice_

Click on the top left corner of the Repetier Host page to print.

![Figure 5.128 Save configuration file](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeB8sMLGnwGCpeCwONvNQ%2Fmagician-p113-img04.png?alt=media)

![Figure 5.129.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXnihPy4fAvO9scL3b94F%2Fmagician-p113-img05.png?alt=media)

_Figure 5.130 Start printing_

Here we choose vase mode to print, and the product after printing as shown in Figure 5.131.

_Figure 5.131 The product of printing_

![Figure 5.130 Start printing](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FN2EDVpDdjuc7CQmh5pkB%2Fmagician-p114-img01.png?alt=media)

![Figure 5.131 The product of printing](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdGSieedvVizY9GJF3tSC%2Fmagician-p114-img02.jpg?alt=media)

#### Operating Cura

If you need to use Cura software for 3D printing, please launch the Cura software after burning firmware. Prerequisites

* Slice software Cura has been installed.

The download path is https://ultimaker.com/en/products/ultimaker-cura-software/list. Please download the recommended version V14.07. The way how to install and use is not descripted in this topic.

* The 3D printing model has been prepared.
* The printing platform has been prepared and please place it in the workspace of Dobot

Magician.

* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully (Only USB connection is supported).
* The 3D printing kit has been installed.

**5.9.3.1 Burning Firmware**

Procedure The 3D Printing FM page is displayed, as shown in Figure 5.132.

_Figure 5.132 Burn firmware_

After burning 3D printing firmware, if the LED indicator on the base turns red, it indicates that the connection of the 3D printing kit is abnormal.

**WARNING**

Please DO NOT operate or turn off Dobot Magician when burning firmware, to avoid machine damage.

**5.9.3.2 Performing 3D Printing**

Procedure Select Machine > settings on the Cura page. The Machine settings page is displayed. Set the corresponding parameters on the Machine settings and click OK, as shown in Figure 5.133. Table 5.16 lists the values of the parameters that need to be set. The other parameters are set by default.

_Figure 5.133 Parameters setting_

_Table 5.16 3D printing parameters description_

Parameter Description Maximum width The maximum width please set to 80mm Maximum depth The maximum with please set to 80mm Maximum height The maximum height Please set to 150mm

![Figure 5.133 Parameters setting](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1KxITdBvNShAz3BWrIKs%2Fmagician-p116-img10.png?alt=media)

Parameter Description Machine center 0,0 Machine center, please select it GCode Flavor The style of GCode Please select RepRap Marlin/Sprinter Build area shape Build the area shape Please select Circular Serial port Serial port Please select the corresponding serial port Baudrate Baud rate Please set to 115200 Set slice parameters, and select File > Open Profile to import these parameters, as shown in Figure 5.134.

_Figure 5.134 Import slice parameters_

The 3D printing effect depends on the slice parameters. This topic provides a configuration sample, you can import it directly for printing. The path of the configuration sample is Installation directory\DobotStudio \attachment, as shown in Figure 5.135.

![Figure 5.134 Import slice parameters](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FofkI1wZ6i8cvOq6kuEHF%2Fmagician-p117-img02.png?alt=media)

_Figure 5.135 Configuration sample_

Dobot-2.0-Vase-Cura.ini is used for printing a thin-walled vase, while Dobot- 2.0-Cura.ini is used for the filling, the filling rate is 20%. Click, the Open 3D model page is displayed, and select the 3D printing model prepared. The format of 3D model is STL. You can design 3D model and transform it into STL format. After importing the model, click the model itself, you can center, zoom or rotate, and so on, as shown in Figure 5.136.

_Figure 5.136 Zoom and rotate_

Click to connect with Dobot Magician.

![Figure 5.135 Configuration sample](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRJggWANTGq81JoHgd9Sx%2Fmagician-p118-img03.png?alt=media)

![Figure 5.136 Zoom and rotate](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FveS2074MBNSvMNG5i2eN%2Fmagician-p118-img05.jpg?alt=media)

The printing window is displayed and the current printing temperature is shown on the top corner of the window, as shown in Figure 5.137.

_Figure 5.137 Printing window_

Set Temperature to 200 and press down Enter to heat the extruder. The temperature of the extruder should be above 170℃. Dobot Maigicain will not start 3D printing until the filament is in the melting state. So you need to heat the extruder first.

**DANGER**

The heating rod will produce high temperature up to 250℃, please be careful. Do not let children play with it alone. The process needs to be monitored when it is running. After the process is completed, please turn off the equipment promptly. Before printing, you need to test the extruder to check whether the melted filament flows from the nozzle of the extruder. Click the feedstock extruder or click the given stepper, such as 10, 1, 0.1 (10 is recommended) on the Operational page and feed up to 10mm-30mm, as shown in

_Figure 5.138._

![Figure 5.137 Printing window](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyE5JuAuBExK5tqCjgVjF%2Fmagician-p119-img04.png?alt=media)

_Figure 5.138 Click feedstock extruder_

If the melted filament flows from the nozzle of the extruder, the extruder is working properly.

**NOTICE**

If the filament extrusion is in the opposite direction, please remove the filament, and turn the extruder around, then re-push down the filament.

**NOTE**

During printing, if the distance from Dobot Magician to the printing platform is too large or too small to paste the first layer, it can lead to the nozzle blockage. For increasing the stickiness of the first layer, placing a masking paper on the platform is recommende. Press the Unlock key on the Forearm and drag Dobot Magician to make the printing head contact the surface of the masking paper(The distance between the printing head and the surface of the masking paper is the thickness of a sheet of A4 paper), then release the Unlock key. Input command M415 on the lower right of the Operational page to get the current coordinates, as shown in Figure 5.139. Also, you can press the Key button on the bace of the base to get the current coordinates.

![Figure 5.138 Click feedstock extruder](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW5TYLvUyj8v8YdefhAqW%2Fmagician-p120-img05.jpg?alt=media)

_Figure 5.139 Input command M415_

### Calibration

#### Base Calibration

The base Encoder has been calibrated before being shipped out. Generally, the J1-coordinate is 0° after homing, where the homing point is the system default. Namely, the Forearm is located at the middle in front of the base. If the J1-coordinate is not 0° (error range: 1°-3°) after homing, you need to re-calibrate the base Encoder. Prerequisites

* The writing and drawing kit has been installed. For details, please see 5.4.1 Installing a

Writing and drawing kit.

* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully.
* The sensor calibration board has been prepared.

Procedure

![Figure 5.139 Input command M415](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZDjFoTjSmsioGevnqjcg%2Fmagician-p121-img13.png?alt=media)

_Figure 5.140 Location of Dobot Magician_

This step is used for observing the nib position on the calibration board when moving J1-axis in Step 5, to improve calibration accuracy. Click Teaching\&Playback on the DobotStudio page. The Teaching\&Playback page is displayed. Press the Unlock key on the Forearm and drag Dobot Magician to make the nib contact the surface of the calibration board, then release the Unlock key. The coordinates of this point will be displayed on the Teaching\&Playback page. Select this point and right-click SetHome, as shown in Figure 5.141.

_Figure 5.141 Set homing position_

![Figure 5.140 Location of Dobot Magician](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTXhYgpFN7TfEhfsTMoah%2Fmagician-p122-img07.jpg?alt=media)

![Figure 5.141 Set homing position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxVaZ6x6CawLn2b3oUSep%2Fmagician-p122-img08.png?alt=media)

Dobot will start homing. Please ensure that there are no obstacles in the workspace during homing. If the speed is too fast when moving J1-axis, you can drag Speed slider to adjust speed.

_Figure 5.142 Move J1-axis_

![Figure 5.142 Move J1-axis](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FALrygIGAhzI5HUPkGG5Q%2Fmagician-p123-img27.png?alt=media)

_Figure 5.143 Nib position_

You can check the J1-coordinate on the Operation Panel page, as shown in Figure 5.144.

![Figure 5.143 Nib position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMSxciGYUxaZ4UksGTu8z%2Fmagician-p124-img05.jpg?alt=media)

![Figure 5.144 J1-coordinate](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F25ehq75BlH9YiFk5Lpqa%2Fmagician-p124-img06.jpg?alt=media)

#### Sensor Calibration

The angle sensors of the Forearm and Rear Arm have been calibrated before being shipped out. Generally, the Z-coordinate will remain the same when moving Dobot Magician in the same horizontal plane. If changed, you need to recalibrate the angle sensors by manual levelling or auto levelling to improve the positioning accuracy.

* Manual Levelling: It is more accurate to calibrate manually with DobotStudio, sensor calibration board, and writing and drawing kit, which is suitable for the application scenarios with high requirements for absolute positioning accuracy.
* Auto Levelling: It is simple and quick to calibrate automatically with DobotStudio and auto-levelling tool, which is suitable for the application scenarios without high requirements for absolute positioning accuracy, such as writing and drawing, 3D printing.

**5.10.2.1 Manual Levelling**

Prerequisites

* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully.
* The sensor calibration board has been prepared.

Procedure

_Figure 5.145 Location of Dobot Magician_

The Manual Levelling page is displayed.

**NOTICE**

Please remove all end-effectors from Dobot Magician before calibrating

_Figure 5.146 Get the angle sensor coefficients_

![Figure 5.146 Get the angle sensor coefficients](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTsA9ymBlDDORWgA2IwfN%2Fmagician-p126-img16.png?alt=media)

_Figure 5.147 Set precisions_

Install the writing and drawing kit. For details, please see 5.4.1 Installing a Writing and drawing kit. Press the Unlock key on the Forearm and drag Dobot Magician to make the nib near the A3 point on the calibration board, then release the Unlock key. Click coordinate buttons on the Manual Levelling page (as shown in Figure 5.148) to make the nib align to the center of A3 point on the calibration board, as shown in Figure 5.149. If the speed is too fast when clicking coordinate buttons, you can drag Speed slider to adjust speed.

![Figure 5.147 Set precisions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIEpwTVSVJ1uG6Hi5Fu3w%2Fmagician-p127-img14.png?alt=media)

_Figure 5.148 Fine-tune page_

_Figure 5.149 Nib position_

![Figure 5.148 Fine-tune page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FswFN9lYOCIvtjikXzvEm%2Fmagician-p128-img09.png?alt=media)

![Figure 5.149 Nib position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCk42jI62rpBfnc7TAvZI%2Fmagician-p128-img10.jpg?alt=media)

**NOTICE**

Please DO NOT drag Dobot Magician in this step, to avoid manual levelling failure. If the speed is too fast when clicking coordinate buttons, you can drag Speed slider to adjust speed.

_Figure 5.150 Fine-tune page_

_Figure 5.151 Nib position on the second calibrated point_

![Figure 5.150 Fine-tune page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhcZsokLj8f7kngLLyDgO%2Fmagician-p129-img07.png?alt=media)

![Figure 5.151 Nib position on the second calibrated point](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNTXU5AE1sp7JYlsLOdq9%2Fmagician-p129-img08.jpg?alt=media)

The distance between the two calibrated points on the Calibration board is 80mm, so please keep the default value in this step.

_Figure 5.152 Set the distance between the two calibrated points_

The result is shown as Figure 5.153.

![Figure 5.152 Set the distance between the two calibrated points](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9MlRi8ZQCWvLMQ0G1v1Q%2Fmagician-p130-img11.jpg?alt=media)

![Figure 5.153 Calibrating result](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5oYQ8hExwbVFqp80Z7BZ%2Fmagician-p130-img12.png?alt=media)

**5.10.2.2 Auto Levelling**

Prerequisites

* Dobot Magician has been connected to a PC via USB cable.
* Dobot Magician has been connected to the power adapter.
* The auto-levelling tool has been obtained, as shown in Figure 5.154.

_Figure 5.154 Auto-levelling tool_

Procedure

**NOTICE**

Please ensure that the platform is flat. Or, the auto levelling will be failed.

![Figure 5.154 Auto-levelling tool](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmzfEVfvpf7EBZkbNPKpN%2Fmagician-p131-img08.jpg?alt=media)

_Figure 5.155 Fix auto-levelling tool_

![Figure 5.155 Fix auto-levelling tool](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGgBoxI8XF4dXuhi7HCUR%2Fmagician-p132-img09.jpg?alt=media)

_Figure 5.156 Insert the cable of the auto-levelling_

![Figure 5.156 Insert the cable of the auto-levelling](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8V3NHi3TvsfbKWYyonWp%2Fmagician-p133-img09.png?alt=media)

**NOTICE**

Please ensure that there are no obstacles in the workspace during auto levelling.

_Figure 5.157 Auto levelling page_

**NOTE**

If the auto levelling is failed, please check if the platform is flat and try again.

![Figure 5.157 Auto levelling page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FY9cjE8CfxNSALoHc1RnP%2Fmagician-p134-img14.jpg?alt=media)

_Figure 5.158 Auto levelling result_

#### Homing

Dobot Magician has been calibrated before being shipped out. If the Dobot Magician has been hit or the motor has lost step, leading data abnormal, you need to operate homing to improve the positioning accuracy. Prerequisites

* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully.

Procedure Click Home on the DobotStudio page, as shown in Figure 5.159.

**NOTICE**

* Please remove the end-effector from the Dobot Magician before homing.
* Please ensure that there are no obstacles in the workspace during homing.

_Figure 5.159 Operate homing_

Dobot Magician will rotate clockwise to the limited position and then return to the default

![Figure 5.158 Auto levelling result](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff765mCS6xhXHvR5WQ8cP%2Fmagician-p135-img02.png?alt=media)

homing is successful, there is a beep sound and the LED indicator turns green. Also, the homing point can be use-defined, you can select a saved point on the Teachong\&Playback page and right-click SetHome to set this saved point as the homing point, as shown in Figure 5.160.

_Figure 5.160 Set homing point_

### Connecting with WIFI Kit

You can connect Dobot Magician to a PC via WIFI kit without USB cable, making Dobot Magician and PC in the same WLAN. Figure 5.161 shows the WIFI kit.

_Figure 5.161 WIFI kit_

![Figure 5.160 Set homing point](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFKR6wdicLwpLTIuFbGdB%2Fmagician-p136-img02.jpg?alt=media)

* Dobot Magician has been connected to a PC via USB cable.
* Dobot Magician has been connected to the power adapter.
* The WIFI name and password have been obtained and must be the same as that of PC.

Procedure

_Figure 5.162 Connect with WIFI kit_

**NOTICE**

Please turn off the Dobot Magician completely first before connecting or disconnecting external equipment. Or, it causes serious damage to your device. After turning on, there are two short beep sounds and the blue LED indicator on the WIFI module is on. The Set Dobot Wi-Fi page is displayed. If you unselect Dynamic Host Configuration Protocol (DHCP), you need to set IP address, Netmask, Gateway. For details, please see Table 5.17.

![Figure 5.162 Connect with WIFI kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fss248DOjVzrDIvyjWlFN%2Fmagician-p137-img26.png?alt=media)

_Figure 5.163 Set WIFI_

_Table 5.17 Parameter description_

Parameter Description SSID Set WIFI name The WIFI name and password have been obtained and must be the same as that of PC Password Set WIFI password Dynamic Host Configuration Whether to select DHCP Protocol (DHCP) Yes: Only set SSID and Password No: Only set IPAddress, Netmask and Gateway IPAddress Set the IP address of Dobot Magician. The IP address of Dobot Magician and the PC must be in the same WLAN without conflict. Netmask Set subnet mask Gateway Set gateway DNS Set DNS

![Figure 5.163 Set WIFI](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeguiKrghoC1rSlUrZqgx%2Fmagician-p138-img05.png?alt=media)

About 5 seconds later, the green LED indicator on the WIFI module is on, indicating that the Dobot Magician has been connected with WLAN.

_Figure 5.164 IP address of Dobot Magician_

After the connection is successful, you can control Dobot Magician without USB cable.

### Connecting with Bluetooth Kit

Dobot Magician can be connected to smart phone with Bluetooth. Figure 5.165 shows the Bluetooth kit. Please download the matched DobotStudio APP from the website https://cn.dobot.cc/downloadcenter.html?sub\_cat=69#sub-download.

_Figure 5.165 Bluetooth kit_

![Figure 5.164 IP address of Dobot Magician](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8arxMja9hbo6haOHaz6u%2Fmagician-p139-img14.jpg?alt=media)

* Dobot Magician has been connected to the power adapter.
* The DobotStudio APP has been downloaded.

Procedure

_Figure 5.166 Connect with Bluetooth kit_

**NOTICE**

Please turn off the Dobot Magician completely first before connecting or disconnecting external equipment. Or, it causes serious damage to your device. After turning on, there are three short beep sounds and the blue LED indicator on the Bluetooth module is on and the green one is blinking. Turn on the Bluetooth and launch DosbotStudio APP on your phone. And click Connect to connect with Dobot Magician. This topic only describes how to connect Bluetooth kit. For details how to operate Dobot Magician with DobotStudio APP, please see https://www.youtube.com/watch?v=kyeXwuf17IY.

### Operating Blockly

Blockly is a programming platform based on Google Blockly. You can program through the puzzle format, which is straightforward and easy to understand. Prerequisites

* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully.

Procedure

_Figure 5.167 Blockly graphic programming_

_Table 5.18 lists the description of blockly module._

_Table 5.18 Blockly description_

No. Description 1 The selection area of blockly module, including logistic, loop, math, and Dobot API. You can program by dragging them to the window. 2 The window of blockly programming 3 The running log of Dobot Magician 4 The corresponding codes of the blockly module on the programming window The demo in Figure 5.167 is described as follows. Set the end-effector as Gripper. Set the loop number as 3 and make the Z-axis move back and forth 3 times. Set the pause time as 3. The Saving Blockly file page is displayed.

![Figure 5.167 Blockly graphic programming](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdTycA6viyMBaHBpv8Ret%2Fmagician-p141-img32.png?alt=media)

### Scripting

You can control Dobot Magician over scripting. Dobot Magician supports various API, such as velocity/acceleration setting, motion mode setting, and I/O configuration, which uses Python language for secondary development. For details about the Dotob Magician API interface and function description, please see Dobot Magician API Description. The download path is https://www.dobot.cc/downloadcenter.html?sub\_cat=72#sub-download. Prerequisites

* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully.

Procedure The Script page is displayed. You can call the interface by double-clicking on the left pane of the Script page, the corresponding interface will be displayed on the middle pane, as shown in Figure 5.168. You can also click icon of the corresponding interface to view the way how to set the parameters. The scripting examples (including Jog, PTP, and Pallet) can refer to Installation directory/DobotStudio/config/ststore/.

_Figure 5.168 Write a script_

The Saving Scrip File page is displayed.

![Figure 5.168 Write a script](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVJbuAbVMu4JYZ2u2f3rq%2Fmagician-p142-img24.png?alt=media)

The running log will be displayed on the lower pane of the Script page for checking.

### Operating Stick Controller Kit

Dobot Magician can be controlled by stick controller kit without DobotStudio. Figure 5.169 shows the stick controller kit. From left to right: Stick controller, USB Host module, USB cable (used for charging stick controller), Transceiver.

_Figure 5.169 Stick controller kit_

**NOTICE**

* Please don’t connect Dobot Magician to DobotStudio when operating the stick controller.
* Please turn off the Dobot Magician completely first before connecting or disconnecting external equipment. Otherwise, it causes serious damage to your device. Prerequisites Dobot Magician has been connected to the power adapter. Procedure

![Figure 5.169 Stick controller kit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FISdMwJBkgBaGcS5XHbK8%2Fmagician-p143-img13.jpg?alt=media)

_Figure 5.170 Connect with USB Host module_

The red LED indicator on the middle of the stick controller is blinking, indicating that the Dobot Magician can be controlled by the stick controller.

![Figure 5.170 Connect with USB Host module](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fg7k5HDHv8KVjV8uZ3Mkh%2Fmagician-p144-img09.jpg?alt=media)

_Figure 5.171 Power button of the stick controller_

_Table 5.19 lists the functions of buttons on the stick controller._

_Table 5.19 Button function_

Button Function Power button Turn on stick controller The stick controller will turn off automatically LT Turn on the peripheral motor RT Turn off the peripheral motor off RB Switch to Cartesian coordinate system mode LB Switch to Joint coordinate system mode X Control the outtake of the air pump Y Control the intake of the air pump B Turn off the air pump Left stick: Front/back • Cartesian coordinate system mode: Dobot Magician moves along X-axis in the positive/negative direction

* Joint coordinate system mode: Dobot Magician rotates along J1-axis in the positive/negative direction

![Figure 5.171 Power button of the stick controller](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYIK0mfX4yQM6OR3hHImD%2Fmagician-p145-img01.jpg?alt=media)

Button Function Left stick: Left/right • Cartesian coordinate system mode: Dobot Magician moves along Y-axis in the positive/negative direction

* Joint coordinate system mode: Dobot Magician rotates along J2-axis in the positive/negative direction Right stick: Front/back • Cartesian coordinate system mode: Dobot Magician moves along Z-axis in the positive/negative direction
* Joint coordinate system mode: Dobot Magician rotates along J3-axis in the positive/negative direction Right stick: Left/right • Cartesian coordinate system mode: Dobot Magician rotates along R-axis in the positive/negative direction
* Joint coordinate system mode: Dobot Magician rotates along J4-axis in the positive/negative direction

### Multiplexed I/O Demo

The addresses of the I/O interfaces in Dobot Magician are unified. Most of I/O interfaces have multiple functions. For details, please see 4.3 Multiplexed I/O Interface Description. You can set I/O interfaces on the advanced Teaching\&Playback page to control the peripheral equipment, as shown in Figure 5.172.

_Figure 5.172 I/O setting page_

![Figure 5.172 I/O setting page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FV8mRYHnqXcL9FoZ2dPkL%2Fmagician-p146-img02.png?alt=media)

Now, demos of level output, level input, and PWM output are given below.

#### Level Output

Normally, air pump can be controlled by the I/O interfaces. The I/O 11 controls its intake (High level) and outtake (Low level) and the I/O 16 controls its start-stop. Table 5.20 lists the multiplexed descriptions of I/O 11 and I/O 16.

_Table 5.20 Multiplexed I/O description_

I/O addressing Voltage Level Output PWM Level Input ADC 11 3.3V √ √ - - 16 12V √ - - - The I/O 11 and I/O 16 are located at the peripheral interface of the base, as shown in Figure 5.173.

_Figure 5.173 Peripheral Interface on the base_

Prerequisites

* The air pump has been connected to Dobot Magician. For details, please see 5.2.1
* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully.

Procedure

![Table 5.20 Multiplexed I/O description](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5IRYboUyt9BwCF2mxkNa%2Fmagician-p147-img09.png?alt=media)

_Figure 5.174 Select end-effector_

**NOTICE**

Normally, If SuctionCup or Gripper is selected from the end-effector drop-down list after the air pump has been connected, the air pump will be controlled by the system. In this topic, we use I/O interfaces to control the air pump, so SuctionCup and Gripper cannot be selected, to avoid conflict.

_Figure 5.175 Switch advanced function_

“The saved point is displayed on the Teaching\&Playback page, as shown in Figure 5.176.

**NOTE**

If the intake is not obvious, please modify PauseTime of this saved point.

![Figure 5.174 Select end-effector](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqTz7zakWYjqccrHG4kqj%2Fmagician-p148-img18.png?alt=media)

_Figure 5.176 Saved point_

The air pump is humming with intake. The saved point is displayed on the Teaching\&Playback page, as shown in Figure 5.177.

_Figure 5.177 Saved point_

#### Level Input

![Figure 5.176 Saved point](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQN6DhbMMALTWHfS7IOCq%2Fmagician-p149-img21.png?alt=media)

![Figure 5.177 Saved point](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfRrZrt6ucEee4Y8d5oEO%2Fmagician-p149-img22.png?alt=media)

This topic also takes I/O 12 as an example.

_Table 5.21 Multiplexed I/O description_

I/O addressing Voltage Level Output PWM Level Input ADC 12 3.3V - - √ - Prerequisites

* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully.
* The saved points list has been existed on the Teaching\&Playback page.

Procedure

_Figure 5.178 Switch advanced function_

_Figure 5.179 Saved point_

![Table 5.21 Multiplexed I/O description](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkZM1EEgLiWOqT8fx3euA%2Fmagician-p150-img35.png?alt=media)

#### PWM OUTPUT

This topic also takes I/O 11 as an example.

_Table 5.22 Multiplexed I/O description_

I/O addressing Voltage Level Output PWM Level Input ADC 11 3.3V √ √ - - Prerequisites

* Dobot Magician has been powered on.
* Dobot Magician has been connected to DobotStudio successfully.

Procedure

_Figure 5.181 Saved point_

The EIO Setting page is displayed, as shown in Figure 5.182.

![Table 5.22 Multiplexed I/O description](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMySphmGCBQ3bFZ0dIRjH%2Fmagician-p151-img24.png?alt=media)

_Figure 5.182 EIO setting_

![Figure 5.182 EIO setting](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcOtYsJ6dL5efLgzTen0s%2Fmagician-p152-img10.png?alt=media)

## Appendix A Dobot Magician Homing Operation

Homing Procedure：

_Figure 5.183 homing tip_

Playback Procedure： If there are some points saved in Dobot Magician before, you can turn on Dobot Maigican directly, wait for about 20 seconds after green light is on, press down Key button for long time to execute homing operation, and then press down Key button again to execute offline mode.

![Figure 5.183 homing tip](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxKp4sREbLllUVsLqqVM1%2Fmagician-p153-img19.jpg?alt=media)
