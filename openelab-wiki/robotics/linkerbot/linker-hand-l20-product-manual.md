---
description: >-
  LINKERBOT L20 original product manual and integrated SDK/developer guide;
  existing URL and figures preserved.
---

# Linker Hand L20 Product Manual

{% hint style="info" %}
[**View LINKERBOT L20 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l20-21)

**Model:** L20 · **SKU:** `Linker-Hand-L20-1 (left, RS485; confirm variant)` · **Manual:** V1.3 (2026-08-04; filename says V10)
{% endhint %}

[LINKERBOT family index](linkerbot-dexterous-hands-developer-guide/) · **Complete manufacturer manual and diagrams below**

### Product overview

**L20** has **16 controlled; 21 total (16 active, 5 passive)**. Its supplied manufacturer product manual is revision **V1.3 (2026-08-04; filename says V10)**. This page describes the exact model; any other Linkerbot hand with a similar number may have a different joint array, mounting flange, sensor option, adapter voltage or bus protocol. **Identity:** Linker-Hand-L20-1 (left, RS485; confirm variant).

### Applications

* Model-specific end-effector integration into research manipulators and humanoid platforms.
* Safe device identification, position/state logging, and supervised dexterous control research.
* Tactile and closed-loop grasp studies **only when installed sensors and controls are verified**.

### Specifications

| Parameter                                  | Source-backed value                                                                                                                 |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| Controlled DoF and physical joints         | 16 controlled; 21 total (16 active, 5 passive)                                                                                      |
| Power                                      | **Manual table 24–48 VDC, while XT30 connector drawing labels +24 V; use the exact supplied adapter pending voltage confirmation.** |
| Bus / variant                              | CAN/RS485 variant                                                                                                                   |
| Manufacturer-reported mass                 | ≈1200 g                                                                                                                             |
| Manufacturer maximum load                  | 20 kg maximum load in OEM PDF vs 10 kg store listing (discrepancy)                                                                  |
| Manufacturer-reported opening/closing time | 0.98 s                                                                                                                              |
| Tactile/sensing                            | Piezoresistive array 6×12, 20 N range, 200 fps per OEM manual. Communication frequency 500 Hz is distinct.                          |
| Manual revision                            | V1.3 (2026-08-04; filename says V10)                                                                                                |

**Evidence:** exact attached product manual and corresponding connected product catalog where available. These are device-level figures, not automatically rated full-arm payload or production contact performance.

### Hardware and connections

1. Inspect the model, serial, left/right label and selected store interface; do not rely only on a family nickname.
2. Confirm the supplied adapter, supported cable, correct keyed connector and the mounting drawing **before** connecting DC power.
3. Use a stable fixture, keep fingers and cables away from moving linkages and make the operator's stop/disconnect method accessible.

#### Model-specific mechanical mounting

M3 mounting and flange pattern, exact drawing on **L20 V1.3 page 12**.

#### Electrical bus and connector

XT30 (2+2): CAN L, CAN H, GND, and +24 V indicated in the **connector pin table**. Confirm physical supply and compatibility because general model table permits a wider range.

**Manufacturer-model note:** The manufacturer updated L20 joint-angle values in V1.3. Its 21 total joints are not a 21-value command array. The active drive is 16 while five linked finger joints are passive.

### Software and development resources

