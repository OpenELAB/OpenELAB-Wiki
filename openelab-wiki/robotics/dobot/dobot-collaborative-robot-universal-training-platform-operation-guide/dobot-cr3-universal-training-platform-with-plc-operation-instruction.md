# DOBOT CR3 Universal Training Platform Operation Instruction - With PLC

## DOBOT Collaborative Robot Universal Training Platform - With PLC System Module

{% embed url="https://openelab.io/products/dobot-cobot-universal-training-platform?variant=46636171428038" %}

**Applies to:** CR3 training system with the PLC system module. Official source issue V1.1 (2026-02-11). The robot is purchased separately. Confirm the actual robot and PLC configuration before following wiring or software steps.

**Copyright © yuejiang Science and Technology Co., LTD 2022-2026. All Rights Reserved. All rights reserved.**

Without the written permission of the company, any unit or individual shall not extract or copy part or all of the content of this document without authorization, and shall not be transmitted in any form.

**Disclaimer** To the maximum extent permitted by law, the products described in this manual (including its hardware, software, firmware, etc.) are provided "as is" and may be defective, erroneous or faulty. Yuejiang does not provide any form of express or implied warranty, including but not limited to warranties of merchantability, quality satisfaction, fitness for a specific purpose, non-infringement of third party rights, etc. Nor will Yuejiang make any compensation for any special, incidental, incidental or indirect damages caused by the use of this manual or the use of the Company's products.

Before using this product, read this manual and related technical documents published on the Internet in detail and understand the relevant information, and ensure that the equipment is used under the premise of full understanding of the equipment and its related knowledge. Yuejiang recommends that you use this manual under the guidance of professionals. All safety information contained in this manual shall not be regarded as a guarantee of Dobot. Even if this manual and related instructions are followed, damage or loss caused by use may still occur.

It is the responsibility of the user of this product to ensure that the applicable laws and regulations of the relevant country are followed and that there is no significant risk in the use of the equipment.

### Yuejiang Technology Co., LTD

Address: 1003, 2, chongwen district, nanshan zhiyuan, no. 3370, liuxian avenue, nanshan district, shenzhen

Website: https://www.dobot.cn/

### Preface

**Purpose**

This document introduces the installation procedure and some operation demos (including Tricolor lamp, trajectory simulation, conveyor, static palletizing, vision sorting, phone chip assembly and dynamic tracking) of the CR3 general training system, which is convenient for users to understand and use the CR3 general training system.

**Note**

In this Document, DobotStudio Pro 2.6.1 is used for Robot Control, And DobotVisionStudio 4.1.2 is used for vision operation.

**Symbol Conventions**

The symbols that may be found in this document are defined as follows.

| **Symbol** | **Description**                                                                                                                                                            |
| ---------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER     | <p>Indicates a hazard with a high level of risk which, if not avoided, could result in<br>death or serious injury</p>                                                      |
| WARNING    | <p>Indicates a hazard with a medium level or low level of risk which, if not avoided,<br>could result in minor or moderate personal injury and damage to the equipment</p> |
| NOTICE     | <p>Indicates a potentially hazardous situation which, if not avoided, can result in<br>damage to the equipment, data loss, or unanticipated result</p>                     |
| NOTE      | <p>Provides additional information to emphasize or supplement important points in the<br>main text</p>                                                                     |

| _4.1 Vision program description.............................................................................................202_ |
| -------------------------------------------------------------------------------------------------------------------------------- |
| _4.2 Robot program description.............................................................................................203_  |

## Chapter 1 CR3 general training system Introduction

### 1. Safety Precautions

This section describes the safety precautions that should be noticed when you use this product. Please read this section carefully before using the training system for the first time. This product needs to be used in an environment meeting the design specifications. You cannot remold the product without authorization, otherwise, it may lead to product failure, and even personal injury, electric shock, fire, etc. People who use this product for system design and manufacture must be trained by Dobot or relevant institutions, or must have the same professional skills, and use the training system strictly following the regulations of this document.

#### 1.1 Safety warning signs

The following safety warning signs may appear in this document, and their meanings are described as follows, as shown in Table 1-1.

**Table 1-1 Safety warning signs**

| **Sign**    | **Description**                                                                                                                                                                                                                              |
| ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DANGER      | <p>Indicates a high degree of potential danger, which, if not avoided, will<br>result in death or serious injury.</p>                                                                                                                        |
| ELECTRICITY | <p>May cause dangerous power consumption soon, which, if not avoided,<br>will cause personal injury or serious damage to the equipment.</p>                                                                                                  |
| HOT         | <p>May cause dangerous hot surfaces, which, if touched, may cause<br>personal injury.</p>                                                                                                                                                    |
| WARNING     | <p>Indicates a moderate or low potential hazard, which, if not<br>avoided,<br>may<br>cause minor personal injury and damage to the equipment.</p>                                                                                            |
| NOTICE      | <p>Indicates a potential risk, which, if ignored, may result in damage to the<br>equipment, loss of data or unpredictable results</p>                                                                                                        |
| ATTENTION   | <p>A situation that, if not avoided, can cause personal injury or damage to<br>the equipment.<br>For items marked with such signs, depending on the specific situation,<br>there is sometimes a possibility of significant consequences.</p> |

#### 1.2 General Safety

Follow the safety instructions below when starting and using the training system for the first time.

**DANGER**  The training system is electrical equipment. Non-professional technicians should not modify the circuit, otherwise, it may cause damage to devices or personal injury.

 Comply with the local laws and regulations when operating the equipment The safety precautions in this document are only supplemental to the local laws and regulations.  Use the equipment in the specified environment scope. Exceeding the specifications or load conditions will shorten the service life of the product, even damage it.

 Ensure that the equipment is operated under the security conditions and there is no harmful object around the robot.

 Turning on or off the power continually may result in degraded performance of the main circuit components inside the controller. If turning on or off the power continually is required, please keep the frequency less than once per minute.

(2) NOTICE

 The personnel responsible for installation, operation and maintenance of equipment must first receive strict training, understand various safety precautions, and master correct operation and maintenance methods before they can operate and maintain the equipment.

 Personnel without professional training shall not disassemble and repair the equipment without authorization. If the equipment fails, please contact Dobot technical support engineer in time.

 Be sure to carry out daily inspections and regular maintenance, and replace faulty components in time to ensure the safe operation of the equipment.

**CR3 General Training System Operation Instruction**

 If the equipment is scrapped, please comply with relevant laws to properly handle industrial waste and protect the environment.

 In order to prevent personnel from accidentally entering the working space of the equipment, be sure to set up safety fence to prevent personnel from entering the hazardous area.

 Before operating the robot, make sure that no one is inside the safety fence. When operating the robot, be sure to operate outside the safety fence.

 Do not expose the training system to permanent magnetic fields all the time. Strong magnetic fields can cause damage to the equipment.

 Dobot assumes no responsibility for equipment damage or personal injury caused by failure to follow product instructions or other improper operations.

 Dobot is not responsible for any damage caused during the transportation and handling of equipment.

 After removing the outer packaging, make sure that the robot maintains the original packing posture and the brakes of all axes are normal.

**WARNING**  Before the operation, please wear antistatic uniform and protective gloves.

 It is prohibited to modify or remove the nameplates, instructions, icons and marks on the equipment.

 Be careful when carrying or installing the equipment. Please follow the instructions on the packing box to put down the robot gently and place it correctly in the direction of the arrow.

 When handling the robot, you need to carry it with both hands, with one holding the upper arm or forearm and the other holding the base, so as to keep the robot stable and avoid the base rotating randomly or other axes loosening to cause injury.

 Please use the matched cables for personal security and equipment protection.

 Please ensure that the robot and tools are installed correctly.

* Please ensure that the robot has enough space to move freely.

 Any impact will release a lot of kinetic energy, which is much higher than

that under high speed and high load.

#### 1.3 Personal safety

When operating the robot system, please strictly follow the general precautions listed below to ensure the personal safety of the operator.

WARNING

 Please comply with local laws or regulations with regard to the maximum weight one person is permitted to carry.

 Do not touch the terminal blocks or disassemble the equipment with the power ON. Otherwise, it may result in an electric shock.

 Please confirm that the equipment is well grounded, otherwise it will endanger personal safety.

 Do not touch the terminal blocks or remove the interval circuit components within 10 minutes after the power is shut off, so as to avoid an electric shock since there is residual capacitance inside the equipment.

 Even if the power switch of the equipment is already in the OFF status, touching the terminal blocks or removing the interval circuit components is not allowed, so as to avoid an electric shock since there is residual capacitance inside the equipment.

 Please ensure that the safety measures are established near the robot operation area, such as guardrails, to protect the operator and surrounding people.

### 2. Product Introduction

The CR3 general training system is an educational solution designed for vocational and higher education to help students understand the functions of standard automation systems and improve the effectiveness of training. A standard CR3 general training system is shown in Figure1-1.

The CR3 general training system can realize the following functions:

* Robot programming and debugging;
* User/Tool coordinate system settings;
* Robot trajectory programming;
* Robot handling and palletizing;
* Machine vision coloured object recognition;
* Machine vision dynamic tracking and picking.

**Figure 1-1 CR3 general training platform system**

![Official CR3 training-system figure, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fi3WCdITDqrHKGeFYrWbn%2Futp-946038eee5410d217f01.jpg?alt=media)

### 3. Hardware Introduction

#### 3.1 Hardware layout of CR3 general training system

The size of CR3 general training system is 900×600 mm. The installation position of each part is shown in Figure 1-2.

**Figure 1-2 Hardware layout of CR3 general training platform**

#### 3.2 CR3 six-axis cooperative robot

CR3 six-axis cooperative robot is composed of the robot body (Figure 1-3) and the robot the controller (Figure 1-4, generally placed in the interior of the workbench). The robot body can move freely in its working space and complete the grasping or processing of parts with different posture.

![Official CR3 training-system figure, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYeIbXwTxR8PlMI055Ghq%2Futp-02be95e9477bc7d2dc30.jpg?alt=media)

**Figure 1-3 CR3 collaborative robot**

**Figure 1-4 Robot the controller**

**Table 1-2 Interface function definition of robot the controller**

| **No.** | **Description**                                                                                                               |
| ------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1       | <p>USB interface<br>For connecting to WiFi module</p>                                                                         |
| 2       | <p>SmartPendant and emergency stop switch interface<br>For connecting to SmartPendant (optional) or emergency stop switch</p> |
|         | LAN Interface (Default Address: 192.168.5.1)                                                                                  |
| 3       | <p>For connecting to PC (Used for debugging), or other external network equipment of<br>TCP/IP or Modbus TCP protocol</p>     |
| 4       | <p>General I/O interface<br>See 6.1.2 General I/O interface panel</p>                                                         |

![Official CR3 training-system figure, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU3EKT62uiFA9avRYEce3%2Futp-43e55cc210ed7718b06a.png?alt=media)

![Official CR3 training-system figure, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fnqgll9MVJJet3ll3V6I9%2Futp-a2be3a4e82d1385d1b8c.jpg?alt=media)

**CR3 General Training System Operation Instruction**

| 5 | <p>Power switch of controller<br>For powering on/off the controller</p>                                    |
| - | ---------------------------------------------------------------------------------------------------------- |
| 6 | <p>Power interface<br>For accessing single-phase 1100/220V AC power supply</p>                             |
| 7 | <p>External DC 48V power supply reserved port<br>For accessing AGV to supply 48V DC power to the robot</p> |
| 8 | <p>Security I/O interface<br>See 6.1.6 Security I/O interface for details</p>                              |
| 9 | <p>Heavy-duty connector interface<br>For connecting to robot, powering robot and communication</p>         |

#### 3.2.1 Definition of robot end button

The interactive panel at the end of the robot has a number of functional keys and indicator lights, as shown in Figure 1-5, which is convenient for users to operate the robot manually. The functional definition of each key is shown in Table 1-3.

**Figure 1-5 Robot end button**

**Table 1-3 Key definition**

| **Keys**                           | **Definition**                                                                                                                                 |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
|                                    | Long press to release: the indicator light turns blue and flashes to enter                                                                     |
| Enter/exit Drag                    | <p>drag and drop mode<br>Press to release: The indicator light changes from blue flashing to green<br>constant light to exit the drag mode</p> |
| <p>Drag the track to<br>record</p> | <p>Long press to release: Turn on track recording mode, and the indicator<br>light turns yellow and stays on</p>                               |
|                                    | Short press release: Exit track recording mode, and the indicator light                                                                        |

![Official CR3 training-system figure, source page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8JK4tbiakKRGE9ZoaKhj%2Futp-f48c70781a30e172c1f4.jpg?alt=media)

|                                               | changes from yellow light to green light                                                                                                                                                                                                      |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Trajectory replay                             | <p>Long press to release: enable trajectory reproduction mode, and the<br>indicator light changes to yellow and flashes<br>Short press release: Exit the track reproduction mode, and the indicator<br>light changes from yellow to green</p> |
| <p>Clamping claw and<br>other end control</p> | Short press to release: Start or close the gripper                                                                                                                                                                                            |
|                                               | Long press 3s to release: on enable, the indicator light flashes from blue                                                                                                                                                                    |
| <p>Quick up and down<br>enable button</p>     | <p>to green<br>Long press 6s release: under enable, indicator light from green flashing<br>to blue light</p>                                                                                                                                  |

Definition :

* When the robot reports an error, the indicator light is red and always on.
* Switch to auto mode and the indicator light is flashing green.
* When the connection between the robot and the control cabinet is abnormal,

and the indicator light is flashing blue.

#### 3.2.2 Movement control of robot

The motion control of the robot can be realized by three ways: hand-held teaching, point control and program running. Here, only two ways of motion control are introduced: drag teaching and point control.

(1) Hand-held demonstration

There is a hand-held teaching button " " on the intelligent interaction panel

at the end of the robot, as shown in Figure 1-6. Long press the teaching button

" " and then release it. When the indicator light changes to blue and flashes, it

will enter dragging mode. Short press" "to release it, and the indicator light changes from blue to green and flashes, which means to exit the dragging mode.

**CR3 General Training System Operation Instruction**

**Figure 1-6 End intelligent interaction panel**

The operation steps of the handheld teaching robot are as follows:

Step 1 : Long press the teaching button " " to release, and the indicator light

turns blue and flashes.

Step 2 : Drag the robot, and you can see that the coordinate value of DobotStudio Pro's inching page is changing, and then move the robot to a certain position.

Step 3 : Press " " to release, the indicator light changes from a flashing blue light to a constant green light, and the hand-held teaching is completed.

* (2) Inching control

In DobotStudio Pro's inching panel, control the robot's movement to the target position or angle by clicking or long pressing each inching button, as shown in Figure 1-7.

![Official CR3 training-system figure, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FP8gXbIHaDdlqIj71vqpm%2Futp-37a6bea394bf0c417309.jpg?alt=media)

**Figure 1-7 Inching control panel**

Take the process of moving the robot end from point A (225, -140, 260) to point B (285, -60, 260) as an example, the specific operation steps are as follows:

Step 1 : Select the default **User Frame** .

Step 2 : Click **X+** in the inching panel to change the X-axis coordinate value from 225 to 285. In the inching process, the moving speed of X-axis can be adjusted by adjusting the value of "global rate" (as shown in Figure 1-8) as required.

**Figure 1-8 Adjusts the global rate**

Step 3 : Click **Y+** in the inching panel to change the Y-axis coordinate value from -140 to -60. In the inching process, the moving speed of Y-axis can be adjusted by adjusting the value of "global rate".

Note: Inching control way to ensure that the robot is in the enabled state, that is to say, the

indicator light on the interactive panel at the end of the robot is green.

#### 3.2.3 Robot coordinate system

* (1) Joint coordinate system

![Official CR3 training-system figure, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdZFtOSQgAGgi2JkXVg8v%2Futp-24aea1761ca6a0efb662.png?alt=media)

Joint coordinate system is based on the movement joint for reference to determine the coordinate system. All joints are rotary joints. As shown in Figure 1-9.

**Figure 1-9 Joint coordinate system**

(2) The base coordinate system

The base coordinate is a coordinate system determined by referring to the base of the robotic arm, as shown in Figure 1-10. Among them, RxB, RyB, and RzB are the angles at which the tool center point TCP rotates around the X, Y, and Z axes of the default base coordinate system, respectively.

**Figure 1-10 Base coordinate system**

(3) The tool coordinate system

The tool coordinate system is a coordinate system that defines the position and posture of the Tool Center Point (TCP), and its origin and direction are constantly

![Official CR3 training-system figure, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8KWrqQjKHOQlX0RcamKE%2Futp-5230212b08fc490e0115.jpg?alt=media)

![Official CR3 training-system figure, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9DjwtrBK2Av1iawM45Lz%2Futp-8bad79a63ddd18eaa16e.jpg?alt=media)

changing with the position and angle of the end work piece. Current system supports 10 tool coordinate system, among them, the tool coordinate system 0 indicates the default tool, located at the end of the robot, don't use tools and can not be changed. The default coordinate system is shown in Figure 1-11.

**Figure 1-11 Tool coordinate system**

(4) The user coordinate system

User coordinate system is a user-defined table or work coordinate system, its origin and the direction of each axis can be determined according to the actual needs, which can be convenient to measure the position of each point in the working interval and arrange tasks, the default user coordinate system is shown in Figure 1-12.

**Figure 1-12 User coordinate system**

3.2.4 Controller I/O interface specifications

![Official CR3 training-system figure, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FreBhKqvU5WSoPNZ1id7Z%2Futp-66ae944b4d998f0b9731.jpg?alt=media)

![Official CR3 training-system figure, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI8UGlk7unR89LngjQ0Ki%2Futp-5b7b7708741b549d95a6.jpg?alt=media)

The controller cabinet of the CR3 robot contains an I/O terminal board to connect external equipment, such as air pump, PLC, conveyor belt, etc. The terminal board has 32 digital inputs, 16 digital outputs, 2 analog outputs and 2 analog inputs.

**Figure 1- 13 Control cabinet I/O port**

The robot of the CR3 general practical training system is connected to the PLC controller and the air pump box through IO. Table 1-4 shows the IO comparison table.

**Table 1-4 I/O comparison table of robots**

Open DobotStudio Pro software, you can set the state of each IO port of the robot. Click the **I/O** into the IO monitor interface, as shown in Figure 1-14, you can view **Digital input** and setting up the **Digital output** value in the interface. For example, when the switch "DO\_9" is turned on, the end sucker of the robot starts to inhale, and when the switch "DO\_10" is turned on, the end sucker of the robot starts to blow.

**Figure 1-14 "I/O" monitoring interface**

![Official CR3 training-system figure, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FT8rE0ZTfKOH9SQag0jvf%2Futp-c342d96b93cb9cf9a25b.jpg?alt=media)

![Official CR3 training-system figure, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMaJCVjdhYmGeTAShiu2u%2Futp-440e78f1ebcdfd6bb5df.jpg?alt=media)

#### 3.3 Total control unit

In the CR3 general training system, Siemens PLC S7-1212 controller is used to complete the communication between PLC and external equipment. The total control unit is equipped with Siemens S7-1212PLC and HMI touch screen, as shown in Figure 1-15 (the HMI touch screen is on the left, and the PLC under the touch screen is on the right).

The core component PLC (Programmable logic controller) is a digital arithmetic controller with a microprocessor for automatic control, which can load the control instructions into memory at any time for storage and execution. The programmable controller is composed of CPU, instruction and data memory, input/output interface, power supply, digital analog conversion and other functional units. The HMI can realize the rapid debugging and control of the total control system, which greatly

