# DOBOT MG400 Universal Training Platform Operation Instruction - With PLC

## DOBOT Collaborative Robot Universal Training Platform - With PLC System Module

{% embed url="https://openelab.io/products/dobot-cobot-universal-training-platform?variant=46636171428038" %}

**Applies to:** MG400 training system with the PLC system module. Official source issue V4.1 (2026-02-11). The robot is purchased separately. Confirm the actual robot and PLC configuration before following wiring or software steps.

**Copyright © Shenzhen Yuejiang Technology Co., Ltd. 2023-2026. All rights reserved.** No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of Yuejiang Technology Co., Ltd.

**Disclaimer** To the maximum extent permitted by applicable law, the products described (including its hardware, software, and firmware, etc.) in this document are provided **AS IS** , which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and noninfringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents.

Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses will be happening in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document.

The user has the responsibility to make sure of following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot.

Shenzhen Yuejiang Technology Co., Ltd. Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China

Website: www.dobot.cc

### Preface

### Purpose

This document introduces the layout and some operation demos (including trajectory simulation, static palletizing, robot handling, vision sorting, phone chip assembly ) of the MG400 training system, which is convenient for users to understand and use the MG400 training system.

### Note

In this document, DobotStudio Pro 2.6.1 is used for robot control software . DobotVisionStudio 4.1.2 is used for vision software. TIA Portal V15.1 is used for PLC software. TIA Portal software must be purchased separately by the customer. The PLC program is pre-loaded within the system. If PLC programming is not required, TIA Portal software is unnecessary.

### Symbol Conventions

The symbols that may be found in this document are defined as follows.

| Symbol  | Description                                                                                                                                                                    |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| DANGER  | <p>Indicates a hazard with a high level of risk which, if not avoided, could<br>result in death or serious injury.</p>                                                         |
| WARNING | <p>Indicates a hazard with a medium level or low level of risk which, if not<br>avoided, could result in minor or moderate personal injury and damage<br>to the equipment.</p> |
| NOTICE  | <p>Indicates a potentially hazardous situation which, if not avoided, can<br>result in damage to the equipment, data loss, or unanticipated result.</p>                        |
| NOTE   | <p>Provides additional information to emphasize or supplement important<br>points in the main text.</p>                                                                        |

4. Key Program Description ..................................... 190

## Chapter 1 MG400 Training System Overview

### 1. Safety Precautions

This section describes the safety precautions that should be noticed when you use this product. Please read this section carefully before using the training system for the first time. This product needs to be used in an environment meeting the design specifications. You cannot remold the product without authorization, otherwise, it may lead to product failure, and even personal injury, electric shock, fire, etc. People who use this product for system design and manufacture must be trained by Dobot or relevant institutions, or must have the same professional skills, and use the training system strictly following the regulations of this document.

#### 1.1 Safety warning signs

The following safety warning signs may appear in this document, and their meanings are described as follows , as shown in Table1-1.

**Table1-1 Safety warning signs**

| **Sign**    | **Description**                                                                                                                                                                                                                              |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER      | <p>Indicates a high potential danger, which, if not avoided, will result in<br>death or serious injury.</p>                                                                                                                                  |
| ELECTRICITY | <p>May cause dangerous electricity usage situation soon, which, if not<br>avoided, will cause personal injury or serious damage to the<br>equipment.</p>                                                                                     |
| HOT         | <p>May cause dangerous hot surfaces, which, if touched, may cause<br>personal injury.</p>                                                                                                                                                    |
| WARNING     | <p>Indicates a moderate or low potential hazard, which, if not avoided,<br>may cause minor personal injury and damage to the equipment.</p>                                                                                                  |
| NOTICE      | <p>Indicates a potential risk, which, if ignored, may result in damage to<br>the equipment, loss of data or unpredictable results.</p>                                                                                                       |
| ATTENTION   | <p>A situation that, if not avoided, can cause personal injury or damage<br>to the equipment.<br>For items marked with such signs, depending on the specific<br>situation, there is sometimes a possibility of significant consequences.</p> |

#### 1.2 General safety

Follow the safety instructions below when starting and using the training system for the first time.

**DANGER**

* The training system is electrical equipment. Non-professional technicians should not modify the circuit, otherwise, it may cause damage to devices or personal injury.
* Comply with the local laws and regulations when operating the equipment.The safety precautions in this document are only supplemental to the local safety regulations.
* Use the equipment in the specified environment scope. Exceeding the specifications or load conditions will shorten the service life of the product, even damage it.
* Ensure that the equipment is operated under the security conditions and there is no harmful object around the robot.
* Turning on or off the power continually may result in degraded performance of the main circuit components inside the controller. If turning on or off the power continually is required, please keep the frequency less than once per minute.

(2) NOTICE

* The personnel responsible for installation, operation and maintenance of equipment must first receive strict training, understand various safety precautions, and master correct operation and maintenance methods before they can operate and maintain the equipment.
* Personnel without professional training shall not disassemble and repair the equipment without authorization. If the equipment fails, please contact Dobot technical support engineer in time.
* Be sure to carry out daily inspections and regular maintenance, and replace faulty components in time to ensure the safe operation of the equipment.
* If the equipment is scrapped, please comply with relevant laws to properly handle industrial waste and protect the environment.
* In order to prevent personnel from accidentally entering the working space of the equipment, be sure to set up safety fence to prevent personnel from entering the hazardous area.
* Before operating the robot, make sure that no one is inside the safety fence. When operating the robot, be sure to operate outside the safety fence.
* Do not expose the training system to permanent magnetic fields all the time. Strong magnetic fields can cause damage to the equipment.
* Dobot assumes no responsibility for equipment damage or personal injury caused by failure to follow product instructions or other improper operations.
* Dobot is not responsible for any damage caused during the transportation and handling of equipment.
* After removing the outer packaging, make sure that the robot maintains the original packing posture and the brakes of all axes are normal.

**WARNING**

* Before the operation, please wear antistatic uniform and protective gloves.
* It is prohibited to modify or remove the nameplates, instructions, icons and marks on the equipment.
* Be careful when carrying or installing the equipment. Please follow the instructions on the packing box to put down the robot gently and place it correctly in the direction of the arrow.
* When handling the robot, you need to carry it with both hands, with one holding the upper arm or forearm and the other holding the base, so as to keep the robot stable and avoid the base rotating randomly or other axes loosening to cause injury.
* Please use the matched cables for personal security and equipment protection.
* Please ensure that the robot and tools are installed correctly.
* Please ensure that the robot has enough space to move freely.
* Any impact will release a lot of kinetic energy, which is much higher than that under high speed and high load.

#### 1.3 Personal safety

When operating the robot system, please strictly follow the general precautions listed below to ensure the personal safety of the operator.

WARNING

* Please comply with local laws or regulations with regard to the maximum weight one person is permitted to carry.
* Do not touch the terminal blocks or disassemble the equipment with the power ON. Otherwise, it may result in an electric shock.
* Please confirm that the equipment is well grounded, otherwise it will endanger personal safety.
* Do not touch the terminal blocks or remove the interval circuit components within 10 minutes after the power is shut off, so as to avoid an electric shock since there is residual capacitance inside the equipment.
* Even if the power switch of the equipment is already in the OFF status, touching the terminal blocks or removing the interval circuit components is not allowed, so as to avoid an electric shock since there is residual capacitance inside the equipment.
* Please ensure that the safety measures are established near the robot operation area, such as guardrails, to protect the operator and surrounding people.

### 2. Product Introduction

The MG400 training system is an educational solution designed for vocational and higher education to help students understand the functions of standard automation systems and improve the effectiveness of training. A standard MG400 training system is shown in Figure1-1. The MG400, vision system and air pump box need to be

purchased separately.

The MG400 training system can realize the following functions:

* Robot programming and debugging
* User/Tool coordinate system settings
* Robot trajectory programming
* Robot handling and palletizing
* Machine vision coloured object recognition
* Machine vision dynamic tracking and picking

Figure1-1 MG400 training system

### 3. Layout Introduction

#### 3.1 Structural layout

The MG400 universal training platform is composed of MG400 industrial four axis robot unit, visual unit, feeding and transmission unit, mini air pump box, quick change board unit, tool box unit, etc , as shown in Figure1-2.

![Official MG400 training-system figure, source page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoGJqh5gflH7RrT2G2viZ%2Futp-a8bd0430ff688684cb35.jpg?alt=media)

Figure1-2 Structural layout

#### 3.2 MG400 Training Platform Core Unit

#### 3.2.1 Robot Unit

MG400 is a four axis desktop industrial robot independently developed by Yuejiang Technology that can support teaching , as shown in Figure1-3. It is flexible and easy to deploy, easy to use, and secure collaboration . MG400 can receive signals from visual units, execute corresponding robot commands, and complete corresponding actions.

Figure1-3 MG400

![Official MG400 training-system figure, source page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fa51vkwlbGCPKj3lgQr3d%2Futp-fc9b71767dbde84bd8c6.jpg?alt=media)

![Official MG400 training-system figure, source page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1QX9ZzzZC88zYUwyMHQL%2Futp-b06c3209d0a2a7057009.png?alt=media)

#### 3.2.2 Visual Unit

The visual unit has the advantages of rich function, stable performance and easy operation . It can meet the rich visual application needs of visual positioning, measurement, detection and recognition , as shown in Figure1-4 . The supporting visual software comes with more than 100 kinds of image processing operators and a powerful visual analysis tool library . It can quickly build machine vision application system to meet different application needs.

Figure1-4 Visual Unit

#### 3.2.3 Feeding and Conveying Unit

The feeding and conveying unit is mainly used to push materials from the silo to the conveyer belt , in order to achieve the transportation of materials between different positions . The conveyer belt adopts a built-in stepper motor, which can accurately control the pushing distance of the material . Driven by a DC deceleration motor, the movement of the convery belt can be controlled to meet the transportation needs of different materials . In addition, the conveyer belt is also equipped with an alignment sensor and encoder, which can accurately detect the position of materials on the convery belt . It can achieve dynamic tracking and grasping of materials by robots in space, improving the transportation efficiency and accuracy of materials , as shown in Figure1-5.

![Official MG400 training-system figure, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcE1mXX9tckGV2NGBgXYG%2Futp-6f9bc58a864a81fbca24.jpg?alt=media)

Figure1-5 Feeding and Conveying Unit

#### 3.2.4 Mini air pump box

The mini air pump box is a practical accessory independently designed and developed by DOBOT . It is used in conjunction with the Yue Jiang robot , as shown in Figure1-6 . The air pump box can provide a pressure range of -70\~110kPa. Its appearance design is exquisite . It can be directly adapted to DOBOT robots through I/O control interfaces, plug and play, and can be suitable for most daily suction cups and flexible gripper application scenarios.

Figure1-6 Mini air pump box

#### 3.2.5 Quick Change Board Unit

The training platform is equipped with 4 quick change board modules as standard, including: trajectory board, standard visual loading plate, mobile phone model workpiece loading plate, circular/rectangular workpiece loading plate , as shown in Figure1-7. The quick change board unit, in conjunction with the robot execution unit and visual unit , completes visual recognition, detection, and positioning of the experimental object , and completes process applications such as item tracking, positioning and grasping , stacking , and assembly .

![Official MG400 training-system figure, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFCGRvy9OHpul2Pb7e6PB%2Futp-747a4b8fd1f436a14a22.jpg?alt=media)

![Official MG400 training-system figure, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRtIJ0HtgbiWGvCk0bh0M%2Futp-d7d346c187303a094929.jpg?alt=media)

Figure1-7 Quick Change Board Unit

#### 3.2.6 Control Button Box

The Control Button Box is mainly composed of four buttons, namely "START", "STOP", "RESET" and "EMERGENCY STOP" , as shown in Figure1-8. The "EMERGENCY STOP" button is not affected by other control devices. When the emergency stop button is pressed, it will immediately stop the operation of the robot . The other three buttons are used to start, stop and reset the system by pressing the corresponding buttons on the touch screen automatic control interface.

Figure1-8 Control Button Box

Note：Only in the automatic control interface of the touch screen, the "Start", "Stop", and "Reset" buttons of the control button box can control the device. In other interfaces, the "Start", "Stop", and "Reset" buttons of the control button box cannot control the device.

#### 3.2.7 Main Control Unit

The Main Control Unit includes a PLC module and a touch screen module , as shown in Figure1-9. The PLC uses Siemens S7-1200, and the touch screen uses Siemens KTP700. Together with the touch screen, PLC can control the discharge of the cylindrical silo, the operation of the conveyor belt, and the detection of the workpiece in place . It also can perform human-machine interaction, monitor

![Official MG400 training-system figure, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8pJhh5LcD224tw7SehcT%2Futp-2fadd59a7c8e4373f450.jpg?alt=media)

![Official MG400 training-system figure, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZrGf2jU5OS3OAzFGAXws%2Futp-057ed7e5b6ddd8dd3ee4.png?alt=media)

![Official MG400 training-system figure, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLQtpWM54xW7f5Co8ybxy%2Futp-5e1abcbf2ab60daf643c.png?alt=media)

![Official MG400 training-system figure, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHYRqP4z0Wza1kYBkHKGg%2Futp-79f1f78f215f6adf7546.png?alt=media)

![Official MG400 training-system figure, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCX8EpFfr0t4oJO4Shd0E%2Futp-93919b21f01ee47c0a6c.png?alt=media)

equipment operation status, display the status of each IP port, and control system processes.

Figure1-9 Main Control Unit

### 4. Software Installation

#### 4.1 Install robot control software

* (1) Enter Dobot official website.

Search https://www.dobot-robots.com/ in the browser to enter Dobot website. Click **User** to enter “USER LOGIN” page, as shown in Figure1-10. Enter your email and password to enter “USER CENTER” page. (You need to register before login.)

Figure1-10 USER LOGIN

* (2) Download the latest robot control software.
* ①Click **Download Center** in “USER CENTER” page, as shown in Figure1-11.

![Official MG400 training-system figure, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0CmYxEcumtUwkX4yz6T6%2Futp-c3c7cc9eae41391fc090.jpg?alt=media)

![Official MG400 training-system figure, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaBVRiaPgTXaVTKg33mho%2Futp-dd3cf8f03bafe40a1dba.jpg?alt=media)

Figure1-11 USER CENTER

②Click **Control Software** in “DOWNLOAD CENTER” page. Click on

the right side of DobotStudio Pro v2.6.1 to download the software, as shown in Figure1-12.

Figure1-12 Download software installation package

* (3) Enter installation guide interface.

Double click the downloaded software, and an installation guide interface will

pop up, as shown in Figure1-13.

![Official MG400 training-system figure, source page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz0uaK89HD9QO388YuKQL%2Futp-e5ae34c73771fa1a215d.png?alt=media)

![Official MG400 training-system figure, source page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FutUEmZf4HNZNz0uXtMTt%2Futp-e34c34c807c7a8a763ef.png?alt=media)

Figure1-13 Installaition guide

(4) Select the installation path.

Click **Next** . Then click **Custom options** and **Browse** to select the installation path, as shown in Figure1-14.

Figure1-14 Select installation path

(5) Start installation.

Click **Install Now** to start installing DobotStudio ProV2.6.1, as shown in

Figure1-15.

![Official MG400 training-system figure, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPgMkmqPRYb0kSqyzNQ9e%2Futp-ef80dd809274bf79d627.jpg?alt=media)

![Official MG400 training-system figure, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdLoZsYrwkJrloKqvniYA%2Futp-0c420c53e66a4b86452e.jpg?alt=media)

Figure1-15 Installing software

* (6) Finish installation.

After installation, click **Experience Now** to enter the software, as shown in

Figure1-16.

Figure1-16 Installation finished

* (7) Know about the software interface.

The main interface mainly includes four parts, as shown in Figure1-17.

![Official MG400 training-system figure, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9ab4ektunX58ZUQlsdGd%2Futp-194c7a143678ea8d4897.jpg?alt=media)

![Official MG400 training-system figure, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUvP72RLZNVQd1bwGoqkN%2Futp-7311119d0ded4b525479.png?alt=media)

Figure1-17 Main interface

* Area 1: Top Toolbar. It includes menu, homepage button, connection panel,alarm log, enabling button, global speed setting, emergency stop switch, etc.
* Area 2: Recent Projects. Display the recent projects,which you can click to open quickly.
* Area 3: Major Functions. It includes DobotBlockly, Script, Setting and Process.
* Area 4: Tools Panel. Click the icon on the right toolbar to display or hide the corresponding panels, including Control, I/O , Modbus, Global Variable and Dobot+. The control panel is displayed by default after DobotStudio Pro is connected to the robot successfully.

Note: For specific functions of each tool, see its corresponding user guide.

#### 4.2 Install vision software

(1) Enter Dobot official website.

Search https://www.dobot-robots.com/ in the browser to enter Dobot website. Click **User** to enter “USER LOGIN” page. Enter your email and password to enter “USER CENTER” page as shown in Figure1-18. (You need to register before login.)

![Official MG400 training-system figure, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3qxfeEp2MR82RlShtl04%2Futp-cccdbb6c71c4391888e3.png?alt=media)

![Official MG400 training-system figure, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAwnJgDT2KWw7M5kqH44q%2Futp-61eacffc6e65b67e629a.png?alt=media)

Figure1-18 USER LOGIN

* (2) Download the latest vision software package.
* ①Click **Download Center** in “USER CENTER” page, as shown in Figure1-19 .

Figure1-19 USER CENTER

Click **Control Software** in “DOWNLOAD CENTER” page. Click on the

right side of DobotVisionStudio v4.1.2 to download the vision software, as shown in Figure1-20.

Figure1-20 Download vision software package

![Official MG400 training-system figure, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaBVRiaPgTXaVTKg33mho%2Futp-dd3cf8f03bafe40a1dba.jpg?alt=media)

![Official MG400 training-system figure, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz0uaK89HD9QO388YuKQL%2Futp-e5ae34c73771fa1a215d.png?alt=media)

![Official MG400 training-system figure, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEbSpmNT7O7ekSq0sVpsL%2Futp-760ecfec932a64662a00.png?alt=media)

* (3) Install vision software

Decompress the installation package and double click **DobotVisionStudio 4.1.2.**

**exe** to install it, as shown in Figure1-21.

Figure1-21 Vision installation file

* (4) Select a language

Select **English** , and click **OK** , as shown in Figure1-22.

Figure1-22 Select a language

* (5) Welcome to DobotVisionStudio4.1.2 Setup

Enter “Welcome to DobotVisionStudio4.1.2 Setup” page, and click **Next** . Install

the software according to the guide, as shown in Figure1-23.

![Official MG400 training-system figure, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8CMQqD493aHnfmwUGLtw%2Futp-24a948e307da623feb9a.png?alt=media)

![Official MG400 training-system figure, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNUDAeDEQfwuqLJ8Q9PJY%2Futp-e91c7bdeb79dbda555d5.jpg?alt=media)

Figure1-23 Welcome to DobotVisionStudio4.1.2 Setup

* (6) Choose Components

In “Choose Components” page, select **Hard Encrytion** , **AlgorithmInstall** and

