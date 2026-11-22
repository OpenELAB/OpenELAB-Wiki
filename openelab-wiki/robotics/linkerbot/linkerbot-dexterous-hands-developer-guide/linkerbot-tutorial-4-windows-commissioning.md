---
description: >-
  Windows UI first-connection and read-only version/status for L20 Lite, O20,
  O30 and L30 safety limitations.
---

# Tutorial 4 — LINKERBOT Windows Host Software Commissioning

{% hint style="info" %}
[**L6**](https://openelab.io/products/linker-hand-linkerbot-l6-11) · [**L20 Lite**](https://openelab.io/products/linker-hand-linkerbot-l20-lite) · [**L20**](https://openelab.io/products/linker-hand-linkerbot-l20-21) · [**L30 Tendon**](https://openelab.io/products/linker-hand-linkerbot-l30-l30) · [**O6**](https://openelab.io/products/linker-hand-linkerbot-o6-11) — OpenELAB product links

**Scope:** Windows tools described in the uploaded model manuals, not a generic multi-model motion application.
{% endhint %}

[**Complete seven-manual library — all 137 original PDF pages and downloads**](../source-library/)

[LINKERBOT developer series](./)

## Product overview

The supplied manuals describe **several different Windows host utilities**. A technician must select the one that corresponds to the exact hand, bus, adapter and firmware. This tutorial stops at **read-only connection and version/status information** and does not authorize slider commands, position reset, finger-dance routines, calibration, torque changes or firmware updates.

## Applications

* Connect and inspect an L20 Lite using CAN Bridge and its browser Dashboard.
* Read O20/O30 identity and firmware information using their separate CAN-FD graphical tools.
* Document software package/version differences instead of copying a similarly named hand's GUI sequence.

## Specifications

| Model             | Manual-described Windows application                              | First non-moving observation                                                     |
| ----------------- | ----------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| L20 Lite V1.0     | `can_bridge.exe` and `dashboard.exe` at **http://localhost:9090** | Online/offline, port, model and side                                             |
| O20 V1.2          | `020_hand_ui.exe`                                                 | CAN device connection and **Read Version Information**                           |
| O30 V1.0          | `O30_hand_ui.exe`                                                 | CAN connection and **Read Version Information**                                  |
| L30 Standard V1.3 | `dexterous_hand_controller.exe`                                   | **Electrical connection blocked** pending voltage and bus discrepancy resolution |
| L6 / O6 / L20     | USB-to-CAN and SDKs documented                                    | Do **not** assume the L20 Lite/O20/O30 software is model-compatible              |

**The uploaded PDFs do not contain Windows installer binaries.** Obtain matching manufacturer packages and verify software authenticity and firmware compatibility.

## Hardware and connections

1. Identify the hand body, left/right variant, electrical adapter and exact model connector with the source drawing; use only the approved power supply.
2. Secure the mounting flange and clear the hand's pinch zone before powering any approved unit.
3. **L20 Lite:** its manual calls for the PEAK USB-to-CAN driver on Windows; its bridge process must be restarted after changing a CAN device connection.
4. **O20 and O30:** the source manuals use USB-to-CAN-FD adapters and their distinct multipin cable/connector designs; neither is interchangeable with a generic XT30 cable.
5. **L30:** do not perform powered commissioning while the uploaded manual's 24 V/CAN-FD requirements conflict with the store's 12 V/CAN/RS485 information.

## Software and development resources

* [Existing L20 Lite User Manual](../linker-hand-l20-lite-product-manual.md): PEAK driver, `config.toml`, CAN Bridge and Dashboard.
* [Complete O20 supplied OEM Manual V1.2](../source-library/complete-o20.md): CAN-FD connection, `020_hand_ui.exe`, version/ID, graphical curves and original command descriptions, including downloadable PDF parts.
* [Existing O30 OEM Manual](../linker-hand-o30-product-manual.md): `O30_hand_ui.exe`, connected CAN status and read-version action.
* [Existing L30 Standard OEM Manual](../linker-hand-l30-standard-edition-product-manual.md): original `dexterous_hand_controller.exe` workflow, subject to blocked power pairing.
* [Current ROS 2 SDK](https://github.com/linker-bot/linkerbot-hand-ros2-sdk): alternative Linux read-only workflow.

## Getting started

### First working result: confirm model and software status without motion

1. **L20 Lite:** after verifying its 24 V/adapter and CAN variant, install the manufacturer-supported PEAK driver on Windows. Set the matching interface(s) in `can_bridge_dashboard/config.toml`, for example `can_interface = ["can1"]` for one device if that is the actual interface. Start the included **`can_bridge.exe`**, then **`dashboard.exe`**, and open **http://localhost:9090**. Observe the online indicator, side and model. Do not use sliders or preset movements.
2. **O20:** only after exact power and unique CAN-FD connector are approved, launch manufacturer **`020_hand_ui.exe`**, use **Connect CAN**, and click **Read Version Information**. Its manual describes a CAN button changing from black to green after successful connection. Record the actual device firmware/ID.
3. **O30:** only after confirming the correct O30 connector and adapter, launch **`O30_hand_ui.exe`**, choose the correct CAN connection and click **Read Version Information**. Log the real response fields rather than copying screenshot placeholders.
4. **L30:** complete a documentation-only inventory of supply label, bus/PCB revision, connector and store SKU; **do not run the host tool against powered hardware** until matching vendor documentation is obtained.
5. Stop after identity/status verification; **do not** press Run Table, Finger Dance, Reset/Zero, Calibration, Overcurrent/Deviation settings, firmware upgrade or motor-control sliders.

**Expected result:** the real program identifies the matching hand and provides online/version data—or a clearly documented **blocked** status if the identity/electrical prerequisite is unresolved.

## Troubleshooting and FAQs

**L20 Lite Dashboard does not open.** Check that the CAN Bridge service is running and inspect `can_bridge.log`, driver setup, configured interface names and local port 9090. The manual says to restart the bridge after a Windows adapter is unplugged/replugged.

**O20/O30 CAN button does not connect.** Check the USB-to-CAN-FD adapter, actual device power, matching unique connector, controller ID and vendor driver; avoid changing motor parameters to diagnose a missing link.

**Is the software Stop button equivalent to a rated E-stop?** No such independent safety certification is established in these manuals; keep an approved physical disconnect/stop arrangement.

## Downloads and technical documents

* [L20 Lite manual and commissioning screenshots](../linker-hand-l20-lite-product-manual.md).
* [O30 manual and commissioning screenshots](../linker-hand-o30-product-manual.md).
* [L30 Standard manual and program description](../linker-hand-l30-standard-edition-product-manual.md).
* [Official current ROS 2 SDK](https://github.com/linker-bot/linkerbot-hand-ros2-sdk).

## References and validation

* LINKERBOT product manuals: L20 Lite V1.0, O20 V1.2, O30 V1.0, L30 Standard V1.3, uploaded by OpenELAB and reviewed 2026-11-21.
* [Manufacturer current ROS 2 SDK](https://github.com/linker-bot/linkerbot-hand-ros2-sdk), checked 2026-11-21.

**Documentation:** reviewed. **Software execution:** not run. **Hardware validation:** not run. Exact electrical and SKU gaps are explicitly blocking.

## Complete source coverage and revision checkpoints

| Model / revision                               | Complete supplied reference                            | Key interpretation                                          |
| ---------------------------------------------- | ------------------------------------------------------ | ----------------------------------------------------------- |
| L6 V1.4 · 2026-05-18                           | [15 PDF pages](../source-library/complete-l6.md)       | LED and speed-unit note                                     |
| L20 Lite V1.0 · 2025-09-11                     | [19 PDF pages](../source-library/complete-l20-lite.md) | 10 active / 20 physical joints; optional sensor variants    |
| L20 V1.3 · 2026-08-04                          | [14 PDF pages](../source-library/complete-l20.md)      | 24–48 V table / 24 V connector; V1.3 joint angles           |
| L30 Standard (tendon-driven) V1.3 · 2025-10-27 | [17 PDF pages](../source-library/complete-l30.md)      | Tendon/wrist model; voltage, bus and rate conflicts         |
| O6 V1.4 · 2026-07-21                           | [17 PDF pages](../source-library/complete-o6.md)       | Optional 4×10 tactile; actual protocol option               |
| O20 V1.2 · 2026-06-05                          | [30 PDF pages](../source-library/complete-o20.md)      | 30 Hz tactile / 1000 Hz communication; unique connector     |
| O30 V1.0 · 2026-07-10                          | [25 PDF pages](../source-library/complete-o30.md)      | 6×11 pressure array; unique connector and descriptor layout |

### Windows control reference and recovery boundaries

| Tool / model          | Read or inspect                                                                     | Commands requiring a separate cleared motion/configuration procedure                                              |
| --------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| L20 Lite Dashboard    | Port, hand type, online/offline, logs, returned sensor data                         | Global joint/palm poses, speed/torque, reset, presets and animations                                              |
| O20 `020_hand_ui.exe` | CAN connection, version/ID, temperature/current/pressure queries, returned position | Zero/reset, sliders, Run Table, Finger Dance, deviation/overcurrent writes, calibration, device-information edits |
| O30 `O30_hand_ui.exe` | CAN connection, version/ID, curves and calibration-status read                      | Sliders, zero/reset, Run Table, Finger Dance, ID changes and Re-calibrate                                         |
| L30 controller        | Documentation review while electrical match is unresolved                           | Every powered connection, position/torque write and sequence execution remains blocked for an unconfirmed variant |

O20 sequence rows have **18 columns** (number + 16 joints + interval); O30 rows have **22** (number + 20 joints + interval). Their whole-table default interval is **1000 ms**. These files are not interchangeable. L30’s sequence editor interval is in seconds. Stop is application-specific: stopping plot queries, a finger dance and a table loop are distinct actions and are not proof of safety-rated torque removal.

O20 parameter Send may submit default values for blank fields. Do not explore a settings panel by sending empty parameters. O30 ID changes use decimal 0–1022 and take effect after restart; record the current ID before any approved change. For a failed connection, gather adapter enumeration, power/cable identity, version information and logs. Do not treat calibration, firmware upgrade or factory resets as generic recovery actions.

The O20/O30 manuals describe driver-free use for their specific supplied adapter; the PEAK installation described for L20 Lite/O6 is a different adapter workflow. Executable names and screenshot release dates are package identifiers, not evidence that a binary was downloaded or run during this review.

Current software reference: [ROS 2 source at `8d56b3355d2c`](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/8d56b3355d2cfcd90e4e3c6b377ebceb7a5c09ac/README.md), reviewed 22 November 2026. This is a documentation review; **software execution and hardware validation were not run**.
