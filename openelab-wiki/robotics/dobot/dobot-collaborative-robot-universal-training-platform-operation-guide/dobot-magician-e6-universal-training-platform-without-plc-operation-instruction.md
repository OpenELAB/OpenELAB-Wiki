# DOBOT Magician E6 Universal Training Platform Operation Instruction - Without PLC

## DOBOT Collaborative Robot Universal Training Platform - Without PLC System Module

{% embed url="https://openelab.io/products/dobot-cobot-universal-training-platform?variant=46636171395270" %}

**Applies to:** Magician E6 training system without the PLC system module. Official source issue V1.0 (2023-08-02). The robot is purchased separately. Confirm the actual robot and PLC configuration before following wiring or software steps.

**Copyright © Shenzhen Yuejiang Technology Co., Ltd. 2023. All rights reserved.** No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of Yuejiang Technology Co., Ltd.

**Disclaimer** To the maximum extent permitted by applicable law, the products described (including its hardware, software, and firmware, etc.) in this document are provided **AS IS** , which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents.

Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses will be happening in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document.

The user has the responsibility to make sure of following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot.

Shenzhen Yuejiang Technology Co., Ltd. Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China

Website: www.dobot.cc

### Preface

### Purpose

This document introduces the installation procedure and some operation demos (including tricolor light, trajectory simulation, static palletizing, robot handling, visual sorting, visual positioning guided assembly) of the Magician E6 training system, which is convenient for users to understand and use the Magician E6 training system.

### Note

In this document, DobotStudio Pro 4.1 is used for robot control software and DobotVisionStudio 4.1.2 is used for vision software.

### Symbol Conventions

The symbols that may be found in this document are defined as follows.

| Symbol  | Description                                                                                                                                                                    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DANGER  | <p>Indicates a hazard with a high level of risk which, if not avoided, could<br>result in death or serious injury.</p>                                                         |
| WARNING | <p>Indicates a hazard with a medium level or low level of risk which, if not<br>avoided, could result in minor or moderate personal injury and damage to<br>the equipment.</p> |
| NOTICE  | <p>Indicates a potentially hazardous situation which, if not avoided, can result<br>in damage to the equipment, data loss, or unanticipated result.</p>                        |
| NOTE   | <p>Provides additional information to emphasize or supplement important<br>points in the main text.</p>                                                                        |

## Chapter 1 Magician E6 Training System Overview

### 1. Safety Precautions

This section describes the safety precautions that should be noticed when you use this product. Please read this section carefully before using the training system for the first time. This product needs to be used in an environment meeting the design specifications. You cannot remold the product without authorization, otherwise, it may lead to product failure, and even personal injury, electric shock, fire, etc. People who use this product for system design and manufacture must be trained by Dobot or relevant institutions, or must have the same professional skills, and use the training system strictly following the regulations of this document.

#### 1.1 Safety warning signs

The following safety warning signs may appear in this document, and their meanings are described as follows , as shown in Table1-1.

**Table1-1 Safety warning signs**

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
* Machine vision coloured object recognition
* Machine vision mobile phone assembly

Figure1-1 E6 training system

### 3. Layout Introduction

#### 3.1 Structural layout

The E6 general training platform is composed of E6 industrial six axis robot unit, visual unit, feeding and transmission unit, mini air pump box, quick change board unit, tool box unit, etc , as shown in Figure1-2.

![Official Magician E6 training-system figure, source page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPXslPPpvwV3M2Jcm39kQ%2Futp-970ccecc40e06be3e57e.jpg?alt=media)

Figure1-2 Structural layout

#### 3.2 E6 training platform core unit

#### 3.2.1 Robot Unit

The E6 robot is a six axis collaborative robot for teaching and research, which adopts an integrated design and the controller is placed in the base. It can be paired with a training platform for robot practical teaching.

Equipped with special security mechanisms including collision detection. It is flexible and easy to deploy, easy to use, and secure collaboration. E6 can receive signals from visual units, execute corresponding robot commands, and complete corresponding actions.

* (1) Robot composition

E6 robot, as shown in Figure1-3, includes a base, 6 rotating motion joints, and two connecting rods (upper arm and forearm), with an aviation socket on the side of its end flange.

![Official Magician E6 training-system figure, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWsBKioKcI19jf6IRMENW%2Futp-de6a8cde40ed9d1c4717.jpg?alt=media)

Figure1-3 E6 composition

**(2) Indicator lights**

The E6 robot is equipped with a circle of status indicators near the J1 and J6 joints,

with the meanings described below, as shown in Table1-2.

**Table1-2 Indicator lights**

| Colour       | Status      | Definition                                                                                                                |
| ------------ | ----------- | ------------------------------------------------------------------------------------------------------------------------- |
| Bl liht      | Steady on   | The robot arm has been started but not enabled.                                                                           |
| ue g         | Quick flash | The robot arm is starting.                                                                                                |
|              | Steady on   | The robot arm is enabled (not running).                                                                                   |
| Green light  | Slow flash  | <p>Automatic running status(project debugging/running/pause, TCP<br>motion commands except jog, trajectory playback).</p> |
|              | Quick flash | <p>Single<br>running<br>status(jog/<br>run<br>to<br>in<br>software)/drag<br>mode/trajectory recording status.</p>         |
| Rd lih       | Slow flash  | Joint brake switched on in disable status.                                                                                |
| e gt         | Steady on   | Alarm status                                                                                                              |
| Yellow light | Steady on   | Collision detected                                                                                                        |

**(3) Buttons**

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

#### 3.2.3 Feeding and Conveying Unit

The feeding and conveying unit is mainly used to push materials from the silo to the conveyor belt , in order to achieve the transportation of materials between different

![Official Magician E6 training-system figure, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8T36bBe6FHjbGctdoHz5%2Futp-bdd91cc27632cd722e0f.jpg?alt=media)

positions. The conveyor belt adopts a built-in stepper motor, which can accurately control the pushing distance of the material. Driven by a DC deceleration motor, the movement of the conveyor belt can be controlled to meet the transportation needs of different materials . In addition, the conveyor belt is also equipped with an alignment sensor and encoder, which can accurately detect the position of materials on the conveyor belt. It can achieve dynamic tracking and grasping of materials by robots in space, improving the transportation efficiency and accuracy of materials, as shown in Figure1-6.

**Figure1-6 Feeding and Conveying Unit 3.2.4 Mini Air Pump Box**

The mini air pump box is a practical accessory independently designed and developed by DOBOT. It is used in conjunction with the Yue Jiang robot, as shown in Figure1-7. The air pump box can provide a pressure range of -70\~110kPa. Its appearance design is exquisite. It can be directly adapted to DOBOT robots through I/O control interfaces, plug and play, and can be suitable for most daily suction cups and flexible gripper application scenarios.

![Official Magician E6 training-system figure, source page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFCGRvy9OHpul2Pb7e6PB%2Futp-747a4b8fd1f436a14a22.jpg?alt=media)

Figure1-7 Mini air pump box

#### 3.2.5 Quick Change Board Unit

The training platform is equipped with 4 quick change board modules as standard, including: trajectory board, standard visual loading board, mobile phone model workpiece loading board, circular/rectangular workpiece loading board, as shown in Figure1-8. The quick change board unit, in conjunction with the robot execution unit and visual unit, completes visual recognition, detection, and positioning of the experimental object, and completes process applications such as item tracking, positioning and grasping, stacking , and assembly .

Figure1-8 Quick Change Board Unit

![Official Magician E6 training-system figure, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fo149alWPA3w3Vfrsdkvj%2Futp-ca8256082d3eba21288b.jpg?alt=media)

![Official Magician E6 training-system figure, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAngqpSeiAHm2Q9MUbwxA%2Futp-77c1fe980a5d3ad00a26.jpg?alt=media)

## Chapter 2 Use of the Tricolour Light

### 1. Introduction

For the E6 general training system, the light color of the Tricolor light (as shown in Figure2-1) and the sound of the buzzer together indicate the operation of each device.

Figure2-1 the Tricolor light

This Demo mainly includes the following tasks:

* (1) When you press the **START** button on the control button box(as shown in
* Figure2-2), the green light is on.

(2) When you press the **STOP** button, the green light is off and the red light is on. (3) When you press the **RESET** button, the red light is off and the yellow light is on . After 2 seconds, the yellow light is off and the green light is on. After 1 second, the green light is off and the yellow light is on. After 1 second, the yellow light is off and the red light is on. After 1 second, three lights are all on and the buzzer sounds. After

2 seconds, three lights are all off and the buzzer stops.

Figure2-2 the control button box

![Official Magician E6 training-system figure, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMjzZKYQpdo1Me0GvcTnl%2Futp-a995867829313471ed5a.png?alt=media)

![Official Magician E6 training-system figure, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD3YnKxQ5JT2VgmukRI9m%2Futp-5221c25552b477b4f307.jpg?alt=media)

### 2. IO Configuration

The IO configuration of the Tricolour light, buzzer and Control buttons is shown in Table2-1.

**Table2-1 IO configuration**

| **Input** | **Description** | **Output** | **Description** |
| --------- | --------------- | ---------- | --------------- |
| DI01      | START           | DO03       | Green light     |
| DI02      | STOP            | DO04       | Yellow light    |
| DI03      | RESET           | DO05       | Red light       |
| /         | /               | DO06       | Buzzer          |

### 3. Program Debugging

#### 3.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 3.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it

on, as shown in Figure2-3.

Figure2-3 Turn on the E6 power switch

#### 3.3 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the

other end to the PC.

![Official Magician E6 training-system figure, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBD28FcfXriGGieKA64D0%2Futp-12979b8ae7c529877839.jpg?alt=media)

* (2) Modify IP of the computer.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure2-4. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

Figure2-4 Set IP of the PC

* (3) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro** to open the software. After you enter DobotStudio

Pro, the software will automatically search for robots and displays the search results (Magician E6) on the interface. Click **Connect** on the right side of the device to connect it, as shown in Figure2-5.

![Official Magician E6 training-system figure, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfFW8rxCNQcXS2wrdDVKt%2Futp-8ffcc127698c75d5fef2.jpg?alt=media)

Figure2-5 Connect robot

After successful connection, the software interface will refresh and display the

information about the E6 and its 3D model, as shown in Figure2-6.

Figure2-6 the information about the E6

#### 3.4 Enable robot

Click on the “Enable” switch of the “Magician E6” interface. Modify

various parameter values according to the actual situation in the “Load enabling settings” window that pops up. Click **Enable,** as shown in Figure2-7. The Enabling switch

![Official Magician E6 training-system figure, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI52WALexkcCkcr0KRTBC%2Futp-0a5e0c0bd67c2bffac21.png?alt=media)

