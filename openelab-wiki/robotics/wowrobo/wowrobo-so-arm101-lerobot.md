---
description: >-
  Build WR-ARM101-Kit with its12 V follower/5 V leader supplies, configure six
  motor IDs, read raw feedback and calibrate before LeRobot teleoperation and
  recording.
---

# WowRobo SO-ARM101 DIY: exact power, motor setup and LeRobot teleoperation

{% hint style="info" %}
[**WowRobo SO-ARM101 unassembled black leader–follower kit + camera — SKU WR-ARM101-Kit**](https://openelab.io/products/wowrobo-robotics-so-arm101-diy?variant=45497995067590)
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

This SKU is the **unassembled black SO-101 pair with one leader, one follower and one RGB camera**. Each arm has five articulated joints and a gripper actuator. It is intended for LeRobot teleoperation, data collection and imitation-learning experiments. It is not the printed-parts-only WR-ARM101-P package or the assembled/calibrated WR-ARM101-Kit-A option. [Exact OpenELAB configuration](https://openelab.io/products/wowrobo-robotics-so-arm101-diy?variant=45497995067590), [WowRobo package comparison](https://shop.wowrobo.com/products/so-arm101-diy-kit-assembled-version-1).

Commission the two buses separately: verify their supplies and motor types, assign unique IDs, assemble with correct motor gearing, read raw positions and calibrate before any leader-to-follower mapping. A powered USB adapter being visible does not establish correct motor IDs or safe power wiring.

## Applications

Use the leader to demonstrate a constrained tabletop task and the follower to reproduce it. Start with short unloaded joint movements, then a light foam-block pick and finally several consistently framed demonstrations. Keep camera viewpoint, arm calibration and task geometry stable across recordings.

The supplied 2MP camera is RGB only; native depth, force sensing, ROS 2, MoveIt and Isaac Sim are separate integrations. Do not infer a metric3D grasp point from an uncalibrated image or assume a policy trained with another action normalization will work unchanged. [Store scope](https://openelab.io/products/wowrobo-robotics-so-arm101-diy), [LeRobot robot guide](https://huggingface.co/docs/lerobot/so101).

## Specifications

| Item                         | Exact package / development reference                                       |
| ---------------------------- | --------------------------------------------------------------------------- |
| SKU                          | WR-ARM101-Kit; unassembled black pair +1 camera                             |
| Arms / actuators             | 2 arms; 6 actuators each; 12 servos total                                   |
| Leader motors                | 7.4 V-class STS3215: 1×C001, 2×C044, 3×C046                                 |
| Follower motors              | 6×C018, 12 V-class STS3215, 1/345 gearing in WowRobo packing image          |
| Included supplies            | 12 V 8 A and 5 V 6 A; separate follower/leader power domains                |
| USB motor adapters           | 2 Waveshare servo adapters in package comparison                            |
| Mounting/data                | 4 C-clamps; 2 dual-Type-C 1.5m data cables                                  |
| Vision                       | 1 × 2MP RGB camera                                                          |
| Assembly/calibration service | Not included in this unassembled package                                    |
| Shipping reference           | Package2: 34 × 30 × 25 cm, 5 kg; shipping data, not arm envelope or payload |
| Software snapshot reviewed   | LeRobot0.7.1 source, Python≥3.12 at the pinned commit below                 |

The power and motor identification above comes from the **manufacturer's package-detail image**, which was visually inspected. Upstream SO-101 also supports other follower motor-voltage options; that general BOM does not override this vendor's C01812 V follower bundle. Check the delivered labels before connecting either supply. [WowRobo package image](https://shop.wowrobo.com/cdn/shop/files/0041.jpg?v=1746455209), [hardware BOM](https://github.com/TheRobotStudio/SO-ARM100).

| Joint ID/name    | Leader gear ratio | Follower gear ratio |
| ---------------- | ----------------- | ------------------- |
| 1 shoulder\_pan  | 1/191, C044       | 1/345, C018         |
| 2 shoulder\_lift | 1/345, C001       | 1/345, C018         |
| 3 elbow\_flex    | 1/191, C044       | 1/345, C018         |
| 4 wrist\_flex    | 1/147, C046       | 1/345, C018         |
| 5 wrist\_roll    | 1/147, C046       | 1/345, C018         |
| 6 gripper        | 1/147, C046       | 1/345, C018         |

[SO-101 gearing/assembly guide](https://huggingface.co/docs/lerobot/so101). Faster leader gears reduce manual resistance; swapping all leader motors for follower gearing changes the experience even if the connectors fit. No verified object payload, repeatability or arm dimensions are invented from packaging dimensions.

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Separate the 12 V follower from the 5 V leader

![WowRobo SO-ARM101 official package-detail chart](https://shop.wowrobo.com/cdn/shop/files/0041.jpg?v=1746455209)

Attributed WowRobo packing chart. Label the **follower adapter12 V** and **leader adapter5 V** before assembly. The leader's7.4 V-class motor designation is not an instruction to replace its included5 V supply with 12 V. The upstream BOM explicitly distinguishes7.4 V and 12 V motor versions. Keep the adapter, motors and matching power supply together.

Each arm uses its own USB adapter and its own three-wire serial-servo chain. Use the board's printed GND/supply/data markings and keyed cable orientation; do not infer polarity from a mirrored product photograph. This is a half-duplex servo bus, not a pair of cross-connected RS-232 lines. USB provides host communication; it is not a substitute for the correct motor supply. On the Waveshare adapter branch, the LeRobot guide specifies both routing jumpers on **B/USB**. Verify the actual board revision and its markings before moving jumpers. [Motor setup](https://huggingface.co/docs/lerobot/so101#configure-the-motors).

### Assembly order and mechanical checks

Configure IDs before daisy-chaining brand-new motors, which can all start atID1. Keep only the motor requested by the setup tool connected during each assignment. After assignment, disconnect power before changing the chain and inspect cabling before proceeding. Only join all six once each has a unique role/ID.

Follow the official joint-by-joint sequence: clean printed supports, install horns and the correct geared motor, fasten its holder, route the cable, then continue to the next link. The guide distinguishes M2 × 6 and M3 × 6 fasteners and the leader handle from follower gripper. A screw that bottoms out or distorts a printed part should not be forced. Check horn seating, free cable travel and clearance before loading the arm. [Assembly drawings/videos and printable parts](https://github.com/TheRobotStudio/SO-ARM100), [joint sequence](https://huggingface.co/docs/lerobot/so101).

Clamp both bases to a rigid surface with separate clear workspaces. Support the follower before torque changes or loss of power; it can drop. Do not hold a leader at one extreme while connecting a follower at another, then start mirroring.

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

This guide reviews LeRobot commit `c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad`, whose package metadata identifies0.7.1 and Python≥3.12. Older tutorials using Python 3.10 or earlier Feetech class paths describe a different release. The current source exports `SerialMotorsBus` from `lerobot.motors`; `FeetechMotorsBus` is a deprecated compatibility alias. [Pinned project metadata](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/pyproject.toml), [bus API](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py).

Use a supported Python 3.12 environment; the official installation guide covers OS, PyTorch, video decoding and optional platform dependencies. A robot-control environment and a GPU training environment need not be the same machine. Save the source commit and dependency versions with every dataset.

```bash
git clone https://github.com/huggingface/lerobot.git
cd lerobot
git checkout c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad
python3.12 -m venv .venv
. .venv/bin/activate
python -m pip install -e '.[feetech]'
lerobot-find-port
```

The port tool asks you to unplug one adapter's **USB data cable** to identify it. Record which physical board is leader/follower; do not unplug a loaded motor harness during motion. Port names can change after reconnecting; use a stable device path or repeat identification. Resolve normal serial-group permissions rather than making every serial port globally writable. [Installation](https://huggingface.co/docs/lerobot/installation), [port identification](https://huggingface.co/docs/lerobot/so101).

## Getting started <a href="#getting-started" id="getting-started"></a>

### 1. Configure one bus at a time

1. Confirm adapter power labels, motor voltage/gearing and board jumper positions. Keep the arm supported and the motor workspace clear.
2. Identify the follower port, then run `lerobot-setup-motors --robot.type=so101_follower --robot.port="$FOLLOWER_PORT"` after assigning `FOLLOWER_PORT` to that observed path.
3. Follow the prompt to connect **only** the named motor; the documented sequence starts with the gripper and assignsID6, then continues through the other roles. This writes IDs/baud settings in motor memory; do not run it on the entire unconfigured chain.
4. Repeat for the leader with `lerobot-setup-motors --teleop.type=so101_leader --teleop.port="$LEADER_PORT"`, using its distinct observed port and 5 V supply.
5. Power down, recheck each arm's IDs/cabling and finish mechanical assembly. Preserve the role-to-ID table above.

\*\*Expected result: \*\*the tool confirms the requested role/ID for each motor and completes without duplicate responses. A missing response calls for power, cable, jumper and single-motor inspection, not repeated bulk EEPROM writes. [Official setup procedure](https://huggingface.co/docs/lerobot/so101#_2-set-the-motors-ids-and-baudrates).

### 2. Original read-only six-position report

After IDs/baud are configured, save `so101_read_positions.py` and run `python so101_read_positions.py "$FOLLOWER_PORT"`. It opens the bus, handshakes and reads raw position registers. It does **not** call the robot class's `connect()`, which configures motors, and it closes with `disable_torque=False` to avoid changing torque state. Physically support the arm regardless of its current state.

```python
import sys
import time
from lerobot.motors import Motor, MotorNormMode, SerialMotorsBus

names = ['shoulder_pan', 'shoulder_lift', 'elbow_flex',
         'wrist_flex', 'wrist_roll', 'gripper']
bus = SerialMotorsBus(
    port=sys.argv[1],
    motors={name: Motor(i + 1, 'sts3215', MotorNormMode.DEGREES)
            for i, name in enumerate(names)})
try:
    bus.connect()
    for sample in range(10):
        values = bus.sync_read('Present_Position', normalize=False, num_retry=1)
        if set(values) != set(names):
            raise RuntimeError('Incomplete six-motor response')
        print(sample, ', '.join(f'{name}={values[name]}' for name in names))
        time.sleep(0.2)
finally:
    bus.disconnect(disable_torque=False)
```

\*\*Expected result: \*\*ten rows containing all six names and raw register values. They are not degrees despite the declared normalization mode, because normalization is explicitly disabled. Read success does not prove calibration, range or safe actuation. Repeat with the leader port as a separate check. The bus source verifies that this connect path only opens/handshakes; normal robot connection additionally configures the actuators. [Reviewed implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py).

### 3. Calibrate without mixing identities

Give each arm a durable unique ID, for example `bench_follower` and `bench_leader`. Run the documented calibrator with its correct port/type:

```bash
lerobot-calibrate --robot.type=so101_follower --robot.port="$FOLLOWER_PORT" --robot.id=bench_follower
lerobot-calibrate --teleop.type=so101_leader --teleop.port="$LEADER_PORT" --teleop.id=bench_leader
```

Follow the prompted middle/reference posture and manually record the required range with torque disabled. Support links and avoid forcing mechanical stops. Calibration defines how raw readings map into joint/action values; save the generated files and retain the same arm IDs for later teleoperation/recording. A replacement motor, horn reassembly or altered range can invalidate them. [Calibration](https://huggingface.co/docs/lerobot/so101#calibrate).

\*\*Expected result: \*\*separate calibration records for the two physical arms and sensible corresponding normalized positions in similar poses. The current follower defaults to degrees for body joints and 0–100 for the gripper; older normalized datasets can differ. Record `use_degrees` with dataset/policy configuration rather than assuming a universal action scale. [Follower configuration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/config_so_follower.py).

### 4. First teleoperation and camera check

Bring both calibrated arms to similar supported starting postures. Clear their link/gripper sweeps and retain quick access to motor power. Inspect the installed command's options with `lerobot-teleoperate --help`, then start the matched pair:

```bash
lerobot-teleoperate --robot.type=so101_follower --robot.port="$FOLLOWER_PORT" --robot.id=bench_follower --teleop.type=so101_leader --teleop.port="$LEADER_PORT" --teleop.id=bench_leader
```

This is an **actuation** command. Move the leader slowly through a small local excursion first; verify the follower's direction, scale and gripper response before larger movements. Stop the process before changing wiring. Torque-off disconnect behavior can let the follower settle/drop; support it before ending the session. Do not equate a target-increment cap with collision or force protection.

Find the actual camera device using the installed camera tools/OS enumeration. Validate one RGB stream at the intended resolution/FPS before adding it to teleoperation or recording. Camera index0 is only an example, not a stable identity. Fix its viewpoint/exposure, mount and timestamp settings, and verify the arm/target remain visible throughout the task. [Teleoperation implementation/options](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_teleoperate.py), [camera guide](https://huggingface.co/docs/lerobot/cameras).

### 5. Recording, training and replay

Use the current [imitation-learning tutorial](https://huggingface.co/docs/lerobot/il_robots)for the selected release's recording/training commands. Define a short measurable task, record a few pilot episodes and inspect them before collecting many more. Check joint names, action units, camera key, resolution, FPS, task text and episode boundaries. Keep failed attempts distinguishable from successful demonstrations.

Train with a policy appropriate to the available compute, and retain dataset/policy revision, normalization and calibration. Before deployment, inspect the proposed action stream and initial observation against the training setup. Test a small clear workspace with a light object; policy inference is physical control, not just video playback. Do not claim a trained policy exists or works merely because model files download.

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                            | Diagnostic                                                                                                   |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| USB adapter visible, no motor reply                | Check correct12 V/5 V supply, USB/B jumper route, three-wire cable and configured baud/ID                    |
| Setup sees inconsistent motors                     | Use only the prompted unconfigured motor; duplicate factoryID1 devices can collide                           |
| Leader hard to move                                | Check correct mixed gearing, torque state and joint binding; do not replace all leaders with follower motors |
| Follower jumps at start                            | Stop; compare calibration IDs, initial poses, action units and leader/follower ports                         |
| Raw positions readable but normalized values wrong | Inspect calibration range/reference and `use_degrees`; raw ticks are not a task-space transform              |
| Camera missing/wrong view                          | Enumerate actual device and close competing capture owners; verify selected camera key/index                 |
| Import fails with old Feetech path                 | Use the pinned release's `SerialMotorsBus` API or intentionally pin the older tutorial environment           |

**Can I use12 V on both adapters?** No. This vendor bundle has a 12 V follower and a 5 V-supplied leader with 7.4 V-class motors.

**Does the unassembled kit arrive calibrated?** Its package excludes the assembled option's assembly/calibration service. Perform the role/ID and calibration workflow yourself.

**Should I flash motor firmware to fix every timeout?** First diagnose power, ports, cables, IDs and baud. Firmware changes can alter compatibility; record each motor's current firmware and follow the matched [Feetech firmware guide](https://huggingface.co/docs/lerobot/feetech)only when required. Back up calibration before replacing motors or changing their configuration.

## Downloads and technical documents

| Resource                                             | Direct destination                                                                                                                                                      |
| ---------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Exact package chart                                  | [WowRobo packing image](https://shop.wowrobo.com/cdn/shop/files/0041.jpg?v=1746455209)                                                                                  |
| Mechanical source, BOM, printing and optional mounts | [TheRobotStudio/SO-ARM100](https://github.com/TheRobotStudio/SO-ARM100/tree/141aea7bcac2744d92998e30268c413202a56f96)                                                   |
| Assembly/IDs/calibration                             | [Official SO-101 guide](https://huggingface.co/docs/lerobot/so101)                                                                                                      |
| Software/install                                     | [LeRobot source](https://github.com/huggingface/lerobot/tree/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad),[installation](https://huggingface.co/docs/lerobot/installation) |
| Protocol/SDK                                         | [Serial motor bus implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py)                |
| Camera/recording examples                            | [Cameras](https://huggingface.co/docs/lerobot/cameras),[imitation learning](https://huggingface.co/docs/lerobot/il_robots)                                              |
| Optional features                                    | Upstream mounts, tactile, compliant-gripper and mobile-base links are separate hardware projects, not contents of WR-ARM101-Kit                                         |

The upstream hardware repository includes an Apache2.0 license; respect file-specific notices for any separately linked design. Code was inspected rather than copied as a complete application. This guide's bus report is an original example.

## WOWROBO SO-ARM101 full assembly and LeRobot workflow reference

[**OpenELAB SO-ARM101 unassembled black leader–follower and camera kit, WR-ARM101-Kit**](https://openelab.io/products/wowrobo-robotics-so-arm101-diy?variant=45497995067590)**.** This supporting reference expands the [canonical OpenELAB guide](https://wiki.openelab.io/robotics/wowrobo/wowrobo-so-arm101-lerobot). It applies to one SO-101 leader, one SO-101 follower and one RGB camera. The selected variant requires assembly, motor setup and calibration. OpenELAB separately lists printed parts plus servos as `WR-ARM101-P` and the assembled kit as `WR-ARM101-Kit-A`; their preparation states are different. Store identity was independently checked on **24 November 2026**. [Store variant data](https://openelab.io/products/wowrobo-robotics-so-arm101-diy.js), [vendor options](https://shop.wowrobo.com/products/so-arm101-diy-kit-assembled-version-1.js).

### Versions, prerequisites and control ownership <a href="#so101-reference-scope" id="so101-reference-scope"></a>

The software instructions below are tied to **LeRobot commit `c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad`**, whose package metadata says **0.7.1** and **Python ≥3.12**. The hardware reference is TheRobotStudio/SO-ARM100 commit **`141aea7bcac2744d92998e30268c413202a56f96`**. The motor transport is **rustypot**, not an independently installed historical SCServo Python driver: the reviewed LeRobot extra requires `rustypot>=1.13.1,<2.0.0`. The optional explicit SDK pin used below is **1.13.1**, independently checked at upstream commit **`7aa85e13143594ea4fd4ed9f29e3e29d39b5de85`**. These are source pins, not a claim that this combination was installed or commissioned on hardware. [LeRobot metadata](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/pyproject.toml), [hardware README](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/README.md), [rustypot metadata](https://github.com/pollen-robotics/rustypot/blob/7aa85e13143594ea4fd4ed9f29e3e29d39b5de85/Cargo.toml).

Before any arm-facing example, assign one person responsibility for the physical setup and one process ownership of each serial port. Stop teleoperation, recording, replay, policy rollout and vendor debugging applications before another program connects. The camera also needs an available device handle. Keep both bases clamped, the follower unloaded, the workspace clear and power reachable. Support the links whenever torque may be removed. This is especially relevant to this software:

| Operation                 | Actual source-level effect to plan for                                                                                                                                                                                               |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `lerobot-setup-motors`    | Changes motor ID and baud rate in nonvolatile memory; only the prompted motor may be on that bus.                                                                                                                                    |
| Follower `connect()`      | Opens the bus; may initiate calibration; connects cameras; writes motor configuration. Its torque-disabled configuration context **enables torque on exit**. Treat connection as an actuator operation, even before `send_action()`. |
| Leader `connect()`        | Configures position mode with torque disabled for ordinary hand-guided teleoperation. The leader can nevertheless be actuated by feedback/handover workflows.                                                                        |
| Calibration               | Frees the joints, changes homing/limit registers and saves a local calibration file. It requires controlled manual movement.                                                                                                         |
| Teleoperation / recording | Follower receives leader-derived joint targets. Reset phases in recording remain live teleoperation.                                                                                                                                 |
| Replay                    | Sends stored joint targets immediately after connection; a matching model name alone does not establish matching units, calibration or a safe initial pose.                                                                          |
| Rollout / HIL             | Policy owns the follower until an explicit handover. In HIL, the SO-101 leader may move under power to match the follower.                                                                                                           |
| Disconnect / shutdown     | Follower torque is disabled by default, so an unsupported link can drop. Rollout additionally defaults to returning toward the startup pose before disconnecting.                                                                    |

The source-reviewed examples are instructions for a future operator. **No installation, SDK import, serial transaction, camera capture, training, replay or motion was executed while preparing this reference.** The ownership and commissioning sequence is an engineering synthesis of the actual driver and workflow behavior. [Follower driver](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py), [leader driver](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/teleoperators/so_leader/so_leader.py), [motor bus](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py), [rollout configuration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/configs.py).

### Exact kit, motors, gearing and power <a href="#so101-kit-bom" id="so101-kit-bom"></a>

The WOWROBO package chart identifies Package 2 as the unassembled leader + follower + camera option. Its component list is the relevant BOM for this store selection; the upstream generic SO-101 shopping list also permits a lower-voltage follower and therefore must not replace the vendor-specific follower specification. [Vendor package chart](https://shop.wowrobo.com/cdn/shop/files/0041.jpg?v=1746455209), [vendor options](https://shop.wowrobo.com/products/so-arm101-diy-kit-assembled-version-1.js), [upstream sourcing alternatives](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/README.md).

| Supplied item                | Quantity / specification                                                                                     | Integration meaning                                                                                                                           |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Leader servos                | 1 × STS3215 **C001**, 7.4 V class, 1/345; 2 × **C044**, 7.4 V class, 1/191; 3 × **C046**, 7.4 V class, 1/147 | Install by joint, not simply by identical case appearance.                                                                                    |
| Follower servos              | 6 × STS3215 **C018**, **12 V class**, 1/345                                                                  | All six follower joints use this variant in the vendor chart.                                                                                 |
| Printed structures           | Black PLA+ parts for both arms                                                                               | Check fit, support removal and cracks before loading a motor into a holder.                                                                   |
| USB servo adapters           | 2 × Waveshare servo adapters                                                                                 | One independent serial motor bus per arm.                                                                                                     |
| DC supplies                  | One **12 V, 8 A** and one **5 V, 6 A** adapter                                                               | Use the 12 V supply for the C018 follower and the 5 V supply for the low-voltage leader arrangement; verify actual labels and polarity first. |
| Fixed clamps                 | 4 × C-shaped clamps                                                                                          | Secure both bases before calibration or actuation.                                                                                            |
| Host data leads              | 2 × 1.5 m dual-Type-C data cables                                                                            | Each servo adapter needs a working data connection, not only a charging lead.                                                                 |
| Camera                       | 1 × advertised **2 MP** camera                                                                               | One RGB observation stream; the chart does not establish depth, a particular sensor model, field of view or every supported capture mode.     |
| Assembly/calibration service | Not included for Package 2                                                                                   | Do not assume saved IDs, horn alignment or calibration.                                                                                       |

The vendor chart's “7.4 V” describes the leader servo class; it does **not** change the listed leader power adapter from 5 V to 7.4 V. Do not connect the 12 V follower supply to the leader bus. Adapter USB powers the interface but does not replace the correct servo DC supply. Connector polarity, plug fit and the delivered servo/supply labels must be checked on the actual kit; the reviewed package chart is not a dimensioned wiring drawing.

| Joint ID | Name used by LeRobot | Leader motor                      | Follower motor                |
| -------- | -------------------- | --------------------------------- | ----------------------------- |
| 1        | `shoulder_pan`       | C044, 1/191                       | C018, 1/345                   |
| 2        | `shoulder_lift`      | C001, 1/345                       | C018, 1/345                   |
| 3        | `elbow_flex`         | C044, 1/191                       | C018, 1/345                   |
| 4        | `wrist_flex`         | C046, 1/147                       | C018, 1/345                   |
| 5        | `wrist_roll`         | C046, 1/147                       | C018, 1/345                   |
| 6        | `gripper`            | C046, 1/147; operates the trigger | C018, 1/345; operates the jaw |

The different leader gear reductions reduce hand-guiding effort while supporting the structure. They do not change the joint IDs or justify multiplying LeRobot joint angles by the reduction ratio. The software's `sts3215` model discovery is not proof of the motor's voltage variant. [Assembly gearing table](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx), [driver motor definitions](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py), [vendor chart](https://shop.wowrobo.com/cdn/shop/files/0041.jpg?v=1746455209).

The hardware README quotes **stall torque**, including 30 kg·cm for the 12 V alternative and 16.5 kg·cm at 6 V for the low-voltage version. These are servo stall figures, not arm payload, continuous joint torque or gripper force. No verified payload, reach, repeatability, continuous duty cycle or complete arm mass is established by the sources reviewed here. The vendor's **34 × 30 × 25 cm / 5 kg** Package 2 figures describe the shipping package, not the assembled workspace or arm-only mass. [Hardware sourcing note](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/README.md), [vendor shipping description](https://shop.wowrobo.com/products/so-arm101-diy-kit-assembled-version-1.js).

### Host installation and reproducible configuration <a href="#so101-host-installation" id="so101-host-installation"></a>

Use a host with Python 3.12 or newer, two available USB serial connections, a camera connection, disk space for video and a suitable compute device for the chosen policy. Recording and motor control do not inherently require an NVIDIA GPU. Training and inference throughput must be assessed separately. The pinned installation guide documents macOS 14+ for Apple Silicon PyTorch and macOS 15+ for MPS; on macOS 14 the documented path falls back to CPU. At LeRobot commit `c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad`, the default Linux PyPI Torch/torchvision wheels are CUDA 13 builds requiring an NVIDIA driver **580.65 or newer**. These are that revision’s requirements, not a promise that later releases retain them. [Pinned installation requirements](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/installation.mdx). For the older-driver Linux CUDA 12 branch, first install matching Torch and torchvision in the active environment using `python -m pip install --index-url https://download.pytorch.org/whl/cu126 torch torchvision`, then CPU-index TorchCodec with `python -m pip install --index-url https://download.pytorch.org/whl/cpu torchcodec`, before the LeRobot installation below. The pinned guide states that Torch 2.15 has no CUDA 12 build and the `cu126` index selects 2.14; retaining CUDA 12 therefore means Torch 2.14 or older. With Torch below 2.11, also select the matching TorchCodec release from its compatibility table rather than assuming the newest decoder matches. This is an alternative dependency branch for a compatible older driver/GPU, not an extra installation required by every host. `uv pip install --torch-backend cu126 lerobot` selects that backend for a uv-pip install; `uv sync` instead follows the committed lock, so changing its CUDA build requires the relevant `[tool.uv.index]` and `[tool.uv.sources]` entries and regenerating the lock with `uv lock`. [Pinned CUDA installation branch](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/installation.mdx).

Create a new checkout and environment for this pin. These commands install software only; do not attach arm power until the later preparation steps:

```bash
git clone https://github.com/huggingface/lerobot.git so101-lerobot
cd so101-lerobot
git checkout c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad
conda create -n so101-reference python=3.12
conda activate so101-reference
conda install -c conda-forge ffmpeg
python -m pip install -e '.[core_scripts,feetech,training]' 'rustypot==1.13.1'
git rev-parse HEAD
python -m pip show lerobot rustypot
```

An already supported Python environment can use `venv` or `uv` instead. `core_scripts` brings dataset, hardware and visualization dependencies; `feetech` brings serial-motor support; `training` brings dataset/trainer dependencies including Accelerate and Trackio. ACT is included without a separate ACT extra. Base `pip install lerobot` alone is insufficient for this full workflow. The editable commit pin fixes LeRobot source, but the broad dependency ranges are **not** a complete dependency lock: save the resolved package list and platform information for a reproducible experiment. [Extras and entry points](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/pyproject.toml), [installation guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/installation.mdx), [ACT requirements](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/act.mdx).

TorchCodec is the usual decoder and needs compatible FFmpeg libraries. At this pin, the conda FFmpeg route used above works across supported Torch versions and is required by the documented older combinations. **System-wide FFmpeg linking requires both PyTorch ≥2.10 and TorchCodec ≥0.10**; those versions can use `sudo apt install ffmpeg` on Ubuntu/Debian or `brew install ffmpeg` on Apple Silicon. For older Torch combinations, use conda FFmpeg instead. The guide says conda normally installs FFmpeg 8.X; if an encoder is missing or TorchCodec/library versions conflict, check `ffmpeg -encoders` and optionally install `conda install ffmpeg=7.1.1 -c conda-forge`. That fallback is conditional, not a universal version pin. On macOS Intel and Linux armv7l, the documented PyAV fallback avoids the TorchCodec FFmpeg requirement. Jetson aarch64/CUDA uses CPU video decoding by default; the cited JetPack 6.2 CUDA source-build container is community maintained rather than a guarantee for every Jetson image. [Pinned video/platform branches](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/installation.mdx).

Inside WSL, the pinned guide adds `conda install evdev -c conda-forge` for the conda route. Its uv route requires `sudo apt install libevdev-dev` followed by `uv pip install evdev`; the guide scopes that uv environment path to PyTorch ≥2.10. USB forwarding and device permissions still need to expose the real interfaces to that environment. A source build may need CMake, a compiler, Python headers, pkg-config and FFmpeg development libraries. Resolve encoder and library compatibility before collecting a large dataset; package resolution alone does not verify video capture or decoding. [Installation and build troubleshooting](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/installation.mdx).

On Linux, grant the operator access to the actual serial and video devices through the distribution's device groups or device-specific policy, then reconnect the session if group membership changed. The upstream tutorial shows a temporary world-writable serial permission command; a persistent installation should use its administrator's access policy. On macOS, allow camera access and, when needed, Accessibility/Input Monitoring for global keyboard listeners. Recording control-flow keys have a terminal fallback at this pin; keyboard-based robot teleoperation has different backend requirements. [USB setup instructions](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx), [recording keyboard behavior](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx).

After identifying the real devices, define a small session configuration. The paths below are **examples to replace**, and camera index 0 is valid only if discovery identifies the intended camera:

```bash
export FOLLOWER_PORT='/dev/ttyACM0'
export LEADER_PORT='/dev/ttyACM1'
export FOLLOWER_ID='wr101-follower-01'
export LEADER_ID='wr101-leader-01'
export SO101_CAM_INDEX=0
export CAMERAS='{"front":{"type":"opencv","index_or_path":0,"width":640,"height":480,"fps":30}}'
export DATASET_ID='local/so101-cube-v1'
export DATASET_ROOT="$PWD/data/so101-cube-v1"
export TRAIN_DEVICE='cuda'
```

`local/...` is a local dataset identifier convention in these examples; it is not an owned Hub account. The commands explicitly disable uploads. If uploading later, use an actual authorized user or organization namespace. Set `TRAIN_DEVICE` to an available supported device, not automatically to `cuda` on every host. Keep the same follower/leader IDs, calibration, units, camera name, resolution and task wording through recording and deployment. A USB device path can change without changing the physical arm's identity. [Dataset record config](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/dataset.py), [dataset read config](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/default.py), [imitation tutorial](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx).

### Motor identification and bus wiring <a href="#so101-motor-setup" id="so101-motor-setup"></a>

#### Identify each adapter before programming

Connect one adapter at a time and run `lerobot-find-port`; disconnect only its USB cable when the prompt requests it, then reconnect. Label the detected adapter and port as leader or follower. Repeat for the other adapter. On macOS a result may resemble `/dev/tty.usbmodem...`; on Linux it may resemble `/dev/ttyACM...` or another device name. Do not copy the tutorial's example serial numbers. Discovery identifies the interface, not whether the motor chain has correct IDs. [Official port-discovery procedure](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx).

Use the adapter's **B / USB channel for both Waveshare jumpers**, as specified in the assembly troubleshooting instructions. Each arm is its own three-wire daisy chain: adapter → ID 1 → ID 2 → ID 3 → ID 4 → ID 5 → ID 6. Follow the actual connector markings; do not invent pin order from cable colors. Route the cable with slack at each pivot and without trapping it beneath a holder or horn. Keep leader and follower DC domains separate. [Motor setup and cabling](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx).

#### Assign one motor at a time

Do this before completing the daisy chains. The setup script assumes the requested motor is the **only** motor electrically connected to that adapter. New motors can share ID 1, so connecting all six at once creates an ambiguous programming situation. For the leader, first label each servo by the gearing table so the requested logical joint receives the correct physical variant.

With the correct supply connected and one loose, supported motor ready, start the corresponding command. Do not run both commands against one adapter:

```bash
lerobot-setup-motors \
  --robot.type=so101_follower \
  --robot.port="$FOLLOWER_PORT"
```

```bash
lerobot-setup-motors \
  --teleop.type=so101_leader \
  --teleop.port="$LEADER_PORT"
```

The default prompt order is **gripper 6, wrist\_roll 5, wrist\_flex 4, elbow\_flex 3, shoulder\_lift 2, shoulder\_pan 1**. At each prompt, isolate that motor, check its three-pin lead, power and USB, then confirm. As an engineering handling precaution, remove servo DC power while changing a motor cable and restore it before confirming the prompt. Keep the adapter's USB connection intact so the port remains available. The script searches supported baud rates, changes ID and baud rate, then verifies the motor answers with its expected model. The bus default at this pin is **1,000,000 bit/s**. Both sides can use IDs 1–6 because they are separate buses. [Setup CLI](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_setup_motors.py), [actual setup/search implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py).

**Expected result:** each named motor is reported with its assigned ID, and the setup script finishes without a missing/wrong-model error. Label the motors after programming. Only then connect each six-motor chain. Replacing a servo or borrowing it from another robot can require this setup again; changing the USB port alone does not require reprogramming IDs. Do not use motor setup as a way to repair an unknown power or cable fault.

### Complete mechanical assembly <a href="#so101-mechanical-assembly" id="so101-mechanical-assembly"></a>

The following sequence rewrites the pinned official joint instructions, preserving their fastener sizes and counts. It is for the SO-101 structure; SO-100 gear-removal instructions are not applicable. Sort the M2×6 mm case screws, M3×6 mm horn/structure screws, horns, holders and leader/follower-specific parts before starting. The package chart does not provide a complete fastener inventory or tightening torque, so the per-step counts below are not a claim about the number of spare screws shipped. Use suitable small Phillips drivers; the hardware README recommends sizes #0 and #1. [Assembly sections “Clean Parts” through “Gripper / Handle”](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx), [hardware tools note](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/README.md).

1. Remove print supports and loose residue, particularly around motor pockets, screw seats and moving interfaces. Test that a motor fits without splitting or distorting a holder. Do not enlarge a critical seat simply to force a misprinted part into service.
2. Have the assigned motor and one three-pin lead ready at every joint. The official guide recommends installing a cable once a motor is placed, before access is obstructed by later parts.
3. Assemble the common base-to-wrist structure using the correct motor at each numbered location. Where the instructions call for upper and lower horns, the upper horn gets its retaining M3×6 mm screw; the lower horn has no separate retaining screw in that step.
4. Choose the follower jaw or leader handle/trigger finish. Their wrist-end parts differ; do not install two follower grippers merely because the first five joints look similar.

| Stage                            | Assembly actions and fastener allocation                                                                                                                                                                                                                                                                                          | Inspection before the next stage                                                                                 |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| **Joint 1: base / shoulder pan** | Fit both horns; retain the top horn with **1 × M3×6**. Seat motor 1 in the base. Use **4 × M2×6** for the motor, two from above and two from below. Slide on the first motor holder and use **2 × M2×6**, one each side. Attach the shoulder piece to the horns with **4 × M3×6 above + 4 below**. Add the shoulder motor holder. | Base motor is seated squarely; both sides of the shoulder attachment are secured; cable exits remain accessible. |
| **Joint 2: shoulder lift**       | Fit both horns and the top retaining **M3×6**. Insert motor 2 from above; secure its case with **4 × M2×6**. Join the upper arm to the horns with **4 × M3×6 on each side**.                                                                                                                                                      | Correct 1/345 leader motor is here; the upper arm rotates without rubbing or pulling its cable.                  |
| **Joint 3: elbow flex**          | Fit both horns and top retaining **M3×6**. Insert motor 3 and use **4 × M2×6**. Attach the forearm with **4 × M3×6 per side**.                                                                                                                                                                                                    | Forearm attachment is symmetric and the cable is outside the pinch path.                                         |
| **Joint 4: wrist flex**          | Fit both horns and top retaining **M3×6**. Position holder 4, slide motor 4 into it and secure with **4 × M2×6**.                                                                                                                                                                                                                 | Holder orientation agrees with the wrist geometry; cabling can flex through the intended travel.                 |
| **Joint 5: wrist roll**          | Seat motor 5 in its wrist holder and use **2 front M2×6** case screws. This motor gets **one horn**, retained by **1 × M3×6**. Connect the wrist structure to motor 4 with **4 × M3×6 on each side**.                                                                                                                             | Wrist roll is free of cable winding and the single-horn arrangement matches the guide.                           |
| **Follower gripper / motor 6**   | Attach the gripper body to motor 5's wrist horn with **4 × M3×6**. Install motor 6 with **2 × M2×6 on each side**. Fit its two horns, retaining the upper one with **1 × M3×6**. Attach the moving claw using **4 × M3×6 per side**.                                                                                              | Jaw motion does not trap the cable; fixed and moving jaw parts are the follower versions.                        |
| **Leader handle / motor 6**      | Attach the leader holder to the wrist with **4 × M3×6**. Fit the handle with **1 × M2×6**. Install motor 6 using **2 × M2×6 per side**, then its horn with **1 × M3×6**. Attach the trigger with **4 × M3×6**.                                                                                                                    | Handle and trigger are secure and move without binding; the C046 motor occupies the trigger joint.               |

The videos are useful for spatial orientation that a fastener table cannot convey: [joint 1](https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint1_v2.mp4), [joint 2](https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint2_v2.mp4), [joint 3](https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint3_v2.mp4), [joint 4](https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint4_v2.mp4), [joint 5](https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Joint5_v2.mp4), [follower gripper](https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Gripper_v2.mp4) and [leader handle](https://huggingface.co/datasets/huggingface/documentation-images/resolve/main/lerobot/Leader_v2.mp4). These are Hugging Face's official linked media. The textual assembly instructions were read; these videos were not frame-by-frame audited for an exact delivered kit revision.

After assembly, clamp both bases to a firm bench, check all case and horn screws, verify the correct adapter mounting plate, and move unpowered/supported joints slowly to inspect clearance. Confirm the ID 1-to-6 chain and remove any cable tension at the wrist. Calibration establishes software coordinates; it cannot repair a cracked holder, loose horn, wrong gearing or a cable that reaches its physical limit first.

### Homing, travel calibration and saved identity <a href="#so101-calibration" id="so101-calibration"></a>

SO-101 calibration at this pin is a **manual homing-offset and travel measurement**, not an automatic search for external home switches. The five arm joints and the gripper must express compatible physical poses on leader and follower. The CLI connects the device first, then calls calibration; as described earlier, follower connection itself configures and can enable the motors. Start with supported links in a controlled rest configuration and no payload. [Calibration CLI](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_calibrate.py), [follower calibration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py), [bus calibration implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py).

Calibrate each device separately, using the stable names chosen above:

```bash
lerobot-calibrate \
  --robot.type=so101_follower \
  --robot.port="$FOLLOWER_PORT" \
  --robot.id="$FOLLOWER_ID"
```

```bash
lerobot-calibrate \
  --teleop.type=so101_leader \
  --teleop.port="$LEADER_PORT" \
  --teleop.id="$LEADER_ID"
```

1. If a saved calibration exists, the program offers to reuse it. Pressing Enter writes that saved file back to the motors with torque off; type **`c`** to collect a new calibration. Reuse only a file belonging to this physical mechanism and horn arrangement.
2. Follow the displayed homing diagram and place the joints around the middle of their usable travel. The current source diagram depicts the upper arm upright with the forearm extending horizontally; the objective is the prescribed common reference, not “all raw encoders equal zero.” Support the mechanism before confirming.
3. The bus disables torque, selects position mode, establishes directions and writes half-turn homing offsets. Move the prompted joints **one at a time** across the actual usable range. Include the gripper's opening and closing travel without forcing the jaw or stretching cables.
4. **`wrist_roll` is excluded from measured range collection** at this pin: it receives the model's full encoder range, 0 to resolution−1. That does not make twisting a camera cable through repeated full turns acceptable. The other ranges must have distinct minimum and maximum values; an unmoved joint can cause calibration to fail.
5. Confirm to finish. The device writes the collected offset/limit values, saves its file and reports the file path. Support the arm as the command exits and torque is removed. Repeat on the other arm.

The driver stores `id`, `drive_mode`, `homing_offset`, `range_min` and `range_max` per motor. IDs are not written by `write_calibration()`; motor setup is a separate operation. At this pin, default file locations use the generic implementation names: `${HF_LEROBOT_CALIBRATION}/robots/so_follower/<id>.json` and `${HF_LEROBOT_CALIBRATION}/teleoperators/so_leader/<id>.json`. The usual calibration root is `~/.cache/huggingface/lerobot/calibration`, unless the Hugging Face/LeRobot environment or an explicit `calibration_dir` changes it. Use the **path actually printed by your pinned installation**, particularly when migrating older `so101_*` examples. [Robot base and file reuse](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/robot.py), [teleoperator base](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/teleoperators/teleoperator.py), [cache constants](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/utils/constants.py).

**Expected result:** both devices have six named calibration records, each measured joint has a real travel interval, and corresponding leader/follower poses produce compatible joint values. A replaced motor, reindexed horn, changed mechanical stop or altered gripper requires reassessment and usually fresh calibration. Back up the file and note the physical arm, servo variants, commit and date; copying an unrelated file merely to suppress a calibration prompt invalidates the coordinate contract.

#### Position units and limits

The reviewed configurations default to **`use_degrees=true`** for both devices. The five body joints use degrees around their calibrated range midpoint; **gripper remains a calibrated 0–100 coordinate**. With `use_degrees=false`, body joints use −100 to +100 normalized travel instead. Do not mix these settings between demonstration, replay, training and deployment, or assume old datasets use the current default. [Follower config](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/config_so_follower.py), [leader config](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/teleoperators/so_leader/config_so_leader.py).

The STS3215 definition has resolution **4096**. The current LeRobot degree conversion uses `(raw − midpoint) × 360 / (resolution−1)`, so its denominator is **4095**. This is the implementation's coordinate conversion, not an arm accuracy claim. Range normalization clips to calibrated min/max, whereas the degree conversion itself does not apply that same clipping in software. `max_relative_target` can bound the change from measured position, globally or per joint; it defaults to **None**, adds a position read, and is neither a collision model nor an independently enforced speed limit. [Normalization and target implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py), [follower action handling](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py), [SDK servo definition](https://github.com/pollen-robotics/rustypot/blob/7aa85e13143594ea4fd4ed9f29e3e29d39b5de85/src/servo/feetech/sts3215.rs).

### Camera discovery, mounting and frame contract <a href="#so101-camera" id="so101-camera"></a>

The kit supplies one 2 MP RGB camera. Start with one fixed `front` view; the two-camera wrist/top examples in the general LeRobot tutorial are optional configurations, not additional included cameras. Verify the camera separately before enabling the follower:

```bash
lerobot-find-cameras opencv \
  --output-dir outputs/so101-camera-check \
  --record-time-s 2
```

The actual command discovers devices **and attempts to capture images**; it is not just an enumeration call. Inspect the saved images to distinguish the kit camera from a laptop webcam. Update `SO101_CAM_INDEX` and the `index_or_path` inside `CAMERAS` together. Device numbering can change after reconnection or reboot. The example 640×480 at 30 fps is a requested operating profile to verify, not a guaranteed mode inferred from “2 MP.” [Camera discovery guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/cameras.mdx), [discovery CLI](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_find_cameras.py).

For a camera-only Python check, prerequisites are the selected available camera, installed camera dependencies and a permitted capture device; no motor application should run. This original example opens no serial port:

```python
import os
from lerobot.cameras.opencv import OpenCVCamera, OpenCVCameraConfig

cfg = OpenCVCameraConfig(
    index_or_path=int(os.environ["SO101_CAM_INDEX"]),
    width=640, height=480, fps=30,
)
with OpenCVCamera(cfg) as camera:
    frame = camera.async_read(timeout_ms=1000)
    print(frame.shape, frame.dtype)
```

**Expected result:** a correctly framed, focused RGB image with shape `(480, 640, 3)` and `uint8` data for this configuration. Keep the object, jaw and goal visible, mount the camera rigidly, avoid strong shadows/reflections, and retain the same view between dataset capture and evaluation. Changing camera mounting, focus or lighting can change the learned observation distribution even when the dataset keys still match. [Camera placement and API](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/cameras.mdx), [OpenCV configuration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/cameras/opencv/configuration_opencv.py).

| Frame method                  | Contract at this pin                                               | Consequence                                                                                                                         |
| ----------------------------- | ------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------- |
| `read()`                      | Hardware read; can block                                           | Do not infer a hard real-time deadline from a requested FPS.                                                                        |
| `async_read(timeout_ms=...)`  | Waits for an unconsumed background frame, bounded by timeout       | Useful for a standalone fresh-frame check; handle `TimeoutError`.                                                                   |
| `read_latest(max_age_ms=...)` | Immediately peeks at the newest buffered frame; rejects stale data | The SO follower uses this path, with OpenCV's default **500 ms** age limit; successive control ticks can see the same camera frame. |

OpenCV output defaults to RGB, with selectable color mode, rotation, warmup, FOURCC and backend. A non-four-character FOURCC is rejected. Unsupported capture settings or unexpected image dimensions can fail connection/processing rather than silently producing the requested image. Changing rotation also changes the effective image contract. Keep matching names and dimensions in `observation.images.front` throughout the policy pipeline. The API index does not fully spell out `read_latest`; the actual camera implementation and camera guide were checked as well. [Camera guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/cameras.mdx), [OpenCV implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/cameras/opencv/camera_opencv.py), [API index](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/api/cameras.mdx).

An optional **32×32 mm UVC wrist mount** in the hardware repository uses four M2 camera screws plus two M3×8 screws and two M3 nuts, with a printed adapter. Its procedure removes motor 6, inserts nuts in the wrist recesses, reinstalls the motor, attaches the adapter and then the module. The guide suggests 40% infill for that adapter and manually focusing its example camera. This is **not verified as the supplied WOWROBO camera's exact footprint or focus mechanism**, and the extra mounting hardware is not established by the package chart. Check fit before buying or printing a mount; any horn or mechanical change needs calibration review. [SO-101 optional mount instructions](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/Optional/SO101_Wrist_Cam_Hex-Nut_Mount_32x32_UVC_Module/README.md).

### First observable result and controlled teleoperation <a href="#so101-first-result" id="so101-first-result"></a>

Aim first for a valid pair of calibrated joint streams and a camera preview, followed by a short, unloaded leader-to-follower movement. This does not require a trained policy, Hub login or a published dataset.

1. Complete the BOM/power check, isolated ID setup, mechanical inspection and separate calibrations above. Confirm two distinct serial paths and an inspected camera image.
2. Put leader and follower in compatible physical poses with the jaw clear. Give one operator control of both DC supplies and keep every other serial program closed. Follower connection can enable torque; normal disconnection can release it.
3. If bus identity is still uncertain, use the raw-read diagnostic in the API section first. It reports raw counts and does not issue target writes. Do not substitute uncalibrated raw counts for degrees.
4. Run the bounded teleoperation command below. Move only a small shoulder-pan amount first, then inspect each joint separately. Check that the corresponding follower joint follows with the expected direction and that the camera view remains useful.
5. Finish within the defined interval, support the follower as torque is disabled, and investigate any incorrect direction, discontinuity, noise or missing joint before recording demonstrations.

```bash
lerobot-teleoperate \
  --robot.type=so101_follower \
  --robot.port="$FOLLOWER_PORT" \
  --robot.id="$FOLLOWER_ID" \
  --robot.use_degrees=true \
  --robot.cameras="$CAMERAS" \
  --teleop.type=so101_leader \
  --teleop.port="$LEADER_PORT" \
  --teleop.id="$LEADER_ID" \
  --teleop.use_degrees=true \
  --fps=30 \
  --teleop_time_s=10 \
  --display_data=true
```

**Expected result:** the viewer shows the selected camera, six joint values are available, and the follower tracks small movements of the matching leader joints without hitting stops or pulling cables. The command ends after approximately ten seconds of loop time and releases resources. This is an expected commissioning observation, **not a result measured for this document**. The CLI defaults to 60 fps, so this example explicitly selects 30 to align with the later dataset. Both loops still need measured timing validation. [Teleoperation tutorial](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx), [actual CLI fields and lifecycle](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_teleoperate.py).

For initial motion commissioning, a carefully selected per-joint `robot.max_relative_target` can reduce a target jump, but choose it in the current units and inspect its effect. Do not present an arbitrary scalar as a validated safe limit for every joint. Resolve calibration and matching-pose errors instead of relying on a clip to conceal them. The recording caveat below matters if clipping is used.

### Recording demonstrations and dataset integrity <a href="#so101-recording" id="so101-recording"></a>

Recording requires the successful motion check, fixed camera, consistent units, an intentional task and a **fresh** local destination. The leader owns follower motion during recording and during reset intervals. A keyboard shortcut changes the data-collection flow; it is not a safety-rated power stop. Keep the physical workspace supervised. The current `lerobot-record` requires a teleoperator and does **not** accept a policy as an alternative controller. [Record CLI](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_record.py), [imitation tutorial](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx).

This original local-only starter records five short demonstrations. It keeps the exact dataset name with `no_stamp=true`, so choose a new path/name if it already exists:

```bash
lerobot-record \
  --robot.type=so101_follower \
  --robot.port="$FOLLOWER_PORT" \
  --robot.id="$FOLLOWER_ID" \
  --robot.use_degrees=true \
  --robot.cameras="$CAMERAS" \
  --teleop.type=so101_leader \
  --teleop.port="$LEADER_PORT" \
  --teleop.id="$LEADER_ID" \
  --teleop.use_degrees=true \
  --dataset.repo_id="$DATASET_ID" \
  --dataset.root="$DATASET_ROOT" \
  --dataset.no_stamp=true \
  --dataset.single_task='Pick the cube and place it in the tray.' \
  --dataset.fps=30 \
  --dataset.num_episodes=5 \
  --dataset.episode_time_s=20 \
  --dataset.reset_time_s=10 \
  --dataset.streaming_encoding=true \
  --dataset.encoder_threads=2 \
  --dataset.push_to_hub=false \
  --display_data=true
```

The durations, five-episode count and thread count are example choices, not a trained-policy performance promise. At 30 fps, a full 20-second episode nominally contains about 600 frames; early stops or loop timing alter the actual count. A small dataset first establishes acquisition quality. The official tutorial suggests roughly 50 demonstrations across several object locations as an initial learning exercise; task complexity and diversity determine whether that is enough. Keep successful trajectories consistent before widening variation. [Data collection guidance](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx).

| Recording control / field | Behavior and practical implication                                                                      |
| ------------------------- | ------------------------------------------------------------------------------------------------------- |
| Right arrow or `n`        | Ends the current episode or reset phase early.                                                          |
| Left arrow or `r`         | Discards/re-records the current episode.                                                                |
| Escape or `q`             | Stops the session and enters finalization/cleanup; upload depends on configuration.                     |
| `dataset.episode_time_s`  | Recording duration per episode; source default 60 s.                                                    |
| `dataset.reset_time_s`    | Unrecorded reset period; default 60 s. The teleoperator still drives the follower.                      |
| `dataset.num_episodes`    | Number to collect in this invocation; default 50, including on resume as an additional count.           |
| `dataset.no_stamp`        | Default false appends `_YYYYMMDD_HHMMSS` to the ID at creation. Resume preserves the existing full ID.  |
| `dataset.push_to_hub`     | Default true. The examples override it to false. A local dataset can later be deliberately uploaded.    |
| `dataset.private`         | `None` defers to Hub/organization behavior; request true explicitly when creating a private repository. |

Recording flow keys work with the source's terminal fallback on Wayland/headless/SSH when launched in an interactive focused terminal. This is distinct from driving a robot with keyboard teleoperation, which still needs the appropriate global input backend. If keys do nothing, inspect terminal focus/TTY and permissions before assuming the dataset has stopped. [Recording keyboard section](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx), [shared dataset defaults](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/dataset.py).

#### Encoding, cadence and what “action” means

Streaming encoding avoids writing a PNG sequence before video encoding and makes episode saves quicker, but adds ongoing encoder work and bounded queues. At this pin `streaming_encoding` defaults false, queue capacity defaults 30 frames per camera, image-writer processes default 0 and image-writer threads default 4 per camera. Start modestly and measure; more threads can contend with the control loop. RGB codec settings are nested under `dataset.rgb_encoder`: documented defaults include `libsvtav1`, `yuv420p`, GOP 2 and CRF 30; `vcodec=auto` selects an available hardware encoder with fallback. Do not assume FFmpeg on every host includes the same codecs. [Dataset defaults](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/dataset.py), [encoding parameters](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/video_encoding_parameters.mdx).

Video feature metadata combines properties probed from the encoded stream (codec, pixel format, dimensions and FPS) with encoder settings such as GOP, CRF, preset and extra options. It is populated from the **first episode**: changing encoding settings midway through a recording is unsupported and can make that metadata misleading. When merging video datasets, codec, pixel format, dimensions and FPS must agree. Tuning fields such as GOP/CRF/preset may be set to null, or extra options to an empty object, when sources disagree; that warning is not equivalent to re-encoding every input into one uniform stream. Keep these settings stable or make a deliberate, separately validated conversion. [Video metadata and merge rules](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/video_encoding_parameters.mdx).

Read the per-episode and whole-run cadence summaries before trusting timestamps. The recorder paces toward the configured FPS, but dataset time is derived from frame index. If the machine achieves 25 Hz while the metadata declares 30 Hz, playback represents the motion faster than its real execution. The summary breaks down observation, processing, teleoperation, sending, recording and pacing headroom. High observation time points toward camera acquisition; high recording time points toward image/encoder work. Correct sustained overruns before expanding the dataset. [Cadence explanation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx).

**Source-level action caveat:** in the reviewed `record_loop`, `robot.send_action()` returns `_sent_action`, but the saved action frame is built from the earlier **`action_values`** after the teleoperator processor. The returned value is not used for that frame. Thus a follower's internal `max_relative_target` clipping can make logged targets differ from targets actually applied by the driver, despite an adjacent source comment suggesting otherwise. The state stream is measured joint position, not proof that every target was reached. Avoid systematically clipped demonstrations; inspect target/state tracking, and if an application requires applied-action labels, implement and validate that logging contract explicitly rather than assuming the CLI already does it. This finding is based on source inspection, not a hardware capture. [Record loop “send” and “record” blocks](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_record.py), [follower `send_action`](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py).

#### Resume without mixing incompatible sessions

To append, rerun the matching recording command with `--resume=true`, the existing full ID, the same `dataset.root`, and the number of **additional** episodes. For example, `num_episodes=5` adds five rather than bringing the total to five. Resume checks robot type, FPS and feature schema. It does not establish that the same physical camera view, horn positions, object placement or operator behavior was used. Do not delete an existing dataset just to make a command succeed; choose a new version when the acquisition contract changed. [Resume implementation and compatibility check](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_record.py), [compatibility helper](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/common/control_utils.py).

### Dataset format, inspection and editing <a href="#so101-dataset-inspection" id="so101-dataset-inspection"></a>

LeRobotDataset v3 separates logical episodes from physical files. Numeric frames are in Parquet, camera streams are MP4, and metadata describes boundaries and locations. Several episodes can share one file, so manually deleting “an episode video” by filename can damage unrelated data. [Dataset v3 guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/lerobot-dataset-v3.mdx).

| Location / API                 | Information to preserve                                                                 |
| ------------------------------ | --------------------------------------------------------------------------------------- |
| `meta/info.json`               | Feature schema, shapes/dtypes, FPS, version and data/video path templates.              |
| `meta/stats.json`              | Feature statistics used by policy normalization.                                        |
| `meta/tasks.parquet`           | Task strings and their integer indices.                                                 |
| `meta/episodes/`               | Per-episode lengths, tasks and offsets in chunked Parquet.                              |
| `data/`                        | Frame-level numerical Parquet shards.                                                   |
| `videos/`                      | Camera-specific MP4 shards.                                                             |
| `observation.state` / `action` | Ordered joint vectors; inspect the metadata `names`, not an assumed alphabetical order. |
| `observation.images.front`     | The camera key generated from this reference's `front` configuration.                   |

Inspect before replaying or training. The following opens stored data only and does not connect a robot:

```bash
lerobot-dataset-viz \
  --repo-id "$DATASET_ID" \
  --root "$DATASET_ROOT" \
  --mode local \
  --episode-index 0
```

The visualization command uses **hyphenated** options such as `--repo-id` and `--episode-index`, unlike the dotted dataclass options of recording. A Foxglove viewer is available with `--display-mode foxglove`; Rerun is the default. Hub-hosted datasets can also be viewed in the [LeRobot Dataset Visualizer](https://huggingface.co/spaces/lerobot/visualize_dataset), including supported 3D previews. A 3D preview is a software rendering, not physical replay or evidence of mechanical repeatability. [Dataset tools guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/using_dataset_tools.mdx), [actual visualization parser](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_dataset_viz.py).

This original API inspection reads the first stored frame and reports the action ordering. Run only after the recording writer has finalized:

```python
import os
from lerobot.datasets import LeRobotDataset

data = LeRobotDataset(
    os.environ["DATASET_ID"],
    root=os.environ["DATASET_ROOT"],
    episodes=[0],
)
print(data.num_episodes, data.num_frames, data.fps)
print(data.features["action"]["names"])
sample = data[0]
print(sample["observation.state"].shape, sample["action"].shape)
print(sample["observation.images.front"].shape)
```

**Expected result:** a nonempty episode, six-element state/action vectors for this configuration, and an image tensor in channel-first form. Verify the actual six names, camera view, task label, timestamps, beginning/end poses and action/state continuity. Loaded image tensor dtype and scale depend on reader options such as `return_uint8`; camera NumPy RGB arrays and policy input tensors are not interchangeable by shape alone. [Dataset constructor and item API](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/datasets/lerobot_dataset.py), [v3 load examples](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/lerobot-dataset-v3.mdx).

`lerobot-edit-dataset` provides deletion, episode splits, merges, feature removal, task modification, image-to-video conversion, re-encoding, statistics and information workflows. Adding a feature is available through the Python dataset-tools API. Use new output datasets for curation where supported and retain originals. **`modify_tasks` is explicitly in-place and ignores `new_repo_id`/`new_root`** in the reviewed guide, so a new-name flag is not a backup mechanism for that operation. Merge requires identical feature schemas; matching six-joint dimensions alone does not prove matching units or calibration. [Dataset tools operations and warnings](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/using_dataset_tools.mdx).

For larger projects, `delta_timestamps` requests temporal windows, `StreamingLeRobotDataset` supports Hub streaming, and the training config supports `dataset.streaming=true`. Image augmentation is a **training-time** transform, not a modification of recorded raw images. GPU augmentation is optional and requires an accelerator. v2.1-to-v3 conversion and the optional Lance reader are separate migration/storage paths, not required for this kit's first dataset. Preserve the original dataset and review those source sections before using them. [Dataset v3 operations and migration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/lerobot-dataset-v3.mdx).

### Replay and controlled reproducibility <a href="#so101-replay" id="so101-replay"></a>

Replay is an **actuator workflow**, unlike dataset visualization. Before it starts, the operator must verify the dataset's actual joint names and ordering, degree/normalized convention, gripper range, calibration provenance, FPS, collision-free path and compatible initial physical pose. An episode from an arbitrary SO-101 Hub dataset is not automatically transferable to this kit. Only the replay process should own the follower serial port; stop teleoperation and recording first. Keep the follower unloaded for the first check.

```bash
lerobot-replay \
  --robot.type=so101_follower \
  --robot.port="$FOLLOWER_PORT" \
  --robot.id="$FOLLOWER_ID" \
  --robot.use_degrees=true \
  --dataset.repo_id="$DATASET_ID" \
  --dataset.root="$DATASET_ROOT" \
  --dataset.episode=0
```

The actual implementation selects the episode's `action` column, reconstructs the target dictionary from its stored names, obtains observations and sends actions through the robot action processor. It paces using **`dataset.fps` from the loaded dataset**. Although `DatasetReplayConfig` declares an `fps` field, the reviewed replay loop does not use that field to change playback rate; do not offer it as an established speed override. The source does not establish a general collision-aware approach to the first target. [Replay CLI source](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_replay.py).

**Expected result:** the unloaded arm repeats a comparable joint trajectory at the dataset's rate and the process disconnects after the episode. Actual repeatability must be measured; a visually similar replay does not establish a payload or accuracy specification. An unexpected first movement, direction or gripper action calls for inspecting the data/units/calibration before another run.

### ACT training, checkpointing and offline evaluation <a href="#so101-training" id="so101-training"></a>

Training uses recorded files and does not need an energized arm. Stop all hardware applications and disconnect arm power during this compute-only phase. Inspect and curate the dataset first; confirm GPU/MPS availability, a working video decoder and adequate storage. A source pin does not guarantee a particular accelerator driver or wheel is usable. ACT is a practical first workflow here because the pinned official documentation recommends it and includes it in LeRobot. No success rate or training duration is asserted for this kit. [ACT guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/act.mdx), [installation guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/installation.mdx).

ACT predicts a chunk of future joint targets from image/state observations. Its reviewed defaults include one observation step, a 100-step prediction chunk, 100 action steps per chunk, ResNet-18 visual backbone, VAE training enabled and mean/std normalization for visual/state/action inputs. These defaults explain why frame rate, feature names and saved statistics matter. They do not turn a degree-valued dataset into radians or make a different camera view equivalent. Temporal ensembling is optional; this pin requires `n_action_steps=1` when it is enabled, and action steps must not exceed chunk size. [ACT configuration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/policies/act/configuration_act.py).

This local training example deliberately disables Hub pushes and remote experiment tracking. Ten thousand steps and batch size eight are an example budget to adjust after inspecting data, memory and loss; they are not an established convergence requirement:

```bash
lerobot-train \
  --dataset.repo_id="$DATASET_ID" \
  --dataset.root="$DATASET_ROOT" \
  --policy.type=act \
  --policy.device="$TRAIN_DEVICE" \
  --policy.push_to_hub=false \
  --output_dir=outputs/train/so101-act-v1 \
  --job_name=so101-act-v1 \
  --batch_size=8 \
  --steps=10000 \
  --save_freq=2000 \
  --save_checkpoint_to_hub=false \
  --trackio.enable=false
```

The trainer defaults to 100,000 steps and saves every 20,000 if not overridden. Estimate the amount of repeated data exposure as approximately `steps × batch_size / training_frames`; this is an engineering budgeting approximation, not a source claim of an exact epoch schedule for every sampler. More steps do not repair bad action labels, frozen video or a calibration mismatch. A new run refuses an existing output directory rather than overwriting it. [Train pipeline defaults/validation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/train.py), [training tutorial](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx).

Checkpoints appear under `outputs/train/so101-act-v1/checkpoints`; the `last/pretrained_model` directory supplies model/config/processor resources for deployment. For a true resume, use the stored training configuration and `resume=true`:

```bash
lerobot-train \
  --config_path=outputs/train/so101-act-v1/checkpoints/last/pretrained_model/train_config.json \
  --resume=true
```

A resumed run restores training state; fine-tuning a checkpoint on a changed dataset is a different operation using `policy.path` and a new output directory. If using Hub data, record the dataset revision as well as the code and policy revision. Hub training uploads require an actual `policy.repo_id` when `push_to_hub` is enabled. Remote `job.target` workflows can upload local-only data and create model repositories; they are an explicit optional cloud workflow, not a drop-in substitute for the local-only recipe. [Resume resolution and validation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/train.py), [local/cloud workflow documentation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx).

For a sufficiently large multi-episode dataset, hold out episodes using `dataset.eval_split` and enable periodic loss evaluation with `eval_steps`; the source requires `eval_split>0` when `eval_steps>0`, and this split is incompatible with streaming mode. For example, adding `--dataset.eval_split=0.2 --eval_steps=1000` requests an episode-held-out loss check. Keep related trials together where necessary to avoid an overly easy split. Falling training or held-out loss is not a measured physical task success rate. The separate `lerobot-eval` workflow is for configured simulation environments; it does not automatically score the real SO-101 bench task. [Dataset split validation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/default.py), [training evaluation fields](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/train.py).

Optional Trackio local logging uses `trackio.enable=true` and can be viewed with `trackio show --project lerobot`. Hosted Space logging has separate credentials, privacy and console-capture settings; current training examples use Trackio rather than blindly reusing older W\&B flags. Keep access tokens outside saved commands and ordinary run logs. [Tracking installation section](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/installation.mdx).

### Deploying a policy and evaluating the real task <a href="#so101-policy-evaluation" id="so101-policy-evaluation"></a>

Policy deployment begins only after the physical operator checks the exact trained observation/action contract, restores the matching camera position/lighting, reuses the correct calibration ID, confirms an achievable initial pose and clears the complete anticipated motion path. Stop the leader teleoperation and recording processes; **the rollout is the follower's sole command owner**. Start unloaded, bound the run duration and keep a separate means of removing servo power. The device's torque behavior and disconnect behavior still apply.

At the reviewed pin, **`lerobot-rollout` deploys policies**. `lerobot-record` collects teleoperator demonstrations. This original short ACT example loads the local checkpoint and records no evaluation dataset:

```bash
lerobot-rollout \
  --strategy.type=base \
  --inference.type=sync \
  --policy.path=outputs/train/so101-act-v1/checkpoints/last/pretrained_model \
  --robot.type=so101_follower \
  --robot.port="$FOLLOWER_PORT" \
  --robot.id="$FOLLOWER_ID" \
  --robot.use_degrees=true \
  --robot.cameras="$CAMERAS" \
  --task='Pick the cube and place it in the tray.' \
  --fps=30 \
  --duration=10 \
  --device="$TRAIN_DEVICE" \
  --return_to_initial_position=false \
  --display_data=true
```

The default duration is **0, meaning unbounded**, so the example explicitly sets ten seconds. The default `return_to_initial_position=true` requests additional shutdown motion; the example disables it to make the end state intentional, after which the operator must support the links before normal torque-off disconnection. Neither choice is universally safe for every loaded task. A camera/command failure can prevent normal return, and software shutdown is not a guarantee of immediate physical immobility. [Deployment guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/inference.mdx), [actual rollout config](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/configs.py).

**Expected result:** the checkpoint loads against the six-joint and `front` image schema, actions execute for the bounded run, and timing/status information is available. Measure completion independently: define success (for example, the cube fully inside the tray), fixed trial initial states, timeout and failure categories before comparing checkpoints. Record attempts, successes, collisions/near misses, grasp losses, run duration and checkpoint/calibration/camera provenance. A camera display or fluent-looking movement alone is not task completion. These evaluation criteria are engineering guidance, not results claimed by the official demonstration video.

#### Recording evaluation episodes

The following three-trial recipe intentionally returns to the startup pose between episodes. Inspect that entire return path before launch. The policy is the only follower controller; no leader is connected by this command. During each ten-second reset interval, reset the objects only after the arm has returned and the workspace is accessible:

```bash
lerobot-rollout \
  --strategy.type=episodic \
  --strategy.reset_to_initial_position=true \
  --policy.path=outputs/train/so101-act-v1/checkpoints/last/pretrained_model \
  --robot.type=so101_follower \
  --robot.port="$FOLLOWER_PORT" \
  --robot.id="$FOLLOWER_ID" \
  --robot.use_degrees=true \
  --robot.cameras="$CAMERAS" \
  --dataset.repo_id=local/rollout_so101-act-v1 \
  --dataset.root=outputs/data/rollout-so101-act-v1 \
  --dataset.no_stamp=true \
  --dataset.push_to_hub=false \
  --dataset.single_task='Pick the cube and place it in the tray.' \
  --dataset.fps=30 \
  --dataset.num_episodes=3 \
  --dataset.episode_time_s=20 \
  --dataset.reset_time_s=10 \
  --fps=30 \
  --device="$TRAIN_DEVICE" \
  --return_to_initial_position=false \
  --display_data=true
```

**Expected result:** up to three logical policy episodes and their observations/actions are saved locally, with reset phases between trials and no automatic success score. Dataset inspection can then open the resulting folder. This expectation assumes successful model loading, hardware operation and writer finalization; none were executed here. [Actual strategy fields](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/configs.py), [episode/reset implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/strategies/episodic.py).

Use `strategy.type=episodic` for discrete recorded policy trials, with a fresh ID such as `local/rollout_so101-act-v1`. Supply a fresh root, `dataset.no_stamp=true` if managing names yourself, `dataset.push_to_hub=false` for local-only storage, matching `dataset.fps=30`, the task string, episode count, episode duration and reset duration. Otherwise the creation path timestamps the dataset name. Do not combine base strategy with `dataset.*`: base declares no dataset and rejects those flags. [Strategy validation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/configs.py), [deployment strategies](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/inference.mdx).

Episodic reset behavior deserves its own physical plan. With no teleoperator, **`strategy.reset_to_initial_position` defaults true**, so the arm can move toward its captured initial position between trials. With a leader, smooth handover may actuate the leader to match the follower before allowing manual reset. The prose statement that an omitted leader “holds its position” is not a blanket promise that no reset motion occurs; the current strategy configuration and implementation must be considered. Use a clear, inspected reset path and keep hands away during powered handover. [Episodic configuration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/configs.py), [episodic implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/strategies/episodic.py).

| Strategy / backend | Appropriate use and boundary                                                                                                                                                             |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `base`             | Autonomous execution without a dataset; useful for a short initial check.                                                                                                                |
| `episodic`         | Bounded recorded trials with reset phases; right/left/Escape controls affect trial flow.                                                                                                 |
| `sentry`           | Continuous recording with automatically selected episode boundaries and upload cadence; boundaries do not inherently reset policy state.                                                 |
| `highlight`        | Memory-bounded ring buffer; default `s` saves/toggles an event and `h` requests upload. Blocking saves have explicit inference-pause handling.                                           |
| `dagger`           | Supervised policy/leader handover and correction collection; requires a compatible teleoperator and a dataset.                                                                           |
| `sync` inference   | Default; control waits for policy computation. Suitable starting path for ACT, subject to measured timing.                                                                               |
| `rtc` inference    | Asynchronous chunking for compatible VLA policies; not an assumption that ACT needs or supports every RTC feature. Validate usable horizon, queue/freshness deadlines and hold behavior. |
| `remote` inference | Separate policy server and client contract; requires its own optional dependencies and deployment review. Not configured by the local ACT recipe.                                        |

`interpolation_multiplier=N` increases robot command frequency to `fps×N`; policy action and dataset frequency remain `fps`. It smooths interpolation but does not create new independent observations or remove inference latency. Cadence summaries distinguish policy cycles from interpolated ticks. SO follower position hold retains the last applied targets, including the gripper; it can continue settling and is not a guarantee of a retained grasp. [Deployment timing and waiting behavior](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/inference.mdx), [thread-safe hold implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/robot_wrapper.py).

Interactive base/sentry sessions can use `--interactive=true`; `/start` begins a segment, `/reset` requests a return/reset, and `/stop` ends the session. Connecting still configures hardware before `/start`, so “waiting for start” should not be interpreted as electrically inactive. `/subtask` affects policies with language conditioning; ACT does not acquire language-following capability from a task string. Text questions, autosteering and external planners require their documented model capabilities and additional review. [Interactive and programmatic deployment](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/inference.mdx).

### Human correction, retraining and control transfer <a href="#so101-hil" id="so101-hil"></a>

HIL is optional and follows a working base policy and a proven ordinary teleoperation setup. Both buses and the leader workspace must be under the same physical operator's supervision: the SO-101 leader has active motors, and **a pause/handover can move it under power**. No second teleoperation process should run alongside DAgger. Use the same camera/features/FPS and calibration as the original demonstrations. [HIL requirements and protocol](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/hil_data_collection.mdx), [leader feedback methods](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/teleoperators/so_leader/so_leader.py).

For a reviewed configuration, start from the rollout hardware/policy fields above and select `strategy.type=dagger`, add the leader type/port/ID, a fresh `rollout_...` dataset/root, matching `dataset.fps`, task and episode limit, and deliberately chosen upload settings. The default is corrections-only; `strategy.record_autonomous=true` also records autonomous frames. The official default controls are:

1. Observe autonomous behavior, then press **Space** to pause before a recoverable failure.
2. Allow the powered leader-to-follower matching/handover to complete with hands clear.
3. Press **Tab** while paused to take control. The leader becomes free to guide; demonstrate a clean recovery and completion. These correction frames are recorded.
4. Press **Tab** to end the correction and **Space** to resume autonomous control. Do not start another controller to “help” the handover.
5. Use **Escape** to end the session. In corrections-only mode each correction becomes an episode. Enter requests upload; treat that as an external-data operation, not a pause key.

The `intervention` feature marks human frames. Before merging HIL corrections with ordinary demonstrations, reconcile this extra feature and ensure identical robot/camera/FPS schemas. The official workflow removes `intervention` into a new dataset, then merges with the demonstration dataset and fine-tunes from `policy.path` into a new output directory. Preserve the original correction labels for audit even if the derived training dataset omits them. This is an iterative deploy → inspect failures → collect corrections → curate → fine-tune cycle, not evidence that every intervention automatically improves performance. [HIL merge/fine-tune procedure](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/hil_data_collection.mdx), [dataset tools](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/using_dataset_tools.mdx).

### Python and SDK resource contracts <a href="#so101-api-contracts" id="so101-api-contracts"></a>

Use the current public packages rather than copying old import paths from unrelated versions. The following contracts were checked in actual pinned source, not inferred solely from the API index:

| Resource              | Verified entry points and responsibilities                                                                                                                                                                                                                                                             |
| --------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Follower              | `from lerobot.robots.so_follower import SO101Follower, SO101FollowerConfig`; config includes port, ID/calibration directory, cameras, units, target bound, disconnect torque behavior and read retries. `connect`, `calibrate`, `get_observation`, `send_action`, `disconnect` are the main lifecycle. |
| Leader                | `from lerobot.teleoperators.so_leader import SO101Leader, SO101LeaderConfig`; `get_action()` produces the six `.pos` keys. `send_feedback`, `enable_torque`, `disable_torque` support powered handover.                                                                                                |
| Generic serial bus    | `from lerobot.motors import SerialMotorsBus, Motor, MotorNormMode`; model definitions resolve through rustypot. `connect()` performs model/firmware handshake; direct bus connection is different from robot-level configuration.                                                                      |
| Position reads/writes | `read` / `sync_read` default to normalization for position fields; pass `normalize=False` for raw register values. `write` waits for an acknowledgement; `sync_write` does not obtain a response from each motor.                                                                                      |
| Calibration           | `setup_motors()` handles IDs/baud; `record_calibration()` measures offsets/ranges; `write_calibration()` writes supported homing/limit registers; the device saves the file. These are different persistence operations.                                                                               |
| Camera                | `OpenCVCameraConfig`, `OpenCVCamera`; context-manager cleanup or `finally` is required. Hardware frames are H×W×3 arrays, while dataset/policy image tensors have their own convention.                                                                                                                |
| Dataset               | `from lerobot.datasets import LeRobotDataset`; `create`/`resume` open a writer, `add_frame` needs the full schema and task, `save_episode` commits a logical episode, `clear_episode_buffer` discards it, `finalize` closes writers before reading/pushing.                                            |
| Policy deployment     | `lerobot.rollout` exposes configuration/context/strategy/controller APIs; `build_rollout_context` loads the policy and connects hardware. `RolloutController` supports start/reset/stop/task operations and requires a `LinkedEvent`; teardown remains the caller's responsibility.                    |

[Follower](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py), [leader](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/teleoperators/so_leader/so_leader.py), [motor bus](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py), [dataset implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/datasets/lerobot_dataset.py), [camera API](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/api/cameras.mdx), [deployment API](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/inference.mdx).

Both leader and follower `configure()` call the shared `configure_motors()` with its defaults. At this pin it writes **Return\_Delay\_Time=0**, **Maximum\_Acceleration=254** where that register exists, and **Acceleration=254** where supported. Return delay uses 2 µs units, so 0 means 0 µs; the source describes the factory value as 250 (500 µs), without establishing the delivered kit’s current readback. The acceleration values are raw register settings, not verified physical acceleration units or safe motion limits. For STS3215, configuration also reads `Phase` and clears bit 4 if set to keep positions within the encoder range. The follower additionally writes position PID coefficients **P=16, I=0, D=32**. These writes occur within the torque lifecycle described in the control-ownership section; invoking robot connection is therefore different from opening a read-only bus. [Shared bus defaults](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py), [leader configuration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/teleoperators/so_leader/so_leader.py), [follower configuration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py). Gripper-specific raw protection writes are **Max\_Torque\_Limit=500, Protection\_Current=250, Overload\_Torque=25**. These are source configuration values, not measured torque/current limits for a delivered kit; do not relabel the raw register numbers as newtons, amps or a universal safe grip force. `num_read_retries=2` is the follower/leader default, meaning two extra read attempts, not a physical fault cure. [Driver configuration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py), [bus configuration](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py), [SDK register definitions](https://github.com/pollen-robotics/rustypot/blob/7aa85e13143594ea4fd4ed9f29e3e29d39b5de85/src/servo/feetech/sts3215.rs).

#### Read-only raw bus diagnostic

Prerequisites: the motor setup is already complete, the six-ID chain and correct supply are checked, the mechanism is supported, and no other program owns the follower port. This diagnostic intentionally avoids robot `connect()`, configuration writes and target writes. It uses raw positions without a calibration file and closes the port with `disable_torque=False` so cleanup does not itself issue a torque-disable command. It therefore also **does not make an already energized mechanism safe**; the operator retains responsibility for its existing state.

```python
import os
from lerobot.motors import Motor, MotorNormMode, SerialMotorsBus

names = (
    "shoulder_pan", "shoulder_lift", "elbow_flex",
    "wrist_flex", "wrist_roll", "gripper",
)
bus = SerialMotorsBus(
    port=os.environ["FOLLOWER_PORT"],
    motors={name: Motor(i, "sts3215", MotorNormMode.DEGREES)
            for i, name in enumerate(names, start=1)},
)
try:
    bus.connect()
    print(bus.sync_read("Present_Position", normalize=False))
finally:
    bus.disconnect(disable_torque=False)
```

**Expected result:** six named raw position counts or an explicit connection/model/firmware/read error. No numeric output is fabricated here. The counts are not degrees, not wrist Cartesian coordinates and not a voltage-variant identification. A successful sync write in another application would not establish successful motion because sync writes do not return per-motor acknowledgement. [Bus lifecycle/read/write implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py).

`FeetechMotorsBus` is a **deprecated compatibility alias** at this pin; its optional `protocol_version` argument is ignored. Use `SerialMotorsBus` for new pinned examples. The lower-level rustypot `Sts3215PyController` typed angle accessors use physical-angle conversions, while generic named register access gives decoded integers and the LeRobot wrapper applies its own calibration/normalization. Do not pass a raw register count, controller-radian value and LeRobot-degree value interchangeably. The reviewed SDK defines 4096-step STS3215 resolution, little-endian register handling and sign-magnitude encoding for several position/speed/offset fields. No hand-built packet encoder is needed for this workflow. [Deprecated shim](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/feetech/feetech.py), [SDK APIs](https://github.com/pollen-robotics/rustypot/blob/7aa85e13143594ea4fd4ed9f29e3e29d39b5de85/README.md), [servo encoding declarations](https://github.com/pollen-robotics/rustypot/blob/7aa85e13143594ea4fd4ed9f29e3e29d39b5de85/src/servo/feetech/sts3215.rs).

For a custom application, use bounded loops, record the action actually returned by the driver when that is the intended label, and place resource cleanup in `finally`. With policy strategies, preserve their motion-permission, observation freshness and hold/teardown contracts; a home-written background loop should not bypass those contracts. The current public `lerobot.inference` package owns backend scheduling, while `lerobot.rollout` owns robot execution/recording. [Deployment extension contracts](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/inference.mdx).

### Troubleshooting and maintenance decisions <a href="#so101-troubleshooting" id="so101-troubleshooting"></a>

#### Firmware mismatch and official update route

If the current handshake reports mixed firmware, first rule out incorrect motor IDs/models and consult the kit supplier about the intended versions. Firmware updating is a separate maintenance operation, not a required step for every new kit. Before using the following Windows procedure, stop every LeRobot/debugging process, give the updater sole ownership of the adapter, use the correct motor supply and support the mechanism without a payload:

1. Obtain the **FD debugging software** from the [official Feetech software page](https://www.feetechrc.com/software.html). The reviewed LeRobot tutorial specifies Windows for firmware updates; no particular current FD release or firmware image is certified here.
2. Connect the motor control board by USB and provide stable servo DC power. Confirm the actual COM port in Device Manager and the bus baud rate; a previously configured LeRobot chain normally uses 1 Mbit/s.
3. Open that connection in FD, search for devices and check each discovered ID against the intended motor. Select the individual motor to maintain.
4. In its upgrade interface, query the online update, inspect the proposed version/model match and start the upgrade only when that match has been established.
5. Keep USB and DC power uninterrupted until the updater finishes. Read back the reported version and repeat deliberately for any other required motors.
6. Close FD before returning to LeRobot. Recheck IDs, baud and calibration, then perform the unloaded joint check before restoring a task or dataset workflow. An update is not proof that configuration/calibration stayed suitable.

The tutorial links **FT\_SCServo\_Debug\_Qt** for Linux/macOS debugging and parameter adjustment; it explicitly reserves firmware upgrading for official Windows software. The hardware README links a different fork, so neither fork is presented as an interchangeable firmware updater. Their installation/build paths and downloaded executables were not tested. [Pinned firmware procedure and limitations](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/feetech.mdx), [hardware debugging links](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/README.md).

| Symptom                                         | Checks and corrective path                                                                                                                                            | Source basis / limit                                                                                                                                                                                                                                                                                                                                                                               |
| ----------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| No serial device                                | Test the data cable, adapter USB connection, host permissions and port discovery one adapter at a time. Recheck after reconnect/reboot.                               | USB identification in [assembly](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx). A visible port alone does not prove servo power.                                                                                                                                                                                                     |
| Setup finds no motor                            | Check correct DC adapter, three-pin lead and B/USB jumper positions; isolate only the prompted motor.                                                                 | [Assembly setup troubleshooting](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx). Do not keep changing IDs on a whole ambiguous chain.                                                                                                                                                                                                 |
| Wrong/missing model or firmware mismatch        | Confirm actual labels, IDs, baud and chain connections. A borrowed/replacement motor may need isolated setup; obtain firmware compatibility guidance before flashing. | [Handshake/setup code](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py). A model match does not identify 5 V versus 12 V hardware.                                                                                                                                                                                           |
| Incorrect status packet / intermittent reads    | Inspect connectors, cable strain, supply stability and competing serial software. The current configs allow two extra read attempts.                                  | [Follower config](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/config_so_follower.py), [leader config](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/teleoperators/so_leader/config_so_leader.py). Repeated retries can hide timing problems; they do not repair wiring. |
| Calibration gives equal min/max                 | Move every prompted measured joint through real travel; check a stuck/bound joint. Wrist roll is handled separately.                                                  | [Range and full-turn logic](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py). Do not invent endpoints to bypass the check.                                                                                                                                                                                                   |
| Calibration prompt unexpectedly returns         | Confirm stable device ID, actual calibration path and matching motor register values. Review horn/motor changes.                                                      | [Robot base](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/robot.py), [driver calibration check](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py).                                                                                                    |
| Joint follows the wrong axis/direction or jumps | Stop, inspect gear placement, motor IDs, horn indexing, pose reference and `use_degrees` on both sides.                                                               | [Assembly](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx), [normalization](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/motors/motors_bus.py). A clip is not a substitute for calibration.                                                                                        |
| Arm drops on exit                               | Default disconnect removes torque. Support the mechanism before exit and plan a rest pose.                                                                            | [Follower disconnect](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/robots/so_follower/so_follower.py). Setting torque retention changes behavior but is not a general safe shutdown solution.                                                                                                                                                  |
| Unexpected leader movement                      | HIL/episodic handover can actuate the leader; ordinary leader free motion does not establish it will remain unpowered in every workflow.                              | [HIL protocol](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/hil_data_collection.mdx), [leader feedback](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/teleoperators/so_leader/so_leader.py).                                                                                                |
| Camera black, wrong device or busy              | Run camera discovery/capture separately; inspect saved images; close other camera users and check OS camera permission.                                               | [Camera guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/cameras.mdx), [find-cameras source](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_find_cameras.py).                                                                                                             |
| Camera rejects profile / stale frames           | Request a supported width/height/FPS/FOURCC, inspect actual capture, reduce USB load and check background-thread errors.                                              | [OpenCV checks and 500 ms default stale limit](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/cameras/opencv/camera_opencv.py). Do not disable dimension validation to conceal a contract mismatch.                                                                                                                                              |
| Dataset is slow or disk fills                   | Begin with one 640×480 view; inspect cadence, encoder availability, queue/thread contention and free storage.                                                         | [Encoding](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/video_encoding_parameters.mdx), [cadence](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx). The camera's 2 MP label is not a requirement to record at maximum resolution.                                               |
| Recording keys ineffective                      | Use an interactive focused terminal; try `n/r/q`; distinguish recording control from keyboard teleoperation permissions.                                              | [Keyboard behavior](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx). Keys are not a power isolator.                                                                                                                                                                                                                                |
| Existing dataset/output error                   | Choose a fresh version or use the proper resume path/count. Keep matching schema, units and camera placement.                                                         | [Recording](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_record.py), [training validation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/train.py). Do not delete useful data as a routine fix.                                                                     |
| Dataset cannot load after interruption          | Inspect saved episode metadata/video and whether writers finalized. Preserve the folder before recovery/curation.                                                     | [v3 finalize requirement](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/lerobot-dataset-v3.mdx), [dataset API](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/datasets/lerobot_dataset.py). No universal corruption repair is asserted.                                                       |
| Replay speed seems wrong                        | Check actual recorded cadence versus declared FPS. The current replay uses stored FPS, not its unused config FPS field.                                               | [Replay implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/scripts/lerobot_replay.py), [cadence explanation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx).                                                                                                        |
| Training lacks package/decoder support          | Confirm active environment, source pin, extras and FFmpeg/TorchCodec/PyAV compatibility.                                                                              | [Installation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/installation.mdx). Base install alone is not the complete workflow.                                                                                                                                                                                                                |
| GPU out of memory / slow data loading           | Reduce batch size, inspect camera resolution and decoding workers, check device availability and augmentation path.                                                   | [Train/default configs](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/configs/train.py), [dataset v3](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/lerobot-dataset-v3.mdx). No fixed VRAM guarantee is established.                                                                         |
| Policy fails with familiar-looking hardware     | Compare exact camera keys/view, image dimensions, action ordering/units, calibration and dataset statistics; evaluate dataset quality before increasing steps.        | [ACT config](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/policies/act/configuration_act.py), [imitation workflow](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx).                                                                                                            |
| Rollout resets or moves after a trial           | Distinguish startup pose, episodic reset, leader handover and final `return_to_initial_position`; inspect each selected setting.                                      | [Rollout config](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/configs.py), [episodic source](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/rollout/strategies/episodic.py).                                                                                                         |

Before each session, inspect clamps, printed-part cracks, horn/case screws, connector seating and cable bending at moving joints. With DC disconnected and links supported, replace a failed servo with the correct **voltage and gearing for that exact joint**; isolate it for ID/baud setup, reinstall the horn/structure, recalibrate and repeat the small unloaded joint check. A source model string is not an adequate replacement-part specification. The vendor notes servos are wear items and specifically suggests keeping follower spares; it does not supply a measured replacement interval. [Vendor service note](https://shop.wowrobo.com/products/so-arm101-diy-kit-assembled-version-1.js), [assembly](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx).

### Replacement prints, CAD, simulation and technical resources <a href="#so101-downloads" id="so101-downloads"></a>

The unassembled kit already supplies printed parts. The following upstream fabrication information is useful for repairs or deliberate changes, not a requirement to reprint a good kit. The hardware README recommends PLA+, 15% infill, either a 0.4 mm nozzle / 0.2 mm layer or a 0.6 mm nozzle / 0.4 mm layer. Its printing-service instructions instead request 20% infill; those are different documented contexts, not proof of a single mandatory factory recipe. Configure supports as directed, keep horizontal screw holes clear, test the servo/Lego gauges and remove supports before assembly. [Printing instructions](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/README.md), [printing-service guide](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/3DPRINT.md).

For a pair, common parts are needed for **both arms**. The individual-file list includes base, base motor holder, base/wrist motor holders, under/upper arm, rotation pitch, wrist roll pitch and the matching adapter plate. Leader-specific parts are handle, trigger and leader wrist roll; follower-specific parts are moving jaw and follower wrist roll. Choose one Waveshare or Seeed plate per arm to match its actual board. **`SO101 Assembly.stl` is a reference assembly, not a printable single component.** [Individual parts](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/README.md), [service preparation notes](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/3DPRINT.md).

| Resource                                                                                                                                                                                                                                                                                                                                                                                             | What it contains / model boundary                                                                                                                                                                  |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Pinned hardware repository](https://github.com/TheRobotStudio/SO-ARM100/tree/141aea7bcac2744d92998e30268c413202a56f96)                                                                                                                                                                                                                                                                              | SO-101 mechanical sources alongside older SO-100 material. Stay in the SO101 directories.                                                                                                          |
| [SO101 individual STL directory](https://github.com/TheRobotStudio/SO-ARM100/tree/141aea7bcac2744d92998e30268c413202a56f96/STL/SO101/Individual)                                                                                                                                                                                                                                                     | Replacement component meshes and alternative adapter plates. Inspect dimensions/fit before fabrication.                                                                                            |
| [Follower plate files](https://github.com/TheRobotStudio/SO-ARM100/tree/141aea7bcac2744d92998e30268c413202a56f96/STL/SO101/Follower) and [leader plate files](https://github.com/TheRobotStudio/SO-ARM100/tree/141aea7bcac2744d92998e30268c413202a56f96/STL/SO101/Leader)                                                                                                                            | Combined oriented print plates. README specifies Ender 220×220 mm and Prusa/UP 205×250 mm choices; the tree also lists A1 mini plate files.                                                        |
| [SO101 STEP directory](https://github.com/TheRobotStudio/SO-ARM100/tree/141aea7bcac2744d92998e30268c413202a56f96/STEP/SO101)                                                                                                                                                                                                                                                                         | Editable component CAD and `SO101 Assembly.step`; no CAD import, tolerance or mating analysis was performed for this reference.                                                                    |
| [Gauges](https://github.com/TheRobotStudio/SO-ARM100/tree/141aea7bcac2744d92998e30268c413202a56f96/STL/Gauges)                                                                                                                                                                                                                                                                                       | Servo-fit and Lego-size tests for checking a printer before full plates.                                                                                                                           |
| [SO101 simulation directory](https://github.com/TheRobotStudio/SO-ARM100/tree/141aea7bcac2744d92998e30268c413202a56f96/Simulation/SO101)                                                                                                                                                                                                                                                             | URDF/MJCF-related resources and meshes. Simulation properties are not measured kit performance.                                                                                                    |
| [Simulation conventions README](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/Simulation/SO101/README.md)                                                                                                                                                                                                                                                | New middle-of-range zero versus old fully horizontal zero; some base collision meshes were removed. The gripper's LeRobot 0–100 convention is not fully represented by the current model geometry. |
| [SO-101 wrist camera mount](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/Optional/SO101_Wrist_Cam_Hex-Nut_Mount_32x32_UVC_Module/README.md)                                                                                                                                                                                                             | Optional 32×32 module adapter; extra M3 hardware and exact camera fit must be checked.                                                                                                             |
| [Compliant gripper](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/Optional/Compliant_Gripper/README.md)                                                                                                                                                                                                                                                  | Optional TPU 95A replacement jaw/body, documented 20% print infill and supports; changes grasp behavior and needs fresh task validation.                                                           |
| [Pinned assembly/calibration text](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/so101.mdx)                                                                                                                                                                                                                                                       | All joint steps, IDs, gearing, setup and manual calibration; associated videos linked above.                                                                                                       |
| [Pinned LeRobot metadata](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/pyproject.toml)                                                                                                                                                                                                                                                                       | Python/dependency bounds, extras and actual console command registration.                                                                                                                          |
| [Pinned rustypot 1.13.1](https://github.com/pollen-robotics/rustypot/blob/7aa85e13143594ea4fd4ed9f29e3e29d39b5de85/README.md)                                                                                                                                                                                                                                                                        | Transport, typed controller and generic bus API; not a standalone commissioned arm controller.                                                                                                     |
| [LeRobot workflow](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/il_robots.mdx), [camera guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/cameras.mdx), [deployment guide](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/inference.mdx) | Recording, learning, inference and runtime contracts corresponding to the source pin.                                                                                                              |
| [Dataset API](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/docs/source/api/datasets.mdx) and [implementation](https://github.com/huggingface/lerobot/blob/c2a086e24fa20911bf060ee5cffbc0e1dbfd96ad/src/lerobot/datasets/lerobot_dataset.py)                                                                                                                  | Writer/reader operations, metadata and stored-frame access.                                                                                                                                        |

The simulation README specifically warns that the leader trigger's zero, provisional 0–45° travel and printed-part inertia estimates were derived from geometry rather than a measured leader, and that no leader MJCF counterpart is supplied there. Its gripper note does not make LeRobot's 0–100 value a literal linear displacement unit. Align simulation/model conventions with the current calibration before using kinematics. Optional 4040 base hardware is listed by the main README for SO100/101, but its own installation README explicitly describes an **SO-100 base**; SO-101 fit is not independently established here. Tactile sensors, depth cameras, a second RGB camera, mobile bases and dual-follower systems are additions, not contents of this selected kit. [Simulation caveats](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/Simulation/SO101/README.md), [4040 instructions](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/Optional/4040_Base_Mount/README.md), [optional hardware listing](https://github.com/TheRobotStudio/SO-ARM100/blob/141aea7bcac2744d92998e30268c413202a56f96/README.md).

### Source reconciliation and validation limits <a href="#so101-source-boundaries" id="so101-source-boundaries"></a>

| Topic                               | Resolved interpretation / remaining limit                                                                                                                                                                                       |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Generic BOM versus vendor kit       | Generic upstream follower can be 7.4 V class; vendor Package 2 specifies six C018 12 V followers and 12 V/8 A + 5 V/6 A supplies. Actual delivered labels remain the commissioning check.                                       |
| Software version drift              | CLI/config examples are pinned to the reviewed 0.7.1 source commit. Older `lerobot.common...` or `FeetechMotorsBus` examples and older Python requirements are not silently mixed into it.                                      |
| Recording documentation             | One current tutorial command repeats `--robot.cameras` with two different values. This reference supplies one coherent, one-camera dictionary rather than depending on duplicate-argument behavior.                             |
| Logged target versus applied target | Actual record source saves teleoperator-processed `action_values`, not `_sent_action` returned by the follower. Clipped targets can therefore be mislabeled if treated as applied-action ground truth.                          |
| Replay FPS                          | Declared config FPS is not the loop's playback-rate source; the loaded dataset's FPS is used.                                                                                                                                   |
| Episodic reset prose                | “Hold” prose is bounded by the actual default reset-to-start setting and optional powered leader handover.                                                                                                                      |
| Calibration state                   | Files/commands were source-checked; no actual six-motor register readback, horn alignment, calibration or transfer between two kits was tested.                                                                                 |
| Camera fit/capability               | Package chart establishes one advertised 2 MP camera, not its sensor/USB mode table or compatibility with every optional mount.                                                                                                 |
| Mechanical ratings                  | No manufacturer-backed kit payload/reach/repeatability/continuous-duty rating was found in the reviewed sources. Shipping measurements and servo stall torque remain separately labeled.                                        |
| Resource access                     | Official raw documentation/code, store/vendor product data and the package chart were accessible. Assembly videos are linked but not fully audited; CAD/STL/URDF files were inventoried, not imported, fabricated or simulated. |

Validation here consists of source/config/API inspection, original-example syntax checks and document consistency checks. It does not certify a functioning installation, physical safety, dataset quality, learned performance or production deployment.

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Verified the exact OpenELAB SKU and WowRobo Package2 chart, includingC018 follower motors and the two supplies. Read the current SO-101 guide, hardware BOM, and pinned motor-bus/follower/configuration source. The package image was visually inspected.

The original report passed Python syntax parsing. No installation, serial query, EEPROM setup, calibration, teleoperation, camera test, training or hardware execution was run. No arm payload, precision or task-success result is asserted. Related assembled/parts-only options remain distinct references rather than assumed equivalents.
