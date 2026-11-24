---
description: >-
  Robot perception, motion, manipulation and mobile-platform manuals, with
  model-specific commissioning, calibration, software and source references.
---

# Robotics Documentation

**Understand the hardware behind perception, motion and manipulation.**

Find manuals and engineering references for LiDAR, depth cameras, joint actuators, servos, dexterous hands, industrial and research arms, mobile robots and humanoid platforms. Begin with the manufacturer, then select the exact model and hardware/software revision.

Browse 32 manufacturer and brand directories with 541 visible wiki pages beneath them. Coverage updated 24 November 2026.

Unitree robot development. [Explore Unitree model guides, English manuals, SDK2 and ROS 2 development](unitree/); verify hardware edition, development access, software versions and message family before a robot session.

## Model-specific commissioning paths

Use the exact power, mechanism and software revision before moving hardware. These guides stage communication and calibration before application control, and identify automatic startup/exit movement where it is implemented.

| Development task                                                              | Guide                                                                               |
| ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Calibrate an assembled leader/follower pair and inspect a local dataset       | [Seeed SO-ARM101 Pro](../aiot/seeed-studio/so-arm101-pro-development-guide.md)      |
| Read a leader’s seven joint angles before connecting a follower               | [Seeed Star Arm 102](../aiot/seeed-studio/star-arm-102-leader-development-guide.md) |
| Identify a DAMIAO follower bus and account for LeRobot startup/return motion  | [Seeed reBot B601-DM](../aiot/seeed-studio/rebot-b601-dm-development-guide.md)      |
| Establish camera, UART and ROS2 control-publisher boundaries on a mobile base | [Waveshare UGV Beast](../aiot/waveshare/waveshare-ugv-beast-development-guide.md)   |
| Develop a desktop character one subsystem at a time                           | [M5Stack StackChan](../aiot/m5stack/stackchan-k151-development-guide.md)            |

## Start here

| What you want to do                      | Where to find documentation                                                                                                                                                              |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Find LiDAR or depth camera documentation | [LIVOX](livox/) · [HESAI](hesai/) · [RoboSense](robosense/) · [Orbbec](orbbec/)                                                                                                          |
| Configure a joint actuator or servo      | [CubeMars](cubemars/) · [DAMIAO](damiao/) · [RobStride](robstride/) · [FEETECH](feetech/) · [MyActuator](myactuator/)                                                                    |
| Explore robotic arms or mobile platforms | [AgileX](agilex/) · [DOBOT](dobot/) · [RealMan](realman/) · [AgiBot](agibot/) · [Yahboom](yahboom/) · [Agile Robots](agile-robots/) · [Franka](franka/)                                  |
| Work with a dexterous hand               | [LINKERBOT](linkerbot/) · [Leadshine](leadshine/) · [AgiBot](agibot/) · [Agile Hand](agile-robots/agile-hand.md)                                                                         |
| Develop with Industrial APIs or FCI      | [Industrial C/C++ and Python](agile-robots/development/industrial-api.md) · [Diana FS FCI](agile-robots/development/diana-fci.md) · [Franka FCI / ROS 2](franka/development/fci-ros2.md) |

## Popular product guides

| Product guide                                                                                                 | Manufacturer              |
| ------------------------------------------------------------------------------------------------------------- | ------------------------- |
| [Livox MID-360S 3D LiDAR Sensor Engineering Guide](livox/livox-mid-360s-3d-lidar-sensor-engineering-guide.md) | [Livox](livox/)           |
| [RobStride 04 Instruction Manual](robstride/robstride-04-instruction-manual.md)                               | [RobStride](robstride/)   |
| [Robosense Airy](robosense/robosense-airy.md)                                                                 | [RoboSense](robosense/)   |
| [MyActuator RMD-X12-P20-320-E Development Guide](myactuator/rmd-x12-p20-320-e-development-guide.md)           | [MyActuator](myactuator/) |
| [RobStride 03 Instruction Manual](robstride/robstride-03-instruction-manual.md)                               | [RobStride](robstride/)   |
| [RobStride 06 Instruction Manual](robstride/robstride-06-instruction-manual.md)                               | [RobStride](robstride/)   |
| [Orbbec Gemini 435Le User Manual](orbbec/orbbec-gemini-435le-user-manual.md)                                  | [Orbbec](orbbec/)         |
| [Robosense M1 Plus](robosense/robosense-m1-plus.md)                                                           | [RoboSense](robosense/)   |

Guide order follows our Top 200 net-sales snapshot for 17 August–17 November 2026. Guides shared by multiple variants appear once.

## Develop with model-specific references <a href="#develop-with-model-specific-references" id="develop-with-model-specific-references"></a>

