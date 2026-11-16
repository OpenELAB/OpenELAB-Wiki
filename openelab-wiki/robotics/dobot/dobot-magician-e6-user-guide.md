---
description: >-
  User guide for the DOBOT Magician E6 collaborative robot, covering safety,
  transportation, product specifications, interfaces, installation, wiring,
  maintenance, disposal, and technical data.
---

# DOBOT Magician E6 User Guide

## DOBOT E6 Robot with ES01 Electric Suction Cup

{% embed url="https://openelab.io/products/dobot-e6-es01-suction-robot" %}

## Contents

* Preface
* 1\. Safety
* 2\. Transportation
* 3\. Product Introduction
* 4\. Product Features
* 5\. Mechanical Specifications
* 6\. Electrical Features
* 7\. Installation and Use
* 8\. Maintenance
* Maintenance
* 9\. Warranty
* Appendix Technical Specifications

Copyright © Shenzhen Yuejiang Technology Co., Ltd. 2024. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of Shenzhen Yuejiang Technology Co., Ltd (hereinafter referred to as “Dobot”).

### Disclaimer

To the maximum extent permitted by applicable law, the products described (including its hardware, software, and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses will be happening in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure of following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot. Shenzhen Yuejiang Technology Co., Ltd. Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

## Preface

Purpose This document introduces the functions, technical specifications and installation procedure of Dobot Magician E6 robots, which is convenient for users to understand and use the robot. Intended Audience This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Change History Date Issue Change Description 2024/03/06 V1.4 Add load curve 2024/01/16 V1.3 Add tool IO interface type 2023/10/25 V1.2 Modify button trigger time (Controller V4.4.0.0 and above) 2023/07/19 V1.1 Update description on trajectory playback Update content styles 2023/06/29 V1.0 The first release Symbol Conventions The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could

**DANGER**

result in death or serious injury Indicates a hazard with a medium level or low level of risk which, if not

**WARNING**

avoided, could result in minor or moderate injury, robot damage Indicates a potentially hazardous situation which, if not avoided, can

**NOTICE**

result in equipment damage, data loss, or unanticipated result Provides additional information to emphasize or supplement important

**NOTE**

points in the main text

## 1. Safety

### 1.1 Liability

#### 1.1.1 Validity and responsibility

The information in this document does not cover designing, installing and operating a complete robot system, nor does it cover all peripheral equipment that can affect the safety of the complete system. The complete system must be designed and installed in accordance with the safety requirements set forth in the standards and regulations of the country where the robot is installed. The integrators of Dobot are responsible for ensuring that the applicable safety laws and regulations in the country concerned are observed and that any significant hazards in the complete robot application are eliminated. This includes, but is not limited to:

* Performing a risk assessment for the complete robot system.
* Adding safety machines and mechanisms based on the risk assessment.
* Setting up the appropriate safety settings in the software.
* Ensuring that the user will not modify any safety measures.
* Validating that the total robot system is designed and installed correctly.
* Specifying instructions for use.
* Marking relevant signs and contact information of the integrators on the robot.
* Archiving relevant technical files.

#### 1.1.2 Limitation of liability

Any safety information provided in this document should not be construed as a warranty, by Dobot. The robot may cause injury or damage even if all safety instructions are observed.

#### 1.1.3 Intended use

The Dobot Magician E6 is a collaborative robot designed for education and scientific research (only for general education and research purposes, such as robotics teaching with a training system). Dobot Magician E6 robots are equipped with special safety mechanisms including collision detection. These mechanisms are purposely designed for human-robot collaborative operation, but only intended for non-hazardous applications after risk assessment, where tools, commodities, environments and other machines have been demonstrated to be incapable of significant risk through application-specific risk assessments. Any use or application deviating from intended use is deemed to be impermissible misuse, including, but is not limited to:

* Use in potentially explosive environments.
* Use in life critical applications.
* Use before performing a risk assessment.
* Use over-stated specifications.
* Use as a climbing aid.

### 1.2 Safety warning signs

The following safety warning signs may appear in this document, and their meanings are described as follows. The same safety warning signs are also used in the products. Sign Description Indicates a high degree of potential danger, which, if not avoided, will

**DANGER**

result in death or serious injury. May cause dangerous power consumption soon, which, if not avoided, ELECTRICITY will cause personal injury or serious damage to the equipment. May cause dangerous hot surfaces, which, if touched, may cause HOT personal injury. or Indicates a moderate or low potential hazard, which, if not avoided, may

**WARNING**

cause minor personal injury and damage to the equipment. Indicates a potential risk, which, if ignored, may result in damage to the ATTENTION robot arm, loss of data or unpredictable results A situation that, if not avoided, can cause personal injury or damage to

**NOTICE**

the equipment. For items marked with such signs, depending on the specific situation, there is sometimes a possibility of significant consequences

### 1.3 General safety

Follow the safety instructions below when starting and using the robot for the first time.

**DANGER**

* The robot system is electrical equipment. Non-professional technicians should not modify the circuit, otherwise, it may cause damage to devices or personal injury.
* Comply with the local laws and regulations when operating the robot. The security precautions in this document are only supplemental to the local laws and regulations.
* Use the robot in the specified environment scope. Exceeding the specifications or load conditions will shorten the service life of the robot, even damage it.
* Ensure that the robot is operated under the security conditions and there is no harmful object around the robot.
* Turning on or off the power continually may result in degraded performance of the main circuit components inside the controller. If turning on or off the power continually is required, please keep the frequency less than once per minute. HOT
* The robot and the controller will generate heat during operation. Please do not operate or touch the robot when the robot is working or has just stopped working.
* Turn off the power and wait an hour for the robot to cool down.
* Do not put your fingers to where the control cabinet gets hot.

**NOTICE**

* The personnel responsible for installation, operation and maintenance of equipment must first receive strict training, understand various safety precautions, and master correct operation and maintenance methods before they can operate and maintain equipment.
* Personnel without professional training shall not disassemble and repair the equipment without authorization. If the device fails, please contact Dobot technical support engineer in time.
* Be sure to carry out daily inspections and regular maintenance, and replace faulty components in time to ensure the safe operation of the equipment.
* If the equipment is scrapped, please comply with relevant laws to properly handle industrial waste and protect the environment.
* Please establish safety measures (such as guardrails, ropes or warning lines) near the operating area of the robot to ensure that personnel remain out of reach of the robot being operated or the robot about to start operation.
* Do not enter the safety range of the robot as determined by the risk assessment or touch the robot while the system is in operation.
* Do not expose the robot to permanent magnetic fields all the time. Strong magnetic fields can cause damage to the robot.
* Dobot assumes no responsibility for robot damage or personal injury caused by failure to follow product instructions or other improper operations.
* Use appropriate and reliable lifting equipment during handling operations such as lifting rings and bridge crane. According to the relevant regulations of various countries, it must be carried out by personnel with operating qualification certificates or personnel authorized by the company.
* Make sure that there are no obstacles within 2 meters of the robot during transportation. Relevant personnel should stay away from the suspended robot.
* Dobot is not responsible for any damage caused during the transportation and handling of equipment.
* Make sure that the robot is in the packing posture before packaging, and the brakes on each axis are normal.
* Make sure that there are no obstacles around the packing area, so that the staff can
* When the robot is transported, the packaging needs to be fixed to ensure that the robot is stable.
* After removing the outer packaging, make sure that the robot maintains the original packing posture and the brakes of each axis are normal.
* During the commissioning process, make sure that no relevant personnel and equipment (include computer used for debugging) stay in the dangerous area of the machine.
* If necessary, wear corresponding safety protective equipment, such as safety helmets, safety shoes (with non-slip soles), face shields, protective glasses and gloves. Inappropriate clothing may cause personal injury.
* In order to prevent personnel from entering the working space of the robot arm by mistake, please set up safety barriers to prevent personnel from entering the hazardous area.
* Do not enter the working space of the manipulator at will during operating the robot, otherwise cause injury to the robot or yourself.
* The personnel responsible for installation, operation, and maintenance of the equipment must first undergo strict training, understand various safety precautions, and master the correct operation and maintenance methods before operating and maintaining the equipment.
* When an abnormality occurs in the mechanical arm, it is necessary to ensure that the machine is stopped and then checked.
* After the commissioning of the operator is completed, the test needs to be performed in the Manual mode first, and then it is automatically run after it is confirmed to be correct.
* If the controller needs to be restarted due to power failure, when restarting, the robot must be manually returned to the initial position of the automatic operation program before restarting the automatic operation.
* Before maintenance and wiring work, the power supply must be cut off, and the sign

No power supply must be put on. Otherwise, electric shock and personal injury may result.

* Please observe the ESD regulations when disassembling the robot or controller.
* Avoid dismantling the power supply system in the controller. After the controller is turned off, its power supply system may still have high voltage for several hours.
* Please contact our technical support staff for the disassembly and repair of the robot.
* Maintenance and repair work must be carried out by designated personnel, otherwise electric shock and personal injury may result.
* If the brake is manually released, the robot may move because of the action of gravity.

So, when manually releasing the brake, please ensure that the robot body and the tools or workpieces installed on the robot are effectively supported.

* In order to prevent electric shock, when replacing parts, please turn off the circuit breaker in advance and cut off the main power before proceeding.
* Turn off the main power supply for 5 minutes before replacing parts.
* The replacement operation must be performed by the specified operator.
* The robot is designed and tested according to the group I class A engineering medical robot standard. In order to reduce the radio interference in in light industry or family environment, please take protective measures.
* It is prohibited to operate the robot in strong radiation environment (such as RF source without shielding), otherwise, it could interference robot work.

**WARNING**

* Before the operation, please wear protective clothing, such as antistatic uniform, protective gloves, and protective shoes.
* It is prohibited to modify or remove the nameplates, instructions, icons and marks on the robot and the related equipment.
* Before operating the equipment, please find and be familiar with the operation method of the emergency stop function to ensure that the robot arm can be stopped urgently in the case of sudden stress. The emergency stop function is Stop Category 1.
* Be careful when carrying or installing the robot. Please follow the instructions on the packing box to put down the robot gently and place it correctly in the direction of the arrow.
* Please use the matched cables when connecting a robot to internal or external equipment for personal security and equipment protection.
* Please ensure that the robot and tools are installed correctly.
* Please ensure that the robot has enough space to move freely.
* If the robot is damaged, do not continue to use it.
* Any impact will release a lot of kinetic energy, which is much higher than that under high speed and high load.

### 1.4 Personal safety

When operating the robot system, please strictly follow the general precautions listed below to ensure the personal safety of the operator.

**WARNING**

* Please comply with local laws or regulations with regard to the maximum weight one person is permitted to carry.
* Do not touch the terminal blocks or disassemble the equipment with the power ON.

Otherwise, it may result in an electric shock.

* Please confirm that the equipment is well grounded, otherwise it will endanger personal safety.
* Do not touch the terminal blocks or remove the interval circuit components within

10 minutes after the power is shut off, so as to avoid an electric shock since there is residual capacitance inside the controller.

* Even if the power switch of the controller is already in the OFF status, touching the terminal blocks or removing the interval circuit components is not allowed, so as to avoid an electric shock since there is residual capacitance inside the controller.
* When working with robots, do not wear loose clothing or jewelry. When operating the robot, make sure that you have bundle your hair behind your head.
* If the robot appears to have stopped during the operation of the equipment, it may be because the robot is waiting for the start signal and is in the state of being about to move. In this case, the robot should also be considered to be in motion. Do not approach the robot.

### 1.5 Emergency

#### 1.5.1 Emergency stop switch

After you press the emergency stop switch in emergencies, the robot will immediately stop all motions and be locked. According to IEC 60204-1 and ISO 13850, the emergency stop switch is not a safeguard. It is a complimentary protective measure and not intended to prevent injury.

#### 1.5.2 Emergency recovery

The emergency stop switch will be locked after you press it. To unlock the switch, you need to rotate the switch according to the mark on the switch. The alarm can be cleared through the software only after the emergency stop switch is unlocked. Then the robot arm can be enabled and resumed from the emergency status.

**WARNING**

Please operate the robot to recover from the emergency only after the danger of the robot system is completely removed.

## 2. Transportation

You need to transport the robot in its packing posture (set in the control software in reference to the control software user guide for details), and use the original packaging for transportation. During transportation, ensure that the robot arm is stable and fixed by corresponding measures. During transportation and long-term storage, ensure that the ambient temperature ranges from -20 °C to +70 °C, and the ambient humidity is no more than 85% without condensation. When moving the robot from its packaging to the installation space, hold the robot arm in place until all mounting bolts are securely tightened at the base of the robot. After transportation, store the original package in a dry place for repacking and transporting it in the future.

**WARNING**

* Ensure that the operator is not unduly stressed on their back or other body parts when lifting the equipment, and use appropriate lifting equipment if necessary.
* Dobot shall not be held responsible for any damage caused by transportation of the equipment.
* Be sure to follow all installation instructions when installing the robot.

## 3. Product Introduction

### 3.1 Overview

The main components of the robot system include:

_Figure 3.1 Robot system_

Magician E6 robot: six-axis robot, integrated design, with the controller inside the base. Emergency stop switch: connected to the robot base to realize the emergency stop function. In addition, the system includes an operating terminal (tablet or PC) for installing the robot control software, which is connected to the robot via a network cable (standard) or a WiFi module (self-prepared, plugged into the robot USB interface).

_Figure 3.1 Operating terminal_

### 3.2 Composition

Magician E6 robot, as shown in Figure 3.2, includes a base, 6 rotating motion joints, and two connecting rods (upper arm and forearm), with an aviation socket on the side of its end flange.

![Figure 3.1 Robot system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnJbQeMsxwGsQzczcE1Jn%2Fmagician-e6-p013-img01.jpg?alt=media)

![Figure 3.1 Operating terminal](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhZ2cZuYW2VNOiHch5du7%2Fmagician-e6-p013-img02.jpg?alt=media)

_Figure 3.2 Magician E6_

### 3.3 Indicator light and buttons

The Magician E6 robot is equipped with a circle of status indicators near the J1 and J6 joints, with the meanings described below:

_Table 3.1 Indicator lightS_

Color Status Definition Blue light Steady on The robot arm has been started but not enabled Quick flash The robot arm is starting. Green light Steady on The robot arm is enabled (not running) Slow flash Automatic running status (project debugging/running/pause, TCP motion commands except jog, trajectory playback) Quick flash Single running status (jog/runto in software)/drag mode/ trajectory recording status Red light Slow flash Joint brake switched on in disabled status Steady on Alarm status Yellow light Steady on Collision detected

**NOTE**

The quick flash frequency is 5Hz, and slow flash frequency is 1.25Hz.

![Figure 3.2 Magician E6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjL4HuOriIdocf1kKuAfB%2Fmagician-e6-p014-img01.png?alt=media)

There are multiple buttons at the end and base, as shown in Figure 3.3.

_Figure 3.3 Button position_

* : Power switch. Short-press (in 0.5s) to switch on; Long press for 1.5s in power-on state, the indicator light will flash red fast, and then release the button to turn off the power.
* : Run/stop button. When the robot is enabled and idle, long press to start running;

when the robot is running, short-press to stop running. You can configure the functions (trajectory playback by default) of the button in DobotStudio Pro. ◦ Trajectory playback: Play back the last trajectory recorded by at the original speed. ◦ Run project: configure the project to be run via DobotStudio Pro. After the configuration is completed, you can run the project directly via this button, with no need to connect to the operating terminal. Powering off the robot will not clear the configuration.

* : Enabling button. When the robot arm is not enabled, long-press the button to enable the robot. When the robot arm is enabled and idle, short-press the button to disable the robot.
* : Hand-guiding button. When the robot arm is enabled and idle, long-press the button and the robot arm will enter the drag mode. Long-press the button again in the drag mode, and the robot arm will enter the trajectory recording mode. Short-press the button, and the robot arm will exit the drag mode and stop trajectory recording.

![Figure 3.3 Button position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ8Ngdv9yyNzFXXxZvYiN%2Fmagician-e6-p015-img01.jpg?alt=media)

* : Tool control button. When the robot is disabled, enabled and idle or in the drag mode, short-pressing the button can switch the status of the specified tool DO for controlling the end tool. You can configure the tool DO via the tool IO plug-in in DobotStudio Pro.

**NOTE**

* Except for the power button, pressing a button and releasing it within 1.5s is a short press, and more than 1.5s is a long press.
* Some of the button functions are affected by the manual/automatic mode of the controller. See the instructions on mode switch in the DobotStudio Pro user guide for details.

### 3.4 Operating terminal

The Magician E6 robot supports control through PC and App, as shown in Table 3.2.

_Table 3.2 Operating terminal parameters_

Terminal type PC Tablet (Android) iPad Operation Windows7/10/11 64-bit Android 10 and above iOS 10 and above system Control software DobotStudio Pro (V4.0 and above) Minimum CPU: Intel Core i3 CPU: 4-core iPad 5 and above configuration Memory: 4G Running memory: 2G Storage space: 128GB Storage space: 32G Network card: Gigabit- Screen: 8-inch NIC Display memory: 1G Communication LAN/WiFi WiFi WiFi mode When purchasing Magician E6 robot arms, you can ask for matching Android tablets; or use self-prepared operating terminal which is consistent with or higher than the recommended configuration in Table 3.2.

## 4. Product Features

### 4.1 Coordinate system

#### 4.1.1 Joint coordinate system

The joint coordinate system is determined based on all motion joints. All joints are rotating joints, as shown in Figure 4.1.

_Figure 4.1 Joint coordinate system_

#### 4.1.2 User coordinate system

The user coordinate system is a custom workpiece or workbench coordinate system. The origin and the orientations of axes can be defined based on the site requirement to measure the points within the workspace and arrange tasks conveniently. The origin of the default user coordinate system is the intersection of the J1 axis with the lower surface of robot base. Y+ direction faces the shorter side of the base, as shown in Figure 4.2.

![Figure 4.1 Joint coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fkpj9ivs23AiRKzYjMFWa%2Fmagician-e6-p017-img01.png?alt=media)

_Figure 4.2 User coordinate system_

#### 4.1.3 Tool coordinate system

The tool coordinate system defines the tool center point (TCP) and tool posture, of which the origin and orientations vary with the position and angle of the workpiece at the end of robot. The default tool coordinate system is determined based on the center point of the end flange. The Y+ direction is the opposite direction of the aviation socket, as shown in Figure 4.3.

_Figure 4.3 Tool coordinate system_

![Figure 4.2 User coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHouJcrVyCbVMJ4feDAvN%2Fmagician-e6-p018-img01.png?alt=media)

![Figure 4.3 Tool coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FF5CnbJtD2MhWpcOzSVpI%2Fmagician-e6-p018-img02.png?alt=media)

### 4.2 Home posture

When the robot arm is in the vertical state shown in Figure 4.4, the angle of each joint is 0 degree. This posture is called the home posture. There is a home-point score at each joint of the robot (red line shown below). The scores on both sides of the joint will align when the robot is in the home posture. If the home posture of the robot arm changes due to the replacement of the transmission parts or collision, you can move the robot arm to a state where the scores of each joint are aligned. Then calibrate the home posture through the control software.

_Figure 4.4 Home posture score_

### 4.3 Singularity point

#### 4.3.1 Shoulder singularity

When the intersection of the J5 axis and the J6 axis of the robot arm is located in the plane formed by the J1 axis and the J2 axis, it will lead to singularity, as shown in Figure 4.5.

![Figure 4.4 Home posture score](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1rLxRDOJi3nvqKfY3hyw%2Fmagician-e6-p019-img01.jpg?alt=media)

![Figure 4.5 Shoulder singularity](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKxGjsLr8R8wcyF68i4Vl%2Fmagician-e6-p019-img02.jpg?alt=media)

#### 4.3.2 Elbow singularity

When the upper arm and forearm are in the same line, it will lead to singularity. When the intersection of the J5 axis and the J6 axis of the robot arm is located in the plane formed by the J1 axis and the J2 axis, it will lead to singularity,

_Figure 4.6 Elbow singularity_

#### 4.3.3 Wrist singularity

When the J4 axis and J6 axis are parallel, it will lead to singularity, as shown in Figure 4.7.

_Figure 4.7 Wrist singularity_

![Figure 4.6 Elbow singularity](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIm6zPMjak0fAhWn9zlX2%2Fmagician-e6-p020-img01.jpg?alt=media)

![Figure 4.7 Wrist singularity](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fy64FjPNhILjZxyQuPifZ%2Fmagician-e6-p020-img02.jpg?alt=media)

## 5. Mechanical Specifications

All dimensions in this chapter are in millimeters (mm).

### 5.1 Dimensions and working space

When selecting the installation position for the robot, you must consider the cylindrical space directly over and under the robot, and try to avoid moving the tool to the cylindrical space. Because this will cause the joints to rotate too fast while the tool moves slowly, resulting in low working efficiency of the robot and difficult risk assessment.

![Figure 5.1 Dimensions and working space](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw0sypmAaBwGw8TYC1bgw%2Fmagician-e6-p021-img01.png?alt=media)

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbqTbF01NQEeLHeWdQvyc%2Fmagician-e6-p021-img02.png?alt=media)

