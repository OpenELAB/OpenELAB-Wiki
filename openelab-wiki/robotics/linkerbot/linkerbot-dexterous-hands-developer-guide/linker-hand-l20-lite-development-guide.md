---
description: >-
  LINKERBOT L20 Lite revision V1.0 (2025-09-11) engineering setup and read-only
  first result; exact model-specific safety constraints.
---

# LINKERBOT Linker Hand L20 Lite — Development Guide

{% hint style="info" %}
[**View LINKERBOT L20 Lite on OpenELAB**](https://openelab.io/products/linker-hand-linkerbot-l20-lite)

**Model:** L20 Lite · **SKU:** `Linker-Hand-L20-Lite-1 (left, RS485; confirm chosen side/bus)` · **Manual:** V1.0 (2025-09-11)
{% endhint %}

[Return to LINKERBOT developer series](./) · [Preserved L20 Lite OEM manual in OpenELAB Wiki](../linker-hand-l20-lite-product-manual.md)

### Product overview

**L20 Lite** has **10 controlled; 20 total (10 active, 10 passive)**. Its supplied manufacturer product manual is revision **V1.0 (2025-09-11)**. This page describes the exact model; any other Linkerbot hand with a similar number may have a different joint array, mounting flange, sensor option, adapter voltage or bus protocol. **Identity:** Linker-Hand-L20-Lite-1 (left, RS485; confirm chosen side/bus).

### Applications

* Model-specific end-effector integration into research manipulators and humanoid platforms.
* Safe device identification, position/state logging, and supervised dexterous control research.
* Tactile and closed-loop grasp studies **only when installed sensors and controls are verified**.

### Specifications

| Parameter                                  | Source-backed value                                                                                                                    |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------- |
| Controlled DoF and physical joints         | 10 controlled; 20 total (10 active, 10 passive)                                                                                        |
| Power                                      | **24 VDC ±10%**                                                                                                                        |
| Bus / variant                              | CAN/RS485; actual store variant must match adapter                                                                                     |
| Manufacturer-reported mass                 | 800 g                                                                                                                                  |
| Manufacturer maximum load                  | 25 kg per OEM manual vs 5 kg listed in storefront (discrepancy)                                                                        |
| Manufacturer-reported opening/closing time | 1.2 s                                                                                                                                  |
| Tactile/sensing                            | Fingertip piezoresistive 6×12 array at 200 fps; optional ≥50 Hz capacitive sensor and optional visual-tactile module are NOT standard. |
| Manual revision                            | V1.0 (2025-09-11)                                                                                                                      |

**Evidence:** exact attached product manual and corresponding connected product catalog where available. These are device-level figures, not automatically rated full-arm payload or production contact performance.

### Hardware and connections

1. Inspect the model, serial, left/right label and selected store interface; do not rely only on a family nickname.
2. Confirm the supplied adapter, supported cable, correct keyed connector and the mounting drawing **before** connecting DC power.
3. Use a stable fixture, keep fingers and cables away from moving linkages and make the operator's stop/disconnect method accessible.

#### Model-specific mechanical mounting

M3 flange screws, length determined from mounting-thickness and **L20 Lite V1.0 page 13** drawing.

#### Electrical bus and connector

XT30 (2+2) **on the documented CAN connection**: pin 1 CAN L, 2 CAN H, 3 GND, 4 +24 V. Confirm keyed orientation and purchased RS485 versus CAN adapter. Do not transfer this pin table to other hand models.

**Manufacturer-model note:** The storefront title calls this a '20-DOF' hand, but the manual defines **10 active plus 10 passive joints**, and the modern ROS 2 driver exposes **10 controllable axes**. Do not send a 20-element motor vector.

### Software and development resources

| Resource                                                                                                                              | Verified purpose                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [Current seven-model Linkerbot ROS 2 driver](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                   | ROS 2 Humble/Jazzy driver and read-only state topics; **native CAN/CAN FD** model entry |
| [ROS 2 model compatibility matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) | Confirms active joint count, bus and per-model capability differences                   |
| [LinkerHand Python SDK](https://github.com/linker-bot/linkerhand-python-sdk)                                                          | Firmware/adapter-specific Python examples; verify variant and driver before using       |
| [Preserved L20 Lite OEM manual in OpenELAB Wiki](../linker-hand-l20-lite-product-manual.md)                                           | Exact manual hardware, mechanical dimensions, connector and installation source         |

**Version constraint:** a current GitHub model entry does not certify a purchased RS485 variant for a CAN-only launch. Check model/device capabilities, firmware and the installed transport. Never run sample code that writes angles or torque as the first device check.

### Getting started

#### Prerequisites

Physical hand and variant labeling; correct original or manufacturer-approved adapter; matching CAN/CAN FD/RS485 interface; secure fixture; model manual. For first read-only software use, a compatible Windows host utility or ROS 2 environment must be available as appropriate.

#### First working result

1. Following the OEM Windows CAN commissioning section, install the compatible **PEAK USB-to-CAN driver** if Windows, adjust `can_bridge_dashboard/config.toml` `can_interface` to the actual interface(s) (example `['can1']`), launch the supplied `can_bridge.exe`, then the matching `dashboard.exe` and open `http://localhost:9090`. Select the actual hand model, side and port; inspect **online/offline status without touching global control, sliders or preset actions**.
2. Record current model, side, revision, bus, installed host utility/SDK commit and relevant status values. Do **not** command finger positions, resets, gains or torque until identity and safety are confirmed.

**Expected result:** A reachable local dashboard showing the selected device's online status, port and model, without motion.

**If the check fails:** If the dashboard is inaccessible, check CAN bridge process/log (`can_bridge.log`), PEAK driver and interface names. On Windows the manual says restart the CAN bridge after device plug/unplug.

#### Next safe experiment

With device and software explicitly approved, log a sequence of **read-only** state observations and compare expected joint count/units, metadata validity and sample freshness. Motion/grasping is a separate supervised step after confirming range, direction, force and stop behavior.

### Troubleshooting and FAQs

**A device appears but the reported joint count differs.** Confirm the exact model, model discovery, loaded SDK feature definition and **active DoF versus passive mechanical joints**. Do not pad/trim a control vector to guess joint mapping.

**The device does not connect or respond.** If the dashboard is inaccessible, check CAN bridge process/log (`can_bridge.log`), PEAK driver and interface names. On Windows the manual says restart the CAN bridge after device plug/unplug.

**Can I use another Linkerbot model's power cable or protocol?** No. This model's documented electrical interface is **CAN/RS485; actual store variant must match adapter**; use its own labeled cable, supply and OEM connector drawing.

**Can I assume tactile data is present?** Fingertip piezoresistive 6×12 array at 200 fps; optional ≥50 Hz capacitive sensor and optional visual-tactile module are NOT standard. Validate sensor options and returned data before relying on tactile feedback.

### Downloads and technical documents

| Resource                        | Scope and link                                                                                                                               |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Original product manual         | [Preserved L20 Lite OEM manual in OpenELAB Wiki](../linker-hand-l20-lite-product-manual.md)                                                  |
| Manufacturer ROS 2 model matrix | [Model definitions and control semantics](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) |
| Manufacturer current ROS 2 SDK  | [Installation and examples](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                                           |
| Manufacturer Python SDK         | [Source and model examples](https://github.com/linker-bot/linkerhand-python-sdk)                                                             |
| OpenELAB product/SKU            | [Matched model and selectable variants](https://openelab.io/products/linker-hand-linkerbot-l20-lite)                                         |

**Physical drawings:** preserve the flange/connector images in the existing manual; do not recreate dimensioned pinout diagrams from photos.

### References and validation

* LINKERBOT / Lingxin Qiaoshou, _L20 Lite Product Manual_, **V1.0 (2025-09-11)**, provided upload, reviewed 2026-11-21.
* [Current official Linkerbot ROS 2 model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md), reviewed 2026-11-21.
* [OpenELAB exact model listing](https://openelab.io/products/linker-hand-linkerbot-l20-lite), matched to catalog variant on 2026-11-21.

**Documentation review:** completed for provided revision; **software execution:** not run; **hardware test:** not run. Check the actual shipped interface and firmware before any actuator operation.
