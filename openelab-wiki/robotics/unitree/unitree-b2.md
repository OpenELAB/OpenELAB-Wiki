---
description: >-
  Integrate the legged Unitree B2 using model-specific manuals, battery and
  remote revision checks, conditional SDK2 state support and an offline first
  result.
---

# Unitree B2: power, remote revisions and read-only development

{% hint style="info" %}
[**View Unitree B2 on OpenELAB**](https://openelab.io/products/unitree-b2-robotic-dog-high)

**Model:** Unitree B2, legged configuration · **SKU:** `Unitree-B2` · **Listing option:** Default Title. Confirm delivered battery, computers, remote revision and accessories against the order. This page owns the B2 model scope; [B2-W](unitree-b2-w.md), [B2-Ex](unitree-b2-ex.md) and [B1](unitree-b1.md) have separate references.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree B2 is an industrial quadruped with a battery-powered legged chassis, front/rear perception devices and user-development computing. This guide connects the official B2 specifications with the English User Manual V1.0, Remote Control Manual V2.1 and Battery and Charger Manual V1.0. It distinguishes operating instructions from demonstration maxima, and offers an offline state-decoding checkpoint before any robot connection. The current product page advertises optional wheeled feet; that does not make a purchased B2 interchangeable with the separately documented B2-W. [Official B2 product page](https://www.unitree.com/b2/)

SDK2 sources contain a B2-specific GO-message example, but they do not establish a firmware range for the delivered robot. Charging-voltage discrepancies and changed remote-control instructions also require per-unit confirmation. Hardware commissioning remains a draft; no robot, SDK, ROS or DDS program was run for this guide.

## Applications <a href="#applications" id="applications"></a>

B2's published applications include power inspection, industrial inspection and emergency-response research. The documented Ethernet, USB and accessory power interfaces support integration planning for cameras, networking and inspection payloads; the exact payload, connector rating and software configuration still need engineering confirmation. A LiDAR/camera-equipped chassis does not by itself supply a validated autonomous mission, obstacle-free route or explosion-protected installation. B2-Ex's markings do not apply to this B2.

For development, start by separating state observation from locomotion requests and whole-body commands. A state reader can help confirm a matched transport and decoder; it does not verify joint calibration, payload stability, collision protection or emergency-stop performance. [B2 interface and application descriptions](https://www.unitree.com/b2/)

## Specifications <a href="#specifications" id="specifications"></a>

Values below are manufacturer-reported, not measurements made here. Dimensions are length × width × height, and quoted endurance is conditional on load and terrain.

| Parameter             | B2 source value and conditions                                                                                                                                                                                               |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Standing / prone size | Approximately 1098 × 450 × 645 mm / 880 × 460 × 330 mm. The original drawings remain the authority for mechanical integration.                                                                                               |
| Mass                  | Approximately 60 kg including battery.                                                                                                                                                                                       |
| Payload               | Product page: standing ≥120 kg; continuous walking >40 kg. These are different operating states, not interchangeable payload allowances.                                                                                     |
| Endurance             | Product page: unloaded walking >5 h and >20 km; 20 kg load >4 h and >15 km; general battery-life range 4–6 h. Speed, posture, body height, terrain and payload affect the result.                                            |
| Battery advertising   | Product page: 45 Ah, 2250 Wh, “58 V.” Dedicated battery manual gives different rated/charge figures; see the power boundary below.                                                                                           |
| Speed / torque        | Product page: >6 m/s and about 360 N·m maximum joint torque. Its speed footnote requires special configurations and says practical speed limits apply. Neither number is a commissioning target.                             |
| Steps / slopes        | Product page advertises continuous 20–25 cm stairs, 40 cm forward obstacle capability and >45° climbing. User Manual V1.0 instead gives mode-specific operating restrictions; use the distinction below.                     |
| Body environment      | −20 to +55 °C in product/user sources, with weather and surface restrictions. This does not resolve the narrower battery-use wording.                                                                                        |
| Ingress               | Product page/User Manual advertise IP67. Correctly fitted battery and dry mating surfaces matter; no independent IP report or immersion conditions were verified here.                                                       |
| Compute / sensors     | Standard page configuration: Core i5 for platform functions, Core i7 for user development; optional i7/Orin NX configurations, up to three devices. LiDAR ×1, depth cameras ×2 and optical cameras ×2 vary by configuration. |
| Interfaces            | Product page lists 1000M-Base-Ethernet ×4, USB 3.0 ×4, 12 V ×4, 5 V ×1, 24 V ×4 and BAT ×1. These counts do not supply pin polarity, permissible current or a mating-connector specification.                                |

Source: [B2 parameter table and footnotes](https://www.unitree.com/b2/), [User Manual V1.0, source-image pages 6–9 and 20–23](https://marketing.unitree.com/article/en/B2/User_Manual.html).

### Operating limits versus demonstrations <a href="#operating-limits-versus-demonstrations" id="operating-limits-versus-demonstrations"></a>

The User Manual's environment/precaution sections describe conventional control at steps below 20 cm and slopes below 20°, and AI control at steps below 25 cm, low-gear slopes below 45° and high-gear slopes below 30°. The later Remote Manual V2.1 deletes regular-motion-control instructions and adds Free Walk, so those older mode names cannot be assumed to describe current firmware. Its environmental table also prints “<40m” for obstacle surmounting; the original image confirms that problematic unit. Do not silently turn it into a validated 40 cm operating limit. Obtain the delivered controller's current operating envelope. [User Manual, images 12 and 20–21](https://marketing.unitree.com/article/en/B2/User_Manual.html), [Remote Manual, images 9 and 14](https://marketing.unitree.com/article/en/B2/Remote_Control.html)

The product-page jump headline (>1.6 m) and User Manual introduction/function text (0.5–1.2 m / maximum 1.2 m) also describe different published figures. No jump, recovery or maximum-speed action is part of this guide's first result.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Identify the delivered assembly before power <a href="#identify-the-delivered-assembly-before-power" id="identify-the-delivered-assembly-before-power"></a>

Use the original [B2 body/parts figure, source image 6](https://doc-cdn.unitree.com/static/2024/5/17/c5454bd3ffa7434ebd2bc722cd414e28_2481x3509.png) and [interface drawing, source image 9](https://doc-cdn.unitree.com/static/2024/5/28/7fd54ebde720499c801fd917c35c3a40_2481x3508.png). They identify the battery compartment, belly support, legs, perception devices and interface modules. Keep the original connector drawing available; do not reconstruct an electrical pinout from OCR labels or assume an Ethernet-shaped connector carries accessory power.

Record the body/pack/charger labels, remote R1 or R3 hardware, installed computers and accessory cable specifications. The manual requires correct keyed battery orientation, a fully engaged latch and no forcing of a partly inserted pack. For the documented startup posture, the belly support is flat on level ground with retracted legs and no limb trapped under the chassis. Startup is an actuation event: V1.0 describes automatic standing after roughly two minutes. Keep people clear and use a commissioned stop plan before any later power-on. [User Manual, images 12–14](https://marketing.unitree.com/article/en/B2/User_Manual.html)

### Battery and charger: unresolved numerical differences <a href="#battery-and-charger-unresolved-numerical-differences" id="battery-and-charger-unresolved-numerical-differences"></a>

| Read source                  | Exact printed value                                                               | Consequence                                                                                                                                     |
| ---------------------------- | --------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Product page                 | 45 Ah / 2250 Wh / 58 V                                                            | Commercial configuration description; not a charger setpoint.                                                                                   |
| Battery Manual V1.0, image 3 | Rated DC 50.4 V; limited charge DC 58.5 V; capacity line prints “45000mA, 2268Wh” | The capacity unit is printed inconsistently. Rated voltage differs in role from a charge limit.                                                 |
| Same manual, images 6–7      | OEM charger output 58.8 V, 10 A, 588 W; nominal charging time 3 h 20 min          | The 58.8 V output versus 58.5 V pack limit remains unresolved in this edition. Do not select/configure a substitute charger from these figures. |
| Same manual, image 11        | Battery-use ambient −5 to +55 °C                                                  | Do not assume the body's −20 °C claim authorizes this pack below −5 °C. Match the actual pack revision and cold-weather instructions.           |

Sources: [B2 battery/charger manual](https://marketing.unitree.com/article/en/B2/Battery_Charger.html), including original images 3 and 6 visually checked during this review. OEM pack/charger pairing and label confirmation are required before charging; this guide does not resolve the discrepancy by averaging values.

The B2 manual's plug-in charging sequence requires the pack off and removed, AC supplied to the official charger first, then connection to the pack; a hot pack must cool to room temperature. The battery manual recommends 5–40 °C charging conditions and dry, noncombustible surroundings under observation. Contact charging is a separate optional installation with exposed electrodes, polarity/orientation and its own inspection requirements. No charging pad approach or energization is a first check. “Quick change” does not establish hot swapping: the battery manual requires power off before insertion/removal. [Battery Manual, images 7–14](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)

### Remote control, stopping and maintenance <a href="#remote-control-stopping-and-maintenance" id="remote-control-stopping-and-maintenance"></a>

Remote Manual V2.1 covers both R3 and older R1 controllers. It describes R3 as 780 mAh, 5 V charging/700 mA specification and about 5 h operation; R1 is 2500 mAh, 5 V/2 A and about 4.5 h. Both quote >100 m only in an open environment. Do not confuse the remote called R1 with the humanoid robot family. The older user manual's USB-adapter and charge-indicator wording differs from the newer remote manual; identify the actual remote and use its matching section. [Remote Manual, images 2–7 and 10–12](https://marketing.unitree.com/article/en/B2/Remote_Control.html)

For the documented official control system, the current remote table names L2 held plus B clicked as damping and L2 held plus A clicked as lock-standing/lying. User Manual V1.0 describes L2+A twice, then battery-button shutdown only after lying. These are posture/power operations, not a proven independent emergency stop. The manuals say remote commands can compete with high-level API commands and cease to be effective during low-level development. Do not rely on remote damping as the sole stop during a custom low-level controller session. [Remote command table, images 8 and 13](https://marketing.unitree.com/article/en/B2/Remote_Control.html), [User Manual, images 4 and 18–20](https://marketing.unitree.com/article/en/B2/User_Manual.html)

The user manual states a 2 m operating separation; the later remote recovery warning specifies a **2 m radius**, while the older user recovery text uses a diameter. Preserve that difference and use the matching, stricter remote recovery exclusion when planning; this guide does not initiate recovery. Loss-of-remote forced shutdown is a collapse/lifting hazard, not a generic “press power to stop safely” instruction.

Before/after use inspect lenses, LiDAR clearance, fasteners, cooling, feet, battery shell/mating surfaces and remote centering. Cleaning is with power off and soft materials; the user manual says keep the battery installed during body cleaning, but remove it for long-term dry storage. The battery manual calls for periodic storage checks and recharge to 70% if below 30%, and storage below 40 °C; those values are not firmware settings. Joint recalibration is not routine fault recovery: the manual says contact Unitree before deciding it is necessary. [User Manual, images 19–23](https://marketing.unitree.com/article/en/B2/User_Manual.html)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

| Component        | Verified source scope                                                                                                      | Boundary                                                                                                  |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| SDK2 C++         | `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`; project 2.0.0; vendor prebuild Ubuntu 20.04, GCC 9.4.0, aarch64/x86\_64; C++17 | Architecture-specific core library is prebuilt. No build or firmware pairing was tested here.             |
| SDK2 Python      | `814556d15970dd2ecf1c9984e845ca02ab07e206`; package 1.0.1; Python ≥3.8; CycloneDDS runtime ==0.10.2, NumPy and OpenCV      | Generated IDL v0.11.0 banner is not a runtime upgrade instruction.                                        |
| B2 state         | Actual B2 example uses `unitree_go::msg::dds_::LowState_` on DDS `rt/lowstate`; 20 transport slots, leg map 0–11           | Array capacity does not make slots 12–19 active B2 leg joints.                                            |
| B2 sport service | `unitree::robot::b2::SportClient`; `sport`, API version 1.0.0.1                                                            | Source API version is not robot firmware. `Move`, `Damp`, `StandDown` and `StopMove` are action requests. |

Sources: [C++ README](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), [Python requirements](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py), [B2 leg map](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/b2/low_level/unitree_legged_const.py), [B2 sport API](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/robot/b2/sport/sport_api.hpp).

The [B2 stand example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/b2/b2_stand_example.cpp) is **not** a passive reader. It creates `rt/lowcmd`, releases the motion mode and publishes trajectories with example gains. It initializes motor mode 0x0A, whereas the reviewed B2-W example initializes 0x01; neither constant is a universal whole-family setting. Its sensor-printing text does not turn it into a safe connectivity test.

Use the shared [SDK2 state-development guide](unitree-sdk2-state-development.md) for environment preparation and the [ROS 2 integration guide](unitree-ros2-integration.md) for wrapper-specific domain/interface and message differences. For any later robot reader, confirm firmware, dedicated Ethernet interface, the actual domain (0 in cited real examples), one identified state source and an independently verified stop system. Simulation loopback/domain 1 remains separate. Do not disable a motion service just to obtain a state sample. Exact B2 firmware bounds remain unknown.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Offline first result: decode a B2-shaped mock without connecting <a href="#offline-first-result-decode-a-b2-shaped-mock-without-connecting" id="offline-first-result-decode-a-b2-shaped-mock-without-connecting"></a>

1. Keep the robot off and data cables unused. Gather its label/order record and the B2 manual revisions above; record any mismatch instead of applying a B2-W or B2-Ex procedure.
2. Copy this original Python 3 check. It uses standard-library math only and synthetic dictionaries. It imports no Unitree library and starts no discovery traffic.
3. Run it with a local Python 3 interpreter. Check the printed capacities and tick progress; the values are deliberately synthetic, not expected hardware measurements.

```python
import math

def inspect_b2(samples):
    previous = None
    changes = 0
    for sample in samples:
        motors = sample["motor_state"]
        if len(motors) != 20:
            raise ValueError("B2 GO schema requires 20 transport slots")
        for index in range(12):
            if not all(math.isfinite(float(motors[index][f])) for f in ("q", "dq")):
                raise ValueError("Non-finite leg state")
        tick = int(sample["tick"])
        changes += previous is not None and tick != previous
        previous = tick
    if changes < 1:
        raise ValueError("No observed tick transition")
    return {"model": "B2", "transport_slots": 20, "leg_slots": 12,
            "tick_changed": True, "data_origin": "original mock"}

mock_motors = [{"q": 0.0, "dq": 0.0} for _ in range(20)]
print(inspect_b2([{"tick": 1, "motor_state": mock_motors},
                  {"tick": 2, "motor_state": mock_motors}]))
```

**Expected result:** B2, 20 transport slots, 12 leg slots and `tick_changed: True`, explicitly labeled `original mock`. Repeated ticks, a 16-element transport array or nonfinite leg values must fail. This result tests original formatting logic only.

A later subscriber-only result requires a precommissioned robot and a confirmed native GO decoder. Capture only `rt/lowstate`; inspect actual schema, tick changes, finite joint/IMU values and source identity, then close the reader. No live command is supplied here because current pack/controller/firmware conditions are unresolved. An unseen sample, wrong type, stale tick or uncertain stop behavior ends the check. Power-on itself may stand the robot up; do not activate hardware to reproduce an offline example.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**No state arrives.** Verify the purchased development configuration, matched firmware and GO type first, then dedicated interface, domain and one intended source. State subscription requires no `ReleaseMode` or stand command. Domain 1/loopback simulation data must not be mistaken for robot domain 0 data.

**Battery/charger voltage labels differ.** Stop charger selection and compare actual pack/charger nameplates with the Battery Manual's 50.4/58.5/58.8 V entries. Keep the mismatch in the per-unit record and obtain a definitive pairing. Do not adjust a bench supply to a marketing “58 V” value.

**B2 does not stand after the manual's initialization period.** Treat this as failed startup. Recheck the documented unpowered posture, latch and environment before any later retry; the manual's two-minute example is not a controller watchdog. Do not repeatedly recalibrate joints or invoke recovery as a network diagnostic.

**Remote modes disagree with the old user manual.** Identify R3/R1 hardware and the V2.1 remote revision, which deletes regular-motion instructions and introduces Free Walk. Verify delivered firmware before using a button label. Low-level software can make remote commands ineffective.

**The body is IP67; can the loose pack be wet?** No such inference is supported. The battery manual forbids exposing the pack to liquids and conditions protection on correct installation; the user manual requires dry battery/mating surfaces. No immersion experiment or cleaning under power is authorized by this guide.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                    | Revision and purpose                                                                                                                                                                                                           |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [B2 product parameter table](https://www.unitree.com/b2/)                                                                                                   | Living manufacturer page; commercial capability conditions and interface counts.                                                                                                                                               |
| [English B2 User Manual](https://marketing.unitree.com/article/en/B2/User_Manual.html)                                                                      | V1.0; 23 source images. Disclaimer/safety, overview/parts, functions/interfaces, charging, preparation/startup/app/remote, shutdown/packing, abnormalities, precautions and maintenance.                                       |
| [English B2 Remote Control Manual](https://marketing.unitree.com/article/en/B2/Remote_Control.html)                                                         | V2.1, 18 April 2025 revision; 14 images, covering R3 and R1 hardware, calibration, charging, binding, command tables, environment and history.                                                                                 |
| [English B2 Battery and Charger Manual](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)                                                   | V1.0; 14 images, pack/charger specs, functions/indicators, plug-in/contact charging, protection, storage, maintenance and disposal.                                                                                            |
| [B2 app download](https://www.unitree.com/app/b2/)                                                                                                          | Manufacturer app distribution; no app installed or account action performed. Manuals describe Unitree Explore enterprise-account binding; an old remote page also says Unitree Go, so confirm the current enterprise workflow. |
| [B2 source-specific example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/b2/b2_stand_example.cpp) | Audit control hazards and GO message selection; not a first-run executable.                                                                                                                                                    |

Mechanical mounting loads/fastener torque, connector current/pin assignment, independent stop-circuit behavior, matched firmware images and a definitive battery/charger correction remain missing for the actual unit. No generic replacement diagram, reset sequence or firmware-update recipe is invented.

### Manual chapter index <a href="#manual-chapter-index" id="manual-chapter-index"></a>

Page ranges below are source-image numbers, not guessed printed-page offsets. Each link opens the original model-specific manual.

| Manual / source images                                                                      | Engineering content                                                                         |
| ------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [B2-user images 1](https://marketing.unitree.com/article/en/B2/User_Manual.html)            | Cover / identity; interpreted in Product overview.                                          |
| [B2-user images 2](https://marketing.unitree.com/article/en/B2/User_Manual.html)            | Contents; interpreted in Downloads and technical documents.                                 |
| [B2-user images 3–4](https://marketing.unitree.com/article/en/B2/User_Manual.html)          | Disclaimer / intended-use and service boundaries; interpreted in References and validation. |
| [B2-user images 4–5](https://marketing.unitree.com/article/en/B2/User_Manual.html)          | Safety instructions; interpreted in Hardware and connections.                               |
| [B2-user images 6–7](https://marketing.unitree.com/article/en/B2/User_Manual.html)          | Introduction and parts; interpreted in Product overview.                                    |
| [B2-user images 7–8](https://marketing.unitree.com/article/en/B2/User_Manual.html)          | Function highlights; interpreted in Applications.                                           |
| [B2-user images 9](https://marketing.unitree.com/article/en/B2/User_Manual.html)            | Interface drawing; interpreted in Hardware and connections.                                 |
| [B2-user images 10–11](https://marketing.unitree.com/article/en/B2/User_Manual.html)        | Battery/remote charging; interpreted in Hardware and connections.                           |
| [B2-user images 12–13](https://marketing.unitree.com/article/en/B2/User_Manual.html)        | Environment/unpacking/preflight; interpreted in Hardware and connections.                   |
| [B2-user images 14](https://marketing.unitree.com/article/en/B2/User_Manual.html)           | Startup and automatic standing; interpreted in Hardware and connections.                    |
| [B2-user images 15–16](https://marketing.unitree.com/article/en/B2/User_Manual.html)        | Enterprise app binding / networking; interpreted in Software and development resources.     |
| [B2-user images 17](https://marketing.unitree.com/article/en/B2/User_Manual.html)           | Remote operation; interpreted in Hardware and connections.                                  |
| [B2-user images 18](https://marketing.unitree.com/article/en/B2/User_Manual.html)           | Shutdown / packing; interpreted in Hardware and connections.                                |
| [B2-user images 19–20](https://marketing.unitree.com/article/en/B2/User_Manual.html)        | Abnormalities and calibration limits; interpreted in Troubleshooting and FAQs.              |
| [B2-user images 20–21](https://marketing.unitree.com/article/en/B2/User_Manual.html)        | Operating precautions; interpreted in Specifications.                                       |
| [B2-user images 22–23](https://marketing.unitree.com/article/en/B2/User_Manual.html)        | Cleaning/storage/inspection/pack maintenance; interpreted in Hardware and connections.      |
| [B2-remote images 1](https://marketing.unitree.com/article/en/B2/Remote_Control.html)       | Cover / controller revision; interpreted in Product overview.                               |
| [B2-remote images 2–3](https://marketing.unitree.com/article/en/B2/Remote_Control.html)     | Upgrade notice / R3 hardware and specification; interpreted in Hardware and connections.    |
| [B2-remote images 3–4](https://marketing.unitree.com/article/en/B2/Remote_Control.html)     | R3 joystick fitting / calibration / power; interpreted in Hardware and connections.         |
| [B2-remote images 5](https://marketing.unitree.com/article/en/B2/Remote_Control.html)       | R3 feedback controls; interpreted in Downloads and technical documents.                     |
| [B2-remote images 6–7](https://marketing.unitree.com/article/en/B2/Remote_Control.html)     | R3 charging and binding; interpreted in Hardware and connections.                           |
| [B2-remote images 8–9](https://marketing.unitree.com/article/en/B2/Remote_Control.html)     | R3 command table / clearances; interpreted in Hardware and connections.                     |
| [B2-remote images 10](https://marketing.unitree.com/article/en/B2/Remote_Control.html)      | R1 hardware and specifications; interpreted in Hardware and connections.                    |
| [B2-remote images 11](https://marketing.unitree.com/article/en/B2/Remote_Control.html)      | R1 calibration/power/charging; interpreted in Hardware and connections.                     |
| [B2-remote images 12](https://marketing.unitree.com/article/en/B2/Remote_Control.html)      | R1 binding and operation; interpreted in Hardware and connections.                          |
| [B2-remote images 13–14](https://marketing.unitree.com/article/en/B2/Remote_Control.html)   | R1 commands / clearances / revision history; interpreted in Hardware and connections.       |
| [B2-battery images 1](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)     | Cover / identity; interpreted in Product overview.                                          |
| [B2-battery images 2–3](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)   | Pack introduction and parts; interpreted in Hardware and connections.                       |
| [B2-battery images 3](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)     | Pack electrical specifications; interpreted in Specifications.                              |
| [B2-battery images 4](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)     | BMS functions / protections; interpreted in Hardware and connections.                       |
| [B2-battery images 5](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)     | Indicators and pack power; interpreted in Hardware and connections.                         |
| [B2-battery images 6–7](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)   | Plug-in / contact charger specifications; interpreted in Hardware and connections.          |
| [B2-battery images 8–9](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)   | Charging methods / orientation; interpreted in Hardware and connections.                    |
| [B2-battery images 10](https://marketing.unitree.com/article/en/B2/Battery_Charger.html)    | Charge / protection indicators; interpreted in Troubleshooting and FAQs.                    |
| [B2-battery images 11–12](https://marketing.unitree.com/article/en/B2/Battery_Charger.html) | Battery handling and use limits; interpreted in Hardware and connections.                   |
| [B2-battery images 12–13](https://marketing.unitree.com/article/en/B2/Battery_Charger.html) | Storage / transportation / maintenance / disposal; interpreted in Hardware and connections. |
| [B2-battery images 13–14](https://marketing.unitree.com/article/en/B2/Battery_Charger.html) | Charging-station precautions and maintenance; interpreted in Hardware and connections.      |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026 from the linked official pages and complete OCR sequences for the three B2 manuals. Original battery specification/charger images and the remote environmental table were visually checked where noted. Source-image numbers are used above: User Manual image 3 corresponds to printed page 2; keep the original page labels when checking a citation.

The root SDK2 C++ and Python sources carry BSD-3-Clause licenses; third-party middleware and manual/figure rights remain separate. The historical manuals are interpreted in original English prose here, not reproduced as a substitute licensed manual.

**Validation:** original offline Python snippet, invalid-capacity/repeated-tick/nonfinite mocks, source hashes, declared chapter coverage and Markdown structure checked locally. **Not run:** vendor imports/examples, installation/build, ROS/DDS/network discovery, hardware, motion, calibration or flashing. Exact firmware, stop behavior and electrical discrepancies keep hardware readiness in draft. Portal articles newly accessible through the parent's browser are separate evidence; no complete support-portal read is claimed here.

**Related documentation:** [Unitree model and development directory](./).