### 5.2 Base installation dimensions

_Figure 5.2 Base installation dimensions_

### 5.3 Base plate dimensions

The thickness of the installation board is 6 mm.

_Figure 5.3 Base board dimensions_

![Figure 5.2 Base installation dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6gslKfl5lo2mWA89GYJJ%2Fmagician-e6-p022-img01.png?alt=media)

![Figure 5.3 Base board dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdBblvT2co6Rou3dzzq8S%2Fmagician-e6-p022-img02.png?alt=media)

### 5.4 Flange dimensions

_Figure 5.4 End flange dimensions_

### 5.5 Load curve

The figure below shows the load curve of Magician E6 when it is installed normally. The horizontal axis represents the distance from the center of mass of the load to the center of the end flange of Magician E6 (eccentric distance), unit: mm. The vertical axis represents the load weight, unit: g. The blue line represents the maximum load of Magician E6 at each eccentric distance. When the eccentric distance is less than 60mm, the maximum load of Magician E6 is 750g. When the eccentric distance is greater than 60mm, the maximum load of Magician E6 decreases as the distance increases.

![Figure 5.4 End flange dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0joOShDFvNkl7DzO3PBR%2Fmagician-e6-p023-img01.png?alt=media)

_Figure 5.5 End load curve_

![Figure 5.5 End load curve](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fr8jvUFTqQMcVsi8SA2jV%2Fmagician-e6-p024-img01.jpg?alt=media)

