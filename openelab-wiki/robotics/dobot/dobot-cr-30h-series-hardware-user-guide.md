---
description: >-
  Hardware guide for DOBOT CR 30H and CR 30HT collaborative robots, covering
  safety, specifications, interfaces, installation, maintenance, and
  stop-distance data.
---

# DOBOT CR 30H Series Hardware User Guide

## DOBOT CR30H/CR30HT Heavy-Payload Collaborative Robot

{% embed url="https://openelab.io/products/dobot-cr30h-heavy-payload-cobot" %}

## Contents

* Preface
* 1\. Safety
* 2\. Product Introduction
* 3\. Product Features
* 4\. Mechanical Specifications
* 5\. Electrical Characteristics
* 6\. Transportation
* 7\. Installation and Use
* 8\. Maintenance
* 9\. Disposal and Environmental Protection
* 10\. Warranty
* Appendix A Technical Specifications
* Appendix B Emergency Stop Time and Distance
* Appendix C Normal Stop Time and Distance

Copyright © SHENZHEN DOBOT CORP LTD 2025-2026. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as "DOBOT"). Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. DOBOT makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will DOBOT be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. DOBOT shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot.

### SHENZHEN DOBOT CORP LTD

Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

### DOBOT Europe GmbH

Address: Waldeckerstraße 11 64546 Mörfelden-Walldorf, Contact: Lang Xulin, lang@dobot-robots.com

## Preface

This document describes the functions, technical specifications, installation guide of DOBOT CR 30H series collaborative robot, making it easy for users to fully understand and use it.

### Scope of application

Robot arm:

* DOBOT CR 30H
* DOBOT CR 30HT
* DOBOT CR 30H-Food

You can find the model of robot arm on the right-top corner of the nameplate on the robot base. The figure below takes CR 30H as an example. Controller:

* DOBOT CC365

You can find the controller information on the nameplate. The figure below takes CC262 as an example.

![Official manual figure, page 3](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeH4SgCt4nOBBcIoQpAXr%2Fcr30h-p003-img01.png?alt=media)

![Official manual figure, page 3](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFeJ6ZVsrpFHb3yOTsoPZ%2Fcr30h-p003-img02.png?alt=media)

### Important safety notice

The robot is a semi-finished machinery, so a risk assessment must be conducted after each installation. Please strictly adhere to all safety regulations outlined in Chapter 1.

### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

### Related documents

Document Description Download link DobotStudio Pro User Explains how to use the robot Guide control software, DobotStudio Pro. Describes how to use the secondary development interface based on DOBOT TCP\_IP Remote TCP/IP protocol. In addition to the Control Interface Guide document, you can also access multi-language development DEMOs from Github. Download Center DOBOT Bus Introduces the usage of the robot's Communication Protocol bus communication functions Guide (EtherNetIP/Profinet). (EtherNetIP\_Profinet) Explains how to use the Teach DOBOT Cobot Teach Pendant that accompanies the Pendant User Guide collaborative robot.

### Revision history

Date Version Revised content 2026/06/11 V1.3 Revised the tool I/O interface description

* The control software version of CR 30H has been upgraded to 4.7 or above. 2026/01/19 V1.2
* Added instructions for the fixing screws and hole positions of the CR 30H base mounting dimensions. 2025/10/30 V1.1 Revised the CR 30H end load curve 2025-09-16 V1.0 The first release

### Symbol conventions

The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided,

**DANGER**

could result in death or serious injury. Indicates a hazard with a medium level or low level of risk which, if

**WARNING not avoided, could result in minor or moderate injury, robot arm**

damage. Indicates a potentially hazardous situation which, if not avoided,

**NOTICE**

could result in robot arm damage, data loss, or unanticipated result. Provides additional information to emphasize or supplement

**NOTE**

important points in the main text.

### How to use this guide

Reference Phase Description section Before installing and using the robot, read the Safety Learning safety section thoroughly and strictly follow the Safety safety guidelines provided. Product Introduction Product Understand the components, features, and Product Features Understanding detailed technical specifications of the product. Appendix Technical Specifications

Reference Phase Description section Space planning: Understand the mechanical specifications and installation environment Mechanical requirements of the robot arm and controller, Specifications and plan the installation space by considering Installation the end tool's mechanical specifications and environment installation method. Electrical planning: Read the relevant sections to understand the function and location of the Electrical robot's electrical interfaces, and plan the Features electrical connections and wiring. Planning Transport the robot arm and controller to their Transportation respective installation locations. Mechanical Install the robot arm, controller, and end tools in Specifications place. Robot installation Electrical Connect to the robot. Features Cable connection Power-on and Power on the robot, then refer to DobotStudio Power-on and Use Pro User Guide to configure and use the robot. debugging Perform routine maintenance and care of the Maintenance robot while strictly following the safety Maintenance instructions. Disposal and Follow the instructions in this document for Disposal Environmental deactivating and disposing of the robot. Protection

## 1. Safety

### 1.1 Responsibility

#### 1.1.1 Responsibility and norms

The information in this document does not cover designing, installing and operating a complete robot system, nor does it cover all peripheral equipment that may affect the safety of the complete system. The complete system must be designed and installed in accordance with the safety requirements set forth in the standards and regulations of the country where the robot is installed. The integrators of DOBOT are responsible for ensuring that the applicable safety laws and regulations in the country concerned are observed and that any significant hazards in the complete robot application are eliminated. This includes, but is not limited to:

* Performing a risk assessment for the complete robot system.
* Adding safety machines and mechanisms based on the risk assessment, including but not limited to building a proper safety circuit to achieve safe stop.
* Setting up the appropriate safety settings in the software.
* Ensuring that the user will not modify any safety measures.
* Validating that the total robot system is designed and installed correctly.
* Specifying instructions for use.
* Marking relevant signs and contact information of the integrators on the robot.
* Archiving relevant technical files.

#### 1.1.2 Limitation of liability

Any safety information provided in this document should not be considered as a warranty from DOBOT. The robot may cause injury or damage even if all safety instructions are observed.

### 1.2 Intended use

DOBOT CR 30H series robots are high-payload collaborative robots only for general industrial use, such as processing or delivering products or parts through end tools. DOBOT CR 30H series robots are equipped with special safety mechanisms including collision detection. These mechanisms are purposely designed for human-robot collaboration, but only intended for non-hazardous applications after risk assessment, where tools, products, environment and other machines have been demonstrated to be incapable of significant risk through application-specific risk assessments. Any use or application deviating from intended use is deemed to be impermissible misuse, including, but is not limited to:

* Use in potentially explosive environments.
* Use in vacuum environments.
* Use for transporting people or animals.
* Use in life-critical applications.
* Use before performing a risk assessment.
* Use over-stated specifications.
* Use as a climbing aid.

### 1.3 Risk assessment

As the robot is a semi-finished machinery, the integrator is responsible for conducting a risk assessment of the overall system after integration. It is recommended that integrators perform a risk assessment based on ISO 12100 and ISO 10218-2 and refer to the Technical Specification ISO/TS 15066 for integration guidance. The risk assessment should consider all workflows during the robot’s entire lifecycle, including but not limited to:

* Teaching the robot during the setup and development process.
* Maintenance and repairs.
* Robot installation.

The risk assessment must be completed before the robot is powered on for the first time, including but not limited to confirming the safety function settings and evaluating whether additional emergency stop buttons or other protective measures are required. When performing the risk assessment, the integrator should focus on the following safety functions:

* Collision detection sensitivity settings: Limiting the force applied during a collision between the robot and the operator.
* Robot and tool pose limitations: Reducing the risk of the robot and tools colliding with the operator, especially in specific body areas such as the head and neck.
* Speed limit: Limiting the robot’s operating speed to reduce safety risks.

The integrator must set permissions and passwords to prevent unauthorized personnel from modifying the safety function configurations. When conducting a risk assessment for collaborative robot applications, the integrator must consider potential collision risks caused by human error, including:

* The severity of potential collisions.
* The probability of potential collisions.
* The likelihood of avoiding potential collisions.

If the robot is installed in a non-collaborative application where its built-in safety functions cannot effectively eliminate safety risks (e.g., using hazardous tools), the integrator must consider adding additional protective measures (e.g., safety barriers or safety lasers) during the risk assessment. The integrator must consider potential risks including but not limited to:

1. Cuts from sharp edges and points on the end tools or end effector connectors.
2. Cuts from sharp edges and points on obstacles in or near the robot’s workspace.
3. Scrapes caused by contact with the robot.
4. Sprains or fractures resulting from collisions between heavy payloads on the

robot’s end and hard surfaces.

5. Consequences of loose bolts securing the robot or end tool.
6. Consequences of items falling off the end tool.
7. Consequences of incorrectly pressing the emergency stop button of other

equipment.

8. Consequences of unauthorized changes to the safety function configurations.

For information on emergency stop time and distance, please refer to the Emergency stop time and distance section.

### 1.4 Pre-use assessment

Before using the robot for the first time or after any modifications are made, testing must be conducted to ensure that all safety inputs and outputs are correctly connected and functioning properly:

1. Test whether the emergency stop button and user emergency stop input can

trigger an emergency stop.

2. Test whether the protective stop input can halt the robot’s motion. If a protective

stop reset input is configured, test whether this input must be activated before the robot can resume operation.

3. If a reduced mode input is configured, test whether this input can switch the robot

to reduced mode (reduced-speed operation).

4. If a teach pendant is optionally configured with a three-position switch for enabling

functionality, test whether the robot can only be enabled when the three-position switch is in the center position in manual mode.

5. Test whether the system connected to the emergency stop status output can

detect the output change and respond accordingly.

6. If other safety outputs are configured, test whether the system connected to the

corresponding output can detect the output change and respond accordingly.

### 1.5 Safety warning sign

The following safety warning signs may appear on the product, and their meanings are as follows: Sign Description Indicates a high potential hazard that, if not avoided, could

**DANGER result in death or serious injury.**

Indicates a potentially dangerous electrical situation that, if not avoided, could result in injury, death, or serious damage to the ELECTRICITY equipment. HOT Indicates a potentially dangerous hot surface that, if touched, could result in personnel injury.

Sign Description Indicates a moderate or low potential hazard that, if not avoided, could result in minor personal injury and damage to

**WARNING**

the equipment. Indicates a potential risk that, if ignored, could result in robot

**NOTICE arm damage, data loss, or unpredictable result.**

Indicates a situation that, if not avoided, could result in personnel injury or damage to the equipment. CAUTION For items marked with such signs, depending on the specific situation, there is sometimes a possibility of significant consequences

### 1.6 General safety

Follow the safety instructions below when starting and using the robot for the first time.

