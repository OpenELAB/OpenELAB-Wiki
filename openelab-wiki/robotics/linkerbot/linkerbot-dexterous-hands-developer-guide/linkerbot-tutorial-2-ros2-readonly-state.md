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

[LINKERBOT developer series](./)

### Product overview

This tutorial implements the manufacturer's **read-only first working result** through the current [Linkerbot Hand ROS 2 SDK](https://github.com/linker-bot/linkerbot-hand-ros2-sdk). It separates software-only installation checks from live device discovery, and never sends an angle, gain, torque or motion-target command as part of the initial test.

### Applications

* Prepare Ubuntu/ROS 2 and the current manufacturer transport and Python modules.
* Verify a driver build before a physical hand is connected.
* Discover actual hand identity, controlled joint count and angle-state validity.

### Specifications

| Layer               | Source-supported target                                                       |
| ------------------- | ----------------------------------------------------------------------------- |
| Ubuntu 22.04        | ROS 2 **Humble**, Python **3.10**                                             |
| Ubuntu 24.04        | ROS 2 **Jazzy**, Python **3.12**                                              |
| Active joint counts | L6/O6 **6**; L20 Lite **10**; L20/O20 **16**; L30 **17**; O30 **20**          |
| Packages            | \`linkerbot\_hand\_msgs\`, \`linkerbot\_hand\_ros\`, \`linkerbot\_hand\_gui\` |
| Read-only channels  | \`/linkerbot\_hand/capabilities\`, \`/linkerbot\_hand/state/angles\`          |

### Hardware and connections

1. Read the [hardware/bus preflight](linkerbot-tutorial-1-hardware-and-buses.md), confirming the actual purchased model, adapter, bus and supply. Keep the workspace and fingers clear.
2. Use a separate CAN/CAN-FD channel for each hand as documented in the SDK.
3. **Do not power the conflicting L30 JQ variant or unidentified O20/O30 sold configuration** solely to complete a tutorial. The software-only build stage requires no physical robot.
4. Keep device stop/disconnect readily available. A successful ROS topic alone is not evidence of safe mechanical operation.

### Software and development resources

* [Official ROS 2 quick start](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/quick_start.md): exact apt/venv, three repositories, colcon and lifecycle.
* [Connection and adapter setup](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/connection.md).
* [Model differences](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md).

### Getting started

#### First working result: build and query angles

1. Install your Ubuntu release's matching ROS 2, \`rosdep\`, \`colcon\`, \`git\`, \`can-utils\` and Python venv packages from the **linked quick start**. For Ubuntu 22.04, initialize Humble:

```bash
export LINKERBOT_ROS_DISTRO=humble
source /opt/ros/humble/setup.bash
/usr/bin/python3 -m venv --system-site-packages "$HOME/venvs/linkerbot-hand-$ROS_DISTRO"
source "$HOME/venvs/linkerbot-hand-$ROS_DISTRO/bin/activate"
```

For Ubuntu 24.04, use the matching Jazzy installation and Python 3.12 rather than the Humble commands.

2. Clone and install the manufacturer current \`main\` repositories in a vendor-ROS-compatible shell:

```bash
mkdir -p ~/linkerbot_deps
cd ~/linkerbot_deps
git clone --branch main --depth 1 https://github.com/linker-bot/linkerbot-transport.git linkerbot-transport
git clone --branch main --depth 1 https://github.com/linker-bot/linkerbot-hand-python-sdk.git linkerbot-hand
python -m pip install -e './linkerbot-transport[all]' -e ./linkerbot-hand
mkdir -p "$HOME/linkerbot_$ROS_DISTRO"_ws/src
cd "$HOME/linkerbot_$ROS_DISTRO"_ws/src
git clone --branch main --depth 1 https://github.com/linker-bot/linkerbot-hand-ros-sdk.git linkerbot-hand-ros
```

3. Use the vendor's \`rosdep\` and \`colcon\` instructions to install dependencies and build. After sourcing the workspace, check without hardware:

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

**Expected live result:** lifecycle \`active\`, \`identity.verified=true\` and angle \`meta.valid=true\`, \`meta.stale=false\` with model-appropriate joint names and count. Record **actual** data and source revisions, not copied sample output.

6. Close connection with the OEM lifecycle sequence:

```bash
ros2 lifecycle set /linkerbot_hand deactivate
ros2 lifecycle set /linkerbot_hand cleanup
```

### Troubleshooting and FAQs

**The software builds but no device appears.** Inspect OS adapter device, bus bitrate, firmware, model identity, and whether another process holds the interface. Do not send a motion command for discovery.

**Why do I see 10 angles for an L20 Lite?** The manual specifies **10 active joints and 10 passive joints**, despite a storefront title mentioning 20 DOF.

**Can I run \`angle\_command\` to verify connectivity?** No. The current SDK says it moves the hand; first verify valid and fresh read-only state.

### Downloads and technical documents

* [Manufacturer current ROS 2 quick start](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/quick_start.md).
* [SDK model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md).
* [Model-specific OEM manuals](../).

### References and validation

* Seven uploaded Linkerbot manuals, examined 2026-11-21.
* [Linkerbot current ROS 2 source, quick start](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/quick_start.md), reviewed 2026-11-21.

**Documentation:** source-reviewed. **Software execution:** not run. **Hardware validation:** not run. Unverified store/power/bus pairings block the corresponding physical steps.