## 6. Electrical Features

### 6.1 Base interface

#### 6.1.1 Overview

The base interface panel is shown below. No. Description 1 Emergency stop switch interface For connecting emergency stop switch. See 6.1.2Emergency stop switch interface. 2 Digital I/O interface Universal DI/DO. See 6.1.3Digital I/O interface. 3 Power interface For connecting matched power adapter 4 Encoder interface For connecting conveyor for dynamic tracking. See 6.1.4Encoder interface. 5 USB interface For connecting WiFi module or importing/exporting files 6 LAN interface, default address: LAN1: 192.168.5.1

*

LAN2: 192.168.200.1

*

For connecting to PC, or other external network equipment of TCP/IP or Modbus TCP protocol Only LAN1 IP address can be modified through DobotStudio Pro.

![Official manual figure, page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3t7KVNxJlLXmowKlKrPo%2Fmagician-e6-p025-img01.png?alt=media)

#### 6.1.2 Emergency stop switch interface

The emergency stop switch is included in the shipping accessories, which has been connected to the wiring terminals. You just need to plug it into the corresponding interface. If you use a self-prepared emergency stop switch, please wire as below.

_Figure 6.1 Connect to one or multiple emergency stop switches_

#### 6.1.3 Digital I/O interface

The digital I/O interfaces at the rear of the base include 16 universal DOs (500mA maximum single output current), 16 universal DIs, 2 24V power supplies and 2 GNDs, with a total current load capacity of 2A. DI and DO are both PNP type. The wiring of DI connected to a simple switch is shown below.

