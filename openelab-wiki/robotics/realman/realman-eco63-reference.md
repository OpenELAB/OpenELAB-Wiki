# RealMan ECO63: collaborative arm reference

{% hint style="info" %}
**Model: ECO63 standard / six-axis force.** This is a manufacturer-document reference. A current exact-model OpenELAB `.io` product/SKU match was not verified on 22 November 2026; no order link or substitute product is asserted. Check the delivered model, controller generation and project bill of materials before using technical procedures.
{% endhint %}

## Product overview

ECO63 is a 900 mm reach, 3 kg collaborative configuration. The shared ECO manual also covers ECO65; the latter has a shorter reach and a higher rated payload. RML63 has different construction and brake behavior.

{% hint style="warning" %}
**Brake revision:** use the hard-brake statement only for the supplied ECO revision. Earlier ECO documentation describes unbraked wrist axes. Verify the delivered hardware before relying on power-off holding; never use a brake claim as a substitute for securing a suspended load.
{% endhint %}

## Applications

Research, teaching and manipulation integration within the model-specific load curve and guarded workspace. Include the end-effector and workpiece in the load assessment. A collaborative-arm description does not certify an assembled workcell.

## Specifications

| Parameter                          | Value and scope                           |
| ---------------------------------- | ----------------------------------------- |
| Degrees of freedom / payload       | 6 / 3 kg                                  |
| Working radius                     | 900 mm standard; 917 mm force version     |
| Self-weight                        | 9.5 kg standard; 9.6 kg force version     |
| Repeatability / TCP speed          | ±0.05 mm / ≤2.8 m/s                       |
| Typical / instantaneous peak power | ≤150 W / ≤900 W                           |
| Brakes                             | Supplied ECO manual: hard brakes on J1–J6 |

Source: [ECO family manual, PDF pp. 29–40 \[ECO\]](realman-source-library/). These are reference ratings for the stated configuration, not initial test speeds or application safety limits.

