---
description: >-
  Three model-specific Magician curriculum pathways with published technical
  manuals and source-grounded lesson modules.
---

# DOBOT Magician Series — Education and Project Wiki

{% hint style="info" %}
[**Magician Lite on OpenELAB**](https://openelab.io/products/dobot-magician-lite-education-robot) · [**Magician on OpenELAB**](https://openelab.io/products/dobot-magician-education-robot-arm) · [**Magician E6 with ES01 on OpenELAB**](https://openelab.io/products/dobot-e6-es01-suction-robot)

**Family scope:** Magician Lite `DOBOT-1100000080` · Magician Basic `DOBOT-1100000015` (other edition SKU to verify) · Magician E6 + ES01 `DOBOT-1100000203`
{% endhint %}

### Product overview

This is an **education and application wiki library**, not a shared hardware manual. It organizes three different DOBOT robot models and the instructional resources from the Google Drive curriculum collections supplied by OpenELAB. All course text is rewritten as navigable wiki lessons; technical procedures are limited to the **correct robot/edition** and manufacturer documentation.

**Source curriculum collections:** [Magician](https://drive.google.com/drive/folders/1tMVXzLlg4TA0lM3DdBTyADu23M_lT2B2), [Magician Lite](https://drive.google.com/drive/folders/1QJum_vr-DhQR9ajhXQjlLQy6YOWlKVru), [Magician E6](https://drive.google.com/drive/folders/13zElGtZdOEx3DKASLOX_EAoy3tW4A0YU).

Magician and Magician Lite both have **four axes**, but use different arm dimensions, kits and physical interfaces. **Magician E6 is a six-axis robot**, has Ethernet and DobotStudio Pro workflows, and the linked OpenELAB bundle includes the **ES01 electric suction cup**. E6 training material must not be copied as Magician/Lite wiring or motion commands.

### Applications

* **Magician Lite:** introductory robot movement, Blockly/Scratch logic, Magic Box communication, optional sensor and AI classroom scenarios.
* **Magician:** joint/Cartesian motion, repeatability, teach-and-playback, palletizing, robotics handshaking, sensor-based sorting and work-cell design.
* **Magician E6:** six-axis setup, user/tool frames, script jobs, conditional logic, industrial digital I/O, external handshaking and ES01 pick-and-place.
* **Cross-model teaching:** compare concepts such as coordinates, loop logic, input interlocks and measurement without reusing another model's motion program verbatim.

### Specifications

| Parameter                | Magician Lite                                            | Magician (Basic Plan)                                              | Magician E6 with ES01                                              |
| ------------------------ | -------------------------------------------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------ |
| DoF                      | 4                                                        | 4                                                                  | 6                                                                  |
| Max / rated payload      | 250 g max                                                | 500 g max                                                          | 750 g rated                                                        |
| Listed reach             | 340 mm                                                   | 320 mm                                                             | 450 mm                                                             |
| Repeatability            | ±0.2 mm                                                  | ±0.2 mm                                                            | ±0.1 mm                                                            |
| Robot supply             | 12 VDC, 5 A                                              | 12 VDC, 7 A                                                        | Rated 48 VDC, 5 A                                                  |
| Main development/control | DobotLab / USB                                           | DobotLab/DobotStudio / USB                                         | DobotStudio Pro / Ethernet                                         |
| Tool/kit supplied        | Confirm order; optional sensors and tools not guaranteed | Basic includes vacuum, gripper, writing/drawing and 3D-print tools | **ES01 electric suction cup included; servo gripper not included** |

**Sources:** respective verified [Lite](https://openelab.io/products/dobot-magician-lite-education-robot), [Magician](https://openelab.io/products/dobot-magician-education-robot-arm) and [E6 ES01](https://openelab.io/products/dobot-e6-es01-suction-robot) retail specifications. Payload and repeatability do not guarantee a particular exercise's task success.

### Hardware and connections

1. Read the **exact model** on the robot label and identify the end effector before connecting power.
2. Use only that model's original power supply; never substitute 12 V or 48 V based on the same _Magician_ family name.
3. Connect optional sensors, Magic Box, mini conveyor, sliding rail, controller I/O or ES01 **only when included/compatible**, using the relevant matching manual.
4. Establish operator stop access and a clear reach envelope before homing, jogging or executing a recorded path.
5. Keep laser/printing, electrical I/O, grippers and classroom face-camera examples out of the first robot-motion test until their extra tooling and safety prerequisites are satisfied.

### Software and development resources

| Curriculum                 | Source volume / structure                                                    | Official cross-check                                                                                                      |
| -------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Magician V3.2 (2024)       | 4 instruction chapters + printable resources, T\&P and DobotBlock lessons    | [Magician User Guide](../dobot-magician-user-guide.md)                                                                    |
| Magician Lite V1.1 (2024)  | 4 instruction chapters + printable resources                                 | [Lite User Guide](../dobot-magician-lite-user-guide.md)                                                                   |
| Lite Scratch/Blockly       | 6 chapters, interactive simulation/sensing and projects                      | [Lite source folder](https://drive.google.com/drive/folders/1haMkYBwCE40tZNBHkfLBHiopzD5l6-71)                            |
| Lite AI at Your Fingertips | AI Campus, AI Farm, AI Mall illustrated experiments                          | [Lite AI source folder](https://drive.google.com/drive/folders/1HduKhJvc59GwWua4ATOMgG59Dp18UcIo)                         |
| Magician E6 course         | **15 module folders**, lesson plans, video transcripts, work-cell STL assets | [E6 source folder](https://drive.google.com/drive/folders/1B5_ovBSMTY1UW88Ah8mFgQqLuG9wgeyO)                              |
| E6/ES01 technical docs     | installation, network, I/O, hardware constraints                             | [E6 User Guide](../dobot-magician-e6-user-guide.md) · [ES01 User Guide](../dobot-es01-electric-suction-cup-user-guide.md) |

### Getting started

#### First working result: select the right course and verify the robot

1. Identify the robot label: **Lite**, **Magician**, or **E6**; photograph (without posting serials) and note exact SKU/edition.
2. Compare actual included equipment against the table above. **Do not assume** that a workbook's Sensor Kit, Magic Box, AI Camera or suction/gripper is included.
3. For Lite/Magician, follow the model's user guide to connect by USB, open the supported **DobotLab/DobotStudio** version and enter Teaching & Playback. Inspect connection status/COM before homing.
4. For E6, the Module 1 lesson plan uses **Windows 10/11, DobotStudio Pro, LAN2 default 192.168.200.1** with a PC address in the 192.168.200.0/24 subnet. Verify actual firmware/network settings and emergency-stop wiring before connecting; inspect robot status **without motion**.
5. Record a **first-result evidence sheet**: model, firmware, OS, software version, connection type, detected status, installed tool, stop procedure and source document revision.

**Expected result:** an accurately identified robot and software connection, with no automatic movement. If connection fails, check the correct power supply, cable, COM/Ethernet adapter, installed driver, selected model, network segment and stop state **in that order**.

### Choose a model-specific learning path

| Robot                     | Curriculum and scope                                                                                                      | Direct guide                                                              |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| **Magician Lite**         | Four-axis K–12/introductory robot, DobotLab, 4 workbook chapters + Scratch and AI Campus/Farm/Mall exercises              | [Magician Lite curriculum guide](magician-lite-curriculum-project-guide/) |
| **Magician**              | Four-axis desktop robot, 4 V3.2 curriculum chapters including palletization, handshaking, sensors and complete work cells | [Magician curriculum guide](magician-curriculum-project-guide/)           |
| **Magician E6 with ES01** | Six-axis robot, Ethernet/DobotStudio Pro, **15 original curriculum modules**, suction rather than mechanical jaw gripper  | [Magician E6 curriculum guide](magician-e6-es01-curriculum-guide/)        |

**Teaching sequence:** choose and verify the correct SKU → read its model manual → complete a no-motion setup checkpoint → study relevant lessons → test optional tools and I/O only after their own documentation is verified. The downloadable source curricula are linked in each guide.

### Troubleshooting and FAQs

**Can E6 sample scripts run on four-axis Magician/Lite?** Not without a model-specific rewrite and verification. Their control transport, joint structure, motion limits and tooling are different.

**Does the E6 + ES01 bundle include the separate servo gripper featured in some module lessons?** **No.** The delivered bundle includes ES01; any mechanical gripping exercise requires another compatible purchased tool.

**Why do Lite workbook lessons mention Magic Box/AI Camera when my box only has the arm?** Those chapters are **optional accessory-dependent**. Check your ordered bundle.

**Can Magician Educational Plan lessons assume Basic Plan parts?** The Educational Plan adds wireless, laser and joystick modules to the Basic Plan tools. Check the exact purchased edition; optional laser instruction needs separate controlled safety precautions.

### Downloads and technical documents

* [Magician Lite V1.1 curriculum PDF](https://drive.google.com/file/d/1QIVA1S21EIHV1TOdHESgUXxE8Xso_kcP/view).
* [Magician V3.2 curriculum PDF](https://drive.google.com/file/d/1wfgDZ2CETKxll6oDhMkfIFI5Yn5p03-9/view).
* [Magician E6 15-module source collection](https://drive.google.com/drive/folders/1B5_ovBSMTY1UW88Ah8mFgQqLuG9wgeyO).
* [Magician Lite official-style user guide](../dobot-magician-lite-user-guide.md) · [Magician user guide](../dobot-magician-user-guide.md) · [E6 user guide](../dobot-magician-e6-user-guide.md) · [ES01 guide](../dobot-es01-electric-suction-cup-user-guide.md).

### References and validation

* DOBOT-linked Magician curriculum, **V3.2 2024**, attributed to Chris & Jim CIM, inspected 2026-11-21.
* DOBOT-linked Magician Lite curriculum, **V1.1 2024**, attributed to Chris & Jim CIM, inspected 2026-11-21.
* DOBOT Magician Lite Scratch and _AI at Your Fingertips_ Google Drive curriculum files, inspected 2026-11-21.
* DOBOT Magician E6 instructional collection of **15 modules** with lesson plans/video transcripts and STL resources, inspected 2026-11-21.
* OpenELAB exact product pages and the previously published matching manuals, checked 2026-11-21.

**Documentation:** organized and source-reviewed for draft. **Software execution:** not run. **Hardware validation:** not run. Classroom worksheet and video-based instructions may refer to older interfaces: verify the current installed software and physical equipment before applying any motion, I/O wiring or tool changes.
