# DOBOT Magician E6 Universal Training Platform Operation Instruction - With PLC

## DOBOT Collaborative Robot Universal Training Platform - With PLC System Module

{% embed url="https://openelab.io/products/dobot-cobot-universal-training-platform?variant=46636171428038" %}

**Applies to:** Magician E6 training system with the PLC system module. Official source issue V1.2 (2026-02-11). The robot is purchased separately. Confirm the actual robot and PLC configuration before following wiring or software steps.

**Copyright © Shenzhen Yuejiang Technology Co., Ltd. 2023-2026. All rights reserved.** No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of Yuejiang Technology Co., Ltd.

**Disclaimer** To the maximum extent permitted by applicable law, the products described (including its hardware, software, and firmware, etc.) in this document are provided **AS IS** , which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and noninfringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents.

Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses will be happening in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document.

The user has the responsibility to make sure of following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot.

## Shenzhen Yuejiang Technology Co., Ltd.

Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China

Website: www.dobot.cc

#### Preface

### Purpose

This document introduces the installation procedure and some operation demos (including trajectory simulation, static palletizing, robot handling, visual sorting, visual positioning guided assembly) of the Magician E6 training system, which is convenient for users to understand and use the Magician E6 training system.

### Note

In this document, DobotStudio Pro 4.4 is used for robot control software and DobotVisionStudio 4.1.2 is used for vision software. The PLC software version is TIA Portal V15.1. TIA Portal software must be purchased separately by the customer. The PLC program is pre-loaded within the system. If PLC programming is not required, TIA Portal software is unnecessary.

### Symbol Conventions

The symbols that may be found in this document are defined as follows.

| Symbol  | Description                                                                                                                                                                    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DANGER  | <p>Indicates a hazard with a high level of risk which, if not avoided, could<br>result in death or serious injury.</p>                                                         |
| WARNING | <p>Indicates a hazard with a medium level or low level of risk which, if not<br>avoided, could result in minor or moderate personal injury and damage to<br>the equipment.</p> |
| NOTICE  | <p>Indicates a potentially hazardous situation which, if not avoided, can result<br>in damage to the equipment, data loss, or unanticipated result.</p>                        |
| NOTE   | <p>Provides additional information to emphasize or supplement important<br>points in the main text.</p>                                                                        |

**Contents** Appendix 1:Installation of Robot Software .............................. 192 Appendix 2:Installation of Vision Related Software ..................... 196 Appendix 3:IO Testing Method for E6 General Training Platform (PLC Version) ....................................................................... 206

## Chapter 1 Magician E6 Training System Overview

### 1. Safety Precautions

This section describes the safety precautions that should be noticed when you use this product. Please read this section carefully before using the training system for the first time. This product needs to be used in an environment meeting the design specifications. You cannot remold the product without authorization, otherwise, it may lead to product failure, and even personal injury, electric shock, fire, etc. People who use this product for system design and manufacture must be trained by Dobot or relevant institutions, or must have the same professional skills, and use the training system strictly following the regulations of this document.

#### 1.1 Safety warning signs

The following safety warning signs may appear in this document, and their meanings are described as follows , as shown in Table 1-1.

**Table 1-1 Safety warning signs**

| **Sign**    | **Description**                                                                                                                                                                                                                              |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER      | <p>Indicates a high potential danger, which, if not avoided, will result in<br>death or serious injury.</p>                                                                                                                                  |
| ELECTRICITY | <p>May cause dangerous electricity usage situation soon, which, if not<br>avoided, will cause personal injury or serious damage to the<br>equipment.</p>                                                                                     |
| HOT         |                                                                                                                                                                                                                                              |
|             | <p>May cause dangerous hot surfaces, which, if touched, may cause<br>personal injury.</p>                                                                                                                                                    |
| WARNING     | <p>Indicates a moderate or low potential hazard, which, if not avoided,<br>may cause minor personal injury and damage to the equipment.</p>                                                                                                  |
| NOTICE      | <p>Indicates a potential risk, which, if ignored, may result in damage to<br>the equipment, loss of data or unpredictable results.</p>                                                                                                       |
| ATTENTION   | <p>A situation that, if not avoided, can cause personal injury or damage to<br>the equipment.<br>For items marked with such signs, depending on the specific situation,<br>there is sometimes a possibility of significant consequences.</p> |

#### 1.2 General safety

Follow the safety instructions below when starting and using the training system for the first time.

**DANGER**

* The Robot control system is electrical equipment. Non-professional technicians should not modify the circuit, otherwise, it may cause damage to devices or personal injury.
* Comply with the local laws and regulations when operating the equipment. The safety precautions in this document are only supplemental to the local safety regulations.
* Use the equipment in the specified environment scope. Exceeding the specifications or load conditions will shorten the service life of the product, even damage it.
* Ensure that the equipment is operated under the security conditions and there is no harmful object around the robot.
* Turning on or off the power of the robot continually may result in degraded performance of the main circuit components inside the controller. If turning on or off the power continually is required, please keep the frequency less than once per minute.

(2) HOT

* The robot and the controller will generate heat during operation. Please do not operate or touch the robot when the robot is working or has just stopped working.
* Turn off the power and wait an hour for the robot to cool down.
* Do not put your fingers to where the control cabinet gets hot.
* (3) NOTICE
* The personnel responsible for installation, operation and maintenance of equipment must first receive strict training, understand various safety precautions, and master correct operation and maintenance methods before they can operate and maintain the equipment.
* Personnel without professional training shall not disassemble and repair the equipment without authorization. If the equipment fails, please contact Dobot technical support engineer in time.
* Be sure to carry out daily inspections and regular maintenance, and replace faulty components in time to ensure the safe operation of the equipment.
* If the equipment is scrapped, please comply with relevant laws to properly handle industrial waste and protect the environment.
* Please establish safety measures (such as guardrails, ropes or warning lines) near the operating area of the robot to ensure that personnel remain out of reach of the robot being operated or the robot about to start operation.
* Do not enter the safety range of the robot as determined by the risk assessment or touch the robot while the system is in operation.
* Do not expose the robot to permanent magnetic fields all the time. Strong magnetic fields can cause damage to the robot.
* Dobot assumes no responsibility for equipment damage or personal injury caused by failure to follow product instructions or other improper operations.
* Dobot is not responsible for any damage caused during the transportation and handling of equipment.
* After removing the outer packaging, make sure that the robot maintains the original packing posture and the brakes of all axes are normal.
* (4) WARNING
* Before the operation, please wear antistatic uniform and protective gloves.
* It is prohibited to modify or remove the nameplates, instructions, icons and marks on the equipment.
* Before operating the equipment, please find and be familiar with the operation method of the emergency stop function to ensure that the robot arm can be stopped urgently in the case of sudden stress. The emergency stop function is Stop Category 1.
* Be careful when carrying or installing the equipment. Please follow the instructions on the packing box to put down the robot gently and place it correctly in

the direction of the arrow.

* Please use the matched cables for personal security and equipment protection.
* Please ensure that the robot and tools are installed correctly.
* Please ensure that the robot has enough space to move freely.
* Any impact will release a lot of kinetic energy, which is much higher than that
* under high speed and high load.

#### 1.3 Personal safety

When operating the robot system, please strictly follow the general precautions listed below to ensure the personal safety of the operator.

WARNING

* Please comply with local laws or regulations with regard to the maximum weight one person is permitted to carry.
* Do not touch the terminal workpieces or disassemble the equipment with the power ON. Otherwise, it may result in an electric shock.
* Please confirm that the equipment is well grounded, otherwise it will endanger personal safety.
* Do not touch the terminal workpieces or remove the interval circuit components within 10 minutes after the power is shut off, so as to avoid an electric shock since there is residual capacitance inside the equipment.
* Even if the power switch of the equipment is already in the OFF status, touching the terminal workpieces or removing the interval circuit components is not allowed, so as to avoid an electric shock since there is residual capacitance inside the equipment.
* When working with robots, do not wear loose clothing or jewelry. When operating the robot, make sure that you have bundle your hair behind your head.
* If the robot appears to have stopped during the operation of the equipment, it may be because the robot is waiting for the start signal and is in the state of being about

to move. In this case, the robot should also be considered to be in motion. Do not approach the robot.

#### 1.4 Emergency

#### 1.4.1 Emergency stop switch

After you press the emergency stop switch in emergencies, the robot will immediately stop all motions and be locked. According to IEC 60204-1 and ISO 13850, the emergency stop switch is not a safeguard. It is a complimentary protective measure and not intended to prevent injury.

#### 1.4.2 Emergency recovery

The emergency stop switch will be locked after you press it. To unlock the switch, you need to rotate the switch according to the mark on the switch. The alarm can be cleared through the software only after the emergency stop switch is unlocked. Then the robot arm can be enabled and resumed from the emergency status.

**WARNING**

Please operate the robot to recover from the emergency only after the danger of the robot system is completely removed.

### 2. Product Introduction

Dobot Magician E6 （Abbreviation E6）training system is an educational solution designed for vocational and higher education to help students understand the functions of standard automation systems and improve the effectiveness of training. A standard E6 training system is shown in Figure1-1.

The E6 training system can realize the following functions:

* Robot programming and debugging
* User/Tool coordinate system settings
* Robot trajectory programming
* Robot handling and palletizing
* Machine vision colored object recognition
* Machine vision positioning guided assembly

Figure1-1 E6 training system

### 3. Layout Introduction

#### 3.1 Structural layout

The E6 general training platform is composed of E6 industrial six axis robot unit, visual unit, feeding and transmission unit, mini air pump box, quick change board unit, tool box unit, etc , as shown in Figure1-2.

![Official Magician E6 training-system figure, source page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fhu018mgSzxUcXkjZzyHm%2Futp-3e96273985f3ac5ae0fa.jpg?alt=media)

Figure1-2 Structural layout

#### 3.2 E6 training platform core unit

#### 3.2.1 Robot Unit

The E6 robot is a six axis collaborative robot for teaching and research, which adopts an integrated design and the controller is placed in the base. It can be paired with a training platform for robot practical teaching.

Equipped with special security mechanisms including collision detection. It is flexible and easy to deploy, easy to use, and secure collaboration. E6 can receive signals from visual units, execute corresponding robot commands, and complete corresponding actions.

* (1) Robot composition

E6 robot, as shown in Figure1-3, includes a base, 6 rotating motion joints, and two connecting rods (upper arm and forearm), with an aviation socket on the side of its end flange.

![Official Magician E6 training-system figure, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F105sDLmE9HljnnyOPObZ%2Futp-5b810fa8fc6bde232b7e.jpg?alt=media)

Figure1-3 E6 composition

**(2) Indicator light**

The E6 robot is equipped with a circle of status indicators near the J1 and J6 joints,

with the meanings described below, as shown in Table1-2.

**Table1-2 Indicator lights**

| **Color**    | **Status**  | **Definition**                                                                                                               |
| ------------ | ----------- | ---------------------------------------------------------------------------------------------------------------------------- |
| Ble liht     | Steady on   | The robot arm has been started but not enabled.                                                                              |
| u g          | Quick flash | The robot arm is starting.                                                                                                   |
|              | Steady on   | The robot arm is enabled (not running).                                                                                      |
| Green light  | Slow flash  | <p>Automatic running status (project debugging /running /pause,<br>TCP motion commands except jog, trajectory playback).</p> |
|              | Quick flash | <p>Single running status (jog /run to in software) /drag mode<br>/trajectory recording status.</p>                           |
| Rd liht      | Slow flash  | Joint brake switched on in disable status.                                                                                   |
| e g          | Steady on   | Alarm status                                                                                                                 |
| Yellow light | Steady on   | Collision detected                                                                                                           |

* (3) Buttons

There are multiple buttons at the end and base, as shown in Figure1-4.

![Official Magician E6 training-system figure, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtyNmXh7gG6yXXrBhvdC0%2Futp-fb11bb902800713b6579.jpg?alt=media)

Figure1-4 Button position

: **Power switch** . Short-press (in 0.5s) to switch on. Long press for 1.5s in power-on state, the indicator light will flash red fast, and then release the button to turn off the power.

: **Run/stop button** . When the robot is enabled and idle, long press to start running; when the robot is running, short-press to stop running. You can configure the functions (trajectory playback by default) of the button in DobotStudio Pro.

* **Trajectory playback** : Play back the last trajectory recorded by at the original speed.
* **Run projec** t: Configure the project to be run via DobotStudio Pro. After the configuration is completed, you can run the project directly via this button, with no need to connect to the operating terminal. Powering off the robot will not clear the configuration.

: **Enabling button** . When the robot arm is not enabled, long-press the button to enable the robot. When the robot arm is enabled and idle, short-press the button to disable the robot.

: **Hand-guiding button** . When the robot arm is enabled and idle, long-press the button and the robot arm will enter the drag mode. Long-press the button again in

![Official Magician E6 training-system figure, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Furgddn05VPtj7kkquNw4%2Futp-268f456ad4e2f384ea5b.jpg?alt=media)

the drag mode, and the robot arm will enter the trajectory recording mode. Short-press the button, and the robot arm will exit the drag mode and stop trajectory recording.

: **Tool control button** . When the robot is disabled, enabled and idle or in the drag mode, short-pressing the button can switch the status of the specified tool DO for controlling the end tool. You can configure the tool DO via the tool IO plug-in in DobotStudio Pro.

Note:

* Except for the power switch, short pressing is to release within 0.5s after pressing. Long
* pressing is to release within 0.5s\~5s after pressing. Pressing for more than 5s and then releasing is an invalid operation.

 Some of the button functions are affected by the manual/automatic mode of the controller. See the instructions on mode switch in the DobotStudio Pro user guide for details.

#### 3.2.2 Visual Unit

The visual unit has the advantages of rich function, stable performance and easy operation. It can meet the rich visual application needs of visual positioning, measurement, detection and recognition , as shown in Figure1-5. The supporting visual software comes with more than 100 kinds of image processing operators and a powerful visual analysis tool library. It can quickly build machine vision application system to meet different application needs.

Figure1-5 Visual Unit

![Official Magician E6 training-system figure, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fhk7n3rY7DA05jvlgBvaF%2Futp-c355238820f9b8e7dc8e.jpg?alt=media)

#### 3.2.3 Feeding and Conveying Unit

The feeding and conveying unit is mainly used to push materials from the silo to the conveyor belt , in order to achieve the transportation of materials between different positions. The conveyor belt adopts a built-in stepper motor, which can accurately control the pushing distance of the material . Driven by a DC deceleration motor, the movement of the convery belt can be controlled to meet the transportation needs of different materials. In addition, the conveyor belt is also equipped with an alignment sensor and encoder, which can accurately detect the position of materials on the convery belt. It can achieve dynamic tracking and grasping of materials by robots in space, improving the transportation efficiency and accuracy of materials, as shown in Figure16.

Figure1-6 Feeding and Conveying Unit

#### 3.2.4 Mini Air Pump Box

The mini air pump box is a practical accessory independently designed and developed by DOBOT . It is used in conjunction with the Yue Jiang robot , as shown in Figure1-7. The air pump box can provide a pressure range of -70\~110kPa. Its appearance design is exquisite. It can be directly adapted to DOBOT robots through I/O control interfaces, plug and play, and can be suitable for most daily suction cups and flexible gripper application scenarios.

![Official Magician E6 training-system figure, source page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFCGRvy9OHpul2Pb7e6PB%2Futp-747a4b8fd1f436a14a22.jpg?alt=media)

Figure1-7 Mini air pump box

#### 3.2.5 Quick Change Board Unit

The training platform is equipped with 4 quick change board modules as standard, including: trajectory board, standard visual loading board, mobile phone model workpiece loading board, circular/rectangular workpiece loading board, as shown in Figure1-8. The quick change board unit, in conjunction with the robot execution unit and visual unit, completes visual recognition, detection, and positioning of the experimental object, and completes process applications such as item tracking, positioning and grasping, stacking, and assembly.

Figure1-8 Quick Change Board Unit

#### 3.2.6 Control Button Box

The Control Button Box is mainly composed of four buttons, namely “START”, “STOP”, “RESET” and “EMERGENCY STOP”, as shown in Figure1-9. The

![Official Magician E6 training-system figure, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fo149alWPA3w3Vfrsdkvj%2Futp-ca8256082d3eba21288b.jpg?alt=media)

![Official Magician E6 training-system figure, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAngqpSeiAHm2Q9MUbwxA%2Futp-77c1fe980a5d3ad00a26.jpg?alt=media)

“EMERGENCY STOP” button is not affected by other control devices. When the emergency stop button is pressed, it will immediately stop the operation of the robot. The other three buttons are used to start, stop and reset the system by pressing the corresponding buttons on the touch screen automatic control interface.

Figure1-9 Control Button Box

Note：Only in the automatic control interface of the touch screen, the “Start”, “Stop”, and “Reset” buttons of the control button box can control the device. In other interfaces, the “Start”, “Stop”, and “Reset” buttons of the control button box cannot control the device.

#### 3.2.7 Main Control Unit

The Main Control Unit includes a PLC module and a touch screen module , as shown in Figure1-10. The PLC uses Siemens S7-1200, and the touch screen uses Siemens KTP700. Together with the touch screen, PLC can control the discharge of the cylindrical silo, the operation of the conveyor belt, and the detection of the workpiece in place. It also can perform human-machine interaction, monitor equipment operation

status, display the status of each IP port, and control system processes.

Figure1-10 Main Control Unit

![Official Magician E6 training-system figure, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh0jAbchZckMKRDeKfgYJ%2Futp-9bcf4ee3ca6e5642470b.jpg?alt=media)

![Official Magician E6 training-system figure, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0CmYxEcumtUwkX4yz6T6%2Futp-c3c7cc9eae41391fc090.jpg?alt=media)

## Chapter 2 Application of Trajectory Simulation

### 1. Introduction

In the trajectory simulation demo, the end of the robot can move along the specified trajectory based on the taught points, as shown in Figure2-1 .

Figure2-1 Trajectory simulation

### 2. Program Debugging

#### 2.1 Preparation

#### 2.1.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 2.1.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it on, as shown in Figure2-2.

![Official Magician E6 training-system figure, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FR5LTziI5Ta5fDaVBofz7%2Futp-f4f96033f62baa1a6e5c.jpg?alt=media)

Figure2-2 Turn on the E6 power switch

#### 2.1.3 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the other end to the PC.

* (2) Modify IP of the PC.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure2-3. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

