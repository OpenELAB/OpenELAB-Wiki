---
description: >-
  Model scope, hardware, first-run tutorial, firmware, troubleshooting and
  official development resources.
---

# Seeed Studio reBot Arm B601-RS Development Guide

{% hint style="info" %}
[**View Seeed Studio reBot Arm B601-RS on OpenELAB**](https://openelab.io/products/seeed-studio-rebot-arm-b601-rs-assembled-kit-with-gripper-without-power-supply)

**Covered model:** Seeed Studio reBot Arm B601-RS · **OpenELAB SKU:** `Seeed-100019336`
{% endhint %}

![Seeed Studio reBot Arm B601-RS Development Guide](../../.gitbook/assets/rebot-b601-rs-development-guide.webp)

_Manufacturer image: Seeed Studio._ [_Image source_](https://files.seeedstudio.com/wiki/robotics/projects/rebot_arm/RS5_56.webp)_._

[Product at OpenELAB](https://openelab.io/products/seeed-studio-rebot-arm-b601-rs-assembled-kit-with-gripper-without-power-supply) · [Manufacturer wiki hub](./)

## Product and exact kit scope

**reBot Arm B601-RS** is Seeed's open-source six-axis robotic arm based on RobStride actuators. The structural design, BOM and software are published for developers building manipulation, teleoperation and learning-based robotics experiments. The **B601-DM** uses different actuators and requires its own motor/protocol configuration; similar appearance does not establish compatibility.

This page covers the **assembled B601-RS with gripper, code 100019336**, sold without a power supply. Inspect the actual gripper, cables and USB-CAN adapter supplied with the order. The reBot Arm 102/Star Arm 102 leader is a separate product and power path.

## Hardware and software map

| Subsystem       | Development reference                                                                       |
| --------------- | ------------------------------------------------------------------------------------------- |
| Arm             | Six-axis B601-RS, RobStride motor configuration                                             |
| Host/control    | USB-to-CAN adapter and MotorBridge control/SDK path                                         |
| Power           | Manufacturer reference setup uses a 48 V follower supply; supply is separate from this kit  |
| Wiring          | Power-signal splitter and XT30/XT30 2+2 path; follow RS-specific diagram                    |
| Optional leader | reBot Arm 102; documented 12 V / 2 A leader supply, separate USB connection                 |
| Software routes | MotorBridge Studio, manufacturer Python SDK/project, LeRobot plugin and SenseCraft Robotics |

Use the [RS quick-start](https://wiki.seeedstudio.com/rebot_b601_rs_getting_started/) and [open hardware/software repository](https://github.com/Seeed-Projects/reBot-DevArm) for exact joint/BOM revisions, mounting drawings, assembly and load guidance. No payload, reach or accuracy figure is inferred from another reBot revision here.

## Prepare the bench

Use a rigid fixture or the specified clamps to secure the follower. Support links that could fall when torque is off. Prepare the correct supplied cable assemblies, a suitable preassembled supply, a computer and a physical way to remove drive power. Wire and inspect the low-voltage connections with power off; do not hot-plug motor connectors. Keep the travel area clear before enabling a motor.

This guide uses the manufacturer's MotorBridge first-run workflow. Its current quick-start recommends a physical Ubuntu 24.04 host for that route and also documents Windows/macOS support. Treat the Python/LeRobot environment as a separate software choice: the [LeRobot integration guide](https://wiki.seeedstudio.com/rebot_arm_b601_rs_lerobot/) has its own OS, PyTorch, plugin and communication requirements.

## Getting started: identify all joints before moving

1. **Confirm RS hardware.** Record motor labels, adapter type and assembly revision. Open the RS hardware/BOM files and match the installed power/communication path.
2. **Connect while unpowered.** Follow the RS wiring figure for USB-CAN, splitter, first motor and subsequent links. The documented PCAN setup uses the adapter's **120R** setting; verify which adapter you received before applying that setting to a different interface.
3. **Install/open MotorBridge Studio** from the [official distribution page](https://motorbridge.github.io/motorbridge-studio/). Connect the adapter, select the actual interface/port and the B601-RS configuration, then apply the documented supply.
4. **Read and inspect.** Scan the bus and compare every detected motor identity with the RS joint map. Record voltage, temperature and position feedback where available. For an assembled kit, inspect the existing IDs before running any tool that rewrites them.
5. **Calibrate with support.** Follow the manufacturer's RS zero-position procedure and illustrated poses. A zero-write changes the joint reference; do not perform it while the arm is unsupported or in an arbitrary pose. Save the resulting configuration and calibration identity.
6. **Run a minimal first motion.** Use the vendor's supported single-joint/first-run control in a clear workspace and start with a small change near the present pose. Confirm direction, joint identity and stop behavior before running a trajectory or linking a leader.

The first checkpoint is **all required joints detected with plausible feedback**, followed by a completed RS calibration and controlled small motion. Launching a GUI or detecting the USB adapter alone is insufficient.

## LeRobot and application development

The official [B601 plugin](https://github.com/Seeed-Projects/lerobot-robot-seeed-b601) provides the LeRobot-specific integration. Follow its matching installation/configuration guide and supported bus backend. Pin the selected repository/plugin revision with the installed LeRobot release; do not assume the same commands apply to every fork or package version.

For a graphical path, use the [reBot Arm 102 + B601-RS SenseCraft training guide](https://wiki.seeedstudio.com/sensecraft_robotics_rebot_arm_102_b601_rs/). Keep follower and leader calibration, power, port identity and cameras consistent. Begin with verified teleoperation, then collect a short dataset with a single task before adding autonomous policy execution. ROS and simulation support live in the project ecosystem; use the RS-specific model and joint limits.

## Troubleshooting and recovery

| Symptom                                 | Check and next action                                                                                                                |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| Adapter detected, motors missing        | Verify drive power, connector seating, splitter path, adapter/backend and termination with power removed before rewiring.            |
| One motor missing                       | Compare against the expected joint map; inspect the preceding cable/connector and isolate the affected segment before rewriting IDs. |
| Voltage/driver fault                    | Stop enabling motion; check the actual DC voltage, connector polarity and supply/load behavior against the motor manual.             |
| Wrong joint or reversed motion          | Stop and verify motor IDs, joint mapping and RS calibration.                                                                         |
| Arm drops when disabled                 | Support the mechanism; torque-off is not a mechanical holding device.                                                                |
| LeRobot cannot connect but Studio works | Inspect plugin version, bus backend, port ownership/permissions and configured arm type separately from hardware.                    |
| Need to update motor firmware           | Use the exact RobStride model/revision procedure and retain settings/calibration; do not use a DM image or an arbitrary full reset.  |

## Technical documents and software

| Resource                                                                                             | Use                                         |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [B601-RS quick-start](https://wiki.seeedstudio.com/rebot_b601_rs_getting_started/)                   | Wiring, adapter, motor IDs and zeroing      |
| [Hardware CAD, BOM and SDK](https://github.com/Seeed-Projects/reBot-DevArm)                          | RS-specific mechanical and software files   |
| [MotorBridge Studio](https://motorbridge.github.io/motorbridge-studio/)                              | Initial device control and diagnostics      |
| [LeRobot integration](https://wiki.seeedstudio.com/rebot_arm_b601_rs_lerobot/)                       | Supported environment and B601 plugin setup |
| [B601 LeRobot plugin](https://github.com/Seeed-Projects/lerobot-robot-seeed-b601)                    | Robot integration source and configuration  |
| [SenseCraft training route](https://wiki.seeedstudio.com/sensecraft_robotics_rebot_arm_102_b601_rs/) | Leader/follower workflow                    |

**Review date:** 17 November 2026. **Validation:** official documentation and the cited software interfaces reviewed. Commands and examples have not been compiled or run on physical hardware by OpenELAB for this guide. Record your hardware revision, firmware, software versions and actual results when reproducing it.
