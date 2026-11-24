---
description: >-
  Integrate Dex5-1 editions using the full 20-to-16 mapping, conditioned load
  and power limits, tactile-count discrepancies and an original offline
  checkpoint.
---

# Unitree Dex5-1 and Dex5-1P: coupled joints, tactile data and power

{% hint style="info" %}
[**View Unitree Dex5-1 and Dex5-1P options on OpenELAB**](https://openelab.io/products/unitree-dex5-1-left-and-dex5-1p-right-tactile-hand-for-unitree-h1-h1-2)

**Models:** Dex5-1 / Dex5-1P · **Observed Left option:** `Unitree-Dex5-1` · **Observed Right option:** `Unitree-Dex5-1P`. Those are the store's observed option labels. The manufacturer distinguishes the P model by tactile sensing; P is not a universal right-hand identifier. Confirm actual handedness, sensing and host kit before purchasing or connecting.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree Dex5-1 is a five-finger hand with **20 described joint degrees of freedom and 16 active motors**. Four fingers each have a coupled distal joint; the thumb has four active joints. Dex5-1P adds tactile sensing in the manufacturer's comparison. The USB hand controller and its resident DDS bridge expose a different contract from Dex3's seven motors, Dex5-S's22 motors or the two-actuator Dex2/5. This guide explains the20-slot versus16-motor mapping and reaches an original offline interpretation result. [Manufacturer comparison](https://www.unitree.com/Dex5-1), [hardware article](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/About%20Dex5-1%20Hand), [DDS control article](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS).

The store's Left/Right labels do not establish that every left hand lacks sensing or every right hand has it. Nor does its H1/H1-2 title prove a complete firmware pairing or mounting kit. The hardware article specifically discusses H1-2, and the H2 assembly source lists distinct H2-specific Dex5-1 and Dex5-1P kits. Retain the hand label, physical side, tactile option, adapter/harness revision, server package and host firmware as separate identity fields. [Hardware scope](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/About%20Dex5-1%20Hand), [H2 kit table](https://support.unitree.com/home/en/H2_developer/DexterousHand%20_Assembly).

## Applications <a href="#applications" id="applications"></a>

Dex5-1 can support supervised multi-contact grasp research, manipulation datasets, finger coordination and optional tactile studies. Its backdrivable/coupled structure requires a consistent kinematic model;20 command positions do not imply20 independently torque-controlled motors. An object held by several contacts can still slip, crush or fall when power or a controller changes. The hand is not qualified here for lifting above people, safety-critical medical work or safe human contact.

For a tactile configuration, preserve raw channels, optional-group presence, loss indicators, hand side and calibration history. Pressure-array values, joint torque estimates, a10 N fingertip capability and a20 kg non-damage sensing statement are different quantities. None permits converting an arbitrary raw channel to Newtons without the appropriate calibration and contact geometry. [Manufacturer sensing conditions](https://www.unitree.com/Dex5-1), [current HG pressure type](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/PressSensorState_.hpp).

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter                                  | Manufacturer value and interpretation                                                                        |
| ------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| Mass / dimensions                          | Approximately1100 g /217.3 ×127.5 ×72.1 mm; shipped geometry may vary                                        |
| Active / described joints                  | 16 active motors,20 described joints; four coupled finger distal joints                                      |
| Active distribution                        | Thumb4; index/middle/ring/pinky3 each                                                                        |
| Transmission                               | 12 miniature force-controlled composite joints plus4 geared joints; not a promise of zero transmission ratio |
| Thumb mechanical ranges                    | J0 −33.5° to39°, J1 0–100°, J2 0–110°, J3 0–92°                                                              |
| Other-finger ranges                        | Lateral −22° to22°, MCP0–90°, PIP0–95°, DIP0–81° coupled with PIP                                            |
| Repeat positioning / minimum grip diameter | ±1 mm /10 mm                                                                                                 |
| Fingertip capability                       | 10 N manufacturer claim; not calibrated torque-to-contact-force feedback                                     |
| Supply / quiescent current                 | 24–60 V DC /58 V at0.2 A                                                                                     |
| Maximum current                            | 58 V at4 A in primary sources; not a continuous rating or current at every supply voltage                    |
| Interface / advertised communication rate  | USB2.0 /1000 Hz; an actual DDS callback rate is not established by that label                                |
| Environment                                | −20 to60 °C; no complete-hand IP rating or wet-operation approval verified                                   |
| Grasp payload                              | Room temperature,5 cm cylindrical hard object:3.5 kg palm down,4.5 kg palm left                              |
| Tactile distinction                        | Dex5-1 `/`; Dex5-1P94 sensing elements in manufacturer comparison                                            |

The store lists1000 g and3 A maximum, while the read manufacturer page and hardware article say1100 g and4 A at58 V. The portal's mechanical row also describes16 while mistakenly saying four joints for every finger; the introduction, coupled-joint description and20-to16 mapping clarify the active/described distinction. Preserve these source differences; do not size a mount or supply from the most convenient value. [Primary specifications](https://www.unitree.com/Dex5-1), [hardware tables](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/About%20Dex5-1%20Hand), [observed store description](https://openelab.io/products/unitree-dex5-1-left-and-dex5-1p-right-tactile-hand-for-unitree-h1-h1-2).

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### USB communication, XT30 power and host kits <a href="#usb-communication-xt30-power-and-host-kits" id="usb-communication-xt30-power-and-host-kits"></a>

The hardware article describes a4+2 lead harness that splits into USB communication and XT30 supply. Its power lead length is1800 mm including internal routing. In the **pictured XT30 side orientation**, upper is **+Power** and lower **−GND**. This is the exact drawing view, not permission to mirror it into a generic mating-side pinout. Confirm the delivered cable keying, polarity, connector orientation, grounding and supply budget while isolated. USB5 V is not the hand's24–60 V motor supply. [Electrical connection chapter](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/About%20Dex5-1%20Hand), [original power drawing](https://doc-cdn.unitree.com/static/2026/4/24/7af77b98ae734283823d9a8056f5f90c_588x211.png).

![Dex5-1 original power connector definition; upper and lower refer to the illustrated view](https://doc-cdn.unitree.com/static/2026/4/24/7af77b98ae734283823d9a8056f5f90c_588x211.png)

Use the original dimensions and mounting-hole drawing with the actual adapter stack; no bolt torque, screw-length selection or cable bend radius was verified. Preserve clearance around all fingers, the lateral swing and the wrist cable outlet. The hand's load table is not the host wrist's allowable payload. [Dimension drawing](https://oss-global-cdn.unitree.com/static/60bc416bca9642e0a3b60e8e34c99508_1555x1081.png), [mounting holes](https://oss-global-cdn.unitree.com/static/b302a7a0190a49c99544c5c5edd7d9ef_1745x1190.png).

The H2 source distinguishes distal-end Dex5 wiring from side-exit Dex3. It describes a dedicated adapter, cable clamping, wrist cover/Mylar replacement and marked routing to the H2 board. Its **H2-specific** Dex5/P kits use24 V plus USB to PC1 through hand connectors13/14. Do not substitute H2's direct54–75.6 V battery port: its upper voltage exceeds this hand's60 V maximum. Exact kit selection and the original front/back board-connector views are required; these are not the standalone XT30 pinout. Installation disassembly is not part of the offline first result. [H2 assembly and board interfaces](https://support.unitree.com/home/en/H2_developer/DexterousHand%20_Assembly).

Before later active work, mount securely, remove unsupported objects, isolate all command owners and establish the effective stop/power-loss/retention behavior. Mechanical backdrivability and software timeout behavior do not establish safe retention or a certified independent stop.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Environment and source versions <a href="#environment-and-source-versions" id="environment-and-source-versions"></a>

The audited common C++ SDK2 pin is **`b7fec6020eb93d4c059a6edf19905e12a75a8d3d`**, project2.0.0/C++17 with an Ubuntu20.04/GCC9.4 x86\_64/aarch64 prebuild statement. Python pin **`814556d15970dd2ecf1c9984e845ca02ab07e206`** declares1.0.1, Python≥3.8 and `cyclonedds==0.10.2`; its generator banner is not a runtime release instruction. These pins define the reviewed message declarations, not a tested Dex5 firmware pair. Use the [common SDK2 guide](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development) for shared preparation. [README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), [CMake](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/CMakeLists.txt), [Python setup](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py).

The dedicated self-deployment article reports vendor testing on Ubuntu18.04/20.04/22.04, recommends20.04 or22.04, and lists x86\_64/ARM64, libusb and Unitree/CycloneDDS libraries. Its package layout includes `dex5_anemone`, `urdf_motion_test`, configuration, logs, CasADi functions and a CasADi3.7.2 library directory. Those are manufacturer package requirements, not tests performed for this guide. The linked AMD64 archive was not fully inspected and no exact executable version/SDK ABI pair was verified. The precheck script, server and reciprocating-motion test were not run. [Self-deployment workflow](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Dex5_SDK).

The SDK's root BSD-3-Clause license is distinct from rights to the proprietary server, CAD and manufacturer images. A downloadable binary is not an open-source implementation or a validated deployment. Keep package hash, architecture, server version, hand revision and firmware together before commissioning.

### HG messages, topics and command interpretation <a href="#hg-messages-topics-and-command-interpretation" id="hg-messages-topics-and-command-interpretation"></a>

The current HG `HandCmd_` has a dynamic motor-command vector plus four uint32 reserve words. `HandState_` has motor/tactile vectors, IMU, power voltage/current, system/device voltages, error\[2] and reserve\[2]. Motor commands contain mode,q,dq,tau,kp,kd; current pressure groups contain12 floats,12 temperature floats, a loss word and reserve. Not every allocated field is meaningful on every bridge. [Pinned command](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/HandCmd_.hpp), [state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/HandState_.hpp), [pressure](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/PressSensorState_.hpp), [IDL explanation](https://support.unitree.com/home/en/dex3-1_hand/Dex_IDL_specification).

The Dex5 article's naming rule says `rt/dex5/{left|right}/state` and `/cmd`, but its subscription example uses **`rt/dex5/left` without `/state`**. This is a source inconsistency, not an instruction to create two subscriptions or guess firmware behavior. Its factory examples use domain0; the actual pinned SDK factory supports `Init(domain, interface)` and does not provide the separately documented three-argument shared-memory overload. Resolve the installed bridge's exact type/topic/domain/interface before an approved read-only session. Generic HG type compatibility does not establish which server is publishing. [Dex5 DDS examples](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS), [pinned channel factory](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/channel/channel_factory.hpp).

The described supported control route is **URDF joint control**. The bridge converts joint q into motor positions. The article explicitly says direct motor control is not open. q is joint position in radians, but the article additionally says thumb torque/gains use N·m-based units while the other four fingers use mN·m-based units because reduction fitting is unavailable. That conflicts with treating all generic HG tau fields as one universal physical scale. Do not move gains or torque limits between fingers or hand types; obtain the exact server's units and version before active commands. Mode1 and example gains are source descriptions, not a validated startup recipe. [Control methods and units](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS).

### Twenty URDF slots mapped to sixteen motors <a href="#twenty-urdf-slots-mapped-to-sixteen-motors" id="twenty-urdf-slots-mapped-to-sixteen-motors"></a>

| DDS/URDF slot | Joint function            | Associated physical motor |
| ------------- | ------------------------- | ------------------------- |
| 0             | Index lateral /Roll\_21L  | 0                         |
| 1             | Index MCP /Pitch\_22L     | 1                         |
| 2             | Index PIP /Pitch\_23L     | 2                         |
| 3             | Index DIP /Pitch\_24L     | 2                         |
| 4             | Middle lateral /Roll\_31L | 3                         |
| 5             | Middle MCP /Pitch\_32L    | 4                         |
| 6             | Middle PIP /Pitch\_33L    | 5                         |
| 7             | Middle DIP /Pitch\_34L    | 5                         |
| 8             | Ring lateral /Link\_41L   | 6                         |
| 9             | Ring MCP /Pitch\_42L      | 7                         |
| 10            | Ring PIP /Pitch\_43L      | 8                         |
| 11            | Ring DIP /Pitch\_44L      | 8                         |
| 12            | Pinky lateral /Roll\_51L  | 9                         |
| 13            | Pinky MCP /Pitch\_52L     | 10                        |
| 14            | Pinky PIP /Pitch\_53L     | 11                        |
| 15            | Pinky DIP /Pitch\_54L     | 11                        |
| 16            | Thumb CMC /Yaw\_11L       | 12                        |
| 17            | Thumb lateral /Roll\_12L  | 13                        |
| 18            | Thumb MP /Pitch\_13L      | 14                        |
| 19            | Thumb IP /Pitch\_14L      | 15                        |

This is the article's mapping for the URDF control profile. Four-finger q groups undergo inverse kinematics; thumb slot16 also undergoes a kinematic transform, while17–19 map directly. Other parameters and feedback share the coupled motor for each PIP/DIP pair; the article says the later pair entry prevails during parsing and recommends matching pair gains. Its secondary short table uses inconsistent labels, so retain the complete table and actual server contract. A motor association is not a20-independent-motor interface or a proof that right-hand axes have identical signs. [Full mapping and parameter rules](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS), [original motor illustration](https://doc-cdn.unitree.com/static/2026/4/24/2d330863aa394ad78df4333d61ad2539_1551x1140.png).

### Optional tactile groups and diagnostic limits <a href="#optional-tactile-groups-and-diagnostic-limits" id="optional-tactile-groups-and-diagnostic-limits"></a>

The manufacturer comparison says12 modules/94 elements, while the hardware portal says15 array units and the DDS example requires at least16 vector slots. These count different or incompletely documented groupings. Its sample printer selects15 groups, skips slot13 and prints only six values from each12-channel array:90 displayed numbers do not cover94 physical taxels. The left-hand example groups fingers at9–11,6–8,3–5,0–2, thumb at15/14 and palm at12. The original figure explicitly mirrors left/right layouts; do not reuse one side's drawing orientation as a wire map. [Sensing tables](https://www.unitree.com/Dex5-1), [portal hardware](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/About%20Dex5-1%20Hand), [sensor distribution and printer](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS).

![Dex5 source tactile-index figure; mirrored sides and raw index groups require the actual installed sensing profile](https://doc-cdn.unitree.com/static/2026/4/29/f1ba837440aa42809930935e8cf9800f_1170x751.png)

No universal raw-to-force calibration, zero offset or contact-area correction was verified. An empty pressure vector may be an option/profile difference; a loss flag or malformed group must not be silently presented as healthy data. The20 kg non-damage sensing claim is not the3.5/4.5 kg grasp rating. [Sensing conditions](https://www.unitree.com/Dex5-1), [current pressure binding](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/PressSensorState_.hpp).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: original offline mapping and raw-array inspection <a href="#first-result-original-offline-mapping-and-raw-array-inspection" id="first-result-original-offline-mapping-and-raw-array-inspection"></a>

Prerequisites: Python3.8+, no SDK installation, hand/robot powered down and disconnected. This is an original selected-metadata fixture, not a DDS decoder or kinematic solver.

1. Record hand side, base/P tactile option and unresolved bridge profile.
2. Save this complete code as `offline_dex5.py`.
3. Run `python3 offline_dex5.py` locally.
4. Confirm20 copied slots map to16 associated motors, while tactile data remains raw and uncalibrated.

```python
"""Original offline mapping fixture; no vendor code, network or actuation."""
from math import isfinite

MOTOR = (0, 1, 2, 2, 3, 4, 5, 5, 6, 7, 8, 8,
         9, 10, 11, 11, 12, 13, 14, 15)

def copy_state(q, groups, lost):
    angles = tuple(float(x) for x in q)
    if len(angles) != 20 or not all(isfinite(x) for x in angles):
        raise ValueError('twenty finite URDF-slot positions required')
    tactile = tuple(tuple(float(x) for x in row) for row in groups)
    if len(tactile) != len(lost):
        raise ValueError('one loss flag per raw group required')
    if any(type(x) is not int or x != 0 for x in lost):
        raise ValueError('loss/unknown flag; inspect raw source')
    if any(len(row) != 12 or not all(isfinite(x) for x in row)
           for row in tactile):
        raise ValueError('finite twelve-channel groups required')
    return angles, tactile

if __name__ == '__main__':
    raw = [0.0] * 20
    angles, groups = copy_state(raw, [[0.0] * 12], [0])
    raw[3] = 99.0
    print('OFFLINE PASS: %d slots; %d associated motors; slots2/3=%d/%d'
          % (len(angles), len(set(MOTOR)), MOTOR[2], MOTOR[3]))
    print('q3=%.1f; raw_groups=%d; force_N=unverified; hardware_tested=False'
          % (angles[3], len(groups)))
```

**Expected result:**

```
OFFLINE PASS: 20 slots; 16 associated motors; slots2/3=2/2
q3=0.0; raw_groups=1; force_N=unverified; hardware_tested=False
```

The single synthetic tactile group is deliberately not a physical94-taxel layout. Empty optional arrays are permitted;16-position motor data is rejected because this fixture models the documented20-slot URDF route. No q-to-motor IK, physical force, stream arrival, sensor calibration or hardware support is established by this pass.

### Gate before a later state observer <a href="#gate-before-a-later-state-observer" id="gate-before-a-later-state-observer"></a>

Resolve electrical identity, side, host kit, server package/firmware,20-slot layout, exact topic suffix, interface/domain and optional tactile map. Have an operator own the already commissioned bridge with a verified stop and object-retention plan. Bound the capture and copy fields inside callbacks with monotonic receipt timing; the current HG hand state has no source tick/timestamp. Multiple identical joint positions can be normal, while a default vector or one old message is not a proven stream. Do not run `urdf_motion_test`, a publisher or service autostart as an observation check.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### No state stream or unexpected joint count <a href="#no-state-stream-or-unexpected-joint-count" id="no-state-stream-or-unexpected-joint-count"></a>

Check the installed bridge's topic first: the dedicated document disagrees about `/state`. Confirm HG type, actual20-slot URDF route, side and service identity before interpreting vectors. A16-element vector may belong to another profile; do not pad it into a validated20-element command. Validate the archive/SDK ABI and exact firmware with support; no package helper or source include alone proves compatibility. [DDS examples](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS), [deployment](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Dex5_SDK).

### Fault flags appear or power drops <a href="#fault-flags-appear-or-power-drops" id="fault-flags-appear-or-power-drops"></a>

Preserve the actual state and loss/receipt information, make the assembly safe under its approved procedure and inspect the matched supply/harness. The source motherboard table assigns bits0–7 respectively to NO\_START, undervoltage, overvoltage,24 V internal anomaly, capacitance overload, overcurrent, output overload and startup failure. These flags do not justify repeated resetting or a higher-voltage supply. [Mainboard error table](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS).

For the source's motor error table, masks are:0x01 overcurrent;0x02 transient overvoltage;0x04 sustained overvoltage;0x08 transient undervoltage;0x10 chip overheat;0x20 MOS over/underheat;0x40 MOS temperature abnormal;0x100 housing temperature;0x200 winding overheat;0x400 rotor encoder1;0x1000 output encoder;0x2000 storage data;0x4000 abnormal reset;0x10000 chip verification;0x20000 calibration mode;0x80000 old driver;0x100000 firmware-model mismatch;0x400000 hardware overcurrent. Confirm the bridge's word location/meaning before decoding. [Motor error table](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS).

Do **not** copy the article's error-detection snippet: it indexes `motor_state()[i].reserve()[i]` for20 joints even though current reserve has only four words, and its printed bit meanings disagree with its table. The newer IDL page describes motor reserve\[0] for error status; that still requires a matching bridge version. There is no `error_code` accessor in the pinned HG MotorState declaration. [IDL explanation](https://support.unitree.com/home/en/dex3-1_hand/Dex_IDL_specification), [pinned motor state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/MotorState_.hpp), [inconsistent snippet](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS).

### Grip trajectory or torque differs by finger <a href="#grip-trajectory-or-torque-differs-by-finger" id="grip-trajectory-or-torque-differs-by-finger"></a>

Stop active testing and check the complete20-to16 table, coupled pair precedence, thumb kinematics and documented unit differences. Do not copy thumb torque/gains to the other fingers or use the unopened direct-motor mode. Retain raw commands, package/version and frame description for manufacturer review rather than tuning through collisions. [Mapping, units and control modes](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS).

### Tactile values are absent, mirrored or appear to imply excessive force <a href="#tactile-values-are-absent-mirrored-or-appear-to-imply-excessive-force" id="tactile-values-are-absent-mirrored-or-appear-to-imply-excessive-force"></a>

Check the actual P sensing option, side, group count and loss fields first. Compare the original index figure and preserve unscaled channels. A shortened printer output is not a complete taxel map; negative/large readings or defaults need calibration/profile review. Do not convert a manufacturer gram-loading headline into a channel-to-Newton formula. [Sensing distribution](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS), [comparison](https://www.unitree.com/Dex5-1).

### Installation or server startup fails <a href="#installation-or-server-startup-fails" id="installation-or-server-startup-fails"></a>

Match architecture, Linux libraries, SDK ABI, package/config directories and USB/power separately. The server's role is USB-to-DDS bridging; it is not interchangeable with an arbitrary SDK2 subscriber. The standalone article lists a precheck and log directory but no tested delivered-firmware pair was established here. No vendor helper was executed, and its name does not prove read-only hardware behavior. [Self-deployment workflow](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Dex5_SDK).

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               | Purpose / access scope                                                                                           |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| [Manufacturer comparison](https://www.unitree.com/Dex5-1) · [hardware article](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/About%20Dex5-1%20Hand)                                                                                                                                                                                                                                                                                                                                                                                                                                           | Base/P sensing, active/coupled joints, power/load and mechanics                                                  |
| [Power definition](https://doc-cdn.unitree.com/static/2026/4/24/7af77b98ae734283823d9a8056f5f90c_588x211.png) · [motor layout](https://doc-cdn.unitree.com/static/2026/4/24/2d330863aa394ad78df4333d61ad2539_1551x1140.png) · [tactile figure](https://doc-cdn.unitree.com/static/2026/4/29/f1ba837440aa42809930935e8cf9800f_1170x751.png)                                                                                                                                                                                                                                                                             | Original figures visually inspected; drawing orientation retained                                                |
| [URDF source directory](https://github.com/unitreerobotics/unitree_ros/tree/157ff950351e5f535e03c5d85a16b7d594b3dbcc/robots/dexterous_hand_description/dex5_1)                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Description resource; not hardware calibration or a tested simulator                                             |
| [Upper-layer DDS article](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Upper-Layer%20Communication%20Method%20Based%20on%20DDS) · [self-deployment workflow](https://support.unitree.com/home/en/Dex5-1%20SDK%20Development%20Guide/Dex5_SDK)                                                                                                                                                                                                                                                                                                                                                | All dedicated sections reviewed, including mappings, sensing, faulty example and troubleshooting                 |
| [ARM64 archive](https://oss-global-cdn.unitree.com/static/bedd922bac7d4bf087983b341a5f21fe.zip) · [AMD64 archive](https://oss-global-cdn.unitree.com/static/0a9ee2f250e54f8684707aeacaa3235a.zip)                                                                                                                                                                                                                                                                                                                                                                                                                      | Official program listings; archive contents not fully inspected, no binary run or exact executable release claim |
| [Current HandCmd](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/HandCmd_.hpp) · [HandState](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/HandState_.hpp) · [pressure](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/PressSensorState_.hpp) · [motor state](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/hg/MotorState_.hpp) | Pinned schema declarations, not bridge-specific firmware guarantees                                              |
| [H2 assembly](https://support.unitree.com/home/en/H2_developer/DexterousHand%20_Assembly)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | H2-specific kit/harness, side-versus-end cable routing and mounting context                                      |
| Full schematic, approved stop specification and tactile calibration                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    | Not verified for the delivered revision; obtain before active integration                                        |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed24 November2026 using all three actual dedicated Dex5 portal articles, the manufacturer comparison, observed store options, relevant H2 assembly and pinned SDK declarations. Read-source coverage and every linked resource's access state are recorded privately. The archive listing is not a claim to review or execute its proprietary implementation. Figure/URDF/download links retain manufacturer attribution and rights.

Only the original offline mapping program and synthetic invalid-shape/nonfinite/loss/copy tests were executed. No SDK/server/helper/import/build/install, DDS/ROS, USB/hardware, motion, calibration or flashing was run. Sensing counts, topic suffix, mixed torque units, approved current/harness and exact firmware/stop behavior remain bounded gaps; hardware readiness stays **draft**.

**Related documentation:** [Unitree model and development directory](./).
