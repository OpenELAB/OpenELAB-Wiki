---
description: >-
  Quick-start guide for DOBOT ATOM humanoid robots, covering safety, product
  configuration, technical specifications, unpacking, startup, remote control,
  shutdown, charging, and transport.
---

# DOBOT ATOM Humanoid Robot Quick Start

## DOBOT Atom Max EDU Humanoid Robot for Embodied AI Education

{% embed url="https://openelab.io/products/dobot-atom-max-edu-humanoid" %}

## DOBOT Atom Max Research Humanoid Robot Without Dexterous Hands

{% embed url="https://openelab.io/products/dobot-atom-max-research-humanoid" %}

## Contents

* Preface
* 1\. Safety Instructions
* 2\. Product Introduction
* 3\. Quick Start
* 4\. Common Issues and Solutions
* 5\. Maintenance

Copyright © SHENZHEN DOBOT CORP LTD 2025. All rights reserved. No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as "Dobot"). Disclaimer To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided AS IS, which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents. Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot is used on the premise of fully understanding the robot and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document. The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot. SHENZHEN DOBOT CORP LTD Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China Website: www.dobot-robots.com

## Preface

This document describes the functions, technical specifications, installation instructions of Dobot ATOM humanoid robot, making it easy for users to fully understand and use ATOM.

### Scope of application

* DOBOT Atom – Max
* DOBOT Atom-Trainer
* DOBOT Atom-Standard
* DOBOT Atom D-Data Collection

### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

### Revision history

Date Version Revision history 2025/09/04 V1.1 Updated the robot charging time

### Symbol conventions

The symbols that may be found in this document are defined as follows. Symbol Description Indicates a hazard with a high level of risk which, if not avoided, could

**DANGER**

result in death or serious injury. Indicates a hazard with a medium level or low level of risk which, if not

**WARNING**

avoided, could result in minor or moderate injury, robot damage. Indicates a potentially hazardous situation which, if not avoided, could

**NOTICE**

result in robot damage, data loss, or unanticipated result. Provides additional information to emphasize or supplement important

**NOTE**

points in the main text.

## 1. Safety Instructions

### 1.1 Safety warning sign

The following safety warning signs may appear on the product, and their meanings are as follows: Symbol Description Indicates a high potential hazard that, if not avoided, could

**DANGER**

result in death or serious injury. Indicates a potentially dangerous electrical situation that, if not ELECTRICITY avoided, could result in injury, death, or serious damage to the equipment. HOT Indicates a potentially dangerous hot surface that, if touched, could result in personnel injury. Indicates a moderate or low potential hazard that, if not

**WARNING avoided, could result in minor personal injury and damage to**

the equipment. Indicates a potentially hazardous situation which, if not

**NOTICE avoided, could result in robot damage, data loss, or**

unanticipated result. Indicates a situation that, if not avoided, could result in personnel injury or damage to the product. For items marked CAUTION with such signs, depending on the specific situation, this may lead to significant consequences.

### 1.2 General safety

Please operate the robot in an indoor environment with a working temperature range of -5°C to +40°C. Follow the safety instructions below when starting and using the robot for the first time.

**DANGER**

* Please comply with local laws and regulations strictly. The safety precautions described in this document serve only as a supplement to local safety standards.
* Avoid using the robot in harsh environments such as wet, high-temperature, strong magnetic, or high-radiation conditions.
* Minors, untrained individuals, or persons with limited physical / sensory abilities must not operate the robot.
* Unauthorized modification or disassembly of the robot by non-professionals is strictly prohibited.
* Stop and power off the robot immediately when the battery is low to prevent damage from automatic shutdown and falling.

HOT The robot generates heat during operation. Avoid touching the motor surface while it is running to prevent burns.

**WARNING**

* It is prohibited to modify or remove the nameplate, instructions, icons, or labels on the robot.
* Do not obstruct the robot's sensor areas (head, wrists, waist). Blockage may impair detection accuracy and cause system malfunction.
* If the robot exhibits abnormal operation, immediately press the "LB + A" buttons on the remote controller to put the robot into damping mode. The robot will slowly fall to the ground.
* If remote stop or other operations fail to take immediate effect, promptly press

