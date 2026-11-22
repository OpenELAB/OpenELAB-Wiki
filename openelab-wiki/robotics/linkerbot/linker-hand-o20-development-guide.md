---
description: >-
  Canonical LINKERBOT O20 manufacturer manual-based development guide; OpenELAB
  SKU match remains pending.
---

# LINKERBOT Linker Hand O20 — Product & Developer Guide (Store Match Pending)

{% hint style="warning" %}
**No verified OpenELAB .io product page or SKU for LINKERBOT O20.** This is a **published manufacturer-manual reference**; do not assign a store variant or approve electrical commissioning from this page alone.

**Model:** O20 · **Manual:** V1.2 (2026-06-05; filename says V10)
{% endhint %}

[**Complete supplied O20 manual — 30 PDF pages and downloads**](source-library/complete-o20.md) · [All seven complete manuals](source-library/)

[LINKERBOT manufacturer page](./) · [Seven-model developer hub](linkerbot-dexterous-hands-developer-guide/)

## Product overview

**O20** has **16 active; 16 total joints**. Its supplied manufacturer product manual is revision **V1.2 (2026-06-05; filename says V10)**. This page describes the exact model; any other Linkerbot hand with a similar number may have a different joint array, mounting flange, sensor option, adapter voltage or bus protocol. **Identity:** Not found in connected OpenELAB .io product catalog; OEM model identity only.

## Applications

* Model-specific end-effector integration into research manipulators and humanoid platforms.
* Safe device identification, position/state logging, and supervised dexterous control research.
* Tactile and closed-loop grasp studies **only when installed sensors and controls are verified**.

## Specifications

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

## Complete supplied-manual reference

The following details supplement the original guide using **V1.2 · 2026-06-05**. Every supplied page, including diagrams, revision history, controls and service clauses, is available in the [Complete supplied O20 manual — 30 PDF pages and downloads](source-library/complete-o20.md).

### Detailed electrical, mechanical and sensor parameters

| Parameter                       | Manufacturer source entry                                                                                     |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| Joints and transmission wording | 16 active joints; overview brushless hollow-cup motor / worm-gear module; parameter-table mode “Direct drive” |
| DC input and current            | 24 V ±10%; 0.27 A quiescent, 0.8 A no-load motor average, 2 A maximum                                         |
| Bus, mass and cycle             | CAN FD; 1000 Hz communication entry; 888 g; opening/closing 0.88 s                                            |
| Mechanical force                | Thumb fingertip 6.5 N; other fingertips 10 N; each-finger maximum grip 44 N                                   |
| Load discrepancy                | Overview rated load 20 kg; parameter-table maximum load 36 kg; test conditions not defined                    |
| Repeatability                   | 0.2 mm as printed; do not add an unstated sign or test condition                                              |
| Piezoresistive sensor           | 6×12; 0.7×0.7 mm spatial resolution; 0.5 N touch force; 0.5–20 N range; 0.1 N resolution                      |
| Tactile life and traffic        | 200,000 cycles; 921600 bps traffic entry; 30 Hz refresh, separate from 1000 Hz bus entry                      |