_Figure 6.2 DI connected to simple switch_

The wiring of DI connected to external PNP-type 3-wire sensor is shown below.

![Figure 6.1 Connect to one or multiple emergency stop switches](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fl1Jti6ncs3fWkKSfh2ZA%2Fmagician-e6-p026-img01.png?alt=media)

![Figure 6.2 DI connected to simple switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F48nRSUYH4GIUG4RSnIfv%2Fmagician-e6-p026-img02.png?alt=media)

![Figure 6.3 DI connected to sensor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fk4CEZT94nqXYPJGfBN4e%2Fmagician-e6-p026-img03.png?alt=media)

The wiring of DO connected to external load is shown below.

_Figure 6.4 DO connected to external load_

#### 6.1.4 Encoder interface

The socket pins of the encoder interface are distributed and defined as follows. Pin Name Definition 1 En\_A+ 2 En\_A- 3 En\_B+ ABZ encoder data interface 4 En\_B- 5 En\_Z+ 6 En\_Z- 7 EX\_5VDC 5V output 8 GND Ground 9-Reserved

### 6.2 Tool I/O interface

The tool interface is an aviation socket located on the side of the end flange. The socket pins

![Figure 6.4 DO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHTZUxzLPdzc0JdjhbAk6%2Fmagician-e6-p027-img01.png?alt=media)