**DANGER**

* The robot control system is an electrically powered device. Non-professionals should not modify the circuit, otherwise, it may result in robot damage or personal injury.
* Strictly comply with local laws and regulations when operating the robot. The safety precautions described in this document serve only as a supplement to local safety standards.
* Use the robot within the specified environmental conditions. Operating beyond the rated specifications and load conditions may shorten the robot's lifespan or even damage it.
* Ensure that the robot is operated under safe conditions and there is no harmful object around the robot.
* Avoid frequently powering the robot on and off, as this may degrade the performance of the main circuit components inside. If repeated power cycling is necessary, limit it to no more than once per minute. HOT The robot and controller generate heat during operation. Do not operate or touch the robot while it is running or immediately after it stops.
* Turn off the power and wait one hour for the robot to cool down.
* Do not place your fingers on the heat generating area of the controller.

**NOTICE**

* Personnel responsible for installing, operating, and maintaining the equipment must undergo rigorous training, fully understand all safety precautions, and master proper operation and maintenance procedures before handling the equipment.
* Unauthorized personnel without professional training must not disassemble or repair the equipment. In case of a malfunction, contact DOBOT's technical support engineer in time.
* Perform daily inspections and periodic maintenance, replacing faulty components promptly to ensure the safe operation of the equipment.
* If the equipment is scrapped, please comply with the relevant laws for the proper disposal of industrial waste to protect the environment.
* Establish safety measures (e.g., fences, ropes, or warning lines) near the robot’s operating area to ensure that personnel stay out of the robot's reach while it is in operation or about to start.
* Do not enter the robot’s safety zone defined by the risk assessment or touch the robot while the system is running.
* Do not expose the robot to a permanent magnetic field, as strong magnetic fields can cause damage.
* DOBOT assumes no responsibility for robot damage or personal injury caused by improper operation or failure to follow the product’s instructions for use.
* Handling operations using lifting rings, cranes, or similar equipment must be conducted using appropriate and reliable lifting devices, and must be carried out by qualified personnel or those authorized by the company in accordance with local regulations.
* Make sure that there are no obstacles within 2 meters of the robot during the transportation, and personnel should stay away from the suspended robot.
* DOBOT is not responsible for any damage caused during the transportation and handling of the equipment.
* Make sure that the robot is in the packing posture before packaging, and the brakes on each axis are normal.
* Make sure that the packing area is free of obstacles to allow staff to evacuate quickly in case of emergencies.
* Secure the packaging firmly during transport to keep the robot stable.
* After removing the outer packaging, make sure that the robot maintains its original packing posture and the brakes on each axis are normal.
* Make sure that the packing and unpacking areas are free of obstacles to allow staff to evacuate quickly in case of emergencies.
* During debugging, make sure that no personnel or other equipment (including computer used for debugging) is present in the hazardous area of the machine.
* Wear appropriate personal protective equipment when necessary, such as safety helmets, safety shoes (with non-slip soles), face shields, safety goggles, and gloves. Inappropriate clothing may cause personal injury.

**NOTICE**

* Do not enter the robot’s workspace while the robot is operating, as this may result in injury to the robot or operator.
* If an abnormality occurs with the robot, ensure that the system is stopped before conducting an inspection.
* After debugging, operators must first test the system in manual mode. Once this is confirmed to be correct, switch to automatic operation.
* All suspended safety configurations should be restored to their full functionality before selecting the automatic operation mode.
* If the controller needs to be restarted due to a power failure, the robot must be manually returned to the initial position of the automatic operation program before restarting automatic operation.
* Before performing maintenance, inspection, or wiring work, the power supply must be completely cut off, and a "No power supply" sign must be posted. Failure to do so may result in electric shock or personal injury.
* Observe ESD (Electrostatic Discharge) regulations when disassembling the robot or controller.
* Avoid disassembling the power supply system inside the controller. Even after the controller is turned off, high voltage may remain for several hours.
* For disassembly and repair of the robot, contact DOBOT's technical support engineer.
* Maintenance and repair work must be carried out by designated personnel, otherwise electric shock or personal injury may result.
* If the brake is manually released, the robot may move due to gravity.

Therefore, when manually releasing the brake, ensure proper support for the robot and any attached tools or workpieces.

* If the power supply must be turned on while the controller door is open for maintenance or inspection, avoid direct exposure of the controller interior to strong light sources such as sunlight or spotlights, as this may cause malfunctions or errors.
* To prevent electric shock, turn off the circuit breaker and disconnect the main power before replacing any components.
* Wait at least five minutes after disconnecting the main power before replacing components.
* Component replacement must be performed by authorized personnel.
* The robot is designed and tested according to industrial, scientific, and medical (ISM) equipment standards. In household and light industrial environments, the robot may cause radio interference, requiring protective measures.
* Do not operate the robot near strong radiation sources (e.g., unshielded RF sources), as this may interfere with normal operation.
* The maximum operating speed of the robot is set to an optimal value at the factory. If an increase in speed is required, contact DOBOT's technical support engineer for consultation. Unauthorized modification of the maximum speed limit may result in excessive joint torque and other operational issues.

**WARNING**

* Wear anti-static clothing and anti-static gloves before operating the equipment.
* It is prohibited to modify or remove the nameplate, instructions, icons, or labels on the equipment.
* Before operating the equipment, locate and be familiar with the emergency stop function to ensure that the robot can be stopped urgently in case of an emergency. The emergency stop function is classified as a Stop Category 1.
* Be careful when handling or installing the robot. Follow the instructions on the packaging box, place the robot gently, and position it according to the arrow markings to prevent damage.
* To ensure device and personal safety, use supplied cables.
* Make sure that both the robot and the tools are correctly and securely installed.
* Make sure that the robot has sufficient space to move freely.
* Do not continue using the robot if it is damaged.
* Any impact will release a large amount of kinetic energy, which can be much higher than during high-speed or high-load operations.

### 1.7 Personal safety

When operating the robot system, please strictly follow the general precautions listed below to ensure the personal safety.

**WARNING**

* Comply with local laws or regulations with regard to the maximum weight one person is permitted to carry.
* Do not touch the wiring terminals or disassemble the equipment while it is powered on, as this may result in electric shock.
* Make sure that the equipment is properly grounded, otherwise, it may endanger personal safety.
* Do not touch the power terminals or disassemble internal components within

10 minutes of disconnecting the robot from the power supply, as residual voltage in the internal capacitors may cause electric shock.

* Even if the controller's power switch is already in the "OFF" status, do not touch or disassemble internal components, as residual voltage in the internal capacitors may cause electric shock.
* Do not wear loose clothing or jewelry when working with the robot. Tie your long hair back behind your head.
* If the robot appears to be stationary while the equipment is running, it may be in a standby state, waiting for a start signal. In such cases, the robot should still be considered active. Do not approach the robot.

### 1.8 Residual risks

DOBOT Robotics have undergone rigorous safety design and testing, and a series of safety measures have been implemented to minimize risks during installation, commissioning, operation, and maintenance. However, certain residual risks may remain and should be handled with caution during operation:

* Mechanical collision or pinching:

Unexpected collisions of mechanical components or abnormal gripping may occur during the robot's operation.

* Electrical hazards:

Risks such as accidental electrical leakage may arise due to cable aging or improper installation environments.

* Programming errors or loss of control:

Communication interference, incorrect parameter settings, or improper integration with other equipment could result in deviations from the intended robot actions.

* Human operational errors:

Risks caused by failure to strictly adhere to operational requirements, unauthorized parameter adjustments, or untrained personnel entering the robot's motion area. To reduce residual risks, follow these recommended practices during use:

* Wear protective equipment:

Always wear safety gear such as hard hats, safety glasses, and insulated gloves, especially when entering the robot's motion area.

* Isolate the workspace:

Use barriers or warning signs to prevent unauthorized personnel from entering the robot's operating range.

* Familiarize yourself with the emergency stop button:

Ensure the emergency stop button is always easily accessible and press it immediately in case of emergencies.

* Perform regular maintenance:

Conduct routine inspections of all robot components as specified in the manual to ensure proper functioning.

* Authorized use only:

Robots should only be operated by trained and qualified personnel. Unauthorized modification of parameters or disassembly of components is strictly prohibited. When using the robot, always operate it in strict accordance with the operational instructions and safety guidelines. DOBOT assumes no responsibility for any losses incurred due to failure to comply with these regulations.

### 1.9 Emergencies

#### 1.9.1 Emergency stop device

In an emergency, pressing the emergency stop button will immediately halt all robot motions. According to IEC 60204-1 and ISO 13850, emergency stop devices are not safeguards. They serve as supplementary protective measures and are not intended to prevent injuries. Based on the results of the risk assessment for the robot system, additional emergency stop buttons may be connected. The emergency stop button must comply with the IEC 60947-5-5 standard.

#### 1.9.2 Emergency recovery

The emergency stop button locks when pressed and must be rotated as indicated on the button to unlock it. After unlocking, the alarm can be cleared and the robot can be re- enabled via DobotStudio Pro to recover from the emergency status.

**WARNING**

Operate the robot arm to recover from emergency status only after the danger to the robot system has been completely eliminated.

#### 1.9.3 Personnel rescue in emergency situations

In rare emergency cases, you may need to move the robot arm while in an emergency stop status to rescue a trapped person. In such cases, you can: Manually releasing the brakes Open DobotStudio Pro and navigate to "Settings > Safety > Joint brake" page, click "Edit", hold the joint with your hand and turn on the switch of the joint you want to move, then click "Save". Once the brake is ON, you can drag the joint to rescue the trapped person.

**WARNING**

When switching on the "Joint brake" function, be sure to hold the joint with your hand to prevent it from falling.

_Figure 1.1 Manually release the brakes_

![Figure 1.1 Manually release the brakes](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnwBhw72Tu6zP9Fo2qG4g%2Fcr30h-p017-img01.png?alt=media)

Removing the fixing screws from robot base Refer to Robot arm installation. After removing the fixing screws from the robot base, you can move the robot arm to free the trapped person.

**WARNING**

* Disconnect the robot arm from the power before removing the screws.
* Hold the robot throughout the process of removing the screws and moving the robot arm.

## 2. Product Introduction

### 2.1 Overview

The main components of the robot system include:

_Figure 2.1 Robot overview_

The main components of the robot system include the following: Robot arm Six-axis robot arm (CR 30H series), main moving parts. Controller Core computing and electrical components. Connect to the controller to implement the emergency stop E-stop button function. Heavy-duty cable Used to connect the robot arm to the controller. Additionally, you can opt for an operation terminal (e.g., PC, tablet, or teach pendant) to install and run the robot's control software.

