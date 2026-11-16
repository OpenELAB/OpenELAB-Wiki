# DOBOT CR3 Universal Training Platform Operation Instruction - Without PLC

## DOBOT Collaborative Robot Universal Training Platform - Without PLC System Module

{% embed url="https://openelab.io/products/dobot-cobot-universal-training-platform?variant=46636171395270" %}

**Applies to:** CR3 training system without the PLC system module. Official source issue V1.0 (2023-06-02). The robot is purchased separately. Confirm the actual robot and PLC configuration before following wiring or software steps.

**Copyright © yuejiang Science and Technology Co., LTD 2022. All Rights Reserved. All rights reserved.** Without the written permission of the company, any unit or individual shall not extract or copy part or all of the content of this document without authorization, and shall not be transmitted in any form.

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

![Official CR3 training-system figure, source page 14](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHCMA1WjBAQsIUFRxrNKu%2Futp-4cd273c929a828b72fb0.jpg?alt=media)

### 3. Hardware Introduction

#### 3.1 Hardware layout of CR3 general training system

The size of CR3 general training system is 900×600 mm. The installation position of each part is shown in Figure 1-2.

**Figure 1-2 Hardware layout of CR3 general training platform**

#### 3.2 CR3 six-axis cooperative robot

CR3 six-axis cooperative robot is composed of the robot body (Figure 1-3) and the robot the controller (Figure 1-4, generally placed in the interior of the workbench). The robot body can move freely in its working space and complete the grasping or processing of parts with different posture.

![Official CR3 training-system figure, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4KjtwdNijCv1egqhM8zs%2Futp-ed8899cbc427d231d574.jpg?alt=media)

**Figure 1-3 CR3 collaborative robot**

**Figure 1-4 Robot the controller**

**Table 1-2 Interface function definition of robot the controller**

| **No.** | **Description**                                                                                                               |
| ------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1       | <p>USB interface<br>For connecting to WiFi module</p>                                                                         |
| 2       | <p>SmartPendant and emergency stop switch interface<br>For connecting to SmartPendant (optional) or emergency stop switch</p> |
|         | LAN Interface (Default Address: 192.168.5.1)                                                                                  |
| 3       | <p>For connecting to PC (Used for debugging), or other external network equipment of<br>TCP/IP orModbus TCP protocol</p>      |
| 4       | <p>General I/O interface<br>See 6.1.2 General I/O interface panel</p>                                                         |

![Official CR3 training-system figure, source page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FU3EKT62uiFA9avRYEce3%2Futp-43e55cc210ed7718b06a.png?alt=media)

![Official CR3 training-system figure, source page 16](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2BeFDom1ijN3jm5brzAa%2Futp-d8ca2312a11dcac1c298.jpg?alt=media)

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

![Official CR3 training-system figure, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8JK4tbiakKRGE9ZoaKhj%2Futp-f48c70781a30e172c1f4.jpg?alt=media)

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

![Official CR3 training-system figure, source page 19](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FP8gXbIHaDdlqIj71vqpm%2Futp-37a6bea394bf0c417309.jpg?alt=media)

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

![Official CR3 training-system figure, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdZFtOSQgAGgi2JkXVg8v%2Futp-24aea1761ca6a0efb662.png?alt=media)

Joint coordinate system is based on the movement joint for reference to determine the coordinate system. All joints are rotary joints. As shown in Figure 1-9.

**Figure 1-9 Joint coordinate system**

(2) The base coordinate system

The base coordinate is a coordinate system determined by referring to the base of the robotic arm, as shown in Figure 1-10. Among them, RxB, RyB, and RzB are the angles at which the tool center point TCP rotates around the X, Y, and Z axes of the default base coordinate system, respectively.

**Figure 1-10 Base coordinate system**

(3) The tool coordinate system

The tool coordinate system is a coordinate system that defines the position and posture of the Tool Center Point (TCP), and its origin and direction are constantly

![Official CR3 training-system figure, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8KWrqQjKHOQlX0RcamKE%2Futp-5230212b08fc490e0115.jpg?alt=media)

![Official CR3 training-system figure, source page 21](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9DjwtrBK2Av1iawM45Lz%2Futp-8bad79a63ddd18eaa16e.jpg?alt=media)

changing with the position and angle of the end work piece. Current system supports 10 tool coordinate system, among them, the tool coordinate system 0 indicates the default tool, located at the end of the robot, don't use tools and can not be changed. The default coordinate system is shown in Figure 1-11.

**Figure 1-11 Tool coordinate system**

(4) The user coordinate system

User coordinate system is a user-defined table or work coordinate system, its origin and the direction of each axis can be determined according to the actual needs, which can be convenient to measure the position of each point in the working interval and arrange tasks, the default user coordinate system is shown in Figure 1-12.

**Figure 1-12 User coordinate system**

3.2.4 Controller I/O interface specifications

![Official CR3 training-system figure, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FreBhKqvU5WSoPNZ1id7Z%2Futp-66ae944b4d998f0b9731.jpg?alt=media)

![Official CR3 training-system figure, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FI8UGlk7unR89LngjQ0Ki%2Futp-5b7b7708741b549d95a6.jpg?alt=media)

The controller cabinet of the CR3 robot contains an I/O terminal board to connect external equipment, such as air pump, PLC, conveyor belt, etc. The terminal board has 32 digital inputs, 16 digital outputs, 2 analog outputs and 2 analog inputs.

**Figure 1- 13 Control cabinet I/O port**

The communication between the robot of the CR3 general training system and external sensors and conveyor belt equipment is through IO connection, and the IO communication connection between the control cabinet and external equipment is shown in Figure 1-14.

| **Pin** | **In(DI)** | **Description**                                           | **Pin** | **Out(DO)** |
| ------- | ---------- | --------------------------------------------------------- | ------- | ----------- |
| DI1     | R1\_IN01   | Start                                                     | I/O17   | R1\_OUT01   |
| DI2     | R1\_IN02   | Stop                                                      | I/O18   | R1\_OUT02   |
| DI3     | R1\_IN03   | Reset                                                     | I/O19   | R1\_OUT03   |
| DI4     | R1\_IN04   | /                                                         | I/O20   | R1\_OUT04   |
| DI5     | R1\_IN05   | /                                                         | I/O21   | R1\_OUT05   |
| DI6     | R1\_IN06   | /                                                         | I/O22   | R1\_OUT06   |
| DI7     | R1\_IN07   | /                                                         | I/O23   | R1\_OUT07   |
| DI8     | R1\_IN08   | /                                                         | I/O24   | R1\_OUT08   |
| DI9     | R1\_IN09   | <p>The Stock bin has material<br>inspection knowledge</p> | I/O25   | R1\_OUT09   |
| DI10    | R1\_IN10   | In-place detection                                        | I/O26   | R1\_OUT10   |
| DI11    | R1\_IN11   | /                                                         | I/O27   | R1\_OUT11   |
| DI12    | R1\_IN12   | /                                                         | I/O28   | R1\_OUT12   |
| DI13    | R1\_IN13   | /                                                         | I/O29   | R1\_OUT13   |
| DI14    | R1\_IN14   | /                                                         | I/O30   | R1\_OUT14   |
| DI15    | R1\_IN15   | /                                                         | I/O31   | R1\_OUT15   |
| DI16    | R1\_IN16   | /                                                         | I/O32   | R1\_OUT16   |

**Figure 1- 14 IO comparison of control cabinet wiring**

Open DobotStudio Pro software, you can set the state of each IO port of the robot. Click the **I/O** into the IO monitor interface, as shown in Figure 1-15, you can view **Digital input** and setting up the **Digital output** value in the interface. For example, when the **DO\_02** switch is turned on, the conveyor moves forward.

**Figure 1-15 "I/O" monitoring interface**

#### 3.3 Air pump box

Mini air pump box is adopted for CR3 general training system, as shown in Figure 1-16. Compared with the traditional air supply method with large noise, large volume and high cost, this air pump box provides users with a more convenient and simple way of air supply and use. Pump box can provide - 70 \~ 110 kpa pressure range, the appearance design is exquisite, facilitate can directly by the I/O control interface and robot adapter, plug and play, and can be applied to daily most sucker and flexible grip application scenario.

![Official CR3 training-system figure, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F93iscZ1lE7di6G8SmdEr%2Futp-41a318ee85129767cc7e.jpg?alt=media)

![Official CR3 training-system figure, source page 25](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuJXCRzyjk0BGTanQmDij%2Futp-1b68b8ef5481f3c687a9.jpg?alt=media)

**Figure 1-16 Air pump case**

#### 3.4 Visual unit

Visual unit hardware consists of camera, lens, the light source (a white ring light source, two white strip light and two blue bar light), dual channel light controller, CCD controller, etc, as shown in Figure 1-17. Which is 5 million pixels color camera, camera lens is the prime lens focal length of 12 mm, ring light source of the figure is white light source. The switching position of light source of CR3 general training system is shown in Figure 1-18. When using it, the USB cable of the visual unit should be connected to the computer, as shown in Figure 1-19.

**Figure 1-17 Connect camera cables**

**Figure 1-18 Light source of the power switch**

![Official CR3 training-system figure, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCEzoV1rfPsaJ5JrffVxm%2Futp-1e231d5138ac587f7f63.png?alt=media)

![Official CR3 training-system figure, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzqYVyFXz34pNzIgH8gHE%2Futp-d4c363c10a4e17cb08ec.png?alt=media)

**Figure 1-19 Links the visual unit**

#### 3.5 Trichromatic lamp and the control button

Trichromatic lamp mainly through the transformation of different colors, to display the current operation state, trichromatic lamp as shown in Figure 1-20.

**Figure 1-20 Tricolor lamp**

Including control button **Start** and **Stop** and **Reset** and **Emergency Stop** , a total of four buttons, the former three buttons can be used to set the running status of equipment, Stop control of the power machine and the robot, such as robot ontology cannot access to electricity, could be **Emergency Stop** button to be taken. Control button as shown in Figure 1-21.

![Official CR3 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHfsNmVzrfx2xI3RDcVmx%2Futp-4bb5879fb65e86f779b5.jpg?alt=media)

![Official CR3 training-system figure, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9RLS7BKCdfhgql2654Dt%2Futp-524f808310c2b266dbbd.jpg?alt=media)

**Figure 1-21 Control button**

#### 3.6 Conveyor

Feeding conveyor belt as shown in Figure 1-22. It is mainly used to push the material from the silo to the belt line to realize the transportation of the material between different locations. Built-in stepper motor on the conveyor belt, which can accurately control the material of the driving distance and speed. Driven by DC gear motor, the speed of the belt line can be controlled to adapt to the transportation needs of different materials. In addition, the conveyor is equipped with multiple correlation sensor and encoder, can accurately detect the location of the material on the belt line, and realize the robot space dynamic follow and grab for the material, improve the transport efficiency and accuracy of the material.

**Figure 1-22 Conveyor belt**

#### 3.7 Other accessories

#### 3.7.1 Quick change plate unit

Training standard four quick change board module, include: trackpad, mobile phone standard visual cargo version model artifacts slide plate, round/rectangle

![Official CR3 training-system figure, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfB3KtSFN6k6SKWRkU9XD%2Futp-56a0b90fab275c2d9114.jpg?alt=media)

![Official CR3 training-system figure, source page 28](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSZe2OCXDIjY7ouTCVJkj%2Futp-408e5a085402826a64bf.jpg?alt=media)

**CR3 General Training System Operation Instruction**

workpiece slide plate. With the robot execution unit and vision unit, the visual recognition, detection and positioning of the experimental object can be completed, and the process applications such as object tracking, positioning and grasping, palletizing and assembly can be realized.

**Figure 1-23 Quick change plate unit**

#### 3.7.2 Toolbox unit

Know about the objects in the toolbox, including chip model, mobile phone

model, materials and tools for assembling, as shown in Figure 1-24.

**Figure 1-24 Toolbox unit inside24**

### 4. Software Installation

#### 4.1 Install the robot control software

* (1) Enter Dobot official website

![Official CR3 training-system figure, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FY2jCdcOgwISbN2AUTohV%2Futp-479cc39ad28ea1f140b1.jpg?alt=media)

![Official CR3 training-system figure, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5f2AQg3sftTnkY3sEYhb%2Futp-a97fab19d62e8f387b7c.jpg?alt=media)

Search https://www.dobot-robots.com/ in the browser to enter Dobot website. Click **User** to enter **USER LOGIN** page, as shown in Figure1-25. Enter your email and password to enter **USER CENTER** page. (You need to register before login.)

**Figure 1-25 User Login**

(2)Download the latest robot control software.

①Click **Download Center** in **USER CENTER** page, as shown in Figure1-26.

**Figure 1-26 User Center**

② Enter the **DOWNLOAD CENTER** interface, and click **Control Software;**

locate the **DobotStudio Pro v2.6.1** software, and click " " on the right side, and then download the robot software, as shown in Figure 1-27.

![Official CR3 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZKHzfyB47wcOswBHIwh9%2Futp-b9cede2b4fd2d9c598b0.jpg?alt=media)

![Official CR3 training-system figure, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu9BhrQ9xp6c2XRodGijg%2Futp-3f241dae65ac30f7a502.jpg?alt=media)

**Figure 1-27 Download software installation package**

* (3) Enter installation guide interface

Double-click the downloaded software, and an installation guide interface will

pop up, as shown in Figure1-28.

**Figure 1-28 Installation instructions**

(4) Select the installation path

Click **Next** to enter the software installation interface, and click **Custom options**

and **Browse** , then select the installation directory, and click **Install Now** , as shown in

Figure 1-29.

![Official CR3 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKwc0lSN0FamLMfqykjrf%2Futp-96530478301131c4803e.jpg?alt=media)

![Official CR3 training-system figure, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC8uH0VxNYoG11PvVNY70%2Futp-629b322a80b30c1c6c05.jpg?alt=media)

**Figure 1-29 Select the installation path**

* (5) Start installation

Click **Install Now** to start **DobotStudio ProV2.6.1** , as shown in Figure1-30.

**Figure 1-30 Installing the software**

* (6) Finish Installation

After installation, click **Experience Now** to enter the software, as shown in

Figure1-31.

![Official CR3 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSlvKlNdR6YtxLWu0Vx2N%2Futp-2b983c22dd25af80cc2c.jpg?alt=media)

![Official CR3 training-system figure, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUBIznfz0YTK3IeOtm4AN%2Futp-51f69d10eeedaca36296.jpg?alt=media)

**Figure 1-31 Installation complete**

* (7) Know about the software interface

The main interface includes four parts, as shown in Figure1-32:

**Figure 1-32 Main interface**

 Area 1:Top Toolbar. It includes menu bar, the main interface, connection panel, alarm log button, enabling button, jog setting button, emergency stop button etc.

 Area 2:Recent Projects.Display the recent projects,which you can click to open quickly.

![Official CR3 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrycBn453WFyWykc4Rr4B%2Futp-9efc8f7dd580896f420f.jpg?alt=media)

![Official CR3 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FX68ZsoDyuTXhg9iZt69R%2Futp-7381f078c72c3de40e0d.jpg?alt=media)

![Official CR3 training-system figure, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqCvLYVXMt0YAeFFAVyBV%2Futp-772fcec3365154b20cdb.jpg?alt=media)

**CR3 General Training System Operation Instruction**

 Area 3:Major Functions.It includes DobotBlockly, Script, Setting and Process.

 Area 4:Tools Panel.Click the icon on the right toolbar to display or hide the corresponding panels,including Control, I/O, Modbus, Global Variable and Dobot+. The control panel is displayed by default after DobotStudio Pro is connected to the robot successfully.

Note: For specific functions of each tool, see its corresponding user guide.

#### 4.2 Install vision software

(1) Enter Dobot official website

Search https://www.dobot-robots.com/ in the browser to enter Dobot official website. Click **User** to enter **USER LOGIN** page. Enter your email and password to enter **USER CENTER** page as shown in Figure1-33. (You need to register before

login.)

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

## Chapter 2 Tricolor lights

### 1. Introduction

This chapter will learn how to write programs through DobotStudio Pro to control the turning on and off of the tricolor light (as shown in Figure 2-1) and the buzzer on and off of the CR3 general training system.

**Figure 2-1 Tricolor alarm lamp**

In this chapter, the control tasks of tricolor lights and buzzers are as follows:

(1) Press the **Star** button (as shown in Figure 2-2) and the green light in the tricolor light is on.

(2) Press the **Stop** button again, and the green light in the tricolor light is off → the red light is on.

(3) Press the **Reset** button again, the red light in the tricolor light goes off →the yellow light goes on →after 2 seconds, the yellow light goes off and the green light goes on →after 1 seconds, the green light goes off and the yellow light goes on → after 1 second, the yellow light goes off and the red light goes on →after 1 second, the red, green, yellow light go on and the buzzer goes on at the same time →after 2 seconds, all the lights in the tricolor go off and the buzzer stops.

![Official CR3 training-system figure, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTw3tqf0Sk29alhbpflOu%2Futp-2bab06b63e5409cb6a20.jpg?alt=media)

**Figure 2-2 CR3 control button**

### 2. IO Configuration Definition

The IO configuration of tricolor lights, buzzers and control buttons is shown in

Table 2-1.

Table 2-1 Three-color alarm lamp and control button IO configuration

| **Input** | **Description** | **Output** | **Description**                                          |
| --------- | --------------- | ---------- | -------------------------------------------------------- |
| DI1       | Start button    | DO3        | <p>Light the green light of the<br>tricolour light.</p>  |
| DI2       | Stop button     | DO4        | <p>Light the yellow light of the<br>tricolour light.</p> |
| DI3       | Reset button    | DO5        | <p>Light the red light of the<br>tricolour light.</p>    |
| DI4       | /               | DO6        | Buzzer                                                   |

### 3. Program Debugging

#### 3.1 Power on the CR3 general training system

Connect the power plug of CR3 general training system to the power supply, and then turn on the power switch of CR3 general training system, as shown in Figure 2-3.

![Official CR3 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSmxIlftx81w8WOrCh5qm%2Futp-11d72c91f72ff601715d.jpg?alt=media)

![Official CR3 training-system figure, source page 41](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVv3xfRTGdCXB1gtLZ6FI%2Futp-44489226e5513b810567.jpg?alt=media)

**Figure 2-3 CR3 general training system power switch**

#### 3.2 Connecting robot

* (1) Power on the robot.

Check whether the power switch of the robot controller cabinet (Figure 2-4) and the Robot body switch (Figure 2-5) are turned on. If not, all switches need to be turned on.

**Figure 2-4 Robot the controller power switch**

**Figure 2-5 Robot switch**

* (2) Connect the robot to the computer.

Connect one end of the network cable to the LAN interface of the controller, and the other end to the computer.

* (3) Change the IP address of the computer.

![Official CR3 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLkSy7P8M2YUuhLKQtTIk%2Futp-b3dd68c7d2eb7ca565e0.jpg?alt=media)

![Official CR3 training-system figure, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FvqokjyvvIrEtpGM0ye6g%2Futp-ccd9884cde8ec24f3565.jpg?alt=media)

Open your computer's control panel, select **Network and Internet/ Network and Share Center** , and enter the network and share center window. Click **Ethernet** and select **Properties** to enter the ethernet property setting page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to enter the interface of **Internet Protocol version 4 (TCP/IPv4) properties** , and reset the IP address of PC side, as shown in Figure 2-6. The default address of the robot is **192.168.5.1** , and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment with the robot. The subnet mask and default gateway are the same as those of the robot, taking **192.168.5.100** as an example here.

**Figure 2-6 PC IP address Settings**

* (4) DobotStudio Pro connects the robot.

Double-click the **DobotStudio Pro 2.6.1** software icon to open the software. Then select the robot **CR3** you want to connect to in the top toolbar of the DobotStudio Pro interface, and click **Connect** , as shown in Figure 2-7.

![Official CR3 training-system figure, source page 43](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft5P2WygcLRwtOb3LhbOt%2Futp-117c4ca7b1cb1485bc86.png?alt=media)

**Figure 2-7 Connecting robot**

After successful connection, DobotStudio Pro will pop up a prompt message and

the connection state will become **Connected** , as shown in Figure 2-8.

**Figure 2-8 Connected robot**

#### 3.3 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 2-9.

Then click **Confirm modification** , the enable icon becomes " ".

