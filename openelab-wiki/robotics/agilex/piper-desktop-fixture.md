---
description: >-
  Install the passive PiPER fixture on a suitable1–5 cm workbench edge, verify
  the 70 mm M5 pattern, record clamp contact and assess motion loads without
  invented ratings.
---

# AgileX PiPER desktop fixture: fit, mounting and mechanical first checks

{% hint style="info" %}
[**AgileX PiPER desktop fixture kit on OpenELAB — SKU Agilex-PiPER-Desktop-Fixture**](https://openelab.io/products/agilex-piper-desktop-fixture-kit?variant=45885890756806)
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

This is a **passive desktop mounting kit for a PiPER arm**, not a robot, controller or payload upgrade. It provides a stand frame, two adjustable clamps, installation tools and a manual. Use it to establish a stable, repeatable base on a suitable workbench before connecting the arm's power/CAN harness. [Exact store accessory](https://openelab.io/products/agilex-piper-desktop-fixture-kit?variant=45885890756806).

The PiPER manufacturer manual supplies the arm-side base pattern and desktop installation procedure. The store supplies the fixture's advertised fit/envelope. Neither source establishes a universal clamp-force rating, screw torque or overturning capacity for every tabletop. Inspect the actual fixture, arm base and bench together before motion. [Official PiPER manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn).

## Applications

Use the fixture for supervised bench demonstrations, teaching, data collection and small manipulation prototypes where the arm must remain fixed relative to a camera or work surface. Mark the fixture position and record the bench/setup so a later relocation can be detected.

For a repeated experiment, the base position is part of the coordinate system. Re-clamping changes the robot-to-camera/workbench transform even if the program and CAN settings are unchanged. Recheck external calibration after moving the fixture rather than compensating a mechanical shift by changing robot joint zeros.

## Specifications

| Item                          | Reference and boundary                                                               |
| ----------------------------- | ------------------------------------------------------------------------------------ |
| Exact accessory SKU           | Agilex-PiPER-Desktop-Fixture                                                         |
| Supplied contents             | 1 stand frame, 2 adjustable clamps, installation toolkit, user manual                |
| Listed materials              | Aluminum alloy +ABS                                                                  |
| Advertised tabletop fit       | 1–5 cm thickness; actual edge geometry must also allow full jaw seating              |
| Listed fixture envelope       | 25 × 15 × 10 cm; store reference, not a machining drawing                            |
| PiPER arm-side base interface | 4×M5 on 70 × 70 mm square pattern                                                    |
| Electrical supply / logic     | None; fixture has no powered circuit or signal interface                             |
| Firmware / SDK                | None; arm controller software remains separate                                       |
| Published load/torque rating  | No independently verified fixture-specific rating found in reviewed primary material |

[Fixture catalog](https://openelab.io/products/agilex-piper-desktop-fixture-kit),[PiPER mounting dimensions](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn). “M5 × 4”describes four M5 mounting positions; it does not establish a 4 mm screw length. Use the supplied/matched fasteners and confirm engagement against the actual base/fixture stack.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Base pattern and clamp contact

The manufacturer's base-mounting drawing shows the 70 mm square pattern. Confirm both directions by measurement on the actual plate; do not force screws through holes that only approximately align. Check the screw length beneath the fixture before loading the arm: bottoming in a blind feature or insufficient thread engagement can both feel like a tight joint.

The optional desktop assembly is shown in the [manufacturer installation section](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn). Its drawing identifies the mounting assembly; it is not a generic permission to clamp onto glass, thin veneer, a hollow unsupported edge or a loose desk panel. Both jaws must contact sound material with pads fully seated. Rounded edges, under-desk rails and cable trays can prevent seating even when thickness is within 1–5 cm.

A clamp resists slip and overturning through the complete contact arrangement. Do not infer capacity from how hard the handle feels. Follow the supplied fixture instructions for clamp placement and fastener tightening; no torque value is invented here. Keep the arm's base flat on the fixture, with no rocking or hardware trapped beneath it.

### Cable routing and emergency access

Route the power/CAN aviation cable so it cannot pull on the base connector or become a lever against the fixture. Leave room for its keyed insertion/release and keep clamp handles away from the moving arm. The fixture itself has no grounding terminal, emergency stop or electrical isolation function.

Support the arm before releasing any clamp. Remove robot power and manage its gravity load before dismantling; the clamps must not be the last support removed from an otherwise unsupported arm. The correct arm model's instructions determine disable/power-down behavior.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

There is no fixture driver, firmware target or runnable hardware API. For a standard PiPER, use the [PiPER commissioning guide](https://wiki.openelab.io/robotics/agilex/piper-product-user-manual)and its exact firmware profile. A PiPER-H or NERO mounting claim requires its own mechanical confirmation; matching-looking holes alone do not establish this accessory's rated compatibility.

Record the fixture as part of the robot configuration: arm model/base revision, table material/thickness, clamp positions, installed tool, cable route and date. Store a photograph and a simple reference measurement with the workcell calibration. This is more useful than assigning a nonexistent fixture software version.

## Getting started <a href="#getting-started" id="getting-started"></a>

### 1. Establish a static mechanical first result

1. Switch off and physically support the arm. Inventory the frame, two clamps and supplied mounting hardware against the kit sheet.
2. Measure the intended tabletop edge thickness and inspect its underside. Confirm1–5 cm fit \*\* and\*\* unobstructed, flat jaw contact on sound material.
3. Place the fixture and compare its mounting holes with the arm's70 × 70 mm M5 pattern. Confirm fastener engagement/clearance before tightening; do not drill or modify the arm base to force a match.
4. Assemble and secure the fixture according to the supplied arrangement. Check both clamp contacts, base flatness and freedom from rocking. Route the arm harness without strain.
5. Mark the fixture outline or place removable witness marks across stationary contact references. Photograph the clamp jaws and mounting stack, then record distances from the base to two fixed bench references.

**Expected result:** a completely seated, stationary assembly with no rocking, visible contact gaps or cable pull, and a recorded reference for detecting later movement. This is a static installation checkpoint, not a certified load test.

### 2. Understand the load before moving

An original calculation illustrates why tabletop thickness alone is insufficient. Payload gravity moment about the base is approximately `M=m×g×r`, where `r` is horizontal distance. For the standard PiPER's1.5 kg nominal payload at an illustrative0.4m horizontal lever arm:

`M_payload=1.5kg×9.80665m/s²×0.4m≈5.88N·m`.

At0.6m, it is about 8.83 N·m. These are **payload-only static moments**. They exclude the arm/tool's own mass distribution, inertial loads, cable forces and any design margin. They are not fixture ratings or permission to operate at those reaches. A suitable fixture/bench assessment must include the complete moving system and the arm's permitted load/reach conditions. [PiPER payload/workspace reference](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn).

### 3. Transfer to the arm's commissioning procedure

After the installation is accepted for the intended workcell, follow the exact arm's power and feedback procedure. Keep the first supervised motion slow, unloaded and within a small clear envelope. Have an observer watch the base/clamp contacts and witness references while the operator retains the arm's stop control. End the motion if the base rocks, a jaw shifts, the tabletop flexes or a cable becomes taut.

**Expected result:** no relative motion at the fixture/base/bench interfaces through the small checked movement. That observation validates only the tested configuration and envelope; reassess when adding load, changing reach, speed, tool, mounting surface or location. A failed mounting check is repaired mechanically, not with CAN tuning or joint recalibration.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                       | Likely check                                                                            |
| --------------------------------------------- | --------------------------------------------------------------------------------------- |
| Clamp cannot seat within thickness range      | Inspect rounded edges, under-table structures, pad angle and actual jaw travel          |
| Base rocks despite tight screws               | Look for trapped hardware, uneven contact, wrong screw length or a mismatched pattern   |
| Fixture moves during a small motion           | Stop the arm; support it; inspect contacts and bench stiffness before further operation |
| Image/task coordinates shift after relocation | Re-establish base-to-camera/workbench calibration; do not redefine robot joint zero     |
| Cable pulls at full reach                     | Revise routing/strain relief with power off; keep clamp handles outside the sweep       |
| Printed/plastic part cracks or pad deforms    | Remove from service and replace matched parts; do not hide damage with extra tightening |

**Does the fixture raise the PiPER payload?** No. It secures the base; the arm's payload/reach limits remain unchanged.

**Can this guide specify a tightening torque?** The reviewed public sources do not provide a fixture-specific torque schedule. Use the supplied installation sheet/manufacturer specification for the actual hardware; do not convert screw diameter into a guessed torque.

**Can I attach two arms or invert the fixture?** No such assembly/rating was verified here. The arm's support for an orientation does not automatically qualify this desktop accessory for it.

**What changes require another check?** Moving the fixture, replacing clamps/fasteners, changing the tabletop, adding a tool/load or enlarging the motion envelope. Reinspect before resuming.

## Downloads and technical documents

| Resource                                       | Direct destination                                                                                                                       |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| Exact fixture/contents/fit reference           | [OpenELAB fixture](https://openelab.io/products/agilex-piper-desktop-fixture-kit)                                                        |
| Manufacturer mounting and desktop instructions | [PiPER manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn)                                                     |
| Official downloadable arm manual               | [PiPER PDF](https://cdn.shopify.com/s/files/1/0551/0630/6141/files/PIPER_Product_User_Manual_EN_1.pdf?v=1794214904)                      |
| Historical source retained                     | [Earlier PiPER manual copy](https://static.generation-robots.com/media/agilex-piper-user-manual.pdf)                                     |
| Arm SDK                                        | [Current pyAgxArm](https://github.com/agilexrobotics/pyAgxArm);[legacy piper\_sdk](https://github.com/agilexrobotics/piper_sdk)          |
| Fixture-specific CAD/load/torque data          | Not established in the reviewed public resources; use the supplied matched installation sheet before machining or qualifying a load case |

The arm's electrical schematic, SDK and firmware are arm resources, not fixture electronics. The official manual's base and desktop drawings were reviewed; the store envelope is not substituted for dimensioned fixture CAD.

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed the exact fixture catalog/live product and AgileX's standard PiPER base/desktop installation sections, including the relevant drawings. The guide adds an original installation record, static first-result procedure and explicitly limited gravity-moment calculation.

No physical mounting, fastener torque measurement, bench/load qualification or arm motion test was run. Software compilation and electrical testing are not applicable to this passive accessory. No fixture load capacity or cross-model compatibility is asserted.
