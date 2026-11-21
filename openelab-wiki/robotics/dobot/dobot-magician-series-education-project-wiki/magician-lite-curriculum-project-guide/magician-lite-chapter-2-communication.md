---
description: >-
  Source-derived DOBOT Magician Lite education lesson: DobotBlock Communication
  and Magic Box Handshaking. Equipment, model limitations and
  validated-first-result pathway.
---

# DOBOT Magician Lite — DobotBlock Communication and Magic Box Handshaking

{% hint style="info" %}
[**View DOBOT Magician Lite on OpenELAB**](https://openelab.io/products/dobot-magician-lite-education-robot)

**Model:** DOBOT Magician Lite · **SKU:** `DOBOT-1100000080` · **Scope:** Optional Magic Box, AI camera, sensor kit, conveyor and rail are not guaranteed in the bare retail unit
{% endhint %}

[DOBOT Magician Lite course guide](./) · [Magician Series index](../) · [Existing user guide](../../dobot-magician-lite-user-guide.md)

### Product overview

**Chapter 2 (pp. 82–110) of Lite V1.1 (2024).** DobotBlock Communication and Magic Box Handshaking is a source-derived teaching tutorial for **DOBOT Magician Lite**. It preserves the workbook's concepts while separating classroom planning, safe read-only setup and optional physical robotics. Do not apply another Magician-family model's points, voltage, connector or tool command.

### Applications

* Two Magician Lite units and robot-to-robot internal handshaking
* Magic Box to Magic Box Bluetooth handshaking
* Magician Lite and Magic Box cooperative pick/place

### Specifications

| Integration parameter | Value / conditions                                                                                                     |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Robot / power         | Four-axis, 250 g maximum payload, 340 mm reach, ±0.2 mm repeatability, 12 VDC/5 A original adapter                     |
| Development software  | DobotLab Teaching & Playback / DobotBlock / optional Magic Box MicroPython                                             |
| Lesson equipment      | At least one Lite and compatible optional Magic Box; two robots or two Magic Boxes for peer handshaking, as applicable |
| Course version        | Chapter 2 (pp. 82–110) of Lite V1.1 (2024)                                                                             |
| Physical motion       | Instructor-supervised only; complete model-specific manual and stop procedure before use                               |

### Hardware and connections

1. Inspect the model label, 12 VDC/5 A original supply, USB cable and purchased kit contents before energizing.
2. Identify all optional items required for this specific lesson: **At least one Lite and compatible optional Magic Box; two robots or two Magic Boxes for peer handshaking, as applicable**. If absent, use the offline alternative rather than claiming the physical experiment worked.
3. Follow [the matching DOBOT Magician Lite user manual](../../dobot-magician-lite-user-guide.md) for end-effector mounting, stop controls, homing and operating range. No pinout or power wiring is inferred from the workbook's pictures.
4. Secure the arm and prevent people, cables and tools from entering its reach envelope. Never automatically repeat an unverified trajectory or bypass a hardware stop.
5. Record actual robot firmware, software, tool, zero/home pose and units for each run.

### Software and development resources

* [Source: Chapter 2 (pp. 82–110) of Lite V1.1 (2024)](https://drive.google.com/file/d/1QIVA1S21EIHV1TOdHESgUXxE8Xso_kcP/view) — original instruction, printable lesson/experiment text and assessment content.
* [DOBOT Magician Lite User Guide](../../dobot-magician-lite-user-guide.md) — authority for exact power, end-effector and hardware control.
* [Magician Series curriculum comparison](../) — tool/edition differences.
* **Note:** Older course materials may reference DobotLab, DobotStudio, DobotBlock and Teach & Playback versions that differ from the installed software. Match the current interface to its manufacturer's manual instead of guessing menu names.

### Getting started

#### Prerequisites

Confirm source worksheet, actual purchased model and available tools; arrange a safe instructor-supervised workspace. Start with dry-run, paper or screen-based planning wherever the workbook requires unavailable peripherals.

#### First working result

1. Write a three-signal peer protocol on a DobotBlock worksheet: REQUEST, ACK, DONE. Simulate a missing ACK and have the state machine stop without performing a pick. Use Bluetooth only after pairing and confirming correct devices.
2. Save the project/worksheet and include the model, software version, measured or synthetic input values and any observed fault.
3. Compare the result against the source-defined task, then stop safely before further extension.

**Expected result:** A sequence diagram with timeout/retry outcomes and no undesired robot motion.

#### Extension and assessment

Define message events and on-screen log fields for request, success, timeout and reset; record actual messages only after verifying the hardware. Assessment: provide a labeled workflow, input/output table, one result screenshot and a paragraph describing the hardware prerequisites and failure handling.

### Troubleshooting and FAQs

**What if the first checkpoint fails?** When pairing fails, confirm that the actual Magic Box/Bluetooth modules are installed, supported, powered and matched to the relevant firmware. The Lite robot alone cannot complete a two-Magic-Box lesson..

**Can this lesson run on a bare DOBOT Magician Lite?** Only its screen/paper or included-tool parts can. The lesson's required items are enumerated above; check the selected bundle and manual before physical extensions.

**What should be done after a motion or electrical fault?** Stop with the verified physical control, power down as prescribed, document controller alarm/status, and obtain qualified instruction before retrying. Do not bypass a safety mechanism.

### Downloads and technical documents

| Resource                                                                                                             | Use                                        |
| -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Chapter 2 (pp. 82–110) of Lite V1.1 (2024)](https://drive.google.com/file/d/1QIVA1S21EIHV1TOdHESgUXxE8Xso_kcP/view) | Source lesson, worksheets and activities   |
| [DOBOT Magician Lite user guide](../../dobot-magician-lite-user-guide.md)                                            | Hardware and setup instructions            |
| [Exact OpenELAB listing](https://openelab.io/products/dobot-magician-lite-education-robot)                           | Sold model and included/optional equipment |

### References and validation

* Chapter 2 (pp. 82–110) of Lite V1.1 (2024), retrieved from user-supplied Google Drive curriculum collections 2026-11-21.
* [OpenELAB DOBOT Magician Lite listing](https://openelab.io/products/dobot-magician-lite-education-robot), checked 2026-11-21.
* [Previously published model-specific technical user manual](../../dobot-magician-lite-user-guide.md), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware validation:** not run. The result above is the anticipated check, not observed data. Do not treat proposed software decisions as industrial/medical safety functions.
