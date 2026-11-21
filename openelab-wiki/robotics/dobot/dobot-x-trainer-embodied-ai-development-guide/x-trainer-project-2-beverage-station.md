---
description: >-
  Model-scoped X-Trainer embodied-AI educational project with reproducible
  offline/simulation checkpoint, source links and hardware validation
  requirements.
---

# Project 2 — X-Trainer Intelligent Beverage Station

{% hint style="info" %}
[**View DOBOT X-Trainer Dual-Arm Robot for AI Data Collection on OpenELAB**](https://openelab.io/products/dobot-x-trainer-data-robot)

**Product:** DOBOT X-Trainer · **SKU:** `DOBOT-8000000050` · **Sold kit:** two master hands, two slave grippers, three depth cameras, fixed base; **two Nova 2 robot arms and training PC not included**
{% endhint %}

[Return to X-Trainer course index](./) · [Existing Lightweight Base V1.6 Manual](../dobot-x-trainer-lightweight-base-user-guide.md)

### Product overview

**Project 2 — Intelligent Beverage Station Robot** translates the course's three tasks into an incremental research exercise: **(1) force-controlled opening of sealed containers, (2) adaptive pouring of viscous liquids, (3) handling and placement of flexible containers.** The final course outcome is a beverage-preparation sequence; the uploaded guide does **not** contain a validated X-Trainer beverage policy, force sensor specification or manipulator code.

Start with **empty, inert, unsealed props** and a dry or water-free simulated setup. Pressurized containers, hot liquids, food safety and force-controlled seal opening demand separate tooling, hardware validation and risk review.

### Applications

* Bimanual teleoperated demonstrations and action annotations.
* Object-relative grasp/pose planning and approach/retreat trajectories.
* Visual estimation of tilt and fill state in a simulator.
* Flexible-container support and error recovery in a supervised academic test cell.

### Specifications

| Item                          | Dependency / scope                                                                               |
| ----------------------------- | ------------------------------------------------------------------------------------------------ |
| Master control                | Two 6-DoF master hands are included, subject to correct delivered hardware setup                 |
| Real robot actuation          | Two DOBOT Nova 2 arms **required but not included**                                              |
| End effectors                 | Two slave grippers included; confirm stroke/force and appropriate container grips                |
| Cameras                       | Three depth cameras included, actual model/calibration to confirm                                |
| Force-control feedback        | **Not established** by storefront/course as a native force sensor or validated force-control API |
| Open-source simulator example | [X-Trainer Lift Cube](https://github.com/embodied-dobot/x-trainer), **not** a beverage task      |
| Nominal operating/data rates  | 25 Hz product interface vs 30 Hz simulation recording; not guaranteed closed-loop force rate     |

### Hardware and connections

1. Begin with nonpressurized, lightweight, rigid containers and a soft **dummy pouch**; keep caps unlocked and no liquids near electronics.
2. Confirm gripper suitability for compliant materials and ensure the two arms cannot collide with each other.
3. For actual experiments, source two Nova 2 arms plus PC, verify robot firmware, gripper integration, E-stops, excluded workspace, correct fixed-base assembly and camera calibration.
4. Do not infer that opening a seal is safe or available merely because a motion controller supports gripping. Real force-aware opening requires measured contact/torque/force feedback, constraints and a separately approved fixture.
5. Keep pressing/pouring stages disabled until there is a verified stop procedure and spill containment.

### Software and development resources

The [official X-Trainer repository](https://github.com/embodied-dobot/x-trainer) provides a **general bimanual simulation and dataset pipeline**, not a ready-made liquid simulator. The [DOBOT Lightweight Base V1.6 manual](../dobot-x-trainer-lightweight-base-user-guide.md) describes master-slave synchronization, recording controls and data processing for its compatible hardware revision. A separate simulation environment, object geometry/physical properties, camera drivers and datasets must be added for beverage tasks.

### Getting started

#### Task 1 — Task and object analysis

Prepare three task cards: **open** (cap/contact state), **pour** (source/target positions and tilt), **place flexible container** (deformation and support). For each, record states, allowed tool contact, required feedback, success/abort criteria, object mass and expected failure modes. Clearly mark the actual DOBOT-supported and custom-developed portions.

#### Task 2 — First working result: offline behavior gate

The following is a **pure Python example**, not a robot controller. Thresholds are instructional fixtures, not validated force limits:

```python
def beverage_action(phase, operator_ok, pose_valid, contact_valid, spill):
    if not operator_ok or not pose_valid or spill:
        return "HOLD"
    if phase == "open":
        return "DRY_RUN" if contact_valid else "HOLD"
    if phase in ("tilt", "place"):
        return "DRY_RUN"
    return "HOLD"

assert beverage_action("open", True, True, False, False) == "HOLD"
assert beverage_action("tilt", True, True, True, False) == "DRY_RUN"
assert beverage_action("place", True, False, True, False) == "HOLD"
assert beverage_action("tilt", True, True, True, True) == "HOLD"
```

**Expected result:** assertions pass and unapproved/invalid/spill states block transitions. **DRY\_RUN is only an offline label**; it does not authorize motor commands.

#### Task 3 — Record the relevant demonstrations

After physical setup is separately commissioned, collect supervised **dry** demonstrations of object approach, both-hand support, mock cap rotation, gradual tilt and placement. The **Lightweight Base** manual describes yellow unlock/sync, green recording, indicator states and a required manufacturer script sequence. Only apply that sequence when the hardware/software match has been verified. Record RGB/depth, joint/pose, gripper status, phase labels, success/failure and timestamps.

#### Task 4 — Evaluate and extend

In simulation first, compare target/actual container pose, simulated fluid trajectory if supported by the chosen physics engine, grip slip and task aborts. Only after explicit review add **non-hot, nonpressurized** real liquids in a spill-contained experiment. Report both failures and successful trials.

### Troubleshooting and FAQs

**Can X-Trainer natively do force-controlled sealed-container opening?** The course sets it as a goal; the provided public sources do not establish a validated force/torque sensor or opening policy. Specify and test the required contact feedback separately.

**The pouch slips from the gripper:** inspect verified gripper stroke/force, compliant fixture, grasp geometry and tool material. Do not increase force beyond manufacturer limits.

**The simulator has no liquid model:** its public example is Lift Cube, not a fluid task; use a separately selected/verified simulator rather than claiming the official scene handles liquids.

### Downloads and technical documents

* [Official X-Trainer simulation and data pipeline](https://github.com/embodied-dobot/x-trainer).
* [OpenELAB product packing list](https://openelab.io/products/dobot-x-trainer-data-robot).
* [Lightweight Base V1.6 teleoperation/recording instructions](../dobot-x-trainer-lightweight-base-user-guide.md).

**Student deliverable:** task-state diagrams, offline control-gate tests, safety/fixture requirements and—if fully commissioned—an annotated, supervised dry demonstration dataset.

### Course navigation

[Previous project](x-trainer-project-1-simulation-sim2real.md) · [Continue to Project 3](x-trainer-project-3-waste-sorting.md)

### References and validation

* DOBOT, _Embodied AI Data Acquisition and Application Practice_, Educational Tutorial Guide **V2.0, 2026-09-15** (provided course outline), corresponding project.
* [OpenELAB DOBOT X-Trainer product listing](https://openelab.io/products/dobot-x-trainer-data-robot), reviewed 2026-11-21.
* [Official X-Trainer-LeIsaac repository and usage](https://github.com/embodied-dobot/x-trainer), reviewed 2026-11-21.
* [DOBOT X-Trainer Lightweight Base manual V1.6](../dobot-x-trainer-lightweight-base-user-guide.md), 2026-02-05; different base scope.

**Documentation:** source-informed draft. **Software execution:** not run. **Hardware validation:** not run. Offline/simulator results stated here are expected outcomes, not observed logs. Do not transfer an untested simulator policy to the physical Nova 2 arms without DOBOT-approved integration, collision/safety verification and supervised trials.
