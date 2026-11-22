# RealMan RML63: long-reach six-axis arm reference

{% hint style="info" %}
**Model: RML63 standard / force L / force K.** This is a manufacturer-document reference. A current exact-model OpenELAB `.io` product/SKU match was not verified on 22 November 2026; no order link or substitute product is asserted. Check the delivered model, controller generation and project bill of materials before using technical procedures.
{% endhint %}

## Product overview

RML63 is the long-reach, 3 kg family. It is distinct from ECO63 despite their similar reach and payload, and from RM65 despite common controller concepts.

{% hint style="warning" %}
**Long reach and wrist support:** the wrist axes use soft brakes. Secure the tool and support the arm for power-off handling. Do not use ECO63 brake assumptions or load curves.
{% endhint %}

## Applications

Research, teaching and manipulation integration within the model-specific load curve and guarded workspace. Include the end-effector and workpiece in the load assessment. A collaborative-arm description does not certify an assembled workcell.

## Specifications

| Parameter                          | Value and scope                                          |
| ---------------------------------- | -------------------------------------------------------- |
| Degrees of freedom / payload       | 6 / 3 kg                                                 |
| Working radius                     | 900 mm standard; 917 mm force L; 928.5 mm force K        |
| Self-weight                        | 10 kg standard; 10.1 kg force version                    |
| Repeatability / TCP speed          | ±0.05 mm / ≤2.8 m/s                                      |
| Typical / instantaneous peak power | ≤150 W / ≤900 W                                          |
| Brakes / base diameter             | J1–J3 hard, J4–J6 soft / 107 mm parameter-table diameter |

Source: [RML63 manual, PDF pp. 13–29, 30–48 \[RML63\]](realman-source-library.md). These are reference ratings for the stated configuration, not initial test speeds or application safety limits.

