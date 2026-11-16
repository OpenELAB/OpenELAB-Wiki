---
description: >-
  User guide for the DOBOT collaborative robot teach pendant, covering safety,
  installation, controls, operation, maintenance, warranty, and specifications.
---

# DOBOT Cobot Teach Pendant User Guide

## DOBOT CRA Series Teach Pendant for Collaborative Robot Control

{% embed url="https://openelab.io/products/dobot-cra-series-teach-pendant" %}

## Contents

* Preface
* 1\. Safety
* 2\. Product Introduction
* 3\. Mechanical Specifications
* 4\. Installation and Use
* 5\. Maintenance
* 6\. Warranty
* Appendix Technical specifications

Copyright © Shenzhen Yuejiang Technology Co., Ltd 2024. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of Shenzhen Yuejiang Technology Co., Ltd (hereinafter referred to as “Dobot”). Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot. Shenzhen Yuejiang Technology Co., Ltd. Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

## Preface

Purpose This document introduces the appearance, functions, installation and use of Dobot teach pendant, which is convenient for users to understand and use the teach pendant. Intended audience This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Revision history Date Version Revised content 2024/02/29 V1.0 The first release Symbol conventions The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could result

**DANGER**

in death or serious injury. Indicates a hazard with a medium level or low level of risk which, if not

**WARNING**

avoided, could result in minor or moderate injury, robot arm damage. Indicates a potentially hazardous situation which, if not avoided, could result

**NOTICE**

in robot arm damage, data loss, or unanticipated result. Provides additional information to emphasize or supplement important

**NOTE**

points in the main text.

## 1. Safety

### 1.1 Safety instructions

This section contains general safety precautions, please read before installing the teach pendant.

**WARNING**

1. Installation or maintenance of device connected to the power supply may result

in electric shock. Please ensure that the device is disconnected before installation or maintenance.

2. Improper power connection may lead to device damage or personnel injury.

Please ensure that the power supply is properly connected.

3. As the operation terminal of the robot, the teach pendant should be used in full

compliance with the safety instructions of the robot. See the corresponding robot user guide for details.

4. Dropping may cause the screen to be broken, please be careful.

**NOTICE**

Before installing and using the teach pendant, a risk assessment based on the overall robot system is required to avoid device damage or personnel injury.

### 1.2 Emergencies

#### 1.2.1 Emergency stop device

In case of emergency, press the emergency stop switch, the robot arm will stop all movement and lock. Emergency equipment is not a safety guard according to IEC 60204-1 and ISO 13850. They are supplemental protective measures and are not intended to prevent injury.

_Figure 1.1 Emergency stop switch_

#### 1.2.2 Emergency recovery

The emergency stop switch will be locked after you press it. To unlock the switch, you need to rotate the switch according to the mark on it. The alarm can be cleared through the software only after the emergency stop switch is unlocked. Then the robot arm can be powered on, enabled and resumed from the emergency status.

![Figure 1.1 Emergency stop switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxbjgBwn8qXRY76klN4Wb%2Ftp10-p005-img01.jpg?alt=media)

**WARNING**

Please operate the robot to recover from the emergency status only after the danger of the robot system is completely removed.

## 2. Product Introduction

### 2.1 Appearance

The teach pendant is the operation terminal of the CR A series robot, which is connected to the robot by a wired connection. Its appearance is as follows.

_Figure 2.1 Appearance of the teach pendant_

* Touch screen: 10.1-inch capacitive touch screen.
* Emergency stop switch: used to stop the robot in an emergency. See Emergency stop device for details.
* Jog button: used to jog the robot. See Jog button description for details.
* Three-position switch: functions are configurable. See Three-position switch description for details.
* Aviation plug interface: used to connect the teach pendant to the robot controller via cable. The teach pendant will automatically power on after plugging in the aviation connector cable.
* Screen switch: short press to rest/light the screen when it is on.
* USB interface: 1 Type C (USB3.0) interface and 2 Type A (USB2.0) interfaces, which can be used to connect peripherals such as computer, USB flash drive, keyboard and mouse.
* Lanyard mounting hole: used to install the lanyard.

![Figure 2.1 Appearance of the teach pendant](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FG1BeAZRmHwlm511dqCXJ%2Ftp10-p007-img01.jpg?alt=media)

### 2.2 Accessories description

For specifications and quantities of accessories, please refer to the shipping list.