are distributed and defined as follows. The tool digital inputs and digital outputs are PNP type.

**WARNING**

When connecting end tools, ensure that power interruptions do not cause any hazards, such as a workpiece falling off the tool. Pin Name Definition 1 24V 24V output 2 DO\_1 Digital output 1 3 DO\_2 Digital output 2 4 DI\_1 Digital input 1 5 DI\_2 Digital input 2 6 GND Ground

![Official manual figure, page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAYbvH9tm7hObfN7PFS0Q%2Fmagician-e6-p028-img01.png?alt=media)

## 7. Installation and Use

### 7.1 Installation environment

To maintain the performance of the robot and ensure safe use, please place the robot in an environment with the following conditions.

**NOTICE**

Please make sure that the installation environment meets the following conditions to avoid damage.

* Install indoors with good ventilation.
* Keep away from excessive vibration and shock.
* Keep away from direct sunlight.
* Keep away from dust, oily smoke, salinity, metal powder, corrosive gases and other contaminants.
* Do not use in a closed environment. A closed environment may cause high temperature of the robot and shorten its service life.
* Keep away from flammable.
* Keep away from cutting and grinding fluids.
* Keep away from sources of electromagnetic interference, such as large transformer, large electromagnetic contactor, electric welding machine, etc.
* When the robot is transported, ensure that the robot is stable and kept in proper place.
* When the robot is hoisted, be sure to take appropriate measures to locate the moving parts so as not to cause accidental movement and harm during hoisting and transportation.
* When moving the robot from the packing box to the mounting position, hold the robot until all bolts on the robot base are fastened.
* When the robot is installed, take corresponding measures to locate it. Be sure to use 6 hex bolts M4 (length ≥ 10 mm, ISO898-1: 2013, property class: 12.9) to fix and tighten the robot base.
* When the robot is installed on the wall, be sure to take the anti-fall measures of the robot base.
* When the robot is installed, fix the robot on a sufficiently strong base, which needs to be able to fully withstand the reaction force of the robot acceleration and deceleration and the static weight of the robot and the workpiece.

