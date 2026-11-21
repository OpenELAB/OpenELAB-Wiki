---
description: >-
  DOBOT ATOM-W education tutorial derived from official course outline, with
  edition prerequisites, reproducible offline/simulation exercise and technical
  references.
---

# Chapter 1 — ATOM-W Humanoid Robot Architecture

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (verified Standard selection; Education SKU unresolved) · **Variants:** Standard / Education · **Scope:** wheeled humanoid
{% endhint %}

[ATOM-W course and development index](./) · [Official ATOM SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) · [Official ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2)

### Product overview

This is **Chapter 1: Introduction to Humanoid Robots**, covering **1.1 Definition and Development of Humanoid Robots** and **1.2 Humanoid Robot Architecture and Applications**. A humanoid robot may have a head, torso and anthropomorphic manipulators while using different locomotion platforms. **ATOM-W's chassis is wheeled**, whereas the course also discusses legged humanoids in general.

**Learning outcome:** identify the robot's major subsystems, the architectural differences between wheeled and bipedal platforms, and suitable educational/research applications.

### Applications

* Describing the evolution from fixed industrial manipulators to mobile, human-oriented manipulation systems.
* Comparing stability and mobility tradeoffs: wheeled AMR-style motion versus bipedal foot-contact locomotion.
* Identifying the electrical, control, perception and planning components needed for a real robot application.

### Specifications

| ATOM-W subsystem           | Documented scope / key characteristic                                                   |
| -------------------------- | --------------------------------------------------------------------------------------- |
| Upper-body joints          | 20 DoF **excluding** optional hands: head 2, arms 7 + 7, waist 4 (store listing)        |
| Mobility                   | Wheeled mobile chassis; not two walking legs                                            |
| Head sensors               | Depth camera, HD binocular camera                                                       |
| Navigation                 | LiDAR-based platform; actual map/network stack requires commissioning                   |
| Audio                      | Microphone and two speakers                                                             |
| Education-specific options | Two 6-DoF hands, two wrist depth cameras, VR Quest, data toolchain                      |
| Compute                    | Platform product listing describes Intel i9 and GPU; record actual system configuration |

The hardware overview is **not** a wiring guide. Use the ATOM-W V1.0 user manual and V2.1 SDK joint sequence tables for exact revision-level identification.

### Hardware and connections

1. Compare the physical delivered device to the Standard/Education packing list.
2. Locate the mobile chassis, head sensors, waist, each arm, tool flange and any installed hand/wrist camera. **Do not disassemble** components for the exercise.
3. Identify the operator console, emergency stops, charging interface and the **developer PC2** separately from the reserved **control PC1**.
4. Draw a system block diagram with arrows for sensors → compute → software decisions → high-level controller → arms/chassis; label the two operating domains.
5. Photograph external labels only where permitted; don't publish serial numbers, private Wi-Fi credentials or internal access tokens.

### Software and development resources

| Resource                                                                                                                                                                 | Purpose                                                   |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------- |
| [ATOM-W product page](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)                                                                                        | Standard and Education bill of materials                  |
| [ATOM SDK application guide V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) | ATOM\_W joint names, states, and network architecture     |
| [ROS 2 ATOM W-P3 Gazebo](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md)                                                                   | Simulation of this **wheeled** configuration              |
| [ATOM P2/P3 reinforcement-learning project](https://github.com/embodied-dobot/atom-locomotion-training)                                                                  | **Different legged research models**, for comparison only |

### Getting started

#### Activity 1 — Hardware inventory and system diagram

Prepare a table of every physical subsystem and whether it is included, optional, or absent from the purchased edition. Keep the definition of “20 DoF excluding hands” separate from added hand degrees of freedom.

#### Activity 2 — First working result: wheeled model in Gazebo

On a PC with the official [ROS 2 Humble prerequisites and workspace](https://github.com/Dobot-Arm/dobot_atom_ros2) already installed:

```bash
source /opt/ros/humble/setup.bash
source ~/atom_ros2_ws/install/setup.bash
ros2 launch atom_gazebo atom_gazebo.launch.py
```

**Expected result:** the **ATOM W-P3** robot appears in Gazebo. Identify chassis, torso, head and arm links from the displayed model; record the total listed joints and model asset revision. If loading fails, inspect the build errors, `atom\_urdf`, `gazebo\_ros`, `ros2\_control` and `gazebo\_ros2\_control` dependencies; no hardware motion is required.

#### Activity 3 — Compare designs

In two columns, compare wheel traction, continuous support, turning space, obstacles, step-crossing ability, actuation cost and software complexity against bipedal gait theory. Do **not** describe P2/P3 legged locomotion policy files as ATOM-W firmware.

### Troubleshooting and FAQs

**Does “humanoid” always mean bipedal walking?** No. ATOM-W has humanoid manipulators and a wheeled mobile base.

**Are the extra dexterous hands included on all units?** No. Check the exact edition and delivered tool flange; Standard lists no hands.

**Why doesn't my physical robot have the same joint count as a generic ATOM URDF?** Distinguish W and legged P2/Max models, edition hand options and the **SDK's joint array representation** before mapping joint indices. Do not apply another model's motor limits.

### Downloads and technical documents

* [ATOM-W listing and packing list](https://openelab.io/products/dobot-atom-w-wheeled-humanoid).
* [ATOM-W V1.0 user guide](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) — physical architecture, safety and interfaces.
* [ATOM W-P3 Gazebo README](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md).
* [ATOM SDK V2.1 joint and coordinate sections](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).

**Student deliverable:** illustrated system diagram, edition inventory, correctly labeled wheeled-versus-biped comparison and simulation screenshot/log.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, V2.0, 2026-09-15 (user-supplied course outline); the topical breakdown above follows its respective chapter.
* [OpenELAB ATOM-W product and edition listing](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [DOBOT ATOM-W User Guide V1.0 (manufacturer-authored document mirrored by ManualsLib)](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html), 2026-08-07.
* [DOBOT ATOM SDK Application Development Guide V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf), 2026-08-26.
* [Official ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2), reviewed 2026-11-21.

**Source review:** performed for this draft. **Software execution:** not run. **Hardware test:** not run. All expected results are learning checkpoints, not measured outcomes; firmware pairing, exact model frames, installed options and real-platform safety remain to be confirmed before physical experiments.
