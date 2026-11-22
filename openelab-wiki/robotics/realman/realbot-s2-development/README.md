# RealBot-S2: development and interface guide

{% hint style="info" %}
**Scope:** RealBot2.0 / S2 general customer interface, supplied V1.3 dated 24 August 2026. Match the robot version, scene and delivered SDK. This is not an L2 or RMC-DA-LIII control guide.
{% endhint %}

## Product overview

Develop independent customer applications against the documented public interfaces. The manufacturer owns the base software and hardware drivers; keep customer code in a separate workspace such as `~/s2_customer_ws`. Do not modify `/rm_app` installation files, safety parameters, calibration or internal driver connections.

## Applications

Status dashboards, camera validation, odometry inspection and accepted data collection. Motion interfaces require the exact delivery contract, trained on-site operators and verified stops; topic discovery alone is not authorization or compatibility evidence.

## Specifications

| Interface                                   | Type                                  | Boundary                                                                   |
| ------------------------------------------- | ------------------------------------- | -------------------------------------------------------------------------- |
| `/robot_slave/states`                       | `std_msgs/msg/String`                 | Low-frequency JSON overview; validate V1.3 schema                          |
| `/chassis/odom`                             | `nav_msgs/msg/Odometry`               | Chassis feedback; verify frame, time and covariance                        |
| `/motor_state`, `/chassis/wheel_encoder`    | `sensor_msgs/msg/JointState`          | Map by name; units/counters from delivery appendix                         |
| `/diagnostics`, `/chassis_driver/lf_report` | `diagnostic_msgs/msg/DiagnosticArray` | May have multiple publishers/subsystems                                    |
| `/battery_state/bms1`, optional `bms2`      | `sensor_msgs/msg/BatteryState`        | ROS fraction differs from aggregate battery percentage                     |
| `/robot/command`                            | `rm_robot_interfaces/srv/StringCmd`   | Authorized arms/body/head control; JSON inside `data`                      |
| `/cmd_vel`                                  | `geometry_msgs/msg/Twist`             | Authorized S2 chassis control; not a generic differential-drive assumption |

Source: [S2 interface V1.3, PDF pp. 11–24, 35–49, 69–70 \[S2\_API\]](../realman-source-library/).

## Hardware and connections

Use the [S2 hardware guide](../realbot-s2-guide.md) for LAN identity and stop controls. The production graph uses Ubuntu 22.04 / Humble with Fast DDS and a delivered profile. An external workstation requires explicit project network, domain, RMW, interface SDK and security configuration. Do not change `ROS_LOCALHOST_ONLY` or robot network settings just because a workstation cannot see topics.

## Software and development resources

The version source is `/rm_app/rm_robot_ws/version.txt`; match the delivered SDK to it. Load the supplied ROS installation overlays in order. Query installed message files or `ros2 interface show` where available. Public RM\_API2 and the arm ROS repository do not replace the S2 `rm_robot_interfaces` SDK.

| Tutorial                                                                                | First result                                                 |
| --------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| [1. Read-only environment and discovery](s2-read-only-environment.md)                   | Version, interfaces and publisher/QoS baseline               |
| [2. State, odometry and sensor validity](s2-state-and-sensors.md)                       | Correct units, fresh data and usable image stream            |
| [3. Data acceptance and controlled-motion boundaries](s2-data-and-motion-acceptance.md) | Readable closed MCAP and a delivery-specific acceptance plan |

## Complete supplied document and engineering details

[RealBot2.0 / S2 interface manual V1.3 — all 70 PDF pages](../realman-source-library/complete-s2-interface-manual.md). The full reference is readable inside the wiki, with an original-page view and searchable text for every page. It includes the material not repeated in this entry guide.

