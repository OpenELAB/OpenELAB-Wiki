---
description: >-
  Develop for the Unitree D2 arm with ArmEcho and Python SDK guidance, joint
  limits, feedback checks, control ownership, backup scope and bounded recovery.
---

# Unitree D2 Arm: ArmEcho, Python SDK and State Diagnostics

{% hint style="info" %}
**Unitree D2 — unlisted manufacturer reference.** No exact OpenELAB product URL or SKU was found in the reviewed 67-product Unitree catalog. The scope is the D2 seven-joint arm, its integrated controller, optional gripper, ArmEcho and D2 Python SDK. [Official product](https://www.unitree.com/D2/).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

The D2 is a 5.9 kg, seven-axis aluminum-alloy manipulator with an integrated real-time controller. Ethernet/UDP and onboard USB serial provide control and telemetry; an optional gripper occupies an additional channel. At power-on the controller starts in `DISABLED`, with no automatic arm motion. Its 180° elbow folding supports desktop and mobile configurations. [Product](https://www.unitree.com/D2/), [user documentation](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2)

**The joints have no mechanical brakes.** Disable, power loss and the SDK's normal cleanup can remove support, allowing the arm and payload to fall. The firmware has no hardware emergency-stop input: the ArmEcho emergency-stop control is a communication-dependent software disable. An installation needs an independently accessible physical stopping/power-isolation arrangement and a plan for gravity-driven movement. These software functions are not certified safety functions. [Safety and handling](https://support.unitree.com/home/en/D2_Arm_Development_Guide/about), [stop boundary](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2)

## Applications <a href="#applications" id="applications"></a>

D2 supports research manipulation, teaching, recorded trajectories and mobile manipulation. Its seven joints provide kinematic redundancy, but the arm has no automatic obstacle-detection or avoidance sensors. An SDK or geometric model alone does not make a path collision-free. The manufacturer illustrates A2/As2 integration with two explicit limits: **As2 supports one arm only; A2 must not perform high-speed movement with two arms fitted**. Base stability, battery capacity, mounts and reaction forces still require system-level assessment. [Applications and footnotes](https://www.unitree.com/D2/), [safety scope](https://support.unitree.com/home/en/D2_Arm_Development_Guide/about)

An appropriate development sequence is offline sample validation, verified state acquisition, model/device comparison, then a separate supervised motion experiment. Payload identification and fatigue examples are advanced procedures with substantial movement, not introductory diagnostics.

## Specifications <a href="#specifications" id="specifications"></a>

Values below are manufacturer claims, not measurements made for this guide. The portal safety instructions limit end payload to **3 kg**; the product page's separate 5 kg maximum-load illustration does not provide an operating envelope that authorizes exceeding that limit. [Product](https://www.unitree.com/D2/), [portal specifications](https://support.unitree.com/home/en/D2_Arm_Development_Guide/product), [payload safety limit](https://support.unitree.com/home/en/D2_Arm_Development_Guide/about)

| Item                               | D2 value / condition                                                                                 |
| ---------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Arm / gripper channels             | Seven rotary joints; optional gripper is SDK index 7, separate from J7                               |
| Mass; material                     | 5.9 kg; aluminum alloy                                                                               |
| Arm length; gripper working radius | 612 mm; 760 mm                                                                                       |
| Rated end payload                  | 3 kg                                                                                                 |
| Supply                             | 36–58 V battery-voltage range; verify approved supply and harness                                    |
| Power                              | 870 W peak; normal/typical ≤60 W                                                                     |
| Processor; published control rate  | Arm Cortex-M33, 32-bit; 500 Hz                                                                       |
| Interfaces                         | One XT30 power, one Type-C, one Ethernet, one RS485                                                  |
| Environment                        | −20 to +50 °C; IP42; stop outdoor work in rain and move to a dry place; no continuous-rain operation |
| Mechanical mounting options        | Upright, side, suspended, mobile; high-level gravity-supported software currently supports upright   |

| Joint / SDK index | Angular limit, degrees (radians) | Peak torque: product / portal | Published maximum speed |
| ----------------- | -------------------------------- | ----------------------------- | ----------------------- |
| J1 / 0            | ±156° (±2.7227)                  | 60 / 60 N·m                   | 18.7 rad/s              |
| J2 / 1            | 0–195° (0–3.4034)                | 60 / 60 N·m                   | 18.7 rad/s              |
| J3 / 2            | ±160° (±2.7925)                  | 60 / 60 N·m                   | 18.7 rad/s              |
| J4 / 3            | −180–0° (−3.1416–0)              | **30 / 33 N·m**               | 52.4 rad/s              |
| J5 / 4            | ±102° (±1.7802)                  | **30 / 33 N·m**               | 52.4 rad/s              |
| J6 / 5            | ±86.5° (±1.5097)                 | 10 / 10 N·m                   | 37.7 rad/s              |
| J7 / 6            | ±90° (±1.5708)                   | 10 / 10 N·m                   | 37.7 rad/s              |

J4/J5 peak torque is inconsistent across the two official sources; neither number establishes continuous torque or a software permission. Joint-module maximum speed is distinct from high-level `movej` limits. The repository URDF contains zero `effort` and `velocity` attributes, so it must not be used as an actuator-capacity table. [Portal table](https://support.unitree.com/home/en/D2_Arm_Development_Guide/product), [reviewed URDF](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/urdf/urdf/D2_URDF.urdf)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Mounting, tools and package inventory <a href="#mounting-tools-and-package-inventory" id="mounting-tools-and-package-inventory"></a>

The portal lists an assembled rectangular adapter base, actuator flange block, optional preinstalled Dex1-1 gripper, gripper RGB camera/bracket, five 4 mm and five 8 mm cable clips, two XT30 power cables (1 m male/female; 0.8 m single-female), 3 m RJ45 cable, 0.6 m RS485 cable, Type-C cable and two 4-inch G-clamps. Tool/fastener entries are T10, 4 mm and 2 mm wrenches; M3×12 countersunk camera screws ×2, M3×8 clip screws ×10, M3×12 Torx actuator screws ×6, and M5×12/M5×14 screws ×5 each. Check the delivered option list rather than assuming every pictured gripper/camera is included. [Packing list](https://support.unitree.com/home/en/D2_Arm_Development_Guide/product)

The standard base plate is 220 × 100 mm, with four slotted attachment positions for M5 screws or desktop clamping. Four M5 screws and four Ø5 mm locating pins join the arm to that plate; a custom mount can replace the plate using the documented four-screw interface. Size a mount for dynamic loading, not just 5.9 kg static mass. The tool flange has four Ø3.97 mm positioning bosses and four M3 mounting holes. [Mechanical details and drawings](https://support.unitree.com/home/en/D2_Arm_Development_Guide/product)

| Manufacturer drawing                                                                                                          | Use                                                          |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| [Overall dimensions](https://doc-cdn.unitree.com/static/2026/9/30/120d7b7404de4bd28c07afb224d097c3_4400x2670.png)             | Body and folded-envelope design                              |
| [Base attachment](https://doc-cdn.unitree.com/static/2026/9/29/a3cad76620af447588d4a5dc5359b433_4400x1533.png)                | Plate slots and direct-mount interface                       |
| [Flange](https://doc-cdn.unitree.com/static/2026/9/29/20719704c7ad4215b9b4dab04b5c5b14_4400x1226.png)                         | End-effector locating and screw pattern                      |
| [J7 flange/cable-cover assembly](https://doc-cdn.unitree.com/static/2026/11/5/6c890fce606a41c38aedbb2d6d4ca3f3_4400x2444.png) | Documented service access; cables remain attached internally |
| [Pinch zones](https://doc-cdn.unitree.com/static/2026/11/3/5598b294c2f840f0bb07fe77be2c3a35_4465x2836.png)                    | Shoulder, both elbow sides and wrist hazards                 |

Drawings © Unitree Robotics. The portal describes loosening two internal screws through the lower access holes before lifting the J7 driven-side/flange assembly; the cable cover has three screws. Do not pull the assembly away against its internal wires. Use the exact drawing and supplier service instructions; tightening torques and connector pin polarity were not established here. [Flange service boundaries](https://support.unitree.com/home/en/D2_Arm_Development_Guide/product)

For carrying, fold the arm and hold the base and lower upper-arm shell with both hands. Do not grasp the forearm or insert fingers into joint gaps. Power-off joints move freely and can pinch unexpectedly. Inspect connectors, harnesses, loosening, deformation and unusual noise before use. Keep people out of both the commanded workspace and possible falling envelope. Avoid corrosive/flammable environments, strong permanent magnetic fields, loose clothing and contact with hot joints. Store folded in a dry, ventilated location. The manufacturer's terms and operator restrictions remain in the [original safety document](https://support.unitree.com/home/en/D2_Arm_Development_Guide/about).

### Power and communications <a href="#power-and-communications" id="power-and-communications"></a>

Use a stable, protected 36–58 V supply with a verified XT30 harness; Type-C is a communications path, not an established substitute for arm power. Do not unplug power during operation. Plan a supported/folded shutdown posture before disabling, and budget battery energy and transient power for a mobile base. [Electrical and handling guidance](https://support.unitree.com/home/en/D2_Arm_Development_Guide/about)

The documented factory network is `192.168.123.2:2000`, mask `255.255.255.0`, gateway `192.168.123.1`, broadcast port `2001`; a host example is `192.168.123.100/24`. Delivered configuration may differ. USB paths should use `/dev/serial/by-id/…` or `by-path/…`; `ttyACM` numbers can change. Serial requires suitable host/container permissions and `pyserial>=3.5`. Both transports control the same device; **only UDP supports firmware upgrade**. [Connection instructions](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### Delivery, host application and ownership <a href="#delivery-host-application-and-ownership" id="delivery-host-application-and-ownership"></a>

The reviewed [D2-Arm delivery repository](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/README.md) is pinned at `8d505a8c511f2a8dd401bd4c410e37121b1bfd17`. Its files name SDK/ArmEcho 1.0.0. SDK wheels are `cp310-abi3`, Linux x86\_64/aarch64, covering 64-bit CPython 3.10–3.12 and glibc ≥2.17. Ubuntu 22.04 is recommended; WSL/VM environments still need working device/network access. Match architecture, verify the supplied SHA-256 and retain the package/version before installation. A virtual environment resolves externally managed Python installations; pip/venv must be present. No binary was downloaded or installed for this guide. The current repository lacks the README-linked `docs/D2 SDK API参考.md` and a root LICENSE; the now-readable [portal SDK manual](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK) supplies functional documentation, but licensing and exact delivered SDK/firmware compatibility still need confirmation.

ArmEcho is a prebuilt image requiring Docker Engine and Compose V2, with separate x86\_64/aarch64 archives and checksums; ARM64 selects `ARMECHO_ARCH=aarch64`. The documented deployment loads the checked image and starts `armecho-compose.yml`; a healthy container, usually after 10–30 s, serves `http://<host>:8000`. Port remapping such as `18000:8000` changes the browser address. The `d2arm-data` volume preserves connection settings; removing a container does not erase it, but deleting the volume does. Arm-resident teaching/configuration data is separate. [ArmEcho installation](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho), [compose file](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/armecho/armecho-compose.yml)

For multiple arms use one SDK `Arm` and one independent ArmEcho instance per device. Give each device a distinct IP; give each compose project a unique `name` and host port while retaining the image tag. A single NIC can serve `.2/.3/.4` on one subnet; multiple direct Ethernet NICs should use distinct subnets to avoid ambiguous routes. Keep bridge networking for multiple ArmEcho instances: host networking would collide on fixed port 8000. Each serial instance must map its own stable device path and `dialout` group. Explicit `ARM_TRANSPORT`/`ARM_SERIAL_*` environment values override page settings. [Multi-arm and serial deployment](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho)

Only one controller should own an arm. Multiple browsers connected to **one ArmEcho server** may observe together, but their commands are not isolated; appoint one operator. The SDK manual is internally inconsistent about whether a second client is rejected or seizes authority. Do not rely on either outcome: close other clients before connecting and verify `arm.robot.held`. Each SDK instance has receive and lease-renewal threads. [Session behavior](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK), [browser ownership](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho)

### State, sessions and enable semantics <a href="#state-sessions-and-enable-semantics" id="state-sessions-and-enable-semantics"></a>

`arm_sdk.connect(target, mounting="upright")` opens transport, handshakes and requests control authority; it **does not enable**, but may automatically apply a matching saved payload record while disabled. `arm.robot` exposes `held`, `link_ok`, `link_state`, `last_recovery`, `on_link_change()`, `device_info()`, `fault_reset()`, `reconnect()` and `close()`. Device info includes counts, limits, axes, geometry identity and `sw_version()` when reported. Link states include `CONNECTED`, `DISCONNECTED`, `RECOVERING`, `SESSION_LOST`. Reconnection after reboot does not authorize automatic enable or fault reset. Closing, including `with` exit, attempts disable/release; support the arm first. [SDK II–III](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

`arm.state.snapshot()` may be absent or stale. Require `fresh(0.5)`, at least seven motors and valid feedback for all seven arm channels before using joint angles. `age()` reports elapsed seconds; `hz` is a sliding estimate and can initially be zero without proving link loss. `joints()` defaults to fresh data, returning `None` on expiry; `fresh=False` can return old data. `wait_state(predicate, timeout)` returns `None` on timeout. `subscribe()` callbacks run in the receiver thread: do not block; unsubscribe after use and inspect `callback_errors`. [SDK IV](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

| Snapshot field                                             | Meaning                                                            |
| ---------------------------------------------------------- | ------------------------------------------------------------------ |
| `execution_state`                                          | 0 disabled, 1 hold, 2 running, 4 fault                             |
| `fault_code`, `stop_reason`                                | Current arm fault versus most recent stop cause; distinct meanings |
| `enabled_mask`                                             | Bitmask of force-producing channels; zero means none               |
| `motors[i].q`, `dq`, `tau_est`                             | rad, rad/s, N·m                                                    |
| `status`; `enable/fault/overtemp/installed/feedback_valid` | Raw channel status and convenience flags                           |
| `temperature_c`, `voltage_v`, `error_mask`                 | Optional fields; `None` means unreported, not zero                 |

`enable()` constructs an anchoring hold from measured positions, requests enable and confirms status (default confirmation limit 0.5 s). `disable()` also confirms. `enabled` can be `True`, `False` or **`None` when status is stale**. A completed motion handle is not evidence of physical movement if the arm was disabled. `arm.stop()` cancels motion and enters gravity-compensated hold; it is different from force release. Device-local stream-loss hold can sag and is different again from SDK cleanup that explicitly disables. [SDK V–VI](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

ArmEcho organizes connection/authority/link indicators along the top, motor details on the left, the live model and last-command result in the center, and mode/function panels on the right; narrow screens use floating controls. Judge a rejected command from its result bar, not the animation alone. Read Current TCP fills an IK reference; the view is not evidence of an obstacle-free path. A panel selection alone does not enable motion. [Interface layout](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho)

### Motion API decisions <a href="#motion-api-decisions" id="motion-api-decisions"></a>

| Interface                                 | Semantics and conditions                                                                                                                                                                                                                 |
| ----------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `movej(q, speed, accel)`                  | Seven joint radians; synchronized joint-space interpolation. Speed 0.2–5 rad/s, default/zero 2; acceleration 0.8–12 rad/s², default 12. Values below minima can be raised, making motion faster than requested. Inspect `result.detail`. |
| `movejp(pos, rpy, …)`                     | Position meters, ZYX Euler orientation radians; IK once, then joint-space travel, **not a straight TCP path**. Approximate solutions within 1 cm/2° may be accepted; `allow_approx=False` disables that behavior.                        |
| `home()`                                  | Joint-space return to zero and hold; verify the entire path and current model.                                                                                                                                                           |
| `forward_kinematics(q)`                   | Exactly seven finite radians, no gripper; base-frame TCP meters and ZYX Euler radians. Raises `KinematicsError` for invalid input.                                                                                                       |
| `start_drag(kd)`                          | Gravity-supported manual guidance; damping 0.5–2 N·m·s/rad, default 1. Stream loss removes gravity feedforward and can cause sinking.                                                                                                    |
| `start_damping()` / `start_zero_torque()` | No gravity support; zero-torque remains electrically enabled. Neither is a safe suspended rest.                                                                                                                                          |
| `start_fatigue(rounds, speed)`            | Wide repeated sweeps; `None` continuous or integer ≥1, speed 8–12 rad/s, default 10, acceleration speed/4; overtemperature stops the exercise.                                                                                           |
| `fatigue_state()`                         | Read-only progress: `rounds_done`, `rounds_target`, `phase`, `stop_reason`; phases initial home, sweep, round-end home; `None` when inactive.                                                                                            |

All above behavior is from [SDK VI](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK). High-level gravity/geometry gates currently require upright mounting, despite broader mechanical mounting options. A new motion cancels the previous one. A handle exposes `status`, `ok`, `result.error/detail/diffs`, `cancel()` and bounded `wait()`. Only `COMPLETED` makes `wait()` true; timeout/failure/cancellation return false or raise `MotionError` with `raise_on_failure=True`. **Wait timeout does not stop motion**: use cancellation/hold under the approved procedure. Duration follows travel, speed and acceleration, with no eight-second cap. `wait_idle()` only waits for running state to end.

ServoJ uses `servoj_start()`, repeated `servoj(q,t)`, then `servoj_end()`. `t` is desired travel time, not send period; positive values below 0.002 s are raised to that minimum, nonpositive values fail. One pending target is retained; each quintic segment has zero endpoint velocity, so segment-to-segment velocity continuity is not promised. Fresh state, ownership, enable and geometry agreement are prerequisites; conflicting motion is rejected, and stream loss/fault/disable aborts the servo. [SDK VII](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

### Expert MIT, gripper, teaching and payload <a href="#expert-mit-gripper-teaching-and-payload" id="expert-mit-gripper-teaching-and-payload"></a>

Expert MIT uses `mit_start()`, `mit(q,kp,kd,dq,tau)`, `mit_end()`. It can raw-enable through its own anchoring path, bypassing high-level gravity/mounting/model gates. Eight channels are submitted latest-wins and sent in the background at approximately 500 Hz. Channels 0–6 use joint radians; channel 7 uses native gripper radians, factory 0–5.27, with all five channel-7 inputs required to be zero if absent. Unknown installed gripper range rejects a nonzero command. `mit()` reports `clamped` and `gripper_ignored`; an absent all-zero gripper channel is ignored. `q` is clamped and reported in `clamped`; gains must be finite/nonnegative, but gains, `dq` and signed `tau` have no protective rated upper bounds. No gravity feedforward or high-level collision/path planning is added. `mit_end()` leaves force-producing hold, **not disable**. Stream loss uses measured-position hold, previous gains, zero velocity and **zero feedforward torque**, potentially losing load support. MIT excludes ordinary arm/gripper motion; fault, lease release or link loss aborts it. [SDK VIII](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

Teaching uses `record()`, `play()`, `set_speed()`, `set_accel()`, `set_loop()` and device slots `save/load/clear/list_slots`. Eight zero-indexed SDK slots each hold up to 256 waypoints; ArmEcho displays groups 1–8. Playback needs at least two points, moves segment by segment with zero endpoint velocities and can loop. Changes apply from the next segment. Speed/acceleration follow the ordinary motion ranges; wait expiry does not stop playback. Save only after checking existing data. [SDK IX](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK), [ArmEcho IX](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho)

`arm.gripper.move/open/close/stop/state` return dictionaries: inspect `ok` and `error`; ordinary command errors are not exceptions. `configure(GripperCalibration(…))` can throw `GripperError`. Opening is 0–100%; range is read from the device or explicitly configured. Stall torque hold defaults to 0.3 N·m and allows 0–1.5 N·m as an open-loop estimate; after stall, target becomes the measured position with `kp=0`, `kd=2` and signed feedforward torque. `gripper.stop()` sends a zero frame and releases gripper force; support any grasped object before relying on it. Overtemperature zeros the channel. Gripper speed documentation conflicts: ArmEcho maps UI 50–100 to SDK 500–1000 and describes 1000 as one full stroke/s, while SDK prose says 1000 completes a stroke in 0.1 s. Confirm the delivered version's semantics before using timed gripper motion. Gripper commands are rejected during identification. [SDK X](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK), [ArmEcho XI](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho)

`payloads.identify_bidirectional()` performs substantial automatic sampling motion, applies compensation and attempts saving; it blocks until terminal state. Calling `handle.wait(timeout)` afterwards cannot impose an acquisition timeout; cancellation requires `payloads.cancel()` from another thread. Do not touch/support the moving arm during sampling. Inspect `state().active`, `.saved`, save errors and whether saved parameters match active mass/first moment. `clear()` and `apply_saved()` require disable; clearing retains the saved record and suppresses automatic reload within that connection. Matching records may reload before connect/reconnect/enable while disabled; a failed automatic apply is silently skipped and never enables. Change flange/payload → reassess and re-identify. The manual both calls the production preset fixed and mentions custom `IdentificationConfig`; a custom workflow is not specified here. [SDK XI](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK), [payload example](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/09_payload.py)

Teaching, payload records and `device_config.mounting` live on the arm, but `device_data.export_bytes()` includes only nonempty teaching slots and device configuration in one JSON file—**payload records are excluded**. `import_bytes()` validates then writes records, potentially replacing stored data. `connect(mounting=…)` is an initial connection value, overridden by a stored device value; persisting needs explicit `device_config.mounting = …`. Write configuration while idle and confirm runtime compensation afterwards; a write during identification/ServoJ may persist without synchronizing the running state. [SDK XII](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: reject bad feedback offline <a href="#first-result-reject-bad-feedback-offline" id="first-result-reject-bad-feedback-offline"></a>

1. Keep hardware disconnected. Save this synthetic local record as `sample.json`. This original interchange schema is **not** a D2 wire packet or SDK serialization; its values are an offline fixture, not observed hardware feedback.

```json
{"age_s":0.1,"motors":[
  {"q":0.0,"feedback_valid":true},
  {"q":0.3,"feedback_valid":true},
  {"q":0.0,"feedback_valid":true},
  {"q":-0.5,"feedback_valid":true},
  {"q":0.0,"feedback_valid":true},
  {"q":0.0,"feedback_valid":true},
  {"q":0.0,"feedback_valid":true}
]}
```

2. Save the original program below as `check_snapshot.py` and run `python3 check_snapshot.py sample.json`.

```python
"""Original offline snapshot interchange example, not the D2 wire format."""
import json
import math
import sys


def check(sample):
    age = sample["age_s"]
    if isinstance(age, bool) or not isinstance(age, (int, float)) or not math.isfinite(age) or not 0 <= age < 0.5:
        raise ValueError("stale or invalid local sample age")
    motors = sample["motors"]
    if len(motors) < 7:
        raise ValueError("incomplete arm feedback")
    q = []
    for motor in motors[:7]:
        v = motor["q"]
        if motor["feedback_valid"] is not True:
            raise ValueError("invalid feedback flag")
        if isinstance(v, bool) or not isinstance(v, (int, float)) or not math.isfinite(v):
            raise ValueError("non-finite or non-numeric joint angle")
        q.append(v)
    return {"arm_joints": 7, "q_rad": q, "quality": "fresh complete local sample"}


if __name__ == "__main__":
    with open(sys.argv[1]) as stream:
        print(json.dumps(check(json.load(stream)), indent=2))
```

Expected checkpoint: seven finite `q_rad` values and `quality="fresh complete local sample"`. A stale age, absent axis, false feedback flag or NaN/Infinity fails. The 0.5 s local policy mirrors the freshness threshold used in the manufacturer's state/FK examples, but an offline sample does not prove a device link or safe pose. [State example](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/02_state_subscribe.py), [TCP example](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/12_read_tcp.py)

### Supervised first-status procedure, documented but not executed <a href="#supervised-first-status-procedure-documented-but-not-executed" id="supervised-first-status-procedure-documented-but-not-executed"></a>

1. Record hardware/gripper, firmware, geometry ID, mounting, supply and SDK/ArmEcho versions. Verify mounting and power drawings, exclusive ownership, support against gravity and the independent physical stopping arrangement.
2. With controller disabled and arm supported, select one transport. For Ethernet, set the host NIC to the documented subnet and check the current device address (`ping 192.168.123.2` only when the unit still has that address). For serial, verify the stable path and host/container access. Do not run ArmEcho and a separate SDK client against the same arm.
3. In ArmEcho, use **System Configuration → Connection Method** to choose UDP/address or USB/path. Applying a different transport can disable, disconnect and abort identification; do it only after stopping and supporting the mechanism. Confirm Connected, control Held, Disabled, changing joint readings and plausible link quality. Multiple windows share one command owner.
4. In a dedicated SDK session, `connect()` then `device_info()` and fresh `state` can establish identity/counts/geometry/version and seven valid joints without calling `enable()`. Nevertheless connect takes authority and can apply saved compensation, and closing explicitly attempts disable; this is **not** a passive monitor for an already controlled arm. The original offline example remains this guide's only executed first result.
5. Do not use Hold, Damping, Zero Torque, Return-to-Zero, Drag, Playback, Fatigue or Identification as observation buttons: ArmEcho can automatically enable force-producing modes. Joint `movej` and IK require prior explicit enable, and the SDK never implicitly enables ordinary motion. Stop at verified identity/status before any supervised motion acceptance. [ArmEcho IV–VII](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho), [FAQ enable distinctions](https://support.unitree.com/home/en/D2_Arm_Development_Guide/FAQ)

ArmEcho joint entries use radians; IK position uses meters but its orientation UI uses **degrees**, unlike the SDK's radians. Read Current TCP supplies a reference, not a path guarantee. Drag damping changes take effect through Apply. Teaching speed UI 100%=2 rad/s and acceleration 100%=8 rad/s² (Auto uses 12); the UI rejects some invalid entries while the SDK may clamp. The host/user manuals also disagree on clamping versus rejecting out-of-range joint input: check the actual command bar and do not rely on automatic correction. [ArmEcho panels](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho), [limit handling](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2)

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### Indicators and four different stop meanings <a href="#indicators-and-four-different-stop-meanings" id="indicators-and-four-different-stop-meanings"></a>

| Indicator                                            | Documented interpretation                                                   |
| ---------------------------------------------------- | --------------------------------------------------------------------------- |
| Ice-blue breathing                                   | Disabled                                                                    |
| Green breathing                                      | Enabled/idle or running without task effect; check telemetry                |
| Orange breathing                                     | Host motion task                                                            |
| Red heartbeat-like effect                            | Hardware/power fault; unknown red codes take this severe path               |
| Red interrupted pulses                               | Internal/control-loop fault                                                 |
| Red slow breathing / “aurora”                        | Recoverable motion fault                                                    |
| Amber interrupted pulses                             | Axis offline; not necessarily whole-arm fault                               |
| Purple; green ripple                                 | Firmware receiving/waiting; upgrade success                                 |
| Amber steady; fast green flash; red flash during SW1 | Reset press recognized; network restored/restarting; rejected/write failure |

Normal priority is fault → host task → offline axis → automatic status; SW1 feedback overrides normal effects. LEDs are assistance, not authority for entering the workspace. A green channel `ON` badge can coexist with a whole-arm fault and continued force. Inspect execution state, fault bar and channel details. [LED and fault guidance](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2)

Stream loss after the controller timeout enters local hold and can sag; no numeric timeout was established. SDK `stop()` requests supported hold, SDK `disable()` releases force, and physical emergency power interruption also removes support. Idle is not automatic disable. SDK cleanup explicitly requests disable, unlike unmanaged client disappearance. The manuals differ about whether fallback anchors to actual or last-target position; do not use fallback as a planned holding mechanism. [User VI](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2), [SDK V/VIII](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

### Connection, command and fault diagnosis <a href="#connection-command-and-fault-diagnosis" id="connection-command-and-fault-diagnosis"></a>

Connection/session/transport/protocol exceptions include `LinkError`, `SessionError`, `ProtocolVersionError` and `TransportError`. Model/command exceptions include `IKError`, `KinematicsError`, `MountingError`, `GravityError`, `GripperError`, `ServoJError`, `CommandError` and `ExpertMitError`; storage uses `TeachStoreError`, `PayloadStoreError` and `DeviceStorageError`. `MotionError` and `UpgradeError` cover their specific operations. Catch the actual type and preserve result/detail instead of treating all failures as a reconnect problem. `EnableError` is separate, and ordinary gripper commands return status dictionaries. [Exception contract](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

Check in order: power/physical link → current address/path → host/container permissions/firewall → correct model/protocol → exclusive authority → fresh seven-axis feedback → enable/geometry/mounting → command limits/result. `LinkError` points to link/address/power, `TransportError` can include serial permission/path hints, `SessionError` denotes authority failure. `EnableError.result` gives a rejection code; `.observed` describes a confirmation timeout. A handle may fail without throwing; inspect `result.error`, `detail` and model `diffs`. Stale or absent readings are not measured zeros. [SDK XIV](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK), [FAQ](https://support.unitree.com/home/en/D2_Arm_Development_Guide/FAQ)

| Command `result`                       | Meaning / first interpretation                                           |
| -------------------------------------- | ------------------------------------------------------------------------ |
| 0 `OK`                                 | Command succeeded; not independent proof of physical motion              |
| 1 `DENIED_BUSY`; 2 `NOT_READY`         | Resource owner conflict; readiness/anchor gate not met                   |
| 3 `BAD_BOOT`; 4 `BAD_SESSION`          | Device rebooted; authority invalid—reconnect with recorded configuration |
| 5 `FAULT_ACTIVE`; 6 `OUT_OF_RANGE`     | Resolve fault; validate parameter                                        |
| 7 `INTERNAL_ERROR`; 8 `BAD_SEQUENCE`   | Preserve logs; duplicate/out-of-order sequence                           |
| 9 `NOT_FINITE`; 10 `LIMIT_EXCEEDED`    | Reject NaN/Infinity; review limit/model                                  |
| 11 `UNSUPPORTED`; 12 `SAFETY_OVERRIDE` | Capability unavailable; safety intervention                              |

| Arm `fault_code`                               | Recovery boundary                                                                                                                              |
| ---------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 0                                              | No arm fault; still check gripper/channel status                                                                                               |
| 1 motor; 2 overtemperature; 3 encoder; 8 power | Support the arm, stop work, resolve wiring/supply/load/cooling; manual prioritizes controlled power restart; reset cannot repair the cause     |
| 4 joint limit                                  | May still exert force. Support, disable, verify force release, return physically within allowed range using the approved procedure, then reset |
| 7 stale control loop                           | Controlled restart and supplier logs; repeated reset/continued operation is inappropriate                                                      |
| 9 tracking error                               | Remove obstruction/overload, reduce demand; after reset choose a new target close to measured pose, never blindly resend the distant target    |

Codes 5/6 are retired. `stop_reason` 0 none, 1 target expired, 2 lease expired, 3 user cancel, 4 prior fault describes the **latest stop**, not necessarily a current fault. Channel error bits 0–10 mean under-voltage, over-voltage, overcurrent, overtemperature, encoder, overload, uncalibrated, overspeed, driver, other, offline. Unknown optional fields remain unknown. Gripper faults affect index 7 and do not enter top-level arm `fault_code`; offline status may clear when feedback returns or escalate if persistent. Expert gripper recovery may require reset → supported disable → re-enable, never automatically. [SDK XIV](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

The user/SDK manuals say reset preserves the prior enable state (enabled → hold; disabled stays disabled), while the ArmEcho manual says reset leaves disabled. **Observe actual state after reset; assume neither force release nor re-enable.** No reset automatically replays an old target. [User VIII](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2), [ArmEcho V](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho)

### Recovering a wrong network configuration <a href="#recovering-a-wrong-network-configuration" id="recovering-a-wrong-network-configuration"></a>

Saving device IP/mask/listen/broadcast settings requires disable and takes effect after restart; **Connect Device** changes only the host target. When still reachable, connect at the current address, save the corrected settings, then perform a supported restart. When unreachable, the official SW1 sequence is: start normally **without holding SW1 during power-on**; with motors not enabled, hold SW1 about five seconds. Amber around one second only acknowledges the press; release early cancels. Fast green around five seconds signals save, followed by automatic restart around 1.5 s later. Red flash means rejected/write failed and no restart. Reconnect host `.123.x/24` to `192.168.123.2:2000`, then set any required unique address. This resets **network only**, retaining trajectories, payload and mounting records. Do not operate it on an enabled arm. [User IX](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2)

### Upgrade, backup and persistent-data boundaries <a href="#upgrade-backup-and-persistent-data-boundaries" id="upgrade-backup-and-persistent-data-boundaries"></a>

Firmware upgrades require UDP, an identified supplier `.bin`, stable power/link and all motors disabled; fault state alone is not disqualifying, but remaining enable is. ArmEcho's System Configuration → Controller Firmware Upgrade checks connection/no running task/disable, transfers, restarts and compares versions. `arm.upgrade.run()` yields authority and then reconnects/reacquires automatically; inspect `link_state` and reported version afterwards. Bootloader is factory-only, not upgraded by this UI. Same-version reporting cannot distinguish a successful reflash from rollback. [ArmEcho XIV](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho), [SDK XIII](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK)

Interrupted transfer/verification can leave the device waiting for re-upload; a fully written image that fails boot may retry or recover a retained usable image. Early boot stalls may require supplier-directed restart, and one attempt does not guarantee recovery. Never interrupt an active write or substitute a guessed image. Repeated failure or post-start runtime faults require supplier support. Backup nonempty teaching/configuration separately; export excludes payload records, so migration needs re-identification or separate parameter records. [Recovery FAQ](https://support.unitree.com/home/en/D2_Arm_Development_Guide/FAQ)

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                                                                                         | Scope                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------- |
| [D2 product](https://www.unitree.com/D2/)                                                                                                                                                                                                                                                                                                        | Applications and published performance                                                 |
| [Safety introduction](https://support.unitree.com/home/en/D2_Arm_Development_Guide/about), [product/packing/drawings](https://support.unitree.com/home/en/D2_Arm_Development_Guide/product)                                                                                                                                                      | Handling, environment, mechanical interfaces                                           |
| [User documentation](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2), [ArmEcho manual](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20ArmEcho), [SDK manual](https://support.unitree.com/home/en/D2_Arm_Development_Guide/D2%20SDK), [FAQ](https://support.unitree.com/home/en/D2_Arm_Development_Guide/FAQ) | All accessible article functions paraphrased above; source-specific conflicts retained |
| [Official download article](https://support.unitree.com/home/en/D2_Arm_Development_Guide/data)                                                                                                                                                                                                                                                   | Resource provenance and update entry point                                             |
| [D2 delivery repository](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/README.md), [ArmEcho releases](https://github.com/unitreerobotics/D2-Arm/releases)                                                                                                                                              | SDK/wheel/checksum/example and host-image distribution                                 |
| [Manufacturer URDF archive](https://oss-global-cdn.unitree.com/static/d31972190a194e7690e6dd7f10ef8f83.zip), [simplified model](https://oss-global-cdn.unitree.com/static/dcc9d4fe3f2b4291801b19d456bed000.zip)                                                                                                                                  | Observed direct CAD/model links; archives not downloaded or executed                   |
| [Manufacturer firmware archive](https://oss-global-cdn.unitree.com/static/241df3e1e8d94d559a524d0d64086444.zip)                                                                                                                                                                                                                                  | Observed link, **not a verified version or approved image for an arbitrary D2**        |

The repository has 13 example scripts. Their functions and effects are: [01 minimal](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/01_minimal.py) enables/moves; [02 state](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/02_state_subscribe.py) subscribes within a control session; [03 gripper](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/03_gripper.py) actuates; [04 upgrade](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/04_upgrade.py) writes firmware; [05 MIT](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/05_expert_mit.py) raw-enables/moves; [06 IK/home](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/06_movejp_home.py) moves; [07 ServoJ](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/07_servoj.py) moves; [08 teach](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/08_teach.py) records/replays motion; [09 payload](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/09_payload.py) moves and persists compensation; [10 backup](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/10_device_data.py) exports or overwrites device data; [11 modes](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/11_motion_modes.py) changes force output/sweeps; [12 TCP](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/12_read_tcp.py) computes FK from session state; [13 errors](https://github.com/unitreerobotics/D2-Arm/blob/8d505a8c511f2a8dd401bd4c410e37121b1bfd17/sdk/examples/13_errors.py) enables/moves while demonstrating failures. Even state/TCP session exit can disable. These are references, not a run-all checklist.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed 24 November 2026: current manufacturer product HTML, seven actual English portal article bodies from the official documentation CDN, the pinned delivery repository files, and selected manufacturer figures. Portal source timestamps span 11 November 2026 updates; an article update time is not an installed firmware version. Detailed article/heading crosswalk and source hashes accompany this draft.

Validation executed only original offline sample-quality checks. No vendor code, SDK installation/import, build, Docker/ROS launch, device connection, firmware transfer or hardware motion was executed. Published figures remain source links with attribution rather than republished manuals. Unresolved supply pinout, package licensing, delivered firmware compatibility and the documented cross-source differences prevent blanket commissioning approval.

**Related documentation:** [Unitree model and development directory](./).
