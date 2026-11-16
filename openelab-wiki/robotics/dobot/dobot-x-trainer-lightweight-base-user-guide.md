---
description: >-
  Official V1.6 user guide for the DOBOT X-Trainer Lightweight Base AI robot
  operating platform.
---

# DOBOT X-Trainer Lightweight Base User Guide

## DOBOT X-Trainer Dual-Arm Robot for AI Data Collection

{% embed url="https://openelab.io/products/dobot-x-trainer-data-robot" %}

[Official manual PDF, V1.6](https://dobot-cloud-1256299428.cos.accelerate.myqcloud.com/dobot/Dobot%20X-Trainer%20\(Lightweight%20Base\)%20User%20Guide_V1.6_20260205_en.pdf)

## Contents

* Preface
* 1\. Product Introduction
* 2\. Hardware Installation
* 3\. Configuring the operating environment
* 4\. Teleoperation and Data Collection
* 5\. Algorithm Training for Imitation Learning
* 6\. Running the Autonomous Inference
* 7\. Data Interface

## Copyright and Disclaimer

### Copyright © SHENZHEN DOBOT CORP LTD 2024–2026. All rights reserved.

No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as "Dobot").

### Disclaimer

To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided **AS IS** , which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents.

Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot arm is used on the premise of fully understanding the robot arm and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document.

The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot arm.

SHENZHEN DOBOT CORP LTD Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China

Website: www.dobot-robots.com

## Preface

#### Purpose

This document is used to guide users to install and configure the Dobot X-Trainer AI Robot Operating Platform (Lightweight Base).

#### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

#### Revision history

|**Date**|**Version**|**Revision history**|

|2026/02/05|V1.6|Replace Anaconda with Miniforge.| |2025/06/04|V1.5|The third release, content optimization and updates| |2024/07/31|V1.1|The second release, content optimization| |2024/05/24|V1.0|The first release|

#### Symbol conventions

The symbols that may be found in this document are defined as follows.

| **Symbol**  | **Description**                                                                                                                                             |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DANGER**  | <p>Indicates a hazard with a high level of risk which, if not avoided,<br>could result in death or serious injury.</p>                                      |
| **WARNING** | <p>Indicates a hazard with a medium level or low level of risk which, if<br>not avoided, could result in minor or moderate injury, robot arm<br>damage.</p> |
| **NOTICE**  | <p>Indicates a potentially hazardous situation which, if not avoided,<br>could result in robot arm damage, data loss, or unanticipated<br>result.</p>       |
| **NOTE**    | <p>Provides additional information to emphasize or supplement<br>important points in the main text</p>                                                      |

## 1. Product Introduction

### 1.1 Overview

At present, research on Artificial General Intelligence (AGI) at home and abroad has entered a new upsurge, with Embodied AI being recognized as a crucial step towards AGI. A promising approach to developing Embodied AI is imitation learning from human demonstrations. This approach, known as behavior cloning, allows robots to acquire various fundamental skills, ranging from simple pick-and-place operations to more complex manipulation tasks.

The kit offers a platform for bimanual teleoperation, enabling intuitive, dexterous, and precise control of slave hands by directly manipulating the master hands to achieve reliable, efficient and high-quality demonstration data collection. The kit also provides basic demonstration program for data collection, algorithm training, and inference, along with a comprehensive API for the entire platform. This API includes interfaces for: Master-hand joint angle reading, Master-hand locking control, Slave-hand joint angle and Cartesian coordinate reading/control, Gripper stroke control, and Camera RGB/depth image acquisition.

With this hardware platform and customizable development interfaces, flexible and diverse research on robot applications can be conducted. For example, Household service robots help people with daily chores such as cooking, cleaning and organizing. Industrial automation robots perform tasks such as assembly and quality inspection.

### 1.2 Components

* **Master hands** : High-precision 6-DOF (degrees of freedom) master hands, one for each side, each equipped with an operation handle (see the figure below) at the end.

#### Master Hand Sensor Not Installed Master Hand Sensor Installed

* **Slave hands:** Nova 2 robot arms (version 3.5.8.1 or higher), one for each side. The slave hand will follow the master hand after synchronizing with it.

**NOTICE** The Nova series robot requires firmware version V3.5.8.1 or higher. If the current version is lower, users must upgrade the firmware. The slave hand's firmware version can be checked via "run\_control.py" script in Configuring and collecting data.

* **Grippers** : One at the end of each slave hand with a maximum stroke of 95mm. The gripper is controlled by the trigger at the end of the master hand after synchronizing with it.

![Official manual image, source page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXZIzemfjMY2rkHe5icV3%2Fxtrainer-v16-p007-img01.jpg?alt=media)

![Official manual image, source page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F48JQMYGOHcec2oPgfKcb%2Fxtrainer-v16-p007-img02.jpg?alt=media)

![Official manual image, source page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgEm7KVkEbP5RiIgvTZMw%2Fxtrainer-v16-p007-img03.jpg?alt=media)

* **Cameras** : Three Intel RealSense D405 cameras. One is mounted on the camera bracket as a global camera, and each slave hand has one camera mounted at its end.
* **E-Stop switches** : The emergency stop switch of the slave hand. Pressing any one will brake both slave hands in an emergency.
* **Indicator** : Tricolor indicator light, with the following meanings.
  * Light-off: Master and slave hands are not synchronized.
  * Yellow: Master and slave hands are synchronized but not recording data.
  * Green: Data recording.
  * Red: Error.
* **Electric control cabinet** : It uses mains power as the power input. For details on the interfaces at the rear of the cabinet, see Electric control cabinet interface.
* **Fixed base** : The mounting base for X-Trainer, including the camera bracket.

### 1.3 Electric control cabinet interface

① : 5 network interfaces, for connecting the slave-hand controller (CCBOX) and computer.

② : 2 E-Stop switch interfaces.

③ : 2 robot E-Stop output interfaces, for connecting to the E-Stop input interfaces of the slave-hand controller.