| Resource                                                                                                                              | Verified purpose                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [Current seven-model Linkerbot ROS 2 driver](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                   | ROS 2 Humble/Jazzy driver and read-only state topics; **native CAN/CAN FD** model entry |
| [ROS 2 model compatibility matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) | Confirms active joint count, bus and per-model capability differences                   |
| [LinkerHand Python SDK](https://github.com/linker-bot/linkerhand-python-sdk)                                                          | Firmware/adapter-specific Python examples; verify variant and driver before using       |
| [Preserved L20 OEM manual in OpenELAB Wiki](linker-hand-l20-product-manual.md)                                                        | Exact manual hardware, mechanical dimensions, connector and installation source         |

**Version constraint:** a current GitHub model entry does not certify a purchased RS485 variant for a CAN-only launch. Check model/device capabilities, firmware and the installed transport. Never run sample code that writes angles or torque as the first device check.

### Getting started

#### Prerequisites

Physical hand and variant labeling; correct original or manufacturer-approved adapter; matching CAN/CAN FD/RS485 interface; secure fixture; model manual. For first read-only software use, a compatible Windows host utility or ROS 2 environment must be available as appropriate.

#### First working result

1. Perform a **device-label, adapter-output-label and cable pinout inspection** against the OEM V1.3 manual. Do not energize an unconfirmed 24–48 V variant. Once adapter and selected CAN interface are confirmed by the manufacturer, use the model-specific ROS 2 driver to read `/linkerbot_hand/capabilities` and a fresh `/linkerbot_hand/state/angles` sample without issuing motion commands.
2. Record current model, side, revision, bus, installed host utility/SDK commit and relevant status values. Do **not** command finger positions, resets, gains or torque until identity and safety are confirmed.

**Expected result:** A signed device/adapter compatibility record, then (only after approved connection) a 16-active-joint state sample.

**If the check fails:** If a stale state or wrong joint count appears, verify actual driver model, interface, side, firmware and capabilities; do not map a 21-joint mechanical drawing directly into 16 motor commands.

#### Next safe experiment

With device and software explicitly approved, log a sequence of **read-only** state observations and compare expected joint count/units, metadata validity and sample freshness. Motion/grasping is a separate supervised step after confirming range, direction, force and stop behavior.

### Troubleshooting and FAQs

**A device appears but the reported joint count differs.** Confirm the exact model, model discovery, loaded SDK feature definition and **active DoF versus passive mechanical joints**. Do not pad/trim a control vector to guess joint mapping.

**The device does not connect or respond.** If a stale state or wrong joint count appears, verify actual driver model, interface, side, firmware and capabilities; do not map a 21-joint mechanical drawing directly into 16 motor commands.

**Can I use another Linkerbot model's power cable or protocol?** No. This model's documented electrical interface is **CAN/RS485 variant**; use its own labeled cable, supply and OEM connector drawing.

**Can I assume tactile data is present?** Piezoresistive array 6×12, 20 N range, 200 fps per OEM manual. Communication frequency 500 Hz is distinct. Validate sensor options and returned data before relying on tactile feedback.

### Downloads and technical documents

| Resource                        | Scope and link                                                                                                                               |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Original product manual         | [Preserved L20 OEM manual in OpenELAB Wiki](linker-hand-l20-product-manual.md)                                                               |
| Manufacturer ROS 2 model matrix | [Model definitions and control semantics](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) |
| Manufacturer current ROS 2 SDK  | [Installation and examples](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                                           |
| Manufacturer Python SDK         | [Source and model examples](https://github.com/linker-bot/linkerhand-python-sdk)                                                             |
| OpenELAB product/SKU            | [Matched model and selectable variants](https://openelab.io/products/linker-hand-linkerbot-l20-21)                                           |

**Physical drawings:** preserve the flange/connector images in the existing manual; do not recreate dimensioned pinout diagrams from photos.

### References and validation

* LINKERBOT / Lingxin Qiaoshou, _L20 Product Manual_, **V1.3 (2026-08-04; filename says V10)**, provided upload, reviewed 2026-11-21.
* [Current official Linkerbot ROS 2 model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md), reviewed 2026-11-21.
* [OpenELAB exact model listing](https://openelab.io/products/linker-hand-linkerbot-l20-21), matched to catalog variant on 2026-11-21.

**Documentation review:** completed for provided revision; **software execution:** not run; **hardware test:** not run. Check the actual shipped interface and firmware before any actuator operation.

### Original LINKERBOT L20 Manufacturer Manual and Diagrams

This section preserves the original LINKERBOT manufacturer manual text, technical tables, images and installation illustrations from the established product page.

#### LINKERBOT Linker Hand L20 21-DOF Dexterous Robotic

{% embed url="https://openelab.io/products/linker-hand-linkerbot-l20-21" %}

![Linker Hand L20](../../.gitbook/assets/l20-cover.png)

#### Revision History

| Version | Date       | Description                                       |
| ------- | ---------- | ------------------------------------------------- |
| V1.0    | 2025-09-11 | Initial edition                                   |
| V1.1    | 2025-11-24 | Parameters and host-computer instructions updated |
| V1.2    | 2026-03-24 | Parameters and host-computer instructions updated |
| V1.3    | 2026-08-04 | Joint-angle values updated                        |

#### Safety Instructions

Read this manual and all related manuals before installing or using the product. Observe the following precautions:

1. Use only the matching or specified cables, and secure the product as instructed. Do not use damaged power cords, damaged plugs, or loose sockets.
2. Follow the installation requirements in this manual. Operation outside the specified conditions may shorten the service life and create serious safety hazards.
3. Extended high-power operation may increase the product temperature. If the temperature becomes excessive, stop operation and allow the product to cool before resuming use.
4. Only trained personnel may operate the equipment. Do not open the housing, disassemble the device, or attempt unauthorized repairs. Contact after-sales support if the equipment malfunctions.
5. Diagrams and photographs are illustrative and may differ from the purchased product. The manual may be revised as the product and its specifications are updated.

#### Product Overview

![Linker Hand L20 exterior, front view](../../.gitbook/assets/l20-exterior-front.png)

![Linker Hand L20 exterior, palm view](../../.gitbook/assets/l20-exterior-palm.png)

The Linker Hand L20 is a 21-joint robotic hand that combines high-performance brushless motors with precision ball screws. It reproduces human-hand motion for precise grasping and stable gripping while providing high power density and efficient transmission. The hand is intended as an industrial alternative to conventional grippers.

Its high-precision motion control and stable operation support automotive assembly, aerospace operations, irregular-package sorting, and remote or automated work in hazardous environments.

**High-Precision Control and Bionic Manipulation**

Brushless motors and micron-scale ball-screw transmission provide closed-loop position and torque control for tasks such as precision assembly and handling fragile objects.

**Powerful, Efficient Output**

The brushless motors, high-rigidity linkages, and ball screws support a rated load of up to 20 kg. Opening and closing takes approximately 0.9 seconds, enabling efficient grasp-lift-release workflows.

**Energy-Efficient Continuous Operation**

The rated static current is 0.3 A. The hand supports 24 V industrial power and continuous operation for production-line applications.

**Lightweight Integration**

The lightweight design supports rapid installation and deployment in high-precision manufacturing applications, including 3C electronics, automotive, and aerospace production.

#### Product Functions

**Position Control**

Position control manages the overall hand position and individual finger joints so that preset trajectories can be executed smoothly. This supports whole-hand movement and fine joint adjustment for precision assembly and path-guided operation.

**Speed Control**

Finger speed can be adjusted for different tasks. High-speed operation improves efficiency, while low-speed operation supports safer precision work.

**Tactile Feedback and Force Control**

Fingertip sensors detect applied force and torque in real time. The controller can adjust output force to protect fragile objects and reduce the risk of slipping.

**Online Firmware Upgrade**

The dexterous-hand firmware can be updated from the host computer, allowing functional updates and performance optimization over the service life of the product.

#### Dimensions, Joints, and Motion Range

**External Dimensions**

![Linker Hand L20 external dimensions](../../.gitbook/assets/l20-external-dimensions.png)

All dimensions in the drawing are in millimetres.

**Degrees of Freedom**

The Linker Hand L20 has 16 active degrees of freedom and 21 joints in total: 16 active joints and 5 passive joints.

![Linker Hand L20 joint degrees-of-freedom diagram](../../.gitbook/assets/l20-joint-dof.png)

The following diagrams show the actual joint ranges.

![Thumb CMC yaw range](../../.gitbook/assets/l20-thumb-cmc-yaw.png)

![Thumb CMC roll range](../../.gitbook/assets/l20-thumb-cmc-roll.png)

![Thumb IP and MCP range](../../.gitbook/assets/l20-thumb-ip-mcp.png)

![Thumb CMC pitch range](../../.gitbook/assets/l20-thumb-cmc-pitch.png)

![Finger DIP range](../../.gitbook/assets/l20-finger-dip.png)

![Finger PIP range](../../.gitbook/assets/l20-finger-pip.png)

![Finger MCP range](../../.gitbook/assets/l20-finger-mcp.png)

**Controlled Motion Range and Speed**

| Joint     | Maximum motion range | Maximum speed |
| --------- | -------------------: | ------------: |
| IP        |                  71° |     133.96°/s |
| MCP       |                  70° |     132.08°/s |
| CMC pitch |                  45° |      80.36°/s |
| CMC yaw   |                  91° |     185.71°/s |
| CMC roll  |                77.6° |        129°/s |
| DIP       |                  78° |        195°/s |
| PIP       |                  99° |      247.5°/s |
| MCP pitch |                  70° |     194.44°/s |
| MCP roll  |                 ±13° |      68.42°/s |

#### Technical Specifications

**Basic Parameters**

| Parameter                     | Specification              |
| ----------------------------- | -------------------------- |
| Model                         | Linker Hand L20            |
| Active degrees of freedom     | 16                         |
| Joint count                   | 21 (16 active + 5 passive) |
| Drive                         | Linkage transmission       |
| Control interfaces            | CAN / RS485                |
| Communication frequency       | 500 Hz                     |
| Weight                        | Approximately 1,200 g      |
| Maximum load                  | 20 kg                      |
| Working voltage               | 24-48 V DC                 |
| Quiescent current             | 0.3 A                      |
| Average no-load motor current | 0.4 A                      |
| Maximum current               | 1.8 A                      |
| Repeatability                 | ±0.2 mm                    |
| Opening and closing time      | 0.98 s                     |

**Mechanical Performance**

| Performance item                                    | Specification |
| --------------------------------------------------- | ------------: |
| Maximum thumb-fingertip force                       |          15 N |
| Maximum fingertip force of each of the four fingers |          20 N |
| Maximum five-finger gripping force                  |         100 N |

#### Sensor System

The left-hand L20 is equipped with a pressure-sensitive sensor.

| Parameter                | Specification  |
| ------------------------ | -------------- |
| Piezoresistive array     | 6 × 12         |
| Force-sensitive area     | 9.6 × 14.4 mm  |
| Touch-force threshold    | 5 g            |
| Measurement range        | 20 N           |
| Service life             | 100,000 cycles |
| Communication frame rate | 200 FPS        |

#### Installation and Commissioning

**Accessory List**

Confirm that all accessories are present before installation.

| No. | Item                       | Quantity |
| --: | -------------------------- | -------: |
|   1 | USB-to-CAN debugging cable |        1 |
|   2 | XT30 (2+2) plug-in cable   |        1 |
|   3 | Power adapter              |        1 |
|   4 | Power cable                |        1 |

![USB-to-CAN debugging cable](../../.gitbook/assets/l20-accessory-usb-can.png)

![XT30 2+2 plug-in cable](../../.gitbook/assets/l20-accessory-xt30.png)

![Power adapter](../../.gitbook/assets/l20-accessory-power-adapter.png)

![Power cable](../../.gitbook/assets/l20-accessory-power-cable.png)

**Mechanical Installation**

Use M3 screws. Select the screw length according to the thickness of the mounting component.

![Flange connection dimensions](../../.gitbook/assets/l20-flange-connection.png)

**Electrical Connection**

The hand uses an XT30 (2+2) connector.

![XT30 2+2 connector pin locations](../../.gitbook/assets/l20-xt30-pinout.png)

| Pin | Signal |
| --: | ------ |
|   1 | CAN L  |
|   2 | CAN H  |
|   3 | GND    |
|   4 | 24 V   |

**Debugging Cable Connection**

1. Connect the dexterous hand to the debugging computer with the USB-to-CAN cable.
2. Connect the power cable to the power adapter.
3. Connect the adapter to the power input of the USB-to-CAN cable.
4. Connect the other end of the power cable to a 220 V AC outlet.

#### Warranty and Service

1. The product is covered by a 12-month limited warranty from the date of purchase.
2. During the warranty period, failures caused by manufacturing or material defects are eligible for free repair or component replacement.
3. The warranty does not cover surface wear caused by normal use or damage caused by improper operation, accidents, unauthorized disassembly, or failure to follow the manual.
4. Returns or exchanges are not accepted when the issue is not a product-quality problem.
5. If the product malfunctions, contact official after-sales support. Do not disassemble the product yourself.
6. Repair services outside the warranty period are chargeable.

#### SDK and Technical Support

* ROS SDK: [linkerhand-ros-sdk](https://github.com/linker-bot/linkerhand-ros-sdk)
* ROS 2 SDK: [linkerhand-ros2-sdk](https://github.com/linker-bot/linkerhand-ros2-sdk)
* Python SDK: [linkerhand-python-sdk](https://github.com/linker-bot/linkerhand-python-sdk)
* Technical support: [support@linkerbot.cn](mailto:support@linkerbot.cn)
* Official website: [linkerbot.cn](https://linkerbot.cn)
