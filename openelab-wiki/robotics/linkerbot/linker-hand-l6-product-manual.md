---
description: >-
  LINKERBOT L6 OEM manual and integrated model-specific engineering development
  guide; existing URL and drawings preserved.
---

# Linker Hand L6 Product Manual

{% hint style="info" %}
[**View LINKERBOT L6 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l6-11)

**Model:** L6 · **SKU:** `Linker-Hand-L6-1 (left, RS485; other hand/interface variants have different SKUs)` · **Manual:** V1.4 (2026-05-18)
{% endhint %}

[LINKERBOT family index](linkerbot-dexterous-hands-developer-guide/) · **Complete manufacturer manual and diagrams below**

### Product overview

**L6** has **6 controlled; 11 total (6 active, 5 passive)**. Its supplied manufacturer product manual is revision **V1.4 (2026-05-18)**. This page describes the exact model; any other Linkerbot hand with a similar number may have a different joint array, mounting flange, sensor option, adapter voltage or bus protocol. **Identity:** Linker-Hand-L6-1 (left, RS485; other hand/interface variants have different SKUs).

### Applications

* Model-specific end-effector integration into research manipulators and humanoid platforms.
* Safe device identification, position/state logging, and supervised dexterous control research.
* Tactile and closed-loop grasp studies **only when installed sensors and controls are verified**.

### Specifications

| Parameter                                  | Source-backed value                                                          |
| ------------------------------------------ | ---------------------------------------------------------------------------- |
| Controlled DoF and physical joints         | 6 controlled; 11 total (6 active, 5 passive)                                 |
| Power                                      | **24 VDC ±10%**                                                              |
| Bus / variant                              | CAN or RS485, according to purchased variant                                 |
| Manufacturer-reported mass                 | 607 g                                                                        |
| Manufacturer maximum load                  | 28 kg maximum load per OEM table (not universal host-arm payload)            |
| Manufacturer-reported opening/closing time | 0.35 s                                                                       |
| Tactile/sensing                            | Piezoresistive 6×12 at fingertips; manufacturer lists 20 N range and 200 fps |
| Manual revision                            | V1.4 (2026-05-18)                                                            |

**Evidence:** exact attached product manual and corresponding connected product catalog where available. These are device-level figures, not automatically rated full-arm payload or production contact performance.

### Hardware and connections

1. Inspect the model, serial, left/right label and selected store interface; do not rely only on a family nickname.
2. Confirm the supplied adapter, supported cable, correct keyed connector and the mounting drawing **before** connecting DC power.
3. Use a stable fixture, keep fingers and cables away from moving linkages and make the operator's stop/disconnect method accessible.

#### Model-specific mechanical mounting

Circular flange drawing and Ø36 mm wrist; hole layout, screw depth and orientation must be taken from **L6 V1.4 page 12** (manufacturer drawing).

#### Electrical bus and connector

XT30 (2+2) carries power and CAN L/H on the CAN version, with a manufacturer side-view diagram on **L6 V1.4 page 13**. The PDF doesn't supply an independent RS485 pin table; use the RS485-specific cable supplied with the variant.

**Manufacturer-model note:** An integrated status indicator was added in revision V1.4: **green** normal, **flashing yellow** motor offline/failure, **solid yellow** sensor communication abnormal, and **red** main-control program failure. Record its real color before debugging.

### Software and development resources

