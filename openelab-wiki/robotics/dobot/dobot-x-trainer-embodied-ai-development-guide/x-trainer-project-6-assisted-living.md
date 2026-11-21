---
description: >-
  X-Trainer embodied AI course project: scope, hardware requirements, runnable
  offline/simulation tests and conditional physical validation.
---

# Project 6 — X-Trainer Healthcare and Assisted Living

{% hint style="info" %}
[**View DOBOT X-Trainer Dual-Arm Robot for AI Data Collection on OpenELAB**](https://openelab.io/products/dobot-x-trainer-data-robot)

**Model:** DOBOT X-Trainer · **OpenELAB SKU:** `DOBOT-8000000050` · **Kit:** 2 master hands, 2 grippers, 3 depth cameras, fixed base · **Not included:** Nova 2 collaborative arms ×2 and host PC
{% endhint %}

[Back to X-Trainer development guide](./) · [Manufacturer Lightweight Base V1.6 manual in OpenELAB Wiki](../dobot-x-trainer-lightweight-base-user-guide.md)

### Product overview

**Project 6 — Healthcare and Assisted-Living Robot** follows **Task 1: accurate retrieval of specified objects** and **Task 2: safe object delivery and handover**. Use this as a **nonclinical, tabletop assistance demonstration**, not a medical device or unsupervised patient-care robot. The X-Trainer listed product is a stationary training platform; it does **not** include an autonomous mobile base, medical certification or patient-monitoring equipment.

The course's “safe delivery” is a target for designing and evaluating an application—not an established manufacturer-certified safety function.

### Applications

* Interpret clear, pre-approved requests for ordinary non-medical objects.
* Find and localize objects using documented camera calibration.
* Create a supervised pick-and-place task with a **fixed recipient tray**, not direct human contact.
* Analyze handover consent, ambiguous commands, unrecognized users and lost perception.

### Specifications

| Dependency             | Current evidence                                                                                         |
| ---------------------- | -------------------------------------------------------------------------------------------------------- |
| Teleoperation platform | Two master hands/grippers/cameras/base supplied                                                          |
| Physical actuators     | Compatible Nova 2 ×2 **not included**                                                                    |
| Mobility               | Fixed-base data-collection cell, not a room-to-room delivery robot                                       |
| Perception             | Three depth cameras listed; user recognition, emotion or health-state interpretation is **not** provided |
| Gripping safety        | Requires installed gripper force limits, reach/collision validation and actual stop behavior             |
| Intended objects       | Light, inert, **non-medical training props**, not medication or clinical devices                         |
| Model inference        | Source repository provides Lift Cube simulation; not a clinical assistant model                          |

### Hardware and connections

1. Create a consent-aware setup with **two marked trays**: request origin and recipient handover tray, both inside a validated stationary robot workspace.
2. Use only **inert low-mass items**, e.g. a clean empty plastic bottle or foam cube. Do not retrieve, sort or dispense medicine, sharp objects, hot drinks or medical equipment.
3. Keep the human outside the robot reach during motion; **no direct person-to-robot hand contact** for the introductory experiment.
4. For any physical trial, check exact Nova 2, gripper, cameras, E-stop and supervised laboratory protections. The older Lightweight Base manual does not establish fixed-base wiring.
5. Record user consent and data-retention boundaries; avoid unnecessary face recognition or health inference.

### Software and development resources

* [DOBOT X-Trainer-LeIsaac](https://github.com/embodied-dobot/x-trainer) — dual-arm robot simulation and action/demonstration recording.
* [X-Trainer Lightweight Base V1.6](../dobot-x-trainer-lightweight-base-user-guide.md) — teleoperation/recording, only for matching revisions.
* A separately versioned speech/visual request interface is required if the course implementation moves beyond explicit typed, supervised commands.

### Getting started

#### Task 1 — Define the safety and delivery contract

List permissible requests, allowed items, request confirmation, tray coordinates, recipient confirmation, timeout, stopping condition and supervisor action. Keep a high-priority **abort and retract-to-safe-state** policy that does not depend solely on vision.

#### Task 2 — First working result: offline request-to-delivery gate

```python
ALLOWED = {"water_bottle_prop", "foam_cube", "towel_prop"}

def assist(request, object_located, supervisor_ok, tray_clear):
    if request not in ALLOWED:
        return "REJECT"
    if not supervisor_ok or not object_located or not tray_clear:
        return "HOLD"
    return "SIMULATE_PLACE_IN_TRAY"

assert assist("foam_cube", True, True, True) == "SIMULATE_PLACE_IN_TRAY"
assert assist("medication", True, True, True) == "REJECT"
assert assist("towel_prop", False, True, True) == "HOLD"
assert assist("water_bottle_prop", True, False, True) == "HOLD"
```

**Expected result:** permitted, validated props may reach a simulated _tray placement_ stage; medical or unknown requests are rejected. This code **does not drive a robot** and does not implement clinical handover.

#### Task 3 — Simulate retrieval and tray handover

1. Model a labeled object at an approved reachable origin and a marked empty recipient tray.
2. Confirm the object class and pose; reject occluded/missing depth.
3. Plan a collision-checked approach, grip, lift, transfer and release in the simulator.
4. Insert explicit _wait for supervisor_ and _tray clear_ checks.
5. Capture episode data and count misses, drop/slip events, operator interventions and placement errors.

#### Task 4 — Carefully scope a future physical test

Only if Nova 2 arms, grippers and calibrated safety controls are commissioned, run an inert-object trial with no person inside the reach envelope; never use contact handover or clinical duties to establish a generic safe performance claim.

### Troubleshooting and FAQs

**A user gives a vague request such as “bring what I need”:** reject or ask for a specific permitted item; do not guess medical, personal or safety-critical intent.

**The desired object is outside the robot's reach:** a fixed-base X-Trainer cannot travel through the building. Reposition the safe training cell or explicitly develop a different mobile robot platform.

**Can this be described as a healthcare robot certified for patient use?** No. It is an educational prototype and has no evidenced medical-device approval or clinical validation.

### Downloads and technical documents

* [Official X-Trainer-LeIsaac research source](https://github.com/embodied-dobot/x-trainer).
* [DOBOT X-Trainer exact package and NOVA 2 requirement](https://openelab.io/products/dobot-x-trainer-data-robot).
* [Existing Lightweight Base documentation](../dobot-x-trainer-lightweight-base-user-guide.md).

**Student deliverable:** nonclinical task contract, consent/safety checklist, offline request rejection tests and supervised/simulated tray-placement evaluation.

### Course navigation

[Previous project](x-trainer-project-5-agricultural-harvesting.md) · [Continue to Project 7](x-trainer-project-7-home-assistant.md)

### References and validation

* DOBOT, _Embodied AI Data Acquisition and Application Practice_, Tutorial Guide **V2.0, 2026-09-15**, supplied educational outline.
* [OpenELAB X-Trainer exact sold configuration](https://openelab.io/products/dobot-x-trainer-data-robot), checked 2026-11-21.
* [Official X-Trainer-LeIsaac project](https://github.com/embodied-dobot/x-trainer), checked 2026-11-21.
* [DOBOT X-Trainer Lightweight Base User Guide V1.6](../dobot-x-trainer-lightweight-base-user-guide.md), 2026-02-05, **not automatically identical to the fixed-base SKU**.

**Source review:** documentation draft. **Software execution:** not run. **Hardware testing:** not run. The example code is explicitly **offline and does not command a robot**. Any physical use requires a documented exact-model setup, compatible Nova 2 arms, validated grippers/sensors, emergency-stop access and supervised bench testing.
