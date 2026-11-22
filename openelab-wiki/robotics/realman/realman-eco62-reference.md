# RealMan ECO62: compact embedded arm reference

{% hint style="info" %}
**Model: ECO62.** This is a manufacturer-document reference. A current exact-model OpenELAB `.io` product/SKU match was not verified on 22 November 2026; no order link or substitute product is asserted. Check the delivered model, controller generation and project bill of materials before using technical procedures.
{% endhint %}

## Product overview

ECO62 is a compact embedded arm. Its supplied four-page specification sheet is not an installation manual and does not establish the connector orientation or a delivery-specific controller address.

{% hint style="warning" %}
**Commissioning boundary:** the first result below is a de-energized identity/document check. The ECO63/ECO65 manual is not evidence for ECO62 wiring, mounting or network defaults.
{% endhint %}

## Applications

Research, teaching and manipulation integration within the model-specific load curve and guarded workspace. Include the end-effector and workpiece in the load assessment. A collaborative-arm description does not certify an assembled workcell.

## Specifications

| Parameter                          | Value and scope                                                    |
| ---------------------------------- | ------------------------------------------------------------------ |
| Degrees of freedom / rated payload | 6 / 2 kg                                                           |
| Self-weight / working radius       | 3.6 kg / 425 mm                                                    |
| Repeatability / height             | ±0.1 mm / 514.5 mm                                                 |
| Brakes                             | J1–J3 mechanical; J4–J6 soft                                       |
| Typical / peak power               | ≤100 W / ≤180 W                                                    |
| Controller supply                  | 20–30 V DC; nominal 24 V                                           |
| Interfaces                         | Ethernet, USB serial, RS485; tool: 2 DI/DO, RS485 and power output |

Source: [ECO62 specification sheet, PDF pp. 1–4 \[ECO62\]](realman-source-library/). These are reference ratings for the stated configuration, not initial test speeds or application safety limits.

## Hardware and connections

