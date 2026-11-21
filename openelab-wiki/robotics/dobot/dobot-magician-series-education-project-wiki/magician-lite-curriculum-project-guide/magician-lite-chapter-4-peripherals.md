---
description: >-
  Source-derived DOBOT Magician Lite education lesson: Mini Conveyor, Linear
  Rail, AI Camera and Work Cells. Equipment, model limitations and
  validated-first-result pathway.
---

# DOBOT Magician Lite — Mini Conveyor, Linear Rail, AI Camera and Work Cells

{% hint style="info" %}
[**View DOBOT Magician Lite on OpenELAB**](https://openelab.io/products/dobot-magician-lite-education-robot)

**Model:** DOBOT Magician Lite · **SKU:** `DOBOT-1100000080` · **Scope:** Optional Magic Box, AI camera, sensor kit, conveyor and rail are not guaranteed in the bare retail unit
{% endhint %}

[DOBOT Magician Lite course guide](./) · [Magician Series index](../) · [Existing user guide](../../dobot-magician-lite-user-guide.md)

### Product overview

**Chapter 4 (pp. 173–217) plus printed field diagrams of Lite V1.1.** Mini Conveyor, Linear Rail, AI Camera and Work Cells is a source-derived teaching tutorial for **DOBOT Magician Lite**. It preserves the workbook's concepts while separating classroom planning, safe read-only setup and optional physical robotics. Do not apply another Magician-family model's points, voltage, connector or tool command.

### Applications

* Start/stop mini conveyor and slide-rail pick/place
* AI camera demonstration and Magic Box stack light
* Guided and open-ended robotic work-cell design

### Specifications

| Integration parameter | Value / conditions                                                                                                                |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Robot / power         | Four-axis, 250 g maximum payload, 340 mm reach, ±0.2 mm repeatability, 12 VDC/5 A original adapter                                |
| Development software  | DobotLab Teaching & Playback / DobotBlock / optional Magic Box MicroPython                                                        |
| Lesson equipment      | Optional compatible conveyor, slide rail, AI camera, Magic Box and stack light; base Lite alone does not supply these accessories |
| Course version        | Chapter 4 (pp. 173–217) plus printed field diagrams of Lite V1.1                                                                  |
| Physical motion       | Instructor-supervised only; complete model-specific manual and stop procedure before use                                          |

### Hardware and connections

1. Inspect the model label, 12 VDC/5 A original supply, USB cable and purchased kit contents before energizing.
2. Identify all optional items required for this specific lesson: **Optional compatible conveyor, slide rail, AI camera, Magic Box and stack light; base Lite alone does not supply these accessories**. If absent, use the offline alternative rather than claiming the physical experiment worked.
3. Follow [the matching DOBOT Magician Lite user manual](../../dobot-magician-lite-user-guide.md) for end-effector mounting, stop controls, homing and operating range. No pinout or power wiring is inferred from the workbook's pictures.
4. Secure the arm and prevent people, cables and tools from entering its reach envelope. Never automatically repeat an unverified trajectory or bypass a hardware stop.
5. Record actual robot firmware, software, tool, zero/home pose and units for each run.

### Software and development resources

* [Source: Chapter 4 (pp. 173–217) plus printed field diagrams of Lite V1.1](https://drive.google.com/file/d/1QIVA1S21EIHV1TOdHESgUXxE8Xso_kcP/view) — original instruction, printable lesson/experiment text and assessment content.
* [DOBOT Magician Lite User Guide](../../dobot-magician-lite-user-guide.md) — authority for exact power, end-effector and hardware control.
* [Magician Series curriculum comparison](../) — tool/edition differences.
* **Note:** Older course materials may reference DobotLab, DobotStudio, DobotBlock and Teach & Playback versions that differ from the installed software. Match the current interface to its manufacturer's manual instead of guessing menu names.

### Getting started

#### Prerequisites

Confirm source worksheet, actual purchased model and available tools; arrange a safe instructor-supervised workspace. Start with dry-run, paper or screen-based planning wherever the workbook requires unavailable peripherals.

#### First working result

1. Draw a field template identifying Lite base position, travel/arm envelope, source/target points, stack light states and stop area. Define an offline sequence where the conveyor halts before every robot pick and restarts only after the arm clears the transfer zone.
2. Save the project/worksheet and include the model, software version, measured or synthetic input values and any observed fault.
3. Compare the result against the source-defined task, then stop safely before further extension.

**Expected result:** Layout diagram and offline verified interlock-state table, with listed accessory BOM.

#### Extension and assessment

Produce an instructor-reviewed bill of materials and a list of separately tested checkpoints for each peripheral. Assessment: provide a labeled workflow, input/output table, one result screenshot and a paragraph describing the hardware prerequisites and failure handling.

### Troubleshooting and FAQs

**What if the first checkpoint fails?** If the rail or camera cannot be connected, check exact kit compatibility, interface type, supply and mounting before applying any connector or calibration data.

**Can this lesson run on a bare DOBOT Magician Lite?** Only its screen/paper or included-tool parts can. The lesson's required items are enumerated above; check the selected bundle and manual before physical extensions.

**What should be done after a motion or electrical fault?** Stop with the verified physical control, power down as prescribed, document controller alarm/status, and obtain qualified instruction before retrying. Do not bypass a safety mechanism.

### Downloads and technical documents

| Resource                                                                                                                                   | Use                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| [Chapter 4 (pp. 173–217) plus printed field diagrams of Lite V1.1](https://drive.google.com/file/d/1QIVA1S21EIHV1TOdHESgUXxE8Xso_kcP/view) | Source lesson, worksheets and activities   |
| [DOBOT Magician Lite user guide](../../dobot-magician-lite-user-guide.md)                                                                  | Hardware and setup instructions            |
| [Exact OpenELAB listing](https://openelab.io/products/dobot-magician-lite-education-robot)                                                 | Sold model and included/optional equipment |

### References and validation

* Chapter 4 (pp. 173–217) plus printed field diagrams of Lite V1.1, retrieved from user-supplied Google Drive curriculum collections 2026-11-21.
* [OpenELAB DOBOT Magician Lite listing](https://openelab.io/products/dobot-magician-lite-education-robot), checked 2026-11-21.
* [Previously published model-specific technical user manual](../../dobot-magician-lite-user-guide.md), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware validation:** not run. The result above is the anticipated check, not observed data. Do not treat proposed software decisions as industrial/medical safety functions.