**CameraDriver** . Then click **Next,** as shown in Figure1-24.

Figure1-24 Choose Components

* (7) Choose Install Location

Click **Browse...** to define the installation path of the software. Then click **Install** ,

as shown in Figure1-25 and Figure1-26.

![Official MG400 training-system figure, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft4fJob4CCG6c2e3xnyi9%2Futp-aa23979bc85c16299ec1.png?alt=media)

Figure1-25 Choose Install Location

Figure1-26 Installing

* (8) Finish installation

Select **Run DobotVisionStudio4.1.2** and click **Finish** to exit the installation, as

shown in Figure1-27.

![Official MG400 training-system figure, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhXDhIxnpEXNRUSpG88Wo%2Futp-0e8487bbc32964408ec3.png?alt=media)

![Official MG400 training-system figure, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ0H8VWbDWDJvQ8DZF38U%2Futp-f0708a1fc5b62b6345a6.png?alt=media)

<br>

Figure1-27 Installation finished

* (9) Know about the vision software interface

Open the software and select **General Solution** to enter the corresponding

software interface, as shown in Figure1-28.

Figure1-28 Main interface

Area 1: Menu Bar. It includes File, Settings, System, Tools and Help.

![Official MG400 training-system figure, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp5UzAHvqp85f9UxxVC8S%2Futp-23c0e50705320f1d0bd0.jpg?alt=media)

![Official MG400 training-system figure, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuNRYLyCNWAPdB6cccFaO%2Futp-73a1788edc7e6eabea0f.png?alt=media)

Area 2: Control Toolbar. It provides quick operations for the software, including file saving, file open, camera management, controller management, etc.

Area 3: Tool Box. It includes image collection, positioning, measurement, identification, calibration, position, image processing, colour processing, defect detection, logic tools, communication, etc.

Area 4: Flow Toolbar. It provides quick operations for flows.

Area 5: Flow Process. You can edit the flow here.

Area 6: Overview. It provides an overview of the flow.

Area 7: Status. It displays flow time, tool time and algorithm time.

Area 8: Image. Image is displayed here.

Area 9: Results. You can view current results, history results and help information.

Note: For specific functions of each tool, see its corresponding user guide.

#### 4.3 Install camera MVS client software

The industrial camera MVS client is a software application developed for debugging industrial cameras. It is applicable to GigE and USB3.0 interface industrial surface and line cameras, and supports real-time preview, parameter configuration, image capture and camera firmware upgrading. It is applicable to CameraLink interface industrial surface and line cameras, and supports parameter configuration and camera firmware upgrading.

(1) Find MVS file.

Double click MVS\_STD\_3.1.0\_181229.exe in the installation package to install it, as shown in Figure1-29.

Figure1-29 MVS installation file

(2) Select a language.

Accept the agreement, select a language, and click **Start Setup** , as shown in

Figure1-30.

Figure1-30 Select language

* (3) Set installation options.

Before installing the software, you need to set the installation path, set the driver,

and select whether to enable built-in debug features and whether to enable Jumbo Frames for all NICs. The default settings interface is shown in Figure1-31.

![Official MG400 training-system figure, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvAJGsrz2ZsKOpSRvz2Ys%2Futp-b3e06cd8d53e18e125f6.jpg?alt=media)

Figure1-31 Options

* (4) Confirm your settings and click **Next** . Then the software starts to be installed,

as shown in Figure1-32.

Figure1-32 Installing

* (5) After installation, you can set whether to run the client and whether to open

![Official MG400 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbujbDGvU6AX7rzBLw7Ia%2Futp-05564233659fadbce52f.jpg?alt=media)

![Official MG400 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCDbbnNCYQ9DX5jx4mAhg%2Futp-404cef0b2415219f1128.jpg?alt=media)

the release note, as shown in Figure1-33.

Figure1-33 Installation finished

* (6) Know about the software interface

After starting the MVS software, you will see the main interface as shown in

Figure1-34, which includes six parts.

![Official MG400 training-system figure, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNu2lIqKCYhwl2qdx1l2Y%2Futp-ee8c1b094db94c47ea32.jpg?alt=media)

Figure1-34 Main interface

Area 1: Menu Bar. Function modules including File, View, Settings, Tool and Help.

Area 2: Control Toolbar.

Area 3: Display the GigE Vision cameras, USB3 Vision cameras and Camera Link cameras. Provide icons for connecting/disconnecting camera, start/stop acquisition, and refreshing device list.

Area 4: Interface and Device Information Panel. Display the network interface information and the device information.

Area 5: Display Window. View the live video of the selected camera.

Area 6: Feature Panel. View and configure features of the selected camera, and

perform other operations such as importing, exporting and saving features.

Note: For specific functions of each tool, see its corresponding user guide.

![Official MG400 training-system figure, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ2wFIPquAt5xSqHH6FOD%2Futp-3b05690978790c003e67.png?alt=media)

## Chapter 2 Trajectory Simulation

### 1. Introduction

In the trajectory simulation demo, the end of the robot can move along the specified trajectory based on the taught points, as shown in Figure2-1 .

Figure2-1 Trajectory simulation

### 2. Program Debugging

#### 2.1 Preparation

#### 2.1.1 Turn on system power switch

Connect the power plug of the robot and MG400 platform to the power supply,

and turn on the switch , as shown in Figure2-2.

![Official MG400 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO7axeqq7Bfl0PGHFCk3a%2Futp-6b6d5ebf8f32ade52c20.jpg?alt=media)

Figure2-2 Turn on MG400 training system power switch

#### 2.1.2 Power on the robot

Press the power button on the back of MG400 base to **ON** , as shown in Figure2-

3.

Figure2-3 MG400 power switch

#### 2.1.3 Install calibration needle

* (1) Prepare material.

Prepare the flange, suction cup and corresponding screws, as shown in Figure2-4.

Figure2-4 Prepare material

![Official MG400 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCwqugTyNCXJ4ScFtsPbm%2Futp-0076dbaf76d70f61b0ed.jpg?alt=media)

![Official MG400 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm3hEvrncz6V8JXMlvtfu%2Futp-3dd338c090ce87ce8961.jpg?alt=media)

![Official MG400 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FegvAbwDsk0jj2rz0otCA%2Futp-9bcc5697d7a403995934.jpg?alt=media)

* (2) Install the suction cup on the flange through four screws using inner
* hexagonal tools, as shown in Figure2-5.

Figure2-5 Install calibration needle on the flange

* (3) Install the flange installation plate on the end of the robot using inner
* hexagonal tools, as shown in Figure2-6.

Figure2-6 Install flange installation plate on the end of robot

* (4) Remove the suction nozzle from the suction nozzle connecting rod and install
* the calibration needle, as shown in Figure2-7.

![Official MG400 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWxL4RNb6ZmtMRfbQq7uU%2Futp-149206b8131250211b8b.jpg?alt=media)

![Official MG400 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0X63NarF95oZiAkXMk69%2Futp-019f2e3035d9a3072c87.jpg?alt=media)

![Official MG400 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYjKJQpicvh8pjFqfHsO5%2Futp-275b33405d774c2b62a3.jpg?alt=media)

Figure2-7 Install the calibration needle

#### 2.1.4 Place trajectory board

Place the trajectory board on the conveyor, as shown in Figure2-8.

Figure2-8 Place trajectory board

#### 2.2 Connect robot

* (1) Connect the robot to the computer.

Connect the other end of the robot network cable to the PC.

* (2) Modify IP of the computer.

Open the control panel of the computer. Select **Network and Internet/Network**

**and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure2-9. The default address of the robot is “192.168.1.6”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168. 1.18” as an example.

![Official MG400 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU8f3s1912FrCNJfYj7uq%2Futp-8e324eaad734ff3ad644.jpg?alt=media)

Figure2-9 Set IP of PC

* (3) Connect DobotStudio Pro to the robot.

Double click DobotStudio Pro 2.6.1 to open the software. Select **MG400** on the

top toolbar and click **Connect** , as shown in Figure2-10.

Figure2-10 Connect robot

After successful connection, you will see a prompt message, and the connection

![Official MG400 training-system figure, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ89x7p1g0OJlCffikCkd%2Futp-758d932b2eaf6708247a.png?alt=media)

![Official MG400 training-system figure, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvwreaHWHw13NvygKW42W%2Futp-1e3505e4739bad1742d4.png?alt=media)

status will change to **Connected** , **Online** and **Safe-L1** , as shown in Figure2-11.

Figure2-11 Robot connected

#### 2.3 Enable robot

Click on the top toolbar of DobotStudio Pro interface. Set **Payload** to **200g** in “Set load params” window. Set **Offset x** and **Offset y** to **0mm** , as shown in

Figure2-12. Click **OK** , and the icon turns to

Figure2-12 Set load parameters

#### 2.4 Set Global Speed

Click **Global Speed** button on the top toolbar to set it to 30% , as shown in Figure2-13.

Figure2-13 Set Global speed

#### 2.5 Import program

![Official MG400 training-system figure, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ftcq9BZOnZ5XshiBRVH0M%2Futp-02e8fbe129fd12056302.jpg?alt=media)

* (1) Open DobotStudio Pro and enter Script page. Click **File** > **Import project** , as
* shown in Figure2-14.

Figure2-14 Import project

Select “Trajectory Simulation” folder, and click **Open** to import the trajectory simulation program into DobotStudio Pro.

Note: If the trajectory file has been saved before, you can click **File** > **Open** >

**Trajectory\_Simulation** to open it.

#### 2.6 Debug points

You need to debug 40 points in this demo. The points on the trajectory board are

shown in Figure2-15.

![Official MG400 training-system figure, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLeqxgeOUkD2g26gwYFrj%2Futp-dacf360c67e0778a3524.png?alt=media)

![Official MG400 training-system figure, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuqKv8XL4WkcffBpR5ZHa%2Futp-35a9b81cd9cf59a87922.jpg?alt=media)

Figure2-15 Trajectory board points

(1) Drag the robot to move over the trajectory board, as shown in Figure2-16. Click **Cover** in the point list to update P1 (HOME point), as shown in Figure2-17. Then click **OK** in the pop-up Tips window.

Figure2-16 Point P1

Figure2-17 Update P1

(2) Jog or drag the robot to point gj1 on the trajectory board, as shown in Figure2-18. Click **Cover** in the point list to update P2, as shown in Figure2-19. Then

![Official MG400 training-system figure, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYVHiqA6naGHIC5mjlBAD%2Futp-1178236e674e04cb63c8.jpg?alt=media)

![Official MG400 training-system figure, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtdAjAsxEQ104VNFYRFI9%2Futp-5f160379c7908db5d253.png?alt=media)

click **OK** in the pop-up Tips dialog box.

Figure2-18 Locate Point gj1

Figure2-19 Update P2(gj1)

(3) Jog or drag the robot to point gj2 on the trajectory board, as shown in Figure2-20. Click **Cover** in the point list to update P3, as shown in Figure2-21. Then click **OK** in the pop-up Tips dialog box.

![Official MG400 training-system figure, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3A4dunchddfKjL5aRr1H%2Futp-5ab3e559cb5f7c81b42e.jpg?alt=media)

![Official MG400 training-system figure, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FleOAFlWB1qQCLJeY3f7B%2Futp-80035de31bab433ab0f1.png?alt=media)

Figure2-20 Locate Point gj2

Figure2-21 Update P3(gj2)

(4) Repeat the steps above to teach the remaining 38 points. The updated points are shown in Figure2-22.

![Official MG400 training-system figure, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBOCe49j7UONN1z14xQJj%2Futp-ac6e3b771cdb0afcc89e.jpg?alt=media)

![Official MG400 training-system figure, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FurGiwPuN3cfklVbE2Bnk%2Futp-e1ca20b5f3d8cc393b10.png?alt=media)

**（1）P1-P8 （2）P9-P17**

**（3）P18-P26**

**（4）P27-P35**

![Official MG400 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FL5ns53elx5Cz7i2OwcAF%2Futp-0a5574252a1de2490b16.jpg?alt=media)

![Official MG400 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhKEY3FOk4zvMunfg0Y7r%2Futp-2602a30da091da7bbf4b.png?alt=media)

![Official MG400 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F456TdqPrJDcC64vjrjFO%2Futp-ded04e3a4198a5564c16.png?alt=media)

![Official MG400 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcC0f7uLQjPBo013kzUym%2Futp-1f1de49333343a2ce3dd.jpg?alt=media)

![Official MG400 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkJ1aVP7VHhe2To3QjgXI%2Futp-b67aee9548a571c8cf36.png?alt=media)

（5）P36-P41

Figure2-22 Updated points

#### 2.7 Save program

Click , and enter a project name in the pop-up dialog box, as shown in

Figure2-23.

Figure2-23 Save program

Note: Saving a program refers to saving the program to the robot controller. If you want to

save the program to local, you need to export the project.

#### 2.8 Run program

Click to run the program, and observe whether the robot moves

following the trajectory.

Note: After the program completes running, if the program does not exit the running status

automatically, click .

#### 2.9 Export program

Click **File** > **Export project** , and select the path to save the program. Then enter

a project name in the pop-up dialog box.

Note: Exporting a project refers to export the program to local for backup.

![Official MG400 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpTBZbNyyHT1Or7dAx0wV%2Futp-1109ac8535b7b43df27b.png?alt=media)

### 3. Key Program Description

This section mainly describes the key script. For complete script, see the project in Script page.

The trajectory simulation is mainly about moving between different points, as shown in Figure2-24.

Figure2-24 Trajectory points

As the trajectory consists of shapes with different characteristics, the robot moves in four modes: **Go** for point-to-point motion, **Move** for linear motion, **Arc** for arc motion, and **Circle** for circular motion.

![Official MG400 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjDMUKhNTVzFE72239NEY%2Futp-338453cdb6cf14d13c66.png?alt=media)

![Official MG400 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMcI9e4bB2tPvfnxZgMYh%2Futp-0fd8bea31c9b223e7c03.png?alt=media)

## Chapter 3 Application of Static Palletizing

### 1. Introduction

The specific task of static palletizing is to use the robot to carry six rectangular blocks placed in a 3×3×1 matrix on the standard vision board to the storage area and

code it as 1×3×3 stacks, as shown in Figure3-1 and Figure3-2.

Figure3-1 Palletizing blocks

Figure3-2 Storage area

### 2. IO Configuration

The IO configuration of static palletizing is shown in Table3-1.

**Table3-1 IO configuration**

| **Output** | **Description** |
| ---------- | --------------- |
| DO09       | Vacuum pumping  |
| DO10       | Vacuum breaking |

![Official MG400 training-system figure, source page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyH6K1m06odBXsDVy3Oro%2Futp-eb579dd867085cc54578.jpg?alt=media)

![Official MG400 training-system figure, source page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fy2SxfZU25MtgdXYxKKRg%2Futp-edfcebfe0ff03d76a43f.jpg?alt=media)

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on system power switch

Connect the power plug of the robot and MG400 platform to the power supply,

and turn on the switch , as shown in Figure3-3 .

Figure3-3 Turn on MG400 training system power switch

#### 3.1.2 Power on the robot

Press the power button on the back of MG400 base to **ON** , as shown in Figure3-

4.

Figure3-4 Power on the robot

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to **Auto** ,

as shown in Figure3-5.

![Official MG400 training-system figure, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FunIDBurppg3l241G9knH%2Futp-103c4534b72fa9100342.jpg?alt=media)

![Official MG400 training-system figure, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7CT93DwhXcAhOHyvKk3o%2Futp-ecb037f94495a885f4b3.jpg?alt=media)

Figure3-5 Turn on the power switch of the pump box

#### 3.1.4 Install eccentric suction cup

* (1) Prepare the flange, the eccentric flange, the suction cup and corresponding

screws, as shown in Figure3-6.

Figure3-6 Material preparation

* (2) Install the suction cup and the flange on the eccentric flange through eight

screws using inner hexagonal tools, as shown in Figure3-7.

Figure3-7 Assemble eccentric tool

(3) Install the eccentric tool to the end of robot using inner hexagonal tools. Connect one end of the air pipe to the suction cup and the other end to the robot air

![Official MG400 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyCHCNwEo95N0rrXXxvOy%2Futp-1ceddb11d257e1615ae6.jpg?alt=media)

![Official MG400 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCmAtESsGDEI8g0WTogbi%2Futp-c51693c9c3083a30b605.jpg?alt=media)

![Official MG400 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDQS95XgqG9uYUFOsaGiJ%2Futp-933a080711277b3a8cfb.jpg?alt=media)

pipe interface, as shown in Figure3-8.

Figure3-8 Install eccentric tool on the end of robot

#### 3.1.5 Install standard vision board

Install the standard vision board above the conveyor , as shown in Figure3-9.

Figure3-9 Install standard vision board

#### 3.2 Connect robot

* (1) Connect the robot to the computer.

Connect the other end of the robot network cable to the PC.

* (2) Modify IP of the computer.

Open the control panel of the computer. Select **Network and Internet/Network**

**and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure3-10. The default address of the robot is “192.168.1.6”. You can change the IP address of the PC to any

![Official MG400 training-system figure, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0kIr2m1Jemo7noEnVov5%2Futp-8941c0b2f43e6a68fed8.jpg?alt=media)

![Official MG400 training-system figure, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1z0edXaYcXnUKgPc5Oh4%2Futp-29da838e64ab108ebcf3.jpg?alt=media)

IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168.

* 1.18” as an example.

Figure3-10 IP setting of PC

* (3) Connect DobotStudio Pro to the robot.

Double click DobotStudio Pro to open the software. Select **MG400** on the top

toolbar, and click **Connect** , as shown in Figure3-11.

![Official MG400 training-system figure, source page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ89x7p1g0OJlCffikCkd%2Futp-758d932b2eaf6708247a.png?alt=media)

Figure3-11 Connect robot

After successful connection, you will see a prompt message, and the connection

status will change to **Connected** , **Online** and **Safe-L1** , as shown in Figure3-12.

Figure3-12 Robot connected

#### 3.3 Enable robot

Click on the top toolbar of DobotStudio Pro interface. Set **Payload** to **200g** in “Set load params” dialog box. Set **Offset x** and **Offset y** to **0mm** , as shown in

Figure3-13. Then click **OK** . The Enabling icon changes to .

![Official MG400 training-system figure, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLsrJeYWECazjjw3FRs5u%2Futp-a3cc10b423bbc6118638.jpg?alt=media)

Figure3-13 Set load parameters

#### 3.4 Set Global Speed

Click **Global Speed** button on the top toolbar to set it to 30% , as shown in Figure3-14.

Figure3-14 Set Global speed

#### 3.5 Establish tool coordinate system

The Tool coordinate system is generated by the two-point calibration method. After installing an end effector on MG400, adjust the posture of the tool to make the TCP (Tool Center Point) align with the same point (reference point) in space with two different postures. Obtain the position offset of the tool, and generate the tool coordinate system, as shown in Figure3-15.

![Official MG400 training-system figure, source page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ftcq9BZOnZ5XshiBRVH0M%2Futp-02e8fbe129fd12056302.jpg?alt=media)

Figure3-15 Tool coordinate system example

