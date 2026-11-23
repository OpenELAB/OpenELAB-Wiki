---
description: >-
  Bring up the SO-ARM101 Pro assembled pair with correct 5 V / 12 V supplies,
  calibration, teleoperation and local dataset checks.
---

# Seeed Studio SO-ARM101 Pro Development Guide

{% hint style="info" %}
[**View Seeed Studio SO-ARM101 Pro Assembled Kit on OpenELAB**](https://openelab.io/products/seeed-studio-so-arm101-pro-assembled-kit-lerobot-6dof-robotic-arm)

**Model:** SO-ARM101 Pro assembled leader/follower kit · **SKU:** `Seeed-100046482` · **Power:** leader 5 V; follower 12 V. This is the assembled Pro configuration, not the Standard or motor-only kit.
{% endhint %}

## Product overview

![SO-ARM101 Pro assembled arm kit](../../.gitbook/assets/so-arm101-pro-development-guide.png)

_Manufacturer image: Seeed Studio;_ [_original_](https://files.seeedstudio.com/wiki/robotics/projects/lerobot/Arm_kit.png)_._ [Seeed Studio wiki hub](./)

SO-ARM101 Pro is a manually guided leader and powered follower system for collecting robot demonstrations. Its first engineering milestone is repeatable joint correspondence: identify the physical ports, retain the configured motor IDs, calibrate both mechanisms, and check a small unloaded movement before adding cameras or policies. Assembly at the factory does not establish a calibration for your installation.

_Seeed Studio image;_ [_original kit illustration_](https://files.seeedstudio.com/wiki/robotics/projects/lerobot/Arm_kit.png)_._

[Seeed Studio product guides](./) · [Motor-only kit and assembly guide](so101-pro-servo-motor-kit.md)

### Product and kit scope

The “6DOF” listing describes the servo-actuated mechanism, including its gripper. Do not interpret it as a six-axis industrial wrist with a separate seventh gripper actuator. The SO101 driver exposes shoulder pan/lift, elbow flex, wrist flex/roll and gripper. The product is a research platform; no payload or production-safety qualification is inferred from the name. [SO101 driver](https://github.com/Seeed-Projects/lerobot/blob/d490e472a5d1a207cfe0255caaaf74b6d66e4656/src/lerobot/robots/so_follower/so_follower.py), [hardware project](https://github.com/TheRobotStudio/SO-ARM100).

## Applications

Use the pair to teach pick-and-place motions, compare camera viewpoints, build a small imitation-learning dataset or study calibration error. Start with a soft, lightweight object inside a deliberately small workspace. Define success as a repeatable task outcome, not merely completion of a training job.

For experiments, keep an installation record containing the two arm identities, supply labels, controller and servo revisions, calibration files, camera serials, software commit and task description. Replacing a servo, moving a camera or changing a gripper changes the experiment and should create a new record.

## Specifications

| Integration item                      | Exact Pro-kit interpretation                                                              |
| ------------------------------------- | ----------------------------------------------------------------------------------------- |
| Arm architecture                      | One SO101 leader and one SO101 follower; six servo positions on each                      |
| Host data                             | Separate USB-to-servo-bus controllers; USB is not the motor supply                        |
| Leader supply in Seeed Pro workflow   | 5 V DC, including calibration and operation                                               |
| Follower supply in Seeed Pro workflow | 12 V DC, including calibration and operation                                              |
| Leader gear allocation                | L1 1:191; L2 1:345; L3 1:191; L4–L6 1:147                                                 |
| Follower gearing                      | F1–F6 1:345; confirm fitted 12 V servo marking                                            |
| Servo position IDs                    | 1 shoulder\_pan; 2 shoulder\_lift; 3 elbow\_flex; 4 wrist\_flex; 5 wrist\_roll; 6 gripper |
| Manufacturer x86 tutorial baseline    | Ubuntu 22.04, Python 3.12; GPU dependencies depend on CUDA                                |

Power/gearing: [Seeed hardware/setup reference](https://wiki.seeedstudio.com/lerobot_so100m_new/). Joint names and model map: [SO101 implementation](https://github.com/Seeed-Projects/lerobot/blob/d490e472a5d1a207cfe0255caaaf74b6d66e4656/src/lerobot/robots/so_follower/so_follower.py). The leader servo's printed 7.4 V family rating does not override Seeed's 5 V leader operating instruction. Standard-edition 5 V follower guidance must not be applied to the Pro follower.

## Hardware and connections

### Mounting and power separation

Clamp both bases to a rigid surface. Route cables so the full permitted joint movement cannot pull on USB sockets or servo connectors. Support the follower before disabling torque: a powered pose is not mechanically self-supporting after shutdown.

With all supplies off, check the chain from the base controller through all six joints and inspect three-pin connector orientation against the actual controller/servo markings. Do not reverse a cable to make a plug fit. Connect the labeled 5 V supply to the leader and the labeled 12 V supply to the follower; connect each controller's USB data separately. Do not hot-plug servo wiring. Keep at least 1 m of clear space around the motion area as required by Seeed's setup instructions. [Official assembly/calibration reference](https://wiki.seeedstudio.com/lerobot_so100m_new/).

### Preserve the assembled configuration

Skip `lerobot-setup-motors` on a correctly configured assembled pair. That tool changes individual motor settings and is intended for unconfigured/replacement servos, one motor at a time. A missing joint does not justify rewriting every ID. First inspect cabling, supply, controller port and the expected joint map. Use the [motor-kit procedure](so101-pro-servo-motor-kit.md) if replacing or building a chain.

## Software and development resources

### Prepare the development environment

The source reviewed here is the **Seeed-Projects/lerobot** main-branch snapshot `d490e472a5d1a207cfe0255caaaf74b6d66e4656`, rather than the unrelated assumption that every upstream package release matches the vendor fork. Install into an isolated Python 3.12 environment. The repository's dependency declarations, not a previously installed global package, determine the environment. [Pinned source](https://github.com/Seeed-Projects/lerobot/tree/d490e472a5d1a207cfe0255caaaf74b6d66e4656), [installation reference](https://huggingface.co/docs/lerobot/installation).

```bash
conda create -n openelab-so101 python=3.12 -y
conda activate openelab-so101
git clone https://github.com/Seeed-Projects/lerobot.git openelab-lerobot
cd openelab-lerobot
git checkout d490e472a5d1a207cfe0255caaaf74b6d66e4656
python -m pip install -e '.[feetech,core_scripts]'
conda install -c conda-forge ffmpeg
python -m pip check
lerobot-calibrate --help
lerobot-teleoperate --help
```

If a dependency needs a compiler, install the host's normal development tools before retrying. For training, verify the installed PyTorch/CUDA pair separately; a CPU-only installation can still be suitable for initial hardware bring-up. Seeed's current Jetson instructions distinguish JetPack 6.0/6.1 and their matching GPU wheels; do not install x86 wheels on aarch64 or assume that a newer JetPack is validated. [Vendor environment requirements](https://wiki.seeedstudio.com/lerobot_so100m_new/).

The SDK's license and third-party servo/camera dependencies remain those of their repositories. Examples below are original task configurations and inspection code; no SDK, calibration or hardware execution was performed for this guide.

## Getting started

### Calibrate before teleoperation <a href="#getting-started-calibrate-before-teleoperation" id="getting-started-calibrate-before-teleoperation"></a>

1. Start with no object in the gripper, both bases secure, correct supplies and accessible power isolation. Use the actual mechanism's assembly reference to check joint orientations.
2. Run `lerobot-find-port` with one controller at a time. Label the physical arm and its port. `/dev/ttyACM0` and `/dev/ttyACM1` below are examples; replace them with the observed follower and leader ports. On Linux, inspect `/dev/serial/by-id/` and give your account normal serial-device access.
3. Calibrate the follower, then the leader. At each prompt, use the manufacturer pose/range procedure without forcing a joint through a mechanical stop. Use a unique persistent ID for each physical arm.

```bash
lerobot-calibrate \
  --robot.type=so101_follower \
  --robot.port=/dev/ttyACM0 \
  --robot.id=openelab_pro_follower

lerobot-calibrate \
  --teleop.type=so101_leader \
  --teleop.port=/dev/ttyACM1 \
  --teleop.id=openelab_pro_leader
```

4. Before commanding the follower, archive and inspect the calibration files. This original script only reads local JSON; it does not connect to an arm or change a servo. Save as `inspect_calibration.py`, then run `python inspect_calibration.py` in the same user account.

```python
import json
from pathlib import Path

root = Path.home() / '.cache/huggingface/lerobot/calibration'
for kind, arm_id in [('robots', 'openelab_pro_follower'),
                     ('teleoperators', 'openelab_pro_leader')]:
    files = sorted((root / kind).rglob(arm_id + '.json'))
    if not files:
        print(kind, arm_id, 'NO_MATCH: verify calibration path and ID')
        continue
    for file in files:
        data = json.loads(file.read_text())
        print(file, 'entries=', len(data))
        for joint, record in sorted(data.items()):
            print(' ', joint, record)
```

**Expected result:** both calibrations finish, and the script locates records for the selected physical IDs. This verifies file presence and inspectability; it does not prove the encoder ranges or mechanism are correct. Check that expected joints exist and no ID was silently reused for a different arm. Source for the calibration layout: [SO101 workflow](https://huggingface.co/docs/lerobot/so101).

5. With the follower workspace clear, start the small-motion check using the same IDs. Move one leader joint slightly, observe the corresponding follower joint and return to the starting pose. Repeat only after direction and scale are correct.

```bash
lerobot-teleoperate \
  --robot.type=so101_follower \
  --robot.port=/dev/ttyACM0 \
  --robot.id=openelab_pro_follower \
  --teleop.type=so101_leader \
  --teleop.port=/dev/ttyACM1 \
  --teleop.id=openelab_pro_leader
```

Expected motion is bounded correspondence without a starting jump or wrong joint. Stop the process and isolate power if mapping is wrong, communication is lost or a joint oscillates; support the arm as torque is removed. Software interruption is not a substitute for accessible power isolation.

### Cameras, datasets and further development

Before recording, verify a camera's view without follower motion. For a standard USB camera, inspect it using `lerobot-find-cameras opencv`; enter the observed `index_or_path`, not an index copied from another computer. Check focus, exposure, mounting stability and gripper visibility. Camera index changes can produce valid video of the wrong scene.

For depth cameras, keep the documented **DepthCameraSupport** branch and RealSense/Orbbec dependencies together with their camera type strings. Color and depth streams can have different dimensions and metric scaling. Do not feed colorized depth visualization to a policy as though it were calibrated metric depth. The [manufacturer camera sections](https://wiki.seeedstudio.com/lerobot_so100m_new/) cover detection, warm-up, serial binding and supported stream options.

After verified teleoperation, this original one-episode configuration records a short local experiment. Replace camera index 0 and the serial ports with observed identities; keep `push_to_hub=false` unless you intend to upload data.

```bash
lerobot-record \
  --robot.type=so101_follower \
  --robot.port=/dev/ttyACM0 \
  --robot.id=openelab_pro_follower \
  --robot.cameras='{front: {type: opencv, index_or_path: 0, width: 640, height: 480, fps: 30}}' \
  --teleop.type=so101_leader \
  --teleop.port=/dev/ttyACM1 \
  --teleop.id=openelab_pro_leader \
  --dataset.repo_id=local/so101_bench_check \
  --dataset.single_task='Move the empty gripper between two marked poses' \
  --dataset.num_episodes=1 \
  --dataset.episode_time_s=10 \
  --dataset.reset_time_s=10 \
  --dataset.push_to_hub=false \
  --display_data=true
```

**Expected result:** one local episode with joint data and the intended camera stream. Inspect its beginning/end, dropped frames and timing before recording a batch. Keep failed demonstrations distinguishable rather than merging them into successful training data. [LeRobot dataset recording](https://huggingface.co/docs/lerobot/il_robots), [Seeed dataset tools](https://wiki.seeedstudio.com/lerobot_so100m_new/).

Replay is real motion: inspect the episode, clear the workspace and use `lerobot-replay --help` before selecting episode 0 with the same model/calibration. Training is a separate stage. Start with a small ACT experiment, record dataset/checkpoint and task metrics, then use the vendor's ACT/SmolVLA/Pi0/Pi0.5/GR00T sections for the corresponding dependency extra and model requirements. A LIBERO simulation score does not establish a real SO101 success rate. SenseCraft Robotics offers an alternative UI for project setup, binding, calibration, replay, datasets, training, model selection and operation; keep its project configuration consistent rather than mixing calibration stores. [SenseCraft SO-ARM101 guide](https://wiki.seeedstudio.com/sensecraft_robotics_so_arm101/).

## Troubleshooting and FAQs <a href="#troubleshooting-and-faq" id="troubleshooting-and-faq"></a>

| Symptom                                                 | Ordered diagnosis and recovery                                                                                                                                   |
| ------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Port opens but servos do not reply                      | Confirm controller identity, correct arm supply, connector seating and six-joint chain. USB enumeration alone says nothing about motor power.                    |
| Wrong arm moves                                         | Stop; re-run unplug/replug port discovery. Do not infer identity from plug-in order.                                                                             |
| Calibration is skipped                                  | Check the physical ID and selected existing JSON; back it up before choosing interactive recalibration. Avoid deleting the whole calibration cache.              |
| Multiple joints respond together                        | Suspect duplicate IDs after a replacement. Isolate unconfigured servos and use the motor-kit procedure, not an all-chain rewrite.                                |
| Wrong direction or large offset                         | Stop; compare joint map, gearing, horn orientation and calibration with the actual mechanism. Do not compensate with a policy.                                   |
| Missing wrist-roll range prompt                         | Some SDK revisions handle this joint differently. Compare the pinned driver's behavior; a missing range prompt is not permission to ignore communication errors. |
| Camera works alone but recording stalls                 | Reduce to one camera, verify resolution/fps and USB bandwidth, then inspect encoder/backend dependencies.                                                        |
| Does “training complete” mean ready for autonomous use? | Inspect offline data and conduct a clear-workspace supervised evaluation with known stop controls. No hardware behavior was tested for this page.                |

## Downloads and technical documents <a href="#technical-documents-and-software" id="technical-documents-and-software"></a>

| Resource                                                                                                            | Purpose / exact scope                                                                     |
| ------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| [SO101 single STL download](https://files.seeedstudio.com/wiki/robotics/projects/lerobot/so101/soarm101.stl)        | Manufacturer-listed leader/follower printed parts; not required for a sound assembled kit |
| [SO100/SO101 hardware repository](https://github.com/TheRobotStudio/SO-ARM100)                                      | Select SO101 BOM, drawings and assembly files                                             |
| [Pinned Seeed LeRobot SDK](https://github.com/Seeed-Projects/lerobot/tree/d490e472a5d1a207cfe0255caaaf74b6d66e4656) | Software source and dependency definitions                                                |
| [Seeed full hardware-to-policy tutorial](https://wiki.seeedstudio.com/lerobot_so100m_new/)                          | Assembly poses, servo setup, calibration, camera and training reference                   |
| [Upstream SO101 reference](https://huggingface.co/docs/lerobot/so101)                                               | Upstream compatibility and calibration changes                                            |
| [SenseCraft Robotics SO101 training guide](https://wiki.seeedstudio.com/sensecraft_robotics_so_arm101/)             | Alternative application route                                                             |

## References and validation <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

Reviewed **24 November 2026** against the sources linked beside the procedures and tables. The [Seeed setup guide](https://wiki.seeedstudio.com/lerobot_so100m_new/), [upstream project](https://github.com/huggingface/lerobot) and [SO101 hardware project](https://github.com/TheRobotStudio/SO-ARM100) remain authoritative for their own revisions. Download links to CAD/STL are resource references, not evidence of fit or fabrication validation.

**Validation:** source reviewed. Installation, compilation, servo communication, calibration, recording, training and hardware motion were **not run** by OpenELAB for this revision. Expected results above are reproduction checkpoints. Preserve your actual software, calibration and hardware records before extending the experiment.

### Related retained references

* [Historical LeRobot package release; use the pinned SDK selected above](https://pypi.org/project/lerobot/0.7.0/)
* [Read official source: lerobot](https://github.com/Seeed-Projects/lerobot)
