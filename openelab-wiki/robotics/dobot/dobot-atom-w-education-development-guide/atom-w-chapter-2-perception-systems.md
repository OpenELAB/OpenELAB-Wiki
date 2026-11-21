---
description: >-
  DOBOT ATOM-W education tutorial derived from official course outline, with
  edition prerequisites, reproducible offline/simulation exercise and technical
  references.
---

# Chapter 2 — ATOM-W Robot Perception Systems

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (verified Standard selection; Education SKU unresolved) · **Variants:** Standard / Education · **Scope:** wheeled humanoid
{% endhint %}

[ATOM-W course and development index](./) · [Official ATOM SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) · [Official ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2)

### Product overview

**Chapter 2: Humanoid Robot Perception Systems** preserves the source's three topics: **2.1 perception fundamentals** (proprioceptive/exteroceptive sensors), **2.2 computer vision**, and **2.3 human perception and behavior understanding**. This tutorial centers on **sensor identification, message discovery, geometry and evaluation**, not unverified automatic detection performance.

### Applications

* RGB, depth and LiDAR acquisition for scene understanding.
* Object localization in a calibrated camera frame.
* Human detection, pose/gesture understanding and consent-aware interaction design.
* Correlating joint/IMU telemetry with external scene measurements.

### Specifications

| Sensor or data type | ATOM-W applicability and limits                                                                        |
| ------------------- | ------------------------------------------------------------------------------------------------------ |
| Head depth          | Listed on base platform; confirm camera driver, resolution and unit scaling                            |
| HD binocular camera | Listed on base platform; left/right calibration must be obtained                                       |
| LiDAR               | Used for wheeled navigation; scan topic, units and mounting frame need confirmation                    |
| Wrist depth         | **Education Version adds two**; not standard equipment                                                 |
| IMU / joint state   | SDK and ROS 2 expose robot state; exact covariance, timestamps and indices require firmware validation |
| Force / tactile     | Included in generic course theory; not proof of a tactile sensor on the ordered hand                   |

The SDK V2.1 describes low-level DDS telemetry (including `rt/upper/state`, `rt/lower/state` and AMR data). The ROS 2 package documents `/upper/state`, `/lower/state`, `/main/nodes/state` and `/hands/state` readers. **No universal camera topic/optical frame is asserted here** because the supplied hardware may differ.

### Hardware and connections

1. Confirm the exact edition, head camera models, LiDAR and optional wrist modules.
2. Inspect cables, sensor lenses and mechanical mounting **without disassembly**. Obtain manufacturer calibration for camera intrinsics and extrinsics.
3. Keep the robot stationary with the motion function disabled while testing camera drivers and topic discovery.
4. Do not expose images of identifiable people without the proper permission; plan a local/consented test subject or use synthetic data.
5. Confirm whether a given data stream belongs to host PC2, the base controller or an externally connected sensor before configuring drivers.

### Software and development resources

* [ATOM ROS 2](https://github.com/Dobot-Arm/dobot_atom_ros2): sensor/state messages and Gazebo environment.
* [ATOM ROS 2 state-reader examples](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_control_examples/README.md): known state reader names and topics; **hand reader requires installed hands**.
* [ATOM SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf): raw DDS/AMR interface documentation.
* Obtain the exact camera's official driver and calibration file from DOBOT or the installed camera maker; the source course does not identify a universal depth-camera model.

### Getting started

#### Task 1 — Discover live or simulated topics safely

From a configured, operator-authorized ROS 2 Humble environment:

```bash
source /opt/ros/humble/setup.bash
source ~/atom_ros2_ws/install/setup.bash
ros2 topic list
ros2 topic type /upper/state
ros2 topic echo /upper/state --once
```

**Expected result:** a list of topics and, **only if the robot bridge/simulation is publishing**, a type and one upper-body state message. This example is **read-only**. If missing, check simulation is running or real-robot DDS setup, the active ROS\_DOMAIN\_ID and interface; do not fabricate camera topic names.

#### Task 2 — Calibrate 3D localization offline

After obtaining depth scale and the **camera's** `fx`, `fy`, `cx`, `cy` intrinsics, reconstruct a point from measured pixel `(u,v)` and metric distance `Z`:

```python
def deproject(u, v, z_m, fx, fy, cx, cy):
    if z_m <= 0 or fx <= 0 or fy <= 0:
        raise ValueError("Invalid calibrated depth/intrinsics")
    return ((u - cx) * z_m / fx, (v - cy) * z_m / fy, z_m)

assert deproject(320, 240, 1.0, 600, 600, 320, 240) == (0, 0, 1.0)
```

**Expected result:** the calibration test returns (0, 0, 1.0) m in the **camera optical frame**. The arbitrary test intrinsics are illustrative, **not ATOM-W calibration**. It cannot locate a real object in base/arm coordinates until extrinsics, timestamp alignment and depth validity are verified.

#### Task 3 — Evaluate detection and human perception

Use a manually labeled, consented/synthetic image set to compare object detection, person bounding boxes, pose estimation and gesture recognition. Record false positives/false negatives, illumination, occlusions and response latency; do not equate face identification with the course's simpler person-presence objective.

### Troubleshooting and FAQs

**The topic appears but no data arrives:** inspect publisher state, ROS\_DOMAIN\_ID, DDS interface, QoS and sim time before installing unrelated drivers.

**Depth points are systematically shifted:** verify intrinsic resolution, distortion, depth scale and camera-to-robot transform; do not use uncalibrated pixels for a grasp.

**Is LiDAR sufficient for human recognition?** No. It supports geometric perception and navigation; human identification requires separate vision models and appropriate safeguards.

### Downloads and technical documents

* [ATOM ROS 2 package](https://github.com/Dobot-Arm/dobot_atom_ros2).
* [ROS 2 state reader tutorial](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_control_examples/README.md).
* [ATOM-W User Guide V1.0](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) — sensor locations.
* [SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) — model state and AMR fields.

**Student deliverable:** sensor inventory, observed ROS 2 topic/type table, one validated calibration test, and a labeled perception evaluation report.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, V2.0, 2026-09-15 (user-supplied course outline); the topical breakdown above follows its respective chapter.
* [OpenELAB ATOM-W product and edition listing](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [DOBOT ATOM-W User Guide V1.0 (manufacturer-authored document mirrored by ManualsLib)](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html), 2026-08-07.
* [DOBOT ATOM SDK Application Development Guide V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf), 2026-08-26.
* [Official ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2), reviewed 2026-11-21.

**Source review:** performed for this draft. **Software execution:** not run. **Hardware test:** not run. All expected results are learning checkpoints, not measured outcomes; firmware pairing, exact model frames, installed options and real-platform safety remain to be confirmed before physical experiments.
