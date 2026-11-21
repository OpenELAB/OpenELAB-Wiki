---
description: >-
  E6 module 1: Initial Setup, E-Stop, Ethernet and Firmware. DOBOT curriculum
  lesson plan, equipment scope, first working result and safety checks.
---

# Magician E6 — Module 01: Initial Setup, E-Stop, Ethernet and Firmware

{% hint style="info" %}
[**View DOBOT Magician E6 with ES01 on OpenELAB**](https://openelab.io/products/dobot-e6-es01-suction-robot)

**Robot:** Magician E6 (6 axes) · **SKU:** `DOBOT-1100000203` · **Delivered tool:** ES01 electric suction cup · **Servo gripper:** not included
{% endhint %}

[E6 curriculum guide](./) · [Magician Series index](../) · [Existing E6 user guide](../../dobot-magician-e6-user-guide.md)

### Product overview

**Module 1 — Initial Setup, E-Stop, Ethernet and Firmware.** This tutorial follows the matching instructor lesson plan and videos in the user-provided **15-module Magician E6 curriculum**. It converts the classroom sequence into a model-specific engineering learning checkpoint for the **six-axis E6 with ES01**, distinguishing source demonstrations from physical actions that still require real-device checks.

### Applications

* Install a controller-matched DobotStudio Pro on Windows 10/11
* Identify E-stop, power, LAN1/LAN2 and verify Ethernet
* Use actual LAN2 network setting and record firmware/Studio versions

### Specifications

| Parameter              | Value / conditions                                                                                          |
| ---------------------- | ----------------------------------------------------------------------------------------------------------- |
| Robot                  | Magician E6, six-axis, **750 g** rated payload, **450 mm** reach, **±0.1 mm** repeatability                 |
| Electrical / transport | Manufacturer E6 original 48 VDC/5 A rated supply; Ethernet controller, two ports                            |
| Software               | **DobotStudio Pro** with matching firmware; Lua Script Programming where applicable                         |
| Included end effector  | **ES01 suction cup** only; separate servo gripper is not included in this SKU                               |
| Lesson prerequisite    | E6 with ES01, original power/E-stop cable, Windows 10/11 PC, Ethernet cable and compatible DobotStudio Pro. |
| Source lesson          | [Module 1 lesson plan](https://docs.google.com/document/d/1uIZBkPoGTGHeC2g6Wiz09iCqvku5PbJf/edit)           |

These are model-level ratings, not validated training task accuracy or safe contact forces.

### Hardware and connections

1. Verify the purchased **E6 with ES01** configuration, manufacturer E-stop, model/software revision and safe work envelope before connecting or actuating anything.
2. E6 with ES01, original power/E-stop cable, Windows 10/11 PC, Ethernet cable and compatible DobotStudio Pro.
3. Follow [the E6 user guide](../../dobot-magician-e6-user-guide.md) and [ES01 manual](../../dobot-es01-electric-suction-cup-user-guide.md) for exact tool electrical limits, mounting and operating states. Do not use a Magician Lite/4-axis Magician power supply or guessed I/O pinout.
4. Treat any change to TCP, payload, host network, robot I/O or motion limits as a controlled engineering configuration change. Record original settings and supervisor authorization.
5. Do not execute automatic trajectories or physical handling until all required calibration, obstacle checks and physical stop tests have succeeded.

### Software and development resources

* [Original Module 1 folder](https://drive.google.com/drive/folders/1-IEk7KTS_nbOnBq70IESlnrG0K-u1mVc) — instructional plan plus associated transcripts, video demonstrations and, for some modules, example code.
* [Module 1 lesson plan](https://docs.google.com/document/d/1uIZBkPoGTGHeC2g6Wiz09iCqvku5PbJf/edit) — specific classroom objectives and activities.
* [E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md) — model-specific mechanical/electrical safety.
* [ES01 User Guide](../../dobot-es01-electric-suction-cup-user-guide.md) — installed electric suction-cup hardware and Tool I/O.
* **Source-to-hardware boundary:** The source Module 1 states LAN2 default 192.168.200.1 and LAN1 default 192.168.5.1; the LAN2 connection should be checked on the actual firmware before using these addresses. It names Dobot Robot Maintenance Tool but an upgrade is not necessary unless compatibility requires it.

### Getting started

#### Prerequisites

Confirm that the E6 is the correctly identified six-axis model and that the actual included or additional tools required for this exercise are available. Start with the safe, read-only or offline checkpoint below.

#### First working result

1. With the E6 **stationary**, check correct E-stop wiring and LAN2 cable using the E6 V1.4 guide. Set a nonconflicting PC IPv4 such as 192.168.200.100/24 only if the real robot has default LAN2 192.168.200.1; run `ping 192.168.200.1` in Windows Command Prompt. In DobotStudio Pro use **Add Manually → 192.168.200.1 → Connect** and inspect the software/controller versions.
2. Record the actual input conditions, selected user/tool frame, software and firmware versions (where relevant) and any discrepancy.
3. Compare the result with the expected criterion and **stop before** adding physical motion or wiring that has not been verified.

**Expected result:** A visible connected robot and software/controller version fields, not a firmware upgrade or motor motion.

#### Extension and student assessment

When the first check succeeds, follow the module's source lesson for additional, instructor-supervised tasks while preserving hardware safety and correct tool model. **Deliverable:** Screenshot of connected version/status and a labeled network diagram. Distinguish theoretical values, user-entered examples and measured robot values.

### Troubleshooting and FAQs

**What should I check if the lesson does not match the robot?** If no reply, inspect actual robot LAN2 address, PC adapter subnet, cable, power and E-stop rather than flashing firmware or changing arbitrary IPs.

**Are all source example settings safe for my E6?** No. The source Module 1 states LAN2 default 192.168.200.1 and LAN1 default 192.168.5.1; the LAN2 connection should be checked on the actual firmware before using these addresses. It names Dobot Robot Maintenance Tool but an upgrade is not necessary unless compatibility requires it.

**Does the course include the gripper shown in every video?** No. The selected E6 + ES01 product includes suction tool only; consult the relevant separate mechanical gripper manual for any jaw-gripper workflow.

### Downloads and technical documents

| Resource                                                                                           | Purpose                                              |
| -------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| [Module 1 source folder](https://drive.google.com/drive/folders/1-IEk7KTS_nbOnBq70IESlnrG0K-u1mVc) | Videos, transcript(s), lesson plan and module assets |
| [Module 1 lesson plan](https://docs.google.com/document/d/1uIZBkPoGTGHeC2g6Wiz09iCqvku5PbJf/edit)  | Original educational objectives and assessment       |
| [E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md)                                        | Robot power, work envelope, I/O and installation     |
| [ES01 User Guide V1.0](../../dobot-es01-electric-suction-cup-user-guide.md)                        | Correct tool setup and control                       |
| [Exact ES01 bundle](https://openelab.io/products/dobot-e6-es01-suction-robot)                      | Product and included tool scope                      |

### References and validation

* [Source Magician E6 Module 1 folder](https://drive.google.com/drive/folders/1-IEk7KTS_nbOnBq70IESlnrG0K-u1mVc) and [lesson plan](https://docs.google.com/document/d/1uIZBkPoGTGHeC2g6Wiz09iCqvku5PbJf/edit), retrieved from user-provided Google Drive curriculum 2026-11-21.
* [Existing E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md) and [ES01 V1.0 manual](../../dobot-es01-electric-suction-cup-user-guide.md), manufacturer-authorized instructions reviewed 2026-11-21.
* [OpenELAB verified E6 + ES01 retail product](https://openelab.io/products/dobot-e6-es01-suction-robot), checked 2026-11-21.

**Documentation:** reviewed and organized as a curriculum draft. **Software execution:** not run. **Hardware validation:** not run. Do not interpret a sample exercise value, a video screenshot or an offline logic result as a verified robot controller setting or certification.
