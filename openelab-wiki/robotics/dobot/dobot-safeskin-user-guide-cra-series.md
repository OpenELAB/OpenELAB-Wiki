---
description: >-
  SafeSkin guide for DOBOT CR3AS, CR5AS, and CR10AS collaborative robots,
  covering safety, installation, settings, commands, and specifications.
---

# DOBOT SafeSkin User Guide for CRA Series

## DOBOT CR3AS SafeSkin Collaborative Robot

{% embed url="https://openelab.io/products/dobot-cr3as-safeskin-collaborative-robot" %}

## DOBOT CR5AS Collaborative Robot with SafeSkin

{% embed url="https://openelab.io/products/dobot-cr5as-collaborative-robot-safeskin" %}

## DOBOT CR10AS SafeSkin Collaborative Robot

{% embed url="https://openelab.io/products/dobot-cr10as-safeskin-collaborative-robot" %}

## Contents

* Preface
* 1\. Safety Precautions
* 2\. Product Introduction
* 3\. Installation
* 4\. Operation
* 5\. Technical specifications

Copyright © SHENZHEN DOBOT CORP LTD 2023–2026. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as "DOBOT"). Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. DOBOT makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will DOBOT be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. DOBOT shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot.

### SHENZHEN DOBOT CORP LTD

Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

## Preface

### Applicable scope

* DOBOT CR3AS
* DOBOT CR5AS
* DOBOT CR10AS

Other models of CRA series can also be installed with SafeSkin (except forearm). Please consult technical support if required.

### Purpose

This document introduces the functions, installation procedure and settings of the SafeSkin, which is convenient for users to understand and use the SafeSkin. For relavant content of CRA series robots, please refer to DOBOT CRA Series Hardware User Guide.

### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

### Change history

Date Version Change Description Updated the former company name "Shenzhen Yuejiang 2026-01-22 V1.4 Technology Co., Ltd." to the new name "SHENZHEN DOBOT CORP LTD." Modified installation procedure in Chapter 3 to wiring method; 2023-07-20 V1.4 Added technical specifications; Updated content style 2021-10-09 V1.2 Added general precautions 2021-09-26 V1.1 Added safety precautions

Date Version Change Description 2021-07-02 V1.0 First release

### Symbol conventions

The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided,

**DANGER**

could result in death or serious injury Indicates a hazard with a medium level or low level of risk which,

**WARNING if not avoided, could result in minor or moderate injury, robot**

damage Indicates a potentially hazardous situation which, if not avoided,

**NOTICE can result in equipment damage, data loss, or unanticipated**

result Provides additional information to emphasize or supplement

**NOTE**

important points in the main text

## 1. Safety Precautions

This chapter introduces the safety precautions when you use the product. Please read the document carefully before using the SafeSkin for the first time. Any safety information provided in this document should not be construed as a warranty of universal robots. The robot may cause injury or damage even if all safety instructions are observed. As the automatic obstacle avoidance function of the SafeSkin will make the robot move out of its original trajectory, please pay attention to the possible safety risks caused by obstacle avoidance, otherwise please do not switch on this function. The obstacle avoidance function is switched off by default. If you need to switch it on, please contact technical support. Warning

* Please confirm the safety risks of the end tools of the robot when avoiding obstacles. Do not use excessively long tools or sharp tools. As there is no SafeSkin on the end tool, the end tool may hit external devices or even cause injuries to people when avoiding obstacles.
* Please confirm whether the action of obstacle avoidance may cause the end tool or the robot to hit external devices, base or fixed platform.

**NOTICE**

When switching on the SafeSkin

* Please make sure that the SafeSkin is in the normal working condition without physical damage, and it reads signal normally.
* Please make sure that no signal source (including but not limited to metal objects, wires, etc.) is attached or fixed to the SafeSkin that may interfere with its induction. When avoiding obstacles
* When using the obstacle avoidance function, do not interfere with the movement of the robot continuously to prevent the robot from hitting external equipment, base or fixed platform due to the excessive moving range for obstacle avoidance.
* During obstacle avoiding, please press the emergency stop button immediately if any uncontrollable or unexpected situation occurs. When using the SafeSkin
* When handling or using the robot, the SafeSkin should not be used as the stress point to avoid damage to the SafeSkin. The SafeSkin uses silica gel, which is a flexible material, so the SafeSkin is prone to elastic deformation when hit and squeezed by external forces, which will cause abnormal signals of the SafeSkin. If the SafeSkin signal is abnormal, try smoothing the SafeSkin properly by hand. Then confirm whether the SafeSkin signal is normal.
* The installation position of the SafeSkin built-in sensor is shown below. As it is a sensitive device, do not press hard to avoid unnecessary damage to the SafeSkin.
* The conductive object cannot be directly fixed to the surface of the SafeSkin, which will cause the SafeSkin function to be automatically triggered. The conductive object needs to be suspended, as shown below.