④ : 24V output interfaces (2 rows, 6 sets in total), mainly used to power the slavehand grippers.

![Official manual image, source page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSpYYDgs9HRiszFt0Mmt0%2Fxtrainer-v16-p008-img01.png?alt=media)

## 2. Hardware Installation

### 2.1 Installation environment

To maintain the X-Trainer performance and to ensure the safety, please place the X- Trainer in an environment with the following conditions.

* Install indoors with good ventilation.
* Keep away from excessive vibration and shock.
* Keep away from direct sunlight and radiant heat.
* Keep away from dust, oil mist, smoke, salinity, metal powder, corrosive gases, and other contaminants.
* Do not use in a closed environment. A closed environment may cause the controller to overheat and shorten its service life.
* Keep away from flammable.
* Keep away from cutting and grinding fluids.
* Keep away from sources of electromagnetic interference.

### 2.2 Unpacking

Before unpacking, please carefully check the outer packaging for signs of damage in transportation. If any damage is found, please unpack in the presence of shipping company staff.

When unpacking, please check the attached shipping list to ensure that all contents are included and intact. If anything is missing or damaged, please contact your supplier.

After unpacking, please save all packaging materials for future transportation.

In addition to the standard parts provided with the X-Trainer, users need to prepare the following parts.

* Prepare a computer for teleoperation and algorithm training (hereafter referred to as the **training host** ), with the following specifications (lower specifications are acceptable for teleoperation only):

|**Configuration item**|**Recommended config**\
|**uration**\
|

||**Teleoperation only**|**Algorithm training**| |Graphics card|GTX1050|RTX4090, 24GB VRAM\
(minimum: RTX2080 Ti,\
11GB VRAM)| |CPU|Intel i5-9300H|Intel i9-14900KF| |RAM|16 GB|32 GB| |Hard drive|1 TB|2TB SSD| |Operating system|Ubuntu 20.04||

* Prepare another computer (Windows 7/10/11 operating system, you can also install dual systems on the training host) or a tablet (Android 10 or above, or iOS 10 or above) to install the control software for the slave hand (Nova2) (hereafter referred to as the **slave-hand operation terminal** ), with the following specifications:

| **Terminal type**                                              | PC                                                                                                                   | Tablet (Android)                                                      | iPad                                        |
| -------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- | ------------------------------------------- |
| <p><strong>Operating</strong><br><strong>system</strong></p>   | Windows7/10/11                                                                                                       | <p>Android 10 and<br>above</p>                                        | <p>iOS 10 and<br>above</p>                  |
| <p><strong>Control</strong><br><strong>software</strong></p>   | DobotStudio Pro                                                                                                      | Dobot CRStudio                                                        | <p>Dobot<br>CRStudio</p>                    |
| **Minimum**                                                    | <p>CPU: Intel Core<br>i3<br>Memory: 4G<br>Hard drive space:<br>128GB<br>Network card:<br>Gigabit-NIC<br>VRAM: 1G</p> | <p>CPU: 4-core<br>RAM: 2G<br>Storage space: 32G<br>Screen: 8-inch</p> | <p>iPad 5th-<br>generation<br>and above</p> |
| <p><strong>Communication</strong><br><strong>mode</strong></p> | LAN/WiFi                                                                                                             | WiFi                                                                  | WiFi                                        |

*  If WiFi communication is required, please select the WiFi module for Nova when purchasing the X-Trainer.
* Prepare a power strip that meets local standards, with at least 5 additional sockets available for the X-Trainer in addition to the socket for computer.

### 2.3 Installation steps

#### 2.3.1 Overall layout

The lightweight-base X-Trainer base measures 1400mm x 1000mm (excluding handles), and the overall layout is shown below.

The EVA foam is included in the shipping list and should be arranged according to the figure below. The 6 fixed feet on both sides are shipped as separate parts. If the user needs to fix the base to the tabletop, use M5\*10 screws to install the fixed feet.

#### 2.3.2 Installing electric control cabinet

Take out the electric control cabinet from its packaging box and place it next to the base.

#### 2.3.3 Installing slave hand

**Tools needed** : Allen wrenc&#x68;_&#x32; (M3/M6), M&#x33;_&#x38; screws.

1. Remove 4 M6 hex screws from the mounting plate of slave hand 1 (highlighted in red in the figure below). Take out one slave hand (Nova 2) from its packaging and use the removed screws to fasten it onto the mounting plate, **with the heavyduty cable facing towards the left** . When moving the robot from its packaging box to the mounting position, hold the robot until all bolts on the robot base are fastened.

![Official manual image, source page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuuR2lkJGNtH0Qq1q6CTE%2Fxtrainer-v16-p011-img01.png?alt=media)

2. Place the slave-hand controller (CCBOX, as shown in the figure below) near the slave hand, leaving at least 50mm of space on each side for heat dissipation.
3. Refer to the above steps to install the other slave hand to the installation position for Slave hand 2, **with the heavy-duty cable facing towards the right** . Both slave hands should be symmetrically mirrored, with an approximate distance of 93 cm between them.

![Official manual image, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyY2WoIRerbvgIkFSuQuC%2Fxtrainer-v16-p012-img01.jpg?alt=media)

![Official manual image, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH4I44UHGdPdb0NQ7jSu6%2Fxtrainer-v16-p012-img02.png?alt=media)

![Official manual image, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd8ZxXNUam4T1UePZHJpH%2Fxtrainer-v16-p012-img03.png?alt=media)

4. Refer to the figure below to connect the cables for the slave hands (both slave hands are connected in the same way).

The RB-STOP cable is shown below, with the black terminal connected to the CCBOX and the green terminal connected to the electric control cabinet.

![Official manual image, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHv4eSL6XO5PyGLy2x4Y%2Fxtrainer-v16-p013-img01.jpg?alt=media)

![Official manual image, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHEa7BJmlmAZUvdLM4f8u%2Fxtrainer-v16-p013-img02.jpg?alt=media)

