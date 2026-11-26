---
description: >-
  Secure the standard1.5 kg PiPER, verify24 V power and CAN, select its firmware
  profile, read fresh joints and progress to controlled GUI/ROS 2 operation.
---

# AgileX PiPER: CAN setup, firmware matching and joint-feedback guide

{% hint style="info" %}
[**View AgileX PiPER 6-DOF robotic arm on OpenELAB**](https://openelab.io/products/agilex-piper-ros-ai-arm?variant=45854559240390)

**Model:** PiPER standard · **SKU:** `Agilex-PiPER` · **Option:** Default Title
{% endhint %}

## Product overview

The **AgileX PiPER standard** is a six-axis CAN-controlled arm for manipulation experiments, teaching and robot integration. Start by securing the base, identifying the installed firmware and reading joint feedback with the motors left disabled. A USB-CAN device appearing on a computer does not establish that the arm is powered, in follower mode or reporting correctly.

This guide covers the standard **1.5 kg** PiPER. PiPER-H, PiPER-L, PiPER-X and NERO have separate mechanical models and software selections. A gripper, teacher pendant and desktop fixture are separate accessories; confirm the order contents before budgeting tool mass or choosing an end-effector driver. The current official development path is `pyAgxArm`; the older `piper_sdk` and `piper_ros` remain useful when maintaining their matching applications. [Manufacturer resource index](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/vfn6piw3lqc7g1rs), [current SDK](https://github.com/agilexrobotics/pyAgxArm).

![AgileX PiPER standard six-axis arm](<../../.gitbook/assets/PiPER Product User Manual image 1>)

_Manufacturer figure retained from the original OpenELAB manual. Geometry and accessories must match the received arm._

## Applications

Use PiPER for constrained pick-and-place, camera-to-arm calibration, trajectory recording and replay, or leader–follower data collection. Establish separate checkpoints for mechanics, CAN transport, joint feedback, tool geometry and motion before combining them into a learned policy.

For a vision experiment, first compare a stationary camera target with the arm's reported flange pose. Store the camera-to-base transform, TCP offset, tool identity and firmware with each dataset. A point expressed in camera coordinates cannot be sent directly as a base-frame Cartesian target.

For imitation learning, record the model and joint convention with every sequence. Keep commanded positions, measured positions and timestamps distinct. A policy's nominal sampling rate is not the measured arrival rate of CAN feedback. Evaluate inference against recorded observations before giving it command ownership.

## Specifications

| Parameter                   | Standard PiPER reference                                                                 |
| --------------------------- | ---------------------------------------------------------------------------------------- |
| Axes / payload              | 6 / 1.5 kg                                                                               |
| Arm mass / working radius   | 4.2 kg / 626.75 mm                                                                       |
| Repeatability               | ±0.1 mm, manufacturer conditions                                                         |
| Arm supply                  | 24 V DC; manual operating range 24–26 V                                                  |
| Arm power                   | ≤120 W maximum; ≤40 W average reference                                                  |
| External supply requirement | Regulated, never above 26 V, at least10 A current capability per connection instructions |
| Base pattern                | Four M5 positions on 70 × 70 mm spacing                                                  |
| Environment                 | −20 to 50 °C; 25–85% RH, noncondensing                                                   |
| End auxiliary output        | 24 V, 2 A maximum, exact connector orientation below                                     |
| Control transport           | CAN through supplied USB-CAN adapter; 1 Mbit/s Linux setup                               |

Mechanical/electrical values: [PiPER manual V1.0, June2025](https://cdn.shopify.com/s/files/1/0551/0630/6141/files/PIPER_Product_User_Manual_EN_1.pdf?v=1794214904), pp.11–17 and connection section. The supply's current capability is not continuous arm consumption. [Current CAN setup](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/can_user.md).

| Joint | Mechanical range | Published maximum speed |
| ----- | ---------------- | ----------------------- |
| J1    | −154° to 154°    | 180°/s                  |
| J2    | 0° to 195°       | 195°/s                  |
| J3    | −175° to 0°      | 180°/s                  |
| J4    | −102° to 102°    | 225°/s                  |
| J5    | −75° to 75°      | 225°/s                  |
| J6    | −120° to 120°    | 225°/s                  |

These standard-model limits come from the manual's motion table. They are ceilings, not initial jog settings. Preserve the received controller limits and inspect the configured model before changing them. The **payload curve** is more useful than treating1.5 kg as a guarantee throughout a rectangular workspace: include tool, adapter, object and cable forces in the load budget.

![Standard PiPER workspace and payload curve](<../../.gitbook/assets/PiPER Product User Manual image 19>)

_Manufacturer load diagram retained from the original guide; consult the complete manual for the plotted coordinate convention._

## Hardware and connections

### Mounting, tools and coordinate references

Secure all four base mounting positions to a sufficiently rigid support. Check screw engagement and underside clearance using the actual base drawing; do not infer screw length or tightening torque from the M5 thread alone. A desktop clamp fixture needs its own table-edge and stability checks: see the [PiPER desktop fixture guide](piper-desktop-fixture.md).

With power isolated, fit the appropriate flange/adaptor and supported tool, route its cable with slack throughout the intended envelope, and inspect interference around J5/J6. Distinguish a tool's mechanical stop from a calibrated encoder zero. The manual's illustrated flange sequence and screw lengths apply to those supplied parts; a custom flange requires its own drawing and engagement check.

The base origin, user frame, flange frame and TCP are separate objects. Record which frame a pose uses and whether its rotation is Euler angles or another representation. At a singularity, a modest Cartesian change can demand large joint changes. Begin commissioning in joint space and inspect the planned joint path before using linear or arc Cartesian motion.

### Power and CAN harness

1. Isolate power and secure the arm in its supported commissioning posture. Connect the intended J2/inter-joint harness according to the received assembly diagram.
2. Fit the keyed power/CAN cable using its red alignment marks. Release the locking sleeve when disconnecting; do not twist or pull on the wires.
3. Connect CAN-H/CAN-L to the matching adapter terminals, then the supplied adapter/data cable. The standard manual identifies yellow as CAN-H and blue as CAN-L on its supplied harness; a replacement cable must be verified independently.
4. Complete the adapter's power-side connections and inspect polarity before applying AC power. Follow the exact manual's illustrated power-on sequence; USB is the host data connection, not the 24 V arm supply.
5. Observe the base status indicator and then establish host communication. Leave the arm disabled for the diagnostic below.

The drawing's labels **4–7 are figure callouts**, not a seven-pin connector numbering scheme. Use the keyed mating face and cable markings; never transfer a rear solder-side view directly to the front mating face.

![PiPER keyed power and CAN connector with manufacturer callouts](<../../.gitbook/assets/PiPER Product User Manual image 5>)

_Manufacturer figure;_ [_electrical interface, manual pp.15–17_](https://cdn.shopify.com/s/files/1/0551/0630/6141/files/PIPER_Product_User_Manual_EN_1.pdf?v=1794214904)_. The power pins carry arm supply, not3.3 V logic._

### End-effector power and bus ownership

The XT30 2+2 diagram, viewed in its published orientation, places **positive above negative** and **CAN-H left of CAN-L**. The24 V/2 A auxiliary limit does not authorize arbitrary CAN devices: the current manufacturer instructions restrict the end CAN connection to supported AgileX equipment. Confirm a custom tool's separate interface with the manufacturer rather than assuming that every CAN gripper is compatible.

![PiPER end-joint auxiliary power and CAN orientation](<../../.gitbook/assets/PiPER Product User Manual image 29>)

_Original manufacturer connector figure retained._ [_Current electrical instructions_](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn)_._

For one arm, preserve factory termination. Before combining leader/follower arms, inventory all terminations, addressing and adapter topology. Do not install another resistor merely because CAN networks commonly use120Ω ends; the delivered arm already contains a configured matching network. Use separate adapter/device identities for initial multi-arm diagnostics.

## Software and development resources

### Select a model and a firmware profile

The reviewed `pyAgxArm` source is commit **`d90e234ba8e408cfa964b38aa9120b3131fc9f85`**. Select **`ArmModel.PIPER`**, Linux **`socketcan`**, and the actual CAN interface. The configuration keyword is literally **`firmeware_version`**, including the upstream spelling. Joint feedback from this API is in **radians**; the older SDK and GUI can use different units. [Factory/configuration implementation](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/pyAgxArm/api/agx_arm_factory.py).

| Reported arm firmware                               | Reviewed SDK profile |
| --------------------------------------------------- | -------------------- |
| S-V1.8-2 or earlier                                 | `PiperFW.DEFAULT`    |
| S-V1.8-3 through S-V1.8-7                           | `PiperFW.V183`       |
| S-V1.8-8                                            | `PiperFW.V188`       |
| S-V1.8-9 or later, within the published SDK mapping | `PiperFW.V189`       |

[Official firmware matrix](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/piper/firmware_reference.md). The MIT torque encoding and mode values change across these profiles. Reusing an older torque example after a firmware update can change the command's meaning. Keep advanced MIT/CPV control out of the first result; validate the precise firmware, coefficients and joint behavior before using it.

The upstream environment list includes Ubuntu 18.04/20.04/22.04/24.04 and Python≥3.6. Use a currently maintained host and the appropriate Python/ROS environment. Windows requires the separate `python-can-agx-cando` backend; Linux scripts are not Windows setup steps. macOS uses a different serial-CAN backend. The standalone route below deliberately uses Ubuntu/SocketCAN. [SDK environment/backend instructions](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/README.md).

### Current ROS 2 versus maintained legacy applications

`agx_arm_ros` branch `ros2`, reviewed at **`747d0722074d4cebc095d8d44f3ef68d2023ba6f`**, supports an explicit `arm_type:=piper`. Preserve its submodule revisions. Its control-node defaults include **`auto_enable:=true`** and **`control_enabled:=true`**: override both for first feedback inspection. Do not use an unqualified vendor launch command as a passive visualization command. [Actual launch defaults](https://github.com/agilexrobotics/agx_arm_ros/blob/747d0722074d4cebc095d8d44f3ef68d2023ba6f/src/agx_arm_ctrl/launch/start_single_agx_arm.launch.py).

Older `piper_sdk`, `piper_ros` Noetic/Humble and `Piper_sdk_ui` use different APIs and launch layouts. Keep an existing working application on its documented stack until its API, unit and firmware migration has been reviewed. The current SDK declares LGPL-3.0-only; the legacy SDK's own license and bundled dependencies must be retained separately.

## Getting started

### Establish a passive CAN baseline

1. Check mounting, arm model, harness orientation, supply and clear workspace. Keep the mechanism supported and disabled; do not recalibrate or replay a trajectory to obtain feedback.
2. On Ubuntu 22.04/Python 3.10 install the tools and create a dedicated environment:

{% code collapsedlinecount="10" %}
```bash
sudo apt update
sudo apt install can-utils ethtool python3-venv
python3 -m venv ~/piper-env
source ~/piper-env/bin/activate
python -m pip install "git+https://github.com/agilexrobotics/pyAgxArm.git@d90e234ba8e408cfa964b38aa9120b3131fc9f85"
ip -details link show type can
```
{% endcode %}

3. Identify the supplied adapter by unplug/replug observation or the manufacturer's `find_all_can_port.sh`. Replace `can0` below if that adapter has another name. Configure it only after confirming no other application owns it:

{% code collapsedlinecount="10" %}
```bash
sudo ip link set can0 down
sudo ip link set can0 type can bitrate 1000000
sudo ip link set can0 up
ip -details -statistics link show can0
timeout 5s candump -L can0
```
{% endcode %}

**Expected result:** the intended interface is UP at 1,000,000bit/s and receives arm frames without a rising bus-off/error count. No frames calls for power, mode, wiring, adapter and termination checks; it does not justify enabling a motor. Stop `candump` after the bounded capture. [Official CAN workflow](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/can_user.md).

### Original firmware-aware feedback sampler

Save as `piper_feedback.py` in the activated environment. The first connection requests firmware; it is closed before creating a matching profile. The second connection samples six measured joints for ten seconds. It sends no enable, position, calibration or trajectory command.

{% code collapsedlinecount="10" %}
```python
import json
import math
import time
from pyAgxArm import (AgxArmFactory, ArmModel, PiperFW,
                      create_agx_arm_config, resolve_firmware_profile)

MODEL = ArmModel.PIPER
CHANNEL = "can0"


def open_arm(profile):
    config = create_agx_arm_config(robot=MODEL,
                                  firmeware_version=profile,
                                  interface="socketcan", channel=CHANNEL)
    arm = AgxArmFactory.create_arm(config)
    arm.connect()
    return arm


probe = open_arm(PiperFW.DEFAULT)
try:
    firmware = probe.get_firmware(timeout=2.0)
finally:
    probe.disconnect()
if not firmware or not firmware.get("software_version"):
    raise SystemExit("No firmware identity: inspect CAN and the matching host GUI")
profile = resolve_firmware_profile(MODEL, firmware["software_version"])
print(json.dumps({"firmware": firmware, "profile": profile}, ensure_ascii=False))
arm = open_arm(profile)
samples = 0
last_stamp = None
try:
    deadline = time.monotonic() + 10.0
    while time.monotonic() < deadline:
        joints = arm.get_joint_angles()
        if joints is not None and joints.timestamp != last_stamp:
            values = list(joints.msg)
            if len(values) != 6 or not all(math.isfinite(v) for v in values):
                raise RuntimeError("Invalid six-joint feedback")
            last_stamp = joints.timestamp
            samples += 1
            print(json.dumps({"sample": samples,
                              "angles_deg": [round(math.degrees(v), 3) for v in values],
                              "feedback_hz": joints.hz}))
        time.sleep(0.05)
finally:
    arm.disconnect()
if samples < 5:
    raise SystemExit("Insufficient fresh samples: inspect power, arm role and CAN errors")
```
{% endcode %}

{% code collapsedlinecount="10" %}
```bash
python piper_feedback.py
```
{% endcode %}

**Expected result:** a real firmware identifier, a matching profile and repeated finite six-joint samples with changing receive timestamps. A stationary arm can report constant angles; freshness comes from new feedback, not invented movement. Displayed degrees are a presentation conversion only. Source-reviewed API/thread behavior: [connect/disconnect](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/pyAgxArm/protocols/can_protocol/drivers/core/arm_driver_abstract.py), [firmware/joint readers](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/pyAgxArm/protocols/can_protocol/drivers/piper/default/driver.py).

### ArmRobotUA: connection, controlled jog and trajectory work

1. Obtain the official host application from the manufacturer resource index and record its version. Connect the detected CAN adapter, inspect feedback and confirm follower/slave role for standalone control. A leader-role arm can intentionally reject ordinary control or suppress follower-style feedback.
2. Before enabling, compare physical joint marks, measured pose, configured limits and the correct standard-model geometry. Support the arm where disabling can allow gravity movement. Identify the host E-stop control and the installation's physical stop/power isolation.
3. Under direct supervision, choose a low speed percentage and a small joint-space change that stays well inside the verified limits. Check one joint/direction at a time, stop, inspect and return deliberately. Do not start with an all-joint zero command or a saved Cartesian trajectory.
4. For a fitted gripper, first confirm its model, zero, aperture and force limits without an object. Keep fingers out; a grip-force setting is not a measured object retention force.
5. Create a short trajectory only after individual joints and stop/re-enable behavior work. In TraceLib, inspect points, ordering, speed and tool identity, then run one supervised cycle. Retain an unmodified copy before editing or importing a library.

The GUI has separate panels for joint angle/speed/acceleration limits, Cartesian speed, collision sensitivity, motor state, firmware upgrade and trajectory libraries. Read and record current values before changing one setting. Initialization buttons can restore parameters; they are not harmless refresh buttons. The current host guide describes collision settings0–8, including0=off, whereas older screenshots show1–8. Follow the installed firmware's semantics and do not present collision detection as obstacle sensing or a guaranteed person-protection function. [Updated host guide](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/ermnzf7axdt17chz).

### Teach mode, zero setting and recovery boundary

Distinguish **zero-pose movement**, **encoder-zero calibration**, **drag recording** and **trajectory replay**. They are four different operations. The wrist teaching indicator and button can start recording/replay; clear old recordings and inspect the intended mode before touching it. Follow the exact manual's supported posture and mode-exit sequence. In particular, the standard manual warns against changing from MIT/teaching into host control at a nonzero posture.

Do not rewrite zeros simply because a Cartesian pose looks unexpected. Check tool offset, coordinate frame, model, joint order and physical marks first. The manufacturer provides a dedicated joint-zero procedure and upgrade procedure. If a firmware update requires new zero calibration, perform both as one controlled maintenance task, retaining firmware identity, calibration and parameter backups. A firmware file for another PiPER variant is not selected by the shared six-axis count.

### ROS 2 feedback and simulation progression

After the standalone check, install ROS 2 and the repository dependencies according to its supported environment. In a workspace using the same Python/SDK environment as the ROS node, clone the reviewed driver and its recorded submodules:

{% code collapsedlinecount="10" %}
```bash
mkdir -p ~/agx_ws/src
cd ~/agx_ws/src
git clone -b ros2 https://github.com/agilexrobotics/agx_arm_ros.git
cd agx_arm_ros
git checkout 747d0722074d4cebc095d8d44f3ef68d2023ba6f
git submodule update --init --recursive
```
{% endcode %}

Use the repository's dependency installation instructions, source the chosen ROS distribution, then build from `~/agx_ws` with `colcon build` and source `install/setup.bash`. First inspect with control disabled:

{% code collapsedlinecount="10" %}
```bash
ros2 launch agx_arm_ctrl start_single_agx_arm.launch.py can_port:=can0 arm_type:=piper effector_type:=none auto_enable:=false control_enabled:=false
```
{% endcode %}

In another sourced terminal, use `ros2 topic list -t` and inspect the advertised feedback topic before subscribing. **Expected result:** the standard model and real joint feedback, without an automatic motor enable. For model-only work use `agx_arm_description`/RViz without a hardware control node; MoveIt planning and Isaac/Gazebo simulation are separate workflows. A successful planned path must still be checked against the physical tool, joint limits and environment before execution.

## Troubleshooting and FAQs

| Symptom                                    | Ordered diagnosis and supported recovery                                                                                                        |
| ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| USB-CAN exists, no arm frames              | Confirm arm supply/status, actual adapter, 1 Mbit/s, H/L, cable seating and follower role; inspect error counters before changing termination   |
| Bus-off or increasing errors               | Stop control clients, preserve logs, check wiring/termination and adapter; bring the interface back only after correcting the physical cause    |
| SDK import works, samples are absent       | Same interpreter/venv, actual channel/backend, power, role and firmware identification; a Python import is not CAN validation                   |
| Feedback exists but motion is rejected     | Inspect role, emergency/error state and enable state; remove conflicting control applications instead of repeatedly issuing resets              |
| Angles differ by a factor near57.3 or 1000 | Compare SDK API units: radians/degrees and metres/millimetres are separate; do not alter calibration to hide a unit error                       |
| Tool tip misses an otherwise correct pose  | Check flange-to-TCP transform, tool identity, camera/base transform and joint-zero marks independently                                          |
| Sudden drop when disabled                  | Stop operation; support the mechanism and review the specified posture/power/stop design before re-enabling                                     |
| Teach replay follows an old path           | Stop, inspect stored trajectory/mode and button state; do not test playback with people or cables in the envelope                               |
| Overcurrent/stall/disabled joint           | Remove the mechanical/load cause, inspect reported driver states and allow recovery as documented; do not simply raise current/collision limits |
| GUI or firmware mismatch                   | Record complete GUI/firmware identifiers, restore the exact supported package and repeat passive feedback checks before motion                  |

For loss of host communication, distinguish a CAN fault from power loss and a software E-stop from power isolation. Stop the command source, preserve the last status and support the mechanism before intervention. Inspect connectors, fasteners, cable bend points and abnormal heat/noise during routine maintenance; leave internal repairs and lubrication changes to the documented service procedure.

## Downloads and technical documents

| Resource                                                                                                                                             | Exact use and boundary                                                                                    |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| [Official PiPER manual PDF](https://cdn.shopify.com/s/files/1/0551/0630/6141/files/PIPER_Product_User_Manual_EN_1.pdf?v=1794214904)                  | V1.0 June2025; electrical, workspace/load curves, installation, GUI, maintenance and dimensional drawings |
| [Current manufacturer resource index](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/vfn6piw3lqc7g1rs)                                          | Model identification, GUI downloads, firmware/zero videos, CAD and technical posts                        |
| [Current English manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn)                                                       | Readable manufacturer's updated online copy; includes terminal power and supply requirements              |
| [Host application guide](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/ermnzf7axdt17chz)                                                       | Roles, operation modes, parameter panels, upgrade/zero and overload diagnostics                           |
| [Current Python SDK source archive](https://github.com/agilexrobotics/pyAgxArm/archive/d90e234ba8e408cfa964b38aa9120b3131fc9f85.zip)                 | Reviewed source snapshot; LGPL-3.0-only; not an arm firmware image                                        |
| [Firmware/profile matrix](https://github.com/agilexrobotics/pyAgxArm/blob/d90e234ba8e408cfa964b38aa9120b3131fc9f85/docs/piper/firmware_reference.md) | Driver selection, MIT encodings and model-specific sign handling                                          |
| [ROS 2 driver](https://github.com/agilexrobotics/agx_arm_ros/tree/747d0722074d4cebc095d8d44f3ef68d2023ba6f)                                          | Hardware control, passive-feedback flags, model selection and submodule-based description                 |
| [URDF/meshes](https://github.com/agilexrobotics/agx_arm_urdf)                                                                                        | Exact standard PiPER model, flange and tool geometry                                                      |
| [Simulation and MoveIt resources](https://github.com/agilexrobotics/agx_arm_sim)                                                                     | Planning/simulation; verify model and frame conventions before connecting hardware                        |
| [Legacy PiPER SDK](https://github.com/agilexrobotics/piper_sdk)                                                                                      | Maintain older applications with their matching API and firmware                                          |
| [Legacy SDK UI](https://github.com/agilexrobotics/Piper_sdk_ui)                                                                                      | Preserve source link for applications built around that interface                                         |
| [Legacy Isaac Sim models](https://github.com/agilexrobotics/piper_isaac_sim)                                                                         | Retained simulation source; choose the standard model, not H/L/X geometry                                 |

### Retained release-specific resources

These historical links remain useful for reproducing an existing installation; select a current supported release through the resource index for a new setup.

| Original resource                                                                                                                                                                                                                                                                                                                                                     | Scope                                                                    |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| [ArmRobotUA1.5.2.260310 executable](https://www.dropbox.com/scl/fi/78e4ch20ok9n040onay0y/ArmRobotUA_V1.5.2.260310_release.exe?rlkey=q4q1xr9f7k1gc5j0vtl803m5f\&st=kw1yaszi\&dl=0)                                                                                                                                                                                     | Manufacturer-linked Windows host build; download only, not executed here |
| [Original ROS Noetic branch](https://github.com/agilexrobotics/Piper_ros/tree/ros-noetic-no-aloha)                                                                                                                                                                                                                                                                    | Legacy ROS 1 configuration                                               |
| [Original ROS Humble branch](https://github.com/agilexrobotics/Piper_ros/tree/ros-humble-no-aloha)                                                                                                                                                                                                                                                                    | Legacy ROS 2 configuration, distinct from current agx\_arm\_ros          |
| [Legacy MoveIt1](https://github.com/agilexrobotics/piper_ros/tree/noetic/src/piper_moveit) / [MoveIt2](https://github.com/agilexrobotics/piper_ros/tree/humble/src/piper_moveit)                                                                                                                                                                                      | Matching branch-specific planning examples                               |
| [Legacy Gazebo](https://github.com/agilexrobotics/piper_ros/tree/noetic/src/piper_sim/piper_gazebo) / [URDF](https://github.com/agilexrobotics/piper_ros/tree/noetic/src/piper_description/urdf)                                                                                                                                                                      | Legacy simulation and geometry sources                                   |
| <p><a href="https://github.com/agilexrobotics/piper_sdk/tree/b847e5393a7ce6ff8508d713eca7bdd3a42421b4/piper_sdk/demo">PiPER Python SDK demos (V2/V3, pinned source)</a></p><p>Select the demo interface for the installed firmware and inspect each example before running it. Current V2/V3 demos do not establish compatibility with a legacy PiPER controller.</p> | Read each demo before running: some enable or move the arm               |

The manual's dimensional section covers the zero posture, complete arm, leader/follower grippers, base and end flange. Use its drawings for fabrication; do not scale a screenshot. Existing drawing references are retained below.

![PiPER end-of-arm dimensional reference](<../../.gitbook/assets/PiPER Product User Manual image 73>)

_Manufacturer dimensional figure retained from the original manual; check the complete drawing and received revision before machining._

### Operating environment and inspection reference

These arms have no built-in automatic obstacle-avoidance sensing. The manufacturer's ordinary enclosure rating is **IP22 unless customized**; this does not qualify rain, washdown or conductive dust exposure. Use the stated −20 to +50 °C and 25–85% RH noncondensing environment. Keep people outside the complete arm/tool sweep, operate within sight and secure hair/clothing that could catch. The manufacturer excludes unsupervised use by people under 18 and requires the complete installation, including other machines and its stop arrangement, to be assessed separately.

Before operation, check base/tool fasteners, harness retention, jacket damage, deformed brackets and visible motor faults. Stop on abnormal motion or a controller error, preserve the diagnostic record and resolve the cause before clearing it. Do not modify protective measures or expose the arm to strong permanent magnetic fields. After demanding operation, isolate/support it and allow the manufacturer's stated **one-hour cooling interval** before handling hot joints. Clean only the exterior using a dry or lightly water-dampened cloth; do not flood connectors. The arm manual and diagrams remain part of the installation record, rather than a claim that a GUI stop or collision sensitivity makes a completed cell safe.

[Manufacturer operating and safety reference](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn).

### Arm and optional-tool reference details

The arm uses an aluminum-alloy frame with a plastic enclosure and an integrated controller. The manual reports noise below 60 dB under its stated conditions; this is not a measured result for the reader's installation. Optional gripper and teaching accessories have their own integrated controllers, rubber contact surfaces, CAN communication and flange mounting. Their listed 24 V supply, up-to-50 W maximum and 30 W comprehensive power figures are accessory specifications, not extra current available from an arbitrary host port. Keep the end-output limit above when choosing a tool.

Historical accessory tables describe a 500 g two-finger gripper and a 550 g teaching handle with ±0.5 mm stated accuracy. Some older English tables give a 0–100 mm opening for both, while newer Chinese teaching-handle tables give **0–70 mm**. Those values identify differing documentation/accessory revisions; read the actual handle label and matched drawing before choosing a stroke. The two-finger gripper's 0–100 mm opening is separate. Do not use arm joint travel as a tool-opening range.

[Manufacturer operating and safety reference](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn).

### Base indicators and harness reference

Keep the manufacturer's mating-view drawing with the cable. For the numbered PiPER/PiPER-H panel, 1 identifies the external power/communication connector, 2 the indicator, 3 the inter-joint connector, and 4/5/6/7 identify power positive, power negative, CAN-H and CAN-L in that drawing. They are **drawing labels, not a generic plug pin numbering standard**. Align the red marks and release the connector sleeve without pulling wires.

| Base indication | Meaning in the model manual                                                              | Next check                                                                                          |
| --------------- | ---------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| Green flashing  | Normal running indication                                                                | Verify fresh feedback and fault state before enabling                                               |
| Green steady    | H manual: main-controller initialization; older standard manual: abnormal power-on state | Allow boot, then inspect power/controller state if it persists; do not infer ready from green alone |
| Red flashing    | Fault or upgrade mode                                                                    | Read fault/version/mode and confirm whether an upgrade is intentionally active                      |

The end teaching light is a different indicator: off means stopped, steady green recording and flashing green playback. Preserve the factory single-arm termination: the manual illustrates switch 1 down/on and switch 2 up/off, described as a 60 Ω arrangement. Its multi-arm switch wording is topology-specific and translated ambiguously; obtain the matching topology diagram before changing it rather than converting that sentence into a universal CAN termination rule. External CAN is documented as CAN 2.0B, 1 Mbit/s, with Motorola/MSB field layout; the matched SDK's model/firmware encoder determines actual payload units.

[Manufacturer operating and safety reference](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn).

### Detailed operating reference

The following model-specific operating details and native manufacturer illustrations complement the commissioning procedure above. GUI screenshots depict their documented release; current firmware, power and calibration requirements take precedence where versions differ. [Manufacturer manual](https://agilexsupport.yuque.com/staff-hso6mo/alxgtf/apuyzk6ei2ubdrcn).

#### PiPER Product User Manual

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### AgileX PiPER Robotic Arm Gripper <a href="#agilex-piper-robotic-arm-gripper" id="agilex-piper-robotic-arm-gripper"></a>

The illustrated optional tool is a separate fitted accessory, not part of every bare-arm order. Confirm its exact model, supply, firmware/device identity and mechanical flange before connection. The two-finger gripper and teaching handle have different opening ranges, mass and feedback roles. Include the tool in payload/TCP configuration and verify motion direction with a light test object before using it to retain anything.

#### AgileX PiPER Teacher Control Pendant <a href="#agilex-piper-teacher-control-pendant" id="agilex-piper-teacher-control-pendant"></a>

The illustrated optional tool is a separate fitted accessory, not part of every bare-arm order. Confirm its exact model, supply, firmware/device identity and mechanical flange before connection. The two-finger gripper and teaching handle have different opening ranges, mass and feedback roles. Include the tool in payload/TCP configuration and verify motion direction with a light test object before using it to retain anything.

<details>

<summary>AgileX PiPER Teacher Control Pendant — manufacturer figures</summary>

![Manufacturer PiPER illustration for AgileX PiPER Teacher Control Pendant](<../../.gitbook/assets/PiPER Product User Manual image 2>)

![Manufacturer PiPER illustration for AgileX PiPER Teacher Control Pendant](<../../.gitbook/assets/PiPER Product User Manual image 1>)

</details>

#### 1 Introduction <a href="#ka0bu" id="ka0bu"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

#### 1.1 Product list <a href="#id-5ikyh" id="id-5ikyh"></a>

Inventory the arm, supplied USB-CAN adapter, power adapter/cable, mounting hardware and tools against the ordered package. Optional gripper, teaching handle, dexterous hand and desktop fixture remain separate items unless listed. The model-specific Specifications table above distinguishes rated payload, reach, mass, joint travel/speed and accessory limits. Treat manufacturer repeatability/power/environment figures as conditions to verify in the actual setup, not measurements from this guide.

#### 1.2 Performance Parameters <a href="#eqs02" id="eqs02"></a>

Inventory the arm, supplied USB-CAN adapter, power adapter/cable, mounting hardware and tools against the ordered package. Optional gripper, teaching handle, dexterous hand and desktop fixture remain separate items unless listed. The model-specific Specifications table above distinguishes rated payload, reach, mass, joint travel/speed and accessory limits. Treat manufacturer repeatability/power/environment figures as conditions to verify in the actual setup, not measurements from this guide.

<details>

<summary>1.2 Performance Parameters — manufacturer figures</summary>

![Manufacturer PiPER illustration for 1.2 Performance Parameters](<../../.gitbook/assets/PiPER Product User Manual image 3>)

</details>

#### 2 Basic Usage <a href="#id-1t8tg" id="id-1t8tg"></a>

This operating reference belongs to the exact arm model named on this page. Secure the base and tool, preserve the matching power/CAN connections and clear the entire reachable workspace before enabling. Record current mode, firmware, joint status, mounting orientation and tool configuration; begin with stationary observation, then one checked small motion. Keep the manufacturer diagrams below with their original model context and apply the current numerical/version corrections in Specifications and Software before using an older GUI illustration.

<details>

<summary>2 Basic Usage — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2 Basic Usage](<../../.gitbook/assets/PiPER Product User Manual image 4>)

</details>

#### 2.1 Electrical Interface Introduction <a href="#id-2.1-electrical-interface-introduction" id="id-2.1-electrical-interface-introduction"></a>

The base external power/CAN harness, Ethernet where fitted and end accessory connector have different functions. The end XT30(2+2) supplies24 V up to 2 A and its CAN is reserved for supported AgileX accessories; it is not a general CAN expansion socket. Follow the illustrated mating viewpoint and keying, not wire color alone. Keep the internal/service CAN unused without manufacturer service instructions and remove power before changing an end tool.

<details>

<summary>2.1 Electrical Interface Introduction — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.1 Electrical Interface Introduction](<../../.gitbook/assets/PiPER Product User Manual image 5>)

![Manufacturer PiPER illustration for 2.1 Electrical Interface Introduction](<../../.gitbook/assets/PiPER Product User Manual image 6>)

![Manufacturer PiPER illustration for 2.1 Electrical Interface Introduction](<../../.gitbook/assets/PiPER Product User Manual image 8>)

![Manufacturer PiPER illustration for 2.1 Electrical Interface Introduction](<../../.gitbook/assets/PiPER Product User Manual image 7>)

</details>

#### 2.2 Robotic Arm Teach/Demonstration Mode Instructions <a href="#id-3rwat" id="id-3rwat"></a>

The end button distinguishes stopped/recording/playback: off means stopped, solid green records and flashing green replays. A single press toggles recording/stop; a double press from stopped replays the recorded path. Playback is motion, not a preview. Starting a new recording replaces the previous one; the manual's recording limit is 3 minutes and its replay indication flashes at about 500 ms intervals. Support and correctly configure the tool before entering teaching, clear the whole recorded path before replay and finish with the indicator off. Return through the documented standby/CAN mode transition before handing ownership back to the GUI/SDK; do not leave two modes issuing commands.

#### 2.2.1The position of the origin <a href="#wui62" id="wui62"></a>

The standard PiPER reference uses the J1 scale and the illustrated J2/J3 supported posture; the J4/J6 axis relationship identifies the wrist reference. The historical illustration lists X=56.128 mm, Y=0, Z=213.266 mm and RX=0°, RY=85°, RZ=0° for its stated reference. These values are a frame/tool-specific documentation reference, not a universal home target. Preserve the factory zero, confirm the exact model/tool frame and support the arm before any calibration; a GUI Return to Zero command is physical motion, whereas redefining zero changes calibration.

<details>

<summary>2.2.1The position of the origin — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.2.1The position of the origin](<../../.gitbook/assets/PiPER Product User Manual image 9>)

</details>

#### 2.2.2 User Coordinate System <a href="#g47fb" id="g47fb"></a>

The illustrated origin belongs to the robot base; user coordinates in this manual refer to that base frame. A gripper TCP, external camera frame and workbench frame are different transforms. Record the selected tool and units with a pose; GUI degrees, SDK radians and millimeter/meter coordinates must be converted explicitly. Re-clamping the base or reversing a tool changes external geometry without changing the mechanical joint reference.

<details>

<summary>2.2.2 User Coordinate System — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.2.2 User Coordinate System](<../../.gitbook/assets/PiPER Product User Manual image 10>)

</details>

#### 2.2.3 Singular Position <a href="#zlasw" id="zlasw"></a>

The manual distinguishes wrist singularity when J4/J6 are coaxial, elbow alignment involving J1/J4, shoulder alignment when the wrist-axis intersection lies on J1, and the fully extended workspace boundary. These are geometric warning cases, not additional reachable poses. Start Cartesian work away from these configurations; check intermediate joint motion and use a verified joint-space retreat when an IK solution becomes poorly conditioned.

<details>

<summary>2.2.3 Singular Position — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.2.3 Singular Position](<../../.gitbook/assets/PiPER Product User Manual image 14>)

![Manufacturer PiPER illustration for 2.2.3 Singular Position](<../../.gitbook/assets/PiPER Product User Manual image 16>)

![Manufacturer PiPER illustration for 2.2.3 Singular Position](<../../.gitbook/assets/PiPER Product User Manual image 15>)

![Manufacturer PiPER illustration for 2.2.3 Singular Position](<../../.gitbook/assets/PiPER Product User Manual image 12>)

![Manufacturer PiPER illustration for 2.2.3 Singular Position](<../../.gitbook/assets/PiPER Product User Manual image 13>)

![Manufacturer PiPER illustration for 2.2.3 Singular Position](<../../.gitbook/assets/PiPER Product User Manual image 11>)

</details>

#### 2.2.4 Zero position <a href="#ylzfz" id="ylzfz"></a>

The standard PiPER reference uses the J1 scale and the illustrated J2/J3 supported posture; the J4/J6 axis relationship identifies the wrist reference. The historical illustration lists X=56.128 mm, Y=0, Z=213.266 mm and RX=0°, RY=85°, RZ=0° for its stated reference. These values are a frame/tool-specific documentation reference, not a universal home target. Preserve the factory zero, confirm the exact model/tool frame and support the arm before any calibration; a GUI Return to Zero command is physical motion, whereas redefining zero changes calibration.

<details>

<summary>2.2.4 Zero position — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.2.4 Zero position](<../../.gitbook/assets/PiPER Product User Manual image 17>)

</details>

#### 2.3 Robotic Arm Workspace and Payload <a href="#ouzzq" id="ouzzq"></a>

The standard arm is nominally1.5 kg with 626.75 mm reach. Keep the manufacturer workspace/load diagram with the intended tool and posture; it does not authorize the rated object at every extension and acceleration. Include gripper/adapter mass and center-of-gravity offset. A changed tool can meet the mass limit yet exceed a moment or clearance condition.

<details>

<summary>2.3 Robotic Arm Workspace and Payload — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.3 Robotic Arm Workspace and Payload](<../../.gitbook/assets/PiPER Product User Manual image 18>)

![Manufacturer PiPER illustration for 2.3 Robotic Arm Workspace and Payload](<../../.gitbook/assets/PiPER Product User Manual image 19>)

</details>

#### 2.4 Mechanical Specifications <a href="#pmb6c" id="pmb6c"></a>

Use the dimensioned view for the identified bare-arm, tool-equipped, base or end-flange assembly. Keep its viewpoint, units and model revision with any fixture design; an axonometric picture is not a scale drawing. Check hole pattern, screw engagement, cable exit and the complete swept volume against the physical parts before machining. The numerical arm limits and actual tool transform remain separate from the drawing envelope.

#### 2.4.1 Base Installation Instructions <a href="#jgv6k" id="jgv6k"></a>

The arm base uses four M5 mounting positions on a 70 × 70 mm pattern. Support the arm while fitting it to a rigid plate and check both hole spacing and thread engagement against the drawing. Neither the notation M5 × 4 nor the base mass establishes screw length, tightening torque or allowable overturning moment. Inspect contact flatness and the underside of the mount before power; a mobile or inverted installation also needs the corresponding controller mounting setting.

<details>

<summary>2.4.1 Base Installation Instructions — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.4.1 Base Installation Instructions](<../../.gitbook/assets/PiPER Product User Manual image 20>)

</details>

#### 2.4.2 End Part Installation Instructions <a href="#bk5vx" id="bk5vx"></a>

For the illustrated PiPER-family flange revision, the locating screw is M3 × 4 with a 4.5 mm head, positioned at the upper-left of the J6 output in the drawing's viewpoint. Align the flange slot, use six M3 × 8 countersunk screws, then the keyed gripper/teaching accessory and its specified M3 × 14 countersunk screws. These sizes belong to that assembly; verify the delivered flange rather than mixing newer tool hardware. Connect its matching power/CAN lead only after mechanical fitting, with power off. Cable slack and the tool's full sweep must remain clear.

<details>

<summary>2.4.2 End Part Installation Instructions — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.4.2 End Part Installation Instructions](<../../.gitbook/assets/PiPER Product User Manual image 23>)

![Manufacturer PiPER illustration for 2.4.2 End Part Installation Instructions](<../../.gitbook/assets/PiPER Product User Manual image 21>)

![Manufacturer PiPER illustration for 2.4.2 End Part Installation Instructions](<../../.gitbook/assets/PiPER Product User Manual image 22>)

</details>

#### 2.5 Desktop Installation Instructions <a href="#ay6ro" id="ay6ro"></a>

The desktop mounting module is optional; the bare-arm packing list does not imply it is supplied. Fit the arm to the matched module before clamping it to a sound, suitable bench, keep all clamp pads seated and preserve access to power/CAN release. Recheck rocking and cable interference after relocation. Changing the fixture location changes the external workcell transform even if joint zeros remain correct; redo the affected camera/workbench calibration.

<details>

<summary>2.5 Desktop Installation Instructions — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.5 Desktop Installation Instructions](<../../.gitbook/assets/PiPER Product User Manual image 24>)

</details>

#### 2.6 Joint zero point description <a href="#id-8iqox" id="id-8iqox"></a>

The standard PiPER reference uses the J1 scale and the illustrated J2/J3 supported posture; the J4/J6 axis relationship identifies the wrist reference. The historical illustration lists X=56.128 mm, Y=0, Z=213.266 mm and RX=0°, RY=85°, RZ=0° for its stated reference. These values are a frame/tool-specific documentation reference, not a universal home target. Preserve the factory zero, confirm the exact model/tool frame and support the arm before any calibration; a GUI Return to Zero command is physical motion, whereas redefining zero changes calibration.

<details>

<summary>2.6 Joint zero point description — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.6 Joint zero point description](<../../.gitbook/assets/PiPER Product User Manual image 25>)

![Manufacturer PiPER illustration for 2.6 Joint zero point description](<../../.gitbook/assets/PiPER Product User Manual image 26>)

</details>

#### 2.7 Instructions for the installation method of the robotic arm <a href="#dtfb0" id="dtfb0"></a>

The mounting setting must describe the physical upright, side or inverted installation so gravity compensation and motion coordinates agree with the arm. Record the previous setting, select the actual orientation in motor/system configuration and confirm it before teaching or actuation. On NERO, the manual defines side mounting relative to the Ethernet-port direction at the reference pose. The arm supporting an orientation does not qualify every clamp or mobile base for it.

<details>

<summary>2.7 Instructions for the installation method of the robotic arm — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.7 Instructions for the installation method of the robotic arm](<../../.gitbook/assets/image (1206).png>)

</details>

#### 2.8 CAN Connection and Preparation <a href="#id-3nm9k" id="id-3nm9k"></a>

Use the external keyed harness and the supplied USB-CAN adapter, matching CAN\_H/yellow and CAN\_L/blue. Align the red marks before seating the base connector and clamp conductors under the terminal tab without loose strands. Select the actual adapter/channel and 1 Mbit/s configuration before connecting the GUI. Preserve factory termination for a single-arm topology; an empty feedback panel calls for adapter, power, mode and receive-counter checks before any enable or firmware update.

<details>

<summary>2.8 CAN Connection and Preparation — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.8 CAN Connection and Preparation](<../../.gitbook/assets/PiPER Product User Manual image 28>)

</details>

#### 2.9 Terminal connection electrical appliance instructions: <a href="#fnsgl" id="fnsgl"></a>

The base external power/CAN harness, Ethernet where fitted and end accessory connector have different functions. The end XT30(2+2) supplies24 V up to 2 A and its CAN is reserved for supported AgileX accessories; it is not a general CAN expansion socket. Follow the illustrated mating viewpoint and keying, not wire color alone. Keep the internal/service CAN unused without manufacturer service instructions and remove power before changing an end tool.

<details>

<summary>2.9 Terminal connection electrical appliance instructions: — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.9 Terminal connection electrical appliance instructions:](<../../.gitbook/assets/PiPER Product User Manual image 29>)

</details>

#### 2.10 Power-on operation instructions: <a href="#vea8z" id="vea8z"></a>

With the arm supported and disabled, assemble CAN and keyed power branches, seat the base connector, power the matched regulated adapter and wait for the documented boot indication before the host connection. Confirm live status/feedback and faults before enabling. NERO uses the newer25 V ceiling; the PiPER-family limits in Specifications remain model-specific. Never substitute a power-cycle or connector removal for a planned controlled stop when gravity can drop the arm.

<details>

<summary>2.10 Power-on operation instructions: — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.10 Power-on operation instructions:](<../../.gitbook/assets/PiPER Product User Manual image 30>)

![Manufacturer PiPER illustration for 2.10 Power-on operation instructions:](<../../.gitbook/assets/PiPER Product User Manual image 31>)

</details>

#### 2.11 Robotic Arm Teach/Demonstration Mode Instructions <a href="#kwsnd" id="kwsnd"></a>

The end button distinguishes stopped/recording/playback: off means stopped, solid green records and flashing green replays. A single press toggles recording/stop; a double press from stopped replays the recorded path. Playback is motion, not a preview. Starting a new recording replaces the previous one; the manual's recording limit is 3 minutes and its replay indication flashes at about 500 ms intervals. Support and correctly configure the tool before entering teaching, clear the whole recorded path before replay and finish with the indicator off. Return through the documented standby/CAN mode transition before handing ownership back to the GUI/SDK; do not leave two modes issuing commands.

<details>

<summary>2.11 Robotic Arm Teach/Demonstration Mode Instructions — manufacturer figures</summary>

![Manufacturer PiPER illustration for 2.11 Robotic Arm Teach/Demonstration Mode Instructions](<../../.gitbook/assets/PiPER Product User Manual image 34>)

![Manufacturer PiPER illustration for 2.11 Robotic Arm Teach/Demonstration Mode Instructions](<../../.gitbook/assets/PiPER Product User Manual image 32>)

![Manufacturer PiPER illustration for 2.11 Robotic Arm Teach/Demonstration Mode Instructions](<../../.gitbook/assets/PiPER Product User Manual image 33>)

</details>

#### 3 Host computer instruction <a href="#id-3-host-computer-instruction" id="id-3-host-computer-instruction"></a>

ArmRobotUA is the PC operator interface for the matching PiPER-family model/firmware. Install the manufacturer release rather than an unrelated robot GUI, connect the actual CAN adapter and record GUI/firmware versions together. The interface combines connection, mode selection, joint/Cartesian control, accessory settings, diagnostics and trajectory management; keep the status/feedback panels visible before enabling. A successful connection is separate from accepted mode, enabled joints and valid live feedback.

#### 3.1 ArmRobotUA <a href="#mddk7" id="mddk7"></a>

ArmRobotUA is the PC operator interface for the matching PiPER-family model/firmware. Install the manufacturer release rather than an unrelated robot GUI, connect the actual CAN adapter and record GUI/firmware versions together. The interface combines connection, mode selection, joint/Cartesian control, accessory settings, diagnostics and trajectory management; keep the status/feedback panels visible before enabling. A successful connection is separate from accepted mode, enabled joints and valid live feedback.

<details>

<summary>3.1 ArmRobotUA — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.1 ArmRobotUA](<../../.gitbook/assets/PiPER Product User Manual image 36>)

![Manufacturer PiPER illustration for 3.1 ArmRobotUA](<../../.gitbook/assets/PiPER Product User Manual image 35>)

</details>

#### 3.2 Robotic Arm communication <a href="#chkrj" id="chkrj"></a>

Use the external keyed harness and the supplied USB-CAN adapter, matching CAN\_H/yellow and CAN\_L/blue. Align the red marks before seating the base connector and clamp conductors under the terminal tab without loose strands. Select the actual adapter/channel and 1 Mbit/s configuration before connecting the GUI. Preserve factory termination for a single-arm topology; an empty feedback panel calls for adapter, power, mode and receive-counter checks before any enable or firmware update.

<details>

<summary>3.2 Robotic Arm communication — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.2 Robotic Arm communication](<../../.gitbook/assets/PiPER Product User Manual image 38>)

![Manufacturer PiPER illustration for 3.2 Robotic Arm communication](<../../.gitbook/assets/PiPER Product User Manual image 37>)

![Manufacturer PiPER illustration for 3.2 Robotic Arm communication](<../../.gitbook/assets/PiPER Product User Manual image 40>)

![Manufacturer PiPER illustration for 3.2 Robotic Arm communication](<../../.gitbook/assets/PiPER Product User Manual image 39>)

</details>

#### 3.3 Vertical menu bar <a href="#tysu2" id="tysu2"></a>

Use the mode/navigation panel to identify which subsystem currently owns control before editing a target. Connection, motion, tool configuration, diagnostics, upgrade and trajectories are separate pages. Preserve the current configuration and read feedback first; changing page, minimizing the window or closing a display is not automatically a physical stop. Confirm the active mode and operator stop action before a test.

<details>

<summary>3.3 Vertical menu bar — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.3 Vertical menu bar](<../../.gitbook/assets/PiPER Product User Manual image 41>)

</details>

#### 3.4 Speed percentage setting <a href="#gzdbq" id="gzdbq"></a>

The global speed percentage scales motion within the controller configuration; it does not redefine joint limits, guarantee braking distance or validate a recorded path. Begin at a low setting for commissioning, apply it only in the mode that accepts the change and verify actual behavior with a small checked movement. A trajectory or leader–follower mode may require returning to Web/GUI control before editing the setting.

<details>

<summary>3.4 Speed percentage setting — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.4 Speed percentage setting](<../../.gitbook/assets/PiPER Product User Manual image 42>)

</details>

#### 3.5 Robotic arm Enable button <a href="#h2dcr" id="h2dcr"></a>

Enable is an actuation-state change after communication succeeds, not a read-only health query. Check all joint states, faults, mounting and tool configuration first, then enable only in a clear supported setup. Disable can remove holding torque; support gravity-loaded links and a held object before using it. If a joint refuses enable, preserve the error and resolve the cause rather than repeatedly clearing it.

#### 3.6 E-stop button <a href="#jbhbc" id="jbhbc"></a>

The GUI stop/pause control is available only while its communication/control path works. Historical releases describe a toggle/re-enable sequence, so identify the exact installed behavior and inspect the queued trajectory/target before resuming; never assume a second click clears every pending action. It is not a safety-rated hardware-stop qualification. Power removal can drop the arm, so the complete installation needs a suitable support/stop arrangement.

#### 3.7 Window zoom and close buttons <a href="#bsucj" id="bsucj"></a>

The window controls change the operator display size, visibility or application state. Minimizing or closing a window is not a substitute for the robot stop/disable procedure. Stop the active behavior, inspect mode/status and support the arm before ending a control session. Restore the view without hiding fault or feedback panels during commissioning; keep the operator stop control accessible.

<details>

<summary>3.7 Window zoom and close buttons — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.7 Window zoom and close buttons](<../../.gitbook/assets/PiPER Product User Manual image 47>)

