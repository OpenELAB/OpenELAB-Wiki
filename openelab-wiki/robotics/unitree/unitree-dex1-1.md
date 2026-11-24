---
description: >-
  Compare three Dex1-1 bundles, verify power and RS485 wiring, inspect pinned
  service behavior and reach a safe offline one-motor state result.
---

# Unitree Dex1-1: power, RS485 bridge and offline state inspection

{% hint style="info" %}
[**View Unitree Dex1-1 gripper options on OpenELAB**](https://openelab.io/products/unitree-dex1-1-robotic-gripper)

**Model:** Dex1-1 · **Standard:** `Unitree-Dex1-1S` · **Advanced:** `Unitree-Dex1-1A` · **Ultimate:** `Unitree-Dex1-1U`. The audited options are Standard, Advanced and Ultimate. Identify the delivered camera, bracket, adapter and harness separately; an option name is not a host-robot firmware qualification.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree Dex1-1 is a parallel two-finger gripper driven by one M4010 motor. It offers a 90 mm opening stroke and motor position, velocity, torque, stiffness and damping control. Its standalone connection is high-speed RS485 with separate DC power through a combined connector; a USB adapter and a serial-to-DDS service connect it to a development computer. A DDS motor angle is not a jaw opening in millimetres. This guide identifies the electrical and software contracts and reaches an original offline state-inspection result. [Product specifications](https://www.unitree.com/Dex1-1), [hardware article](https://support.unitree.com/home/en/dex1-1_gripper/about_dex1_1), [pinned service](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/README.md).

The store's Standard option includes the gripper, D405 mounting bracket, RS485-to-USB board and cables/accessories; Advanced adds RGB camera hardware and its mount; Ultimate includes both RGB and D405 depth cameras with dedicated mounts. A D405 bracket alone is not a depth camera. The manufacturer's standard/advanced presentation and the store's three bundles describe different packaging scopes. Camera firmware, USB bandwidth, driver, optical calibration and hand-eye transform need their own delivered-part records. The advertised RGB specification is 1080p at 30/60 FPS, with H/V/D fields of view 118°/87°/140°; no image-stream API was verified here. [Manufacturer options](https://www.unitree.com/Dex1-1), [exact store options](https://openelab.io/products/unitree-dex1-1-robotic-gripper).

## Applications <a href="#applications" id="applications"></a>

Dex1-1 can support supervised object sorting, grasp-data collection and robot manipulation studies. Select jaw contact material, approach direction, opening clearance and object retention according to the actual object. A payload that fits mechanically can still slip, crush, rotate or fall when motor power is removed. Neither a grip-force headline nor a motor torque estimate certifies safe human contact, medical use or overhead lifting. [Load definitions and conditions](https://www.unitree.com/Dex1-1).

Treat the host arm, gripper and vision system as separate controllers and calibration frames. The manufacturer lists standalone, G1, H2 and R1 applications, but the harnesses and software routes differ. A host installation video or product compatibility illustration does not establish a universal mounting adapter, stop path or firmware pair. Keep the robot and gripper powered down for the first exercise below. [Product compatibility](https://www.unitree.com/Dex1-1), [R1 hand interface](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands), [H2 installation](https://support.unitree.com/home/en/H2_developer/DexterousHand%20_Assembly).

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter                         | Exact scope and conditions                                                                                                                         |
| --------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mass / nominal envelope           | 550 g / 143 × 78 × 67 mm; 78 mm width is the half-open state                                                                                       |
| Full motion envelope              | Product note gives 120 mm fully open and 124.5 mm fully closed with side rails extended; allow external rail clearance                             |
| Stroke / finger length            | 90 / 80 mm                                                                                                                                         |
| Grip force / fingertip resolution | Adjustable 5–120 N / 0.1 mm; force is a manufacturer capability, not calibrated feedback from `tau_est`                                            |
| Speed / shortest closure          | Product table 50–375 mm/s / 0.24 s; values are measured under different 24–60 V control conditions                                                 |
| Load by contact                   | Form-fitting: up to 20 kg horizontal retention; friction: 5 kg vertical retention using a square steel block; not interchangeable working payloads |
| External supply                   | 24–64 V DC; manufacturer recommends 24/48 V DC                                                                                                     |
| Current                           | 0.03 A standby; product calls 3.5 A peak line current, portal calls it peak phase current; input-supply budget remains to be confirmed             |
| Motor                             | 5 N·m peak, 1:25 reduction, 15-bit absolute encoder; up to 27 rad/s at 64 V                                                                        |
| Bus / advertised control rate     | High-speed RS485, 6 Mbps / 1000 Hz; bitrate is not a measured DDS callback rate                                                                    |
| Recommended environment           | −20 to 60 °C; no verified complete-gripper IP rating or wet-operation procedure                                                                    |

The portal introduction says 150 mm/s maximum, its detailed table says 20–375 mm/s, and the product table says 50–375 mm/s. Preserve this conflict rather than setting a universal speed limit from the largest number. The service's nominal loop also differs from the 1000 Hz headline. Confirm the delivered motor, power/current specification, firmware and intended duty before selecting a supply or motion profile. [Product table and notes](https://www.unitree.com/Dex1-1), [portal introduction and detailed tables](https://support.unitree.com/home/en/dex1-1_gripper/about_dex1_1), [service loop](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/main.cpp).

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Combined power and RS485 connector <a href="#combined-power-and-rs485-connector" id="combined-power-and-rs485-connector"></a>

The portal identifies **XT30PW(2+2)-M**, male, combining DC power and RS485. In the **pictured connector orientation**, the two small RS485 contacts are A above B; the large power contacts are negative on the left and positive on the right. This is the manufacturer's drawing view, not a separately verified wire-side mating view. Confirm the mating connector, keying, continuity and harness revision with power isolated; do not mirror the drawing or use wire color as a pin assignment. [Electrical interface drawing](https://oss-global-cdn.unitree.com/static/969f4b95129346e185de4e8a8b1bc4f9_719x434.jpg).

![Dex1-1 original combined power and RS485 connector definition; orientation is the drawing view](https://oss-global-cdn.unitree.com/static/969f4b95129346e185de4e8a8b1bc4f9_719x434.jpg)

The connection diagram separates the computer's USB link to the RS485 adapter from the 24–64 V external supply feeding the hand-side cable. USB is not the gripper motor supply. The 6 Mbps differential RS485 pair is not TTL UART, USB D+/D− or CAN. Termination, bus topology, isolation, cable shield and grounding requirements were not established by this drawing. Use the matched adapter and cable rather than a generic serial board selected by connector appearance. [Original connection diagram](https://oss-global-cdn.unitree.com/static/b6858b52e64b425daf96614009fa601b_1196x424.jpg).

### Mount, travel and host-specific harnesses <a href="#mount-travel-and-host-specific-harnesses" id="mount-travel-and-host-specific-harnesses"></a>

The mechanical drawing shows four M3 mounting holes and an approximately 50 mm circular rear feature, but it supplies no verified bolt torque or permissible insertion length. Use the original drawing/CAD and the actual adapter stack to resolve those details. Keep both moving side rails, fingers and camera cable clear through the full envelope; adding a camera changes clearance and load on the mount. [Mechanical drawing](https://oss-global-cdn.unitree.com/static/8300718d3f38474fb2e557e11f5372e1_4400x3400.png), [CAD and URDF resources](https://support.unitree.com/home/en/dex1-1_gripper/about_dex1_1).

An **H2-specific** advanced gripper kit uses the H2 hand interface board's 24 V plus RS485 connection to PC2. That board/harness is distinct from the standalone XT30PW assembly. H2's direct battery output can reach 75.6 V, above Dex1-1's stated 64 V maximum; do not substitute that battery port for the hand's approved 24 V kit connection. Internal R1 wiring is another installation with app-selected peripheral type. These host examples establish scoped routes, not permission to splice cables or power an unverified unit. [H2 wiring and port table](https://support.unitree.com/home/en/H2_developer/DexterousHand%20_Assembly), [R1 interface](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands).

Before a later live session, document the supply rating/current limit, polarity, grounding and cable revision; mount securely with supported objects removed; isolate hand and arm motion sources; and establish what stops each controller and what happens to a held object on loss of power or communication. No independent certified stop or fail-safe retention performance was verified.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Standalone serial-to-DDS service <a href="#standalone-serial-to-dds-service" id="standalone-serial-to-dds-service"></a>

The audited `dex1_1_service` commit is **`ced3216290bb22dae356213993786beeaa7143ab`**, with version **1.0.1** in `include/param.h`. It selects C++17/CMake ≥3.10 and links Unitree SDK2, DDS libraries, Boost program\_options, yaml-cpp, fmt, pthread and the architecture-specific Unitree motor library. The README describes Linux/Ubuntu development and supplies Ubuntu 22.04 libserialport packages for arm64 and amd64; this is source evidence, not a verified installed image. Its BSD-3-Clause root license does not replace notices for bundled binaries or camera/CAD assets. [Pinned README](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/README.md), [CMake](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/CMakeLists.txt), [parameters](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/include/param.h), [license](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/LICENSE).

The service scans `/dev/ttyUSB*`, `/dev/ttyCH343USB*` and `/dev/ttyACM*`, probing motor IDs 0 and 1. ID **0 is right**, ID **1 is left**. Its factory domain is **0**, and the interface defaults to `eth0` via the `--network` option. Device paths and interface names are observed runtime choices, not stable identities. The portal's older calibration log capitalizes `Right`/`Left`; the pinned implementation and README use lowercase topics. [Portal tutorial](https://support.unitree.com/home/en/dex1-1_gripper/dex1_1), [actual main](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/main.cpp).

| Route                                       | Exact pinned type / layout                                                                                                                    |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| `rt/dex1/right/cmd`, `rt/dex1/left/cmd`     | GO `unitree_go::msg::dds_::MotorCmds_`, `cmds` sequence of one motor per hand                                                                 |
| `rt/dex1/right/state`, `rt/dex1/left/state` | GO `MotorStates_`, `states` sequence of one motor per hand                                                                                    |
| Published state fields                      | Main loop fills `q`, `dq`, `tau_est`; do not interpret default temperature/error fields as measured healthy values                            |
| Coordinate scaling                          | Outgoing motor q/dq multiply by reduction ratio, torque divides by it, kp/kd divide by its square; returned q/dq divide and torque multiplies |

The return is a joint-output angle/velocity/torque estimate. No calibrated jaw-width or fingertip-force conversion is supplied by the service. The pinned repository's URDF uses two prismatic joints with limits −0.02 to 0.0245 m; the portal's 30 October 2026 URDF archive uses differently named prismatic joints with 0–0.041 m limits. Both are model descriptions, and neither makes service radians equal prismatic metres. Retain the URDF revision and derive/validate the actual linkage and frame transform before using either in a planner. [Service conversions](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/main.cpp), [repository URDF](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/urdf/dex1_1.urdf), [updated URDF archive](https://oss-global-cdn.unitree.com/static/d7c835f0bba5402ea9c035d0ee49e76c.zip).

### Serial frames are a separate contract <a href="#serial-frames-are-a-separate-contract" id="serial-frames-are-a-separate-contract"></a>

The pinned motor header declares packed `ControlData_hg` (20 bytes) and `MotorData_hg` (26 bytes). The control declaration contains a two-byte header, a packed four-bit motor ID / three-bit status / one-bit timeout, one reserved byte, int16 torque and speed, int32 position, uint16 position/velocity gains and CRC32. Feedback contains the header/mode bits, housing and winding temperatures, voltage, int16 torque/speed, int32 position, uint32 error, four extension bytes and CRC32. The header comments identify feedback header bytes FC/EE and CRC32-MPEG2 excluding the header. These are serial motor-layer fields, not a DDS memory dump. [Packed declarations](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/include/unitreeMotor/include/motor_msg_HG.h).

Several comments use different fixed-point descriptions for outgoing and returned quantities, and the M4010 torque comment has a model-specific scale exception. The conversion implementation is supplied through a motor library; the declarations alone do not establish its byte order, CRC implementation or verified end-to-end scaling. No raw-frame encoder, calibration packet or guessed checksum recipe is provided here. Use the matched library and exact motor revision in a separately qualified deployment; do not send a hand-built frame to infer the missing contract. [Motor API boundary](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/include/unitreeMotor/unitreeMotor.h), [bridge conversions](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/main.cpp).

### Startup, timeout and demonstration hazards <a href="#startup-timeout-and-demonstration-hazards" id="startup-timeout-and-demonstration-hazards"></a>

Starting the server is **active**: motor detection sends serial FOC requests before serving DDS. It is not a subscriber-only device enumeration. The main motor loop uses a nominal 2000 μs recurrent interval, approximately 500 Hz before communication delays, rather than proving the product's 1000 Hz headline. On command timeout, the source selects motor BRAKE, zeroes its command fields and sets a timeout bit. The subscription wrapper's threshold is 1000 ms; no safety-rated stopping time or holding force follows from that code. On fresh commands it selects FOC and clears the timeout bit. Incoming DDS `mode` is not used as the motor-mode selector by this loop. [Main source](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/main.cpp), [subscription timeout](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/include/dds/Subscription.h).

`test/test_gripper.cpp` creates command publishers and sends a recurring position trajectory with nonzero gains. It does not merely print state. The Python `test_gripper_sub.py` is subscriber-only but imports an additional `logging_mp` module; it is not the self-contained first exercise below. Calibration changes the motor reference and involves manual finger positioning; the portal says it is normally needed once for the absolute encoder. Autostart changes boot behavior and the supplied script defaults to the service interface choice. Do not run calibration, a motion test or autostart to diagnose a missing subscription. [Test source](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/test/test_gripper.cpp), [Python subscriber](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/test/test_gripper_sub.py), [calibration/autostart tutorial](https://support.unitree.com/home/en/dex1-1_gripper/dex1_1).

### Internal host control is a different route <a href="#internal-host-control-is-a-different-route" id="internal-host-control-is-a-different-route"></a>

G1/G1+ internal-hand documentation uses **`rt/hand_sdk`**, GO `MotorCmds_` with **four** entries. Only `cmds[0].mode` encodes weight×100; all five command fields blend with `ai_sport` defaults. Positive torque closes and negative opens under that documented host convention. In damping, commands are not forwarded; after leaving damping, the blend weight must be explicitly set again. If `ai_sport` defaults differ from the external targets, an abrupt weight change from 0 to 1 can cause sudden hand motion. The source's transition warning requires a qualified ownership plan; no executable ramp, gain or timing recipe is provided here. A publishing timeout falls back to `ai_sport` defaults, which guarantees neither a stop nor a hold or load retention. Confirm these behaviors for the documented compatible host/service and delivered firmware. The example alternates torque and is active. Do not apply this weight encoding to the standalone one-motor serial service or assume an undocumented four-slot hand order. [G1 internal interface](https://support.unitree.com/home/en/G1_developer/hand_sdk), [pinned host example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/g1/high_level/g1_hand_sdk_example.cpp).

R1 instead adds Dex1-1 left/right hand motors at HG whole-body indices 31/33; 32/34 are the additional Dex2/5 thumb slots. Its peripheral selection and restart procedure are host-specific. Do not copy G1 topic/type/weight fields into `LowCmd_`. See the [shared SDK2 source guide](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development) for common dependencies and the [ROS2 integration guide](https://wiki.openelab.io/robotics/unitree/unitree-ros2-integration) for the separate middleware path; neither resolves the hand's delivered firmware pairing. [R1 source article](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: original offline one-motor snapshot <a href="#first-result-original-offline-one-motor-snapshot" id="first-result-original-offline-one-motor-snapshot"></a>

Prerequisites: Python 3.8+ on an ordinary computer. Leave the hand/robot powered down and disconnected. The following complete original program copies selected **synthetic** GO state values. It imports no SDK, opens no device and starts no DDS participant. Its receipt times are test values; it does not decode a wire frame or prove live freshness.

1. Record standalone versus internal-host wiring and the intended service/firmware revision.
2. Save this code as `offline_dex1.py`.
3. Run `python3 offline_dex1.py` locally.
4. Compare the expected output and then inspect the waiting/fault conditions described below.

```python
"""Original offline fixture; no SDK, network, device, calibration or motion."""
from dataclasses import dataclass
from math import isfinite

@dataclass(frozen=True)
class Sample:
    values: tuple
    received: float

def capture(states, received):
    if len(states) != 1:
        raise ValueError('Dex1 serial profile needs one motor')
    values = tuple(float(states[0][k]) for k in ('q', 'dq', 'tau_est'))
    if not all(isfinite(v) for v in values) or not isfinite(received):
        raise ValueError('finite state and receipt time required')
    return Sample(values, float(received))

def assess(samples, now):
    if len(samples) < 2:
        return 'WAIT: two local receipts required'
    first, last = samples[0], samples[-1]
    if not isfinite(now) or not 0 <= now-last.received <= 2.0:
        return 'WAIT: latest receipt stale or future'
    if last.received <= first.received:
        return 'WAIT: local receipt must advance'
    return 'OFFLINE PASS: one-motor metadata copied'

if __name__ == '__main__':
    raw = [dict(q=0.25, dq=0.0, tau_est=0.0)]
    a = capture(raw, 10.0)
    b = capture(raw, 10.1)
    raw[0]['q'] = 99.0
    print(assess([a, b], 10.2))
    print('q=%.2f rad; jaw_mm=unverified; hardware_tested=False' % b.values[0])
```

**Expected result:**

```
OFFLINE PASS: one-motor metadata copied
q=0.25 rad; jaw_mm=unverified; hardware_tested=False
```

The unchanged angle is intentional: a stationary gripper can publish multiple samples. This checks advancing **local receipts**, not source timestamps, actual bus health or object retention. Empty/two-motor arrays and nonfinite values are rejected; silence, one message, stale or reversed receipt times stay WAIT. The two-second freshness threshold is an original example policy, not a manufacturer timeout.

### Before any later live observer <a href="#before-any-later-live-observer" id="before-any-later-live-observer"></a>

Resolve supply/current and cable orientation, stop/retention behavior, exact host/service version, lowercase topic/type, one-motor layout, interface and isolated DDS domain. Have the already commissioned service owned by an authorized operator; do not start it just to obtain a passive first result. Copy data in the callback and retain a monotonic receipt time. A generic GO schema or default-valued state is not proof that the serial bridge is reporting temperatures or motor faults.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### No serial ports or no detected motor <a href="#no-serial-ports-or-no-detected-motor" id="no-serial-ports-or-no-detected-motor"></a>

Separate USB enumeration from motor power. Check the matched adapter/cable and isolated supply evidence first, then the actual port identity and permissions on the approved computer. A pinned service supports three port prefixes even though its warning still mentions ttyUSB. Do not scan unknown robot serial devices or rerun FOC probing indiscriminately. Duplicate IDs are skipped by the server; resolve the physical hand/ID assignment through the approved service procedure. [Main detection](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/main.cpp), [tutorial FAQ](https://support.unitree.com/home/en/dex1-1_gripper/dex1_1).

### State topic exists but values look frozen or incomplete <a href="#state-topic-exists-but-values-look-frozen-or-incomplete" id="state-topic-exists-but-values-look-frozen-or-incomplete"></a>

Confirm lowercase topic names, GO `MotorStates_` rather than HG `HandState_`, exactly one motor, and the selected interface. USB Ethernet hubs can change which device is called `eth0`; the README highlights this and the autostart interface issue. Require new local receipts; do not interpret zero unfilled fields as sensor evidence. Do not send motion to test transport. [Pinned README FAQ](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/README.md), [main](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/main.cpp).

### A position command closes too far or differs from the URDF <a href="#a-position-command-closes-too-far-or-differs-from-the-urdf" id="a-position-command-closes-too-far-or-differs-from-the-urdf"></a>

Stop active development and retain the object safely under the operator's plan. Check motor output radians, URDF metres, linkage geometry, absolute reference and the exact description revision. Do not guess a linear conversion from the 90 mm stroke or recalibrate automatically. Contact support with the serial, service commit, URDF hash and recorded state. [Updated URDF](https://oss-global-cdn.unitree.com/static/d7c835f0bba5402ea9c035d0ee49e76c.zip), [service mapping](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/main.cpp).

### The motor stops accepting commands or the host takes over <a href="#the-motor-stops-accepting-commands-or-the-host-takes-over" id="the-motor-stops-accepting-commands-or-the-host-takes-over"></a>

Standalone subscription timeout and G1 `ai_sport` fallback are different mechanisms. One selects a serial motor brake in source; the other restores host defaults. Neither is a guaranteed emergency stop or safe object hold. Record which route was active, message age and controller owner before recovery. Do not bypass timeouts or change calibration to suppress the symptom. [Timeout wrapper](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/include/dds/Subscription.h), [G1 host interface](https://support.unitree.com/home/en/G1_developer/hand_sdk).

### Missing SDK header or camera feed <a href="#missing-sdk-header-or-camera-feed" id="missing-sdk-header-or-camera-feed"></a>

A missing `unitree/idl/go2/MotorCmds_.hpp` points to SDK include/install configuration in the source tutorial, not a gripper firmware fault. Verify the pinned dependency inventory and architecture before a separately authorized build. For cameras, check whether the chosen bundle actually includes that camera, then its driver/calibration independently; the gripper's DDS service does not publish a verified image stream. [Tutorial FAQ](https://support.unitree.com/home/en/dex1-1_gripper/dex1_1), [options](https://www.unitree.com/Dex1-1).

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                                                                                                                                    | Purpose / status                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| [Product table and option description](https://www.unitree.com/Dex1-1)                                                                                                                                                                                                                                                                                                                      | Mechanical/electrical capabilities and test-condition footnotes                                           |
| [Hardware source article](https://support.unitree.com/home/en/dex1-1_gripper/about_dex1_1)                                                                                                                                                                                                                                                                                                  | Appearance, mechanics, connector, cabling, optional cameras and parameter tables                          |
| [Mechanical drawing](https://oss-global-cdn.unitree.com/static/8300718d3f38474fb2e557e11f5372e1_4400x3400.png) · [connector](https://oss-global-cdn.unitree.com/static/969f4b95129346e185de4e8a8b1bc4f9_719x434.jpg) · [connection schematic](https://oss-global-cdn.unitree.com/static/b6858b52e64b425daf96614009fa601b_1196x424.jpg)                                                      | Original figures inspected; use exact viewing orientation                                                 |
| [3D CAD archive](https://oss-global-cdn.unitree.com/static/3dabd1b23711434390071150800bb7a5.zip)                                                                                                                                                                                                                                                                                            | Listed official CAD resource; CAD geometry not independently validated                                    |
| [30 October 2026 URDF archive](https://oss-global-cdn.unitree.com/static/d7c835f0bba5402ea9c035d0ee49e76c.zip)                                                                                                                                                                                                                                                                              | Archive/XML read statically; camera and two prismatic joints; meshes not simulated                        |
| [Pinned service README](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/README.md) · [main](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/main.cpp) · [repository URDF](https://github.com/unitreerobotics/dex1_1_service/blob/ced3216290bb22dae356213993786beeaa7143ab/urdf/dex1_1.urdf) | Service v1.0.1 source contract, not a ready-to-run first check                                            |
| [Portal SDK tutorial](https://support.unitree.com/home/en/dex1-1_gripper/dex1_1)                                                                                                                                                                                                                                                                                                            | Installation, launch, calibration, autostart and connection FAQs; active steps excluded from first result |
| [R1 interface](https://support.unitree.com/home/en/R1_developer/Dex1-1%20and%20Dex2_5%20Dexterous%20Hands) · [G1 internal control](https://support.unitree.com/home/en/G1_developer/hand_sdk) · [H2 assembly](https://support.unitree.com/home/en/H2_developer/DexterousHand%20_Assembly)                                                                                                   | Exact host-specific routes and mechanical/wiring differences                                              |
| Firmware, complete electrical schematic and camera calibration                                                                                                                                                                                                                                                                                                                              | No exact delivered release/qualification package verified; obtain it before active integration            |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026 using the two actual Dex1-1 portal articles, manufacturer product snapshot, exact catalog options, relevant host articles and commit-pinned source. The portal is readable in the supplied source cache; this guide claims only the articles actually reviewed, not all portal contents. Manufacturer figures are attributed originals. CAD/video listings are not claims that their contents were fully reviewed or executed.

The original offline program and synthetic boundary checks were run. Vendor service, SDK, dependency helper, installation/build, DDS/ROS, hardware, calibration, motion, camera streaming and autostart were **not run**. Runtime firmware pairing, electrical current discrepancy, approved harness/stop behavior and jaw/force calibration remain unresolved. This is a bounded engineering reference with hardware readiness **draft**.

**Related documentation:** [Unitree model and development directory](./).