_Figure 2.2 Operation terminal_

![Figure 2.1 Robot overview](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fi4YRo2ZUmEWJU44WxoOR%2Fcr30h-p019-img01.jpg?alt=media)

![Figure 2.2 Operation terminal](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgYz8ll3c9rwgH33dLt3P%2Fcr30h-p019-img02.jpg?alt=media)

### 2.2 Robot arm

#### 2.2.1 Composition

The CR 30H series robot arm includes:

* Six rotary motion joints (J1 J6), and 2 connecting rods (upper arm and

– forearm).

* The robot base is equipped with a heavy-duty socket.
* The tool flange is equipped with buttons, indicator lights, and two aviation connectors.

_Figure 2.3 CR 30H robot arm_

#### 2.2.2 Tool flange buttons and indicator lights

* The tool flange of the CR 30H series is equipped with buttons and indicator lights, as shown in the diagram below.

![Figure 2.3 CR 30H robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F66WlGDmD5gq7AXULPnR4%2Fcr30h-p020-img01.jpg?alt=media)

_Figure 2.4 Tool flange buttons and indicator light_

When the robot arm is enabled, long-press the hand-guiding button to enter the drag-teaching mode. After dragging the robot arm to the teaching point, short-press the hand-guiding button to exit Hand-guiding button: the drag-teaching mode. If a collision occurs while the robot is in motion, short-pressing this button can reset the collision, allowing the robot arm to resume operation. Indicator light: Please refer to Table 2.1 for specific meanings.

_Table 2.1 Indicator light meanings_

Indicator color Status Description Blue Fast flashing The robot is starting up Blue Steady on The robot is powered on but not enabled Green Steady on The robot is enabled but not running Automatic running status (project Green Slow flashing debugging/running/pause, motion commands except TCP jog mode, trajectory playback) Single running status (Jog / "RunTo" function in Green Fast flashing software) / Drag mode / Trajectory recording status Red Slow flashing Joint brake switched on in disabled status

![Figure 2.4 Tool flange buttons and indicator light](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpzuEILH1BQYJUdxS6fES%2Fcr30h-p021-img01.jpg?alt=media)

Indicator color Status Description Red Steady on The robot is in alarm status Yellow Steady on Collision detected

**NOTE**

The quick flashing frequency is 5Hz (0.2s per cycle), and the slow flashing frequency is 1.25Hz (0.8s per cycle).

### 2.3 Controller

The CR 30H series robot arms need to be used with the CC365 controller. This controller only supports AC power input. For details on its electrical interfaces and switches, see Electrical Characteristics.

_Figure 2.5 Controller appearance_

![Figure 2.5 Controller appearance](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCWVK8Be4CDlLtgW7bG8Q%2Fcr30h-p022-img01.jpg?alt=media)

### 2.4 Operation terminal

The CR 30H series robot arms can be optionally controlled using a teach pendant. For more information, please refer to DOBOT Cobot Teach Pendant User Guide. Additionally, the CR 30H series robot arms support control via PC and mobile devices, as shown in Table 2.2.

_Table 2.2 Operation terminal specifications_

Terminal type PC Tablet (Android) Operating Windows 10 (64-bit) 1809 or Android 10 and above system above Control DobotStudio Pro (V4.7 and above) software

* CPU: 64-bit Intel or AMD processor (SSE4.2 or later, 2.9GHz or higher)
* Memory: 16G
* CPU: 4-core
* Storage: 128GB (at least 4GB
* RAM: 2GB

Recommended available) configuration • Storage: 32GB

* Network card: Gigabit-NIC
* Screen: 8-inch
* Graphics card: 4GB,

DirectX12 support

* Display: 1920x1080 or higher resolution Communication LAN/WiFi WiFi mode When purchasing a CR 30H series robot arm, you can request an optional Android tablet, or use self-prepared operation terminal as long as it meets or exceeds the recommended specifications in Table 2.2.

## 3. Product Features

### 3.1 Coordinate system

#### 3.1.1 Joint coordinate system

The joint coordinate system is determined based on all motion joints. All joints are rotational joints, as shown in Figure 3.1.

_Figure 3.1 Joint coordinate system_

#### 3.1.2 User coordinate system

The user coordinate system is a user-defined coordinate system based on the workbench or workpiece. The origin and axis directions can be defined as needed to measure points within the workspace and arrange tasks conveniently. The default user coordinate system is determined based on the center point of the robot base, and Y+ direction is the direction that the heavy-duty socket faces, as shown in Figure 3.2.

_Figure 3.2 User coordinate system_

![Figure 3.1 Joint coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5IWAGdl2xsdoA1LyNDoK%2Fcr30h-p024-img01.png?alt=media)

![Figure 3.2 User coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC75Od0tV9FIKvKkp1KDA%2Fcr30h-p024-img02.png?alt=media)

#### 3.1.3 Tool coordinate system

The tool coordinate system defines the position and posture of the Tool Center Point (TCP). Its origin and direction change dynamically based on the position and angle of the end tool. The default tool coordinate system is determined based on the center point of the end flange, with the Y+ direction facing opposite to the X1 aviation connector, as shown in

_Figure 3.3._

_Figure 3.3 Tool coordinate system_

### 3.2 Home posture

When the robot arm is in the upright position as shown in Figure 3.1, all joint angles are set to 0 degrees. This posture is called the home posture. Each joint of the robot arm is marked with a home-posture sticker (transparent, with a blue alignment line), as shown in the figure below. When a joint is at 0 degrees, the stickers on both sides of the joint will be perfectly aligned.

_Figure 3.4 Home-posture sticker_

If the home posture changes due to component replacement or collision, you can move the robot arm to a state where all the home-posture stickers of each joint are aligned. Then calibrate the home posture through DobotStudio Pro.

![Figure 3.3.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCkBr75kEyPXBo9AOZb4c%2Fcr30h-p025-img01.png?alt=media)

![Figure 3.3 Tool coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM3KSs4t8iKGfFfAXzCak%2Fcr30h-p025-img02.jpg?alt=media)

### 3.3 Singularities

When the robot moves in a linear or arc trajectory and approaches certain specific postures, an alarm will be triggered, and the robot will stop movement. These postures are referred to as singular positions or singular points.

**NOTICE**

* Joint motion is not affected by singular positions.
* Avoid stopping the robot near a singularity using drag mode or joint motion and then attempting linear or arc motion. The CR 30H series robot arms have three types of singularities, as described below.

#### 3.3.1 Shoulder singularity

The singularity occurs when the intersection of the J5 and J6 axes is located in the plane formed by the J1 and J2 axes. This typically happens in the cylindrical space directly above or below the robot. Refer to the motion range in the Mechanical Specifications chapter for details about each model. As shown in the figure below.

_Figure 3.5 Shoulder singularity_

![Figure 3.5 Shoulder singularity](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6NrXo4z5j0aye43X59NO%2Fcr30h-p026-img01.jpg?alt=media)

#### 3.3.2 Elbow singularity

The singularity occurs when J3=0°±2°, where the upper arm and forearm are parallel. As shown in the figure below.

_Figure 3.6 Elbow singularity_

![Figure 3.6 Elbow singularity](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUyKyjC5xZMObUbBQ9P8q%2Fcr30h-p027-img01.jpg?alt=media)

#### 3.3.3 Wrist singularity

The singularity occurs when J5=0°±2°, where the J4 axis and J6 axis are parallel. As shown in the figure below.

_Figure 3.7 Wrist singularity_

#### 3.3.4 Recommendations for avoiding singularities

● Switch the motion type to joint motion when near a singularity. ● Add transition points in the trajectory to bypass the singularity. ● Adjust the installation posture of the robot to avoid singularities in the path. For example, switch from standard-angle mounting to hoisting or side mounting. ● Modify the length of the end tool. ● Adjust the installation angle of the end tool to bypass singularities in the path.

![Figure 3.7 Wrist singularity](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGtDZcOhU9Z9RDggqw8yA%2Fcr30h-p028-img01.jpg?alt=media)

### 3.4 Emergency stop time and distance

The emergency stop time refers to the duration required from triggering an emergency stop to the complete cessation of the robot’s movement. The emergency stop distance, on the other hand, indicates the distance traveled by the robot’s end effector during this emergency stopping time. It is important to note that the robot remains in motion throughout this process and may still pose a risk of injury to personnel or damage to other devices. Therefore, both operators and integrators should take into account the robot’s emergency stop time and distance when conducting risk assessments.

**NOTE**

* The DOBOT CR 30H, CR 30HT, and CR 30H-Food series robots have the same emergency stop time and the same emergency stop distance.
* For information on the testing postures and conditions, please refer to the descriptions below. Detailed testing data can be found in Appendix B Emergency Stop Time and Distance, and Appendix C Normal Stop Time and Distance.

#### 3.4.1 Testing posture

For the J1 axis, emergency stop testing is conducted by moving horizontally, meaning the rotational axis is perpendicular to the ground.

_Figure 3.8 J1 Emergency stop test_

For the J2 and J3 axes, emergency stop testing follows a vertical trajectory, meaning the rotational axis is parallel to the ground. The emergency stop is triggered while the robot is moving downward.

_Figure 3.9 J2 Emergency stop test_

![Figure 3.8 J1 Emergency stop test](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8iqUcEXKl2YLQuhApt71%2Fcr30h-p029-img01.jpg?alt=media)

![Figure 3.9 J2 Emergency stop test](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyND34qJn9cklefi5SBiw%2Fcr30h-p029-img02.jpg?alt=media)

_Figure 3.10 J3 Emergency stop test_

#### 3.4.2 Testing condition

* Joints: J1, J2, J3
* Arm extension: 33%, 66%, 100%
* Speed: 33%, 66%, 100%
* Payload: 10kg, 20kg, 30kg

**NOTICE**

When testing the J3 axis, the arm extension is fixed at 100%.

![Figure 3.10 J3 Emergency stop test](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnXGiGv7VHsBu4YAgcjqV%2Fcr30h-p030-img01.jpg?alt=media)

## 4. Mechanical Specifications

All dimensions in this chapter are in millimeters (mm). The appearance and dimensions of the DOBOT CR 30H, CR 30HT, and CR 30H-Food series robots are identical.

### 4.1 Robot mechanical specifications

#### 4.1.1 CR 30H dimensions and workspace

When selecting the installation position for the robot, you must consider the cylindrical space directly above and below the robot, and try to avoid moving the tool into this cylindrical space. As doing so may cause the joints to rotate too fast even when the tool moves slowly, resulting in low work efficiency and making risk assessment more difficult.

_Figure 4.1 CR 30H dimensions and workspace_

