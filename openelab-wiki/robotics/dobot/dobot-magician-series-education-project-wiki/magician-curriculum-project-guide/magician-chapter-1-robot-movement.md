---
description: >-
  Source-derived DOBOT Magician education lesson: Robot Movement, Teach &
  Playback and Palletization. Equipment, model limitations and
  validated-first-result pathway.
---

# DOBOT Magician — Robot Movement, Teach & Playback and Palletization

{% hint style="info" %}
[**View DOBOT Magician on OpenELAB**](https://openelab.io/products/dobot-magician-education-robot-arm)

**Model:** DOBOT Magician · **SKU:** `DOBOT-1100000015` · **Scope:** Basic/Educational Plans; additional wireless, laser and joystick accessories require Educational Plan
{% endhint %}

[DOBOT Magician course guide](./) · [Magician Series index](../) · [Existing user guide](../../dobot-magician-user-guide.md)

### Product overview

**Chapter 1 (pp. 6–81) of Magician V3.2 (2024).** Robot Movement, Teach & Playback and Palletization is a source-derived teaching tutorial for **DOBOT Magician**. It preserves the workbook's concepts while separating classroom planning, safe read-only setup and optional physical robotics. Do not apply another Magician-family model's points, voltage, connector or tool command.

### Applications

* Joint and Cartesian motion; absolute vs relative coordinates; accuracy vs repeatability
* T\&P pen tracing of the word CIM, including above (AB) and at (AT) points
* Pick/place via T\&P and DobotBlock; jumps, loops, pallet routines and cube-matrix programming

### Specifications

| Integration parameter | Value / conditions                                                                                                          |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Robot / power         | Four-axis, 500 g maximum payload, 320 mm reach, ±0.2 mm repeatability, 12 VDC/7 A original adapter                          |
| Development software  | DobotLab Teaching & Playback / DobotBlock; older DobotStudio only when compatible                                           |
| Lesson equipment      | Original Magician + writing pen holder; for pick-and-place use its included gripper/vacuum tool and safe lightweight blocks |
| Course version        | Chapter 1 (pp. 6–81) of Magician V3.2 (2024)                                                                                |
| Physical motion       | Instructor-supervised only; complete model-specific manual and stop procedure before use                                    |

### Hardware and connections

1. Inspect the model label, 12 VDC/7 A original supply, USB cable and purchased kit contents before energizing.
2. Identify all optional items required for this specific lesson: **Original Magician + writing pen holder; for pick-and-place use its included gripper/vacuum tool and safe lightweight blocks**. If absent, use the offline alternative rather than claiming the physical experiment worked.
3. Follow [the matching DOBOT Magician user manual](../../dobot-magician-user-guide.md) for end-effector mounting, stop controls, homing and operating range. No pinout or power wiring is inferred from the workbook's pictures.
4. Secure the arm and prevent people, cables and tools from entering its reach envelope. Never automatically repeat an unverified trajectory or bypass a hardware stop.
5. Record actual robot firmware, software, tool, zero/home pose and units for each run.

### Software and development resources

* [Source: Chapter 1 (pp. 6–81) of Magician V3.2 (2024)](https://drive.google.com/file/d/1wfgDZ2CETKxll6oDhMkfIFI5Yn5p03-9/view) — original instruction, printable lesson/experiment text and assessment content.
* [DOBOT Magician User Guide](../../dobot-magician-user-guide.md) — authority for exact power, end-effector and hardware control.
* [Magician Series curriculum comparison](../) — tool/edition differences.
* **Note:** Older course materials may reference DobotLab, DobotStudio, DobotBlock and Teach & Playback versions that differ from the installed software. Match the current interface to its manufacturer's manual instead of guessing menu names.

### Getting started

#### Prerequisites

Confirm source worksheet, actual purchased model and available tools; arrange a safe instructor-supervised workspace. Start with dry-run, paper or screen-based planning wherever the workbook requires unavailable peripherals.

#### First working result

1. Connect Magician by USB in DobotLab → Teaching & Playback; with a clear work envelope select Home under supervision. Inspect current XYZ and joint angles. Record HOME, AB-A and AB-B as three safe above-field points, then Save to Local. Do not lower the pen onto the template on the first trial.
2. Save the project/worksheet and include the model, software version, measured or synthetic input values and any observed fault.
3. Compare the result against the source-defined task, then stop safely before further extension.

**Expected result:** Three saved, labeled points and coordinate values for the same robot, with no contact with paper or objects.

#### Extension and assessment

Draft a 19-point CIM route using the workbook's AB/AT pattern, choose MoveJ for safe transit and MoveL for line tracing, and compare repeated results only after instructor-approved first run. Assessment: provide a labeled workflow, input/output table, one result screenshot and a paragraph describing the hardware prerequisites and failure handling.

### Troubleshooting and FAQs

**What if the first checkpoint fails?** When the pen collides with paper, do not raise speed. Revisit AT/AB Z values, tool spring travel and actual taught coordinates; run each step separately before full playback.

**Can this lesson run on a bare DOBOT Magician?** Only its screen/paper or included-tool parts can. The lesson's required items are enumerated above; check the selected bundle and manual before physical extensions.

**What should be done after a motion or electrical fault?** Stop with the verified physical control, power down as prescribed, document controller alarm/status, and obtain qualified instruction before retrying. Do not bypass a safety mechanism.

### Downloads and technical documents

| Resource                                                                                                               | Use                                        |
| ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| [Chapter 1 (pp. 6–81) of Magician V3.2 (2024)](https://drive.google.com/file/d/1wfgDZ2CETKxll6oDhMkfIFI5Yn5p03-9/view) | Source lesson, worksheets and activities   |
| [DOBOT Magician user guide](../../dobot-magician-user-guide.md)                                                        | Hardware and setup instructions            |
| [Exact OpenELAB listing](https://openelab.io/products/dobot-magician-education-robot-arm)                              | Sold model and included/optional equipment |

### References and validation

* Chapter 1 (pp. 6–81) of Magician V3.2 (2024), retrieved from user-supplied Google Drive curriculum collections 2026-11-21.
* [OpenELAB DOBOT Magician listing](https://openelab.io/products/dobot-magician-education-robot-arm), checked 2026-11-21.
* [Previously published model-specific technical user manual](../../dobot-magician-user-guide.md), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware validation:** not run. The result above is the anticipated check, not observed data. Do not treat proposed software decisions as industrial/medical safety functions.