</details>

#### 3.8 Operation function area <a href="#ixawj" id="ixawj"></a>

Use the mode/navigation panel to identify which subsystem currently owns control before editing a target. Connection, motion, tool configuration, diagnostics, upgrade and trajectories are separate pages. Preserve the current configuration and read feedback first; changing page, minimizing the window or closing a display is not automatically a physical stop. Confirm the active mode and operator stop action before a test.

<details>

<summary>3.8 Operation function area — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.8 Operation function area](<../../.gitbook/assets/PiPER Product User Manual image 48>)

</details>

#### 3.9 Motion control <a href="#jem3c" id="jem3c"></a>

The six GUI joint fields are in degrees and follow J1 at the base through J6 at the wrist. Load reads the current pose into the edit fields; Send commands those fields; Return to Zero sends the factory initial pose and therefore moves the arm. Load before changing one field so stale values in other joints are not sent accidentally. Optional joint light-board controls select a joint and RGB values; lighting hardware is not implied by the bare arm. Keep display feedback separate from target entry.

<details>

<summary>3.9 Motion control — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.9 Motion control](<../../.gitbook/assets/PiPER Product User Manual image 51>)

![Manufacturer PiPER illustration for 3.9 Motion control](<../../.gitbook/assets/PiPER Product User Manual image 50>)