![Figure 4.1 CR 30H dimensions and workspace](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuJY0JUUbMqkeZMldkKpk%2Fcr30h-p031-img01.jpg?alt=media)

#### 4.1.2 CR 30H base mounting dimensions

_Figure 4.2 CR 30H base mounting dimensions_

**NOTE**

For ease of securing the forklift sheet metal, the CR 30H base is equipped with M12 threaded mounting holes.

![Figure 4.2 CR 30H base mounting dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK11CrwrzXEedSFl6CNLU%2Fcr30h-p032-img01.jpg?alt=media)

#### 4.1.3 CR 30H end flange dimensions

The flange design conforms to ISO 9409-1.

_Figure 4.3 CR 30H end flange dimensions_

#### 4.1.4 CR 30H end load curve

The figure below illustrates the load curve for CR 30H when installed at the standard mounting angle. The horizontal axis represents the offset distance (eccentricity), which is the distance from the load’s center of mass to the center of the CR 30H end flange, measured in millimeters (mm). The vertical axis represents the load weight, measured in kilograms (kg).

_Figure 4.4 CR 30H end load curve_

### 4.2 Controller dimensions

![Figure 4.3 CR 30H end flange dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkZCyusK4O5qUAk0gWwfk%2Fcr30h-p033-img01.jpg?alt=media)

![Figure 4.4 CR 30H end load curve](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FflFH6gO5SgcDwLCi6EQY%2Fcr30h-p033-img02.png?alt=media)

_Figure 4.5 CC365 dimensions_

![Figure 4.5 CC365 dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFlIE43NqeocD1pG5jisW%2Fcr30h-p034-img01.jpg?alt=media)

## 5. Electrical Characteristics

### 5.1 Electrical warnings and precautions

When designing and installing robot applications, please strictly follow the warnings and precautions listed below.

**WARNING**

The following warnings must be observed when designing and installing safety signal-related functions, as failure to do so may result in the loss of safety functions and cause injury or death.

* Never connect safety signals to a non-safety PLC with an inappropriate safety level. Always separate safety signals from regular I/O signals.
* All safety signals must use a dual-channel redundant design, with both channels remaining independent. This ensures that if one channel fails, the safety function will still be maintained.

**WARNING: ELECTRICITY**

* Make sure that the equipment is protected from water ingress. If water gets into the equipment, disconnect the power and contact technical support. Do not reconnect the power until the issue is resolved.
* Only use the robot's original cables and avoid bending the cables.
* Make sure that the power supply connected to the controller is properly grounded and avoid leaving the grounding prong of the power plug floating.

**NOTICE**

* The robot has passed electromagnetic compatibility (EMC) tests according to relevant standards. Electromagnetic interference exceeding these standards may affect the robot's behavior. Extremely high signal levels or excessive exposure to electromagnetic fields may cause permanent damage to the robot. DOBOT assumes no responsibility for any damage caused by EMC issues beyond the standards.
* The length of I/O cables used to connect the controller to other machinery or equipment should not exceed 30 meters unless confirmed feasible through on-site testing. If necessary, use shielded cables.

### 5.2 Controller interface

#### 5.2.1 Overview

The electrical interfaces of the controller are all on the front panel, as shown in the figure below.

_Figure 5.1 Controller interface overview_

No. Description Controller switch. After the controller is powered on, press the button for 0.5s and release it, the controller will be turned on. ① When the controller is started, press the button for 3s and release it, the controller will be turned off and the robot arm will be powered off.

![figure below.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx60cFPLVBQ9qmNjsS3Sa%2Fcr30h-p036-img01.jpg?alt=media)

No. Description

**NOTE**

This is a self-resetting switch and does not support automatic startup when the controller is powered on. However, you can use the remote switch interface to realize remote control of startup or shutdown. Teach Pendant and E-Stop interface. See Teach pendant and emergency stop ② interface for details. USB port. ③ For importing/exporting files. LAN port, default IP address:

* LAN1: 192.168.5.1
* LAN2: 192.168.200.1

④ For connecting to a PC for debugging or to external devices that support TCP/IP or Modbus TCP protocols. Only LAN1's IP address can be modified via DobotStudio Pro. EtherCAT interface (Internally reserved, not open for external use). ⑤ I/O interface panel. Used for connecting external devices. ⑥ See I/O interface panel for details. Heavy-duty interface. For connecting to the robot, providing power and enabling communication with ⑦ the robot. For details, see Controller heavy-duty interface. AC power input. ⑧ For connecting to 200 – 240V AC single-phase power supply. AC power switch. ⑨ For powering on/off the controller.

#### 5.2.2 Teach pendant and emergency stop interface

This interface is used to connect to the teach pendant (optional) or an E-stop button. The pin definitions are as follows.

_Figure 5.2 Teach pendant and E-stop button interface_

Pin Definition 1 DC 24V 2 DC 0V 3 DC 24V Emergency stop circuit 1 input (normally closed) 5 DC 24V Emergency stop circuit 2 input (normally closed) Dedicated for communication with 7 – 15 the teach pendant

![Figure 5.2 Teach pendant and E-stop button interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FltZgIs6rTIoU4YRGAayg%2Fcr30h-p038-img01.png?alt=media)

#### 5.2.3 I/O interface panel

The controller contains an I/O interface panel for connecting to external devices such as air pump, PLC, etc. The I/O interface panel supports: 24 digital inputs, 24 digital outputs, 2 analog outputs, 2 analog inputs, 1 incremental encoder input, 1 RS485 interface, 1 CAN interface, 10 safety inputs, and 10 safety outputs. All interfaces with the same silkscreen label have common functions, so any available interface with the same label can be used for wiring. The interfaces connected by green lines in the figure below are factory short-circuited by default.

_Figure 5.3 Controller I/O interface_

![Figure 5.3 Controller I/O interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpEnSKV394B0kBoxbYBiE%2Fcr30h-p039-img01.png?alt=media)

Silkscreen Definition I/O 5V Internal power +5V and 0V, mainly used for powering pulse encoders. I/O 0V A+/A- Pulse encoder interface, used for receiving encoder signals. B+/B- See Encoder interface for details. Z+/Z- RP 24V Remote switch interface, used for remote power on/off. See Remote switch interface for details. ON/OFF AI1 – AI2 Analog input/output interface, used for connecting external devices that operate with analog signals. AO1 – AO2 See Analog I/O interface for details. DI1 – DI24 Digital input/output interface, used for connecting external devices that operate with digital signals. DO1 – DO24 See Digital I/O interface for details. Digital input common terminal interface, used to switch DI signal COM1 – COM2 types. I/O 24V I/O power +24V and 0V. The power source can be configured for internal or external power supply based on wiring methods. I/O 0V See I/O interface power for details. 24V Internal power +24V and 0V, used for powering I/O interfaces or external devices. 0V 485A RS485 interface, mainly used for Modbus RTU communication. See RS485 interface for details. 485B FG Used for grounding encoders or RS485, and CAN interfaces. CAN\_H CAN bus interface (Internally reserved, not open for external use). CAN\_L SI 24V Safety I/O power +24V and 0V, used for powering external safety devices. SO 0V SI1 – SI10 Safety input/output interface, used for connecting external safety devices. See Safety I/O interface for details. SO1 – SO10

#### 5.2.4 I/O interface power

The I/O interface can be powered by either an internal or an external 24V power supply.

_Table 5.1 I/O power supply specifications_

Interface Parameter Min value Typical Max value Unit Internal 24V power supply Voltage 23 24 25 V 24V–0V Current 0-3 A External 24V power supply Voltage 20 24 29 V External power supply Current 0-6 A When using the internal power supply, short-circuit the 0V and 24V terminals to the nearest I/O 0V and I/O 24V interfaces, as shown in the figure below.

_Figure 5.4 I/O connected to internal power supply_

If a higher total output current is required, an external 24V power supply can be connected, as shown in the figure below. The external and internal power supplies are isolated from each other and do not interfere with one another.

_Figure 5.5 I/O connected to external power supply_

![Table 5.1 I/O power supply specifications](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz22Xhg3ZQ24mNpyoFejr%2Fcr30h-p041-img01.png?alt=media)

![Figure 5.4 I/O connected to internal power supply](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJzb3OQLeykK9jJtX95ii%2Fcr30h-p041-img02.png?alt=media)

**NOTE**

All subsequent sections assume that the I/O power supply is properly connected, and the wiring details for I/O power will not be repeated.

#### 5.2.5 Digital I/O interface

_Table 5.2 Digital I/O interface specifications_

Interface Parameter Min value Typical Max value Unit Digital input Voltage -3-30 V OFF range -3-5 V DIx ON range 15-30 V Current (ON range) 4-7 mA Type-NPN/PNP - - Digital output Current 0-0.5 A Voltage drop 0-0.5 V DOx Current leakage 0-0.1 mA Type-NPN/PNP - - The DI interface must be connected to the COM interface, which can switch signal types (PNP or NPN). COM1 is used for DI1 – DI12. COM2 is used for DI13 – DI24. These configurations can be set independently. For DI connected to a simple switch, the wiring is shown below (left figure: PNP wiring, right figure: NPN wiring). You can choose the appropriate wiring method based on the on-site requirements.

_Figure 5.6 DI connected to simple switch_

For DI connected to an external PNP three-wire sensor, the wiring is shown below. If the sensor is powered by the controller, short-circuit the corresponding COM port to I/O 0V (left figure below). If the sensor is powered by an external supply, connect the COM port to 0V of the external power supply (right figure below).

_Figure 5.7 DI connected to PNP input_

For DI connected to an external NPN-type DO, the wiring is shown below. If the external DO is powered by the controller, short-circuit the corresponding COM port to I/O 24V (left figure below). If the external DO is powered by an external supply, connect the COM port to 24V of the external power supply (right figure below).

![Figure 5.6 DI connected to simple switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FenuXugjCoQzlnGuCYXPe%2Fcr30h-p043-img01.png?alt=media)

![Figure 5.7 DI connected to PNP input](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FT2qSGl9EbUz7pUuKOrrX%2Fcr30h-p043-img02.png?alt=media)

_Figure 5.8 DI connected to NPN input_

DO is set to PNP by default but can be configured to NPN via the software (DobotStudio Pro). If the software setting and the actual wiring method do not match (e.g., PNP is set in DobotStudio Pro, but the load wiring is NPN), the load will not work properly. When DO is set to PNP, the wiring for connecting to an external load is shown below.

_Figure 5.9 PNP DO connected to external load_

![Figure 5.8 DI connected to NPN input](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWzhg4WuQkmuHonY5npoU%2Fcr30h-p044-img01.png?alt=media)

