---
description: >-
  DOBOT ATOM-W education tutorial derived from official course outline, with
  edition prerequisites, reproducible offline/simulation exercise and technical
  references.
---

# Chapter 4 — ATOM-W Embodied Data Acquisition

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (verified Standard selection; Education SKU unresolved) · **Variants:** Standard / Education · **Scope:** wheeled humanoid
{% endhint %}

[ATOM-W course and development index](./) · [Official ATOM SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) · [Official ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2)

### Product overview

**Chapter 4: Humanoid Robot Data Acquisition Systems** corresponds to **4.1 data fundamentals**, **4.2 embodied AI data toolchain** and **4.3 training center application case**. The objective is an **inspectable multimodal dataset** linking observation, joint state, human action and timing, not merely collecting a folder of unrelated images.

### Applications

* Timestamped vision, joint state, pose, action and audio data logging.
* Human demonstrations and supervised teleoperation traces.
* Dataset annotation, validation, train/validation splits and safe retention.
* Infrastructure planning from acquisition workstations to policy training and deployment evaluation.

### Specifications

| Data source             | Available evidence and scope                                                                                  |
| ----------------------- | ------------------------------------------------------------------------------------------------------------- |
| Upper/lower robot state | ROS 2 `/upper/state`, `/lower/state` provided in official example package                                     |
| Node diagnostics        | `/main/nodes/state`; actual publisher required                                                                |
| Hand joints             | `/hands/state`; **Education Version or supported installed hands**                                            |
| Head visual stream      | Hardware listed; topic, camera calibration and file format require verification                               |
| VR demonstration        | **Education Version** lists VR Quest and collection software; closed toolchain/version not publicly specified |
| Time synchronization    | Not guaranteed by the course outline; clocks and interpolation must be designed and measured                  |

No per-sensor sampling rate, dataset license, API token or deployment readiness is invented here. The SDK V2.1 lists raw DDS data directions and some typical rates; live ROS 2 availability depends on the installed bridge and firmware.

### Hardware and connections

1. Inventory sensors, operator devices, storage capacity, network and permission boundaries.
2. Confirm the installed ATOM-W **Standard versus Education** configuration. Standard cannot assume VR Quest, 6-DoF hands or wrist depth cameras.
3. Use only authorized developer access on PC2; avoid changes to reserved PC1 control programs.
4. Keep robot motion **disabled** for the first recording. Use simulated or pre-consented human examples before live teleoperation.
5. Document camera clocks, ROS time, DDS timestamps, frame transforms and recording privacy/retention policy.

### Software and development resources

* [DOBOT ROS 2 state readers](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_control_examples/README.md): concrete read-only `upper\_state\_reader`, `lower\_state\_reader`, `main\_nodes\_state\_reader` executables.
* [DOBOT ROS 2 workspace](https://github.com/Dobot-Arm/dobot_atom_ros2): `rosdep`, `colcon` and Gazebo support.
* [ATOM-W SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf): raw DDS and service telemetry definitions.
* Optional external ASR/policy learning frameworks require distinct versioned installation and validation.

### Getting started

#### Task 1 — First working result: record read-only robot state

On a configured **ROS 2 Humble** environment with W-P3 simulation or the validated robot bridge running:

```bash
source /opt/ros/humble/setup.bash
source ~/atom_ros2_ws/install/setup.bash
ros2 topic list
ros2 topic type /upper/state
ros2 topic echo /upper/state --once
```

**Expected result:** if the `/upper/state` publisher is active, one message can be inspected. Record topic type and timestamp fields, not assumed sample values. For a bounded recording, use `ros2 bag record -o atom\_upper\_trial /upper/state`, then **Ctrl+C** after a short stationary interval; inspect the bag metadata and saved messages before adding further streams. The upper-state stream may be high-rate, so plan storage and retention.

#### Task 2 — Create a dataset schema

For every observation, record at minimum: robot edition and firmware, SDK/git commit, sensor name, time source, timestamp, frame ID, unit, calibration reference, permission, and annotation status. Link `action\_request`, `action\_observed` and `operator` through trial IDs rather than joining solely by array order.

#### Task 3 — Test synchronization and data quality offline

```python
def time_gap_ms(camera_stamp_s, joint_stamp_s):
    return abs(camera_stamp_s - joint_stamp_s) * 1000

assert round(time_gap_ms(2.010, 2.000), 5) == 10.0
```

**Expected result:** a synthetic 10 ms gap. This is **not** a measured ATOM-W synchronization error. Create a histogram of real measured gaps and flag missing samples, clock resets, out-of-order messages, invalid joint values, occlusions and unlabeled episodes.

#### Task 4 — Plan a training center case

Create a route: approved scenario → demonstrated episodes → synchronized raw capture → annotation and quality checks → dataset split (by episode/session, not random adjacent frames) → offline training → simulated evaluation → supervised deployment decision. Report dataset provenance and consent.

### Troubleshooting and FAQs

**Hand data is missing:** check installed edition and end-effector, DDS/ROS bridge, correct topic and whether the hand controller reports state. Do not fill missing hand data with fabricated zeros.

**Bag timestamps do not align:** check hardware clock synchronization, ROS `use\_sim\_time`, dropped frames and pipeline latency. Distinguish source timestamp from receive timestamp.

**Can VR demonstration run with the Standard Version?** Not from the listed box contents; Education Version adds VR Quest and data software. Ask DOBOT for exact toolchain/version documentation.

### Downloads and technical documents

* [Official ROS 2 state reader and recorder examples](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_control_examples/README.md).
* [ATOM SDK V2.1 network and telemetry specification](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [OpenELAB hardware configurations](https://openelab.io/products/dobot-atom-w-wheeled-humanoid).

**Student deliverable:** a short bag/dataset with metadata, timestamp analysis, data quality report, and conceptual training/validation/deployment workflow.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, V2.0, 2026-09-15 (user-supplied course outline); the topical breakdown above follows its respective chapter.
* [OpenELAB ATOM-W product and edition listing](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [DOBOT ATOM-W User Guide V1.0 (manufacturer-authored document mirrored by ManualsLib)](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html), 2026-08-07.
* [DOBOT ATOM SDK Application Development Guide V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf), 2026-08-26.
* [Official ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2), reviewed 2026-11-21.

**Source review:** performed for this draft. **Software execution:** not run. **Hardware test:** not run. All expected results are learning checkpoints, not measured outcomes; firmware pairing, exact model frames, installed options and real-platform safety remain to be confirmed before physical experiments.