![Manufacturer PiPER illustration for 3.9 Motion control](<../../.gitbook/assets/PiPER Product User Manual image 49>)

</details>

#### 3.10 Linkage control area <a href="#meygh" id="meygh"></a>

Standalone control uses the appropriate follower role; a leader can reject ordinary commands or provide different feedback. For dual-arm work, identify each adapter/model, configure leader/follower roles and the intended joint/coordinate offsets before joining command paths. Start from nearby matched poses and verify signs with a small checked excursion. A role/offset change can immediately affect tracking; do not use it as a passive communication test or leave both arms as competing command sources.

<details>

<summary>3.10 Linkage control area — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.10 Linkage control area](<../../.gitbook/assets/PiPER Product User Manual image 52>)

</details>

#### 3.11 Gripper control area (valid only with grippers) <a href="#vrgl6" id="vrgl6"></a>

For the fitted supported gripper/teaching accessory, configure its enable state, opening/spacing and force/torque controls in the accessory panel, then compare feedback on the status side of the GUI. Do not send arm joint values to a gripper field or assume a force target proves object retention. Use a light compliant target first and inspect opening direction and contact. The tool model, firmware, ID and TCP/payload configuration must match the actual accessory.

<details>

<summary>3.11 Gripper control area (valid only with grippers) — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.11 Gripper control area (valid only with grippers)](<../../.gitbook/assets/PiPER Product User Manual image 53>)

