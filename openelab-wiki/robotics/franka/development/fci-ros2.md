# Franka FCI, libfranka and ROS 2: version-matched development

{% hint style="info" %}
**First result:** read arm state over the approved wired FCI network. This guide contains no motion-control example. Match the installed System Image, server, libfranka and ROS versions before building or connecting.
{% endhint %}

## Interface and network selection

Use arm **X5** for initial browser/UI access and Control **C2** for the FCI workstation's shop-floor Ethernet link. A working browser page or Internet connection does not validate FCI networking. Configure separate non-overlapping networks as specified by the installed manual and the [official FCI setup guide](https://frankarobotics.github.io/docs/doc/libfranka/docs/getting_started.html). Do not copy a sample FCI address into a delivered Duo/Mobile network without checking its topology.

FCI arm control/state exchange operates at 1 kHz. Real-time control requires a suitable Linux workstation, the supported library/server pair and measured network/kernel performance. Wi-Fi, generic virtual networking and a successful ping do not establish those properties. The [system requirements](https://frankarobotics.github.io/docs/doc/libfranka/docs/system_requirements.html) explain the required host/network characteristics.

## Choose versions before installation

| Installed FR3 System Image | Manufacturer matrix libfranka range | Notes                                      |
| -------------------------- | ----------------------------------- | ------------------------------------------ |
| ≥5.9.0                     | ≥0.18.0                             | Matrix robot/gripper server pair 10 / 3    |
| ≥5.7.2 and <5.9.0          | ≥0.15.0 and <0.18.0                 | Matrix server pair 9 / 3                   |
| Older images               | Consult exact matrix row            | Do not reuse a current-image build blindly |

Source: [manufacturer compatibility matrix](https://franka.de/fr3-compatibility-matrix) and [libfranka compatibility](https://frankarobotics.github.io/docs/doc/libfranka/docs/compatibility_matrix.html), reviewed 22 November 2026. Check the exact released library's support as well; an unbounded “newest” package is not a reproducibility plan.

For the current supported routes, the manufacturer matrix pairs ROS 2 **Humble with Ubuntu 22.04** and its applicable `franka_ros2` 2.x range, or **Jazzy with Ubuntu 24.04** and its applicable 3.x range. Verify the row for the installed image, selected branch and mobile embodiment. Some old-image rows in the overview table contain inconsistent distro/Ubuntu labels; use the branch-specific documentation and seek an exact supported combination instead of copying those rows. Windows is not the documented supported route.

The 5.10 operating manual includes a legacy clone example using libfranka 0.10.0. It conflicts with the current ≥5.9 matrix requirement above and is **not** the build selection used here. Do not execute broad uninstall commands or downgrade robot software merely to reproduce that old example.

## Sources, licensing and supported targets

| Resource                                                                                                      | Reviewed scope                                                                         |
| ------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| [libfranka 0.19.0](https://github.com/frankarobotics/libfranka/tree/0.19.0)                                   | Example release snapshot `4df37dd2b527f41ef34b76d6d4d3805864b09993`; Apache-2.0        |
| [Official libfranka installation](https://frankarobotics.github.io/docs/doc/libfranka/docs/installation.html) | Current release packages, checksums, C++ and Python paths                              |
| [franka\_ros2 Jazzy](https://github.com/frankarobotics/franka_ros2/tree/jazzy)                                | Reviewed branch snapshot `8c946641bdedaf20c35604d8bc5a809117e4ed6c`; Apache-2.0        |
| [Humble documentation](https://frankarobotics.github.io/docs/doc/franka_ros2_humble/docs/index.html)          | Select for matching Humble/delivery environment, including documented prototype routes |
| [Jazzy documentation](https://frankarobotics.github.io/docs/doc/franka_ros2_jazzy/docs/index.html)            | Select for supported Jazzy host/package route                                          |

Official Python bindings are named `pylibfranka`; do not infer support from an unrelated similarly named third-party package. A mobile prototype may require a delivered mobile-capable branch/build beyond a standalone arm example.

## First working result

Prerequisites: completed physical commissioning, trained operator, clear workcell/tool travel, verified stop functions, supported host/kernel/network and matching FCI feature/license. Activating FCI and opening brakes are state-changing commissioning actions and must follow the installed operating manual with responsible on-site personnel. Do not automate safety resets to make an example connect.

1. Record the System Image and robot/gripper server versions, selected libfranka release/commit, host OS and actual C2 address. Match them to the compatibility source.
2. Obtain/build the selected release in an isolated development workspace using its [official installation instructions](https://frankarobotics.github.io/docs/doc/libfranka/docs/installation.html). Pin the source/release and verify supplied release checksums. Ensure examples are built if using the executable below.
3. Have the on-site operator prepare the robot for FCI using the exact installed-version procedure. App execution and FCI control are exclusive; stop competing controllers first.
4. From the selected build directory, substitute the **actual** FCI controller address and run the upstream state-reading example:

{% code collapsedlinecount="10" %}
```bash
./examples/echo_robot_state ACTUAL_FCI_CONTROLLER_ADDRESS
```
{% endcode %}

5. Compare the reported identity/mode, joint-state array size, tool/load configuration and plausible state values with the commissioned robot. Save a redacted small sample and version record; do not continue to a motion demo just because it prints data.

**Expected result:** the upstream example prints arm state and finishes after its finite read loop, without issuing an arm motion-control command. The [0.19.0 source](https://github.com/frankarobotics/libfranka/blob/0.19.0/examples/echo_robot_state.cpp) uses `robot.read(...)`; it is not a generic network-performance or hardware-commissioning test. Code has been source reviewed, not executed here.

## Interpret state and failures carefully

The seven joint positions `q` are radians and velocities `dq` are rad/s; Cartesian translation values in the transform use meters. Use the exact `RobotState` API documentation for frame, array layout and force/torque semantics rather than guessing from a printed JSON sample. Arm torque sensing does not imply Franka Hand accepts real-time force-control commands.

**Timeouts:** inspect C2 routing, physical Ethernet, library/server match, host real-time setup and competing control sources. A ping alone is insufficient; do not suppress exceptions or raise collision thresholds to make the experiment run.

**SLP-C/Watchman blocks FCI:** behavior changes by System Image; 5.10 documentation explicitly distinguishes older releases. Resolve the application safety configuration with the responsible safety operator. Do not delete protective functions as an installation step.

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

## References and validation

Official resources above; [FR3 brochure, October 2025, PDF pp. 6–8](../source-library/); [System Startup training, 21 October 2025, slide 12](../source-library/); [Operating Manual 5.10](https://franka.de/hubfs/Operating%20Manual%20Franka%20Research%203_5.10_R02216_1.3_EN.pdf), §§10.1–10.5. Reviewed 22 November 2026. Documentation and source checks only. Software installation, compilation, live robot communication, calibration and physical tests: **not run**.

Diana FCI adaptation: the supplied Agile Robots V1.3 manual documents specific Diana FS configurations. Use the [Diana FS FCI version/configuration review](../../agile-robots/development/diana-fci.md) for that implementation. The FR3 System Image matrix and C2/X5 instructions on this page do not establish Diana client compatibility, network ports, dynamics or gripper support.
