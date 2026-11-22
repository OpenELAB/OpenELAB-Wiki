# RealMan arms: commissioning and SDK selection

{% hint style="info" %}
**Scope:** standalone RM65/RM75, RML63, RX75 and ECO families only where the exact delivered controller supports the selected package. RealBot-S2 requires its own interface SDK. GEN62 is not GEN72.
{% endhint %}

## Product overview

Use this shared procedure after reading the canonical exact-model guide. It establishes identity and version compatibility before development. The original [RM65](realman-rm65-series-user-manual-v1.2.0.md), [ECO65](realman-eco65-series-user-manual-v1.2.0.md) and [teaching-pendant](realman-robot-web-teaching-pendant-user-manual-v1.5.md) URLs remain the entry points for those products.

## Applications

Controller identity checks, reproducible SDK selection and initial host-to-arm communication. Motion commissioning is a separate stage with physical stop verification, calibrated tool/payload, confirmed joint limits and a documented workspace assessment.

## Specifications

| Layer             | Reviewed target                                                                                                                                   |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| RM\_API2 snapshot | `a810b9fdea29e3567c5e9155794e6ef9cc17be62`, 1.1.7 update                                                                                          |
| Python host       | Repository states Python 3.9+; Windows or supported Linux x86/Arm binary target                                                                   |
| ROS 2 snapshot    | `711abedd48c6614f26fb4f7661db92f306ff05bd`, V1.7.1, Ubuntu 22.04 / Humble, based on controller 1.7.5                                              |
| SDK license       | RM\_API2 root does not expose a license file in the reviewed file listing; do not assume redistribution terms. ROS 2 package declares Apache-2.0. |

Sources: [RM\_API2 instructions](https://github.com/RealManRobot/RM_API2/tree/a810b9fdea29e3567c5e9155794e6ef9cc17be62), [ROS 2 instructions/license](https://github.com/RealManRobot/ros2_rm_robot/tree/711abedd48c6614f26fb4f7661db92f306ff05bd).

## Hardware and connections

The supplied arm manuals describe 24 V DC power and factory wired teach-pendant access at `192.168.1.18`, with host example `192.168.1.100`. Match the actual delivery first. Controller I/O and tool connector pinouts are revision-specific. Isolate power before wiring; do not infer connector orientation from wire colors or reuse another family's mounting diagram.

Tool outputs documented at 1.5 A maximum are insufficient evidence for directly supplying the RMG22-65's stated 1.9 A rated / 5.7 A peak demand. Obtain the approved power arrangement before accessory connection.

## Software and development resources

Match four identifiers together: complete arm model, controller generation/software, tool/end-link variant and SDK/package snapshot. Force L/K and ROS `6f`/`6fb` names cannot be selected solely by the product title. The ROS support table distinguishes generation 3 and generation 4 software; simulation retains older geometry names in some cases.

The reviewed public ROS 2 README lists GEN72, not GEN62. Its RX75 dual-arm support does not establish support for the entire S2. The older [ROS 1 package](https://github.com/RealManRobot/rm_robot) targets Melodic/Noetic and must not be mixed into a Humble workspace.

## Complete model manuals and integration acceptance

[RM65 and RM75 hardware manual — all 58 PDF pages](realman-source-library/complete-rm65-rm75-manual.md)

[RML63 hardware manual — all 48 PDF pages](realman-source-library/complete-rml63-manual.md)

[RX series hardware manual — all 49 PDF pages](realman-source-library/complete-rx-manual.md)

[ECO series hardware manual — all 56 PDF pages](realman-source-library/complete-eco-manual.md)

[ECO62 specification sheet — all 4 PDF pages](realman-source-library/complete-eco62-specification.md)

[GEN62 specification sheet — all 3 PDF pages](realman-source-library/complete-gen62-specification.md)

[RMG22-65 parallel gripper manual V1.3 — all 53 PDF pages](realman-source-library/complete-rmg22-65-manual.md)

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

### Software evidence and reproducibility

Use the exact manufacturer repository, pinned commit/release and delivered controller support matrix already linked in this guide. Record host OS/architecture, controller firmware, arm model and force-sensor revision before selecting binaries or a launch file. A driver README support entry and a successful build are different from a verified hardware run. Keep first checks read-only and keep simulation configuration separate from real-hardware trajectory execution. This expansion adds source coverage and integration explanation; it does not claim any unperformed SDK or hardware test.

## Getting started

1. Complete the exact model guide's hardware/UI status check with all motion controls inactive. Record the reported model and controller software.
2. On a separate supported host, obtain the approved RM\_API2 snapshot. Keep the robot's production installation unchanged. The repository installation command is `python3 -m pip install Robotic_Arm`; record the resolved package version and binary architecture in an isolated environment rather than assuming that an unpinned newest package matches the arm.
3. Use the manufacturer's read-only software-information example below after confirming the supplied controller address and API port. This example creates a connection and queries information; it includes no motion, enable, calibration or fault-clear call.

{% code collapsedlinecount="10" %}
```python
from Robotic_Arm.rm_robot_interface import RoboticArm, rm_thread_mode_e

robot = RoboticArm(rm_thread_mode_e.RM_TRIPLE_MODE_E)
handle = robot.rm_create_robot_arm("192.168.1.18", 8080)
try:
    if handle.id < 0:
        raise RuntimeError("Controller connection failed")
    status, info = robot.rm_get_arm_software_info()
    if status != 0:
        raise RuntimeError(f"Software-information query failed: {status}")
    print(info)
finally:
    robot.rm_delete_robot_arm()
```
{% endcode %}

4. Compare the returned model/software with the label, UI and selected SDK support table. Keep the SDK version and result with the commissioning record. Do not continue to a movement demo merely because the connection succeeded.

**Expected result:** a successful information query for the correct arm and controller, with no commanded movement. This is the repository's software-information workflow with explicit error handling; it has not been executed here. Confirm `rm_delete_robot_arm` in the selected installed API before running a different SDK revision.

For ROS 2, first inspect the exact model's support/launch table and build instructions. Do not use a default `mode=real` launch for a first simulation. The repository states that `mode` defaults to real and trajectory execution defaults to enabled.

## Troubleshooting and FAQs

**The Python import fails:** check interpreter version, environment, package version and native library architecture before editing robot firmware.

**Connection fails:** check the UI works, approved IP/port, host subnet and whether another control source owns the connection. An S2 internal controller must not be bypassed with a second direct connection.

**Model/force link differs:** stop setup and compare controller generation, software and full model selector against the package's generation-specific support table. Do not replace a seven-joint vector with a six-joint example.

## Downloads and technical documents

| Resource                                                                                           | Purpose                                          |
| -------------------------------------------------------------------------------------------------- | ------------------------------------------------ |
| [Official SDK downloads](https://develop.realman-robotics.com/en/robot4th/download/redevelopment/) | API/JSON/ROS route by controller generation      |
| [RM\_API2](https://github.com/RealManRobot/RM_API2)                                                | Arm host APIs and examples                       |
| [ROS 2 package](https://github.com/RealManRobot/ros2_rm_robot/tree/humble)                         | Supported models, build and launch configuration |
| [Model/CAD downloads](https://develop.realman-robotics.com/en/robot4th/download/model/)            | Exact-model geometry and end-link assets         |
| [Supplied source library](realman-source-library/)                                                 | Manual page ranges and revision notes            |

## References and validation

Official resources above plus supplied RM65/RM75, ECO, RML63 and RX manuals, installation/hardware chapters. Reviewed 22 November 2026. Commands were source reviewed; dependency installation, compilation, SDK execution and hardware motion were **not run**.
