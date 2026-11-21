---
description: >-
  Model-scoped X-Trainer embodied-AI educational project with reproducible
  offline/simulation checkpoint, source links and hardware validation
  requirements.
---

# Project 3 — X-Trainer Intelligent Waste Sorting

{% hint style="info" %}
[**View DOBOT X-Trainer Dual-Arm Robot for AI Data Collection on OpenELAB**](https://openelab.io/products/dobot-x-trainer-data-robot)

**Product:** DOBOT X-Trainer · **SKU:** `DOBOT-8000000050` · **Sold kit:** two master hands, two slave grippers, three depth cameras, fixed base; **two Nova 2 robot arms and training PC not included**
{% endhint %}

[Return to X-Trainer course index](./) · [Existing Lightweight Base V1.6 Manual](../dobot-x-trainer-lightweight-base-user-guide.md)

### Product overview

**Project 3 — Intelligent Waste Sorting** covers the course's **(1) waste recognition and 3D localization**, **(2) stable grasping**, and **(3) classification, transport and placement**. The intended chain is **Recognition → Localization → Grasping → Transport → Classification**.

This is a **nonhazardous mock-waste** educational sorting cell. The X-Trainer open-source simulation provides dual-arm manipulation infrastructure, not a validated waste recognition model, camera calibration or sorting policy.

### Applications

* RGB/depth object detection and optical-frame deprojection.
* Class-to-bin routing with a reject/unknown category.
* Two-arm grasp strategy and simulated path planning.
* Full-trial evaluation: recognition, localization, pick, bin placement and recovery.

### Specifications

| Dependency     | Product/source scope                                                                                                              |
| -------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Physical arms  | Two compatible Nova 2 arms, **not included**                                                                                      |
| Grippers       | Two slave-hand grippers are listed; measured grasp force/limits depend on installed revision                                      |
| Cameras        | Three depth-sensing units are included; the old **Lightweight Base** manual states D405 ×3, not verified for every fixed-base SKU |
| Simulator      | [X-Trainer-LeIsaac Lift Cube](https://github.com/embodied-dobot/x-trainer), extend for mock-waste geometry                        |
| Localization   | Intrinsic matrix, valid depth scale and camera-to-arm extrinsics required                                                         |
| Classification | Model/classes not supplied by the course or X-Trainer source repo                                                                 |
| Safety         | Only clean, light, nonsharp, nonhazardous demonstration objects                                                                   |

### Hardware and connections

1. Use colored paper, empty packaging, lightweight plastic/metal replicas or other safe props. **Do not include used sharps, chemicals, contaminated waste, batteries or actual healthcare waste.**
2. Measure the sorting tray and bins, keeping them inside the actual validated reachable workspace and away from the base/camera mounts.
3. Before hardware execution, confirm the exact depth-camera model, intrinsics, time alignment, robot-world transform and gripper geometry.
4. Keep the robot motion gateway locked during recognition tests; a classification result is **not permission to actuate**.
5. Follow the applicable fixed-base installation/E-stop documentation; the Lightweight Base manual is not interchangeable by assumption.

### Software and development resources

Use [embodied-dobot/x-trainer](https://github.com/embodied-dobot/x-trainer) for initial two-arm simulation and data recording, then implement or select a separately versioned detection/segmentation model, depth decoder and robot-specific transformation chain. For commissioned physical training, consult [X-Trainer Lightweight Base V1.6](../dobot-x-trainer-lightweight-base-user-guide.md) only where its hardware revision matches.

### Getting started

#### Task 1 — Define the perception dataset

Choose three mock classes, plus unknown; label images across lighting/occlusion conditions. Keep one object instance entirely in one train/validation/test split to avoid leakage. Capture camera model, calibration, units and timestamp for every frame.

#### Task 2 — First working result: offline localization and routing

```python
def point_in_camera(u, v, z_m, fx, fy, cx, cy):
    if z_m <= 0 or fx <= 0 or fy <= 0:
        raise ValueError("Invalid depth or calibration")
    return ((u - cx)*z_m/fx, (v - cy)*z_m/fy, z_m)

BINS = {"paper": "A", "plastic": "B", "mock_metal": "C"}
def destination(label, valid_depth):
    return BINS.get(label, "REVIEW") if valid_depth else "REVIEW"

point = point_in_camera(320, 240, 0.7, 600, 600, 320, 240)
assert point == (0, 0, 0.7)
assert destination("plastic", True) == "B"
assert destination("unknown", True) == "REVIEW"
assert destination("paper", False) == "REVIEW"
```

**Expected result:** synthetic camera-center point is (0, 0, 0.7) m and unknown/invalid cases route to REVIEW. Intrinsics **600,600,320,240 are teaching constants, not X-Trainer camera calibration**. The output is camera-frame only; no physical grasp pose is provided.

#### Task 3 — Simulate grasp and bin placement

1. Add a simple safe mock object to the official **Lift Cube** simulation, preserving model file version and collision geometry.
2. Use a calibrated robot-camera transform to define target pose; reject missing depth.
3. Choose a feasible arm, tool approach and collision-checked trajectory in simulation.
4. Label grasp success, slip/drop, bin accuracy and human intervention, and record these separately from classification accuracy.
5. When actual dual Nova 2 hardware is verified, obtain a supervised test protocol before issuing any physical gripper or arm command.

### Troubleshooting and FAQs

**The image is detected but 3D pose is wrong:** inspect camera intrinsics, depth units, distortion, timestamp and extrinsics; do not use virtual camera FOV as real calibration.

**A grasp seems within reach but fails:** inspect actual Nova 2 joint limits, gripper stroke, tool offset, self-collision and object orientation.

**Can the platform recognize waste classes out of the box?** Not from this evidence. The document defines a project goal, and the public source demonstrates **Lift Cube**, not a trained waste model.

### Downloads and technical documents

* [X-Trainer-LeIsaac source](https://github.com/embodied-dobot/x-trainer).
* [OpenELAB X-Trainer cameras and kit scope](https://openelab.io/products/dobot-x-trainer-data-robot).
* [Lightweight Base V1.6 manual, cameras and data interfaces](../dobot-x-trainer-lightweight-base-user-guide.md).

**Student deliverable:** labeled mock-waste images, validated depth/pose calibration plan, routing unit tests, simulated pick/place records and a full-trial confusion and failure table.

### Course navigation

[Previous project](x-trainer-project-2-beverage-station.md) · [Continue to Project 4](x-trainer-project-4-precision-assembly.md)

### References and validation

* DOBOT, _Embodied AI Data Acquisition and Application Practice_, Educational Tutorial Guide **V2.0, 2026-09-15** (provided course outline), corresponding project.
* [OpenELAB DOBOT X-Trainer product listing](https://openelab.io/products/dobot-x-trainer-data-robot), reviewed 2026-11-21.
* [Official X-Trainer-LeIsaac repository and usage](https://github.com/embodied-dobot/x-trainer), reviewed 2026-11-21.
* [DOBOT X-Trainer Lightweight Base manual V1.6](../dobot-x-trainer-lightweight-base-user-guide.md), 2026-02-05; different base scope.

**Documentation:** source-informed draft. **Software execution:** not run. **Hardware validation:** not run. Offline/simulator results stated here are expected outcomes, not observed logs. Do not transfer an untested simulator policy to the physical Nova 2 arms without DOBOT-approved integration, collision/safety verification and supervised trials.
