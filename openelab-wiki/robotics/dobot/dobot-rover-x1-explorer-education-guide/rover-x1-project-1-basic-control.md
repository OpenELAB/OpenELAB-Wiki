---
description: >-
  DOBOT Rover X1 Explorer educational project tutorial; source-backed draft with
  expected results and validation boundaries.
---

# Project 1 — ROVER X1 Basic Control and SDK Setup

{% hint style="info" %}
[**View DOBOT Rover X1 Explorer on OpenELAB**](https://openelab.io/products/dobot-rover-x1-explorer-robot)

**Model:** ROVER X1 Explorer · **SKU:** DOBOT-1100000231 (Basic EDU default product selection; other variant SKUs require confirmation) · **Edition scope:** Basic / Smart / Max EDU; point-foot robot
{% endhint %}

[Return to Explorer education guide](./) · [Existing ROVER X1 manual (Air/Standard/Pro scope)](../dobot-rover-x1-user-manual.md)

### Product overview

**Project 1: Introduction to Quadruped Robots and Basic Control.** This beginner tutorial expands the course tasks: (1) hardware/system architecture, (2) development environment and connection, (3) high-level SDK motion from standing to waving. It is intended for a supervised laboratory with a **point-foot ROVER X1**.

### Applications

* Teaching high-level state machines, movement commands and human-supervised safe operation.
* Confirming network and SDK communication before a more complex perception project.
* Learning to capture an experiment log containing robot edition, firmware, SDK revision and actual results.

### Specifications

| Integration item                         | Value / applicable scope                                                           |
| ---------------------------------------- | ---------------------------------------------------------------------------------- |
| Host                                     | Ubuntu 22.04; Python 3.10+                                                         |
| Control transport                        | High-level gRPC through official RobotClient                                       |
| Wired robot service                      | 192.168.5.2:50051; PC on 192.168.5.0/24                                            |
| Supported legged state/action examples   | balance\_stand, walk\_forward, wave\_hand, ready / stand\_down                     |
| Distance range in current high-level API | line\_walk / walk\_forward 0–3 m per call                                          |
| Speed ratio                              | 10–100; use a supervised low setting for initial trials                            |
| Edition distinction                      | Smart and Max add perception modules; they are not required for this basic SDK lab |

Source: [High-Level API reference](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md).

### Hardware and connections

1. Place the robot on flat, firm, dry ground with a generous clear perimeter; keep people out of its movement area.
2. Check for damaged feet, loose parts and battery warnings. Confirm the remote/App emergency stop on the physical robot.
3. Connect the host to **wired Ethernet** and set a non-conflicting address on the 192.168.5.0/24 subnet. Use the original battery/charging equipment and do not modify electrical wiring.
4. Keep the optional wheel-foot features disabled/not used: this tutorial assumes the **point-foot** platform. The installed sensors and accessories depend on the EDU edition.

### Software and development resources

| Resource                                                                                                                 | Use                                                    |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------ |
| [Quad SDK README](https://github.com/Dobot-Team/dobot_quad_sdk)                                                          | OS, networking, installation and example entry points  |
| [High-Level API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md)                     | RobotClient, state, motion and stop methods            |
| [High-level Python example directory](https://github.com/Dobot-Team/dobot_quad_sdk/tree/main/high_level/python/examples) | Manufacturer examples for inspecting motions and state |

The official implementation uses **gRPC**, not a required ROS 2 node. ROS 2 is introduced as a separate integration objective in later course projects.

### Getting started

#### Task 1 — Identify the architecture

Record the physical edition, point-foot configuration, battery, sensors and onboard modules. Draw a simple block diagram: development PC → Ethernet → high-level gRPC service → robot control software → actuators; separate sensor topics run through CycloneDDS on wired Ethernet. Do not invent motor IDs or electrical pinouts.

#### Task 2 — Install and verify communication

```bash
git clone https://github.com/Dobot-Team/dobot_quad_sdk.git
cd dobot_quad_sdk/high_level/python
python3 -m venv .venv
source .venv/bin/activate
python -m pip install .
python3 examples/e1_get_available_motions.py
```

The last command is DOBOT's supplied high-level example. **Expected result:** the example can query the connected robot's registered motion set; actual contents depend on robot software. If connection fails, diagnose host IP, Ethernet, robot firmware and the gRPC endpoint before commanding motion.

#### Task 3 — Stand, move, wave (supervised motion)

Only after the remote/App stop, movement area and first status query have been physically verified, execute the following **small, illustrative sequence**. It uses SDK-documented methods; its order and clearance still require a supervised first run.

```python
from dobot_quad import RobotClient

with RobotClient("192.168.5.2:50051") as robot:
    robot.enable_safety_ready()  # Ctrl+C handler; not a hardware E-stop
    if not robot.is_quad():
        raise RuntimeError("Expected a point-foot / legged robot")

    robot.set_speed_ratio(10)
    try:
        robot.balance_stand()
        robot.walk_forward(0.20, speed_ratio=10)
        robot.wave_hand(duration=2.0)
    finally:
        robot.ready()  # documented slow stand-down request
```

**Expected result:** observed stand → 0.20 m commanded forward travel → wave → return to ready, with the robot never unattended. Measure **actual** travel; the commanded distance is not an accuracy guarantee. Ctrl+C handling is a software convenience, not a replacement for the physical emergency stop. If the robot behaves unexpectedly, use the verified physical stop and end the test.

### Troubleshooting and FAQs

**No motions or gRPC timeout:** check physical link and robot IP, run the read-only state test in the parent guide and confirm SDK/firmware pairing.

**Motion rejected or unsupported:** use the SDK's get\_robot\_type() / is\_quad() and get\_state() to verify legged configuration and state, then inspect error output. Do not override a safety interlock.

**The robot moves farther or shorter than 0.20 m:** measure actual displacement on a marked test surface; compare terrain, speed ratio and initial pose. Do not compensate with higher-speed trials until the discrepancy is understood.

### Downloads and technical documents

* [DOBOT High-Level API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md) — state, line walk, wave and ready methods.
* [Official SDK source](https://github.com/Dobot-Team/dobot_quad_sdk) — Python package and example scripts.
* [ROVER X1 existing user manual](../dobot-rover-x1-user-manual.md) — operational safety; **edition names differ**.

**Student deliverable:** a dated setup record, screenshot/text of actual state response, supervised sequence video and a short explanation of the SDK's high-level control architecture.

### References and validation

* DOBOT, _Practical Applications of Quadruped Robots — Educational Guide_ V2.0, 2026-09-30, supplied course outline.
* [OpenELAB Explorer product listing](https://openelab.io/products/dobot-rover-x1-explorer-robot), reviewed 2026-11-21.
* [Official DOBOT Quad SDK](https://github.com/Dobot-Team/dobot_quad_sdk), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware testing:** not run. Outcomes and diagnostic checks below are expected behavior from the cited interfaces or explicit project acceptance criteria; they are not claimed test results. Use the delivered firmware and record the actual SDK commit before performing experiments.
