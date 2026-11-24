---
description: >-
  DAMIAO actuator references: exact V3/V4 and voltage options, typed CAN
  registers, DMTool setup, read-only diagnostics, calibration and firmware
  resources.
cover: ../../.gitbook/assets/damiao-logo.jpg
coverY: 0
---

# DAMIAO

DAMIAO develops motor modules and control tools for robotic joints and motion systems. Its product range includes integrated joint actuators and other motor families, with model-specific setup, communication, and tuning requirements.

[Browse DAMIAO products on OpenELAB](https://openelab.io/collections/brands-damiao)

### Popular product guides

Products in the OpenELAB Top200 net-sales snapshot for 17 August–17 November 2026, ordered by their original sales rank. Shared model-family guides appear once; match the exact model, SKU and purchased option. This dated sales order is separate from manufacturer website-traffic ranking.

| Product guide                                                                                           | Models / order codes                   |
| ------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| [DAMIAO DM-J4310-2EC and DM-J8009P-2EC Engineering Guide](damiao-2ec-j4310-j8009p-development-guide.md) | DM-J4310-2EC-24V-V3 · DM-J8009P-2EC-V3 |

### Exact-model development reference

The [DM-J4310-2EC and DM-J8009P-2EC guide](damiao-2ec-j4310-j8009p-development-guide.md) covers the listed V3 options in one comparison with both product links. It separates the 4310 24V configuration from the 8009P's 24–48V supply, distinct connector faces, encoder generations and firmware families.

The page includes a complete typed register dictionary with per-model address differences, mode-specific frame layouts, command/persistence semantics, version-gated CAN-FD notes, calibration and firmware navigation, and an original non-enabling parameter reader. DMTool adapter configuration is separate from motor firmware and the mechanical CAD.

Start with the exact motor label, saved configuration and isolated readback before selecting a motion mode. Physical or software execution is not claimed by the source review. [4310 official resources](https://github.com/dmBots/DM-J4310-2EC) · [8009P official resources](https://github.com/dmBots/DM-J8009P-2EC) · [DMTool documentation](https://github.com/dmBots/motor-debugging-tool)

### Product range

* DM-J integrated robotic joint motors
* DM-H and other specialized motor families
* USB-CAN tools, host-computer software, and communication documentation

### Product families and examples

| Product      | Typical use                                                | Links                                                                                                                                                               |
| ------------ | ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DM-J4310-2EC | Compact robotic joint integration                          | [DM-J4310-2EC V1.2 manual](damiao-dm-j4310-2ec-v1.2-motor-instruction-manual.md) · [OpenELAB product](https://openelab.io/products/damiao-brushless-servo-dm-j4310) |
| DM-H6215     | Direct-drive hub-motor integration                         | [Wiki guide](damiao-dm-h6215-v1.0-motor-instruction-manual.md) · [OpenELAB product](https://openelab.io/products/damiao-brushless-servo-dm-h6215)                   |
| DM-J3507-2EC | Small joint-actuator development                           | [Wiki guide](damiao-dm-j3507-2ec-v1.1-motor-instruction-manual.md) · [OpenELAB product](https://openelab.io/products/damiao-brushless-servo-dm-j3507)               |
| DM-USB-CAN   | Connecting a development computer to compatible CAN motors | [Host computer manual](damiao-host-computer-user-manual.md) · [OpenELAB product](https://openelab.io/products/damiao-brushless-servo-usb-can)                       |

### Popular applications

* Develop robot-arm, legged-robot, and articulated-mechanism joints.
* Prototype CAN-based position, velocity, and torque control.
* Tune and diagnose motors during robot integration.

Confirm the full motor suffix and hardware version before applying settings. The documentation index includes separate manuals for several revisions.

### Manufacturer resources

* [DAMIAO](https://www.mdmbot.com/)
* [DAMIAO code resources](https://gitee.com/kit-miao/damiao)

### More manuals and tutorials

<details>

<summary>Browse 22 additional guides</summary>

* [DAMIAO Host Computer User Manual](damiao-host-computer-user-manual.md)
* [DAMIAO DM-J4310-2EC V1.1 Motor Instruction Manual](damiao-dm-j4310-2ec-v1.1-motor-instruction-manual.md)
* [DAMIAO DM-J4310-2EC V1.2 Motor Instruction Manual](damiao-dm-j4310-2ec-v1.2-motor-instruction-manual.md)
* [DAMIAO DM-J4340-2EC V1.1 Motor Instruction Manual](damiao-dm-j4340-2ec-v1.1-motor-instruction-manual.md)
* [DAMIAO DM-J4340P-2EC V1.1 Motor Instruction Manual](damiao-dm-j4340p-2ec-v1.1-motor-instruction-manual.md)
* [DAMIAO DM-J8009P-2EC Motor Instruction Manual](damiao-dm-j8009p-2ec-motor-instruction-manual.md)
* [DAMIAO DM-J6248P-2EC Motor Instruction Manual](damiao-dm-j6248p-2ec-motor-instruction-manual.md)
* [DAMIAO DM-J8009-2EC Motor Instruction Manual](damiao-dm-j8009-2ec-motor-instruction-manual.md)
* [DAMIAO DM-J8006-2EC Motor Instruction Manual](damiao-dm-j8006-2ec-motor-instruction-manual.md)
* [DAMIAO DM-J6006-2EC Motor Instruction Manual](damiao-dm-j6006-2ec-motor-instruction-manual.md)
* [DAMIAO DM-J4310P-2EC V1.1 Motor Instruction Manual](damiao-dm-j4310p-2ec-v1.1-motor-instruction-manual.md)
* [DAMIAO DM-J3507-2EC V1.1 Motor Instruction Manual](damiao-dm-j3507-2ec-v1.1-motor-instruction-manual.md)
* [DAMIAO DM-J10010-2EC V1.0 Motor Instruction Manual](damiao-dm-j10010-2ec-v1.0-motor-instruction-manual.md)
* [DAMIAO DM-J10010L-2EC V1.1 Motor Instruction Manual](damiao-dm-j10010l-2ec-v1.1-motor-instruction-manual.md)
* [DAMIAO DM-J10422P-2EC V1.1 Motor Instruction Manual](damiao-dm-j10422p-2ec-v1.1-motor-instruction-manual.md)
* [DAMIAO DM-JH11-2EC V1.0 Motor Instruction Manual](damiao-dm-jh11-2ec-v1.0-motor-instruction-manual.md)
* [DAMIAO DM-S2325-1EC V1.0 Motor Instruction Manual](damiao-dm-s2325-1ec-v1.0-motor-instruction-manual.md)
* [DAMIAO DM-S3519-1EC V1.1 Motor Instruction Manual](damiao-dm-s3519-1ec-v1.1-motor-instruction-manual.md)
* [DAMIAO DM-H6215 V1.0 Motor Instruction Manual](damiao-dm-h6215-v1.0-motor-instruction-manual.md)
* [DAMIAO DM-H3510 V1.0 Motor Instruction Manual](damiao-dm-h3510-v1.0-motor-instruction-manual.md)
* [DAMIAO DM-H65 V1.1 Motor Instruction Manual](damiao-dm-h65-v1.1-motor-instruction-manual.md)
* [DAMIAO DM-G6220 Motor Instruction Manual](damiao-dm-g6220-motor-instruction-manual.md)

</details>

[Explore Robotics documentation](../robotics-wiki-home-page.md) · [OpenELAB Wiki home](../../)