</details>

#### 3.12 oint setting area <a href="#makhy" id="makhy"></a>

Record the existing minimum/maximum angle, speed and acceleration for every joint before editing. The GUI Edit→Save sequence writes settings; narrower workcell limits should remain within the physical model/firmware envelope. An IK failure or blocked path is not solved by widening limits. Verify one deliberate change and preserve a rollback copy; resetting defaults can remove application-specific restrictions.

<details>

<summary>3.12 oint setting area — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.12 oint setting area](<../../.gitbook/assets/PiPER Product User Manual image 54>)

</details>

#### 3.13 Speed setting area <a href="#acstf" id="acstf"></a>

This panel limits endpoint linear/angular velocity and acceleration, separately from global speed percentage and individual joint limits. Record both units and values before editing. A Cartesian path can still require high joint speed near a singularity even when endpoint speed looks small. Initialize/Reset restores factory settings and may remove tuned application limits; do not press it as a harmless view refresh.

<details>

<summary>3.13 Speed setting area — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.13 Speed setting area](<../../.gitbook/assets/PiPER Product User Manual image 55>)

</details>

#### 3.14 Collosion grade <a href="#kq7pl" id="kq7pl"></a>

Collision sensitivity is configured per joint and must be interpreted for the installed firmware. The historical GUI illustrates levels 1–8; newer material also includes0 as disabled. Do not copy a numeric setting across revisions without its definition. Keep sensitivity active as appropriate to the supported application, investigate recurrent triggers and verify tool mass/mount/zero before reducing sensitivity. This feature does not replace collision-free planning or certified personnel protection.

