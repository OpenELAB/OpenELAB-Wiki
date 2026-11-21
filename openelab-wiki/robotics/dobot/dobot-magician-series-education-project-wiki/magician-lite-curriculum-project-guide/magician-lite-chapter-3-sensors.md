---
description: >-
  Source-derived DOBOT Magician Lite education lesson: I/O, Sensor Exploration
  and Color-Sorting. Equipment, model limitations and validated-first-result
  pathway.
---

# DOBOT Magician Lite — I/O, Sensor Exploration and Color-Sorting

{% hint style="info" %}
[**View DOBOT Magician Lite on OpenELAB**](https://openelab.io/products/dobot-magician-lite-education-robot)

**Model:** DOBOT Magician Lite · **SKU:** `DOBOT-1100000080` · **Scope:** Optional Magic Box, AI camera, sensor kit, conveyor and rail are not guaranteed in the bare retail unit
{% endhint %}

[DOBOT Magician Lite course guide](./) · [Magician Series index](../) · [Existing user guide](../../dobot-magician-lite-user-guide.md)

### Product overview

**Chapter 3 (pp. 111–172) of Lite V1.1.** I/O, Sensor Exploration and Color-Sorting is a source-derived teaching tutorial for **DOBOT Magician Lite**. It preserves the workbook's concepts while separating classroom planning, safe read-only setup and optional physical robotics. Do not apply another Magician-family model's points, voltage, connector or tool command.

### Applications

* Input/output introduction and optional Sensor Kit exploration
* Color sensor through Magic Box for object classes
* Mini-conveyor color sorting and servo feeder exercises

### Specifications

| Integration parameter | Value / conditions                                                                                        |
| --------------------- | --------------------------------------------------------------------------------------------------------- |
| Robot / power         | Four-axis, 250 g maximum payload, 340 mm reach, ±0.2 mm repeatability, 12 VDC/5 A original adapter        |
| Development software  | DobotLab Teaching & Playback / DobotBlock / optional Magic Box MicroPython                                |
| Lesson equipment      | Lite Sensor Kit/Magic Box; optional color sensor, mini conveyor and servo feeder as described in workbook |
| Course version        | Chapter 3 (pp. 111–172) of Lite V1.1                                                                      |
| Physical motion       | Instructor-supervised only; complete model-specific manual and stop procedure before use                  |

### Hardware and connections

1. Inspect the model label, 12 VDC/5 A original supply, USB cable and purchased kit contents before energizing.
2. Identify all optional items required for this specific lesson: **Lite Sensor Kit/Magic Box; optional color sensor, mini conveyor and servo feeder as described in workbook**. If absent, use the offline alternative rather than claiming the physical experiment worked.
3. Follow [the matching DOBOT Magician Lite user manual](../../dobot-magician-lite-user-guide.md) for end-effector mounting, stop controls, homing and operating range. No pinout or power wiring is inferred from the workbook's pictures.
4. Secure the arm and prevent people, cables and tools from entering its reach envelope. Never automatically repeat an unverified trajectory or bypass a hardware stop.
5. Record actual robot firmware, software, tool, zero/home pose and units for each run.

### Software and development resources

* [Source: Chapter 3 (pp. 111–172) of Lite V1.1](https://drive.google.com/file/d/1QIVA1S21EIHV1TOdHESgUXxE8Xso_kcP/view) — original instruction, printable lesson/experiment text and assessment content.
* [DOBOT Magician Lite User Guide](../../dobot-magician-lite-user-guide.md) — authority for exact power, end-effector and hardware control.
* [Magician Series curriculum comparison](../) — tool/edition differences.
* **Note:** Older course materials may reference DobotLab, DobotStudio, DobotBlock and Teach & Playback versions that differ from the installed software. Match the current interface to its manufacturer's manual instead of guessing menu names.

### Getting started

#### Prerequisites

Confirm source worksheet, actual purchased model and available tools; arrange a safe instructor-supervised workspace. Start with dry-run, paper or screen-based planning wherever the workbook requires unavailable peripherals.

#### First working result

1. Prepare three synthetic input observations (color A, color B, missing/ambiguous). Use a reject-by-default DobotBlock decision tree to select an output bin only for a validated class; leave all motion blocks disconnected while checking classification.
2. Save the project/worksheet and include the model, software version, measured or synthetic input values and any observed fault.
3. Compare the result against the source-defined task, then stop safely before further extension.

**Expected result:** Two accepted class outcomes and an UNKNOWN reject path, with an accessory inventory list.

#### Extension and assessment

After instructor approval, identify a physical sensor value and repeat the classification test in a stationary setup before linking it to a pick/place job. Assessment: provide a labeled workflow, input/output table, one result screenshot and a paragraph describing the hardware prerequisites and failure handling.

### Troubleshooting and FAQs

**What if the first checkpoint fails?** If the input signal is absent, first check whether the Sensor Kit or Magic Box was actually purchased; then use the **Lite** hardware guide for input voltage and port mapping, not 12 V motor supply pins..

**Can this lesson run on a bare DOBOT Magician Lite?** Only its screen/paper or included-tool parts can. The lesson's required items are enumerated above; check the selected bundle and manual before physical extensions.

**What should be done after a motion or electrical fault?** Stop with the verified physical control, power down as prescribed, document controller alarm/status, and obtain qualified instruction before retrying. Do not bypass a safety mechanism.

### Downloads and technical documents

| Resource                                                                                                       | Use                                        |
| -------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Chapter 3 (pp. 111–172) of Lite V1.1](https://drive.google.com/file/d/1QIVA1S21EIHV1TOdHESgUXxE8Xso_kcP/view) | Source lesson, worksheets and activities   |
| [DOBOT Magician Lite user guide](../../dobot-magician-lite-user-guide.md)                                      | Hardware and setup instructions            |
| [Exact OpenELAB listing](https://openelab.io/products/dobot-magician-lite-education-robot)                     | Sold model and included/optional equipment |

### References and validation

* Chapter 3 (pp. 111–172) of Lite V1.1, retrieved from user-supplied Google Drive curriculum collections 2026-11-21.
* [OpenELAB DOBOT Magician Lite listing](https://openelab.io/products/dobot-magician-lite-education-robot), checked 2026-11-21.
* [Previously published model-specific technical user manual](../../dobot-magician-lite-user-guide.md), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware validation:** not run. The result above is the anticipated check, not observed data. Do not treat proposed software decisions as industrial/medical safety functions.
