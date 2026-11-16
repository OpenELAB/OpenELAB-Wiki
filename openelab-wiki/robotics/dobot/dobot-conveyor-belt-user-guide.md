---
description: >-
  User guide for the DOBOT conveyor belt kit used with Magician and Magician
  Lite, covering the kit components, hardware connections, picking and sorting
  demonstrations, position adjustment, and trouble
---

# DOBOT Conveyor Belt User Guide

## DOBOT Conveyor Belt for Magician and Magician Lite

{% embed url="https://openelab.io/products/dobot-conveyor-belt-magician-lite" %}

## Contents

* Preface
* Conveyor Belt Kit Overview
* Hardware Connection
* Conveyor Belt Picking and Sorting Demo
* Position Adjustment
* Run the Conveyor Belt
* Precautions

Copyright © ShenZhen Yuejiang Technology Co., Ltd. 2018. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without prior written consent of Yuejiang Technology Co., Ltd. Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. Yuejiang makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non- infringement of third party rights. In no event will Yuejiang be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robotic arm is used on the premise of fully understanding the robotic arm and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, Damages or losses will be happen in the using process, Dobot shall not be considered as a guarantee regarding to all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robotic arm. ShenZhen Yuejiang Technology Co., Ltd. Address: 3F, Building NO.3, Tongfuyu Industrial Town, Nanshan District, Shenzhen, China Website: https://www.dobot.cc/

## Preface

Purpose This document describes that how to install Conveyor Belt kit and help user to use it. Intended Audience This document is intended for:

* Customer Engineer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Change History Date Change Description 2019/03/26 Update picking and sorting demos 2017/7/3 The first release Symbol Conventions The symbols that may be founded in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not

**DANGER avoided, could result in death or serious injury**

Indicates a hazard with a medium level or low level of

**WARNING risk which, if not avoided, could result in minor or**

moderate injury, robotic arm damage Indicates a potentially hazardous situation which, if not

**NOTICE avoided, can result in robotic arm damage, data loss, or**

unanticipated result

**NOTE Provides additional information to emphasize or**

supplement important points in the main text

## Conveyor Belt Kit Overview

Conveyor belt kit contains conveyor belt, color sensor and photoelectric sensor as shown in

_Figure 1.1._

_Figure 1.1 Conveyor Belt Kit_

**NOTICE**

Please turn off the Dobot Magician completely before plugging or unplugging external modules, such as Infrared sensor, Color sensor and so on, otherwise, it will damage your Dobot. Magician. Only the status LED indicator turns off, the Dobot Magician has powered down completely after you turn off the power of the Dobot Magician. The operational steps are shown below:

* Install the photoelectric sensor and color sensor.
* Turn on the Dobot Magician power, the buzzer beeps three times, indicating that the module has finished initializing.
* For the Dobot Magician details, please refer to Dobot Magician User Guide.

![Figure 1.1.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNe2JpeC8PION6eEXI2B6%2Fconveyor-belt-p005-img02.jpg?alt=media)

## Hardware Connection

This topic describes how to connect Conveyor Belt Kit. The connection shown in this topic is available for Dobot Magician V1 and Dobot Magician V2, and we will use Dobot Magician V1 to give a connection example as shown in Figure 2.1.

_Figure 2.1 The whole connection example_

**NOTE**

The Dobot 1 is used to pick block and the Dobot 2 is used to sort block.

### Conveyor Belt Connection

Connect the motor wire of the conveyor belt to the interface Stepper1 on the base of the Dobot 1.

_Figure 2.2 Conveyor Belt connection_

### Color Sensor Connection

Connect the power wire of the Color Sensor to the interface GP1, GP2, GP4 or GP5 on the Dobot 2 (This document takes interface GP2 as an example).

![Figure 2.1 The whole connection example](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4cjmqABgwAt6U8pjIb0M%2Fconveyor-belt-p006-img04.jpg?alt=media)

![Figure 2.2 Conveyor Belt connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKQJbGBxpDJuUC2Cxbc1K%2Fconveyor-belt-p006-img05.jpg?alt=media)

_Figure 2.3 Color Sensor connection_

### Photoelectric Sensor Connection

Connect the power wire of the photoelectric sensor to the interface GP1, GP4 or GP5 on the Dobot 2 (This document takes interface GP4 as an example).

_Figure 2.4 Photoelectric Sensor connection_

The final connection is shown in Figure 2.5 and Figure 2.6.

_Figure 2.5 Dobot 1 connection_

![Figure 2.3 Color Sensor connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fhv34rvNwB0hHX6o3sCI3%2Fconveyor-belt-p007-img02.jpg?alt=media)

![Figure 2.4 Photoelectric Sensor connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgeHdzrP1vj1G8dSwo0fj%2Fconveyor-belt-p007-img03.jpg?alt=media)

![Figure 2.5 Dobot 1 connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYM8LsrZL65pzLdbxdQHy%2Fconveyor-belt-p007-img04.jpg?alt=media)

![Official manual figure, page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkGg0oLbhI6WAZ9QaMOtH%2Fconveyor-belt-p007-img05.jpg?alt=media)