E-stop button A or B to trigger the emergency stop function and ensure safety.

* During the installation process, the robot must be held by personnel to prevent any collisions that could lead to surface scratches or functional damage.
* Make sure that the robot has sufficient space to move freely. Do not approach the robot while it is in operation.
* Do not continue using the robot if it is damaged.

**NOTICE**

* Personnel responsible for the installation, operation, maintenance, and servicing of the robot must undergo rigorous training, be fully aware of all safety precautions, and master the correct operation and maintenance procedures.
* In case of a malfunction, contact Dobot's technical support engineer in time.
* Perform daily inspections and regular maintenance, and promptly replace any faulty components.
* Dobot assumes no responsibility for robot damage or personal injury caused by improper operation or failure to follow the product’s instructions for use.
* Robot Handling operations must be conducted using appropriate and reliable lifting devices, and must be carried out by qualified personnel or those authorized by the company in accordance with local regulations.
* Do not move or transport the robot while it is powered on.
* Dobot is not responsible for any damage caused during the transportation and handling of the robot.
* Make sure that the packing and unpacking area are free of obstacles to allow staff to evacuate quickly in case of emergencies.
* When transporting the robot, secure the packaging properly to prevent tilting or shaking.
* During debugging, make sure that no personnel or other equipment (including computer used for debugging) is present in the hazardous area of the machine.
* When the robot is in motion, ensure the surrounding area is clear. Always use a tether or protective frame to prevent falls, which may damage the robot or cause injury to personnel.
* If you need a long standby time, please hang the robot on the protective frame and secure it, which can avoid the robot from automatically shutting down and falling down due to low battery.

### 1.3 Personal safety

When using the robot, please strictly follow the general precautions listed below to ensure the personal safety.

**WARNING**

* Comply with local laws or regulations with regard to the maximum weight one person is permitted to carry.
* After powering on the robot, do not touch it with your hands.
* When using the robot, avoid wearing loose clothing or jewelry. Keep fingers, hair, and clothing away from joints, gaps, and moving parts to prevent pinching or entanglement.

## 2. Product Introduction

### 2.1 Product overview

The Dobot ATOM series is the world's first "Dexterous Manipulation + Straight-Knee Walking" embodied AI humanoid robot, independently developed by Dobot. The robot features a full joint hollow routing and a 1:1 full-scale humanoid arm design. It is equipped with a 7-DOF industrial-grade bionic collaborative arm (±0.05mm repeat positioning accuracy), a synchronized humanoid head, and a five-fingered dexterous hand. Powered by embodied AI operation models and AI edge computing, it enables “collection, training, and inference” for specific application scenarios. The Dobot ATOM robot is ideal for continuous and repetitive tasks in scenarios where equipment positions are not fixed, products vary in specifications, operations involve a high degree of similarity, and there is a need to navigate through short, confined spaces with agile turning capabilities. Examples include industrial tasks like automotive assembly line material handling, beverage preparation in coffee shops, and pharmacy nighttime dispensing.

### 2.2 Appearance

* DOBOT Atom-Max / DOBOT Atom-Trainer

![Official manual figure, page 8](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZ6B4xWAwpkDjKth4rUN2%2Fatom-max-p008-img01.png?alt=media)

* DOBOT Atom D-Data Collection

### 2.3 Technical specifications