improves the application efficiency and accuracy of the equipment.

**Figure 1-15 HMI touch screen and PLC**

PLC is used to control system start, reset, stop, sensor sensing, tricolour lights, buzzers and conveyor belts. The IO comparison table between PLC and robots and external devices is shown in Tables 1-5.

**Table 1-5 I/O comparison table of PLC**

![Official CR3 training-system figure, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBVfpCgPVvvpP3jdlVT44%2Futp-279eee1bde0467ea49a6.jpg?alt=media)

Note：ROB stands for robot state.

#### 3.4 Air pump box

Mini air pump box is adopted for CR3 general training system, as shown in Figure 1-16. Compared with the traditional air supply method with large noise, large volume and high cost, this air pump box provides users with a more convenient and simple way of air supply and use. Pump box can provide -70 \~ 110 kpa pressure range, the appearance design is exquisite, facilitate can directly by the I/O control interface and robot adapter, plug and play, and can be applied to daily most sucker and flexible grip application scenario.

![Official CR3 training-system figure, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F268NvFWHyGZzsCdsf3lR%2Futp-b54fd43c6e5240b7a7e4-optimized.jpg?alt=media)

**Figure 1-16 Air pump case**

#### 3.5 Visual unit

Visual unit hardware consists of camera, lens, the light source (a white ring light source, two white strip light and two blue bar light), dual channel light controller, CCD controller, etc, as shown in Figure 1-17. Which is 5 million pixels color camera, camera lens is the prime lens focal length of 12 mm, ring light source of the figure is white light source. The switching position of light source of CR3 general training system is shown in Figure 1-18. When using it, the USB cable of the visual unit should be connected to the computer, as shown in Figure 1-19.

**Figure 1-17 Visual unit**

![Official CR3 training-system figure, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuJXCRzyjk0BGTanQmDij%2Futp-1b68b8ef5481f3c687a9.jpg?alt=media)

![Official CR3 training-system figure, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCEzoV1rfPsaJ5JrffVxm%2Futp-1e231d5138ac587f7f63.png?alt=media)

**Figure 1-18 Power switch for light source**

**Figure 1-19 Links the visual unit**

#### 3.6 Tricolour light and the control button

Tricolour light mainly through the transformation of different colors, to display the current operation state, tricolour light as shown in Figure 1-20.

**Figure 1-20 Tricolor lamp**

![Official CR3 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3y1I9YDtAWjvsZ8KCzRQ%2Futp-1aacd46a70c34f01e0e9.jpg?alt=media)

![Official CR3 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHfsNmVzrfx2xI3RDcVmx%2Futp-4bb5879fb65e86f779b5.jpg?alt=media)

![Official CR3 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9RLS7BKCdfhgql2654Dt%2Futp-524f808310c2b266dbbd.jpg?alt=media)

**CR3 General Training System Operation Instruction**

There are four control buttons, including Start, Stop, Reset and Emergency stop. The front three buttons can be used to set the running state of the device, Emergency stop control the entire machine and the robot power off, such as the robot body can not be powered on, it may be the "emergency stop" button was photographed. Figure

1-21 shows the control button.

**Figure 1-21 Control button**

#### 3.7 Conveyor belt

Feeding conveyor belt as shown in Figure 1-22. It is mainly used to push the material from the silo to the belt line to realize the transportation of the material between different locations. The conveyor uses a built-in stepper motor to accurately control the driving distance and speed of the material. Driven by DC gear motor, the speed of belt line can be controlled to meet the transportation needs of different materials. In addition, the conveyor belt is also equipped with a number of targeting sensors and encoders, which can accurately detect the position of the material on the belt line, and realize the dynamic space of the robot to follow and grasp the material, improving the transportation efficiency and accuracy of the material.

**Figure 1-22 Conveyor belt**

![Official CR3 training-system figure, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfB3KtSFN6k6SKWRkU9XD%2Futp-56a0b90fab275c2d9114.jpg?alt=media)

![Official CR3 training-system figure, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSZe2OCXDIjY7ouTCVJkj%2Futp-408e5a085402826a64bf.jpg?alt=media)

#### 3.8 Other accessories

#### 3.8.1 Quick change plate unit

The training platform is equipped with 4 quick-change plate modules, including: track plate standard visual load plate, mobile phone model workpiece load plate, circular/rectangular workpiece load plate. Cooperating with the robot execution unit and visual unit, it can achieve visual recognition, detection, and positioning of experimental objects, as well as achieve process applications such as item tracking, positioning and grasping, stacking, and assembly.

**Figure 1-23 Quick change plate unit**

#### 3.8.2 Toolbox unit

Know about the objects in the toolbox, including chip model, mobile phone

model, materials and tools for assembling, as shown in Figure 1-24.

**Figure 1-24 Toolbox unit inside24**

![Official CR3 training-system figure, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FY2jCdcOgwISbN2AUTohV%2Futp-479cc39ad28ea1f140b1.jpg?alt=media)

![Official CR3 training-system figure, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHQODr1Q9ucn9T2z3zgQo%2Futp-b5ea09bd093cc6a5288c.jpg?alt=media)

### 4. Software Installation

#### 4.1 Install the robot control software

* (1) Enter Dobot official website

Search https://www.dobot-robots.com/ in the browser to enter Dobot website.

Click **User** to enter **USER LOGIN** page, as shown in Figure1-25. Enter your email and password to enter **USER CENTER** page. (You need to register before login.)

**Figure 1-25 User Login**

* (2)Download the latest robot control software.
* ①Click **Download Center** in **USER CENTER** page, as shown in Figure1-26.

**Figure 1-26 User Center**

![Official CR3 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZKHzfyB47wcOswBHIwh9%2Futp-b9cede2b4fd2d9c598b0.jpg?alt=media)

![Official CR3 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu9BhrQ9xp6c2XRodGijg%2Futp-3f241dae65ac30f7a502.jpg?alt=media)

* ②Enter the **DOWNLOAD CENTER** interface, and click **Control Software;**

locate the **DobotStudio Pro v2.6.1** software, and click " " on the right side, and then download the robot software, as shown in Figure 1-27.

**Figure 1-27 Download software installation package**

(3) Enter installation guide interface

Double-click the downloaded software, and an installation guide interface will

pop up, as shown in Figure1-28.

**Figure 1-28 Installation instructions**

(4) Select the installation path

![Official CR3 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKwc0lSN0FamLMfqykjrf%2Futp-96530478301131c4803e.jpg?alt=media)

![Official CR3 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC8uH0VxNYoG11PvVNY70%2Futp-629b322a80b30c1c6c05.jpg?alt=media)

Click **Next** to enter the software installation interface, and click **Custom options** and **Browse** , then select the installation directory, and click **Install Now** , as shown in

Figure 1-29.

**Figure 1-29 Select the installation path**

* (5) Start installation

Click **Install Now** to start **DobotStudio ProV2.6.1** , as shown in Figure1-30.

**Figure 1-30 Installing the software**

(6) Finish Installation

![Official CR3 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSlvKlNdR6YtxLWu0Vx2N%2Futp-2b983c22dd25af80cc2c.jpg?alt=media)

![Official CR3 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUBIznfz0YTK3IeOtm4AN%2Futp-51f69d10eeedaca36296.jpg?alt=media)

After installation, click **Experience Now** to enter the software, as shown in

Figure1-31.

**Figure 1-31 Installation complete**

* (7) Know about the software interface

The main interface includes four parts, as shown in Figure1-32:

**Figure 1-32 Main interface**

 Area 1:Top Toolbar. It includes menu bar, the main interface, connection panel, alarm log button, enabling button, jog setting button, emergency stop button etc.

![Official CR3 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrycBn453WFyWykc4Rr4B%2Futp-9efc8f7dd580896f420f.jpg?alt=media)

![Official CR3 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FX68ZsoDyuTXhg9iZt69R%2Futp-7381f078c72c3de40e0d.jpg?alt=media)

![Official CR3 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqCvLYVXMt0YAeFFAVyBV%2Futp-772fcec3365154b20cdb.jpg?alt=media)

 Area 2:Recent Projects.Display the recent projects,which you can click to open quickly.

 Area 3:Major Functions.It includes DobotBlockly, Script, Setting and Process.

 Area 4:Tools Panel.Click the icon on the right toolbar to display or hide the corresponding panels,including Control, I/O, Modbus, Global Variable and Dobot+. The control panel is displayed by default after DobotStudio Pro is connected to the robot successfully.

Note: For specific functions of each tool, see its corresponding user guide.

#### 4.2 Install vision software

(1) Enter Dobot official website

Search https://www.dobot-robots.com/ in the browser to enter Dobot official website. Click **User** to enter **USER LOGIN** page. Enter your email and password to enter **USER CENTER** page as shown in Figure1-33. (You need to register before login.)

**Figure 1-33 User Login**

(2)Download the latest vision software package

①Click **Download Center** in **USER CENTER** page, as shown in Figure1-34.

![Official CR3 training-system figure, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZKHzfyB47wcOswBHIwh9%2Futp-b9cede2b4fd2d9c598b0.jpg?alt=media)

**Figure 1-34 User Center**

②Click **Control Software** in **DOWNLOAD CENTER** page. Click “ ” on

the right side of **DobotVisionStudio v4.1.2** , and then download the vision software package, as shown in Figure1-35.

**Figure 1-35 Download vision software package**

(3) Install vision software

Find and and unzip the installation package, and then double-click

**DobotVisionStudio4.1.2** . **exe** to install it, as shown in Figure1-36.

**Figure 1-36 Vision software installation file**

(4) Select a language

Select **English** , and click **OK** , as shown in Figure1-37.

![Official CR3 training-system figure, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2DNOagIYfU1NX4diw2Z1%2Futp-34abd3c57f014571b27b.png?alt=media)

![Official CR3 training-system figure, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FECnd5QBTc9rdgDI4JpQb%2Futp-63aa01825c01d5f1c255.jpg?alt=media)

**Figure 1-37 Select a language**

* (5) Welcome to DobotVisionStudio4.1.2 Setup

Enter **Welcome to DobotVisionStudio4.1.2 Setup** page, and click **Next** . Install

the software according to the guide, as shown in Figure 1-38.

**Image 1-38 Welcome to DobotVisionStudio4.1.2 Setup**

* (6) Choose Components

In **Choose Components** page, select **Hard Encrytion** , **AlgorithmInstall** and

**CameraDriver** . Then click **Next** , as shown in Figure1-39.

![Official CR3 training-system figure, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfEEe2NffANImfC974UsG%2Futp-6d3b72b2a19034c25858.jpg?alt=media)

![Official CR3 training-system figure, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4e1VqGOFo4aMH6vNnPPP%2Futp-ca72ad3d4a25bbef2837.jpg?alt=media)

**Figure 1-39 Choose Components**

* (7) Choose Install Location

Click **Browse...** to define the installation path of the software. Then click **Install** ,

as shown in Figure1-40 and Figure1-41.

**Figure 1-40 Choose Install Location**

![Official CR3 training-system figure, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FL3BxROq8RjuApDBlvYHh%2Futp-359e4e814119703d2d75.jpg?alt=media)

![Official CR3 training-system figure, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLAriGQMAuQUAnKuliBBY%2Futp-d29977ac5d4fdc2d22ff.jpg?alt=media)

**Figure 1-41 Installing**

* (8) Finish installation

Select **Run DobotVisionStudio4.1.2** and click **Finish** to exit the installation, as

shown in Figure1-42.

<br>

**Figure 1-42 Installation finished**

![Official CR3 training-system figure, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3tQJNPcY9FfbHMVa6NUq%2Futp-c8b83b6c4f583149be1b.jpg?alt=media)

![Official CR3 training-system figure, source page 38](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FW9aHY654FSnForhURfW8%2Futp-631167d4074cb2249139.jpg?alt=media)

* (9) Know about the vision software interface

Open the software and select **General Solution** to enter the corresponding software interface, as shown in Figure1-43.

**Figure 1-43 Main interface**

* Area 1:Menu Bar. It includes File, Settings, System, Tools, and Help.
* Area 2:Control Toolbar. It provides quick operations for the software,
* including file saving, file open, camera management, controller management, etc.

 Area 3:Tool Box. It includes image collection, positioning, measurement, identification, calibration, position, image processing, color processing, defect detection, logic tools, communication, etc.

* Area 4:Flow Toolbar. It provides quick operations for flows.
* Area 5:Flow Process. You can edit the flow here.
* Area 6:Overview. It provides an overview of the flow.
* Area 7:Status. It displays flow time, tool time, and algorithm time.
* Area 8:Image. Image is displayed here.
* Area 9:Results. You can view current results, history results, and help

information.

Note: For specific functions of each tool, see its corresponding user guide.

![Official CR3 training-system figure, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0cNvepFLHZCqDVOC5IrY%2Futp-d326f4569182ba04cc32.jpg?alt=media)

## Chapter 2 Application of trajectory simulation

### 1. Introduction

Trajectory simulation is based on the point position of hand-held teaching, so

that the end of the robot moves along a specific trajectory,, as shown in Figure 2-1.

**Figure 2-1 Trajectory simulation**

### 2. Hardware Description

#### 2.1 Install the support for the loading plate

Install the supports of the two loading plates on both sides of the conveyor belt

by using hex socket screws, as shown in Figure 2-2.

**Figure 2-2 Install the support for the loading plate**

![Official CR3 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuKlAMXhqZUBCsFv963R6%2Futp-7e7f06aa83f98fd4009a.jpg?alt=media)

![Official CR3 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2UhXufpSvPNvL6FndlMO%2Futp-06c00357495957c4c86e.png?alt=media)

#### 2.2 Place trajectory board

Place the trajectory board on the conveyor, as shown in Figure 3-3.

**Figure 2-3 Place trajectory board**

#### 2.3 Install calibration needle

Remove the sucker at the end of the robot, as shown in Figure 2-4.

**Figure 2-4 Remove the end of the sucker**

Then, install the prepared calibration needle onto the end of the robot, as shown in Figure 2-5.

![Official CR3 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIOEIKG3ipTnwASwMB7wt%2Futp-68436c078ad4e91f452e.jpg?alt=media)

![Official CR3 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Foz1fQrj3lE4qhQz9CBUH%2Futp-a2c5bdb58db0f2ca8618.jpg?alt=media)

**Figure 2-5 Install calibration needle**

### 3. Program Debugging

#### 3.1 Turn on CR3 general training system power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3 general training system, as shown in Figure 2-6.

**Figure 2-6 CR3 general training system power switch**

#### 3.2 Connecting robot

* (1) Power on the robot.

Check whether the power switch of the robot controller and the robot switch are turned on. If not, all switches need to be turned on, as shown in Figure 2-7.

![Official CR3 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUdzFAkMnuAIMcggIG3MD%2Futp-3dae1313a7ae54303788.jpg?alt=media)

![Official CR3 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdYXuXhds2VJQa1ytyJ40%2Futp-76fe66931110b0a471b2.jpg?alt=media)

**Figure 2-7 Robot control cabinet**

* (2) Connect network cable.

Connect one end of a network cable to the LAN1 port of the robot control cabinet and the other end to the upper network port of the PLC module box; Connect one end of the network cable to the lower network port of the PLC module box and the other end to the computer, as shown in Figure 2-8.

**Figure 2-8 Connect network cable**

(3) Change the IP address of the computer.

Open your computer's control panel, select **Network and Internet/ Network** and **Share Center** , and enter the network and share center window. Click **Ethernet** and select **Properties** to enter the ethernet property setting page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to enter the interface of **Internet Protocol version 4 (TCP/IPv4) properties** , and reset the IP address of PC side, as shown in

