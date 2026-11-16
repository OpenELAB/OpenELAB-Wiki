---
description: >-
  User guide for the DOBOT ES01 electric suction cup, covering structure,
  interfaces, hardware installation, software control, troubleshooting, and
  specifications.
---

# DOBOT ES01 Electric Suction Cup User Guide

## DOBOT ES01 Electric Suction Cup End Effector

{% embed url="https://openelab.io/products/dobot-es01-electric-suction-cup" %}

## DOBOT E6 Robot with ES01 Electric Suction Cup

{% embed url="https://openelab.io/products/dobot-e6-es01-suction-robot" %}

## Contents

* Preface
* 1\. Product Introduction
* 2\. Hardware Installation
* 3\. Software
* 4\. Technical Specifications

Copyright © Shenzhen Yuejiang Technology Co., Ltd 2024. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of Shenzhen Yuejiang Technology Co., Ltd (hereinafter referred to as “Dobot”). Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot arm is used on the premise of fully understanding the robot arm and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot arm. Shenzhen Yuejiang Technology Co., Ltd. Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

## Preface

Purpose This document introduces the installation and usage of Dobot ES01 electric suction cup, which is convenient for users to understand and use the suction cup. Intended audience This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Revision history Date Version Revised content 2024/03/05 V1.0 The first release Symbol conventions The symbols that may be found in this document are defined as follows. Symbol Description

**DANGER Indicates a hazard with a high level of risk which, if not avoided, could result**

in death or serious injury.

**WARNING Indicates a hazard with a medium level or low level of risk which, if not**

avoided, could result in minor or moderate injury, robot arm damage.

**NOTICE Indicates a potentially hazardous situation which, if not avoided, could result**

in robot arm damage, data loss, or unanticipated result.

**NOTE Provides additional information to emphasize or supplement important**

points in the main text.

## 1. Product Introduction

### 1.1 Overview

The Dobot ES01 electric suction cup is an accessory for the Dobot Magician E6 robot. It can be installed at the end of the robot arm and can be controlled via IO. It supports quick control through the plugin of DobotStudio Pro. The Dobot ES01 electric suction cup adopts an integrated design, eliminating the need for an external air source and control source. The end of the suction cup is equipped with an aviation plug, which is compatible with the aviation socket of Magician E6. It is plug-and-play and requires no external wiring and hardware adaptation. The Dobot ES01 electric suction cup is compact and lightweight, with lower operating noise. It can adapt to different sizes of objects to be gripped by changing the suction nozzles, which perfectly meets the teaching needs.

![Official manual figure, page 5](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKHeyahoi9Ripix5dkjjY%2Fes01-p005-img01.jpg?alt=media)

### 1.2 Structure

* Top cover of suction cup: It is used to connect the suction cup body and the robot arm. It comes with an aviation connector cable for connecting the aviation socket at the end of the robot arm.
* Suction cup body: It generates suction by a built-in electric vacuum pump. There is a status indicator on the front with the following meanings. Status Definition Green light on Idle/adsorbing/releasing Slowly-flashing green (1Hz) Object has been adsorbed Red light on Motor overheating Quickly-flashing red (5Hz) Object dropped
* Suction nozzle: It is supplied with two suction nozzles, one large and one small. The specifications are as follows. You can change it according to your actual needs.
* Brand: SMC, Model: ZPT13BS-AG1, Diameter: 13mm, Suitable for objects to be gripped within 300g.
* Brand: SMC, Model: ZP3E-T32UMS-AG1, Diameter: 32mm, Suitable for objects to be gripped within 700g.

![Official manual figure, page 6](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjtX1tyhjSd67qSOoR9Em%2Fes01-p006-img01.jpg?alt=media)

### 1.3 Mechanical specifications

### 1.4 Electrical interface

The suction cup body is connected to the top cover through 8 pins, and the interfaces are defined as follows. Pin Definition Pin Definition 1 24V 5 DI1 2 DO2 6 DI2 3 DO1 7 Reserved 4 GND 8 Reserved The top cover of the suction cup is connected to the end of Magician E6 through the aviation plug interface. DI and DO are PNP type, and the interfaces are defined as follows. Pin Definition 1 24V 2 DO1 3 DO2 4 DI1 5 DI2 6 GND

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv4yt1ktX54MTOjWGm4Vq%2Fes01-p008-img01.jpg?alt=media)

## 2. Hardware Installation

### 2.1 Operating environment

* Operating temperature: 0℃ – 40 ℃, humidity: 25% – 85% (non-condensing).
* Ambient temperature for transportation and storage: -20℃ – 70℃, humidity: 25% – 85%

(non-condensing).

* Install indoors with good ventilation.
* Keep away from excessive vibration and shock.
* Keep away from direct sunlight.
* Keep away from dust, oily smoke, salinity, metal powder, corrosive gases, and other contaminants.
* Keep away from flammable.
* Keep away from cutting and grinding fluids.
* Keep away from sources of electromagnetic interference.

### 2.2 Installation steps

1. Connect the top cover of the suction cup to the aviation socket at the end of the robot arm