DOBOT Atom D-Data Product model DOBOT Atom-Max DOBOT Atom-Trainer Collection Height About 1650mm About 1650mm About 650mm Weight (Without dexterous About 62kg About 62kg About 20kg hand/gripper) Total Degrees of Freedom 29 29 16 (Without dexterous hand/gripper) Head Degrees of 2 2 2 Freedom Single Arm Degrees of Freedom 7 7 7 (Without dexterous hand/gripper) Waist Degrees of 1 1 0 Freedom Single Leg Degrees of 6 6 0 Freedom Arm's Reach (Without dexterous 600 mm 600 mm 600 mm hand/gripper) Single Arm Weight (Without dexterous About 6.8kg About 6.8kg About 6.5kg hand/gripper) Single Arm Payload (Without dexterous 3.5 kg 3.5 kg 3.5 kg hand/gripper) Single Arm Repeated ±0.05mm ±0.05mm ±0.05mm Positioning Accuracy Maximum End Speed of 1.5 m/s 1.5 m/s 1.5 m/s the Arm 360° Omnidirectional 360° Omnidirectional Audio Equipment Microphone x 1 Microphone x 1 - Neodymium Speakers x 2 Neodymium Speakers x 2 Maximum Walking 1.5 m/s 1.5 m/s - Speed Full Joint Hollow Yes Yes Yes

![Official manual figure, page 9](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZ03jNlfPdkhibkVYFttp%2Fatom-max-p009-img01.png?alt=media)

Basic Computing Power Intel i5 Intel i5 Intel i5 Intel i9 (24 Cores 32 Intel i9 (24 Cores 32 Threads) Threads) High Computing Power High-Memory Dedicated High-Memory Dedicated - Module 1500 TOPS Graphics Card (FP32 GPU Graphics Card (FP32 GPU Computing Power: 41.15 Computing Power: 41.15 TFLOPS) TFLOPS) Battery Life About 2h About 2h About 2h Charging About 2h About 2h About 2h End Effector 6-DoF Dexterous Hand x 2 0 - Depth Camera x 1 Depth Camera x 1 Depth Camera x 1 Head Sensor High-Definition Stereo High-Definition Stereo High-Definition Stereo Camera x 1 Camera x 1 Camera x 1 Wrist Sensor Depth Camera x 2 Depth Camera x 2 - Waist sensor Depth Camera x 2 Depth Camera x 2 - Head LiDAR 3D LiDAR × 1 3D LiDAR × 1 - Secondary Support Support Support Development Warranty 1 year 1 year 1 year

### 2.4 Camera and radar field of view

* Head Depth Camera Field of View

The DOBOT ATOM-Max / DOBOT ATOM - Trainer / DOBOT ATOM-Data Collection are equipped with a head depth camera, enabling the robot to perceive and understand its surroundings with greater accuracy. The head depth camera has a field of view as shown in the right figure:

* Head High-Definition Stereo Camera

Field of View The DOBOT ATOM-Max / DOBOT ATOM - Trainer / DOBOT ATOM-Data Collection are equipped with a head high-definition stereo camera, combined with a depth camera, enhancing the robot's spatial perception and obstacle detection capabilities. The head high-definition stereo camera has a field of view as shown in the right figure:

* Head LiDAR Field of View

The DOBOT ATOM-Max / DOBOT ATOM - Trainer are equipped with head LiDAR, enabling real-time acquisition of precise environmental data and providing the robot with advanced environmental perception capabilities. The head LiDAR has a field of view as shown in the right figure:

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHnxuvMAPbBQAUTra8Is7%2Fatom-max-p011-img01.png?alt=media)

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgFbMLghA7gm5akyon33q%2Fatom-max-p011-img02.png?alt=media)

![Official manual figure, page 11](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fe0JEejKNiaB2gkgGBq9F%2Fatom-max-p011-img03.jpg?alt=media)

## 3. Quick Start

### 3.1 Unpacking

**NOTE**

The subsequent figures use the DOBOT ATOM-Max as reference. Other ATOM series models differ only in design while maintaining identical operation procedures. Please refer to the product you received for accurate appearance details.

1. Upon receiving the robot, please check the outer packaging to ensure it is in good

condition. If any damage is found, promptly contact the logistics company and your local supplier.

2. After opening the outer packaging, please verify the items against the unpacking

checklist included with the product shipment. If any items are missing, promptly contact after-sales support for a replacement.

### 3.2 Battery pack charging