* Aviation connector cable: used to connect the teach pendant to the robot controller.
* Teach pendant (TP) stand: can be fixed to the robot controller or placed on the table, with mounting screws.
* Lanyard: can be installed on the top of the teach pendant for hanging the teach pendant.
* Polishing cloth: used to wipe the screen.

## 3. Mechanical Specifications

All dimensions in this chapter are in mm.

### 3.1 Dimensions of teach pendant

_Figure 3.1 Dimensions of the teach pendant_

![Figure 3.1 Dimensions of the teach pendant](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRps7oS9Nv8kGQ8fohL5w%2Ftp10-p009-img01.png?alt=media)

### 3.2 Dimensions of TP stand

_Figure 3.2 Dimensions of the TP stand_

![Figure 3.2 Dimensions of the TP stand](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJCMarYz2tJKSvlfAxTL3%2Ftp10-p010-img01.png?alt=media)

## 4. Installation and Use

### 4.1 Unpacking

When opening the box, please check the attached shipping list to ensure that all contents are included. If anything is missing, please contact your supplier.

**NOTICE**

Dobot is not responsible for any damage incurred during transportation.

### 4.2 Installation stand (optional)

Depending on the site requirements, you can choose to fix the teach pendant stand to the robot controller, or stand it on the table after assembling. Fix the stand to the controller:

1. Remove the two adjacent screws at the top of the side panel of the controller with M3

Phillips screwdriver (remove according to the position where you want to install the stand, it is recommended to remove the screws on the side without the heat sink).

2. Use two M3\*6 hexagon socket screws that supplied with the teach pendant to fix the stand

to the side of the controller, as shown in the figure below.

_Figure 4.1 Fix the stand to the controller_

Place the stand on the table: Use three M3\*6 hexagon socket screws that supplied with the teach pendant to assemble the standing legs of the stand, as shown in the figure below.

![Figure 4.1 Fix the stand to the controller](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjWq2KGNVpExyCIexg2N2%2Ftp10-p011-img01.png?alt=media)

_Figure 4.2 Assemble the stand_

### 4.3 Connecting to Robot

Use the aviation connector cable provided with the teach pendant to connect the teach pendant 1. to the controller. The teach pendant will automatically power on and display the DobotStudio Pro software interface.

_Figure 4.3 Connect the aviation connector cable_

Click Connect on the top left of the interface. If Automatic connection is switched on via 2. Settings > Teach pendant settings > Basic settings, the teach pendant will automatically connect to the robot after it is powered on.

_Figure 4.4 Automatic connection_

### 4.4 Three-position switch description

The three-position switch has three positions (released/middle position/fully pressed). It is recommended to operate it in the posture shown below.

![Figure 4.2 Assemble the stand](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F83KsdrktDPyY0QyBaiMr%2Ftp10-p012-img01.png?alt=media)

![Figure 4.3 Connect the aviation connector cable](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUs74qChyLCHkvZkkuFM1%2Ftp10-p012-img02.jpg?alt=media)

![Figure 4.4 Automatic connection](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTKHLGzZR3a3ytJTZYcUi%2Ftp10-p012-img03.jpg?alt=media)

_Figure 4.5 Use of the three-position switch_

You can modify the function of the three-position switch on the Settings > Teach pendant settings > Three position switch page. It is Disable by default and can be configured as Drag mode or Enable.

_Figure 4.6 Three-position switch configuration_

* Disable: Three-position switch has no effect.
* Drag mode: Use the three-position switch to control the robot to enter or exit the drag mode.
* Enable: Use the three-position switch to control the robot's enabling status in manual mode.

#### 4.4.1 Drag switch

When the three-position switch is set to Drag mode, the operation method is as follows.

* Press the three-position switch to the middle position, and the robot enters the drag mode.
* Release or fully press the three-position switch, and the robot exits the drag mode.

In addition to the three-position switch, the robot end button and remote IO/Modbus can also trigger the drag mode. These triggering methods are effective at the same time.

#### 4.4.2 Enable switch

If you want to use the Enable switch, you need to switch on the Operation mode switch via Settings > Operation mode first.

_Figure 4.7 Switch on the operation mode switch_

![Figure 4.5 Use of the three-position switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgKJ4d1yNbh022Mve6jys%2Ftp10-p013-img01.png?alt=media)

![Figure 4.6 Three-position switch configuration](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZZlGoYge668xTaP2WneE%2Ftp10-p013-img02.jpg?alt=media)

![Figure 4.7 Switch on the operation mode switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F31mjbdvF5cB6Dh3YX3l0%2Ftp10-p013-img03.jpg?alt=media)