![Official manual image, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWsG4gVzFBWdpi6qBm1Bt%2Fxtrainer-v16-p013-img03.jpg?alt=media)

#### 2.3.4 Installing E-Stop switch

Place the E-Stop switch on the mounting base and connect the cable to the E-Stop switch interface of the electric control cabinet.

#### 2.3.5 Installing master hand

**Tools needed** : Allen wrench\*1 (M5).

1. Remove three M4\*25 hex screws from the mounting base of Master hand 1 (highlighted in red in the figure below). Take out one master hand from its packaging box and use the removed screws to fasten it onto the mounting plate, **with the wiring panel facing towards the left** .

The cylindrical base shown in the figure below is pre-installed on the master hand mounting plate. Depending on the site requirements (e.g., if the operator’s seating height is lower), it can be removed, and the master hand can be directly mounted onto the lower mounting plate.

![Official manual image, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1h2gaNhs1UO0fxM8TFt3%2Fxtrainer-v16-p014-img01.png?alt=media)

![Official manual image, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSS7r5SJVan2yyuEiMvzQ%2Fxtrainer-v16-p014-img02.png?alt=media)

2. Refer to the above steps to install the other master hand to the installation position for Master hand 2, **with the wiring panel facing towards the right** . Both master hands should be symmetrically mirrored.
3. Refer to the figure below to connect the power cable and data cable for the master hands (both master hands are connected in the same way).

#### 2.3.6 Installing global camera

**Tools needed** : Allen wrenc&#x68;_&#x32; (M4/M6), M&#x36;_&#x31;2 screws, M6\*8 screws, M6 flat gaskets.

**NOTE** Before installing the camera, it is recommended to record the ID (as shown in the figure below) and installation position of each camera for future configuration.

![Official manual image, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkcSO9hM1ZLHuexPqeX77%2Fxtrainer-v16-p015-img01.jpg?alt=media)

![Official manual image, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPP8uiAE3nM8L07RpCVa7%2Fxtrainer-v16-p015-img02.jpg?alt=media)

![Official manual image, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXdpofun8EFvqbqZ2adGE%2Fxtrainer-v16-p015-img04.jpg?alt=media)

1. Prepare the global camera bracket, which consists of two vertical bars and one horizontal bar. The vertical bars are 1240mm in length, and the horizontal bar is 1400mm in length.
2. Align the horizontal bar and vertical bars at the sticker positions as shown in the figure below, and assemble them using four M6\*12 screws.

NOTE<br>

Both the horizontal and vertical bars have built-in T-nuts. When assembling, slide the nuts to the appropriate positions to fix the screws. This will not be repeated in subsequent instructions.

3. Take out the camera mounting kit (as shown in the figure below). Align the vertical sheet metal with the sticker on the horizontal bar (as shown in the figure above), and use 2 M6\*12 screws to fix it.

![Official manual image, source page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOsONdAJzh9pJQSV1eLIk%2Fxtrainer-v16-p016-img01.jpg?alt=media)

![Official manual image, source page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMEjNte6HCrngngHSxbVe%2Fxtrainer-v16-p016-img02.jpg?alt=media)

4. Use 1 M6\*8 screws and 3 M6 flat gaskets to install the global camera.

**NOTE** After installation, refer to the figure below to verify the angle of the camera bracket (with the center of the two screw holes located on extended blue line on the sticker). If not aligned, adjust it manually. The screw specification here is M4\*10.

5. Insert the global camera bracket between the two L-shaped parts on the slavehand’s base plate. At this point, the centerline of the vertical bar should align with the sticker on the L-shaped part. Then, use 2 M6\*12 screws to fix it.

![Official manual image, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlIE4Omm6yXulGlwGd9IH%2Fxtrainer-v16-p017-img01.png?alt=media)

![Official manual image, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgIAIBOLNYGkWYL42rztS%2Fxtrainer-v16-p017-img02.jpg?alt=media)

![Official manual image, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOHDxUebDybxQlCwaxrH5%2Fxtrainer-v16-p017-img04.jpg?alt=media)

6. Connect the camera cable as shown in the figure below.

The camera cable is shown below.

**NOTICE**

* Ensure that the camera and master hands are connected to different USB hubs, and the USB hub for the camera is connected to a USB 3.0 interface on the computer.
* Make sure the camera cable is securely connected to prevent any data collection issues due to a poor connection.

![Official manual image, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8v5HyoDyV9gsqQTPFq59%2Fxtrainer-v16-p018-img01.png?alt=media)

![Official manual image, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkAXpAxRGRpYVsI4T5VVI%2Fxtrainer-v16-p018-img02.jpg?alt=media)

![Official manual image, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA9Nhv5BfPhYY2Iq3TzHt%2Fxtrainer-v16-p018-img03.jpg?alt=media)

#### 2.3.7 Installing slave-hand gripper and camera

**Tools needed** : Allen wrenc&#x68;_&#x32; (M3/M6), M&#x36;_&#x31;2 screws, M&#x33;_&#x36; screws, camera calibration car&#x64;_&#x31;.

Before installing the slave-hand gripper and camera, refer to Powering on slave hand and Slave hand settings. Move slave hand 1 and slave hand 2 to their initial positions, then power them off before proceeding with the installation.

After installation of slave-hand grippers and cameras, the two cameras should be positioned as shown in the figure below.

#### Installing slave-hand gripper

1. Take out the gripper from its packaging box, remove 6 M3\*14 screws, and separate the gripper body from the adapter.
2. Use 4 M6\*12 screws to secure the gripper adapter to the end flange of the slave hand.
3. Use 6 M3\*14 screws to fix the gripper body to the adapter. **The two slave-hand grippers are installed in different orientations. Please refer to the figure below and pay attention to the position of the end-flange aviation socket, the gripper adapter, and the gripper body.**

![Official manual image, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLazgXzr7oQzEFryQZUU0%2Fxtrainer-v16-p019-img01.jpg?alt=media)