![Official manual figure, page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7iv6gjLlZN0L2HnClbZT%2Fconveyor-belt-p007-img06.jpg?alt=media)

_Figure 2.6 Dobot 2 connection_

![Figure 2.6 Dobot 2 connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFnqHDNE1lnBlwlwWIESK%2Fconveyor-belt-p008-img01.jpg?alt=media)

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQmcEvZWjJSQThI1AZNps%2Fconveyor-belt-p008-img02.jpg?alt=media)

## Conveyor Belt Picking and Sorting Demo

Preparation

* The DobotStudio has been installed.
* The Dobot Magician has been connected to your computer.
* The demos have been downloaded from our official website.

The download path of DobotStudio is https://www.dobot.cc/downloadcenter.html. As shown in Figure 3.1.

_Figure 3.1 Get DobotStudio_

The download path of the demos is https://www.dobot.cc/downloadcenter/conveyor-belt- kit.html?sub\_cat=103#sub-download. As shown in Figure 3.2.

_Figure 3.2 Get the demos_

Step 1. Put the two demos for picking and sorting into the path Installation path/DobotSutido/config/bystore or other folders. As shown in Figure 3.3.

![Figure 3.1 Get DobotStudio](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2kaIeoSWVNqpUyrZmYyD%2Fconveyor-belt-p009-img02.png?alt=media)

![Figure 3.2 Get the demos](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxkbXNFLvTyd1XAT12eBV%2Fconveyor-belt-p009-img03.jpg?alt=media)

_Figure 3.3 Save demos_

Step 2. Launch two DobotStudio clients, and open Blockly module and import the picking demo and the sorting demo respectively. As shown in Figure 3.4 and Figure 3.5.

_Figure 3.4 Open Blockly module_

_Figure 3.5 Import demo_

Step 3. If the Dobot Studio client imports the picking demo, connect it to the Dobot 1, otherwise,

![Figure 3.3 Save demos](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZ5K8pfCXAVqUSUgg99Ud%2Fconveyor-belt-p010-img01.png?alt=media)

![Figure 3.4 Open Blockly module](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0LRtVSHFQu7Id7rzmP2i%2Fconveyor-belt-p010-img02.jpg?alt=media)

![Figure 3.5 Import demo](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7vdoof34xg7L8AK8fB8v%2Fconveyor-belt-p010-img03.png?alt=media)

connect it to the Dobot 2. As shown in Figure 3.6 and Figure 3.7.

_Figure 3.6 Import the picking demo_

_Figure 3.7 Import the sorting demo_

![Figure 3.6 Import the picking demo](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnBonIDZD4yw6NpcDNBur%2Fconveyor-belt-p011-img01.png?alt=media)

![Figure 3.7 Import the sorting demo](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjrQrZapLA1nOaGiSMesH%2Fconveyor-belt-p011-img02.png?alt=media)

## Position Adjustment

### Adjusting Picking and Placing Positions of Dobot 1

* Adjusting picking position

1. Press and hold down the Unlock button on the forearm to move the Dobot 1 to make

suction cup on the block. As shown in Figure 4.1.

_Figure 4.1 Picking position_

**NOTE**

You can move the Dobot 1 by the DobotStudio to make the suction cup on the center of the block.

2. The operation panel on the DobotStudio will record the values of X, Y, Z axes

automatically, and write the values of the X, Y, Z axes in the picking demo as shown in Figure 4.2.

_Figure 4.2 Modify the picking position_

![Figure 4.1 Picking position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FF9U2jx3GZtF1xXnh79Qw%2Fconveyor-belt-p012-img03.jpg?alt=media)

![Figure 4.2 Modify the picking position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFrOSrODCHjjN7evrY9fP%2Fconveyor-belt-p012-img04.png?alt=media)

* Adjusting the Placing Position

1. Select SuctionCup to pick up the blocks, and then press and hold down the Unlock

button to move the Dobot 1 to make the blocks on the conveyor belt. As shown in

_Figure 4.3._

_Figure 4.3 Adjust Placing position_

2. Unselect SuctionCup to put down blocks on the conveyor belt. The operation panel

on the DobotStudio will record the values of X, Y, Z axes automatically, and write the values of the X, Y, Z axes in the picking demo as shown in Figure 4.4.

_Figure 4.4 Modify the placing position_

* Adjusting the stopping position

Control the conveyor belt move a distance by setting the speed and time in the picking demo to make these blocks in a position where is in the workspace of the Dobot 2.

![Figure 4.3.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fkn1lV5N5P54VvOoxfqaa%2Fconveyor-belt-p013-img01.jpg?alt=media)

![Figure 4.3 Adjust Placing position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUxXXoDKvuWNxnuAIqAc7%2Fconveyor-belt-p013-img02.png?alt=media)

_Figure 4.5 Adjust the stopping position_

### Adjusting Sorting Position of Dobot 2

* Adjust picking position

1. Press and hold down the Unlock button on the forearm to move the Dobot 2 to make

the suction cup on the center of the block. As shown in Figure 4.6.

_Figure 4.6 Adjust picking position_