Then go to the Three-position switch page and configure the function of the three-position switch to Enable. After successful setting, when the robot is in Manual mode, the enable switch on the software interface will be disabled (only the status is displayed, the enable status cannot be switched by the software), and the robot enable status can only be controlled by the three-position switch.

* Press the three-position switch to the middle position, and enable the robot.
* Release or fully press the three-position switch, and disable the robot.

In Manual mode, the three-position switch must be kept in the middle position while the robot is running. Releasing or fully pressing the three-position switch will cause the robot to stop running and be disabled. As shown below.

* Jog/Step/RunTo/Trajectory playback: stop running and disable the robot.
* Hand guiding: exit the drag mode and disable the robot.
* Trajectory recording: stop running, save the trajectory and disable the robot.
* Run project: stop running the project and disable the robot.

In Automatic mode, the three-position switch is disabled, and the robot operates in the same manner as when the three-position switch is disabled.

### 4.5 Jog button description

The jog button on the right of the teach pendant screen can be used to jog the robot. Its function is the same as the jog button on the software jog panel. The corresponding relationship is shown in the figure below.

_Figure 4.8 Correspondence between jog buttons_

### 4.6 Vibration and buzzing

The vibration and buzzing functions of the teach pendant can be switched on or off in Basic settings.

_Figure 4.9 Feedback switch_

![Figure 4.8 Correspondence between jog buttons](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fus0FlMMAdQg3Vd3ebRtc%2Ftp10-p014-img01.jpg?alt=media)

![Figure 4.9 Feedback switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSbhK5oXPusZ1J7FmJmCr%2Ftp10-p014-img02.jpg?alt=media)

When the Vibration switch is ON, the teach pendant will vibrate in the following scenarios:

* In Manual mode, if the three-position switch is configured as Enable, but the robot is in the Disable status while jogging, it will vibrate once.
* Vibrate once when the robot reaches the target point through the RunTo function.
* When the joint limit is triggered during jogging, or once the warnings and alarms related to enable, brake, and safety are triggered while the robot is running, it will vibrate continuously for one second. When the Buzzer feedback is ON, the teach pendant will buzz once to prompt when the robot triggers an alarm.

### 4.7 Adjust screen brightness

The screen brightness of the teach pendant can be set in the Basic settings.

_Figure 4.10 Adjust the screen brightness_

You can drag the slider to adjust the screen brightness.

### 4.8 Export crash log

If the software crashes, you can export the crash log in Basic settings page to assist Dobot technical support engineer in troubleshooting. Click Crash log, and the Crash log management window will pop up. After checking the log, you can perform the following operations.

* If a USB flash drive is plugged into the teach pendant, you can Export it to the USB flash drive.

**NOTE**

If the storage device connected to the USB interface contains multiple partitions, the log will be exported to the first partition. The first partition of some storage devices (e.g., a USB flash drive used as a boot disk) is a hidden partition, which prevents the exported logs from being viewed directly in Windows.

* Delete the crash log as needed.

![Figure 4.10 Adjust the screen brightness](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLeorTVL2LB2LuQCdf9UY%2Ftp10-p015-img02.jpg?alt=media)

### 4.9 Software update

To update the software version of the teach pendant, follow the steps below.

1. Get the latest software installation package for the teach pendant (the apk file whose name

starts with DobotStudioPro).

2. Put the installation package into your own USB flash drive.
3. Insert the USB flash drive into the teach pendant.
4. Click Check firmware in Basic settings page.
5. If an update package is detected, a pop-up window will display the version of the update

package (if more than one update package is detected, you need to select one in the pop- up window), and click Update.

6. Wait for the software to finish updating.

**NOTE**

* For how to use the other functions of DobotStudio Pro, please refer to the help document in the software. This document only introduces the functions of the teach pendant.
* When using the onscreen keyboard for input in DobotStudio Pro, please only use standard text input functions. Do not use other functions such as emoji, emoticons, and special symbols.

## 5. Maintenance

Maintenance and repairing must be performed in compliance with all safety instructions in this document. The purpose of maintenance and repairing is to ensure that the system is kept operational, or to return the system to an operational state in the event of a fault. Repairing includes troubleshooting in addition to the actual repair itself. Repairing must be performed by an authorized system integrator or Dobot staff. Before returning the teach pendant to Dobot, you need to:

* Remove all parts that do not belong to Dobot.
* Make a backup copy of the files. Dobot will not be responsible for the loss of programs, data or files stored in robot.

