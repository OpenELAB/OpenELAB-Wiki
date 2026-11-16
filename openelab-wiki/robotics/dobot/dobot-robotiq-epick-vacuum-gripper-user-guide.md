---
description: >-
  User guide for the Robotiq EPick vacuum gripper used with DOBOT six-axis
  robots, covering hardware installation, plugin operation, shortcut settings,
  Blockly programming, and script commands.
---

# DOBOT Robotiq EPick Vacuum Gripper User Guide

## DOBOT ROBOTIQ EPick Vacuum Gripper and Expansion Kits

{% embed url="https://openelab.io/products/dobot-epick-2-epick-4-expansion-kits" %}

## Contents

* Preface
* 1\. Overview
* 2\. Hardware Installation
* 3\. Software Operation
* 3.1 Plugin description
* 3.2 End shortcut settings
* 3.3 Programming commands
* 3.3.1 Blockly programming
* 3.3.2 Script programming

## Preface

Purpose This document introduces the installation and use of Robotiq EPick vacuum gripper applied to the end of Dobot six-axis robots, which is convenient for users to fully understand and use Robotiq EPick vacuum gripper. Intended audience This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Revision history Date Version Revised content 2024/07/09 V1.0 The first release Symbol conventions The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could result

**DANGER**

in death or serious injury. Indicates a hazard with a medium level or low level of risk which, if not

**WARNING**

avoided, could result in minor or moderate injury, robot arm damage. Indicates a potentially hazardous situation which, if not avoided, could result

**NOTICE**

in robot arm damage, data loss, or unanticipated result. Provides additional information to emphasize or supplement important points

**NOTE**

in the main text.

## 1. Overview

The EPick vacuum gripper generates vacuum with an electric vacuum pump. It is equipped with one or multiple suction cups. Each suction cup can be adapted to your application and gripping needs.

![Official manual figure, page 5](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLn9DLlnCvrlaTILcugvI%2Frobotiq-epick-p005-img01.jpg?alt=media)

## 2. Hardware Installation

The diagram for installing the EPick gripper onto the robot arm is as follows.

1. Install the suction cup onto the vacuum generator and tighten by hand.
2. Use M6 hex screws and washers to install the gripper coupling onto the robot arm

according to the position of the dowel pins.

3. Use M5 hex screws and washers to secure the vacuum generator to the gripper coupling.
4. Plug the coupling cable into the I/O interface at the end of the robot arm and tighten it.

If you need to use multiple suction cups, please use the suction cup bracket to connect the suction cups and vacuum generator. The suction cup bracket and the vacuum generator are connected with four M5 hex screws and tooth lock washers, as shown in the figure below.

![Official manual figure, page 6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVykmUDipdZ0vR4Y63QMv%2Frobotiq-epick-p006-img01.jpg?alt=media)

![Official manual figure, page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjFaJc4uLJM81IqyC7xPR%2Frobotiq-epick-p007-img01.png?alt=media)

## 3. Software Operation

### 3.1 Plugin

1. Open DobotStudio Pro and enter the Dobot+ page, import and install the RobotiqEPick

plugin.

2. When connecting for the first time, it will show as Unconnected. Confirm the ID and

baud rate (if the gripper configuration has not been modified, keep the default values: ID = 9, baud rate = 115200), and click Initialize.

**NOTE**

Make sure that the working mode of the end of the robot arm is RS485 before connecting to the gripper, which can be checked and modified in the Monitor > Tool I/O page.

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxnpEjVvO3b6wru4Im3sL%2Frobotiq-epick-p008-img01.jpg?alt=media)

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fg1LGCNTLhXhFay43bDCS%2Frobotiq-epick-p008-img02.png?alt=media)

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSMLF7SaxrvAP49XXXMgn%2Frobotiq-epick-p008-img04.jpg?alt=media)

3. Once initialization is successful, the status will change to Connected, and the plugin can

be used to control the gripper. Current vacuum degree displays the real-time vacuum level feedback from the gripper. The plugin supports two modes for controlling the gripper.

* Automatic mode

Click Grip to grip the object, click Release to release it.

* Advanced mode

In Advanced mode, users can manually set the vacuum level and timeout. Maximum level: The maximum vacuum degree during gripping. Unit: %, Range: \[20, 100]. Minimum level: The minimum vacuum degree during gripping. Unit: %, Range: \[10, 100]. Timeout: The gripping timeout. Unit: %, Range: \[0, 25500]. If the last two digits of the timeout are not zero, the system will round up automatically, e.g., 1 will be treated as 100, 3550 will be treated as 3600. ◦ When the Maximum level is not 0, the gripper starts working automatically, maintaining the vacuum degree between the Maximum level and Minimum level

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiF0SNBx7xvQXQY03QF5p%2Frobotiq-epick-p009-img01.jpg?alt=media)

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGWAfVqvKu84PIf9aiqGM%2Frobotiq-epick-p009-img02.jpg?alt=media)

