# Franka development and training: choose your workflow

{% hint style="info" %}
**Training scope:** the supplied Startup, Desk and World decks are from October 2025. Use them as a learning sequence alongside the operating manual for the installed System Image. Keep the FR3 hardware revision, desktop/mobile embodiment, tool and software versions explicit.
{% endhint %}

## Learning and development routes

| Guide                                                            | First result                                                |
| ---------------------------------------------------------------- | ----------------------------------------------------------- |
| [1. System startup and first connection](system-startup.md)      | Identity, UI access and configuration checklist             |
| [2. Desk, Settings and Watchman](franka-desk.md)                 | Correct local roles, tool profile and status interpretation |
| [3. Franka World, registration and software](franka-world.md)    | Correct organization/robot association and update plan      |
| [4. FCI, libfranka and ROS 2](fci-ros2.md)                       | Version-matched wired state-reading path                    |
| [5. Simulation and research-data acceptance](simulation-data.md) | Correct offline model and a traceable dataset sample        |

## Separate the interfaces

* **Franka UI/Desk:** browser interface to the robot, normally through arm X5 for first connection.
* **Settings:** local configuration, logs, users and software management, subject to role permissions.
* **Watchman:** safety configuration/viewing. Editing belongs to qualified safety personnel and requires validation.
* **Franka World:** cloud organization, robot ownership/software and account roles, separate from local robot users.
* **FCI/libfranka:** wired robot state and low-level arm control through Control C2; not the X5 browser network.
* **ROS 2/GELLO/LABS:** version- and embodiment-specific integrations on top of the relevant controller interfaces.

The supplied brochure mentions Desk API operations that can open brakes, activate FCI and clear safety violations. Those are control/administrative actions, not benign discovery calls. No such operation is needed to read this wiki or validate its links.

## Version and source rules

The Desk slides use older product-manual page numbers. In particular, the “Safety” slide repeats a log-download chapter reference. Follow the semantic section in the **matching current operating manual**, not that page number alone. The current [Franka World guide](https://download.franka.de/franka-world-manual/) describes World 2.0 organization roles and a different interface from the 2025 screenshots.

Use the [compatibility matrix](https://franka.de/fr3-compatibility-matrix) and each repository's branch/release support table. The current System Image 5.10 operating manual still includes a legacy `libfranka 0.10.0` clone example; it is not the selected build target for a ≥5.9 image, for which the compatibility matrix requires libfranka ≥0.18.0. The development guide explains the supported selection rather than copying the stale command.

## Acceptance before physical experiments

Record model/serial/hardware revision, System Image, controller/server version, library/package commit, host OS/kernel, robot/host network, tool/load, calibration and stop configuration. Complete status and communication checks before motion. Treat simulation, source review, compiled software and hardware tests as separate evidence.

## Sources and validation

[System Startup training, 21 October 2025, slides 3–13](../source-library/); [Franka Desk training, 22 October 2025, slides 3–20](../source-library/); [Franka World training, 22 October 2025, slides 3–7](../source-library/); [Operating Manual 5.10](https://franka.de/hubfs/Operating%20Manual%20Franka%20Research%203_5.10_R02216_1.3_EN.pdf), §§3, 6–10; official web sources linked above. Reviewed 22 November 2026. Documentation and source checks only. Software installation, compilation, live robot communication, calibration and physical tests: **not run**.

For Diana/Thor Industrial V3.3, use the separate [Agile Robots training and development route](../../agile-robots/development/). Its six training decks, controller networks and Industrial API conventions differ from the Franka training above.

## Complete source coverage and engineering details

The supplied material is now readable inside the wiki. The complete readers retain every original page, drawing, table, example and notice; the guidance below explains how to use them for this model or workflow.

| Complete in-wiki source                                                             | Coverage      |
| ----------------------------------------------------------------------------------- | ------------- |
| [FR3 Arm v2.1 hardware manual R02210/1.2](../source-library/complete-fr3-hardware/) | 118 PDF pages |
| [Franka Hand manual R50010/1.2](../source-library/complete-hand.md)                 | 36 PDF pages  |
| [Franka training 1 — System Startup](../source-library/complete-startup.md)         | 14 slides     |
| [Franka training 2 — Franka Desk](../source-library/complete-desk.md)               | 21 slides     |
| [Franka training 3 — Franka World](../source-library/complete-world.md)             | 8 slides      |

### Keep hardware, software and research evidence aligned

Select the exact workflow before a package or launch: Desk/task programming, FCI/libfranka, ROS integration, simulation, data collection and leader/follower teleoperation have different prerequisites. Preserve hardware labels, Control/System Image, SDK/repository commit, host/toolchain, installed tool and calibrated frames. A current library release is not a universal match for an older delivered image; use the official compatibility matrix linked in this series.

For simulation, verify joint names/order, joint and actuator limits, base/tool transforms, geometry and the selected model revision. A visually plausible model does not verify collision geometry, inertia or controller behavior. For data, retain units, frame IDs, timestamps/time base, sample validity, calibration and software/hardware versions; inspect actual samples and decoding instead of accepting only file size or a successful recording command.

For any real controller connection, start with an identified read-only state result. Activation, homing, servo/torque examples, follower synchronization and mobile-base launches require their own attended procedure. Record software and hardware tests separately; this expansion does not claim any unperformed compile, simulation or robot test.
