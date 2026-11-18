# Seeed Studio reBot Arm B601-DM Engineering Guide

{% hint style="info" %}
[**View Seeed Studio reBot Arm B601-DM Assembled Kit on OpenELAB**](https://openelab.io/products/seeed-studio-rebot-arm-b601-dm-assembled-kit)

**Model:** reBot Arm B601-DM, with gripper · **SKU:** `Seeed-100065783` · **Scope:** DAMIAO motor configuration. The assembled kit excludes the 24 V power adapter and G-clamp; verify required accessories before first motion.
{% endhint %}

[Seeed-100065783](https://openelab.de/products/seeed-studio-rebot-arm-b601-dm-assembled-kit)

## Product and scope

**100065783 B601-DM** is the DAMIAO-actuated reBot follower arm with gripper. Use it for teleoperation, motion-planning and robot-learning experiments. B601-RS is a different actuator/power configuration; its calibration and CAN settings must not be substituted.

## Hardware and technical documents

| Item       | Reference                                                                |
| ---------- | ------------------------------------------------------------------------ |
| Role       | 6+1-DoF follower-arm platform                                            |
| Actuators  | DAMIAO motor family; match individual joint labels and revisions         |
| Main input | 24V DC; current quick start discusses a 14.6A/15A-class supported supply |
| Leader     | Star Arm 102 is separate and uses its own supply                         |
| Host       | Manufacturer-supported desktop application or robot SDK                  |

The current **reBot-DevArm** repository contains BOM and hardware resources. Use the DM-specific CAD, joint map, CAN topology and connector diagrams. This package excludes the main supply by default. Prefer a correctly assembled supported supply; do not follow an RS supply diagram for the DM arm.

## Getting started

1. Clamp the arm to a rigid bench, clear its workspace and arrange accessible power isolation. Do not fit a payload.
2. Identify the actual USB-CAN adapter and serial device; record the joint inventory before changing any IDs.
3. Install the version of **MotorBridge / manufacturer tooling** specified by the current DM quick start.
4. Inspect each motor and its CAN ID. On an assembled, configured arm, avoid resetting all IDs unless the supplied configuration requires it.
5. Complete the DM calibration workflow, then command only a small, low-speed movement with conservative limits.

**Expected checkpoint:** all expected joints identify correctly, calibration succeeds and one small motion follows the intended direction without abnormal noise.

## Development software and recovery

The current DM quick start uses **MotorBridge** for calibration/first run and links a Python SDK; older workflows may use different applications. Keep application, adapter driver, firmware and calibration records together. Use the DM-specific LeRobot or Pinocchio tutorial only after this baseline. Recovery starts with supply/cabling/ID checks, not increasing gains.

## FAQs

**Can I use the B601-RS 48V supply?** The DM guide specifies 24V. Use the correct model's supported supply.

**Why did the software workflow change?** Follow a single documented revision; do not mix historical calibration files and new tools without migration guidance.

**Missing joints or startup noise?** Stop, inspect bus connections, IDs, actuator parameters and the actual voltage under load.

## Sources and validation

* [Current DM quick start](https://wiki.seeedstudio.com/rebot_b601_dm_getting_started/)
* [Open hardware/BOM/software](https://github.com/Seeed-Projects/reBot-DevArm)
* [DM LeRobot workflow](https://wiki.seeedstudio.com/rebot_arm_b601_dm_lerobot/)
* [DM Pinocchio workflow](https://wiki.seeedstudio.com/rebot_arm_b601_dm_pinocchio_meshcat/)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
