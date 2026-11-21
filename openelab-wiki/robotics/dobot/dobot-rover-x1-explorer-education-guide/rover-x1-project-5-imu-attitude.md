---
description: >-
  DOBOT Rover X1 Explorer educational project tutorial; source-backed draft with
  prerequisites, experiments, and validation boundaries.
---

# Project 5 — ROVER X1 IMU and Attitude Monitoring

{% hint style="info" %}
[**View DOBOT Rover X1 Explorer on OpenELAB**](https://openelab.io/products/dobot-rover-x1-explorer-robot)

**Model:** ROVER X1 Explorer · **SKU:** DOBOT-1100000231 (Basic EDU default product selection; other variant SKUs require confirmation) · **Edition scope:** Basic / Smart / Max EDU; point-foot robot
{% endhint %}

[Return to Explorer education guide](./) · [Existing ROVER X1 manual (Air/Standard/Pro scope)](../dobot-rover-x1-user-manual.md)

### Product overview

**Project 5: IMU-Based Attitude Monitoring and Balance Compensation.** The course sets three tasks: (1) acquire IMU acceleration/angular velocity and study compensation, (2) compare flat/sloped terrain data, and (3) visualize robot attitude. The verified first result is **read-only IMU/pose telemetry**, with compensation analysis kept separate from untested control changes.

### Applications

* Telemetry acquisition and dashboard construction.
* Estimating roll/pitch/yaw and quantifying sensor noise, sample rates and drift.
* Exploring how surface inclination correlates with measured attitude.
* Planning closed-loop correction mathematically **without** assuming a safe physical compensation controller.

### Specifications

| Source                                                     | Data and units                                                                                                        |
| ---------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| High-level RobotClient.get\_state().robot\_state.ori\_body | Roll, pitch, yaw in **radians**                                                                                       |
| High-level robot state                                     | Body acceleration m/s² and angular velocity rad/s                                                                     |
| Low-level IMU example                                      | low\_level/python/e4\_imu\_state\_sub.py                                                                              |
| Low-level IMU topic                                        | rt/lower/state (LowerState)                                                                                           |
| Raw low-level data                                         | Orientation quaternion, gyro and accelerometer                                                                        |
| Low-level transport                                        | CycloneDDS on wired Ethernet                                                                                          |
| High-level posture actions                                 | balance\_\* methods apply to documented **legged** balance-stand state; they are **actuation**, not simple monitoring |

Sources: [High-Level RobotState fields](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md), [Low-Level API E4 IMU](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md).

### Hardware and connections

1. Begin on a flat, dry surface with the robot **stationary**; ensure no unauthorized modification of limb motors or controller.
2. High-level telemetry may be queried over the documented gRPC connection. Raw IMU via DDS requires **wired Ethernet**, appropriate middleware and a correct interface.
3. The additional RealSense D435i on Smart/Max also has an internal IMU; **do not confuse D435i sensor coordinates with the robot's body IMU** without calibrated frames and timestamps.
4. Slope, perturbation and balance-actuation experiments require separately approved training surfaces and direct supervision; this page does not define a safe test slope or controller gains.

### Software and development resources

The official [Quad SDK](https://github.com/Dobot-Team/dobot_quad_sdk) documents both gRPC and CycloneDDS. Use the parent [SDK setup guide](./) and, for raw DDS subscriptions, the wired DDS setup described in [Project 2](rover-x1-project-2-voice-interaction.md). ROS 2 dashboards are optional integrations and require a validated message bridge.

### Getting started

#### Task 1 — First working result: a static attitude snapshot

Install the official high-level Python package and run this **read-only** query:

```python
import math
from dobot_quad import RobotClient

with RobotClient("192.168.5.2:50051") as robot:
    state = robot.get_state()
    rpy_rad = list(state.robot_state.ori_body)
    rpy_deg = [math.degrees(value) for value in rpy_rad]
    print("State:", state.current_state)
    print("Roll / pitch / yaw (rad):", rpy_rad)
    print("Roll / pitch / yaw (deg):", rpy_deg)
```

**Expected result:** three real-valued orientation components in radians and their degree conversions. The displayed attitude is device-specific; do not insert sample angles as measured evidence. Confirm the robot pose and whether the values are body-frame relative before drawing conclusions.

#### Task 2 — Subscribe to raw IMU and compare sources

With wired CycloneDDS configured, from the SDK root:

```bash
export CYCLONEDDS_HOME=/usr/local/
export CYCLONEDDS_URI=file://"$PWD"/cyclonedds.xml
cd low_level/python
python3 e4_imu_state_sub.py
```

**Expected result:** the official example receives **rt/lower/state** IMU data. Record time stamps where available, orientation quaternion, gyroscope and acceleration values, plus the exact message/units from the current API. For quaternion-derived angles, verify axis convention and transform rather than assuming library defaults are the robot body frame.

For lab recording, store time, robot edition, firmware, surface, body RPY and IMU readings to CSV, then calculate sample interval statistics, roll/pitch plots and zero-motion baseline variation. The course does not provide an executable logger: implement and test it against the current SDK data type.

#### Task 3 — Multi-terrain comparison and dashboard

1. Capture a stationary flat-surface baseline and note battery/firmware.
2. On an independently assessed training surface and under supervision, collect an equivalent dataset; avoid an unverified incline limit or dynamic disturbance.
3. Plot time versus roll/pitch/yaw; label units and absolute/relative frame definitions.
4. Compare amplitude, mean, standard deviation and gaps/stale samples.
5. Test dashboard behavior with simulated missing/late IMU frames.

#### Task 4 — Balance-compensation study (not automatic actuation)

Develop the correction principle **offline**: define reference roll/pitch, estimate error, set bounds, simulate commands and analyze stability. The manufacturer exposes legged **balance\_pitch/roll/yaw/neutral** and pose methods, but sending commands requires validating the current firmware, operating state, limits and physical clearance. **Do not use the low-level motor-command publishing example as a shortcut.** A demonstrated monitoring dashboard is a complete introductory result even when compensation is not enabled.

### Troubleshooting and FAQs

**Orientation appears 57.3 times too large or small:** check **radian versus degree** conversion.

**Raw IMU subscriber receives nothing:** check wired DDS setup, interface, configured topic and middleware; a working high-level gRPC state query is not evidence of DDS connectivity.

**High-level RPY and D435i IMU disagree:** confirm they refer to different sensor frames, clocks, filtering and calibration; do not average them without an explicit transform.

**Can this page guarantee balance compensation?** No. The source is a course objective; control tuning and physical stability testing remain outstanding engineering work.

### Downloads and technical documents

* [High-Level API: RobotState and balance interfaces](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md).
* [Low-Level API: IMU E4](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md).
* [Official SDK repository](https://github.com/Dobot-Team/dobot_quad_sdk).

**Student deliverable:** two timestamped attitude recordings, clearly labeled plots, a comparison table and an offline compensation-design note. Only after a supervised bench protocol may actuation be considered.

### References and validation

* DOBOT, _Practical Applications of Quadruped Robots — Educational Guide_ V2.0, 2026-09-30, supplied course outline.
* [OpenELAB Explorer product listing](https://openelab.io/products/dobot-rover-x1-explorer-robot), reviewed 2026-11-21.
* [Official DOBOT Quad SDK](https://github.com/Dobot-Team/dobot_quad_sdk), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware validation:** not run. Quoted API fields are documented interfaces; no live robot data, calibration, dynamic stop time or autonomous-navigation performance was measured.
