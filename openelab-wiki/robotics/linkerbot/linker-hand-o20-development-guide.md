---
description: >-
  Canonical LINKERBOT O20 manufacturer manual-based development guide; OpenELAB
  SKU match remains pending.
---

# LINKERBOT Linker Hand O20 — Product & Developer Guide (Store Match Pending)

{% hint style="warning" %}
**No verified OpenELAB .io product page or SKU for LINKERBOT O20.** This is a **manufacturer-manual-based draft**; do not assign a store variant or approve electrical commissioning from this page alone.

**Model:** O20 · **Manual:** V1.2 (2026-06-05; filename says V10)
{% endhint %}

[LINKERBOT manufacturer page](./) · [Seven-model developer hub](linkerbot-dexterous-hands-developer-guide/)

### Product overview

**O20** has **16 active; 16 total joints**. Its supplied manufacturer product manual is revision **V1.2 (2026-06-05; filename says V10)**. This page describes the exact model; any other Linkerbot hand with a similar number may have a different joint array, mounting flange, sensor option, adapter voltage or bus protocol. **Identity:** Not found in connected OpenELAB .io product catalog; OEM model identity only.

### Applications

* Model-specific end-effector integration into research manipulators and humanoid platforms.
* Safe device identification, position/state logging, and supervised dexterous control research.
* Tactile and closed-loop grasp studies **only when installed sensors and controls are verified**.

### Specifications

| Parameter                                  | Source-backed value                                                                                           |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------- |
| Controlled DoF and physical joints         | 16 active; 16 total joints                                                                                    |
| Power                                      | **24 VDC ±10%**                                                                                               |
| Bus / variant                              | **CAN FD** with O20\_V1.0\_PAB20251123 connector                                                              |
| Manufacturer-reported mass                 | 888 g                                                                                                         |
| Manufacturer maximum load                  | 36 kg maximum load per OEM V1.2; independent end-effector suitability must be assessed                        |
| Manufacturer-reported opening/closing time | 0.88 s                                                                                                        |
| Tactile/sensing                            | 6×12 pressure array, reported **30 Hz refresh**; do NOT confuse with the 1000 Hz bus communication frequency. |
| Manual revision                            | V1.2 (2026-06-05; filename says V10)                                                                          |

**Evidence:** exact attached product manual and corresponding connected product catalog where available. These are device-level figures, not automatically rated full-arm payload or production contact performance.

### Hardware and connections

1. Inspect the model, serial, left/right label and selected store interface; do not rely only on a family nickname.
2. Confirm the supplied adapter, supported cable, correct keyed connector and the mounting drawing **before** connecting DC power.
3. Use a stable fixture, keep fingers and cables away from moving linkages and make the operator's stop/disconnect method accessible.

#### Model-specific mechanical mounting

M3 flange mounting with **O20-specific drawing on the uploaded manual page 13**.

#### Electrical bus and connector

**O20\_V1.0\_PAB20251123 multipin connector**, illustrated on manual page 14. Not XT30 (2+2). Use OEM orientation/pin diagram and a **USB-to-CAN-FD** adapter. Do not infer mating connector from L-series hands.

**Manufacturer-model note:** The O20 manual documents a Windows host program **`020_hand_ui.exe`** and separate position, temperature, current and tactile curves. It shows CAN button changing to green on connection; Read Version Information does not send motion.

### Software and development resources

