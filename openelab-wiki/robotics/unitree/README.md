---
description: >-
  English Unitree robot and component guides: model setup, SDK2, ROS 2, hands,
  sensors, motors, teleoperation, RL and navigation with official source
  coverage.
cover: ../../.gitbook/assets/unitree-wordmark.png
coverY: 0
---

# Unitree

Unitree documentation spans quadrupeds, wheel-legged robots, humanoids, arms, hands, LiDAR and joint actuators. Identify the exact hardware, retail/EDU option and software release before selecting a development interface. A shared model name, DDS topic or SDK repository does not establish the same joint map or development entitlement.

## Choose a Unitree development workflow <a href="#choose-a-unitree-development-workflow" id="choose-a-unitree-development-workflow"></a>

Start with the exact model guide for power, physical support, controller revision and fitted options. Then choose the software task below. Standard/EDU labels, common topic names and similar bodies do not establish identical development access or message layouts.

| Development task                                | Start here                                                                                                                                                                                                                                                                                                       | Decision to resolve first                                                                                                                     |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Read robot state through SDK2                   | [Unitree SDK2 State Development: Go2, G1 and R1](unitree-sdk2-state-development.md)                                                                                                                                                                                                                              | Match the exact model, GO/HG type, firmware, host interface and installed joint map before a subscriber-only check.                           |
| Connect ROS 2 and visualize sensor data         | [Unitree ROS 2 integration: message families, Cyclone DDS and subscriber-first checks](unitree-ros2-integration.md)                                                                                                                                                                                              | Keep middleware, generated message types, topic direction, timestamps and coordinate frames together.                                         |
| Train or transfer a locomotion policy           | [Unitree RL Gym: training, policy contracts and simulator transfer](unitree-reinforcement-learning.md)                                                                                                                                                                                                           | Match observation/action order, control period, artifact and simulator configuration; simulated success does not qualify physical deployment. |
| Study a legacy quadruped controller             | [Unitree quadruped control practice: FSM, simulation and timing](unitree-algorithm-practice.md)                                                                                                                                                                                                                  | The Go1/A1 ROS1 practice controller is a different generation from SDK2.                                                                      |
| Build a teleoperation system                    | [Unitree teleoperation: AVP, Kinect and model compatibility](unitree-teleoperation.md)                                                                                                                                                                                                                           | Choose the exact robot, arm, hand and tracking generation; separate image transport from control ownership.                                   |
| Integrate maps, routes or industrial navigation | [Unitree industrial navigation: maps, routes, APIs and offline data](unitree-industrial-navigation.md); [Unitree G1 Standard and EDU: Robot Setup and State Development Guide](unitree-g1-standard-edu-development-guide.md); [Unitree R1, R1 AIR and R1 EDU: Setup, Charging and SDK Boundaries](unitree-r1.md) | Industrial navigation and biped SLAM have separate model/service contracts; request acceptance is not arrival.                                |
| Decode LiDAR or joint-actuator data             | [Unitree L2 4D LiDAR Engineering Guide](unitree-l2-4d-lidar-engineering-guide.md); [Unitree GO-M8010-6 Motor User Manual](unitree-go-m8010-6-motor-user-manual.md)                                                                                                                                               | Retain the correct supply, wiring, packet layout, CRC, units, coordinate convention and firmware release.                                     |

## Popular product guides <a href="#popular-product-guides" id="popular-product-guides"></a>

The existing Top200 net-sales order for 17 August–17 November 2026 is retained. It is separate from manufacturer website-traffic ranking.

| Product guide                                                                     | Scope                                                                                                             |
| --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| [Unitree L2 4D LiDAR engineering guide](unitree-l2-4d-lidar-engineering-guide.md) | Serial/Ethernet, packets/IMU, SDK and ROS; its historical exact OpenELAB package/listing match remains unverified |

## Robot setup and development guides <a href="#robot-setup-and-development-guides" id="robot-setup-and-development-guides"></a>

