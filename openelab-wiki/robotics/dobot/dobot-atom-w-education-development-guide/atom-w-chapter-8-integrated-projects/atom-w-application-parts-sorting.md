---
description: >-
  ATOM-W capstone project tutorial: source-mapped objectives, required
  edition/hardware, reproducible offline prototype, and validation gates.
---

# Application 8.3 — ATOM-W Automotive Parts Sorting

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (Standard verified; Education SKU not verified) · **Edition scope:** Education includes two dexterous hands and wrist cameras; Standard requires separately verified optional grasp hardware
{% endhint %}

[ATOM-W curriculum index](../) · [Chapter 8 — system integration](./) · [ATOM-W User Guide V1.0](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html)

### Product overview

**Application 8.3: Automotive Parts Sorting.** The source course combines (1) automotive part recognition, (2) position estimation, (3) grasp strategy, (4) classification/placement and (5) integrated system testing. Build this as a **small training-cell prototype**, not a production conveyor integration. On ATOM-W, the Education Version is the natural reference because it includes dexterous hands/wrist depth cameras; Standard requires separately sourced compatible grasp hardware.

### Applications

* Recognizing and classifying non-hazardous sample automotive parts.
* Estimating object pose and selecting a reachable left/right arm.
* Executing a simulated pick-and-place sequence with an explicit unknown-part bin.
* Recording classification, localization and grasp/placement quality as separate metrics.

### Specifications

| Item                 | Requirement and constraint                                                                                   |
| -------------------- | ------------------------------------------------------------------------------------------------------------ |
| Platform             | ATOM-W wheel-base locked/parked for bench sorting                                                            |
| Vision               | Head depth/binocular, plus optional Edition-specific wrist depth                                             |
| Grasp tool           | Requires actually installed hand/gripper; Education includes two six-DoF hands                               |
| Motion model         | W-P3 arms-only simulation, W-specific joint/limits/frames                                                    |
| Part classes         | Lab-defined samples, not manufacturer-recognized built-in categories                                         |
| Safety               | Fixed training objects, clear workspace and operator stop                                                    |
| Industrial readiness | Not established; guarding, standards, PLC/conveyor interface and production validation are separate projects |

### Hardware and connections

1. Select a shallow tray with **light, non-sharp, non-energized training parts** and labeled bins. Do not use unguarded real industrial tooling/conveyors.
2. Confirm robot edition, gripper compatibility, safe fixture/mount, camera calibration and load limits. Keep wheels secured and speed/arm authority under operator review.
3. Establish actual `camera → base → arm → tool` transforms from the W-P3 model and calibrations. Do not infer grasp coordinates from photos.
4. Check and record the ATOM-W V1.0 emergency-stop and physical workspace clearance.
5. Isolate people and reconfigure only in a known safe robot state.

### Software and development resources

* [Chapter 2 — Perception](../atom-w-chapter-2-perception-systems.md) — object detection and metric geometry.
* [Chapter 3 — Motion planning](../atom-w-chapter-3-motion-control-planning.md) — arm/world frames and IK concepts.
* [Chapter 4 — Data recording](../atom-w-chapter-4-data-acquisition.md) — timestamps, provenance and outcomes.
* [Chapter 7 — Teleoperation/simulation](../atom-w-chapter-7-kinematics-teleoperation.md) — W-P3 arms-only motion.
* [ATOM-W model SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) — model joint tables.
* [ATOM-W V1.0 manual](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) — end flange/hand options.

### Getting started

#### Task 1 — Define the dataset

Choose three visibly distinguishable **teaching classes** (e.g., washer, plastic connector, metal bracket), plus `unknown`. Image-label examples under different lighting, rotations and partial occlusion; record exact class names and training/test split by object instance.

#### Task 2 — First working result: offline classification and bin routing

```python
BINS = {
    "washer": "bin_A",
    "connector": "bin_B",
    "bracket": "bin_C",
}
def choose_bin(label, confidence, enabled):
    if not enabled or confidence < 0.90:
        return "review"
    return BINS.get(label, "review")

assert choose_bin("washer", 0.95, True) == "bin_A"
assert choose_bin("washer", 0.70, True) == "review"
assert choose_bin("bolt", 0.99, True) == "review"
assert choose_bin("bracket", 0.99, False) == "review"
print("Offline sorter routing tests passed")
```

**Expected result:** all tests pass. The **0.90 threshold is an illustrative software test constant, not a validated confidence setting**. There is no camera model or robot motion in this program.

#### Task 3 — Simulated perception to placement

1. Use annotated images to obtain class and detector confidence with a recorded model version.
2. Determine actual object center/orientation with calibrated camera parameters; reject stale, occluded or out-of-range targets.
3. Transform to W-P3 arm frame, compute a collision-checked pose and supported grasp strategy.
4. Dry-run in `ros2 launch atom\_gazebo atom\_arms\_only.launch.py` using a simulated tool/object model appropriate to the installed hand.
5. Evaluate arm reach and safe bin placement with controlled separation. Do not automatically send the simulator trajectory to hardware.

#### Task 4 — Supervised physical test and evaluation

Only after manufacturer compatibility and safety review, perform bounded single-object trials with an operator and physical stop. Count: total samples, correctly classified, valid 3D localizations, feasible IK solutions, successful picks, correct placements, partial failures and interventions. Report **precision/recall** separately from grasp and sorting success; include all unsuccessful attempts. No performance figures are assumed.

### Troubleshooting and FAQs

**A part is recognized but cannot be picked:** check 3D depth scale, tool reach, gripper opening, hand contact pose and collision constraints before changing motor commands.

**Different classes collide in one bin:** inspect class mapping, bin coordinate calibration and per-class rules. A high model confidence is not a safe placement condition.

**Can Standard Edition follow this project out of the box?** Not for physical grasping: Standard does not include hands; you need a compatible fitted and documented gripper or Education hardware.

**Is an automotive production line supported by the course?** No. The source specifies an educational sorting project; an industrial cell needs guarded hardware, controls, commissioning and separate certification.

### Downloads and technical documents

* [OpenELAB ATOM-W Standard/Education packing list](https://openelab.io/products/dobot-atom-w-wheeled-humanoid).
* [ATOM-W SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [ATOM-W end-effector and flange manual](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html).
* [ATOM W-P3 ROS 2/Gazebo](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md).

**Student deliverable:** labeled part dataset, offline routing tests, simulated grasp-place sequence and a structured evaluation sheet. Physical sorting remains conditional on documented hardware validation.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, V2.0 (2026-09-15), Chapter 8 application outline, user-provided document.
* [OpenELAB ATOM-W product listing, Standard and Education configurations](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [ATOM-W User Guide V1.0, 2026-08-07](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html), DOBOT-authored manual mirrored online.
* [ATOM SDK Application Development Guide V2.1, 2026-08-26](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [Official DOBOT Atom ROS 2 repository](https://github.com/Dobot-Arm/dobot_atom_ros2), W-P3 model.

**Source review:** completed for draft planning. **Software execution:** not run. **Physical robot tests:** not run. No detection, localization, grasp success rate or autonomy performance is claimed here. All live movement requires site-specific physical validation and supervision.
