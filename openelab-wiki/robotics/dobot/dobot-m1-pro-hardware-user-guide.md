---
description: >-
  Hardware guide for the DOBOT M1 Pro SCARA robot: safety, transport,
  specifications, installation, wiring, maintenance, disposal, and I/O circuits.
---

# DOBOT M1 Pro Hardware User Guide

## DOBOT M1 Pro High-Speed SCARA Robot

{% embed url="https://openelab.io/products/dobot-m1-pro-scara-robot" %}

## Contents

* Preface
* 1\. Security Precautions
* 2\. Transportation
* 3\. Product Introduction
* 4\. Product Features
* 5\. Mechanical Specifications
* 6\. Electrical Specifications
* 7\. Installation
* 8\. Maintenance and Repair
* 9\. Disposal and Environment
* Appendix A Technical Specifications
* Appendix B Digital Circuit Description

## Copyright and Disclaimer

Copyright © Shenzhen Yuejiang Technology Co., Ltd 2024. All rights reserved.

No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of Yuejiang Technology Co., Ltd.

To the maximum extent permitted by applicable law, the products described in this document, including their hardware, software, and firmware, are provided as is and may contain flaws, errors, or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to merchantability, satisfactory quality, fitness for a particular purpose, and non-infringement of third-party rights. Dobot will not be liable for special, incidental, consequential, or indirect damages resulting from the use of its products or documentation.

Before using the product, thoroughly read and understand this guide and the related technical documents published online. Use the product with guidance from qualified professionals. The user is responsible for complying with the applicable laws and regulations of the country or region where the robot is used.

