---
description: >-
  Hardware guide for DOBOT CR5AP, CR10AP, and CR20AP IP68 collaborative robots,
  including safety, specifications, interfaces, installation, maintenance, and
  compliance.
---

# DOBOT CRA-IP68 Series Hardware User Guide

## DOBOT CR5AP IP68 Palletizing Robot

{% embed url="https://openelab.io/products/dobot-cr5ap-ip68-palletizing-robot" %}

## DOBOT CR10AP IP68 Palletizing Robot

{% embed url="https://openelab.io/products/dobot-cr10ap-ip68-palletizing-robot" %}

## DOBOT CR20AP IP68 Palletizing Robot

{% embed url="https://openelab.io/products/dobot-cr20ap-ip68-palletizing-robot" %}

## Contents

* Preface
* 1\. Safety
* 2\. Product Introduction
* 3\. Product Features
* 4\. Mechanical specifications
* 5\. Electrical Characteristics
* 6\. Transportation
* 7\. Installation and Use
* 8\. Maintenance
* 9\. Disposal and Environmental Protection
* 10\. Warranty
* 11\. Compliance Statements
* Appendix Technical Specifications
* Appendix A Robot arm technical specifications
* Appendix B Controller technical specifications

Copyright © SHENZHEN DOBOT CORP LTD 2026. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as "DOBOT"). Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. DOBOT makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will DOBOT be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. DOBOT shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot.

### SHENZHEN DOBOT CORP LTD

Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

### DOBOT Europe GmbH

Address: Waldeckerstraße 11 64546 Mörfelden-Walldorf, Contact: Lang Xulin, lang@dobot-robots.com

## Preface

This document describes the functions, technical specifications, installation guide of DOBOT CRA-IP68 series robot arm, making it easy for users to fully understand and use it.

### Scope of application

Robot arm:

* DOBOT CR5AP
* DOBOT CR10AP
* DOBOT CR20AP

You can find the model of robot arm on the right-top corner of the nameplate on the robot base. The figure below takes CR5A as an example. Controller:

* DOBOT CC262
* DOBOT CC263

You can find the controller information on the nameplate. The figure below takes CC262 as an example.

![Official manual figure, page 3](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F80SwxKQFGCgKmKzVJCZa%2Fcra-ip68-p003-img01.png?alt=media)

![Official manual figure, page 3](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM2kDzZPhn3jUZY5WoMs1%2Fcra-ip68-p003-img02.png?alt=media)

### Important safety notice

The robot is a semi-finished machinery, so a risk assessment must be conducted after each installation. Please strictly adhere to all safety regulations outlined in Chapter 1.

### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

### Related documents

Document Description Download link DobotStudio Pro User Explains how to use the robot Guide control software, DobotStudio Pro. Describes how to use the secondary development interface based on DOBOT TCP\_IP Remote TCP/IP protocol. In addition to the Control Interface Guide document, you can also access multi-language development DEMOs from Github. DOBOT Bus Click Download Introduces the usage of the robot's Communication Protocol Center, and search bus communication functions Guide by document name (EtherNetIP/Profinet). (EtherNetIP\_Profinet) or filter by product series. Explains how to use the Teach DOBOT Cobot Teach Pendant that accompanies the Pendant User Guide collaborative robot. Explains how to use the VX500 DOBOT VX500 Smart Smart Camera with the CRA-IP68 Camera User Guide series robot. DOBOT DSC Controller Explains how to use DSC controller. User Guide

### Revision history

Date Version Revised content 2026-08-21 V1.0 The first release

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

Reference Phase Description section Before installing and using the robot, read the Safety Learning safety section thoroughly and strictly follow the 1. Safety safety guidelines provided.

2. Product

Introduction

3. Product

Product Understand the components, features, and Features Understanding detailed technical specifications of the product. Appendix Technical Specifications Space planning: Understand the mechanical specifications and installation environment 4. Mechanical requirements of the robot arm and controller, Specifications Planning and plan the installation space by considering 7.1 Installation the end tool's mechanical specifications and environment installation method.

Reference Phase Description section Electrical planning: Read the relevant sections to understand the function and location of the 5. Electrical robot's electrical interfaces, and plan the Features electrical connections and wiring. Unpack the robot. 7.2 Unpacking Transport the robot arm and controller to their

6. Transportation

respective installation locations.

4. Mechanical

Install the robot arm, controller, and end tools in Specifications Installation place. 7.3 Robot installation

5. Electrical

Features Connect to the robot. 7.4 Cable connection Power-on and Power on the robot, then refer to DobotStudio 7.5 Power-on and Use Pro User Guide to configure and use the robot. debugging Perform routine maintenance and care of the Maintenance robot while strictly following the safety 8. Maintenance instructions.

9. Disposal and

Follow the instructions in this document for Disposal Environmental deactivating and disposing of the robot. Protection

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

DOBOT CRA-IP68 series robots are collaborative robots only for general industrial use, such as processing or delivering products or parts through end tools. DOBOT CRA-IP68 series robots are equipped with special safety mechanisms including collision detection. These mechanisms are purposely designed for human-robot collaboration, but only intended for non-hazardous applications after risk assessment, where tools, products, environment and other machines have been demonstrated to be incapable of significant risk through application-specific risk assessments. Any use or application deviating from intended use is deemed to be impermissible misuse, including, but is not limited to:

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
4. Sprains or fractures resulting from collisions between heavy payloads on the robot’s

end and hard surfaces.

5. Consequences of loose bolts securing the robot or end tool.
6. Consequences of items falling off the end tool.
7. Consequences of incorrectly pressing the emergency stop button of other equipment.
8. Consequences of unauthorized changes to the safety function configurations.

For information on emergency stop time and distance, please refer to the Emergency stop time and distance section.

### 1.4 Pre-use assessment

Before using the robot for the first time or after any modifications are made, testing must be conducted to ensure that all safety inputs and outputs are correctly connected and functioning properly:

1. Test whether the emergency stop button and user emergency stop input can trigger

an emergency stop.

2. Test whether the protective stop input can halt the robot’s motion. If a protective stop

reset input is configured, test whether this input must be activated before the robot can resume operation.

3. If a reduced mode input is configured, test whether this input can switch the robot to

reduced mode (reduced-speed operation).

4. If a teach pendant is optionally equipped and the three-position enabling switch is

configured, test whether the robot can only be enabled when the three-position switch is in the center position in manual mode.

5. Test whether the system connected to the emergency stop status output can detect

the output change and respond accordingly.

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

Indicates a situation that, if not avoided, could result in personnel injury or damage to the equipment.

**NOTICE For items marked with such signs, depending on the specific**

situation, there is sometimes a possibility of significant consequences

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
* Make sure that the unpacking area is free of obstacles to allow staff to evacuate quickly in case of emergencies.
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

DOBOT robots have undergone rigorous safety design and testing, and a series of safety measures have been implemented to minimize risks during installation, commissioning, operation, and maintenance. However, certain residual risks may remain and should be handled with caution during operation:

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

Removing the fixing screws from robot base Refer to Robot arm installation. After removing the fixing screws from the robot base, you can move the robot arm to free the trapped person.

**WARNING**

* Disconnect the robot arm from the power before removing the screws.
* Hold the robot throughout the process of removing the screws and moving the robot arm.

![Figure 1.1 Manually release the brakes](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fzkn4nYPkjT3xTtOFr7cU%2Fcra-ip68-p018-img01.png?alt=media)

## 2. Product Introduction

### 2.1 Overview

The main components of the robot system include:

_Figure 2.1 Robot overview_

Robot arm: Six-axis robot arm, main moving parts. Controller: Core computing and electrical components. An IP54 protective cover is configured. E-Stop: Connected to the controller to enable the emergency stop function. Heavy-duty cable: Used to connect the robot arm to the controller. Additionally, you can opt for an operation terminal (e.g., PC, tablet, or teach pendant) to install and run the robot's control software.

_Figure 2.2 Operation terminal_

![Figure 2.1 Robot overview](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FE7Ita8KYMXutWumvEUfj%2Fcra-ip68-p019-img01.png?alt=media)

![Figure 2.2 Operation terminal](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTLqzfJVxKegYFvS7Dh1j%2Fcra-ip68-p019-img02.png?alt=media)

### 2.2 Robot arm

#### 2.2.1 Composition

The CRA-IP68 series robot arm includes 6 rotary motion joints, and 2 connecting rods (upper arm and forearm). The robot base is equipped with a heavy-duty interface. The main differences between the series lie in the placement and function of end button and indicators.

* CR5AP and CR10AP: Equipped with end button and indicators. Additionally, the tool flange includes an aviation connector on its side.

_Figure 2.3 CR10AP robot arm_

![Figure 2.3 CR10AP robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBCjBrCpzEAyV3NGCutBz%2Fcra-ip68-p020-img01.jpg?alt=media)

* CR20AP: Equipped with two ring-shaped indicators: one located on the J1 rear cover and the other on the side of the tool flange. The rear cover of J6 does not have a button panel, but the side of the tool flange is equipped with two buttons and two aviation connectors.

_Figure 2.4 CR20AP robot arm_

#### 2.2.2 End button and indicators

