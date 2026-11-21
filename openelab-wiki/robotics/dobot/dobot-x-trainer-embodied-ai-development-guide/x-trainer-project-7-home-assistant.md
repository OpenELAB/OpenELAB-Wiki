---
description: >-
  X-Trainer embodied AI course project: scope, hardware requirements, runnable
  offline/simulation tests and conditional physical validation.
---

# Project 7 — X-Trainer Intelligent Home Assistant

{% hint style="info" %}
[**View DOBOT X-Trainer Dual-Arm Robot for AI Data Collection on OpenELAB**](https://openelab.io/products/dobot-x-trainer-data-robot)

**Model:** DOBOT X-Trainer · **OpenELAB SKU:** `DOBOT-8000000050` · **Kit:** 2 master hands, 2 grippers, 3 depth cameras, fixed base · **Not included:** Nova 2 collaborative arms ×2 and host PC
{% endhint %}

[Back to X-Trainer development guide](./) · [Manufacturer Lightweight Base V1.6 manual in OpenELAB Wiki](../dobot-x-trainer-lightweight-base-user-guide.md)

### Product overview

**Project 7 — Intelligent Home Assistant** is the course capstone, combining **Task 1: household object sorting**, **Task 2: specified pick-and-place**, **Task 3: multi-step assistance**, and **Task 4: complete system integration**. The supported X-Trainer starting point is a **stationary dual-arm teaching cell** with separately sourced Nova 2 robots, not a mobile home robot able to drive between rooms.

The intended result is a modular end-to-end **Perception → Human Demonstration → Dataset → Skill Policy → Test → Supervised Action** system. The open-source project provides the **Lift Cube** foundation, not an installed autonomous home-assistant policy.

### Applications

* Bimanual sorting of clean household props on a fixed table.
* Human-demonstrated pick-and-place skill data capture.
* Integrating calibrated vision, task planning, action authorization and trajectory simulation.
* Training/evaluating a simple imitation-learning policy and identifying its failure modes.

### Specifications

| Component                | Current scope / constraint                                                                                                  |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------- |
| Cell                     | X-Trainer master hands, two grippers, three depth cameras and fixed base                                                    |
| Physical follower robots | Nova 2 arms ×2 **required, not included**                                                                                   |
| Host                     | Computer/GPU **not included**                                                                                               |
| Data                     | X-Trainer-LeIsaac **30 Hz** simulated HDF5 and LeRobot conversion                                                           |
| Physical demonstration   | Lightweight Base V1.6 manual describes master/arm synchronization and recording; fixed-base compatibility must be confirmed |
| Policy training          | Simulator supports model evaluation with a separate LeRobot inference server; not a guarantee of real hardware deployment   |
| Task mobility            | **Stationary tabletop**. No autonomous household navigation provided                                                        |
| Supported props          | Lightweight inert objects only; avoid powered appliances, medicines, food handling hazards and unknown items                |

### Hardware and connections

1. Arrange a safe, limited two-arm workspace with **clear source and target trays** and low-mass inert household props.
2. Identify the sold fixed-base revision and **exact physical follower arms, grippers, cameras and training host**; do not use the old Lightweight Base power/wiring layout without confirmation.
3. Verify physical robot stop behavior before a real teleoperation session. Keep synchronized hand/arm control **disabled** until the safety checklist is complete.
4. Create a coordinate-frame registry for each camera, arm and tray with actual calibration; the simulator's virtual 69° RGB cameras do not substitute for physical depth intrinsics.
5. Do not let a speech model, object classifier or VLA output publish unreviewed physical motor commands.

### Software and development resources

* [X-Trainer-LeIsaac](https://github.com/embodied-dobot/x-trainer): simulated keyboard/leader operation and multi-view capture; **`scripts/convert/isaaclab2lerobot\_xtrainer.py`** for data conversion.
* [LeIsaac](https://lightwheelai.github.io/leisaac/): simulator dependencies.
* [Lightweight Base V1.6 manual](../dobot-x-trainer-lightweight-base-user-guide.md): physical master/slave recording, dataset preprocessing and algorithm training for that hardware version; the **Dobot\_Xtrainer** demo project is distinct from **X-Trainer-LeIsaac**.
* Each of the earlier six project tutorials provides an individual scene, dataset or safety-gate building block.

### Getting started

#### Task 1 — Define an integrated home-object task

Choose a **single table** containing three safe object categories and two target trays. Define allowed operator requests, which hand owns which workspace, object/pose confidence requirements, stop authority and explicit failure recovery.

#### Task 2 — First working result: offline multi-step task controller

```python
ALLOWED_TASKS = {
    "organize": ("observe", "classify", "localize", "pick", "place", "verify"),
    "fetch_prop": ("observe", "localize", "pick", "place", "verify"),
}
def plan(request, operator_enabled, calibrated, object_present):
    if not operator_enabled or not calibrated or not object_present:
        return ("HOLD",)
    return ALLOWED_TASKS.get(request, ("REJECT",))

assert plan("organize", True, True, True)[0] == "observe"
assert plan("fetch_prop", True, False, True) == ("HOLD",)
assert plan("use_stove", True, True, True) == ("REJECT",)
assert plan("organize", False, True, True) == ("HOLD",)
```

**Expected result:** all assertions pass. The output is only a **software plan**, not a sequence of actual robot commands. A full implementation must validate each transition against actuator state, camera timestamps, collisions, stop conditions and measured errors.

#### Task 3 — Acquire and inspect demonstrations

After completing [Project 1](x-trainer-project-1-simulation-sim2real.md), record a small simulated **Lift Cube** dataset using the official keyboard workflow. Check actual HDF5 keys, trajectory lengths, image alignment, success/failure labels and commit. If recorded episodes are compatible, invoke the repository's documented converter from the configured project root:

```bash
python scripts/convert/isaaclab2lerobot_xtrainer.py
```

**Expected result:** converted dataset artifacts **only if** the required source path/configuration and dependencies are correctly supplied per the pinned repository. Do not present a successful conversion as a trained policy.

#### Task 4 — Training, evaluation and guarded integration

1. Split by episode/scene/object instance, preserving complete trajectories in one partition.
2. Train a small supervised imitation policy using your versioned software and data schema.
3. Evaluate success rate on **held-out simulations**, while separately logging intervention, false selection, drop, collision and policy timeout.
4. Check versioned LeRobot inference integration in the official README; only after an independent safety validation should a physical robot even be considered.
5. Compose an explicit **operator-authorized motion gateway**, collision checks and deterministic stop/fault states. Never route a raw LLM instruction directly to grippers/arms.

### Troubleshooting and FAQs

**A policy works in the simulator but misses objects in the lab:** inspect depth calibration, camera exposure, material friction, payload/grip and control latency (Sim2Real); simulation success is not evidence of safe physical manipulation.

**The planned action requests a location in another room:** reject it under the fixed-base scope. The supplied X-Trainer is a stationary data-collection cell, not a walking or wheeled household service platform.

**Why did my dataset converter fail?** Check actual HDF5 contents, repository commit, output paths, required libraries and LeRobot version before changing robot firmware.

**Is a full home-assistant model provided?** No. The V2.0 document defines a capstone project; the public X-Trainer repository demonstrates a dual-arm cube task and supporting data tools.

### Downloads and technical documents

* [Official X-Trainer simulated data and evaluation workflows](https://github.com/embodied-dobot/x-trainer).
* [X-Trainer product components and options](https://openelab.io/products/dobot-x-trainer-data-robot).
* [Existing DOBOT X-Trainer Lightweight Base manual](../dobot-x-trainer-lightweight-base-user-guide.md).

**Student deliverable:** integrated requirements, offline plan/rejection tests, one recorded/split simulation dataset, skill evaluation report and a clear boundary between safe simulator result and unverified physical deployment.

### Course navigation

[Previous project](x-trainer-project-6-assisted-living.md) · [Return to course index](./)

### References and validation

* DOBOT, _Embodied AI Data Acquisition and Application Practice_, Tutorial Guide **V2.0, 2026-09-15**, supplied educational outline.
* [OpenELAB X-Trainer exact sold configuration](https://openelab.io/products/dobot-x-trainer-data-robot), checked 2026-11-21.
* [Official X-Trainer-LeIsaac project](https://github.com/embodied-dobot/x-trainer), checked 2026-11-21.
* [DOBOT X-Trainer Lightweight Base User Guide V1.6](../dobot-x-trainer-lightweight-base-user-guide.md), 2026-02-05, **not automatically identical to the fixed-base SKU**.

**Source review:** documentation draft. **Software execution:** not run. **Hardware testing:** not run. The example code is explicitly **offline and does not command a robot**. Any physical use requires a documented exact-model setup, compatible Nova 2 arms, validated grippers/sensors, emergency-stop access and supervised bench testing.