![Official manual image, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfnUc2yUN0TbwbOeYm7fF%2Fxtrainer-v16-p019-img02.png?alt=media)

4. Connect the gripper cable 485 as shown in the figure below.

The gripper cable 485 is shown in the figure below, and the wiring instructions are listed in the table below.

|**Cable label (Color)**|**Peer interface**|**Peer device**|

|A (Green)|T/R+|USB-485 conversion| |B (White)|T/R-|module| |24V (Red)|24V|Electric control cabinet| |GND (Black)|0V|| |PE (Black)||N/A|

![Official manual image, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdbeDn4AapwEd3CfCqoIZ%2Fxtrainer-v16-p020-img01.png?alt=media)

![Official manual image, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsogOPVODeCpjb4Eskt6h%2Fxtrainer-v16-p020-img02.jpg?alt=media)

5. Connect the gripper fan cable: Attach the gripper fan cable to the GVBA port on the opposite side of the gripper adapter.

**NOTE** The GVBA ports on both sides of the gripper adapter are functionally identical. The gripper cable 485 and gripper fan cable can be connected to either side.

#### Installing slave-hand camera

1. Use 2 M3\*6 screws to mount the camera onto the camera bracket.

**NOTICE** The cameras on the two slave hands need to be installed in opposite orientations. Ensure that when the two cameras are facing each other, their labels are oriented towards the user.

2. Use 2 M3\*6 screws to mount the camera bracket onto the gripper adapter.

![Official manual image, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvrwjmEykeaT2bcAnaLup%2Fxtrainer-v16-p021-img01.jpg?alt=media)

![Official manual image, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjIJReR1RZA66nC149jNn%2Fxtrainer-v16-p021-img02.jpg?alt=media)

3. After installation, it is recommended to adjust the camera position as shown in the figure below. Align the center of the screw hole on the side of the bracket with the blue lines on the sticker. Then, use the fan-shaped calibration card included in the shipment to adjust the angle, ensuring the upper corner forms a 112-degree angle.

**4.** Connect the camera cables. The connection method is the same as for the global camera.

**NOTICE**

* Ensure that the camera and master hands are connected to different USB hubs, and the USB hub for the camera is connected to a USB 3.0 interface on the computer.
* Make sure the camera cable is securely connected to prevent any data collection issues due to a poor connection.

#### 2.3.8 Connecting the indicator

The indicator is factory installed on the base. Use the indicator cable to connect the Indicator and the **Slave-hand 1** controller. Ensure the cable labels align with the silkscreens on the controller, and organize the cables to the left side of the terminal after connecting.

![Official manual image, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIWCxstLFM1Q3qXhOSVbq%2Fxtrainer-v16-p022-img01.png?alt=media)

#### 2.3.9 Connecting the training host

Use the network cable to connect the training host to the electric control cabinet.

#### 2.3.10 Organizing the cables

After completing the installation and connection, organize the cables as shown below. Use the Velcro provided (shipped as a whole roll, to be cut by the user) to secure the gripper and camera cables to the slave hand, preventing cable strain when the slave hand is moving.

![Official manual image, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIQllRGLwdNZIbP7xsxF5%2Fxtrainer-v16-p023-img01.jpg?alt=media)

![Official manual image, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMZPFwlbjjQx4MqDIHAf1%2Fxtrainer-v16-p023-img02.png?alt=media)

The shipping list also includes a pack of plastic ties for organizing additional cables.

#### 2.3.11 Powering on device

#### Powering on master hand

The power switch for the master hand is located on the base. Press the switch to power the master hand on, press again to power the master hand off.

#### Powering on slave hand

The power switch for the slave hand is located on the controller (CCBOX). Short-press to power the slave hand on, long-press (over 3 seconds) to power the slave hand off.

![Official manual image, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fltp1TzimK2D0Q3hwHhJq%2Fxtrainer-v16-p024-img01.jpg?alt=media)

![Official manual image, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJv7SKJXNFhd59uJ04akE%2Fxtrainer-v16-p024-img02.jpg?alt=media)

#### Powering on slave-hand gripper

The slave-hand gripper is powered by the electric control cabinet. Connect the electric control cabinet to the power supply to power it on. The power interface of the electric control cabinet is located on the front side (opposite to the network interface).

#### Powering on camera

The cameras are powered by the training host via USB. The camera powers on automatically after the training host is powered on.

![Official manual image, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9R4jl8ho8t70pHtzWiTW%2Fxtrainer-v16-p025-img01.jpg?alt=media)

![Official manual image, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9mkAome591DwXjk9TEoJ%2Fxtrainer-v16-p025-img02.jpg?alt=media)

## 3. Configuring the operating environment

Unless otherwise specified, the following operations are performed on the training host. If you encounter any issues during configuration and use that are not covered in this document, please refer to the _Dobot X-Trainer Operation Guide and FAQ_ for solutions (Visit Dobot official website, click "Support > Download Center", and search by document name or filter by product series).

### 3.1 Operating system

It is recommended to use a Linux system: either Ubuntu 20.04 or 23.10.

**NOTE**

*  Dobot has not verified the configuration and use of the training and inference environment on other versions of Linux or on Windows systems, so we cannot provide corresponding guidance.
*  Compared to Linux systems, master-slave teleoperation has higher latency on Windows systems (approximately an additional 10ms).
*  It is prohibited to install the system and run programs through a virtual machine, otherwise errors such as insufficient resources or robot connection timeouts may occur.
* Avoid using Chinese characters when naming folders. It is recommended to use English letters and numbers.

### 3.2 Installing CUDA and cuDNN

**NOTE:** This section can be skipped if only master–slave teleoperation is required. The official example uses CUDA 11.8 on Ubuntu 20.04; choose driver, CUDA, cuDNN and PyTorch versions compatible with the actual graphics card.

