# DOBOT CRA/CRH Series Palletizing Workstation User Guide

## DOBOT CR20A V2 Lifting and Columnar Palletizing Workstation

{% embed url="https://openelab.io/products/dobot-cr20a-palletizing-workstation-v2" %}

## DOBOT CRA One-Stop Columnar Palletizing Workstation for CR20A (Robot Not Included)

{% embed url="https://openelab.io/products/dobot-cr20a-columnar-palletizing-workstation" %}

## DOBOT CRA One-Stop Lifting Palletizing Workstation for CR20A (Robot Not Included)

{% embed url="https://openelab.io/products/dobot-cr20a-lifting-palletizing-workstation" %}

## DOBOT CR30H Columnar Palletizing Robot Workstation

{% embed url="https://openelab.io/products/dobot-cr30h-columnar-palletizing-workstation" %}

**Manual versions:** The workstation hardware, safety, and operating text below follows the official CRA/CRH Series Palletizing Workstation User Guide V2.4.2 (2026-04-24). The separate [official DOBOT Palletizing Process Package User Guide V2.5.0 (2026-09-22)](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260923/DOBOT%20Palletizing%20Process%20Package%20User%20Guide_V2.5.0_20260922_en.pdf) covers plugin V2.5.0, software configuration, projects, and debugging for CR20A/CR30H columnar and lifting workstations. It supplements the hardware guide; it does not replace its installation or safety instructions. Match the installed controller and DobotStudio Pro versions to the software guide before following V2.5.0 steps. See the [searchable V2.5.0 process-package Wiki](https://wiki.openelab.io/dobot/dobot-palletizing-process-package-user-guide-v2-5-0).

## Contents

* Preface
* 1\. Safety
* 2\. Product Introduction
* 3\. Workflow
* 4\. Hardware Installation
* 5\. Software Configuration
* 6\. Palletizing Project Run & Monitoring
* 7\. IO Configuration
* 8\. Alarm Message and Solution
* 9\. Product Specifications
* 10\. Maintenance
* 11\. Warranty
* Appendix A Terms

## Preface

Purpose This document describes the functions, technical specifications, installation guide of DOBOT CRA/CRH Series Palletizing Workstation, making it easy for users to fully understand and use it. The terms "palletizing workstation", "workstation" used in this document all refer to the DOBOT CRA/CRH Series Palletizing Workstation. Intended audience This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

Compatible versions Product Version How to obtain Palletizing\_v2-4- Contact technical support for Palletizing Process Package 2-stable access DobotStudio Pro 4.6.4.0-stable or (PC / Android / DOBOT Download Center above Teach Pendant) CR20A Upgrade via Robot Maintenance Tool Controller 4.6.6.0-pal-stable (Get the Robot Maintenance Tool from DOBOT Download Center) DobotStudio Pro (PC / Android / 4.7.0.0-stable DOBOT Download Center Teach Pendant) CR30H Upgrade via Robot Maintenance Tool Controller 4.7.3.1-stable (Get the Robot Maintenance Tool from DOBOT Download Center)

**NOTE: The current version of DobotStudio Pro does not support import or export functions when running**

on the Teach Pendant.

Related documents Document Description Download link DOBOT Palletizing Provides guidance on configuring the Workstation Safety SICK safety LiDAR. Function Manual Introduces the functions, technical DOBOT CRA Series specifications, and installation guidance Contact technical Hardware User Guide for DOBOT CRA series collaborative support for robots. access. Introduces the functions, technical DOBOT CR30H Series specifications, and installation guidance User Guide for DOBOT CRH series collaborative robots. Revision history Date Version Revised content 2026/04/24 V2.4.2 Based on the palletizing plugin V2-4-2 2026/03/05 V2.4.1 Edited the description for pallet arrival confirmation button. Compatible with CR30H model.

*

Compatible with palletizing plugin V2-4-1. Click 2025/12/17 V2.4.1 • Version Update to search for the software update instructions for this version. 2025/11/12 V2.4.0 Replace some images. Added the user coordinate system for the picking

* point. 2025/10/31 V2.4.0 Compatible with palletizing plugin V2-4-0, you can
* click on the Version Update to search for the software update instructions for this version. 2025/01/24 V2.3.0 Based on the palletizing plugin V2-3-0 2024/09/18 V1.2 Modified figures in Product nameplate
* Based on the new version of workstation hardware

2024/09/02 V1.2

* Based on the palletizing plugin V2-2-0

2024/04/30 V1.1 Based on the palletizing plugin V2-1-0 2024/02/01 V1.0 The first release

Symbol conventions The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided,

**DANGER**

could result in death or serious injury. Indicates a hazard with a medium level or low level of risk which, if

**WARNING not avoided, could result in minor or moderate injury, robot arm**

damage. Indicates a potentially hazardous situation which, if not avoided,

**NOTICE could result in robot arm damage, data loss, or unanticipated**

result. Provides additional information to emphasize or supplement

**NOTE**

important points in the main text.

## 1. Safety

### 1.1 Responsibilities and norms

The DOBOT CRA/CRH Series Palletizing Workstation (hereinafter referred to as “Palletizing Workstation”) is a palletizing solution developed based on the DOBOT CR20A series or CR30H collaborative robot. The installation and use of the Palletizing Workstation must comply with the safety requirements outlined in the standards and regulations of the country in which it is located. All safety information contained in this document should not be regarded as a guarantee by DOBOT. Even if all safety instructions are followed, the robot may still pose a risk of injury or damage.

### 1.2 Intended use

The Palletizing Workstation is specifically designed for palletizing scenarios, and any use outside of this intended purpose is not permitted.

### 1.3 Safety instructions

Before using the Palletizing Workstation, users must read and understand all of the following instructions.

**NOTICE**

* Before installing and using the Palletizing Workstation, a complete risk assessment must be conducted for the specific field application, and additional safety equipment or mechanisms should be implemented based on the results of the assessment.
* Before initial use, it is recommended to perform a dry run of the project at a slow speed to prevent collisions or other unexpected incidents.
* Users must fully adhere to the safety instructions provided in the CRA/CRH series user guide.
* If users need to customize the suction cup component, they should pay special attention to the associated safety risks, including but not limited to: a) Risk of box shaking or falling due to insufficient suction. b) Risk of collision with the Palletizing Workstation due to the shape and size of the suction cup. c) Risk of overloading due to the weight of the suction cup. d) Risk of deformation or fracture of the bracket due to quality problems of the suction cup bracket.

**NOTICE**

* For the Lifting Palletizing Workstation, the potential safety risks associated with the lifting column must also be fully considered in the application-specific risk assessment: e) The lifting column cannot automatically detect collisions and will not stop moving if a collision occurs. This can lead to: ◦ Crushing or injuring people or objects in the path of the lifting column, resulting in serious injury, death, or property damage. ◦ Collisions with people or objects, resulting in serious injury, death, or property damage. f) The lifting column may not stay precisely at the expected position, causing the robot to follow an unintended path, which could lead to serious injury or property damage.

### 1.4 Warning labels

The workstation is labeled with the following safety warning signs. Their meanings and locations are as follows: Label Meaning Location Electrical Hazard. Operating here may cause electric shock. Be careful. Pinch Point Hazard. Operating here may result in injury due to pinch points. Be careful.

### 1.5 Emergencies

#### 1.5.1 Emergency stop device

In case of emergency, you can press the emergency stop switch to immediately halt and lock the robot arm and lifting column. It’s important to note that emergency stop devices are not safety guards as defined by IEC 60204-1 and ISO 13850. They serve as supplemental protective measures and are not intended to fully prevent injury.

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3uoNQSPhDPVkaB0L9SmD%2Fpalletizing-p009-img03.png?alt=media)

**WARNING**

The suction cup will continue to function during an emergency stop, but it may shake due to inertia, potentially causing the box to fall. Please be aware that a falling box could result in damage or injury.

#### 1.5.2 Emergency recovery

The emergency stop switch will be locked after you press it. To unlock it, turn the switch in the direction indicated. Once the emergency stop button is reset, you need to clear the alarm in the control software, re-enable the robot arm, and then restart the project.

**WARNING**

* Make sure that all system hazards are completely eliminated before recovering the robot arm from emergency status.
* Before resuming operation, make sure that no one is within the workstation’s working range and remove any load (box) from the suction cup at the end of the robot arm.

### 1.6 Safety distance and protective device

The workstation should be centered on the base of the robot arm, and a safe space must be reserved according to the motion range of the robot arm (CR20A: 1700mm, CR30H: 1800mm). Protective devices, such as fences and safety lasers, should be installed at a safe distance. The control device for the workstation should also be positioned at a safe distance. DOBOT offers a safety solution based on Safe LiDAR. For more details, please refer to the DOBOT Palletizing Workstation Safety Function Manual.

## 2. Product Introduction

### 2.1 Overview

The Palletizing Workstation developed by DOBOT is specifically designed for palletizing applications and comes in two types: Columnar and Lifting. The robot arm in the Columnar Palletizing Workstation is mounted on a fixed-height column, offering a simpler system and lower cost. In contrast, the robot arm in the Lifting Palletizing Workstation is mounted on an adjustable-height lifting column, which allows for increased palletizing height and the stacking of more products.

_Figure 2.1 Main components of CR30H Columnar Palletizing Workstation_

_Figure 2.2 Main components of CR20A Columnar & Lifting Palletizing Workstation_

![Figure 2.1 Main components of CR30H Columnar Palletizing Workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9yzHSVD0JElFQVOrcNBw%2Fpalletizing-p011-img02.png?alt=media)

![Figure 2.2 Main components of CR20A Columnar & Lifting Palletizing Workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxP0q8RXW4xvOCaV7JpPv%2Fpalletizing-p011-img03.png?alt=media)

No. Component Description Used to pick up boxes through vacuum suction. The End-of-arm suction suction cup is an optional accessory and must be ① cup purchased separately by the customer. See "End-of- arm suction cup (optional)" for details. ② Robot arm The main moving part of the palletizing workstation. One on each side (left/right). Used to indicate the ③ Indicator lights operating status of the workstation. See "Indicator light" for status definitions. One on each side (left/right). Used to confirm that the Pallet arrival pallet on the corresponding side has been replaced and ④ confirmation button is properly positioned, preventing the robot arm from moving before the pallet replacement is complete. Emergency stop Used to stop the workstation in an emergency. ⑤ button ⑥ Robot controller Controller that supplied with the robot arm. Some electrical components and cables are installed ⑦ Palletizing base inside the base. The base has four leveling feet in total, two at the front and two at the rear. Used to widen the base, allowing the pallet to be positioned further away from the robot arm's center to ⑧ Base extension plate prevent collisions during operation. The base extension plate is only required for CR30H. Used to support the robot arm. The height of the lifting column is adjustable. When a palletizing project is running, the system automatically calculates the lifting Column / ⑨ column height required for picking or placing the next Lifting column box and controls the lifting column's movement accordingly. No user configuration is required. When the script stops, the lifting column stops simultaneously. Includes air source interface, air valves, etc., used to control the workstation's air supply. The air valve switch is set to ON by default and locked with a padlock. To ⑩ Pneumatic assembly turn off the air valve, remove the padlock using the key provided in the shipping list and turn the air valve switch clockwise.

Used to connect an external pneumatic equipment to Air source interface supply air to the suction cup. ⑪ Includes external interfaces reserved for users, such as Wiring terminal panel LAN port, safety I/O, etc. See "Electrical interface" for details. ⑫ Both left and right sides are equipped with a barrier for Pallet sensing & pallet positioning. Each barrier is fitted with a sensor to positioning device detect whether the pallet is in place. ⑬ Used to connect to an external power supply to provide Power interface power to the workstation. ⑭

### 2.2 Indicator light

Indicator Color Status Definition Steady on Pallet on this side is idle Green Flashing Palletizing in progress Steady on No pallet detected on this side Yellow Flashing Palletizing on this side is finished. Alarm triggered during palletizing on this side (see Steady on "Alarm Message and Solution") Red Communication failure (communication lost between Flashing the robot and the lifting column; see "Alarm Message and Solution")

![Official manual figure, page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVTEjjFCxIFW1DFwoCBiJ%2Fpalletizing-p013-img02.jpg?alt=media)

### 2.3 End-of-arm suction cup (optional)

The palletizing workstation can be optionally equipped with a vacuum suction cup. This suction cup features a built-in vacuum generator and check valve. When using this suction cup, the pneumatic equipment must meet the following requirements: airflow > 350 NL/min, air tube diameter of 12 mm, and a stable air supply pressure of 0.6 MPa.

_Figure 2.3 Suction cup_

You can also purchase or customize the suction cups according to your specific needs.

![Figure 2.3 Suction cup](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDPN3xsSHsY5WaGi37scF%2Fpalletizing-p014-img02.jpg?alt=media)

## 3. Workflow

### 3.1 Basic workflow for first-time use

Module Operation steps Reference content

1. Prepare materials and confirm installation Pre-installation

environment preparation

2. Unpack to verify that the shipped items

Unpacking match the packing list

3. Transport the robot arm, base, controller, Unpackaged

and related accessories transportation

4. Install base pallet barriers and pallet

Base installation position sensors Hardware 5. Install and connect the controller to the Robot controller Installation base installation

6. Install and connect the robot arm to the Robot arm

base installation

7. Install and connect the end-of-arm End-of-arm suction

suction cup cup installation

8. Install the conveyor Conveyor installation
9. After confirming that all installation and

wiring are correct, start the palletizing Power-on workstation

10. Get the corresponding palletizing process

Compatible versions package plugin

11. Install the palletizing process package Palletizing plugin

plugin installation a. Select column / lifting column, set Set workstation

12. Set the suction cup type basic parameters

palletizing and size Software workstation Configuration b. Create tool Create tool coordinate system coordinate system a. Set interlayer coordinate system

13. Create a new Set interlayer

(required only for project and coordinate system projects using configure interlayer) parameters b. Select "Palletizing Set basic

Module Operation steps Reference content mode", "Palletizing parameters type", "Conveyor direction", "Interlayer", and "Box type" c. Set box and pallet Set box/pallet parameters parameters d. Self-define the stacking pattern or select an Set stacking pattern automatic stacking pattern e. Set the number of layers and the Set number of layers stacking pattern used for each layer f. Set the number, size, and position of interlayers Set interlayer (required only for projects using interlayer) g. Set picking point, placing point and Set points transition point h. Check if the points are reachable and Check reachability save the project Run palletizing

14. Run palletizing project project

Project Run & Typical workflow Monitoring

15. Monitor the project operation data in real Real-time monitoring

time of palletizing project

**NOTE**

* When creating a new palletizing or depalletizing project, refer to the illustrations in "Typical path planning" for specific points such as safe picking height, picking/placing points, transition points, and offset points for the placing direction.
* If you encounter issues while running a palletizing project, refer to "Alarm message and solution".
* For more information on other functions of the palletizing process package, refer to "Other functions".

### 3.2 Typical workflow

After completing the hardware installation and software configuration of the palletizing workstation, the typical workflow (taking double pallets as an example) is as follows:

_Figure 3.1 Workstation workflow_

![Figure 3.1 Workstation workflow](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0CJ4zUE0UHUqbAPyzN6x%2Fpalletizing-p017-img02.png?alt=media)

**NOTE**

* Before running the project, ensure that the end-of-arm suction cup is properly installed and that the pallet user coordinate system has been calibrated.
* When both pallets are in position, if the project is stopped and then restarted, it will first stack the left pallet, even if the right pallet was being stacked before the stop. If you want the project to resume stacking the right pallet first after restarting, enable the pallet arrival confirmation signal and press the confirmation button for the right pallet after the project starts running. In addition to the standard palletizing scenario described above, the workstation also supports the following scenarios:
* Depalletizing: Removing boxes from the pallet and placing them onto a conveyor.
* One-pallet operation: Operating with just one pallet.
* Dual-box or multi-box handling: Picking up and placing two or more boxes at a time.
* Manual adjustment: Continuing palletizing with an unfinished pattern after manually adjusting the number of boxes on the pallet.
* Dual-conveyor operation: Handling boxes of two different sizes on two conveyors, each with its own palletizing pattern.

**NOTE**

The pattern on each pallet is composed of boxes of the same size; boxes of different sizes on the same pallet is not supported.

### 3.3 Typical path planning

#### 3.3.1 Palletizing

A typical path during palletizing is as follows:

_Figure 3.2 Palletizing path_

![Figure 3.2 Palletizing path](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW652UZ2bmLfdSzws4bAH%2Fpalletizing-p018-img02.jpg?alt=media)

1. The robot moves to a position directly above the picking point (B). The height above

the picking point (safe picking height) can be set in the "Basic debugging" page of the debugging panel.

2. The robot descends vertically to the user-taught picking point (A) and picks up the

box.

3. The robot returns to the position directly above the picking point (B).
4. The robot moves sequentially to the user-taught transition points (C and D). Transition

points are mainly used to avoid obstacles during movement, with their height automatically adjusted based on the current palletizing layer.

5. The robot moves to the offset point for the placing direction (E). This point is primarily

used to avoid interference between the current box being placed and the boxes already on the pallet. For more details, refer to the "Set placement direction and offset" section.

6. The robot moves to a position directly above the placing point (F). The height above

the placing point (placing point height compensation) can be set in the "Advanced debugging" page of the debugging panel.

7. The robot descends vertically to the placing point (G) and releases the box. The

placing point is calculated by the system based on the palletizing pattern and the current palletizing progress.

8. The robot returns along the same path to pick up the next box.

#### 3.3.2 Depalletizing

The depalletizing path is the reverse of the palletizing path, using the same points and height settings. A typical depalletizing path is as follows:

_Figure 3.3 Depalletizing path_

1. The robot moves to the picking point of the first box to be depalletized (G,

corresponding to the placing point during palletizing).

2. The robot ascends vertically to the position above the picking point (F).
3. The robot moves to the offset point for the placing direction (E).
4. The robot moves sequentially to the user-taught transition points (D and C).
5. The robot moves to a position directly above the placing point (B).
6. The robot descends vertically to the user-taught placing point (A) and releases the

![Figure 3.3 Depalletizing path](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2s7SEMnGCr4mIvizyPnR%2Fpalletizing-p019-img02.jpg?alt=media)

box.

7. The robot returns to the position directly above the placing point (B), then calculates

new points C to G based on the location of the next box to be picked, and follows this path to pick up the next box.

## 4. Hardware Installation

### 4.1 Pre-installation preparation

#### 4.1.1 Material Preparation

