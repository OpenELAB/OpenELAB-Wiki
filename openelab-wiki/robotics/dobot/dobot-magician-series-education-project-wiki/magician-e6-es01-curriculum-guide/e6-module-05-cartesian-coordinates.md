---
description: >-
  E6 module 5: Cartesian Coordinates and Coordinate Frames. DOBOT curriculum
  lesson plan, equipment scope, first working result and safety checks.
---

# Magician E6 — Module 05: Cartesian Coordinates and Coordinate Frames

{% hint style="info" %}
[**View DOBOT Magician E6 with ES01 on OpenELAB**](https://openelab.io/products/dobot-e6-es01-suction-robot)

**Robot:** Magician E6 (6 axes) · **SKU:** `DOBOT-1100000203` · **Delivered tool:** ES01 electric suction cup · **Servo gripper:** not included
{% endhint %}

[E6 curriculum guide](./) · [Magician Series index](../) · [Existing E6 user guide](../../dobot-magician-e6-user-guide.md)

### Product overview

**Module 5 — Cartesian Coordinates and Coordinate Frames.** This tutorial follows the matching instructor lesson plan and videos in the user-provided **15-module Magician E6 curriculum**. It converts the classroom sequence into a model-specific engineering learning checkpoint for the **six-axis E6 with ES01**, distinguishing source demonstrations from physical actions that still require real-device checks.

### Applications

* 2D/3D origins, quadrants and right-hand coordinate convention
* Tool-center-point positions and orientation
* Translate a table of teaching points into the correct base/user frame

### Specifications

| Parameter              | Value / conditions                                                                                |
| ---------------------- | ------------------------------------------------------------------------------------------------- |
| Robot                  | Magician E6, six-axis, **750 g** rated payload, **450 mm** reach, **±0.1 mm** repeatability       |
| Electrical / transport | Manufacturer E6 original 48 VDC/5 A rated supply; Ethernet controller, two ports                  |
| Software               | **DobotStudio Pro** with matching firmware; Lua Script Programming where applicable               |
| Included end effector  | **ES01 suction cup** only; separate servo gripper is not included in this SKU                     |
| Lesson prerequisite    | Paper/grid/calculator; connected E6 is optional for the first mathematical lesson.                |
| Source lesson          | [Module 5 lesson plan](https://docs.google.com/document/d/1GBXkItnWIxdVp17_m5aVKG02rBDmgTyL/edit) |

These are model-level ratings, not validated training task accuracy or safe contact forces.

### Hardware and connections

1. Verify the purchased **E6 with ES01** configuration, manufacturer E-stop, model/software revision and safe work envelope before connecting or actuating anything.
2. Paper/grid/calculator; connected E6 is optional for the first mathematical lesson.
3. Follow [the E6 user guide](../../dobot-magician-e6-user-guide.md) and [ES01 manual](../../dobot-es01-electric-suction-cup-user-guide.md) for exact tool electrical limits, mounting and operating states. Do not use a Magician Lite/4-axis Magician power supply or guessed I/O pinout.
4. Treat any change to TCP, payload, host network, robot I/O or motion limits as a controlled engineering configuration change. Record original settings and supervisor authorization.
5. Do not execute automatic trajectories or physical handling until all required calibration, obstacle checks and physical stop tests have succeeded.

### Software and development resources

* [Original Module 5 folder](https://drive.google.com/drive/folders/1d_wPKbubHTG1Cu7O7VQCou1h9Aoqs6bA) — instructional plan plus associated transcripts, video demonstrations and, for some modules, example code.
* [Module 5 lesson plan](https://docs.google.com/document/d/1GBXkItnWIxdVp17_m5aVKG02rBDmgTyL/edit) — specific classroom objectives and activities.
* [E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md) — model-specific mechanical/electrical safety.
* [ES01 User Guide](../../dobot-es01-electric-suction-cup-user-guide.md) — installed electric suction-cup hardware and Tool I/O.
* **Source-to-hardware boundary:** The source uses classroom coordinates such as (9,12) in 2D and (12,-9,12) in 3D; these are math examples, **not reachable E6 robot positions or tested millimeter setpoints**.

### Getting started

#### Prerequisites

Confirm that the E6 is the correctly identified six-axis model and that the actual included or additional tools required for this exercise are available. Start with the safe, read-only or offline checkpoint below.

#### First working result

1. Plot three **hypothetical** 3D coordinates relative to a labeled classroom origin and calculate displacement from A=(0,0,0) mm to B=(30,40,0) mm. Use a calculator or Python to verify a 50 mm Euclidean XY distance. Compare only the axis directions, not the numeric positions, with the E6 DobotStudio Pro read-only Jog display.
2. Record the actual input conditions, selected user/tool frame, software and firmware versions (where relevant) and any discrepancy.
3. Compare the result with the expected criterion and **stop before** adding physical motion or wiring that has not been verified.

**Expected result:** A coordinate diagram and 50 mm computed displacement between illustrative points.

#### Extension and student assessment

When the first check succeeds, follow the module's source lesson for additional, instructor-supervised tasks while preserving hardware safety and correct tool model. **Deliverable:** Labeled X/Y/Z diagram, coordinate table and frame note. Distinguish theoretical values, user-entered examples and measured robot values.

### Troubleshooting and FAQs

**What should I check if the lesson does not match the robot?** If the direction differs from the interface, check frame selection and axis orientation; never send these fictional coordinates to the robot.

**Are all source example settings safe for my E6?** No. The source uses classroom coordinates such as (9,12) in 2D and (12,-9,12) in 3D; these are math examples, **not reachable E6 robot positions or tested millimeter setpoints**.

**Does the course include the gripper shown in every video?** No. The selected E6 + ES01 product includes suction tool only; consult the relevant separate mechanical gripper manual for any jaw-gripper workflow.

### Downloads and technical documents

| Resource                                                                                           | Purpose                                              |
| -------------------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| [Module 5 source folder](https://drive.google.com/drive/folders/1d_wPKbubHTG1Cu7O7VQCou1h9Aoqs6bA) | Videos, transcript(s), lesson plan and module assets |
| [Module 5 lesson plan](https://docs.google.com/document/d/1GBXkItnWIxdVp17_m5aVKG02rBDmgTyL/edit)  | Original educational objectives and assessment       |
| [E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md)                                        | Robot power, work envelope, I/O and installation     |
| [ES01 User Guide V1.0](../../dobot-es01-electric-suction-cup-user-guide.md)                        | Correct tool setup and control                       |
| [Exact ES01 bundle](https://openelab.io/products/dobot-e6-es01-suction-robot)                      | Product and included tool scope                      |

### References and validation

* [Source Magician E6 Module 5 folder](https://drive.google.com/drive/folders/1d_wPKbubHTG1Cu7O7VQCou1h9Aoqs6bA) and [lesson plan](https://docs.google.com/document/d/1GBXkItnWIxdVp17_m5aVKG02rBDmgTyL/edit), retrieved from user-provided Google Drive curriculum 2026-11-21.
* [Existing E6 User Guide V1.4](../../dobot-magician-e6-user-guide.md) and [ES01 V1.0 manual](../../dobot-es01-electric-suction-cup-user-guide.md), manufacturer-authorized instructions reviewed 2026-11-21.
* [OpenELAB verified E6 + ES01 retail product](https://openelab.io/products/dobot-e6-es01-suction-robot), checked 2026-11-21.

**Documentation:** reviewed and organized as a curriculum draft. **Software execution:** not run. **Hardware validation:** not run. Do not interpret a sample exercise value, a video screenshot or an offline logic result as a verified robot controller setting or certification.