**Receive and interpret sensor data.** [MID-360S](livox/livox-mid-360s-3d-lidar-sensor-engineering-guide.md), [Airy](robosense/robosense-airy.md) and [AC1](robosense/robosense-ac1-active-camera-engineering-guide.md) connect packet fields, timing, SDK callbacks and configuration to observable data checks.

**Read joint telemetry before motion.** [RMD-X6-P20-60-E](myactuator/myactuator-rmd-x6-x8-p20-development-guide.md) and [RobStride 10P](robstride/robstride-10p-development-guide.md) distinguish physical limits from encoded ranges and keep model, transport and firmware differences explicit.

**Develop with the correct robot image.** [ROSMASTER M3 Pro](yahboom/rosmaster-m3-pro-development-guide.md), [ROSpider](hiwonder/hiwonder-rospider-development-guide.md) and [JetRover](hiwonder/hiwonder-jetrover-development-guide.md) bring controller APIs, perception, navigation, calibration and course procedures onto the canonical product guides.

**Calibrate and recover.** [SO-ARM101](wowrobo/wowrobo-so-arm101-lerobot.md) and [myAGV Raspberry Pi 2023](elephant-robotics/myagv-2023-pi.md) retain exact-kit and host boundaries, configuration records, diagnostic steps and recovery resources. Source review is stated separately from hardware execution.

## Manufacturer directory

Manufacturers are ordered by recorded GitBook website page views over the last three months, then by visible wiki-page count when views are tied. Equal view and page counts are ordered by brand name. Ranking snapshot: 24 November 2026.

“Wiki pages” counts visible document pages beneath each manufacturer; it excludes the manufacturer landing page, hidden pages and external links. Traffic includes the manufacturer page and its published branch pages. The Popular product guides lists use the separate dated net-sales snapshot stated above.

