---
description: >-
  Distinguish AlienGo SDK v3.3.1 from the original normalized-command API,
  inspect pinned sources and retain unresolved power, firmware and stop
  requirements.
---

# Unitree AlienGo: legacy SDK lineages, interfaces and compatibility

{% hint style="info" %}
**Manufacturer reference: Unitree AlienGo.** No exact OpenELAB robot listing/SKU has been verified. Developer onboard-PC access is an option described by the manufacturer, not an entitlement inferred for every unit. This guide's first result inspects public source without connecting to or powering a robot.
{% endhint %}

AlienGo is a 12-actuator quadruped with depth perception, visual odometry and separate high-level and joint-level control interfaces. Two observed legacy SDK lineages contain materially different command structures. Choosing the exact delivered firmware contract is necessary before interpreting a packet or considering control. [Official AlienGo](https://www.unitree.com/aliengo)

## Product overview <a href="#product-overview" id="product-overview"></a>

The product page describes joint compound force control, dual encoders, internal joint wiring, air cooling, torque/reducer protection and four foot-end sensors. Its developer version adds an onboard PC and open interfaces for payload modules. A supported mechanical payload is not automatically an electrically supported camera, arm or LiDAR configuration.

Depth cameras, a visual odometry camera and optional single/multiline LiDAR serve different purposes. Depth measures nearby geometry, odometry estimates motion, and an installed navigation stack must use those observations. Neither the phrase “industrial level” nor a stabilization demonstration establishes an ingress, functional-safety or autonomous-operation certification.

## Applications <a href="#applications" id="applications"></a>

* **Existing-robot maintenance:** identify the controller image and SDK lineage before analyzing historical exported logs or restoring an old application.
* **Perception research:** distinguish depth images from odometry, retain calibration and evaluate the actual environment and sensor availability.
* **Payload integration planning:** compare mount, payload mass, electrical budget and available developer interfaces without assuming a complete mobile-manipulator bundle.
* **Joint-control and model research:** use the official description/simulation resources as models; physical motor control still requires the exact robot's software, limits and protection. [Manufacturer functions and developer interfaces](https://www.unitree.com/aliengo), [official model catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)

## Specifications <a href="#specifications" id="specifications"></a>

| Manufacturer parameter        | Published value                          | Interpretation                                                                   |
| ----------------------------- | ---------------------------------------- | -------------------------------------------------------------------------------- |
| Mass                          | 21.5 ±1 kg **without battery**           | Do not compare directly with a battery-inclusive robot mass                      |
| Standing / folded size, L×W×H | 0.65×0.31×0.60 m / 0.60×0.31×0.15 m      | Static dimensions, not a collision or swing-leg envelope                         |
| Motors / foot sensors         | 12 / 4                                   | State-array capacity may be larger than physical count                           |
| Load / maximum walking speed  | 13 kg / >1.5 m/s                         | Continuous load and combined speed/load conditions are not specified             |
| Climbing / endurance          | ≤25° / 2.5–4.6 h                         | No common test conditions given; not a simultaneous guarantee                    |
| Battery capacity              | 12600 mAh                                | Does not establish charge voltage, wiring or interchangeable battery type        |
| Output rails                  | 5,12,19 V and BAT 24–30 V                | Listed **outputs**, not a charger or external supply-input recipe                |
| Depth / odometry cameras      | Two depth sets / one visual-odometry set | The listed sensor configuration does not verify every delivered option           |
| Depth sensing                 | Minimum 0.11 m; up to 1280×720           | Global-shutter/wide-view description; no universal lighting/material performance |

[Official specification table and perception sections](https://www.unitree.com/aliengo). The page reports closed-loop odometry drift below 1% and delay below 6 ms without sufficient test conditions for a system guarantee. Its field-angle text is malformed, so no corrected numerical field of view is inferred. “Movement Control: Ubuntu” and “Environment Sensing: Ubuntu-ROS” do not identify a release or kernel.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

The detailed product text lists **two Ethernet, two USB 3.0, one USB 2.0 and one RS485** interface. Its shorter summary lists only Ethernet and USB 3.0. Treat that difference as an inventory check on the actual configuration, not permission to assume hidden connectors. The developer PC and payload interfaces require delivered-option confirmation. No exact connector pinout, polarity, per-rail current, mounting drawing or approved charger was established from these resources. External power and charging are therefore not specified here. [Interface and output descriptions](https://www.unitree.com/aliengo)

Both motor-side and output-side encoders are listed. Reducer-wear and physical torque protection are manufacturer-described features, not replaceable by an application-side torque clamp. Low-voltage, temperature, short-circuit and overcharge alarms are listed without qualified thresholds. Do not substitute A1's or Go1's battery protection values for AlienGo.

Wireless emergency-stop and fall protection are listed, but an exact stop timing, mode-dependent authority, power-loss result or guaranteed holding behavior is not established. A1/Go1 remote manuals do not apply by analogy. Before any physical session, obtain the AlienGo unit's startup, mechanical support, remote/firmware, emergency-stop and shutdown instructions. No button sequence or unsupported stand/hold procedure is provided in this source-bounded guide.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Two different AlienGo contracts <a href="#two-different-aliengo-contracts" id="two-different-aliengo-contracts"></a>

| Contract                         | `unitree_legged_sdk` v3.3.1                           | Original `aliengo_sdk`                                                    |
| -------------------------------- | ----------------------------------------------------- | ------------------------------------------------------------------------- |
| Pinned commit                    | `20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd`            | `583cc616828c23580c691aa0c16aff6b9447ef73`                                |
| Support evidence                 | README names AlienGo and A1; excludes Laikago and Go1 | README describes PC-to-AlienGo-controller communication                   |
| Observed version                 | v3.3.1                                                | ChangeLog latest entry V1.2.2, 2020-08-12                                 |
| High-level selector              | `0x00`                                                | `0x00`                                                                    |
| Motor field names                | `q`, `dq`, `tauEst`                                   | `position`, `velocity`, `torque`                                          |
| High-level motion representation | `HighCmd` velocity/yaw fields in that release         | `forwardSpeed`, `sideSpeed`, `rotateSpeed`, `bodyHeight` normalized −1..1 |
| UDP API                          | `SetSend`/`Send` style                                | `Send` overloads; default local 8008, target `192.168.123.10:8007`        |
| Root license read                | BSD-3-Clause                                          | Mozilla Public License 2.0                                                |

[v3.3.1 README](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/README.md), [state header](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/include/unitree_legged_sdk/comm.h), [original README](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/README.md), [ChangeLog](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/ChangeLog.md), [original command/state header](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/include/aliengo_sdk/comm.hpp), [original UDP header](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/include/aliengo_sdk/udp.hpp). Identical level bytes do **not** prove layout, units, binary ABI or firmware compatibility. Normalized speed values must not silently become SI m/s or rad/s. Historical Laikago names in old changelog/library text do not establish Laikago support.

The v3.3.1 low-state `tick` comment uses **microseconds**. Its motor array has 20 slots although AlienGo has 12 motors. Joint order is FR,FL,RR,RL, each hip/thigh/calf. AlienGo constants give hip −0.873..1.047, thigh −0.524..3.927 and calf −2.775..−0.611 rad; these are software constants rather than a safe path, calibrated hardware envelope or authorization to move. A1 constants in the same repository differ. [Joint order](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/include/unitree_legged_sdk/quadruped.h), [AlienGo constants](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/include/unitree_legged_sdk/aliengo_const.h)

Both READMEs list Boost ≥1.5.4, CMake ≥2.8.3 and LCM ≥1.4.0. The inspected v3.3.1 CMake uses C++11 and an amd64 shared library, LCM and pthread. Those historical dependencies do not establish support on a modern OS, ARM host or modern ROS2 DDS middleware. The current v3.8.6 legged-SDK README explicitly excludes AlienGo, even though some enum/header names remain. [v3.3.1 build](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/CMakeLists.txt), [Go1-only v3.8.6 notice](https://github.com/unitreerobotics/unitree_legged_sdk/blob/4539a6c10dfbc9781cea6fcb7d51bc6ddc6f71e1/README.md)

The official [shared A1/AlienGo app page](https://www.unitree.com/app/a1_aliengo/) describes imagery, tracking, model selection, SLAM and 3D display. Its historical beta download references are not proof of a current package/firmware match. The pinned [ROS catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md) lists a 12-DoF AlienGo model and a separate AlienGo-with-Z1 model; the latter does not make an arm part of the base robot. Low-level Gazebo controllers and real-robot bridges are distinct resources, with distinct deployment risks and version constraints.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: identify an AlienGo API lineage without executing it <a href="#first-result-identify-an-aliengo-api-lineage-without-executing-it" id="first-result-identify-an-aliengo-api-lineage-without-executing-it"></a>

Prerequisites: a browser and the linked official source files. Keep the robot disconnected. Do not install LCM, run a vendor example or interpret a live packet during this checkpoint.

1. Open the pinned [v3.3.1 README](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/README.md) and the [original AlienGo README](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/README.md). Record two distinct repository/commit identifiers. The A1 sport\_mode ≥1.19 parenthetical is not an observed universal AlienGo firmware requirement.
2. In [v3.3.1 `comm.h`](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/include/unitree_legged_sdk/comm.h), find `MotorState`, `HighCmd`, `tick` and `HIGHLEVEL`. Record the field names, µs tick comment and `0x00` selector.
3. In [original `comm.hpp`](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/include/aliengo_sdk/comm.hpp), find `MotorState` and `HighCmd`. Locate `forwardSpeed`, `sideSpeed`, `rotateSpeed`, `bodyHeight` and their normalized range. Compare the motor field names with step 2.
4. Inspect the [original UDP header](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/include/aliengo_sdk/udp.hpp). Locate local/target defaults and `Send`; classify them as source defaults, not observed network settings.
5. Record `AlienGo: two non-equivalent source contracts; decoder/firmware lineage unresolved until delivered image is identified`. A proposed decoder using normalized commands as SI values fails this inspection.

**Expected result:** a small compatibility record that distinguishes field names, units, UDP API and exact commits, without creating any robot connection. If files appear identical, check the repository name and commit in each link. If the installed application cannot be tied to either contract, retain that gap rather than trying both against the robot.

For later offline log analysis, preserve the decoder and firmware identity with the exported data. Require a first real sample, advancing tick and fresh local receive time; reject uninitialized, repeated, stale, backward or nonfinite records. A source-level field match is not CRC validation, packet provenance, time synchronization or proof that hardware is stopped.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Why are plausible values decoded incorrectly?** Compare complete layout and units first. The two SDKs share a selector but use different fields and motion scaling. Use the producing software's exact contract; do not reinterpret bytes merely until numbers look reasonable.

**Why does v3.8.6 contain an AlienGo name but fail the support check?** The README explicitly limits that branch to Go1. A surviving enum is not supported firmware evidence. Return to the identified historical application baseline without running either version.

**Why does a receive-named example require caution?** Inspect its send path and control loop. The v3.3.1 multi-PC receive example also transmits; the position example commands joints. Neither is a read-only status tool. [Receive example](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/examples/multi_pc_udp_recv.cpp), [position example](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/examples/example_position.cpp)

**Can BAT 24–30 V be used as a charger specification?** No. It is listed as an output rail. Charger voltage/current, pack limits, connector polarity and charge sequence remain unqualified. Do not import Go1/A1 values.

**Are protection and navigation functions guaranteed on every unit?** No such guarantee is established. Check developer version, actual sensors/PC, installed image and matching stop instructions. Manufacturer performance claims do not prove autonomous safety or recovery behavior on a modified payload.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                                                                             | Purpose and exact scope                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| [Official AlienGo page](https://www.unitree.com/aliengo)                                                                                                                                                                                                                                                                             | Specification, interfaces, sensing, protection, alarms and developer options                                     |
| [v3.3.1 README](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/README.md)                                                                                                                                                                                                       | AlienGo/A1 support, exclusions, dependencies, build/usage sections                                               |
| [v3.3.1 state header](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/include/unitree_legged_sdk/comm.h) and [AlienGo constants](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/include/unitree_legged_sdk/aliengo_const.h) | Historical layout, units, joint constants; not a current firmware match                                          |
| [Original AlienGo README](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/README.md)                                                                                                                                                                                                    | Separate SDK installation/environment and PC/ROS usage sections                                                  |
| [Original ChangeLog](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/ChangeLog.md)                                                                                                                                                                                                      | Version history through V1.2.2; not proof of a delivered unit's version                                          |
| [Original state/command](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/include/aliengo_sdk/comm.hpp) and [UDP declarations](https://github.com/unitreerobotics/aliengo_sdk/blob/583cc616828c23580c691aa0c16aff6b9447ef73/include/aliengo_sdk/udp.hpp)                                 | Normalized command fields, API and endpoint defaults                                                             |
| [Official A1/AlienGo app page](https://www.unitree.com/app/a1_aliengo/)                                                                                                                                                                                                                                                              | Feature and model-selection reference; beta paths are historical                                                 |
| [Official ROS catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)                                                                                                                                                                                                       | Description/simulation packages, controllers, dependencies, build, worlds and examples; physical bridge separate |

### Functional source index <a href="#functional-source-index" id="functional-source-index"></a>

| Source section                                                        | Engineering coverage on this page                                                      |
| --------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Product: sportiness, stability, joint control and impact descriptions | Overview/applications; physical demonstrations are not a commissioning test            |
| Product: openness, developer PC and interfaces                        | Hardware and API lineage; payload access is option dependent                           |
| Product: depth, odometry and optional LiDAR                           | Specifications/applications; unqualified FOV and odometry conditions remain explicit   |
| Product: full parameter table, power outputs, alarms and protection   | Specifications/hardware; no charger or remote-stop protocol inferred                   |
| SDK READMEs and build files                                           | Version/dependency/license scope above; no install/build sequence executed             |
| Header and example resources                                          | Layout/scaling/order comparison and browser first result; active send paths identified |
| ROS/app resources                                                     | Simulation versus physical bridge and feature versus delivered image distinctions      |

The manufacturer's [depth/odometry section](https://www.unitree.com/aliengo) supplies the source illustrations; the [official model catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md) supplies the model-package link. No exact AlienGo user/battery/remote manual, electrical pinout, charger, mechanical mounting drawing or firmware compatibility matrix was successfully established for this guide. A1 or Go1 chapters are not substitutes.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed **2026-11-24**. Observed software baselines are v3.3.1 commit `20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd` and original `aliengo_sdk` commit `583cc616828c23580c691aa0c16aff6b9447ef73`, whose ChangeLog reaches V1.2.2. No claim is made that both work with the same firmware.

**Validation:** source/document inspection only; SDK installation, build, shared-library loading, vendor examples, ROS, robot networking, power, motion and flashing **not run**. This source-bounded draft supports compatibility analysis. Live commissioning remains blocked on exact developer hardware, firmware/API lineage, battery/charger/pinout, mounting and effective model-specific startup/stop instructions.

**Related documentation:** [Unitree model and development directory](./).