#### 3.15 Motor setting <a href="#yubzl" id="yubzl"></a>

Motor settings expose per-joint enable/disable, zero calibration and fault clearing. These actions have different consequences: disable can remove support, zero changes the joint reference and Clear Error does not remove a physical obstruction or overheating cause. Read/save joint information and faults first, support the arm before torque changes and use the model-specific calibration reference only when maintenance requires it.

<details>

<summary>3.15 Motor setting — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.15 Motor setting](<../../.gitbook/assets/PiPER Product User Manual image 58>)

</details>

#### 3.16 Upgrade <a href="#rhgrp" id="rhgrp"></a>

The historical ArmRobotUA upgrade workflow first checks recognized node information, then loads the matched .bin package, verifies its displayed identity and starts the upgrade while observing progress; the old reference gives roughly2–3 minutes, not a timeout guarantee. Support the arm because update mode can disable holding torque. Newer firmware/GUI releases can require additional zero/calibration procedures; use the exact matching update guide and preserve settings before starting. Re-query firmware and select its SDK profile before resuming, rather than applying an old motor-control example blindly.

<details>

<summary>3.16 Upgrade — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.16 Upgrade](<../../.gitbook/assets/PiPER Product User Manual image 59>)

</details>

#### 3.17 3D simulation model <a href="#id-5cjz8" id="id-5cjz8"></a>