(1) Remove the suction nozzle from the suction nozzle connecting rod . Install

the calibration needle, as shown in Figure3-16.

Figure3-16 Install the calibration needle

(2) Click **Settings** > **Coordinate System** > **Tool Frame** on DobotStudio Pro main page.

(3) Select Tool coordinate system 1, and click **Modify** to update the coordinate system (if there is only No. 0, you can click **Add** to add a coordinate system), as shown in Figure3-17.

![Official MG400 training-system figure, source page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZPzJXkHscxdCP2Ys2VPI%2Futp-e83e5774f9f6cf555489.jpg?alt=media)

![Official MG400 training-system figure, source page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiRZatR60MrBPbvMalUUX%2Futp-9999962d5a63a5eccf6e.jpg?alt=media)

Figure3-17 Select “Tool Frame”

* (4) Click **Two points setting** , as shown in Figure3-18.

Figure3-18 Select Two points setting

(5) Place the calibration paper on the standard vision board. Jog MG400 to align

![Official MG400 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmndK747fpp1kXuLkx6UY%2Futp-58ae4fe08c064ad9e6a6.png?alt=media)

![Official MG400 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaRIZLkbSDC6ghSz6TzFp%2Futp-42b02a49b644e6f95d2e.png?alt=media)

the needle at the end of the robot with the center point of the calibration paper, as

shown in Figure3-19. Then click **obtain** on P1 panel, as shown in Figure3-20.

Figure3-19 the first positioning center point

Note: In order to avoid the vision interference of the patterns on the standard vision board,

you can place a white piece of paper on the standard vision board.

Figure3-20 Obtain P1

(6) Jog the R value in the Control panel to change the posture and make the

![Official MG400 training-system figure, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F27lEAmZBcEbY2sJ5g3Zo%2Futp-4822382a35114282f17b.jpg?alt=media)

![Official MG400 training-system figure, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmndK747fpp1kXuLkx6UY%2Futp-58ae4fe08c064ad9e6a6.png?alt=media)

needle at the end of the robot align with the center point again, as shown inFigure3-21.

Then click **obtain** on P2 panel, as shown in Figure3-22.

Figure3-21 the second positioning center point

Figure3-22 Obtain P2

* (7) Click **OK** . The Tool coordinate system 1 is updated.
* (8) Modify the **Tool Frame** to **1** on the Control panel, as shown in Figure3-23.

![Official MG400 training-system figure, source page 53](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGw6P2Ea4H5WcRoRjMOGJ%2Futp-bb69a665215028211e91.jpg?alt=media)

![Official MG400 training-system figure, source page 53](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmndK747fpp1kXuLkx6UY%2Futp-58ae4fe08c064ad9e6a6.png?alt=media)

Figure3-23 Modify the Tool Frame

Note: By clicking "Rx+" or "Rx -" on the jog panel, it can be observed that regardless of the "R" value, the calibration needle is aligned with a point in the middle of the calibration board. If there is no alignment, it indicates that the tool coordinate system calibration is inaccurate and needs to be recalibrated.

After the calibration of the tool coordinate system is completed, it is necessary to remove the calibration needle from the suction nozzle connecting rod and replace it with a suction nozzle.

#### 3.6 Import program

* (1) Open DobotStudio Pro and enter Script page. Click **File** > **Import project** ，

as shown in Figure3-24.

![Official MG400 training-system figure, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMKgzhpSUyd6an6FPfBIR%2Futp-bfd6af3a47041e030843.jpg?alt=media)

![Official MG400 training-system figure, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLeqxgeOUkD2g26gwYFrj%2Futp-dacf360c67e0778a3524.png?alt=media)

Figure3-24 Import project

(2) Select **Palletizing** folder and click **Open** , as shown in Figure3-25. Now the static palletizing program has been imported into DobotStudio Pro, as shown in Figure3-26.

Figure3-25 Import path

Figure3-26 Project imported

Note: If the static palletizing file has been saved before, you can click **File** > **Open** >

**Palletizing** to open it.

#### 3.7 Prepare material

Place six blocks in the lower right corner of the standard vision board in a 2×3

![Official MG400 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWG3mUQTnsH1pc6FMfRY5%2Futp-b40320516324d80003b1.png?alt=media)

![Official MG400 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNoXFbYw68EWO7IMtT87S%2Futp-95acd7305d5030e16668.png?alt=media)

matrix, as shown in Figure3-27 .

Figure3-27 Palletizing blocks

#### 3.8 Debug points

Static stacking uses 3 points, and the debugging method is as follows:

* (1) Update safe point P1.

The tool coordinate system is "1". Jog or drag the robot to a position between the

conveyor and the storage area, as shown in Figure3-28.

Figure3-28 Locate Point P1

Click **Points** in the right-side menu of DobotStudio Pro. Select **P1** and click

**Cover** , as shown in Figure3-29. Then click **OK** in the pop-up Tips dialog box.

![Official MG400 training-system figure, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FewU2uuBgjFM7yQpqiPx4%2Futp-6b13d6fe8a34286f1873.jpg?alt=media)

![Official MG400 training-system figure, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2wgp5YmMpsoOQjdPXiaE%2Futp-399a2f18b49435a71d44.jpg?alt=media)

Figure3-29 Update P1

* (2) Update picking point P2.

Jog or drag the robot to the picking point of the first block on the standard vision board. The suction cup needs to touch the centre of the first block, as shown in Figure3-30. Then select **P2** in **Points** , and click **Cover** , as shown in Figure3-31. Then click **OK** in the pop-up Tips dialog box.

Figure3-30 Locate the first Picking point P2

![Official MG400 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSiIIPaQGGTA9VoZc3AdP%2Futp-64038bdced5acf99d454.jpg?alt=media)

![Official MG400 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJEAMti2G5lDW4CyRyi5l%2Futp-b02df9d579b46b339e0a.jpg?alt=media)

Figure3-31 Update P2

* (3) Update placing point P3.

Open **I/O** panel. Set **DO\_09** to **ON** to make the robot suck the block, as shown in Figure3-32. Then jog the robot to move to the first placing point (P3) in the storage area, as shown in Figure3-33. Select **P3** in **Points** and click **Cover** , as shown in Figure3-34. Then click **OK** in the pop-up Tips dialog box.

![Official MG400 training-system figure, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpOa6DDIElVjsjndaoYIl%2Futp-1e3514b4e2a1cc55cbdc.jpg?alt=media)

Figure3-32 I/O panel

Figure3-33 Locate the first Placing point P3

![Official MG400 training-system figure, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgxI8Kdnnz0j4otZnJHCC%2Futp-53d546276235f127fbfd.png?alt=media)

![Official MG400 training-system figure, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqsSBu6DsaCBJbWiTNy6W%2Futp-5db17a07db7db3b33465.jpg?alt=media)

Figure3-34 Update P3

Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the block is placed into the groove accurately. If not, you need to re-debug the point.

#### 3.9 Save program

Click and enter a project name in the pop-up dialog box, as shown in

Figure3-35.

![Official MG400 training-system figure, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2F0K4XoeFfbWw37iEn2R%2Futp-957fe09e341e294d0aa6.png?alt=media)

Figure3-35 Save program

Note: Saving a program refers to saving the program to the robot controller. If you want to

save the program to local, you need to export the project.

#### 3.10 Run program

Click . Observe whether the program is running as follows: The robot puts the blocks arranged in a 3×3×1 matrix on the standard vision board into the storage area and code it as 1×3×3 stacks, as shown in Figure3-36.

Figure3-36 Palletizing effect

#### 3.11 Export project

![Official MG400 training-system figure, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsZK76RdiS9tEZ5PZPrh6%2Futp-050098b59f04ac1a5da0.png?alt=media)

![Official MG400 training-system figure, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLecYTvBonw5ijonuK3La%2Futp-3931fdca58129c226f7d.jpg?alt=media)

Click **File** > **Export project** , and select the path to save the program. Then enter

a project name in the pop-up dialog box, as shown in Figure3-37.

Figure3-37 Export project

Note: Exporting a project refers to exporting the program to local for backup.

### 4. Key Program Description

This section mainly describes the key script. The complete code can be viewed in

the script project page.

#### 4.1 Output port reset program

The output port reset program is shown in Figure3-38, which sets all output ports

to **OFF** .

Figure3-38 Output port reset program

#### 4.2 Robot pick-up program

The robot pick-up program is shown in Figure3-39, which controls the robot to pick up the blocks from the standard vision board.

![Official MG400 training-system figure, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCWYMfs2BWyFfMUyYedU7%2Futp-02ff1e9718051bb9a0a4.png?alt=media)

Figure3-39 Robot pick-up program

You only need to teach and save the placing point P2 of the first block. Then the corresponding coordinates of 8 other picking points can be obtained according to the distance between the first picking point and each of the remaining picking points.

The order of material collection is shown in Figure3-40, with the red column

taken first, followed by the green column, and finally the white column.

Figure3-40 The order of material collection

#### 4.3 Robot placement program

The robot placement program is shown in Figure3-41, which controls the robot to place nine blocks into the storage area and code it as 1×3×3 stacks.

![Official MG400 training-system figure, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJuIxx2iDSPoO8cMFoRj2%2Futp-ed4f66807c285468ef0c.png?alt=media)

![Official MG400 training-system figure, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0t0tg3jhfez6zY5mmo3k%2Futp-6edef2aeca3e7257cb80.jpg?alt=media)

Figure3-41 Robot placement program

You only need to teach and save the placing point P3 of the first block. Then the corresponding coordinates of 8 other placing points can be obtained according to the distance between the first placing point and each of the remaining placing points.

![Official MG400 training-system figure, source page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeVJgngatimBDzCyjQ6py%2Futp-11b3ab7fb8ac64bc3455.png?alt=media)

## Chapter 4 Application of Robot Handling

### 1. Introduction

The task that the robot handling application aims to achieve is to push 12 circular workpieces from the silo onto the conveyor belt through a push motor, and then the robot will transport the workpieces conveyed by the conveyor belt to the storage area. During the operation of the system, the device can be controlled to stop, reset, and start by pressing the buttons on the touch screen or the buttons on the control button box. At the same time, the operating status of the device can be feedback through the color of the tricolor light. The buttons on the control button box are shown in Figure4-

1.

Figure4-1 Control Button Box

The specific task description is as follows:

The robot handling application project is controlled by buttons on the touch screen or buttons on the control button box, and there are two modes: manual control and automatic control. The manual control mode is mainly used for debugging, and can control the tricolor light, buzzer, pushing motor, and conveyor belt by pressing the buttons on the touch screen. In automatic control mode, the buttons on the touch screen or on the control button box control the stop, reset, and start of the system .

Firstly, the robot moves to a safe point and sends a discharge signal to the PLC . After receiving the signal, PLC starts the push motor, which pushes the workpiece out of the cylindrical silo (as shown in Figure4-2). Then turn on the conveyor belt, which moves the workpiece forward. When the in place detection sensor detects that the workpiece has arrived, the PLC sends a material arrival signal to the robot. After receiving the signal, the robot takes the workpiece from the conveyor belt and

![Official MG400 training-system figure, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMfCIumOX1CyR1OP3bEbj%2Futp-6e04b7b3d4ee389c4bb0.jpg?alt=media)

transports it to the corresponding location in the storage area. This cycle is repeated 12 times, and the robot moves the circular workpiece to the circular groove of the rectangular/circular workpiece loading plate in the storage area, arranged in a 3X2X2 array, as shown in Figure4-3.

Figure4-2 Cylindrical Silo

Figure4-3 Storage Area

### 2. IO Configuration

The Robot IO configuration of the Robot Handling is shown in Table4-1 . The PLC IO configuration is shown in Table4-2. The HMI IO configuration is shown in Table4-3.

Table4-1 Robot IO configuration

| DO   | **Description** |
| ---- | --------------- |
| DO09 | Vacuum pumping  |
| DO10 | Vacuum breaking |

Table4-2 PLC IO configuration

| **DI**                  | **Description** | **DO**                   | **Description** |
| ----------------------- | --------------- | ------------------------ | --------------- |
| PL&#x43;**\_**&#x49;N01 | START           | PL&#x43;**\_**&#x4F;UT01 | Green light     |
| PL&#x43;**\_**&#x49;N02 | STOP            | PL&#x43;**\_**&#x4F;UT02 | Yellow light    |
| PL&#x43;**\_**&#x49;N03 | RESET           | PL&#x43;**\_**&#x4F;UT03 | Red light       |

![Official MG400 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5EwWBfAE3Ja7O0CorYTf%2Futp-f2b2afbd9d4b406049ec.jpg?alt=media)

![Official MG400 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyTKmdUAmHDbW3M10NyhY%2Futp-279f5f907ecb7b8fdfcd.jpg?alt=media)

Application of Robot Handling

| PL&#x43;**\_**&#x49;N04 | RESERVE                                            | PL&#x43;**\_**&#x4F;UT04 | buzzer              |
| ----------------------- | -------------------------------------------------- | ------------------------ | ------------------- |
| PL&#x43;**\_**&#x49;N05 | Material inspection in the silo                    | PL&#x43;**\_**&#x4F;UT05 | Pushing motor start |
| PL&#x43;**\_**&#x49;N06 | <p>Material inspection on the<br>conveyor belt</p> | PL&#x43;**\_**&#x4F;UT06 | Conveyor start      |

Table4-3 HMI IO configuration

| **DI**                  | <p><strong>Correspon-</strong><br><strong>dence</strong></p> | **Description**                           | **DO**                   | <p><strong>Correspo-</strong><br><strong>ndence</strong></p> | **Description**                    |
| ----------------------- | ------------------------------------------------------------ | ----------------------------------------- | ------------------------ | ------------------------------------------------------------ | ---------------------------------- |
| PL&#x43;**\_**&#x49;N11 | R&#x31;**\_**&#x4F;UT11                                      | Robot is ready                            | PL&#x43;**\_**&#x4F;UT11 | R&#x31;**\_**&#x49;N11                                       | Robot starts                       |
| PL&#x43;**\_**&#x49;N12 | R&#x31;**\_**&#x4F;UT12                                      | Robotpaused                               | PL&#x43;**\_**&#x4F;UT12 | R&#x31;**\_**&#x49;N12                                       | Robotpaused                        |
| PL&#x43;**\_**&#x49;N13 | R&#x31;**\_**&#x4F;UT13                                      | <p>Robot operation<br>status</p>          | PL&#x43;**\_**&#x4F;UT13 | R&#x31;**\_**&#x49;N13                                       | Robot continues                    |
| PL&#x43;**\_**&#x49;N14 | R&#x31;**\_**&#x4F;UT14                                      | Robot alarm status                        | PL&#x43;**\_**&#x4F;UT14 | R&#x31;**\_**&#x49;N14                                       | <p>Robot operation<br>status</p>   |
| PL&#x43;**\_**&#x49;N15 | R&#x31;**\_**&#x4F;UT15                                      | Robot Interaction 1                       | PL&#x43;**\_**&#x4F;UT15 | R&#x31;**\_**&#x49;N15                                       | Robot clear alarm                  |
| PL&#x43;**\_**&#x49;N16 | R&#x31;**\_**&#x4F;UT16                                      | <p>Robot requests to<br>push material</p> | PL&#x43;**\_**&#x4F;UT16 | R&#x31;**\_**&#x49;N16                                       | <p>Robot materials in<br>place</p> |

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on system power switch

Connect the power plug of the robot and MG400 platform to the power supply, and turn on the switch , as shown in Figure4-4.

Figure4-4 Turn on MG400 training system power switch

#### 3.1.2 Power on the robot

Press the power button on the back of MG400 base to **ON** , as shown in Figure4-

5.

![Official MG400 training-system figure, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSxumPL3kBdluPfg38wl1%2Futp-cf6ee49edd6228343ed5.jpg?alt=media)

Figure4-5 Turn on MG400 power switch

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to **Auto** ,

as shown in Figure4-6.

Figure4-6 Turn on the power switch of the pump box

#### 3.1.4 Prepar material

Place twelve circular blocks into the stock bin, as shown in Figure4-7.

![Official MG400 training-system figure, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFBa05LMOyJpM4Ds1lkpk%2Futp-fc5b17c5928659f0a0c2.jpg?alt=media)

![Official MG400 training-system figure, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsaZd3JJgIIeEDh03wNwv%2Futp-2db2f8f61934c760e68e.jpg?alt=media)

Figure4-7 Place material

#### 3.1.5 Install coaxial suction cup

* (1) Prepare material.

Prepare the flange, suction cup and corresponding screws, as shown in Figure4-8.

Figure4-8 Material preparation

* (2) Install the suction cup on the flange through four screws using inner

hexagonal tools, as shown in Figure4-9.

Figure4-9 Install suction cup on the flange

(3) Install the flange on the end of the robot using inner hexagonal tools, as

shown in Figure4-10.

![Official MG400 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUdaM31m8bihY6uM4I6VL%2Futp-f5a4fe881de1cba212d4.jpg?alt=media)

![Official MG400 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXT19l1Dpfr2KKJdRX4RM%2Futp-fa1dce0bffa473a5b7d5.jpg?alt=media)

![Official MG400 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPnCotOaoBPd262DANGvb%2Futp-4560fa847a2a94b1f756.jpg?alt=media)

Figure4-10 Install flange on the end of robot

(4) Connect one end of the air pipe to the suction cup, and the other end to the

robot air pipe interface, as shown in Figure4-11.

Figure4-11 Connect air pipe

#### 3.1.6 Connect network cables

First, connect one end of a network cable to the LAN1 port of the robot and the other end to the upper network port of the PLC module box. Then, connect one end of a network cable to the lower network port of the PLC module box and the other end to the computer, as shown in Figure4-12.

![Official MG400 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdstXv9wCpZ6GrKV2z9RG%2Futp-a84a7c058fb50c650d30.jpg?alt=media)

![Official MG400 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fxj0XhtlfDOMtxgwN1tGV%2Futp-c86dbce2898eaaf23866.jpg?alt=media)

Figure4-12 Connect network cables

#### 3.1.7 Modify IP of the computer

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding window. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure4-13. The default address of the robot is “192.168.1.6”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168. 1.18” as an example.

![Official MG400 training-system figure, source page 71](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fdars1ueDy5UBb6oLX69E%2Futp-eab4ca40e02d48daa920.jpg?alt=media)

Figure4-13 Set IP address of PC

#### 3.2 Download PLC program

* (1) Open **TIA Portal** software, as shown in Figure4-14.

Figure4-14 PLC software initial interface

(2) Select **Open Existing Project**  **Browse** and find the storage location of the PLC program . Select **PLC and HMI program. ap15\_1** and click **open** , as shown in Figure4-15.

![Official MG400 training-system figure, source page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ89x7p1g0OJlCffikCkd%2Futp-758d932b2eaf6708247a.png?alt=media)

![Official MG400 training-system figure, source page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3VX7xuZbcGfaVtqfSVEJ%2Futp-0b59317d4d89686dc765.jpg?alt=media)

Figure4-15 Open program

(3) Click **Project view Open the project view** . Open project view. Double

