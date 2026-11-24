---
description: >-
  Preserve Laikago and separately named Laikago Pro history, classify official
  ROS model and simulation resources, and avoid unsupported physical SDK
  transfers.
---

# Unitree Laikago and Laikago Pro: historical models and ROS resources

{% hint style="info" %}
**Historical manufacturer family reference: Laikago and Laikago Pro.** No exact OpenELAB robot listing/SKU is verified. Laikago Pro is a distinct historical model named by Unitree, not a silently substituted label for base Laikago. Physical specifications and firmware compatibility must be qualified separately for an existing unit.
{% endhint %}

Laikago is Unitree's early commercial quadruped platform, documented in manufacturer history and official ROS model/simulation resources. Those resources make a useful starting point for preserving an older project, but they do not establish a compatible physical SDK, charging procedure or Laikago Pro hardware mapping. [Official company history](https://www.unitree.com/about/), [Go1 page's historical timeline](https://www.unitree.com/go1)

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree's English history places a reconstructed Laikago platform in September 2017 and describes dedicated motors, drives, master control, mechanics and control-system work following the earlier XDog prototype. Another official history page names October 2017 for public retail. The common supported year is **2017**; the month should remain source-specific. The Go1 historical timeline identifies a **Laikago Pro first shipment in 2018**. This establishes a separately named historical model, not its electrical, dimensional or software equivalence to Laikago. [English history](https://www.unitree.com/about/), [Chinese history](https://www.unitree.com/operate/robot/), [Go1 timeline](https://www.unitree.com/go1)

For an inherited robot, keep physical Laikago, physical Laikago Pro, an old ROS package and a modern model-catalog entry as four distinct identities until the unit's records connect them. A mesh that resembles a robot is insufficient evidence for control gains, mass distribution, encoder zero, limits or firmware.

## Applications <a href="#applications" id="applications"></a>

* **Historical engineering study:** follow the transition from prototype motor/control development to a reconstructed commercial platform without assigning later models' capabilities to it.
* **Project preservation:** identify the exact repository revision, dependencies and architecture assumptions in a legacy ROS workspace before attempting migration.
* **Model inspection:** study description-package structure, mesh/URDF/Xacro roles and controller organization using public source browsing.
* **Migration planning:** separate display/model resources, low-level simulator controllers, ROS messages and any physical communication component. A successful display or simulation is not a physical driver qualification.

The guide does not provide a retail selection recommendation, present-day support promise or a command sequence for an unqualified robot.

## Specifications <a href="#specifications" id="specifications"></a>

| Item                                                               | Evidence established                                              | Boundary                                                                            |
| ------------------------------------------------------------------ | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| Laikago historical platform                                        | 2017 manufacturer history                                         | Sources differ on September platform introduction versus October retail description |
| Laikago Pro                                                        | Named 2018 shipment in official timeline                          | No verified Pro/base hardware-difference table                                      |
| Model degrees of freedom                                           | Official `unitree_ros` catalog lists 12 for `laikago_description` | Model catalog value; not qualification of every Pro configuration                   |
| Description resources                                              | Mesh, URDF and Xacro named in official Laikago ROS README         | Individual inertias, transmissions and calibration not independently validated here |
| Physical mass, dimensions, payload, speed, battery and input power | Not established by an exact-model manual in this source set       | Do not reuse A1, AlienGo or Go1 numbers                                             |
| Ingress, safety or industrial certification                        | Not established                                                   | Historical demos and generic quadruped descriptions are not certification           |

[Pinned official model catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md), [pinned Laikago ROS README](https://github.com/unitreerobotics/laikago_ros/blob/a3e659847d18fdafe18b17fa3a1e2c4b447954a2/README.md). Keeping unknown values explicit prevents a historical model reference from becoming a false hardware specification.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

No exact Laikago/Laikago Pro battery, charger, electrical pinout, mounting drawing, remote manual or qualified startup/stop contract was successfully established. **Do not power, charge or wire an inherited unit from this guide.** Obtain its model label, serial/revision records, original battery/charger approval, connector drawing and delivered controller documentation first. No voltage, polarity, stop button or stable-hold behavior is inferred from another Unitree robot.

Physical differences must also be considered when using a model: mounting and link geometry, encoder direction/offset, actuator/transmission revisions, foot/contact assumptions, mass/inertia and available sensors can invalidate controller assumptions. These are engineering checks for a future qualified comparison, not claims that a particular difference exists between Laikago and Pro.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Original Laikago ROS resource <a href="#original-laikago-ros-resource" id="original-laikago-ros-resource"></a>

The inspected `laikago_ros` README is pinned to commit **`a3e659847d18fdafe18b17fa3a1e2c4b447954a2`**. It names **Ubuntu 16.04/ROS Kinetic** and **Ubuntu 18.04/ROS Melodic** as test environments, recommends **Gazebo8**, explicitly warns against Gazebo7 compatibility, and mentions architecture-specific x86/ARM library selection. These are historical environment statements, not a verified modern toolchain. [Pinned README](https://github.com/unitreerobotics/laikago_ros/blob/a3e659847d18fdafe18b17fa3a1e2c4b447954a2/README.md)

| README section                         | What it documents                                                    | Interpretation                                                         |
| -------------------------------------- | -------------------------------------------------------------------- | ---------------------------------------------------------------------- |
| Environment/dependencies/configuration | ROS/Gazebo paths, workspace/library paths and architecture selection | A path export does not validate a binary ABI or hardware transport     |
| Build                                  | Catkin workspace build                                               | Not executed; do not copy into an unknown robot's system               |
| `laikago_controller`                   | Position, velocity and torque joint-control modes                    | Control functionality, not passive state observation                   |
| `laikago_msgs`                         | High/low command and state messages; build-order warning             | Message definitions alone do not establish a physical wire contract    |
| `laikago_description`                  | Mesh, URDF, Xacro and RViz display resource                          | A display model does not identify the real robot's firmware            |
| `laikago_gazebo`                       | World launch, servo stand-up and external-force examples             | The servo and disturbance examples deliberately change simulated state |

The modern official `unitree_ros` README at **`157ff950351e5f535e03c5d85a16b7d594b3dbcc`** separately lists Laikago among complete Gazebo controller configurations. It distinguishes low-level joint simulation from high-level walking and from a real-robot bridge. It also describes stand/servo, pose and external-force publishers. Preserve that scope when evaluating an inherited ROS project; do not interpret “real robot” wording at repository level as exact Laikago Pro firmware support. [Pinned catalog, controllers and examples](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)

### SDK exclusions matter <a href="#sdk-exclusions-matter" id="sdk-exclusions-matter"></a>

The inspected `unitree_legged_sdk` **v3.8.6** README supports Go1 only and explicitly excludes Laikago. The actual **v3.3.1** README supports AlienGo/A1 and also explicitly excludes Laikago. Following a redirect to an older tag therefore does not solve Laikago support. Neither SDK's packet selector, motor fields, UDP target or safety model may be transferred to this family. [v3.8.6 support notice](https://github.com/unitreerobotics/unitree_legged_sdk/blob/4539a6c10dfbc9781cea6fcb7d51bc6ddc6f71e1/README.md), [v3.3.1 support notice](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/README.md)

The Laikago ROS root license was not independently read successfully; repository metadata is not sufficient to state redistribution terms for all code/assets/binaries. Follow its actual license and dependency notices before reuse. This page links source resources and provides original interpretation without repackaging them.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: classify a legacy Laikago project using public source <a href="#first-result-classify-a-legacy-laikago-project-using-public-source" id="first-result-classify-a-legacy-laikago-project-using-public-source"></a>

Prerequisites: a browser, with no robot or ROS process connected. This is a source-preservation checkpoint, not a simulator launch or a physical connection test.

1. Open the [pinned original Laikago ROS README](https://github.com/unitreerobotics/laikago_ros/blob/a3e659847d18fdafe18b17fa3a1e2c4b447954a2/README.md). Record the exact commit and both historical Ubuntu/ROS pairs. Find the Gazebo8 versus Gazebo7 statement.
2. Locate the `laikago_description`, `laikago_controller`, `laikago_msgs` and `laikago_gazebo` sections. Classify them as description, joint controller, messages and simulation respectively. Mark servo/force examples as active.
3. Open the [pinned modern model catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md). Locate the Laikago row and `12` model DoF. Read the distinction between complete Gazebo setups and display-only resources, then between simulation and a physical bridge.
4. Inspect the actual [v3.3.1 exclusion](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/README.md) and [v3.8.6 exclusion](https://github.com/unitreerobotics/unitree_legged_sdk/blob/4539a6c10dfbc9781cea6fcb7d51bc6ddc6f71e1/README.md). Record both as excluding Laikago; a name elsewhere in source is not an override.
5. Create a project note with `model role`, `repository/commit`, `ROS/Gazebo generation`, `active examples`, and `physical protocol unresolved`. Keep Laikago Pro separately unresolved unless exact Pro documentation establishes the mapping.

**Expected result:** a useful dependency/role map and an explicit rejection of the two unsupported physical SDK assumptions. Nothing is installed, built or launched. If the project you inherited differs, first compare repository revision, package names and hardware records. Do not repair an environment mismatch by trying a Go1/A1/AlienGo control example.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Why can I display Laikago but not establish hardware compatibility?** RViz uses description data. It does not verify actuators, communication protocol, firmware, calibration or stop behavior. Keep model and physical-driver validation separate.

**Why does an old workspace mention Gazebo8?** The original README specifically targets that generation and warns about Gazebo7. A modern package with a similar name does not establish binary/API compatibility. First document the existing dependencies offline; migration remains a separate tested task.

**Does SDK 3.3.1 support Laikago because a current page links to it?** No. The actual README explicitly excludes Laikago. Use the contents of the pinned release rather than a redirect, generic family name or old library filename.

**Is Laikago Pro just a renamed Laikago?** The manufacturer names Pro separately. No equivalence or complete difference table was established. Do not copy base model parameters or commissioning steps to Pro without exact documentation.

**Does an unavailable old product path prove retirement or current unavailability?** No. A missing web path does not establish commercial status, stock, support entitlement or safe replacement parts. This reference makes none of those claims.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                              | Purpose                                                                              |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| [Official English history](https://www.unitree.com/about/)                                                                                                                                                                                            | XDog research, company formation and reconstructed Laikago platform context          |
| [Official Chinese product history](https://www.unitree.com/operate/robot/)                                                                                                                                                                            | 2017 retail timeline; preserve date-context difference                               |
| [Official Go1 historical timeline](https://www.unitree.com/go1)                                                                                                                                                                                       | Separately named Laikago Pro shipment in 2018                                        |
| [Original Laikago ROS README](https://github.com/unitreerobotics/laikago_ros/blob/a3e659847d18fdafe18b17fa3a1e2c4b447954a2/README.md)                                                                                                                 | All environment, configuration, build, package and simulation sections indexed above |
| [Modern official model/simulation catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)                                                                                                    | Laikago 12-DoF listing, package/controller roles and simulation limits               |
| [SDK v3.3.1](https://github.com/unitreerobotics/unitree_legged_sdk/blob/20929b54030c0d8ca4e7ac49ec2a02c447cb9fcd/README.md) / [v3.8.6](https://github.com/unitreerobotics/unitree_legged_sdk/blob/4539a6c10dfbc9781cea6fcb7d51bc6ddc6f71e1/README.md) | Explicit exclusions, not Laikago developer packages                                  |

The manufacturer's history pages provide contextual illustrations, and the linked description resources identify model assets. No exact Laikago/Pro manual chapter set, approved electrical drawing, verified physical API or delivered firmware package was found readable in this source set. The A1 manual's inherited Laikago metadata is not an applicable Laikago manual. No separate download or guessed model retail URL is invented.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed **2026-11-24**. Exact Laikago ROS and modern model-catalog commits are printed above. Historical timelines establish the model names and their context; they do not establish present-day retail readiness or physical compatibility.

**Validation:** source inspection only. SDK/ROS installation, build, simulation, physical transport, charging, motion and flashing **not run**. This historical family guide remains a source-bounded draft for engineering preservation. The read-only first result is usable without hardware; physical commissioning requires exact model-specific records and remains unresolved.

**Related documentation:** [Unitree model and development directory](./).