| Source section                                                                      | Full in-wiki reference                                                             |
| ----------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| Document scope, versions, hardware profiles and scenes                              | [PDF 1–7](../realman-source-library/complete-s2-interface-manual.md#pdf-page-1)    |
| Autostart readiness, lifecycle, runtime domains and development routes              | [PDF 8–14](../realman-source-library/complete-s2-interface-manual.md#pdf-page-8)   |
| Types, SI units, QoS, timestamps and JSON conventions                               | [PDF 14–16](../realman-source-library/complete-s2-interface-manual.md#pdf-page-14) |
| Aggregate-state fields, complete JSON schema and state enumerations                 | [PDF 16–24](../realman-source-library/complete-s2-interface-manual.md#pdf-page-16) |
| Head/waist and arm service contracts, units, schema, response handling and stopping | [PDF 24–35](../realman-source-library/complete-s2-interface-manual.md#pdf-page-24) |
| Chassis topics, wheel/odometry/battery data, collision and speed-control contracts  | [PDF 35–43](../realman-source-library/complete-s2-interface-manual.md#pdf-page-35) |
| Arm/hand high-frequency fields, validation and control                              | [PDF 44–50](../realman-source-library/complete-s2-interface-manual.md#pdf-page-44) |
| Cameras, encoding, IMU/LiDAR/navigation and data recording                          | [PDF 50–54](../realman-source-library/complete-s2-interface-manual.md#pdf-page-50) |
| Operations, lifecycle, logs, evidence and safety/failure behavior                   | [PDF 54–60](../realman-source-library/complete-s2-interface-manual.md#pdf-page-54) |
| Client workspace, dependencies, complete examples, deployment and self-test         | [PDF 61–66](../realman-source-library/complete-s2-interface-manual.md#pdf-page-61) |
| Custom/standard interface definitions and full quick reference                      | [PDF 66–70](../realman-source-library/complete-s2-interface-manual.md#pdf-page-66) |

### Interface routing and access levels

The V1.3 document separates general read-only interfaces, project options, authorized controls and project-specific agreements. A node or topic appearing in the ROS graph does not by itself make it a supported public API. Record software version, hardware profile and scene (`standard`, `local` or `teleop`) before comparing an observed graph with the contract. External ROS hosts additionally require the delivered message SDK and project-approved DDS/network settings.

| Need                          | Interface / message                                                    | Important contract                                                                             |
| ----------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Low-frequency system overview | `/robot_slave/states`, `std_msgs/msg/String`                           | Validate the JSON schema; local receipt time is needed for freshness                           |
| Chassis motion feedback       | `/chassis/odom`, `nav_msgs/msg/Odometry`                               | Verify frames, timestamp, covariance, available degrees of freedom and drift                   |
| Wheel and encoder data        | `/motor_state`, `/chassis/wheel_encoder`, `sensor_msgs/msg/JointState` | Match by name; units, count direction and wrap depend on delivery                              |
| Diagnosis                     | `/diagnostics`, `/chassis_driver/lf_report`                            | Multiple publishers may exist; filter by diagnostic identity                                   |
| Battery                       | `/battery_state/bms1`, optional `/battery_state/bms2`                  | `BatteryState.percentage` is typically 0–1; aggregate JSON percent is 0–100                    |
| Collision event               | `/chassis/collision`, `std_msgs/msg/Bool`                              | Event-triggered `true`; no periodic `false` clearance message                                  |
| Head / waist                  | `/mcap/body`, `rm_robot_interfaces/msg/BodyData`                       | S2 waist has 4 joints and head 2; ROS state is in radians                                      |
| Slave arms                    | `/mcap/slave_arm_left`, `/mcap/slave_arm_right`, `ArmSlaveData`        | Seven named joints; check hardware/source validity, not publication alone                      |
| Master arms                   | `/mcap/master_arm_left`, `/mcap/master_arm_right`, `ArmMasterData`     | Raw position units are not normalized by this generic contract                                 |
| Camera health                 | `/robot_driver/camera_hz_state`, `Camerastate`                         | Health/frequency does not prove image validity                                                 |
| Camera pixels / encoded video | Project camera topic table                                             | H.264/H.265 bytes carried in `Image` are not raw pixels                                        |
| Chassis command               | `/cmd_vel`, `geometry_msgs/msg/Twist`                                  | Project authorization, authority arbitration, timeout and recovery apply                       |
| Arm/head/waist command        | `/robot/command`, `rm_robot_interfaces/srv/StringCmd`                  | The string wraps a separate JSON business contract; transport success is not motion completion |

### Data contracts that affect real applications

The aggregate-state schema requires `arm_left`, `arm_right`, `body`, `head` and `system`. Arm position/enable/error arrays have **7** entries; waist arrays **4** and head arrays **2**. Camera status is optional and must be matched by camera **name**, rather than an array index. Preserve unknown enum values as unknown, accept compatible extra fields, and reject missing required fields, wrong types and wrong array lengths. A raw subsystem error is not a universal diagnostic code.

The aggregate position fields and JSON motion targets use integer **0.001° (millidegrees)**, while the typed slave-arm/body state uses **radians**. The documented conversion is `command_mdeg = round(state_rad × 180 / π × 1000)`. “Milliradian” wording in parts of the English source conflicts with that degree symbol and formula; do not implement that wording as a radian scale. Validate every joint name/order and unit before using data in a planner or a controller.

For `ArmSlaveData`, the outer header timestamp is robot-node publication time, not necessarily the controller's original sampling time. The nested joint-state header can be empty. `joint_state.effort` is currently filled with zeros, so it is not measured torque; `joint_acc` is derived from velocity samples. Pose frames and wrench calibration/units are not frozen as a general force/pose-control contract. Gripper `0` is not proof of an absent device or a fully closed grip. The `rps_*` arrays need an exact end-device protocol for valid entries, scaling and status semantics.

`ArmMasterData` is a teleoperation data path: the generic source does not finish radian normalization for master positions, and current velocity/effort values are not valid speed/torque measurements. A newly stamped message can still carry stale upstream data. Do not infer a working master arm, a safe master/slave map or a trajectory input merely from message frequency.

### QoS, readiness and camera/recording acceptance

Readiness includes an expected endpoint, matching installed type, compatible QoS, data within an agreed timeout, valid content, continuous timestamps where applicable, and the required operating authority. Query the chassis lifecycle state read-only; do not automatically configure/activate production nodes, restart core services or change parameters as a discovery step.

Arm high-frequency topics use SensorDataQoS (Keep Last 5, Best Effort, Volatile) and a documented nominal 5 ms / 200 Hz publication interval. Those figures are not a hard real-time guarantee. Measure received rate and gaps and keep callbacks light. For cameras, record topic/type, encoding, calibration/resolution, rate, timestamp and a decoded sample. An encoded H.26x payload needs a matching decoder before a pixel-processing path such as `cv_bridge`.

For a data session, save the robot/profile/scene/SDK versions, exact interface definitions, source/read timestamps, QoS, frame IDs, units, named channel order and a bounded recording. Check that the MCAP opens, contains the intended channels, spans the intended interval, has valid sample content and can be decoded. A file on disk or an upload-complete indication alone does not establish an acceptable training dataset. Recording, upload and remote-operation control APIs remain project-specific unless explicitly delivered.

### Command, collision and recovery boundaries

The JSON routing uses left arm `device=0`, right arm `device=1`, waist `device=2` and head `device=3`. The waist/head contract repeats the device in the payload; the arm payload does not require that extra field. Exact schemas, all fields, response classifications and source examples are retained in full in the source reader. Preserve the difference between a completed ROS service exchange, a parsed business response and observed completion in the correct state source.

The chassis gives manual/teleoperation channels higher priority than `/cmd_vel`; a client must yield rather than raise its rate to compete. The source recommends continuous 20 Hz client publication and describes a 1.0 s command-expiry condition, but expiry is not a guaranteed 1.0 s physical stopping time or a specified braking distance. The client must deliberately stop its own non-zero target generation on task end or failure.

Latch collision events in the client. The source states that a new velocity message can clear an internal collision-stop flag, including a zero message; this does not establish that the physical hazard has been removed. There is no `false` collision message to wait for. Recovery requires an on-site inspection, valid diagnostics and continuously updated motor state, stopped competing sources and an explicitly authorized recovery sequence. Do not replay a cached pre-stop target after a collision, physical emergency stop or network restoration. The complete stopping, low-speed direction-verification and recovery procedures remain in the cited V1.3 pages; this entry remains a read-only first-result guide.

## Getting started

1. Record software version, hardware/camera profile, scene and delivery appendix.
2. Complete the first tutorial on the robot itself with read-only discovery; do not start a second chassis or arm driver.
3. Check type, publisher, QoS, freshness, validity and missing-option behavior for every required interface.
4. Validate the aggregate JSON using V1.3 §7.2; use strongly typed feedback for algorithms instead of treating display fields as safety measurements.
5. Only after this baseline passes, design a separate authorized motion acceptance with stop commands prepared and physical emergency stop attended. Do not use the first-run procedure for autonomous operation.

**Expected result:** a version-matched customer interface baseline and valid status data. A ROS service reply or continuously published topic does not prove physical task completion or valid upstream sensor data.

## Troubleshooting and FAQs

**Unexpected field scaling:** standard state messages generally use SI units, but aggregate joint values and S2 command joint arrays use **millidegrees (0.001°)**. The supplied English translation incorrectly calls these “milliradians” in places. Its explicit conversion is `round(rad × 180 / π × 1000)`, which yields millidegrees. Do not use `rad × 1000`.

**Timestamp looks fresh but master data is stale:** the robot-side publisher can continue stamping a message while upstream master-arm data has stopped. Require the delivery's upstream-validity indicators; the V1.3 generic master positions are not normalized radians and cannot be used for mapping/control.

**A control feature is missing:** check the delivery's interface whitelist and hardware/scene first. Internal nodes, discovered services and parameters are not automatically stable public APIs.

## Downloads and technical documents

[Complete supplied V1.3 interface document \[S2\_API\]](../realman-source-library/) and [S2 user manual \[S2\]](../realman-source-library/). Obtain the matching message SDK, control appendix, camera table and any recording/remote-access contract through the project delivery. No public generic S2 SDK package was verified during this review.

## References and validation

[S2 interface V1.3, PDF pp. 1–70 \[S2\_API\]](../realman-source-library/), especially §§2, 7–12, 15–17. Reviewed 22 November 2026. ROS commands, customer-node compilation, live communication and physical tests: **not run**. Delivery-specific motion limits, frame definitions and optional interfaces remain prerequisites for their corresponding operation.