using the aviation connector cable.

2. Fix the top cover of the suction cup to the end flange of the robot arm using four M4

screws.

3. Fix the suction cup body to the top cover using four M2.5 screws, align the pins and

positioning slots of the body with that of the top cover.

4. Install the nozzle according to your actual needs. The large nozzle (as shown in the figure

below) can be disassembled and assembled by holding the nozzle with your fingers and rotating it. The small nozzle can be disassembled and assembled by using a small wrench to rotate the hex nut at the top.

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fip7koeTXtls9R60b1cbK%2Fes01-p009-img01.png?alt=media)

## 3. Software

### 3.1 Plugin installation and use

DobotES01 electric suction cup plugin needs to be used with DobotStudio Pro V4.5.1 and above. For instructions on how to use DobotStudio Pro, please refer to its help document.

1. Open DobotStudio Pro and connect it to the robot.
2. Go to the Dobot+ page and install the DobotES01 plugin.
3. Open the DobotES01 plugin, you can view the current status of the suction cup and

control the suction cup to adsorb or release.

* Click Adsorb to control the suction cup to adsorb the object.
* Click Release to control the suction cup to release the object.
* Click Clear Alarm to clear the alarm.

Suction cup status: Status Definition Blue light Idle status Green light Object has been adsorbed Red light Alarm

### 3.2 Shortcut key settings

After installing the DobotES01 plugin, you can set the function of robot end shortcut keys. Click End shortcut key in the upper right corner of the Dobot+ home page to enter the configuration page. The left side of the configuration page shows the position of the end button and the definition of Shortcut key 1 and Shortcut key 2, while the right side is used to configure the button functions.

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkKI6BweTulYMqYnGZJ3q%2Fes01-p010-img02.jpg?alt=media)

![Official manual figure, page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXO8wpJASuNOwRyfZ1c6o%2Fes01-p010-img03.jpg?alt=media)

* For Plugin list, select DobotES01 plugin;
* For Shortcut key 1/2, you can configure it as follows:

◦ DobotES\_Grip: Control the suction cup to adsorb. ◦ DobotES\_Release: Control the suction cup to release.

* For Long press, you can configure it as DobotES\_ClearAlarm, which is used to clear the alarm. After configuration, click Save, and you can control the suction cup with the robot end shortcut keys.

### 3.3 Programming instructions

#### 3.3.1 Blockly programming

Description: Obtain the status of the suction cup. Return:

* 0: Idle status
* 1: Adsorbing
* 2: Alarm

Description: Control the suction cup. Parameter: Select Adsorb or Release.

#### 3.3.2 Script programming

Command: DobotESStatusGet() Description: Obtain the status of the suction cup. Return:

* 0: Idle status
* 1: Adsorbing
* 2: Alarm

Example: status = DobotESStatusGet() Command: DobotESGrip()

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FguNEvpUVILGeGNbipUsH%2Fes01-p011-img01.jpg?alt=media)

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj7EVZ9VA7R6PKVWu7NuC%2Fes01-p011-img02.jpg?alt=media)

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2bz1P0BzpCZIBMTBiL8x%2Fes01-p011-img03.jpg?alt=media)

Description: Control the suction cup to adsorb. Example: DobotESGrip() Command: DobotESRelease() Description: Control the suction cup to release. Example: DobotESRelease()

### 3.4 Exception handling

* Motor overheating: After the suction cup has been working for a long time, the motor overheating alarm may occur, and the red light of the suction cup body will always be on. In this case, it is recommended to stop the suction cup (control the suction cup to release) and leave it for a while, wait for the suction cup to cool down, clear the alarm, and then you can continue to use it. If you continue to use the suction cup after it reports motor overheating, the suction cup may be overheated and be forced to stop, and the adsorbed objects may drop.
* Object dropped: After the suction cup picks up the object, if it detects the object dropped before releasing it, an object dropped alarm may occur, and the red light of the suction cup body will flash quickly. In this case, it is recommended to stop the suction cup (control the suction cup to release), clear the alarm, and then adsorb the object again.

## 4. Technical Specifications

Product model DT-ES01 Size (&#x4C;_&#x57;_&#x48;) 7&#x34;_&#x36;&#x35;_&#x36;5mm Weight 250 g Maximum payload 700 g Vacuum degree 55 kPa Maximum flow 2.0LPM (24.0V) Fastest adsorption time 0.3s Fastest release time 0.4s Communication mode IO IP rating IP20 Noise 50 dB Rated voltage DC 24V Rated power 2.55W Peak power 3.67W Operating temperature 0℃ – 40℃ Relative humidity for operating 25% – 85% (non-condensing) environment Transportation and storage -20℃ – 70℃ temperature Relative humidity for transportation 25% – 85% (non-condensing) and storage Material PC+ABS Certification CE, RoHS

1. The maximum payload is a theoretical value. The actual value depends on the shape of the

object to be gripped, the friction of the contact surface, and the center of gravity of the object to be gripped. If you have any questions, please contact Dobot technical support.

2. The parameters above are subject to change without prior notice for product improvement.
