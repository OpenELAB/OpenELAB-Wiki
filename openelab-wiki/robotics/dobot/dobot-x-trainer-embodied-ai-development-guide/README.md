---
description: >-
  Exact-kit X-Trainer dual-arm teleoperation, embodied-AI simulation/dataset
  guide and seven-project curriculum; Nova 2 arms not included.
---

# DOBOT X-Trainer — Embodied AI Development and Data Acquisition Guide

{% hint style="info" %}
[**View DOBOT X-Trainer Dual-Arm Robot for AI Data Collection on OpenELAB**](https://openelab.io/products/dobot-x-trainer-data-robot)

**Manufacturer:** DOBOT · **Product:** X-Trainer Data Acquisition Platform · **OpenELAB SKU:** `DOBOT-8000000050` · **Scope:** listed master hands, slave grippers, cameras and fixed base; **two Nova 2 arms and host computer must be sourced separately**
{% endhint %}

### Product overview

**X-Trainer** is a bimanual teleoperation and embodied-AI data-acquisition platform. A human operator moves two master hands to demonstrate tasks with paired **compatible robot arms**; synchronized observation and action records can support imitation-learning experiments.

This guide is adapted from DOBOT's **Embodied AI Data Acquisition and Application Practice, Tutorial Guide V2.0 (2026-09-15)**. That document is a _course outline_, not seven completed application repositories. The seven independent tutorials below turn its project objectives into reproducible **simulation or offline first results** and carefully scoped real-hardware validation plans.

**Do not confuse the configured platform with the complete robot cell.** The exact [OpenELAB SKU](https://openelab.io/products/dobot-x-trainer-data-robot) provides **two master hands, two grippers, three depth-sensing cameras and a fixed base with camera bracket**. **Two compatible DOBOT Nova 2 collaborative arms are required but NOT included.** A training computer is also not included. Confirm camera identity, end-effector revisions and the shipped base before installation.

The existing [DOBOT X-Trainer Lightweight Base User Guide V1.6](../dobot-x-trainer-lightweight-base-user-guide.md) documents a **Lightweight Base variant**. It covers valuable operational practices and Nova 2 firmware requirements but **must not be treated as a confirmed dimensional, wiring or mounting drawing for every current fixed-base package**.

### Applications

* Collect dual-arm human demonstrations for robot-imitation-learning datasets.
* Train and evaluate bimanual skills in simulation before real operation.
* Compare keyboard and leader-arm teleoperation, multimodal sensor observation and action labels.
* Teach data synchronization, train/validation splitting, offline policy evaluation and Sim2Real gaps.
* Prototype beverage preparation, waste sorting, assembly, harvesting, assisted delivery and household organization **only with the necessary fixtures, end effectors, validated limits and supervision**.

### Specifications

| Item                          | Store-listed value / scope                                                                                     |
| ----------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Two master hands              | 6 DoF each, USB connection; maximum master working radius 437 mm                                               |
| Two slave grippers            | Included; confirm installed model and safe stroke/force before operation                                       |
| Cameras                       | Three depth-sensing units in listed package; exact type/driver must be confirmed                               |
| Base                          | Fixed base with camera bracket; listed base mass 85 kg, unfolded 1530 × 960 × 1300 mm                          |
| Slave robot arms              | **Two Nova 2 required, not included**                                                                          |
| Training host                 | **Optional purchase, not included**                                                                            |
| Listed robot reach            | 625 mm per arm; 1200 mm dual-arm working range                                                                 |
| Listed payload                | 2 kg per arm / 3 kg dual-arm (store wording; confirm robot configuration, tool and mounting conditions)        |
| Listed repeatability          | ±0.05 mm for compatible robot arms under manufacturer conditions; **not task success or calibration accuracy** |
| Store-listed system interface | 25 Hz; **do not confuse with 30 Hz simulated logging**                                                         |
| Safety                        | Collision detection is listed; no integrated course project is a safety-certified machine cell                 |

Source: [OpenELAB exact product listing](https://openelab.io/products/dobot-x-trainer-data-robot). Manufacturer documentation for the **Lightweight Base** identifies **three Intel RealSense D405** cameras, gripper stroke **95 mm** and Nova 2 firmware **≥ V3.5.8.1**; verify those details against the actual sold revision rather than assuming all variants are identical.

### Hardware and connections

1. Identify the **fixed-base X-Trainer SKU, mounting/base revision, two optional Nova 2 robots, host PC, controllers, three camera model labels, installed gripper revision, mains voltage, cable and safety devices** before assembly. Do not substitute a lightweight-base mounting orientation from another document.
2. Follow the exact supplied manufacturer assembly and electrical drawings. The [Lightweight Base V1.6 guide](../dobot-x-trainer-lightweight-base-user-guide.md) illustrates a control cabinet with networking, gripper power and E-stop links; it is **a comparison reference**, not an authorized fixed-base wiring pinout.
3. Commission each Nova 2 separately using the correct Nova 2 manual/software and firmware. The **Lightweight Base manual** requires Nova firmware **3.5.8.1 or higher**; confirm current compatibility with DOBOT and the delivered kit. Do not guess static IPs or overwrite production network settings.
4. Before master–slave sync, clear the complete dual-arm workspace and identify **both physical emergency stops**. The relevant manual describes a left yellow button for unlock/synchronize and a right green button for recording; indicator statuses include yellow (synchronized), green (recording) and red (fault). Confirm the delivered button/interface behavior.
5. Keep actual robot actuation disabled for the **first software exercises**. Do not mix bare hardware ports, arm firmware controls, Isaac Lab simulation controllers or LeRobot data converters without an explicit integration test.

### Software and development resources

| Development track                                    | Supported/observed source                                                                                                            | Usage boundary                                                                                                                      |
| ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| Official open-source simulation                      | [embodied-dobot/x-trainer](https://github.com/embodied-dobot/x-trainer)                                                              | Isaac Sim + Isaac Lab/LeIsaac; simulated `LeIsaac-XTrainer-PickCube-v0` environment                                                 |
| Recommended simulation stack                         | Isaac Sim **4.5** noted by repository as working; GPU/CUDA dependencies per [LeIsaac setup](https://lightwheelai.github.io/leisaac/) | Pin actual versions and USD assets before use                                                                                       |
| Keyboard simulated teleoperation                     | `bi\_keyboard` mode and 3 camera views                                                                                               | Does not actuate Nova 2 hardware                                                                                                    |
| Physical master-arm → simulation                     | `xtrainerleader`; utility scripts `scripts/find\_port.py` and `scripts/get\_offset.py`                                               | Only after device/serial calibration; commands apply to simulation follower                                                         |
| Dataset pipeline                                     | HDF5 demonstrations and `scripts/convert/isaaclab2lerobot\_xtrainer.py`                                                              | Repository specifies **30 Hz** simulation collection and LeRobot conversion                                                         |
| Physical robot teleoperation and algorithm workflows | [DOBOT X-Trainer Lightweight Base V1.6 manual](../dobot-x-trainer-lightweight-base-user-guide.md)                                    | Different base revision; described `Dobot\_Xtrainer` demo scripts require the actual manufacturer SDK archive and matching hardware |

Do not run a real arm `run\_control.py`, `run\_inference.py`, or gripper command merely because a similarly named script exists. The **Isaac Lab GitHub repository** and older **Dobot\_Xtrainer physical-cell demo project** are **different software workflows**.

### Getting started

#### Prerequisites for a simulation-first result

* NVIDIA GPU-equipped Linux workstation supported by the chosen Isaac Sim / Isaac Lab / LeIsaac versions (the cited repository reports **Isaac Sim 4.5** worked).
* Git, project dependencies, correct matching **USD assets** and model files from the official repository's documentation; simulator setup per [LeIsaac](https://lightwheelai.github.io/leisaac/).
* No Nova 2 robot arms, X-Trainer hardware, grippers or real cameras are required for the initial simulation.
* Note the exact repository Git commit, Python version, simulator version and GPU driver for reproducibility.

#### First working result: simulated two-arm cube task

1. Clone the official repository into a working directory:

```bash
git clone https://github.com/embodied-dobot/x-trainer.git
cd x-trainer
git rev-parse HEAD
```

2. Follow the repository README to download its **USD assets** and install compatible Isaac Sim, Isaac Lab and LeIsaac. The README documents this installation route inside the activated LeIsaac environment:

```bash
conda activate leisaac
pip install -e source/leisaac
```

3. With the simulator and assets installed, launch the official **keyboard-only simulation** from the project root:

```bash
python scripts/environments/teleoperation/teleop_se3_agent.py \
  --task=LeIsaac-XTrainer-PickCube-v0 \
  --teleop_device=bi_keyboard \
  --num_envs=1 \
  --device=cuda \
  --enable_cameras \
  --multi_view
```

4. The [README keyboard mapping](https://github.com/embodied-dobot/x-trainer#usage) uses **Q/W/E/A/S/D** for left-arm joints, **U/I/O/J/K/L** for right-arm joints, **G/H** grippers, **B** to start, **R** for failed reset and **N** for success/reset. **These keys affect the simulator, not a physical robot.**

**Expected result:** the X-Trainer dual-arm **Lift Cube** scene loads with left/right/top simulated RGB views; keyboard actions change the simulated robot, and the environment can be reset. Capture the actual result, console log and software revisions. The task setup is documented in the public repository; **this guide has not executed it**.

**If it fails:** check USD asset placement, actual LeIsaac/Isaac Sim versions, GPU/driver, `pip install -e` project path and the official task registration. Confirm `LeIsaac-XTrainer-PickCube-v0` exists in the installed repository. Do not “fix” simulator errors by enabling real Nova 2 motion.

#### Optional next stage — data capture

The GitHub repository documents **30 Hz HDF5 recording** and conversion to LeRobot format with:

```bash
python scripts/convert/isaaclab2lerobot_xtrainer.py
```

Use it **only after a successful recorded simulator episode** and confirm dataset source/output paths and dependencies from the exact checked-out commit. Conversion is not policy training; separate training/validation/test records must be designed before model deployment.

### Course pathway — seven tutorials

| Tutorial                                                                                                      | Project and core deliverable                                                                            |
| ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [**Project 1 — Embodied AI and Simulation Configuration**](x-trainer-project-1-simulation-sim2real.md)        | Isaac Sim/LeIsaac Lift Cube, simulated demonstrations, HDF5 inspection and Sim2Real analysis            |
| [**Project 2 — Intelligent Beverage Station**](x-trainer-project-2-beverage-station.md)                       | Supervised dry-task state machine for opening, pouring and flexible-container placement                 |
| [**Project 3 — Intelligent Waste Sorting**](x-trainer-project-3-waste-sorting.md)                             | Recognition, metric depth localization, mock-waste grasp/route validation                               |
| [**Project 4 — Precision Industrial Component Assembly**](x-trainer-project-4-precision-assembly.md)          | Part picking, visual alignment and force-control requirements                                           |
| [**Project 5 — Agricultural Fruit and Vegetable Harvesting**](x-trainer-project-5-agricultural-harvesting.md) | Mock-fruit perception, gentle grasp planning and transport stability                                    |
| [**Project 6 — Healthcare and Assisted-Living Robot**](x-trainer-project-6-assisted-living.md)                | Nonclinical object retrieval, restricted request handling and supervised delivery to a tray             |
| [**Project 7 — Intelligent Home Assistant**](x-trainer-project-7-home-assistant.md)                           | Integrated object sorting, imitation-learning dataset, multi-step task plan and system-level evaluation |

**Progression:** simulate first → validate sensor and motion metadata → acquire annotated demonstrations → train/evaluate on held-out tasks → conduct a separately authorized physical trial. No tutorial assumes that the excluded Nova 2 arms or PC are bundled.

### Troubleshooting and FAQs

**Can I use the kit without two Nova 2 arms?** Yes, certain master-arm/software and simulator exercises are possible; **physical dual-arm manipulation requires two compatible Nova 2 arms**, which the listed kit does not include.

**Do I have the cameras used by the manual?** The V1.6 **Lightweight Base** guide specifies three RealSense D405 units; the current fixed-base retail listing only guarantees “depth-sensing camera ×3.” Check exact labels and firmware before using D405 calibration or drivers.

**Why do some docs say 25 Hz and the GitHub project 30 Hz?** The storefront lists **25 Hz interface**, while [X-Trainer-LeIsaac](https://github.com/embodied-dobot/x-trainer) specifies **30 Hz simulation recording**. These describe different layers; neither establishes a measured physical robot throughput.

**Can I use the V1.6 Lightweight Base assembly steps on this product?** Only if DOBOT confirms the shipped fixed-base hardware uses the same interface/mounting revision. Do not assume the two base variants are mechanically or electrically identical.

**Can these experiments produce an autonomous robot policy immediately?** No. The course outline describes the full learning cycle; the GitHub repository provides **one Lift Cube simulation implementation**, not a verified real-world version of each of the six application tasks.

### Downloads and technical documents

| Resource                                                                                                                                                            | Purpose                                                         | Scope                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------ |
| [OpenELAB X-Trainer listing](https://openelab.io/products/dobot-x-trainer-data-robot)                                                                               | Exact package selection and official manual entry               | DOBOT-8000000050                                             |
| [Manufacturer X-Trainer AI Operating Platform User Guide](https://cdn.robotshop.com/media/D/Dot/RB-Dot-74/pdf/dobot-x-trainer-ai-operating-platform-user-guide.pdf) | Base operation, interfaces and programming guidance             | Confirm edition/version before following physical steps      |
| [X-Trainer Lightweight Base V1.6 in OpenELAB Wiki](../dobot-x-trainer-lightweight-base-user-guide.md)                                                               | Installation, data acquisition, physical training and inference | Explicit **Lightweight Base** variant                        |
| [X-Trainer-LeIsaac GitHub repository](https://github.com/embodied-dobot/x-trainer)                                                                                  | Isaac Lab, multi-view simulation, teleop and HDF5 → LeRobot     | Official open-source simulation                              |
| [Official LeIsaac setup](https://lightwheelai.github.io/leisaac/)                                                                                                   | Compatible Isaac Sim/Isaac Lab environment                      | Third-party framework documentation referenced by repository |

A product-specific fixed-base electrical/pinout drawing, exact camera calibration and shipped Nova 2 firmware verification are still needed for **physical commissioning**; this page does not invent them.

### References and validation

* DOBOT, _Embodied AI Data Acquisition and Application Practice_, **Tutorial Guide V2.0 (2026-09-15)**, user-supplied document.
* [OpenELAB X-Trainer exact product details](https://openelab.io/products/dobot-x-trainer-data-robot), reviewed **2026-11-21**.
* [embodied-dobot/x-trainer README](https://github.com/embodied-dobot/x-trainer), reviewed **2026-11-21**.
* [OpenELAB archived X-Trainer Lightweight Base User Guide V1.6](../dobot-x-trainer-lightweight-base-user-guide.md), dated 2026-02-05.
* [Manufacturer-authored older X-Trainer AI Operating Platform manual linked by OpenELAB](https://cdn.robotshop.com/media/D/Dot/RB-Dot-74/pdf/dobot-x-trainer-ai-operating-platform-user-guide.pdf).

**Documentation checked:** product listing, official GitHub README, existing manual text and V2.0 educational course. **Software executed:** not run. **Hardware validated:** not run. **Open critical gaps for real-arm operation:** fixed-base electrical/mounting documents, delivered Nova 2 arm/firmware/driver scope, confirmed camera/gripper revisions, emergency-stop testing and laboratory risk controls. The simulation-first workflow is available to review independently.