**NOTE**

You can move the Dobot 2 by the DobotStudio to make the suction cup on the center of the block.

2. The operation panel in DobotStudio will record the values of X, Y, Z axes

automatically, and write the values of the X, Y, Z axes in the sorting demo as shown in Figure 4.7.

![Figure 4.5 Adjust the stopping position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGfSPBKyuyTVpme6innWN%2Fconveyor-belt-p014-img02.png?alt=media)

![Figure 4.6 Adjust picking position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyQ27rpIV6rhIi0W8yI6F%2Fconveyor-belt-p014-img03.jpg?alt=media)

_Figure 4.7 Modify picking position_

* Adjust color-identified position

1. Select SuctionCup to pick up the block, and then press and hold down the Unlock

button to move the Dobot 2 to make the block above the color sensor. The distance range between the color sensor and block should be 5mm to 10mm. As shown in

_Figure 4.8._

_Figure 4.8 Adjust color-identified position_

2. The operation panel on the DobotStudio will record the values of X, Y, Z axes

automatically, and write the values of the X, Y, Z axes in the sorting demo as shown in Figure 4.9.

![Figure 4.7 Modify picking position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSVvTazj9uPHGDJAc5K6E%2Fconveyor-belt-p015-img01.jpg?alt=media)

![Figure 4.8.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPAPnCRg7MQ6O4HemAIIU%2Fconveyor-belt-p015-img02.jpg?alt=media)

_Figure 4.9 Modify color- identified position_

* Adjust placing position

1. Press and hold down the Unlock button to move the Dobot 2 to make the block on a

placing position. As shown in Figure 4.10.

_Figure 4.10 A placing position_

**NOTE**

Make sure that this position is in the workspace of the Dobot Magician.

2. The operation panel on the DobotStudio will record the values of X, Y, Z axes

automatically, and write the values of the X, Y, Z axes in the sorting demo as shown in Figure 4.11.

![Figure 4.9 Modify color- identified position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrQPf8NnZuTCKmLtcjQfq%2Fconveyor-belt-p016-img01.jpg?alt=media)

![Figure 4.10 A placing position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3Gw6t36ZvymKaJh08loX%2Fconveyor-belt-p016-img02.jpg?alt=media)

_Figure 4.11 Modify placing position_

3. Click Save to save the settings.

_Figure 4.12 Save the settings_

![Figure 4.11 Modify placing position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FE5p0V3bAXxjxZv2FYlio%2Fconveyor-belt-p017-img01.png?alt=media)

![Figure 4.12 Save the settings](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeOXH3dsYkSyFN7m3jl9Q%2Fconveyor-belt-p017-img02.jpg?alt=media)

## Run the Conveyor Belt

1. Modify 0 to 1 in the Test:0; Run:1 module when running the picking demo as shown in

_Figure 5.1._

_Figure 5.1 Modify 0 to 1_

2. Click Start to run the Dobot 2 first, and then run the Dobot 1.

_Figure 5.2 Start the Dobot 2_

![Figure 5.1.](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhwIeYT4XZE5WFymXQruN%2Fconveyor-belt-p018-img02.jpg?alt=media)

![Figure 5.1 Modify 0 to 1](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbmSetO0Cee3xeRyW4cIA%2Fconveyor-belt-p018-img03.jpg?alt=media)

_Figure 5.3 Start the Dobot 1_

![Figure 5.3 Start the Dobot 1](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNAOkIv0SUiUIb22EPgbe%2Fconveyor-belt-p019-img01.jpg?alt=media)

## Precautions

* You need to reset Dobot Magician before running the conveyor belt, adjust and save positions after 20s. Reset Dobot Magician again, and run conveyor belt after 20s.
* The homing point should be set higher to avoid crash. If Dobot Magician loses step, you need to operate homing procedure again.

## Appendix A Setting the Home Position

Step 1. Open DobotStudio, connect Dobot Magician and click Teaching\&Playback as shown in Attach Figure 6.1. Attach Figure 6.1 Teaching\&Playback Step 2. Click + point to save a point of which the axes X, Y, Z, R are 250, 0, 50, 0 respectively. You can set the point based on site requirements. Attach Figure 6.2 Add Point

**NOTE**

Make sure that this position is in the workspace of the Dobot Magician. Step 3. Select this point and right-click SetHome. As shown in Attach Figure 6.3.

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F00mtOWgpUg7u1fWiRmwk%2Fconveyor-belt-p021-img02.jpg?alt=media)

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAUD3tXm2bNtDWMFUtPTX%2Fconveyor-belt-p021-img03.jpg?alt=media)

Attach Figure 6.3 Set home position Step 4. If the settings are successful, it will pop up a tip as shown Attach Figure 6.4, click OK. Click Home to check whether the setting is available, if not, please set the homing position again after pressing down the reset key on base of Dobot Magician. Attach Figure 6.4 Setting tip

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTG2uNv5eenG6c2DPZET0%2Fconveyor-belt-p022-img01.png?alt=media)

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAyEZdrkUqKGLnaakVJdg%2Fconveyor-belt-p022-img02.jpg?alt=media)