through intermittent suction. ◦ When the Maximum level is 0, the gripper stops suction for releasing the object. ◦ When the Timeout is not 0 and the Current vacuum degree is continuously below the Minimum level, the gripper stops working after the timeout. ◦ Timeout of 0 means the gripper will not timeout and will keep trying to grip. ◦ Setting the Maximum level to 100 will automatically enable Continuous grip (it can also be manually enabled via the switch (ON/OFF) on the right of Continuous grip; when enabled, the plugin sets the Maximum level to 100). This is typically used to prevent the object from falling due to inertia while handling.

**NOTE**

Even with Continuous grip enabled, a timeout may still occur if the actual vacuum degree remains below the minimum level, causing the object to fall. To avoid this, set the Minimum level to a lower value or the Timeout to 0. ◦ Setting the Maximum level to any value other than 100 will automatically disable Continuous grip (it can also be manually disabled via the switch (ON/OFF) on the right of Continuous grip; when disabled, the plugin sets the Maximum level to 80).

### 3.2 End shortcut settings

After installing the RobotiqEPick plugin, you can set the functions for the robot’s end shortcut keys. Click End shortcut key on the upper right corner of the Dobot+ homepage to enter the configuration page. The left side of the configuration page shows the position of the end button and the definition of Shortcut key 1 and Shortcut key 2, while the right side for configuring the button functions.

* For Plugin list, select RobotiqEPick plugin.
* For Shortcut key 1/2, you can configure it as follows:

◦ RobotiqEPick\_Grip: Control the gripper to grip (maximum vacuum level 100%). ◦ RobotiqEPick\_Release: Control the gripper to release (maximum vacuum level 0%).

* For Long press, you can configure it as follows:

◦ RobotiqEPick\_Init: Initialize the gripper. After configuration, click Save, and you can control the gripper with the robot’s end shortcut keys.

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHHycZQZqvFvp3LJcu1qA%2Frobotiq-epick-p010-img01.jpg?alt=media)

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6hbztnegYqWgsTnujzIY%2Frobotiq-epick-p010-img02.png?alt=media)

### 3.3 Programming commands

After installing the RobotiqEPick plugin, the relevant commands will appear in the Blockly programming and Script programming interfaces.

#### 3.3.1 Blockly programming

Description: Initialize the gripper. Parameter: 1) Gripper mode, supports Automatic mode and Advanced mode. 2) Device ID of the gripper. If the configuration of the gripper has not been modified, keep the default value of 9. Description: Control the gripper to grip the object. Parameter: 1) Device ID of the gripper, the same as the device ID at initialization. 2) Synchronization: ◦ True: The robot will wait until the gripper feedbacks successful gripping or timeout before executing subsequent commands. ◦ False: The robot will continue to execute subsequent commands after issuing the command to the gripper. Description: Control the gripper to release the object. Parameter: 1) Device ID of the gripper, the same as the device ID at initialization. 2) Synchronization: ◦ True: The robot will wait until the gripper feedbacks the operation is completed before executing subsequent commands. ◦ False: The robot will continue to execute subsequent commands after issuing the command to the gripper. Description: Set gripper parameters in advanced mode, and the gripper starts working immediately according to the parameters. Parameter: 1) Maximum vacuum level. Unit: %, Range: \[20, 100]. ◦ Setting to 0 stops suction, used for releasing objects. ◦ Setting to 100 enables continuous vacuum suction, similar to enabling

Continuous grip in the plugin. ◦ Setting between 0 and 100 maintains vacuum degree between maximum and minimum levels through intermittent suction. 2) Minimum vacuum level. Unit: %, Range: \[10, 100]. 3) Timeout. Unit: %, Range: \[0, 25500]. If the last two digits of the timeout are not zero, the system will round up automatically, e.g., 1 will be treated as 100, 3550 will be treated as 3600. ◦ Setting to 0 means no timeout, the gripper will keep trying to grip. ◦ Setting to a positive integer stops the gripper after the timeout if the actual vacuum degree remains below the minimum level. 4) Device ID of the gripper. If the configuration of the gripper has not been modified, keep the default value of 9.

**NOTE**

Even with Continuous grip enabled, a timeout may still occur if the actual vacuum degree does not reach the minimum level, causing the object to fall. To avoid this, set the Minimum level to a lower value or the Timeout to 0. Description: Get the gripper’s initialization status. Parameter: Device ID of the gripper, the same as the device ID at initialization. Return: The initialization status of the gripper, with the following meanings.