Due to battery self-discharge during transportation and storage, it is normal for the robot to have low or empty battery power upon first use. Please charge the battery pack according to the following procedure:

1. Remove the battery pack: After unpacking, take out the battery pack and the

charger set. Check for any missing components.

![Official manual figure, page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC8SRkCdS7XQ1EXz4YuQ2%2Fatom-max-p012-img01.png?alt=media)

![Official manual figure, page 12](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh2tOMQiWWKYSCUBSAOf4%2Fatom-max-p012-img02.png?alt=media)

2. Connection: Connect the battery pack to the charger set as shown in the figure

below. Connect one end of the AC charging cable to the SP2425 charging module, ① and the other end to an AC power outlet. Connect one end of the charging module power cable to the SP2425 ② charging module, and the other end to the POWER port of the CM1620 charging module. Connect one end of the USB cable to the HOST port of the CM1620 charging ③ module, and the other end to the control unit. Connect the BATTERY port of the CM1620 charging module to the IN port ④ of the charging dock.

3. Turn on the AC supply: After checking all connections, turn on the AC socket

switch.

4. Turn on the SP2425 charging module: Switch the rocker switch on the SP2425

charging module to the "I".

5. Activate the battery pack: Short-press the power button on the battery pack

once, then long-press for 3 seconds. The battery pack is successfully turned on when all four power indicator lights illuminate in sequence and then blink.

![Official manual figure, page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIgwvunSq1cWi4biDRC70%2Fatom-max-p013-img01.jpg?alt=media)

![Official manual figure, page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaZWrTq6QIanqCf7GweOa%2Fatom-max-p013-img02.png?alt=media)

6. Start charging: After powering on the control unit, follow the steps below to begin

charging the battery pack. 1) Press the O key to return to the main interface. 2) First, press the ˅ button to select "Start", then press the O key to confirm. 3) First, press the ˄ button to select "√", then press the O key to confirm and start charging.

![Official manual figure, page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F42BSA0b3ys38WZxsV1ie%2Fatom-max-p014-img01.png?alt=media)

![Official manual figure, page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBEXBDpp0ry2twpbio7e9%2Fatom-max-p014-img02.png?alt=media)

![Official manual figure, page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1MACqAIYaf3H0n9wPr5q%2Fatom-max-p014-img03.png?alt=media)

![Official manual figure, page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOhcBDv38MWS0TAApDPxv%2Fatom-max-p014-img04.png?alt=media)

4. During the charging process, the control unit will display real-time data. When all four power indicator lights on the battery pack are steadily illuminated and the control unit displays 67.2V, it indicates that the battery pack is fully charged.

**NOTE**

If charging continues when the battery pack is already fully charged, the overcharge protection of the battery pack will be triggered, and the control unit will display a charging error.

7. Stop charging: After the battery is fully charged, first press the O button on the

control unit to return to the main interface. Then press ˅ to select "Stop", and finally press the O button to confirm and stop charging.

8. Power off the battery pack: Long-press the battery pack’s power button for 3

seconds. The four battery indicator lights will dim sequentially, indicating that the battery pack is powered off.

9. Disconnect the AC power: Set the rocker switch of the SP2425 charging module

to the O, then manually unplug the AC power plug.

![Official manual figure, page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3s35Fk1Zqvf76eYy1Oco%2Fatom-max-p015-img01.png?alt=media)

![Official manual figure, page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4LwE0nGTl15cDajqNMja%2Fatom-max-p015-img02.png?alt=media)

![Official manual figure, page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Foiitk1jrgF8WbTKPGdAq%2Fatom-max-p015-img04.png?alt=media)

**NOTICE**

* Always use the official Dobot charger provided with your device. Using unofficial chargers to charge the battery pack is strictly prohibited.
* Operating temperature range for the charger: -20°C to +60°C. Charging voltage: DC 67.2V. The default charging current is 5A, which can be adjusted via the control unit but must not exceed 10A (it is recommended to keep the default value of 5A).
* Before connecting to an AC power source, ensure that the voltage of the

