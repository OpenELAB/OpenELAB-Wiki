---
description: >-
  Review the distinct B2-W wheel-leg map, English manual revisions, charging and
  stop boundaries, SDK2 control hazards and an offline wheel-aware state
  checkpoint.
---

# Unitree B2-W: wheel mapping, operating limits and first state checks

{% hint style="info" %}
**Manufacturer model reference: Unitree B2-W.** No exact B2-W OpenELAB listing or SKU was verified in the observed catalog. **SKU:** unverified · **Store URL:** unverified. This is a separate wheel-legged model reference, not additional coverage claimed by the listed [B2](unitree-b2.md). [Official Unitree B2-W product page](https://www.unitree.com/b2-w/).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

Unitree B2-W combines twelve leg joints with four wheel joints in a wheel-legged industrial platform. The wheels change its state map, commands, contact geometry, stopping behavior and maintenance requirements. This guide uses the B2-W User Manual V1.1 and B2-W Remote Control Manual V1.0, together with B2-W-specific SDK2 examples. B2 battery instructions and B2 remote mode tables are not silently substituted for B2-W documentation. [B2-W manufacturer description](https://www.unitree.com/b2-w/), [B2-W joint constants](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/b2w/low_level/unitree_legged_const.py)

The source supports a GO-family state interface, but not a validated firmware range or a complete stop/charging specification for a delivered unit. The first result below is a wheel-aware offline mock, with no robot, SDK, ROS or DDS activation. The [B2](unitree-b2.md), [B2-Ex](unitree-b2-ex.md) and [B1](unitree-b1.md) references retain their own scopes.

## Applications <a href="#applications" id="applications"></a>

B2-W's manufacturer describes wheel-leg travel over industrial terrain, stairs and uneven surfaces, and inspection payload integration. Its quoted range targets do not establish the endurance of a particular sensor payload, slope, tire condition or mission. Select and validate rolling versus stepping operation against the actual controller, traction and site conditions before route planning.

A useful initial development task is identifying the four wheel-state slots separately from leg angles. Another is recording the delivered computers, perception stack and interface module against the order. Neither task requires releasing control mode or issuing a wheel-speed command. Standard B2-W has no B2-Ex certification implication. [B2-W product functions and conditions](https://www.unitree.com/b2-w/)

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter                  | B2-W source value and conditions                                                                                                                                                                 |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Standing / prone size      | Approximately 1098 × 550 × 758 mm / 950 × 550 × 450 mm, length × width × height.                                                                                                                 |
| Mass                       | Approximately 85 kg including battery. Do not use B2's 60 kg handling assumption.                                                                                                                |
| Payload                    | Product page: standing 120 kg, walking >40 kg. Payload position, restraint and configured mode remain per-unit engineering inputs.                                                               |
| Battery description        | Product page: >2 kWh, 58 V; User Manual V1.1 describes up to 45000 mAh. No B2-W-specific rated/maximum cell-voltage or charger-output table was established here.                                |
| Endurance                  | Approximately 30 km unloaded and maximum 25 km with 40 kg load. The product-page footnote qualifies the loaded-range/speed figures as special configurations; real speed limits apply.           |
| Travel speed               | Advertised maximum 15 km/h, configuration-limited in practice. This is not a commissioning or first-check speed.                                                                                 |
| Wheels                     | Product page: diameter 225 mm, maximum wheel angular speed 50 rad/s, maximum wheel torque 40 N·m. The two maxima are not a simultaneous continuous-duty rating or a tire-pressure specification. |
| Terrain capability         | Product page: continuous 20–25 cm stairs, 40 cm forward step capability and >45° slope. Manual operating guidance is materially more restrictive; see below.                                     |
| Body environment / ingress | −20 to +55 °C; IP67 advertised. Do not operate in lightning/tornado conditions; dry mating surfaces and the correct installed battery matter. No independent test report was read.               |
| Compute                    | Product page: Core i5 platform computer, Core i7 user-development computer; optional i7/Orin NX arrangements up to three devices, configuration-dependent.                                       |
| Expansion                  | User Manual lists Ethernet ×4, USB 3.0 ×4, 12 V ×4, 5 V ×1, 24 V ×4 and BAT ×1. Connector assignment, direction and allowed current require the exact interface module specification.            |

Sources: [official parameter table and footnotes](https://www.unitree.com/b2-w/), [B2-W User Manual V1.1, source images 6–12 and 20–23](https://marketing.unitree.com/article/en/B2-W/User_Manual.html).

### Keep the operating envelope separate <a href="#keep-the-operating-envelope-separate" id="keep-the-operating-envelope-separate"></a>

User Manual V1.1 directs ordinary operation on open, flat ground with steps **below 20 cm** and slopes **below 20°**, unlike the product-page maximum demonstrations. Its precautions state obstacle crossing ≤20 cm and say not to cross obstacles higher than 25 cm. They also warn about lateral drift near/above 45° and instability when turning on steep slopes. None of these passages validates a route at the product-page maxima. Use the delivered firmware's approved mode-specific envelope and reduce speed for uneven ground. [User Manual, source images 12 and 20–21](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

The manual requires at least 3 m separation from obstacles/crowds/water in its operating-environment section. For stand-up recovery, its earlier safety text says a 2 m diameter, later precautions say a 3 m diameter, while the separate remote manual states a **3 m radius**. These are conflicting published clearances, not a single consistent specification. Recovery is excluded from this first-result workflow; confirm a definitive procedure, and do not shrink a radius requirement to a diameter. [User Manual, images 5, 12 and 20](https://marketing.unitree.com/article/en/B2-W/User_Manual.html), [Remote Manual, images 8–9 and 13–14](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Wheels, body, perception and interface identification <a href="#wheels-body-perception-and-interface-identification" id="wheels-body-perception-and-interface-identification"></a>

Use the original B2-W parts/wheel illustrations in [User Manual images 6–7](https://marketing.unitree.com/article/en/B2-W/User_Manual.html), and the [B2-W interface-module drawing, source image 9](https://doc-cdn.unitree.com/static/2025/7/29/e974f27f40ee4032a099788d712bd8dc_2482x3509.png). The drawing has wheel-motor/leg-bus labels and an emergency-stop label, but it is not a verified mating pinout or proof of stop coverage in every controller mode. Do not wire a homemade stop circuit from OCR text, expose internal RS-485 wiring or connect a load to BAT without the delivered electrical drawing.

Before a later commissioning session identify the tire assemblies, body/pack/charger labels, remote R3 or R1 revision, computer allocation and accessory interface module. Check tires for wear/damage and loose wheel components, plus cameras/LiDAR, cooling, fasteners and battery latch. The sources do not give a verified tire pressure, wheel-fastener torque or permitted rail-mount moment; obtain those before mechanically altering the platform. [User Manual, images 7, 9 and 22–23](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

### Power and charging boundary <a href="#power-and-charging-boundary" id="power-and-charging-boundary"></a>

B2-W's own user manual describes removing the switched-off battery for plug-in charging, matching the delivered charger's AC nameplate, connecting AC first and then the battery, and cooling a hot pack to room temperature before charging. The documented AC input example is 100–240 V, 50/60 Hz. This does **not** establish the charger's DC output or an interchangeable B2 battery/charger model. The separate B2 Battery Manual is not applied here as a B2-W electrical specification. [B2-W User Manual, image 10](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

The user manual requires correct keyed battery orientation and a fully latched installation; never force a pack into place. It describes a prone, horizontal startup posture with the belly support on flat ground, legs retracted and no limb trapped by the body. The power-button sequence is a short press then a hold over three seconds, followed by roughly two minutes before automatic standing. This is documented context for a commissioned operator, not an action to perform for the offline check. Automatic standing and wheeled contact create movement hazards even without an application command. [User Manual, images 13–14](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

### Remote, stop behavior and upkeep <a href="#remote-stop-behavior-and-upkeep" id="remote-stop-behavior-and-upkeep"></a>

B2-W's Remote Manual V1.0 covers R3 and older R1 hardware, with a December 2024 upgrade notice. R3's table lists 780 mAh, 5 V/700 mA and about 5 h; R1 lists 2500 mAh, 5 V/2 A and about 4.5 h. Both state >100 m only in open conditions. R3 charging guidance recommends a 5 V/2 A USB adapter; the documented R1/R3 full-charge LED indications differ, so use the correct hardware section. [Remote Manual, images 2–7 and 10–12](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)

For the delivered official controller, the B2-W table identifies L2 held + B clicked as damping, L2 held + A clicked as lock-standing/lying, Y as General Mode and L2/R2 held + START clicked as Special Mode. It also lists recovery and a special-configuration rotating-jump action. These mode/action entries differ from B2 Remote V2.1 and are **not** setup tests. The [original B2-W command table, image 8](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html) is the versioned source; verify actual firmware before relying on any button mapping.

The user manual says high-level API and remote commands can both act on the robot, and remote commands cease to work during low-level development. Damping/lying controls are not proof of an independent wheel brake or safety-rated stop. User shutdown guidance first brings the robot to a stable lying state, then uses the battery button; abrupt power loss while standing can collapse it. A failed remote requires a unit-specific recovery plan, not an improvised lifting/power-off maneuver. [User Manual, images 4 and 18–20](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

The app workflow uses Unitree Explore with a Unitree-supplied enterprise account, Bluetooth-assisted binding, and AP or Wi-Fi connection. R3 link indication is the right DL light; older R1 guidance describes the left transmission indicators. A link light is not proof that the correct control mode or independent stop is armed. Store the machine dry/cool, inspect tires and cooling, and clean only with power off and soft materials. The user manual says retain the installed pack during body cleaning, but remove it for long storage; do not treat that as permission to wet the loose pack. Joint calibration is not a routine troubleshooting step. [User Manual, images 15–17 and 19–23](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Exact source map, not a universal firmware pairing <a href="#exact-source-map-not-a-universal-firmware-pairing" id="exact-source-map-not-a-universal-firmware-pairing"></a>

The reviewed C++ SDK2 commit is `b7fec6020eb93d4c059a6edf19905e12a75a8d3d`; Python SDK2 is `814556d15970dd2ecf1c9984e845ca02ab07e206`. C++ sources report project 2.0.0, vendor Ubuntu 20.04/GCC 9.4.0 prebuild for aarch64/x86\_64 and C++17. Python setup declares package 1.0.1, Python ≥3.8 and CycloneDDS ==0.10.2 plus NumPy/OpenCV. These identify source/environment baselines, not the robot's image. [C++ baseline](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/README.md), [Python requirements](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/setup.py)

B2-W-specific sources use `unitree_go` low state/command on DDS `rt/lowstate` / `rt/lowcmd`. Twenty slots are transport capacity. The Python constants define this exact map:

| Group                           | DDS indices in the inspected B2-W example                     |
| ------------------------------- | ------------------------------------------------------------- |
| Front right hip/thigh/calf      | 0, 1, 2                                                       |
| Front left hip/thigh/calf       | 3, 4, 5                                                       |
| Rear right hip/thigh/calf       | 6, 7, 8                                                       |
| Rear left hip/thigh/calf        | 9, 10, 11                                                     |
| Front right / front left wheels | 12 / 13                                                       |
| Rear right / rear left wheels   | 14 / 15                                                       |
| Remaining GO slots              | 16–19; no active B2-W actuator assignment is established here |

Source: [pinned B2-W `unitree_legged_const.py`](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/b2w/low_level/unitree_legged_const.py). This is the example's contract; it is not a joint-sign/zero/calibration certificate for a particular machine.

The [C++ B2-W stand example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/b2w/b2w_stand_example.cpp) releases the motion mode, creates a low-command publisher and later commands wheel slots 12–15 at positive and negative angular velocities. It initializes 0x01 motor mode; the inspected B2 legged example uses 0x0A. The Python counterpart also requests StandDown/ReleaseMode during initialization. None is a passive “read sensor” program, despite sensor-printing text. Do not reuse their gains, sentinels, mode byte, CRC assumptions or wheel commands for a first check.

The [B2-W sport client example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/b2w/b2w_sport_client.cpp) uses the B2 `SportClient` (`sport`, API 1.0.0.1). Move/StopMove/SwitchGait/RecoveryStand are control requests; its movement-duration comments do not prove a hardware stopping guarantee. Confirm firmware, gait/rolling mode, wheel sign, traction, braking and one command owner before any later control work.

See the shared [SDK2 state guide](unitree-sdk2-state-development.md) and [ROS 2 integration guide](unitree-ros2-integration.md) for environment-specific details. A future subscriber must use the matched GO type, actual dedicated Ethernet interface and confirmed robot domain (0 in the reviewed examples). Keep simulation on a separately matched domain/interface, such as domain 1/lo. No interface activation, build or simulator is needed below.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Offline first result: preserve wheel slots separately <a href="#offline-first-result-preserve-wheel-slots-separately" id="offline-first-result-preserve-wheel-slots-separately"></a>

1. Record the exact B2-W and remote/pack/charger revisions. Stop if only a B2 or B2-Ex commissioning document is available.
2. Keep power/data connections unused. Copy this original standard-library Python 3 code, which inspects synthetic dictionaries only.
3. Run locally and compare its explicit wheel map with the pinned constants above. Do not interpret synthetic zeros as observed robot position or velocity.

```python
import math

WHEELS = {"FR": 12, "FL": 13, "RR": 14, "RL": 15}
def inspect_b2w(samples):
    previous = None
    changes = 0
    for sample in samples:
        motors = sample["motor_state"]
        if len(motors) != 20:
            raise ValueError("GO transport has 20 slots, not 16")
        for index in range(16):
            if not all(math.isfinite(float(motors[index][f])) for f in ("q", "dq")):
                raise ValueError("Non-finite leg/wheel state")
        tick = int(sample["tick"])
        changes += previous is not None and tick != previous
        previous = tick
    if changes < 1:
        raise ValueError("No observed tick transition")
    return {"model": "B2-W", "transport_slots": 20, "leg_slots": 12,
            "wheel_slots": WHEELS, "data_origin": "original mock"}

mock_motors = [{"q": 0.0, "dq": 0.0} for _ in range(20)]
print(inspect_b2w([{"tick": 1, "motor_state": mock_motors},
                   {"tick": 2, "motor_state": mock_motors}]))
```

**Expected result:** B2-W, 20 transport slots, 12 leg slots and FR/FL/RR/RL wheel indices 12/13/14/15. A 16-slot array, repeated tick or nonfinite wheel sample must fail. Only original mock parsing is verified; DDS compatibility, wheel direction, calibration and stop behavior are not.

For a later precommissioned subscriber-only session, capture `rt/lowstate` with the exact GO binding, show leg and wheel slots separately, require observed tick changes and finite samples, preserve firmware/domain/interface/source identity and close the reader on timeout or uncertainty. Do not call StandDown, ReleaseMode, SwitchGait or a stand demo to “enable” the read. No live activation command is given while firmware, charging and independent stop evidence remain unresolved.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Why does a leg-only decoder miss part of B2-W?** Its twelve-leg-slot loop omits wheels 12–15, while the GO record still has twenty slots. Use the map from the B2-W constants; do not reduce the serialized record to sixteen fields or label slots 16–19 as wheels.

**Can a B2 stand program test the wheels?** No. The B2-W example deliberately issues wheel velocity commands and releases control mode. The B2 and B2-W example motor modes also differ. A state-only check needs a subscriber with no action client/publisher.

**Why does the product page say 45°/40 cm but the manual restrict operation?** Maximum demonstrated capability and operator instructions describe different conditions. Use the current delivered operating envelope, not a product headline. This guide does not validate a route, jump or incline.

**Can the remote always stop a custom program?** The manual explicitly excludes remote control during low-level development. Link indication and damping buttons are not an independently validated wheel-braking system. Resolve stop behavior before hardware use.

**Can the B2 battery manual supply the missing B2-W charging values?** Not without explicit pack/charger compatibility evidence. The B2-W user manual supports its own removal/charging sequence, but no matched B2-W DC-output/current table was verified here. Read the delivered labels and obtain the matching accessory manual.

**App cannot bind or data does not arrive.** Separate account/Bluetooth/AP or Wi-Fi setup from SDK DDS. Confirm enterprise account, matching remote ID, correct app permissions and network path. For DDS check model type, exact interface/domain and source identity without changing controller modes. Do not treat a factory calibration action as network recovery.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                    | Scope                                                                                                                                                                                                               |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Official B2-W page](https://www.unitree.com/b2-w/)                                                                                                                         | Dedicated wheel-legged specification table and configuration footnotes.                                                                                                                                             |
| [English B2-W User Manual](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)                                                                                  | V1.1, revision 29 July 2025; 23 images. Safety, parts/tire figure, functions/interfaces, charging, preparation/startup/app/remote, shutdown/packing, fault handling, precautions, maintenance and revision history. |
| [English B2-W Remote Control Manual](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)                                                                     | V1.0, 18 April 2025; 14 images. R3/R1 hardware, calibration/feedback, charging/binding, operation/command tables, clearances and revision history.                                                                  |
| [Exact wheel constants](https://github.com/unitreerobotics/unitree_sdk2_python/blob/814556d15970dd2ecf1c9984e845ca02ab07e206/example/b2w/low_level/unitree_legged_const.py) | Model-specific leg/wheel index evidence; read as text only.                                                                                                                                                         |
| [Wheel-command example](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/example/b2w/b2w_stand_example.cpp)                    | Control-path audit resource, not first-result execution.                                                                                                                                                            |

No B2-W exact store SKU, dedicated pack electrical manual, tire-pressure/fastener specification, mating connector/current-rating table, complete independent stop design or firmware bounds were established. B2-Ex certifications and B2 charger values are not transferred.

### Manual chapter index <a href="#manual-chapter-index" id="manual-chapter-index"></a>

Page ranges below are source-image numbers, not guessed printed-page offsets. Each link opens the original model-specific manual.

| Manual / source images                                                                        | Engineering content                                                                         |
| --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [B2-W-user images 1](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)          | Cover / identity; interpreted in Product overview.                                          |
| [B2-W-user images 2](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)          | Contents; interpreted in Downloads and technical documents.                                 |
| [B2-W-user images 3–4](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)        | Disclaimer / intended-use and service boundaries; interpreted in References and validation. |
| [B2-W-user images 4–5](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)        | Safety instructions; interpreted in Hardware and connections.                               |
| [B2-W-user images 6–7](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)        | Introduction and parts; interpreted in Product overview.                                    |
| [B2-W-user images 7–8](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)        | Function highlights; interpreted in Applications.                                           |
| [B2-W-user images 9](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)          | Interface drawing; interpreted in Hardware and connections.                                 |
| [B2-W-user images 10–11](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Battery/remote charging; interpreted in Hardware and connections.                           |
| [B2-W-user images 12–13](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Environment/unpacking/preflight; interpreted in Hardware and connections.                   |
| [B2-W-user images 14](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)         | Startup and automatic standing; interpreted in Hardware and connections.                    |
| [B2-W-user images 15–16](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Enterprise app binding / networking; interpreted in Software and development resources.     |
| [B2-W-user images 17](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)         | Remote operation; interpreted in Hardware and connections.                                  |
| [B2-W-user images 18](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)         | Shutdown / packing; interpreted in Hardware and connections.                                |
| [B2-W-user images 19–20](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Abnormalities and calibration limits; interpreted in Troubleshooting and FAQs.              |
| [B2-W-user images 20–21](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Operating precautions; interpreted in Specifications.                                       |
| [B2-W-user images 22–23](https://marketing.unitree.com/article/en/B2-W/User_Manual.html)      | Cleaning/storage/inspection/pack maintenance; interpreted in Hardware and connections.      |
| [B2-W-remote images 1](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)     | Cover / controller revision; interpreted in Product overview.                               |
| [B2-W-remote images 2–3](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)   | Upgrade notice / R3 hardware and specification; interpreted in Hardware and connections.    |
| [B2-W-remote images 3–4](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)   | R3 joystick fitting / calibration / power; interpreted in Hardware and connections.         |
| [B2-W-remote images 5](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)     | R3 feedback controls; interpreted in Downloads and technical documents.                     |
| [B2-W-remote images 6–7](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)   | R3 charging and binding; interpreted in Hardware and connections.                           |
| [B2-W-remote images 8–9](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)   | R3 command table / clearances; interpreted in Hardware and connections.                     |
| [B2-W-remote images 10](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)    | R1 hardware and specifications; interpreted in Hardware and connections.                    |
| [B2-W-remote images 11](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)    | R1 calibration/power/charging; interpreted in Hardware and connections.                     |
| [B2-W-remote images 12](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html)    | R1 binding and operation; interpreted in Hardware and connections.                          |
| [B2-W-remote images 13–14](https://marketing.unitree.com/article/en/B2-W/Remote_Control.html) | R1 commands / clearances / revision history; interpreted in Hardware and connections.       |

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026. Complete OCR sequences for the 23-image B2-W User Manual V1.1 and 14-image Remote Manual V1.0 were read; the remote command/clearance image was visually checked. User Manual image 3 corresponds to printed page 2; citations above consistently identify source-image sequence pages. The original interface drawing is linked for inspection rather than converted into a guessed pinout.

**Validation:** original inline Python exercised with synthetic good/bad capacities, repeated ticks and invalid leg/wheel values; source hashes and manual page/chapter coverage checked. **Not run:** Unitree imports/examples, SDK install/build, ROS/DDS/network discovery, simulator, hardware, wheel motion, calibration or flashing. Root SDK2 licenses are BSD-3-Clause; manual/figure and third-party rights remain separate. Hardware readiness stays draft. Parent browser-derived portal articles can be added when actually read; no all-portal coverage claim is made.

**Related documentation:** [Unitree model and development directory](./).
