---
description: >-
  X-Trainer embodied AI course project: scope, hardware requirements, runnable
  offline/simulation tests and conditional physical validation.
---

# Project 4 — X-Trainer Precision Industrial Assembly

{% hint style="info" %}
[**View DOBOT X-Trainer Dual-Arm Robot for AI Data Collection on OpenELAB**](https://openelab.io/products/dobot-x-trainer-data-robot)

**Model:** DOBOT X-Trainer · **OpenELAB SKU:** `DOBOT-8000000050` · **Kit:** 2 master hands, 2 grippers, 3 depth cameras, fixed base · **Not included:** Nova 2 collaborative arms ×2 and host PC
{% endhint %}

[Back to X-Trainer development guide](./) · [Manufacturer Lightweight Base V1.6 manual in OpenELAB Wiki](../dobot-x-trainer-lightweight-base-user-guide.md)

### Product overview

**Project 4 — Precision Industrial Component Assembly** implements the course's learning sequence: **Task 1: precision component picking**, **Task 2: visual/pose alignment**, **Task 3: force-controlled assembly**. The complete educational chain is **Picking → Alignment → Assembly → Verification**.

The uploaded course describes desired skills, not an X-Trainer-ready industrial assembly controller. In particular, **a force-controlled insertion claim requires measured contact feedback, validated actuator interface, fixture compliance and collision protection**; the stock X-Trainer product listing does not establish a complete force/torque control solution.

### Applications

* Build pick-and-place training demonstrations for two Nova 2 manipulators.
* Align two lightweight teaching components using calibrated cameras and robot frames.
* Compare approaches with and without passive compliance in simulation.
* Analyze insertion error, failed contact and recovery using a structured dataset.

### Specifications

| Element             | Actual scope                                                                                                                                               |
| ------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Robot arms          | Two compatible DOBOT Nova 2 arms are **required but not included** with SKU DOBOT-8000000050                                                               |
| End effectors       | Two included grippers, tool mass, grip and opening limits to verify                                                                                        |
| Vision              | Three depth cameras in sold kit; model, depth scale and calibration must be confirmed                                                                      |
| Robot repeatability | Listed **±0.05 mm** for compatible robots, **not guaranteed assembled-part alignment**                                                                     |
| Force sensing       | External/verified sensor or control feedback necessary for force-aware tasks; **not specified as a provided accessory**                                    |
| Simulation          | Official [X-Trainer-LeIsaac Lift Cube](https://github.com/embodied-dobot/x-trainer) is a starting platform, not a finished connector-insertion environment |
| Industrial use      | Not certified by course objectives or simulation success                                                                                                   |

### Hardware and connections

1. Build a table fixture from **blunt, low-mass, nonenergized mock parts**; use passive compliance and alignment markers where appropriate. Do not use press-fit connectors, sharp parts, powered equipment or production machinery in the first experiment.
2. Document the camera-to-base calibration, tool-center-point (TCP), exact compatible robot limits and real collision envelope.
3. Keep the dual-arm and gripper actuators disabled until the alignment checker passes in simulation.
4. For a real test, perform an equipment-level safety review: emergency-stop devices, gripper limits, collision/force limits, fixture stiffness and human clearance.
5. The [Lightweight Base V1.6 installation details](../dobot-x-trainer-lightweight-base-user-guide.md) are **not proof** of identical fixed-base mechanical mount orientation, power connector or controller wiring.

### Software and development resources

* [Official X-Trainer-LeIsaac simulation and data capture](https://github.com/embodied-dobot/x-trainer): model and teleoperation architecture; extend its cube task only after pinning commit/physics settings.
* [LeIsaac framework and Isaac Lab](https://lightwheelai.github.io/leisaac/): simulation environment.
* [Existing DOBOT X-Trainer Lightweight Base V1.6 manual](../dobot-x-trainer-lightweight-base-user-guide.md): physical demonstration collection, training and inference workflow for compatible lightweight-base setup.

The course does not specify a supported force sensor brand, Nova 2 force-control API, fixture CAD, connector tolerance, or insertion controller. Require those individually before publishing a physical force-controlled assembly command.

### Getting started

#### Task 1 — Define the assembly tolerance stack

Sketch two nonsharp teaching parts: **pick part** and **receiving fixture**. Define camera calibration, target frame, approach vector, fixture clearance, arm/tool envelope and a tool/no-tool collision check. Measure allowed clearances for the actual objects rather than copying the robot's repeatability rating.

#### Task 2 — First working result: offline alignment gate

The following gate uses **example classroom tolerances only**; it makes no robot movement request:

```python
def assembly_gate(dx_mm, dy_mm, theta_deg, contact_valid, operator_ok):
    # Illustrative unit tests, NOT manufacturer insertion limits.
    if not operator_ok or not contact_valid:
        return "HOLD"
    aligned = abs(dx_mm) <= 1.0 and abs(dy_mm) <= 1.0 and abs(theta_deg) <= 2.0
    return "SIMULATE_INSERT" if aligned else "REALIGN"

assert assembly_gate(0.3, -0.5, 1.0, True, True) == "SIMULATE_INSERT"
assert assembly_gate(2.0, 0.0, 0.0, True, True) == "REALIGN"
assert assembly_gate(0.0, 0.0, 0.0, False, True) == "HOLD"
assert assembly_gate(0.0, 0.0, 0.0, True, False) == "HOLD"
```

**Expected result:** all assertions pass. The code verifies unit handling, alignment and an operator/contact hold condition. **SIMULATE\_INSERT is a label, not a motor command**; these arbitrary thresholds are not prescribed hardware limits.

#### Task 3 — Simulate pick, align and insert

1. Use the official simulator's **dual-arm model** to create a mock component and fixture.
2. Define collision meshes, frames and object mass; record the exact updated scene/configuration.
3. Use a generated or supervised simulated demonstration to approach, grasp, place above fixture and align.
4. Allow insertion **only in the simulator**, compare commanded and simulated poses; record collisions and invalid force/contact cases.
5. Collect images, gripper state, joint positions, action sequences and annotated task phases; retain failed episodes.

#### Task 4 — Plan physical validation separately

Before trying real insertion, obtain verified Nova 2/gripper firmware pair, force-sensor calibration (if available), TCP and extrinsics, compliance characteristics and approved limits. Progress through **stationary camera calibration → empty-hand dry run → lightweight mock-part pickup → approach without contact → contact test → insertion**, each requiring supervisor permission and independent stop checks. Do not use real industrial parts or uncontrolled force from a generic model.

### Troubleshooting and FAQs

**The vision system reports alignment but the part jams:** verify camera/tool transforms, compliance, actual fixture clearance and contact feedback; do **not** retry with greater force by default.

**Can the listed ±0.05 mm repeatability be used as assembly tolerance?** No. Repeat positioning under defined conditions is not camera/fixture accuracy or end-to-end insertion success.

**Is a six-axis force sensor included?** The retail package does not establish one; the course's force-control topic is a design objective requiring a documented compatible sensing/control mechanism.

### Downloads and technical documents

* [X-Trainer-LeIsaac source and dual-arm model](https://github.com/embodied-dobot/x-trainer).
* [X-Trainer SKU and supplied components](https://openelab.io/products/dobot-x-trainer-data-robot).
* [Lightweight Base manual and collected-data pipeline](../dobot-x-trainer-lightweight-base-user-guide.md).

**Student deliverable:** part/fixture specification, frame and tolerance diagram, offline alignment test, a simulated pick–align–place sequence, and an explicit list of blocked physical force-control requirements.

### Course navigation

[Previous project](x-trainer-project-3-waste-sorting.md) · [Continue to Project 5](x-trainer-project-5-agricultural-harvesting.md)

### References and validation

* DOBOT, _Embodied AI Data Acquisition and Application Practice_, Tutorial Guide **V2.0, 2026-09-15**, supplied educational outline.
* [OpenELAB X-Trainer exact sold configuration](https://openelab.io/products/dobot-x-trainer-data-robot), checked 2026-11-21.
* [Official X-Trainer-LeIsaac project](https://github.com/embodied-dobot/x-trainer), checked 2026-11-21.
* [DOBOT X-Trainer Lightweight Base User Guide V1.6](../dobot-x-trainer-lightweight-base-user-guide.md), 2026-02-05, **not automatically identical to the fixed-base SKU**.

**Source review:** documentation draft. **Software execution:** not run. **Hardware testing:** not run. The example code is explicitly **offline and does not command a robot**. Any physical use requires a documented exact-model setup, compatible Nova 2 arms, validated grippers/sensors, emergency-stop access and supervised bench testing.
