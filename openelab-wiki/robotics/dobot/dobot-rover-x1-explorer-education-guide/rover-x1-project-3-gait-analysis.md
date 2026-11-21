---
description: >-
  DOBOT Rover X1 Explorer educational project tutorial; source-backed draft with
  expected results and validation boundaries.
---

# Project 3 — ROVER X1 Locomotion and Gait Analysis

{% hint style="info" %}
[**View DOBOT Rover X1 Explorer on OpenELAB**](https://openelab.io/products/dobot-rover-x1-explorer-robot)

**Model:** ROVER X1 Explorer · **SKU:** DOBOT-1100000231 (Basic EDU default product selection; other variant SKUs require confirmation) · **Edition scope:** Basic / Smart / Max EDU; point-foot robot
{% endhint %}

[Return to Explorer education guide](./) · [Existing ROVER X1 manual (Air/Standard/Pro scope)](../dobot-rover-x1-user-manual.md)

### Product overview

**Project 3: Ground Locomotion Control and Gait Analysis.** This tutorial follows the course tasks: locomotion and remote-controller basics; forward/turn/lateral commands; comparative gait and foot-trajectory analysis. It applies to the default **point-foot** Explorer EDU robots, not an assumed wheel-foot accessory package.

### Applications

* Reproducible tests of directional motion, distance and turning.
* Differentiating a **commanded motion profile** from actual measured displacement.
* Learning quadruped gait terminology, support phases and the limitations of API-level gait labels.

### Specifications

| Control item                       | Documented behavior                                                              |
| ---------------------------------- | -------------------------------------------------------------------------------- |
| High-level transport               | gRPC via RobotClient                                                             |
| Example linear actions             | walk\_forward / walk\_backward / move\_left / move\_right                        |
| Documented single-command distance | 0–3 m                                                                            |
| Example rotation                   | rotate("left", degrees)                                                          |
| Motion mode selectors              | walk and flying\_trot for legged robot                                           |
| Sequence command                   | velocity\_sequence(steps, gait="walk", speed\_ratio=..., stand\_down\_after=...) |
| Actual hardware                    | Point-foot legged configuration in listed Explorer EDU editions                  |

Reference: [High-Level API: state switching, line walk, rotate and velocity sequences](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md).

### Hardware and connections

1. Confirm the robot is point-foot using the delivered order and the SDK's get\_robot\_type() / is\_quad() interface.
2. Mark a measured straight path on a clean, flat floor with a generous perimeter for stopping. Avoid steep ramps, loose objects and crowds.
3. Keep a second observer ready with the **physical emergency stop**. Set a conservative speed ratio; collect no-contact measurements with tape/markers/video.
4. Use wired Ethernet for the example. Do not program wheel\_loco, drift or handstand on an unverified point-foot unit.

### Software and development resources

Install the high-level Python package from [the official repository](https://github.com/Dobot-Team/dobot_quad_sdk) as described in the [Explorer development guide](./). ROS 2 and inverse-kinematics/foot trajectory reconstruction are _course extension topics_, not automatically provided by a high-level walk command.

### Getting started

#### Task 1 — Inspect modes and controller

With the robot at rest, confirm state and available motion methods:

```python
from dobot_quad import RobotClient

with RobotClient("192.168.5.2:50051") as robot:
    print("Robot type:", robot.get_robot_type())
    print("State:", robot.get_state().current_state)
    print("Available motions:", robot.get_motions())
```

**Expected result:** non-error robot type, current state and a list of server-registered motions. Note that **miniQuad** denotes the legged configuration; an unexpected robot type must be resolved before motion testing.

#### Task 2 — Program a low-speed directional sequence

With all safety conditions physically confirmed, run one bounded step at a time. The following is a supervised study example, not an autonomous navigation controller:

```python
from dobot_quad import RobotClient

with RobotClient("192.168.5.2:50051") as robot:
    robot.enable_safety_ready()
    if not robot.is_quad():
        raise RuntimeError("Use point-foot / legged ROVER X1")
    robot.set_speed_ratio(10)
    try:
        robot.balance_stand()
        robot.walk_forward(0.20, speed_ratio=10)
        robot.move_left(0.20, speed_ratio=10)
        robot.rotate("left", 15)
    finally:
        robot.ready()
```

**Expected result:** a small forward command, lateral command and left turn, followed by a slow stand-down request. Measure actual distance, direction, turning angle and stop behavior. Avoid automatically repeating a failed or blocked command.

#### Task 3 — Gait and foot-trajectory analysis

The manufacturer's SDK currently names legged high-level **walk** and **flying\_trot** modes, but the course's _triangular gait_ and _four-point gait_ labels are pedagogical topics and **not verified as matching named API states**. Do not equate them without manufacturer mapping.

For a quantitative comparison:

1. Record commanded mode, speed ratio, surface and battery state.
2. Film the legs from a safe position; label successive support/contact phases and foot trajectory estimates.
3. Log high-level body orientation, velocity and joint telemetry from get\_state(); note orientation units are **radians** and joint position is **radians**.
4. Analyze stance/swing ratio and measured path; optionally compare to the manufacturer-documented gait options **only with supervision and adequate room**.
5. Separate the lab's manually measured quantities from unverified internal gait-controller parameters.

A first acceptable lab result is a labeled walking sequence and a table of **commanded versus observed** displacement, without needing to enable faster modes.

### Troubleshooting and FAQs

**Lateral motion rejected:** check legged/wheeled type and current state. The SDK notes wheel DRIFT mode lacks lateral movement, but that does not grant wheel support on an Explorer EDU point-foot product.

**Robot moves but trajectory is inaccurate:** compare floor friction, battery, stance, speed ratio and measurement method; do not claim odometry precision from the command value.

**How can students study triangular and four-point gaits?** Use the course's theoretical definitions and independently recorded foot-contact data. Do not claim those names are SDK parameters until a manufacturer document explicitly maps them.

### Downloads and technical documents

* [DOBOT High-Level API, line walks and velocity control](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md).
* [DOBOT Quad SDK examples](https://github.com/Dobot-Team/dobot_quad_sdk).
* [Existing ROVER X1 safety and remote-control manual](../dobot-rover-x1-user-manual.md), noting the different Air/Standard/Pro scope.

**Student deliverable:** three trial logs, measurements of commanded versus observed travel, annotated foot-contact video and an explanation of gait differences/uncertainty. No numerical performance result is asserted without a bench test.

### References and validation

* DOBOT, _Practical Applications of Quadruped Robots — Educational Guide_ V2.0, 2026-09-30, supplied course outline.
* [OpenELAB Explorer product listing](https://openelab.io/products/dobot-rover-x1-explorer-robot), reviewed 2026-11-21.
* [Official DOBOT Quad SDK](https://github.com/Dobot-Team/dobot_quad_sdk), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware testing:** not run. Outcomes and diagnostic checks below are expected behavior from the cited interfaces or explicit project acceptance criteria; they are not claimed test results. Use the delivered firmware and record the actual SDK commit before performing experiments.