* End-of-arm suction cup (purchased from DOBOT or self-provided).
* Pneumatic equipment: airflow > 350 NL/min, air tube diameter 12 mm, stable air supply pressure at 0.6 MPa.
* Conveyor.
* Incoming material sensor.
* Picking point fixing structure.

#### 4.1.2 Layout recommendations

The floor space dimensions of the palletizing workstation for several typical palletizing modes are shown in the figures below. Please plan the installation site in advance according to your actual conditions. For CR30H 1 Conveyor 1 Pallet (Left Pallet) 1 Conveyor 1 Pallet (Right Pallet) 1 Conveyor 2 Pallets 2 Conveyors 2 Pallets

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fs4V6LocIPsK2ftow0LgZ%2Fpalletizing-p021-img02.jpg?alt=media)

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDsuSbUdjRHCxTT7yAhNS%2Fpalletizing-p021-img03.jpg?alt=media)

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6tJipno5V5q2RSmkfLDB%2Fpalletizing-p021-img04.jpg?alt=media)

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWBb1pW4cg782f9tQdc0d%2Fpalletizing-p021-img05.jpg?alt=media)

For CR20A 1 Conveyor 1 Pallet (Left Pallet) 1 Conveyor 1 Pallet (Right Pallet) 1 Conveyor 2 Pallets 2 Conveyors 2 Pallets

#### 4.1.3 Installation environment

To maintain the workstation performance and to ensure the safety, please place the workstation in an environment with the following conditions.

* Install indoors with good ventilation.
* Keep away from excessive vibration and shock.
* Keep away from direct sunlight and radiant heat.
* Keep away from dust, oily smoke, salinity, metal powder, corrosive gases, and other contaminants.
* Do not use in a closed environment. A closed environment may cause high temperature of the controller and shorten its service life.

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz7UkbCXsIzaYyZ7rhflI%2Fpalletizing-p022-img02.jpg?alt=media)

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fjjua0d4BS7nS27AdXHmA%2Fpalletizing-p022-img03.jpg?alt=media)

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpmmcYWxSX9ChIQQJZGXI%2Fpalletizing-p022-img04.jpg?alt=media)

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcxeTfYvs5M9ExIqxBkVE%2Fpalletizing-p022-img05.jpg?alt=media)

* Keep away from flammable.
* Keep away from cutting and grinding fluids.
* Keep away from sources of electromagnetic interference.

### 4.2 Unpacking

1. Before unpacking, please carefully check the outer packaging for signs of damage in

transportation. If any damage is found, please unpack in the presence of shipping company staff.

2. To move the packaged workstation, handle the packaging box of the workstation with

a forklift.

3. When unpacking, please check the attached shipping list to ensure that all contents

are included and intact. If anything is missing or damaged, please contact your supplier.

4. After unpacking, please save all packaging materials for future transportation.

### 4.3 Unpackaged transportation

#### 4.3.1 For CR30H

1. When it is necessary to move the unpackaged robot arm to the installation site or to

reposition it, please follow the handling recommendations below:

* During hoisting, the robot arm must remain in its packaged posture.
* While moving and installing the robot, manually support the arm until all base mounting bolts are fully tightened.
* Use only the factory-provided lifting sling for hoisting. For detailed hoisting instructions, refer to "Robot arm installation". Never secure the lifting sling to J3–J6 joints or the forearm to lift the robot, as this may damage its internal structure.

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkNBeaXI8yFpzZxr6AIZp%2Fpalletizing-p023-img02.jpg?alt=media)

_Figure 4.1 Hoisting the robot arm_

2. To move the workstation, you can use a forklift to enter the palletizing base from the

side and lift the workstation, as shown in the figure below.

_Figure 4.2 Base slot size_

_Figure 4.3 Handle the workstation_

![Figure 4.1 Hoisting the robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaDmZ8aTuzoyxgHf3D5Qe%2Fpalletizing-p024-img02.jpg?alt=media)

![Figure 4.2 Base slot size](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZJWvaVaJzcUlROpGtjp2%2Fpalletizing-p024-img03.png?alt=media)

![Figure 4.3 Handle the workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUkvJnJh6wNShLbtxcjZ9%2Fpalletizing-p024-img04.jpg?alt=media)

#### 4.3.2 For CR20A

1. When it is necessary to move the unpackaged robot arm to the installation site or to

reposition it, please follow the handling recommendations below:

* During hoisting, the robot arm must remain in its packaged posture.
* While moving and installing the robot, manually support the arm until all base mounting bolts are fully tightened.
* Use only the factory-provided lifting sling for hoisting, securing them at the J1 joint and the upper arm. Never secure the lifting sling to J3–J6 joints or the forearm to lift the robot, as this may damage its internal structure.

_Figure 4.4 Hoisting the robot arm_

2. Base handling: The base dimensions of the CR20A and CR30H palletizing

workstations are the same. Please refer to Base handling for specific instructions.

### 4.4 Installation of CR30H palletizing workstation

The pre-installation and wiring of the main parts of the Palletizing Workstation have been completed before delivery, and users only need to carry out simple assembly.

![Figure 4.4 Hoisting the robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFpwrPVP88ay7eOV6e0Xd%2Fpalletizing-p025-img02.png?alt=media)

**NOTICE**

* When the robot is transported, ensure that the robot is stable and kept in proper place.
* When the robot is hoisted, be sure to take appropriate measures to locate the moving parts so as not to cause accidental movement and harm during hoisting and transportation.
* When moving the robot from the packaging box to the mounting position, hold the robot until all bolts on the robot base are fastened.
* When the robot is installed, take corresponding measures to locate it. Be sure to use hex bolts to fix and tighten the robot base.
* The specifications and installation method of the external cables should comply with local laws and regulations.
* Do not disassemble the controller by yourself. Otherwise, it may result in electric leakage.
* The device must be always grounded properly.
* Do not bend the cable excessively, otherwise it may cause poor contact or cable breakage.
* When connecting an external device, make sure the power outlet of the control system is disconnected. If not disconnected, may result in electric shock or device failure.
* Use supporting cables to protect device and personal safety.
* After wiring, ensure that there are no fallen screws or exposed cables in the device.
* Do not plug or remove the power cable or communication cable when the device is running normally.
* Power on the device only after connecting all the cables required.
* Ensure that the cables are connected correctly, otherwise, it may cause fault in internal modules or external devices.
* Before connecting, check whether there is breakage in the insulation and shield of the external cables.

_Figure 4.5 Assembly diagram of the workstation_

#### 4.4.1 Base installation

1. Install the pallet barriers on both sides of the base and lock them with four

M10\*20 screws.

_Figure 4.6 Install the pallet barriers_

2. Remove the plug of the pallet sensor from the inside of the base, and connect it

to the cable of the pallet sensor through the slot.

![Figure 4.5 Assembly diagram of the workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff2ZY3wJrt3TtIYBgPqxR%2Fpalletizing-p027-img02.png?alt=media)

![Figure 4.6 Install the pallet barriers](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx54C2LYgZAlzAutZGRDu%2Fpalletizing-p027-img03.png?alt=media)

![Official manual figure, page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwIeFJOqmG3NYbNrY0FHf%2Fpalletizing-p027-img04.jpg?alt=media)

_Figure 4.7 Connect the pallet sensor_

3. Install the base extension plates on both sides. For each side, secure the front

with eight M10x25 screws and the rear with four M10x25 screws.

_Figure 4.8 Install the base extension plates_

4. After installing the side cover for the pallet edges on both sides separately,

fasten each side cover with four M10\*25 screws.

_Figure 4.9 Install the pallet side cover_

![Figure 4.7 Connect the pallet sensor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXL6UlohJH4uPhTQDNWDN%2Fpalletizing-p028-img02.jpg?alt=media)

![Figure 4.8 Install the base extension plates](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FytU6lNgBafnBHVWQ5X7m%2Fpalletizing-p028-img03.png?alt=media)

![Figure 4.9 Install the pallet side cover](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ9A2csSlIr9QAVK0tc15%2Fpalletizing-p028-img04.jpg?alt=media)

#### 4.4.2 Robot controller installation

1. Install the controller at the position shown in the figure below.

_Figure 4.10 Controller installation position_

2. Refer to the figure below to complete the wiring of the controller.

_Figure 4.11 Controller wiring_

![Figure 4.10 Controller installation position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCMVMigNVydURYI1VDpaP%2Fpalletizing-p029-img02.png?alt=media)

![Figure 4.11 Controller wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2ww4F5gWllpEZl3nT6Uv%2Fpalletizing-p029-img03.jpg?alt=media)

#### 4.4.3 Robot arm installation

1. Move the hoist so that the hook aligns with the central axis of the robot arm and is

positioned approximately 30–35 cm away from it.

2. Wrap the sling in a figure-eight pattern as shown in the diagram below.
3. Hang the sling from the robot arm onto the hook.
4. Operate the hoist to slowly lift the robot arm, ensuring that staff hold and support the

arm throughout the entire process.

![Official manual figure, page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmhSnJ7n8IkuvPXN2hOWO%2Fpalletizing-p030-img02.jpg?alt=media)

![Official manual figure, page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaRMBFeTVpwLKlNBnUmXy%2Fpalletizing-p030-img03.jpg?alt=media)

![Official manual figure, page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWCcwQPgkjP4m7S9QdfXy%2Fpalletizing-p030-img04.jpg?alt=media)

5. Hoist the robot arm to the top of the workstation cabinet, aligning the heavy-duty

cable toward the front panel of the workstation. Secure it using six M10\*25 screws.

![Official manual figure, page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FisqRxGMYlX09L9M09Utc%2Fpalletizing-p031-img02.jpg?alt=media)

![Official manual figure, page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5w31OmYrksNMiTVKwoel%2Fpalletizing-p031-img03.jpg?alt=media)

![Official manual figure, page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTE1Wqj8F3rnvoBReub7j%2Fpalletizing-p031-img04.png?alt=media)

_Figure 4.12 Install the robot arm_

6. Connect the heavy-duty cable placed next to the column with the interface of the

heavy-duty cable protruding from the robot base.

_Figure 4.13 Connect the heavy-duty cables_

![Figure 4.12 Install the robot arm](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGNsHBTySk2zzlRxU9vuw%2Fpalletizing-p032-img02.png?alt=media)

![Figure 4.13 Connect the heavy-duty cables](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnSg3K7dELwQI1O9QL6c6%2Fpalletizing-p032-img03.jpg?alt=media)

#### 4.4.4 End-of-arm suction cup installation

1. Install the end-of arm suction cup. Lock it with ten M&#x38;_&#x31;2 screws and one Ø&#x38;_&#x31;5 pin.

Refer to the figure below to install the suction cup. Then, connect the sensor cable attached to the suction cup to the aviation connector (X1) at the end of the robot arm.

**NOTE**

The direction of the X1 aviation connector must remain perpendicular to the suction cup's direction. Failure to do so may result in abnormalities during picking and placing operations.

_Figure 4.14 Install the suction cup_

2. Connect the air tube to the suction cup port.

![Figure 4.14 Install the suction cup](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUlaShLS58dgyjpfZTjqo%2Fpalletizing-p033-img02.jpg?alt=media)

![Official manual figure, page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvu25Jl12hrEcanPCm5oY%2Fpalletizing-p033-img03.jpg?alt=media)

_Figure 4.15 Connect the air tube_

3. Connect the pneumatic equipment (prepared by user, air flow ≥ 500L/min, air tube

diameter: 12mm) to the air source interface.

_Figure 4.16 Air inlet and power interface_

4. Connect one end of the power cable supplied with the device to the power interface

and the other end to the external power.

![Figure 4.15 Connect the air tube](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fa0wNuoffjaDJWJx0eVtw%2Fpalletizing-p034-img02.jpg?alt=media)

![Figure 4.16 Air inlet and power interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFOZ0o3SOoG784n4Y5KkP%2Fpalletizing-p034-img03.jpg?alt=media)

### 4.5 Installation of CR20A palletizing workstation

This section takes the installation of the CR20A Columnar Palletizing Workstation as an example. The other models of CR20A are installed in a similar way.

_Figure 4.17 Assembly diagram of the workstation_

#### 4.5.1 Base installation

1. Install the pallet barriers on both sides of the base and lock them with four M10\*20

screws.

_Figure 4.18 Install the pallet barriers_

2. Remove the plug of the pallet-in-position sensor from the base, route it through the

cable hole, and connect it to the sensor cable.

![Figure 4.17 Assembly diagram of the workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgpfWUkmzCPuxH6iQzksj%2Fpalletizing-p035-img02.png?alt=media)

_Figure 4.19 Connect the pallet sensor_

#### 4.5.2 Robot controller installation

1. Install the controller at the position shown in the figure below.

_Figure 4.20 Controller installation position_

2. Refer to the figure below to complete the wiring of the controller.

![Figure 4.19 Connect the pallet sensor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx7vXlqpj64lRtlHtFcqV%2Fpalletizing-p036-img02.jpg?alt=media)

![Figure 4.20 Controller installation position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0rHVKVI6sTz7qGOTtyt8%2Fpalletizing-p036-img03.png?alt=media)

_Figure 4.21 Controller wiring_

#### 4.5.3 Robot arm installation

The installation steps for the CR20A robot arm and the CR30A robot arm are identical. Please refer to "Robot arm installation" in Section 4.4.3.

#### 4.5.4 End-of-arm suction cup installation

Refer to "End-of-arm suction cup installation" in Section 4.4.4.

![Figure 4.21 Controller wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlZvNT4Iwk1Nsn3f6e3H3%2Fpalletizing-p037-img02.jpg?alt=media)

### 4.6 Conveyor installation

Install the conveyor on the front of the barriers of the palletizing workstation. The conveyor can be installed vertically or horizontally. It is necessary to use barriers or photoelectric sensors to ensure that the box will stop there when it reaches the picking point, and wait for the robot arm to pick up the box. The picking point should be within the reach of the end-of-arm suction cup and as close to the workstation as possible. There are no special requirements for the installation height of the conveyor. The installation method for the CR20A and CR30H palletizing workstations is the same. Here, the CR30H palletizing workstation is used as an example.

_Figure 4.22 Vertical conveyor_

_Figure 4.23 Horizontal conveyor_

![Figure 4.22 Vertical conveyor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Faa0VZ3xYtPn7BCrWlfJJ%2Fpalletizing-p038-img02.png?alt=media)

![Figure 4.23 Horizontal conveyor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4DSIvavjfLHHQgyRAJ7W%2Fpalletizing-p038-img03.png?alt=media)

### 4.7 Power on

1. After connection, flip the switch upwards to power on the workstation, as shown in the

figure below. The power switch can be locked to prevent accidental operation (the lock is user-prepared).

_Figure 4.24 Workstation main power switch_

2. Then press the ON/OFF button (on the top right of the controller) to start the controller.

Once the indicator lights on the end of the robot arm and the circular button on the controller both turn to solid blue, the workstation has powered on successfully. Fig 4.25 Controller ON/OFF button (CR20A) Fig 4.26 Controller ON/OFF button (CR30H)

