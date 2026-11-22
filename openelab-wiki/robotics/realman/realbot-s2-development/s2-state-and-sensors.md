# S2 tutorial: state, odometry and sensor validity

{% hint style="info" %}
**Target:** V1.3 S2 public status contracts and the installed, version-matched message definitions. All checks are read-only. A published message is not proof that its upstream device is healthy.
{% endhint %}

## Prerequisites

Complete [environment discovery](s2-read-only-environment.md). Obtain the profile's camera/interface table and unit/frame appendix. For each stream record its actual topic, type, publisher, QoS, expected frequency, timestamp source and validity conditions.

## Decode the aggregate overview correctly

`/robot_slave/states` carries JSON in `std_msgs/msg/String`. V1.3 requires `arm_left`, `arm_right`, `body`, `head` and `system`. Arm position/enable/error arrays have 7 elements; body arrays have 4; head arrays have 2. Validate types, required fields, array sizes and finite/range-valid values before accepting a frame. Unknown fields may be added; unknown enumerations should remain unknown, not be mapped to a nearby value.

| Value                              | Meaning/handling                                                     |
| ---------------------------------- | -------------------------------------------------------------------- |
| Aggregate joint `position`         | Integer millidegrees, 0.001°; not radians                            |
| Aggregate battery `percent`        | 0–100                                                                |
| Standard `BatteryState.percentage` | Typically 0–1 fraction; confirm delivery behavior                    |
| `system.cameras[]`                 | Optional; match by `name`; missing/empty means no camera-status data |
| Aggregate timestamp                | No source timestamp; track local message receipt time                |
| Zero temperature/branch voltage    | May mean unavailable; do not use as protection data                  |

Use V1.3 §7.2's complete JSON Schema for validation, not this overview table as a replacement. On parse/schema failure or timeout, reject the frame and inhibit decisions that depend on it. Source: [S2 interface V1.3, PDF pp. 17–24 \[S2\_API\]](../realman-source-library/).

## Validate strongly typed chassis and arm data

{% code collapsedlinecount="10" %}
```bash
timeout 15 ros2 topic info /chassis/odom --verbose --no-daemon --spin-time 5
timeout 15 ros2 topic echo /chassis/odom --once --no-daemon --spin-time 5
timeout 15 ros2 topic info /motor_state --verbose --no-daemon --spin-time 5
timeout 15 ros2 topic echo /diagnostics --once --no-daemon --spin-time 5
```
{% endcode %}

Check odometry `header.frame_id`, `child_frame_id`, timestamp progression, stationary drift and covariance against the delivery. Do not fuse a pose merely because the topic is nonempty. Map wheel/encoder `JointState` arrays by `name`; do not assume counter units or rollover behavior. Filter diagnostics by subsystem name and allow multiple publishers.

The slave-arm streams `/mcap/slave_arm_left` and `/mcap/slave_arm_right` use `ArmSlaveData`, commonly SensorDataQoS (Best Effort, Volatile, depth 5) with a nominal 200 Hz publisher. Verify actual QoS/frequency; 200 Hz is not a hard real-time guarantee. Slave joint positions are radians and velocities rad/s. Outer timestamps are robot-side publication times; `effort` is currently zero-filled, not measured torque. Acceleration is an estimate. Pose reference frames and wrench units/directions are not frozen for generic control.

Master-arm position units have not been normalized in the V1.3 generic contract. Do not use `/mcap/master_arm_*` for joint display, trajectory calculation or master-slave control until the delivered normalized-unit contract exists. A fresh outer timestamp does not prove fresh upstream master data. Source: [S2 interface V1.3, PDF pp. 35–37, 43–48 \[S2\_API\]](../realman-source-library/).

## Validate one delivered camera stream

1. Select one channel from the delivered camera table. Discover the actual topic and inspect type/publisher/QoS; do not type a placeholder camera name as if it were a real topic.
2. Read the installed message definition and camera table's encoding, resolution, frame rate, calibration version and timestamp source.
3. Measure topic frequency and bandwidth in a bounded observation window using `ros2 topic hz` and `ros2 topic bw` for that actual topic. Check content with the delivery-supported viewer/decoder.
4. For raw pixels, confirm image encoding/step and matching `CameraInfo`. For JPEG, use the documented compressed-image path. Some S2 profiles put H.264/H.265 bytes in `sensor_msgs/Image.data`; decode the video stream before image processing rather than passing it directly to `cv_bridge`.
5. Match `/robot_driver/camera_hz_state` arrays using `camera_names`, verify equal array lengths and cross-check with real image frames. Camera-health frequency is not image acceptance.

