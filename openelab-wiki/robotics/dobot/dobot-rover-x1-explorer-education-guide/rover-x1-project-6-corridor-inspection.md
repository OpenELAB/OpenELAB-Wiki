---
description: >-
  DOBOT Rover X1 Explorer educational project tutorial; source-backed draft with
  prerequisites, experiments, and validation boundaries.
---

# Project 6 — ROVER X1 Corridor Inspection Prototype

{% hint style="info" %}
[**View DOBOT Rover X1 Explorer on OpenELAB**](https://openelab.io/products/dobot-rover-x1-explorer-robot)

**Model:** ROVER X1 Explorer · **SKU:** DOBOT-1100000231 (Basic EDU default product selection; other variant SKUs require confirmation) · **Edition scope:** Basic / Smart / Max EDU; point-foot robot
{% endhint %}

[Return to Explorer education guide](./) · [Existing ROVER X1 manual (Air/Standard/Pro scope)](../dobot-rover-x1-user-manual.md)

### Product overview

**Project 6: Campus Corridor Robot Inspection System Integration.** This capstone integrates the previous five projects into a **supervised, low-speed prototype**: requirements, a unified motion/safety gateway, module integration, and corridor trial/data analysis. The source course proposes ROS 2 architecture, but the reviewed manufacturer SDK documents separate **gRPC** and **CycloneDDS** layers; an end-to-end ROS 2 package and autonomous controller are not supplied here.

### Applications

* End-to-end student systems engineering with explicit module interfaces.
* Robot monitoring and operator-authorized inspection simulations.
* Comparing expected and measured inspection task performance.
* Designing fault handling around intermittent sensors, voice uncertainty and human take-over.

### Specifications

| Module                   | Input/output                            | Evidence / required work                                                                                                                              |
| ------------------------ | --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Robot state and movement | High-level RobotClient gRPC             | Official [High-Level API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md)                                         |
| Front/rear depth         | DDS Image, camera2/camera3 image\_depth | Official [Low-Level API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md); metric scale/latency validation required |
| Attitude                 | RobotState RPY or raw IMU               | [Project 5](rover-x1-project-5-imu-attitude.md); confirm frames                                                                                       |
| Speech interface         | DDS VoiceState/VoiceCmd + custom ASR    | [Project 2](rover-x1-project-2-voice-interaction.md); no native ASR assumed                                                                           |
| Motion arbitration       | **To be implemented**                   | No tested, safety-rated controller provided in course                                                                                                 |
| ROS 2                    | **Optional custom integration**         | Bridge and topics must be independently implemented/validated                                                                                         |

The listed Explorer EDU editions differ: Smart adds 40 TOPS compute and D435i; Max also adds Mid360. Their inclusion does **not** by itself establish a working SLAM or autonomous-inspection implementation.

### Hardware and connections

1. Use a confirmed point-foot Rover X1 Explorer and document the exact configuration, firmware, cameras and compute modules installed.
2. Restrict initial trials to an approved, quiet, flat indoor test zone with an operator carrying the physical emergency-stop controller and maintaining visibility.
3. Use wired Ethernet when a project needs low-level DDS sensor streams. Do not assume Wi-Fi supports the same sensor transport.
4. Keep power, accessory mounting and calibration within the manufacturer-supported configuration; no custom payload, battery or motor wiring is specified here.
5. Capture a route map and a human-approved stop/turn sequence. Public, occupied corridors and unsupervised patrols are outside this initial experiment.

### Software and development resources

Recommended **separation of concerns**:

* **Perception readers:** front/rear depth, validation of units, frames, timestamps and stale-data detection; never publish direct motor commands.
* **Attitude monitor:** read-only IMU and robot-state logging.
* **Voice/GUI command source:** propose actions, with explicit operator confirmation and rejection of uncertain phrases.
* **Motion gateway:** the _only application component_ allowed to issue high-level gRPC motion requests.
* **Supervisor:** operator enable, emergency/abort priority, connection watchdog, motion timeouts and deterministic fault-state logging.
* **Telemetry recorder:** record decisions, sensed conditions, commands and observed robot state using a consistent clock strategy.

A custom ROS 2 representation may be introduced after DDS/gRPC-to-ROS bridges, QoS, clocks and transforms have been tested. The manufacturer APIs alone are not a ROS 2 navigation stack.

### Getting started

#### Task 1 — Define the inspection acceptance criteria

Write a corridor inspection specification with exact route length, allowed speed, human-supervision rules, control source priorities and **measured** stop distance. Avoid an invented performance target being presented as a DOBOT guarantee. Define at least: operator stop, lost communications, stale front/rear depth, low battery, command timeout, invalid direction and conflicting voice/manual request.

#### Task 2 — First working result: offline arbitration test

Before any robot movement, validate a small **pure software** motion gateway. The code below is deliberately offline and **does not actuate hardware**:

```python
def decide(command, operator_enabled, sensors_fresh,
           front_clear, rear_clear, robot_healthy):
    if not operator_enabled or not robot_healthy or not sensors_fresh:
        return "BLOCK"
    if command == "forward":
        return "ALLOW" if front_clear else "BLOCK"
    if command == "reverse":
        return "ALLOW" if rear_clear else "BLOCK"
    return "BLOCK"

assert decide("forward", True, True, True, True, True) == "ALLOW"
assert decide("forward", True, False, True, True, True) == "BLOCK"
assert decide("reverse", True, True, True, False, True) == "BLOCK"
assert decide("turn", True, True, True, True, True) == "BLOCK"
```

**Expected result:** all assertions pass. The meanings of **front\_clear** and **rear\_clear** must be supplied only by calibrated and time-validated measurements—not by arbitrary colorized depth images. The sample does not handle braking, network partitions, physical emergency stops or simultaneous control conflicts; those remain explicit integration and review requirements.

#### Task 3 — Integrate modules without enabling motion

1. Prove the [Project 1](rover-x1-project-1-basic-control.md) read-only gRPC state connection.
2. Prove [Project 4](rover-x1-project-4-obstacle-detection.md) front/rear depth samples and correct timestamp/frame mapping.
3. Record the [Project 5](rover-x1-project-5-imu-attitude.md) attitude stream.
4. Demonstrate a [Project 2](rover-x1-project-2-voice-interaction.md) text/voice command being **accepted or rejected in software only**.
5. Inject stale sensors, connection loss and operator disable in a test harness. Confirm a motion request is blocked and an incident is logged.
6. Require independent human review of route, stop mechanism, fallback behavior and edition/firmware compatibility **before** connecting the real motion executor.

#### Task 4 — Supervised corridor inspection and data analysis

After independent bench validation, progress through stationary sensing → a controlled single segment → manual recovery → multiple bounded segments. Collect actual route time, number of blocked requests, latency between detection and commanded stop, measured physical stopping behavior, sensor gap rate and failure/recovery log. Report these as measurements only after testing; **no accuracy, autonomy level or safety certification is claimed here**.

### Troubleshooting and FAQs

**Multiple modules send conflicting actions:** route every application motion request through one command gateway. Treat direct subsystem motor publishing as prohibited for the capstone.

**Sensor stream pauses while robot state continues:** treat sensor freshness independently of gRPC health and block affected directions until validated recovery.

**The custom ROS 2 bridge has message delays:** inspect QoS, network interfaces, timestamps and transforms; do not assume the raw CycloneDDS topics are native ROS 2 topics.

**A voice command and obstacle signal disagree:** the software gateway must prioritize an operator stop or validated block over the requested action. The physical emergency stop remains independent.

### Downloads and technical documents

* [High-Level gRPC API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md) — state/motion gateway.
* [Low-Level CycloneDDS API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md) — sensor and voice streams.
* [Official Quad SDK repository](https://github.com/Dobot-Team/dobot_quad_sdk).
* [Explorer overview and edition BOM](https://openelab.io/products/dobot-rover-x1-explorer-robot).
* [ROVER X1 legacy user manual](../dobot-rover-x1-user-manual.md) — verify EDU applicability.

**Student deliverable:** requirements and software architecture, offline arbitration test log, module integration checklist, measured trial report and explicit unresolved safety limitations. **The uploaded course outline does not supply a completed or validated corridor-inspection implementation.**

### References and validation

* DOBOT, _Practical Applications of Quadruped Robots — Educational Guide_ V2.0, 2026-09-30, supplied course outline.
* [OpenELAB Explorer product listing](https://openelab.io/products/dobot-rover-x1-explorer-robot), reviewed 2026-11-21.
* [Official DOBOT Quad SDK](https://github.com/Dobot-Team/dobot_quad_sdk), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware validation:** not run. Quoted API fields are documented interfaces; no live robot data, calibration, dynamic stop time or autonomous-navigation performance was measured.
