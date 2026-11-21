---
description: >-
  Model-scoped X-Trainer embodied-AI educational project with reproducible
  offline/simulation checkpoint, source links and hardware validation
  requirements.
---

# Project 1 — X-Trainer Embodied AI Simulation and Sim2Real

{% hint style="info" %}
[**View DOBOT X-Trainer Dual-Arm Robot for AI Data Collection on OpenELAB**](https://openelab.io/products/dobot-x-trainer-data-robot)

**Product:** DOBOT X-Trainer · **SKU:** `DOBOT-8000000050` · **Sold kit:** two master hands, two slave grippers, three depth cameras, fixed base; **two Nova 2 robot arms and training PC not included**
{% endhint %}

[Return to X-Trainer course index](./) · [Existing Lightweight Base V1.6 Manual](../dobot-x-trainer-lightweight-base-user-guide.md)

### Product overview

**Project 1 — Introduction to Embodied AI and Simulation Configuration** covers the course's four tasks: **(1)** perception–decision–action foundations, **(2)** multimodal perception, imitation learning and VLA concepts, **(3)** simulation environment/model/sensor setup, and **(4)** simulation training and the Sim2Real gap.

It is the **required foundation** for Projects 2–7. The first meaningful result uses the official X-Trainer simulation and does **not require a physical X-Trainer, Nova 2 arms or cameras**.

### Applications

* Explain the distinction between conventional programmed trajectories, behavioral cloning, policy learning and vision-language-action (VLA) models.
* Explore dual-arm manipulation in a reproducible simulator.
* Observe how keyboard/leader demonstration actions can be associated with multi-view RGB observations and joint states.
* Design train/validation splits and a simulator-to-physical transfer checklist.

### Specifications

| Component                 | Documented simulation configuration                                                                   |
| ------------------------- | ----------------------------------------------------------------------------------------------------- |
| Simulator project         | [embodied-dobot/x-trainer](https://github.com/embodied-dobot/x-trainer), built on LeIsaac / Isaac Lab |
| Tested upstream simulator | **Isaac Sim 4.5** reported in repository; verify local environment                                    |
| Demo task                 | `LeIsaac-XTrainer-PickCube-v0` (dual-arm cube lift)                                                   |
| Simulated cameras         | Left wrist, right wrist and top RGB views, **640 × 480**, **69° FOV** as described in simulation      |
| Simulated joint actions   | 14 arm joints plus gripper controls represented in 16-dimension follower actions                      |
| Simulated dataset         | **30 Hz** synchronized RGB + joint-state HDF5, not the storefront's 25 Hz hardware interface          |
| Physical hardware         | Nova 2 ×2 required for real dual-arm robot tasks; absent from the sold X-Trainer kit                  |

The simulated 69° FOV and virtual camera configuration **are not measured intrinsics/extrinsics of the three supplied physical depth cameras**.

### Hardware and connections

1. For the first simulation exercise, use a workstation with an NVIDIA GPU supported by **Isaac Sim/Isaac Lab**; follow the versions documented by the repo and LeIsaac.
2. No robot wiring is required. Keep the shipped X-Trainer master controllers disconnected unless deliberately testing the separate `xtrainerleader` simulation mode.
3. For later hardware experiments, identify actual master-hand serial ports, Nova 2 firmware, E-stops, grippers and cameras **before** mapping any control data.
4. Preserve safe simulation–hardware isolation: ensure demo environment variables or config files cannot inadvertently select live robot mode.

### Software and development resources

| Resource                                                                           | Use                                                                                               |
| ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| [X-Trainer-LeIsaac README](https://github.com/embodied-dobot/x-trainer)            | USD model assets, supported simulator, keyboard/leader/VR commands, HDF5/LeRobot conversion       |
| [LeIsaac framework](https://lightwheelai.github.io/leisaac/)                       | Isaac Sim/Isaac Lab dependency and compatible environment setup                                   |
| [X-Trainer leader-arm serial scripts](https://github.com/embodied-dobot/x-trainer) | `scripts/find\_port.py`, `scripts/get\_offset.py`, only when a real leader master arm is attached |
| [Lightweight Base V1.6 manual](../dobot-x-trainer-lightweight-base-user-guide.md)  | Separate physical operation and Nova 2 firmware context                                           |

### Getting started

#### Task 1 — Map the embodied-AI pipeline

Draw: **human demonstration → camera/robot-state observation → synchronized episode → cleaned training dataset → imitation-learning policy → simulated evaluation → guarded physical deployment**. For each arrow, state its input, output, clock, unit and failure mode.

#### Task 2 — First working result: simulated two-arm keyboard control

Prepare Isaac Sim + Isaac Lab + LeIsaac and obtain the **USD assets** required by the official README. From a checkout of the public repository:

```bash
git clone https://github.com/embodied-dobot/x-trainer.git
cd x-trainer
git rev-parse HEAD
conda activate leisaac
pip install -e source/leisaac
python scripts/environments/teleoperation/teleop_se3_agent.py \
  --task=LeIsaac-XTrainer-PickCube-v0 \
  --teleop_device=bi_keyboard \
  --num_envs=1 --device=cuda --enable_cameras --multi_view
```

**Expected result:** the Lift Cube environment opens with dual robot arms and three **simulated** views. The README maps left J1–J6 to **Q/W/E/A/S/D**, right J1–J6 to **U/I/O/J/K/L**, and grippers to **G/H**; **B** starts, **R** resets a failed trial, **N** labels success/reset. Record frames and console logs, including actual versions.

If launch fails, check the registered task name, path to USD assets, Isaac Sim build, LeIsaac installation and NVIDIA drivers. A working virtual camera does not prove the X-Trainer D405 physical cameras are connected.

#### Task 3 — Produce and inspect a small demonstration dataset

Perform a short **simulated** trial and mark success/failure through the documented controls. Inspect whether an HDF5 episode was written, then examine the file with the package installed in its simulation environment:

```python
# Point to the actual generated HDF5 path; no fixed filename is assumed.
import h5py
from pathlib import Path
episode = Path("PATH_TO_RECORDED_EPISODE.hdf5")
with h5py.File(episode, "r") as f:
    print(list(f.keys()))
```

This snippet **requires replacing** the illustrative file path with an actually generated file; it deliberately does not guess the schema. Expected result: a readable list of existing dataset groups. If missing, inspect the repo's episode recording settings and simulator success/failure action.

#### Task 4 — Frame a Sim2Real comparison

Create a table for visual calibration, object mass/friction, robot encoder resolution, contact dynamics, control rate, latency, action dimensions, gripper state and safety constraints. Explain the difference between the repository's **30 Hz simulated recording** and the listed physical system interface. Do not declare a trained policy transferable on the basis of a simulation success.

### Troubleshooting and FAQs

**The task is not registered:** ensure the X-Trainer `source/leisaac` package installed in the correct environment; confirm the exact repository commit and USD paths.

**Cameras show the wrong viewpoint:** check the simulated sensor configuration and actual task; do not “fix” hardware camera calibration based on the simulated FOV.

**I want to control the simulator with the physical master hands:** follow the README's separate **`find\_port.py` → `get\_offset.py` → `xtrainerleader`** sequence with the robot master hands connected and correctly calibrated. This still controls the simulated follower, not the two physical Nova 2 arms.

### Downloads and technical documents

* [Official X-Trainer simulation/teleoperation source](https://github.com/embodied-dobot/x-trainer).
* [LeIsaac installation documentation](https://lightwheelai.github.io/leisaac/).
* [X-Trainer physical Lightweight Base V1.6 manual](../dobot-x-trainer-lightweight-base-user-guide.md).
* [Store SKU/package scope](https://openelab.io/products/dobot-x-trainer-data-robot).

**Student deliverable:** environment/version record, one labeled simulated task run, sample HDF5 group inventory, and a one-page Sim2Real risk table.

### Course navigation

[Continue to Project 2](x-trainer-project-2-beverage-station.md)

### References and validation

* DOBOT, _Embodied AI Data Acquisition and Application Practice_, Educational Tutorial Guide **V2.0, 2026-09-15** (provided course outline), corresponding project.
* [OpenELAB DOBOT X-Trainer product listing](https://openelab.io/products/dobot-x-trainer-data-robot), reviewed 2026-11-21.
* [Official X-Trainer-LeIsaac repository and usage](https://github.com/embodied-dobot/x-trainer), reviewed 2026-11-21.
* [DOBOT X-Trainer Lightweight Base manual V1.6](../dobot-x-trainer-lightweight-base-user-guide.md), 2026-02-05; different base scope.

**Documentation:** source-informed draft. **Software execution:** not run. **Hardware validation:** not run. Offline/simulator results stated here are expected outcomes, not observed logs. Do not transfer an untested simulator policy to the physical Nova 2 arms without DOBOT-approved integration, collision/safety verification and supervised trials.
