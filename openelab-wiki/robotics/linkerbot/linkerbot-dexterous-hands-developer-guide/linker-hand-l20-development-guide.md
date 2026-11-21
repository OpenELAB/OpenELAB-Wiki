---
description: >-
  LINKERBOT L20 revision V1.3 (2026-08-04; filename says V10) engineering setup
  and read-only first result; exact model-specific safety constraints.
---

# LINKERBOT Linker Hand L20 — Development Guide

{% hint style="info" %}
[**View LINKERBOT L20 on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l20-21)

**Model:** L20 · **SKU:** `Linker-Hand-L20-1 (left, RS485; confirm variant)` · **Manual:** V1.3 (2026-08-04; filename says V10)
{% endhint %}

[Return to LINKERBOT developer series](./) · [Preserved L20 OEM manual in OpenELAB Wiki](../linker-hand-l20-product-manual.md)

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
| [Preserved L20 OEM manual in OpenELAB Wiki](../linker-hand-l20-product-manual.md)                                                     | Exact manual hardware, mechanical dimensions, connector and installation source         |

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
| Original product manual         | [Preserved L20 OEM manual in OpenELAB Wiki](../linker-hand-l20-product-manual.md)                                                            |
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