The GUI model displays live reported pose and joint angles alongside the robot visualization. Help describes view controls; View Restore resets the camera view, not the physical arm; Settings changes display/application parameters. Compare visualization with actual supported joint feedback before relying on it. This display is not a collision checker or a dynamics/payload qualification, and it is distinct from the separate URDF/MoveIt/Gazebo environment.

<details>

<summary>3.17 3D simulation model — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.17 3D simulation model](<../../.gitbook/assets/PiPER Product User Manual image 60>)

</details>

#### 3.18 TraceLib <a href="#ahc0h" id="ahc0h"></a>

Create a separately named trajectory, load the current pose and add only checked points. Import loads a saved library; Export preserves it; Delete removes the selected entry. The secondary editor supports adding, deleting and changing individual points. Send/Run can execute once, a finite count or continuously depending on settings, so inspect the loop/count and every intermediate path before replay. Export a backup before edits, start with one short unloaded run and verify stop/resume behavior before considering repetition.

<details>

<summary>3.18 TraceLib — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.18 TraceLib](<../../.gitbook/assets/PiPER Product User Manual image 61>)

![Manufacturer PiPER illustration for 3.18 TraceLib](<../../.gitbook/assets/PiPER Product User Manual image 63>)

![Manufacturer PiPER illustration for 3.18 TraceLib](<../../.gitbook/assets/PiPER Product User Manual image 62>)

