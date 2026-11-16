---
description: >-
  Operation guide for Robotiq 2F-85 and 2F-140 grippers used with DOBOT six-axis
  robots, covering hardware installation, plugin operation, shortcut settings,
  graphical programming, and script commands.
---

# DOBOT Robotiq 2F Gripper Operation Guide

## DOBOT Robotiq 2F-85 Adaptive Two-Finger Robot Gripper

{% embed url="https://openelab.io/products/dobot-robotiq-2f-85-adaptive-gripper" %}

## Contents

* Preface
* 1\. Introduction
* 2\. Hardware installation
* 3\. Software operation
* 3.1 Plugin description
* 3.2 End shortcut settings
* 3.3 Programming command
* 3.3.1 Graphical programming
* 3.3.2 Script programming

## Preface

Purpose This document describes the installation and use of Robotiq 2F grippers applied to the end of Dobot six-axis robots, which is convenient for users to fully understand and use Robotiq 2F grippers. Intended audience This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Revision history Date Version Revised content 2023-10-11 V1.0 The first release, based on software V4.4.0.0 Symbol conventions The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could result

**DANGER**

in death or serious injury Indicates a hazard with a medium level or low level of risk which, if not

**WARNING**

avoided, could result in minor or moderate injury, robotic arm damage Indicates a potentially hazardous situation which, if not avoided, can result

**NOTICE**

in robotic arm damage, data loss, or unanticipated result Provides additional information to emphasize or supplement important

**NOTE**

points in the main text

## 1. Introduction

Robotiq 2F gripper can be installed at the end of the robot as an actuator, and communicates with the robot via ModbusRTU protocol. Robotiq 2F-85&2F-140 grippers have two articulated fingers that each have two joints (two phalanges per finger). The grasp-type gripper can engage up to five points of contact with an object (two on each of the phalanges plus the palm). The fingers are under-actuated, meaning they have fewer motors than the total number of joints. This configuration allows the fingers to automatically adapt to the shape of the object they grasp, which simplifies the control of the gripper.

![Official manual figure, page 5](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtWxzB0ilJA7Y4e28WfGi%2Frobotiq-2f-p005-img01.jpg?alt=media)

## 2. Hardware installation

Please refer to the gripper installation instruction to complete the installation and wiring of the gripper, it will not be described in details in this document.

## 3. Software operation

### 3.1 Plugin description

1. Open the DobotStudio Pro and enter the Dobot+ page to install RobotiqGrip plugin.
2. After confirming that the gripper status is Connected, and confirming the ID and baud

rate (if the gripper configuration has not been modified, keep the default values: ID = 9, baud rate = 115200), click Initialize.

**NOTE**

There may be opening and closing actions during the gripper initialization process, which is used to calibrate the gripper stroke. Please ensure that the gripper movement space is sufficient, so as to prevent injury from being pinched, and avoid initialization error.

![Official manual figure, page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQMdY1y7f7VMl40r9Wz9b%2Frobotiq-2f-p007-img01.png?alt=media)

![Official manual figure, page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3AZ07jgwfsAiRm49Rcnl%2Frobotiq-2f-p007-img02.png?alt=media)

3. After successful initialization, the plugin can be used to control the gripper.

* The current width is the percentage of the current fingertip opening and closing of the gripper.
* The target width is used to set the target percentage of gripper fingertip opening and closing, and the gripper starts moving immediately after setting.
* The target force is used to set the target force percentage for the gripper to clamp or stretch the target object. When the gripper detects the force value, it will be judged that the target object has been grasped and the fingertip movement will be stopped.
* The target speed is used to set the speed percentage of gripper fingertip opening and closing.

### 3.2 End shortcut settings

After installing the RobotiqGrip plugin, you can set the functions for the robot end shortcuts. Click End shortcut key button in the upper right corner of the Dobot+ home page to enter the configuration page. The left side of the configuration page shows the position of the end button and the definition of Shortcut key 1 and Shortcut key 2, while the right side is used to configure the button functions.

* For Plugin list, select RobotiqGrip plugin;
* For Shortcut key 1/2, you can configure it as follows:

◦ RobotiqGripControl\_Open: Control the gripper to fully open. ◦ RobotiqGripControl\_Close: Control the gripper to fully close. ◦ No selection.

* For Long press, you can configure it as follows:

◦ RobotiqGripInit: Initialize the gripper. ◦ No selection. After configuration, click Save, and you can control the gripper with the robot end shortcuts.

### 3.3 Programming command

After installing the RobotiqGrip plugin, the relevant commands will appear in the graphical programming and script programming interface.

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0vNqIy7zM6AtCKaXFfPM%2Frobotiq-2f-p008-img01.png?alt=media)

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAcm2JVPffNARVwROQzEL%2Frobotiq-2f-p008-img02.png?alt=media)