click on **Devices\&networks** to open the device and network interface . Click (Show address labels) and check if the IP addresses of the PLC, PLC expansion module, and the touch screen are in the 192.168.1. \* network segment , as shown in Figure4-16. Here, for example, the IP of the PLC is set to “192.168.1.10”, the IP of the PLC expansion module is set to “192.168.1.11”, and the IP of the touch screen is set to “192.168.1.12”.

Figure4-16 Set “Devices\&networks” parameters

* (4) Expand **PLC\_1\[CPU 1212C DC/DC/DC]** → **Program blocks** . Then double

click **Main\[OB1]** and view it , as shown in Figure4-17 .

![Official MG400 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMQ4CCYuqsEVeQyLwJsmi%2Futp-f6a1828ebe2693df75f3.jpg?alt=media)

![Official MG400 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMUcfuIG5PdGZdTwLL2hU%2Futp-ecacfb27f9aaa48fd7b9.png?alt=media)

Figure4-17 Open main program

(5) Click **PLC\_1\[CPU 1212C DC/DC/DC]** . Click “

(download to device)”

on the menu bar. In the “Extended download to device” interface, select **Direct at slot '1X1** ' in the “connection to interface/subnet” column. Click **Start search** and select **PLC\_1** from the searched devices. Finally, click **Load** , as show in Figure4-18.

Figure4-18 Set “Extend download to device” parameters

(6) In “Load preview” interface, select **Re initialize** for the “Action” parameter

of “Data block re initialization” , and then click **Load** , as shown in Figure4-19.After the download is completed, the message “Main was loaded successfully.” will appear at the bottom of the software interface, as shown in Figure4-20.

![Official MG400 training-system figure, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnluHBfd7qNQ4ja4Fn9vv%2Futp-3c363b4878c4eed1f0c3.png?alt=media)

![Official MG400 training-system figure, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA02ltjB4iSQB7XaV4joN%2Futp-0ff57f1392d7028b1959.png?alt=media)

Figure4-19 Set “Load preview” parameters<br>

Figure4-20 PLC program download

(7) Click “ ” on the menu bar , then program goes online.The

PLC program in the device bar will display a green icon “ ”or “ ”，as shown in Figure4-21. This indicates that the PLC program has been successfully downloaded and can be debugged and monitored online.

Figure4-21 Online mode

![Official MG400 training-system figure, source page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnqX71s6HqmUZrSW7c23L%2Futp-dfe0dcef93da8a17c251.png?alt=media)

![Official MG400 training-system figure, source page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA9MMenONUsKAs8Dndh17%2Futp-d1fcc4aee05bd3aff30f.jpg?alt=media)

#### 3.3 Download HMI program

(1) Expand “HMI 1 \[KTP700 Basic PN]→Screens” and check if the programs on each sub interface need to be downloaded to the HMI program on the touch screen , as shown in Figure4-22.

Figure4-22 View HMI Programs

(2) Click **HMI 1 \[KTP700 Basic PN]** . Click “ (download to device)” on the

menu bar. In the “Extended download to device” interface, select **Direct at slot '1X1** ' in the “connection to interface/subnet” column. Click **Start search** and select **hmi\_1** from the searched devices . Finally, click **Load** ，as shown in Figure4-23.

Figure4-23 Set “Extend download to device” parameters

![Official MG400 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkR8UoFO9pgo0RdJOtMjd%2Futp-f7c7515ec01b0d4baa9a.png?alt=media)

![Official MG400 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu5PmZbBygju1KMPG9dgN%2Futp-1c9954b9a39eff1074b0.jpg?alt=media)

(3) In “Load preview” interface, check the **Action** parameter of **verwrite** and then click **Load** , as shown in Figure4-24. After the download is completed, the message “File pdata.ORlE.cnk is being loaded” will appear at the bottom of the software interface, as shown in Figure4-25.

Figure4-24 Set “load preview” parameters<br>

Figure4-25 HMI program download

(4) Click “ ”on the menu bar , then program goes online.The

HMI program in the device bar will display a green icon “ ”or “ ”，as shown in Figure4-26. This indicates that the HMI program has been successfully downloaded and can be debugged and monitored online.

![Official MG400 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdirPgnUdJIq1FC4UPgLM%2Futp-b441d36457e6f51d7899.png?alt=media)

![Official MG400 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpkqywufKtDIPEe6S9hLs%2Futp-490a3c126bfa1b3ad437.png?alt=media)

Figure4-26 Online mode

#### 3.4 Debug function of a single button

Observe whether the control buttons on the control box and touch screen are controlled as follows：

* ①Debug the function of the buttons in manual control mode.

Switch the touch screen interface to the “Manual control” interface, as shown in Figure4-27.

Figure4-27 “Manual control” interface

Press **Pusher motor starts** button and the pusher motor pushes out materials； Press **Pusher motor starts** button again and the pusher motor stops pushing materials and returns to the initial position . Press **Conveyor starts** button and the conveyor belt operates . Press **Conveyor starts** again and the conveyor belt stops running .Press the **Green light** button and the green light turns on . Press the **Green light** button again and the green light turns off . Press the **Yellow light** button and the yellow light turns on . Press the **Yellow light** button again and the yellow light turns off . Press the **Red**

![Official MG400 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQUELn6WXyyyWUPsSFK98%2Futp-84087e3c15872381b24f.png?alt=media)

![Official MG400 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7mXn9IvJTwk3b4Ubhp64%2Futp-d112d8f72cd64aabcf31.jpg?alt=media)

**light** button and the red light turns on . Press the **Red light** button again and the red light turns off. Press the **Buzzer** button and the buzzer sounds. Press the **Buzzer** button again and the buzzer does not sound.

②Debug the function of buttons in automatic control mode.

Switch the touch screen interface to the “Automatic control” interface, as shown

in Figure4-28.

Figure4-28 “Automatic control”interface

In “Automatic control” interface, press the **STOP** button and the red light turns

on. Press the **RESET** button and the yellow light turns on. Press the **START** button and the green light turns on.

On the control button box, press the **STOP** button and the red light turns on. Press the **RESET** button and the yellow light turns on. Press the **START** button and the green light turns on.

During the debugging process, it is necessary to modify the PLC and touch screen programs when inconsistencies are observed with the above.

#### 3.5 Debug Robot program

#### 3.5.1 Connect the robot

Double click DobotStudio Pro to open the software. Select **MG400** on the top toolbar, and click **Connect** , as shown in Figure4-29.

![Official MG400 training-system figure, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F512m4MrNLRf5tKNrb1Hl%2Futp-804677fecd7e59beaa27.jpg?alt=media)

Figure4-29 Connect robot

After successful connection, you will see a prompt message, and the connection

status will change to **Connected** , **Online** and **Safe-L1** , as shown in Figure4-30.

Figure4-30 Robot connected

#### 3.5.2 Enable robot

Click on the top toolbar of DobotStudio Pro interface. Set **Payload** to **200g** in “Set load params” dialog box. Set **Offset x** and **Offset y** to **0mm** , as shown in

Figure4-31. Click **OK** and the Enabling icon changes to

Figure4-31 Set load parameters

![Official MG400 training-system figure, source page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvosk5rsBgoFZfF1OImPt%2Futp-1b9f09d8db30e3bfcccb.jpg?alt=media)

![Official MG400 training-system figure, source page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3GRjKBzlYQ2xekjyf7id%2Futp-7e3181a32d934cbc78a4.jpg?alt=media)

#### 3.5.3 Set Global Speed

Click **Global Speed** button on the top toolbar to set it to 30%, as shown in Figure4-32.

Figure4-32 Set Global Speed

#### 3.5.4 Import program

* (1) Open DobotStudio Pro and enter Script page. Click **File** > **Import project** , as

shown in Figure4-33.

Figure4-33 Import project

* (2) Select **Robot Handling** folder, and click **Open** ,as shown in Figure4-34. Now

the program has been imported into DobotStudio Pro.

![Official MG400 training-system figure, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLeqxgeOUkD2g26gwYFrj%2Futp-dacf360c67e0778a3524.png?alt=media)

![Official MG400 training-system figure, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcwHydnYFV0cg9mOcjCBY%2Futp-1f8818feee9a25e84d92.png?alt=media)

Figure4-34 Import program

Note: If the **Robot Handling** file has been saved in the controller before, you can click **File** >

**Open** > **Robot\_Handling** to open it.

#### 3.5.5 Save program

* Click , and enter a project name in the pop-up dialog box, as shown in

Figure4-35.

Figure4-35 Save program

#### 3.5.6 Debug points

The robot handling demo includes three major points, as described below.

* (1) Update safe point P1.

Jog or drag the robot to a position between the conveyor and the storage area, as

shown in Figure4-36.

Figure4-36 Locate P1

![Official MG400 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmUTmJUQ0xCiOhexcqUi6%2Futp-e05f5471be0655ea6682.jpg?alt=media)

![Official MG400 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCQuhac3zvOjANpniq94C%2Futp-286502bf12c06e1d3443.png?alt=media)

![Official MG400 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxR7DADeqbMzeRjbBqLY4%2Futp-914522b14fa305d596cb.png?alt=media)

②Click **Points** in DobotStudio Pro. Select **P1** and click **Cover** , as shown in

Figure4-37. Then click **OK** in the pop-up Tips dialog box.

Figure4-37 Update P1

* (2) Update picking point P2.

①Place the circular workpiece into the silo, and then click the **Pusher motor starts** button in the “Manual control” interface of the touch screen. When the circular workpiece is pushed onto the conveyor belt, click the **Pusher motor starts** button again. Then click the **Conveyor starts** button . When the conveyor belt moves the workpiece to the suction position, click the **Conveyor starts** button again.

②Drag or jog the robot to the circular block, and make the suction cup slightly touch the surface of the block, as shown inFigure 4-38.

Figure 4-38 Locate P2

③Open **I/O** panel. Set **DO\_09** to **ON** to make the robot suck the circular block,

as shown in Figure4-39.

![Official MG400 training-system figure, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fb71M5nOst8zWWbFNJ6X0%2Futp-e1ea69d16237f1d67e0c.png?alt=media)

![Official MG400 training-system figure, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH1fKksnIFNKLuCcrXkmH%2Futp-9d225a6c056dd71088a6.jpg?alt=media)

Figure4-39 I/O panel

④Open **Points** page. Select **P2** and click **Cover** , as shown in Figure4-40. Then

click **OK** in the pop-up Tips dialog box.

Figure4-40 Update P2

* (3) Update placing point P3.
* ①Drag or jog the robot to the first placing point, as shown in Figure4-41. Open

**IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF**

to drop the circular block into the groove accurately.

![Official MG400 training-system figure, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FX16jYwHd76p7Gm8cmUDx%2Futp-581bfb77c78507b91e25.png?alt=media)

![Official MG400 training-system figure, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F72wKtkzu5nUq5guR8c1W%2Futp-6182d81d2c9166f5a4c8.png?alt=media)

Figure4-41 Locate the first placing point

②Open **Points** page. Select **P3** and click **Cover** , as shown in Figure4-42. Then

click **OK** in the pop-up Tips dialog box. Click

and save the program.

Figure4-42 Update P3

#### 3.6 System joint debugging in online operation mode

* (1) Switch the touch screen interface to the **Automatic control** interface.
* (2) In the **Automatic control** interface , first press the **STOP** button, then press

the **RESET** button, and finally press the **START** button . Alternatively, first press the **STOP** button of the control button box, then press the **RESET** button, and finally press the **START** button .

![Official MG400 training-system figure, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FprAik70z8Wx4npK0iuZ8%2Futp-1b1d7f468e67dc927b5b.jpg?alt=media)

![Official MG400 training-system figure, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4DNiPUp0O01XdndLOIl2%2Futp-3ecfb891cac27830476a.png?alt=media)

(3) Operate system.

Open the robot program for the robot handling application project . Click

. Observe whether the program runs as follows:

The robot moves to a safe point, and the pusher motor starts to operate. The pusher motor pushes the workpiece out of the cylindrical silo . When the workpiece reaches the conveyor belt, the pusher motor retracts and stops pushing and the conveyor belt runs. The conveyor belt moves the workpiece forward, and when the workpiece reaches the sensor detection station, the conveyor belt stops running. The robot moves onto the conveyor belt to extract the workpiece and transports it to the corresponding location in the storage area. This cycle continues until all 12

workpieces are transported to the storage area, as shown in Figure4-43.

Figure4-43 Program running result

During operation, if inconsistencies are found, click

, or press the

**STOP** button on the control button box, or the **STOP** button in the **Automatic control** interface. Then modify the robot program, PLC program, and HMI program according to the running status.

#### 3.7 System joint debugging in remote control mode

#### 3.7.1 Set Offline parameters

Click **Menu>Settings>Remote Control** to enter the **Remote Control** settings interface . First set **Current mode** to **Remote I/O** and **Script to run** to **Script .** Then

![Official MG400 training-system figure, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4MIjaO2bBdaSOAVf4K4l%2Futp-f54ea905c4ab9991dbe1.jpg?alt=media)

click **Open** and select **Robot\_Handling** . Click **Modify** . IN **DI configuration** parameters , set **Start** to **DI\_11** , **Pause** to **DI\_12** , **Resume** to **DI\_13, Stop** to **DI\_14** , **Emergency stop** to **Reserve** , and **Clear alarm** to **DI\_15** . IN **DO configuration** parameters, set **Ready status** to **DO\_11** , **Pause status** to **DO\_12** , **Alarm status** to **DO\_14, Running status** to **DO\_13** . Finally click **Apply** . It is shown in Figure4-44. The robot has become a remote operation mode, as shown in Figure4-45.

Figure4-44 Set **Remote Control**

Figure4-45 Remote Control mode

#### 3.7.2 Run program in automatic mode

Switch the touch screen interface to the **Automatic control** interface .

In the **Automatic control** interface of the touch screen, first press the **STOP** button, then press the **RESET** button, and finally press the **START** button. Alternatively, first press the **STOP** button of the control button box, then press the **RESET** button, and finally press the **START** button.

Observe whether the system runs as follows:

![Official MG400 training-system figure, source page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5VqeFvc1A6FBTroTJMYm%2Futp-ab1f8bd7bdc9cb00186e.png?alt=media)

The robot moves to a safe point, and the pusher motor starts to operate. The pusher motor pushes the workpiece out of the cylindrical silo . When the workpiece reaches the conveyor belt, the pusher motor retracts and stops pushing and the conveyor belt runs. The conveyor belt moves the workpiece forward, and when the workpiece reaches the sensor detection station, the conveyor belt stops running. The robot moves onto the conveyor belt to extract the workpiece and transports it to the corresponding location in the storage area. This cycle continues until all 12 workpieces are transported to the storage area.

During operation, if inconsistencies are found, click , or press the **STOP** button on the control button box, or the **STOP** button in the **Automatic control** interface . Then modify the robot program, PLC program, and HMI program according to the running status.

#### 3.8 Export program

Click **File** > **Export project** , and select the path to save the program. Then enter a project name in the pop-up dialog box.

Note: Exporting a project refers to export the program to local for backup.

### 4. Key Program Description

This section mainly describes the key script. For complete script, see the project in Script page.

#### 4.1 PLC program description

#### 4.1.1 System control description

The system control has two modes: manual control and automatic control.

(1) Control requirements in manual control mode.

In the manual control mode of the touch screen, press **Pusher motor starts** button and the pusher motor pushes out materials. Press **Conveyor starts** button and the conveyor belt operates . Press the **Green light** button and the green light turns on .

Press the **Yellow light** button and the yellow light turns on . Press the **Red light** button and the red light turns on .

* (2) Control requirements in automatic control mode.

In the **Automatic control** interface of the touch screen , first press the **STOP** button, then press the **RESET** button, and finally press the **START** button . Alternatively, first press the **STOP** button of the control button box, then press the **RESET** button, and finally press the **START** button .

#### 4.1.2 Main program (OB1)

Main (OB1) program is shown in Figure4-46.

（a）Automatic control

![Official MG400 training-system figure, source page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6ZiCAWVgwotmgJeb0IVy%2Futp-1e97d808783e847ea09d.png?alt=media)

（b）Manual control

（c）Robot control

Figure4-46 Main Program

![Official MG400 training-system figure, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQzM9tsAOrPmTvMXTqIaL%2Futp-cc808bf89ba499141633.png?alt=media)

![Official MG400 training-system figure, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fy9ns3hAB4yb7ah0TwDgA%2Futp-f18a87b847b3d4aadc38.png?alt=media)

#### 4.1.3 Automatic control program(FB1)

Automatic control program is shown in Figure 4-47.

（a）Initialization status

（b）Device initialization

![Official MG400 training-system figure, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiJuNQYP85eACWq46Kmdz%2Futp-a7be549804dddaee35dd.png?alt=media)

![Official MG400 training-system figure, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwvGpHzwBLotZPDDKfpgP%2Futp-961ce38f64417c0161ea.png?alt=media)

（c）The device runs the process<br>

（d）Tricolor lamp<br>

Figure 4-47 Automatic control program

![Official MG400 training-system figure, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1dQ6ECf7fe5RMNqm3kM2%2Futp-d3d3d87f31c7a39d9e22.png?alt=media)

![Official MG400 training-system figure, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdUdz5ohhW9TfzePj1ggI%2Futp-49e80f857900baf78f48.png?alt=media)

#### 4.1.4 Manual control program (FC1)

Manual control program is shown in Figure4-48.

Figure4-48 Manual control program

#### 4.1.5 Robot status control program (FC2)

Robot status control program is shown in Figure4-49.

![Official MG400 training-system figure, source page 94](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNbkEdoSf7gPX0p7rPlbW%2Futp-d44ae09dafa7e5e338fd.png?alt=media)

Figure4-49 Robot status control program

#### 4.1.6 Automatic control data

Automatic control data is shown in Figure4-50.

Figure4-50 Automatic control data

#### 4.2 HMI program description

The touch screen interface needs to include four interfaces: Main interface,

automatic control, manual control and monitoring interface.

![Official MG400 training-system figure, source page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQmalm3KzUsctXiaLHrV0%2Futp-30d53cff3cddb7a1f6ed.png?alt=media)

![Official MG400 training-system figure, source page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYELcmAifBg4yPyJjD0ZZ%2Futp-b777f9932bb3d7da9f4e.png?alt=media)

#### 4.2.1 Main interface

In the Main interface, there are four buttons:“Main interface”, “Automatic control”,“Manual control”,“IO monitoring”,as shown in Figure4-51. You can enter the corresponding interface by pressing the corresponding button.

Figure4-51 Main interface

#### 4.2.2 Automatic control interface

In the Automatic control interface, there are three buttons:“START”, “STOP”, “RESET”, as shown in Figure4-52. When the system is running, press the **STOP** button to stop the system and the red light is on. Press the **RESET** button to reset all IO to the initial state and the yellow light is on. Press the **START** button to start the system and the green light is on.

![Official MG400 training-system figure, source page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7MbQmPQNzbYZPNLBcPSG%2Futp-b6cf1e45f75789c0e04f.jpg?alt=media)

Figure4-52 Automatic control interface

#### 4.2.3 Manual control interface