</details>

#### 3.19 Robotic arm joint status button <a href="#ovsfh" id="ovsfh"></a>

The joint-information/status view monitors connected joints in real time, while the overall status bar reports arm-level state. Confirm expected joint count, changing timestamps/feedback, temperatures and fault indicators before motion. A colored status button or a frozen3D pose alone is insufficient evidence of healthy communication. Preserve the fault/time/operating pose before clearing an error, and compare requested mode with reported mode when commands appear ignored.

<details>

<summary>3.19 Robotic arm joint status button — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.19 Robotic arm joint status button](<../../.gitbook/assets/PiPER Product User Manual image 66>)

![Manufacturer PiPER illustration for 3.19 Robotic arm joint status button](<../../.gitbook/assets/PiPER Product User Manual image 64>)

</details>

#### 3.20 Robotic arm status <a href="#ccvqo" id="ccvqo"></a>

The joint-information/status view monitors connected joints in real time, while the overall status bar reports arm-level state. Confirm expected joint count, changing timestamps/feedback, temperatures and fault indicators before motion. A colored status button or a frozen3D pose alone is insufficient evidence of healthy communication. Preserve the fault/time/operating pose before clearing an error, and compare requested mode with reported mode when commands appear ignored.

<details>

<summary>3.20 Robotic arm status — manufacturer figures</summary>

![Manufacturer PiPER illustration for 3.20 Robotic arm status](<../../.gitbook/assets/PiPER Product User Manual image 67>)

</details>

#### 4 Secondary Development <a href="#mdj0o" id="mdj0o"></a>

Use the current model/firmware-specific SDK, CAN mapping and ROS description rather than copying another arm profile. The public implementation defines message units, version-dependent encoders/decoders and connection cleanup; raw protocol documents can be gated or older. Query firmware before selecting a profile, preserve the supplied CAN topology and begin with stationary fresh feedback. Keep original direct SDK/protocol/model downloads with the project revision and do not equate a source review with compilation or hardware validation.

