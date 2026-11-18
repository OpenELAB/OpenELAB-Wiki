# AgileX PiPER desktop fixture: installation and mechanical checks

{% hint style="info" %}
[**View AgileX PiPER desktop fixture on OpenELAB**](https://openelab.io/products/agilex-piper-desktop-fixture-kit)

**Product/option:** AgileX PiPER desktop fixture · **Workbook SKU:** `Agilex-PiPER-Desktop-Fixture`
{% endhint %}

[Agilex-PiPER-Desktop-Fixture](https://openelab.io/products/agilex-piper-desktop-fixture-kit)

## Product and scope

A passive mounting accessory for securing a PiPER arm on a suitable workbench. It supports repeatable robot-development setups but supplies no motion controller, SDK or additional payload rating. Confirm the exact fixture and PiPER base revision before installation.

## Hardware and technical documents

| Item                 | Reference                                                                   |
| -------------------- | --------------------------------------------------------------------------- |
| Scope                | Agilex-PiPER-Desktop-Fixture accessory                                      |
| Mechanical interface | Match the supplied fixture drawing and arm-base hole pattern                |
| Fasteners            | Use manufacturer-specified diameter, engagement depth and tightening torque |
| Software             | Arm-side PiPER SDK only; the fixture has no firmware                        |

A fixture-specific dimensioned drawing and torque schedule were not found in accessible primary material. Do not fabricate hole spacing, screw length, clamp range or load capacity from a photograph. Obtain those details from AgileX or the supplied installation sheet before drilling a bench or operating the arm. The PiPER arm manual remains the authority for base mounting and permitted installation orientation.

## Getting started

1. Switch off and support the arm. Inventory the fixture plate/clamps and fasteners against the supplied installation sheet.
2. Confirm bench thickness, material and load capacity are suitable for the complete moving system. Check that all clamps can seat fully.
3. Compare the base pattern and screw engagement with the correct PiPER mounting diagram. Do not force mismatched holes or bottom screws in the housing.
4. Secure the fixture and arm following the specified sequence; inspect for rocking, interference and cable pinch points.
5. After mechanical sign-off, follow the PiPER startup procedure. Test low-speed motion inside a small clear envelope while watching the base and fixture.

**Expected checkpoint:** The base remains stationary without rocking, clamp movement or cable interference during a controlled low-speed check.

## Development software and recovery

For arm control use AgileX's PiPER SDK and select the API appropriate to the actual arm firmware. Firmware/API compatibility is independent of fixture compatibility. Save the fixture installation record with the robot's configuration; changing bench location warrants a new mechanical check.

## FAQs

**Can I infer compatible screws from the arm model name?** No. Confirm the base revision, fixture drawing and allowable engagement.

**Does the fixture increase the arm's payload?** No. Follow the robot's own load and mounting conditions.

**Why is there no fixture SDK?** It is a mechanical accessory; software belongs to the arm controller.

## Sources and validation

* [PiPER manufacturer user manual](https://static.generation-robots.com/media/agilex-piper-user-manual.pdf)
* [AgileX PiPER SDK](https://github.com/agilexrobotics/piper_sdk)
* [Exact OpenELAB fixture](https://openelab.io/products/agilex-piper-desktop-fixture-kit)

Reviewed 18 November 2026. Source links and accessible manufacturer documentation were reviewed; this guide has not been compiled or tested on physical hardware. Before reproducing a project, record the board revision, firmware/SDK release or commit, operating system and any changes to the supplied configuration.