### 5.1 Safety instructions

The following safety procedures and warnings must be observed when maintaining the teach pendant.

**NOTICE**

* Replace faulty components using new components with the same model or equivalent components approved by Dobot.
* Reactivate all deactivated safety measures immediately after the repairing is completed.
* Record all repairs and save them in the technical document associated with the robot system.
* Observe ESD regulations during the disassembly of the parts of the teach pendant.
* Prevent water and dust from entering the teach pendant.

### 5.2 Maintenance

To maintain high performance for the robot over a long period of time,, maintenance checks must be carried out. The personnel in charge of the maintenance must prepare a maintenance plan and carry out the maintenance. The maintenance items are shown below.

_Table 5.1 Maintenance item_

Period Maintenance item Maintenance essential Daily 6 months Use water, 10% ethanol, etc. to wipe any dust, √ Surface cleaning dirt, oil, etc. visible on the teach pendant. Touch screen Check whether the display of the touch screen is √ checking normal and the touch is sensitive. √ Button checking Check whether the buttons work properly. √ USB interface Check whether the USB interface works checking properly by exporting logs or projects. Check whether the connection ends of the √ Cable checking aviation connector cable are secure and whether the skin is worn out.

## 6. Warranty

### 6.1 Product warranty

Without prejudice to any claim agreement that the user (customer) may reach with the distributor or retailer, the manufacturer shall guarantee the quality of the products to the customer in accordance with the terms and conditions below: If defects caused by manufacturing and/or improper material occur in a new device and its components within 12 months (15 months at most if the shipping time is included) after the device is put into use, Dobot shall provide the necessary spare part, and the user (customer) shall offer personnel to replace the spare part, using another part that represents the latest technology level to replace or repair the related part. If the device defects are caused by improper handling and/or failure to follow the relevant information set out in the User Guide, the warranty is invalid. This warranty does not apply to or extend to maintenance (e.g. installation, configuration, software download) performed by the authorized distributer or customer. The user (customer) must provide the purchase receipt and the purchase date as valid evidence for the warranty. Claims under this warranty must be made within two months of the apparent failure to perform the product warranty. The ownership of the device or components that are replaced or returned to Dobot shall remain with Dobot. Any other claims arising from or related to the device are not covered by this warranty. Any items in this product warranty do not intend to limit or exclude the legal rights of the customer or to limit or exclude the liability of the manufacturer for the personnel casualty resulting from its negligence. The duration of this product warranty shall not be extended due to the services provided under the product warranty terms. Under the principle of not violating the warranty, Dobot reserves the right to charge customers for the replacement or maintenance. The foregoing does not imply a change in the burden of proof to the detriment of the client. If there are defects on the device, Dobot shall not be liable for any damage or loss arising therefrom, including but not limited to loss of production or damage to other production device.

### 6.2 Disclaimer

Dobot is committed to improve the reliability and performance of its products, and as such reserves the right to upgrade products without prior notice. Dobot strives to ensure the contents of the User Guide are precise and reliable, but takes no responsibility for any errors or missing information.

## Appendix Technical specifications

Product model DT-TP10-3PE-N Size Exclude E-Stop 29&#x34;_&#x31;8&#x34;_&#x34;3mm (Lengt&#x68;_&#x57;idth_ Height) Include E-Stop 29&#x34;_&#x31;8&#x34;_&#x35;9mm Weight 1.09 kg IP rating IP54 Connection mode for teach pendant Wired connection and controller Whole Cable length from teach pendant to device 5 m controller parameter Working temperature 0℃ – 50℃ Relative humidity for working Maximum 90% (no condensation) environment Transportation and storage -20℃ – 55℃ temperature Relative humidity for transportation Maximum 95% (no condensation) and storage Material PC+ABS Size 10.1 inch Screen Resolution 192&#x30;_&#x31;200@60Hz Touch screen Multi-touch capacitive touch screen Operating Android 12 system ROM 32 GB Memory RAM 4 GB Type&#x41;_&#x32;: USB2.0 USB Communic Type&#x43;_&#x31; ation One 100M Ethernet interface for interface Aviation plug interface communication between the teach pendant and the controller Physical Emergency stop switc&#x68;_&#x31;; Three-position switc&#x68;_&#x31;; buttons ON/OFF butto&#x6E;_&#x31;; Jog button\*12 The size data are from Dobot. Actual size may vary depending on configuration, manufacturing ① process, and measurement method, the actual product shall prevail. Specifications are subject to change without prior notice for product improvement. ②
