---
description: >-
  DOBOT ATOM-W education tutorial derived from official course outline, with
  edition prerequisites, reproducible offline/simulation exercise and technical
  references.
---

# Chapter 3 — ATOM-W Motion Control and Planning

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (verified Standard selection; Education SKU unresolved) · **Variants:** Standard / Education · **Scope:** wheeled humanoid
{% endhint %}

[ATOM-W course and development index](./) · [Official ATOM SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) · [Official ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2)

### Product overview

**Chapter 3: Humanoid Robot Motion Control and Planning** maps to **3.1 kinematics**, **3.2 gait planning**, **3.3 dynamics** and **3.4 trajectory tracking**. The source introduces biped support and swing phases as theory. **For the ATOM-W the applicable physical task is mobile-base trajectory control plus arm/torso manipulation**. Keep bipedal gait demonstrations in a separately labeled legged simulation, not on the W chassis.

### Applications

* Coordinate systems and pose transforms for head, torso, left/right arms and base.
* Forward/inverse kinematics (FK/IK), workspace constraints and 7-DoF arm redundancy.
* Wheeled speed and turning plans in a supervised environment.
* Trajectory interpolation and commanded-versus-measured tracking error analysis.

### Specifications

| Model or interface        | Documented scope                                                                                  |
| ------------------------- | ------------------------------------------------------------------------------------------------- |
| Kinematics                | Arm 7 DoF each; actual lengths/limits derive from **ATOM\_W** model and manufacturer joint tables |
| High-level motion         | `GetFsmId`, `SetFsmId`, `SetVel(vx,vy,vyaw,duration)` documented by DOBOT                         |
| Velocity units            | `vx`, `vy` in m/s, `vyaw` in rad/s, `duration` seconds                                            |
| Model simulation          | `atom\_gazebo`: **ATOM W-P3** with chassis and upper body                                         |
| Biped walking examples    | Other ATOM models; **not W wheel-base behavior**                                                  |
| Joint commands and limits | Firmware-specific; do **not** use P2 leg indexing on W                                            |

The sample `rpc\_test` in the [C++ SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) sends motion commands. It is **not** a read-only teaching command, nor should students automatically select an FSM ID used for legged walking.

### Hardware and connections

* Keep the real ATOM-W at rest while testing FK/IK and motion planning.
* Only after a reviewed site safety assessment should an authorized operator enable live chassis/arm commands using the **ATOM-W V1.0 user guide**.
* Do not place an object or student within the potential 600 mm arm reach plus mobile-base path.
* For an actual manipulator trajectory, confirm **joint count, names, positions, torque/velocity limits, end flange, attached tool mass and calibration** using the exact W model.

### Software and development resources

| Resource                                                                                                                                          | Purpose                                             |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| [ROS 2 ATOM-W Gazebo README](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md)                                        | Safe simulated chassis/arms                         |
| [ROS 2 atom\_urdf sources](https://github.com/Dobot-Arm/dobot_atom_ros2/tree/main/atom_urdf)                                                      | Frames, links and mesh definitions                  |
| [SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) | **ATOM\_W** joint limits and RPC method definitions |
| [ATOM locomotion training](https://github.com/embodied-dobot/atom-locomotion-training)                                                            | **Biped P2/P3 only**; compare conceptually          |

### Getting started

#### Task 1 — Build coordinate system notes

Draw `map → odom → base\_link → torso → left/right arm → tool` as a proposed conceptual TF tree. **Do not assume these exact names are exported by your installed ATOM-W URDF**. Inspect the actual URDF and `ros2 run tf2\_tools view\_frames` after loading the model; use its real frame names in code.

#### Task 2 — First working result: offline wheel-path integration

This Python-only toy calculation demonstrates the units and interpretation of a mobile-base velocity command. It is **not** a real robot controller:

```python
import math

vx_m_s, vy_m_s, omega_rad_s, dt_s = 0.2, 0.0, 0.0, 0.5
yaw = 0.0
dx = (vx_m_s * math.cos(yaw) - vy_m_s * math.sin(yaw)) * dt_s
dy = (vx_m_s * math.sin(yaw) + vy_m_s * math.cos(yaw)) * dt_s
assert abs(dx - 0.1) < 1e-9 and abs(dy) < 1e-9
print("ideal planar displacement (m):", dx, dy)
```

**Expected result:** idealized displacement 0.1 m forward over 0.5 s. Actual motion differs due to traction, controller limits, obstacle avoidance and acceleration; never equate this calculation to measured performance.

#### Task 3 — Inspect W-P3 in Gazebo

```bash
source /opt/ros/humble/setup.bash
source ~/atom_ros2_ws/install/setup.bash
ros2 launch atom_gazebo atom_arms_only.launch.py
```

**Expected result:** upper-body simulated model loads, suitable for inspecting arm joint axes and planning. For trajectories, first test interpolation and IK **inside simulation**, with real model limits and collision checks. Do not publish direct motor trajectories to hardware for the coursework.

#### Task 4 — Trajectory error report

For a simulated reference trajectory `q\_ref(t)` and actual feedback `q\_meas(t)`, calculate per-joint `e(t) = q\_ref(t)-q\_meas(t)`, RMSE (rad) and maximum joint error. Record solver failures, reachable workspace and collision attempts. If using legged walking theory, clearly label it **comparison only**.

### Troubleshooting and FAQs

**A tutorial uses a "walking" state 301/302:** those example FSM states in the generic SDK are for **legged walking**. Verify an **ATOM-W-specific** state mapping before any mobile-base motion.

**The IK solution reaches an impossible pose:** check the real W-P3 joint limits, end-effector frame, current seed posture and self-collision constraints.

**My commanded distance is not exact:** high-level velocity/duration are command inputs, not an odometry or repeatability guarantee.

### Downloads and technical documents

* [W-P3 Gazebo instructions](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md).
* [ATOM-W coordinate/joint tables, SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [SDK RPC examples](https://github.com/Dobot-Arm/dobot_atom_sdk/blob/main/example/rpc_test.cpp) — motion-producing; review, do not blindly run.

**Student deliverable:** W-P3 kinematic frame diagram, offline path calculation, simulated joint/path plots and a note distinguishing biped theory from W wheeled control.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, V2.0, 2026-09-15 (user-supplied course outline); the topical breakdown above follows its respective chapter.
* [OpenELAB ATOM-W product and edition listing](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [DOBOT ATOM-W User Guide V1.0 (manufacturer-authored document mirrored by ManualsLib)](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html), 2026-08-07.
* [DOBOT ATOM SDK Application Development Guide V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf), 2026-08-26.
* [Official ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2), reviewed 2026-11-21.

**Source review:** performed for this draft. **Software execution:** not run. **Hardware test:** not run. All expected results are learning checkpoints, not measured outcomes; firmware pairing, exact model frames, installed options and real-platform safety remain to be confirmed before physical experiments.