**Shenzhen Yuejiang Technology Co., Ltd**\
Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China\
[www.dobot-robots.com](https://www.dobot-robots.com)

## Preface

### Purpose

This document describes the functions, technical specifications, and installation requirements of the DOBOT M1 Pro robot so that users can fully understand and use the product.

### Intended Audience

This document is intended for:

* Customers
* Sales engineers
* Installation and commissioning engineers
* Technical support engineers

### Change History

| Date       | Issue | Change description                                        |
| ---------- | ----- | --------------------------------------------------------- |
| 2024-12-05 | V1.8  | Content optimization                                      |
| 2024-10-30 | V1.7  | Added the packaging posture description                   |
| 2024-04-18 | V1.6  | Added Chapter 9, Disposal and Environment                 |
| 2024-02-26 | V1.5  | Added design service life to the technical specifications |
| 2023-07-19 | V1.4  | Updated content styles                                    |
| 2023-02-02 | V1.3  | Overall content optimization                              |
| 2022-03-29 | V1.2  | Added the brake-release description                       |
| 2021-07-08 | V1.1  | Added general safety information                          |
| 2021-04-23 | V1.0  | First release                                             |

### Symbol Conventions

| Symbol  | Description                                                                                                                             |
| ------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER  | Indicates a high-risk hazard that, if not avoided, could result in death or serious injury.                                             |
| WARNING | Indicates a medium- or low-risk hazard that, if not avoided, could result in minor or moderate injury or robot damage.                  |
| NOTICE  | Indicates a potentially hazardous situation that, if not avoided, could result in equipment damage, data loss, or an unexpected result. |
| NOTE    | Provides additional information that emphasizes or supplements important points in the main text.                                       |

## 1. Security Precautions

### 1.1 Liability

#### 1.1.1 Validity and Responsibility

The information in this document does not cover the design, installation, and operation of a complete robot system, nor does it cover every peripheral device that can affect the safety of the complete system. The complete system must be designed and installed in accordance with the safety requirements, standards, and regulations of the country or region where the robot is installed.

Dobot integrators are responsible for ensuring compliance with applicable safety laws and regulations and for eliminating significant hazards in the complete robot application. Their responsibilities include, but are not limited to:

* Performing a risk assessment for the complete robot system.
* Adding safety machines and mechanisms based on the risk assessment.
* Configuring appropriate safety settings in the software.
* Ensuring that users cannot modify the safety measures.
* Validating that the complete robot system is designed and installed correctly.
* Providing instructions for use.
* Marking the integrator's contact information and relevant safety signs on the robot system.
* Archiving relevant technical files.

#### 1.1.2 Limitation of Liability

Safety information in this document must not be construed as a warranty by Dobot. The robot may cause injury or damage even when all safety instructions are followed.

#### 1.1.3 Intended Use

DOBOT M1 Pro robots are industrial robots intended only for general industrial use, such as processing or transferring components and other products with end-of-arm tools.

Any application that deviates from the intended use is considered impermissible misuse, including but not limited to:

* Use in potentially explosive environments.
* Use in life-critical applications.
* Use before a complete risk assessment has been performed.
* Use beyond the stated specifications.

### 1.2 Safety Warning Signs

The following warning signs may appear in this document and on the product.

![Attention warning sign](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO4VjayXY5HtdsLM43YBn%2Fm1-pro-p08-img01.jpg?alt=media)

| Sign        | Description                                                                                                                                                |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER      | Indicates a high degree of potential danger that, if not avoided, will result in death or serious injury.                                                  |
| ELECTRICITY | Indicates an electrical hazard that may cause personal injury or serious equipment damage.                                                                 |
| HOT         | Indicates a hot surface that may cause injury if touched.                                                                                                  |
| WARNING     | Indicates a moderate or low potential hazard that, if not avoided, may cause minor personal injury or equipment damage.                                    |
| ATTENTION   | Indicates a potential risk that, if ignored, may damage the robot, cause data loss, or produce unpredictable results.                                      |
| NOTICE      | Indicates a situation that, if not avoided, may cause personal injury or equipment damage. Depending on the situation, significant consequences may occur. |

### 1.3 General Safety

Follow these instructions when starting and using the robot for the first time.

{% hint style="danger" %}
* The robot system is electrical equipment. Personnel without the necessary electrical qualifications must not modify its circuitry.
* Comply with local laws and regulations when operating the robot. The precautions in this manual supplement, but do not replace, local requirements.
* Operate the robot only within the specified environmental and load limits. Exceeding those limits may shorten its service life or damage it.
* Ensure that the robot operates under safe conditions and that no harmful objects are present around it.
* Repeatedly switching the power on and off can degrade main-circuit components. If repeated switching is necessary, keep the frequency below once per minute.
{% endhint %}

{% hint style="warning" %}
* Personnel responsible for installation, operation, and maintenance must receive strict training, understand the safety precautions, and master the correct procedures before working with the equipment.
* Untrained personnel must not disassemble or repair the equipment. Contact Dobot technical support when the device fails.
* Perform daily inspections and scheduled maintenance, and replace faulty parts promptly.
* Dispose of scrapped equipment in accordance with applicable industrial-waste and environmental regulations.
* Install safety measures such as guardrails, ropes, or warning lines around the robot's operating area and keep personnel outside its reach.
* Do not enter the safety area defined by the risk assessment or touch the robot while the system is operating.
* Install a safety fence to prevent accidental entry into the robot workspace. Confirm that nobody is inside the fence before operating the robot, and operate it from outside the fence.
* Do not expose the robot to permanent strong magnetic fields.
* Use suitable and reliable lifting equipment. Lifting must be performed by appropriately qualified or authorized personnel.
* During transportation, keep personnel away from a suspended robot and make sure no obstacles are present within 2 m.
* Before packaging, confirm that the robot is in the packaging posture and that the brakes on all axes operate correctly.
* Secure the packaging so that the robot remains stable during transportation.
* After removing the outer packaging, confirm that the robot remains in its original packaging posture and that all axis brakes operate correctly.
* During commissioning, keep personnel and unrelated equipment, including the commissioning computer, outside the machine's hazardous area.
* Wear appropriate personal protective equipment when required, including a safety helmet, non-slip safety shoes, face shield, protective glasses, and gloves.
* If the robot behaves abnormally, stop it before inspection.
* After commissioning, test the program in Manual mode first. Use automatic operation only after the test has been confirmed correct.
* If the controller is restarted after a power failure, manually return the robot to the initial position of the automatic program before restarting automatic operation.
* Disconnect the power before maintenance or wiring work and display a "No power supply" sign.
* Observe ESD requirements when disassembling the robot or controller.
* The controller power system may retain high voltage for several hours after shutdown. Contact Dobot technical support for disassembly and repair.
* Maintenance and repair must be carried out by designated personnel.
* When manually releasing a brake, support the robot body and any attached tool or workpiece because gravity may cause the robot to move.
* Before replacing parts, switch off the circuit breaker, disconnect the main power, and wait at least 5 minutes.
* Do not operate the robot in a strong-radiation environment, including near an unshielded RF source.
{% endhint %}

{% hint style="warning" %}
* Wear suitable protective clothing, including an antistatic uniform, protective gloves, and protective shoes.
* Do not modify or remove nameplates, instructions, icons, or marks from the robot or related equipment.
* Before operating the equipment, locate the emergency stop and become familiar with its operation. The emergency stop function is Stop Category 1.
* Handle and install the robot carefully. Follow the orientation markings on the packaging.
* Use the specified cables when connecting the robot to internal or external equipment.
* Make sure the robot and its tools are installed correctly and have sufficient space to move freely.
* Do not continue using a damaged robot.
* Impacts can release substantial kinetic energy, especially at high speed and high load.
{% endhint %}

### 1.4 Personal Safety

Observe the following precautions to protect operators working with the robot system.

{% hint style="warning" %}
* Comply with local restrictions on the maximum weight that one person may carry.
* Do not touch terminal blocks or disassemble equipment while the power is on.
* Confirm that the equipment is properly grounded.
* Do not touch terminal blocks or remove internal circuit components for at least 10 minutes after shutdown because residual capacitance may remain in the controller.
* Do not wear loose clothing or jewelry while working with robots. Tie back long hair.
* A stationary robot may be waiting for a start signal and may move without further warning. Treat it as active and do not approach it.
{% endhint %}

### 1.5 Emergency

#### 1.5.1 Emergency Stop Switch

Pressing the emergency stop switch immediately stops all robot motion and locks the robot. Emergency equipment is a supplemental protective measure under IEC 60204-1 and ISO 13850; it is not a substitute for a safety guard.

#### 1.5.2 Emergency Recovery

The emergency stop switch locks when pressed. Rotate it in the direction indicated on the switch to release it.

{% hint style="danger" %}
Recover the robot from an emergency only after the source of danger has been completely removed.
{% endhint %}

#### 1.5.3 Forced Joint Movement

In the unlikely event that robot power is unavailable or unwanted during an emergency, it may be necessary to push or pull the robot arm firmly to move a joint.

{% hint style="danger" %}
Forcing a locked joint to move may damage it. Use this method only in an emergency.
{% endhint %}

## 2. Transportation

Transport the robot in its packaging posture. Manually unlock the Z axis, lower it to the lowest position, lock it, switch off the power, and then package the robot. The joint positions for the packaging posture are J1 = 0°, J2 = 0°, J3 = 0 mm, and J4 = 0°. Adjust the joints by jogging or programming as described in the applicable control-software guide.

![Figure 2.1 Packaging posture](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVLw3KD9tH9A7P3fTNLaQ%2Fm1-pro-p13-img01.jpg?alt=media)

During transportation, secure the robot so that it remains stable. For transportation and long-term storage, keep the ambient temperature between -20°C and 55°C and the relative humidity at or below 95% without condensation.

When moving the robot from its packaging to the installation location, support the arm until all mounting bolts at the base are securely tightened.

{% hint style="warning" %}
* Avoid excessive stress on the operator's back or other body parts. Use suitable lifting equipment when necessary.
* Dobot is not responsible for damage caused during transportation.
* Follow all installation instructions when installing the robot.
{% endhint %}

Store the original packaging in a dry location for future repacking and transportation.

## 3. Product Introduction

### 3.1 Overview

DOBOT M1 Pro is a second-generation light-industrial SCARA robot. It supports teaching and playback, script control, Blockly programming, and vision identification, making it suitable for intelligent sorting, PCB soldering, and other automated production lines.

Key characteristics include:

* An integrated drive and controller design eliminates the need for an external controller and simplifies initial installation and deployment.
* Calibrated servos, harmonic reducers, and kinematic algorithms provide a balance of strength and speed.
* The rated payload is 1.5 kg, and repeatability is ±0.02 mm.
* Multiple I/O and communication interfaces support different application scenarios.

The controller is installed in the base. The moving assembly contains three rotary joints, J1, J2, and J4; one vertical prismatic joint, J3; and the upper-arm and forearm links.

![Figure 3.1 M1 Pro appearance and component locations](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVVGQ49P8ocys9QWL0VXc%2Fm1-pro-p15-img01.jpg?alt=media)

### 3.2 Indicator Light

A strip indicator on the top of the M1 Pro displays the robot status.

| Color | Status   | Definition                                 |
| ----- | -------- | ------------------------------------------ |
| White | Flashing | System is starting                         |
| Blue  | Steady   | Robot has started but is not enabled       |
| Blue  | Flashing | Hand-guiding mode                          |
| Green | Steady   | Robot is enabled and no project is running |
| Green | Flashing | Automatic operation; a project is running  |
| Red   | Steady   | General alarm                              |
| Red   | Flashing | Position-limit alarm                       |

### 3.3 Drag Button

When power is disconnected, the brake prevents the upper arm and forearm from falling along the J3 axis under gravity. A drag button is installed at the bottom of the upper arm. With the power on, press and hold the button to drag the arm. The button is a momentary switch and is active only while pressed.

{% hint style="warning" %}
Support the robot arm with your hands while dragging it; otherwise, the arm may fall.
{% endhint %}

### 3.4 Operation Terminal

The M1 Pro can be controlled from a PC or mobile device. Wi-Fi control requires the Wi-Fi module to be connected to a USB port on the base.

| Terminal              | PC                                         | Android tablet                            | iPad            |
| --------------------- | ------------------------------------------ | ----------------------------------------- | --------------- |
| Operating system      | Windows 7/10/11                            | Android 10 or later                       | iOS 10 or later |
| Control software      | DobotStudio Pro                            | Dobot CRStudio                            | Dobot CRStudio  |
| Minimum configuration | Intel Core i3; 4 GB memory; 256 GB storage | Four-core CPU; 2 GB memory; 32 GB storage | 32 GB storage   |
| Communication         | LAN or Wi-Fi                               | Wi-Fi                                     | Wi-Fi           |

## 4. Product Features

### 4.1 Arm Orientation

The M1 Pro supports right-handed and left-handed arm orientations. Specify the intended orientation when commanding motion. If the orientation is not specified correctly, the robot may follow an unexpected path and interfere with surrounding equipment.

![Figure 4.1 Right-handed arm orientation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNnThpiHBfH2IvAOxmWbp%2Fm1-pro-p18-img01.jpg?alt=media)

![Figure 4.2 Left-handed arm orientation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAlQ7DZIhAvs41bsxwlSv%2Fm1-pro-p18-img02.jpg?alt=media)

### 4.2 Coordinate System

#### 4.2.1 Joint Coordinate System

The joint coordinate system is defined by the robot's moving joints.

* J1, J2, and J4 are rotary joints located in the horizontal plane. Their axes are parallel, and their positive direction is counterclockwise.
* J3 is a prismatic joint that moves the end effector vertically. Its positive direction is upward.

![Figure 4.3 M1 Pro joint coordinates](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZh53tUgtzEUUiNEEUyg3%2Fm1-pro-p19-img01.jpg?alt=media)

#### 4.2.2 User Coordinate System

A user coordinate system is a movable coordinate system used to represent equipment such as fixtures and worktables. Its origin and axis directions can be defined for the application to simplify point measurement and task programming.

The default user coordinate system is located at the robot base:

* The origin is at the motor-axis center of the upper arm when the arm is at the bottom of the Z-axis screw.
* The positive X axis points forward, perpendicular to the base.
* The positive Y axis points left, perpendicular to the base.
* The positive Z axis points vertically upward according to the right-hand rule.

![Figure 4.4 Default user coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTZ7Jxgh7kZD0XxvDNjcf%2Fm1-pro-p20-img01.jpg?alt=media)

#### 4.2.3 Tool Coordinate System

The tool coordinate system defines the position and rotation offset of a workpiece or tool attached to the robot flange. Its origin and axes move with the flange pose.

![Figure 4.5 Default tool coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2TbXIfOScLyKNA9aOk6M%2Fm1-pro-p20-img02.jpg?alt=media)

### 4.3 Home Posture

The posture in which all joint angles or positions are 0° or 0 mm is the home posture.

![Figure 4.6 M1 Pro home posture](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPbb9Jt3VmU16CV04GIGr%2Fm1-pro-p21-img01.jpg?alt=media)

If the home position changes because of a collision or replacement of a transmission component, use the supplied calibration block and control software to recalibrate the robot. Refer to the corresponding control-software guide for instructions.

### 4.4 Stop Time and Angle

The following values are the maximum stopping time and stopping angle or distance for each joint at maximum speed, maximum load, and full arm extension.

| Axis | Maximum stopping angle | Maximum stopping time |
| ---- | ---------------------: | --------------------: |
| J1   |                   9.6° |                103 ms |
| J2   |                   9.4° |                102 ms |
| J4   |                  36.5° |                100 ms |

| Axis | Maximum stopping distance | Maximum stopping time |
| ---- | ------------------------: | --------------------: |
| J3   |                     43 mm |                104 ms |

## 5. Mechanical Specifications

All dimensions in this section are in millimetres.

### 5.1 Robot Dimensions

![Figure 5.1 M1 Pro dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FY35dcMPXkDrz9ZmOrhf7%2Fm1-pro-p22-img01.jpg?alt=media)

### 5.2 Base and End-Effector Dimensions

Compatible grippers and suction cups can be installed at the end of the M1 Pro for handling and intelligent sorting applications.

![Figure 5.2 Base and end-effector dimensions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIMRtotyVklc5z6o3Bl49%2Fm1-pro-p23-img01.jpg?alt=media)

### 5.3 Robot Workspace

![Figure 5.3 M1 Pro workspace](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw8vK9R7OehWMkLgeYfZd%2Fm1-pro-p23-img02.jpg?alt=media)

{% hint style="warning" %}
Operate the robot only within its defined workspace.
{% endhint %}

### 5.4 Robot Load Curve

The payload center-of-mass offset must remain within 100 mm of the J4 axis. The maximum payload is 1.5 kg and decreases as the offset increases. At a 100 mm offset, the maximum payload is 0.5 kg.

![Figure 5.4 M1 Pro load curve](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F75tvhAgRBQQV6LXatQ2j%2Fm1-pro-p24-img01.jpg?alt=media)

## 6. Electrical Specifications

### 6.1 Base Interfaces

#### 6.1.1 Interface Overview

![Figure 6.1 Base interface panel](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh19j3ou2pmFcwRw4e4SD%2Fm1-pro-p25-img01.jpg?alt=media)

| Label          | Description                                                                                                  |
| -------------- | ------------------------------------------------------------------------------------------------------------ |
| Ethernet 1     | Ethernet interface for PC commissioning. Default IP address: `192.168.1.6`; this address cannot be modified. |
| Ethernet 2     | Ethernet interface for external equipment. Default IP address: `192.168.2.6`; this address can be modified.  |
| USB 1          | USB interface for the Wi-Fi module, firmware updates, and other supported devices.                           |
| USB 2          | USB interface for the Wi-Fi module, firmware updates, and other supported devices.                           |
| Encoder        | Differential ABZ incremental encoder interface for conveyor tracking.                                        |
| Power switch   | Switches robot power on and off.                                                                             |
| Emergency stop | Emergency-stop interface.                                                                                    |
| Power          | Connection for the 48 V DC power supply.                                                                     |
| I/O            | Base digital I/O interface.                                                                                  |

The encoder connector and its pinout are shown below.

![Figure 6.2 Encoder connector](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJaNyVxlpWS20HuyLYYfo%2Fm1-pro-p26-img01.jpg?alt=media)

| Pin    | 1       | 2       | 3       | 4       | 5       | 6       | 7   | 8   | 9      |
| ------ | ------- | ------- | ------- | ------- | ------- | ------- | --- | --- | ------ |
| Signal | ABZ\_A+ | ABZ\_A- | ABZ\_B+ | ABZ\_B- | ABZ\_Z+ | ABZ\_Z- | 5 V | 0 V | Unused |

#### 6.1.2 Base I/O Interface

The base I/O interface connects external equipment such as a PLC and provides 16 digital inputs and 16 digital outputs.

![Figure 6.3 Base I/O interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpLmGuqqWHxAsYjJTY5bZ%2Fm1-pro-p26-img02.png?alt=media)

{% hint style="info" %}
* Digital I/O is powered by the internal 24 V supply. Total current must not exceed 2 A.
* Output current from any individual I/O channel must not exceed 500 mA.
{% endhint %}

**Digital input wiring**

The following diagram shows a digital input connected to a simple switch.

![Figure 6.4 Digital input connected to a simple switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVrHlrumsZv4dgiUGCHoJ%2Fm1-pro-p27-img01.jpg?alt=media)

The following diagram shows a digital input connected to a PNP three-wire sensor.

![Figure 6.5 Digital input connected to an external output](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAoMBeKfklGGKq9BDGnwo%2Fm1-pro-p27-img02.jpg?alt=media)

**Digital output wiring**

The following diagram shows a digital output connected to an external load without a separate external power supply.

![Figure 6.6 Digital output connected to a load without an external power supply](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgOokgHihdqMBJteUcheV%2Fm1-pro-p27-img03.jpg?alt=media)

If a load requires more than 500 mA, use an external drive circuit to increase the available drive capacity.

![Figure 6.7 Digital output connected to a load with an external power supply](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuDrjfFgnwJ5bPj2yOAzy%2Fm1-pro-p27-img04.jpg?alt=media)

### 6.2 End-Effector I/O Interface

The M1 Pro end-effector interface provides one RS-485 interface, four digital inputs, and four digital outputs.

![Figure 6.8 End-effector I/O connector](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWJP9yDRA3dYfKMWIJ59c%2Fm1-pro-p28-img01.jpg?alt=media)

| Pin | Signal | Pin | Signal   |
| --: | ------ | --: | -------- |
|   1 | 24 V   |   9 | RS-485 A |
|   2 | DO17   |  10 | RS-485 B |
|   3 | DO18   |  11 | DI17     |
|   4 | DO19   |  12 | DI18     |
|   5 | DO20   |  13 | DI19     |
|   6 | Unused |  14 | DI20     |
|   7 | Unused |  15 | 0 V      |
|   8 | Unused |     |          |

## 7. Installation

### 7.1 Installation Environment

Install the controller and robot in an environment that meets the following conditions:

{% hint style="warning" %}
* Install indoors in a well-ventilated location.
* Keep the robot away from excessive vibration and shock.
* Keep it away from direct sunlight.
* Keep it away from dust, oil mist, salt, metal powder, corrosive gases, and other contaminants.
* Do not operate it in an enclosed space; excessive temperature may shorten the robot's service life.
* Keep it away from flammable materials.
* Keep it away from cutting and grinding fluids.
* Keep it away from electromagnetic-interference sources such as large transformers, large contactors, and welding equipment.
* High-altitude operation may affect performance. Contact Dobot technical support for guidance.
{% endhint %}

### 7.2 Unpacking

Check the supplied packing list when unpacking the robot. If any item is missing, contact the supplier.

### 7.3 Robot Installation

After removing the robot from the packaging, secure the base with six M6 hexagon-socket bolts tightened to 17 N·m. The installation directly affects operating stability.

Design or select the mounting platform according to the base-hole dimensions, robot workspace, and installation environment. The installation height must be greater than 0.6 m. The platform must support both the robot weight and the dynamic forces generated during maximum-acceleration motion.

When mounting the robot:

* Ensure that the movement path is unobstructed throughout the robot workspace.
* Keep the mounting surface horizontal.

### 7.4 Wiring and Power-On

1. Connect the emergency-stop cable to the emergency-stop terminal.
2. Connect the power cable. Connect its other end to the external supply through the power adapter.
3. Connect the computer to Ethernet 1 for commissioning. If a Wi-Fi module was purchased, insert it into a USB port on the base instead of using the Ethernet cable.
4. Press the power switch. After startup, control the robot with DobotStudio Pro or Dobot CRStudio. Refer to the applicable software guide for operating instructions.

![Figure 7.1 M1 Pro wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fuclh0RQkBr2hvVwxHWVL%2Fm1-pro-p30-img01.jpg?alt=media)

## 8. Maintenance and Repair

Maintenance and repair must be carried out in accordance with all safety instructions in this manual. Their purpose is to keep the system operational or return it to an operational condition after a fault. Repair includes troubleshooting as well as the physical repair itself.

Repairs must be performed by an authorized system integrator or Dobot personnel.

Before returning a robot or component to Dobot:

* Remove all components that are not supplied by Dobot.
* Back up all files. Dobot is not responsible for loss of programs, data, or files stored in the robot.
* Move the robot to its packaging posture.

### 8.1 Safety Instructions

{% hint style="warning" %}
* Replace faulty components only with new parts of the same model or equivalent parts approved by Dobot.
* Reactivate every disabled safety measure immediately after repair.
* Record all repairs and store the records with the robot system's technical documentation.
* Disconnect the controller's main input cable and every other power source. Prevent other personnel from restoring power during repair.
* Observe ESD requirements when disassembling robot-arm or controller components.
* Prevent water and dust from entering the robot arm or controller.
{% endhint %}

### 8.2 Body Maintenance

Prepare a maintenance plan and perform regular inspections to maintain long-term robot performance.

| Cycle          | Item                                 | Required work                                                                                                       |
| -------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| Daily          | Robot cleanliness                    | Remove dirt, dust, and cutting residue from the body with water or 10% alcohol.                                     |
| Every 3 months | Cables, protective covers, and bolts | Inspect moving cables for damage, local bending, or deformation; inspect protective covers; check for loose screws. |
| Every 6 months | Motor                                | Check for abnormal heating or noise.                                                                                |
| Every 6 months | Brake                                | Confirm that the robot arm and end effector do not fall when servo power is off.                                    |

Recommended tightening torques:

| Bolt size | Hexagon-socket button-head screw | Countersunk hexagon-socket screw | Hexagon screw in rubber part |
| --------- | -------------------------------: | -------------------------------: | ---------------------------: |
| 2.5 mm    |                          0.7 N·m |                                - |                            - |
| 3 mm      |                            2 N·m |                                - |                      1.2 N·m |
| 4 mm      |                            4 N·m |                            2 N·m |                            - |
| 5 mm      |                            9 N·m |                                - |                            - |

The required tightening torque may vary with the base material and bolt type. If no value is specified, contact a Dobot technical engineer.

A comprehensive overhaul is required every 10,000 operating hours or every three years. Contact Dobot technical support if the maintenance procedure is unclear.

## 9. Disposal and Environment

Dispose of DOBOT robots in accordance with applicable national laws, regulations, and standards. The crossed-out wheeled-bin symbol means that the product must not be discarded with ordinary household waste.

![Waste electrical and electronic equipment disposal symbol](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9NqTea5pBx2Atrls1Scj%2Fm1-pro-p33-img01.jpg?alt=media)

## Appendix A Technical Specifications

| Parameter                            | Specification                   |
| ------------------------------------ | ------------------------------- |
| Product                              | DOBOT M1 Pro                    |
| Model                                | DT-M1-P4R15-01I                 |
| Weight                               | 15.7 kg                         |
| Maximum payload                      | 1.5 kg                          |
| Reach                                | 400 mm                          |
| AC input                             | 100-240 V AC, 50/60 Hz          |
| Rated voltage                        | 48 V DC                         |
| Installation                         | Table installation, indoor      |
| Rated power                          | 192 W                           |
| Repeatability                        | ±0.02 mm                        |
| Base dimensions                      | 230 × 175 mm                    |
| Operation software                   | DobotSCStudio, DobotStudio 2020 |
| J1 motion range                      | ±85°                            |
| J2 motion range                      | ±130°                           |
| J3 motion range                      | 5-245 mm                        |
| J4 motion range                      | ±360°                           |
| J1 maximum speed                     | 180°/s                          |
| J2 maximum speed                     | 180°/s                          |
| J3 maximum speed                     | 1000 mm/s                       |
| J4 maximum speed                     | 1000°/s                         |
| End-effector DI                      | 4                               |
| End-effector DO                      | 4                               |
| End-effector RS-485                  | 1, Modbus RTU                   |
| Base DI                              | 16                              |
| Base DO                              | 16                              |
| Differential ABZ incremental encoder | 1                               |
| Ethernet                             | 2                               |
| USB 2.0                              | 2                               |
| Storage temperature                  | -25°C to 55°C                   |
| Working temperature                  | 0°C to 40°C                     |
| Design service life                  | 3 years                         |

### Safety Standards

* EN ISO 10218-1:2011, Robots and robotic devices - Safety requirements for industrial robots - Part 1: Robots
* EN 60204-1:2018, Safety of machinery - Electrical equipment of machines - Part 1: General requirements
* EN ISO 12100:2010, Safety of machinery - General principles for design - Risk assessment and risk reduction
* ISO/TS 15066:2016, Robots and robotic devices - Collaborative robots

### EMC Standards

* EN IEC 61000-6-4:2019, Electromagnetic compatibility - Part 6-4: Generic standards - Emission standard for industrial environments
* EN IEC 61000-6-2:2019, Electromagnetic compatibility - Part 6-2: Generic standards - Immunity standard for industrial environments

## Appendix B Digital Circuit Description

### Digital Input

![Digital input circuit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FePs7dYeOVo7OoWklYbtE%2Fm1-pro-p36-img01.jpg?alt=media)

| Item           | Specification    |
| -------------- | ---------------- |
| Input channels | 16               |
| Connection     | Crimp terminal   |
| Input type     | PNP              |
| Input voltage  | 24 V DC ±10%     |
| Isolation      | Optical coupling |

### Digital Output

![Digital output circuit](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVLbr1C30RWJjMZByMKuN%2Fm1-pro-p36-img02.jpg?alt=media)

| Item                        | Specification      |
| --------------------------- | ------------------ |
| Output channels             | 16                 |
| Connection                  | Crimp terminal     |
| Output type                 | PNP                |
| Power supply                | 24 V DC ±10%       |
| Maximum current per channel | 500 mA             |
| Total output current        | 2 A                |
| Isolation                   | Magnetic isolation |
