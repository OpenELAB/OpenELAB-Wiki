---
description: >-
  E6 module 7: First Job: Box Points and MoveJ/MoveL. DOBOT curriculum lesson
  plan, equipment scope, first working result and safety checks.
---

# Magician E6 — Module 07: First Job: Box Points and MoveJ/MoveL

{% hint style="info" %}
[**View DOBOT Magician E6 with ES01 on OpenELAB**](https://openelab.io/products/dobot-e6-es01-suction-robot)

**Robot:** Magician E6 (6 axes) · **SKU:** `DOBOT-1100000203` · **Delivered tool:** ES01 electric suction cup · **Servo gripper:** not included
{% endhint %}

[E6 curriculum guide](./) · [Magician Series index](../) · [Existing E6 user guide](../../dobot-magician-e6-user-guide.md)

### Product overview

**Module 7 — First Job: Box Points and MoveJ/MoveL.** This tutorial follows the matching instructor lesson plan and videos in the user-provided **15-module Magician E6 curriculum**. It converts the classroom sequence into a model-specific engineering learning checkpoint for the **six-axis E6 with ES01**, distinguishing source demonstrations from physical actions that still require real-device checks.

### Applications

* Duplicate Park job into a Box job
* Record and name approach/exit/box points in the Points table
* Differentiate MoveJ, MoveL, motion speed and continuous-path behavior

### Specifications

| Parameter              | Value / conditions                                                                                                            |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| Robot                  | Magician E6, six-axis, **750 g** rated payload, **450 mm** reach, **±0.1 mm** repeatability                                   |
| Electrical / transport | Manufacturer E6 original 48 VDC/5 A rated supply; Ethernet controller, two ports                                              |
| Software               | **DobotStudio Pro** with matching firmware; Lua Script Programming where applicable                                           |
| Included end effector  | **ES01 suction cup** only; separate servo gripper is not included in this SKU                                                 |
| Lesson prerequisite    | E6 in supervised training cell, marked box worksheet and safe pointer (if supplied); ES01 alone is a suction tool, not a pen. |
| Source lesson          | [Module 7 lesson plan](https://docs.google.com/document/d/1KWB-QYvPFrUbAOgkMiWGzfelal4xc6s0/edit)                             |

These are model-level ratings, not validated training task accuracy or safe contact forces.

### Hardware and connections

1. Verify the purchased **E6 with ES01** configuration, manufacturer E-stop, model/software revision and safe work envelope before connecting or actuating anything.
2. E6 in supervised training cell, marked box worksheet and safe pointer (if supplied); ES01 alone is a suction tool, not a pen.
3. Follow [the E6 user guide](../../dobot-magician-e6-user-guide.md) and [ES01 manual](../../dobot-es01-electric-suction-cup-user-guide.md) for exact tool electrical limits, mounting and operating states. Do not use a Magician Lite/4-axis Magician power supply or guessed I/O pinout.
4. Treat any change to TCP, payload, host network, robot I/O or motion limits as a controlled engineering configuration change. Record original settings and supervisor authorization.
5. Do not execute automatic trajectories or physical handling until all required calibration, obstacle checks and physical stop tests have succeeded.

### Software and development resources

* [Original Module 7 folder](https://drive.google.com/drive/folders/1gy6XCb1uVUOVikvU-mkbIWTMSpYq2Suj) — instructional plan plus associated transcripts, video demonstrations and, for some modules, example code.
* [Module 7 lesson plan](https://docs.google.com/document/d/1KWB-QYvPFrUbAOgkMiWGzfelal4xc6s0/edit) — specific classroom objectives and activities.
* [E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md) — model-specific mechanical/electrical safety.
* [ES01 User Guide](../../dobot-es01-electric-suction-cup-user-guide.md) — installed electric suction-cup hardware and Tool I/O.
* **Source-to-hardware boundary:** The source includes a **Box Circle Triangle Gasket** printed worksheet and 3D-printed pointer. The E6+ES01 bundle does **not** guarantee that pointer or mechanical gripper. For drawing a box, use only an installed and calibrated compatible pointer/fixture.

### Getting started

#### Prerequisites

Confirm that the E6 is the correctly identified six-axis model and that the actual included or additional tools required for this exercise are available. Start with the safe, read-only or offline checkpoint below.

#### First working result

1. Open Script Programming, **Save As → Box** from the existing Park job. In the **Points** tab, record and label a safe **Approach Exit** above the worksheet without contact; add two further above-field points using instructor-approved reduced jog settings, then save. Compare command types in the Help view but do not execute an unverified sequence.
2. Record the actual input conditions, selected user/tool frame, software and firmware versions (where relevant) and any discrepancy.
3. Compare the result with the expected criterion and **stop before** adding physical motion or wiring that has not been verified.

**Expected result:** A Box job containing three labeled approach points and no contact/motion-loop execution.

#### Extension and student assessment

When the first check succeeds, follow the module's source lesson for additional, instructor-supervised tasks while preserving hardware safety and correct tool model. **Deliverable:** Point table, workspace diagram and a written rationale for selecting MoveJ vs MoveL. Distinguish theoretical values, user-entered examples and measured robot values.

### Troubleshooting and FAQs

**What should I check if the lesson does not match the robot?** If a taught path approaches the table, stop, review frame/tool offset and Z clearance; the original worksheet coordinates are not safe universal setpoints.

**Are all source example settings safe for my E6?** No. The source includes a **Box Circle Triangle Gasket** printed worksheet and 3D-printed pointer. The E6+ES01 bundle does **not** guarantee that pointer or mechanical gripper. For drawing a box, use only an installed and calibrated compatible pointer/fixture.

**Does the course include the gripper shown in every video?** No. The selected E6 + ES01 product includes suction tool only; consult the relevant separate mechanical gripper manual for any jaw-gripper workflow.

### Downloads and technical documents

| Resource                                                                                           | Purpose                                              |
| -------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| [Module 7 source folder](https://drive.google.com/drive/folders/1gy6XCb1uVUOVikvU-mkbIWTMSpYq2Suj) | Videos, transcript(s), lesson plan and module assets |
| [Module 7 lesson plan](https://docs.google.com/document/d/1KWB-QYvPFrUbAOgkMiWGzfelal4xc6s0/edit)  | Original educational objectives and assessment       |
| [E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md)                                        | Robot power, work envelope, I/O and installation     |
| [ES01 User Guide V1.0](../../dobot-es01-electric-suction-cup-user-guide.md)                        | Correct tool setup and control                       |
| [Exact ES01 bundle](https://openelab.io/products/dobot-e6-es01-suction-robot)                      | Product and included tool scope                      |

### References and validation

* [Source Magician E6 Module 7 folder](https://drive.google.com/drive/folders/1gy6XCb1uVUOVikvU-mkbIWTMSpYq2Suj) and [lesson plan](https://docs.google.com/document/d/1KWB-QYvPFrUbAOgkMiWGzfelal4xc6s0/edit), retrieved from user-provided Google Drive curriculum 2026-11-21.
* [Existing E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md) and [ES01 V1.0 manual](../../dobot-es01-electric-suction-cup-user-guide.md), manufacturer-authorized instructions reviewed 2026-11-21.
* [OpenELAB verified E6 + ES01 retail product](https://openelab.io/products/dobot-e6-es01-suction-robot), checked 2026-11-21.

**Documentation:** reviewed and organized as a curriculum draft. **Software execution:** not run. **Hardware validation:** not run. Do not interpret a sample exercise value, a video screenshot or an offline logic result as a verified robot controller setting or certification.
