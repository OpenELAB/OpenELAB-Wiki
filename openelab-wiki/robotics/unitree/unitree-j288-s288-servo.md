---
description: >-
  Compare J288 and S288 voltage, gearing and encoder limits, decode synthetic
  single-bus feedback, and assess the documented arm and small-biped examples.
---

# Unitree J288 and S288 Brushless Servos: Wiring and Development Guide

> **Manufacturer reference — no verified OpenELAB SKU.** This page covers the [Unitree Brushless Digital Servo](https://www.unitree.com/DigitalServo) family, specifically **YS-342026-J288** and **YS-342026-S288**. They are distinct motors with different voltage, materials and torque limits, not interchangeable SKU aliases.

## Product overview <a href="#product-overview" id="product-overview"></a>

These compact FOC servos integrate a high-ratio spur reducer and dual absolute encoders. Their interface is **5 V TTL single-wire half-duplex**, not the RS485 A/B bus used by IM6014 and GO-M8010-6. A shared command/reply size with IM6014 does not imply equivalent scales, voltage or adapters. [About J288/S288](https://doc-cdn.unitree.com/36/1596/en/36_1596_en) [Line Connection](https://doc-cdn.unitree.com/36/1578/en/36_1578_en) [Motor Protocol](https://doc-cdn.unitree.com/36/1582/en/36_1582_en)

This guide synthesizes all **18 actual English J288/S288 portal articles**, the manufacturer comparison table and visually inspected connector/mounting figures, as read on 24 November 2026. The reference arm and reinforcement-learning articles were read; their linked archives, training repositories and policies were not executed or independently validated.

## Applications <a href="#applications" id="applications"></a>

The family is intended for small mechanisms and research assemblies where size, reflected gearing and the model-specific stall capability are appropriate. The reference UniArmL1 uses J288 joints in a six-axis arm; the small-biped article discusses a 14-motor topology. Neither article supplies a turnkey validated mechanical platform, training dataset or certified autonomous behavior. [Python Robot Arm Example](https://doc-cdn.unitree.com/36/1595/en/36_1595_en) [Multi-Motor Reinforcement Learning Deployment Example (For Small Bipedal Robots)](https://doc-cdn.unitree.com/36/1622/en/36_1622_en)

Use J288 or S288 according to the actual nameplate and power system. A model field in a configuration file must not silently switch both voltage and observation layout. A small plastic-geared servo is not a replacement for a higher-torque Unitree quadruped joint simply because the host API uses torque, speed and position fields.

## Specifications <a href="#specifications" id="specifications"></a>

| Item                                  | J288 / YS-342026-J288                                        | S288 / YS-342026-S288           |
| ------------------------------------- | ------------------------------------------------------------ | ------------------------------- |
| Supply range                          | 6.4–25.2 V DC                                                | 6.4–12.6 V DC                   |
| Recommended supply                    | 25.2 V                                                       | 12.6 V                          |
| Gears / housing                       | Steel spur gears / aluminum housing                          | Plastic gears / plastic housing |
| Mass                                  | Manufacturer 39 g; portal 35 g; revision conflict unresolved | 19.5 g                          |
| Opposing-rotation stall torque        | 1.5 Nm                                                       | 0.6 Nm                          |
| No-load speed                         | 35 rad/s at 25.2 V; 16.5 at 12 V                             | 16.5 rad/s at 12 V              |
| Maximum line current in product table | 1.92 A                                                       | 0.84 A                          |
| No-load current                       | 0.45 A at 25.2 V; 0.27 A at 12 V                             | 0.27 A at 12 V                  |
| Shared outline                        | 20 × 34 × 26 mm, width × height × depth                      | Same advertised outline         |
| Reduction                             | 288.35:1                                                     | 288.35:1                        |
| Encoders                              | Rotor 15-bit single-turn absolute; output 8192 steps/turn    | Same advertised resolutions     |
| Bus                                   | 5 V TTL single-wire, half-duplex, 6 Mbps, 8N1                | Same physical interface         |
| Addresses                             | 0–14 unicast; 15 broadcast without reply                     | Same addressing                 |

Sources: [manufacturer servo comparison](https://www.unitree.com/DigitalServo) and [About J288/S288](https://doc-cdn.unitree.com/36/1596/en/36_1596_en). The manufacturer also lists torque constant 0.554 Nm/A and minimum temperature −20°C, with driver protection at 90°C and winding protection at 120°C. Those thermal trip figures are not the upper continuous ambient rating. Neither stall torque nor no-load speed is a continuous operating point.

**Do not use the shared Quick Start's 24 V power example on S288.** Its 12.6 V upper operating limit governs. The portal's J288 35 g and product table's 39 g remain separately attributed rather than averaged into a new specification. The generic overview's planetary-reducer language must not override these model-specific spur gear descriptions. [Quick Start](https://doc-cdn.unitree.com/36/1594/en/36_1594_en) [Motor Overview](https://doc-cdn.unitree.com/36/1577/en/36_1577_en)

Power design must accommodate the actual servo count, load, transients, wiring loss and regenerative braking. No-load current is insufficient for sizing. A supply unable to absorb reverse energy can be damaged even if a drive trips. Use a reviewed protected battery or bidirectional supply with the correct model voltage; a model-matched braking-energy strategy is separate from a fuse or timeout.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Single-bus wiring and connector orientation <a href="#single-bus-wiring-and-connector-orientation" id="single-bus-wiring-and-connector-orientation"></a>

The official figure shows two equivalent three-contact ports with **mirrored visible order**: on the left in this view, top-to-bottom is −, +, signal; on the right it is signal, +, −. Read the actual keying and matching harness; this is not a universal mating-plug pin order. The communication signal is 5 V TTL with common ground. Never connect it to RS485 A/B or a 24 V supply. [About J288/S288](https://doc-cdn.unitree.com/36/1596/en/36_1596_en) [Line Connection](https://doc-cdn.unitree.com/36/1578/en/36_1578_en)

![Official J288/S288 connector view showing mirrored visible polarity order](https://doc-cdn.unitree.com/static/2026/9/15/deec5bd6fc214ef1abab95d3b2b67788_1416x919.png)

The documented USB single-bus board connects the PC at A, external power at B and motor cable at C. The signal is a high-speed half-duplex UART bus, not the Dallas/Maxim OneWire timing protocol. Use a compatible single-wire direction-control interface and a model-correct power source. The Quick Start/assistant's generic “485” wording does not change the physical TTL specification. Power off before rewiring; all devices on a shared bus need unique IDs and the same supported rate. [Line Connection](https://doc-cdn.unitree.com/36/1578/en/36_1578_en) [Quick Start](https://doc-cdn.unitree.com/36/1594/en/36_1594_en)

![Official servo single-bus adapter wiring reference](https://doc-cdn.unitree.com/static/2026/10/20/aa745d96cc5e4c7ea3fe599792697e9e_2409x863.png)

The line/protocol articles describe fixed 6 Mbps, while configuration/assistant pages offer 6/4 Mbps options. This is an unresolved revision or documentation conflict: do not assume a delivered servo or adapter supports 4 Mbps or change it based on a copied GUI label.

### Front and rear fixing <a href="#front-and-rear-fixing" id="front-and-rear-fixing"></a>

S288 uses M2 self-tapping screws and J288 M2 machine screws. The mounting article recommends approximately 10 mm screws for the front arrangement; its rear arrangement shows upper 14 mm and lower 10 mm screws, with 3D-printed plate thickness at least 3 mm. These dimensions depend on that illustrated fixture and engagement; do not substitute them for the delivered assembly drawing or force a long screw into the housing. There is no universal tightening torque established here. [Structure Installation](https://doc-cdn.unitree.com/36/1614/en/36_1614_en)

![Official front servo fixing arrangement](https://doc-cdn.unitree.com/static/2026/9/21/5ce6b0b1aff5428390c1d77a16026fba_2422x1451.png)

![Official rear servo fixing arrangement](https://doc-cdn.unitree.com/static/2026/9/21/5f1b09973f6842eaab1c8628b0768992_2422x1451.png)

Select a supported load path and mechanical stops appropriate for the reduction gear. Avoid self-disassembly or using the housing as an improvised clamp. A reflected large numerical rotor range does not permit unlimited output travel through the physical mechanism.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### FOC, hybrid control and coordinates <a href="#foc-hybrid-control-and-coordinates" id="foc-hybrid-control-and-coordinates"></a>

The drive combines feedforward torque with proportional position and velocity feedback:

`tau = tau_ff + kp * (q_des - q) + kd * (dq_des - dq)`.

`kp` has units Nm/rad and `kd` has units Nm/(rad/s). Position control uses nonzero position gain and damping; speed control sets position gain to zero and uses velocity gain; damping sets a zero desired speed with velocity gain; pure torque sets both gains to zero. Zero feedforward and zero gains remove the commanded torque contribution while the drive can remain enabled. That is neither an independent power disconnect nor a guarantee that a gravity-loaded linkage will hold position. Feedforward plus feedback creates hybrid control. These are combinations of fields within FOC, not necessarily distinct packet mode numbers.

A gear ratio `r` relates rotor and ideal output quantities as `q_out=q_rot/r`, `dq_out=dq_rot/r`, and `tau_out≈tau_rot*r`; friction and losses make torque conversion an estimate. Equivalent output position and velocity gains scale by `r²`. Always identify which side an API uses before applying a ratio. A source integer's representable range describes serialization, not a safe mechanical command envelope.

For J288/S288, the ratio is 288.35. The wire fields are rotor-side; example API wrappers can expose output-side commands and perform conversion internally. Check that convention before multiplying again. The output encoder is a distinct 13-bit signal; it is not the same as rotor-position reconstruction. Factory startup behavior, joint zero, sign, gear backlash and mechanical range remain properties of the specific assembly. [Motor Overview](https://doc-cdn.unitree.com/36/1577/en/36_1577_en) [Control Mode](https://doc-cdn.unitree.com/36/1592/en/36_1592_en) [Motor Protocol](https://doc-cdn.unitree.com/36/1582/en/36_1582_en)

The control-mode chapter covers output torque, speed, position and damping, plus tuning gains and combined modes. High position or speed gain increases reaction forces and can excite gearing; feedforward is not a substitute for feedback limits. A zero-gain servo may release a gravity-loaded linkage. No tuning values are provided here as a universal safe operating recipe.

### Protocol: same envelope, different semantics <a href="#protocol-same-envelope-different-semantics" id="protocol-same-envelope-different-semantics"></a>

Commands are 20 bytes starting FE EE; replies are 26 bytes starting FC EE. Byte 2 packs four-bit ID, three-bit mode and timeout option/status. Mode 0 is stop and mode 1 FOC; clear-error and reset are special state-changing transactions. Bytes 4–5, 6–7, 8–11, 12–13 and 14–15 of the command hold torque, speed, position, position gain and velocity gain respectively. [Motor Protocol](https://doc-cdn.unitree.com/36/1582/en/36_1582_en)

| Rotor-side field        | Servo scaling; do not use IM6014 scaling          |
| ----------------------- | ------------------------------------------------- |
| Torque                  | Nm = signed raw / 256000                          |
| Velocity                | rad/s = signed raw / 2.56 × 2π                    |
| Position                | rad = signed raw / 32768 × 2π                     |
| Position gain (`k_pos`) | signed `int16_t`; physical gain = raw / 1280000   |
| Velocity gain (`k_spd`) | signed `int16_t`; physical gain = raw / 128000000 |

The servo command structure declares both `k_pos` and `k_spd` as signed `int16_t`. This does not authorize negative gains: the read servo article establishes no general permission to use negative gain values. Preserve the signed declaration and the servo-specific scales; do not substitute GO packed-header `uint16_t` gain fields or IM6014 scaling. [Motor Protocol](https://doc-cdn.unitree.com/36/1582/en/36_1582_en)

Reply byte 3 is signed driver/case temperature, byte 4 winding temperature, byte 5 voltage ×2; torque, speed and position occupy 6–13. Faults occupy 14–17. Bytes 18–19 pack **output encoder in low 13 bits and warnings in the high 3 bits**. IM6014 reserves those low bits, despite using the same header and frame length. Bytes 20–21 are reserved; CRC is 22–25, little-endian. Host struct alignment padding such as `NoUse[2]` is not part of a 26-byte wire reply. [Motor Protocol](https://doc-cdn.unitree.com/36/1582/en/36_1582_en)

CRC32 is the documented wordwise algorithm: seed FFFFFFFF, polynomial 04C11DB7, little-endian input words processed most-significant bit first. Command checksum covers bytes 0–15; reply checksum covers bytes 2–21. It is not generic reflected `zlib.crc32`. The serialized torque/output range is not the physical 1.5/0.6 Nm stall rating. A valid checksum cannot distinguish IM6014 from a servo; physical model provenance is mandatory.

### Development examples and dependencies <a href="#development-examples-and-dependencies" id="development-examples-and-dependencies"></a>

The portal offers separate STM32, Python and C++ examples, describing a shared parsing/CRC state machine and asynchronous send/receive architecture. The dedicated Python example calls for **Python ≥3.11 and pyserial**. The STM32 example uses **STM32F413RGT6**, recommends hardware floating point and describes **PA9 TX/RX on the single bus plus ground**, not the IM6014 PA10 RX / PA11 DE wiring. These are active control examples. [Example](https://doc-cdn.unitree.com/36/1584/en/36_1584_en) [STM32 Example](https://doc-cdn.unitree.com/36/1585/en/36_1585_en) [Python Example](https://doc-cdn.unitree.com/36/1586/en/36_1586_en)

The dedicated C++ chapter declares **C++17, CMake ≥3.16**, Visual Studio on Windows, and Linux/macOS paths. Its host-communication and controller wrapper are documentation claims; archive implementation, platform binaries and build success were not verified. A build-only reference after acquiring the correct reviewed archive would be `cmake -S <reviewed-source> -B <local-build>` followed by `cmake --build <local-build>`. Do not run an example simply to test the build. The summary's C++ ZIP URL is identical to IM6014's, while the dedicated servo C++ article links a different ZIP. Obtain the correct exact-model package from Unitree rather than treating either link as validated. The older actuator SDK pin in the GO/A1/B1 guide does not name J288/S288. [C++ Example](https://doc-cdn.unitree.com/36/1598/en/36_1598_en) [Data Download](https://doc-cdn.unitree.com/36/1593/en/36_1593_en)

### Assistant, configuration and firmware <a href="#assistant-configuration-and-firmware" id="assistant-configuration-and-firmware"></a>

The assistant provides communication settings, transmit/receive panels, configuration and plotting. Start/control actions transmit; graph checkboxes only select traces. Auto Refresh/Scale and zoom affect visibility, not wire traffic, and receipt-order plots do not provide a synchronized sensor clock. Rotor/output display toggles can convert values. Its baud choices and generic RS485 labels must be checked against the single-bus hardware and actual firmware. The Windows port-latency suggestion above 60 Hz is driver-specific, not a universal tested control rate. [Motor Debugging Assistant](https://doc-cdn.unitree.com/36/1580/en/36_1580_en) [Quick Start](https://doc-cdn.unitree.com/36/1594/en/36_1594_en)

Configuration changes IDs, firmware and the documented baud option. Never share duplicate IDs or mix rates. Firmware transfer is described as 10–20 s; the collected downloads say no firmware update currently. No exact delivered firmware pair or minimum version for all described behaviors is established. A copied power-on/high-precision option in the assistant is insufficient to import IM6014's calibration procedure into these servos. [Motor configuration](https://doc-cdn.unitree.com/36/1591/en/36_1591_en) [Data Download](https://doc-cdn.unitree.com/36/1593/en/36_1593_en)

### UniArmL1 and learning/deployment boundaries <a href="#uniarml1-and-learningdeployment-boundaries" id="uniarml1-and-learningdeployment-boundaries"></a>

The J288 UniArmL1 reference is a six-axis Python arm example with VR, keyboard and master/slave teleoperation, joint/camera data collection and a linked `unitree_lerobot` training path. Those operations move joints and may record images. The article was read; the linked repository, datasets and trained policies were not audited or run. It is not evidence that S288 can replace J288 in the same arm. [Python Robot Arm Example](https://doc-cdn.unitree.com/36/1595/en/36_1595_en)

The small-biped RL article describes **14 servo IDs 0–13**, Linux with Python ≥3.10, 6-Mbps motor communication and an optional **LSM6DSV16X** on I²C bus 1 at 0x6A or 0x6B. Its phases are wiring/check, zero/sign collection, ONNX-contract inspection, then real-robot deployment. No trained policy, complete training setup or mechanical robot model is included. Null calibration templates are not deployable calibration.

The J288 observation uses its output-side information, while the **S288 61-dimensional rotor-only contract** is distinct. Equal input dimensions do not make policies interchangeable. A zero-gain `check_bus` still performs active bus transactions and can drop an unsupported mechanism. Direction calibration moves motors. The S288 HOME transition takes about 12 s before policy execution; the duration argument counts policy time, not HOME. A zero forward-velocity request can still cause HOME and balance motion. Fake upright IMU values are a stand-debug convenience, not sensing for free walking. The source says the reorganized example was offline-tested, not real-robot verified; that is an upstream claim, not OpenELAB testing. Best-effort zero-gain shutdown cannot be delivered over a failed bus, so an independent power-removal design remains necessary. [Multi-Motor Reinforcement Learning Deployment Example (For Small Bipedal Robots)](https://doc-cdn.unitree.com/36/1622/en/36_1622_en)

A later live integration needs the delivered model, drive and hardware revision, firmware identifier, adapter, operating system, serial device, bus rate and ID recorded together. Assign one process exclusive ownership of the serial bus; close the assistant, other terminal tools and any robot controller before a qualified bench session. Each active status poll can transmit a control/state transaction. None of these motors provides a DDS subscriber-only first result. A successful frame CRC is not proof of model identity, firmware compatibility, safe mounting or fresh physical measurement.

For an eventual receive log, preserve immutable frame bytes with model provenance, monotonic receipt time, local frame counter and the exact parser revision. Reject mismatched IDs, length, header, CRC and invalid SDK results. Measure arrival age separately from changes in position: a stationary motor can have valid fresh feedback. On loss or stale feedback, stop the application under a separately engineered stop procedure; closing a port or attempting a final zero command cannot guarantee delivery over a broken link.

## Getting started <a href="#getting-started" id="getting-started"></a>

1. Save the complete original Python block below as a local file.
2. Run that file with an existing Python 3 interpreter; no package installation is needed.
3. Compare the printed OFFLINE PASS result and preserve all unverified metadata flags.

### First result: a synthetic J288 reply <a href="#first-result-a-synthetic-j288-reply" id="first-result-a-synthetic-j288-reply"></a>

This original standard-library Python block creates and parses one synthetic reply. It opens no port, imports no Unitree software and sends no command. Run it with an existing Python 3 interpreter. Expected output: `J288 OFFLINE PASS 26 bytes`, then `rotor_torque=0.001 Nm output_estimate=0.288 Nm`. The synthetic voltage is 12 V and is not a power-supply instruction.

```python
"""Original synthetic feedback exercise. Select one documented model, never autodetect."""
import math
import struct
MODEL = 'J288'  # Explicit source contract; the frame does not identify the model.

def crc_words(data):
    if len(data) % 4:
        raise ValueError('CRC input must contain whole little-endian words')
    value = 0xffffffff
    for offset in range(0, len(data), 4):
        word = int.from_bytes(data[offset:offset+4], 'little')
        for bit in range(31, -1, -1):
            top = value >> 31
            value = (value << 1) & 0xffffffff
            if top ^ ((word >> bit) & 1):
                value ^= 0x04c11db7
    return value

def decode(frame, expected_id=0):
    if MODEL not in ('IM6014', 'J288', 'S288'):
        raise ValueError('Unknown model contract')
    frame = bytes(frame)
    if len(frame) != 26 or frame[:2] != b'\xfc\xee':
        raise ValueError('Expected a 26-byte feedback frame, no host padding')
    if crc_words(frame[2:22]) != int.from_bytes(frame[22:], 'little'):
        raise ValueError('CRC mismatch')
    if (frame[2] & 15) != expected_id or (frame[2] & 15) == 15:
        raise ValueError('Unexpected or broadcast ID')
    ratio, torque_scale, speed_scale = ((38/3, 2560, 64) if MODEL == 'IM6014'
                                       else (288.35, 256000, 2.56))
    torque, speed, position = struct.unpack_from('<hhi', frame, 6)
    status = int.from_bytes(frame[18:20], 'little')
    return dict(model=MODEL, mode=(frame[2] >> 4) & 7,
                timeout=bool(frame[2] & 128), voltage=frame[5] / 2,
                driver_or_case_temp=struct.unpack_from('b', frame, 3)[0],
                winding_temp=frame[4],
                error=int.from_bytes(frame[14:18], 'little'), warning=status >> 13,
                rotor_torque=torque / torque_scale,
                output_torque_estimate=torque / torque_scale * ratio,
                output_position_from_rotor=position / 32768 * math.tau / ratio,
                output_speed_from_rotor=speed / speed_scale * math.tau / ratio,
                output_encoder_raw=(status & 8191) if MODEL != 'IM6014' else None,
                data_origin='synthetic offline frame')

if __name__ == '__main__':
    frame = bytearray(26)
    frame[:2] = b'\xfc\xee'
    frame[3:6] = bytes([25, 30, 24])
    struct.pack_into('<hhi', frame, 6, 256, 0, 0)
    frame[22:] = crc_words(frame[2:22]).to_bytes(4, 'little')
    result = decode(frame)
    print(result['model'], 'OFFLINE PASS', len(frame), 'bytes')
    print('rotor_torque=%.3f Nm output_estimate=%.3f Nm' %
          (result['rotor_torque'], result['output_torque_estimate']))
```

Set model metadata deliberately. The exercise selects J288 and does not discover a motor; selecting S288 changes the allowed model identity for interpretation but never verifies the delivered unit, its voltage or calibration. Output encoder raw counts and rotor-derived position are different measurements; neither synthetic zero proves a physical joint zero. The checksum guards byte integrity, not trust or freshness.

### Later integration gate <a href="#later-integration-gate" id="later-integration-gate"></a>

Before a qualified powered session, confirm J288 versus S288 on the actual part, supply/adapter/wiring, firmware and documented baud, mounting and external load support, joint zero/sign/range, exclusive bus ownership and an independent stop plan. Resolve the archive-link discrepancy before acquiring software. Establish validated stopped-state feedback before introducing gains or an arm/policy application. No vendor example, calibration, HOME trajectory or learning deployment was executed for this guide.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### No reply or wrong readings <a href="#no-reply-or-wrong-readings" id="no-reply-or-wrong-readings"></a>

Check exact model, voltage limit, TTL adapter identity, shared ground, port ownership, configured rate and unique ID. A 485 transceiver or opposite connector's remembered pin order can be wrong even when the connector fits. Broadcast 15 does not reply. Verify the 26-byte reply without host padding, CRC coverage excluding the header, model-specific scales and the correct warning/output-encoder word. Correctly decoded stationary feedback need not have a changing position; distinguish local receipt age from physical motion. [Line Connection](https://doc-cdn.unitree.com/36/1578/en/36_1578_en) [Motor Protocol](https://doc-cdn.unitree.com/36/1582/en/36_1582_en)

If the assistant's generic labels disagree with the electrical specification, stop and obtain a matched revision answer. Do not diagnose S288 by powering it with the shared 24 V demonstration. For a blank graph, check trace selection and Auto Refresh/Scale; doing so does not stop transmission. A Python import or C++ build problem needs the exact archive and environment, not a guessed dependency copied from the older GO SDK.

### Faults, warnings and timeout <a href="#faults-warnings-and-timeout" id="faults-warnings-and-timeout"></a>

| Bit        | Fault meaning                                                        | Clear after cause removed? |
| ---------- | -------------------------------------------------------------------- | -------------------------- |
| 0          | Overcurrent                                                          | Reset/power cycle required |
| 1, 2       | Transient / sustained overvoltage                                    | Clear supported            |
| 3          | Transient undervoltage                                               | Clear supported            |
| 4          | Chip overheating                                                     | Clear supported            |
| 5, 6       | MOS hot/cold / abnormal temperature                                  | Clear supported            |
| 8, 9       | Housing temperature abnormal / winding overheat                      | Clear supported            |
| 10         | Rotor encoder error                                                  | Reset/power cycle required |
| 12         | Output encoder error                                                 | Clear supported            |
| 13         | Stored data error                                                    | Reset/power cycle required |
| 14         | Abnormal reset                                                       | Clear supported            |
| 16, 17     | Chip verification / calibration mode                                 | Reset/power cycle required |
| 19, 20, 22 | Driver version too low / wrong firmware model / hardware overcurrent | Reset/power cycle required |

These are simultaneous bit flags, not a sequential error enum. Warning bit 0 means an abnormal low-voltage supply. “Clear supported” describes the protocol's recovery option after the physical cause is removed, not permission to mask an active fault. Unsupported bits remain unknown. A clear-error transaction uses special mode 6 and prescribed fields; mode 7 resets the drive. Both mutate its state. The source quotes about 0.3 s for reset and 1.3 s for power-up; lack of replies during either interval is expected, not proof of a healthy stop.

Fault evidence is the full mask, voltage, temperatures and actual firmware, not just one selected bit. The source's opt-in communication timeout is about one second and latches; clear-error alone is not recovery. Approved stop/reset transitions are separate state-changing procedures. Remove the physical cause and support the mechanism before manufacturer-directed reset or power cycling. Firmware-model and driver-version faults especially require an exact hardware/software match, not a loop that repeatedly clears them. [Motor Error Table](https://doc-cdn.unitree.com/36/1583/en/36_1583_en) [Motor Protocol](https://doc-cdn.unitree.com/36/1582/en/36_1582_en)

### Arm, biped and policy failures <a href="#arm-biped-and-policy-failures" id="arm-biped-and-policy-failures"></a>

A missing encoder, reversed sign, null offset or mismatched ONNX contract must stop deployment planning. A script accepting a file does not prove that it matches a J288/S288 robot. Keep model metadata, joint mapping, observation order, action scaling and IMU assumptions together. The reference includes no verified policy or complete robot calibration, and no free-walking first result is established. For assistance, provide Unitree or the purchase channel the exact servo model, firmware, de-energized wiring diagram and fault log. [Python Robot Arm Example](https://doc-cdn.unitree.com/36/1595/en/36_1595_en) [Multi-Motor Reinforcement Learning Deployment Example (For Small Bipedal Robots)](https://doc-cdn.unitree.com/36/1622/en/36_1622_en)

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

The actual [servo resource summary](https://doc-cdn.unitree.com/36/1593/en/36_1593_en) lists an assistant, USB driver, STM32 and Python examples, the UniArmL1 Python arm archive, C++ archive, CAD and fixing drawings. The [dedicated C++ chapter](https://doc-cdn.unitree.com/36/1598/en/36_1598_en) gives a **different C++ ZIP**, and the summary's URL duplicates IM6014's. This is a source discrepancy requiring manufacturer confirmation, not a package-selection recommendation.

The [single-bus wiring](https://doc-cdn.unitree.com/36/1578/en/36_1578_en), [protocol](https://doc-cdn.unitree.com/36/1582/en/36_1582_en), [configuration](https://doc-cdn.unitree.com/36/1591/en/36_1591_en), [fault handling](https://doc-cdn.unitree.com/36/1583/en/36_1583_en), [mounting](https://doc-cdn.unitree.com/36/1614/en/36_1614_en), [arm example](https://doc-cdn.unitree.com/36/1595/en/36_1595_en) and [biped RL article](https://doc-cdn.unitree.com/36/1622/en/36_1622_en) were read as primary documentation. Linked binaries, archives, third-party dependencies and policies are listed-only unless explicitly stated otherwise. No software archive's license was established by opening it; the BSD license of an unrelated actuator repository cannot be assigned to these files.

### Direct upstream resource links (listed only) <a href="#direct-upstream-resource-links-listed-only" id="direct-upstream-resource-links-listed-only"></a>

These resource targets are preserved from the read articles. None of the following file contents was opened or executed; a link is not a compatible-package recommendation.

* [Data Download resource](https://oss-global-cdn.unitree.com/static/a14bc99cfd6842b78120150494fa639f.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1593/en/36_1593_en).
* [Quick Start resource](https://oss-global-cdn.unitree.com/static/e26ef991bbb84867aca9fd0cc6ffbbc5.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1594/en/36_1594_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/9716456655734ec796ebe32134e29a3e.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1593/en/36_1593_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/65c673695e054209a8fcfcf5eb8bfd52.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1593/en/36_1593_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/91cb8424a3044e3e8c903bc8b0ea67ae.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1593/en/36_1593_en).
* [C++ Example resource](https://oss-global-cdn.unitree.com/static/05d2ec3b90b2478aa30156b4efce9594.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1598/en/36_1598_en).
* [Multi-Motor Reinforcement Learning Deployment Example (For Small Bipedal Robots) resource](https://oss-global-cdn.unitree.com/static/3ac3e525c7494c659f050eacef3a99e3.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1622/en/36_1622_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/64305def0f584da987f2b529a073ebd1.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1593/en/36_1593_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/71540fcf6406463a88fc001141b04ca8.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1593/en/36_1593_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/b63a3a407f8643f8b49d4d1c325d9d54.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1593/en/36_1593_en).
* [Data Download resource](https://oss-global-cdn.unitree.com/static/bd68bae979024bba9bb1a9add90eac0f.zip) — [listing chapter](https://doc-cdn.unitree.com/36/1593/en/36_1593_en).

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Sources are the [Unitree servo product comparison](https://www.unitree.com/DigitalServo) and all 18 actual cached articles in the [English J288/S288 space](https://support.unitree.com/home/en/J288-S288%20Servo/About_J288-S288); citations above use the actual article CDN responses. The interface, adapter wiring and front/rear mounting figures were visually inspected. This is original English explanation with an original offline exercise. Upstream manuals, photographs and archives retain their owners' rights.

Original synthetic and static document checks are the only validation performed. No Unitree software was installed, built, imported or executed; there was no serial, DDS, ROS, hardware, firmware, teleoperation or policy test. J288 mass, 4/6-Mbps behavior, assistant wording, exact C++ archive and delivered firmware remain explicit gaps. Readiness: **draft for independent review**, with no stock or exact store SKU claimed.

### Read source catalog <a href="#read-source-catalog" id="read-source-catalog"></a>

| Actual read primary chapter                                                                                                           | Treatment on this page                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| [About J288/S288](https://doc-cdn.unitree.com/36/1596/en/36_1596_en)                                                                  | Exact model comparison, torque/speed/power/thermal/mass conflicts and connector figures                                 |
| [Motor Overview](https://doc-cdn.unitree.com/36/1577/en/36_1577_en)                                                                   | Basic integration/FOC/encoders/hybrid; spur-model specificity overrides generic planetary wording                       |
| [Line Connection](https://doc-cdn.unitree.com/36/1578/en/36_1578_en)                                                                  | 5VTTL single bus, grounding, mirrored contacts and adapter path                                                         |
| [Development Guide](https://doc-cdn.unitree.com/36/1581/en/36_1581_en)                                                                | Intro links to quickstart/control/config/protocol/fault; each read separately                                           |
| [Quick Start](https://doc-cdn.unitree.com/36/1594/en/36_1594_en)                                                                      | Driver/GUI/active control introduction, dangerous24Vshared example excludedS288                                         |
| [Control Mode](https://doc-cdn.unitree.com/36/1592/en/36_1592_en)                                                                     | Output torque/speed/position/damping, tuning and side conventions                                                       |
| [Motor configuration](https://doc-cdn.unitree.com/36/1591/en/36_1591_en)                                                              | ID, firmware and 6/4 rate conflict; no invented startup procedure                                                       |
| [Motor Protocol](https://doc-cdn.unitree.com/36/1582/en/36_1582_en)                                                                   | 20/26frames, TTLrate, field/scales, OutPos/ExFlag/padding/CRC/timeout and model provenance                              |
| [Motor Error Table](https://doc-cdn.unitree.com/36/1583/en/36_1583_en)                                                                | Complete bitmask, warning and qualified clear/reset distinction                                                         |
| [Example](https://doc-cdn.unitree.com/36/1584/en/36_1584_en)                                                                          | Threeplatforms/parser-state machine; archive implementation not independently verified                                  |
| [STM32 Example](https://doc-cdn.unitree.com/36/1585/en/36_1585_en)                                                                    | F413 singlebusPA9TX/RX and active example, no inherited RS485 pins                                                      |
| [Python Example](https://doc-cdn.unitree.com/36/1586/en/36_1586_en)                                                                   | Python3.11+pyserial, rotor/output interpretation and active examples                                                    |
| [Python Robot Arm Example](https://doc-cdn.unitree.com/36/1595/en/36_1595_en)                                                         | Six-axisJ288,VR/keyboard/master/slave and joint/camera/lerobotdata path; repo linked-only                               |
| [C++ Example](https://doc-cdn.unitree.com/36/1598/en/36_1598_en)                                                                      | C++17CMake3.16/platform claim and dedicated archive link versus wrong summary                                           |
| [Multi-Motor Reinforcement Learning Deployment Example (For Small Bipedal Robots)](https://doc-cdn.unitree.com/36/1622/en/36_1622_en) | Allphases/deps/mapping/IMU/ONNX/calibration/HOME/observations/stand-only qualification and upstream verification limits |
| [Motor Debugging Assistant](https://doc-cdn.unitree.com/36/1580/en/36_1580_en)                                                        | GUI areas/trace/scale/side conversion/baud/copy labels/latency; active operations qualified                             |
| [Structure Installation](https://doc-cdn.unitree.com/36/1614/en/36_1614_en)                                                           | Model-specific screws and fixture-specific front/rear lengths; visual figures read                                      |
| [Data Download](https://doc-cdn.unitree.com/36/1593/en/36_1593_en)                                                                    | Assistant/driver/STM/Python/arm/C++/CAD/fixing linked resources; conflicting C++archive/no version guarantee            |

**Related documentation:** [Unitree model and development directory](./).
