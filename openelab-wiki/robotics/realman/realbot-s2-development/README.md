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

Source: [S2 interface V1.3, PDF pp. 11–24, 35–49, 69–70 \[S2\_API\]](../realman-source-library.md).

## Hardware and connections

Use the [S2 hardware guide](../realbot-s2-guide.md) for LAN identity and stop controls. The production graph uses Ubuntu 22.04 / Humble with Fast DDS and a delivered profile. An external workstation requires explicit project network, domain, RMW, interface SDK and security configuration. Do not change `ROS_LOCALHOST_ONLY` or robot network settings just because a workstation cannot see topics.

## Software and development resources

The version source is `/rm_app/rm_robot_ws/version.txt`; match the delivered SDK to it. Load the supplied ROS installation overlays in order. Query installed message files or `ros2 interface show` where available. Public RM\_API2 and the arm ROS repository do not replace the S2 `rm_robot_interfaces` SDK.

| Tutorial                                                                                | First result                                                 |
| --------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| [1. Read-only environment and discovery](s2-read-only-environment.md)                   | Version, interfaces and publisher/QoS baseline               |
| [2. State, odometry and sensor validity](s2-state-and-sensors.md)                       | Correct units, fresh data and usable image stream            |
| [3. Data acceptance and controlled-motion boundaries](s2-data-and-motion-acceptance.md) | Readable closed MCAP and a delivery-specific acceptance plan |

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

[Complete supplied V1.3 interface document \[S2\_API\]](../realman-source-library.md) and [S2 user manual \[S2\]](../realman-source-library.md). Obtain the matching message SDK, control appendix, camera table and any recording/remote-access contract through the project delivery. No public generic S2 SDK package was verified during this review.

## References and validation

[S2 interface V1.3, PDF pp. 1–70 \[S2\_API\]](../realman-source-library.md), especially §§2, 7–12, 15–17. Reviewed 22 November 2026. ROS commands, customer-node compilation, live communication and physical tests: **not run**. Delivery-specific motion limits, frame definitions and optional interfaces remain prerequisites for their corresponding operation.
