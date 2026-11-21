---
description: >-
  Source-derived DOBOT Magician education lesson: Conveyor, Sliding Rail, Stack
  Light and Work-Cell Design. Equipment, model limitations and
  validated-first-result pathway.
---

# DOBOT Magician — Conveyor, Sliding Rail, Stack Light and Work-Cell Design

{% hint style="info" %}
[**View DOBOT Magician on OpenELAB**](https://openelab.io/products/dobot-magician-education-robot-arm)

**Model:** DOBOT Magician · **SKU:** `DOBOT-1100000015` · **Scope:** Basic/Educational Plans; additional wireless, laser and joystick accessories require Educational Plan
{% endhint %}

[DOBOT Magician course guide](./) · [Magician Series index](../) · [Existing user guide](../../dobot-magician-user-guide.md)

### Product overview

**Chapter 4 (pp. 237–284) and printed resources (pp. 285–311) of Magician V3.2.** Conveyor, Sliding Rail, Stack Light and Work-Cell Design is a source-derived teaching tutorial for **DOBOT Magician**. It preserves the workbook's concepts while separating classroom planning, safe read-only setup and optional physical robotics. Do not apply another Magician-family model's points, voltage, connector or tool command.

### Applications

* Mini-conveyor start/stop and material motion
* Linear slidebase pick-and-place and expanded workspace
* Stack light/AI camera examples and complete work-cell design with and without a microcontroller

### Specifications

| Integration parameter | Value / conditions                                                                                                                |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Robot / power         | Four-axis, 500 g maximum payload, 320 mm reach, ±0.2 mm repeatability, 12 VDC/7 A original adapter                                |
| Development software  | DobotLab Teaching & Playback / DobotBlock; older DobotStudio only when compatible                                                 |
| Lesson equipment      | Conveyor, sliding rail, Magic Box/sensor kit, stack light or vision kit as appropriate; do not assume these on the Basic Plan arm |
| Course version        | Chapter 4 (pp. 237–284) and printed resources (pp. 285–311) of Magician V3.2                                                      |
| Physical motion       | Instructor-supervised only; complete model-specific manual and stop procedure before use                                          |

### Hardware and connections

1. Inspect the model label, 12 VDC/7 A original supply, USB cable and purchased kit contents before energizing.
2. Identify all optional items required for this specific lesson: **Conveyor, sliding rail, Magic Box/sensor kit, stack light or vision kit as appropriate; do not assume these on the Basic Plan arm**. If absent, use the offline alternative rather than claiming the physical experiment worked.
3. Follow [the matching DOBOT Magician user manual](../../dobot-magician-user-guide.md) for end-effector mounting, stop controls, homing and operating range. No pinout or power wiring is inferred from the workbook's pictures.
4. Secure the arm and prevent people, cables and tools from entering its reach envelope. Never automatically repeat an unverified trajectory or bypass a hardware stop.
5. Record actual robot firmware, software, tool, zero/home pose and units for each run.

### Software and development resources

* [Source: Chapter 4 (pp. 237–284) and printed resources (pp. 285–311) of Magician V3.2](https://drive.google.com/file/d/1wfgDZ2CETKxll6oDhMkfIFI5Yn5p03-9/view) — original instruction, printable lesson/experiment text and assessment content.
* [DOBOT Magician User Guide](../../dobot-magician-user-guide.md) — authority for exact power, end-effector and hardware control.
* [Magician Series curriculum comparison](../) — tool/edition differences.
* **Note:** Older course materials may reference DobotLab, DobotStudio, DobotBlock and Teach & Playback versions that differ from the installed software. Match the current interface to its manufacturer's manual instead of guessing menu names.

### Getting started

#### Prerequisites

Confirm source worksheet, actual purchased model and available tools; arrange a safe instructor-supervised workspace. Start with dry-run, paper or screen-based planning wherever the workbook requires unavailable peripherals.

#### First working result

1. Draw a tabletop work-cell layout with source tray, destination bin, robot exclusion zone, optional conveyor boundary and an E-stop. Prepare a sequencing table for the controller: conveyor OFF → object detected → robot ready → pick/place cycle → conveyor ON. Reject any state in which conveyor and robot conflict.
2. Save the project/worksheet and include the model, software version, measured or synthetic input values and any observed fault.
3. Compare the result against the source-defined task, then stop safely before further extension.

**Expected result:** A grounded work-cell layout and interface/stop-state specification with no automatic movement.

#### Extension and assessment

Make a bill of materials separating Basic Plan contents from required conveyor/rail/vision/sensor accessories; test one device at a time. Assessment: provide a labeled workflow, input/output table, one result screenshot and a paragraph describing the hardware prerequisites and failure handling.

### Troubleshooting and FAQs

**What if the first checkpoint fails?** If the robot cannot reach the conveyor station, measure the actual Magician 320 mm working reach and tool offset; do not copy an unrelated rail coordinate or move the secured robot while powered.

**Can this lesson run on a bare DOBOT Magician?** Only its screen/paper or included-tool parts can. The lesson's required items are enumerated above; check the selected bundle and manual before physical extensions.

**What should be done after a motion or electrical fault?** Stop with the verified physical control, power down as prescribed, document controller alarm/status, and obtain qualified instruction before retrying. Do not bypass a safety mechanism.

### Downloads and technical documents

| Resource                                                                                                                                               | Use                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| [Chapter 4 (pp. 237–284) and printed resources (pp. 285–311) of Magician V3.2](https://drive.google.com/file/d/1wfgDZ2CETKxll6oDhMkfIFI5Yn5p03-9/view) | Source lesson, worksheets and activities   |
| [DOBOT Magician user guide](../../dobot-magician-user-guide.md)                                                                                        | Hardware and setup instructions            |
| [Exact OpenELAB listing](https://openelab.io/products/dobot-magician-education-robot-arm)                                                              | Sold model and included/optional equipment |

### References and validation

* Chapter 4 (pp. 237–284) and printed resources (pp. 285–311) of Magician V3.2, retrieved from user-supplied Google Drive curriculum collections 2026-11-21.
* [OpenELAB DOBOT Magician listing](https://openelab.io/products/dobot-magician-education-robot-arm), checked 2026-11-21.
* [Previously published model-specific technical user manual](../../dobot-magician-user-guide.md), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware validation:** not run. The result above is the anticipated check, not observed data. Do not treat proposed software decisions as industrial/medical safety functions.