In the Manual control interface, there are six buttons:“Pusher motor starts”, “Conveyor starts”, “Green light”, “Yellow light”, “Red light”, “Buzzer”, as shown in Figure 4-53.

Figure 4-53 Manual control interface

![Official MG400 training-system figure, source page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaBTNZOl733JF0k6XS2hg%2Futp-7a21a655f376f68b0836.png?alt=media)

![Official MG400 training-system figure, source page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfcgYf0NOIuTDpyvSbnf6%2Futp-0109cbf196d537b2aa0b.png?alt=media)

#### 4.2.4 IO monitoring interface

IO monitoring interface is shown in Figure4-54. Monitor the status of all input and output ports.When the robot malfunctions and sends an alarm, the buzzer will sound.

Figure4-54 IO monitoring interface

#### 4.3 Robot program description

#### 4.3.1 Robot pick-up program

The robot pick-up program is shown in Figure4-55. The function of the program is to start the pusher motor when material is detected in the material slot, and the circular workpiece is pushed onto the conveyor belt. Then the conveyor belt starts. When the conveyor belt drives the workpiece to the material in place detection station, the conveyor belt stops and the robot picks up material on the conveyor belt .

![Official MG400 training-system figure, source page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBwxWamaWbjBXtiICagyG%2Futp-859a97bb6b924b2f8b9d.png?alt=media)

Figure4-55 Pick-up program

Note: The robot pick-up program is in the variable program.

#### 4.3.2 Initialize program

The initialization program is shown in Figure 4-56, with all output ports set to 0.

Figure4-56 Initialize program

**4.3.3Robot placement program**

The robot placement program is shown in Figure4-57, which controls the robot

to move to twelve placing points to place materials.

Figure4-57 Robot placement program

In line 28 and line 29 of the program, the first placing point P3 is the reference

![Official MG400 training-system figure, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6mw1Em3U71xQ2OnsbcVL%2Futp-f0f415fce979dcac1f4c.png?alt=media)

![Official MG400 training-system figure, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbK0VT6Y2WHRObW7ILuzq%2Futp-8b52ef64376a0dab5dd3.png?alt=media)

point for the other placing points. As the placing positions are fixed, the coordinates of the remaining eleven placing points are calculated based on the cycle times and the distance between point P3 and each placing point.

## Chapter 5 Application of Vision Sorting

### 1. Introduction

The specific task of vision sorting is to use the robot to carry six rectangular blocks in three colours on the standard vision board, as shown in Figure5-1, to the grooves of the rectangular/circular board in the storage area and sort them according to colours, as shown in Figure5-2.

Figure5-1 Six rectangular blocks

Red block placement area\
l i\
Green block placement area\
l i\
Blue block placement area<br>

Figure5-2 Storage area

### 2. IO Configuration

The IO configuration of vision sorting is shown in Table5-1 .

**Table5-1 IO configuration**

| **Output** | **Description** |
| ---------- | --------------- |

![Official MG400 training-system figure, source page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FASM6tPWpuGZyNuijmzzN%2Futp-91fa77293f0b0994b188.jpg?alt=media)

![Official MG400 training-system figure, source page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fez7LVJcMjzzoSGCpgG86%2Futp-65736d26aa94419202f1.jpg?alt=media)

DO09 Vacuum pumping DO10 Vacuum breaking

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on system power switch

Connect the power plug of the robot and MG400 platform to the power supply,

and turn on the switch , as shown in Figure5-3.

Figure5-3 Turn on MG400 training system power switch

#### 3.1.2 Power on the robot

Press the power button on the back of MG400 base to **ON** , as shown in Figure5-

4.

Figure5-4 Turn on MG400 power switch

![Official MG400 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUU3up7VSVOKuoeyutdYi%2Futp-514eab78f5dc63fdb9ab.jpg?alt=media)

![Official MG400 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFBa05LMOyJpM4Ds1lkpk%2Futp-fc5b17c5928659f0a0c2.jpg?alt=media)

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to **Auto** , as shown in Figure5-5.

Figure5-5 Turn on the pump box power switch

#### 3.1.3 Turn on light source switch

Turn on the light source switch, as shown in Figure5-6.

Figure5-6 Turn on light source switch

#### 3.1.4 Install standard vision board

Install the standard vision board above the conveyor , as shown in Figure5-7.

Figure5-7 Install standard vision board

![Official MG400 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTn7ujsshAoKvkZsWpeuH%2Futp-21f6d680e6d9971b88ee.jpg?alt=media)

![Official MG400 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxyztmljrLM2Sl16ezldy%2Futp-e9ef85ea461b1403b821.jpg?alt=media)

![Official MG400 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQym0JcGuJxay9OZVtTeq%2Futp-816bc2836f2e9a213cb9.jpg?alt=media)

#### 3.1.5 Install coaxial suction cup

* (1) Material preparation.

Prepare the flange plate, suction cup and corresponding screws, as shown in

Figure5-8.

Figure5-8 Material preparation

* (2) Install the suction cup on the flange plate through four screws using inner

hexagonal tools, as shown in Figure5-9.

Figure5-9 Install suction cup on the flange plate

* (3) Install the flange plate on the end of the robot using inner hexagonal tools, as

shown in Figure5-10.

Figure5-10 Install flange plate on the end of robot

![Official MG400 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F16oVRQvu2hxBZDlKD8ak%2Futp-663f3599432345da7bab.jpg?alt=media)

![Official MG400 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ8GUlngnC3qDqzG7cQuo%2Futp-ff02c97212cfd1e4d63e.jpg?alt=media)

![Official MG400 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaxNRyOOr5s7iZIsSEWdK%2Futp-df54e82a80381ba5b089.jpg?alt=media)

* (4) Connect one end of the air pipe to the suction cup, and the other end to the
* robot air pipe interface, as shown in Figure5-11.

Figure5-11 Connect air pipe

#### 3.2 Connect camera

Plug the dongle of DobotVisionStudio into the computer. Plug the USB cable of

the training system (used to connect the camera) into the computer.

#### 3.3 Connect robot

* (1) Connect the robot to the computer.

Connect the other end of the robot network cable to the PC.

* (2) Modify IP of the computer.

Open the control panel of the computer. Select **Network and Internet/Network**

**and Sharing Center** to enter the corresponding dialog box. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure5-12. The default address of the robot is “192.168.1.6”. You can change the IP address of the PC to any

![Official MG400 training-system figure, source page 105](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjLForwFV27dMRCkuh5Ya%2Futp-bed067fecf1a35218432.jpg?alt=media)

IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168. 1.18” as an example.

Figure5-12 Set IP of PC

* (3) Connect DobotStudio Pro to the robot.

Double click DobotStudio Pro 2.6.1 to open the software. Select **MG400** on the

top toolbar and click **Connect** , as shown in Figure5-13.

Figure5-13 Connect robot

![Official MG400 training-system figure, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ89x7p1g0OJlCffikCkd%2Futp-758d932b2eaf6708247a.png?alt=media)

![Official MG400 training-system figure, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fds7ggr6tQ1qVKr3uPU9V%2Futp-e6abd249ad2a110048d5.png?alt=media)

After successful connection, the connection status on the top toolbar will change

to **Connected** , **Online** and **Safe-L1** , as shown in Figure5-14.

Figure5-14 Connected

#### 3.4 Enable robot

Click on the top toolbar of DobotStudio Pro interface. In “Set load params” dialog box, set **Payload** to **200g** . Set **Offset x** and **Offset y** to **0mm** , as shown in

Figure5-15. Then click **OK** . The Enabling icon changes to

Figure5-15 Set Load params

#### 3.5 Set Global Speed

Click **Global Speed** button on the top toolbar to set it to 30%, as shown in Figure5-16.

Figure5-16 Set Global Speed

![Official MG400 training-system figure, source page 107](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGqA7cwvw9FkHGCJgnpNg%2Futp-aca262b4459937033eb7.jpg?alt=media)

#### 3.6 Debug vision program

#### 3.6.1 Eye-to-hand calibration

* (1) Place the calibration board on the standard visual carrier board , as shown in

Figure5-17.

Figure5-17 Place Calibration board

Note: In order to avoid interference from visual inspection caused by the texture of the visual

carrier board, a piece of paper can be placed on the visual carrier board.

* (2) Remove the suction nozzle from the suction nozzle connecting rod and install
* the calibration needle, as shown in Figure5-18.

Figure5-18 Install the calibration needle

* (3) Open DobotVisionStudio and select **General Solution** .
* (4) Establish the flow. Drag **Image Source** in Acquisition toolbox to the flow
* editing area, as shown in Figure5-19.

![Official MG400 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWi3N6lOCUfOBi6gOFoIE%2Futp-48e462f4369b6a0726b3.jpg?alt=media)

![Official MG400 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9RPmmem8QtiRhHtEFZZd%2Futp-5cf4d6483f9308dde017.jpg?alt=media)

Figure5-19 Flow

① Set **0Image Source1** parameters. Double click **0Image Source1** to set parameters. Select **Image Source** to **Camera** , as shown in Figure5-20. Click **Camera set** on the right side of **Relate Camera** to enter the corresponding page.

Figure5-20 Set **0Image Source1** parameters

②Create global camera. Click **+** on the right side of **Device List** to create **1**

**Global Camera1** and set the parameters of the camera. In the "Common Params" tab, click the triangle in the lower right corner of **Choose Camera** to open the drop-down list and select the camera that is currently connected to the computer. Select **Mono8** for **Pixel Format** , as shown in Figure5-21. Click “Trigger Settings” tab, and set **Trigger Source** to **SOFTWARE** . Then click **Confirm** , as shown in Figure5-22.

![Official MG400 training-system figure, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLvPgBzDlOPnsKFYOkxrk%2Futp-b09976af39162b0eff59.png?alt=media)

![Official MG400 training-system figure, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYh4PiYmIbqGLOjETa40i%2Futp-664e160b702aed1a395e.png?alt=media)

Figure5-21 Common Params

Figure5-22 Trigger Settings

In “0 Image Source” page, click the triangle in the lower right corner of **Relate**

**Camera** and select **1Global Camera1** , as shown in Figure5-23.

![Official MG400 training-system figure, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxQMFOirRac9SBMYflD3G%2Futp-ebbdbf9bfdd9f3baab00.png?alt=media)

![Official MG400 training-system figure, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuJYKQskIO6eHS7bHKRkx%2Futp-0fc8e039b03961c8ffbb.png?alt=media)

Figure5-23 Relate Camera

③Click (Continuously) on the toolbar to adjust the aperture and focus ring

of the lens and the exposure time of the camera until you can see a clear image in the image display area. The image acquisition result is shown in Figure5-24.

Figure5-24 Image acquisition result

(5) Add CalibBoard Calib in the flow.

Drag **CalibBoard Calib** in Calibration toolbox to the flow editing area. Connect

it with **0Image Source1** , as shown in Figure5-25.

![Official MG400 training-system figure, source page 111](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2Q77RvOSUpy4UW8DWElt%2Futp-20b889e5756343fbf909.jpg?alt=media)

![Official MG400 training-system figure, source page 111](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F05SyxvYsSkCNccpWkjOr%2Futp-d6b17ccbf095379e4cc0.png?alt=media)

Figure5-25 Flow

Note: The calibration of the calibration board is used to obtain the calibration point, and

provide the pixel coordinates of the calibration point for N-point calibration.

* (6) Add N-point Calibration in the flow.

①Drag **N-point Calibration** in Calibration toolbox to the flow editing area.

Connect it with **2CalibBoard Calib1** . Click (Once) in the toolbar. Nine calibration points and their calibration sequence are shown automatically in the image display area, as shown in Figure5-26.

(Once) in the toolbar. Nine

Figure5-26 Check nine calibration points and calibration sequence

② Set 3N-point Calibration basic parameters. Double click **3N-point Calibration** to set basic parameters. In “Basic Params” page, set **Translation Number** to **9** by default, as shown in Figure5-27. Click on the right side of **Rotation Number** to edit the calibration points, as shown in Figure5-28.

![Official MG400 training-system figure, source page 112](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQqFNpwcCBnH09cB1GzW0%2Futp-18809d91f93fbf3e9321.jpg?alt=media)

Figure5-27 3N-Point Calibration

Figure5-28 Edit Calibration Points

In “Edit Calibration Points” page, exchange Line 3 (ID: 3) and Line 5 (ID: 5)

data, as shown in Figure5-29.

![Official MG400 training-system figure, source page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhGsw2NbYTEO02Zbdj1W5%2Futp-3b6d6889572269e191a2.png?alt=media)

![Official MG400 training-system figure, source page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtXZZZNHASkf0gg82pSgl%2Futp-b20f2adbc901cb2af5c1.png?alt=media)

Figure5-29 “Edit Calibration Points” after data exchange

Click (Once), and you will see that the calibration sequence in the image

**display area turn to “ ” shape, as shown in Figure5-30.**

Figure5-30 Calibration sequence after data exchange

③Switch to DobotStudio Pro, control the robot to move according to the

sequence of the nine points.

![Official MG400 training-system figure, source page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FooRk9jtskcybnRc4DI1S%2Futp-533c70e47391aac8d53d.jpg?alt=media)

![Official MG400 training-system figure, source page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqsBqwWZali69mtkyM7gp%2Futp-4a7db9f90055df3bb465.png?alt=media)

Move the robot to the first calibration point, and read the physical coordinates X and Y of the first point in DobotStudio Pro, as shown in Figure5-31. Fill the X and Y values in the physical coordinates of the first line in "Edit Calibration Points" page in DobotVisionStudio,as shown in Figure5-32. Obtain the physical coordinates of the remaining 8 points and fill in “Edit Calibration Points” page, as shown in Figure5-33.

Figure5-31 Locate the first calibration point

Figure5-32 Fill in the physical coordinates of the first calibration points

![Official MG400 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbzAi2E8A02Ep5lcCSK8O%2Futp-37e6e75d8bdc33e79154.jpg?alt=media)

![Official MG400 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn71AqNoLiEINVkcmv5Us%2Futp-0921ccfae729e25722f5.jpg?alt=media)

![Official MG400 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFBqCQLzyMy7coFKmATKD%2Futp-f5015bf4b809661a408e.png?alt=media)

Figure5-33 Physical coordinates of 9 calibration points

④Generate the calibration file. After editing the calibration points, click in

“Basic Params” page. Click **Create Calibration File** to export the calibration file to local, and name it as “Calibration file” for being called later, as shown in Figure5-34.

Figure5-34 Generate calibration file

(7) Add Calibration Transformation in the flow. After calibration, you can add

this tool to verify whether the calibration is accurate.

①Drag **Calibration Transformation** in Calculation toolbox to the flow editing area, and connect it with **3N-point Calibration1** , as shown in Figure5-35.

![Official MG400 training-system figure, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhBxZS7kABpfRxaS8aMNA%2Futp-8b9ef1eb473c4b8b378b.png?alt=media)

![Official MG400 training-system figure, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVwEwlIrOqkXnDMNVpjPm%2Futp-8dfc5b1683f69d913a5b.png?alt=media)

Figure5-35 Flow

②Set 4Calibration Transformation parameters. In “Basic Params” page, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** . Set **Load Calibration File** to **Calibration file** generated from 3N-point Calibration1, as shown in Figure536.

Figure5-36 Set 4Calibration Transformation parameters

③Click (Once), and check whether the nine coordinates after 4Calibration Transformation1 are consistent with the physical coordinates in 3N-point Calibration1, as shown in Figure5-37. If consistent, the calibration is accurate. Otherwise, you need

![Official MG400 training-system figure, source page 117](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnYRiVeX96GJLzlRiUhtj%2Futp-9c13af414e9b584b0f5f.png?alt=media)

to re-calibrate.

Figure5-37 Comparison result

After the calibration is completed, it is necessary to remove the calibration needle from the suction nozzle connecting rod and replace it with a suction nozzle.

#### 3.6.2 Import vision program

Open DobotVisionStudio 4.1.2 and select **General Solution** . Select **Open** in the toolbar. Find the vision sorting program and click **Open** . The imported vision program is shown in Figure5-38.

Figure5-38 Vision program

#### 3.6.3 Place detection object

Place six blocks within the detection view, as shown in Figure5-39.

![Official MG400 training-system figure, source page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxLvseMezvrChmr8MW2Ix%2Futp-ed7421dd1da38ccd7b2f.png?alt=media)

![Official MG400 training-system figure, source page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZIJwWKlNB4rx9v95LH7M%2Futp-e1a803b4eb9d8a6d5f92.png?alt=media)

![Official MG400 training-system figure, source page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhY0PcsrLYGAnWIBGpm3r%2Futp-ebba1806e0cfa5c3702e.png?alt=media)

Figure5-39 Place six blocks within the detection view

#### 3.6.4 Debug program parameters

(1) Debug **0Image Source** parameters.

Click (Once). Select **0Image Source1** and observe whether the image is

clear. If the image is not clear or there is no image, you need to reset the parameters according to the method described in 3.6.1. When setting the parameters, set **Pixel Format** to **RGB8** . The image collected by the camera is shown in Figure5-40.

Figure5-40 Collected image

* (2) Debug **2Color Transformation1** parameters.

![Official MG400 training-system figure, source page 119](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyBVzguEdJwUVTunaNvtb%2Futp-0882d2f31e805e83b653.jpg?alt=media)

![Official MG400 training-system figure, source page 119](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FV0XVRXHAS4cdg62Yerj7%2Futp-6e216cb92ab9fd884eae.jpg?alt=media)

Double click **2Color Transformation1** to check whether **Transfer Type** is **RGB to Grayscale** , as shown in Figure5-41. If not, modify as the figure.

Figure5-41 2Color Transformation

Click (Once). The execution result of 2Color Transformation1 is shown in

Figure5-42.

Figure5-42 Grayscale Image

![Official MG400 training-system figure, source page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFcHAem2U4d4EtMoM5QBi%2Futp-de00b82901d86f1a41d0.png?alt=media)

![Official MG400 training-system figure, source page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9rXrUvfN61BModxo6OUu%2Futp-4b479f3fcd113498ceeb.jpg?alt=media)

* (3) Debug **3Fast Match1** parameters.

Double click **3Fast Match1** . Click **Run Params** and modify **Max Number to find** to **6** . Then click **Execute** and observe whether all the blocks are recognized in the image display area, as shown in Figure5-43.

Figure5-43 Run Params

If all the blocks are recognized, use the original model. Otherwise, you need to

re-create the feature model, as described below.

①Enter “Feature Model” page. Delete the original model and then click **Create** ,

as shown in Figure5-44.

Figure5-44 Feature Model

②In ModelSettings page, click **Current Image** . Click (Create Rect Mask),

select the corresponding area in the image and set corresponding model parameters

![Official MG400 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F46J7jDhAOeibwsoF4HXq%2Futp-2b71709252c4aa561e89.png?alt=media)

![Official MG400 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNCiNRB1RLHzLUYyz5xx5%2Futp-865e09bd14875ff8dcdf.jpg?alt=media)

![Official MG400 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaLoHApFRDJE9XUz8k2Ru%2Futp-01239a8ec4c729aa0ea9.png?alt=media)

