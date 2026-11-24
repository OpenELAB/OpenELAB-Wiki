---
description: >-
  Document As2-W X and EDU wheel hardware, 648 Wh battery, app and remote
  ownership, rear connections, and an offline state checkpoint while exact wheel
  SDK compatibility remains open.
---

# Unitree As2-W X and EDU: Wheel Robot and State Development Guide

{% hint style="info" %}
**Unitree As2-W manufacturer reference.** No verified OpenELAB product listing, SKU or product URL was found in the audited catalog. This page is reference-only and makes no store match or SKU ownership claim.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree As2-W is a wheel-leg robot with 16 motors, approximately 25 kg mass with battery, and 178 mm diameter wheels. The V1.1 manufacturer comparison identifies **X and EDU** editions, both marked secondary development Supported. It does not list As2-W AIR or PRO; stray references to AIR in reused explanatory text do not establish such editions. [User Manual V1.1](https://marketing.unitree.com/article/en/As2-W/User_Manual.html), [As2-W comparison](https://www.unitree.com/As2-W).

This manufacturer reference has no verified OpenELAB As2-W listing, SKU or product URL. EDU compute expansion and charging-dock support must be matched to the delivered option. The As2-named SDK2 example remains evidence for a family sport-state interface, not confirmation of As2-W wheel-state fields, wheel indexing, low-level control, simulator support or an exact firmware pairing. The offline checkpoint below deliberately requires none of those unresolved contracts.

## Applications <a href="#applications" id="applications"></a>

As2-W can support supervised perception studies, payload integration and inspection-route development within its documented load, environment and terrain limits. Wheel travel adds tire wear, rolling clearance and wheel/leg mode transitions to the integration problem. A leg-only kinematic model cannot represent its four wheel actuators. Autonomous navigation and following require a separate application design, sensor calibration, localization and an operator-controlled environment. Camera/LiDAR presence alone does not prove a navigation stack or safety certification. [User Manual, overview and precautions](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

Begin development with inventory and offline state handling, then an edition- and firmware-approved subscriber. Mapping, learning, simulation, low-level motor control, charging-dock automation and field deployment are later projects. No matching BSP (board support package), wheel/leg firmware matrix, simulator configuration or deployed learning policy has been verified for the delivered As2-W. Do not fill those gaps using Go2 settings or family names.

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter                                 | As2-W X / EDU manufacturer specification                                                                                  |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| Standing / folded dimensions, L × W × H   | 721 × 493 × 521 / 768 × 602 × 211 mm                                                                                      |
| Motors / mass with battery                | 16 / approximately 25 kg                                                                                                  |
| Tires                                     | 7 inch, 178 mm diameter, 50 mm width                                                                                      |
| Maximum joint torque                      | Approximately 95 N·m; not a continuous wheel torque specification                                                         |
| Continuous walking / static standing load | Approximately 16 / 150 kg; standing load is not an in-motion or passenger rating                                          |
| Travel                                    | 0–3.7 m/s; limit-condition maximum approximately 6 m/s                                                                    |
| Terrain                                   | Approximately 45° slope; 30 cm stair rating; separate maximum-climb claim 0.4–0.8 m                                       |
| Battery / charger                         | One 15 Ah, 648 Wh, 43.2 V nominal pack; 50.4 V, 7.4 A charger                                                             |
| Endurance in V1.1 manual                  | Unloaded \~3 h / 33 km; 16 kg load \~2 h / 27 km                                                                          |
| Compute / perception                      | 8-core CPU; industrial 64–128-line LiDAR, HD camera; EDU optional compute expansion up to 150 TOPS in feature description |
| Interfaces                                | Gigabit Ethernet, SBUS, BAT output; Wi-Fi 6 and Bluetooth 5.2                                                             |
| Environment                               | IP54; robot table −20 to 55 °C; separate battery limits below                                                             |
| Edition differences                       | X/EDU both support development; EDU marks charging-dock and higher-compute expansion options                              |

The range website gives roughly 30 km unloaded and 25 km loaded, while the manual gives 33/27 km. Preserve the source and conditions rather than combining them into a guaranteed range. The manual figure identifies 50 mm as tire **width**; website wording calls it a radius. The dimensions here follow the visually checked manual table. An 80 cm climb headline is not a regular stair height: the comparison and precautions use 30 cm stairs. [Manual V1.1, comparison and precautions](https://marketing.unitree.com/article/en/As2-W/User_Manual.html), [manufacturer comparison](https://www.unitree.com/As2-W).

GPS/4G entries are mainland-China versions only, disabled by default and dependent on authorization. IP54 covers the stated dust/splash conditions, not immersion or arbitrary waterlogged crossings. Optional EDU compute and charging equipment require a delivered-part match.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### As2-W battery and rear connections <a href="#as2-w-battery-and-rear-connections" id="as2-w-battery-and-rear-connections"></a>

The robot supply range is 36–50.4 V; its battery is 43.2 V nominal, with 50.4 V charging output. The X/EDU table specifies one 15 Ah / 648 Wh pack and a 50.4 V, 7.4 A charger. The battery book describes both standard and long-range pack families; that does not change the exact delivered edition's specified pack. Pack dimensions are approximately 144.4 × 201.6 × 87.6 mm. A2's 58.8 V charger is a different electrical target and must not be substituted. [User Manual, comparison](https://marketing.unitree.com/article/en/As2-W/User_Manual.html), [battery/charger ratings](https://marketing.unitree.com/article/en/As2-W/Battery_Charger.html).

The rear-port figure identifies XT30PW-F **BAT output, 36–50.4 V / 5 A**, GH1.25-2P **SBUS / GND**, and an RJ45 **1000BASE-T** interface. SBUS does not supply power; top-to-bottom SBUS/GND applies to the pictured viewing orientation. BAT is unregulated battery voltage, not a 5 V logic supply. Confirm mating view and delivered harness before touching conductors; the drawing does not establish SBUS logic voltage or a complete external device power budget. [Original rear-port figure](https://doc-cdn.unitree.com/static/2026/11/12/9d8dae4be9294cd2a38b528f5b4f1bcb_2482x3509.png).

The As2-W rear-port figure must be matched to the delivered X/EDU chassis, not borrowed from a legged As2 photograph. Ethernet permits a user Ubuntu PC connection according to the manual, but no exact interface address, subnet, credentials, firmware-specific DDS profile or BSP version is established by this chapter. Leave those settings unconfigured until the model-specific deployment record is supplied. [User Manual, Interface Description](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

### Charging, storage and the pre-power inspection <a href="#charging-storage-and-the-pre-power-inspection" id="charging-storage-and-the-pre-power-inspection"></a>

Use the matched charger on a clear, hard surface with ventilation and supervision. The manuals call for the pack off and removed from the robot for cable charging, AC connected before the pack, and a hot pack allowed to cool to room temperature. Prefer the manual's 5–40 °C charging environment; the BMS 0–50 °C protection window is not a recommended charging setpoint. The BMS provides cell balancing, overcharge/overdischarge and short-circuit protection, charging-temperature/current checks, pack load detection and fault indication. Load detection can prevent a removed pack from switching on and can switch it off after removal; that is not a hot-swap qualification. Protection/precharge behavior is internal to the matched charger/pack system, not a user recovery procedure. The 1 Hz charging indication and all indicators off at completion apply to the documented charging state, not every possible off/fault state. Check the model-specific LED matrix before diagnosing a fault. [Charging chapter](https://marketing.unitree.com/article/en/As2-W/User_Manual.html), [battery protections, indicators and precautions](https://marketing.unitree.com/article/en/As2-W/Battery_Charger.html).

Battery guidance recommends storage around 20–25 °C and periodic charge checks; for prolonged storage, below 30% recharge to about 70% as specified. The battery book's recommended discharge environment of −5 to 55 °C is narrower than the robot table's −20 °C lower bound. Confirm the assembled system's battery/temperature approval rather than promising full performance at the robot's headline minimum. Swelling, leakage, damaged shells, wet contacts or abnormal heat require removal from service and manufacturer support, not a BMS bypass or a recovery-charging experiment. Dock/contact-charger descriptions are not permission to connect an unverified dock. [Battery manual](https://marketing.unitree.com/article/en/As2-W/Battery_Charger.html).

Before any later authorized operation, inspect tires, wheel fasteners and leg assemblies, camera/LiDAR windows, fan intake/exhaust, dry battery contacts and positive latch engagement. Check remote charge, centered sticks and non-sticking buttons. Unpack and repack using this model's leg-folding figures and designated case recesses. Keep hands away from hip/knee pinch points and use the designated lifting locations and handling personnel. The placement figure shows belly supports level on a flat surface with folded lower legs and tires supported, with no limb trapped beneath the chassis. It is a preparation requirement, not permission to power the robot during the offline exercise. [Preparation and packing chapters](https://marketing.unitree.com/article/en/As2-W/User_Manual.html), [placement figure](https://doc-cdn.unitree.com/static/2026/11/12/95643b73010841599984571091a1ccba_2482x3508.png).

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### What the pinned SDK2 source actually supports <a href="#what-the-pinned-sdk2-source-actually-supports" id="what-the-pinned-sdk2-source-actually-supports"></a>

At C++ SDK2 commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`, `example/as2/sport/as2_sport_state.cpp` includes `unitree/idl/go2/SportModeState_.hpp` and subscribes as `unitree_go::msg::dds_::SportModeState_`. Its topic is **`rt/lf/sportmodestate`**, channel factory domain is **0**, the network interface comes from `argv[1]`, and `InitChannel(callback, 1)` registers the callback. The `go2` include directory and GO namespace are actual source names; they do not mean that Go2 IP addresses, editions or motion APIs apply to As2-W. [Pinned As2 state example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/as2/sport/as2_sport_state.cpp), [channel subscriber](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_subscriber.hpp).

This example is named As2, not As2-W. No exact As2-W wheel firmware/IDL support statement has been verified. Use it as a family reference only; live wheel subscriptions remain conditional on manufacturer confirmation. The As2 AIR/PRO restriction still applies even though an As2 directory exists.

The GO `SportModeState_` contract contains `stamp`, `position[3]`, `velocity[3]`, `mode`, `progress`, IMU, gait and foot/path fields. `stamp` is a `TimeSpec_` containing signed 32-bit `sec` and unsigned 32-bit `nanosec`; `mode` is uint8. The read sources do not establish the timestamp epoch, synchronization, frame convention, nominal publishing rate, wheel indices or semantics for all firmware releases. Keep source timestamps separate from a local monotonic receipt clock; do not compute wall-clock latency by assuming an epoch. Display mode numerically: the upstream example indexes a fixed name array without an explicit bounds check. An unfamiliar numeric mode must not crash a reader or be relabeled as an assured control state. [GO state contract](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/SportModeState_.hpp), [time contract](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/TimeSpec_.hpp).

### Toolchain and release boundaries <a href="#toolchain-and-release-boundaries" id="toolchain-and-release-boundaries"></a>

The reviewed SDK2 README reports Ubuntu 20.04 LTS, GCC 9.4 and x86\_64/aarch64 support; the root project is version 2.0.0 and selects C++17. The README asks for CMake ≥3.10, while modern `cmake -S/-B` recipes also require a sufficiently recent CMake; the shared setup guide explains this distinction. Python SDK2 commit `814556d15970dd2ecf1c9984e845ca02ab07e206` declares package 1.0.1, Python ≥3.8, `cyclonedds==0.10.2`, `numpy` and `opencv-python`. Its generated GO binding describes the same field family; this is not evidence of a wheel-specific Python application or installation on a particular As2-W. [C++ README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), [root CMake](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/CMakeLists.txt), [Python setup](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py), [Python GO binding](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_go/msg/dds_/_SportModeState_.py).

Use the [SDK2 state development guide](unitree-sdk2-state-development.md) for pinned C++/Python preparation and the separate [ROS2 guide](unitree-ros2-integration.md) for ROS setup. Those guides do not resolve missing As2-W firmware compatibility. Legacy `unitree_legged_sdk`, a generic GO low-level schema, an arbitrary MuJoCo model, and a learning deployment repository must not be selected solely because their organization is Unitree. The source audit has no exact As2-W BSP/release pair or wheel/leg simulator-to-hardware validation record. Retain the robot image, SDK commit and binary architecture together in the project record.

### Ownership: observation, RPC and low-level commands <a href="#ownership-observation-rpc-and-low-level-commands" id="ownership-observation-rpc-and-low-level-commands"></a>

A channel subscriber observes data; an RPC client invokes services, and a command publisher can drive actuators. A factory domain or an API version is not a firmware release number. The model manuals explicitly distinguish high-level and low-level development: in high-level mode remote and API commands can both be processed; in low-level mode remote commands are disabled. Assign one command owner across app, R3, companion follow, voice actions, autonomous services and development processes. A successful subscriber does not obtain ownership, stop another controller or make the area motion-free. [User Manual, developer-mode discussion](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

Do not add motion-switcher `ReleaseMode`, stand, move, damping, wheel commands or a low-level writer to a state check. Release/ownership operations change controller state and need a separate model/firmware-specific procedure. Demonstration binaries may actuate immediately after startup or enter indefinite loops; review each source before eventual supervised commissioning. The state example itself loops forever and its sleep/unused `dt` member does not document a publishing rate. Low-level remote disablement means an R3 button cannot be assumed to remain an effective stop path in custom control. [Pinned state example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/as2/sport/as2_sport_state.cpp), [manual control modes](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

SDK2 root code is BSD-3-Clause; third-party middleware/binaries retain their own notices. Keep the pinned license and dependency notices when redistributing SDK-derived code. Manufacturer manuals retain their copyright; link the originals rather than republishing whole OCR transcripts. The checkpoint here is an original standard-library exercise, with no vendor code copied into its implementation. [SDK2 license](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/LICENSE).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: offline sport-state metadata <a href="#first-result-offline-sport-state-metadata" id="first-result-offline-sport-state-metadata"></a>

Prerequisites: an ordinary computer with Python 3.8 or later and this complete code. No robot, battery connection, SDK package, network interface, DDS discovery or ROS installation is required. The synthetic dictionary resembles selected GO sport-state fields; it is **not** a DDS decoder or a As2-W firmware test. For this wheel model, the family source does not yet justify a live adapter.

1. Record the intended model/edition and unresolved image/BSP in your project notes. Leave the robot powered down and disconnected for this exercise.
2. Save the following complete original code as `offline_state.py`. It copies timestamp/vectors into a frozen snapshot and accepts unfamiliar modes as numbers.
3. Run `python3 offline_state.py` locally. No installation command is needed.
4. Compare the two output lines below. A single message, repeated timestamp or stale local receipt must remain a waiting condition. The two-second freshness limit is an example application policy, not a Unitree timing guarantee.

```python
"""Original offline metadata exercise. No SDK, network, device or robot access."""
from dataclasses import dataclass
from math import isfinite

@dataclass(frozen=True)
class Snapshot:
    stamp: tuple
    position: tuple
    velocity: tuple
    mode: int
    received: float

def capture(message, received):
    sec, ns = message['stamp']
    if type(sec) is not int or type(ns) is not int:
        raise ValueError('integer timestamp fields required')
    if not -(2**31) <= sec < 2**31 or not 0 <= ns < 1_000_000_000:
        raise ValueError('timestamp out of range')
    vectors = [tuple(float(x) for x in message[k])
               for k in ('position', 'velocity')]
    if any(len(v) != 3 or not all(isfinite(x) for x in v) for v in vectors):
        raise ValueError('finite three-element vectors required')
    mode = message['mode']
    if type(mode) is not int or not 0 <= mode <= 255:
        raise ValueError('uint8 mode required')
    if not isfinite(received):
        raise ValueError('finite local receipt time required')
    return Snapshot((sec, ns), *vectors, mode, float(received))

def assess(samples, now):
    if len(samples) < 2:
        return 'WAIT: two messages required'
    first, last = samples[0], samples[-1]
    if not isfinite(now) or not 0 <= now - last.received <= 2.0:
        return 'WAIT: latest local receipt is stale'
    if last.received <= first.received or last.stamp <= first.stamp:
        return 'WAIT: timestamp must advance'
    return 'OFFLINE PASS: advancing stamp and fresh copied metadata'

if __name__ == '__main__':
    message = dict(stamp=[12, 100], position=[0, 0, 0],
                   velocity=[0, 0, 0], mode=255)
    first = capture(message, 10.0)
    message['stamp'][1] = 200
    last = capture(message, 10.1)
    print(assess([first, last], 10.2))
    print('mode=%d position=%s' % (last.mode, last.position))
```

**Expected result:**

```
OFFLINE PASS: advancing stamp and fresh copied metadata
mode=255 position=(0.0, 0.0, 0.0)
```

This pass demonstrates copied metadata, a timestamp transition and a fresh synthetic local receipt. It says nothing about physical motion, robot health, coordinates, sensor accuracy, network transport or command ownership. The program does not interpret mode 255 as a known state. If no transition is observed, keep the diagnostic in WAIT rather than calling one received message a working stream.

### Gate before a later read-only network session <a href="#gate-before-a-later-read-only-network-session" id="gate-before-a-later-read-only-network-session"></a>

Have the model/edition, installed image, approved network interface/subnet, DDS type/topic/domain and current controller owner documented. Use an already commissioned robot under its authorized operator, with the approved stop/recovery path established for its actual mode. Starting the robot can cause it to stand automatically, so powering up is not a passive network preparation step. Do not guess addresses or run a service-changing RPC just to make a subscription visible. [User Manual, startup and development modes](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

For an approved implementation, copy fields inside the callback into immutable data, record local monotonic receipt time, and bound the observation period. Require at least two samples with an advancing source stamp and a currently fresh local receipt; distinguish a clock reset/backwards jump from a good stream. Preserve raw numeric mode and model/firmware identifiers in the capture. A missing stream warrants interface/domain/type/firmware checks, not a motion command. The original offline tests cover silent, single-message, stationary, advancing and stale cases; no live subscription was executed.

### Remote, companion and operating lifecycle <a href="#remote-companion-and-operating-lifecycle" id="remote-companion-and-operating-lifecycle"></a>

The As2-W R3 manual covers the two sticks, posture/movement controls, gait/mode selection, function settings, pairing, charging and the dedicated emergency button. Its 5 V / 700 mA charging specification and 780 mAh battery are different from the companion handset's 5 V / 600 mA and 520 mAh. The R3 book recommends a 5 V / 2 A USB source; the companion book recommends 5 V / 1 A. About five hours runtime and quoted radio distance are manufacturer estimates under conditions, not a guaranteed control radius. [R3 manual](https://marketing.unitree.com/article/en/As2-W/Remote_Control.html), [companion manual](https://marketing.unitree.com/article/en/As2-W/Companion_Remote_Control.html).

The R3 dedicated emergency-stop indication is separate from ordinary data/Bluetooth indicators: flashing means no connection and steady indicates a connected link; red indicates the triggered button state and green the released remote state. The button has a three-second lockout after a press. The manual says the robot must restart after an emergency stop; releasing the remote button alone is not a robot recovery procedure. The L2+B damping combination is a different control path and is not proof of a certified independent stop. Establish effectiveness for the actual firmware/control mode before any later motion session; it is not tested here. [R3 emergency-stop chapter](https://marketing.unitree.com/article/en/As2-W/Remote_Control.html).

Pairing instructions in the R3 manual use the app's Device Data / Remote Control page, the handset ID and SELECT held for more than three seconds. Interface labels may vary by app/firmware. The vibration/sound setting uses an F1 triple-press; the manual describes holding F1 during shutdown to retain the changed feedback mode. Center-stick calibration uses F1/F3 with F3 saving in the documented R3 procedure; do not use it as a generic robot joint-calibration command. Wheel-model stunt mappings differ from legged handsets; do not copy flip, side-gait or wheel-mode button combinations from another model. The exact diagrams and action table remain available in the model-specific R3 original. [Pairing, calibration and key-function chapters](https://marketing.unitree.com/article/en/As2-W/Remote_Control.html).

Companion following is an active controller, not a passive tracking tag. The manuals describe right-waist placement with the user directly to the robot’s left and facing the same direction. The joystick side faces right toward the robot; the antenna stays vertically upright and must not be gripped. The handset should be approximately 0.2–0.5 m ABOVE the robot’s head/base station; this is a relative height difference, not height above the ground. The preferred straight-line distance to the robot’s head is about 0.8 m, within the documented 2.4 m companion range. Avoid confined spaces, metal obstruction, stairs/slopes and abrupt walking; the described walking speed is no more than 2 m/s. M enters following, while P double-press can change prone/stand state; it is not an emergency stop. Handset power cycling can resume following according to the documented behavior. Stop follow through the approved mode-exit path before changing controller ownership. The companion original provides the complete button, orientation, mode-exit and troubleshooting figures. [User Manual, operating chapter](https://marketing.unitree.com/article/en/As2-W/User_Manual.html), [companion controls and precautions](https://marketing.unitree.com/article/en/As2-W/Companion_Remote_Control.html).

The user manual's preparation, startup, operation, shutdown and case-packing chapters form a lifecycle. Startup is active and may automatically raise the body. For normal shutdown the documented posture sequence precedes battery power-off; cutting power while standing can make the chassis fall. A remote failure or fallen robot requires the manufacturer's trained handling/recovery procedure, not reaching into a live joint or repeating power commands. This guide does not turn the manual's emergency lifting/forced-shutdown description into a general unattended recipe. [Operation, abnormal conditions and packing](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

### App, indications, regional features and maintenance <a href="#app-indications-regional-features-and-maintenance" id="app-indications-regional-features-and-maintenance"></a>

The user guide calls the app Unitree Go, while the R3 introduction calls its pairing app Unitree Explore. Obtain the application through the manufacturer's model download page and confirm the installed firmware/app combination rather than assuming those labels mean identical screens. The user guide's onboarding flow is Bluetooth discovery nearby, Add Robot, select the robot, choose direct AP or Wi-Fi/router connection, complete the required activation/tutorial, then enter GO controls. A phone using router mode must be on the intended network. App connectivity and activation do not establish SDK access. [User Manual, app activation](https://marketing.unitree.com/article/en/As2-W/User_Manual.html), [R3 introduction](https://marketing.unitree.com/article/en/As2-W/Remote_Control.html), [official download page](https://www.unitree.com/app/As2).

The app chapters cover remote binding, companion mode, motion/settings, voice interaction, unbinding and clearing device data. App unbinding changes account access; Clear Device Data erases data and is not a first-line connection diagnostic. Voice/action features can initiate movement, so include them in the single-owner plan. Manufacturer-marked mainland-China GPS/4G and default-disabled functions require the stated authorization and regional configuration; camera or voice availability is not a promise of cloud-service availability everywhere. [User Manual, app operation and feature comparison](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

The sensor appendix separates WLAN/WebRTC signaling, BLE network provisioning, remote radio control and UWB companion positioning. Its HTTP signaling service is not a verified camera-stream API or a point-cloud topic, and a listed LiDAR does not identify its deployed driver/calibration. Match the actual sensor and image before sensor integration. [Interface/Sensors appendix](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

The robot's indication table distinguishes blue startup breathing, cyan ready/avoidance indication, green voice wake, purple following, slow yellow low battery and red fault indication. Record steady/flashing pattern and context rather than diagnosing from color alone: the FAQ uses a flashing-red alarm description in a different context. An indication does not prove obstacles will always be detected or that movement is disabled. [User Manual, status indications and FAQ](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

Startup text uses a hold over three seconds and about two minutes, but FAQ timing uses two seconds/about one minute. The maintenance chapter's periodic calibration language also conflicts with the FAQ's advice that normal use needs no joint calibration. Keep these conflicts attached to the revision: use the delivered firmware's approved instructions and manufacturer support, rather than inventing one universal timing or weekly calibration requirement. Do not calibrate motors merely to fix an app connection or missing stream. [Startup, maintenance and FAQ chapters](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### No state messages, or only one old message <a href="#no-state-messages-or-only-one-old-message" id="no-state-messages-or-only-one-old-message"></a>

First confirm the exact edition permits development and that the installed image exports the expected interface. Then check the approved physical adapter/link, the actual user-PC interface, domain and exact type/topic. A2/As2 examples use `rt/lf/sportmodestate`, not an inferred low-state topic. One message does not prove continuous publishing. Keep source stamp progression and local receipt age separate; no current data means no PASS. Do not use `ReleaseMode`, move or stand as connection tests. The unresolved wheel binding is a real stop condition, not a reason to try a Go2 publisher. [State example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/as2/sport/as2_sport_state.cpp), [type](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/SportModeState_.hpp).

### The model does not stand, falls, or reports abnormal posture <a href="#the-model-does-not-stand-falls-or-reports-abnormal-posture" id="the-model-does-not-stand-falls-or-reports-abnormal-posture"></a>

Stop commissioning. Have the operator make the system safe according to the delivered manual, then inspect the startup surface, folded-leg placement, latch/contact condition, surrounding clearance and reported errors. A wrong initial posture can corrupt startup angle interpretation. Persistent failure goes to Unitree support with serial, image and error evidence. Do not lift a powered robot by a joint, manually force a motor, disable a fall-protection service or start a generic calibration routine. [User Manual, pre-start checks and abnormal conditions](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

### Remote pairing fails or sticks do not center <a href="#remote-pairing-fails-or-sticks-do-not-center" id="remote-pairing-fails-or-sticks-do-not-center"></a>

Check handset charge, robot/remote identity, correct app/network and the model-specific pairing page before changing settings. Confirm whether the link indicator is steady or flashing and whether a dedicated stop is triggered. Inspect centered sticks for obstruction; use the R3's documented handset calibration only if appropriate. If the problem occurs in a low-level development mode, remember that the manual says ordinary remote commands are disabled. Restart and rebind only under an operator-approved non-motion procedure; retain logs if it persists. [R3 pairing/calibration](https://marketing.unitree.com/article/en/As2-W/Remote_Control.html), [manual development-mode distinction](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

### Following is unstable or a voice/action request surprises the operator <a href="#following-is-unstable-or-a-voiceaction-request-surprises-the-operator" id="following-is-unstable-or-a-voiceaction-request-surprises-the-operator"></a>

Exit the active mode through its approved path and restore one command owner. Check compatible edition, handset binding, joystick side facing right toward the robot, antenna vertically upright, handset height approximately 0.2–0.5 m above the robot’s head/base station (not above ground), obstruction, battery and distance; do not try to repair following by walking faster or into narrow metal-sided areas. A handset double-press or power cycle can initiate posture/follow behavior. Disable competing action sources in the project design before a later live subscriber session. [Companion/operation chapters](https://marketing.unitree.com/article/en/As2-W/User_Manual.html), [companion manual](https://marketing.unitree.com/article/en/As2-W/Companion_Remote_Control.html).

### Low battery, charging failure or unusual indicator pattern <a href="#low-battery-charging-failure-or-unusual-indicator-pattern" id="low-battery-charging-failure-or-unusual-indicator-pattern"></a>

Read the actual pack/charger nameplates first: As2-family 43.2 V nominal / 50.4 V charger. Check cool/dry condition, approved charger input, pack-off charging state and the correct LED matrix. Battery protection thresholds describe BMS behavior, not permission to set custom recovery voltages. The wheel battery book calls for stopping below 25%; keep a return reserve before that threshold.

If the pack is damaged, wet, swollen, smells abnormal or becomes unusually hot, discontinue use and contact the manufacturer. Do not open it, bridge terminals, bypass the BMS or charge a suspect pack to clear an alarm. [Battery precautions and alarm matrix](https://marketing.unitree.com/article/en/As2-W/Battery_Charger.html), [user charging/FAQ chapters](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

### Range is shorter or motors/fans are hotter than expected <a href="#range-is-shorter-or-motorsfans-are-hotter-than-expected" id="range-is-shorter-or-motorsfans-are-hotter-than-expected"></a>

Compare load, terrain, speed, stance height, turning and ambient conditions with the manufacturer's estimate. Low body stance, bent joints, uneven ground and payload raise power demand. Inspect cooling inlets, fan sound and tire condition, wheel fasteners and rolling obstruction with power off. Reduce the task demand under the operator's plan and escalate persistent abnormal heat/noise rather than modifying thermal limits. As2-W website and manual ranges differ; retain the specific source and log your measured reserve. [Precautions and inspection/maintenance](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

### Cleaning, long storage and transport <a href="#cleaning-long-storage-and-transport" id="cleaning-long-storage-and-transport"></a>

Switch off before wiping with a soft cloth. Follow the model's cleaning sequence, keep electrical interfaces dry and avoid abrasive tools. An IP label is not a pressure-washing or immersion instruction. The manuals retain the battery during whole-body cleaning but call for removal during prolonged storage; those are different states, not permission to unplug a wet live pack. For storage, keep the robot dry/cool and check pack charge periodically. Repack using the exact model's folded-leg drawing and fixed accessory recesses, with no loose charger/remote. [Cleaning, storage and packing](https://marketing.unitree.com/article/en/As2-W/User_Manual.html), [battery storage](https://marketing.unitree.com/article/en/As2-W/Battery_Charger.html).

### Firmware, calibration, camera/LiDAR or a replacement part is uncertain <a href="#firmware-calibration-cameralidar-or-a-replacement-part-is-uncertain" id="firmware-calibration-cameralidar-or-a-replacement-part-is-uncertain"></a>

Record the delivered image, app, sensor serial/model and observed error before contacting support. Confirm the correct exact-model firmware and recovery procedure before any OTA/update; this guide provides no flashing command or verified BSP download. Sensor quantity and WebRTC service descriptions do not establish a point-cloud or video API. Damaged consumables, unusual fan noise, persistent startup errors or calibration uncertainty need the model-specific service channel. The manuals also retain jurisdiction-specific radio/exposure notices and terms; their presence is not a blanket certification for every market or modified payload. Use the originals for those notices. [User Manual, sensor appendix, maintenance, legal/radio notices and revision history](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                       | Exact scope / revision                                                                        | Official original                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| -------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| As2-W User Manual                                              | 1.1 2026-11-10                                                                                | [Open original](https://marketing.unitree.com/article/en/As2-W/User_Manual.html)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| As2-W Battery and Charger Manual                               | 1.0 2026-07-28                                                                                | [Open original](https://marketing.unitree.com/article/en/As2-W/Battery_Charger.html)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| As2-W R3 Remote Control Manual                                 | 1.0 2026-07-28                                                                                | [Open original](https://marketing.unitree.com/article/en/As2-W/Remote_Control.html)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| As2-W Companion Remote Control Manual                          | 1.0 2026-07-28                                                                                | [Open original](https://marketing.unitree.com/article/en/As2-W/Companion_Remote_Control.html)                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| As2-W manufacturer range and comparison                        | Public page snapshot 2026-11-24                                                               | [Open original](https://www.unitree.com/As2-W)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| As2 official app/manual download page                          | Observed public download navigation; apps/videos not executed or watched                      | [Open original](https://www.unitree.com/app/As2)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Interface / placement figures                                  | Exact model, visually checked source pages; connector numbering conflicts remain where stated | [Interface](https://doc-cdn.unitree.com/static/2026/11/12/9d8dae4be9294cd2a38b528f5b4f1bcb_2482x3509.png) · [Placement](https://doc-cdn.unitree.com/static/2026/11/12/95643b73010841599984571091a1ccba_2482x3508.png)                                                                                                                                                                                                                                                                                                                                                       |
| SDK2 source and state contract                                 | Pinned C++ commit; source evidence only                                                       | [State example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/as2/sport/as2_sport_state.cpp) · [GO IDL](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/SportModeState_.hpp) · [TimeSpec](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/TimeSpec_.hpp)                                                                                                                |
| C++ / Python package sources                                   | Pinned toolchain/dependency declarations, no install/build performed                          | [C++ README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md) · [CMake](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/CMakeLists.txt) · [Python requirements](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py) · [Python GO binding](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_go/msg/dds_/_SportModeState_.py) |
| SDK license                                                    | Root BSD-3-Clause; separate third-party obligations                                           | [License](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/LICENSE)                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| CAD, full electrical schematic and cavity-level harness pinout | No exact revision-controlled resource verified for this guide                                 | Unresolved; request model/serial-specific package from Unitree                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Firmware/BSP and wheel/leg compatibility releases              | No exact delivered-image/SDK pairing or approved flashing package verified                    | Unresolved; no guessed download or flashing procedure                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |

The official download pages also list tutorial videos, app packages, calibration and OTA topics. Their listing was read; video contents, executable packages and any linked firmware were not reviewed or run here. The complete model-specific manuals above remain the authoritative originals for every chapter, action table, LED matrix and jurisdiction-specific notice.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026 against the manufacturer As2-W user/battery/remote originals and comparison page, with pinned SDK source contracts. The model-specific source set comprises 4 manuals / 64 source image pages; full text was read, including family-manual comparisons, and critical specification/interface/startup figures were visually checked. The full supplied corpus contains 41 English manuals / 692 pages; this guide does not claim semantic review of unrelated models.

The only executed result is the original offline Python metadata exercise and synthetic checks. Vendor SDK installation, import, build and execution, DDS/ROS, hardware, motion and flashing were **not run**. Source review does not prove firmware or hardware readiness. Exact delivered firmware/BSP, network configuration, electrical harness details and effective control handover remain unresolved. Exact wheel firmware and actuator mapping also remain unresolved.

Normal-browser access to the support portal is now reported available by the parent research task; prior direct HTTP requests returned 567. This guide cites only the manufacturer originals and pinned files actually read for this model. It makes no claim to have read all portal articles or all linked videos/resources. Public explanations are original English interpretation; manufacturer images/manuals and SDK dependencies retain their respective rights.

* **As2-W User Manual** — V1.1, 2026-11-10. [Primary source](https://marketing.unitree.com/article/en/As2-W/User_Manual.html).
* **As2-W Battery and Charger Manual** — V1.0, 2026-07-28. [Primary source](https://marketing.unitree.com/article/en/As2-W/Battery_Charger.html).
* **As2-W R3 Remote Control Manual** — V1.0, 2026-07-28. [Primary source](https://marketing.unitree.com/article/en/As2-W/Remote_Control.html).
* **As2-W Companion Remote Control Manual** — V1.0, 2026-07-28. [Primary source](https://marketing.unitree.com/article/en/As2-W/Companion_Remote_Control.html).
* **As2-W manufacturer range and comparison** — Public page snapshot 2026-11-24. [Primary source](https://www.unitree.com/As2-W).
* **As2 official app/manual download page** — Observed public download navigation; apps/videos not executed or watched. [Primary source](https://www.unitree.com/app/As2).
* **As2 sport state example** — b7fec6020eb93d4c059a6edf19905e12a75a8d3d. [Primary source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/as2/sport/as2_sport_state.cpp).
* **Channel subscriber contract** — b7fec6020eb93d4c059a6edf19905e12a75a8d3d. [Primary source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_subscriber.hpp).
* **GO SportModeState C++ contract** — b7fec6020eb93d4c059a6edf19905e12a75a8d3d. [Primary source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/SportModeState_.hpp).
* **GO TimeSpec C++ contract** — b7fec6020eb93d4c059a6edf19905e12a75a8d3d. [Primary source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/TimeSpec_.hpp).
* **C++ SDK2 README** — b7fec6020eb93d4c059a6edf19905e12a75a8d3d. [Primary source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md).
* **C++ SDK2 project/toolchain declaration** — b7fec6020eb93d4c059a6edf19905e12a75a8d3d. [Primary source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/CMakeLists.txt).
* **Python SDK2 package requirements** — 814556d15970dd2ecf1c9984e845ca02ab07e206. [Primary source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py).
* **Python GO sport state binding** — 814556d15970dd2ecf1c9984e845ca02ab07e206. [Primary source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/idl/unitree_go/msg/dds_/_SportModeState_.py).
* **SDK2 BSD-3-Clause root license** — b7fec6020eb93d4c059a6edf19905e12a75a8d3d. [Primary source](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/LICENSE).

**Related documentation:** [Unitree model and development directory](./).