1. Obtain the appropriate CUDA runfile instructions from [NVIDIA's CUDA 11.8 download archive](https://developer.nvidia.com/cuda-11-8-0-download-archive).
2. Download the runfile in a terminal. The official example is:

```bash
wget https://developer.download.nvidia.com/compute/cuda/11.8.0/local_installers/cuda_11.8.0_520.61.05_linux.run
```

3. Start the installer:

```bash
sudo sh cuda_11.8.0_520.61.05_linux.run
```

4. Follow the installer prompts. The official guide instructs users to deselect the bundled GPU driver to avoid replacing a newer installed driver.
5. Open the shell configuration file with a text editor, for example:

```bash
sudo gedit ~/.bashrc
```

6. Add these paths, adjusting them if CUDA was installed elsewhere:

```bash
export PATH=/usr/local/cuda-11.8/bin:$PATH
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.8/lib64
```

7. Restart the operating system, then confirm that `nvcc -V` displays the compiler version.
8. Obtain the appropriate cuDNN package and installation commands from [NVIDIA's cuDNN download page](https://developer.nvidia.com/cudnn-downloads), and complete its installation.

![Official CUDA installation reference, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVkrD455go06KBdWXr5NN%2Fxtrainer-v16-p027-img01.png?alt=media)

### 3.3 Installing Miniforge

The V1.6 official guide uses Miniforge instead of the Anaconda workflow in earlier revisions.

1. Download the Linux x86-64 installer:

```bash
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
```

2. Change file permissions as instructed in the official guide, then run the installer:

```bash
sudo chmod 777 Miniforge3-Linux-x86_64.sh
./Miniforge3-Linux-x86_64.sh
```

3. Follow the prompts. Open `~/.bashrc`, for example with `sudo gedit ~/.bashrc`, then add the installation directory to `PATH`. Replace `/home/dobot/Miniforge3` with the actual location:

```bash
export PATH="/home/dobot/Miniforge3/bin:$PATH"
source ~/.bashrc
conda -V
```

The final command should display the installed Conda version.

![Official Miniforge setup reference, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOtJ92zRkDpGq2SGkPFJY%2Fxtrainer-v16-p028-img01.png?alt=media)

### 3.4 Configuring the virtual environment

1. Create and activate the example Python 3.8.10 environment. Confirm with `y` if prompted:

```bash
conda create -n Xtrainer python==3.8.10
conda activate Xtrainer
```

![Official Conda environment reference, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F21FkTUijtJFaHGPpRGzl%2Fxtrainer-v16-p029-img01.jpg?alt=media)

![Official Conda environment reference, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F414o4juWcgjpmKTgASy8%2Fxtrainer-v16-p029-img02.jpg?alt=media)

2. If training or inference is needed, install the versions listed by DOBOT for its CUDA 11.8 example:

```bash
pip install torch==2.0.1 torchvision==0.15.2 torchaudio==2.0.2 --index-url https://download.pytorch.org/whl/cu118
```

3. Verify in an interactive Python session:

```python
import torch
import torchvision
torch.cuda.is_available()
```

The last expression should return `True` when the CUDA stack is correctly available. 4. In the `Dobot_Xtrainer` demo project, install the required packages:

```bash
pip install -r requirements.txt
pip install -e third_party/DynamixelSDK/python
```

The official guide additionally lists the following for training/inference; they are not required for master–slave teleoperation alone:

```bash
pip install -e ModelTrain/detr
pip install -e robomimic-r2d2
sudo apt install libxcb-cursor0
```

5. In the IDE, select the Python interpreter inside the `Xtrainer` Miniforge environment. The official PyCharm example uses **File > Settings > Python Interpreter > Add Interpreter > Existing** and the installed `Miniforge3/envs/Xtrainer/bin/python3` path.

![Official PyCharm interpreter reference, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FE548HPulHJ0OKtWmQCcP%2Fxtrainer-v16-p030-img01.jpg?alt=media)

**Source-consistency caution:** The official guide contains a conflicting `192.158.5.1` address in section 3.5.1, whereas later instructions use the `192.168.5.x` network. Confirm the physical controller's current address and DOBOT's latest network instructions before changing robot IP settings.

### 3.5 Slave hand settings

#### 3.5.1 Modifying the IP of slave hand 2

Both slave hand 1 and slave hand 2 have the same default IP address for their LAN1 interface (192.158.5.1). To avoid conflicts, you need to modify the IP address of slave hand 2 (right hand) to 192.168.5.2. Follow the steps below to modify the IP address, with specific operations referenced in the DobotStudio Pro help documentation.

1. Use the network cable to connect the CCBOX of slave hand 2 to the **slave-hand operation terminal (e.g., a computer)** .
2. Modify the IP address of the computer used for connecting to the slave hand to the 192.168.5.xxx subnet (subnet mask 255.255.255.0) without conflicting with the IPs of the two slave hands. For example, set it to 192.168.5.102.

![Official manual image, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F68vWzQS3EerOvt3NBdLQ%2Fxtrainer-v16-p031-img01.jpg?alt=media)

3. Open the control software (DobotStudio Pro 2.x.x) on the computer and connect to the detected Nova 2.
4. Go to “Settings > Communication settings”. Select “Set IP manually” on the “IP Configuration” page, and modify the IP to 192.168.5.2.
5. Click “Apply”.

If the LAN1 interface of the CCBOX is used for connection, reconnect the LAN1 interface to the electric control cabinet via the network cable after the configuration is completed. Then, connect the **slave-hand operation terminal** to the electric control cabinet, as shown in the figure below.

![Official manual image, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FswMJvaTxMA3oX8M6gPAb%2Fxtrainer-v16-p032-img01.png?alt=media)

![Official manual image, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fy5zoqGicGdq169eRPUdU%2Fxtrainer-v16-p032-img02.jpg?alt=media)

#### 3.5.2 Configuring slave hand 1 and 2

#### Perform the following operations for slave hand 1 and slave hand 2 respectively.

1. Manually add the IP addresses of the two slave hands in DobotStudio Pro.
2. Use DobotStudio Pro to connect to the slave hand.
   * Slave hand 1 (left hand): Nova 2 (192.168.5.1).
   * Slave hand 2 (right hand): Nova 2 (192.168.5.2).

When the slave hand is successfully connected, the main interface menu bar will display "Connected" and "Online".

![Official manual image, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu08w2Gg7avhiuoS553Cr%2Fxtrainer-v16-p033-img01.png?alt=media)

![Official manual image, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F13g1qCtprQnnKhtzWUZp%2Fxtrainer-v16-p033-img02.jpg?alt=media)

![Official manual image, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9Bo1IuRU3oakPIrS8U6p%2Fxtrainer-v16-p033-img03.jpg?alt=media)

3. Click the Enable switch at the top right of the interface and set the payload to 0.5kg.
4. Set the initial posture for slave hand.
   * a) Go to “Settings > Basic settings” page, click “Reset Initial Pose” on the right of “Initial Posture”.

* b) Set the Initial Pose to the following values (which represent the joint angles J1 to J6 respectively), and click **“** OK **”** .