(Build Model) and click **Confirm** , as shown in

(generally default). Then click

Figure5-45.

Figure5-45 ModelSettings

* ③After creating the model, click **Execute** and **Confirm** , as shown in Figure5-46.

Figure5-46 Result

Note: If not all the blocks can be recognized, maybe it is caused by the light. You can change

the threshold value.

④Double click **3Fast Match1** . Click **Run Params** and modify **Max Number to**

**find** to **1** . Then click **Execute** , and the recognized block is shown in the image display

![Official MG400 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fkz8gsImEF9kXn6ZRwKg3%2Futp-d9501a3838500658e044.jpg?alt=media)

![Official MG400 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2rpljps63pCj1yn7Bb9n%2Futp-eddbb1dbc4522c97a2a3.jpg?alt=media)

area. Click **Confirm** , as shown in Figure5-47.

Figure5-47 Result

* (4) Debug 4Calibration Transformation1 parameters.

Double click **4Calibration Transformation1** . Check whether **Coord Point** is

**Fast Match.Match Point** . Load the saved calibration file, as shown in Figure5-48.

Figure5-48 Basic Params

Click **Execute** and **Confirm** , and the physical coordinates of the blocks are

displayed in the result display area, as shown in Figure5-49.

![Official MG400 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrT4Hptm4UWGswEg2vzZK%2Futp-52cf6f7e6590727ef760.jpg?alt=media)

![Official MG400 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2S4HPjLK4vaN7AWnscQQ%2Futp-e44ae64c1132e76e12b5.png?alt=media)

![Official MG400 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS5mysJvHyuHlvgimttS0%2Futp-edb45fa0a40f384622bc.png?alt=media)

Figure5-49 Result

(5) Debug **5Color Recognition1** parameters.

Click (Once). Select **5Color Recognition1** and modify the image display to **ImageSource1.OutputImage** . Observe whether the colour of the image is recognized correctly, as shown in Figure5-50.

Figure5-50 Result

If the colours are recognized incorrectly, you need to debug according to the

![Official MG400 training-system figure, source page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsahLbVRG8FOJ4N5eB3v1%2Futp-d20bf38adddedf9f157b.jpg?alt=media)

![Official MG400 training-system figure, source page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZQXydtOKFc8v2DANiGx5%2Futp-94cab26e6488d820a1b6.jpg?alt=media)

following method.

* ①Double click **5Color Recognition1** . Check whether **Input Source** and **ROI**
* **Area** in “Basic Params” page are set as Figure5-51.

Figure5-51 Basic Params

②In “Color Model” page, delete the existing model. Click **+** to re-create models,

as shown in Figure5-52.

![Official MG400 training-system figure, source page 125](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbszTbkmkMlD88ckEcixf%2Futp-27eebcb52c30f71e5cd8.png?alt=media)

Figure5-52 Color Model

③Create a red model. In **ModelSettings** page, click (add the current image), then click **+** on the right side of **Label List** to add a new label and change the label name. Click in the toolbar and drag a rectangular mask on the current image. Then click **Add To Label** and you will see the added red model on the right side, as shown in Figure5-53.

![Official MG400 training-system figure, source page 126](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFxMlRUPV0PDsk7mBSZAq%2Futp-f462ebd2851687b0c65f.png?alt=media)

Figure5-53 Create red model

Note: The material may be reflective due to the light which could result in a difference in

colour. In this case, you need to create several red models.

* ④Create the green and blue models using the same method , as shown in

Figure5-54. Click **Confirm** to return to “Color Model” page.

![Official MG400 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvPz0xkrlVF0QbExJSLvb%2Futp-24a0474c7399114a8639.jpg?alt=media)

![Official MG400 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmpTwum3n3VjvwsJY8Z6j%2Futp-45ae6acfc67f0ea39f8b.jpg?alt=media)

Figure5-54 Create green and blue models

* ⑤Click **Execute** and **Confirm.** The recognized colour of the block is shown in
* the result display area, as shown in Figure5-55.

Figure5-55 Result

(6) Debug **6Variable Calculation1** parameters.

Click (Once). Select **6Variable Calculation1** and check whether **var0** which

in the display area and the **MatchBoxAngle** value of **3Fast Match** are opposite values, as shown in Figure5-56.

Figure5-56 Comparison result

If the values are not opposite, you need to debug according to the following method.

①Double click **6Variable Calculation1** . Click below **Expression** to enter

![Official MG400 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeouYT2EW2JOXEYaULHdW%2Futp-90eab73b744470ebdad3.jpg?alt=media)

![Official MG400 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlzneMIQsMhvDHO72PWk7%2Futp-462713edb968540fb88b.jpg?alt=media)

**Var0** page. Click  **3Fast Match1**  **MatchRect**  **MatchBoxAngle** to select the variable, and then plus “-” in front of the variable, that is, to get the negative value of the angle. Then click **Save** to return to the “Basic Params” page, as shown in Figure557.

Figure5-57 Expression

②Click **Execute** and **Confirm** and you will see the angle value, as shown in

Figure5-58.

![Official MG400 training-system figure, source page 129](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUBKpdvvdAlvZbqlJiNH5%2Futp-3ae115c459d6f3b57be2.png?alt=media)

Figure5-58 Result

(7) Debug **7Format1** parameters

Click (Once). Select **7Format1** and observe whether the result display area shows the format result as Figure5-59.

Figure5-59 Result

![Official MG400 training-system figure, source page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJpRdGKNHFE3eSIW3xS48%2Futp-78651aa82b931bfec183.jpg?alt=media)

![Official MG400 training-system figure, source page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRo9kRp9kgQw09hoAYb2x%2Futp-3cb942b7c14a8d2f0d5f.jpg?alt=media)

If not, you need to debug according to the following method.

①Double click **7Format1** . In “Basic Params” page, as shown in Figure5-60, click **+** to add a row. Click (InsertSubscription) and select **5Color Recognition1**  **Best Matched Name** .

Figure5-60 Basic Params

② Then click **T** and enter “,”. Click and select **4 Calibration Transformation1**  **OutputPoint**  **TransPointX** . Insert “<4 Calibration Transformation1.TransPointY(%1.3f)>\[0]” “,”. “<6 Variable Calculation1.var0(%1.3f)>\[0]” following the same method. The format parameters are shown in Figure5-61.

![Official MG400 training-system figure, source page 131](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd335unODVoMoSJCtiew5%2Futp-4deb6e034fb6c1ff265c.png?alt=media)

Figure5-61 Format Params

* (8) Communication management settings

Click in the quick toolbar to enter “Communication Management” page. Check whether there is established TCP Server and whether its parameters are consistent with the figure below. If not consistent, modify as Figure5-62.

Figure5-62 Communication Management

If there is no **TCP Server** , you need to create one, as described below.

Click beside **Device Lists** to add devices. Select **Protocol Type** to **TCP Server,** and modify **Device Name** (TCP Server by default), **Local IP** and **Local Port** according to the actual condition, and click **Create** , as shown in Figure5-63. After creating the communication device, switch on **1TCP Server** , as shown in Figure5-64

![Official MG400 training-system figure, source page 132](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXYGlL7Dim0fFsd3PqHwG%2Futp-ea765ee532fbeb2c530f.png?alt=media)

![Official MG400 training-system figure, source page 132](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNDYMCbt58jQQVV3jvKrH%2Futp-4beec9d36d12b65766e0.png?alt=media)

Figure5-63 Add device

![Official MG400 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F87jCOtAy8FsexH6DRrLP%2Futp-47d1f03fb586649374c1.png?alt=media)

![Official MG400 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp8KTygww63YpIFvcljmv%2Futp-c1843e2d85236398a525.png?alt=media)

Figure5-64 TCP Server

* (9) Debug **8Send Data1** parameters.

Double click **8Send Data1** and check whether the parameters are shown as Figure5-65. If not, modify as the figure. Set **Output To** to **Communication Device** , **Communication Device** to **1 TCP Server** , and **Send Data1** to **7Format 1.for mat\_o ut\[]** . Then click **Confirm** .

![Official MG400 training-system figure, source page 134](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F87jCOtAy8FsexH6DRrLP%2Futp-47d1f03fb586649374c1.png?alt=media)

Figure5-65 Send Data

* (10) Global trigger settings

Click in the quick toolbar to enter “Global Trigger” page. In “String Trigger” page, check whether the string trigger setting is shown in Figure5-66 (String

is void; Mode is Mismatched; Trigger Configuration is All Process).

Figure5-66 Set Global Trigger parameters

#### 3.6.5 Save program

Click in the toolbar to save the program. If you need to save the program

![Official MG400 training-system figure, source page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx1IPS5UFrpEHtPojPwdN%2Futp-0e9b3058365b64bd00ef.jpg?alt=media)

![Official MG400 training-system figure, source page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhR1OAIWUwjShffP6VhZW%2Futp-0a86b65db70ed8fe13f7.png?alt=media)

elsewhere on your local computer, click **File** > **Save as** , select the saving path and

enter the name of the project.

#### 3.7 Debug robot program

#### 3.7.1 Import program

* (1) Open DobotStudio Pro and enter Script page. Click **File** > **Import project** , as

shown in Figure5-67.

Figure5-67 Import robot program

Select “Vision Sorting” folder and click **Open** to import the vision sorting

program into DobotStudio Pro.

#### 3.7.2 Save program

Click and enter a project name in the pop-up dialog box, as shown in

Figure5-68.

![Official MG400 training-system figure, source page 136](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYlWEFMF7OSyH48m70Es6%2Futp-bd601ade03ff28bd5d08.png?alt=media)

Figure5-68 Save program

Note: Saving a program refers to saving the program to the robot controller. If you want to

save the modified program to local, you need to export the project.

#### 3.7.3 Set communication

Ensure that the IP address and port of TCP server in the robot program are consistent with those in vision communication settings, that is, set IP address in the robot program to 192.168.1.18. Set port to 4001, as shown in Figure5-69.

Figure5-69 Set communication

#### 3.7.4 Program debugging

(1) Modify Z coordinate of the picking point.

Place two red square materials on the loading plate.

Drag or jog the robot make the suction cup slightly touch the surface of the red block, as shown in Figure5-70. Then read the current Z coordinate of the robot, as shown in Figure5-71. Modify the Z coordinate in the command “local GetProductPos

\= {coordinate = {move\_x,move\_y,-17.23,move\_r}, tool =0, user = 0}” of the pickup sub-program to the current Z coordinate.

![Official MG400 training-system figure, source page 137](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2Hwsq02CWyHgMRW9ngNP%2Futp-0d06c19c8898c5924c5d.png?alt=media)

Figure5-70 Picking point

Figure5-71 Z coordinate of picking point

(2) Modify Z coordinate over the picking point.

Jog the robot to lift some distance, as shown in Figure5-72. Then read the Z

![Official MG400 training-system figure, source page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhkkkzgR9nu8zBwejN0yI%2Futp-dfcba3ac676b6197b0ac.jpg?alt=media)

![Official MG400 training-system figure, source page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5MeXw0TYHdGV6EXga0O2%2Futp-f703c64808c8ca4dcd86.jpg?alt=media)

coordinate of the robot, as shown in Figure5-73. Modify the Z coordinate in the command “local GetProductPosUp = {coordinate = {move\_x,move\_y,1.77,move\_r}, tool =0, user = 0}” of the pickup sub-program to the current Z coordinate.

Figure5-72 Over picking point

![Official MG400 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCqYAUKLdPTLDYZ7x2mGQ%2Futp-8e1f6fe5b89a43d44c5f.jpg?alt=media)

![Official MG400 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTDV6HoQL2krGsuNJEm2L%2Futp-bbfcfbdcb209a57b6b6c.jpg?alt=media)

Figure5-73 Z coordinate over picking point

#### 3.7.5 Debug points

The vision sorting demo includes seven major points, as described below.

* (1) Update the safe point P1.

Jog or drag the robot to a position between the conveyor belt and the storage area, as shown in Figure5-74. Click **Points** in the right-side menu of DobotStudio Pro. Select **P1** and click **Cover** , as shown inFigure5-75. Then click **OK** in the pop-up Tips dialog box. Click "Save" to save the program.

Figure5-74 Locate Point P1

![Official MG400 training-system figure, source page 140](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fecz5jgk07hJOEZm6wklv%2Futp-226932f23a3b863f5867.jpg?alt=media)

![Official MG400 training-system figure, source page 140](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm0cndZiib5DnPyKsuAwl%2Futp-7b5079450286b5bf7bf6.png?alt=media)

Figure5-75 Update Point P1

Note: Every time a point is updated, you need to click "Save" to save the program once.

* (2) Update the first red block placing point P2.

①Click to make the robot suck the red block according to the

coordinates sent by the vision system. Then click

immediately. Jog the

robot to the first red block placing point in the storage area, as shown in Figure5-76.

Figure5-76 Locate the first red block placing point P2

②Open **Points** page. Select **P2** and click **Cover** , as shown in Figure5-77. Then

click **OK** in the pop-up Tips dialog box. Click "Save" to save the program.

![Official MG400 training-system figure, source page 141](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqER1i0Vnjj6XeZkntnMR%2Futp-5184197a62d239bdd34f.jpg?alt=media)

Figure5-77 Update P2

③Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set **DO\_10** to **OFF** and observe whether the block is placed into the groove accurately. If not, you need to re-debug the point.

* (3) Update the second red block placing point P3.

①Click to make the robot suck the second red block according to

the coordinates sent by the vision system. Then click immediately. Jog

the robot to the second red block placing point in the storage area, as shown in Figure5-78.

![Official MG400 training-system figure, source page 142](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiTWohAnqi9jaSkQFXSF1%2Futp-2b8dd00c412303ad1b6e.png?alt=media)

![Official MG400 training-system figure, source page 142](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fi1kAaRtpJgujXJ1eTWXt%2Futp-2471e72dbcbca5c3cbbe.jpg?alt=media)

Figure5-78 Locate the second red block placing point P3

②Open **Points** page. Select **P3** and click **Cover** , as shown in Figure5-79. Then

click **OK** in the pop-up Tips dialog box. Click "Save" to save the program.

Figure5-79 Update P3

③Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set **DO\_10** to **OFF** and observe whether the block is placed into the groove accurately. If not, you need to re-debug the point.

* (4) Update the first green block placing point P4.

①Click to make the robot suck the green block according to the

coordinates sent by the vision system. Then click immediately. Jog the robot to the first green block placing point in the storage area, as shown in Figure5-80.

![Official MG400 training-system figure, source page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbxrAG4uInwNJRL7w9gH9%2Futp-e875f61673f4d071510c.png?alt=media)

Figure5-80 Locate the first green block placing point P4

②Open **Points** page. Select **P4** and click **Cover** , as shown in Figure5-81. Then

click **OK** in the pop-up Tips dialog box. Click "Save" to save the program.

Figure5-81 Update P4

③Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set

**DO\_10** to **OFF** and observe whether the block is placed into the groove accurately. If not, you need to re-debug the point.

* (5) Update the second green block placing point P5.
* ①Click to make the robot suck the second green block according

![Official MG400 training-system figure, source page 144](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdV9OXKjwPcbktc2NcMwF%2Futp-403a683e27793a164f51.jpg?alt=media)

![Official MG400 training-system figure, source page 144](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfYq2Z4rl8PzFtiIhFOz6%2Futp-ed9419db8ab877a641eb.png?alt=media)

to the coordinates sent by the vision system. Then click immediately. Jog the robot to the second green block placing point in the storage area, as shown in Figure5-82.

immediately. Jog

Figure5-82 Locate the second green block placing point P5

②Open **Points** page. Select **P5** and click **Cover** , as shown in Figure5-83. Then

click **OK** in the pop-up Tips dialog box. Click "Save" to save the program.

Figure5-83 Update P5

③Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set **DO\_10** to **OFF** and observe whether the block is placed into the groove accurately. If

![Official MG400 training-system figure, source page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Faq5yhCxcBcGxMJlBbeoY%2Futp-d31be4cdfd92042ea234.jpg?alt=media)

![Official MG400 training-system figure, source page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSvjo2W5QcyRgj5YPgeby%2Futp-6a5b9a38da48cfcfb41d.png?alt=media)

not, you need to re-debug the point.

* (6) Update the first blue block placing point P6.

①Click to make the robot suck the blue block according to the

coordinates sent by the vision system. Then click

immediately. Jog the

robot to the first blue block placing point in the storage area, as shown in Figure5-84.

Figure5-84 Locate the first blue block placing point P6

②Open **Points** page. Select **P6** and click **Cover** , as shown in Figure5-85. Then

click **OK** in the pop-up Tips dialog box. Click "Save" to save the program.

Figure5-85 Update P6

![Official MG400 training-system figure, source page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQEdNLXxWMPJmgzPY8TlO%2Futp-391aeb289a29c36caa4e.jpg?alt=media)

![Official MG400 training-system figure, source page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRbtuXX4RSs1QApiuEsdH%2Futp-ae123731d3c7e3be7b03.png?alt=media)

③Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set **DO\_10** to **OFF** and observe whether the block is placed into the groove accurately. If not, you need to re-debug the point.

* (7) Update the second green block placing point P7.

①Click to make the robot suck the second blue block according to

the coordinates sent by the vision system. Then click

immediately. Jog

the robot to the second blue block placing point in the storage area, as shown in Figure5-86.

Figure5-86 Locate the second blue block placing point P7

②Open **Points** page. Select **P7** and click **Cover** , as shown in Figure5-87. Then click **OK** in the pop-up Tips dialog box. Click "Save" to save the program.

![Official MG400 training-system figure, source page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUoMui39Mdi0kbRkHejAn%2Futp-9ef8e8a5ba4f5a986e7b.jpg?alt=media)

Figure5-87 Update P7

③Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set **DO\_10** to **OFF** and observe whether the block is placed into the groove accurately. If not, you need to re-debug the point.

Note: When updating the remaining points, only the corresponding colored blocks will be placed.

#### 3.7.6 Run program

Click , and check whether the program is running as follows:

The vision system detects the data of blocks, and transmits the colour and position data of blocks to the robot. After obtaining the information, the robot moves to the detection area to suck the blocks, sorts and places them in the corresponding colour area. The sorting effect is shown in Figure5-88.

![Official MG400 training-system figure, source page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoMH8VKQYUBPQU6MWaRae%2Futp-54b969570164bed21429.jpg?alt=media)

Figure5-88 Sorting finished

#### 3.7.7 Export program

Click **File** > **Export project** and select the path to save the program. Then enter

a project name in the pop-up dialog box.

Note: Exporting a project refers to export the program to local for backup.

### 4. Key Program Description

#### 4.1 Vision program description

This section only describes the main functions of each tool in the program. For specific parameter settings of the tools, please see the vision project file.

The vision program is shown in Figure5-89. **0Image Source1** is mainly used for image acquisition. During the system operation, the camera takes photos immediately after the vision software receives the trigger signal sent by the robot. The images acquired are all coloured images because colour recognition is to be performed. **2Color Transformation1** is mainly used for converting colour images into grayscale images to locate grayscale images. **3Fast Match1** is mainly used for locating grayscale images, and **3Fast Match1** is used to obtain the image coordinates and matching angle of the detected object. **4Calibration Transformation1** is used for transforming the image coordinates obtained by **3Fast Match1** into actual physical coordinates. **5Color Recognition1** is used for creating a colour model to recognize