AC supply matches the charger's rated input voltage. Failure to do so may damage the charger.

* Before charging, ensure that the battery pack is turned off; otherwise, it may damage both the battery pack and the charger.
* When all four battery indicator lights are steadily on, it indicates that the battery pack is fully charged. Please disconnect the battery pack from the charger promptly.
* The battery pack must cool down to room temperature before recharging.
* If smoke, unusual odors, overheating, or deformation occur during charging, immediately unplug the charger.
* If battery electrolyte accidentally gets into the eyes, immediately rinse thoroughly with plenty of clean water and seek medical attention without delay.

### 3.3 Check the battery pack level

Short-press the battery pack’s power button to check the remaining battery level based on the indicator lights.

**NOTE**

* The battery indicator lights are labeled LED0 to LED3 from left to right, with LED0 on the far left and LED3 on the far right.
* Battery indicator icon meanings: Off

, Steady on, Fast Flashing, ○ ● ◉ Slow Flashing. ◎

![Official manual figure, page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcZMQer0UHIpydrXY8T5T%2Fatom-max-p016-img03.png?alt=media)

Battery indicators SOC status LED0 LED1 LED2 LED3 ○ ○ ○ ○ SOC ≤ 10 (Unable to discharge) ○ ○ ○ 10＜SOC≤20 ◉ ○ ○ ○ 20＜SOC≤30 ●◎ ○ ○ ○ 30＜SOC≤40 ● ○ ○ 40＜SOC≤50 ● ●◎ ○ ○ 50＜SOC≤60 ● ● ○ 60＜SOC≤70 ● ● ●◎ ○ 70＜SOC≤80 ● ● ● 80＜SOC≤90 ● ● ● ●◎ 90＜SOC≤100

### 3.4 Suspension before powering on

1. Prepare the robot: Place the packaging box in an appropriate position under the

hoist and extend the robot's arms and legs outward.

**NOTICE**

During the entire hoisting process, someone needs to hold the robot's hands and legs throughout to avoid bumping or damaging the robot.

2. Suspension preparation:

Grab the fixed ring on the back of the robot to slightly lift it away from the inner ① lining of the packaging box. Attach the hoist hook to the fixed rings on both shoulders of the robot. ②

![Official manual figure, page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnJqMz4LK3iJfm24RcGSW%2Fatom-max-p018-img01.jpg?alt=media)

![Official manual figure, page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsEiDx2IpO8HAy8Ct57Hz%2Fatom-max-p018-img02.jpg?alt=media)

3. Raise the robot: Use the hoist to slowly raise the robot, and once the robot is

out of the packaging box, remove the packaging box.

4. Straighten the robot: As the hoist raises the robot, use your hands to support

the robot's arms and legs to slowly lower it down, until the robot's two feet are close to the ground but not touching it (in a suspended state). Ensure that the robot's arms and legs are naturally positioned, with no entanglement in the joints.

![Official manual figure, page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7KFld3owKNTdWDpqU7vV%2Fatom-max-p019-img01.png?alt=media)

![Official manual figure, page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdyqZBol0IYVTAw35hH77%2Fatom-max-p019-img02.png?alt=media)

5. Install the battery pack

Hold the battery pack with Gently push buckles to both sides ① ② one hand, pinch the buckle to ensure they are securely fixed in the middle with the other in place. After installation, lightly hand, and push the fully pull the battery pack to ensure charged battery pack into there is no looseness. the battery slot on the back of the robot.

6. Activate the battery pack: Before powering on the battery pack, please adjust

the robot's head to a straight position (level and facing forward). Then short-press the battery pack’s power button once, and long-press for 3 seconds. The four indicator lights illuminate in sequence and then flash, indicating that the battery pack has been successfully activated.

**NOTICE**

If the robot's head is not properly positioned (e.g., the head is drooping), powering on may trigger a limit alarm.

7. Start the robot: After the robot passes the self-check, it enters the zero-torque

