---
description: >-
  Read Star Arm102 encoder angles before follower motion; distinguish mechanical
  and SDK ranges, origins, UART IDs and 12 V power.
---

# Seeed Studio Star Arm 102 Leader Arm Development Guide

{% hint style="info" %}
[**View Seeed Studio Star Arm 102 for reBot B601-DM/RS on OpenELAB**](https://openelab.io/products/seeed-studio-rebot-arm-b601-dm-leader-arm)

**Model:** Star Arm 102 / reBot Arm 102 leader · **SKU:** `Seeed-100004723` · **Scope:** encoder-only leader; follower and optional 12 V / 2 A supply are separate.
{% endhint %}

## Product overview <a href="#product-role-and-scope" id="product-role-and-scope"></a>

Star Arm 102 converts an operator's hand-guided joint movement into teleoperation input for a reBot B601 follower. The product name and SDK use **Star Arm 102** and **reBot Arm 102** for this leader. It does not provide the follower's motors, drive power or a ready-to-run autonomous policy. [Exact manufacturer model](https://www.seeedstudio.com/Star-Arm-102-p-6765.html).

The same SKU may appear as a selectable accessory on a B601 bundle listing. That makes it another purchasing route for the leader, not evidence that the follower includes it. This page preserves the existing standalone OpenELAB URL. [Seeed Studio wiki hub](./).

## Applications

Use the leader to inspect joint mapping, practice teleoperation and capture demonstrations after the follower is commissioned. For data work, keep leader/follower origins, direction mapping and camera geometry unchanged across episodes. A hand-guided encoder device can be validated with the follower disconnected, which isolates serial and mapping problems before any powered follower motion.

The end-to-end loop includes leader polling, mapping, CAN command/state exchange and rendering. The documented 60 Hz configuration gives a calculated 16.7 ms cycle budget; it does not establish a measured USB latency or servo bandwidth. Record actual loop timing under the intended camera/host load. [Hardware and teleoperation course](https://wiki.seeedstudio.com/robotics/paper_reading_hardware_and_teleoperation/).

## Specifications

| Parameter                         | Star Arm 102 manufacturer value            |
| --------------------------------- | ------------------------------------------ |
| Mechanism                         | 6 joints + gripper input                   |
| Supply option                     | 12 V / 2 A, XT30                           |
| Reach                             | 420 mm                                     |
| Weight                            | 663 g                                      |
| Servos                            | Encoder-only                               |
| Angle sensor                      | 12-bit magnetic encoder                    |
| Recommended operating temperature | 0–40 °C                                    |
| Host path                         | USB-C serial connection in the Seeed setup |
| SDK serial default                | 1,000,000 baud, current leader integration |

Hardware values: [Seeed exact-product specification](https://www.seeedstudio.com/Star-Arm-102-p-6765.html). Serial default: [leader configuration source](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102/blob/main/lerobot_teleoperator_rebot_arm_102/config_rebot_arm_102_leader.py). A 12-bit encoder provides 4096 nominal codes per revolution; the calculated 0.0879° step is a quantization interval, **not a measured angular accuracy**.

### Mechanical travel versus configured teleoperation range

| Physical input | Product's mechanical range |
| -------------- | -------------------------- |
| Joint0         | ±120°                      |
| Joint1         | ±163°                      |
| Joint2         | 0° to 270°                 |
| Joint3         | ±88°                       |
| Joint4         | ±66°                       |
| Joint5         | ±168°                      |
| Gripper        | 0° to 336°                 |

Source: [manufacturer mechanical table](https://www.seeedstudio.com/Star-Arm-102-p-6765.html). Do not force the leader to a hard stop to match a software limit. The current plugin has different normalized coordinate ranges and origins:

| SDK joint      | Servo ID | Plugin `joint_ranges`, degrees in its coordinate convention |
| -------------- | -------- | ----------------------------------------------------------- |
| shoulder\_pan  | 0        | −150 to 150                                                 |
| shoulder\_lift | 1        | −1 to 170                                                   |
| elbow\_flex    | 2        | −200 to 1                                                   |
| wrist\_flex    | 3        | −80 to 90                                                   |
| wrist\_yaw     | 4        | −90 to 90                                                   |
| wrist\_roll    | 5        | −130 to 130                                                 |
| gripper        | 6        | 0 to 270                                                    |

[Read configuration source](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102/blob/main/lerobot_teleoperator_rebot_arm_102/config_rebot_arm_102_leader.py). These are software mapping parameters, not replacement mechanical specifications. Check their mapping/zero against the actual leader and follower before using the full range; a clamped value near one end can indicate a coordinate mismatch.

## Hardware and connections

1. Clamp the leader on a rigid flat table and verify that the base does not move under ordinary hand input. Keep its links and cables clear.
2. With supplies off, attach the documented **12 V / 2 A** supply to the leader's power connector and a USB-C data cable to the host. Match actual polarity/connector markings; the USB connection is not proof of correct external power.
3. Label the leader's actual serial port and SN. Prefer `/dev/serial/by-id/` on Linux where available; `/dev/ttyUSB0` is an example that can change after a reboot or replug.
4. Keep the follower disconnected during initial angle reading. Later commission its separate [B601-DM](rebot-b601-dm-development-guide.md) or [B601-RS](rebot-b601-rs-development-guide.md) power/control path first. DM is 24 V and RS is 48 V; neither supply belongs on this leader.

[Official leader wiring and setup](https://wiki.seeedstudio.com/rebot_arm_b601_dm_lerobot/), [RS leader setup](https://wiki.seeedstudio.com/rebot_arm_b601_rs_lerobot/). This is a packaged serial device; no exposed motor connector pinout is invented from a photograph. Disconnect power before changing internal harnesses.

## Software and development resources <a href="#development-software-and-data" id="development-software-and-data"></a>

The current Seeed integration registers **`rebot_arm_102_leader`**, uses `motorbridge-smart-servo` and the `FashionStarServo` API, and maps IDs **0–6**. B601 follower CAN IDs **1–7** are a separate namespace. The plugin package declares Python≥3.10 and LeRobot≥0.4, but your selected LeRobot core may require **Python 3.12** and specific dependency extras. Use the higher requirement and record a compatible set. [Plugin README](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102), [package metadata](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102/blob/main/pyproject.toml).

The product page describes a preassembled unit; the software can still need zero/origin alignment. In the reviewed implementation, explicit `calibrate()` writes origins, while `configure()` unlocks servos and resets multi-turn counters. Even the manufacturer's `read_raw_angles.py` performs initialization writes before polling. The original read-only program below omits those write calls so the first check does not deliberately reset origins/counters. [Implementation source](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102/blob/main/lerobot_teleoperator_rebot_arm_102/rebot_arm_102_leader.py), [vendor raw-angle example](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102/blob/main/examples/read_raw_angles.py).

SenseCraft Robotics is the alternative guided project route. Choose the exact B601 follower model, bind the leader and follower independently, then verify calibration, small-joint teleoperation and cameras before datasets/training. Do not register both historical plugin and newly integrated core classes blindly; inspect the installed CLI help and retain one coherent route.

## Getting started <a href="#getting-started-leader-recognition-before-follower-movement" id="getting-started-leader-recognition-before-follower-movement"></a>

### First result: seven changing leader angles, follower disconnected

1. Secure and power the leader correctly, leave follower drive power disconnected and identify the leader's serial device. Close other programs that own that port.
2. Create an isolated environment and install the focused serial SDK. This does not install or run a follower policy.

```bash
conda create -n openelab-star102 python=3.12 -y
conda activate openelab-star102
python -m pip install motorbridge-smart-servo
python -m pip show motorbridge-smart-servo
python -m pip check
```

3. Save this complete original program as `leader_snapshot.py`. It uses the reviewed API's ping and raw-angle reads; no unlock, origin-write, multi-turn-reset or follower-action call is present. Replace `PORT` in the invocation with the observed leader serial device.

```python
import argparse
import time
from motorbridge_smart_servo import FashionStarServo

parser = argparse.ArgumentParser()
parser.add_argument('port')
args = parser.parse_args()
names = ('shoulder_pan', 'shoulder_lift', 'elbow_flex',
         'wrist_flex', 'wrist_yaw', 'wrist_roll', 'gripper')
with FashionStarServo(args.port, baudrate=1_000_000) as bus:
    missing = [i for i in range(7) if not bus.ping(i)]
    if missing:
        raise SystemExit(f'Missing leader servo IDs: {missing}')
    try:
        while True:
            angles = [bus.read_raw_angle(i, multi_turn=True) for i in range(7)]
            print(','.join(f'{name}={angle:.2f}_deg'
                           for name, angle in zip(names, angles)), flush=True)
            time.sleep(0.25)
    except KeyboardInterrupt:
        pass
```

```bash
python leader_snapshot.py PORT
```

4. Move one input joint slightly while watching the corresponding column, then return to the same pose. Repeat for the gripper. Do not force a joint to the product's full travel.

**Expected result:** all seven IDs respond and the intended column changes smoothly. Raw multi-turn angles can include offsets/wrap history; they need not be zero in the mechanical reference pose. This checks communication and mapping, not absolute calibration, accuracy or follower behavior. No output shown here is a fabricated hardware log.

### Calibrate a coherent LeRobot installation

After leader-only checks, install a supported LeRobot core and the [leader integration](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102) in an isolated environment; record repository commits and `pip freeze`. The manufacturer offers the package name `lerobot-teleoperator-rebot-arm-102`. Inspect `lerobot-calibrate --help` and the plugin config before using it.

1. Put the leader in the manufacturer's zero pose with gripper closed, then run calibration with the **actual** serial path and a unique physical ID:

```bash
lerobot-calibrate --teleop.type=rebot_arm_102_leader \
  --teleop.port=/dev/ttyUSB0 --teleop.id=openelab_star102
```

2. Read the prompt carefully. Reusing an existing calibration and deliberately establishing new servo origins are different actions. Back up the old record before recalibration; do not zero at an arbitrary desk pose.
3. Repeat a small one-joint movement and inspect mapping/range behavior before enabling the follower. If a value stays near a limit, compare raw angles, configured `joint_ranges` and follower direction transforms rather than extending physical travel.

Expected result is a calibration associated with that physical leader and a mapping consistent with its intended zero. The reviewed source uses configured joint ranges; the generic ±90 calibration record text is not a definitive mechanical travel specification. [Calibration implementation](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102/blob/main/lerobot_teleoperator_rebot_arm_102/rebot_arm_102_leader.py).

### Bind the follower and collect data only after correspondence is sound

Use the [DM](https://wiki.seeedstudio.com/rebot_arm_b601_dm_lerobot/) or [RS](https://wiki.seeedstudio.com/rebot_arm_b601_rs_lerobot/) procedure for its actual bus backend, power, motor IDs and origin reference. Before a motion program, support both arms, clear the follower workspace and make drive-power isolation accessible. Compare leader raw readings and follower state before commanding actions; a vendor comparison script can disable follower torque, so support the links before starting it.

The RS SocketCAN example below assumes both systems are already commissioned and `/dev/ttyUSB0`/`can0` are the observed identities:

```bash
lerobot-teleoperate \
  --teleop.type=rebot_arm_102_leader \
  --teleop.port=/dev/ttyUSB0 --teleop.id=openelab_star102 \
  --robot.type=seeed_b601_rs_follower \
  --robot.port=can0 --robot.can_adapter=socketcan --robot.id=openelab_rs
```

Expected result is a small leader movement producing the intended small follower movement with correct sign and scale. Stop at the first wrong joint, jump, stall or loss of communication. A DM serial bridge needs its own documented `damiao` backend and serial port; changing only the model word is insufficient.

For demonstration collection, bind wrist and fixed cameras by actual identity, inspect their views before motion, and record a short local episode with stable task/start/end poses. Review timestamps, gripper visibility, dropped frames and joint correspondence before accumulating training data. The course's repeated object-transfer exercise is a practice target, not a verified success rate for this product. [Hardware/teleoperation course](https://wiki.seeedstudio.com/robotics/paper_reading_hardware_and_teleoperation/), [SenseCraft project route](https://wiki.seeedstudio.com/sensecraft_robotics_rebot_arm_102_b601_rs/).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                                         | Checks and bounded recovery                                                                                                                 |
| ----------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| USB port exists, no angles                      | Confirm leader 12 V supply, serial ownership/permissions, 1 Mbaud setting and IDs0–6. Do not assume the USB cable supplies all electronics. |
| Some columns missing                            | Stop; inspect corresponding harness/ID with power off. Do not broadcast a reset to an unidentified chain.                                   |
| Raw angles move but mapped values do not        | Check configured joint ranges, origin/wrap handling and output normalization before replacing hardware.                                     |
| Follower moves opposite                         | Isolate follower motion; compare leader raw sign, follower observation sign and explicit direction transform.                               |
| Values change after restarting                  | Compare origin/calibration and multi-turn-counter initialization in the exact SDK revision; save raw readings before resetting.             |
| Device names swap                               | Rebind physical serial/CAN identities and use persistent names where available.                                                             |
| Need full follower supply on leader?            | No: leader12 V, DM follower24 V and RS follower48 V are distinct domains.                                                                   |
| Does preassembled mean no software calibration? | Mechanical assembly and software origin alignment are different; inspect and preserve the supplied configuration.                           |

## Downloads and technical documents <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

| Resource                                                                                                                               | Purpose                                                                           |
| -------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------- |
| [Star Arm 102 product PDF](https://files.seeedstudio.com/Bazaar/product_pdf/100004723.pdf)                                             | Official exact-model product document; manufacturer-listed download               |
| [Exact manufacturer product page](https://www.seeedstudio.com/Star-Arm-102-p-6765.html)                                                | Mechanical range, supply and encoder facts                                        |
| [Leader SDK/integration](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102)                                         | MIT-declared plugin, config and examples                                          |
| [Raw-angle example source](https://github.com/Seeed-Projects/lerobot-teleoperator-rebot-arm-102/blob/main/examples/read_raw_angles.py) | Read initialization writes before executing it                                    |
| [B601 follower integration](https://github.com/Seeed-Projects/lerobot-robot-seeed-b601)                                                | DM/RS model/backend and direction mapping                                         |
| [Hardware and teleoperation](https://wiki.seeedstudio.com/robotics/paper_reading_hardware_and_teleoperation/)                          | Host/camera setup and measured-loop interpretation                                |
| [reBot hardware project](https://github.com/Seeed-Projects/reBot-DevArm)                                                               | Hardware/CAD ecosystem; confirm exact leader-specific resource before fabrication |

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November 2026** against the exact product page, current plugin README/config/implementation and the linked Seeed DM/RS tutorials. The source-map's generic teleoperation article was supplemented with the actual Star Arm ordering code and numerical specification. No follower specification was silently assigned to the leader.

**Validation:** source reviewed. Python installation, serial reads, calibration, follower control and hardware tests were **not run**. The original program is an API-reviewed reproduction example, not a claim of verified bench output. Retain actual firmware, SDK commit, origins and results with each physical pair.

### Related retained references

* [SenseCraft Robotics](https://sensecraft.seeed.cc/en/robotics)