![Official MG400 training-system figure, source page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fwrbqv1oug2RCapNUCU8r%2Futp-297485ab33cc008f2dfd.jpg?alt=media)

the colour of blocks so that sorting can be performed by colour. **6Variable Calculation1** is used for correcting the matching angle. **7Format1** is used for summarizing and defining the format of the information that the vision system needs to send to the robot. **8Send Data1** is used for sending the contents of **7Format1** to the robot.

Figure5-89 Vision program

#### 4.2 Robot program description

This section mainly describes the key script. For complete script, see the project in Script page.

#### 4.2.1 Output port reset program

The output port reset program is shown in Figure5-90, which sets all output ports to **OFF** .

Figure5-90 Output port reset program

#### 4.2.2 Data transmission program

The data transmission program is shown in Figure5-91 which mainly sends

photography trigger signal “OK” and receives the data sent by the vision system.

Figure5-91 Data transmission program

#### 4.2.3 Robot pick-up program

The robot pick-up program is shown in Figure5-92. The function of the program

is that the robot parses the information sent by the vision system and moves to the

calculated picking point for picking up blocks.

Figure5-92 Robot pick-up program

#### 4.2.4 Creat TCP communication program

Create a TCP client program as shown in Figure5-93.

![Official MG400 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHWNELXuD7vuJ7YgXWnro%2Futp-c24841067b4ba260f60a.png?alt=media)

![Official MG400 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F13TfxEOEoTNXqyPpZfpI%2Futp-121f3222d250a9520251.png?alt=media)

Figure5-93 Create a TCP client program

#### 4.2.5 Robot placement program

* (1) Place the red blocks .

If the robot picks up the red block, it moves to the placing point (P2 or P3) via

the safe point (P1) to place the block. Then it returns to P1, as shown in Figure5-94.

Figure5-94 Place the red blocks

* (2) Place the green blocks.

If the robot picks up the green block, it moves to the placing point (P4 or P5) via

the safe point (P1) to place the block. Then it returns to P1, as shown in Figure5-95.

![Official MG400 training-system figure, source page 152](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkpLnAXD7itV4WiwyyDel%2Futp-09ddb1b0d8118b3efa81.png?alt=media)

Figure5-95 Place the green blocks

* (3) Place the blue blocks.

If the robot picks up the blue block, it moves to the placing point (P6 or P7) via

the safe point (P1) to place the block. Then it returns to P1, as shown in Figure5-96.

Figure5-96 Place the blue blocks

![Official MG400 training-system figure, source page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fauq1uANCVeQ4s2UBowns%2Futp-a6bdfddeb1c0cf5654a0.png?alt=media)

![Official MG400 training-system figure, source page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXOBbr9FJdjXOoF3IvilY%2Futp-591a73d405ba496d3c3f.png?alt=media)

## Chapter 6 Application of Phone Chip Assembly

### 1. Introduction

The specific task of phone chip assembly is to use the robot to assemble six chips placed on the standard vision board (Figure6-1) to the six grooves of the mobile phone model, as shown in Figure6-2.

Figure6-1 Phone chip

Figure6-2 Phone model

### 2. IO Configuration

The IO configuration of the phone chip assembly demo is shown in Table6-1.

**Table6-1 IO configuration**

| **Output** | **Descr** | **iption** |
| ---------- | --------- | ---------- |
| DO09       | Vacuum    | pumping    |
| DO10       | Vacuum    | breaking   |

### 3. Program Debugging

#### 3.1 Preparation

![Official MG400 training-system figure, source page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fpzsym6bVVaKXx9duVNux%2Futp-bf870dec075698ad08eb.jpg?alt=media)

![Official MG400 training-system figure, source page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkdcIVfl1rxWOPrzctwee%2Futp-3d3f9f604667512ee5f7.jpg?alt=media)

#### 3.1.1 Turn on system power switch

Connect the power plug of the robot and MG400 platform to the power supply, and turn on the switch , as shown in Figure6-3.

Figure6-3 Turn on MG400 training system power switch

#### 3.1.2 Power on the robot

Press the power button on the back of MG400 base to **ON** , as shown in Figure6-

4.

Figure6-4 Turn on MG400 power switch

#### 3.1.3 Turn on pump box power switch

Turn on the power switch of the pump box and turn the control button to **Auto** , as shown in Figure6-5.

![Official MG400 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqkBo6s4fOz5RT4pQ957j%2Futp-d10b4903bcb517e8a477.jpg?alt=media)

![Official MG400 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMUVx4E7obmLuGPqeRzNO%2Futp-e83ac29242606e204d4d.jpg?alt=media)

Figure6-5 Turn on Pump box power switch

#### 3.1.4 Turn on light source switch

Turn on the light source switch, as shown in Figure6-6.

Figure6-6 Turn on light source switch

#### 3.1.5 Install standard vision board

Install the standard vision board above the conveyor belt, as shown in Figure6-7.

Figure6-7 Install standard vision board

#### 3.1.6 Install phone model board

Install the phone model board into the storage area, as shown in Figure6-8.

![Official MG400 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMLuY8PZsXOomSjlxgjPw%2Futp-ea03dd125a359b391db0.jpg?alt=media)

![Official MG400 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxyztmljrLM2Sl16ezldy%2Futp-e9ef85ea461b1403b821.jpg?alt=media)

![Official MG400 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh0pkpwzeiyUf10qjzLNR%2Futp-3b7e09f30b15d5038a51.jpg?alt=media)

![Official MG400 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlSKidT5MeAwBcbDTSJbw%2Futp-6f187603e5626fcf8976.jpg?alt=media)

Figure6-8 Install phone model board

#### 3.1.7 Install coaxial suction cup

* (1) Prepare the material.

Prepare the flange, suction cup and corresponding screws, as shown in Figure6-9.

Figure6-9 Prepare material

* (2) Install the suction cup on the flange through four screws using inner

hexagonal tools, as shown in Figure6-10.

Figure6-10 Install suction cup on the flange

* (3) Install the flange on the end of the robot using inner hexagonal tools, as

shown in Figure6-11.

Figure6-11 Install flange on the end of robot

(4) Connect one end of the air pipe to the suction cup and the other end to the

![Official MG400 training-system figure, source page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbRsVx2nlgTVbpq8biCux%2Futp-d66958706c25f2425cd0.jpg?alt=media)

![Official MG400 training-system figure, source page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBGs7IuI20q7Jb27xewwl%2Futp-b0c11696ef306de9caae.jpg?alt=media)

![Official MG400 training-system figure, source page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK6bZvAWWoWTwpTSccXQJ%2Futp-84da15b3e5894eb76d63.jpg?alt=media)

robot air pipe interface, as shown in Figure6-12.

Figure6-12 Connect air pipe

#### 3.2 Connect camera

Plug the dongle of DobotVisionStudio into the computer. Plug the USB cable of the training system (used to connect the camera) into the computer.

#### 3.3 Connect robot

* (1) Connect the robot to the computer.

Connect the other end of the robot network cable to the PC.

* (2) Modify IP of the computer.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Center** to enter the corresponding dialog box. Click **Ethernet** and select **Properties** to enter the Ethernet Properties page. Double click **Internet Protocol Version 4 (TCP/IPv4)** . Reset the IP address, as shown in Figure6-13. The default address of the robot is “192.168.1.6”. You can change the IP address of the PC to any IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are consistent with those of the robot. Here takes “192.168. 1.18” as an example.

![Official MG400 training-system figure, source page 158](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZi9138Rhz5MtXd3jgOCa%2Futp-14a708d133fc708ce953.jpg?alt=media)

Figure6-13 IP setting of PC

* (3) Connect DobotStudio Pro to the robot.

Double click DobotStudio Pro 2.6.1 to open the software. Select **MG400** on the

top toolbar, and click **Connect** , as shown in Figure6-14.

Figure6-14 Connect robot

After successful connection, the connection status on the top toolbar will change

to **Connected** , **Online** and **Safe-L1** , as shown in Figure6-15.

Figure6-15 Robot connected

![Official MG400 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ89x7p1g0OJlCffikCkd%2Futp-758d932b2eaf6708247a.png?alt=media)

![Official MG400 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvwreaHWHw13NvygKW42W%2Futp-1e3505e4739bad1742d4.png?alt=media)

#### 3.4 Enable robot

Click on the top toolbar of DobotStudio Pro interface. Set **Payload** to **200g** in “Set load params” dialog box. Set **Offset x** and **Offset y** to **0mm** , as shown in

Figure6-16. Then click **OK** . The Enabling icon changes to

Figure6-16 Set load parameters

#### 3.5 Set Global Speed

Click **Global Speed** button on the top toolbar to set it to 30%, as shown in

Figure6-17.

Figure6-17 Set Global speed

#### 3.6 Debug vision program

#### 3.6.1 Eye-to-hand calibration

(1) Remove the suction nozzle from the suction nozzle connecting rod and install

the calibration needle , as shown in Figure6-18.

![Official MG400 training-system figure, source page 160](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdYMAqDQcFO0Hycq9YSNv%2Futp-9036f320642772b55a34.jpg?alt=media)

Figure6-18 Install the calibration needle

(2) Place the calibration board on the standard vision board, as shown in Figure6-

19.

Figure6-19 Place the Calibration board

Note: In order to avoid the vision interference of the grain on the standard vision board, you

can place a piece of paper on the standard vision board.

* (3) Open DobotVisionStudio and select **General Solution** .
* (4) Establish the flow. Drag **Image Source** in Acquisition toolbox to the flow
* editing area, as shown in Figure6-20.

![Official MG400 training-system figure, source page 161](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fb5FKRuKI4FzK5LKoV7rX%2Futp-b749f810b0a0ed3c0fc4.jpg?alt=media)

![Official MG400 training-system figure, source page 161](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZkKjagL0cKS3198NGy99%2Futp-9c193a8f0101c810d314.jpg?alt=media)

Figure6-20 Flow

① Set **0Image Source1** parameters. Double click **0Image Source1** to set parameters. Select **Image Source** to **Camera** , as shown in Figure6-21. Click **Camera set** on the right side of **Relate Camera** to enter the corresponding page.

Figure6-21 Set Image source parameter

②Create the global camera. Click **+** on the right side of **Device List** to create **1 Global Camera1** and set the parameters of the camera. In the “Common Params” tab, click the triangle in the lower right corner of **Choose Camera** to open the drop-down list and select the camera that is currently connected to the computer. Select **Mono8** for **Pixel Format** , as shown in Figure6-22. Click “Trigger Settings” tab, and set **Trigger Source** to **SOFTWARE** . Then click **Confirm** , as shown in Figure6-23. In “0 Image Source” page, click the triangle in the lower right corner of **Relate Camera**

![Official MG400 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F05SyxvYsSkCNccpWkjOr%2Futp-d6b17ccbf095379e4cc0.png?alt=media)

![Official MG400 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYh4PiYmIbqGLOjETa40i%2Futp-664e160b702aed1a395e.png?alt=media)

and select **1Global Camera1** , as shown in Figure6-24.

Figure6-22 Set Camera management Common Parameters

Figure6-23 Camera management trigger setting

Figure6-24 Image source related camera

![Official MG400 training-system figure, source page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuJYKQskIO6eHS7bHKRkx%2Futp-0fc8e039b03961c8ffbb.png?alt=media)

![Official MG400 training-system figure, source page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxQMFOirRac9SBMYflD3G%2Futp-ebbdbf9bfdd9f3baab00.png?alt=media)

![Official MG400 training-system figure, source page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F05SyxvYsSkCNccpWkjOr%2Futp-d6b17ccbf095379e4cc0.png?alt=media)

③Click (Continuously) to adjust the aperture and focus ring of the lens and the exposure time of the camera until you can see a clear image in the image display area. The image acquisition result is shown in Figure6-25.

Figure6-25 Image acquisition result

* (5) Add **CalibBoard Calib** in the flow.

Drag **CalibBoard Calib** in Calibration toolbox to the flow editing area and

connect it with **0Image Source1** , as shown in Figure6-26.

Figure6-26 Flow

Note: The calibration of the calibration board is used to obtain the calibration point, and provide the pixel coordinates of the calibration point for N-point calibration.

* (6) Add **N-point Calibration** in the flow.

①Drag **N-point Calibration** in Calibration toolbox to the flow editing area, and

connect it with **2CalibBoard Calib1** ， as shown in Figure6-27. Click (Once) in

the toolbar, and nine calibration points and their calibration sequence are shown automatically in the image display area, as shown in Figure6-28.

![Official MG400 training-system figure, source page 164](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWwCIl3KWVSTfwfLdCCcT%2Futp-cef4e12a4e4474f4937d.jpg?alt=media)

Figure6-27 Flow

Figure6-28 Check nine calibration points and calibration sequence

② Set **3N-point Calibration1** basic parameters. Double click **3N-point Calibration** to set basic parameters. In “Basic Params” page, set **Translation Number** to **9** by default, as shown in Figure6-29. Click on the right side of **Rotation Number** to edit the calibration points, as shown in Figure6-30.

![Official MG400 training-system figure, source page 165](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F07bvhlsTBXwo5JPOkYMK%2Futp-bc4ae3a578a41074915f.jpg?alt=media)

Figure6-29 3N-point calibration parameter setting

Figure6-30 Edit Calibration Points

In “Edit Calibration Points” page, exchange Line 3 (ID: 3) and Line 5 (ID: 5) data, as shown in Figure6-31.

![Official MG400 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtXZZZNHASkf0gg82pSgl%2Futp-b20f2adbc901cb2af5c1.png?alt=media)

![Official MG400 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHWKxsDMLBZEuRHoLbrTe%2Futp-33c837e98a0506dcdec5.png?alt=media)

Figure6-31 “Edit Calibration Points” after data exchange

Click (Once) and you will see that the calibration sequence in the image

display area turns to “ ”shape, as shown in Figure6-32.

Figure6-32 Calibration sequence after data exchange

③Open DobotStudio Pro. Connect and enable the robot. Move the robot to each of the nine calibration points according to the calibration sequence, as shown in Figure6-33. Read the physical coordinates X and Y of each point in DobotStudio Pro, as shown in Figure6-34. Then fill the X and Y values in the physical coordinates of “Edit Calibration Points” page in DobotVisionStudio, as shown in Figure6-35.

![Official MG400 training-system figure, source page 167](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FniccHjTLtHOB8VTr9fvE%2Futp-fe41272313dcd6ce3af0.jpg?alt=media)

![Official MG400 training-system figure, source page 167](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuN5vkKFFg4beBNlbTK6b%2Futp-ad65c05c04fa492b8810.png?alt=media)

Figure6-33 Locate the First calibration point

Figure6-34 Physical coordinates of the first calibration point

![Official MG400 training-system figure, source page 168](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fljwu1gyGdbSYEuk1JRvH%2Futp-2c5beab35a12c521eca2.jpg?alt=media)

![Official MG400 training-system figure, source page 168](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUTu1SfTCC7ObBV8C7iDm%2Futp-5081b5b94f1f0f3bb725.jpg?alt=media)

Figure6-35 Physical coordinates of 9 calibration points

Note: For the method to connect and enable the robot, see 3.3 and 3.4.

④After editing the calibration points, click (Once). Click “Basic Params” tab of **3N-point Calibration** . Click **Create Calibration File** to export the calibration file to local and name it as “Calibration file” for being called later, as shown in Figure6-36.

Figure6-36 Generate calibration file

* (7) Add **Calibration Transformation** in the flow.

①Verify whether the calibration is accurate. Drag **Calibration Transformation** in **Calculation** toolbox to the flow editing area and connect it with **3N-point**

![Official MG400 training-system figure, source page 169](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSEdgxT33gDqcGVPCWSOW%2Futp-2d2c5fd880f31dbf7f61.png?alt=media)

![Official MG400 training-system figure, source page 169](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVwEwlIrOqkXnDMNVpjPm%2Futp-8dfc5b1683f69d913a5b.png?alt=media)

**Calibration1** , as shown in Figure6-37.

Figure6-37 Flow

②Set **4Calibration Transformation1** parameters. In “Basic Params” page, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** , **Load Calibration File** to **Calibration file** generated from 3N-point Calibration1, as shown in Figure6-38.

Figure6-38 Set 4Calibration Transformation1 parameters

③Click (Once) and check whether the nine coordinates after 4Calibration

Transformation1 （ as shown in Figure6-39 ） are consistent with the physical coordinates in 3N-point Calibration1. If consistent, the calibration is accurate.

![Official MG400 training-system figure, source page 170](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnYRiVeX96GJLzlRiUhtj%2Futp-9c13af414e9b584b0f5f.png?alt=media)

Otherwise, you need to re-calibrate.

Figure6-39 Compare Results

After the calibration is completed, it is necessary to remove the calibration needle from the suction nozzle connecting rod and replace it with a suction nozzle.

#### 3.6.2 Import vision program

Open DobotVisionStudio 4.1.2 and select **General Solution** . Select **Open** in the toolbar. Find the phone chip assembly program and click **Open** . The imported vision

program is shown in Figure6-40.

Figure6-40 Vision program

![Official MG400 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbgHHcJp6EURCMZxyQpWG%2Futp-2665f436d73070216d40.png?alt=media)

![Official MG400 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZIJwWKlNB4rx9v95LH7M%2Futp-e1a803b4eb9d8a6d5f92.png?alt=media)

![Official MG400 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhY0PcsrLYGAnWIBGpm3r%2Futp-ebba1806e0cfa5c3702e.png?alt=media)

#### 3.6.3 Place phone model

Place the phone model on the phone model board, as shown in Figure6-41.

Figure6-41 Place phone model

#### 3.6.4 Place phone chips

Place six chips within the detection vision, as shown in Figure6-42. For the first

time of debugging, ensure that the chips are placed in the same orientation as that inside the phone model in the assembly area.

Figure6-42 Place chips within the detection view

#### 3.6.5 Debug parameters

(1) Debug **0Image Source1** parameters.

Click (Once), select **0Image Source1** and observe whether the image is clear. If the image is not clear or there is no image, you need to reset the parameters according to the method described in 3.6.1.

![Official MG400 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fcg3N8VrlSkF6VZRapFWk%2Futp-13a7948cbbfd67d782aa.jpg?alt=media)

![Official MG400 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJjIgiwIjWxJfJVWwLQ24%2Futp-c718f58b242d757b49de.jpg?alt=media)

The image acquisition result is shown in Figure6-43.

Figure6-43 Image acquisition result

(2) Debug **2Fast Match1** parameters.

Click (Once). Select **2Fast Match1** and observe whether all types of chips can be recognized. If not, you need to modify 2Fast Match1 parameters, as described below.

Set Basic Params as shown in Figure6-44.

Figure6-44 Set 2Fast Match1 parameters

Click **Feature Model** . Select the first feature model **hexagon** and click **Edit**

![Official MG400 training-system figure, source page 173](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOU0Gj7c6ze3EzhRtBsTa%2Futp-a3d205e884d1994aff01.jpg?alt=media)