### 7.2 Unpacking

When unpacking, please check the attached shipping list to ensure that all contents are included. If there is anything missing, please contact your supplier.

### 7.3 Robot installation

#### 7.3.1 Robot installation

Dobot Magician E6 robot supports both standard and side mounting. Here shows several typical mounting positions.

**NOTE**

The installation posture in the middle of the figure is the standard mounting angle. When installing the robot in a non-standard mounting angle, you need to calibrate the mounting angle through the software after powering on the robot arm, See the user guide of the control software for details.

_Figure 7.1 E6 installation posture_

The installation platform of the robot arm should be stable enough to withstand at least 10 times the maximum torque of the J1 joint, and at least 5 times the weight of the robot arm. If the robot arm is installed on a linear axis or a moving platform, the acceleration of the platform should be low. High acceleration may trigger the collision detection mechanism of robot arm and cause the robot arm to stop. When installing the robot arm, position the mounting holes on the installation platform according to the installation size of the robot base. Fix the robot arm base on the platform using bolts. For the specific dimensions of the robot base, refer to 5.2Base installation dimensions.

![Figure 7.1 E6 installation posture](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fizn7RiSmju7Kn3qIfJLq%2Fmagician-e6-p030-img01.jpg?alt=media)

_Figure 7.2 E6 installation steps_