![Official Magician E6 training-system figure, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

changes to in the E6 interface.

Figure2-7 Set load parameters

#### 3.5 Import program

(1) On the Home screen of DobotStudio Pro software, click **Application > Script**

**programming** and enter “Programming” interface, as shown in Figure2-8.

Figure2-8 Enter “Programming” interface

(2) Click to open File menu and select “Import project”, as shown in

Figure2-9. Select **Tricolor\_light** folder, and click **Open** , as shown in Figure2-10. Now

![Official Magician E6 training-system figure, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

![Official Magician E6 training-system figure, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIDfxzrViBZi5foblFukd%2Futp-935379b9dfa08aa4f7ce.jpg?alt=media)

the Tricolour light program has been imported into DobotStudio Pro, as shown in

Figure2-11.

Figure2-9 Import project

Figure2-10 Import path

![Official Magician E6 training-system figure, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGsU2mr86gkZMGdNHJD5J%2Futp-aed3b0205cc089b9adf9.png?alt=media)

![Official Magician E6 training-system figure, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fo43PSFfCM4YqKxdck15n%2Futp-8fe1997d92a2aa4ade31.png?alt=media)

Figure2-11 Project imported

#### 3.6 Save program

Click and enter a project name in the pop-up dialog box, as shown in Figure2-

12.

Figure2-12 Save program

Note: Saving a program refers to saving the program to the robot controller.

#### 3.7 Run program

![Official Magician E6 training-system figure, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyuHvOGmC2BXb5BUBLjuo%2Futp-a1580e9409736cd39ab4.jpg?alt=media)

![Official Magician E6 training-system figure, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiNJKZCriobFa2RN9bv35%2Futp-e845d83965d7b132b6e4.jpg?alt=media)

Click , and check whether the program is running as follows:

* (1) When you press the **START** button, the green light is on .
* (2) When you press the **STOP** button, the green light is off and the red light is on.

(3) When you press the **RESET** button , the red light is off and the yellow light is on. After 2 seconds, the yellow light is off and the green light is on. After 1 second, the green light is off and the yellow light is on. After 1 second, the yellow light is off and the red light is on. After 1 second, three lights are all on and the buzzer sounds. After 2 seconds, three lights are all off and the buzzer stops.

#### 3.8 Export program

Click to open File menu and select “Export project”. Select the path to save the program. Then enter a project name in the pop-up dialog box, as shown in Figure213.

Figure2-13 Export project

Note: Exporting a project refers to export the program to local for backup.

### 4. Key Program Description

This section mainly describes the key script. For complete script, see the project

![Official Magician E6 training-system figure, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7UDgFYR2Hd8hr2xbhhA2%2Futp-873e097133495dd50746.png?alt=media)

in Script page.

#### 4.1 Output port reset program

The output port reset program is shown in Figure2-14, which sets all output ports

to **OFF** .

Figure2-14 Output port reset program

#### 4.2 Start program

The start program is shown in Figure2-15. When you press the Start button, the green light is on .

Figure2-15 Start program

#### 4.3 Stop program

The stop program is shown in Figure2-16. When you press the STOP button, the green light is off and the red light is on.

Figure2-16 Stop program

#### 4.4 Reset program

The reset program is shown in Figure2-17. When you press the **RESET** button, the red light is off and the yellow light is on. After 2 seconds, the yellow light is off and the green light is on. After 1 second, the green light is off and the yellow light is on. After 1 second, the yellow light is off and the red light is on. After 1 second, three lights are all on and the buzzer sounds. After 2 seconds, three lights are all off and the

**buzzer stops.**

Figure2-17 Reset program

![Official Magician E6 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUqcDazIczPxvGHSCMFUx%2Futp-0ff0a4b23a041c621f3e.png?alt=media)

## Chapter 3 Application of Trajectory Simulation

### 1. Introduction

In the trajectory simulation demo, the end of the robot can move along the specified trajectory based on the taught points, as shown in Figure3-1 .

Figure3-1 Trajectory simulation

### 2. Program Debugging

#### 2.1 Preparation

#### 2.1.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 2.1.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it on, as shown in Figure3-2.

![Official Magician E6 training-system figure, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FR5LTziI5Ta5fDaVBofz7%2Futp-f4f96033f62baa1a6e5c.jpg?alt=media)

Figure3-2 Turn on the E6 power switch

#### 2.1.3 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the other end to the PC.

* (2) Modify IP of the PC.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure3-3. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

![Official Magician E6 training-system figure, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

Figure3-3 Set IP of the PC

(3) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro** to open the software. After you enter DobotStudio Pro, the software will automatically search for robots and displays the search result “Magician E6” on the interface. Click **Connect** on the right side of the device to connect it, as shown in Figure3-4.

Figure3-4 Connect robot

After successful connection, the software interface will refresh and display the

information about the E6 and its 3D model, as shown in Figure3-5.

![Official Magician E6 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfFW8rxCNQcXS2wrdDVKt%2Futp-8ffcc127698c75d5fef2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI52WALexkcCkcr0KRTBC%2Futp-0a5e0c0bd67c2bffac21.png?alt=media)

Figure3-5 the information about the E6

#### 2.1.4 Enable robot

Click on the “Enable” switch of the “Magician E6” interface. Modify various parameter values according to the actual situation in the “Load enabling settings” window that pops up. Click Enable, as shown in Figure3-6. The Enabling switch changes to in the E6 interface.

![Official Magician E6 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

Figure3-6 Set load parameters

#### 2.1.5 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to

set the speed to 15%, as shown in Figure3-7.

Figure3-7 Set Speed

Note: The global speed can be set lower during debugging, and after debugging is completed,

it can be adjusted higher according to actual needs.

#### 2.1.6 Installing the calibration needle

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro4.1 to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure3-8.

![Official Magician E6 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

Figure3-8 The posture of installing the end tool

Note: It is best to adjust the value of J6 to 0°.

(2) Install the suction cup onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Figure3-9.

Figure3-9 Install flange installation plate on the end of robot

(4) Remove the suction nozzle from the suction nozzle connecting rod and install

the calibration needle, as shown in Figure 3-10.

![Official Magician E6 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8ogIZ2WtTF7v8rFcqY3D%2Futp-2d68c8a8d27ecc7a907d.jpg?alt=media)

![Official Magician E6 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaurAi1A7IEXFaD2zlMhD%2Futp-2df2a85a50f9a9c39daa.jpg?alt=media)

![Official Magician E6 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD5KfFmPpmjn6AdSqe1yW%2Futp-4bef8fec333f7f4052a3.jpg?alt=media)

Figure 3-10 Install the calibration needle

#### 2.1.7 Adjust the robot’s posture

Adjust the robot's posture through the control panel, as shown in Figure3-11, so

that the joint coordinates are {0, 0, -90, 0, 90, 0}.

Figure3-11 Adjust the robot's posture

#### 2.1.8 Place trajectory board

Place the trajectory board on the storage area, as shown in Figure3-12.

![Official Magician E6 training-system figure, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FG0NA9bxunFDuWZaOBGl4%2Futp-9abfbb3e3bbe5be10714.jpg?alt=media)

![Official Magician E6 training-system figure, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsQASufzZrqGFmqfhvQ4o%2Futp-02771c88dfe736dbdf5e.jpg?alt=media)

Figure3-12 Place the trajectory board

#### 2.2 Import program

(1) On the Home screen of DobotStudio Pro software, click **Application > Script**

**programming** and enter “Programming ” interface, as shown in Figure3-13.

Figure3-13 Enter “Programming” interface

(2) Click to open File menu and select “Import project”, as shown in Figure3-14. Select **Trajectory\_Simulation** folder, and click **Open** . Now the **Trajectory\_Simulation** program has been imported into DobotStudio Pro, as shown in Figure3-15.

![Official Magician E6 training-system figure, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaPfdsHLkEXSnR59mqVr2%2Futp-b16bad06b8e612aa9480.jpg?alt=media)

![Official Magician E6 training-system figure, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIDfxzrViBZi5foblFukd%2Futp-935379b9dfa08aa4f7ce.jpg?alt=media)

Figure3-14 Import project

Figure3-15 Project imported

#### 2.3 Save program

Click and enter a project name in the pop-up dialog box, as shown in Figure3-

16.

![Official Magician E6 training-system figure, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGsU2mr86gkZMGdNHJD5J%2Futp-aed3b0205cc089b9adf9.png?alt=media)

![Official Magician E6 training-system figure, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTZQixOCmpWKvbNmpMqrQ%2Futp-3f8d9cd41bd021f8ec91.png?alt=media)

Figure3-16 Save program

#### 2.4 Debug points

You need to debug 40 points in this demo. The points on the trajectory board are

shown in Figure3-17.

Figure3-17 Trajectory board points

(1) Jog the robot to move over the trajectory board, as shown in Figure3-18. Click **Points** to enter the Points interface. Firstly select P1, then click the tool **Cover** , finally

click **Cover** in the pop-up tips again to update P1 point, as shown in Figure3-19.

![Official Magician E6 training-system figure, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FodZ7FzHOyxs3WMSno45E%2Futp-31f5f0fb37298696e77a.png?alt=media)

![Official Magician E6 training-system figure, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuqKv8XL4WkcffBpR5ZHa%2Futp-35a9b81cd9cf59a87922.jpg?alt=media)

Figure3-18 Locate P1

Figure3-19 Update P1

(2) Jog the robot to point gj1 on the trajectory board, as shown in Figure3-20. Firstly select P2, then click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P2 point, as shown in Figure3-21.

![Official Magician E6 training-system figure, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FguLdoRqMnK21gWhDKNYL%2Futp-2106cc802ec5f0eb9981.jpg?alt=media)

![Official Magician E6 training-system figure, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnMAaxzqeJcJNuY81ADJ4%2Futp-4466cb8322bb8bf4ecca.png?alt=media)

![Official Magician E6 training-system figure, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

Figure3-20 Locate Point gj1

Figure3-21 Update P2(gj1)

(3) Jog the robot to point gj2 on the trajectory board, as shown in Figure3-22.

Firstly select P3, then click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P3 point, as shown in Figure3-23.

![Official Magician E6 training-system figure, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKKSnaFFjDwxlmzIkSBSp%2Futp-8711793412b14bdfa2ca.jpg?alt=media)

![Official Magician E6 training-system figure, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIsgNuhu07InVo62e5pN1%2Futp-f93f8cdea7178947a4ac.jpg?alt=media)

![Official Magician E6 training-system figure, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

Figure3-22 Locate Point gj2

Figure3-23 Update P3(gj2)

(4) Repeat the steps above to teach the remaining 38 points. The updated points

are shown in Figure3-24.

![Official Magician E6 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0EnoJtaNnVh8JshFKy5Y%2Futp-1b70e7090f05e5196967.jpg?alt=media)

![Official Magician E6 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuDnLFF3wRMikbsL7lHRh%2Futp-4b51f2720490003799e9.png?alt=media)

![Official Magician E6 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

**Application of Trajectory Simulation** (1) P1-P9

(2) P10-P18

![Official Magician E6 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5sIgVUYLA18amam4soBb%2Futp-f414076e02026480e98b.png?alt=media)

![Official Magician E6 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU1mKTmAi8QXDoRsYWbC1%2Futp-0262944637ba6c45b0e6.png?alt=media)

Figure3-24 Updated points

#### 2.5 Run program

Click to run the program, and observe whether the robot moves following

![Official Magician E6 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM0qXjoOJb6Nbbkg1vk6c%2Futp-ca969376537bea144367.png?alt=media)

![Official Magician E6 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHaxPP8SvI5CdcWpk2awp%2Futp-aee31e48c9b43ff80253.png?alt=media)

![Official Magician E6 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu32PbZA8UIlxYl8O95zw%2Futp-8e5c54c923ddfabebfcc.png?alt=media)

the trajectory.

Note: During the program operation, if the robot’s point position is found to be incorrect, please directly press the “ ” button to stop the program operation, and then follow the method

explained in **2.4** to perform point debugging again.

#### 2.6 Export program

Click to open File menu and select “Export project”. Select the path to save the program. Then enter a project name in the pop-up dialog box.

Note: Exporting a project refers to export the program to local for backup.

### 3. Key Program Description

This section mainly describes the key script. For complete script, see the project in Script page.

The trajectory simulation is mainly about moving between different points, as shown in Figure3-25.

Figure3-25 Trajectory points

As the trajectory consists of shapes with different characteristics, the robot moves

in four modes: **MovJ** for point-to-point motion, **MovL** for linear motion, **Arc** for arc motion, and **Circle** for circular motion.

![Official Magician E6 training-system figure, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTcLkZuTxWBPbc8iaGapr%2Futp-31600926637c51f83328.png?alt=media)

## Chapter 4 Application of Static Palletizing

### 1. Introduction

The specific task of static palletizing is to use the robot to carry six rectangular workpieces placed in a 3×3×1 matrix on the standard vision board to the storage area

and code it as 1×3×3 stacks, as shown in Figure4-1 and Figure4-2.

Figure4-1 Palletizing workpieces

Figure4-2 Storage area

### 2. IO Configuration

The IO configuration of static palletizing is shown in Table4-1.

![Official Magician E6 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyagQQrimABcoSp62q4pN%2Futp-f2eea9cb0a7a6efd7c03.jpg?alt=media)

![Official Magician E6 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FttxpURIedspchCL90xJH%2Futp-443388d5b6342e1ac393.jpg?alt=media)

**Table4-1 IO configuration**

| **Output** | **Description** |
| ---------- | --------------- |
| DO09       | Vacuum pumping  |
| DO10       | Vacuum breaking |

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

Turn on the power switch of the pump box and turn the control button to **Auto** , as shown in Figure4-4.

![Official Magician E6 training-system figure, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

Figure4-4 Turn on the power switch of the pump box

#### 3.1.4 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the other end to the PC.

* (2) Modify IP of the PC.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure4-5. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

![Official Magician E6 training-system figure, source page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIOo2VwMNtIqj3S5oUm1e%2Futp-fb05a14080aeb7630a08.jpg?alt=media)

Figure4-5 Set IP of the PC

* (3) Connect DobotStudio Pro to the robot.

Double-click DobotStudio Pro to open the software. After you enter DobotStudio Pro, the software will automatically search for robots and displays the search results “Magician E6” on the interface. Click **Connect** on the right side of the device to connect

it, as shown in Figure4-6.

Figure4-6 Connect robot

After successful connection, the software interface will refresh and display the

![Official Magician E6 training-system figure, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfFW8rxCNQcXS2wrdDVKt%2Futp-8ffcc127698c75d5fef2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI52WALexkcCkcr0KRTBC%2Futp-0a5e0c0bd67c2bffac21.png?alt=media)

information about the E6 and its 3D model, as shown in Figure4-7.

Figure4-7 Robot connected

#### 3.1.5 Enable robot

Click on the “Enable” switch of the “Magician E6” interface. Modify various parameter values according to the actual situation in the “Load enabling settings” window that pops up. Click **Enable,** as shown in Figure4-8. The Enabling switch

changes to in the E6 interface.

![Official Magician E6 training-system figure, source page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

Figure4-8 Set load parameters

#### 3.1.6 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to

set the speed to 40%, as shown in Figure4-9.

Figure4-9 Set Speed

Note: The speed can be set lower during debugging, and after debugging is completed, it can

be adjusted higher according to actual needs.

#### 3.1.7 Install eccentric tools

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro4.1 to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure4-10.

![Official Magician E6 training-system figure, source page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

Figure4-10 The posture of installing the end tool

Note: It is best to adjust the value of J6 to 0°.

* (2) Prepare installation materials.

Prepare the eccentric flange, suction cup, and corresponding installation screws,

as shown in Figure4-11.

Figure4-11 Prepare installation materials

* (3) Install the suction cup onto the eccentric flange plate through four M3 \* 8

screws using an allen tool, as shown in Figure4-12.

Figure4-12 Assemble eccentric tools

![Official Magician E6 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8ogIZ2WtTF7v8rFcqY3D%2Futp-2d68c8a8d27ecc7a907d.jpg?alt=media)

![Official Magician E6 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaurAi1A7IEXFaD2zlMhD%2Futp-2df2a85a50f9a9c39daa.jpg?alt=media)

![Official Magician E6 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPvrlM0eHWNAwOwFjITjZ%2Futp-546af7717d65634d97a3.jpg?alt=media)

![Official Magician E6 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F99G3ufok8c4wL8LmhkNS%2Futp-a06e24909360dbc50a21.jpg?alt=media)

* (4) Install the eccentric tools onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Figure4-13.

Figure4-13 Install the eccentric tools on the end of robot

(5) Connect one end of the air pipe to the “Air” hole in the air pump box, and the

other end to the suction cup. Fix it to the robot with a tie, as shown in Figure4-14.

Figure4-14 Connect the air pipe

#### 3.1.8 Install standard vision board

Install the standard vision board above the conveyor belt, as shown in Figure4-15.

![Official Magician E6 training-system figure, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrE34J9LWIv8LjzcCTmxA%2Futp-76608609e0cc0c45a13b.jpg?alt=media)

![Official Magician E6 training-system figure, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxIvRTpyabMeTw1K4ZyRS%2Futp-2a34d50e82b6568cc1c2.jpg?alt=media)

Figure4-15 Install standard vision board

#### 3.2 Establish tool coordinate system

The tool coordinate system is generated by four point teaching method: After installing the tool at the end of E6, adjust the position and posture of the tool, make TCP (Tool Center Point) align with the same point in space (reference point) in four different attitudes, obtain the position offset of the tool, and generate the tool coordinate system, as shown in Figure4-16.

Figure4-16 Tool coordinate system example

(1) Adjust the robot’s posture through the control panel, as shown in Figure4-17,

so that the joint coordinates are {0, 0, -90, 0, 90, 0}.

![Official Magician E6 training-system figure, source page 53](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FR5NLEtQALpNDl1HmIeOJ%2Futp-124adef7817cef796840.jpg?alt=media)

Figure4-17 Adjust the robot's posture

(2) Remove the suction nozzle from the suction nozzle connecting rod. Install the

calibration needle, as shown in Figure4-18.

Figure4-18 Install the calibration needle

Note: Do not touch the tip of the calibration needle with your hands, be careful not to scratch

it.

(3) Place a pointed screw on the visual loading plate, using the tip of the screw as

a reference point, as shown in Figure4-19.

![Official Magician E6 training-system figure, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNejXQZejePervcaQQPat%2Futp-4a5be73ad2f93dd3a527.jpg?alt=media)

![Official Magician E6 training-system figure, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtsN5nQdMIul4EgSVZyjQ%2Futp-ba7c4103e2d63ff8a651.jpg?alt=media)

Figure4-19 Set reference point

(4) Click **Settings** > **Coordinate System** > **Tool coordinate system** on DobotStudio Pro main page. Select Tool coordinate system 1, and click **Modify** to update the coordinate system (if there is only No. 0, you can click **Add** to add a coordinate system), as shown in Figure4-20.

Figure4-20 Select “Tool coordinate system”

* (5) Click **Four-point setting** in Modify interface, as shown in Figure4-21.

Figure4-21 Select “Four-point setting”

![Official Magician E6 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fff46RQ4LDhlcU2BwoO56%2Futp-88c72a3ca2a9b24dd7de.jpg?alt=media)

![Official Magician E6 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDnqpDG6mYoUXktpanqNr%2Futp-d57e48f1a86a5da4f8f3.jpg?alt=media)

![Official Magician E6 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fk82SmqM75Qvla4xe3hXt%2Futp-27237bbce4fdd6c23156.jpg?alt=media)

(6) Jog E6 and align the needle tip of the robot end with the reference point in the first posture, as shown in Figure4-22. Then select P1 and click **Obtain** , as shown in Figure4-23.

Figure4-22 The first attitude alignment reference point

Figure4-23 Obtain P1

(7) Jog E6 and align the needle tip of the robot end with the reference point in the second posture, as shown in Figure4-24. Then select P2 and click **Obtain** , as shown in Figure4-25.

![Official Magician E6 training-system figure, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcyiII5fWZydZCREgHzoW%2Futp-d416a6de90e85ba964c5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHcxQMmMKanA8vXAJZe1t%2Futp-f8ebb6f3f19826b0c76c.jpg?alt=media)

Application of Static Palletizing<br>

Figure4-24 The second attitude alignment reference point

Figure4-25 Obtain P2

(8) Jog E6 and align the needle tip of the robot end with the reference point in the third posture, as shown in Figure4-26. Then select P3 and click **Obtain** , as shown in Figure4-27.

![Official Magician E6 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCUmJrJwb6kQnGxwzl7i3%2Futp-d702093600839b9cc168.jpg?alt=media)

![Official Magician E6 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGrbDYovQd7xqtEAiNCq1%2Futp-24e5f91688af5eb75235.jpg?alt=media)

Figure4-26 The third attitude alignment reference point

Figure4-27 Obtain “P3”

(9) Jog E6 and align the needle tip of the robot end with the reference point in the fourth posture, as shown in Figure4-28. Then select P4 and click **Obtain** , as shown in Figure4-29.

![Official Magician E6 training-system figure, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC8Z93WfP1f3qJCSKnKZn%2Futp-032eb6d7a4752387d5a6.jpg?alt=media)

![Official Magician E6 training-system figure, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRwzW5THcFKgvhPCGCUeP%2Futp-d776e58edac362c3ff2e.jpg?alt=media)

Figure4-28 The fourth attitude alignment reference point

Figure4-29 Obtain “P4”

(10) Click **Confirm** , the system will automatically return to the “Modify” interface,

and then click **Save** , as shown in Figure4-30.

![Official Magician E6 training-system figure, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJOafgynXX36aSOncyVPE%2Futp-9182d0ed8e2706344a74.jpg?alt=media)

![Official Magician E6 training-system figure, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjqwHdCGHOg62ieNyTR61%2Futp-44794f5aca01800c8bd6.jpg?alt=media)

Figure4-30 Save

(11) Prove if the tool coordinate system has been calibrated successfully.

Set the “Tool coordinate system” to “1” in the “Jog” panel, and then continuously click **RZ-** or **RZ+** to observe whether the calibration needle tip is always aligned with a point, as shown in Figure4-31. If the calibration needle tip is consistently aligned with a point, it indicates that tool coordinate 1 has been calibrated successfully. Otherwise, it is necessary to calibrate the tool coordinate system again.

![Official Magician E6 training-system figure, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FX1NjBBb1aYLbHkaTHODA%2Futp-7b556fa453234b9bdb59.png?alt=media)

Figure4-31 Tool coordinate system 1

(12) Remove the calibration needle and replace it with a suction nozzle.

#### 3.3 Import program

(1) On the Home screen of DobotStudio Pro software, click **Application > Script programming** and enter “Programming” interface, as shown in Figure4-32.

Figure4-32 Enter “Programming ” interface

![Official Magician E6 training-system figure, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbtKeHRKnuDDECWTyeOm8%2Futp-d0d9d372bce2188a0f6b.jpg?alt=media)

![Official Magician E6 training-system figure, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIPTDA6WjSxcC0MT1skA4%2Futp-65b63174caccb96d8b8f.jpg?alt=media)

(2) Click to open File menu and select “Import project”, as shown in Figure4-33. Select **Static\_Palletizing** folder, and click **Open** . Now the Modify **Static\_Palletizing** program has been imported into DobotStudio Pro, as shown in Figure4-34.

Figure4-33 Import project

Figure4-34 Project imported

#### 3.4 Save program

Click and enter a project name in the pop-up dialog box, as shown in Figure4-

35.

![Official Magician E6 training-system figure, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fg48DkFmrFOwg3OvetNJM%2Futp-9237a070884cb38d8169.jpg?alt=media)

![Official Magician E6 training-system figure, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F66CzqQr1LFq978zUdrz0%2Futp-e6f44442d5fb1d883537.png?alt=media)

Figure4-35 Save program

#### 3.5 Prepare material

Place 9 workpieces in the upper right corner of the standard vision board in 3×3×1

matrix, as shown in Figure4-36.

Figure4-36 Palletizing workpieces

Note: When placing stacked materials, you can choose a cross on the pallet as the reference

point for placement.

#### 3.6 Debug points

The robot uses a total of 3 points for static stacking, and the debugging method is

as follows:

* (1) Adjust the robot’s posture through the control panel, as shown in Figure4-37,

so that the joint coordinates are {0, 0, -90, 0, 90, 0}.

![Official Magician E6 training-system figure, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYZU9DljnWqsXPWeNnOJG%2Futp-54405f950c4e6c4e1e77.jpg?alt=media)

![Official Magician E6 training-system figure, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvdpnfjseuI4bYKKh2ux2%2Futp-b0fc8a6b3d41595baa73.jpg?alt=media)

Figure4-37 Adjust the robot’s posture

(2) Update safe point P1.

The tool coordinate system is “1”. Jog the robot to a position between the conveyor

and the storage area, as shown in Figure4-38.

Figure4-38 Locate Point P1

Click **Points** to enter the **Points** interface. Firstly select P1, then click the tool

**Cover** , and finally click **Cover** in the pop-up tips again to update P1 point, as shown in

Figure4-39.

![Official Magician E6 training-system figure, source page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwMQni0cQhdyuW93tBW9Q%2Futp-707994058fef8cb24986.jpg?alt=media)

![Official Magician E6 training-system figure, source page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVukv3sZL68mqw0iYMsYz%2Futp-22e7626d23e3f3473cb4.jpg?alt=media)

Figure4-39 Update P1

(3) Update picking point P2.

Jog the robot to the picking point of the first workpiece on the standard vision board. The suction cup needs to touch the centre of the first workpiece, as shown in Figure4-40. In the **Points** interface, firstly select P2, then click the tool **Cover** , and finally click **Cover** in the pop-up tips again to update P2 point, as shown in Figure4-41.

Figure4-40 Locate the first Picking point P2

![Official Magician E6 training-system figure, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9ljjd9oCj3mx5lKBG4we%2Futp-6935e52088201ed16fe8.jpg?alt=media)

![Official Magician E6 training-system figure, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv8isBmEvBz7SHBCuDRjH%2Futp-abb391a268388ef416fd.png?alt=media)

![Official Magician E6 training-system figure, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

Figure4-41 Update P2

* (4) Update placing point P3.

Open “Controller DI/DO” panel. Set **DO\_09** to **ON** to make the robot suck the workpiece, as shown in Figure4-42. Then jog the robot to move to the first placing point (P3) in the storage area, as shown in Figure4-43. Select P3 in Points and click the tool **Cover** . Click **Cover** in the pop-up tips again to update P3 point , as shown in Figure444.

Figure4-42 Controller DI/DO panel

![Official Magician E6 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F26KenPjX34iujg6hlXgo%2Futp-4ec4e88359215127c73d.png?alt=media)

![Official Magician E6 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8bUnxi4HqbeBaD6zHk2t%2Futp-eb3de02fbcd3bbe08472.png?alt=media)

![Official Magician E6 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F77EeOqJWySCuHr7NyseD%2Futp-11b6deac6cd4e884f97b.png?alt=media)

Figure4-43 Locate the first Placing point P3

Figure4-44 Update P3

Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the workpiece is placed into the groove accurately. If not, you need to re-debug the point.

#### 3.7 Run program

Click . Observe whether the program is running as follows: The robot puts the workpieces arranged in a 3×3×1 matrix on the standard vision board into the storage area and codes it as 1×3×3 stacks, as shown in Figure4-45.

![Official Magician E6 training-system figure, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fdf7CLqsQ12LvykyQ1BZm%2Futp-b90daed5070626d5a4ff.jpg?alt=media)

![Official Magician E6 training-system figure, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNtQ7tdOOKudr4r0mmXN4%2Futp-c31b859e0fb090c42c93.png?alt=media)

![Official Magician E6 training-system figure, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeToF0ahKMobK1TfYdTl2%2Futp-be72b44da868c7d99681.png?alt=media)

Figure4-45 Palletizing effect

Note: During the program operation, if the robot's point position is found to be incorrect, please directly press the “ ” button to stop the program operation, and then follow the method explained in 3.6 to perform point debugging again.

#### 3.8 Export project

Click to open File menu and select “Export project”. Select the path to save the program. Then enter a project name in the pop-up dialog box.

Note: Exporting a project refers to exporting the program to local for backup.

### 4. Key Program Description

This section mainly describes the key script. The complete code can be viewed in the script project page.

#### 4.1 Output port reset program

The output port reset program is shown in Figure4-46, which sets all output ports to **OFF** .

![Official Magician E6 training-system figure, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FttxpURIedspchCL90xJH%2Futp-443388d5b6342e1ac393.jpg?alt=media)

Figure4-46 Output port reset program

#### 4.2 Attitude adjustment program

Adjust the posture of the robot with coordinates {0,0, -90,0, 90,0}, as shown in

Figure4-47 and Figure4-48.

Figure4-47 The posture adjustment program of the robot

Figure4-48 Robot posture

#### 4.3 Robot pick-up program

The robot pick-up program is shown in Figure4-49, which controls the robot to

pick up the workpieces from the standard vision board.

![Official Magician E6 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdbHWNH9tvXHbMPQtmItS%2Futp-50c6237f8f13d5782630.jpg?alt=media)

![Official Magician E6 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJhgpjYgimY9u7JK5asqx%2Futp-8a5fc576d2dfd3258236.png?alt=media)

Figure4-49 Robot pick-up program

You only need to teach and save the placing point P2 of the first workpiece. Then the corresponding coordinates of 8 other picking points can be obtained according to the distance between the first picking point and each of the remaining picking points.

The order of material collection is shown in Figure4-50, with the red column taken

first, followed by the green column, and finally the blue column.

Figure4-50 The order of material collection

#### 4.4 Robot placement program

The robot placement program is shown in Figure4-51, which controls the robot to

place nine workpieces into the storage area and code it as 1×3×3 stacks.

Figure4-51 Robot placement program

You only need to teach and save the placing point P3 of the first workpiece. Then

the corresponding coordinates of 8 other placing points can be obtained according to

![Official Magician E6 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZ4ddZOHq0YaxiOzNJAkC%2Futp-4376f9479ec034093abf.jpg?alt=media)

![Official Magician E6 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5JqtFUS89MhaUtLoGnlE%2Futp-b14dd60f940e9ce2d70d.png?alt=media)

the distance between the first placing point and each of the remaining placing points.

## Chapter 5 Application of Robot Handling

### 1. Introduction

The task that the robot handling application aims to achieve is for the robot to transport the workpiece conveyed by the conveyor belt to the storage area. During the system operation, the operation of the equipment can be controlled through the control buttons, while at the same time the Tricolour light indicates the operating status of the device through the light colour. The specific task description is as follows:

Online operation: When you press the **RESET** button, the device is initialized and the yellow light of the Tricolour light is on. When you press the **START** button, the device starts running and the green light of the Tricolour light is on. When you press the **STOP** button, after the device completes the currently executing action, it stops running and the red light is on.

Offline operation: When you press the **START** button, the device starts running and the green light is on. When you press the **STOP** button, the device stops soon and the red light is on. If an alarm signal appears on the robot, it can be cleared by pressing the **RESET** button. The control buttons are shown in the Figure5-1.

START STOP RESET EMGENCY STOP<br>

Figure5-1 Control Buttons Box

When the system is running , the circular workpiece is pushed from the stock bin (as shown in Figure5-2) by the motor to the conveyor belt, and moves forward with the conveyor belt. When the workpiece reaches the picking point (sensing point), the conveyor belt stops moving, and the robot carries the workpiece to the circular groove of the rectangular/circular plate in the storage area and arrange in a 3x2 matrix, as shown in Figure5-3.

![Official Magician E6 training-system figure, source page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMfCIumOX1CyR1OP3bEbj%2Futp-6e04b7b3d4ee389c4bb0.jpg?alt=media)

Figure5-2 Stock bin

Figure5-3 Storage area

**2. IO Configuration**

The IO configuration of the Robot Handling is shown in Table 5-1.

**Table 5-1 IO configuration**

| **DI** | **Description**                     | **DO** | **Description**    |
| ------ | ----------------------------------- | ------ | ------------------ |
| DI01   | START                               | DO01   | Pusher motor start |
| DI02   | STOP                                | DO02   | Conveyor start     |
| DI03   | RESET                               | DO03   | Green light        |
| DI09   | Material detection in the stock bin | DO04   | Yellow light       |
| DI10   | Material inplace inspection         | DO05   | Red light          |
| /      | /                                   | DO09   | Vacuumpumping      |
| /      | /                                   | DO10   | Vacuum breaking    |

![Official Magician E6 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3Q9sDTwwL8ive6FjIkA2%2Futp-2dc076844322c061faec.jpg?alt=media)

![Official Magician E6 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWnugeDBRtnN7tAvmvZCj%2Futp-a6817cd71dd146fa52e0.jpg?alt=media)

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 3.1.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it

on, as shown in Figure5-4.

Figure5-4 Turn on the E6 power switch

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to Auto, as

shown in Figure5-5.

Figure5-5 Turn on the power switch of the pump box

#### 3.1.4 Connect robot

* (1) Connect the robot to the computer.

![Official Magician E6 training-system figure, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

![Official Magician E6 training-system figure, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIOo2VwMNtIqj3S5oUm1e%2Futp-fb05a14080aeb7630a08.jpg?alt=media)

Connect one end of the network cable to the LAN1 port on the E6 base and the other end to the PC.

* (2) Modify IP of the PC.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure5-6. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

Figure5-6 Set IP of the PC

* (3) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro** to open the software. After you enter DobotStudio

Pro, the software will automatically search for robots and displays the search results “Magician E6” on the interface. Click **Connect** on the right side of the device to connect it, as shown in Figure5-7.

![Official Magician E6 training-system figure, source page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDb5ccDkzTmqRU8BOmmx9%2Futp-ca3a257ba809811bdc70.png?alt=media)

Figure5-7 Connect robot

After successful connection, the software interface will refresh and display the

information about the E6 and its 3D model, as shown in Figure5-8.

Figure5-8 the information about the E6

#### 3.1.5 Enable robot

Click on the “Enable” switch in the “Magician E6” interface. Modify

various parameter values according to the actual situation in the “Load enabling settings”

![Official Magician E6 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI52WALexkcCkcr0KRTBC%2Futp-0a5e0c0bd67c2bffac21.png?alt=media)

![Official Magician E6 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

window that pops up. Click **Enable,** as shown in Figure5-9. The Enabling switch

changes to in the E6 interface.

Figure5-9 Set load parameters

#### 3.1.6 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to

set the speed to 34%, as shown in Figure5-10.

Figure5-10 Set Speed

#### 3.1.7 Install suction cup tool

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro4.1 to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure5-11.

![Official Magician E6 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

Figure5-11 The posture of installing the end tool

Note: It is best to adjust the value of J6 to 0°.

* (2) Install the suction cup onto the end of the robot through four M3 \* 8 screws
* using an allen tool, as shown in Figure5-12.

Figure5-12 Install the suction cup on the end of robot

(3) Connect one end of the air pipe to the “Air” hole in the air pump box, and the

other end to the suction cup. Fix it to the robot with a tie, as shown in Figure5-13.

![Official Magician E6 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGID1lJWubeuP8tsnZlsT%2Futp-b553235602b81b2845ed.jpg?alt=media)

![Official Magician E6 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaurAi1A7IEXFaD2zlMhD%2Futp-2df2a85a50f9a9c39daa.jpg?alt=media)

![Official Magician E6 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzcv41juFPW7siMzWaWqI%2Futp-17f289914692994ebfa2.jpg?alt=media)

Figure5-13 Connect the air pipe

#### 3.1.8 Adjust the robot’s posture

Adjust the robot’s posture through the control panel, as shown in Figure5-14, so

that the joint coordinates are {0, 0, -90, 0, 90, 0}.

Figure5-14 Adjust the robot’s posture

#### 3.2 Import program

(1) On the Home screen of DobotStudio Pro software, click **Application > Script programming** and enter “Programming” interface, as shown in Figure5-15.

![Official Magician E6 training-system figure, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKL03BrmYi69M0J3Njcfn%2Futp-ae4eddabe9f601483fd3.jpg?alt=media)

![Official Magician E6 training-system figure, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fksw5YLQKKPrr3LO6R4x8%2Futp-90ab4ecf4d4d9d93ab9a.jpg?alt=media)

Figure5-15 Enter “Programming ” interface

(2) Click to open File menu and select “Import project”, as shown in Figure5-16. Select **Robot\_Handling** folder, and click **Open** . Now the **Robot\_Handling** program has been imported into DobotStudio Pro, as shown in Figure5-17.

Figure5-16 Import project

![Official Magician E6 training-system figure, source page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2pd9Bs7iatuY2gGSze50%2Futp-f495039ececa6de769b7.jpg?alt=media)

![Official Magician E6 training-system figure, source page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIXwKTE5fyuvCTREYDDhV%2Futp-2e8c805b2f78fea08838.jpg?alt=media)

Figure5-17 Project imported

#### 3.3 Save program

Click and enter a project name in the pop-up dialog box. Click **Save** , as

shown in Figure5-18.

Figure5-18 Save program

#### 3.4 Debug points

The robot handling demo includes three major points, as described below.

* (1) Update safe point P1.

Jog the robot to a position between the conveyor and the storage area, as shown in

![Official Magician E6 training-system figure, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fxrbw5GT8RlqtEGC1Woer%2Futp-df3edbb96395ae3b78d9.jpg?alt=media)

![Official Magician E6 training-system figure, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEtLWar5sRKk60VifLVww%2Futp-d2790552a867757c1179.jpg?alt=media)

Figure5-19.

Figure5-19 Locate P1

②Click **Points** to enter the Points interface. Firstly select P1.Then click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P1 point, as shown in

Figure5-20. Click and save the program.

Figure5-20 Update P1

* (2) Update picking point P2.
* ①The workpiece reaches the picking point.

Click . Press the **RESET** button to wait for the light to flash. Then press

the **START** button to run the program. When the conveyor with the circular workpiece stops at the picking point, click to stop running the program.

②Jog the robot to the circular workpiece, and make the suction cup slightly touch

the surface of the workpiece, as shown in Figure5-21.

![Official Magician E6 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpfVCjSA5a5GOmCaud25Y%2Futp-b4e2b942743bc623f3e5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzdy0KnhL5SSZeEoxhDcV%2Futp-c5f16d5ccfda081448fa.jpg?alt=media)

Figure5-21 Locate P2

③Open **Controller DI/DO** panel. Set **DO\_09** to **ON** to make the robot suck the

circular workpiece, as shown in Figure5-22.

Figure5-22 **Controller DI/DO** panel

④Open **Points** page. Select **P2** and click **Cover** , as shown in Figure5-23. Then

click **Cover** in the pop-up Tips dialog box again to update P2 point. Click and save the program.

![Official Magician E6 training-system figure, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUqpTgmYC25l2wYGhvuOV%2Futp-1a89fe3894e090a56059.jpg?alt=media)

![Official Magician E6 training-system figure, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F26KenPjX34iujg6hlXgo%2Futp-4ec4e88359215127c73d.png?alt=media)

**Application of Robot Handling**

Figure5-23 Update P2

(3) Update placing point P3.

①Jog the robot to the first placing point, as shown in Figure5-24. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the circular workpiece is accurately placed in the groove. If it is not, it needs to be repositioned.

Figure5-24 Locate the first placing point

②Open **Points** page. Select **P3** and click **Cover** , as shown in Figure5-25. Then

click **Cover** in the pop-up Tips dialog box again to update P3 point. Click and save

the program.

![Official Magician E6 training-system figure, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3m7vjSJVOYAA6fPeQqKa%2Futp-09bc5f91cf0246e60cb7.png?alt=media)

![Official Magician E6 training-system figure, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FG2cAv47I2S6xd0UYwGra%2Futp-dc5c5c2c939967a6d2dc.jpg?alt=media)

Figure5-25 Update P3

#### 3.5 Run Online program

Place 6 circular workpieces into the silo. Click . Observe whether the program runs as follows: When you press the **RESET** button , the system resets and the yellow light lights up once . Then when you press the **START** button, the green light is on and the system runs. The circular workpiece is pushed from the stock bin by the motor to the conveyor belt, and moves forward with the conveyor belt. When the workpiece reaches the picking point (sensing point), the conveyor belt stops moving, and the robot carries the workpiece to the circular groove of the rectangular/circular plate in the storage area and arrange in a 3x2 matrix, as shown in Figure5-26. If the **STOP** button is pressed midway, the device stops running and the red light is on after executing the current action.

![Official Magician E6 training-system figure, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsmN1J6Kd4V1p2p0oHj4z%2Futp-560c403ed35b77575839.png?alt=media)

Figure5-26 Program running result

#### 3.6 Run Offline program

#### 3.6.1 Set Offline parameters

Click **Monitor** on the top toolbar of DobotStudio Pro4.1 to enter the default **Controller DI/DO** interface. Then click **Settings** , as shown in Figure5-27, to enter the **IO settings** interface. In the **IO settings** interface, set “Function configuration” of DI\_1 to “Start” and set “Function configuration” of DI\_2 to “Stop” and set “Function configuration” of DI\_3 to “Clear alarm”, as shown in Figure5-28.

Figure5-27 “Controller DI/DO” interface

![Official Magician E6 training-system figure, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYlvHAoZBrdd0Pw9sZQfR%2Futp-cda6a241546d09cc3256.jpg?alt=media)

![Official Magician E6 training-system figure, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDD7M2qcBuY9T7RJBdiGG%2Futp-f12b9b54d59dd84e5856.png?alt=media)

Figure5-28 Set Offline parameters

Click **Select project** to enter the project selection interface and select **Run default**

**project** . Then click **Select** and select the **Robot\_Handling** program from the pop-up drop-down menu. Finally, click **Save** , as shown in Figure5-29.

Figure5-29 Select project

![Official Magician E6 training-system figure, source page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRHyObZ8v05I9fJ7eQzv5%2Futp-e964c29cf6863776ffa4.png?alt=media)

![Official Magician E6 training-system figure, source page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBJlScgwxrD9v63PX3uIr%2Futp-2f1a4f1b05faddac992a.png?alt=media)

#### 3.6.2 Offline operation

Place 6 circular workpieces into the silo. Close the DobotStudio Pro4.1 software. After pressing the **START** button, the green light is on and the system runs. The circular workpiece is pushed from the silo to the conveyor belt by an electric motor, and moves forward with the conveyor. When the workpiece reaches the picking point (sensing point), the conveyor stops moving, and the robot carries the workpiece to the circular groove of the rectangular/circular plate in the storage area and arranges in a 3x2 matrix . After pressing the **STOP** button midway, the device immediately stops running and the red light is on.

#### 3.7 Export program

Click to open File menu and select **Export project** . Select the path to save the program. Then enter a project name in the pop-up dialog box.

### 4. Key Program Description

This section mainly describes the key script. For complete script, see the project in Script page.

#### 4.1 Input signal detection program

The input signal detection program is shown in Figure5-30, which detects whether there are input signals in IO port.

Figure5-30 Input signal detection program

Note: The input signal detection program is in the variable program.

#### 4.2 Robot pick-up program

The robot pick-up program is shown in Figure5-31 . The function of the program

is to start the pusher motor when material is detected in the material slot, and the circular workpiece is pushed onto the conveyor belt. Then the conveyor belt starts. When the conveyor belt drives the workpiece to the material in place detection station, the conveyor belt stops and the robot picks up material on the conveyor belt .

Figure5-31 Pick-up program

Note: The robot pick-up program is in the variable program.

#### 4.3 Reset/Start program

The reset/start program is shown in Figure5-32. Press the “RESET” button to reset

the system. Press the “START” button to start the system.

Figure5-32 Reset/start program

#### 4.4 Attitude adjustment program

The posture adjustment program is shown in Figure5-33, which implements the function of adjusting the robot’s posture to the posture shown in Figure5-34.

![Official Magician E6 training-system figure, source page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMwiAuZPx0lDkqI7UGDN9%2Futp-d53df9566ca1f5557368.png?alt=media)

![Official Magician E6 training-system figure, source page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fqwj8ITyfBLci6j5jkvod%2Futp-a34150578c9f11c3c941.png?alt=media)

Figure5-33 Robot attitude adjustment program

Figure5-34 Robot attitude

#### 4.5 Robot placement program

The robot placement program is shown in Figure5-35, which controls the robot to

move to six placing points to place materials.

Figure5-35 Robot placement program

In line 42 and line 43 of the program, the first placing point P3 is the reference

![Official Magician E6 training-system figure, source page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrsyCNhlggnD131BK5Ksr%2Futp-71f4121b0634a9ca52e5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDHdzgQtcuwkdUHxEyPCj%2Futp-edebe1c30e309db3c793.png?alt=media)

point for the other placing points. As the placing positions are fixed, the coordinates of the remaining five placing points are calculated based on the cycle times and the distance between point P3 and each placing point.

#### 4.6 Button control program

The button control program is shown in Figure5-36. When the **START** button is pressed, the green light is on. When the **RESET** button is pressed, the yellow light is on, and all IO ports will be set to **OFF** , which means device initialization (turning off the feeding motor, turning off the conveyor belt, turning off the green light and the red light). After initialization is completed, the yellow light goes out. When the **STOP** button is pressed, and after the device completes the currently executing action, it stops running and the red light is on.

Figure5-36 Button control program

Note: The button control program is in the SCR1 program.

![Official Magician E6 training-system figure, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjGBAjsJKyDfs9CUsAsBg%2Futp-dbaf98687672546ad8d4.png?alt=media)

## Chapter 6 Application of Visual Sorting

### 1. Introduction

Based on the visual inspection of the workpiece coordinates and color recognition information, the robot transports the square workpieces (with any number of two colors ,as shown in Figure6-1) on the loading board, to the corresponding storage area in the square grooves of the loading board, with red and green workpieces placed in one column each, as shown in Figure6-2. If the number of the same colour exceeds 3, it will be stacked and placed.，

Figure6-1 rectangular workpieces

Green workpiece Red workpiece\
placement area placement area<br>

Figure6-2 Storage area

![Official Magician E6 training-system figure, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTYGi1yRDCmNdyWfeK96r%2Futp-35ee2388667a88818afc.jpg?alt=media)

![Official Magician E6 training-system figure, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpT6BJthFer0dTvvbznRd%2Futp-81088d683f1c4bb8f117.jpg?alt=media)

### 2. IO Configuration

The IO configuration of Visual Sorting is shown in Table 6-1 .

**Table 6-1 IO configuration**

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

on, as shown in Figure6-3.

Figure6-3 Turn on the E6 power switch

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to Auto, as shown in Figure6-4.

![Official Magician E6 training-system figure, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

Figure6-4 Turn on the power switch of the pump box

#### 3.1.4 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the other end to the PC.

* (2) Modify IP of the PC.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure6-5. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

![Official Magician E6 training-system figure, source page 94](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIOo2VwMNtIqj3S5oUm1e%2Futp-fb05a14080aeb7630a08.jpg?alt=media)

Figure6-5 Set IP of the PC

* (3) Connect DobotStudio Pro to the robot.

Double-click DobotStudio Pro to open the software. After you enter DobotStudio Pro, the software will automatically search for robots and displays the search results “Magician E6” on the interface. Click **Connect** on the right side of the device to connect it, as shown in Figure6-6.

Figure6-6 Connect robot

After successful connection, the software interface will refresh and display the

information about the E6 and its 3D model, as shown in Figure6-7.

![Official Magician E6 training-system figure, source page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDb5ccDkzTmqRU8BOmmx9%2Futp-ca3a257ba809811bdc70.png?alt=media)

![Official Magician E6 training-system figure, source page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI52WALexkcCkcr0KRTBC%2Futp-0a5e0c0bd67c2bffac21.png?alt=media)

Figure6-7 the information about the E6

#### 3.1.5 Enable robot

Click on the “Enable” switch in the “Magician E6” interface. Modify various parameter values according to the actual situation in the “Load enabling settings” window that pops up. Click **Enable,** as shown in Figure6-8. The Enabling switch changes to in the E6 interface.

![Official Magician E6 training-system figure, source page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

Figure6-8 Set load parameters

#### 3.1.6 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to

set the speed to 20%, as shown in Figure6-9.

Figure6-9 Set Speed

#### 3.1.7 Install suction cup tool

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro4.1 to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure6-10. It is best to adjust the coordinate value of J6 to 0°, as shown in Figure6-11.

![Official Magician E6 training-system figure, source page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

Figure6-10 The posture of installing the end tool

Figure6-11 Coordinates for installing the end tool

(2) Install the suction cup onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Figure6-12

![Official Magician E6 training-system figure, source page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhnnRnBok8zzUoTAwEEwt%2Futp-c0f6117f8a23cb7b53d2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGID1lJWubeuP8tsnZlsT%2Futp-b553235602b81b2845ed.jpg?alt=media)

Figure6-12 Install the suction cup on the end of robot

(3) Connect one end of the air pipe to the “Air” hole in the air pump box, and the

other end to the suction cup. Fix it to the robot with a tie, as shown in Figure6-13.

Figure6-13 Connect the air pipe

#### 3.1.8 Adjust the robot’s posture

Adjust the robot’s posture to a vertical position through the control panel, as shown in Figure6-14, so that the joint coordinates are {0, 0, -90, 0, 90, 0}.

![Official Magician E6 training-system figure, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzcv41juFPW7siMzWaWqI%2Futp-17f289914692994ebfa2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS9DspBiKzVSACrt6PCXW%2Futp-e540813590f6924d40b7.jpg?alt=media)

Figure6-14 Adjust the robot’s posture

#### 3.1.9 Install standard visual carrier

Install the standard visual carrier board above the conveyor belt, as shown in

Figure6-15.

Figure6-15 Install standard visual carrier board

#### 3.1.10 Connect the camera

Insert the encryption dog of Dobot VisionStudio into the computer, and then plug

the USB plug of the training platform vision (used to connect the camera) into the USB

interface of the computer.

#### 3.1.11 Turn on the light source switch

Turn on the power switch of the circular light source.

![Official Magician E6 training-system figure, source page 100](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fksw5YLQKKPrr3LO6R4x8%2Futp-90ab4ecf4d4d9d93ab9a.jpg?alt=media)

![Official Magician E6 training-system figure, source page 100](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5Ehw6wCVC09ivS9TmMUc%2Futp-f05b77dc434d53908ec5.jpg?alt=media)

#### 3.2 Debug vision program

**3.2.1 Eye-to-hand calibration**

* (1) Place the calibration board on the standard visual carrier board , as shown in

Figure6-16.

Figure6-16 Calibration board placement

Note: To avoid sliding of the calibration board, adhesive tape can be used to secure it.

* (2) Remove the suction nozzle from the suction nozzle connecting rod and install

the calibration needle, as shown in Figure6-17.

Figure6-17 Install the calibration needle

* (3) Open DobotVisionStudio and select **General Solution** .

![Official Magician E6 training-system figure, source page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA1zNOqQhn9BoCL0fKc5e%2Futp-21e2241f0933a51a6056.jpg?alt=media)

![Official Magician E6 training-system figure, source page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXBCxjt6S1RBsMEKU2bUm%2Futp-6413364cb964bf1849e5.jpg?alt=media)

(4) Establish the flow. Drag **Image Source** in Acquisition toolbox to the flow editing area, as shown in Figure6-18.

Figure6-18 Flow

①Set **0Image Source1** parameters. Double-click **0Image Source1** to set parameters. Select **Image Source** to **Camera** , as shown in Figure6-19. Click **Camera set** on the right side of **Relate Camera** to enter the corresponding page.

Figure6-19 0Image Source

②Create global camera. Click **+** on the right side of **Device List** to create **1 Global Camera1** and set the parameters of the camera. In the “Common Params” tab, click the triangle in the lower right corner of **Choose Camera** to open the drop-down list and select the camera that is currently connected to the computer. Select **Mono8** for **Pixel**

![Official Magician E6 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYh4PiYmIbqGLOjETa40i%2Futp-664e160b702aed1a395e.png?alt=media)

![Official Magician E6 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLvPgBzDlOPnsKFYOkxrk%2Futp-b09976af39162b0eff59.png?alt=media)

**Format** , as shown in Figure6-20. Click **Trigger Settings** tab, and set **Trigger Source**

to **SOFTWARE** . Then click **Confirm** , as shown in Figure6-21.

Figure6-20 Common Params

Figure6-21 Trigger Settings

In “0 Image Source” page, click the triangle in the lower right corner of **Relate**

**Camera** and select **1Global Camera1** , as shown in Figure6-22.

![Official Magician E6 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuJYKQskIO6eHS7bHKRkx%2Futp-0fc8e039b03961c8ffbb.png?alt=media)

![Official Magician E6 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxQMFOirRac9SBMYflD3G%2Futp-ebbdbf9bfdd9f3baab00.png?alt=media)

Figure6-22 Relate Camera

③Click (Continuously) on the toolbar to adjust the aperture and focus ring

of the lens and the exposure time of the camera until you can see a clear image in the image display area. The image acquisition result is shown in Figure6-23.

Figure6-23 Image acquisition result

(5) Add **CalibBoard Calib** in the flow.

Drag **CalibBoard Calib** in Calibration toolbox to the flow editing area. Connect

it with **0Image Source1** , as shown in Figure6-24.

![Official Magician E6 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fqt71AvoImgyGlPiGchWo%2Futp-e223d97ed5f4e9db8502.jpg?alt=media)

![Official Magician E6 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F05SyxvYsSkCNccpWkjOr%2Futp-d6b17ccbf095379e4cc0.png?alt=media)

Figure6-24 Flow

Note: The calibration of the calibration board is used to obtain the calibration point, and provide

the pixel coordinates of the calibration point for N-point calibration.

* (6) Add **N-point Calibration** in the flow.

①Drag **N-point Calibration** in Calibration toolbox to the flow editing area.

Connect it with **2CalibBoard Calib1** . Click (Once) in the toolbar. Nine calibration points and their calibration sequence are shown automatically in the image display area, as shown in Figure6-25.

Figure6-25 Process of hand eye calibration scheme and calibration sequence

②Set **3N-point Calibration** basic parameters. Double-click **3N-point Calibration** to set basic parameters. In “Basic Params” page, set **Translation Number**

to **9** by default, as shown in Figure6-26. Click on the right side of **Rotation**

**Number** to edit the calibration points, as shown in Figure6-27.

![Official Magician E6 training-system figure, source page 105](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLDGaz3nzOu6ry6DhD2vd%2Futp-919bb8ad223584066b28.jpg?alt=media)

Figure6-26 3N-Point Calibration

Figure6-27 Edit Calibration Points

In “Edit Calibration Points” page, exchange Line 3 (ID: 3) and Line 5 (ID: 5) data,

as shown in Figure6-28.

![Official Magician E6 training-system figure, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2ipLPIgghuX0PjKbiTqK%2Futp-8461ac5c4cee840b20f5.png?alt=media)

![Official Magician E6 training-system figure, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtXZZZNHASkf0gg82pSgl%2Futp-b20f2adbc901cb2af5c1.png?alt=media)

Figure6-28 “Edit Calibration Points” after data exchange

Click (Once), and you will see that the calibration sequence in the image display area turn to “ ” shape, as shown in Figure6-29.

Figure6-29 Calibration sequence after data exchange

③Switch to DobotStudio Pro, control the robot to move according to the sequence

of the nine points.

Move the robot to the first calibration point, and read the physical coordinates X and Y of the first point in DobotStudio Pro, as shown in Figure6-30. Fill the X and Y values in the physical coordinates of the first line in “Edit Calibration Points” page in DobotVisionStudio, as shown in Figure6-31. Obtain the physical coordinates of the remaining 8 points and fill in “Edit Calibration Points” page, as shown in Figure6-32.

![Official Magician E6 training-system figure, source page 107](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOhvMGJbWiemGAmBiZzBq%2Futp-d348ca27eda7059f8b60.png?alt=media)

![Official Magician E6 training-system figure, source page 107](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfoUN88BQPrnBTOnowT7g%2Futp-79ff44f2cb6db5db3ef2.jpg?alt=media)

Figure6-30 Locate the first calibration point

Figure6-31 Fill in the physical coordinates of the first calibration point

![Official Magician E6 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD8JdCAKz6nX1TW9vNOfT%2Futp-2f6cc0198964836e8239.jpg?alt=media)

![Official Magician E6 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx0qjwTvOiyBhJ258PWFH%2Futp-c25a86865998bba5b99c.png?alt=media)

![Official Magician E6 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvavAKIDaIlZnGdfMeNu5%2Futp-82026f23ad61cf09e1b7.png?alt=media)

Figure6-32 Physical coordinates of 9 calibration points

④Create the calibration file. After editing the calibration points, click in “Basic Params” page. Click **Create Calibration File** to export the calibration file to local and name it, as shown in Figure6-33.

Figure6-33 Create calibration file

(7) Add **Calibration Transformation** in the flow. After establishing the calibration file, it is necessary to verify whether the calibration is accurate.

Drag **Calibration Transformation** in Calculation toolbox to the flow editing area, and connect it with **3N-point Calibration1** , as shown in Figure6-34.

![Official Magician E6 training-system figure, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPSxMyzujIQNu52Fcxcrg%2Futp-417eec82e6e80abcd8de.png?alt=media)

![Official Magician E6 training-system figure, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVwEwlIrOqkXnDMNVpjPm%2Futp-8dfc5b1683f69d913a5b.png?alt=media)

Figure6-34 Flow

②Set 4Calibration Transformation parameters. In “Basic Params” page, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** . Set **Load Calibration File** to **Calibration file** generated from 3N-point Calibration1, as shown in Figure6-35.

Figure6-35 Set “4Calibration Transformation” parameters

③Click (Once), and check whether the nine coordinates after 4Calibration Transformation1 are consistent with the physical coordinates in 3N-point Calibration1, as shown in Figure6-36. If the difference in values is very small, it indicates that the calibration is accurate. Otherwise, you need to re-calibrate.

![Official Magician E6 training-system figure, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnYRiVeX96GJLzlRiUhtj%2Futp-9c13af414e9b584b0f5f.png?alt=media)

Figure6-36 Comparison result

Note: The converted sequence numbers “3” and “5” need to be compared with the “5” and “3” of “Edit Calibration Points”.

After the calibration is completed, it is necessary to remove the calibration needle from the suction nozzle connecting rod and install the suction nozzle.

#### 3.2.2 Import vision program

Open DobotVisionStudio 4.1.2 and select **General Solution** . Select **Open** in the toolbar. Find the Visual Sorting program and click **Open** . The imported vision program is shown in Figure6-37.

![Official Magician E6 training-system figure, source page 111](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ficf2IzFNid0avxfg8HzQ%2Futp-7abf529b053a764882d6.jpg?alt=media)

Figure6-37 Vision program

#### 3.2.3 Place detection object

Place seven rectangular workpieces of two different colours in the detection field

of view, as shown in Figure6-38.

Figure6-38 Place seven workpieces within the detection field of view

#### 3.2.4 Debug program parameters

* (1) Debug **0Image Source** parameters.

Click (Once). Select **0Image Source1** and observe whether the image is clear.

![Official Magician E6 training-system figure, source page 112](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxLvseMezvrChmr8MW2Ix%2Futp-ed7421dd1da38ccd7b2f.png?alt=media)

![Official Magician E6 training-system figure, source page 112](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ4byAS9oQWkRJ8odV5RJ%2Futp-f98d16579462e03b6508.jpg?alt=media)

If the image is not clear or there is no image, you need to reset the parameters according to the method described in 3.2.1. When setting the parameters, set **Pixel Format** to **RGB8** . The image collected by the camera is shown in Figure6-39.

Figure6-39 Collected image

* (2) Debug **2Color Transformation1** parameters.

Double-click **2Color Transformation1** to check whether **Transfer Type** is **RGB**

**to Grayscale** , as shown in Figure6-40. If not, modify as the figure.

Figure6-40 2Color Transformation

Click (Once). The execution result of 2Color Transformation1 is shown in

![Official Magician E6 training-system figure, source page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHSuaKWcr8yILPrvpye8M%2Futp-b3af7e9f237a35aa5982.jpg?alt=media)

![Official Magician E6 training-system figure, source page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFcHAem2U4d4EtMoM5QBi%2Futp-de00b82901d86f1a41d0.png?alt=media)

Figure6-41.

Figure6-41 Grayscale Image

* (3) Debug **3Fast Match1** parameters.

Double-click **3Fast Match1** . Click **Run Params** and modify **Max Number to find** to **7** (Number of rectangular workpieces). Then click **Execute** and observe whether all the workpieces are recognized in the image display area, as shown in Figure6-42.

Figure6-42 Run Params

If all the workpieces are recognized, use the original model. Otherwise, you need

to re-create the feature model, as described below.

* ①Enter “Feature Model” page. Delete the original model and then click **Create** ,

![Official Magician E6 training-system figure, source page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBSiiIkOaQBKFAYdRn1Vn%2Futp-f89505adb0582ddfac72.jpg?alt=media)

![Official Magician E6 training-system figure, source page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7rbH7UjXrHNvCIUUdob8%2Futp-06db4713b06fb26bf633.png?alt=media)

as shown in Figure6-43.

Figure6-43 Feature Model

②In ModelSettings page, click **Current Image** . Click (Create Rect Mask), select the corresponding area in the image and set corresponding model parameters (generally default). Then click (Build Model) and click **Confirm** , as shown in Figure6-44.

Figure6-44 ModelSettings

③After creating the model, click **Execute** and **Confirm** , as shown in Figure6-45.

![Official Magician E6 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F46J7jDhAOeibwsoF4HXq%2Futp-2b71709252c4aa561e89.png?alt=media)

![Official Magician E6 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8QL75o6C7b8VUhIHVAoE%2Futp-e87a9987ee16366fc92a.jpg?alt=media)

Figure6-45 Result

Note: If not all the workpieces can be recognized, maybe it is caused by the light. You can change the threshold value.

④Double-click **3Fast Match1** . Click **Run Params** and modify **Max Number to find** to **1** . Then click **Execute** , and the recognized workpiece is shown in the image display area. Click **Confirm** , as shown in Figure6-46.

Figure6-46 Result

* (4) Debug 4Calibration Transformation1 parameters.

Double-click **4Calibration Transformation1** . Check whether **Coord Point** is

3 **Fast Match1.Match Point** . Load the saved calibration file, as shown in Figure6-47.

![Official Magician E6 training-system figure, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCV0PKSHRhsMstwofx2k8%2Futp-5b5f7a2789cf6228a299.jpg?alt=media)

![Official Magician E6 training-system figure, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWVnlUetVneWSbvc4XtYt%2Futp-b36457b57bb42447ba79.jpg?alt=media)

Figure6-47 Basic Params

Click **Execute** and **Confirm** , and the physical coordinates of the workpieces are

displayed in the result display area, as shown in Figure6-48.

Figure6-48 Result

![Official Magician E6 training-system figure, source page 117](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fkjo9LB7rV7YHjn5iMi7H%2Futp-050d6998a3f37261e129.jpg?alt=media)

![Official Magician E6 training-system figure, source page 117](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2S4HPjLK4vaN7AWnscQQ%2Futp-e44ae64c1132e76e12b5.png?alt=media)

![Official Magician E6 training-system figure, source page 117](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS5mysJvHyuHlvgimttS0%2Futp-edb45fa0a40f384622bc.png?alt=media)

(5) Debug **5Color Recognition1** parameters.

Click (Once). Select **5Color Recognition1** and modify the image display to **ImageSource1.OutputImage** . Observe whether the colour of the image is recognized correctly, as shown in Figure6-49.

Figure6-49 Result

If the colours are recognized incorrectly, you need to debug according to the

following method.

①Double click **5Color Recognition1** . Check whether **Input Source** and **ROI**

**Area** in “Basic Params” page are set as Figure6-50.

![Official Magician E6 training-system figure, source page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzc4RbmMgTUbzB0Z7dSf4%2Futp-96e1778ed958757c75ff.jpg?alt=media)

Figure6-50 Basic Params

②In “Colour Model” page, delete the existing models. Click **+** to re-create models, as shown in Figure6-51.

Figure6-51 Colour Model

③Create a red model. In **ModelSettings** page, click (add the current image),

then click **+** on the right side of **Label List** to add a new label and change the label

![Official Magician E6 training-system figure, source page 119](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbszTbkmkMlD88ckEcixf%2Futp-27eebcb52c30f71e5cd8.png?alt=media)

![Official Magician E6 training-system figure, source page 119](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFxMlRUPV0PDsk7mBSZAq%2Futp-f462ebd2851687b0c65f.png?alt=media)

name. Click in the toolbar and drag a rectangular mask on the current image. Then click **Add To Label** and you will see the added red model on the right side, as shown in Figure6-52.

Figure6-52 Create red model

Note: The material may be reflective due to the light which could result in a difference in colour.

In this case, you need to create several red models.

④Create the green models as shown in Figure6-53 using the same method. Click **Confirm** to return to “Colour Model” page.

![Official Magician E6 training-system figure, source page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmS1qEVHG2BoF2wV5TBVd%2Futp-dce0aa610bdafc572a14.jpg?alt=media)

Figure6-53 Create green models

⑤Click **Execute** and **Confirm.** The recognized colour of the workpieces is shown

in the result display area, as shown in Figure6-54.

Figure6-54 Result

(6) Debug **6Variable Calculation1** parameters.

Click (Once). Select **6Variable Calculation1** and check whether **var0** which

in the display area and the **MatchBoxAngle** value of **3Fast Match** are opposite values, as shown in Figure6-55.

![Official Magician E6 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWLxdOoKy3mrlwolpihDN%2Futp-e9a4bb76bab5e8973f2d.jpg?alt=media)

![Official Magician E6 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZiFzvP8KXsEIqOoT2zyz%2Futp-f095fa1a89b23b626bec.jpg?alt=media)

![Official Magician E6 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDBLlBydpHriPPZu7HeHq%2Futp-af941278f8fa31911373.jpg?alt=media)

Figure6-55 Comparison result

If the values are not opposite, you need to debug according to the following method.

①Double-click **6Variable Calculation1** . Click below **Expression** to enter

**Var0** page. Click and select **3Fast Match1**  **MatchRect**  **MatchBoxAngle** , and then plus “-” in front of the variable, that is, to get the negative value of the angle. Then click **Save** to return to the “Basic Params” page, as shown in Figure6-56.

Figure6-56 Expressions

![Official Magician E6 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEu33VWg0Uv3sK9NYyEi8%2Futp-4dcec1ca86e17fbb32bb.jpg?alt=media)

![Official Magician E6 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUBKpdvvdAlvZbqlJiNH5%2Futp-3ae115c459d6f3b57be2.png?alt=media)

* ②Click **Execute** and **Confirm** and you will see the angle value, as shown in

Figure6-57.

Figure6-57 Result

* (7) Debug **7Format1** parameters

Click (Once). Select **7Format1** and observe whether the result display area

shows the format result as Figure6-58.

![Official Magician E6 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLla5OG77XrUEq5YfdKgQ%2Futp-9ea2709fc3cb41e05eea.jpg?alt=media)

Figure6-58 Result

If not, you need to debug according to the following method.

* ①Double-click **7Format1** . In “Basic Params” page, as shown in Figure6-59, click

**+** to add a row. Click (InsertSubscription) and select **5Color Recognition1**  **Best**

**Matched Name** .

![Official Magician E6 training-system figure, source page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn56GcVfdLnD1OI7VG2qB%2Futp-dc0c7765d93523444746.jpg?alt=media)

Figure6-59 Basic Params

②Then click **T** and enter “,”. Click and select **4 Calibration Transformation1**  **OutputPoint**  **TransPointX** . Insert “<4 Calibration Transformation1.TransPointY(%1.3f)>\[0]” “,”. “<6 Variable Calculation1.var0(%1.3f)>\[0]” “,” “<3 Fast Match1.ModuStatus(%0d)>\[0]

following the same method. The format parameters are shown in Figure6-60.

Figure6-60 Format Params

(8) Set “Communication Management” parameters.

![Official Magician E6 training-system figure, source page 125](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd335unODVoMoSJCtiew5%2Futp-4deb6e034fb6c1ff265c.png?alt=media)

![Official Magician E6 training-system figure, source page 125](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgYvPhFBbTeNhYP6uFXT9%2Futp-6d457cb78cf03f49239d.png?alt=media)

Click in the quick toolbar to enter “Communication Management” page. Check whether there is established TCP Server and whether its parameters are consistent with the figure below. If not consistent, modify as Figure6-61.

Figure6-61 Communication Management

If there is no **TCP Server** , you need to create one, as described below.

Click beside **Device Lists** to add devices. Select **Protocol Type** to **TCP Server,** and modify **Device Name** (TCP Server by default), **Local IP** and **Local Port** according to the actual condition, and click **Create** , as shown in Figure6-62. After creating the communication device, switch on **1TCP Server** , as shown in Figure6-63.

![Official Magician E6 training-system figure, source page 126](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjiKPrhe7VwkXa4UVAUp6%2Futp-f50e08df10a1531c4995.png?alt=media)

Figure6-62 Add device

Figure6-63 TCP Server

* (9) Debug **8Send Data1** parameters.

Double-click **8Send Data1** and check whether the parameters are shown as Figure6-64. If not, modify as the figure. Set **Output To** Transient **Communication Device** , **Communication Device** to **1 TCP Server** , and **Send Data1** to **7Format1.format\_out\[]** . Then click **Confirm** .

![Official Magician E6 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW9lgwD3wRvzvoR6tVmOq%2Futp-29d56a601c7da5beb3ce.jpg?alt=media)

![Official Magician E6 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYMxaD9hRI0XWWmsFHmL8%2Futp-88697e4bb06b31f593df.png?alt=media)

Figure6-64 Send Data

* (10) Global trigger settings

Click in the quick toolbar to enter “Global Trigger” page. In “String Trigger” page, check whether the string trigger setting is shown as Figure6-65 (String is void; Mode is Mismatched; Trigger Configuration is All Process).

Figure6-65 Set Global Trigger parameters

#### 3.2.5 Save program

Click in the toolbar to save the program. If you need to save the program elsewhere on your local computer, click **File** > **Save as** , select the saving path and enter the name of the project.

![Official Magician E6 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx1IPS5UFrpEHtPojPwdN%2Futp-0e9b3058365b64bd00ef.jpg?alt=media)

![Official Magician E6 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhR1OAIWUwjShffP6VhZW%2Futp-0a86b65db70ed8fe13f7.png?alt=media)

#### 3.3 Debug robot program

#### 3.3.1 Import program

* (1) On the Home screen of DobotStudio Pro software, click **Application > Script**

**programming** and enter “Programming ” interface, as shown in Figure6-66.

Figure6-66 Enter “Programming ” interface

* (2) Click to open File menu and select “Import project”, as shown in

Figure6-67. Select **Vision\_Sorting** folder, and click **Open** . Now the **Vision\_Sorting** program has been imported into DobotStudio Pro, as shown in Figure6-68.

Figure6-67 Import project

![Official Magician E6 training-system figure, source page 129](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsQS744H6iw1U1UAQ5ZJc%2Futp-5bc85ae512fb87b2a0dc.jpg?alt=media)

![Official Magician E6 training-system figure, source page 129](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOsCydw1CqYPv8Nk6PwIG%2Futp-d9289b42d88012871292.png?alt=media)

Figure6-68 Project imported

#### 3.3.2 Save program

Click and enter a project name in the pop-up dialog box. Click **Save** , as

shown in Figure6-69.

Figure6-69 Save program

#### 3.3.3 Set communication

Ensure that the IP address and port of TCP server in the robot program are consistent with those in vision communication settings, that is, set IP address in the robot program to 192.168.5.18. Set port to 4001, as shown in Figure6-70.

![Official Magician E6 training-system figure, source page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDBTmKzPjb4HrClcVmFq5%2Futp-b1e1c4f6d3d723a8d3de.png?alt=media)

![Official Magician E6 training-system figure, source page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuB9tdKGtuyu4MHhZxafy%2Futp-38a2a42baa6a3b613b7b.png?alt=media)

Figure6-70 Set communication

#### 3.3.4 Program debugging

* (1) Modify Z coordinate of the picking point.

Jog the robot make the suction cup slightly touch the surface of the workpiece, as shown in Figure6-71. Then read the current Z coordinate of the robot, as shown in Figure6-72. Modify the Z coordinate in the command “local GetProductPos = {pose = {move\_x, move\_y, 222.2,P1.pose\[4],P1.pose\[5], move\_r} }” of the pickup sub-

program to the current Z coordinate.

Figure6-71 Picking point

![Official Magician E6 training-system figure, source page 131](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1w1oHFzrTZXA566fGeos%2Futp-3677849cd31f334fdc24.jpg?alt=media)

Figure6-72 Z coordinate of picking point

(2) Modify Z coordinate over the picking point.

Jog the robot to lift some distance, as shown in Figure6-73. Then read the Z coordinate of the robot, as shown in Figure6-74. Modify the Z coordinate in the command “local GetProductPosUp = {pose = {move\_x, move\_y, 252.2, P1.pose\[4], P1.pose\[5], move\_r} }” of the pickup sub-program to the current Z coordinate.

![Official Magician E6 training-system figure, source page 132](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiQhDwZ9JR9IR1390yy2b%2Futp-9f888d7f5ad3dca889c8.jpg?alt=media)

Figure6-73 Over picking point

Figure6-74 Z coordinate over picking point

#### 3.3.5 Debug points

The Visual Sorting demo includes seven major points, as described below.

* (1) Update the safe point P1.

Jog the robot to a position between the conveyor belt and the storage area, as

shown in Figure6-75. Click **Points** to enter the Points interface. Firstly select P1.Then

![Official Magician E6 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFWrK3DxsCDDKVHAwQqZ0%2Futp-ae7b59f57cde6e477b23.jpg?alt=media)

![Official Magician E6 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5Cn8tAPOX3vJQJmInMU3%2Futp-00a501321a9a920ff229.jpg?alt=media)

click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P1 point,

as shown in Figure6-76. Click and save the program.

Figure6-75 Locate Point P1

Figure6-76 Update Point P1

(2) Update the first red workpiece placing point P2.

①Click to make the robot suck a workpiece according to the coordinates sent by the vision system. Then click immediately. Jog the robot to the first red workpiece placing point in the storage area, as shown in Figure6-77. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the red workpiece is placed into the groove accurately. If not,

![Official Magician E6 training-system figure, source page 134](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbQPxb5g3gsDZkgu14frS%2Futp-8b0bcc255b7212743581.jpg?alt=media)

![Official Magician E6 training-system figure, source page 134](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEgEhdMwV8yGJxFiMS4W0%2Futp-b3fd43aff12633c6db4d.jpg?alt=media)

you need to re-debug the point.

Figure6-77 Locate the first red workpiece placing point P2

②Open **Points** page. Select **P2** and click **Cover** , as shown in Figure6-78. Then

click **Cover** in the pop-up Tips dialog box again to update P2. Click and save the

program.

Figure6-78 Update P2

(3) Update the green workpiece placing point P3.

①Click to make the robot suck a workpiece according to the coordinates sent by the vision system. Then click immediately. Jog the robot to the first green workpiece placing point in the storage area, as shown in Figure6-79. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set

![Official Magician E6 training-system figure, source page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNlQgOm3heu9s38JQT9VO%2Futp-cadb612ce8558c66aeba.jpg?alt=media)

![Official Magician E6 training-system figure, source page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fog6YDVM27CPc3mL9MOYI%2Futp-1496736b9f964b0bbf8a.png?alt=media)

**DO\_10** to **OFF** and observe whether the green workpiece is placed into the groove accurately. If not, you need to re-debug the point.

Figure6-79 Locate the green workpiece placing point P3

②Open **Points** page. Select **P3** and click **Cover** , as shown in Figure6-80. Then

click **Cover** in the pop-up Tips dialog box again to update P3. Click and save the

program.

Figure6-80 Update P3

#### 3.3.6 Run program

Click , and check whether the program is running as follows:

The vision system detects the colour and position data of workpiece, and transmits

these information to the robot. After obtaining the information, the robot moves to the

![Official Magician E6 training-system figure, source page 136](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCfSK2koOgGwtUAPk29Lc%2Futp-d5c8a363716e9246ba3c.jpg?alt=media)

![Official Magician E6 training-system figure, source page 136](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKzeb0fphSCdF9yrIZHgY%2Futp-6d16e03800c24ed0643f.png?alt=media)

detection area to suck the workpieces, sorts and places them in the corresponding colour

area. The sorting effect is shown in Figure6-81.

Figure6-81 Sorting finished

#### 3.3.7 Export program

Click to open File menu and select “Export project”. Select the path to save the program. Then enter a project name in the pop-up dialog box.

### 4. Key Program Description

#### 4.1 Vision program description

The following text only explains the main functions of each algorithm tool in the program. Please refer to the visual project file for the specific parameter settings of the algorithm tool.

The vision program is shown in Figure6-82. **0Image Source1** is mainly used for image acquisition. During the system operation, the camera takes photos immediately after the vision software receives the trigger signal sent by the robot. The images acquired are all coloured images because colour recognition is to be performed. **2Color Transformation1** is mainly used for converting colour images into grayscale images to locate grayscale images. **3Fast Match1** is mainly used for locating grayscale images, and to obtain the image coordinates and matching angle of the detected object. **4Calibration Transformation1** is used for transforming the image coordinates

![Official Magician E6 training-system figure, source page 137](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsLGl0aacjw9h4qpkPvII%2Futp-3fb885f0f82610a33528.jpg?alt=media)

obtained by **3Fast Match1** into actual physical coordinates. **5Color Recognition1** is used for creating a colour model to recognize the colour of workpieces so that sorting can be performed by colour. **6Variable Calculation1** is used for correcting the matching angle. **7Format1** is used for summarizing and defining the format of the information that the vision system needs to send to the robot. **8Send Data1** is used for sending the contents of **7Format1** to the robot.

Figure6-82 Vision program

#### 4.2 Robot program description

This section mainly describes the key script. For complete script, see the project in Script page.

#### 4.2.1 Character separation program

The character separation program is shown in Figure6-83.

Figure6-83 Character separation program

#### 4.2.2 Data transmission program

The data transmission program is shown in Figure6-84 which mainly sends

photography trigger signal “ok” and receives the data sent by the vision system.

Figure6-84 Data transmission program

#### 4.2.3 Robot pick-up program

The robot pick-up program is shown in Figure6-85. The main function achieved

is for the robot to analyze the information sent by the visual system and move to the

material retrieval point for material retrieval.

![Official Magician E6 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6j3y2hQQlL5lgyHhCVeF%2Futp-4d24d6e9996c9f260e8e.png?alt=media)

![Official Magician E6 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FT8YE0pHwl1EeZQY64b7R%2Futp-cb5d20f3c11e5b41e0ba.png?alt=media)

![Official Magician E6 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfhSi0AuoTwYzL0Asn7oh%2Futp-68bf89a940c4e42f6525.png?alt=media)

Figure6-85 Robot pick-up program

#### 4.2.4 Output port reset program

The output port reset program is shown in Figure6-86, which sets all output ports

to **OFF** .

Figure6-86 Output port reset program

#### 4.2.5 Create TCP client program

Create a TCP client program, as shown in Figure6-87, whose function is to create

a TCP client for communication with visual units.

Figure6-87 Create TCP client program

#### 4.2.6 Attitude adjustment program

The posture adjustment program is shown in Figure6-88, which implements the

function of adjusting the robot’s posture to the posture shown in Figure6-89.

Figure6-88 Robot attitude adjustment program

Figure6-89 Robot attitude

![Official Magician E6 training-system figure, source page 140](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9S2P6hbOaOUD8zmzdbSf%2Futp-389916c54d2a502ff91a.jpg?alt=media)

#### 4.2.7 Robot placement program

* (1) Program for placing red workpieces.

If the robot picks up the red workpiece, it moves to the placing point through the safe point (P1) to place the workpiece. Then it returns to P1, as shown in Figure6-90. P2 point is the position of the first red workpiece placement point, and the placement points of other red workpieces are calculated based on the distance between the first red workpiece placement point and each placement point to determine the corresponding placement point coordinates for each red workpiece.

Figure6-90 Red workpieces placement program

* (2) Program for placing green workpieces.

If the robot picks up the green workpiece, it moves to the placing point through the safe point (P1) to place the workpiece. Then it returns to P1, as shown in Figure691. P3 is the position of the first green workpiece placement point, and the placement points of other green workpieces are calculated based on the distance between the first green workpiece placement point and each placement point to determine the corresponding placement point coordinates for each green workpiece.

![Official Magician E6 training-system figure, source page 141](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjw3DYTq0gem3vBUqjxWL%2Futp-ba8c1155ff9b43b2aa32.png?alt=media)

Application of Visual Sorting<br>

Figure6-91 Green workpieces placement program

![Official Magician E6 training-system figure, source page 142](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwIISPvEZKnN3A78vbCL9%2Futp-af60735c585ac4836530.png?alt=media)

## Chapter 7 Application of Visual Positioning Guided

### Assembly

### 1. Introduction

The specific task of visual positioning guided assembly is for the robot to assemble six mobile chips placed on the standard vision board (Figure7-1) into the six grooves of the mobile phone model workpiece based on the chip shape and position information recognized by vision, as shown in Figure7-2.

Figure7-1 Phone chip

Figure7-2 Phone model

### 2. IO Configuration

The IO configuration of the visual positioning guided assembly demo is shown in

![Official Magician E6 training-system figure, source page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCy1tkysd5O61KRGe1Jzh%2Futp-bedd9be05882de3bf2df.jpg?alt=media)

![Official Magician E6 training-system figure, source page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8Ry7hhObgabYdYZoEvpD%2Futp-75eb2f8dcc4ed52a36e5.jpg?alt=media)

Table7-1.

**Table7-1 IO configuration**

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

on, as shown in Figure7-3.

Figure7-3 Turn on the E6 power switch

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to Auto, as shown in Figure7-4.

![Official Magician E6 training-system figure, source page 144](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjed8t1Mj6mXPhdbQrXoX%2Futp-92d94e55570945ea4d42.jpg?alt=media)

Figure7-4 Turn on the power switch of the pump box

#### 3.1.4 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the other end to the PC.

* (2) Modify IP of the PC.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure7-5. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

![Official Magician E6 training-system figure, source page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIOo2VwMNtIqj3S5oUm1e%2Futp-fb05a14080aeb7630a08.jpg?alt=media)

Figure7-5 Set IP of the PC

(3) Connect DobotStudio Pro to the robot.

Double-click DobotStudio Pro to open the software. After you enter DobotStudio Pro, the software will automatically search for robots and displays the search results “Magician E6” on the interface. Click **Connect** on the right side of the device to connect it, as shown in Figure7-6.

Figure7-6 Connect robot

After successful connection, the software interface will refresh and display the

information about the E6 and its 3D model, as shown in Figure7-7.

![Official Magician E6 training-system figure, source page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDb5ccDkzTmqRU8BOmmx9%2Futp-ca3a257ba809811bdc70.png?alt=media)

![Official Magician E6 training-system figure, source page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI52WALexkcCkcr0KRTBC%2Futp-0a5e0c0bd67c2bffac21.png?alt=media)

Figure7-7 the information about the E6

#### 3.1.5 Enable robot

Click on the “Enable” switch in the “Magician E6” interface. Modify various parameter values according to the actual situation in the “Load enabling settings” window that pops up. Click Enable, as shown in Figure7-8. The Enabling switch

changes to in the E6 interface..

![Official Magician E6 training-system figure, source page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

Figure7-8 Set load parameters

#### 3.1.6 Set Speed

Drag the “Speed” drag bar on the top toolbar of the DobotStudio Pro interface to

set the speed to 20%, as shown in Figure7-9.

Figure7-9 Set Speed

#### 3.1.7 Install suction cup tool

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro4.1 to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Figure7-10. It is best to adjust the coordinate value of J6 to 0°, as shown in Figure7-11.

![Official Magician E6 training-system figure, source page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

Figure7-10 The posture of installing the end tool

Figure7-11 Coordinates for installing the end tool

(2) Install the suction cup onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Figure7-12.

![Official Magician E6 training-system figure, source page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4YCH0hDYQtwlUfbycbrL%2Futp-66158be50749ed75a504.jpg?alt=media)

![Official Magician E6 training-system figure, source page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGID1lJWubeuP8tsnZlsT%2Futp-b553235602b81b2845ed.jpg?alt=media)

Figure7-12 Install the suction cup on the end of robot

(3) Connect one end of the air pipe to the “Air” hole in the air pump box, and the

other end to the suction cup. Fix it to the robot with a tie, as shown in Figure7-13.

Figure7-13 Connect the air pipe

#### 3.1.8 Adjust the robot’s posture

Adjust the robot’s posture to a vertical position through the control panel, as shown in Figure7-14, so that the joint coordinates are {0, 0, -90, 0, 90, 0}.

![Official Magician E6 training-system figure, source page 150](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzcv41juFPW7siMzWaWqI%2Futp-17f289914692994ebfa2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 150](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGHMloBxWCbCJ7Vzxmw3m%2Futp-748440c039c3f49da81b.jpg?alt=media)

Figure7-14 Adjust the robot's posture

#### 3.1.9 Install standard visual carrier

Install the standard visual carrier board above the conveyor belt, as shown in

Figure7-15.

Figure7-15 Install standard visual carrier board

#### 3.1.10 Install the mobile phone model workpiece loading plate

Install the mobile phone model workpiece loading plate into the storage area, as shown in Figure7-16. Place the mobile phone model workpiece into the mobile phone model workpiece loading plate, as shown in Figure7-17.

![Official Magician E6 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fksw5YLQKKPrr3LO6R4x8%2Futp-90ab4ecf4d4d9d93ab9a.jpg?alt=media)

![Official Magician E6 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5Ehw6wCVC09ivS9TmMUc%2Futp-f05b77dc434d53908ec5.jpg?alt=media)

Figure7-16 Installation of mobile phone model workpiece loading board

Figure7-17 Place mobile phone model workpiece

#### 3.1.11 Connect the camera

Insert the encryption dog of Dobot VisionStudio into the computer, and then plug the USB plug of the training platform vision (used to connect the camera) into the USB

interface of the computer.

#### 3.1.12 Turn on the light source switch

Turn on the power switch of the circular light source.

#### 3.2 Debug vision program

#### 3.2.1 Eye-to-hand calibration

(1) Place the calibration board on the standard vision board, as shown in Figure7-

18.

![Official Magician E6 training-system figure, source page 152](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ftt3VG8vIs3OKbIoAL6Iw%2Futp-7cf6ea55e2bc2c1064ed.jpg?alt=media)

![Official Magician E6 training-system figure, source page 152](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FT4f1aQ2LKgJT4RRLeYao%2Futp-c34caa2cf1e13bda97e1.jpg?alt=media)

Figure7-18 Place the Calibration board

Note: To avoid sliding of the calibration board, adhesive tape can be used to secure it.

(2) Remove the suction nozzle from the suction nozzle connecting rod and install

the calibration needle, as shown in Figure7-19.

Figure7-19 Install the calibration needle

(3) Open **DobotVisionStudio** and select **General Solution** .

* (4) Establish the flow. Drag **Image Source** in Acquisition toolbox to the flow

editing area, as shown in Figure7-20.

![Official Magician E6 training-system figure, source page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA1zNOqQhn9BoCL0fKc5e%2Futp-21e2241f0933a51a6056.jpg?alt=media)

![Official Magician E6 training-system figure, source page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqZvNJtbu2RGbU7HHe7WT%2Futp-a256de74bd19b5bca89a.jpg?alt=media)

Figure7-20 Flow

①Set **0Image Source1** parameters. Double-click **0Image Source1** to set parameters. Select **Image Source** to **Camera** , as shown in Figure7-21. Click **Camera set** on the right side of **Relate Camera** to enter the corresponding page.

Figure7-21 Set Image source parameter

②Create the global camera. Click **+** on the right side of **Device List** to create **1 Global Camera1** and set the parameters of the camera. In the “Common Params” tab, click the triangle in the lower right corner of **Choose Camera** to open the drop-down list and select the camera that is currently connected to the computer. Select **Mono8** for **Pixel Format** , as shown in Figure7-22. Click “Trigger Settings” tab, and set **Trigger Source** to **SOFTWARE** . Then click **Confirm** , as shown in Figure7-23. In “0 Image Source” page, click the triangle in the lower right corner of **Relate Camera** and select

![Official Magician E6 training-system figure, source page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FF0E85xjk21YLFriuhZN7%2Futp-a77868a0e6b5f2211361.jpg?alt=media)

![Official Magician E6 training-system figure, source page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGFglOUzksRl3ABePSI4h%2Futp-cb90e18447e2a540ca2b.png?alt=media)

* **1Global Camera1** , as shown in Figure7-24.

Figure7-22 Set “Common Parameters”

Figure7-23 Set “Trigger settings”

Figure7-24 Relate Camera

③Click (Continuously) to adjust the aperture and focus ring of the lens and

![Official Magician E6 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxQMFOirRac9SBMYflD3G%2Futp-ebbdbf9bfdd9f3baab00.png?alt=media)

![Official Magician E6 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuJYKQskIO6eHS7bHKRkx%2Futp-0fc8e039b03961c8ffbb.png?alt=media)

![Official Magician E6 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F05SyxvYsSkCNccpWkjOr%2Futp-d6b17ccbf095379e4cc0.png?alt=media)

the exposure time of the camera until you can see a clear image in the image display

area. The image acquisition result is shown in Figure7-25.

Figure7-25 Image acquisition result

* (5) Add **CalibBoard Calib** in the flow.

Drag **CalibBoard Calib** in Calibration toolbox to the flow editing area and connect it with **0Image Source1** , as shown in Figure7-26.

Figure7-26 Flow

Note: The calibration of the calibration board is used to obtain the calibration point, and provide

the pixel coordinates of the calibration point for N-point calibration.

* (6) Add **N-point Calibration** in the flow.
* ①Drag **N-point Calibration** in Calibration toolbox to the flow editing area, and

connect it with **2CalibBoard Calib1** . Click (Once) in the toolbar, and nine calibration points and their calibration sequence are shown automatically in the image display area, as shown in Figure7-27.

![Official Magician E6 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdDa21sPLcOFT3hOLacqE%2Futp-fd0d0c14f1df2383fd4f.jpg?alt=media)

**Application of Visual Positioning Guided Assembly**

Figure7-27 Flow and calibration sequence

②Set **3N-point Calibration1** basic parameters. Double-click **3N-point Calibration** to set basic parameters. In “Basic Params” page, set **Translation Number** to **9** by default, as shown in Figure7-28. Click on the right side of **Rotation Number** to edit the calibration points, as shown in Figure7-29.

Figure7-28 Set “3N-point calibration” parameter

![Official Magician E6 training-system figure, source page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLDGaz3nzOu6ry6DhD2vd%2Futp-919bb8ad223584066b28.jpg?alt=media)

![Official Magician E6 training-system figure, source page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtXZZZNHASkf0gg82pSgl%2Futp-b20f2adbc901cb2af5c1.png?alt=media)

Figure7-29 Edit Calibration Points

In “Edit Calibration Points” page, exchange Line 3 (ID: 3) and Line 5 (ID: 5) data,

as shown in Figure7-30.

Figure7-30 “Edit Calibration Points” after data exchange

Click (Once) and you will see that the calibration sequence in the image display area turns to “ ”, as shown in Figure7-31.

![Official Magician E6 training-system figure, source page 158](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2ipLPIgghuX0PjKbiTqK%2Futp-8461ac5c4cee840b20f5.png?alt=media)

![Official Magician E6 training-system figure, source page 158](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOhvMGJbWiemGAmBiZzBq%2Futp-d348ca27eda7059f8b60.png?alt=media)

**Application of Visual Positioning Guided Assembly**

Figure7-31 Calibration sequence after data exchange

③Switch to the DobotStudio Pro software and control the robot to move in the order of 9 calibration points.

Firstly, control the robot to reach the first calibration point, and then read the physical coordinates X and Y of the first point in the DobotStudio Pro software, as shown in Figure7-32. Fill the X and Y values into the physical coordinates of the first line of “Edit Calibration Points” in the DobotVisionStudio software, respectively, as shown in Figure7-33. Follow the same operation to obtain the physical coordinate values of the remaining 8 points and fill them in the “Edit Calibration Points” table in the DobotVisionStudio software, as shown in Figure7-34.

Figure7-32 Locate the first calibration point

![Official Magician E6 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNhp42Ifoy40IfvuNZi0v%2Futp-894880f012ef2b3752d2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQUSdD6kLJzib3hPEC4ei%2Futp-6467c794dcff34a6c8ad.jpg?alt=media)

![Official Magician E6 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx0qjwTvOiyBhJ258PWFH%2Futp-c25a86865998bba5b99c.png?alt=media)

Figure7-33 Fill in the physical coordinates of the first calibration point

Figure7-34 Physical coordinates of 9 calibration points

④Create calibration files. After editing the calibration points, the robot is moved

to a position that does not affect visual photography through jog control. Click (Once). Click **Basic Params** tab of **3N-point Calibration** . Click **Create Calibration File** to export the calibration file to local and name it, as shown in Figure7-35.

![Official Magician E6 training-system figure, source page 160](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvavAKIDaIlZnGdfMeNu5%2Futp-82026f23ad61cf09e1b7.png?alt=media)

![Official Magician E6 training-system figure, source page 160](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPSxMyzujIQNu52Fcxcrg%2Futp-417eec82e6e80abcd8de.png?alt=media)

Figure7-35 Create calibration file

* (7) Add **Calibration Transformation** in the flow.

①Verify whether the calibration is accurate. Drag **Calibration Transformation**

in **Calculation** toolbox to the flow editing area and connect it with **3N-point Calibration1** , as shown in Figure7-36.

Figure7-36 Flow

②Set **4Calibration Transformation1** parameters. In “Basic Params” page, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** , **Load Calibration File** to **Calibration file** generated from 3N-point Calibration1, as shown in Figure7-37.

![Official Magician E6 training-system figure, source page 161](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVwEwlIrOqkXnDMNVpjPm%2Futp-8dfc5b1683f69d913a5b.png?alt=media)

Figure7-37 Set “4Calibration Transformation” parameters

③Click (Once) and check whether the nine coordinates after 4Calibration Transformation1（as shown in Figure7-38） are consistent with the physical coordinates in 3N-point Calibration1. If the difference in values is very small, it indicates that the calibration is accurate. Otherwise, you need to re-calibrate.

Figure7-38 Compare Results

After the calibration is completed, it is necessary to remove the calibration needle

from the suction nozzle connecting rod and replace it with a suction nozzle.

![Official Magician E6 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnYRiVeX96GJLzlRiUhtj%2Futp-9c13af414e9b584b0f5f.png?alt=media)

![Official Magician E6 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ficf2IzFNid0avxfg8HzQ%2Futp-7abf529b053a764882d6.jpg?alt=media)

#### 3.2.2 Import vision program

Open **DobotVisionStudio 4.1.2** and select **General Solution** . Select **Open** in the toolbar. Find the visual positioning guided assembly program and click **Open** . The imported vision program is shown in Figure7-39.

Figure7-39 Vision program

#### 3.2.3 Place phone chips

Place six chips within the detection vision, as shown in Figure7-40.

![Official Magician E6 training-system figure, source page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbgHHcJp6EURCMZxyQpWG%2Futp-2665f436d73070216d40.png?alt=media)

Figure7-40 Place chips within the detection view

#### 3.2.4 Debug parameters

* (1) Debug **0Image Source1** parameters.

Click (Once), select **0Image Source1** and observe whether the image is clear.

If the image is not clear or there is no image, you need to reset the parameters according

to the method described in 3.2.1.

The image acquisition result is shown in Figure7-41.

Figure7-41 Image acquisition result

* (2) Debug **2Fast Match1** parameters.

Click (Once). Select **2Fast Match1** and observe whether all types of chips can

![Official Magician E6 training-system figure, source page 164](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdD7PAl3OebUXVpIkX0QL%2Futp-fa0e724f22ca00e86b6d.jpg?alt=media)

![Official Magician E6 training-system figure, source page 164](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGf6lxDqWinCag7KnllAI%2Futp-3eb37d238b49aa32b12f.jpg?alt=media)

be recognized. If not, you need to modify “2Fast Match1” parameters, as described below.

Set **Basic Params** as shown in Figure7-42.

Figure7-42 Set 2Fast Match1 parameters

Click **Feature Model** . Select the first feature model **hexagon** and click **Edit Model** , as shown in Figure7-43. In ModelSettings page, click **Current image** . Click **Create Rect Mask** and drag to generate the rectangular mask to cover the hexagonal material. Configure the parameters in the lower right corner. Set **Scale Mode** and **Thresh Mode** according to the actual condition. Click **Build Model** to generate the feature model, as shown in Figure7-44. Finally, click **Confirm** to save the feature model.

Figure7-43 Feature Model

![Official Magician E6 training-system figure, source page 165](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJZmJ6jN8pO0UUUPLpofn%2Futp-6498c02eb7d9bcc6e44a.png?alt=media)

![Official Magician E6 training-system figure, source page 165](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0TcVRj7r5z81rwNMnImt%2Futp-2902aa02584fbac85084.png?alt=media)

Figure7-44 Update feature model

Modify the feature models of GPS chip, electronic compass, gravity sensor, WIFI chip and photosensor following the method above.

Note: The model sequence must be consistent with Figure7-43 , which corresponds to the robot program.

* (3) Debug 3Calibration Transformation1 parameters.

Double-click **3Calibration Transformation1** to set parameters. In “Basic Params”

page, set **Coord Point** to **2 Fast Match1.Match Point\[]** , **Load Calibration File** to

**Calibration file** generated from N-point Calibration, as shown in Figure7-45.

Figure7-45 Set “3Calibration Transformation” parameters

![Official Magician E6 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCrrMf4jgoPU2mtCvhTXd%2Futp-e2b5ce8912fc3121847a.jpg?alt=media)

![Official Magician E6 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9TF1NLrOvsj23Vk5Q7us%2Futp-17efef61822b5520d99c.png?alt=media)

(4) Debug **4Variable Calculation1** parameters.

Double-click **4Variable Calculation1** and check whether the **Expression** is “-<2 Fast Match1.MatchBoxAngle>\[0]”, as shown in Figure7-46. If not, modify it to “-<2 Fast Match1.MatchBoxAngle>\[0]”.

Figure7-46 Set “4Variable Calculation” parameters

(5) Debug **5Format1** parameters.

Double-click **5Format1** , and check whether the parameters are “<2 Fast Match1.MatchModelIndex(%0d)>\[0], <3 Calibration Transformation1.TransPointX (%1.3f)>\[0], <3 Calibration Transformation1.TransPointY(%1.3f)>\[0], <4 Variable Calculation1.var0(%1.3f)>\[0]”, as shown in Figure7-47. If not, modify it as the figure.

![Official Magician E6 training-system figure, source page 167](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3jIN4iqulho0qFtgsQtS%2Futp-739486d810672e7d9931.png?alt=media)

Figure7-47 Set “5Format” parameters

(6) Debug **Communication Management** parameters.

Click in the toolbar to enter “Communication Management” page. Check whether there is created TCP Server. If not, you need to re-create one, as described

below. Click beside Device List. Set **Protocol Type** to **TCP Server** , **Load IP** to **192.168.5.18** , and **Local Port** to **4001** , as shown in Figure7-48. Then click **Create** . The TCP Server is shown in Figure7-49 . Switch on **1TCP Server** . If there is TCP Server, check whether its parameters are consistent with Figure7-49 . If not, modify as the figures.

![Official Magician E6 training-system figure, source page 168](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYufYaNBCSe5e9gVLddHO%2Futp-c53a51e837c032017f15.png?alt=media)

Figure7-48 Create TCP Server

Figure7-49 Set “Communication Management” parameters

* (7) Debug **6Send Data1** parameters.

Double-click **6Send Data1** and check whether the parameters are shown as Figure7-50. If not, modify as the figure. Set **Output To** to **Communication Device** , **Communication Device** to **1 TCP Server** , **SendData1** to **5Format.format\_out\[]** .

![Official Magician E6 training-system figure, source page 169](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPBxgvRNTmyrd4aqN2f7U%2Futp-917ad1b4bbe5dc4b3eb8.png?alt=media)

![Official Magician E6 training-system figure, source page 169](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPc97ydj6OoVgYpay6cqq%2Futp-06239c89c1ae780ab8f5.png?alt=media)

Figure7-50 Set “6Send Data” parameters

**(8) Debug Global Trigger parameters.**

Click in the toolbar to enter “Global Trigger” page. In “String Trigger” page, check whether the string trigger setting is shown as Figure7-51. (String is void. Mode

is Mismatched. Trigger Configuration is All Process).

Figure7-51 Set “Global Trigger” parameters

#### 3.2.5 Save program

Click in the toolbar to save the program. If you need to save the program elsewhere on your local computer, click **File** > **Save as** , select the saving path and enter the name of the project.

#### 3.3 Debug robot program

#### 3.3.1 Import program

(1) On the Home screen of DobotStudio Pro software, click **Application > Script**

**programming** and enter “Programming ” interface, as shown in Figure7-52.

![Official Magician E6 training-system figure, source page 170](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBVNdtwUAkJF2LIJVD4XC%2Futp-a22a6268b6e9c7616adc.png?alt=media)

![Official Magician E6 training-system figure, source page 170](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhLTyetkPyLAl1tAnRUKE%2Futp-25a00bd0e40f766173af.png?alt=media)

Figure7-52 Enter “Programming ” interface

(2) Click to open File menu and select “Import project”, as shown in Figure7-53. Select **Visual positioning guided assembly** folder, and click **Open** . Now the **visual positioning guided assembly** program has been imported into DobotStudio Pro, as shown in Figure7-54.

Figure7-53 Import project

![Official Magician E6 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsQS744H6iw1U1UAQ5ZJc%2Futp-5bc85ae512fb87b2a0dc.jpg?alt=media)

![Official Magician E6 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOsCydw1CqYPv8Nk6PwIG%2Futp-d9289b42d88012871292.png?alt=media)

Figure7-54 Project imported

#### 3.3.2 Save program

Click and enter a project name in the pop-up dialog box. Click **Save** , as

shown in Figure7-55.

Figure7-55 Save program

#### 3.3.3 Set communication

Ensure that the IP address and port of TCP server in the robot program are

![Official Magician E6 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZ7GLUsbZVTieFqJPMLfq%2Futp-53a7c04864d1acf1e73d.jpg?alt=media)

![Official Magician E6 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz5UOpdcKw9cYslJPmMQd%2Futp-a40772f5d7108c35fb22.png?alt=media)

consistent with those in vision communication settings, that is, set IP address in the

robot program to 192.168.5.18. Set port to 4001, as shown in Figure7-56.

Figure7-56 Set communication

#### 3.3.4 Modify Z coordinates

* (1) Modify Z coordinate of the picking point.

Jog the robot to make the suction cup slightly touch the surface of the chips, as shown in Figure7-57. Then read the current Z coordinate of the robot, as shown in Figure7-58. Modify the Z coordinate in the command “local GetProductPos = {pose = {move\_x, move\_y, 212.5,P1.pose\[4],P1.pose\[5], move\_r} }” in the chip pickup subprogram to the current Z coordinate.

Figure7-57 Picking point

![Official Magician E6 training-system figure, source page 173](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F87STGn3Y6OM473fTCqJY%2Futp-eefa31befe24b8489a79.jpg?alt=media)

Figure7-58 Z coordinate of picking point

(2) Modify Z coordinate over the picking point.

Jog the robot to lift some distance, as shown in Figure7-59. Then read the Z coordinate of the robot, as shown in Figure7-60. Modify the Z coordinate in the command “local GetProductPosUp = {pose = {move\_x, move\_y, 242.5, P1.pose\[4], P1.pose\[5], move\_r} }” in the chip pickup sub-program to the current Z coordinate. Click“ ”to save the program.

![Official Magician E6 training-system figure, source page 174](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOLjHrOQb73wQf9SfQINF%2Futp-7d4c110ea81fb3721271.jpg?alt=media)

Figure7-59 Over picking point

Figure7-60 Z coordinate over picking point

#### 3.3.5 Debug points

* (1) Update the safe point P1.

![Official Magician E6 training-system figure, source page 175](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F28Uh3q1gErtLClHFyTwd%2Futp-ffbadcc3d78c89dad049.jpg?alt=media)

![Official Magician E6 training-system figure, source page 175](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0qQ1kk0OSdiSsazUQFoF%2Futp-65726ca572850aa7bac7.jpg?alt=media)

Jog the robot to a position between the conveyor belt and the storage area, as shown in Figure7-61. Click **Points** to enter the **Points** interface. Firstly select P1.Then click the tool **Cover** . Finally click **Cover** in the pop-up tips again to update P1 point,

as shown in Figure7-62. Click and save the program.

Figure7-61 Locate P1

Figure7-62 Update P1

Note: After updating each point, the program needs to be saved once.

* (2) Update the Hexagonal chip assembly point P2.

Click to make the robot suck the hexagonal chip according to the

coordinates sent by the vision system. Then click immediately. Jog the robot to

move the robot to the hexagonal chip assembly area, as shown in Figure7-63. Open

![Official Magician E6 training-system figure, source page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fl7EmjVw8pTL5Q44aeztx%2Futp-7f9be8db7952fda631dc.jpg?alt=media)

![Official Magician E6 training-system figure, source page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkOrE3kFLiPNeBkECS0tr%2Futp-b6b9af2bc61a656f5854.png?alt=media)

**Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the hexagonal chip is placed into the groove accurately. If not, you need to re-debug the point.

Figure7-63 Locate Hexagonal chip assembly point P2

Select **P2** and click **Cover** in the points interface. Then click **Cover** in the pop-up

Tips dialog box again to update P2, as shown in Figure7-64. Click“ ”to save the

program.

Figure7-64 Update P2

* (3) Update the GPS chip assembly point P3.

Click to make the robot suck the GPS chip according to the coordinates

sent by the vision system and click immediately. Jog the robot to move the robot

to the GPS chip assembly point in the assembly area, as shown in Figure7-65. Open

![Official Magician E6 training-system figure, source page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8eLIFnTV1GkGlx5aFwJM%2Futp-2e5ddb1dfb09bf2fe43b.jpg?alt=media)

![Official Magician E6 training-system figure, source page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPzcR7tsEHmDfnKU6WDpZ%2Futp-de540062a3009b3f7573.jpg?alt=media)

**Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the GPS chip is placed into the groove accurately. If not, you need to re-debug the point.

Figure7-65 Locate GPS chip assembly point P3

Select **P3** in **Points** page and click **Cover** in the points interface. Then click **Cover**

in the pop-up Tips dialog box again to update P3, as shown in Figure7-66. Click“ ”

to save the program.

Figure7-66 Update P3

* (4) Update the electronic compass chip assembly point P4.

Click to make the robot suck the electronic compass chip according to the

coordinates sent by the vision system and click immediately. Jog the robot to

![Official Magician E6 training-system figure, source page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4kvtRhXind1lRk22LBay%2Futp-830d4f9d7c2bced7078e.jpg?alt=media)

![Official Magician E6 training-system figure, source page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGS58aSJpKTPuWOTfhfps%2Futp-83a524c2f0bd5e74549f.jpg?alt=media)

move the robot to the electronic compass chip assembly point in the assembly area, as shown inFigure7-67. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the electronic compass is placed into the groove accurately. If not, you need to re-debug the point.

Figure7-67 Locate Electronic compass chip assembly point P4

Select P4 in **Points** page and click **Cover** in the points interface. Then click **Cover**

in the pop-up Tips dialog box again to update P4, as shown in Figure7-68. Click“ ”

to save the program.

Figure7-68 Update P4

* (5) Update the gravity sensor chip assembly point P5.

Click to make the robot suck the gravity sensor chip according to the

![Official Magician E6 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLs0aJGK1k0Ov83auOove%2Futp-18e85633f995fde7a8ba.jpg?alt=media)

![Official Magician E6 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsMw5nV5ZcB0RGHsSNUcf%2Futp-9c71d1a74b6b5b720f4d.jpg?alt=media)

coordinates sent by the vision system, and click immediately. Jog the robot to the gravity sensor chip assembly point in the assembly area, as shown in Figure7-69. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the gravity sensor chip is placed into the groove accurately. If not, you need to re-debug the point.

Figure7-69 Locate the gravity sensor chip assembly point P5

Select **P5** in **Points** page and click **Cover** in the points interface. Then click **Cover**

in the pop-up Tips dialog box again to update P5, as shown in Figure7-70. Click “ ”

to save the program.

Figure7-70 Update P5

* (6) Update the WIFI chip assembly point P6.

Click to make the robot suck the WIFI chip according to the coordinates

![Official Magician E6 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfGDJlCFO64SWkY0WNuMP%2Futp-7caa598b40a3af84118a.jpg?alt=media)

![Official Magician E6 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpTOJ4nlE4YEEV8tdygvb%2Futp-790868d3a6c43083a322.jpg?alt=media)

sent by the vision system and click immediately. Jog the robot to the WIFI chip assembly point in the assembly area, as shown in Figure7-71. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the WIFI chip is placed into the groove accurately. If not, you need to re-debug the point.

Figure7-71 Locate the WIFI chip assembly point P6

Select **P6** in **Points** page and click **Cover** in the points interface. Then click **Cover**

in the pop-up Tips dialog box again to update P6, as shown in Figure7-72. Click “ ”

to save the program.

Figure7-72 Update P6

* (7) Update the photosensor chip assembly point P7.

Click to make the robot suck the photosensor chip according to the

![Official Magician E6 training-system figure, source page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5qlmRGOs5STty5ehDpTV%2Futp-488f248a2b39d156dec5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6PY8sFCVtmQVwUTxEIE8%2Futp-dcdf8f3b96354c618842.jpg?alt=media)

coordinates sent by the vision system and click immediately. Jog the robot to the photosensor chip assembly point in the assembly area, as shown in Figure7-73. Open **Controller DI/DO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set **DO\_10** to **OFF** and observe whether the photosensor chip is placed into the groove

accurately. If not, you need to re-debug the point.

Figure7-73 Locate the photosensor chip assembly point P7

Select **P7** in Points page and click **Cover** in the points interface. Then click **Cover**

in the pop-up Tips dialog box again to update P7, as shown in Figure7-74. Click“ ” to save the program.

Figure7-74 Update P7

Note1: For point debugging, please adjust the installation point of the chip based on the actual phone base model.

![Official Magician E6 training-system figure, source page 182](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFv5xpYOTosqDq3yPHXpk%2Futp-22a91e0db4e5b1423563.jpg?alt=media)

![Official Magician E6 training-system figure, source page 182](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7nWbfZKBRj4dqkQW6584%2Futp-51a631ae8f5ccf240899.jpg?alt=media)

#### 3.3.6 Run program

Place all the chips on the standard vision board. Open the vision program. Click in DobotStudio Pro. The program starts running. After receiving the chip coordinates sent by the vision system, the robot sucks the phone chips from the standard vision board and assembles them into the corresponding grooves of the phone models. The installed phone is shown in in Figure7-75.

Figure7-75 Installed phone

#### 3.3.7 Export program

Click to open File menu and select “Export project”. Select the path to save the program. Then enter a project name in the pop-up dialog box.

### 4. Key Program Description

#### 4.1 Vision program description

The vision program is shown in Figure7-76. **0Image Source1** is mainly used for image acquisition. During the running process of the system, once the vision software receives the trigger signal from the robot. The camera takes photos immediately. **2Fast Match1** is mainly used for positioning, in order to obtain the image coordinates and matching angle of the detected object. **3Calibration Transformation1** is used for transforming the image coordinates to the actual physical coordinates. **4Variable**

![Official Magician E6 training-system figure, source page 183](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpBaDTYoOphJLP9dogBTj%2Futp-df26a7b25d0128c5b90f.jpg?alt=media)

**Calculation1** is used for correcting the matching angle. **5Format1** is used for summarizing the information that the vision system needs to send to the robot and defining the format. **6Send Data1** is used for sending the 5Format1 content to the robot.

Figure7-76 Vision program

* **4.2 Robot program description**

#### 4.2.1 Character separation program

The character separation program is shown in Figure7-77.

Figure7-77 Character separation program

#### 4.2.2 Data transmission program

The data transmission program is shown in Figure7-78, which mainly sends photography trigger signal “ok” and receives the data sent by the vision system.

![Official Magician E6 training-system figure, source page 184](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6j3y2hQQlL5lgyHhCVeF%2Futp-4d24d6e9996c9f260e8e.png?alt=media)

Figure7-78 Data transmission program

#### 4.2.3 Robot pick-up program

The robot pick-up program is shown in Figure7-79. The function of the program is that the robot sucks the chips on the standard vision board according to the coordinates sent by the vision system.

Figure7-79 Robot pick-up program

#### 4.2.4 Output port reset program

The output port reset program is shown in Figure7-80, which sets all output ports

**to OFF .**

Figure7-80 Output port reset program

#### 4.2.5 Communication program

The communication program is shown in Figure7-81, which mainly creates TCP

client and establish connect with TCP server (vision).

![Official Magician E6 training-system figure, source page 185](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FetqPRTW1qekNLCpAr0XS%2Futp-a97122835336e9312ed9.png?alt=media)

![Official Magician E6 training-system figure, source page 185](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FinEfipVijDtal5iibz8r%2Futp-7ceccf2a2d261e731448.png?alt=media)

Figure7-81 Communication program

#### 4.2.6 Attitude adjustment program

The posture adjustment program is shown in Figure7-82, which implements the

function of adjusting the robot’s posture to a vertical posture .

Figure7-82 Robot attitude adjustment program

#### 4.2.7 Robot assembly program

The robot assembly program is shown in Figure7-83. The function of the program is that the robot assembles the phone chips into the corresponding grooves of the phone

models according to the chip index sent by the vision system.

(1)Assemble the hexagonal chip

(2)Assemble the GPS positioning chip

![Official Magician E6 training-system figure, source page 186](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq06nknsVr4jInny9qQEF%2Futp-07f7f688958539477d1a.png?alt=media)

![Official Magician E6 training-system figure, source page 186](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm4vXoCOQVxCwnDkL3MzS%2Futp-6f7798e59041ba0e3bd1.png?alt=media)

**Application of Visual Positioning Guided Assembly**

(3)Assembling the electronic compass chip<br>

(4)Assemble the gravity sensor chip<br>

(5)Assemble the WIFI chip<br>

(6)Assemble the photosensitive sensor chip

Figure7-83 Robot assembly program

![Official Magician E6 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp3C5zMGqqgTEZi30Y9Ik%2Futp-ec8071d687893d193a09.png?alt=media)

![Official Magician E6 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FajvOTxHSlfbl1w7k4DmP%2Futp-9a8f689ac4bf025c8d71.png?alt=media)

![Official Magician E6 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjRn3SHYkM6KYB0B3VDIu%2Futp-02f2fd4729ef27500e6d.png?alt=media)

![Official Magician E6 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fi3pVQSs91MwgPPBe9ttV%2Futp-6a0fc6f8ca15174173f2.png?alt=media)

### Appendix 1: Installation of Robot Software

**Step 1: Download the robot software installation package.**

Please download the latest DobotStudio Pro installation package from the official

website.

**Step 2: Enter installation guide interface.**

Double-click the downloaded software, and an installation guide interface will pop

up. Select the installation language and click **Next** , as shown in Appendix Figure1-1.

Appendix Figure1-1 Installation guide

**Step 3: Select the installation path.**

Click **One Click Install** , or start installation after setting the installation path in Custom options, as shown in Appendix Figure1-2 and Appendix Figure1-3.

![Official Magician E6 training-system figure, source page 188](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPgMkmqPRYb0kSqyzNQ9e%2Futp-ef80dd809274bf79d627.jpg?alt=media)

Appendix 1<br>

Appendix Figure1-2 One click install\
Appendix Figure1-3 Select installation path<br>

**Step 4: Start installing.**

Click **Install Now** to start installing DobotStudio Pro, as shown in Appendix

Figure1-4.

![Official Magician E6 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiSy1cZbJVTIag35qXiUx%2Futp-c48d9ded31325058e835.jpg?alt=media)

![Official Magician E6 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdLoZsYrwkJrloKqvniYA%2Futp-0c420c53e66a4b86452e.jpg?alt=media)

Appendix Figure1-4 Installing software

**Step 5: Finish installation.**

After installation, click **Experience Now** to enter the software, as shown in

Appendix Figure1-5.

Appendix Figure1-5 Installation finished

**Step 6: Know about the software interface.**

The main interface mainly includes fourteen parts, as shown in Appendix Figure1-

6.

![Official Magician E6 training-system figure, source page 190](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9ab4ektunX58ZUQlsdGd%2Futp-194c7a143678ea8d4897.jpg?alt=media)

![Official Magician E6 training-system figure, source page 190](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUvP72RLZNVQd1bwGoqkN%2Futp-7311119d0ded4b525479.png?alt=media)

Appendix 1<br>

Appendix Figure1-6 Main interface

① Click to open the main interface (current interface). The colour of the robot arm icons changes according to the robot status. For detailed definition of the indicator

colours, see the corresponding hardware guide.

* ② Click to open Settings interface.
* ③ Click to open Log interface.
* ④ Click to open Dobot+ interface.
* ⑤ Click to open Programming interface.
* ⑥ Click to open help documents, which can be displayed in the software interface,

in a separate window or in a browser.

* ⑦ Click to open Jog panel.
* ⑧ Click to open Monitor panel.
* ⑨ Display the current global speed rate. Drag the slider or click the speed bar to
* adjust the global speed rate. The global speed rate is the calculation factor of the robot actual running speed.
  * ⑩ Emergency stop switch. Press the button in an emergency, and robot arm will

stop running and be powered off.

* ⑪ Robot information panel.
* ⑫ Robot 3D model, with a posture consistent with the real robot.
* ⑬ Software and firmware version information.

![Official Magician E6 training-system figure, source page 191](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvGcTlUsWvYi0LRJhd5N1%2Futp-edcdc75f84997d01f597.jpg?alt=media)

⑭ Click to view the voltage, current and temperature of the robot.

Note: For specific functions of each tool, see its corresponding user guide.

### Appendix 2: Installation of Vision Related Software

### 1. Installation of vision software.

**Step 1: Enter Dobot official website.**

Search https://www.dobot-robots.com/ in the browser to enter Dobot website. Click **User** to enter “USER LOGIN” page. Enter your email and password to enter “USER CENTER” page as shown in Appendix Figure2-1. (You need to register before

login.)

Appendix Figure2-1 USER LOGIN

**Step 2: Download the latest vision software package.**

①Click **Download Center** in “USER CENTER” page, as shown in Appendix

Figure2-2 .

Appendix Figure2-2 USER CENTER

![Official Magician E6 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhW3JerdDtfUzzco6jScQ%2Futp-87e852542cfb0780856e.jpg?alt=media)

![Official Magician E6 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC7YhIhSMAUALJiCUko2d%2Futp-80f4584534c1fc3e59a1.png?alt=media)

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

![Official Magician E6 training-system figure, source page 194](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEbSpmNT7O7ekSq0sVpsL%2Futp-760ecfec932a64662a00.png?alt=media)

![Official Magician E6 training-system figure, source page 194](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8CMQqD493aHnfmwUGLtw%2Futp-24a948e307da623feb9a.png?alt=media)

Appendix Figure2-6 Welcome to DobotVisionStudio4.1.2 Setup

**Step 6: Choose Components.**

In “Choose Components” page, select **Hard Encryption** , **AlgorithmInstall** and

**CameraDriver** . Then click **Next,** as shown in Appendix Figure2-7.

Appendix Figure2-7 Choose Components

**Step 7: Choose Install Location.**

Click **Browse...** to define the installation path of the software. Then click **Install** ,

as shown in Appendix Figure2-8 and Appendix Figure2-9.

![Official Magician E6 training-system figure, source page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNUDAeDEQfwuqLJ8Q9PJY%2Futp-e91c7bdeb79dbda555d5.jpg?alt=media)

![Official Magician E6 training-system figure, source page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft4fJob4CCG6c2e3xnyi9%2Futp-aa23979bc85c16299ec1.png?alt=media)

Appendix Figure2-8 Choose Install Location

Appendix Figure2-9 Installing

**Step 8: Finish installation.**

Select **Run DobotVisionStudio4.1.2** and click **Finish** to exit the installation, as

shown in Appendix Figure2-10.

![Official Magician E6 training-system figure, source page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhXDhIxnpEXNRUSpG88Wo%2Futp-0e8487bbc32964408ec3.png?alt=media)

![Official Magician E6 training-system figure, source page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ0H8VWbDWDJvQ8DZF38U%2Futp-f0708a1fc5b62b6345a6.png?alt=media)

<br>

Appendix Figure2-10 Installation finished

**Step 9: Know about the vision software interface.**

Open the software and select **General Solution** to enter the corresponding

software interface, as shown in Appendix Figure2-11.

Appendix Figure2-11 Main interface

Area 1: Menu Bar. It includes File, Settings, System, Tools and Help.

![Official Magician E6 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp5UzAHvqp85f9UxxVC8S%2Futp-23c0e50705320f1d0bd0.jpg?alt=media)

![Official Magician E6 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuNRYLyCNWAPdB6cccFaO%2Futp-73a1788edc7e6eabea0f.png?alt=media)

Area 2: Control Toolbar. It provides quick operations for the software, including file saving, file open, camera management, controller management, etc.

Area 3: Tool Box. It includes image collection, positioning, measurement, identification, calibration, position, image processing, colour processing, defect detection, logic tools, communication, etc.

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

Appendix Figure2-14 Options

![Official Magician E6 training-system figure, source page 199](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvAJGsrz2ZsKOpSRvz2Ys%2Futp-b3e06cd8d53e18e125f6.jpg?alt=media)

![Official Magician E6 training-system figure, source page 199](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F73A8mrMUOAHMb9aAElcC%2Futp-927b815bb4ad240d87f9.jpg?alt=media)

**Step 4: Start installing.**

Confirm your settings and click **Next** . Then the software starts to be installed, as shown in Appendix Figure2-15.

Appendix Figure2-15 Installing

**Step 5: Finish installation.**

After installation, you can set whether to run the client and whether to open the release note, as shown in Appendix Figure2-16.

![Official Magician E6 training-system figure, source page 200](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCDbbnNCYQ9DX5jx4mAhg%2Futp-404cef0b2415219f1128.jpg?alt=media)

Appendix Figure2-16 Installation finished

**Step 6: Know about the software interface.**

After opening the MVS software, you will see the main interface as shown in Appendix Figure2-17, which includes six parts.

Appendix Figure2-17 Main interface

![Official Magician E6 training-system figure, source page 201](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNu2lIqKCYhwl2qdx1l2Y%2Futp-ee8c1b094db94c47ea32.jpg?alt=media)

![Official Magician E6 training-system figure, source page 201](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ2wFIPquAt5xSqHH6FOD%2Futp-3b05690978790c003e67.png?alt=media)

Area 1: Menu Bar. Function modules including File, View, Settings, Tool and Help. Area 2: Control Toolbar.

Area 3: Display the GigE Vision cameras, USB3 Vision cameras and Camera Link cameras. Provide icons for connecting/disconnecting camera, start/stop acquisition, and refreshing device list.

Area 4: Interface and Device Information Panel. Display the network interface information and the device information.

Area 5: Display Window. View the live video of the selected camera.

Area 6: Feature Panel. View and configure features of the selected camera, and

perform other operations such as importing, exporting and saving features.

Note: For specific functions of each tool, see its corresponding user guide.

### Appendix 3: IO Testing Method for E6 General Training

### Platform

### 1. IO Configuration

The IO configuration of the E6 General training platform is shown in Appendix

Table 3-1.

**Appendix Table 3-1 IO configuration**

| **DI** | **Description**                     | **DO** | **Description**    |
| ------ | ----------------------------------- | ------ | ------------------ |
| DI01   | START                               | DO01   | Pusher motor start |
| DI02   | STOP                                | DO02   | Conveyor start     |
| DI03   | RESET                               | DO03   | Green light        |
| DI09   | Material detection in the stock bin | DO04   | Yellow light       |
| DI10   | Material inplace inspection         | DO05   | Red light          |
| /      | /                                   | DO06   | Buzzer             |
| /      | /                                   | DO09   | Vacuumpumping      |
| /      | /                                   | DO10   | Vacuum breaking    |

### 2. IO Testing Method

#### 2.1 Preparation

#### 2.1.1 Turn on system power switch

Connect the power adapter of the conveyor belt and the E6 robot to an external

power source, and turn on the switch of the external power source.

#### 2.1.2 Power on the robot

Short press the power button on the back of the E6 base in 0.5 seconds to turn it

on, as shown in Appendix Figure3-1.

Appendix Figure3-1 Turn on the E6 power switch

![Official Magician E6 training-system figure, source page 203](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKnEGhLBCCwu1wT5Ekol1%2Futp-c91bbf3653b922e59d0c.jpg?alt=media)

#### 2.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to **Auto** , as shown in Appendix Figure3-2.

Appendix Figure3-2 Turn on Pump box power switch

#### 2.1.4 Connect robot

* (1) Connect the robot to the computer.

Connect one end of the network cable to the LAN1 port on the E6 base and the

other end to the PC.

* (2) Modify IP of the computer.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Appendix Figure3-3. The default address of the robot is “192.168.5.1”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.5.18” as an example.

![Official Magician E6 training-system figure, source page 204](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMLuY8PZsXOomSjlxgjPw%2Futp-ea03dd125a359b391db0.jpg?alt=media)

Appendix Figure3-3 Set IP of the PC

* (3) Connect DobotStudio Pro to the robot.

Double-click DobotStudio Pro to open the software. After you enter DobotStudio

Pro, the software will automatically search for robots and displays the search results on the interface. Click **Connect** on the right side of the E6 to connect it, as shown in Appendix Figure3-4.

Appendix Figure3-4 Connect robot

After successful connection, the software interface will refresh and display the

![Official Magician E6 training-system figure, source page 205](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfFW8rxCNQcXS2wrdDVKt%2Futp-8ffcc127698c75d5fef2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 205](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI52WALexkcCkcr0KRTBC%2Futp-0a5e0c0bd67c2bffac21.png?alt=media)

information about the E6 and its 3D model, as shown in Appendix Figure3-5.

Appendix Figure3-5 the information about the E6

#### 2.1.5 Enable robot

Click on the “Enable” switch of the “Magician E6” interface. Modify various parameter values according to the actual situation in the “Load enabling settings” window that pops up. Click **Enable** , as shown in Appendix Figure3-6. The Enabling switch changes to in the E6 interface..

![Official Magician E6 training-system figure, source page 206](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HVeckjxBUbBwnRxv6zE%2Futp-eb1dd06dec648d21e861.jpg?alt=media)

Appendix Figure3-6 Set load parameters

#### 2.1.6 Install coaxial suction cup

* (1) Adjust the installation posture of the robot’s end tool.

Click **Jog** on the top toolbar of DobotStudio Pro4.1 to enter the “Jog” panel. By jogging control, adjust the robot to a posture that is conducive to installing the end tool, as shown in Appendix Figure3-7.

Appendix Figure3-7 The posture of installing the end tool

![Official Magician E6 training-system figure, source page 207](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8U7sbdqebP6pOyLEuvI%2Futp-c1058e90e6b279fce6e2.png?alt=media)

![Official Magician E6 training-system figure, source page 207](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGID1lJWubeuP8tsnZlsT%2Futp-b553235602b81b2845ed.jpg?alt=media)

![Official Magician E6 training-system figure, source page 207](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaurAi1A7IEXFaD2zlMhD%2Futp-2df2a85a50f9a9c39daa.jpg?alt=media)

Note: It is best to adjust the value of J6 to 0°.

* (2) Install the suction cup onto the end of the robot through four M3 \* 8 screws

using an allen tool, as shown in Appendix Figure3-8.

Appendix Figure3-8 Install the suction cup on the end of robot

(3) Connect one end of the air pipe to the “Air” hole in the air pump box, and the other end to the suction cup. Fix it to the robot with a tie, as shown in Appendix Figure39.

Appendix Figure3-9 Connect the air pipe

#### 2.1.7 Enter “Controller DI/DO” interface

Click **Monitor** on the top-level toolbar of DobotStudio Pro4.1 to enter the default “Controller DI/DO” interface, as shown in Appendix Figure3-10.

![Official Magician E6 training-system figure, source page 208](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzcv41juFPW7siMzWaWqI%2Futp-17f289914692994ebfa2.jpg?alt=media)

![Official Magician E6 training-system figure, source page 208](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGHMloBxWCbCJ7Vzxmw3m%2Futp-748440c039c3f49da81b.jpg?alt=media)

Appendix Figure3-10 “Controller DI/DO” interface

#### 2.2 Input IO Test Method

#### 2.2.1 “START” button (DI\_1) port test

Press the “START” button on the button box (as shown in Appendix Figure3-11), and the “Status” of “DI\_1” in the DI column will turn green, as shown in Appendix Figure3-12. If it does not turn green, it indicates that there is a problem with the circuit of “DI\_1” and it needs to be investigated.

Appendix Figure3-11 the control button box

![Official Magician E6 training-system figure, source page 209](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSZfkJhE1K3lmevsHkUh3%2Futp-e3ebb356c79e19e20afb.jpg?alt=media)

![Official Magician E6 training-system figure, source page 209](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpiFgvphhemC1FaW7GPRv%2Futp-20c4b496921855508f25.jpg?alt=media)

Appendix Figure3-12 DI\_1 Port Status

**2.2.2 “ STOP ” button (DI\_2) port test**

Press the “STOP” button on the button box , and the “Status” of “DI\_2” in the DI column will turn green, as shown in Appendix Figure3-13. If it does not turn green, it indicates that there is a problem with the circuit of “DI\_2” and it needs to be investigated.

![Official Magician E6 training-system figure, source page 210](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCJICZdTBab8h2l0o95Xg%2Futp-d671e5ee718b98170ce8.jpg?alt=media)

![Official Magician E6 training-system figure, source page 210](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCDIyUbdPcoS3KbLCob0X%2Futp-c090e970d644854fce6b.jpg?alt=media)

**Appendix Figure3-13 DI\_2 Port Status**

**2.2.3 “ RESET ” button (DI\_3) port test**

Press the “RESET” button on the button box , and the “Status” of “DI\_3” in the DI column will turn green, as shown in Appendix Figure3-14. If it does not turn green, it indicates that there is a problem with the circuit of “DI\_3” and it needs to be investigated.

Appendix Figure3-14 DI\_3 Port Status

#### 2.2.4 Material detection in the silo (DI\_9) port test

Place a cylindrical workpiece into the silo ,as shown in Appendix Figure3-15 and the “Status” of “DI\_9” in the DI column will turn green, as shown in Appendix Figure316. If it does not turn green, it indicates that there is a problem with the circuit of “DI\_9” and it needs to be investigated.

Appendix Figure3-15 Place a cylindrical workpiece

![Official Magician E6 training-system figure, source page 211](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8eA1bPwZozqeIy5Cezqa%2Futp-95316eff59727911bc61.jpg?alt=media)

![Official Magician E6 training-system figure, source page 211](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOgoXJdjjbYFSvrmaO4yP%2Futp-5cda110fb511bfb183f8.jpg?alt=media)

Appendix Figure3-16 DI\_9 Port Status

#### 2.2.5 Material in place inspection (DI\_10) port test

Place a cylindrical workpiece in place, as shown in Appendix Figure3-17 and the “Status” of “DI\_10” in the DI column will turn green, as shown in Appendix Figure318. If it does not turn green, it indicates that there is a problem with the circuit of “DI\_10” and it needs to be investigated.

Appendix Figure3-17 Workpiece in place

![Official Magician E6 training-system figure, source page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBkuHOBZreu7Q1Etxotpq%2Futp-7a8a3c42361b160127a9.jpg?alt=media)

![Official Magician E6 training-system figure, source page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIfxEPRaaqOtAGkpbKzrh%2Futp-09be34b2fd6325a01784.jpg?alt=media)

Appendix Figure3-18 DI\_10 Port Status

#### 2.3 Output IO Test Method

#### 2.3.1 Pusher motor control (DO\_1) port test

Place a cylindrical workpiece into the silo and set the “Status” of “DO\_1” to “ON” (as shown in Appendix Figure3-19). Observe whether the pusher motor can push the circular workpiece onto the conveyor belt. Set the “Status” of “DO\_1” to “OFF” and observe whether the push rod of the pusher motor retracts. If it does not work, it indicates that there is a problem with the circuit of “DO\_1” and it needs to be investigated.

![Official Magician E6 training-system figure, source page 213](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4UPs9B1tqI9jq4Bp3Syj%2Futp-8631f5a4ea33de0c03cd.jpg?alt=media)

Appendix Figure3-19 DO\_1 Port Status

#### 2.3.2 Conveyor belt control (DO\_2) port test

Set the “Status” of “DO\_2” in the DO column to “ON”, as shown in Appendix Figure3-20. Observe if the conveyor belt is moving forward. If it does not work, it indicates that there is a problem with the circuit of “DO\_2” and it needs to be investigated.

Appendix Figure3-20 DO\_2 Port Status

![Official Magician E6 training-system figure, source page 214](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmQ0xSqSrA8wfLiXo370Y%2Futp-5741bee62ede725e4738.png?alt=media)

![Official Magician E6 training-system figure, source page 214](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3JPn0ANqfIaMDYHpHquY%2Futp-fe76bd2f5fc5b24f506b.png?alt=media)

#### 2.3.3 Green light control of the tricolour light(DO\_3) port test

Set the “Status” of “DO\_3” in the DO column to “ON”, as shown in Appendix Figure3-21. Observe if the green light of the tricolour light is on, as shown in Appendix Figure3-22. If the green light is not on or the colour is incorrect, it indicates that there is a problem with the circuit of “DO\_3” and it needs to be investigated.

Appendix Figure3-21 DO\_3 Port Status

Appendix Figure3-22 Green light on

#### 2.3.4 Yellow light control of the tricolour light(DO\_4) port test

Set the “Status” of “DO\_4” in the DO column to “ON”, as shown in Appendix Figure3-23. Observe if the yellow light of the tricolour light is on, as shown in Appendix

![Official Magician E6 training-system figure, source page 215](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrN9gCdKN8bZsRk8c426k%2Futp-fd764ec4f127ba9d05cc.png?alt=media)

![Official Magician E6 training-system figure, source page 215](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdKQkT96zCttArsKHg7sC%2Futp-d0e1433f1be84c6f8d95.png?alt=media)

Figure3-24. If the yellow light is not on or the colour is incorrect, it indicates that there is a problem with the circuit of “DO\_4” and it needs to be investigated.

Appendix Figure3-23 DO\_4 Port Status

Appendix Figure3-24 Yellow light on

#### 2.3.5 Red light control of the tricolour light(DO\_5) port test

Set the “Status” of “DO\_5” in the DO column to “ON”, as shown in Appendix Figure3-25. Observe if the red light of the tricolour light is on, as shown in Appendix Figure3-26. If the red light is not on or the colour is incorrect, it indicates that there is a problem with the circuit of “DO\_5” and it needs to be investigated.

![Official Magician E6 training-system figure, source page 216](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fy99yhjvl66tSMJxD50zz%2Futp-9216ab4814ebfc6580b4.png?alt=media)

![Official Magician E6 training-system figure, source page 216](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0AWxRA3GaA3OJqnEjXtH%2Futp-8d0405b2f2abec2991ee.png?alt=media)

Appendix Figure3-25 DO\_5 Port Status

Appendix Figure3-26 Red light on

**2.3.6 Buzzer control (DO\_6) port test**

Set the “Status” of “DO\_6” in the DO column to “ON”, as shown in Appendix Figure3-27. Observe weather Buzzer sounds. If the Buzzer does not sound, it indicates that there is a problem with the circuit of “DO\_6” and it needs to be investigated.

![Official Magician E6 training-system figure, source page 217](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVu05s87LYIhNsMUXDtOK%2Futp-a8570ace5525678a3995.png?alt=media)

![Official Magician E6 training-system figure, source page 217](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4Wk4uDZXWoRnvcrTsPmE%2Futp-8c8565cc93d983f7b0d5.png?alt=media)

Appendix Figure3-27 DO\_6 Port Status

Note: The buzzer is integrated into the three colour light.

#### 2.3.7 Inspiratory control (DO\_9) port test

Set the “Status” of “DO\_9” in the DO column to “ON”, as shown in Appendix Figure3-28. Place your finger under the suction cup and feel if the suction cup is inhaling, as shown in Appendix Figure3-29. If the suction cup does not inhale, it indicates that there is a problem with the circuit of “DO\_9” and it needs to be investigated.

Appendix Figure3-28 DO\_9 Port Status

![Official Magician E6 training-system figure, source page 218](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfRnwxVde1czXxWbjkQIV%2Futp-cb353c261274daafa098.png?alt=media)

![Official Magician E6 training-system figure, source page 218](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2ForufvsqG53xeacEYWLJd%2Futp-aff37b1ca4dc0e6e9132.png?alt=media)

Appendix Figure3-29 Finger placement position

#### 2.3.8 Blowing control (DO\_10) port test

Set the “Status” of “DO\_10” in the DO column to “ON”, as shown in Appendix Figure3-30. Place your finger under the suction cup and feel if the suction cup is blowing. If the suction cup does not below, it indicates that there is a problem with the circuit of “DO\_10” and it needs to be investigated.

Appendix Figure3-30 DO\_10 Port Status

![Official Magician E6 training-system figure, source page 219](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcGkfons7xPoOB7gKmZbj%2Futp-b5ae5d138e2609995c2c.png?alt=media)

![Official Magician E6 training-system figure, source page 219](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoLZbU160cV84u7cO6fTo%2Futp-cd79f37ac33229b473dd.png?alt=media)

## Official source and related installation guides

The complete English source is in the [official DOBOT Universal Training Platform operation-instruction archive](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260722/1770703893557_Collaborative%20Robot%20Universal%20Training%20Platform%20Operation%20Instruction-EN.rar). Select file `05-Collaborative Robot Universal Training Platform (Magician E6 _exclude PLC)_2023-08-02_en.pdf`. The archive also contains the platform installation, emergency-stop wiring, conveyor, and PLC-upgrade guides.