![Official manual figure, page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0OHhNFA1i044zc8dPUQF%2Fsafeskin-cra-p007-img01.png?alt=media)

![Official manual figure, page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fr7ZCPF0RG2JeazO48oY8%2Fsafeskin-cra-p007-img02.jpg?alt=media)

## 2. Product Introduction

The SafeSkin is a safety protective device specially tailored for the robot arm. The robot arm can detect obstacles when wearing the SafeSkin. When an obstacle is detected, the robot stops or avoids the obstacle to prevent collision and avoid causing loss of people or property. A set of SafeSkin includes forearm SafeSkin, J4 SafeSkin, J5 SafeSkin and J6 SafeSkin, as shown below. The SafeSkin has different sensing levels for different approaching objects, as shown below. The SafeSkin has the highest sensing level to the human body and the lowest sensing level to insulating materials. Approaching Human Attachment Insulation Metal Wood Plastic object body (human body) material Sensing 4 3 3 2 1 0 level

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO1ePNrdHqOur2Zx7T8eE%2Fsafeskin-cra-p008-img01.jpg?alt=media)

## 3. Installation

This chapter mainly introduces the precautions of fixing the cables on the robot installed with SafeSkin and the wiring method to avoid mistakenly triggering the SafeSkin.

### 3.1 Installation precautions

1. The yellow side in the figure below is the sensing area of SafeSkin. Do not arrange

cables or conductive materials over the sensing area.

2. As silica gel is easy to deform, it is recommended not to forcibly tighten the silica gel

with cable ties to avoid mistakenly triggering the SafeSkin.

### 3.2 Recommended wiring method

1. It is recommended that the wiring be on the gap between the sensing areas, with a

height of at least 3cm from the skin (the actual distance should be determined after the test on site).

2. The cables need to be fixed steadily so as not to shake while the robot is running.

The figure below shows a recommended wiring method (the red line represents the cables, and the green line represents the wire bundles).

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3DV1WTweNfz7csXSe8j4%2Fsafeskin-cra-p009-img01.png?alt=media)

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3uOjpc8emOlZM0w8uU5b%2Fsafeskin-cra-p010-img01.png?alt=media)

## 4. Operation

When the SafeSkin is switched on, the robot arm will immediately enter the pause status as long as an object approaches the SafeSkin. At this time, you will see a pop-up window on the software. The robot will resume operation only after you manually confirm to continue running the script. In addition, you can also select to exit running in the pop-up window.

### 4.1 SafeSkin settings and display

1. Install the SafeSkin plug-in in Dobot+ page of the software, and open it.
2. Click the switch icon on the right side of SafeSkin switch to turn on (or off) the

SafeSkin function. The robot arm responds to the approaching object only when the function is switched on. There is a special color block to display each sensing area of the SafeSkin, When the obstacle in the sensing area gradually approaches the robot, the color of the block turns darker accordingly.

3. Set the sensitivity of each SafeSkin. Separate sensitivity setting can improve the

suitability of SafeSkin in complex scenes. For example, in a fixed working trajectory, if a SafeSkin is very close to a fixed mechanism, you can turn the sensitivity of this skin down to ensure that the robot will not trigger proximity pause or obstacle avoidance actions frequently due to the action of this skin. The sensitivity range is described below.

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHyxohU2nn3i2u6LnWETE%2Fsafeskin-cra-p011-img01.jpg?alt=media)

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRfXrAqR5EykVYoRNn9fs%2Fsafeskin-cra-p011-img02.jpg?alt=media)

* OFF: Switch off the SafeSkin of the corresponding part.
* Low: Proximity distance ≤ 5cm
* Medium: Proximity distance ≤ 10cm
* High: Proximity distance ≤ 15cm

Click Restore on the upper-right corner to set the sensitivity to the default value. Click Reset to reset the trigger status of SafeSkin, which is mainly used for handling when the safety skin is mistakenly triggered.