You can also fix the robot on the base plate, and fix the base plate on the installation platform using M4 screws or G-type cramps (maximum clip distance: 55 cm). You can refer to 5.3Base plate dimensions for the specific dimensions of the base plate. The G-clamp is recommended to be fixed diagonally, as shown below.

_Figure 7.3 G-type cramp_

#### 7.3.2 Tool installation

The end flange of the robot arm has four M6 threaded holes, which can fix the tool to the end of the robot arm. In order to accurately adjust the position of the tool, you can also use the reserved Φ6 positioning hole, and position it using pins. For specific dimensions, refer to 5.4Flange dimensions.

![Figure 7.2 E6 installation steps](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYr1oV2FcOz9RbYlvQ713%2Fmagician-e6-p031-img01.png?alt=media)

![Figure 7.3 G-type cramp](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F44noBqqLiW2V5r22eILq%2Fmagician-e6-p031-img02.png?alt=media)

### 7.4 Wiring

_Figure 7.4 Wiring diagram_

1. Plug the emergency stop switch cable into the emergency stop switch interface.
2. Plug one end of the power cable into the power interface and the other end into the

corresponding external power supply.

**NOTICE**

* Set the specifications and installation method of external cables in compliance with local power distribution laws and regulations.
* Do not disassemble the robot by yourself, otherwise it may cause electricity leakage.
* Make sure the device is grounded.
* Do not bend the cable excessively, otherwise it may cause poor contact or cable breakage.
* Make sure the power outlet for the control system is disconnected when connecting an external device, otherwise it may cause an electric shock or device failure.
* Use supporting cables to protect device and personal safety.
* After wiring, ensure that there are no fallen screws or exposed cables in the device.
* Do not plug or remove the power cable or communication cable when the device is running normally.
* Power on the device only after connecting all the cables required.
* Ensure that the cables are connected correctly, otherwise, it may cause fault in internal modules or external devices.
* Before connecting, check whether there is breakage in the insulation and shield of the external cables.

![Figure 7.4 Wiring diagram](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK6M6Yymtkuef0RHwnnLL%2Fmagician-e6-p032-img01.png?alt=media)

### 7.5 Debugging

After turning on the external power supply, short-press the power switch. When the indicator lights of the robot arm turn blue, you can connect the robot arm, enable and jog it for debugging through the operation terminal. For specific operations, refer to the control software user guide.

## 8. Maintenance

Maintenance and repairing must be performed in compliance with all safety instructions in this manual. The purpose of maintenance and repairing is to ensure that the system is kept operational, or to return the system to an operational state in the event of a fault. Repairing includes troubleshooting in addition to the actual repair itself. Repairing must be performed by an authorized system integrator or Dobot staff. Robots or parts returned to Dobot should follow the instructions below:

* Remove all parts that do not belong to Dobot.
* Before returning to Dobot, please make a backup copy of the files. Dobot will not be responsible for the loss of programs, data or files stored in robot.
* The robot should move to the package point before returning to Dobot.

### 8.1 Safety instructions

The following safety procedures and warnings must be observed during the operation of the robot or controller:

**NOTICE**

* Replace faulty components using new components with the same model or equivalent components approved by Dobot.
* Reactivate all deactivated safety measures immediately after the repairing is completed.
* Record all repairs and save them in the technical document with the robot system.
* Remove the main input cables from the back of the controller to ensure that it is completely unpowered. Cut off any other power source connected to the robot or controller. Take necessary precautions to prevent other people from powering on the system during the repair period.
* Observe ESD regulations during the disassembly of the parts of the robot arm or controller.
* Avoid disassembling the power supply inside the controller. High voltage may remain inside the power supply for several hours after the controller has been powered off.
* Prevent water and dust from entering the robot arm or controller.