#### 3.3.1 Graphical programming

Description: Initialize the gripper. Parameter: Device ID of the gripper. If the configuration of the gripper has not been modified, keep the default value 9. Description: Control the gripper to move. Parameter: 1) Target width ratio of the gripper. Range: \[0, 100]. 2) Target force value ratio of the gripper. When the gripper detects the force value, it will be judged that the target object has been grasped and the fingertip movement will be stopped. Range: \[20, 100]. 3) Movement speed ratio of gripper fingertip opening and closing. Range: \[1, 100]. 4) Device ID of the gripper, the same as the device ID at initialization. 5) When “Synchronization” is true, the robot will wait until the gripper movement is completed (the target width or force value is reached) before continuing to execute the later commands; When “Synchronization” is false, the robot will continue to execute the later commands after delivering commands to the gripper. Description: Get the gripping status of the gripper. Parameter: Device ID of the gripper, the same as the device ID at initialization. Return: The gripping status value of the gripper, with the following meanings.

* 0: Moving, no object is detected.
* 1: Reached the specified position, no object is detected.
* 2: Objects are detected during opening.
* 3: Objects are detected during closing.
* -1: Command execution error.

Description: Get the current width ratio of the gripper. Parameter: Device ID of the gripper, the same as the device ID at initialization. Return: The current width ratio of the gripper, range: \[0, 100].

Description: Get the gripper initialization status. Parameter: Device ID of the gripper, the same as the device ID at initialization. Return: The initialization status value of the gripper, with the following meanings.

* 0: Initialization is not completed.
* 1: Initialization is completed.
* 2: Initializing.
* -1: Command execution error.

Description: Get the gripper error code. Parameter: Device ID of the gripper, the same as the device ID at initialization. Return: The error code of the gripper. Refer to the operation guide of corresponding gripper provided by Robotiq for details or consult Robotiq technical support.

#### 3.3.2 Script programming

Command: RobotiqGripInit({id = 9}) Description: Initialize the gripper. Optional parameter: id: Device ID of the gripper. If the configuration of the gripper has not been modified, keep the default value 9. Example: RobotiqGripInit({id = 9}) Command: RobotiqGripControl(width, force, speed, {id = 9, isBlock = true}) Description: Control the gripper to move. Required parameter:

* width: Target width ratio of the gripper. Range: \[0, 100].
* force: Target force value ratio of the gripper. When the gripper detects the force value, it will be judged that the target object has been grasped and the fingertip movement will be stopped. Range: \[20, 100].
* speed: Movement speed ratio of gripper fingertip opening and closing. Range: \[1,

100].

* Optional parameter:
* id: Device ID of the gripper, the same as the device ID at initialization. “9” by default.
* isBlock: When it is true, the robot will wait until the gripper movement is completed

(the target width or force value is reached) before continuing to execute the later commands. When it is false, the robot will continue to execute the later commands after delivering commands to the gripper. “true” by default. Example: RobotiqGripControl(20, 50, 50, {id = 9, isBlock = true})

Command: RobotiqGripWidthGet({id = 9}) Description: Get the current width ratio of the gripper. Optional parameter: id: Device ID of the gripper, the same as the device ID at initialization. Return: The current width ratio of the gripper, range: \[0, 100]. Example: RobotiqGripWidthGet({id = 9}) Command: RobotiqGripMoveStatus ({id = 9}) Description: Get the gripping status of the gripper. Optional parameter: id: Device ID of the gripper, the same as the device ID at initialization. Return: The gripping status value of the gripper, with the following meanings.

* 0: Moving, no object is detected.
* 1: Reached the specified position, no object is detected.
* 2: Objects are detected during opening.
* 3: Objects are detected during closing.
* -1: Command execution error.

Example: RobotiqGripMoveStatus({id = 9}) Command: RobotiqGripInitStatus({id = 9}) Description: Get the gripper initialization status. Optional parameter: id: Device ID of the gripper, the same as the device ID at initialization. Return: The initialization status value of the gripper, with the following meanings.

* 0: Initialization is not completed.
* 1: Initialization is completed.
* 2: Initializing.
* -1: Command execution error.

Example: RobotiqGripInitStatus({id = 9}) Command: RobotiqGripErrStatus({id = 9}) Description: Get the gripper error code. Optional parameter: id: Device ID of the gripper, the same as the device ID at initialization. Return: The error code of the gripper. Refer to the operation guide of corresponding gripper provided by Robotiq for details or consult Robotiq technical support. Example: RobotiqGripErrStatus({id = 9})
