---
description: >-
  Official V2.5.0 software guide for the DOBOT Palletizing Process Package used
  with compatible CR20A and CR30H workstations.
---

# DOBOT Palletizing Process Package User Guide V2.5.0

## DOBOT CR20A V2 Lifting and Columnar Palletizing Workstation

{% embed url="https://openelab.io/products/dobot-cr20a-palletizing-workstation-v2" %}

## DOBOT CRA One-Stop Columnar Palletizing Workstation for CR20A

{% embed url="https://openelab.io/products/dobot-cr20a-columnar-palletizing-workstation" %}

## DOBOT CRA One-Stop Lifting Palletizing Workstation for CR20A

{% embed url="https://openelab.io/products/dobot-cr20a-lifting-palletizing-workstation" %}

## DOBOT CR30H Columnar Palletizing Robot Workstation

{% embed url="https://openelab.io/products/dobot-cr30h-columnar-palletizing-workstation" %}

[Official process-package manual PDF, V2.5.0](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260923/DOBOT%20Palletizing%20Process%20Package%20User%20Guide_V2.5.0_20260922_en.pdf)

**Version boundary:** This guide covers the V2.5.0 palletizing software process package. For workstation hardware installation and safety, use the separate [CRA/CRH Series Palletizing Workstation User Guide V2.4.2](https://wiki.openelab.io/dobot/dobot-cra-crh-series-palletizing-workstation-user-guide). The official V2.5.0 guide warns that an installed plugin V2.4.2 or earlier must be uninstalled and workstation settings reconfigured before upgrading. Check controller and DobotStudio Pro compatibility before starting that change.

## Contents

* Preface
* 1\. Preparation
* 2\. Software Configuration
* 3\. I/O Virtual Signal Debugging
* 4\. Set Workstation
* 5\. Product Management
* 6\. New Palletizing Project (With Interlayer)
* 7\. New Palletizing Project (Without Interlayer)
* 8\. Run and Monitor the Project
* 9\. Troubleshooting
* Appendix A Register Address Definitions and Descriptions
* Appendix B Reference Manuals

## Copyright and Disclaimer

### Copyright © SHENZHEN DOBOT CORP LTD 2026. All rights reserved.

No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as "DOBOT").

### Disclaimer

To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided **AS IS** , which may have flaws, errors or faults. DOBOT makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will DOBOT be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents.

Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot arm is used on the premise of fully understanding the robot arm and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process DOBOT shall not be considered as a guarantee regarding all security information contained in this document.

The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot arm.

SHENZHEN DOBOT CORP LTD Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China

Website: www.dobot-robots.com

## Preface

This document describes the download and installation of the DOBOT Palletizing Process Package plugin, parameter configuration of the Palletizing Workstation, configuration and operation of palletizing projects, and system debugging, helping users understand and use the palletizing workstation.

### Applicable models

* DOBOT CR25V Columnar / Lifting Palletizing Workstation
* DOBOT CR20A Columnar / Lifting Palletizing Workstation
* DOBOT CR30H Columnar / Lifting Palletizing Workstation

### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

### Compatible versions

| Product or model                                             | Required version            | Source or note                                             |
| ------------------------------------------------------------ | --------------------------- | ---------------------------------------------------------- |
| Palletizing Process Package                                  | `Palletizing_v2-5-0-stable` | DOBOT Palletizing Process Package.                         |
| Robot Maintenance Tool                                       | 2.4.0-stable or later       | DOBOT Robot Maintenance Tool.                              |
| CR25V / CR20A: DobotStudio Pro, PC / Android / Teach Pendant | 4.6.7.0-stable or later     | Corresponding V4.6.X package.                              |
| CR25V / CR20A: controller                                    | 4.6.7.0-pal-stable          | Factory-installed or upgraded with Robot Maintenance Tool. |
| CR30H: DobotStudio Pro, PC / Android / Teach Pendant         | 4.7.0.0-stable or later     | Corresponding V4.7.X package.                              |
| CR30H: controller                                            | 4.7.3.1-stable              | Factory-installed or upgraded with Robot Maintenance Tool. |

### Related documents

| Official document                                    | Use                                                           |
| ---------------------------------------------------- | ------------------------------------------------------------- |
| DOBOT Palletizing Workstation Safety Function Manual | SICK safety LiDAR configuration.                              |
| DOBOT CRV Series Hardware User Guide                 | CRV-series robot functions, specifications, and installation. |
| DOBOT CRA Series Hardware User Guide                 | CRA-series robot functions, specifications, and installation. |
| DOBOT CR30H Series Hardware User Guide               | CR30H robot functions, specifications, and installation.      |
| DOBOT Robot Maintenance Tool User Guide              | Firmware, controller-file backup, and recovery.               |

### Revision history

| Date       | Version | Change                                                                                                                                          |
| ---------- | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 2026-09-22 | V2.5.0  | Interlayer safety zone, quantity alerts, automatic transition point, production task/data, page optimizations, and plugin V2.5.0 compatibility. |
| 2026-04-24 | V2.4.2  | Plugin V2.4.2 compatibility.                                                                                                                    |
| 2025-12-17 | V2.4.1  | Plugin V2.4.1 compatibility.                                                                                                                    |
| 2025-10-31 | V2.4.0  | Picking-point user coordinate system and plugin V2.4.0 compatibility.                                                                           |
| 2025-01-24 | V2.3.0  | Plugin V2.3.0 basis.                                                                                                                            |

### Symbol conventions

The symbols that may be found in this document are defined as follows.

| **Symbol**  | **Description**                                                                                                                                             |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DANGER**  | <p>Indicates a high potential hazard that, if not avoided, could result in<br>death or serious injury.</p>                                                  |
| **WARNING** | <p>Indicates a hazard with a medium level or low level of risk which, if<br>not avoided, could result in minor or moderate injury, robot arm<br>damage.</p> |
| **NOTICE**  | <p>Indicates a potential risk that, if ignored, could result in robot arm<br>damage, data loss, or unpredictable result.</p>                                |
| **NOTE**    | <p>Provides additional information to emphasize or supplement<br>important points in the main text.</p>                                                     |

## 1. Preparation

### 1.1 Access training videos

Click the link below to access training videos to help you better understand and use the palletizing workstation:

