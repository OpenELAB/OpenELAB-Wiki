# Diana FS FCI: supported configurations and version review

{% hint style="info" %}
Scope: supplied “How to Use FCI on Diana7FS” V1.3, Industrial V3.3.0, FCI version V0.18.2. This is the Agile Robots FCI adaptation, distinct from Franka FR3 setup.
{% endhint %}

## Supported source configurations

The supplied document establishes FCI support for specific Diana FS configurations. It is more precise than assuming every robot named Diana 7, every Diana hardware generation or a six-axis Thor has the same implementation.

| Configuration         | Documented scope                                                    |
| --------------------- | ------------------------------------------------------------------- |
| Diana3FS              | Mechanical/algorithm Diana3\_L\_V1.1.20260119; Industrial V3.3.0    |
| Diana7FS              | Mechanical/algorithm Diana7\_FS\_V2\_3.20260119; Industrial V3.3.0  |
| Diana7G2\_FS          | Mechanical/algorithm Diana7\_G2\_V1\_0.20260119; Industrial V3.3.0  |
| Shared source entries | ControlBox-FS-3.2T.20250107 and joint firmware V4.2.7-2-ga59ea07    |
| Feature scope         | Arm FCI interfaces; gripper and suction-cup interfaces are excluded |

The table is a source-version record, not an instruction to flash those files onto an unmatched system. Adaptation tables contain model-specific joint/motion limits, including differences between normal and G2 joint ranges. Sources: [How to Use FCI on Diana7（English version）V1.3-20260209.pdf, PDF pp. 1, 11–12, 16](../source-library/).

## Network and service behavior

The workstation connects to **controller Ethernet A**, factory server `192.168.10.75`, TCP port `1337`. Real-time commands/state use the separately specified UDP/1 kHz loop and require an accepted real-time host/network. Do not transfer Franka's X5/C2 instructions to this cabinet. Server configuration is preinstalled and maintained by Agile Robots; the manual does not ask users to edit it.

The pendant's FCI switch is red when disabled and green when enabled. Enabling/disabling changes control authority and can disconnect or terminate a client. Pendant/program/API motion has exclusive-control restrictions; a client may read state while a conflicting motion request is rejected. Do not use automatic error recovery to reset an unresolved stop. Sources: [How to Use FCI on Diana7（English version）V1.3-20260209.pdf, PDF pp. 4–10, 13–15](../source-library/).

## Resolve the client-version ambiguity

The cover identifies **FCI V0.18.2**, while many API/example links inside the PDF point to libfranka **0.15.0**, and other links point to moving upstream documentation. These are not a verified all-version compatibility matrix. Obtain the supported client build/commit and server protocol/model configuration from the delivery's Agile Robots support record before compiling or connecting a client. Do not assume the latest stock libfranka or the FR3 System Image matrix is the correct Diana pairing.

[Official libfranka source](https://github.com/frankarobotics/libfranka) and [current installation documentation](https://frankarobotics.github.io/docs/doc/libfranka/docs/installation.html) identify the upstream project. They do not independently certify this Diana adaptation. Some old PDF documentation paths have moved; use the current official documentation for reference, with the exact client/version resolved separately.

## First result: inspect the adaptation record

1. With the responsible operator and a commissioned, clear cell, inspect the actual arm/CB-FS labels and installed software/model/algorithm/control-box/joint firmware.
2. Compare them to the applicable source table and record the FCI feature/service state. Do not enable FCI solely to discover the robot version.
3. If already enabled under the accepted procedure, inspect **System Settings / Franka API** status/parameter page. Record the current mode and client connection state without starting control.
4. Resolve the supported client release/protocol and Linux/real-time/network requirements before any client test. If the match is unavailable, stop at this UI/configuration record.
5. A later approved state-only client test must use the matched build and explicit address, handle finite reads/errors and issue no motion/recovery command. A real-time controller experiment requires its own validated limits and acceptance.

**Expected result:** a configuration/service-state record and an explicitly verified or still-unresolved client pairing. No real-time command is proposed as ready while the V0.18.2/older-link ambiguity remains. Sources: [How to Use FCI on Diana7（English version）V1.3-20260209.pdf, PDF pp. 6–15](../source-library/).

## Migration and differences from FR3

The manual's V3.2-or-earlier migration note requires current configurations rather than retention of old files. Treat it as a controlled upgrade with complete backups and safety acceptance, not an automatic prerequisite for reading this wiki. See [migration planning](backup-updates.md).

For Franka Research 3 use its [own FCI/ROS 2 guide](../../franka/development/fci-ros2.md). Sharing the FCI concept does not make network ports, UI, limits, arm dynamics, gripper support or software-version selection interchangeable.

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                                                        | Coverage     |
| -------------------------------------------------------------------------------------------------------------- | ------------ |
| [Diana 7 FCI guide V1.3](../source-library/complete-how-to-use-fci-on-diana7-english-version-v1-3-20260209.md) | 17 PDF pages |

### Exact Diana FCI configuration

All seventeen pages are retained, including preparation, client connection, activation, examples and the source's version conditions. Separate the Diana FS configuration supported by this guide from other Diana/Thor hardware and from the FR3 product. The cover's FCI V0.18.2 and older linked libfranka 0.15.0 example do not establish one client version for every delivered V3.3 controller.

Record the exact arm/controller/FS capability, server/interface version, approved client library and host network/kernel requirements. Reconcile their support statement before selecting a binary or running a control example. A familiar Franka API class name does not transfer FR3 pinouts, Hand support, network addresses or safety assumptions to Diana.

Start with the documented read-only connection/state result and check actual joint count/order, units, frames and errors. Activation, control callbacks, torque/Cartesian targets and example launches require a reviewed motion procedure and real-time/loss-of-command behavior. A sample executable completing or the UI showing FCI active does not establish a validated force-control experiment.

The original material, including its older links and examples, stays separate from the [Franka FCI development guide](../../franka/development/fci-ros2.md). No FCI package was compiled, launched or connected to hardware in this review.

### Source chapter map

| Source section                                     | Full detail                                                                                                |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| 1. Introduction                                    | [PDF 3](../source-library/complete-how-to-use-fci-on-diana7-english-version-v1-3-20260209.md#pdf-page-3)   |
| 2. Preparation                                     | [PDF 3](../source-library/complete-how-to-use-fci-on-diana7-english-version-v1-3-20260209.md#pdf-page-3)   |
| 3. FCI Client Development Environment Installation | [PDF 12](../source-library/complete-how-to-use-fci-on-diana7-english-version-v1-3-20260209.md#pdf-page-12) |
| 4. FCI Client Development Guidance                 | [PDF 13](../source-library/complete-how-to-use-fci-on-diana7-english-version-v1-3-20260209.md#pdf-page-13) |
| 5. Disclaimer                                      | [PDF 16](../source-library/complete-how-to-use-fci-on-diana7-english-version-v1-3-20260209.md#pdf-page-16) |

## References and validation

Reviewed 22 November 2026. Documentation/source review only. SDK installation, compilation, robot communication, calibration, simulation, welding and physical safety tests: **not run**.