The specification sheet identifies a base-integrated controller and supply range, but does not provide sufficient connector pinout or grounding instructions for a new wiring job. Obtain the exact ECO62 installation drawing, keyed cable, rated supply and stop arrangement before powered commissioning. The [official ECO62 parameters](https://develop.realman-robotics.com/en/robot/robotParameter/ECO62OntologyParameters/) agree on the basic payload/reach/brakes.

Before energizing, verify grounding, polarity, mounting, stop access and payload support. Keep controller I/O, power supply and tool outputs distinct; the connector shape does not establish electrical compatibility. Use the source manual's hardware chapter for the delivered cable generation and connector orientation.

## Software and development resources

The official [RM\_API2](https://github.com/RealManRobot/RM_API2) repository provides arm APIs; its Python instructions require Python 3.9 or newer. The reviewed snapshot is `a810b9fdea29e3567c5e9155794e6ef9cc17be62` (1.1.7 update). Select binaries for the delivered controller generation and host architecture. Availability of an API does not establish support for every new arm or whole-robot system.

The reviewed [ROS 2 Humble package](https://github.com/RealManRobot/ros2_rm_robot/tree/711abedd48c6614f26fb4f7661db92f306ff05bd) is V1.7.1, based on controller 1.7.5, for Ubuntu 22.04. Its support table includes RM65, RM75, ECO62/63/65, RML63, GEN72 and RX75. GEN62 is a different model. Confirm the exact end-link and controller support table before selecting a launch configuration. A default real-hardware launch may enable trajectory execution. Use the shared commissioning guide before launching anything.

See [Arm commissioning and SDK selection](realman-arm-commissioning-and-sdk.md) and the [existing teaching-pendant reference](realman-robot-web-teaching-pendant-user-manual-v1.5.md).

## Complete supplied document and engineering details

[ECO62 specification sheet — all 4 PDF pages](realman-source-library/complete-eco62-specification.md). The full reference is readable inside the wiki, with an original-page view and searchable text for every page. It includes the material not repeated in this entry guide.

| Source section                              | Full in-wiki reference                                                     |
| ------------------------------------------- | -------------------------------------------------------------------------- |
| Composite flyer                             | [PDF 1](realman-source-library/complete-eco62-specification.md#pdf-page-1) |
| Product overview                            | [PDF 2](realman-source-library/complete-eco62-specification.md#pdf-page-2) |
| Complete arm/controller specification table | [PDF 3](realman-source-library/complete-eco62-specification.md#pdf-page-3) |
| Application panels                          | [PDF 4](realman-source-library/complete-eco62-specification.md#pdf-page-4) |

### Complete brochure parameter table

| Item                           | Supplied specification                                                            |
| ------------------------------ | --------------------------------------------------------------------------------- |
| Axes / payload / mass          | 6 axes; 2 kg rated payload; 3.6 kg arm mass                                       |
| Repeatability / reach / height | ±0.1 mm; 425 mm working radius; 514.5 mm overall height                           |
| Brakes                         | Mechanical J1–J3; soft J4–J6                                                      |
| Joint ranges                   | J1 −178°…+178°; J2 −169°…+104°; J3 −151°…+133°; J4/J5 −172°…+172°; J6 −360°…+360° |
| Maximum joint speed            | J1–J3 225°/s; J4–J6 180°/s                                                        |
| TCP speed                      | <1.6 m/s                                                                          |
| Power                          | Typical ≤100 W; peak ≤180 W                                                       |
| Controller / input             | Base-integrated; DC 20–30 V, rated DC 24 V                                        |
| Interfaces                     | Ethernet, USB serial, RS485; tool 2 DI/DO, 1 RS485, 1 power output                |
| Teaching/control               | Drag teaching, teach pendant, API, JSON                                           |
| Environment / material         | 0–50°C; relative humidity ≤85%; aluminum alloy / ABS                              |

[Original parameter page and verified transcription](realman-source-library/complete-eco62-specification.md#pdf-page-3).

### What the brochure does and does not establish

The full reader includes every cover/application panel as well as the complete parameter table. The material supports model selection and an integration requirements record. It does not provide a complete power/connector drawing, mounting torque schedule, controller image, command contract or recovery procedure. Obtain those exact-model deliverables before powered integration; do not fill them with another arm’s manual. Retain the distinction between rated and maximum payload and between soft and mechanical brakes.

Supplementary acceptance work should record the controller and arm labels, the delivered tool and load, actual mounting drawing, approved supply and cable, per-joint limits, brake/support plan and the version-matched software package. Check firmware/SDK/URDF support by the exact model name. A general “SDK / ROS 2 ready” brochure statement is not a compatibility matrix for a particular release.

## Getting started

1. Keep power disconnected. Photograph the complete arm and controller labels and record the serial/revision and included cable part numbers.
2. Compare the delivered unit with the supplied specification sheet and the exact-model manufacturer parameter page linked above. Record each difference in weight, joint ranges, environment or speed notation.
3. Obtain the exact delivered installation manual, power connector drawing, emergency-stop circuit, safe support/transport posture and software support matrix. Match the controller and end-link model explicitly.
4. Review the documentation with the responsible integrator before connecting power. For GEN62, confirm that the delivered SDK actually lists GEN62; GEN72 support is insufficient.

**Expected result:** an identified arm/controller and a completed revision/document list, without energizing the product. If a pinout, mounting detail or limit is missing, retain this state and obtain the missing exact-model document before continuing.

## Troubleshooting and FAQs

**The tool moves or drops when power is removed.** Check the exact brake arrangement below and the delivered revision. A soft brake is not a load-holding mechanical brake. Support the tool and payload and use the manufacturer's safe shutdown/transport posture; do not rely on power removal to hold every axis.

**Can a nearby family's URDF or force-sensor option be substituted?** No. Confirm link geometry, joint order, end-link revision, load curve, tool mass and controller support before planning. A force/torque sensor's full-scale range is not a permissible contact-force setting.

**The SDK connects but motion is not ready.** Model identity and readable status do not validate limits, calibration, stop behavior, tool center point or control-source arbitration. Complete the exact revision's commissioning and risk assessment before a bounded motion test.

## Downloads and technical documents

| Resource                                                                                             | Scope and use                                                                          |
| ---------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [Supplied manual/specification \[ECO62\]](realman-source-library/)                                   | Exact supplied reference, with original PDF page ranges in the source library          |
| [Manufacturer manual downloads](https://develop.realman-robotics.com/en/robot4th/download/manual/)   | Select exact family and controller generation; newer files may differ                  |
| [Manufacturer model/CAD downloads](https://develop.realman-robotics.com/en/robot4th/download/model/) | Confirm model/end-link dimensions before mounting or simulation                        |
| [RM\_API2](https://github.com/RealManRobot/RM_API2)                                                  | C/C++/Python arm interfaces; version and architecture matching required                |
| [ROS 2 package](https://github.com/RealManRobot/ros2_rm_robot/tree/humble)                           | Supported model table and launch instructions; do not assume GEN62 or whole-S2 support |

Firmware replacement is outside this first-result procedure. Obtain the exact controller image and recovery instructions through the manufacturer delivery channel; no cross-model firmware is supplied here.

## References and validation

[ECO62 specification sheet, PDF pp. 1–4 \[ECO62\]](realman-source-library/); official repositories and downloads linked above. Reviewed 22 November 2026. Software execution: **not run**. Hardware validation: **not run**. The published reference does not authorize operation on an unmatched revision; any unresolved delivery-specific mounting, power or software target keeps powered commissioning blocked.

[RealMan series index](./)