[Official palletizing solution unboxing video](https://dobot-cloud-1256299428.cos.accelerate.myqcloud.com/dobot/Palletizing_Palletizing%20Solution_Solution%20Unboxing%20Video_2024-02-22_en.mp4)

### 1.2 Download the Palletizing Process Package plugin

Click the link below to get the latest version of the palletizing process package plugin: DOBOT Palletizing Solution\_Process Package.

### 1.3 Install and Upgrade

**NOTE** If a version 2.4.2 or earlier of the Palletizing plugin has been previously installed and configured, you must first uninstall the old version. Then, import and install version 2.5.0 of the plugin. After installation, the Palletizing Workstation Settings must be reconfigured.

1. After connecting the robot with DobotStudio Pro, open the Dobot+ page and import the Palletizing plugin.

Figure 1.1 Import the plugin

2. Click "Install" next to the Palletizing plugin to start the installation.

Figure 1.2 Install the plugin

The version installed at this point is the basic version. To upgrade to the Pro version, please follow the steps below:

1. Open DobotStudio Pro and enter the "Application" page, select "Palletizing" to access the Palletizing plugin.

![Official manual image, source page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzZ4WjUlhdy1cbP5v9xzB%2Fpallet-process-p009-img02.jpg?alt=media)

Figure 1.3 Access palletizing

2. Click "Upgrade to Pro version" or click any icon on the interface to enter the upgrade page.

Figure 1.4 Upgrade to Pro Version

3. The differences between the basic and professional versions are displayed on the interface. Click "Upgrade Now" to proceed to the authorization page.

Figure 1.5 Upgrade

4. On the authorization page, copy the device serial number and visit dobotplus.dobot-robots.com. Enter the device serial number and activation code (contact DOBOT technical support to obtain) on the webpage, then click "Get registration code".

![Official manual image, source page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH6txKYFha80J1lE2QAVA%2Fpallet-process-p010-img02.jpg?alt=media)

![Official manual image, source page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYrmT3eSNcbj6u33ScTeB%2Fpallet-process-p010-img04.png?alt=media)

![Official manual image, source page 10](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqiSqAXKEQV62bG4JB4t7%2Fpallet-process-p010-img05.png?alt=media)

Figure 1.6 Copy the device serial No.

Figure 1.7 Get registration code

5. Copy the generated registration code or save the registration code as a file.

![Official manual image, source page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFLxs8tPPw5lR7cCW9abn%2Fpallet-process-p011-img02.png?alt=media)

![Official manual image, source page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmDwbS2TuJfmmt2bHnLQv%2Fpallet-process-p011-img03.png?alt=media)

Figure 1.8 Save registration code

6. Return to the authorization page, paste the registration code or import the file, then click "Upgrade Now". Wait for the authorization and plugin installation to complete successfully. A popup window will confirm the successful installation.

Figure 1.9 Upgrade authorization<br>

Figure 1.10 Installation successful

![Official manual image, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpLRhdhj0V37cYdv5ecTg%2Fpallet-process-p012-img02.png?alt=media)

![Official manual image, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuGd8iot23dbyMHmE8CP9%2Fpallet-process-p012-img03.jpg?alt=media)

![Official manual image, source page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjR6Mq81LoGk1axtK9Yab%2Fpallet-process-p012-img04.png?alt=media)

## 2. Software Configuration

This chapter takes the PC control software (DobotStudio Pro) as an example to explain the operation method, which is basically the same as that of the App control software. For basic operations of DobotStudio Pro (such as connecting to the robot, enabling and jogging), please refer to its help document.

The figure below shows the chapters of the document that correspond to the common operations in using the palletizing workstation.

Figure 2.1 DobotStudio Pro help document

### 2.1 Compatibility

If a version 2.4.2 or earlier of the Palletizing plugin has been previously installed and configured, you must first uninstall the old version. Then, import and install version 2.5.0 of the plugin. After installation, the "Palletizing workstation settings" must be reconfigured.

![Official manual image, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8cHTErqJ1GcxKQlbTHOq%2Fpallet-process-p013-img02.png?alt=media)

### 2.2 Permissions

The palletizing process package implements access control based on the current role logged into DobotStudio Pro, preventing unauthorized personnel from modifying project settings. Permissions for different roles can be viewed in the palletizing process package under "Workstation settings > Permissions".

Figure 2.2 Current login role

![Official manual image, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq8nsG0WswRanPzKw2szJ%2Fpallet-process-p014-img02.jpg?alt=media)

## 3. I/O Virtual Signal Debugging

In scenarios where a physical workstation is not equipped: after completing the I/O signal settings, you can perform debugging either by short-circuiting the wiring or by setting the signals as virtual signals. The robot arm will only execute the predefined motion trajectory and will not physically pick up products. To perform actual picking, the corresponding wiring must be completed.

**Safety Note:** During debugging and operation, ensure that all personnel remain outside the robot arm's working range to ensure safety.

### 3.1 I/O definitions

#### 3.1.1 DI definitions

| **Pin**               | **In (DI)**           | **Description**                                    | **Correspondence** |
| --------------------- | --------------------- | -------------------------------------------------- | ------------------ |
| DI1                   | DI1                   | <p>Conveyor 1 - Incoming material<br>detection</p> |                    |
| DI2                   | DI2                   | Left pallet - Position detection 1                 |                    |
| DI3                   | DI3                   | Left pallet - Position detection 2                 | Sensor In 1 – 5    |
| DI4                   | DI4                   | Right pallet - Position detection 1                |                    |
| DI5                   | DI5                   | Right pallet - Position detection 2                |                    |
| DI6                   | DI6                   | <p>Conveyor 2 - Incoming material<br>detection</p> | --                 |
| DI7                   | DI7                   | Enable button                                      | --                 |
| DI8                   | DI8                   | Reserved                                           | --                 |
| DI9                   | DI9                   | Left\_Pallet confirmation                          |                    |
| DI10                  | DI10                  | Right\_Pallet confirmation                         |                    |
| DI11                  | DI11                  | Start button                                       | User signal        |
| DI12                  | DI12                  | Stop button                                        |                    |
| DI13                  | DI13                  | Reset button                                       |                    |
| DI14                  | DI14                  | Reserved                                           | --                 |
| DI15                  | DI15                  | Reserved                                           | --                 |
| DI16                  | DI16                  | Reserved                                           | --                 |
| <p>DI17 –<br>DI24</p> | <p>DI17 –<br>DI24</p> | --                                                 | --                 |

#### 3.1.2 DO definitions

| **Pin**               | **Out (DO)**          | **Description**                  | **Correspondence** |
| --------------------- | --------------------- | -------------------------------- | ------------------ |
| DO1                   | DO1                   | Left\_Three color light\_Yellow  |                    |
| DO2                   | DO2                   | Left\_Three color light\_Green   |                    |
| DO3                   | DO3                   | Left\_Three color light\_Red     |                    |
| DO4                   | DO4                   | Right\_Three color light\_Yellow | Light out 1–6      |
| DO5                   | DO5                   | Right\_Three color light\_Green  |                    |
| DO6                   | DO6                   | Right\_Three color light\_Red    |                    |
| DO7                   | DO7                   | Enable button light              |                    |
| DO8                   | DO8                   | Reserved                         | --                 |
| DO9                   | DO9                   | Reserved                         | --                 |
| DO10                  | DO10                  | Reserved                         |                    |
| DO11                  | DO11                  | Start button indicator           | U il               |
| DO12                  | DO12                  | Reset button indicator           | ser sgna           |
| DO13                  | DO13                  | Stop button indicator            |                    |
| DO14                  | DO14                  | Vacuum suction solenoid valve 1  | --                 |
| DO15                  | DO15                  | Reserved                         | --                 |
| DO16                  | DO16                  | Vacuum release solenoid valve 1  | --                 |
| <p>DO17 –<br>DO24</p> | <p>DO17 –<br>DO24</p> | --                               | --                 |

**NOTICE**

* Dual signals control two solenoid valves: DO14 & DO16, and DO15 & DO17.
* If a suction cup with a solenoid valve is connected to other DO signals or ToolIO, DO14 or DO15 must be set to Normally Open (NO).

### 3.2 I/O wiring instructions

When using with the palletizing process package, refer to the I/O definitions for wiring. During actual use, wire according to the I/O signals in the workstation configuration.

#### 3.2.1 DI wiring

The DI interface must be connected to the COM interface, which can switch signal types (PNP or NPN). COM1 is used for DI1 – DI12. COM2 is used for DI13 – DI24.

* **DI connected to a simple switch:**

The wiring method is shown in the figure below (left: PNP wiring; right: NPN wiring). Select the appropriate wiring method based on on-site requirements.

Figure 3.1 DI simple switch wiring

![Official manual image, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXqtzDtyOog3stfOLRuAW%2Fpallet-process-p017-img02.png?alt=media)

* **DI shorted wiring:**

The wiring method is shown in the figure below (left: PNP wiring; right: NPN wiring). Select the appropriate wiring method based on on-site requirements.

Figure 3.2 DI shorted wiring

* **DI connected to an external PNP three-wire sensor:**

The wiring method is shown in the figure below. If the sensor is powered by the controller, short-circuit the corresponding COM port to **I/O 0V** (left figure below). If the sensor is powered by an external supply, connect the COM port to **0V of the external power supply** (right figure below).

Figure 3.3 DI connected to PNP input

![Official manual image, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeFBqOl0Qtgf4joMMVnSW%2Fpallet-process-p018-img02.png?alt=media)

![Official manual image, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIZ48fQQTcenPP8eTGBjG%2Fpallet-process-p018-img03.png?alt=media)

* **DI connected to an external NPN DO:**

The wiring method is shown in the figure below. If the external DO is powered by the controller, short-circuit the corresponding COM port to **I/O 24V** (left figure below). If the external DO is powered by an external supply, connect the COM port to **24V of the external power supply** (right figure below).

Figure 3.4 DI connected to NPN input

![Official manual image, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F72SFVM3mRxD4ho0Zs7ln%2Fpallet-process-p019-img02.png?alt=media)

#### 3.2.2 DO wiring

DO is set to PNP by default but can be switched to NPN via the software (DobotStudio Pro). If the software setting and the actual wiring configuration do not match (e.g., software set to PNP while wiring is NPN), the load will not function properly.

* **DO is PNP type, connected to an external load:**

The wiring method is shown in the figure below.

Figure 3.5 PNP-type DO connected to an external load

* **DO is NPN type, connected to an external load:**

The wiring method is shown in the figure below.

Figure 3.6 NPN-type DO connected to an external load

![Official manual image, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5sG6PTLyXvVTRDdAqajO%2Fpallet-process-p020-img02.png?alt=media)

![Official manual image, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqyCLnyp1SPhKUcmTikK1%2Fpallet-process-p020-img03.png?alt=media)

### 3.3 Set virtual I/O

1. Go to "Monitor > Controller DI/DO > Settings".

Figure 3.7 Controller DI/DO page

2. Check the "Switch to virtual DI" box for the corresponding DI, then click "“Save".

Figure 3.8 Switch to virtual DI page

![Official manual image, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWOJe7mJMeQntvvsXVe4Z%2Fpallet-process-p021-img02.png?alt=media)

![Official manual image, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeiDH5vg2qj5c400GK085%2Fpallet-process-p021-img03.png?alt=media)

Figure 3.9 Virtual DI status page

![Official manual image, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FN8xXkdIqasbHPTKHkw0y%2Fpallet-process-p022-img02.png?alt=media)

## 4. Set Workstation

Open DobotStudio Pro and enter the "Application" page, select "Palletizing" to access the Palletizing plugin.

Figure 4.1 Access palletizing

If you're using the palletizing process package for the first time, or if you've recently replaced or adjusted the workstation hardware, you'll need to configure the workstation settings. Click " Workstation settings" at the top right corner of the palletizing process package homepage to open the settings page.

Figure 4.2 Workstation settings

### 4.1 Set workstation basic parameters

Figure 4.3 Basic settings

![Official manual image, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7vFLZ4xtFkdaSg5WtDLy%2Fpallet-process-p023-img04.png?alt=media)

![Official manual image, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOya1QPGqSPRTZEYXThxY%2Fpallet-process-p023-img05.jpg?alt=media)

| **No.** | **Module**                                  | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ①       | Unit                                        | <p>Set the length and weight units used for suction cup, pallet,<br>interlayer, and box parameters. Both metric units (mm &#x26;<br>kg) and imperial units (in &#x26; lb) are supported. When you<br>change the units, all related parameters in the palletizing<br>project will automatically be converted and updated.</p>                                                                                                                                                                                                                                              |
| ②       | <p>Workstation<br>safe home<br>position</p> | <p>When the palletizing project starts running (or restarts after<br>being stopped), and after completing each pallet, the robot<br>arm will return to the safe home position. If the posture at<br>this position does not cause any interference, it is<br>advisable not to alter this point, as changes could result in<br>abnormal movements of the lifting column or robot arm.</p>                                                                                                                                                                                   |
| ③       | <p>Workstation<br>hardware</p>              | <p>Select column or lifting column, suction cup type and size.<br>See"Workstation hardware" for details.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ④       | <p>Enable safety<br>protection</p>          | <p><br>**Palletizing height limit:**When checked, allows<br>setting the maximum stacking height for the current<br>workstation. Minimum input limit: Machine height +<br>Robot safe pose height + 50mm.<br><br>**Box collision detection:**When checked, enables the<br>box collision detection function. If a collision or<br>excessive offset is detected while editing a stacking<br>pattern, a pop-up warning will appear (virtual<br>simulation is recommended). Click "Cancel" to<br>continue editing, or click "Save" to force save the<br>stacking pattern.</p> |
| ⑤       | I/O signals                                 | <p>Pre-configured by default. No modification is required<br>unless the hardware configuration has been changed. For<br>details on each I/O signal, see"I/O signals".</p>                                                                                                                                                                                                                                                                                                                                                                                                 |

#### 4.1.1 Workstation hardware

Figure 4.4 Set workstation hardware

![Official manual image, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlbvMJfJ265kP4OU6mIzV%2Fpallet-process-p024-img02.png?alt=media)

####  **Lifting column:**

Select the model of column or lifting column based on the actual configuration of your palletizing workstation. For the column type, the available models are "DT-PR-C-DV01, DT-PR-C-HSM-OV, or DT-PR-C-HSM-OV-20/30-02 (new)". For the lifting column type, the available models are "DT-PR-L-GM-DV, DT-PR-L-TX-HSM-OV, DT-PR-LTX-HSM-OV-20-02, or LC30100-00-LINAK (new)".

####  **Suction cup type:**

Select the type of suction cup according to the actual one equipped with your workstation. The default suction cup for the palletizing workstation is single-channel suction cup, which supports only single pick-and-place, meaning it can pick up and place one box at a time. If a higher cycle rate is required, please contact DOBOT technical support for evaluation and customization of a multi-channel suction cup. Multi-channel suction cups support single pick-and-place, dual pick-and-place (picking and placing two boxes at a time), dual-pick single-place (picking two boxes at a time and placing them one by one), triple pick-and-place (picking and placing three boxes at a time), and quadruple pick-and-place (picking and placing four boxes at a time).

* The principle and operation of multi-channel suction cups are the same. Take dual pick-and-place as an example. In dual pick-and-place mode, two boxes must be treated as a single unit when determining the picking point and tool coordinate system, as shown in the figure below.

Figure 4.5 Dual pick-and-place

* When using a dual-channel suction cup for single pick-and-place, only one side of the channel is used to pick up a box, as shown in the figure below. There is no need to separately configure the picking point and tool coordinate system for this situation. The system will automatically calculate these based on the box sizes and other parameters.

Figure 4.6 Single-pick with Dual-channel suction cup

![Official manual image, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeR38j1zalIva2M4kyWNx%2Fpallet-process-p025-img02.png?alt=media)

![Official manual image, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOPDjQQrjZWGUPcLukg8X%2Fpallet-process-p025-img03.png?alt=media)

####  **Preset suction cup:**

Check "Preset suction cup" to select a built-in suction cup from the system. Once a preset suction cup model is selected, the suction cup type and size will be grayed out and cannot be edited.

Figure 4.7 Preset suction cup

####  **Suction cup size:**

Set the size of suction cup according to the actual one equipped with your workstation. The height refers to the distance from the robot arm's end flange to the top surface of the box after it's picked up (approximately half the height of the suction nozzle). For details, refer to the diagram on the interface.

#### 4.1.2 I/O signals

#### Suction cup signal

Figure 4.8 Suction cup signal

* **Suction cup 1/2/3/4 vacuum signal:**

Signal to control the vacuum function of the suction cup for picking up boxes. For single-channel suction cup, you only need to configure the signal for Suction Cup 1. For multi-channel suction cup, you need to configure multiple signals to control each channel independently. Select the signal according to the actual situation. The subsequent suction cup related signals follow the same principle, no more details in this document.

DO\_14 and DO\_15 by default. If the wiring has been modified, please select according to the actual wiring.

####  **Suction cup 1/2/3/4 drop detection signal:**

The signal from the drop detection sensor of the suction cup, used to detect whether the suction cup has successfully picked up a box and for drop detection during

![Official manual image, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNa7Eip31OPCcixSslN2Y%2Fpallet-process-p026-img02.png?alt=media)

![Official manual image, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS8x0glCW9euxVGb5pVQx%2Fpallet-process-p026-img03.png?alt=media)

palletizing.

This can be configured after checking "Drop detection signal". If this function is not required, leave it unchecked.

DI\_14 and DI\_15 by default. If your suction cup supports vacuum release detection, set this signal to the corresponding DI for that function.

* **Suction cup 1/2/3/4 vacuum release signal:**

Signal to control the vacuum release function of the suction cup for placing boxes.

This can be configured after checking "Vacuum release signal". If this function is not required, leave it unchecked.

DO\_16 and DO\_17 by default. If the wiring has been modified, please select according to the actual wiring.

#### Conveyor feeding signal

Figure 4.9 Conveyor feeding signal

It refers to the signal from the conveyor box in-position sensor. Each conveyor can be configured with up to two sensor signals. The palletizing workstation supports up to two conveyors. If only one conveyor is needed, you can skip the settings for Conveyor 2.

* For one placing method (e.g., all boxes are handled with single pick-and-place or multiple pick-and-place), only one sensor signal needs to be configured.
* For multiple placing methods, you need to configure multiple sensor signals to indicate that Box 1/2/3/4 are in position respectively.

DI\_1 when the cable is connected to the Conveyor Sensor 1 interface on the I/O panel of the palletizing workstation, and DI\_6 when connected to the Conveyor Sensor 2 interface. For details, refer to _DOBOT Palletizing Workstation Installation and Operation Instructions_ .

#### Pallet signal

Figure 4.10 Pallet signal

* **Left pallet detection signal:**

This signal detects whether the left pallet is properly installed. DI\_2 and DI\_3 by default. If the wiring has been modified, please select according to the actual wiring.

* **Right pallet detection signal:**

This signal detects whether the right pallet is properly installed. DI\_4 and DI\_5 by default. If the wiring has been modified, please select according to the actual wiring.

* **New pallet (left/right) confirmation signal:**

After checking "New pallet arrival confirmation signal", if the pallet has been replaced, the corresponding new pallet confirmation button must be pressed before the robot arm will start working.

**NOTICE** It is recommended to enable this function to prevent the robot from moving during pallet replacement.

* **Left/Right pallet data reset signal:**

After checking "Reset pallet data signal", if the left or right pallet data reset signal is detected as triggered, the pallet data on that side will be reset to its initial state:

* In palletizing scenarios: reset to layer 1, 0 boxes.
* In depalletizing scenarios: reset to full layers, full boxes.

**NOTICE** The "Left/Right pallet data reset signal" is responded to only when the script is in the stopped state.

![Official manual image, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAxm1bo5b2WDuIFGgoJaN%2Fpallet-process-p028-img02.png?alt=media)

#### Safety signal

Figure 4.11 Safety signal

* **Left/Right pallet LiDAR signal:**

Unchecked by default. When checked, the LiDAR safety protection function for the corresponding pallet side is enabled. For details on LiDAR installation and configuration, refer to the _DOBOT Palletizing Workstation Safety Function Manual_ .

#### Interlayer signal

Figure 4.12 Interlayer signal

####  **Interlayer pick-and-place signal:**

If a separate signal is needed to control the suction cup for handling interlayer (e.g., using a dedicated suction nozzle), enable and configure this signal. DO\_22 by default. If there is no interlayer during palletizing or a general suction cup signal is used, there is no need to check this signal.

####  **Interlayer detection signal:**

Once checked, the "Interlayer detection signal" can be set as either a "Distance sensor signal" (factory default: DI\_1) or a "Through-beam sensor signal" (factory default: DI\_2). Both can only be enabled or disabled at the same time.

After the "Interlayer detection signal" is enabled, signal changes can be monitored in the "I/O Monitor" panel on the home page. If the "Interlayer detection signal" is triggered during palletizing, a pop-up will indicate that the interlayers have run out.

Figure 4.13 Monitoring the interlayer detection signal

![Official manual image, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FE44JybLYtm2F7scPvitW%2Fpallet-process-p029-img03.png?alt=media)

![Official manual image, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0iIbSf4jZTxpDzZY8V3G%2Fpallet-process-p029-img04.png?alt=media)

If "Interlayer detection signal" is not enabled, you can still implement an alert for insufficient interlayers by setting the "Interlayer count" and the "Interlayer remaining quantity alert threshold". For details, refer to "Set interlayer".

#### Other signals

Figure 4.14 Other signals

####  **Buzzer signal:**

Once checked, after palletizing is completed, in addition to the indicator light prompt, the buzzer will also sound an alarm. The buzzer must be connected to the configured DO interface. DO\_24 by default.

####  **Wrapping signal:**

Once checked, triggering the wrapping signal will pause the robot's motion so that personnel can wrap the boxes with film. DO\_19 by default.

### 4.2 Set coordinate system

Figure 4.15 Coordinate system settings

| **No.** | **Module**                       | **Description**                                                                                                                                                                                                                                                                         |
| ------- | -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ①       | <p>Tool coordinate<br>system</p> | <p>A reference coordinate system based on the end-of-arm<br>suction cup. Its origin is the center of the suction cup’s<br>contact surface when it picks up a box, and its orientation<br>aligns with the flange tool coordinate system. See"Tool<br>coordinate system” for details.</p> |
| ②       | Pallet user                      | <p>Calibrated at the factory and recorded on the "Palletizing<br>Workstation Data Card" shipped with theproduct.</p>                                                                                                                                                                    |
| Issue V | 2.5.0(2026-09-22)                | <p>User Guide<br>Copyright © SHENZHEN DOBOT CORP LTD</p>                                                                                                                                                                                                                                |

![Official manual image, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnERuBJDMx0tUs2PAslAU%2Fpallet-process-p030-img03.jpg?alt=media)

| **No.** | **Module**                                     | **Description**                                                                                                                                                                                                                                                                                                                                                                    |
| ------- | ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|         | coordinate system                              | <p>However, after actual installation, deviations from the<br>factory test values may occur. It must be recalibrated with<br>reference to the"Pallet user coordinate system".</p>                                                                                                                                                                                                  |
| ③       | <p>Picking-point user<br>coordinate system</p> | <p>Disabled by default. When enabled, there is no need to<br>teach the picking point separately. For instructions on<br>creating a new picking point's user coordinate system,<br>refer to"Picking-point user coordinate system".</p>                                                                                                                                              |
| ④       | <p>Interlayer user<br>coordinate system</p>    | <p>For palletizing projects with interlayers, the interlayer<br>user coordinate system must be configured in advance.<br>"Single interlayer" is selected by default. If "Double<br>interlayer" is selected, left and right interlayer coordinate<br>systems must be created and selected separately. For<br>detailed settings, refer to"Interlayer user coordinate<br>system".</p> |

#### 4.2.1 Tool coordinate system

When using it for the first time, create a new tool coordinate system. Click "New" to create a new tool coordinate system either by "Numeric input" or by "Process teaching".

**NOTE** The controller supports a maximum of 50 tool coordinate systems. If all 50 coordinate systems are already in use, clicking "New" will display a prompt and you cannot continue setting a new one.

#### Create a tool coordinate system by "Numeric input"

1. Click "New > Numeric input". The following page appears.

Figure 4.16 Create tool coordinate system

2. Enter the tool coordinate system alias and the X, Y, Z, RX, RY, RZ coordinate values, then click "Save".

![Official manual image, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FF3iehdKnHMLf9uugV4Dc%2Fpallet-process-p031-img02.png?alt=media)

#### Create a tool coordinate system by "Process teaching"

1. Click "New > Process teaching". The following page appears. Make sure the end-ofarm suction cup is properly installed, then click "Next". The J6 joint of the robot arm is at 0° in the diagram.

Figure 4.17 Suction cup installation

**NOTICE** This setup process applies only to the standard suction cup installation method. If there is a rotation angle between the suction cup and the robot arm's end flange, you'll need to measure the angle as described below and configure it manually on the "Tool coordinate system settings" page in DobotStudio Pro:

First, adjust the robot so that RZ is 180°. Then, rotate the tool coordinate system so that the long side of the suction cup is parallel to the palletizing workstation. Record the rotation angle as the Rz value of the tool coordinate system.

2. After enabling the robot arm, use the jog function to align the center of the suction cup with the center of the box (for dual-channel suction cup, treat the two boxes being picked up as a single unit to calculate the center point). With the suction nozzle pressed against the box surface, click "Suction". Once the suction cup picks up the box, click "Next".

Figure 4.18 Pick up the box

3. Measure and enter the suction cup offset values.
   * ① Measure the vertical distance from the robot arm’s end flange to the top surface of the box, and enter this value as the "Z-axis offset" (If using an optional suction cup, this distance is about 110mm).

![Official manual image, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkihAyM9Tb9Ks5y7rc9LC%2Fpallet-process-p032-img02.jpg?alt=media)

![Official manual image, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzasL68PNchtF3V0qZFlS%2Fpallet-process-p032-img03.jpg?alt=media)

* ② Measure the offset from the center of the robot arm’s end flange to the center of the box and enter it (If there is no offset, enter 0. If using an optional suction cup, set the "X- offset" to 10mm and leave the "Y+ offset" at 0mm).

Figure 4.19 Set suction cup offset values

4. After entering these values, click "Next".
5. After successful calibration, you can release the suction cup on this page, then enter an alias (optional) and click "Finish". The system will save the tool coordinate system and return to the coordinate system settings page.

Figure 4.20 Save tool coordinate system

6. After returning to the coordinate system settings page, the system will automatically select the newly created tool coordinate system.

![Official manual image, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FftTmqaI5n5Z7TeqEM42W%2Fpallet-process-p033-img02.jpg?alt=media)

![Official manual image, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsYCfwGpphFyD06Vgwac8%2Fpallet-process-p033-img03.png?alt=media)

#### Select/Delete tool coordinate system

Click the "Select" button next to the tool coordinate system name to select or delete a previously added tool coordinate system. (Clicking the icon will display a second confirmation pop-up. Once deleted, it cannot be undone.)

Figure 4.21 Select/Delete tool coordinate system

#### Edit tool coordinate system

Click "Edit" to view or modify the alias and coordinate values of the currently selected tool coordinate system.

"Tool coordinate system 0" is the flange tool coordinate system and cannot be modified.

![Official manual image, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFkQ7pcb3CXgWkoQppdkM%2Fpallet-process-p034-img03.png?alt=media)

![Official manual image, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7jrgYA14sIhf2hN0zBPf%2Fpallet-process-p034-img04.png?alt=media)

![Official manual image, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F57y7xQvCSWWAbwhbjxv7%2Fpallet-process-p034-img05.png?alt=media)

Figure 4.22 Modify tool coordinate system

#### 4.2.2 Pallet user coordinate system

The pallet user coordinate system is calibrated at the factory before the palletizing workstation is shipped, and the calibration results are recorded on the "Palletizing Workstation Data Card" shipped with the product. The left pallet coordinate system corresponds to User Coordinate System 1 (User1), and the right pallet coordinate system corresponds to User Coordinate System 2 (User2). The origin of the pallet user coordinate system is on the ground, with the Z-axis pointing upward.

Figure 4.23 Palletizing Workstation Data Card

![Official manual image, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA4HeblzFfIxkTwyVvjiG%2Fpallet-process-p035-img02.jpg?alt=media)

![Official manual image, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUjSAjbM7HKACUKa1gF7i%2Fpallet-process-p035-img03.png?alt=media)

Figure 4.24 Pallet user coordinate system definition

However, after the palletizing workstation is installed, the actual pallet user coordinate system will inevitably deviate slightly from the factory default values. You must recalibrate the pallet user coordinate system by following the procedure below:

1. Click "New > Process teaching".

Figure 4.25 Coordinate system calibration entry

2. Prepare the pallet and boxes to be used. Place the pallet at the left working position of the base, and record the sizes of the pallet and boxes. Then control the robot arm to pick up a box and move it to three positions aligned with the edges of the pallet (as shown in the illustration). After entering the sizes, click "Next".

Figure 4.26 Enter box and pallet sizes

![Official manual image, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWfCasUZIyqgPOhteDjen%2Fpallet-process-p036-img02.png?alt=media)

![Official manual image, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXOU8MreDZDgSHeeDTMUN%2Fpallet-process-p036-img03.jpg?alt=media)

![Official manual image, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7bYXpU3vyoj0jMLy6H6Q%2Fpallet-process-p036-img04.jpg?alt=media)

**NOTICE**

* If you're using a dual-channel suction cup, prepare two boxes and treat them as a single unit to calculate the sizes.
* Ensure that the size of the subsequently placed boxes matches the size of the currently set boxes, and that the position of the pallet should be the same as the one in actual use.

3. After selecting the tool coordinate system corresponding to the suction cup, use the jog panel to move the robot arm so that the suction cup center is aligned with the box center. With the suction nozzle pressed against the box surface, click "Suction". Once the suction cup picks up the box, click “Next”.

Figure 4.27 Pick up the box

4. Jog the robot arm to place the box at the corresponding positions shown in the diagram (do not release the suction cup after the box is in position), then click "Obtain" for each position. Once all three points have been obtained, click "Next".

Figure 4.28 Get specified points

**NOTICE** Keep the edge of the box aligned with the edge of the pallet, otherwise there may be an error.

5. After successful calibration, you can release the suction cup on this page, then enter an alias (optional) and click "Finish". The system will save the user coordinate system and return to the coordinate system settings page.
6. After returning to the coordinate system settings page, the system will automatically select the newly created user coordinate system.

![Official manual image, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUFiHQyfJ1povlkA0UBx1%2Fpallet-process-p037-img02.png?alt=media)

![Official manual image, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS6MrTleWtkSY3ISd8E1W%2Fpallet-process-p037-img03.jpg?alt=media)

**NOTE** The operations for selecting/deleting a pallet user coordinate system are the same as those for the tool coordinate system.

#### 4.2.3 Picking-point user coordinate system

When incoming materials arrive, the box is placed against a certain edge of the conveyor. This edge and its vertices form a fixed coordinate axis. By teaching the conveyor user coordinate system, the system can automatically plan the center of the box as the picking point based on the entered box dimensions.

The "Picking-point user coordinate system" function is disabled by default. Once enabled, there is no need to teach the picking point separately.

**NOTICE** After enabling the "Picking-point user coordinate system" function, do not modify the coordinate system via the "Settings" page in DobotStudio Pro.

Figure 4.29 Picking-point user coordinate system

![Official manual image, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FadPuY4Cm01frjhrkTR7o%2Fpallet-process-p038-img02.jpg?alt=media)

**NOTICE** "Conveyor 1 picking point user coordinate system" and "Conveyor 2 picking point user coordinate system" correspond to different conveyors. A maximum of two conveyor coordinate systems can be created. When there is only one conveyor, "Conveyor 1 picking point user coordinate system" is used and selected by default.

If you need to create a new picking point user coordinate system by teaching, click "New > Process teaching" on the right side of the corresponding coordinate system to create and calibrate a picking point user coordinate system. The steps are as follows:

1. Select the conveyor direction and click "Next".

| **Outer → Inner**                                                                                  | **Left → Right**                                                                                           | **Right → Left**                                                                                            |
| -------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| <p>The conveyor is<br>perpendicular to the<br>workstation, and boxes<br>approach the robot arm</p> | <p>The conveyor is parallel<br>to the workstation, and<br>boxes approach the<br>robot arm from left to</p> | <p>The conveyor is parallel<br>to the workstation, and<br>boxes approach the<br>robot arm from right to</p> |
| from far to near.                                                                                  | right.                                                                                                     | left.                                                                                                       |

2. Locate the box center and mark the center point.

Figure 4.30 Locate the box center

![Official manual image, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FY5zxMFJLQ1xxFXw0CLMi%2Fpallet-process-p039-img05.jpg?alt=media)

3. Pick up the box as follows:
   * ① Select the tool coordinate system corresponding to the suction cup.
   * ② Jog the robot arm so that the suction cup center is aligned with the box center (for dual-channel suction cup, treat the two boxes being picked up as a single unit to calculate the center point).
   * ③ Press the suction nozzle against the box surface and click "Suction".
   * ④ Once the suction cup picks up the box, click "Next".

Figure 4.31 Pick up the box

Figure 4.32 Pick up the box center

![Official manual image, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FP5BhkD0zRiGApM90n5aP%2Fpallet-process-p040-img02.jpg?alt=media)

![Official manual image, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ftx4tYcA6xGgba1kuqjIv%2Fpallet-process-p040-img03.jpg?alt=media)

4. Based on the schematic showing the conveyor direction, select the position where the box is close to the conveyor, and click "Next".

Figure 4.33 Select the box position

Fixed to the leftmost edge

Fixed to the rightmost edge

Figure 4.34 Fixed position for the box

5. Measure the actual box dimensions, enter them with reference to the schematic on the page, and click "Next".

Figure 4.35 Enter box parameters

6. Jog the robot arm to move the box to the corresponding positions shown in the schematic (the pallet placement position must be consistent with actual application; do not release the suction cup after the box is in position), and click "Obtain" for each position. Once all three points have been obtained, click "Next".

![Official manual image, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn3ovnDObciwSqinKkjfV%2Fpallet-process-p041-img02.png?alt=media)

![Official manual image, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2PB4Siiw7hli56rOtInG%2Fpallet-process-p041-img03.jpg?alt=media)

![Official manual image, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGjwISynXq0496OWxpwAT%2Fpallet-process-p041-img04.jpg?alt=media)

![Official manual image, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Foa0rJ6DBrqm9hqCDyAkF%2Fpallet-process-p041-img05.png?alt=media)

Figure 4.36 Obtain the specified points

Figure 4.37 Positions for P1, P2 and P3

7. The interface displays the coordinate system parameters for the picking point. Enter an alias (optional).

Figure 4.38 Calibration result

8. Verify the result.
   * ① The interface displays the box dimensions and the indicated picking points. When the box dimensions are changed, the picking point coordinate values update in real time.
   * ② Click "Re-obtain" to automatically update the picking point coordinate system by comparing the robot arm's current position with the generated picking point coordinate system.
   * ③ After verifying the picking point for single suction, click "Double Suction" to verify the picking point for double suction.
   * ④ Click "Finish". The system will save the picking point user coordinate system and return to the coordinate system configuration page.

![Official manual image, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjVFPY1RdDVsFHsnNzYVG%2Fpallet-process-p042-img02.png?alt=media)

![Official manual image, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIkSnXGap5JLpcf3QSFhK%2Fpallet-process-p042-img03.jpg?alt=media)

![Official manual image, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfFeiUHntbUclE1fYeheA%2Fpallet-process-p042-img04.jpg?alt=media)

![Official manual image, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz1OyDEJObbLp1JTphCMg%2Fpallet-process-p042-img05.jpg?alt=media)

Figure 4.39 Verification result

9. After returning to the coordinate system configuration page, the system will automatically select the newly created picking user coordinate system.

**NOTE** The operations for selecting/editing/deleting a picking point user coordinate system are the same as those for the tool coordinate system.

#### 4.2.4 Interlayer user coordinate system

#### Interlayer instructions

Users can add interlayers between layers of boxes as needed. The palletizing workstation will, according to the user-specified interlayer parameters, automatically pick up an interlayer from the designated stacking area after a certain number of layers have been palletized and place it on top of the completed layers before continuing to palletize the next layer of boxes. During depalletizing, the system will automatically remove and place the interlayer back into the stacking area after depalletizing a certain number of layers.

Figure 4.40 Interlayer

#### Interlayer stacking zone

If you need to place (palletizing) or remove (depalletizing) an interlayer every few layers, the interlayer stacking zone needs to be determined. It is recommended to place the interlayers in the designated area first, then jog or drag the robot arm to confirm that the

![Official manual image, source page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9dqyssMeit4fUOdWEvCH%2Fpallet-process-p043-img02.png?alt=media)

![Official manual image, source page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpY9z70Pb8sgylxYnaZ7e%2Fpallet-process-p043-img03.jpg?alt=media)

end-of-arm suction cup can grip the topmost and bottommost interlayers.

It is recommended to stack the interlayers on the same side as the picking point. If they must be stacked on the opposite side of the picking point and require navigating around the stacked boxes, a customized version of the palletizing process package is needed. A typical usage example is shown below:

Figure 4.41 Recommended interlayer stacking position

#### Create interlayer coordinate system

For palletizing/depalletizing projects that involve interlayers, the interlayer user coordinate system must be configured first. "Single interlayer" is selected by default. If "Double interlayer" is selected, you can create and select left and right interlayer coordinate systems separately.

Figure 4.42 Single interlayer user coordinate system

![Official manual image, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEQikEg0z7wSB58dXgfB5%2Fpallet-process-p044-img02.jpg?alt=media)

![Official manual image, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxCMKhTSFVIEi2irEuOqW%2Fpallet-process-p044-img03.png?alt=media)

Figure 4.43 Double interlayer user coordinate system

Click "New > Numeric input" on the right of the corresponding coordinate system to directly enter the coordinate values for the interlayer user coordinate system. Alternatively, you can create the interlayer user coordinate system in advance via the "Settings" page of DobotStudio Pro, and then click the "Select" button here to choose it.

1. In DobotStudio Pro, click "Settings > Coordinate system > User coordinate system" to enter the user coordinate system settings page, and add or modify a user coordinate system.

Figure 4.44 User coordinate system

2. Click the "Three-point setting" button on the "Add user coordinate system" page.

Figure 4.45 Add user coordinate system

3. In the "Three-point setting" page, teach the system and obtain any three non-collinear points on the plane of the interlayer stacking zone (refer to the the figure below, the

![Official manual image, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2UNzjttudQ6ryypWYCgi%2Fpallet-process-p045-img02.jpg?alt=media)

![Official manual image, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkppHsWjMcDqPGuLHGRDF%2Fpallet-process-p045-img03.jpg?alt=media)

![Official manual image, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4KRmPRBUfsXhAponsusF%2Fpallet-process-p045-img04.png?alt=media)

Z-axis should be oriented towards the interlayer stacking direction), then click "Confirm".

Figure 4.46 User coordinate system - Three-point setting

4. The system automatically returns to the "Add user coordinate system" page, and the coordinate system values are updated to the calibrated values. Click "Save" to complete the user coordinate system settings for the interlayer.

### 4.3 Set automatic transition point

The current version of the palletizing process package supports the "Automatic transition point" function. Once enabled, there is no need to manually set transition points for each project. The robot will automatically generate transition points for each box through an algorithm, optimizing efficiency and reducing configuration complexity.

**NOTE** The robot needs to determine whether it will collide with the workstation or other obstacles during palletizing. Before using the automatic transition point function, first confirm the relative positions of the workstation and conveyor, as well as the safety zone.

#### 4.3.1 Motion trajectory with/without transition points

When the robot arm moves directly from the picking point to the placing point in a straightline trajectory and there is a risk of collision, you need to manually set transition points within the safety zone. The robot arm will bypass obstacles by moving from the picking point to the placing point via the transition point, ensuring the optimal trajectory. Below is an example of motion trajectories with and without transition points, using left-side palletizing as a reference:

![Official manual image, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFfpmBWXM2WsF3uP7x22C%2Fpallet-process-p046-img02.png?alt=media)

Fig 4.47 Trajectory with transition points

Fig 4.48 Trajectory without transition points

#### 4.3.2 Set automatic transition point

On the "Workstation settings" page, click "Auto-Transition" to enable or disable the automatic transition point function, and configure conveyor, safety zone, and obstaclerelated parameters.

Figure 4.49 Automatic transition points page

![Official manual image, source page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx7VeypsibiElGEeYA3rj%2Fpallet-process-p047-img02.jpg?alt=media)

![Official manual image, source page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMlIoLOxYZ6rWhLsgFg1k%2Fpallet-process-p047-img03.jpg?alt=media)

| **No.** | **Module**                               | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ------- | ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ①       | <p>Enable auto-<br>transition points</p> | <p>"OFF" by default. Once enabled, theLayer Transition Point<br>in the "Point settings" module can be set to "Custom"<br>(manual teaching) or "Auto-obtain". The robot will move<br>according to the "Diagram of trajectory with auto transition<br>points".</p>                                                                                                                                                                                                                                                                                                                                                                             |
| ②       | <p>Calibration pin<br>height</p>         | <p>For teaching points related to conveyors, safety zones,<br>and obstacles, it is recommended to use the calibration pin<br>included with the workstation. If the calibration pin is not<br>used, set the height to 0.</p>                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ③       | <p>Conveyor<br>parameters</p>            | <p><br>Select the number and direction of conveyors.<br><br>Configure the length, width, and height of the<br>conveyors (range: 0–1700 mm; if the set value<br>exceeds 1700 mm, the system will cap them at 1700).<br><br>Use jog mode in DobotStudio Pro to obtain the<br>teaching point for the conveyor (A1). See"Get<br>conveyor teaching point" for details.</p>                                                                                                                                                                                                                                                                     |
| ④       | <p>Safety zone<br>parameters</p>         | <p>The safety zone must be within the robot's motion range.<br>Its length and width may overlap with the pallet or<br>conveyor (range: 0–1700 mm). Its height is automatically<br>calculated by the robot and must be higher than the<br>conveyor height. No other objects are allowed in the safety<br>zone, otherwise collision risks may occur. The system has<br>two preset safety zones by default. Check "Interlayer<br>safety zone params" to configure the interlayer safety<br>zone. If the preset safety zones do not match the on-site<br>conditions, edit them accordingly. See"Teach the safety<br>zone range" for details.</p> |
| ⑤       | <p>Obstacle<br>parameters</p>            | <p>If there is equipment within the robot's reachable range<br>that poses a collision risk,add it as an obstacle to inform<br>the robot. The robot will then avoid the obstacle during<br>trajectory planning.</p>                                                                                                                                                                                                                                                                                                                                                                                                                           |

#### 4.3.3 Get conveyor teaching point

1. Attach the calibration pin to the robot.
2. Drag the robot's end-effector close to point A1.
3. Use the jog panel in DobotStudio Pro to fine-tune the position so that the calibration pin reaches point A. Ensure that the flange surface is parallel to the base (RX = 180°, RY = 0°), as shown below.

Figure 4.50 Reach the conveyor teaching point

4. Click "Obtain" to acquire the conveyor teaching point.

Figure 4.51 Get conveyor teaching point

**NOTE** The diagram in the process package will automatically update based on the selected number and direction of conveyors. Follow the actual diagram for calibration.

![Official manual image, source page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtUMBUIfMsAqN8MTjglXT%2Fpallet-process-p049-img02.jpg?alt=media)

![Official manual image, source page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIjXKqThizzJv8pF3dnCY%2Fpallet-process-p049-img03.png?alt=media)

#### 4.3.4 Teach the safety zone range

Teach the safety zone range (Example: Left safety zone):

1. Confirm the dimensions of the safety zone.
2. Based on the actual situation, select a point above the conveyor surface as the teaching point (B1).
3. The robot will automatically generate a safe space above the teaching point based on its motion range and the palletizing height, as shown below.

Figure 4.52 Teach the safety zone range

#### 4.3.5 Teach the interlayer safety zone range

The "Interlayer safety zone params" option is disabled by default. Once checked, interlayer safety zone parameters can be configured separately to generate automatic transition points for interlayers.

**NOTICE** The interlayer safety zone parameters take effect only after the "Interlayer auto-transition point" function is enabled, i.e., when "Interlayer settings > Auto pick interlayer > Interlayer transition point mode" is set to "Auto-obtain".

![Official manual image, source page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F19fzhwaldKOWqYaUovov%2Fpallet-process-p050-img02.png?alt=media)

Figure 4.53 Teach the interlayer safety zone range

* L3 × W3: Left interlayer safety zone range; L4 × W4: Right interlayer safety zone range.
* The teaching points B3 / B4 for the left and right interlayer safety zones can use the default values (i.e., the coordinate values of the safety zone teaching points B1 / B2 on the left and right pallets), or they can be re-taught based on the actual situation.
* Once the interlayer safety zone parameters take effect, the safety zones associated with the original automatic transition points for the interlayer will change from B1 and B2 to B3 and B4.

#### 4.3.6 Add obstacle

Click "Add obstacle" to access the following interface (up to 4 obstacles can be added). Enter the obstacle name, dimensions (length and width: 0–1700 mm, height: 0–3000 mm), and obtain the teaching points for the obstacle.

Figure 4.54 Add obstacle

![Official manual image, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmzUnc9BB4u44Ad7ODEiT%2Fpallet-process-p051-img02.png?alt=media)

![Official manual image, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FifOfioZLLczV6PHdDq6Z%2Fpallet-process-p051-img03.jpg?alt=media)

How to get the teaching points for the obstacle:

1. Attach the calibration pin to the robot.
2. Drag the robot's end-effector close to point C.
3. Use the jog panel in DobotStudio Pro to fine-tune the position so that the calibration pin reaches point C. Ensure that the flange surface is parallel to the base (RX = 180°, RY = 0°).

**NOTE**

* The point C for different obstacles (irregular objects are all treated as cubes, as indicated by the blue box in the figure below) is always at the upper-right corner of the cube, as shown below.
* When the obstacle height exceeds the robot's reachable height, select a point at the upper right of the robot's maximum reachable height, as shown below.
* When the automatic transition point is enabled, the height protection for the picking point is automatically activated and triggered during reachability check. The height of the picking point is calculated using the following formula, and if the height requirement is not met, a prompt will appear on the interface.

_Picking point height ≥ Conveyor teaching height + Box height - Calibration pin height_

![Official manual image, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsEFr7kLge9vkiTbhKsMm%2Fpallet-process-p052-img03.jpg?alt=media)

![Official manual image, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEhzYWGbXynxuQmQvsUIF%2Fpallet-process-p052-img04.jpg?alt=media)

### 4.4 Permissions

The table below outlines the functions available to different roles (Administrator / Technician / Operator).

Figure 4.55 Permissions

**Current Role:** Consistent with the role displayed in the robot status bar on DobotStudio Pro's home page.

Functions available to different roles:

* **Administrator** : Can access all functions of the palletizing process package.
* **Technician** : Can use all functions except those related to manufacturer configuration.
* **Operator** and **Custom** roles: Can only select, start, pause, or stop projects, and modify the number of palletized/depalletized layers and boxes on the process package home page's run panel. They cannot manage or debug palletizing projects, configure palletizing workstation, or perform manufacturer configuration.

### 4.5 Manufacturer configuration

Integrators and distributors can pre-configure parameters such as coordinate systems and signals before delivering the workstation to end users, and then hide them via the Manufacturer Configuration page to prevent accidental changes by end users.

Click the icon in the upper right corner of the palletizing process package home page and select "Manufacturer configuration". This function is only available under Administrator permissions. For other roles, the Manufacturer Configuration menu is grayed out and cannot be edited.

![Official manual image, source page 53](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcU8HruMmWBUwwd3BXZL5%2Fpallet-process-p053-img02.png?alt=media)

Figure 4.56 Manufacturer configuration entry

You can select which core function modules to show or hide. By default, all modules are visible, but you can freely choose modules to hide. Any changes will save the data as it was before hiding.

Figure 4.57 Manufacturer configuration

If this is the first time using the palletizing process package and the workstation has not yet been configured, ensure the workstation is configured before using the "Manufacturer configuration" function.

### 4.6 Import/Export configuration

Click in the upper right corner of the palletizing process package home page and select "Import/Export configuration".

Figure 4.58 Import/Export configuration

* After clicking "Export Configuration", you can customize the save path and file name for the exported file. The default file name is "Dobot Workstation Settings + Export

![Official manual image, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh0Zf7MBScMkqdzkyOdH0%2Fpallet-process-p054-img03.png?alt=media)

Time.json".

* After clicking "Import Configuration", the following prompt will appear. Since the coordinates may vary between workstations, the imported configuration data does not include coordinate system parameters. You will need to configure and confirm the coordinate systems after import. Click "Cancel" to close the prompt and abort the import process, or click "OK" to select the file path for the import.

Figure 4.59 Prompt

![Official manual image, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5DK3WBgI4UmbQt6F9yct%2Fpallet-process-p055-img02.png?alt=media)

## 5. Product Management

Click "Product management" on the home page to open the product library. Add products in advance (including box dimensions, number of layers, number of boxes, and stacking pattern). When creating a new palletizing project later, you can directly select a product that has already been added here without having to re-enter the information.

Figure 5.1 Product management

| **No.** | **Module**                             | **Description**                                                                                                                                                                                                                                                                                                                                  |
| ------- | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| ①       | <p>Enable<br>Product<br>Management</p> | <p>OFF by default. When it is ON, you can view, search,<br>import/export, delete, copy, edit, and create new stacking<br>patterns.</p>                                                                                                                                                                                                           |
| ②       | Product list                           | <p>Displays the name, box dimensions, number of layers,<br>number of boxes, and thumbnails of Pattern A/B for existing<br>products. The first product is selected by default. Click the<br>icon<br>to modify the product name.</p>                                                                                                               |
| ③       | <p>3D product<br>image</p>             | <p>When a product is selected from the product list, the 3D<br>stacking pattern of that product is displayed on the right. The<br>default view is from a top-down perspective, but you can drag<br>the mouse to change the viewing angle. Pallet dimensions<br>and box dimensions are displayed.</p>                                             |
| ④       | <p>Search<br>product</p>               | <p>Enter keywords in the input box to filter products whose<br>names contain the keywords. After filtering, the first pattern is<br>selected by default.<br>Search results can be sorted by creation time (newest first),<br>total number of boxes (highest first), or by pattern name.<br>Results can also be filtered by suction cup type.</p> |
| ⑤       | <p>Import<br>product</p>               | <p>Click "Import", select the file from the path where the product<br>file is located, and add external products to the current</p>                                                                                                                                                                                                              |

![Official manual image, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSSnBfGsux1PCdiAYtMJn%2Fpallet-process-p056-img02.png?alt=media)

![Official manual image, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3qSFNxYiZFtcgGAWu7NG%2Fpallet-process-p056-img03.jpg?alt=media)

| **No.** | **Module**               | **Description**                                                                                                                                                                                                                                                                                                                                     |
| ------- | ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|         |                          | product library.                                                                                                                                                                                                                                                                                                                                    |
| ⑥       | <p>Export<br>product</p> | <p>Click "Export" to export all products from the product library.<br>You can customize the save path and file name for the<br>exported file. The default file name is "Dobot Pattern Library +<br>Export Time.json".</p>                                                                                                                           |
| ⑦       | <p>Delete<br>product</p> | <p>Select a product and click "Delete". A confirmation pop-up will<br>appear. After deletion, the first product in the list will be<br>automatically selected.</p>                                                                                                                                                                                  |
| ⑧       | Copy product             | <p>Select a product and click "Copy". The copied product will be<br>named "Original Name_1" by default. The creation time is set<br>to the time the copy was completed. After copying, the new<br>product will be automatically selected.</p>                                                                                                       |
| ⑨       | Edit product             | <p>Select a product and click "Edit". The interface will redirect to<br>theSet box/pallet parameterspage.</p>                                                                                                                                                                                                                                       |
| ⑩       | <p>Create<br>product</p> | <p>The process for creating a new product is the same as<br>configuring parameters for a new palletizing project. The box<br>dimensions and pallet dimensions from the last created<br>pattern will be automatically filled in. When the number of<br>patterns reaches 100, clicking "New" will prompt that a new<br>pattern cannot be created.</p> |

## 6. New Palletizing Project (With Interlayer)

Figure 6.1 Workflow for a New Palletizing Project With Interlayer

For palletizing projects with interlayers, the Interlayer User Coordinate System must be created in advance. When creating a new palletizing project, select "With Interlayer" and click "Next" to enter the "Interlayer settings" page. For parameter configuration on other pages, refer to "New Palletizing Project (Without Interlayer)".

Figure 6.2 Project basic parameters (with interlayer)

### 6.1 Auto pick interlayer

The following uses the palletizing project interface as an example. The depalletizing project interface is essentially the same; differences are noted where applicable.

Figure 6.3 Auto pick interlayer page

![Official manual image, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCRe7ucjerqlBSTW0CDFj%2Fpallet-process-p058-img02.png?alt=media)

![Official manual image, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaMX8kP4HPWpGkkWy1xsa%2Fpallet-process-p058-img03.jpg?alt=media)

![Official manual image, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fewqzetgw2a5yLrXacp9z%2Fpallet-process-p058-img04.jpg?alt=media)

* ① **Single/Double interlayer point:**

This option appears only when the current project is a dual-side (2 pallets) project and "Double interlayer" is selected in the Interlayer User Coordinate System page with both left and right interlayer coordinate systems configured. The default is "Single interlayer point". When switching to "Double interlayer points", parameters for both left and right interlayers must be configured separately.

* ② **Total interlayers at interlayer-picking point:**
  * In palletizing mode, this field is displayed as "Total interlayers at interlayerpicking point". In depalletizing mode, it is displayed as "Max capacity at interlayer-placing point". Unit: pcs. Range: (0, 100].
  * In "Double interlayer points" page, the total interlayer counts for the left and right sides must be set separately.

Fig 6.4 Total interlayers at interlayer-picking point (Single interlayer point)

Fig 6.5 Total interlayers at interlayer-picking point (Double interlayer points)

* In palletizing mode, this represents the number of interlayers in each stack. If the system detects that the interlayers have been used up, it will pause and prompt you to replenish them. The replenished interlayers must be placed in the same position and quantity as the previous stack; otherwise, interlayer counting errors will occur and the project will report an error. The minimum value in palletizing mode is 1 (if set to 0, a pop-up will indicate insufficient interlayers).
* In depalletizing mode, this represents the maximum number of interlayers that can be stacked at the interlayer placement position. When the system detects that the interlayer placement position is full, it will pause and prompt you to remove them. After resuming, the system will continue placing interlayers at that position. The maximum value in depalletizing mode = Total interlayers - 1.

Fig 6.6 Max capacity at interlayer-placing point (Double interlayer points)

![Official manual image, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FISjuUCxfPxw6B7yFmYNR%2Fpallet-process-p059-img02.png?alt=media)

![Official manual image, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5wm9dpcGF90LaOXWCyGK%2Fpallet-process-p059-img03.png?alt=media)

![Official manual image, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdXZMl1UH89hAlq7lBJVX%2Fpallet-process-p059-img04.png?alt=media)

* ③ **Interlayer remaining quantity alert threshold:**

Available only in palletizing mode. The default value is 0. The set value cannot exceed the "Total interlayers at interlayer-picking point". If the remaining interlayers are detected to be ≤ the alert threshold (non-zero), a prompt will indicate insufficient interlayer stock.

**NOTE** In the following scenarios, no insufficient interlayer stock prompt will appear during palletizing:

* The interlayer detection signal is enabled in "Workstation settings > Basic settings > Interlayer signal".
* The "Interlayer remaining quantity alert threshold" is set to 0.

#### ④ **Interlayer size:**

Set the interlayer length, width, height, and weight. In "Double interlayer points" page, the dimensions for the left and right sides must be set separately.

* Interlayer length and width default to pallet length and width; thickness defaults to 1 mm. The maximum values for length, width, and height are 2000 x 2000 x 150. Decimal values are accepted.
* Interlayer weight defaults to 2 kg. Range: (0, 100]. Decimal values are accepted.

**NOTICE** Interlayer size cannot be set to 0; otherwise, an error will occur during "Reachability check".

#### ⑤ **Interlayer transition point mode:**

Supports "Auto-obtain" or "Custom" for interlayer transition points.

**NOTICE** The "Auto-obtain" option for Interlayer Transition Point Mode can be enabled only after Layer Transition Point is set to "Auto-obtain" on the Point Settings page.

* **Auto-obtain:**

Figure 6.7 Interlayer transition point mode - Auto-obtain

![Official manual image, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPINlhoLOxvlykQqpMYLA%2Fpallet-process-p060-img02.png?alt=media)

After switching to "Auto-obtain", click the dropdown menu to select the layer (the interlayer corresponding to each layer is shown in the table below). After a successful "Reachability check", interlayer transition points will be generated automatically.

Click "3D trajectory preview" to preview the point trajectory connections; click again to hide.

| **Layer**     | **Corresponding interlayer**                 |
| ------------- | -------------------------------------------- |
| Bottom        | The first interlayer at the bottom           |
| Layer 1       | The interlayer above the first box           |
| Layer 2       | The interlayer above the second box          |
| Layer n (Top) | The interlayer above the last layer of boxes |

* **Custom:**

After switching to "Custom", manually teach the interlayer transition point positions on this page. See "Interlayer placing point / Transition point" for details.

#### ⑥ **Interlayer position:**

Set the position where interlayers are added. Check or click the empty space between layers to add an interlayer for that layer, including the top and bottom layers.

Figure 6.8 Interlayer position

* ⑦ **Set interlayer points:** Includes the interlayer picking point, safe home position before interlayer pickup, safe home position after interlayer pickup, interlayer placing point, and any number of transition points (at least 1, up to 5).

#### Interlayer picking point:

* **For palletizing:** Set the first point as the interlayer picking point, which should be at the bottommost interlayer in the stacking zone (see "Interlayer stacking zone" for details). The system will automatically calculate the picking points for the remaining interlayers based on the number of interlayers already used and their thickness. The interlayer placing point is where the first interlayer will be placed on each pallet.
* **For depalletizing:** Set the first point as the interlayer placing point, which should be at the bottommost interlayer in the stacking zone. The system will automatically calculate the placing points for the remaining interlayers based on

![Official manual image, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4zJW3kEJ215X8QgCgC6d%2Fpallet-process-p061-img02.png?alt=media)

the number of interlayers already placed and their thickness. The interlayer picking point is where the first interlayer will be picked up from each pallet.

* The Single/Double Interlayer Point pages are displayed differently, as shown below:

Figure 6.9 Interlayer-picking point settings (Single interlayer point)

Figure 6.10 Interlayer-picking point settings (Double interlayer points)

#### Interlayer placing point / Transition point:

Interlayer transition points are required only when "Custom" is selected in the "Interlayer transition point mode" (at least 1, no more than 5). The Single/Double Interlayer Point pages are displayed the same:

Figure 6.11 Interlayer placing point / Transition point settings

**NOTE** The coordinate values for the picking/placing points displayed on the interface are based on the interlayer coordinate system, while the coordinate values for the interlayer transition points are based on the pallet coordinate system on the corresponding side.

![Official manual image, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq3wWiYjs61m0HluF1Fun%2Fpallet-process-p062-img02.png?alt=media)

![Official manual image, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm2hke6qUm87vsWC6tntW%2Fpallet-process-p062-img03.png?alt=media)

![Official manual image, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWd291aAADzpeGbht0CN6%2Fpallet-process-p062-img04.png?alt=media)

#### Safe home position after interlayer pickup:

One point is provided by default, and up to 5 points can be added. Safety points are fixed and do not change with the lifting column position. The Single/Double Interlayer Point pages are displayed differently:

Figure 6.12 Safe home position before interlayer pickup (Single interlayer point)

Figure 6.13 Safe home position before interlayer pickup (Double interlayer points)

#### Safe home position after interlayer pickup:

Left and right pallets are distinguished separately. One point is provided by default, and up to 5 points can be added to left or right pallet. Safety points are fixed and do not change with the lifting column position. The Single/Double Interlayer Point pages are displayed the same:

Figure 6.14 Safe home position after interlayer pickup

![Official manual image, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLyzWUWYgqifj4aCOA6rN%2Fpallet-process-p063-img02.png?alt=media)

![Official manual image, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlIBMrIdLlLcSFgaCraIr%2Fpallet-process-p063-img03.png?alt=media)

![Official manual image, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fszp4w7NplGcxt3xL30bP%2Fpallet-process-p063-img04.png?alt=media)

**NOTICE**

* Safe home position cannot be set to 0.
* It is recommended to set the safe home positions before and after interlayer pickup to different points; otherwise, CP smoothing will not be available.

### 6.2 Manually place interlayer

This function is available only for palletizing projects with interlayers. You can customize the interlayer thickness and specify the layer where the interlayer is to be placed.

Figure 6.15 Manually place interlayer

![Official manual image, source page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJoHXaD06hXsZiWgt1EmE%2Fpallet-process-p064-img02.png?alt=media)

## 7. New Palletizing Project (Without Interlayer)

Figure 7.1 Workflow for a New Palletizing Project Without Interlayer

### 7.1 Set basic parameters

1. Click "New Project" in the upper-right corner of the home page to create a new project. To import an existing project, click "More projects" and import it from the project list page.

Figure 7.2 New palletizing project

2. Configure the basic parameters of the project based on your actual application scenario. You can preview the configuration in real-time through the 3D model on the right side of the interface. Once configuration is complete, click "Next" to proceed to the box/pallet settings page.

Figure 7.3 Project basic parameters (without interlayer)

#### 7.1.1 Palletizing mode

Select the palletizing mode based on the actual number of pallets and conveyors in your application. In "2 Conveyors 2 Pallets" mode, each conveyor is paired with a specific pallet. When palletizing, boxes from Conveyor 1 will be stacked onto the left pallet, and boxes from Conveyor 2 will be stacked onto the right pallet. The same logic applies to depalletizing.

![Official manual image, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIXItbvP3NWJgbCEurUGz%2Fpallet-process-p065-img02.png?alt=media)

![Official manual image, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw37pJR6dT6a0SEH4IrIe%2Fpallet-process-p065-img03.png?alt=media)

![Official manual image, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fwm45sUAdrE01N74k0Ai3%2Fpallet-process-p065-img04.jpg?alt=media)

**NOTE**

* In "1 Conveyor 2 Pallets" mode, when both pallets are in position, the workstation will first complete the full stack on the left pallet, then palletize the right pallet.
* "2 Conveyors 2 Pallets" mode is suitable for scenarios where the two conveyor lines have similar throughput and box sizes are roughly the same. A buffer zone should be set up on the conveyors to handle material accumulation.
* In "2 Conveyors 2 Pallets" mode, when both pallets are in position, the workstation will alternately palletize the two pallets. See "2 Conveyors 2 Pallets Configuration" for details.

#### 7.1.2 Palletizing type

* **Palletizing:** Pick up the boxes from the conveyor and stack them on the pallet.
* **Depalletizing:** Remove boxes from the pallet and place them onto the conveyor. The parameters need to be configured are similar to palletizing, with only some point definitions differing.
* **Demo mode:** Available only when the palletizing mode is "1 Conveyor 2 Pallets". Used to demonstrate the palletizing workstation at trade shows.

#### 7.1.3 Other accessories

* **Conveyor direction:** Set the direction of the conveyor relative to the workstation based on your actual application. When the palletizing mode is "2 Conveyors 2 Pallets", only "Outer → Inner" is available.
  * **Outer → Inner:**

The conveyor is perpendicular to the workstation, and boxes approach the robot arm from far to near.

Figure 7.4 Outer → Inner

 **Left → Right:**

![Official manual image, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMb6WYhos2lRsRLgKnFcH%2Fpallet-process-p066-img02.jpg?alt=media)

The conveyor is parallel to the workstation, and boxes approach the robot arm from left to right.

Figure 7.5 Left → Right

* **Right → Left:**

The conveyor is parallel to the workstation, and boxes approach the robot arm from right to left.

Figure 7.6 Right → Left

* **Interlayer:** For palletizing, select based on whether interlayers need to be placed between layers of boxes. For depalletizing, select based on whether the stacking pattern to be depalletized contains interlayers. When "With Interlayer" is selected, create the Interlayer User Coordinate System in advance based on the interlayer placement zone.
* **Box type:** The "Two sizes" option is available only when the palletizing mode is "2 Conveyors 2 Pallets". Each box size is paired with one specific conveyor and one pallet. For example, the boxes arriving on Conveyor 1 must be of the same size and are only stacked onto the left pallet.

![Official manual image, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8Yt6IasjRJfWmemLjOtS%2Fpallet-process-p067-img02.jpg?alt=media)

![Official manual image, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbngdbnjjeKQSV1BXcIzs%2Fpallet-process-p067-img03.jpg?alt=media)

### 7.2 Set box/pallet parameters

Figure 7.7 Box/pallet parameter

#### 7.2.1 Box parameter

Figure 7.8 Box parameter

| **Parameter** | **Description**                                                                                                                                                                                                                                                                                                                                                                   |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Box size      | <p>Enter the actual box dimensions (length should be greater than<br>width; use "Rotate 90°" to adjust box direction) or select an existing<br>product. Click "Choose existing product" to navigate to the"Product<br>management"page. The system will automatically display the box<br>dimensions, weight, and stacking pattern when a corresponding<br>product is selected.</p> |
| Weight        | <p>Enter the actual weight of the box, or it will be automatically<br>entered when an existing product is selected.</p>                                                                                                                                                                                                                                                           |
| Box direction | <p>Click "Rotate 90°" to adjust based on the actual box posture when<br>it arrives on the conveyor (long side forward / short side forward).<br>The adjustment effect can be previewed in the 3D model on the<br>right of the interface.</p>                                                                                                                                      |

![Official manual image, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrcJALuHgk1MXl6fgzU8F%2Fpallet-process-p068-img02.jpg?alt=media)

![Official manual image, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJYPgSlbSVbU66ot0NhbQ%2Fpallet-process-p068-img03.png?alt=media)

| **Parameter**   | **Description**                                                                                                                                                                                                                                                                                                             |                                 |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------- |
| Label direction | <p>To design the stacking pattern<br>based on the label position on<br>the box, select the direction of<br>the box face where the label is<br>located (relative to the<br>conveyor's forward direction).<br>Once selected, it will be<br>displayed in the 3D model and<br>in the subsequent stacking<br>pattern editor.</p> | Fig 7.9 Label direction (front) |

**NOTE** The "Choose existing product" button for "Box size" will only appear if you have added products on the "Product management" page in advance; otherwise, this button will not appear.

In "2 Conveyors 2 Pallets" mode, if two box sizes are selected, each must be configured separately. "Box 1 size" corresponds to the box parameters for palletizing on the left pallet, "Box 2 size" corresponds to the box parameters for palletizing on the right pallet.

Figure 7.10 Box parameter\_Two sizes

![Official manual image, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiGBnhYG2Oazyc7NdWVkK%2Fpallet-process-p069-img02.jpg?alt=media)

![Official manual image, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FL3ZPQjuBRE4JnNOExl6N%2Fpallet-process-p069-img03.png?alt=media)

#### 7.2.2 Placement lift height

It corresponds to the height at which the box is finally lowered vertically during palletizing, i.e., the height difference between the point directly above the placement point and the placement point itself. The box will approach the point directly above the placing point from a specified direction according to the placement direction and offset settings, and then be lowered vertically, as shown in the figure below.

Figure 7.11 Placement lift height diagram

* The default placement lift height is 100 mm. Positive (upward) or negative (downward) values are supported. If the box height is modified, the placement lift height will automatically update to half of the box height.
* The placement lift height is distinguished between the left and right pallets, and the values for both sides are displayed synchronously. If there are two box sizes, changes to the box height on the left pallet will only affect the placement lift height on the left side; the same applies to the right side. Adjust according to actual situation.

Figure 7.12 Placement lift height (Single side)

Figure 7.13 Placement lift height (Both sides)

![Official manual image, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUlF2SdNl2ySpyVu1viOw%2Fpallet-process-p070-img02.png?alt=media)

#### 7.2.3 Pallet parameter

Figure 7.14 Pallet parameter (Single side)

Select the corresponding pallet size from the dropdown menu, or select "Custom" and manually enter the pallet’s length, width, and height.

In "2 Conveyors 2 Pallets" mode with two box sizes, the pallet sizes for the left and right sides can be set separately.

Figure 7.15 Pallet parameter (Both sides)

**NOTE** Pallet size affects the minimum box size that can be palletized. To confirm the box size, perform a simulation in the Simulation System.

### 7.3 Set stacking pattern

Based on the box size and label direction for each product, users can design the layout of boxes on the pallet. Some products require the same layout for each layer, while others may require different layouts for different layers. This three-dimensional arrangement of boxes is called "stacking pattern". The DOBOT Palletizing Process Package is preconfigured with 2 patterns and supports user-defined patterns, allowing users to add up to 3 additional patterns.

![Official manual image, source page 71](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FexUzViEpgPHPsNhHw8au%2Fpallet-process-p071-img03.png?alt=media)

Figure 7.16 Pattern

* For one box size: The stacking pattern is the same for both left and right pallets. You can switch the perspective of the diagram (left/right pallet) through the drop-down menu. For two box sizes: You need to set the stacking patterns for the left and right pallets separately. Set the left pallet’s pattern based on the size of Box 1, and the right pallet’s pattern based on the size of Box 2.

Figure 7.17 Pattern settings (One size)

* Click the "+" button next to "Pattern A" or "Pattern B" to add a new pattern (up to three additional patterns). Each pattern represents the arrangement of boxes for one layer. When configuring the palletizing method later, you can set the number of layers and assign a pattern for each layer.

Figure 7.18 Add pattern

![Official manual image, source page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNDbzhR6GzicztUg88sge%2Fpallet-process-p072-img02.jpg?alt=media)

![Official manual image, source page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO4DcdS6Ypn7DotJGx8mK%2Fpallet-process-p072-img03.jpg?alt=media)

* Click "Auto pattern" to select a recommended pattern that automatically generated by the system. Click "Edit" to modify the current pattern.

**NOTE** If the box sizes have not been set, clicking "Auto pattern" will display a pop-up message: "Please confirm the pallet and box size first".

#### 7.3.1 Auto pattern

The "Auto pattern" function is only applicable to scenarios where only one box is picked up at a time.

Figure 7.19 Recommended pattern

| **Parameter**                           | **Description**                                                                                                                                |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| Min Box Spacing                         | <p>The minimum distance between boxes. Unit: mm. Default: 5<br>mm.</p>                                                                         |
| <p>Min Top/Bottom<br>Pallet Spacing</p> | <p>The minimum distance between the boxes and the top/bottom<br>edges of the pallet. Unit: mm. Default: 5 mm.</p>                              |
| <p>Min Left/Right<br>Pallet Spacing</p> | <p>The minimum distance between the boxes and the left/right<br>edges of the pallet. Unit: mm. Default: 5 mm.</p>                              |
| Exceed the edge                         | <p>Default is "No". If "Yes" is selected, boxes may overhang the<br>pallet edge. The maximum overhang is 40% of the box’s shorter<br>side.</p> |

* The system will automatically generate recommended patterns based on the parameters you’ve set. If the above parameters are modified, click "Regenerate pattern", and the system will update the recommended patterns based on the new parameters.

![Official manual image, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9liA0CYrsHj7F7na7T2k%2Fpallet-process-p073-img02.jpg?alt=media)

**NOTE** No recommended pattern is available for extreme parameters. The system will display the message: "There is no recommended palletizing pattern under the current parameters, please reset the parameters."

* After selecting a pattern, click "Edit" to enter the Pattern Editing interface. The selected pattern will be automatically processed to generate the placement order, offset direction, and offset values, and then loaded into the current pattern. You can modify the selected pattern as needed. If no recommended pattern is available, the "Edit" button is disabled.
* Quick apply:

Figure 7.20 Quick apply

* If this option is unchecked, the associated dropdown menu is grayed out and disabled.
* If this option is checked, the selected pattern can be rotated 180° (default) or mirrored, and quickly applied to a specified pattern upon saving.
* The pattern dropdown menu does not include the current pattern. For example, if you entered "Auto pattern" page from Pattern A, the dropdown menu will only display options other than Pattern A.

#### 7.3.2 Edit pattern

Figure 7.21 Edit pattern

**No. Description** ① Switch to the stacking pattern you want to edit.

![Official manual image, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhYKC2cYl7FVQ0hu4Zo37%2Fpallet-process-p074-img03.jpg?alt=media)

| **No.** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ②       | "Copy/Paste" button: Used to copy the current pattern to another one.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| ③       | Check the direction in which the box is placed and removed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ④       | Displays a preview of the current pattern.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| ⑤       | <p>Define how the suction cup picks up and places the boxes. Options: "Single<br>Pick-and-Place" (Pick One, Place One), "Dual Pick-and-Place" (Pick Two,<br>Place Two), "Dual Pick, Single Place" (Pick Two, Place One), "Triple Pick-<br>and-Place" (Pick Three, Place Three), "Quadruple Pick-and-Place" (Pick<br>Four, Place Four).<br>For "Dual Pick, Single Place" (Pick Two, Place One): When adding boxes,<br>boxes in the same group must have the same serial number. When deleting,<br>boxes in the same group are deleted together. One-click generation and<br>manual modification of serial numbers are not supported.</p> |
| ⑥       | See"Edit box placement pattern” for details.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ⑦       | <p><br>Yes: Boxes may overhang the pallet edge, up to a maximum of 40% of<br>the box's shorter side (points are reachable but at the limit; improper<br>placement direction or offsetmay cause collisions).<br><br>No: If there are already boxes overhanging the pallet edge, they will be<br>automatically adjusted to align flush with the pallet edge.</p>                                                                                                                                                                                                                                                                        |
| ⑧       | See"Set placement order and direction offset"for details.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ⑨       | See"Set placement/leave direction and offset" for details.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

#### Edit box placement pattern

Fig 7.22 Box placement pattern

(single box selected)

Fig 7.23 Box placement pattern

(multiple or all boxes selected)

![Official manual image, source page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM72kjekjVjRwKc0JlF3X%2Fpallet-process-p075-img02.png?alt=media)

![Official manual image, source page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWg64REUClW1Gq2xVLB0S%2Fpallet-process-p075-img03.png?alt=media)

| **Parameter/Icon**        | <p><strong>Description</strong><br>Click "Add box" to add one box. For "Dual Pick-and-<br>Place" mode, two boxes are added at a time, but<br>they are treated as a single unit. The same logic<br>applies to "Triple Pick-and-Place" and "Quadruple<br>Pick-and-Place" modes. A maximum of 50 boxes can<br>be added to one pattern.</p>         |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Add box                   |                                                                                                                                                                                                                                                                                                                                                 |
|                           | <p><br>The blue line next to the box indicates the box<br>label (if set to "No label" inBox Parameter,<br>there will be no blue line).<br><br>The number on the top left indicates the box<br>placement order.<br><br>The arrow in the center of the box indicates the<br>placement direction. See the following section<br>for details.</p> |
| Multi-select / Select All | <p>Click "Multi-select" to select or deselect multiple<br>boxes by clicking them in the pallet area. Click<br>"Select All" to select all boxes on the current pallet.<br>When a box is selected, a blue border will appear<br>around it, and the distance to the nearest box or<br>pallet edge will be displayed.</p>                           |
|                           | Set the jogging distance for the box, unit: mm.                                                                                                                                                                                                                                                                                                 |
|                           | <p>Direction keys, used to jog the selected boxes in the<br>specified direction.</p>                                                                                                                                                                                                                                                            |
|                           | Delete the selected box.                                                                                                                                                                                                                                                                                                                        |
|                           | <p>Rotate the selected box 90° clockwise, the box label<br>will rotate accordingly.</p>                                                                                                                                                                                                                                                         |
|                           | <p><br>When"Label direction"is set to"No label",</p>                                                                                                                                                                                                                                                                                           |

![Official manual image, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FE4SSmPYFe0sp1ihW5njF%2Fpallet-process-p076-img02.png?alt=media)

![Official manual image, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD0FBtFOUApcUQBMl72mw%2Fpallet-process-p076-img03.png?alt=media)

| **Parameter/Icon** | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                    | <p>rotation options are 0° and 90° clockwise.<br><br>When "Label direction" is set to "With label",<br>rotation options are 0°, 90°, 180°, and 270°<br>clockwise.</p>                                                                                                                                                                                                                                                                                                                                                    |
|                    | <p>Single-box alignment icons. Align the selected box to<br>a specific direction. The selected box will align with<br>the edge of the nearest box in that direction. If there<br>is no other box in that direction, it will align with the<br>pallet edge.</p>                                                                                                                                                                                                                                                            |
|                    | <p>Multi-box alignment icons. Appears only in<br>"Multi-select" or "Select All" mode. Used for aligning<br>multiple boxes as a group.<br><br>Left / Right / Bottom / Top align: Requires at<br>least 2 boxes. Aligns based on the leftmost,<br>rightmost, bottommost, or topmost box edge<br>among the selected boxes.<br><br>Horizontally / Vertically distribute: Requires at<br>least 3 boxes. Distributes the selected boxes<br>evenly in the horizontal or vertical direction<br>based on their center points.</p> |
| Center             | <p>Move all boxes in the current pattern as a single unit<br>to the center of the pallet.</p>                                                                                                                                                                                                                                                                                                                                                                                                                             |

**NOTE** If any boxes overlap, the corresponding box icon will turn red.

![Official manual image, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjuxMlTHY9FEvAFdyYj6n%2Fpallet-process-p077-img05.png?alt=media)

#### Set placement order and direction offset

Figure 7.24 Placement order and direction offset

On the "Place" tab, click the "Quick Generation" button. A pop - up window will appear showing sorting rule options. Select the desired sorting rule as needed. The dropdown menu is used to set the placement order for the currently selected box. The robot arm places boxes one by one in numerical order. The schematic diagrams for different sorting rules are shown below:

From Far to Near, From Far to Near, From Near to Far, From Near to Far,\
From Top to Bottom From Bottom to Top From Top to Bottom From Bottom to Top<br>

**NOTICE** This function is available only when the page is on the "Place" tab. When you switch to the "Leave" tab, the "Quick Generation" button is disabled.

![Official manual image, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiBDLZ5KniAvFimcaLQ6Y%2Fpallet-process-p078-img02.png?alt=media)

![Official manual image, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVrxX2ELQzg981SyX6Co1%2Fpallet-process-p078-img03.jpg?alt=media)

![Official manual image, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTR528K1hHiolHN8VViWb%2Fpallet-process-p078-img04.jpg?alt=media)

![Official manual image, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKDnBCvZorT7BlcxAdSNr%2Fpallet-process-p078-img05.jpg?alt=media)

![Official manual image, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3pyBQ36HkRdSKTJLRKxY%2Fpallet-process-p078-img06.jpg?alt=media)

#### Set placement/leave direction and offset

During placement, configure the direction from which the arm approaches the point above the box placement location and its offset. This helps prevent interference between boxes. Set a safe leave direction and offset as well, particularly for fragile goods. Start with the defaults and adjust them during commissioning.

The **Placement mode** can be **Same**, applying one direction and offset to all boxes, or **Separate**, allowing each selected box to have its own settings. The default approach direction is directly above the placement point. The absolute placement offset is measured in millimetres and accepts values from 0 to 1,500 mm. If unchanged, X and Y default to 50 mm, while Z defaults to the box height. Only the offsets relevant to the selected direction can be edited; refer to the official diagram for direction-specific axes.

After placing a box, the arm moves to the leave-offset position. The default leave direction is opposite the approach direction, but both the leave direction and offset can be changed independently. For a double-pallet configuration, these settings are relative to the current pallet, and the software mirrors them for the opposite pallet.

![Official placement-direction diagram, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKd9N0XPmVzRRPnJ71uv9%2Fpallet-process-p079-img03.jpg?alt=media)

![Official placement/leave offset settings, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F11wPso4ocyjbz6pxdiJQ%2Fpallet-process-p079-img04.jpg?alt=media)

### 7.4 Set layers

Set the number of palletizing/depalletizing layers, the stacking pattern to be used for each layer, and whether to enable Safe Placement Mode for that layer (i.e., switching to a lowforce safety mode during the movement from the offset point to the placement point).

* For "1 Conveyor 1 Pallet" projects with one box size, the layer settings are shown in the figure below:

Figure 7.27 Layer settings (1 conveyor 1 pallet, 1-size box)

* For "2 Conveyors 2 Pallets" projects with two box sizes, the layer settings are shown in the figure below. The palletizing/depalletizing mode for the left and right pallets must be set separately:

Figure 7.28 Layer settings (2 conveyors 2 pallets, 2-size box)

* For "1 Conveyor 1 Pallet" and "2 Conveyors 2 Pallets" projects with one box size, the layer settings are shown in the figure below: When "Both-side setting" is enabled, you can set the layer height and stacking pattern for the left and right sides separately. The home page panel will dynamically calculate the total number of boxes based on the different stacking patterns on each side.

![Official manual image, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm5pEpK7j4j0JMgBCEhcz%2Fpallet-process-p081-img02.png?alt=media)

![Official manual image, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzljXPWPOzLhktsVbbS1X%2Fpallet-process-p081-img03.png?alt=media)

Figure 7.29 Layer settings (2 pallets, 1-size box)

### 7.5 Set points

Figure 7.30 Point settings

You should refer to the instructions and illustrations on the page to set the picking points (placing points for depalletizing) and transition points. Click "3D-Preview" to view the recommended point positions in the 3D model on the right of the page. Click this button again to hide the points in the 3D model.

![Official manual image, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6NWSNl49cLY6ymeLiC3z%2Fpallet-process-p082-img02.png?alt=media)

![Official manual image, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1wGgL3VbCQsfiuGub8T3%2Fpallet-process-p082-img03.jpg?alt=media)

Figure 7.31 Preview 3D illustration

The point where the robot arm picks up boxes from the conveyor during palletizing is referred to as the "picking point". During depalletizing, the corresponding point where boxes are placed onto the conveyor is called the "placing point". This following will focus on the picking point as an example.

The picking point is a fixed point, so the conveyor must be secured to the floor to prevent its position from changing. Additionally, stoppers and guide rails should be used to ensure that the boxes stop at a fixed position at the end of the conveyor, ready for the robot arm to pick them up.

The following figure illustrates an example of using guide rails to fix the position of the boxes:

* One side of the conveyor has a fixed guide rail for aligning the boxes.
* The other side of the conveyor has an adjustable guide rail to guide the boxes into the correct position. The position of this rail should be adjusted based on the actual width of the boxes.

Figure 7.32 Conveyor guide rail example

For depalletizing, guide rails are not required, you just need to ensure the placing point is located on the conveyor.

![Official manual image, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDdg7RPQ5De3dtWWo206b%2Fpallet-process-p083-img02.jpg?alt=media)

![Official manual image, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKmNwltDRGU2Fr3CerApj%2Fpallet-process-p083-img03.png?alt=media)

#### 7.5.1 Picking point / placing point

The coordinate values of the picking point (palletizing) / placing point (depalletizing) displayed on the interface are based on the left pallet coordinate system.

Figure 7.33 Picking point / placing point settings

* **Auto-obtain (default)**

This option is available only when "Enable picking point user coordinate system" is turned on in the "Workstation settings > Coordinates settings" page. Once enabled, the picking point will be automatically generated after a successful "Reachability check".

* **Custom**

Figure 7.34 Custom picking point / placing point

Check "Custom". The following uses the picking point settings as an example; the placement point settings are similar:

1. Place the box on the conveyor and jog the robot arm so that the end-of-arm suction cup contacts the box. The posture of the robot arm’s end effector during each pick will be the same as the posture taught for the picking point. Therefore, when teaching the picking point, ensure that the suction cup center is aligned with the box center (for dual-suction cups, treat the two boxes as a single unit when calculating the center), and that the long side of the suction cup is parallel to the long side of the box. Refer to the figure below for the recommended

![Official manual image, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS8XPjJDTCGhgXXdF2QWW%2Fpallet-process-p084-img02.png?alt=media)

![Official manual image, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F25hoBwk5pYaRplghSmkY%2Fpallet-process-p084-img03.png?alt=media)

posture.

Figure 7.35 Picking posture

**NOTICE** The J3 angle of the picking point must be greater than 0; otherwise, the acquired point cannot be saved.

2. Based on the box orientation, the recommended picking point posture (using the left or right pallet user coordinate system):

Box long side facing the workstation – Box short side facing the workstation –\
Picking point RZ: 90° Picking point RZ: 180°<br>

3. After the robot arm has moved into position, click the "Obtain" button to set the picking point.

In "2 Conveyors 2 Pallets" mode, picking/placing points for both conveyors must be set separately. During palletizing, boxes picked up from Conveyor 1 will only be stacked onto the left pallet, and boxes picked up from Conveyor 2 will only be stacked onto the right pallet. The same principle applies to depalletizing. Please set the points according to your on-site configuration.

![Official manual image, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK829HyhXq0jmzo3C2ibP%2Fpallet-process-p085-img02.jpg?alt=media)

![Official manual image, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNNeMqqOp8Eea6NxReXYV%2Fpallet-process-p085-img03.png?alt=media)

![Official manual image, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUz2tN5a22DBRSYGfLaN1%2Fpallet-process-p085-img04.png?alt=media)

Figure 7.36 Set picking point\_2 conveyors

#### 7.5.2 Layer transition point

Layer transition points are points that the robot arm passes through during the process of picking a box and placing it. They are generally used to control the robot's motion trajectory to avoid obstacles. They can be set either by "Auto-obtain" or "Custom".

Figure 7.37 Set layer transition point

####  **Custom (default)**

Check "Custom" (default) next to the layer transition point. After moving the robot arm to the desired position, click "Obtain" next to the transition point (e.g., T1) to obtain its position. Left and right transition points must be configured separately. Each side supports a minimum of 1 and a maximum of 5 transition points.

The coordinate values of the transition points displayed on the interface are based on the pallet coordinate system on the corresponding side (left/right).

In depalletizing mode, the order in which the transition points are added is opposite to the order in which the robot arm moves.

![Official manual image, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiGFyhHaTmoxeN6XmmhId%2Fpallet-process-p086-img02.png?alt=media)

![Official manual image, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv6PKElGc2SgJpO3FTzv7%2Fpallet-process-p086-img03.png?alt=media)

**NOTE** The height of the transition point set here is the height of the transition point corresponding to the first layer of boxes. During actual operation, the system automatically adjusts the height of the transition point based on the number of layers being palletized or depalletized.

If more than one transition point is set on one side, selecting any transition point will display a "Delete" button. Click it to delete the selected transition point.

Figure 7.38 Delete transition point

It is recommended to set two transition points per side: one outside the pallet and another inside the pallet, both positioned higher than the point above the picking point. Configure based on the actual scenario to ensure a smooth robot motion without collisions. The point settings vary slightly depending on the conveyor installation method, but the overall principle is the same. It is recommended to refer to the aforementioned 3D illustration for configuration.

####  **Auto-obtain**

First, go to "Workstation settings > Auto-Transition" page and activate the "Enable auto-transition points" function. The "Auto-obtain" option will then be displayed.

Checking "Auto-obtain" will clear all existing custom transition points.

**NOTE** The number of conveyors configured for auto-transition points must match the number of conveyors configured in the current project; otherwise, switching to the transition point mode will not be possible.

After switching to "Auto-obtain", the original transition point list is hidden, and the following page is displayed. Click the dropdown menu to select the layer. After a successful "Reachability check", layer transition points will be generated automatically.

Click "3D trajectory preview" to preview the motion trajectory for that layer (including the picking point, transition points, placement offset point, and placing point). Click the button again to hide the trajectory.

![Official manual image, source page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fs3HYs2dNwLYqcAzeNvyl%2Fpallet-process-p087-img02.png?alt=media)

Figure 7.39 Auto-obtain

####  **Fixed points**

The "Fixed points" function is available only when "Layer transition point" is set to "Custom". Click "Fixed points" to display the following page, where you can set fixed transition points for the left and right pallets.

Figure 7.40 Fixed points

**NOTE**

* Newly added transition points are unchecked by default.
* Checked transition points will not have their heights dynamically calculated based on layer height during script execution.
* The last transition point must be unfixed (i.e., grayed out and cannot be checked).

### 7.6 Check reachability

After configuring the palletizing project parameters, enter the project name and click "Reachability check" to verify that all required parameters have been set and that all points in the stacking pattern are reachable. After the reachability check passes, click "Save" to complete the palletizing project configuration.

Figure 7.41 Reachability check

![Official manual image, source page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp9Rdp5KvciZqLDqQFf57%2Fpallet-process-p088-img03.png?alt=media)

![Official manual image, source page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbMb2TrHJvS0N5cgDOeBZ%2Fpallet-process-p088-img04.jpg?alt=media)

## 8. Run and Monitor the Project

### 8.1 Robot warm-up

When the palletizing workstation is started for the first time, or after it has not been used for a long period since the last startup, before restarting it: first run the robot at low speed without a payload (i.e., without mounting an end effector such as a suction cup or gripper) through the recommended warm-up script (please contact technical support to obtain this warm-up script). After the robot has warmed up, proceed with other operations.

**NOTICE**

If the robot is set directly to 100% operating speed after startup, it may be damaged.

### 8.2 Run palletizing project

#### 8.2.1 Run via palletizing process package

Figure 8.1 Stop/Run button

 After creating a project, it will open by default, or you can open a project via "More projects". Click , the following prompt appears. You must first confirm that the actual number of boxes on the pallet matches the data shown in the prompt, then click "Confirm" to start the project. The initial palletizing/depalletizing direction is the pallet enabled on the process package home page.

![Official manual image, source page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBDO7YJiqLZcdWrqZ8UDs%2Fpallet-process-p089-img02.jpg?alt=media)

Figure 8.2 Pre-run prompt

* Click to stop the robot arm immediately.
* Click . If the robot arm is currently holding a box/interlayer, it will complete the placement and return to the safe home position before stopping. If the robot arm is not currently holding a box/interlayer, it will finish the current action (for example, if the robot arm is about to pick up a box/interlayer, it will first complete the pickup and placement actions) and return to the safe home position before stopping.

**NOTICE** If the project is stopped during palletizing (due to an alarm or manual stop), the workstation must be manually reset before restarting the project. The reset steps are as follows:

* If there is a box gripped by the suction cup, hold the box and manually release the suction cup, then place the box to a safe area.
* Use the jog function to move the robot arm to a safe position (the hover point that the arm first moves to after the project starts).

#### 8.2.2 Run via control panel buttons

After correctly configuring the palletizing workstation and creating the palletizing project, associate the palletizing project with the remote I/O as the running project, so that users can run the palletizing project via the control panel buttons.

1. Go to the "Monitor" page in DobotStudio Pro and check whether the DI/DO configurations of the controller are correct.

![Official manual image, source page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2PnysGOaRMs3liEm8fxC%2Fpallet-process-p090-img02.jpg?alt=media)

| <p><strong>Controller</strong><br><strong>DI/DO</strong></p> | **Function**               |
| ------------------------------------------------------------ | -------------------------- |
| DI\_7                                                        | Enable button              |
| DI\_11                                                       | Start button               |
| DI\_12                                                       | Stop / Soft stop button    |
| DI\_13                                                       | Reset button (clear alarm) |
| DO\_7                                                        | Enable status indicator    |
| DO\_11                                                       | Running status indicator   |
| DO\_12                                                       | Alarm status indicator     |
| DO\_13                                                       | Stop status indicator      |

Figure 8.3 Correct I/O configuration

2. If the I/O configuration is incorrect, click "Settings" to enter the "IO settings" tab and modify the "Feature configuration".

Figure 8.4 Feature configuration entry

3. After modifying the feature configuration, click "Save" to return to the I/O monitoring page.

Figure 8.5 Modify I/O configuration

![Official manual image, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLxuc8bpIg6JEWKeEAswd%2Fpallet-process-p091-img02.png?alt=media)

![Official manual image, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3Mh8B4o0nCUXomruvora%2Fpallet-process-p091-img03.jpg?alt=media)

![Official manual image, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvWDZMpQIHFJ1Ih3w832w%2Fpallet-process-p091-img04.png?alt=media)

**NOTICE** If DI\_12 is configured as "Stop", pressing the button labeled "Stop" on the palletizing workstation panel will immediately stop the robot arm. If DI\_12 is configured as "Universal DI", the button labeled "Stop" on the palletizing workstation panel will correspond to the "Soft stop" function.

4. Click "Remote Control" to navigate to the "Settings > Remote Control > I/O Remote Control" page in DobotStudio Pro. Select the desired palletizing project and click "Set as Default Operating Project" on the right.

Figure 8.6 Select project

5. Return to the DobotStudio Pro home page and check that the "Default I/O Project" is correct. Then, change the "I/O/Modbus Configuration" switch to "ON".

Figure 8.7 Enable I/O/Modbus configuration

![Official manual image, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FneW1gW07aynYhR01i3f2%2Fpallet-process-p092-img02.jpg?alt=media)

![Official manual image, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FahvIat8oi1tNn77bdPSr%2Fpallet-process-p092-img03.jpg?alt=media)

![Official manual image, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3RVF5VhGcSubCgw8kCoj%2Fpallet-process-p092-img04.png?alt=media)

6. Power on the palletizing workstation, then press the corresponding buttons on the palletizing workstation in the following order to run the palletizing project:
   * ① Press the "Power\_up" button. Wait for the "Power\_up" button indicator to light up, indicating that the robot arm has been successfully enabled.
   * ② Press the "Start" button. Wait for the "Start" indicator to light up, indicating that the palletizing project has begun running.

Figure 8.8 Workstation control buttons

### 8.3 Real-time project monitoring

Figure 8.9 Palletizing monitoring page

| **No.** | **Parameter**           | **Description**                                                                                                                                                                                                                                                                                                              |
| ------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ①       | <p>Capacity<br>data</p> | <p>Displays the real-time production data for the palletizing<br>workstation, including total pallets/boxes, working time, and<br>production tasks. It supports both production task<br>configuration and production data statistics. Click "Clear" to<br>clear all production data except for production task settings.</p> |

![Official manual image, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9fRZjxVKOeMaEUnv0mKo%2Fpallet-process-p093-img02.png?alt=media)

![Official manual image, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzJ4U7lMBfqV9jgTtRc8m%2Fpallet-process-p093-img03.jpg?alt=media)

| **No.** | **Parameter**                     | **Description**                                                                                                                                                                                                                                                     |
| ------- | --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|         |                                   | See"Capacity data"for details.                                                                                                                                                                                                                                      |
| ②       | <p>Interlayer<br>count</p>        | <p>For projects with interlayers, here displays the number of<br>interlayers. Click "Edit" to modify based on the actual<br>interlayer count.</p>                                                                                                                   |
| ③       | <p>Pallet<br>monitor</p>          | See"Monitor pallet data" for details.                                                                                                                                                                                                                               |
| ④       | Running log                       | <p>Displays user print messages, error messages, and custom<br>errors generated during palletizing operations. For details on<br>error messages, see"Troubleshooting". Click "Clear" to clear<br>the running logs.</p>                                              |
| ⑤       | <p>Project<br>information</p>     | The name and type of the currently open project.                                                                                                                                                                                                                    |
| ⑥       | Position                          | <p>Enable the robot arm, click the "Position" button to jog the<br>robot arm, or long-press the "Safe Home" button to return the<br>arm to the workstation's safe home position.</p>                                                                                |
| ⑦       | I/O monitor                       | <p>Click to open the I/O monitoring window to view theI/O<br>signals configured for the palletizing workstation. DO signals<br>appear as ON/OFF switches, which correspond to high/low<br>levels of the signal. The DO state can be adjusted via the<br>switch.</p> |
| ⑧       | <p>Parameter<br>configuration</p> | <p>Manually control the lifting column and suction cup, as well as<br>set debugging-related parameters. See"Parameter<br>configuration" for details.</p>                                                                                                            |
| ⑨       | Edit                              | <p>Enter the palletizing project configuration page to modify<br>parameters of the current project.</p>                                                                                                                                                             |
| ⑩       | <p>Stop / Soft<br>stop / Run</p>  | <p>Run the palletizing project, safely pause it, or stop it entirely.<br>See"Run via palletizing process package" for details.</p>                                                                                                                                  |

#### 8.3.1 Capacity data

Figure 8.10 Capacity data

| **Parameter**                     | **Description**                                                                                     |
| --------------------------------- | --------------------------------------------------------------------------------------------------- |
| <p>Total number of<br>pallets</p> | <p>The total number of pallets that have been palletized or<br>depalletized by the workstation.</p> |
| Total number of                   | The total number of boxes that have been palletized or                                              |

| **Parameter**   | **Description**                                                                                                                                                                                                                                     |
| --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| boxes           | <p>depalletized by the workstation.<br>When the actual number of boxes placed is a multiple of the<br>number of placement cycles, click<br>and enter the<br>multiplier. The total number of boxes = Number of placement<br>cycles × Multiplier.</p> |
| Running time    | <p>The duration for which the current workstation has been<br>running the project.</p>                                                                                                                                                              |
| Production data | <p>Click the "Production data" button to view production statistics<br>for the current workstation. Supports conditional filtering and<br>data export.</p>                                                                                          |
| Production task | <p>Displays the configured production task (e.g., current quantity<br>and target quantity of boxes or pallets). If no production task<br>is set, "Not set" is displayed.</p>                                                                        |
| Clear           | Clears all production data except production tasks.                                                                                                                                                                                                 |

#### Set production task

Click the "Production task" button to open the following settings window. Only one option can be enabled (either "Pallet" or "Box"). The target value can only be a non-zero integer; otherwise, it cannot be saved.

If the production task is completed (current total ≥ target), the robot arm stops moving and returns to the safehome position. When you click "Start" again, the current task count resets to zero and a new accumulation begins.

If the target is not reached and the project is paused or stopped midway, the current task

count will continue to accumulate when you click "Start" again.

Figure 8.11 Set production task

![Official manual image, source page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvkh5fyMfWU4aGY5562su%2Fpallet-process-p095-img03.png?alt=media)

**NOTE**

* During project execution, production tasks cannot be set or modified. The "Production task" button is not displayed when no project is open or in Demo mode.
* In single-pick scenarios, the production task is complete when the current total = target.
* In multi-pick scenarios, the current total is allowed to exceed the target, and the production task is based on the exceeded value.

#### Production data statistics

Click the "Production data" button to view the production data of the palletizing workstation after normal operation (regardless of project type, stacking pattern type, or depalletizing/palletizing mode). The most recent month's data is displayed by default. You can filter by date or project name, and query up to 180 days of data.

Figure 8.12 Production data statistics

| **Parameter**                     | **Description**                                                                                                                                                                                                                                                           |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <p>Total Pallets<br>Completed</p> | <p>The total pallet count under the current filter criteria, unit: pcs.<br><br>**Palletizing:**Counted once after a complete palletizing<br>cycle.<br><br>**Depalletizing:**Counted once after a complete<br>depalletizing cycle, regardless of left or right side.</p> |
| <p>Total Boxes<br>Completed</p>   | <p>The total box count under the current filter criteria, unit: pcs.<br><br>**Palletizing:**Counted once after a complete palletizing<br>cycle.<br><br>**Depalletizing:**Counted once after a complete<br>depalletizing cycle, regardless of left or right side.</p>    |
| <p>Total Production<br>Time</p>   | <p>The duration of projects currently running under the selected<br>criteria, in hours:minutes:seconds (hh<span data-gb-custom-inline data-tag="emoji" data-code="1f1f2-1f1f2">🇲🇲</span>ss). Paused duration<br>is not included.</p>                                    |
| Export                            | <p>Click "Export" to export the currently displayed data as an<br>".xlsx" file. The file name format is "Palletizing data + Export<br>date (YYYYMMDD)".</p>                                                                                                               |

![Official manual image, source page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F506QN7NMMNmwxBDWN7p5%2Fpallet-process-p096-img02.png?alt=media)

**NOTE**

* During project execution, the "Production data" button cannot be clicked.
* Data in Demo mode is not included in the statistics.
* Production data is stored in the controller. Before upgrading or downgrading the controller version, back up the data in advance; otherwise, there is a risk of data loss.

#### 8.3.2 Monitor pallet data

Figure 8.13 Pallet monitoring

If "1 Conveyor 1 Pallet" was selected as the palletizing mode when creating the project, the unselected pallet will be locked in a disabled status and cannot be enabled or modified.

| **No.** | **Parameter**                     | **Description**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ------- | --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| a       | <p>Pallet ON/OFF<br>switch</p>    | <p>Enable or disable the left/right pallet as needed. The<br>workstation will only perform palletizing on the enabled<br>pallet.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| b       | <p>Pallet status<br>indicator</p> | <p>Indicates the current status of the pallet via color and text<br>(when the pallet is disabled, no color or text is displayed).<br>See"Pallet status description" for details.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| c       | Pallet data                       | <p>During operation, the system provides real-time statistics<br>on the number of boxes that have been palletized or<br>depalletized, including the exact layer and position of each<br>box. The current pallet data is updated each time a box is<br>successfully placed. For example, if the 3rd box on the 1st<br>layer is currently being placed, the interface will display<br>Layer 1 with 2 boxes already placed. After the current box<br>is placed, the display will update to Layer 1 with 3 boxes.<br>If the actual number of boxes already on the pallet differs<br>from the number displayed on this page, click the "Modify"<br>button to manually adjust the data to match the actual<br>count to avoid errors during palletizing.</p> |

![Official manual image, source page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNvHu28o590RPO0cXEDkY%2Fpallet-process-p097-img02.jpg?alt=media)

#### 8.3.3 Pallet status description

Figure 8.1 Pallet status description

| **Scenario** | **Color** | **Text**                                  | **Scenario** | **Color** | **Text**                                  |
| ------------ | --------- | ----------------------------------------- | ------------ | --------- | ----------------------------------------- |
|              |           | <p>Pallet not<br>detected</p>             |              |           | <p>Pallet not<br>detected</p>             |
|              | Yellow    | <p>Pallet detected<br>but not enabled</p> |              | Yellow    | <p>Pallet detected<br>but not enabled</p> |
| Plltii       |           | Idle                                      | Dlltii       |           | Idle                                      |
| aezng        |           | Pallet full                               | epaezng      |           | Pallet empty                              |
|              | Green     | <p>Palletizing in<br>progress</p>         |              | Green     | <p>Depalletizing in<br>progress</p>       |
|              | Red       | <p>Error (see<br>"Troubleshooting")</p>   |              | Red       | <p>Error (see<br>"Troubleshooting")</p>   |

#### 8.3.4 Parameter configuration

#### Basic configuration

Figure 8.14 Parameter configuration (Basic configuration)

#### ① **Lifting column debugging**

If the lifting column is not connected, click to view and modify the IP and port settings for the lifting column you want to connect. Typically, the default IP of the lifting column matches the preset IP in the palletizing process package when the workstation is shipped, so no changes are needed. However, if you’ve modified the lifting column’s IP or are using a different lifting column, you’ll need to update the IP and port here.

![Official manual image, source page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0zR70KoJMN0r8zpxByG1%2Fpallet-process-p098-img02.jpg?alt=media)

Figure 8.15 Lifting column IP

Click "Connect", the system will start connecting to the lifting column. Once connected, the current position of the lifting column (relative to the initial position, with a maximum height of 900mm) will be displayed. You can manually control the lifting column by longpressing the "Down" or "Up" buttons.

You can also enter a target position and then long-press the "Run to" button to move the lifting column to the specified position (a prompt will appear once the target position is reached). If an unexpected situation occurs during movement, releasing the "Run to" button can stop the lifting column.

After debugging, click "Disconnect" to disconnect from the lifting column.

#### ② **Pneumatic suction cup debugging**

You can click "Suction" or "Release" to change the status of the suction cup for debugging.

#### ③ **Basic debugging parameter settings**

* **Infeed Wait Time:** The time to wait for the robot arm to pick up material after the infeed signal is triggered. Unit: ms. Range: (0, 3600000]. Default: 0.
* **Suction Wait Time:** The time to wait for the suction cup to securely pick up the box. Reducing the wait time can increase palletizing speed, but it may cause the box to be insecurely gripped. Adjust according to the actual situation. Unit: ms. Range: (0, 5000]. Default: 1500.
* **Release Wait Time:** The time to wait for the suction cup to place the box. Reducing the wait time can increase palletizing speed, but it may cause the robot arm to drag the box when moving away, affecting the palletizing result. Adjust according to the actual situation. Unit: ms. Range: (0, 5000]. Default: 1500.
* **Safe Picking Height:** The vertical height the robot arm moves to before and after picking up a box. Unit: mm. Range: (0,1000]. Default: 300.
* **Drop Detection Delay:** The time interval between two drop detections, used to confirm whether a box drop has occurred. Unit: ms. Range: (0, 3600000]. Default: 0.
* **Drop Detection:** This function can be enabled only after the "Drop Detection Signal" option is checked in the palletizing workstation's I/O signals. Once enabled, if a box drop is detected during palletizing, the project will trigger an alarm and stop.

![Official manual image, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUu2LP0MlitRrPG48GWvu%2Fpallet-process-p099-img02.jpg?alt=media)

#### Advanced configuration

8.16 Parameter configuration (Advanced configuration)

**NOTE** For double pallets, the compensation values for the left and right pallets must be set separately.

#### ① **Z-axis height compensation**

During palletizing, discrepancies in the actual box sizes or deformation of lower layers due to compression can lead to significant differences between the actual height and the calculated theoretical height after stacking several layers, impacting the palletizing quality.

To address this, identify the layer where the significant differences occurs. If the actual height of that layer is lower than the theoretical height, choose "Downward"; if it is higher, choose "Upward". Then calculate the compensation height (maximum: 200mm) using the following formula:

_Compensation height = Theoretical box height × Current layer count − Actual stack height_

Figure 8.17 Z-axis height compensation

In the actual palletizing process, as shown in the figure, if height deviation starts from

![Official manual image, source page 100](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPtP93wPHlL1jBdCbpbsC%2Fpallet-process-p100-img02.jpg?alt=media)

![Official manual image, source page 100](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fps1yi2t3zTlmRptvhHTi%2Fpallet-process-p100-img03.jpg?alt=media)

the third layer, you should begin compensating from that layer. If, after adjusting and continuing, further height deviations occur in the upper layers, you need to add the required compensation for each layer to form a new compensation value.

#### ② **Home safety transition point**

The transition points that the robot arm passes through when resetting in the stopped state. Disabled by default. Once enabled, up to 3 points can be set per pallet side. The J1 range for the left reset safety transition point is \[90°, 180°], and the J1 range for the right reset safety transition point is \[0°, 90°].

Whether the robot passes through the left or right transition point is determined by the current position of the robot arm's J1 axis when the project is running. When the J1 axis is at the right rear (-80°, -90°) or left rear (260°, -270°), automatic homing is prohibited when safety protection is triggered.

**NOTE** The Home Safety Transition Point is effective only for the current project.

#### "2 Conveyors 2 Pallets" configuration

Figure 8.18 "2 Conveyors 2 Pallets" debugging

This tab is displayed only when the current project is in "2 Conveyors 2 Pallets" mode.

First, you need to select the specific palletizing mode based on the actual conditions of the production line:

####  **Alternate palletizing on left and right pallets**

In this mode, the workstation alternately palletizes the left and right pallets, following the pattern "Left box 1 => Right box 1 => Left box 2 => Right box 2".

![Official manual image, source page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F47Likq547MqZ73JxUGnn%2Fpallet-process-p101-img02.png?alt=media)

If the system finishes palletizing Left box 1 and the right conveyor’s feeding signal is inactive while the left conveyor’s signal is active, the workstation will continue palletizing on the left pallet until the right conveyor’s signal is activated, and vice versa.

This mode is suitable for scenarios where the production capacities of both conveyors are similar, and the box sizes are comparable. If the production capacities or box sizes differ too much, it may lead to a significant height difference between the boxes on the left and right pallets during palletizing. This could result in frequent raising and lowering of the lifting column, slowing down the palletizing speed and potentially damaging the lifting column.

####  **Prioritize lower-level palletizing**

This mode calculates the height difference between the boxes on the left and right pallets in real time on the basis of the alternating palletizing mode. When the height difference reaches or exceeds a trigger value (h1), the workstation enters one-sided palletizing mode, continuing to palletize only on the side with the lower height until the height difference falls below the ending value (h2), and then resumes the alternating palletizing mode.

**NOTE** When the workstation is in one-sided palletizing mode, it may cause material to accumulate on the other side. Users should set up a buffer zone on the conveyor based on the actual situation of the production line.

Figure 8.19 Settings for Prioritize lower-level palletizing

* **Trigger one-sided palletizing height difference (h1)** : When the height difference between the two sides is greater than or equal to this value, one-sided palletizing mode is activated. Range: \[0, 2200].
* **End one-sided palletizing height difference (h2)** : When the height difference between the two sides is less than this value, one-sided palletizing mode ends. Range: \[0, 2200].
* **Pause left/right pallet line function** : When the corresponding DI is ON, the workstation will pause palletizing on that side and only continue palletizing on the other side, ignoring the height difference. When both DI signals are ON, the workstation will stop operating. When both DI signals are OFF, the workstation

![Official manual image, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fs45DaaLlXUMBKlnLG5vA%2Fpallet-process-p102-img02.png?alt=media)

will resume normal palletizing operations.

The line pause function is only effective in "Prioritize lower-level palletizing" mode and can be configured to be triggered by either "DI Trigger" or "Virtual DI":

* **DI Trigger:** Triggered by a physical DI. The user needs to connect a trigger source, such as a toggle switch, to the corresponding DI on the controller.
* **Virtual DI:** Triggered by virtual DI from the control software. Once configured as virtual DI, the corresponding DI on the I/O monitoring page will appear as ON/OFF button (as shown in the figure below). The user can only control the DI status through the DobotStudio Pro software, and the real status of the corresponding DI interface on the controller will be ignored.

Figure 8.20 Virtual DI

Typical application scenarios for the line pause function (using a physical switch to trigger the DI as an example):

* **Scenario 1:**

If the left pallet’s production line experiences an issue and no material is fed, the workstation will continue palletizing on the right pallet. If no action is taken, once the right pallet reaches a certain height, the height difference will trigger one-sided palletizing, causing the workstation to stop and wait for material from the left conveyor. In this case, the operator should press the left line’s pause switch to have the workstation palletize only on the right pallet. Once the left line is back to normal, the operator can reset the switch.

* **Scenario 2:**

When replacing the left pallet, only a few boxes remain on the right pallet to complete palletizing. If no action is taken, the height difference will trigger one-sided palletizing, causing the workstation to ignore the nearly completed right pallet and continue palletizing on the new left pallet. To prevent this, the operator can press the left line’s pause switch during pallet replacement, allowing the workstation to first complete the right palletizing. Once the right palletizing is finished, the operator can reset the switch.

![Official manual image, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcsexkyEsBlSzaeBQIog6%2Fpallet-process-p103-img02.png?alt=media)

#### Motion parameter

Figure 8.21 Motion parameter

* Set the speed percentage for robot arm motion. The speeds with and without a box must be set separately. The system is configured with default parameters at the factory; no modification is required unless there are special requirements.
* The "Move before picking interlayer" and "Move after picking interlayer" parameters are disabled by default. Once checked, you can customize the safe home position speed during interlayer pickup and the safe home position speed after interlayer pickup.
* When "Place motion" is checked, the motion speed from the transition point to the placing point defaults to the speed set for "With box" above. You can also adjust it as needed.

**NOTICE** After enabling the custom placement speed, the CR30H series robot arm will not enable optimal trajectory time optimization.

![Official manual image, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYCW4iTcebd9PNPf9VxBY%2Fpallet-process-p104-img02.png?alt=media)

### 8.4 Manage palletizing project

Figure 8.22 Manage project

Click "More projects" on the palletizing monitoring page to open the project list.

Figure 8.23 Project list

| **No.** | **Description**                                                                                                                  |
| ------- | -------------------------------------------------------------------------------------------------------------------------------- |
| ①       | <p>Click<br>next to the project name to rename the project.</p>                                                                  |
| ②       | Filter the projects displayed in the list by project type.                                                                       |
| ③       | <p>Select a project and click "Save to product management" to store the current<br>palletizing project toproduct management.</p> |
| ④       | Select a project and click "Delete" to delete the selected project.                                                              |
| ⑤       | Select a project and click "Copy" to generate a copy of the selected project.                                                    |
| ⑥       | <p>Select a project and click "Edit" to modify the configuration of the selected<br>project.</p>                                 |
| ⑦       | Click "New" to create a new palletizing project.                                                                                 |
| ⑧       | <p>Select a project and click "Export" to export the selected project in "json"<br>format to your local system.</p>              |
| ⑨       | <p>Click "Import" to import a palletizing project in "json" format from your local<br>system.</p>                                |
| ⑩       | <p>Select a project and click "Open project" to set the selected project as the<br>current project.</p>                          |
| ⑪       | <p>Select a project and click "Virtual simulation"to run a virtual simulation of that<br>project.</p>                            |

![Official manual image, source page 105](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAVQzZbFo3UqixcvrPNGo%2Fpallet-process-p105-img02.jpg?alt=media)

![Official manual image, source page 105](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNrSJfE7KMK6bPQt61Wa0%2Fpallet-process-p105-img03.jpg?alt=media)

### 8.5 Virtual simulation

Virtual simulation is available only when the robot arm is in the disabled status. You can turn off the "Enable" switch on the DobotStudio Pro homepage.

Figure 8.24 Enable switch

On the project list page, click the "Simulation" button, and the following prompt will appear:

Figure 8.25 Virtual simulation prompt

Click "Start Simulation" to enter the simulation page. Once entered, the simulation project will automatically start running.

Figure 8.26 Virtual simulation

| <p><strong>No.</strong><br><strong>Description</strong></p> |
| ----------------------------------------------------------- |

① Click "Hide Panel" to collapse the control panel, the button will then change

![Official manual image, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhZ1j7kKikRoFOM69rqt1%2Fpallet-process-p106-img02.jpg?alt=media)

![Official manual image, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoiVnmiLWPQnV0UGVVfny%2Fpallet-process-p106-img03.png?alt=media)

![Official manual image, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyBG7IiUNtATtWx7EXw56%2Fpallet-process-p106-img04.jpg?alt=media)

| **No.** | **Description**                                                                                                                                                                                                                                                                                  |
| ------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
|         | to "Show Panel".                                                                                                                                                                                                                                                                                 |
| ②       | <p>You can pause, stop, or restart the project. The number below the pause<br>button indicates the current simulation runtime. After stopping the simulation,<br>"Restart" and "Quit Simulation" buttons will appear. Click to either restart the<br>simulation or exit the simulation page.</p> |
| ③       | Display the total number and rate of palletizing.                                                                                                                                                                                                                                                |
| ④       | <p>Display the current stacking layer and the number of boxes in the current<br>layer. While stopped, click "Edit" to input the desired starting layer and<br>number of boxes per layer. Click "Confirm and Start Simulation" to begin the<br>simulation.</p>                                    |

If a collision or other abnormal situation occurs during the simulation, the project will stop, and a pop-up window will inform you of the issue.

Figure 8.27 Simulation error

* Click "Configure" to go to the palletizing project configuration page. Adjust the configuration based on the exceptions encountered during simulation.
* Click "Not Configure" or the "X" at the top right to close the pop-up window, stay on the simulation page and check the status of the 3D model when the anomaly occurs. After an error, a "Restart" button will appear on the control panel, allowing you to restart the palletizing project from the beginning.

**NOTE**

* The "Virtual Simulation" function uses the robot's real controller, and the simulation speed cannot be accelerated.
* You can also perform simulation operations via the web at: http://8.129.2.35:9702.

![Official manual image, source page 107](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7mdhz0hBrxF9980qbF4K%2Fpallet-process-p107-img02.png?alt=media)

## 9. Troubleshooting

### 9.1 Communication failure between robot and lifting axis

| Field          | Official guidance                                          |
| -------------- | ---------------------------------------------------------- |
| Error code     | 1                                                          |
| Cause          | Communication between the robot and lifting column failed. |
| Project status | Stop.                                                      |

1. Restart the palletizing workstation.
2. If the error persists, check the robot-controller and servo-drive RS-485 cables for secure connections.
3. If these checks do not resolve the error, contact DOBOT technical support.

![Official robot-controller RS-485 cable connection, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlF1uf6KpHsEopw0ufD9C%2Fpallet-process-p108-img02.jpg?alt=media)

![Official servo-drive RS-485 connection, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHzBxsPNndsAhsXF2vSEC%2Fpallet-process-p109-img02.jpg?alt=media)

![Official RS-485 wiring reference, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC89f4Mugy23aDXT7wnb6%2Fpallet-process-p109-img03.png?alt=media)

### 9.2 Point unreachable

| Field           | Official guidance                                                                           |
| --------------- | ------------------------------------------------------------------------------------------- |
| Error code      | 2                                                                                           |
| Example message | “Layer 2, placing point for box 3 is unreachable. Please check the stack pattern settings.” |
| Cause           | The target point has no inverse-kinematics solution.                                        |
| Project status  | Stop.                                                                                       |
| Solution        | Modify the project configuration according to the error message.                            |

### 9.3 Pallet missing detected

| Field          | Official guidance                                                          |
| -------------- | -------------------------------------------------------------------------- |
| Error code     | 3                                                                          |
| Cause          | The pallet signal has been lost for more than 20 seconds during operation. |
| Project status | Stop.                                                                      |

1. Put the pallet in its correct position.
2. On the palletizing monitoring page, open the I/O monitoring window. Block each pallet-position sensor by hand and check that the corresponding I/O indicator turns green. If a sensor does not respond, contact DOBOT technical support.

![Official pallet-detection I/O reference, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXkXiZx8JbRy94MYDBxjG%2Fpallet-process-p110-img02.png?alt=media)

![Official pallet sensor location, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLSK1Y0kWyF8v99clmQNJ%2Fpallet-process-p110-img03.png?alt=media)

### 9.4 Height limit function enabled, both conveyors stopped

| **Error message**  | <p>Both production lines and their corresponding pallets have<br>been paused by DI trigger. To resume normal operation, please<br>adjust the DI status.</p> |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Error code**     | 4                                                                                                                                                           |
| **Cause**          | <p>In "2 Conveyors 2 Pallets" mode, with the height difference limit<br>function enabled, signals of both conveyors are simultaneously<br>disabled.</p>     |
| **Project status** | Pause                                                                                                                                                       |

Change the status of the corresponding DI based on the actual **Solution** production line status. See "2 Conveyors 2 Pallets" Configuration for details.

### 9.5 Box dropped

| **Error message**  | Box dropped.                                                                                                                                                                          |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Error code**     | 5                                                                                                                                                                                     |
| **Cause**          | During operation, a box fell off from the suction cup.                                                                                                                                |
| **Project status** | Stop                                                                                                                                                                                  |
| **Solution**       | <p>①<br>Adjust the suction cup or pneumatic equipment to increase<br>the suction cup airflow.<br>②<br>Adjust the picking point so that the suction cup and the box<br>fit better.</p> |

### 9.6 Box not released

| **Error message**  | The box is not released.                                                                                    |
| ------------------ | ----------------------------------------------------------------------------------------------------------- |
| **Error code**     | 6                                                                                                           |
| **Cause**          | <p>When starting the process package, a box was detected on the<br>suction cup.</p>                         |
| **Project status** | Pause                                                                                                       |
| **Solution**       | <p>Manually release the box via the Parameter Configuration<br>page, then continue running the project.</p> |

### 9.7 Interlayer empty/full

| **Error message**  | Insufficient interlayers / Interlayer placement area is full.                                                                                    |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Error code**     | 7                                                                                                                                                |
| **Cause**          | <p>①<br>During palletizing, the interlayer storage location is empty.<br>②<br>During depalletizing, the interlayer storage location is full.</p> |
| **Project status** | Pause                                                                                                                                            |

**Solution**

* ① During palletizing, replenish the interlayers and continue running.
* ② During depalletizing, remove the interlayers and continue running.

### 9.8 Modbus communication creation failed, check Modbus address

| **Error message**  | <p>Failed to create Modbus communication, please check the<br>Modbus address.</p>                        |
| ------------------ | -------------------------------------------------------------------------------------------------------- |
| **Error code**     | 8                                                                                                        |
| **Cause**          | The robot failed to create the Modbus connection.                                                        |
| **Project status** | Stop                                                                                                     |
|                    | <p>①<br>Restart the robot controller.</p>                                                                |
| **Solution**       | <p>②<br>Check if the IP of the ModbusCreate command in the project<br>script matches the robot's IP.</p> |

### 9.9 Excessive lifting column movement count

| **Error message**  | <p>The lifting column has exceeded the limit of 35 lifts per hour.<br>Please stop for 30 minutes before resuming operation;<br>otherwise, there is a risk of burning out the lifting column.</p> |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Error code**     | 9                                                                                                                                                                                                |
| **Cause**          | The lifting column has been operating too frequently.                                                                                                                                            |
| **Project status** | Stop                                                                                                                                                                                             |
|                    | <p>①<br>Stop the project for 30 minutes before resuming.</p>                                                                                                                                     |
| **Solution**       | <p>②<br>Refer to"2 Conveyors 2 Pallets"Configuration to set the<br>"Prioritize lower-level palletizing" function to avoid triggering<br>this alarm.</p>                                          |

### 9.10 Abnormal lifting column status

| **Error message**  | Abnormal state of the lifting column.                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------- |
| **Error code**     | 12                                                                                                                           |
| **Cause**          | <p>Communication between the robot and the lifting column is<br>normal, but the lifting column is not working properly.</p>  |
| **Project status** | Stop                                                                                                                         |
| **Solution**       | <p>Try restarting the workstation. If the error persists, please<br>contact DOBOT technical support for troubleshooting.</p> |

### 9.11 No pallet enabled

| **Error message**  | No pallet enabled.                                                                                                             |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| **Error code**     | 14                                                                                                                             |
| **Cause**          | <p>All pallet enable buttons on the process package interface are<br>disabled.</p>                                             |
| **Project status** | Stop                                                                                                                           |
| **Solution**       | <p>Enable any pallet button on the monitoring interface. For pallet<br>button signal details, refer to the"Pallet signal".</p> |

### 9.12 Failed to read the lifting column position

| **Error message**  | Failed to read the lifting column position.                     |
| ------------------ | --------------------------------------------------------------- |
| **Error code**     | 15                                                              |
| **Cause**          | The robot cannot obtain the lifting column position.            |
| **Project status** | Stop                                                            |
| **Solution**       | Refer to"Communication failure between robot and lifting axis". |

### 9.13 Queue timeout

| **Error message**  | <p>The log will output the specific reason, such as: Queue lock<br>timeout.</p>                                                                                                                               |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Error code**     | 16                                                                                                                                                                                                            |
| **Cause**          | <p>The queue has been occupied for a long time, indicating<br>coroutine contention or a deadlock.</p>                                                                                                         |
| **Project status** | Stop                                                                                                                                                                                                          |
| **Solution**       | <p>Restart the project. If the issue occurs repeatedly, check<br>whether the point queue enqueue/dequeue operations in the<br>palletizing script are abnormal (deadlock or long-term lock<br>occupation).</p> |

### 9.14 Work data error

| **Error message**  | <p>The log will specify the exact exception item, such as: ToolData<br>is wrong.</p>                                                                                                                                                           |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Error code**     | 17                                                                                                                                                                                                                                             |
| **Cause**          | <p>Internal work data exception during operation: invalid<br>configuration parameters, state machine transition error, empty<br>data / incorrect data type, Modbus write failure, box count<br>exception, etc.</p>                             |
| **Project status** | Stop                                                                                                                                                                                                                                           |
| **Solution**       | <p>Check the corresponding configuration based on the specific<br>log message (palletizing mode, tool data, suction cup type,<br>conveyor, signal type, box count, etc.). If necessary, redeploy<br>the project or restart the controller.</p> |

### 9.15 Interlayer quantity warning

| **Error message**  | <p>The interlayer quantity will fall below the warning threshold X (X<br>is the configuredInterlayer stock alert threshold).</p> |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------- |
| **Error code**     | 18                                                                                                                               |
| **Cause**          | <p>Remaining interlayers ≤ the configured interlayer stock alert<br>threshold.</p>                                               |
| **Project status** | Continue running                                                                                                                 |
| **Solution**       | Replenish interlayers promptly or adjust theinterlayer stock                                                                     |

alert threshold in the interlayer settings.

### 9.16 Robot home position return error

| **Error message**  | Robot home position return error.                       |
| ------------------ | ------------------------------------------------------- |
| **Error code**     | 19                                                      |
| **Cause**          | Robot joint J1 is less than -80° or greater than 260°.  |
| **Project status** | Stop                                                    |
| **Solution**       | Jog robot joint J1 to within the range of -80° to 260°. |

### 9.17 Project suction cup type inconsistent with workstation configuration

| **Error message**  | <p>Project suction cup type is inconsistent with the workstation<br>configuration.</p>                                             |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| **Error code**     | 20                                                                                                                                 |
| **Cause**          | <p>The suction cup type in the project is inconsistent with the<br>suction cup type configured for the workstation.</p>            |
| **Project status** | Stop                                                                                                                               |
| **Solution**       | <p>Change the workstation's suction cup type to match the suction<br>cup type of the remote default startup project, and save.</p> |

### 9.18 Material not released

| **Error message**  | Material not released.                                                                         |
| ------------------ | ---------------------------------------------------------------------------------------------- |
| **Error code**     | 21                                                                                             |
| **Cause**          | <p>After the suction cup is turned off, the box or interlayer is not<br>properly released.</p> |
| **Project status** | Stop                                                                                           |
|                    | <p>①<br>Enable the vacuum release function.</p>                                                |
| **Solution**       | <p>②<br>Increase the release wait time.</p>                                                    |
|                    | <p>③<br>Reduce the placement speed.</p>                                                        |

### 9.19 Stacking pattern offset

The entire layer of the pallet is tilted as a whole, but the boxes\
remain parallel to each other.\
Scenario 1\
The user coordinate system (or pallet coordinate system) has a\
rotation angle.\
Cause<br>

Each box is tilted, forming a zigzag arrangement.\
Scenario 2\
The tool coordinate system (TCP) has a rotation angle.\
Cause<br>

![Official manual image, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBeC8FxJAkzTG7zvsK2pE%2Fpallet-process-p116-img02.jpg?alt=media)

![Official manual image, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhrapC3r7uWW09BFRavgO%2Fpallet-process-p116-img03.jpg?alt=media)

![Official manual image, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwfKyYUCVC0xhYxohXJD4%2Fpallet-process-p116-img04.jpg?alt=media)

![Official manual image, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fwe5YbUVBmycFoBPAktUu%2Fpallet-process-p116-img05.jpg?alt=media)

## Appendix A Register Address Definitions and Descriptions

This section provides the IP address and port number of the controller, along with the definitions of relevant register addresses, enabling users to perform advanced configurations.

* **Left Pallet Register Address Definitions:**

| **Address** | **Description**                                                              | **Val**                 | **ue definition**                                                                                                           |
| ----------- | ---------------------------------------------------------------------------- | ----------------------- | --------------------------------------------------------------------------------------------------------------------------- |
|             |                                                                              | <p><br></p>           | <p>0: Pallet not detected<br>1: Pallet detected but not<br>enabled</p>                                                      |
| 5000        | Palletizing status                                                           | <p><br><br><br></p> | <p>2: Palletizing in progress<br>3: Pallet full<br>4: Error (box dropped, pallet<br>lost during palletizing)<br>5: Idle</p> |
| 5002        | Current palletizing layer                                                    | --                      |                                                                                                                             |
| 5003        | <p>Remaining boxes in current<br>layer (Index)</p>                           | --                      |                                                                                                                             |
| 5007        | Enable pallet                                                                | --                      |                                                                                                                             |
| 5010        | Next box count                                                               | --                      |                                                                                                                             |
| 5020        | <p>Theoretical maximum box<br>index from First layer to<br>Current layer</p> | --                      |                                                                                                                             |
| 5022        | <p>Additional box count for<br>dual pick-and-place mode</p>                  | --                      |                                                                                                                             |
| 5024        | Interlayer count                                                             | --                      |                                                                                                                             |
| 5026        | Working mode                                                                 | <p><br></p>           | <p>1: Palletizing<br>2: Depalletizing</p>                                                                                   |
| 5028        | Conveyor direction                                                           | Re                      | ad-only                                                                                                                     |
| 5029        | Pallet direction                                                             | <p>Us<br><br></p>     | <p>ed in Demo mode:<br>0: Left pallet<br>1: Right pallet</p>                                                                |

| **Address** | **Description**                                                           | **Value definition**                                                                     |
| ----------- | ------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| 5037        | <p>Pallet direction of last<br>completed<br>palletizing/depalletizing</p> | <p>Used in Demo mode:<br><br>0: Idle<br><br>1: Left pallet<br><br>2: Right pallet</p> |
| 5038        | <p>Current count in current<br>layer</p>                                  | --                                                                                       |
| 5041        | <p>Manual pallet placement<br>stop flag</p>                               | <p><br>0: Not stopped<br><br>1: Stopped</p>                                            |

####  **Right Pallet Register Address Definitions:**

| **Address** | **Description**                                                              | **Val**                           | **ue definition**                                                                                                                                                                              |
| ----------- | ---------------------------------------------------------------------------- | --------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 5001        | Palletizing status                                                           | <p><br><br><br><br><br></p> | <p>0: Pallet not detected<br>1: Pallet detected but not<br>enabled<br>2: Palletizing in progress<br>3: Pallet full<br>4: Error (box dropped, pallet<br>lost during palletizing)<br>5: Idle</p> |
| 5004        | Current palletizing layer                                                    | --                                |                                                                                                                                                                                                |
| 5005        | <p>Remaining boxes in current<br>layer (Index)</p>                           | --                                |                                                                                                                                                                                                |
| 5009        | Enable pallet                                                                | --                                |                                                                                                                                                                                                |
| 5011        | Next box count                                                               | --                                |                                                                                                                                                                                                |
| 5021        | <p>Theoretical maximum box<br>index from First layer to<br>Current layer</p> | --                                |                                                                                                                                                                                                |
| 5023        | <p>Additional box count for<br>dual pick-and-place mode</p>                  | --                                |                                                                                                                                                                                                |

| **Address** | **Description**                             | **Value definition**                                                     |
| ----------- | ------------------------------------------- | ------------------------------------------------------------------------ |
| 5025        | Interlayer count                            | --                                                                       |
| 5027        | Working mode                                | <p><br>1: Palletizing<br><br>2: Depalletizing</p>                      |
| 5028        | Conveyor direction                          | Read-only                                                                |
| 5029        | Pallet direction                            | <p>Used in Demo mode:<br><br>0: Left pallet<br><br>1: Right pallet</p> |
| 5039        | <p>Current count in current<br>layer</p>    | --                                                                       |
| 5041        | <p>Manual pallet placement<br>stop flag</p> | <p><br>0: Not stopped<br><br>1: Stopped</p>                            |

####  **Common Variable Register Address Definitions:**

| **Address** | **Description**          | **Value definition**                                                                                                                                                                                                                                                                                   |
| ----------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 5012        | Total number of pallets  | --                                                                                                                                                                                                                                                                                                     |
| 5013        | Total number of boxes    | --                                                                                                                                                                                                                                                                                                     |
| 5014        | Operating time - Hours   | --                                                                                                                                                                                                                                                                                                     |
| 5015        | Operating time - Minutes | --                                                                                                                                                                                                                                                                                                     |
| 5016        | Operating time - Seconds | --                                                                                                                                                                                                                                                                                                     |
| 5040        | Soft stop flag           | <p>When the soft stop flag is detected:<br><br>If the robot is holding a box, it<br>completes placement and<br>returns to the safe home<br>position before stopping.<br><br>If the robot is not holding a<br>box, it returns to the safe<br>home position during the<br>process before stopping.</p> |

| **Address** | **Description**                                                | **Value definition**                    |
| ----------- | -------------------------------------------------------------- | --------------------------------------- |
| 5044        | <p>Pallets completed in<br>current task under task<br>mode</p> | --                                      |
| 5045        | <p>Boxes completed in current<br>task under task mode</p>      | --                                      |
| 5046        | Task mode completion flag                                      | <p>0: Not completed<br>1: Completed</p> |
| 5047        | <p>Clear alarm status, reset<br>buzzer</p>                     | --                                      |

####  **Alarm Register Address Definitions:**

| **Address** | **Description** | **Value definition**                                                         |
| ----------- | --------------- | ---------------------------------------------------------------------------- |
|             |                 | <p>Error messages (uploaded to the Modbus<br>register).</p>                  |
|             |                 | <p><br>0: No error</p>                                                      |
|             |                 | <p><br>1: Communication failure between robot and<br>lifting axis</p>       |
|             |                 | <p><br>2: Point unreachable</p>                                             |
|             |                 | <p><br>3: Pallet missing detected</p>                                       |
|             |                 | <p><br>4: Height limit function enabled, both both<br>conveyors stopped</p> |
|             |                 | <p><br>5: Box dropped</p>                                                   |
|             |                 | <p><br>6: Startup with a box</p>                                            |
| 5030        | Alarm code      | <p><br>7: Interlayer empty/full</p>                                         |
|             |                 | <p><br>8: Modbus communication creation failed,<br>check Modbus address</p> |
|             |                 | <p><br>9: Excessive lifting column movement count</p>                       |
|             |                 | <p><br>10: Reserved for camera-related functions</p>                        |
|             |                 | <p><br>11: Reserved for camera-related functions</p>                        |
|             |                 | <p><br>12: Abnormal lifting column status</p>                               |
|             |                 | <p><br>13: Reserved for camera-related functions</p>                        |
|             |                 | <p><br>14: No pallet enabled</p>                                            |
|             |                 | <p><br>15: Failed to read the lifting column position</p>                   |
|             |                 | <p><br>16: Queue timeout</p>                                                |

User Guide Copyright © SHENZHEN DOBOT CORP LTD

| **Address** | **Description** | **Value definition**                                                                    |
| ----------- | --------------- | --------------------------------------------------------------------------------------- |
|             |                 | <p><br>17: Work data error</p>                                                         |
|             |                 | <p><br>18: Interlayer quantity warning</p>                                             |
|             |                 | <p><br>19: Robot Home position return error</p>                                        |
|             |                 | <p><br>20: Project suction cup type inconsistent with<br>workstation configuration</p> |
|             |                 | <p><br>21: Material not released</p>                                                   |

####  **Registers Used When Alarm Code = 2:**

| **Address** | **Description**             | **Value definition**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| ----------- | --------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 5031        | Alarm point type            | <p>Picking point = {1: No interlayer, 2:<br>With interlayer}<br>Point above picking point = {3: No<br>interlayer, 4: With interlayer}<br>Transition point = {5: No interlayer,<br>6: With interlayer}<br>Placing offset point = {7: No<br>interlayer, 8: With interlayer}<br>Point above placing point = {9: No<br>interlayer, 10: With interlayer}<br>Placing point = {11: No interlayer,<br>12: With interlayer}<br>**NOTE:**During depalletizing, the<br>picking and placing points are<br>reversed, and the placing point<br>index is not displayed.<br>During palletizing, the picking point<br>index is not displayed.</p> |
| 5032        | Layer index of alarm point  | --                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| 5033        | Alarm point index           | --                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| 5034        | Pallet index of alarm point | <p><br>1: Left pallet<br><br>2: Right pallet</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |

## Appendix B Reference Manuals

### B.1 Cycle Rate Improvement Guide

Find the _DOBOT Palletizing Workstation Cycle Rate Improvement Guide_ in [DOBOT's official Download Center](https://portal.dobot-robots.com/home).

### B.2 Safety Function Manual

Find the _DOBOT Palletizing Workstation Safety Function Manual_ in [DOBOT's official Download Center](https://portal.dobot-robots.com/home).
