---
description: >-
  LINKERBOT L30 Standard (Tendon-Driven) revision V1.3 (2025-10-27) engineering
  setup and read-only first result; exact model-specific safety constraints.
---

# LINKERBOT Linker Hand L30 Standard (Tendon-Driven) — Development Guide

{% hint style="info" %}
[**View LINKERBOT L30 Standard (Tendon-Driven) on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l30-l30)

**Model:** L30 Standard (Tendon-Driven) · **SKU:** `Linker-Hand-L30-JQ1 (left tendon-driven RS485 store option; manual says CAN FD; mismatch)` · **Manual:** V1.3 (2025-10-27)
{% endhint %}

[Return to LINKERBOT developer series](./) · [Preserved L30 Standard (Tendon-Driven) OEM manual in OpenELAB Wiki](../linker-hand-l30-standard-edition-product-manual.md)

### Product overview

**L30 Standard (Tendon-Driven)** has **17 controlled; 21 total (17 active, 4 passive), including one wrist DoF**. Its supplied manufacturer product manual is revision **V1.3 (2025-10-27)**. This page describes the exact model; any other Linkerbot hand with a similar number may have a different joint array, mounting flange, sensor option, adapter voltage or bus protocol. **Identity:** Linker-Hand-L30-JQ1 (left tendon-driven RS485 store option; manual says CAN FD; mismatch).

### Applications

* Model-specific end-effector integration into research manipulators and humanoid platforms.
* Safe device identification, position/state logging, and supervised dexterous control research.
* Tactile and closed-loop grasp studies **only when installed sensors and controls are verified**.

### Specifications

| Parameter                                  | Source-backed value                                                                                     |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------- |
| Controlled DoF and physical joints         | 17 controlled; 21 total (17 active, 4 passive), including one wrist DoF                                 |
| Power                                      | **24 VDC per attached OEM Standard manual; store lists 12 V in product comparison — CRITICAL CONFLICT** |
| Bus / variant                              | Manual CAN FD + miniUSB, while store offers CAN/RS485 variants — CRITICAL CONFLICT                      |
| Manufacturer-reported mass                 | ≈1400 g                                                                                                 |
| Manufacturer maximum load                  | 5 kg per OEM vs different store comparison payload; verify source scope                                 |
| Manufacturer-reported opening/closing time | 0.2 s                                                                                                   |
| Tactile/sensing                            | Optional fingertip piezoresistive sensor, 6×12 at 200 fps; **not automatically present**.               |
| Manual revision                            | V1.3 (2025-10-27)                                                                                       |

**Evidence:** exact attached product manual and corresponding connected product catalog where available. These are device-level figures, not automatically rated full-arm payload or production contact performance.

### Hardware and connections

1. Inspect the model, serial, left/right label and selected store interface; do not rely only on a family nickname.
2. Confirm the supplied adapter, supported cable, correct keyed connector and the mounting drawing **before** connecting DC power.
3. Use a stable fixture, keep fingers and cables away from moving linkages and make the operator's stop/disconnect method accessible.

#### Model-specific mechanical mounting

The Standard Edition manual shows an **M4 flange and a 160 × 160 mm mounting base drawing** on pages 12–13. The separate direct-drive L30 does not share this documented flange by assumption.

#### Electrical bus and connector

Its OEM XT30 (2+2) pin table gives CAN L, CAN H, GND, 24 V on page 13; the retail variant instead offers CAN/RS485 and a comparison cites 12 V. **Do not wire or energize from either source until the exact SKU is confirmed.**

**Manufacturer-model note:** The L30 model is **tendon-driven**, not the other Shopify **L30 Direct-Drive** item. The 17 active DoF include a wrist. Its manual calls the 500 kbps number a communication **bit rate**, not a 500 Hz loop rate.

### Software and development resources

