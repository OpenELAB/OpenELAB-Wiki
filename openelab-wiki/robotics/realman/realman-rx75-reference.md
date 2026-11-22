# RealMan RX75: force and vision arm reference

{% hint style="info" %}
**Model: RX75 six-axis force / force + vision.** This is a manufacturer-document reference. A current exact-model OpenELAB `.io` product/SKU match was not verified on 22 November 2026; no order link or substitute product is asserted. Check the delivered model, controller generation and project bill of materials before using technical procedures.
{% endhint %}

## Product overview

This guide covers the RX family described in the supplied RX manual. Left and right arms have mirrored restrictions. The RX75S arms on RealBot-S2 have different geometry and must use the S2/RX75S delivery documents.

{% hint style="warning" %}
**RX75 is not RX75S.** Do not transfer 709/732 mm reach, D405 camera configuration, joint limits or URDF to the S2 RX75S assembly. Retain the physical left/right label throughout software setup.
{% endhint %}

## Applications

Research, teaching and manipulation integration within the model-specific load curve and guarded workspace. Include the end-effector and workpiece in the load assessment. A collaborative-arm description does not certify an assembled workcell.

## Specifications

| Parameter                          | Value and scope                                                                |
| ---------------------------------- | ------------------------------------------------------------------------------ |
| Degrees of freedom / payload       | 7 / 5 kg                                                                       |
| Working radius                     | 709 mm force version; 732 mm force + vision                                    |
| Self-weight                        | 8.18 kg force; 8.38 kg force + vision                                          |
| Repeatability / TCP speed          | ±0.2 mm / ≤2.2 m/s                                                             |
| Typical / instantaneous peak power | ≤200 W / ≤1000 W                                                               |
| Brakes / force sensor              | J1–J4 hard, J5–J7 soft / 200 N and 7 N·m, ±0.5% FS                             |
| Vision option                      | D405 end camera in supplied RX manual; not a universal S2 camera specification |

Source: [RX family manual, PDF pp. 14–32, 33–49 \[RX\]](realman-source-library/). These are reference ratings for the stated configuration, not initial test speeds or application safety limits.

