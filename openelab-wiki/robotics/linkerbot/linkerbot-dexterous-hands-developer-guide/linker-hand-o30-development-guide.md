---
description: >-
  LINKERBOT O30 revision V1.0 (2026-07-10) engineering setup and read-only first
  result; exact model-specific safety constraints.
---

# LINKERBOT Linker Hand O30 — Development Guide (Store Match Pending)

{% hint style="warning" %}
**No verified OpenELAB .io product page or SKU for LINKERBOT O30.** This is a **manufacturer-manual-based draft**; do not assign a store variant or approve electrical commissioning from this page alone.

**Model:** O30 · **Manual:** V1.0 (2026-07-10)
{% endhint %}

[Return to LINKERBOT developer series](./) · [Preserved O30 OEM manual in OpenELAB Wiki](../linker-hand-o30-product-manual.md)

### Product overview

**O30** has **20 active; 20 total joints**. Its supplied manufacturer product manual is revision **V1.0 (2026-07-10)**. This page describes the exact model; any other Linkerbot hand with a similar number may have a different joint array, mounting flange, sensor option, adapter voltage or bus protocol. **Identity:** Not found in connected OpenELAB .io product catalog; OEM model identity only.

### Applications

* Model-specific end-effector integration into research manipulators and humanoid platforms.
* Safe device identification, position/state logging, and supervised dexterous control research.
* Tactile and closed-loop grasp studies **only when installed sensors and controls are verified**.

### Specifications

| Parameter                                  | Source-backed value                                                                                                 |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------------- |
| Controlled DoF and physical joints         | 20 active; 20 total joints                                                                                          |
| Power                                      | **24–48 VDC per OEM manual, correct adapter/revision must be checked**                                              |
| Bus / variant                              | CAN / CAN FD; model-specific R20\_V3.0\_PAB20260529 connector                                                       |
| Manufacturer-reported mass                 | 730 g                                                                                                               |
| Manufacturer maximum load                  | 30 kg maximum load per OEM                                                                                          |
| Manufacturer-reported opening/closing time | 0.8 s                                                                                                               |
| Tactile/sensing                            | 6×11 pressure-sensitive array, 200 fps, 20 N/cm² reported sensing range; do not substitute O20 6×12/30 Hz encoding. |
| Manual revision                            | V1.0 (2026-07-10)                                                                                                   |

**Evidence:** exact attached product manual and corresponding connected product catalog where available. These are device-level figures, not automatically rated full-arm payload or production contact performance.

### Hardware and connections

1. Inspect the model, serial, left/right label and selected store interface; do not rely only on a family nickname.
2. Confirm the supplied adapter, supported cable, correct keyed connector and the mounting drawing **before** connecting DC power.
3. Use a stable fixture, keep fingers and cables away from moving linkages and make the operator's stop/disconnect method accessible.

#### Model-specific mechanical mounting

M3 flange mounting, model-specific OEM drawing on page 12.

#### Electrical bus and connector

**R20\_V3.0\_PAB20260529** multipin connector pictured on **O30 V1.0 page 12**, with dedicated VCC/CAN\_H/CAN\_L/GND. Do not copy the O20 or XT30 pinout; orientation is essential.

**Manufacturer-model note:** O30's **20 individually actuated joints** and tactile layout differ from O20. The OEM host utility is **`O30_hand_ui.exe`**, with a read-only CAN-connection and version information view plus motion-producing controls.

### Software and development resources