state. At this point, you can connect to the App to check if the robot has any errors. If there are no errors, you can follow the steps below to switch different robot modes.

![Official manual figure, page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsL54pJYGblkLOvbdNjuc%2Fatom-max-p020-img01.png?alt=media)

![Official manual figure, page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxjefHZv6dUOFDHm8uAXn%2Fatom-max-p020-img03.png?alt=media)

![Official manual figure, page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Frf0HmdIvjYPC7hwGABwB%2Fatom-max-p020-img04.png?alt=media)

Prepare for Bent-Knee Walking Mode

**NOTICE**

After entering the Prepare for Bent-Knee / Straight-Knee Walking Mode, the robot will interpolate within 10 seconds to transition to the default joint angles of the bent-knee model or straight-knee model (non-operable). During this process, the robot needs to be hoisted to suspend in the air or have personnel hold it to prevent it from falling.

8. Lower the suspension rope: Make ATOM's feet touch the ground, press the

RB+A button on the remote controller to enter the Bent-Knee / Straight-Knee Walking Mode (the specific walking mode entered depends on the prepared mode in the previous step).

**NOTICE**

During the descent of the suspension rope, personnel must hold onto ATOM to ensure it remains upright and stable, with the suspension rope slack and free of tension.

9. Release the suspension rope: Once ATOM's movement is confirmed normal,

untie the rope and control the robot via remote controller.

![Official manual figure, page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj8uf0Vv6s7j6Pq2aCB2L%2Fatom-max-p021-img02.png?alt=media)

**NOTICE**

In case of an emergency, press LB+A to put the robot into damping state, and the robot will slowly fall to the ground.

### 3.5 Connect to Dobot Ex app

1. Please contact Dobot technical support to obtain the Dobot Ex App installation

package, download and install it.

2. Double-click to open the Dobot Ex App and log in using the enterprise account

and password provided by the sales.

**NOTE**

If you do not have an enterprise account, please contact DOBOT sales service personnel to obtain one.

3. Power on ATOM by following the Suspension before powering on procedure.
4. Turn on the phone's WiFi switch and connect to the WiFi named "ATOM+SN

code" (default password: 12345678).

5. On the initial interface of the Dobot Ex App, click the "Connect" button. When the

interface displays the ATOM appearance and battery level, it indicates that the connection has been completed. Robot not connected Robot connected

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOiUCxdtsvXhql9Za3gBW%2Fatom-max-p022-img01.png?alt=media)

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUEqYD6pQV4IOKBCRkgcl%2Fatom-max-p022-img02.png?alt=media)

![Official manual figure, page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDeFE2BbFIOP39XwDz38l%2Fatom-max-p022-img03.png?alt=media)

### 3.6 Connect to remote controller

Before using the remote controller, switch the top button to the "X" mode, and press the MODE button to turn off the indicator light. The ATOM robot will automatically connect to the remote controller after powering on. You can control the robot's motion direction and motion state using the joystick and buttons on the remote controller.

**NOTICE**

* The remote controller must be strictly set to "X" mode. After switching mode, the robot needs to be powered on again.
* During the use of the remote controller, the MODE indicator light must always remain off.

### 3.7 Basic operations

#### 3.7.1 View ATOM information

After connecting the robot using the App, you can enter the "Device" page to view robot information such as robot mode, version information, joint information, alarm information, etc., and configure some functions. "Device" page "Device > Robot Settings" "Device > Data" "Device > Alarm Information"

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiROdYPDjtBzuTRaAQkuA%2Fatom-max-p023-img01.png?alt=media)

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBor8N3dK4W4llIx6w9UF%2Fatom-max-p023-img02.png?alt=media)

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4c20NWcVjabWkNBOPpqO%2Fatom-max-p023-img03.png?alt=media)

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdvU26wXlgCvuQFBHgAAv%2Fatom-max-p023-img04.png?alt=media)

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZruUDd6xBLi01OSFpPFu%2Fatom-max-p023-img05.png?alt=media)

