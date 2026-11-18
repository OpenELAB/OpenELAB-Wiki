# PiPER Product User Manual

{% hint style="info" %}
[**View PiPER Product on OpenELAB**](https://openelab.io/products/agilex-piper-ros-ai-arm)

**Product model/family:** PiPER Product · **OpenELAB SKU:** `Agilex-PiPER`
{% endhint %}

AgileX PiPER 6-DOF 1.5kg Payload Robotic Arm for ROS & AI

{% embed url="https://openelab.io/products/agilex-piper-ros-ai-arm" %}

### **AgileX PiPER Robotic Arm Gripper**

{% embed url="https://openelab.io/products/agilex-piper-robotic-arm-gripper" %}

**Relevant section: 3.11 Gripper control area (valid only with grippers).**

### **AgileX PiPER Teacher Control Pendant**

{% embed url="https://openelab.io/products/agilex-piper-teacher-control-pendant" %}

**Firmware applicability: teacher-pendant-related SDK functions require firmware V1.5-2 or later. Confirm the installed firmware before use.**

**PiPER ROBOTIC ARM**

<img src="../../.gitbook/assets/PiPER Product User Manual image 1" alt="PiPER Product User Manual image 1" width="597">

&#x20;

<img src="../../.gitbook/assets/PiPER Product User Manual image 2" alt="PiPER Product User Manual image 2" width="414">

V1.0 2025.06

**Important Safety Information**

This chapter contains important safety information that must be read and understood by any user or organization before using the device for the first time. If there are any questions regarding the usage, please contact us at support@agilex.ai. It is essential to follow and implement all assembly instructions and guidelines in other chapters of this manual. Special attention should be paid to the text associated with warning signs.

**Warning icon：**⚠This refers to situations that may cause danger and, if not avoided, could result in personal injury or serious equipment damage.

**Warning⚠：**&#x41;gileX assumes no responsibility if the robotic arm is damaged, altered, or modified in any way. AgileX is not liable for any damages to the robotic arm or any other equipment caused by program errors or robotic arm malfunctions.

**Limitation of Liability:** Any safety information contained in this manual shall not be considered as a warranty of the AgileX robotic arm. Even if the robot arm complies with all safety instructions, it may still cause injury or damage.

The information in this manual does not include the design, installation and operation of a complete robotic arm application, nor does it include all peripheral equipment that may affect the safety of this complete system. The design and use of the complete system must comply with the safety requirements established in the standards and regulations of the country where the robot arm is installed.

It is the responsibility of the integrator and end customer of the robotic arm to ensure that relevant regulations and applicable laws and regulations are followed to ensure that there are no major hazards in the complete robotic arm application example.

This includes but is not limited to the following:

Effectiveness and Responsibility ● Conduct a risk assessment for the complete robotic arm system.\
● Connect additional safety devices for other machinery as defined in the risk assessment.\
● Ensure the accurate design and installation of the entire robotic arm system, including both software and hardware.\
● The integrator and end customer must follow relevant regulations and applicable legal requirements for safety assessment to ensure that the developed robotic arm has no major hazards or safety risks in actual applications.\
● Be aware of any potential safety risks before operating and using the equipment.\
● Ensure that users do not modify any safety measures.\
● Collect all documents in the technical files, including the risk assessment and this manual.

Environment

● Before first use, carefully read this manual to understand basic operations and usage guidelines.

● Choose a relatively open area for use, as the robotic arm does not come with any automatic obstacle-avoidance sensors.

● Use the robotic arm in an environment with a temperature between -20°C and 50°C.

● If the robotic arm is not custom-made with a specific IP protection rating, its water and dust resistance is rated at IP22.

Check

● Ensure the robotic arm has no visible abnormalities.\
● Ensure proper connection of the wiring harness during use.

Operation

● Ensure the surrounding area is relatively open during operation.

● Operate within visual range.

● The maximum payload of the robotic arm is 1.5KG; ensure that the effective load does not exceed 1.5KG during use.

● If the equipment shows abnormalities, stop using it immediately to avoid secondary damage.

● If abnormalities occur, contact relevant technical personnel and do not handle it on your own.

● Use the equipment in an environment that meets the IP protection rating requirements.

Warnings⚠：

● Ensure that the robotic arm and tools/end effectors are always correctly and securely fixed in place.

● If you must enter the robotic arm's working space, wear safety goggles to protect yourself.

● Ensure that the robotic arm has enough space for free movement.

● Ensure that safety measures are established as defined in the risk assessment.

● Do not wear loose clothing while operating the robotic arm. Tie back long hair when operating the robotic arm.

● Do not use the robotic arm if it is damaged or showing any abnormalities.

● If the host computer software displays error messages, immediately perform an emergency stop and contact relevant technical personnel.

● Ensure that people keep their heads, faces, or other body parts away from the operating robotic arm or from the area the robotic arm can reach during operation.

● Never modify the robotic arm. Altering the robotic arm may introduce unforeseen dangers for the integrator.

● Do not expose the robotic arm to permanent magnetic fields. Strong magnetic fields can damage the robotic arm.

● The robotic arm generates heat during operation. Do not handle or touch the robotic arm while it is operating or shortly after it has stopped, as prolonged contact may cause discomfort. Power off the system and wait for one hour for the robotic arm to cool down.

● Connecting different machines together may increase risk or introduce new hazards. Always perform a comprehensive risk assessment for the entire installation. Depending on the risk assessment, different functional safety levels may apply; therefore, when different safety and emergency stop performance levels are required, always choose the highest performance level. Always read and understand the manuals for all devices used in the installation.

●Robotic arms are not suitable for use by individuals under the age of 18 or others who do not have full capacity for civil conduct.

Safety Instructions for Use:

* Note when switching modes: The main control of the new version of the firmware has undergone MIT processing. If you need to switch to the upper computer control mode after using the MIT mode (teaching mode), the following actions should be taken:

1\. Drag the robotic arm back to the zero position and briefly press the teaching button to turn it off.

2.Connect to the upper computer. After disabling, re-enable it. It is strictly prohibited to switch modes at non-zero positions.

* Switching at non-zero positions may cause sudden drops or abnormal movements due to disabling.

\
\
<br>

**Catalogue**

1\. Introduction - 5 -

1.1. Product list - 5 -

1.2. Performance Parameters - 5 -

2\. Basic Usage - 7 -

2.1. Electrical Interface Introduction - 8 -

2.2. Robotic Arm Teach/Demonstration Mode Instructions - 10 -

2.2.1The position of the origin - 10 -

2.2.2 User Coordinate System - 10 -

2.2.3 Singular Position - 10 -

2.2.4 Zero position - 13 -

2.3. Robotic Arm Workspace and Payload - 14 -

2.4. Mechanical Specifications - 14 -

2.4.1. Base Installation Instructions - 14 -

2.4.2. End Part Installation Instructions - 15 -

2.5. Desktop Installation Instructions - 17 -

2.6. Joint zero point description - 18 -

2.7. Instructions for the installation method of the robotic arm - 19 -

2.8. CAN Connection and Preparation - 19 -

2.9. Terminal connection electrical appliance instructions: - 19 -

2.10. Power-on operation instructions: - 20 -

2.11. Robotic Arm Teach/Demonstration Mode Instructions - 21 -

3\. Host computer instruction - 22 -

3.1. ArmRobotUA - 22 -

3.2. Robotic Arm communication - 24 -

3.3. Vertical menu bar - 25 -

3.4. Speed percentage setting - 26 -

3.5. Robotic arm Enable button - 26 -

3.6. E-stop button - 27 -

3.7. Window zoom and close buttons - 27 -

3.8. Operation function area - 27 -

3.9. Motion control - 28 -

3.10. Linkage control area - 29 -

3.11. Gripper control area (valid only with grippers) - 30 -

3.12. oint setting area - 31 -

3.13. Speed setting area - 32 -

3.14. Collosion grade - 33 -

3.15. Motor setting - 34 -

3.16. Upgrade - 35 -

3.17. 3D simulation model - 36 -

3.18. TraceLib - 37 -

3.19. Robotic arm joint status button - 38 -

3.20. Robotic arm status - 39 -

4\. Secondary Development - 39 -

5\. CAN protocol - 39 -

6\. Maintenance and Servicing - 39 -

7\. Maintenance Precautions - 40 -

8\. Emergency Handling - 40 -

9\. Dimensional drawings - 40 -

9.1. Zero position - 40 -

9.2. Axonometric drawing of the robotic arm - 41 -

9.3. Robotic arm with leader gripper - 42 -

9.4. Robotic arm with follower gripper - 43 -

9.5. Base - 44 -

9.6. End of the arm - 45 -

\
\
<br>

## 1 Introduction <a href="#ka0bu" id="ka0bu"></a>

This 6 DOFs robotic arm is specifically designed for the education and research industry, consumer-level applications, and industrial automation. With a payload capacity of 1.5kg, it is suitable for various research and industrial applications, including humanoid robots, automatic assembly, and automated handling. The six rotating joints provide full-range operational flexibility, ensuring high precision and repeatability. The robotic arm features a modular design, making it easy to maintain and upgrade. It offers an intuitive user interface that simplifies programming and operation, allowing even non-professionals to get started quickly. It can be widely applied in fields such as scientific research, education, automotive manufacturing, electronics assembly, food processing, laboratory automation, and medical equipment operation.

### 1.1 Product list <a href="#id-5ikyh" id="id-5ikyh"></a>

| **Name**                      | **Quantity** |
| ----------------------------- | ------------ |
| 6 DOFs Robotic arm            | 1            |
| USB toCAN module              | 1            |
| Power adapter                 | 1            |
| MicroUSB cable                | 1            |
| Power and communication cable | 1            |
| Base mounting screws          | 4            |
| Base installation wrench      | 1            |

### 1.2 Performance Parameters <a href="#eqs02" id="eqs02"></a>

| Parameter Type                                                                                                                                                                                                              | Item                                                                                             | Specification                                                                                           |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| Structural Parameters                                                                                                                                                                                                       | DOF                                                                                              | 6                                                                                                       |
| Payload                                                                                                                                                                                                                     | 1.5KG                                                                                            |                                                                                                         |
| Weight                                                                                                                                                                                                                      | 4.2KG                                                                                            |                                                                                                         |
| Repeatability                                                                                                                                                                                                               | ±.0.1mm                                                                                          |                                                                                                         |
| Working Radius                                                                                                                                                                                                              | 626.75mm                                                                                         |                                                                                                         |
| Standard Power Supply Voltage                                                                                                                                                                                               | <p>DC24V</p><p>(Min. Operating Voltage 24V, Max. Operating Voltage 26V)</p>                      |                                                                                                         |
| Power Consumption                                                                                                                                                                                                           | <p>Max Power Consumption ≤ 120W</p><p>Average Power Consumption ≤ 40W</p>                        |                                                                                                         |
| Material                                                                                                                                                                                                                    | <p>Aluminum Alloy Frame</p><p>Plastic Casing</p>                                                 |                                                                                                         |
| Controller                                                                                                                                                                                                                  | Intergrated                                                                                      |                                                                                                         |
| Communication Method                                                                                                                                                                                                        | CAN                                                                                              |                                                                                                         |
| Control Method                                                                                                                                                                                                              | Drag\&Teaching/Offline Trajectory/API/Host PC                                                    |                                                                                                         |
| External Interface                                                                                                                                                                                                          | 1 Power Interface, 1 CAN Interface                                                               |                                                                                                         |
| Base Mounting Dimensions                                                                                                                                                                                                    | 70mm\*70mm\*M5\*4                                                                                |                                                                                                         |
| Operating Environment                                                                                                                                                                                                       | <p>Temperature: -20°C to 50°C</p><p>Humidity: 25% - 85%, Non-condensing</p>                      |                                                                                                         |
| Noise                                                                                                                                                                                                                       | <60dB                                                                                            |                                                                                                         |
| Installation                                                                                                                                                                                                                | Compatible with all products of AgileX Robotics                                                  |                                                                                                         |
| Motion Parameters                                                                                                                                                                                                           | Joint Motion Range                                                                               | <p>J1:±154°</p><p>J2:0°~195°</p><p>J3:-175°~0°</p><p>J4:-102°~102°</p><p>J5:-75°~75°</p><p>J6:±120°</p> |
| Maximum joint speed                                                                                                                                                                                                         | <p>J1:180°/s</p><p>J2:195°/s</p><p>J3:180°/s</p><p>J4:225°/s</p><p>J5:225°/s</p><p>J6:225°/s</p> |                                                                                                         |
| Note: The above data is the test result of AgileX Robotic Arm in a controlled test environment. The results may vary to varying degrees in different environments and usage methods. Please refer to the actual experience. |                                                                                                  |                                                                                                         |

<br>

| Two-Finger Gripper Specifications (Optional) |                                                                                                   |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Weight                                       | 500g                                                                                              |
| Accuracy                                     | ±0.5mm                                                                                            |
| Opening and closing distance                 | 0-100mm                                                                                           |
| Supply voltage                               | DC24V                                                                                             |
| Power dissipation                            | <p>Maximum power consumption ≤50W .</p><p>The comprehensive power consumption ≤30W</p><p><br></p> |
| <p>Contact surface material</p><p><br></p>   | Rubber                                                                                            |
| Controller                                   | Intergrated                                                                                       |
| Communication mode                           | CAN                                                                                               |
| <p>Control mode</p><p><br></p>               | Drag\&Teaching/Offline Trajectory/API/Host PC                                                     |
| <p>External interfaces</p><p><br></p>        | Power interface \*1, CAN interface \*1.                                                           |
| Installation method                          | Flange installation                                                                               |
| Working environment                          | Temperature:-20-50;℃humidity: 25%-85%, non-condensing                                             |
| Noise                                        | <60dB                                                                                             |

\
\
<br>

| Teaching device parameters (optional) |                                                                                            |
| ------------------------------------- | ------------------------------------------------------------------------------------------ |
| Body weight                           | 550g                                                                                       |
| Accuracy                              | ± 0.5mm                                                                                    |
| Opening and closing spacing           | 0-100mm                                                                                    |
| Power supply voltage                  | DC24V                                                                                      |
| Power consumption                     | <p>maximum power consumption &#x3C;50W</p><p>comprehensive power consumption &#x3C;30W</p> |
| Contact surface material              | rubber                                                                                     |
| Controller                            | integrated                                                                                 |
| Communication method                  | CAN                                                                                        |
| Control method                        | Drag\&Teaching/Offline Trajectory/API/Host PC                                              |
| External interface                    | power interface \*1 CAN interface \*1                                                      |
| Installation method                   | Flange installation                                                                        |
| Working environment                   | temperature: -20-50℃, humidity: 25%-85%, non-condensing                                    |
| Noise                                 | <60dB                                                                                      |

Modified DH

<img src="../../.gitbook/assets/PiPER Product User Manual image 3" alt="PiPER Product User Manual image 3" width="569">

## 2 Basic Usage <a href="#id-1t8tg" id="id-1t8tg"></a>

The robotic arm has 6 DOFs and a 1.5kg payload at the end. The six rotating joints provide full-range operational flexibility, ensuring high precision and repeatability. It features a lightweight design, allowing the robotic arm to achieve fast motion capabilities while maintaining a relatively high payload capacity. It can be widely used in embodied intelligence for real-world data collection.

\
<br>

<img src="../../.gitbook/assets/PiPER Product User Manual image 4" alt="PiPER Product User Manual image 4" width="589">

### 2.1 Electrical Interface Introduction

<img src="../../.gitbook/assets/PiPER Product User Manual image 5" alt="PiPER Product User Manual image 5" width="1441">

1: Power and communication port

2: Status indicator light

3: J1J2 connection port

4: Power positive

5: Power negative

6: CAN-H

7: CAN-L

**Note**: Align the red dot with the corresponding red dot on the cable. The textured area of the connector is designed to retract under force. During installation, align the red dot downward with the protruding point and insert it directly. To remove, press down on the textured area and pull it out.The installation method is shown in the following figure

<img src="../../.gitbook/assets/PiPER Product User Manual image 6" alt="PiPER Product User Manual image 6" width="717">

**Light indication instructions for Position 2 of electrical panel**:

| Indicator light color      | Status description                                                                                                                                                |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| The green light flashing.  | The robotic arm is operating normally                                                                                                                             |
| The green light is on.     | The power on of the king controller is abnormal. It needs to be replugged in                                                                                      |
| The red light is flashing. | If the red light is flashing, the mechanical arm is abnormal or the mechanical arm has entered the upgrade mode, the fault needs to be checked in the former case |

<br>

**Description of the teaching indicator light for the terminal joint of the robotic arm:**

<br>

| <p>Teaching indicator light color</p><p><br></p> | <p>Status description</p><p><br></p>                                                                         |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| Absence of lighting                              | The stop status of the mechanical arm dragging teaching/the end status of the mechanical arm dragging record |
| The green light is on                            | The robotic arm enters the dragging teaching trajectory recording state                                      |
| The green light is flashing.                     | The robotic arm enters the state of reproducing the dragging teaching trajectory                             |

**Description of the reserved interface at the end joint of the robotic arm: (The power supply interface is positive at the top and negative at the bottom, and the communication interface is higher on the left and lower on the right.**

<img src="../../.gitbook/assets/PiPER Product User Manual image 7" alt="PiPER Product User Manual image 7" width="343">

**CAN matching resistance adjustment paddles for the main control of the robotic arm**

The main control CAN matching resistance paddle is mainly used in the case where one master arm controls multiple slave arms:

No adjustment is required for single-arm use.

By factory default, 1 is on (down) and 2 is off (up). At this time, the default resistance is 60 ohms.

When there are more than two arms, one of the arms opens 1 (downward) and closes 2 (upward), while the other arms 12 all close (upward).

<img src="../../.gitbook/assets/PiPER Product User Manual image 8" alt="PiPER Product User Manual image 8" width="563">

\
\
\
<br>

### 2.2 Robotic Arm Teach/Demonstration Mode Instructions <a href="#id-3rwat" id="id-3rwat"></a>

### 2.2.1The position of the origin <a href="#wui62" id="wui62"></a>

(x:0, y:0, z:0) of the origin coordinate system piper

<img src="../../.gitbook/assets/PiPER Product User Manual image 9" alt="PiPER Product User Manual image 9" width="475">

### 2.2.2 User Coordinate System <a href="#g47fb" id="g47fb"></a>

The user coordinate system is the robot arm base coordinate system.

<br>

<img src="../../.gitbook/assets/PiPER Product User Manual image 10" alt="PiPER Product User Manual image 10" width="732">

\
\
\
<br>

### 2.2.3 Singular Position <a href="#zlasw" id="zlasw"></a>

1\. Wrist singular position: When J4 and J6 are coaxial, it is a wrist singular position.

<br>

<img src="../../.gitbook/assets/PiPER Product User Manual image 11" alt="PiPER Product User Manual image 11" width="365">

2\. Elbow singular position: When J1 and J4 are coaxial, it is elbow singular position.

<img src="../../.gitbook/assets/PiPER Product User Manual image 12" alt="PiPER Product User Manual image 12" width="410">

\
<br>

3\. Shoulder singular position: when the intersection of the axes of J5 and J6 lies on the axis of J1, it’s shoulder singular position.

<img src="../../.gitbook/assets/PiPER Product User Manual image 13" alt="PiPER Product User Manual image 13" width="342">

4\. Boundary singular position: It occurs when the end position of the robotic arm is at the maximum working range, resulting in a boundary singular position.

<div><img src="../../.gitbook/assets/PiPER Product User Manual image 14" alt="PiPER Product User Manual image 14" width="353"> <img src="../../.gitbook/assets/PiPER Product User Manual image 15" alt="PiPER Product User Manual image 15" width="340"></div>

<br>

<img src="../../.gitbook/assets/PiPER Product User Manual image 16" alt="PiPER Product User Manual image 16" width="573">

#### 2.2.4 Zero position <a href="#ylzfz" id="ylzfz"></a>

The zero point of the robotic arm joint is at the position shown in the figure. The zero point of J1 is the zero point when the calibration scale is aligned. The zero point of J2J3 is the zero point when the robotic arm is placed naturally when it is disabled. When the axis of J6 is in the same line as that of J4, the zero point of J5 is the zero point

<br>

The zero point coordinates are:X = 56.128 , Y = 0 , Z = 213.266 , RX = 0 ,RY = 85.0 , RZ = 0.

<img src="../../.gitbook/assets/PiPER Product User Manual image 17" alt="PiPER Product User Manual image 17" width="1000">

<br>

### 2.3 Robotic Arm Workspace and Payload <a href="#ouzzq" id="ouzzq"></a>

<div><img src="../../.gitbook/assets/PiPER Product User Manual image 18" alt="PiPER Product User Manual image 18" width="1428"> <img src="../../.gitbook/assets/PiPER Product User Manual image 19" alt="PiPER Product User Manual image 19" width="858"></div>

Robotic Arm End-Effector Payload Curve Diagram

<br>

### 2.4 Mechanical Specifications <a href="#pmb6c" id="pmb6c"></a>

#### 2.4.1 Base Installation Instructions <a href="#jgv6k" id="jgv6k"></a>

The robotic arm base is installed using screws for fixation. The base has four pre-drilled M5 threaded holes. The accessory kit includes four M5 screws, which can be tightened using the provided hex tool. The hole spacing is 70mm. If you need to attach the base to mobile equipment or a fixed surface, you can design the corresponding structure with 70mm hole spacing.

<img src="../../.gitbook/assets/PiPER Product User Manual image 20" alt="PiPER Product User Manual image 20" width="902">

#### 2.4.2 End Part Installation Instructions <a href="#bk5vx" id="bk5vx"></a>

The end can be equipped with other tools via a flange. Optional accessories include a two-finger gripper and a teach pendant. The installation method is shown in the diagram below.

* Install and fix the mechanical arm on the installation table surface, remove the claw clamp, the teaching device, the flange accessories, and the flange and accessory bolts inside.
* As shown in the figure, the limit bolt (M3\*4, head diameter 4.5) is installed at the upper left corner of the J6 motor when looking at it, as shown in the figure.

<img src="../../.gitbook/assets/PiPER Product User Manual image 21" alt="PiPER Product User Manual image 21" width="762">

* After aligning the limit slots of the flange with the installed limit bolts, lock in 6 m3\*8 hex socket countersunk bolts, as shown in the figure

<img src="../../.gitbook/assets/PiPER Product User Manual image 22" alt="PiPER Product User Manual image 22" width="865">

* After installing the hairpin, take out the claw clamp and the teaching device. The back cover of the claw clamp and the teaching device is designed with a fool-proof structure, as shown in the figure. Insert the claw clamp and the teaching device and then lock and fix them with M3\*14 hex socket countersunk bolts, as shown in the figure
* After installing the claw clamp teaching device, insert the power supply and communication cables in the accessory package into J6 and the claw clamp teaching device.
* Connect the aviation plug-in cable to the robotic arm properly. Then, connect the USB-to-CAN module and the aviation plug-in cable in the order of yellow corresponding to CAN-H and blue corresponding to CAN-L. Plug the USB cable into the USB-to-CAN module and connect it to the computer. After connecting the aviation plug-in cable and the adapter, power on the adapter.
* After power-on, observe the light indicator on the base of the robotic arm flashing slowly in green. Turn on the upper computer. After the upper computer communicates with the robotic arm, rotate the claw clamp and the teaching device to the limit position as shown in the figure. Then click to set the zero point of the J6 joint. After the setting is completed, enable the robotic arm and operate the upper computer to return the J6 joint to the zero point. Check whether the zero point marks on the J6 joint and the claw clamp teaching device correspond.As shown in the picture：

<br>

<img src="../../.gitbook/assets/PiPER Product User Manual image 23" alt="PiPER Product User Manual image 23" width="588">

<br>

### 2.5 Desktop Installation Instructions <a href="#ay6ro" id="ay6ro"></a>

The desktop installation module is an optional module. The standard product does not come with this component. If you need to purchase it separately, please contact us. The dimensions are as shown in the following figure. When in use, please make sure to fix it firmly before using the mechanical arm.

<img src="../../.gitbook/assets/PiPER Product User Manual image 24" alt="PiPER Product User Manual image 24" width="800">

### 2.6 Joint zero point description <a href="#id-8iqox" id="id-8iqox"></a>

<img src="../../.gitbook/assets/PiPER Product User Manual image 25" alt="PiPER Product User Manual image 25" width="809">

&#x20;

<img src="../../.gitbook/assets/PiPER Product User Manual image 26" alt="PiPER Product User Manual image 26" width="869">

### 2.7 Instructions for the installation method of the robotic arm <a href="#dtfb0" id="dtfb0"></a>

When the robotic arm is in use, different Settings are required due to different installation methods. The installation method can be set through the upper computer configuration, and different installation methods can be selected according to different installation positions.

<img src="../../.gitbook/assets/image (1206).png" alt="image.png" width="1950">

### 2.8 **CAN Connection and Preparation** <a href="#id-3nm9k" id="id-3nm9k"></a>

Lead out the CAN cable and connect the CAN\_H and CAN\_L wires to the CAN\_TO\_USB adapter.

Connect the CAN\_TO\_USB adapter to the laptop's USB port. The connection diagram is shown as below

<img src="../../.gitbook/assets/PiPER Product User Manual image 28" alt="PiPER Product User Manual image 28" width="1280">

\
<br>

Note: If using a non-standard charger, the power input must not exceed 26V, and the current must be no less than 10A.

### 2.9 Terminal connection electrical appliance instructions: <a href="#fnsgl" id="fnsgl"></a>

The end joint reserves the XT30 2+2 interface: The power supply and CAN are defined as shown in the following figure.

Voltage: 24V, current: 2A MAX.

The terminal CAN communication is only compatible with Songling's own equipment. It is strictly prohibited to privately connect other CAN devices, otherwise it may cause uncontrollable damage.

<img src="../../.gitbook/assets/PiPER Product User Manual image 29" alt="PiPER Product User Manual image 29" width="348">

### 2.10 Power-on operation instructions: <a href="#vea8z" id="vea8z"></a>

The first power-on of the robotic arm should be carried out in the following A-G sequence:

1\. First, plug in the J2 connection port of A;

2\. Connect the CAN wire of aviation plug B properly.

3\. Align the XT30 connector of C properly.

4\. Insert the D aviation plug with the red dot facing down properly.

5\. Plug in Adapter E properly.

6\. Check and confirm that the AC head of adapter E is properly plugged in and powered on. Wait until the indicator light on the electrical panel flashes green;

7\. Plug the USB cable into the computer for use.

<img src="../../.gitbook/assets/PiPER Product User Manual image 30" alt="PiPER Product User Manual image 30" width="874">

Note: The direction of the red dot corresponds to the red dot on the cable below. The patterned part of the power strip is the area that can be retracted backward under force. When installing, just insert the red dot directly towards the protruding point. When pulling out, press down on the patterned part and then pull it out.

<br>

<img src="../../.gitbook/assets/PiPER Product User Manual image 31" alt="PiPER Product User Manual image 31" width="413">

<br>

### 2.11 Robotic Arm Teach/Demonstration Mode Instructions <a href="#kwsnd" id="kwsnd"></a>

The robotic arm's drag & teach mode status is indicated by the button light between J5 and J6.

There are three types of robotic arm status light displays:

1. **No light display**: **Robotic arm’s drag & teach mode is stopped, or the drag recording has ended.**

<img src="../../.gitbook/assets/PiPER Product User Manual image 32" alt="PiPER Product User Manual image 32" width="1287">

1. **Solid green light**: The robotic arm has entered the drag & teach mode for trajectory recording.

<img src="../../.gitbook/assets/PiPER Product User Manual image 33" alt="PiPER Product User Manual image 33" width="1277">

1. **Flashing green light**: The robotic arm has entered the drag & teach mode for trajectory playback.

<br>

**How to switch to drag mode:**

1. **Single click button**: Toggle between drag teach trajectory recording and stopping the drag recording.
2. **Double click button**: Activates the drag teach trajectory playback mode.

**Instructions:**

First, observe the indicator light status:

1. If the light is off, click the button once. The green light should turn solid, indicating that the user can drag the robotic arm to start recording the trajectory.
2. If the light is off and a trajectory has been recorded previously, double-click the button. The green light should flash every 500ms, indicating the robotic arm is in playback mode and will reproduce the recorded trajectory.
3. If the light is solid, it indicates trajectory recording is in progress. To stop the recording, click the button once; the light should turn off, indicating that recording has ended. If you want to replay the trajectory, follow step 2.
4. If the light is flashing, the robotic arm is currently in playback mode.

**Notes:**

1. During trajectory playback, the user must keep a safe distance from the robotic arm to avoid injury.
2. Each time the robotic arm enters teach trajectory recording mode, the previously recorded trajectory is erased. The playback mode will use the most recent recorded trajectory.
3. The maximum trajectory recording time is 3 minutes; any trajectory exceeding this time will be invalid.
4. After finishing drag teaching, ensure the indicator light is off/drag teaching mode is stopped.
5. If you want to switch to host computer control or command control, ensure the indicator light is off/drag teach mode is stopped. Then switch to standby mode via the host computer, and after entering standby mode, switch to CAN mode. The same applies to command control—first switch to standby mode, then switch to CAN control mode.
6. When switching from link mode and teach by dragging mode to CAN control mode, the robotic arm must be positioned at the zero point before changing modes. The zero point is shown in the figure below:

<img src="../../.gitbook/assets/PiPER Product User Manual image 34" alt="PiPER Product User Manual image 34" width="781">

Robotic Arm Zero Position

## 3 Host computer instruction

### 3.1 ArmRobotUA <a href="#mddk7" id="mddk7"></a>

Software Download:

Link: [https://www.dropbox.com/scl/fi/78e4ch20ok9n040onay0y/ArmRobotUA\_V1.5.2.260310\_release.exe?rlkey=q4q1xr9f7k1gc5j0vtl803m5f\&st=kw1yaszi\&dl=0](https://www.dropbox.com/scl/fi/78e4ch20ok9n040onay0y/ArmRobotUA_V1.5.2.260310_release.exe?rlkey=q4q1xr9f7k1gc5j0vtl803m5f\&st=kw1yaszi\&dl=0)

Using a PC with Windows 7 or higher, double-click to open the host computer software. Through this human-machine interaction software, you can operate the robotic arm and read feedback data of the robotic arm. The user interface is shown as follows:

<img src="../../.gitbook/assets/PiPER Product User Manual image 35" alt="PiPER Product User Manual image 35" width="139">

**Host software**

<img src="../../.gitbook/assets/PiPER Product User Manual image 36" alt="PiPER Product User Manual image 36" width="1536">

**Host Computer Operation Interface**

<br>

**Names of the functional areas in the host computer software panel**

| Index | Name                              |
| ----- | --------------------------------- |
| 1     | Robotic Arm Communication Button  |
| 2     | Menu Options                      |
| 3     | Speed Percentage Setting          |
| 4     | Robotic Arm Enable Button         |
| 5     | Robotic Arm Emergency Stop Button |
| 6     | Window Resize/Close Buttons       |
| 7     | Operation Function Area           |
| 8     | 3D Simulation Model               |
| 9     | Trajectory Library Function       |
| 10    | Robotic Arm Joint Status          |
| 11    | Robotic Arm Status Bar            |

### 3.2 Robotic Arm communication <a href="#chkrj" id="chkrj"></a>

Click setting to switch the language.

<img src="../../.gitbook/assets/PiPER Product User Manual image 37" alt="PiPER Product User Manual image 37" width="1536">

Click the robot communication button on the upper left of the window, and a \[Connect Robot] window will pop up, which will automatically identify the CAN device connected to the PC device and display it. Users can manually connect and disconnect the selected CAN device. If the connection is successful, the button will monitor and display the current status in real time based on the online status of the connected CAN device.

<img src="../../.gitbook/assets/PiPER Product User Manual image 38" alt="PiPER Product User Manual image 38" width="1536">

Robotic arm communication button

<div><img src="../../.gitbook/assets/PiPER Product User Manual image 39" alt="PiPER Product User Manual image 39" width="164"> <img src="../../.gitbook/assets/PiPER Product User Manual image 40" alt="PiPER Product User Manual image 40" width="170"></div>

Robotic arm status display (left: online, right: offline)

### 3.3 Vertical menu bar <a href="#tysu2" id="tysu2"></a>

Click the option on the left side of the window to switch to the corresponding panel and select the function you want to operate. The background of the selected item will be light blue.

<img src="../../.gitbook/assets/PiPER Product User Manual image 41" alt="PiPER Product User Manual image 41" width="1342">

Vertical menu

### 3.4 Speed percentage setting <a href="#gzdbq" id="gzdbq"></a>

After successfully connecting to the CAN device, the user can change the speed percentage setting at the top of the window to set the movement speed of the robotic arm. The value is the corresponding percentage of the maximum movement speed of the robotic arm.

<img src="../../.gitbook/assets/PiPER Product User Manual image 42" alt="PiPER Product User Manual image 42" width="362">

Speed percentage setting

### 3.5 Robotic arm Enable button <a href="#h2dcr" id="h2dcr"></a>

After successfully connecting to the CAN device, the user can press the robotic arm enable button at the top of the window. The display shows the current status of the six joints. Clicking it will reverse the positions of the six joints at the same time.

<div><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGYAAAAzCAYAAABlnH0mAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAQWSURBVHhe7ZxLThtBFEW9BhBeAlP2wCpgwAaYsgTWEiVKlIkHBokMEDYSCImJAQEC8f+Yr3dQ0e1wW4/y67LdscuF/K50JFz1qrvr3a6Pge5Kp9Nx5P393b29vbnX19eMl5cXIzL0IjeGpqDy+fnZPT09ZbTbbSMin4yBKRgh7dtb11hedr+qVfetUjHGQG4MTcHogClasBGP3BhMXzDl/v7e/ZyZUYONeHAGq2BNeXx8dBcXF2qgEReu9RUs9Hd3d+709FQNNOKSG4Np7Obmxh0fH6uBRly45mfGXF9fu6OjIzXQiEtuDPbOMObw8FANNOJixiTKJ2Ourq7MmEQwYxLFjEkUMyZRJt6Y39Wq219ZcX/m59X6EGirlQ+DiTZG6rZWU2N8mgsLHy36b1OGoRtTn5v7uOywarOzantAlbmLywD1m2T0D7GDtCnDSEcMJcsw/NkxSNYRqrW6qtYPG2jQJJdpMwjRjSGY1yGtcxhNqPfLR0XRdYQo02YQxmYMoELTWgygFI3Bn2LGYoxcSFnGXRKkdZx1Uv7owtrkK7SDgnAueT1Qr3VQuz7t3FiX/LhedBlzcHCgBpaB0uoAOk6xTMrvOCWTzGTyMxPDZCCWYowPhfMhXrYpMhTyr483jdy0YJ2EBp0VxmoMoLRyzRjtLoXkz5CsRxu/TELJMppTtAGB5LXwJtPWRsovD/HljIGK7mKAkYJRJMv6MabIcMgvZ51sQ8kY0uv8Gl/KGHYQwp0cMgigXq5JWgyANGNCCYVkG0rG9FNXRHJrDIG0ZPkLtBYjjyu/EPpxBNKOE2oHyTb9SLbvxViN4d2szeOQliyChEv55Vz8QSxjQtc7KF3GjON7jDYlQX5HtV/RUEWfQSjBANKSSvnlrPONgWTM/zA2Y7iN1HYxAPKTBfkm+kmHtHaQLJNQsgzngfq9Pl6HdvOAovIiohsj5/+iTgNIS7DccTF5Mo5CHL/TUDh30eiEOKWG1j4CFd0AKMcxUMapNdRXjaEb48/9mkI7Kk2s4yiT8jvsnx+faSDFWCkcxz9+yEQpuZ5p1zjoaAEjHTFGeWDMxP6hLGXMmEQxYxLFjEkUMyZRzJhEMWMS5ZMx9t/+6WDGJEpuDB/1wxNlP6an1WAjHl3G4BnM+tKSGmzEIzdGPrW8v7vraouL7vvUlNrIGD0wJntqGb/JxHP+l5eX2XS2s7PjNjc33cbGhltfX89YW1vLqNfrxghgfkH+Aga+GQOj5vz83LVaLbe3t5cZtL297ZrNpms0GqXY2tqaSLRc9ANynRvDOQ3m4LUl+E5zdnaWTW0nJyfZ2mPEI3+XDB2COVhvsH3G1Pbw8JAZBTCajNGDXH8yhuZgWsOaA4PkO8uMeHQZQ3NokASjyYjDPy867i8OcTaNk0GIzgAAAABJRU5ErkJggg==" alt="PiPER Product User Manual image 43" width="102"> <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAG0AAAAzCAYAAACdfIbRAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAQFSURBVHhe7ZzLTttAFIZ5BiryCGx5B54CFrwAWx6BRTet2i676KYL1hWVAAlVQkAkEOqKi4CCuEO45w2m+i1+6XA4tscEO7Y4v/QtMp45SebL2ONIyUC32w15PD4+On1E+8iVhkEPDw/h/v4+4e7uzqkY7SRTGoVh4O3tbbi5uUm4vr52KkR7SZUGYVhZ553zMPl7MrS+tsLAxwGnD2gvpjQKw6qCMKuQUx3aywtpPCVC2OXlZRj6MmQWcqpDe3kmjQdwDet0OuHo6Mgs4lSL9mJKw6bj4uIi7O/vm0WcatFeXkjjtezs7Czs7u6aRZxq0V5SpZ2enoadnR2ziFMt2ospDfcGOLi9vW0WcapFe3FpDSBa2snJiUurCdqLS2sALq2BuLQG4tIUrW+tMPVnKozOjJrHs8BYq/2tcWkCmdl/s2YfzdivsacR8WN6pS/SRn6MPL3NuFg1ygSJFYD3gr5FxvRK31caYx3jp9g6ViZIUQGvGfNaai1t+Ptw6rEyQRotDV//90sayDpWFkjdpUkvtZGGa4Vuw+5suj2d9MfuDo8xUTLWDg59dbJ2egjqyk0GgpVv9QeIJc16buu9FaGQtK2tLbNILzBWu9XGYFuOYKIwMZSJyDGcNE4UZDGyn4RBbfSXY9JkI1oaXyNeA9v4OrM+AHk0Shph9AQyeW2YXN0mYWQbxWHSZTtBpDRejyFO9gOMbo+lNtKsWP0Boj/VwJKBFYbTnGyLkWbVZ3Q7j8kxjOxD8p4/j8auNGtS8yYDq4WnLMTqA5Ci9RE5hpF9Yo7F8C6k8VSFyJth3Y8gReoDRI6JiRxfhNpKywKJnVRIQuSOLWvyARJbnyByjH78lhSSVpf7NCR2UhnZljX5ALHqM7qdx+QYRvZ5K2otjatEtyNFpOm+jGyTMLKNu0drNwgQ+Tx8LXK7L0lrj6HW0tK+e0SKSENQi/dsDK511n0Xw+29vCbqvgRJ+3Cgnfdl/CCmyY+hL9L4wmPDcVay6lnH8JirhrHqY1LlDTuSJVgGz8HjugbSyyoDudLK/sLYKY724tIagEtrIC6tgbi0BuLSGohLayAurYFES/NfzdQH7cWlNYAoafyZKH4J+uHzB7OQUx3aS6Y0/OZ6YmbCLORUR640/e8G63/Xw/jP8TD4adAs6JSP9vJMGsXhG2X8X8Xx8XFyilxbWwtLS0thcXExLCwsJMzPzyfMzc05JcD5BdqLKQ1WsRRh9fDwMGxuboaNjY1EXrvdDqurq2FlZeVVLC8vv0usuYgBc629vJDGDjyH4q+WcG9wcHCQnC739vaSa51THdqLKQ2wA86j2GpiWV5dXSUSAVahUz6Ya+0lVRrgksS5FPIAVp9TLc+9dMN/1qqAuqQlDwIAAAAASUVORK5CYII=" alt="PiPER Product User Manual image 44" width="109"></div>

Robotic arm Enable button

### 3.6 E-stop button <a href="#jbhbc" id="jbhbc"></a>

After successfully connecting to the CAN device, the user can press the robot arm emergency stop button above the window. After pressing the emergency stop button, the robot arm will immediately stop any movement. Press the button again to resume use. It can be resumed after enabling.

<div><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGkAAAAzCAYAAACUlyarAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAPdSURBVHhe7ZxLTuNQEEVZAwiWwJQ9sAoYsAGmLIG1tLrVrZ5kEJDoASJBAiExCSBAIP6f8M0OXutafVGlXM92LMWx1XWlw6DqvXx87GeTKJ4aDAZB8/n56UwQ7SMlCYM+Pj7C+/t7wtvbm1Mx2smQJArCwNfX1/Dy8pLQ7/edCpFOwJckCMKR07+/D53V1fBrbi58m5pyJoAUBBJJFISjBoKsiU51pCRxiYOgx8fH8HN21pzoVEdKEs9Bz8/P4erqypzkVIspCRcJDw8P4fz83JzkVEtKEs9Fd3d34fT01JzkVEtU0u3tbTg5OTEnOdViSsK1OSQdHx+bk5xqcUkNICrp5ubGJdUEl9QAXFIDcEkNwCU1AJfUAMYqqb2wEEaJ9RgWrfn5fzOG01tfHxo3an6rr2Niz4P3JceBIu8Vr08/RxHGKknCWL3u0lK0p+HG0EL4GH8WF79qCOpyHCNrlCHnHq6tJTX9PKzft1pDdQkja1L4qKJqIYlvwOppmFhPS8Jj6zGIrLHOuRShBRPuEFogYXRditK9LFKS8DVF1ZJAVk+CxPZiRC5FiOyzhlh1zMVezugxEkbvBLKn63m9GBOXZK3vWTBWrwiM1QM4OhAcTVafZC17jK7n9WJkSjo6OjInlYGx6rqWhUyZkzBj9QCTt/NkLV2Mruf1YjROklyOGGvJicFYPcBYPQ1TtJ53LotRuSQr1vgsIArLjE4RWYzVA4zV0zB5dbxeLqOIHFuEyiVZdV0rCt48zw1M3jLFWD3AWD0NE6vLYKca5YiX1FKSFT1GU3RPZaweYMZ1TirDxCVZYANorHEaxuoRxuoBLqNFr+6s8wuj62XJlFTX/5Ni0riBrR5hrB7AYzNWnzDWFSaj62WphSQsLbGeBpGfKugeYvUIY/UIl868TxxiRxtj9cpQC0l801ZPw8iavNrLWxoZqyehKL2ccZnLWg4Zq1eGsUriEVI01mNocBTFYi09IOt1ZF0gyKVPxtoRsp5Djx2VlCT/Pql+uKQG4JIagEtqAC6pAbikBuCSGoBLagBRSf6rivrgkhqAKYk/x8Qv/X7MzJgTnerIlITfzLZXVsyJTnWkJOlfnx/u74fW8nL4Pj1tPoAzflKScLMNfBKO+zhcX18nS97e3l7Y3t4OW1tbYXNzM2FjYyOh3W47Y4DbF5iSeEcUHE2Xl5eh1+uFg4ODRNbu7m7odruh0+mUYmdn57/E2hZFwLZOScIfeW8h3LoG/zNdXFwky9/Z2VlyrnKqw5QEKArnJ1ySY/l7enpKpAEcZc74wbaWgkDm/e7kPe+c6pBOBoNB+As+VVeDb3tHdgAAAABJRU5ErkJggg==" alt="PiPER Product User Manual image 45" width="105"> <img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAGgAAAAzCAYAAAB7VU2VAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAOmSURBVHhe7ZzLTttAFIbzDCDyCGx5B54CFrwAWx6BRTet2i676KYL1hWVAAkhISBSEOqKi4CCuEMSbnmDqf4Rf3M0OpM4KB6P1PNLH5LneMx4PtuxF3at2+068vr6alSIdEH+CcIKLy8v7vn52fP09GQkRoohXhDlYKXHx0fX6XQ87XbbSEgoB9QgB2fMbevWzf+ad/UvdVf7UDMqQBUEOThbIEfrZKRDFQQ59/f3buLzhNrJSIcqqNVquYuLC7WDkRZV0N3dnTs9PVU7GGlRBd3c3Ljj42O1g5EWVdD19bU7OjpSOxhpiQo6PDxUOxhpMUGZowq6uroyQZlggjLHBGWOCcocE5Q5JihzShE09X3KFcnkt0m1v9GjFEESRrbVv9bfWp2XKWtlsPxn2aPVcqcSQUBKCmujBjFBEZhha6MEMUERmGFr00vTb9VetMvhwsbCW7UXtKEGKVpYJ9r/QptcB+Cs5/9bbCz6NhnUuW7R8Q8iKujg4EDtMCxM2M4bCe3I5iTIScKEIPLGgpETM/NzxrdxmevFziBKlJPHsVECkWE/jgvhOIqOvwiVCOIOILIdYAeQ8CgHjFzWJh4Jl7X1eJRDalijaO1MYrTaMOMvQjJBYbSdk+trNR61XGbkGaSBxEQiYTthirYPqoXjL0IyQVqbNrFM2K7VuMMILiExUcioBWnbYw0ZthajEkG8DPSbtH6R6/NSxMS2mVpQv2j9YlQiaFB7bOf7wR92RtaQlILeM/4YUUFl32Yz4V0NI9ti9PsBD9tSCkK02nuoTBAvTeHdDnYcid1EyHYk/N1hf9mGaBOKbSHa/+pXQ2KChhl/ESoThIllwhqDneUZxkuYFIrIW2RuM5w8hsvymYfRnoMQtkmQmCDADBp/EUoRJHcwjFyPRxsSPhTKB0AmPPq0dbQJQJtMuB0sh9GOdC1SrKTI+ItQiiBjdJigzDFBmWOCMscEZY4JyhwTlDkmKHNUQfZ2Qz6YoMxRBeEVSLxhN/5pXO1kpCMqCO+ozi3NqZ2MdKiC+Jb37u9dN/tj1o19HFM7G+WjCsJ3Ei4vL/1lrtlsus3NTbe+vu7W1tY8q6urnpWVFaMEOL9AFYQvjeAsOj8/d/v7+25vb8+LajQabmdnx21vb7+Lra2t/xJtLoqAuVYF8Vs9+BwMnonOzs78Je/k5MT/NhnpUAXxa1f4DBk+iYVL3sPDgxcGcHYZ5YO5VgXhT/i9OPnNOCMdoZxut+v+Apmx3YQlJ1XaAAAAAElFTkSuQmCC" alt="PiPER Product User Manual image 46" width="104"></div>

Robotic Arm e-stop button

### 3.7 Window zoom and close buttons <a href="#bsucj" id="bsucj"></a>

The three buttons on the upper right are window minimize, window maximize, and window close. Pressing them can realize the corresponding functions of the window.

<img src="../../.gitbook/assets/PiPER Product User Manual image 47" alt="PiPER Product User Manual image 47" width="616">

Window zoom and close button

### 3.8 Operation function area <a href="#ixawj" id="ixawj"></a>

The central area of the window is the operation function area, which can be switched synchronously by \[2. Vertical menu bar options] to switch to different partitions according to user needs. For example, the figure below is the motion control area, which can realize the actual joint control of the robot arm.

<img src="../../.gitbook/assets/PiPER Product User Manual image 48" alt="PiPER Product User Manual image 48" width="520">

Motion control area

### 3.9 Motion control <a href="#jem3c" id="jem3c"></a>

The robotic arm has a total of 6 joints, named Joint 1 to Joint 6 from bottom to top, corresponding to the 6 joint settings in the operation bar. Users can edit the joint degrees by themselves or click the plus and minus buttons to realize the joint operation of the robotic arm (unit: °).

<img src="../../.gitbook/assets/PiPER Product User Manual image 49" alt="PiPER Product User Manual image 49" width="444">

Joint degree

The 3 buttons below are ①Return to zero button, ②Load button, and ③Send button. Button ①: automatically sends the factory initial position angle value of the robot arm, button ②: fills the current degree of the 6 joints of the robot arm into the user edit bar, and button ③: sends the 6 joint degrees in the user edit bar to the robot arm. The specific content is subject to actual experience.

<img src="../../.gitbook/assets/PiPER Product User Manual image 50" alt="PiPER Product User Manual image 50" width="480">

Joint button

\
\
<br>

The picture below shows the lighting control area. If the joint light board is installed, the lighting control of the six joints of the robot arm can be realized.

<img src="../../.gitbook/assets/PiPER Product User Manual image 51" alt="PiPER Product User Manual image 51" width="519">

Light control area

The joint number and RGB channel above are the light board that the user needs to operate and the grayscale value of the corresponding channel. The effect bar below is the actual calculated light color. Click the \[Confirm] button to operate the light board.

### 3.10 Linkage control area <a href="#meygh" id="meygh"></a>

Note:

When using the robotic arm independently (i.e., not in master-slave teleoperation mode), you must first set it to slave mode!

<br>

If the arm is set to master mode, it cannot be controlled. You will need to use the host computer to switch it back to slave mode before operation.

The following figure shows the linkage control area. If the user needs to achieve dual-arm linkage, the Master and servant status and offset value can be configured on this page.

<img src="../../.gitbook/assets/PiPER Product User Manual image 52" alt="PiPER Product User Manual image 52" width="660">

Linkage control area

### 3.11 Gripper control area (valid only with grippers) <a href="#vrgl6" id="vrgl6"></a>

The following figure shows the gripper control area, where you can set the gripper enable status, torque value, etc. The right area of the host computer will feedback the corresponding gripper value.

<img src="../../.gitbook/assets/PiPER Product User Manual image 53" alt="PiPER Product User Manual image 53" width="637">

Gripper/claw setting area

### 3.12 oint setting area <a href="#makhy" id="makhy"></a>

The figure below shows the joint setting area, where you can edit the maximum and minimum angles, maximum speed, and maximum acceleration of the six joints of the robot arm. The operation process is \[Edit] - \[Save].

<img src="../../.gitbook/assets/PiPER Product User Manual image 54" alt="PiPER Product User Manual image 54" width="517">

Joint setting area

### 3.13 Speed setting area <a href="#acstf" id="acstf"></a>

The following figure shows the speed setting area, where the maximum linear speed and angular speed and the maximum linear acceleration and angular acceleration of the end of the robot arm can be set. The \[Initialization button] is used to restore the factory settings.

<img src="../../.gitbook/assets/PiPER Product User Manual image 55" alt="PiPER Product User Manual image 55" width="517">

End speed setting area

<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJ8AAABSCAIAAADFD5HdAAAACXBIWXMAABJ0AAASdAHeZh94AAAFVUlEQVR4nO2cXUhbZxiA36QVpbNq1bCuMUnFq0YwSwbC3I+1xOrKmloQjLU6iKzQgbYdkc3VbgPtLqrsxx86Igbmf8HW9qZTEufKZi5WWnexHm9E8KfiZuJ0qEVYk118cJpGPTkTNZ8v70MuTs77vcnLeXK+v5AoAoEAEEhRRroAYgchu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5ghu5jZLxFz3rq3a3UQW8ZWdGazkJRdADjxpkmpUGx3PcS24fY8koiG6ZlJ7Z6Gxl3MkF3MkF3MkF3MkF3MkF3MhFnvRhC/3z8zM+P1ehUKhUqVrFanKGh59j/h0e7q6urd/jvDw8M+n088maxSncw9+f7p0zExMWtraw8e/JydfTw6OjqCdfIPd3YFQai/cWNpaVGj0eTknHj18GEA+HNu7uHD37q7u1wuV3V19V/z89/fvJmQcCgzMzPS9XINX3Z9Pt+XX3weCATKyj6wnDmjVL6YFliLiwcHBjo62q9e/ayoyAoAz5//G7lK9wZ82Y2LiysoOJuVlXU0NTUkpFQq3zt1KsOQUWW39/ffiUh50pTbbADQ5nRGupAX8DVnjoqKOldSsl6tiFqdUlpatrS0tJtVycTtdkW6hFD4siuHvPz8ZJUKAOh/1MKy9+wqlcq0tDQAWFhYWB/1+bytDodOq2loqAcAnVbDHj6flzXweEbEkzqtZkwQgtNZrvhodTiCo5vllttsOq0GANxu14aJkYIXu4IglJWeF16+1ptxKCEBAP7ZqH82GY11dbUAMCaM6bSaisrK4Girw1Fstfb09k5OTU9OTVdUVubn501MTLCoTqupq6t9PDrKok3NLeylwua2OZ2TU9MAYDbnsuiHFy5s8UJsK7zY/X308fLy8sivv8hp/PY778bGxr5uNK0PsYsLAG63q6e3126vYmeSkpInJibq6mpraq5lZb3FGtvtVQCQczxbTDebc5OSktmxxWIRz8vJ5RBe7MbFxwPA34uLchrr9fr2jk69Xi/dTDTBYCZC7iqzOTf4qdvtEvtwAGAfFJm5HMKL3cTERAAYHx/3+/3b8oIyL33wRJelmIzGhob6YMdycvmEF7tsD9k7Pz84MLCjbxQ8LWJTIZE2p7OpuQUAmhobTUYjW7/KzOUTvnYz4uPjOzraMwwZanXKhg3m5uZmZ2dNpg1GXDmYzbnSuw0Wi8VisYwJQn5+HpsAi51z2FwO4eXeZRQUnFUoFFV2+4/374d00X6//25//6XKim+/+XrLvbd0X+rxjLCDY3q9KFVmLp/wYnffvv0A8NqRI9evf3XwYFxrq+PjK5e7Ojt/GhoaGhrq7uq8cvlSe/sPBw688smn1cH7z/Jhw6qoUEQ8U2y1Bg+3wSN32Fw+4cWuwWC4ePEjg8FwNDX1u8bGcyXnV589u327r7m5qaW5qa+vb2VlpbCwsLmlJT09fWtvwfrVYqu13GZj69QxQdBpNU/+eCK2GRnxsAOfz+t2u0TBcnIh6P4ek7dw32kUEvt5zlv3zFlv7GY1wQQCgadPZ+bnvYFAQKVSqdVqObdsyGRnYGDw2MsLp4aG+qbGRvFpT2+vuHAKCdXUXAtZAknkAkCrwyHufoSEdg6355HEbxH4tUvIQdouLz0zsROQXcyQXcyQXcyQXcyQXcyQXcyE+RZB+qfdBOdI7WYQex3qmTFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjFDdjHzH7YvAbKOTUVhAAAAAElFTkSuQmCC" alt="PiPER Product User Manual image 56" width="159">

Reset area

### 3.14 Collosion grade <a href="#kq7pl" id="kq7pl"></a>

The picture shows the collision level setting. The collision level of level 1 to level 8 can be configured for the 6 joints of the robot arm. The operation process is \[Edit] - \[Save].

碰撞等级设置区

### 3.15 Motor setting <a href="#yubzl" id="yubzl"></a>

The figure below shows the motor settings, which can be used to set the status (enable, disable), zero position setting, and clear errors of the six joint motors of the robot arm.

<img src="../../.gitbook/assets/PiPER Product User Manual image 58" alt="PiPER Product User Manual image 58" width="516">

Motor setting

### 3.16 Upgrade <a href="#rhgrp" id="rhgrp"></a>

The following figure is the page related to the robot version upgrade. The upgrade steps are as follows:

① Check whether there are words such as node information generated in the information display area (area 1). If there are words, it means that the robot has entered the upgrade state normally. If the check is correct, it can be upgraded normally;

② Click the \[Load Software Package] button (area 5), select the version firmware configured by R\&D (suffixed with bin), and after confirmation, the information area (area 4) will display the firmware package information selected by the user;

③ Click the \[Start Upgrade] button (area 6) and wait for the progress bar (area 2) to complete. The normal time is about 2\~3 minutes.

<img src="../../.gitbook/assets/PiPER Product User Manual image 59" alt="PiPER Product User Manual image 59" width="1265">

Upgrade area

### 3.17 3D simulation model <a href="#id-5cjz8" id="id-5cjz8"></a>

On the right side of the window is the real-time 3D simulation model of the robot arm. The upper left corner shows the real-time feedback coordinate values and 6 joint degrees of the current robot arm. The three buttons below are ① Help, ② View Restore, and ③ Settings. Button ①: Pop-up window displays the usage of the 3D area, button ②: Restore the original 3D display view, and button ③: Set various parameters of the host computer. The specific content is subject to actual experience.

<img src="../../.gitbook/assets/PiPER Product User Manual image 60" alt="PiPER Product User Manual image 60" width="994">

3D simulation model

### 3.18 TraceLib <a href="#ahc0h" id="ahc0h"></a>

Click the \[TraceLib] below the vertical menu bar, and a pop-up window will appear. Users can customize and edit a complete robot arm motion trajectory and run it.

<img src="../../.gitbook/assets/PiPER Product User Manual image 61" alt="PiPER Product User Manual image 61" width="1280">

&#x20;

<img src="../../.gitbook/assets/PiPER Product User Manual image 62" alt="PiPER Product User Manual image 62" width="1010">

轨迹库弹窗

① Import: Import the local trajectory library log file.

② Create: Create a new motion trajectory.

③ Delete: Delete the selected trajectory.

④ Send: Send the selected trajectory to make the robot arm run the trajectory once, multiple times, or in a cycle.

⑤ Export file: Export the selected trajectory to the local.

At the same time, the user can double-click any trajectory to enter the secondary menu, edit the specific content of the trajectory (as shown below), and right-click to add, delete, modify, and check.

<img src="../../.gitbook/assets/PiPER Product User Manual image 63" alt="PiPER Product User Manual image 63" width="1280">

TraceLib secondary menu

### 3.19 Robotic arm joint status button <a href="#ovsfh" id="ovsfh"></a>

Click the robot arm joint status button at the bottom left of the window, and a \[Joint Status] window will pop up (as shown below), which will monitor the status information of the 6 joints in real time. The button will monitor and display the current status in real time according to the status of the connected joints (as shown below).

<img src="../../.gitbook/assets/PiPER Product User Manual image 64" alt="PiPER Product User Manual image 64" width="757">

Joint status window

<div><img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAALYAAABNCAYAAAALpZ7eAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAEnQAABJ0Ad5mH3gAAAViSURBVHhe7Z29bhs5FEYNWOqsx/CbpLBUqJK6tFKXN8gDpJUDbJdSSrVAmgWCNCpWgIEUBoINjAUW+vFDuOb6jHENLnMpKWtn5KG+4sA2L38k85Bzh1PMyd3dXRCiNCS2KBKJLYpEYosikdiiSCS2KJKfFnu5XIbJZBIuLi7C+fl5ODs7CycnJ0I8GVzCKdzCMVzzHNyHvcVerVZhNBqF09NT90MJ8dy0Wq3KufV67Tq5jb3Ens1modPpVIO12+3Q7/fD5eVlmM/n4ebmJtze3grxZHAJp3ALx3AN53BvOp26bubYKXav13tcQd1uNywWC/dDCfHc4BrOmX+46DnqsVVsVol1OhwOw2azcT+AEL8KnMM985DswXM1JSs2ObWlH3TsDSpEXQwGg8pFnNwn586KTdJOR2z/2qnFocFBS0vG47HrbIwrNscsnH6QvCunFi8FXOSkBMgoPHcNV2zOEFkZ3Jl6AwhxKHASNzk58dw1XLE5ILfGXudCHAqcxE0c9dw1XLF5+kNjzhS9zoU4FDiJmzjquWu4Yttjcj18ES8NnMRNHPXcNVyxaQhex0IcGvPTc9eQ2KJxSGxRJBJbFInEFkUisUWRSGxRJBJbFInEFkUisUWRSGxRJBJbFInEFi7X/1y75U1BYotH3l+9Dye/3c/rPa9+f+XWaQpHLbZNopHGP//1+Yc6Xr1S4PsiNN9RYjudNg0T9uP1RzcOJQudIrELExtyuaXEbhYS+x4m8s2XN49y5+p45SUisQsS234CuWaujgcpjLU1vLSGq8Hb+dsqzkKiLG5D/Pvye9X29R+vw/xmHq7+vvpPG+K0I2blwO8WS/E+37ZTD+IS2+m0aTCR/EQWm/hcnRQEIBYvBrvpNHkN6xusXXylQDZOJqzsw9cP1e/0Z32++/PdY51P3z5Vn5l6FovHA5PaPh9j8DekdQ1iEtvptGnEk2xHXunEeiKYNLRJY9aPt3NTnosZxNm1410YcXPt2LE9GW2suMwWVVwWQ0xiO502jXSSTYZ4F/ZEsHppuZGL72oHxNmJ4zLbmeOyXTG+Q7rwJPYDRye2d7n2REjrpOTilO0ShzrPIXYM3yvOy706QExiO502DW+S05TEq0OZV27k4pTVKXZ878AOzti5ukBMYjudNo3cJJsMJkYunpYbuThldYltN51xWiWxHzhaseOUxKuTKze2tatLbMrScon9wNGKDZaSeHXsVMQ7pdgWo7xOsdOxKMv1A16bpiGx79k2ybBNBIvFl3q7/G9rU6fYwAK1xWaQYnFV8tpIbKfTphBPshELalhKkpYbqTCQ26lT0vEQkPNri9tRXXzlQDor58lk/JCHtjy4sf7iRQb8nUux4jLD+380gaMWW5SLxBZFIrFFkUhsUSQSWxSJxBZFIrFFkUhsUSQSWxSJxBZFIrFFkfxvsfUCU/FSedILTPXKafFSedIrp3kBO415IbvXuRCHAidxE0c9dw1X7MlkUjXu9/tu50IcCpy0Tddz13DFXi6XodVqhXa7HRaLhTuAEHWDi3gJq9XqB29jXLFhNBpVK6Pb7YbNZuMOJERd4CAu4uR4PHadjcmKvV6vQ6fTqToaDofuYELUxWAwqFzESdz0nI3Jig3T6bTqDOhYO7eoG5wzqWE2m7mupmwVG3q93mOnXAqUc4u6wDVLPwAXPUc9dooNrBJLS7ih5M6Uu1LOFPUQRzwXuIRTuIVj3CTiHO6RPXhu5thLbOAulKTdBhPiV4NrOLdPTp2yt9gGgrOiOCDn6Y89fhfiqeASTuEWju060tvGT4stRBOQ2KJIJLYoEoktikRiiyKR2KJIJLYokLvwL8adm5wzUQCRAAAAAElFTkSuQmCC" alt="PiPER Product User Manual image 65" width="182"> <img src="../../.gitbook/assets/PiPER Product User Manual image 66" alt="PiPER Product User Manual image 66" width="190"></div>

Joint status

### 3.20 Robotic arm status <a href="#ccvqo" id="ccvqo"></a>

The robot arm status bar at the bottom right of the window will monitor the robot arm status information in real time (as shown below).

<img src="../../.gitbook/assets/PiPER Product User Manual image 67" alt="PiPER Product User Manual image 67" width="404">

Robotic arm status

<br>

## 4 Secondary Development <a href="#mdj0o" id="mdj0o"></a>

Currently, the robotic arm supports secondary development through a Python SDK and ROS1 & ROS2 driver package. For detailed secondary development instructions, please refer to the GitHub link.

| Content     | Linkage                                                                                                                                                                     |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| SDK         | [https://github.com/agilexrobotics/piper\_sdk](https://github.com/agilexrobotics/piper_sdk)                                                                                 |
| SDK-DEMO    | [https://github.com/agilexrobotics/piper\_sdk/tree/master/demo](https://github.com/agilexrobotics/piper_sdk/tree/master/demo)                                               |
| SDK-UI      | [https://github.com/agilexrobotics/Piper\_sdk\_ui](https://github.com/agilexrobotics/Piper_sdk_ui)                                                                          |
| ROS1-NOETIC | [https://github.com/agilexrobotics/Piper\_ros/tree/ros-noetic-no-aloha](https://github.com/agilexrobotics/Piper_ros/tree/ros-noetic-no-aloha)                               |
| ROS2-HUMBLE | [https://github.com/agilexrobotics/Piper\_ros/tree/ros-humble-no-aloha](https://github.com/agilexrobotics/Piper_ros/tree/ros-humble-no-aloha)                               |
| URDF        | [https://github.com/agilexrobotics/piper\_ros/tree/noetic/src/piper\_description/urdf](https://github.com/agilexrobotics/piper_ros/tree/noetic/src/piper_description/urdf)  |
| MOVEIT2     | [https://github.com/agilexrobotics/piper\_ros/tree/humble/src/piper\_moveit](https://github.com/agilexrobotics/piper_ros/tree/humble/src/piper_moveit)                      |
| MOVEIT      | [https://github.com/agilexrobotics/piper\_ros/tree/noetic/src/piper\_moveit](https://github.com/agilexrobotics/piper_ros/tree/noetic/src/piper_moveit)                      |
| GAZEBO      | [https://github.com/agilexrobotics/piper\_ros/tree/noetic/src/piper\_sim/piper\_gazebo](https://github.com/agilexrobotics/piper_ros/tree/noetic/src/piper_sim/piper_gazebo) |
| ISSAC SIM   | [https://github.com/agilexrobotics/piper\_isaac\_sim](https://github.com/agilexrobotics/piper_isaac_sim)                                                                    |
| ISSAC SIM   | [https://github.com/agilexrobotics/piper\_isaac\_sim](https://github.com/agilexrobotics/piper_isaac_sim)                                                                    |

<br>

## 5 CAN protocol <a href="#jxp90" id="jxp90"></a>

The robot arm provides a CAN interface for user development, through which users can control the robot arm with commands.

The CAN communication standard in the robot arm adopts the CAN2.0B standard, the communication baud rate is 1000K, and the message format adopts the MOTOROLA (MSB) format.

If you need to use CAN command development, please contact Songling Technical Support to obtain the CAN protocol manual.

## 6 Maintenance and Servicing <a href="#f7c6z" id="f7c6z"></a>

To ensure the robotic arm maintains high performance over the long term, regular maintenance and servicing are essential. All maintenance operations must be carried out in strict accordance with the instructions provided in this manual. The purpose of maintenance and servicing is to ensure the proper functioning of the robotic arm and its accessories.

## 7 Maintenance Precautions <a href="#gxtjd" id="gxtjd"></a>

All maintenance procedures must be performed after the robotic arm is powered off and returned to its zero position. Once powered off, proceed with the following operations:

* Robotic Arm Cleaning: Use wet wipes or a dry cloth dampened with water to clean dust, dirt, and oil stains from the surface of the robotic arm.
* Screw Tightness Check: Inspect all screws to ensure none are loose.
* Motor Inspection: Check the motors and associated structural components for any signs of damage or deformation.
* Cable Inspection: Ensure power cables and CAN cables are securely connected, and check for any visible damage or wear on the cable insulation.

## 8 Emergency Handling <a href="#wgpyi" id="wgpyi"></a>

**Power-Off**

In emergency situations, power can be cut off directly by unplugging the aviation connector.

Caution: After power-off, the robotic arm will become disabled and may drop abruptly. Please take precautions to prevent damage to the robotic arm, surrounding equipment, or personnel.

Unplugging the power is an emergency measure only, and is not intended as a safety mechanism to prevent injury.

<br>

**Emergency Stop**

When connected to the host computer, the robotic arm can be paused or resumed by using the Pause button in the control interface.

## 9 Dimensional drawings <a href="#bvwrf" id="bvwrf"></a>

### 9.1 Zero position <a href="#sqpyj" id="sqpyj"></a>

<img src="../../.gitbook/assets/PiPER Product User Manual image 68" alt="PiPER Product User Manual image 68" width="1067">

### 9.2 Axonometric drawing of the robotic arm <a href="#mmlvy" id="mmlvy"></a>

<img src="../../.gitbook/assets/PiPER Product User Manual image 69" alt="PiPER Product User Manual image 69" width="744">

### 9.3 Robotic arm with leader gripper <a href="#id-3fczs" id="id-3fczs"></a>

<img src="../../.gitbook/assets/PiPER Product User Manual image 70" alt="PiPER Product User Manual image 70" width="850">

### 9.4 Robotic arm with follower gripper <a href="#nssju" id="nssju"></a>

<img src="../../.gitbook/assets/PiPER Product User Manual image 71" alt="PiPER Product User Manual image 71" width="733">

### 9.5 Base <a href="#bnyxd" id="bnyxd"></a>

<br>

### 9.6 End of the arm <a href="#bf5qo" id="bf5qo"></a>

<img src="../../.gitbook/assets/PiPER Product User Manual image 73" alt="PiPER Product User Manual image 73" width="693">

### Development Resources

* [pyAgxArm Python SDK](https://github.com/agilexrobotics/pyAgxArm) — current official SDK for PiPER, PiPER-H, PiPER-L, and PiPER-X.
* [PiPER SDK repository](https://github.com/agilexrobotics/piper_sdk) — legacy and V2 Python interfaces, CAN setup, examples, and release history.
* [AgileX arm ROS 2 driver](https://github.com/agilexrobotics/agx_arm_ros/tree/ros2) — select the exact model with `arm_type:=piper`, `piper_h`, `piper_l`, or `piper_x`.
* [PiPER-series URDF, Xacro, and mesh resources](https://github.com/agilexrobotics/agx_arm_urdf) — separate official model directories are provided for PiPER, PiPER-H, PiPER-L, and PiPER-X.
* [PiPER-series firmware compatibility reference](https://github.com/agilexrobotics/pyAgxArm/blob/master/docs/piper/firmware_reference.md) — read the arm firmware first and choose the matching SDK driver; PiPER-X has additional version-specific joint-sign behavior. This page is a compatibility reference, not a firmware binary download.
