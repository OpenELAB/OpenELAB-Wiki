---
description: >-
  Current ROS 2 setup, verified package build and read-only
  identity/capability/joint telemetry.
---

# Tutorial 2 — LINKERBOT ROS 2 Installation and Read-Only Joint State

{% hint style="info" %}
[**L6 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l6-11) · [**L20 Lite**](https://openelab.io/products/linker-hand-linkerbot-l20-lite) · [**L20**](https://openelab.io/products/linker-hand-linkerbot-l20-21) · [**L30 Tendon**](https://openelab.io/products/linker-hand-linkerbot-l30-l30) · [**O6**](https://openelab.io/products/linker-hand-linkerbot-o6-11)

**Family scope:** O20 and O30 store identity pending; do not substitute SKU/firmware data from another model.
{% endhint %}

[**Complete seven-manual library — all 137 original PDF pages and downloads**](../source-library/)

[LINKERBOT developer series](./)

## Product overview

This tutorial implements the manufacturer's **read-only first working result** through the current [Linkerbot Hand ROS 2 SDK](https://github.com/linker-bot/linkerbot-hand-ros2-sdk). It separates software-only installation checks from live device discovery, and never sends an angle, gain, torque or motion-target command as part of the initial test.

## Applications

* Prepare Ubuntu/ROS 2 and the current manufacturer transport and Python modules.
* Verify a driver build before a physical hand is connected.
* Discover actual hand identity, controlled joint count and angle-state validity.

## Specifications

| Layer               | Source-supported target                                              |
| ------------------- | -------------------------------------------------------------------- |
| Ubuntu 22.04        | ROS 2 **Humble**, Python **3.10**                                    |
| Ubuntu 24.04        | ROS 2 **Jazzy**, Python **3.12**                                     |
| Active joint counts | L6/O6 **6**; L20 Lite **10**; L20/O20 **16**; L30 **17**; O30 **20** |
| Packages            | `linkerbot_hand_msgs`, `linkerbot_hand_ros`, `linkerbot_hand_gui`    |
| Read-only channels  | `/linkerbot_hand/capabilities`, `/linkerbot_hand/state/angles`       |

## Hardware and connections

1. Read the [hardware/bus preflight](linkerbot-tutorial-1-hardware-and-buses.md), confirming the actual purchased model, adapter, bus and supply. Keep the workspace and fingers clear.
2. Use a separate CAN/CAN-FD channel for each hand as documented in the SDK.
3. **Do not power the conflicting L30 JQ variant or unidentified O20/O30 sold configuration** solely to complete a tutorial. The software-only build stage requires no physical robot.
4. Keep device stop/disconnect readily available. A successful ROS topic alone is not evidence of safe mechanical operation.

## Software and development resources

* [Official ROS 2 quick start](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/quick_start.md): exact apt/venv, three repositories, colcon and lifecycle.
* [Connection and adapter setup](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/connection.md).
* [Model differences](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md).

## Getting started

### First working result: build and query angles

1. Install your Ubuntu release's matching ROS 2, `rosdep`, `colcon`, `git`, `can-utils` and Python venv packages from the **linked quick start**. For Ubuntu 22.04, initialize Humble:

```bash
export LINKERBOT_ROS_DISTRO=humble
source /opt/ros/humble/setup.bash
/usr/bin/python3 -m venv --system-site-packages "$HOME/venvs/linkerbot-hand-$ROS_DISTRO"
source "$HOME/venvs/linkerbot-hand-$ROS_DISTRO/bin/activate"
```

For Ubuntu 24.04, use the matching Jazzy installation and Python 3.12 rather than the Humble commands.

2. Clone and install the manufacturer current `main` repositories in a vendor-ROS-compatible shell:

```bash
mkdir -p ~/linkerbot_deps
cd ~/linkerbot_deps
git clone --branch main --depth 1 https://github.com/linker-bot/linkerbot-transport.git linkerbot-transport
git clone --branch main --depth 1 https://github.com/linker-bot/linkerbot-hand-python-sdk.git linkerbot-hand
python -m pip install -e './linkerbot-transport[all]' -e ./linkerbot-hand
mkdir -p "$HOME/linkerbot_$ROS_DISTRO"_ws/src
cd "$HOME/linkerbot_$ROS_DISTRO"_ws/src
git clone --branch main --depth 1 https://github.com/linker-bot/linkerbot-hand-ros2-sdk.git linkerbot-hand-ros
```

3. Use the vendor's `rosdep` and `colcon` instructions to install dependencies and build. After sourcing the workspace, check without hardware:

```bash
ros2 pkg prefix linkerbot_hand_ros
ros2 interface show linkerbot_hand_msgs/msg/HandJointCommand
```

**Expected software-only result:** installed ROS package prefix and the typed message definition. This **does not prove a live robot is connected**.

4. Only after the physical device, voltage and appropriate CAN/CAN FD adapter have been verified, launch one hand:

```bash
ros2 launch linkerbot_hand_ros hand.launch.py discover:=true
```

5. In a second terminal with the same ROS environment, read (do not command) the hand:

```bash
ros2 lifecycle get /linkerbot_hand
ros2 topic echo --once --qos-durability transient_local /linkerbot_hand/capabilities
ros2 topic echo --once --qos-reliability best_effort /linkerbot_hand/state/angles
```

**Expected live result:** lifecycle `active`, `identity.verified=true` and angle `meta.valid=true`, `meta.stale=false` with model-appropriate joint names and count. Record **actual** data and source revisions, not copied sample output.

6. Close connection with the OEM lifecycle sequence:

```bash
ros2 lifecycle set /linkerbot_hand deactivate
ros2 lifecycle set /linkerbot_hand cleanup
```

## Complete build checkpoint and source pairing

The manufacturer’s quick-start clone URL `linkerbot-hand-ros-sdk` currently redirects to `linkerbot-hand-ros2-sdk`; the commands above use the verified canonical ROS 2 URL. This differs from the older `linkerhand-ros-sdk` repository printed in the PDF appendices. Use matching current Transport, Hand Python and ROS sources, retaining each checkout’s commit and OS/firmware record. The current ROS 2 repository declares an MIT license.

After installing the selected distribution’s `rosdep`/`colcon` prerequisites and both editable Python dependencies, build in the same ROS/system-Python environment:

```bash
cd "$HOME/linkerbot_${ROS_DISTRO}_ws"
rosdep install --from-paths src --ignore-src -y --rosdistro "$ROS_DISTRO"
rosdep check --from-paths src --ignore-src --rosdistro "$ROS_DISTRO"
python -m colcon build --symlink-install --cmake-args -DPython3_EXECUTABLE="$(command -v python)"
source "$HOME/linkerbot_${ROS_DISTRO}_ws/install/setup.bash"
python -c 'import linkerbot_transport, linkerbot_hand; print("Python dependencies: OK")'
ros2 pkg prefix linkerbot_hand_msgs
ros2 pkg prefix linkerbot_hand_ros
ros2 pkg prefix linkerbot_hand_gui
```

**Expected result:** dependency checks succeed and package prefixes point to this workspace. The text printed by the Python command is a prescribed checkpoint, not a test run performed for this wiki. Use `--system-site-packages` with the host’s matching system Python; do not mix Humble/Jazzy terminals or upgrade Ubuntu-provided setuptools blindly. GUI assets are separate and are not needed for the command-line state check.

Discovery requires an already configured adapter. `channels:=can0` restricts scanning to a verified channel. Exactly one complete candidate is expected; zero/multiple candidates are an identity problem to resolve before motion. Deactivation keeps the device connection; cleanup closes it. No active target-publishing application should be left running during the state-only check.

Source: [pinned official quick start](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/8d56b3355d2cfcd90e4e3c6b377ebceb7a5c09ac/linkerbot_hand_ros/docs/quick_start.md).

## Troubleshooting and FAQs

**The software builds but no device appears.** Inspect OS adapter device, bus bitrate, firmware, model identity, and whether another process holds the interface. Do not send a motion command for discovery.

**Why do I see 10 angles for an L20 Lite?** The manual specifies **10 active joints and 10 passive joints**, despite a storefront title mentioning 20 DOF.

**Can I run `angle_command` to verify connectivity?** No. The current SDK says it moves the hand; first verify valid and fresh read-only state.

## Downloads and technical documents

* [Manufacturer current ROS 2 quick start](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/quick_start.md).
* [SDK model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md).
* [Model-specific OEM manuals](../).

## References and validation

* Seven uploaded Linkerbot manuals, examined 2026-11-21.
* [Linkerbot current ROS 2 source, quick start](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/quick_start.md), reviewed 2026-11-21.

**Documentation:** source-reviewed. **Software execution:** not run. **Hardware validation:** not run. Unverified store/power/bus pairings block the corresponding physical steps.

## Complete source coverage and revision checkpoints

| Model / revision                               | Complete supplied reference                            | Key interpretation                                          |
| ---------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------------- |
| L6 V1.4 · 2026-05-18                           | [15 PDF pages](../source-library/complete-l6.md)       | LED and speed-unit note                                     |
| L20 Lite V1.0 · 2025-09-11                     | [19 PDF pages](../source-library/complete-l20-lite.md) | 10 active / 20 physical joints; optional sensor variants    |
| L20 V1.3 · 2026-08-04                          | [14 PDF pages](../source-library/complete-l20.md)      | 24–48 V table / 24 V connector; V1.3 joint angles           |
| L30 Standard (tendon-driven) V1.3 · 2025-10-27 | [17 PDF pages](../source-library/complete-l30.md)      | Tendon/wrist model; voltage, bus and rate conflicts         |
| O6 V1.4 · 2026-07-21                           | [17 PDF pages](../source-library/complete-o6.md)       | Optional 4×10 tactile; actual protocol option               |
| O20 V1.2 · 2026-06-05                          | [30 PDF pages](../source-library/complete-o20.md)      | 30 Hz tactile / 1000 Hz communication; unique connector     |
| O30 V1.0 · 2026-07-10                          | [25 PDF pages](../source-library/complete-o30.md)      | 6×11 pressure array; unique connector and descriptor layout |

Current software reference: [ROS 2 source at `8d56b3355d2c`](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/8d56b3355d2cfcd90e4e3c6b377ebceb7a5c09ac/README.md), reviewed 22 November 2026. This is a documentation review; **software execution and hardware validation were not run**.