![Figure 5.9 PNP DO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjIDpUT2sSGCK7V5m678f%2Fcr30h-p044-img02.png?alt=media)

When DO is set to NPN, the wiring for connecting to an external load is shown below.

_Figure 5.10 NPN DO connected to external load_

To ensure stable operation, it is recommended to maintain a minimum interval of 15ms between two DI signals or two DO signals.

#### 5.2.6 Analog I/O interface

The analog signal interface supports both Voltage (0V – 10V) and Current (4mA – 20Ma) signals. By default, it is set to "Voltage" mode, but it can be configured to "Current" mode via DobotStudio Pro. To improve the accuracy of analog signals, it is recommended to use shielded cables or twisted-pair wiring.

_Table 5.3 Analog I/O interface specifications_

Interface Parameter Min value Typical Max value Unit Analog input (Voltage mode) Voltage -10-10 V AIx Resistance-6100-Ω Resolution-12-Bits Analog input (Current mode) Current 4-20 mA AIx Resistance-160-Ω

![Figure 5.10 NPN DO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FubLLoOPOQsAaOb1z0RGw%2Fcr30h-p045-img01.png?alt=media)

Resolution-12-Bits Analog output (Voltage mode) Voltage -10-10 V Current -20-20 mA AOx Resistance-100-Ω Resolution-12-Bits Analog output (Current mode) Current 4-20 mA AOx Voltage 0-12 V Resolution-12-Bits For AI interface connected to the tested object, the wiring is shown below.

_Figure 5.11 AI connected to tested object_

![Figure 5.11 AI connected to tested object](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYcBe8qDzJdta0P4n4Kha%2Fcr30h-p046-img01.png?alt=media)

For AO interface connected to external load, the wiring is shown below.

_Figure 5.12 AO connected to external load_

#### 5.2.7 Remote switch interface

The remote switch interface is used to remotely control the on/off function of the controller. When the ON/OFF interface inputs are at high level for 0.5s or more, the controller will be turned on. In the power-on status, when the ON/OFF interface inputs are at high level for 3s or more, the controller will be turned off. The wiring is shown below.

_Figure 5.13 Remote switch interface wiring_

![Figure 5.12 AO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIbvsVk9Qeg9DpPxhAdxu%2Fcr30h-p047-img01.png?alt=media)

![Figure 5.13 Remote switch interface wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9Q2EvutNSyyOzl2P5VXE%2Fcr30h-p047-img02.png?alt=media)

#### 5.2.8 Encoder interface

An encoder is a device that converts angular or linear displacement into electrical signals. It converts the displacement into periodic electrical signals, then converts these signals into counting pulses, so that the magnitude of the displacement can be measured by the number of pulses. The input signal in a specified format is supported. In this section, wiring is explained using the OMRON E6B2-CWZ1X encoder as an example. Based on the encoder's wiring colors, connect each signal cable to the controller. First, connect the power cables (5V and 0V) to the corresponding I/O 5V and I/O 0V interfaces. Then, connect the remaining encoder signal cables to their respective interfaces. If a ground wire is required, you can connect the shielded cable to the FG interface located under the RS485 interface. In most cases, the ground wire does not need to be connected unless there is strong magnetic interference.

_Table 5.4 Encoder wiring color_

Color Corresponding interface Brown I/O 5V Blue I/O 0V Black A+ White B+ Orange Z+ Black and Red A- White and Red B- Orange and Red Z-

_Figure 5.14 Encoder interface wiring_

#### 5.2.9 RS485 interface

The RS485 interface is mainly used for Modbus RTU communication. When connecting external devices (such as PLCs), connect the 485A (or 485+) and 485B (or 485-) interfaces of both devices correspondingly, and connect the ground wire according to the actual site conditions, as shown in the figure below (using dual-end grounding as an example).

_Figure 5.15 RS485 connected to PLC_

![Figure 5.14 Encoder interface wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fs2qWA9nZzLaQKnfnm7SO%2Fcr30h-p049-img01.jpg?alt=media)

![Figure 5.15 RS485 connected to PLC](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Faku0DIBFIGOP7Lt0X3GE%2Fcr30h-p049-img02.png?alt=media)

#### 5.2.10 Safety I/O interface

The safety I/O includes 20 interfaces: SI1 – SI10 (input), SO1 – SO10 (output). The basic electrical specifications of the safety I/O are the same as those of the common digital I/O. Safety input

_Table 5.5 SI interface definition_

Silkscreen Definition SI1, SI2 User emergency stop input SI3, SI4 Protective stop input No configuration by default, can be configured via DobotStudio Pro to: SI5 – SI10 • User emergency stop input (no status output)

* Protective stop reset input
* Reduced mode input

User emergency stop input The user emergency stop input is an emergency stop interface provided for users to connect to external emergency stop devices. By default, the user emergency stop input is a high-level, normally closed signal. Any low-level input will trigger the robot to enter emergency stop status. This function typically triggers the emergency stop output, which may cause self-locking in certain cases. To prevent this, you can configure the SI interface to "User E-Stop (no status output)" in the software, and use the corresponding interface for this purpose. SI1 and SI2 are user emergency stop inputs. The wiring for connecting one or more emergency stop switches is shown below.

_Figure 5.16 SI connected to one emergency stop switch_

![Table 5.5 SI interface definition](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWPVl1LIx3gQlfUpsHyzC%2Fcr30h-p050-img01.png?alt=media)

_Figure 5.17 SI connected to multiple emergency stop switches_

Protective stop input The protective stop input is used for connecting external protective devices (e.g., safety door, safety light curtains). By default, the protective stop input is a high-level, normally closed signal. Any low- level input will trigger the robot to enter a protective stop (pause) status.

* When the protective stop reset input interface is configured, the protective stop status can be released only by restoring the protective stop input signal and triggering the protective stop reset input signal simultaneously. After confirming the continue operation in the software, the robot will resume operation.
* When the protective stop reset input interface is not configured, the protective stop status can be released by restoring the protective stop input signal, and the robot will resume operation. SI3 and SI4 are the protective stop inputs. The following are two typical cases where a protective stop reset input is not used:
* Safety door: When the door opens, the switch disconnects, triggering the protective stop. When the door closes, the robot resumes operation.

![Figure 5.17 SI connected to multiple emergency stop switches](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOzNkBDq5Smqouuuj7z2K%2Fcr30h-p051-img01.png?alt=media)

_Figure 5.18 SI connected to safety door switch_

* Safety laser scanner: When an operator enters the safety zone set by the laser scanner, the protective stop is triggered. Once the operator leaves the safety zone, the robot resumes operation.

_Figure 5.19 SI connected to safety laser scanner_

![Figure 5.18 SI connected to safety door switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9HXCycUEr5NBwQ8QVIjZ%2Fcr30h-p052-img01.png?alt=media)

![Figure 5.19 SI connected to safety laser scanner](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Frx1wnJI9O0j2NsAJGGWC%2Fcr30h-p052-img02.png?alt=media)

Protective stop reset input The protective stop reset input is used to reset the protective stop status. By default, the protective stop reset input is a high-level, normally open signal. The rising edge of both circuits triggers to reset the protective stop status. The protective stop reset switch must be a dual-channel switch and must be placed outside the protective zone. A typical example of using the protective stop input with the protective stop reset input is a safety light curtain: When the operator passes through the light curtain, the protective stop is triggered. When the operator leaves the protective zone, presses the reset switch, and then confirms the continue operation in the software, the robot will resume operation. Below is an example where SI9 and SI10 are configured as protective stop reset inputs.

_Figure 5.20 SI connected to safety light curtain_

Reduced mode input The reduced mode input is used to control the robot to enter reduced mode. In reduced mode, the robot’s motion parameters (joint speed, TCP speed) are limited within the reduced mode range. By default, the reduced mode input is a high-level, normally closed signal. Any low- level input will trigger the robot to enter reduced mode. If the high-level input is restored, the robot will exit the reduced mode and return to the normal mode. The wiring for connecting the reduced mode switch is the same as the wiring for connecting the user emergency stop switch or protective stop switch.

![Figure 5.20 SI connected to safety light curtain](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4VGvTNKj8RBgq3yb1dif%2Fcr30h-p053-img01.png?alt=media)

Safety output

_Table 5.6 SO interface definition_

Silkscreen Definition SO1, SO2 Emergency stop status output No configuration by default, can be configured via DobotStudio Pro to:

* Protective stop status output
* Reduced mode output

SO3 – SO10 • Non-stop status output

* Running status output
* Safety home status output
* System emergency stop status output
* User emergency stop status output

Emergency stop status output When the robot is in emergency stop status, the output voltage is low-level; otherwise, the output voltage is high-level. Any emergency stop source will trigger this output. SO1 and SO2 are the emergency stop status outputs, and the wiring for connecting external loads (e.g., warning lights) is shown below.

_Figure 5.21 SO connected to external load_

By using this output and the user emergency stop input, emergency stop interlock can be implemented between multiple robots. In this case, when one robot triggers an emergency stop, the others will also trigger an emergency stop. The following figure shows how to configure the emergency stop interlock between two robots, where each robot's SO1/SO2 is connected to the other robot's SI1/SI2.

![Table 5.6 SO interface definition](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiwjQWWiio0plqvnv0qXb%2Fcr30h-p054-img01.png?alt=media)

_Figure 5.22 Emergency stop interlock between two robots_

Protective stop status output When the robot is in protective stop status, the output voltage is low-level; otherwise, the output voltage is high-level. Reduced mode output When the robot is in reduced mode, the output voltage is low-level; otherwise, the output voltage is high-level. Non-stop status output When the robot is in automatic running (non-stop status), the output voltage is low- level; otherwise, the output voltage is high-level. This status indicates whether the robot is running a program, not whether the joints are moving. For example, while running a project, if the robot is waiting for a specified DI to turn ON and not moving, the robot is in non-stop status and outputs low-level voltage. If the project is paused, the robot is in stop status and outputs high-level voltage.

![Figure 5.22 Emergency stop interlock between two robots](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fas0wXDxNBNOsOOGG4zTb%2Fcr30h-p055-img01.png?alt=media)

Running status output If one or more joints of the robot are moving at more than 1°/s (except drag mode), it is considered to be in running status, and the output voltage is low-level; otherwise, the output voltage is high-level. Safety home status output When the robot is in safe home position, the output voltage is high-level; otherwise, the output voltage is low-level. The safe home position is a user-defined posture that can be set through the software. System emergency stop status output When the robot is in emergency stop status triggered by the emergency stop button or software, the output voltage is high-level; otherwise, the output voltage is low-level. User emergency stop status output When the robot is in user emergency stop status (triggered by SI1 / SI2), the output voltage is high-level; otherwise, the output voltage is low-level.

