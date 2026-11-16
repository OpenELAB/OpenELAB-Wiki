---
description: >-
  Official V1.0 user guide for the DOBOT Magician E6 ROS mobile platform; the
  robot arm is sold separately.
---

# DOBOT E6 Robot ROS Mobile Platform User Guide

## DOBOT Magician E6 ROS Mobile Platform Without Robot Arm

{% embed url="https://openelab.io/products/dobot-e6-ros-mobile-platform" %}

[Official manual PDF](https://dobot-cloud-1256299428.cos.ap-guangzhou.myqcloud.com/pro/1763689147857_Dobot%20E6%20Robot%20ROS%20Mobile%20Platform%20User%20Guide_V1.0_20251121_en.pdf)

## Contents

* Preface
* 1\. Introduction
* 2\. Robot specifications and Parameters
* 3\. Introduction of robot Installation and Expansion Interface
* 4\. Basic Operations
* 5\. Bobac3 Hardware Detection
* 6\. Comprehensive Application
* 7\. Robot ROS Development API
* Appendix:
* 8\. Precautions and Maintenance
* 9\. Appendix

## Copyright and Disclaimer

### Copyright © SHENZHEN DOBOT CORP LTD 2025. All rights reserved.

No part of this document may be reproduced or transmitted in any form or by any means without the prior written consent of SHENZHEN DOBOT CORP LTD (hereinafter referred to as “Dobot”).

### Disclaimer

To the maximum extent permitted by applicable law, the products described (including its hardware, software and firmware, etc.) in this document are provided **AS IS** , which may have flaws, errors or faults. Dobot makes no warranties of any kind, express or implied, including but not limited to, merchantability, satisfaction of quality, fitness for a particular purpose and non-infringement of third party rights. In no event will Dobot be liable for any special, incidental, consequential or indirect damages resulting from the use of our products and documents.

Before using our product, please thoroughly read and understand the contents of this document and related technical documents that are published online, to ensure that the robot arm is used on the premise of fully understanding the robot arm and related knowledge. Please use this document with technical guidance from professionals. Even if follow this document or any other related instructions, damages or losses may happen in the using process. Dobot shall not be considered as a guarantee regarding all security information contained in this document.

The user has the responsibility to make sure following the relevant practical laws and regulations of the country, in order that there is no significant danger in the use of the robot arm.

SHENZHEN DOBOT CORP LTD Address: Room 1003, Building 2, Chongwen Garden, Nanshan iPark, Liuxian Blvd, Nanshan District, Shenzhen, Guangdong Province, China

Website: www.dobot-robots.com

## Preface

#### Purpose

This document describes the functions, technical specifications, installation guide of Dobot E6 Robot ROS Mobile Platform, making it easy for users to fully understand and use it.

#### Intended audience

This document is intended for:

* Customer
* Sales Engineer
* Installation and Commissioning Engineer
* Technical Support Engineer

### Revision history

| Date       | Version | Change         |
| ---------- | ------- | -------------- |
| 2025-11-21 | V1.0    | First release. |

#### Symbol conventions

The symbols that may be found in this document are defined as follows.

| **Symbol**  | **Description**                                                                                                                                             |
| ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **DANGER**  | <p>Indicates a hazard with a high level of risk which, if not avoided,<br>could result in death or serious injury.</p>                                      |
| **WARNING** | <p>Indicates a hazard with a medium level or low level of risk which, if<br>not avoided, could result in minor or moderate injury, robot arm<br>damage.</p> |
| **NOTICE**  | <p>Indicates a potentially hazardous situation which, if not avoided,<br>could result in robot arm damage, data loss, or unanticipated<br>result.</p>       |
| **NOTE**    | <p>Provides additional information to emphasize or supplement<br>important points in the main text.</p>                                                     |

## 1. Introduction

The robot is a service robot developed using ROS. It not only features a control interface for its underlying development board but also comes equipped with a variety of extended sensors, such as a depth camera, ultrasonic sensor, smoke sensor, and temperature and humidity sensor. These sensors are like adding eyes, a nose, and a mouth to the robot, enhancing its functionality and enabling it to perform various tasks more intelligently.

The robot service robot can be equipped with an open-source kit designed for the development of various service robots. This kit includes a scalable mobile chassis, a human-machine interaction unit, a food delivery rack, and a disinfection kit. It can support the development of platforms for welcoming robots, food delivery robots, and medical service robots, as well as other types of service robots, such as those equipped with collaborative arms to become picking robots.

**Figure 1.1 Generic chassis - Human-robot interface unit**

ROS (Robot Operating System) is an open-source, general-purpose platform for developing robot software. The project originated from a collaboration between the STAIR project at Stanford University's Artificial Intelligence Laboratory and Willow Garage's Personal Robots Program in 2007. Over the years, ROS has become the most widely used general-purpose robot software development platform globally.

ROS is now maintained and managed by the Open Sour Robotics Foundation.

The biggest features of this operation platform are:

* Universality: At present, dozens of robot research and development institutions

![Official manual image, source page 7](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FdaOywku0WtrWIiHYSs8d%2Fe6-ros-p007-img02.png?alt=media)

and robot manufacturing companies around the world announce that the robots they have developed support ROS every year, which means that more and more robot companies around the world have taken ROS as the standard robot development platform.

* Open source: A large number of open source robot applications are provided on the official website of ROS for users to download and use. Robot developers can easily understand and engage in cutting-edge topics in the field of robot research.
* Reusability: The ROS modular development environment makes it possible to reuse programs, allowing robot developers to use programs that have already been developed by others while focusing on new features.
* Community: Currently, the official ROS forum has brought together a large number of robot developers from around the world. Through collaborative discussions and development efforts, they have made robot development work simpler and more convenient.

This document focuses on how to use this robot, covering hardware introductions, basic function usage, and comprehensive case studies that integrate these functions. We hope that users will learn more about the ROS platform while using the robot and develop their own functional applications. If any issues arise during use, please feel free to contact us promptly. We hope you enjoy the joy of technology with robot.

## 2. Robot specifications and Parameters

| **No.** | **Parameter name** | **Specifications**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | **Quantity** |
| ------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| 1       | Overall parameters | <p>1. The platform has four degrees of freedom for<br>mobility. It can move in the xy plane, rotate in the<br>plane, perform horizontal rotation, and nod its<br>head through three omnidirectional wheels. Each<br>of the robot's three wheels is equipped with an<br>independent spring pneumatic suspension<br>system, which effectively reduces vibrations<br>during movement.<br>2. Maximum speed of the robot: linear speed<br>0.6m/s, angular speed 0.8rad/s;<br>3. Large range positioning and navigation accuracy:<br>5cm;<br>4. Key points use visual secondary positioning to<br>achieve high precision of 2mm;<br>5. sensors: depth camera<em>1; 2D LiDAR</em>2; visual<br>intercom<em>1; auxiliary positioning camera</em>1; far-<br>field microphone array<em>1; 13-inch touch screen</em><br><em>LCD</em>1; ultrasonic sensors<em>3; temperature and</em><br><em>humidity sensor</em>1; smoke sensor<em>1, carbon</em><br><em>dioxide sensor</em>1, light intensity sensor<em>1;</em><br><em>6. Software system: ubuntu20.04+ROS, integrated</em><br><em>learning system and development system, power</em><br><em>failure reset of learning system, setting</em><br><em>permission of development system;</em><br><em>7. Full power operation time: 3h;</em><br><em>8. Standby time: 6h;</em><br><em>9.Overall size: 377mm</em>377mm*798mm.</p> | 1            |
| 2       | Robot controller   | <p>CPU: i5; Memory: 4G; Hard disk: 120G SSD.<br>Interface: RS232<em>5, RS485</em>1, network port <em>2,</em><br><em>support wifi, USB3.0</em>4, USB2.0*4.<br>System: The EROS system is a dedicated AI robot<br>system.<br>It includes: (1) 3D visual simulation scenarios, (2) an<br>integrated deep learning framework, Tensorflow, (3)</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 1            |

| **No.**             | **Parameter name**                                                | **Specifications**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | **Quantity**         |
| ------------------- | ----------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------- |
|                     |                                                                   | <p>various commonly used sensor drivers, such as 2D<br>cameras, 3D cameras, depth cameras, LiDAR, and<br>IMU, (4) common robot localization and mapping<br>algorithms, including gmapping and cartographer, (5)<br>common path planning algorithms, such as A*, D*,<br>DWA, and TEB.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |                      |
| 3                   | <p>Touch<br>LCD<br>with<br>speaker</p>                            | <p>Screen size: 13 inches; speaker: stereo full range;<br>resolution: 1440 x 900, touch screen type: capacitive<br>screen.</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | 1                    |
| <p>4<br>5</p>       | <p>Drive and control<br>integrated controller<br>Depth camera</p> | <p><br>board integration: 4 channels of 120W DC<br>servo motor drive;<br><br>interfaces: 4 motor drive interfaces, 4 motor<br>encoder interfaces, 3 collision sensors with 5V<br>power supply, 3 fall prevention sensors with 5V<br>power supply, 3 ultrasonic sensors with 5V<br>power supply, 1 temperature and humidity<br>sensor with 5V power supply, 1 smoke alarm<br>sensor with 5V power supply, 1 RS232<br>interface for communication with the host<br>computer, 1 RS485 interface with 5V power<br>supply, and 1 CAN interface with 5V power<br>supply.<br><br>Power output: 12V/5A,5V/5A<br><br>Input voltage: 12-30V<br><br>Function: Drive the speed closed-loop control<br>of more than 4 DC servo motors, receive speed<br>control instructions through RS232, upload the<br>distance of 3 ultrasonic sensors, the status of 3<br>collision sensors, the status of 3 anti-fall<br>sensors, the status of 1 smoke sensor and the<br>information of 1 temperature and humidity<br>sensor.<br>Color image resolution: 1280x720, frame rate: 30fps<br>or more; Depth image resolution: 1280x1024, frame<br>rate: 7fps or more; Measurement range: 8 meters.</p> | <p>1<br>1</p>        |
| <p>Issue V<br>6</p> | <p>1.0 (2025-11-21)<br>2D LiDAR</p>                               | <p>User Guide<br>Copyright © SHENZHEN DOBOT<br>Measurement range: 360<code>°</code>; measurement distance:</p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | <p>CORP LTD<br>2</p> |

| **No.** | **Parameter name**                           | **Specifications**                                                                                                                                                                                                                                                           | **Quantity** |
| ------- | -------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
|         |                                              | 10000mm; Angle resolution: 1`°`                                                                                                                                                                                                                                              |              |
| 7       | <p>Auxiliary positioning<br>camera</p>       | <p>Highest frame rate: 1280*720/30 frames; support for<br>global shutter;</p>                                                                                                                                                                                                | 1            |
| 8       | <p>Interactive<br>recognition camera</p>     | <p>Resolution: 1920x1080 (1280 x720); Frame rate:<br>30fps; Function requirements: support autofocus,<br>built-in microphone</p>                                                                                                                                             | 1            |
| 10      | <p>Automatic charging<br>dock</p>            | <p>Input voltage: 25.4V; Charging current: 2A; Automatic<br>charging guidance mode: QR code</p>                                                                                                                                                                              | 1            |
| 11      | DC servo motor                               | <p>Encoder line: 500 lines; reduction ratio: 27:1<br>(planetary gear reduction); rated torque: 1.3Nm; rated<br>speed: 230r/min; power: 30W, supply voltage: DC<br>24V, no-load current: 130ma.</p>                                                                           | 3            |
| 12      | Ultrasonic sensor                            | <p>Working power supply: 5V; measurement distance:<br>750cm, resolution: 1cm, corresponding frequency:<br>15HZ, maximum beam angle: 60.</p>                                                                                                                                  | 2            |
| 13      | Battery + charger                            | <p>Input voltage: 25.4V; output voltage: 21.6-25.2V;<br>number of battery series: 6; battery capacity:<br>5200mAh, continuous current: 20A.</p>                                                                                                                              | 1            |
| 14      | <p>Temperature<br>and<br>humidity sensor</p> | <p>Temperature accuracy:<code>±</code>0.8<code>°</code>;<br>Temperature measurement range: -10<code>°</code>~50<code>°</code>;<br>Temperature resolution: 0.1℃;<br>Humidity accuracy:<code>±</code>3%RH;<br>Humidity range: 0%RH-100%RH;<br>Humidity resolution: 0.1%RH;</p> | 1            |
| 15      | Accessories                                  | <p>Wireless mouse: 1 set, controller: 1 set, experiment<br>guide: 1 copy, user guide: 1 copy.</p>                                                                                                                                                                            | 1            |

|**No.**\
B1|**Name**\
E-stop button|**Description**\
Control the motor servo. Press the emergency stop switch to cut off the\
power of the motor encoder, and the motor loses the servo. Turn it open to\
control the motor normally. In case the robot loses control or flies, press\
this switch to stop robot in time.|

|B2|Switch button|The total switch for all parts of bobac3 is powered on. When the power\
switch is turned off, all parts stop working.| |B3|Main switch\
button|The main start button for bobac3| |D1|High resolution\
touch screen|The bobac3 screen allows for simple touch operations. Built-in speaker.| |D2|Wifi antenna|Enhance the WiFi signal reception of bobac3.| |D3|All-direction\
wheels 1|Driven by DC servo motor, built-in encoder and shock absorption\
structure.| |D4|All-direction\
wheels 2|Driven by DC servo motor, built-in encoder and shock absorption\
structure.| |D5|All-direction\
wheels 3|Driven by DC servo motor, built-in encoder and shock absorption\
structure.| |S1|Auto-focus\
camera|For face recognition, expression analysis and other visual applications.\
Built-in microphone.|

![Official manual image, source page 13](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F2um2Y9evqVgp14oUrpS2%2Fe6-ros-p013-img02.png?alt=media)

|**No.**|**Name**\
|**Description**|

|S2|Temperature and\
humidity sensor|Temperature and humidity can be detected.| |S3|Smoke\
transducer|It can detect flammable gas| |S4|Depth camera|RGB, depth and other data can be obtained, which can be used for\
common visual recognition, local obstacle avoidance and other\
applications.| |S5|Ultrasonic sensor\
1|It makes up for the defect that laser sensors cannot detect transparent| |S6|Ultrasonic sensor\
2|substances such as glass.| |S7|Global shutter\
camera|Images with a maximum of 60 frames per second can be obtained for\
visual assisted positioning.| |S8|Rear 2D LiDAR|Obtaining distance data between two planes is usually used for mapping,\
obstacle avoidance and other functions.| |S9|Front 2D LiDAR|Obtaining distance data between two planes is usually used for mapping,\
obstacle avoidance and other functions.| |I1|Charging port|Adapter charging port.| |I2|USB3.0|USB devices can be accessed| |I3|USB3.0|USB devices can be accessed| |I4|Wireless charging\
port|When paired with the charging base, automatic charging can be achieved.| |I5|LAN|Local LAN interface| |I6|USB3.0|Can be connected to USB devices| |I7|48V power supply\
output|Can provide 48V direct current| |I8|IO port|Expansion terminal block|

## 3. Introduction of robot Installation and Expansion Interface

### 3.1 Description of robot expansion interface

All interactions and extension interfaces of the robot are integrated at the top, as shown in the figure below. It is mainly composed of three parts: interaction box, embedded extension interface and quick installation panel.

Among them, the interface and switch button on the interactive box are mainly used for normal startup, charging, and interactive devices such as mouse, keyboard, wireless arm, etc. which are used for general interaction between human and robot;

The built-in expansion interface is mainly used for the upper-level expansion platform of the robot, such as screen, control of the disinfection platform, common ground of various equipment, etc., which is used for the mutual control between the upper-level application equipment and the robot chassis;

The quick installation panel with profile panels can be quickly fixed on the platform by profile nuts, and the whole panel is profile panels. The installation position is flexible, and there is no need to drill screw holes to fix the upper equipment on the robot chassis.

The specific locations of each interface are shown in the following pictures, and the functions of each interface button are shown in the following table.

![Official manual image, source page 15](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0FZhFj1dnd4lYFg6SePF%2Fe6-ros-p015-img02.jpg?alt=media)

| **No.** | <p><strong>Name</strong><br></p>         | **Quantit** | <p><strong>y</strong><br><strong>Description</strong></p>                                                                                                                                                                                                                  |
| ------- | ---------------------------------------- | ----------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1       | <p>Expand network<br>interface</p>       | 1           | <p>Directly connected to the underlying robot controller,<br>enabling<br>expansion<br>of<br>network<br>communication<br>devices.</p>                                                                                                                                       |
| 2       | <p>48V power<br>supply interface</p>     | 1           | Provide 48V DC output                                                                                                                                                                                                                                                      |
| 3       | <p>USB 3.0<br>expansion<br>interface</p> | 1           | <p>The USB is directly connected to the underlying robot<br>controller and is used when external expansion<br>devices are connected, such as the end camera<br>attached to the arm.</p>                                                                                    |
| 4       | <p>IO expansion<br>interface</p>         | 4           | <p>Multifunctional expansion interface, integrating 24V,<br>12V, and 5V power supply, 1 relay output, 4 NPN IO<br>outputs, and 4 IO inputs. The power supply for the<br>upper platform and some general control functions are<br>provided through this expansion port.</p> |
| 5       | <p>Automatic<br>charging port</p>        | 1           | <p>In conjunction with the charging dock to achieve<br>automatic charging, only a 54.6V lithium battery<br>charger can be connected, and the current is less than<br>5A. Remember not to connect the power adapter</p>                                                     |
| 6       | Charging port                            | 1           | <p>The manual charging port can only be connected to<br>the 54.6V lithium battery charger with a current of less<br>than 5A. Remember not to connect the power adapter</p>                                                                                                 |
| 7       | Start button                             | 1           | <p>Press the robot startup switch. Press "On" to turn it on.<br>Press "Off" to turn it off.</p>                                                                                                                                                                            |
| 8       | <p>Main power<br>switch</p>              | 1           | <p>The main power switch for the robot. If it is not<br>activated after being pressed, please charge the robot.</p>                                                                                                                                                        |
| 9       | E-stop button                            | 1           | Emergency braking of the robot                                                                                                                                                                                                                                             |
| 10      | Antenna terminal                         | 2           | Antenna connector for WIFI connection.                                                                                                                                                                                                                                     |
| 11      | <p>Interconnected<br>USB port</p>        | 2           | <p>It is mainly used for devices such as mice, keyboards,<br>wireless controllers, USB drives, etc.</p>                                                                                                                                                                    |

**Figure 3.1 Built-in extension interface**

**Figure 3.2 Built-in extension interface**

![Official manual image, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FFvVAwyLuCuA05jFPGMEf%2Fe6-ros-p017-img02.jpg?alt=media)

![Official manual image, source page 17](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeAsrivV0qC7SqvL7mvxq%2Fe6-ros-p017-img03.jpg?alt=media)

**Figure 3.3 Bottom automatic charging port**

**Figure 3.4 Interactive boxes**

#### Expansion I/O interface

![Official manual image, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FfLYK93aB663jQoEBXQfP%2Fe6-ros-p018-img02.jpg?alt=media)

![Official manual image, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrRTZTLC2tnjPr3TbDBMg%2Fe6-ros-p018-img03.jpg?alt=media)

![Official manual image, source page 18](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F1BpJrUNCkySGXfUcfQ7B%2Fe6-ros-p018-img04.jpg?alt=media)

#### The specific interface pin is defined as follows:

| **No.** | **Signal**  | <p><br><strong>Interface type</strong></p> | <p><br><strong>Description</strong></p>                                                                         |
| ------- | ----------- | ------------------------------------------ | --------------------------------------------------------------------------------------------------------------- |
| 1       | 24V         | Power supply                               | <p>The output voltage is the internal battery voltage, 20V-25.4V,<br>and the maximum output current is 10A.</p> |
| 2       | GND         | Power supply                               | Power ground                                                                                                    |
| 3       | 2V          | Power supply                               | 12V constant voltage output, maximum output current 7A                                                          |
| 4       | GND         | Power supply                               | Power ground                                                                                                    |
| 5       | 5V          | Power supply                               | 5V constant voltage output, maximum output current 7A                                                           |
| 6       | GND         | Power supply                               | Power ground                                                                                                    |
| 7       | K+          | Switch output                              | <p>At the output end of the relay, K+ and K-are on during output,<br>5A/250VAC, 5A/30VDC</p>                    |
| 8       | K-          | Switch output                              | <p>At the output end of the relay, K+ and K-are on during output,<br>5A/250VAC, 5A/30VDC</p>                    |
| 9       | OUT1        | IO output                                  | <p>NPN common ground output, maximum output current<br>250mA</p>                                                |
| 10      | OUT2        | IO output                                  | <p>NPN common ground output, maximum output current<br>250mA</p>                                                |
| 11      | OUT3        | IO output                                  | <p>NPN common ground output, maximum output current<br>250mA</p>                                                |
| 12      | OUT4        | IO output                                  | <p>NPN common ground output, maximum output current<br>250mA</p>                                                |
| 13      | IN1         | IO input                                   | IO input, connected to GND trigger                                                                              |
| 14      | IN2         | IO input                                   | IO input, connected to GND trigger                                                                              |
| 15      | IN3         | IO input                                   | IO input, connected to GND trigger                                                                              |
| 16      | IN4         | IO input                                   | IO input, connected to GND trigger                                                                              |
| Issue V | 1.0 (2025-1 | 1-21)                                      | <p>User Guide<br>Copyright © SHENZHEN DOBOT CORP LTD</p>                                                        |

NPN common ground output internal electrical diagram:

IO input internal electrical diagram:

### 3.2 Installation and disassembly of the welcome kit

The intelligent interaction kit should be installed in advance before installation.

The welcome kit and chassis are securely fastened to the profile groove pit using 8 T-nut blocks and matching hex bolts. During installation, it automatically aligns, requiring only the tightening of the bolts. To disassemble, simply loosen the T-nut blocks and shake the kit to remove it.

![Official manual image, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FOSud0WYT67Smh3DmSdeH%2Fe6-ros-p020-img02.png?alt=media)

![Official manual image, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAVMiOdi3kjbOd8utNvv8%2Fe6-ros-p020-img03.png?alt=media)

![Official manual image, source page 20](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNCi9nmx4ahenMIFl5j9D%2Fe6-ros-p020-img04.png?alt=media)

## 4. Basic Operations

Starting with this chapter, the next section will run through all the functions of the robot.

**NOTE** The robot is configured with Ubuntu 20.04. To open the terminal, use the 'Ctrl+Alt+T' shortcut and run the commands provided in the corresponding steps. When you are done or starting a new experiment, to prevent process conflicts, it is recommended to terminate the running program by pressing 'Ctrl+d' (it is not advisable to directly close the terminal while the program is running). **Refer to the** **Appendix** for the creation and modification of the necessary files.

### 4.1 Joystick control for vehicle

Function: After connecting to the controller interface, the robot can be controlled by publishing messages via the joystick, enabling movement control.

#### 4.1.1 Start the chassis and controller nodes

Open a terminal (Ctrl+Alt+t) and enter the following command to open the chassis node:

```bash
roslaunch rei_robot_base base.launch
```

Keep the chassis program running and open a new terminal (Ctrl+Alt+t) to enter the following command to enable the controller control function:

```bash
roslaunch robot_joy robot_joy.launch
```

Long-press the MODE button to switch the controller mode.

Set the joystick mode to red light (MODE LED) to indicate that the controller is in control mode.

During operation, the user needs to press both the left and right joysticks simultaneously to switch the control mode of the controller between "wakeup" mode and "sleep" mode.

![Official manual image, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYeIZbYdZxy3QbTN9asAZ%2Fe6-ros-p022-img02.jpg?alt=media)

![Official manual image, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FgwfvqJxpzDY7pSAZTHrU%2Fe6-ros-p022-img03.jpg?alt=media)

![Official manual image, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FVtyEq49bRohYs7znTeOB%2Fe6-ros-p022-img04.jpg?alt=media)

![Official manual image, source page 22](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FAqbolGt9HsQHLCQ3lMRg%2Fe6-ros-p022-img05.jpg?alt=media)

After waking up the controller, press the emergency stop button, and then you can control the movement of bobac3 robot through the joystick of the controller.

### 4.2 Map construction and navigation

#### 4.2.1 Start the slam node

The default SLAM algorithm is GMapping algorithm. You can change the SLAM algorithm to cartographer algorithm by setting the "slam\_methods" parameter of bobac3\_slam.launch file

Open a new terminal and enter:

_Default GMapping algorithm_

```bash
roslaunch bobac3_slam bobac3_slam.launch
```

Or temporarily modified to Cartographer algorithm

_Cartographer algorithm_

```bash
roslaunch bobac3_slam bobac3_slam.launch slam_methods:=cartographer
```

You can see that the display will open rviz. Remember the current position of bobac3 robot when it opens slam. When robot uses the map constructed this time for navigation, this position is the starting point of the robot navigation without any other changes.

The controller can control the robot to move in a map environment and build a complete two-dimensional map.

![Official manual image, source page 23](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtxSdbwXDUvNupJ1fMZBL%2Fe6-ros-p023-img02.png?alt=media)

**NOTICE** Permanent modification of the default algorithm: Modify the _default_ of the slam\_methods parameter in file bobac3\_ws/src/bobac3\_slam/launch /bobac3\_slam.launch.

#### 4.2.2 Save the map

Once the map is built, you need to save the map for navigation.

Keep the slam program running (do not close it), open a new terminal (Ctrl+Alt+t), and enter the following commands in sequence to save the map (map\_file specifies the map file name, default is "map"):

_The default format of the map created by the gmapping algorithm_

```bash
roslaunch map_manager map_save.launch map_file:=test
```

_When using cartographer algorithm to build a map, you need to change the cartographer parameter to save the map_

```bash
roslaunch map_manager map_save.launch map_file:=test map_type:=cartographer
```

When the interface shows the prompt Done, it means that the map is created and all open terminals can be closed.

![Official manual image, source page 24](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F9ul7roJ8Lc0USBtxQj2T%2Fe6-ros-p024-img02.png?alt=media)

**NOTICE** You can also directly modify the default values of the "map\_type" and "map\_file" parameters in the "~~/bobac3\_ws/src/map\_manager /launch/map\_save.launch" file to modify the default values of map saving. If you do not modify these two parameters, the map will be saved to the "~~/bobac3\_ws/src/map\_manager/maps" directory after running.

#### 4.2.3 Autonomous navigation

Autonomous navigation is actually the robot's autonomous path planning on the map we have, and then reaching the target point. In order to carry out navigation, it is necessary to load the map first. In the previous section, we have built and saved the map, so how to use the map created by ourselves?

The "map\_file\_name" parameter is the name of the saved map file.

The default positioning algorithm is AMCL algorithm. The positioning algorithm can be modified to cartographer algorithm by setting the "location\_method" parameter of bobac3\_nav\_2d.launch file.

First move the robot to the starting position (and starting point of navigation) where the map was built, and then enter the following instructions at the terminal:

_Use the amcl positioning algorithm_

```bash
roslaunch bobac3_navigation bobac3_nav_2d.launch map_file_name:=test
```

Or

_Use the cartographer positioning algorithm_

```bash
roslaunch bobac3_navigation bobac3_nav_2d.launch location_method:=cartographer map_file_name:=test
```

It will open up an rviz interface, where the robot model is displayed, and the map that was just saved;

**Figure 4.1 Autonomous mapping**

The "2D Nav Goal" button in the toolbar above is used to give a navigation goal for a given robot.

Click the "2D Nav Goal" button, then move the mouse to the white area on the map where the robot needs to reach. Hold down the right mouse button and drag to select the robot's orientation. Once you are satisfied, release the right mouse button. The robot will then follow the route planned by the path planner, as shown in Figure 4.3. Green represents the planned path, black objects on the map indicate obstacles, gray areas show the expanded layer of obstacles, and red arrows indicate the destination and the direction after reaching it. If the target point is on a black or gray area, the robot will not move, as it is considered an obstacle and cannot be reached.

**NOTICE** Similarly, you can change the default map by modifying the default value of the "map\_file" parameter in \~/bobac3\_ws/src/bobac3\_navigation/launch/bobac3\_nav\_2d.launch. If you don't modify it, the map named "home" will be loaded by default.

### 4.3 Secondary Positioning

Function: The robot will use the bottom camera to identify the AR marker on the charging dock. It acquires the marker's position and then controls the robot to move directly facing the AR marker, finally stopping at a precise position directly in front of it.

Turn on the robot's emergency stop. Place the charging dock within the field of view of the robot's bottom camera (confirm the location of the bottom camera) as shown in the figure below:

![Official manual image, source page 26](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F0hh9pz5ZLsTGIckyyyxB%2Fe6-ros-p026-img02.png?alt=media)

#### 4.3.1 Open related nodes

Open a **new robot terminal** and enter the following command to launch the chassis node:

```bash
roslaunch rei_robot_base base.launch
```

Open a **new robot terminal** and enter the following command to launch the bottom camera node:

```bash
roslaunch ar_pose ar_base.launch
```

Open another **new robot terminal** and enter the following command to launch the robot model:

```bash
roslaunch bobac3_description display.launch
```

Open another **new robot terminal** and enter the following command to run the relative movement node:

```bash
roslaunch relative_move relative_move.launch
```

Open another **new robot terminal** and enter the following command to start the AR marker recognition and tracking program:

```bash
rosservice call /track "ar_id: 0 goal_dist: 0.2"
```

"ar\_id: 0": 0 represents the ID number of the AR marker on the charging dock. goal\_dist: 0.2" specifies that the robot will stop at a distance of 200 mm in front of the charging dock.

### 4.4 Automatic recharge

Autonomous recharge is the process in which the robot returns to the charging dock to charge itself when the battery is low or the task is completed.

![Official manual image, source page 27](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FywbiMnICyTvdvymYM3n3%2Fe6-ros-p027-img02.png?alt=media)

It needs to be coordinated with autonomous navigation and QR code guidance.

#### 4.4.1 Place the charging dock

Place the charging dock in a position where the robot can navigate to, against the wall, and connect the charger.

#### 4.4.2 Obtain the navigation coordinates of charging dock

Refer to 4.2.3 to open the navigation function:

```bash
roslaunch bobac3_navigation bobac3_nav_2d.launch
```

Open the controller control node (refer to 5.1 for the control method of the controller):

```bash
roslaunch robot_joy robot_joy.launch
```

Control the robot to move so that the bottom camera is facing the QR code of the charging dock about 30\~40 cm in front. Another terminal is opened to query the current posture of the robot (/base\_footprint is the origin of the robot, /odom is the coordinate system of the robot odometer):

```bash
rosrun tf tf_echo /odom /base_footprint
```

#### 4.4.3 Run automatic recharge

Open the terminal and refer to 5.2.3 to open the navigation function:

```bash
roslaunch bobac3_navigation bobac3_nav_2d.launch
```

Open another **new robot terminal** and enter the following command to run the AR marker recognition:

```bash
roslaunch ar_pose ar_base.launch
```

Open another **new robot terminal** and enter the following command to execute the relative movement node:

```bash
roslaunch relative_move relative_move.launch
```

Open a **new robot terminal** and enter the following instructions to run autonomous recharge:

```bash
roslaunch auto_charging auto_charging.launch
```

After all nodes run successfully, open a new terminal and enter the following instructions to set the parameters corresponding to the charging service and start charging (it is recommended to use TAB to complete the content and modify the parameters):

* When the nav parameter is set to true, navigate to the target point position.

Pose represents the target point for navigation.

* track\_id: The ID of the AR marker on the charging dock (default is marker 0).

 track\_dist: The distance between the robot's center and the charging dock. Issue V1.0 (2025-11-21) User Guide Copyright © SHENZHEN DOBOT CORP LTD

* docking\_dist: The additional distance to move towards the dock after reaching the specified track\_dist.

At this point, the robot will navigate itself to the charging dock and recharge.

### 4.5 Face detection and recognition

#### 4.5.1 Add new faces

Enter the /home/bobac3/.reinovo/face\_data directory and create a new directory (named after the face that recognizes it), and put the corresponding face data (take a picture of a face without anyone else in it) into the newly created directory.

#### 4.5.2 Subscribe to topics to get results in real time

Open the terminal to run

```bash
roslaunch face_rec face_rec_topic.launch
```

Open a new terminal and subscribe to the topic /camera/face\_recognition:

rqt\_image\_view

![Official manual image, source page 29](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FX0WOaW4vW5WPA2xy4bco%2Fe6-ros-p029-img03.png?alt=media)

#### 4.5.3 Call the service to obtain the result

Open the terminal to run

```bash
roslaunch face_rec face_rec_service.launch
```

Open another terminal and send a service request. When mode is 1, the current camera picture is identified:

```bash
rosservice call /face_recognition_results <Use TAB to complete>
```

Open another terminal and send a service request. When mode is 2, the specified image can be identified:

![Official manual image, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FteL0Rp47MyFTVsEHr6y7%2Fe6-ros-p030-img02.jpg?alt=media)

![Official manual image, source page 30](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5arw21ZJ9LhdohYZbtVW%2Fe6-ros-p030-img03.png?alt=media)

## 5. Bobac3 Hardware Detection

### 5.1 Controller

#### 5.1.1 Wake up the controller

Insert the receiver end of the controller into the USB port of the robot. If the controller is in sleep state (the two lights on the top of the controller are all off), click the mode key or the round button of the start key on the front of the controller to activate it. The default activation state is the green light is on.

#### 5.1.2 Check the device input

Enter the following command at the terminal:

```bash
ls /dev/input
```

As shown in Figure 3.1 below, the device input list contains devices with the word js, indicating that the system recognizes the controller.

**Figure 5.1 List of input devices**

A js serial number corresponds to only one controller device. When multiple controller devices are connected, the system will number them according to the power-up order of the USB port when starting up.

#### 5.1.3 Corresponding number of test controller

If multiple js are found, jstest can be used to determine the js serial number corresponding to the controller.

Enter the following command at the terminal:

```bash
sudo jstest /dev/input/js0
```

Turn the joystick of the controller. If there is data on the terminal, it indicates that this controller corresponds to the corresponding serial number. If there is no response, continue to test the next js number. After determining the corresponding js number, write it down for later use.

**Figure 5.2 Correct sample of controller test**

Use the roscd command on the terminal to enter robot\_joy/launch:

Roscd robot\_joy/launch

|Modify robot\_joy.launch:|||

||25||

![Official manual image, source page 31](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtKhFkQ5aPS8cYkuTDya8%2Fe6-ros-p031-img03.png?alt=media)

**Figure 5.3 bobac3\_joy.launch**

Find the parameter "dev" and fill in the previously determined js number.

If you only have one controller, this step only needs to be operated once, confirm the js number, under normal circumstances, there is no need to operate again.

#### 5.1.4 Control nodes with the controller

Enter the following command at the terminal:

```bash
roslaunch robot_joy robot_joy.launch
```

This function subscribes to the key button information of the controller: /joy, and the message type is sensor\_msgs/Joy. Publishes the speed message: /cmd\_vel, and the topic type is geometry\_msgs/Twist.

**Figure 5.4 Controller node communication diagram**

The specific message members are shown in Figure 5.5 and Figure 5.6.

**Figure 5.5 geometry\_msgs/Twist information**

**Figure 5.6 sensor\_msgs/Joy information**

Control mode: The left joystick of the controller controls the speed command of moving forward, backward, left and right, and the right joystick controls the speed command of

![Official manual image, source page 32](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FbjLCqiNr460YptWmcnzc%2Fe6-ros-p032-img02.png?alt=media)

turning left and right. The above is the observation node. For the specific steps of controlling the controller to control the car, please see 4.1.

### 5.2 Detection of chassis sensors and wheels

#### 5.2.1 Robot chassis node start

To get the sensor data, you need to start the robot's chassis node.

Open the terminal (Ctrl+Alt+t) and enter the following command:

```bash
roslaunch rei_robot_base bobac3_base.launch
```

#### 5.2.2 View sensor information

After the operation is successful, a topic named /car\_data will be sent out. By monitoring this topic, you can obtain real-time data of each motor speed and sensor. Keep the program of bobac3\_base running, open a new terminal (Ctrl+Alt+t), and enter the following instructions:

```bash
rostopic echo /car_data
```

As shown in Figure 5.7:

**Figure 5.7 car\_data data**

Look down from above:

* Motor\_speed is the speed of the three motors. When you press the emergency stop and push the robot by hand, you will see the corresponding data change.
* Ultrasound: two ultrasonic sensor messages.
* Smoke: Smoke sensor, which has two state values, 0 and 1. In a normal environment, it is displayed as 1. When the smoke sensor detects combustible gas, the state value is 0.
* Power voltage: Check the battery voltage message, you can see the current voltage of the battery here. When the voltage is less than 21V, it needs to be charged immediately.
* Is\_charge: Detect whether it is charging, only for detecting whether it is charging from the bottom.

![Official manual image, source page 33](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F19189zHrabrbIjCkDvY3%2Fe6-ros-p033-img02.png?alt=media)

* Temperature is a measure of the current temperature of the environment.
* Humidity is the detection of the current humidity in the environment.
* input\_io: Input IO information
* output\_io: Output IO information
* relay\_status: Relay status

#### 5.2.3 Robot bottom wheel detection

After launching the robot base node and opening the sensor data monitoring terminal, press the emergency stop button. Then, manually rotate the wheels on the base. You can observe the motor\_speed values (which represent the rotational speeds of the three motors) on terminal information in the View sensor information. If the data changes, it indicates that the wheels are functioning normally.

### 5.3 Turn on the LiDAR

#### 5.3.1 Check whether the LiDAR is recognized

Enter the command at the terminal:

```bash
ls /dev/*lidar
```

/dev/output /dev/front\_lidar indicates that the front lidar is detected, and /dev/rear\_lidar indicates that the rear LiDAR is detected.

#### 5.3.2 Start the LiDAR node

Enter the following command at the terminal to enable the LiDAR node:

```bash
roslaunch rei_ydlidar_nodelet nodelet_2_lidar.launch
```

If there is no error, the startup is successful.

#### 5.3.3 Display LiDAR data in rviz

Keep the lidar in step 5.3.2 Start the LiDAR node running.

Open a terminal and enter the following command to open the 3d model of the robot:

```bash
roslaunch bobac3_description display.launch
```

At this point, the robot's 3D model will be displayed. By adding the LiDAR data in RViz using "add", the laser scan information will become visible around the model.

![Official manual image, source page 34](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYAtUgm2bo8zPLWuDI8Yf%2Fe6-ros-p034-img02.png?alt=media)

### 5.4 Depth camera image view

The terminal runs the following command:

```bash
roslaunch berxel_camera berxel_base_camera.launch
```

After the operation is successful, keep the program running and open a new terminal to enter the following instructions to open rviz to view the image:

rviz

Follow these steps to see the image:

**Figure 5.8 Modify fixed\_frame**

**Figure 5.9 Add and display the depth image**

![Official manual image, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FtDWytjn6tvUnzUCn1TiU%2Fe6-ros-p035-img02.jpg?alt=media)

![Official manual image, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNnT15rSyvV8ATz1fZNuW%2Fe6-ros-p035-img03.jpg?alt=media)

![Official manual image, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FV08WcJnQNDgbG0jHsM4H%2Fe6-ros-p035-img04.jpg?alt=media)

![Official manual image, source page 35](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FNnYMVWJusjCYVSr3yYcU%2Fe6-ros-p035-img05.jpg?alt=media)

**Figure 5.10 Point cloud display**

### 5.5 USB camera image viewing

The robot is equipped with two USB cameras, one at the bottom and one at the head. The bottom camera is used for landmark recognition, and the head camera is used for face recognition and interaction.

#### 5.5.1 Open and view the bottom camera

Open a terminal and enter the following command to open the camera:

```bash
roslaunch ar_pose usbcam_base.launch
```

Open another terminal and enter the following command:

#### $ rqt\_image\_view

As shown in the figure below, select the topic name to be displayed as: /usb\_cam/image\_raw.

![Official manual image, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F5oolTXdg00MsFTlt9YBe%2Fe6-ros-p036-img02.png?alt=media)

![Official manual image, source page 36](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F3T2FIlvhPD0QfcOa9xJx%2Fe6-ros-p036-img03.png?alt=media)

#### 5.5.2 Turn on and view the head camera

Open a terminal and enter the following command to open the camera:

_### $_

```bash
roslaunch ar_pose usbcam_head.launch
```

Open another terminal and enter the following command:

#### $ rqt\_image\_view

As shown in the figure below, select the topic name to be displayed as: /usb\_cam/image\_raw.

### 5.6 Turn on the simulated disinfection lamp

The disinfection lamp of the disinfection robot is controlled by the robot expansion IO1.

Open a terminal and enter the following command to open the chassis:

_### $_

```bash
roslaunch rei_robot_base bobac3_base.launch
```

Open a terminal again and enter the following command to call the service to turn on the light:

bobac3@reinovo:\~$ rosservice call /set\_io "{all\_off: false, all\_on: false, io: \[1, 0, 0, 0, 0, 0, 0], state: true}"

To turn off the service light, open a terminal and enter the following command: bobac3@reinovo:\~$ rosservice call /set\_io "{all\_off: false, all\_on: false, io: \[1, 0, 0, 0, 0, 0, 0], state: false}"

### 5.7 Turn on and off the atomizing sterilizer

The sterilizer is controlled by a robot extension relay.

Open a terminal and enter the following command to open the chassis:

```bash
roslaunch rei_robot_base bobac3_base.launch
```

Open a terminal again and enter the following instructions to call the service to open the relay and open the sterilizer

```bash
rosservice call /set_relay "data: true"
```

Open the terminal and enter a command to turn off the sterilizer

```bash
rosservice call /set_relay "data: false"
```

![Official manual image, source page 37](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FsnzSxQoLyuY2KJhQ35qd%2Fe6-ros-p037-img02.png?alt=media)

## 6. Comprehensive Application

The previous foundational modules have introduced the core functionalities of the bobac3 robot. Through hands-on experimentation, you should now be familiar with the operation and principles of its various sensors. This chapter builds upon that knowledge, guiding you to integrate these hardware components within the ROS framework to develop complex algorithms for multi-task applications.

This chapter combines autonomous navigation, chassis control, and voice recognition to create a comprehensive voice-interaction application for the robot.

### 6.1 Voice integration application

#### 6.1.1 Voice command control of the robot

Previous experiments have demonstrated the voice chat functionality, which primarily utilized the voice module alone. The voice module can now be integrated with other systems to enable comprehensive applications.

The following experiment will involve controlling the bobac3 robot's movement through voice commands. Examples include: "move forward", "move backward", "turn left" and "turn right".

Ensure the robot is connected to the network, then open a terminal and enter the following command to launch the bobac3 voice chat system:

```bash
roslaunch robot_audio voice_interaction.launch
```

Keep this program running, open a new terminal (Ctrl+Alt+T), and enter the following command to launch the robot's base node:

```bash
roslaunch rei_robot_base base.launch
```

Open the robot relative motion node:

```bash
roslaunch relative_move relative_move.launch
```

After all systems are launched, release the emergency stop button and use the following voice command to switch the bobac3 robot into control mode.

User: "Yuanbao, Yuanbao" Bobac3 Robot: "Yes, what can I do?" User: "Please move forward 0.1 meters." Bobac3 Robot: "Okay, moving forward 0.1 meters." User: "Yuanbao, Yuanbao" Bobac3 Robot: "Yes, what is it?" User: "Please move left 0.1 meters." Bobac3 Robot: "Okay, moving forward 0.5 meters."

No problem if it misrecognizes. Just wake it up again and re-interact. If it prompts "Say it again", no wake-up is needed.

Recognizable directional commands: forward, backward, turn left, turn right, move left, move right.

Recognizable distance units: meter, decimeter, centimeter, radian, degree.

#### 6.1.2 Intelligent voice navigation

Similar to the voice control functionality described above, this voice navigation feature replaces the manual mouse operation for setting the robot's navigation target points. However, prior to this, we need to assign specific location names to corresponding coordinate points on the map.

1. First, follow the steps in Section 4.2 to construct and load the map. This step can be skipped if already completed during previous operations.
2. Next, define location names for specific positions on the map according to your requirements. For example, identify and label points such as the doorway, office, dining area, etc. Afterwards, we need to capture the precise coordinate data for these labeled points.

Move the robot to the intended navigation starting point, then open a terminal and enter the following command to launch the navigation function:

_###_

```bash
roslaunch bobac3_navigation bobac3_nav_2d.launch
```

Press the E-stop button to immobilize the robot. While keeping the current program running, open a new terminal (Ctrl+Alt+T) and enter the following command to monitor the /move\_base\_simple/goal topic:

```bash
rostopic echo /move_base_simple/goal
```

Return to the rviz interface and use the2d\_nav\_goal tool to mark the target pose for your desired location name. The corresponding coordinate information will then be visible in the second terminal we opened earlier. For example: to designate point A on the map as the "kitchen", use the 2d\_nav\_goal tool to set the target pose for the robot at that point. This means when the robot reaches this target position, it will be considered to have arrived at the kitchen. Record the corresponding coordinates (x, y) and quaternion values (z, w) as shown in Figure 5.3.

**Figure 6.1 Acquiring coordinate data**

Navigate to the home directory and use Ctrl+H to display hidden files. Open the configuration file position\_info.txt located at /home/bobac3/.ros/AIUI/dist. Configure the **waypoint names** according to the format shown in the image below, and modify the waypoint coordinates in the configuration file by entering the values in the order of x, y, z, w. The description for each location is added afterward.

![Official manual image, source page 39](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FHykbfgWk9ZEYarrGGLQc%2Fe6-ros-p039-img02.png?alt=media)

After configuring the first waypoint, use the 2d\_nav\_goal tool again to mark the next location. Repeat this process until all required locations are configured. Save and close the position\_info.txt file, then terminate all previously running programs.

3. Configuring voice recognition points

To ensure the robot understands our navigation intent upon hearing the predefined location names, we need to upload these names to the voice server. Navigate to the path /home/bobac3/.ros/AIUI/dist, open the pos\_name.txt file, and list all navigation point names in the specified format.

4. Compiling the workspace

The following step is to compile the workspace so that the changes made in position\_info.txt and pos\_name.txt can take effect. In the terminal, enter the following commands sequentially:

`cd ~/bobac3_ws` followed by `catkin_make`

5. Program execution

After the compilation is complete, move the robot to the navigation starting point. Then, open a terminal and enter the following command to launch the program:

```bash
roslaunch bobac3_navigation bobac3_nav_2d.launch
```

Then, in another terminal, enter the following command:

```bash
roslaunch robot_audio voice_interaction.launch
```

① Use the voice\_up\_sync service to upload the voice recognition point to the server. rosservice call /voice\_up\_sync

* ② Voice navigation

![Official manual image, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F795aUvK83JAVaZWhpwiG%2Fe6-ros-p040-img02.png?alt=media)

![Official manual image, source page 40](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F4vKRLRKr6aNYAE5tXPNx%2Fe6-ros-p040-img03.png?alt=media)

After activation, wake up the robot and say to the bobac3 robot: "Take me to..." (or "Navigate to..."). The destination must be a waypoint defined in the position\_info.txt configuration file; otherwise, it will not be recognized.

For example, if you say to the bobac3 robot: "Take me to the balcony", the robot will move to the target point and then play the voice description corresponding to that waypoint.

## 7. Robot ROS Development API

### 7.1 rei\_robot\_base

Function: Communicates with the lower-level controller to read motor speed, ultrasonic sensor data, temperature and humidity, smoke, and I/O status. Controls motor operation, digital I/O, and relays.

Node name: robot\_base\_node

#### 7.1.1 File structure

| **File name**                | **Function**                            |
| ---------------------------- | --------------------------------------- |
| kinematics.h                 | Kinematics solver header file           |
| rei\_print.h                 | Information printing header file        |
| rei\_robot\_base.h           | Base communication header file          |
| bobac3\_base.launch          | Launch file                             |
| librei\_robot\_base.so       | Base communication encapsulated library |
| librei\_robot\_kinematics.so | Kinematics solver encapsulated library  |

![Official manual image, source page 42](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2F28TQoYPFH7pIXqDR3hgr%2Fe6-ros-p042-img02.png?alt=media)

| **File name**   | **Function**                               |
| --------------- | ------------------------------------------ |
| BumperCliff.msg | Bumper/cliff sensor custom message         |
| CarData.msg     | Lower-level controller data custom message |
| MotorCmd.msg    | Motor speed control custom message         |
| base\_node.cpp  | ROS node                                   |
| Int8.srv        | Buzzer control custom service file         |
| SetIO.srv       | Output I/O control custom service file     |

#### 7.1.2 ROS API

#### Published TF

(\~robot\_base\_frame\_id)<——(\~odom\_frame\_id) (Published when publish\_odom\_tf is set to true)

#### Subscribed topic

|**Topic name (message type)**\
cmd\_vel(geometry\_msgs/Twist)|**Function**\
Velocity control|**Parameter description**\
http://docs.ros.org/en/melodic/ap\
i/geometry\_msgs/html/msg/Twist\
.html|

|motor\_cmd(rei\_robot\_base/Mot\
orCmd)|Motor speed control|std\_msgs/Header header:\
Message header\
float64\[] motor\_expect\_speed:\
Target speed for each motor|

#### Published Topic

|**Topic name**\
**(message type)**|**Function**|**Parameter description**|

|car\_data(\
rei\_robot\_base/\
CarData)|Lower-level controller data|std\_msgs/Header header: Message header\
float64\[] motor\_speed: Current speed of each\
motor (r/min)\
int8\[] crash: Values from each collision sensor\
int8\[] cliff: Values from each cliff sensor\
float32\[] ultrasound: Data from each ultrasonic\
sensor\
int8 smoke: Smoke sensor value\
float32 power\_voltage: Battery voltage (V)\
bool is\_charge: Charging status\
float32 temperature: Temperature value (°C)\
float32 relative\_humidity: Relative humidity\
value (RH)\
int8\[4] input\_io: Status of each input IO\
int8\[7] output\_io: Status of each output IO\
bool relay\_status: Relay status| |odom(\
nav\_msgs/Odo\
metry)|Wheel odometry data\
(published when\
publish\_odom is set to\
true)|http://docs.ros.org/en/melodic/api/nav\_msgs/\
html/msg/Odometry.html|

#### Services

|**Topic name (message**\
**type)**|**Function**|**Parameter description**|

|pub\_odom(std\_srvs/SetBo\
ol)|Control whether to\
publish the odometry\
topic|http://docs.ros.org/en/api/std\_srvs/h\
tml/srv/SetBool.html\
data=true: Enable publishing/ON\
data=false: Disable publishing/OFF| |pub\_odom\_tf(std\_srvs/Set\
Bool)|Control whether to\
publish the odometry tf|<sup>/</sup>| |set\_relay(std\_srvs/SetBool\
)|Control relay switching|| |set\_io(rei\_robot\_base/SetI\
O)|Control output IO|bool all\_off: When true, all IO\
outputs 0 (effective only when all\_on\
is false)\
bool all\_on: When true, all IO\
outputs 1 (effective only when all\_off\
is false)\
int8\[] io: Effective only when both\
all\_on and all\_off are false. Select\
the IO port number(s) to change\
(one or multiple; there are only 7\
output IOs, numbering starts from 1)\
bool state: The state to set for the IO\
ports listed in int8\[] io\
\---\
bool\
success:\
Returns\
true\
if\
successful\
string message| |clear\_odom(std\_srv/Empty\
)|Reset wheel odometry\
data|http://docs.ros.org/en/api/std\_srvs/h\
tml/srv/Empty.html| |set\_buzzer(rei\_robot\_base|<sup>Control the buzzer</sup>|int8 data: Buzzer sounds when|

| <p><strong>Topic name (message</strong><br><strong>type)</strong></p> | **Function**                                                                  | **Parameter desc**                                                                    | **ription** |
| --------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- | ----------- |
| /Int8)                                                                |                                                                               | <p>value > 0<br>---<br>bool success<br>string message</p>                             |             |
| <p>set_extra_motor(rei_robot_<br>base/Int8)</p>                       | <p>Control the additional<br>expansion motor (valid<br>for oryxBot robot)</p> | <p>int8<br>data:<br>0=Stop,<br>2=Reverse<br>---<br>bool success<br>string message</p> | 1=Forward,  |

#### Configuration parameters

| **Parameter name**  | **Description**                                                                                                         |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| robot\_model        | string. Robot model. Options: bobac2, bobac3, oryxbot, fox                                                              |
| port                | string. Communication serial port                                                                                       |
| baud                | int. Default 115200. Baud rate                                                                                          |
| data\_bit           | int. Default 8. Data bits                                                                                               |
| stop\_bit           | int. Default 1. Stop bits                                                                                               |
| slave               | int. Default 1. Slave address                                                                                           |
| range\_1\_frame\_id | <p>string. Default ultrasound1_link. Frame ID for ultrasonic sensor 1.<br>Valid when robot_model is a bobac series.</p> |
| range\_2\_frame\_id | <p>string. Default ultrasound2_link. Frame ID for ultrasonic sensor 2.<br>Valid when robot_model is a bobac series.</p> |

| **Parameter name**     | **Description**                                                                                                                                                                           |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BC\_1\_frame\_id       | <p>string. Default bumper_cliff1_link. Frame ID for bumper-cliff sensor<br>1. Valid when robot_model is bobac2.</p>                                                                       |
| BC\_2\_frame\_id       | <p>tring. Default bumper_cliff2_link. Frame ID for bumper-cliff sensor<br>2. Valid when robot_model is bobac2.</p>                                                                        |
| BC\_3\_frame\_id       | <p>string. Default bumper_cliff3_link. Frame ID for bumper-cliff sensor<br>3. Valid when robot_model is bobac2.</p>                                                                       |
| odom\_frame\_id        | string. Default odom. Frame ID for the odometry coordinate frame.                                                                                                                         |
| robot\_base\_frame\_id | <p><sup>string. Default base_footprint. Frame ID for the robot base</sup><br>coordinate frame.</p>                                                                                        |
| publis\_odom           | bool. Default false. Whether to publish the odometry topic.                                                                                                                               |
| publis\_odom\_tf       | bool. Default false. Whether to publish the odometry tf.                                                                                                                                  |
| kinematics\_mode       | <p>int. Chassis kinematic model. 2: Two-wheel differential, 3: Three-<br>wheel omni-directional, 5: Four-wheel Mecanum wheel omni-<br>directional.</p>                                    |
| wheel\_radius          | double. Wheel radius. Unit: m.                                                                                                                                                            |
| wheel\_separation\_x   | <p>double. Not used when kinematics_mode is 2. Represents wheel<br>separation when kinematics_mode is 3, and wheel separation in the<br>x-direction when kinematics_mode is 5.</p>        |
| wheel\_separation\_y   | <p>double. Represents wheel separation when kinematics_mode is 2.<br>Not used when kinematics_mode is 3. Represents wheel separation<br>in the y-direction when kinematics_mode is 5.</p> |
| max\_vx                | <p>double. Maximum allowed linear velocity in the x-direction. Unit:<br>m/s. It is recommended not to exceed 0.4 m/s.</p>                                                                 |
| max\_vy                | <p>double. Maximum allowed linear velocity in the y-direction. Unit:<br>m/s. It is recommended not to exceed 0.4 m/s.</p>                                                                 |

|**Parameter name**|**D**|**escription**|

|max\_vth|double. Maximum allowed\
recommended not to exceed|angular velocity. Unit: rad/s. It is\
0.8 rad/s.|

#### Others

For definitions and functionalities of the classes BaseKinematics and RobotBaseCom used in this package, please refer to their corresponding header files:

BaseKinematics——kinematics.h

RobotBaseCom——rei\_robot\_base.h

The source code files can be viewed or downloaded from the master branch at:

https://gitee.com/reinovo/rei\_robot\_base.git

#### 7.1.3 Operating requirements

To successfully run the programs in this package, the following conditions must be met: stable communication with the lower-level controller and normal power operation.

#### 7.1.4 Chassis communication protocol

The chassis communication utilizes the Modbus protocol for data exchange.

#### Scope

This communication protocol applies to data exchange between the drive control board and the industrial computer, specifying their physical connection, communication link, and application technical specifications.

#### Referenced standards

Modbus-RTU protocol

#### Overview

* Byte format

Asynchronous serial communication. Each byte consists of 8 data bits, no parity bit, 1 stop bit(1). Asynchronous communication at 115200 bps. The drive control board address is 01.

* Frame format

Adhere to the standard Modbus-RTU protocol. A typical frame format is as follows:

#### 1. Master sends query command

| **Start gap**                                   | <p><strong>Device</strong><br><strong>address</strong></p> | <p><strong>Function</strong><br><strong>code</strong></p> | <p><strong>Start</strong><br><strong>register</strong><br><strong>address</strong></p> | <p><strong>Number of</strong><br><strong>registers</strong></p> | <p><br><strong>CRC</strong><br><strong>Checksum</strong></p> | **End gap**                                         |
| ----------------------------------------------- | ---------------------------------------------------------- | --------------------------------------------------------- | -------------------------------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------ | --------------------------------------------------- |
| <p>longer than<br>3.5<br>character<br>times</p> | 1 byte                                                     | 1 byte                                                    | <p>2 bytes,<br>high byte<br>first</p>                                                  | <p>2 bytes,<br>high byte<br>first</p>                           | <p>2 bytes, high<br>byte first</p>                           | <p><br>longer than<br>3.5<br>character<br>times</p> |

#### Slave response

| **Start gap**                    | <p><strong>Device</strong><br><strong>address</strong></p> | <p><strong>Function</strong><br><strong>code</strong></p> | <p><strong>Start</strong><br><strong>register</strong><br><strong>address</strong></p> | **Data**          | <p><strong>CRC</strong><br><strong>Checksum</strong></p> | **End gap**                          |
| -------------------------------- | ---------------------------------------------------------- | --------------------------------------------------------- | -------------------------------------------------------------------------------------- | ----------------- | -------------------------------------------------------- | ------------------------------------ |
| longer than                      |                                                            |                                                           |                                                                                        |                   |                                                          | longer than                          |
| <p>3.5<br>character<br>times</p> | 1 byte                                                     | 1 byte                                                    | <p>2 bytes, high<br>byte first</p>                                                     | <p><br>N byte</p> | <p>2 bytes, high<br>byte first</p>                       | <p><br>3.5<br>character<br>times</p> |

**Example** : The master reads HoldDataReg\[1]. The operation is as follows:

01 03 00 01 00 01 D5 CA

Slave Address | Function Code | Data Address | Number of Registers | CRC Checksum

Upon receiving this data stream, the drive control board calculates a CRC checksum to verify its integrity. If the data is validated, it sends a formatted response back to the master.

Response:

01 03 02 0017 F8 4A

Slave Address | Function Code | Byte Count | Data (2 bytes) | CRC Checksum

#### 2. Master writes to slave (Single register write)

| **Start gap**                    | <p><strong>Device</strong><br><strong>address</strong></p> | <p><strong>Function</strong><br><strong>code</strong></p> | <p><br><strong>Start</strong><br><strong>register</strong><br><strong>address</strong></p> | **Data**          | <p><strong>CRC</strong><br><strong>Checksum</strong></p> | **End gap**                          |
| -------------------------------- | ---------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ----------------- | -------------------------------------------------------- | ------------------------------------ |
| longer than                      |                                                            |                                                           |                                                                                            |                   |                                                          | longer than                          |
| <p>3.5<br>character<br>times</p> | 1 byte                                                     | 1 byte                                                    | <p>2 bytes, high<br>byte first</p>                                                         | <p><br>N byte</p> | <p>2 bytes, high<br>byte first</p>                       | <p><br>3.5<br>character<br>times</p> |

**Example:**

01 06 00 01 00 17 98 04

Slave Address | Function Code | Data Address | Data | CRC Checksum

If the local address is 01, the microcontroller receives this data stream, calculates the CRC checksum to verify its integrity. If the data is validated, the result is: HoldDataReg\[1] = 0x0017. This completes a write operation by the Modbus master to the slave, achieving successful communication.

**NOTE:** In Modbus, "coils" and "registers" essentially refer to "bit variables" and "16-bit variables" respectively. The term "coil" originates from the protocol's initial development by Schneider Electric for its PLCs, hence many terms are related to PLC terminology. **This communication specification uses only holding registers; coils are not enabled.** Additionally, regarding the Modbus verification method, the corresponding C language implementation is provided at the end of the document.

3. Application

#### Read Wheel Speed (for each wheel)

Function: Read the wheel speed command. Returns 4 double values. One double value (8 bytes) is formed by 4 registers (high byte first), corresponding to the speed of wheels 1-4. The unit is revolutions per minute (RPM).

Modbus function code: 04

Register starting address: 30001 (Input registers)

Data length: 16 (Registers)

Data type: double

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><br><strong>Function</strong><br><strong>Code</strong></p> | <p><br><strong>Register</strong><br><strong>address</strong><br><strong>high</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>low</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | **CRC high** | **CRC low** |
| ---------------------------------------------------------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------- | -------------------------------------------------------- | ------------ | ----------- |
| 1                                                          | 4                                                             | 30001                                                                                     |                                                                                      | 16                                                        |                                                          | /            |             |

Drive control board response:

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong><br></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><br><strong>Quantity</strong><br><strong>high</strong><br></p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | <p><br><strong>Motor</strong><br><strong>1</strong><br><strong>speed</strong></p> | <p><strong>Motor</strong><br><strong>2</strong><br><strong>speed</strong></p> | <p><strong>Motor</strong><br><strong>3</strong><br><strong>speed</strong></p> | <p><strong>Motor</strong><br><strong>4</strong><br><strong>speed</strong></p> | <p><strong>CRC</strong><br><strong>high</strong></p> | <p><strong>CRC</strong><br><strong>low</strong></p> |
| -------------------------------------------------------------- | --------------------------------------------------------- | ----------------------------------------------------------------- | -------------------------------------------------------- | --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------- | ---------------------------------------------------- | --------------------------------------------------- |
| <p>1<br></p>                                                   | 4                                                         | 16                                                                |                                                          | /                                                                                 | /                                                                             | /                                                                             | <p>/<br>/</p>                                                                 |                                                      |                                                     |

Data definition:

Wheel 1 Speed: Double-precision data, using 4 input registers, i.e., 8 bytes of data, high byte first, unit is rpm.

Wheel 2 Speed: Double-precision data, using 4 input registers, i.e., 8 bytes of data, high byte first, unit is rpm.

Wheel 3 Speed: Double-precision data, using 4 input registers, i.e., 8 bytes of data, high byte first, unit is rpm.

Wheel 4 Speed: Double-precision data, using 4 input registers, i.e., 8 bytes of data, high byte first, unit is rpm.

#### Read battery charging status

Function: Determine whether the robot is charging.

Modbus function code: 04

Register starting address: 30017 (Input register)

Data Length: 1

Data Type: 16-bit unsigned integer

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>high</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>low</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><br><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>CRC high</strong><br><strong>CRC low</strong></p> |
| ---------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1                                                          | 4                                                         | 30017                                                                                 |                                                                                      | 1                                                         |                                                              | /                                                            |

Drive control board response:

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>Charging</strong><br><strong>status</strong></p> | **CRC high** | **CRC low** |
| ---------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | -------------------------------------------------------- | ----------------------------------------------------------- | ------------ | ----------- |
| 1                                                          | 4                                                         | 1                                                         |                                                          | 0 or 1                                                      | /            |             |

Data definition:

Charging status: 16-bit unsigned integer, occupying 1 input register (i.e., 2 bytes of data), high byte first. It indicates whether the battery is currently charging, where 0 represents not charging and 1 represents charging.

#### Read power supply voltage

Function: Read the value of the power supply voltage.

Modbus function code: 04

Register starting address: 30018 (Input register)

Data length: 1

Data type: 16-bit unsigned integer

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><br><strong>Register</strong><br><strong>address</strong><br><strong>high</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>low</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><br><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>CRC high</strong><br><strong>CRC low</strong></p> |
| ---------------------------------------------------------- | --------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1                                                          | 4                                                         | 30018                                                                                     |                                                                                      | 1                                                         |                                                              | /                                                            |

Drive control board response:

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>Power</strong><br><strong>supply</strong><br><strong>voltage</strong></p> | **CRC high** | **CRC low** |
| ---------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------ | ----------- |
|                                                            |                                                           |                                                           |                                                          | **value**                                                                            |              |             |
| 1                                                          | 4                                                         | 1                                                         |                                                          | /                                                                                    | /            |             |

Data definition:

Power supply voltage value: 16-bit unsigned integer, occupying 1 input register (i.e., 2 bytes of data), high byte first. It corresponds to the current power supply voltage value, in units of mV.

#### Read IO Status

Function: Read the status of the extended input IO or the bumper-cliff sensors (when using the bobac2 robot).

Modbus function code: 04

Register starting address: 30019 (Input register)

Data length: 1

Data type: 16-bit unsigned integer

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong><br>1</p> | <p><strong>Function</strong><br><strong>Code</strong><br>4</p> | <p><br><strong>Quantity</strong><br><strong>high</strong><br>30019</p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong><br>1</p> | <p><br><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>CRC high</strong><br><strong>CRC low</strong><br>/</p> |
| --------------------------------------------------------------- | -------------------------------------------------------------- | ---------------------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------------- | ------------------------------------------------------------ | ----------------------------------------------------------------- |

Drive control board response:

Frame format:

||47||

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | **IO status** | **CRC high** | **CRC low** |
| ---------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | -------------------------------------------------------- | ------------- | ------------ | ----------- |
| 1                                                          | 4                                                         | 1                                                         |                                                          | /             | /            |             |

Data definition:

IO status: 16-bit unsigned integer, occupying 1 input register (i.e., 2 bytes of data), high byte first. The lower 4 bits represent the status of the four corresponding channel IOs. The bit status is 1 when the IO input is connected to GND, and 0 when the IO input is floating. The device input IOs are typically connected to sensors with NPN outputs or switch output sensors.

IO status: When the device is a bobac2 robot, the lower 6 bits (bits 0-5) correspond to the IO status of the following sensors, respectively: Cliff 2, Bumper 2, Cliff 3, Bumper 3, Cliff 1, Bumper 1.

#### Read ultrasonic sensor status

Function: Read the status of the ultrasonic sensors, returning 3 integers corresponding to the distance values (in mm) from ultrasonic sensors 1-3.

Modbus function code: 04

Register starting address: 30020

Data length: 3

Data type: 16-bit unsigned integer

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><br><strong>Quantity</strong><br><strong>high</strong></p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><br><strong>Quantity</strong><br><strong>low</strong></p> | <p><br><strong>CRC high</strong><br><strong>CRC low</strong></p> |
| ---------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------- | -------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------ | ---------------------------------------------------------------- |
| 1                                                          | 4                                                         | 30020                                                         |                                                          | 3                                                         |                                                              | /                                                                |

Drive control board response:

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong><br>1</p> | <p><strong>Function</strong><br><strong>Code</strong><br>4</p> | <p><strong>Quantity</strong><br><strong>high</strong><br>3</p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>Ultrasonic</strong><br><strong>1-3</strong><br>/<br></p> | <p><strong>CRC high</strong><br>/</p> | **CRC low** |
| --------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------------- | ------------------------------------- | ----------- |

Data definition:

Ultrasonic 1-3: Return the distance measured by the corresponding ultrasonic sensor, in millimeters (mm). The data type is a 16-bit unsigned integer. It should be read at 200ms intervals.

#### Read smoke sensor status

Function: Determine if the smoke sensor has been triggered.

Modbus function code: 04

Register starting address: 30023 (Input register)

Data length: 1

Data Type: 16-bit unsigned integer

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><br><strong>Quantity</strong><br><strong>high</strong></p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><br><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>CRC high</strong><br><strong>CRC low</strong></p> |
| ---------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------- | -------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1                                                          | 4                                                         | 30023                                                         |                                                          | 1                                                         |                                                              | /                                                            |

Drive control board response:

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>Smoke</strong><br><strong>status</strong></p> | **CRC high** | **CRC low** |
| ---------------------------------------------------------- | --------------------------------------------------------- | --------------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------- | ------------ | ----------- |
| 1                                                          | 4                                                         | 1                                                         |                                                          | 0 or 1                                                   | /            |             |

Data definition:

Smoke sensor status: 16-bit unsigned integer, occupying 1 input register (i.e., 2 bytes of data), high byte first. It indicates the current status of the smoke sensor, where 0 represents Normal and 1 represents Triggered.

#### Read temperature and humidity sensor status

Function: Read the data from the temperature and humidity sensor.

Modbus function code: 04 Register starting address: 30024 (Input register) Data length: 4 Data type: float

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><br><strong>Register</strong><br><strong>address</strong><br><strong>high</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>low</strong></p> | <p><strong>Quantity</strong><br><strong>high</strong></p> | <p><br><strong>Quantity</strong><br><strong>low</strong></p> | <p><strong>CRC high</strong><br><strong>CRC low</strong></p> |
| ---------------------------------------------------------- | --------------------------------------------------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | --------------------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1                                                          | 4                                                         | 30024                                                                                     |                                                                                      | 4                                                         |                                                              | /                                                            |

Drive control board response:

Frame format:

| <p><strong>Device</strong><br><strong>Address</strong></p> | <p><strong>Function</strong><br><strong>Code</strong></p> | <p><br><strong>Quantity</strong><br><strong>high</strong></p> | <p><strong>Quantity</strong><br><strong>low</strong></p> | <p><br><strong>Temperature</strong></p> | <p><br><strong>Humidity</strong></p> | <p><br><strong>CRC high</strong><br><strong>CRC low</strong></p> |
| ---------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------- | -------------------------------------------------------- | --------------------------------------- | ------------------------------------ | ---------------------------------------------------------------- |
| 1                                                          | 4                                                         | 4                                                             |                                                          | /                                       | /                                    | /                                                                |

Data definition:

Temperature status: Float data type, occupying 2 input registers (i.e., 4 bytes of data), high byte first. It corresponds to the current temperature value in degrees Celsius (°C).

Humidity status: Float data type, occupying 2 input registers (i.e., 4 bytes of data), high byte first. It corresponds to the current humidity value, expressed as a percentage of relative humidity. Relative humidity refers to the ratio of the partial pressure of water vapor in the air to the saturated vapor pressure of water at the same temperature.

#### Set Individual Wheel Speed

Function: Set the speed command for the wheels. Write 4 double-precision values, where each value is composed of 4 registers (8 bytes), with the high byte first. These values correspond to the rotational speed of wheels 1-4, in revolutions per minute (rpm).

Modbus function code: 16

Register starting address: 40001 (Holding register)

Data length: 16

Data type: double

Frame format:

Motor Motor Motor Motor\
Register Register CRC CRC\
Device Function Quantity Quantity\
address address 1 2 3 4\
address code high low high low high low\
speed speed speed speed\
1 16 40001 16<br>

Data definition:

Wheel 1 Speed: Double-precision data, occupying 4 input registers (i.e., 8 bytes of data), high byte first. Unit is rpm.

Wheel 2 Speed: Double-precision data, occupying 4 input registers (i.e., 8 bytes of data), high byte first. Unit is rpm.

Wheel 3 Speed: Double-precision data, occupying 4 h input registers (i.e., 8 bytes of data), high byte first. Unit is rpm.

Wheel 4 Speed: Double-precision data, occupying 4 input registers (i.e., 8 bytes of data), high byte first. Unit is rpm.

#### Set buzzer playback

Function: Play the buzzer by writing an unsigned integer corresponding to the delay time for the buzzer to sound.

Modbus function code: 06

Register starting address: 40017 (Holding register)

Data length: 1

Data type: 16-bit unsigned integer

Frame format:

| <p><strong>Device</strong><br><strong>address</strong></p> | <p><strong>Function</strong><br><strong>code</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>high</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>low</strong></p> | <p><strong>Playback</strong><br><strong>duration</strong></p> | **CRC high** | **CRC low** |
| ---------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------- | ------------ | ----------- |
| 1                                                          | 6                                                         | 40017                                                                                 |                                                                                      |                                                               |              |             |

Data definition:

Playback time: 16-bit unsigned integer, occupying 1 input register (i.e., 2 bytes of data), high byte first. This corresponds to the buzzer delay time, with a unit of 100ms.

#### Set drive control board relay output

Function: Configure the relay output of the drive control board.

Modbus function code: 06

Register starting address: 40018 (holding register)

Data length: 1

Data type: 16-bit unsigned integer

Frame format:

| <p><strong>Device</strong><br><strong>address</strong></p> | <p><strong>Function</strong><br><strong>code</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>high</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>low</strong></p> | <p><strong>Relay</strong><br><strong>status</strong></p> | **CRC high** | **CRC low** |
| ---------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------- | ------------ | ----------- |
| 1                                                          | 6                                                         | 40018                                                                                 |                                                                                      | 0 or 1                                                   |              |             |

Data definition:

Relay status: 16-bit unsigned integer accepting only input 0 or 1, 1 input register (2 bytes of data), high byte first, where 1 indicates relay closure.

#### Set IO output

Function: Configure extended IO output to control the output level of 7 extended IO channels and one relay output.

Modbus function code: 06

Register starting address: 40019 (holding register)

Data length: 1

Data type: 16-bit unsigned integer

Frame format:

| <p><strong>Device</strong><br><strong>address</strong></p> | <p><strong>Function</strong><br><strong>code</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>high</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>low</strong></p> | **IO status** | **CRC high** | **CRC low** |
| ---------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | ------------- | ------------ | ----------- |
| 1                                                          | 6                                                         | 40019                                                                                 |                                                                                      |               |              |             |

Data definition:

IO status: 16-bit unsigned integer, 1 input register (2 bytes of data), high byte first.

The lower 7 bits represent the output level of the extended IO, which is NPN commonground output.

#### Set extended motor output

Function: Set extended motor output to control the stop, forward rotation, and reverse rotation of the extended motor.

Modbus function code: 06

Starting register address: 40020 (holding register)

Data length: 1

Data type: 16-bit unsigned integer

Frame format:

| <p><strong>Device</strong><br><strong>address</strong></p> | <p><strong>Function</strong><br><strong>code</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>high</strong></p> | <p><strong>Register</strong><br><strong>address</strong><br><strong>low</strong></p> | <p><strong>Motor</strong><br><strong>status</strong></p> | **CRC high** | **CRC low** |
| ---------------------------------------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ | -------------------------------------------------------- | ------------ | ----------- |
| 1                                                          | 6                                                         | 40020                                                                                 |                                                                                      | 0-3                                                      |              |             |

Data definition:

Motor status: A 16-bit unsigned integer that only accepts the values 0, 1, or 3, occupying 1 holding register (i.e., 2 bytes of data), high byte first.

0: Motor stop; 1: Motor forward; 2: Motor reverse; Other values are invalid.

## Appendix:

The C language function for CRC calculation is as follows:

/\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\* ->Function name: CRCVerify() ->Function: Verifies the CRC of received and transmitted commands -> Input Parameters: Verify the pointer to data Number of bytes to verify

-> Return value: None

\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*/

WORDCRCVerify(BYTE\*pMsg,WORDusDataLen) { BYTEucCRCHi=0xFF; /_highbyteofCRCinitialized_/ BYTEucCRCLo=0xFF; /_lowbyteofCRCinitialized_/ WORDuIndex=0; /_willindexintoCRClookuptable_/ while(usDataLen--) /_passthroughmessagebuffer_/ { uIndex=ucCRCHi^\*pMsg++; /_calculatetheCRC_/ ucCRCHi=ucCRCLo^auchCRCHi\[uIndex]; ucCRCLo=auchCRCLo\[uIndex]; } return(ucCRCHi<<8|ucCRCLo);

}/\*The return value is the check value for the RTU message frame \*/ staticBYTEauchCRCHi\[]={

0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x41,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0x40 ,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0x40,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x4 1,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0x40,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x 41,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x41,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0 x40,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0x40,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80, 0x41,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x41,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81 ,0x40,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x41,0x01,0xC0,0x80,0x41,0x00,0xC1,0x8 1,0x40,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0x40,0x00,0xC1,0x81,0x40,0x01,0xC0,0x 80,0x41,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0x40,0x00,0xC1,0x81,0x40,0x01,0xC0,0 x80,0x41,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x41,0x01,0xC0,0x80,0x41,0x00,0xC1, 0x81,0x40,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x41,0x01,0xC0,0x80,0x41,0x00,0xC1 ,0x81,0x40,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0x40,0x00,0xC1,0x81,0x40,0x01,0xC 0,0x80,0x41,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x41,0x01,0xC0,0x80,0x41,0x00,0x C1,0x81,0x40,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0x40,0x00,0xC1,0x81,0x40,0x01,0 xC0,0x80,0x41,0x01,0xC0,0x80,0x41,0x00,0xC1,0x81,0x40,0x00,0xC1,0x81,0x40,0x01, 0xC0,0x80,0x41,0x00,0xC1,0x81,0x40,0x01,0xC0,0x80,0x41,0x01,0xC0,0x80,0x41,0x00 ,0xC1,0x81,0x40};

staticcharauchCRCLo\[]={

#### CRC calculation reference

The official PDF prints the CRC byte-array listing without dependable copyable spacing. Inspect the original listing below or in the linked PDF before using it in software.

![Official CRC reference listing, source page 60](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FYfoHUvjZKL0yxo5okIW1%2Fe6-ros-crc-code-1.png?alt=media)

![Official CRC reference listing, source page 61](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FTv2FXD9qzhd3S9Xx8uhA%2Fe6-ros-crc-code-2.png?alt=media)

### 7.2 robot\_joy

Function: Joystick speed control

Node name: robot\_joy\_node

#### 7.2.1 File structure

#### 7.2.2 ROS API

#### Subscribed Topic

|**Topic name**\
**(Message type)**|**Function**|**Parameter description**|

|joy(sensor\_msgs/Joy)|Joystick key values||

#### Published Topic

|**Topic name**\
**(Message type)**|**Function**|**Parameter description**|

|cmd\_vel(geometry\_ms\
gs/Twist)|Speed control|http://docs.ros.org/en/melodic/api/geomet\
ry\_msgs/html/msg/Twist.html|

#### Configuration parameters

| **Parameter name** | **Parameter description**                                                                           |
| ------------------ | --------------------------------------------------------------------------------------------------- |
| axis\_linear\_x    | <p>int type, default value 1, axis number for x-direction<br>control keys (forward/backward)</p>    |
| axis\_linear\_y    | <p>int type, default value 0, axis number for y-direction<br>control keys (left/right movement)</p> |
| axis\_angular      | <p>int type, default value 3, axis number for yaw angle<br>control keys (left/right turn)</p>       |

| axis\_accelerator              | int type, default value 5, axis number for acceleration key                                                                                          |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| axis\_deceleration             | int type, default value 2, axis number for deceleration key                                                                                          |
| button\_max\_linear\_increase  | <p>int type, default value 0, button for increasing maximum<br>linear velocity</p>                                                                   |
| button\_max\_angular\_increase | <p><sup>int type, default value 2, button for increasing maximum</sup><br>angular velocity</p>                                                       |
| button\_max\_linear\_reduce    | <p>int type, default value 1, button for decreasing maximum<br>linear velocity</p>                                                                   |
| button\_max\_angular\_reduce   | <p>int type, default value 3, button for decreasing minimum<br>angular velocity</p>                                                                  |
| linear\_vel\_max               | <p>double type, default value 0.8, maximum achievable<br>linear velocity (velocity will be limited to this value<br>regardless of acceleration)</p>  |
| angular\_vel\_max              | <p>double type, default value 3.0, maximum achievable<br>angular velocity (velocity will be limited to this value<br>regardless of acceleration)</p> |
| linear\_vel                    | <p>double type, default value 0.3, initial maximum linear<br>velocity</p>                                                                            |
| angular\_vel                   | <p>double type, default value 0.6, initial maximum angular<br>velocity</p>                                                                           |

#### 7.2.3 Operating requirements

To successfully run the programs in this package, you need to:

Insert the joystick receiver and turn on the joystick power.

### 7.3 relative\_move

Function: Chassis relative movement

Node name: relative\_move\_node

#### 7.3.1 File structure

#### 7.3.2 ROS API

#### Subscribed Topic

|**Topic name**\
**(message type)**|**Function**|**Parameter description**|

|scan(sensor\_msgs/La\
serScan)|2D LiDAR Data|http://docs.ros.org/en/melodic/api/sensor\_m\
sgs/html/msg/LaserScan.html|

#### Published Topic

|**Topic name**\
**(message type)**|**Function**|**Parameter description**|

|cmd\_vel(geometry\_m\
sgs/Twist)|Speed control|http://docs.ros.org/en/melodic/api/geometry\
\_msgs/html/msg/Twist.html|

#### Services

|**Service name**\
**(Service type)**|**Function**|**Parameter description**|

|relative\_move(relativ\
e\_move/SetRelative\
Move)|Robot relative\
movement|geometry\_msgs/Pose2D goal: The direction\
and distance for the movement.\
string global\_frame: The global reference\
frame (typically /odom, or set to /map when\
used with navigation).\
bool finishStopObstacle : Whether to directly\
end when stopping due to obstacles (generally|

|||occurs after obstacle avoidance is enabled)\
\---\
bool success\
string message|

|stop\_rel\_move|Stop relative\
movement|std\_sr vs/Empty|

#### Configuration parameters

|**Parameter name**|**Parameter description**|**Default value**|

|base\_frame|string type, robot base\
coordinate frame.|base\_footprint| |odom\_model\_type|string type, chassis motion\
model;\
Differential: diff\
Omnidirectional: omni|\
diff| |x\_p||0.5| |x\_i|double type, PID adjustment\
in the x-direction|\
0.0| |x\_d||0.2| |y\_p||0.5| |y\_i|double type, PID adjustment\
in the y-direction|\
0.0| |y\_d||0.2| |theta\_p|double type, rotational PID|1.0| |theta\_i|adjustment|0.0| |theta\_d||0.3|

#### 7.3.3 Operating conditions

To successfully run the programs in this package, the following is required:

Launch bobac3\_base.launch from rei\_robot\_base, with the parameter publish\_odom set to true.

### 7.4 ar\_track\_alvar

Function: AR marker recognition

#### 7.4.1 ROS API

Offical document: http://wiki.ros.org/ar\_track\_alvar

#### Configuration parameters

Two new configuration parameters have been added.

| **Parameter**   | **Parameter description**                                                                                   |
| --------------- | ----------------------------------------------------------------------------------------------------------- |
| special\_detect | <p>bool type, default value false. Determine whether to only<br>recognize AR marker with specified IDs.</p> |
| special\_id     | <p>int type, default value 0. AR marker ID. Effective only<br>when special_detect is true.</p>              |

### 7.5 ar\_pose

Function: AR marker tracking

Node name: pose\_adjust

#### 7.5.1 File structure

![Official manual image, source page 66](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FPc5GiIOjJgghX98MMlT5%2Fe6-ros-p066-img02.png?alt=media)

Among them,

base\_camera.yaml is the camera intrinsic parameter calibration file

usbcam\_base.launch is the launch file for visual positioning camera

ar\_base.launch is the master launch file for this function, which also publishes a world——>usb\_cam TF transformation.

#### 7.5.2 ROS API

#### Subscribed Topic

|**Topic name**\
**(message type)**|**Function**|**Parameter description**|

|ar\_pose\_marker(ar\_track\_\
alvar\_msgs/AlvarMarkers)|AR marker\
information|Header header: Message header\
AlvarMarker\[] markers：Information\
of all detected AR markers|

#### Published Topic

|                      | <p><strong>Topic name</strong><br><strong>(message type)</strong></p> | **Function**  | **Parameter description**                                                       |
| -------------------- | --------------------------------------------------------------------- | ------------- | ------------------------------------------------------------------------------- |
| <p>cmd_<br>wist)</p> | <p>vel(geometry_msgs/T<br></p>                                        | Speed control | <p>http://docs.ros.org/en/melodic/api/g<br>eometry_msgs/html/msg/Twist.html</p> |

#### Services

| <p><strong>Service name</strong><br><strong>(service type)</strong><br><strong>Function</strong><br>ar_track(bobac3_msgs/track) AR marker tracking</p> |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ |

| **Function**   | **Parameter description**                          |
| -------------- | -------------------------------------------------- |
|                | int8 ar\_id: AR ID being tracked.                  |
|                | <p>float32 goal_dist: The tracking<br>distance</p> |
| arker tracking | ---                                                |
|                | string message                                     |
|                | bool success                                       |

#### 7.5.3 Operating requirements

To run this package successfully, you must:

Install or compile the ar\_track\_alvar package

### 7.6 auto\_charging

Function: Auto charging

Node name: auto\_charge

#### 7.6.1 File structure

Among them,

The auto\_charging.launch file is the launch file for the automatic charging feature and it simultaneously initiates the ar\_base.launch.

#### 7.6.2 ROS API

#### Services

|**Service name (service type)**|**Function**|**Parameter description**|

|goto\_charge(auto\_charging/SetCharge)|<sup>Auto</sup>\
charging|bool nav: whether to navigate to\
the charging location\
bool ar\_track: whether the robot\
is aligned with the charging\
docker\
int8 ar\_id: The id of AR marker\
\---\
string message\
bool success|

![Official manual image, source page 68](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FrWKlNM551fZq1vFHq1FS%2Fe6-ros-p068-img02.png?alt=media)

#### Clients

|**Service name**\
**(service type)**|**Function**|**Parameter description**|

|ar\_track(ar\_pose/track)|AR marker\
tracking|int8 ar\_id: AR id being tracked\
float32 goal\_dist: The tracking\
distance\
\---\
string message\
bool success|

#### Actionlib Clients

move\_base: Autonomous navigation action

#### Configuration parameters

| **Parameter name** | **Parameter description**                           |
| ------------------ | --------------------------------------------------- |
| anchor\_x          | double type, default 0, charging point coordinate x |
| anchor\_y          | double type, default 0, charging point coordinate y |
| anchor\_theta      | double type, default 0, charging point yaw angle    |

#### 7.6.3 Operating conditions

To successfully run the programs in this package, the following is required:

The ar\_pose.launch in ar\_pose must be able to run successfully.

### 7.7 rei\_ydlidar\_nodelet

Function: Acquiring 2D LiDAR data

This package utilizes nodelet to reduce the time loss caused by data transmission during dual LiDAR data fusion.

Plugin name: rei\_ydlidar/ReiYdlidars

#### 7.7.1 File structure

Among them,

nodelet\_1\_lidar.launch: Start the front LiDAR

nodelet\_2\_lidar.launch: Start both the front and rear LiDARs

#### 7.7.2 ROS API

#### Published Topic

|**Topic name**\
**(message type)**|**Function**|**Parameter description**|

|\~/scan(sensor\_msgs/La\
serScan)|LiDAR topics|http://docs.ros.org/en/melodic/api/senso\
r\_msgs/html/msg/LaserScan.html|

#### Configuration parameters

| **Parameter name** | **Parameter description**                                                                 |
| ------------------ | ----------------------------------------------------------------------------------------- |
| Port               | <p>string type, default value /dev/ydlidar, LiDAR serial port<br>number or IP address</p> |
| ignore\_array      | string type, default value " ", laser angles to be ignored                                |
| frame\_id          | <p>string type, default value laser_frame, LiDAR coordinate<br>frame</p>                  |
| baudrate           | <p>int type, default value 230400, baud rate or network port<br>number</p>                |

![Official manual image, source page 70](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FnsEXFC1llC0Lo56DsNkh%2Fe6-ros-p070-img02.png?alt=media)

| <p><strong>Parameter name</strong><br>lidar_type</p> | <p><strong>Parameter description</strong><br>int type, default value 1, LiDAR type, 0 TYPE_TOF, 1<br>TYPE_TRIANGLE, 2 TYPE_TOF_NET</p> |
| ---------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| device\_type                                         | <p>int type, default value 0, device communication type, 0<br>YDLIDAR_TYPE_SERIAL, 1 YDLIDAR_TYPE_TCP, 2<br>YDLIDAR_TYPE_UDP</p>       |
| sample\_rate                                         | <p>int type, default value 9, measurement frequency, unit: kilo-<br>times/second</p>                                                   |
| abnormal\_check\_count                               | <p>int type, default value 4, defines the number of retry attempts<br>for handling abnormal data during device startup</p>             |
| resolution\_fixed                                    | bool type, default value true, fixed angular resolution                                                                                |
| reversion                                            | bool type, default value true, invert LiDAR                                                                                            |
| inverted                                             | <p>bool type, default value true, reverse LiDAR, false for<br>clockwise, true for counterclockwise</p>                                 |
| auto\_reconnect                                      | bool type, default true, auto-reconnect to the LiDAR                                                                                   |
| isSingleChannel                                      | bool type, default false, whether the LiDAR is single-channel                                                                          |
| intensity                                            | <p>bool type, default false, whether the LiDAR supports<br>intensity data</p>                                                          |
| support\_motor\_dtr                                  | <p>bool type, default false, whether the LiDAR can be<br>started/stopped via Serial DTR</p>                                            |
| invalid\_range\_is\_inf                              | <p>bool type, default false, whether to set invalid distances as<br>inf</p>                                                            |
| angle\_max                                           | float type, default 180.0, maximum valid angle in degrees                                                                              |
| angle\_min                                           | float type, default -180.0, minimum valid angle in degrees                                                                             |

| **Parameter name** | **Parameter description**                              |
| ------------------ | ------------------------------------------------------ |
| range\_min         | float type, default 0.1, minimum valid range in meters |
| frequency          | float type, default 10.0, scanning frequency in Hz     |

#### 7.7.3 Operating conditions

To successfully run the programs in this package, the following condition must be met:

The LiDAR must be functioning properly and communication must be stable.

### 7.8 rei\_lidar\_fuse

Function: Dual LiDAR fusion

Subscribe to LiDAR data using the nodelet method.

Plugin name: rei\_lidar\_fuse/LidarFuse

#### 7.8.1 File structure

![Official manual image, source page 72](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FKb8kcYa0nlHeKYsYL8pJ%2Fe6-ros-p072-img02.png?alt=media)

#### 7.8.2 ROS API

#### Subscribed Topic

|**Topic name**\
**(message type)**|**Function**|**Parameter description**|

|<\~front\_topic>(sensor\_msg\
s/LaserScan)|Front LiDAR topic|http://docs.ros.org/en/melodic/api/s\
ensor\_msgs/html/msg/LaserScan.h\
tml| |<\~rear\_topic>(sensor\_msgs\
/LaserScan)|Rear LiDAR topic|/|

#### Published Topic

|**Topic name**\
**(message type)**|**Function**|**Parameter description**|

|fuse\_scan(sensor\_msgs/La\
serScan)|Fused LiDAR data|http://docs.ros.org/en/melodic/api/\
sensor\_msgs/html/msg/LaserSca\
n.html|

#### Configuration parameters

| **Parameter name** | **Parameter description**                                                             |
| ------------------ | ------------------------------------------------------------------------------------- |
| frame\_id          | <p>string type, default "laser_link", coordinate frame of the fused<br>LiDAR data</p> |
| front\_topic       | string type, default /front\_lidar/scan, topic of the front LiDAR                     |
| rear\_topic        | string type, default /rear\_lidar/scan, topic of the rear LiDAR                       |
| angle\_max         | float type, default 3.1415, maximum valid angle in radians                            |
| angle\_min         | float type, default -3.1415, minimum valid angle in radians                           |
| range\_max         | float type, default 7.0, maximum valid range in meters                                |
| range\_min         | float type, default 0.25, minimum valid range in meters                               |

| angle\_increment | float type, default 0.014, angular resolution in radians |
| ---------------- | -------------------------------------------------------- |
| scan\_time       | ffloat type, default 0.02, scan time interval in seconds |

#### 7.8.3 Operating requirements

To successfully run the programs in this package, the following condition must be met: None.

### 7.9 berxel\_camera

Function: Depth camera driver package

Node name: berxel\_camera

#### 7.9.1 File structure

Among them,

berxel\_arm\_camera.launch: Arm-mounted depth camera launch file

![Official manual image, source page 74](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FO6s4jVsw7Rl3OlZHCPyx%2Fe6-ros-p074-img02.png?alt=media)

berxel\_body\_camera.launch: Chassis-mounted depth camera launch file

berxel\_multi\_camera.launch: Dual depth camera launch file

#### 7.9.2 ROS API

#### Published Topic

|**Topic name**\
**(message type)**|**Function**|**Parameter description**|

|~~/rgb/camera\_info(sensor\_~~\
~~msgs/CameraInfo)|Color camera intrinsics|http://docs.ros.org/en/melodic~~\
~~/api/sensor\_msgs/html/msg/C~~\
~~ameraInfo.html| |~~/depth/camera\_info(sensor\
\_msgs/CameraInfo)|Depth camera intrinsics|/| |~~/ir/camera\_info(sensor\_ms~~\
~~gs/CameraInfo)|Infrared camera intrinsics|/| |~~/rgb/rgb\_raw(sensor\_msgs\
/Image)|Color image|http://docs.ros.org/en/melodic\
/api/sensor\_msgs/html/msg/I\
mage.html| |~~/depth/depth\_raw(sensor\_~~\
~~msgs/Image)|Depth image|http://docs.ros.org/en/melodic~~\
~~/api/sensor\_msgs/html/msg/I~~\
~~mage.html| |~~/ir/ir\_raw(sensor\_msgs/Im\
age)|Infrared image|http://docs.ros.org/en/melodic\
/api/sensor\_msgs/html/msg/I\
mage.html| |\~/berxel\_cloudpoint(sensor\
\_msgs/PointCloud2)|Point cloud data|http://docs.ros.org/en/melodic\
/api/sensor\_msgs/html/msg/P\
ointCloud2.html|

#### Configuration parameters

| **Parameter name** | **Parameter description**                                                                                                  |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| stream\_flag       | <p>int type, default 1, stream mode, 1 single stream, 2 mixed<br>stream, 3 HD mixed mode (infrared not supported in HD</p> |

|                               | mode), 4 QVGA                                                                                                                                          |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| stream\_type                  | <p>int type, default 1, stream type, 1 color, 2 depth, 3<br>color+depth, 4 infrared with flood illumination, 5<br>color+infrared, 6 depth+infrared</p> |
| color\_width                  | int type, default 400, color stream resolution                                                                                                         |
| color\_height                 | int type, default 640, color stream resolution                                                                                                         |
| depth\_width                  | int type, default 400, depth stream resolution                                                                                                         |
| depth\_height                 | int type, default 640, depth stream resolution                                                                                                         |
| ir\_width                     | int type, default 400, infrared stream resolution                                                                                                      |
| ir\_height                    | int type, default 640, infrared stream resolution                                                                                                      |
| depth\_fps                    | <p>int type, default 640, depth frame rate (VGA and QVGA<br>support 5, 10, 15, 20, 25, 30; HD mode only supports 10)</p>                               |
| Registration                  | int type, default 0, registration switch: 0: off, 1: on                                                                                                |
| publish\_depth\_original\_raw | <p><sup>int type, default 0, depth data publishing mode: 0: depth, 1:</sup><br>depth_original_raw</p>                                                  |
| publish\_cloud\_point         | int type, default 0, point cloud publishing switch: 0: off, 1: on                                                                                      |
| color\_cloud\_point           | int type, default 0, colored point cloud: 0: off, 1: on                                                                                                |
| ordered\_cloud                | <p>int type, default 0, point cloud type: 0: unorganized point<br>cloud, 1: organized point cloud</p>                                                  |
| time\_stamp                   | <p>int type, default 0, timestamp type: 0: use device timestamp,<br>1: use ROS timestamp</p>                                                           |

**NOTE:** When the stream\_flag is set to HD mode, the color and depth resolution of the depth camera used on this robot must be set to 1280×800.

#### 7.9.3 Operating requirements

To successfully run the programs in this package, the following conditions must be met:

* The depth camera must be functioning properly and communication must be stable.
* It cannot be launched simultaneously with the LiDAR.

### 7.10 robot\_cruise

Function: Picking task scheduling

Node names: cruise\_node, cruise\_client

#### 7.10.1 File structure

The client.cpp is a client used to invoke various services in cruise\_node, designed for adding and configuring picking tasks.

#### 7.10.2 ROS API

#### Published Topic(cruise\_node)

|**Topic name**\
**(message type)**|**Function**|**Parameter description**|

|goals\_markers(visualization\_\
msgs/MarkerArray)|Visualize\
target\
points in RViz|http://docs.ros.org/en/melodic/api/vi\
sualization\_msgs/html/msg/Marker\
Array.html|

![Official manual image, source page 78](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2FeFsBFZpM1TDR9HmuYPCN%2Fe6-ros-p078-img02.png?alt=media)

#### Services(cruise\_node)

|**Service name**\
**(service type)**|**Function**|**Parameter description**|

|set\_goals(robot\_cruise/SetG\
oals)|Set target point|string mode: Target point setting\
mode, insert: add new target points,\
reset: delete previous target points\
and then add new target points\
robot\_cruise/NavGoal\[] goals:\
Information of the target points to be\
added (\
string point\_name: Navigation point\
name\
int8 level: Navigation point priority, 0: if\
navigation to this point fails, skip and\
continue to the next point, 1: if\
navigation to this point fails, stop the\
entire task\
geometry\_msgs/PoseStamped\
target\_pose: Coordinate information of\
the navigation point )\
\---\
bool isSuccess| |start\_stop\_nav(robot\_cruise/\
StartStopNav)|Start, pause, sto\
task|p\
string mode: Action mode, start: begin,\
pause: suspend, stop: terminate\
int8 level: Command priority, 0: wait\
for the previous task to complete\
before executing this command, 1:\
execute this command immediately\
\---\
bool isSuccess| |set\_goals\_order(robot\_cruis\
e/SetNavOrder)|Set navigation\
point execution\
order|int16 loop\_time: Number of cycles, 0\
indicates infinite looping\
string\[] goal\_order: Navigation point|

|**Service name**\
**(service type)**|**Function**|**Parameter description**|

|||sequence\
\---\
bool isSuccess| |remove\_goalsr(robot\_cruise/\
RemoveGoal)|Delete navigation\
points|\
string mode: Deletion mode, all: delete\
all, not\_all: delete specific points\
string\[] goal\_names: Names of\
navigation points to be deleted, valid\
when mode is not\_all\
\---\
bool isSuccess|

#### Others

This node offers sophisticated functionality designed for diverse navigation scheduling tasks. By mastering the RobotCruise class within this node, you can subsequently configure multi-point navigation missions according to your specific requirements.

#### RobotCruise class

Invocation logic:

For detailed source code explanations, please refer to: https://gitee.com/reinovo/robot\_cruise.git.

![Official manual image, source page 81](https://1292444914-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FtgOfPnscWebs1eh82EKq%2Fuploads%2Fu3sOJovMSojXCdw4Nyqq%2Fe6-ros-p081-img02.png?alt=media)

## 8. Precautions and Maintenance

The Bobac3 robot is a mobile service robot designed to ensure continuous energy supply, ensuring its uninterrupted operation. It features a charging interface, and the battery typically lasts up to 4 hours. When not in use, press the emergency stop button and use a power adapter or a mobile charging station to recharge the robot. The adapter's indicator light has two states: red and green. A red light indicates that the robot is charging, while a green light signifies that the battery is fully charged. However, avoid overcharging the robot when it is fully charged. Keep the robot powered when idle and charge it regularly. When not in use, try to charge it once a month or twice a month. Below are the usage precautions.

1. When using, please handle with care, especially when removing the module, be careful not to pull the internal wires, and ensure that the ground is clean for robot use.
2. Do not place other objects or shielding on the bobac3 robot.
3. Do not change or plug and unplug the lines privately, and check whether the external sensor and receiver connection lines are inserted into the control machine.
4. Check whether the emergency stop button is in normal condition.
5. Check if the screws are loose.
6. Check whether there is any foreign matter on each sensor, especially metal foreign matter is prohibited.
7. Ensure that there is no obstacle on the radar to ensure the normal operation of the radar.
8. Please handle with care during transportation.
9. When using the controller to control the robot, do not collide with sharp or uneven objects
10. Use the human body following laboratory to choose a place where the foreground and background are clearly distinguished as far as possible, control the robot, please follow the control gesture rules (surrender gesture)
11. When using voice-related features, make sure the robot is connected to the Internet
12. Keep a proper distance from the robot when it is moving
13. In case of special circumstances, stop the robot movement and press the emergency stop button directly. After turning off the program, the emergency stop button can be suspended.
14. After long-term idling, please charge the robot before use. If not used, please keep the battery sufficient for storage. Do not use non-compatible adapter to charge the robot.
15. Do not connect the charging port to the power adapter.

## 9. Appendix

#### Commonly used commands in Ubuntu system:

* sudo: Authorize
* rm: Delete
* mkdir: Create a directory
* touch: Create a file
* cat: View and concatenate file contents
* ps: Display status of running processes
* grep: Search for specified strings
* kill: Terminate processes
* nohup: Run processes in the background

```bash
ls command: ls -a displays all files and directories, including hidden ones
```

* pwd command: Used to show the current path

```bash
cd command: Used to change the current directory
```

* apt-get update command: Get the latest package information
* apt-get upgrade command: Update the software package
* apt-get dist-upgrade command: Update the software package

These commands are highly useful in the Ubuntu system, helping you manage and utilize your system more efficiently.

#### How to use Vim editor

1. Three modes in Vim:
   * Command mode: Control the cursor, perform operations like copy, paste, delete, and query files.
   * Edit mode: Enter and modify text.
   * Last-Line mode: Save and exit documents, and configure the editing environment.
2. Press a, A, or i in Vim's Command Mode to switch to Edit mode.
3. In command mode, actions like deletion, copying, and pasting are available, but direct text editing is disabled. Pressing any of the keys i, I, o, O, a, A, r, or R switches to Edit mode. In Linux systems, when pressing these keys, "INSERT" or "REPLACE" will appear at the bottom-left of the screen to indicate active editing. Press 『 Esc 』 to return to command mode.
4. Pressing “I” in Command mode keeps the cursor at its current position, inserting text before the cursor. Pressing “a” moves the cursor one position forward and inserts text before it.
5. In command mode, pressing "o" allows you to enter edit mode and start editing on a new line. Regardless of the current cursor position, it will automatically jump to the next line and insert a new line for editing.
6. In Last-Line Mode, use “wq” or “Shift + zz”” to save and exit. To force quit without saving, enter “q!” in Last-Line Mode.