![Official CR3 training-system figure, source page 44](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure 2-9 Set load parameters**

#### 3.4 Importing program

* (1) Open the DobotStudio Pro software, enter the scripting page, and click **File >**
* **Import project** , as shown in Figure 2-10.

**Figure 2-10 Import project**

(2) Select **CR3Project > Tricolor light** folder, and click the **Open** , as shown in

Figure 2-11, then import the tricolor light program into the software.

![Official CR3 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

![Official CR3 training-system figure, source page 45](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

CR3 General Training System Operation Instruction<br>

**Figure 2-11 Import path**

#### 3.5 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 2-12.

**Figure 2-12 Saves the program**

Note: " " is to save the program to the robot controller. If you want to save the

modified program to your local computer, you need to use " ".

![Official CR3 training-system figure, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFQoMXO0eDs5niIgPBCCR%2Futp-4890ba85922c3f270b42.jpg?alt=media)

![Official CR3 training-system figure, source page 46](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYHaoHNf1coL3F5HBU5nH%2Futp-f3cc4aa2c6dd02c3f49a.jpg?alt=media)

#### 3.6 Program operation

Click " " button to observe whether the program is running as follows: (1) Press the **Start** button (as shown in Figure 2-2) and the green light in the tricolour light is on.

(2) Press the **Stop** button again, and the green light in the tricolour light is off → the red light is on.

(3) Press the **Reset** button again, the red light in the tricolour light is off →the yellow light is on →after 2 seconds, the yellow light is off and the green light is on →after 1 second, the green light is off and the yellow light is on →after 1 second, the yellow light is off and the red light is on →after 1 second, the red, green and yellow light are on and the buzzer goes on at the same time→after 2 seconds, all the lights in the tricolour light are off and the buzzer stops.

Note: After the program finishes running, if the program does not exit the running state

automatically, click " " manually.

#### 3.7 Export program

Click **File > Export project** , and select the path to store the program, and then name the program in the pop-up dialog box, as shown in Figure 2-13.

**Figure 2- 13 Export project**

Note: **Export Project** is the process of exporting a program to a local computer for backup.

### 4. Program Description

#### 4.1 Src0.lua

(1) Reset the tricolour light and buzzer, and set the relevant output signal to **0** , as

shown in Figure 2-14.

**Figure 2-14 Reset the output signal**

(2) Wait for the **Start** button to be pressed, and the green light will be on. The

program is shown in Figure 2-15.

![Official CR3 training-system figure, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjNtkpGCgTOJ35e2aXZup%2Futp-a77c08181255358672fe.jpg?alt=media)

![Official CR3 training-system figure, source page 48](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGt0ZXmz5WGx90Sq2OYKD%2Futp-49c9c6380d902bb53a62.jpg?alt=media)

**Figure 2-15 Press the Start button**

(3) Wait for the **Stop** button to be pressed, the green light will be off and the red

light will be on. The program is shown in Figure 2-16.

**Figure 2-16 Press the Stop button**

(4) Wait for the **Reset** button, the red light will go off and the yellow light will go on; after 2 seconds, the yellow light will go off and the green light will go on; after 1 second, the green light will go off and the yellow light will go on; after 1 second, the yellow light will go off and the red light will go on; after 1 second, the red, green, yellow light will go on, and the buzzer will emit sound; 2 seconds later, all the lights in the tricolour light will go off, and the buzzer will stop, as shown in Figure 2-17.

**Figure 2-17 Press the Reset button**

#### 4.2 Global.lua

The input signal detection program is shown in Figure 2-18. The function to be

realized is to detect whether there is an input signal on the relevant IO port.

**Figure 2-18 Input signal detection**

![Official CR3 training-system figure, source page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmdrTkgvp0yfeBHNbGTox%2Futp-fc403687226ac35688ee.jpg?alt=media)

![Official CR3 training-system figure, source page 50](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmkT56Ys8xX48lZmIbBbg%2Futp-cf06901d881b37c8a049.jpg?alt=media)

## Chapter 3 Application of trajectory simulation

### 1. Introduction

Trajectory simulation is based on the point position of hand-held teaching, so

that the end of the robot moves along a specific trajectory,, as shown in Figure 3-1.

**Figure 3-1 Trajectory simulation**

### 2. Hardware Description

#### 2.1 Install the support for the loading plate

Install the supports of the two loading plates on both sides of the conveyor belt

by using hex socket screws, as shown in Figure 3-2.

**Figure 3-2 Install the support for the loading plate**

![Official CR3 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuKlAMXhqZUBCsFv963R6%2Futp-7e7f06aa83f98fd4009a.jpg?alt=media)

![Official CR3 training-system figure, source page 51](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2UhXufpSvPNvL6FndlMO%2Futp-06c00357495957c4c86e.png?alt=media)

#### 2.2 Place trajectory board

Place the trajectory board on the conveyor, as shown in Figure 3-3.

**Figure 3-3 Place trajectory board**

#### 2.3 Install calibration needle

Remove the sucker at the end of the robot, as shown in Figure 3-4.

**Figure 3-4 Remove the end of the sucker**

Then, install the prepared calibration needle onto the end of the robot, as shown in Figure 3-5.

![Official CR3 training-system figure, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIOEIKG3ipTnwASwMB7wt%2Futp-68436c078ad4e91f452e.jpg?alt=media)

![Official CR3 training-system figure, source page 52](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Foz1fQrj3lE4qhQz9CBUH%2Futp-a2c5bdb58db0f2ca8618.jpg?alt=media)

**Figure 3-5 Install calibration needle**

### 3. Program Debugging

#### 3.1 Turn on CR3 general training system power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3 general training system, as shown in Figure 3-6.

**Figure 3-6 CR3 general training system power switch**

#### 3.2 Connecting robot

* (1) Power on the robot.

Check whether the power switch of the robot controller and the robot switch are turned on. If not, all switches need to be turned on, as shown in Figure 3-7.

![Official CR3 training-system figure, source page 53](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUdzFAkMnuAIMcggIG3MD%2Futp-3dae1313a7ae54303788.jpg?alt=media)

![Official CR3 training-system figure, source page 53](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdYXuXhds2VJQa1ytyJ40%2Futp-76fe66931110b0a471b2.jpg?alt=media)

**Figure 3-7 Robot control cabinet**

(2) Connect the robot to the computer.

Connect one end of the network cable to the LAN interface of the robot controller, and the other end to the computer.

* (3) Change the IP address of the computer.

Open your computer's control panel, select **Network and Internet/ Network** and **Share Center** , and enter the network and share center window. Click **Ethernet** and select **Properties** to enter the ethernet property setting page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to enter the interface of **Internet Protocol version 4 (TCP/IPv4) properties** , and reset the IP address of PC side, as shown in Figure 3-8. The default address of the robot is **192.168.5.1** , and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment with the robot. The subnet mask and default gateway are the same as those of the robot, taking **192.168.5.100** as an example here.

![Official CR3 training-system figure, source page 54](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

**Figure 3-8 PC IP address Settings**

* (4) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro v2.6.1** to open the software. Select **CR3** on the

top toolbar of the DobotStudio Pro interface, and click **Connect** , as shown in Figure

3-9.

**Figure 3-9 Connecting robot**

![Official CR3 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft5P2WygcLRwtOb3LhbOt%2Futp-117c4ca7b1cb1485bc86.png?alt=media)

![Official CR3 training-system figure, source page 55](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

After successful connection, DobotStudio Pro Pro interface will pop up a prompt message and the connection status will change to **Connected** , as shown in Figure 3-10.

**Figure 3-10 Connected robot**

#### 3.3 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 3-11.

Then click **Confirm modification** , the enable icon becomes " ".

**Figure 3-11 Set load parameters**

![Official CR3 training-system figure, source page 56](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

#### 3.4 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 3-12.

**Figure 3-12 Global rate Settings**

#### 3.5 Adjust the initial pose of the robot

**(1) Select Setting>Basic .**

(2) Check if the joint coordinate of the robot is as shown in Figure 3-13, and then click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

**Figure 3-13 Adjusting the initial pose of the robot**

![Official CR3 training-system figure, source page 57](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

#### 3.6 Importing program

* (1) Open the DobotStudio Pro software, enter the script programming page, and
* click **File > Import project** , as shown in Figure 3-14.

**Figure 3-14 Import project**

(2) Select the folder **CR3Project> Trajectory Simulation** , and click **Open** , as shown in Figure 3-15, then import the program of trajectory simulation into the software.

**Figure 3-15 Import path**

![Official CR3 training-system figure, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 58](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5pjFMmBfAxlhv3vP9XRR%2Futp-533342d472b143605dea.png?alt=media)

#### 3.7 Debug points

The program of trajectory simulation requires debugging 41 points, including 40 trajectory points and 1 safety point. The point positions of the trajectory board are shown in Figure 3-16.

**Figure 3-16 The point positions of the trajectory board**

(1) Manually drag the robot onto the trajectory board，as shown in Figure. 3-17. On the save point page, overwrite the P1 point, which is the **HOME** point (safe point), as shown in Figure 3-18, and then click **OK** in the pop-up **Tips** window.

![Official CR3 training-system figure, source page 59](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNySViKStswhUf9rJ1UYS%2Futp-68a8fa291eeb8e3c37fc.jpg?alt=media)

**CR3 General Training System Operation Instruction**

**Figure 3-17 Point P1**

**Figure 3-18 Update P1**

(2) By inching control or dragging methods, move the robot to the **gj1** point on the trajectory board, as shown in Figure 3-18, then overwrite P2 point on the point page, as shown in Figure 3-20, and then click **OK** in the pop-up **Tips** window.

![Official CR3 training-system figure, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDTwwFQ6AASwKbDBBl7SH%2Futp-b69dd8892be32def00c4.jpg?alt=media)

![Official CR3 training-system figure, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHquiRNqx368BXCIz3jbn%2Futp-56b086a5af147346d33c.jpg?alt=media)

**Figure 3-19 Point gj1**

**Figure 3-20 Update P2**

(3) By inching control or dragging methods, move the robot to the **gj2** point on the trajectory board, as shown in Figure 3-21; Then overwrite P3 on the point page, as shown in Figure 3-22. Then click **OK** in the pop-up **Tips** window .

![Official CR3 training-system figure, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Febg8nULGcSli2IYxMoDz%2Futp-c4302307b328875af037.png?alt=media)

![Official CR3 training-system figure, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZWPU6kE7LAxHizfghpnR%2Futp-765f03632230e557ddf1.jpg?alt=media)

**CR3 General Training System Operation Instruction**

**Figure 3-21 Point gj2**

**Figure 3-22 Update P3**

(4)Repeat the above steps and complete the remaining 38 points by hand-held teaching according to the points on the trajectory board.

Note: During the calibration, there should be a certain distance between the calibration needle and the Trajectory board, so as to avoid the calibration needle from the Trajectory board.

![Official CR3 training-system figure, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoFdvdlqI4scuT9NBRTC9%2Futp-828bae68270f8c5929e1.png?alt=media)

![Official CR3 training-system figure, source page 62](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQHBPHU3gHh5WRgrMp9HE%2Futp-4734509cce620ed72edf.jpg?alt=media)

#### 3.8 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 3-23.

**Figure 3-23 Save program**

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

![Official CR3 training-system figure, source page 63](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fd0LqRgUVef5SRoHMtJ3k%2Futp-0bc91e813fa4aa8d5094.jpg?alt=media)

### 4. Program Description

Since the path on the trajectory board is made up of graphs with different features, including straight lines, arcs, and circles. Therefore, 4 different motion modes are adopted in the program to design the trajectory motion of the robot. **Go** represents point-to-point motion, **Move** represents linear motion, **Arc** represents circular motion, and **Circle** represents whole circle motion. The trajectory simulation application is shown in Figures 3-24.

**Figure 3-24 Trajectory motion program**

![Official CR3 training-system figure, source page 64](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FaARvv4JJAW2hOIkHpmwZ%2Futp-78ff4c73939c771adab7.jpg?alt=media)

## Chapter 4 The conveyor application

**1. Introduction**

The task to be achieved in this chapter is to control the operation of the device through buttons, at the same time using the light color of tricolor light to reflect the running state of the equipment. Press the **Reset** button, the device is initialized, and the yellow light is on; press the **Start** button, the device runs, and the green light turns on; press the **Stop** button, the equipment stop running, the red light turns on.

After the equipment is running, the circular workpiece in the silo is pushed onto the conveyor belt by the pushing motor, which carries the circular workpiece forward for transmission. When the circular workpiece reaches the grasping point (sensor sensing point), the conveyor belt stops moving, as shown in Figure 4-1, and then the robot moves the circular workpiece to the circular groove of the circular workpiece loading plate in the storage area, as shown in Figure 4-2.

**Figure 4-1 Stock bin**

**Figure 4-2 Storage area**

![Official CR3 training-system figure, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fudn1vVO5cEZhpZzi78bK%2Futp-7e4bc08c9149b8eaed2d.png?alt=media)

![Official CR3 training-system figure, source page 65](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn2Cr9XJlFARKqanbNjjF%2Futp-35ae3445096231e88ed8.jpg?alt=media)

**2. Hardware Description**

#### 2.1 Install coaxial sucker tool

* (1) Remove the calibration needle from the end of the robot, as shown in Figure

4-3.

**Figure 4-3 Remove the calibration needle**

* (2) Install the sucker to the end of the robot, as shown in Figure 4-4.

**Figure 4-4 Mounting the sucker**

![Official CR3 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6vV1Bph0ko6Vb8kwDXOH%2Futp-96cd3accccfb6e62f158.jpg?alt=media)

![Official CR3 training-system figure, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTbv7JTVon7KIbSDHKSUy%2Futp-1347477b4c31405e0d89.jpg?alt=media)

#### 2.1 IO configuration description

The IO configuration of the conveyor belt application is shown in Table 4-1.

**Table 4-1 IO configuration for conveyor belt application**

| **DI** | **Description**                                    | **DO** | **Description**                                          |
| ------ | -------------------------------------------------- | ------ | -------------------------------------------------------- |
| DI1    | Start button                                       | DO1    | Pushing motor is enabled                                 |
| DI2    | Stop button                                        | DO2    | Startconveyorbelt                                        |
| DI3    | Reset button                                       | DO3    | <p>Light the green light of the<br>tricolour light.</p>  |
| DI4    | /                                                  | DO4    | <p>Light the yellow light of the<br>tricolour light.</p> |
| DI5    | /                                                  | DO5    | <p>Light the red light of the tricolour<br>light.</p>    |
| DI6    | /                                                  | DO6    | Buzzer                                                   |
| DI7    | /                                                  | DO7    | /                                                        |
| DI8    | /                                                  | DO8    | <p>Material inspection by<br>photograph</p>              |
| DI9    | <p>Material in the stock bin is<br>detected</p>    | DO9    | Vacuum pumping                                           |
| DI10   | <p>Material on the conveyor<br>beltis detected</p> | DO10   | Vacuum breaking                                          |

**3. Program Debugging**

#### 3.1 Preparation

#### 3.1.1 Turn on the platform power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3

general training system, as shown in Figure 4-5.

**Figure 4-5 CR3 power switch of training platform**

![Official CR3 training-system figure, source page 67](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdYXuXhds2VJQa1ytyJ40%2Futp-76fe66931110b0a471b2.jpg?alt=media)

#### 3.1.2 Turn on the air pump box switch

Turn on the power switch of the air pump box and rotate the control button to

**Auto,** as shown in Figure 4-6.

**Figure 4-6 Pump box**

#### 3.1.3 Prepare Material

Place six circular materials into the material barrel, as shown in Figure 4-7.

**Figure 4-7 Placing workpiece**

#### 3.2 Connect robot

(1) Power on the robot.

![Official CR3 training-system figure, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzFjaVYWzyhPEtjiJk3QP%2Futp-01cbfdd56a2023048af3.jpg?alt=media)

![Official CR3 training-system figure, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJDXLYi6uIiqZV1Hlhqjy%2Futp-0702682a35b18d83511d.jpg?alt=media)

Check whether the power switch of the robot controller and the robot switch are turned on. If not, all switches need to be turned on, as shown in Figure 4-8.

**Figure 4-8 Robot control cabinet**

(2) Connect the robot to the computer.

Connect one end of the network cable to the LAN interface of the robot controller, and the other end to the computer.

* (3) Change the IP address of the computer.

Open your computer's control panel, select **Network and Internet/ Network and Share Center** , and enter the network and share center window. Click **Ethernet** and select **Properties** to enter the ethernet property setting page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to enter the interface of **Internet Protocol version 4 (TCP/IPv4) properties** , and reset the IP address of PC side, as shown in Figure 4-9. The default address of the robot is **192.168.5.1** , and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment with the robot. The subnet mask and default gateway are the same as those of the robot, taking **192.168.5.100** as an example here.

![Official CR3 training-system figure, source page 69](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

**Figure 4-9 PC IP address Settings**

* (4) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro v2.6.1** to open the software. Select **CR3** on the top toolbar, and click **Connect** , as shown in Figure 4-10.

**Figure 4-10 Connecting robot**

After successful connection, DobotStudio Pro Pro interface will pop up a prompt message and the connection status will change to **Connected** , as shown in Figure 4-11.

![Official CR3 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

![Official CR3 training-system figure, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO4i6HsBXGfJE7JdiPcSu%2Futp-51aeb9dae4cd9095b731.png?alt=media)

**Figure 4-11 Connected robot**

#### 3.3 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 4-12.

Then click **Confirm modification** , the enable icon becomes " ".

**Figure 4-12 Set load parameters**

#### 3.4 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 4-13.

![Official CR3 training-system figure, source page 71](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

**Figure 4-13 Global rate setting**

#### 3.5 Adjust the initial pose of the robot

* (1) Select **Setting>Basic** .

(2) Check if the joint coordinate of the robot is as shown in Figure 4-14, and then click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

**Figure 4-14 Adjusting the initial pose of the robot**

**3. 6 Importing programs**

* (1) Open the DobotStudio Pro software, enter the script programming page, and

click **File > Import project** , as shown in Figure 4-15.

![Official CR3 training-system figure, source page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

**Figure 4-15 Import Project**

(2) Select the folder **CR3Project> Trajectory Simulation** , and click **Open** , as shown in Figure 4-16, then import the program of the conveyor belt application into the software.

**Figure 4-16 Import path**

**3. 7 Debug points**

The conveyor belt application includes three major points, and the debugging method is as follows:

![Official CR3 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 73](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FIDq1XtYumCo470rOMTns%2Futp-4c78f87b52ae7c874e57.png?alt=media)

* (1) Safe point P1
  * ① Move the robot between the conveyor belt and the storage area through
* handheld teaching or inching control methods, as shown in Figure 4-17.

**Figure 4-17 Point P1**

* ②Click **Points** in DobotStudio Pro, and select **P1** , then click **Cover** , as shown in

Figure 4-18, and then click **OK** on the **Tips** interface that pops up.

**Figure 4 18 Update P1**

* (2) Pick-up point P2
* ① Make the material reach the pick-up point (sensor sensing point). First click
* the " " button, then manually press the **Reset** button, wait for the yellow light to flashes off, and then press the **Start** control button to run the device. When the

![Official CR3 training-system figure, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwvcpoucfYEWktZiZWs7J%2Futp-8e63c32685c462801b1d.jpg?alt=media)

![Official CR3 training-system figure, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Feek8gzz9zKi6WycSPsVs%2Futp-4658141cfc9fa13f2385.jpg?alt=media)

conveyor belt stops carrying circular workpieces in the picking area, click the

* " " button to stop the program running.

② Move the robot to the circular workpiece in the mode of inching control, and let the sucker gently touch the surface of the circular workpiece, as shown in Figure 4-19.

**Figure 4-19 Positioning to point P2**

③Open the **IO** control panel, then open the **DO\_09** signal switch, let the end of

the robot suck the blocks. As shown in Figure 4-20.

**Figure 4-20 I/O Control panel**

![Official CR3 training-system figure, source page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrQ2V2J4KCjkLpmvubg6d%2Futp-e122060b4f957a6b10e3.jpg?alt=media)

![Official CR3 training-system figure, source page 75](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlJMhnIzhzAdJV71BamQg%2Futp-1352085c139dbf47b66d.jpg?alt=media)

④ Open **Points** , and click **P2** , then click **Cover,** as shown in Figure 4-21, and then click **OK** on the **Tips** interface that pops up.

**Figure 4-21 Update P2**

(3) Pick-up point P3

① The robot is moved to the first discharge point in the storage area through the inching control moths, as shown in Figure 4-22. In the **IO** control panel, turn off the **DO\_09** signal switch, and turn on the **DO\_10** signal switch. After 1 second, turn off the **DO\_10** signal switch. Let the end of the robot release the material and then close the sucker. See whether the circular material can be accurately placed in the groove, if not, it needs to be debugged again.

**Figure 4-22 First placing point**

![Official CR3 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSYAcydckK0frVxV8q3HC%2Futp-07a3de25de26ce140c71.jpg?alt=media)

![Official CR3 training-system figure, source page 76](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeCe75ExfzY0k6TN5b4LW%2Futp-b627e43af4a09b559ae2.jpg?alt=media)

* ② Open **Points** , and click **P3** , then click **Cover,** as shown in Figure 4-23, and
* then click **OK** on the **Tips** interface that pops up.

**Figure 4-23 Update P3**

**3. 8 Save program**

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 4-24.

**Figure 4-24 Save program**

* Note: " " is for saving the program to the robot controller. If you want to save the

modified program to the local computer, you need to use "

".

#### 3.9 Run program

![Official CR3 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbkXG1FuIuZdpWz5LxSPB%2Futp-4c37c33cade6995ca9ed.jpg?alt=media)

![Official CR3 training-system figure, source page 77](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FN3e6w3uC5tepm1pzqcIA%2Futp-d1def01bbc6f8c9eac8c.jpg?alt=media)

First click the " " button, then press the **Reset** button, wait for the yellow light to flash, and then press the **Start** button, as shown in Figure 4-25.

Observe the operation of the program as follows: After the equipment is running, the circular workpiece in the silo is pushed onto the conveyor belt by the pushing motor, which carries the circular workpiece forward. When the circular workpiece reaches the grasping point, the conveyor belt stops moving. The robot moves the circular workpiece to the circular groove of the circular workpiece loading plate in the storage area, as shown in Figure 4-26.

**Figure 4-25 Control button**

**Figure 4-26 Storage area**

**3. 10 Export program**

Click **File > Export project** , select the path where the program is stored, and in

the dialog box that pops up, name the program.

Note: **Export project** is to export the program to your local computer for backup.

![Official CR3 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fn2Cr9XJlFARKqanbNjjF%2Futp-35ae3445096231e88ed8.jpg?alt=media)

![Official CR3 training-system figure, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9SvCZJbnE1urIVZ3DRK8%2Futp-a8c1f4125430dd8a8d90.jpg?alt=media)

**4. Program Description**

#### 4.1 Set variables for material spacing

Use a ruler or other measuring tool to measure the distance between two adjacent

circles in the storage area, as shown in Figure 4-27.

**Figure 4-27 Measure interval between blocks**

According to the measurement results, the variable of material spacing at the

discharge point was set in the robot **src0.lua** program, as shown in Figure 4-28.

**Figure 4-27 Set the variable of material spacing**

#### 4.2 Robots Program Description

#### 4.2.1 src0. Lua

After starting the program, initialize the variable **signal** and reset the tricolour

light and conveyor belt, as shown in Figure 4-29.

![Official CR3 training-system figure, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0LcPN4rhtsAbSo3xBLdL%2Futp-c95899a2f6de4e2a038b.jpg?alt=media)

![Official CR3 training-system figure, source page 79](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTx2Ya7aBTl5okEnfPc8J%2Futp-ce9d5f7ea454491ce489.png?alt=media)

**Figure 4-29 Reset IO port**

When the received **signal** is **reset** , only the yellow light is on, then reset the suction and blowing IO ports of the suction cup, and retract the pushing motor, and then clear the **signal** , and the yellow light is off, as shown in Figure 4-30.

**Figure 4-30 "Reset" button is pressed**

If the **Start** button is pressed and the green light is on, the robot will move to the safe position. By calling the get\_material() function in the global.lua program, the conveyor belt is started to transport materials to the sensor sensing point (P2 point) and the robot is controlled to move to P2 point to absorb materials. Then, the robot is controlled to move to 6 discharge points in the storage area to place materials, as shown in Figure 4-31.

![Official CR3 training-system figure, source page 80](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fw61EpEOuOOnQuWod0QkV%2Futp-1df14cc50529a0b013f3.jpg?alt=media)

**Figure 4-31 The "Start" button is pressed**

In the process of material handling by the robot, if the **Stop** button is pressed, the

red light will turn on and the green light will turn off, and the device will stop running, as shown in Figure 4-32.

**Figure 4-32 The "Stop" button is pressed**

#### 4.2.2 src1.lua

Start a thread in the **src1.lua** program to detect the input signal of the external

button, as shown in Figure 4-33.

![Official CR3 training-system figure, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGPz6XFSLWvn5hVG2nZpi%2Futp-a173e9b115b1dfb9c37c.jpg?alt=media)

![Official CR3 training-system figure, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5ExLaPWt5Ey6ONQLvqII%2Futp-b274178caed3fd3963f4.jpg?alt=media)

**Figure 4-33 Detecting if a button is pressed**

#### 4.2.3 global.lua

Figure 4-34 shows the function of waiting for DI signal. The function is used to

wait for external signal input.

**Figure 4-34 Define the function that waits for the DI signal**

Define the function of the robot to grab the material from the conveyor belt. When there is material in the silo, the pusher motor pushes out the material. After five seconds, the pusher motor retracts and the conveyor belt moves forward with the material until it is detected by the sensor. The robot moves to the grab point to extract the material. Figure 4-35 shows the program.

![Official CR3 training-system figure, source page 82](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlytNlyzJvWla5fa7KMN9%2Futp-b0a2d19648bf77350614.jpg?alt=media)

**Figure 4-35 Robot to draw the workpiece**

![Official CR3 training-system figure, source page 83](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeQG6rZRbOdSNKoEn2Q43%2Futp-cca8ae4060c29b9640fc.jpg?alt=media)

## Chapter 5 Static palletizing

### 1. Introduction

The specific task to be realized in the static palletizing application is to use the robot to move the blocks placed on the standard vision loading board to the grooves of the rectangular workpiece loading board in the storage area, as shown in Figure

5-1.

**Figure 5-1 Palletizing blocks**

### 2. Hardware Description

#### 2.1 Install standard vision carrier board

Install the standard vision carrier board above the conveyor belt, as shown in

Figure 5-2 .

![Official CR3 training-system figure, source page 84](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEpVlKyTvAscKBj5nQnbv%2Futp-bf8a975dc12d2ee2a392.png?alt=media)

**Figure 5-2 Install standard vision board**

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

Connect the CR3 to the power supply, and turn on the power switch of the CR3 general training system, as shown in Figure 5-3.

![Official CR3 training-system figure, source page 85](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2NYKzbYIrypZ5vSIQd7Y%2Futp-c0671878f6b71b572d7f.jpg?alt=media)

**Figure 5-3 CR3 general training system power switch**

#### 3.1.2 Turn on the air pump box switch

Turn on the power switch of the air pump box and rotate the control button to

**Auto** , as shown in Figure 5-4.

**Figure 5-4 Pump box**

#### 3.1.3 Preparation of palletized materials

Place the six blocks in the lower right corner of the standard visual loading board and arrange them in a 2×3 matrix, as shown in Figure 5-5.

![Official CR3 training-system figure, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdYXuXhds2VJQa1ytyJ40%2Futp-76fe66931110b0a471b2.jpg?alt=media)

![Official CR3 training-system figure, source page 86](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzFjaVYWzyhPEtjiJk3QP%2Futp-01cbfdd56a2023048af3.jpg?alt=media)

**Figure 5-5 Palletizing materials**

#### 3.2 Connect robot

* (1) Power on the robot.

Check whether the power switch of the robot controller and the robot switch are

turned on. If not, all switches need to be turned on, as shown in Figure 5-6.

**Figure 5-6 Robot control cabinet**

* (2) Connect the robot to the computer.

Connect one end of the network cable to the LAN interface of the robot

controller, and the other end to the computer.

* (3) Change the IP address of the computer.

Open your computer's control panel, select **Network and Internet/ Network** and **Share Center** , and enter the network and share center window. Click **Ethernet**

![Official CR3 training-system figure, source page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

![Official CR3 training-system figure, source page 87](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNUpcH4bPuGi7l9myuQkr%2Futp-8c4368818792f6ab5753.jpg?alt=media)

and select **Properties** to enter the ethernet property setting page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to enter the interface of **Internet Protocol version 4 (TCP/IPv4) properties** , and reset the IP address of PC side, as shown in Figure 5-7. The default address of the robot is **192.168.5.1** , and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment with the robot. The subnet mask and default gateway are the same as those of

the robot, taking **192.168.5.100** as an example here.

**Figure 5-7 IP setting of PC**

* (4) Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro v2.6.1** to open the software. Select **CR3** on the top toolbar, and click **Connect** , as shown in Figure 5-8.

![Official CR3 training-system figure, source page 88](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLv9PNYl0uSccplTE60qJ%2Futp-84222134110a55868311.png?alt=media)

**Figure 5-8 Connect robot**

After successful connection, DobotStudio Pro Pro interface will pop up a prompt message and the connection status will change to **Connected** , as shown in Figure 5-9.

**Figure 5-9 Connected robot**

#### 3.3 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 5-10. Then click **Confirm modification** , the enable icon becomes " ".

![Official CR3 training-system figure, source page 89](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure 5-10 Set load parameters**

#### 3.4 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 5-11.

**Figure 5-11 Global rate settings**

#### 3.5 Adjust the initial pose of the robot

**(1) Select Setting>Basic .**

(2) Check if the joint coordinate of the robot is as shown in Figure 5-12, and then click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

![Official CR3 training-system figure, source page 90](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

**Figure 5-12 Adjusting the initial pose of the robot**

#### 3.6 Importing program

* (1) Open the DobotStudio Pro software, enter the script programming page, and

click **File** > **Import project** , as shown in Figure 5-13.

**Figure 5-13 Import project**

* (2) Select the folder **CR3Project> Trajectory Simulation** , and click **Open** , as

shown in Figure 5-14, then import the static palletizing program into the software.

![Official CR3 training-system figure, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 91](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

**Figure 5-14 Import path**

#### 3.7 Debug points

* (1) Safe point P1

Move the robot between the conveyor belt and the storage area through hand-held teaching or inching control methods, as shown in Figure 5-15. Click **Points** in DobotStudio Pro, and select **P1** , then click **Cover** , as shown in Figure 5-16.

**Figure 5-15 Point P1**

![Official CR3 training-system figure, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdBExaZHFaE7uzaLeKUdO%2Futp-bebd700412d3da9b683d.jpg?alt=media)

![Official CR3 training-system figure, source page 92](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZFDnDOPCnGefA6Oz1uky%2Futp-2b1efbabb928d77568b6.jpg?alt=media)

**Figure 5-16 Update P1**

**(2) Pick-up point P2**

By using hand-held teaching or inching control methods, the robot is moved to the position of the first block’s pick-up point on the standard visual loading board, and the sucker needs to needs to touch the center position of the first block, as shown in

Figure 5-17. Then select **P2** in **Points** , and click **Cover** , as shown in Figure 5-18.

**Figure 5-17 Picking point P2 of the first block**

![Official CR3 training-system figure, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FObG74lwjew1YZ1emGvvt%2Futp-a6cef1291757627b05b1.jpg?alt=media)

![Official CR3 training-system figure, source page 93](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FT2hTfpLgmtsXifg7ENM4%2Futp-c59185c9a541bf7cecee.jpg?alt=media)

**Figure 5-18 Update P2**

(3) Placing material point P3

Make sure that the end of the robot is at point P2, and then open **IO** control panel. Open the **DO\_09** signal switch allows the end of the robot pick up the block, as shown in Figure 5-19. By using inching control methods, the robot is allowed to draw the first material and move it to the position P3 of the first placing point in the storage area, as shown in Figure 5-20. Then select **P3** in **Points** , and click **Cover** , as shown in

Figure 5-21.

**Figure 5-19 IO panel**

![Official CR3 training-system figure, source page 94](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlJMhnIzhzAdJV71BamQg%2Futp-1352085c139dbf47b66d.jpg?alt=media)

![Official CR3 training-system figure, source page 94](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcNltGmQkBRbSGbISLYDr%2Futp-5f653d55fa7593c459c3.jpg?alt=media)

**Figure 5-20 Placing point P3 of the first block**

**Figure 5-21 Update P3**

In the **IO** control panel, turn off the **DO\_09** signal; at the same time, turn on the DO\_10 signal. After 1 second, turn off the **DO\_10** signal switch; let the end of the robot close the sucker after releasing the block. Check if the block can be accurately placed in the grooves, and if not, it needs to be debugged again.

#### 3.8 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 5-22.

![Official CR3 training-system figure, source page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzxBz3q1U6HMSfDk4J6Ox%2Futp-9fe9fd3e81c407f30317.jpg?alt=media)

![Official CR3 training-system figure, source page 95](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3ki5kgp9x317OdmYfB0d%2Futp-f227fa75acb0eca6737b.jpg?alt=media)

**Figure 5-22 Save program**

Note: " " is for saving the program to the robot controller. If you want to save the

modified program to the local computer, you need to use "

".

#### 3.9 Run program

Click the " " button to run the program. Observe whether the robot successively moves the 6 blocks which are arranged by a 2×3 matrix in the standard visual loading board, and successively place them into the grooves of the 6

rectangular workpiece loading board in the storage area, as shown in Figure 5-23.

**Figure 5-23 Palletizing effect**

#### 3.10 Export program

Click **File > Export project** , and select the path where the program is stored, then, in the dialog box that pops up, name the program.

Note: **Export project** is to export the program to your local computer for backup.

![Official CR3 training-system figure, source page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEpVlKyTvAscKBj5nQnbv%2Futp-bf8a975dc12d2ee2a392.png?alt=media)

![Official CR3 training-system figure, source page 96](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu2GPdWmEiLPRWNkepZI6%2Futp-8eac6a122f2945c2f709.jpg?alt=media)

### 4. Program Description

#### 4.1 Set variables for block interval

Use a ruler or other measuring tools to measure the horizontal and vertical spacing between the two blocks of the material extraction point; using the same method, respectively measure the horizontal and vertical spacing between the two

blocks of the placing point, as shown in Figure 5-24.

**Figure 5-2 4Measure interval between blocks**

According to the measurement results, the variables of material spacing at the take-up point and the variables of material spacing at the placing point were set

respectively in the robot program, as shown in Figure 5-25.

**Figure 5-25 Set block interval variables**

#### 4.2 Robot pick-up program

Set the robot to pick up the blocks in the standard vision board following the sequence shown in Figure 5-26. The coordinate of the first block that the robot draws at the pick-up point is P2.

![Official CR3 training-system figure, source page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0yqsJkYjqVMrAg58eJMc%2Futp-fde88ec7fd3da3894117.png?alt=media)

![Official CR3 training-system figure, source page 97](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtbzHhcPV0SVbpL10AokA%2Futp-159a31a4dff09b1e49aa.jpg?alt=media)

**Figure 5-26 Robot pick-up sequence**

By using hand-held teaching methods, the robot can store the coordinates P2 of the first block of the pinking point. According to the order of robot picking up materials and the horizontal and vertical spacing of the picking points,the coordinates of the corresponding picking points of the other 5 blocks can be obtained. The program of the robot pick-up 6 blocks from the standard visual carrier board is shown in Figure 5-27.

**Figure 5-27 Robot pick-up program**

After picking up the block, the robot needs to move to the safe point P1 to ensure the safety of the robot movement.

#### 4.3 Robot placement program

Set the robot to place blocks following the sequence shown in Figure 5-28. The coordinate of the first block that placed by the robot at the placing point is P3.

![Official CR3 training-system figure, source page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGOh0UJ6cCGTd1GdmoGDP%2Futp-1b78aa054f10e0176beb.jpg?alt=media)

![Official CR3 training-system figure, source page 98](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBzDOGKAj3TjvHLFLHq53%2Futp-f29ef388ddaf80260187.jpg?alt=media)

**Figure 5-28 Robot placement sequence**

By using hand-held teaching methods, the robot can store the coordinates P3 of the first block of the placing point. According to the order of robot placing materials and the horizontal and vertical spacing of the placing points, the coordinates of the corresponding placing points of the other 5 blocks can be obtained. The program for placing 6 blocks into the 6 rectangular grooves of the board in the storage area is shown in Figure 5-29.

**Figure 5-29 Robot placement program**

![Official CR3 training-system figure, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5iRDYgI3ouvZ9j6ma06Y%2Futp-f0cff833cee4c7880b84.jpg?alt=media)

![Official CR3 training-system figure, source page 99](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0ghdx4HP4TeNvZLaMXEN%2Futp-03d7849ffe676b05969b.jpg?alt=media)

## Chapter 6 Vision sorting

**1. Introduction**

The specific task to be realized in this chapter is to use the robot to move 6 building blocks of 3 colors in the standard vision loading board, as shown in Figure 6-1, to the grooves of the rectangular/circular workpiece loading board in the storage area, and place them in different colors as required, as shown in Figure 6-2.

**Figure 6-1 Six square materials**

**Figure 6-2 Storage area**

### 2. Hardware Description

#### 2.1 Install standard vision carrier board

Install the standard vision carrier board above the conveyor belt, as shown in

Figure 6-3.

![Official CR3 training-system figure, source page 100](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZfbWr4KaHPJTaIaL6uvL%2Futp-cf8e3edfb0d0a1e1d979.jpg?alt=media)

![Official CR3 training-system figure, source page 100](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUOc6nFaD8qraMTEFwMAo%2Futp-5b4e63b835c12f6fe7f1.jpg?alt=media)

**Figure 6-3 Install standard vision board**

#### 2.2 IO configuration configuration

The IO configuration of vision sorting is shown in Table 6-1 .

**Table 6-1 IO configuration**

| **Output** | **Description** |
| ---------- | --------------- |
| DO10       | Vacuum pumping  |
| DO11       | Vacuum breaking |

**3. Program Debugging**

#### 3.1 Preparation

#### 3.1.1 Turn on CR3 general training system power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3

general training system, as shown in Figure 6-4.

92<br>

![Official CR3 training-system figure, source page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVv3xfRTGdCXB1gtLZ6FI%2Futp-44489226e5513b810567.jpg?alt=media)

![Official CR3 training-system figure, source page 101](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FURo9Up5mFWRNLc0ChZjM%2Futp-8125ec12cbd5c93cbdd2.jpg?alt=media)

**Figure 6-4 CR3 general training system power switch**

#### 3.1.2 Turn on the air pump box switch

Turn on the power switch of the air pump box and rotate the control button to

**Auto** , as shown in Figure 6-5.

**Figure 6-5** Air pump box

#### 3.1.3 Turn on the light source switch

Turn on the light source switch, as shown in Figure 6-6.

**Figure 6-6 Light source switch**

#### 3.2 Connect camera

Plug the dongle of DobotVisionStudio into the computer. Plug the USB cable of

the training system (used to connect the camera) into the computer.

#### 3.3 Connect robot

![Official CR3 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMm3WSG8sjLeWuIAbArPE%2Futp-f432b12a339c15ee8bcd.jpg?alt=media)

![Official CR3 training-system figure, source page 102](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoZeyuuzXAE8alHg9x3T6%2Futp-2984aa0143483d7d9143.jpg?alt=media)

* （1）Power on the robot.

Check whether the power switch of the robot controller and the robot switch are

turned on. If not, all switches need to be turned on, as shown in Figure 6-7.

**Figure 6-7 Robot control cabinet**

(2) Connect the robot to the computer.

Connect one end of the network cable to the LAN interface of the robot controller, and the other end to the computer.

* (3) Change the IP address of the computer.

Open your computer's control panel, select **Network and Internet/ Network** and **Share Center** , and enter the network and share center window. Click **Ethernet** and select **Properties** to enter the ethernet property setting page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to enter the interface of **Internet Protocol version 4 (TCP/IPv4) properties** , and reset the IP address of PC side, as shown in Figure 6-8. The default address of the robot is **192.168.5.1** , and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment with the robot. The subnet mask and default gateway are the same as those of the robot, taking **192.168.5.100** as an example here.

![Official CR3 training-system figure, source page 103](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

**Figure 6-8 PC IP address Settings**

* （4）Connect DobotStudio Pro to the robot.

Double-click **DobotStudio Pro v2.6.1** to open the software. Select **CR3** on the

top toolbar, and click **Connect** , as shown in Figure 6-9.

**Figure 6-9 Connect robot**

After successful connection, you will see a prompt message, and the connection

status will change to **Connected** , as shown in Figure 6-10.

![Official CR3 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft5P2WygcLRwtOb3LhbOt%2Futp-117c4ca7b1cb1485bc86.png?alt=media)

![Official CR3 training-system figure, source page 104](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure 6-10 Robot connected**

#### 3.4 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 6-11.

Then click **Confirm modification** , the enable icon becomes " ".

**Figure 6-11 Set load parameters**

#### 3.5 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 6-12.

![Official CR3 training-system figure, source page 105](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

**Figure 6-12 Global rate settings**

#### 3.6 Adjust the initial pose of the robot

* (1) Select **Setting>Basic** .

(2) Check if the joint coordinate of the robot is as shown in Figure 6-13, and then click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

**Figure 6-13 Adjusting the initial pose of the robot**

#### 3.7 Debug vision program

#### 3.7.1 Eye-to-hand calibration

* （1）Install calibration needle

Use the hexagonal tools to remove the screw at the end of the CR3 robot sucker,

as shown in Figure 6-14.

![Official CR3 training-system figure, source page 106](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

**Figure 6-14 Remove the end of the sucker**

Then install the prepared calibration needle and the removed screw to the end of the robot, as shown in Figure 6-15.

**Figure 6-15 Install calibration needle**

（2）Place the calibration paper on the standard vision carrier board, as shown in

Figure 6-16.

![Official CR3 training-system figure, source page 107](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Foz1fQrj3lE4qhQz9CBUH%2Futp-a2c5bdb58db0f2ca8618.jpg?alt=media)

![Official CR3 training-system figure, source page 107](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUdzFAkMnuAIMcggIG3MD%2Futp-3dae1313a7ae54303788.jpg?alt=media)

**Figure 6-16 Place the calibration paper**

* （3）Open DobotVisionStudio, and select **General Solution.**
* （4）Establish the solution process. In the toolbox, drag the **Image Source** tool

from the **Acquisition** sub toolbox to the process editing area, as shown in Figure 6-17.

**Figure 6-17 Solution process**

Set **0 Image Source1** parameters. Double-click **0 Image Source1** to set parameters. Select **Camera** as the image source, as shown in Figure 6-18. Click **Camera management** on the right side of the associated camera to enter the camera management interface.

![Official CR3 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7iaQverxU0bEscWLyh1D%2Futp-8830a7aa7061ddacb0a0.jpg?alt=media)

![Official CR3 training-system figure, source page 108](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUxqe4sO6ePG9ltCSLTSm%2Futp-74da5aad8c09a5020cf7.jpg?alt=media)

**Figure 6-18 0 Image Source**

Create global camera. Click the plus sign on the right of **Device List** to create **1 Global Camera 1** and set camera parameters. On the **Common Params** screen, click the small triangle symbol on the right of **Choose Camera** to select the camera that is currently directly connected to the computer. Select **Mono8** in **Pixel Format** of **Image Params** , as shown in Figure 6-19. Click **Trigger Settings** , set **Trigger Sourse** to **SOFTWARE** , and click **Confirm** , as shown in Figure 6-20. Then return to the image source interface.

**Figure 6-19 Common Params**

![Official CR3 training-system figure, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoO2B5F62t2cMOwLMCMj0%2Futp-d30f26b70bbbbf837708.png?alt=media)

![Official CR3 training-system figure, source page 109](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpvfQCyKsLhCU8Dyl1iSF%2Futp-5bce1e064af32a01bba6.jpg?alt=media)

**Figure 6-20 Trigger Settings**

In the **0 Image Source 1** interface, click the small triangle symbol in the lower right corner of the associated camera and select **1 Global Camera1** , as shown in Figure 6-21.

**Figure 6-21 Relate Camera**

Then click" ( **Continuously)** " and adjust the aperture and focus ring of the lens and the exposure time of the camera until you can see a clear image in the image display area. The image collection results are shown in Figure 6-22.

![Official CR3 training-system figure, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDIIOWMraRE5jeh4J84mc%2Futp-e3f076bf49cb5ff64f1c.jpg?alt=media)

![Official CR3 training-system figure, source page 110](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0KIGoI3XUG20X0DrXDRJ%2Futp-6b20bb76fefb77320e71.jpg?alt=media)

**Figure 6-22 Image collection result**

（5）Add **calibration of calibration board** tool in the solution process.

Drag the **CalibBoard Calib** tool from the **Calibration** sub toolbox to the process editing area and connect it to **0 Image Source1** , as shown in Figure 6-23.

**Figure 6-23 Process**

Note: The calibration of the calibration board is used to obtain the calibration point, and provide the pixel coordinates of the calibration point for N-point calibration.

（6）Add **N-point Calibration** in the solution process. Drag the **N-point Calibration** tool from the **Calibration** sub toolbox to the process editing area and connect it to **2 CalibBoard Calib1** . After **3N-point Calibration1** is connected to **2**

**CalibBoard Calib1** , click the " ( **Once)** " button. In the image display area, the nine calibration points and its calibration sequence will be automatically displayed, as shown in Figure 6-24.

![Official CR3 training-system figure, source page 111](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzEdL2k57ePQySRTsi70R%2Futp-33c139f1a4711c4cb598.jpg?alt=media)

**Figure 6-24 Check nine calibration points and calibration sequence**

Basic parameter settings for **3N-point Calibration1** . Double-click **3N-point Calibration** to set basic parameters. Set **Translation Number** in **Basic Params** .

Keep the default parameter 9 and set **Rotation Number** . Click the icon " " to the right of translation number, as shown in Figure 6-25. The **Edit Calibration Point** interface that pops up allows you to edit the calibration points, as shown in Figure 6-26.

![Official CR3 training-system figure, source page 112](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fykz4PCe3Bw1FT4ymOA4w%2Futp-5457362104e6b136bd5a.jpg?alt=media)

![Official CR3 training-system figure, source page 112](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZgVCoH0vV4rtwLT6wm6X%2Futp-1c8c17ad7b2e51026fa8.jpg?alt=media)

**Figure 6-25 3 N-Point Calibration**

**Figure 6-26 Edit Calibration Points**

In **Edit Calibration Points** page, exchange Line 3 (ID: 3) and Line 5 (ID: 5)

data, as shown in Figure 6-27.

**Figure 6-27 “Edit Calibration Points” after data exchange**

After clicking the " **(Once)** ", you can see that the calibration sequence turns

into the font **2** in the image display area, as shown in Figure 6-28.

![Official CR3 training-system figure, source page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH3fUADZt5OHpruHPYXFI%2Futp-92b2b2a4f23d7ef7fab2.jpg?alt=media)

![Official CR3 training-system figure, source page 113](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvu6iL3RRZl3dS0zmkQSz%2Futp-c90bd98253620309409f.jpg?alt=media)

**Figure 6-28 Calibration sequence after data exchange**

Open the DobotStudio Pro software, connect the robot, and turn on the robot's enable switch. According to the calibration sequence of 9 calibration points, the control robot reaches each calibration point according to the calibration sequence, as shown in Figure 6-29. Read the physical coordinates X and Y values of 9 calibration points on the DobotStudio Pro software, as shown in Figure 6-30. Then fill in the physical coordinates of **Edit Calibration Points** in DobotStudio Pro, as shown in Figure 6-31.

**Figure 6-29 First calibration point**

![Official CR3 training-system figure, source page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff9I0IIuMqS9fr4GLrnqc%2Futp-2af238a69f88f61bc3fd.jpg?alt=media)

![Official CR3 training-system figure, source page 114](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNxe7TpKrSSr2PfqXFq2E%2Futp-4169c9418f291a032bc9.jpg?alt=media)

**Figure 6-30** Robot physical coordinates of the first calibration point

**Figure 6-31 Physical coordinates of 9 calibration points**

![Official CR3 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhDvuMuDWrdoEyh8LjgWi%2Futp-7cd95e9e3a44a8c39e9e.jpg?alt=media)

![Official CR3 training-system figure, source page 115](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwmYPRL4J5XySH2SH1pMx%2Futp-89147f65e1432274c342.jpg?alt=media)

After the operation of editing the calibration point is completed, click **Refresh** and then click **Confirm** to save the physical calibration coordinates, as shown in Figure 6-32.

**Figure 6-32 "N point calibration" completed**

Generate the calibration file. After editing the calibration points, click " " in **Basic Params** page. Click **Create Calibration File** to export and store the calibration file to the computer and name it **Calibration file** for future calls, as shown in Figure 6-33.

In the **Basic Params** interface of **3N-point Calibration1** , click the **Create Calibration File** button to export and store the calibration file to the computer, and named **Calibration file** for future calls, as shown in Figure 6-33.

![Official CR3 training-system figure, source page 116](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhChCLWIftTI7tQC70F2E%2Futp-4cd240f5fe7c291acf64.jpg?alt=media)

**Figure 6-33 Generate calibration file**

Add **Calibration Transformation** in the flow. After calibration, you can add this tool to verify whether the calibration is accurate.

Drag **Calibration Transformation** in **Calculation** sub toolbox to the process editing area, and connect it with **3N-point Calibration1** ,as shown in Figure 6-34.

**Figure 6-34 Scheme process**

Set **4 Calibration Calibration** basic parameters. In **Basic Params** page, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** , and select the **Calibration file** generated by hand-eye calibration for **Load Calibration File** , as shown in Figure 6-35.

![Official CR3 training-system figure, source page 117](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFLimlIMLfeA73ktbA2MS%2Futp-4c12c11a50f1d5ce721f.jpg?alt=media)

**Figure 6-35 Set 44Calibration Transformation1 parameters**

Click " **(Once)** ", and check whether the 9 calibration data converted from **4 Calibration Transformation1** are consistent with the material coordinates obtained by the robot during N-point calibration, as shown in Figure 6-36. If consistent, the calibration is accurate. Otherwise, you need to re-calibrate.

![Official CR3 training-system figure, source page 118](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fox4bycXawVQnpAyuwjNZ%2Futp-2d60c09ffc9497eb43f5.jpg?alt=media)

**Figure 6-36 Comparison result**

#### 3.7.2 Import vision program

Open DobotVisionStudio 4.1.2, and select **General Solution** . Select **Open** in the toolbar. Find the vision sorting program and click **Open** . The imported vision program is shown in Figure 6-37.

![Official CR3 training-system figure, source page 119](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFxuJSxXIBsNsvkZ3xVoT%2Futp-02fb55ad6a056ea0abcc.jpg?alt=media)

**Figure 6-37 Vision program**

#### 3.7.3 Place detection object

Put the 3 colors blocks of red, green and blue into the detection field, as shown in

Figure 6-38.

**Figure 6-38 Place six blocks within the detection view**

![Official CR3 training-system figure, source page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUW1MSJcUrjr0fnqSRadr%2Futp-981daf3201d490131393.jpg?alt=media)

![Official CR3 training-system figure, source page 120](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnCN0APmJf2jdbfAHn6SR%2Futp-5b36c7fb2113087a093c.jpg?alt=media)

#### 3.7.4 Debug program parameters

（1）Debug **0 Image Source1** parameters.

Click " **(Once)** ", select **0 Image Source1** and observe whether the image is clear. If the image is not clear or there is no image, you need to reset the parameters according to the method described in 3.4.1. When setting the parameters, set **Pixel**

**Format** to **RGB8** . The image collected by the camera is shown in Figure 6-39.

**Figure 6-39 Collected image**

（2）Debug **2 Color Transformation1** parameters.

Double-click **2 Color Transformation1** to check whether **Transfer Type** is

**RGB to Grayscale** , as shown in Figure 6-40. If not, modify as the figure.

![Official CR3 training-system figure, source page 121](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2JldY4cODyViwalHsOJ1%2Futp-be39a0ffa44c28bea88a.jpg?alt=media)

**Figure 6-40 2Color Transformation**

Click " **(Once)** ". The execution result of **2 Color Transformation 1** is shown

in Figure 6-41.

**Figure 6-41 Grayscale Image**

* （3）Debug **3 Fast Match1** parameters.

![Official CR3 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjYDHifLyrDJK5kGo39xi%2Futp-464c9c3ecf48362bd885.jpg?alt=media)

![Official CR3 training-system figure, source page 122](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgPjJU5mXN5ixK1O76QKt%2Futp-2608f1f3c83242d444f3.jpg?alt=media)

Double-click **3 Fast Match1** . Click **Run Params** and modify **Max Number to find** to **3** . Then click **Execute** and observe whether all the blocks are recognized in the image display area, as shown in Figure 6-42.

**Figure 6-42 Run Params**

If all the blocks are recognized, use the original model. Otherwise, you need to

re-create the feature model, as described below.

①Enter **Feature Model** page. Delete the original model and then click **Create** ,

as shown in Figure 6-43.

**Figure 6-43 Feature Model**

* ② In template creation page, click **Current Image** . Click " **(Create Rect**
* **Mask)** ", select the corresponding area in the image and set corresponding model

![Official CR3 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5nceRLRNS51GsKpUBJdz%2Futp-45529d085237a6efb7fc.jpg?alt=media)

![Official CR3 training-system figure, source page 123](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTxcBtcGCNpM4lUP9lbtQ%2Futp-9bb2a786bb2f2784a24a.jpg?alt=media)

parameters (generally default). Then click " **(Build Model)** ", and click **Confirm** , as

shown in Figure 6-44.

**Figure 6-44 Model settings**

③ After creating the model, click **Execute** and **Confirm** , as shown in Figure

6-50.

**Figure 6-45 Result**

![Official CR3 training-system figure, source page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxwzoYdxLMuJFPuNPRjvG%2Futp-3dcef3da4cebf663cbac.jpg?alt=media)

![Official CR3 training-system figure, source page 124](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAmujsNSKpCyT8lPCAUOU%2Futp-8a08985ef11c34fa738e.jpg?alt=media)

Note: If not all the blocks can be recognized, maybe it is caused by the light. You can change the threshold value.

④ Double-click **3 Fast Match1** . Click **Run Params** and modify **Max Number to find** to **1** . Then click **Execute** , and the recognized block is shown in the image display area. Click **Confirm** , as shown in Figure 6-46.

**Figure 6-46 Result**

（4）Debug **4 Calibration Transformation1** parameters.

Double-click **4 Calibration Transformation1** . Check whether **Coord Point** is **Fast Match.Match Point** . Load the saved 9-point calibration file, as shown in Figure 6-47.

**Figure 6-47 Basic Params**

![Official CR3 training-system figure, source page 125](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fh3PRVQ73qmPoIsSzSPYx%2Futp-53d2dab3f9c60f2651fc.jpg?alt=media)

![Official CR3 training-system figure, source page 125](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJDn9FGwLVnL65FqHfraj%2Futp-e3b6ed0b507bcdff2d53.jpg?alt=media)

![Official CR3 training-system figure, source page 125](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzjYP9DnqYbVp6GGQKk92%2Futp-2c5a92831ad931aed733.jpg?alt=media)

Click **Execute** and **Confirm** , and the physical coordinates of the blocks are displayed in the result display area, as shown in Figure 6-48.

**Figure 6-48 Result**

（5）Debug **5 Color Recognition1** parameters.

Click " **(Once)** ". Select **5 Color Recognition1** , and modify the image display to **ImageSource1.OutputImage** . Observe whether the colour of the image is recognized correctly, as shown in Figure 6-49.

**Figure 6-49 Result**

![Official CR3 training-system figure, source page 126](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1AW3HMBL6GrOtPhP8mcY%2Futp-307a7ef87b4a06cf0c4e.jpg?alt=media)

![Official CR3 training-system figure, source page 126](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxPUh8icHHCw0nAGMMDS2%2Futp-39a2adb44422f664ca5a.jpg?alt=media)

If the objects of different colors are recognized incorrectly, you need to debug according to the following method.

* ① Double click **5 Color Recognition1** . In **Basic Params** page, check whether

**Input Source** and **ROI Area** are set as Figure 6-50.

**Figure 6-50 Basic Params**

② In **Color Model** page, delete the existing model. Click "+" to re-create

models, as shown in Figure 6-51.

**Figure 6-51 Color Model**

![Official CR3 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYN69Gy3MMUF2iOJElMop%2Futp-6d4a903696e4a078aab4.jpg?alt=media)

![Official CR3 training-system figure, source page 127](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnkE4FwhjucbATOmn3s14%2Futp-a70d517e22281694048e.jpg?alt=media)

③ Create a red model: In **ModelSettings** page, click " (add the current image)", then click "+" on the right side of **Label List** to add a new label, and click " ", then change the label name. Click " " in the toolbar, and drag a rectangular mask onto the image of the red building block (the selection range is the interior of the red building block image). Then click **Add To Label** , and you will see the added red model on the right side, as shown in Figure 6-52.

**Figure 6-52 Create red model**

Note: The material may be reflective due to the light, which could result in a difference in colour. In this case, you need to create several red models.

④ Using the same method, create the green and blue models as shown in Figure 6-53. Click **Confirm** to return to **Color Model** page.

![Official CR3 training-system figure, source page 128](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7RSngd2VEAnrZvB6UQRa%2Futp-a5af70aee1dbbdb1b0ca.jpg?alt=media)

**Figure 6-53 Create green and blue model**

⑤ Click **Execute** and **Confirm** , and the recognized colour of the block is shown

in the result display area, as shown in Figure 6-54.

**Figure 6-54 Result**

* （6）Debug **6 Variable Calculation1** parameters.

![Official CR3 training-system figure, source page 129](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0fPtftYrBmxsVdbmhYyZ%2Futp-b833a8cc126fee9cc3bb.jpg?alt=media)

![Official CR3 training-system figure, source page 129](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWVmDJ9RGAtdaSVCGo3G8%2Futp-35251ae276c85f9f5077.jpg?alt=media)

Click " **(Once)** ". Compare whether the value of **var0** in **6 Variable Calculation1** and the value of **MatchBoxAngle** in **3 Fast Match** are opposite to each other, as shown in Figure 6-55.

**Figure 6-55 Contrast**

If the values are not opposite, you need to debug according to the following method.

① Double-click **6 Variable Calculation1** . Click " " below **Expression** to enter **Var0** page. Click "  **3Fast Match1**  **MatchRect**  **MatchBoxAngle** " to add the variable. Select the variable, and then plus " **-** " in front of the variable, that is, to get the negative value of the angle. Then click **Save** to return to the **Basic Params** page, as shown in Figure 6-56.

![Official CR3 training-system figure, source page 130](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F52NPaCyJR3OviUTo3uPK%2Futp-848b94a43f399d6a42c6.jpg?alt=media)

**Figure 6-56 Expression**

② Click **Execute** and **Confirm** , and you will see the angle values, as shown in

Figure 6-57.

**Figure 6-57 Result**

* （7）Debug **7 Format1** parameters.

![Official CR3 training-system figure, source page 131](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA2lc6OfFVbEVW9KCjsrh%2Futp-40ffd8c3c2e92983ff7f.jpg?alt=media)

![Official CR3 training-system figure, source page 131](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGwfiBU9zTy5dKecawVjo%2Futp-ada51adeebbbc93eb550.jpg?alt=media)

Click " **(Once)** ". Select **7 Format1** , and observe whether the result display area the format result, as shows in Figure 6-58.

**Figure 6-58 Result**

If not, you need to debug according to the following method.

① Double-click **7 Format1** . In **Basic Params** page, as shown in Figure 6-59,

click "+" to add a row. Click " **(InsertSubscription)** ", and select **5 Color**

**Recognition1**  **Best Matched Name** .

![Official CR3 training-system figure, source page 132](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSoCRzvzGf2EgDsMNyA6S%2Futp-25f9b74dc2a3b22973f2.jpg?alt=media)

**Figure 6-59 Basic Params**

② Then click **T** and enter ",". Click " " and select " **4 Calibration Transformation1**  **OutputPoint**  **TransPointX** ", Insert“ **4 Calibration Transformation1.TransPointY** ” “ **,** ” “ **<6 Variable Calculation1.var0(%1.3f)>\[0]** ”, The format parameters are shown Figure 6-60.

**Figure 6-60 Foramt Params**

* （6）Debug the **Communication Management** parameters.

![Official CR3 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FANxJOfPZ58hhFTxsbw89%2Futp-eb0262b61063db3ffc3d.jpg?alt=media)

![Official CR3 training-system figure, source page 133](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnEP0DKEnbaj37ajeprr2%2Futp-34232e1c31bd437d7faa.jpg?alt=media)

Click " " in the quick toolbar to enter **Communication Management** page. Check whether there is established **TCP Server** , and whether its parameters are consistent with the figure below. If not consistent, modify as Figure 6-61.

**Figure 6-61 Communication Management**

If there is no **TCP Server** , you need to create one, as described below.

Click " " beside **Device Lists** to add devices，and set **Protocol Type** to **TCP Server** , **Load IP** to **192.168.5.100** , **Local Port** is set to **4001** , and then click **Create** , as shown in Figure 6-62. Finally, turn on the switch next to **1TCP Server** , as shown in Figure 6-63.

**Figure 6-62 Create “TCP Server”**

![Official CR3 training-system figure, source page 134](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fapw5DJOfuokVccNgeycY%2Futp-34ac7e35b647c6786c4f.jpg?alt=media)

![Official CR3 training-system figure, source page 134](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAghOns3nerPtHTTbGmdN%2Futp-d26ca8ca33d2831e8385.jpg?alt=media)

**Figure 6-63 Communication Management**

（7）Debug **8 Send Data1** parameters.

Double-click **8 Send Data1** , and check whether the parameters are shown as Figure 6-64. If not, modify as the figure. Set **Output To** to **Communication Device** , **Communication Device** to **1 TCP Server** , and **Send Data1** to **7Format1.format\_out\[]** . Then click **Confirm** .

![Official CR3 training-system figure, source page 135](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fe64lcOXjbIbfpt2hOWbh%2Futp-493b7ee5f89ebd39230f.jpg?alt=media)

**Figure 6-64 8Send Data1**

（7）Set the **Global Trigger** parameters

Click " " in the quick toolbar to enter **Global Trigger** page. In **String Trigger** page, check whether the string trigger setting is shown as Figure 6-65. String

is void; **Mode** is **Mismatched** ; **Trigger Configuration** is **All Process** .

**Figure 6-65 Global Trigger**

![Official CR3 training-system figure, source page 136](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FSv13bucxWIb6ODIPJ3xn%2Futp-83cbda2e5cff2c6248d0.jpg?alt=media)

![Official CR3 training-system figure, source page 136](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8sccsP4nk2fSjyFAPbdA%2Futp-b8756c7d914fa2d559af.jpg?alt=media)

#### 3.7.5 Save program

Click " **(Save)** " in the shortcut toolbar to save the program. If you need to Save the program somewhere else on your local computer, click **File > Save as** , select the path you want to save, and give the program a name.

#### 3.8 Robot Program Debugging

#### 3.8.1 Install the coaxial sucker tool

（1）Remove the calibration needle from the end of the robot, as shown in Figure

6-66.

**Figure 6-66 Remove the calibration needle**

* （3）Install the sucker on the end of the robot, as shown in Figure 6-67.

**Figure 6-67 Mounting the suction cup**

![Official CR3 training-system figure, source page 137](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQvp4KahZQkekVKishMEE%2Futp-e3a0c71a1cd80b78e119.jpg?alt=media)

![Official CR3 training-system figure, source page 137](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F59uzR2cwMTe2wCMYx85Q%2Futp-a31d4c3335c37a62092b.jpg?alt=media)

#### 3.8.2 Place blocks

Place blocks of different colors above the standard visual loading board, and confirm whether the materials in the storage area are empty, as shown in Figure 6-68.

**Figure 6-68 Place blocks**

#### 3.8.3 Import program

* （1）Open **DobotStudio Pro** and enter script page. Click **File** > **Import project** ，

as shown in Figure 6-69.

**Figure 6-69 Import robot program**

* （2）Select the **CR3 Vision Sorting** folder and click **Open** , as shown in Figure
* 6-70. The program is imported into DobotStudio Pro.

![Official CR3 training-system figure, source page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 138](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGGI3pHaQi4dR2wwOrkYy%2Futp-91e7b4e85968742f7ee3.jpg?alt=media)

**Figure 6-70 Import program**

#### 3.8.4 Debug points

The visual sorting application shares 7 points, and the debugging method is as

follows:

* （1）Safe point P1

Move the robot between the conveyor belt and the storage area through hand-held teaching or inching control methods. Click **Points** in the right-side menu of DobotStudio Pro. Select **P1** and click **Cover** , as shown in Figure 6-71. Then click **OK**

in the pop-up **Tips** window.

**Figure 6-71 Point P1**

![Official CR3 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAIrMYmw3YqnLiKMiP5JR%2Futp-284c6e605fedc622bbf1.jpg?alt=media)

![Official CR3 training-system figure, source page 139](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfVc8KiHM58RQqKie9fF2%2Futp-5b0a979e3f2c22083c95.png?alt=media)

* （2）First red block placing point P2

① Move the robot to one of the red blocks on the standard vision loading board through inching control methods. Open **IO** panel. Set **DO\_09** to **ON** to make the robot suck the block, as shown in Figure 6-72.

**Figure 6-72 I/O panel**

② Move the robot to the first red block placing point in the storage area through inching control method, as shown in Figure 6-73. Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the block

is placed into the groove accurately. If not, you need to re-debug the point.

![Official CR3 training-system figure, source page 140](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlJMhnIzhzAdJV71BamQg%2Futp-1352085c139dbf47b66d.jpg?alt=media)

![Official CR3 training-system figure, source page 140](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcDARI74Ahpk05nAB7EYO%2Futp-485afbf6b0265e32e078.jpg?alt=media)

**Figure 6-73 First red block placing point P2**

③ Open **Points** page. Select **P2** and click **Cover,** as shown in Figure 6-74.

**Figure 6-74 Update P2**

Update P3-P7 using the same method of P2, according to the placement requirement of red, green and blue blocks. The point position completed by update is shown in Figure 6-75.

**Figure 6-75 Updated points**

![Official CR3 training-system figure, source page 141](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBxW62ibiWEakMBroJbLO%2Futp-115fd10a24d691297cc3.jpg?alt=media)

#### 3.8.5 Set communication

Set the IP address of the robot program to the IP address of the computer ( **192.168.5.100** ) and the port number to **4001** . Ensure that the IP address and port number of the TCP server in the robot program are consistent with the local IP address and port number in the visual communication Settings, as shown in Figure 6-76.

**Figure 6-76 Set communication**

#### 3.8.6 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 6-77.

**Figure 6-77 Save program**

Note: " " is for saving the program to the robot controller. If you want to save the

modified program to the local computer, you need to use " ".

#### 3.8.7 Run program

Click the " " button to see if the program runs as follows:

The vision system detects the data of blocks, and transmits the colour and position data of blocks to the robot. After obtaining the information, the robot moves

![Official CR3 training-system figure, source page 142](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC0QQSLCSMJBKDQ3nCPnD%2Futp-5e301c25cfddad6c7809.jpg?alt=media)

to the detection area to suck the blocks, sorts and places them in the corresponding colour area. The sorting effect is shown in Figure 6-78.

**Figure 6-78 Sorting completed**

#### 3.8.8 Export program

Click **File** > **Export project** , and select the path where the program is stored, then, in the dialog box that pops up, name the program.

Note: **Export project** is to export the program to your local computer for backup.

**4. Program Description**

#### 4.1 Vision program description

This section only describes the main functions of each tool in the program. For specific parameter settings of the tools, please see the vision project file.

The vision program is shown in Figure 6-79. **0 Image Source1** is mainly used for image acquisition. During the system operation, the camera takes photos immediately after the vision software receives the trigger signal sent by the robot. The images acquired are all coloured images because colour recognition is to be performed. **2 Color Transformation1** is mainly used for converting colour images into grayscale images to locate grayscale images. **3 Fast Match1** is mainly used for locating grayscale images, and **3 Fast Match1** is used to obtain the image coordinates and matching angle of the detected object; **4 Calibration Transformation1** is used for transforming the image coordinates obtained by **3 Fast Match1** into actual

![Official CR3 training-system figure, source page 143](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKtc6Kv9NOfEVm9bdRjKQ%2Futp-12f7a4d9d1394f720d63.jpg?alt=media)

physical coordinates. **5 Color Recognition1** is used for creating a colour model to recognize the colour of blocks so that sorting can be performed by colour. **6 Variable Calculation1** is used for correcting the matching angle. **7 Format1** is used for summarizing and defining the format of the information that the vision system needs to send to the robot. **8 Send Data1** is used for sending the contents of **7 Format1** to the robot.

**Figure 6-79 Vision program**

#### 4.2 Robot program description

#### 4.2.1 src0.lua

The relevant variables for defining the robot program are shown in Figure 6-80.

**Figure 6-80 Define the relevant variables**

Define TCP data transfer function as shown in Figure 6-81. The robot sends the signal **ok** to the vision, which is triggered by the photo, and then receives the data sent by the vision.

**Figure 6-81 Data transfer program**

The function of defining the robot to absorb the blocks at the calibration point is shown in Figure 6 -82. The robot absorbs the blocks in the standard vision loading board according to the coordinate information sent by the vision.

![Official CR3 training-system figure, source page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fpo7zcpXEV6XchATm5UDc%2Futp-a515ccb398d053f8cbd4.jpg?alt=media)

![Official CR3 training-system figure, source page 145](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGfnN5WMabNFhMCg5UUfB%2Futp-e2ff7f2718f205dc6ca5.jpg?alt=media)

**Figure 6-82 Robot feeding program**

The program of communication is shown in Figure 6-83, which is mainly to

create TCP client and establish a connection with TCP server (visual).

**Figure 6-83 The program of communication**

The program for resetting the relevant IO output port is shown in Figure 6-84. It

is mainly to set some output port IO signals to **0** .

**Figure 6-84 Procedure of Reset outlet**

The complete sorting program of the robot is shown in Figure 6-85, Figure 6-86 and Figure6-87. The program circulates for 6 times. After obtaining the color and coordinate information of the building blocks sent by the vision, the robot will absorb the building blocks, and then place them into the groove where the rectangular/circular workpiece plate corresponds in the storage area, and then return to the safe point P1.

![Official CR3 training-system figure, source page 146](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2DpVLmZwo0DfZ3E0lKLL%2Futp-b1fa394045dc461e25bb.jpg?alt=media)

**Figure 6-85 Robot sorted the red blocks to points P2 and P3**

**Figure 6-86 Robot sorted green blocks to points P4 and P5**

![Official CR3 training-system figure, source page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRjiMDhF8uauDpO31nrLY%2Futp-f6509dce79ff1bf852c6.jpg?alt=media)

![Official CR3 training-system figure, source page 147](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUKbWywzqaaLx4nLEP4vL%2Futp-7b573d96e13cd76d803b.jpg?alt=media)

**Figure 6-87 Robot sorted blue blocks to points P6 and P7**

#### 4.2.2 global.lua

The function defining the string segmentation is shown in Figure 6-88. This

function is used to process the data sent from the visual side.

**Figure 6-88 Function that defines string segmentation**

The function defining the waiting DI signal is shown in Figure 6-89. This

function is used to wait for an external signal input.

**Figure 6-89 Define the function waiting for DI signal**

![Official CR3 training-system figure, source page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlCLv4vd6NLV7rhaxgXlT%2Futp-96d44721404444e31acb.jpg?alt=media)

![Official CR3 training-system figure, source page 148](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FLjvPNJIuc9Cvn8VXFMUB%2Futp-04f00a45c0bdea8782d7.jpg?alt=media)

## Chapter 7 Phone chip assembly

**1. Introduction**

The specific task to be realized in the mobile phone chip assembly application is to use the robot to install 6 chips (as shown in Figure 7-1) placed in the standard visual loading board into 6 grooves in the mobile phone base (as shown in Figure 7-2).

**Figure 7-1 Phone chip**

**Figure 7-2 Phone model**

### 2. Hardware Description

#### 2.1 Install standard vision loading board

![Official CR3 training-system figure, source page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0dRoKMg2i03VirWgmXdW%2Futp-b75dfa8a1385916062a5.jpg?alt=media)

![Official CR3 training-system figure, source page 149](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZQDtUie6PBxcM5bHmI1Z%2Futp-449afc5e54702ea24a86.jpg?alt=media)

Install the standard vision board above the conveyor belt, as shown in Figure 7-3.

**Figure 7-3 Install standard vision board**

#### 2.2 Install phone model board

Install the phone model board to the installation station, as shown in Figure 7-4.

**Figure 7-4 Phone model board**

#### 2.3 IO configuration

The IO configuration for installing mobile phone chips is shown in Table 7-1.

**Table 7-1 IO configuration of phone chip assembly**

![Official CR3 training-system figure, source page 150](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkM8jyhkiHTjsCxXcZh8Y%2Futp-98fb837f4e8753b59d2c.jpg?alt=media)

![Official CR3 training-system figure, source page 150](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNlvW8PyaXIfdZAGKSzF3%2Futp-30b5b3acb8d27f240e2f.jpg?alt=media)

| **Output** | **Description** |
| ---------- | --------------- |
| DO10       | Vacuumpumping   |
| DO11       | Vacuum breaking |

**3. Program Debugging**

#### 3.1 Preparation

#### 3.1.1 Turn on CR3 general training system power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3

general training system, as shown in Figure 7-5.

**Figure 7-5 CR3 general training system power switch**

#### 3.1.2 Turn on the air pump box switch

Turn on the power switch of the air pump box and rotate the control button to

**Auto** , as shown in Figure 7-6.

**Figure 7-6 Air pump box**

![Official CR3 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMm3WSG8sjLeWuIAbArPE%2Futp-f432b12a339c15ee8bcd.jpg?alt=media)

![Official CR3 training-system figure, source page 151](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVyFCDqtslz1jm8g1xuIg%2Futp-bdc5de15a6fb97c1a615.jpg?alt=media)

#### 3.1.3 Turn on the light source switch

Turn on the light source switch, as shown in Figure 7-7.

**Figure 7-7 Light source switch**

#### 3.2 Connect camera

Plug the dongle of DobotVisionStudio into the computer. Plug the USB cable of the training system (used to connect the camera) into the computer.

#### 3.3 Connect robot

* (1) Power on the robot.

Check whether the power switch of the robot controller and the robot switch are

turned on. If not, all switches need to be turned on, as shown in Figure 7-8.

**Figure 7-8 Robot control cabinet**

![Official CR3 training-system figure, source page 152](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

![Official CR3 training-system figure, source page 152](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3y1I9YDtAWjvsZ8KCzRQ%2Futp-1aacd46a70c34f01e0e9.jpg?alt=media)

* (2) Connect the robot to the computer.

Connect one end of the network cable to the LAN interface of the robot controller, and the other end to the computer.

* (3) Change the IP address of the computer.

Open your computer's control panel, select **Network and Internet/ Network** and **Share Center** , and enter the network and share center window. Click **Ethernet** and select **Properties** to enter the ethernet property setting page. Double-click **Internet Protocol Version 4 (TCP/IPv4)** to enter the interface of **Internet Protocol version 4 (TCP/IPv4) properties** , and reset the IP address of PC side, as shown in Figure 7-9. The default address of the robot is **192.168.5.1** , and the IP address of the PC can be modified to any IP address that is not occupied in the same network segment with the robot. The subnet mask and default gateway are the same as those of the robot, taking **192.168.5.100** as an example here.

**Figure 7-9 IP setting of PC**

* (4) Connect **DobotStudio Pro** to the Robot

Double-click **DobotStudio Pro v2.6.1** to open the software. Select **CR3** on the top toolbar, and click **Connect** , as shown in Figure 7-10.

![Official CR3 training-system figure, source page 153](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft5P2WygcLRwtOb3LhbOt%2Futp-117c4ca7b1cb1485bc86.png?alt=media)

**Figure 7-10 Connect robot**

After successful connection, you will see a prompt message, and the connection

status will change to **Connected** , as shown in Figure 7-11.

**Figure 7-11 Robot connected**

#### 3.4 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 7-12. Then click **Confirm modification** , the enable icon becomes " ".

![Official CR3 training-system figure, source page 154](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure 7-12 Set load parameters**

#### 3.5 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 7-13.

**Figure 7-13 Global rate settings**

#### 3.6 Adjust the initial pose of the robot

**(1) Select Setting>Basic .**

(2) Check if the joint coordinate of the robot is as shown in Figure 7-14, and then click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

![Official CR3 training-system figure, source page 155](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

**Figure 7-14 Adjusting the initial pose of the robot**

#### 3.7 Debug vision program

#### 3.7.1 Eye-to-hand calibration

* (1) Install calibration needle

Use the hexagonal tools to remove the screw at the end of the CR3 robot sucker,

as shown in Figure 7-15.

**Figure 7-15 Remove the end of the sucker**

Then install the prepared calibration needle on the end of the robot, as shown in

![Official CR3 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

![Official CR3 training-system figure, source page 156](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8od62ZQ72zyzRQB6TCqm%2Futp-7a6823186b9baf54ee83.jpg?alt=media)

Figure 7-16.

**Figure 7-16 Install calibration needle**

(2) Place the calibration paper on the standard vision carrier board, as shown in Figure 7-17.

**Figure 7-17 Place the calibration paper**

（3）Open DobotVisionStudio, and select **General Solution.**

* （4）Establish the solution process. In the toolbox, drag the **Image Source** tool
* from the **Acquisition** sub toolbox to the process editing area, as shown in Figure 7-18.

![Official CR3 training-system figure, source page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7iaQverxU0bEscWLyh1D%2Futp-8830a7aa7061ddacb0a0.jpg?alt=media)

![Official CR3 training-system figure, source page 157](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4AMzctqtFAdjc8S6f1X3%2Futp-b12276fdf159cc14c132.jpg?alt=media)

**Figure 7-18 Solution process**

Set **0 Image Source1** parameters. Double-click **0 Image Source1** to set parameters. Select **Camera** in the image source, as shown in Figure 7-19. Click **Camera management** on the right side of the associated camera to enter the camera management interface.

**Figure 7-19 0 Image Source**

Create global camera. Click the plus sign on the right of **Device List** to create **1 Global Camera 1** and set camera parameters. On the **Common Params** screen, click the small triangle symbol on the right of **Choose Camera** to select the camera that is currently directly connected to the computer. Select **Mono8** in **Pixel Format** of **Image Params** , as shown in Figure 7-20. Click **Trigger Settings** , set **Trigger Sourse**

![Official CR3 training-system figure, source page 158](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUxqe4sO6ePG9ltCSLTSm%2Futp-74da5aad8c09a5020cf7.jpg?alt=media)

![Official CR3 training-system figure, source page 158](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoO2B5F62t2cMOwLMCMj0%2Futp-d30f26b70bbbbf837708.png?alt=media)

to **SOFTWARE** , and click **Confirm** , as shown in Figure 7-21. Then return to the image source interface.

**Figure 7-20 Common Params**

**Figure 7-21 Trigger Settings**

In the **0 Image Source 1** interface, click the small triangle symbol in the lower right corner of the associated camera and select **1 Global Camera1** , as shown in Figure 7-22.

![Official CR3 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpvfQCyKsLhCU8Dyl1iSF%2Futp-5bce1e064af32a01bba6.jpg?alt=media)

![Official CR3 training-system figure, source page 159](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDIIOWMraRE5jeh4J84mc%2Futp-e3f076bf49cb5ff64f1c.jpg?alt=media)

**Figure 7-22 Relate Camera**

Then click " ( **Continuously)** " and adjust the aperture and focus ring of the lens and the exposure time of the camera until the image display area gets a clear picture. The image collection results are shown in Figure 7-23.

**Figure 7-23 Image acquisition result**

（5）Add **calibration of calibration board** tool in the solution process.

![Official CR3 training-system figure, source page 160](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0KIGoI3XUG20X0DrXDRJ%2Futp-6b20bb76fefb77320e71.jpg?alt=media)

![Official CR3 training-system figure, source page 160](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzEdL2k57ePQySRTsi70R%2Futp-33c139f1a4711c4cb598.jpg?alt=media)

Drag the **CalibBoard Calib** tool from the **Calibration** sub toolbox to the process editing area and connect it to **0 Image Source1** , as shown in Figure 7-24.

**Figure 7-24 Flow**

Note: The calibration of the calibration board is used to obtain the calibration point, and provide the pixel coordinates of the calibration point for N-point calibration.

（7）Add **N-point Calibration** in the solution process. Drag the **N-point Calibration** tool from the **Calibration** sub toolbox to the process editing area and connect it to **2 CalibBoard Calib1** . After **3N-point Calibration1** is connected to

**2CalibBoard Calib1** , click the " ( **Once)** " button. In the image display area, the nine calibration points and its calibration sequence will be automatically displayed, as shown in Figure 7-25.

**Figure 7-25 Check nine calibration points and calibration sequence**

![Official CR3 training-system figure, source page 161](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fykz4PCe3Bw1FT4ymOA4w%2Futp-5457362104e6b136bd5a.jpg?alt=media)

Basic parameter settings for **3N-point Calibration1** . Double-click **3N-point Calibration** to set basic parameters. Set **Translation Number** in **Basic Params** .

Keep the default parameter 9 and set **Rotation Number** . Click the icon " " to the right of translation number, as shown in Figure 7-26. The **Edit Calibration Point** interface that pops up allows you to edit the calibration points, as shown in Figure 7-27.

**Figure 7-26 3 N-Point Calibration**

**Figure 7-27 Edit Calibration Points**

![Official CR3 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZgVCoH0vV4rtwLT6wm6X%2Futp-1c8c17ad7b2e51026fa8.jpg?alt=media)

![Official CR3 training-system figure, source page 162](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FH3fUADZt5OHpruHPYXFI%2Futp-92b2b2a4f23d7ef7fab2.jpg?alt=media)

In **Edit Calibration Points** page, exchange Line 3 (ID: 3) and Line 5 (ID: 5) data, as shown in Figure 7-28.

**Figure 7-28 “Edit Calibration Points” after data exchange**

After clicking the **Refresh** , **Confirm** , and **Execute** buttons in sequence, you can see that the calibration order has changed to a into the font **2** in the image display area, as shown in Figure 7-29.

**Figure 7-29 Calibration sequence after data exchange**

![Official CR3 training-system figure, source page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fvu6iL3RRZl3dS0zmkQSz%2Futp-c90bd98253620309409f.jpg?alt=media)

![Official CR3 training-system figure, source page 163](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ff9I0IIuMqS9fr4GLrnqc%2Futp-2af238a69f88f61bc3fd.jpg?alt=media)

Open the DobotStudio Pro software, connect the robot, and turn on the robot's enable switch. According to the calibration sequence of 9 calibration points, the control robot reaches each calibration point according to the calibration sequence, as shown in Figure 7-30. Read the physical coordinates X and Y values of 9 calibration points on the DobotStudio Pro software, as shown in Figure 7-31. Then fill in the physical coordinates of **Edit Calibration Points** in DobotStudio Pro, as shown in Figure 7-32.

**Figure 7-30 First calibration point**

![Official CR3 training-system figure, source page 164](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNxe7TpKrSSr2PfqXFq2E%2Futp-4169c9418f291a032bc9.jpg?alt=media)

**Figure 7-31 Robot physical coordinates of the first the calibration point**

![Official CR3 training-system figure, source page 165](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhDvuMuDWrdoEyh8LjgWi%2Futp-7cd95e9e3a44a8c39e9e.jpg?alt=media)

![Official CR3 training-system figure, source page 165](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwmYPRL4J5XySH2SH1pMx%2Futp-89147f65e1432274c342.jpg?alt=media)

**Figure 7-32 Physical coordinates of 9 calibration points**

After the operation of editing the calibration point is completed, click **Refresh** and then click **Confirm** to save the physical calibration coordinates, as shown in

Figure 7-33.

**Figure 7-33 "N point calibration" completed**

Generate the calibration file. After editing the calibration points, click " " in **Basic Params** page. Click **Create Calibration File** to export and store the calibration file to the computer and name it **Calibration file** for future calls, as shown in Figure 7-34.

**Figure 7-34 Generate calibration file**

![Official CR3 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhChCLWIftTI7tQC70F2E%2Futp-4cd240f5fe7c291acf64.jpg?alt=media)

![Official CR3 training-system figure, source page 166](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFLimlIMLfeA73ktbA2MS%2Futp-4c12c11a50f1d5ce721f.jpg?alt=media)

Add **Calibration Transformation** in the flow. After calibration, you can add this tool to verify whether the calibration is accurate.

Drag **Calibration Transformation** in **Calculation** sub toolbox to the process editing area, and connect it with **3N-point Calibration1** ,as shown in Figure 7-35.

**Figure 7-35 the flow**

Set **4 Calibration Calibration** basic parameters. In the **Basic Params** column, set **Coord Point** to **2 CalibBoard Calib1.Calibration Point\[]** , and select the **Calibration file** generated by hand eye calibration for **Load Calibration File** , as shown in Figure 7-36.

**Figure 7-36 Set 4 Calibration Transformation1 parameters**

![Official CR3 training-system figure, source page 167](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fox4bycXawVQnpAyuwjNZ%2Futp-2d60c09ffc9497eb43f5.jpg?alt=media)

Click " **(Once)** ", and check whether the nine coordinates after **4 Calibration Transformation1** are consistent with the physical coordinates in 3N-point Calibration1, as shown in Figure 7-37. If consistent, the calibration is accurate. Otherwise, you need to re-calibrate。

**Figure 7-37 Comparison result**

#### 3.7.2 Import vision program

Open DobotVisionStudio 4.1.2, and select **General Solution** . Select **Open** in the toolbar. Find the phone chip assembly program and click **Open** . The imported vision program is shown in Figure 7-38.

![Official CR3 training-system figure, source page 168](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFxuJSxXIBsNsvkZ3xVoT%2Futp-02fb55ad6a056ea0abcc.jpg?alt=media)

**Figure 7-38 Vision program**

#### 3.7.3 Place phone model

Place six chips within the detection vision, as shown in Figure 7-39. For the first time of debugging, ensure that the chips are placed in the same orientation as that inside the phone model in the assembly area.

![Official CR3 training-system figure, source page 169](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZB5gjl7930aqa9qOHqSG%2Futp-d4ab2cb9ed050e4e0bbb.jpg?alt=media)

**Figure 7-39 Place chips within the detection view**

#### 3.7.4 Debug parameters

(1) Debug **0 Image Source1** parameters.

Click " **(Once)** ", select **0 Image Source1** and observe whether the image is clear. If the image is not clear or there is no image, you need to reset the parameters according to the method described in 3.7.1. The image collection results are shown in Figure 7-40.

![Official CR3 training-system figure, source page 170](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fp2X8LL3vL067LbcbsYrX%2Futp-cfae41ee9d8378f5a4bc.jpg?alt=media)

**Figure 7-40 Image acquisition result**

（2）Debug **2 Fast Match1** parameters.

Click " **(Once)** ", and double-click **2 Fast Match1** with the mouse, and then take away the chips one by one according to the order of chips placed in the groove of the phone model. Observe whether **2 Fast Match1** can accurately identify each type

of chip, as shown in Figure 7-41.

**Figure 7-41** Checking template-matching results

![Official CR3 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fycaa17mX1S7p8GQGQLnw%2Futp-f40a3fcf18740de7d6ea.jpg?alt=media)

![Official CR3 training-system figure, source page 171](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FK9cgFvUMX9A7qsA1cH53%2Futp-90ef48c83fd7f211dfe4.png?alt=media)

If it cannot be accurately identified, you need to modify the parameter of **2 Fast Match1** . Set **Basic Params** as shown in Figure 7-42.

**Figure 7-42 Set 2Fast Match1 parameters**

Click **Feature Model** , and select the first feature model **WIFI** , and then click **Edit Model** , as shown in Figure 7-43. In **ModelSettings** page, click **Current image** , as shown in Figure 7-44. Click **Create Rect Mask** , and drag to generate the rectangular mask to cover material. Configure the parameters in the lower right corner. Set **Scale Mode** and **Thres Mode** according to the actual condition, and click **Build Model** to generate the feature model, as shown in Figure 7-45. Finally, click **Confirm** to save the feature model.

**Figure 7-43 Feature model**

![Official CR3 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhWWUpmYBGZtsPvXXO2Kq%2Futp-f945727c2875c1ab1e23.jpg?alt=media)

![Official CR3 training-system figure, source page 172](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkU0RXC9vU7CtXh1xxvmY%2Futp-ae35946671454a94a7c1.jpg?alt=media)

**Figure 7-44 Model settings**

**Figure 7-45 Update feature model**

According to the above method, modify the feature models of CPS chip, electronic compass, light sensor, hexagon and gravity sensor following the method above.

![Official CR3 training-system figure, source page 173](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ08rotkKzx7A7BSCQ5ah%2Futp-23e7202c085ecd586421.jpg?alt=media)

![Official CR3 training-system figure, source page 173](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FV2NE52NveHSjzjlBVtHD%2Futp-38e55ac330e8b1e80dac.jpg?alt=media)

Note: The model sequence must be consistent with Figure 7-43.

（3）Debug **3 Calibration Transformation1** parameters.

Double-click **3 Calibration Transformation1** to set parameters. In **Basic Params** page, set **Coord Point** to **2 High Precision Match1.Match Point\[]** , and **Load Calibration File** select the calibration file generated by hand-eye calibration, as shown in Figure 7-46.

**Figure 7-46 Set 3 Calibration Transformation1 parameters**

（4）Debug **4 Variable Calculation1** parameters.

Double-click **4 Variable Calculation1** , and check whether the **Expression** is " **-<2 High Precision Match1.MatchBoxAngle>\[0]** ", as shown in Figure 7-47. If not, modify it to " **-<2 High Precision Match1.MatchBoxAngle>\[0]** ".

![Official CR3 training-system figure, source page 174](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fufc5HBtPhkbQq4Cltj3h%2Futp-4423c54639da2dd0e677.jpg?alt=media)

**Figure 7-47 Set 4Variable Calculation1 parameters**

（5）Debug **5 Format1** parameters.

| Double-click **5 Format1**, and check whether the parameters                                                         | are **" <2 Fast** |
| -------------------------------------------------------------------------------------------------------------------- | ----------------- |
| <p><strong>Match1.MatchModelIndex(%0d)>[0]</strong><br>，<br><strong>&#x3C;3</strong></p>                             | **Calibration**   |
| <p><strong>Transformation1.TransPointX</strong><br><strong>(%1.3f)>[0]</strong><br>，<br><strong>&#x3C;3</strong></p> | **Calibration**   |
| <p><strong>Transformation1.TransPointY(%1.3f)>[0]</strong><br>，<br><strong>&#x3C;4</strong></p>                      | **Variable**      |
| <p><strong>Calculation1.var0(%1.3f)>[0]</strong>"<br>,as shown in Figure 7-48. If not,</p>                           | modify it as the  |
| figure.                                                                                                              |                   |

![Official CR3 training-system figure, source page 175](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAHGmztVXEz9oCbnMPmkX%2Futp-0aae75b060e7b84761a6.jpg?alt=media)

**Figure 7-48 Set 5Format1 parameters**

（6）Debug **Communication Management** parameters.

Click " " in the toolbar to enter **Communication Management** page. Check whether there is created **TCP Server** , as shown in Figure 7-49. If not, you need to

re-create one, as described below. Click " " beside **Device List** . Set **Protocol Type** to **TCP Server** ; **Load IP** to **192.168.5.100** , and **Local Port** to **4001** ,then click **Create** . Switch on **1 TCP Server,** as shown in Figure 7-50.

**Figure 7-49 Communication Management parameters setting**

![Official CR3 training-system figure, source page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9rkoLD0e9G28klm1sHMe%2Futp-e3ac16dd54432fa842b5.jpg?alt=media)

![Official CR3 training-system figure, source page 176](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM0dszDqv9pkKquDu14XI%2Futp-9c077df55e81d1dab4dd.jpg?alt=media)

**Figure 7-50 Create TCP Server**

（7）Debug **6 Send Data1** parameters.

Double-click **6 Send Data1** , and check whether the parameters are shown as

Figure 7-51. If not, modify as the figure. Set **Output To** to **Communication Device** ,

**Communication Device** to **1 TCP Server** , **SendData1** to **5 Format.format\_out\[]** .

**Figure 7-51 Set "6 Send Data1 parameters"**

* （7）Global trigger settings

![Official CR3 training-system figure, source page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAghOns3nerPtHTTbGmdN%2Futp-d26ca8ca33d2831e8385.jpg?alt=media)

![Official CR3 training-system figure, source page 177](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsllCjqdC9TyEMbvmZnc5%2Futp-5c313587d87137577f89.jpg?alt=media)

Click " " in the toolbar to enter **Global Trigger** page. In **String Trigger** page, check whether the string trigger setting is shown as Figure 7-52. Set **String** to blank, **Mode** to **Mismatched** , and **Trigger Configuration** to **All Pross** .

**Figure 7-52 Set global trigger parameters**

#### 3.7.5 Save program

Click " " in the toolbar to save the program. If you need to save the program elsewhere on your local computer, click **File** > **Save as** , select the saving path and enter the name of the project.

#### 3.8 Robot Program Debugging

#### 3.8.1 Install the coaxial sucker tool

* (1) Hand tighten and remove the calibration needle, as shown in Figure 7-53.

![Official CR3 training-system figure, source page 178](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F061fPB1WZFy6feOaPFyq%2Futp-3d3e73132603ff765952.jpg?alt=media)

**Figure 7-53 Remove the calibration needle**

* （3）Then twist the sucker to the end of the robot, as shown in Figure 7-54.

**Figure 7-54 Installing sucker**

#### 3.8.2 Place the phone model and chip

Place the phone model on the phone model board, as shown in Figure 7-55.

![Official CR3 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQyjRfjUxNUnK1b6R428j%2Futp-c1d1abfcc1f2c4e72ebc.jpg?alt=media)

![Official CR3 training-system figure, source page 179](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fsh79pJpiT4H1qrMAlkDp%2Futp-6f499b3a2537858ce286.jpg?alt=media)

**Figure 7-55 Place phone model**

Place six chips on the standard visual loading board, as shown in Figure 7-56.

**Figure 7-56 Place chips within the detection view**

#### 3.8.3 Import program

(1) Open **DobotStudio Pro** and enter script page. Click **File** > **Import project** ,

as shown in Figure 7-57.

![Official CR3 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKZ21mvYLvbhFS3iDaJsp%2Futp-0d5c8254d3dfd6235259.jpg?alt=media)

![Official CR3 training-system figure, source page 180](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdSGo7QfNXNHSMpn3dlC3%2Futp-4b590299ed51f159d1c7.jpg?alt=media)

**Figure 7-57 Import project**

（2）Select **CR3Mobile Phone Chip Sorting** folder, and click **Open** , as shown in Figure 7-59. Now the phone chip assembly program has been imported into DobotStudio Pro, as shown in Figure 7-58.

**Figure 7-58 Import path**

#### 3.8.4 Debug points

* （1）Safe point P1

Move the robot between the conveyor belt and the storage area through hand-held teaching or inching control methods, as shown in Figure 7-59. Click **Points**

![Official CR3 training-system figure, source page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 181](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FA3YR9srDVRS9k8DMzu0N%2Futp-ba2b68e22d2249ad7247.png?alt=media)

in the right-side menu of DobotStudio Pro. Select **P1** and click **Cover** , as shown in Figure 7-60. Then click **OK** in the pop-up **Tips** window.

**Figure 7-59 Point P1**

**Figure 7-60 Update P1**

（2）The placement point of the first chip **P2**

Place the first chip (WIFI chip) on the phone model, and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves

![Official CR3 training-system figure, source page 182](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKexS1y4VeeQtjzaba3AL%2Futp-7866dcf15e34723bd3cc.jpg?alt=media)

![Official CR3 training-system figure, source page 182](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtqpWYkRbl2GJ0ZagUOD6%2Futp-d188c173bdd6ec728a53.jpg?alt=media)

from the point P1 to the top of the first chip on the phone model, This is shown in Figure 7-61.

**Figure 7-61 Place the WIF chip**

Adjust the Z-direction so that the end of the robot moves down and touches the first chip, then open the **IO** control panel and open the **DO\_09** signal switch to let the robot absorb the chip, as shown in Figure 7-62.

**Figure 7-62 Sucking WIFI chip**

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the WIFI chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 7-63. Then select **P2** in

![Official CR3 training-system figure, source page 183](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FlJMhnIzhzAdJV71BamQg%2Futp-1352085c139dbf47b66d.jpg?alt=media)

![Official CR3 training-system figure, source page 183](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7zt5cVz4FAoQSJeUsipg%2Futp-5d4cda359d7bc3f9205d.jpg?alt=media)

**Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 7-64.

**Figure 7-63 WIFI chip assembly point P3**

**Figure 7-64 Update P3**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second, let the end of the robot release the WIFI chip and close the sucker, and check whether the chip can be accurately placed in the groove of the phone model. If not, it needs to be adjusted again.

![Official CR3 training-system figure, source page 184](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FGShqnsnrbcws2Q4YYDPD%2Futp-ae3ecc58810e74370de3.jpg?alt=media)

![Official CR3 training-system figure, source page 184](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ffbyj7EtKVGIcis3Prf1d%2Futp-68ce08e67575515adad5.jpg?alt=media)

（3）The placement point of the second chip **P3**

Place the second chip (GPS chip) on the phone model, and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the point P1 to the top of the second chip on the phone model, This is shown in

Figure 7-61.

**Figure 7-65 Place the GPS chip**

Adjust the Z-direction so that the end of the robot moves downwards and touches the second chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the GPS chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 7-66. Then select **P3** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 7-67.

![Official CR3 training-system figure, source page 185](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrLBoq14WjBRgmKS1Flqx%2Futp-bf83facafd2c713afbb8.jpg?alt=media)

**Figure 7-66 GPS chip assembly point P3**

**Figure 7-67 Update P3**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the GPS chip is placed into the groove accurately. If not, you need to re-debug the point.

（4）The placement point of the third chip **P4**

![Official CR3 training-system figure, source page 186](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8sC2Q87J0fYIxvdHZO6T%2Futp-6e84779fed236a1531de.jpg?alt=media)

![Official CR3 training-system figure, source page 186](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOoKsXNRHvSBgpoU060jd%2Futp-7a5de67054f0d4e13ff0.jpg?alt=media)

Place the third chip (Electronic compass chip) on the phone model, and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the P1 point to the top of the third chip on the phone model, This is shown in Figure 7-68.

**Figure 7-68 Place the Electronic compass chip**

Adjust the Z-direction so that the end of the robot moves downwards and touches the third chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the electronic compass chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 7-69. Then select **P4** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 7-70.

**Figure 7-69 Electronic compass chip placement point P4**

![Official CR3 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxWaFB7VdJatO0GfKvz5I%2Futp-478d053293d7ee72911e.jpg?alt=media)

![Official CR3 training-system figure, source page 187](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoI05zoS8QEbvsW9PDvr2%2Futp-e3b087200507cc9358ff.jpg?alt=media)

**Figure 7-70 Update P3**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the electronic compass chip is placed into the groove accurately. If not, you need to re-debug the point.

（5）The placement point of the fourth chip **P5**

Place the fourth chip (Light sensor chip) on the phone model, and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the P1 point to the top of the fourth chip on the phone model, This is shown in Figure 7-71.

![Official CR3 training-system figure, source page 188](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeMv9uP0wc2YTMSLcLqyd%2Futp-43ff746d6662ee538c1c.jpg?alt=media)

**Figure 7-71 Place the light sensor chip**

Adjust the Z-direction so that the end of the robot moves downwards and touches the fourth chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the light sensor chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 7-72. Then select **P5** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 7-73.

**Figure 7-72 Light sensor chip assembly point P5**

![Official CR3 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEnBIX9GNRVsU4ES1tm91%2Futp-097c077db7ec852d003e.jpg?alt=media)

![Official CR3 training-system figure, source page 189](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FM8dM7Ro3gIbhLxzs5GoF%2Futp-55e19bfe1be1d04ec8fc.jpg?alt=media)

**Figure 7-73 Update P5**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the light sensor chip is placed into the groove accurately. If not, you need to re-debug the point.

* （6）The placement point of the fifth chip **P6**

Place the fifth chip (Hexagon chip) on the phone model，and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the P1 point to the top of the fifth chip on the phone model, This is shown in

Figure 7-74.

181<br>

![Official CR3 training-system figure, source page 190](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfsyQQhqqhapht5fjrVsK%2Futp-a07ce426f4c4b4e41ba7.jpg?alt=media)

![Official CR3 training-system figure, source page 190](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZw3x5SjijUru3NZAkvG6%2Futp-19cb1f5ba1869997fc96.jpg?alt=media)

**Figure 7-74 Place the hexagon chip**

Adjust the Z-direction so that the end of the robot moves downwards and touches the fifth chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the hexagon chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 7-75. Then select **P6** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 7-76.

**Figure 7-75 Hexagon chip assembly point P6**

![Official CR3 training-system figure, source page 191](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FECEm1nKUPe8RgikXaASI%2Futp-c9879f617edc5799d9f0.jpg?alt=media)

**Figure 7-76 Update P6**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 second set **DO\_10** to **OFF** and observe whether the hexagon chip is placed into the groove accurately. If not, you need to re-debug the point.

（7）The placement point of the sixth chip **P7**

Place the sixth chip (Gravity sensor chip) on the phone model and then in the **Control** panel, control the X/Y/Z direction by inching control method, so that the robot moves from the P1 point to the top of the sixth chip on the phone model, This is shown in Figure 7-77.

![Official CR3 training-system figure, source page 192](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FuzBwyHkZ0YPvETMDvmrc%2Futp-2fe634bcb750d5cf5efe.jpg?alt=media)

**Figure 7-77 Place the gravity sensor chip**

Adjust the Z-direction so that the end of the robot moves downwards and touches the sixth chip, then open the **IO** control panel, and then open the **DO\_09** signal switch and let the end of the robot suck the chip.

The Z-direction is controlled by inching control method, so that the end of the robot can absorb the gravity sensor chip and move up to the appropriate distance, which is the distance of the robot to place the chip, as shown in Figure 7-78. Then select **P7** in **Points** , then click **Cover** , and then click **OK** in the pop-up **Tips** interface, as shown in Figure 7-79.

**Figure 7-78 Gravity sensor chip assembly point P7**

![Official CR3 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMjio5cCAsVd9jrq0oJx4%2Futp-9422b14f4b3e86b40e2d.jpg?alt=media)

![Official CR3 training-system figure, source page 193](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4X3qTmf4xfXCkVP3UK7i%2Futp-35c30e2aa2d8845dc9a0.jpg?alt=media)

**Figure 7-79 Update P7**

Open **IO** panel. Set **DO\_09** to **OFF** , and **DO\_10** to **ON** . After 1 sixth set **DO\_10** to **OFF** and observe whether the gravity sensor chip is placed into the groove accurately. If not, you need to re-debug the point.

#### 3.8.5 Set communication

Set the IP address of the robot program to the IP address of the computer ( **192.168.5.100** ) and the port number to **4001** . Ensure that the IP address and port number of the TCP server in the robot program are consistent with the local IP address and port number in the visual communication Settings, as shown in Figure 7-80.

**Figure 7-80 Set communication**

![Official CR3 training-system figure, source page 194](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVMSzSsktB9LX4voWVaXJ%2Futp-8b231b6072e50305f853.jpg?alt=media)

#### 3.8.6 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 7-81.

**Figure 7-81 Save program**

Note: " " is for saving the program to the robot controller. If you want to save the

modified program to the local computer, you need to use " ".

#### 3.8.7 Run program

Click the " " button in DobotStudio Pro software to run the robot program. After the robot receives the coordinates of the chip sent by vision, it sips the chip from the standard visual loading board and installs it in a groove in the phone model. The mobile phone after assembly is shown in Figure 7-82.

**Figure 7-82 Phone after assembly**

![Official CR3 training-system figure, source page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FyO3jgxNToKxA5wKRo4A2%2Futp-89899ab95f24cfbe1526.jpg?alt=media)

![Official CR3 training-system figure, source page 195](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHK75j6t1iLIk3OqaxCBC%2Futp-5618c8516d6cee047688.jpg?alt=media)

#### 3.8.8 Export program

Click **File** > **Export project** , and select the path where the program is stored,

then, in the dialog box that pops up, name the program.

Note: **Export project** is to export the program to your local computer for backup.

**4. Program Description**

#### 4.1 Vision program description

The visual program is shown in Figure 7-83. **0 Image Source1** is mainly used for image acquisition. When the system is running, the camera takes pictures of the chip immediately after the vision program receives the **ok** trigger signal sent by the robot. The chip is positioned through **3 Fast Match1** to obtain the image coordinates and matching angles of the chip. Then use **4 Calibration Transformation1** to convert the image coordinates, which are obtained from **3 Fast Match1** , into actual physical coordinates. Then transform and correct the matching angle through **5 Variable Calculation1** . In **5 Format1** , summarize the template model, X/Y physical coordinates, matching angles and other information corresponding to the chip, and then use **6 Send Data1** to send these information to the robot.

**Figure 7-83 Vision program**

#### 4.2 Robot program description

#### 4.2.1 src0.lua

The relevant variables for defining the robot program are shown in Figure 7-84.

**Figure 7-84 Define the relevant variables**

Define TCP data transfer function as shown in Figure 7-85. The robot sends the signal **ok** to the vision, which is triggered by the photo, and then receives the data sent by the vision.

**Figure 7-85 Data transfer program**

The function of defining the robot to absorb the chip at the calibration point is shown in Figure 7-86. The robot absorbs the chip in the standard vision loading board according to the coordinate information sent by the vision.

![Official CR3 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FICDluwA6piqIlV4cK5TS%2Futp-1dcdc1c7803b485e92ad.jpg?alt=media)

![Official CR3 training-system figure, source page 197](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj98pO0R9hiyYdakhgq3n%2Futp-b0817af7f296bd7b8eea.jpg?alt=media)

**Figure 7-86 Robot feeding program**

The program of communication is shown in Figure 7-87, which is mainly to

create TCP client and establish a connection with TCP server (visual).

**Figure 7-87 The program of communication**

The program for resetting the relevant IO output port is shown in Figure 6-84. It

is mainly to set some output port IO signals to **0** .

**Figure 7-88 Procedure of Reset outlet**

When the **Start** button is pressed, the green light in the tricolour light lights up,

and the robot moves to the safe point P1. The program is shown in Figure 7 -89.

**Figure 7-89 Reset after waiting for DI signal**

Figure 7-91 and Figure 7-92 shows the program for the robot to assemble the chip. The program loops 6 times to let the robot obtain the coordinate information of

![Official CR3 training-system figure, source page 198](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnTLmfdxH2SfAR4vmzctR%2Futp-e14d735741632903e319.jpg?alt=media)

the chip sent by vision, and absorb the 6 chips in turn, then assemble them into the groove corresponding to the mobile phone model, and finally return to the Safe point

point P1.

**Figure 7-91 Robot placement program** （ **1** ）

![Official CR3 training-system figure, source page 199](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdAcYzeS7AE7OiEDDVpSw%2Futp-fb0c6692914ee8f89e54.jpg?alt=media)

![Official CR3 training-system figure, source page 199](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTrE0vLuXaY95PKsCNxJv%2Futp-b9e6b51bbbac642fd0f0.jpg?alt=media)

#### 4.2.2 global.lua

The function defining the string segmentation is shown in Figure 7-93. This

function is used to process the data sent by the visual side.

**Figure 7-93 Defines a function to split strings**

The function defining the waiting DI signal is shown in Figure 7 -94. This

function is used to wait for an external signal input.

**Figure 7-94 Define the function that waits for the DI signal**

![Official CR3 training-system figure, source page 200](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqcJA7Q3Th2vyaVrzS6Lw%2Futp-2d53f13b285afd7326ea.jpg?alt=media)

## Chapter 8 Dynamic tracking application

**1. Introduction**

Dynamic tracking is a process in which a robot calculates the real-time position of an object in the robot coordinate system based on the position information fed back by the visual system or photoelectric sensor, combined with the position data fed back by the conveyor belt encoder. By using tracking algorithms to predict the position of objects on the conveyor belt and adjusting their own movement speed and end pose in real-time, the moving objects on the conveyor belt are tracked, ultimately achieving dynamic tracking and grasping of the target object.

The dynamic tracking tasks to be realized in this chapter are as follows: when the system is started, the pushing motor pushes the round workpiece in the feeding well to the conveyor belt; when the workpiece reaches the visual detection area, the vision positions the workpiece visually and sends the coordinates to the robot; after receiving the information, the robot follows the movement of the workpiece, then reaches the specified grasping point, and the sucks up the circular workpiece on the moving conveyor belt, as shown in Figure 8-1, and finally places it in the circular groove in the storage area.

**Figure 8-1 Dynamic palletizing**

### 2. **IO Configuration**

The IO configuration of dynamic tracking application is shown in Table 8-1.

**Table 8-1 IO configuration of dynamic tracking application**

![Official CR3 training-system figure, source page 201](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDkS9zqQeYZ66DltgBr2Z%2Futp-efeab3689ee1ce1af950.png?alt=media)

**CR3 General Training System Operation Instruction**

| **DI** | **Description**                                            | **DO** | **Description**                                |
| ------ | ---------------------------------------------------------- | ------ | ---------------------------------------------- |
| DI6    | <p>Detect whether there are<br>blocks in the stock bin</p> | DO2    | Enable push motor                              |
| DI7    | Photo detection                                            | DO3    | Direction of push motor                        |
| DI8    | In-place detection                                         | DO4    | Conveyor moves forward                         |
| DI9    | Front stop of push motor                                   | DO5    | Conveyor moves backward                        |
| DI10   | Back stop of push motor                                    | DO6    | <p>Green LED light + green<br>button light</p> |
| DI16   | Emergency stop                                             | DO7    | <p>Yellow LED light + blue<br>button light</p> |
|        |                                                            | DO8    | <p>Red LED light + red button<br>light</p>     |
|        |                                                            | DO9    | Buzzer                                         |
|        |                                                            | DO10   | Vacuum pumping                                 |
|        |                                                            | DO11   | Vacuum breaking                                |

**3. Program Debugging**

#### 3.1 Preparation

#### 3.1.1 Turn on CR3 general training system power switch

Connect the CR3 to the power supply, and turn on the power switch of the CR3

general training system, as shown in Figure 8-2.

**Figure 8-2 CR3 general training system power switch**

#### 3.1.2 Turn on the air pump box switch

urn on the power switch of the air pump box and rotate the control button to

**Auto** , as shown in Figure8-3.

![Official CR3 training-system figure, source page 202](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVv3xfRTGdCXB1gtLZ6FI%2Futp-44489226e5513b810567.jpg?alt=media)

**Figure 8-3 air pump box**

#### 3.1.3 Turn on the light source switch

Turn on the light source switch, as shown in Figure 8-4.

**Figure 8-4 Light source switch**

#### 3.2 Connect camera

Plug the dongle of DobotVisionStudio into the computer. Plug the USB cable of the training system (used to connect the camera) into the computer.

#### 3.3 Connect robot

* (1) Power on the robot.

Check whether the power switch of the robot controller and the robot switch are turned on. If not, all switches need to be turned on, as shown in Figure 8-5.

![Official CR3 training-system figure, source page 203](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMm3WSG8sjLeWuIAbArPE%2Futp-f432b12a339c15ee8bcd.jpg?alt=media)

![Official CR3 training-system figure, source page 203](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3y1I9YDtAWjvsZ8KCzRQ%2Futp-1aacd46a70c34f01e0e9.jpg?alt=media)

**Figure 8-5 Robot control cabinet**

(2) Connect the robot to the computer.

Connect one end of the network cable to the LAN interface of the robot controller, and the other end to the computer.

* (3) Change the IP address of the computer.

Open the control panel of the computer. Select **Network and Internet/Network and Sharing Centre** to enter the corresponding window. **Click Ethernet** and select **Properties** to enter the Ethernet Properties page. Double-click Internet **Protocol Version 4 (TCP/IPv4)** . Reset the IP address, As shown in Figure 8-6. The default address of the robot is "192.168.5.1". You can change The IP address of The PC to any 9 IP address that is not occupied on the same network segment as the robot. Its subnet mask and default gateway are "Consistent with those of the robot. Here takes" 192.168.5.100 "as an example.

![Official CR3 training-system figure, source page 204](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FCB9qFPgMJHH8gxO2EQoT%2Futp-dce5e7af81a8e8c5b274.jpg?alt=media)

**Figure 8-6 IP setting of PC**

* (4)Connect **DobotStudio Pro** to the Robot

Double-click **DobotStudio Pro V2.6.1** to open the software. Select **CR3** on the

top Toolbar, and click **Connect** , as shown in Figure 8-7.

**Figure 8-7 Connect robot**

After successful connection, you will see a prompt message, and the connection

status will change to **Connected** , as shown in Figure 8-8.

![Official CR3 training-system figure, source page 205](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ft5P2WygcLRwtOb3LhbOt%2Futp-117c4ca7b1cb1485bc86.png?alt=media)

![Official CR3 training-system figure, source page 205](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T1tjOq0oHryI7Il585q%2Futp-648ebc56c8331a4951ec.jpg?alt=media)

**Figure 8-8 Robot connected**

#### 3.4 Enable robot

Click the enable icon " " in the top toolbar of the DobotStudio Pro interface, and set the weight of the end load to **1kg** in the load parameter setting window that pops up. The other parameters remain unchanged by default, as shown in Figure 8-9.

Then click **Confirm modification** , the enable icon becomes " ".

**Figure 8-9 Set load parameters**

#### 3.5 Set speed

Click on the **Global Speed** button in the top toolbar of the DobotStudio Pro interface and set the speed to 30%, as shown in Figure 8-10.

**Figure 8-10 Global rate settings**

![Official CR3 training-system figure, source page 206](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVHNsbBFGYkrJVJlVZTEX%2Futp-208ad0a3eb724405fb65.jpg?alt=media)

#### 3.6 Adjust the initial pose of the robot

* (1) Select **Setting>Basic** .
* (2) Check if the joint coordinate of the robot is as shown in Figure 8-11, and then

click **Move to Default Pose** to control the robot and make it move to its initial position. If the joint coordinate of the robot is incorrect, you need to click **Restore Default Pose** to modify the robot's joint coordinate.

**Figure 8-11 Adjusting the initial pose of the robot**

#### 3.7 Debug vision program

#### 3.7.1 Import program

Open the DobotVisionStudio software and select **General Solution** . Select **Open** from the shortcut toolbar, locate the visual program for the dynamic tracking application, and click **Open** . The imported visual program is shown in Figure 8-12.

![Official CR3 training-system figure, source page 207](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzVK8INJdd17hdZCixXY7%2Futp-52c5669db89df373518a.png?alt=media)

**Figure 8-12 Imported vision program**

#### 3.7.2 Place blocks

Place a circular workpiece within the visual inspection range on the conveyor

belt, as shown in Figure 8-13.

**Figure 8-13 Place circular block within the detection view**

#### 3.7.3 Debug parameters

(1) Debug **0 Image Source1** parameters.

![Official CR3 training-system figure, source page 208](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FC4HOIxc5NuZoMRTgbK9O%2Futp-c63c82c8fed81fef4462.jpg?alt=media)

![Official CR3 training-system figure, source page 208](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Ftc3Xq8XCUwCyaexCU9YM%2Futp-888ef7bf44bafab7be3e.jpg?alt=media)

Click " **(Once)** ", select **0 Image Source1** and observe whether the image is clear. If the image is not clear or there is no image, you need to adjust **0 Image Source1** .

Double-click **0 Image Source1** to enter the corresponding parameter setting page. Select **Camera** for **Image Source** , as shown in Figure 8-14. Check whether there is related camera in **Relate Camera** . If not, click **Camera set** on the right side of relate camera to create a global camera.

**Figure 8-14 Set 0 Image Source1 parameters**

In the **Camera Set** page, click " **+** " on the right side of **Device List** to create **1 Global Camera1** and set the parameters of the camera. In the **Common Params** tab, click the triangle in the lower right corner of **Choose Camera** to open the drop-down list and select the camera that is currently connected to the computer. Select **Mono8** for **Pixel Format** , as shown in Figure 8-15. Click **Trigger Settings** tab, and set **Trigger Source** to **SOFTWARE** . Then click **Confirm** , as shown in Figure 8-16. In **0 Image Source** page, click the triangle in the lower right corner of **Relate Camera** and select **1Global Camera1** , as shown in Figure 8-17.

![Official CR3 training-system figure, source page 209](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoO2B5F62t2cMOwLMCMj0%2Futp-d30f26b70bbbbf837708.png?alt=media)

**Figure 8-15 Camera Set common parameters**

**Figure 8-16 Camera Set trigger setting**

![Official CR3 training-system figure, source page 210](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FpvfQCyKsLhCU8Dyl1iSF%2Futp-5bce1e064af32a01bba6.jpg?alt=media)

![Official CR3 training-system figure, source page 210](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDIIOWMraRE5jeh4J84mc%2Futp-e3f076bf49cb5ff64f1c.jpg?alt=media)

**Figure 8-17 Image source related camera**

Click " **(Continuously)** " to adjust the aperture and focusing ring of the lens,

and adjust the exposure time of the camera until a clear image is obtained in the image display area. The image acquisition results are shown in Figure 8-18.

**Figure 8-18 Image acquisition result**

If there is a global cameras in **Relate Camera** , you can select it directly through the drop-down list. Then click **Camera set** on the right side of **Relate Camera** to

![Official CR3 training-system figure, source page 211](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0KIGoI3XUG20X0DrXDRJ%2Futp-6b20bb76fefb77320e71.jpg?alt=media)

![Official CR3 training-system figure, source page 211](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1OMoqMvVfHbdBz73C1yN%2Futp-76c8777c7bf88a78a318.jpg?alt=media)

enter the “Camera Set” page. Check whether the camera parameters are set as shown in Figure 8-15 and Figure 8-16. If inconsistent, modify as the figure. If consistent, click **Once** to see whether the image captured by the camera is clear. If not, adjust the lens aperture, focus ring and exposure time.

Note: Do not set the exposure time of the camera too long as the camera takes photos dynamically during dynamic tracking. Too long exposure time will cause the vision system not to accurately recognize the circular blocks. Therefore, dynamic tracking requires good light conditions.

(2) Debug **2 Fast Match1** parameters.

Click " **(Once)** ". Select **2 Fast Match1** and observe whether the circular block can be recognized accurately. If it cannot be accurately identified, it is necessary to modify the parameters of **2 Fast Match1** . The **Basic Params** interface settings are shown in Figure 8-19.

**Figure 8-19 Set 2 Fast Match1 parameters**

Click **Feature Model** , and select the feature model, and then click **Edit Model** , as shown in Figure 8-20. In **ModelSettings** page, click **Current image** , as shown in Figure 8-21. Click **Create Rect Mask** , and drag to generate the circular mask to cover the circular block. Configure parameters in the lower right corner, set appropriate roughness scale and contrast threshold according to the actual situation, and click the

![Official CR3 training-system figure, source page 212](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FhWWUpmYBGZtsPvXXO2Kq%2Futp-f945727c2875c1ab1e23.jpg?alt=media)

**Build Model** button to generate a feature model, as shown in Figure 8-22. Finally, click the **Confirm** button to save the feature template.

Due to the influence of light, several feature models can be added to facilitate

dynamic visual recognition.

**Figure 8-20 Feature Model**

**Figure 8-21 ModelSettings**

![Official CR3 training-system figure, source page 213](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FwnwaiZZd3DeWsklcBssN%2Futp-87a8bb0ff48a3b64e610.jpg?alt=media)

![Official CR3 training-system figure, source page 213](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fz0rA1y3k2wkPKT3G5Zpe%2Futp-4121c19a8e0b61504a82.jpg?alt=media)

**Figure 8-22 Update feature model**

(3) Debug **3 Branch1** parameters.

Double-click **3 Branch1** , and check whether the parameters are shown as Figure 8-23. If not, modify as the figure. Then set **Condition Input** to **2 Fast Match1.MatchNum\[]** , **Module ID: 4** to **1** , and **Module ID: 6** to **0** .

**Figure 8-23 Set 3 Branch1 parameters**

![Official CR3 training-system figure, source page 214](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzdZslgMiSx7G885k0WjD%2Futp-531269eb932ee49ec815.jpg?alt=media)

![Official CR3 training-system figure, source page 214](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6wVnkKZ9iqhhue3VMktF%2Futp-479300e7e8609e1e6966.jpg?alt=media)

* (4) Debug **4 Format1** parameters.

Double-click **4 Format1** , and check whether the parameters are " **0; <2 Fast Match1.MatchPointX(%1.3f)>\[0], <2 Fast Match1.MatchPointY(%1.3f)>\[0], 0,**

**1&** ", as shown in Figure 8-24. If not, modify as the figure.

**Figure 8-24 Set 4 Format1 parameters**

* (5) Debug **6 Format2** parameters.

Double-click **6 Format2** , and check whether the parameters are shown as Figure

* 8-25. If not, modify as the figure.

![Official CR3 training-system figure, source page 215](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Frda1kkZfqxJiJp9LGu2s%2Futp-032756ea05cf79d7186f.jpg?alt=media)

**Figure 8-25 Set 6 Format2 parameters**

* （6）Debug **Communication Management** parameters.

Click " " in the toolbar to enter **Communication Management** page. Check whether there is created **ConveyorCAM** , as shown in Figure 8-26. If not, you need to

re-create one, recreate it as follows: Click " " beside **Device List** . Set **Protocol Type** to **TCP Client** , **Load IP** to **192.168.5.1** , and **Local Port** to **8080** . Then click **Create** . Finally, turn on the switch next to **ConveyorCAM** , as shown in Figure 8-27.

**Figure 8-26 "Communication Management" parameters setting**

![Official CR3 training-system figure, source page 216](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHN6HnB5zax8BsP0Smkgf%2Futp-f46707405a52ccc85e94.jpg?alt=media)

![Official CR3 training-system figure, source page 216](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxG7WTTq9JDh1A0bjs5al%2Futp-8b6f8cbe22c4119b1349.jpg?alt=media)

**Figure 8-27 Create TCP client**

（7）Debug **5 Send Data1** parameters.

Double-click **5 Send Data1** , and check whether the parameters are shown as Figure 8-28. If not, modify as the figure. Set **Output To Communication Device** , **Communication Device** to **1 ConveyorCAM** , and **SendData1** to **4 Format1.format\_out\[]** .

**Figure 8-28 Set 5 Send Data1 parameters**

(8) Debug **7 Send Data2** parameters.

![Official CR3 training-system figure, source page 217](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKZvuA9cI4NTOHfFoBH6Y%2Futp-50e0377a4c81ebf188cd.jpg?alt=media)

![Official CR3 training-system figure, source page 217](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHAc5YHOvMdJxUGjzwZ4y%2Futp-2fb1d0c9d4db07414533.jpg?alt=media)

Double-click **7 Send Data2** , and check whether the parameters are shown as Figure 8-29. If not, modify as the figure. Set **Output** to **Communication Device** , **Communication Device** to **1 ConveyorCAM** , and **SendData1** to **6 Format2.format\_out\[]** .

**Figure 8-29 Set 7 Send Data5 parameters**

* (9) Global trigger settings

Click " " in the quick toolbar to enter **Global Trigger** page. In **String Trigger** page, check whether the string trigger setting is shown as Figure 8-30. Set

**String** to blank, **Mode** to **Mismatched** , and **Trigger Configuration** to **All Pross** .

![Official CR3 training-system figure, source page 218](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1HDjilu8UdZv58VW7QJE%2Futp-50358134abd78faefa9c.jpg?alt=media)

**Figure 8-30 Set Global Trigger parameters**

(10) Modify **Trigger Source**

Click " " in the toolbar to enter **Camera set** page. Click **1 Global Camera1** . Click **Trigger Settings** , and set **Trigger Source** to **LINE0** . Then click **Confirm** , as shown in Figure 8-31.

**Figure 8-31 Modify "Trigger Source" parameters**

![Official CR3 training-system figure, source page 219](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F061fPB1WZFy6feOaPFyq%2Futp-3d3e73132603ff765952.jpg?alt=media)

![Official CR3 training-system figure, source page 219](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsDeZPNeyNaaVJ32qQ7xs%2Futp-39a86d4c3c60ccb0690e.jpg?alt=media)

Note: During dynamic tracking, the material reaches the material photo sensing point on the conveyor belt, triggering the camera to take photos. Therefore, this is a hardware triggered method.

#### 3.7.4 Save program

Click " " in the toolbar to save the program. If you need to save the program somewhere else on your local computer, click **File** > **Save as** , then select the path to save it, and then name the program.

#### 3.8 Robot program debugging

#### 3.8.1 Install calibration needle

Remove the sucker at the end of the robot, as shown in Figure 8-32.

**Figure 8-32 Remove the end of the sucker**

Install the prepared calibration needle onto the end of the robot, as shown in

Figure 8-33.

![Official CR3 training-system figure, source page 220](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Foz1fQrj3lE4qhQz9CBUH%2Futp-a2c5bdb58db0f2ca8618.jpg?alt=media)

**Figure 8-33 Install calibration needle**

#### 3.8.2 Create a user coordinate system

Before the robot tracks objects on the conveyor belt, it needs to set up a **user coordinate system** to calibrate the conveyor belt, which is used to describe the relative relationship between the conveyor belt and the robot. During the calibration process, the **user coordinate system** is used for calibration, and it is assumed that the positive direction of the X-axis in the **base coordinate system** coincides with the direction of the conveyor belt movement. That is, the conveyor belt calibration needs to first create a **user coordinate system** , and then perform dynamic tracking settings. **User coordinate system** is generated by three-point calibration method, as shown in Figure 8-34.

**Figure 8-34 Three-point calibration method**

According to the three-point calibration method, determine the direction of **user coordinate system** 1, as shown in Figure 8 -35. Where point A is the origin, the line between two points A and B can determine the positive X-axis direction of **user**

![Official CR3 training-system figure, source page 221](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUdzFAkMnuAIMcggIG3MD%2Futp-3dae1313a7ae54303788.jpg?alt=media)

![Official CR3 training-system figure, source page 221](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FQ3jrT1Kj1fHfZ6NXoFTJ%2Futp-a0450f1f17023940ef2a.jpg?alt=media)

**coordinate system** 1. After determining the point C, make a vertical line along the X-axis and determine the positive direction of the Y-axis. According to the right-hand rule, determine the direction of the Z-axis. The specific process is as follows.

**Figure 8-35 User coordinate system**

* (1) Select **Setting>Coordinate Syestem>User Frame** .

(2) Select **user coordinate system 1** , and click **Modify** to update the coordinate

system (if there is only **user coordinate system 0** , you can click **Add** to add a coordinate system), as shown in Figure 8-36. In the pop-up setting interface, select

**Three points setting** , as shown in Figure 8-37.

**Figure 8-36 Modify user coordinate system 1**

![Official CR3 training-system figure, source page 222](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfunWiY2gHaC2rDsyvcfM%2Futp-30f33c7323072806fb07.png?alt=media)

![Official CR3 training-system figure, source page 222](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fj8i8OjrUxFwdnenjFs0R%2Futp-daa264147537ee2e23bd.jpg?alt=media)

**Figure 8-37 Select Three points setting**

* (3) Place the calibration board on the conveyor, as shown in Figure 8-38.

**Figure 8-38 Calibration board placing position**

(4) The robot is controlled to move to point A (assumed to be point A) in the middle of the calibration paper on the conveyor belt by hand-held teaching or inching

![Official CR3 training-system figure, source page 223](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbbYYK4IBqQuJVuWnaqS5%2Futp-c1fa350ad4646b03a995.jpg?alt=media)

![Official CR3 training-system figure, source page 223](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPnzXoKE9Vlh9G05SwNjt%2Futp-005ed05992e8964e598d.jpg?alt=media)

control methods, as shown in Figure 8-39. Click **obtion** to obtain the coordinates of the first target point, as shown in Figure 8-40.

**Figure 8-39 Control the robot to move to the first point of calibration (point A).**

**Figure 8-40 Obtain "P1Jog"**

(5) Set **DO04** to **ON** in **IO** panel, and let the conveyor belt move forward with the calibration paper for a certain distance, and then turn off the switch of **DO\_02** , as shown in Figure 8-41.

![Official CR3 training-system figure, source page 224](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F17Xbr1YxkeKXe22A9Q8F%2Futp-365226657abb0ed8f1c5.jpg?alt=media)

![Official CR3 training-system figure, source page 224](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPeANIttQ2kjjoBZAmwNc%2Futp-40fbb2805b95bdf87dba.jpg?alt=media)

**Figure 8-41 Control the conveyor for a certain distance**

(6) The robot is moved to the point in the middle of the calibration paper on the conveyor belt (suppose it is point B) by inching control method, as shown in Figure 8-42. Click **obtion** to obtain the coordinates of the second point, as shown in Figure 8-43.

**Figure 8-42 Control the robot to move to the second point of calibration (point B)**

![Official CR3 training-system figure, source page 225](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJcZIKgMuI75Nbm5rIjoy%2Futp-23b91948f13bcfd31be0.jpg?alt=media)

![Official CR3 training-system figure, source page 225](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYltVp6qvImIB5hhqlNmA%2Futp-a0035d60a31ba7151783.png?alt=media)

![Official CR3 training-system figure, source page 225](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRoncyW4OP9aw4DhmuQH6%2Futp-e7ff2cca8873549e2b70.jpg?alt=media)

**Figure 8-43 Obtain P2Jog**

(7) Continue to use the inching control method to move the robot to any position on the conveyor belt except for the straight line determined by point A and B, and obtain the third point (point C, used to determine the Y-axis), as shown in Figure 8-44. Click **object** to obtain the coordinates of the third calibration point, as shown in Figure 8-45.

**Figure 8-44 Control the robot to move to the third point of calibration (Point C)**

![Official CR3 training-system figure, source page 226](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzFP28pSF0ld5Q39emAMC%2Futp-47bffadbc382cb289b34.jpg?alt=media)

![Official CR3 training-system figure, source page 226](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fuk6zWvBIBrVv6DBEuqV4%2Futp-46a161499fdfa02847e0.jpg?alt=media)

**Figure 8-45 Obtain P3Jog**

(8) Click **OK** , and **user coordinate system 1** will be created. Modify **User Frame** to **1** in **Control** , as shown in Figure 8-46. Click on **"x+"** to see the robot moving in the forward direction of the conveyor belt.

**Figure 8-46 Select User coordinate system 1**

#### 3.8.3 Dynamic tracking process configuration

(1) Basic setting

![Official CR3 training-system figure, source page 227](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fb3Zz0HfCUjRh6puvaAf4%2Futp-92970e68fd7df83e897b.jpg?alt=media)

![Official CR3 training-system figure, source page 227](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfDEekBDrLszWRWm1GcEP%2Futp-37817f370d3042064970.jpg?alt=media)

Set the user coordinate system to **0** . Select **Process** in **Homepage** , then select **Conveyor** in **Process** page, and click **Open Tool** to enter **Base** page. **User Coord Index** selects **1** and **Data Sources** selects **Camera** , as shown in Figure 8 -47.

**Figure 8-47 Basic setting**

* (2) Encoder setting
* ① Click **Encoder** to enter the corresponding page, as shown in Figure 8-48.

**Figure 8-48 Encoder setting**

②Attach the calibration board to the conveyor. The robot is moved to a point in the middle of the calibration paper on the conveyor belt through inching control

![Official CR3 training-system figure, source page 228](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F7ZBnz6Wm0Ub1SgQphVsV%2Futp-941da751db07797f42fd.jpg?alt=media)

![Official CR3 training-system figure, source page 228](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOpsgLsT1agE02VXol004%2Futp-f05d0987261bfc036673.jpg?alt=media)

method, as shown in Figure 8-49. Click **1** in the encoder setting interface to obtain the coordinates of the first point and the encoder code, as shown in Figure 8-50.

**Figure 8-49 Encoder setting-first point**

**Figure 8-50 Coordinates and code of first point**

③ In the **I/O** page, set **DO\_09** to **ON** , and the conveyor belt carrying the calibration board will move forward for a certain distance, and then set **DO\_09** to off **.** The robot is moved to a point in the middle of the calibration paper on the conveyor belt by through inching control method, as shown in Figure 8-51. Click **2** below the position on the encoder setting interface to obtain the coordinates of the second point and the encoder code, as shown in Figure 8-52.

![Official CR3 training-system figure, source page 229](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FBX48CONSXmCGcE61rDHB%2Futp-7363e8ac42a7e3624067.jpg?alt=media)

![Official CR3 training-system figure, source page 229](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FWufWVjHyqg9AQ6izokEw%2Futp-abb6284a7ac598dd3c65.jpg?alt=media)

**Figure 8-51 Encoder setting-second point**

**Figure 8-52 Coordinates and code of second point**

④ Click **Calculation** to obtain the resolution of the encoder. The resolution of the encoder is the pulse increment of the encoder when the conveyor belt moves a unit length (mm), as shown in Figure 8-53.

![Official CR3 training-system figure, source page 230](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeoRiF0YXTQQFt68YNvK0%2Futp-f117024fa9a968fe8503.jpg?alt=media)

![Official CR3 training-system figure, source page 230](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FRR7MDHPnvopYz3QOvWTm%2Futp-e16899b878010e8f2f64.jpg?alt=media)

**Figure 8-53 Calculate encoder resolution**

Note: The calculation result of **Encoder Resolution** should be within 20\~22. If it is not in

this range, you need to re-obtain the coordinates and codes of the two points.

* (3) Camera calibration
* ①Basic setting

Click **Camera** to enter the camera settings interface. In the **Base** column, set the width to **2592** , the height to **1944** , the **Trigger** to **8** , the **Interval** to **15mm** , and the

**Repeat Thresh** to **10mm** , as shown in Figure 8-54.

**Figure 8-54 Camera basic setting**

![Official CR3 training-system figure, source page 231](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVLSNja7pDpkI6RcU1Alk%2Futp-1248e4421c433e7c2265.png?alt=media)

![Official CR3 training-system figure, source page 231](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUb94YlakkqJ3NDE3PBKa%2Futp-b4e39c065feb2a40bd83.jpg?alt=media)

Note: The values of width and height are the length and width of the camera's resolution.

* ②Calibration

Place the calibration board on the conveyor belt and within the camera's field of view, as shown in Figure 8-55. Click **Calibration** to enter the calibration interface and record the current encoder value by clicking **Conveyor Pos** , as shown in Figure

8-56.

**Figure 8-55 Calibration board position**

**Figure 8-56 Obtain conveyor belt position 1**

![Official CR3 training-system figure, source page 232](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0jewBuqwStdWJst6zoWx%2Futp-e92f59d8cb0bba7bbf16.jpg?alt=media)

![Official CR3 training-system figure, source page 232](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9ZCn3l7oH9XE6WyxxTvr%2Futp-cab81eb3679b7c188490.jpg?alt=media)

Fill in the image coordinate values of 9 calibration points. The method for obtaining image coordinates of 9 calibration points is as follows:

Step 1: Open DobotVisionStudio software, and select **General Solution** . Step 2: Establish the solution process. In the toolbox, drag the **Image Source** tool from the **Acquisition** sub toolbox to the process editing area, as shown in Figure 8-57.

**Figure 8-57 Solution process**

The parameter setting of **0 Image Source1** can be seen in 3.6.4. After setting,

Click " ( **Continuously)** ", and adjust the aperture and focus ring of the lens and the exposure time of the camera until you can see a clear image in the image display area. The image collection result is shown in Figure 8-58.

![Official CR3 training-system figure, source page 233](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FUxqe4sO6ePG9ltCSLTSm%2Futp-74da5aad8c09a5020cf7.jpg?alt=media)

![Official CR3 training-system figure, source page 233](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F6ZrQNdPq1lLG8O45A5KJ%2Futp-23362a809c81f9fadd6a.jpg?alt=media)

Step 3: Add **calibration of calibration board** tool in the solution process. Drag the **CalibBoard Calib** tool from the **Calibration** sub toolbox to the process editing area and connect it to **0 Image Source1** , as shown in Figure 8-59.

**Figure 8-59 Process**

Note: The calibration of the calibration board is used to obtain the calibration point, and provide the pixel coordinates of the calibration point for N-point calibration.

Click " ( **Continuously)** ". The execution results of **CalibBoard Calib** are shown in

Figure 8-60, and the 9 calibration points are displayed.

**Figure 8-60 CalibBoard Calib execution result**

Step 5:Add **N-point Calibration** in the solution process.

Drag the **N-point Calibration** tool from the **Calibration** sub toolbox to the

process editing area and connect it to **2 CalibBoard Calib1** .

![Official CR3 training-system figure, source page 234](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FmXEaiUOSvmVSbk7Dq5r1%2Futp-5dd69b7ba3e8a7ffcbc5.jpg?alt=media)

**Figure 8-61 Flow**

After **3N-point Calibration1** is connected to **2 CalibBoard Calib1** , click the

" ( **Once)** " button. In the image display area, the nine calibration points and its calibration sequence will be automatically displayed, as shown in Figure 8-62.

**Figure 8-62 Check nine calibration points and calibration sequence**

Basic parameter settings for **3N-point Calibration1** . Double-click **3N-point Calibration** to set basic parameters. Set **Translation Number** in **Basic Params** . Keep the default parameter 9 and set **Rotation Number** . Click the icon " " to the right of translation number, as shown in Figure 8-63. The **Edit Calibration Point** interface that pops up allows you to edit the calibration points, as shown in Figure 8-64.

![Official CR3 training-system figure, source page 235](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FjxkRx1mdn5hpbSh8VW2n%2Futp-59ca0829ae3ef7abdefe.jpg?alt=media)

**Figure 8-63 3N calibration parameter setting**

**Figure 8-64 Edit Calibration Points**

In **Edit Calibration Points** page, exchange Line 3 (ID: 3) and Line 5 (ID: 5) data, as shown in Figure 8-65.

![Official CR3 training-system figure, source page 236](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3pXuMWByFUXlA7INC8zg%2Futp-cb8f2e2c9d47b3e81248.jpg?alt=media)

![Official CR3 training-system figure, source page 236](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkSKilxzj2aGekKjWfajp%2Futp-774c2be3d8b80580bc76.jpg?alt=media)

**Figure 8-65 “Edit Calibration Points” after data exchange**

After clicking the " (Once)", you can see that the calibration sequence turns into the font **2** in the image display area, as shown in Figure 8-66.

(Once)", you can see that the calibration sequence turns

**Figure 8-66 New calibration sequence**

In the calibration interface, fill the image coordinate X and image coordinate Y in the **Edit Calibration Points** column into the corresponding number X and Y, as shown in Figure 8-67. After filling out the 9 positions, click "Conveyor Pos" to get the current encoder value,then click **Next** .

![Official CR3 training-system figure, source page 237](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtDotDkczJ5Vao1QziVlE%2Futp-02423ed1d84634ada567.jpg?alt=media)

![Official CR3 training-system figure, source page 237](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FcnHfKhZU0EQ96sKObGck%2Futp-b89abe8481b985655df9.jpg?alt=media)

**Figure 8-67 Fill image coordinates of 9 calibration points**

In the **IO** control panel, open the **DO\_02** switch, and start the conveyor belt, then wait for the calibration paper to move with the conveyor belt to the front of the robot, and then stop the conveyor belt, as shown in Figure 8-68. In Calibration panel, click **Conveyor Pos** to obtain the current encoder value, as shown in Figure 8-69.

**Figure 8-68 Conveyor moves some distance**

![Official CR3 training-system figure, source page 238](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD3N2dLdCiaGdDnvbzlxg%2Futp-e1df96bbef8a5707b54b.jpg?alt=media)

![Official CR3 training-system figure, source page 238](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fptcs7GvOcTGf2k8f4ujI%2Futp-3ffd132b21511dd67aa6.jpg?alt=media)

**Figure 8-69 Obtain conveyor position 2**

Through inching control methods, let the robot to the corresponding 9 standard points on the calibration paper (the order must be the same as the order of visual calibration). Click the **1** \~ **9** buttons to obtain the coordinates of the robot, and then fill in the corresponding position, as shown in Figure 8-70. Then click **Calculation** . In this way, you can calculate the Cartesian coordinates of the 9 points of the calibration board at the photography position based on the image coordinates, corresponding Cartesian coordinates and the moving distance of the conveyor, and get the correspondence between the image coordinates and Cartesian coordinates.

**Figure 8-70 Fill physical coordinates of 9 calibration points**

* （4）Set working boundary

Click **Border** to set the working boundary.

![Official CR3 training-system figure, source page 239](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FkcfotXF3764od0QOdPeY%2Futp-4390bb3bdc0ad0ec3dbe.jpg?alt=media)

![Official CR3 training-system figure, source page 239](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FMTplLV4rRMBcQoo2ngij%2Futp-5fb6427a1e441850da5e.png?alt=media)

**①Set Working upstream limit**

By inching control methods, control the robot to reach the **Working upstream limit** position, as shown in Figure 8-71. Then click **Working upstream limit** to obtain the current boundary value, as shown in Figure 8-72.

**Figure 8-71 Working upstream limit position**

**Figure 8-72 Obtain working upstream limit**

**②Set Pickup downstream limit**

By inching control methods, control the robot to reach the **Pickup downstream limit** position, as shown in Figure 8-73. Then click on the **Pickup downstream limit**

![Official CR3 training-system figure, source page 240](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fr6HW5PcylsNPO9rsyWdX%2Futp-5687069517d27c183ac2.jpg?alt=media)

![Official CR3 training-system figure, source page 240](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzjzWJ8BNK0h5WyRqC1yY%2Futp-d25c91d4381bccf48d35.jpg?alt=media)

in the work boundary calibration interface to obtain the boundary value at this time, as shown in Figure 8-74.

**Figure 8-73 Pickup downstream limit**

**Figure 8-74 Obtain pickup downstream limit**

**③Set Working dowstream limit**

By inching control methods, control the robot to reach the **Working**

**downstream limit** , as shown in Figure 8-75. Then click on **Working downstream limit** in the work boundary calibration interface to obtain the boundary value at this time, as shown in Figure 8-76.

![Official CR3 training-system figure, source page 241](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxKT0wGwpUBNxxeHeKbLJ%2Futp-d4c20a8756eb0d09935f.jpg?alt=media)

![Official CR3 training-system figure, source page 241](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNxnGtoV9t2fxzh16UGlk%2Futp-04c642454af9267a8e1d.jpg?alt=media)

**Figure 8-75 Obtain the value of "Working dowstream limit"**

**Figure 8-76 Obtain working downstream limit**

After setting **Working downstream limit** , click **Save** . Click **OK** in the dialog box that pops up, as shown in Figure 8-77, to complete the **Border** setting.

![Official CR3 training-system figure, source page 242](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNmJdMR930HIZGqxpbmyJ%2Futp-c1ede0796609b0ac3a09.jpg?alt=media)

![Official CR3 training-system figure, source page 242](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F8YNhcKqqAUgFWOsCeYxP%2Futp-624e1c7a3df5d6d011ee.jpg?alt=media)

**Figure 8-77 Save working boundary**

#### 3.8.4 Install the coaxial sucker tool

* (1) Twist and remove the calibration needle by hand, as shown in Figure 8-78.

**Figure 8-78 remove the calibration needle**

(2) Then twist the sucker to the end of the robot, as shown in Figure 8-79.

![Official CR3 training-system figure, source page 243](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqCCijkjrJQePcvBtdg3f%2Futp-88053059899e1ae7513e.jpg?alt=media)

![Official CR3 training-system figure, source page 243](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FF4NvXYfRBHQECPho9CMI%2Futp-2bc23a197ff866ff1ce4.jpg?alt=media)

**Figure 8-79 Mounting the suction cup**

#### 3.8.5 Import program

(1) Open **DobotStudio Pro** and enter script page. Click **File** > **Import project** ,

as shown in Figure 8-80.

**Figure 8-80 Import robot project**

(2) Select the **CR3 Vision Sorting** folder and click **Open** , as shown in Figure 8-81. In this way, the dynamic tracking application program is imported into DobotStudio Pro.

![Official CR3 training-system figure, source page 244](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO8XlpMDjwRsAqEqxcQyf%2Futp-f4d1111aa97559d3f0c3.jpg?alt=media)

![Official CR3 training-system figure, source page 244](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdNohPQYIzgN7G8Zt1aUH%2Futp-2c5bff46ca26044eab53.jpg?alt=media)

**Figure 8-81 Import path**

#### 3.8.6 Debug points

* (1) Tracking waiting point P1

Set **User Frame** to **0** . Move the robot above the conveyor belt through hand-held teaching or inching control methods, as shown in Figure 8-82. Click **Points** in the right-side menu of **DobotStudio Pro** . Select **P1** and click **Cover** . Then click **OK** in

the pop-up **Tips** window, as shown in Figure 8-83.

**Figure 8-82 Point P1**

![Official CR3 training-system figure, source page 245](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPLADKVHkW3H9FxWdnCXW%2Futp-9727a6fad629cd43f634.png?alt=media)

![Official CR3 training-system figure, source page 245](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTOb1XJt3qb5NWzzyr7iw%2Futp-2d1172a9df016cf59378.jpg?alt=media)

**Figure 8-83 Update P1**

(2) Above the tracking point P2

Set **User Frame** to **1** . The robot is moved to the top of the tracking point on the conveyor belt by inching control method, as shown in Figure 8-84. Click **Points** in the right-side menu of **DobotStudio Pro** . Select **P2** and click **Cover** . Then click **OK** in the pop-up **Tips** window, as shown in Figure 8-85.

**Figure 8-84 Point P2**

![Official CR3 training-system figure, source page 246](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FD1UOy9CZuMMyeiQ4ne3T%2Futp-1463849c95b7aa9bdde3.jpg?alt=media)

![Official CR3 training-system figure, source page 246](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1J1UANUn1rWSF3on92ej%2Futp-aa019b29095e5c9c4ba7.jpg?alt=media)

**Figure 8-85 Update P2**

**(3) Picking point P3**

Place a circular block to the picking point. The suction cup at the end of the robot is controlled to touch the surface of the circular workpiece gently by inching control method, as shown in Figure 8-86. Click **Points** in the right-side menu of **DobotStudio Pro** . Select **P3** and click **Cover** , Click **OK** in the pop-up **Tips** window. Then delete X and Y value, as shown in Figure 8-87.

**Figure 8-86 Point P3**

![Official CR3 training-system figure, source page 247](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdYLLOKsLVVWXLYSRhgYr%2Futp-c89c244e3e51dc807681.jpg?alt=media)

![Official CR3 training-system figure, source page 247](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FxREkil67XtwhX9Repz0W%2Futp-17ff7db86cfb9665d710.jpg?alt=media)

**Figure 8-87 Update P3**

Open the **IO** control panel, turn on the **DO\_09** signal switch. Let the end of the robot absorb the circular workpiece and lift it upward. Observe whether the suction cup can absorb the workpiece. If not, it is necessary to readjust the P3 point.

* (4) Lifting point P4

The robot is lifted to a certain height by inching control method. After absorbing the circular workpiece, the robot leaves the conveyor belt, as shown in Figure 8-88. Click **Points** in **DobotStudio Pro** . Select **P4** and click **Cover** . Click **OK** in the pop-up **Tips** window. Then delete X and Y value, as shown in Figure 8-89.

**Figure 8-88 Point P4**

![Official CR3 training-system figure, source page 248](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FqC68bSYgzGC2tPDK15ac%2Futp-9415f640521cd14570b6.jpg?alt=media)

![Official CR3 training-system figure, source page 248](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoycPaTeFmztCByN4o9J9%2Futp-ceabdc54a72f330b7648.jpg?alt=media)

**CR3 General Training System Operation Instruction**

**Figure 8-89 Update P4**

(5) Safe point P5

Set **User Frame** to **0** . The robot is moved to a position between the conveyor belt and the storage area by inching control method, as shown in Figure 8-90. Click **Points** in **DobotStudio Pro** . Select **P5** and click **Cover** . Then click **OK** in the pop-up **Tips** window, as shown in Figure 8-91.

**Figure 8-90 Point P5**

![Official CR3 training-system figure, source page 249](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FzDsATcFQaR6FroQAdnDc%2Futp-e1b3e3c6596c7f3b32f4.jpg?alt=media)

![Official CR3 training-system figure, source page 249](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fm2a4suPLOfljC0JKZy1f%2Futp-3334f1fcd45d42537a6b.jpg?alt=media)

**Figure 8-91 Update P5**

**(6) Placing point P6**

The robot is moved to the feeding point of the first circular workpiece in the storage area by inching control method, as shown in Figure 8-92. Click **Points** in the right-side menu of **DobotStudio Pro** . Select **P6** and click **Cover** . Then click **OK** in the pop-up **Tips** window, as shown in Figure 8-93.

**Figure 8-92 Placing point P6 of the first block**

![Official CR3 training-system figure, source page 250](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4xrOGFArYwi5CJPoLBd5%2Futp-7bb28158d97bf314f9c1.jpg?alt=media)

![Official CR3 training-system figure, source page 250](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FoP0aCO60KtIs6YL7hbqy%2Futp-8ac6b201168f8fff5f9c.jpg?alt=media)

**Figure 8-93 Update P6**

#### 3.8.7 Save program

Click " ", and in the dialog box that pops up, name the program, as

shown in Figure 8-94.

**Figure 8-94 Save program**

Note: " " is for saving the program to the robot controller. If you want to save the

modified program to the local computer, you need to use " ".

![Official CR3 training-system figure, source page 251](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FS3kmvhusPNZqafXmkIfI%2Futp-3c13fba9178c8c3f76a8.jpg?alt=media)

![Official CR3 training-system figure, source page 251](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FZo2PmxwNHlZmrzcFk4M4%2Futp-1948be82b4e9da0ce5b8.jpg?alt=media)

#### 3.8.8 Run program

Place six circular blocks into the stock bin, as shown in Figure 8-95. Click the

* " " button to see if the program runs as follows:

After the system starts, the pushing motor pushes the circular workpiece in the material well onto the conveyor belt; when the workpiece reaches the visual detection area, the vision locates the workpiece visually and sends the coordinates to the robot; after receiving the information, the robot first follows the movement of the workpiece, and reaches the designated grasping point, then absorbs the circular workpiece on the conveyor belt, and finally places it in the circular groove in the storage area, as shown in Figure 8-96.

**Figure 8-95 Cylinder stock bin**

**Figure 8-96 Palletizing effect**

![Official CR3 training-system figure, source page 252](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEaw3eGeB2iS2gd7eqtT5%2Futp-a157670c71aeae7e8d51.jpg?alt=media)

![Official CR3 training-system figure, source page 252](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJyVAln5caqrL6o6RgpzL%2Futp-a7471a3a6882f836a691.jpg?alt=media)

#### 3.8.9 Export program

Click **File** > **Export project** , and select the path to save the program. Then enter a project name in the pop-up window.

Note: **Export project** is to export the program to your local computer for backup.

**4. Program Description**

#### 4.1 Vision program description

The vision program is shown in Figure 8-97. **0 Image Source1** is mainly used for image acquisition. During the running process of the system, once the vision software receives the trigger signal from the robot, the camera takes photos immediately. **2 Fast Match1** is mainly used for positioning, in order to obtain the image coordinates of the detected object. **3 Branch1** includes two branches according to the detection result of 2Fast Match1. **4 Format1** is used for summarizing the circular block information detected by the vision system and defining the format. **5 Send Data1** is used for sending the **4 Format1** content to the robot. **6 Format2** is used for summarizing the circular block information detected by the vision system and defining the format. **7 Send Data2** is used for sending the **6 Format2** content to the robot.

**Figure 8-97 Vision program** 244

![Official CR3 training-system figure, source page 253](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FJz13m3p5N2h4fZ5AjuDq%2Futp-eee3e5b42b9fed3985c2.jpg?alt=media)

#### 4.2 Robot program description

#### 4.2.1 src0.lua

The relevant variables for defining the robot program are shown in Figure 8-98.

**Figure 8-98 Define the relevant variables**

Define dynamic tracking functions. After detecting the presence of material in the silo, the push motor pushes out the material. After the push action lasts for 5 seconds, the motor retracts. The conveyor belt starts to transport materials. Set the speed of robot movement, as shown in Figures 8-99.

**Figure 8-99 Defines a function for dynamic tracing**

Call the **GetCnvObject()** instruction function. Obtain the data of the workpiece

from the conveyor belt and detect whether it enters the grab area. If a workpiece is

![Official CR3 training-system figure, source page 254](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2nZ5aiKJtkFuTP125GBY%2Futp-6c814971b991fce12fb4.jpg?alt=media)

![Official CR3 training-system figure, source page 254](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FDkLwkSHRdNSdek9LkyTh%2Futp-0e74e648f651ddb0a0c6.jpg?alt=media)

detected, the robot reaches point P2 and begins to follow the workpiece to point P3. It then draws the workpiece from the moving conveyor belt to point P4 and moves to transition point P5. The program is shown in Figure 8-100.

**Figure 8-100 The robot dynamic tracking absorbs workpiece**

The robot will draw the workpiece into the storage area. The program is shown in Figure 8-101.

**Figure 8-101 Process of stacking workpiece**

When the system starts, firstly reset the suction and blowing signals of the suction cup, control the robot to move to the transition point P1, and then execute the dynamic tracking function. The program is shown in Figure 8-102.

![Official CR3 training-system figure, source page 255](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FodfRa4scZy1mLhE6em8t%2Futp-04d64176b7be815526f2.jpg?alt=media)

![Official CR3 training-system figure, source page 255](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FEeXKA3kdyKTVFhgB8mFg%2Futp-7c0ae682e9983fcd7d1c.jpg?alt=media)

**Figure 8-102 Reset program**

#### 4.2.2 global.lua

The function defining the waiting DI signal is shown in Figure 7-103. This

function is used to wait for an external signal input.

**Figure 8-103 Define the function that waits for the DI signal**

## Official source and related installation guides

The complete English source is in the [official DOBOT Universal Training Platform operation-instruction archive](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/20260722/1770703893557_Collaborative%20Robot%20Universal%20Training%20Platform%20Operation%20Instruction-EN.rar). Select file `03-Collaborative Robot Universal Training Platform（CR3_exclude PLC）_2023-07-07_en.pdf`. The archive also contains the platform installation, emergency-stop wiring, conveyor, and PLC-upgrade guides.