Slave hand 1: {-90, 0,-90, 0, 90, 90}

* Slave hand 2: {90, 0, 90, 0, -90, -90}
* c) Long-press “Move to Default Pose” until the slave hand reaches the initial point.

![Official manual image, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmIVvTnxzryx8z0mbNFhA%2Fxtrainer-v16-p034-img01.jpg?alt=media)

![Official manual image, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fco9h1qNKMdP4KLeOYWa6%2Fxtrainer-v16-p034-img02.jpg?alt=media)

![Official manual image, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNDdoZIfV4d6PEL0LEXNf%2Fxtrainer-v16-p034-img03.jpg?alt=media)

![Official manual image, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fxuyo5Cibbc0yuvvFWT6i%2Fxtrainer-v16-p034-img04.jpg?alt=media)

**NOTICE**

During moving, observe carefully. If a collision is likely to occur, release the button and jog to avoid obstacles before continuing to move to the initial point.

5. Go to “Settings > Remote control” page, set the “Current mode” to “TCP/IP secondary development”, and click “Apply”.

After completing the above configurations, all subsequent operations will be performed on the **training host** . If the slave hand reports errors or other abnormal statuses, use the **slave-hand operation terminal** to open DobotStudio Pro for troubleshooting.

### 3.6 Configuring the training host IP

Modify the IP address of the training host used for connecting to the electric control cabinet to the 192.168.5.xxx subnet (subnet mask 255.255.255.0), without conflicting with the IPs of the two slave hands and the slave-hand operation terminal. For example, set it to 192.168.5.102 (the figure below takes Ubuntu’s settings interface as an example). After configuration, turn on the switch of the corresponding wired network.

![Official manual image, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSQegLBLRKUGrjJnWWNLL%2Fxtrainer-v16-p035-img01.jpg?alt=media)

## 4. Teleoperation and Data Collection

### 4.1 How to use master hand

This section introduces how to use the handle at the end of the master hand. Refer to this section to operate the robot after completing the configuration according to Configuring and collecting data.

#### Master Hand Sensor Not Installed

#### Master Hand Sensor Installed

* Unlock/Sync button (left yellow button):
  * Short-press (0.5s) to lock or unlock the master hand. When unlocked, the master hand can be freely dragged.
  * Long-press (2s) to sync or disconnect sync. When synced, the slave hand will slowly sync to the current posture and normal operation speed of the master hand. Once the sync is completed, teleoperation control of the slave hand can begin.
  * The left and right master hands need to use this button separately for unlocking and synchronization.
*
* Record button (right green button):
* Short-press (0.5s) to start recording and collect data once, short-press again to stop recording.
* Once the master-slave sync is successful, pressing the record button on either side will start or stop the overall data recording of the X-Trainer. Recording data for only one side is not supported.
*
* Gripper control trigger:

Press the trigger to close the slave-hand gripper. Release the trigger to open the slave-hand gripper. The gripper stroke can be controlled by the distance the trigger is pressed.

* Sensor:

When the hand accidentally releases the master hand, the sensor can detect the disengagement and automatically disengage the master-slave synchronization, stopping the slave hand's movement to prevent it from falling and damaging the equipment (this feature is only supported by X-Trainer installed with master hand sensors).

![Official manual image, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F57PvkjSUf2QFtChY0gQc%2Fxtrainer-v16-p037-img01.jpg?alt=media)

![Official manual image, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2W29s6icK60zKjemh04i%2Fxtrainer-v16-p037-img02.jpg?alt=media)

**NOTICE**

* Hold the handle with both hands before unlocking the master hand to prevent accidental falling of the master or slave hand.
* Ensure an appropriate safety distance between the master hands and lock them in a safe position before synchronizing the master hand and robot slave hands to prevent accidental falling, collision, or other anomalies.
* Do not collide with the master hand after it is locked to prevent servo damage.
* Ensure the slave hands do not interfere with each other during operation, which could damage the robot arms or cameras.

### 4.2 Configuring and collecting data

1. Open the Dobot\_Xtrainer folder in IDE (here takes PyCharm as an example).

**NOTICE** It is highly recommended to use **PyCharm** to run the scripts, as other tools like VSCode may cause script execution conflicts or unexpected termination.

2. Modify the scripts > dobot\_config > dobot\_settings.ini file.
   * a) Locate to the "passcode" code line, change the password to your local computer’s password for executing the sudo commands.

* b) Locate to the \[CAMERA], and fill in the IDs for each camera. top: Global camera. left: Slave hand 1 camera. right: Slave hand 2 camera.

![Official manual image, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZjQoZ0mGTxG5z7etJAfM%2Fxtrainer-v16-p038-img01.png?alt=media)

![Official manual image, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGkeaXGP9dmNn5QDT3eHT%2Fxtrainer-v16-p038-img02.jpg?alt=media)