<table><thead><tr><th>Manufacturer / brand</th><th>Products and documentation</th><th data-type="number">Wiki pages</th></tr></thead><tbody><tr><td><a href="agibot/">AgiBot</a></td><td>Robot platforms, OmniHand devices and OmniPicker.</td><td>13</td></tr><tr><td><a href="agilex/">AgileX</a></td><td>UGVs, LIMO platforms, PiPER and NERO arms, and PiKA data tools.</td><td>11</td></tr><tr><td><a href="dobot/">DOBOT</a></td><td>Desktop arms, collaborative robots, workstations, and embodied-AI tools.</td><td>101</td></tr><tr><td><a href="robosense/">RoboSense</a></td><td>Airy, Fairy, solid-state LiDAR, and AC1 robot perception hardware.</td><td>17</td></tr><tr><td><a href="orbbec/">Orbbec</a></td><td>Gemini and Femto camera families, SDK compatibility, calibration and synchronization.</td><td>11</td></tr><tr><td><a href="damiao/">DAMIAO</a></td><td>DM-J8006-2EC actuator and USB2CAN commissioning, frames and diagnostics.</td><td>23</td></tr><tr><td><a href="cubemars/">CubeMars</a></td><td>Robot actuators, gimbal motors, underwater thrusters, and setup guides.</td><td>24</td></tr><tr><td><a href="linkerbot/">LINKERBOT</a></td><td>L/O-series canonical model guides, seven complete supplied manuals covering all 137 PDF pages, and bus, ROS 2, tactile and Windows tutorials.</td><td>21</td></tr><tr><td><a href="realman/">RealMan</a></td><td>RM/RML/RX and ECO arms, WHJ joints, RMG22-65 gripper, RealBot L2/S2 platforms and development references. Complete in-wiki manuals for all 405 supplied source pages.</td><td>30</td></tr><tr><td><a href="xiaomi/">Xiaomi</a></td><td>CyberGear micromotor references.</td><td>2</td></tr><tr><td><a href="lkmtech/">LKMTECH</a></td><td>Robot joint motors and encoder references.</td><td>4</td></tr><tr><td><a href="livox/">Livox</a></td><td>MID, HAP, TELE, and AVIA LiDAR families and integration guides.</td><td>13</td></tr><tr><td><a href="feetech/">FEETECH</a></td><td>Bus servos, control protocols, memory tables, SDKs, and debug tools.</td><td>13</td></tr><tr><td><a href="robstride/">RobStride</a></td><td>Joint actuators, CAN parameters, debug/power boards and humanoid motor integration.</td><td>12</td></tr><tr><td><a href="hiwonder/">Hiwonder</a></td><td>ROS robot cars, hexapods, robotic arms, bus servos, and chassis.</td><td>104</td></tr><tr><td><a href="unitree/">Unitree</a></td><td>Humanoid and quadruped robot guides, SDK2, ROS 2, English manuals, LiDAR and joint actuators; match exact model/edition and firmware.</td><td>30</td></tr><tr><td><a href="hesai/">HESAI</a></td><td>JT and XT LiDAR families and JT128 integration documentation.</td><td>1</td></tr><tr><td><a href="franka/">Franka (Agile Robots)</a></td><td>FR3 Arm v2.1, Franka Hand, FR3 Duo, Mobile FR3 Duo, TMR and GELLO Duo, with startup, Desk, World and FCI development guides. Complete supplied manuals and all 43 training slides are readable in the wiki.</td><td>25</td></tr><tr><td><a href="myactuator/">MyActuator</a></td><td>RMD joint actuators, CAN commands, EtherCAT objects and model-specific limits.</td><td>12</td></tr><tr><td><a href="leadshine/">Leadshine</a></td><td>DH116 dexterous robot hand documentation.</td><td>1</td></tr><tr><td><a href="agile-robots/">Agile Robots</a></td><td>Diana 3/7, Thor 3/7/7 Pro/12/20, controllers, Agile Hand, H10-W/H20 references and Industrial V3.3 training/API guides. Complete public manuals and all 134 training slides are readable in the wiki; H10-W/H20 specifications are summarized without internal files.</td><td>64</td></tr><tr><td><a href="yahboom/">Yahboom</a></td><td>ROSMASTER, MicroROS, DOFBOT, and JetCobot robotics platforms.</td><td>2</td></tr><tr><td><a href="realsense/">RealSense</a></td><td>D400 and D405 depth cameras, D435if filtering, SDK setup and calibration.</td><td>1</td></tr><tr><td><a href="elephant-robotics/">Elephant Robotics</a></td><td>myCobot desktop arms, grippers, cameras, and learning accessories.</td><td>1</td></tr><tr><td><a href="ldrobot/">LDROBOT</a></td><td>Compact 2D LiDAR, developer kits, and single-point ranging sensors.</td><td>1</td></tr><tr><td><a href="lslidar/">LSLiDAR</a></td><td>2D and 3D LiDAR sensors for navigation, mapping, and spatial sensing.</td><td>1</td></tr><tr><td><a href="steadywin/">SteadyWin</a></td><td>GIM robot joint actuators and motor-control hardware.</td><td>1</td></tr><tr><td><a href="aumovio/">AUMOVIO</a></td><td>ARS 548 RDI radar hardware, physical interfaces and integration resources.</td><td>1</td></tr><tr><td><a href="wowrobo/">WowRobo</a></td><td>SO-ARM101, XLeRobot, LeKiwi, robotic hands, and tactile-sensing kits.</td><td>1</td></tr><tr><td><a href="changingtek.md">ChangingTek</a></td><td>Electric grippers, adaptive hands, and manipulation-data tools.</td><td>0</td></tr><tr><td><a href="slamtec.md">SLAMTEC</a></td><td>RPLIDAR, Mapper, Aurora, and industrial laser scanners.</td><td>0</td></tr><tr><td><a href="wheeltec.md">WHEELTEC</a></td><td>Control learning kits, balance robots, ROS platforms, and components.</td><td>0</td></tr></tbody></table>

## Recently expanded robotics documentation

| Documentation series          | What you’ll find                                                                                                                      |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| [Agile Robots](agile-robots/) | Diana/Thor arms, two controller families, Agile Hand and humanoid references; 64 wiki pages beneath the directory.                    |
| [Franka research](franka/)    | FR3, Hand, Duo/TMR/GELLO and training/development; 25 wiki pages beneath the directory.                                               |
| [RealMan](realman/)           | Arm families, joint modules, gripper and RealBot platform/development documentation.                                                  |
| [LINKERBOT](linkerbot/)       | 21 wiki pages with expanded canonical model guides, complete coverage of all 137 supplied PDF pages and shared development tutorials. |

## Before you begin

* Check the exact hardware model, firmware and communication interface against the manual.
* Review the manufacturer’s power, mounting and safety instructions before enabling motion.
* For software integration, record the SDK or driver version, operating system and relevant coordinate-frame or calibration settings.

## Explore other areas

| Explore                                                      | Documentation coverage                                                                             |
| ------------------------------------------------------------ | -------------------------------------------------------------------------------------------------- |
| [AIoT](../aiot/aiot-wiki-home-page.md)                       | Microcontrollers, connected devices, sensors, displays, wireless communication and edge computing. |
| [STEM & DIY](../stem-and-diy/stem-and-diy-wiki-home-page.md) | Educational robots, electronics projects, drones and FPV, 3D printing and CNC equipment.           |

[Return to the OpenELAB Wiki home page](../) for the complete brand directory and more starting points.

If you need technical help, include the product model, page link, software versions and a description of the problem.

[**Contact OpenELAB**](mailto:info@openelab.io) · [**Explore hardware on OpenELAB**](https://openelab.io)
