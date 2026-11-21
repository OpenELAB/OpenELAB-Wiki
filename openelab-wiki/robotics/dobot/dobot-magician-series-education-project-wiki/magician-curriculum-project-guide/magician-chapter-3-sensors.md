---
description: >-
  Source-derived DOBOT Magician education lesson: Digital Inputs, Sensors and
  Color-Based Sorting. Equipment, model limitations and validated-first-result
  pathway.
---

# DOBOT Magician — Digital Inputs, Sensors and Color-Based Sorting

{% hint style="info" %}
[**View DOBOT Magician on OpenELAB**](https://openelab.io/products/dobot-magician-education-robot-arm)

**Model:** DOBOT Magician · **SKU:** `DOBOT-1100000015` · **Scope:** Basic/Educational Plans; additional wireless, laser and joystick accessories require Educational Plan
{% endhint %}

[DOBOT Magician course guide](./) · [Magician Series index](../) · [Existing user guide](../../dobot-magician-user-guide.md)

### Product overview

**Chapter 3 (pp. 152–236) of Magician V3.2.** Digital Inputs, Sensors and Color-Based Sorting is a source-derived teaching tutorial for **DOBOT Magician**. It preserves the workbook's concepts while separating classroom planning, safe read-only setup and optional physical robotics. Do not apply another Magician-family model's points, voltage, connector or tool command.

### Applications

* Microswitch-based digital inputs and guarded pick-and-place
* Sensor Kit / Magic Box input and output exploration
* Color sensor reading and mini-conveyor classification

### Specifications

| Integration parameter | Value / conditions                                                                                                                         |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Robot / power         | Four-axis, 500 g maximum payload, 320 mm reach, ±0.2 mm repeatability, 12 VDC/7 A original adapter                                         |
| Development software  | DobotLab Teaching & Playback / DobotBlock; older DobotStudio only when compatible                                                          |
| Lesson equipment      | Matching Magician Sensor Kit or Magic Box and color sensor; mini conveyor for the final sorting activity; these are additional accessories |
| Course version        | Chapter 3 (pp. 152–236) of Magician V3.2                                                                                                   |
| Physical motion       | Instructor-supervised only; complete model-specific manual and stop procedure before use                                                   |

### Hardware and connections

1. Inspect the model label, 12 VDC/7 A original supply, USB cable and purchased kit contents before energizing.
2. Identify all optional items required for this specific lesson: **Matching Magician Sensor Kit or Magic Box and color sensor; mini conveyor for the final sorting activity; these are additional accessories**. If absent, use the offline alternative rather than claiming the physical experiment worked.
3. Follow [the matching DOBOT Magician user manual](../../dobot-magician-user-guide.md) for end-effector mounting, stop controls, homing and operating range. No pinout or power wiring is inferred from the workbook's pictures.
4. Secure the arm and prevent people, cables and tools from entering its reach envelope. Never automatically repeat an unverified trajectory or bypass a hardware stop.
5. Record actual robot firmware, software, tool, zero/home pose and units for each run.

### Software and development resources

* [Source: Chapter 3 (pp. 152–236) of Magician V3.2](https://drive.google.com/file/d/1wfgDZ2CETKxll6oDhMkfIFI5Yn5p03-9/view) — original instruction, printable lesson/experiment text and assessment content.
* [DOBOT Magician User Guide](../../dobot-magician-user-guide.md) — authority for exact power, end-effector and hardware control.
* [Magician Series curriculum comparison](../) — tool/edition differences.
* **Note:** Older course materials may reference DobotLab, DobotStudio, DobotBlock and Teach & Playback versions that differ from the installed software. Match the current interface to its manufacturer's manual instead of guessing menu names.

### Getting started

#### Prerequisites

Confirm source worksheet, actual purchased model and available tools; arrange a safe instructor-supervised workspace. Start with dry-run, paper or screen-based planning wherever the workbook requires unavailable peripherals.

#### First working result

1. With arm power/motion disabled, create a table of three labeled object colors. For each measured/synthetic color event, classify it as red, blue or UNKNOWN. Verify that UNKNOWN never authorizes a grasp/transport step. Only after checking the real sensor output mapping should a teacher connect the decision to the arm.
2. Save the project/worksheet and include the model, software version, measured or synthetic input values and any observed fault.
3. Compare the result against the source-defined task, then stop safely before further extension.

**Expected result:** Classification and rejection table, annotated with actual sensor type and its observed signal when available.

#### Extension and assessment

Describe a flowchart: detect part → confirm clear work cell → classify → select allowed bin → supervise pick/place → verify → log rejects. Assessment: provide a labeled workflow, input/output table, one result screenshot and a paragraph describing the hardware prerequisites and failure handling.

### Troubleshooting and FAQs

**What if the first checkpoint fails?** If a color result varies with lighting, compare white balance, illumination, surface material and sensor working distance; do not classify from an invented fixed numeric threshold.

**Can this lesson run on a bare DOBOT Magician?** Only its screen/paper or included-tool parts can. The lesson's required items are enumerated above; check the selected bundle and manual before physical extensions.

**What should be done after a motion or electrical fault?** Stop with the verified physical control, power down as prescribed, document controller alarm/status, and obtain qualified instruction before retrying. Do not bypass a safety mechanism.

### Downloads and technical documents

| Resource                                                                                                           | Use                                        |
| ------------------------------------------------------------------------------------------------------------------ | ------------------------------------------ |
| [Chapter 3 (pp. 152–236) of Magician V3.2](https://drive.google.com/file/d/1wfgDZ2CETKxll6oDhMkfIFI5Yn5p03-9/view) | Source lesson, worksheets and activities   |
| [DOBOT Magician user guide](../../dobot-magician-user-guide.md)                                                    | Hardware and setup instructions            |
| [Exact OpenELAB listing](https://openelab.io/products/dobot-magician-education-robot-arm)                          | Sold model and included/optional equipment |

### References and validation

* Chapter 3 (pp. 152–236) of Magician V3.2, retrieved from user-supplied Google Drive curriculum collections 2026-11-21.
* [OpenELAB DOBOT Magician listing](https://openelab.io/products/dobot-magician-education-robot-arm), checked 2026-11-21.
* [Previously published model-specific technical user manual](../../dobot-magician-user-guide.md), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware validation:** not run. The result above is the anticipated check, not observed data. Do not treat proposed software decisions as industrial/medical safety functions.
