# Seeed SO-101 Pro Servo Motor Kit: assembly and role configuration

{% hint style="info" %}
[**View Seeed Studio SO-101 Pro Servo Motor Kit on OpenELAB**](https://openelab.io/products/seeed-studio-so-101-pro-servo-motor-kit-lerobot)

**SKU:** `Seeed-114993667` · **Selected option:** **Servo Motor Kit Only**. This guide covers motors/electronics for one leader and one follower; printed structure and cameras are separate. Pro operation uses **leader5 V / follower12 V**.
{% endhint %}

### Product overview <a href="#product-and-scope" id="product-and-scope"></a>

The SO-101 Pro motor kit is an assembly starting point, not a ready-mounted robot. Its task is to turn twelve correctly identified serial servos into two separately powered, uniquely addressed six-joint chains, then assemble and calibrate the matching SO-ARM101 structure. After assembly, use the SO-ARM101 Pro commissioning guide for the complete camera/dataset workflow.

The same storefront now offers a **motor kit + printed parts** option. This page's SKU is the motor-only variant, so the presence of that option does not make printed parts or a camera included. [Exact SKU listing](https://openelab.io/products/seeed-studio-so-101-pro-servo-motor-kit-lerobot).

### Applications

Build or repair an SO-101 leader/follower pair for teleoperation, demonstration collection and robot-learning research. The assembly workflow is also useful for identifying a replacement servo without disturbing the other five configured motors.

Choose the physical arm role before assigning IDs. A joint number is reused on the separate leader and follower buses; it is not a globally unique motor identity. Label each servo with role, joint, voltage/gearing and final ID before mounting it in the structure.

### Specifications

#### Kit inventory and joint assignment

| Role / joint                                      | Quantity             | Manufacturer servo/gearing reference                                  | Operating supply in Seeed Pro workflow                    |
| ------------------------------------------------- | -------------------- | --------------------------------------------------------------------- | --------------------------------------------------------- |
| L1 shoulder\_pan, L3 elbow\_flex                  | 2                    | ST-3215-C044,7.4 V family,1:191                                       | **5 V leader**                                            |
| L2 shoulder\_lift                                 | 1                    | ST-3215-C001,7.4 V family,1:345                                       | **5 V leader**                                            |
| L4 wrist\_flex, L5 wrist\_roll, L6 gripper/handle | 3                    | ST-3215-C046,7.4 V family,1:147                                       | **5 V leader**                                            |
| F1–F6                                             | 6                    | STS3215,12 V family,1:345; current tutorial lists C018/C047 options   | **12 V follower**                                         |
| Servo driver boards                               | 2                    | LeRobot bus-servo controller                                          | One separate power/data path per role                     |
| Listed accessories                                | See option inventory | USB-C cables, DC pigtails/power cables, studs/screws and fixing clips | Verify actual supply label/current and connector polarity |

[Seeed motor/joint table](https://wiki.seeedstudio.com/lerobot_so100m_new/), [motor-only inventory](https://openelab.io/products/seeed-studio-so-101-pro-servo-motor-kit-lerobot). The source's generic follower table also mentions7.4 V variants for other editions; do not apply that to the Pro motor-only SKU's six12 V followers. The Basic/Standard kit's all5 V instruction is a different configuration.

_Seeed Studio_ [_original L1–L6/F1–F6 gearing photograph_](https://files.seeedstudio.com/wiki/robotics/projects/lerobot/so101/all_motos.png)_, visually inspected. Read the actual part label/voltage as well as the role annotation._

#### Serial controller and component limits

| Component                   | Numerical fact / exact scope                                                             |
| --------------------------- | ---------------------------------------------------------------------------------------- |
| Bus driver                  | 5–12 V input **dependent on attached servo**; UART/USB modes;42×25 mm reference board    |
| Driver power connector      | 2-pin3.5 mm screw terminal in linked driver reference                                    |
| Servo connector             | 3-pin serial-bus connector; confirm GND/Vcc/signal markings and actual cable orientation |
| STS3215-C0017.4 V datasheet | 4–7.4 V rated input; half-duplex async serial,8 data bits/1 stop/no parity               |
| C001 baud/ID                | 38400–1000000 bit/s configurable;1 Mbit/s default; IDs0–253                              |
| C001 encoder                | 12-bit,4096 nominal codes/revolution; approximately0.088° code step, not system accuracy |
| C001 at7.4 V test condition | 19.5 kg·cm stall torque /2.5 A stall current;5 kg·cm rated load /650 mA rated current    |

[Driver datasheet](https://files.seeedstudio.com/wiki/reComputer-Jetson/lerobot/bus_servo_xiao.pdf), [Feetech C001 A/1 datasheet,23June2023](https://files.seeedstudio.com/wiki/reComputer-Jetson/lerobot/STS3215-C001-20230624.pdf). **The C0017.4 V numbers are not ratings for the Pro12 V follower, nor measurements at the prescribed5 V leader supply.** Stall is not continuous operation. Use the actual fitted follower variant's specification for load/thermal design.

The store's assembled-arm500 g payload reference describes a completed mechanism; it is not a torque guarantee for a motor kit, arbitrary printed frame or every reach/pose.

### Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

#### Separate roles before applying power

Make two labeled trays, **L /5 V** and **F /12 V**. Check every motor's exact model and ratio against the table. Label the two controller boards and supplies to match; a7.4 V-family label on the leader does not override Seeed's5 V operating instruction. Connect controller power through the documented polarity; USB is the host-data path and is not a motor supply.

For host commissioning use the driver board's USB mode. The linked driver document describes solder-jumper changes for UART mode; do not solder those merely because a UART-capable servo is attached. Changing the interface mode can make a good USB setup appear unresponsive. [Bus-servo driver reference](https://files.seeedstudio.com/wiki/reComputer-Jetson/lerobot/bus_servo_xiao.pdf).

#### One unconfigured servo at a time

A chain of factory-default IDs is ambiguous. Configure each unconfigured servo in isolation with its correct supply, then mark the assigned role/joint/ID. At a tool prompt, turn off **motor power** before changing a servo cable, keep fingers clear, and only restore power after checking the connector. Retain the controller's USB identity as required by the tool. Never connect a12 V supply to a chain containing a leader motor.

After configuration, power off and daisy-chain the six servos of **one role**, base/shoulder\_pan first. Connect each bus only to its own controller. Two servo sockets are bus connections, not separate arbitrary PWM channels. Confirm every physical cable's ground/power/signal markings; do not infer pin numbering from a mirrored photograph.

#### Mechanics, print and calibration boundary

Use SO101-specific STL/CAD and gearing. The Seeed print reference recommends PLA+,15% infill and documented support/nozzle settings; those are a reproduction baseline, not proof of strength for every printer/material. Inspect support removal, bearing/horn alignment, fasteners and cable routing before loading the mechanism. Do not force a horn against a motor to compensate for wrong centering. An assembled motor chain still needs whole-arm calibration in its final geometry. [SO101 assembly/print reference](https://wiki.seeedstudio.com/lerobot_so100m_new/).

### Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

Use a coherent LeRobot environment with Feetech support. The source baseline for these commands is Seeed LeRobot commit **`d490e472a5d1a207cfe0255caaaf74b6d66e4656`**, package metadata0.7.1/Python≥3.12. The setup command is implemented in [the pinned SDK](https://github.com/Seeed-Projects/lerobot/blob/d490e472a5d1a207cfe0255caaaf74b6d66e4656/src/lerobot/scripts/lerobot_setup_motors.py); the current generic SO follower maps IDs1–6 to shoulder\_pan, shoulder\_lift, elbow\_flex, wrist\_flex, wrist\_roll and gripper.

| Task                                   | Tool / target                                                     |
| -------------------------------------- | ----------------------------------------------------------------- |
| Identify controller                    | `lerobot-find-port`, one controller at a time                     |
| Configure unconfigured follower motors | `lerobot-setup-motors`, `so101_follower`                          |
| Configure unconfigured leader motors   | `lerobot-setup-motors`, `so101_leader`                            |
| Calibrate assembled geometry           | `lerobot-calibrate`, separate robot/teleop roles and physical IDs |
| Operate/collect data                   | Only after empty-gripper small-motion correspondence is verified  |

LeRobot's Apache-2.0 licensing and the hardware project's own licenses apply to those source files. Original inspection code below is not a copied vendor servo-control implementation. Source review does not imply an installed/tested SDK environment.

### Getting started

#### Configure motor identities

1. Inventory all twelve labels/gears and both supplies before connecting a servo. Keep the motor shaft unloaded and clear. Do not configure an already working assembled arm this way; preserve its existing IDs/calibration.
2. Install the pinned source in an isolated environment:

```bash
conda create -n openelab-so101-build python=3.12 -y
conda activate openelab-so101-build
git clone https://github.com/Seeed-Projects/lerobot.git openelab-so101-sdk
cd openelab-so101-sdk
git checkout d490e472a5d1a207cfe0255caaaf74b6d66e4656
python -m pip install -e '.[feetech,core_scripts]'
python -m pip check
lerobot-find-port
lerobot-setup-motors --help
```

3. Label the observed follower and leader ports. `/dev/ttyACM0` and `/dev/ttyACM1` below are examples, not fixed identities. Prepare the **follower controller with12 V** and start:

```bash
lerobot-setup-motors --robot.type=so101_follower --robot.port=/dev/ttyACM0
```

4. Follow the tool's requested joint order. Connect **only the named motor**, confirm correct part/power, then let the tool assign its ID/baud. Mark it immediately. Turn motor power off before cable changes. Do not daisy-chain until the isolated sequence is complete.
5. Repeat with the separately labeled **leader controller and5 V**:

```bash
lerobot-setup-motors --teleop.type=so101_leader --teleop.port=/dev/ttyACM1
```

**Expected result:** each role has six individually configured/marked servos with IDs1–6 and the specified gearing. The tool completing is not proof that the mechanical arm is assembled or calibrated. Compare the actual labels and assigned IDs before building the chain. [Motor configuration procedure](https://wiki.seeedstudio.com/lerobot_so100m_new/).

#### Original role/gearing inventory check

Create `motor_inventory.json` as an array of12 records containing your **observed** `role` (`L` or `F`), integer `id`, and `ratio` (191,345 or147). Do not fill it from assumptions. Save this original script as `check_inventory.py` and run `python check_inventory.py motor_inventory.json`; it only reads the record.

```python
import json
import sys

records = json.load(open(sys.argv[1], encoding='utf-8'))
expected_leader = {1:191, 2:345, 3:191, 4:147, 5:147, 6:147}
assert len(records) == 12, 'Expected twelve observed motor records'
for role in ('L', 'F'):
    group = [m for m in records if m['role'] == role]
    assert len(group) == 6, f'{role}: expected six motors'
    assert {m['id'] for m in group} == set(range(1, 7)), f'{role}: duplicate/missing IDs'
    for motor in group:
        required = expected_leader[motor['id']] if role == 'L' else 345
        assert motor['ratio'] == required, f'Wrong gearing: {motor}'
        print(role, motor['id'], 'ratio=', motor['ratio'])
print('RECORD_CONSISTENT: verify physical voltage labels before connecting power')
```

**Expected result:** twelve consistent entries, or an assertion identifying an inventory inconsistency. The check cannot detect a motor placed in the wrong tray or a misread voltage label; compare with the physical photograph/table and setup results.

#### Assemble, calibrate and hand over to the complete-arm workflow

1. With all power off, mount the configured servos in the exact SO101 structure and correct horn/link orientation. Route cables through clips with slack for permitted motion; clamp the finished bases to a rigid table.
2. Connect only each role's own chain/controller/supply and verify all expected identities before calibration. Keep the follower empty, supported and its workspace clear; Seeed requires at least1 m of clearance from people/objects during operation.
3. Use unique physical IDs for calibration, matching the example ports to the observed arm:

```bash
lerobot-calibrate --robot.type=so101_follower \
  --robot.port=/dev/ttyACM0 --robot.id=openelab_built_follower
lerobot-calibrate --teleop.type=so101_leader \
  --teleop.port=/dev/ttyACM1 --teleop.id=openelab_built_leader
```

4. Use the manufacturer poses and prompts without forcing mechanical stops. Save calibration files with the actual motor/gear inventory, source commit and supply labels. Then use the assembled Pro guide's teleoperation/one-episode procedure with these IDs.

**Expected result:** correctly mapped/calibrated six-joint chains and a small leader motion corresponding to the intended follower joint. Stop if identity, direction, scale or centering is wrong. Camera binding, recording, replay and policy evaluation follow this result; a motor setup utility is not a policy or payload validation.

### Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                              | Ordered checks / bounded recovery                                                                                              |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------ |
| Setup sees multiple motors           | Power off and isolate one requested servo; a duplicate-ID chain cannot be configured unambiguously.                            |
| No reply from isolated servo         | Check correct supply, controller port, USB/UART mode and cable orientation before changing baud/ID guesses.                    |
| Leader feels unexpectedly stiff      | Confirm correct lower-ratio leader joints, supply and torque state; do not force the mechanism through a bound.                |
| Joint misplaced after assembly       | Check role, joint ID, gear ratio and horn/link centering; correct mechanics before recalibrating.                              |
| Motor current/heat excessive         | Stop, remove load and inspect blocked motion, wrong voltage/mode and calibration. C001 stall values are not continuous limits. |
| Calibration unexpectedly reused      | Confirm unique physical ID and saved record; back up before deliberately choosing recalibration.                               |
| USB controller present, chain absent | USB enumeration checks only the controller; verify separate motor power and chain continuity.                                  |
| Need replacement follower ratings    | Read the exact12 V C018/C047 variant document; the linked7.4 V C001 sheet is insufficient.                                     |

When a replacement changes model/ratio/origin, update the physical inventory and calibration as a matched set. Do not delete every arm's calibration cache or broadcast new IDs to recover one missing joint.

### Downloads and technical documents <a href="#official-documentation-and-development-resources" id="official-documentation-and-development-resources"></a>

| Resource                                                                                                              | Purpose / scope                                                                     |
| --------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| [SO101 STL](https://files.seeedstudio.com/wiki/robotics/projects/lerobot/so101/soarm101.stl)                          | Manufacturer-listed printable leader/follower parts; not included in motor-only SKU |
| [SO101 hardware project](https://github.com/TheRobotStudio/SO-ARM100)                                                 | Select SO101 BOM/assembly, not SO100 leader gearing                                 |
| [Seeed complete setup](https://wiki.seeedstudio.com/lerobot_so100m_new/)                                              | Print, wiring, isolated servo setup, calibration and advanced workflow              |
| [Feetech C0017.4 V datasheet](https://files.seeedstudio.com/wiki/reComputer-Jetson/lerobot/STS3215-C001-20230624.pdf) | A/1,23June2023; voltage-specific electrical, connector and protocol reference       |
| [Bus driver datasheet](https://files.seeedstudio.com/wiki/reComputer-Jetson/lerobot/bus_servo_xiao.pdf)               | Supply, interfaces, USB/UART jumper and board documentation                         |
| [Pinned LeRobot source](https://github.com/Seeed-Projects/lerobot/tree/d490e472a5d1a207cfe0255caaaf74b6d66e4656)      | Tool/target/dependency reference                                                    |
| [LeRobot SO101 guide](https://huggingface.co/docs/lerobot/so101)                                                      | Upstream model/calibration changes                                                  |
| [Seeed catalog](https://files.seeedstudio.com/wiki/wiki-platform/2026_Seeed_Studio_Catalog.pdf)                       | Retained ordering-code reference; verify selected variant against live product      |

### References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed **24 November2026**: exact live product/option, [manufacturer Pro hardware workflow](https://wiki.seeedstudio.com/lerobot_so100m_new/), pinned SDK interfaces and component PDFs above. The gearing photograph was visually inspected. The7.4 V component sheet is explicitly separated from the12 V follower scope; no unsupported follower torque or current figure was substituted.

**Validation:** source reviewed. SDK installation/compilation, servo programming, assembly, calibration and hardware motion were **not run**. The original inventory program checks a user record; it is not a hardware test. Expected results are reproduction checkpoints.

#### Related retained references

* [Read official source: lerobot](https://github.com/Seeed-Projects/lerobot)