| Resource                                                                                                                                                     | Verified purpose                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------- |
| [Current seven-model Linkerbot ROS 2 driver](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                                          | ROS 2 Humble/Jazzy driver and read-only state topics; **native CAN/CAN FD** model entry |
| [ROS 2 model compatibility matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md)                        | Confirms active joint count, bus and per-model capability differences                   |
| [LinkerHand Python SDK](https://github.com/linker-bot/linkerhand-python-sdk)                                                                                 | Firmware/adapter-specific Python examples; verify variant and driver before using       |
| **O20 OEM manual V1.2 (2026-06-05; filename says V10)** — supplied as an upload in the authoring conversation; permanent GitBook file link not yet available | Exact manual hardware, mechanical dimensions, connector and installation source         |

**Version constraint:** a current GitHub model entry does not certify a purchased RS485 variant for a CAN-only launch. Check model/device capabilities, firmware and the installed transport. Never run sample code that writes angles or torque as the first device check.

### Getting started

#### Prerequisites

Physical hand and variant labeling; correct original or manufacturer-approved adapter; matching CAN/CAN FD/RS485 interface; secure fixture; model manual. For first read-only software use, a compatible Windows host utility or ROS 2 environment must be available as appropriate.

#### First working result

1. First identify model/body/serial, cable and the unique **O20 multipin connector**, and obtain the OEM-approved 24 V adapter and USB-to-CAN-FD tool. Because the OpenELAB store match is **unverified**, do not power an unidentified unit. After exact hardware/adapter verification by the supplier, run the delivered Windows **`020_hand_ui.exe`**, select the correct CAN-FD module, click **Connect CAN** then **Read Version Information**. Avoid zero/reset, sliders, finger dance, table execution or overcurrent/calibration writes.
2. Record current model, side, revision, bus, installed host utility/SDK commit and relevant status values. Do **not** command finger positions, resets, gains or torque until identity and safety are confirmed.

**Expected result:** A verified O20 identity, controller version/ID and read-only status; no motion.

**If the check fails:** If the CAN connection remains black/not connected, inspect USB-to-CAN-FD driver and actual physical connector/controller ID; do not use an L20 ordinary CAN adapter or modify calibration/overcurrent limits.

#### Next safe experiment

With device and software explicitly approved, log a sequence of **read-only** state observations and compare expected joint count/units, metadata validity and sample freshness. Motion/grasping is a separate supervised step after confirming range, direction, force and stop behavior.

### Troubleshooting and FAQs

**A device appears but the reported joint count differs.** Confirm the exact model, model discovery, loaded SDK feature definition and **active DoF versus passive mechanical joints**. Do not pad/trim a control vector to guess joint mapping.

**The device does not connect or respond.** If the CAN connection remains black/not connected, inspect USB-to-CAN-FD driver and actual physical connector/controller ID; do not use an L20 ordinary CAN adapter or modify calibration/overcurrent limits.

**Can I use another Linkerbot model's power cable or protocol?** No. This model's documented electrical interface is **CAN FD with O20\_V1.0\_PAB20251123 connector**; use its own labeled cable, supply and OEM connector drawing.

**Can I assume tactile data is present?** 6×12 pressure array, reported **30 Hz refresh**; do NOT confuse with the 1000 Hz bus communication frequency. Validate sensor options and returned data before relying on tactile feedback.

### Downloads and technical documents

| Resource                        | Scope and link                                                                                                                                               |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Original product manual         | **O20 OEM manual V1.2 (2026-06-05; filename says V10)** — supplied as an upload in the authoring conversation; permanent GitBook file link not yet available |
| Manufacturer ROS 2 model matrix | [Model definitions and control semantics](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md)                 |
| Manufacturer current ROS 2 SDK  | [Installation and examples](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                                                           |
| Manufacturer Python SDK         | [Source and model examples](https://github.com/linker-bot/linkerhand-python-sdk)                                                                             |
| OpenELAB product/SKU            | No matching .io catalog product verified; match pending                                                                                                      |

**Physical drawings:** preserve the flange/connector images in the existing manual; do not recreate dimensioned pinout diagrams from photos.

### References and validation

* LINKERBOT / Lingxin Qiaoshou, _O20 Product Manual_, **V1.2 (2026-06-05; filename says V10)**, provided upload, reviewed 2026-11-21.
* [Current official Linkerbot ROS 2 model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md), reviewed 2026-11-21.
* OpenELAB .io product catalog search, 2026-11-21: **no product/SKU match** for this model.

**Documentation review:** completed for provided revision; **software execution:** not run; **hardware test:** not run. **Identity block:** store SKU and actual adapter/connector pairing unresolved—physical first result must await confirmation.