{% hint style="warning" %}
**Revision conflict:** the supplied manual lists ≤900 W peak, while the current developer page lists ≤600 W; mounting and joint-limit details also vary by source. See the [current manufacturer ECO63 parameters](https://develop.realman-robotics.com/en/robot4th/robotParameter/ECO63OntologyParameters/). These figures are kept source-specific. Do not size a supply, select a mount or set limits from this comparison. Powered setup requires the exact delivered drawing, supply specification and controller revision to resolve the discrepancy.
{% endhint %}

## Hardware and connections

The supplied ECO manual specifies 24 V DC and separates the base controller connector from the six-core tool connector. It documents multiple 16-core cable generations: identify the delivered cable before using wire colors. Refer to PDF pp. 13–14 for the installation drawing, pp. 21–29 for connector diagrams and pp. 29–40 for ECO63 geometry/load curves.

Before energizing, verify grounding, polarity, mounting, stop access and payload support. Keep controller I/O, power supply and tool outputs distinct; the connector shape does not establish electrical compatibility. Use the source manual's hardware chapter for the delivered cable generation and connector orientation.

## Software and development resources

The official [RM\_API2](https://github.com/RealManRobot/RM_API2) repository provides arm APIs; its Python instructions require Python 3.9 or newer. The reviewed snapshot is `a810b9fdea29e3567c5e9155794e6ef9cc17be62` (1.1.7 update). Select binaries for the delivered controller generation and host architecture. Availability of an API does not establish support for every new arm or whole-robot system.

The reviewed [ROS 2 Humble package](https://github.com/RealManRobot/ros2_rm_robot/tree/711abedd48c6614f26fb4f7661db92f306ff05bd) is V1.7.1, based on controller 1.7.5, for Ubuntu 22.04. Its support table includes RM65, RM75, ECO62/63/65, RML63, GEN72 and RX75. GEN62 is a different model. Confirm the exact end-link and controller support table before selecting a launch configuration. A default real-hardware launch may enable trajectory execution. Use the shared commissioning guide before launching anything.

See [Arm commissioning and SDK selection](realman-arm-commissioning-and-sdk.md) and the [existing teaching-pendant reference](realman-robot-web-teaching-pendant-user-manual-v1.5.md).

## Complete supplied document and engineering details

[ECO series hardware manual — all 56 PDF pages](realman-source-library/complete-eco-manual.md). The full reference is readable inside the wiki, with an original-page view and searchable text for every page. It includes the material not repeated in this entry guide.

| Source section                                                | Full in-wiki reference                                                 |
| ------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Safety, responsibilities and warranty                         | [PDF 1–10](realman-source-library/complete-eco-manual.md#pdf-page-1)   |
| Composition, mounting, startup, teaching and shutdown         | [PDF 10–21](realman-source-library/complete-eco-manual.md#pdf-page-10) |
| Controller and tool wiring, I/O, external power and RS485     | [PDF 21–28](realman-source-library/complete-eco-manual.md#pdf-page-21) |
| ECO63 specifications, MDH, dynamics, workspace and load curve | [PDF 29–39](realman-source-library/complete-eco-manual.md#pdf-page-29) |
| ECO65 specifications, MDH, dynamics, workspace and load curve | [PDF 40–50](realman-source-library/complete-eco-manual.md#pdf-page-40) |
| FAQs, handling, maintenance, repair and disposal              | [PDF 51–56](realman-source-library/complete-eco-manual.md#pdf-page-51) |

### Exact-model parameter selection

For **ECO63**, start with [the applicable parameter chapter](realman-source-library/complete-eco-manual.md#pdf-page-29). Retain the adjacent dynamic tables, diagrams and load curves as part of the specification; the short table above is not the complete parameter set.

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

Source for this wired, read-only path: [ECO family manual, installation and teaching-pendant chapters \[ECO\]](realman-source-library/).

## Troubleshooting and FAQs

**The tool moves or drops when power is removed.** Check the exact brake arrangement below and the delivered revision. A soft brake is not a load-holding mechanical brake. Support the tool and payload and use the manufacturer's safe shutdown/transport posture; do not rely on power removal to hold every axis.

**Can a nearby family's URDF or force-sensor option be substituted?** No. Confirm link geometry, joint order, end-link revision, load curve, tool mass and controller support before planning. A force/torque sensor's full-scale range is not a permissible contact-force setting.

**The SDK connects but motion is not ready.** Model identity and readable status do not validate limits, calibration, stop behavior, tool center point or control-source arbitration. Complete the exact revision's commissioning and risk assessment before a bounded motion test.

## Downloads and technical documents

| Resource                                                                                             | Scope and use                                                                          |
| ---------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [Supplied manual/specification \[ECO\]](realman-source-library/)                                     | Exact supplied reference, with original PDF page ranges in the source library          |
| [Manufacturer manual downloads](https://develop.realman-robotics.com/en/robot4th/download/manual/)   | Select exact family and controller generation; newer files may differ                  |
| [Manufacturer model/CAD downloads](https://develop.realman-robotics.com/en/robot4th/download/model/) | Confirm model/end-link dimensions before mounting or simulation                        |
| [RM\_API2](https://github.com/RealManRobot/RM_API2)                                                  | C/C++/Python arm interfaces; version and architecture matching required                |
| [ROS 2 package](https://github.com/RealManRobot/ros2_rm_robot/tree/humble)                           | Supported model table and launch instructions; do not assume GEN62 or whole-S2 support |

Firmware replacement is outside this first-result procedure. Obtain the exact controller image and recovery instructions through the manufacturer delivery channel; no cross-model firmware is supplied here.

## References and validation

[ECO family manual, PDF pp. 29–40 \[ECO\]](realman-source-library/); official repositories and downloads linked above. Reviewed 22 November 2026. Software execution: **not run**. Hardware validation: **not run**. The published reference does not authorize operation on an unmatched revision; any unresolved delivery-specific mounting, power or software target keeps powered commissioning blocked.

[RealMan series index](./)
