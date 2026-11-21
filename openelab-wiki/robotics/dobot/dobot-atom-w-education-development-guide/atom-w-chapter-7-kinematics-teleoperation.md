---
description: >-
  DOBOT ATOM-W education chapter with model-specific hardware scope, practical
  workflow, validation checkpoints and source links.
---

# Chapter 7 — ATOM-W Kinematics Simulation and Teleoperation

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (Standard Version verified; Education SKU pending) · **Versions:** Standard / Education · **Platform:** wheeled humanoid
{% endhint %}

[ATOM-W course index](./) · [ATOM-W physical-operation guide](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) · [Official ROS 2 package](https://github.com/Dobot-Arm/dobot_atom_ros2)

### Product overview

**Chapter 7: Humanoid Robot Motion Control Practice** covers **7.1 Forward and Inverse Kinematics Simulation** and **7.2 Humanoid Robot Teleoperation**. The right ATOM-W progression is: **kinematic model → W-P3 wheeled/arm simulation → offline operator retargeting → authorized hardware pilot**. The Education Version includes the VR device and collection toolchain; Standard does not.

### Applications

* Reproducing a wheeled humanoid and seven-DoF arms in Gazebo.
* Computing a target end-effector pose and inspecting joint feasibility.
* Building a teleoperation retargeting layer with deadband, workspace bounds and a stop gate.
* Recording demonstration trajectories for an embodied dataset.

### Specifications

| Item                      | Documented condition                                                                                                 |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------- |
| ROS 2                     | Ubuntu 22.04 + Humble, per official repository                                                                       |
| Simulation                | `atom\_gazebo` **ATOM W-P3**, full body or arms-only                                                                 |
| Manipulators              | 7 DoF per arm; exact joint names and limits from the **ATOM\_W** model/version                                       |
| Hardware developer access | Authorized PC2 only, control PC1 reserved                                                                            |
| Hands and VR              | Included only with **Education Version**, if delivered                                                               |
| Low-level motor commands  | `bridge\_test`, DDS `/upper/cmd`, `/lower/cmd`, `/hands/cmd` can actuate and are **not** beginner first-run commands |

The [ATOM\_W section of SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) is the relevant W joint-map authority, not a P2 biped robot config.

### Hardware and connections

* Keep the actual robot **powered safely or parked** as required by its manufacturer procedure; no physical movement in the first simulation exercises.
* For Education VR retargeting, record VR tracking frame and arm tool-frame calibration. Confirm the actual glove/controller/hand variant before mapping.
* Keep a spotter and verified E-stop available for any later mobile-manipulation trial; assess collisions with both base and arms.
* Never command an unavailable dexterous hand on Standard hardware.

### Software and development resources

| Resource                                                                                                                                               | Purpose                                                |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| [W-P3 Gazebo README](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md)                                                     | Verified launch file names and dependencies            |
| [ROS 2 root README](https://github.com/Dobot-Arm/dobot_atom_ros2)                                                                                      | Build environment and workspace                        |
| [atom\_urdf repository](https://github.com/Dobot-Arm/dobot_atom_ros2/tree/main/atom_urdf)                                                              | Robot description and transforms                       |
| [ATOM SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) | ATOM\_W limits and RPC/DDS                             |
| [P2/P3 locomotion training](https://github.com/embodied-dobot/atom-locomotion-training)                                                                | Separate **biped** learning; not ATOM-W wheeled policy |

### Getting started

#### Task 1 — First working result: launch arms-only simulation

With the [official ROS 2 workspace](./) built:

```bash
source /opt/ros/humble/setup.bash
source ~/atom_ros2_ws/install/setup.bash
ros2 launch atom_gazebo atom_arms_only.launch.py
```

**Expected result:** a simulated W-P3 upper-body model loads in Gazebo. Inspect axis directions, default poses and available simulated controllers. If unavailable, inspect `atom\_gazebo`, `atom\_urdf`, `gazebo\_ros2\_control` and the current ROS 2 release.

#### Task 2 — Kinematics in simulation

1. Inspect the **actual W-P3 URDF** for left/right shoulder, elbow, wrist, torso and tool frames.
2. Compute FK for the current joint vector using the model's transform chain.
3. Define a reachable target pose; run IK with seed configuration, correct joint bounds and collision checks. Record residual position (m), orientation (rad) and target errors.
4. Replay only in simulation, measuring commanded and observed trajectories. Do not use published bipedal gait commands on ATOM-W.

#### Task 3 — Offline operator retargeting gate

The following tests authorization and deadband without ever publishing a motor command:

```python
def bounded_delta(raw_delta, enabled, limit=0.05, deadband=0.005):
    if not enabled:
        return 0.0
    if abs(raw_delta) < deadband:
        return 0.0
    return max(-limit, min(limit, raw_delta))

assert bounded_delta(0.10, True) == 0.05
assert bounded_delta(0.003, True) == 0.0
assert bounded_delta(0.10, False) == 0.0
```

**Expected result:** all tests pass in a **synthetic, unit-agnostic** operator input. The arbitrary clamp/deadband are not DOBOT joint-motion or safety limits; they must never be directly reused as robot setpoints. Real VR-to-arm retargeting requires coordinate transforms, absolute joint limits, velocity/acceleration constraints, timeouts, collision checks and human review.

#### Task 4 — Teleoperation trial design

Design the gated system: VR sensor → tracking/filter → calibration → IK → bounds and collision checks → operator hold-to-enable → trusted motion gateway → simulated controller → log. Use a separate authority for physical emergency stop. Test disabled controller, stale VR tracking and simulated self-collision before live trials.

### Troubleshooting and FAQs

**Why does an ATOM P2 walking example not work on W-P3?** Their lower-body kinematic structures differ; use W-P3 Gazebo and its joint/actuator definition.

**The simulation model loads but no controller responds:** run `ros2 control list\_controllers` and inspect loaded controller configuration and model names; do not improvise joint command topics.

**Can Standard Edition perform VR hand teleoperation as sold?** Not with the specified Standard box contents; Education includes hands, wrist cameras and VR Quest.

### Downloads and technical documents

* [W-P3 full-body and arms-only simulation](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md).
* [ATOM ROS 2 sources and robot description](https://github.com/Dobot-Arm/dobot_atom_ros2).
* [ATOM\_W-specific SDK tables](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).

**Student deliverable:** W-P3 simulation screenshot, FK/IK error log, retargeting filter unit tests and a teleoperation safety/recording architecture.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, Tutorial Guide V2.0 (2026-09-15), supplied source; chapter mapping as listed above.
* [OpenELAB, ATOM-W product/edition configuration](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [DOBOT, ATOM-W Wheeled Humanoid Robot User Guide V1.0, 2026-08-07](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) (manufacturer document mirrored by a third party).
* [DOBOT, ATOM SDK Application Development Guide V2.1, 2026-08-26](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [Official Atom C++ SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) and [ROS 2 source](https://github.com/Dobot-Arm/dobot_atom_ros2), reviewed 2026-11-21.

**Source review:** completed for documentation draft. **Software execution:** not run. **Hardware validation:** not run. Real ATOM-W trials require a confirmed firmware, installed edition and a supervised, manufacturer-compliant safety procedure.