![Official MG400 training-system figure, source page 173](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJZmJ6jN8pO0UUUPLpofn%2Futp-6498c02eb7d9bcc6e44a.png?alt=media)

**Model** , as shown in Figure6-45. In ModelSettings page, click **Current image** , as shown in Figure6-46. Click **Create Rect Mask** and drag to generate the rectangular mask to cover the hexagonal material. Configure the parameters in the lower right corner. Set **Scale Mode** and **Thres Mode** according to the actual condition. Click **Build Model** to generate the feature model, as shown in Figure6-47. Finally, click **Confirm** to save the feature model.

Figure6-45 Feature Model

Figure6-46 ModelSettings

![Official MG400 training-system figure, source page 174](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0TcVRj7r5z81rwNMnImt%2Futp-2902aa02584fbac85084.png?alt=media)

![Official MG400 training-system figure, source page 174](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1oPhEO40dQmb6idgiwez%2Futp-037376539656d34ddee8.jpg?alt=media)

Figure6-47 Update feature model

Modify the feature models of CPS chip, electronic compass, gravity sensor, WiFi chip and photosensor following the method above.

Note: The model sequence must be consistent with Figure6-45 , which corresponds to the

robot program.

* (3) Debug 3Calibration Transformation1 parameters.

Double click **3Calibration Transformation1** to set parameters. In “Basic Params” page, set **Coord Point** to **2 Fast Match1.Match Point\[]** , **Load Calibration**

**File** to **Calibration file** generated from N-point Calibration, as shown in Figure6-48.

![Official MG400 training-system figure, source page 175](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9koIMnPylbh5038yYe7Z%2Futp-bb678f18f05245e3706a.jpg?alt=media)

![Official MG400 training-system figure, source page 175](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9TF1NLrOvsj23Vk5Q7us%2Futp-17efef61822b5520d99c.png?alt=media)

Figure6-48 Set 3Calibration Transformation1 parameters

(4) Debug 4Variable Calculation1 parameters.

Double click **4Variable Calculation1** and check whether the **Expression** is “-<2 Fast Match1.MatchBoxAngle>\[0]”, as shown in Figure6-49. If not, modify it to “-<2 Fast Match1.MatchBoxAngle>\[0]”.

Figure6-49 Set **4Variable Calculation** parameters

(5) Debug **5Format1** parameters.

Double click **5Format1** , and check whether the parameters are “<2 Fast Match1.MatchModelIndex(%0d)>\[0], <3 Calibration Transformation1.TransPointX (%1.3f)>\[0], <3 Calibration Transformation1.TransPointY(%1.3f)>\[0], <4 Variable Calculation1.var0(%1.3f)>\[0]”, as shown in Figure6-50. If not, modify it as the figure.

![Official MG400 training-system figure, source page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3jIN4iqulho0qFtgsQtS%2Futp-739486d810672e7d9931.png?alt=media)

Figure6-50 Set 5Format1 parameters

6. Debug Communication Management parameters.

Click in the toolbar to enter “Communication Management” page. Check whether there is created TCP Server. If not, you need to re-create one, as described

below. Click beside Device List. Set **Protocol Type** to **TCP Server** , **Load IP** to **192.168.1.18** , and **Local Port** to **4001** , as shown in Figure6-51. Then click **Create** . The TCP Server is shown in Figure6-52 . Switch on **1TCP Server** . If there is TCP Server, check whether its parameters are consistent with Figure6-52 . If not, modify as the figures.

![Official MG400 training-system figure, source page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYufYaNBCSe5e9gVLddHO%2Futp-c53a51e837c032017f15.png?alt=media)

Figure6-51 Create TCP Server

Figure6-52 Communication Management parameters setting

(7) Debug **6Send Data1** parameters.

Double click **6Send Data1** and check whether the parameters are shown as Figure6-53. If not, modify as the figure. Set **Output To** to **Communication Device** , **Communication Device** to **1 TCP Server** , **SendData1** to **5Format.format\_out\[]** .

![Official MG400 training-system figure, source page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoSo4xNn4h66EP7GkQWdF%2Futp-5f7c8da130e057eb0547.png?alt=media)

![Official MG400 training-system figure, source page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD6f7JcJqQEFzG4fDTcrZ%2Futp-85a3d6966836c4cc0090.png?alt=media)

Figure6-53 Set 6Send Data1 parameters

(8) Global trigger settings.

Click in the toolbar to enter “Global Trigger” page. In “String Trigger” page, check whether the string trigger setting is shown in Figure6-54. (String is void. Mode is Mismatched. Trigger Configuration is All Process).

Figure6-54 Set Global Trigger parameters

#### 3.6.6 Save program

Click in the toolbar to save the program. If you need to save the program elsewhere on your local computer, click **File** > **Save as** , select the saving path and

enter the name of the project.

#### 3.7 Debug robot program

#### 3.7.1 Import program

(1) Open DobotStudio Pro and enter Script page. Click **File** > **Import project** , as shown in Figure6-55.

![Official MG400 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBVNdtwUAkJF2LIJVD4XC%2Futp-a22a6268b6e9c7616adc.png?alt=media)

![Official MG400 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fl3G1f2QjG6Anjpid5SQI%2Futp-3830284a2f5fbaf6c556.png?alt=media)

Figure6-55 Import project

(2) Select **Mobile\_phone\_chip\_assembly** folder and click **Open** , as shown in

Figure6-56. Now the phone chip assembly program has been imported into DobotStudio Pro, as shown in Figure6-57.

Figure6-56 Import path

![Official MG400 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLeqxgeOUkD2g26gwYFrj%2Futp-dacf360c67e0778a3524.png?alt=media)

![Official MG400 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpbSDVRWtH41wUXSdsGM7%2Futp-90aefc2720682e5c1c55.png?alt=media)

Figure6-57 Project imported

#### 3.7.2 Save program

Click . Enter a project name in the pop-up dialog box and click **OK** , as

shown in Figure6-58.

Figure6-58 Save the program

#### 3.7.3 Communication management settings

Ensure that the IP address and port of TCP server in the robot program are consistent with those in vision communication settings, that is, set IP address in the robot program to 192.168.1.18 and port to 4001, as shown in Figure6-59.

![Official MG400 training-system figure, source page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F613RI2rhyqgcRhS7jzFc%2Futp-bc06687927a95b2a561b.png?alt=media)

![Official MG400 training-system figure, source page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6fxUR91UeWVwAPwBUWML%2Futp-900d2a41f6f7bbad0de8.png?alt=media)

Figure6-59 Communication management settings

#### 3.7.4 Program debugging

* (1) Modify Z coordinate of the picking point.

Drag or jog the robot make the suction cup slightly touch the surface of the chips, as shown in Figure6-60. Then read the current Z coordinate of the robot, as shown in Figure6-61. Modify the Z coordinate in the command “local GetProductPos = {coordinate = {move\_x,move\_y,6.3,move\_r}, tool = 0, user = 0}” in the chip pickup

sub-program to the current Z coordinate.

Figure6-60 Picking point

![Official MG400 training-system figure, source page 182](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F937ec5qZLR6iUeGDMIRg%2Futp-67d9dd8dcbb4b393baf4.jpg?alt=media)

Figure6-61 Z coordinate of picking point

(2) Modify Z coordinate over the picking point.

Jog the robot to lift some distance, as shown in Figure6-62. Then read the Z coordinate of the robot, as shown in Figure6-63. Modify the Z coordinate in the command “local GetProductPosUp = {coordinate = {move\_x,move\_y,37,move\_r}, tool = 0, user = 0}” in the chip pickup sub-program to the current Z coordinate. Click “ ”to save the program.

![Official MG400 training-system figure, source page 183](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyMd076FgiaHzEgmajyF4%2Futp-cc00e7ec318eb97d7ca1.jpg?alt=media)

Figure6-62 Over picking point

Figure6-63 Z coordinate over picking point

![Official MG400 training-system figure, source page 184](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKBaJessaCqjwEE27z62D%2Futp-d35153d38a048011d8aa.jpg?alt=media)

![Official MG400 training-system figure, source page 184](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkYEZCgQ9ThWe1frp14Hk%2Futp-61d7bc231ba56f4aa28f.jpg?alt=media)

#### 3.7.5 Debug points

* (1) Update the safe point P1.

Jog or drag the robot to a position between the conveyor belt and the storage area, as shown in Figure6-64. Click **Points** in the right-side menu of DobotStudio Pro. Select **P1** and click **Cover** . Then click OK in the pop-up Tips dialog box, as shown in

Figure6-65. Click“ ”to save the program.

Figure6-64 Locate Point P1

![Official MG400 training-system figure, source page 185](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx6YEhplqaDypdkaQwudx%2Futp-7587be41f3a1e75e90ec.jpg?alt=media)

![Official MG400 training-system figure, source page 185](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeqM2LK3chsJj417p7oJm%2Futp-3bcac6c829c4a36f569c.jpg?alt=media)

Figure6-65 Update P1

Note: After updating each point, the program needs to be saved once.

(2) Update the Hexagonal chip assembly point P2.

Click to make the robot suck the hexagonal chip according to the

coordinates sent by the vision system. Then click immediately. Jog the robot to the hexagonal chip assembly area, as shown in Figure6-66. Click **Points** in the right-side menu of DobotStudio Pro. Select **P2** and click **Cover** . Then click **OK** in

the pop-up Tips dialog box, as shown in Figure6-67. Click“ ”to save the program.

Figure6-66 Locate Hexagonal chip assembly point P2

![Official MG400 training-system figure, source page 186](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOFtJJLS4dLBXidhtxED3%2Futp-4bac718ca3e476350443.jpg?alt=media)

Figure6-67 Update P2

Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set **DO\_10** to **OFF** and observe whether the hexagonal chip is placed into the groove accurately. If not, you need to re-debug the point.

(3) Update the GPS chip assembly point P3.

Click to make the robot suck the GPS chip according to the coordinates sent by the vision system and click . Jog the robot to the GPS chip assembly point in the assembly area, as shown in Figure6-68. Select **P3** in **Points** page and click **Cover** . Then click **OK** in the pop-up Tips dialog box, as shown in Figure6-69. Click“ ”to save the program.

![Official MG400 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD1r0ggX98AS1zz8fwc73%2Futp-dcaf3a69a563ec0fb013.png?alt=media)

Figure6-68 Locate GPS chip assembly point P3

Figure6-69 Update P3

Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set

**DO\_10** to **OFF** and observe whether the GPS chip is placed into the groove accurately. If not, you need to re-debug the point.

* (4) Update the electronic compass chip assembly point P4.

Click to make the robot suck the electronic compass chip according

to the coordinates sent by the vision system and click . Jog the robot to the electronic compass chip assembly point in the assembly area, as shown inFigure6-70.

![Official MG400 training-system figure, source page 188](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGsEXyqOu7LjMNdUy3Fcb%2Futp-8bad0ede6516155f46a1.jpg?alt=media)

![Official MG400 training-system figure, source page 188](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoUg5EnKusuL6461gnIAw%2Futp-57043e280220893c8075.png?alt=media)

Select P4 in **Points** page and click **Cover** . Then click **OK** in the pop-up Tips dialog

box, as shown in Figure6-71. Click“ ”to save the program.

Figure6-70 Locate Electronic compass chip assembly point P4

Figure6-71 Update P4

Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set

**DO\_10** to **OFF** and observe whether the electronic compass is placed into the groove accurately. If not, you need to re-debug the point.

* (5) Update the gravity sensor chip assembly point P5.

![Official MG400 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH5hFX3T8B2bptfiuOuGA%2Futp-206f9c69c1e7ae9a2671.jpg?alt=media)

![Official MG400 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYmFD1BGLEBQE2Xj43iHN%2Futp-b112c2f23c4a85113098.png?alt=media)

Click to make the robot suck the gravity sensor chip according to the coordinates sent by the vision system, and click . Jog the robot to the gravity sensor chip assembly point in the assembly area, as shown in Figure6-72. Select **P5** in **Points** page and click **Cover** . Then click **OK** in the pop-up Tips dialog

box, as shown in Figure6-73. Click“

”to save the program.

Figure6-72 Locate Gravity sensor chip

Figure6-73 Update P5

Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set

![Official MG400 training-system figure, source page 190](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcdGxK7OlMjMoGiuWeEor%2Futp-90ce1feebac950bab46d.jpg?alt=media)

![Official MG400 training-system figure, source page 190](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7gQWqHWdzQUKPlXFBfXp%2Futp-5c66b6b70841d1e12a59.png?alt=media)

**DO\_10** to **OFF** and observe whether the gravity sensor chip is placed into the groove accurately. If not, you need to re-debug the point.

* (6) Update the WiFi chip assembly point P6.

Click to make the robot suck the WiFi chip according to the

coordinates sent by the vision system and click . Jog the robot to the WiFi chip assembly point in the assembly area, as shown in Figure6-74. Select **P6** in **Points** page and click **Cover** . Then click **OK** in the pop-up Tips dialog box, as shown in

Figure6-75. Click“ ”to save the program.

Figure6-74 Locate WiFi chip assembly point P6

![Official MG400 training-system figure, source page 191](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWxvJZyQxnY8bgO2cSZHL%2Futp-bb48422486289629ab09.jpg?alt=media)

Application of Phone Chip Assembly<br>

Figure6-75 Update P6

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, set **DO\_10** to **OFF** and observe whether the WiFi chip is placed into the groove accurately. If not, you need to re-debug the point.

* (7) Update the photosensor chip assembly point P7.

Click to make the robot suck the photosensor chip according to the

coordinates sent by the vision system and click . Jog the robot to the photosensor chip assembly point in the assembly area, as shown in Figure6-76. Select **P7** in Points page and click **Cover** . Then click **OK** in the pop-up Tips dialog box, as

shown in Figure6-77. Click“ ”to save the program.

![Official MG400 training-system figure, source page 192](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBSofBaqgphf7CyTYCjQw%2Futp-29ed9ce9826a36f48f92.png?alt=media)

Figure6-76 Locate photosensor chip assembly point P7

Figure6-77 Update P7

Open **I/O** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second , set

**DO\_10** to **OFF** and observe whether the photosensor chip is placed into the groove accurately. If not, you need to re-debug the point.

After debugging all the points, click **Save** .

Note: Saving a program refers to saving the program to the robot controller. If you want to save the program to local, you need to export the project.

![Official MG400 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnjmD6iUynuYTuRSZMvpl%2Futp-c230739678c69859e710.jpg?alt=media)

![Official MG400 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBSr2471SOObKmp2fj3P0%2Futp-6043fb9e1cc6f225cee3.jpg?alt=media)

#### 3.7.6 System running

Place all the chips on the standard vision board. Open the vision program. Click

in DobotStudio Pro. The program starts running. After receiving the chip coordinates sent by the vision system, the robot sucks the phone chips from the standard vision board and assembles them into the corresponding grooves of the phone models. The installed phone is shown in in Figure6-78.

Figure6-78 Installed phone

#### 3.7.7 Export program

Click **File** > **Import project** and select the path to save the program. Then enter

a project name in the pop-up dialog box, as shown in Figure6-79.

Figure6-79 Export project

![Official MG400 training-system figure, source page 194](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRTqJUwmXsHymkFX2JBpB%2Futp-21d21f4d4b70c089b343.jpg?alt=media)

![Official MG400 training-system figure, source page 194](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYtieCGAQhd1NCr2SJuRR%2Futp-d978f04fe5f576f8f289.png?alt=media)

Note: Exporting a project refers to export the program to local for backup.

### 4. Key Program Description

#### 4.1 Vision program description

The vision program is shown in Figure6-80. **0Image Source1** is mainly used for image acquisition. During the running process of the system, once the vision software receives the trigger signal from the robot. The camera takes photos immediately. **2Fast Match1** is mainly used for positioning, in order to obtain the image coordinates and matching angle of the detected object. **3Calibration Transformation1** is used for transforming the image coordinates to the actual physical coordinates. **4Variable Calculation1** is used for correcting the matching angle. **5Format1** is used for summarizing the information that the vision system needs to send to the robot and defining the format. **6Send Data1** is used for sending the 5Format1 content to the robot.

Figure6-80 Vision program

#### 4.2 Robot program description

#### 4.2.1 Data transmission program

The data transmission program is shown in Figure6-81, which mainly sends

photography trigger signal “OK” and receives the data sent by the vision system.

Figure6-81 Data transmission program

#### 4.2.2 Robot pick-up program

The robot pick-up program is shown in Figure6-82. The function of the program is that the robot sucks the chips on the standard vision board according to the

coordinates sent by the vision system.

Figure6-82 Robot pick-up program

#### 4.2.3 Output port reset program

The output port reset program is shown in Figure6-83, which sets all output ports

to **OFF** .

Figure6-83 Output port reset program

![Official MG400 training-system figure, source page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYwQBEYMOBKHluW9cJMvq%2Futp-cc08d7782573be5605d9.png?alt=media)

![Official MG400 training-system figure, source page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5EoVkcGaL1ctUzkBnHTB%2Futp-3b993b250962b329c069.png?alt=media)

#### 4.2.4 Communication program

The communication program is shown in Figure6-84, which mainly creates TCP

client and establish connect with TCP server (vision).

Figure6-84 Communication program

#### 4.2.5 Robot assembly program

The robot assembly program is shown in Figure6-85. The function of the program is that the robot assembles the phone chips into the corresponding grooves of

the phone models according to the chip index sent by the vision system.

(1)Assemble a hexagonal chip

(2)Assemble a GPS positioning chip

(3)Assembling a electronic compass chip

![Official MG400 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMXlLNLBoBPqR7frLoPsS%2Futp-ab386d214b94ceece495.png?alt=media)

![Official MG400 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMGEgksdF7Bo1xl9DGh7d%2Futp-33cfc062e7a464927c7c.png?alt=media)

![Official MG400 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtdFrhTgIGKg1UaYLihpH%2Futp-53517b18a0a40e0ea7e8.png?alt=media)

Application of Phone Chip Assembly<br>

(4)Assemble a gravity sensor chip

(5)Assemble a WIFI chip<br>

(6)Assemble a photosensitive sensor chip

Figure6-85 Robot assembly program

![Official MG400 training-system figure, source page 198](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyHe8njv8JHuGAINi0UYK%2Futp-62a11d93ebbfe0afc7aa.png?alt=media)

![Official MG400 training-system figure, source page 198](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FADkeKAmoAT2qobmOjapZ%2Futp-5de4dfc173c365b4626f.png?alt=media)

![Official MG400 training-system figure, source page 198](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRW8b5zEoNt1ZaRJx317C%2Futp-d561432c0151dae196cc.png?alt=media)

## Official source and related installation guides

The complete English source is in the [official DOBOT Universal Training Platform operation-instruction archive](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260722/1770703893557_Collaborative%20Robot%20Universal%20Training%20Platform%20Operation%20Instruction-EN.rar). Select file `02-Collaborative Robot Universal Training Platform（MG400_include PLC）_20260211_en.pdf`. The archive also contains the platform installation, emergency-stop wiring, conveyor, and PLC-upgrade guides.