{% hint style="warning" %}
**Revision conflict:** the supplied manual lists 709 mm, 8.18/8.38 kg and ≤1000 W peak, while the current developer page lists 709.2 mm, 8.2/8.4 kg and ≤600 W; the manual says any-angle installation, while the current page specifies side mounting Ry=−90°. See the [current manufacturer RX75 parameters](https://develop.realman-robotics.com/en/robot4th/robotParameter/RX75OntologyParameters/). These figures are kept source-specific. Do not size a supply, select a mount or set limits from this comparison. Powered setup requires the exact delivered drawing, supply specification and controller revision to resolve the discrepancy.
{% endhint %}

## Hardware and connections

The source installation narrative uses an RXL75-6F-C3 example with different stated weight/base dimensions from the later parameter table. Confirm the exact model and dimensioned drawing before selecting a mount; the example is not a universal RX75 mounting specification. The supplied power procedure uses 24 V DC; align the keyed two-core connector while de-energized. PDF p. 32 gives different left/right J7 ranges.

Before energizing, verify grounding, polarity, mounting, stop access and payload support. Keep controller I/O, power supply and tool outputs distinct; the connector shape does not establish electrical compatibility. Use the source manual's hardware chapter for the delivered cable generation and connector orientation.

## Software and development resources

The official [RM\_API2](https://github.com/RealManRobot/RM_API2) repository provides arm APIs; its Python instructions require Python 3.9 or newer. The reviewed snapshot is `a810b9fdea29e3567c5e9155794e6ef9cc17be62` (1.1.7 update). Select binaries for the delivered controller generation and host architecture. Availability of an API does not establish support for every new arm or whole-robot system.

The reviewed [ROS 2 Humble package](https://github.com/RealManRobot/ros2_rm_robot/tree/711abedd48c6614f26fb4f7661db92f306ff05bd) is V1.7.1, based on controller 1.7.5, for Ubuntu 22.04. Its support table includes RM65, RM75, ECO62/63/65, RML63, GEN72 and RX75. GEN62 is a different model. Confirm the exact end-link and controller support table before selecting a launch configuration. A default real-hardware launch may enable trajectory execution. Use the shared commissioning guide before launching anything.

See [Arm commissioning and SDK selection](realman-arm-commissioning-and-sdk.md) and the [existing teaching-pendant reference](realman-robot-web-teaching-pendant-user-manual-v1.5.md).

## Complete supplied document and engineering details

[RX series hardware manual — all 49 PDF pages](realman-source-library/complete-rx-manual.md). The full reference is readable inside the wiki, with an original-page view and searchable text for every page. It includes the material not repeated in this entry guide.

| Source section                                                        | Full in-wiki reference                                                |
| --------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Safety, responsibilities and warranty                                 | [PDF 1–11](realman-source-library/complete-rx-manual.md#pdf-page-1)   |
| Composition, mounting, startup, teaching and shutdown                 | [PDF 11–22](realman-source-library/complete-rx-manual.md#pdf-page-11) |
| Controller and tool wiring, I/O, external power and RS485             | [PDF 22–30](realman-source-library/complete-rx-manual.md#pdf-page-22) |
| RX75 parameters, MDH, dynamics, dimensions, workspace and load curves | [PDF 30–43](realman-source-library/complete-rx-manual.md#pdf-page-30) |
| FAQs, handling, maintenance, repair and disposal                      | [PDF 44–49](realman-source-library/complete-rx-manual.md#pdf-page-44) |

### Exact-model parameter selection

For **RX75**, start with [the applicable parameter chapter](realman-source-library/complete-rx-manual.md#pdf-page-30). Retain the adjacent dynamic tables, diagrams and load curves as part of the specification; the short table above is not the complete parameter set.

### Installation and electrical integration

Use the exact model's installation drawing before selecting base fasteners, tool screws or a mounting plate. The dimension drawings, joint distribution, working envelope and load curves are separate documents within the full manual: a headline payload does not specify the permitted payload at every reach, center of gravity or acceleration. Keep the arm label, force-sensor option, mounting orientation, tool mass and TCP record with the installation.

The hardware chapters distinguish the **16-core controller expansion connector** from the **6-core tool connector**. The controller chapter also distinguishes Gen1 and Gen2 wire colors. Select the delivered cable generation and the connector view shown in that model's source; a wire color from another generation is not a pin assignment. The original pages preserve the connector drawings and the complete tables, including reserved pins, E\_STOP, I/O references, power outputs, RS485 and FDCAN where documented.

Before attaching any peripheral, separate these electrical roles in the wiring plan: arm power input, programmable auxiliary output, digital input reference, digital output reference, signal/common ground and communications pair. Confirm voltage, current budget and return path for each. An auxiliary output specification is not an input-supply specification. Do not connect two supplies together merely because their nominal voltage is the same.

The supplied hardware manuals describe configurable I/O and tool power; those settings can be disabled at startup. A physically connected device can therefore remain unpowered, or expose the wrong I/O role, until the intended configuration is verified. Start by reading the configuration and recording the delivered state. Standard I/O is not a substitute for a safety-rated protective circuit.

### Kinematic and dynamic data

The full parameter chapters contain the modified Denavit–Hartenberg coordinate-system figures, parameter tables, link mass and inertia data, joint/dimension drawings, working envelope, singular configurations and load curves. Preserve **model, force-sensor suffix, reference frame, units and inertia-axis convention** when entering them into simulation or planning software. Do not copy an RM65 table to an RM75 model, or an ECO63 table to an ECO65 model, simply because the interface looks similar.

For a planned integration, make a configuration record containing the base transform, tool transform, installed end link, payload mass, payload center of gravity, permitted joint interval and speed for every axis, and the exact source page for each value. Check that the URDF/driver joint count and order match that record. A visual model loading in a simulator does not verify its dynamics, joint limits or the controller's motion capabilities.

### Operation, shutdown and maintenance

Teaching buttons, drag modes, playback and initial-pose functions can move the arm. Establish a safe mounted state, a clear swept envelope, an accessible emergency stop and the correct tool/payload settings before using them. A button that records or reproduces a trajectory is not a read-only communication check. Keep source-specific brake arrangements in view when supporting a tool or removing power; a soft brake is not a mechanical holding brake.

For normal shutdown, follow the model's switch/supply sequence. For work on the arm or controller, isolate the power and prevent re-energization. The safety chapters distinguish residual-energy discharge from thermal cooldown: their emergency energy-discharge guidance does not replace the separate hot-surface waiting period. Internal repair is reserved to qualified/authorized personnel; retain the ESD, approved-parts and sealing precautions in the full maintenance chapter.

After changing mounting, TCP, payload, I/O mode, safety settings, controller software or a tool, repeat the relevant acceptance checks and save the configuration. Record the fault text/code and the circumstances before clearing it. Repeatedly clearing an error without determining its cause is not a recovery procedure.

### Integration acceptance record

| Check                    | Evidence to retain                                                                                             |
| ------------------------ | -------------------------------------------------------------------------------------------------------------- |
| Exact hardware           | Arm/controller labels, model/sensor suffix, cable generation and installed tool                                |
| Mounting and load        | Source drawing, fastener selection, installed orientation, payload/center of gravity and applicable load curve |
| Electrical configuration | Supply approval, measured/configured voltages, peripheral current budget, grounds and I/O roles                |
| Communication            | Controller model/software reported by the read-only interface; expected network configuration                  |
| Kinematics               | Joint names/order, per-axis bounds, base/tool transforms and the exact model data source                       |
| Operational recovery     | Stop/reset authority, fault evidence, shutdown and restoration checks                                          |

This acceptance record is supplementary integration guidance. The original safety, warranty, hardware, handling, repair and disposal sections remain available in full in the source reader.

## Getting started

Prerequisites: trained operator, rigid mounting, secured tool/payload, the delivered 24 V supply and keyed cables, reachable emergency stop, an isolated wired Ethernet connection, and the exact controller manual. Keep all motion controls inactive.

1. Record the complete arm label, left/right designation where applicable, controller generation, firmware and tool option. Match mounting dimensions to the exact drawing, rather than a nearby family's illustration.
2. With power isolated, fit the supplied keyed power cable and Ethernet cable. Verify the delivered cable against the manual's connector view. Do not hot-plug the aviation connectors or connect tool peripherals yet.
3. Following the delivered startup procedure, observe controller startup and initialization. Investigate a warning/fault indication before continuing; do not clear faults repeatedly to force operation.
4. For the factory wired configuration in the supplied arm manual, set the host to unused `192.168.1.100` with the matching subnet; do not assign the robot's `192.168.1.18` to the host. Open `http://192.168.1.18` in a browser. A changed delivery configuration takes precedence.
5. Sign in with the credentials supplied for the unit, open the controller's system-information/status view, and record the reported model/software, enable state and fault status. Do not press drag-teach/playback buttons or run a trajectory.

**Expected result:** a reachable teaching interface with the correct model and readable controller status, without commanded movement. This is a communication checkpoint, not motion acceptance.

**If this check fails:** inspect power and startup indication, Ethernet link, address/subnet and duplicate-IP conflicts, then the delivered controller configuration. A browser refresh can resolve stale interface assets after an upgrade; it cannot resolve a hardware fault.

Source for this wired, read-only path: [RX family manual, installation and teaching-pendant chapters \[RX\]](realman-source-library/).

## Troubleshooting and FAQs

**The tool moves or drops when power is removed.** Check the exact brake arrangement below and the delivered revision. A soft brake is not a load-holding mechanical brake. Support the tool and payload and use the manufacturer's safe shutdown/transport posture; do not rely on power removal to hold every axis.

**Can a nearby family's URDF or force-sensor option be substituted?** No. Confirm link geometry, joint order, end-link revision, load curve, tool mass and controller support before planning. A force/torque sensor's full-scale range is not a permissible contact-force setting.

**The SDK connects but motion is not ready.** Model identity and readable status do not validate limits, calibration, stop behavior, tool center point or control-source arbitration. Complete the exact revision's commissioning and risk assessment before a bounded motion test.

## Downloads and technical documents

| Resource                                                                                             | Scope and use                                                                          |
| ---------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [Supplied manual/specification \[RX\]](realman-source-library/)                                      | Exact supplied reference, with original PDF page ranges in the source library          |
| [Manufacturer manual downloads](https://develop.realman-robotics.com/en/robot4th/download/manual/)   | Select exact family and controller generation; newer files may differ                  |
| [Manufacturer model/CAD downloads](https://develop.realman-robotics.com/en/robot4th/download/model/) | Confirm model/end-link dimensions before mounting or simulation                        |
| [RM\_API2](https://github.com/RealManRobot/RM_API2)                                                  | C/C++/Python arm interfaces; version and architecture matching required                |
| [ROS 2 package](https://github.com/RealManRobot/ros2_rm_robot/tree/humble)                           | Supported model table and launch instructions; do not assume GEN62 or whole-S2 support |

Firmware replacement is outside this first-result procedure. Obtain the exact controller image and recovery instructions through the manufacturer delivery channel; no cross-model firmware is supplied here.

## References and validation

[RX family manual, PDF pp. 14–32, 33–49 \[RX\]](realman-source-library/); official repositories and downloads linked above. Reviewed 22 November 2026. Software execution: **not run**. Hardware validation: **not run**. The published reference does not authorize operation on an unmatched revision; any unresolved delivery-specific mounting, power or software target keeps powered commissioning blocked.

[RealMan series index](./)