* CR5AP and CR10AP: Configuration of the end button and indicators is illustrated in the figure below.

_Figure 2.5 End buttons and indicators (CR5AP and CR10AP)_

![Figure 2.4 CR20AP robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fuk8ClmComw0fqtGQyE7k%2Fcra-ip68-p021-img01.jpg?alt=media)

![Figure 2.5 End buttons and indicators (CR5AP and CR10AP)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHT8DluS8lEvpfshLmYQb%2Fcra-ip68-p021-img02.jpg?alt=media)

* CR20AP: Configuration of the end button and indicators is illustrated in the figure below.

_Figure 2.6 End button and indicators (CR20AP)_

Indicator meanings: Indicator color Status Description Blue Fast flashing The robot is starting up Blue Steady on The robot is powered on but not enabled Green Steady on The robot is enabled but not running Automatic running status (project Green Slow flashing debugging/running/pause, motion commands except TCP jog mode) Single running status (Jog/"Run To" function in Green Fast flashing software)/Drag mode status Red Slow flashing Joint brake switched on in disabled status Red Steady on The robot is in alarm status Yellow Steady on Collision detected

**NOTE**

The quick flashing frequency is 5 Hz (0.2s per cycle), and the slow flashing frequency is 1.25 Hz (0.8s per cycle).

![Figure 2.6 End button and indicators (CR20AP)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQHzvU6IvZt2g45kwBrLO%2Fcra-ip68-p022-img01.jpg?alt=media)

End button function:

* Hand-guiding button (CR5AP and CR10AP): When the robot arm is enabled, long-press the hand-guiding button, and release it to enter the drag-teaching mode. After dragging the robot arm to the teaching point, short-press the hand- guiding button, and release it to exit the drag-teaching mode.
* Hand-guiding button (CR20AP): When the robot arm is enabled, press the hand- guiding button to enter the drag-teaching mode. After dragging the robot arm to the teaching point, release the hand-guiding button to exit the drag-teaching mode.

**NOTE**

Releasing the button within 1.5 seconds is considered a short press, while holding it for more than 1.5 seconds is considered a long press.

### 2.3 Controller

The CRA-IP68 series robot arms need to be used with a controller. The controller model for CR20AP robot arm is CC263, and the controller model for CR5AP and CR10AP robot arms is CC262. For details on its electrical interfaces and switches, see Electrical Characteristics.

_Figure 2.7 Controller appearance_

![Figure 2.7 Controller appearance](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm3nUgAIMRRun7yFk5a1F%2Fcra-ip68-p023-img01.jpg?alt=media)

### 2.4 Operation terminal

The CRA-IP68 series robot arms can be optionally equipped with a teach pendant for control. For more information, please refer to DOBOT Cobot Teach Pendant User Guide. Additionally, the CRA-IP68 series robot arms support control via PC and mobile devices, as shown in Table 2.1.

_Table 2.1 Operation terminal specifications_

Terminal type PC Tablet (Android) Operating Windows 10 (64-bit) 1809 or Android 10 and above system above Control DobotStudio Pro (V4.0 and above) software

* CPU: 64-bit Intel or AMD processor (SSE4.2 or later, 2.9GHz or higher)
* Memory: 16G • CPU: 4-core, above

2.0GHz

* Storage: 128GB (at least 4GB

Recommended available) • RAM: 4GB configuration

* Network card: Gigabit-NIC • Storage: 32GB
* Graphics card: 4GB, • Screen: 8-inch

DirectX12 support

* Display: 1920x1080 or higher resolution Communication LAN/WiFi WiFi mode When purchasing a CRA-IP68 series robot arm, you can request an optional Android tablet, or use self-prepared operation terminal as long as it meets or exceeds the recommended specifications in Table 2.1.

## 3. Product Features

### 3.1 Coordinate system

#### 3.1.1 Joint coordinate system

The joint coordinate system is determined based on all motion joints. All joints are rotational joints, as shown in Figure 3.1.

_Figure 3.1 Joint coordinate system_

#### 3.1.2 User coordinate system

The user coordinate system is a user-defined coordinate system based on the workbench or workpiece. The origin and axis directions can be defined as needed to measure points within the workspace and arrange tasks conveniently. The default user coordinate system is determined based on the center point of the robot base, and Y+ direction is the direction that the heavy-duty socket faces, as shown in Figure 3.2.

_Figure 3.2 User coordinate system_

![Figure 3.1 Joint coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FG00iH6iIiUZqfPBjXOTU%2Fcra-ip68-p025-img01.png?alt=media)

![Figure 3.2 User coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgrDpVdCD8dSc1t4wLPqp%2Fcra-ip68-p025-img02.png?alt=media)

#### 3.1.3 Tool coordinate system

The tool coordinate system defines the position and posture of the Tool Center Point (TCP). Its origin and direction change dynamically based on the position and angle of the end tool. The default tool coordinate system is determined based on the center point of the end flange, with the Y+ direction facing opposite to the aviation connector (for CR20AP, it is opposite to the X1 aviation connector), as shown in Figure 3.3.

_Figure 3.3 Tool coordinate system_

### 3.2 Home posture

When the robot arm is in the upright position as shown in Figure 3.1, all joint angles are set to 0 degrees. This posture is called the home posture. Each joint of the robot arm is marked with a home-posture sticker (transparent, with a blue alignment line), as shown in the figure below. When a joint is at 0 degrees, the stickers on both sides of the joint will be perfectly aligned.

_Figure 3.4 Home-posture sticker_

![Figure 3.3 Tool coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSD2JzqMDfVZwe9W6ScGV%2Fcra-ip68-p026-img01.png?alt=media)

![Figure 3.4 Home-posture sticker](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaBosD0PL8RVhTACKn2OE%2Fcra-ip68-p026-img02.png?alt=media)

If the home posture changes due to component replacement or collision, you can move the robot arm to a state where all the home-posture stickers of each joint are aligned. Then calibrate the home posture through DobotStudio Pro.

### 3.3 Singularities

When the robot moves in a linear or arc trajectory and approaches certain specific postures, an alarm will be triggered, and the robot will stop movement. These postures are referred to as singular positions or singular points.

**NOTICE**

* Joint motion is not affected by singular positions.
* Avoid stopping the robot near a singularity using drag mode or joint motion and then attempting linear or arc motion. The CRA-IP68 series robot arms have three types of singularities, as described below.

#### 3.3.1 Shoulder singularity

The singularity occurs when the intersection of the J5 and J6 axes is located in the plane formed by the J1 and J2 axes. This typically happens in the cylindrical space directly above or below the robot. Refer to the motion range in the Mechanical Specifications chapter for details about each model. As shown in the figure below.

_Figure 3.5 Shoulder singularity_

![Figure 3.5 Shoulder singularity](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVwhwqXyhhZYUHbzj9XAH%2Fcra-ip68-p027-img01.png?alt=media)

#### 3.3.2 Elbow singularity

The singularity occurs when J3=0°±2°, where the upper arm and forearm are parallel. As shown in the figure below.

_Figure 3.6 Elbow singularity_

#### 3.3.3 Wrist singularity

The singularity occurs when J5=0°±2°, where the J4 axis and J6 axis are parallel. As shown in the figure below.

_Figure 3.7 Wrist singularity_

![Figure 3.6 Elbow singularity](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOenvEuhss23oQO23KI6Z%2Fcra-ip68-p028-img01.png?alt=media)

![Figure 3.7 Wrist singularity](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4q9LJTfrDOf6J5RoMgCu%2Fcra-ip68-p028-img02.png?alt=media)

#### 3.3.4 Recommendations for avoiding singularities

● Switch the motion type to joint motion when near a singularity. ● Add transition points in the trajectory to bypass the singularity. ● Adjust the installation posture of the robot to avoid singularities in the path. For example, switch from standard-angle mounting to hoisting or side mounting. ● Modify the length of the end tool. ● Adjust the installation angle of the end tool to bypass singularities in the path.

### 3.4 Emergency stop time and distance

When J1 to J3 axes operate at 100% speed, with maximum payload and maximum reach, the stop time and stop distance for each joint upon triggering an emergency stop are listed in the table below. For the J1 axis, testing is conducted by moving horizontally, meaning the rotational axis is perpendicular to the ground.

_Figure 3.8 J1 Emergency stop test_

For the J2 and J3 axes, testing follows a vertical trajectory, meaning the rotational axis is parallel to the ground. The emergency stop is triggered while the robot is moving downward.

_Figure 3.9 J2 Emergency stop test_

![Figure 3.8 J1 Emergency stop test](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FITKnPrYAgQU74rhVoHVj%2Fcra-ip68-p029-img01.jpg?alt=media)

![Figure 3.9 J2 Emergency stop test](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fbwq9x6VIro0DDzAWeAN1%2Fcra-ip68-p029-img02.jpg?alt=media)

_Figure 3.10 J3 Emergency stop test_

The table below provides reference data for selected models.

_Table 3.1 Emergency stop time and distance_

Emergency Stop Time / Distance Robot arm J1 J2 J3 CR5AP 351ms/389.94mm 239ms/366.58mm 248ms/205.14mm CR10AP 306ms/420.46mm 242ms/411.42mm 252ms/293.75mm CR20AP 448ms/836.23mm 456ms/835.95mm 272ms/338.54mm

