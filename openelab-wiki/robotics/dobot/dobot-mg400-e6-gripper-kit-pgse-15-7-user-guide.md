---
description: >-
  User guide for the DOBOT PGSE-15-7 integrated drive-control gripper kit used
  with Magician E6 and MG400 robots.
---

# DOBOT MG400/E6 Gripper Kit PGSE-15-7 User Guide

## DOBOT Mini Servo Gripper for Magician E6 Robot

{% embed url="https://openelab.io/products/dobot-e6-mini-servo-gripper" %}

## Contents

* Preface
* 1\. Product Introduction
* 2\. Installation Instructions
* 3\. Gripper Control
* 4\. Shipping List

Copyright © SHENZHEN DOBOT CORP LTD 2025. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as "Dobot"). Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot.

### SHENZHEN DOBOT CORP LTD

Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

## Preface

Purpose This document introduces the functions, parameters, installation, and operation of the Integrated Drive-Control Parallel Electric Gripper Kit PGSE-15-7, which is compatible with the MG400 and Magician E6 robots, helping users understand and use the PGSE gripper kit effectively. Intended audience This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Revision history Date Version Revised content Added content related to PGSE gripper compatible with 2025/10/14 V2.0 MG400 2024/08/22 V1.0 The first release (Compatible with Magician E6) Symbol conventions The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could

**DANGER**

result in death or serious injury. Indicates a hazard with a medium level or low level of risk which, if not

**WARNING**

avoided, could result in minor or moderate injury, robot arm damage. Indicates a potentially hazardous situation which, if not avoided, could

**NOTICE**

result in robot arm damage, data loss, or unanticipated result. Provides additional information to emphasize or supplement important

**NOTE**

points in the main text.

## 1. Product Introduction

### 1.1 Product specifications

The PGSE157 is a parallel gripper equipped with a pair of parallel fingertips that move symmetrically during operation. The gripper comes with an aviation connector cable that can be directly connected to the Magician E6 and MG400 end. It communicates with Magician E6 and MG400 via digital I/O. The Dobot Mini Servo Gripper Kit (E6) and the Integrated Drive-Control Parallel Electric Gripper Kit (MG400) are two distinct accessory packages designed for different robot arms. While the mechanical structure and appearance of the grippers are identical, they differ in the adapter flange and aviation connector interface definitions specific to the E6 and MG400. For detailed differences, please refer to the Electrical interfaces of the grippers and the Shipping list. Parameter Value Model (compatible with DT-AC-PGSE157-01 Magician E6) Model (compatible with DT-AC-PGSE157-02 MG400) Gripper force (single side) 6\~15 N Maximum recommended 0.25 kg payload ① Stroke 7 mm Opening / Closing time 0.15 s / 0.15 s Weight 0.15 kg Size 85.6 mm x 38 mm x 23.2 mm Transmission method Precision planetary reducer + Gear rack Operating noise < 50 dB Communication protocol Modbus RTU RS485, Digital I/O (2 Inputs, 2 Outputs) （ ） Operating voltage 24V DC ± 10% Rated current 0.15 A

![Official manual figure, page 5](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvaZJMI6y6y7vllxEEJZl%2Fpgse-p005-img01.png?alt=media)

Peak current 0.8 A Rated power 3.6 W Protection level IP40 Recommended environment 0 – 40, ≤85% RH International standards CE, FC℃C, RoHS The recommended load calculation is based on pure friction grip, with a friction coefficient of 0.2 and ① a safety factor of 4. The offset of the object's center of gravity may also affect the load. Please consult us if you have any questions.

### 1.2 Indicator definition

In addition to reading the real-time status of the gripper through digital I/O, it can also be determined by the indicator light color. The description of the indicator light colors is as follows:

* Uninitialized state: Red light flashes, other lights OFF.
* Initialization completed: Blue light ON, indicating the gripper is in operable state.
* Object gripped state: Green light ON, other lights OFF.

### 1.3 Mechanical specifications

![Official manual figure, page 6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu1y0UHlSN8pNqP4KwnHr%2Fpgse-p006-img01.png?alt=media)

### 1.4 Electrical interface

The gripper is connected to the aviation connector interface at the end of the Magician E6 and MG400 via an aviation connector cable. Both DI and DO are PNP-type. The interface definitions of the gripper's aviation connector are as follows. Gripper Aviation Connector Gripper Aviation Connector (Compatible with E6) (Compatible with MG400) Pin Definition Pin Definition 1 24V 1 24V 2 DO1 2 GND 3 DO2 3 DO18 4 DI1 4 DO17 5 DI2 5 DI18 6 GND 6 DI17