Sources: [PDF page 11](source-library/complete-o20.md#pdf-page-11) and the chapter map below. Maximum-load, maximum-force and cycle entries are manufacturer figures; the manual does not establish that they can be reached simultaneously or safely in a complete robot.

### Joint ranges and source interpretation

| Joint / motion label                | Source angle range (degrees) | Source speed entry (°/s unless noted) |
| ----------------------------------- | ---------------------------- | ------------------------------------- |
| THUMB1 bend / THUMB2 bend           | 89.2 / 67                    | 99 / 96                               |
| THUMB3 side swing / THUMB4 rotation | 126.2 / 60                   | 103 / Not specified                   |
| LF1 / RF1 / MF1 / FF1 bend          | 114                          | 125                                   |
| LF2 / RF2 / MF2 / FF2 bend          | 112                          | 109                                   |
| LF3 / RF3 / MF3 / FF3 lateral swing | 17.5 / 23.1 / 30.6 / 25.3    | Not specified                         |

Source: [PDF page 10](source-library/complete-o20.md#pdf-page-10). Physical/passive joint labels are not an independent command-vector definition.

Use internal **V1.2 (2026-06-05)**, not the filename’s “V10”. The 20 kg rated versus 36 kg maximum entries are different source claims, with no demonstrated duty cycle, orientation or safe suspended-load condition. The complete reference retains both. Neither is permission to lift that mass on a host robot. The connector is **O20\_V1.0\_PAB20251123**, named with the mounting instructions on original **PDF page 13**, with the actual pin-orientation diagram on **PDF page 14**. It is not the L20/L-series XT30 assembly. A verified OpenELAB product/SKU URL remains unavailable.

### Mounting, supplied items and model-specific operation

The manual lists a USB-to-CAN-FD adapter, power adapter and power line, and describes driver-free Windows use for that supplied adapter. The executable name is **`020_hand_ui.exe`** (leading zero as printed). After approved hardware setup, the CAN button becomes green on connection; Read Version Information retrieves PCB version, unique ID, factory serial, embedded version and hand ID. Temperature/current/pressure plots have their own query start/stop controls; `position` is returned motor position and `position_ui` the target. The action table has **18 columns: row number + 16 joints + interval**. Whole-table execution defaults to **1000 ms** between rows; looping/finger dance and zero/reset move the hand. Parameter Send can transmit defaults when inputs are empty, and low overcurrent entries are clamped to the UI’s minimum. Deviation, calibration and protected device-information writes require the matching manufacturer procedure; they are not communication recovery steps.

The source connector diagram labels **pins 1 and 2 VCC, pin 3 CAN H, pin 4 CAN L, pins 5 and 6 GND**. Read its keyed connector/viewing orientation in [PDF page 14](source-library/complete-o20.md#pdf-page-14) before identifying a physical contact; identical signal names do not establish interchangeable mating hardware.

### Complete chapter and drawing map

| Original PDF page                                         | Topic                                                |
| --------------------------------------------------------- | ---------------------------------------------------- |
| [PDF page 2](source-library/complete-o20.md#pdf-page-2)   | Revision history                                     |
| [PDF page 3](source-library/complete-o20.md#pdf-page-3)   | Safety requirements                                  |
| [PDF page 5](source-library/complete-o20.md#pdf-page-5)   | Overview, transmission and rated-load claim          |
| [PDF page 7](source-library/complete-o20.md#pdf-page-7)   | Dimensions and joint count                           |
| [PDF page 10](source-library/complete-o20.md#pdf-page-10) | Actual joint limits and speeds                       |
| [PDF page 11](source-library/complete-o20.md#pdf-page-11) | Electrical/force/max-load table                      |
| [PDF page 12](source-library/complete-o20.md#pdf-page-12) | Tactile and accessory parameters                     |
| [PDF page 13](source-library/complete-o20.md#pdf-page-13) | M3 flange and connector identity                     |
| [PDF page 14](source-library/complete-o20.md#pdf-page-14) | Connector pin diagram, CAN-FD setup and host program |
| [PDF page 19](source-library/complete-o20.md#pdf-page-19) | CAN connected indication                             |
| [PDF page 21](source-library/complete-o20.md#pdf-page-21) | Version query                                        |
| [PDF page 22](source-library/complete-o20.md#pdf-page-22) | Control button functions                             |
| [PDF page 23](source-library/complete-o20.md#pdf-page-23) | 18-column sequence file format                       |
| [PDF page 24](source-library/complete-o20.md#pdf-page-24) | Intervals, loops and stop controls                   |
| [PDF page 25](source-library/complete-o20.md#pdf-page-25) | Telemetry query controls                             |
| [PDF page 26](source-library/complete-o20.md#pdf-page-26) | Actual/target curves and parameter writes            |
| [PDF page 27](source-library/complete-o20.md#pdf-page-27) | Deviation, overcurrent and calibration               |
| [PDF page 28](source-library/complete-o20.md#pdf-page-28) | Warranty                                             |
| [PDF page 30](source-library/complete-o20.md#pdf-page-30) | SDK appendix                                         |

### Service, recovery and development records

The source provides a **12-month limited warranty from purchase** for manufacturing/material defects, excludes normal wear and improper operation, impact/accidents, unauthorized disassembly or use contrary to instructions, and describes paid out-of-warranty service. The original return/exchange exclusions remain in the complete reference; use the actual sales agreement for an order. If a fault occurs, stop operation and contact manufacturer support rather than dismantling the hand. Preserve model/side, serial, firmware/PCB revision, supply label, adapter, SDK commit, LED/error state and logs with the service request. Manufacturer support is `support@linkerbot.cn`; this wiki review does not send a support request.

The manuals describe firmware-upgrade capability, but do not include every model-specific firmware image, recovery package, binary protocol, CAD/URDF model or installer. Original drawings and screenshots are included; obtain the exact missing package from the manufacturer. Do not flash a related model or create pin mappings from an image’s appearance.

For current software, read the [pinned O20 feature guide](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/8d56b3355d2cfcd90e4e3c6b377ebceb7a5c09ac/linkerbot_hand_ros/docs/o20.md) and [model/capability definitions](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/8d56b3355d2cfcd90e4e3c6b377ebceb7a5c09ac/linkerbot_hand_ros/docs/models.md). The current ROS 2 stack and its `linkerbot-hand-python-sdk` dependency differ from the older `linkerhand-python-sdk` appendix. Check actual bus, joint names, validity masks and raw-unit metadata; cached configuration values are not live torque/current measurements. Current source reviewed at `8d56b3355d2c` on 22 November 2026. Software build and hardware operation were **not run**.

## Hardware and connections

1. Inspect the model, serial, left/right label and selected store interface; do not rely only on a family nickname.
2. Confirm the supplied adapter, supported cable, correct keyed connector and the mounting drawing **before** connecting DC power.
3. Use a stable fixture, keep fingers and cables away from moving linkages and make the operator's stop/disconnect method accessible.

### Model-specific mechanical mounting

M3 flange mounting with **O20-specific drawing on the uploaded manual page 13**.

### Electrical bus and connector

**O20\_V1.0\_PAB20251123 multipin connector**, illustrated on original PDF page 14. Not XT30 (2+2). Use OEM orientation/pin diagram and a **USB-to-CAN-FD** adapter. Do not infer mating connector from L-series hands.

**Manufacturer-model note:** The O20 manual documents a Windows host program **`020_hand_ui.exe`** and separate position, temperature, current and tactile curves. It shows CAN button changing to green on connection; Read Version Information does not send motion.

## Software and development resources

| Resource                                                                                                                              | Verified purpose                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| [Current seven-model Linkerbot ROS 2 driver](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                   | ROS 2 Humble/Jazzy driver and read-only state topics; **native CAN/CAN FD** model entry |
| [ROS 2 model compatibility matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) | Confirms active joint count, bus and per-model capability differences                   |
| [LinkerHand Python SDK](https://github.com/linker-bot/linkerhand-python-sdk)                                                          | Firmware/adapter-specific Python examples; verify variant and driver before using       |
| [Complete O20 V1.2 manual and PDF downloads](source-library/complete-o20.md)                                                          | Exact manual hardware, mechanical dimensions, connector and installation source         |

**Version constraint:** a current GitHub model entry does not certify a purchased RS485 variant for a CAN-only launch. Check model/device capabilities, firmware and the installed transport. Never run sample code that writes angles or torque as the first device check.

## Getting started

### Prerequisites

Physical hand and variant labeling; correct original or manufacturer-approved adapter; matching CAN/CAN FD/RS485 interface; secure fixture; model manual. For first read-only software use, a compatible Windows host utility or ROS 2 environment must be available as appropriate.

### First working result

1. First identify model/body/serial, cable and the unique **O20 multipin connector**, and obtain the OEM-approved 24 V adapter and USB-to-CAN-FD tool. Because the OpenELAB store match is **unverified**, do not power an unidentified unit. After exact hardware/adapter verification by the supplier, run the delivered Windows **`020_hand_ui.exe`**, select the correct CAN-FD module, click **Connect CAN** then **Read Version Information**. Avoid zero/reset, sliders, finger dance, table execution or overcurrent/calibration writes.
2. Record current model, side, revision, bus, installed host utility/SDK commit and relevant status values. Do **not** command finger positions, resets, gains or torque until identity and safety are confirmed.

**Expected result:** A verified O20 identity, controller version/ID and read-only status; no motion.

**If the check fails:** If the CAN connection remains black/not connected, inspect USB-to-CAN-FD driver and actual physical connector/controller ID; do not use an L20 ordinary CAN adapter or modify calibration/overcurrent limits.

### Next safe experiment

With device and software explicitly approved, log a sequence of **read-only** state observations and compare expected joint count/units, metadata validity and sample freshness. Motion/grasping is a separate supervised step after confirming range, direction, force and stop behavior.

## Troubleshooting and FAQs

**A device appears but the reported joint count differs.** Confirm the exact model, model discovery, loaded SDK feature definition and **active DoF versus passive mechanical joints**. Do not pad/trim a control vector to guess joint mapping.

**The device does not connect or respond.** If the CAN connection remains black/not connected, inspect USB-to-CAN-FD driver and actual physical connector/controller ID; do not use an L20 ordinary CAN adapter or modify calibration/overcurrent limits.

**Can I use another Linkerbot model's power cable or protocol?** No. This model's documented electrical interface is **CAN FD with O20\_V1.0\_PAB20251123 connector**; use its own labeled cable, supply and OEM connector drawing.

**Can I assume tactile data is present?** 6×12 pressure array, reported **30 Hz refresh**; do NOT confuse with the 1000 Hz bus communication frequency. Validate sensor options and returned data before relying on tactile feedback.

## Downloads and technical documents

| Resource                        | Scope and link                                                                                                                               |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Original product manual         | [Complete O20 V1.2 manual and PDF downloads](source-library/complete-o20.md)                                                                 |
| Manufacturer ROS 2 model matrix | [Model definitions and control semantics](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md) |
| Manufacturer current ROS 2 SDK  | [Installation and examples](https://github.com/linker-bot/linkerbot-hand-ros2-sdk)                                                           |
| Manufacturer Python SDK         | [Source and model examples](https://github.com/linker-bot/linkerhand-python-sdk)                                                             |
| OpenELAB product/SKU            | No matching .io catalog product verified; match pending                                                                                      |

**Physical drawings:** preserve the flange/connector images in the existing manual; do not recreate dimensioned pinout diagrams from photos.

## References and validation

* LINKERBOT / Lingxin Qiaoshou, _O20 Product Manual_, **V1.2 (2026-06-05; filename says V10)**, provided upload, reviewed 2026-11-21.
* [Current official Linkerbot ROS 2 model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md), reviewed 2026-11-21.
* OpenELAB .io product catalog search, 2026-11-21: **no product/SKU match** for this model.

**Documentation review:** completed for provided revision; **software execution:** not run; **hardware test:** not run. **Identity block:** store SKU and actual adapter/connector pairing unresolved—physical first result must await confirmation.