* -1: Initialization not completed.
* 1: Initialization completed.
* 2: Initializing.

Description: Get the gripper’s gripping status. Parameter: Device ID of the gripper, the same as the device ID at initialization. Return: The gripping status of the gripper, with the following meanings.

* 0: Gripping.
* 1: Object detected and minimum vacuum level reached.
* 2: Object detected and maximum vacuum level reached.
* 3: No object detected.

Description: Get the gripper’s error code. Parameter: Device ID of the gripper, the same as the device ID at initialization. Return: The error code of the gripper. Refer to the Robotiq gripper user manual or contact Robotiq technical support for details.

#### 3.3.2 Script programming

Command: RobotiqEPickInit(mode,{id=9}) Description: Initialize the gripper. Required parameter: mode: Gripper mode, 0 for Automatic mode, 1 for Advanced mode. Optional parameter: id: Device ID of the gripper. If the configuration of the gripper has not been modified, keep the default value of 9. Example: RobotiqEPickInit(0,{id=9}) Command: RobotiqEPickGrip({id=9,isBlock=true}) Description: Control the gripper to grip the object. Optional parameter:

* id: Device ID of the gripper, the same as the device ID at initialization. “9” by default.
* isBlock: True: The robot will wait until the gripper feedbacks successful gripping or timeout before executing subsequent commands. False: The robot will continue to execute subsequent commands after issuing the command to the gripper. “true” by default. Example: RobotiqEPickGrip({id=9,isBlock=true}) Command: RobotiqEPickRelease({id=9,isBlock=true}) Description: Control the gripper to release the object. Optional parameter:
* id: Device ID of the gripper, the same as the device ID at initialization. “9” by default.
* isBlock: True: The robot will wait until the gripper feedbacks the operation is completed before executing subsequent commands. False: The robot will continue to execute subsequent commands after issuing the command to the gripper. “true” by default. Example: RobotiqEPickRelease({id=9,isBlock=true}) Command: RobotiqEPickSet(maxVacuum,minVacuum,timeout,{id=9}) Description: Set gripper parameters in advanced mode, and the gripper starts working immediately according to the parameters. Required parameter:
* maxVacuum: Maximum vacuum level. Unit: %, Range: \[20, 100].

◦ Setting to 0 stops suction, used for releasing objects. ◦ Setting to 100 enables continuous vacuum suction, similar to enabling Continuous grip in the plugin. ◦ Setting between 0 and 100 maintains vacuum degree between maximum and minimum levels through intermittent suction.

* minVacuum: Minimum vacuum level. Unit: %, Range: \[10, 100].
* timeout: Timeout. Unit: %, Range: \[0, 25500]. If the last two digits of the timeout are not zero, the system will round up automatically, e.g., 1 will be treated as 100, 3550 will be treated as 3600. ◦ Timeout of 0 means the gripper will not timeout and will keep trying to grip. ◦ Setting to a positive integer stops the gripper after the timeout if the actual vacuum degree remains below the minimum level.

**NOTE**

Even with Continuous grip enabled, a timeout may still occur if the actual vacuum degree does not reach the minimum level, causing the object to fall. To avoid this, set the Minimum level to a lower value or the Timeout to 0. Optional parameter: id: Device ID of the gripper. If the configuration of the gripper has not been modified, keep the default value of 9. Example: RobotiqEPickSet(80,50,3000,{id=9}) Command: RobotiqInitStatus({id = 9}) Description: Get the gripper’s initialization status. Optional parameter: id: Device ID of the gripper, the same as the device ID at initialization. Return: The initialization status of the gripper, with the following meanings.

* -1: Initialization not completed.
* 1: Initialization completed.
* 2: Initializing.

Example: RobotiqInitStatus({id = 9}) Command: RobotiqEPickDetected({id = 9}) Description: Get the gripper’s gripping status. Optional parameter: id: Device ID of the gripper, the same as the device ID at initialization. Return: The gripping status of the gripper, with the following meanings.

* 0: Gripping.
* 1: Object detected and minimum vacuum level reached.
* 2: Object detected and maximum vacuum level reached.
* 3: No object detected.

Example: RobotiqEPickDetected({id = 9})

Command: RobotiqEPickErrStatus({id = 9}) Description: Get the gripper’s error code. Optional parameter: id: Device ID of the gripper, the same as the device ID at initialization. Return: The error code of the gripper. Refer to the Robotiq gripper user manual or contact Robotiq technical support for details. Example: RobotiqEPickErrStatus({id = 9})
