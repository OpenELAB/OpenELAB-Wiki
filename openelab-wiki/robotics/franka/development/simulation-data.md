# Franka simulation and research-data acceptance

{% hint style="info" %}
**Scope:** offline model/sensor validation followed by a separate data-acceptance plan. Simulation examples below are specific to the cited ROS 2 documentation; they are not launch instructions for real robot controllers.
{% endhint %}

## Match the embodiment and tools

The [manufacturer models page](https://franka.de/models-and-simulation) separates FR3 Arm v2, stationary FR3 Duo, TMR v0.2 and Mobile FR3 Duo v0.2. It also distinguishes a bare system from the **reference setup** with two Robotiq 2F-85 grippers, D405 wrist cameras and ZED Mini head camera. Match the delivered gripper, mounting orientation, joint names, camera frames and calibration; do not substitute a Panda, FP3 or generic seven-axis URDF.

| Target                   | Official description/model route                                                                                     |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------- |
| FR3 Arm v2               | [fr3v2](https://github.com/frankarobotics/franka_description/tree/main/robots/fr3v2)                                 |
| FR3 Duo                  | [fr3\_duo](https://github.com/frankarobotics/franka_description/tree/main/robots/fr3_duo)                            |
| TMR prototype            | [tmrv0\_2](https://github.com/frankarobotics/franka_description/tree/main/robots/tmrv0_2)                            |
| Mobile FR3 Duo prototype | [mobile\_fr3\_duo\_v0\_2](https://github.com/frankarobotics/franka_description/tree/main/robots/mobile_fr3_duo_v0_2) |

## First offline result

On a host configured using the **Jazzy** documentation's installation and dependency instructions, source the built workspace and use its explicitly simulated Duo entry:

{% code collapsedlinecount="10" %}
```bash
source install/setup.bash
ros2 launch franka_gazebo_bringup gazebo_fr3_duo_example.launch.py
```
{% endcode %}

The [Jazzy Gazebo guide](https://frankarobotics.github.io/docs/doc/franka_ros2_jazzy/franka_gazebo/franka_gazebo_bringup/doc/index.html#fr3-duo-example-with-gazebo) documents this command and the optional `with_sensors:=true` path with the required vision/manipulation package. The manufacturer also links a **Humble** route for mobile reference examples. Follow that branch's dependency/launch instructions rather than copying the desktop Duo command onto the delivered mobile computer.

Keep real-controller drivers and teleoperation clients stopped during an offline simulation. Do not convert a simulated planning success into a permission to use real hardware.

**Expected result:** the intended virtual embodiment appears with the correct two arms, tool links and configured sensor frames. Compare joint names and transforms against the physical BOM and reference drawings. Verify package/asset licensing and record the exact package commits. This simulation was **not run** during the wiki review.

## Data collection requires more than a running topic

For later supervised physical data collection, define the accepted configuration first: robot and controller versions, software commits, tool/load, all camera names, resolution/encoding, calibration revision, frame graph and timestamp source. For dual arms, verify physical left/right mapping and use a consistent cross-device time base.

1. Complete the robot's commissioning and state-reading acceptance before recording demonstrations.
2. Inspect a short sample from each required state and camera stream. Confirm units, array sizes, finite values, timestamp continuity and source-device validity.
3. Verify camera frames/encoding and view the actual image content. A reported topic frequency does not prove correct exposure, decoding or calibration.
4. Record a bounded, authorized sample using the delivered recorder or selected framework. Stop and finalize it before reading/copying the artifact.
5. Check required streams, duration/counts, sample content, synchronization, missing frames and checksums. Retain the original until backup/export verification is complete.

**Expected result:** a small readable dataset sample with a version/BOM/calibration record and explicit acceptance criteria. Do not describe it as successful imitation learning or policy deployment without the corresponding training/evaluation evidence.

## GELLO and LABS boundaries

The [GELLO Duo guide](../gello-duo.md) establishes leader identity/calibration before follower synchronization. The manufacturer also links [Franka LABS](https://github.com/frankarobotics/labs) for reference teleoperation/data workflows. Treat its supported embodiments, software versions and deployment instructions as a separate integration choice, not an automatic replacement for the supplied 2025 training material.

Simulation assets can omit joint friction, cable behavior, protective-device effects or other real limitations. Validate the physical stop/authority and tool/payload behavior separately; do not use a virtual collision check as the complete safety case.

## Sources and validation

[Models and simulation](https://franka.de/models-and-simulation), branch-specific Gazebo documentation and official model repositories above; [FR3 brochure, October 2025, PDF pp. 6–9](../source-library/); [Franka GELLO Duo brochure, PDF p. 1](../source-library/). Reviewed 22 November 2026. Documentation and source checks only. Software installation, compilation, live robot communication, calibration and physical tests: **not run**. No dataset or policy result has been fabricated.

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
