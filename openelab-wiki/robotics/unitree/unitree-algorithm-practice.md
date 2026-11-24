---
description: >-
  Inspect unitree_guide states, ROS1 simulation settings and timing contracts,
  analyze synthetic overruns, and distinguish legacy model and physical SDK
  boundaries.
---

# Unitree quadruped control practice: FSM, simulation and timing

{% hint style="info" %}
**Shared algorithm-development guide: `unitree_guide` FSM and simulator architecture.** This is a tutorial, not an additional robot or SKU. The project targets legacy Go1/A1 paths; it is not SDK2 or a ROS2 controller. Use the [Unitree SDK2 reference](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development), [ROS2 guide](https://wiki.openelab.io/robotics/unitree/unitree-ros2-integration) and [manufacturer model directory](https://wiki.openelab.io/robotics/unitree) for their separate scopes.
{% endhint %}

`unitree_guide` is the software companion to Unitree's quadruped modeling/control book. It organizes state estimation, gait generation, IO and finite-state behavior into an educational controller. The English portal provides seven entries, including two short chapter introductions, an FSM explanation, networking, a Gazebo quick start and troubleshooting. A basic controller is not a production safety system. [About the project](https://support.unitree.com/home/en/Algorithm_Practice/about_unitreeguide)

## Product overview <a href="#product-overview" id="product-overview"></a>

The source baseline is **`unitree_guide` commit `fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb`**. Its build file distinguishes `SIMULATION` and `REAL_ROBOT`, accepts Go1/A1 model choices and architecture-specific libraries, and rejects both modes simultaneously enabled or disabled. The default source selects Go1 simulation, with real-robot support off. This is a configuration fact, not proof that an inherited binary was built with those settings. [Pinned README](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/README.md), [CMake settings](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/CMakeLists.txt)

The accompanying book is identified as Chinese-only in the article; this page is an original English engineering interpretation of the available public documentation, not a translation or reproduction of the entire book. The controller is introductory and may need tuning or more advanced control methods for a different task. [About article](https://support.unitree.com/home/en/Algorithm_Practice/about_unitreeguide)

## Applications <a href="#applications" id="applications"></a>

* **FSM study:** separate a controller's internal state transitions from a robot's physical posture and independently qualified stop behavior.
* **Timing analysis:** check whether IO, gait/estimator updates, control and scheduling fit the intended 2 ms iteration budget.
* **Simulator project preservation:** map Gazebo descriptions, ROS messages, build options and launch files before modifying a legacy workspace.
* **Algorithm development:** add a state with explicit entry/exit/reset behavior and test logic offline before any isolated simulator work.

No observed source qualifies this controller for G1, H1/H1-2, H2/H2-X, G1+, R1 or all legacy quadrupeds. Similar motor counts do not transfer its SDK, gains, calibration or communication protocol.

## Specifications <a href="#specifications" id="specifications"></a>

| Requirement / contract                | Source detail                                                                     | Engineering interpretation                                                                                                        |
| ------------------------------------- | --------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Historical ROS environment            | Ubuntu 18.04/Melodic recommended; portal also mentions 20.04/Noetic               | ROS1 generation, not a ROS2 DDS recipe                                                                                            |
| Dependencies                          | `unitree_guide`, `unitree_ros`, standalone `unitree_legged_msgs`, LCM and pthread | Message package is extracted from `unitree_ros_to_real`; the physical `unitree_legged_real` package is not a simulator dependency |
| Debug dependency                      | Python2 needed only when DEBUG is enabled; default off                            | Do not add a legacy interpreter to satisfy an unrelated runtime symptom                                                           |
| Source build                          | CMake ≥3.14; C++11; model Go1/A1; amd64/arm64 library choices                     | Exact binary architecture and mode must be retained                                                                               |
| Intended iteration                    | 500 Hz / 0.002 s / 2000 µs                                                        | Scheduling target, not measured worst-case execution time                                                                         |
| Legacy physical link choices in CMake | A1 library path labelled SDK 3.2; Go1 path labelled 3.8.0                         | Distinct from separately reviewed 3.3.1 and 3.8.6 releases; no silent protocol upgrade                                            |

[QuickStart](https://support.unitree.com/home/en/Algorithm_Practice/quickstart), [FAQ](https://support.unitree.com/home/en/Algorithm_Practice/faq), [pinned build file](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/CMakeLists.txt). The portal discourages virtual machines for controller efficiency; this is not evidence that every bare-metal host meets deadlines. No build or real-time measurement was performed here.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

The network article illustrates an A1 main board plus UP Board and Raspberry Pi/TX2, and a Go1 EDU main board, Pi 4B and three Nano boards linked through a switch. Those are illustrated developer configurations, not a universal retail board inventory. Its example main-controller address is `192.168.123.10`, and its file-copy example targets a Go1 Pi at `.161`. [Network framework and original diagrams](https://support.unitree.com/home/en/Algorithm_Practice/networkframework)

Ping establishes limited reachability, not compatible state, command authority or freshness. File copying changes a target filesystem and is not needed for the offline first result. This tutorial supplies no model-specific pinout, charger, startup, hoist, remote-stop sequence or physical holding guarantee. Existing robots require their exact model/edition/firmware/manual and approved protection; using simulator messages is not evidence of a compatible real-robot bridge.

For later simulation, use a separate environment with no robot NIC or real-robot ROS bridge, keep `SIMULATION=ON` and `REAL_ROBOT=OFF` in the actual inspected build, and check which launch files/plugins run. The provided `gazeboSim.launch` loads model/controllers and unpauses the spawned model; it is not merely a static viewer. Its `user_debug` option affects simulated suspension and is not a real hoist instruction. [Pinned launch file](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/launch/gazeboSim.launch)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### FSM behavior and authority <a href="#fsm-behavior-and-authority" id="fsm-behavior-and-authority"></a>

| State / manager item     | Documented role                                                            | Boundary                                                                           |
| ------------------------ | -------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Passive                  | Desired joint velocity zero and `Kp=0` produce damping behavior            | Damping can allow descent under gravity; not zero torque, a brake or a stable hold |
| FixedStand               | Interpolates toward specified joint angles                                 | An active posture target, not proof of safe startup                                |
| FreeStand                | Body height/posture adjustment while standing                              | Requires an appropriate source/model/control configuration                         |
| Trotting                 | Translation/turning and stop commands                                      | Active gait control; simulator keyboard inputs are not physical remote buttons     |
| Other constructed states | BalanceTest, SwingTest, StepTest; optional MoveBase                        | Source presence is not a validated task or hardware support guarantee              |
| NORMAL → CHANGE          | `checkChange()` chooses the next state; the manager schedules a transition | Different from immediately changing joint power or mode                            |
| CHANGE → NORMAL          | Current `exit()`, next `enter()`, then `run()`                             | Reset per-state flags for re-entry rather than retaining stale intent              |

[FSM article](https://support.unitree.com/home/en/Algorithm_Practice/fsm), [pinned implementation](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/src/FSM/FSM.cpp). The source initializes Passive and NORMAL. Each iteration performs `sendRecv`, gait-wave generation and estimator updates, evaluates `checkSafty`, then executes state logic and timing. The spelling `checkSafty` is actual code; the prose also mentions `checkSafety`. `sendRecv` includes sending, so this loop is not a read-only observer.

The safety predicate checks `R(2,2)<0.5` from the body rotation matrix, corresponding to a tilt boundary around 60° under a valid rotation convention. Its failure asks the IO layer for Passive; the manager still continues through its current iteration logic. This one threshold does not validate sensor freshness, finite/normalized orientation, collision, joint limits, control authority or physical emergency-stop operation. Do not disable it to reproduce the article's extreme-motion examples. [FSM safety discussion and figure](https://support.unitree.com/home/en/Algorithm_Practice/fsm)

### Timing implementation versus prose <a href="#timing-implementation-versus-prose" id="timing-implementation-versus-prose"></a>

The pinned `absoluteWait` implementation warns when `elapsed > waitTime`, otherwise sleeps in 50 µs increments while `elapsed < waitTime`. The portal's explanatory subtraction/sign wording is confusing; use the actual predicate when analyzing logs. Its clock is `gettimeofday`, so wall-clock adjustment can affect elapsed calculations. For a new measurement tool, use a monotonic clock and record complete iteration time separately from CPU utilization. This is an engineering improvement, not a claim that the vendor code has already changed. [Pinned timing header](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/include/common/timeMarker.h)

The FAQ's example reports 4033 µs against a 2000 µs budget. That is an overrun of 2033 µs, not evidence of an adequate 500 Hz controller. The FAQ suggests reducing output, avoiding VMs, obtaining scheduling privileges and splitting work into threads. Those changes require actual measurements and synchronization review; more threads or elevated permissions do not guarantee a deadline. [Timing FAQ](https://support.unitree.com/home/en/Algorithm_Practice/faq)

### Build and source workflow <a href="#build-and-source-workflow" id="build-and-source-workflow"></a>

The portal quick start describes catkin build, then a Gazebo launch and the `junior_ctrl` executable. It documents simulator keys 2 for Passive→FixedStand, 4 for FixedStand→Trotting, translational/turn keys and space to stop. These are **active simulated control actions**, presented here as source behavior rather than a first-run sequence. The FSM article's directional-key wording differs from the README; inspect the actual input mapping instead of treating the prose as an authoritative key map. Physical use in the article is remote-controlled, with different transition conditions. [QuickStart](https://support.unitree.com/home/en/Algorithm_Practice/quickstart), [FSM](https://support.unitree.com/home/en/Algorithm_Practice/fsm)

The portal recommends elevated controller launch for real-time scheduling, while the pinned README shows an unprivileged launch. Record that source difference. The FAQ's system-wide library-path edit and `ldconfig` remedy can affect other applications; first identify the specific missing library, architecture and runtime environment. Do not change global configuration or use elevated execution to make a source-inspection example work.

Root license read: BSD-3-Clause. Simulator assets, physical libraries and dependencies may carry separate notices. No vendor code is reproduced beyond short identifiers and contract descriptions.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: inspect mode selection and analyze a synthetic timing trace <a href="#first-result-inspect-mode-selection-and-analyze-a-synthetic-timing-trace" id="first-result-inspect-mode-selection-and-analyze-a-synthetic-timing-trace"></a>

Prerequisites: a browser and Python 3 standard library. No ROS, robot, simulator or vendor library is needed.

1. Open the [pinned CMake file](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/CMakeLists.txt). Locate Go1/A1 choices, `SIMULATION`, `REAL_ROBOT`, their mutual-exclusion test and the two distinct historical SDK paths. Record the defaults without building.
2. Open [`FSM.cpp`](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/src/FSM/FSM.cpp). Identify initial Passive/NORMAL, the IO/gait/estimator order and the `exit`→`enter` transition. Note that the loop sends commands.
3. Open [`timeMarker.h`](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/include/common/timeMarker.h). Confirm the overrun comparison and clock type. Then copy the complete original example below to `iteration_budget_check.py` and run `python3 iteration_budget_check.py`.

```python
from math import isfinite

def classify_us(elapsed):
    if type(elapsed) not in (int, float) or not isfinite(elapsed) or elapsed < 0:
        return "reject invalid duration"
    if elapsed > 2000:
        return f"overrun by {elapsed - 2000:g} us"
    return f"within budget; margin {2000 - elapsed:g} us"

cases = [(1500, "within budget; margin 500 us"),
         (2000, "within budget; margin 0 us"),
         (4033, "overrun by 2033 us"),
         (-1, "reject invalid duration"),
         (float("nan"), "reject invalid duration")]
for elapsed, expected in cases:
    result = classify_us(elapsed)
    assert result == expected, result
    print(result)
print("PASS: 5 synthetic timing cases; no controller executed")
```

**Expected result:** two within-budget records, one explicit overrun, two invalid-duration rejections and a PASS line. This evaluates only supplied synthetic elapsed times. It does not measure a host, promise 500 Hz, inspect a compiled binary or validate the physical controller. If it fails, check the copied file; if a later measured trace overruns, retain the run/configuration and investigate the timing components before changing privileges, threads or gains.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Missing `.so` during launch.** Identify the missing file, actual binary architecture and ROS/library environment first. The portal's global search-path remedy is a historical option, not proof that an incompatible binary can be repaired with a path.

**Scheduler setup failed.** The source explains that real-time scheduling privileges may be absent. A process continuing to run does not establish its deadlines. Record scheduler policy and latency measurements in an isolated test; do not apply a blanket elevated launch here.

**`-llcm` cannot be found.** This is a link/dependency issue. Match LCM installation and target architecture; it is unrelated to robot reachability or DDS discovery. [FAQ items 1–5](https://support.unitree.com/home/en/Algorithm_Practice/faq)

**The simulator appears unresponsive.** Distinguish a paused/unsupported launch, missing controller and keyboard focus. The source controller changes simulated state, and a “suspended” debug model is a simulator setting, not physical support. [QuickStart](https://support.unitree.com/home/en/Algorithm_Practice/quickstart), [FAQ item 6](https://support.unitree.com/home/en/Algorithm_Practice/faq)

**Does Passive make the robot safe to touch?** No. The article describes damping and gravitational descent. Power state, hot joints, stored loads, external contact and model-specific stop behavior remain separate concerns.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

### Complete seven-entry article index <a href="#complete-seven-entry-article-index" id="complete-seven-entry-article-index"></a>

| Source article / update date                                                                                   | Functional coverage and boundary                                                                                                                  |
| -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| [About unitree\_guide](https://support.unitree.com/home/en/Algorithm_Practice/about_unitreeguide) · 2024-01-02 | Introductory quadruped controller accompanying Chinese book; tuning and performance limitations.                                                  |
| [Concept](https://support.unitree.com/home/en/Algorithm_Practice/concept) · 2023-12-26                         | Short concept grouping introduction, not a separate technical implementation.                                                                     |
| [FSM](https://support.unitree.com/home/en/Algorithm_Practice/fsm) · 2023-12-26                                 | Passive/FixedStand/FreeStand/Trotting; transition manager, send/gait/estimator ordering, entry/exit reset, tilt predicate and timing discrepancy. |
| [Network framework](https://support.unitree.com/home/en/Algorithm_Practice/networkframework) · 2023-12-26      | A1/Go1 EDU illustrated compute/switch roles; ping reachability versus protocol qualification and file-copy side effects.                          |
| [development](https://support.unitree.com/home/en/Algorithm_Practice/development) · 2023-12-26                 | Short software-engineering chapter introduction; no extra API body.                                                                               |
| [QuickStart](https://support.unitree.com/home/en/Algorithm_Practice/quickstart) · 2023-12-26                   | ROS1 environment, LCM/pthread/Python2 condition, package boundaries, catkin/Gazebo/controller phases and active simulation key behavior.          |
| [FAQ](https://support.unitree.com/home/en/Algorithm_Practice/faq) · 2023-12-26                                 | All six topics: dynamic libraries, privileged/direct launch versus rosrun, scheduler failure, 2ms overruns, LCM linking and simulated suspension. |

Selected original figures: [FSM transitions](https://doc-cdn.unitree.com/static/2023/12/26/58e204e7550e47d6b4db8be0d0c92de5_1920x1080.jpg), [tilt protection illustration](https://doc-cdn.unitree.com/static/2023/10/12/340ea06e2b03497595a06bf4d9cf0ef9_1182x901.png), [Go1 network architecture](https://doc-cdn.unitree.com/static/2023/9/22/128a2fc106bf4b749f5eba816c9395d9_1920x1080.png). The figures remain linked in their original context; they are not newly verified wiring or physical protection drawings.

Pinned resources: [README](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/README.md), [build configuration](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/CMakeLists.txt), [launch](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/launch/gazeboSim.launch), [FSM implementation](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/src/FSM/FSM.cpp), [timing helper](https://github.com/unitreerobotics/unitree_guide/blob/fdf4d23de6affe8ee38fb4d892f61053fa1fcbcb/unitree_guide/include/common/timeMarker.h). Related references: [manufacturer/model directory](https://wiki.openelab.io/robotics/unitree), [SDK2 state](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development), [ROS2 integration](https://wiki.openelab.io/robotics/unitree/unitree-ros2-integration). This tutorial does not establish those newer protocols for a legacy robot.

### Original figure and media link index <a href="#original-figure-and-media-link-index" id="original-figure-and-media-link-index"></a>

These are links to the original article resources, not newly measured results or reproduced manuals. All linked media retain their source context.

<details>

<summary>About unitree_guide — 1 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2023/9/22/5da5e4ec9080498c9a7c9f7d6c943191_800x800.png)

</details>

<details>

<summary>FSM — 7 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2023/9/22/ca1edbaea656458ebe70d8f29768e381_1168x708.gif) · [Resource 2](https://doc-cdn.unitree.com/static/2023/9/22/42bb3784f25a4f0ea764e5ec839907ce_1168x708.gif) · [Resource 3](https://doc-cdn.unitree.com/static/2023/9/22/da0b45e7fd0741cf91284dac6b793a3f_1168x708.gif) · [Resource 4](https://doc-cdn.unitree.com/static/2023/9/22/93ae25d5a8fc44a285bb1205d7691e93_1168x708.gif) · [Resource 5](https://doc-cdn.unitree.com/static/2023/12/26/58e204e7550e47d6b4db8be0d0c92de5_1920x1080.jpg) · [Resource 6](https://doc-cdn.unitree.com/static/2023/9/22/f6b2a6a4aac74cf5b88e64aa7e676525_713x139.png) · [Resource 7](https://doc-cdn.unitree.com/static/2023/10/12/340ea06e2b03497595a06bf4d9cf0ef9_1182x901.png)

</details>

<details>

<summary>Network framework — 3 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2023/9/22/fba9434b1e8c456dbb3390eb4987d5bb_1920x1080.png) · [Resource 2](https://doc-cdn.unitree.com/static/2023/9/22/128a2fc106bf4b749f5eba816c9395d9_1920x1080.png) · [Resource 3](https://doc-cdn.unitree.com/static/2023/9/22/dcf23a258a874ec6a6cd147a8d66819e_1168x708.gif)

</details>

<details>

<summary>QuickStart — 9 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2023/9/21/2b612028aff345f1803b45bc877f477e_728x434.png) · [Resource 2](https://doc-cdn.unitree.com/static/2023/9/21/274cef931ae641a699b6d877e91102b5_731x159.png) · [Resource 3](https://doc-cdn.unitree.com/static/2023/9/21/ec632042ab114f989a1a75d5f55a1cd7_777x470.png) · [Resource 4](https://doc-cdn.unitree.com/static/2023/9/21/950926c9f13944dc97da7620a5f6d962_733x480.png) · [Resource 5](https://doc-cdn.unitree.com/static/2023/9/21/1d36a5876f0f484ead276c0d37d0f7b4_1707x840.png) · [Resource 6](https://doc-cdn.unitree.com/static/2023/9/21/0b09f59153ec446ea90b001b3e41a302_728x232.png) · [Resource 7](https://doc-cdn.unitree.com/static/2023/9/21/35886748016449b4b76fb3806e0bf4d7_1380x578.gif) · [Resource 8](https://doc-cdn.unitree.com/static/2023/9/21/b683575b7c6f484ab53981f36ccdc386_1380x578.gif) · [Resource 9](https://doc-cdn.unitree.com/static/2023/12/26/ffcd23ff39264ff59cd3ed76b643bb11_1920x1080.jpg)

</details>

<details>

<summary>FAQ — 7 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2023/9/22/f5f5950b1ebc48f588a6769421b83545_726x108.png) · [Resource 2](https://doc-cdn.unitree.com/static/2023/12/26/915b55d96b2c4815a64b93915ded6b87_1356x301.jpg) · [Resource 3](https://doc-cdn.unitree.com/static/2023/9/22/cdbeb8db33664919a982bcd185734e87_712x97.png) · [Resource 4](https://doc-cdn.unitree.com/static/2023/9/22/f6b2a6a4aac74cf5b88e64aa7e676525_713x139.png) · [Resource 5](https://doc-cdn.unitree.com/static/2023/12/26/472809178d344bf9b3f9108ddf6a49da_1170x668.jpg) · [Resource 6](https://doc-cdn.unitree.com/static/2023/9/27/3b2483af24b94c2ea40b8d5b71864264_1228x523.png) · [Resource 7](https://doc-cdn.unitree.com/static/2023/9/27/47c298117ad142089667a656e25ffd11_1101x747.png)

</details>

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed **2026-11-24** against all seven English portal entries and the pinned repository files. The original five-case timing example was run offline. Source comparisons retain timing prose, privilege and SDK-version differences instead of merging them into a single physical procedure.

**Not run:** ROS/SDK installation, vendor builds/imports/controller execution, Gazebo, real-time scheduling changes, robot communication or hardware motion. Source-bounded draft: useful for architecture/source study; future simulator tests need isolation and measured results, and physical use needs a separate exact-model qualification.

**Related documentation:** [Unitree model and development directory](./).
