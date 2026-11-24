---
description: >-
  Explore Unitree R1-7a motor frames, calibration, web console and
  teleoperation, with source-specific payload, J4 and supply conflicts clearly
  identified.
---

# Unitree R1-7a Arm: Serial SDK, Web Console and Teleoperation Guide

{% hint style="info" %}
**Unitree R1-7a robotic arm — unlisted manufacturer reference.** No exact OpenELAB product URL or SKU was found in the reviewed 67-product Unitree catalog. This is the standalone seven-axis arm, not an R1 humanoid edition or the R1-A application platform. The associated repositories use `r1-7a_sdk` and `R1-7A`; retain those exact identifiers. [Official product](https://www.unitree.com/R1-7a/).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

R1-7a is a desktop seven-joint serial manipulator for research, teaching and dual-arm development. Unitree describes a 5.5 kg body made from metal and engineering plastic, a replaceable end effector and position/force interfaces. The portal's user guide describes the delivered arm as a bare mechanism **without a control board**; the SDK drives its joints through a serial motor bus. Do not apply a humanoid SDK2/DDS arm-control recipe to this interface. [Product](https://www.unitree.com/R1-7a/), [arm user guide](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm)

Three software products serve different tasks: the low-level `r1-7a_sdk`, a separately distributed `r1_7a_web` graphical console, and the `R1-7A` PICO/XRoboToolkit teleoperation framework. The internally routed gripper has a branch-specific SDK procedure. Hardware, side, calibration, end effector and software branch must be identified together; a similar name is not enough to choose a command or joint order.

## Applications <a href="#applications" id="applications"></a>

The documented uses include kinematics/force-control teaching, manipulation algorithms, coordinated arms, maintenance simulations and household-service research. Seven revolute joints offer alternative configurations around obstacles; this does not establish automatic collision avoidance. The teleoperation framework explicitly provides **no dual-arm collision planning**. Keep the workspace and both arms' falling paths clear, including grippers and attached cameras. [Application descriptions](https://support.unitree.com/home/en/R1-7a/about%20_R1-A7), [teleoperation README](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/README_en.md)

An effective first engineering result is a reproducible calibration-file audit, followed by a separately supervised identity/feedback session. Data-collection work should retain measured state separately from command targets and distinguish arm radians from gripper slide coordinates. No load or speed figure in this guide is a permission to commission an unverified controller.

## Specifications <a href="#specifications" id="specifications"></a>

Official sources disagree on payload, J4 direction and supply wording. Keep those differences visible rather than merging them into a new specification. [Product table](https://www.unitree.com/R1-7a/), [portal overview](https://support.unitree.com/home/en/R1-7a/about%20_R1-A7), [user guide](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm), [deployment](https://support.unitree.com/home/en/R1-7a/Usage_and%20SDK%20Deployment)

| Parameter                   | Source-specific value / consequence                                                                                                                                         |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arm joints                  | 7 revolute joints, J1 base through J7 flange; gripper separate                                                                                                              |
| Mass                        | 5.5 kg, product and portal overview                                                                                                                                         |
| Payload                     | Product: 3–5 kg; portal overview: **2 kg**. No reconciled load envelope obtained; confirm the exact unit/tool/load case before lifting                                      |
| Reach                       | 650 mm **with dexterous hand**, not bare-flange reach                                                                                                                       |
| Supply                      | Product/overview: 24–60 V; deployment: **24/48 V, 15 A**; mounting diagram/packing entry: **12–60 V**. The lower 12 V label is not adopted as verified operation below 24 V |
| External interface label    | XT30 + CAN485; standard wiring article identifies XT30 2+2 carrying power and RS485                                                                                         |
| Host                        | Ubuntu; SDK README Ubuntu 20.04+ for x86\_64/aarch64                                                                                                                        |
| Published control features  | Position and force; force feedback/collision detection claimed, not independently validated                                                                                 |
| Product maximum joint speed | >180°/s for every joint; not a commissioned limit                                                                                                                           |

| Joint | Motor / reduction ratio | Product angular range | Portal user-guide angular range |
| ----- | ----------------------- | --------------------- | ------------------------------- |
| J1    | 6010 / 32               | −156° to +156°        | Same                            |
| J2    | 6010 / 32               | 0° to 180°            | Same                            |
| J3    | 6014 / 12.666           | −20° to 200°          | Same                            |
| J4    | 6014 / 12.666           | **0° to 180°**        | **−180° to 0°**                 |
| J5    | 6014 / 12.666           | ±130°                 | Same                            |
| J6    | 5010 / 16               | ±30°                  | Same                            |
| J7    | 5010 / 16               | ±90°                  | Same                            |

The product page also has a **“Torque Range”** row containing `−2.7227…2.7227`, `0…3.1416`, `−0.3491…3.491`, `0…3.1416`, `−2.269…2.269`, `−0.524…0.524`, `−1.571…1.571`. The field has no unit and resembles converted angular ranges. **It is not a usable N·m rating, and this guide does not silently relabel it as radians.** Obtain a corrected manufacturer torque table. The portal motor protocol's representable rotor-side torque is a separate encoding bound, not a load rating. [Ambiguous product field](https://www.unitree.com/R1-7a/), [motor protocol](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm)

The manufacturer warns that low reduction can give limited positional stiffness and oscillation unless the control algorithm is appropriate. Repeatability, continuous torque, a complete duty-cycle/load envelope and ingress protection are not numerically established by the read sources.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Mounting and package scope <a href="#mounting-and-package-scope" id="mounting-and-package-scope"></a>

The user guide describes M8 attachment to a support bracket or at least two C-clamps at a table edge. The dedicated mounting article recommends a user-supplied base plate with at least four M8 screws, up to twelve; it lists one arm, two G-clamps, a USB-to-485 adapter cable and a power adapter described as DC12–60 V. This is not confirmation of the operating voltage or included base plate for every order. Design fixtures for dynamic reactions as well as arm mass, and confirm fastener lengths/torques from the delivered drawing. [Mounting article](https://support.unitree.com/home/en/R1-7a/Mounting_Method)

| Official drawing / resource                                                                                                 | Use and limit                                                                                                 |
| --------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Base screw pattern](https://doc-cdn.unitree.com/static/2026/9/18/6aaf415f5d0a43f59bd3306633ab90c0_773x646.png)             | Manufacturer mounting geometry; verify revision before machining                                              |
| [Desktop mounting](https://doc-cdn.unitree.com/static/2026/9/18/e5549e17e70e4dbab3a9f2f71f3a0a9d_448x497.png)               | Clamp arrangement reference                                                                                   |
| [XT30 2+2 / adapter diagram](https://doc-cdn.unitree.com/static/2026/9/18/46da8ca5030e491583578c89e3916940_848x310.png)     | Arm to power/485 breakout and USB-to-485 PC path; diagram's 12–60 V label conflicts with product supply range |
| [Deployment wiring photograph](https://doc-cdn.unitree.com/static/2026/9/21/1b03c6658c344f5896bd352f681e2f19_2304x1585.png) | Actual adapter arrangement illustration, not a connector pinout                                               |

Images © Unitree Robotics. The XT30 2+2 connection carries positive/negative supply and RS485 wires. Use the revision-matched adapter/harness; no authoritative pin-by-pin orientation/polarity drawing was established. Supply and J4/payload conflicts must be resolved before live commissioning. Serial/USB communication does not supply arm power.

The teleoperation reference uses a four-channel FTDI USB-to-RS485 adapter with `if00` right gripper, `if01` right arm, `if02` left gripper, `if03` left arm. Each arm has its own serial port/calibration; grippers have independent services. Stable `by-id` paths identify the actual adapter; README example serial numbers are not universal device identities. Do not place two program owners on the same bus. [Teleoperation wiring and configuration](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/README_en.md), [detailed guide](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/detail.md)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Low-level SDK and motor protocol <a href="#low-level-sdk-and-motor-protocol" id="low-level-sdk-and-motor-protocol"></a>

The reviewed `r1-7a_sdk` commit is `92f32514c6a9089c580ddf331eeb26075fcc5609`, with VERSION **0.1.0**, dated 17 September 2026 in that file. README requirements are Ubuntu 20.04+, x86\_64/aarch64, GCC 9.4, CMake ≥3.10, Make and pthread; architecture-specific prebuilt `motor_controller` libraries are supplied. `build.sh` chooses the appropriate library. These are source-reviewed requirements, not a build performed here. The repository LICENSE is BSD 3-Clause; separately supplied libraries/assets still need their own license checks. [README](https://github.com/unitreerobotics/r1-7a_sdk/blob/92f32514c6a9089c580ddf331eeb26075fcc5609/README_en.md), [VERSION](https://github.com/unitreerobotics/r1-7a_sdk/blob/92f32514c6a9089c580ddf331eeb26075fcc5609/VERSION), [LICENSE](https://github.com/unitreerobotics/r1-7a_sdk/blob/92f32514c6a9089c580ddf331eeb26075fcc5609/LICENSE)

The portal defines a common IM6014 protocol for 6010/6014/5010 motors: **RS485, 6 Mbps, 8 data bits, no parity, one stop bit**, periodic 20-byte commands followed by 26-byte responses. There is no response without a command; ID15 broadcasts without replies, IDs0–14 are addressed. Multi-byte values are little-endian. The SDK normally assigns seven joints IDs0–6. A fresh-feedback session therefore cannot be assumed to be a passive serial sniffer. [Protocol](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm), [SDK header](https://github.com/unitreerobotics/r1-7a_sdk/blob/92f32514c6a9089c580ddf331eeb26075fcc5609/include/arm_motor_bus.h)

| Command offsets  | Contents                                                      |
| ---------------- | ------------------------------------------------------------- |
| 0–1              | `FE EE` header                                                |
| 2                | ID in low four bits; three status bits; timeout flag in bit 7 |
| 3                | Reserved                                                      |
| 4–5 / 6–7 / 8–11 | Signed torque / speed / position targets                      |
| 12–13 / 14–15    | Position and velocity stiffness                               |
| 16–19            | CRC32-MPEG2                                                   |

| Response offsets  | Contents                                                                          |
| ----------------- | --------------------------------------------------------------------------------- |
| 0–1 / 2           | `FC EE` header / ID, status, timeout                                              |
| 3 / 4 / 5         | Signed driver temperature °C / winding temperature °C / bus voltage at 2 counts/V |
| 6–7 / 8–9 / 10–13 | Rotor torque / velocity / position                                                |
| 14–17             | Motor error bitmap; an error causes motor stop                                    |
| 18–19             | Low 13 reserved bits; upper three warning bits                                    |
| 20–21 / 22–25     | Reserved / CRC                                                                    |

CRC32-MPEG2 uses polynomial `0x04C11DB7` and initial `0xFFFFFFFF`. Commands cover bytes0–15 including the header; responses cover bytes2–21 excluding the header. The reference routine consumes32-bit words (four for commands, five for responses), so a generic byte-oriented CRC package must not be assumed wire-compatible without independent reference vectors. No packet writer or vendor CRC was executed here. [CRC definition](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm)

Status 0 is stop, 1 is FOC; the timeout-enabled mode stops after more than one second without commands. The response timeout flag is distinct from host reply-timeout counters. CRC uses polynomial `0x04C11DB7`, initial `0xFFFFFFFF`; the command covers its first 16 bytes **including header**, the response covers 20 bytes **excluding header**. The source's reference implementation consumes four/five little-endian 32-bit words respectively; do not substitute an arbitrary byte-stream CRC merely because its name matches. [Wire definitions and reference CRC](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm)

All protocol fields are **rotor-side**. Torque uses 2560 counts/N·m, velocity `64/(2π)` counts/(rad/s), position `32768/(2π)` counts/rad, stiffness 12800 counts/(N·m/rad), damping 51200 counts/(N·m·s/rad). Apply the per-joint reduction: output torque = rotor torque × ratio; output position/velocity = rotor / ratio; output stiffness/damping = rotor × ratio². The signed torque encoding reaches about 12.8 N·m rotor-side; that is not an approved operating torque. [Scaling](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm)

`ArmMotorBus` converts public URDF-frame commands/states at the bus edge. Calibration rows are `joint dir scale offset`, with angle `dir × scale × raw_motor_angle + offset`. Its `states()`/`feedbackReady()` provide snapshots/received flags; require all seven joints, not default zero arrays. `step()` transmits commands; `stop`, clear and reset mutate device state. **`close()` and the destructor send mode-0 stop packets**, so a program that only calls `states()` can still change force output on exit. [Implementation](https://github.com/unitreerobotics/r1-7a_sdk/blob/92f32514c6a9089c580ddf331eeb26075fcc5609/src/arm_motor_bus.cpp)

The source README defaults to `/dev/ttyUSB3`, 6000000 baud, right side unless `-l/--left` is selected; relative calibration paths depend on working directory. These defaults are examples, not identification of your adapter. `test_arm_lowlevel` FOC/home/goto/zero/stop/clear/reset and the motion demo all send commands. Homing to seven URDF zeros is distinct from the teleoperation home pose. The older portal demo documents a 50 Hz command default and up to 700 Hz support, while the current README's motion demo defaults to 100 Hz; neither supersedes the separate console's 200 Hz loop. [SDK README](https://github.com/unitreerobotics/r1-7a_sdk/blob/92f32514c6a9089c580ddf331eeb26075fcc5609/README_en.md), [portal deployment](https://support.unitree.com/home/en/R1-7a/Usage_and%20SDK%20Deployment)

### Internally routed gripper and version-specific calibration <a href="#internally-routed-gripper-and-version-specific-calibration" id="internally-routed-gripper-and-version-specific-calibration"></a>

The dedicated gripper article requires branch **`r1-dex-1`**, with an eight-value `--goto-hold` example. It is a branch-specific end-effector workflow, not proof that the reviewed seven-joint `main` executable accepts those flags or an eighth joint target. Obtain that branch's matching README and release commit before using it. [Internal-routing article](https://support.unitree.com/home/en/R1-7a/Gripper%20with%20Internal%20Cable%20Routing)

The portal deployment/console text describes supplied calibration as common across R1-7a units and normally not requiring recalibration. The newer teleoperation documentation requires a file matching the physical side and encoder reference, warns against double sign reversal, and does not generate physical zero during setup. Preserve the supplied calibration, exact side and hash; do not automatically recapture after USB reconnection, copy arbitrary offsets across arms or force an out-of-limit pose through by wrapping angles. [Deployment calibration statement](https://support.unitree.com/home/en/R1-7a/Usage_and%20SDK%20Deployment), [teleoperation calibration](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/detail.md)

### Graphical console: persistent targets and HTTP contract <a href="#graphical-console-persistent-targets-and-http-contract" id="graphical-console-persistent-targets-and-http-contract"></a>

The portal documents `r1_7a_web_console-1.0.0`: Ubuntu22.04/Debian12+ and glibc≥2.34 for the prebuilt x86\_64 application, fixed 6 Mbps USB-to-485, current browser, no Python/Node/ROS runtime requirement. The package includes executable, `web` assets, calibration and communication libraries with relative RUNPATH. Ubuntu20.04 or aarch64 requires recompilation with matching SDK libraries/system g++; none was performed here. [Console manual](https://support.unitree.com/home/en/R1-7a/graphical%20console)

`run_web.sh --sim` is the documented simulation start; `--tty <actual-device>` auto-connects to hardware and is **not** equivalent to a passive status query. Default HTTP address is `127.0.0.1:8420`. Other options are `--port` for HTTP port, `--listen` for IP, `--web-dir`, `--calib`, `--rate` (default200) and `--no-browser`. Stop the simulation server before changing to real hardware; otherwise the same HTTP port remains occupied. A failed serial connection leaves the server alive and disconnected, allowing the path to be corrected through the UI. Preserve loopback binding; exposing it to a LAN exposes motor-control endpoints. [Startup/options](https://support.unitree.com/home/en/R1-7a/graphical%20console)

The console's targets **do not expire automatically**. Closing the page does not cancel a pending trajectory. Sliders send one absolute target on release; jog changes one joint by ±1.5°. Default speed is 20°/s; the dialog accepts 0.5–90°/s, but **0 means URDF full speed**, not stop. It clamps to a 0.5° soft-limit margin and uses a 6 rad/s² acceleration limit. The quoted URDF speeds are172°/s for J1–J4 and229°/s for J5–J7; these are console model values, distinct from the product's >180°/s statement. [Console controls and safety](https://support.unitree.com/home/en/R1-7a/graphical%20console)

The 3D view is a frontend FK display, with TCP centimeters; rotate/zoom/reset affect observation only. Status includes enabled/feedback counts, gains, servo state, following error, fault text and timestamped logs. Hold aligns targets to measured angles and zeros velocity. Emergency stop/Esc stops targets and disables, and disconnect also releases force; **the console says the arm has no brake and will sink**. Re-enable is explicit. Frozen readings after disconnect are old measurements. Software stop is not a certified independent hardware stop. [Interface behavior](https://support.unitree.com/home/en/R1-7a/graphical%20console)

| HTTP method / endpoint           | Contract and effect                                                                                                                                      |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| GET `/api/state`                 | Read server snapshot; inspect `connected`, `sim`, `port`, `q_deg`, `dq`, `tau`, `foc`, `feedback`, `fault`, `limits_deg`, `servo`, `speed_dps`, `frozen` |
| POST `/api/connect`              | `{"sim":true}` or `{"port":"actual-device"}`; omitted `sim` selects real hardware                                                                        |
| POST `/api/disconnect`           | Stops stream, disables/closes bus, retains frozen readings                                                                                               |
| POST `/api/target`               | `q_deg` array of seven or `joint`/`value`; absolute degrees                                                                                              |
| POST `/api/jog`                  | Zero-indexed `joint` with degree `delta`                                                                                                                 |
| POST `/api/speed`                | `dps` and `accel`; zero requests full speed                                                                                                              |
| POST `/api/hold` / `/api/enable` | Replace targets with measured hold / re-enable FOC                                                                                                       |
| POST `/api/reset` / `/api/estop` | Clear faults / stop stream and disable                                                                                                                   |

All endpoints are the portal's console contract, not a protocol implemented or tested by this guide. Joint index0 is J1; target angles are degrees, unlike low-level SDK radians. A read-only GET against an already supervised server can observe state; starting or connecting that server remains active. [HTTP API](https://support.unitree.com/home/en/R1-7a/graphical%20console)

### PICO teleoperation and data development <a href="#pico-teleoperation-and-data-development" id="pico-teleoperation-and-data-development"></a>

The separate `R1-7A` framework was read at `e2faf3ec17f589db2139c51b020592a4a05f836b`: Ubuntu22.04 x86\_64, PICO/XRoboToolkit PC service/client, optional RealSense/V4L2 cameras and independent Dex1 services. Its setup pins dependencies/patches and builds native bridges; setup does not establish physical calibration. SDK2 dependencies serve gripper DDS integration, not a substitute arm transport. The repository currently has no root LICENSE; dependencies retain their licenses. [README](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/README_en.md), [submodules](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/.gitmodules)

Select exactly one of right/left/dual; `--record` creates recording/camera work, while pure teleoperation does not. Real motion requires `--motion-mode`, startup checks and `MOVE`; default startup goes to home `[0,1.2,0,-1.2,0,0,0]` rad, not the SDK's all-zero home. Grip holds relative-pose tracking; trigger closes the selected gripper; right A returns home, left X starts/saves recording, right B pauses/resumes recording/tracking. Ctrl+C stops/exits but does not remove the need for support. Stale XR updates beyond250 ms trigger stop/hold and re-anchoring after recovery; a connected service with frozen/zero timestamps is not usable tracking. [Controls and stale-input behavior](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/detail.md)

Recorded MCAP vectors are eight values for one side or sixteen for right arm/gripper then left arm/gripper. Control targets/feedback/timing are in `/r1arm/control_sample`; observations/images in `/whole_body/frame`. Gripper slide values are not motor radians. Preserve `control_side` and `record_segment`; do not bridge pause segments as continuous motion. Camera timestamps are receipt times, not guaranteed exposure times, and dual serial transactions are not hardware synchronization. Target rates90 Hz control/30 Hz images are requests, not measured performance; timing reports separate loop, SDK completion, preparation, I/O and recording overhead. [Data and timing](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/detail.md)

Replay without motion mode checks data; `--preview-only` shows observations/actions without serial or DDS. Real replay can approach the first frame and execute motion; it needs matching side, ports, calibration and gripper services. Simulation/mock XR does not validate real wiring, gravity, feedback or calibration. Camera conflicts, wrong Conda/bridge ABI, stale shell variables and default model-side transforms must be resolved before adding recording load. [Replay/simulation/troubleshooting](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/detail.md)

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: audit calibration without opening a bus <a href="#first-result-audit-calibration-without-opening-a-bus" id="first-result-audit-calibration-without-opening-a-bus"></a>

1. Obtain the **supplied, side-specific calibration file** and retain its source/version and physical arm identity. Do not overwrite the delivered file.
2. Save the following original standard-library program as `check_calibration.py`. Run `python3 check_calibration.py /absolute/path/calibration.txt` against a copy.

```python
"""Original offline calibration-file audit; does not certify physical zero."""
import hashlib
import json
import math
from pathlib import Path
import sys


def check(path):
    data = Path(path).read_bytes()
    rows = {}
    for line in data.decode().splitlines():
        text = line.split("#", 1)[0].strip()
        if not text:
            continue
        fields = text.split()
        if len(fields) != 4:
            raise ValueError("expected joint dir scale offset")
        joint = int(fields[0])
        direction, scale, offset = map(float, fields[1:])
        if joint in rows or joint not in range(7):
            raise ValueError("duplicate or out-of-range joint index")
        if not all(math.isfinite(v) for v in (direction, scale, offset)) or direction not in (-1, 1) or scale <= 0:
            raise ValueError("invalid direction, scale or offset")
        rows[joint] = (direction, scale, offset)
    if set(rows) != set(range(7)):
        raise ValueError("need exactly seven calibration rows")
    return {"rows": 7, "sha256": hashlib.sha256(data).hexdigest(),
            "q_at_raw_zero_rad": [rows[i][2] for i in range(7)],
            "meaning": "file structure only; confirm side, physical reference and encoder state"}


if __name__ == "__main__":
    print(json.dumps(check(sys.argv[1]), indent=2))
```

Expected checkpoint: exactly seven rows, a SHA-256, and seven offsets shown as the transformed angle at raw zero. Duplicated/missing indices, invalid signs/scales and non-finite offsets fail. Distinct left/right files should retain distinct hashes; matching this syntax does **not** certify the physical side, zero pose, encoder state, gear conversion or safe limits. The stricter offline validation is an integration policy, not a clone of the vendor loader.

### Documented live stages, not executed here <a href="#documented-live-stages-not-executed-here" id="documented-live-stages-not-executed-here"></a>

Before any power or motion, resolve payload/J4/supply conflicts, exact harness polarity and delivered controller/SDK/branch. Mount and support the arm, clear the swept/falling envelope, establish exclusive serial ownership and an independently accessible stopping arrangement. Keep the supplied calibration and confirmed encoder reference. A fresh status session requires command/reply traffic; bus closure sends stop and can release support.

The portal console recommends learning its UI in simulation first, then stopping that server before real connection. Confirm real/sim through **all three**: startup banner, page badge, and `/api/state` (`sim=false` with actual serial path versus `sim=true`/`port=sim`). Seven feedback channels and seven enabled channels mean different things; an enabled count is not a safe-status badge. The portal's supervised first movement uses no payload, low posture, 5°/s and one jog at a time; this is a later commissioning exercise, not this guide's offline checkpoint. Teaching-style jogging waits between joints and records only stationary poses. [Console workflow](https://support.unitree.com/home/en/R1-7a/graphical%20console)

For shutdown, the console manual uses hold/confirm stationary, support before disconnect/disable, then end the server and power down. Killing the process or merely closing the browser is not a controlled cancellation policy. Do not proceed with live control until exact hardware/revision conflicts are resolved.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**No feedback but error code appears zero.** With no returned frame there may be no valid error to inspect. Check supply, harness, adapter recognition, correct stable path, role/side, permissions, baud and sole ownership first. The protocol replies only after commands. Do not use reset or recalibration as device discovery. `to=1` is motor timeout; mode0 stop and mode1 FOC have distinct meanings. [Deployment](https://support.unitree.com/home/en/R1-7a/Usage_and%20SDK%20Deployment), [protocol](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm)

**J4 sign, payload or supply disagree.** Stop the integration decision and retain the two source versions listed above. Do not mirror a target, reinterpret the torque row or use the lowest diagram voltage without manufacturer confirmation. The independent calibration transforms and left-model transforms must not both flip the same axis. [Calibration discussion](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/detail.md)

**Console page blank or port busy.** Confirm its `web` assets and one server instance; the simulation and real server both default8420. A responsive `/api/state` with a blank model points toward browser/assets such as `web/meshes.bin`. A prebuilt `GLIBC_2.34` failure needs a matching host or documented source rebuild, not a different robot binary. A failed serial open leaves the server alive; correct the path/permissions and reconnect through the page. [Console FAQ](https://support.unitree.com/home/en/R1-7a/graphical%20console)

**The arm moves after closing a page.** Console targets persist until reached, overwritten, held or stopped. Page closure is not a deadman switch. Enter zero in the speed field only if full model speed is intended; zero is not a stop command. Esc/disconnect releases torque and can drop the arm. Plan support and a proper physical stopping procedure first. [Console target lifetime](https://support.unitree.com/home/en/R1-7a/graphical%20console)

**FOC cannot be entered or faults recur.** Preserve actual feedback and the triggering condition. The portal suggests stop then controlled power restart if FOC remains unavailable, but the arm must be supported before stop/power loss. Clear/reset operations transmit state-changing packets; recurring electrical/thermal/encoder problems need diagnosis rather than repeated resets. Current SDK cleanup sends mode0. [Deployment fault handling](https://support.unitree.com/home/en/R1-7a/Usage_and%20SDK%20Deployment), [bus implementation](https://github.com/unitreerobotics/r1-7a_sdk/blob/92f32514c6a9089c580ddf331eeb26075fcc5609/src/arm_motor_bus.cpp)

**Teleoperation has no tracking or bad recordings.** Check continuous XR timestamps/validity, intended controller side, loaded `.env`/bridge/calibration, separate gripper services and DDS side/network, then camera ownership. A file path marked Accessible is not evidence of motor response. Recorded slide units, actual state and action targets must stay distinct; pause boundaries are not motion continuity. Do not relax feedback/limit checks for throughput. [Detailed troubleshooting](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/detail.md)

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                   | Model / purpose                                                              |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------- |
| [Product](https://www.unitree.com/R1-7a/), [portal user/protocol guide](https://support.unitree.com/home/en/R1-7a/R1%20Robotic%20Arm), [overview](https://support.unitree.com/home/en/R1-7a/about%20_R1-A7)                                                                | Hardware selection; source conflicts retained                                |
| [Mounting](https://support.unitree.com/home/en/R1-7a/Mounting_Method), [deployment](https://support.unitree.com/home/en/R1-7a/Usage_and%20SDK%20Deployment)                                                                                                                | Mechanical connections and low-level workflow                                |
| [Internal-routing gripper](https://support.unitree.com/home/en/R1-7a/Gripper%20with%20Internal%20Cable%20Routing)                                                                                                                                                          | `r1-dex-1` branch; not the reviewed main SDK                                 |
| [Graphical console manual](https://support.unitree.com/home/en/R1-7a/graphical%20console), [console archive](https://oss-global-cdn.unitree.com/static/fd1e418e66eb409e9a33907bfc01615b.zip)                                                                               | Documented1.0.0 web application; archive not downloaded or executed          |
| [SDK/model download article](https://support.unitree.com/home/en/R1-7a/get_SDK), [simplified STEP archive](https://oss-global-cdn.unitree.com/static/564832cf9c644bab9d7f06a7268c1b75.zip)                                                                                 | Default end geometry; replace with actual end-effector model                 |
| [Pinned low-level SDK](https://github.com/unitreerobotics/r1-7a_sdk/blob/92f32514c6a9089c580ddf331eeb26075fcc5609/README_en.md), [URDF directory](https://github.com/unitreerobotics/r1-7a_sdk/tree/92f32514c6a9089c580ddf331eeb26075fcc5609/urdf)                         | Code, calibration examples, vendored communication dependencies and geometry |
| [PICO teleoperation framework](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/README_en.md), [detailed configuration/data guide](https://github.com/unitreerobotics/R1-7A/blob/e2faf3ec17f589db2139c51b020592a4a05f836b/detail.md) | Separate higher-level single/dual-arm workflow                               |

The portal “example” record is empty; it supplies no further code or test evidence. Direct archives are observed resources, not checked releases or permission to execute. No standalone R1-7a firmware update image or complete corrected torque/payload table was verified.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026: current product HTML, all eight actual English R1-7a portal records (seven substantive, one empty), pinned SDK/control/teleoperation files, and selected connection figures. Portal titles retain the inconsistent spelling “R1-A7”; that title alone does not reidentify the arm as an R1-A platform. A heading-by-heading coverage ledger records source URLs, hashes and update times.

Executed only the original offline calibration audit and its malformed-input checks. No vendor code or downloaded console was run; no SDK build/import, ROS launch, serial connection, hardware test or firmware change occurred. The guide is a manufacturer reference with bounded offline results; unresolved supply/payload/J4/torque and delivered-version questions block commissioning approval.

**Related documentation:** [Unitree model and development directory](./).