**Expected result:** one actual delivered image stream decodes with correct resolution/calibration and continuous valid timestamps, and a small baseline records topic/type/QoS and observed rate. Missing optional cameras should produce a controlled “unavailable” state. Source: [S2 interface V1.3, PDF pp. 50–52, 67–68 \[S2\_API\]](../realman-source-library/).

## Troubleshooting and acceptance limits

**CLI receives but application does not:** compare offered/requested QoS and installed message definitions. High-rate callbacks should be lightweight and allow frame loss.

**Array lengths or units change after an upgrade:** reject mismatched data, retain the version evidence, compare the SDK and repeat interface acceptance. Do not repair by silently truncating arrays.

**Navigation/IMU/BEV topics appear:** these are not general public S2 interfaces in V1.3. Obtain their project contract, TF, calibration and validity definitions before integration.

## Sources and validation

[S2 interface V1.3, PDF pp. 14–24, 35–37, 43–54, 67–70 \[S2\_API\]](../realman-source-library/). Reviewed 22 November 2026. Live telemetry, image decoding and hardware validity checks: **not run**. These are acceptance instructions, not reported robot measurements.

## Complete interface contract and acceptance details

[RealBot2.0 / S2 interface manual V1.3 — all 70 PDF pages](../realman-source-library/complete-s2-interface-manual.md). For the full interface map, see the [S2 development guide](./).

### Data contracts that affect real applications

The aggregate-state schema requires `arm_left`, `arm_right`, `body`, `head` and `system`. Arm position/enable/error arrays have **7** entries; waist arrays **4** and head arrays **2**. Camera status is optional and must be matched by camera **name**, rather than an array index. Preserve unknown enum values as unknown, accept compatible extra fields, and reject missing required fields, wrong types and wrong array lengths. A raw subsystem error is not a universal diagnostic code.

The aggregate position fields and JSON motion targets use integer **0.001° (millidegrees)**, while the typed slave-arm/body state uses **radians**. The documented conversion is `command_mdeg = round(state_rad × 180 / π × 1000)`. “Milliradian” wording in parts of the English source conflicts with that degree symbol and formula; do not implement that wording as a radian scale. Validate every joint name/order and unit before using data in a planner or a controller.

For `ArmSlaveData`, the outer header timestamp is robot-node publication time, not necessarily the controller's original sampling time. The nested joint-state header can be empty. `joint_state.effort` is currently filled with zeros, so it is not measured torque; `joint_acc` is derived from velocity samples. Pose frames and wrench calibration/units are not frozen as a general force/pose-control contract. Gripper `0` is not proof of an absent device or a fully closed grip. The `rps_*` arrays need an exact end-device protocol for valid entries, scaling and status semantics.

`ArmMasterData` is a teleoperation data path: the generic source does not finish radian normalization for master positions, and current velocity/effort values are not valid speed/torque measurements. A newly stamped message can still carry stale upstream data. Do not infer a working master arm, a safe master/slave map or a trajectory input merely from message frequency.

### QoS, readiness and camera/recording acceptance

Readiness includes an expected endpoint, matching installed type, compatible QoS, data within an agreed timeout, valid content, continuous timestamps where applicable, and the required operating authority. Query the chassis lifecycle state read-only; do not automatically configure/activate production nodes, restart core services or change parameters as a discovery step.

Arm high-frequency topics use SensorDataQoS (Keep Last 5, Best Effort, Volatile) and a documented nominal 5 ms / 200 Hz publication interval. Those figures are not a hard real-time guarantee. Measure received rate and gaps and keep callbacks light. For cameras, record topic/type, encoding, calibration/resolution, rate, timestamp and a decoded sample. An encoded H.26x payload needs a matching decoder before a pixel-processing path such as `cv_bridge`.

For a data session, save the robot/profile/scene/SDK versions, exact interface definitions, source/read timestamps, QoS, frame IDs, units, named channel order and a bounded recording. Check that the MCAP opens, contains the intended channels, spans the intended interval, has valid sample content and can be decoded. A file on disk or an upload-complete indication alone does not establish an acceptable training dataset. Recording, upload and remote-operation control APIs remain project-specific unless explicitly delivered.