![Figure 3.10 J3 Emergency stop test](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLyQwqbNTeDpwCCJLT5u1%2Fcra-ip68-p030-img01.jpg?alt=media)

## 4. Mechanical specifications

All dimensions in this chapter are in millimeters (mm).

### 4.1 CR5AP mechanical specifications

#### 4.1.1 CR5AP dimensions and workspace

When selecting the installation position for the robot, you must consider the cylindrical space directly above and below the robot, and try to avoid moving the tool into this cylindrical space. As doing so may cause the joints to rotate too fast even when the tool moves slowly, resulting in low work efficiency and making risk assessment more difficult.

_Figure 4.1 CR5AP dimensions and workspace_

![Figure 4.1 CR5AP dimensions and workspace](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpeHfpgiyaM3pPa8oCjAj%2Fcra-ip68-p031-img01.png?alt=media)

![Official manual figure, page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC9MXyDaPxdQsx4ACg982%2Fcra-ip68-p031-img02.png?alt=media)

#### 4.1.2 CR5AP base mounting dimensions

_Figure 4.2 CR5AP base mounting dimensions_

#### 4.1.3 CR5AP end flange dimensions

The flange design conforms to ISO 9409-1-50-4-M6.

_Figure 4.3 CR5AP end flange dimensions_

![Figure 4.2 CR5AP base mounting dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9iivxUcSCLKnfN4cS9lo%2Fcra-ip68-p032-img01.png?alt=media)

![Figure 4.3 CR5AP end flange dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fhg07Hr4Fl2Ykf1vAjSJT%2Fcra-ip68-p032-img02.png?alt=media)

![Official manual figure, page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fl33MQCgUXhbIi7vq7pgP%2Fcra-ip68-p032-img03.png?alt=media)

#### 4.1.4 CR5AP end load curve

The origin of the coordinate system for the end load curve is the center of the robot's end flange. X and Y represent the offset distance of the load’s center of mass from the flange center along the X and Y axes. The radial distance (r) is calculated as:. This r-value corresponds to the vertical axis (Y-axis) in the load curve graph, labe2led a2s X, Y \[cm]. The horizontal axis (X-axis) represents Z \[cm], which is the distanrc=e f√ro𝑋𝑋m +th𝑌𝑌e load’s center of mass to the flange along the Z direction. You can evaluate the working condition of the robot according to the statistical results. For example, if the load is 2.8kg, X = 6cm, Y = 8cm, Z = 5cm, and you can get r = 10cm. The judgment steps are as follows:

* According to , calculate r = 10cm.
* Select the appropriat 2 e cur 2 ve based on the load weight. Since 2.8kg is close to r=√𝑋𝑋 +𝑌𝑌 3kg, use the 4kg curve as a reference.
* Locate the (r, Z) = (10cm, 5cm) point in the load curve graph and compare it with the 3kg curve. If the point is below the curve, the load is within the robot’s operational range (selection valid). If the point is above the curve, the load exceeds the robot’s limit (selection invalid). In this example, the point is below the curve, indicating that the selected load is acceptable, and the robot can operate safely under this condition.

_Figure 4.4 CR5AP end load curve_

![Figure 4.4 CR5AP end load curve](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FETfKE8jV6owZpXQHejcj%2Fcra-ip68-p033-img01.png?alt=media)

### 4.2 CR10AP mechanical specifications

#### 4.2.1 CR10AP dimensions and workspace

When selecting the installation position for the robot, you must consider the cylindrical space directly above and below the robot, and try to avoid moving the tool into this cylindrical space. As doing so may cause the joints to rotate too fast even when the tool moves slowly, resulting in low work efficiency and making risk assessment more difficult.

_Figure 4.5 CR10AP dimensions and workspace_

![Figure 4.5 CR10AP dimensions and workspace](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOdfV3i7xmqiGF5fWfn0S%2Fcra-ip68-p034-img01.png?alt=media)

![Official manual figure, page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCd2Xc0Z0gXKKUKmqdGg6%2Fcra-ip68-p034-img02.png?alt=media)

#### 4.2.2 CR10AP base mounting dimensions

_Figure 4.6 CR10AP base mounting dimensions_

#### 4.2.3 CR10AP end flange dimensions

The flange design conforms to ISO 9409-1-50-4-M6.

_Figure 4.7 CR10AP end flange dimensions_

![Figure 4.6 CR10AP base mounting dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5cjnvIEpOJ0OLQgQjoF3%2Fcra-ip68-p035-img01.png?alt=media)

![Figure 4.7 CR10AP end flange dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBiOLwfiWloqjCm8qmEpM%2Fcra-ip68-p035-img03.png?alt=media)

#### 4.2.4 CR10AP end load curve

The origin of the coordinate system for the end load curve is the center of the robot's end flange. X and Y represent the offset distance of the load’s center of mass from the flange center along the X and Y axes. The radial distance (r) is calculated as:. This r-value corresponds to the vertical axis (Y-axis) in the load curve graph, r= labe2led a2s X, Y \[cm]. The horizontal axis (X-axis) represents Z \[cm], which is the distance √fro𝑋𝑋m +th𝑌𝑌e load’s center of mass to the flange along the Z direction. You can evaluate the working condition of the robot according to the statistical results. For example, if the load is 3.8kg, X = 6cm, Y = 8cm, Z = 5cm, and you can get r = 10cm. The judgment steps are as follows:

* According to , calculate r = 10cm.
* Select the appropriat 2 e cur 2 ve based on the load weight. Since 3.8kg is close to r=√𝑋𝑋 +𝑌𝑌 4kg, use the 4kg curve as a reference.
* Locate the (r, Z) = (10cm, 5cm) point in the load curve graph and compare it with the 4kg curve. If the point is below the curve, the load is within the robot’s operational range (selection valid). If the point is above the curve, the load exceeds the robot’s limit (selection invalid). In this example, the point is below the curve, indicating that the selected load is acceptable, and the robot can operate safely under this condition.

_Figure 4.8 CR10AP end load curve_

![Figure 4.8 CR10AP end load curve](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkoVBujdFM6Si2Z9Hezrg%2Fcra-ip68-p036-img01.png?alt=media)

### 4.3 CR20AP mechanical specifications

#### 4.3.1 CR20AP dimensions and workspace

When selecting the installation position for the robot, you must consider the cylindrical space directly above and below the robot, and try to avoid moving the tool into this cylindrical space. As doing so may cause the joints to rotate too fast even when the tool moves slowly, resulting in low work efficiency and making risk assessment more difficult.

_Figure 4.9 CR20AP dimensions and workspace_

![Figure 4.9 CR20AP dimensions and workspace](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBuSnL3P0xvpDGVpDn3AF%2Fcra-ip68-p037-img01.png?alt=media)

#### 4.3.2 CR20AP base mounting dimensions

_Figure 4.10 CR20AP base mounting dimensions_

#### 4.3.3 CR20AP end flange dimensions

_Figure 4.11 CR20AP end flange dimensions_

![Figure 4.10 CR20AP base mounting dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEZg6cXlQwjJGMN2Yftwt%2Fcra-ip68-p038-img01.png?alt=media)

![Figure 4.11 CR20AP end flange dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFRHFRclAgSZVXGzePojw%2Fcra-ip68-p038-img02.png?alt=media)

#### 4.3.4 CR20AP end load curve

The figure below illustrates the load curve for CR20AP when installed at the standard mounting angle. The horizontal axis represents the offset distance (eccentricity), which is the distance from the load’s center of mass to the center of the CR20AP end flange, measured in millimeters (mm). The vertical axis represents the load weight, measured in kilograms (kg). The blue line indicates the maximum allowable load for CR20AP at different offset distances:

* When the offset distance is less than 131mm, the maximum load is 20kg.
* When the offset distance is greater than 131mm, the maximum load decreases as the distance increases.
* When the offset distance is 623mm, the maximum load is 6.7kg.

_Figure 4.12 CR20AP end load curve_

![Figure 4.12 CR20AP end load curve](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdV2Up56eeTsH6ghGRWkn%2Fcra-ip68-p039-img01.png?alt=media)

### 4.4 Controller dimensions

#### 4.4.1 CC262 dimensions

The right figure shows the length after the protective cover is installed. Dimensions not labeled remain the same as when the protective cover is not installed.

_Figure 4.13 CC262 dimensions_

#### 4.4.2 CC263 dimensions

The right figure shows the length after the protective cover is installed. Dimensions not labeled remain the same as when the protective cover is not installed.

_Figure 4.14 CC263 dimensions_

![Figure 4.13 CC262 dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FehnZplkCn0ZX2TxYF9FK%2Fcra-ip68-p040-img01.png?alt=media)

![Figure 4.14 CC263 dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiEYRwSeBMUo8Gew34ysb%2Fcra-ip68-p040-img02.png?alt=media)

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

The electrical interfaces of the controller are all on the front panel, as shown in the figure below (CC262 as an example). The interface layout of CC263 is mostly identical to CC262, except for differences in the power interface and switch design. No Name Description. Controller switch • After the controller is powered on, press the button for 0.5s and release it, the controller will be turned on.

