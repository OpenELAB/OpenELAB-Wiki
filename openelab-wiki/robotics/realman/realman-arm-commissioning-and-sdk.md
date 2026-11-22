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
| [Supplied source library](realman-source-library.md)                                               | Manual page ranges and revision notes            |

## References and validation

Official resources above plus supplied RM65/RM75, ECO, RML63 and RX manuals, installation/hardware chapters. Reviewed 22 November 2026. Commands were source reviewed; dependency installation, compilation, SDK execution and hardware motion were **not run**.