![Official manual figure, page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcvjPDL2k4npPrmJkTXkm%2Fpgse-p007-img02.png?alt=media)

## 2. Installation Instructions

### 2.1 Assembling the gripper

1. Attach the L-shaped gripper adapter to the electromagnetic gripper and securely

tighten the screws.

2. Install the gripper fingers and tighten the screws. Adjust the installation position

of the gripper fingers on the L-shaped gripper adapter according to the actual requirements. The protective pads on the sides of the gripper fingers can be applied or removed as needed.

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4hMKPoQ6WElpN7OCWd0A%2Fpgse-p008-img01.jpg?alt=media)

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAiryw0aOFac8KxcdMIdu%2Fpgse-p008-img02.jpg?alt=media)

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcXu5L0Uhdfi54teMhH5k%2Fpgse-p008-img03.jpg?alt=media)

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm0yy3Q4SssJXuf8kIUGU%2Fpgse-p008-img04.jpg?alt=media)

### 2.2 Installing gripper onto Magician E6 end

1. Attach the adapter flange of the Magician E6 (a standard part of the E6, also

available for separate purchase) to the gripper and securely tighten the two screws.

2. Mount the electromagnetic gripper to the end of the Magician E6 using the

adapter flange, and securely tighten the four screws.

3. Connect the gripper cable to the aviation connector at the end of the robot arm.

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmRBayCdbJYrKqTmxjTTN%2Fpgse-p009-img01.jpg?alt=media)

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNrRVgC1LANj62NdS4q1o%2Fpgse-p009-img02.jpg?alt=media)

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHUtTj8mgeMak2suOjzGx%2Fpgse-p009-img03.jpg?alt=media)

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz5wsVFoasx0QINNMSzS9%2Fpgse-p009-img04.jpg?alt=media)

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLalrjJwZaZ4AhLLbMQyL%2Fpgse-p009-img05.jpg?alt=media)

### 2.3 Installing gripper onto MG400 end

1. Use two screws to secure the adapter flange included with the gripper kit to the

electromagnetic gripper.

2. First, loosen the fixing screws on the side of the MG400 end flange and remove

the end flange. Then, use four screws to secure the adapter flange of the electromagnetic gripper to the MG400's end flange.

3. Reattach the end flange with the installed electromagnetic gripper to the end of

the MG400 robot arm.

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0AsuhbwWwOMSdGxDSzSH%2Fpgse-p010-img01.png?alt=media)

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUe0eZbPl4BwCwWl0vcNs%2Fpgse-p010-img02.jpg?alt=media)

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBGkmlzI4KGUikYLUOWfZ%2Fpgse-p010-img03.jpg?alt=media)

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgTkCi5BP2vzdcv7HHLMj%2Fpgse-p010-img04.jpg?alt=media)

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdM7TfCudPBtq7MJGLH68%2Fpgse-p010-img05.jpg?alt=media)

4. Connect the cable of the electromagnetic gripper to the aviation connector at the

end of the MG400 robot arm.

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4v7u2VLx0vgC2Vo0rxIX%2Fpgse-p011-img01.jpg?alt=media)

## 3. Gripper Control

The PC control software for the Magician E6 robot is DobotStudio Pro V4.6.x, while the PC control software for the MG400 robot is DobotStudio Pro V2.8.0. You can download the latest software from the DOBOT Download Center. The robot can control the gripper via the tool DO1 and DO2. The gripper is pre-initialized before shipment, so in most cases, users can directly control the gripper via tool DO1. Tool\_DO1 Function Tool\_DO2 Function OFF Open OFF Default ON Close ON Initialize The robot can read the status of the gripper via the tool DI1 and DI2. Tool\_DI1 Tool\_DI2 Gripper status OFF OFF Moving/Just started/Fault ON OFF Closed OFF ON Opened ON ON Object gripped

## 4. Shipping List

### 4.1 Mini Servo Gripper Kit (E6)

### 4.2 Integrated Drive-Control Parallel Electric Gripper Kit (MG400)

![Official manual figure, page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8knVe60tbHnvsOV4WptD%2Fpgse-p013-img01.png?alt=media)

![Official manual figure, page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSnZ3O8TCln6hO0UuYyTM%2Fpgse-p013-img02.png?alt=media)