* When the controller is started, press the button for 3s and release it, the controller will be turned off and the robot arm will be powered off.

**NOTE**

This is a self-resetting switch and does not support automatic startup when the controller is powered on. However, you can use the remote switch interface to realize remote control of startup or shutdown. Teach Pendant See Teach Pendant and E-Stop interface for details. 2 and E-Stop interface WiFi antenna For wireless connection to a PC or tablet for debugging.

![Official manual figure, page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuoeEU4LkNoHvPerb6wjh%2Fcra-ip68-p042-img01.png?alt=media)

No Name Description. 4 USB interface For importing/exporting files. LAN interface Default IP address:

* LAN1: 192.168.5.1
* LAN2: 192.168.200.1

For connecting to a PC for debugging or to external devices that support TCP/IP or Modbus TCP protocols. Only LAN1's IP address can be modified via DobotStudio Pro. EtherCAT interface Internally reserved interface, not open for external use. I/O interface panel Used for connecting external devices. See I/O interface panel for details. Heavy-duty For connecting to the robot, providing power and interface enabling communication with the robot. 9 AC power switch For powering on/off the controller. AC power For connecting to 100–240V AC single-phase power interface supply.

#### 5.2.2 Teach Pendant and E-Stop interface

This interface is used to connect to the dedicated teach pendant (optional) or an emergency stop switch. The pin definitions are as follows. Pin Definition 1 DC 24V 2 DC 0V 3 DC 24V

![Official manual figure, page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqOKO3HHEf2E54Nt6sbNW%2Fcra-ip68-p043-img01.png?alt=media)

Pin Definition Emergency stop circuit 1 input (normally closed) 5 DC 24V Emergency stop circuit 2 input (normally closed) Dedicated for communication with 7 – 15 the Teach Pendant

#### 5.2.3 I/O interface panel

The controller contains an I/O interface panel for connecting to external devices such as air pump, PLC, etc. The I/O interface panel supports: 24 digital inputs, 24 digital outputs, 2 analog outputs, 2 analog inputs, 1 incremental encoder input, 1 RS485 interface, 1 CAN interface, 10 safety inputs, and 10 safety outputs. All interfaces with the same silkscreen label have common functions, so any available interface with the same label can be used for wiring. The interfaces connected by green lines in the figure below are factory short-circuited by default.

_Figure 5.1 Controller I/O interface_

Silkscreen Definition I/O 5V Internal power +5V and 0V, mainly used for powering pulse encoders. I/O 0V A+/A- Pulse encoder interface, used for receiving encoder signals. B+/B- See Encoder interface for details. Z+/Z- RP 24V Remote switch interface, used for remote power on/off.

![Figure 5.1 Controller I/O interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtreoCMH8E3eCwkGnQfFf%2Fcra-ip68-p045-img01.png?alt=media)

Silkscreen Definition See Remote switch interface for details. ON OFF I/O 24V I/O power +24V and 0V. The power source can be configured for internal or external power supply based on wiring methods. I/O 0V See I/O interface power for details. AI1 – AI2 Analog input/output interface, used for connecting external devices that operate with analog signals. AO1 – AO2 See Analog I/O interface for details. DI1 – DI24 Digital input/output interface, used for connecting external devices that operate with digital signals. DO1 – DO24 See Digital I/O interface for details. Digital input common terminal interface, used to switch DI signal COM1 – COM2 types. 24V Internal power +24V and 0V, used for powering I/O interfaces or external devices. 0V 485A RS485 interface, mainly used for Modbus RTU communication. See RS485 interface for details. 485B FG Used for grounding encoders or RS485, and CAN interfaces. CAN\_H CAN bus interface (Internally reserved, not open for external use). CAN\_L SI 24V Safety I/O power +24V and 0V, used for powering external safety devices. SO 0V SI1 – SI10 Safety input/output interface, used for connecting external safety devices. See Safety I/O interface for details. SO1 – SO10

#### 5.2.4 I/O interface power

The I/O interface can be powered by either an internal or an external 24V power supply.

_Table 5.1 I/O power supply specifications_

Interface Parameter Min value Typical Max value Unit Internal 24V power supply Voltage 23 24 25 V 24V–0V Current 0-3 A External 24V power supply Voltage 20 24 29 V External power supply Current 0-6 A When using the internal power supply, short-circuit the 0V and 24V terminals to the nearest I/O 0V and I/O 24V interfaces, as shown in the figure below.

_Figure 5.2 I/O connected to internal power supply_

If a higher total output current is required, an external 24V power supply can be connected, as shown in the figure below. The external and internal power supplies are isolated from each other and do not interfere with one another.

_Figure 5.3 I/O connected to external power supply_

![Table 5.1 I/O power supply specifications](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQorlShoIh7RRR06OrXvA%2Fcra-ip68-p047-img01.png?alt=media)

![Figure 5.2 I/O connected to internal power supply](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1IsX7gz6QLuYEYZyf3o0%2Fcra-ip68-p047-img02.png?alt=media)

**NOTE**

All subsequent sections assume that the I/O power supply is properly connected, and the wiring details for I/O power will not be repeated.

#### 5.2.5 Digital I/O interface

_Table 5.2 Digital I/O interface specifications_

Interface Parameter Min value Typical Max value Unit Digital input Voltage -3-30 V OFF range -3-5 V DIx ON range 15-30 V Current (ON range) 4-7 mA Type-NPN/PNP - - Digital output Current 0-0.5 A Voltage drop 0-0.5 V DOx Current leakage 0-0.1 mA Type-NPN/PNP - - The DI interface must be connected to the COM interface, which can switch signal types (PNP or NPN). COM1 is used for DI1 – DI12. COM2 is used for DI13 – DI24. These configurations can be set independently. For DI connected to a simple switch, the wiring is shown below (left figure: PNP wiring, right figure: NPN wiring). You can choose the appropriate wiring method based on the on- site requirements.

_Figure 5.4 DI connected to simple switch_

For DI connected to an external PNP three-wire sensor, the wiring is shown below. If the sensor is powered by the controller, short-circuit the corresponding COM port to I/O 0V (left figure below). If the sensor is powered by an external supply, connect the COM port to 0V of the external power supply (right figure below).

_Figure 5.5 DI connected to PNP input_

For DI connected to an external NPN-type DO, the wiring is shown below. If the external DO is powered by the controller, short-circuit the corresponding COM port to I/O 24V (left figure below). If the external DO is powered by an external supply, connect the COM port to 24V of the external power supply (right figure below).

![Figure 5.4 DI connected to simple switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2nMQgVbsvTqaLBBxq8Z7%2Fcra-ip68-p049-img01.png?alt=media)

![Figure 5.5 DI connected to PNP input](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH7XdGyZzSPsyecjTSAac%2Fcra-ip68-p049-img02.png?alt=media)

_Figure 5.6 DI connected to NPN input_

DO is set to PNP by default but can be configured to NPN via the software (DobotStudio Pro). If the software setting and the actual wiring method do not match (e.g., PNP is set in DobotStudio Pro, but the load wiring is NPN), the load will not work properly. When DO is set to PNP, the wiring for connecting to an external load is shown below.

_Figure 5.7 PNP DO connected to external load_

When DO is set to NPN, the wiring for connecting to an external load is shown below.

![Figure 5.6 DI connected to NPN input](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkeedT7IChXEkJsWE202p%2Fcra-ip68-p050-img01.png?alt=media)

![Figure 5.7 PNP DO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQbkf5EpPDzmq60mPfrjN%2Fcra-ip68-p050-img02.png?alt=media)

_Figure 5.8 NPN DO connected to external load_

To ensure stable operation, it is recommended to maintain a minimum interval of 15ms between two DI signals or two DO signals.

**NOTE**

When driving inductive loads, a protection diode must be connected in parallel to prevent burnout of the output circuit.

![Figure 5.8 NPN DO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCnKCD2FSk9gwLLKamySF%2Fcra-ip68-p051-img01.png?alt=media)

#### 5.2.6 Analog I/O interface

The analog signal interface supports both Voltage (0V – 10V) and Current (4mA – 20Ma) signals. By default, it is set to "Voltage" mode, but it can be configured to "Current" mode via DobotStudio Pro. To improve the accuracy of analog signals, it is recommended to use shielded cables or twisted-pair wiring.

_Table 5.3 Analog I/O interface specifications_

Interface Parameter Min value Typical Max value Unit Analog input (Voltage mode) Voltage -10-10 V AIx Resistance-6100-Ω Resolution-12-Bits Analog input (Current mode) Current 4-20 mA AIx Resistance-160-Ω Resolution-12-Bits Analog output (Voltage mode) Voltage -10-10 V Current -20-20 mA AOx Resistance-100-Ω Resolution-12-Bits Analog output (Current mode) Current 4-20 mA AOx Voltage 0-12 V Resolution-12-Bits

For AI interface connected to the tested object, the wiring is shown below.

_Figure 5.9 AI connected to tested object_

For AO interface connected to external load, the wiring is shown below.

_Figure 5.10 AO connected to external load_

![Figure 5.9 AI connected to tested object](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fgl852W3AE2ruymZUZJHw%2Fcra-ip68-p053-img01.png?alt=media)