### 4.2 Programming commands

After installing the Dobot+ plug-in, you will see the SafeSkin commands on Blockly page and Script page. In addition, you can also set the SafeSkin status through TCP/IP commands. The SafeSkin status set through programming commands is the same to Dobot+, including the SafeSkin switch and sensitivity of each part, but the SafeSkin settings through programming commands take effect only in the corresponding project or TCP mode. After exiting the project or TCP mode, the SafeSkin settings will restore to the pre-modified value.

#### 4.2.1 Blockly command

Command Description Enable or disable the SafeSkin. Parameter Select the status of SafeSkin, including Open and Close. Command Description Set the sensitivity of each part of SafeSkin. Parameter • Select a part to set the sensitivity, including forearm, J4, J5 and J6.

* Select the sensitivity, including OFF, Low, Medium and High.

#### 4.2.2 Script command

Command EnableSafeSkin(ON|OFF) Description Enable or disable the SafeSkin. Parameter ON|OFF: ON means switching on the SafeSkin, and OFF means switch off the SafeSkin. Return • 0: Not detected SafeSkin

* 1: Detected SafeSkin

EnableSafeSkin(ON) Example Switch on the SafeSkin function. Command SetSafeSkin(part,status) Description Set the sensitivity of each part of SafeSkin. Parameter • part: Part of the robot, range: 3 – 6 ◦ 3: Forearm ◦ 4: Joint 4 ◦ 5: Joint 5 ◦ 6: Joint 6

* status: Sensitivity, range: 0 – 3

◦ 0: OFF ◦ 1: Low sensitivity ◦ 2: Medium sensitivity ◦ 3: High sensitivity Return None SetSafeSkin(3,0) Example Set the SafeSkin sensitivity of the forearm to 0.

#### 4.2.3 TCP/IP command

Command EnableSafeSkin(status) Description Enable or disable the SafeSkin. Parameter Status: 0: OFF, 1: ON. Return ErrorID,{},EnableSafeSkin(status); EnableSafeSkin(1) Example Switch on the SafeSkin function. Command SetSafeSkin(part,status) Description Set the sensitivity of each part of SafeSkin. Parameter • part: Part of the robot, range: 3 – 6 ◦ 3: Forearm ◦ 4: Joint 4 ◦ 5: Joint 5 ◦ 6: Joint 6

* status: Sensitivity, range: 0 – 3

◦ 0: OFF ◦ 1: Low sensitivity ◦ 2: Medium sensitivity ◦ 3: High sensitivity Return ErrorID,{},SetSafeSkin(part,status); SetSafeSkin(3,0) Example Set the SafeSkin sensitivity of the forearm to 0.

## 5. Technical specifications

Product name DOBOT CR3AS DOBOT CR5AS DOBOT CR10AS Robot arm weight 19kg (41.9lb) 26.5kg (58.4lb) 43kg (94.8lb) Maximum load 3 kg (6.6 lb) 5 kg (11 lb) 10 kg (22 lb) Working radius 620 mm (24.4 in) 900 mm (35.4 in) 1300 mm (51.2 in) Maximum linear 2 m/s (78.7 in/s) speed J1 ±360° J2 ±360° Joint J3 ±155° ±160° ±160° motion J4 ±360° range J5 ±360° J6 ±360° J1 180°/s 180°/s 150°/s J2 180°/s 180°/s 150°/s Joint J3 223°/s 180°/s 180°/s Maximum J4 223°/s speed J5 223°/s J6 223°/s DI 2 DO 2 Tool I/O AI 2 RS485 Support (two AIs multiplexing) Repeatability ±0.02 mm ±0.02 mm ±0.03 mm IP rating IP20 Noise 70 dB(A) Temperature 0 – 50 Typical power ℃ ℃ 120W 150W 350W consumption Installation mode Any angle

Product name DOBOT CR3AS DOBOT CR5AS DOBOT CR10AS Cable length from 5m (16.4 feet) robot to controller Material Aluminium alloy, ABS, silica gel SafeSkin parameter Sensing type Proximity sensing, tactile sensing Human body, metal, liquid, etc. (conductor, slightly weaker Sensing object induction to non-conductor) Installation position Forearm to end Sensing distance 5 – 15 cm (different parts vary) Reaction cycle 0.01s Emergency stop time 0.1s
