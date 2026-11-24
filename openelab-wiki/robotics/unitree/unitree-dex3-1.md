---
description: >-
  Map Dex3-1 joints, distinguish legacy and HG state, resolve supply and tactile
  conflicts, and inspect an offline seven-joint snapshot before active
  integration.
---

# Unitree Dex3-1: seven-joint mapping, power and DDS boundaries

{% hint style="info" %}
[**View Unitree G1 Dex3-1 on OpenELAB**](https://openelab.io/products/unitree-g1-dex3-1-force)

**Model:** Dex3-1 · **SKU:** `Unitree-G1-Dex3-1` · **Observed option:** Default Title. Confirm handedness, tactile option, controller revision and host-specific harness on the delivered unit; the listing name does not establish those details.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree Dex3-1 is a three-finger hand with seven controlled joints: three thumb joints and two each for the middle and index fingers. USB connects its hand controller to a resident bridge; DDS exposes HG hand command/state messages above that bridge. A standalone deployment, a G1 service and an H2-specific installation are different environments. This guide explains their source contracts, wiring and diagnostic boundaries and provides a complete original offline checkpoint. [Product table](https://www.unitree.com/Dex3-1), [hardware article](https://support.unitree.com/home/en/dex3-1_hand/about_dex3-1), [communication overview](https://support.unitree.com/home/en/dex3-1_hand/Dex3-1_software_development).

Tactile arrays are optional. The product describes nine groups containing 33 sensing elements, while older G1 text describes six 3×4 fingertip arrays. Identify the actual tactile hardware and bridge release rather than combining those descriptions. A hand with no tactile option can still report motor state. The product's force-control terminology does not make pressure samples or `tau_est` a calibrated contact-force measurement. [Hardware/sensing specification](https://support.unitree.com/home/en/dex3-1_hand/about_dex3-1), [older G1 hand article](https://support.unitree.com/home/en/G1_developer/dexterous_hand).

## Applications <a href="#applications" id="applications"></a>

Dex3-1 supports supervised grasping research, finger-state recording, manipulation and tactile-algorithm work within the actual payload and environment. Three independent fingers permit different contacts from a one-motor parallel gripper; they do not make a five-finger controller applicable. Plan object retention, collision clearance, fingertip compliance and host-arm motion together. The hand's external supply, internal motors and USB communication require separate electrical treatment.

For tactile research, retain raw channels, hand side, sensor-group identity, loss flags, temperature context, zero/reference conditions and calibration revision. Sensor contact geometry and material affect readings. Do not claim Newtons, pressure units, slip detection or safe human interaction from an uncalibrated array. The source's sensing test uses a vertical 1 cm diameter cylinder; its non-damage load is not a grasp payload. [Manufacturer sensing footnote](https://www.unitree.com/Dex3-1).

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter                       | Dex3-1 source value / condition                                                                                         |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Envelope / mass                 | 175 × 88 × 77 mm flat-state envelope / 710 g                                                                            |
| Controlled joints               | Thumb 3, middle 2, index 2; seven in total                                                                              |
| Transmission description        | Six miniature force-controlled joints plus one geared joint; detailed actuator variants have their own reduction ratios |
| Mechanical angle ranges         | Thumb0 −60° to 60°, thumb1 −35° to 60°, thumb2 0–100°; each other finger joint0 0–90°, joint1 0–100°                    |
| Fingertip repeat positioning    | Manufacturer ±2 mm; not a measured calibration result                                                                   |
| External hand supply            | Product website 12–58 V; exact portal hardware table 24–58 V; delivered operating lower bound unresolved                |
| Current                         | 58 V / 0.2 A quiescent; 10 A maximum stated; no duty/aggregate host budget supplied                                     |
| Communication / advertised rate | USB 2.0 / 1000 Hz; source bridge and DDS observation rate must be checked independently                                 |
| Environment                     | −20 to 60 °C; no verified hand ingress-protection rating                                                                |
| Grasp payload                   | At room temperature, 5 cm cylindrical hard object: 500 g with palm down or palm left                                    |
| Peak-power claim                | Website 400 W for 3 s under those load-table conditions, not a continuous operating budget                              |
| Tactile option                  | Nine groups / 33 sensing elements: palm 3×(2×2), pads 3×(2×2), tips 3×(3×1)                                             |
| Sensing headline                | 10–2500 g test loading and 20 kg non-damage statement; neither specifies calibrated force output                        |

The small-joint table separately names F-1515-108 and F-1515-214: approximately 45 g, 34.8 × 23.1 × 23.3 mm, reductions 1:108 and 1:214, ideal torques 0.76/1.498 N·m and speeds 23/11 rad/s. Its actual torque depends on direction relative to speed: 0.49/1.37 N·m for the 108 variant and 0.86/3.1 N·m for the 214 variant. It lists 4.76 A maximum line current, 12–24 V internal actuator supply, absolute rotor encoders and 1000 Hz high-speed Unibus. These are **actuator** parameters, not permission to connect 12 V to an unidentified complete hand or sum all peaks into a supply prescription. [Detailed motor and hand tables](https://support.unitree.com/home/en/dex3-1_hand/about_dex3-1), [website table and notes](https://www.unitree.com/Dex3-1).

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### USB signals and separate motor power <a href="#usb-signals-and-separate-motor-power" id="usb-signals-and-separate-motor-power"></a>

The exact portal drawings separate USB communication from hand power. In the pictured USB lead orientation, top-to-bottom labels are **5 V, D−, D+, GND**. This is not a universal connector cavity numbering or wire-color map. The separate power drawing identifies the positive and negative supply leads; its pictured exposed/insulated ends must not be generalized to another harness. USB 5 V is not the 24–58 V hand supply. Confirm complete-hand rating, polarity, mating view, grounding, fusing and approved current budget before power. The 12 V versus 24 V lower-bound discrepancy keeps an unknown standalone supply choice unresolved. [USB definition](https://doc-cdn.unitree.com/static/2025/1/23/57641b25de744b089fd2e2ae23cd8d45_2016x1034.png), [power definition](https://doc-cdn.unitree.com/static/2025/1/23/62f18a4f412a41e8814156db4b0b1009_2168x1035.png), [hardware article](https://support.unitree.com/home/en/dex3-1_hand/about_dex3-1).

![Dex3-1 manufacturer USB lead labels; this view is not a generic mating pinout](https://doc-cdn.unitree.com/static/2025/1/23/57641b25de744b089fd2e2ae23cd8d45_2016x1034.png)

The portal states 1150 mm communication cable and 90 mm power cable lengths including internal routing. Inspect cable strain relief and wrist travel with the actual host adapter. The mounting drawing shows four M3 depth-4 holes, four Ø4 depth-2.5 features and a separate two-M3 depth-3 pattern; use its orientation and dimensions with the actual wrist stack. No tightening torque or universal screw length was verified. [Mounting drawing](https://doc-cdn.unitree.com/static/2025/1/23/ed23aaa0354a4c7892a992a1b21d60ab_5226x1927.png), [dimensions/connection schematic](https://support.unitree.com/home/en/dex3-1_hand/about_dex3-1).

### G1, R1 and H2 installation scope <a href="#g1-r1-and-h2-installation-scope" id="g1-r1-and-h2-installation-scope"></a>

The older G1 article labels its hand interface RS485/24 V, while the standalone hardware article describes a USB controller. Treat these as host/service/harness scopes requiring revision confirmation, not interchangeable plug definitions. The R1 Dex3 installation article is a video-only resource: its listing was read, but the video was not used as electrical or procedural evidence. [G1 article](https://support.unitree.com/home/en/G1_developer/dexterous_hand), [R1 installation](https://support.unitree.com/home/en/R1_developer/Dex3-1%20Installation).

H2's specific Dex3 and tactile-Dex3 kits use a 24 V hand board/harness and USB to PC1; they are not generic bare-hand USB/power cables. H2 assembly distinguishes side-exit Dex3 wiring from the distal-exit Dex5 installation, requires its dedicated adapter and routes/clamps cables along marked positions. The H2 direct battery port reaches 75.6 V, exceeding Dex3's 58 V maximum; it is not the hand-kit supply. Avoid live mounting or connector changes. [H2 assembly, adapted-kit table and connector drawing](https://support.unitree.com/home/en/H2_developer/DexterousHand%20_Assembly).

Before any future active test, secure the hand, clear fingers and all host joints, remove unsupported objects and assign one command owner. A process called “stop” or a DDS timeout is not a verified independent stop circuit. Loss of grip power may drop an object; define retention and recovery with the actual assembly.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Pinned type and topic audit <a href="#pinned-type-and-topic-audit" id="pinned-type-and-topic-audit"></a>

The reviewed C++ SDK2 is **`b7fec6020eb93d4c059a6edf19905e12a75a8d3d`**, project 2.0.0/C++17. Its README describes an Ubuntu 20.04/GCC 9.4 prebuild environment for x86\_64/aarch64; Python pin **`814556d15970dd2ecf1c9984e845ca02ab07e206`** declares package 1.0.1, Python ≥3.8 and CycloneDDS 0.10.2. Generated Python IDL's 0.11.0 banner is a generator version, not an instruction to change that runtime dependency. Common preparation belongs in the [SDK2 state guide](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development); these pins do not establish a delivered hand firmware/server pairing. SDK root code is BSD-3-Clause; proprietary bridge binaries retain separate notices. [SDK README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), [CMake](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/CMakeLists.txt), [Python requirements](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py), [binding](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_hg/msg/dds_/_HandState_.py).

| Item                     | Read source contract / unresolved difference                                                                                |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------- |
| Command type             | HG `HandCmd_`: dynamic `motor_cmd` vector plus four uint32 reserve words; Dex3 profile uses seven motors                    |
| State type               | HG `HandState_`: motor/tactile vectors, IMU, supply voltage/current, system/device voltages, error\[2], reserve\[2]         |
| Motor command fields     | uint8 mode; float q, dq, tau, kp, kd; uint32 reserve                                                                        |
| Motor state fields       | mode, q, dq, ddq, tau\_est, two int16 temperatures, voltage, sensor\[2], motorstate and reserve\[4]                         |
| Current pressure binding | `pressure[12]` float, `temperature[12]` float, uint32 `lost`, uint32 reserve; optional groups need actual-device validation |
| Portal Dex3 topics       | `rt/dex3/{left\|right}/cmd` and `rt/dex3/{left\|right}/state`                                                               |
| Pinned C++ example       | Domain0, caller-selected NIC; commands use those cmd topics, but selected state topic is `rt/lf/dex3/{left\|right}/state`   |

Current headers are under `include/unitree/idl/hg/`, not the older article's `unitree/hg_idl/` path. The newer IDL explanation sits in the Dex3 space but begins with `rt/dex5/...`; do not copy that namespace to Dex3. The old DDS article mixes a packed low-level integer motor frame with HG DDS structures. Those are different layers. Its old unsigned-short pressure example cannot represent the stated ≥100000 threshold; current float pressure arrays are a different binding. No universal scaling or validity threshold is adopted here. [DDS article](https://support.unitree.com/home/en/dex3-1_hand/DDS-based_communication_method), [IDL explanation](https://support.unitree.com/home/en/dex3-1_hand/Dex_IDL_specification), [pinned HG state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/HandState_.hpp), [pressure header](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/PressSensorState_.hpp), [actual example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/dex3/g1_dex3_example.cpp).

### Motor order and frames <a href="#motor-order-and-frames" id="motor-order-and-frames"></a>

| HG vector index | Joint     | Left G1 URDF name | Right G1 URDF name |
| --------------- | --------- | ----------------- | ------------------ |
| 0               | thumb\_0  | left\_hand\_zero  | right\_hand\_zero  |
| 1               | thumb\_1  | left\_hand\_one   | right\_hand\_one   |
| 2               | thumb\_2  | left\_hand\_two   | right\_hand\_two   |
| 3               | middle\_0 | left\_hand\_five  | right\_hand\_three |
| 4               | middle\_1 | left\_hand\_six   | right\_hand\_four  |
| 5               | index\_0  | left\_hand\_three | right\_hand\_five  |
| 6               | index\_1  | left\_hand\_four  | right\_hand\_six   |

The index order is thumb, **middle**, index despite explanatory prose elsewhere saying thumb/index/middle. Left and right axes/signs differ in the source limits; the mechanical degree ranges are not a universal signed DDS command range. Retain the actual URDF, hand side, axis orientation and firmware conversion. `q`/`dq` are joint-position/velocity fields, and `tau_est` is an estimate, not fingertip force. The service's interpretation of reserved error words must match its version. [Exact ordering tables](https://support.unitree.com/home/en/dex3-1_hand/DDS-based_communication_method), [pinned left/right limit arrays](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/dex3/g1_dex3_example.cpp).

### Bridge deployment and example hazards <a href="#bridge-deployment-and-example-hazards" id="bridge-deployment-and-example-hazards"></a>

The official standalone x86 archive was inspected statically: **Dex3 1.2.6, x86\_64, dated 20 September 2026**. Its configuration separates reduction types 1/2 from sensor types 0/1; shipped `dex_type` is `2.1`, while the portal calls the hardware selector a single model number such as2.0. Do not choose a reduction/sensor combination by trial. Keep the actual hand revision, `dex_type`, `HandConfig.json`, archive hash and SDK pin together. [Deployment article](https://support.unitree.com/home/en/dex3-1_hand/dex3_user_install), [actual package](https://oss-global-cdn.unitree.com/static/b1436d77c71447e5acbb426a343da1d7.zip).

The package requires Ubuntu and architecture-matched binaries; its README advertises Ubuntu20.04 while listing additional ABI requirements and Ubuntu22.04 dependency packages. libusb, fmt, SSL/crypto, udev, libstdc++ and CycloneDDS libraries need actual-host validation. Relative configuration paths require the package directory as working directory; logs are anchored to the binary directory and rotate daily with seven-day retention. USB identities in the source are `34b7:1010` left and `34b7:1011` right. A dependency-helper “pass” would only check files/libraries; it would not qualify wiring, calibration or motion. The helper and all binaries were not run. [Deployment and FAQ chapters](https://support.unitree.com/home/en/dex3-1_hand/dex3_user_install), [package README/config/build information](https://oss-global-cdn.unitree.com/static/b1436d77c71447e5acbb426a343da1d7.zip).

The pinned `g1_dex3_example.cpp` constructs a command publisher and changes INIT directly to ROTATE. Its rotate/grip routines read a RIS timeout member without initializing it; its stop routine still publishes FOC-mode commands with zero gains/torque and does not implement a certified independent stop. The `q` key sets STOP but leaves the outer loop running. The shared state object is also not consistently protected in the callback/read path. Do not use the executable as a safe subscriber, or treat pressing “p” after startup as proof no commands were sent. [Full pinned example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/dex3/g1_dex3_example.cpp).

The portal's packed RIS format allocates four ID bits, three status bits and one timeout bit, while the newer IDL page describes a simple mode0/1. That interpretation is bridge/version-specific. Its grip snippet disables timeout despite a contrary comment; its stop comment disagrees with the assigned status. Obtain a version-matched control contract before sending even an apparent zero/stop command. The standalone test client periodically opens/closes fingers. Autostart, upgrades, calibration and uninstall are active maintenance operations, outside this first-result procedure. Do not enable multicast, launch a bridge or run the test client to diagnose a source mismatch. [DDS examples](https://support.unitree.com/home/en/dex3-1_hand/DDS-based_communication_method), [deployment lifecycle](https://support.unitree.com/home/en/dex3-1_hand/dex3_user_install).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: original offline seven-joint and tactile-shape check <a href="#first-result-original-offline-seven-joint-and-tactile-shape-check" id="first-result-original-offline-seven-joint-and-tactile-shape-check"></a>

Use Python3.8+ on a computer with the hand/robot disconnected and powered down. This fixture is selected metadata, not the complete DDS type or a USB decoder. It validates seven joint positions and optional twelve-channel raw tactile groups without converting them to force.

1. Record the hand side, tactile option and unresolved bridge/firmware profile.
2. Save this code as `offline_dex3.py`.
3. Run `python3 offline_dex3.py`; no SDK installation or network configuration is needed.
4. Verify the exact synthetic output; an incorrect shape, loss flag or nonfinite value must fail.

```python
"""Original offline Dex3 metadata fixture; never publishes or opens hardware."""
from math import isfinite

NAMES = ('thumb_0', 'thumb_1', 'thumb_2', 'middle_0',
         'middle_1', 'index_0', 'index_1')

def copy_state(q, groups, lost):
    angles = tuple(float(x) for x in q)
    if len(angles) != 7 or not all(isfinite(x) for x in angles):
        raise ValueError('seven finite joint positions required')
    tactile = tuple(tuple(float(x) for x in row) for row in groups)
    if len(tactile) != len(lost):
        raise ValueError('one loss flag per tactile group required')
    if any(type(x) is not int or x != 0 for x in lost):
        raise ValueError('tactile loss/unknown flag; inspect raw record')
    if any(len(row) != 12 or not all(isfinite(x) for x in row)
           for row in tactile):
        raise ValueError('finite twelve-channel raw groups required')
    return angles, tactile

if __name__ == '__main__':
    raw_q = [0.0] * 7
    angles, tactile = copy_state(raw_q, [[0.0] * 12], [0])
    raw_q[3] = 99.0
    print('OFFLINE PASS: %d joints; index3=%s; copied_q=%.1f'
          % (len(angles), NAMES[3], angles[3]))
    print('tactile_groups=%d raw-only; force_N=unverified; hardware_tested=False'
          % len(tactile))
```

**Expected result:**

```
OFFLINE PASS: 7 joints; index3=middle_0; copied_q=0.0
tactile_groups=1 raw-only; force_N=unverified; hardware_tested=False
```

One synthetic tactile group illustrates the transport shape; it does not claim one group is a complete real Dex3 array. An empty optional array is allowed, while sensor layout/count, calibration and loss semantics require the actual bridge. Passing this code proves only copied finite data and model-specific shape handling. It does not prove arrival, source freshness, joint health, payload retention or physical force.

### Later read-only capture gate <a href="#later-read-only-capture-gate" id="later-read-only-capture-gate"></a>

Before an approved live observer, resolve exact hardware supply, USB power/data wiring, archive/config/firmware match, actual topic (`rt/...` versus `rt/lf/...`), HG type and hand side. Use an already commissioned bridge under an operator with a verified stop/retention plan. Bound the capture, copy vectors in the callback, track monotonic receipt time, require multiple new receipts and stop interpretation on nonfinite data, loss flags or errors. HG hand messages here provide no source timestamp/tick; repeated positions alone cannot establish or disprove a current stream. Do not run a publisher as a connectivity check.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### USB board missing or LinuxSendMcu initialization fails <a href="#usb-board-missing-or-linuxsendmcu-initialization-fails" id="usb-board-missing-or-linuxsendmcu-initialization-fails"></a>

Check the approved separate supply, actual USB cable/board, architecture and permissions in that order. The source lists left/right USB product IDs, but finding one device does not prove a second hand is installed. Resolve side selection and controller identity before service launch. A host-specific RS485 description does not authorize replacing the USB bridge. [Deployment FAQ](https://support.unitree.com/home/en/dex3-1_hand/dex3_user_install), [hardware](https://support.unitree.com/home/en/dex3-1_hand/about_dex3-1).

### DDS discovery works but no hand state arrives <a href="#dds-discovery-works-but-no-hand-state-arrives" id="dds-discovery-works-but-no-hand-state-arrives"></a>

Check the exact service topic and HG type first, then interface/domain/isolation. The pinned example's `rt/lf/dex3/.../state` differs from the portal's state topic. Do not create several uncontrolled publishers while trying alternatives. A discovered topic, default-initialized vector or one old message is not a verified stream. [Pinned example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/dex3/g1_dex3_example.cpp), [DDS article](https://support.unitree.com/home/en/dex3-1_hand/DDS-based_communication_method).

### Joint ordering, sign or pressure values look wrong <a href="#joint-ordering-sign-or-pressure-values-look-wrong" id="joint-ordering-sign-or-pressure-values-look-wrong"></a>

Check the seven-slot table, hand side and exact URDF before interpreting motion. Separate raw pressure shape from calibrated sensing and verify the installed option. Do not cast the older ≥100000 pressure convention into uint16, divide values into assumed Newtons, or substitute Dex5's grouping. Preserve raw samples and firmware/configuration evidence for support. [IDL explanation](https://support.unitree.com/home/en/dex3-1_hand/Dex_IDL_specification), [ordering](https://support.unitree.com/home/en/dex3-1_hand/DDS-based_communication_method), [hardware](https://support.unitree.com/home/en/dex3-1_hand/about_dex3-1).

### Package starts from one directory but not as a service <a href="#package-starts-from-one-directory-but-not-as-a-service" id="package-starts-from-one-directory-but-not-as-a-service"></a>

The documented program loads HandConfig/dex\_type relative to its working directory; an autostart service must preserve that context. Check existing configuration and log location before changing it. Keep one bridge instance per isolated topic environment; the portal and package describe fixed hand topics. Do not enable an autostart service merely to collect diagnostics, and do not remove shared SDK libraries during cleanup. [Deployment lifecycle and logs](https://support.unitree.com/home/en/dex3-1_hand/dex3_user_install), [package README](https://oss-global-cdn.unitree.com/static/b1436d77c71447e5acbb426a343da1d7.zip).

### Fingers move during a supposed test or stop command <a href="#fingers-move-during-a-supposed-test-or-stop-command" id="fingers-move-during-a-supposed-test-or-stop-command"></a>

Treat that as an active-control event. Follow the actual assembly's stop/retention procedure and isolate command owners. The source example starts ROTATE, the test client cycles fingers, and its software STOP is not a verified hardware stop. Save logs, selected hand/config and command-source identity before recovery; do not raise gains or disable timeout protection. [Example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/dex3/g1_dex3_example.cpp), [DDS snippets](https://support.unitree.com/home/en/dex3-1_hand/DDS-based_communication_method).

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Scope / status                                                                                       |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| [Product specification](https://www.unitree.com/Dex3-1) · [hardware article](https://support.unitree.com/home/en/dex3-1_hand/about_dex3-1)                                                                                                                                                                                                                                                                                                                          | Parameters, mounting, electrical and tactile option; voltage/current and sensor differences retained |
| [Dimensions](https://doc-cdn.unitree.com/static/2025/1/23/21da63f9f9574056b435993b530cbaf8_5707x3084.png) · [mount](https://doc-cdn.unitree.com/static/2025/1/23/ed23aaa0354a4c7892a992a1b21d60ab_5226x1927.png) · [USB](https://doc-cdn.unitree.com/static/2025/1/23/57641b25de744b089fd2e2ae23cd8d45_2016x1034.png) · [power](https://doc-cdn.unitree.com/static/2025/1/23/62f18a4f412a41e8814156db4b0b1009_2168x1035.png)                                        | Original drawings; mount/USB/power figures visually inspected                                        |
| [3D STEP archive](https://oss-global-cdn.unitree.com/static/4934ca571aef4d08bf7081ae63531e91.zip)                                                                                                                                                                                                                                                                                                                                                                   | Listed official CAD; no simulated or manufactured-fit claim                                          |
| [URDF source directory](https://github.com/unitreerobotics/unitree_ros/tree/157ff950351e5f535e03c5d85a16b7d594b3dbcc/robots/dexterous_hand_description)                                                                                                                                                                                                                                                                                                             | Pinned repository reference; description presence does not validate hardware control                 |
| [Software overview](https://support.unitree.com/home/en/dex3-1_hand/Dex3-1_software_development) · [DDS communication](https://support.unitree.com/home/en/dex3-1_hand/DDS-based_communication_method) · [IDL explanation](https://support.unitree.com/home/en/dex3-1_hand/Dex_IDL_specification) · [standalone deployment](https://support.unitree.com/home/en/dex3-1_hand/dex3_user_install)                                                                      | All five dedicated articles read, including lifecycle, examples, FAQs and linked resources           |
| [x86 package1.2.6](https://oss-global-cdn.unitree.com/static/b1436d77c71447e5acbb426a343da1d7.zip) · [arm64 package](https://oss-global-cdn.unitree.com/static/77ac8419baa343a3a27a8287e1e48677.zip)                                                                                                                                                                                                                                                                | x86 archive/config/docs read statically; arm64 link listed, neither executable run                   |
| [Pinned example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/dex3/g1_dex3_example.cpp) · [HG state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/HandState_.hpp) · [pressure type](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/PressSensorState_.hpp) | Source audit; example publishes motion and has the limitations above                                 |
| [G1 hand](https://support.unitree.com/home/en/G1_developer/dexterous_hand) · [H2 assembly](https://support.unitree.com/home/en/H2_developer/DexterousHand%20_Assembly) · [R1 installation video listing](https://support.unitree.com/home/en/R1_developer/Dex3-1%20Installation)                                                                                                                                                                                    | Host-specific applicability; video contents not reviewed                                             |
| Firmware and calibrated tactile transfer function                                                                                                                                                                                                                                                                                                                                                                                                                   | Exact delivered package/units/approved stop behavior unresolved; no flashing recipe                  |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed24 November2026 against the actual cached Dex3 portal sources, manufacturer product page, relevant host sources and pinned SDK files. The x86 deployment archive identifies1.2.6 and was parsed as data; its scripts and binaries were not executed. The detailed source ledger records each article section and linked-resource access state. This is not an all-portal or all-video claim.

The original offline fixture and shape/nonfinite/loss/ownership checks ran successfully. Vendor SDK/server/example/helper, build/install, ROS/DDS, USB/hardware, motion, calibration and flashing were **not run**. Exact firmware, topic/mode differences, external-supply lower bound, sensor layout/force calibration and stop effectiveness keep hardware readiness **draft**.

**Related documentation:** [Unitree model and development directory](./).