![Official manual figure, page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJ4KUwF8gzotzHQTA9WHv%2Fatom-max-p023-img06.png?alt=media)

#### 3.7.2 Control movement and steering

First, make sure the MODE button indicator light on the remote controller is always off, then use the left joystick on the remote controller to move the robot forward and backward, and the right joystick to turn the robot left and right. As shown in the figure below:

#### 3.7.3 Switch robot states

The robot's states can be switched using the following combined buttons on the remote controller.

![Official manual figure, page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLehfMqQ4mniwxCW5dzCN%2Fatom-max-p024-img01.png?alt=media)

![Official manual figure, page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft6qmzWwFBY2lG3IwJQN2%2Fatom-max-p024-img02.jpg?alt=media)

![Official manual figure, page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqtI1FgUuOnevbfFXZWs5%2Fatom-max-p024-img03.png?alt=media)

![Official manual figure, page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC0VKNUELcYYNpcftXwZn%2Fatom-max-p024-img04.png?alt=media)

Remote controller Robot status Description buttons All robot motors will stop active movement, Zero Torque LB+B and there is no damping sensation during State swinging. All robot motors will stop active movement, LB+ A Damping State and there is a noticeable damping sensation during swinging. Development and debugging based on the underlying control SDK. Acquire real-time LT+RT Debugging State operation data (battery, motors, IMU, etc.) and directly drive the motors. Controls joint positions to switch the robot to a specific diagnostic posture. Press LT+B to LT+ A Diagnostic State switch from diagnostic mode to debugging mode. The robot slowly assumes a squatting LB+DOWN Squatting state posture within 5 seconds (without balance control). Prepare for The robot slowly assumes the prepared LB+UP Locked Standing posture before the motion mode within 5 Posture seconds (without balance control) The robot slowly assumes a sitting posture LB+LEFT Sitting State within 5 seconds (without balance control). Prepare for The robot slowly assumes a prepared RB+B Straight-Knee posture for straight-knee walking within 5 Walking seconds (without balance control). The robot slowly assumes a prepared Prepare for Bent- RB+X posture for bent-knee walking within 5 Knee Walking seconds (without balance control). First press RB+X to control the robot into a prepared posture for bent-knee walking, RB+X  Bent-Knee then press RB+A to enter the bent-knee RB+A Walking Mode walking mode, to be used as a prepared posture before the motion state and skill state. First, press RB+B to control the robot into the prepared posture before straight-knee RB+B  Straight-Knee walking, then press RB+A to enter the RB+A Walking Mode straight-knee walking mode, to be used as a prepared posture for motion state and skill state.

### 3.8 Debugging instructions

1. Hang the ATOM robot and press the LB+A button on the remote controller to

control it in damping state.

2. Press the LT+RT button on the remote controller, and ATOM will enter debugging

state. Under debugging state, the robot defaults to a damping state. Development and debugging can be performed using the underlying control SDK to directly drive the motors. It supports customized teleoperation, deployment and control of reinforcement learning models, as well as real-time monitoring of battery, motor, and IMU data. The interface for debugging is located under the fixing ring on the back of the robot, and can be accessed by uncovering the silicone shell, as shown in the figure below:

3. Press the LT+A button, and ATOM will enter diagnostic state and assume a

specific diagnostic posture. Press the LT+B button again, and ATOM will return to debugging state.

**NOTE**

This process is used to confirm whether ATOM has successfully entered the debugging state or for hardware troubleshooting.

![figure below:](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FStxm41HXIp9MF2nu4H93%2Fatom-max-p026-img01.png?alt=media)

### 3.9 Emergency stop instructions

The robot can be controlled to stop immediately using the following methods, please ensure the robot is protected before performing an emergency stop to avoid accidental damage.

* Soft E-stop

In the event of an emergency, the robot can be controlled to enter a damping state by pressing the LB+A button on the remote controller and slowly fall to the ground.

* Hard E-stop