### 8.2 Robot maintenance

In order for the robot to maintain high performance for a long time, a maintenance inspection must be carried out. The personnel in charge of the maintenance must prepare a maintenance plan and carry out the maintenance. The maintenance items are shown below.

_Table 8.1 Check items_

Period

## Maintenance

Maintenance essential item Daily 3 months 6 months Wipe off dirt, dust, cutting residue on √ Robot clean the body with water or 10% alcohol Check the torque of exposed bolts √ Joint bolts based on the specified tightening torque table Tool mounting Check the torque based on the specified √ tightening torque table bolts √ Motor Confirm abnormal heating or sound Check whether the robot arm or end- √ Brake effector will fall when the servo is powered off Check abnormal vibration, noise, and √ Reducer oil leakage The screw tightening torque is shown in Table 8.2.

_Table 8.2 screw tightening torque_

Screw size Inner hexagonal screw Cross recessed screw 2 mm / 0.079 in 0.4 Nm 0.4 Nm 2.5 mm / 0.099 in 1 Nm - 3 mm / 0.118 in 2 Nm - 4 mm / 0.157 in 4 Nm - The tightening torques vary depending on the types of base metal or screws. When it is not specified, please contact Dobot technical support engineers.

## 9. Warranty

### 9.1 Product warranty

Without prejudice to any claim agreement that the user (customer) may reach with the distributor or retailer, the manufacturer shall guarantee the quality of the products to the customer in accordance with the terms and conditions below: If defects caused by manufacturing and/or improper material occur in a new device and its components within 12 months (15 months at most if the shipping time is included) after the device is put into use, Dobot shall provide the necessary spare part, and the user (customer) shall offer personnel to replace the spare part, using another part that represents the latest technology level to replace or repairing the related part. If the device defects are caused by improper handling and/or failure to follow the relevant information set out in the User Guide, the warranty is invalid. This warranty does not apply to or extend to maintenance (e.g. installation, configuration, software download) performed by the authorized distributer or customer. The user (customer) must provide the purchase receipt and the purchase date as valid evidence for the warranty. Claims under this warranty must be made within two months of the apparent failure to perform the product warranty. The ownership of the equipment or components that are replaced or returned to Dobot shall remain with Dobot. Any other claims arising from or related to the equipment are not covered by this warranty. Any items in this product warranty do not intend to limit or exclude the legal rights of the customer or to limit or exclude the liability of the manufacturer for the personnel casualty resulting from its negligence. The duration of this product warranty shall not be extended due to the services provided under the product warranty terms. Under the principle of not violating the warranty, Dobot reserves the right to charge customers for the replacement or maintenance. The foregoing does not imply a change in the burden of proof to the detriment of the client. If there are defects on the equipment, Dobot shall not be liable for any damage or loss arising therefrom, including but not limited to loss of production or damage to other production equipment.

### 9.2 Disclaimer

Dobot is committed to improve the reliability and performance of its products, and as such reserves the right to upgrade products without prior notice. Dobot strives to ensure the contents of the User Guide are precise and reliable, but takes no responsibility for any errors or missing information.

## Appendix Technical Specifications

Parameter Value Weight 7.2kg Freedom degree 6 Maximum load 750g Maximum working radius 450mm Repeatability ±0.1mm Maximum tool speed 0.5m/s J1 ±360° J2 ±135° J3 ±154° Joint working range J4 ±160° J5 ±173° J6 ±360° Maximum joint speed (J1-J6) 120°/s Power input 100V – 240V AC, 50/60 Hz Nominal voltage 48V DC, 5A Nominal power 130W Ethernet 2, for TCP/IP and Modbus TCP communication Communication interface USB 1, for connecting WiFi module Tool D&#x49;_&#x32;, D&#x4F;_&#x32;, 24&#x56;_&#x31;, GN&#x44;_&#x31; IO interface Base D&#x49;_&#x31;6, D&#x4F;_&#x31;6, 24&#x56;_&#x34;, GN&#x44;_&#x34; IO output 24V, total output: 2A, maximum 0.5A for each External interface Emergency stop, ABZ encoder interface, power interfac&#x65;_&#x31; Control software DobotStudio Pro IP rating IP20 Base dimensions 16&#x32;_&#x31;20\*103mm Working environment Temperature: 0℃ – 50℃ Humidity: 25% – 85%, no condensation Noise 60dB(A)

Installation method Floor mounting Material Aluminum alloy, ABS