| Resource                                                                                                                              | Verified purpose                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [Current seven-model Linkerbot ROS 2 driver](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                   | ROS 2 Humble/Jazzy driver and read-only state topics; **native CAN/CAN FD** model entry |
| [ROS 2 model compatibility matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) | Confirms active joint count, bus and per-model capability differences                   |
| [LinkerHand Python SDK](https://github.com/linker-bot/linkerhand-python-sdk)                                                          | Firmware/adapter-specific Python examples; verify variant and driver before using       |
| [Preserved O30 OEM manual in OpenELAB Wiki](../linker-hand-o30-product-manual.md)                                                     | Exact manual hardware, mechanical dimensions, connector and installation source         |

**Version constraint:** a current GitHub model entry does not certify a purchased RS485 variant for a CAN-only launch. Check model/device capabilities, firmware and the installed transport. Never run sample code that writes angles or torque as the first device check.

### Getting started

#### Prerequisites

Physical hand and variant labeling; correct original or manufacturer-approved adapter; matching CAN/CAN FD/RS485 interface; secure fixture; model manual. For first read-only software use, a compatible Windows host utility or ROS 2 environment must be available as appropriate.

#### First working result

1. Confirm the exact O30 model, supplied adapter, side and unique connector with OEM pin diagram. Because no matched OpenELAB product SKU exists, hold electrical commissioning until the actual supply/cable provenance is verified. Then, on a validated Windows CAN-FD setup, run the delivered **`O30_hand_ui.exe`**, use the **CAN Connect** button, and select **Read Version Information** without moving sliders or activating finger-dance/table routines.
2. Record current model, side, revision, bus, installed host utility/SDK commit and relevant status values. Do **not** command finger positions, resets, gains or torque until identity and safety are confirmed.

**Expected result:** Device/version identification and online status, and later (if approved) 20 valid active joint observations.

**If the check fails:** If O30 status is missing, check the CAN-FD adapter, installed firmware, controller/device ID and connector orientation. Never use O20's 16-element action table or assume same sensor matrix.

#### Next safe experiment

With device and software explicitly approved, log a sequence of **read-only** state observations and compare expected joint count/units, metadata validity and sample freshness. Motion/grasping is a separate supervised step after confirming range, direction, force and stop behavior.

### Troubleshooting and FAQs

**A device appears but the reported joint count differs.** Confirm the exact model, model discovery, loaded SDK feature definition and **active DoF versus passive mechanical joints**. Do not pad/trim a control vector to guess joint mapping.

**The device does not connect or respond.** If O30 status is missing, check the CAN-FD adapter, installed firmware, controller/device ID and connector orientation. Never use O20's 16-element action table or assume same sensor matrix.

**Can I use another Linkerbot model's power cable or protocol?** No. This model's documented electrical interface is **CAN / CAN FD; model-specific R20\_V3.0\_PAB20260529 connector**; use its own labeled cable, supply and OEM connector drawing.

**Can I assume tactile data is present?** 6×11 pressure-sensitive array, 200 fps, 20 N/cm² reported sensing range; do not substitute O20 6×12/30 Hz encoding. Validate sensor options and returned data before relying on tactile feedback.

### Downloads and technical documents

| Resource                        | Scope and link                                                                                                                               |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Original product manual         | [Preserved O30 OEM manual in OpenELAB Wiki](../linker-hand-o30-product-manual.md)                                                            |
| Manufacturer ROS 2 model matrix | [Model definitions and control semantics](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) |
| Manufacturer current ROS 2 SDK  | [Installation and examples](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                                           |
| Manufacturer Python SDK         | [Source and model examples](https://github.com/linker-bot/linkerhand-python-sdk)                                                             |
| OpenELAB product/SKU            | No matching .io catalog product verified; match pending                                                                                      |

**Physical drawings:** preserve the flange/connector images in the existing manual; do not recreate dimensioned pinout diagrams from photos.

### References and validation

* LINKERBOT / Lingxin Qiaoshou, _O30 Product Manual_, **V1.0 (2026-07-10)**, provided upload, reviewed 2026-11-21.
* [Current official Linkerbot ROS 2 model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md), reviewed 2026-11-21.
* OpenELAB .io product catalog search, 2026-11-21: **no product/SKU match** for this model.

**Documentation review:** completed for provided revision; **software execution:** not run; **hardware test:** not run. **Identity block:** store SKU and actual adapter/connector pairing unresolved—physical first result must await confirmation.
