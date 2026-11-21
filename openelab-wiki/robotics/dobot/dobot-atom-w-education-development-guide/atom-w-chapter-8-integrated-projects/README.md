---
description: >-
  DOBOT ATOM-W education chapter with model-specific hardware scope, practical
  workflow, validation checkpoints and source links.
---

# Chapter 8 — ATOM-W Integrated Project Architecture

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (Standard Version verified; Education SKU pending) · **Versions:** Standard / Education · **Platform:** wheeled humanoid
{% endhint %}

[ATOM-W course index](../) · [ATOM-W physical-operation guide](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) · [Official ROS 2 package](https://github.com/Dobot-Arm/dobot_atom_ros2)

### Product overview

**Chapter 8: Integrated Humanoid Robot Design Projects** is the systems-engineering bridge to the source course's three applications: **8.1 Exhibition Guide**, **8.2 Vision-Based Grasping**, and **8.3 Automotive Parts Sorting**. Each application has an independent tutorial. This page defines reusable integration rules so the projects do not bypass robot safety when combining perception, navigation, speech, arms and hands.

### Applications

* Modular architecture for indoor mobile humanoid applications.
* Clear boundaries between camera inference, operator approval and robot control.
* Capstone testing from offline simulation to supervised physical experiments.
* Reporting task quality with reproducible metrics and failure cases.

### Specifications

| Layer                | Data flow / evidence                                                                                                                                                                                                      |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Perception           | Verified head RGB/depth, LiDAR and (EDU) wrist depth, with timestamps/calibration                                                                                                                                         |
| Interaction          | Versioned ASR/TTS and Q\&A, separately validated                                                                                                                                                                          |
| Motion               | ATOM-W chassis control and 7-DoF arms via proper model/SDK                                                                                                                                                                |
| Manipulation         | Dexterous hands only if present; Education package includes two                                                                                                                                                           |
| Operator authority   | Human enable, physical stop, permission and recovery policy                                                                                                                                                               |
| ROS 2 / SDK          | [Official W-P3 ROS 2](https://github.com/Dobot-Arm/dobot_atom_ros2) and [SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) |
| Production readiness | Not provided by course outline; requires risk assessment and actual tests                                                                                                                                                 |

### Hardware and connections

1. Record the precise ATOM-W edition and any installed custom gripper. A Standard Version does not include two hands.
2. Confirm the real E-stop and remote behavior from the W guide; do not reuse legged models' stop sequences.
3. Use the developer PC2 and permitted network paths. Avoid modifications to reserved PC1.
4. Use training props with safe mass, geometry and spacing. Do not operate near unbriefed exhibition visitors or working industrial conveyors.
5. Keep a verified operator and clearly defined physical/virtual exclusion zone during any physical integration.

### Software and development resources

The overall pattern is: perception adapters → time/frame normalization → intention classifier / mission planner → **central motion authorization gateway** → manufacturer-supported actuator interface. Store logs separately.

Use [ROS 2 W-P3 Gazebo](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md) for preliminary integration, and [Chapter 4 data acquisition](../atom-w-chapter-4-data-acquisition.md) for provenance and synchronized logging. A direct wire from ASR, object detector or LLM output into motor or hand DDS control is not an acceptable tutorial architecture.

### Getting started

#### Task 1 — Requirements and modes

For each project, define: user/task goal, valid/invalid inputs, robot edition, world frames, approved actuators, stop authority, timing, battery limits, human acceptance criteria and data retention. Plan states such as Idle, Observe, Plan, WaitForApproval, Execute, Verify and Fault.

#### Task 2 — First working result: offline unified authority gate

This Python example is **pure software**, not connected to any actuator:

```python
def permit(action, enabled, healthy, perception_fresh, hand_installed):
    if not enabled or not healthy or not perception_fresh:
        return False
    if action == "speak":
        return True
    if action == "grasp":
        return bool(hand_installed)
    return False

assert permit("speak", True, True, True, False)
assert not permit("grasp", True, True, True, False)
assert permit("grasp", True, True, True, True)
assert not permit("speak", True, True, False, True)
assert not permit("move_base", True, True, True, True)
```

**Expected result:** all assertions pass. The sample blocks motion by default and distinguishes speech from grasp. It does **not** implement physical safety interlocks, collision avoidance or hand capabilities; those are design/test obligations.

#### Task 3 — Integrate modules incrementally

1. Read-only robot status and physical access checks ([Chapter 5](../atom-w-chapter-5-operation-sensors.md)).
2. Verify sensor topics and metric frames ([Chapter 2](../atom-w-chapter-2-perception-systems.md)).
3. Simulate W-P3 arm/chassis trajectories ([Chapter 7](../atom-w-chapter-7-kinematics-teleoperation.md)).
4. Integrate non-motion speech and perception feedback ([Chapter 6](../atom-w-chapter-6-human-robot-interaction.md)).
5. Validate action arbitration, stale-data handling, operator-disable, collision/no-go conditions and logs.
6. Only after a formal physical test protocol, progress from stationary tests to bounded supervised actions.

#### Task 4 — Evaluate a project scientifically

Define completion rate, correct-detection/recognition rate, intervention count, command rejection count, latency, actual collision/stopping behavior, data loss, energy/time budget and recovery effectiveness. Report denominators and hardware versions. A simulation pass cannot be counted as a live robot success.

### Three Chapter 8 application tutorials

* [**8.1 Exhibition Guide**](atom-w-application-exhibition-guide.md) — interactive exhibition route and spoken guidance.
* [**8.2 Vision-Based Grasping**](atom-w-application-vision-grasping.md) — 3D localization and installed hand/gripper prerequisites.
* [**8.3 Automotive Parts Sorting**](atom-w-application-parts-sorting.md) — recognition, grasp planning and placement evaluation.

### Troubleshooting and FAQs

**The camera detects an item but the arm cannot reach it:** frame transforms, calibration, 7-DoF joint limits, tool geometry and self-collision may block a valid solution.

**A spoken request conflicts with a navigation safety event:** the motion gateway must reject/abort or hold the action, respecting the operator stop; do not let an ASR node command motors directly.

**Why are hands missing in grasp demos?** The Standard Edition does not include dexterous hands. Confirm compatible installed hardware before enabling grasping.

### Downloads and technical documents

* [Official ATOM-W SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [Official ROS 2 / W-P3 Gazebo](https://github.com/Dobot-Arm/dobot_atom_ros2).
* [ATOM-W User Guide V1.0](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html).
* [ATOM-W product editions](https://openelab.io/products/dobot-atom-w-wheeled-humanoid).

**Student deliverable:** system architecture, interface contracts, gate unit tests, per-module test checklist and measured capstone evaluation plan.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, Tutorial Guide V2.0 (2026-09-15), supplied source; chapter mapping as listed above.
* [OpenELAB, ATOM-W product/edition configuration](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [DOBOT, ATOM-W Wheeled Humanoid Robot User Guide V1.0, 2026-08-07](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) (manufacturer document mirrored by a third party).
* [DOBOT, ATOM SDK Application Development Guide V2.1, 2026-08-26](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [Official Atom C++ SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) and [ROS 2 source](https://github.com/Dobot-Arm/dobot_atom_ros2), reviewed 2026-11-21.

**Source review:** completed for documentation draft. **Software execution:** not run. **Hardware validation:** not run. Real ATOM-W trials require a confirmed firmware, installed edition and a supervised, manufacturer-compliant safety procedure.