| Resource                                                                                                                              | Verified purpose                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [Current seven-model Linkerbot ROS 2 driver](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                   | ROS 2 Humble/Jazzy driver and read-only state topics; **native CAN/CAN FD** model entry |
| [ROS 2 model compatibility matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) | Confirms active joint count, bus and per-model capability differences                   |
| [LinkerHand Python SDK](https://github.com/linker-bot/linkerhand-python-sdk)                                                          | Firmware/adapter-specific Python examples; verify variant and driver before using       |
| [Preserved L6 OEM manual in OpenELAB Wiki](linker-hand-l6-product-manual.md)                                                          | Exact manual hardware, mechanical dimensions, connector and installation source         |

**Version constraint:** a current GitHub model entry does not certify a purchased RS485 variant for a CAN-only launch. Check model/device capabilities, firmware and the installed transport. Never run sample code that writes angles or torque as the first device check.

### Getting started

#### Prerequisites

Physical hand and variant labeling; correct original or manufacturer-approved adapter; matching CAN/CAN FD/RS485 interface; secure fixture; model manual. For first read-only software use, a compatible Windows host utility or ROS 2 environment must be available as appropriate.

#### First working result

1. Install/mount only after matching the exact left/right hand and cable. With the approved adapter and CAN variant connected to a compatible host and the manufacturer ROS 2 SDK built, launch its **model-discovery driver** and subscribe to `/linkerbot_hand/capabilities` or `/linkerbot_hand/state/angles` read-only. Record six active joint names and whether sample metadata is valid/stale. The indicator should be interpreted with the V1.4 table.
2. Record current model, side, revision, bus, installed host utility/SDK commit and relevant status values. Do **not** command finger positions, resets, gains or torque until identity and safety are confirmed.

**Expected result:** A verified L6 model identity, six **active** joint states and a documented LED status, not commanded movement.

**If the check fails:** If the indicator is blinking yellow, investigate motor offline/failure; solid yellow indicates sensor communications; red means main controller failure. Do not drive the fingers to clear a diagnostic state.

#### Next safe experiment

With device and software explicitly approved, log a sequence of **read-only** state observations and compare expected joint count/units, metadata validity and sample freshness. Motion/grasping is a separate supervised step after confirming range, direction, force and stop behavior.

### Troubleshooting and FAQs

**A device appears but the reported joint count differs.** Confirm the exact model, model discovery, loaded SDK feature definition and **active DoF versus passive mechanical joints**. Do not pad/trim a control vector to guess joint mapping.

**The device does not connect or respond.** If the indicator is blinking yellow, investigate motor offline/failure; solid yellow indicates sensor communications; red means main controller failure. Do not drive the fingers to clear a diagnostic state.

**Can I use another Linkerbot model's power cable or protocol?** No. This model's documented electrical interface is **CAN or RS485, according to purchased variant**; use its own labeled cable, supply and OEM connector drawing.

**Can I assume tactile data is present?** Piezoresistive 6×12 at fingertips; manufacturer lists 20 N range and 200 fps Validate sensor options and returned data before relying on tactile feedback.

### Downloads and technical documents

| Resource                        | Scope and link                                                                                                                               |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Original product manual         | [Preserved L6 OEM manual in OpenELAB Wiki](linker-hand-l6-product-manual.md)                                                                 |
| Manufacturer ROS 2 model matrix | [Model definitions and control semantics](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) |
| Manufacturer current ROS 2 SDK  | [Installation and examples](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                                           |
| Manufacturer Python SDK         | [Source and model examples](https://github.com/linker-bot/linkerhand-python-sdk)                                                             |
| OpenELAB product/SKU            | [Matched model and selectable variants](https://openelab.io/products/linker-hand-linkerbot-l6-11)                                            |

**Physical drawings:** preserve the flange/connector images in the existing manual; do not recreate dimensioned pinout diagrams from photos.

### References and validation

* LINKERBOT / Lingxin Qiaoshou, _L6 Product Manual_, **V1.4 (2026-05-18)**, provided upload, reviewed 2026-11-21.
* [Current official Linkerbot ROS 2 model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md), reviewed 2026-11-21.
* [OpenELAB exact model listing](https://openelab.io/products/linker-hand-linkerbot-l6-11), matched to catalog variant on 2026-11-21.

**Documentation review:** completed for provided revision; **software execution:** not run; **hardware test:** not run. Check the actual shipped interface and firmware before any actuator operation.

### Original LINKERBOT L6 Manufacturer Manual and Diagrams

The following preserves the previously published OEM manual content, technical tables and hosted images. Engineering setup above is a structured companion; hardware diagrams below remain the original source reference.

#### LINKERBOT Linker Hand L6 11-DOF Bionic Robotic Hand

{% embed url="https://openelab.io/products/linker-hand-linkerbot-l6-11" %}

![Linker Hand L6 product views](../../.gitbook/assets/l6-product-views.jpg)

#### Revision History

| Version | Date       | Description                                                    |
| ------- | ---------- | -------------------------------------------------------------- |
| V1.0    | 2025-09-02 | Initial edition                                                |
| V1.1    | 2025-09-04 | Updated motion specifications, product display, and dimensions |
| V1.2    | 2025-10-30 | Updated motion parameters and flange interface                 |
| V1.3    | 2026-02-05 | Added optional colors                                          |
| V1.4    | 2026-05-18 | Added the integrated status-indicator behavior                 |

#### Product Overview

The Linker Hand L6 is a high-precision bionic robotic hand with six active and five passive joints. Its self-developed joint modules and linkage transmission provide a rigid 607 g mechanism for precision assembly, irregular-object grasping, collaborative robots, and service robots.

![L6 structure and status-indicator locations](../../.gitbook/assets/l6-structure.jpg)

The integrated status indicator reports the operating condition:

* **Green:** normal operation.
* **Flashing yellow:** motor offline or motor fault.
* **Steady yellow:** abnormal sensor communication.
* **Red:** the main motor-control program is not operating correctly.

**Main Characteristics**

* Compact 607 g construction.
* High-rigidity linkage transmission and ±0.2 mm repeatability.
* 0.35-second opening/closing response.
* Independent thumb control and synchronized four-finger motion.
* Position, speed, tactile-force, and online firmware controls.

#### Dimensions, Colors, and Joints

![Linker Hand L6 external dimensions in millimetres](../../.gitbook/assets/l6-external-dimensions.jpg)

| Dimension                     |    Value |
| ----------------------------- | -------: |
| Fingertip to palm-base length |   193 mm |
| Maximum palm width            |    84 mm |
| Thumb tip to palm-base length | 142.5 mm |
| Wrist height                  |   4.7 mm |
| Wrist diameter                |    36 mm |

Available colors are Pearl White, Obsidian Black, and Tech Silver.

![Linker Hand L6 color options](../../.gitbook/assets/l6-colors.jpg)

The hand has 11 joints: six active and five passive. Active joints respond to control commands; the passive joints use elastic damping to conform to object contours, cushion contact, and reduce load on the drive system.

![Linker Hand L6 joint layout](../../.gitbook/assets/l6-joint-layout.jpg)

![Four-finger and thumb motion ranges](../../.gitbook/assets/l6-motion-ranges.jpg)

| Motion group       | Angle range | Maximum speed |
| ------------------ | ----------: | ------------: |
| Dorsal thumb base  |       43.2° |     127.06°/s |
| Index-finger root  |       66.9° |     179.84°/s |
| Middle-finger root |       65.2° |     180.61°/s |
| Ring-finger root   |       66.5° |      183.7°/s |
| Little-finger root |         67° |     185.08°/s |
| Thumb tip          |       34.8° |     102.35°/s |
| Index-finger tip   |       60.6° |      162.9°/s |
| Middle fingertip   |       58.6° |     162.33°/s |
| Ring-finger tip    |       58.1° |      160.5°/s |
| Little-finger tip  |       59.5° |     164.36°/s |
| Dorsal thumb swing |       72.6° |     177.51°/s |
| Closing time       |           — |        0.35 s |

#### Technical Specifications

| Parameter                     | Specification            |
| ----------------------------- | ------------------------ |
| Model                         | Linker Hand L6           |
| Degrees of freedom            | 6                        |
| Joints                        | 11: 6 active + 5 passive |
| Drive                         | Linkage transmission     |
| Control interface             | CAN / RS-485             |
| Weight                        | 607 g                    |
| Maximum load                  | 28 kg                    |
| Working voltage               | 24 V DC ±10%             |
| Quiescent current             | 0.2 A                    |
| Average no-load motor current | 0.6 A                    |
| Maximum current               | 5.6 A                    |
| Repeatability                 | Better than ±0.2 mm      |

| Mechanical performance                              | Specification |
| --------------------------------------------------- | ------------: |
| Maximum thumb-fingertip force                       |          12 N |
| Maximum fingertip force of each of the four fingers |          15 N |
| Maximum gripping force of each finger               |          50 N |

#### Control and Sensor Functions

* **Position control:** Controls the complete hand and individual joints along preset trajectories.
* **Speed control:** Adjusts finger movement speed to match the required precision and throughput.
* **Tactile feedback:** Fingertip sensing supports real-time force adjustment to protect fragile objects and prevent slipping.
* **Online upgrade:** The host computer can update firmware and optimize parameters.

| Sensor parameter         | Specification  |
| ------------------------ | -------------- |
| Piezoresistive array     | 6 × 12         |
| Force-sensitive area     | 9.6 × 14.4 mm  |
| Touch-force threshold    | 5 g            |
| Range                    | 20 N           |
| Service life             | 100,000 cycles |
| Communication frame rate | 200 FPS        |
| Scale                    | 0–4095         |

#### Installation and Commissioning

**Accessories**

1. USB-to-CAN debugging cable × 1
2. Power cable × 1
3. Power adapter × 1

![L6 accessories](../../.gitbook/assets/l6-accessories.jpg)

**Flange Interface**

Use the mounting-hole dimensions in the official flange drawing.

![L6 flange dimensions](../../.gitbook/assets/l6-flange.jpg)

**Communication Connector**

The hand uses an XT30 (2+2) connector.

![L6 XT30 connector and CAN terminals](../../.gitbook/assets/l6-connector.jpg)

#### Storage

If the product will remain unused for an extended period, return it to its original packaging. Store it indoors, away from dust and flammable, explosive, or corrosive gases and liquids. Keep the temperature between −10 and 50°C and relative humidity at or below 80%, without condensation.

#### Warranty and Service

The product has a 12-month limited warranty from the purchase date. Manufacturing or material defects are eligible for repair or component replacement. Normal wear, improper operation, accidental impact, unauthorized disassembly or modification, and failure to follow the instructions are excluded. Non-quality issues are not eligible for return or exchange. Contact official support instead of disassembling a malfunctioning product. Out-of-warranty repair may incur charges.

#### Development Resources

* [ROS SDK](https://github.com/linker-bot/linkerhand-ros-sdk)
* [ROS 2 SDK](https://github.com/linker-bot/linkerhand-ros2-sdk)
* [Python SDK](https://github.com/linker-bot/linkerhand-python-sdk)
* Technical support: `support@linkerbot.cn`
* [LINKERBOT official website](https://linkerbot.cn)