{% hint style="warning" %}
**Revision conflict:** the supplied manual lists ≤900 W peak and a 107 mm parameter-table base, while the current developer page lists ≤600 W and 110 mm; the standard/force reach options also depend on revision. See the [current manufacturer RML63 parameters](https://develop.realman-robotics.com/en/robot4th/robotParameter/RML63OntologyParameters/). These figures are kept source-specific. Do not size a supply, select a mount or set limits from this comparison. Powered setup requires the exact delivered drawing, supply specification and controller revision to resolve the discrepancy.
{% endhint %}

## Hardware and connections

Use the supplied RML63 manual base/flange drawings and end-effector load curves. The installation narrative refers to a 110 mm base while the parameter table gives 107 mm; use the dimensioned drawing for the exact revision, not either headline diameter as a mounting pattern. The manual specifies 24 V DC, brown positive and blue negative for its two-core supply cable; check the supplied keyed cable before use.

Before energizing, verify grounding, polarity, mounting, stop access and payload support. Keep controller I/O, power supply and tool outputs distinct; the connector shape does not establish electrical compatibility. Use the source manual's hardware chapter for the delivered cable generation and connector orientation.

## Software and development resources

The official [RM\_API2](https://github.com/RealManRobot/RM_API2) repository provides arm APIs; its Python instructions require Python 3.9 or newer. The reviewed snapshot is `a810b9fdea29e3567c5e9155794e6ef9cc17be62` (1.1.7 update). Select binaries for the delivered controller generation and host architecture. Availability of an API does not establish support for every new arm or whole-robot system.

The reviewed [ROS 2 Humble package](https://github.com/RealManRobot/ros2_rm_robot/tree/711abedd48c6614f26fb4f7661db92f306ff05bd) is V1.7.1, based on controller 1.7.5, for Ubuntu 22.04. Its support table includes RM65, RM75, ECO62/63/65, RML63, GEN72 and RX75. GEN62 is a different model. Confirm the exact end-link and controller support table before selecting a launch configuration. A default real-hardware launch may enable trajectory execution. Use the shared commissioning guide before launching anything.

See [Arm commissioning and SDK selection](realman-arm-commissioning-and-sdk.md) and the [existing teaching-pendant reference](realman-robot-web-teaching-pendant-user-manual-v1.5.md).

## Getting started

Prerequisites: trained operator, rigid mounting, secured tool/payload, the delivered 24 V supply and keyed cables, reachable emergency stop, an isolated wired Ethernet connection, and the exact controller manual. Keep all motion controls inactive.

1. Record the complete arm label, left/right designation where applicable, controller generation, firmware and tool option. Match mounting dimensions to the exact drawing, rather than a nearby family's illustration.
2. With power isolated, fit the supplied keyed power cable and Ethernet cable. Verify the delivered cable against the manual's connector view. Do not hot-plug the aviation connectors or connect tool peripherals yet.
3. Following the delivered startup procedure, observe controller startup and initialization. Investigate a warning/fault indication before continuing; do not clear faults repeatedly to force operation.
4. For the factory wired configuration in the supplied arm manual, set the host to unused `192.168.1.100` with the matching subnet; do not assign the robot's `192.168.1.18` to the host. Open `http://192.168.1.18` in a browser. A changed delivery configuration takes precedence.
5. Sign in with the credentials supplied for the unit, open the controller's system-information/status view, and record the reported model/software, enable state and fault status. Do not press drag-teach/playback buttons or run a trajectory.

**Expected result:** a reachable teaching interface with the correct model and readable controller status, without commanded movement. This is a communication checkpoint, not motion acceptance.

**If this check fails:** inspect power and startup indication, Ethernet link, address/subnet and duplicate-IP conflicts, then the delivered controller configuration. A browser refresh can resolve stale interface assets after an upgrade; it cannot resolve a hardware fault.

Source for this wired, read-only path: [RML63 manual, installation and teaching-pendant chapters \[RML63\]](realman-source-library.md).

## Troubleshooting and FAQs

**The tool moves or drops when power is removed.** Check the exact brake arrangement below and the delivered revision. A soft brake is not a load-holding mechanical brake. Support the tool and payload and use the manufacturer's safe shutdown/transport posture; do not rely on power removal to hold every axis.

**Can a nearby family's URDF or force-sensor option be substituted?** No. Confirm link geometry, joint order, end-link revision, load curve, tool mass and controller support before planning. A force/torque sensor's full-scale range is not a permissible contact-force setting.

**The SDK connects but motion is not ready.** Model identity and readable status do not validate limits, calibration, stop behavior, tool center point or control-source arbitration. Complete the exact revision's commissioning and risk assessment before a bounded motion test.

## Downloads and technical documents

| Resource                                                                                             | Scope and use                                                                          |
| ---------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [Supplied manual/specification \[RML63\]](realman-source-library.md)                                 | Exact supplied reference, with original PDF page ranges in the source library          |
| [Manufacturer manual downloads](https://develop.realman-robotics.com/en/robot4th/download/manual/)   | Select exact family and controller generation; newer files may differ                  |
| [Manufacturer model/CAD downloads](https://develop.realman-robotics.com/en/robot4th/download/model/) | Confirm model/end-link dimensions before mounting or simulation                        |
| [RM\_API2](https://github.com/RealManRobot/RM_API2)                                                  | C/C++/Python arm interfaces; version and architecture matching required                |
| [ROS 2 package](https://github.com/RealManRobot/ros2_rm_robot/tree/humble)                           | Supported model table and launch instructions; do not assume GEN62 or whole-S2 support |

Firmware replacement is outside this first-result procedure. Obtain the exact controller image and recovery instructions through the manufacturer delivery channel; no cross-model firmware is supplied here.

## References and validation

[RML63 manual, PDF pp. 13–29, 30–48 \[RML63\]](realman-source-library.md); official repositories and downloads linked above. Reviewed 22 November 2026. Software execution: **not run**. Hardware validation: **not run**. The published reference does not authorize operation on an unmatched revision; any unresolved delivery-specific mounting, power or software target keeps powered commissioning blocked.

[RealMan series index](./)