#### 5 CAN protocol <a href="#jxp90" id="jxp90"></a>

Use the current model/firmware-specific SDK, CAN mapping and ROS description rather than copying another arm profile. The public implementation defines message units, version-dependent encoders/decoders and connection cleanup; raw protocol documents can be gated or older. Query firmware before selecting a profile, preserve the supplied CAN topology and begin with stationary fresh feedback. Keep original direct SDK/protocol/model downloads with the project revision and do not equate a source review with compilation or hardware validation.

#### 6 Maintenance and Servicing <a href="#f7c6z" id="f7c6z"></a>

Return through a checked path to the supported storage posture, stop the active mode and power down before cleaning or mechanical inspection. Do not reinterpret a storage instruction as routine recalibration of zero. Inspect fasteners, motor/bracket damage, cable jackets and connector retention; clean the exterior with a lightly dampened cloth without flooding openings. Keep the specified−20…50 °C and 25–85 %RH noncondensing environment where applicable, avoid strong magnetic fields and allow hot joints to cool before handling. Log wear or repeated faults before replacing parts.

#### 7 Maintenance Precautions <a href="#gxtjd" id="gxtjd"></a>

Return through a checked path to the supported storage posture, stop the active mode and power down before cleaning or mechanical inspection. Do not reinterpret a storage instruction as routine recalibration of zero. Inspect fasteners, motor/bracket damage, cable jackets and connector retention; clean the exterior with a lightly dampened cloth without flooding openings. Keep the specified−20…50 °C and 25–85 %RH noncondensing environment where applicable, avoid strong magnetic fields and allow hot joints to cool before handling. Log wear or repeated faults before replacing parts.

#### 8 Emergency Handling <a href="#wgpyi" id="wgpyi"></a>

The manual describes power disconnection as an emergency measure and warns that the disabled arm can drop immediately. Plan support and access before actuation; never reach into the sweep merely to unplug a connector. GUI pause/stop depends on a live communication path and can preserve a trajectory for later resumption. Clear the workcell and inspect pending commands before restart. Neither power removal nor a PC toggle is a complete certified injury-prevention system.

#### 9 Dimensional drawings <a href="#bvwrf" id="bvwrf"></a>

Use the dimensioned view for the identified bare-arm, tool-equipped, base or end-flange assembly. Keep its viewpoint, units and model revision with any fixture design; an axonometric picture is not a scale drawing. Check hole pattern, screw engagement, cable exit and the complete swept volume against the physical parts before machining. The numerical arm limits and actual tool transform remain separate from the drawing envelope.

#### 9.1 Zero position <a href="#sqpyj" id="sqpyj"></a>

The standard PiPER reference uses the J1 scale and the illustrated J2/J3 supported posture; the J4/J6 axis relationship identifies the wrist reference. The historical illustration lists X=56.128 mm, Y=0, Z=213.266 mm and RX=0°, RY=85°, RZ=0° for its stated reference. These values are a frame/tool-specific documentation reference, not a universal home target. Preserve the factory zero, confirm the exact model/tool frame and support the arm before any calibration; a GUI Return to Zero command is physical motion, whereas redefining zero changes calibration.

<details>

<summary>9.1 Zero position — manufacturer figures</summary>

![Manufacturer PiPER illustration for 9.1 Zero position](<../../.gitbook/assets/PiPER Product User Manual image 68>)

</details>

#### 9.2 Axonometric drawing of the robotic arm <a href="#mmlvy" id="mmlvy"></a>

Use the dimensioned view for the identified bare-arm, tool-equipped, base or end-flange assembly. Keep its viewpoint, units and model revision with any fixture design; an axonometric picture is not a scale drawing. Check hole pattern, screw engagement, cable exit and the complete swept volume against the physical parts before machining. The numerical arm limits and actual tool transform remain separate from the drawing envelope.

<details>

<summary>9.2 Axonometric drawing of the robotic arm — manufacturer figures</summary>

![Manufacturer PiPER illustration for 9.2 Axonometric drawing of the robotic arm](<../../.gitbook/assets/PiPER Product User Manual image 69>)

</details>

#### 9.3 Robotic arm with leader gripper <a href="#id-3fczs" id="id-3fczs"></a>

The illustrated optional tool is a separate fitted accessory, not part of every bare-arm order. Confirm its exact model, supply, firmware/device identity and mechanical flange before connection. The two-finger gripper and teaching handle have different opening ranges, mass and feedback roles. Include the tool in payload/TCP configuration and verify motion direction with a light test object before using it to retain anything.

<details>

<summary>9.3 Robotic arm with leader gripper — manufacturer figures</summary>

![Manufacturer PiPER illustration for 9.3 Robotic arm with leader gripper](<../../.gitbook/assets/PiPER Product User Manual image 70>)

</details>

#### 9.4 Robotic arm with follower gripper <a href="#nssju" id="nssju"></a>

The illustrated optional tool is a separate fitted accessory, not part of every bare-arm order. Confirm its exact model, supply, firmware/device identity and mechanical flange before connection. The two-finger gripper and teaching handle have different opening ranges, mass and feedback roles. Include the tool in payload/TCP configuration and verify motion direction with a light test object before using it to retain anything.

<details>

<summary>9.4 Robotic arm with follower gripper — manufacturer figures</summary>

![Manufacturer PiPER illustration for 9.4 Robotic arm with follower gripper](<../../.gitbook/assets/PiPER Product User Manual image 71>)

</details>

#### 9.5 Base <a href="#bnyxd" id="bnyxd"></a>

Use the dimensioned view for the identified bare-arm, tool-equipped, base or end-flange assembly. Keep its viewpoint, units and model revision with any fixture design; an axonometric picture is not a scale drawing. Check hole pattern, screw engagement, cable exit and the complete swept volume against the physical parts before machining. The numerical arm limits and actual tool transform remain separate from the drawing envelope.

#### 9.6 End of the arm <a href="#bf5qo" id="bf5qo"></a>

Use the dimensioned view for the identified bare-arm, tool-equipped, base or end-flange assembly. Keep its viewpoint, units and model revision with any fixture design; an axonometric picture is not a scale drawing. Check hole pattern, screw engagement, cable exit and the complete swept volume against the physical parts before machining. The numerical arm limits and actual tool transform remain separate from the drawing envelope.

<details>

<summary>9.6 End of the arm — manufacturer figures</summary>

![Manufacturer PiPER illustration for 9.6 End of the arm](<../../.gitbook/assets/PiPER Product User Manual image 73>)

</details>

#### Development Resources <a href="#development-resources" id="development-resources"></a>

Use the current model/firmware-specific SDK, CAN mapping and ROS description rather than copying another arm profile. The public implementation defines message units, version-dependent encoders/decoders and connection cleanup; raw protocol documents can be gated or older. Query firmware before selecting a profile, preserve the supplied CAN topology and begin with stationary fresh feedback. Keep original direct SDK/protocol/model downloads with the project revision and do not equate a source review with compilation or hardware validation.

#### Additional model resources

The following direct resources retain the manufacturer/model context of the detailed manual. Select the package matching the installed hardware and firmware; a historical download is not an update recommendation.

* [https://www.dropbox.com/scl/fi/78e4ch20ok9n040onay0y/ArmRobotUA\_V1.5.2.260310\_release.exe?rlkey=q4q1xr9f7k1gc5j0vtl803m5f\&st=kw1yaszi\&dl=0](https://www.dropbox.com/scl/fi/78e4ch20ok9n040onay0y/ArmRobotUA_V1.5.2.260310_release.exe?rlkey=q4q1xr9f7k1gc5j0vtl803m5f\&st=kw1yaszi\&dl=0)
* [AgileX arm ROS 2 driver](https://github.com/agilexrobotics/agx_arm_ros/tree/ros2)
* [PiPER-series firmware compatibility reference](https://github.com/agilexrobotics/pyAgxArm/blob/master/docs/piper/firmware_reference.md)

## References and validation

Reviewed24 November2026: official manual/resource pages, downloaded manufacturer PDF, current SDK/API implementation and firmware matrix, and ROS 2 launch source at the commits above. The original feedback sampler was syntax-checked. **SDK installation, CAN connection, ROS builds, firmware updates, motion and hardware measurements were not run.**

Related exact-model guides: [PiPER-H](piper-h-user-manual.md), [NERO](nero-user-manual.md), [desktop fixture](piper-desktop-fixture.md). Source manuals remain the authority for the received hardware's assembly and service procedures; this engineering workflow adds staged diagnostics and explicit software/version boundaries.
