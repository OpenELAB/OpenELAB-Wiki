---
description: >-
  Official V1.1 operation guide. The linked OpenELAB gripper products apply only
  to their PGC-50-35 variants; the source also describes other gripper models.
---

# DOBOT DH-Robotics Electric Parallel Gripper Operation Guide

## DOBOT DH PGC-50-35 Collaborative Parallel Gripper

{% embed url="https://openelab.io/products/dobot-pgc50-collaborative-parallel-gripper" %}

## DOBOT NOVA Electric Grippers - PGC-50 variant only

{% embed url="https://openelab.io/products/dobot-grippers-nova-robots?variant=47169190953158" %}

## DOBOT CRA DH Robotics Grippers - PGC-50 variant only

{% embed url="https://openelab.io/products/dobot-dh-robotics-grippers-cra-robots?variant=47169192591558" %}

[Official manual PDF](https://dobot-cloud-1256299428.cos.accelerate.myqcloud.com/dobot/CRA%20%26%20Nova%20Accessories_DH-Robotics%20Electric%20Parallel%20Gripper%20Operation%20Guide-PGC50_2024-06-11_en.pdf)

**Applicability:** Among several gripper models, this source explicitly covers PGC-50-35. The NOVA and CRA links above select only the PGC-50 variant; it is not an AG-95 manual.

## Contents

* Preface
* 1\. Introduction
* 2\. Hardware installation
* 3\. Software operation

## Copyright and Disclaimer

### Copyright © ShenZhen Yuejiang Technology Co., Ltd 2023. All rights reserved.

No part of this document may be reproduced or transmitted in any form or by any means without prior written consent of Yuejiang Technology Co., Ltd.

### Disclaimer

To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided **AS IS** , which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents.

Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robotic arm is used on the premise of fully understanding the robotic arm and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. Dobot shall not be considered as a guarantee regarding to all security information contained in this document.

The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robotic arm.

Shenzhen Yuejiang Technology Co., Ltd. Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China

Website: www.dobot-robots.com

## Preface

#### Purpose

This document describes the installation and use of DH-Robotics electric parallel grippers applied to the end of Dobot six-axis robots, which is convenient for users to fully understand and use DH-Robotics electric parallel grippers.

#### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

### Revision history

| Date       | Version | Change                    |
| ---------- | ------- | ------------------------- |
| 2023-10-11 | V1.1    | Based on software V4.4.0. |
| 2023-02-23 | V1.0    | First release.            |

#### Symbol conventions

The symbols that may be found in this document are defined as follows.

| Symbol  | Description                                                                                                                                               |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER  | <p>Indicates a hazard with a high level of risk which, if not avoided, could result<br>in death or serious injury</p>                                     |
| WARNING | <p>Indicates a hazard with a medium level or low level of risk which, if not<br>avoided, could result in minor or moderate injury, robotic arm damage</p> |
| NOTICE  | <p>Indicates a potentially hazardous situation which, if not avoided, can result in<br>robotic arm damage, data loss, or unanticipated result</p>         |
| NOTE    | <p>Provides additional information to emphasize or supplement important points<br>in the main text</p>                                                    |

## 1. Introduction

DH-Robotics electric parallel gripper can be installed at the end of the robot as an actuator, it communicates with the robot via ModbusRTU protocol. DH-Robotics has several series of electric parallel grippers, and the models described below are more typical for use with Dobot robot arms.

### 1.1 PGE-50-26

The PGE series is an industrial slim-type electric parallel gripper. The first number represents the maximum gripping force of the gripper, and the second number represents the maximum stroke of the gripper. The gripper is equipped with a pair of parallel fingertips, which runs symmetrically during movement. The main structure of the grippers is a smooth rectangular structure with 5 mounting holes to meet the different installation conditions of the equipment. It is also equipped with an 8-core communication interface.

### 1.2 PGC-50-35 / PGC-140-50

The PGC series is a collaborative electric parallel gripper. The first number represents the maximum gripping force of the gripper, and the second number represents the maximum stroke of the gripper. The gripper is equipped with a pair of parallel fingertips, which runs symmetrically during movement and meets different installation conditions of the equipment. It is also equipped with an 8-core communication interface.

### 1.3 AG-160-95

The AG series is a linkage-type adaptive electric gripper. The first number represents the maximum gripping force of the gripper, and the second number represents the maximum stroke of the gripper. The gripper is equipped with a pair of parallel fingertips, which runs symmetrically during movement. The main structure of the grippers is a smooth rectangular structure, and the bottom is adapted to the standard flange. It is also equipped with an 8-core communication interface for connecting to the end of the robot or other devices.

### 1.4 Indicator light definition

The above grippers are equipped with indicator lights, and the meaning of the indicator lights is the same.

* Uninitialized status: Red light flashes, other lights are off.
* Initialized status: The blue light is always on, indicating that it is in an operable status.
* Command received status: The red light flashes quickly once (the gripper indicator will appear to be purple since the blue light is always on at this time).
* Object caught status: Green light is always on, other lights are off.
* Object dropped status: Green light flashes.

![Official manual image, source page 6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEWBeutSF3KcOSyCho6yZ%2Fpgc50-p006-img01.jpg?alt=media)

## 2. Hardware installation

Please refer to the quick operation guide that came with the gripper to complete the installation and wiring of the gripper, it will not be described in details in this document.

## 3. Software operation

The software operation of each series of DH-Robotics electric parallel gripper is the same.

### 3.1 Plugin description

1. Open the DobotStudio Pro and enter the Dobot+ page to install **DHGrip** plugin.
2. After confirming that the gripper status is **Connected** , and confirming the ID and baud rate (if the gripper configuration has not been modified, keep the default values: ID = 1, baud rate = 115200), click **Initialize** .
3. After successful initialization, the plugin can be used to control the gripper.

NOTE

There may be opening and closing actions during the gripper initialization process, which is used to calibrate the gripper stroke. Please ensure that the gripper movement space is sufficient, so as to prevent injury from being pinched, and avoid initialization error.

![Official manual image, source page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEtDQUNov0gZrFr5Ldhla%2Fpgc50-p008-img01.png?alt=media)

![Official manual image, source page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh512xVydORxbFFyyKhIN%2Fpgc50-p008-img02.png?alt=media)

* The current width is the percentage of the current fingertip opening and closing of the gripper.
* The target width is used to set the target percentage of gripper fingertip opening and closing, and the gripper starts moving immediately after setting.
* The target force is used to set the target force percentage for the gripper to clamp or stretch the target object. When the gripper detects the force value, it will be judged that the target object has been grasped and the fingertip movement will be stopped.
* The target speed is used to set the speed percentage of gripper fingertip opening and closing.

NOTE

The AG series gripper does not support speed setting, settings for corresponding parameters are invalid.

### 3.2 End shortcut settings

After installing the DHGrip plugin, you can set the function of robot end shortcuts. Click **End shortcut key** button in the upper right corner of the Dobot+ home page to enter the configuration page.

The left side of the configuration page shows the position of the end button and the definition of Shortcut key 1 and Shortcut key 2, while the right side is used to configure the button functions.

* For **Plugin list** , select DHGrip plugin;
* For **Shortcut key 1/2** , you can configure it as follows:
  * DHGripper\_Open: Control the gripper to fully open.
  * DHGripper\_Close: Control the gripper to fully close.
  * No selection.
* For **Long press** , you can configure it as follows:
  * DHGripperInit: Initialize the gripper.
  * No selection.

After configuration, click **Save** , and you can control the gripper with the robot end shortcuts. Issue V1.1 (2023-10-11) Operation Guide Copyright © Yuejiang Technology Co., Ltd.

![Official manual image, source page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCuFiHThqfbOOAAV2c2TI%2Fpgc50-p009-img01.png?alt=media)

![Official manual image, source page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FayvFj8g2CGuCBNnrz2Gq%2Fpgc50-p009-img02.png?alt=media)

### 3.3 Programming command

After installing the DHGrip plugin, the relevant commands will appear in the graphical programming and script programming interface.

#### 3.3.1 Graphical programming

Description: Initialize the gripper.

Parameter: Device ID of the gripper. If the configuration of the gripper has not been modified, keep the default value 1.

Description: Control the gripper to move.

Parameter:

*
  1. Target width ratio of the gripper. Range: \[0, 100].
*
  2. Target force value ratio of the gripper. When the gripper detects the force value, it will be judged that the target object has been grasped and the fingertip movement will be stopped. Range: \[20, 100].
*
  3. Movement speed ratio of gripper fingertip opening and closing. Range: \[1, 100].
*
  4. Device ID of the gripper, the same as the device ID at initialization.
*
  5. When “Synchronization” is true, the robot will wait until the gripper movement is completed (the target width or force value is reached) before continuing to execute the later commands.

When “Synchronization” is false, the robot will continue to execute the later commands after delivering commands to the gripper.

Description: Get the current width ratio of the gripper.

Parameter: Device ID of the gripper, the same as the device ID at initialization.

Return: The current width ratio of the gripper, range: \[0, 100].

Description: Get the gripping status of the gripper.

Parameter: Device ID of the gripper, the same as the device ID at initialization.

Return: The gripping status value of the gripper, with the following meanings.

* 0: Moving, no object is detected.
* 1: Reached the specified position, no object is detected.
* 2: Gripped object. Judging by the force value, it may not have reached the specified position.
* 3: Object dropped.
* -1: Command execution error.

Description: Get the gripper initialization status.

Parameter: Device ID of the gripper, the same as the device ID at initialization.

Return: The initialization status value of the gripper, with the following meanings.

* 0: Initialization is not completed.
* 1: Initialization is completed.
* 2: Initializing.
* -1: Command execution error.

Description: Get the error code of the gripper.

Parameter: Device ID of the gripper, the same as the device ID at initialization. Return: The error code of the gripper. Refer to the user guide of corresponding gripper provided by DH-Robotics for details or consult DH-Robotics technical support.

#### 3.3.2 Script programming

Command: DHGripInit({id = 1}) Description: Initialize the gripper.

Optional parameter:

id: Device ID of the gripper. If the configuration of the gripper has not been modified, keep the default value 1.

Example:

DHGripInit({id = 1})

Command: DHGripControl(width, force, speed, {id = 1, isBlock = true}) Description: Control the gripper to move.

Required parameter:

* width: Target width ratio of the gripper. Range: \[0, 100].
* force: Target force value ratio of the gripper. When the gripper detects the force value, it will be judged that the target object has been grasped and the fingertip movement will be stopped. Range: \[20, 100].
* speed: Movement speed ratio of gripper fingertip opening and closing. Range: \[1, 100].

NOTE

The AG series gripper does not support speed setting, and setting the corresponding parameters does not work.

Optional parameter:

* id: Device ID of the gripper, the same as the device ID at initialization. “1” by default.
* isBlock: When it is true, the robot will wait until the gripper movement is completed (the target width or force value is reached) before continuing to execute the later commands.

When it is false, the robot will continue to execute the later commands after delivering commands to the gripper. “true” by default.

Example:

DHGripControl(20, 50, 50, {id = 1, isBlock = true})

Command: DHGripWidthGet({id = 1}) Description: Get the current width ratio of the gripper. Optional parameter: id: Device ID of the gripper, the same as the device ID at initialization. Return: The current width ratio of the gripper, range: \[0, 100]. Example: DHGripWidthGet({id = 1})

Command: DHGripMoveStatus({id = 1}) Description: Get the gripping status of the gripper. Optional parameter:

id: Device ID of the gripper, the same as the device ID at initialization.

Return: The gripping status value of the gripper, with the following meanings.

* 0: Moving, no object is detected.
* 1: Reached the specified position, no object is detected.
* 2: Gripped object. Judging by the force value, it may not have reached the specified position.
* 3: Object dropped.
* -1: Command execution error.

Example:

* DHGripMoveStatus({id = 1})

Command: DHGripInitStatus({id = 1}) Description: Get the gripper initialization status. Optional parameter:

id: Device ID of the gripper, the same as the device ID at initialization.

Return: The initialization status value of the gripper, with the following meanings.

* 0: Initialization is not completed.
* 1: Initialization is completed.
* 2: Initializing.
* -1: Command execution error.

Example:

DHGripInitStatus({id = 1})

Command: DHGripErrStatus({id = 1}) Description: Get the error code of the gripper. Optional parameter:

id: Device ID of the gripper, the same as the device ID at initialization.

Return: The error code of the gripper. Refer to the operation guide of corresponding gripper provided by DH-Robotics for details or consult DH-Robotics technical support.
