---
description: >-
  Model-specific DOBOT curriculum entry and connected educational project
  navigation.
---

# Magician E6 + ES01 — Curriculum and Programming Guide

{% hint style="info" %}
[**View DOBOT Magician E6 with ES01 Electric Suction Cup on OpenELAB**](https://openelab.io/products/dobot-e6-es01-suction-robot)

**Robot:** Magician E6 six-axis · **OpenELAB SKU:** `DOBOT-1100000203` · **Bundle:** E6 + ES01 electric suction cup; **servo gripper not included**
{% endhint %}

[Magician Series index](../) · [Existing E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md) · [Existing ES01 User Guide](../../dobot-es01-electric-suction-cup-user-guide.md)

### Product overview

The Magician E6 is a **six-axis desktop collaborative arm** controlled through **DobotStudio Pro**. The selected OpenELAB bundle includes the **ES01 electric suction cup** for pick-and-place. This education guide follows the **fifteen DOBOT Magician E6 curriculum modules** in the user-supplied Google Drive folder, from installation and coordinates through programming, digital I/O, tool/user frames, pick-and-place, offsets and external communications.

The 15 modules include lesson plans, transcripts/videos and some auxiliary **STL objects and example code**. In several lessons, a **mechanical gripper or pointer** is shown; the selected E6+ES01 retail bundle **does not include a servo gripper**. Read the correct end-effector manual before attempting that exercise.

### Applications

* First-time E6 controller, network and programming environment setup.
* Jogging in joint and Cartesian frames; record points and build simple safe script jobs.
* Lua-style reusable functions, variables, loops and program flow.
* Digital I/O, tool-center-point (TCP), user frames and external PLC handshaking.
* Controlled ES01 vacuum pick/place and classroom palletization under supervision.

### Specifications

| Parameter          | Verified E6 model scope                                         |
| ------------------ | --------------------------------------------------------------- |
| Axes               | **6**                                                           |
| Payload            | **750 g rated**, including tool/workpiece loading as prescribed |
| Reach              | **450 mm**                                                      |
| Repeatability      | **±0.1 mm**                                                     |
| TCP speed          | Up to **0.5 m/s** (not an initial teaching speed)               |
| Input              | 100–240 VAC input, rated 48 VDC / 5 A to robot; power **130 W** |
| Communications     | Two Ethernet ports; TCP/IP and Modbus TCP listed                |
| Ingress protection | **IP20**; indoor desktop use                                    |
| Included end tool  | **ES01 electric suction cup**                                   |
| Not included       | Servo gripper; separate accessory if used in course             |

Source: [E6+ES01 OpenELAB product listing](https://openelab.io/products/dobot-e6-es01-suction-robot) and [DOBOT E6 user guide V1.4](../../dobot-magician-e6-user-guide.md). Do not assume a 4-axis Magician teaching program, supply or USB protocol applies.

### Hardware and connections

1. Identify the E6 **model, controller software version and installed ES01 tool**. Secure the arm to a suitable desk/mount per E6 V1.4; clear its 450 mm work radius and potential tool movement.
2. Connect the manufacturer E-stop exactly as documented before powering the robot. Verify stop/release behavior under a qualified operator, not by guessing button combinations.
3. Follow the E6 V1.4 diagram to attach original power; the curriculum **Module 1** uses **LAN2** with documented default **192.168.200.1**, PC **192.168.200.x/24** where x is not 1. Verify actual controller network settings before changing host IP.
4. Configure only the **ES01** according to the ES01 manual. Do not follow the course's mechanical-servo-gripper fastening/port steps on a suction-cup-only kit.
5. **Do not** set TCP/payload values or I/O port assignments by copying instructor examples. The lesson's 65 mm TCP and 250 g payload were task fixtures, **not universal defaults**.
6. Start with read-only connection and status checks, then teach simple moves at instructor-approved reduced speed.

### Software and development resources

| Resource                                                                                                        | Application                                                  |
| --------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| [E6 full 15-module curriculum folder](https://drive.google.com/drive/folders/1B5_ovBSMTY1UW88Ah8mFgQqLuG9wgeyO) | Lesson plans, videos, transcripts and STL                    |
| [E6 Module 1 — Initial Setup](https://drive.google.com/drive/folders/1-IEk7KTS_nbOnBq70IESlnrG0K-u1mVc)         | DobotStudio Pro, E-stop, LAN2 and software update            |
| [E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md)                                                     | Safety, connectors, spec and mounting                        |
| [ES01 Electric Suction Cup User Guide](../../dobot-es01-electric-suction-cup-user-guide.md)                     | Accessory installation, Tool I/O, control and suction limits |
| [E6 Source Resources](https://drive.google.com/drive/folders/12-JyS10mO2AxbRuayykoV7z4FnmUl_I8)                 | Printed box/circle/triangle gasket and STL practice models   |

### Getting started

#### First working result — connect DobotStudio Pro without motion

1. On a **Windows 10/11** host, install a version of **DobotStudio Pro** supported by the delivered E6 firmware (from DOBOT official Download Center).
2. Connect the E-stop and original power according to E6 V1.4. Connect Ethernet to **LAN2** and computer/adapter, and keep the arm envelope clear.
3. Set a free host IPv4 address on **192.168.200.0/24**, for example **192.168.200.100/255.255.255.0**, **only if the actual LAN2 default remains 192.168.200.1**.
4. Check from Command Prompt:

```bat
ping 192.168.200.1
```

5. Open **DobotStudio Pro → Add Manually → 192.168.200.1 → Confirm → Connect**, then inspect robot software and controller versions at the bottom-right of the interface as the Module 1 assignment asks.

**Expected result:** E6 detected and connected with version information displayed. No joint motion or firmware update is needed. If ping fails, check Ethernet adapter, LAN2 port, E-stop power/connector status, host subnet and actual controller IP. Do not randomly flash firmware or change LAN1 network values to fix a host issue.

**Firmware update:** Module 1 also describes the **Dobot Robot Maintenance Tool**. Perform an upgrade only for a documented compatibility need and manufacturer-supported package; do not upgrade simply because an example screenshot shows a different revision.

### Magician E6 curriculum navigation — 15 modules

The modules follow the original lesson-plan folders. **Modules 1–3** establish setup and status; **4–7** cover tool and motion basics; **8–12** cover programming and frames; **13–15** build integration examples. Use the E6/ES01 manuals before actual movement, wiring or tool calibration.

* [Module 01 · Initial Setup](e6-module-01-initial-setup.md)
* [Module 02 · Settings and TCP](e6-module-02-settings.md)
* [Module 03 · DobotStudio Interface](e6-module-03-studio-interface.md)
* [Module 04 · Tool Setup and I/O](e6-module-04-tool-io.md)
* [Module 05 · Cartesian Coordinates](e6-module-05-cartesian-coordinates.md)
* [Module 06 · Jobs and Park Routine](e6-module-06-programming-basics.md)
* [Module 07 · First Box Job](e6-module-07-first-job.md)
* [Module 08 · Motion Parameters/Variables](e6-module-08-parameters-variables.md)
* [Module 09 · Functions/Shapes](e6-module-09-functions.md)
* [Module 10 · Digital and Group I/O](e6-module-10-digital-io.md)
* [Module 11 · Conditional Logic](e6-module-11-logic.md)
* [Module 12 · Frames and TCP](e6-module-12-frames.md)
* [Module 13 · ES01 Pick-and-Place](e6-module-13-pick-place-es01.md)
* [Module 14 · Offsets/Nested Loops](e6-module-14-offsets-nested-loops.md)
* [Module 15 · Timers and PLC Communication](e6-module-15-external-communication.md)

**ES01 compatibility:** the included suction cup differs from the mechanical/servo gripper shown in some videos. Use the [ES01 manual](../../dobot-es01-electric-suction-cup-user-guide.md) for correct mounting, Tool I/O and load limits.

### Troubleshooting and FAQs

**Can I follow the mechanical gripper lesson with the included ES01?** The E6+ES01 listing does not include the servo gripper. Follow the **ES01** Tool I/O and suction manual instead of assuming its commands match a jaw gripper.

**The robot is found on Ethernet but a program cannot start:** check current alarms, safety/enable state, user/tool frame and controller version before motion; never bypass an E-stop.

**What about Module 15 PLC I/O wiring?** Do not connect wires based only on lesson-plan example pin numbers. Use E6 V1.4's exact I/O diagram, voltage, reference ground and supervision; start with software-only truth-table simulation.

### Downloads and technical documents

* [E6 V1.4 User Guide](../../dobot-magician-e6-user-guide.md) · [ES01 V1.0 User Guide](../../dobot-es01-electric-suction-cup-user-guide.md).
* [E6 curriculum lesson resources](https://drive.google.com/drive/folders/1B5_ovBSMTY1UW88Ah8mFgQqLuG9wgeyO).
* [Source E6 Module 1 lesson plan](https://docs.google.com/document/d/1uIZBkPoGTGHeC2g6Wiz09iCqvku5PbJf/edit).
* [ES01 retail bundle](https://openelab.io/products/dobot-e6-es01-suction-robot).

### References and validation

* DOBOT Magician E6 **15-module lesson plan collection**, supplied Google Drive curriculum library (2024 source assets), reviewed 2026-11-21.
* [E6 V1.4 hardware user guide](../../dobot-magician-e6-user-guide.md), 2024; [ES01 V1.0 accessory guide](../../dobot-es01-electric-suction-cup-user-guide.md), 2024.
* [OpenELAB E6+ES01 listing](https://openelab.io/products/dobot-e6-es01-suction-robot), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software:** not run. **Hardware:** not tested. Per-module procedures distinguish recorded classroom activities from validated instrument settings, exact firmware and actual end-effector configuration.