* c) Locate to the "using\_sensor" code line: If the master hand has a sensor installed, set "using\_sensor" to 1; If the master hand does not have a sensor, set "using\_sensor" to 0.

3. After saving the configuration, it is recommended to run scripts > 5\_camera\_read.py to check if the program can correctly read the camera images.

![Official manual image, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1ayXonTMPdJHSpCtmMp4%2Fxtrainer-v16-p039-img01.jpg?alt=media)

![Official manual image, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJRqwHM43ZHPgr3mrWpEC%2Fxtrainer-v16-p039-img02.jpg?alt=media)

![Official manual image, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNUCwfqp0bTnQYvuT6hPD%2Fxtrainer-v16-p039-img03.jpg?alt=media)

**NOTE** The method to run the script: Right-click on the script page and select "Run xx.py" or click the Run button in the menu bar.

The expected output is shown in the figure below.

If the camera images are abnormal or the script reports an error, please reconnect the camera data cables and verify that each camera ID is correctly filled in, then rerun the script.

After completing the camera test, please manually stop the script.

4. Run scripts > 1\_find\_port.py to configure the USB interfaces for the two master hands and two slave-hand grippers.

The script needs to be re-run every time the training host is powered off or the USB interfaces are reconnected.

5. Set the sync posture for master and slave hands.

After completing this step, the synchronized posture of the master and slave hands will be saved in dobot\_settings.ini. Unless there are issues such as desynchronization of the master and slave hands or loss of the configuration file, there is no need to repeat the settings.

* a) Run scripts > 3\_just\_buttonA.py. After running, you can unlock and drag the master hand.

![Official manual image, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiPQH5PY2tnzuJxJyNbDd%2Fxtrainer-v16-p040-img01.jpg?alt=media)

![Official manual image, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbEBWzT3aUsmyo3QU7J7o%2Fxtrainer-v16-p040-img02.jpg?alt=media)

* b) Hold the handles at the end of both master hands and short-press the yellow button to unlock them. Drag both master hands until their posture matches the initial posture of the slave hands (refer to Configuring slave hand 1 and 2). Short-press the yellow button again to lock the master hands.
* c) Stop running 3\_just\_buttonA.py script. Before proceeding to the next step, ensure that the script has completely stopped. For example, in PyCharm, if the stop button does not disappear after the first click, click the stop button again. The script is considered stopped only when the stop button disappears.
* d) Run scripts > 2\_get\_offset.py script to set the current posture of the master and slave hands as the base value for synchronization.

![Official manual image, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fuhotz16bCsAuRsH6XGIc%2Fxtrainer-v16-p041-img01.jpg?alt=media)

![Official manual image, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGdPwXSug87NhkCa59AlL%2Fxtrainer-v16-p041-img02.jpg?alt=media)

6. Run experiments > launch\_nodes.py to start the server process for the slave hands.

**Script-name caution:** The official V1.6 guide refers to `run_inference.py` in the following setup step but to `run_control.py` in the subsequent recording and recovery steps. Verify the actual filenames in your delivered SDK before running the workflow.

7. Open experiments > run\_inference.py:
   * (1) Locate to the "project\_name" code line and customize the dataset name according to your training task.
   * (2) Locate to the "using\_sensor\_protection” code line and configure whether to enable the master hand sensor. True enables sensor protection, False disables sensor protection (This setting only applies to X-Trainer equipped with a master hand sensor).

* (3) After completing the above configurations, save and run the script.

**NOTICE** When running this script, it will automatically detect the firmware versions of the left and right slave hands. For Nova series robot, it requires firmware version V3.5.8.1 or higher. If the current version is lower, users must upgrade the firmware.

![Official manual image, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv3QXZjP2I5XPpKUhwxpa%2Fxtrainer-v16-p042-img01.jpg?alt=media)

![Official manual image, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F07KNYNatRL5WyBQZOHgU%2Fxtrainer-v16-p042-img02.jpg?alt=media)

8. Once both the launch\_nodes.py and run\_control.py scripts have finished running, teleoperation and training data recording can begin.

**NOTICE**

* find\_port.py, launch\_nodes.py, and run\_control.py must be started in sequence and kept running (do not close them, otherwise teleoperation may fail).
* Recommended recording attempts per task: 50–100 times. The more recordings, the higher the reproduction accuracy.
* During the entire teleoperation process, the green button on the master hand's end handle controls the start and stop of recording.
* After clicking the Stop button in the script window's menu bar, the entire teleoperation process will end, and both the master hand's recording and master-slave control will stop.

For safety, Dobot has set limits for teleoperation related to speed and operation position. Triggering these limits will cause teleoperation to stop, and the indicator on the table will turn red to signal an alarm. In such cases, you need to stop and re-run the run\_control.py script to clear the alarm.

**NOTICE** After re-running the script, it is recommended to:

1. Short-press the yellow button to unlock the master hands, and drag them to the initial position and lock them.
2. Long-press the yellow button to sync the slave hand posture.
3. Unlock the master hands for teleoperation.

By default, the slave-hand gripper can only operate above the EVA foam area on the workbench. If necessary, you can modify the activity area limits for the slave hand in the run\_control.py script (as shown in the figure below). Ensure you have thoroughly evaluated the potential safety risks before making any changes.

![Official manual image, source page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeGd5dpnXz9Vjjxt0Fcms%2Fxtrainer-v16-p043-img01.jpg?alt=media)

## 5. Algorithm Training for Imitation Learning

### 5.1 Processing training dataset

After data collection is complete, you can find a folder with the same name as the dataset (i.e., the project\_name in experiments > run\_control.py) in the datasets folder, which is at the same level as Dobot\_XTrainer (hereinafter referred to as the “training data folder”).

This folder should initially contain only a collect\_data folder, which holds the raw collected data. If you need to use the collected data for algorithm training, you'll first need to compress and consolidate it. The steps are as follows:

