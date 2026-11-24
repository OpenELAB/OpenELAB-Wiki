---
description: >-
  Understand the single Dex2/5 two-actuator product, conditioned payload, R1
  motor indices, G1 service ownership and unresolved torque-only control
  requirements.
---

# Unitree Dex2/5: tendon hand and host-specific control

{% hint style="info" %}
**Model reference — unlisted store product.** Dex2/5 is one slash-named, five-finger product with two actuators, not separate Dex2 and Dex5 products. No OpenELAB SKU or product URL was verified. This reference uses the actual manufacturer product page and G1/R1 portal articles; it does not qualify an arbitrary firmware or standalone RS485 driver. Hardware readiness is **draft**. [Product](https://www.unitree.com/Dex2-5), [R1 mapping](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands), [G1 interface](https://support.unitree.com/home/en/G1_developer/hand_sdk).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

The manufacturer describes a ten-DOF tendon-driven hand with two actuated groups. One actuator drives the thumb; the index, middle, ring and little fingers share the other actuated degree of freedom. Ten described joint motions therefore do not imply ten independently commandable motor slots. The transmission uses a gear–tendon rope drive. [Introduction and mechanism](https://www.unitree.com/Dex2-5).

The product page lists internal wiring compatibility with G1/R1. That is a host-family statement, not a firmware qualification or a common low-level index map. The G1 hand service blends a four-motor GO command message through `ai_sport`, while the R1 article assigns hand entries within a whole-body HG low-level array. These paths have different ownership and control hazards. They cannot be connected by changing topic names alone. [Internal wiring](https://www.unitree.com/Dex2-5), [G1 hand SDK](https://support.unitree.com/home/en/G1_developer/hand_sdk), [R1 hand sequence](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands).

The advertised fatigue and drop-test figures are greater than100,000 fatigue cycles and greater than100 drop tests. The source does not publish the complete test protocol, specimen count, allowable payload degradation or a certified service life. Treat them as manufacturer test claims rather than maintenance intervals or safety certification. [Reliability claims](https://www.unitree.com/Dex2-5).

## Applications <a href="#applications" id="applications"></a>

Dex2/5 suits studies of coordinated enveloping grasps where a lightweight hand and two actuator groups are acceptable. It does not provide independent positioning of all five fingertips. Planning should account for the shared four-finger actuator and tendon coupling; a planner that assumes separate index/middle/ring/pinky motor control will not describe this mechanism. [Actuation layout](https://www.unitree.com/Dex2-5).

The product's1.5 kg holding claim applies at room temperature while grasping a5 cm round hard object, with the palm down or left. It is not a general payload rating for arbitrary tools, surfaces, acceleration or extended carrying. The thumb's15 N and the other four fingers' **combined**15 N are separate specifications; the latter is not15 N at each finger. [Load and strength rows](https://www.unitree.com/Dex2-5).

Useful first work includes documenting the installed host, side, hand selection and delivered firmware, checking the model-specific wiring documentation, and validating an offline index-label extractor. Do not begin by executing the R1 whole-body example, changing peripheral settings or sending grip torque. Host configuration and restart are later active integration steps.

## Specifications <a href="#specifications" id="specifications"></a>

| Item                                     | Manufacturer specification / condition                             |
| ---------------------------------------- | ------------------------------------------------------------------ |
| Configuration                            | Five fingers; ten described DOF; two actuated groups               |
| Transmission                             | Gear–tendon rope                                                   |
| Mass / flat dimensions                   | 365 g;151×70×63 mm                                                 |
| Thumb joint ranges                       | Joint0:0–42°; joint1:0–105°                                        |
| Shared four-finger joint ranges          | Joint0:0–88°; joint1:0–105°                                        |
| Minimum fist-clench time / grip diameter | 0.5 s /8 mm; headline limits, not a test recipe                    |
| Fingertip strength                       | Thumb15 N; other four fingers together15 N                         |
| Supply / current                         | 24–60 V; static58 V@0.1 A; maximum58 V@1.5 A                       |
| Communication                            | RS485; listed communication rate1000 Hz                            |
| Operating temperature                    | −20 to60°C; no verified IP rating                                  |
| Holding load                             | 1.5 kg, room temperature,5 cm round hard object, palm down or left |

All values are from the [exact product table](https://www.unitree.com/Dex2-5). Joint limits are mechanical product claims, not an actuator-to-joint conversion, gain limit or torque command range. The source lists feedback concepts: mode, position, velocity, torque, temperature, voltage and current. Its “control feedback” row names mode, position, velocity, torque, stiffness and damping. The R1 portal nevertheless explicitly limits Dex2/5 to torque control; do not interpret the generic product row as permission to command position gains on R1. [R1 torque-only statement](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands).

The1000 Hz communication headline does not establish serial bit rate, address, packet layout, CRC, command acknowledgment or firmware compatibility. No delivered bus measurements or power tests were performed. Product parameters may vary by configuration, as the manufacturer notes; use the exact revision documents for electrical and thermal qualification.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Internal host wiring <a href="#internal-host-wiring" id="internal-host-wiring"></a>

The R1 article says the cable is routed through the arm and that the corresponding hand must be selected in Unitree Explore followed by a robot restart. Record the installed configuration first. Changing this selection or restarting a robot can change active control behavior and is outside the offline first check. G1's host service is separate; the R1 whole-body indices below are not verified G1 indices. [Host configuration](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands), [G1 interface](https://support.unitree.com/home/en/G1_developer/hand_sdk).

The manufacturer product confirms RS485 and24–60 V but does not provide connector cavity assignments, a standalone harness drawing, termination, ground reference or fuse/current-limit prescription. Do not reuse Dex1-1's pictured XT30PW(2+2) pinout or its single-motor protocol merely because both hands use an internal host option. Wrong polarity or voltage can damage electronics; undocumented cavities remain a connection blocker. [Electrical table](https://www.unitree.com/Dex2-5).

### Mechanical and environmental preparation <a href="#mechanical-and-environmental-preparation" id="mechanical-and-environmental-preparation"></a>

Obtain the actual wrist adapter, cable exit, mounting screw lengths/torques and side-specific assembly instructions. The151×70×63 mm flat-state envelope does not define a drilling template. The saved R1 installation article is a video embed; its text was read, but its video was not watched and no step-by-step mechanical procedure is inferred from it. [Installation listing](https://support.unitree.com/home/en/R1_developer/Dex2-5%20%20Installation).

The−20 to60°C working range is not an ingress rating or permission to operate while wet, condensed, contaminated or in explosive atmospheres. Protect exposed cables and tendon/finger pinch zones under the approved installation procedure. No lubricant, tendon tensioning, recalibration or service interval was verified in the read sources; do not improvise these from another hand model.

### Stop and load-retention gate <a href="#stop-and-load-retention-gate" id="stop-and-load-retention-gate"></a>

Before powered work, establish independent stop access, the exact controller's lost-command behavior, how to remove stored energy and what happens to a held object on release or power loss. A torque-only grasp can release or continue clamping depending on the actual command/firmware; neither zero torque nor a host blending weight is a safety-rated stop. No delivered stop or watchdog timing was verified here. Retain this as a hardware-readiness gap rather than filling it with a generic SDK timeout.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### R1: whole-body HG indices, not a standalone hand array <a href="#r1-whole-body-hg-indices-not-a-standalone-hand-array" id="r1-whole-body-hg-indices-not-a-standalone-hand-array"></a>

The [actual R1 hand article](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands) assigns these entries in `LowCmd_.motor_cmd` and `LowState_.motor_state`:

| Index | Dex2/5 meaning                    | Scope           |
| ----- | --------------------------------- | --------------- |
| 31    | Left shared four-finger actuator  | R1 host mapping |
| 32    | Left thumb actuator               | R1 host mapping |
| 33    | Right shared four-finger actuator | R1 host mapping |
| 34    | Right thumb actuator              | R1 host mapping |

Dex1-1 uses31 and33 for its single left/right grippers; its missing thumb entries do not turn Dex2/5 into the same device. R1 whole-body commands also include non-hand motors, mode/ownership and transport concerns. Publishing an incompletely populated low-level command can affect the entire robot. A whole-body example is therefore not a safe hand-only test. [R1 sequence and linked routine](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands), [pinned R1 example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/r1/low_level/r1_A5_wrist_swing_example.cpp).

The same R1 article says Dex2/5 **only supports torque control**, then gives generic `kp=40`, `kd=2` instructions. These statements conflict for this hand. This guide does not prescribe those gains. Require the exact supported torque units, signs, maximum values and firmware mode before any active hand command; do not resolve the contradiction by experimenting on hardware.

### G1 and G1+: blended service ownership <a href="#g1-and-g1-blended-service-ownership" id="g1-and-g1-blended-service-ownership"></a>

The actual G1 hand article documents the **command interface only**: publish GO `unitree_go::msg::dds_::MotorCmds_` with four command entries to `rt/hand_sdk`, where the running `ai_sport` service blends position, velocity, torque and both gains with its defaults. Only `cmds[0].mode` stores the integer `weight * 100` in 0–100; the other three mode fields are unused. Decode the blend weight as `cmds[0].mode / 100.0`. Under this service's sign convention, positive torque closes and negative torque opens. The article and pinned example do **not** establish a G1 hand state topic, message type, motor count, ordering or populated feedback fields. A generic GO `MotorStates_` declaration is not a runtime state binding, and the standalone Dex1 state topics are not a substitute. [DDS interface and command layout](https://support.unitree.com/home/en/G1_developer/hand_sdk), [pinned publisher-only example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/high_level/g1_hand_sdk_example.cpp).

For this documented host/service, user commands are **not forwarded during damping**. After leaving damping, the user must explicitly set the blend weight again. If the host defaults and external targets differ, an abrupt weight change from 0 to 1 can cause sudden hand motion. The source's transition warning is retained as a qualification requirement, not an executable ramp or commissioning procedure. If publishing times out, control falls back to `ai_sport` defaults; that does **not** guarantee stop, holding force or load retention. These ownership behaviors require the compatible installed hand, running service and delivered firmware to be confirmed. [Mode and transition notes](https://support.unitree.com/home/en/G1_developer/hand_sdk), [G1+ duplicate notes](https://support.unitree.com/home/en/G1pl_developer/hand_sdk).

No four-slot left/right/thumb ordering was established from the read G1 example, which fills all four uniformly. The R1 table must not be substituted. G1+ has a byte-identical saved hand article; that duplication adds no new firmware evidence. The exact service configuration, delivered firmware and hand selection remain prerequisites. [G1+ article](https://support.unitree.com/home/en/G1pl_developer/hand_sdk), [pinned service example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/high_level/g1_hand_sdk_example.cpp).

### Pinned source and raw-state ownership <a href="#pinned-source-and-raw-state-ownership" id="pinned-source-and-raw-state-ownership"></a>

Public SDK2 commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d` and Python SDK commit `814556d15970dd2ecf1c9984e845ca02ab07e206` are static source references, not a tested Dex2/5 deployment pair. The common C++ build declarations and Python setup do not supply a delivered-hand firmware minimum. The SDK's BSD-3-Clause license applies to its own source; it does not license every portal video or proprietary binary. [SDK README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), [license](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/LICENSE), [Python setup](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py).

The generic GO `MotorStates_` declaration is a vector wrapper inspected only as schema context; it does not establish a G1/G1+ hand state endpoint or publication behavior. A current HG motor-state declaration includes mode, q/dq/ddq, estimated torque, temperatures, voltage, sensors and reserved/status words. The R1 article supplies its own R1-only state indices; those generic fields do not prove Dex2/5 fills every field or that torque is measured contact force. Keep the independently verified host state binding, indexing and units together. Copy values into application-owned snapshots when callbacks return; preserve device timing/loss and local receipt separately rather than retaining a mutable callback object. [GO state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/MotorStates_.hpp), [HG motor state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/MotorState_.hpp).

At the C++ pin, the factory takes two arguments, domain and interface. The portal's additional shared-memory argument is not supported by that header. Network selection/domain alone is not isolation, and no DDS activation is needed for the example below. [Pinned factory](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_factory.hpp).

## Getting started <a href="#getting-started" id="getting-started"></a>

1. Keep the robot and hand unpowered; use an ordinary offline workstation.
2. Copy only the original Python program below into the named local file.
3. Run it with Python 3 and compare the **Expected output**; an offline pass does not authorize hardware.

### First result: offline labels for the documented R1 entries <a href="#first-result-offline-labels-for-the-documented-r1-entries" id="first-result-offline-labels-for-the-documented-r1-entries"></a>

The original standard-library program below uses a synthetic mapping of index to position, not a vendor message or a live robot. Save it as `dex25_labels.py`, then run `python3 dex25_labels.py`. It does not construct a whole-body command, choose a control mode or connect to anything.

```python
from math import isfinite
from numbers import Real

LABELS = ((31, "left_four_fingers"), (32, "left_thumb"),
          (33, "right_four_fingers"), (34, "right_thumb"))

def snapshot(host, values):
    if host != "R1":
        raise ValueError("no verified index map for this host")
    result = []
    for index, label in LABELS:
        if index not in values:
            raise ValueError(f"missing R1 entry {index}")
        value = values[index]
        if isinstance(value, bool) or not isinstance(value, Real):
            raise ValueError("position must be a real scalar")
        value = float(value)
        if not isfinite(value):
            raise ValueError("nonfinite position")
        result.append((index, label, value))
    return tuple(result)

if __name__ == "__main__":
    synthetic = {31: 0.0, 32: 0.0, 33: 0.0, 34: 0.0}
    copied = snapshot("R1", synthetic)
    synthetic[31] = 99.0
    print(f"OFFLINE PASS: {len(copied)} labeled R1 entries; "
          f"first={copied[0][1]}; copied_q={copied[0][2]}")
    print("force_N=unverified; hardware_tested=False")
```

Expected output:

```
OFFLINE PASS: 4 labeled R1 entries; first=left_four_fingers; copied_q=0.0
force_N=unverified; hardware_tested=False
```

This confirms only the original extractor's labels, finite-scalar checks and copied ownership. The zeros are synthetic values, not a neutral/open/closed command or a real-hand calibration. Calling it for G1 deliberately fails because this guide has no verified G1 slot order. A later read-only capture needs an independently approved existing state path and documented host/firmware; running an arbitrary vendor low-level example is not that path.

### Before any later active work <a href="#before-any-later-active-work" id="before-any-later-active-work"></a>

Resolve the exact host/side/hand configuration, verify harness and mechanical assembly, obtain the firmware-bound torque contract and approved stop/restart procedure, and secure any retained load. Confirm that only the intended hand service owns commands and that a whole-body publisher cannot compete. No motion, gain tuning, peripheral-selection change or reboot is prescribed as an initial check.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### Why do ten joints produce only two actuator groups? <a href="#why-do-ten-joints-produce-only-two-actuator-groups" id="why-do-ten-joints-produce-only-two-actuator-groups"></a>

Joint articulation and independent actuation are different. The thumb has one actuation group; the other four fingers share one. Do not allocate a motor command for every described joint angle or assume a ten-element q array is the hardware contract. [Configuration table](https://www.unitree.com/Dex2-5).

### Can I use the R1 table on G1? <a href="#can-i-use-the-r1-table-on-g1" id="can-i-use-the-r1-table-on-g1"></a>

The read sources define different host paths. R1 embeds four hand entries at31–34 in HG whole-body state; G1 uses a four-entry GO hand-service message without a verified slot ordering here. The product's G1/R1 compatibility headline does not erase those differences. [R1](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands), [G1](https://support.unitree.com/home/en/G1_developer/hand_sdk).

### Should I use the portal's40/2 gains? <a href="#should-i-use-the-portals402-gains" id="should-i-use-the-portals402-gains"></a>

The same R1 article explicitly says torque-only for Dex2/5. That contradiction requires manufacturer clarification for the installed firmware. A generic gain recommendation is not a valid exception to the model-specific control restriction. Preserve the conflicting source statements when requesting support.

### Does torque feedback equal fingertip force? <a href="#does-torque-feedback-equal-fingertip-force" id="does-torque-feedback-equal-fingertip-force"></a>

No verified tendon geometry/calibration or channel-to-force mapping is supplied here. The product's15 N headlines are physical capability claims, not a conversion for `tau_est`. Do not turn raw torque estimates, current or a copied position into a measured Newton value. The four-finger strength is a combined total, not per-finger sensing.

### Why did an offline pass not enable hardware? <a href="#why-did-an-offline-pass-not-enable-hardware" id="why-did-an-offline-pass-not-enable-hardware"></a>

The program checks synthetic data ownership and labels. It supplies no wiring, bus protocol, firmware qualification, stop behavior or load-release evidence. A missing-entry, nonfinite value or wrong-host error means the offline assumptions failed; investigate the data source rather than filling absent fields with zeros in a real capture.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                                                                          | Reviewed scope / limitation                                                          |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| [Dex2/5 manufacturer product](https://www.unitree.com/Dex2-5)                                                                                                                                                                                                                                                                     | Full functional, mechanical, electrical and conditioned-load table read              |
| [R1 Dex1-1/Dex2/5 article](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands)                                                                                                                                                                                                            | Full index table, internal configuration and conflicting torque/gain statements read |
| [G1 hand service](https://support.unitree.com/home/en/G1_developer/hand_sdk) · [G1+ duplicate](https://support.unitree.com/home/en/G1pl_developer/hand_sdk)                                                                                                                                                                       | Blending, signs, message layout, example and notes read; no transferred R1 ordering  |
| [R1 installation article](https://support.unitree.com/home/en/R1_developer/Dex2-5%20%20Installation)                                                                                                                                                                                                                              | Embed listing read; video not watched, not an installation procedure here            |
| [Pinned G1 example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/high_level/g1_hand_sdk_example.cpp) · [R1 example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/r1/low_level/r1_A5_wrist_swing_example.cpp) | Static code inspected only; active/whole-body routines not run                       |
| [GO state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/MotorStates_.hpp) · [HG motor state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/MotorState_.hpp)                       | Schema declarations, not proof of populated fields or hand calibration               |
| Exact connector/pinout, torque/firmware and stop documents                                                                                                                                                                                                                                                                        | Not verified; obtain before powered work                                             |

No verified standalone RS485 command-frame specification, model-specific public URDF, calibration package or complete service manual was found in these read sources. The nearby Dex1 service and other hand downloads are not substitutes. Source and media rights remain with their owners.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed24 November2026 using actual saved manufacturer/portal text and pinned SDK declarations. All relevant sections of the read product, R1 and G1 hand-service articles are covered, including the control contradiction and missing electrical data. The two R1-A joint-control search hits concern other host/control scopes and were not promoted into Dex2/5 compatibility evidence.

Only the original offline extractor and synthetic wrong-host, missing-index, nonfinite, wrong-type and ownership checks were executed. No vendor code/import, SDK installation/build, ROS/DDS, network/USB/hardware, motion, calibration, reboot or flashing was performed. Exact firmware bounds, harness/standalone frames and independent stop behavior remain unresolved; hardware readiness stays **draft**.

**Related documentation:** [Unitree model and development directory](./).