#### 5.2.11 Controller heavy-duty interface

The heavy-duty interface, located on the robot base, is connected to the controller via a heavy-duty cable to provide power and control signals for the robot arm. The pin distribution and definitions for the heavy-duty interface of the CR 30H series controller are as follows.

_Figure 5.23 Controller heavy-duty interface pin distribution_

![Figure 5.23 Controller heavy-duty interface pin distribution](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6qIoDltFrvbXVDLoVaKH%2Fcr30h-p056-img01.png?alt=media)

Pin Name Definition Pin1 108V 108V DC Power + Pin2 108V 108V DC Power + Pin3 0V 108V DC Power - Power Pin4 0V 108V DC Power - interface Pin5 SH1 Outer Cable Shielding Pin 1 8 – Pin6 -- Reserved, PE Pin7 24V 24V DC Power + Pin8 GND 24V DC Power - PE PE Protective Ground 1 T+ Send Data + 2 T- Send Data - Communication 3 R+ Receive Data + Interface 4 R- Receive Data - (Pin 9) 5 -- Reserved 6 -- Reserved

### 5.3 Robot arm interface

#### 5.3.1 Robot arm heavy-duty interface

The heavy-duty interface, located on the robot base, is connected to the controller via a heavy-duty cable to provide power and control signals for the robot arm. The pin distribution and definitions for the heavy-duty interface of the CR 30H series robot arms are as follows. See Heavy-duty interface pin distribution for the definition of each pin.

_Figure 5.24 Robot heavy-duty interface pin distribution_

#### 5.3.2 Tool I/O interface

Location and pin definitions The tool interface is located on the side of the end flange of the robot arm and uses two aviation connectors (mechanical specifications are M8 and M12). The pin layout and definitions for the two connectors are as follows.

![Figure 5.24 Robot heavy-duty interface pin distribution](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRsR2bQOtIK9t1MCsUbcZ%2Fcr30h-p058-img01.png?alt=media)

_Figure 5.25 Tool I/O pin distribution_

Aviation connector X1 (M8) Aviation connector X2 (M12) Pin Name Definition P in Name Definition 1 485A 485A 1 24V 24V Output 2 485B 485B 2 GND Ground 3 DI\_2 Digital input 2 3 DI\_4 Digital Input 4 4 DI\_1 Digital input 1 4 DI\_3 Digital Input 3 0/12/24V Power 5 0/12/24V 5 24V 24V Output Output Digital Output 2 or 6 DO\_2 6 DO\_4 Digital Output 4 Ground Digital Output 1 or 7 DO\_1 0/12/24V Power 7 DO\_3 Digital Output 3 Output 8 GND Ground 8 GND Ground

![Figure 5.25 Tool I/O pin distribution](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Flb3T6ZIf5A6eReuPOr6I%2Fcr30h-p059-img01.png?alt=media)

Aviation cable description Both aviation connector X1 (M8) and aviation connector X2 (M12) utilize cables specified by our company. Below are the models, connector pin distributions, and definitions for the two types of cables:

_Table 5.7 Tool I/O aviation cable_

M8 Aviation cable M12 Aviation cable Model: LUTRONIC, TC-FP-222912, Model: SIGNAL, SGNN2502018-2- Single-ended M8A CODING 8P/F, 90- 1960, Single-ended M12A 8P/M, 90- degree angled head. degree angled head. Connector pin diagram: Connector pin diagram: Cable color and definitions: Cable color and definitions: Cable Cable Pin Definition Pin Definition color color 1 White 485A 1 White 24V output 2 Brown 485B 2 Brown Ground 3 Green Digital input 2 3 Green Digital input 4 4 Yellow Digital input 1 4 Yellow Digital input 3 0/12/24V power 5 Gray 5 Gray 24V output output Digital output 2 or 6 Pink 6 Pink Digital output 4 ground Digital output 1 or 7 Blue 0/12/24V power 7 Blue Digital output 3 output 8 Red Ground 8 Red Ground Tool I/O (M8) power specifications The Tool I/O (M8) can supply 0/12/24V power to the end tools, with specific voltage

![Table 5.7 Tool I/O aviation cable](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkaqSTktqowI1aqPIRpVB%2Fcr30h-p060-img01.jpg?alt=media)

![Official manual figure, page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBGD18w9JWcPtlxB8JLIE%2Fcr30h-p060-img02.jpg?alt=media)

levels configured through the DobotStudio Pro control software. It supports single-pin and dual-pin modes, with different wiring methods and output power ranges in different modes.

* Single-Pin Mode: Only the power pin is used, connecting the power wire (gray) and the ground wire (red) from the M8 connector cable to the end tool.

1. The wiring diagram for Single-Pin Mode is shown below:

_Figure 5.26 Tool I/O (M8) wiring-Single-Pin Mode_

2. Navigate to the "Monitoring > Tool I/O" page in the DobotStudio Pro control

software. Set the "DO Settings" to "Standard Output" (default value), and adjust the "Tool Output Voltage" according to the voltage of the actual connected device.

_Figure 5.27 Tool I/O (M8) configuration-Single-Pin Mode_

![Figure 5.26 Tool I/O (M8) wiring-Single-Pin Mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6UmNu4ULLcOct7zAqLNw%2Fcr30h-p061-img01.png?alt=media)

![Figure 5.27 Tool I/O (M8) configuration-Single-Pin Mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FssgcglfKVXfW5xAiwwdA%2Fcr30h-p061-img02.png?alt=media)

3. In Single-Pin Mode, the power output available from the tool I/O is as follows:

Parameter Min value Typical Max value Unit Voltage (24V) 22 24 26 V Voltage (12V) 10 12 14 V Current 0 1 2 A

* Dual-Pin Mode: Use both the power pins and DO pins simultaneously by connecting the power line (grey), ground line (red), DO2 (pink), and DO1 (blue) of the M8 aviation plug cable to the end tool.

1. A wiring diagram for Dual-Pin Mode is shown below:

_Figure 5.28 Tool I/O (M8) wiring-Dual-Pin Mode_

2. Navigate to the "Monitoring > Tool I/O" page in the DobotStudio Pro control

software. Set "DO Settings" to "Dual-Pin Power Supply" and adjust the "Tool Output Voltage" according to the voltage of the actual connected device.

![Figure 5.28 Tool I/O (M8) wiring-Dual-Pin Mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRG9gf19tJs5tcxmlVe4U%2Fcr30h-p062-img01.png?alt=media)

_Figure 5.29 Tool I/O (M8) configuration-Dual-Pin Mode_

3. In Dual-Pin Mode, the power output available from the tool I/O is as follows:

Parameter Min value Typical Max value Unit Voltage (24V) 22 24 26 V Voltage (12V) 10 12 14 V Current 0 2 4 A Tool I/O (M12) power specifications The tool I/O (M12) can supply a 24V power output to end tools. The M12 aviation connector has two sets of power pins, and the power output varies depending on whether one set or both sets of power pins are connected.

* When only one set of power pins is connected: Connect the 24V power wire

(white or grey wire, choose either one) and the ground wire (brown or red wire, choose either one) of the M12 aviation connector cable to the end tool. The wiring diagram and the description of the available output power in this mode are as follows:

![Figure 5.29 Tool I/O (M8) configuration-Dual-Pin Mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLctaBBzk2eb6pp55wPjZ%2Fcr30h-p063-img01.png?alt=media)

_Figure 5.30 Tool I/O (M12) wiring-Single Power Mode_

Parameter Minimum Typical Value Maximum Unit Voltage (24V) 22 24 26 V Current 0 1 2 A

* When both sets of power pins are connected: Connect both sets of 24V power wires (white and grey wires) and ground wires (brown and red wires) of the M12 aviation connector cable to the end tool respectively. The wiring diagram and the description of the available output power in this mode are as follows:

_Figure 5.31 Tool I/O (M12) wiring-Dual Power Mode_

Parameter Min value Typical Max value Unit Voltage (24V) 22 24 26 V Current 0 2 4 A

![Figure 5.30 Tool I/O (M12) wiring-Single Power Mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxYkxQX2sBMfVW4suqagi%2Fcr30h-p064-img01.png?alt=media)

![Figure 5.31 Tool I/O (M12) wiring-Dual Power Mode](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlsHO1fY8euTNoNWd9ssO%2Fcr30h-p064-img02.png?alt=media)

Tool I/O digital input/output

_Table 5.8 Tool digital I/O specifications_

Interface Parameter Min value Typical Max value Unit Digital input (PNP with pull-down resistor, reads low when floating) Voltage -0.5-30 V OFF range -0.5-2 V DI\_x ON range 7-30 V Input resistance-57K-Ω Type-PNP - - Digital output Current 0-0.5 A Voltage drop 0-0.5 V DO\_x Current leakage 0-0.1 mA Type-PNP - - The tool digital input is PNP type. The wiring for connecting an external simple switch circuit is as follows.

_Figure 5.32 Tool DI connected to simple switch_

When using a PNP three-wire sensor as the DI input source, the wiring is shown below.

_Figure 5.33 Tool DI connected to PNP-type sensor_

![Table 5.8 Tool digital I/O specifications](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfEV8Kw4zp90diVnFsvbE%2Fcr30h-p065-img01.png?alt=media)

![Figure 5.32 Tool DI connected to simple switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK2kOu2BnR00l5jZbho0b%2Fcr30h-p065-img02.png?alt=media)

The digital output of the tool I/O defaults to High Impedance State, but can be configured as "PNP, NPN, Push/Pull, High Impedance State" through the DobotStudio Pro control software. It is powered by the internal power supply, with the total output current at the end-effector not exceeding the maximum 24V output current as described before. The output current for a single DO channel should be 500mA. The software settings and ≤ wiring methods are as follows.

_Figure 5.34 Tool DO standard output_

_Figure 5.35 Tool DO wiring_

![Figure 5.34 Tool DO standard output](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhekAGQQBkD3cq4oURXbH%2Fcr30h-p066-img01.png?alt=media)

![Figure 5.35 Tool DO wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZVfft4UJF3OOziAaan2y%2Fcr30h-p066-img02.png?alt=media)

## 6. Transportation

### 6.1 Transportation precautions

* The robot arm should be restored to its packing posture before transportation.

This can be set in DobotStudio Pro (refer to DobotStudio Pro User Guide for details). Use the original packaging for transportation.

* During transportation, ensure that the robot arm remains stable and is securely fastened.
* During transportation and long-term storage, maintain an ambient temperature range of -20°C to +55°C, with humidity ≤95% and no condensation.
* After transportation, store the original packaging in a dry place for future repacking and transportation.
* During transportation, unpacking, and handling, avoid any impact to the tool flange of the CRAF series (as it contains a high-precision force sensor) to prevent accidental drops and shocks.