![Official Magician E6 training-system figure, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

Figure2-3 Set IP of the PC

* (3) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro** to open the software. After you enter DobotStudio Pro, the software will automatically search for robots and displays the search result “Magician E6” on the interface. Click **Connect** on the right side of the device to connect it, as shown in Figure2-4.

![Official Magician E6 training-system figure, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfFW8rxCNQcXS2wrdDVKt%2Futp-8ffcc127698c75d5fef2.jpg?alt=media)

Figure2-4 Connect robot

After successful connection, the software interface will refresh and display the

information about the E6 and its 3D model, as shown in Figure2-5.

Figure2-5 Information about the E6

#### 2.1.4 Enable robot

Click on the “Enable” switch of the “Magician E6” interface. Modify

various parameter values according to the actual situation in the “Load enabling settings”

![Official Magician E6 training-system figure, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRujPrpBXi8viLdzRzUD4%2Futp-1436143103c7aa0204d7.png?alt=media)

![Official Magician E6 training-system figure, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

window that pops up. Click **Enable** , as shown in Figure2-6. The Enabling switch

changes to in the E6 interface.

Figure2-6 Set load parameters

#### 2.1.5 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to

set the speed to 15%, as shown in Figure2-7.

Figure2-7 Set Speed

Note: The speed can be set lower during debugging, and after debugging is completed, it can

be adjusted higher according to actual needs.

#### 2.1.6 Installing the calibration needle

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure2-8.

![Official Magician E6 training-system figure, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

Figure2-8 The posture of installing the end tool

Note: It is best to adjust the value of J6 to 0°.

* (2) Install the suction cup onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Figure2-9.

Figure2-9 Install the suction cup on the end of robot

* (4) Remove the suction nozzle from the suction nozzle connecting rod and install

the calibration needle, as shown in Figure2-10.

![Official Magician E6 training-system figure, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8ogIZ2WtTF7v8rFcqY3D%2Futp-2d68c8a8d27ecc7a907d.jpg?alt=media)

![Official Magician E6 training-system figure, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaurAi1A7IEXFaD2zlMhD%2Futp-2df2a85a50f9a9c39daa.jpg?alt=media)

![Official Magician E6 training-system figure, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD5KfFmPpmjn6AdSqe1yW%2Futp-4bef8fec333f7f4052a3.jpg?alt=media)

Figure2-10 Install the calibration needle

#### 2.1.7 Adjust the robot’s posture

Adjust the robot’s posture through the control panel, as shown in Figure2-11, so

that the joint coordinates are {0, 0, -90, 0, 90, 0}.

Figure2-11 Adjust the robot’s posture

#### 2.1.8 Place trajectory board

Place the trajectory board on the storage area, as shown in Figure2-12.

![Official Magician E6 training-system figure, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIvNmBMr2qWdQpJQH2u8x%2Futp-bbfe3f149339ddcd2bcf.jpg?alt=media)

![Official Magician E6 training-system figure, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsQASufzZrqGFmqfhvQ4o%2Futp-02771c88dfe736dbdf5e.jpg?alt=media)

Figure2-12 Place the trajectory board

#### 2.2 Import program

(1) On the Home screen of DobotStudio Pro software, click **Application > Script**

**programming** and enter “Programming” interface, as shown in Figure2-13.

Figure2-13 Enter “Programming” interface

(2) Click to open File menu and select “Import project”, as shown in Figure2-14. Select **Trajectory\_Simulation** folder, and click **Open** . Now the **Trajectory\_Simulation** program has been imported into DobotStudio Pro, as shown in Figure2-15.

![Official Magician E6 training-system figure, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaPfdsHLkEXSnR59mqVr2%2Futp-b16bad06b8e612aa9480.jpg?alt=media)

![Official Magician E6 training-system figure, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqaLYR97NdUnK5i6XNfac%2Futp-0488c5134fc0a3c08469.jpg?alt=media)

Figure2-14 Import project

Figure2-15 Project imported

#### 2.3 Save program

Click and enter a project name in the pop-up dialog box, as shown in Figure2-

16.

![Official Magician E6 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiuDIQcvsMYmHpewAvnzf%2Futp-613e1172fcce5ee05aa5.png?alt=media)

![Official Magician E6 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUgmf9RUYvaz2l0aA3D2J%2Futp-8ffac6bd7cb4e1892c7b.png?alt=media)

Figure2-16 Save program

#### 2.4 Debug points

You need to debug 40 points in this demo. The points on the trajectory board are

shown in Figure2-17.

Figure2-17 Trajectory board points

(1) Jog the robot to move over the trajectory board, as shown in Figure2-18. Click

**Points** to enter the Points interface. Firstly select P1. Then click the tool **Cover** . Finally

click **Cover** in the pop-up tips again to update P1 point, as shown in Figure2-19.

![Official Magician E6 training-system figure, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyPbembbFTrr2DqLJ1ZWM%2Futp-ebb53ff510b3cab6d2bf.png?alt=media)

![Official Magician E6 training-system figure, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuqKv8XL4WkcffBpR5ZHa%2Futp-35a9b81cd9cf59a87922.jpg?alt=media)

Figure2-18 Locate P1

Figure2-19 Update P1

(2) Jog the robot to point gj1 on the trajectory board, as shown in Figure2-20. Firstly select P2. Then click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P2 point, as shown in Figure2-21.

![Official Magician E6 training-system figure, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq8gmOJZA4HDzehKhpUOT%2Futp-c249d80b134d31b7a3c4.jpg?alt=media)

![Official Magician E6 training-system figure, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F29jVrLIncaCTsLRbelhR%2Futp-796ae2e5474481c3c373.jpg?alt=media)

![Official Magician E6 training-system figure, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

Figure2-20 Locate Point gj1

Figure2-21 Update P2(gj1)

(3) Jog the robot to point gj2 on the trajectory board, as shown in Figure2-22. Firstly select P3. Then click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P3 point, as shown in Figure2-23.

![Official Magician E6 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F357BHBjymhmqUrshLQP2%2Futp-a416ee9bddd067235fc3.jpg?alt=media)

![Official Magician E6 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSb9hb8QdOjJXQxaBKchl%2Futp-220869fe9259c7fd779f.jpg?alt=media)

![Official Magician E6 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0L9ZsyJqArN1Xi00Ih3s%2Futp-0665038e20a779251058.jpg?alt=media)

![Official Magician E6 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

Figure2-22 Locate Point gj2

Figure2-23 Update P3(gj2)

(4) Repeat the steps above to update the remaining 38 points. The updated points

are shown in Figure2-24.

![Official Magician E6 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgHlieeAzzfCQRi3jotaN%2Futp-89e37cee50ac1430689f.jpg?alt=media)

![Official Magician E6 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0EnoJtaNnVh8JshFKy5Y%2Futp-1b70e7090f05e5196967.jpg?alt=media)

![Official Magician E6 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuDnLFF3wRMikbsL7lHRh%2Futp-4b51f2720490003799e9.png?alt=media)

![Official Magician E6 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

**Application of Trajectory Simulation**

| (1)P1-P9 |
| -------- |

(2)P10-P18

![Official Magician E6 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5sIgVUYLA18amam4soBb%2Futp-f414076e02026480e98b.png?alt=media)

![Official Magician E6 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU1mKTmAi8QXDoRsYWbC1%2Futp-0262944637ba6c45b0e6.png?alt=media)

Figure2-24 Updated points

#### 2.5 Run program

Click to run the program, and observe whether the robot moves following

![Official Magician E6 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM0qXjoOJb6Nbbkg1vk6c%2Futp-ca969376537bea144367.png?alt=media)

![Official Magician E6 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHaxPP8SvI5CdcWpk2awp%2Futp-aee31e48c9b43ff80253.png?alt=media)

![Official Magician E6 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu32PbZA8UIlxYl8O95zw%2Futp-8e5c54c923ddfabebfcc.png?alt=media)

the trajectory.

Note: During the program operation, if the robot’s point position is found to be incorrect, please directly press the “ ” button to stop the program operation, and then follow the method explained in 2.4 to perform point debugging again.

#### 2.6 Export program

Click to open File menu and select “Export project”. Select the path to save the program. Then enter a project name in the pop-up dialog box.

Note: Exporting a project refers to export the program to local for backup.

### 3. Key Program Description

This section mainly describes the key script. For complete script, see the project in Script page.

The trajectory simulation is mainly about moving between different points, as shown in Figure2-25.

Figure2-25 Trajectory points

As the trajectory consists of shapes with different characteristics, the robot moves

in four modes: **MovJ** for point-to-point motion, **MovL** for linear motion, **Arc** for arc motion, and **Circle** for circular motion.

![Official Magician E6 training-system figure, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTcLkZuTxWBPbc8iaGapr%2Futp-31600926637c51f83328.png?alt=media)

## Chapter 3 Application of Static Palletizing

### 1. Introduction

The specific task of static palletizing is to use the robot to carry six rectangular workpieces placed in a 3×3×1 matrix on the standard vision board to the storage area and code it as 1×3×3 stacks, as shown in Figure3-1 and Figure3-2.

Figure3-1 Palletizing workpieces

Figure3-2 Storage area

### 2. IO Configuration

The IO configuration of static palletizing is shown in Table3-1.

**Table3-1 IO configuration**

| **Output** | **Description** |
| ---------- | --------------- |
| DO09       | Vacuum pumping  |
| DO10       | Vacuum breaking |

![Official Magician E6 training-system figure, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXeKAnBzZruNqHVEdSQTa%2Futp-5e0b2666262b337ba153.jpg?alt=media)

![Official Magician E6 training-system figure, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjskiuldQAh36GfbZeQ6n%2Futp-12cb0fc85b24db8a4a2f.jpg?alt=media)

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 3.1.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it

on, as shown in Figure3-3.

Figure3-3 Turn on the E6 power switch

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to **Auto** , as

shown in Figure3-4.

Figure3-4 Turn on the power switch of the pump box

#### 3.1.4 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the

![Official Magician E6 training-system figure, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

![Official Magician E6 training-system figure, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXNgabrIkDXTUXwasw4VI%2Futp-e2041f0a4aaf8ec24106.jpg?alt=media)

other end to the PC.

* (2) Modify IP of the PC.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure3-5. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

Figure3-5 Set IP of the PC

* (3) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro** to open the software. After you enter DobotStudio

Pro, the software will automatically search for robots and displays the search results "Magician E6" on the interface. Click **Connect** on the right side of the device to connect it, as shown in Figure3-6.

![Official Magician E6 training-system figure, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfFW8rxCNQcXS2wrdDVKt%2Futp-8ffcc127698c75d5fef2.jpg?alt=media)

Figure3-6 Connect robot

After successful connection, the software interface will refresh and display the information about the E6 and its 3D model, as shown in Figure3-7.

Figure3-7 the information about the E6

#### 3.1.5 Enable robot

Click on the “Enable” switch of the “Magician E6” interface. Modify

various parameter values according to the actual situation in the “Load enabling settings”

![Official Magician E6 training-system figure, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRujPrpBXi8viLdzRzUD4%2Futp-1436143103c7aa0204d7.png?alt=media)

![Official Magician E6 training-system figure, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

window that pops up. Click **Enable** , as shown in Figure3-8. The Enabling switch

changes to in the E6 interface.

Figure3-8 Set load parameters

#### 3.1.6 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to

set the speed to 40%, as shown in Figure3-9.

Figure3-9 Set Speed

Note: The speed can be set lower during debugging, and after debugging is completed, it can

be adjusted higher according to actual needs.

#### 3.1.7 Install eccentric tools

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro to enter the “Jog” panel. By

jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure3-10.

![Official Magician E6 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

Figure3-10 The posture of installing the end tool

Note: It is best to adjust the value of J6 to 0°.

* (2) Prepare installation materials.

Prepare the eccentric flange, suction cup, and corresponding installation screws,

as shown in Figure3-11.

Figure3-11 Prepare installation materials

* (3) Install the suction cup onto the eccentric flange plate through four M3\*8 screws

using an allen tool, as shown in Figure3-12.

Figure3-12 Assemble eccentric tools

![Official Magician E6 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8ogIZ2WtTF7v8rFcqY3D%2Futp-2d68c8a8d27ecc7a907d.jpg?alt=media)

![Official Magician E6 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaurAi1A7IEXFaD2zlMhD%2Futp-2df2a85a50f9a9c39daa.jpg?alt=media)

![Official Magician E6 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPvrlM0eHWNAwOwFjITjZ%2Futp-546af7717d65634d97a3.jpg?alt=media)

![Official Magician E6 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw7UkFJDTyecyqzZ5noKE%2Futp-7c8096920a23aa3c9451.jpg?alt=media)

* (4) Install the eccentric tools onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Figure3-13.

Figure3-13 Install eccentric tool on the end of robot

* (5) Connect one end of the air pipe to the “Air” hole in the air pump box, and the

other end to the suction cup. Fix it to the robot with a tie, as shown in Figure3-14.

Figure3-14 Connect the air pipe

#### 3.1.8 Install standard vision board

Install the standard vision board above the conveyor , as shown in Figure3-15.

Figure3-15 Install the standard vision board

![Official Magician E6 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbE7nS1MOK3X0xylsQqSu%2Futp-035e220847427a8432f5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxIvRTpyabMeTw1K4ZyRS%2Futp-2a34d50e82b6568cc1c2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmYwpGLIK0MdWBogc323o%2Futp-b594c3eafe70ae68a5c6.jpg?alt=media)

#### 3.2 Establish tool coordinate system

The tool coordinate system is generated by four point teaching method: after installing the tool at the end of E6, adjust the position and posture of the tool, make TCP (Tool Center Point) align with the same point in space (reference point) in four different attitudes, obtain the position offset of the tool, and generate the tool coordinate system, as shown in Figure3-16.

Figure3-16 Tool coordinate system example

(1) Adjust the robot’s posture through the control panel, as shown in Figure3-17,

so that the joint coordinates are {0, 0, -90, 0, 90, 0}.

Figure3-17 Adjust the robot’s posture

(2) Remove the suction nozzle from the suction nozzle connecting rod. Install the

calibration needle, as shown in Figure3-18.

![Official Magician E6 training-system figure, source page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlB4DXS3YM5CrKOdNgXsM%2Futp-d0c7837fab77a2437642.jpg?alt=media)

Figure3-18 Install the calibration needle

Note: Do not touch the tip of the calibration needle with your hands, be careful not to scratch

it.

* (3) Place a pointed screw on the visual loading board, using the tip of the screw as

a reference point, as shown in Figure3-19.

Figure3-19 Set reference point

(4) Click **Settings** > **Coordinate System** > **Tool coordinate system** on DobotStudio Pro main page. Select Tool coordinate system 1, and click **Modify** to update the coordinate system (if there is only No.0, you can click **Add** to add a coordinate system), as shown in Figure3-20.

![Official Magician E6 training-system figure, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtsN5nQdMIul4EgSVZyjQ%2Futp-ba7c4103e2d63ff8a651.jpg?alt=media)

![Official Magician E6 training-system figure, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fff46RQ4LDhlcU2BwoO56%2Futp-88c72a3ca2a9b24dd7de.jpg?alt=media)

Figure3-20 Select “Tool coordinate system”

(5) Click **Four-point setting** in Modify interface, as shown in Figure3-21.

Figure3-21 Select “Four-point setting”

(6) Jog E6 and align the needle tip of the robot end with the reference point in the first posture, as shown in Figure3-22. Then select P1 and click **Obtain** , as shown in Figure3-23.

Figure3-22 The first attitude alignment reference point

![Official Magician E6 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3k8PVup1s0G5Zc1qBhrp%2Futp-01cb887c56c3fb0c6e92.jpg?alt=media)

![Official Magician E6 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW8FCHyk2j9nk69k0zLYN%2Futp-d10cf2dafb7d67fa58d4.png?alt=media)

![Official Magician E6 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcyiII5fWZydZCREgHzoW%2Futp-d416a6de90e85ba964c5.jpg?alt=media)

Figure3-23 Obtain P1

(7) Jog E6 and align the needle tip of the robot end with the reference point in the second posture, as shown in Figure3-24. Then select P2 and click **Obtain** , as shown in Figure3-25.

Figure3-24 The second attitude alignment reference point

![Official Magician E6 training-system figure, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHcxQMmMKanA8vXAJZe1t%2Futp-f8ebb6f3f19826b0c76c.jpg?alt=media)

![Official Magician E6 training-system figure, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS8lK0tq7WY60zsWgFmSq%2Futp-335930d33d737656dbc1.jpg?alt=media)

Application of Static Palletizing<br>

Figure3-25 Obtain P2

(8) Jog E6 and align the needle tip of the robot end with the reference point in the third posture, as shown in Figure3-26. Then select P3 and click **Obtain** , as shown in Figure3-27.

Figure3-26 The third attitude alignment reference point

![Official Magician E6 training-system figure, source page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fc7g0TX6Vk2esd5gMO1le%2Futp-89e0965c1673ca50b5e3.jpg?alt=media)

![Official Magician E6 training-system figure, source page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC8Z93WfP1f3qJCSKnKZn%2Futp-032eb6d7a4752387d5a6.jpg?alt=media)

Application of Static Palletizing<br>

Figure3-27 Obtain “P3”

(9) Jog E6 and align the needle tip of the robot end with the reference point in the fourth posture, as shown in Figure3-28. Then select P4 and click **Obtain** , as shown in Figure3-29.

Figure3-28 The fourth attitude alignment reference point

![Official Magician E6 training-system figure, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRwzW5THcFKgvhPCGCUeP%2Futp-d776e58edac362c3ff2e.jpg?alt=media)

![Official Magician E6 training-system figure, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJOafgynXX36aSOncyVPE%2Futp-9182d0ed8e2706344a74.jpg?alt=media)

Figure3-29 Obtain “P4”

(10) Click **Confirm** , the system will automatically return to the “Modify” interface,

and then click **Save** , as shown in Figure3-30.

Figure3-30 Save

* (11) Prove if the tool coordinate system has been calibrated successfully.

Set the “Tool coordinate system” to “1” in the “Jog” panel, and then continuously

![Official Magician E6 training-system figure, source page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjqwHdCGHOg62ieNyTR61%2Futp-44794f5aca01800c8bd6.jpg?alt=media)

![Official Magician E6 training-system figure, source page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCMieeOXSSYWXiiO2Yu9P%2Futp-7ce81b169837b5654eab.png?alt=media)

click **RZ–** or **RZ+** to observe whether the calibration needle tip is always aligned with a point, as shown in Figure3-31. If the calibration needle tip is consistently aligned with a point, it indicates that tool coordinate 1 has been calibrated successfully. Otherwise, it is necessary to calibrate the tool coordinate system again.

Figure3-31 Tool coordinate system 1

(12) Remove the calibration needle at the end of the machine and replace the upper suction nozzle.

#### 3.3 Import program

(1) On the Home screen of DobotStudio Pro software, click **Application > Script programming** and enter “Programming ” interface, as shown in Figure3-32.

![Official Magician E6 training-system figure, source page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbtKeHRKnuDDECWTyeOm8%2Futp-d0d9d372bce2188a0f6b.jpg?alt=media)

Figure3-32 Enter “Programming ” interface

(2) Click to open File menu and select “Import project”, as shown in Figure3-33. Select **Static\_Palletizing** folder, and click **Open** . Now the Modify **Static\_Palletizing** program has been imported into DobotStudio Pro, as shown in Figure3-34.

Figure3-33 Import project

![Official Magician E6 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhnYlWhIc8wZYr5o2mm13%2Futp-8c8439046cf117a7e420.jpg?alt=media)

![Official Magician E6 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FF9drowGftJjwbg5rxUzl%2Futp-d2ddbd6c305f430344b9.png?alt=media)

Figure3-34 Project imported

#### 3.4 Save program

Click and enter a project name in the pop-up dialog box, as shown in Figure3-\
35.<br>

Figure3-35 Save program

#### 3.5 Prepare material

Place 9 workpieces in the upper right corner of the standard vision board in 3×3×1

matrix, as shown in Figure3-36.

![Official Magician E6 training-system figure, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtHB9eBa8En4OjpsNoSvT%2Futp-886871c78d1bb2011c93.png?alt=media)

![Official Magician E6 training-system figure, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ffxw3tggSoiWdPit2MXoF%2Futp-1685e8b4f5541db8bef9.png?alt=media)

Figure3-36 Palletizing workpieces

Note: When placing stacked materials, you can choose a cross on the pallet as the reference point for placement.

#### 3.6 Debug points

The robot uses a total of 3 points for static stacking, and the debugging method is as follows:

(1) Adjust the robot’s posture through the control panel, as shown in Figure3-17,

so that the joint coordinates are {0, 0, -90, 0, 90, 0}.

Figure3-37 Adjust the robot’s posture

(2) Update safe point P1.

The tool coordinate system is “1”. Jog the robot to a position between the conveyor and the storage area, as shown in Figure3-38.

![Official Magician E6 training-system figure, source page 53](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXeKAnBzZruNqHVEdSQTa%2Futp-5e0b2666262b337ba153.jpg?alt=media)

![Official Magician E6 training-system figure, source page 53](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhCEFGRkYjNWgicYwn9Ah%2Futp-91b373c7863ab24a045e.jpg?alt=media)

Figure3-38 Locate Point P1

Click **Points** to enter the Points interface. Firstly select P1. Then click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P1 point, as shown in Figure3-39.

Figure3-39 Update P1

* (3) Update picking point P2.

Jog the robot to the picking point of the first workpiece on the standard vision board. The suction cup needs to touch the centre of the first workpiece, as shown in Figure3-40. In the Points interface, firstly select P2, then click the tool Cover, and finally click **Cover** in the pop-up tips again to update P2 point, as shown in Figure3-41.

![Official Magician E6 training-system figure, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVukv3sZL68mqw0iYMsYz%2Futp-22e7626d23e3f3473cb4.jpg?alt=media)

![Official Magician E6 training-system figure, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbdKXvyJiaqM55UoCx3qI%2Futp-6231c04a9afa0589ae51.jpg?alt=media)

![Official Magician E6 training-system figure, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

Figure3-40 Locate the first picking point P2

Figure3-41 Update P2

(4) Update placing point P3.

Open “Controller DI/DO” panel. Set **DO\_09** to **ON** to make the robot suck the workpiece, as shown in Figure3-42. Then jog the robot to move to the first placing point (P3) in the storage area, as shown in Figure3-43. Select P3 in Points and click the tool **Cover** . Click **Cover** in the pop-up tips again to update P3 point , as shown in Figure344.

![Official Magician E6 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9ljjd9oCj3mx5lKBG4we%2Futp-6935e52088201ed16fe8.jpg?alt=media)

![Official Magician E6 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrgzJGuXMTcfoCy09iU0i%2Futp-f6d39cea2b9dcae63bac.jpg?alt=media)

![Official Magician E6 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

Figure3-42 Controller DI/DO panel

Figure3-43 Locate the first placing point P3

![Official Magician E6 training-system figure, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F26KenPjX34iujg6hlXgo%2Futp-4ec4e88359215127c73d.png?alt=media)

![Official Magician E6 training-system figure, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3hOOCZI9m0sYjycnMMEo%2Futp-1b9311137b60fd86305b.jpg?alt=media)

Figure3-44 Update P3

Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1

second, set **DO\_10** to **OFF** and observe whether the workpiece is placed into the groove accurately. If not, you need to re-debug the point.

#### 3.7 Run program

Click . Observe whether the program is running as follows: The robot puts the workpieces arranged in a 3×3×1 matrix on the standard vision board into the storage area and codes it as 1×3×3 stacks, as shown in Figure3-45.

Figure3-45 Palletizing effect

Note: During the program operation, if the robot’s point position is found to be incorrect, please

![Official Magician E6 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FttxpURIedspchCL90xJH%2Futp-443388d5b6342e1ac393.jpg?alt=media)

![Official Magician E6 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmSko2SXtcBaxRSFTHItF%2Futp-ff48270478a1587417a4.jpg?alt=media)

![Official Magician E6 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

directly press the “ ” button to stop the program operation, and then follow the method

explained in 3.6 to perform point debugging again.

#### 3.8 Export project

Click to open File menu and select “Export project”. Select the path to save

the program. Then enter a project name in the pop-up dialog box.

Note: Exporting a project refers to exporting the program to local for backup.

### 4. Key Program Description

This section mainly describes the key script. The complete code can be viewed in

the script project page.

#### 4.1 Output port reset program

The output port reset program is shown in Figure3-46, which sets all output ports

to **OFF** .

Figure3-46 Output port reset program

#### 4.2 Attitude adjustment program

Adjust the posture of the robot with coordinates {0,0, -90,0, 90,0}, as shown in

Figure3-47 and Figure3-48.

Figure3-47 The posture adjustment program of the robot

Figure3-48 Robot posture

#### 4.3 Robot pick-up program

The robot pick-up program is shown in Figure3-49, which controls the robot to

pick up the workpieces from the standard vision board.

Figure3-49 Robot pick-up program

You only need to teach and save the placing point P2 of the first workpiece. Then the corresponding coordinates of 8 other picking points can be obtained according to the distance between the first picking point and each of the remaining picking points.

The order of material collection is shown in Figure3-50, with the red column taken first, followed by the green column, and finally the blue column.

![Official Magician E6 training-system figure, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNejXQZejePervcaQQPat%2Futp-4a5be73ad2f93dd3a527.jpg?alt=media)

![Official Magician E6 training-system figure, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJhgpjYgimY9u7JK5asqx%2Futp-8a5fc576d2dfd3258236.png?alt=media)

Figure3-50 The order of material collection

#### 4.4 Robot placement program

The robot placement program is shown in Figure3-51 which controls the robot to

place nine workpieces into the storage area and code it as 1×3×3 stacks.

Figure3-51 Robot placement program

You only need to teach and save the placing point P3 of the first workpiece. Then the corresponding coordinates of 8 other placing points can be obtained according to the distance between the first placing point and each of the remaining placing points.

![Official Magician E6 training-system figure, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZ4ddZOHq0YaxiOzNJAkC%2Futp-4376f9479ec034093abf.jpg?alt=media)

![Official Magician E6 training-system figure, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5JqtFUS89MhaUtLoGnlE%2Futp-b14dd60f940e9ce2d70d.png?alt=media)

## Chapter 4 Application of Visual Sorting

### 1. Introduction

Based on the visual inspection of the workpiece coordinates and color recognition information, the robot transports the square workpieces (with any number of two colors) on the loading plate, as shown in Figure4-1, to the corresponding storage area in the square grooves of the loading plate, with red and green workpieces placed in one column each, as shown in Figure4-2. If the number of the same colour exceeds 3, it will be stacked and placed.

Figure4-1 Rectangular workpieces

Green workpieces Red workpieces\
placement area placement area<br>

Figure4-2 Storage area

![Official Magician E6 training-system figure, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTYGi1yRDCmNdyWfeK96r%2Futp-35ee2388667a88818afc.jpg?alt=media)

![Official Magician E6 training-system figure, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpT6BJthFer0dTvvbznRd%2Futp-81088d683f1c4bb8f117.jpg?alt=media)

### 2. IO Configuration

The IO configuration of visual sorting is shown in Table4-1 .

**Table4-1 IO configuration**

| **Output** | **Descr** | **iption** |
| ---------- | --------- | ---------- |
| DO09       | Vacuum    | pumping    |
| DO10       | Vacuum    | breaking   |

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 3.1.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it

on, as shown in Figure4-3.

Figure4-3 Turn on the E6 power switch

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to Auto, as shown in Figure4-4.

![Official Magician E6 training-system figure, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

Figure4-4 Turn on the power switch of the pump box

#### 3.1.4 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the other end to the PC.

* (2) Modify IP of the PC.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure4-5. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

![Official Magician E6 training-system figure, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIOo2VwMNtIqj3S5oUm1e%2Futp-fb05a14080aeb7630a08.jpg?alt=media)

Figure4-5 Set IP of the PC

* (3) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro** to open the software. After you enter DobotStudio

Pro, the software will automatically search for robots and displays the search results “Magician E6” on the interface. Click **Connect** on the right side of the device to connect

it, as shown in Figure4-6.

![Official Magician E6 training-system figure, source page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDb5ccDkzTmqRU8BOmmx9%2Futp-ca3a257ba809811bdc70.png?alt=media)

![Official Magician E6 training-system figure, source page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRujPrpBXi8viLdzRzUD4%2Futp-1436143103c7aa0204d7.png?alt=media)

Figure4-6 Connect robot

After successful connection, the software interface will refresh and display the information about the E6 and its 3D model, as shown in Figure4-7.

Figure4-7 the information about the E6

#### 3.1.5 Enable robot

Click on the “Enable” switch in the “Magician E6” interface. Modify various parameter values according to the actual situation in the “Load enabling settings” window that pops up. Click **Enable,** as shown in Figure4-8. The Enabling switch

changes to in the E6 interface.

![Official Magician E6 training-system figure, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

Figure4-8 Set load parameters

#### 3.1.6 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to

set the speed to 20%, as shown in Figure4-9.

Figure4-9 Set Speed

#### 3.1.7 Install suction cup tool

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure4-10. It is best to adjust the coordinate value of J6 to 0°, as shown in Figure4-11.

![Official Magician E6 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

Figure4-10 The posture of installing the end tool

Figure4-11 Coordinates for installing the end tool

(2) Install the suction cup onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Figure4-12.

![Official Magician E6 training-system figure, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4YCH0hDYQtwlUfbycbrL%2Futp-66158be50749ed75a504.jpg?alt=media)

![Official Magician E6 training-system figure, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGID1lJWubeuP8tsnZlsT%2Futp-b553235602b81b2845ed.jpg?alt=media)

Figure4-12 Install the suction cup on the end of the robot

(3) Connect one end of the air pipe to the “Air” hole in the air pump box, and the

other end to the suction cup. Fix it to the robot with a tie, as shown in Figure4-13.

Figure4-13 Connect the air pipe

#### 3.1.8 Adjust the robot’s posture

Adjust the robot’s posture to a vertical position through the control panel, as shown in Figure4-14, so that the joint coordinates are {0, 0, -90, 0, 90, 0}.

![Official Magician E6 training-system figure, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzcv41juFPW7siMzWaWqI%2Futp-17f289914692994ebfa2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGHMloBxWCbCJ7Vzxmw3m%2Futp-748440c039c3f49da81b.jpg?alt=media)

Figure4-14 Adjust the robot’s posture

#### 3.1.9 Install standard visual carrier

Install the standard visual carrier board above the conveyor belt, as shown in

Figure4-15.

Figure4-15 Install standard visual carrier board

#### 3.1.10 Connect the camera

Insert the encryption dog of Dobot VisionStudio into the computer, and then plug

the USB plug of the training platform vision (used to connect the camera) into the USB

interface of the computer.

#### 3.1.11 Turn on the light source switch

Turn on the power switch of the circular light source.

![Official Magician E6 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fksw5YLQKKPrr3LO6R4x8%2Futp-90ab4ecf4d4d9d93ab9a.jpg?alt=media)

![Official Magician E6 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5Ehw6wCVC09ivS9TmMUc%2Futp-f05b77dc434d53908ec5.jpg?alt=media)

#### 3.2 Debug vision program

#### 3.2.1 Eye-to-hand calibration

* (1) Place the calibration board on the standard visual carrier board, as shown in

Figure4-16.

Figure4-16 Calibration board placement

Note: To avoid sliding of the calibration board, adhesive tape can be used to secure it.

* (2) Remove the suction nozzle from the suction nozzle connecting rod and install

the calibration needle, as shown in Figure4-17.

Figure4-17 Install the calibration needle

* (3) Open DobotVisionStudio and select **General Solution** .

![Official Magician E6 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA1zNOqQhn9BoCL0fKc5e%2Futp-21e2241f0933a51a6056.jpg?alt=media)

![Official Magician E6 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXBCxjt6S1RBsMEKU2bUm%2Futp-6413364cb964bf1849e5.jpg?alt=media)

(4) Establish the flow. Drag **Image Source** in Acquisition toolbox to the flow editing area, as shown in Figure4-18.

Figure4-18 Flow

①Set **0Image Source1** parameters. Double-click **0Image Source1** to set parameters. Select **Image Source** to **Camera** . Click **Camera set** on the right side of **Relate Camera** to enter the corresponding page, as shown in Figure4-19.

Figure4-19 Set Image Source parameters

②Create global camera. Click **+** on the right side of **Device List** to create **1 Global Camera1** and set the parameters of the camera. In the “Common Params” tab, click the triangle in the lower right corner of **Choose Camera** to open the drop-down list and select the camera that is currently connected to the computer. Select **Mono8** for **Pixel Format** , as shown in Figure4-20. Click **Trigger Settings** tab, and set **Trigger Source**

![Official Magician E6 training-system figure, source page 71](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYh4PiYmIbqGLOjETa40i%2Futp-664e160b702aed1a395e.png?alt=media)

![Official Magician E6 training-system figure, source page 71](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLvPgBzDlOPnsKFYOkxrk%2Futp-b09976af39162b0eff59.png?alt=media)

to **SOFTWARE** . Then click **Confirm** , as shown in Figure4-21.

Figure4-20 Common Params

Figure4-21 Trigger Settings

In “0 Image Source” page, click the triangle in the lower right corner of **Relate**

**Camera** and select **1Global Camera1** , as shown in Figure4-22.

![Official Magician E6 training-system figure, source page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuJYKQskIO6eHS7bHKRkx%2Futp-0fc8e039b03961c8ffbb.png?alt=media)

![Official Magician E6 training-system figure, source page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxQMFOirRac9SBMYflD3G%2Futp-ebbdbf9bfdd9f3baab00.png?alt=media)

Figure4-22 Relate Camera

③Click (Continuously) on the toolbar to adjust the aperture and focus ring

of the lens and the exposure time of the camera until you can see a clear image in the image display area. The image acquisition result is shown in Figure4-23.

Figure4-23 Image acquisition result

(5) Add **CalibBoard Calib** in the flow.

Drag **CalibBoard Calib** in Calibration toolbox to the flow editing area. Connect

it with **0Image Source1** , as shown in Figure4-24.

![Official Magician E6 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FF1v38FTXJ5KQv0XQ2Y1u%2Futp-01b767d049c8b18825db.jpg?alt=media)

![Official Magician E6 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F05SyxvYsSkCNccpWkjOr%2Futp-d6b17ccbf095379e4cc0.png?alt=media)

Figure4-24 Flow

Note: The calibration of the calibration board is used to obtain the calibration point, and provide

the pixel coordinates of the calibration point for N-point calibration.

* (6) Add **N-point Calibration** in the flow.

①Drag **N-point Calibration** in Calibration toolbox to the flow editing area.

Connect it with **2CalibBoard Calib1** . Click (Once) in the toolbar. Nine calibration points and their calibration sequence are shown automatically in the image display area, as shown in Figure4-25.

Figure4-25 Flow and calibration sequence

②Set **3N-point Calibration** basic parameters. Double-click **3N-point Calibration** to set basic parameters. In “Basic Params” page, set **Translation Number**

to **9** by default, as shown in Figure4-26. Click on the right side of **Rotation Number** to edit the calibration points, as shown in Figure4-27.

![Official Magician E6 training-system figure, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLDGaz3nzOu6ry6DhD2vd%2Futp-919bb8ad223584066b28.jpg?alt=media)

Figure4-26 3N-Point Calibration

Figure4-27 “Edit Calibration Points” interface

In “Edit Calibration Points” page, exchange Line 3 (ID: 3) and Line 5 (ID: 5) data,

as shown in Figure4-28.

![Official Magician E6 training-system figure, source page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2ipLPIgghuX0PjKbiTqK%2Futp-8461ac5c4cee840b20f5.png?alt=media)

![Official Magician E6 training-system figure, source page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtXZZZNHASkf0gg82pSgl%2Futp-b20f2adbc901cb2af5c1.png?alt=media)

Figure4-28 “Edit Calibration Points” after data exchange

Click (Once), and you will see that the calibration sequence in the image display area turn to “ ” shape, as shown in Figure4-29.

Figure4-29 Calibration sequence after data exchange

③Switch to DobotStudio Pro, control the robot to move according to the sequence

of the nine points.

Move the robot to the first calibration point, and read the physical coordinates X and Y of the first point in DobotStudio Pro, as shown in Figure4-30. Fill the X and Y values in the physical coordinates of the first line in “Edit Calibration Points” page in DobotVisionStudio, as shown in Figure4-31. Obtain the physical coordinates of the remaining 8 points and fill in “Edit Calibration Points” page, as shown in Figure4-32.

![Official Magician E6 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOhvMGJbWiemGAmBiZzBq%2Futp-d348ca27eda7059f8b60.png?alt=media)

![Official Magician E6 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfoUN88BQPrnBTOnowT7g%2Futp-79ff44f2cb6db5db3ef2.jpg?alt=media)

Figure4-30 Locate the first calibration point

Figure4-31 Fill in the physical coordinates of the first calibration point

![Official Magician E6 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD8JdCAKz6nX1TW9vNOfT%2Futp-2f6cc0198964836e8239.jpg?alt=media)

![Official Magician E6 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx0qjwTvOiyBhJ258PWFH%2Futp-c25a86865998bba5b99c.png?alt=media)

![Official Magician E6 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvavAKIDaIlZnGdfMeNu5%2Futp-82026f23ad61cf09e1b7.png?alt=media)

Figure4-32 Physical coordinates of 9 calibration points

④Create the calibration file. After editing the calibration points, click in “Basic Params” page. Click **Create Calibration File** to export the calibration file to local and name it , as shown in Figure4-33.

Figure4-33 Create calibration file

(7) Add **Calibration Transformation** in the flow. After establishing the calibration file, it is necessary to verify whether the calibration is accurate.

Drag **Calibration Transformation** in Calculation toolbox to the flow editing area, and connect it with **3N-point Calibration1** , as shown in Figure4-34.

![Official Magician E6 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPSxMyzujIQNu52Fcxcrg%2Futp-417eec82e6e80abcd8de.png?alt=media)

![Official Magician E6 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVwEwlIrOqkXnDMNVpjPm%2Futp-8dfc5b1683f69d913a5b.png?alt=media)

Figure4-34 Flow

②Set **4Calibration Transformation** parameters. In “Basic Params” page, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** . Set **Load Calibration File** to **Calibration file** generated from 3N-point Calibration1, as shown in Figure4-35.

Figure4-35 Set “4Calibration Transformation” parameters

③Click (Once), and check whether the nine coordinates after **4Calibration Transformation1** are consistent with the physical coordinates in **3N-point Calibration1** , as shown in Figure4-36. If the difference in values is very small, it indicates that the calibration is accurate. Otherwise, you need to re-calibrate.

![Official Magician E6 training-system figure, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnYRiVeX96GJLzlRiUhtj%2Futp-9c13af414e9b584b0f5f.png?alt=media)

Figure4-36 Comparison result

Note: The converted sequence numbers “3” and “5” need to be compared with the “5” and “3” of “Edit Calibration Points”.

After the calibration is completed, it is necessary to remove the calibration needle from the suction nozzle connecting rod and install the suction nozzle.

#### 3.2.2 Import vision program

Open DobotVisionStudio 4.1.2 and select **General Solution** . Select **Open** in the toolbar. Find the visual sorting program and click **Open** . The imported vision program is shown in Figure4-37.

![Official Magician E6 training-system figure, source page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ficf2IzFNid0avxfg8HzQ%2Futp-7abf529b053a764882d6.jpg?alt=media)

Figure4-37 Vision program

#### 3.2.3 Place detection object

Place seven rectangular workpieces of two different colors in the detection field

of view, as shown in Figure4-38.

Figure4-38 Place seven workpieces within the detection field of view

#### 3.2.4 Debug program parameters

* (1) Debug **0Image Source** parameters.

Click (Once). Select **0Image Source1** and observe whether the image is clear.

![Official Magician E6 training-system figure, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxLvseMezvrChmr8MW2Ix%2Futp-ed7421dd1da38ccd7b2f.png?alt=media)

![Official Magician E6 training-system figure, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ4byAS9oQWkRJ8odV5RJ%2Futp-f98d16579462e03b6508.jpg?alt=media)

If the image is not clear or there is no image, you need to reset the parameters according to the method described in 3.2.1. When setting the parameters, set **Pixel Format** to **RGB8** . The image collected by the camera is shown in Figure4-39.

Figure4-39 Collected image

* (2) Debug **2Color Transformation1** parameters.

Double-click **2Color Transformation1** to check whether **Transfer Type** is **RGB**

**to Grayscale** , as shown in Figure4-40. If not, modify as the figure.

Figure4-40 2Color Transformation

![Official Magician E6 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHSuaKWcr8yILPrvpye8M%2Futp-b3af7e9f237a35aa5982.jpg?alt=media)

![Official Magician E6 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFcHAem2U4d4EtMoM5QBi%2Futp-de00b82901d86f1a41d0.png?alt=media)

Click

(Once). The execution result of 2Color Transformation1 is shown in

Figure4-41.

Figure4-41 Grayscale Image

* (3) Debug **3Fast Match1** parameters.

Double-click **3Fast Match1** . Click **Run Params** and modify **Max Number to**

**find** to **7** (Number of rectangular workpieces). Then click **Execute** and observe whether

all the workpieces are recognized in the image display area, as shown in Figure4-42.

Figure4-42 Run Params

![Official Magician E6 training-system figure, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBSiiIkOaQBKFAYdRn1Vn%2Futp-f89505adb0582ddfac72.jpg?alt=media)

![Official Magician E6 training-system figure, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7rbH7UjXrHNvCIUUdob8%2Futp-06db4713b06fb26bf633.png?alt=media)

If all the workpieces are recognized, use the original model. Otherwise, you need to re-create the feature model, as described below.

①Enter “Feature Model” page. Delete the original model and then click **Create** , as shown in Figure4-43.

Figure4-43 Feature Model

②In ModelSettings page, click **Current Image** . Click (Create Rect Mask), select the corresponding area in the image and set corresponding model parameters (generally default). Then click (Build Model) and click **Confirm** , as shown in Figure4-44.

Figure4-44 ModelSettings

![Official Magician E6 training-system figure, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F46J7jDhAOeibwsoF4HXq%2Futp-2b71709252c4aa561e89.png?alt=media)

![Official Magician E6 training-system figure, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8QL75o6C7b8VUhIHVAoE%2Futp-e87a9987ee16366fc92a.jpg?alt=media)

* ③After creating the model, click **Execute** and **Confirm** , as shown in Figure4-45.

Figure4-45 Result

Note: If not all the workpieces can be recognized, maybe it is caused by the light. You can

change the threshold value.

④Double-click **3Fast Match1** . Click **Run Params** and modify **Max Number to find** to **1** . Then click **Execute** , and the recognized workpiece is shown in the image

display area. Click **Confirm** , as shown in Figure4-46.

Figure4-46 Result

* (4) Debug **4Calibration Transformation1** parameters.

Double-click **4Calibration Transformation1** . Check whether **Coord Point** is

* 3 **Fast Match1.Match Point** . Load the saved calibration file, as shown in Figure4-47.

![Official Magician E6 training-system figure, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCV0PKSHRhsMstwofx2k8%2Futp-5b5f7a2789cf6228a299.jpg?alt=media)

![Official Magician E6 training-system figure, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWVnlUetVneWSbvc4XtYt%2Futp-b36457b57bb42447ba79.jpg?alt=media)

Figure4-47 Basic Params

Click **Execute** and **Confirm** , and the physical coordinates of the workpieces are

displayed in the result display area, as shown in Figure4-48.

Figure4-48 Result

(5) Debug **5Color Recognition1** parameters.

![Official Magician E6 training-system figure, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCgKzEFpo912332Td4RVm%2Futp-08436dcb9ed75ce54873.png?alt=media)

![Official Magician E6 training-system figure, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fkjo9LB7rV7YHjn5iMi7H%2Futp-050d6998a3f37261e129.jpg?alt=media)

Click (Once). Select **5Color Recognition1** and modify the image display to **ImageSource1.OutputImage** . Observe whether the color of the image is recognized correctly, as shown in Figure4-49.

Figure4-49 Result

If the colors are recognized incorrectly, you need to debug according to the following method.

①Double-click **5Color Recognition1** . Check whether **Input Source** and **ROI**

**Area** in “Basic Params” page are set as Figure4-50.

![Official Magician E6 training-system figure, source page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzc4RbmMgTUbzB0Z7dSf4%2Futp-96e1778ed958757c75ff.jpg?alt=media)

Figure4-50 Basic Params

②In “Color Model” page, delete the existing models. Click **+** to re-create models,

as shown in Figure4-51.

Figure4-51 Color Model

③Create a red model. In **ModelSettings** page, click (add the current image),

then click **+** on the right side of **Label List** to add a new label and change the label name. Click in the toolbar and drag a rectangular mask on the current image. Then click **Add To Label** and you will see the added red model on the right side, as shown in Figure4-52.

![Official Magician E6 training-system figure, source page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbszTbkmkMlD88ckEcixf%2Futp-27eebcb52c30f71e5cd8.png?alt=media)

![Official Magician E6 training-system figure, source page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFxMlRUPV0PDsk7mBSZAq%2Futp-f462ebd2851687b0c65f.png?alt=media)

Figure4-52 Create red model

Note: The material may be reflective due to the light which could result in a difference in color.

In this case, you need to create several red models.

④Create the green models as shown in Figure4-53 using the same method. Click

**Confirm** to return to “Color Model” page.

![Official Magician E6 training-system figure, source page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmS1qEVHG2BoF2wV5TBVd%2Futp-dce0aa610bdafc572a14.jpg?alt=media)

Figure4-53 Create green models

⑤Click **Execute** and **Confirm.** The recognized color of the workpieces is shown

in the result display area, as shown in Figure4-54.

Figure4-54 Result

(6) Debug **6Variable Calculation1** parameters.

Click (Once). Select **6Variable Calculation1** and check whether **var0** which

in the display area and the **MatchBoxAngle** value of **3Fast Match** are opposite values, as shown in Figure4-55.

![Official Magician E6 training-system figure, source page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWLxdOoKy3mrlwolpihDN%2Futp-e9a4bb76bab5e8973f2d.jpg?alt=media)

![Official Magician E6 training-system figure, source page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDbiovUadnsF65r8pYV05%2Futp-3b2e1b596d55889ead7c.jpg?alt=media)

![Official Magician E6 training-system figure, source page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDBLlBydpHriPPZu7HeHq%2Futp-af941278f8fa31911373.jpg?alt=media)

Figure4-55 Comparison result

If the values are not opposite, you need to debug according to the following method.

①Double-click **6Variable Calculation1** . Click below **Expression** to enter

**Var0** page. Click and select **3Fast Match1**  **MatchRect**  **MatchBoxAngle** , and then plus “-” in front of the variable, that is, to get the negative value of the angle. Then click **Save** to return to the “Basic Params” page, as shown in Figure4-56.

Figure4-56 Expressions

![Official Magician E6 training-system figure, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEu33VWg0Uv3sK9NYyEi8%2Futp-4dcec1ca86e17fbb32bb.jpg?alt=media)

![Official Magician E6 training-system figure, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUBKpdvvdAlvZbqlJiNH5%2Futp-3ae115c459d6f3b57be2.png?alt=media)

* ②Click **Execute** and **Confirm** and you will see the angle value, as shown in

Figure4-57.

Figure4-57 Result

* (7) Debug **7Format1** parameters.

Click (Once). Select **7Format1** and observe whether the result display area

shows the format result as Figure4-58.

![Official Magician E6 training-system figure, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLla5OG77XrUEq5YfdKgQ%2Futp-9ea2709fc3cb41e05eea.jpg?alt=media)

Figure4-58 Result

If not, you need to debug according to the following method.

* ①Double-click **7Format1** . In “Basic Params” page, as shown in Figure4-59, click

**+** to add a row. Click (InsertSubscription) and select **5Color Recognition1**  **Best**

**Matched Name** .

![Official Magician E6 training-system figure, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn56GcVfdLnD1OI7VG2qB%2Futp-dc0c7765d93523444746.jpg?alt=media)

Figure4-59 Basic Params

②Then click **T** and enter “,”. Click and select **4 Calibration Transformation1**  **OutputPoint**  **TransPointX** . Insert “<4 Calibration Transformation1.TransPointY(%1.3f)>\[0]” “,”. “<6 Variable Calculation1.var0(%1.3f)>\[0]” “,” “<3 Fast Match1.ModuStatus(%0d)>\[0]

following the same method. The format parameters are shown in Figure4-60.

Figure4-60 Format Params

(8) Debug Communication Management parameters.

![Official Magician E6 training-system figure, source page 94](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd335unODVoMoSJCtiew5%2Futp-4deb6e034fb6c1ff265c.png?alt=media)

![Official Magician E6 training-system figure, source page 94](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgYvPhFBbTeNhYP6uFXT9%2Futp-6d457cb78cf03f49239d.png?alt=media)

Click in the quick toolbar to enter “Communication Management” page. Check whether there is established TCP Server and whether its parameters are consistent with the figure below. If not consistent, modify as Figure4-61.

Figure4-61 Communication Management

If there is no **TCP Server** , you need to create one, as described below.

Click beside **Device Lists** to add devices. Select **Protocol Type** to **TCP Server,** and modify **Device Name** (TCP Server by default), **Local IP** and **Local Port** according to the actual condition, and click **Create** , as shown in Figure4-62. After creating the communication device, switch on **1TCP Server** , as shown in Figure4-63.

![Official Magician E6 training-system figure, source page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjiKPrhe7VwkXa4UVAUp6%2Futp-f50e08df10a1531c4995.png?alt=media)

Figure4-62 Add device

Figure4-63 TCP Server

* (9) Debug **8Send Data1** parameters.

Double-click **8Send Data1** and check whether the parameters are shown as Figure4-64. If not, modify as the figure. Set **Output To** to **Communication Device** , **Communication Device** to **1 TCP Server** , and **Send Data1** to **7Format1.format\_out\[]** . Then click **Confirm** .

![Official Magician E6 training-system figure, source page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW9lgwD3wRvzvoR6tVmOq%2Futp-29d56a601c7da5beb3ce.jpg?alt=media)

![Official Magician E6 training-system figure, source page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYMxaD9hRI0XWWmsFHmL8%2Futp-88697e4bb06b31f593df.png?alt=media)

Figure4-64 Send Data

* (10) Global trigger settings

Click in the quick toolbar to enter “Global Trigger” page. In “String Trigger” page, check whether the string trigger setting is shown as Figure4-65 (String is void; Mode is Mismatched; Trigger Configuration is All Process).

Figure4-65 Set Global Trigger parameters

#### 3.2.5 Save program

Click in the toolbar to save the program. If you need to save the program elsewhere on your local computer, click **File** > **Save as** , select the saving path and enter the name of the project.

![Official Magician E6 training-system figure, source page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx1IPS5UFrpEHtPojPwdN%2Futp-0e9b3058365b64bd00ef.jpg?alt=media)

![Official Magician E6 training-system figure, source page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhR1OAIWUwjShffP6VhZW%2Futp-0a86b65db70ed8fe13f7.png?alt=media)

#### 3.3 Debug robot program

#### 3.3.1 Import program

* (1) On the Home screen of DobotStudio Pro software, click **Application > Script**

**programming** and enter “Programming” interface, as shown in Figure4-66.

Figure4-66 Enter “Programming ” interface

* (2) Click to open File menu and select “Import project”, as shown in

Figure4-67. Select **Vision\_Sorting** folder, and click **Open** . Now the **Vision\_Sorting** program has been imported into DobotStudio Pro, as shown in Figure4-68.

Figure4-67 Import project

![Official Magician E6 training-system figure, source page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOHGC48azPSIFZ1K00Ghe%2Futp-1f24392881c675820cef.jpg?alt=media)

![Official Magician E6 training-system figure, source page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUbFBlj439vs9tUdCkkai%2Futp-cf36ed7c290c8cc831c6.png?alt=media)

Figure4-68 Project imported

#### 3.3.2 Save program

Click and enter a project name in the pop-up dialog box. Click **Save** , as

shown in Figure4-69.

Figure4-69 Save program

#### 3.3.3 Set communication

Ensure that the IP address and port of TCP server in the robot program are consistent with those in vision communication settings, that is, set IP address in the robot program to 192.168.5.18. Set port to 4001, as shown in Figure4-70.

![Official Magician E6 training-system figure, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmYNcFHGFAhTtJ7Vdj96Q%2Futp-e3c7bfa73cd100e0731b.png?alt=media)

![Official Magician E6 training-system figure, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLovG6Vxnxkx9x5YnkNVP%2Futp-709e4db7888eff8f65ba.png?alt=media)

Figure4-70 Set communication

#### 3.3.4 Modify Z coordinates

* (1) Modify Z coordinate of the picking point.

Jog the robot make the suction cup slightly touch the surface of the workpiece, as shown in Figure4-71. Then read the current Z coordinate of the robot, as shown in Figure4-72. Modify the Z coordinate in the command “local GetProductPos = {pose = {move\_x, move\_y, 190.5,P1.pose\[4],P1.pose\[5], move\_r} }” of the pickup sub-

program to the current Z coordinate.

Figure4-71 Picking point

![Official Magician E6 training-system figure, source page 100](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1w1oHFzrTZXA566fGeos%2Futp-3677849cd31f334fdc24.jpg?alt=media)

Figure4-72 Z coordinate of picking point

(2) Modify Z coordinate over the picking point.

Jog the robot to lift some distance, as shown in Figure4-73. Then read the Z coordinate of the robot, as shown in Figure4-74. Modify the Z coordinate in the command “local GetProductPosUp = {pose = {move\_x, move\_y, 232.2, P1.pose\[4], P1.pose\[5], move\_r} }” of the pickup sub-program to the current Z coordinate.

![Official Magician E6 training-system figure, source page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiQhDwZ9JR9IR1390yy2b%2Futp-9f888d7f5ad3dca889c8.jpg?alt=media)

Figure4-73 Over picking point

Figure4-74 Z coordinate over picking point

![Official Magician E6 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMoVue80EJgFczOwKk7UF%2Futp-7d371059b5d239f87e79.jpg?alt=media)

![Official Magician E6 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5Cn8tAPOX3vJQJmInMU3%2Futp-00a501321a9a920ff229.jpg?alt=media)

#### 3.3.5 Debug points

The visual sorting demo includes seven major points, as described below.

* (1) Update the safe point P1.

Jog the robot to a position between the conveyor belt and the storage area, as shown in Figure4-75. Click **Points** to enter the Points interface. Firstly select P1.Then click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P1 point,

as shown in Figure4-76. Click

and save the program.

Figure4-75 Locate Point P1

Figure4-76 Update Point P1

(2) Update the first red workpiece placing point P2.

![Official Magician E6 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FglZ4hXYZmapx5HdEqJug%2Futp-6326e7ee311b0a1436b6.jpg?alt=media)

![Official Magician E6 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfKGt8Ox0Itc6qH5Qiaf8%2Futp-5828d73fd804b9f12626.jpg?alt=media)

①Click to make the robot suck a workpiece according to the coordinates sent by the vision system. Then click immediately. Jog the robot to the first red workpiece placing point in the storage area, as shown in Figure4-77. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the red workpiece is placed into the groove accurately. If not, you need to re-debug the point.

Figure4-77 Locate the first red workpiece placing point P2

②Open **Points** page. Select **P2** and click **Cover** , as shown in Figure4-78. Then

click **Cover** in the pop-up Tips dialog box. Click and save the program.

Figure4-78 Update P2

* (3) Update the green workpiece placing point P3.

![Official Magician E6 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNlQgOm3heu9s38JQT9VO%2Futp-cadb612ce8558c66aeba.jpg?alt=media)

![Official Magician E6 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fog6YDVM27CPc3mL9MOYI%2Futp-1496736b9f964b0bbf8a.png?alt=media)

①Click to make the robot suck a workpiece according to the coordinates sent by the vision system. Then click immediately. Jog the robot to the first green workpiece placing point in the storage area, as shown in Figure4-79. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the green workpiece is placed into the groove accurately. If not, you need to re-debug the point.

Figure4-79 Locate the green rectangular workpiece placing point P3

②Open **Points** page. Select **P3** and click **Cover** , as shown in Figure4-80. Then

click **Cover** in the pop-up Tips dialog box. Click and save the program.

Figure4-80 Update P3

Note: When updating the remaining points, only the corresponding colored workpieces will be

![Official Magician E6 training-system figure, source page 105](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCfSK2koOgGwtUAPk29Lc%2Futp-d5c8a363716e9246ba3c.jpg?alt=media)

![Official Magician E6 training-system figure, source page 105](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKzeb0fphSCdF9yrIZHgY%2Futp-6d16e03800c24ed0643f.png?alt=media)

placed.

#### 3.7.6 Run program

Click , and check whether the program is running as follows:

The vision system detects the color and position data of workpiece, and transmits these information to the robot. After obtaining the information, the robot moves to the detection area to suck the workpieces, sorts and places them in the corresponding color area. The sorting effect is shown in Figure4-81.

Figure4-81 Sorting finished

#### 3.3.7 Export program

Click to open File menu and select “Export project”. Select the path to save the program. Then enter a project name in the pop-up dialog box.

Note: Exporting a project refers to export the program to local for backup.

### 4. Key Program Description

#### 4.1 Vision program description

The following text only explains the main functions of each algorithm tool in the program. Please refer to the visual project file for the specific parameter settings of the algorithm tool.

The vision program is shown in Figure4-82. **0Image Source1** is mainly used for image acquisition. During the system operation, the camera takes photos immediately

![Official Magician E6 training-system figure, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsLGl0aacjw9h4qpkPvII%2Futp-3fb885f0f82610a33528.jpg?alt=media)

after the vision software receives the trigger signal sent by the robot. The images acquired are all colored images because color recognition is to be performed. **2Color Transformation1** is mainly used for converting color images into grayscale images to locate grayscale images. **3Fast Match1** is mainly used to locate grayscale images, and to obtain the image coordinates and matching angle of the detected object. **4Calibration Transformation1** is used for transforming the image coordinates obtained by **3Fast Match1** into actual physical coordinates. **5Color Recognition1** is used for creating a color model to recognize the color of workpieces so that sorting can be performed by color. **6Variable Calculation1** is used for correcting the matching angle. **7Format1** is used for summarizing and defining the format of the information that the vision system needs to send to the robot. **8Send Data1** is used for sending the contents of **7Format1** to the robot.

Figure4-82 Vision program

#### 4.2 Robot program description

This section mainly describes the key script. For complete script, see the project

in Script page.

#### 4.2.1 Character separation program

The character separation program is shown in Figure4-83.

Figure4-83 Character separation program

#### 4.2.2 Data transmission program

The data transmission program is shown in Figure4-84 which mainly sends

photography trigger signal “ok” and receives the data sent by the vision system.

Figure4-84 Data transmission program

#### 4.2.3 Robot pick-up program

The robot pick-up program is shown in Figure4-85. The main function achieved

is for the robot to analyze the information sent by the visual system and move to the material retrieval point for material retrieval.

![Official Magician E6 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6j3y2hQQlL5lgyHhCVeF%2Futp-4d24d6e9996c9f260e8e.png?alt=media)

![Official Magician E6 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FT8YE0pHwl1EeZQY64b7R%2Futp-cb5d20f3c11e5b41e0ba.png?alt=media)

Figure4-85 Robot pick-up program

#### 4.2.4 Output port reset program

The output port reset program is shown in Figure4-86, which sets all output ports

to **OFF** .

Figure4-86 Output port reset program

#### 4.2.5 Create TCP client program

Create a TCP client program, as shown in Figure4-87, whose function is to create

a TCP client for communication with visual units.

Figure4-87 Create TCP client program

#### 4.2.6 Attitude adjustment program

The posture adjustment program is shown in Figure4-88, which implements the

function of adjusting the robot's posture to the posture shown in Figure4-89.

Figure4-88 Robot attitude adjustment program

![Official Magician E6 training-system figure, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfhSi0AuoTwYzL0Asn7oh%2Futp-68bf89a940c4e42f6525.png?alt=media)

Figure4-89 Robot attitude

#### 4.2.7 Robot placement program

* (1) Program for placing red workpieces.

If the robot picks up the red workpiece, it moves to the placing point through the safe point (P1) to place the workpiece. Then it returns to P1, as shown in Figure4-90. P2 point is the position of the first red workpiece placement point, and the placement points of other red workpieces are calculated based on the distance between the first red workpiece placement point and each placement point to determine the corresponding placement point coordinates for each red workpiece.

Figure4-90 Red workpieces placement program

* (2) Program for placing green workpieces.

If the robot picks up the green workpiece, it moves to the placing point through the safe point (P1) to place the workpiece. Then it returns to P1, as shown in Figure491. P3 is the position of the first green workpiece placement point, and the placement

![Official Magician E6 training-system figure, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9S2P6hbOaOUD8zmzdbSf%2Futp-389916c54d2a502ff91a.jpg?alt=media)

![Official Magician E6 training-system figure, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjw3DYTq0gem3vBUqjxWL%2Futp-ba8c1155ff9b43b2aa32.png?alt=media)

points of other green workpieces are calculated based on the distance between the first green workpiece placement point and each placement point to determine the corresponding placement point coordinates for each green workpiece.

Figure4-91 Green workpieces placement program

![Official Magician E6 training-system figure, source page 111](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fti9TYv3mMu48Yf7qe4BM%2Futp-63d3b2d8921027538e90.png?alt=media)

## Chapter 5 Application of Visual Positioning Guided

## Assembly

### 1. Introduction

The specific task of visual positioning guided assembly is for the robot to assemble six chips placed on the standard vision board (as shown in Figure5-1) into the six grooves of the mobile phone model based on visual recognition of chip shape and position information, as shown in Figure5-2.

Figure5-1 Phone chip

Figure5-2 Phone model

### 2. IO Configuration

The IO configuration of the visual positioning guided assembly demo is shown in

![Official Magician E6 training-system figure, source page 112](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCy1tkysd5O61KRGe1Jzh%2Futp-bedd9be05882de3bf2df.jpg?alt=media)

![Official Magician E6 training-system figure, source page 112](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8Ry7hhObgabYdYZoEvpD%2Futp-75eb2f8dcc4ed52a36e5.jpg?alt=media)

Table5-1.

**Table5-1 IO configuration**

| **Output** | **Descr** | **iption** |
| ---------- | --------- | ---------- |
| DO09       | Vacuum    | pumping    |
| DO10       | Vacuum    | breaking   |

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 3.1.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it

on, as shown in Figure5-3.

Figure5-3 Turn on the E6 power switch

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to Auto, as shown in Figure5-4.

![Official Magician E6 training-system figure, source page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

Figure5-4 Turn on the power switch of the pump box

#### 3.1.4 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the other end to the PC.

* (2) Modify IP of the PC.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure5-5. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

![Official Magician E6 training-system figure, source page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIOo2VwMNtIqj3S5oUm1e%2Futp-fb05a14080aeb7630a08.jpg?alt=media)

Figure5-5 Set IP of the PC

* (3) Connect DobotStudio Pro to the robot.

Double-click DobotStudio Pro to open the software. After you enter DobotStudio Pro, the software will automatically search for robots and displays the search results “Magician E6” on the interface. Click **Connect** on the right side of the device to connect it, as shown in Figure5-6.

Figure5-6 Connect robot

After successful connection, the software interface will refresh and display the

information about the E6, as shown in Figure5-7.

![Official Magician E6 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDb5ccDkzTmqRU8BOmmx9%2Futp-ca3a257ba809811bdc70.png?alt=media)

![Official Magician E6 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRujPrpBXi8viLdzRzUD4%2Futp-1436143103c7aa0204d7.png?alt=media)

Figure5-7 the information about the E6

**3.1.5 Enable robot**

Click on the “Enable” switch in the “Magician E6” interface. Modify various parameter values according to the actual situation in the “Load enabling settings” window that pops up. Click **Enable** , as shown in Figure5-8. The Enabling switch

changes to in the E6 interface.

Figure5-8 Set load parameters

![Official Magician E6 training-system figure, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

![Official Magician E6 training-system figure, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

#### 3.1.6 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to set the speed to 20%, as shown in Figure5-9.

Figure5-9 Set Speed

#### 3.1.7 Install suction cup tool

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure5-10. It is best to adjust the coordinate value of J6 to 0°, as shown in Figure5-11.

Figure5-10 The posture of installing the end tool

![Official Magician E6 training-system figure, source page 117](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUYEgRpT5lJh3ZmgL3Da3%2Futp-d770f07168e7b81bc3a1.jpg?alt=media)

Figure5-11 Coordinates for installing the end tool

(2) Install the suction cup onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Figure5-12.

Figure5-12 Install the suction cup on the end of robot

(3) Connect one end of the air pipe to the “Air” hole in the air pump box, and the

other end to the suction cup. Fix it to the robot with a tie, as shown in Figure5-13.

![Official Magician E6 training-system figure, source page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGID1lJWubeuP8tsnZlsT%2Futp-b553235602b81b2845ed.jpg?alt=media)

![Official Magician E6 training-system figure, source page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzcv41juFPW7siMzWaWqI%2Futp-17f289914692994ebfa2.jpg?alt=media)

Figure5-13 Connect the air pipe

#### 3.1.8 Adjust the robot’s posture

Adjust the robot’s posture to a vertical position through the control panel, as shown

in Figure5-14, so that the joint coordinates are {0, 0, -90, 0, 90, 0}.

Figure5-14 Adjust the robot's posture

#### 3.1.9 Install standard visual carrier

Install the standard visual carrier board above the conveyor belt, as shown in Figure5-15.

![Official Magician E6 training-system figure, source page 119](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyuH8Qv9FBsdk83xn0AXm%2Futp-1f4e8b2eb7ec2f7dd289.jpg?alt=media)

![Official Magician E6 training-system figure, source page 119](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fksw5YLQKKPrr3LO6R4x8%2Futp-90ab4ecf4d4d9d93ab9a.jpg?alt=media)

**Application of the visual positioning** **guided assembly**

Figure5-15 Install standard visual carrier board

#### 3.1.10 Install the mobile phone model workpiece loading board

Install the mobile phone model workpiece loading board into the storage area, as shown in Figure5-16. Place the mobile phone model workpiece into the mobile phone

model workpiece loading board, as shown in Figure5-17.

Figure5-16 Installation of mobile phone model workpiece loading board

Figure5-17 Place mobile phone model workpiece

![Official Magician E6 training-system figure, source page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5Ehw6wCVC09ivS9TmMUc%2Futp-f05b77dc434d53908ec5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ftt3VG8vIs3OKbIoAL6Iw%2Futp-7cf6ea55e2bc2c1064ed.jpg?alt=media)

![Official Magician E6 training-system figure, source page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOFCY2ZMcFJzU3iGi561y%2Futp-4453b25548e68070c66f.jpg?alt=media)

#### 3.1.11 Connect the camera

Insert the encryption dog of Dobot VisionStudio into the computer, and then plug the USB plug of the training platform vision (used to connect the camera) into the USB

interface of the computer.

#### 3.1.12 Turn on the light source switch

Turn on the power switch of the circular light source.

#### 3.2 Debug vision program

#### 3.2.1 Eye-to-hand calibration

* (1) Place the calibration board on the standard vision board, as shown in Figure5-

18.

Figure5-18 Place the Calibration board

Note: To avoid sliding of the calibration board, adhesive tape can be used to secure it.

* (2) Remove the suction nozzle from the suction nozzle connecting rod and install

the calibration needle, as shown in Figure5-19.

![Official Magician E6 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA1zNOqQhn9BoCL0fKc5e%2Futp-21e2241f0933a51a6056.jpg?alt=media)

**Application of the visual positioning** **guided assembly**

Figure5-19 Install the calibration needle

(3) Open DobotVisionStudio and select **General Solution** .

(4) Establish the flow. Drag **Image Source** in Acquisition toolbox to the flow editing area, as shown in Figure5-20.

Figure5-20 Flow

①Set **0Image Source1** parameters. Double-click **0Image Source1** to set parameters. Select **Image Source** to **Camera** . Click **Camera set** on the right side of **Relate Camera** to enter the corresponding page, as shown in Figure5-21.

![Official Magician E6 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhhNFIeTwQSA0nbIiAJ3H%2Futp-6b674c2be0ae94474ed9.jpg?alt=media)

![Official Magician E6 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYh4PiYmIbqGLOjETa40i%2Futp-664e160b702aed1a395e.png?alt=media)

Figure5-21 Set “Image source” parameter

②Create the global camera. Click **+** on the right side of **Device List** to create **1 Global Camera1** and set the parameters of the camera. In the “Common Params” tab, click the triangle in the lower right corner of **Choose Camera** to open the drop-down list and select the camera that is currently connected to the computer. Select **Mono8** for **Pixel Format** , as shown in Figure5-22. Click “Trigger Settings” tab, and set **Trigger Source** to **SOFTWARE** . Then click **Confirm** , as shown in Figure5-23. In “0 Image Source” page, click the triangle in the lower right corner of **Relate Camera** and select **1Global Camera1** , as shown in Figure5-24.

Figure5-22 Set “Common Parameters”

![Official Magician E6 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGFglOUzksRl3ABePSI4h%2Futp-cb90e18447e2a540ca2b.png?alt=media)

![Official Magician E6 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuJYKQskIO6eHS7bHKRkx%2Futp-0fc8e039b03961c8ffbb.png?alt=media)

Figure5-23 Set “Trigger settings”

Figure5-24 Relate Camera

③Click (Continuously) to adjust the aperture and focus ring of the lens and the exposure time of the camera until you can see a clear image in the image display area. The image acquisition result is shown in Figure5-25.

![Official Magician E6 training-system figure, source page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxQMFOirRac9SBMYflD3G%2Futp-ebbdbf9bfdd9f3baab00.png?alt=media)

![Official Magician E6 training-system figure, source page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F05SyxvYsSkCNccpWkjOr%2Futp-d6b17ccbf095379e4cc0.png?alt=media)

**Application of the visual positioning** **guided assembly**

Figure5-25 Image acquisition result

* (5) Add **CalibBoard Calib** in the flow.

Drag **CalibBoard Calib** in Calibration toolbox to the flow editing area and connect it with **0Image Source1** , as shown in Figure5-26.

Figure5-26 Flow

Note: The calibration of the calibration board is used to obtain the calibration point, and provide

the pixel coordinates of the calibration point for N-point calibration.

* (6) Add **N-point Calibration** in the flow.
* ①Drag **N-point Calibration** in Calibration toolbox to the flow editing area, and

connect it with **2CalibBoard Calib1** . Click (Once) in the toolbar, and nine calibration points and their calibration sequence are shown automatically in the image display area, as shown in Figure5-27.

![Official Magician E6 training-system figure, source page 125](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdDa21sPLcOFT3hOLacqE%2Futp-fd0d0c14f1df2383fd4f.jpg?alt=media)

**Application of the visual positioning** **guided assembly**

Figure5-27 Process of hand eye calibration scheme and calibration sequence

②Set **3N-point Calibration1** basic parameters. Double-click **3N-point Calibration** to set basic parameters. In “Basic Params” page, set **Translation Number** to **9** by default, as shown in Figure5-28. Click on the right side of **Rotation Number** to edit the calibration points, as shown in Figure5-29.

Figure5-28 “3N-point calibration” parameter setting

![Official Magician E6 training-system figure, source page 126](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLDGaz3nzOu6ry6DhD2vd%2Futp-919bb8ad223584066b28.jpg?alt=media)

![Official Magician E6 training-system figure, source page 126](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtXZZZNHASkf0gg82pSgl%2Futp-b20f2adbc901cb2af5c1.png?alt=media)

Figure5-29 Edit Calibration Points

In “Edit Calibration Points” page, exchange Line 3 (ID: 3) and Line 5 (ID: 5) data,

as shown in Figure5-30.

Figure5-30 “Edit Calibration Points” after data exchange

Click (Once) and you will see that the calibration sequence in the image display area turns to “ ”, as shown in Figure5-31.

![Official Magician E6 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2ipLPIgghuX0PjKbiTqK%2Futp-8461ac5c4cee840b20f5.png?alt=media)

![Official Magician E6 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOhvMGJbWiemGAmBiZzBq%2Futp-d348ca27eda7059f8b60.png?alt=media)

**Application of the visual positioning** **guided assembly**

Figure5-31 Calibration sequence after data exchange

③Switch to the DobotStudio Pro software and control the robot to move in the order of 9 calibration points.

Firstly, control the robot to reach the first calibration point, and then read the physical coordinates X and Y of the first point in the DobotStudio Pro software, as shown in Figure5-32. Fill the X and Y values into the physical coordinates of the first line of “Edit Calibration Points” in the DobotVisionStudio software, respectively, as shown in Figure5-33. Follow the same operation to obtain the physical coordinate values of the remaining 8 points and fill them in the “Edit Calibration Points” table in the DobotVisionStudio software, as shown in Figure5-34.

Figure5-32 Locate the first calibration point

![Official Magician E6 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNhp42Ifoy40IfvuNZi0v%2Futp-894880f012ef2b3752d2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx94yxb9vPWfpD9KcIXBE%2Futp-9b3bbd2207eba9492ac5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx0qjwTvOiyBhJ258PWFH%2Futp-c25a86865998bba5b99c.png?alt=media)

Figure5-33 Fill in the physical coordinates of the first calibration point

Figure5-34 Physical coordinates of 9 calibration points

④Create calibration files. After editing the calibration points, the robot is moved

to a position that does not affect visual photography through jog control. Click (Once). Click **Basic Params** tab of **3N-point Calibration** . Click **Create Calibration File** to export the calibration file to local and name it, as shown in Figure5-35.

![Official Magician E6 training-system figure, source page 129](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvavAKIDaIlZnGdfMeNu5%2Futp-82026f23ad61cf09e1b7.png?alt=media)

![Official Magician E6 training-system figure, source page 129](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPSxMyzujIQNu52Fcxcrg%2Futp-417eec82e6e80abcd8de.png?alt=media)

Figure5-35 Create calibration file

* (7) Add **Calibration Transformation** in the flow.

①Verify whether the calibration is accurate. Drag **Calibration Transformation**

in **Calculation** toolbox to the flow editing area and connect it with **3N-point Calibration1** , as shown in Figure5-36.

Figure5-36 Flow

②Set **4Calibration Transformation1** parameters. In “Basic Params” page, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** , **Load Calibration File** to **Calibration file** generated from 3N-point Calibration1, as shown in Figure5-37.

![Official Magician E6 training-system figure, source page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVwEwlIrOqkXnDMNVpjPm%2Futp-8dfc5b1683f69d913a5b.png?alt=media)

Figure5-37 Set “4Calibration Transformation” parameters

③Click (Once) and check whether the nine coordinates after 4Calibration Transformation1 (as shown in Figure5-38) are consistent with the physical coordinates in 3N-point Calibration1. If the difference in values is very small, it indicates that the calibration is accurate. Otherwise, you need to re-calibrate.

Figure5-38 Compare Results

After the calibration is completed, it is necessary to remove the calibration needle

from the suction nozzle connecting rod and replace it with a suction nozzle.

![Official Magician E6 training-system figure, source page 131](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnYRiVeX96GJLzlRiUhtj%2Futp-9c13af414e9b584b0f5f.png?alt=media)

![Official Magician E6 training-system figure, source page 131](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ficf2IzFNid0avxfg8HzQ%2Futp-7abf529b053a764882d6.jpg?alt=media)

#### 3.2.2 Import vision program

Open DobotVisionStudio 4.1.2 and select **General Solution** . Select **Open** in the toolbar. Find the visual positioning guided assembly program and click **Open** . The imported vision program is shown in Figure5-39.

Figure5-39 Vision program

#### 3.2.3 Place phone chips

Place six chips within the detection vision, as shown in Figure5-40.

![Official Magician E6 training-system figure, source page 132](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbgHHcJp6EURCMZxyQpWG%2Futp-2665f436d73070216d40.png?alt=media)

**Application of the visual positioning** **guided assembly**

Figure5-40 Place chips within the detection view

#### 3.2.4 Debug parameters

* (1) Debug **0Image Source1** parameters.

Click (Once), select **0Image Source1** and observe whether the image is clear.

If the image is not clear or there is no image, you need to reset the parameters according to the method described in 3.2.1.

The image acquisition result is shown in Figure5-41.

Figure5-41 Image acquisition result

* (2) Debug **2Fast Match1** parameters.

![Official Magician E6 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdD7PAl3OebUXVpIkX0QL%2Futp-fa0e724f22ca00e86b6d.jpg?alt=media)

![Official Magician E6 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGf6lxDqWinCag7KnllAI%2Futp-3eb37d238b49aa32b12f.jpg?alt=media)

Click (Once). Select **2Fast Match1** and observe whether all types of chips can be recognized. If not, you need to modify “2Fast Match1” parameters, as described below.

Set Basic Params as shown in Figure5-42.

Figure5-42 Set “Basic Params”

Click **Feature Model** . Select the first feature model **hexagon** and click **Edit Model** , as shown in Figure5-43. In ModelSettings page, click **Current image** . Click **Create Rect Mask** and drag to generate the rectangular mask to cover the hexagonal material. Configure the parameters in the lower right corner. Set **Scale Mode** and **Thresh Mode** according to the actual condition. Click **Build Model** to generate the feature model, as shown in Figure5-44. Finally, click **Confirm** to save the feature model.

Figure5-43 Feature Model

![Official Magician E6 training-system figure, source page 134](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJZmJ6jN8pO0UUUPLpofn%2Futp-6498c02eb7d9bcc6e44a.png?alt=media)

![Official Magician E6 training-system figure, source page 134](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0TcVRj7r5z81rwNMnImt%2Futp-2902aa02584fbac85084.png?alt=media)

Figure5-44 Update feature model

Modify the feature models of GPS chip, electronic compass, gravity sensor, WIFI chip and photosensor following the method above.

Note: The model sequence must be consistent with Figure5-43 , which corresponds to the robot program.

* (3) Debug **3Calibration Transformation1** parameters.

Double-click **3Calibration Transformation1** to set parameters. In “Basic Params”

page, set **Coord Point** to **2 Fast Match1.Match Point\[]** , **Load Calibration File** to

**Calibration file** generated from N-point Calibration, as shown in Figure5-45.

Figure5-45 Set “3Calibration Transformation” parameters

![Official Magician E6 training-system figure, source page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCrrMf4jgoPU2mtCvhTXd%2Futp-e2b5ce8912fc3121847a.jpg?alt=media)

![Official Magician E6 training-system figure, source page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9TF1NLrOvsj23Vk5Q7us%2Futp-17efef61822b5520d99c.png?alt=media)

* (4) Debug **4Variable Calculation1** parameters.

Double-click **4Variable Calculation1** and check whether the **Expression** is “-<2 Fast Match1.MatchBoxAngle>\[0]”, as shown in Figure5-46. If not, modify it to “-<2 Fast Match1.MatchBoxAngle>\[0]”.

Figure5-46 Set “4Variable Calculation” parameters

(5) Debug **5Format1** parameters.

Double-click **5Format1** , and check whether the parameters are “<2 Fast Match1.MatchModelIndex(%0d)>\[0], <3 Calibration Transformation1.TransPointX (%1.3f)>\[0], <3 Calibration Transformation1.TransPointY(%1.3f)>\[0], <4 Variable Calculation1.var0(%1.3f)>\[0]”, as shown in Figure5-47. If not, modify it as the figure.

![Official Magician E6 training-system figure, source page 136](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcucUtIUZATOSgF4KZn9n%2Futp-cfe669dd14f1227da762.png?alt=media)

Figure5-47 Set “5Format1” parameters

(6) Debug **Communication Management** parameters.

Click in the toolbar to enter “Communication Management” page. Check whether there is created TCP Server. If not, you need to re-create one, as described

below. Click beside Device List. Set **Protocol Type** to **TCP Server** , **Load IP** to **192.168.5.18** , and **Local Port** to **4001** , as shown in Figure5-48. Then click **Create** . The TCP Server is shown in Figure5-49 . Switch on **1TCP Server** . If there is TCP Server, check whether its parameters are consistent with Figure5-49 . If not, modify as the figures.

![Official Magician E6 training-system figure, source page 137](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYufYaNBCSe5e9gVLddHO%2Futp-c53a51e837c032017f15.png?alt=media)

Figure5-48 Create TCP Server

Figure5-49 Set “Communication Management” parameters

(7) Debug **6Send Data1** parameters.

Double-click **6Send Data1** and check whether the parameters are shown as

Figure5-50. If not, modify as the figure. Set **Output To** to **Communication Device** ,

**Communication Device** to **1 TCP Server** , **SendData1** to **5Format.format\_out\[]** .

![Official Magician E6 training-system figure, source page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXyIixA19ng2GAJhwDhep%2Futp-b8406808f93ebfca314f.jpg?alt=media)

![Official Magician E6 training-system figure, source page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSgEqzEX14KXbWWGu9Ztc%2Futp-4c9ea76e4a8bf2d3000c.png?alt=media)

Figure5-50 Set “6Send Data” parameters

**(8) Debug Global trigger parameters.**

Click in the toolbar to enter “Global Trigger” page. In “String Trigger” page, check whether the string trigger setting is shown as Figure5-51. (String is void. Mode

is Mismatched. Trigger Configuration is All Process).

Figure5-51 Set “Global Trigger” parameters

#### 3.2.5 Save program

Click in the toolbar to save the program. If you need to save the program elsewhere on your local computer, click **File** > **Save as** , select the saving path and enter the name of the project.

#### 3.3 Debug robot program

#### 3.3.1 Import program

(1) On the Home screen of DobotStudio Pro software, click **Application > Script**

**programming** and enter “Programming ” interface, as shown in Figure5-52.

![Official Magician E6 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBVNdtwUAkJF2LIJVD4XC%2Futp-a22a6268b6e9c7616adc.png?alt=media)

![Official Magician E6 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhLTyetkPyLAl1tAnRUKE%2Futp-25a00bd0e40f766173af.png?alt=media)

Figure5-52 Enter “Programming ” interface

(2) Click to open File menu and select “Import project”, as shown in Figure5-53. Select **Mobile\_phone\_chip\_assembly** folder, and click **Open** . Now the visual positioning guided assembly program has been imported into DobotStudio Pro, as shown in Figure5-54.

Figure5-53 Import project

![Official Magician E6 training-system figure, source page 140](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOHGC48azPSIFZ1K00Ghe%2Futp-1f24392881c675820cef.jpg?alt=media)

![Official Magician E6 training-system figure, source page 140](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUbFBlj439vs9tUdCkkai%2Futp-cf36ed7c290c8cc831c6.png?alt=media)

Figure5-54 Project imported

#### 3.3.2 Save program

Click and enter a project name in the pop-up dialog box. Click **Save** , as

shown in Figure5-55.

Figure5-55 Save program

#### 3.3.3 Set communication

Ensure that the IP address and port of TCP server in the robot program are

![Official Magician E6 training-system figure, source page 141](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmbeQfzGvfSZSbiXVC0J4%2Futp-1bc09950500b5edbe702.png?alt=media)

![Official Magician E6 training-system figure, source page 141](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz5UOpdcKw9cYslJPmMQd%2Futp-a40772f5d7108c35fb22.png?alt=media)

consistent with those in vision communication settings, that is, set IP address in the

robot program to 192.168.5.18. Set port to 4001, as shown in Figure5-56.

Figure5-56 Set communication

#### 3.3.4 Modify Z coordinates

* (1) Modify Z coordinate of the picking point.

Jog the robot to make the suction cup slightly touch the surface of the chips, as shown in Figure5-57. Then read the current Z coordinate of the robot, as shown in Figure5-58. Modify the Z coordinate in the command “local GetProductPos = {pose = {move\_x, move\_y, 212.5,P1.pose\[4],P1.pose\[5], move\_r} }” in the chip pickup subprogram to the current Z coordinate.

Figure5-57 Locate the picking point

![Official Magician E6 training-system figure, source page 142](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F87STGn3Y6OM473fTCqJY%2Futp-eefa31befe24b8489a79.jpg?alt=media)

**Application of the visual positioning** **guided assembly**

Figure5-58 Z coordinate of picking point

(2) Modify Z coordinate over the picking point.

Jog the robot to lift some distance, as shown in Figure5-59. Then read the Z coordinate of the robot, as shown in Figure5-60. Modify the Z coordinate in the command “local GetProductPosUp = {pose = {move\_x, move\_y, 242.5, P1.pose\[4], P1.pose\[5], move\_r} }” in the chip pickup sub-program to the current Z coordinate. Click“ ”to save the program.

![Official Magician E6 training-system figure, source page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOLjHrOQb73wQf9SfQINF%2Futp-7d4c110ea81fb3721271.jpg?alt=media)

Figure5-59 Over picking point

Figure5-60 Z coordinate over picking point

![Official Magician E6 training-system figure, source page 144](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F28Uh3q1gErtLClHFyTwd%2Futp-ffbadcc3d78c89dad049.jpg?alt=media)

![Official Magician E6 training-system figure, source page 144](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0qQ1kk0OSdiSsazUQFoF%2Futp-65726ca572850aa7bac7.jpg?alt=media)

#### 3.3.5 Debug points

* (1) Update the safe point P1.

Jog the robot to a position between the conveyor belt and the storage area, as shown in Figure5-61. Click **Points** to enter the Points interface. Firstly select P1.Then click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P1 point,

as shown in Figure5-62. Click and save the program.

Figure5-61 Locate P1

Figure5-62 Update P1

Note: After updating each point, the program needs to be saved once.

* (2) Update the Hexagonal chip assembly point P2.
* Click to make the robot suck the hexagonal chip according to the

![Official Magician E6 training-system figure, source page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fl7EmjVw8pTL5Q44aeztx%2Futp-7f9be8db7952fda631dc.jpg?alt=media)

![Official Magician E6 training-system figure, source page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkOrE3kFLiPNeBkECS0tr%2Futp-b6b9af2bc61a656f5854.png?alt=media)

coordinates sent by the vision system. Then click immediately. Jog the robot to move the robot to the hexagonal chip assembly area, as shown in Figure5-63. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the hexagonal chip is placed into the groove accurately. If not, you need to re-debug the point.

Figure5-63 Locate Hexagonal chip assembly point P2

Select **P2** and click **Cover** in the Points interface. Then click **Cover** in the pop-up

Tips dialog box, as shown in Figure5-64. Click“ ”to save the program.

Figure5-64 Update P2

* (3) Update the GPS chip assembly point P3.

Click to make the robot suck the GPS chip according to the coordinates

![Official Magician E6 training-system figure, source page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8eLIFnTV1GkGlx5aFwJM%2Futp-2e5ddb1dfb09bf2fe43b.jpg?alt=media)

![Official Magician E6 training-system figure, source page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPzcR7tsEHmDfnKU6WDpZ%2Futp-de540062a3009b3f7573.jpg?alt=media)

sent by the vision system and click immediately. Jog the robot to move the robot to the GPS chip assembly point in the assembly area, as shown in Figure5-65. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the GPS chip is placed into the groove accurately. If not, you need to re-debug the point.

Figure5-65 Locate GPS chip assembly point P3

Select **P3** in **Points** page and click **Cover** in the Points interface. Then click **Cover** in the pop-up Tips dialog box, as shown in Figure5-66. Click“ ”to save the program.

Figure5-66 Update P3

* (4) Update the electronic compass chip assembly point P4.

![Official Magician E6 training-system figure, source page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4kvtRhXind1lRk22LBay%2Futp-830d4f9d7c2bced7078e.jpg?alt=media)

![Official Magician E6 training-system figure, source page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGS58aSJpKTPuWOTfhfps%2Futp-83a524c2f0bd5e74549f.jpg?alt=media)

Click to make the robot suck the electronic compass chip according to the coordinates sent by the vision system and click immediately. Jog the robot to move the robot to the electronic compass chip assembly point in the assembly area, as shown inFigure5-67. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the electronic compass

is placed into the groove accurately. If not, you need to re-debug the point.

Figure5-67 Locate Electronic compass chip assembly point P4

Select P4 in **Points** page and click **Cover** in the Points interface. Then click **Cover**

in the pop-up Tips dialog box, as shown in Figure5-68. Click“ ”to save the

program.

Figure5-68 Update P4

![Official Magician E6 training-system figure, source page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLs0aJGK1k0Ov83auOove%2Futp-18e85633f995fde7a8ba.jpg?alt=media)

![Official Magician E6 training-system figure, source page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsMw5nV5ZcB0RGHsSNUcf%2Futp-9c71d1a74b6b5b720f4d.jpg?alt=media)

* (5) Update the gravity sensor chip assembly point P5.

Click to make the robot suck the gravity sensor chip according to the coordinates sent by the vision system, and click immediately. Jog the robot to the gravity sensor chip assembly point in the assembly area, as shown in Figure5-69. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the gravity sensor chip is placed into the groove accurately. If not, you need to re-debug the point.

Figure5-69 Locate Gravity sensor chip

Select **P5** in **Points** page and click **Cover** in the points interface. Then click **Cover**

in the pop-up Tips dialog box, as shown in Figure5-70. Click “ ” to save the

program.

Figure5-70 Update P5

![Official Magician E6 training-system figure, source page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzDVKjtURtyUoLJdmfKVW%2Futp-7e3c128a95b80975bdf0.jpg?alt=media)

![Official Magician E6 training-system figure, source page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMngPJ80pW1Wvtj1UXhHN%2Futp-e9676358bcd304a4e787.jpg?alt=media)

(6) Update the WIFI chip assembly point P6. Click to make the robot suck the WIFI chip according to the coordinates

sent by the vision system and click immediately. Jog the robot to the WIFI chip assembly point in the assembly area, as shown in Figure5-71. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the WIFI chip is placed into the groove accurately. If not, you need to re-debug the point.

Figure5-71 Locate WIFI chip assembly point P6

Select **P6** in **Points** page and click **Cover** in the Points interface. Then click **Cover**

in the pop-up Tips dialog box, as shown in Figure5-72. Click “ ” to save the

program.

Figure5-72 Update P6

![Official Magician E6 training-system figure, source page 150](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrA09RS3wyfMjuS2yjqsP%2Futp-18bb63ce7f9460375df4.jpg?alt=media)

![Official Magician E6 training-system figure, source page 150](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6PY8sFCVtmQVwUTxEIE8%2Futp-dcdf8f3b96354c618842.jpg?alt=media)

(7) Update the photosensor chip assembly point P7.

Click to make the robot suck the photosensor chip according to the coordinates sent by the vision system and click immediately. Jog the robot to the photosensor chip assembly point in the assembly area, as shown in Figure5-73. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set **DO\_10** to **OFF** and observe whether the photosensor chip is placed into the groove accurately. If not, you need to re-debug the point.

Figure5-73 Locate Photosensor chip assembly point P7

Select **P7** in Points page and click **Cover** in the Points interface. Then click **Cover** in the pop-up Tips dialog box, as shown in Figure5-74. Click“ ”to save the

program.

Figure5-74 Update P7

Note1: For point debugging, please adjust the installation point of the chip based on the actual

![Official Magician E6 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvFpKXZ9LdIepnFzDpaeh%2Futp-0279f9991874d7d92363.jpg?alt=media)

![Official Magician E6 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7nWbfZKBRj4dqkQW6584%2Futp-51a631ae8f5ccf240899.jpg?alt=media)

phone base model.

#### 3.3.6 Run program

Place all the chips on the standard vision board. Open the vision program. Click in DobotStudio Pro. The program starts running. After receiving the chip coordinates sent by the vision system, the robot sucks the phone chips from the standard vision board and assembles them into the corresponding grooves of the phone models. The installed phone is shown in in Figure5-75.

Figure5-75 Installed phone

#### 3.3.7 Export program

Click to open File menu and select “Export project”. Select the path to save the program. Then enter a project name in the pop-up dialog box.

Note: Exporting a project refers to export the program to local for backup.

### 4. Key Program Description

#### 4.1 Vision program description

The vision program is shown in Figure5-76. **0Image Source1** is mainly used for image acquisition. During the running process of the system, once the vision software receives the trigger signal from the robot. The camera takes photos immediately. **2Fast Match1** is mainly used for positioning, in order to obtain the image coordinates and matching angle of the detected object. **3Calibration Transformation1** is used for transforming the image coordinates to the actual physical coordinates. **4Variable Calculation1** is used for correcting the matching angle. **5Format1** is used for

![Official Magician E6 training-system figure, source page 152](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVAjq8QvssFZh6KABVdfh%2Futp-24b9e675d412073f0c40.jpg?alt=media)

summarizing the information that the vision system needs to send to the robot and defining the format. **6Send Data1** is used for sending the 5Format1 content to the robot.

Figure5-76 Vision program

#### 4.2 Robot program description

#### 4.2.1 Character separation program

The character separation program is shown in Figure5-77.

Figure5-77 Character separation program

#### 4.2.2 Data transmission program

The data transmission program is shown in Figure5-78, which mainly sends

photography trigger signal “ok” and receives the data sent by the vision system.

![Official Magician E6 training-system figure, source page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6j3y2hQQlL5lgyHhCVeF%2Futp-4d24d6e9996c9f260e8e.png?alt=media)

Figure5-78 Data transmission program

#### 4.2.3 Robot pick-up program

The robot pick-up program is shown in Figure5-79. The function of the program is that the robot sucks the chips on the standard vision board according to the coordinates sent by the vision system.

Figure5-79 Robot pick-up program

#### 4.2.4 Output port reset program

The output port reset program is shown in Figure5-80, which sets all output ports

**to OFF .**

Figure5-80 Output port reset program

#### 4.2.5 Communication program

The communication program is shown in Figure5-81, which mainly creates TCP

client and establish connect with TCP server (vision).

![Official Magician E6 training-system figure, source page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FetqPRTW1qekNLCpAr0XS%2Futp-a97122835336e9312ed9.png?alt=media)

![Official Magician E6 training-system figure, source page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FinEfipVijDtal5iibz8r%2Futp-7ceccf2a2d261e731448.png?alt=media)

Figure5-81 Communication program

#### 4.2.6 Attitude adjustment program

The posture adjustment program is shown in Figure5-82, which implements the

function of adjusting the robot's posture to a vertical posture .

Figure5-82 Robot attitude adjustment program

#### 4.2.7 Robot assembly program

The robot assembly program is shown in Figure5-83. The function of the program is that the robot assembles the phone chips into the corresponding grooves of the phone

models according to the chip index sent by the vision system.

(1)Assemble the hexagonal chip

(2)Assemble the GPS positioning chip

![Official Magician E6 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq06nknsVr4jInny9qQEF%2Futp-07f7f688958539477d1a.png?alt=media)

![Official Magician E6 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm4vXoCOQVxCwnDkL3MzS%2Futp-6f7798e59041ba0e3bd1.png?alt=media)

![Official Magician E6 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp3C5zMGqqgTEZi30Y9Ik%2Futp-ec8071d687893d193a09.png?alt=media)

(3)Assemble the electronic compass chip<br>

(4)Assemble the gravity sensor chip\
(5)Assemble the WIFI chip<br>

(6)Assemble the photosensitive sensor chip

Figure5-83 Robot assembly program

![Official Magician E6 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FajvOTxHSlfbl1w7k4DmP%2Futp-9a8f689ac4bf025c8d71.png?alt=media)

![Official Magician E6 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjRn3SHYkM6KYB0B3VDIu%2Futp-02f2fd4729ef27500e6d.png?alt=media)

![Official Magician E6 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fi3pVQSs91MwgPPBe9ttV%2Futp-6a0fc6f8ca15174173f2.png?alt=media)

## Chapter 6 Application of Robot Handling

### 1. Introduction

The task that the robot handling application aims to achieve is to push 6 circular workpieces from the silo onto the conveyor belt through a pusher motor, and then the robot will transport the workpieces conveyed by the conveyor belt to the storage area. During the operation of the system, the device can be controlled to stop, reset, and start by pressing the buttons on the touch screen or the buttons on the control button box. At the same time, the operating status of the device can be feedback through the color of the tricolor light. The buttons on the control button box are shown in Figure6-1.

Figure6-1 Control Button Box

The specific task description is as follows:

The robot handling application project is controlled by buttons on the touch screen or buttons on the control button box, and there are two modes: manual control and automatic control. The manual control mode is mainly used for debugging, and can control the tricolor light, buzzer, pusher motor, and conveyor belt by pressing the buttons on the touch screen. In automatic control mode, the buttons on the touch screen or on the control button box control the stop, reset, and start of the system .

Firstly, the robot moves to the waiting point and sends a discharge signal to the PLC . After receiving the signal, PLC starts the pusher motor, which pushes the workpiece out of the cylindrical silo (as shown in Figure6-2). Then turn on the conveyor belt, which moves the workpiece forward. When the in place detection sensor detects that the workpiece has arrived, the PLC sends a material arrival signal to the robot. After receiving the signal, the robot takes the workpiece from the conveyor belt and transports it to the corresponding location in the storage area. This cycle is repeated 6

![Official Magician E6 training-system figure, source page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMfCIumOX1CyR1OP3bEbj%2Futp-6e04b7b3d4ee389c4bb0.jpg?alt=media)

times, and the robot moves the circular workpiece to the circular groove of the rectangular/circular workpiece loading plate in the storage area, arranged in a 3×2×1 array, as shown in Figure6-3.

Figure6-2 Cylindrical Silo

Figure6-3 Storage Area

### 2. **IO Configuration**

The Robot IO configuration of the Robot Handling is shown in Table6-1. The PLC IO configuration is shown in Table6-2. The HMI IO configuration is shown in Table63.

**Table6-1 Robot IO configuration**

| **DO** | \*\*Description \*\* |
| ------ | -------------------- |
| DO09   | Vacuum pumping       |

![Official Magician E6 training-system figure, source page 158](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIaKlvZjxWc5LyZGcAubu%2Futp-080603f5b63dbc69c0b9.jpg?alt=media)

![Official Magician E6 training-system figure, source page 158](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv1FWh5U9MOjOJWcFXYKm%2Futp-bb48ae9da0cbe1d04603.jpg?alt=media)

DO10 Vacuum breaking

**Table6-2 PLC IO configuration**

| **DI**                  | **Description**                                    | **DO**                   | **Description**    |
| ----------------------- | -------------------------------------------------- | ------------------------ | ------------------ |
| PL&#x43;**\_**&#x49;N01 | START                                              | PL&#x43;**\_**&#x4F;UT01 | Green light        |
| PL&#x43;**\_**&#x49;N02 | STOP                                               | PL&#x43;**\_**&#x4F;UT02 | Yellow light       |
| PL&#x43;**\_**&#x49;N03 | RESET                                              | PL&#x43;**\_**&#x4F;UT03 | Red light          |
| PL&#x43;**\_**&#x49;N04 | RESERVE                                            | PL&#x43;**\_**&#x4F;UT04 | Buzzer             |
| PL&#x43;**\_**&#x49;N05 | Material inspection in the silo                    | PL&#x43;**\_**&#x4F;UT05 | Pusher motor start |
| PL&#x43;**\_**&#x49;N06 | <p>Material inspection on the<br>conveyor belt</p> | PL&#x43;**\_**&#x4F;UT06 | Conveyor start     |

**Table6-3 HMI IO configuration**

| **DI**                  | <p><strong>Correspon-</strong><br><strong>dence</strong></p> | **Description**                           | **DO**                   | <p><strong>Correspon-</strong><br><strong>dence</strong></p> | **Description**                    |
| ----------------------- | ------------------------------------------------------------ | ----------------------------------------- | ------------------------ | ------------------------------------------------------------ | ---------------------------------- |
| PL&#x43;**\_**&#x49;N11 | R&#x31;**\_**&#x4F;UT11                                      | Robot readiness                           | PL&#x43;**\_**&#x4F;UT11 | R&#x31;**\_**&#x49;N11                                       | Robot start                        |
| PL&#x43;**\_**&#x49;N12 | R&#x31;**\_**&#x4F;UT12                                      | Robotpause status                         | PL&#x43;**\_**&#x4F;UT12 | R&#x31;**\_**&#x49;N12                                       | Robotpause                         |
| PL&#x43;**\_**&#x49;N13 | R&#x31;**\_**&#x4F;UT13                                      | <p>Robot operation<br>status</p>          | PL&#x43;**\_**&#x4F;UT13 | R&#x31;**\_**&#x49;N13                                       | Robot continue                     |
| PL&#x43;**\_**&#x49;N14 | R&#x31;**\_**&#x4F;UT14                                      | Robot alarm status                        | PL&#x43;**\_**&#x4F;UT14 | R&#x31;**\_**&#x49;N14                                       | Robot stop                         |
| PL&#x43;**\_**&#x49;N15 | R&#x31;**\_**&#x4F;UT15                                      | Robot interaction 1                       | PL&#x43;**\_**&#x4F;UT15 | R&#x31;**\_**&#x49;N15                                       | <p>Robot clear<br>alarm</p>        |
| PL&#x43;**\_**&#x49;N16 | R&#x31;**\_**&#x4F;UT16                                      | <p>Robot requests to<br>push material</p> | PL&#x43;**\_**&#x4F;UT16 | R&#x31;**\_**&#x49;N16                                       | <p>Robot materials<br>in place</p> |

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 3.1.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it

on, as shown in Figure6-4.

Figure6-4 Turn on the E6 power switch

![Official Magician E6 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to Auto, as

shown in Figure6-5.

Figure6-5 Turn on the power switch of the pump box

#### 3.1.4 Connect network cables

First, connect one end of a network cable to the LAN1 port of the robot and the other end to the upper network port of the PLC module box. Then, connect one end of a network cable to the lower network port of the PLC module box and the other end to the computer, as shown in Figure6-6.

Figure6-6 Connect network cables

#### 3.1.5 Modify IP of the PC

Open the control panel of the computer. Select **Network and Internet/Network**

**and Sharing Center** to enter the corresponding window. Click **Ethernet** and select

![Official Magician E6 training-system figure, source page 160](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIOo2VwMNtIqj3S5oUm1e%2Futp-fb05a14080aeb7630a08.jpg?alt=media)

![Official Magician E6 training-system figure, source page 160](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWryHC8s0w9vqYnt7NTpp%2Futp-c8aa8859d30b05358a50.jpg?alt=media)

**Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure6-7. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

Figure6-7 Set IP of the PC

#### 3.1.6 Connect DobotStudio Pro to the robot

Double-click **DobotStudio Pro** to open the software. After you enter DobotStudio Pro, the software will automatically search for robots and displays the search results “Magician E6” on the interface. Click **Connect** on the right side of the device to connect it, as shown in Figure6-8.

![Official Magician E6 training-system figure, source page 161](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDb5ccDkzTmqRU8BOmmx9%2Futp-ca3a257ba809811bdc70.png?alt=media)

Figure6-8 Connect robot

After successful connection, the software interface will refresh and display the

information about the E6 and its 3D model, as shown in Figure6-9.

Figure6-9 the information about the E6

#### 3.1.7 Enable robot

Click on the “Enable” switch in the “Magician E6” interface. Modify various parameter values according to the actual situation in the “Load enabling settings”

![Official Magician E6 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRujPrpBXi8viLdzRzUD4%2Futp-1436143103c7aa0204d7.png?alt=media)

![Official Magician E6 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

window that pops up. Click **Enable** , as shown in Figure6-10. The Enabling switch

changes to in the E6 interface.

Figure6-10 Set load parameters

#### 3.1.8 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to

set the speed to 35%, as shown in Figure6-11.

Figure6-11 Set Speed

#### 3.1.9 Install suction cup tool

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure6-12. It is best to adjust the coordinate value of J6 to 0°, as shown in

Figure6-13.

![Official Magician E6 training-system figure, source page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

Figure6-12 The posture of installing the end tool

Figure6-13 Coordinates for installing the end tool

(2) Install the Centre suction cup onto the end of the robot through four M3 \* 8 screws using an allen tool, as shown in Figure6-14.

![Official Magician E6 training-system figure, source page 164](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4YCH0hDYQtwlUfbycbrL%2Futp-66158be50749ed75a504.jpg?alt=media)

![Official Magician E6 training-system figure, source page 164](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGID1lJWubeuP8tsnZlsT%2Futp-b553235602b81b2845ed.jpg?alt=media)

Figure6-14 Install flange installation plate on the end of robot

(3) Connect one end of the air pipe to the “Air” hole in the air pump box, and the

other end to the suction cup. Fix it to the robot with a tie, as shown in Figure6-15.

Figure6-15 Connect the air pipe

#### 3.2 Download PLC program

* (1) Open **TIA Portal** software, as shown in Figure6-16.

![Official Magician E6 training-system figure, source page 165](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzcv41juFPW7siMzWaWqI%2Futp-17f289914692994ebfa2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 165](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsWyaiet443IAqncmvS7g%2Futp-f7f856a184ba52dfc609.jpg?alt=media)

Figure6-16 PLC software initial interface

(2) Select **Open Existing Project**  **Browse** and find the storage location of the PLC program . Select **PLC and HMI program. ap15\_1** and click **open** , as shown in Figure6-17.

Figure6-17 Open program

(3) Click **Project view Open the project view** . Open project view. Double click

on **Devices\&networks** to open the device and network interface . Click (Show address labels) and check if the IP addresses of the PLC, PLC expansion module, and the touch screen are in the 192.168.5. \* network segment , as shown in Figure6-18. Here, for example, the IP of PLC is set to “192.168.5.10”, the IP of the PLC expansion module is set to “192.168.5.11”, and the IP of HMI is set to “192.168.5.12”.

![Official Magician E6 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3VX7xuZbcGfaVtqfSVEJ%2Futp-0b59317d4d89686dc765.jpg?alt=media)

![Official Magician E6 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMQ4CCYuqsEVeQyLwJsmi%2Futp-f6a1828ebe2693df75f3.jpg?alt=media)

Figure6-18 Set “Devices\&networks” parameters

(4) Expand **PLC\_1\[CPU 1212C DC/DC/DC]** → **Program blocks** . Then double

click **Main\[OB1]** and view it , as shown in Figure6-19.

Figure6-19 Open main program

(5) Click **PLC\_1\[CPU 1212C DC/DC/DC]** . Click “

(download to device)”

on the tool bar. In the “Extended download to device” interface, select **Direct at slot '1X1** ' in the “connection to interface/subnet” column. Click **Start search** and select **PLC\_1** from the searched devices. Finally, click **Load** , as show in Figure6-20.

![Official Magician E6 training-system figure, source page 167](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FR4smfQGXHMKTnlNSgzAu%2Futp-d362943bb6a4a58274f8.png?alt=media)

![Official Magician E6 training-system figure, source page 167](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnluHBfd7qNQ4ja4Fn9vv%2Futp-3c363b4878c4eed1f0c3.png?alt=media)

Figure6-20 Set “Extend download to device” parameters

* (6) In the pop-up “Software synchronization before loading to a device” interface,

click **Continue without synchronization,** as show in Figure6-21.

Figure6-21 Set “Software synchronization before loading to a device”

* (7) In the pop-up “Load preview” interface, click **Load** , as shown in Figure6-22.

![Official Magician E6 training-system figure, source page 168](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRoRCa3vpS6Fm6wazWVQV%2Futp-1fff0dab19d2c5a22195.png?alt=media)

![Official Magician E6 training-system figure, source page 168](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXLZnLP3ANVS1JxLFFHmY%2Futp-48398c8a1c6392363e10.png?alt=media)

Figure6-22 Set “Load preview”

(8) In the pop-up “Load results” interface, click **Finish** , as shown in Figure6-23. After the download is completed, the message “Main was loaded successfully.” will appear at the bottom of the software interface, as shown in Figure6-24.

Figure6-23 Load results

![Official Magician E6 training-system figure, source page 169](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvGQltexOfRqpKmNffQ3x%2Futp-f54ca334f19932c88662.png?alt=media)

![Official Magician E6 training-system figure, source page 169](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxnYWWnwcA7ghmb5UJK4N%2Futp-be42b18f6c8e026d6c9e.png?alt=media)

Figure6-24 PLC program download

(9) Click “ ” on the tool bar , then program goes online. The PLC program in the device bar will display a green icon “ ”or “ ”，as shown in Figure625. This indicates that the PLC program has been successfully downloaded and can be debugged and monitored online.

Figure6-25 Online mode

#### 3.3 Download HMI program

(1) Expand “HMI 1 \[KTP700 Basic PN]→Screens” and check if the programs on each sub interface need to be downloaded to the HMI program on the touch screen, as shown in Figure6-26.

![Official Magician E6 training-system figure, source page 170](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWGgHQXMqVXltuzZwSqRQ%2Futp-e5b497648e6acf980683.png?alt=media)

![Official Magician E6 training-system figure, source page 170](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3U9CkFCSJE2iXQyjtVEr%2Futp-ddc2ff85167be93410bb.png?alt=media)

Figure6-26 View HMI Programs

(2) Click **HMI 1 \[KTP700 Basic PN]** . Click “ (download to device)” on the tool bar. In the “Extended download to device” interface, select **Direct at slot '1X1** ' in the “connection to interface/subnet” column. Click **Start search** and select **hmi\_1** from the searched devices . Finally, click **Load** ，as shown in Figure6-27.

Figure6-27 Set “Extend download to device” parameters

(3) In the pop-up “Load preview” interface, select “Overwrite all” of “Overwrite” parameter and then click **Load** , as shown in Figure6-28. After the download is completed, the message “Loading completed (errors: 0; warnings: 0)” will appear at the bottom of the software interface, as shown in Figure6-29.

![Official Magician E6 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBWWcESSyPWSkAIe9Utqa%2Futp-3070459eeea071f38eba.jpg?alt=media)

![Official Magician E6 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FviOh5wZee7BlNFzkOwKI%2Futp-a86f5aa12dfbef5fe2f7.jpg?alt=media)

Figure6-28 Set “load preview” parameters<br>

Figure6-29 HMI program download

(4) Click “ ”on the tool bar , then program goes online. The HMI program in the device bar will display a green icon “ ”or “ ”，as shown in Figure630. This indicates that the HMI program has been successfully downloaded and can be debugged and monitored online.

Figure6-30 Online mode

![Official Magician E6 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWczGmJuIeU31kRpeJlQS%2Futp-e208e2393d94e42eae9f.png?alt=media)

![Official Magician E6 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpkqywufKtDIPEe6S9hLs%2Futp-490a3c126bfa1b3ad437.png?alt=media)

![Official Magician E6 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ftg9uTE2TEZwN7PFaMHvq%2Futp-4bd5a7ba6bb95fcf4ab1.jpg?alt=media)

#### 3.4 Debug HMI and PLC program (Debug function of a single

#### button )

Observe whether the control buttons on the control box and touch screen are controlled as follows：

#### 3.4.1 Debug the function of the buttons in manual control mode

Switch the touch screen interface to the “Manual control” interface, as shown in

Figure6-31.

Figure6-31 “Manual control” interface

Press **Pusher motor starts** button and the pusher motor pushes out materials；

Press **Pusher motor starts** button again and the pusher motor stops pushing materials and returns to the initial position. Press **Conveyor starts** button and the conveyor belt operates. Press **Conveyor starts** again and the conveyor belt stops running .Press the **Green light** button and the green light turns on . Press the **Green light** button again and the green light turns off. Press the **Yellow light** button and the yellow light turns on. Press the **Yellow light** button again and the yellow light turns off. Press the **Red light** button and the red light turns on. Press the **Red light** button again and the red light turns off. Press the **Buzzer** button and the buzzer sounds. Press the **Buzzer** button again and the buzzer stops ringing.

![Official Magician E6 training-system figure, source page 173](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZljyNnawwwIpYWj7DfpO%2Futp-7d89512610e7943c2934.jpg?alt=media)

#### 3.4.2 Debug the function of the buttons in automatic control mode

Switch the touch screen interface to the “Automatic control” interface, as shown

in Figure6-32.

Figure6-32 “Automatic control” interface

In “Automatic control” interface, press the **STOP** button and the red light turns on.

Press the **RESET** button and the yellow light turns on. Press the **START** button and the green light turns on.

On the control button box, press the **STOP** button and the red light turns on. Press the **RESET** button and the yellow light turns on. Press the **START** button and the green light turns on.

During the debugging process, it is necessary to modify the PLC and touch screen programs when the operation result is observed to be inconsistent with the above.

#### 3.5 Debug Robot program

#### 3.5.1 Adjust the robot’s posture

Adjust the robot’s posture to a vertical position through the control panel, as shown

in Figure6-33, so that the joint coordinates are {0, 0, -90, 0, 90, 0}.

![Official Magician E6 training-system figure, source page 174](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC4f0yMuadcwRWaNXEqFJ%2Futp-3b64b7c00cd00200ccf6.jpg?alt=media)

Figure6-33 Adjust the robot's posture

#### 3.5.2 Import program

(1) On the Home screen of DobotStudio Pro software, click **Application > Script programming** and enter “Programming ” interface, as shown in Figure6-34.

Figure6-34 Enter “Programming ” interface

(2) Click to open File menu and select “Import project”, as shown in Figure6-35. Select **Robot\_Handling** folder, and click **Open** . Now the Robot\_Handling program has been imported into DobotStudio Pro, as shown in Figure6-36.

![Official Magician E6 training-system figure, source page 175](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fksw5YLQKKPrr3LO6R4x8%2Futp-90ab4ecf4d4d9d93ab9a.jpg?alt=media)

![Official Magician E6 training-system figure, source page 175](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfxaqYXx1qXsqZkCSbNwQ%2Futp-9ce18039fa2cccbd0017.jpg?alt=media)

Figure6-35 Import project

Figure6-36 Project imported

#### 3.5.3 Save program

Click and enter a project name in the pop-up dialog box. Click **Save** , as

shown in Figure6-37.

![Official Magician E6 training-system figure, source page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH9tJotY3Nq8TUmTcygay%2Futp-20d535c39930d845947a.png?alt=media)

![Official Magician E6 training-system figure, source page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRZ5OmwVjxmImE1DiYhYp%2Futp-8bc26a70b67203e4ed99.png?alt=media)

Figure6-37 Save program

#### 3.5.4 Debug points

The robot handling demo includes three major points, as described below.

* (1) Update the waiting point P1.

Jog the robot near the picking point, as shown in Figure6-38.

Figure6-38 Locate P1

②Click **Points** to enter the Points interface. Firstly select P1.Then click the tool

**Cover** . Finally click **Cover** in the pop-up tips again to update P1 point, as shown in

Figure6-39. Click and save the program.

![Official Magician E6 training-system figure, source page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEtLWar5sRKk60VifLVww%2Futp-d2790552a867757c1179.jpg?alt=media)

![Official Magician E6 training-system figure, source page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrGB0WdsQ2DsrxtcJfhkG%2Futp-b29cacca41d02920dea2.jpg?alt=media)

Application of Robot Handling<br>

Figure6-39 Update P1

(2) Update picking point P2.

①The material has arrived at the picking point. Firstly press the **STOP** button on the control button box, next press the **RESET** button, then press the **START** control

button, and finally click the in DobotStudio Pro to run the program.

②Jog the robot to the circular workpiece, and make the suction cup slightly touch

the surface of the workpiece, as shown in Figure6-40.

Figure6-40 Locate P2

③Open **Controller DI/DO** panel. Set **DO\_09** to **ON** to make the robot suck the

circular block, as shown in Figure6-41.

![Official Magician E6 training-system figure, source page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzdy0KnhL5SSZeEoxhDcV%2Futp-c5f16d5ccfda081448fa.jpg?alt=media)

![Official Magician E6 training-system figure, source page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzjtYxs4h9qF1JMiXh3ro%2Futp-ef6ee3eb111fcf7d60c8.jpg?alt=media)

Figure6-41 “Controller DI/DO” panel

* ④Open **Points** page. Select **P2** and click **Cover** , as shown in Figure6-42. Then

click Cover in the pop-up Tips dialog box. Click and save the program.<br>

Figure6-42 Update P2

* (3) Update placing point P3.
* ①Jog the robot to the first placing point, as shown in Figure6-43. Open **Controller**

![Official Magician E6 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6aSm9Uki5KWuAEW4jY3r%2Futp-8e4c5a37720579c4b9f6.jpg?alt=media)

![Official Magician E6 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHCJEcQwbMhgnGytxfGA%2Futp-929a5d64863a090849bc.png?alt=media)

**DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the circular workpiece is placed into the groove accurately.

If not, you need to re-debug the point.

Figure6-43 Locate the first placing point

②Open **Points** page. Select **P3** and click **Cover** , as shown in Figure6-44. Then

click **Cover** in the pop-up Tips dialog box. Click and save the program.

Figure6-44 Update P3

#### 3.6 System joint debugging in online operation mode

**3.6.1 Place the workpieces**

Place 6 cylindrical workpieces into the silo, as shown in Figure6-45.

![Official Magician E6 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHbqXKTNbxWcPbMD0dZZY%2Futp-e79329daa7235ae073b0.jpg?alt=media)

![Official Magician E6 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FY9sva4FYYAgF5MDEqyHa%2Futp-e0c28c691b64859ced85.png?alt=media)

Figure6-45 Place the workpieces

#### 3.6.2 Switch interface

Switch the touch screen interface to the **Automatic control** interface.

#### 3.6.3 Press the buttons

In the **Automatic control** interface, firstly press the **STOP** button, then press the **RESET** button, and finally press the **START** button . Alternatively, firstly press the **STOP** button of the control button box, then press the **RESET** button, and finally press the **START** button .

#### 3.6.4 Operate system

Open the robot program for the robot handling application project. Click . Observe whether the program runs as follows:

The robot moves to the waiting point, and the pusher motor starts to operate. The pusher motor pushes the workpiece out of the cylindrical silo . When the workpiece reaches the conveyor belt, the pusher motor retracts and stops pushing. The conveyor belt runs. The conveyor belt moves the workpiece forward, and when the workpiece reaches the sensor detection station, the conveyor belt stops running. The robot moves onto the conveyor belt to extract the workpiece and transports it to the corresponding location in the storage area. This cycle continues until all workpieces are transported to the storage area, as shown in Figure6-46.

![Official Magician E6 training-system figure, source page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu1DYJUlsXzglnzKRyw8a%2Futp-ca58857765573b8fa2a0.jpg?alt=media)

Figure6-46 Program running result

During operation, if inconsistencies are found, click , or press the **STOP**

button on the control button box, or the **STOP** button in the **Automatic control** interface. Then modify the robot program, PLC program, and HMI program according to the running status.

#### 3.7 System joint debugging in remote control mode

#### 3.7.1 Set Offline parameters

Click **Monitor** on the top toolbar of DobotStudio Pro to enter the default “Controller DI/DO” interface. Then click **Settings** , to enter the “IO settings” interface. In the “IO settings” interface, set “Function configuration” of DI\_11 to “Start”. Set “Function configuration” of DI\_12 to “Pause”. Set “Function configuration” of DI\_14 to “Stop”. Set “Function configuration” of DI\_15 to “Clear alarm”, as shown in Figure6-47.

![Official Magician E6 training-system figure, source page 182](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNXAfTpPuh8ywXkrX3tjx%2Futp-34f88c3abfae06cc6a06.jpg?alt=media)

Figure6-47 Set Offline parameters

Click **Select project** to enter the project selection interface and select **Run default**

**project** . Then click **Select** and select the **Robot\_Handling** program from the pop-up

drop-down menu. Finally, click **Save** , as shown in Figure6-48.

Figure6-48 Select project

![Official Magician E6 training-system figure, source page 183](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9ZlnWfgbnsQao2itwgEH%2Futp-ed635ed29eb50ab9e7b7.png?alt=media)

![Official Magician E6 training-system figure, source page 183](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD3pZgT0f2H88Kj4WZOgX%2Futp-87280eb32dd98b21e5ea.png?alt=media)

#### 3.7.2 Run program in automatic mode

Switch the touch screen interface to the **Automatic control** interface .

In the **Automatic control** interface of the touch screen, firstly press the **STOP** button, then press the **RESET** button, and finally press the **START** button. Alternatively, firstly press the **STOP** button of the control button box, then press the **RESET** button, and finally press the **START** button.

Observe whether the system runs as follows:

The robot moves to the waiting point, and the pusher motor starts to operate. The pusher motor pushes the workpiece out of the cylindrical silo. When the workpiece reaches the conveyor belt, the pusher motor retracts and stops pushing and the conveyor belt runs. The conveyor belt moves the workpiece forward, and when the workpiece reaches the sensor detection station, the conveyor belt stops running. The robot moves onto the conveyor belt to extract the workpiece and transports it to the corresponding location in the storage area. This cycle continues until all 6 workpieces are transported to the storage area.

During operation, if inconsistencies are found, press the **STOP** button on the control button box. Then modify the robot program, PLC program and HMI program according to the running status.

#### 3.8 Export program

Click to open File menu and select **Export project** . Select the path to save the program. Then enter a project name in the pop-up dialog box.

### 4. Key Program Description

This section mainly describes the key script. For complete script, see the project in Script page.

#### 4.1 PLC program description

#### 4.1.1 System control description

The system control has two modes: manual control and automatic control.

* (1) Control requirements in manual control mode.

In the manual control mode of the touch screen, press **Pusher motor starts** button and the pusher motor pushes out materials. Press **Conveyor starts** button and the conveyor belt runs . Press the **Green light** button and the green light turns on . Press the **Yellow light** button and the yellow light turns on . Press the **Red light** button and the red light turns on . Press the **Buzzer** button and the buzzer rings.

* (2) Control requirements in automatic control mode.

In the **Automatic control** interface of the touch screen , firstly press the **STOP** button, then press the **RESET** button, and finally press the **START** button. Alternatively, firstly press the **STOP** button of the control button box, then press the **RESET** button, and finally press the **START** button .

After receiving the discharge request from the robot, the PLC starts the pusher motor. When the workpiece is pushed out of the cylindrical silo, the pusher motor shuts down; Then the conveyor belt starts, and the conveyor belt moves the workpiece to the position where the robot absorbs the workpiece (with a material in place detection signal). The conveyor belt stops moving, and send a material in place signal to the robot.

#### 4.1.2 Main program (OB1)

Main (OB1) program is shown in Figure6-49.

(a) Automatic control

![Official Magician E6 training-system figure, source page 186](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6ZiCAWVgwotmgJeb0IVy%2Futp-1e97d808783e847ea09d.png?alt=media)

(b) Manual control<br>

(c) Robot control

Figure6-49 Main Program Sweep (Cycle)

![Official Magician E6 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQzM9tsAOrPmTvMXTqIaL%2Futp-cc808bf89ba499141633.png?alt=media)

![Official Magician E6 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fy9ns3hAB4yb7ah0TwDgA%2Futp-f18a87b847b3d4aadc38.png?alt=media)

#### 4.1.3 Automatic control program(FB1)

Automatic control program is shown in Figure6-50.

(a) Initialization status

(b) Device initialization

![Official Magician E6 training-system figure, source page 188](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiJuNQYP85eACWq46Kmdz%2Futp-a7be549804dddaee35dd.png?alt=media)

![Official Magician E6 training-system figure, source page 188](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwvGpHzwBLotZPDDKfpgP%2Futp-961ce38f64417c0161ea.png?alt=media)

(c) The device runs the process<br>

（d）Tricolor lamp<br>

Figure6-50 Automatic control program(FBI)

![Official Magician E6 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1dQ6ECf7fe5RMNqm3kM2%2Futp-d3d3d87f31c7a39d9e22.png?alt=media)

![Official Magician E6 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdUdz5ohhW9TfzePj1ggI%2Futp-49e80f857900baf78f48.png?alt=media)

#### 4.1.4 Manual control program (FC1)

Manual control program is shown in Figure6-51.

Figure6-51 Manual control program(FCI)

#### 4.1.5 Robot status control program (FC2)

Robot status control program is shown in Figure6-52.

![Official Magician E6 training-system figure, source page 190](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNbkEdoSf7gPX0p7rPlbW%2Futp-d44ae09dafa7e5e338fd.png?alt=media)

Figure6-52 Robot status control program(FC2)

#### 4.1.6 Automatic control data

Automatic control data is shown in Figure6-53.

Figure6-53 Automatic control data

#### 4.2 HMI program description

The touch screen interface needs to include four interfaces: Main interface,

Automatic control, Manual control and IO monitoring interface.

![Official Magician E6 training-system figure, source page 191](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQmalm3KzUsctXiaLHrV0%2Futp-30d53cff3cddb7a1f6ed.png?alt=media)

![Official Magician E6 training-system figure, source page 191](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYELcmAifBg4yPyJjD0ZZ%2Futp-b777f9932bb3d7da9f4e.png?alt=media)

#### 4.2.1 Main interface

In the Main interface, there are four buttons: “Main interface”, “Automatic control”, “Manual control”, “IO monitoring”, as shown in Figure6-54. You can enter the corresponding interface by pressing the corresponding button.

Figure6-54 Main interface

#### 4.2.2 Automatic control interface

In the Automatic control interface, there are three buttons: “START”, “STOP”, “RESET”, as shown in Figure6-55. When the system is running, press the **STOP** button to stop the system and the red light is on. Press the **RESET** button to reset all IO ports to the initial state and the yellow light is on. Press the **START** button to start the system and the green light is on.

![Official Magician E6 training-system figure, source page 192](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHt69gmSSDswmmVvSP5gR%2Futp-73da3d26408d3e58fe04.jpg?alt=media)

Figure6-55 Automatic control interface

**4.2.3 Manual control interface**

In the Manual control interface, there are six buttons: “Pusher motor starts”, “Conveyor starts”, “Green light”, “Yellow light”, “Red light”, “Buzzer”, as shown in Figure6-56.

Figure6-56 Manual control interface

![Official Magician E6 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKhORb1o1qxVLfjPHmfXn%2Futp-8d885863d0918802d5e0.png?alt=media)

![Official Magician E6 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZHSF8FgDASe234DbYbkY%2Futp-8de84730396a367f7ada.png?alt=media)

#### 4.2.4 IO monitoring interface

IO monitoring interface is shown in Figure6-57. Monitor the status of all input and

output ports. When the robot malfunctions and sends an alarm, the buzzer will sound.

Figure6-57 IO monitoring interface

#### 4.3 Robot program description

#### 4.3.1 Input signal detection program

The input signal detection program is shown in Figure6-58, which detects whether

there are input signals in IO port.

Figure6-58 Input signal detection program

Note: The input signal detection program is in the variable program.

#### 4.3.2 Robot pick-up program

The robot pick-up program is shown in Figure6-59. The function of the program

is to start the pusher motor when material is detected in the material slot, and the circular workpiece is pushed onto the conveyor belt . Then the conveyor belt starts. When the

![Official Magician E6 training-system figure, source page 194](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYJEhyPJeQmDcFnS2X8Ut%2Futp-2f4936de85f97e165d86.png?alt=media)

conveyor belt drives the workpiece to the material in place detection station, the

conveyor belt stops and the robot picks up material on the conveyor belt .

Figure6-59 Pick-up program

Note: The robot pick-up program is in the variable program.

#### 4.3.3 Initialization program

The initialization program is shown in Figure6-60, with all output ports set to 0.

Figure6-60 Initialization program

#### 4.3.4 Attitude adjustment program

The posture adjustment program is shown in Figure6-61, which implements the

function of adjusting the robot's posture to the posture shown in Figure6-62.

Figure6-61 Robot attitude adjustment program

![Official Magician E6 training-system figure, source page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHTaxly5I3eZQ4JCDKTC6%2Futp-b5f5ece6fbfd8396ca2b.png?alt=media)

Figure6-62 Robot attitude

#### 4.3.5 Robot placement program

The robot placement program is shown in Figure6-63, which controls the robot to

move to six placing points to place workpieces.

Figure6-63 Robot placement program

In line 29 and line 30 of the program, the first placing point P3 is the reference point for the other placing points. As the placing positions are fixed, the coordinates of the remaining five placing points are calculated based on the cycle times and the distance between point P3 and each placing point.

![Official Magician E6 training-system figure, source page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrsyCNhlggnD131BK5Ksr%2Futp-71f4121b0634a9ca52e5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvqQvGKkjOLMr5oQTQtDY%2Futp-33a9c8bedcef4b912009.png?alt=media)

## Appendix 1: Installation of Robot Software

**Step 1: Download the robot software installation package.**

Please download the latest DobotStudio Pro installation package from the official

website.

**Step 2: Enter installation guide interface.**

Double-click the downloaded software, and an installation guide interface will pop up. Select the installation language and click **Start Setup** , as shown in Appendix Figure1-1.

Appendix Figure1-1 Installaition guide

**Step 3: Select the installation path.**

Click **custom** . Click **Preview** in Custom options. Set the installation path, as

shown in Appendix Figure1-2.

![Official Magician E6 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqZszcd7fvXtf423ALIIs%2Futp-3f0df95b80c5796567bd.png?alt=media)

Appendix Figure1-2 Select installation path

**Step 4: Start installing.**

Click **One click installation** to start installing DobotStudio Pro, as shown in

Appendix Figure1-3.

Appendix Figure1-3 Installing software

![Official Magician E6 training-system figure, source page 198](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgffXfgkcdM2BwrbZ1nAF%2Futp-b2f502051a828b2ebb46.png?alt=media)

![Official Magician E6 training-system figure, source page 198](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFlt6GCW9gpEJQPDoYOtf%2Futp-f5a327c9e018fe197653.png?alt=media)

**Step 5: Finish installation.**

After installation, click **Experience Now** to enter the software, as shown in Appendix Figure1-4.

Appendix Figure1-4 Installation finished

**Step 6: Know about the software interface.**

The main interface mainly includes fourteen parts, as shown in Appendix Figure1-

5.

Appendix Figure1-5 Main interface

![Official Magician E6 training-system figure, source page 199](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2h5mS5SDDWezR2Uadd2I%2Futp-5be52a79ad52190e638a.jpg?alt=media)

![Official Magician E6 training-system figure, source page 199](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvGcTlUsWvYi0LRJhd5N1%2Futp-edcdc75f84997d01f597.jpg?alt=media)

①Click to open the main interface (current interface). The color of the robot arm icons changes according to the robot status. For detailed definition of the indicator

colors, see the corresponding hardware guide.

* ②Click to open Settings interface.
* ③Click to open Log interface.
* ④Click to open Dobot+ interface.
* ⑤Click to open Programming interface.
* ⑥Click to open help documents, which can be displayed in the software interface,

in a separate window or in a browser.

⑦Click to open Jog panel.

⑧Click to open Monitor panel.

⑨Display the current global speed rate. Drag the slider or click the speed bar to adjust the global speed rate. The global speed rate is the calculation factor of the robot actual running speed.

⑩Emergency stop switch. Press the button in an emergency, and robot arm will

stop running and be powered off.

⑪Robot information panel.

⑫Robot 3D model, with a posture consistent with the real robot.

⑬Software and firmware version information.

⑭Click to view the voltage, current and temperature of the robot.

Note: For specific functions of each tool, see its corresponding user guide.

## Appendix 2: Installation of Vision Related Software

### 1. Installation of vision software.

**Step 1: Enter Dobot official website.**

Search https://www.dobot-robots.com/ in the browser to enter Dobot website. Click **User** to enter “USER LOGIN” page. Enter your email and password to enter “USER CENTER” page as shown in Appendix Figure2-1. (You need to register before

login.)

Appendix Figure2-1 USER LOGIN

**Step 2: Download the latest vision software package.**

①Click **Download Center** in “USER CENTER” page, as shown in Appendix

Figure2-2.

Appendix Figure2-2 USER CENTER

![Official Magician E6 training-system figure, source page 201](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhW3JerdDtfUzzco6jScQ%2Futp-87e852542cfb0780856e.jpg?alt=media)

![Official Magician E6 training-system figure, source page 201](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC7YhIhSMAUALJiCUko2d%2Futp-80f4584534c1fc3e59a1.png?alt=media)

Click **Control Software** in “DOWNLOAD CENTER” page. Click on the right side of DobotVisionStudio v4.1.2 to download the vision software, as shown in Appendix Figure2-3.

Appendix Figure2-3 Download vision software package

**Step 3: Install vision software.**

Decompress the installation package and double-click **DobotVisionStudio**

**4.1.2.exe** to install it, as shown in Appendix Figure2-4.

Appendix Figure2-4 Vision installation file

**Step 4: Select a language.**

Select **English** , and click **OK** , as shown in Appendix Figure2-5.

Appendix Figure2-5 Select a language

**Step 5: Enter installation guide interface.**

Enter “Welcome to DobotVisionStudio4.1.2 Setup” page, and click **Next** . Install

the software according to the guide, as shown in Appendix Figure2-6.

![Official Magician E6 training-system figure, source page 202](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEbSpmNT7O7ekSq0sVpsL%2Futp-760ecfec932a64662a00.png?alt=media)

![Official Magician E6 training-system figure, source page 202](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8CMQqD493aHnfmwUGLtw%2Futp-24a948e307da623feb9a.png?alt=media)

Appendix Figure2-6 Welcome to DobotVisionStudio4.1.2 Setup

**Step 6: Choose Components.**

In “Choose Components” page, select **Hard Encryption** , **AlgorithmInstall** and

**CameraDriver** . Then click **Next,** as shown in Appendix Figure2-7.

Appendix Figure2-7 Choose Components

**Step 7: Choose Install Location.**

Click **Browse...** to define the installation path of the software. Then click **Install** ,

as shown in Appendix Figure2-8 and Appendix Figure2-9.

![Official Magician E6 training-system figure, source page 203](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNUDAeDEQfwuqLJ8Q9PJY%2Futp-e91c7bdeb79dbda555d5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 203](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft4fJob4CCG6c2e3xnyi9%2Futp-aa23979bc85c16299ec1.png?alt=media)

Appendix Figure2-8 Choose Install Location

Appendix Figure2-9 Installing

**Step 8: Finish installation.**

Select **Run DobotVisionStudio4.1.2** and click **Finish** to exit the installation, as

shown in Appendix Figure2-10.

![Official Magician E6 training-system figure, source page 204](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhXDhIxnpEXNRUSpG88Wo%2Futp-0e8487bbc32964408ec3.png?alt=media)

![Official Magician E6 training-system figure, source page 204](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ0H8VWbDWDJvQ8DZF38U%2Futp-f0708a1fc5b62b6345a6.png?alt=media)

<br>

Appendix Figure2-10 Installation finished

**Step 9: Know about the vision software interface.**

Open the software and select **General Solution** to enter the corresponding

software interface, as shown in Appendix Figure2-11.

Appendix Figure2-11 Main interface

Area 1: Menu Bar. It includes File, Settings, System, Tools and Help.

![Official Magician E6 training-system figure, source page 205](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp5UzAHvqp85f9UxxVC8S%2Futp-23c0e50705320f1d0bd0.jpg?alt=media)

![Official Magician E6 training-system figure, source page 205](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuNRYLyCNWAPdB6cccFaO%2Futp-73a1788edc7e6eabea0f.png?alt=media)

Area 2: Control Toolbar. It provides quick operations for the software, including file saving, file open, camera management, controller management, etc.

Area 3: Tool Box. It includes image collection, positioning, measurement, identification, calibration, position, image processing, color processing, defect detection, logic tools, communication, etc.

Area 4: Flow Toolbar. It provides quick operations for flows.

Area 5: Flow Process. You can edit the flow here.

Area 6: Overview. It provides an overview of the flow.

Area 7: Status. It displays flow time, tool time and algorithm time.

Area 8: Image. Image is displayed here.

Area 9: Results. You can view current results, history results and help information. Note: For specific functions of each tool, see its corresponding user guide.

### 2. Installation of camera MVS client software.

The industrial camera MVS client is a software application developed for debugging industrial cameras. It is applicable to GigE and USB3.0 interface industrial surface and line cameras, and supports real-time preview, parameter configuration, image capture and camera firmware upgrading. It is applicable to CameraLink interface industrial surface and line cameras, and supports parameter configuration and camera firmware upgrading.

**Step 1: Find MVS file.**

Double-click **MVS\_STD\_3.1.0\_181229.exe** in the installation package to install

it, as shown in Appendix Figure2-12.

Appendix Figure2-12 MVS installation file

**Step 2: Select a language.**

Accept the agreement, select a language, and click **Start Setup** , as shown in Appendix Figure2-13.

Appendix Figure2-13 Select language

**Step 3: Set installation options.**

Before installing the software, you need to set the installation path, set the driver, and select whether to enable built-in debug features and whether to enable Jumbo

Frames for all NICs. The default settings interface is shown in Appendix Figure2-14.

![Official Magician E6 training-system figure, source page 207](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvAJGsrz2ZsKOpSRvz2Ys%2Futp-b3e06cd8d53e18e125f6.jpg?alt=media)

![Official Magician E6 training-system figure, source page 207](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbujbDGvU6AX7rzBLw7Ia%2Futp-05564233659fadbce52f.jpg?alt=media)

Appendix Figure2-14 Options

**Step 4: Start installing.**

Confirm your settings and click **Next** . Then the software starts to be installed, as shown in Appendix Figure2-15.

Appendix Figure2-15 Installing

**Step 5: Finish installation.**

After installation, you can set whether to run the client and whether to open the

release note, as shown in Appendix Figure2-16.

![Official Magician E6 training-system figure, source page 208](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCDbbnNCYQ9DX5jx4mAhg%2Futp-404cef0b2415219f1128.jpg?alt=media)

Appendix Figure2-16 Installation finished

**Step 6: Know about the software interface.**

After opening the MVS software, you will see the main interface as shown in Appendix Figure2-17, which includes six parts.

Appendix Figure2-17 Main interface

![Official Magician E6 training-system figure, source page 209](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNu2lIqKCYhwl2qdx1l2Y%2Futp-ee8c1b094db94c47ea32.jpg?alt=media)

![Official Magician E6 training-system figure, source page 209](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ2wFIPquAt5xSqHH6FOD%2Futp-3b05690978790c003e67.png?alt=media)

Area 1: Menu Bar. Function modules including File, View, Settings, Tool and Help. Area 2: Control Toolbar.

Area 3: Display the GigE Vision cameras, USB3 Vision cameras and Camera Link cameras. Provide icons for connecting/disconnecting camera, start/stop acquisition, and refreshing device list.

Area 4: Interface and Device Information Panel. Display the network interface information and the device information.

Area 5: Display Window. View the live video of the selected camera.

Area 6: Feature Panel. View and configure features of the selected camera, and

perform other operations such as importing, exporting and saving features.

Note: For specific functions of each tool, see its corresponding user guide.

## Appendix 3: IO Testing Method for E6 General Training

## Platform (PLC Version)

### 1. IO Configuration

The Robot IO configuration of the E6 General Training Platform (PLC Version) is shown in Appendix Table3-1. The PLC IO configuration is shown in Appendix Table3-2. The HMI IO configuration is shown in Appendix Table3-3.

**Appendix Table3-1 Robot IO configuration**

| DO   | **Description** |
| ---- | --------------- |
| DO09 | Vacuum pumping  |
| DO10 | Vacuum breaking |

**Appendix Table3-2 PLC IO configuration**

| **DI**                  | **Description**                                    | **DO**                   | **Description**    |
| ----------------------- | -------------------------------------------------- | ------------------------ | ------------------ |
| PL&#x43;**\_**&#x49;N01 | START                                              | PL&#x43;**\_**&#x4F;UT01 | Green light        |
| PL&#x43;**\_**&#x49;N02 | STOP                                               | PL&#x43;**\_**&#x4F;UT02 | Yellow light       |
| PL&#x43;**\_**&#x49;N03 | RESET                                              | PL&#x43;**\_**&#x4F;UT03 | Red light          |
| PL&#x43;**\_**&#x49;N04 | RESERVE                                            | PL&#x43;**\_**&#x4F;UT04 | Buzzer             |
| PL&#x43;**\_**&#x49;N05 | Material inspection in the silo                    | PL&#x43;**\_**&#x4F;UT05 | Pusher motor start |
| PL&#x43;**\_**&#x49;N06 | <p>Material inspection on the<br>conveyor belt</p> | PL&#x43;**\_**&#x4F;UT06 | Conveyor start     |

**Appendix Table3-3 HMI IO configuration**

| **DI**                  | <p><strong>Correspon-</strong><br><strong>dence</strong></p> | **Description**                           | **DO**                   | <p><strong>Correspon-</strong><br><strong>dence</strong></p> | **Description**                    |
| ----------------------- | ------------------------------------------------------------ | ----------------------------------------- | ------------------------ | ------------------------------------------------------------ | ---------------------------------- |
| PL&#x43;**\_**&#x49;N11 | R&#x31;**\_**&#x4F;UT11                                      | Robot readiness                           | PL&#x43;**\_**&#x4F;UT11 | R&#x31;**\_**&#x49;N11                                       | Robot start                        |
| PL&#x43;**\_**&#x49;N12 | R&#x31;**\_**&#x4F;UT12                                      | Robotpause status                         | PL&#x43;**\_**&#x4F;UT12 | R&#x31;**\_**&#x49;N12                                       | Robotpause                         |
| PL&#x43;**\_**&#x49;N13 | R&#x31;**\_**&#x4F;UT13                                      | <p>Robot operation<br>status</p>          | PL&#x43;**\_**&#x4F;UT13 | R&#x31;**\_**&#x49;N13                                       | Robot continue                     |
| PL&#x43;**\_**&#x49;N14 | R&#x31;**\_**&#x4F;UT14                                      | Robot alarm status                        | PL&#x43;**\_**&#x4F;UT14 | R&#x31;**\_**&#x49;N14                                       | Robot stop                         |
| PL&#x43;**\_**&#x49;N15 | R&#x31;**\_**&#x4F;UT15                                      | Robot interaction 1                       | PL&#x43;**\_**&#x4F;UT15 | R&#x31;**\_**&#x49;N15                                       | <p>Robot clear<br>alarm</p>        |
| PL&#x43;**\_**&#x49;N16 | R&#x31;**\_**&#x4F;UT16                                      | <p>Robot requests to<br>push material</p> | PL&#x43;**\_**&#x4F;UT16 | R&#x31;**\_**&#x49;N16                                       | <p>Robot materials<br>in place</p> |

### 2. IO Testing Method

### 2.1 Preparation

#### 2.1.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 2.1.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it

on, as shown in Appendix Figure3-1.

Appendix Figure3-1 Turn on the E6 power switch

#### 2.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to **Auto** , as

shown in Appendix Figure3-2.

Appendix Figure3-2 Turn on Pump box power switch

#### 2.1.4 Install suction cup tool

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Appendix Figure3-3. It is best to adjust the coordinate value of J6 to 0°, as shown in Appendix Figure3-4.

![Official Magician E6 training-system figure, source page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBD28FcfXriGGieKA64D0%2Futp-12979b8ae7c529877839.jpg?alt=media)

![Official Magician E6 training-system figure, source page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMLuY8PZsXOomSjlxgjPw%2Futp-ea03dd125a359b391db0.jpg?alt=media)

Appendix Figure3-3 The posture of installing the end tool

Appendix Figure3-4 Coordinates for installing the end tool

(2) Install the suction cup onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Appendix Figure3-5.

![Official Magician E6 training-system figure, source page 213](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4YCH0hDYQtwlUfbycbrL%2Futp-66158be50749ed75a504.jpg?alt=media)

![Official Magician E6 training-system figure, source page 213](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGID1lJWubeuP8tsnZlsT%2Futp-b553235602b81b2845ed.jpg?alt=media)

Appendix Figure3-5 Install the suction cup on the end of robot

(3) Connect one end of the air pipe to the “Air” hole in the air pump box, and the

other end to the suction cup. Fix it to the robot with a tie, as shown in Appendix Figure36.

Appendix Figure3-6 Connect the air pipe

#### 2.1.5 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the

other end to the PC.

* (2) Modify IP of the computer.

Open the control panel of the computer. Select **Network and Internet/Network**

![Official Magician E6 training-system figure, source page 214](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzcv41juFPW7siMzWaWqI%2Futp-17f289914692994ebfa2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 214](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGHMloBxWCbCJ7Vzxmw3m%2Futp-748440c039c3f49da81b.jpg?alt=media)

**and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Appendix Figure3-7. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

Appendix Figure3-7 Set IP of the PC

(3) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro** to open the software. After you enter DobotStudio Pro, the software will automatically search for robots and displays the search results on the interface. Click **Connect** on the right side of the E6 to connect it, as shown in Appendix Figure3-8.

![Official Magician E6 training-system figure, source page 215](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfFW8rxCNQcXS2wrdDVKt%2Futp-8ffcc127698c75d5fef2.jpg?alt=media)

Appendix Figure3-8 Connect robot

After successful connection, the software interface will refresh and display the

information about the E6 and its 3D model, as shown in Appendix Figure3-9.

Appendix Figure3-9 Robot connected

#### 2.1.6 Enable robot

Click on the “Enable” switch of the “Magician E6” interface. Modify

various parameter values according to the actual situation in the “Load enabling settings” window that pops up. Click **Enable** , as shown in Appendix Figure3-10. The Enabling

![Official Magician E6 training-system figure, source page 216](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI52WALexkcCkcr0KRTBC%2Futp-0a5e0c0bd67c2bffac21.png?alt=media)

![Official Magician E6 training-system figure, source page 216](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

switch changes to

**in the E6 interface.**

Appendix Figure3-10 Set load parameters

#### 2.1.7 Download PLC program

* (1) Open **TIA Portal** software, as shown in Appendix Figure3-11.

Appendix Figure3-11 PLC software initial interface

(2) Select **Open Existing Project**  **Browse** and find the storage location of the PLC program . Select **PLC and HMI program. ap15\_1** and click **open** , as shown in Appendix Figure3-12.

![Official Magician E6 training-system figure, source page 217](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

![Official Magician E6 training-system figure, source page 217](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3VX7xuZbcGfaVtqfSVEJ%2Futp-0b59317d4d89686dc765.jpg?alt=media)

Appendix Figure3-12 Open program

(3) Click **Project view Open the project view** . Open project view. Double click

on **Devices\&networks** to open the device and network interface . Click (Show address labels) and check if the IP addresses of the PLC, PLC expansion module, and the touch screen are in the 192.168.5. \* network segment , as shown in Appendix Figure3-13. Here, for example, the IP of PLC is set to “192.168.5.10”, the IP of the PLC expansion module is set to “192.168.5.11”, and the IP of HMI is set to “192.168.5.12”.

Appendix Figure3-13 Set “Devices\&networks” parameters

* (4) Expand **PLC\_1\[CPU 1212C DC/DC/DC]** → **Program blocks** . Then double

click **Main\[OB1]** and view it , as shown in Appendix Figure3-14.

![Official Magician E6 training-system figure, source page 218](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMQ4CCYuqsEVeQyLwJsmi%2Futp-f6a1828ebe2693df75f3.jpg?alt=media)

![Official Magician E6 training-system figure, source page 218](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FR4smfQGXHMKTnlNSgzAu%2Futp-d362943bb6a4a58274f8.png?alt=media)

Appendix Figure3-14 View Main program

(5) Click **PLC\_1\[CPU 1212C DC/DC/DC]** . Click “ (download to device)”

on the tool bar. In the “Extended download to device” interface, select **Direct at slot '1X1** ' in the “connection to interface/subnet” column. Click **Start search** and select **PLC\_1** from the searched devices. Finally, click **Load** , as show in Appendix Figure315.

Appendix Figure3-15 Set “Extend download to device” parameters

(6) In the pop-up “Software synchronization before loading to a device” interface,

click **Continue without synchronization,** as show in Appendix Figure3-16.

![Official Magician E6 training-system figure, source page 219](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnluHBfd7qNQ4ja4Fn9vv%2Futp-3c363b4878c4eed1f0c3.png?alt=media)

![Official Magician E6 training-system figure, source page 219](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRoRCa3vpS6Fm6wazWVQV%2Futp-1fff0dab19d2c5a22195.png?alt=media)

Appendix Figure3-16 Set “Software synchronization before loading to a device”

(7) In the pop-up “Load preview” interface, click **Load** , as shown in Appendix Figure3-17.

Appendix Figure3-17 Set “Load preview”

(8) In the pop-up “Load results” interface, click **Finish** , as shown in Appendix Figure3-18. After the download is completed, the message “Main was loaded successfully.” will appear at the bottom of the software interface, as shown in Appendix Figure3-19.

![Official Magician E6 training-system figure, source page 220](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXLZnLP3ANVS1JxLFFHmY%2Futp-48398c8a1c6392363e10.png?alt=media)

![Official Magician E6 training-system figure, source page 220](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvGQltexOfRqpKmNffQ3x%2Futp-f54ca334f19932c88662.png?alt=media)

Appendix Figure3-18 Load results<br>

Appendix Figure3-19 PLC program download

(9) Click “ ” on the tool bar , then program goes online. The PLC program in the device bar will display a green icon “ ”or “ ”，as shown in Appendix Figure3-20. This indicates that the PLC program has been successfully downloaded and can be debugged and monitored online.

![Official Magician E6 training-system figure, source page 221](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxnYWWnwcA7ghmb5UJK4N%2Futp-be42b18f6c8e026d6c9e.png?alt=media)

![Official Magician E6 training-system figure, source page 221](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWGgHQXMqVXltuzZwSqRQ%2Futp-e5b497648e6acf980683.png?alt=media)

Appendix Figure3-20 Online mode

#### 2.1.8 Download HMI program

(1) Expand “ **HMI 1 \[KTP700 Basic PN]** → **Screens** ” and check if the programs

on each sub interface need to be downloaded to the HMI program on the touch screen, as shown in Appendix Figure3-21.

Appendix Figure3-21 View HMI Program

(2) Click **HMI 1 \[KTP700 Basic PN]** . Click “

(download to device)” on the

tool bar. In the “Extended download to device” interface, select **Direct at slot '1X1** ' in the “connection to interface/subnet” column. Click **Start search** and select **hmi\_1** from the searched devices . Finally, click **Load** ，as shown in Appendix Figure3-22.

![Official Magician E6 training-system figure, source page 222](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3U9CkFCSJE2iXQyjtVEr%2Futp-ddc2ff85167be93410bb.png?alt=media)

![Official Magician E6 training-system figure, source page 222](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBWWcESSyPWSkAIe9Utqa%2Futp-3070459eeea071f38eba.jpg?alt=media)

Appendix Figure3-22 Set “Extend download to device” parameters

(3) In the pop-up “Load preview” interface, select “Overwrite all” of “Overwrite” parameter and then click **Load** , as shown in Appendix Figure3-23. After the download is completed, the message “Loading completed (errors: 0; warnings: 0)” will appear at the bottom of the software interface, as shown in Appendix Figure3-24.

Appendix Figure3-23 Set “load preview” parameters

Appendix Figure3-24 HMI program download

![Official Magician E6 training-system figure, source page 223](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FviOh5wZee7BlNFzkOwKI%2Futp-a86f5aa12dfbef5fe2f7.jpg?alt=media)

![Official Magician E6 training-system figure, source page 223](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWczGmJuIeU31kRpeJlQS%2Futp-e208e2393d94e42eae9f.png?alt=media)

(4) Click “ ”on the tool bar, then program goes online. The HMI program in the device bar will display a green icon “ ”or “ ”，as shown in Appendix Figure3-25. This indicates that the HMI program can be debugged and monitored online.

Appendix Figure3-25 Online mode

#### 2.2 IO Test Method

#### 2.2.1 Enter the "Monitor" interface

Click **Monitor** on the top-level toolbar of DobotStudio Pro to enter the default

“Controller DI/DO” interface, as shown in Appendix Figure3-26.

![Official Magician E6 training-system figure, source page 224](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ftg9uTE2TEZwN7PFaMHvq%2Futp-4bd5a7ba6bb95fcf4ab1.jpg?alt=media)

![Official Magician E6 training-system figure, source page 224](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSZfkJhE1K3lmevsHkUh3%2Futp-e3ebb356c79e19e20afb.jpg?alt=media)

**Appendix Figure3-26 “Controller DI/DO” interface**

#### 2.2.2 Inspiratory control (DO\_9) port test

Set the “Status” of “DO\_9” in the DO column to “ON”, as shown in Appendix Figure3-27. Place your finger under the suction cup and feel if the suction cup is inhaling, as shown in Appendix Figure3-28. If the suction cup does not inhale, it indicates that there is a problem with the circuit of “DO\_9” and it needs to be investigated.

Appendix Figure3-27 DO\_9 Port Status

Appendix Figure3-28 Finger placement position

![Official Magician E6 training-system figure, source page 225](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYjWnJCmvb68zIEMK9KRZ%2Futp-68c43116661f0dfc79de.jpg?alt=media)

![Official Magician E6 training-system figure, source page 225](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcGkfons7xPoOB7gKmZbj%2Futp-b5ae5d138e2609995c2c.png?alt=media)

#### 2.2.3 Blowing control (DO\_10) port test

Set the “Status” of “DO\_10” in the DO column to “ON”, as shown in Appendix Figure3-29. Place your finger under the suction cup and feel if the suction cup is blowing. If the suction cup does not below, it indicates that there is a problem with the circuit of “DO\_10” and it needs to be investigated.

Appendix Figure3-29 DO\_10 Port Status

#### 2.3 PLC/HMI Input IO Testing Method

#### 2.3.1 Switch the touch screen interface to the IO monitoring interface

Click the “IO monitoring” button on the touch screen interface to the **IO**

**monitoring interface** , as shown in Appendix Figure3-30.

![Official Magician E6 training-system figure, source page 226](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBLlZpR1s1diFGqTXZSUq%2Futp-2044ae1c444bbf860054.jpg?alt=media)

Appendix Figure3-30 IO monitoring interface

**2.3.2 Test of “ STOP ” button status**

Press the “STOP” button on the button box (as shown in Appendix Figure3-31) and the red light will turn on, as shown in Appendix Figure3-32. The status indicator lights for “STOP”, “Red light”, “ROB stops” on the IO monitoring interface will turn blue, as shown in Appendix Figure3-33. If the status indicator light does not turn blue or the red light does not light up, it indicates a problem with the circuit of the control button box “STOP” and needs to be investigated.

Appendix Figure3-31 the control button box

![Official Magician E6 training-system figure, source page 227](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPIm4avePSeL3QaR19A3k%2Futp-46f0a90b6ce1b4af3284.jpg?alt=media)

![Official Magician E6 training-system figure, source page 227](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpiFgvphhemC1FaW7GPRv%2Futp-20c4b496921855508f25.jpg?alt=media)

Appendix Figure3-32 Red light on

Appendix Figure3-33 “STOP” status of the IO monitoring interface

**2.3.3 Test of** “ **RESET** ” **button status**

Press the “RESET” button on the button box, and the yellow light will turn on, as shown in Appendix Figure3-34. The status indicator lights for “RESET”, “Yellow light”, “ROB clears the alarm” on the IO monitoring interface will turn blue, as shown in Appendix Figure3-35. If the status indicator light does not turn blue or the yellow light does not light up, it indicates a problem with the circuit of the control button box “RESET” and needs to be investigated.

![Official Magician E6 training-system figure, source page 228](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtcWK4ikWvPKAfOYYbe7e%2Futp-b5ef673145bf04a7a626.jpg?alt=media)

![Official Magician E6 training-system figure, source page 228](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRpHKAKHijH2LsH6wbjaA%2Futp-f40a46c7f28625e6a9b1.jpg?alt=media)

Appendix Figure3-34 Yellow light on

Appendix Figure3-35 “RESET” status of the IO monitoring interface

#### 2.3.4 Test of “START” button status

Press the “START” button on the button box, and the green light will turn on, as shown in Appendix Figure3-36. The status indicator lights for “START”, “Green light”, “ROB Interaction1”, “ROB initiate” and “Obligate” on the IO monitoring interface will turn blue, as shown in Appendix Figure3-37. If the status indicator light does not turn

![Official Magician E6 training-system figure, source page 229](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTuU2mIBSNnOsdyPxQt3B%2Futp-5fd99a014247771383a9.jpg?alt=media)

![Official Magician E6 training-system figure, source page 229](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fo1DYR7shTSijQBozpHN3%2Futp-a397a208917929fc62bf.jpg?alt=media)

blue or the green light does not light up, it indicates a problem with the circuit of the

control button box “START” and needs to be investigated.

Appendix Figure3-36 Green light on

Appendix Figure3-37 “START” status of the IO monitoring interface

#### 2.3.5 Test of material status in the silo

Place a cylindrical workpiece into the silo, as shown in Appendix Figure3-38 and the status indicator light of “Stock bin has blocks” on the IO monitoring interface turns blue, as shown in Appendix Figure3-39. If it does not turn blue, it is necessary to investigate the circuit problem or adjust the sensitivity of the sensor again.

![Official Magician E6 training-system figure, source page 230](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQJT5BC9lE1RaxtYDReyR%2Futp-d16e063bbe45ea001659.jpg?alt=media)

![Official Magician E6 training-system figure, source page 230](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FExRyM4CjwRadceFKkqln%2Futp-7cd5ed93b4ce83cc3af8.jpg?alt=media)

Appendix Figure3-38 Place a cylindrical workpiece

Appendix Figure3-39 “Silo material” status of IO monitoring interface

#### 2.3.6 Test of material in place inspection

Place a cylindrical workpiece in place, as shown in Appendix Figure3-40 and the status indicator light of “Belt material inspection” on the IO monitoring interface turns blue, as shown in Appendix Figure3-41. If it does not turn blue, it indicates that there is a problem or insufficient sensitivity in the circuit of the sensor for detecting whether the material is in place. It is necessary to investigate the circuit problem or adjust the sensitivity of the sensor again.

![Official Magician E6 training-system figure, source page 231](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOgoXJdjjbYFSvrmaO4yP%2Futp-5cda110fb511bfb183f8.jpg?alt=media)

![Official Magician E6 training-system figure, source page 231](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0uWKQUM1sBWqY5MDUagO%2Futp-015188bf5dc1490fd5e0.jpg?alt=media)

Appendix Figure3-40 Workpiece in place

Appendix Figure3-41 “Material in place inspection” status of IO monitoring interface

#### 2.4 PLC/HMI Output IO Test Method

#### 2.4.1 Switch the touch screen interface to the manual control interface

Click the “Manual control” button on the touch screen interface to switch the touch

screen interface to the manual control interface,

#### 2.4.2 Test of pusher motor control

Place a cylindrical workpiece into the silo. Observe the movement of the pusher motor. Press the “Pusher motor starts” button on the Manual control interface (as shown in Appendix Figure3-42), the pusher motor can push the circular workpiece onto the conveyor belt. Press the "Pusher motor starts" button again to retract the push rod of the pusher motor. If not, it indicates that there is a problem with the control circuit of the pusher motor, and the circuit problem needs to be investigated.

![Official Magician E6 training-system figure, source page 232](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIfxEPRaaqOtAGkpbKzrh%2Futp-09be34b2fd6325a01784.jpg?alt=media)

![Official Magician E6 training-system figure, source page 232](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVhu2QQNvZpqusFVwsg9V%2Futp-7d4019947b299b67a0fe.jpg?alt=media)

Appendix Figure3-42 “Pusher motor starts” button

#### 2.4.3 Test of conveyor belt control

Observe the movement of the conveyor belt. Press the “Conveyor starts” button on the Manual control interface (as shown in Appendix Figure3-43). The conveyor belt moves forward. Press the “Conveyor starts” button again to stop the conveyor belt from moving. If not, it indicates that there is a problem with the conveyor belt control circuit and the circuit needs to be investigated.

Appendix Figure3-43 “Conveyor starts” button

![Official Magician E6 training-system figure, source page 233](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM5VS9pq52AJq2dXW24pF%2Futp-e7055d58fc2a3f057a01.jpg?alt=media)

![Official Magician E6 training-system figure, source page 233](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPogG2onI6PQ4l8NgAU3t%2Futp-c93908a5c18d5dd558cb.jpg?alt=media)

#### 2.4.4 Test of green light control

Observe if the phenomenon is as follows: Press the “Green light” button on the manual control interface, as shown in Appendix Figure3-44, and the green light will turn on, as shown in Appendix Figure3-45. Press the “Green light” button again, and the green light will turn off. If not, it indicates that there is a problem with the green light circuit and it is necessary to investigate the circuit problem.

Appendix Figure3-44 “Green light” button

Appendix Figure3-45 Green light on

![Official Magician E6 training-system figure, source page 234](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD4wjJzhXJgCOhZs7MgGy%2Futp-786dde658c5eb6c5f725.jpg?alt=media)

![Official Magician E6 training-system figure, source page 234](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlFmr8eMlWLc2iWtfb1df%2Futp-fa411f6e8b639d296edf.jpg?alt=media)

#### 2.4.5 Test of yellow light control

Observe if the phenomenon is as follows: Press the “Yellow light” button on the manual control interface, as shown in Appendix Figure3-46, and the yellow light will turn on , as shown in Appendix Figure3-47; Press the “Yellow light” button again, and the yellow light will turn off. If not, it indicates that there is a problem with the yellow light circuit and it is necessary to investigate the circuit problem.

Appendix Figure3-46 “Yellow light” button

Appendix Figure3-47 Yellow light on

![Official Magician E6 training-system figure, source page 235](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK3IqNCkCurf3XG5MWUf0%2Futp-536d53ff7f77d44eee09.jpg?alt=media)

![Official Magician E6 training-system figure, source page 235](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhlNocbxWFWYq05FUTkLD%2Futp-90ef286f56e88338006d.jpg?alt=media)

#### 2.4.6 Test of red light control

Observe if the phenomenon is as follows: Press the “Red light” button on the manual control interface, as shown in Appendix Figure3-48, and the red light will turn on , as shown in Appendix Figure3-49. Press the “Red light” button again, and the red light will turn off. If not, it indicates that there is a problem with the red light circuit and it is necessary to investigate the circuit problem.

Appendix Figure3-48 “Red light” button

Appendix Figure3-49 Red light on

![Official Magician E6 training-system figure, source page 236](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLrfD7qUpjKUsifOh2kAJ%2Futp-072a962193cfd04b7b1c.jpg?alt=media)

![Official Magician E6 training-system figure, source page 236](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FptzPY8dwcROYpTpZbJvx%2Futp-e37c764f4322094e0e3d.jpg?alt=media)

#### 2.4.7 Test of Buzzer control

Observe if the phenomenon is as follows: Press the “Buzzer” button on the manual control interface (as shown in Appendix Figure3-50), the buzzer will ring. Press the “Buzzer” button again and the buzzer will stop ring. If not, it indicates a problem with the circuit of the buzzer and requires troubleshooting.

Appendix Figure3-50 “Buzzer” button

Note: The buzzer is integrated into the tricolor light.

![Official Magician E6 training-system figure, source page 237](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJT4chBMVtC7B2pAjMTaO%2Futp-fd02592eb713555bcec6.jpg?alt=media)

## Official source and related installation guides

The complete English source is in the [official DOBOT Universal Training Platform operation-instruction archive](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260722/1770703893557_Collaborative%20Robot%20Universal%20Training%20Platform%20Operation%20Instruction-EN.rar). Select file `06-Collaborative Robot Universal Training Platform (Magician E6 _include PLC)_20260211_en.pdf`. The archive also contains the platform installation, emergency-stop wiring, conveyor, and PLC-upgrade guides.