![figure below. The power switch can be locked to prevent accidental operation (the lock](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEwhzpL08uGOwe7ENxOKy%2Fpalletizing-p039-img02.png?alt=media)

![Figure 4.24 Workstation main power switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7h87pFcAgkzFXT5KyEal%2Fpalletizing-p039-img03.jpg?alt=media)

![Official manual figure, page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkPYXh42Wa0EsW8Og6zR5%2Fpalletizing-p039-img04.jpg?alt=media)

**NOTICE**

* After power-on, press and hold the reset button on the workstation control panel to clear the emergency stop error.
* It is recommended to run the robot at low speed for about 5 minutes after power-on to warm it up before performing other operations. Setting the robot to 100% speed immediately after power-on may damage the robot.

## 5. Software Configuration

This chapter takes the PC control software (DobotStudio Pro) as an example to explain the operation method, which is basically the same as that of the App control software. For basic operations of DobotStudio Pro (such as connecting to the robot, enabling and jogging), please refer to its help document. The figure below shows the chapters of the document that correspond to the common operations in using the palletizing workstation.

_Figure 5.1 DobotStudio Pro help document_

### 5.1 Compatibility

If a version 2.4.0 or earlier of the palletizing plugin has been previously installed and configured, you must first uninstall the old version. Then, import and install version 2.4.1 of the plugin. After installation, the "Palletizing workstation settings" must be reconfigured.

### 5.2 Install and upgrade

1. After connecting the robot with DobotStudio Pro, open the Dobot+ page and import

the Palletizing plugin.

_Figure 5.2 Import the plugin_

![Figure 5.1 DobotStudio Pro help document](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVyjSniYXZaF79gApVKBo%2Fpalletizing-p041-img02.png?alt=media)

2. Click "Install" next to the palletizing process package to start the installation.

_Figure 5.3 Install the plugin_

The version installed at this point is the basic version. To upgrade to the Pro version, please follow the steps below: ① Navigate to the "Application" page in DobotStudio Pro, select "Palletizing" to open the palletizing process package.

_Figure 5.4 Access palletizing_

② Click "Upgrade to Pro version" or click any icon on the interface to enter the upgrade page.

_Figure 5.5 Upgrade to Pro version_

③ The differences between the basic and professional editions are displayed on the interface. Click "Upgrade" to proceed to the authorization page.

![Figure 5.3 Install the plugin](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGIAL0HwBa2hkRlh2kDfL%2Fpalletizing-p042-img03.jpg?alt=media)

![Figure 5.4 Access palletizing](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpKEOnJ15BA8Jx8oix3qF%2Fpalletizing-p042-img05.png?alt=media)

_Figure 5.6 Upgrade now_

On the authorization page, copy the device serial number and visit ④ dobotplus.dobot-robots.com. Enter the device serial number and activation code (please contact DOBOT technical support to obtain) on the webpage, then click "Get registration code".

_Figure 5.7 Copy the device serial number_

![Figure 5.6 Upgrade now](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ1ZzfQzVXVKVWYBviOVg%2Fpalletizing-p043-img02.png?alt=media)

![Figure 5.7 Copy the device serial number](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTRHfVbRAlWTM6C4Sq7vm%2Fpalletizing-p043-img03.png?alt=media)

_Figure 5.8 Get registration code_

Copy the generated registration code or save it as a file. ⑤

_Figure 5.9 Save the registration code_

Return to the authorization window, paste the registration code or import the file, ⑥ then click "Upgrade Now". Wait for the authorization and process package installation to complete successfully. A popup window will confirm the successful installation.

![Figure 5.8 Get registration code](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7W3yj0Jk2fMZPCgg1Vzm%2Fpalletizing-p044-img02.png?alt=media)

![Figure 5.9 Save the registration code](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFA5uFdeyqd0i9Ry4vPVQ%2Fpalletizing-p044-img03.png?alt=media)

_Figure 5.10 Upgrade authorization_

_Figure 5.11 Installation Successful_

### 5.3 Role

The palletizing process package implements access control based on the current role logged into DobotStudio Pro, preventing unauthorized personnel from modifying project settings. Permissions for different roles can be viewed in the palletizing process package under "Workstation settings > Permissions".

![Figure 5.10 Upgrade authorization](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpLhvLWoM70mTV327y60x%2Fpalletizing-p045-img02.jpg?alt=media)

![Figure 5.11 Installation Successful](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCcOUH4kKpzE2AzsvOb9Z%2Fpalletizing-p045-img03.png?alt=media)

_Figure 5.12 Current login role_

### 5.4 Palletizing workstation settings

Open the "Application" page in DobotStudio Pro and select "Palletizing" to access the palletizing process package.

_Figure 5.13 Palletizing_

If you're using the palletizing process package for the first time, or if you've recently replaced or adjusted the workstation hardware, you'll need to configure the workstation settings. Click " Workstation settings" at the top right corner of the palletizing process package homepage to open the settings page.

_Figure 5.14 Workstation settings_

![Figure 5.12 Current login role](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCwMZAhEvvuvX6s02UXZ6%2Fpalletizing-p046-img02.jpg?alt=media)

![Figure 5.13 Palletizing](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbT1WXH8ELUbqkB0AAYgr%2Fpalletizing-p046-img03.jpg?alt=media)

![Figure 5.14 Workstation settings](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2SfKFAKc5huzU7LLshdr%2Fpalletizing-p046-img05.png?alt=media)

#### 5.4.1 Basic settings

_Figure 5.15 Basic settings_

No. Module Description Choose the units for length and weight that will be used for the suction cup, pallet, and box parameters in the palletizing project. You can select either metric units (mm & kg) or Unit Ế imperial units (in & lb). When you change the units, all related parameters in the palletizing project will automatically be converted and updated. Workstation Select column or lifting column, suction cup type and size. See ế Hardware "Workstation hardware" for details.

* Palletizing height limit: When checked, allows setting the maximum stacking height for the current workstation. Minimum input limit: Machine height + Robot safe pose height + 50mm. Enable safety • Box collision detection: When checked, enables the Ề protection box collision detection function. If a collision or excessive offset is detected while editing a stacking pattern, a pop- up warning will appear (virtual simulation is recommended). Click "Cancel" to continue editing, or click "Save" to force save the stacking pattern. Pre-configured by default. No modification is required unless I/O signals the hardware configuration has been changed. For details on ề each I/O signal, see "I/O signals".

![Figure 5.15 Basic settings](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkxmA0bpEIq9M9Uuw0wOF%2Fpalletizing-p047-img02.jpg?alt=media)

Workstation hardware

_Figure 5.16 Set workstation hardware_

* Lifting column:

Select the type of lifting column based on the actual configuration of your palletizing workstation. The model selected for the fixed column is DT-PR-C-HSM-OV-20/30-02, and for the lifting column is DT-PR-L-TX-HSM-OV-20-02.

* Suction cup type:

Select the type of suction cup according to the actual one equipped with your workstation. ◦ Single-channel suction cups support single pick-and-place mode. ◦ Dual-channel suction cups support double pick-and-place and double-pick single-place modes. ◦ Triple-channel suction cups support triple pick-and-place, double pick-and-place, and single pick-and-place modes. ◦ Quad-channel suction cups support quadruple pick-and-place, triple pick-and- place, double pick-and-place, and single pick-and-place modes. Multi-channel suction cups require customization. If you have such a need, please contact DOBOT technical support for a technical evaluation.

* Suction cup size:

Set the size of suction cup based on the actual one equipped with your workstation. The height refers to the distance from the robot arm's end flange to the top surface of the box after it's picked up (approximately half the height of the suction nozzle). For details, refer to the illustration on the interface.

![Figure 5.16 Set workstation hardware](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBX3zsOiageptkOOcOjnh%2Fpalletizing-p048-img02.jpg?alt=media)

I/O signals Suction cup signal

_Figure 5.17 Suction cup signal_

* Suction cup 1/2/3/4 vacuum signal:

Signal to control the vacuum function of the suction cup for picking up boxes. For single-channel suction cup, you only need to configure the signal for Suction cup 1. For multi-channel suction cup, you need to configure multiple signals to control each channel independently. Select the signal according to the actual situation. The subsequent suction cup related signals follow the same principle, no more details in this document. DO\_14 and DO\_15 by default. If the wiring has been modified, please select according to the actual wiring.

* Suction cup 1/2/3/4 drop detection signal:

This signal comes from the drop detection sensor of the suction cup and is used to detect whether the suction cup has successfully picked up the material box and to monitor for dropped materials during the palletizing process. You can configure this signal if you enable drop detection function. If this function is not required, leave it unchecked. DI\_14 and DI\_15 by default. If your suction cup supports vacuum release detection, set this signal to the corresponding DI for that function.

* Suction cup 1/2/3/4 vacuum release signal:

Signal to control the vacuum release function of the suction cup for placing boxes. You can configure this signal if you enable the vacuum release function. If this function is not required, leave it unchecked. DO\_16 and DO\_17 by default. If the wiring has been modified, please select according to the actual wiring. Conveyor feeding signal

_Figure 5.18 Conveyor feeding signal_

![Figure 5.17 Suction cup signal](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCpxiMpi31LvglMRm8NdJ%2Fpalletizing-p049-img02.png?alt=media)

![Figure 5.18 Conveyor feeding signal](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0Kp2ljIWN0Rh2YNTeYcq%2Fpalletizing-p049-img03.png?alt=media)

It refers to the conveyor box sensor signal. You can configure up to two sensor signals for each conveyor. The palletizing workstation supports up to two conveyors. If only one conveyor is needed, you can skip the settings for Conveyor 2.

* For one placing method (e.g., all boxes are handled with single pick-and-place or multiple pick-and-place), you only need to configure one sensor signal.
* For two placing methods, you need to configure multiple sensor signals to indicate that Box 1/2/3/4 are arrived respectively. DI\_1 when the cable is connected to the Conveyor Sensor 1 interface on the I/O panel of the palletizing workstation, and DI\_6 when connected to the Conveyor Sensor 2 interface. See "Conveyor Sensor interface" for details. Pallet signal

_Figure 5.19 Pallet signal_

* Left pallet detection signal:

This signal detects whether the left pallet is properly in place. DI\_2 and DI\_3 by default. If the wiring has been modified, please select according to the actual wiring.

* Right pallet detection signal:

This signal detects whether the right pallet is properly in place. DI\_4 and DI\_5 by default. If the wiring has been modified, please select according to the actual wiring.

* New pallet (left/right) confirmation signal:

When "New pallet arrival confirmation signal" is checked, if a pallet is replaced, the corresponding new pallet confirmation button must be pressed before the robot arm starts working.

**NOTICE**

It is recommended to enable this function; otherwise, there is a risk that the robot arm may start moving while the pallet is being replaced.

* Left/Right pallet data reset signal:

When "Reset pallet data signal" is checked, if the reset signal for the left or right pallet is triggered, the pallet data for that side will be reset to the initial status:

![Figure 5.19 Pallet signal](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYlC1X6ruFDdjin7LYKm5%2Fpalletizing-p050-img02.png?alt=media)

◦ Palletizing scenario: Reset to Layer 1, 0 boxes. ◦ Depalletizing scenario: Reset to full layers, full boxes.

**NOTICE**

The "Left/right pallet data reset signal" is only responded to when the system is in the script stopped status. Safety signal

_Figure 5.20 Safety signal_

* Suction cup safety signal:

Disabled by default. When enabled, if the machine loses power during the placement process, the box will not fall off.

* Left/Right pallet LiDAR signal:

Disabled by default. When enabled, the LiDAR safety protection function for the corresponding pallet is activated. For details on LiDAR installation and configuration, refer to DOBOT Palletizing Workstation Safety Function Manual. Other signals

_Figure 5.21 Other signals_

* Interlayer pick-and-place signal:

If a separate signal is needed to control the suction cup for handling interlayer (e.g., using a dedicated suction nozzle), enable and configure this signal. DO\_22 by default. If the palletizing pattern does not include interlayer, or if a general suction cup signal can be used, you can leave this signal unchecked.

* Buzzer signal:

If selected, the buzzer will provide an alert in addition to the indicator light when palletizing is completed. The buzzer must be connected to the configured DO interface, with the factory default set to DO\_24.

* Wrapping Signal:

If selected, triggering the wrapping signal will pause the robot motion, allowing the operator to wrap the boxes. The factory default is DO\_19.

#### 5.4.2 Coordinates settings

_Figure 5.22 Coordinates settings_

No. Module Description A reference coordinate system based on the end-of-arm suction cup. Its origin is the center point of the contact Tool coordinate surface when the suction cup picks up a box, and its ① system orientation is the same as the flange tool coordinate system. See "Tool coordinate system" for details. A pallet user coordinate system label is included with the Pallet user shipment. Enter the pallet user coordinate system ② coordinate system according to the label. If recalibration is required, refer to "Pallet user coordinate system". Disabled by default. When enabled, there is no need to Picking point user separately teach the picking point. For instructions on ③ coordinate system creating a new user coordinate system for picking point, refer to "Picking point user coordinate system". Tool coordinate system When using for the first time, create a new tool coordinate system. Click "New" to choose either "Numeric input" or "Process teaching" to create the tool coordinate system.

**NOTE**

The controller supports a maximum of 50 tool coordinate systems. If all 50 coordinate slots are occupied, clicking "New" will display a warning message, and no further configurations can be added.

![Figure 5.22 Coordinates settings](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdliwPKcoLU0eEa9mGGBl%2Fpalletizing-p052-img02.jpg?alt=media)

Create a tool coordinate system via "Numeric input"

1. Click "New > Numeric input" to open the following page.

_Figure 5.23 Create a new tool coordinate system_

2. Enter the alias for the tool coordinate system and the values for X, Y, Z, RX, RY, and

RZ. Click "Save" to complete the process. Create a tool coordinate system via "Process teaching "

1. Click "New > Process teaching" to open the following page. Ensure the end-of-arm

suction cup is correctly installed, then click "Next". The illustration shows the robot arm with J6 at 0°.

_Figure 5.24 Suction cup installation method_

**NOTE**

This setup process applies only to the installation method mentioned above. If there is a rotation angle between the suction cup and the robot arm's end flange, you'll need to measure the angle and manually adjust it on the "Tool coordinate system settings" page in DobotStudio Pro.

2. After enabling the robot arm, use the jog function to align the center of the suction cup

with the center of the box (for dual-channel suction cup, treat the two boxes as a single

![Figure 5.23 Create a new tool coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkrIqWCzAWijiKqF6Cfg1%2Fpalletizing-p053-img02.png?alt=media)

![Figure 5.24 Suction cup installation method](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcIoROuRCAn2P5mf6iX8y%2Fpalletizing-p053-img03.jpg?alt=media)

unit to calculate the center point). Press the suction cup tightly against the box surface, and click "Suction". Once the suction cup picks up the box, click "Next".

_Figure 5.25 Pick up the box_

3. Measure and enter the suction cup offset values.

Measure the vertical distance from the robot arm's end flange to the top surface ① of the box, and enter this value as the "Z-offset" (if using an optional suction cup, this distance is about 110mm). Measure the offset from the center of the robot arm's end flange to the center of ② the box and enter it (if there is no offset, enter 0. If using an optional suction cup, set the "X- offset" to 10mm and leave the "Y offset" at 0mm).

_Figure 5.26 Set suction cup offset values_

4. After entering these values, click "Next".
5. Once the calibration is successful, you can release the suction cup on this page, then

enter an alias (optional) and click "Finish". The system will save the tool coordinate system and return to the coordinate system settings page.

![Figure 5.25 Pick up the box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkgEcw2Hkg34qauZhb180%2Fpalletizing-p054-img02.png?alt=media)

![Figure 5.26 Set suction cup offset values](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyrzKe2PN3chFhSHsiLsk%2Fpalletizing-p054-img03.jpg?alt=media)

_Figure 5.27 Save tool coordinate system_

6. After returning to the coordinate system settings page, the system will automatically

select the newly created tool coordinate system. Select/delete tool coordinate system Click the "Select" button next to the name of a tool coordinate system to select or delete a previously added tool coordinate system. When attempting to delete, a confirmation popup will appear. Once confirmed, the deletion cannot be undone.

_Figure 5.28 Select/Delete tool coordinate system_

![Figure 5.27 Save tool coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRmt5y035Qt3GMaMdFKjH%2Fpalletizing-p055-img02.png?alt=media)

![Figure 5.28 Select/Delete tool coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvDC1WQmbGOBVOP38lHTb%2Fpalletizing-p055-img03.png?alt=media)

![Official manual figure, page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZxPtEFool7xYxiqr5x9e%2Fpalletizing-p055-img04.png?alt=media)

Edit tool coordinate system Click "Edit" to view or modify the alias and coordinate values of the currently selected tool coordinate system. Tool coordinate system 0 is the flange tool coordinate system and cannot be modified.

_Figure 5.29 Modify tool coordinate system_

Pallet User coordinate system The palletizing workstation comes with pre-calibrated pallet coordinate systems. The left pallet coordinate system corresponds to User coordinate system 1 (User1), and the right pallet coordinate system corresponds to User coordinate system 2 (User2). The origin of these coordinate systems is on the ground, with the Z-axis pointing upward, as shown in the figure below.

![Figure 5.29 Modify tool coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdcSclhCJLmyB3vgH3NAf%2Fpalletizing-p056-img02.png?alt=media)

![Official manual figure, page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fljjtgz3YzDpuaM1MxHab%2Fpalletizing-p056-img03.jpg?alt=media)

_Figure 5.30 Pallet coordinate system_

The palletizing workstation is supplied with a pallet coordinate system instruction label. Please enter the left/right pallet user coordinate system values according to the label (Due to manufacturing variations, the specific coordinate values may differ for each workstation. Refer to the actual label for accurate values).

_Figure 5.31 User coordinate system (left/right pallet)_

You can click "Edit" to view or modify the alias and coordinate values of the currently selected user coordinate system.

_Figure 5.32 Modify user coordinates_

![Figure 5.30 Pallet coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaLbSwr5kd49sF3SR1t6T%2Fpalletizing-p057-img02.png?alt=media)

![Figure 5.31 User coordinate system (left/right pallet)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4uY5zZI4MqVsi31nM9Xw%2Fpalletizing-p057-img03.jpg?alt=media)

![Figure 5.32 Modify user coordinates](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4dALcqN4yc8qIETXRY6B%2Fpalletizing-p057-img04.jpg?alt=media)

If you need to recalibrate the user coordinate system due to inaccuracies in the factory default pallet coordinate system, click "New > Process teaching" next to the relevant coordinate system. Follow the following steps to create and calibrate a new user coordinate system:

1. Prepare the pallet and boxes that you will use in the actual application. Refer to the

diagram on the page and enter the sizes, then click "Next". If you're using a dual- channel suction cup, prepare two boxes and treat them as a single unit to calculate the sizes.

_Figure 5.33 Fill in Box and Pallet sizes_

2. After selecting the tool coordinate system for the suction cup, use the jog function to

align the center of the suction cup with the center of the box (for dual-channel suction cup, treat the two boxes as a single unit to calculate the center point). Press the suction cup tightly against the box surface, and click "Suction". Once the suction cup picks up the box, click "Next".

_Figure 5.34 Pick up the box_

3. Jog the robot arm and place the box in the position shown in the diagram (ensure that

the pallet is placed exactly as it will be in actual use, and there is no need to release the suction cup after the box is in place). Then, click "Obtain". Once all three points are obtained, click "Next".

![Figure 5.33 Fill in Box and Pallet sizes](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoxueeJPOWo5pAnpKLOhM%2Fpalletizing-p058-img02.jpg?alt=media)

![Figure 5.34 Pick up the box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHh7LmYbBL1d4Bm8Rj3l3%2Fpalletizing-p058-img03.jpg?alt=media)

_Figure 5.35 Obtain points_

4. Once the calibration is successful, you can release the suction cup on the page, then

enter an alias (optional) and click "Finish". The system will save the user coordinate system and return to the coordinate system settings page.

5. After returning to the coordinate system settings page, the system will automatically

select the newly created user coordinate system. The operations for selecting/deleting a user coordinate system are the same as those for the tool coordinate system. Picking point user coordinate system The "Picking point user coordinate system" function is disabled by default. When enabled, there is no need to separately teach the picking point.

**NOTE**

When boxes arrive on the conveyor belt flush against a certain edge, that edge and its vertex form a fixed coordinate axis. By teaching the conveyor user coordinate system, the system can automatically plan the center of the box as the picking point based on the entered box dimensions.

![Figure 5.35 Obtain points](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1JEok22E6W9aMeP2IvCW%2Fpalletizing-p059-img02.jpg?alt=media)

_Figure 5.36 Picking point user coordinate system_

**NOTICE**

"Picking Point 1 User Coordinate System" and "Picking Point 2 User Coordinate System" correspond to different conveyors. A coordinate system can be established for up to two conveyors. When only one conveyor belt is used, "Picking Point 1 User Coordinate System" is selected and used by default. If you need to create a picking point user coordinate system through teaching, click "New > Process teaching" on the right side of the corresponding coordinate system to create and calibrate a user coordinate system for the picking point. The steps are as follows:

1. Select the conveyor direction and click "Next".

* Outer → Inner:

The conveyor belt is perpendicular to the workstation, and the box approaches the robot from far to near.

* Left Right:

→ The conveyor belt is parallel to the workstation, and the box approaches the robot from left to right.

* Right Left:

→ The conveyor belt is parallel to the workstation, and the box approaches the robot from right to left.

![Figure 5.36 Picking point user coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA6lMBOhhSHVUR0fnx6FT%2Fpalletizing-p060-img02.jpg?alt=media)

_Figure 5.37 Select conveyor direction_

2. You need to determine the center of the box and mark the center point.

_Figure 5.38 Determine the center of the box_

3. Suction the box.

Select the tool coordinate system corresponding to the suction cup. ① Jog the robot to align the center of the suction cup with the center of the box ② (when using a dual-channel suction cup, calculate the center point by treating the two boxes to be picked up as a single unit). Ensure the nozzle is closely aligned with the surface of the box and click "Suction". ③ After the suction cup picks up the box, click "Next". ④

![Figure 5.37 Select conveyor direction](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ2DFU6vPaa4bcWzpgkmJ%2Fpalletizing-p061-img02.png?alt=media)

![Figure 5.38 Determine the center of the box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBshEu6lahmaLj9Ael1m2%2Fpalletizing-p061-img03.jpg?alt=media)

_Figure 5.39 Box suction_

_Figure 5.40 Suction center_

4. According to the conveyor direction display diagram, select the position where the box

is close to the conveyor belt, and click "Next".

![Figure 5.39 Box suction](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWHopeSvSuPYZU72LKhWX%2Fpalletizing-p062-img02.jpg?alt=media)

![Figure 5.40 Suction center](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIBrNe9jyXIUTxqSbYwaF%2Fpalletizing-p062-img03.jpg?alt=media)

_Figure 5.41 Select the position_

Fixed to the left edge Fixed to the right edge

_Figure 5.42 Fixed position for the box_

5. Measure the dimensions of the box in use, then click "Next" after filling in the

dimensions according to the schematic on the page.

_Figure 5.43 Input parameters for the box_

![Figure 5.41 Select the position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fkas75UVg6TTR9eLOQtp9%2Fpalletizing-p063-img02.png?alt=media)

![Figure 5.42 Fixed position for the box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0Xq3kKiJq6vp1oEz790z%2Fpalletizing-p063-img03.jpg?alt=media)

![Figure 5.43 Input parameters for the box](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkuA88acbupJhkvz7HvSN%2Fpalletizing-p063-img04.jpg?alt=media)

![Official manual figure, page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMdNs5FgCTbWGqiFDXRMe%2Fpalletizing-p063-img05.png?alt=media)

6. Jog the robot arm to move the box to the corresponding position shown in the

schematic (ensure the pallet placement matches the actual application, and do not release the suction cup once in position). Then click "Obtain". After three points are obtained, click "Next".

_Figure 5.44 Obtain the specified point_

_Figure 5.45 Positions for P1, P2 and P3_

7. The interface displays parameters of the picking point coordinate. Enter an alias if

needed.

_Figure 5.46 Calibration result_

8. Result verification.

The interface displays the box dimensions and schematic picking points. When ① the box dimensions are modified, the picking point values update in real time upon entering the new length/width/height.

![Figure 5.44 Obtain the specified point](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm1boAtNiwvcY3RhIuaxm%2Fpalletizing-p064-img02.jpg?alt=media)

![Figure 5.45 Positions for P1, P2 and P3](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlGUH0t4UMmyBKvdF721i%2Fpalletizing-p064-img03.jpg?alt=media)

![Figure 5.46 Calibration result](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3eEAI7mDd9D1XglEuFzn%2Fpalletizing-p064-img04.jpg?alt=media)

![Official manual figure, page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJHKNOrHnztZX9fcu83Mm%2Fpalletizing-p064-img05.jpg?alt=media)

Click "Re-obtain" to compare the current robot position with the generated picking ② point coordinate system, automatically updating the latter. After validating picking point for single suction, click "Dual Suction" to validate ③ picking point for dual suction. Click "Finish" to save the user coordinate system for the picking points and return ④ to the coordinate system configuration page.

_Figure 5.47 Result verification_

Upon returning to the coordinate system configuration page, the system will automatically select the newly created picking point user coordinate system. The operations for selecting, editing, and deleting picking point user coordinate systems are the same as those for Pallet user coordinate system.

#### 5.4.3 Automatic transition points

The current version of the palletizing process package supports the "Automatic transition point" function. When enabled, there is no need to manually set transition points for each project. The robot will automatically generate transition points for each material box through an algorithm, optimizing efficiency and reducing configuration complexity.

**NOTE**

Before using the automatic transition point function, ensure the robot can detect potential collisions with the workstation or other obstacles during palletizing. Confirm the relative positions of the workstation and the conveyor, as well as the safety zone. Motion trajectory with/without transition points When the robot arm moves directly from the picking point to the placing point in a straight- line trajectory and there is a risk of collision, you need to manually set transition points within the safety zone. The robot arm will bypass obstacles by moving from the picking point to the placing point via the transition point, ensuring the optimal trajectory. Below is an example of motion trajectories with and without transition points, using left-side palletizing as a reference:

![Figure 5.47 Result verification](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4LoJZLGBLs8W03XSOYEF%2Fpalletizing-p065-img02.png?alt=media)

Fig 5.48 Trajectory with transition points Fig 5.49 Trajectory without transition points Set automatic transition points On the "Workstation settings" page, click "Auto-Transition" to enable or disable the automatic transition point function, and configure parameters for conveyors, safety zones, and obstacles.

_Figure 5.50 Automatic transition points page_

No. Module Description "OFF" by default. When enabled, the layer transition points Enable Auto- in the point setting module can be set to "Custom" (i.e., ① transition points manual teaching) or "Auto-Generated". The robot will move according to the "Diagram of the trajectory through the

![Figure 5.50 Automatic transition points page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZnY2gWBHOML6t21xWhDV%2Fpalletizing-p066-img02.jpg?alt=media)

![Official manual figure, page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxykmlutLNyC95XRHyIqb%2Fpalletizing-p066-img03.png?alt=media)

No. Module Description automatic transition point ". For teaching points related to conveyors, safety zones, Calibration pin and obstacles, it is recommended to use the calibration pin ② height included with the workstation. If the calibration pin is not used, set the height to 0.

* Select the number and direction of conveyors.
* Configure the length, width, and height of the conveyors (range: 0–1700 mm). If the dimensions Conveyor belt exceed 1700 mm, the system will cap them at 1700 ③ parameters
* Use jog mode in DobotStudio Pro to obtain the teaching point for the conveyor (A1). See "Get conveyor teaching point" for details. The safety zone must be within the robot's motion range. Its length and width may overlap with the pallet or conveyor (range: 0–1700 mm). The height is automatically calculated by the robot and must exceed the conveyor Safety zone height. No other objects are allowed in the safety zone, ④ parameters otherwise collision risks may occur. Two safety zones are pre-defined by default. If the predefined zones do not match the actual site conditions, edit them accordingly. See "Teach safety zone range" for details. If equipment within the robot's reachable range poses a Obstacle collision risk, add the obstacles through "Add obstacle" to ⑤ parameters inform the robot. The robot will plan its trajectory to avoid the obstacles. Get conveyor teaching point

1. Attach the calibration pin to the robot.
2. Drag the robot's end-effector close to point A1.
3. Use DobotStudio Pro's jog panel for fine adjustments, aligning the calibration pin with

A1. Ensure the flange surface is parallel to the base (RX=180°, RY=0°), as shown below.

_Figure 5.51 Obtaining teaching point for the conveyor_

**NOTE**

The diagrams in the process package will update automatically based on the selected conveyor number and direction. Follow the actual diagrams for calibration. Teach safety zone range Teach the safety zone range (Example: Left safety zone):

1. Confirm the dimensions of the safety zone.
2. Based on the actual situation, select a point above the conveyor surface as the

teaching point (B1).

3. The robot will automatically generate a safe space above the teaching point based on

its motion range and the palletizing height, as shown below.

_Figure 5.52 Teaching the safety zone range_

Add obstacle Click "Add obstacle" to access the following interface (up to 4 obstacles can be added). Enter the obstacle name, dimensions (length and width: 0–1700 mm, height: 0–3000 mm), and obtain the teaching points for the obstacle.

![Figure 5.51 Obtaining teaching point for the conveyor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBopwZm4BzvXqSayAwMgv%2Fpalletizing-p068-img02.jpg?alt=media)

![Figure 5.52 Teaching the safety zone range](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7CwLqIjcL16lQalNQDmn%2Fpalletizing-p068-img03.png?alt=media)

_Figure 5.53 Add obstacle_

How to get the teaching points for the obstacle:

1. Attach the calibration pin to the robot.
2. Drag the robot's end-effector close to point C.
3. Use DobotStudio Pro's jog panel for fine adjustments, aligning the calibration pin with

point C. Ensure the flange surface is parallel to the base (RX=180°, RY=0°).

**NOTE**

* The point C for different obstacles (irregular objects are treated as cubes, as shown by the blue box) is always at the upper-right corner of the cube, as illustrated below.
* If the obstacle height exceeds the robot's reachable height, select a point at the robot's maximum reachable height in the upper-right corner, as illustrated below.

![Figure 5.53 Add obstacle](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvP9Y0dJ5dYqFEgJzQ9Ye%2Fpalletizing-p069-img02.jpg?alt=media)

![Official manual figure, page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoE8VHAssJRAGoeZmQLg2%2Fpalletizing-p069-img04.jpg?alt=media)

![Official manual figure, page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXzhxm4XWH54NQ5NOGgxb%2Fpalletizing-p069-img05.jpg?alt=media)

**NOTE**

When the automatic transition point is enabled, the height protection for the picking point is automatically activated and triggered during reachability detection. The height of the picking point is calculated using the following formula, and if the height requirement is not met, a prompt will appear on the interface. Picking point height ≥ Conveyor teaching height + Box height - Calibration pin height

#### 5.4.4 Permissions

The table below outlines the functions available to different roles (Administrator/Technician/Operator).

_Figure 5.54 Permissions_

Current Role: The Role displayed is consistent with the role shown in the device status bar on DobotStudio Pro's home page. Functions available to the different roles:

* Administrator: Can access all functions of the palletizing process package.
* Technician: Can use all functions except those related to manufacturer configuration.
* Operator and Custom role: Can only select, start, pause, or stop projects. They can also modify the palletized/unpalletized layers and box quantities on the process package home page's run panel. They cannot manage or debug palletizing projects, configure palletizing workstations, or perform manufacturer-level configurations.

![Figure 5.54 Permissions](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLVG71QS6D56FWalqLqhP%2Fpalletizing-p070-img02.png?alt=media)

### 5.5 Product management

Click "Product management" on the home page to open the product library. Add products in advance (including box dimensions, number of layers, number of boxes, and stacking pattern). When creating a new palletizing project later, you can directly select a product that has already been added here without having to re-enter the information.

_Figure 5.55 Product management_

No. Module Description Enable OFF by default. When it is ON, you can view, search, Product import/export, delete, copy, edit, and create new stacking ① Management patterns. Displays the name, box dimensions, number of layers, number of boxes, and thumbnails of Pattern A/B for existing Product list products. The first product is selected by default. Click the ② icon to modify the product name. When a product is selected from the product list, the 3D stacking pattern of that product is displayed on the right. The 3D product default view is from a top-down perspective, but you can drag ③ image the mouse to change the viewing angle. Pallet dimensions and box dimensions are displayed. Enter keywords in the input box to filter products whose names contain the keywords. After filtering, the first pattern is Search selected by default. ④ product Search results can be sorted by creation time (newest first), total number of boxes (highest first), or by pattern name. Results can also be filtered by suction cup type.

![Figure 5.55 Product management](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfBhIciBtFAGHsqIEBaNf%2Fpalletizing-p071-img02.png?alt=media)

![Official manual figure, page 71](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyOY1j9Yv0PZgl0EF33GM%2Fpalletizing-p071-img03.jpg?alt=media)

No. Module Description Click "Import", select the file from the path where the product Import file is located, and add external products to the current ⑤ product product library. Click "Export" to export all products from the product library. Export Customize the save path and file name. The default file name ⑥ product is "Dobot Pattern Library + Export Time.json". Select a product and click "Delete". A confirmation pop-up will Delete appear. After deletion, the first product in the list will be ⑦ product automatically selected. Select a product and click "Copy". The copied product will be named "Original Name\_1" by default. The creation time is set Copy product ⑧ to the time the copy was completed. After copying, the new product will be automatically selected. Select a product and click "Edit". The interface will redirect to Edit product ⑨ the box/pallet parameter settings page. The process for creating a new product is the same as configuring parameters for a new palletizing project. The box Create dimensions and pallet dimensions from the last created ⑩ product pattern will be automatically filled in. When the number of patterns reaches 100, clicking "New" will prompt that a new pattern cannot be created.

### 5.6 New palletizing project (without interlayer)

_Figure 5.56 Workflow for a New Palletizing Project Without Interlayer_

#### 5.6.1 Set basic parameters

1. Click "New project" in the upper-right corner of the home page. To import an existing

project, click "More projects" and import from the project list page.

_Figure 5.57 New palletizing project_

2. Configure the basic parameters according to the actual application scenario. You can

preview the configuration results in real time via the 3D model on the right side of the

![Figure 5.56 Workflow for a New Palletizing Project Without Interlayer](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKg4hZioGc72tbW9oLdSh%2Fpalletizing-p072-img02.png?alt=media)

interface. Once configuration is complete, click "Next" to proceed to the box/pallet settings page.

_Figure 5.58 Project basic parameters (without interlayer)_

Palletizing mode Select the palletizing mode based on the actual number of pallets and conveyors in your application. In "2 Conveyors 2 Pallets" mode, each conveyor is paired with a specific pallet. When palletizing, boxes from Conveyor 1 will be stacked onto the left pallet, and boxes from Conveyor 2 will be stacked onto the right pallet. The same logic applies to depalletizing.

**NOTE**

* In "1 Conveyor 2 Pallets" mode, when both pallets are in position, first complete the full stack on the left pallet, then stack the right pallet.
* "2 Conveyors 2 Pallets " mode is suitable for scenarios where the two conveyor lines have similar throughput and box sizes are roughly the same. A buffer zone must be set up on the conveyors to manage material backlogs.
* In "2 Conveyors 2 Pallets " mode, when both pallets are in position, the workstation will alternate stacking between the two pallets. See"2 Conveyors 2 Pallets" debugging for details. Palletizing type
* Palletizing: Pick the boxes from the conveyor and stack them on the pallet.
* Depalletizing: Remove boxes from the pallet and place them onto the conveyor. The parameters need to be configured are similar to palletizing, with only some point definitions differing.
* Demo mode: Available only when the palletizing mode is "1 Conveyor 2 Pallets".

Used to demonstrate the palletizing workstation at trade shows. Other accessories

* Conveyor direction: Set the direction of the conveyor relative to the workstation based on your actual application. When the palletizing mode is "2 Conveyors 2 Pallets", only "Outer → Inner" is available. ◦ Outer Inner: The conveyor is perpendicular to the workstation. Boxes → approach the robot arm from far to near.

![Figure 5.58 Project basic parameters (without interlayer)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn0vXldT6hmlObNNW4TAd%2Fpalletizing-p073-img02.jpg?alt=media)

_Figure 5.59 Outer → Inner_

◦ Left Right: The conveyor is parallel to the workstation. Boxes approach the → robot arm from left to right.

_Figure 5.60 Left → Right_

◦ Right Left: The conveyor is parallel to the workstation. Boxes approach the → robot arm from right to left.

_Figure 5.61 Right → Left_

* Interlayer: For palletizing, select based on whether interlayers are needed between layers of boxes. For depalletizing, select based on whether the stack to be depalletized contains interlayers. When "With Interlayer" is selected, refer to "Set

![Figure 5.59 Outer → Inner](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyyiskR4HdKNn1PuFoYCv%2Fpalletizing-p074-img02.jpg?alt=media)

![Figure 5.60 Left → Right](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw1OG210Zj2Yk9ZtMjkfs%2Fpalletizing-p074-img03.jpg?alt=media)

![Figure 5.61 Right → Left](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeZXotIeBz5nyR6XDPEoH%2Fpalletizing-p074-img04.jpg?alt=media)

interlayer coordinate system" to select an appropriate user coordinate system for the interlayer.

* Box type: The "Two sizes" option is available only when the palletizing mode is "2

Conveyors 2 Pallets". Each box size is paired with one specific conveyor and one pallet. For example, the boxes arriving on Conveyor 1 must be of the same size and are only stacked onto the left pallet.

#### 5.6.2 Set box/pallet parameters

_Figure 5.62 Box/pallet parameter_

Box parameter

_Figure 5.63 Box parameters_

Parameter Description Enter the actual box dimensions (length should be greater than width; use "Rotate 90°" to adjust box direction) or select an existing product. Click "Choose existing product" to navigate to the "Product Box size management" page. The system will automatically display the box dimensions, weight, and stacking pattern when a corresponding product is selected. Enter the actual weight of the box, or it will be automatically entered Weight when an existing product is selected. Click "Rotate 90°" to adjust based on the actual direction of Box direction incoming boxes on the conveyor (long side forward / short side forward). The adjustment effect can be previewed in the 3D model

![Figure 5.62 Box/pallet parameter](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9YuaOCQsSxAogqjwK8m9%2Fpalletizing-p075-img02.jpg?alt=media)

![Figure 5.63 Box parameters](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgtUY6PbMMOelxKsao9nf%2Fpalletizing-p075-img03.png?alt=media)

Parameter Description on the right of the interface. To design the stacking pattern based on the label’s position on the box, select the direction of the box face where the label is located (based on the conveyor forward direction). Once Label direction selected, the label direction will be visible in the 3D model and subsequent stacking pattern editor. Fig 5.64 Label direction (Front)

**NOTE**

The "Choose existing product" button for "Box size" will only appear if you have added products in "Product management" page in advance; otherwise, this button will not be shown. In "2 Conveyors 2 Pallets" mode, if two box sizes are selected, each must be configured separately. "Box 1 size" corresponds to the size of the box to be palletized on the left pallet, "Box 2 size" corresponds to the size of the box to be palletized on the right pallet.

_Figure 5.65 Box parameter\_Two sizes_

Pallet parameter

_Figure 5.66 Pallet parameter (Single side)_

![Figure 5.65 Box parameter\_Two sizes](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxCvgXyHY9IkBcHdnXZMx%2Fpalletizing-p076-img02.jpg?alt=media)

![Figure 5.66 Pallet parameter (Single side)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNEIwfFrRXmuKQ0CBTvFT%2Fpalletizing-p076-img03.png?alt=media)

Select the corresponding pallet size from the dropdown menu, or select "Custom" and manually enter the pallet length, width, and height. In "2 Conveyors 2 Pallets" mode with two box sizes, the pallet sizes for the left and right sides can be set independently.

_Figure 5.67 Pallet parameter (Both side)_

**NOTE**

Pallet size affects the minimum palletizable box size. For more details, refer to the recommended minimum box size in "Technical specifications".

#### 5.6.3 Set stacking pattern

Based on the box size and label direction for each product, users can design the layout of boxes on the pallet. Some products require the same layout for each layer, while others may require different layouts for different layers. This three-dimensional arrangement of boxes is called "stacking pattern". The DOBOT Palletizing Process Package is pre- configured with 2 patterns and supports user-defined patterns, allowing users to add up to 3 additional patterns.

_Figure 5.68 Pattern_

* For one box size: The stacking pattern is the same for both left and right pallets. You can switch the perspective of the diagram (left/right pallet) through the drop-down menu.
* For two box sizes: You need to set the stacking patterns for the left and right pallets separately. Set the left pallet’s pattern based on the size of Box 1, and the right pallet’s

![Figure 5.67 Pallet parameter (Both side)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fk47iwS1NyPjWBZUN6ycu%2Fpalletizing-p077-img02.jpg?alt=media)

![Figure 5.68 Pattern](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3XYee8uM6Isn4HulNOQ4%2Fpalletizing-p077-img03.jpg?alt=media)

pattern based on the size of Box 2.

_Figure 5.69 Pattern settings (One size)_

* Click the "+" button next to "Pattern A" or "Pattern B" to add a new pattern (up to three additional patterns). Each pattern represents the arrangement of boxes for one layer. When configuring the palletizing method later, you can set the number of layers and assign a pattern for each layer.

_Figure 5.70 Add pattern_

* Click "Auto pattern" to select a recommended pattern that automatically generated by the system. Click "Edit" to modify the current pattern.

**NOTE**

If the box sizes have not been set, clicking "Auto pattern" will display a pop-up message: "Please confirm the pallet and box size first". Auto pattern The "Auto pattern" function is only applicable to scenarios where only one box is picked up at a time.

![Figure 5.69 Pattern settings (One size)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzOj3U5BE7dpARMmxLEsY%2Fpalletizing-p078-img02.png?alt=media)

_Figure 5.71 Recommended pattern_

Parameter Description Min Box Spacing The minimum distance between boxes. Unit: mm. Default: 5 mm. Min Top/Bottom The minimum distance between the boxes and the top/bottom Pallet Spacing edges of the pallet. Unit: mm. Default: 5 mm. Min Left/Right The minimum distance between the boxes and the left/right Pallet Spacing edges of the pallet. Unit: mm. Default: 5 mm. Default is "No". If "Yes" is selected, boxes may overhang the Exceed the edge pallet edge. The maximum overhang is 40% of the box’s shorter side.

* The system will automatically generate recommended patterns based on the parameters you’ve set. If you modify any of these parameters, click "Regenerate pattern" to update the recommended patterns accordingly.

**NOTE**

No recommended pattern is available for extreme parameters. The system will display the message: "There is no recommended palletizing pattern under the current parameters, please reset the parameters."

* After selecting a pattern, click "Save" to exit the auto pattern page. The selected pattern will be loaded onto the current pattern after automatically generating placement order, offset direction, and offset distance. If no recommended pattern is available, the "Save" button is disabled.

**NOTE**

For patterns generated automatically, the Z-axis offset value defaults to the height of a single box.

![Figure 5.71 Recommended pattern](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOaxns12DIiQqmi5viCA6%2Fpalletizing-p079-img02.jpg?alt=media)

* After selecting a pattern, click " Save and Edit " to enter the pattern editing page. The selected pattern will be loaded onto the current pattern after automatically generating placement order, offset direction, and offset distance. You can modify the selected pattern as needed. If no recommended pattern is available, the "Save and Edit" button is disabled.
* Quick apply:

_Figure 5.72 Quick apply_

◦ If the "Selected pattern" option is unchecked, the associated dropdown menu will be grayed out and disabled. ◦ If the "Selected pattern" option is checked, the selected pattern can be rotated 180° (default), mirrored, and quickly applied to a specified pattern upon saving. ◦ The pattern dropdown menu does not include the current pattern. For example, if you entered "Auto pattern" page from Pattern A, the dropdown menu will only display options other than Pattern A. Edit pattern

_Figure 5.73 Edit pattern_

No. Description Switch to the pattern you want to edit. ① "Copy/Paste" button: Used to copy the current pattern to another one. ② Displays a preview of the current pattern. ③

![Figure 5.72 Quick apply](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F46iyywFVYPHKE4S56k24%2Fpalletizing-p080-img03.png?alt=media)

No. Description Define how the suction cup picks up and places the boxes. Options: "Single Pick-and-Place" (Pick One, Place One), "Dual Pick-and- Place" (Pick Two, Place Two), "Double Suction, Single Place" (Pick Two, Place One), "Triple Pick-and-Place" (Pick Three, Place Three), "Quadruple Pick-and-Place" (Pick Four, Place Four). ④ For "Double Suction, Single Place" (Pick Two, Place One): When adding boxes, boxes in the same group must have the same serial number. When deleting, boxes in the same group are deleted together. One-click generation and manual modification of serial numbers are not supported. See "Edit box placement pattern" for details. ⑤

* Yes: Boxes may overhang the pallet edge, up to a maximum of 40% of the box's shorter side (points are reachable but at the limit; improper placement direction or offset may cause collisions). ⑥
* No: If there are already boxes overhanging the pallet edge, they will be automatically adjusted to align flush with the pallet edge. See "Set placement order and offset direction" for details. ⑦ See "Set placement direction and offset" for details. ⑧ Edit box placement pattern

_Figure 5.74 Box placement_

* Add box:

Click "Add box" to add a box to the pallet area in the diagram (for "Dual Pick-and- Place" mode, two boxes are added at a time, but they are treated as a single unit. The same logic applies to "Triple Pick-and-Place" and "Quadruple Pick-and-Place" modes). A maximum of 50 boxes can be added to one pattern.

![Figure 5.74 Box placement](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOSbM5hk1S826yiW2fomM%2Fpalletizing-p081-img02.png?alt=media)

_Figure 5.75 Box icon_

◦ The blue line next to the box indicates the box label (if set to "No label" when configuring the box parameter, there will be no blue line). ◦ The number on the top left indicates the box placement order. ◦ The icon in the center of the box indicates the placement direction (see below for details).

* Multi-select / Select All:

You can select boxes as follows: ◦ Click a box in the pallet area to select it when not in multi-select mode. ◦ Click "Multi-select" to enter multi-select mode, and the button changes to "Cancel Multi-select". Click multiple boxes in the pallet area to select or deselect them. Click "Cancel Multi-select" to exit multi-select mode. ◦ Click "Select All" to select all boxes on the current pallet. When a box is selected, a blue border will appear around it, and the distance to the nearest box or pallet edge will be displayed.

_Figure 5.76 Box selected_

* Quick actions:

Set the box jog distance. Unit: mm. Direction keys, used to jog the selected box. Delete the selected box. Rotate the selected box 90° clockwise, the box label will rotate accordingly. When label direction is set to "No label", rotation options are 0° and 90° clockwise. When label direction is set to "With label", rotation options are 0°, 90°, 180°,

![Figure 5.75 Box icon](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRiI374o7M4ddUfVfZBv2%2Fpalletizing-p082-img02.png?alt=media)

![Figure 5.76 Box selected](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDBtgkbBbaYKW36NugsK1%2Fpalletizing-p082-img03.png?alt=media)

and 270° clockwise. Align the selected box in the specified direction (left/right/down/up). The selected box will align with the edge of the nearest box in that direction. If there is no other box in that direction, it will align with the pallet edge. Move all boxes in the current pattern as a single Center unit to the center of the pallet.

**NOTE**

If any boxes overlap, the corresponding box icon will display in red. Set placement order and offset direction

_Figure 5.77 Placement order and offset direction_

* Click the "Quick Generation" button to open a window with sorting rule options. Select the rule that meets your needs. The specific options are listed below: ◦ From Far to Near, From Top to ◦ From Far to Near, From Bottom to Bottom Top

![Figure 5.77 Placement order and offset direction](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZxIRxPE5nu6M9EMiEVBx%2Fpalletizing-p083-img03.png?alt=media)

![Official manual figure, page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXONZd66CKAENaFFd3PPc%2Fpalletizing-p083-img05.png?alt=media)

◦ From Near to Far, From Top to ◦ From Near to Far, From Bottom to Bottom Top

* Use the dropdown menu to set the placement order for the currently selected box. The robot arm will place boxes one by one according to the numerical order. Set placement direction and offset

_Figure 5.78 Placement direction diagram_

When unloading, the robot arm will approach the point directly above the placing point from a specified direction, and then place down the boxes. You can click the icon next to "Direction & Offset settings" to view a dynamic diagram. "Direction & Offset settings" is used to set the direction and distance of the approach point relative to the point directly above the placing point.

![Figure 5.78 Placement direction diagram](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3FTIwiBuVNw29gomgDFw%2Fpalletizing-p084-img02.jpg?alt=media)

![Official manual figure, page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4JrzRYTtYvZF1MPZOjPG%2Fpalletizing-p084-img03.jpg?alt=media)

![Official manual figure, page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW23GLbO4Q9QQf4SW4Lcc%2Fpalletizing-p084-img04.jpg?alt=media)

![Official manual figure, page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F93eSTfPzQukd0SArXCan%2Fpalletizing-p084-img05.jpg?alt=media)

![Official manual figure, page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0GDGfkf6krUegWDNYjD1%2Fpalletizing-p084-img06.jpg?alt=media)

**NOTE**

For double pallets, the offset direction and offset distance set here are based on the current pallet's perspective. The corresponding values for the opposite pallet will be automatically mirrored left-right by the software. The direction settings are generally used to prevent interference between boxes during unloading, which could affect the palletizing quality. It is recommended to start with the default settings and fine-tune them based on the actual palletizing results during system debugging.

* When "Placing direction" is set to "Same", all boxes will approach the point directly above the placing point from the same direction. You can configure a uniform placement direction and offset for all boxes.

_Figure 5.79 Placement direction & offset settings (All boxes)_

* When "Placing direction" is set to "Separate", you need to select each box individually to set its specific placement direction and offset.

_Figure 5.80 Placement direction & offset settings (One box)_

Offset: The absolute value of the offset between the approach point and the point directly above the placing point. Unit: mm. Value range: \[0, 1500]. Different approach directions require different offset settings; offsets that do not need to be set cannot be modified. Example:

* For boxes with approach direction , offsets in all directions (X, Y, Z) can be set.

![Figure 5.79 Placement direction & offset settings (All boxes)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F30O8BuijdtLNwWX9cOvr%2Fpalletizing-p085-img02.png?alt=media)

![Figure 5.80 Placement direction & offset settings (One box)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLoF4zLD4igLO0uG50i14%2Fpalletizing-p085-img03.jpg?alt=media)

* For boxes with approach direction , offsets in the Y and Z directions can be set.
* For boxes with approach direction , only the Z offset can be set.

If the direction and offset are not set, the system defaults to an approach direction of (directly above) for all boxes with an offset of 0 mm. After completing the pattern settings, click "Save" to save the current settings.

#### 5.6.4 Layer settings

_Figure 5.81 Layer settings (One box)_

Set the number of layers for palletizing/depalletizing and the pattern used for each layer according to your actual needs. When there are two box sizes, you need to set the palletizing/depalletizing method separately for the left and right pallets.

_Figure 5.82 Layer settings (Two boxes)_

![Figure 5.81 Layer settings (One box)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0zaPdu7EyBciV2JHNkKr%2Fpalletizing-p086-img05.png?alt=media)

![Figure 5.82 Layer settings (Two boxes)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsXYEWENklklahakmumTj%2Fpalletizing-p086-img06.png?alt=media)

#### 5.6.5 Point settings

_Figure 5.83 Point settings_

You should refer to the instructions and illustrations on the page to set the picking points (placing points for depalletizing) and transition points. Click "3D-Preview" to view the recommended point positions in the 3D model on the right. Click the button again to hide the points in the 3D model.

_Figure 5.84 Preview 3D illustration_

The point where the robot arm picks up boxes from the conveyor during palletizing is referred to as the picking point. During depalletizing, the corresponding point where boxes are placed onto the conveyor is called the placing point. This section will focus on the picking point as an example. The picking point is a fixed point. Therefore, the conveyor belt must be secured to the floor to prevent its position from changing. Additionally, barriers and guide rails should be used to ensure that the boxes stop at a fixed position at the end of the conveyor, ready for the robot arm to pick them up. The following figure illustrates an example of using guide rails to fix the position of the boxes:

* One side of the conveyor has a fixed guide rail for aligning the boxes.
* The other side of the conveyor has an adjustable guide rail to guide the boxes into the correct position. The position of this rail should be adjusted based on the actual width of the boxes.

![Figure 5.83 Point settings](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgnQKUoLoKRItURN3d6F1%2Fpalletizing-p087-img02.jpg?alt=media)

![Figure 5.84 Preview 3D illustration](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj4bEY7lG2k2ybv9PUNOd%2Fpalletizing-p087-img03.jpg?alt=media)

_Figure 5.85 Conveyor guide rail example_

For depalletizing, guide rails are not required, you just need to ensure the placing point is located on the conveyor. Picking point / Placing point The coordinates of the picking point/placing point displayed on the interface are based on the left pallet coordinate system. Place the box on the conveyor. Jog the robot arm so that the end-of-arm suction cup is flush against the box, with the box center vertically aligned with the suction cup center (for dual suction cups, treat the two boxes to be picked as a single unit to calculate the center). The long side of the suction cup must be parallel to the long side of the box. Once the robot arm is in position, click "Obtain". If the long or short side of the box is parallel to the palletizing workstation, set Rz to 90° or 180° to avoid abnormal rotation.

_Figure 5.86 Picking point settings_

In "2 Conveyors 2 Pallets" mode, picking/placing points for both conveyors must be set separately.

_Figure 5.87 Picking point settings\_2 conveyors_

![Figure 5.85 Conveyor guide rail example](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0Nqxt7iWjodaT1rVLMlY%2Fpalletizing-p088-img02.png?alt=media)

![Figure 5.86 Picking point settings](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC1SLJ4eVuvmyDLEXNoxV%2Fpalletizing-p088-img03.png?alt=media)

![Figure 5.87 Picking point settings\_2 conveyors](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8qsBzLBIqYNjYLwn1c0L%2Fpalletizing-p088-img04.png?alt=media)

During palletizing, boxes picked from Conveyor 1 will only be stacked onto the left pallet, and boxes from Conveyor 2 will only be stacked onto the right pallet. The same principle applies to depalletizing. Please set the points according to your on-site configuration. Layer transition point

_Figure 5.88 Custom layer transition point_

Layer transition points are points that the robot arm passes through during the process of picking a box and placing it. They are generally used to control the robot's motion trajectory to avoid obstacles.

* Custom layer transition points (default settings)

By default, the "Custom" option for the layer transition point is selected. After jogging the robot arm to the desired point, click "Obtain" next to the transition point (e.g., T1) to obtain its position. Transition points for the left and right sides must be configured separately. Each side requires at least 1 transition point and supports up to 5 transition points. The coordinates of the transition points displayed on the interface are based on the pallet coordinate system on the corresponding side (left/right). In depalletizing mode, the order in which the transition points are added is opposite to the order in which the robot arm moves.

**NOTE**

The height of the transition point set here is the height of the transition point corresponding to the first layer of boxes. During actual operation, the system automatically adjusts the height of the transition point based on the number of layers being palletized or depalletized. If more than one transition point is set on one side, selecting any transition point will display a "Delete" button. Click it to delete the selected transition point.

![Figure 5.88 Custom layer transition point](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F76zzAiNHdm4K2ygVluRj%2Fpalletizing-p089-img02.png?alt=media)

_Figure 5.89 Delete transition point_

It is recommended to set two transition points per side: one outside the pallet and another inside the pallet, both positioned higher than the point above the picking point. Please set these points based on the actual scenario to ensure smooth robot motion without collisions. While point settings may vary slightly depending on the conveyor installation method, the overall principle remains the same. It is recommended to refer to the aforementioned 3D illustration for configuration.

* Auto-generated layer transition points

First, go to "Workstation settings > Auto-Transition" page and activate the "Enable auto transition points" function. The "Auto acquisition" checkbox will then be displayed. When "Auto acquisition" next to "Layer transition point" is checked, any existing custom transition points will be cleared.

**NOTE**

The number of conveyors configured for auto-transition points must match the number of conveyors configured in the current project; otherwise, switching to the transition point mode will not be possible. After switching to "Auto acquisition", the original transition point list is hidden, and the following page is displayed. You can preview the motion trajectory for a specific layer (including the picking point, transition points, placement offset points, and placing points) by selecting the layer and clicking "3D trajectory preview". Click the button again to hide the trajectory.

_Figure 5.90 Auto acquisition_

* Set fixed points

Fixed points are only available when "Layer transition point" is set to "Custom". Click "Fixed points" to display the following page, where you can check fixed transition points for the left/right pallet.

![Figure 5.89 Delete transition point](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOHwcQIPBOv18pVMdVCAk%2Fpalletizing-p090-img02.png?alt=media)

_Figure 5.91 Set fixed points_

**NOTE**

* Newly added transition points are not selected by default.
* For transition points that are already selected, the point height will not be dynamically calculated based on layer height during script execution.
* The last transition point must be unfixed (grayed out and unselectable).

#### 5.6.6 Check reachability

After configuring the palletizing project parameters, enter the project name and click "Reachability detection" to verify that all required parameters have been set and that all points in the stacking pattern are reachable. After the reachability detection passes, click "Save" to complete the palletizing project configuration.

### 5.7 New palletizing project (with interlayer)

_Figure 5.92 Workflow for a New Palletizing Project With Interlayer_

![Figure 5.91 Set fixed points](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FE4QXUkv2WD14mkPwrZHp%2Fpalletizing-p091-img03.jpg?alt=media)

If creating a palletizing project that uses interlayer, you must first set the interlayer coordinate system. When creating the project, select "With Interlayer" and configure the interlayer parameters; the configuration of other parameters is the same as for a new palletizing project without interlayer.

#### 5.7.1 Create interlayer coordinate system

If an interlayer needs to be placed or removed every few layers during palletizing or depalletizing, you'll need to set the user coordinate system for the interlayer. The setting method is as follows:

1. In DobotStudio Pro, click "Settings > Coordinate system > User coordinate system" to

enter the user coordinate system settings page, and add or modify a user coordinate system.

_Figure 5.93 User coordinate system_

2. Click the "Three-point setting" button on the "Add user coordinate system" page.

_Figure 5.94 Add user coordinate system_

3. In the "Three-point setting" page, teach the system and obtain any three non-collinear

points on the plane of the interlayer stacking zone (refer to the figure below, the Z-axis should be oriented towards the interlayer stacking direction), then click "Confirm".

![Figure 5.93 User coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNznPUE6L2iTGWm6O5NON%2Fpalletizing-p092-img02.jpg?alt=media)

![Figure 5.94 Add user coordinate system](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1e9BpTYDH8KqADCAOcM2%2Fpalletizing-p092-img03.png?alt=media)

_Figure 5.95 User coordinate system-Three-point setting_

4. The system automatically returns to the "Add user coordinate system" page, and the

coordinate system values are updated to the calibrated values. Click "Save" to complete the user coordinate system settings for the interlayer. Define the interlayer stacking zone If an interlayer needs to be placed or removed every few layers during palletizing or depalletizing, the interlayer stacking zone must be determined. First, place the interlayers in the designated stacking zone first, then jog or drag the robot arm to confirm that the end-of-arm suction cup can grip the topmost and bottommost interlayers. It is recommended to plan the interlayer stacking zone and the picking point on the same side. If interlayer must be stacked on the opposite side of the picking point and require routing around the already palletized boxes, a customized version of the palletizing process package will be required. See the example image on the right for normal use:

_Figure 5.96 Recommended interlayer stacking position_

![Figure 5.95 User coordinate system-Three-point setting](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEaMDHrOujR14sFP6XmA7%2Fpalletizing-p093-img02.png?alt=media)

![Figure 5.96 Recommended interlayer stacking position](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD5P7YK29E7gXXtmPBoGV%2Fpalletizing-p093-img03.jpg?alt=media)

#### 5.7.2 Set interlayer

_Figure 5.97 Project basic parameters (with interlayer)_

When creating a palletizing project, select "With Interlayer" and choose "User coordinate system (Interlayer)". Click "Next" to enter the "Interlayer settings" page. For parameter configuration on other pages, refer to "New palletizing project (without interlayer)".

_Figure 5.98 Interlayer parameter (palletizing)_

![Figure 5.97 Project basic parameters (with interlayer)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrRRTwG9BC8xseglEKVpo%2Fpalletizing-p094-img02.jpg?alt=media)

![Figure 5.98 Interlayer parameter (palletizing)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuOdqJETdrKFkyzT3kiRS%2Fpalletizing-p094-img03.png?alt=media)

_Figure 5.99 Interlayer parameter (depalletizing)_

① Total interlayers at interlayer-picking point / Maximum number of interlayers at interlayer-placing point: The number of interlayers (for palletizing) / the maximum number of interlayers that can be stacked at the placing position (for depalletizing). Unit: PCS. Value range: \[0, 100]. ◦ For palletizing: When the system detects that interlayers have been used up, it will pause and prompt you to add interlayers. The placement position and quantity of the added interlayers must match those of the previous stack. ◦ For depalletizing: When the system detects that the placing position is full, it will pause and prompt you to remove the interlayers. After resuming, the system will continue placing interlayers at the same position.

**NOTICE**

During palletizing, the placement position and quantity of the added interlayers by the user must be identical to the previous stack. Otherwise, it will result in an incorrect interlayer count and the project will report an error. ② Interlayer thickness: Unit: mm. Value range: \[0, 200]. ③ Interlayer position: The position where users can define to add interlayers. Check or click the empty space between layers to add an interlayer for that layer, including the top and bottom layers.

![Figure 5.99 Interlayer parameter (depalletizing)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FXU9AXsjH6snGmKj84IxG%2Fpalletizing-p095-img02.png?alt=media)

④ Interlayer picking point, interlayer placing point, and any number of transition points (at least 1, up to 5). ◦ For palletizing: Set the first point as the interlayer picking point, which should be at the bottommost interlayer in the stacking zone. The system will automatically calculate the picking points for the remaining interlayers based on the number of interlayers already used and their thickness. The interlayer placing point is where the first interlayer will be placed on each pallet. See the "Interlayer stacking zone" section for details on interlayer stacking positions. ◦ For depalletizing: Set the first point as the interlayer placing point, which should be at the bottommost interlayer in the stacking zone. The system will automatically calculate the placing points for the remaining interlayers based on the number of interlayers already placed and their thickness. The interlayer picking point is where the first interlayer will be picked up from each pallet. ◦ The coordinates for picking/placing points displayed on the interface are based on the interlayer coordinate system, while the coordinates for interlayer transition points are based on the pallet coordinate system on the same side.

### 5.8 Other functions

#### 5.8.1 Manufacturer configuration

System integrators and distributors can pre-configure parameters such as coordinate systems and signals before delivering the workstation to end users. These settings can then be hidden through the Manufacturer Configuration page to prevent accidental changes by end users. To access, click the icon in the upper-right corner of the palletizing process package home page and select "Manufacturer configuration". This function is only available under Administrator permissions. For other roles, the Manufacturer Configuration menu is grayed out and cannot be edited.

_Figure 5.100 Manufacturer configuration_

You can select which core function modules to display or hide. By default, all modules are visible, but you can freely choose modules to hide. Any changes will save the data as it

![Figure 5.100 Manufacturer configuration](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Foy0AiZR22m7hvSI7RrZu%2Fpalletizing-p096-img03.png?alt=media)

was before hiding.

_Figure 5.101 Manufacturer configuration_

If this is the first time using the palletizing process package and the workstation has not yet been configured, ensure the workstation is configured before using the "Manufacturer configuration" function.

#### 5.8.2 Import/Export configuration

To import or export workstation configurations, click the icon in the upper-right corner of the palletizing process package home page and select "Import/Export configuration".

_Figure 5.102 Import/Export workstation configuration_

* After clicking "Export Configuration", you can customize the save path and file name for the exported file. By default, the file name is "Dobot Workstation Settings + Export Time.json".
* After clicking "Import Configuration", the following prompt will appear. Since the coordinates may vary between workstations, the imported configuration data does not include coordinate system parameters. You will need to configure and confirm the coordinate systems after import. Click "Cancel" to close the prompt and abort the import process, or click "Confirm" to select the file path for the import.

![Figure 5.101 Manufacturer configuration](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FB6CXylr35UCsNqjHhBor%2Fpalletizing-p097-img02.png?alt=media)

![Figure 5.102 Import/Export workstation configuration](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmMkvt4pUplCfrrSLBZKp%2Fpalletizing-p097-img04.png?alt=media)

_Figure 5.103 Prompt_

#### 5.8.3 Manage palletizing project

_Figure 5.104 Manage project_

Click "More projects" on the palletizing monitoring page to open the project list.

_Figure 5.105 Project list_

No. Description Click next to the project name to rename the project. ① Filter the projects displayed in the list by project type. ② Select a project and click "Save to product management" to store the current ③ palletizing project to product management.

![Figure 5.103 Prompt](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS8OjQZSDHhgZvSojQQwy%2Fpalletizing-p098-img02.png?alt=media)

![Figure 5.104 Manage project](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRMpFNSULi3SpJ4iHZ1OM%2Fpalletizing-p098-img04.jpg?alt=media)

No. Description Select a project and click "Delete" to delete the selected project. ④ Select a project and click "Copy" to generate a copy of the selected project. ⑤ Select a project and click "Edit" to modify the configuration of the selected ⑥ project. Click "New" to create a new palletizing project. ⑦ Select a project and click "Export" to export the selected project in "json" ⑧ format to your local system. Click "Import" to import a palletizing project in "json" format from your local ⑨ system. Select a project and click "Open project" to set the selected project as the ⑩ current project. Select a project and click "Virtual simulation" to simulate the running of the ⑪ selected project. Virtual simulation Virtual simulation is available only when the robot arm is in the disabled status. You can turn on the Enable switch on the DobotStudio Pro homepage.

_Figure 5.106 Enable switch_

On the "Manage palletizing project" page, click the "Virtual Simulation" button, and the following prompt will appear:

_Figure 5.107 Virtual simulation prompt_

![Figure 5.106 Enable switch](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fq0baCZRuXCmEDVjP0ne4%2Fpalletizing-p099-img03.png?alt=media)

Click "Start Simulation" to enter the simulation page. Once entered, the simulation project will automatically start running.

_Figure 5.108 Virtual simulation_

No. Description Click "Hide Panel" to collapse the control panel, the button will then change to ① "Show Panel". You can pause, stop, or restart the project. The number below the pause button indicates the current simulation runtime. After stopping the simulation, ② "Restart" and "Exit Simulation" buttons will appear. Click to either restart the simulation or exit the simulation page. Display the total number and rate of palletizing. ③ Display the current stacking layer and the number of boxes in the current layer. While stopped, click "Edit" to input the desired starting layer and ④ number of boxes per layer. Click "Confirm and Start Simulation" to begin the simulation. If a collision or other abnormal situation occurs during the simulation, the project will stop, and a pop-up window will inform you of the issue.

_Figure 5.109 Simulation error_

![Figure 5.108 Virtual simulation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIbNFuBTrfCDQrGHlfklV%2Fpalletizing-p100-img02.jpg?alt=media)

![Figure 5.109 Simulation error](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4TdDYyfRsmCKJ48Y7WGn%2Fpalletizing-p100-img03.jpg?alt=media)

* Click "Configure" will take you back to the "Palletizing configuration" page, where you can adjust the settings based on the errors encountered during the simulation.
* Click "Not Configure" or the "X" at the top right to close the pop-up window, stay on the simulation page and check the status of the 3D model when the anomaly occurs. After an error, a "Restart" button will appear on the control panel, allowing you to restart the palletizing project from the beginning.

**NOTE**

* The "Virtual Simulation" function uses the robot's real controller, and the simulation speed cannot be accelerated.
* You can also perform simulation operations via the web at:

http://8.129.2.35:9702.

## 6. Palletizing Project Run & Monitoring

### 6.1 Run palletizing project

#### 6.1.1 Run via palletizing process package

_Figure 6.1 Stop/Run button_

* After creating a new project or opening an existing project via "More projects", click

"Run" to start executing the current project, and the button will change to "Pause". While the palletizing project is running, the data and information on the interface will refresh in real time.

* Click "Pause" to pause the project, and the button will change to "Continue".
* Click "Continue" to continue the paused project, and the button will change back to

"Pause".

* Click "Stop" to stop the current project, and the button on the right will change back to

"Run".

**NOTICE**

If the project is stopped during palletizing (due to an alarm or manual stop), the workstation must be manually reset before restarting the project. The reset steps are as follows:

1. If there is a box gripped by the suction cup, hold the box and manually release

the suction cup, then place the box to a safe area.

2. Use the jog function to move the robot arm to a safe position (the hover point

that the arm first moves to after the project starts).

![Figure 6.1 Stop/Run button](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBdXOQHv3dAYyjcDo2NZI%2Fpalletizing-p102-img02.jpg?alt=media)

#### 6.1.2 Run via control panel buttons

After correctly configuring the palletizing workstation and creating the palletizing project, associate the palletizing project with the remote I/O as the running project, so that users can run the palletizing project via the control panel buttons.

1. Go to the "Monitor" page in DobotStudio Pro and check whether the DI/DO

configurations of the controller are correct. Controller Function DI/DO DI\_7 Enable button DI\_11 Start button DI\_12 Stop button Reset button DI\_13 (clear alarm) DO\_7 Enable status indicator DO\_11 Running status indicator DO\_12 Alarm status indicator DO\_13 Stop status indicator

_Figure 6.2 Correct I/O configuration_

2. If the I/O configuration is incorrect, click "Settings" to enter the "IO settings" tab and

modify the "Feature configuration".

_Figure 6.3 Feature configuration entry_

3. After modifying the function configuration, click "Save" to return to the I/O monitoring

page.

![Figure 6.2 Correct I/O configuration](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGEE9cFOsboqtyLoAd1Os%2Fpalletizing-p103-img02.png?alt=media)

![Figure 6.3 Feature configuration entry](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUMXInBWvbh8Hr1ybLviU%2Fpalletizing-p103-img03.jpg?alt=media)

_Figure 6.4 Modify I/O configuration_

4. Click "Remote Control" to navigate to the "Settings > Remote Control > I/O Remote

Control" page in DobotStudio Pro. Select the desired palletizing project and click "Set as Default Operating Project" on the right.

_Figure 6.5 Select project_

5. Return to the DobotStudio Pro home page and check that the "Default I/O Project" is

correct. Then, change the "I/O/Modbus Configuration" switch to "ON".

![Figure 6.4 Modify I/O configuration](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6BscSvwLp79O9Vej4HgK%2Fpalletizing-p104-img02.png?alt=media)

![Figure 6.5 Select project](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzGAWLvdquBpGx5IYVLf3%2Fpalletizing-p104-img03.jpg?alt=media)

![Official manual figure, page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH1FgQzXEx9D8CCCYnpIc%2Fpalletizing-p104-img04.jpg?alt=media)

_Figure 6.6 Enable I/O/Modbus configuration_

6. Power on the palletizing workstation, then press the corresponding buttons on the

palletizing workstation in the following order to run the palletizing project: ① Press the "Enable" button. Wait for the "Enable" button indicator to light up, indicating that the robot arm has been successfully enabled. ② Press the "Start" button. Wait for the "Start" indicator to light up, indicating that the palletizing project has begun running.

_Figure 6.7 Workstation control buttons_

![Figure 6.6 Enable I/O/Modbus configuration](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxjXKxbKgFB2hY94YkLqA%2Fpalletizing-p105-img02.png?alt=media)

![Figure 6.7 Workstation control buttons](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5q8EwGFSx2maQzCwtZzT%2Fpalletizing-p105-img03.png?alt=media)

### 6.2 Real-time monitoring of palletizing project

_Figure 6.8 Palletizing monitoring page_

No. Parameter Description Indicates the total production capacity of the palletizing workstation. Click "Clear" to clear the capacity data and re- count it.

* Total number of pallets: The total number of pallets that have been palletized or depalletized by the workstation. Capacity data • Total number of boxes: When the actual number of boxes placed is a multiple of the number of placement ① cycles, click and enter the multiplier. The total number of boxes displayed = Number of placement cycles × Multiplier.
* Running time: The duration for which the workstation has been running the project. For projects with interlayers, here displays the number of Interlayer count interlayers. Click "Edit" to modify based on the actual interlayer count. ② Pallet monitor See "Monitor pallet data" for details. ③ Displays user print messages, error messages, and custom errors generated during palletizing operations. See "Alarm Running log Message and Solution" for details. Click "Clear" to clear the running logs. ④ Project The name and type of the currently open project. information ⑤ Enable the robot arm, click the "Position" button to open Position the jog panel, where you can adjust the robot arm's ⑥

![Figure 6.8 Palletizing monitoring page](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfMTINl0bZCRIlf4eF1Jn%2Fpalletizing-p106-img02.jpg?alt=media)

No. Parameter Description up/down, forward/backward, and left/right motions. Long- press "Safe Home" button to return the arm to the workstation's safe home position. Click to open the I/O monitoring window to view the I/O signals configured for the palletizing workstation. DO I/O monitor signals appear as ON/OFF switches, which correspond to high/low levels of the signal. You can change a DO signal's ⑦ status by toggling its switch. Manually control the lifting column and suction cup, as well Debug as set debugging-related parameters. See "Debug panel" for details. ⑧ Enter the palletizing project configuration page to modify Edit parameters of the current project. ⑨ Run the palletizing project or stop the project. See "Run via Stop / Run palletizing process package" for details. ⑩

#### 6.2.1 Monitor pallet data

_Figure 6.9 Pallet monitoring_

If "1 Conveyor 1 Pallet" was selected as the palletizing mode when creating the project, the unselected pallet will be locked in a disabled status and cannot be enabled or modified. No. Parameter Description Enable or disable the left/right pallet as needed. The Pallet ON/OFF a workstation will only perform palletizing on the enabled switch pallet. Indicates the current status of the pallet via color and text Pallet status b (when the pallet is disabled, no color or text is displayed). indicator See "Pallet status description" for details. During operation, the system provides real-time statistics on the number of boxes that have been palletized or depalletized (i.e., which layer and which box). The current pallet data is updated each time a box is successfully c Pallet data placed. For example, if the 3rd box on the 1st layer is currently being placed, the interface will display Layer 1 with 2 boxes already placed. After the current box is placed, the display

![Figure 6.9 Pallet monitoring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmhG02SjkQ7AuhIDocXsw%2Fpalletizing-p107-img02.jpg?alt=media)

No. Parameter Description will update to Layer 1 with 3 boxes. If the actual number of boxes already on the pallet differs from the number displayed on this page, click the "Modify" button to manually adjust the data to match the actual count to avoid errors during palletizing.

#### 6.2.2 Pallet status description

_Table 6.1 Pallet status description_

Scenario Color Text Scenario Color Text Pallet not Pallet not detected detected Pallet detected Pallet detected Yellow but not enabled Yellow but not enabled Idle Idle Palletizing Depalletizing Pallet full Pallet empty Palletizing in Depalletizing in Green Green progress progress Error (refer to Error (refer to Red Alarm Message Red Alarm Message and Solution) and Solution)

#### 6.2.3 Debug panel

Basic debugging

_Figure 6.10 Debugging Popup (Basic debugging)_

Debugging for lifting column ① If the lifting column is not connected, click to view and modify the IP and port settings for the lifting column you want to connect. Typically, the default IP of the lifting column matches the preset IP in the palletizing process package when the workstation is shipped, so no changes are needed. However, if you’ve modified the lifting column’s IP or are using a different lifting column, you’ll need to update the IP and port here.

_Figure 6.11 Lifting column IP_

Click "Connect", the system will start connecting to the lifting column. Once connected, the current position of the lifting column (relative to the initial position, with a maximum height of 900mm) will be displayed. You can manually control the lifting column by long-pressing the "Down" or "Up" buttons. You can also enter a target position and then long-press the "Run to" button to move the lifting column to the specified position (a prompt will appear once the target

![Figure 6.10 Debugging Popup (Basic debugging)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Flo41uoH47DgsCqDaL9Ro%2Fpalletizing-p109-img02.png?alt=media)

![Figure 6.11 Lifting column IP](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9bWlBOfwGG0HrsemEjlM%2Fpalletizing-p109-img04.jpg?alt=media)

position is reached). If an unexpected situation occurs during movement, releasing the "Run to" button can stop the lifting column. After debugging, click "Disconnect" to disconnect from the lifting column. Debugging for pneumatic suction cup ② You can click "Suction" or "Release" to change the status of the suction cup for debugging. Basic debugging parameter settings ③

* Infeed Waiting Time: The time elapsed after the infeed signal is triggered and before the robot arm initiates the picking action. Unit: ms. Range: (0, 3600000]. Default: 0.
* Suction Wait Time: The time to wait for the suction cup to securely pick up the box. Reducing the wait time can increase palletizing speed, but it may cause the box to be inadequately gripped. Adjust according to the actual situation. Unit: ms. Range: (0,5000]. Default: 1500.
* Release Wait Time: The time to wait for the suction cup to place the box.

Reducing the wait time can increase palletizing speed, but it may cause the robot arm to disturb the box when moving away, affecting the palletizing result. Adjust according to the actual situation. Unit: ms. Range: (0,5000]. Default: 1500.

* Safe Picking Height: The vertical height the robot arm moves to before and after picking up a box. Unit: mm. Range: (0,1000]. Default: 300.
* Drop Detection Delay: The interval time between two drop detections, used to confirm whether a box drop has occurred. Unit: ms. Range: (0,3600000]. Default: 0.
* Drop detection: This function can only be enabled after the "Drop Detection

Signal" option is checked in the palletizing workstation's I/O signals. After enabled, if a box drop is detected during palletizing, the project will trigger an alarm and stop.

Advanced debugging

_Figure 6.12 Debugging popup (Advanced debugging)_

Compensation ① You can set the compensation based on the problems that occur during palletizing. For double pallets, you need to set the compensation for the left pallet and the right pallet separately.

* Z-axis height compensation:

During palletizing, discrepancies in the actual box sizes or deformation of lower layers due to compression can lead to significant differences between the actual height and the calculated theoretical height after stacking several layers, impacting the palletizing quality. To address this, identify the layer where the significant differences occurs. If the actual height of that layer is lower than the theoretical height, choose "Downward"; if it is higher, choose "Upward". Then calculate the compensation height (maximum: 200mm) using the following formula: Compensation height = Theoretical height x Number of layers-Actual height

_Figure 6.13 Z-axis height compensation_

![Figure 6.12 Debugging popup (Advanced debugging)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSrjRwQRP4oM6xdNUVv9H%2Fpalletizing-p111-img02.png?alt=media)

![Figure 6.13 Z-axis height compensation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdtABWfh3okVOleKLnojn%2Fpalletizing-p111-img03.jpg?alt=media)

In the actual palletizing process, as shown in the figure, if height deviation starts from the third layer, you should begin compensating from that layer. If, after adjusting and continuing, further height deviations occur in the upper layers, you need to add the required compensation for each layer to form a new compensation value.

* Placing point height compensation:

It corresponds to the height at which the box is vertically placed during palletizing, i.e., the height difference between the "point directly above the placing point" and the "placing point" itself. The box will approach the point directly above the placing point from a specified direction according to "direction & offset settings", and then be lowered vertically, as shown in the figure below.

_Figure 6.14 Placing point height compensation_

Safe home position ② When the palletizing project starts running (or restarts after being stopped), and after completing each pallet, the robot arm will return to the safe home position. If the posture at this position does not cause any interference, it is advisable not to alter this point, as changes could result in abnormal movements of the lifting column or robot arm.

![Figure 6.14 Placing point height compensation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnXn2Sh9ki6oQZ1NZwEF4%2Fpalletizing-p112-img02.png?alt=media)

"2 Conveyors 2 Pallets" debugging

_Figure 6.15 “2 Conveyors 2 Pallets” debugging_

This tab is only displayed when the current project is in “2 Conveyors 2 Pallets” mode. First, you need to select the specific palletizing mode based on the actual conditions of the production line:

* Alternate palletizing on left and right pallets

In this mode, the workstation alternates palletizing between the left and right pallets, following the sequence: Left box 1 => Right box 1 => Left box 2 => Right box 2. If the system finishes palletizing Left box 1 and the right conveyor’s feeding signal is inactive while the left conveyor’s signal is active, the workstation will continue palletizing on the left pallet until the right conveyor’s signal is activated, and vice versa. This mode is suitable for scenarios where the production capacities of both conveyors are similar, and the box sizes are comparable. If the production capacities or box sizes vary greatly, it may lead to a significant height difference between the boxes on the left and right pallets during palletizing. This could result in frequent raising and lowering of the lifting column, slowing down the palletizing speed and potentially damaging the lifting column.

* Prioritize lower-level palletizing

This mode calculates the height difference between the boxes on the left and right pallets in real time on the basis of the alternating palletizing mode. When the height difference reaches or exceeds a trigger value (h1), the workstation enters one-sided palletizing mode, continuing to palletize only on the side with the lower height until the height difference falls below the ending value (h2), and then resumes the alternating palletizing mode.

![Figure 6.15 “2 Conveyors 2 Pallets” debugging](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FspKK1pcgYMRY4ei7UjAU%2Fpalletizing-p113-img02.png?alt=media)

**NOTE**

When the workstation is in one-sided palletizing mode, it may cause material to accumulate on the other side. Users should set up a buffer zone on the conveyor based on the actual situation of the production line.

_Figure 6.16 Settings for Prioritize lower-level palletizing_

* Trigger one-sided palletizing height difference (h1):

When the height difference between the two sides is greater than or equal to this value, one-sided palletizing mode is activated. Range: \[0,2200].

* End one-sided palletizing height difference (h2):

When the height difference between the two sides is less than this value, one- sided palletizing mode ends. Range: \[0,2200].

* Pause left/right pallet line function:

When the corresponding DI is set to ON, the workstation will pause palletizing on that side and only continue palletizing on the other side, ignoring the height difference. If both DI signals are ON, the workstation will stop operating. When both DI signals are OFF, the workstation will resume normal palletizing operations. The line pause function is only effective in "Prioritize lower-level palletizing" mode and can be configured to be triggered by either Controller DI or Virtual DI: ◦ DI Trigger: Triggered by real Controller DI. The user needs to connect a trigger source, such as a toggle switch, to the corresponding DI on the controller. ◦ Virtual DI: Triggered by virtual DI from the control software. When configured as virtual

![Figure 6.16 Settings for Prioritize lower-level palletizing](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fs8km73TnGpDz0UBdsOBZ%2Fpalletizing-p114-img02.png?alt=media)

DI, the corresponding DI on the I/O monitoring page will appear as ON/OFF button (as shown in the figure). The user can only control the DI status through the software, and the real status of the DI interface on the controller will be ignored.

_Figure 6.17 Virtual DI_

Typical application scenarios for the line pause function (using a physical switch to trigger the DI as an example): ◦ Scenario 1: If the left pallet’s production line experiences an issue and no material is fed, the workstation will continue palletizing on the right pallet. If no action is taken, once the right pallet reaches a certain height, the height difference will trigger one-sided palletizing, causing the workstation to stop and wait for material from the left conveyor. In this case, the operator should press the left line’s pause switch to have the workstation palletize only on the right pallet. Once the left line is back to normal, the operator can reset the switch. ◦ Scenario 2: When replacing the left pallet, if only a few boxes remain to complete the right pallet and no action is taken, the height difference could trigger one- sided palletizing. This may cause the workstation to ignore the nearly completed right pallet and continue palletizing on the new left pallet. To prevent this, the operator can press the left line’s pause switch during pallet replacement, allowing the workstation to first complete the right palletizing. Once the right palletizing is finished, the operator can reset the switch.

![Figure 6.17 Virtual DI](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F87fUzqA4R0skOQSMQ2jm%2Fpalletizing-p115-img02.png?alt=media)

Motion parameters

_Figure 6.18 Motion parameters_

Set the speed percentage for robot arm's motions. The speed with a box and without a box must be set separately. Default parameters are pre-configured at the factory. If there are no special requirements, no modification is needed. When "Place motion" is checked, the motion speed from the transition point to the placing point will default to the speed set for "With box" above. You can also adjust it as needed.

![Figure 6.18 Motion parameters](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8Zld3kcaBTUq5hkX3DHt%2Fpalletizing-p116-img02.jpg?alt=media)

## 7. IO Configuration

If the workstation is not equipped, you can complete the signal setup and then use either circuit shorting or virtual signal configuration for debugging. In this mode, the robot arm will execute the pre-defined motion trajectory but will not physically pick up products. To enable actual gripping, proper wiring must be completed. Safety Notice: During debugging and operation, ensure that all personnel remain outside the robot arm’s working range to maintain safety.

### 7.1 I/O wiring method

When using the Palletizing Process Package, refer to the IO definitions in the diagram below for wiring. During actual usage, wire connections should follow the signal settings defined in the workstation configuration.

_Table 7.1 DI definition reference_

Pin In(DI) Label Description Corresponding signal Conveyor 1- Incoming material DI1 DI1 -- detection DI2 DI2 -- Left pallet-Position detection 1 Sensor In 1–5 DI3 DI3 -- Left pallet-Position detection 2 DI4 DI4 -- Right pallet-Position detection 1 DI5 DI5 -- Right pallet-Position detection 2 -- Conveyor 2- Incoming material DI6 DI6 -- detection DI7 DI7 -- Enable button -- DI8 DI8 -- Reserved -- DI9 DI9 -- Left\_Pallet confirm DI10 DI10 -- Right\_Pallet confirm DI11 DI11 -- Start button User signal DI12 DI12 -- Stop button DI13 DI13 -- Reset button DI14 DI14 -- Vacuum gauge 1 -- DI15 DI15 -- Vacuum gauge 2 -- -- Conveyor 3- Incoming material -- DI16 DI16 detection DI17 DI17 -- Conveyor 4- Incoming material --

Pin In(DI) Label Description Corresponding signal detection DI18 DI18 -- Reserved -- DI19 DI19 -- -- -- DI20 DI20 -- -- -- DI21 DI21 -- -- -- DI22 DI22 -- -- -- DI23 DI23 -- -- -- DI24 DI24 -- -- --

_Table 7.2 DO definition reference_

Pin Out(DO) Label Description Corresponding signal DO1 DO1 -- Left\_Three color light\_Yellow DO2 DO2 -- Left\_Three color light\_Green DO3 DO3 -- Left\_Three color light\_Red Light out 1–6 DO4 DO4 -- Right\_Three color light\_Yellow DO5 DO5 -- Right\_Three color light\_Green DO6 DO6 -- Right\_Three color light\_Red DO7 DO7 -- Enable button light -- DO8 DO8 -- Reserved DO9 DO9 -- Reserved -- DO10 DO10 -- Reserved DO11 DO11 -- Start button indicator User signal DO12 DO12 -- Stop button indicator DO13 DO13 -- Reset button indicator DO14 DO14 -- Vacuum suction solenoid valve 1 -- DO15 DO15 -- Vacuum suction solenoid valve 2 -- DO16 DO16 -- Vacuum release solenoid valve 1 -- DO17 DO17 -- Vacuum release solenoid valve 2 --

Pin Out(DO) Label Description Corresponding signal DO18 DO18 -- -- -- DO19 DO19 -- -- -- DO20 DO20 -- -- -- DO21 DO21 -- -- -- DO22 DO22 -- -- -- DO23 DO23 -- -- -- DO24 DO24 -- -- --

*

The DI interface must be connected to the COM interface, which can switch signal types (PNP or NPN). COM1 is used for DI1 – DI12. COM2 is used for DI13 – DI24.

*

For DI connected to a simple switch, the left diagram below shows PNP wiring, and the right diagram shows NPN wiring. You can choose the appropriate wiring method based on the on-site requirements.

_Figure 7.1 DI simple switch wiring_

*

For DI shorted connection, the left diagram below shows PNP wiring, and the right diagram shows NPN wiring. You can choose the appropriate wiring method based on the on-site requirements.

![Figure 7.1 DI simple switch wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2619WOu3UFs8CuPwaxrP%2Fpalletizing-p119-img02.png?alt=media)

_Figure 7.2 DI shorted wiring_

*

For DI connected to an external PNP three-wire sensor, the wiring is as shown below. When the sensor is powered by the controller, short the COM port to I/O 0V (left below). When the sensor is powered by an external source, connect the COM port to 0V of the external power supply (right below).

_Figure 7.3 DI PNP input wiring_

*

For DI connected to an external NPN DO signal, the wiring is as shown below. When the external DO is powered by the controller, short the COM port to I/O 24V (left below). When the external DO is powered by an external source, connect the COM port to 24V of the external power supply (right below).

![Figure 7.2 DI shorted wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoyNBKlSFQCGUmmSHpsOk%2Fpalletizing-p120-img02.png?alt=media)

![Figure 7.3 DI PNP input wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNHytp1ugDFhkNEg25wH0%2Fpalletizing-p120-img03.png?alt=media)

_Figure 7.4 DI NPN input wiring_

*

DO is set to PNP by default but can be switched to NPN via the software (DobotStudio Pro). If the software setting and the actual wiring configuration do not match (e.g., software set to PNP while wiring is NPN), the load will not function properly. When DO is set to PNP, the wiring for connecting to an external load is shown below.

_Figure 7.5 PNP DO external load wiring_

*

When DO is set to NPN, the wiring for connecting to an external load is shown below.

![Figure 7.4 DI NPN input wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKNiFIY0ucoL570tgcYoK%2Fpalletizing-p121-img02.png?alt=media)

![Figure 7.5 PNP DO external load wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHlfSXE7WLPIc3av25KWE%2Fpalletizing-p121-img03.png?alt=media)

_Figure 7.6 NPN DO external load wiring_

### 7.2 Set virtual IO

1. Go to "Monitor > Controller DI/DO > Settings".

_Figure 7.7 Controller DI/DO_

2. Check the "Switch to virtual DI" option for the corresponding DI, then click "Save".

![Figure 7.6 NPN DO external load wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMZlE503gLn0NF5P0Olg3%2Fpalletizing-p122-img02.png?alt=media)

![Figure 7.7 Controller DI/DO](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvCHUGmceaiKql2kGHAyK%2Fpalletizing-p122-img03.png?alt=media)

_Figure 7.8 Switch to virtual DI_

_Figure 7.9 Virtual DI status_

![Figure 7.8 Switch to virtual DI](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0ku8V6Uai76U3SuvivG9%2Fpalletizing-p123-img02.png?alt=media)

![Figure 7.9 Virtual DI status](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyTXBjwBphaIQWizrcluk%2Fpalletizing-p123-img03.png?alt=media)

## 8. Alarm Message and Solution

Alarm message Communication failure between the robot and the lifting axis. Error code 1 Error cause Communication failure between the robot and the lifting column. Project status Stop Restart the palletizing workstation. ① If the problem persists after restarting, check the connection of ② the cables related to the lifting column: a. Check if the network cable connection of the robot controller is secure. Solution

_Figure 8.1 Network cable connection for robot controller_

b. Use the triangular key provided in the shipping list to open the power distribution cabinet and check if the network cables are securely connected to the lifting column control box and the switch.

![Figure 8.1 Network cable connection for robot controller](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzlcOdlA9RKWdCJnjO4CK%2Fpalletizing-p124-img02.jpg?alt=media)

![Official manual figure, page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8fsPkuWVo6osR2rgLWMo%2Fpalletizing-p124-img03.jpg?alt=media)

_Figure 8.2 Check network cables_

c. If none of the above methods can solve the problem, contact DOBOT technical support engineer for troubleshooting. The alarm message will specify the exact unreachable point and Alarm message provide a solution, e.g., "Cannot reach the placing point for Box 3 on Layer 2. Please check the palletizing pattern settings." Error code 2 The target point has no inverse kinematics solution (i.e., the robot Error cause cannot calculate the joint angles required to reach that position). Project status Stop Solution Modify the project configuration according to the alarm message. Alarm message Pallet loss detected. Error code 3 During operation, the pallet signal was lost for more than 20 Error cause seconds. Project status Stop Place the pallet in the correct position. ① Solution Check if the pallet sensors are working properly: Open the I/O ② monitoring window on the palletizing monitoring page, block each pallet sensor with your hand and see if the corresponding I/O signal turns green. If any sensor is not

![Figure 8.2 Check network cables](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F42WZpAMH6Ftmul0S2bVt%2Fpalletizing-p125-img02.jpg?alt=media)

functioning properly, contact DOBOT technical support engineer for troubleshooting.

_Figure 8.3 Pallet detection signal_

_Figure 8.4 Pallet sensor position (same on other side)_

Both production lines and the corresponding pallets have been Alarm message paused by a DI signal. Please adjust the DI status to resume normal operation. Error code 4 In “2 Conveyors 2 Pallets” mode, with the height difference limit Error cause function enabled, signals from both conveyors are simultaneously disabled. Project status Pause Change the DI status according to the actual state of the Solution production line. Refer to "2 Conveyors 2 Pallets" debugging for more details.

![Figure 8.3 Pallet detection signal](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUtJDFbb4nIECBZr4tbYV%2Fpalletizing-p126-img02.jpg?alt=media)

![Figure 8.4 Pallet sensor position (same on other side)](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbBWG7hHo6lyoNJr1ervY%2Fpalletizing-p126-img03.png?alt=media)

Alarm message Box dropped. Error code 5 Error cause During the operation, the material box fell off from the suction cup. Project status Stop Adjust the suction cup or pneumatic equipment to increase ① suction flow. Solution Adjust the picking point to make the suction cup and the box fit ② better. Alarm message The box is not released. Error code 6 When starting the process package, a box was detected on the Error cause suction cup. Project status Pause Manually release the box via the "Debug panel", then continue Status running the project. Alarm message Insufficient interlayers / The space for interlayers is full. Error code 7 During palletizing, the interlayer storage location is empty. Error cause ① During depalletizing, the interlayer storage location is full. ② Project status Pause When palletizing, add interlayers and continue running the ① project. Solution When depalletizing, remove interlayers and continue running ② the project. Failed to create Modbus communication, please check the Modbus Alarm message address! Error code 8 Error cause The robot failed to create a Modbus connection.

Project status Stop Restart the robot controller. ① Solution Check if the IP in the ModbusCreate command in the project ② script is set to the robot’s IP. The lifting column has exceeded the maximum limit of 35 lifts per Alarm message hour. Please stop for half an hour before running again, otherwise there is risk of burning out the lifting column! Error code 9 Error cause The lifting column has been operating too frequently. Project status Stop Stop the project for half an hour before resuming. Solution Refer to "2 Conveyors 2 Pallets" debugging to set up the "Prioritize lower-level palletizing" function to avoid triggering this alarm. Alarm message Lifting column status abnormal. Error code 12 Communication between the robot and the lifting column is normal, Error cause but it is not functioning properly. Project status Stop Try restarting the workstation. If the error persists, contact DOBOT Solution technical support engineer for troubleshooting. Alarm message No pallet enabled. Error code 14 All pallet enable buttons are disabled in the process package Error cause interface. Project status Stop Enable any pallet button on the monitoring interface. For pallet Solution button signal details, please refer to the "Pallet signal".

Alarm message Lifting column position read error. Error code 15 Error cause The robot is unable to retrieve the position of the lifting column. Project status Stop Follow the same procedure as for "Communication failure between Solution the robot and the lifting axis".

## 9. Product Specifications

### 9.1 Product nameplate

_Figure 9.1 Nameplate of CR20A Columnar Palletizing Workstation_

_Figure 9.2 Nameplate of CR20A Lifting Palletizing Workstation_

![Figure 9.1 Nameplate of CR20A Columnar Palletizing Workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhMXztxXbTpIUoZkCZzKo%2Fpalletizing-p130-img02.jpg?alt=media)

![Figure 9.2 Nameplate of CR20A Lifting Palletizing Workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0U9hIreTN4uLE6AbhXpn%2Fpalletizing-p130-img03.jpg?alt=media)

_Figure 9.3 Nameplate of CR30H Columnar Palletizing Workstation_

### 9.2 Technical specifications

_Table 9.1 Palletizing workstation technical specifications_

CR20A Columnar CR20A Lifting CR30H Columnar Product name Palletizing Palletizing Palletizing Workstation V2 Workstation V2 Workstation DT-PR-C-HSM- DT-PR-L-TX-HSM- DT-PR-C-HSM-OV- Model OV-20-02 OV-20-02 30-01 20 kg Payloa&#x64;_&#x31; 30 kg (up to 25 kg under specific conditions) Palletizing rat&#x65;_&#x32; 8 pcs/min 8-10 pcs/min Palletizing 1740 mm 2640 mm 1840 mm heigh&#x74;_&#x33; Working radius 1700 mm 1800mm Total Weigh&#x74;_&#x34; 350 kg 470 kg Dimensions\*5 1560 mm \* 1580 mm \* 1050 mm

![Figure 9.3 Nameplate of CR30H Columnar Palletizing Workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIcAWdTRNOCXt01f7PVky%2Fpalletizing-p131-img02.jpg?alt=media)

Rated Voltage AC 100V – 240V, 50Hz / 60Hz Maximum Power 1300W 1500W 3600W Temperature 10 – 40 range ℃ ℃ Protection Rating Robot body: IP54; Palletizing workstation: IP20 CE, Machinery Directive 2006/42/EC, EN 60204-1, EN 61000-6- Certification 2, EN 61000-6-4, ISO 12100, ISO 10218-2, ISO 13849-1, US\&CAN: SGS NA Listed Mark, FCC, ISED

* \*1: Excludes the weight of the end-effector vacuum gripper.
* \*2: CR20A Palletizing Workstation: The actual palletizing speed depends on factors such as the weight and dimensions of the boxes, as well as the pallet pattern. Experimental data shows that under a 20kg load, the maximum speed for single- suction, single-placement operations can reach up to 8 pcs/min. CR30H Palletizing Workstation: The actual palletizing speed depends on factors such as the weight and dimensions of the boxes, as well as the pallet pattern. Experimental data shows that under a 25kg load, the maximum speed for single- suction, single-placement operations can reach up to 8 -10 pcs/min.
* \*3: Actual palletizing height may vary based on box dimensions and patterns.
* \*4: Excludes the weight of the robot arm and end-effector weight.
* \*5: Height value indicates the workstation height only; robot arm dimensions are excluded.

**NOTICE**

When the ambient temperature is lower than 10°C, the viscosity of the lubricant increases, which may trigger false alarms if the robot arm performs high-speed and high-load movements immediately after powering on. It is recommended to first perform a few minutes of low-speed movements to warm up the device. Recommended minimum box size The minimum size of the box depends on the workstation model and the pallet size. If you need to confirm the dimensions of the box, you can determine it by running a simulation in the Simulation System.

### 9.3 Workstation dimensions

#### 9.3.1 For CR20A

Unit: mm.

_Figure 9.4 Dimensions of CR20A Columnar & Lifting Palletizing Workstation_

For the dimensions of the robot arm, please refer to DOBOT CRA Series Hardware User Guide.

![Figure 9.4 Dimensions of CR20A Columnar & Lifting Palletizing Workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7QUrGX23AqIgINl56ecl%2Fpalletizing-p133-img02.jpg?alt=media)

#### 9.3.2 For CR30H

Unit: mm.

_Figure 9.5 Dimensions of CR30H Columnar Palletizing Workstation_

For the dimensions of the robot arm, please refer to DOBOT CR30H Hardware User Guide.

### 9.4 Electrical topology

The Lifting Palletizing Workstation has lifting-column-related parts, the Columnar Palletizing Workstation has no lifting-column-related parts.

_Figure 9.6 Electrical topology of Lifting palletizing workstation_

![Figure 9.5 Dimensions of CR30H Columnar Palletizing Workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLEoscn6PhTjkePEnp0u5%2Fpalletizing-p134-img02.jpg?alt=media)

![Figure 9.6 Electrical topology of Lifting palletizing workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FP3UF813UxsAroFt8MtdH%2Fpalletizing-p134-img03.jpg?alt=media)

_Figure 9.7 Electrical topology of Columnar palletizing workstation_

### 9.5 Electrical diagram

For electrical diagrams, please contact DOBOT technical support.

### 9.6 Electrical interface

#### 9.6.1 Overview

The electrical interfaces of the palletizing workstation are concentrated on the front terminal panel, as shown in the figure below.

_Figure 9.8 Rear panel interface_

![Figure 9.7 Electrical topology of Columnar palletizing workstation](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FT3LGlDkd5M3xtrJFVnLq%2Fpalletizing-p135-img02.jpg?alt=media)

![Figure 9.8 Rear panel interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD1QeHYZxtsCu1ZjMuCQl%2Fpalletizing-p135-img03.jpg?alt=media)

_Figure 9.9 Front panel interface_

Silkscreen Description The LAN interface used to connect the debugging device has no fixed IP and the network segment is 192.168.5.xxx. During Ethernet debugging, you need to change the IP of the debugging device to the IP of the network segment other than 5.1 and 5.100. Safety In 1 Safety laser interface (reserved), see Safety In interface for Safety In 2 details. Safety In 3 Conveyor Sensor 1 Conveyor Sensor 2 Conveyor incoming signal interface, see Conveyor Sensor interface for details. Conveyor Sensor 3 Conveyor Sensor 4 Control button box interface (reserved), see Control Box interface for details. There is an aviation connector for this Control Box interface included in the accessories list of the palletizing workstation, and the cable is loose and labeled.

#### 9.6.2 Safety In interface

Safety laser interface. Take the SICK NanoScan3 safety laser as an example, the wiring is defined below.

_Figure 9.10 Safety In interface_

![Figure 9.9 Front panel interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbuvvF24IvI8dEeRITJec%2Fpalletizing-p136-img02.png?alt=media)

![Figure 9.10 Safety In interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZupLV6lNmqI6yB2imdLR%2Fpalletizing-p136-img03.jpg?alt=media)

Safety In 1 / Safety In 2 / Safety In 3 Pin Definition NanoScan3 I/O Description 1 N2401-1 Blue 0V DC Internal power 0V 2 P2401-1 Brown +24V DC Internal power +24V 3 S1-OSSD1A White OSSD 1.A The safety laser protection zone outputs dual channels and needs to be configured with SI3 and SI4 as protective stop. When 4 S1-OSSD1B Green OSSD 1.B only using a single laser, the other interface needs to be short-circuited with +24V. Yellow OSSD 2.A 5 S1-OSSD2A The safety laser protection zone outputs (Universal I/O 02) dual channels and needs to be configured with SI5 and SI6 as reduced mode. When Black OSSD 2.B only using a single laser, the other interface 6 S1-OSSD2B needs to be short-circuited with +24V. (Universal I/O 03)

_Figure 9.11 SICK NanoScan3 wiring_

#### 9.6.3 Conveyor Sensor interface

_Figure 9.12 Conveyor Sensor interface_

Conveyor feeding signal interface, support PNP and NPN inputs.

![Figure 9.11 SICK NanoScan3 wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMwW1zZNNxy9VYUkZXNPV%2Fpalletizing-p137-img02.jpg?alt=media)

![Figure 9.12 Conveyor Sensor interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUncaZWSwg7IzaFxvGPc5%2Fpalletizing-p137-img03.jpg?alt=media)

Conveyor Sensor 1 / 2 / 3 / 4 Pin Definition Description Remark Sensor 1 / Sensor 1 2 / Sensor 3 / Arrival signal 1: DI1, 2: DI6, 3: DI16, 4: DI17. Sensor 4 For PNP input, the pin is connected to N2401-1. Arrival signal 2 Com1 / Com2 common For NPN input, the pin is connected to P2401-1. 3 N2401-1 Internal power 0V - 4 P2401-1 Internal power +24V - When using an PNP-type sensor, Com is short-circuited to the internal power 0V:

_Figure 9.13 Wiring diagram for PNP-type feeding detection sensor_

When using an NPN-type sensor, Com is short-circuited to the internal power +24V:

_Figure 9.14 Wiring diagram for NPN-type feeding detection sensor_

When the external input is a relay passive input:

![Figure 9.13 Wiring diagram for PNP-type feeding detection sensor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwhgCal95Q8S4ZuP3mOfc%2Fpalletizing-p138-img02.jpg?alt=media)

![Figure 9.14 Wiring diagram for NPN-type feeding detection sensor](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0PTbqiXFhKc8gk8f17Qo%2Fpalletizing-p138-img03.jpg?alt=media)

_Figure 9.15 Relay passive input wiring diagram_

When the external input is a relay active input:

* When the external input is PNP, EXTcom is 0V.
* When the external input is NPN, EXTcom is 24V.

_Figure 9.16 Relay active input wiring diagram_

#### 9.6.4 Control Box interface

_Figure 9.17 Control Box interface_

User control box interface, used to connect the user's own control box to realize the project start and stop and protective stop reset function. Control Box Pin Definition Description Remark 1 P2401-1 Internal power +24V - 2 N2401-1 Internal power 0V -

![Figure 9.15 Relay passive input wiring diagram](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvFZO3RqpLoI9sfKCpMS4%2Fpalletizing-p139-img02.jpg?alt=media)

![Figure 9.16 Relay active input wiring diagram](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7DqoTj6mXzpdrAj78Qtt%2Fpalletizing-p139-img03.jpg?alt=media)

![Figure 9.17 Control Box interface](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtWoTU4tIwH3sBChneyGT%2Fpalletizing-p139-img04.png?alt=media)

Control Box Pin Definition Description Remark 3 EM01 External emergency Normally closed, short-circuited by stop 1 default 4 EM02 5 EM011 External emergency Normally closed, short-circuited by stop 2 default 6 EM012 Used to run the palletizing project. DI11 needs to be configured as Start. For DI 7 R1\_IN11 Start button input configuration method, please refer to DobotStudio Pro help document. Used to stop the palletizing project. 8 R1\_IN12 Stop button input DI12 needs to be configured as Stop. Used to clear the robot alarms. DI13 9 R1\_IN13 Reset button input needs to be configured as Clear alarm. Used to connect the Running indicator 10 R1\_OUT11 Running status output light. 11 R1\_OUT12 Stop status output Used to connect the Stop indicator light. Used to connect the Alarm indicator 12 R1\_OUT13 Alarm status output light. Safety input power 13 R1\_SI24V Used for safety I/O. +24V 14 R1\_SI9 Protective stop reset Used for protective stop reset function. SI9 needs to be configured as Protective stop reset. For SI 15 R1\_SI10 Protective stop reset configuration method, please refer to DobotStudio Pro help document. If an external emergency stop switch is required (dual-channel normally closed), connect it as follows.

_Figure 9.18 External emergency stop switch wiring_

![Figure 9.18 External emergency stop switch wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FT6ZQS9mcX7W8Lo9LsZZb%2Fpalletizing-p140-img02.jpg?alt=media)

If an external control button is required, connect it as follows.

_Figure 9.19 External control button wiring_

If an external status indicator is required, connect it as follows.

_Figure 9.20 External status indicator wiring_

If an external protective stop reset button is required, connect it as follows (use a dual control button).

_Figure 9.21 External protective stop reset button wiring_

![Figure 9.19 External control button wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLCxzaaJA17kEYeboXszw%2Fpalletizing-p141-img02.png?alt=media)

![Figure 9.20 External status indicator wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7xryWL6g3vWOTuJVpZwB%2Fpalletizing-p141-img03.jpg?alt=media)

![Figure 9.21 External protective stop reset button wiring](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK0QC2imwZpTVU157nF7r%2Fpalletizing-p141-img04.jpg?alt=media)

## 10. Maintenance

Maintenance and repairing must be performed in compliance with all safety instructions in this document. The purpose of maintenance and repairing is to ensure that the system is kept operational, or to return the system to an operational state in the event of a fault. Repairing includes troubleshooting in addition to the actual repair itself. Repairing must be performed by an authorized system integrator or DOBOT staff. Robots or parts returned to DOBOT should follow the instructions below:

* Remove all parts that do not belong to DOBOT.
* Before returning to DOBOT, please make a backup copy of the files. DOBOT will not be responsible for the loss of programs, data or files stored in robot.
* The robot should move to the package point before returning to DOBOT.

To maintain high performance for the robot over a long period of time, maintenance checks must be carried out. The personnel in charge of the maintenance must prepare a maintenance plan and carry out the maintenance. The maintenance items are shown below.

_Table 10.1 Maintenance item_

Period Maintenance Content item 1 week 1 months 3 months Make sure the suction cups and air tubes are free of any √ Suction cup cracks, defects, wear and deformation, and replace if necessary. Make sure all safety signs are securely attached and clearly √ Safety signs marked, and replace if necessary. Press the emergency stop Emergency √ button and observe whether stop button the workstation is powered off. Refer to the screw tightening √ Screws torque table to confirm the torque.

The bolt tightening torques are shown in the table below.

_Table 10.2 Bolt tightening torques_

Nominal diameter Outer hex bolt Inner hex bolt Inner hex bolt of thread (joint) (12.9) (rear cover) 3 mm 2 Nm 2.4 Nm 0.7 Nm 4 mm 4 Nm 4.5 Nm - 5 mm 7.5 Nm 9 Nm - 6 mm 15 Nm 18 Nm - 8 mm-37 Nm - The tightening torques vary depending on the type of base metal or bolt. When it is not specified, please contact DOBOT technical support engineer.

## 11. Warranty

### 11.1 Product warranty

Without prejudice to any claim agreement that the user (customer) may reach with the distributor or retailer, the manufacturer shall guarantee the quality of the products to the customer in accordance with the terms and conditions below: If defects caused by manufacturing and/or improper material occur in a new device and its components within 12 months (15 months at most if the shipping time is included) after the device is put into use, DOBOT shall provide the necessary spare part, and the user (customer) shall offer personnel to replace the spare part, using another part that represents the latest technology level to replace or repair the related part. If the device defects are caused by improper handling and/or failure to follow the relevant information set out in the User Guide, the warranty is invalid. This warranty does not apply to or extend to maintenance (e.g. installation, configuration, software download) performed by the authorized distributer or customer. The user (customer) must provide the purchase receipt and the purchase date as valid evidence for the warranty. Claims under this warranty must be made within two months of the apparent failure to perform the product warranty. The ownership of the device or components that are replaced or returned to DOBOT shall remain with DOBOT. Any other claims arising from or related to the device are not covered by this warranty. Any items in this product warranty do not intend to limit or exclude the legal rights of the customer or to limit or exclude the liability of the manufacturer for the personnel casualty resulting from its negligence. The duration of this product warranty shall not be extended due to the services provided under the product warranty terms. Under the principle of not violating the warranty, DOBOT reserves the right to charge customers for the replacement or maintenance. The foregoing does not imply a change in the burden of proof to the detriment of the client. If there are defects on the device, DOBOT shall not be liable for any damage or loss arising therefrom, including but not limited to loss of production or damage to other production device.

### 11.2 Disclaimer

DOBOT is committed to improve the reliability and performance of its products, and as such reserves the right to upgrade products without prior notice. DOBOT strives to ensure the contents of the User Guide are precise and reliable, but takes no responsibility for any errors or missing information.

## Appendix A Terms

A.1 Single pick-and-place and Multi pick-and-place The default suction cup supplied with the palletizing workstation is a single-channel type, which only supports single pick-and-place, meaning it can pick up and place one box at a time. If higher work efficiency is required, you can contact DOBOT Technical Support to evaluate and customize multi-channel suction cups. These multi-channel suction cups support various modes, including single pick-and-place, double pick-and-place (handling two boxes at a time), double pick single place (picking two boxes at once and placing them individually one by one), Triple pick-and-place (handling three boxes at a time), and Quadruple pick-and-place (handling four boxes at a time). The working principle and operation of multi-channel suction cups remain consistent. Here takes double pick-and-place as an example, when performing this operation, the two boxes must be treated as a single unit to determine the picking point and the tool coordinate system, as illustrated in the figure below. Figure A.1 Double pick-and-place When using a dual-channel suction cup for single-pick-and-place, only one side of the channel is used to pick up a box, as shown in the figure below. There is no need to separately configure the picking point and tool coordinate system for this situation. The system will automatically calculate these based on the box sizes and other parameters. Figure A.2 Single-pick with dual-channel suction cup

![Figure A.1 Double pick-and-place](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fi8W9NlN0rzu2h6MXT1aN%2Fpalletizing-p145-img02.png?alt=media)

![Figure A.2 Single-pick with dual-channel suction cup](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSoeP1mE5HiwwX1hnM4cY%2Fpalletizing-p145-img03.png?alt=media)

A.2 Picking posture The posture of the robot arm's end effector during each pick will be the same as the posture taught by the user when setting the picking point. Therefore, when teaching the picking point, users must ensure that the center of the suction cup aligns with the center of the box and that the long edge of the suction cup is parallel to the long edge of the box. The specific posture can be referenced in the figure below. Figure A.3 Picking posture Based on the orientation of the box, the recommended picking posture is as follows (using the left or right pallet user coordinate system):

* When the long edge of the box faces the workstation, set the picking point RZ to 90°.

Figure A.4 Picking posture 1

* When the short edge of the box faces the workstation, set the picking point RZ to 180°.

Figure A.5 Picking posture 2

![Figure A.3 Picking posture](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWj6tmZhYwg0zVlpg6IBZ%2Fpalletizing-p146-img02.jpg?alt=media)

![Figure A.4 Picking posture 1](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0kuZGSfQup7K9oBTi2s9%2Fpalletizing-p146-img03.png?alt=media)

![Figure A.5 Picking posture 2](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8U0dvFfMl4Ck9wEkeSKi%2Fpalletizing-p146-img04.png?alt=media)

A.3 Interlayer Users can add interlayers between layers of boxes based on their specific needs. The palletizing workstation will, according to the user-specified interlayer parameters, periodically pick up an interlayer from the designated stacking zone and place it onto the completed stack before proceeding to palletize the next layer of boxes. Figure A.6 Interlayer During depalletizing, the system will automatically remove the interlayer from the boxes and place it back into the stacking zone after every few layers.

![Figure A.6 Interlayer](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNicuzP2MVuJOZ5eIn4HH%2Fpalletizing-p147-img02.jpg?alt=media)