**WARNING**

* DOBOT assumes no responsibility for any damage incurred during transportation.
* Strictly follow the installation instructions when installing the robot.

### 6.2 Unpackaged handling

When moving the robot arm from its packaging to the installation position or relocating it, follow these handling guidelines:

* If the robot arm is not in the packing posture, restore it to the packing posture first.
* When handling and installing the robot, hold the robot arm with your hand until all base mounting bolts are fully tightened.
* Always use the provided sling for hoisting. See Robot arm installation for detailed hoisting instructions. Never secure the sling to joints J3-J6 or the forearm to lift the robot, as this may damage the internal structure of the robot.

_Figure 6.1 Hoisting the robot arm_

![Figure 6.1 Hoisting the robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw4Iubm66WrZgRrCuod2D%2Fcr30h-p068-img01.jpg?alt=media)

## 7. Installation and Use

### 7.1 Installation environment

To maintain the performance of the controller and robot arm and ensure safe use, please place the controller and robot arm in an environment that meets the following conditions.

**NOTICE**

Please make sure that the installation environment meets the following conditions to avoid potential damage.

* Install indoors with good ventilation.
* Keep away from excessive vibration and shock.
* Keep away from direct sunlight and radiant heat.
* Keep away from dust, oil mist, smoke, salinity, metal powder, corrosive gases, and other contaminants.
* Do not use in a closed environment. A closed environment may cause the controller to overheat and shorten its service life.
* Keep away from flammable.
* Keep away from cutting and grinding fluids.
* Do not use in high electromagnetic interference environments.

### 7.2 Robot installation

#### 7.2.1 Installation platform requirements

* When installing the robot, it must be securely fixed to a stable base. The base should be able to withstand at least 10 times the maximum torque of the J1 joint and at least 5 times the weight of the robot arm.
* If the robot arm is installed on a linear axis or a movable platform, the acceleration of the platform should be low, as high acceleration may trigger the robot's collision detection mechanism, causing it to stop.
* The robot arm is connected to the controller via a heavy-duty cable. If the heavy- duty cable needs to pass through a cable routing hole on the installation platform, the hole diameter should not be less than 40mm.
* The CR 30H series robot only supports side cable routing. For side cable routing, the recommended distance between the cable routing hole and the robot base should be no less than L+8D (L: the length after connecting the heavy-duty connector; D: the diameter of the heavy-duty cable): ◦ For CR 30H, L ≈ 150mm, D = 15.6mm, so the recommended distance between the cable routing hole and the robot base should be at least 280mm.

_Figure 7.1 Heavy-duty cable routing diagram_

#### 7.2.2 Installation postures

The following figure illustrates several typical installation postures for robot arms:

**NOTE**

The installation posture at the bottom of the figure is the standard mounting angle. When installing the robot in a non-standard mounting angle, you need to calibrate the mounting angle through DobotStudio Pro after power- on. For details, refer to DobotStudio Pro User Guide.

![Figure 7.1 Heavy-duty cable routing diagram](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTOMKuWoYHnHVArrO5ybG%2Fcr30h-p070-img01.png?alt=media)

_Figure 7.2 Robot arm installation postures_

#### 7.2.3 Robot arm installation

When installing the robot arm, position the mounting holes on the installation platform according to the base dimension. After hoisting the robot arm to the installation platform, secure the arm's base to the platform using bolts. Throughout the installation process, strictly adhere to the following precautions.

**NOTICE**

* During transportation, ensure that the robot is stable and properly secured in its position.
* When hoisting the robot, dedicated personnel must be assigned to support and stabilize the body of the robot arm until all bolts on the base are fully tightened.
* No personnel are permitted to remain or pass under the robot arm during hoisting.
* The robot base must be secured to the installation platform using hex bolts (ISO898-1: 2013, property class: 12.9).
* For wall-mounted or upside-down installations, safety measures must be taken to prevent the robot base from falling.

![Figure 7.2 Robot arm installation postures](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRZU9l5R4VBB88XWhuEaX%2Fcr30h-p071-img01.jpg?alt=media)

Upon unpacking, check the Remove the inner lining of the ① ② attached shipping list to ensure that packaging box, and move the hoist all items are included. If there are so that the hook aligns with the any items missing, please contact central axis of the robot arm and is your supplier. positioned approximately 30–35 cm away from the robot arm. Wrap the sling in a figure-8 winding Attach the factory-supplied slings ③ ④ method as shown below. of the robot arm onto the hook.

![Official manual figure, page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVDgV0JR0AbDAzwveuIxd%2Fcr30h-p072-img01.jpg?alt=media)

![Official manual figure, page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTUO5eVk5UsjY4zaCflbJ%2Fcr30h-p072-img02.jpg?alt=media)

![Official manual figure, page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPLevvsGmunQLQciikQcv%2Fcr30h-p072-img03.jpg?alt=media)

![Official manual figure, page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBra3Pe6wwQOqd2tAjGa8%2Fcr30h-p072-img04.jpg?alt=media)

Control the hoist to slowly lift the Lift the robot arm to its installation ⑤ robot arm (ensure personnel ⑥ platform, align it with the holes, and support the arm throughout the securely fasten the arm in place using entire process). six M10 hex bolts.

#### 7.2.4 Controller installation

Place the controller on a stable platform outside the robot's workspace, and reserve enough space for cable connections and operation. The controller supports both vertical and horizontal installation. Keep the air inlet and outlet unobstructed and leave at least 200mm space on the corresponding sides for proper heat dissipation. Leave 200mm space at the front of the controller for cable wiring.

_Figure 7.3 Vertical installation_

![Figure 7.3 Vertical installation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FISc3gnAOjCa2W5OqtNFr%2Fcr30h-p073-img01.png?alt=media)

![Official manual figure, page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FehACmNmBf8VjZ8iBfmMY%2Fcr30h-p073-img02.jpg?alt=media)

![Official manual figure, page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkXJeNdZErHviGBahquY4%2Fcr30h-p073-img03.jpg?alt=media)

_Figure 7.4 Horizontal installation_

#### 7.2.5 Tool installation

The CR 30H series robot arm's end flange has 6 M8 threaded holes, which can fix the tool to the end of the robot arm. To ensure precise alignment of the tool, the reserved positioning holes can be used with pins for accurate positioning.

![Figure 7.4 Horizontal installation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGL4SDXZvOIeQDEQTpY68%2Fcr30h-p074-img01.png?alt=media)

### 7.3 Cable connection

_Figure 7.5 Cable connection_

. Connect the controller to the robot arm using the heavy-duty cable. ①

**NOTICE**

For the NSF models, specifically the DOBOT CR 30H-Food robot, please ensure that the aviation connector of the heavy-load cable is placed in an enclosed space and not directly exposed to the food production environment.. Insert the emergency stop switch cable into the emergency stop switch interface ② on the controller. During connection, align the white dot on the cable connector with the white dot on the interface, and rotate the blue plastic ring clockwise to secure the connection.. Connect the power cable of the controller to the mains power socket. ③

![Figure 7.5 Cable connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAKf42v5Qp6jtWDRK8o3i%2Fcr30h-p075-img01.jpg?alt=media)

**NOTICE**

* The specifications and installation method of the external cables should comply with local electrical distribution regulations.
* Do not disassemble the robot by yourself, as this may result in electrical leakage.
* Make sure that the device is properly grounded.
* Do not bend the cable excessively, otherwise it may cause poor connections or cable breakage.
* Before connecting external devices, make sure the power outlet of the control system is disconnected. If not disconnected, may result in electric shock or device failure.
* To ensure device and personal safety, use supplied cables.
* After wiring, make sure that there are no loose screws or exposed cables inside the device.
* During normal operation, do not plug or remove the power cables and communication cables.
* The device must be fully wired before powering it on.
* Make sure that the cables are connected correctly to avoid damage to internal modules or external devices.
* Before connecting, check that the insulation and shielding of external cables are not damaged. When removing the heavy-duty cable, if the latch of the heavy-duty plug is too tight to release, refer to the figure below. Use a hex wrench to press against the latch and push it away.

_Figure 7.6 Unlock the heavy-duty plug_

![Figure 7.6 Unlock the heavy-duty plug](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRkMj2JZF6c1ggnh36X7E%2Fcr30h-p076-img01.jpg?alt=media)

### 7.4 Power-on and debugging

_Figure 7.7 Power-on_

After turning on the external mains power, rotate the power switch on the controller ① 90° clockwise to power on the controller. Press and release the round button on top of the controller (If the button is ② inaccessible, use the Remote switch interface instead). Once the indicator lights on both the end of the robot arm and the round button on the controller turn solid blue, test whether the E-stop button functions properly. Then connect to the robot arm via the operation terminal, enable it, and perform jogging operations for debugging purposes. For detailed operation instructions, refer to DobotStudio Pro User Guide.

**NOTICE**

If the robot is being used for the first time or has been left idle for a long period of time, performing high-speed, high-load movements immediately after power-on may trigger false alarms. It is recommended to perform a few minutes of low-speed movements to warm up the robot before normal operation.

![Figure 7.7 Power-on](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F830gcuJ7H2fdfO9JxQZT%2Fcr30h-p077-img01.jpg?alt=media)

## 8. Maintenance

Maintenance and repairing must be performed in compliance with all safety instructions in this document. The purpose of maintenance and repairing is to ensure that the system is kept operational, or to return the system to an operational state in the event of a fault. Repairing includes troubleshooting in addition to the actual repair itself. Repairing must be performed by an authorized system integrator or DOBOT staff. Robots or parts returned to DOBOT should follow the instructions below:

* Remove all parts that do not belong to DOBOT.
* Before returning to DOBOT, please make a backup copy of the files. DOBOT will not be responsible for the loss of programs, data or files stored in robot.
* The robot should move to the package point before returning to DOBOT.

### 8.1 Safety instructions

The following safety procedures and warnings must be observed when operating the robot or controller:

**NOTICE**

* Replace faulty components with new components of the same model or equivalent components approved by DOBOT.
* Reactivate all deactivated safety measures immediately after completing maintenance work.
* Record all repairs and save them in the technical document associated with the robot system.
* Remove the main input cable from the back of the robot to ensure it is fully powered off. Take necessary precautions to prevent others from reconnecting the system power during maintenance.
* Observe ESD regulations when disassembling the robot.
* Prevent water or dust from entering the interior of the robot.

### 8.2 Robot maintenance