1. Open scripts > 4\_collect2train\_data.py. Modify the dataset\_name to the name of the actual recorded dataset.
2. Run the script to compress and integrate the training data.
3. Once the script has finished running, two new folders will be generated in the training data folder: output\_videos and train\_data.
   * output\_videos contains the videos captured by the camera during training, which can be used to check for any issues in the data collection operation.
   * train\_data contains the processed training data, which will be used in subsequent training steps.

### 5.2 Setting dataset parameters

The official guide spells the dataset configuration file as `contants.py` in this section and `constants.py` elsewhere. Verify the filename in the delivered SDK. Open that file under `ModelTrain` and modify these parameters:

![Official manual image, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2Pz66XrHMj0QjIexbDVn%2Fxtrainer-v16-p045-img02.jpg?alt=media)

① : The path of the dataset folder, which is the parent directory of the aforementioned train\_data folder.

**NOTE** It is recommended to use absolute paths for all addresses involved in the SDK to avoid file-not-found errors during subsequent training data processing.

② : Task name.

③ : Set to /train\_data, so that ① + ③ equals the full path of the train\_data folder from the previous section.

④ : The number of collection steps. Run scripts > 6\_dataset\_count.py to get the maximum number of steps in the dataset, then set this parameter to a slightly higher value. For example, if the maximum number of steps in the dataset is 410, you can set this parameter to 500.

![Official manual image, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2dojUI7vttif9VqHvuIV%2Fxtrainer-v16-p046-img01.jpg?alt=media)

![Official manual image, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdEMUkhxAAjVR5ewddwVj%2Fxtrainer-v16-p046-img02.jpg?alt=media)

* a: Run the script after modifying it with the actual dataset name.
* b: The maximum number of steps obtained for this dataset after running the script.

⑤ : The proportion of the training set; the remaining data will be used as the validation set.

⑥ : Camera name. If camera-related code has not been modified, keep the defaults. After modification, save the file.

### 5.3 Setting training-related parameters

Open the ModelTrain > model\_train.py script and modify the default values for the following parameters accordingly.

* ckpt\_dir: Set the path where the trained model will be saved. This path must be under the ModelTrain directory and should be a relative path based on this directory.
* task\_name: The task name, which needs to match the parameter with the same name in ModelTrain > constants.py.
* batch\_size: Size of the batch during training, set it based on the graphics card’s performance (e.g., 16 for a single RTX 4090).
* num\_steps: Number of training iterations.
* lr: Learning rate.
* validate\_every: Number of iterations between each validation.
* save\_every: Number of iterations between each model save.
* resume\_ckpt\_path: If you want to continue training based on a previously saved model, use the first resume\_ckpt\_path line (and comment out the second line). The default should be the model path. If you intend to retrain by mixing the original data, use the second resume\_ckpt\_path line (and comment out the first line). No default value is provided.
* chunk\_size: Length of the action sequence predicted by the algorithm at one time.
* temporal\_agg: Action time smoothing, recommended to set to True.
* Other parameters can be kept at their default values.

![Official manual image, source page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOE7OgRp7CIxGMMbkYFJT%2Fxtrainer-v16-p047-img01.jpg?alt=media)

### 5.4 Start training

1. After modification, save and run ModelTrain > model\_train.py to start training model as shown in the figure below. Please be patient, as training can take some time. For the first training session, an Internet connection is required to download the pre-trained model. Subsequent training sessions will not require an Internet connection.
2. Once training is complete, the console will display "Train finished" and a curve graph showing the training results will pop up, as shown in the figure below.
3. The trained model will be saved in the path specified by the ckpt\_dir parameter in model\_train.py. This folder contains multiple models. For inference, it is common to use either policy\_last.ckpt (the last trained model) or policy\_best.ckpt (the model with the best validation accuracy).

![Official manual image, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvSX5o1Pl20MJb5BkNV2c%2Fxtrainer-v16-p048-img01.jpg?alt=media)

![Official manual image, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FL6kfek8gWJf0lv0poW7W%2Fxtrainer-v16-p048-img02.jpg?alt=media)

4. Open the ModelTrain > model\_inference\_test.py script file. Input the collected dataset images and slave hand joint values (including gripper stroke values) into the trained model. Record the action values of slave hand joint and gripper output from the model. Compare the output values with the dataset label values to make an initial assessment of the model's prediction accuracy.

![Official manual image, source page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2NVmf1Xp2m1WjmrGDn8L%2Fxtrainer-v16-p049-img01.png?alt=media)

## 6. Running the Autonomous Inference

1. Open experiments > run\_inference.py, and modify the following parameters:

* model\_name: Model name. Set it to policy\_last.ckpt (the latest trained model) or policy\_best.ckpt (the model with the best validation accuracy).
* ckpt\_dir: Path to the model directory, as specified in ModelTrain > model\_train.py.
* episode\_len: Length of the task steps, which must be less than or equal to the value specified in ModelTrain > contants.py. You can adjust this parameter to trim the length of the action sequence for autonomous inference. For example, if the robot does not complete the target action during autonomous inference, you can increase the step length; if the robot performs some extra actions after completing the target action, you can decrease the step length.

After modification, save the file.

2. Run experiments > launch\_nodes.py to start the server process for the slave hands.
3. Run experiments > run\_inference.py to start the autonomous operation of the slave hand based on inference.

**NOTICE**

Ensure that the parameters in run\_inference.py match those used during the training in model\_train.py.

## 7. Data Interface

Dobot provides a set of DEMOs to demonstrate how to get data from Dobot XTrainer. These DEMOs are located in the example folder of the Dobot XTrainer project.

* example\_agent.py: Demonstrate how to get the joint angles and button information of the master hand.
* example\_camera.py: Demonstrate how to obtain images from the camera.
* example\_dobot\_robot.py: Demonstrate how to set the indicator and get joint angles of the slave hand.
* example\_gripper.py: Demonstrate how to control the slave-hand gripper.
* example\_read\_data\_from\_dataset.py: Demonstrate how to parse data from the dataset.
