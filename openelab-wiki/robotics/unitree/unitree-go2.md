---
description: >-
  Compare Go2 Air, Pro and EDU, identify battery/controller and L1/L2 revisions,
  follow the documented app-status startup, and inspect an EDU-only status
  subscriber with firmware limits.
---

# Unitree Go2 Air, Pro and EDU: model selection, startup and development limits

{% hint style="info" %}
[**View Unitree Go2 Air on OpenELAB**](https://openelab.io/products/unitree-go2-air) — robot option `GO2 Air`, SKU `Unitree-Go2-Air`\
[**View the GO2 Controller option on OpenELAB**](https://openelab.io/products/unitree-go2-air) — accessory option `GO2 Controller`, SKU `Unitree-Go2-AirC`; select this exact option on the Air listing. It is not another robot.\
[**View Unitree Go2 Pro on OpenELAB**](https://openelab.io/products/unitree-go2-pro-quadruped-robot) — SKU `Unitree-Go2-Pro`

**Models:** Unitree Go2 Air / Pro / EDU, leg-only quadrupeds. **Go2 EDU:** manufacturer reference only; no exact OpenELAB product/SKU match was found in the audited catalog. No purchasing URL or SKU is inferred for EDU. Verify the delivered battery, controller and LiDAR revision before using a procedure.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree Go2 is a twelve-joint electric quadruped. Air and Pro provide app/controller operation and graphical programming; official secondary development is an EDU capability, not an entitlement established for Air or Pro. This guide explains model selection, battery and controller differences, stationary app checks and an EDU-only route to reading status. It treats Go2-W as separate wheel-legged hardware. [Current Go2 comparison](https://www.unitree.com/go2/), [Go2 User Manual V4.3](https://marketing.unitree.com/article/en/Go2/User_Manual.html), pp. 3–5.

![Unitree Go2 Pro leg-only quadruped shown on its OpenELAB listing](../../.gitbook/assets/unitree-batch1-063a3015e1c2f5ef.jpg)

_Original product image from the verified OpenELAB Go2 Pro catalog record. Rights remain with the source; the image is not evidence of an EDU compute module, battery model or LiDAR revision._

### Which edition supports development? <a href="#which-edition-supports-development" id="which-edition-supports-development"></a>

| Capability                                                   | Go2 Air                             | Go2 Pro                 | Go2 EDU                                                                       |
| ------------------------------------------------------------ | ----------------------------------- | ----------------------- | ----------------------------------------------------------------------------- |
| App, basic actions, Wi-Fi 6/Bluetooth, graphical programming | Listed                              | Listed                  | Listed                                                                        |
| Official secondary development                               | Not listed as supported             | Not listed as supported | Supported; delivered firmware and interface details still required            |
| Wireless vector tracking / ISS 2.0, voice, 4G with GPS       | Not supported in edition comparison | Listed                  | Listed                                                                        |
| Foot-end force sensors                                       | Not listed                          | Not listed              | Listed                                                                        |
| Depth camera                                                 | Not listed                          | Not listed              | Listed in manufacturer comparison; check delivered model                      |
| Additional high-performance compute                          | Not listed                          | Not listed              | Multiple options, including Orin; exact module/BOM is configuration-dependent |
| Handheld controller                                          | Optional                            | Optional                | Listed as included in platform table                                          |
| Auto-retracting carry strap                                  | Not listed                          | Pro-specific            | Not listed                                                                    |

Source: [current manufacturer comparison](https://www.unitree.com/go2/) and V4.3 pp. 4–5. The manual's drawing labels a high-compute module as EDU standard, while its function table describes an optional Orin module. Do not infer a particular Jetson, TOPS value, depth camera or carrier image from the EDU name. The current page also shows Go2 X with a partial secondary-development symbol; X has no matched OpenELAB SKU in this scope and is not silently treated as EDU.

## Applications <a href="#applications" id="applications"></a>

Air is suited to learning app/remote operation within its documented gait limits. Pro adds the documented companion-following and interaction features. EDU provides the manufacturer-supported basis for robotics research using state telemetry, perception integration and custom control, subject to the exact supplied firmware, development entitlement and sensor BOM. [Edition table](https://www.unitree.com/go2/)

A first engineering task is identifying the unit and observing a stable connection. Autonomous routes, advanced gaits, loaded operation and joint-level control come later. V4.3 states that obstacle avoidance acts in the forward direction; a wide LiDAR field of view does not establish rearward or sideways collision protection. The user manual requires line-of-sight supervision, suitable traction and at least 2 m clearance from people, water and obstacles. It specifies dry, non-dusty conditions and 5–35 °C robot operation; marketing footage on rough terrain does not override those instructions. [User manual](https://marketing.unitree.com/article/en/Go2/User_Manual.html), pp. 2, 5, 15–16.

## Specifications <a href="#specifications" id="specifications"></a>

### Robot platform and edition differences <a href="#robot-platform-and-edition-differences" id="robot-platform-and-edition-differences"></a>

These are manufacturer-reported values, not bench measurements. Preserve the dimension order supplied by Unitree; the current table does not explicitly label axes. [Go2 parameter table and footnotes](https://www.unitree.com/go2/)

| Parameter                       | Go2 Air                                                  | Go2 Pro                                         | Go2 EDU                                                   |
| ------------------------------- | -------------------------------------------------------- | ----------------------------------------------- | --------------------------------------------------------- |
| Standing dimensions             | 70 × 31 × 40 cm                                          | Same                                            | Same                                                      |
| Crouching dimensions            | 76 × 31 × 20 cm                                          | Same                                            | Same                                                      |
| Mass including battery          | About 15 kg                                              | About 15 kg                                     | About 15 kg; actual compute/payload configuration matters |
| Construction                    | Aluminum alloy and high-strength engineering plastic     | Same                                            | Same                                                      |
| Platform voltage entry          | 28–33.6 V                                                | Same                                            | Same; not an external-supply authorization                |
| Working maximum power           | About 3,000 W                                            | Same                                            | Same; not a continuous accessory output rating            |
| Payload                         | Approximately 7 kg; maximum approximately 10 kg          | Approximately 8 kg; maximum approximately 10 kg | Approximately 8 kg; maximum approximately 12 kg           |
| Speed in current table          | 0–2.5 m/s                                                | 0–3.5 m/s                                       | 0–3.7 m/s; maximum approximately 5 m/s laboratory claim   |
| Climb/drop height               | About 15 cm                                              | About 16 cm                                     | About 16 cm                                               |
| Maximum climb angle             | 30°                                                      | 40°                                             | 40°                                                       |
| Motors / degrees of freedom     | 12 / 12                                                  | 12 / 12                                         | 12 / 12                                                   |
| Largest-joint maximum torque    | No numerical Air value in current edition table          | About 45 N·m                                    | About 45 N·m                                              |
| Mechanical motion range         | Body −48 to +48°; thigh −200 to +90°; shank −156 to −48° | Same                                            | Same                                                      |
| Standard platform battery entry | 8,000 mAh                                                | 8,000 mAh                                       | 15,000 mAh long-endurance                                 |
| Platform endurance entry        | About 1–2 h                                              | About 1–2 h                                     | About 2–4 h                                               |
| Platform charger entry          | 33.6 V / 3.5 A standard                                  | Same                                            | 33.6 V / 9 A fast                                         |

The 45 N·m figure is the largest joint motor's maximum, not every joint's continuous capability. Mechanical angular ranges are not safe commanded trajectories, calibrated zeroes or collision-free limits. V4.3 pp. 15–16 further restrict routine terrain use; the laboratory 5 m/s claim is not an initial operating speed.

### LiDAR and configuration revision gate <a href="#lidar-and-configuration-revision-gate" id="lidar-and-configuration-revision-gate"></a>

| Read source                                             | Actual statement                                              | Consequence                                                                               |
| ------------------------------------------------------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| Current Go2 manufacturer page and User Manual V4.3 p. 3 | L2, 360° × 96°; page states minimum detection distance 0.05 m | Describes that source revision, not every shipped Air/Pro/EDU                             |
| OpenELAB Air listing                                    | L1, 360° × 90°, minimum 0.05 m                                | Evidence of a different listed sensor configuration; verify the supplied sensor label/BOM |
| OpenELAB Pro listing                                    | Describes L1/L2 depending on regional version                 | Exact delivered revision is unresolved                                                    |

Do not load an L2 decoder or use L2 geometry solely because a new manual describes it. Record the LiDAR part number, firmware and driver/protocol revision from the actual unit. No exact-unit point-cloud format, extrinsic calibration or timestamp contract was established in this review. Air's storefront also mentions follow/4G capabilities that the manufacturer edition table excludes; use the explicit Air edition limits until an exact revision document resolves the discrepancy.

### Go2 batteries and chargers: part numbers matter <a href="#go2-batteries-and-chargers-part-numbers-matter" id="go2-batteries-and-chargers-part-numbers-matter"></a>

The current battery manual is **V1.1**, revision history dated **27 May 2026**. The following values were checked against its original p. 3 table. [Go2 battery and charger manual](https://marketing.unitree.com/article/en/Go2/Battery_Charger.html)

| Parameter                            | BT2-05 standard      | BT2-06 long-endurance |
| ------------------------------------ | -------------------- | --------------------- |
| Case dimensions                      | 120 × 80 × 182 mm    | Same                  |
| Rated voltage                        | 29.6 V DC            | 28.8 V DC             |
| Limited charge voltage               | 33.6 V DC            | 33.6 V DC             |
| Rated capacity / energy              | 8,000 mAh / 236.8 Wh | 15,000 mAh / 432 Wh   |
| Battery-manual running-time entry    | 1–2 h                | 3–5 h                 |
| Standard-charger charging-time entry | 2 h                  | 4 h                   |
| Fast-charger charging-time entry     | 0.8 h                | 1.5 h                 |

Unitree says BMS reserves and operating conditions can make usable capacity 5–10% below nominal. The BT2-06 battery table's 3–5 h and the robot page's EDU 2–4 h are different source-level claims with no common test conditions supplied; neither guarantees loaded application runtime.

**Electrical discrepancy requiring label confirmation:** the battery manual p. 3 gives the standard charger's output as **34.0 V / 3.5 A / 119.0 W**, while both packs' limited charge voltage is **33.6 V** and the robot page calls the standard charger **33.6 V / 3.5 A**. The fast-charger table gives 33.6 V / 9 A / 302.4 W. Do not average these values, select a third-party charger or set a bench supply from this guide. Confirm the delivered Unitree charger/pack part numbers and approved pairing before charging. Both manual charger columns show 100–240 V AC, 50/60 Hz input, but the actual charger's nameplate remains the required check.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Identify, inspect and place the robot <a href="#identify-inspect-and-place-the-robot" id="identify-inspect-and-place-the-robot"></a>

Check the robot serial and edition, battery label, original charger, controller model, installed LiDAR and optional EDU modules against the packing list. Unpack while powered off; the manual allows lifting with the strap for unpacking but explicitly prohibits lifting a powered robot. Inspect feet, joints, cameras, LiDAR and connectors for damage or contamination; foot pads are consumables. External accessories change the envelope and collision risk, and the manual prohibits side rolling with back-mounted equipment. [User manual](https://marketing.unitree.com/article/en/Go2/User_Manual.html), pp. 2, 6–8, 15–16.

The powered-off Go2 battery installs from the side with its switch facing upward. Align the keyed pack, insert without force and confirm the latch click. For startup, the abdominal support pad rests flat on a level surface, the body is horizontal, lower legs are retracted, and the feet/joints are placed as in the original figure so the body does not trap the legs. Do not substitute a standing or suspended startup arrangement. [Battery installation and startup figure](https://marketing.unitree.com/article/en/Go2/User_Manual.html), pp. 7–8; [original p. 8 diagram](https://doc-cdn.unitree.com/static/2026/6/4/2505a082c2ad442ba5078f45c771dfe1_2482x3509.png).

A battery physical drawing identifies its charge and discharge interfaces but does not publish the contacts' electrical pinout. No verified expansion pinout, GPIO logic levels, accessory-current budget, mounting torque or third-party supply procedure was available. Do not infer them from case photographs, an RJ45-shaped socket or the platform's 3,000 W maximum power entry.

### Battery use, charging and storage <a href="#battery-use-charging-and-storage" id="battery-use-charging-and-storage"></a>

| Topic                            | Supported Go2-specific guidance and limit                                                                                                   | Manual location                                                                        |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| Live handling                    | Switch pack off before insertion/removal; no hot swapping                                                                                   | Battery pp. 4, 8                                                                       |
| Low energy                       | Stop use promptly below 40%; do not rely on BMS cutoff to finish a session                                                                  | Battery p. 8                                                                           |
| Charging preparation             | Remove pack from robot, switch it off, allow it to cool to room temperature, use the approved Unitree charger and confirm nameplate/pairing | Battery pp. 5–6, 9                                                                     |
| Charging environment             | Supervise in a ventilated dry area on a noncombustible surface; recommended ambient 5–40 °C                                                 | Battery p. 9                                                                           |
| Battery versus robot temperature | Battery manual gives −15 to 55 °C battery use; robot manual gives 5–35 °C robot use                                                         | Battery p. 8; robot p. 2; battery range does not expand robot rating                   |
| Protection thresholds            | Manual reports charging-temperature protection outside 0–50 °C, charge-current protection above 15 A and output cutoff at 24 V              | Battery p. 4; protection limits are not operating targets or external charger settings |
| Load detection                   | Pack cannot normally turn on outside robot and turns off if removed                                                                         | Battery p. 4; not permission to remove a live pack                                     |
| Storage                          | Remove pack, keep dry; preferred storage 22–28 °C; do not store above 40 °C                                                                 | Battery pp. 9–10                                                                       |
| Long storage                     | Above 65%, idle 10 days triggers self-discharge toward 65%; periodic check, recharge to 70% if below 30%                                    | Battery pp. 3, 10                                                                      |
| Shipping / end of life           | Manual describes approximately 65% for transport and battery recycling; damaged packs require specialist handling                           | Battery pp. 7, 10; obtain carrier-specific current instructions before shipping        |

A damaged, swollen, wet or severely impacted pack is not a candidate for a charge/retry cycle. Do not open, puncture, short contacts or attempt to defeat protections. The manual's disposal section discusses discharge, but this guide does not direct a user to discharge a damaged pack; arrange approved battery service/recycling.

### Distinguish the controllers before charging or reading LEDs <a href="#distinguish-the-controllers-before-charging-or-reading-leds" id="distinguish-the-controllers-before-charging-or-reading-leds"></a>

The handheld manual **V2.3** covers **R3** and older **R1** remotes. It says R3 superseded R1 starting December 2024 but either may be shipped. This remote named R1 is not the Unitree R1 humanoid robot. The `Unitree-Go2-AirC` store option does not establish which remote revision is delivered. [Handheld manual](https://marketing.unitree.com/article/en/Go2/Handheld_Remote_Control.html), pp. 2–6, 11–13.

| Controller       | Electrical / battery table       | Power and charging differences                                                     |
| ---------------- | -------------------------------- | ---------------------------------------------------------------------------------- |
| R3 handheld      | 5 V; 700 mA; 780 mAh; about 5 h  | USB-C; manual recommends 5 V / 2 A source, controller off; full-charge LEDs all on |
| R1 handheld      | 5 V; 2 A; 2,500 mAh; about 4.5 h | USB-C; 5 V / 2 A recommended source, controller off; full-charge LEDs all off      |
| Companion remote | 5 V; 600 mA; 520 mAh; about 5 h  | USB-C; manual recommends 5 V / 1 A source; full-charge LEDs all off                |

The handheld remotes use a short power press followed by a hold longer than 2 s; the companion turns on with one short press and off with a hold longer than 2 s. Do not confuse the remotes' USB supply with the robot battery's charger. The handheld's over-100 m and companion's over-15 m manual distance claims are open-environment figures; the current robot page's over-30 m ISS claim describes another source context and does not guarantee a working range through walls.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Consumer operation and EDU development are separate paths <a href="#consumer-operation-and-edu-development-are-separate-paths" id="consumer-operation-and-edu-development-are-separate-paths"></a>

For Air/Pro, use the **Unitree Go** app from the [official Go2 download page](https://www.unitree.com/app/go2/) and its built-in tutorial. Graphical programming does not establish low-level SDK access. The app workflow in V4.3 pp. 9–11 includes account binding, Bluetooth discovery, AP or router Wi-Fi connection and optional handheld binding. Menu labels can vary with app release; record the actual version before troubleshooting.

For an entitled EDU, the reviewed Python SDK snapshot is **`814556d15970dd2ecf1c9984e845ca02ab07e206`**, package metadata version **1.0.1**, **BSD-3-Clause**. Its declared dependencies are Python ≥3.8, `cyclonedds == 0.10.2`, NumPy and OpenCV. The SDK's Go2 low-state reader and actual Go2 examples use `unitree_go.msg.dds_`, not the G1 `unitree_hg` message family. [Pinned setup metadata](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py), [license](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/LICENSE), [read-only source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/test/lowlevel/read_lowstate.py).

The C++ SDK2 README snapshot `b7fec6020eb93d4c059a6edf19905e12a75a8d3d` names Ubuntu 20.04 LTS, aarch64/x86\_64 and GCC 9.4.0 as its prebuild environment. Its core includes architecture-specific prebuilt libraries; a wrapper/example build is not evidence of a fully source-rebuildable control stack. This does not prove native macOS support or compatibility with any EDU firmware. The developer portal was inaccessible, so exact network settings, firmware/API version ranges, provisioning and recovery remain unresolved. SDK installation/build and ROS setup are outside this guide's performed validation. [Pinned C++ README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md)

### Which examples are safe to treat as status readers? <a href="#which-examples-are-safe-to-treat-as-status-readers" id="which-examples-are-safe-to-treat-as-status-readers"></a>

The inspected `unitree_sdk2py/test/lowlevel/read_lowstate.py` creates a subscriber for `rt/lowstate` and prints front-right hip, IMU and power fields. By contrast, `example/go2/low_level/go2_stand_example.py` publishes `rt/lowcmd`, calls `StandDown()` / `ReleaseMode()` and changes joint targets. The README's older `lowlevel_control.py` wording appears under both status and active motor instructions. Never infer read-only behavior from a filename or heading. [Actual stand source](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2/low_level/go2_stand_example.py)

Go2 leg SDK indices are `FR_0..FR_2 = 0..2`, `FL_0..FL_2 = 3..5`, `RR_0..RR_2 = 6..8`, `RL_0..RL_2 = 9..11`. They are message-array positions, not connector pins. The `LowState_` type allocates **20** motor slots; only twelve leg indices are established by this Go2 map. Slots do not prove extra physical actuators. Go2-W adds explicit wheel identifiers 12–15 in its separate map. [Go2 constants](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/go2/low_level/unitree_legged_const.py)

## Getting started <a href="#getting-started" id="getting-started"></a>

### Prerequisites and stop conditions <a href="#prerequisites-and-stop-conditions" id="prerequisites-and-stop-conditions"></a>

For the consumer checkpoint, use an identified Air/Pro, approved charged Go2 battery and an available Unitree Go account/phone with Bluetooth permissions. Read the original startup posture and stop controls first. Clear a dry, level area with adequate traction, 5–35 °C ambient and at least 2 m clearance. Power-on can make the robot stand automatically; this is not a motion-free electrical test. Do not lift or reposition it while powered. A trained operator must know the matched app/controller stop action. [V4.3 pp. 2, 7–11](https://marketing.unitree.com/article/en/Go2/User_Manual.html)

Before using a handheld remote, identify R1/R3 and the correct button layout. V2.3 p. 9 maps **hold `L2` + click `B`** to damping/emergency stop and **hold `L2` + click `A`** to stand-lock/low-down. Damping is an operating mode, not electrical isolation or a guarantee that the robot remains upright. Keep hands clear of joints and do not practice a shutdown while someone supports a powered leg. [Original R3 control table](https://doc-cdn.unitree.com/static/2025/12/22/dd0126329a594c34a36b936565dffe17_2481x3509.png)

### First working result for Air/Pro: correct app identity and status <a href="#first-working-result-for-airpro-correct-app-identity-and-status" id="first-working-result-for-airpro-correct-app-identity-and-status"></a>

1. With the battery off, inspect and install it switch-up until latched. Place the robot in the original flat startup posture described above; inspect leg clearance and keep the operator outside the motion envelope.
2. **Resolve the supplied pack's power-button instruction before starting.** V4.3 p. 8 says short press then hold at least 2 s; BT2 battery manual V1.1 p. 5 says short press then hold more than 3 s. For a confirmed BT2-05/BT2-06 with V1.1 applicable, its documented longer-than-3 s hold also exceeds the robot manual's minimum, but record and confirm the supplied revision; do not repeatedly power-cycle to investigate an unidentified pack. If the pack/manual cannot be matched, stop here.
3. Observe startup from a safe distance. V4.3 p. 8 describes flashing green during boot and steady green, with body horizontal, after approximately 2 minutes. Abnormal posture, slipping, persistent slow red or fast red is a failure checkpoint, not a prompt to command a gait.
4. Install Unitree Go from the official page, complete account sign-in, enable phone Bluetooth and app Bluetooth permissions, and keep the phone close for discovery. In the manual's flow choose **Home → Add robot**, select the unit matching your label, and enter its name/information. Do not select a neighboring robot merely because it appears in the list.
5. Select the documented AP/hotspot path for the first local connection or a known router Wi-Fi path. For AP, connect the phone's Wi-Fi settings to the robot hotspot established by that flow; for router mode, use the intended router SSID/password. Return to the app and complete binding. No default password or fixed IP is inferred from the manual screenshots.
6. Read the connected identity, battery/status and available camera view without selecting a gait, side-follow, autonomous route or calibration. Preserve app version, robot firmware, edition, battery model and LiDAR label. Complete the in-app tutorial before any later manual motion.

**Expected result:** the intended Air/Pro is bound to the authorized account, the app connection is live, and startup/status is normal. A live camera view is an additional check when that app/firmware exposes it; it does not validate LiDAR decoding or obstacle detection. No success was observed on hardware during this documentation work. [V4.3 pp. 8–11](https://marketing.unitree.com/article/en/Go2/User_Manual.html)

**If this check fails:** use the status-light and connection diagnostics below. Do not calibrate a normal robot, unbind someone else's unit, bypass account ownership or run SDK examples on Air/Pro.

To finish a normal session, use the trained app/remote low-down action while on a stable level surface; confirm the prone/damping state before switching off. V4.3 p. 13 warns that removing power while standing can cause a hard fall. Match the supplied battery's short-press/hold instruction as above, confirm lights go out, then remove the pack if storing. Forced battery shutdown is not a normal stop method.

### EDU-only first developer result: one bounded low-state sample <a href="#edu-only-first-developer-result-one-bounded-low-state-sample" id="edu-only-first-developer-result-one-bounded-low-state-sample"></a>

This conditional path requires an already commissioned **Go2 EDU** with explicit development entitlement, an approved firmware/SDK pairing and supplier-provisioned host network. It does not apply to the Air/Pro SKUs above. Because the developer portal and exact delivered EDU configuration were unavailable, the network/firmware prerequisites remain a gate; no guessed robot IP, login, installation command or service release is supplied.

In an existing verified Python environment at the pinned SDK commit, save this original example as `read_go2_edu_status.py`. Replace `ROBOT_INTERFACE` with the actual provisioned Linux interface name when invoking it. The source-level API is supported by the official reader and channel implementation; hardware compatibility is still conditional.

```python
import sys
from unitree_sdk2py.core.channel import ChannelFactoryInitialize, ChannelSubscriber
from unitree_sdk2py.idl.unitree_go.msg.dds_ import LowState_

if len(sys.argv) != 2:
    raise SystemExit("Usage: python3 read_go2_edu_status.py ROBOT_INTERFACE")
ChannelFactoryInitialize(0, sys.argv[1])
sub = ChannelSubscriber("rt/lowstate", LowState_)
sub.Init()
try:
    msg = sub.Read(10.0)
    if msg is None:
        raise SystemExit("No Go2 EDU state in 10 seconds; check approved network/firmware.")
    if len(msg.motor_state) < 12:
        raise SystemExit("Insufficient motor slots; verify type and firmware.")
    print("tick:", msg.tick)
    print("power_v:", msg.power_v, "power_a:", msg.power_a)
    print("FR_0 q:", msg.motor_state[0].q, "dq:", msg.motor_state[0].dq)
    print("IMU:", msg.imu_state)
finally:
    sub.Close()
```

```bash
python3 read_go2_edu_status.py ROBOT_INTERFACE
```

**Expected result:** at most one decoded `LowState_` sample within ten seconds, followed by subscriber closure. Check the selected robot's app/label and preserve the real output; the sample's fields alone do not establish identity, force-sensor calibration or actuator safety. Field names are printed as defined by the IDL; do not infer a physical unit or sign convention without the exact firmware protocol reference. This example has no low-command publisher, sport client or motion-switcher calls. [Official status reader](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/test/lowlevel/read_lowstate.py), [channel implementation](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/unitree_sdk2py/core/channel.py).

On timeout, close the reader and check exact edition, SDK snapshot, supplied firmware, message family, selected interface and the approved network's DDS discovery policy. An app link is not proof of DDS reachability. Do not call `ReleaseMode()`, disable the sport service or flash firmware as a connectivity experiment.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### What do the Go2 head lights mean? <a href="#what-do-the-go2-head-lights-mean" id="what-do-the-go2-head-lights-mean"></a>

The following paraphrases V4.3 p. 4; lights can have mode priority, so use the app's state alongside them.

| Indication        | Manual meaning                                               | First diagnostic action                                                              |
| ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| Flashing green    | Boot in progress                                             | Wait for the documented startup checkpoint without touching the unit                 |
| Steady green      | Powered on, default avoidance enabled                        | Confirm app identity/status before further work                                      |
| Steady blue       | Avoidance disabled                                           | Do not assume perception protection remains enabled                                  |
| Steady yellow     | Endurance/range mode                                         | Distinguish from flashing low-battery yellow                                         |
| Steady purple     | Companion mode                                               | Check control ownership; app and companion cannot control simultaneously             |
| Slow blue flash   | Motor/IMU calibration in progress                            | Do not interrupt or invent a calibration procedure                                   |
| Slow yellow flash | Low battery; manual says automatic crouch within ten minutes | End operation safely now, not at the ten-minute boundary                             |
| Slow red flash    | Boot/system/hardware abnormality                             | Power down safely, check original startup posture; persistent fault requires support |
| Fast red flash    | Motor/IMU calibration failed                                 | Preserve error/status and consult support; no repeated blind calibration             |
| Steady white      | Head illumination                                            | Not a standalone fault clearance                                                     |

The indicated priority is companion purple above endurance yellow above avoidance-off blue; a purple light does not prove avoidance is on. [Original indicator table](https://doc-cdn.unitree.com/static/2026/6/4/73171cb89cb14acbbad83773e3c379c9_2481x3509.png)

### The robot does not stand after boot, or its posture is abnormal <a href="#the-robot-does-not-stand-after-boot-or-its-posture-is-abnormal" id="the-robot-does-not-stand-after-boot-or-its-posture-is-abnormal"></a>

For slow-red startup failure, V4.3 p. 14 first directs checking the startup placement and rebooting after correct placement. Power down before repositioning. If the fault persists, record the app alarm and contact Unitree support. For abnormal posture/falls after restart, the manual says to consult technical support before joint calibration; factory-calibrated normal units should not be recalibrated. It identifies **Settings → Data → Machine Dog → imu Information → Calibration**, but that menu location is not authorization to start calibration without the exact support procedure and safe setup.

### The app cannot discover, connect to or control Go2 <a href="#the-app-cannot-discover-connect-to-or-control-go2" id="the-app-cannot-discover-connect-to-or-control-go2"></a>

Check Bluetooth and app permission first, then distinguish the paths: AP requires the phone on the robot's own hotspot; router Wi-Fi requires the intended network and external connectivity; 4G requires a supported edition/region and active data service. The manual's account-binding path is **Home → Settings → Robot Settings → Switch Connection → Unbind** for the authorized account owner. Unbinding removes app control and permits another binding; it is not a casual connectivity reset. Lost binding accounts require official support. If connected but control is unavailable, first exit companion-follow mode and turn the companion remote off. [V4.3 pp. 9–10, 14](https://marketing.unitree.com/article/en/Go2/User_Manual.html)

### The handheld connects differently or its charging lights seem wrong <a href="#the-handheld-connects-differently-or-its-charging-lights-seem-wrong" id="the-handheld-connects-differently-or-its-charging-lights-seem-wrong"></a>

Identify R3 versus R1. Bind through **Settings → Data → Remote Control**, enable its switch and enter the actual controller's code; the manual screenshot's code is illustrative, not a universal ID. R3 uses its right DL indicator to confirm its data link; the R1 section describes the left-side signal lights. Full charging is all-on for R3 and all-off for R1. R3 may shut off after ten minutes without a robot/phone connection or input. [Handheld V2.3 pp. 6–7, 10, 12–13](https://marketing.unitree.com/article/en/Go2/Handheld_Remote_Control.html)

For genuine joystick-centering trouble, the manual's handheld calibration sequence is: do not touch the sticks; press/release F1 and F3 together; after the periodic beeps begin, move both sticks through their full travel/rotations until beeping stops; press F3 to apply. Perform controller calibration only in a setup that cannot command the robot inadvertently. This is remote-stick calibration, not robot joint/IMU calibration. R3 feedback options use triple F3 to choose sound/vibration and triple F1 to toggle feedback; holding F1 during shutdown saves that feedback choice. [Handheld pp. 4–5, 12](https://marketing.unitree.com/article/en/Go2/Handheld_Remote_Control.html)

### How does the companion remote differ from the handheld? <a href="#how-does-the-companion-remote-differ-from-the-handheld" id="how-does-the-companion-remote-differ-from-the-handheld"></a>

The companion is a wearable ISS controller, unavailable as an Air feature in the robot edition table. The manual places it on the right side of the user's belt while the user stands to the robot's left facing the same direction; its table lists a 0.2–1.2 m carrying height. `M` once exits follow into joystick mode; double `M` starts slow follow, and another double press in slow mode requests fast follow. Published maxima are 1.5 and 3.0 m/s, not recommended first-test speeds. Joystick input also exits follow; placing the remote horizontally or powering it off is described as another exit. [Companion V1.0 pp. 2, 4–6](https://marketing.unitree.com/article/en/Go2/Companion_Remote_Control.html)

`L2` twice enables avoidance; once disables it. `P` twice cycles prone/damped/standing, and a held `P` requests recovery from a rollover. `L1` changes heading in 0.1 rad increments by the documented single/double press. These are active controls; they are not part of the first-status workflow, and rollover/recovery must not be attempted with mounted back accessories. The app and companion must not issue control simultaneously. Maintain line of sight and avoid relying on automatic following or forward avoidance as a safety system.

### The battery will not charge, or a protection light flashes <a href="#the-battery-will-not-charge-or-a-protection-light-flashes" id="the-battery-will-not-charge-or-a-protection-light-flashes"></a>

First confirm actual battery and charger labels, approved pairing, powered-off removed pack, dry intact contacts and room-temperature cooling. Compare the **original** V1.1 pp. 4–7 LED tables; solid, off, flash color and flash frequency matter. The protection table distinguishes temperature, voltage, overcurrent/short circuit, host-readable detailed faults and firmware-update mode. Do not guess the LED-to-fault mapping from OCR, bypass protection or retry a damaged pack. The battery's normal full-charge LEDs go out; this is different from R3 remote full-charge LEDs. [Battery manual](https://marketing.unitree.com/article/en/Go2/Battery_Charger.html)

### LiDAR stops or the SDK produces no data <a href="#lidar-stops-or-the-sdk-produces-no-data" id="lidar-stops-or-the-sdk-produces-no-data"></a>

Stop motion and record the exact sensor identity and app alarm before checking obstruction or compatibility. V4.3 pp. 14–15 describes automatic resumption after an external force is removed, restart and escalation. Although its text mentions manually nudging the scanner, this guide does not instruct touching a powered scanner: use a model-specific safe service procedure. L1/L2 labels, driver revision, firmware, frame definition and extrinsics must match before a point cloud can be accepted. A video connection does not validate a LiDAR stream.

### What firmware update and recovery is supported? <a href="#what-firmware-update-and-recovery-is-supported" id="what-firmware-update-and-recovery-is-supported"></a>

OTA is listed, and the user manual recommends current firmware, but the accessible sources do not establish an exact current firmware number, upgrade compatibility matrix, offline image, downgrade path, bootloader recovery or factory-reset sequence. Record app/robot/controller/battery firmware first, obtain the exact model's approved update instructions and do not update to diagnose an unexplained fault. Battery firmware-update LEDs are not a flashing tutorial. A battery forced-off hold longer than 15 s is documented in V1.1 p. 5, but it can remove power abruptly and is not the normal stop or a demonstrated recovery method. No firmware flashing was performed.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                     | Purpose / scope                                                            | Source and read state                                                                                                                             |
| ---------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Go2 product page             | Current Air/Pro/X/EDU comparison; not a delivered BOM                      | [Official page](https://www.unitree.com/go2/), read                                                                                               |
| Go2 app/download hub         | Official Unitree Go app and the four observed manuals below                | [Official download page](https://www.unitree.com/app/go2/), read                                                                                  |
| Go2 User Manual V4.3         | 17 original page images; safety, assembly, binding, operation, diagnostics | [Original manual](https://marketing.unitree.com/article/en/Go2/User_Manual.html), OCR-assisted review plus critical visual checks                 |
| Go2 Battery and Charger V1.1 | 10 images; BT2-05/BT2-06, charging, protection, care; revision 27 May 2026 | [Original manual](https://marketing.unitree.com/article/en/Go2/Battery_Charger.html), OCR-assisted review plus critical visual checks             |
| Go2 Handheld Remote V2.3     | 16 images; R3 and older R1, distinct charging indicators                   | [Original manual](https://marketing.unitree.com/article/en/Go2/Handheld_Remote_Control.html), OCR-assisted review plus control-table visual check |
| Go2 Companion Remote V1.0    | 6 images; wearable controls, charging, follow limits                       | [Original manual](https://marketing.unitree.com/article/en/Go2/Companion_Remote_Control.html), OCR-assisted review                                |
| EDU SDK2 Python              | Actual status reader, IDL, dependencies and source license                 | [Pinned SDK tree](https://github.com/unitreerobotics/unitree_sdk2_python/tree/814556d15970dd2ecf1c9984e845ca02ab07e206), relevant source read     |
| SDK2 C++                     | Supported reference build environment                                      | [Pinned README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), read; not built         |

Exact-unit schematics/pinouts, dimensioned mounting/CAD, EDU network commissioning, firmware compatibility/releases/recovery images, LiDAR packet/calibration references and optional compute carrier images were not established from the accessible material. The developer support portal remained inaccessible; a link to it is not a claim of having read it.

### Complete source-page and functional coverage index <a href="#complete-source-page-and-functional-coverage-index" id="complete-source-page-and-functional-coverage-index"></a>

The index below accounts for all **49 observed page images** in the four official English manuals, including cover and policy pages. Each link opens the original Unitree page image, preserving diagrams and graphical tables. The guide supplies original engineering interpretation; it does not republish full manual text or facsimiles. Page numbers are source sequence positions, including the cover. OCR is a private reading aid, not an authoritative transcript. The reviewed manual scope is Go2, not Go2-W.

### Go2 User Manual V4.3: complete source-page index <a href="#go2-user-manual-v43-complete-source-page-index" id="go2-user-manual-v43-complete-source-page-index"></a>

Original Unitree source: [Go2 User Manual V4.3](https://marketing.unitree.com/article/en/Go2/User_Manual.html). Page links open the OEM originals; summaries below are original engineering interpretation, not a transcript.

| Source page | Section and engineering use                                                                                                                         | Original                                                                                                |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| 1           | **Cover / version:** Establish V4.3 as the reviewed revision; the edition does not identify the delivered sensor.                                   | [OEM p. 1](https://doc-cdn.unitree.com/static/2026/6/4/c772b4b89a874987a60250e9633e054c_2482x3509.png)  |
| 2           | **Safety / environment:** Use dry 5–35 °C conditions, line of sight, traction and clearance; never lift a powered robot.                            | [OEM p. 2](https://doc-cdn.unitree.com/static/2026/6/4/60864762e25a43ac88c4db26d0e69d28_2482x3509.png)  |
| 3           | **Identity / parts:** Twelve-joint architecture, named parts and L2 revision; verify the delivered L1/L2 BOM.                                       | [OEM p. 3](https://doc-cdn.unitree.com/static/2026/6/4/504662926dfb4857961471c23a5f579c_2481x3509.png)  |
| 4           | **Edition matrix / status lights:** Separate Air/Pro/EDU entitlements and read flash patterns as well as colors.                                    | [OEM p. 4](https://doc-cdn.unitree.com/static/2026/6/4/73171cb89cb14acbbad83773e3c379c9_2481x3509.png)  |
| 5           | **Avoidance / following / voice / carry strap:** Forward avoidance is limited; Air lacks ISS/voice/4G and the retracting strap is Pro-specific.     | [OEM p. 5](https://doc-cdn.unitree.com/static/2026/6/4/b5a864e44edd45bab1aa14624de80d7d_2481x3509.png)  |
| 6           | **Case / unpacking / packing:** Remove accessories systematically while off; match the received contents and illustrated packing posture.           | [OEM p. 6](https://doc-cdn.unitree.com/static/2026/6/4/5d4453cafc1140cb863ddee4e662dcdf_2481x3509.png)  |
| 7           | **Inspection / battery installation:** Inspect genuine parts and sensors; insert the off pack switch-up without force until latched.                | [OEM p. 7](https://doc-cdn.unitree.com/static/2026/6/4/809b528b366c4e1781265180ac0e52fe_2482x3509.png)  |
| 8           | **Horizontal posture / startup:** Use the belly-pad and retracted-leg figure; reconcile pack timing before the automatic standing sequence.         | [OEM p. 8](https://doc-cdn.unitree.com/static/2026/6/4/2505a082c2ad442ba5078f45c771dfe1_2482x3509.png)  |
| 9           | **App account / Bluetooth / AP or router:** Bind the label-matched robot and select the intended local network; screenshot names are examples.      | [OEM p. 9](https://doc-cdn.unitree.com/static/2026/6/4/ccbffccb6eab4d19bc7a2666f816a322_2481x3509.png)  |
| 10          | **Unbinding / permissions:** Unbinding removes app control and changes ownership access; use permission checks first.                               | [OEM p. 10](https://doc-cdn.unitree.com/static/2026/6/4/d43ca4827b8845548c9b62ab2f6409e6_2481x3509.png) |
| 11          | **App / voice / handheld:** Complete training, distinguish app speech from offline voice, and bind the actual handheld code.                        | [OEM p. 11](https://doc-cdn.unitree.com/static/2026/6/4/6fb4a5c8295c4ef4a32a5fcda1f2dfc0_2481x3509.png) |
| 12          | **Companion controls:** Separate joystick, slow/fast follow, avoidance switching and exit actions; keep active controls outside first status check. | [OEM p. 12](https://doc-cdn.unitree.com/static/2026/6/4/db9eb437b5d74561b953e8c2ae13df2e_2481x3509.png) |
| 13          | **Normal shutdown / storage:** Low down before off to avoid a fall; only handle after shutdown and prepare the next startup posture.                | [OEM p. 13](https://doc-cdn.unitree.com/static/2026/6/4/3c6acd311f2a48a0ad0027eb64f5484f_2482x3509.png) |
| 14          | **Faults / connection / calibration / LiDAR:** Check posture and connection path first; factory calibration should not be repeated without support. | [OEM p. 14](https://doc-cdn.unitree.com/static/2026/6/4/6710735a7e3640f8ad31cb179a49619c_2481x3508.png) |
| 15          | **Terrain / endurance / foot wear:** Loaded or crouched operation changes endurance; respect edition terrain limits and inspect consumable feet.    | [OEM p. 15](https://doc-cdn.unitree.com/static/2026/6/4/34f0f6d192bd4041839f1b86a52ec1c1_2481x3508.png) |
| 16          | **Terrain cautions / disclaimer:** Keep hands clear of joints and retain OEM restrictions on unsuitable conditions and modification.                | [OEM p. 16](https://doc-cdn.unitree.com/static/2026/6/4/c6a002b241cb407e8cdab0813529b3de_2481x3508.png) |
| 17          | **Disclaimer continuation:** Retain original terms and regional rights in the source; no new warranty promise is made here.                         | [OEM p. 17](https://doc-cdn.unitree.com/static/2026/6/4/c5f7f68ad6d541539f34b44cd85da856_2481x3508.png) |

### Go2 Battery and Charger V1.1: complete source-page index <a href="#go2-battery-and-charger-v11-complete-source-page-index" id="go2-battery-and-charger-v11-complete-source-page-index"></a>

Original Unitree source: [Go2 Battery and Charger V1.1](https://marketing.unitree.com/article/en/Go2/Battery_Charger.html). Page links open the OEM originals; summaries below are original engineering interpretation, not a transcript.

| Source page | Section and engineering use                                                                                                                                                                | Original                                                                                                 |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| 1           | **Cover / version:** Use V1.1 for BT2 revision comparison, not as a Go2-W applicability declaration.                                                                                       | [OEM p. 1](https://doc-cdn.unitree.com/static/2026/5/27/4de74bd4189540c09dde8c956f15f41c_2481x3508.png)  |
| 2           | **Battery / charger anatomy:** Distinguish BT2-05/BT2-06, keyed pack, latch, charge and discharge interfaces; drawings are not pinouts.                                                    | [OEM p. 2](https://doc-cdn.unitree.com/static/2026/5/27/37b8dbe7332d41b0adb680ccea86ed94_2481x3508.png)  |
| 3           | **Ratings / times / BMS:** Keep nominal capacity, usable reserve and runtime separate; flag 34.0 V versus 33.6 V standard-charger discrepancy.                                             | [OEM p. 3](https://doc-cdn.unitree.com/static/2026/5/27/9bb7e8b52a284d99b7b6d1aaae72a677_2481x3508.png)  |
| 4           | **Protections / off-state LED levels:** Protection thresholds are not operating targets; load detection does not authorize hot removal.                                                    | [OEM p. 4](https://doc-cdn.unitree.com/static/2026/5/27/1893107ce96746db957c0b343ecaf75c_2481x3508.png)  |
| 5           | **Discharge LEDs / power / force-off / charging:** Pack hold exceeds 3 s, unlike robot-manual minimum; forced-off is not a normal stop.                                                    | [OEM p. 5](https://doc-cdn.unitree.com/static/2026/5/27/4dd3d798208b4f1889152b6e2c20b5df_2482x3508.png)  |
| 6           | **Charging connection / completion LEDs:** Remove and cool the off pack; full-charge LEDs off differ from the R3 remote.                                                                   | [OEM p. 6](https://doc-cdn.unitree.com/static/2026/5/27/1894c1ad413546ecb9978d629d366ff3_2482x3508.png)  |
| 7           | **Protection indicators / transport discharge:** Use original blink diagrams to identify the fault category; do not bypass protection or infer a firmware procedure.                       | [OEM p. 7](https://doc-cdn.unitree.com/static/2026/5/27/965859af41f64b8a90e39d77d9125693_2481x3508.png)  |
| 8           | **Use safety / damage / temperature:** Stop promptly below 40%; damaged or impacted packs need approved service and must not be punctured or shorted.                                      | [OEM p. 8](https://doc-cdn.unitree.com/static/2026/5/27/dcd8fa07ddd541aca3d9d7f9af8bd848_2481x3508.png)  |
| 9           | **Charging / storage environment:** Supervise approved charging after cooling; separate charge, use and preferred storage temperatures.                                                    | [OEM p. 9](https://doc-cdn.unitree.com/static/2026/5/27/c1e0f0c0c6514876914d9ea53df44af4_2481x3508.png)  |
| 10          | **Storage / maintenance / disposal / revision:** Check stored charge periodically; keep damaged packs out of normal discharge/retry workflows; revision history dates V1.1 to 27 May 2026. | [OEM p. 10](https://doc-cdn.unitree.com/static/2026/5/27/58afa443c406466c86293f7a6c88d391_2481x3508.png) |

### Go2 Companion Remote V1.0: complete source-page index <a href="#go2-companion-remote-v10-complete-source-page-index" id="go2-companion-remote-v10-complete-source-page-index"></a>

Original Unitree source: [Go2 Companion Remote V1.0](https://marketing.unitree.com/article/en/Go2/Companion_Remote_Control.html). Page links open the OEM originals; summaries below are original engineering interpretation, not a transcript.

| Source page | Section and engineering use                                                                                                                                  | Original                                                                                               |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ |
| 1           | **Cover / version:** Identify the wearable companion manual independently of handheld R1/R3.                                                                 | [OEM p. 1](https://doc-cdn.unitree.com/static/2024/6/5/e380f8e11ada45959a46ca9074ce189a_2482x3508.png) |
| 2           | **Anatomy / electrical / radio / wearing height:** Use the 5 V USB-C requirements and published wearing range; wireless figures are open-environment claims. | [OEM p. 2](https://doc-cdn.unitree.com/static/2024/6/5/f4021edafcf44146a1cabe3bff3fd8f4_2482x3508.png) |
| 3           | **Power / USB charging / LEDs:** One short press starts it; the documented 5 V / 1 A source differs from handheld recommendations.                           | [OEM p. 3](https://doc-cdn.unitree.com/static/2024/6/5/65e38b5602b3470b88229227d92a2db4_2481x3508.png) |
| 4           | **Buttons / joystick / mutual exclusion:** P/M/L1/L2 have distinct active actions; app and companion cannot control together.                                | [OEM p. 4](https://doc-cdn.unitree.com/static/2024/6/5/b53ad192ddb943c4a1f73286234c28b1_2481x3508.png) |
| 5           | **Wearing / follow sequence / exits:** Wear on the right while standing to the robot left, use slow/fast modes only after training and know the exits.       | [OEM p. 5](https://doc-cdn.unitree.com/static/2024/6/5/e342ab90811c4193b3b3f731d8e517d4_2481x3508.png) |
| 6           | **Following precautions:** Maintain line of sight and clearance, check wearing geometry and avoid treating tracking as a safety system.                      | [OEM p. 6](https://doc-cdn.unitree.com/static/2024/6/5/e71f1fb7ff9246a89c8cf53f12b1cdc4_2481x3508.png) |

### Go2 Handheld Remote V2.3: complete source-page index <a href="#go2-handheld-remote-v23-complete-source-page-index" id="go2-handheld-remote-v23-complete-source-page-index"></a>

Original Unitree source: [Go2 Handheld Remote V2.3](https://marketing.unitree.com/article/en/Go2/Handheld_Remote_Control.html). Page links open the OEM originals; summaries below are original engineering interpretation, not a transcript.

| Source page | Section and engineering use                                                                                                                                   | Original                                                                                                  |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| 1           | **Cover / version:** Identify V2.3 as a two-revision handheld guide.                                                                                          | [OEM p. 1](https://doc-cdn.unitree.com/static/2025/12/22/ae008aa5a69d46ac999d09537edd62c3_2482x3509.png)  |
| 2           | **R3 transition / anatomy:** Either R1 or R3 may ship; physical revision controls which instructions apply.                                                   | [OEM p. 2](https://doc-cdn.unitree.com/static/2025/12/22/0685c1e8163844f18e1c47e8d88e591e_2481x3509.png)  |
| 3           | **R3 labels / ratings / stick storage:** Different battery/current figures require R3-specific identification; fit removable sticks before use.               | [OEM p. 3](https://doc-cdn.unitree.com/static/2025/12/22/6e5a22294baa47418f78cdb9f1149a24_2481x3509.png)  |
| 4           | **R3 stick fitting / calibration / power:** Keep sticks untouched until calibration starts, then apply with F3; this is not joint calibration.                | [OEM p. 4](https://doc-cdn.unitree.com/static/2025/12/22/64caf961a7be422dbeeb647b0a55ff13_2481x3509.png)  |
| 5           | **R3 feedback settings:** Triple F3 chooses sound/vibration; triple F1 toggles feedback and F1-held shutdown saves it.                                        | [OEM p. 5](https://doc-cdn.unitree.com/static/2025/12/22/39d9612083634643839374a280c0b081_2481x3509.png)  |
| 6           | **R3 charging / binding:** Use off-state USB charging and the actual controller code; full LEDs on is R3-specific.                                            | [OEM p. 6](https://doc-cdn.unitree.com/static/2025/12/22/c3e3f73f439842ed8972580c28803702_2482x3509.png)  |
| 7           | **R3 data-link / standing controls:** Check right-side DL link and distinguish body/posture axes before any control.                                          | [OEM p. 7](https://doc-cdn.unitree.com/static/2025/12/22/e13626fc12904d79a361ed2036cb69a4_2482x3509.png)  |
| 8           | **R3 walking controls:** Translation and turning axes differ from standing behavior; walls degrade the radio link.                                            | [OEM p. 8](https://doc-cdn.unitree.com/static/2025/12/22/d245e9b316104e7298c7bf7475101e72_2481x3509.png)  |
| 9           | **R3 mode / stop / reference axes:** L2+B is damping, L2+A low-down; advanced motions have Air restrictions and are outside first result.                     | [OEM p. 9](https://doc-cdn.unitree.com/static/2025/12/22/dd0126329a594c34a36b936565dffe17_2481x3509.png)  |
| 10          | **R3 actions / avoidance / feedback / idle-off:** Special actions and avoidance switches are active controls; disconnected idle-off is not a fault by itself. | [OEM p. 10](https://doc-cdn.unitree.com/static/2025/12/22/410b6772e4e14c13be178d0526f750fc_2481x3509.png) |
| 11          | **R1 anatomy / ratings:** Older R1 has its own 5 V / 2 A and 2500 mAh entries; do not confuse with the R1 humanoid.                                           | [OEM p. 11](https://doc-cdn.unitree.com/static/2025/12/22/13292dcca3cd4a01a557a1e5de1e4aa3_2481x3509.png) |
| 12          | **R1 calibration / power / charging:** R1 full-charge LEDs go off; follow the illustrated calibration and charging instructions for that revision.            | [OEM p. 12](https://doc-cdn.unitree.com/static/2025/12/22/11e3b8bc35ac4e84963c920a5296e042_2482x3509.png) |
| 13          | **R1 binding / standing controls:** Confirm left-side link signals and actual remote ID before posture control.                                               | [OEM p. 13](https://doc-cdn.unitree.com/static/2025/12/22/5dadabfcf6f54a5ca1c9b87c6ef67ac0_2482x3509.png) |
| 14          | **R1 walking axes:** Use the older controller drawing for translation, pitch and yaw; do not infer axes from case shape.                                      | [OEM p. 14](https://doc-cdn.unitree.com/static/2025/12/22/9c28f59a0def481296e804fa60310c88_2481x3508.png) |
| 15          | **R1 mode / stop table:** Preserve source mode/stop mapping and Air exclusions; no active control is run here.                                                | [OEM p. 15](https://doc-cdn.unitree.com/static/2025/12/22/2060616189a8404599e134e0570ad6f6_2481x3508.png) |
| 16          | **R1 action / avoidance table:** Use original mapping for advanced gestures and switches only after training and configuration checks.                        | [OEM p. 16](https://doc-cdn.unitree.com/static/2025/12/22/27e7d854aaaa4f85adf0bb53f2ff2671_2481x3508.png) |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

* Unitree, [Go2 product comparison](https://www.unitree.com/go2/), reviewed 24 November 2026; current public page has no hardware revision identifier.
* Unitree, [Go2 User Manual V4.3](https://marketing.unitree.com/article/en/Go2/User_Manual.html), 17 source images. Visual checks covered environment limits, edition symbols/indicators and startup placement/timing; all pages were read with OCR assistance.
* Unitree, [Go2 Battery and Charger V1.1](https://marketing.unitree.com/article/en/Go2/Battery_Charger.html), 10 source images, revision history dated 27 May 2026. Critical table and power-button entries were checked against originals.
* Unitree, [Handheld V2.3](https://marketing.unitree.com/article/en/Go2/Handheld_Remote_Control.html), 16 source images; [Companion V1.0](https://marketing.unitree.com/article/en/Go2/Companion_Remote_Control.html), 6 source images. Both revisions are distinct from the robot edition and each other.
* Unitree Robotics, [Python SDK pinned commit](https://github.com/unitreerobotics/unitree_sdk2_python/tree/814556d15970dd2ecf1c9984e845ca02ab07e206), actual source/IDL/dependencies/license reviewed; firmware pairing remains unverified.
* OpenELAB catalog and observed product search results, 24 November 2026: Air, controller accessory and Pro matched; EDU and X unlisted in the audited catalog. Store identity does not override exact OEM hardware limits.

**Documentation reviewed:** accessible official material, with all 49 manual page images indexed. Material gaps remain in delivered LiDAR/compute identity, the charger discrepancy, button-timing revisions, EDU commissioning and firmware recovery. Those affected procedures remain draft and gated as stated alongside them.

**Software execution:** no SDK installation, vendor build, ROS or DDS/hardware connection run. Original example syntax/static or mock checks, if recorded, test only local structure and control flow.

**Hardware validation:** not run. No battery charging, power-on, motion, calibration, flashing, recovery or physical verification was performed. GitBook content and navigation were not read or modified in this task; these are local canonical-guide drafts.

**Related documentation:** [Unitree robot and development directory](./).