To ensure the robot maintains high performance over the long term, regular maintenance checks must be conducted. The personnel in charge of the maintenance must develop a maintenance plan and carry out the necessary tasks. The inspection items are listed in the table below.

_Table 8.1 Inspection items_

Period Inspection Inspection details 3 6 item Daily months months Use a cloth dampened with water or 10% Robot √ ethanol to wipe off any visible dust, dirt, cleaning or oil stains on the robot arm. Refer to the bolt tightening torque table √ Joint bolts and check the torque of exposed bolts at each joint. Tool Check that the tool is securely connected √ mounting to the end flange. bolts Check that there is no abnormal noise or vibration from the joints when the robot is √ Joint module running. After running, touch the joint housing to check for excessive heat. Check that no part of the robot's joints or √ Brake tool falls down when the robot is disabled. Inspect power cables, heavy-duty cables, and IO cables to ensure stable √ Cables connections and check for wear or damage on the cable sheathing. Press the emergency stop switch when Emergency √ the robot is running and observe whether stop switch the robot stops immediately. Remove the side panel of the controller Controller √ with the power disconnected, and clean cleaning any accumulated dust inside.

The bolt tightening torques are shown in Table 8.2.

_Table 8.2 Bolt tightening torques_

Nominal thread Outer hex screw Inner hex bolt Inner hex bolt diameter (joint) (12.9) (rear cover) 3 mm / 0.118 in 2 Nm 2.4 Nm 0.7 Nm 4 mm / 0.157 in 4 Nm 4.5 Nm - 5 mm / 0.197 in 7.5 Nm 9 Nm - 6 mm / 0.236 in 15 Nm 18 Nm - 8 mm / 0.32 in-37 Nm - - 70 Nm (with washer - 10 mm / 0.394 in needed) The tightening torques vary depending on the type of bolt or base material. If not listed in the table, please contact DOBOT technical support engineer.

## 9. Disposal and Environmental Protection

DOBOT robots must be disposed of in accordance with the applicable national laws, regulations and standards. The following symbol indicates that the product must not be disposed of as general waste.

## 10. Warranty

### 10.1 Product warranty

Without prejudice to any claim agreement that the user (customer) may reach with the distributor or retailer, the manufacturer shall guarantee the quality of the products to the customer in accordance with the terms and conditions below: If defects caused by manufacturing and/or improper material occur in a new device and its components within 12 months (15 months at most if the shipping time is included) after the device is put into use, DOBOT shall provide the necessary spare part, and the user (customer) shall offer personnel to replace the spare part, using another part that represents the latest technology level to replace or repair the related part. If the device defects are caused by improper handling and/or failure to follow the relevant information set out in the User Guide, the warranty is invalid. This warranty does not apply to or extend to maintenance (e.g. installation, configuration, software download) performed by the authorized distributer or customer. The user (customer) must provide the purchase receipt and the purchase date as valid evidence for the warranty. Claims under this warranty must be made within two months of the apparent failure to perform the product warranty. The ownership of the device or components that are replaced or returned to DOBOT shall remain with DOBOT. Any other claims arising from or related to the device are not covered by this warranty. Any items in this product warranty do not intend to limit or exclude the legal rights of the customer or to limit or exclude the liability of the manufacturer for the personnel casualty resulting from its negligence. The duration of this product warranty shall not be extended due to the services provided under the product warranty terms. Under the principle of not violating the warranty, DOBOT reserves the right to charge customers for the replacement or maintenance. The foregoing does not imply a change in the burden of proof to the detriment of the client. If there are defects on the device, DOBOT shall not be liable for any damage or loss arising therefrom, including but not limited to loss of production or damage to other production device.

### 10.2 Disclaimer

DOBOT is committed to improve the reliability and performance of its products, and as such reserves the right to upgrade products without prior notice. DOBOT strives to ensure the contents of the User Guide are precise and reliable, but takes no responsibility for any errors or missing information.

## Appendix A Technical Specifications

### A.1 Robot Technical Specifications

DOBOT CR Product name DOBOT CR 30HT DOBOT CR 30H-Food 30H 100kg Weight 102kg (224.87lb) 100kg (220.46lb) (220.46lb) Max payload 30kg (66.14lb) 30kg (66.14lb) 30kg (66.14lb) 1800mm 1800mm 1800mm Working radius (70.87inch) (70.87inch) (70.87inch) Repeated positioning 0.05mm 0.05mm 0.05mm ± ± ± accuracy Torque sensor / 0.1% F.S. / accuracy J1 ±360° J2 ±360° Joint J3 163 163 163 ± ° ± ° ± ° workin g range J4 ±360° J5 ±360° J6 ±360° J1 150°/s J2 150°/s Max J3 200°/s joint speed J4 300°/s J5 300°/s J6 300°/s Power 0/12/24V, average 2A, maximum 3A supply Tool I/O DI 4 DO 4

DOBOT CR Product name DOBOT CR 30HT DOBOT CR 30H-Food 30H RS485 1 IP rating IP65 IP65 IP67 Noise 70dB(A) Temperature range 0 – 50 Power Average ℃500W ℃ Consu mption Max 2500W Installation mode Any angle Cable length from 6m 19.7foot robot to controller （ ） Aluminum alloy, Aluminum alloy, Aluminum alloy, Material stainless steel, ABS, ABS, rubber ABS, rubber food-grade lubricant

**NOTICE**

When the ambient temperature is lower than 10°C, the viscosity of the lubricant increases, which may trigger false alarms if the robot performs high-speed and high- load movements immediately after powering on. It is recommended to first perform a few minutes of low-speed movements to warm up the device.

### A.2 Controller Technical Specifications

Product name DOBOT CC365 400m&#x6D;_&#x31;90m&#x6D;_&#x34;00mm Controller dimensions (15.75inc&#x68;_&#x37;.48inc&#x68;_&#x31;5.75inch) Weight 19kg 41.89lb （ ） Input power Single-phase 200 240V AC, 50 / 60Hz – IO power supply 24V, Max 3A, Max 0.5A for each DI 24 (NPN or PNP) DO 24 (NPN or PNP) Common I/O interface AI 2, Voltage/Current mode, 0V – 10V, 4mA – 20mA AO 2, Voltage/Current mode, 0V – 10V, 4mA – 20mA SI 10 Safety I/O Interface SO 10 Remote power on/off Support Ethernet 2, for TCP/IP, Modbus TCP, Ethernet/IP, Profinet port communication Commu. USB 2, for WiFi module connection, importing/exporting files interface RS485 1, for RS485, Modbus RTU communication Encoder 1, for ABZ incremental encoder Temperature 0 – 50 Environment Humidity ≤ 95%, n℃o cond℃ensation Protection level IP20 (IP54 optional) Cooling method Fan cooling Teaching method PC, APP, teach pendant

## Appendix B Emergency Stop Time and Distance

* J1 axis emergency stop time and distance

![Official manual figure, page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FocE8SYckaiBNfwkZ5vcT%2Fcr30h-p086-img01.png?alt=media)

![Official manual figure, page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRpiYfNuTUHqkSUcdU7Tt%2Fcr30h-p086-img02.png?alt=media)

![Official manual figure, page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEtc1HR5lUXdNipuyg98s%2Fcr30h-p086-img03.png?alt=media)

![Official manual figure, page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdoMKTlyRHxkPN1mgqdMI%2Fcr30h-p086-img04.png?alt=media)

![Official manual figure, page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVcBpZZZ0UV0GusRLKcs7%2Fcr30h-p086-img05.png?alt=media)

![Official manual figure, page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNwZhiKua8nyxZAUI3fFO%2Fcr30h-p086-img06.png?alt=media)

* J2 axis emergency stop time and distance

![Official manual figure, page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F11gJMvZDBSAAsZMjEcEu%2Fcr30h-p087-img01.png?alt=media)

![Official manual figure, page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHA8vKlThGCKNZMrzLNZe%2Fcr30h-p087-img02.png?alt=media)

![Official manual figure, page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F50KsWihKU6CC5u32heWX%2Fcr30h-p087-img03.png?alt=media)

![Official manual figure, page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhziZEjTuN9ZWZq7ue6vE%2Fcr30h-p087-img04.png?alt=media)

![Official manual figure, page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz4wcPi5yVuEBQCcVLtRQ%2Fcr30h-p087-img05.png?alt=media)

![Official manual figure, page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBBIvSXZopNTaLvImxNJ7%2Fcr30h-p087-img06.png?alt=media)

* J3 axis emergency stop time and distance

![Official manual figure, page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq7OnVvbKf4p52gN6txOl%2Fcr30h-p088-img01.png?alt=media)

![Official manual figure, page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqHQWdqnsE0MtIkNKnFCb%2Fcr30h-p088-img02.png?alt=media)

## Appendix C Normal Stop Time and Distance

* J1 axis normal stop time and distance

![Official manual figure, page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUtss8BWYdsxyB0q18eYl%2Fcr30h-p089-img01.png?alt=media)

![Official manual figure, page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FypaLQPhc3RhlyIgep7dk%2Fcr30h-p089-img02.png?alt=media)

![Official manual figure, page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcB6Irbm6YdKBi6tmOGaL%2Fcr30h-p089-img03.png?alt=media)

![Official manual figure, page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUVFJCTVbdqrP1onANvhW%2Fcr30h-p089-img04.png?alt=media)

![Official manual figure, page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI9vCjIN2c4AdvOKpvLP0%2Fcr30h-p089-img05.png?alt=media)

![Official manual figure, page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9QDIkr0VOnnaYUsuiuic%2Fcr30h-p089-img06.png?alt=media)

* J2 axis normal stop time and distance

![Official manual figure, page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZRZdyeYVPvfMfFGz6daA%2Fcr30h-p090-img01.png?alt=media)

![Official manual figure, page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FibpuCnu3jdw6JZcg7lbY%2Fcr30h-p090-img02.png?alt=media)

![Official manual figure, page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3r4XtANHdtQuDVwmYfZ1%2Fcr30h-p090-img03.png?alt=media)

![Official manual figure, page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6zfdtySuEt94mKSQSc65%2Fcr30h-p090-img04.png?alt=media)

![Official manual figure, page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJO7CZXxC5JSp4iscltIm%2Fcr30h-p090-img05.png?alt=media)

![Official manual figure, page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FklQTa009QqB8FVhP2juw%2Fcr30h-p090-img06.jpg?alt=media)

* J3 axis normal stop time and distance

![Official manual figure, page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQgbuHusJOQSqWR2Siufz%2Fcr30h-p091-img01.png?alt=media)

![Official manual figure, page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhiQgv5btOW7tith61jzS%2Fcr30h-p091-img02.png?alt=media)