![Figure 5.10 AO connected to external load](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fi2Tmn0QyMG0LAAeHt3Uh%2Fcra-ip68-p053-img02.png?alt=media)

#### 5.2.7 Remote switch interface

The remote switch interface is used to remotely control the on/off function of the controller. When the ON interface inputs are at high level for 0.5s or more, the controller will be turned on. In the power-on status, when the OFF interface inputs are at high level for 3s or more, the controller will be turned off. The wiring is shown below.

_Figure 5.11 Remote switch interface wiring_

![Figure 5.11 Remote switch interface wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTmMvY2CG9XQFCDa4Osqh%2Fcra-ip68-p054-img01.png?alt=media)

#### 5.2.8 Encoder interface

An encoder is a device that converts angular or linear displacement into electrical signals. It converts the displacement into periodic electrical signals, then converts these signals into counting pulses, so that the magnitude of the displacement can be measured by the number of pulses. The input signal in a specified format is supported. In this section, wiring is explained using the OMRON E6B2-CWZ1X encoder as an example. Based on the encoder's wiring colors, connect each signal cable to the controller. First, connect the power cables (5V and 0V) to the corresponding I/O 5V and I/O 0V interfaces. Then, connect the remaining encoder signal cables to their respective interfaces. If a ground wire is required, you can connect the shielded cable to the FG interface located under the RS485 interface. In most cases, the ground wire does not need to be connected unless there is strong magnetic interference.

_Table 5.4 Encoder wiring color_

Color Corresponding interface Brown I/O 5V Blue I/O 0V Black A+ White B+ Orange Z+ Black and Red A- White and Red B- Orange and Red Z-

#### 5.2.9 RS485 interface

The RS485 interface is mainly used for Modbus RTU communication. When connecting external devices (such as PLCs), connect the 485A (or 485+) and 485B (or 485-) interfaces of both devices correspondingly, and connect the ground wire according to the actual site conditions, as shown in the figure below (using dual-end grounding as an example).

_Figure 5.12 RS485 connected to PLC_

#### 5.2.10 Safety I/O interface

The safety I/O includes 20 interfaces: SI1 – SI10 (input), SO1 – SO10 (output). The basic electrical specifications of the safety I/O are the same as those of the General digital I/O. Safety input

_Table 5.5 SI interface definition_

Silkscreen Definition SI1, SI2 User emergency stop input SI3, SI4 Protective stop input No configuration by default, can be configured via DobotStudio Pro to: SI5 – SI10 • User emergency stop input (no status output)

* Protective stop reset input
* Reduced mode input

User emergency stop input The user emergency stop input is an emergency stop interface provided for users to connect to external emergency stop devices. By default, the user emergency stop input is a high-level, normally closed signal. Any low-level input will trigger the robot to enter emergency stop status. This function typically triggers the emergency stop output, which may cause self-locking in certain cases. To prevent this, you can configure the SI interface to "User E-Stop (no status output)" in the software, and use the corresponding interface for this purpose. SI1 and SI2 are user emergency stop inputs. The wiring for connecting one or more emergency stop switches is shown below.

_Figure 5.13 SI connected to one emergency stop switch_

_Figure 5.14 SI connected to multiple emergency stop switches_

Protective stop input The protective stop input is used for connecting external protective devices (e.g., safety door, safety light curtains). By default, the protective stop input is a high-level, normally closed signal. Any low-level input will trigger the robot to enter a protective stop (pause) status.

* When the protective stop reset input interface is configured, the protective stop status can be released only by restoring the protective stop input signal and triggering the protective stop reset input signal simultaneously. After confirming the continue operation in the software, the robot will resume operation.
* When the protective stop reset input interface is not configured, the protective stop status can be released by restoring the protective stop input signal, and the robot will resume operation.

![Figure 5.13 SI connected to one emergency stop switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0xoF7aNJOOZN10mLUJGQ%2Fcra-ip68-p057-img01.png?alt=media)

![Figure 5.14 SI connected to multiple emergency stop switches](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbhFLqmWnxaqLUif7nrr5%2Fcra-ip68-p057-img02.png?alt=media)

SI3 and SI4 are the protective stop inputs. The following are two typical cases where a protective stop reset input is not used:

* Safety door: When the door opens, the switch disconnects, triggering the protective stop. When the door closes, the robot resumes operation.

_Figure 5.15 SI connected to safety door switch_

* Safety laser scanner: When an operator enters the safety zone set by the laser scanner, the protective stop is triggered. Once the operator leaves the safety zone, the robot resumes operation.

![Figure 5.15 SI connected to safety door switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlNJ1eSfgX6yUWcI1eyFB%2Fcra-ip68-p058-img01.png?alt=media)

_Figure 5.16 SI connected to safety laser scanner_

Protective stop reset input The protective stop reset input is used to reset the protective stop status. By default, the protective stop reset input is a high-level, normally open signal. The rising edge of both circuits triggers to reset the protective stop status. The protective stop reset switch must be a dual-channel switch and must be placed outside the protective zone. A typical example of using the protective stop input with the protective stop reset input is a safety light curtain: When the operator passes through the light curtain, the protective stop is triggered. When the operator leaves the protective zone, presses the reset switch, and then confirms the continue operation in the software, the robot will resume operation. Below is an example where SI9 and SI10 are configured as protective stop reset inputs.

![Figure 5.16 SI connected to safety laser scanner](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvCYcGRhnyRsKQLIN9FS4%2Fcra-ip68-p059-img01.png?alt=media)

_Figure 5.17 SI connected to safety light curtain_

Reduced mode input The reduced mode input is used to control the robot to enter reduced mode. In reduced mode, the robot’s motion parameters (joint speed, TCP speed) are limited within the reduced mode range. By default, the reduced mode input is a high-level, normally closed signal. Any low-level input will trigger the robot to enter reduced mode. If the high-level input is restored, the robot will exit the reduced mode and return to the normal mode. The wiring for connecting the reduced mode switch is the same as the wiring for connecting the user emergency stop switch or protective stop switch. Safety output

_Table 5.6 SO interface definition_

Silkscreen Definition SO1, SO2 Emergency stop status output No configuration by default, can be configured via DobotStudio Pro to: SO3 – SO10 • Protective stop status output

* Reduced mode output
* Non-stop status output

![Figure 5.17 SI connected to safety light curtain](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQNQMSQrRJsZ7cApmc127%2Fcra-ip68-p060-img01.png?alt=media)

Silkscreen Definition

* Running status output
* Safety home status output
* System emergency stop status output
* User emergency stop status output

Emergency stop status output When the robot is in emergency stop status, the output voltage is low-level; otherwise, the output voltage is high-level. Any emergency stop source will trigger this output. SO1 and SO2 are the emergency stop status outputs, and the wiring for connecting external loads (e.g., warning lights) is shown below.

_Figure 5.18 SO connected to external load_

By using this output and the user emergency stop input, emergency stop interlock can be implemented between multiple robots. In this case, when one robot triggers an emergency stop, the others will also trigger an emergency stop. The following figure shows how to configure the emergency stop interlock between two robots, where each robot's SO1/SO2 is connected to the other robot's SI1/SI2.

_Figure 5.19 Emergency stop interlock between two robots_

Protective stop status output When the robot is in protective stop status, the output voltage is low-level; otherwise, the output voltage is high-level. Reduced mode output When the robot is in reduced mode, the output voltage is low-level; otherwise, the output voltage is high-level. Non-stop status output When the robot is in automatic running (non-stop status), the output voltage is low-level; otherwise, the output voltage is high-level. This status indicates whether the robot is running a program, not whether the joints are moving. For example, while running a project, if the robot is waiting for a specified DI to turn ON and not moving, the robot is in non-stop status and outputs low-level voltage. If the project is paused, the robot is in stop status and outputs high-level voltage.

![Figure 5.19 Emergency stop interlock between two robots](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ7KFLnNtlvhZa6csiOKo%2Fcra-ip68-p062-img01.png?alt=media)

Running status output If one or more joints of the robot are moving at more than 1°/s (except drag mode), it is considered to be in running status, and the output voltage is low-level; otherwise, the output voltage is high-level. Safety home status output When the robot is in safe home position, the output voltage is high-level; otherwise, the output voltage is low-level. The safe home position is a user-defined posture that can be set through the software. System emergency stop status output When the robot is in emergency stop status triggered by the emergency stop button or software, the output voltage is high-level; otherwise, the output voltage is low-level. User emergency stop status output When the robot is in user emergency stop status (triggered by SI1 / SI2), the output voltage is high-level; otherwise, the output voltage is low-level.

### 5.3 Robot arm interface

#### 5.3.1 Heavy-duty interface

The heavy-duty interface, located on the robot base, is connected to the controller via a heavy-duty cable to provide power and control signals for the robot arm. The pin distribution and definitions for the heavy-duty interface of CR5AP and CR10AP robot arms are as follows. Pin Name Definition Pin1 DC48V DC 48V + Pin2 DC48V DC 48V + Power interface Pin3 GND DC 48V - Pin4 GND DC 48V - Pin1 TX+ Send data + Pin2 TX- Send data - Communication interface Pin3 RX+ Receive data + Pin6 RX- Receive data - One end of the CR20AP robot arm's heavy duty cable is fixed to the robot base, and the pin distribution and definitions for the interface at the other end are as follows.