* [Unitree G1 Standard and EDU: Robot Setup and State Development Guide](unitree-g1-standard-edu-development-guide.md)
* [Unitree Go2 Air, Pro and EDU: model selection, startup and development limits](unitree-go2.md)
* [Unitree Go2-W U1–U5: wheeled hardware, startup and SDK status](unitree-go2-w.md)
* [Unitree R1, R1 AIR and R1 EDU: Setup, Charging and SDK Boundaries](unitree-r1.md)
* [Unitree SDK2 State Development: Go2, G1 and R1](unitree-sdk2-state-development.md)
* [Unitree ROS 2 integration: message families, Cyclone DDS and subscriber-first checks](unitree-ros2-integration.md)

These guides distinguish source-reviewed instructions, original offline checks, compatible-hardware prerequisites and untested operations. Go2 Air/Pro versus EDU and G1 base versus EDU must not be treated as equivalent SDK entitlements. The exact delivered firmware and physical stop/commissioning controls remain model-specific.

## Humanoid model guides <a href="#unitree-batch-02" id="unitree-batch-02"></a>

* [Unitree H1: 19-joint hardware, power scope and state-only development](unitree-h1.md)
* [Unitree H1-2: 27-joint hardware, parallel ankles and HG state telemetry](unitree-h1-2.md)
* [Unitree H2 and H2 EDU: interfaces, manuals and SDK contract checks](unitree-h2.md)
* [Unitree H2-X and H2-X EDU: model differences and SDK state contracts](unitree-h2-x.md)
* [Unitree G1+ and G1+ EDU: configuration, power and development evidence](unitree-g1-plus.md)

## Industrial quadruped guides <a href="#unitree-batch-03" id="unitree-batch-03"></a>

* [Unitree A2 and A2 Pro: Hardware, Operation and State Development](unitree-a2.md)
* [Unitree A2-W and A2-W Pro: Wheel Hardware and Development Boundaries](unitree-a2-w.md)
* [Unitree As2 AIR, PRO, X and EDU: Model and Development Guide](unitree-as2.md)
* [Unitree As2-W X and EDU: Wheel Robot and State Development Guide](unitree-as2-w.md)
* [Unitree B2: power, remote revisions and read-only development](unitree-b2.md)
* [Unitree B2-W: wheel mapping, operating limits and first state checks](unitree-b2-w.md)
* [Unitree B2-Ex: chassis and inspection-solution engineering boundaries](unitree-b2-ex.md)
* [Unitree B1: specifications and unresolved SDK compatibility](unitree-b1.md)

## Earlier robot platforms <a href="#unitree-batch-05" id="unitree-batch-05"></a>

* [Unitree Go1 Air, Pro and EDU: legacy SDK, interfaces and manual guide](unitree-go1.md)
* [Unitree A1 Standard and Exploration: legacy SDK and manual guide](unitree-a1.md)
* [Unitree AlienGo: legacy SDK lineages, interfaces and compatibility](unitree-aliengo.md)
* [Unitree Laikago and Laikago Pro: historical models and ROS resources](unitree-laikago.md)
* [Unitree XDog: historical quadruped prototype reference](unitree-xdog.md)

## Robot arms and teleoperation hardware <a href="#unitree-batch-04-arms" id="unitree-batch-04-arms"></a>

* [Unitree Z1 AIR and PRO: Ethernet SDK and ROS Development Guide](unitree-z1.md)
* [Unitree D1-T Teleoperation Kits: Edition and Development Guide](unitree-d1-t.md)
* [Unitree D2 Arm: ArmEcho, Python SDK and State Diagnostics](unitree-d2.md)
* [Unitree R1-7a Arm: Serial SDK, Web Console and Teleoperation Guide](unitree-r1-7a.md)

## Teleoperation, simulation and navigation <a href="#unitree-batch-06-advanced" id="unitree-batch-06-advanced"></a>

