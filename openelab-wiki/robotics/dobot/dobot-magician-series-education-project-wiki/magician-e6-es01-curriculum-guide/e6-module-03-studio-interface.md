---
description: >-
  E6 module 3: DobotStudio Pro Interface and Robot Status. DOBOT curriculum
  lesson plan, equipment scope, first working result and safety checks.
---

# Magician E6 — Module 03: DobotStudio Pro Interface and Robot Status

{% hint style="info" %}
[**View DOBOT Magician E6 with ES01 on OpenELAB**](https://openelab.io/products/dobot-e6-es01-suction-robot)

**Robot:** Magician E6 (6 axes) · **SKU:** `DOBOT-1100000203` · **Delivered tool:** ES01 electric suction cup · **Servo gripper:** not included
{% endhint %}

[E6 curriculum guide](./) · [Magician Series index](../) · [Existing E6 user guide](../../dobot-magician-e6-user-guide.md)

### Product overview

**Module 3 — DobotStudio Pro Interface and Robot Status.** This tutorial follows the matching instructor lesson plan and videos in the user-provided **15-module Magician E6 curriculum**. It converts the classroom sequence into a model-specific engineering learning checkpoint for the **six-axis E6 with ES01**, distinguishing source demonstrations from physical actions that still require real-device checks.

### Applications

* Identify Robot, Settings, Log, Application, Jog and Monitor tabs
* Inspect alarm/status, current joint and Cartesian coordinates
* Distinguish joint moves, linear moves and the Points table

### Specifications

| Parameter              | Value / conditions                                                                                                    |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------- |
| Robot                  | Magician E6, six-axis, **750 g** rated payload, **450 mm** reach, **±0.1 mm** repeatability                           |
| Electrical / transport | Manufacturer E6 original 48 VDC/5 A rated supply; Ethernet controller, two ports                                      |
| Software               | **DobotStudio Pro** with matching firmware; Lua Script Programming where applicable                                   |
| Included end effector  | **ES01 suction cup** only; separate servo gripper is not included in this SKU                                         |
| Lesson prerequisite    | Connected and physically safe E6; no additional end tool beyond installed ES01 required for read-only UI exploration. |
| Source lesson          | [Module 3 lesson plan](https://docs.google.com/document/d/1nfn9tQZ3Rlw1tOmRswEm_SaQCBEyFxNd/edit)                     |

These are model-level ratings, not validated training task accuracy or safe contact forces.

### Hardware and connections

1. Verify the purchased **E6 with ES01** configuration, manufacturer E-stop, model/software revision and safe work envelope before connecting or actuating anything.
2. Connected and physically safe E6; no additional end tool beyond installed ES01 required for read-only UI exploration.
3. Follow [the E6 user guide](../../dobot-magician-e6-user-guide.md) and [ES01 manual](../../dobot-es01-electric-suction-cup-user-guide.md) for exact tool electrical limits, mounting and operating states. Do not use a Magician Lite/4-axis Magician power supply or guessed I/O pinout.
4. Treat any change to TCP, payload, host network, robot I/O or motion limits as a controlled engineering configuration change. Record original settings and supervisor authorization.
5. Do not execute automatic trajectories or physical handling until all required calibration, obstacle checks and physical stop tests have succeeded.

### Software and development resources

* [Original Module 3 folder](https://drive.google.com/drive/folders/1ZN3Mpv4JqIgBB5T9lVIrNH5Z1MunsPJP) — instructional plan plus associated transcripts, video demonstrations and, for some modules, example code.
* [Module 3 lesson plan](https://docs.google.com/document/d/1nfn9tQZ3Rlw1tOmRswEm_SaQCBEyFxNd/edit) — specific classroom objectives and activities.
* [E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md) — model-specific mechanical/electrical safety.
* [ES01 User Guide](../../dobot-es01-electric-suction-cup-user-guide.md) — installed electric suction-cup hardware and Tool I/O.
* **Source-to-hardware boundary:** The source lesson walks students through Robot/Settings/Log/Application/Jog/Monitor and introduces points, MoveJ and MoveL; the exact tab layout depends on DobotStudio Pro release.

### Getting started

#### Prerequisites

Confirm that the E6 is the correctly identified six-axis model and that the actual included or additional tools required for this exercise are available. Start with the safe, read-only or offline checkpoint below.

#### First working result

1. In DobotStudio Pro, locate the **Robot**, **Log**, **Jog**, **Points** and **Monitor** views; record current E6 state, controller version, joint values and Cartesian TCP values without jogging or changing settings. Use the Log view to identify current alarms (if any).
2. Record the actual input conditions, selected user/tool frame, software and firmware versions (where relevant) and any discrepancy.
3. Compare the result with the expected criterion and **stop before** adding physical motion or wiring that has not been verified.

**Expected result:** An annotated interface map and baseline robot state/position record.

#### Extension and student assessment

When the first check succeeds, follow the module's source lesson for additional, instructor-supervised tasks while preserving hardware safety and correct tool model. **Deliverable:** Screenshot with at least five labeled views and a saved status table. Distinguish theoretical values, user-entered examples and measured robot values.

### Troubleshooting and FAQs

**What should I check if the lesson does not match the robot?** If a tab has moved, use the installed software's Help and E6 documentation rather than guessing deprecated menu positions.

**Are all source example settings safe for my E6?** No. The source lesson walks students through Robot/Settings/Log/Application/Jog/Monitor and introduces points, MoveJ and MoveL; the exact tab layout depends on DobotStudio Pro release.

**Does the course include the gripper shown in every video?** No. The selected E6 + ES01 product includes suction tool only; consult the relevant separate mechanical gripper manual for any jaw-gripper workflow.

### Downloads and technical documents

| Resource                                                                                           | Purpose                                              |
| -------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| [Module 3 source folder](https://drive.google.com/drive/folders/1ZN3Mpv4JqIgBB5T9lVIrNH5Z1MunsPJP) | Videos, transcript(s), lesson plan and module assets |
| [Module 3 lesson plan](https://docs.google.com/document/d/1nfn9tQZ3Rlw1tOmRswEm_SaQCBEyFxNd/edit)  | Original educational objectives and assessment       |
| [E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md)                                        | Robot power, work envelope, I/O and installation     |
| [ES01 User Guide V1.0](../../dobot-es01-electric-suction-cup-user-guide.md)                        | Correct tool setup and control                       |
| [Exact ES01 bundle](https://openelab.io/products/dobot-e6-es01-suction-robot)                      | Product and included tool scope                      |

### References and validation

* [Source Magician E6 Module 3 folder](https://drive.google.com/drive/folders/1ZN3Mpv4JqIgBB5T9lVIrNH5Z1MunsPJP) and [lesson plan](https://docs.google.com/document/d/1nfn9tQZ3Rlw1tOmRswEm_SaQCBEyFxNd/edit), retrieved from user-provided Google Drive curriculum 2026-11-21.
* [Existing E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md) and [ES01 V1.0 manual](../../dobot-es01-electric-suction-cup-user-guide.md), manufacturer-authorized instructions reviewed 2026-11-21.
* [OpenELAB verified E6 + ES01 retail product](https://openelab.io/products/dobot-e6-es01-suction-robot), checked 2026-11-21.

**Documentation:** reviewed and organized as a curriculum draft. **Software execution:** not run. **Hardware validation:** not run. Do not interpret a sample exercise value, a video screenshot or an offline logic result as a verified robot controller setting or certification.
