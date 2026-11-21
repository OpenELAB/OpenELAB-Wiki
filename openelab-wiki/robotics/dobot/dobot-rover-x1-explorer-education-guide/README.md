---
description: Official SDK getting started and education project roadmap.
---

# DOBOT Rover X1 Explorer — Education and Development Guide

{% hint style="info" %}
[**View DOBOT Rover X1 Explorer Quadruped Robot on OpenELAB**](https://openelab.io/products/dobot-rover-x1-explorer-robot)

**Model:** ROVER X1 Explorer · **Store SKU:** DOBOT-1100000231 (Basic EDU shown by default; confirm separate Smart/Max SKU) · **Editions:** Basic EDU, Smart EDU, Max EDU · **Listed mobility:** point-foot
{% endhint %}

### Product overview

The DOBOT ROVER X1 Explorer is a quadruped development platform for programming, motion control, telemetry, perception and student projects. This page is the **entry point for the Explorer EDU configurations**. It does not replace the manufacturer's operating manual or imply a validated autonomous-navigation system.

The related six-project sequence is adapted from DOBOT's _Practical Applications of Quadruped Robots — Educational Guide V2.0 (2026-09-30)_. This source is a **course outline** rather than a collection of executable tutorials. The separate project pages therefore distinguish implemented, documented SDK interfaces from proposed development tasks.

The existing [ROVER X1 User Manual](../dobot-rover-x1-user-manual.md) covers **Air / Standard / Pro**, not an exact set of matching EDU configurations. Check all edition-specific controls, sensors, firmware and connections against the delivered equipment.

### Applications

* University quadruped-robot courses and supervised robot-control labs.
* High-level Python/C++ robot motion and telemetry applications.
* Front/rear RGB and depth image processing, obstacle sensing and IMU logging.
* Voice-interface prototypes and perception research.
* Supervised indoor corridor-inspection prototypes—not certified unattended deployment.

### Specifications

| Included item or specification          | Basic EDU     | Smart EDU     | Max EDU       |
| --------------------------------------- | ------------- | ------------- | ------------- |
| Battery                                 | 4000 mAh      | 8000 mAh      | 8000 mAh      |
| Listed runtime                          | Approx. 1.5 h | Approx. 2.5 h | Approx. 2.5 h |
| 40 TOPS compute module                  | No            | Yes           | Yes           |
| Intel RealSense D435i                   | No            | Yes           | Yes           |
| Livox Mid360 LiDAR                      | No            | No            | Yes           |
| Original charger, remote, charging dock | Yes           | Yes           | Yes           |
| Standard point-foot configuration       | Yes           | Yes           | Yes           |

**Shared platform specifications (manufacturer/store-listed, not bench-tested):** maximum point-foot speed up to 1.8 m/s; inclined terrain capability 30–35°; obstacle clearance 16 cm; payload range 3–7 kg; front and rear 1080p RGB cameras and front/rear depth sensing. Actual performance depends on terrain, payload, software and battery. The D435i and Mid360 are additional edition-specific devices.

Source: [OpenELAB edition table and packing list](https://openelab.io/products/dobot-rover-x1-explorer-robot).

### Hardware and connections

1. Verify the **selected EDU edition**, robot serial/firmware, installed sensors and shipped accessories. Smart and Max EDU include devices absent from Basic EDU. The optional wheel-foot conversion is **not included** with these listed point-foot versions.
2. Use the supplied battery and original charger. Follow the exact-edition charging instructions; this guide does not supply an unverified connector voltage, pinout or charger workaround.
3. For the SDK's **wired Ethernet** mode, the manufacturer documents robot address **192.168.5.2** and a PC address in **192.168.5.0/24**. A distinct, unused host address must be configured.
4. The manufacturer's **Wi-Fi** method uses its Rover-\* network and gRPC robot address **192.168.1.6**. The SDK specifies **wired Ethernet** for low-level CycloneDDS traffic.
5. Choose a flat, dry, open test area. Keep a human operator within visual range, familiarize the operator with the actual emergency-stop controls, and keep personnel clear. The existing V1.3 manual describes remote **LB + B** and App E-Stop; confirm those controls on the delivered EDU software before testing movement.
6. Never infer accessory mounting orientation, power, connector pin assignments or wheel-foot compatibility from product imagery.

### Software and development resources

| Component               | Documented scope                                                                                                                           | Official resource                                                                                    |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| High-level control      | Python/C++, gRPC, state and predefined motion functions                                                                                    | [High-Level API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md) |
| Sensor/low-level access | CycloneDDS over wired Ethernet; RGB/depth, IMU, audio and robot-state topics                                                               | [Low-Level API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md)   |
| Reference host          | Ubuntu 22.04, Python 3.10+, CMake 3.16+, GCC/G++ 9+                                                                                        | [Quad SDK README](https://github.com/Dobot-Team/dobot_quad_sdk)                                      |
| ROS 2                   | Intended integration in the supplied course outline, but **not established as a supported ready-made native ROS 2 stack** in the cited SDK | [Quad SDK source](https://github.com/Dobot-Team/dobot_quad_sdk)                                      |

Pin SDK commit, firmware, hardware revision and middleware version when reproducing experiments; do not reuse protocol mappings or joint IDs from another robot model.

### Getting started

#### Prerequisites

* A confirmed ROVER X1 Explorer EDU unit, charged battery and manufacturer operating instructions.
* An Ubuntu 22.04 PC, Python 3.10+, Git and permission to install Python dependencies.
* A wired development connection with a distinct PC IP on 192.168.5.0/24.
* A safe, obstacle-free area and access to the robot's verified stop controls.

#### First working result: query state without motion

1. Check Ethernet link and set a free PC address in the robot's wired subnet (for example **192.168.5.10/24**, if not already occupied). Confirm this address with your network administrator as needed.
2. Install the manufacturer high-level Python SDK:

```bash
git clone https://github.com/Dobot-Team/dobot_quad_sdk.git
cd dobot_quad_sdk/high_level/python
python3 -m venv .venv
source .venv/bin/activate
python -m pip install .
```

3. Request a state snapshot without sending any movement command:

```bash
python - <<'PY'
from dobot_quad import RobotClient

with RobotClient("192.168.5.2:50051") as robot:
    state = robot.get_state()
    print("RPC success:", state.success)
    print("Current state:", state.current_state)
    print("Speed ratio:", state.current_speed_ratio)
    print("Obstacle avoidance:", state.obstacle_avoidance_enabled)
PY
```

**Expected result:** a successful gRPC response and current state fields. The displayed state and speed ratio depend on the individual robot; record actual values rather than using an invented sample log.

**If the check fails:** verify physical Ethernet link, host subnet/address conflict, the actual robot's firmware/IP and gRPC service, then the installed SDK version. Do not use motor commands to troubleshoot a failed state query.

### Six project tutorials

1. [**Project 1 — Basic Robot Control and SDK Setup**](rover-x1-project-1-basic-control.md): hardware orientation, setup and supervised stand–move–wave.
2. [**Project 2 — Voice Interaction and Motion Response**](rover-x1-project-2-voice-interaction.md): audio DDS capture, command interpretation and feedback.
3. [**Project 3 — Locomotion and Gait Analysis**](rover-x1-project-3-gait-analysis.md): directional movement and controlled gait observations.
4. [**Project 4 — Bidirectional Obstacle Detection**](rover-x1-project-4-obstacle-detection.md): front/rear 16UC1 depth streams and offline stop logic.
5. [**Project 5 — IMU and Attitude Monitoring**](rover-x1-project-5-imu-attitude.md): body-angle telemetry, raw IMU and monitoring dashboard.
6. [**Project 6 — Corridor Inspection Prototype**](rover-x1-project-6-corridor-inspection.md): module integration, unified motion gateway and offline arbitration.

The chapters follow the supplied educational guide but are independent tutorials with prerequisites and success checks. Complete earlier checkpoints before later integration work.

### Troubleshooting and FAQs

**A high-level state request times out.** Confirm Ethernet versus Wi-Fi IP choice, the host's subnet and the robot's firmware-specific address. A ping alone does not prove gRPC is available.

**Low-level examples cannot see topics.** Confirm **wired Ethernet**, CycloneDDS installation, interface selection and the exact topic names. High-level gRPC success does not verify DDS.

**Do all editions include a RealSense D435i or Mid360?** No. D435i is listed only for Smart/Max; Mid360 only for Max. Built-in front/rear depth sensing is distinct from the extra D435i.

**Can the robot run the supplied course on ROS 2 immediately?** Do not assume so. The currently reviewed manufacturer SDK documents gRPC and CycloneDDS; ROS 2 bridging, message definitions, coordinate transforms and orchestration must be validated separately.

**Is Project 4 a substitute for an emergency stop?** No. Sensor-based stopping here is a supervised educational software prototype, not a verified safety-rated function. Preserve the robot's built-in protections.

### Downloads and technical documents

| Resource                                                                                                       | Engineering purpose                           | Scope                                               |
| -------------------------------------------------------------------------------------------------------------- | --------------------------------------------- | --------------------------------------------------- |
| [DOBOT Quad SDK repository](https://github.com/Dobot-Team/dobot_quad_sdk)                                      | Source, README and examples                   | ROVER X1 development                                |
| [High-Level API reference](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md) | gRPC state, motion and management             | Official SDK                                        |
| [Low-Level API reference](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md)   | CycloneDDS topics and examples                | Official SDK                                        |
| [OpenELAB ROVER X1 manual](../dobot-rover-x1-user-manual.md)                                                   | Safety, start-up, troubleshooting             | V1.3, Air/Standard/Pro; exact EDU match unconfirmed |
| [OpenELAB Explorer product page](https://openelab.io/products/dobot-rover-x1-explorer-robot)                   | Edition bill of materials, links and variants | Basic/Smart/Max EDU                                 |

The exact EDU manual, connector wiring drawings, accessory mount data, firmware pairing and calibration records should be added when obtained from DOBOT.

### References and validation

* DOBOT, _Practical Applications of Quadruped Robots — Educational Guide_, V2.0 (2026-09-30), supplied course outline.
* [OpenELAB, ROVER X1 Explorer product listing](https://openelab.io/products/dobot-rover-x1-explorer-robot), reviewed 2026-11-21.
* [DOBOT, Quad SDK README](https://github.com/Dobot-Team/dobot_quad_sdk), [High-Level API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/high_level.md), [Low-Level API](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md), reviewed 2026-11-21.
* [Existing OpenELAB ROVER X1 V1.3 User Manual](../dobot-rover-x1-user-manual.md) (different edition naming).

**Documentation:** reviewed; draft stage. **Software execution:** not run. **Hardware validation:** not run. **Open issues:** exact Smart/Max SKU, hardware/firmware pairing, actual topic units/calibration, unvalidated ROS 2 bridge and autonomous safety tests.
