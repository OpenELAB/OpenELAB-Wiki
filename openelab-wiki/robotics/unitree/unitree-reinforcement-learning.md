---
description: >-
  Follow Train, Play and Sim2Sim resources for G1, H1 and H1-2, check policy
  metadata offline, and retain model-specific physical-deployment gaps.
---

# Unitree RL Gym: training, policy contracts and simulator transfer

{% hint style="info" %}
**Shared development guide: Unitree RL Gym training and policy validation.** No new retail product or SKU is implied. Model identity and physical development rights belong in the [G1 model guide](https://wiki.openelab.io/robotics/unitree/unitree-g1-standard-edu-development-guide); transport and message selection belong in the [SDK2 state](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development) and [ROS2](https://wiki.openelab.io/robotics/unitree/unitree-ros2-integration) guides. This page's first result is entirely offline.
{% endhint %}

The documented workflow is **Train → Play → Sim2Sim → Sim2Real**. These are progressively different validation stages, not a promise that a policy trained in one simulator is ready for a robot. The English portal describes G1, H1 and H1-2 examples; the repository also registers a Go2 training task. Training-task presence does not establish an equivalent physical deployment example. [RL introduction](https://support.unitree.com/home/en/rl_gym/intro)

## Product overview <a href="#product-overview" id="product-overview"></a>

Isaac Gym supplies parallel training environments, Play evaluates and exports an actor policy, and MuJoCo checks transfer to another dynamics engine. Physical deployment adds model-specific joints, IMU conventions, communication bindings, mechanical protection and a qualified stop contract. This guide preserves the physical articles' boundaries but does not provide an executable commissioning sequence.

The pinned repository is **`unitree_rl_gym` commit `276801e46c5d433564f24658bac64f254b7d2d4b`**. The portal articles were updated in January 2025; the pinned README includes later C++ G1 deployment material. Keep the article version, source commit, configuration and policy artifact together instead of assuming live main matches an older tutorial. [Pinned README](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/README.md)

## Applications <a href="#applications" id="applications"></a>

* **Reproducible policy experiments:** select a task, seed, checkpoint and environment count explicitly; preserve the observation/action schema and normalization alongside the exported policy.
* **Simulator-transfer analysis:** compare contact/dynamics behavior in Gym and MuJoCo while keeping the same policy, joint order and controller period.
* **Offline artifact qualification:** reject a policy/configuration mismatch before loading a tensor file, simulator or communication library.
* **Physical-deployment planning:** identify required model-specific evidence and unsafe assumptions without executing the source's robot examples.

G1+, H2/H2-X, R1 variants, legacy Go1/A1/AlienGo/Laikago and different G1 joint/hand configurations are not qualified by these three humanoid deployment articles. A URDF with a familiar name or matching tensor shape does not establish support.

## Specifications <a href="#specifications" id="specifications"></a>

### Documented environment baseline <a href="#documented-environment-baseline" id="documented-environment-baseline"></a>

| Component           | Portal setup article                                                           | Meaning                                                            |
| ------------------- | ------------------------------------------------------------------------------ | ------------------------------------------------------------------ |
| OS / GPU            | Ubuntu 18.04 or later recommended; NVIDIA GPU; driver 525 or later recommended | Historical recommendation, not an all-version compatibility matrix |
| Environment         | Python 3.8 virtual environment                                                 | Keep training and deployment dependencies separately reproducible  |
| Training packages   | PyTorch 2.3.1, torchvision 0.18.1, torchaudio 2.3.1, CUDA package 12.1         | Do not mix arbitrary current binaries into this baseline           |
| Physics / RL        | NVIDIA Isaac Gym; `rsl_rl` v1.0.2; editable `unitree_rl_gym`                   | Isaac Gym is distinct from Isaac Sim/Isaac Lab                     |
| Robot communication | Optional `unitree_sdk2_python` for physical deployment                         | Not required to inspect a policy manifest or train locally         |

[Installation/configuration article](https://support.unitree.com/home/en/rl_gym/setup). Its 1080-balls example is an Isaac Gym installation check, not robot validation. No package, driver or simulator was installed here.

### Actual policy dimensions are not total robot joints <a href="#actual-policy-dimensions-are-not-total-robot-joints" id="actual-policy-dimensions-are-not-total-robot-joints"></a>

| Pinned training config | Actions / actor observations / privileged observations | Source-specific interpretation                                        |
| ---------------------- | ------------------------------------------------------ | --------------------------------------------------------------------- |
| G1                     | 12 / 47 / 50                                           | `g1_12dof.urdf`, lower-body policy; not a 29-action whole-body policy |
| H1                     | 10 / 41 / 44                                           | Five leg joints per side in this task; separate upper-body posture    |
| H1-2                   | 12 / 47 / 50                                           | Separate H1-2 model, limits and mapping despite G1-like dimensions    |

[Pinned G1 config](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/legged_gym/envs/g1/g1_config.py), [H1 config](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/legged_gym/envs/h1/h1_config.py), [H1-2 config](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/legged_gym/envs/h1_2/h1_2_config.py). The sample recurrent policies use an LSTM with hidden size 64, one layer and 32-unit actor/critic hidden layers. The configurations randomize friction/mass and apply simulated pushes; those are training conditions, not safe physical test instructions. Rewards include velocity tracking, posture/height, smoothness, contact and joint-limit terms; a high reward is not a safety certification.

The G1 MuJoCo configuration has `simulation_dt=0.002`, `control_decimation=10`, hence **0.020 s / 50 Hz** policy updates. It uses 12 gain/default-angle entries, 47 observations and action scale 0.25. The physical G1 configuration separately selects HG messages, pelvis IMU, twelve leg motor indices and upper-body targets; this is a specific 29-body-joint mapping, not every G1 retail option. [Simulation config](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/deploy/deploy_mujoco/configs/g1.yaml), [physical config, inspection only](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/deploy/deploy_real/configs/g1.yaml)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

The offline first result requires no GPU, robot, controller, battery or network. A future training/simulation environment should have no physical robot NIC/bridge attached. If a separate simulator exchanges DDS messages, configure a verified isolated interface/domain on both peers; a simulator flag alone does not establish isolation. Do not assume every repository uses the same domain convention or supports high-level RPC simulation.

For a real robot, the portal deployment chapters assume hoisting, zero-torque/debug preparation, network configuration, a default-position transition and then policy control. They describe a select-button exit into damping **with a fall**, as well as terminal interruption. This is an illustrative controller, explicitly not a stable production controller. Zero torque, damping, default pose, script exit and effective emergency stop are different states. The articles' gestures and network examples are not reproduced as a runnable first-result sequence. [G1 deployment boundary](https://support.unitree.com/home/en/rl_gym/g1_sim2real), [H1](https://support.unitree.com/home/en/rl_gym/h1_sim2real), [H1-2](https://support.unitree.com/home/en/rl_gym/h1_2_sim2real)

Match the actual model/edition, development permission, firmware, joint and IMU map, approved support equipment, startup and stop instructions before any physical procedure. This shared page supplies no charging, connector pinout, hoist rating or stop/holding guarantee.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Training and Play parameters <a href="#training-and-play-parameters" id="training-and-play-parameters"></a>

The source entry points are `legged_gym/scripts/train.py` and `legged_gym/scripts/play.py`, with `--task` selecting `go2`, `g1`, `h1` or `h1_2`. These are source references, not commands executed for this guide.

| Parameter                         | Use and reproducibility implication                                           |
| --------------------------------- | ----------------------------------------------------------------------------- |
| `--headless`                      | Suppress rendering; the `v` key toggles rendering in the source viewer        |
| `--resume`                        | Continue a checkpoint; record which checkpoint rather than relying on latest  |
| `--experiment_name`, `--run_name` | Separate experiment identity from a particular run                            |
| `--load_run`, `--checkpoint`      | Select the run/model; defaults use the latest run/file                        |
| `--num_envs`                      | Parallel environments; affects memory and sampling                            |
| `--seed`, `--max_iterations`      | Experiment seed and run extent                                                |
| `--sim_device`, `--rl_device`     | Physics and learning compute devices; CPU choices are independently specified |

[G1 training](https://support.unitree.com/home/en/rl_gym/g1_train), [H1 training](https://support.unitree.com/home/en/rl_gym/h1_train), [H1-2 training](https://support.unitree.com/home/en/rl_gym/h1_2_train). Default checkpoints are under `logs/<experiment_name>/<date_time>_<run_name>/model_<iteration>.pt`. Play exports the actor under `logs/<experiment_name>/exported/policies`, with MLP `policy_1.pt` and recurrent `policy_lstm_1.pt`. Explicitly identify the policy architecture and recurrent reset/hidden-state behavior; the extension `.pt` alone is insufficient.

The portal calls `--task` required, but the pinned argument helper actually defaults it to `go2`. Select the intended task explicitly. `--headless` is a boolean flag in that helper, not a string argument; the parser also exposes `--horovod` for multi-GPU use, which is not a validated distributed environment here. [Pinned argument helper](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/legged_gym/utils/helpers.py)

### Sim2Sim contract <a href="#sim2sim-contract" id="sim2sim-contract"></a>

The source simulator entry is `deploy/deploy_mujoco/deploy_mujoco.py`, which looks in `deploy/deploy_mujoco/configs/` for `g1.yaml`, `h1.yaml` or `h1_2.yaml`. The corresponding bundled policy paths are `deploy/pre_train/<robot>/motion.pt`; replacing `policy_path` changes the artifact but does not automatically change the observation builder, control period or joint ordering. [G1 Sim2Sim](https://support.unitree.com/home/en/rl_gym/g1_sim2sim), [H1](https://support.unitree.com/home/en/rl_gym/h1_sim2sim), [H1-2](https://support.unitree.com/home/en/rl_gym/h1_2_sim2sim)

In the pinned MuJoCo script, the observation contains angular velocity, projected gravity, scaled command, relative joint positions, joint velocities, previous actions and sine/cosine phase. Its size is `9 + 3×num_actions + 2`; G1's 12 actions therefore produce 47 observations. The script uses quaternion w,x,y,z and a 0.8 s phase period, runs PD torque updates at the physics step and policy inference at the decimated interval. Its configured `cmd_init` is nonzero: a simulator launch is active policy control, not passive model viewing. [Pinned simulator source](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/deploy/deploy_mujoco/deploy_mujoco.py)

### Source discrepancies to resolve before reuse <a href="#source-discrepancies-to-resolve-before-reuse" id="source-discrepancies-to-resolve-before-reuse"></a>

| Source issue                                                                                                                    | Consequence                                                                                                               |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| H1 Train article lists a default `logs/h1_2/…` directory; H1 Play lists `logs/g1/…`                                             | The pinned H1 config's experiment name is `h1`; verify the actual run/export path rather than copying those article paths |
| General Sim2Sim replacement example uses a G1 export path                                                                       | Use the actual task's artifact and verified model/schema, not a common filename                                           |
| Physical articles show shorthand robot arguments and later `.yaml` arguments, while introduction gives the full deployment path | Inspect the exact entry point/parser/config directory before a future qualified procedure                                 |
| Training G1/H1 configs inherit their simulation step; H1-2 explicitly uses 0.0025 s and decimation 8                            | Do not transplant decimation alone; preserve the effective policy period                                                  |
| README license summary differs from the actual root license wording                                                             | Use the actual BSD-3-Clause LICENSE and dependency notices, not a rewritten legal summary                                 |

[H1 Train](https://support.unitree.com/home/en/rl_gym/h1_train), [H1 Play](https://support.unitree.com/home/en/rl_gym/h1_play), [pinned configurations](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/legged_gym/envs/h1/h1_config.py), [actual root license](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/LICENSE). The later pinned README also documents a G1 C++ physical example with LibTorch CPU 2.7.1 under `deploy/deploy_real/cpp_g1`; that is a separate actuator deployment path, not another source-inspection test.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: reject a mismatched policy manifest offline <a href="#first-result-reject-a-mismatched-policy-manifest-offline" id="first-result-reject-a-mismatched-policy-manifest-offline"></a>

Prerequisites: Python 3 standard library only. Copy the complete original example into a new local file named `policy_contract_check.py`, then run `python3 policy_contract_check.py`. It uses synthetic metadata only; it does not load a `.pt`, YAML package, SDK, simulator or robot connection.

The G1 dimensions/period come from the [pinned simulation config](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/deploy/deploy_mujoco/configs/g1.yaml). The manifest format below is an original teaching format, not a Unitree file schema. Even a passing record does not prove tensor contents, joint order, model dynamics, recurrent behavior or hardware compatibility.

1. Inspect the linked pinned G1 simulation configuration and locate `num_actions`, `num_obs`, `simulation_dt` and `control_decimation`.
2. Save the complete original code below to a new local `policy_contract_check.py` file and run `python3 policy_contract_check.py`. No model download is required.
3. Confirm the acceptance/rejection reasons and final PASS line. Retain the distinction between this synthetic manifest check and a real policy or robot test.

```python
from copy import deepcopy
from math import isfinite, isclose

def check_manifest(m):
    if m.get("model") != "g1_12dof_sim":
        return "reject: model"
    if m.get("observations") != 47 or m.get("actions") != 12:
        return "reject: shape"
    dt, decimation = m.get("physics_dt"), m.get("decimation")
    if (type(dt) not in (int, float) or not isfinite(dt) or dt <= 0
            or type(decimation) is not int or decimation <= 0):
        return "reject: timing"
    if not isclose(dt * decimation, 0.020, rel_tol=0, abs_tol=1e-12):
        return "reject: period"
    if m.get("artifact_sha256") != "a" * 64:
        return "reject: artifact"
    return "accept: synthetic metadata only"

base = dict(model="g1_12dof_sim", observations=47, actions=12,
            physics_dt=0.002, decimation=10, artifact_sha256="a" * 64)
cases = [("matching", {}, "accept: synthetic metadata only"),
         ("other model", {"model": "h1_2"}, "reject: model"),
         ("whole-body assumption", {"actions": 29}, "reject: shape"),
         ("changed period", {"decimation": 5}, "reject: period"),
         ("nonfinite", {"physics_dt": float("nan")}, "reject: timing"),
         ("other artifact", {"artifact_sha256": "b" * 64}, "reject: artifact")]
for label, edits, expected in cases:
    item = deepcopy(base)
    item.update(edits)
    result = check_manifest(item)
    assert result == expected, (label, result)
    print(label + ": " + result)
print("PASS: 6 offline metadata cases; no policy or robot loaded")
```

**Expected result:** one synthetic metadata acceptance and five distinct rejections, followed by the PASS line. The repeated `a` hash is a deliberately synthetic fixture, not a real policy checksum. For a real artifact record, calculate and record its actual hash separately and verify model, ordered joints, normalization and recurrent semantics against the producing run. If this miniature fails, check the copied code and Python environment; changing a robot setting cannot fix an offline manifest mismatch.

Before a later isolated simulator evaluation, record exact checkpoint/export hashes, seed, task/config commit, observation order/scales, action map/default offsets, PD gains, control period and recurrent reset conditions. Compare clips, finite values, contacts, failures and timing across both simulators; record disagreements rather than declaring transfer complete after one visual demonstration.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**The wrong policy is loaded.** Inspect experiment/run/checkpoint selection, then the exported `policy_path` and actual file hash. Latest-run defaults and the H1 article path errors can silently select a different model.

**Tensor sizes match but behavior differs.** Check ordered observations/joints, normalization, previous-action/phase terms, quaternion convention, default offsets, gains, control period and recurrent state. G1 and H1-2 share dimensions in this source while describing different robots.

**Training is slow or a GUI is absent.** Rendering and environment count are separate from compute-device selection. The source recommends headless training and gives viewer toggles; no performance result was measured here.

**Sim2Sim looks stable; may it be deployed?** Stability in one engine is only an intermediate check. The physical examples warn they are illustrative and may fall on damping exit. Model-specific access, firmware, limits, support equipment and effective stop behavior remain required.

**Can the optional SDK2 package be skipped?** It is unnecessary for the offline first result and pure training. Physical deployment is a separate task; installing it does not establish a compatible message family, firmware or robot option.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

### Complete 18-entry article index <a href="#complete-18-entry-article-index" id="complete-18-entry-article-index"></a>

| Source article / update date                                                           | Functional coverage and boundary                                                                                                                                    |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Introduction](https://support.unitree.com/home/en/rl_gym/intro) · 2025-01-11          | Four-stage workflow, task/CLI selection, checkpoint/export paths, Sim2Sim configs, physical deployment boundary and demonstration resources.                        |
| [Examples of Robots](https://support.unitree.com/home/en/rl_gym/example) · 2025-01-11  | Empty grouping node: examples hierarchy only, no technical body.                                                                                                    |
| [G1 Example](https://support.unitree.com/home/en/rl_gym/g1) · 2025-01-11               | Empty G1 grouping node, not an additional manual.                                                                                                                   |
| [1. Train](https://support.unitree.com/home/en/rl_gym/g1_train) · 2025-01-11           | G1 training task/parameters/log paths and rendering toggle.                                                                                                         |
| [2. Play](https://support.unitree.com/home/en/rl_gym/g1_play) · 2025-01-11             | G1 evaluation checkpoint selection, actor exports and visualization.                                                                                                |
| [3. Sim2Sim](https://support.unitree.com/home/en/rl_gym/g1_sim2sim) · 2025-01-11       | G1 MuJoCo configuration and policy-path replacement.                                                                                                                |
| [4. Sim2Real](https://support.unitree.com/home/en/rl_gym/g1_sim2real) · 2025-01-11     | Illustrative hoisted/debug/default-pose/policy stages, interface/config arguments, remote/terminal exit and damping/fall warning; no executable hardware procedure. |
| [H1 Example](https://support.unitree.com/home/en/rl_gym/h1) · 2025-01-11               | Empty H1 grouping node.                                                                                                                                             |
| [1. Train](https://support.unitree.com/home/en/rl_gym/h1_train) · 2025-01-11           | H1 task and common training parameters; incorrect h1\_2 log example retained as discrepancy.                                                                        |
| [2. Play](https://support.unitree.com/home/en/rl_gym/h1_play) · 2025-01-11             | H1 evaluation/exports; incorrect g1 export example retained as discrepancy.                                                                                         |
| [3. Sim2Sim](https://support.unitree.com/home/en/rl_gym/h1_sim2sim) · 2025-01-11       | H1 MuJoCo config and model-specific policy replacement.                                                                                                             |
| [4. Sim2Real](https://support.unitree.com/home/en/rl_gym/h1_sim2real) · 2025-01-11     | H1 physical-stage assumptions, active control and damping/fall exit; not transferred to other models.                                                               |
| [H1\_2 Example](https://support.unitree.com/home/en/rl_gym/h1_2) · 2025-01-11          | Empty H1-2 grouping node.                                                                                                                                           |
| [1. Train](https://support.unitree.com/home/en/rl_gym/h1_2_train) · 2025-01-11         | H1-2 task, training parameters/log location and rendering.                                                                                                          |
| [2. Play](https://support.unitree.com/home/en/rl_gym/h1_2_play) · 2025-01-11           | H1-2 evaluation/checkpoint selection and MLP/LSTM exports.                                                                                                          |
| [3. Sim2Sim](https://support.unitree.com/home/en/rl_gym/h1_2_sim2sim) · 2025-01-11     | H1-2 MuJoCo config and policy path; same dimensions do not mean G1 equivalence.                                                                                     |
| [4. Sim2Real](https://support.unitree.com/home/en/rl_gym/h1_2_sim2real) · 2025-01-11   | H1-2 physical-stage assumptions and control/exit risks; no matched firmware or commissioning claim.                                                                 |
| [install and configure](https://support.unitree.com/home/en/rl_gym/setup) · 2025-01-11 | Ubuntu/GPU/driver, virtual Python environment, pinned Torch/CUDA packages, Isaac Gym check, rsl\_rl1.0.2, RL Gym and optional SDK2 Python.                          |

The four zero-body entries are navigation/grouping nodes, not four additional technical manuals. The nonempty articles' training parameters, exports, simulator configuration, physical-stage warnings and setup dependencies are covered above. Original selected visuals: [G1 training view](https://doc-cdn.unitree.com/static/2025/1/6/8dada4ae13a24db09862f23bb8df7c09_2561x1441.png), [H1 Play view](https://doc-cdn.unitree.com/static/2025/1/11/d374a684cf7a4ec7b7611d45cb6d8626_2561x1441.png), [H1-2 training view](https://doc-cdn.unitree.com/static/2025/1/11/fc673eb896a845598f4c4bfe983a9ed2_2561x1441.png). The articles retain their original demo videos and physical support figures; those are not validation results from this guide.

Pinned downloads/source: [README](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/README.md), [G1 config](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/legged_gym/envs/g1/g1_config.py), [H1](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/legged_gym/envs/h1/h1_config.py), [H1-2](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/legged_gym/envs/h1_2/h1_2_config.py), [MuJoCo script](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/deploy/deploy_mujoco/deploy_mujoco.py), [simulation YAML](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/deploy/deploy_mujoco/configs/g1.yaml), [physical YAML for inspection](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/deploy/deploy_real/configs/g1.yaml), [LICENSE](https://github.com/unitreerobotics/unitree_rl_gym/blob/276801e46c5d433564f24658bac64f254b7d2d4b/LICENSE). Related canonical references: [SDK2](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development), [ROS2](https://wiki.openelab.io/robotics/unitree/unitree-ros2-integration), [G1](https://wiki.openelab.io/robotics/unitree/unitree-g1-standard-edu-development-guide).

### Original figure and media link index <a href="#original-figure-and-media-link-index" id="original-figure-and-media-link-index"></a>

These are links to the original article resources, not newly measured results or reproduced manuals. All linked media retain their source context.

<details>

<summary>Introduction — 10 source figures/media</summary>

[Resource 1](https://oss-global-cdn.unitree.com/static/32f06dc9dfe4452dac300dda45e86b34.GIF) · [Resource 2](https://oss-global-cdn.unitree.com/static/244cd5c4f823495fbfb67ef08f56aa33.GIF) · [Resource 3](https://oss-global-cdn.unitree.com/static/78c61459d3ab41448cfdb31f6a537e8b.GIF) · [Resource 4](https://oss-global-cdn.unitree.com/static/ba006789e0af4fe3867255f507032cd7.GIF) · [Resource 5](https://oss-global-cdn.unitree.com/static/fa04e73966934efa9838e9c389f48fa2.GIF) · [Resource 6](https://oss-global-cdn.unitree.com/static/83ed59ca0dab4a51906aff1f93428650.GIF) · [Resource 7](https://oss-global-cdn.unitree.com/static/7ab4e8392e794e01b975efa205ef491e.GIF) · [Resource 8](https://oss-global-cdn.unitree.com/static/2905e2fe9b3340159d749d5e0bc95cc4.GIF) · [Resource 9](https://oss-global-cdn.unitree.com/static/fa07b2fd2ad64bb08e6b624d39336245.GIF) · [Resource 10](https://oss-global-cdn.unitree.com/static/a88915e3523546128a79520aa3e20979.GIF)

</details>

<details>

<summary>1. Train — 1 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2025/1/6/8dada4ae13a24db09862f23bb8df7c09_2561x1441.png)

</details>

<details>

<summary>2. Play — 1 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2025/1/6/58795066861148a9a56c77629cec5a5c_2561x1441.png)

</details>

<details>

<summary>3. Sim2Sim — 1 source figures/media</summary>

[Resource 1](https://oss-global-cdn.unitree.com/static/5aa48535ffd641e2932c0ba45c8e7854.mp4)

</details>

<details>

<summary>4. Sim2Real — 7 source figures/media</summary>

[Resource 1](https://oss-global-cdn.unitree.com/static/ea12b7fb3bb641b3ada9c91d44d348db.mp4) · [Resource 2](https://doc-cdn.unitree.com/static/2023/9/6/0f51cb9b12f94f0cb75070d05118c00a_980x816.jpg) · [Resource 3](https://oss-global-cdn.unitree.com/static/b84485f386994ef08b0ccfa928ab3830_825x484.png) · [Resource 4](https://oss-global-cdn.unitree.com/static/0818dcf7a6874b92997354d628adcacd.mp4) · [Resource 5](https://doc-cdn.unitree.com/static/2025/1/11/52221fd0b5384119ba13463cb598cc7d_1920x1080.png) · [Resource 6](https://doc-cdn.unitree.com/static/2025/1/11/4a929773afd547de8099f4a6fa9e5105_1920x1080.png) · [Resource 7](https://doc-cdn.unitree.com/static/2025/1/11/ec537455cb65488693dec3952e3ea412_1920x1080.png)

</details>

<details>

<summary>1. Train — 1 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2025/1/11/2a7f29aeef9c476891f7be552c0587d1_2561x1441.png)

</details>

<details>

<summary>2. Play — 1 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2025/1/11/d374a684cf7a4ec7b7611d45cb6d8626_2561x1441.png)

</details>

<details>

<summary>3. Sim2Sim — 1 source figures/media</summary>

[Resource 1](https://oss-global-cdn.unitree.com/static/8934052becd84d08bc8c18c95849cf32.mp4)

</details>

<details>

<summary>4. Sim2Real — 7 source figures/media</summary>

[Resource 1](https://oss-global-cdn.unitree.com/static/d4e0cdd8ce0d477fb5bffbb1ac5ef69d.mp4) · [Resource 2](https://doc-cdn.unitree.com/static/2023/9/6/0f51cb9b12f94f0cb75070d05118c00a_980x816.jpg) · [Resource 3](https://oss-global-cdn.unitree.com/static/b84485f386994ef08b0ccfa928ab3830_825x484.png) · [Resource 4](https://oss-global-cdn.unitree.com/static/ea0084038d384e3eaa73b961f33e6210.mp4) · [Resource 5](https://doc-cdn.unitree.com/static/2025/1/11/33b7d85be2544e2385fd68bca4e2c59d_1920x1080.png) · [Resource 6](https://doc-cdn.unitree.com/static/2025/1/11/012095c0cfaa4b3e9a6a6609766de32f_1920x1080.png) · [Resource 7](https://doc-cdn.unitree.com/static/2025/1/11/5440efb0418a4c7a89088f643fd9b5f4_1920x1080.png)

</details>

<details>

<summary>1. Train — 1 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2025/1/11/fc673eb896a845598f4c4bfe983a9ed2_2561x1441.png)

</details>

<details>

<summary>2. Play — 1 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2025/1/11/a01293ca80c943a281fe8da624cf93b1_2561x1441.png)

</details>

<details>

<summary>3. Sim2Sim — 1 source figures/media</summary>

[Resource 1](https://oss-global-cdn.unitree.com/static/ee7ee85bd6d249989a905c55c7a9d305.mp4)

</details>

<details>

<summary>4. Sim2Real — 7 source figures/media</summary>

[Resource 1](https://oss-global-cdn.unitree.com/static/8120e35452404923b854d9e98bdac951.mp4) · [Resource 2](https://doc-cdn.unitree.com/static/2023/9/6/0f51cb9b12f94f0cb75070d05118c00a_980x816.jpg) · [Resource 3](https://oss-global-cdn.unitree.com/static/b84485f386994ef08b0ccfa928ab3830_825x484.png) · [Resource 4](https://oss-global-cdn.unitree.com/static/12d041a7906e489fae79d55b091a63dd.mp4) · [Resource 5](https://doc-cdn.unitree.com/static/2025/1/11/3c405f11a9214cbfbe936253b9d3ec5e_1920x1080.png) · [Resource 6](https://doc-cdn.unitree.com/static/2025/1/11/daecd98335c547ee8a9ac963cbd2392a_1920x1080.png) · [Resource 7](https://doc-cdn.unitree.com/static/2025/1/11/df0d2300acd54b57a7f08b36688cb5f7_1920x1080.png)

</details>

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed **2026-11-24** against all 18 actual portal entries, distinguishing four empty grouping nodes, and the pinned sources. The original six-case metadata example was executed offline; it does not load or validate a learned model.

**Not run:** package/SDK installation, vendor code import/build/execution, GPU training, Gym/MuJoCo/ROS/DDS, policy loading and physical power/motion/flashing. Source-bounded draft: the public first result is reproducible offline, while simulator results and all delivered-hardware compatibility remain unverified.

**Related documentation:** [Unitree model and development directory](./).
