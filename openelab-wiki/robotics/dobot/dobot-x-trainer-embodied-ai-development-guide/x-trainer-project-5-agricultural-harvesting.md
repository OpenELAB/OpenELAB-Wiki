---
description: >-
  X-Trainer embodied AI course project: scope, hardware requirements, runnable
  offline/simulation tests and conditional physical validation.
---

# Project 5 — X-Trainer Agricultural Harvesting

{% hint style="info" %}
[**View DOBOT X-Trainer Dual-Arm Robot for AI Data Collection on OpenELAB**](https://openelab.io/products/dobot-x-trainer-data-robot)

**Model:** DOBOT X-Trainer · **OpenELAB SKU:** `DOBOT-8000000050` · **Kit:** 2 master hands, 2 grippers, 3 depth cameras, fixed base · **Not included:** Nova 2 collaborative arms ×2 and host PC
{% endhint %}

[Back to X-Trainer development guide](./) · [Manufacturer Lightweight Base V1.6 manual in OpenELAB Wiki](../dobot-x-trainer-lightweight-base-user-guide.md)

### Product overview

**Project 5 — Agricultural Fruit and Vegetable Harvesting** covers **Task 1: recognition/localization in complex environments**, **Task 2: gentle grasp/detachment**, and **Task 3: vibration suppression/transport**. The source envisions harvesting, but the delivered X-Trainer is a **stationary dual-arm data-collection cell**, not an outdoor mobile harvester or an agricultural robot with waterproof/dust-resistant equipment.

Teach recognition, occlusion and gentle manipulation indoors with **synthetic plants and soft training fruit**, then treat outdoor harvesting, stem cutting and field deployment as separate hardware/research projects.

### Applications

* Evaluate object detection amid leaves, variable lighting and occlusion.
* Study fragile-object manipulation and gripper contact geometry.
* Collect supervised demonstration trajectories for slow conveyance to a target tray.
* Compare simulated and observed vibration/object slip and define bruise-prevention evaluation.

### Specifications

| Requirement               | Grounded scope                                                                                            |
| ------------------------- | --------------------------------------------------------------------------------------------------------- |
| Platform                  | X-Trainer dual-arm lab cell with master hands, included grippers and cameras                              |
| Physical follower arms    | Nova 2 ×2 **required but not included**                                                                   |
| Vision                    | Three listed depth cameras, not a manufacturer-validated outdoor fruit perception system                  |
| End effector              | Standard slave grippers may need soft pads/specialized harvesting end effector; compatibility to validate |
| Force and stem detachment | No validated native harvesting force/stem-cutting controller is supplied                                  |
| Simulation                | Official repository provides **Lift Cube**, not fruit dynamics or vegetation physics                      |
| Environment               | Indoor supervised learning by default; outdoor agricultural operation not established                     |

### Hardware and connections

1. Use artificial produce or **soft foam objects**, and a tray or mock branch that can release without sharp blades or high force. Do **not** start with knives/cutters, powered harvesting equipment or unbounded pull force.
2. Photograph sample objects at different orientations and occlusion levels. Record lighting, target size, relative depth, surface slip and grip contact points.
3. Document actual gripper opening/payload/force specifications from the installed gripper manufacturer and Nova 2 firmware; don't assume gentle contact automatically.
4. Keep work volume inside the approved fixed-base workspace; build a stable catch tray under the object.
5. Never assume the **Lightweight Base** dimensions/wiring also apply to the sold fixed-base unit.

### Software and development resources

Use [X-Trainer-LeIsaac](https://github.com/embodied-dobot/x-trainer) for dual-arm simulation/episode recording, but define a **new simulated fruit object, compliant contacts and controlled detachment physics**. No off-the-shelf fruit task is documented in that repository. Use a separately versioned detector and, for physical data, only the authorized X-Trainer SDK matching the delivered cell.

### Getting started

#### Task 1 — Build recognition and graspability labels

For at least three mock fruit geometries, label bounding box, visible surface fraction, camera-relative depth, available approach direction and whether a **safe, collision-free grasp** exists. Label occluded objects as _not evaluated_ unless a robust depth estimate is available.

#### Task 2 — First working result: offline conservative grasp selection

The following test uses **synthetic educational thresholds, not validated grip force limits**:

```python
def harvest_plan(depth_valid, visible_fraction, object_supported, tool_ok):
    if not all((depth_valid, object_supported, tool_ok)):
        return "HOLD"
    if not (0.0 <= visible_fraction <= 1.0):
        return "HOLD"
    return "SIMULATE_GRASP" if visible_fraction >= 0.75 else "REOBSERVE"

assert harvest_plan(True, 0.90, True, True) == "SIMULATE_GRASP"
assert harvest_plan(True, 0.30, True, True) == "REOBSERVE"
assert harvest_plan(False, 0.90, True, True) == "HOLD"
assert harvest_plan(True, 0.90, False, True) == "HOLD"
```

**Expected result:** all assertions pass. **SIMULATE\_GRASP** is only an offline permission label. No physical joint or gripper motion is sent.

#### Task 3 — Teleoperated synthetic harvesting sequence

1. In a verified simulator add an artificial fruit/branch object and end-effector collision geometry.
2. Design states **observe → approach → cradle → release from fixture → stabilize → place in tray → verify**.
3. Use keyboard or calibrated leader-arm-to-simulator demo; record joint, RGB, object pose, contact events and actual simulated sequence.
4. Compare gentle versus sudden transport trajectories in the simulated physics; do not claim measured physical bruise or loss rates.
5. For a fully commissioned lab, perform only **slow, supervised mock-fruit pick/transport** with verified gripping limits and physical stops; do not introduce live stem detachment without separate fixture/force analysis.

#### Task 4 — Evaluate carefully

Report object recognition precision/recall, valid pose rate, complete mock detach rate, dropped objects, peak measured acceleration (if a calibrated sensor exists), collision events, and correct placement. Use actual denominators and include failures.

### Troubleshooting and FAQs

**The detector recognizes the object but its 3D target is invalid:** check occlusion, depth confidence/scale, intrinsics and extrinsics; do not guess missing depth from the RGB box alone.

**The mock fruit is crushed or slips:** stop, review actual gripper limits, pad geometry, path acceleration and object material. Do not increase grip force without validated bounds.

**Can X-Trainer operate as an autonomous outdoor harvester?** Not based on the sold fixed-base system or course outline. It is a research training cell; field use requires a different mobile/environmental integration and safety review.

### Downloads and technical documents

* [Official X-Trainer simulation/dataset source](https://github.com/embodied-dobot/x-trainer).
* [OpenELAB X-Trainer hardware scope](https://openelab.io/products/dobot-x-trainer-data-robot).
* [Existing Lightweight Base manual](../dobot-x-trainer-lightweight-base-user-guide.md).

**Student deliverable:** annotated mock-produce dataset, offline graspability tests, simulated picking/placement trial and an experimental protocol for contact/transport monitoring.

### Course navigation

[Previous project](x-trainer-project-4-precision-assembly.md) · [Continue to Project 6](x-trainer-project-6-assisted-living.md)

### References and validation

* DOBOT, _Embodied AI Data Acquisition and Application Practice_, Tutorial Guide **V2.0, 2026-09-15**, supplied educational outline.
* [OpenELAB X-Trainer exact sold configuration](https://openelab.io/products/dobot-x-trainer-data-robot), checked 2026-11-21.
* [Official X-Trainer-LeIsaac project](https://github.com/embodied-dobot/x-trainer), checked 2026-11-21.
* [DOBOT X-Trainer Lightweight Base User Guide V1.6](../dobot-x-trainer-lightweight-base-user-guide.md), 2026-02-05, **not automatically identical to the fixed-base SKU**.

**Source review:** documentation draft. **Software execution:** not run. **Hardware testing:** not run. The example code is explicitly **offline and does not command a robot**. Any physical use requires a documented exact-model setup, compatible Nova 2 arms, validated grippers/sensors, emergency-stop access and supervised bench testing.