| Resource                                                                                                                              | Verified purpose                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [Current seven-model Linkerbot ROS 2 driver](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                   | ROS 2 Humble/Jazzy driver and read-only state topics; **native CAN/CAN FD** model entry |
| [ROS 2 model compatibility matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) | Confirms active joint count, bus and per-model capability differences                   |
| [LinkerHand Python SDK](https://github.com/linker-bot/linkerhand-python-sdk)                                                          | Firmware/adapter-specific Python examples; verify variant and driver before using       |
| [Preserved L30 Standard (Tendon-Driven) OEM manual in OpenELAB Wiki](../linker-hand-l30-standard-edition-product-manual.md)           | Exact manual hardware, mechanical dimensions, connector and installation source         |

**Version constraint:** a current GitHub model entry does not certify a purchased RS485 variant for a CAN-only launch. Check model/device capabilities, firmware and the installed transport. Never run sample code that writes angles or torque as the first device check.

### Getting started

#### Prerequisites

Physical hand and variant labeling; correct original or manufacturer-approved adapter; matching CAN/CAN FD/RS485 interface; secure fixture; model manual. For first read-only software use, a compatible Windows host utility or ROS 2 environment must be available as appropriate.

#### First working result

1. **Documentation-only first check:** record the actual hand body/serial/side, installed flange, accessory list, power adapter label (voltage/polarity/current), controller label, bus connector and exact JQ SKU; compare against the 24 V CAN-FD manual and the storefront's 12 V/CAN-RS485 variants. Request written OEM/merchant pairing for that exact unit **before power, CAN connection, USB, or running dexterous\_hand\_controller.exe**.
2. Record current model, side, revision, bus, installed host utility/SDK commit and relevant status values. Do **not** command finger positions, resets, gains or torque until identity and safety are confirmed.

**Expected result:** A complete identity/adapter/bus reconciliation sheet; **powered first run blocked until source conflict is resolved**.

**If the check fails:** A controller application may show an L30 profile but that alone is not proof the adapter voltage and bus are safe. Stop and resolve exact revision/variant and terminal assignment.

#### Next safe experiment

With device and software explicitly approved, log a sequence of **read-only** state observations and compare expected joint count/units, metadata validity and sample freshness. Motion/grasping is a separate supervised step after confirming range, direction, force and stop behavior.

### Troubleshooting and FAQs

**A device appears but the reported joint count differs.** Confirm the exact model, model discovery, loaded SDK feature definition and **active DoF versus passive mechanical joints**. Do not pad/trim a control vector to guess joint mapping.

**The device does not connect or respond.** A controller application may show an L30 profile but that alone is not proof the adapter voltage and bus are safe. Stop and resolve exact revision/variant and terminal assignment.

**Can I use another Linkerbot model's power cable or protocol?** No. This model's documented electrical interface is **Manual CAN FD + miniUSB, while store offers CAN/RS485 variants — CRITICAL CONFLICT**; use its own labeled cable, supply and OEM connector drawing.

**Can I assume tactile data is present?** Optional fingertip piezoresistive sensor, 6×12 at 200 fps; **not automatically present**. Validate sensor options and returned data before relying on tactile feedback.

### Downloads and technical documents

| Resource                        | Scope and link                                                                                                                               |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Original product manual         | [Preserved L30 Standard (Tendon-Driven) OEM manual in OpenELAB Wiki](../linker-hand-l30-standard-edition-product-manual.md)                  |
| Manufacturer ROS 2 model matrix | [Model definitions and control semantics](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) |
| Manufacturer current ROS 2 SDK  | [Installation and examples](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                                           |
| Manufacturer Python SDK         | [Source and model examples](https://github.com/linker-bot/linkerhand-python-sdk)                                                             |
| OpenELAB product/SKU            | [Matched model and selectable variants](https://openelab.io/products/linker-hand-linkerbot-l30-l30)                                          |

**Physical drawings:** preserve the flange/connector images in the existing manual; do not recreate dimensioned pinout diagrams from photos.

### References and validation

* LINKERBOT / Lingxin Qiaoshou, _L30 Standard (Tendon-Driven) Product Manual_, **V1.3 (2025-10-27)**, provided upload, reviewed 2026-11-21.
* [Current official Linkerbot ROS 2 model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md), reviewed 2026-11-21.
* [OpenELAB exact model listing](https://openelab.io/products/linker-hand-linkerbot-l30-l30), matched to catalog variant on 2026-11-21.

**Documentation review:** completed for provided revision; **software execution:** not run; **hardware test:** not run. **Critical block:** voltage/protocol discrepancy unresolved—no powered bring-up may be inferred.
