---
description: >-
  Review H2-X camera, battery and compute configurations, distinguish its ankle
  mapping from H2, and run offline contract checks without assuming charging or
  firmware compatibility.
---

# Unitree H2-X and H2-X EDU: model differences and SDK state contracts

{% hint style="info" %}
**Manufacturer reference: Unitree H2-X / H2-X EDU.** No exact OpenELAB product URL or SKU was observed in the reviewed store listings. Store match is unverified; no purchasing link is inferred.

**Scope:** 31-joint H2-X biped, with distinct base/EDU columns. H2, H2-D and the separately named H2 Plus are not interchangeable identities.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree H2-X is a full-size humanoid with 31 body joints, a head LED display, binocular and chest camera sensing, and a dual hot-swappable battery architecture. It has its own manufacturer specifications and SDK2 example directory. This guide supports exact-model comparison and an offline source-contract check. Physical commissioning remains a **source-bounded draft** because an H2-X-specific user/battery/remote manual, delivered firmware pair and electrical pinout have not been read. [Official H2-X page](https://www.unitree.com/H2-X/)

H2-X is not an H2 with a cosmetic enclosure change. Its published dimensions, mass, arm/leg torque limits, segment lengths and battery voltage differ. More subtly, the pinned SDK examples label the ankle slots differently. Identical joint counts or HG message types do not establish mechanical, electrical or software interchangeability. The manufacturer marks secondary development YES for H2-X EDU and slash for base H2-X. [Manufacturer table](https://www.unitree.com/H2-X/), [pinned H2-X source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x/low_level/h2x_ankle_swing_example.cpp)

## Applications <a href="#applications" id="applications"></a>

The official page lists security, industrial manufacturing, commercial and home services as application scenarios. Treat these as proposed settings, not evidence of certification, autonomous patrol readiness or permission to operate around people. The same page says some functions remain under development. Its “all-weather” positioning supplies no ingress rating or model-specific wet-operation procedure. [H2-X features and notes](https://www.unitree.com/H2-X/)

For engineering work, H2-X EDU offers a source-backed starting point for body-state integration and configuration review. The LED display and audio hardware suggest supervised interaction research; camera calibration and accessible streaming APIs are still needed. Dual batteries may reduce downtime, but an advertised hot-swap architecture cannot establish the safe removal order, remaining-pack state or load restrictions. Use this guide to identify those required contracts before scheduling a live demonstration.

## Specifications <a href="#specifications" id="specifications"></a>

All figures below are from the exact H2-X product page as read November 24, 2026. The page is undated and configuration dependent; values are not measurements from a purchased robot. [Official specification table](https://www.unitree.com/H2-X/)

| Parameter                             | H2-X                                                                                    | H2-X EDU / condition                                                                                            |
| ------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Standing height × width × thickness   | 1725 × 455 × 245 mm                                                                     | Same published dimensions; feature heading rounds height to about 170 cm                                        |
| Mass including batteries              | 65+ kg                                                                                  | Varies with model/configuration                                                                                 |
| Body joints                           | 31                                                                                      | 31; optional hand actuators are separate                                                                        |
| Per-leg / per-arm / waist / head DoF  | 6 / 7 / 3 / 2                                                                           | Same body arrangement                                                                                           |
| Dexterous hands                       | Slash                                                                                   | Multiple models optional                                                                                        |
| Head display                          | LED status display                                                                      | Same; feature text describes custom patterns/video                                                              |
| Bearings / motors                     | Crossed-roller bearings; low-inertia inner-rotor PMSM                                   | Not a field-replaceable actuator specification                                                                  |
| Maximum arm / leg joint torque        | 150 / 300 N·m                                                                           | Scenario/configuration dependent; no continuous torque supplied                                                 |
| Arm payload                           | Peak about 15 kg; rated about 7 kg                                                      | Posture/application qualification still needed                                                                  |
| Calf + thigh / arm segment length     | 845 / 529 mm, arm length excluding hand                                                 | Do not import H2's 1045 / 690 mm geometry                                                                       |
| Structure / cooling                   | Aerospace aluminum, engineering plastic, energy-absorbing cushioning; local air cooling | No published IP rating in the reviewed evidence                                                                 |
| Power architecture                    | Dual hot-swappable low-internal-resistance lithium batteries                            | Actual hot-swap procedure unresolved                                                                            |
| Combined battery capacity             | 20 Ah, 1.152 kWh                                                                        | Combined figure, not per battery                                                                                |
| Maximum battery voltage               | 67.2 V                                                                                  | Not H2's 75.6 V, and not a charger selection instruction                                                        |
| Body magnetic charging                | Charging current 7 A                                                                    | Voltage, polarity, mating orientation and approved adapter part number unresolved                               |
| PC1                                   | 8-core high-performance CPU                                                             | Platform functions                                                                                              |
| PC2                                   | Slash / not separately listed                                                           | Intel Core i7 **or** Orin NX, one of two choices                                                                |
| PC3                                   | Slash                                                                                   | Optional Thor T5000 **or** Orin AGX; verify actual order                                                        |
| Sensing                               | Head binocular + chest wide-angle monocular                                             | Additional chest RGBD optional on EDU                                                                           |
| Voice / radio                         | Microphone array, high-power speaker; Wi-Fi and Bluetooth                               | Exact wireless revisions are not stated here                                                                    |
| Optional wireless MI                  | Slash                                                                                   | 2.4 GHz, max 50 m line of sight, SNR ≥80 dB, about 5 h runtime; this is an accessory row, not robot radio range |
| Accessories listed                    | Charger, body charging adapter, quick-release battery, manual controller                | Verify actual quantities and matched battery set                                                                |
| Static / continuous walking endurance | About 8 / 4 h                                                                           | Different workloads; not guaranteed endurance under payload                                                     |
| OTA / secondary development           | OTA YES; development slash                                                              | OTA YES; development YES                                                                                        |
| Warranty reference                    | 8 months                                                                                | 12 months; sale terms apply                                                                                     |

### Camera parameters and their limits <a href="#camera-parameters-and-their-limits" id="camera-parameters-and-their-limits"></a>

The feature panel gives a stereo depth FOV of H87° × V58° and depth resolution 1280 × 720; RGB is 1920 × 1080 at 30 fps with H69° × V42° FOV. The monocular camera is 2048 × 2048 at 30 fps, H100° × V100°. The page does not give a depth frame rate, depth accuracy, minimum range, calibration file or timestamp/frame convention. Do not infer them from the RGB stream. The optional chest RGBD camera is not established to have these same specifications. [H2-X complex-environment perception panel](https://www.unitree.com/H2-X/)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

[Original Unitree H2-X architecture figure](https://www.unitree.com/images/b7d78affa59a4ef49d8b2e56ca48a46b_1921x2380.png?x-oss-process=image/format,webp) shows the two rear batteries, head/chest cameras, LED matrix, optional compute and body-axis distribution. It is a feature illustration, not a connector pinout or hot-swap sequence. The figure labels up to Thor T5000 at 2070 TOPS; the table identifies that as an optional EDU compute choice, not standard equipment.

H2-X's dual battery and magnetic charging system is distinct from H2's removable single pack. **Do not connect an H2 charger, H2 breakout cable or improvised magnetic adapter.** The 67.2 V maximum battery figure and 7 A charging-current row do not specify a power-input pinout, charge profile or safe external supply. Charging, pack insertion/removal, hot-swap and custom power are blocked until the exact H2-X battery/charger manual and delivered component part numbers are available. [H2-X power rows](https://www.unitree.com/H2-X/)

No H2-X connector-location drawing, accessory-output voltage/current budget, connector orientation, logic levels, Ethernet subnet or screw torque was verified in the reviewed sources. H2's 15-port map and 500 W peripheral budget cannot fill those gaps. Likewise, a USB-shaped connector or a URDF mesh does not establish physical power routing. Leave unknown ports unconnected; retain labels/photos in the unit's configuration record for manufacturer clarification.

The manufacturer's page cautions about distance from the powerful humanoid but supplies no startup pose, protective-stand procedure or remote-stop state machine. Therefore no H2 suspension, startup key combination, calibration fixture, shutdown sequence or emergency-stop behavior is assigned to H2-X here. Obtain the H2-X operator and remote manuals, compatible controller revision and firmware-specific stop behavior before live power. The public scenario “all-weather” must not be converted into a water-resistance claim. [Official page notes](https://www.unitree.com/H2-X/)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

Unitree SDK2 **C++ commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`** contains actual `example/h2x` sources. The upstream README identifies Ubuntu 20.04 LTS, aarch64/x86\_64 and GCC 9.4.0 as its prebuild environment. No SDK installation, build, DDS, ROS or robot program was run for this guide. A prebuilt-library environment and an EDU development entitlement still do not identify the correct delivered robot image. [Pinned SDK README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md)

| Actual H2-X source            | Engineering meaning                                                                                                       | First-result suitability                                                     |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| `h2x_ankle_swing_example.cpp` | 31 body motors; HG state/command messages; 500 Hz source control loop; zero posture then ankle motion                     | Actuates; do not run for identification                                      |
| `h2x_dual_arm_example.cpp`    | Moves all 31 joints to zero, then replays 14 arm joints from `motion.seq` while legs/waist/head hold zero; needs yaml-cpp | Motion playback, not a passive hand/arm probe                                |
| `low_level/terminations.cpp`  | Subscribes to `rt/lowstate`, no publisher or mode-changing RPC; default DDS domain 0 and selected interface               | Source reference only pending qualification and freshness/concurrency repair |
| `h2x/common/terminations.hpp` | Orientation, joint/angular velocity, winding/casing temperature, battery and missing-state predicates                     | Predicates alone do not stop the robot                                       |
| `CMakeLists.txt`              | yaml-cpp/Eigen-dependent targets are conditional                                                                          | A missing executable can be a dependency issue; building was not attempted   |

[Pinned H2-X README and source directory](https://github.com/unitreerobotics/unitree_sdk2/tree/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x)

### Ankle order and transport capacity <a href="#ankle-order-and-transport-capacity" id="ankle-order-and-transport-capacity"></a>

The H2-X enum assigns left ankle **pitch=4 / roll=5**, right ankle **pitch=10 / roll=11**, waist yaw/roll/pitch=12/13/14, left arm=15–21, right arm=22–28 and head pitch/yaw=29/30. In contrast, the reviewed H2 enum uses roll=4/pitch=5 and roll=10/pitch=11. H2-X's PR and AB representations are separately named; shared slot numbers do not make parallel-actuator and joint-coordinate values interchangeable. [H2-X ankle source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x/low_level/h2x_ankle_swing_example.cpp)

HG `LowState_` has 35 motor slots. H2-X source uses 31 body indices; do not report 35 active physical joints or infer an optional hand mapping in the remaining slots. Confirm `mode_machine`, active joint map, sign conventions and telemetry units against the delivered firmware before a state viewer labels the values. [Pinned HG IDL](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/LowState_.hpp)

### A subscriber warning is not an emergency stop <a href="#a-subscriber-warning-is-not-an-emergency-stop" id="a-subscriber-warning-is-not-an-emergency-stop"></a>

The termination executable prints orientation and connection warnings every 100 ms, with a 1 rad orientation threshold and a 1000 ms no-state threshold in its source. These are example parameters, not validated safety limits. It checks orientation without first qualifying a received sample and shares the state object between callback and polling thread without an explicit lock. A production diagnostic needs synchronized snapshots, a first-sample flag, finite-value validation and monotonic freshness/tick checks. Even then, a passive monitor cannot bring H2-X to a safe state; a model-specific operator/stop procedure is independently necessary. [Termination source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x/low_level/terminations.cpp)

No exact H2-X high-level locomotion service compatibility was verified. Do not assign H2's `sport` getters/setters or Python H2 client to H2-X merely because SDK2 has a low-level H2-X directory. SDK2's BSD-3-Clause root license was read; third-party notices remain applicable. [License](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/LICENSE)

### Portal expansion scope: H2-X remains a distinct target <a href="#portal-expansion-scope-h2-x-remains-a-distinct-target" id="portal-expansion-scope-h2-x-remains-a-distinct-target"></a>

The supplied current portal collections contain **43 H1-family, 29 H2 and 37 G1+ records**. Their article text has now been reviewed, including empty category nodes and repeated shared-service descriptions. A text search of the supplied complete article cache found no exact `H2-X`/`H2X` match. This is a finding about the supplied snapshot, not a claim that Unitree has no H2-X documentation elsewhere.

The [H2 resource chapter](https://doc-cdn.unitree.com/25/1264/en/25_1264_en) and [H2Plus GMSL chapter](https://doc-cdn.unitree.com/25/1576/en/25_1576_en) identify H2-family resources and H2Plus camera configurations. **H2Plus is not established as an alias for H2-X.** Their PC addresses, mixed power/data connectors, single-pack charging values, stereo-service controls, head calibration and remote state transitions are therefore not assigned to H2-X. The existing exact H2-X product and pinned `example/h2x` source findings above remain the accepted scope.

The SDK transport definitions can explain shared HG serialization, but the delivered H2-X firmware, domain/interface, array-to-physical-joint map, permissions and stop behavior still require exact qualification. No additional live program or controller handover is introduced by this portal expansion.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Prerequisites and model qualification <a href="#prerequisites-and-model-qualification" id="prerequisites-and-model-qualification"></a>

Keep H2-X disconnected. Use a browser for pinned-source inspection and, optionally, Python 3 for the self-contained synthetic example. Exact H2-X operator/power/remote instructions, developer entitlement, firmware/image, active joint map, network settings and safe stop behavior must be resolved before any later live session. H2 instructions do not fill those gaps.

### First working result: identify H2-X's published state/control boundary <a href="#first-working-result-identify-h2-xs-published-statecontrol-boundary" id="first-working-result-identify-h2-xs-published-statecontrol-boundary"></a>

1. Open the [H2-X README at commit b7fec602](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x/README.md). Identify the three programs and distinguish the ankle/arm motion examples from the termination subscriber. Do not launch any example.
2. Open the [H2-X ankle source at that commit](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x/low_level/h2x_ankle_swing_example.cpp). Find `H2X_NUM_MOTOR` and `H2XJointIndex`: 31 body motors; left ankle pitch 4 / roll 5, right ankle pitch 10 / roll 11; head pitch/yaw 29/30.
3. Compare the [H2 ankle enum](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2/low_level/h2_ankle_swing_example.cpp), which labels those ankle positions roll/pitch in the opposite order. Then inspect [HG LowState\_.hpp](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/LowState_.hpp) and its 35 transport slots.
4. Read the [H2-X termination source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x/low_level/terminations.cpp). Locate its `rt/lowstate` subscriber, polling loop and missing-message check. Identify that it prints warnings rather than sending a stop command, and that first-sample/freshness/concurrency qualifications remain necessary.

**Expected result:** a note stating “H2-X: 31 body joints; ankle pitch/roll 4/5 and 10/11; head 29/30; HG: 35 slots; motion examples publish commands; termination only warns.” This identifies a meaningful source boundary without connecting a robot.

An unavailable pinned link means that inspection remains incomplete. Do not substitute H2's enum, a different release or a command demo to compensate.

### Self-contained synthetic log check <a href="#self-contained-synthetic-log-check" id="self-contained-synthetic-log-check"></a>

Copy the complete Python example below into a new file named `telemetry_log_check.py`, then run `python3 telemetry_log_check.py` with Python 3. It uses only the standard library and the data included in the example. The example needs no SDK, configuration file or robot/network connection.

```python
import math


def inspect_sample(sample, now_ms, previous_tick=None):
    # Synthetic receive times in one monotonic clock domain; not wall-clock time.
    if sample is None:
        return "REJECT missing sample"
    received = sample.get("received_ms")
    tick = sample.get("tick")
    values = sample.get("values")
    if type(received) not in (int, float) or not math.isfinite(received):
        return "REJECT invalid receive time"
    age_ms = now_ms - received
    if age_ms < 0 or age_ms > 1000:
        return "REJECT stale or future sample"
    if type(tick) is not int or not 0 <= tick < 2**32:
        return "REJECT invalid tick"
    if not isinstance(values, list) or not values or not all(
        type(v) in (int, float) and math.isfinite(v) for v in values
    ):
        return "REJECT invalid values"
    if previous_tick is not None:
        delta = (tick - previous_tick) % 2**32
        if not 0 < delta < 2**31:
            return "REJECT repeated or backward tick"
        return "ACCEPT advancing tick"
    return "ACCEPT first sample"


sample = {"received_ms": 1500, "tick": 11, "values": [0.1, -0.2]}
cases = [
    (None, None, "REJECT missing sample"),
    (sample, None, "ACCEPT first sample"),
    (sample, 10, "ACCEPT advancing tick"),
    (sample, 11, "REJECT repeated or backward tick"),
    ({**sample, "received_ms": 999}, 10, "REJECT stale or future sample"),
    ({**sample, "values": [float("nan")]}, 10, "REJECT invalid values"),
    ({**sample, "tick": 0}, 2**32 - 1, "ACCEPT advancing tick"),
]
for data, previous, expected in cases:
    result = inspect_sample(data, now_ms=2000, previous_tick=previous)
    if result != expected:
        raise RuntimeError((result, expected))
    print(result)
print("PASS: 7 synthetic cases; no robot connection")
```

**Expected result:** the seven acceptance/rejection lines below, followed by the PASS line. The first accepted sample has no previous tick; later samples must advance. The last case exercises unsigned 32-bit wrap. The code checks finite values and receive-time age separately from tick progression.

```
REJECT missing sample
ACCEPT first sample
ACCEPT advancing tick
REJECT repeated or backward tick
REJECT stale or future sample
REJECT invalid values
ACCEPT advancing tick
PASS: 7 synthetic cases; no robot connection
```

The two example values are arbitrary synthetic numbers, **not a robot joint layout or packet schema**. The 1000 ms window and unsigned 32-bit tick rule demonstrate diagnostic logic only; they are not certified safety limits or an assumption about every robot's telemetry. Real logs require the documented model-specific timestamp, rollover, session/restart and unit conventions. A controller restart must reset or requalify the previous-tick baseline. These cases are independent tests, not one continuous measured stream.

**If this check fails:** confirm that the entire example was copied, run it with Python 3, and compare the error/result with the expected lines. A stale/repeated/nonfinite sample must remain rejected; do not remove those checks to obtain PASS. Passing this example proves only that this synthetic logic behaves as shown.

### Qualification required before a later live read <a href="#qualification-required-before-a-later-live-read" id="qualification-required-before-a-later-live-read"></a>

After the exact H2-X EDU order/serial, options, battery/charger, controller/stop revision, firmware/image, active map and network contract are qualified, an independently reviewed subscriber can wait for fresh state without publishing, releasing modes or requesting posture changes. Confirm increasing ticks, finite values and sample age before logging data. This guide supplies no connected command while those critical facts remain unresolved.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Can the H2 battery manual be used because both robots have 31 joints?** No applicability was established. H2-X has dual hot-swap batteries and a lower published maximum voltage. Use exact H2-X pack, charger, controller and instructions; leave power work blocked. [H2-X specification table](https://www.unitree.com/H2-X/)

**The source prints a lost-connection warning.** First distinguish no first sample from a later stale stream. Verify the selected interface/domain, model-specific network instructions, source revision and edition access. Do not start an ankle/arm example to “wake” telemetry. A silent subscriber is not a safe-state assertion. [H2-X termination source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x/low_level/terminations.cpp)

**My model has a chest RGBD camera but the table gives different camera numbers.** The EDU chest RGBD is optional. The reviewed feature panel's stereo/monocular numbers do not identify that optional camera. Obtain its exact model, calibration and stream contract before using it for depth work. [H2-X camera panel and option rows](https://www.unitree.com/H2-X/)

**Why is `h2x_termination` absent from a build someone supplied?** The pinned CMake file conditions targets on dependencies; Eigen is needed for termination and yaml-cpp for dual-arm playback. Verify source/build provenance before accepting a binary. This guide did not build or test it. [H2-X CMake](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x/CMakeLists.txt)

**Does a security application imply rain operation or autonomous patrol?** No ingress rating, operator procedure or autonomous safety case was verified. Obtain explicit model-specific limits; do not transfer H2 limits or substitute a marketing scenario for an engineering qualification. [Manufacturer feature/notes](https://www.unitree.com/H2-X/)

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                       | Use / version                                                                               | Link                                                                                                                                                           |
| ------------------------------ | ------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| H2-X product and feature table | Exact-model base/EDU differences; undated live page                                         | [Official H2-X](https://www.unitree.com/H2-X/)                                                                                                                 |
| H2-X SDK examples              | C++ SDK2 commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`                                  | [Pinned H2-X directory](https://github.com/unitreerobotics/unitree_sdk2/tree/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/h2x)                             |
| Termination predicates         | Understand checks and their limitations                                                     | [H2-X header](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/h2x/common/terminations.hpp) |
| Model descriptions             | `unitree_ros` commit `157ff950351e5f535e03c5d85a16b7d594b3dbcc`; H2-X row lists 31 (37) DoF | [Pinned model catalog](https://github.com/unitreerobotics/unitree_ros/blob/157ff950351e5f535e03c5d85a16b7d594b3dbcc/README.md)                                 |
| Support document center        | Obtain exact model operator, battery, remote and developer documentation                    | [Official portal](https://support.unitree.com/main/en)                                                                                                         |

The model catalog explains parenthesized counts can include transmission joints. A description asset does not establish physical SDK authorization, Gazebo controller coverage or firmware compatibility. Its complete Gazebo-controller list excludes H2-X; do not run quadruped launch instructions against this model.

An H2-X manual set, full wiring/pinout, mounting drawing, approved charging protocol and exact firmware compatibility table were not observed in the reviewed accessible material. They remain explicit resource gaps, not claims that Unitree has never produced them. The English H2 manual index is **not** an H2-X manual index. Compare [H2 manufacturer specifications](https://www.unitree.com/H2/) and [G1+ manufacturer specifications](https://www.unitree.com/G1pl/) only through their separate evidence.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed November 24, 2026: official H2-X product content, pinned SDK2 H2-X README, ankle/termination/CMake sources, termination header, HG IDL and the pinned Unitree ROS model catalog.

**Readiness:** source-bounded draft. Power, stop/commissioning, developer entitlement on the actual unit, firmware/SDK pairing, network and physical pinout remain unresolved. No H2 developer portal article or manual is represented as H2-X documentation. No H2-X developer article content is claimed reviewed here.

**Offline validation:** the standalone seven-case synthetic example was executed successfully; this does not test robot connectivity. **Vendor software execution:** not run; no SDK install/build/import, ROS or DDS. **Hardware validation:** not run; no charging, hot-swap, motion, calibration or flashing.

**Related documentation:** [Unitree model and development directory](./).

**Related documentation:** [Unitree model and development directory](./).