Press the wireless E-stop button A or B that is shipped with the robot to immediately trigger the robot's emergency stop mode. After triggering the emergency stop, the robot needs to be restarted to function normally.

**NOTE**

The wireless E-stop button A is used to toggle the switch of the joint power, while the button B is used to toggle the switch of the control power (excluding the joint power). When the control power is powered off, the joint power will also be powered off.

### 3.10 Suspension before powering off

Before powering off, please make sure to rehang the ATOM onto the protective frame and secure it with a rope to keep it suspended. Ensure the robot is in the initial position after a successful start, with no arm operations and standing still.

1. Press the LB+A button on the remote controller to control the robot into damping

state.

2. First, short-press the battery pack’s power button once, then long-press for 3

seconds to power it off (the four power indicators will dim one by one).

**NOTICE**

* If the robot is not used for a long time, please remove the battery pack in time.
* Ensure the robot is suspended on the protective frame and shut down in a damping state; otherwise, the robot may fall to the ground after powering off, which could pose a safety hazard.
* Be careful of the robot joints pinching your hand.

## 4. Common Issues and Solutions

Issue Cause Solution The robot cannot be The battery pack is depleted Check the battery level and charge it. powered on After the robot is powered Restart the robot using the battery Joint power switch is turned off on, the self-check fails pack’s power button. Contact technical support for calibration. The zero point data has been The robot's zero point data lost unexpectedly, or a: The robot has completed zero is incorrect physical impact resulting in point calibration before leaving the zero point offset factory. Please do not calibrate the joints during normal use.

**NOTE**

If you encounter any other abnormal issues during the use of the robot, please contact technical support promptly.

## 5. Maintenance

Maintenance and repairing must be performed in compliance with all safety instructions in this document. The purpose of maintenance and repairing is to ensure that the system is kept operational, or to return the system to an operation state in the event of a fault. Repairing includes troubleshooting in addition to the actual repair itself. Repairing must be performed by an authorized system integrator or Dobot staff. Robots or parts returned to Dobot should follow the instructions below:

* Remove all parts that do not belong to Dobot.
* Before returning to Dobot, please make a backup copy of the files. Dobot will not be responsible for the loss of programs, data or files stored in robot.
* The robot should be restored to its unpacked posture before returning to Dobot.

### 5.1 Safety instructions

The following safety procedures and warnings must be observed when operating the robot:

**NOTICE**

* Replace faulty components with new components of the same model or equivalent components approved by Dobot.
* Reactivate all deactivated safety measures immediately after completing maintenance work.
* Record all repairs and save them in the technical document associated with the robot system.
* Take necessary precautions to prevent others from re-powering on the robot during maintenance.
* Prevent water or dust from entering the interior of the robot.

### 5.2 Robot maintenance

To ensure the robot maintains high performance over the long term, regular maintenance checks must be conducted. The personnel in charge of the maintenance must develop a maintenance plan and carry out the necessary tasks. The inspection items are listed in the table below. Period Inspection item Inspection details Daily 3 months 6 months

* Store in a dry, dark room to avoid

√ direct sunlight and rain; Robot storage

* Remove the battery pack if storing for a long period.
* Check if the body is clean,

√ Robot appearance undamaged, or deformed;

* Check if the camera and radar are obstructed by dirt or debris.
* Wipe the robot with a dry and clean

√ Robot cleaning soft cloth;

* Check if the camera and radar are clean and dry.
* Check that there is no abnormal noise or vibration from the joints when the √ Joint robot is running.
* After running, touch the joint housing to check for excessive heat.
* Check if the battery pack is securely installed without any looseness;
* Check if no visible damage or swelling on the battery pack casing;
* Check if the power indicator light

√ Battery pack displaying normally;

* Check if the battery pack is sufficiently charged (when not in use for a long time, it is recommended to maintain a 50% charge and recharge every three months). √ Remote controller Check if the buttons and joystick of the remote controller are functioning properly; Press the E-stop button during the robot's √ E-stop button movement to observe if the robot performs an emergency brake.