![Official CR3 training-system figure, source page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

![Official CR3 training-system figure, source page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfnbEewXKvH687fUFbqQb%2Futp-3ed0ec4448fe5f60a565.png?alt=media)

Figure 2-9. The default address of the robot is **192.168.5.1** , and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment as the robot. The subnet mask and default gateway are the same as those of the robot, 192.168.5.101 is used as an example.

**Figure 2-9 PC IP address settings**

(4) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro v2.6.1** to open the software. Select **CR3** on the top toolbar of the DobotStudio Pro interface, and click **Connect** , as shown in Figure

2-10.

![Official CR3 training-system figure, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUAdYCXsL6BI4BYVcjBwO%2Futp-665bb93e97b1f93a54ea.png?alt=media)

![Official CR3 training-system figure, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure 2-10 Connecting robot**

After successful connection, DobotStudio Pro interface will pop up a prompt message and the connection status will change to **Connected** , as shown in Figure 2-11.

**Figure 2-11 Connected robot**

#### 3.3 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 2-12.

Then click **Confirm modification** , the enable icon becomes " ".

**Figure 2-12 Set load parameters**

![Official CR3 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

#### 3.4 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 2-13.

**Figure 2-13 Global rate Settings**

#### 3.5 Adjust the initial pose of the robot

**(1) Select Setting>Basic .**

(2) Check if the joint coordinate of the robot is as shown in Figure 2-14, and then click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

**Figure 2-14 Adjusting the initial pose of the robot**

![Official CR3 training-system figure, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

#### 3.6 Importing program

* (1) Open the DobotStudio Pro software, enter the script programming page, and
* click **File > Import project** , as shown in Figure 2-15.

**Figure 2-15 Import project**

(2) Select the folder **CR3Project> Trajectory Simulation** , and click **Open** , as shown in Figure 2-16, then import the program of trajectory simulation into the software.

**Figure 2-16 Import path**

![Official CR3 training-system figure, source page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 47](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5pjFMmBfAxlhv3vP9XRR%2Futp-533342d472b143605dea.png?alt=media)

#### 3.7 Debug points

The program of trajectory simulation requires debugging 41 points, including 40 trajectory points and 1 safety point. The point positions of the trajectory board are shown in Figure 2-17.

**Figure 2-17 The point positions of the trajectory board**

(1) Manually drag the robot onto the trajectory board，as shown in Figure. 2-18. On the save point page, overwrite the P1 point, which is the **HOME** point (safe point), as shown in Figure 2-19, and then click **OK** in the pop-up **Tips** window.

![Official CR3 training-system figure, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNySViKStswhUf9rJ1UYS%2Futp-68a8fa291eeb8e3c37fc.jpg?alt=media)

**CR3 General Training System Operation Instruction**

**Figure 2-18 Point P1**

**Figure 2-19 Update P1**

(2) By inching control or dragging methods, move the robot to the **gj1** point on the trajectory board, as shown in Figure 2-20, then overwrite P2 point on the point page, as shown in Figure 2-21, and then click **OK** in the pop-up **Tips** window.

![Official CR3 training-system figure, source page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDTwwFQ6AASwKbDBBl7SH%2Futp-b69dd8892be32def00c4.jpg?alt=media)

![Official CR3 training-system figure, source page 49](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHquiRNqx368BXCIz3jbn%2Futp-56b086a5af147346d33c.jpg?alt=media)

**Figure 2-20 Point gj1**

**Figure 2-21 Update P2**

(3) By inching control or dragging methods, move the robot to the **gj2** point on the trajectory board, as shown in Figure 2-22; Then overwrite P3 on the point page, as shown in Figure 2-23. Then click **OK** in the pop-up **Tips** window .

![Official CR3 training-system figure, source page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Febg8nULGcSli2IYxMoDz%2Futp-c4302307b328875af037.png?alt=media)

![Official CR3 training-system figure, source page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZWPU6kE7LAxHizfghpnR%2Futp-765f03632230e557ddf1.jpg?alt=media)

**CR3 General Training System Operation Instruction**

**Figure 2-22 Point gj2**

**Figure 2-23 Update P3**

(4)Repeat the above steps and complete the remaining 38 points by hand-held teaching according to the points on the trajectory board.

Note: During the calibration, there should be a certain distance between the calibration needle and the Trajectory board, so as to avoid the calibration needle from the Trajectory board.

![Official CR3 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoFdvdlqI4scuT9NBRTC9%2Futp-828bae68270f8c5929e1.png?alt=media)

![Official CR3 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQHBPHU3gHh5WRgrMp9HE%2Futp-4734509cce620ed72edf.jpg?alt=media)

#### 3.8 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 2-24.

**Figure 2-24 Save program**

Note: " " is for saving the program to the robot controller. If you want to save the

modified program to the local computer, you need to use " ".

#### 3.9 Run program

Click the " " button to run the program and observe whether the robot

is running according to the trajectory.

Note: After the program is finished running, if the program does not automatically exit the

running state, manually click " ".

#### 3.10 Export program

Click **File > Export project** , select the path where the program is stored, and in the dialog box that pops up, name the program.

Note: **Export project** is to export the program to your local computer for backup.

![Official CR3 training-system figure, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd0LqRgUVef5SRoHMtJ3k%2Futp-0bc91e813fa4aa8d5094.jpg?alt=media)

### 4. Program Description

Since the path on the trajectory board is made up of graphs with different features, including straight lines, arcs, and circles. Therefore, 4 different motion modes are adopted in the program to design the trajectory motion of the robot. **Go** represents point-to-point motion, **Move** represents linear motion, **Arc** represents circular motion, and **Circle** represents whole circle motion. The trajectory simulation application is shown in Figures 3-25.

**Figure 2-25 Trajectory motion program**

![Official CR3 training-system figure, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM3K5Can0FOKYi7Bz7nYz%2Futp-333472b858a1e63d6979.jpg?alt=media)

#### Chapter3 Application of static palletizing

### 1. Introduction

The specific task to be realized in the static palletizing application is to use the robot to move the blocks placed on the standard vision loading board to the grooves of the rectangular workpiece loading board in the storage area, as shown in Figure

3-1.<br>

**Figure 3-1 Palletizing blocks**

### 2. Hardware Description

#### 2.1 Install standard vision carrier board

Install the standard vision carrier board above the conveyor belt, as shown in Figure 3-2 .

![Official CR3 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnMYyFCQWzWgbzAtYdwpb%2Futp-5dd28f8a27c6e1c12ac8.png?alt=media)

**Figure 3-2 Install standard vision board**

#### 2.2 IO configuration description

The IO configuration of static palletizing is shown in Table 3-1 .

**Table 3-1 IO configuration for static palletizing applications**

| **Output** | **Description** |
| ---------- | --------------- |
| DO9        | Vacuumpumping   |
| DO10       | Vacuum breaking |

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on CR3 general training system power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3 general training system, as shown in Figure 3-3.

![Official CR3 training-system figure, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2NYKzbYIrypZ5vSIQd7Y%2Futp-c0671878f6b71b572d7f.jpg?alt=media)

**Figure 3-3 CR3 general training system power switch**

#### 3.1.2 Turn on the air pump box switch

Turn on the power switch of the air pump box and rotate the control button to

**Auto** , as shown in Figure 3-4.

**Figure 3-4 Pump box**

#### 3.1.3 Preparation of palletized materials

Place the nine blocks in a 3×3×1 matrix arrangement (three rows, three columns, one layer) on the bottom right corner of the standard visual carrier board, as shown in

Figure 3-5.

![Official CR3 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdYXuXhds2VJQa1ytyJ40%2Futp-76fe66931110b0a471b2.jpg?alt=media)

![Official CR3 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzFjaVYWzyhPEtjiJk3QP%2Futp-01cbfdd56a2023048af3.jpg?alt=media)

**Figure 3-5 Palletizing materials**

#### 3.2 Connect robot

* (1) Power on the robot.

Check whether the power switch of the robot controller and the robot switch are

turned on. If not, all switches need to be turned on, as shown in Figure 3-6.

**Figure 3-6 Robot control cabinet**

* (2) Connect network cable.

Connect one end of a network cable to the LAN1 port of the robot control cabinet and the other end to the upper network port of the PLC module box; Connect one end of the network cable to the lower network port of the PLC module box and the other end to the computer, as shown in Figure 3-7.

![Official CR3 training-system figure, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

![Official CR3 training-system figure, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuBAq7fPChtiPwWatWYSl%2Futp-eca29a27af97754b7f6b.png?alt=media)

**Figure 3-7 Connect network cable**

(3) Change the IP address of the computer.

Open your computer's control panel, select **Network and Internet/ Network** and **Share Center** , and enter the network and share center window. Click **Ethernet** and select **Properties** to enter the ethernet property setting page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to enter the interface of **Internet Protocol version 4 (TCP/IPv4) properties** , and reset the IP address of PC side, as shown in Figure 3-8. The default address of the robot is **192.168.5.1** , and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment as the robot. The subnet mask and default gateway are the same as those of the robot, 192.168.5.101 is used as an example.

![Official CR3 training-system figure, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfnbEewXKvH687fUFbqQb%2Futp-3ed0ec4448fe5f60a565.png?alt=media)

**Figure 3-8 IP setting of PC**

(4) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro v2.6.1** to open the software. Select **CR3** on the

top toolbar, and click **Connect** , as shown in Figure 3-9.

**Figure 3-9 Connect robot**

After successful connection, DobotStudio Pro interface will pop up a prompt message and the connection status will change to **Connected** , as shown in Figure 3-10.

![Official CR3 training-system figure, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUAdYCXsL6BI4BYVcjBwO%2Futp-665bb93e97b1f93a54ea.png?alt=media)

![Official CR3 training-system figure, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure 3-10 Connected robot**

#### 3.3 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 3-11. Then

click **Confirm modification** , the enable icon becomes " ".

**Figure 3-11 Set load parameters**

#### 3.4 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 3-12.

![Official CR3 training-system figure, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

**Figure 3-12 Global rate settings**

#### 3.5 Adjust the initial pose of the robot

* (1) Select **Setting>Basic** .

(2) Check if the joint coordinate of the robot is as shown in Figure 3-13, and then

click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

**Figure 3-13 Adjusting the initial pose of the robot**

#### 3.6 Importing program

* (1) Open the DobotStudio Pro software, enter the script programming page, and

click **File** > **Import project** , as shown in Figure 3-14.

![Official CR3 training-system figure, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

**Figure 3-14 Import project**

* (2) Select the folder **CR3Project> CR3\_Palletizing** , and click **Open** , as shown

in Figure 3-15, then import the static palletizing program into the software.

**Figure 3-15 Import path**

#### 3.7 Debug points

* (1) Safe point P1

![Official CR3 training-system figure, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdBExaZHFaE7uzaLeKUdO%2Futp-bebd700412d3da9b683d.jpg?alt=media)

Move the robot between the conveyor belt and the storage area through hand-held teaching or inching control methods, as shown in Figure 3-16. Click **Points** in DobotStudio Pro, and select **P1** , then click **Cover** , as shown in Figure 3-17.

**Figure 3-16 Point P1**

**Figure 3-17 Update P1**

(2) Pick-up point P2

By using inching control methods, the robot is moved to the position of the first block’s pick-up point on the standard visual loading board, and the sucker needs to needs to touch the center position of the first block, as shown in Figure 3-18. Then select **P2** in **Points** , and click **Cover** , as shown in Figure 3-19.

![Official CR3 training-system figure, source page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5PCGluf6agmsQS5uPeUP%2Futp-dc4dab4862dbff528879.jpg?alt=media)

![Official CR3 training-system figure, source page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfAyW00gNjwozoitG8nov%2Futp-4f69b31a7c0a034b872b.jpg?alt=media)

**Figure 3-18 Picking point P2 of the first block**

**Figure 3-19 Update P2**

(3) Placing material point P3

Make sure that the end of the robot is at point P2, and then open **IO** control panel. Open the **DO\_09** signal switch allows the end of the robot pick up the block, as shown in Figure 3-20. By using inching control methods, the robot is allowed to draw the first material and move it to the position P3 of the first placing point in the storage area, as shown in Figure 3-21. Then select **P3** in **Points** , and click **Cover** , as shown in Figure 3-22.

![Official CR3 training-system figure, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvCm6jaQA3uuVnsVveWBz%2Futp-687cbbc21facfc9ab1b7.jpg?alt=media)

![Official CR3 training-system figure, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHVL95nrBIXJP8ogtQrOG%2Futp-da7a4bbc0d2cd82f629c.jpg?alt=media)

**Figure 3-20 IO panel**

**Figure 3-21 Placing point P3 of the first block**

![Official CR3 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8KDjBFU7UZkL3nOQYziz%2Futp-0a3e38dd14f87ec6b0a7.jpg?alt=media)

![Official CR3 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzxBz3q1U6HMSfDk4J6Ox%2Futp-9fe9fd3e81c407f30317.jpg?alt=media)

**Figure 3-22 Update P3**

In the **IO** control panel, turn off the **DO\_09** signal; at the same time, turn on the DO\_10 signal. After 1 second, turn off the **DO\_10** signal switch; let the end of the robot close the sucker after releasing the block. Check if the block can be accurately placed in the grooves, and if not, it needs to be debugged again.

#### 3.8 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 3-23.

**Figure 3-23 Save program**

Note: " " is for saving the program to the robot controller. If you want to save the

![Official CR3 training-system figure, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYxtpC2okhI1zlPcSrLHQ%2Futp-52ac53007301e4379ab8.jpg?alt=media)

![Official CR3 training-system figure, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu2GPdWmEiLPRWNkepZI6%2Futp-8eac6a122f2945c2f709.jpg?alt=media)

#### 3.9 Run program

Click the " " button to run the program. Observe whether the robot successively moves the nine blocks which are arranged by a 3×3×1 matrix in the standard visual loading board, and successively place them into the grooves of the 3 rectangular workpiece loading board in the storage area, as shown in Figure 3-24.

**Figure 3-24 Palletizing effect**

#### 3.10 Export program

Click **File > Export project** , and select the path where the program is stored, then, in the dialog box that pops up, name the program.

Note: **Export project** is to export the program to your local computer for backup.

### 4. Program Description

#### 4.1 Set variables for block interval

Use a ruler or other measuring tools to measure the horizontal and vertical spacing between the two blocks of the material extraction point; using the same method, respectively measure the horizontal and vertical spacing between the two blocks of the placing point; simultaneously measure the height of individual block, as shown in Figure 3-25.

![Official CR3 training-system figure, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnMYyFCQWzWgbzAtYdwpb%2Futp-5dd28f8a27c6e1c12ac8.png?alt=media)

**Figure 3-25 Measure interval between blocks and height of individual block**

According to the measurement results, the variables of material spacing at the take-up point and the variables of material spacing at the placing point were set respectively in the robot program, as shown in Figure 3-26.

**Figure 3-26 Set block interval variables**

#### 4.2 Robot pick-up program

Set the robot to pick up the blocks in the standard vision board following the sequence shown in Figure 3-27. The coordinate of the first block that the robot draws at the pick-up point is P2.

**Figure 3-27 Robot pick-up sequence**

![Official CR3 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdoO3hznhSpLfScMmjiMa%2Futp-29061d9dc2e88472d3bf.jpg?alt=media)

![Official CR3 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FP67ZR8VrwuorNMTgLi1I%2Futp-db88cb1bd197e3ce8c72.jpg?alt=media)

![Official CR3 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkRrJ9hr0WPvbMxi9NBeg%2Futp-40bc7bf89a9d27fab2ed.jpg?alt=media)

By using inching control methods, the robot can store the coordinates P2 of the first block of the pinking point. According to the order of robot picking up materials and the horizontal and vertical spacing of the picking points, the coordinates of the corresponding picking points of the other 8 blocks can be obtained. The program of the robot pick-up 9 blocks from the standard visual loading board is shown in Figure

3-28.

**Figure 3-28 Robot pick-up program**

After picking up the block, the robot needs to move to the safe point P1 to ensure the safety of the robot movement.

#### 4.3 Robot placement program

Set the robot to place blocks following the sequence shown in Figure 3-29. The coordinate of the first block that placed by the robot at the placing point is P3.

**Figure 3-29Robot placement sequence**

By using inching control methods, the robot can store the coordinates P3 of the

first block of the placing point. According to the order of robot placing materials and the horizontal and vertical spacing of the placing points, the coordinates of the corresponding placing points of the other eight blocks can be obtained. The robot will

![Official CR3 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCW8T8aQAVLwdWaPHLooI%2Futp-a8f3046c0596367c0eb5.jpg?alt=media)

![Official CR3 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FddFst9W2NoaPpjI6D1aj%2Futp-940478b984d25b8b2fce.jpg?alt=media)

stack nine blocks on three rectangular workpiece loading boards in the storage area in the order of 1×3×3 (one row, three columns and three layers), as shown in Figure 3-30.

**Figure 3-30 Robot placement program**

![Official CR3 training-system figure, source page 71](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUB3pkQeFIzGAOZP7jxZq%2Futp-b5927179ed5147c95e65.jpg?alt=media)

## Chapter 4 Application of robot handling

**1. Introduction**

The task of the robot handling application is to push six circular workpieces from the silo onto the conveyor belt through a push motor, and then the robot moves the workpieces, which are conveyed by the conveyor belt, to the storage area. During the system operation, the device can be controlled to stop, reset, and start by pressing the buttons on the touch screen or the buttons on the control button box (as shown in Figure 4-1). At the same time, the operating status of the device can be feedback through the color of the three color lights.

**Figure4-1 Control button box**

The robot handling application project is controlled by buttons on the touch screen or buttons on the control button box, and there are two modes: manual control and automatic control. The manual control mode is mainly used for debugging, which can control the tricolor light, buzzer, pushing motor, and conveyor belt by pressing the buttons on the touch screen; in automatic process mode, you need to first press the **Stop** button on the touch screen, then press the **Reset** button, and finally press the **Start** button in order for the system to run automatically (or first press the **STOP** button in the control button, then press the **RESET** button, and finally press the **START** button). The three color lights will correspond to red, yellow, and green lights.

First, the robot moves to the safe point, and the robot sends the discharge signal to the PLC. After the PLC receives the signal, the system opens the push motor, and the push motor pushes the material out of the cylindrical silo, and then starts the

forward movement of the conveyor belt, then the conveyor belt moves forward with the material. When the in-place detection sensor detects the material reaching (as shown in Figure 4-2), PLC sends the material reaching signal to the robot. After the robot receives the signal, it draws the material from the conveyor belt and moves it to the corresponding location in the storage area. This cycle is repeated for 6 times, and the robot is controlled to move the circular material into the circular groove of the rectangular/circular material carrier plate in the storage area and place the circular material in a 3X2 matrix arrangement. The final effect of the placement is shown in

Figure 4-3.

**Figure 4-2 Stock bin**

**Figure 4-3 Storage area**

**2. Hardware Description**

#### 2.1 Install coaxial sucker tool

(1) Remove the calibration needle from the end of the robot, as shown in Figure

4-4.

![Official CR3 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fudn1vVO5cEZhpZzi78bK%2Futp-7e4bc08c9149b8eaed2d.png?alt=media)

![Official CR3 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn2Cr9XJlFARKqanbNjjF%2Futp-35ae3445096231e88ed8.jpg?alt=media)

**Figure 4-4 Remove the calibration needle**

* (2) Install the sucker to the end of the robot, as shown in Figure 4-5.

**Figure 4-5 Mounting sucker**

#### 2.1 IO configuration description

The robot IO configuration for the robot handling application project is shown in Table 4-1, the PLC input IO configuration is shown in Table 4-2, the PLC output IO

![Official CR3 training-system figure, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6vV1Bph0ko6Vb8kwDXOH%2Futp-96cd3accccfb6e62f158.jpg?alt=media)

![Official CR3 training-system figure, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTbv7JTVon7KIbSDHKSUy%2Futp-1347477b4c31405e0d89.jpg?alt=media)

configuration is shown in Table 4-3, the touch screen input IO configuration is shown in Table 4-4, and the touch screen output IO configuration is shown in Table 4-5.

**Table 4-1 IO configuration of the robot**

| **Pin** | **Output** | **Description** |
| ------- | ---------- | --------------- |
| 1       | DO09       | Vacuumpumping   |
| 2       | DO10       | Vacuum breaking |

**Table 4-2 IO configuration for PLC input**

| **Pin** | **Input** | **Description**          |
| ------- | --------- | ------------------------ |
| 1       | PLC\_IN01 | start                    |
| 2       | PLC\_IN02 | stop                     |
| 3       | PLC\_IN03 | reset                    |
| 4       | PLC\_IN04 | reserve                  |
| 5       | PLC\_IN05 | the stock bin has blocks |
| 6       | PLC\_IN06 | belt material inspection |

**Table 4-3 IO configuration for PLC output**

| **Pin** | **Output** | **Description**         |
| ------- | ---------- | ----------------------- |
| 1       | PLC\_OUT01 | green light             |
| 2       | PLC\_OUT02 | yellow light            |
| 3       | PLC\_OUT03 | red light               |
| 4       | PLC\_OUT04 | buzzer                  |
| 5       | PLC\_OUT05 | the pusher motor starts |
| 6       | PLC\_OUT06 | the conveyor starts     |

**Table 4-4IO configuration for touch screen input**

| **Pin** | <p><strong>Input</strong><br><strong>Corre</strong></p> | **spondence** | **Description**         |
| ------- | ------------------------------------------------------- | ------------- | ----------------------- |
| 1       | <p>PLC_IN11<br>R1</p>                                   | \_OUT11       | ROB is ready            |
| 2       | <p>PLC_IN12<br>R1</p>                                   | \_OUT12       | ROB is suspended        |
| 3       | <p>PLC_IN13<br>R1</p>                                   | \_OUT13       | ROB running status      |
| 4       | <p>PLC_IN14<br>R1</p>                                   | \_OUT14       | ROB alarm status        |
| 5       | <p>PLC_IN15<br>R1</p>                                   | \_OUT15       | ROB Interaction 1       |
| 6       | <p>PLC_IN16<br>R1</p>                                   | \_OUT16       | ROB requests a pushback |

**Table 4-5IO configuration for touch screen output**

| **Pin** | **Output** | **Correspondence** | **Description**         |
| ------- | ---------- | ------------------ | ----------------------- |
| 1       | PLC\_OUT11 | R1\_IN11           | ROB initiate            |
| 2       | PLC\_OUT12 | R1\_IN12           | ROB paused              |
| 3       | PLC\_OUT13 | R1\_IN13           | ROB continues           |
| 4       | PLC\_OUT14 | R1\_IN14           | ROB stops               |
| 5       | PLC\_OUT15 | R1\_IN15           | ROB clears the alarm    |
| 6       | PLC\_OUT16 | R1\_IN16           | ROB material inspection |

**3. Program Debugging**

#### 3.1 Preparation

#### 3.1.1 Turn on CR3 general training system power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3

general training system, as shown in Figure 4-6.

**Figure 4-6 CR3 power switch of training platform**

#### 3.1.2 Turn on the air pump box switch

Turn on the power switch of the air pump box and rotate the control button to

**Auto,** as shown in Figure 4-7.

**Figure 4-7 Pump box**

#### 3.1.3 Prepare material

Place six circular materials into the material barrel, as shown in Figure 4-8.

![Official CR3 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdYXuXhds2VJQa1ytyJ40%2Futp-76fe66931110b0a471b2.jpg?alt=media)

![Official CR3 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzFjaVYWzyhPEtjiJk3QP%2Futp-01cbfdd56a2023048af3.jpg?alt=media)

**Figure 4-8 Placing workpiece**

#### 3.1.4 Power on the robot.

Check whether the power switch of the robot controller and the robot switch are

turned on. If not, all switches need to be turned on, as shown in Figure 4-9.

**Figure 4-9 Robot control cabinet**

#### 3.1.5 Connect network cable.

Connect one end of a network cable to the LAN1 port of the robot control cabinet and the other end to the upper network port of the PLC module box; Connect one end of the network cable to the lower network port of the PLC module box and the other end to the computer, as shown in Figure 4-10.

![Official CR3 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

![Official CR3 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEI4xPWVy5xNE4GO6xGx9%2Futp-860a503df7209e26f5d5.jpg?alt=media)

**Figure 4-10 Connect network cable**

#### 3.1.6 Change the IP address of the computer.

Open your computer's control panel, select **Network and Internet/ Network and Share Center** , and enter the network and share center window. Click **Ethernet** and select **Properties** to enter the ethernet property setting page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to enter the interface of **Internet Protocol version 4 (TCP/IPv4) properties** , and reset the IP address of PC side, as shown in Figure 4-11. The default address of the robot is **192.168.5.1** , and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment with the robot. The subnet mask and default gateway are the same as those of the robot, taking **192.168.5.101** as an example here.

![Official CR3 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfnbEewXKvH687fUFbqQb%2Futp-3ed0ec4448fe5f60a565.png?alt=media)

**Figure 4-11 PC IP address Settings**

#### 3.2 Download PLC program

TIA Portal software must be purchased separately by the customer. The PLC program is pre-loaded within the system. If PLC programming is not required, TIA Portal software is unnecessary.

Step 1: Open the TIA Portal software, as shown in Figure 4-12.

**Figure 4-12 PLC software initial interface**

Step 2: Select **Open existing project** , and find the storage location of the PLC program, then select **CR3\_Trainiing\_Platform(PLC).ap15\_1** , and then click open, as shown in Figure 4-13.

![Official CR3 training-system figure, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUAdYCXsL6BI4BYVcjBwO%2Futp-665bb93e97b1f93a54ea.png?alt=media)

![Official CR3 training-system figure, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU0c8Ms3GII997qmMCaiX%2Futp-29b5e2d63c09b819f3fc.jpg?alt=media)

**Figure 4-13 Opening an existing project**

Step 3: Click on the **Project view** in the bottom left corner to open the project view, then double-click on **Devices\&networks** , and click on **(Show address labels);** check whether the IP addresses of the device PLC, PLC expansion module, and touch screen are all IP addresses of the 192.168.5. \* network segment, as shown in Figure 4-14. If not, it needs to be modified to the IP address of the network segment. Here, for example, the IP of the PLC is set to **192.168.5.100** , the IP of the PLC expansion module is set to **192.168.5.11** , and the IP of the touch screen is set to **192.168.5.102** .

**Figure 4-14 Settings of Devices\&networks**

![Official CR3 training-system figure, source page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfKSD5W6mRhfiPLt60WGC%2Futp-4437833f41380a2f27d7.jpg?alt=media)

![Official CR3 training-system figure, source page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwdjjAJsauO6RrG6JYt2T%2Futp-571682da917103fc121a.jpg?alt=media)

Step 4: Expand **PLC\_1\[CPU 1212C DC/DC/DC] →Program blocks** , then double-click **Main\[OB1]** to open the main program, as shown in Figure 4-15. Check whether the opened program needs to be downloaded to the PLC. If yes proceed to the next step, if not reopen the correct PLC program.

**Figure 4-15 Viewing the PLC program**

Step 5: Select **PLC\_1\[CPU 1212C DC/DC/DC]** , and then click the

" " **(download to device)** icon on the menu bar. The **Extend download to device** screen is displayed. Select **PN/IE\_1** in the **connection to interface/subnet** column, and then click **Start search** ; Then select **PLC\_1** from the searched device. Finally, click **Load** , as shown in Figure 4-16.

![Official CR3 training-system figure, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3B0hPVCPfWqlQYAfuPIZ%2Futp-eecdab527d48073a73c5.jpg?alt=media)

**Figure 4-16 Settings of Extend download to device**

Step 6: In the pop-up **Software synchronization before loading to a device** interface, click **Continue without synchronization** to continue downloading, as shown in Figure 4-17. Then jump to the **load preview** interface.

**Figure 4-17 Continue without synchronization**

Step 7: In the **load preview** interface, click **Load** , as shown in Figure 4-18. After the download is complete, click **Finish** to complete the download, as shown in Figure 4-19.

![Official CR3 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjIEiwqvaNskax1W808fF%2Futp-671fc4f2c4bb69f19505.jpg?alt=media)

![Official CR3 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5S4X4wKWicaSUHQoPlEa%2Futp-05ba73c63ae9021ad9de.jpg?alt=media)

**Figure 4-19 Settings of Load preview**

**Figure 4-19 PLC program successfully downloaded**

Step 8: Click the " " icon in the menu bar, and the program will

go online. The PLC program in the device bar will appear as a green " " or" ", as shown in Figure 4-20, which indicates that the PLC program has been successfully downloaded, so that online debugging and monitoring can be carried out.

![Official CR3 training-system figure, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1M3Gxhdlur9Wnc09SsXa%2Futp-904121beddbbd486d7f3.jpg?alt=media)

![Official CR3 training-system figure, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBhODcRDT8sE4yeKhfT3d%2Futp-817d1adb184abd330f52.jpg?alt=media)

**Figure 4-20 Online mode**

#### 3.3 Downloading HMI Programs

Step 1: Connect the HMI device. Expand **HMI 1 \[KTP700 Basic PN]→Screens** and check whether programs on each sub-screen are HMI programs that need to be downloaded to the touch screen. Click the " " icon in the menu bar to find the HMI device, and then pop up the **Accessible devices** window, select **PN/IE** in the **Type of the PG/PC interface** bar, and click **Start search** . Then, select **hmi\_1** from the search

device. Finally, click **Show** , as shown in Figure 4-21.

**Figure 4-21 Viewing the HMI program**

![Official CR3 training-system figure, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FV2GUulX9JytUB2KT0XrZ%2Futp-740119e6b0eac2867d20.jpg?alt=media)

![Official CR3 training-system figure, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcpMaal8H0C7yj5Ww0FKX%2Futp-c7fa17eddb34e341a033.jpg?alt=media)

Step 2: Download the HMI program and click the icon of " " on the menu bar.

The system will compile the program in the HMI before downloading, as shown in

Figure 4-22.

**Figure 4-22 Downloading the HMI program**

Step 3: After compiling, the window as shown in Figure 4-23 will pop up. In the **load preview** interface, and check **Overwrite all** under the **Action** parameter, and then click "Load", as shown in Figure 4-24. After the download is complete, the message "Loading completed" will appear at the bottom of the software interface.

**Figure 4-23 Settings of Load preview**

![Official CR3 training-system figure, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpLXsdF5UiOuKxRR5EftC%2Futp-821640f55b2d3a4aeb1c.jpg?alt=media)

![Official CR3 training-system figure, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FySFsGzfwckCTSRhTX95h%2Futp-251854f857dbbf5ade1d.jpg?alt=media)

**Figure 4-24 Successfully downloaded HMI program**

Step 4: Click the " " icon in the menu bar, and the program will

go online. If the HMI program is displayed in green " " or " " on the device bar, as shown in Figure 4-25, it indicates that the HMI program has been successfully downloaded, so that online debugging and monitoring can be carried out.

**Figure 4-25 Online mode**

#### 3.4 Function Debugging of a single key or button

Observe whether the control of each control button on the control box and each touch button on the touch screen are as follows:

* ① Debugging of the **Manual control** interface on the touch screen.

Switch the touch screen to the **Manual control** interface, as shown in Figure

4-26.

![Official CR3 training-system figure, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgbvKQJ2Uu3o3WSr4KO78%2Futp-5e2db2bf7f24716e25c7.jpg?alt=media)

![Official CR3 training-system figure, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGZDfIHpbPFUzvFOIhfIf%2Futp-debc869881b9b759134b.jpg?alt=media)

**Figure 4-26 Manual control interface**

Press the **Pusher motor starts** button to push the material; press **Pusher motor starts** again to retract the motor. Press the **Conveyor starts** button and the conveyor belt runs; press the **Conveyor starts** again and the conveyor belt stops running. Press the **Green light** button, the green light of the tricolour light is on; press **Green light** again and the green light turns off. Press **Yellow light** button, the yellow light of the tricolour light is on; press **Yellow light** again to turn off the yellow light. Press the **Red light** button, the red light is on; press **Red light** again to turn off the red light. Press the **Buzzer** button, and the buzzer will sound. Press **Buzzer** again to stop the buzzer.

* ② Debugging of the **Automatic control** interface on the touch screen. Switch the touch screen to **Automatic control** interface, as shown in Figure

4-27.

![Official CR3 training-system figure, source page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhPEL5CcfzIJOloganvgM%2Futp-6fd81187a8d3c48cb8d3.jpg?alt=media)

**Figure 4-27 Automatic control interface**

Press the **STOP** button in the **Automatic control** interface, and the red light of the tricolour light will turn on. Press the **RESET** button on the **Automatic control** interface. The yellow light of the tricolour light is on. Press **START** on the **Automatic control** interface. The green light of the tricolour light is on.

When the **STOP** button on the control button box is pressed, the red light of the tricolour light is on; press the **RESET** button on the control button box, and the yellow light is on; press the **START** button on the control button box and the green light is on.

During the debugging process, when the observed phenomenon is inconsistent with the above provided, it is necessary to modify the PLC and touch screen program.

#### 3.5 Robot program debugging

![Official CR3 training-system figure, source page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKZqPLBxzWrXe0paKI0lt%2Futp-686877615ea6ac685d2d.jpg?alt=media)

#### 3.5.1 Connect DobotStudio Pro to the robot.

Double-click the DobotStudio Pro software icon to open the software. Then select the robot **CR3** to be connected from the top toolbar of the DobotStudio Pro interface, and click **Connect** , as shown in Figure 4-28..

**Figure 4-28 Connecting robot**

After successful connection, DobotStudio Pro interface will pop up a prompt message and the connection status will change to **Connected** , **Safe L1** , **Online** , as shown in Figure 4-29.

**Figure 4-29 Connected robot**

#### 3.5.2 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 4-30. Then click **Confirm modification** , the enable icon becomes " ".

![Official CR3 training-system figure, source page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure 4-30 Set load parameters**

#### 3.5.3 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 4-31.

**Figure 4-31 Global rate setting**

#### 3.5.4 Adjust the initial pose of the robot

* (1) Select **Setting>Basic** .

(2) Check if the joint coordinate of the robot is as shown in Figure 4-32, and then click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

![Official CR3 training-system figure, source page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

**Figure 4-32 Adjusting the initial pose of the robot**

#### 3.5.5 Importing programs

* (1) Open the DobotStudio Pro software, enter the script programming page, and

click **File > Import project** , as shown in Figure 4-33.

**Figure 4-33 Import Project**

* (2) Select the folder **CR3Project>** ~~**Trajectory Simulation**~~ **CR3Robot** , and click

**Open** , as shown in Figure 4-34, then import the program of the conveyor belt application into the software.

![Official CR3 training-system figure, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

![Official CR3 training-system figure, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

**Figure 4-34 Import path**

Note: If there is already a robot application program in the robot controller, it can be opened

directly by clicking **File>Open>CR3Robot** .

#### 3.5.6 Debug points

The conveyor belt application includes three major points, and the debugging

method is as follows:

* (1) Safe point P1
* ①Move the robot between the conveyor belt and the storage area through

handheld teaching or inching control methods, as shown in Figure 4-35.

**Figure 4-35 Point P1**

![Official CR3 training-system figure, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjFKof8EqsXJERxwnJlNX%2Futp-0d13db6a62f51618b5d2.jpg?alt=media)

![Official CR3 training-system figure, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwvcpoucfYEWktZiZWs7J%2Futp-8e63c32685c462801b1d.jpg?alt=media)

* ②Click **Points** in DobotStudio Pro, and select **P1** , then click **Cover** , as shown in

Figure 4-36, and then click **OK** on the **Tips** interface that pops up.

**Figure 4-36 Update P1**

**(2) Pick-up point P2**

① Place the circular workpiece into the silo, and then on the **Manual control** interface of the touch screen, click **Pusher motor starts** firstly. When the circular workpiece is pushed onto the conveyor belt, click **Pusher motor starts** again to retract the pusher motor; click the **Conveyor starts** button again to start the conveyor belt. When the conveyor belt moves with the workpiece to the suction position (the position sensor on the conveyor belt lights up, as shown in Figure 4-37, indicating that the material has reached the detection point), click the **Conveyor starts** button again

to stop the conveyor belt from moving.

**Figure 4-37 Material arrival at the inspection point**

![Official CR3 training-system figure, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHInEFVCPpRQK5AFVGvWb%2Futp-7bdf0a85216712c716dc.jpg?alt=media)

![Official CR3 training-system figure, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuHiQtbZiq9U7G8B8C3Uf%2Futp-454bf09fe2cf8b490c35.jpg?alt=media)

* ② By inching control method, move the robot to the circular workpiece, and the sucker gently touches the surface of the circular workpiece, as shown in Figure 4-38.

**Figure 4-38 Positioning to point P2**

③Open the **IO** control panel, then open the **DO\_09** signal switch, let the end of

the robot suck the circular workpiece. As shown in Figure 4-39.

86<br>

![Official CR3 training-system figure, source page 94](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBZQeWtJIIlelP6nzVpj5%2Futp-4dcc70a1f9ece4920695.jpg?alt=media)

![Official CR3 training-system figure, source page 94](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fyw2OIABZjajO10JePjSm%2Futp-4ec0c607e897fc4a6b47.jpg?alt=media)

**Figure 4-39 I/O Control panel**

④ Open **Points** , and click **P2** , then click **Cover,** as shown in Figure 4-40, and then click **OK** on the **Tips** interface that pops up.

**Figure 4-40 Update P2**

(3) Pick-up point P3

① The robot is moved to the first discharge point in the storage area through the inching control method, as shown in Figure 4-41. In the **IO** control panel, turn off the **DO\_09** signal switch, and turn on the **DO\_10** signal switch. After 1 second, turn off the **DO\_10** signal switch. Let the end of the robot release the material and then close the sucker. See whether the circular material can be accurately placed in the groove, if not, it needs to be debugged again.

![Official CR3 training-system figure, source page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlWUjOE7SyiiuTkUlmE8k%2Futp-04009e39676fc2630869.jpg?alt=media)

**Figure 4-41 First placing point**

② Open **Points** , and click **P3** , then click **Cover,** as shown in Figure 4-42, and

then click **OK** on the **Tips** interface that pops up.

**Figure 4-42 Update P3**

#### 3.5.7 Save program

Click " ", and in the dialog box that pops up, name the program. Note: " " is for saving the program to the robot controller. If you want to save the

modified program to the local computer, you need to use " ".

#### 3.6 System coordination

![Official CR3 training-system figure, source page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIncYIwgAKXzIefJlxB8K%2Futp-585ebdf6fea9f777ba54.jpg?alt=media)

![Official CR3 training-system figure, source page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVtzLQG1s6ooBAYkMPr3i%2Futp-902e6ce024a5147aad8b.jpg?alt=media)

* (1) Open the PLC program of the Project, select **PLC\_1** in **Project tree** , and
* then select **Start CPU** in the menu bar to start the running CPU mode, as shown in

Figure 4-43.

**Figure 4-43 Run the program of PLC\_1**

(2) Switch the touch screen interface to the automatic control interface.

Click the **Automatic control** button on the touch screen to switch the touch screen interface to the **Automatic control** interface.

First press the **STOP** button on the control button box, then press the **RESET** button, and finally press the **START** button. Or, in the automatic control interface of the touch screen, press the **STOP** button, then press the **RESET** button, and finally press the **START** button. It can be observed that the color of the tricolor light changes from red to yellow and finally to green.

* (3) Open the robot program for the robot handling application project. Click

" " button, run the program, and observe whether the system running status is as follows:

When the robot moves to the safe point, the robot sends the discharge signal to the PLC. After PLC receives the signal, the system starts the push motor, push the material out of the cylinder silo, and then start the forward movement of the conveyor belt, and the conveyor belt moves forward with the material. When the position

![Official CR3 training-system figure, source page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9ZxWGlF3QTUzM1zB4jmM%2Futp-7d91c0c779bbfaba305b.jpg?alt=media)

detection sensor detects that the material has reached, the PLC sends the material reach signal to the robot. After the robot receives the signal, it draws the material from the conveyor belt and moves it to the corresponding location in the storage area; This cycle is repeated six times, and the robot is controlled to move the round material to the circular groove of the rectangular/circular material carrier plate in the storage area,

as shown in Figure 4-44.

**Figure 4-44 Robot handling result**

If you find any inconsistency during operation, tap " ", or press **STOP** on the control button box, or **STOP** on the **Automatic control** screen on the touch screen. Then according to the running state to modify the robot program or PLC program, HMI program.

#### 3.7 Export program

Click **File > Export project** , select the path where the program is stored, and in the dialog box that pops up, name the program , as shown in Figure 4-45.

![Official CR3 training-system figure, source page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn2Cr9XJlFARKqanbNjjF%2Futp-35ae3445096231e88ed8.jpg?alt=media)

**Figure 4-45 Export program**

Note: **Export project** is to export the program to your local computer for backup.

**4. Program Description**

The following text only provides explanations for key codes. Please review the complete version of the code in the engineering file.

#### 4.1 Description of PLC program

The robot handling application system control is divided into two modes: manual and automatic.

* (1) Control requirements in manual control mode.

Under the manual control interface of the touch screen, press the **red light of the tricolour light** button, and the red light of the **tricolour** light will be on; press the **yellow light of the tricolour light** button, the yellow light of the **tricolour** light; press the **green light of the tricolour light** button, the green light of the **tricolour** light is on; after pressing **discharge push motor start** , push motor start; press **Belt Start** and the belt starts.

* (2) Control requirements in automatic process mode.

The robot handling application is controlled by the PLC. When you press the **Stop** button, the red light will be on in the tricolour light, then press the **Reset** button,

![Official CR3 training-system figure, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4c5SSIWlxsVawoTKtBae%2Futp-79ad725ae932c6d0371e.png?alt=media)

the yellow light will be on, and finally press the **Start** button, the green light will be on, and the system will start automatic operation mode. When the PLC receives the discharge request signal from the robot and there is material in the bunker, the push motor is enabled and the material is pushed out. After five seconds, the push motor retracts, and the conveyor belt starts to move forward, and the conveyor belt stops moving when the movement of the material reaches the sensor in place, and then the PLC sends the signal to the robot to grab the material. This cycle is repeated for 6 times. Until the 6 materials in the bin have been placed.

According to the content in task analysis, the PLC program for robot handling application is designed. The distribution of PLC program blocks and PLC variables is shown in Figure 4-46.

**Figure 4-46 PLC program blocks and PLC variable distribution**

#### 4.1.1 Main (OB1) program

![Official CR3 training-system figure, source page 100](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEl8KzeUSPCoeAc7rAURm%2Futp-74fb81393c11e1053e87.jpg?alt=media)

The Main (OB1) program is shown in Figure 4-47. The automatic flow program segment is shown in Figure (a), the manual control program segment is shown in Figure (b), and the robot control program segment is shown in Figure (c).

（ **a** ） **Automatic control**

![Official CR3 training-system figure, source page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5dP0s85fHCSkXUKJUccY%2Futp-3fd7c25ac9cf96348483.jpg?alt=media)

（ **b** ） **Manual control**

（ **c** ） **Robot control**

**Figure 4-47 Main Program Sweep (Cycle)**

![Official CR3 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMTqf2M5miIQwT40IxueF%2Futp-3004089e96776744b2f1.jpg?alt=media)

![Official CR3 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FObr032RF08KekK7E5Aki%2Futp-9a239cf54846ac9281ae.jpg?alt=media)

#### 4.1.2 Automatic control (FB1) program

The automatic control (FB1) program is shown in Figure 4-48. It includes system initialization (Figure a), external equipment initialization (Figure b), automatic operation process of equipment starting (Figure c), and three-color light (Figure d).

（ **a** ） **Initialization status**

![Official CR3 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fx5jgyiqbd1hFM5OmbG2m%2Futp-538ec1c5746213053409.jpg?alt=media)

![Official CR3 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FluNMghqmuGnT6O9qP5KQ%2Futp-ddcf9b305422fa66f7b4.jpg?alt=media)

（ **b** ） **Device initialization**

（ **c** ） **The device runs the process**

![Official CR3 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2XBPdg4enqabyYdVy5ti%2Futp-2f09526d1589182036d0.jpg?alt=media)

![Official CR3 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJqAKZNYbQzzzZv4gqtnI%2Futp-a303932a32170c21edd8.jpg?alt=media)

（ **d** ） **Tricolor lamp**

**Figure 4-48 Automatic control (FB1) program**

#### 4.1.3 Automatic control (FC1) program

The automatic control (FC1) program is shown in Figure 4-49.

**Figure 4-49 Automatic control (FC1) program**

#### 4.1.4 Robot Status Control (FC2) program

The robot Status Control (FC2) program is shown in Figure 4-50

![Official CR3 training-system figure, source page 105](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9MQXLmZLvWbmmc2UK3us%2Futp-5c45900ba163aa586358.jpg?alt=media)

**Figure 4-50 Robot Status Control (FC2) program**

#### 4.1.5 Automatic control data

Figure 4-51 shows the automatic control data.

**Figure 4-51 Automatic control data**

![Official CR3 training-system figure, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F76LQvWFa6XyueXVcATAY%2Futp-4adea7e53c65b256d9ea.jpg?alt=media)

![Official CR3 training-system figure, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaNjKrktoONyQVsTJ1diV%2Futp-9548ad426f6d10c8d4f2.jpg?alt=media)

Explanation: The variables flag1 and flag2 are identification variables and are generally used

to control the process and judgment conditions of the program.

#### 4.2 Description of HMI program

The touch screen interface needs to include four interfaces: main interface, automatic control, manual control and monitoring interface.

#### 4.2.1 Main interface

In the maine interface, as shown in Figure 4-52, there are four buttons: **Main interface** , **Automatic control** , **Manual control** and **IO monitoring** . You can enter the corresponding interface by pressing the corresponding button.

**Figure 4-52 main interface**

#### 4.2.2 Automatic control interface

The automatic control interface, as shown in Figure 4-53, has three buttons: **STOP** , **RESET** , and **START** . Press the **STOP** button to stop the system from running; press the **RESET** button to reset all IO to the initial state; press the **START** button to start the system.

![Official CR3 training-system figure, source page 107](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZn8AUghUvM0rhG8QxbQ0%2Futp-7f83b8eb1db46f46487e.png?alt=media)

**Figure 4-53 Automatic control interface**

#### 4.2.3 Manual control interface

The manual control interface, as shown in Figure 4-54, includes control buttons

for tricolor lights, buzzers, pushing motors, and conveyor belts.

**Figure 4-54 Manual control interface**

![Official CR3 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6hXr8D56nla0a4kVLYL3%2Futp-3da40b1e24679b8eacfd.jpg?alt=media)

![Official CR3 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhybI3fwm5twWZeDLak6v%2Futp-a99b0d86970a7c96f3fe.jpg?alt=media)

#### 4.2.4 IO monitoring interface

The IO monitoring interface, as shown in Figure 4-55, monitors the status of all input and output ports; when the robot experiences a malfunction alarm, the buzzer in the three color light will sound.

**Figure 4-55 IO monitoring interfac**

#### 4.3 Description of the robot program

The robot program is divided into two parts: the main thread scr0.lua program and the global.lua that defines module functions. The specific program design is as follows:

#### 4.3.1 src0.lua

Use a ruler or other measuring tool to measure the distance between two adjacent

circular blocks in the storage area, as shown in Figure 4-56.

![Official CR3 training-system figure, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0qaLETZ90MFSm32Nwcfs%2Futp-90be25fd49fc4f2050cb.jpg?alt=media)

**Figure 4-56 Measure interval between blocks**

According to the measurement results, the variable of material spacing at the

discharge point was set in the **src0.lua** program, as shown in Figure 4-57.

**Figure 4-57 Set the variable of material spacing**

After the robot program is started, the robot first moves to the safety point and

resets the end of the sucker, as shown in Figure 4-58.

**Figure 4-58 Initialization preparation**

After the robot moves to the safety point, it sends the material discharge request signal to PLC, and then detects whether the material has reached the detection point of the sensor in place on the conveyor belt by calling the **get\_material()** function in the global.lua program. After the material is in place, the robot is controlled to move to the P2 point to absorb the material. Then move the materials to 6 discharge points in the storage area to place the materials, as shown in Figure 4-59.

![Official CR3 training-system figure, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0LcPN4rhtsAbSo3xBLdL%2Futp-c95899a2f6de4e2a038b.jpg?alt=media)

![Official CR3 training-system figure, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwpUny7whOOJimSmhFzD9%2Futp-46795bf535b8180a2647.jpg?alt=media)

**Figure 4-59 Procedures for robot picking and discharging materials**

Note: The first discharge point P3 is the reference point for other discharge points. Due to the fixed discharge position, the coordinates of the discharge points for the other 5 circular materials are calculated based on the number of cycles and the distance between P3 and each discharge point.

#### 4.3.2 global.lua

Figure 4-60 shows the function of waiting for DI signal. The function is used to

wait for external signal input.

**Figure 4-60 Define the function that waits for the DI signal**

Define the function of the robot to pick up material at the conveyor belt's gripping point. After waiting for the material to reach the position of position sensing

![Official CR3 training-system figure, source page 111](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwcFUBtKfcRXDUSucUJv0%2Futp-82bf493d723bbc770670.jpg?alt=media)

![Official CR3 training-system figure, source page 111](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWFOKl1mWJSjsotXdJ4nU%2Futp-1c480c706643d2a1cf51.jpg?alt=media)

detection, the robot moves to the grasping point to extract the material. The program is shown in Figure 4-61.

**Figure 4-61 The function of robot absorbing material**

![Official CR3 training-system figure, source page 112](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FiJ2xROdPn0r8XzOKP4hZ%2Futp-4e05b992aedc2dd9b260.jpg?alt=media)

## Chapter 5 Static palletizing

**1. Introduction**

The specific task to be realized in this chapter is to use a robot to transport 3 color 6 building blocks placed in the standard vision board, as shown in Figure5-1. While moving them to the rectangular/circular load plate of the storage area, and placing them in different colors as required, as shown in Figure5-2.

**Figure5-1 Six square materials**

**Figure5-2 Storage area**

### 2. Hardware Description

#### 2.1 Install standard vision carrier board

![Official CR3 training-system figure, source page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F86fhadFdUi6aea9lkIUu%2Futp-90bdbfdb7357a4ef3e73.jpg?alt=media)

![Official CR3 training-system figure, source page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6ilZrWAg8CGGsG0EN43s%2Futp-66c459ac88f001231cc2.jpg?alt=media)

Install the standard vision carrier board above the conveyor belt, as shown in

Figure5-3 .

**Figure5-3 Install standard vision board**

#### 2.2 IO configuration description

The IO configuration of static palletizing is shown in Table 5-1 .

**Table 5-1 Control button IO configuration**

| **Output** | **Description** |
| ---------- | --------------- |
| DO9        | Vacuumpumping   |
| DO10       | Vacuum breaking |

### 3. Program Debugging

#### 3.1 Preparation

#### 3.1.1 Turn on CR3 general training system power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3 general training system, as shown in Figure 5-4.

![Official CR3 training-system figure, source page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkM8jyhkiHTjsCxXcZh8Y%2Futp-98fb837f4e8753b59d2c.jpg?alt=media)

**Figure 5-4 CR3 general training system power switch**

#### 3.1.2 Turn on the air pump box switch

Turn on the power switch of the air pump box and rotate the control button to

**Auto** , as shown in Figure 5-5.

**Figure 5-5 Pump box**

#### 3.1.3 Turn on the light source switch

Turn on the light source switch, as shown in Figure 5-6.

![Official CR3 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdYXuXhds2VJQa1ytyJ40%2Futp-76fe66931110b0a471b2.jpg?alt=media)

![Official CR3 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzFjaVYWzyhPEtjiJk3QP%2Futp-01cbfdd56a2023048af3.jpg?alt=media)

**Figure 5-6 Light source switch**

#### 3.1.4 Power on the robot.

Check whether the power switch of the robot controller and the robot switch are turned on. If not, all switches need to be turned on, as shown in Figure 5-7.

**Figure5-7 Robot control cabinet**

#### 3.1.5 Connection network cable

Connect one end of a network cable to the LAN1 port of the robot the controller, and connect the other end to the upper network port of the PLC module box. Then connect one end of a network cable to the lower network port of the PLC module box, and connect one end to the computer, as shown in Figure 5-8.

![Official CR3 training-system figure, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

![Official CR3 training-system figure, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoZeyuuzXAE8alHg9x3T6%2Futp-2984aa0143483d7d9143.jpg?alt=media)

**Figure5-8 Connection network cable**

#### 3.1.6 Change the IP address of the computer.

Open your computer's control panel, select Network and Internet/ Network and Share Center, and enter the network and share center window. Click Ethernet and select Properties to enter the ethernet property setting page. Double-click Internet Protocol Version 4 (TCP/IPv4) to enter the interface of Internet Protocol version 4 (TCP/IPv4) properties, and reset the IP address of PC side, as shown in Figure 5-9. The default address of the robot is 192.168.5.1, and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment with the robot. The subnet mask and default gateway are the same as those of the robot, taking 192.168.5.101 as an example here.

![Official CR3 training-system figure, source page 117](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfnbEewXKvH687fUFbqQb%2Futp-3ed0ec4448fe5f60a565.png?alt=media)

**Figure5-9 PC IP address Settings**

#### 3.2 Connect camera

Plug the dongle of DobotVisionStudio into the computer. Plug the USB cable of

the training system (used to connect the camera) into the compute, as shown in Figure

5-10.

**Figure5-10 Plug in the camera USB port and dongle**

#### 3.3 Connect DobotStudio Pro to the robot.

Double-click DobotStudio Pro v2.6.1 to open the software. Select CR3 on the top toolbar, and click Connect, as shown in Figure 5-11.

![Official CR3 training-system figure, source page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUAdYCXsL6BI4BYVcjBwO%2Futp-665bb93e97b1f93a54ea.png?alt=media)

![Official CR3 training-system figure, source page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5vGoHrrcFRy5n4sZp12o%2Futp-7cf068a484bda5432fda.png?alt=media)

**Figure5-11 Connect robot**

After successful connection, you will see a prompt message, and the connection

status will change to **Connected** , as shown in Figure 5-12。

**Figure5-12 Connected robots**

#### 3.4 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 5-13.

Then click **Confirm modification** , the enable icon becomes " ".

![Official CR3 training-system figure, source page 119](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure5-13 Set load parameters**

#### 3.5 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 5-14.

**Figure 5-14 Global rate settings**

#### 3.6 Adjust the initial pose of the robot

**(1) Select Setting>Basic .**

(2) Check if the joint coordinate of the robot is as shown in Figure 6-15, and then click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

![Official CR3 training-system figure, source page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

**Figure 6-15 Adjusting the initial pose of the robot**

#### 3.7 Debug vision program

#### 3.7.1 Eye-to-hand calibration

* (1) Eye-to-hand calibration

Remove the end of the suction cup of the CR3 robot by hand and install the

prepared calibration needle on the end of the robot, as shown in Figure 5-16.

**Figure5-16 Install calibration needle**

![Official CR3 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

![Official CR3 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLtI7qw2ct5qH9gra5u7f%2Futp-fd52f0528e067cc8b0a6.png?alt=media)

(2) Place the calibration paper on the standard vision carrier board, as shown in

Figure 5-17.

**Figure5-17 Place the calibration paper**

(3) Open DobotVisionStudio, and select **General Solution.**

(4) Establish the solution process. In the toolbox, drag the **Image Source** tool

from the **Acquisition** sub toolbox to the process editing area, as shown in Figure5-18.

**Figure5-18 Solution process**

Set **0 Image Source1** parameters. Double-click **0 Image Source1** to set parameters. Select **Camera** as the image source, as shown in Figure 5-19. Click **Camera management** on the right side of the associated camera to enter the camera management interface.

![Official CR3 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0easjrUgyi6UmCCqyVFe%2Futp-000b6f2bf407c2fccd31.jpg?alt=media)

![Official CR3 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUxqe4sO6ePG9ltCSLTSm%2Futp-74da5aad8c09a5020cf7.jpg?alt=media)

**Figure5-19 Image Source**

Create global camera. Click the plus sign on the right of **Device List** to create **1 Global Camera 1** and set camera parameters. On the **Common Params** screen, click the small triangle symbol on the right of **Choose Camera** to select the camera that is currently directly connected to the computer. Select **Mono8** in **Pixel Format** of **Image Params** , as shown in Figure 5-20. Click **Trigger Settings** , set **Trigger Sourse** to **SOFTWARE** , and click **Confirm** , as shown in Figure 5-21. Then return to the image source interface. In the **0 Image Source 1** interface, click the small triangle symbol in the lower right corner of the associated camera and select **1 Global Camera1** , as shown in Figure 5-22.

**Figure5-20 Common Params**

![Official CR3 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoO2B5F62t2cMOwLMCMj0%2Futp-d30f26b70bbbbf837708.png?alt=media)

![Official CR3 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpvfQCyKsLhCU8Dyl1iSF%2Futp-5bce1e064af32a01bba6.jpg?alt=media)

**Figure5-21 Trigger Settings**

**Figure5-22 Relate Camera**

Then click" ( **Continuously)** " and adjust the aperture and focus ring of the lens and the exposure time of the camera until you can see a clear image in the image display area. The image collection results are shown in Figure 5-23.

![Official CR3 training-system figure, source page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDIIOWMraRE5jeh4J84mc%2Futp-e3f076bf49cb5ff64f1c.jpg?alt=media)

![Official CR3 training-system figure, source page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0KIGoI3XUG20X0DrXDRJ%2Futp-6b20bb76fefb77320e71.jpg?alt=media)

**Figure5-23 Image collection result**

(5) Add **calibration of calibration board** tool in the solution process

Drag the **CalibBoard Calib** tool from the **Calibration** sub toolbox to the process editing area and connect it to **0 Image Source1** , as shown in Figure 5-24

**Figure5-24 Process**

Note: The calibration of the calibration board is used to obtain the calibration point, and provide the pixel coordinates of the calibration point for N-point calibration。

(6) Add **N-point Calibration** in the solution process. Drag the **N-point Calibration** tool from the **Calibration** sub toolbox to the process editing area and connect it to **2 CalibBoard Calib1** . After **3N-point Calibration1** is connected to **2**

**CalibBoard Calib1** , click the " ( **Once)** " button. In the image display area, the nine calibration points and its calibration sequence will be automatically displayed, as shown in Figure 5-25.

![Official CR3 training-system figure, source page 125](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNZePOvwPZUC6too52G12%2Futp-a001f771ede6bf552678.jpg?alt=media)

**Figure5-25 Check nine calibration points and calibration sequence**

Basic parameter settings for **3N-point Calibration1** . Double-click **3N-point Calibration** to set basic parameters. Set **Translation Number** in **Basic Params** .

Keep the default parameter 9 and set **Rotation Number** . Click the icon " " to the right of translation number, as shown in Figure 5-26. The **Edit Calibration Point** interface that pops up allows you to edit the calibration points, as shown in Figure 5-27.

**Figure5-26 3 N-Point Calibration**

![Official CR3 training-system figure, source page 126](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmPSkpR4PcIOyq7R224B6%2Futp-1a111b95c71854497755.jpg?alt=media)

![Official CR3 training-system figure, source page 126](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZgVCoH0vV4rtwLT6wm6X%2Futp-1c8c17ad7b2e51026fa8.jpg?alt=media)

**Figure5-27 Edit Calibration Points**

In **Edit Calibration Points** page, exchange Line 3 (ID: 3) and Line 5 (ID: 5)

data, as shown in Figure 5-28.

**Figure5-28 “Edit Calibration Points” after data exchange**

After clicking the " **Refresh** "" **Confirm** "" **Execute** ", you can see that the calibration sequence turns into the font **2** in the image display area, as shown in Figure 5-29.

![Official CR3 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH3fUADZt5OHpruHPYXFI%2Futp-92b2b2a4f23d7ef7fab2.jpg?alt=media)

![Official CR3 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvu6iL3RRZl3dS0zmkQSz%2Futp-c90bd98253620309409f.jpg?alt=media)

**Figure5-29 Calibration sequence after data exchange**

Open the **DobotStudio Pro** software, connect the robot, and turn on the robot's enable switch. According to the calibration sequence of 9 calibration points, the robot is controlled to reach the first target point, as shown in Figure 5-30. Read the X and Y physical coordinate values of the first the calibration point on **DobotStudio Pro** , as shown in Figure 5-31, and then fill the X and Y physical coordinate values into the corresponding lines of " **Edit the calibration point** " in **DobotVisionStudio** respectively. Follow the same steps to obtain the physical coordinate values for the remaining 8 Points and fill them in the " **Edit Calibration Points** " table in **DobotVisionStudio** software, as shown in Figure 5-32.

**Figure5-30 First calibration point**

![Official CR3 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBY4AILgYgeqoNYikCwYc%2Futp-1e4e70901b0b9f9bbf4b.jpg?alt=media)

![Official CR3 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD22afonhL96UdjDM5LV9%2Futp-d03c9c7797e450a4c518.jpg?alt=media)

**Figure5-31 Robot physical coordinates of the first calibration point**

![Official CR3 training-system figure, source page 129](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhDvuMuDWrdoEyh8LjgWi%2Futp-7cd95e9e3a44a8c39e9e.jpg?alt=media)

![Official CR3 training-system figure, source page 129](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwmYPRL4J5XySH2SH1pMx%2Futp-89147f65e1432274c342.jpg?alt=media)

**Figure5-32 Physical coordinates of 9 calibration points**

After the operation of editing the calibration point is completed, click **Refresh** and then click **Confirm** to save the physical calibration coordinates, as shown in Figure 5-33.

**Figure5-33 "N point calibration" completed**

In the **Basic Params** interface of **3N-point Calibration1** , click the **Create Calibration File** button to export and store the calibration file to the computer, and named **Calibration file** for future calls, as shown in Figure 5-34.

**Figure5-34 Generate calibration file**

Add **Calibration Transformation** in the flow. After calibration, you can add this tool to verify whether the calibration is accurate.Drag **Calibration Transformation**

![Official CR3 training-system figure, source page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhChCLWIftTI7tQC70F2E%2Futp-4cd240f5fe7c291acf64.jpg?alt=media)

![Official CR3 training-system figure, source page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFLimlIMLfeA73ktbA2MS%2Futp-4c12c11a50f1d5ce721f.jpg?alt=media)

in **Calculation** sub toolbox to the process editing area, and connect it with **3N-point Calibration1** ,as shown in Figure 5-35.

**Figure5-35 Scheme process**

Set **4 Calibration Calibration1** basic parameters. In **Basic Params** page, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** , and select the **Calibration file** generated by hand-eye calibration for **Load Calibration File** , as shown in Figure 5-36.

**Figure5-36 Set 4Calibration Transformation1 parameters**

![Official CR3 training-system figure, source page 131](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fox4bycXawVQnpAyuwjNZ%2Futp-2d60c09ffc9497eb43f5.jpg?alt=media)

Click " **(Once)** ", and check whether the 9 calibration data converted from **4 Calibration Transformation1** are consistent with the material coordinates obtained by the robot during N-point calibration, as shown in Figure 5-37. If consistent, the calibration is accurate. Otherwise, you need to re-calibrate.

**Figure5-37 Comparison result**

#### 3.7.2 Import vision program

Open DobotVisionStudio 4.1.2, and select **General Solution** . Select **Open** in the toolbar. Find the vision sorting program and click **Open** . The imported vision program is shown in Figure 5-38.

![Official CR3 training-system figure, source page 132](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFxuJSxXIBsNsvkZ3xVoT%2Futp-02fb55ad6a056ea0abcc.jpg?alt=media)

**Figure5-38 Vision program**

#### 3.7.3 Place detection object

Put the 3 colors blocks of red, green and blue into the detection field, as shown in

Figure 5-39.

125<br>

![Official CR3 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUW1MSJcUrjr0fnqSRadr%2Futp-981daf3201d490131393.jpg?alt=media)

![Official CR3 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFpjkgYOHlPjXfOZmhnSI%2Futp-ef0829845a4546a87bc9.jpg?alt=media)

**Figure5-39 Place blocks within the detection view**

#### 3.7.4 Debug program parameters

(1) Debug **0 Image Source1** parameters

Click " **(Once)** ", select **0 Image Source1** and observe whether the image is clear. If the image is not clear or there is no image, you need to reset the parameters according to the method described in 3.7.1. When setting the parameters, set **Pixel Format** to **RGB8** . The image collected by the camera is shown in Figure 5-40.

**Figure5-40 Collected image**

* (2) Debug **2 Color Transformation1** parameters

Double-click **2 Color Transformation1** to check whether **Transfer Type** is **RGB to Grayscale** , as shown in Figure 5-41. If not, modify as the figure.

![Official CR3 training-system figure, source page 134](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2JldY4cODyViwalHsOJ1%2Futp-be39a0ffa44c28bea88a.jpg?alt=media)

**Figure5-41 2Color Transformation1**

Click " **(Once)** ". The execution result of **2 Color Transformation 1** is shown

in Figure5-42.

**Figure5-42 Grayscale Image**

(3) Debug **3 Fast Match1** parameters

![Official CR3 training-system figure, source page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjYDHifLyrDJK5kGo39xi%2Futp-464c9c3ecf48362bd885.jpg?alt=media)

![Official CR3 training-system figure, source page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgPjJU5mXN5ixK1O76QKt%2Futp-2608f1f3c83242d444f3.jpg?alt=media)

Double-click **3 Fast Match1** . Click **Run Params** and modify **Max Number to find** to **3** . Then click **Execute** and observe whether all the blocks are recognized in the image display area, as shown in Figure 5-43.

**Figure5-43 Run Params**

If all the blocks are recognized, use the original model. Otherwise, you need to

re-create the feature model, as described below.

* ① Enter **Feature Model** page. Delete the original model and then click **Create** ,

as shown in Figure 5-44。

**Figure5-44 Feature Model**

② In template creation page, click **Current Image** . Click " **(Create Rect**

**Mask)** ", select the corresponding area in the image and set corresponding model

![Official CR3 training-system figure, source page 136](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5nceRLRNS51GsKpUBJdz%2Futp-45529d085237a6efb7fc.jpg?alt=media)

![Official CR3 training-system figure, source page 136](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTxcBtcGCNpM4lUP9lbtQ%2Futp-9bb2a786bb2f2784a24a.jpg?alt=media)

parameters (generally default). Then click " **(Build Model)** ", and click **Confirm** , as

shown in Figure 5-45.

**Figure5-45 ModelSettings**

* ③ After creating the model, click **Execute** and **Confirm** , as shown in Figure

5-46.

**Figure5-46 Result**

![Official CR3 training-system figure, source page 137](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxwzoYdxLMuJFPuNPRjvG%2Futp-3dcef3da4cebf663cbac.jpg?alt=media)

![Official CR3 training-system figure, source page 137](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAmujsNSKpCyT8lPCAUOU%2Futp-8a08985ef11c34fa738e.jpg?alt=media)

Note: If not all the blocks can be recognized, maybe it is caused by the light. You can change the threshold value.

④ Double-click **3 Fast Match1** . Click **Run Params** and modify **Max Number to find** to **1** . Then click **Execute** , and the recognized block is shown in the image display area. Click **Confirm** , as shown in Figure 5-47.

**Figure5-47 Result**

* (4) Debug **4 Calibration Transformation1** parameters

Double-click **4 Calibration Transformation1** . Check whether **Coord Point** is

**Fast Match.Match Point** . Load the saved 9-point calibration file, as shown in Figure 5-48.

![Official CR3 training-system figure, source page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh3PRVQ73qmPoIsSzSPYx%2Futp-53d2dab3f9c60f2651fc.jpg?alt=media)

![Official CR3 training-system figure, source page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJDn9FGwLVnL65FqHfraj%2Futp-e3b6ed0b507bcdff2d53.jpg?alt=media)

![Official CR3 training-system figure, source page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzjYP9DnqYbVp6GGQKk92%2Futp-2c5a92831ad931aed733.jpg?alt=media)

**Figure5-48 Basic Params**

Click **Execute** and **Confirm** , and the physical coordinates of the blocks are

displayed in the result display area, as shown in Figure 5-49。

**Figure5-49 Result**

* (5) Debug **5 Color Recognition1** parameters

Click " **(Once)** ". Select **5 Color Recognition1** , and modify the image display to **ImageSource1.OutputImage** . Observe whether the colour of the image is recognized correctly, as shown in Figure 5-50.

![Official CR3 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1AW3HMBL6GrOtPhP8mcY%2Futp-307a7ef87b4a06cf0c4e.jpg?alt=media)

**Figure5-50 Result**

If the objects of different colors are recognized incorrectly, you need to debug according to the following method：

① Double click **5 Color Recognition1** . In **Basic Params** page, check whether

**Input Source** and **ROI Area** are set as Figure 5-51.

**Figure5-51 Basic Params**

![Official CR3 training-system figure, source page 140](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxPUh8icHHCw0nAGMMDS2%2Futp-39a2adb44422f664ca5a.jpg?alt=media)

![Official CR3 training-system figure, source page 140](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYN69Gy3MMUF2iOJElMop%2Futp-6d4a903696e4a078aab4.jpg?alt=media)

* ② In **Color Model** page, delete the existing model. Click " **+** " to re-create
* models, as shown in Figure 5-52.

**Figure5-52 Color Model**

③ Create a red model: In ModelSettings page, click " (add the current

image)", then click "+" on the right side of Label List to add a new label, and click " ", then change the label name. Click " " in the toolbar, and drag a rectangular mask onto the image of the red building block (the selection range is the interior of the red building block image). Then click Add To Label, and you will see the added red model on the right side, as shown in Figure5-53.

![Official CR3 training-system figure, source page 141](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnkE4FwhjucbATOmn3s14%2Futp-a70d517e22281694048e.jpg?alt=media)

**Figure5-53 Create red model**

Note: The material may be reflective due to the light, which could result in a difference in

colour. In this case, you need to create several red models.

* ④ Using the same method, create the green and blue models as shown in Figure

5-54. Click **Confirm** to return to **Color Model** page.

![Official CR3 training-system figure, source page 142](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7RSngd2VEAnrZvB6UQRa%2Futp-a5af70aee1dbbdb1b0ca.jpg?alt=media)

**Figure5-54 Create green and blue model**

* ⑤ Click **Execute** and **Confirm** , and the recognized colour of the block is shown
* in the result display area, as shown in Figure 5-55.

**Figure5-55 Result**

* (6) Debug **6 Variable Calculation1** parameters

![Official CR3 training-system figure, source page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0fPtftYrBmxsVdbmhYyZ%2Futp-b833a8cc126fee9cc3bb.jpg?alt=media)

![Official CR3 training-system figure, source page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWVmDJ9RGAtdaSVCGo3G8%2Futp-35251ae276c85f9f5077.jpg?alt=media)

Click " **(Once)** ". Compare whether the value of **var0** in **6 Variable Calculation1** and the value of **MatchBoxAngle** in **3 Fast Match** are opposite to each other, as shown in Figure 5-56.

**Figure5-56 Contrast**

If the values are not opposite, you need to debug according to the following method：

① Double-click **6 Variable Calculation1** . Click " " below **Expression** to enter **Var0** page. Click "  **3Fast Match1**  **MatchRect**  **MatchBoxAngle** " to add the variable. Select the variable, and then plus " **-** " in front of the variable, that is, to get the negative value of the angle. Then click **Save** to return to the **Basic Params** page, as shown in Figure 6-56.

![Official CR3 training-system figure, source page 144](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F52NPaCyJR3OviUTo3uPK%2Futp-848b94a43f399d6a42c6.jpg?alt=media)

**Figure5-57 Expression**

② Click **Execute** and **Confirm** , and you will see the angle values, as shown in

Figure 5-58.

**Figure5-58 Result**

* (7) Debug **7 Format1** parameters

Click " **(Once)** ". Select **7 Format1** , and observe whether the result display area the format result, as shows in Figure 5-59.

![Official CR3 training-system figure, source page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA2lc6OfFVbEVW9KCjsrh%2Futp-40ffd8c3c2e92983ff7f.jpg?alt=media)

![Official CR3 training-system figure, source page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLu9QoMC0sq4be2tCo8SF%2Futp-45f5b99692353e800390.jpg?alt=media)

**Figure5-59 Result**

If not, you need to debug according to the following method：

① Double-click **7 Format1** . In **Basic Params** page, as shown in Figure 5-60,

click " **+** " to add a row. Click " **(InsertSubscription)** ", and select **5 Color Recognition1**  **Best Matched Name.**

**Figure5-60 Basic Params**

![Official CR3 training-system figure, source page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8AGQuSYKxQblZF70yWpk%2Futp-7b73f09cc846058b3d2a.jpg?alt=media)

![Official CR3 training-system figure, source page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FANxJOfPZ58hhFTxsbw89%2Futp-eb0262b61063db3ffc3d.jpg?alt=media)

② Then click **T** and enter ",". Click " " and select " **4 Calibration Transformation1**  **OutputPoint**  **TransPointX** ", Insert“ **4 Calibration Transformation1.TransPointY** ” “ **,** ” “ **<6 Variable Calculation1.var0(%1.3f)>\[0]** ”, The format parameters are shown Figure 5-61.

**Figure5-61 Foramt Params**

(8) Debug the **Communication Management** parameters

Click " " in the quick toolbar to enter **Communication Management** page. Check whether there is established **TCP Server** , and whether its parameters are consistent with the figure below. If not consistent, modify as Figure 5-62.

**Figure5-62 Communication Management**

If there is no **TCP Server** , you need to create one, as described below:

Click " " beside **Device Lists** to add devices，and set **Protocol Type** to **TCP Server** , **Load IP** to **192.168.5.101** , **Local Port** is set to **4001** , and then click **Create** ,

![Official CR3 training-system figure, source page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2EQuw9Uka8A0uAHvT5rM%2Futp-7f50877963379e3c1013.jpg?alt=media)

![Official CR3 training-system figure, source page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvgaUFaT2GJzOHxU6twb1%2Futp-8caaeb655dd91f4ea9c2.jpg?alt=media)

as shown in Figure 5-63. Finally, turn on the switch next to **1TCP Server** , as shown in Figure 5-64.

**Figure5-63 Create “TCP Server”**

**Figure5-64 Communication Management**

* (9) Debug 8 Send Data1 parameters。

Double-click **8 Send Data1** , and check whether the parameters are shown as

Figure 5-65. If not, modify as the figure. Set **Output To Communication Device** ,

![Official CR3 training-system figure, source page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fr0tQeNTH3pXahu3vdgJf%2Futp-4e1158348aead5eb659f.jpg?alt=media)

![Official CR3 training-system figure, source page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfJGPZ48G7tI9ChtqJwbc%2Futp-9cad1218317c40291cf6.jpg?alt=media)

**Communication Device** to **1 TCP Server** , and **Send Data1** to **7Format1.format\_out\[]** . Then click **Confirm** 。

**Figure5-65 8Send Data1**

(10) Set the **Global Trigger** parameters

Click " " in the quick toolbar to enter **Global Trigger** page. In **String Trigger** page, check whether the string trigger setting is shown as Figure 5-66. String

is void; **Mode** is **Mismatched** ; **Trigger Configuration** is **All Process.**

![Official CR3 training-system figure, source page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSv13bucxWIb6ODIPJ3xn%2Futp-83cbda2e5cff2c6248d0.jpg?alt=media)

![Official CR3 training-system figure, source page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8sccsP4nk2fSjyFAPbdA%2Futp-b8756c7d914fa2d559af.jpg?alt=media)

**Figure5-66 Global Trigger**

#### 3.7.5 Save program

Click " **(Save)** " in the shortcut toolbar to save the program. If you need to Save the program somewhere else on your local computer, click **File > Save as** , select the path you want to save, and give the program a name.

#### 3.8 Robot Program Debugging

#### 3.8.1 Install the coaxial sucker tool

* (1) Remove the calibration needle from the end of the robot, as shown in Figure

5-67.

**Figure5-67 Remove the calibration needle**

(2) Install the sucker on the end of the robot, as shown in Figure 5-68.

![Official CR3 training-system figure, source page 150](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQvp4KahZQkekVKishMEE%2Futp-e3a0c71a1cd80b78e119.jpg?alt=media)

**Figure5-68 Mounting the suction cup**

#### 3.8.2 Place blocks

Place blocks of different colors above the standard visual loading board, and

confirm whether the materials in the storage area are empty, as shown in Figure 5-69.

**Figure 5-69 Place blocks**

#### 3.8.3 Import program

* (1) Open **DobotStudio Pro** and enter script page. Click **File** > **Import project** ，

as shown in Figure 5-70.

![Official CR3 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtL20UGhjXziKvy9o3mAN%2Futp-8ccf3d6509d107f607f1.jpg?alt=media)

![Official CR3 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGGI3pHaQi4dR2wwOrkYy%2Futp-91e7b4e85968742f7ee3.jpg?alt=media)

**Figure 5-70 Import robot program**

* (2) Select the **CR3 Vision Sorting** folder and click **Open** , as shown in Figure
* 5-71. The program is imported into DobotStudio Pro.

**Figure5-71 Import program**

#### 3.8.4 Debug points

The visual sorting application shares 7 points, and the debugging method is as follows:

* (1) Safe point P1

![Official CR3 training-system figure, source page 152](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 152](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAIrMYmw3YqnLiKMiP5JR%2Futp-284c6e605fedc622bbf1.jpg?alt=media)

Move the robot between the conveyor belt and the storage area through hand-held teaching or inching control methods. Click **Points** in the right-side menu of DobotStudio Pro. Select **P1** and click **Cover** , as shown in Figure 5-72. Then click **OK** in the pop-up **Tips** window.

**Figure5-72 P1** point

* (2) First red block placing point P2
* ① Move the robot to one of the red blocks on the standard vision loading board
* through inching control methods. Open **IO** panel. Set **DO\_09** to **ON** to make the robot suck the block, as shown in Figure 5-73.

**Figure5-73 I/O panel**

![Official CR3 training-system figure, source page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM3pbQz4yltRElUP6pvsk%2Futp-1fa2316d0f09d8e9e558.png?alt=media)

![Official CR3 training-system figure, source page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlJMhnIzhzAdJV71BamQg%2Futp-1352085c139dbf47b66d.jpg?alt=media)

② Move the robot to the first red block placing point in the storage area through inching control method, as shown in Figure 5-74. Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the block

is placed into the groove accurately. If not, you need to re-debug the point.

**Figure5-74 First red block placing point P2**

③ Open **Points** page. Select **P2** and click **Cover,** as shown in Figure 5-75.

**Figure5-75 Update P2**

* (3) Placing points P3\~P7

Update P3-P7 using the same method of P2, according to the placement requirement of red, green and blue blocks. The point position completed by update is shown in Figure5-76.

![Official CR3 training-system figure, source page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcDARI74Ahpk05nAB7EYO%2Futp-485afbf6b0265e32e078.jpg?alt=media)

![Official CR3 training-system figure, source page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMijgX23pecbD8INv3Jkc%2Futp-935f17c720a577115d13.jpg?alt=media)

**Figure5-76 Updated points**

#### 3.8.5 Set communication

Set the IP address of the robot program to the IP address of the computer ( **192.168.5.101** ) and the port number to **4001** . Ensure that the IP address and port number of the TCP server in the robot program are consistent with the local IP address and port number in the visual communication Settings, as shown in Figure 5-77.

**Figure5-77 Set communication**

#### 3.8.6 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 5-78.

![Official CR3 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrEJXuaQ2gLmhLIjidFDT%2Futp-bfa502e3bc4a959d7617.jpg?alt=media)

**Figure5-78 Save program**

Note: " " is for saving the program to the robot controller. If you want to save the

modified program to the local computer, you need to use " ".

#### 3.8.7 Run program

Click the " " button to see if the program runs as follows:

The vision system detects the data of blocks, and transmits the colour and position data of blocks to the robot. After obtaining the information, the robot moves to the detection area to suck the blocks, sorts and places them in the corresponding

colour area. The sorting effect is shown in Figure 5-79.

**Figure5-79 Sorting completed**

#### 3.8.8 Export program

Click **File** > **Export project** , and select the path where the program is stored,

then, in the dialog box that pops up, name the program.

![Official CR3 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6ilZrWAg8CGGsG0EN43s%2Futp-66c459ac88f001231cc2.jpg?alt=media)

![Official CR3 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC0QQSLCSMJBKDQ3nCPnD%2Futp-5e301c25cfddad6c7809.jpg?alt=media)

Note: **Export project** is to export the program to your local computer for backup.

**4. Program Description**

#### 4.1 Vision program description

This section only describes the main functions of each tool in the program. For specific parameter settings of the tools, please see the vision project file.

The vision program is shown in Figure 5-80. **0 Image Source1** is mainly used for image acquisition. During the system operation, the camera takes photos immediately after the vision software receives the trigger signal sent by the robot. The images acquired are all coloured images because colour recognition is to be performed. **2 Color Transformation1** is mainly used for converting colour images into grayscale images to locate grayscale images. **3 Fast Match1** is mainly used for locating grayscale images, and **3 Fast Match1** is used to obtain the image coordinates and matching angle of the detected object; **4 Calibration Transformation1** is used for transforming the image coordinates obtained by **3 Fast Match1** into actual physical coordinates. **5 Color Recognition1** is used for creating a colour model to recognize the colour of blocks so that sorting can be performed by colour. **6 Variable Calculation1** is used for correcting the matching angle. **7 Format1** is used for summarizing and defining the format of the information that the vision system needs to send to the robot. **8 Send Data1** is used for sending the contents of **7 Format1** to the robot.。

**Figure5-80 Vision program**

#### 4.2 Robot program description

#### 4.2.1 src0.lua

The relevant variables for defining the robot program are shown in Figure 5-81.

**Figure5-81 Define the relevant variables**

Define TCP data transfer function as shown in Figure 5-82. The robot sends the signal **ok** to the vision, which is triggered by the photo, and then receives the data sent by the vision.

**Figure5-82 Data transfer program**

The function of defining the robot to absorb the blocks at the calibration point is shown in Figure 5-83. The robot absorbs the blocks in the standard vision loading board according to the coordinate information sent by the vision.

![Official CR3 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj3PDoaOXiFpoODwwjDCB%2Futp-7dd18cd53776f1f0f549.jpg?alt=media)

![Official CR3 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGfnN5WMabNFhMCg5UUfB%2Futp-e2ff7f2718f205dc6ca5.jpg?alt=media)

**Figure5-83 Robot feeding program**

The program of communication is shown in Figure 5-84, which is mainly to create TCP client and establish a connection with TCP server (visual).

**Figure5-84 The program of communication**

The program for resetting the relevant IO output port is shown in Figure 5-85. It is mainly to set some output port IO signals to **0.**

**Figure5-85 Procedure of Reset outlet**

The complete sorting program of the robot is shown in Figure5-86, Figure 5-87 and Figure5-88. The program circulates for 6 times. After obtaining the color and coordinate information of the building blocks sent by the vision, the robot will absorb the building blocks, and then place them into the groove where the rectangular/circular workpiece plate corresponds in the storage area, and then return to the safe point P1.

![Official CR3 training-system figure, source page 160](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fv1AOmW7UQLmZW8osoHzD%2Futp-e6e751e712fb2b8a9dd9.jpg?alt=media)

**Figure5-86 Robot sorted the red blocks to points P2 and P3**

**Figure5-87 Robot sorted green blocks to points P4 and P5**

![Official CR3 training-system figure, source page 161](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1hPcqHUXA0wqFuUTTTvy%2Futp-03e7252fe45fdf724db5.jpg?alt=media)

![Official CR3 training-system figure, source page 161](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMMQ1guYqxGBAWmK3UrZ2%2Futp-04aaa09adbe35919e3bf.jpg?alt=media)

**Figure5-88 Robot sorted blue blocks to points P6 and P7**

#### 4.2.2 global.lua

The function defining the string segmentation is shown in Figure 5-89. This

function is used to process the data sent from the visual side.

**Figure5-89 Function that defines string segmentation**

![Official CR3 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeAovKVepU4VOLFWHo3ws%2Futp-c3d1662fc56ae7655636.jpg?alt=media)

![Official CR3 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLjvPNJIuc9Cvn8VXFMUB%2Futp-04f00a45c0bdea8782d7.jpg?alt=media)

## Chapter 6 Phone chip assembly

**1. Introduction**

The specific task to be realized in the mobile phone chip assembly application is to use the robot to install 6 chips (as shown in Figure 6-1) placed in the standard visual loading board into 6 grooves in the mobile phone base (as shown in Figure 6-2).

**Figure6-1 Phone chip**

**Figure6-2 Phone model**

![Official CR3 training-system figure, source page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4XquW1Dc80CQjyhgFamp%2Futp-1ee5e03df3eddec7ed73.jpg?alt=media)

![Official CR3 training-system figure, source page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FN6QubdY3gGkAaMG4ZhHr%2Futp-71980797dbfd19617cd1.jpg?alt=media)

### 2. Hardware Description

#### 2.1 Install standard vision loading board

Install the standard vision board above the conveyor belt, as shown in Figure 6-3.

**Figure 6-3 Install standard vision board**

#### 2.2 Install phone model board

Install the phone model board to the installation station, as shown in Figure 6-4.

**Figure 6-4 Phone model board**

Note: The picture is for reference only, the base model of the mobile phone is placed

![Official CR3 training-system figure, source page 164](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkM8jyhkiHTjsCxXcZh8Y%2Futp-98fb837f4e8753b59d2c.jpg?alt=media)

![Official CR3 training-system figure, source page 164](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNlvW8PyaXIfdZAGKSzF3%2Futp-30b5b3acb8d27f240e2f.jpg?alt=media)

according to the actual mobile phone case.

#### 2.3 IO configuration

The IO configuration for installing mobile phone chips is shown in Table 6-1。

**Table 6-1 IO configuration of phone chip assembly**

| **Output** | **Description** |
| ---------- | --------------- |
| DO9        | Vacuumpumping   |
| DO10       | Vacuum breaking |

**3. Program Debugging**

#### 3.1 Preparation

#### 3.1.1 Turn on CR3 general training system power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3 general training system, as shown in Figure 6-5.

**Figure6-5 CR3 general training system power switch**

#### 3.1.2 Turn on the air pump box switch

Turn on the power switch of the air pump box and rotate the control button to **Auto** , as shown in Figure 6-6.

![Official CR3 training-system figure, source page 165](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVv3xfRTGdCXB1gtLZ6FI%2Futp-44489226e5513b810567.jpg?alt=media)

**Figure6-6 Air pump box**

#### 3.1.3 Turn on the light source switch

Turn on the light source switch, as shown in Figure 6-7.

**Figure6-7 Light source switch**

#### 3.1.4 Power on the robot

Check whether the power switch of the robot controller and the robot switch are turned on. If not, all switches need to be turned on, as shown in Figure 6-8.

![Official CR3 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3y1I9YDtAWjvsZ8KCzRQ%2Futp-1aacd46a70c34f01e0e9.jpg?alt=media)

![Official CR3 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzFjaVYWzyhPEtjiJk3QP%2Futp-01cbfdd56a2023048af3.jpg?alt=media)

**Figure6-8 Robot control cabinet**

#### 3.1.5 Connection network cable

Connect one end of a network cable to the LAN1 port of the robot the controller, and connect the other end to the upper network port of the PLC module box. Then connect one end of a network cable to the lower network port of the PLC module box,

and connect one end to the computer, as shown in Figure 6-9.

**Figure6-9 Connection network cable**

#### 3.1.6 Change the IP address of the computer.

Open your computer's control panel, select Network and Internet/ Network and Share Center, and enter the network and share center window. Click Ethernet and select Properties to enter the ethernet property setting page. Double-click Internet Protocol Version 4 (TCP/IPv4) to enter the interface of Internet Protocol version 4

![Official CR3 training-system figure, source page 167](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

![Official CR3 training-system figure, source page 167](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfnbEewXKvH687fUFbqQb%2Futp-3ed0ec4448fe5f60a565.png?alt=media)

(TCP/IPv4) properties, and reset the IP address of PC side, as shown in Figure 6-10. The default address of the robot is 192.168.5.1, and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment with the robot. The subnet mask and default gateway are the same as those of the robot, taking 192.168.5.101 as an example here.

**Figure6-10 PC IP address Settings**

#### 3.2 Connect camera

Plug the dongle of DobotVisionStudio into the computer. Plug the USB cable of the training system (used to connect the camera) into the compute, as shown in Figure

6-11.

**Figure6-11 Plug in the camera USB port and dongle**

![Official CR3 training-system figure, source page 168](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUAdYCXsL6BI4BYVcjBwO%2Futp-665bb93e97b1f93a54ea.png?alt=media)

![Official CR3 training-system figure, source page 168](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5vGoHrrcFRy5n4sZp12o%2Futp-7cf068a484bda5432fda.png?alt=media)

#### 3.3 Connect DobotStudio Pro to the robot.

Double-click DobotStudio Pro v2.6.1 to open the software. Select CR3 on the top toolbar, and click Connect, as shown in Figure 6-12.

**Figure 6-12 Connect robot**

After successful connection, you will see a prompt message, and the connection

status will change to **Connected** , as shown in Figure 6-13。

**Figure 6-13 Connected robots**

#### 3.4 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 6-14. Then click **Confirm modification** , the enable icon becomes " ".

![Official CR3 training-system figure, source page 169](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure6-14 Set load parameters**

#### 3.5 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 5-14.

**Figure 5-14 Global rate settings**

#### 3.6 Adjust the initial pose of the robot

**(1) Select Setting>Basic .**

(2) Check if the joint coordinate of the robot is as shown in Figure 5-15, and then click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

![Official CR3 training-system figure, source page 170](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

**Figure6-16 Adjusting the initial pose of the robot**

#### 3.7 Debug vision program

#### 3.7.1 Eye-to-hand calibration

* (1) Eye-to-hand calibration。

Remove the end of the suction cup of the CR3 robot by hand and install the

prepared calibration needle on the end of the robot, as shown in Figure 6-17.

**Figure6-17 Install calibration needle**

![Official CR3 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

![Official CR3 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLtI7qw2ct5qH9gra5u7f%2Futp-fd52f0528e067cc8b0a6.png?alt=media)

* (2) Place the calibration paper on the standard vision carrier board, as shown in

Figure 6-18。

**Figure6-18 Place the calibration paper**

(3) Open DobotVisionStudio, and select **General Solution.**

(4) Establish the solution process. In the toolbox, drag the **Image Source** tool

from the **Acquisition** sub toolbox to the process editing area, as shown in Figure 6-19。

**Figure6-19 Solution process**

Set **0 Image Source1** parameters. Double-click **0 Image Source1** to set parameters. Select **Camera** as the image source, as shown in Figure 6-20. Click **Camera management** on the right side of the associated camera to enter the camera management interface.

![Official CR3 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0easjrUgyi6UmCCqyVFe%2Futp-000b6f2bf407c2fccd31.jpg?alt=media)

![Official CR3 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUxqe4sO6ePG9ltCSLTSm%2Futp-74da5aad8c09a5020cf7.jpg?alt=media)

**Figure6-20 Image Source**

Create global camera. Click the plus sign on the right of **Device List** to create **1 Global Camera 1** and set camera parameters. On the **Common Params** screen, click the small triangle symbol on the right of **Choose Camera** to select the camera that is currently directly connected to the computer. Select **Mono8** in **Pixel Format** of **Image Params** , as shown in Figure 6-21. Click **Trigger Settings** , set **Trigger Sourse** to **SOFTWARE** , and click **Confirm** , as shown in Figure 6-22. Then return to the image source interface. In the **0 Image Source 1** interface, click the small triangle symbol in the lower right corner of the associated camera and select **1 Global Camera1** , as shown in Figure 6-23.

**Figure6-21 Common Params**

![Official CR3 training-system figure, source page 173](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoO2B5F62t2cMOwLMCMj0%2Futp-d30f26b70bbbbf837708.png?alt=media)

![Official CR3 training-system figure, source page 173](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpvfQCyKsLhCU8Dyl1iSF%2Futp-5bce1e064af32a01bba6.jpg?alt=media)

**Figure6-22 Trigger Settings**

**Figure6-23 Relate Camera**

Then click" ( **Continuously)** " and adjust the aperture and focus ring of the lens and the exposure time of the camera until you can see a clear image in the image display area. The image collection results are shown in Figure 6-24.

![Official CR3 training-system figure, source page 174](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDIIOWMraRE5jeh4J84mc%2Futp-e3f076bf49cb5ff64f1c.jpg?alt=media)

![Official CR3 training-system figure, source page 174](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0KIGoI3XUG20X0DrXDRJ%2Futp-6b20bb76fefb77320e71.jpg?alt=media)

**Figure6-24 Image collection result**

(5) Add **calibration of calibration board** tool in the solution process

Drag the **CalibBoard Calib** tool from the **Calibration** sub toolbox to the process editing area and connect it to **0 Image Source1** , as shown in Figure 6-25.

**Figure6-25 Process**

Note: The calibration of the calibration board is used to obtain the calibration point, and provide the pixel coordinates of the calibration point for N-point calibration.

(6) Add **N-point Calibration** in the solution process. Drag the **N-point Calibration** tool from the **Calibration** sub toolbox to the process editing area and connect it to **2 CalibBoard Calib1** . After **3N-point Calibration1** is connected to **2**

**CalibBoard Calib1** , click the " ( **Once)** " button. In the image display area, the nine calibration points and its calibration sequence will be automatically displayed, as shown in Figure 6-26.

![Official CR3 training-system figure, source page 175](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNZePOvwPZUC6too52G12%2Futp-a001f771ede6bf552678.jpg?alt=media)

**Figure6-26 Check nine calibration points and calibration sequence**

Basic parameter settings for **3N-point Calibration1** . Double-click **3N-point Calibration** to set basic parameters. Set **Translation Number** in **Basic Params** .

Keep the default parameter 9 and set **Rotation Number** . Click the icon " " to the right of translation number, as shown in Figure 6-27. The **Edit Calibration Point** interface that pops up allows you to edit the calibration points, as shown in Figure 6-28.

**Figure6-27 3 N-Point Calibration**

![Official CR3 training-system figure, source page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmPSkpR4PcIOyq7R224B6%2Futp-1a111b95c71854497755.jpg?alt=media)

![Official CR3 training-system figure, source page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZgVCoH0vV4rtwLT6wm6X%2Futp-1c8c17ad7b2e51026fa8.jpg?alt=media)

**Figure6-28 Edit Calibration Points**

In **Edit Calibration Points** page, exchange Line 3 (ID: 3) and Line 5 (ID: 5)

data, as shown in Figure 6-29.

**Figure6-29 “Edit Calibration Points” after data exchange**

After clicking the " **Refresh** "" **Confirm** "" **Execute** ", you can see that the calibration sequence turns into the font **2** in the image display area, as shown in Figure 6-30.

![Official CR3 training-system figure, source page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH3fUADZt5OHpruHPYXFI%2Futp-92b2b2a4f23d7ef7fab2.jpg?alt=media)

![Official CR3 training-system figure, source page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvu6iL3RRZl3dS0zmkQSz%2Futp-c90bd98253620309409f.jpg?alt=media)

**Figure6-30 Calibration sequence after data exchange**

Open the **DobotStudio Pro** software, connect the robot, and turn on the robot's enable switch. According to the calibration sequence of 9 calibration points, the robot is controlled to reach the first target point, as shown in Figure 6-31. Read the X and Y physical coordinate values of the first the calibration point on **DobotStudio Pro** , as shown in Figure 6-32, and then fill the X and Y physical coordinate values into the corresponding lines of "Edit the calibration point" in **DobotVisionStudio** respectively. Follow the same steps to obtain the physical coordinate values for the remaining 8 Points and fill them in the " **Edit Calibration Points** " table in **DobotVisionStudio** software, as shown in Figure 6-33.

**Figure6-31 First calibration point**

![Official CR3 training-system figure, source page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBY4AILgYgeqoNYikCwYc%2Futp-1e4e70901b0b9f9bbf4b.jpg?alt=media)

![Official CR3 training-system figure, source page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD22afonhL96UdjDM5LV9%2Futp-d03c9c7797e450a4c518.jpg?alt=media)

**Figure6-32 Robot physical coordinates of the first calibration point**

![Official CR3 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhDvuMuDWrdoEyh8LjgWi%2Futp-7cd95e9e3a44a8c39e9e.jpg?alt=media)

![Official CR3 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwmYPRL4J5XySH2SH1pMx%2Futp-89147f65e1432274c342.jpg?alt=media)

**Figure6-33 Physical coordinates of 9 calibration points**

After the operation of editing the calibration point is completed, click **Refresh** and then click **Confirm** to save the physical calibration coordinates, as shown in Figure 6-34.

**Figure6-34 "N point calibration" completed**

In the **Basic Params** interface of **3N-point Calibration1** , click the **Create Calibration File** button to export and store the calibration file to the computer, and named **Calibration file** for future calls, as shown in Figure 6-35.

**Figure6-35 Generate calibration file**

Add **Calibration Transformation** in the flow. After calibration, you can add this tool to verify whether the calibration is accurate.Drag **Calibration Transformation**

![Official CR3 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhChCLWIftTI7tQC70F2E%2Futp-4cd240f5fe7c291acf64.jpg?alt=media)

![Official CR3 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFLimlIMLfeA73ktbA2MS%2Futp-4c12c11a50f1d5ce721f.jpg?alt=media)

in **Calculation** sub toolbox to the process editing area, and connect it with **3N-point Calibration1** ,as shown in Figure 5-36.

**Figure6-36 Scheme process**

Set **4 Calibration Calibration1** basic parameters. In **Basic Params** page, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** , and select the **Calibration file** generated by hand-eye calibration for **Load Calibration File** , as shown in Figure 6-37.

**Figure6-37 Set 4Calibration Transformation1 parameters**

![Official CR3 training-system figure, source page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fox4bycXawVQnpAyuwjNZ%2Futp-2d60c09ffc9497eb43f5.jpg?alt=media)

Click " **(Once)** ", and check whether the 9 calibration data converted from **4 Calibration Transformation1** are consistent with the material coordinates obtained by the robot during N-point calibration, as shown in Figure 6-38. If consistent, the calibration is accurate. Otherwise, you need to re-calibrate。

**Figure6-38 Comparison result**

#### 3.7.2 Import vision program

Open DobotVisionStudio 4.1.2, and select **General Solution** . Select **Open** in the toolbar. Find the phone chip assembly program and click **Open** . The imported vision program is shown in Figure 6-39.

![Official CR3 training-system figure, source page 182](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFxuJSxXIBsNsvkZ3xVoT%2Futp-02fb55ad6a056ea0abcc.jpg?alt=media)

**Figure6-39 Vision program**

#### 3.7.3 Place phone model

Place six chips within the detection vision, as shown in Figure 6-40. For the first time of debugging, ensure that the chips are placed in the same orientation as that inside the phone model in the assembly area.

![Official CR3 training-system figure, source page 183](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZB5gjl7930aqa9qOHqSG%2Futp-d4ab2cb9ed050e4e0bbb.jpg?alt=media)

**Figure6-40 Place chips within the detection view**

Note: The placement of mobile phone chips needs to be based on the actual mobile phone base on site.

#### 3.7.4 Debug parameters

(1) Debug **0 Image Source1** parameters.

Click " **(Once)** ", select **0 Image Source1** and observe whether the image is clear. If the image is not clear or there is no image, you need to reset the parameters according to the method described in 3.7.1. The image collection results are shown in Figure 6-41.

![Official CR3 training-system figure, source page 184](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp2X8LL3vL067LbcbsYrX%2Futp-cfae41ee9d8378f5a4bc.jpg?alt=media)

**Figure6-41 Image acquisition result**

* (2) Debug **2 Fast Match1** parameters.

Click " **(Once)** ", and double-click **2 Fast Match1** with the mouse, and then take away the chips one by one according to the order of chips placed in the groove of the phone model. Observe whether **2 Fast Match1** can accurately identify each type of chip, as shown in Figure 6-42.

**Figure6-42 Detecting template matching**

If it cannot be accurately identified, you need to modify the parameter of **2 Fast Match1** . Set **Basic Params** as shown in Figure 6-43.

![Official CR3 training-system figure, source page 185](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQbx8efTHbpwBNGbnXilW%2Futp-50eb3800c69c00459125.jpg?alt=media)

![Official CR3 training-system figure, source page 185](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoCRAy0p3vVuPiRftBJlX%2Futp-d6abbcdfe80b2bbb09b7.jpg?alt=media)

**Figure6-43 Set 2Fast Match1 parameters**

Click **Feature Model** , and select the first feature model **WIFI** , and then click **Edit Model** , as shown in Figure 6-44. In **ModelSettings** page, click **Current image** , as shown in Figure 6-45. Click **Create Rect Mask** , and drag to generate the rectangular mask to cover material. Configure the parameters in the lower right corner. Set **Scale Mode** and **Thres Mode** according to the actual condition, and click **Build Model** to generate the feature model, as shown in Figure 6-46. Finally, click **Confirm** to save the feature model.

**Figure6-44 Feature model**

![Official CR3 training-system figure, source page 186](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhWWUpmYBGZtsPvXXO2Kq%2Futp-f945727c2875c1ab1e23.jpg?alt=media)

![Official CR3 training-system figure, source page 186](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkU0RXC9vU7CtXh1xxvmY%2Futp-ae35946671454a94a7c1.jpg?alt=media)

**Figure6-45 Model settings**

**Figure6-46 Update feature model**

According to the above method, modify the feature models of CPS chip, electronic compass, light sensor, hexagon and gravity sensor following the method above.

Note: The model sequence must be consistent with Figure 6-41.

* (3) Debug **3 Calibration Transformation1** parameters.

![Official CR3 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxbFrZzeubFjVcs4rqdfo%2Futp-ed2f12c76797b9bfb811.jpg?alt=media)

![Official CR3 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FV2NE52NveHSjzjlBVtHD%2Futp-38e55ac330e8b1e80dac.jpg?alt=media)

Double-click **3 Calibration Transformation1** to set parameters. In **Basic Params** page, set **Coord Point** to **2 High Precision Match1.Match Point\[]** , and **Load Calibration File** select the calibration file generated by hand-eye calibration, as shown in Figure 6-47.

**Figure6-47 Set 3 Calibration Transformation1 parameters**

* (4) Debug **4 Variable Calculation1** parameters.

Double-click **4 Variable Calculation1** , and check whether the **Expression** is

" **-<2 High Precision Match1.MatchBoxAngle>\[0]** ", as shown in Figure 6-48. If not,

modify it to " **-<2 High Precision Match1.MatchBoxAngle>\[0]** ".

![Official CR3 training-system figure, source page 188](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fufc5HBtPhkbQq4Cltj3h%2Futp-4423c54639da2dd0e677.jpg?alt=media)

**Figure6-48 Set 4Variable Calculation1 parameters**

(5) Debug **5 Format1** parameters

Double-click **5 Format1** , and check whether the parameters are **" <2 Fast**

| <p><strong>Match1.MatchModelIndex(%0d)>[0]</strong><br>，<br><strong>&#x3C;3</strong></p>                             | **Calibration**  |
| -------------------------------------------------------------------------------------------------------------------- | ---------------- |
| <p><strong>Transformation1.TransPointX</strong><br><strong>(%1.3f)>[0]</strong><br>，<br><strong>&#x3C;3</strong></p> | **Calibration**  |
| <p><strong>Transformation1.TransPointY(%1.3f)>[0]</strong><br>，<br><strong>&#x3C;4</strong></p>                      | **Variable**     |
| <p><strong>Calculation1.var0(%1.3f)>[0]</strong>"<br>,as shown in Figure 6-49. If not,</p>                           | modify it as the |

figure。

![Official CR3 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAHGmztVXEz9oCbnMPmkX%2Futp-0aae75b060e7b84761a6.jpg?alt=media)

![Official CR3 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHVaikMslpFcsMATzZjeQ%2Futp-64cca612043679f30107.jpg?alt=media)

**Figure6-49 Set 5Format1 parameters**

(6) Debug **Communication Management** parameters

Click " " in the toolbar to enter **Communication Management** page. Check whether there is created **TCP Server** , as shown in Figure 7-50. If not, you need to

re-create one, as described below. Click " " beside **Device List** . Set **Protocol Type** to **TCP Server** ; **Load IP** to **192.168.5.101** , and **Local Port** to **4001** ,then click **Create** . Switch on **1 TCP Server,** as shown in Figure 6-51.

**Figure6-50 “Communication Management”** parameter settings

![Official CR3 training-system figure, source page 190](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8Db7s6WJDVOGq5FiHssb%2Futp-2d0436a5776cbb029cd0.jpg?alt=media)

**Figure6-51** Creating **“TCP Server”**

* (7) Debug **6 Send Data1** parameters

Double-click **6 Send Data1** , and check whether the parameters are shown as

Figure 6-52. If not, modify as the figure. Set **Output To Communication Device** ,

**Communication Device** to **1 TCP Server** , **SendData1** to **5 Format.format\_out\[].**

**Figure6-52 Set "6 Send Data1 parameters"**

* (7) Global trigger settings

![Official CR3 training-system figure, source page 191](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQT3h4GOVZQYVKADNyMOM%2Futp-7368b49d504c69b915f9.jpg?alt=media)

![Official CR3 training-system figure, source page 191](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsllCjqdC9TyEMbvmZnc5%2Futp-5c313587d87137577f89.jpg?alt=media)

Click " " in the toolbar to enter **Global Trigger** page. In **String Trigger** page, check whether the string trigger setting is shown as Figure 6-53. Set **String** to blank, **Mode** to **Mismatched** , and **Trigger Configuration** to **All Pross.**

**Figure6-53 Set global trigger parameters**

#### 3.7.5 Save program

Click " " in the toolbar to save the program. If you need to save the program elsewhere on your local computer, click **File** > **Save as** , select the saving path and enter the name of the project.

#### 3.8 Robot Program Debugging

#### 3.8.1 Install the coaxial sucker tool

* (1) Hand tighten and remove the calibration needle, as shown in Figure 6-54.

![Official CR3 training-system figure, source page 192](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F061fPB1WZFy6feOaPFyq%2Futp-3d3e73132603ff765952.jpg?alt=media)

**Figure6-54 Remove the calibration needle**

* (2) Then twist the sucker to the end of the robot, as shown in Figure 6-54.

**Figure6-55 Installing sucker**

#### 3.8.2 Place the phone model and chip

Place the phone model on the phone model board, as shown in Figure 6-56.

![Official CR3 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtL20UGhjXziKvy9o3mAN%2Futp-8ccf3d6509d107f607f1.jpg?alt=media)

![Official CR3 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQyjRfjUxNUnK1b6R428j%2Futp-c1d1abfcc1f2c4e72ebc.jpg?alt=media)

**Figure6-56 Place phone model**

Place six chips on the standard visual loading board, as shown in Figure 6-57.

**Figure6-57 Place chips within the detection view**

#### 3.8.3 Import program

(1) Open **DobotStudio Pro** and enter script page. Click **File** > **Import project** ,

as shown in Figure 6-58.

![Official CR3 training-system figure, source page 194](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKZ21mvYLvbhFS3iDaJsp%2Futp-0d5c8254d3dfd6235259.jpg?alt=media)

![Official CR3 training-system figure, source page 194](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdSGo7QfNXNHSMpn3dlC3%2Futp-4b590299ed51f159d1c7.jpg?alt=media)

**Figure6-58 Import project**

(2) Select **CR3Mobile Phone Chip Sorting** folder, and click **Open** , as shown in Figure 6-59. Now the phone chip assembly program has been imported into DobotStudio Pro.

**Figure6-59 Import path**

#### 3.8.4 Debug points

(1) Safe point P1

Move the robot between the conveyor belt and the storage area through hand-held teaching or inching control methods, as shown in Figure 6-60. Click **Points** in the right-side menu of DobotStudio Pro. Select **P1** and click **Cover** , as shown in Figure 6-61. Then click **OK** in the pop-up **Tips** window.

![Official CR3 training-system figure, source page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU2Julfe7SMZk3Zko3WtG%2Futp-702015fd610950780adb.png?alt=media)

**Figure6-60 P1** point

**Figure6-61 Point P1**

(2) The placement point of the first chip **P2** Place the first chip (WIFI chip) on the phone model, and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the point P1 to the top of the first chip on the phone model, This is shown in Figure 6-62.

![Official CR3 training-system figure, source page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKexS1y4VeeQtjzaba3AL%2Futp-7866dcf15e34723bd3cc.jpg?alt=media)

![Official CR3 training-system figure, source page 196](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpJon6AAG3EPLRj5dCGzx%2Futp-89c17db5985baa625a98.jpg?alt=media)

**Figure6-62 Place the WIF chip**

Adjust the Z-direction so that the end of the robot moves down and touches the first chip, then open the **IO** control panel and open the **DO\_09** signal switch to let the robot absorb the chip, as shown in Figure 6-63.

**Figure6-63 Sucking WIFI chip**

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the WIFI chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 6-64. Then select **P2** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 6-65.

![Official CR3 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlJMhnIzhzAdJV71BamQg%2Futp-1352085c139dbf47b66d.jpg?alt=media)

![Official CR3 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7zt5cVz4FAoQSJeUsipg%2Futp-5d4cda359d7bc3f9205d.jpg?alt=media)

**Figure6-64 WIFI chip assembly point P3**

**Figure6-65 Update P3**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, let the end of the robot release the WIFI chip and close the sucker, and check whether the chip can be accurately placed in the groove of the phone model. If not, it needs to be adjusted again.

* (3) The placement point of the second chip **P3**

Place the second chip (GPS chip) on the phone model, and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves

![Official CR3 training-system figure, source page 198](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGShqnsnrbcws2Q4YYDPD%2Futp-ae3ecc58810e74370de3.jpg?alt=media)

![Official CR3 training-system figure, source page 198](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FndqXiovAJmImSbk8Bori%2Futp-804723eb1bd256dd85a2.jpg?alt=media)

from the point P1 to the top of the second chip on the phone model, This is shown in Figure 6-66.

**Figure6-66** Placing **GPS** chip

Adjust the Z-direction so that the end of the robot moves downwards and touches the second chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the GPS chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 6-67. Then select **P3** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 6-68.

**Figure6-67 GPS chip assembly point P3**

![Official CR3 training-system figure, source page 199](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrLBoq14WjBRgmKS1Flqx%2Futp-bf83facafd2c713afbb8.jpg?alt=media)

![Official CR3 training-system figure, source page 199](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8sC2Q87J0fYIxvdHZO6T%2Futp-6e84779fed236a1531de.jpg?alt=media)

**Figure6-68 Update P3**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the GPS chip is placed into the groove accurately. If not, you need to re-debug the point.

* (4) The placement point of the third chip **P4**

Place the third chip (Electronic compass chip) on the phone model, and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the P1 point to the top of the third chip on the phone model, This is shown in Figure 6-69.

![Official CR3 training-system figure, source page 200](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPn9OyDEB2WCnirOnsmAw%2Futp-6e1efb76386e679cc579.jpg?alt=media)

**Figure6-69 Place the Electronic compass chip**

Adjust the Z-direction so that the end of the robot moves downwards and touches the third chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the electronic compass chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 6-70. Then select **P4** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 6-71.

**Figure6-70 Electronic compass chip placement point P4**

![Official CR3 training-system figure, source page 201](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxWaFB7VdJatO0GfKvz5I%2Futp-478d053293d7ee72911e.jpg?alt=media)

![Official CR3 training-system figure, source page 201](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoI05zoS8QEbvsW9PDvr2%2Futp-e3b087200507cc9358ff.jpg?alt=media)

**Figure6-71 Update P3**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the electronic compass chip is placed into the groove accurately. If not, you need to re-debug the point.

* (5) The placement point of the fourth chip **P5**

Place the fourth chip (Light sensor chip) on the phone model, and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the P1 point to the top of the fourth chip on the phone model, This is shown in Figure 6-62.

![Official CR3 training-system figure, source page 202](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQB24xJyw2bKRMpn8vSDS%2Futp-193b1b58b549f6999c46.jpg?alt=media)

**Figure6-72 Place the light sensor chip**

Adjust the Z-direction so that the end of the robot moves downwards and touches the fourth chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the light sensor chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 6-73. Then select **P5** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 6-74.

**Figure6-73 Light sensor chip assembly point P5**

![Official CR3 training-system figure, source page 203](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEnBIX9GNRVsU4ES1tm91%2Futp-097c077db7ec852d003e.jpg?alt=media)

![Official CR3 training-system figure, source page 203](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM8dM7Ro3gIbhLxzs5GoF%2Futp-55e19bfe1be1d04ec8fc.jpg?alt=media)

**Figure6-74 Update P5**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the light sensor chip is placed into the groove accurately. If not, you need to re-debug the point.

* (6) The placement point of the fifth chip **P6**

Place the fifth chip (Hexagon chip) on the phone model，and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the P1 point to the top of the fifth chip on the phone model, This is shown in Figure 6-75.

![Official CR3 training-system figure, source page 204](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1Hrz1c7eUtsRgMhvRGlP%2Futp-4346707ad538e2b7c71f.jpg?alt=media)

![Official CR3 training-system figure, source page 204](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZw3x5SjijUru3NZAkvG6%2Futp-19cb1f5ba1869997fc96.jpg?alt=media)

**Figure6-75 Place the hexagon chip**

Adjust the Z-direction so that the end of the robot moves downwards and touches the fifth chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the hexagon chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 6-76. Then select **P6** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 6-77.

**Figure6-76 Hexagon chip assembly point P6**

![Official CR3 training-system figure, source page 205](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FECEm1nKUPe8RgikXaASI%2Futp-c9879f617edc5799d9f0.jpg?alt=media)

**Figure6-77 Update P6**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the hexagon chip is placed into the groove accurately. If not, you need to re-debug the point.

* (7) The placement point of the sixth chip **P7**

Place the sixth chip (Gravity sensor chip) on the phone model and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the P1 point to the top of the sixth chip on the phone model, This is shown in Figure 6-78.

![Official CR3 training-system figure, source page 206](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbmPNL0aWYt2FXUxJCTTR%2Futp-61d131cb96e80f2a00f5.jpg?alt=media)

**Figure6-78 Place the gravity sensor chip**

Adjust the Z-direction so that the end of the robot moves downwards and touches the sixth chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the gravity sensor chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 6-79. Then select **P7** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 6-80.

**Figure6-79 Gravity sensor chip assembly point P7**

![Official CR3 training-system figure, source page 207](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMjio5cCAsVd9jrq0oJx4%2Futp-9422b14f4b3e86b40e2d.jpg?alt=media)

![Official CR3 training-system figure, source page 207](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4X3qTmf4xfXCkVP3UK7i%2Futp-35c30e2aa2d8845dc9a0.jpg?alt=media)

**Figure6-80 Update P7**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 sixth set **DO\_10** to **OFF** and observe whether the gravity sensor chip is placed into the groove accurately. If not, you need to re-debug the point.

#### 3.8.5 Set communication

Set the IP address of the robot program to the IP address of the computer ( **192.168.5.101** ) and the port number to **4001** . Ensure that the IP address and port number of the TCP server in the robot program are consistent with the local IP address and port number in the visual communication Settings, as shown in Figure 6-81.

**Figure6-81 Set communication**

![Official CR3 training-system figure, source page 208](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVMSzSsktB9LX4voWVaXJ%2Futp-8b231b6072e50305f853.jpg?alt=media)

#### 3.8.6 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 6-82.

**Figure6-82 Save program**

Note: " " is for saving the program to the robot controller. If you want to save the

modified program to the local computer, you need to use " ".

#### 3.8.7 Run program

Click the " " button in DobotStudio Pro software to run the robot program. After the robot receives the coordinates of the chip sent by vision, it sips the chip from the standard visual loading board and installs it in a groove in the phone model. The mobile phone after assembly is shown in Figure 6-83.

![Official CR3 training-system figure, source page 209](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzCAmzXeXRJ3uPofn1E1f%2Futp-a9e7688f5ad152563d1c.png?alt=media)

**Figure6-83 Phone after assembly**

#### 3.8.8 Export program

Click **File** > **Export project** , and select the path where the program is stored, then, in the dialog box that pops up, name the program.

Note: **Export project** is to export the program to your local computer for backup.

**4. Program Description**

#### 4.1 Vision program description

The visual program is shown in Figure 6-84. **0 Image Source1** is mainly used for image acquisition. When the system is running, the camera takes pictures of the chip immediately after the vision program receives the **ok** trigger signal sent by the robot. The chip is positioned through **2 Fast Match1** to obtain the image coordinates and matching angles of the chip. Then use **3 Calibration Transformation1** to convert the image coordinates, which are obtained from **2 Fast Match1** , into actual physical coordinates. Then transform and correct the matching angle through **4 Variable Calculation1** . In **5 Format1** , summarize the template model, X/Y physical coordinates, matching angles and other information corresponding to the chip, and then use **6 Send Data1** to send these information to the robot。

![Official CR3 training-system figure, source page 210](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHK75j6t1iLIk3OqaxCBC%2Futp-5618c8516d6cee047688.jpg?alt=media)

**Figure6-84 Vision program**

#### 4.2 Robot program description

#### 4.2.1 src0.lua

The relevant variables for defining the robot program are shown in Figure 6-85。

**Figure6-85 Define the relevant variables**

Define TCP data transfer function as shown in Figure 6-86. The robot sends the signal **ok** to the vision, which is triggered by the photo, and then receives the data sent by the vision.

![Official CR3 training-system figure, source page 211](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwgBDUOCmzHZVyt2IXoUy%2Futp-b823ed7d04b79ba8737c.jpg?alt=media)

**Figure6-86 Data transfer program**

The function of defining the robot to absorb the chip at the calibration point is shown in Figure 6-87. The robot absorbs the chip in the standard vision loading board according to the coordinate information sent by the vision.

**Figure6-87 Robot feeding program**

The program of communication is shown in Figure 6-88, which is mainly to

create TCP client and establish a connection with TCP server (visual).

**Figure6-88 The program of communication**

![Official CR3 training-system figure, source page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj98pO0R9hiyYdakhgq3n%2Futp-b0817af7f296bd7b8eea.jpg?alt=media)

![Official CR3 training-system figure, source page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnTLmfdxH2SfAR4vmzctR%2Futp-e14d735741632903e319.jpg?alt=media)

The relevant IO output was initialized and the robot moved to the Safe point P1 point, as shown in Figure6-89.

**Figure6-89 Procedure of Reset outlet**

Figure 6-90 and Figure 6-91 shows the program for the robot to assemble the chip. The program loops 6 times to let the robot obtain the coordinate information of the chip sent by vision, and absorb the 6 chips in turn, then assemble them into the groove corresponding to the mobile phone model, and finally return to the Safe point P1.

**Figure6-90 Robot placement program (1)**

![Official CR3 training-system figure, source page 213](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkknBVUAbpghkuSfZRuw8%2Futp-510d707b03e64a8d404f.jpg?alt=media)

**Figure6-91 Robot placement program (2)**

#### 4.2.2 global.lua

The function defining the string segmentation is shown in Figure 6-92. This

function is used to process the data sent by the visual side.

**Figure6-92 Defines a function to split strings**

![Official CR3 training-system figure, source page 214](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUeY2lHGmR0Rj66pHwCNF%2Futp-8043cb3b38dc41e356a1.jpg?alt=media)

![Official CR3 training-system figure, source page 214](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqcJA7Q3Th2vyaVrzS6Lw%2Futp-2d53f13b285afd7326ea.jpg?alt=media)

## Official source and related installation guides

The complete English source is in the [official DOBOT Universal Training Platform operation-instruction archive](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260722/1770703893557_Collaborative%20Robot%20Universal%20Training%20Platform%20Operation%20Instruction-EN.rar). Select file `04-Collaborative Robot Universal Training Platform（CR3_include PLC）_20260211_en.pdf`. The archive also contains the platform installation, emergency-stop wiring, conveyor, and PLC-upgrade guides.