* [Unitree teleoperation: AVP, Kinect and model compatibility](unitree-teleoperation.md)
* [Unitree RL Gym: training, policy contracts and simulator transfer](unitree-reinforcement-learning.md)
* [Unitree quadruped control practice: FSM, simulation and timing](unitree-algorithm-practice.md)
* [Unitree industrial navigation: maps, routes, APIs and offline data](unitree-industrial-navigation.md)

## Perception and charging accessories <a href="#unitree-batch-06-sensors" id="unitree-batch-06-sensors"></a>

* [Unitree L1 4D LiDAR: power, MAVLink, frames and development](unitree-l1.md)
* [Unitree SV1-25: USB stereo capture, calibration and exact SDK interfaces](unitree-sv1-25.md)
* [Unitree BA2 / A2 Autonomous Charging Dock: ratings and integration boundaries](unitree-ba2.md)

## Motors and servos <a href="#unitree-batch-06-motors" id="unitree-batch-06-motors"></a>

* [Unitree IM6014 Motor: Wiring, Protocol and Development Guide](unitree-im6014-motor.md)
* [Unitree J288 and S288 Brushless Servos: Wiring and Development Guide](unitree-j288-s288-servo.md)
* [Unitree A1 Motor: Component Identification and SDK Development](unitree-a1-motor.md)
* [Unitree B1-16 Waterproof Joint: Hardware and Development Boundaries](unitree-b1-16-motor.md)

## Mobile and fixed upper-body platforms <a href="#unitree-batch-04-mobile" id="unitree-batch-04-mobile"></a>

* [Unitree G1-A: Fixed-Base Dual-Arm Robot Integration Guide](unitree-g1-a-fixed-upper-body.md)
* [Unitree G1-D Standard and Flagship: Chassis, Lift and SDK Guide](unitree-g1-d-mobile-manipulator.md)
* [Unitree H2-A and H2-D: Fixed and Mobile Manipulation Guide](unitree-h2-a-h2-d-upper-body.md)
* [Unitree R1-A5, A7 and D Variants: Dual-Arm Development Guide](unitree-r1-a5-a7-mobile-upper-body.md)

## Dexterous hands and grippers <a href="#unitree-batch-06-hands" id="unitree-batch-06-hands"></a>

* [Unitree Dex1-1: power, RS485 bridge and offline state inspection](unitree-dex1-1.md)
* [Unitree Dex3-1: seven-joint mapping, power and DDS boundaries](unitree-dex3-1.md)
* [Unitree Dex5-1 and Dex5-1P: coupled joints, tactile data and power](unitree-dex5-1.md)
* [Unitree Dex5-S and Pro: 22-axis hand integration boundaries](unitree-dex5-s.md)
* [Unitree Dex2/5: tendon hand and host-specific control](unitree-dex2-5.md)

## Official Unitree developer-section crosswalk <a href="#official-unitree-developer-section-crosswalk" id="official-unitree-developer-section-crosswalk"></a>

The English portal snapshot indexed on **24 November 2026** contains **30 sections and 628 source records**. The crosswalk below points to the applicable engineering guides and original resources. The guides combine original English functional explanations, source-specific corrections and resource indexes. This total includes empty grouping nodes and video-only entries; it is not a count of independent tutorials or of videos watched. Linked archives, firmware, CAD and video contents retain the access/review boundaries stated in each guide.

<details>

<summary>Browse all 30 official developer sections and their OpenELAB guides</summary>

