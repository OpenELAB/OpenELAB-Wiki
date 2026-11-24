---
description: >-
  Mount and power NERO, resolve newer25 V and joint-limit guidance, access its
  web controller and read fresh seven-joint feedback with the matching SDK
  profile.
---

# AgileX NERO: 7-axis power, web setup and firmware-aware CAN feedback

{% hint style="info" %}
[**AgileX NERO 7-DOF arm on OpenELAB — SKU Agilex-NERO**](https://openelab.io/products/agilex-nero-embodied-ai-arm?variant=45854559305926)
{% endhint %}

## Product overview <a href="#ffsaj" id="ffsaj"></a>

NERO is a seven-axis, 3 kg-rated robotic arm with an integrated controller, browser-based operator interface and external CAN development connection. Its extra joint permits redundant postures: an endpoint pose does not uniquely identify all seven joint angles. This guide establishes mounting, 24 V power, browser access and firmware-aware joint feedback before introducing trajectories, teaching or ROS 2. [OpenELAB exact option](https://openelab.io/products/agilex-nero-embodied-ai-arm?variant=45854559305926), [current manufacturer resources](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/hf8x32y0tevqyi3g).

The arm is not a PiPER with a seventh value appended. NERO has different geometry, CAN profiles, joint limits and calibration behavior. Select `ArmModel.NERO`, its reported firmware and a NERO URDF. Grippers, teaching handles, dexterous hands and desktop clamps are accessories; establish which are physically fitted before configuring payload and tool coordinates.

## Applications

NERO suits controlled manipulation experiments, embodied-data collection, leader–follower research and workstation integration. Begin with a stationary seven-joint log, then a small repeatable joint motion, a two-point trajectory and a measured tool transform. This provides separate evidence for communication, motion repeatability and task geometry.

A redundant arm can change elbow posture while holding a similar endpoint pose. Inspect the entire link sweep when planning around a table, camera or another robot. Collision sensitivity is an additional controller function, not a certified person-detection system. The manufacturer states that the arm lacks automatic proximity/obstacle sensing. [NERO manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

## Specifications

| Parameter             | NERO value                                                     | Scope                                                                 |
| --------------------- | -------------------------------------------------------------- | --------------------------------------------------------------------- |
| Controlled axes       | 7                                                              | Separate attached tool from arm joints                                |
| Payload               | 3 kg                                                           | Tool and carried load must fit the actual reach/load condition        |
| Arm mass              | 4.8 kg                                                         | Excludes optional tool                                                |
| Reach                 | 580 mm                                                         | Nominal radius, not an obstacle-free operating envelope               |
| Repeatability         | ±0.1 mm                                                        | Manufacturer controlled-condition claim                               |
| Supply                | 24 VDC nominal                                                 | Newer manual: **must not exceed25 V**, regulated external supply≥10 A |
| Arm power             | ≤150 W maximum;≤60 W typical/comprehensive                     | Does not replace transient-current supply requirement                 |
| End electrical output | 24 V, 2 A maximum                                              | Keyed XT30(2+2); approved AgileX accessories only on end CAN          |
| Mounting              | Four M5 holes on 70 × 70 mm pattern                            | Mounting orientation must match controller setting                    |
| Environment           | −20 to +50 °C; 25–85 %RH noncondensing; IP22 unless customized | Not an outdoor weatherproof rating                                    |
| Communication         | CAN; browser interface; listed HTTP/TCP capabilities           | API transport support must be checked independently                   |

The older downloadable English PDF says26 V maximum and gives different J2/J6/J7 ranges. The newer Chinese manual and November2026 English quick-start agree on the 25 V ceiling and the following nominal joint table; use24 V regulated power and verify controller limits for the arm's revision rather than averaging the documents. [Current manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb), [current quick-start](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/famocdascsqfvyrq), [older PDF](https://cdn.shopify.com/s/files/1/0551/0630/6141/files/NERO_USER_MANUAL_2732ff89-040d-4b89-9b02-a09019f21b18.pdf?v=1792486598).

| Joint | Current manual range | Maximum speed | Older PDF range where different |
| ----- | -------------------- | ------------- | ------------------------------- |
| J1    | −157°…+157°          | 180°/s        | same                            |
| J2    | −102°…+102°          | 180°/s        | −15°…190°                       |
| J3    | −160°…+160°          | 180°/s        | same                            |
| J4    | −60°…+125°           | 225°/s        | same                            |
| J5    | −160°…+160°          | 225°/s        | same                            |
| J6    | −44°…+57°            | 225°/s        | −43°…+58°                       |
| J7    | −97°…+97°            | 225°/s        | −90°…+90°                       |

These are reference envelopes, not targets for a first command. Software configuration can impose narrower limits. A maximum speed is not a commissioning speed.

Optional two-finger gripper: 500 g, 0–100 mm opening, 40 N rated/50 N maximum gripping force,±0.5 mm stated accuracy, 24 V,≤50 W maximum. The teaching handle is 550 g with 0–70 mm opening. Include fitted-tool mass and center of gravity in configuration; a nominal 3 kg arm payload does not mean3 kg of object plus an arbitrarily heavy tool. [Current manual accessory tables](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

## Hardware and connections

### Mounting and cable orientation

![AgileX NERO electrical panel: keyed aviation connector, Ethernet, Wi-Fi antenna and status indication](<../../.gitbook/assets/电器面板 (2).png>)

Manufacturer electrical-panel drawing, retained from the existing manual. The aviation harness contains power and external CAN branches. Align its red dot with the socket's red dot before inserting. Release with the textured sleeve rather than pulling the wires. Keep the internal/service CAN connector unused; it is reserved for technical support. The base's Ethernet jack is for the embedded controller, not a USB-CAN substitute. [Quick-start electrical panel and wiring](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/famocdascsqfvyrq).

Mount the arm with four suitable M5 fasteners using the 70 × 70 mm pattern and a rigid supporting surface. The optional desktop fixture must be securely clamped before operation. Confirm screw engagement and underside clearance against the mechanical drawing rather than interpreting “M5 × 4” as a 4 mm screw length. Check resistance to the arm's overturning moment, not just its4.8 kg static weight.

![NERO manufacturer workspace illustration retained from the existing manual](<../../.gitbook/assets/image (1174).png>)

For an end tool, follow its keyed flange orientation and specified screws. The current quick-start distinguishes a standard gripper orientation from a side mount by the camera-hole face relative to the XT30 connection. Tool orientation changes the TCP configuration. A previously purchased PiPER gripper can require a **NERO-specific ID modification**; an ID collision can disturb kinematics and gravity compensation. Do not connect it and repeatedly retry enabling. [Manual installation and legacy-gripper notice](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

### Power and CAN

1. Keep the supply off while assembling the harness. Connect its CAN\_H/yellow and CAN\_L/blue branches to the corresponding supplied adapter terminals.
2. Secure each conductor under the terminal's clamping tab and tug-test gently. Connect matching keyed power branches and the base aviation connector.
3. Power the supplied 24 V adapter; wait for the documented boot indication, then attach the USB-CAN connection to the development computer.
4. Leave the arm supported and disabled while establishing browser access. Do not use the status LED alone to decide that a fault is cleared; inspect the web joint-status panel.

The published connector orientation, not a remembered left/right viewpoint, determines wiring. Do not hot-plug a tool, backfeed its24 V output or connect third-party devices to the reserved end CAN. The arm CAN interface uses1 Mbit/s; the SDK's Linux path is SocketCAN. Preserve the supplied single-arm termination arrangement before considering a multi-arm topology. [Quick-start wiring](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/famocdascsqfvyrq), [SDK CAN guide](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/can_user.md).

## Software and development resources

### Browser control and state ownership

The embedded web controller provides joint status, system usage, enable/disable, emergency stop, error information, speed, joint/Cartesian motion, drag teaching, dexterous-hand control, leader–follower operation, trajectories, calibration, tool/mounting configuration, network configuration and upgrade panels. Treat these as different operating states. Switching to **Web** control stops trajectory-mode operation before web commands are accepted. Preserve faults in a log before using Clear Error. [Complete web manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

| Motion facility | Prerequisite and limit                                                                             |
| --------------- | -------------------------------------------------------------------------------------------------- |
| Joint target    | Seven values in the current joint reference; check limits and link sweep                           |
| Point           | Reachable endpoint pose; redundant IK can choose a different elbow posture                         |
| Line            | Entire interpolated path must remain reachable, not only the endpoint                              |
| Circle          | Start, intermediate and end poses must define a feasible arc                                       |
| MIT/torque      | Version-specific torque and velocity encoding; advanced controller design, not a first-run mode    |
| Drag teaching   | Correct physical zeros, mounting orientation, tool mass and gravity compensation                   |
| Leader–follower | Start both arms near matching reference poses, identify roles and avoid conflicting CAN publishers |

### SDK versions and units

Use [pyAgxArm](https://github.com/agilexrobotics/pyAgxArm) rather than a six-axis PiPER script. The source reviewed here is commit `d90e234ba8e408cfa964b38aa9120b3131fc9f85` (package1.0.0, LGPL-3.0-only). The example below targets Ubuntu 22.04/Python 3.10 with a functioning Linux SocketCAN adapter. The upstream keyword is spelled **`firmeware_version`**.

| Arm firmware reported by `get_firmware()` | SDK profile | Material behavior                                                                    |
| ----------------------------------------- | ----------- | ------------------------------------------------------------------------------------ |
| ≤1.10                                     | `default`   | Older Cartesian workaround; 8-bit MIT torque; reported motor velocity forced to 0    |
| 1.11                                      | `v111`      | 12-bit MIT torque, changed motion encoding and calibration support                   |
| 1.12                                      | `v112`      | CPV and IK feedback; revised leader feedback; follower/CAN-push behavior changes     |
| 1.20                                      | `v120`      | Real motor velocity and corrected CPV feedback; some command sign workarounds remain |
| ≥1.21 in this published matrix            | `v121`      | MIT/CPV command velocity retains requested sign                                      |

Do not use an unknown future firmware merely because its number sorts higher. Confirm it remains covered by the selected SDK's matrix. The older full API table is less detailed than the current firmware-reference document; preserve both the reported firmware and resolved profile in logs. `get_joint_angles().msg` contains **seven radians**, not degrees. [NERO API](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/nero/nero_api.md), [firmware matrix](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/nero/firmware_reference.md).

ROS 2 Humble support is in [agx\_arm\_ros](https://github.com/agilexrobotics/agx_arm_ros), with NERO description/model assets and simulation resources in [agx\_arm\_urdf](https://github.com/agilexrobotics/agx_arm_urdf) and [agx\_arm\_sim](https://github.com/agilexrobotics/agx_arm_sim). A URDF, MoveIt plan or MuJoCo scene does not qualify a physical mount or tool. The SDK can describe custom joint limits without applying every custom configuration to real control; retain controller-side limits and inspect the actual API behavior.

## Getting started

### 1. First result through the embedded web interface

1. Secure the arm and clear its reachable workspace. Use the supplied adapter and support any attached tool before booting.
2. Join its documented hotspot `agx-7ax-xx`, password `12345678`, and open `http://192.168.31.1/`. Published initial web credentials are `admin` / `123456`.
3. Alternatively, connect Ethernet directly and give the computer an unused address such as `10.90.0.153/24`, with the robot at its published default `10.90.0.150`. Keep both on the same subnet; no gateway is needed for a direct isolated link.
4. Open the status page and record firmware, joint state, faults, mounting orientation and tool configuration **without enabling motion**. Check that seven joints are represented.
5. Preserve screenshots/configuration before changing credentials, hotspot or Ethernet settings. A network change can disconnect the current session; keep the alternative access path available.

**Expected result:** the web interface loads, seven joint statuses are readable and the actual software/firmware and mounting configuration are recorded. A successful login proves the embedded network path; it does not prove external CAN feedback. [Connection and web manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

### 2. Prepare a separate SDK environment

```bash
git clone https://github.com/agilexrobotics/pyAgxArm.git
cd pyAgxArm
git checkout d90e234ba8e408cfa964b38aa9120b3131fc9f85
python3 -m venv .venv
. .venv/bin/activate
python -m pip install -e .
ip -details -statistics link show can0
```

The last command must identify the actual supplied adapter configured at 1,000,000bit/s with no persistent bus-off state. If it is not configured, follow the SDK's adapter-identification instructions; do not reconfigure a similarly named interface already serving another device. Installation downloads dependencies but does not operate the arm. [CAN setup](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/can_user.md).

### 3. Original seven-joint freshness logger

For older firmware, enable the documented **CAN publishing** setting in the web interface before the observer; this changes telemetry, not a motor-enable command. Firmware1.12 changes startup push behavior. Keep one arm on this external bus and close other SDK/ROS controllers.

Save as `nero_feedback.py` and run `python nero_feedback.py` inside the environment. It queries firmware, reconnects with the corresponding NERO profile and prints only fresh, finite seven-joint samples. There is no enable, calibration or motion call.

```python
import math
import time
from pyAgxArm import (AgxArmFactory, ArmModel,
                      create_agx_arm_config, resolve_firmware_profile)

def make_arm(profile):
    cfg = create_agx_arm_config(robot=ArmModel.NERO,
                               firmeware_version=profile,
                               interface='socketcan', channel='can0')
    return AgxArmFactory.create_arm(cfg)

probe = make_arm('default')
try:
    probe.connect()
    firmware = probe.get_firmware(timeout=2.0)
    if not firmware or not firmware.get('software_version'):
        raise RuntimeError('No firmware reply: inspect CAN path and publishing')
    version = firmware['software_version']
    profile = resolve_firmware_profile(ArmModel.NERO, version)
    print('firmware=', version, 'profile=', profile)
finally:
    probe.disconnect()

arm = make_arm(profile)
try:
    arm.connect()
    deadline = time.monotonic() + 10.0
    previous = None
    accepted = 0
    while time.monotonic() < deadline:
        sample = arm.get_joint_angles()
        if sample is not None:
            age = time.time() - sample.timestamp
            angles = sample.msg
            if (0 <= age <= 0.5 and sample.timestamp != previous
                    and len(angles) == 7
                    and all(math.isfinite(v) for v in angles)):
                print('rad=', ','.join(f'{v:.5f}' for v in angles))
                previous = sample.timestamp
                accepted += 1
        time.sleep(0.05)
    if not accepted:
        raise RuntimeError('No fresh seven-joint samples; no motion attempted')
    print('fresh_samples=', accepted)
finally:
    arm.disconnect()
```

**Expected result:** a reported firmware/profile followed by seven-radian rows and a nonzero fresh-sample count. A stationary supported arm should show nearly constant values. A timeout is a failed telemetry checkpoint; do not fix it by enabling motors or resetting zeros. Compare a sample with the web's displayed angles after converting radians to degrees, allowing for the documented joint reference and presentation convention. [API definitions and implementation](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/nero/nero_api.md).

### 4. Controlled progression through web modes

After mounting/tool settings and feedback are verified, choose Web mode, retain the operator's stop control and use a low speed percentage. Start from the **displayed current joint pose**, alter one joint by a small amount within a clear local envelope and apply once. Observe that only the intended axis changes; stop if direction or reference differs. Return using the recorded original pose, not a newly invented all-zero target.

For a two-point trajectory, save the current pose, make the same small checked move, save the second point, export the trajectory and inspect its points before replay. Run once before considering repetition. Point/line/circle demos require reachable intermediate poses; an IK error is a planning failure, not a reason to expand limits.

For drag teaching, support the arm before entering gravity compensation and verify that the configured tool and mount match the hardware. Create a named teaching record, start recording, guide a short clear path and pause recording before leaving that mode. Review the record before playback. Avoid J2/J3/J4/J5 simultaneously near the kinematic singular configuration identified by the manufacturer. [Motion, teaching and trajectory chapters](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

For ROS 2, select `arm_type:=nero` and inspect the launch arguments before starting. The reviewed launch defaults can auto-enable and accept control, so passive commissioning must explicitly use `auto_enable:=false control_enabled:=false` and the actual CAN port. Keep the browser's motion mode and every other physical controller inactive. MoveIt/Gazebo, Isaac Sim and MuJoCo are separate environments listed in the resource index; validate geometry and units there before enabling a real bridge. [ROS launch source](https://github.com/agilexrobotics/agx_arm_ros/blob/747d0722074d4cebc095d8d44f3ef68d2023ba6f/src/agx_arm_ctrl/launch/start_single_agx_arm.launch.py).

## Troubleshooting and FAQs

| Symptom                                | Diagnostic and recovery boundary                                                                                                                |
| -------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| Web page absent                        | Check boot/power, selected hotspot or Ethernet subnet, actual configured address and link LEDs; do not factory-reset zeros to repair networking |
| Firmware reply but no joints           | Check CAN-push setting and firmware profile; retain external CAN ownership and inspect receive counters                                         |
| Cached angles repeat forever           | Inspect timestamp age and connection health; require fresh samples, not merely a non-`None` object                                              |
| Web says incorrect control mode        | Switch to Web mode deliberately; this can stop an active trajectory. Do not issue repeated commands across competing modes                      |
| Gravity compensation pulls incorrectly | Stop teaching; verify mount, tool mass/CoG, zero calibration and legacy-gripper ID before further motion                                        |
| Cartesian target rejected              | Check units, joint limits, redundancy, singularity and the complete path; do not widen limits as a workaround                                   |
| Leader–follower CAN abnormal           | Check assigned roles and duplicate push streams; follow the manual's restart procedure with both arms supported                                 |
| Arm drops on power loss                | Plan mechanical support and power-off posture. Software disconnect does not disable a robot, and removing power can release load                |

**Should I zero the arm on every first boot?** No. Read and preserve existing calibration. The dedicated August2026 zeroing guide distinguishes upright/no-tool automatic calibration from side/inverted or loaded cases. Automatic calibration moves to mechanical limits and returns; it is not a harmless reset. For side mounting, select the correct mounting orientation before any permitted single-joint procedure. Loaded/nonstandard cases need the documented manual method and support. J6 can perform an additional calibration movement. [Manufacturer zeroing guide](https://agilexsupport.yuque.com/staff-hso6mo/ihw47g/ugnfto98dgopiuwh).

**Can two connected arms both be followers?** The manual warns against two follower configurations and simultaneous CAN push on the connected pair. Begin near matched reference poses before linking; otherwise a follower can move rapidly to match its leader. Role names and normal-mode support also changed with firmware 1.12. [Manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb), [SDK firmware reference](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/nero/firmware_reference.md).

**How are upgrades recovered?** Record controller/software and every joint firmware version, export trajectories/configuration, support the arm and obtain an exact matching package. Joint firmware upgrade requires entering Upgrade Mode; the arm is disabled, and the manual requires **Exit Upgrade** after completion. Do not interrupt power or repeatedly load an unverified binary. A controller software update and a joint firmware update are different operations. Persistent faults or incomplete calibration need manufacturer-supported recovery. [Upgrade chapters](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

Maintenance begins with a supported, powered-off arm: inspect cable jackets, connector retention, fasteners and deformation; clean without forcing liquid into the housing. Preserve calibration and settings rather than re-zeroing as routine cleaning. The manual's emergency power-disconnection description warns of immediate arm drop; provide a suitable system stop arrangement before actuation.

## Downloads and technical documents

| Resource                       | Direct destination and version boundary                                                                                                                                                                                                      |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Current manual                 | [Chinese manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb); [English manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/vx3iqycffq0pg8af)                                                               |
| First-use guide                | [English quick-start, November2026](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/famocdascsqfvyrq)                                                                                                                                    |
| Downloadable historical manual | [Official PDF](https://cdn.shopify.com/s/files/1/0551/0630/6141/files/NERO_USER_MANUAL_2732ff89-040d-4b89-9b02-a09019f21b18.pdf?v=1792486598); electrical/joint differences identified above                                                 |
| Current CAN protocol           | [V1.2 route from resource index](https://agilexsupport.yuque.com/staff-hso6mo/gp5vq8/rxwtftfridv9qg0c); public text export requested login during review                                                                                     |
| Python SDK/API/examples        | [pyAgxArm](https://github.com/agilexrobotics/pyAgxArm)                                                                                                                                                                                       |
| ROS 2 Humble                   | [agx\_arm\_ros](https://github.com/agilexrobotics/agx_arm_ros)                                                                                                                                                                               |
| URDF and simulation            | [agx\_arm\_urdf](https://github.com/agilexrobotics/agx_arm_urdf); [MoveIt2/Gazebo](https://github.com/agilexrobotics/agx_arm_sim/tree/master/Moveit2); [MuJoCo](https://github.com/agilexrobotics/agx_arm_sim/tree/master/mujoco/agilex_arm) |
| Bare-arm CAD                   | [nero3D.zip](https://agilexsupport.yuque.com/attachments/yuque/0/2026/zip/68774675/1786175467832-1ad8998f-7925-48e3-a916-39a409486831.zip)                                                                                                   |
| Tool flange CAD                | [Two-finger gripper STEP ZIP](https://agilexsupport.yuque.com/attachments/yuque/0/2026/zip/29291030/1773671857392-59c9dda7-b459-48c4-83d6-892f21e13fee.zip)                                                                                  |
| All tool/camera mounts         | [Official model collection](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/alsnhlaawartt3k8): bare/tool-equipped arm, dexterous-hand flanges, DC1/D435i/D405/custom camera mounts and 100 mm gripper model                              |
| Zero calibration               | [Dedicated upright/side/manual guide](https://agilexsupport.yuque.com/staff-hso6mo/ihw47g/ugnfto98dgopiuwh)                                                                                                                                  |

CAD links were observed in the manufacturer index; archives were not mechanically qualified. Use the supplied revision's drawings and confirm dimensions before machining. The integrated controller is not an open general-purpose computer; do not infer shell access from the web system-usage display.

### Operating environment and inspection reference

These arms have no built-in automatic obstacle-avoidance sensing. The manufacturer's ordinary enclosure rating is **IP22 unless customized**; this does not qualify rain, washdown or conductive dust exposure. Use the stated −20 to +50 °C and 25–85% RH noncondensing environment. Keep people outside the complete arm/tool sweep, operate within sight and secure hair/clothing that could catch. The manufacturer excludes unsupervised use by people under 18 and requires the complete installation, including other machines and its stop arrangement, to be assessed separately.

Before operation, check base/tool fasteners, harness retention, jacket damage, deformed brackets and visible motor faults. Stop on abnormal motion or a controller error, preserve the diagnostic record and resolve the cause before clearing it. Do not modify protective measures or expose the arm to strong permanent magnetic fields. After demanding operation, isolate/support it and allow the manufacturer's stated **one-hour cooling interval** before handling hot joints. Clean only the exterior using a dry or lightly water-dampened cloth; do not flood connectors. The arm manual and diagrams remain part of the installation record, rather than a claim that a GUI stop or collision sensitivity makes a completed cell safe.

[Manufacturer operating and safety reference](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

### Arm and optional-tool reference details

The arm uses an aluminum-alloy frame with a plastic enclosure and an integrated controller. The manual reports noise below 60 dB under its stated conditions; this is not a measured result for the reader's installation. Optional gripper and teaching accessories have their own integrated controllers, rubber contact surfaces, CAN communication and flange mounting. Their listed 24 V supply, up-to-50 W maximum and 30 W comprehensive power figures are accessory specifications, not extra current available from an arbitrary host port. Keep the end-output limit above when choosing a tool.

Historical accessory tables describe a 500 g two-finger gripper and a 550 g teaching handle with ±0.5 mm stated accuracy. Some older English tables give a 0–100 mm opening for both, while newer Chinese teaching-handle tables give **0–70 mm**. Those values identify differing documentation/accessory revisions; read the actual handle label and matched drawing before choosing a stroke. The two-finger gripper's 0–100 mm opening is separate. Do not use arm joint travel as a tool-opening range.

[Manufacturer operating and safety reference](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

### Detailed operating reference

The following model-specific operating details and native manufacturer illustrations complement the commissioning procedure above. GUI screenshots depict their documented release; current firmware, power and calibration requirements take precedence where versions differ. [Manufacturer manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/air57k7k3nhgeuxb).

#### NERO User Manual

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### AgileX NERO 7-DOF 3 kg Payload Robotic Arm for Embodied A <a href="#agilex-nero-7-dof-3kg-payload-robotic-arm-for-embodied-a" id="agilex-nero-7-dof-3kg-payload-robotic-arm-for-embodied-a"></a>

NERO is nominally3 kg with 580 mm reach. The workspace illustration and tool-equipped envelope must be considered together; a heavy or offset hand consumes the load/moment budget. Use the exact mount/tool configuration, collision geometry and current joint limits. A reachable FK/IK result does not establish payload capacity or a collision-free path.

#### AgileX NERO Gripper <a href="#agilex-nero-gripper" id="agilex-nero-gripper"></a>

The illustrated optional tool is a separate fitted accessory, not part of every bare-arm order. Confirm its exact model, supply, firmware/device identity and mechanical flange before connection. The two-finger gripper and teaching handle have different opening ranges, mass and feedback roles. Include the tool in payload/TCP configuration and verify motion direction with a light test object before using it to retain anything.

<details>

<summary>AgileX NERO Gripper — manufacturer figures</summary>

![Manufacturer NERO illustration for AgileX NERO Gripper](<../../.gitbook/assets/image (1171).png>)

![Manufacturer NERO illustration for AgileX NERO Gripper](<../../.gitbook/assets/image (1172).png>)

</details>

#### Important Safety Information <a href="#odniv" id="odniv"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### 1 Robotic Arm Overview <a href="#sygvh" id="sygvh"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### 1.1 Product List <a href="#xvxiq" id="xvxiq"></a>

Inventory the arm, supplied USB-CAN adapter, power adapter/cable, mounting hardware and tools against the ordered package. Optional gripper, teaching handle, dexterous hand and desktop fixture remain separate items unless listed. The model-specific Specifications table above distinguishes rated payload, reach, mass, joint travel/speed and accessory limits. Treat manufacturer repeatability/power/environment figures as conditions to verify in the actual setup, not measurements from this guide.

#### 1.2 Performance Parameters <a href="#mnuck" id="mnuck"></a>

Inventory the arm, supplied USB-CAN adapter, power adapter/cable, mounting hardware and tools against the ordered package. Optional gripper, teaching handle, dexterous hand and desktop fixture remain separate items unless listed. The model-specific Specifications table above distinguishes rated payload, reach, mass, joint travel/speed and accessory limits. Treat manufacturer repeatability/power/environment figures as conditions to verify in the actual setup, not measurements from this guide.

#### 2 Basic Introduction <a href="#ouh54" id="ouh54"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

<details>

<summary>2 Basic Introduction — manufacturer figures</summary>

![Manufacturer NERO illustration for 2 Basic Introduction](<../../.gitbook/assets/微信图片_20260118225938_441_140 (2).png>)

</details>

#### 2.1 Electrical Interface <a href="#e8e54" id="e8e54"></a>

The base external power/CAN harness, Ethernet where fitted and end accessory connector have different functions. The end XT30(2+2) supplies24 V up to 2 A and its CAN is reserved for supported AgileX accessories; it is not a general CAN expansion socket. Follow the illustrated mating viewpoint and keying, not wire color alone. Keep the internal/service CAN unused without manufacturer service instructions and remove power before changing an end tool.

#### 2.1.1 Electrical Panel Introduction <a href="#mt4wn" id="mt4wn"></a>

The base external power/CAN harness, Ethernet where fitted and end accessory connector have different functions. The end XT30(2+2) supplies24 V up to 2 A and its CAN is reserved for supported AgileX accessories; it is not a general CAN expansion socket. Follow the illustrated mating viewpoint and keying, not wire color alone. Keep the internal/service CAN unused without manufacturer service instructions and remove power before changing an end tool.

<details>

<summary>2.1.1 Electrical Panel Introduction — manufacturer figures</summary>

![Manufacturer NERO illustration for 2.1.1 Electrical Panel Introduction](<../../.gitbook/assets/电器面板 (2).png>)

![Manufacturer NERO illustration for 2.1.1 Electrical Panel Introduction](<../../.gitbook/assets/image (1173).png>)

</details>

#### 2.1.2 End-Effector Connection Description <a href="#g9qjn" id="g9qjn"></a>

The base external power/CAN harness, Ethernet where fitted and end accessory connector have different functions. The end XT30(2+2) supplies24 V up to 2 A and its CAN is reserved for supported AgileX accessories; it is not a general CAN expansion socket. Follow the illustrated mating viewpoint and keying, not wire color alone. Keep the internal/service CAN unused without manufacturer service instructions and remove power before changing an end tool.

<details>

<summary>2.1.2 End-Effector Connection Description — manufacturer figures</summary>

![Manufacturer NERO illustration for 2.1.2 End-Effector Connection Description](<../../.gitbook/assets/NERO User Manual image 6 (2)>)

</details>

#### 2.2 Robotic Arm Workspace and Payload <a href="#cgwnl" id="cgwnl"></a>

NERO is nominally3 kg with 580 mm reach. The workspace illustration and tool-equipped envelope must be considered together; a heavy or offset hand consumes the load/moment budget. Use the exact mount/tool configuration, collision geometry and current joint limits. A reachable FK/IK result does not establish payload capacity or a collision-free path.

<details>

<summary>2.2 Robotic Arm Workspace and Payload — manufacturer figures</summary>

![Manufacturer NERO illustration for 2.2 Robotic Arm Workspace and Payload](<../../.gitbook/assets/image (1175).png>)

![Manufacturer NERO illustration for 2.2 Robotic Arm Workspace and Payload](<../../.gitbook/assets/image (1174).png>)

</details>

#### 2.3 Mechanical Installation Instructions <a href="#guu5a" id="guu5a"></a>

Use the dimensioned view for the identified bare-arm, tool-equipped, base or end-flange assembly. Keep its viewpoint, units and model revision with any fixture design; an axonometric picture is not a scale drawing. Check hole pattern, screw engagement, cable exit and the complete swept volume against the physical parts before machining. The numerical arm limits and actual tool transform remain separate from the drawing envelope.

#### 2.3.1 Base Mounting Instructions <a href="#dwawn" id="dwawn"></a>

The arm base uses four M5 mounting positions on a 70 × 70 mm pattern. Support the arm while fitting it to a rigid plate and check both hole spacing and thread engagement against the drawing. Neither the notation M5 × 4 nor the base mass establishes screw length, tightening torque or allowable overturning moment. Inspect contact flatness and the underside of the mount before power; a mobile or inverted installation also needs the corresponding controller mounting setting.

#### 2.3.2 End-Effector Installation Instructions <a href="#wp2ga" id="wp2ga"></a>

The historical dexterous-hand assembly uses a baffle/flange: six M3 × 6 countersunk screws at the output shaft, four M3 × 8 screws for the side flange and four M3 × 6 screws securing the hand, with its cable outlet aligned to the flange opening. This is a dexterous-hand assembly, not the newer two-finger gripper's keyed M2.5 × 6 attachment. Select the drawing for the actual tool revision, fit it with power off and configure its mass/CoG/TCP before enabling. The manual's J6 electrical-interface wording must not be used to infer a six-axis NERO or a seventh pose actuator beyond the actual chain.

<details>

<summary>2.3.2 End-Effector Installation Instructions — manufacturer figures</summary>

![Manufacturer NERO illustration for 2.3.2 End-Effector Installation Instructions](<../../.gitbook/assets/灵巧手安装 (2).png>)

![Manufacturer NERO illustration for 2.3.2 End-Effector Installation Instructions](<../../.gitbook/assets/安装手 (2).png>)

</details>

#### 2.3.3 Installation Instructions on Desktop <a href="#bemxi" id="bemxi"></a>

The desktop mounting module is optional; the bare-arm packing list does not imply it is supplied. Fit the arm to the matched module before clamping it to a sound, suitable bench, keep all clamp pads seated and preserve access to power/CAN release. Recheck rocking and cable interference after relocation. Changing the fixture location changes the external workcell transform even if joint zeros remain correct; redo the affected camera/workbench calibration.

<details>

<summary>2.3.3 Installation Instructions on Desktop — manufacturer figures</summary>

![Manufacturer NERO illustration for 2.3.3 Installation Instructions on Desktop](<../../.gitbook/assets/NERO User Manual image 12 (2)>)

</details>

#### 3 Robotic Arm Operation <a href="#vkpyt" id="vkpyt"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### 3.1 CAN cable connection <a href="#wgh5f" id="wgh5f"></a>

Use the external keyed harness and the supplied USB-CAN adapter, matching CAN\_H/yellow and CAN\_L/blue. Align the red marks before seating the base connector and clamp conductors under the terminal tab without loose strands. Select the actual adapter/channel and 1 Mbit/s configuration before connecting the GUI. Preserve factory termination for a single-arm topology; an empty feedback panel calls for adapter, power, mode and receive-counter checks before any enable or firmware update.

<details>

<summary>3.1 CAN cable connection — manufacturer figures</summary>

![Manufacturer NERO illustration for 3.1 CAN cable connection](<../../.gitbook/assets/NERO User Manual image 13 (2)>)

</details>

#### 3.2 Power-On Instructions <a href="#kkruz" id="kkruz"></a>

With the arm supported and disabled, assemble CAN and keyed power branches, seat the base connector, power the matched regulated adapter and wait for the documented boot indication before the host connection. Confirm live status/feedback and faults before enabling. NERO uses the newer25 V ceiling; the PiPER-family limits in Specifications remain model-specific. Never substitute a power-cycle or connector removal for a planned controlled stop when gravity can drop the arm.

<details>

<summary>3.2 Power-On Instructions — manufacturer figures</summary>

![Manufacturer NERO illustration for 3.2 Power-On Instructions](<../../.gitbook/assets/7轴 (2).png>)

</details>

#### 3.3 DH for robotic arm <a href="#hyhqd" id="hyhqd"></a>

The manual's DH reference uses meters for link offsets and degrees for twist/joint offsets. Keep this convention with the chosen URDF/SDK rather than treating a DH offset as a raw encoder zero. The following numerical table belongs to the illustrated NERO chain; a tool transform is additional.

| Joint | a(i−1), m | alpha(i−1),° | d(i), m | theta offset,° |
| ----- | --------- | ------------ | ------- | -------------- |
| j1    | 0         | 0            | 0.138   | 0              |
| j2    | 0         | 90           | 0       | 180            |
| j3    | 0         | 90           | 0.31    | 180            |
| j4    | 0         | 90           | 0       | 180            |
| j5    | 0         | 90           | 0.27001 | 90             |
| j6    | 0         | 90           | 0       | 90             |
| j7    | 0         | 90           | 0.0235  | 0              |

Before using it for external FK, compare a known supported pose with the current controller's reported flange pose. A matrix calculation does not establish collision clearance.

#### 4 Robotic Arm Connection <a href="#rqecy" id="rqecy"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### 4.1 WIFI connection <a href="#wc5sc" id="wc5sc"></a>

The NERO factory hotspot follows agx-7ax-xx with the published initial password12345678, and the web page is at 192.168.31.1 with initial admin/123456 credentials. Read the actual configured values if a previous owner changed them. Hotspot configuration and Ethernet address settings are separate; record both and keep a fallback route before applying changes. Change default credentials before shared-network operation.

#### 4.2 Ethernet Connection <a href="#ia38d" id="ia38d"></a>

The factory NERO wired address is 10.90.0.150. Use an unused computer address on the same subnet, such as10.90.0.153/24 for an isolated direct link, then open the controller page. Record old IP/mask/gateway before changing network settings and retain a tested alternative access path. A saved address change can disconnect the current browser session; it is unrelated to joint zero or motor calibration.

#### 5 Web-Based Host Computer Introduction <a href="#wddhs" id="wddhs"></a>

Use the mode/navigation panel to identify which subsystem currently owns control before editing a target. Connection, motion, tool configuration, diagnostics, upgrade and trajectories are separate pages. Preserve the current configuration and read feedback first; changing page, minimizing the window or closing a display is not automatically a physical stop. Confirm the active mode and operator stop action before a test.

#### 5.1 Page Introduction <a href="#fit2d" id="fit2d"></a>

Use the mode/navigation panel to identify which subsystem currently owns control before editing a target. Connection, motion, tool configuration, diagnostics, upgrade and trajectories are separate pages. Preserve the current configuration and read feedback first; changing page, minimizing the window or closing a display is not automatically a physical stop. Confirm the active mode and operator stop action before a test.

#### 5.1.1 System Usage Rate <a href="#wws92" id="wws92"></a>

The web system-usage panel reports the integrated controller disk, CPU and memory condition. It is useful for recording whether the web service is responsive, but it does not expose a supported general-purpose shell or prove healthy motor communication. Compare joint status and firmware separately. Do not delete controller files or install host packages merely because the usage view resembles a normal Linux dashboard.

<details>

<summary>5.1.1 System Usage Rate — manufacturer figures</summary>

![Manufacturer NERO illustration for 5.1.1 System Usage Rate](<../../.gitbook/assets/image (1179).png>)

</details>

#### 5.1.2 Robotic Arm Status <a href="#gbndg" id="gbndg"></a>

The joint-information/status view monitors connected joints in real time, while the overall status bar reports arm-level state. Confirm expected joint count, changing timestamps/feedback, temperatures and fault indicators before motion. A colored status button or a frozen3D pose alone is insufficient evidence of healthy communication. Preserve the fault/time/operating pose before clearing an error, and compare requested mode with reported mode when commands appear ignored.

#### 5.1.3 Top Function Button Description <a href="#pjqyc" id="pjqyc"></a>

The web toolbar combines speed, stop, Web-mode selection, fault clearing, enabling and system restart with display/language/search controls. Separate passive display functions from physical or state-changing buttons. Read current mode and joint status before changing speed/enable, save fault information before clearing and stop active work before restart. A return to Web mode can stop a running trajectory; inspect remaining targets before any resumption.

<details>

<summary>5.1.3 Top Function Button Description — manufacturer figures</summary>

![Manufacturer NERO illustration for 5.1.3 Top Function Button Description](<../../.gitbook/assets/image (1181).png>)

![Manufacturer NERO illustration for 5.1.3 Top Function Button Description](<../../.gitbook/assets/image (1183).png>)

![Manufacturer NERO illustration for 5.1.3 Top Function Button Description](<../../.gitbook/assets/image (1182).png>)

![Manufacturer NERO illustration for 5.1.3 Top Function Button Description](<../../.gitbook/assets/image (1184).png>)

</details>

#### 6 User Control Area <a href="#gu7uu" id="gu7uu"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### 6.1 Motion Control <a href="#mffqi" id="mffqi"></a>

NERO offers Point, Joint, Line, Circle and firmware-dependent MIT/torque control. Joint entry is bounded by current limits; Point requires reachable IK; Line requires reachable intermediate positions; Circle requires a feasible start/intermediate/end arc. Editing a value is separate from Apply. MIT mixes position, velocity, gains and torque and requires its exact firmware protocol; it is excluded from first-run motion. Start from displayed current joints and one small checked change, not an arbitrary all-zero pose.

#### 6.2 Drag Teaching <a href="#ztlxj" id="ztlxj"></a>

Create a named teaching program, add/start the recording and verify the gravity-compensated mode before guiding the arm. Keep correct zeros, tool mass/CoG and mounting orientation; a wrong compensation direction is a fault to investigate, not resistance to overcome. Pause to end recording, preserve/export the record and inspect its complete path before one supervised replay. Mode changes and power loss can change support behavior, so do not leave a held payload unsupported.

<details>

<summary>6.2 Drag Teaching — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.2 Drag Teaching](<../../.gitbook/assets/image (1185).png>)

</details>

#### 6.3 Dexterous hand <a href="#fddbu" id="fddbu"></a>

Dexterous-hand control applies only to a supported fitted hand and its matching flange, wiring, device identity and controller configuration. A hand illustration is not an inclusion guarantee for the bare arm. Preserve the associated mounting drawing and tool mass/center-of-gravity data, then verify individual hand functions with the arm supported before combined motion. Avoid reusing a two-finger gripper ID/configuration for a multi-actuator hand.

#### 6.4 Coordinated control <a href="#i8jvi" id="i8jvi"></a>

The older NERO interface includes normal/leader/follower, while firmware 1.12 changes the role/CAN-push model and makes the old normal-mode SDK operation a no-op. Use the firmware matrix rather than assuming every menu exists. Before coupling arms, bring them near matching reference postures and identify one leader and the correct follower. The manual warns against two followers and conflicting CAN pushes on a connected pair. A role change can cause rapid synchronization; do not connect arbitrary mismatched poses.

<details>

<summary>6.4 Coordinated control — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.4 Coordinated control](<../../.gitbook/assets/image (1186).png>)

</details>

#### 6.5 Speed Regulation <a href="#bgcrw" id="bgcrw"></a>

The global speed percentage scales motion within the controller configuration; it does not redefine joint limits, guarantee braking distance or validate a recorded path. Begin at a low setting for commissioning, apply it only in the mode that accepts the change and verify actual behavior with a small checked movement. A trajectory or leader–follower mode may require returning to Web/GUI control before editing the setting.

#### 6.6 Trajectory <a href="#id-6.6-trajectory" id="id-6.6-trajectory"></a>

Create a separately named trajectory, load the current pose and add only checked points. Import loads a saved library; Export preserves it; Delete removes the selected entry. The secondary editor supports adding, deleting and changing individual points. Send/Run can execute once, a finite count or continuously depending on settings, so inspect the loop/count and every intermediate path before replay. Export a backup before edits, start with one short unloaded run and verify stop/resume behavior before considering repetition.

<details>

<summary>6.6 Trajectory — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.6 Trajectory](<../../.gitbook/assets/image (1187).png>)

</details>

#### 6.7 Set Zero Position <a href="#auyaw" id="auyaw"></a>

NERO's zero is a physical reference, not an arbitrary convenient pose. Manual setting requires supporting and disabling the selected joint, placing it at the documented reference and confirming; re-enabling can move it. Automatic zero searches can travel to mechanical limits and then return, and J6 has a further calibration movement. The newer dedicated procedure restricts all-joint automatic calibration to the upright, unloaded/no-gripper configuration; side mounting requires its permitted single-joint procedure and correct mounting setting. Loaded/nonstandard setups use the documented manual procedure. Preserve the old calibration and do not run either method as a connection test.

#### 6.7.1 Auto Set Zero Position <a href="#aqj79" id="aqj79"></a>

NERO's zero is a physical reference, not an arbitrary convenient pose. Manual setting requires supporting and disabling the selected joint, placing it at the documented reference and confirming; re-enabling can move it. Automatic zero searches can travel to mechanical limits and then return, and J6 has a further calibration movement. The newer dedicated procedure restricts all-joint automatic calibration to the upright, unloaded/no-gripper configuration; side mounting requires its permitted single-joint procedure and correct mounting setting. Loaded/nonstandard setups use the documented manual procedure. Preserve the old calibration and do not run either method as a connection test.

<details>

<summary>6.7.1 Auto Set Zero Position — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.7.1 Auto Set Zero Position](<../../.gitbook/assets/image (1188).png>)

</details>

#### 6.7.2 Manual Set Zero Position <a href="#nmifu" id="nmifu"></a>

NERO's zero is a physical reference, not an arbitrary convenient pose. Manual setting requires supporting and disabling the selected joint, placing it at the documented reference and confirming; re-enabling can move it. Automatic zero searches can travel to mechanical limits and then return, and J6 has a further calibration movement. The newer dedicated procedure restricts all-joint automatic calibration to the upright, unloaded/no-gripper configuration; side mounting requires its permitted single-joint procedure and correct mounting setting. Loaded/nonstandard setups use the documented manual procedure. Preserve the old calibration and do not run either method as a connection test.

<details>

<summary>6.7.2 Manual Set Zero Position — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.7.2 Manual Set Zero Position](<../../.gitbook/assets/image (1189).png>)

</details>

#### 6.8 System Settings <a href="#e0zbr" id="e0zbr"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### 6.8.1 Joint Limit Settings <a href="#yht1m" id="yht1m"></a>

Record the existing minimum/maximum angle, speed and acceleration for every joint before editing. The GUI Edit→Save sequence writes settings; narrower workcell limits should remain within the physical model/firmware envelope. An IK failure or blocked path is not solved by widening limits. Verify one deliberate change and preserve a rollback copy; resetting defaults can remove application-specific restrictions.

<details>

<summary>6.8.1 Joint Limit Settings — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.8.1 Joint Limit Settings](<../../.gitbook/assets/image (1190).png>)

</details>

#### 6.8.2 End Effector Speed Settings <a href="#til6j" id="til6j"></a>

This panel limits endpoint linear/angular velocity and acceleration, separately from global speed percentage and individual joint limits. Record both units and values before editing. A Cartesian path can still require high joint speed near a singularity even when endpoint speed looks small. Initialize/Reset restores factory settings and may remove tuned application limits; do not press it as a harmless view refresh.

<details>

<summary>6.8.2 End Effector Speed Settings — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.8.2 End Effector Speed Settings](<../../.gitbook/assets/image (1192).png>)

![Manufacturer NERO illustration for 6.8.2 End Effector Speed Settings](<../../.gitbook/assets/image (1191).png>)

</details>

#### 6.8.3 Collision Protection Settings <a href="#mapdt" id="mapdt"></a>

Collision sensitivity is configured per joint and must be interpreted for the installed firmware. The historical GUI illustrates levels 1–8; newer material also includes0 as disabled. Do not copy a numeric setting across revisions without its definition. Keep sensitivity active as appropriate to the supported application, investigate recurrent triggers and verify tool mass/mount/zero before reducing sensitivity. This feature does not replace collision-free planning or certified personnel protection.

<details>

<summary>6.8.3 Collision Protection Settings — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.8.3 Collision Protection Settings](<../../.gitbook/assets/image (1193).png>)

</details>

#### 6.8.4 Mounting Position Settings <a href="#q0xjw" id="q0xjw"></a>

The mounting setting must describe the physical upright, side or inverted installation so gravity compensation and motion coordinates agree with the arm. Record the previous setting, select the actual orientation in motor/system configuration and confirm it before teaching or actuation. On NERO, the manual defines side mounting relative to the Ethernet-port direction at the reference pose. The arm supporting an orientation does not qualify every clamp or mobile base for it.

<details>

<summary>6.8.4 Mounting Position Settings — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.8.4 Mounting Position Settings](<../../.gitbook/assets/image (1194).png>)

</details>

#### 6.8.5 End Effector Configuration <a href="#rpdak" id="rpdak"></a>

Enter the actual tool mass, center of gravity and geometric/TCP offset for the mounted accessory, keeping units and reference axes explicit. Gravity compensation and endpoint motion depend on these values. Read/save the current configuration before a tool change, verify the keyed orientation and compare a known supported pose afterward. An unloaded calibration or bare-flange model cannot be assumed valid with a heavy or reversed tool.

<details>

<summary>6.8.5 End Effector Configuration — manufacturer figures</summary>

![Manufacturer NERO illustration for 6.8.5 End Effector Configuration](<../../.gitbook/assets/image (1195).png>)

</details>

#### 7 Configuration <a href="#d7lwh" id="d7lwh"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### 7.1 Ethernet Port Settings <a href="#osr14" id="osr14"></a>

The factory NERO wired address is 10.90.0.150. Use an unused computer address on the same subnet, such as10.90.0.153/24 for an isolated direct link, then open the controller page. Record old IP/mask/gateway before changing network settings and retain a tested alternative access path. A saved address change can disconnect the current browser session; it is unrelated to joint zero or motor calibration.

<details>

<summary>7.1 Ethernet Port Settings — manufacturer figures</summary>

![Manufacturer NERO illustration for 7.1 Ethernet Port Settings](<../../.gitbook/assets/image (1196).png>)

</details>

#### 7.2 Hotspot Settings <a href="#c3mor" id="c3mor"></a>

The NERO factory hotspot follows agx-7ax-xx with the published initial password12345678, and the web page is at 192.168.31.1 with initial admin/123456 credentials. Read the actual configured values if a previous owner changed them. Hotspot configuration and Ethernet address settings are separate; record both and keep a fallback route before applying changes. Change default credentials before shared-network operation.

<details>

<summary>7.2 Hotspot Settings — manufacturer figures</summary>

![Manufacturer NERO illustration for 7.2 Hotspot Settings](<../../.gitbook/assets/image (1197).png>)

</details>

#### 8 Upgrade <a href="#li6zm" id="li6zm"></a>

NERO separates embedded software updates from joint-module firmware. Read versions and hardware identity first, obtain a matched package and support the disabled arm. For joint firmware, enter Upgrade Mode, verify that the intended joints are recognized, update with stable power, then explicitly Exit Upgrade after completion; remaining in upgrade mode prevents ordinary operation. Recheck calibration, mounting, tool and the SDK firmware profile afterward. Do not treat the older26 V PDF or generic raw protocol as the authority for the newer controller.

#### 8.1 Software Upgrade <a href="#einpj" id="einpj"></a>

NERO separates embedded software updates from joint-module firmware. Read versions and hardware identity first, obtain a matched package and support the disabled arm. For joint firmware, enter Upgrade Mode, verify that the intended joints are recognized, update with stable power, then explicitly Exit Upgrade after completion; remaining in upgrade mode prevents ordinary operation. Recheck calibration, mounting, tool and the SDK firmware profile afterward. Do not treat the older26 V PDF or generic raw protocol as the authority for the newer controller.

<details>

<summary>8.1 Software Upgrade — manufacturer figures</summary>

![Manufacturer NERO illustration for 8.1 Software Upgrade](<../../.gitbook/assets/image (1198).png>)

</details>

#### 8.2 Firmware Upgrade <a href="#abh87" id="abh87"></a>

NERO separates embedded software updates from joint-module firmware. Read versions and hardware identity first, obtain a matched package and support the disabled arm. For joint firmware, enter Upgrade Mode, verify that the intended joints are recognized, update with stable power, then explicitly Exit Upgrade after completion; remaining in upgrade mode prevents ordinary operation. Recheck calibration, mounting, tool and the SDK firmware profile afterward. Do not treat the older26 V PDF or generic raw protocol as the authority for the newer controller.

<details>

<summary>8.2 Firmware Upgrade — manufacturer figures</summary>

![Manufacturer NERO illustration for 8.2 Firmware Upgrade](<../../.gitbook/assets/image (1199).png>)

</details>

#### 9 Secondary Development <a href="#m3qcd" id="m3qcd"></a>

Use the current model/firmware-specific SDK, CAN mapping and ROS description rather than copying another arm profile. The public implementation defines message units, version-dependent encoders/decoders and connection cleanup; raw protocol documents can be gated or older. Query firmware before selecting a profile, preserve the supplied CAN topology and begin with stationary fresh feedback. Keep original direct SDK/protocol/model downloads with the project revision and do not equate a source review with compilation or hardware validation.

<details>

<summary>9 Secondary Development — manufacturer figures</summary>

![Manufacturer NERO illustration for 9 Secondary Development](<../../.gitbook/assets/image (1200).png>)

</details>

#### 10 Robotic Arm CAN Protocol <a href="#egpj6" id="egpj6"></a>

Use the current model/firmware-specific SDK, CAN mapping and ROS description rather than copying another arm profile. The public implementation defines message units, version-dependent encoders/decoders and connection cleanup; raw protocol documents can be gated or older. Query firmware before selecting a profile, preserve the supplied CAN topology and begin with stationary fresh feedback. Keep original direct SDK/protocol/model downloads with the project revision and do not equate a source review with compilation or hardware validation.

#### 11 Maintenance and Servicing <a href="#djrl0" id="djrl0"></a>

Return through a checked path to the supported storage posture, stop the active mode and power down before cleaning or mechanical inspection. Do not reinterpret a storage instruction as routine recalibration of zero. Inspect fasteners, motor/bracket damage, cable jackets and connector retention; clean the exterior with a lightly dampened cloth without flooding openings. Keep the specified−20…50 °C and 25–85 %RH noncondensing environment where applicable, avoid strong magnetic fields and allow hot joints to cool before handling. Log wear or repeated faults before replacing parts.

#### 11.1 Storage Notes <a href="#jwysf" id="jwysf"></a>

Return through a checked path to the supported storage posture, stop the active mode and power down before cleaning or mechanical inspection. Do not reinterpret a storage instruction as routine recalibration of zero. Inspect fasteners, motor/bracket damage, cable jackets and connector retention; clean the exterior with a lightly dampened cloth without flooding openings. Keep the specified−20…50 °C and 25–85 %RH noncondensing environment where applicable, avoid strong magnetic fields and allow hot joints to cool before handling. Log wear or repeated faults before replacing parts.

#### 11.2 Servicing Notes <a href="#gb3xn" id="gb3xn"></a>

Return through a checked path to the supported storage posture, stop the active mode and power down before cleaning or mechanical inspection. Do not reinterpret a storage instruction as routine recalibration of zero. Inspect fasteners, motor/bracket damage, cable jackets and connector retention; clean the exterior with a lightly dampened cloth without flooding openings. Keep the specified−20…50 °C and 25–85 %RH noncondensing environment where applicable, avoid strong magnetic fields and allow hot joints to cool before handling. Log wear or repeated faults before replacing parts.

#### 11.3 Emergency Handling <a href="#g4akm" id="g4akm"></a>

The manual describes power disconnection as an emergency measure and warns that the disabled arm can drop immediately. Plan support and access before actuation; never reach into the sweep merely to unplug a connector. GUI pause/stop depends on a live communication path and can preserve a trajectory for later resumption. Clear the workcell and inspect pending commands before restart. Neither power removal nor a PC toggle is a complete certified injury-prevention system.

#### Appendix: Dimension Drawings <a href="#f42f0" id="f42f0"></a>

Use the dimensioned view for the identified bare-arm, tool-equipped, base or end-flange assembly. Keep its viewpoint, units and model revision with any fixture design; an axonometric picture is not a scale drawing. Check hole pattern, screw engagement, cable exit and the complete swept volume against the physical parts before machining. The numerical arm limits and actual tool transform remain separate from the drawing envelope.

#### 1 Robotic Arm Dimensions <a href="#hltmk" id="hltmk"></a>

Use the dimensioned view for the identified bare-arm, tool-equipped, base or end-flange assembly. Keep its viewpoint, units and model revision with any fixture design; an axonometric picture is not a scale drawing. Check hole pattern, screw engagement, cable exit and the complete swept volume against the physical parts before machining. The numerical arm limits and actual tool transform remain separate from the drawing envelope.

<details>

<summary>1 Robotic Arm Dimensions — manufacturer figures</summary>

![Manufacturer NERO illustration for 1 Robotic Arm Dimensions](<../../.gitbook/assets/资源 7 (2).png>)

</details>

#### 2 Robotic Arm with Dexterous Hand <a href="#iw9im" id="iw9im"></a>

Dexterous-hand control applies only to a supported fitted hand and its matching flange, wiring, device identity and controller configuration. A hand illustration is not an inclusion guarantee for the bare arm. Preserve the associated mounting drawing and tool mass/center-of-gravity data, then verify individual hand functions with the arm supported before combined motion. Avoid reusing a two-finger gripper ID/configuration for a multi-actuator hand.

<details>

<summary>2 Robotic Arm with Dexterous Hand — manufacturer figures</summary>

![Manufacturer NERO illustration for 2 Robotic Arm with Dexterous Hand](<../../.gitbook/assets/image (1201).png>)

![Manufacturer NERO illustration for 2 Robotic Arm with Dexterous Hand](<../../.gitbook/assets/image (1202).png>)

</details>

#### 3 Base <a href="#wdxps" id="wdxps"></a>

Use the dimensioned view for the identified bare-arm, tool-equipped, base or end-flange assembly. Keep its viewpoint, units and model revision with any fixture design; an axonometric picture is not a scale drawing. Check hole pattern, screw engagement, cable exit and the complete swept volume against the physical parts before machining. The numerical arm limits and actual tool transform remain separate from the drawing envelope.

#### 4 Dexterous Hand Diagram <a href="#kyqfk" id="kyqfk"></a>

Dexterous-hand control applies only to a supported fitted hand and its matching flange, wiring, device identity and controller configuration. A hand illustration is not an inclusion guarantee for the bare arm. Preserve the associated mounting drawing and tool mass/center-of-gravity data, then verify individual hand functions with the arm supported before combined motion. Avoid reusing a two-finger gripper ID/configuration for a multi-actuator hand.

<details>

<summary>4 Dexterous Hand Diagram — manufacturer figures</summary>

![Manufacturer NERO illustration for 4 Dexterous Hand Diagram](<../../.gitbook/assets/image (1204).png>)

</details>

#### 5 Dexterous Hand Flange Mounting Diagram <a href="#wif9z" id="wif9z"></a>

Dexterous-hand control applies only to a supported fitted hand and its matching flange, wiring, device identity and controller configuration. A hand illustration is not an inclusion guarantee for the bare arm. Preserve the associated mounting drawing and tool mass/center-of-gravity data, then verify individual hand functions with the arm supported before combined motion. Avoid reusing a two-finger gripper ID/configuration for a multi-actuator hand.

<details>

<summary>5 Dexterous Hand Flange Mounting Diagram — manufacturer figures</summary>

![Manufacturer NERO illustration for 5 Dexterous Hand Flange Mounting Diagram](<../../.gitbook/assets/image (1205).png>)

</details>

#### Development Resources <a href="#development-resources" id="development-resources"></a>

Use the current model/firmware-specific SDK, CAN mapping and ROS description rather than copying another arm profile. The public implementation defines message units, version-dependent encoders/decoders and connection cleanup; raw protocol documents can be gated or older. Query firmware before selecting a profile, preserve the supplied CAN topology and begin with stationary fresh feedback. Keep original direct SDK/protocol/model downloads with the project revision and do not equate a source review with compilation or hardware validation.

#### Additional model resources

The following direct resources retain the manufacturer/model context of the detailed manual. Select the package matching the installed hardware and firmware; a historical download is not an update recommendation.

* [View NERO gripper on OpenELAB](https://openelab.io/products/agilex-nero-gripper)
* [AgileX arm ROS 2 driver](https://github.com/agilexrobotics/agx_arm_ros/tree/ros2)
* [NERO firmware compatibility reference](https://github.com/agilexrobotics/pyAgxArm/blob/master/docs/nero/firmware_reference.md)

### &#x20;<a href="#f1zmr" id="f1zmr"></a>

See [Product overview](nero-user-manual.md#ffsaj) for the model-specific procedure and its source conditions.

### &#x20;<a href="#z7gt8" id="z7gt8"></a>

Seefor the model-specific procedure and its source conditions.

## References and validation

Reviewed current manufacturer manuals, quick-start, calibration/resource pages and pinned SDK/ROS source. The base, keyed connector and mounting/workspace diagrams were visually checked; retained images remain attributed to AgileX. The older PDF's26 V and joint-range differences are explicitly bounded by newer guidance and controller verification.

The original logger passed Python syntax parsing. No SDK installation, CAN connection, firmware update, calibration, physical motion, payload or precision test was run. The login-gated V1.2 raw protocol was not treated as read; the example uses the public SDK's documented firmware query and joint decoder. For related six-axis models, see [PiPER](https://wiki.openelab.io/robotics/agilex/piper-product-user-manual) and [PiPER-H](https://wiki.openelab.io/robotics/agilex/piper-h-user-manual); their limits and geometry do not apply to NERO.