Pin Name Definition 1 DC48V DC 48V + 2 DC48V DC 48V + 7 GND DC 48V - 9 GND DC 48V - 3 FG Functional grounding PE Protective earthing A TX+ Send data + B TX- Send data - C RX+ Receive data + D RX- Receive data -

#### 5.3.2 Tool I/O interface

The tool interface is located on the side of the end flange of the robot arm and uses an aviation connector. The pin layout and definitions for the connector are as follows.

![Official manual figure, page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHD4gBEMWjJHFqzPDZOVc%2Fcra-ip68-p065-img03.png?alt=media)

Pin Name Definition 1 485A/AI\_1 485A or analog input 1 2 485B/AI\_2 485B or analog input 2 3 DI\_2 Digital input 2 4 DI\_1 Digital input 1 5 24V 24V output 6 DO\_2 Digital output 2 7 DO\_1 Digital output 1 8 GND GND

**NOTE**

* The specification of the aviation connector interface for CR20AP is

M12, and M8 for CR5AP and CR10AP robot arms.

* For CR20AP, the pin definitions for the X1 aviation connector are shown above. For the X2 aviation connector, the numbering for AI/DI/DO is shifted accordingly (e.g., DI1 becomes DI3, DI2 becomes DI4). The same logic applies for the cable pin definitions below.
* When driving inductive loads, a protection diode must be connected in parallel to prevent burnout of the output circuit. The cable used for the tool I/O is specified by DOBOT (model: SIGNAL 120108-06-014 (for CR20AP, equipped with M12 aviation connectors on both ends) / Lutronic FP-222460 (for CR5AP and CR10AP robot arms, equipped with M8 aviation connectors on both ends). The pin layout and cable definitions for the connector are as follows.

![Official manual figure, page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdOoh8cRcmSfTlUGP9vH3%2Fcra-ip68-p066-img01.png?alt=media)

Pin Cable color Definition 1 White 485A or analog input 1 2 Brown 485B or analog input 2 3 Green Digital input 2 4 Yellow Digital input 1 5 Gray 24V output 6 Pink Digital output 2 7 Blue Digital output 1 8 Red GND The tool I/O provides 24V power to the end tool. The electrical specifications are as follows.

_Table 5.7 Tool I/O power supply specifications_

Interface Parameter Min value Typical Max value Unit CR5AP and CR10AP Voltage 23 24 25 V 24V – GND Current 0 1 2 A CR20AP (Current is the combined current of the two tool I/Os) Voltage 23 24 25 V 24V – GND Current 0 2 3 A Digital input/output

_Table 5.8 Tool digital I/O specifications_

Interface Parameter Min value Typical Max value Unit Digital input (PNP with pull-down resistor, reads low when floating) Voltage -0.5-30 V OFF range -0.5-2 V DI\_x ON range 7-30 V Input resistance-57K-Ω

Interface Parameter Min value Typical Max value Unit Type-PNP - - Digital output Current 0-0.5 A Voltage drop 0-0.5 V DO\_x Current leakage 0-0.1 mA Type-PNP - - The tool digital input is PNP type. The wiring for connecting an external simple switch circuit is as follows.

_Figure 5.20 Tool DI connected to simple switch_

When using a PNP three-wire sensor as the DI input source, the wiring is shown below.

_Figure 5.21 Tool DI connected to PNP-type sensor_

The tool digital output is PNP type, powered by the internal power supply, with the total output current at the end-effector not exceeding the maximum 24V output current as described before. The output current for a single DO channel should be ≤500mA. The wiring method is shown below.

_Figure 5.22 Tool DO wiring_

![Figure 5.20 Tool DI connected to simple switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fkr9sm6RX0oMDZCCH2RiM%2Fcra-ip68-p068-img01.png?alt=media)

![Figure 5.21 Tool DI connected to PNP-type sensor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlOSKgKKsxjWyXWb5CWnd%2Fcra-ip68-p068-img02.png?alt=media)

![Figure 5.22 Tool DO wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgE82N9UhC5Eqfu0IX806%2Fcra-ip68-p068-img03.png?alt=media)

Analog input The analog signal interface supports both Voltage (0V – 10V) and Current (4mA – 20Ma) signals. By default, it is set to "Voltage" mode, but it can be configured to "Current" mode via DobotStudio Pro.

_Table 5.9 Analog input specifications_

Interface Parameter Min value Typical Max value Unit Analog input (Voltage mode) Voltage -0.5-12 V AI\_x Input resistance (0V – 10V) - 14800-Ω Resolution-12-Bits Analog input (Current mode) Current -2.5-25 mA AI\_x Input resistance (4mA – 20mA) - 200 202 Ω Resolution-12-Bits The wiring for tool analog input connected to the tested object is shown below.

_Figure 5.23 Tool AI wiring_

![Table 5.9 Analog input specifications](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fk7UkdwJ1bArrI4fm2G50%2Fcra-ip68-p069-img01.png?alt=media)

## 6. Transportation

### 6.1 Transportation precautions

* The robot arm should be restored to its packing posture before transportation. This can be set in DobotStudio Pro (refer to DobotStudio Pro User Guide for details). Use the original packaging for transportation.
* During transportation, ensure that the robot arm remains stable and is securely fastened.
* During transportation and long-term storage, maintain an ambient temperature range of -20°C to +55°C, with humidity ≤95% and no condensation.
* After transportation, store the original packaging in a dry place for future repacking and transportation.

**WARNING**

* Ensure that operators do not strain their backs or other body parts while lifting the equipment. Use appropriate lifting equipment if necessary.
* DOBOT assumes no responsibility for any damage incurred during transportation.
* Strictly follow the installation instructions when installing the robot.

### 6.2 Unpackaged handling

When moving the robot arm from its packaging to the installation position or relocating it, follow these handling guidelines:

* If the robot arm is not in the packing posture, restore it to the packing posture first.
* When handling and installing the robot, hold the robot arm with your hand until all base mounting bolts are fully tightened.
* For CR5AP and CR10AP: It is recommended to hold the J1 joint and the upper part of the upper arm for handling (two people should carry it if necessary). Do not lift the robot by grasping joints J3 – J6 or the forearm.

_Figure 6.1 Handling the robot arm_

![Figure 6.1 Handling the robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FG8Jb0ss24dGKfO1qSfaX%2Fcra-ip68-p070-img01.png?alt=media)

* For CR20AP: Use the factory-provided slings for hoisting. The hoisting position should be at the J1 joint and the upper part of the upper arm. Do not attach the slings to joints J3 – J6 or the forearm to lift the robot, as this may damage the internal structure.

_Figure 6.2 Hoisting the robot arm_

![Figure 6.2 Hoisting the robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNlFJjHdgvslI7fB54sYl%2Fcra-ip68-p071-img01.png?alt=media)

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

### 7.2 Unpacking

Upon unpacking, check the attached shipping list to ensure that all items are included. If anything is missing, please contact your supplier.

### 7.3 Robot installation

#### 7.3.1 Installation platform requirements

* When installing the robot, it must be securely fixed to a stable base. The base should be able to withstand at least 10 times the maximum torque of the J1 joint and at least 5 times the weight of the robot arm. Maximum torque for J1 joint: ◦ CR5AP: 194 Nm ◦ CR10AP: 436 Nm ◦ CR20AP: 800 Nm
* If the robot arm is installed on a linear axis or a movable platform, the acceleration of the platform should be low, as high acceleration may trigger the robot's collision detection mechanism, causing it to stop.
* The robot arm is connected to the controller via a heavy-duty cable. If the heavy-duty cable needs to pass through a cable routing hole on the installation platform, the hole diameter should not be less than 40mm.
* The heavy-duty cables of CR20AP robot arm support both bottom cable routing and side cable routing, while CR5AP and CR10AP only support side cable routing. For side cable routing, the recommended distance between the cable routing hole and the robot base should be no less than L+8D (L: the length after connecting the heavy- duty connector; D: the diameter of the heavy-duty cable): ◦ For CR20AP, L ≈ 150 mm, D = 15.6 mm, so the recommended distance between the cable routing hole and the robot base should be at least 280 mm. ◦ For CR5AP and CR10AP, L ≈ 100 mm, D = 11.9 mm, so the recommended distance between the cable routing hole and the robot base should be at least 200 mm.

_Figure 7.1 Heavy-duty cable routing diagram_

![Figure 7.1 Heavy-duty cable routing diagram](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5knMZrPrEHWSLRgczwR5%2Fcra-ip68-p073-img01.png?alt=media)

#### 7.3.2 Robot arm installation

The following figure illustrates several typical installation postures for robot arms, robot arms support 360° mounting at any angle.

**NOTE**

The installation posture at the bottom of the figure is the standard mounting angle. When installing the robot in a non-standard mounting angle, you need to calibrate the mounting angle through DobotStudio Pro after power- on. For details, refer to DobotStudio Pro User Guide.

_Figure 7.2 Robot arm installation postures_

When installing the robot arm, position the mounting holes on the installation platform according to the base dimension. Then, secure the robot base to the platform using bolts. Be sure to observe the following during installation.

* During transportation, ensure that the robot is stable and properly secured in its position.
* When hoisting the robot (CR20AP is supplied with lifting slings, other robot arm models are not supplied with lifting slings. If other models need to be hoisted, users must provide their own lifting slings), properly position the moving parts to prevent accidental movement and damage during hoisting and transportation.
* When moving the robot arm from its packaging to the installation position, hold the robot with your hand until all bolts on the base are tightened.
* During installation, ensure the robot is properly aligned and positioned. The robot base must be secured to the platform using hex bolts (ISO898-1: 2013, property class: 12.9). CR20AP requires 6 M10 bolts, the other models require 4 M8 bolts.
* For wall-mounted or upside-down installations, safety measures must be taken to prevent the robot base from falling.

![Figure 7.2 Robot arm installation postures](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWSfR5D3KPGoaWbUjh6d5%2Fcra-ip68-p074-img01.png?alt=media)

_Figure 7.3 CRA-IP68 series robot arm installation steps_

#### 7.3.3 Air vent instruction

The base of the CRA-IP68 series robot arm includes a reserved air vent. By default, this vent is sealed with M5 screws. In special cases, the screw can be removed to allow air to be pumped into the robot arm to enhance its sealing. The exact location of air vent varies by model, but it is always near the heavy-duty socket. The following figure uses the CR10AP as an example and shows the recommended connection method.

**NOTE**

The user is responsible for connecting the air circuit. Functions of the components in the air circuit are as follows:

* Pressure regulator: Adjusts the air pressure within the system.
* Pressure gauge: A digital or electrical-contact pressure gauge is recommended for monitoring the system air pressure and outputting a digital signal to stop the robot when the air pressure falls outside the specified range.
* Switch valve: Controls the air circuit's flow, making it easier to conduct adjustments.

![Figure 7.3 CRA-IP68 series robot arm installation steps](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK2BkK649r5KuwEH04MEX%2Fcra-ip68-p075-img01.png?alt=media)

![Official manual figure, page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqarH8LSdRTiZeNnFgGgc%2Fcra-ip68-p075-img02.png?alt=media)

Operating procedures:

1. Connect the air circuit as shown in the above figure.
2. Close the switch valve, then turn on the air pump and adjust the pressure regulator

until the pressure gauge reaches the target pressure.

**NOTE**

Recommended operating positive pressure: 2-4 kPa, minimum operating positive pressure: 1 kPa, maximum operating positive pressure: 6 kPa.

3. Once the pressure gauge stabilizes, open the switch valve.
4. Under normal conditions, the pressure should stabilize near the target level. If the

pressure doesn’t reach the target or fluctuates significantly, this indicates a failure in the robot arm’s sealing, and the robot should be stopped immediately.

**NOTE**

It is advisable to set the allowable pressure range on the gauge according to the actual site conditions. If the pressure exceeds this range, the gauge should output a digital signal, which can be connected to the robot controller’s safety IO on SI1/SI2 (SI1/SI2 are user emergency stop inputs, defaulted to high-level normally-closed signal inputs. Any low-level signal on these inputs will trigger the robot to enter an emergency stop state).

#### 7.3.4 Controller installation

Place the controller on a stable platform outside the robot's workspace, and reserve enough space for cable connections and operation. The controller supports both vertical and horizontal installation. Keep the air inlet and outlet unobstructed and leave at least 200mm space on the corresponding sides for proper heat dissipation. Leave 200mm space at the front of the controller for cable wiring.

_Figure 7.4 Vertical installation_

![Figure 7.4 Vertical installation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZUUcaRsWpSJY89bLMitO%2Fcra-ip68-p076-img01.png?alt=media)

_Figure 7.5 Horizontal installation_

#### 7.3.5 Protective cover installation

The controller is equipped with a protective cover. After correct installation of the protective cover, the controller can achieve IP54 protection level. The figure below shows the components of the protective cover.

_Figure 7.6 Protective cover_

Before delivery, the cable entry plate (with modules and plugs) has been mounted on the protective cover frame.

1. Use an M4 hex wrench to remove 4 M4 bolts from the corners of the cable entry plate

frame. Then remove the cable entry plate from the protective cover.

2. Use an M4 hex wrench to loosen 3 M4 bolts on the side of the cable entry plate frame.

Disassemble the cable entry plate and remove the plate module.

![Figure 7.5 Horizontal installation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FraN1jBX42AmhGWxsek6t%2Fcra-ip68-p077-img01.png?alt=media)

![Figure 7.6 Protective cover](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8XTaE7gymdU1RG7rWjYn%2Fcra-ip68-p077-img02.jpg?alt=media)

_Figure 7.7 Cable entry plate_

3. Select the appropriate module according to the cable diameter connected to the

controller (If no suitable module is already installed on the cable entry plate, select one from the separate modules shipped with the protective cover). Remove the plug from the module, then pass the cable through and embed it into the module.

_Figure 7.8 Cable entry plate module_

4. Install the module back into the cable entry plate frame, and tighten 3 M4 bolts on the

frame side.

5. Install the cable entry plate back into the protective cover frame, and fix it using four

M4 bolts.

6. Connect the cables passing through the protective cover to the controller.
7. Use an M3 Phillips screwdriver, remove 5 screws corresponding to the protective

cover mounting holes on both sides of the controller (3 screws on the left, 2 screws on the right). For the installation position of the protective cover, refer to the diagram at the beginning of this section.

8. Install the protective cover and secure it to the controller using 5 M3 screws delivered

with the protective cover.

#### 7.3.6 Tool installation

The robot arm's end flange has 4 M6 threaded holes (6 M8 holes for CR20AP), which can fix the tool to the end of the robot arm. To ensure precise alignment of the tool, the reserved positioning holes can be used with pins for accurate positioning.

![Figure 7.7 Cable entry plate](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FffFAg5mq0mAnEqiNHcnp%2Fcra-ip68-p078-img01.png?alt=media)

![Figure 7.8 Cable entry plate module](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fs0SiFjNvRYjuiAt0tZ8n%2Fcra-ip68-p078-img02.png?alt=media)

### 7.4 Cable connection

_Figure 7.9 Cable connection_

1. Place the controller on a flat and stable surface outside the working space of the

robot.

2. Connect the controller to the robot arm via the heavy-duty cable. After plugging

the heavy-duty cable into the heavy-duty socket, secure the connection according to the connection side: tighten the screws on the heavy-duty plug on the robot arm side, and fasten the latch on the controller side.

3. Plug the E-stop switch cable into the emergency stop switch interface. When

connecting, align the white dot on the connector with the white dot on the interface, then rotate the blue plastic ring clockwise to secure the connection.

4. Plug one end of the power cable into the power interface of the controller, and the

other end into the main power outlet.

![Figure 7.9 Cable connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fe276mGp61UBVkQ9E2TVF%2Fcra-ip68-p079-img01.png?alt=media)

**NOTICE**

* The specifications and installation method of the external cables should comply with local laws and regulations.
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

_Figure 7.10 Unlock the heavy-duty plug_

![Figure 7.10 Unlock the heavy-duty plug](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAdEwAxgYs22V4WIIpL3z%2Fcra-ip68-p080-img01.jpg?alt=media)

### 7.5 Power-on and debugging

After turning on the external power supply, press the switch above the power interface to "I", then press the round button on the top of the controller for 0.5s (if pressing the round button is inconvenient, you can use the Remote switch interface).

_Figure 7.11 Power-on_

Once the indicator lights on both the robot arm's end-effector and the controller's round button turn solid blue, you can connect to the robot using the operation terminal, enable it, and jog it for debugging. For detailed operation instructions, refer to DobotStudio Pro User Guide. When the robot is not in use, long-press the round button on the top of the controller for 3s to power it off. Wait until the indicator lights on both the robot arm's end-effector and the controller's round button turn off. Then, press the switch above the power interface to "O" to disconnect the power supply.

**NOTICE**

If the robot is being used for the first time or has been left idle for a long period of time, performing high-speed, high-load movements immediately after power-on may trigger false alarms. It is recommended to perform a few minutes of low-speed movements to warm up the robot before normal operation.

![Figure 7.11 Power-on](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6qmKRI0eYEQgVxIUh4bc%2Fcra-ip68-p081-img01.png?alt=media)

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

Nominal thread Outer hex screw Inner hex bolt Inner hex bolt diameter (joint) (12.9) (rear cover) 3 mm / 0.118 in 2 Nm 2.4 Nm 0.7 Nm 4 mm / 0.157 in 4 Nm 4.5 Nm - 5 mm / 0.197 in 7.5 Nm 9 Nm - 6 mm / 0.236 in 15 Nm 18 Nm - 8 mm / 0.32 in-37 Nm - The tightening torques vary depending on the type of bolt or base material. If not listed in the table, please contact DOBOT technical support engineer.

## 9. Disposal and Environmental Protection

DOBOT robots must be disposed of in accordance with the applicable national laws, regulations and standards. The following symbol indicates that the product must not be disposed of as general waste.

## 10. Warranty

### 10.1 Product warranty

Without prejudice to any claim agreement that the user (customer) may reach with the distributor or retailer, the manufacturer shall guarantee the quality of the products to the customer in accordance with the terms and conditions below: If defects caused by manufacturing and/or improper material occur in a new device and its components within 12 months (15 months at most if the shipping time is included) after the device is put into use, DOBOT shall provide the necessary spare part, and the user (customer) shall offer personnel to replace the spare part, using another part that represents the latest technology level to replace or repair the related part. If the device defects are caused by improper handling and/or failure to follow the relevant information set out in the User Guide, the warranty is invalid. This warranty does not apply to or extend to maintenance (e.g. installation, configuration, software download) performed by the authorized distributer or customer. The user (customer) must provide the purchase receipt and the purchase date as valid evidence for the warranty. Claims under this warranty must be made within two months of the apparent failure to perform the product warranty. The ownership of the device or components that are replaced or returned to DOBOT shall remain with DOBOT. Any other claims arising from or related to the device are not covered by this warranty. Any items in this product warranty do not intend to limit or exclude the legal rights of the customer or to limit or exclude the liability of the manufacturer for the personnel casualty resulting from its negligence. The duration of this product warranty shall not be extended due to the services provided under the product warranty terms. Under the principle of not violating the warranty, DOBOT reserves the right to charge customers for the replacement or maintenance. The foregoing does not imply a change in the burden of proof to the detriment of the client. If there are defects on the device, DOBOT shall not be liable for any damage or loss arising therefrom, including but not limited to loss of production or damage to other production device.

### 10.2 Disclaimer

DOBOT is committed to improve the reliability and performance of its products, and as such reserves the right to upgrade products without prior notice. DOBOT strives to ensure the contents of the User Guide are precise and reliable, but takes no responsibility for any errors or missing information.

## 11. Compliance Statements

### 11.1 FCC compliance statements

This device complies with Part 15 of the FCC Rules. Operation is subject to the following two conditions: (1) this device may not cause harmful interference, and (2) this device must accept any interference received, including interference that may cause undesired operation. Note: This equipment has been tested and found to comply with the limits for a Class B digital device, pursuant to Part 15 of the FCC Rules. These limits are designed to provide reasonable protection against harmful interference in a residential installation. This equipment generates, uses and can radiate radio frequency energy and, if not installed and used in accordance with the instructions, may cause harmful interference to radio communications. However, there is no guarantee that interference will not occur in a particular installation. If this equipment does cause harmful interference to radio or television reception, which can be determined by turning the equipment off and on, the user is encouraged to try to correct the interference by one or more of the following measures: -- Reorient or relocate the receiving antenna. -- Increase the separation between the equipment and receiver. -- Connect the equipment into an outlet on a circuit different from that to which the receiver is connected. -- Consult the dealer or an experienced radio/TV technician for help. Caution: Changes or modifications not expressly approved by the party responsible for compliance could void the user’s authority to operate the equipment. This transmitter must not be co-located or operating in conjunction with any other antenna or transmitter. This equipment should be installed and operated with minimum distance 20cm between the radiator and your body.

### 11.2 ISED compliance statements

This device contains licence-exempt transmitter(s)/receiver(s) that comply with Innovation, Science and Economic Development Canada’s licence-exempt RSS(s). Operation is subject to the following two conditions: (1) This device may not cause interference. (2) This device must accept any interference, including interference that may cause undesired operation of the device. This equipment complies with IC RSS-102 radiation exposure limits set forth for an uncontrolled environment. This equipment should be installed and operated with minimum distance 20cm between the radiator and your body. L’émetteur/récepteur exempt de licence contenu dans le présent appareil est conforme aux CNR d’Innovation, Sciences et Développement économique Canada applicables aux appareils radio exempts de licence. L’exploitation est autorisée aux deux conditions suivantes: (1) L’appareil ne doit pas produire de brouillage; (2) L’appareil doit accepter tout brouillage radioélectrique subi, même si le brouillage est susceptible d’en compromettre le fonctionnement. Cet équipement est conforme aux limites d'exposition aux radiations IC CNR-102 établies pour un environnement non contrôlé. Haut-parleurs et subwoofer doit être installé et utilisé avec une distance minimale de 20cm entre le radiateur et votre corps.

## Appendix Technical Specifications

## Appendix A Robot arm technical specifications

_Table 1 CR5AP and CR10AP_

Product name DOBOT CR5AP DOBOT CR10AP Weight 25 kg (55.1 lb) 40kg (88.2 lb) Max payload 5 kg (11lb) 10 kg (22 lb) Working radius 900 mm (35.4 inch) 1300 mm (51.2 inch) Max linear speed 2 m/s (78.7 inch/s) J1 ±360° J2 ±360° Joint J3 ±160° working range J4 ±360° J5 ±360° J6 ±360° J1 180°/s 150°/s J2 180°/s 150°/s J3 180°/s 180°/s Max joint speed J4 223°/s 223°/s J5 223°/s 223°/s J6 223°/s 223°/s DI 2 2 DO 2 2 Tool I/O AI 2 (multiplexed with RS485) 2 (multiplexed with RS485) RS485 Support Repeatability ±0.02 mm ±0.03 mm IP rating IP68 Noise 70dB(A)

Product name DOBOT CR5AP DOBOT CR10AP 0°C – 50°C

**NOTICE**

When the ambient temperature is lower than 10°C, the Temperature range viscosity of the lubricant increases, which may trigger false alarms if the robot performs high-speed and high- load movements immediately after powering on. It is recommended to first perform a few minutes of low- speed movements to warm up the device. Humidity ≤ 95%, no condensation Typical power 150 W 350 W consumption Installation mode Any angle Cable length from 5 m (16.4 ft) 5 m (16.4 ft) robot to controller Material Aluminum alloy, ABS Service life 5 years

_Table 2 CR20AP_

Product name DOBOT CR20AP Weight 73 kg (160.9 lb) Max payload 20kg (44.1 lb) Working radius 1700 mm (66.9 inch) Max linear speed 2 m/s (78.7 inch/s) J1 ±360° J2 ±360° Joint J3 ±165° working range J4 ±360° J5 ±360° J6 ±360° J1 120°/s J2 120°/s J3 150°/s Max joint speed J4 180°/s J5 180°/s J6 180°/s DI 4 DO 4 Tool I/O AI 4 (multiplexed with RS485) RS485 Support Repeatability ±0.05 mm IP rating IP68 Noise 70dB(A) Temperature range 0°C – 50°C

Product name DOBOT CR20AP

**NOTICE**

When the ambient temperature is lower than 10°C, the viscosity of the lubricant increases, which may trigger false alarms if the robot performs high-speed and high- load movements immediately after powering on. It is recommended to first perform a few minutes of low- speed movements to warm up the device. Humidity ≤ 95%, no condensation Typical power 500 W consumption Installation mode Any angle Cable length from 6 m (19.7 ft) robot to controller Material Aluminum alloy, ABS Service life 5 years UL1740: 2018 UL Standard for Safety Robots and Robotic Equipment; CSA Z434-14 (R2019) Industrial robots and robot systems; CSA C22.2 NO. 14-13 Industrial Control Equipment; NFPA 79:2018 Electrical Standard for Industrial Machinery; EN ISO 10218-1:2011 Robots and robotic devices – Safety requirements for industrial robots-Part 1: Robots; Safety standard EN 60204-1:2018 Safety of machinery-Electrical equipment of machines-Part 1: General requirements; EN ISO 12100:2010 Safety of machinery-General principles for design-Risk assessment and risk reduction; ISO/TS 15066:2016 Robot and Robotic Devices-Collaborative Robots; EN ISO 13849-1:2015 Safety of machinery-Safety-related parts of control systems-Part 1: General principles for design EN IEC 61000-6-2:2019 Electromagnetic compatibility (EMC) - Part 6-2: Generic standards-Immunity standard for industrial environments; EMC standard EN IEC 61000-6-4:2019 Electromagnetic compatibility (EMC) - Part 6-4: Generic standards-Emission standard for industrial environments

## Appendix B Controller technical specifications

DOBOT CC262 DOBOT CC263 Product name AC version AC version Controller 345 m&#x6D;_&#x33;45 m&#x6D;_&#x31;45 mm 400 m&#x6D;_&#x34;00 m&#x6D;_&#x31;75 mm dimensions Weight 9.5 kg 20.9 lb 15.5 kg 34.2 lb （ ） （ ） Input power 100 – 240V 47 – 63Hz 100 – 240V 47 – 63Hz,, IO power supply 24V, Max 3A, Max 0.5A for each DI 24 (PNP or NPN) DO 24 (PNP or NPN) I/O interface AI 2, Voltage/Current mode, 0V – 10V, 4mA – 20mA AO 2, Voltage/Current mode, 0V – 10V, 4mA – 20mA Ethernet 2, for TCP/IP, Modbus TCP, Ethernet/IP, Profinet port communication Commu. USB 2, for importing/exporting files interface RS485 1, for RS485, Modbus RTU communication Encoder 1, for ABZ incremental encoder Protection level IP20 (configured with IP54protective cover) Teaching method PC, APP (Android), Teach Pendant Compatible models CR5AP and CR10AP CR20AP
