---
description: >-
  DOBOT Rover X1 Explorer educational project tutorial; source-backed draft with
  prerequisites, experiments, and validation boundaries.
---

# Project 4 — ROVER X1 Front and Rear Obstacle Detection

{% hint style="info" %}
[**View DOBOT Rover X1 Explorer on OpenELAB**](https://openelab.io/products/dobot-rover-x1-explorer-robot)

**Model:** ROVER X1 Explorer · **SKU:** DOBOT-1100000231 (Basic EDU default product selection; other variant SKUs require confirmation) · **Edition scope:** Basic / Smart / Max EDU; point-foot robot
{% endhint %}

[Return to Explorer education guide](./) · [Existing ROVER X1 manual (Air/Standard/Pro scope)](../dobot-rover-x1-user-manual.md)

### Product overview

**Project 4: Bidirectional Obstacle Detection and Safety Monitoring.** This tutorial maps the course tasks to accessible SDK functions: (1) front/rear RGB and depth acquisition, (2) forward-obstacle criteria, (3) reverse-obstacle criteria, and (4) integrated state decisions and exception handling.

The deliverable is an **experimental, supervised software obstacle monitor**, not a safety-rated protection device. Preserve factory avoidance, physical emergency-stop access and human supervision.

### Applications

* Understanding front/rear camera geometry and depth image decoding.
* Building software that **proposes** stop/permit decisions based on validated measurements.
* Testing fail-closed behavior for disconnected, delayed, invalid and missing sensor samples.

### Specifications

| Sensor/transport field | Manufacturer-documented value                            |
| ---------------------- | -------------------------------------------------------- |
| Front depth topic      | rt/camera/camera2/image\_depth                           |
| Rear depth topic       | rt/camera/camera3/image\_depth                           |
| Depth message          | DDS Image, encoding 16UC1 (unsigned 16-bit, one channel) |
| Front RGB topic        | rt/camera/camera0/image\_compressed                      |
| Rear RGB topic         | rt/camera/camera1/image\_compressed                      |
| Development transport  | CycloneDDS over **wired** Ethernet                       |
| Sample program         | low\_level/python/e2\_depth\_image\_sub.py               |

Manufacturer document: [Low-Level API: E1/E2 camera subscriptions](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md). **Important:** the API describes 16UC1 data and colorized visualization but does not, in the reviewed passage, establish the exact depth-to-meter conversion, extrinsics, blank-pixel codes, timing bounds or stopping-distance performance. Do not equate an image color with absolute metric distance.

### Hardware and connections

1. Verify installed **front and rear base depth cameras** physically. RealSense D435i is a separate Smart/Max EDU device; the extra Livox Mid360 is Max only.
2. Clean/unobstruct camera windows and confirm camera orientation without relying solely on a product photo.
3. Connect host and robot by **wired Ethernet** in the documented 192.168.5.0/24 subnet; configure the correct CycloneDDS network interface/domain.
4. Conduct the first tests with the robot **stationary** and obstacles moved by the experimenter, not by commanding the robot toward people or objects.
5. Do not disable the robot's built-in obstacle avoidance. Keep a human operator ready with the verified physical stop.

### Software and development resources

Install the official low-level SDK following the [Quad SDK README](https://github.com/Dobot-Team/dobot_quad_sdk), including the provided middleware package, Python wheel, CycloneDDS libraries and modified cyclonedds.xml. Read [Project 2](rover-x1-project-2-voice-interaction.md) for the general wired DDS setup. The manufacturer's depth example uses OpenCV and can save pseudocolored PNG visualizations.

A project-specific ROS 2 image bridge is optional coursework; **no prevalidated native ROS 2 topic or coordinate transform is asserted here**.

### Getting started

#### Task 1 — First working result: two depth streams

From the SDK root, after verifying the DDS configuration:

```bash
export CYCLONEDDS_HOME=/usr/local/
export CYCLONEDDS_URI=file://"$PWD"/cyclonedds.xml
cd low_level/python
python3 e2_depth_image_sub.py
```

**Expected result:** the SDK's example subscribes to the documented **front depth topic**, reports 16UC1 depth frames with timestamps and saves visualization files in its output directory. Capture the **actual** encoding, dimensions, frame ID and timestamps. Exit cleanly with Ctrl+C.

To test the **rear** independently, duplicate the manufacturer example and change only its input topic from **rt/camera/camera2/image\_depth** to **rt/camera/camera3/image\_depth** in the copy, then run that copy with the same DDS environment. Observe and label actual front/rear frames; do not present colorized PNG as calibrated distance.

#### Task 2 — Develop front stop criteria offline

Before connecting it to motion, define a region of interest in the **correct front camera optical frame**, decide how to reject zero/invalid/missing data, verify the physical depth scale against known measured objects, and calculate a stopping margin that includes robot speed, communication delay and braking/stand-down behavior. The numerical threshold must come from measurements; it is **not provided by the course outline**.

#### Task 3 — Develop rear stop criteria offline

Repeat the depth-scale and optical-frame checks with the **rear camera**. Reverse direction must select the **rear** sample, not reuse the forward sensor. Rejected, stale or missing rear data should prevent experimental reverse commands, independently of front data.

#### Task 4 — Test a bounded decision function

The following **offline-only synthetic unit test** does not subscribe to the robot and cannot stop it. The arbitrary 1.0 m example is a test fixture, **not a recommended safety distance**:

```python
def allow_direction(direction, front_m, rear_m, clearance_m):
    if direction not in {"forward", "reverse"}:
        return False
    if clearance_m <= 0:
        return False
    distance = front_m if direction == "forward" else rear_m
    return distance is not None and distance > clearance_m

assert not allow_direction("forward", 0.8, 2.0, 1.0)
assert allow_direction("forward", 1.5, 0.2, 1.0)
assert not allow_direction("reverse", 1.5, None, 1.0)
```

**Expected result:** all asserts pass. The final design must additionally reject **stale data**, distorted frames, calibration errors, unrecognized commands, unavailable robot state and duplicate motion sources. Do not send an actual forward/reverse command through this prototype until the stopping behavior is separately tested under controlled conditions.

### Troubleshooting and FAQs

**RGB streams work, depth streams do not:** check you subscribed to **image\_depth** from camera2/camera3, not the compressed color topic, and verify type/encoding.

**Distances are inconsistent:** check the camera's exact scale, pixel validity and optical frame; colorized values use per-image normalization and are not metric data.

**The rear topic is absent:** verify firmware and edition support for the observed camera mapping; preserve a no-reverse decision until the issue is resolved.

**Can the monitor replace the emergency stop?** No. It is an unvalidated instructional algorithm, not a protective control system.

### Downloads and technical documents

* [Low-Level API — RGB and Depth E1/E2](https://github.com/Dobot-Team/dobot_quad_sdk/blob/main/docs/docs/api/low_level.md).
* [DOBOT Quad SDK camera examples](https://github.com/Dobot-Team/dobot_quad_sdk/tree/main/low_level/python).
* [Explorer EDU variant details](https://openelab.io/products/dobot-rover-x1-explorer-robot).

**Student deliverable:** labeled front/rear raw-frame evidence, verified depth-scale experiment, parameter and timestamp log, offline direction-gate tests, and a table of known failure cases. **Not validated:** reliable metric thresholds and on-device automatic stopping.

### References and validation

* DOBOT, _Practical Applications of Quadruped Robots — Educational Guide_ V2.0, 2026-09-30, supplied course outline.
* [OpenELAB Explorer product listing](https://openelab.io/products/dobot-rover-x1-explorer-robot), reviewed 2026-11-21.
* [Official DOBOT Quad SDK](https://github.com/Dobot-Team/dobot_quad_sdk), reviewed 2026-11-21.

**Documentation:** source-reviewed draft. **Software execution:** not run. **Hardware validation:** not run. Quoted API fields are documented interfaces; no live robot data, calibration, dynamic stop time or autonomous-navigation performance was measured.
