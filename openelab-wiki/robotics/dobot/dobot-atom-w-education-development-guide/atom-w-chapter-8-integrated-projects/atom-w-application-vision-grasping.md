---
description: >-
  ATOM-W capstone project tutorial: source-mapped objectives, required
  edition/hardware, reproducible offline prototype, and validation gates.
---

# Application 8.2 — ATOM-W Vision-Based Grasping

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (Standard verified; Education SKU not verified) · **Edition scope:** Education includes two dexterous hands and wrist cameras; Standard requires separately verified optional grasp hardware
{% endhint %}

[ATOM-W curriculum index](../) · [Chapter 8 — system integration](./) · [ATOM-W User Guide V1.0](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html)

### Product overview

**Application 8.2: Humanoid Robot Vision-Based Grasping.** The course includes (1) target object recognition, (2) 3D localization, (3) grasp-pose estimation, (4) arm motion and (5) task testing. On ATOM-W, a grasp requires **a physically installed compatible hand/gripper**. The **Education Version** lists two six-DoF hands and two wrist-mounted depth cameras; the **Standard Version has no included dexterous hands**.

The first result is a **calibrated-geometry calculation in software**, not a proven grasp.

### Applications

* Camera coordinate reconstruction and 3D object localization.
* Reachability/collision analysis for a 7-DoF arm and configured tool.
* Hand/gripper selection, approach–grasp–retract–place task planning.
* Evaluating robustness to object pose, occlusion, lighting and depth errors.

### Specifications

| Subsystem            | ATOM-W scope                                                                                          |
| -------------------- | ----------------------------------------------------------------------------------------------------- |
| Arm                  | Two seven-DoF arms, 600 mm listed reach without hands                                                 |
| Rated arm payload    | 3.5 kg **per arm** according to product listing; account for tool and dynamic load                    |
| Tool                 | Standard: no included hands; Education: two 6-DoF dexterous hands                                     |
| Wrist depth          | Two included on Education; Standard wrist-depth not included                                          |
| Head perception      | Depth camera and binocular camera on base system                                                      |
| Flange/hand mounting | Exact ATOM-W V1.0 end flange and installed hand drawings required                                     |
| ROS 2 simulation     | ATOM W-P3 arms-only Gazebo model                                                                      |
| Calibration          | Camera intrinsic/extrinsic, hand-eye and tool-center point are **not** supplied by the course outline |

The product-listed **±0.05 mm arm repeat positioning accuracy** is **not** an end-to-end visual grasp accuracy claim. Do not infer grasp success, torque or safe gripping force from it.

### Hardware and connections

1. Confirm the **ordered edition** and actual installed end effectors. Obtain tool mass, supported mounting bolts, communication/power and finger limits from the correct hardware document.
2. Choose a light, inert, blunt training object on a stable table, keeping hands clear and the chassis stationary.
3. Inspect and calibrate head/wrist camera frame, depth scale and camera-to-robot transform. Disable real movement for first geometry test.
4. Confirm the operator's stop access and current ATOM-W state; no automatic grasp in this first tutorial.
5. Avoid unsafe manual probing of motor wiring and do not bypass hand-force or joint limits.

### Software and development resources

* [SDK V2.1 ATOM\_W joint order, bounds and interfaces](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [ATOM-W V1.0 hand/flange compatibility](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html).
* [W-P3 arm simulation](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md).
* [Official ROS 2 hand-state controller examples](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_control_examples/README.md) — **control examples can move fingers**; inspect source and use read-only tests first.

### Getting started

#### Task 1 — First working result: offline camera point reconstruction

Use **synthetic calibrated intrinsics**, not unknown onboard calibration:

```python
def pixel_to_point_m(u, v, depth_m, fx, fy, cx, cy):
    if depth_m <= 0 or min(fx, fy) <= 0:
        raise ValueError("Calibration or depth invalid")
    return ((u-cx)*depth_m/fx, (v-cy)*depth_m/fy, depth_m)

point = pixel_to_point_m(400, 240, 0.8, 600, 600, 320, 240)
assert round(point[0], 6) == round(0.8*80/600, 6)
assert point[1] == 0 and point[2] == 0.8
print("point in synthetic camera frame (m):", point)
```

**Expected result:** a 3D camera-frame point and passing assertions. This is a mathematical fixture only; the calibration constants are **not ATOM-W values** and cannot guide physical arm motion.

#### Task 2 — Prepare real model transforms

1. Obtain camera matrix, correct depth units, undistortion and time-aligned RGB/depth.
2. Calibrate camera-to-`base\_link` and `base\_link`-to-tool transforms using **actual installed ATOM-W model frames**.
3. Estimate object center and orientation with confidence and uncertainty; reject missing/invalid depths.
4. Convert into the arm's tool frame, then check reach, joint limits and self/environment collisions.
5. Use W-P3 Gazebo arms-only mode for trajectory planning/verification before moving the physical robot.

#### Task 3 — Grasp-pose and motion design

For the verified hand/gripper, choose pre-grasp pose, approach direction, grasp orientation, closure force/position and retreat pose. Simulate sequence and recovery after grasp failure. Obtain manufacturer hand API, required finger calibration, grasp limits, tool load and stop behavior for the delivered edition; **none are defined by the uploaded course outline**.

#### Task 4 — Grasp experiment reporting

When a lab-approved physical protocol is available, record each trial: object ID, calibration, recognition, pose error, IK feasibility, contact outcome, slip/drop and human intervention. Keep failed trials, and report completed grasps divided by attempted grasps with conditions.

### Troubleshooting and FAQs

**The object is detected but IK fails:** verify actual tool transforms, camera calibration, W-specific joint bounds, end-effector offset and collision scene.

**The SDK reads arm state but no fingers exist:** confirm edition and installed hand before opening a `/hands/state`/command interface.

**The depth-based pose changes when the camera moves:** check dynamic camera transform, timestamps and extrinsic calibration.

### Downloads and technical documents

* [ATOM-W manual — flange/hand mounting diagrams](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html).
* [ATOM SDK V2.1 model/joint specifications](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [ATOM W-P3 arms-only simulation](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md).

**Student deliverable:** depth-to-3D calculation, documented calibration plan, simulated grasp trajectory and measured manipulation-test protocol. **Not supplied:** validated full ATOM-W grasp pipeline.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, V2.0 (2026-09-15), Chapter 8 application outline, user-provided document.
* [OpenELAB ATOM-W product listing, Standard and Education configurations](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [ATOM-W User Guide V1.0, 2026-08-07](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html), DOBOT-authored manual mirrored online.
* [ATOM SDK Application Development Guide V2.1, 2026-08-26](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [Official DOBOT Atom ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2), W-P3 model.

**Source review:** completed for draft planning. **Software execution:** not run. **Physical robot tests:** not run. No detection, localization, grasp success rate or autonomy performance is claimed here. All live movement requires site-specific physical validation and supervision.
