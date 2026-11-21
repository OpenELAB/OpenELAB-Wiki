---
description: >-
  Read-only tactile fields with model-correct 4x10, 6x11, 6x12 distinctions and
  metadata validity.
---

# Tutorial 3 — LINKERBOT Tactile Data and Sensor Validation

{% hint style="info" %}
[**L6**](https://openelab.io/products/linker-hand-linkerbot-l6-11) · [**L20 Lite**](https://openelab.io/products/linker-hand-linkerbot-l20-lite) · [**L20**](https://openelab.io/products/linker-hand-linkerbot-l20-21) · [**L30 Tendon**](https://openelab.io/products/linker-hand-linkerbot-l30-l30) · [**O6**](https://openelab.io/products/linker-hand-linkerbot-o6-11) — OpenELAB product links

**Scope:** seven LINKERBOT hand manuals, with model-specific tactile features and optional sensing.
{% endhint %}

[LINKERBOT series guide](./)

### Product overview

This tutorial collects **read-only tactile/force observations** and explains why a sensor that is missing or unsupported must never be treated as a valid zero-force measurement. The newer LINKERBOT ROS 2 SDK exposes named force fields and device-specific projections. It does not invent force calibration or guarantee every sold variant has fingertip sensors.

### Applications

* Identify installed tactile hardware and determine whether a normal force/proximity field is supported.
* Read current tactile data with validity, freshness and per-sensor presence fields.
* Compare sampling periods and distinguish sensor frame rate from bus communication frequency.

### Specifications

| Model        | Supplied manual / current SDK scope                                                                            |
| ------------ | -------------------------------------------------------------------------------------------------------------- |
| L6           | 6×12 piezoresistive array, up to 200 fps; native \`fn\` matrix                                                 |
| L20 Lite     | 6×12 at 200 fps; SDK also supports separately polled \`fns\`, \`fts\`, \`fds\`, \`px\` fields                  |
| L20          | 6×12 at 200 fps, normal matrix; protocol support must match firmware                                           |
| O6           | Tactile **optional**, 4×10 sensor at up to 200 fps                                                             |
| L30 Standard | Tactile **optional**, 6×12, up to 200 fps                                                                      |
| O20          | 6×12; manual **30 Hz tactile refresh**, although bus communication is listed at **1000 Hz**                    |
| O30          | 6×11 in manual, 200 fps; current SDK uses **descriptor** tactile data, not the same ROS matrix as other models |

The [official tactile guide](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/force.md) distinguishes \`fn\` normal point values, \`fns\` resultant, tangential fields and proximity. Many fields are model-dependent, not universally available.

### Hardware and connections

1. Confirm model/side and whether physical fingertip sensors are installed—especially optional O6 and L30 configurations.
2. Complete the approved bus/power and read-only ROS 2 setup in the earlier tutorials. Stop if the actual hand's supply, CAN variant or cable is unresolved.
3. Keep hands away from pinch points; no object grip or deliberate force is required to inspect an existing state sample.
4. Record the model's OEM sensor layout and the SDK's reported \`capabilities.force\_fields\`; do not assume a 6×12 grid or calibrated newton scale for every model.

### Software and development resources

* [ROS 2 force/tactile semantics, polling, metadata](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/force.md).
* [ROS 2 model compatibility](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md).
* [ROS 2 read-only setup](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/quick_start.md).

### Getting started

#### First working result: one sensor sample, with true presence and validity

1. With the compatible hand in an approved stationary state, inspect its capabilities:

```bash
ros2 topic echo --once --qos-durability transient_local /linkerbot_hand/capabilities
```

Check reported \`force\_fields\`, supported status and output projection. The manufacturer defaults all tactile polling rates to **0**.

2. On a non-O30 model with an installed, supported \`fn\` sensor:

```bash
ros2 param set /linkerbot_hand force_fn_hz 10.0
ros2 topic echo --once --qos-reliability best_effort /linkerbot_hand/state/tactile
```

On **O30**, the SDK uses a **descriptor-based** projection instead:

```bash
ros2 param set /linkerbot_hand force_fn_hz 10.0
ros2 topic echo --once --qos-reliability best_effort /linkerbot_hand/state/tactile_sensors
```

3. Inspect \`sensor\_name\`, \`present\`, \`valid\_values\`, \`unit\`, \`encoding\` and the sample's generation/sequence and stale flags. An unchanged republished value is not necessarily a new sensor acquisition. Do not request unsupported fields at positive polling rates.
4. For L20 Lite, \`fn\` and \`fns\` can use **separate acquisition requests**. For O30, multiple descriptor fields may share one hardware transaction; do not sum field polling rates to estimate bus load.

**Expected result:** one newly acquired, valid and correctly typed tactile measurement **only if hardware and firmware support it**, or an explicit absent/unsupported report. No motor motion is required.

#### Offline sample validity exercise

```python
def usable(sample):
    return (
        sample.get("present") is True
        and sample.get("meta_valid") is True
        and sample.get("meta_stale") is False
        and any(sample.get("valid_values", []))
    )

assert usable({"present": True, "meta_valid": True, "meta_stale": False, "valid_values": [True]})
assert not usable({"present": False, "meta_valid": True, "meta_stale": False, "valid_values": []})
```

The expected output is **two passing assertions** in an ordinary Python environment; this is an _illustrative software-only filter_, not the exact ROS message structure.

### Troubleshooting and FAQs

**Why is O20 tactile refresh not 1000 Hz?** Its manual reports **30 Hz tactile refresh**; 1000 Hz refers to the control communication layer.

**Why is an O6 tactile topic empty?** The OEM specifies an **optional** sensor; check whether it is physically installed before diagnosing a malfunction.

**Why doesn't O30 expose a 6×12 normal matrix?** Its manual reports **6×11** and the newer SDK uses a descriptor payload for O30.

### Downloads and technical documents

* [Official Linkerbot tactile field reference](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/force.md).
* [SDK model matrix](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/models.md).
* [Original Linkerbot manuals in OpenELAB Wiki](../).

### References and validation

* The seven supplied OEM manual revisions; sensor parameter tables and optional sensor descriptions, reviewed 2026-11-21.
* [Current Linkerbot ROS 2 force guide](https://github.com/linker-bot/linkerbot-hand-ros2-sdk/blob/main/linkerbot_hand_ros/docs/force.md), reviewed 2026-11-21.

**Documentation:** reviewed. **Software execution:** not run. **Hardware validation:** not run. Distinguish raw counts, force units and absent sensors; no assumed calibration or force safety certification.