| Official English developer section                                                                                            | Source records | OpenELAB engineering guide                                                                                                                                                         |
| ----------------------------------------------------------------------------------------------------------------------------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [H1 SDK Development Guide](https://support.unitree.com/home/en/H1_developer/About_H1)                                         | 43             | [Unitree H1: 19-joint hardware, power scope and state-only development](unitree-h1.md); [Unitree H1-2: 27-joint hardware, parallel ankles and HG state telemetry](unitree-h1-2.md) |
| [G1 SDK Development Guide](https://support.unitree.com/home/en/G1_developer/about_G1)                                         | 45             | [Unitree G1 Standard and EDU: Robot Setup and State Development Guide](unitree-g1-standard-edu-development-guide.md)                                                               |
| [H2 SDK Development Guide](https://support.unitree.com/home/en/H2_developer/About_H2)                                         | 29             | [Unitree H2 and H2 EDU: interfaces, manuals and SDK contract checks](unitree-h2.md)                                                                                                |
| [R1 SDK Development Guide](https://support.unitree.com/home/en/R1_developer/about_R1)                                         | 58             | [Unitree R1, R1 AIR and R1 EDU: Setup, Charging and SDK Boundaries](unitree-r1.md)                                                                                                 |
| [G1-D SDK Developer Guide](https://support.unitree.com/home/en/G1D_Developer/about)                                           | 16             | [Unitree G1-D Standard and Flagship: Chassis, Lift and SDK Guide](unitree-g1-d-mobile-manipulator.md)                                                                              |
| [R1-A SDK Development Guide](https://support.unitree.com/home/en/R1-A_developer/about_R1-A)                                   | 26             | [Unitree R1-A5, A7 and D Variants: Dual-Arm Development Guide](unitree-r1-a5-a7-mobile-upper-body.md)                                                                              |
| [R1-A-D SDK Development Guide](https://support.unitree.com/home/en/R1-A-D_SDK_Development_Guide/R1-A-D_SDK_Development_Guide) | 17             | [Unitree R1-A5, A7 and D Variants: Dual-Arm Development Guide](unitree-r1-a5-a7-mobile-upper-body.md)                                                                              |
| [G1+ SDK Development Guide](https://support.unitree.com/home/en/G1pl_developer/about_G1%2B)                                   | 37             | [Unitree G1+ and G1+ EDU: configuration, power and development evidence](unitree-g1-plus.md)                                                                                       |
| [H2D SDK Development Guide](https://support.unitree.com/home/en/H2D/about)                                                    | 14             | [Unitree H2-A and H2-D: Fixed and Mobile Manipulation Guide](unitree-h2-a-h2-d-upper-body.md)                                                                                      |
| [Teleoperation](https://support.unitree.com/home/en/Teleoperation/avp_teleoperate)                                            | 2              | [Unitree teleoperation: AVP, Kinect and model compatibility](unitree-teleoperation.md)                                                                                             |
| [Reinforcement Learning on Motion Control](https://support.unitree.com/home/en/rl_gym/intro)                                  | 18             | [Unitree RL Gym: training, policy contracts and simulator transfer](unitree-reinforcement-learning.md)                                                                             |
| [Go2 SDK Development Guide](https://support.unitree.com/home/en/developer/about_Go2)                                          | 53             | [Unitree Go2 Air, Pro and EDU: model selection, startup and development limits](unitree-go2.md)                                                                                    |
| [B2 SDK Development Guide](https://support.unitree.com/home/en/B2_developer/About%20B2)                                       | 35             | [Unitree B2: power, remote revisions and read-only development](unitree-b2.md); [Unitree B2-W: wheel mapping, operating limits and first state checks](unitree-b2-w.md)            |
| [Go2-W SDK Development Guide](https://support.unitree.com/home/en/Go2-W_developer/about_Go2-W)                                | 21             | [Unitree Go2-W U1–U5: wheeled hardware, startup and SDK status](unitree-go2-w.md)                                                                                                  |
| [Algorithm Practice](https://support.unitree.com/home/en/Algorithm_Practice/about_unitreeguide)                               | 7              | [Unitree quadruped control practice: FSM, simulation and timing](unitree-algorithm-practice.md)                                                                                    |
| [A2 SDK Development Guide](https://support.unitree.com/home/en/A2_SDK_Development_Guide/about_a2)                             | 34             | [Unitree A2 and A2 Pro: Hardware, Operation and State Development](unitree-a2.md); [Unitree A2-W and A2-W Pro: Wheel Hardware and Development Boundaries](unitree-a2-w.md)         |
| [As2 SDK Development Guide](https://support.unitree.com/home/en/AS2_SDK_Development_Guide/about_as2)                          | 27             | [Unitree As2 AIR, PRO, X and EDU: Model and Development Guide](unitree-as2.md); [Unitree As2-W X and EDU: Wheel Robot and State Development Guide](unitree-as2-w.md)               |
| [Z1 SDK Development Guide](https://support.unitree.com/home/en/Z1_developer/z1)                                               | 13             | [Unitree Z1 AIR and PRO: Ethernet SDK and ROS Development Guide](unitree-z1.md)                                                                                                    |
| [R1-7a Development Guide](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm)                                       | 8              | [Unitree R1-7a Arm: Serial SDK, Web Console and Teleoperation Guide](unitree-r1-7a.md)                                                                                             |
| [D2 Development Guide](https://support.unitree.com/home/en/D2_Arm_Development_Guide/about)                                    | 7              | [Unitree D2 Arm: ArmEcho, Python SDK and State Diagnostics](unitree-d2.md)                                                                                                         |
| [IM6014 Motor Development Guide](https://support.unitree.com/home/en/Motor_IM6014%20Development%20Guide/about_IM6014)         | 18             | [Unitree IM6014 Motor: Wiring, Protocol and Development Guide](unitree-im6014-motor.md)                                                                                            |
| [M8010 Motor SDK Development Guide](https://support.unitree.com/home/en/Motor_SDK_Dev_Guide/about)                            | 21             | [Unitree GO-M8010-6 Motor User Manual](unitree-go-m8010-6-motor-user-manual.md)                                                                                                    |
| [SV1-25 development guide](https://support.unitree.com/home/en/SV1-25_develop/about_SV1-25)                                   | 2              | [Unitree SV1-25: USB stereo capture, calibration and exact SDK interfaces](unitree-sv1-25.md)                                                                                      |
| [Dex3-1 Developer](https://support.unitree.com/home/en/dex3-1_hand/about_dex3-1)                                              | 5              | [Unitree Dex3-1: seven-joint mapping, power and DDS boundaries](unitree-dex3-1.md)                                                                                                 |
| [Dex1-1 Developer](https://support.unitree.com/home/en/dex1-1_gripper/about_dex1_1)                                           | 2              | [Unitree Dex1-1: power, RS485 bridge and offline state inspection](unitree-dex1-1.md)                                                                                              |
| [Dex5-1 SDK Development Guide](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/About%20Dex5-1%20Hand)  | 3              | [Unitree Dex5-1 and Dex5-1P: coupled joints, tactile data and power](unitree-dex5-1.md)                                                                                            |
| [J288/S288 Servo Development Guide](https://support.unitree.com/home/en/J288-S288%20Servo/About_J288-S288)                    | 18             | [Unitree J288 and S288 Brushless Servos: Wiring and Development Guide](unitree-j288-s288-servo.md)                                                                                 |
| [L1 SDK Development Guide](https://support.unitree.com/home/en/L1_SDK/L1_introduce)                                           | 14             | [Unitree L1 4D LiDAR: power, MAVLink, frames and development](unitree-l1.md)                                                                                                       |
| [L2 SDK Development Guide](https://support.unitree.com/home/en/L2_SDK/L2_introduce)                                           | 13             | [Unitree L2 4D LiDAR Engineering Guide](unitree-l2-4d-lidar-engineering-guide.md)                                                                                                  |
| [Industry-Grade Navigation User Guide](https://support.unitree.com/home/en/navigation/SLAM%26Navigation_service)              | 22             | [Unitree industrial navigation: maps, routes, APIs and offline data](unitree-industrial-navigation.md)                                                                             |

</details>

The original source revision, exact model/firmware applicability and the stated validation level remain part of each guide. Original offline checks support reproducible learning; they do not certify a delivered robot, a live stop function or physical deployment.

## Unitree Official Site <a href="#unitree-official-site" id="unitree-official-site"></a>

* [Unitree official products](https://www.unitree.com/)
* [Official support and developer portal](https://support.unitree.com/main/en)
* [Official Unitree source repositories](https://github.com/unitreerobotics)

## Product Collections <a href="#product-collections" id="product-collections"></a>

[Browse the full OpenELAB Unitree brand collection](https://openelab.io/collections/brands-unitree). Use the exact model guide's store/SKU links for its purchased configuration. The separate [Unitree collection](https://openelab.io/collections/unitree) is narrower and must not be used as a complete product inventory.

{% embed url="https://openelab.io/collections/unitree" %}

## More manuals and tutorials <a href="#more-manuals-and-tutorials" id="more-manuals-and-tutorials"></a>

<details>

<summary>Browse 1 additional guides</summary>

* [Unitree GO-M8010-6 motor user manual](unitree-go-m8010-6-motor-user-manual.md)

</details>

### Official English manual library <a href="#official-english-manual-library" id="official-english-manual-library"></a>

These are the manufacturer's original manuals, including model-specific user, battery, controller and mounting documents. Check the edition printed in the source and the configuration stated in the model guide; a live document URL may be revised over time. The model guides include original English interpretations and chapter indexes for reviewed manuals. Linked videos, CAD and archives have separate review limits; confirm the exact firmware and configuration.

| Model / document                 | Original English manual                                                                               | Source scan pages |
| -------------------------------- | ----------------------------------------------------------------------------------------------------- | ----------------- |
| A2-W — Battery Charger           | [Manufacturer original](https://marketing.unitree.com/article/en/A2-W/Battery_Charger.html)           | 14                |
| A2-W — Remote Control            | [Manufacturer original](https://marketing.unitree.com/article/en/A2-W/Remote_Control.html)            | 9                 |
| A2-W — User Manual               | [Manufacturer original](https://marketing.unitree.com/article/en/A2-W/User_Manual.html)               | 28                |
| A2 — Battery Charger             | [Manufacturer original](https://marketing.unitree.com/article/en/A2/Battery_Charger.html)             | 15                |
| A2 — Companion Remote Control    | [Manufacturer original](https://marketing.unitree.com/article/en/A2/Companion_Remote_Control.html)    | 7                 |
| A2 — Remote Control              | [Manufacturer original](https://marketing.unitree.com/article/en/A2/Remote_Control.html)              | 9                 |
| A2 — User Manual                 | [Manufacturer original](https://marketing.unitree.com/article/en/A2/User_Manual.html)                 | 28                |
| As2-W — Battery Charger          | [Manufacturer original](https://marketing.unitree.com/article/en/As2-W/Battery_Charger.html)          | 11                |
| As2-W — Companion Remote Control | [Manufacturer original](https://marketing.unitree.com/article/en/As2-W/Companion_Remote_Control.html) | 7                 |
| As2-W — Remote Control           | [Manufacturer original](https://marketing.unitree.com/article/en/As2-W/Remote_Control.html)           | 9                 |
| As2-W — User Manual              | [Manufacturer original](https://marketing.unitree.com/article/en/As2-W/User_Manual.html)              | 37                |
| As2 — Battery Charger            | [Manufacturer original](https://marketing.unitree.com/article/en/As2/Battery_Charger.html)            | 11                |
| As2 — Companion Remote Control   | [Manufacturer original](https://marketing.unitree.com/article/en/As2/Companion_Remote_Control.html)   | 7                 |
| As2 — Remote Control             | [Manufacturer original](https://marketing.unitree.com/article/en/As2/Remote_Control.html)             | 9                 |
| As2 — User Manual                | [Manufacturer original](https://marketing.unitree.com/article/en/As2/User_Manual.html)                | 38                |
| B2-W — Remote Control            | [Manufacturer original](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)            | 14                |
| B2-W — User Manual               | [Manufacturer original](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)               | 23                |
| B2 — Battery Charger             | [Manufacturer original](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)             | 14                |
| B2 — Remote Control              | [Manufacturer original](https://marketing.unitree.com/article/en/B2/Remote_Control.html)              | 14                |
| B2 — User Manual                 | [Manufacturer original](https://marketing.unitree.com/article/en/B2/User_Manual.html)                 | 23                |
| G1 — Battery Charger             | [Manufacturer original](https://marketing.unitree.com/article/en/G1/Battery_Charger.html)             | 9                 |
| G1 — Lumbar fasteners            | [Manufacturer original](https://marketing.unitree.com/article/en/G1/Lumbar_fasteners.html)            | 6                 |
| G1 — Remote Control              | [Manufacturer original](https://marketing.unitree.com/article/en/G1/Remote_Control.html)              | 10                |
| G1 — User Manual                 | [Manufacturer original](https://marketing.unitree.com/article/en/G1/User_Manual.html)                 | 31                |
| Go2-W — User Manual              | [Manufacturer original](https://marketing.unitree.com/article/en/Go2-W/User_Manual.html)              | 16                |
| Go2 — Battery Charger            | [Manufacturer original](https://marketing.unitree.com/article/en/Go2/Battery_Charger.html)            | 10                |
| Go2 — Companion Remote Control   | [Manufacturer original](https://marketing.unitree.com/article/en/Go2/Companion_Remote_Control.html)   | 6                 |
| Go2 — Handheld Remote Control    | [Manufacturer original](https://marketing.unitree.com/article/en/Go2/Handheld_Remote_Control.html)    | 16                |
| Go2 — User Manual                | [Manufacturer original](https://marketing.unitree.com/article/en/Go2/User_Manual.html)                | 17                |
| H1-2 — Remote Control            | [Manufacturer original](https://marketing.unitree.com/article/en/H1-2/Remote_Control.html)            | 16                |
| H1-2 — User Manual               | [Manufacturer original](https://marketing.unitree.com/article/en/H1-2/User_Manual.html)               | 23                |
| H1 — Battery Charger             | [Manufacturer original](https://marketing.unitree.com/article/en/H1/Battery_Charger.html)             | 9                 |
| H1 — Remote Control              | [Manufacturer original](https://marketing.unitree.com/article/en/H1/Remote_Control.html)              | 17                |
| H1 — User Manual                 | [Manufacturer original](https://marketing.unitree.com/article/en/H1/User_Manual.html)                 | 26                |
| H2 — Battery Charger             | [Manufacturer original](https://marketing.unitree.com/article/en/H2/Battery_Charger.html)             | 11                |
| H2 — Remote Control              | [Manufacturer original](https://marketing.unitree.com/article/en/H2/Remote_Control.html)              | 10                |
| H2 — User Manual                 | [Manufacturer original](https://marketing.unitree.com/article/en/H2/User_Manual.html)                 | 39                |
| R1 — Battery Charger             | [Manufacturer original](https://marketing.unitree.com/article/en/R1/Battery_Charger.html)             | 10                |
| R1 — Remote Control              | [Manufacturer original](https://marketing.unitree.com/article/en/R1/Remote_Control.html)              | 11                |
| R1 — User Manual                 | [Manufacturer original](https://marketing.unitree.com/article/en/R1/User_Manual.html)                 | 40                |
| R1\_A5A7 — User Manual           | [Manufacturer original](https://marketing.unitree.com/article/en/R1_A5A7/User_Manual.html)            | 32                |

## Model-specific protocol and development references <a href="#model-specific-protocol-and-development-references" id="model-specific-protocol-and-development-references"></a>

Use the model guide for power, battery, connector, joint and startup requirements; use SDK2/ROS 2 references for pinned message contracts and subscriber-first checks. GO and HG schemas differ, and a message array's capacity is not the robot's active joint count. Motion, ownership release, calibration and firmware replacement need their own model-specific prerequisites and recovery evidence.

The existing [L2 protocol and development reference](unitree-l2-4d-lidar-engineering-guide.md) remains the canonical guide for that LiDAR. Its store-link gap is retained; no replacement product URL or package contents are inferred from another sensor. The [GO-M8010-6 manual](unitree-go-m8010-6-motor-user-manual.md) covers its separate motor scope.

[Explore Robotics documentation](../robotics-wiki-home-page.md) · [OpenELAB Wiki home](../../)
