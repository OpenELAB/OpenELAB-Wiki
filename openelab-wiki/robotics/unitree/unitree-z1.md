---
description: >-
  Compare Unitree Z1 AIR and PRO, audit six-axis models, distinguish Ethernet
  SDK, ROS and DDS routes, and understand mounting, power and control limits.
---

# Unitree Z1 AIR and PRO: Ethernet SDK and ROS Development Guide

{% hint style="info" %}
**Unitree Z1 AIR / Z1 PRO — unlisted manufacturer reference.** No exact OpenELAB product URL or SKU was found in the reviewed 67-product Unitree catalog. This guide covers the two manufacturer editions; confirm the arm label, controller revision and gripper option before procurement or commissioning. [Manufacturer product page](https://www.unitree.com/z1/).
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

The Unitree Z1 is a six-axis manipulator with Ethernet connectivity, intended for desktop manipulation and integration with mobile robots. AIR and PRO share the published 740 mm reach but have different mass and payload figures. A gripper is an end-effector option, not a seventh arm joint. This guide explains how to select the appropriate control stack and audit a model without powering an arm. [Z1 specifications](https://www.unitree.com/z1/)

There are two distinct development paths. The standalone `z1_sdk` works with the standalone `z1_controller`. The ROS repository contains its own controller and SDK packages; its README explicitly says the standalone SDK is incompatible with that bundled controller. Treat a repository pair, its configuration and the arm firmware as one integration record. [ROS compatibility warning](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/README.md)

## Applications <a href="#applications" id="applications"></a>

The documented applications include mobile manipulation, logistics research and everyday object handling. The product page illustrates cooperation with AlienGo and B1. This establishes an intended integration use, not a universal bracket, harness, battery or balance approval for every Unitree base. Include tool mass and center of gravity when assessing payload. [Manufacturer applications and limitations](https://www.unitree.com/z1/)

For development, a useful progression is model inspection, controller/firmware identification, supervised state acquisition, and only then a separately approved manipulation experiment. Force feedback and collision detection are published capabilities; they do not establish a safety-rated collaborative operating mode. The supplied controller configuration actually disables collision detection by default. [Standalone configuration](https://github.com/unitreerobotics/z1_controller/blob/639bb773bd11b0e8495faf40eadc9e8eb8bc8400/config/config.xml)

## Specifications <a href="#specifications" id="specifications"></a>

The following values are from the current [manufacturer Z1 page](https://www.unitree.com/z1/), reviewed 24 November 2026. Its repeatability and performance footnotes require application-specific testing.

| Parameter              | Z1 AIR                                       | Z1 PRO                                            |
| ---------------------- | -------------------------------------------- | ------------------------------------------------- |
| Arm degrees of freedom | 6                                            | 6                                                 |
| Mass                   | 4.3 kg                                       | 4.5 kg                                            |
| Payload                | 2 kg                                         | ≥3 kg, published without a complete load envelope |
| Reach                  | 740 mm                                       | 740 mm                                            |
| Repeatability          | Approximately 0.1 mm, test conditions matter | Approximately 0.1 mm, test conditions matter      |
| Supply                 | 24 V; current >20 A                          | 24 V; current >20 A                               |
| Maximum power          | 500 W                                        | 500 W                                             |
| Host / interface       | Ubuntu / Ethernet                            | Ubuntu / Ethernet                                 |
| Control                | Position and force                           | Position and force                                |

| Joint | Product-page angular range | Published maximum speed |
| ----- | -------------------------- | ----------------------- |
| J1    | −150° to +150°             | 180°/s                  |
| J2    | 0° to 180°                 | 180°/s                  |
| J3    | −165° to 0°                | 180°/s                  |
| J4    | −80° to +80°               | 180°/s                  |
| J5    | −85° to +85°               | 180°/s                  |
| J6    | −160° to +160°             | 180°/s                  |

These are selection parameters, not a validated command envelope. In the reviewed ROS URDF, J2 instead ends at 170°, J4 is ±87°, and J5 is ±77°. Do not overwrite model limits with a marketing table or expand either set until Unitree confirms the exact hardware/model pairing. [Reviewed URDF](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/z1_controller/config/z1.urdf)

The product page also contains a **joint-module** table: RS485, maximum 33 N·m, 15-bit encoder, approximately 0.2 N·m force-control accuracy, approximately 6 arcmin backlash, 405 g, Φ65 × 52 mm, 1 kHz, harmonic reducer with 60+ ratio, and recommended 24 V. It lists torque/angle/angular-velocity feedback and stiffness/damping commands. These module values must not be substituted for whole-arm Ethernet protocol, per-joint continuous torque or SDK loop timing. The standalone SDK declares a 0.002 s default interval, a separate 500 Hz software exchange loop. [Product module table](https://www.unitree.com/z1/), [SDK timing](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/include/unitree_arm_sdk/control/ctrlComponents.h)

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

Secure the base to a structure that carries both arm weight and dynamic reaction loads; account for the entire swept volume and tool. An older Unitree-branded manual hosted by Generation Robots shows four M6 mounting bolts, base-hole geometry, the workspace, end flange, joint numbering and a PC/power-adapter connection diagram. Use the actual drawings to identify the relevant features, then obtain a current revision before machining a fixture. [Manual pp. 4–7](https://static.generation-robots.com/media/user-manual-z1-unitree-robotics.pdf#page=4)

| Drawing                                                                                              | What it helps identify                           | Limit                                                                             |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------ | --------------------------------------------------------------------------------- |
| [Manual p. 4](https://static.generation-robots.com/media/user-manual-z1-unitree-robotics.pdf#page=4) | Link geometry and swept workspace                | Historical geometry; current page specifies 740 mm reach, manual specifies 730 mm |
| [Manual p. 5](https://static.generation-robots.com/media/user-manual-z1-unitree-robotics.pdf#page=5) | Four-bolt base mounting                          | Does not supply verified current tightening torque                                |
| [Manual p. 6](https://static.generation-robots.com/media/user-manual-z1-unitree-robotics.pdf#page=6) | Power adapter, main/auxiliary ports and J1–J6    | Diagram identifies roles, not connector pin polarity                              |
| [Manual p. 7](https://static.generation-robots.com/media/user-manual-z1-unitree-robotics.pdf#page=7) | End flange and historical zero-reference posture | Confirm current calibration procedure before applying it                          |

The manual cautions against wet or dusty use, hot surfaces, unsecured mounting and people in the working envelope. It identifies exposed end-motor black/white power wiring as 24 V and requires unused conductors to be insulated. Do not infer polarity from wire colors. Use the supplied, revision-matched harness and approved 24 V supply; no verified current connector pinout or electrical emergency-stop circuit was obtained. [Manual pp. 2, 5–7](https://static.generation-robots.com/media/user-manual-z1-unitree-robotics.pdf#page=2)

For identification, Unitree publishes this [gripper illustration](https://oss-global-cdn.unitree.com/static/04e1a2bf8613432d9cad774da006cd85_564x400.png). It depicts the end effector, not the complete arm or the package contents. Image © Unitree Robotics; linked from its Z1 page.

### Portal specifications, mounting and power preparation <a href="#portal-specifications-mounting-and-power-preparation" id="portal-specifications-mounting-and-power-preparation"></a>

The generic portal table gives **4.1 kg**, ≥3 kg and740 mm without an AIR/PRO edition selector. Preserve that scope alongside the current variant table and historical PDF, rather than replacing one with another. The joint-coordinate article defines J1–J6 positive/negative rotation and gives geometry vectors, but its J3 vector and flange-origin string (`[0,049, 0, 0.1605]`) contain malformed punctuation. The gripper-center string is `[0.0872, 0, 0.1605]`, without a consistent nearby unit/frame declaration. Do not silently repair those strings into a calibrated transform. Use the matched SDK/URDF and confirm the actual tool frame. [Technical parameters](https://support.unitree.com/home/en/Z1_developer/param)

The portal packing list names one Z1, one DC24 V adapter, one fixing plate, two G-clamps, a2 m network cable, four M6×16 and two M2.5×8 screws, plus2 mm and5 mm hex keys. Verify the actual order and end-effector option. The mounting platform must withstand dynamic reactions as well as arm weight. The main network port controls the robot; the auxiliary port changes device IP. Power is **not hot-swappable**. [Installation](https://support.unitree.com/home/en/Z1_developer/install)

| Official figure                                                                                                        | Purpose                                                          |
| ---------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| [Base attachment](https://oss-global-cdn.unitree.com/static/f0ed6f292ca24dff9c15955628772bc2.JPG)                      | Revision-specific base geometry                                  |
| [Desktop fixing plate/clamps](https://oss-global-cdn.unitree.com/static/3713d551c0744bdc822b60c3e61c70e7.JPG)          | Alternative desktop mounting                                     |
| [Current connection diagram](https://oss-global-cdn.unitree.com/static/1c45c432002348c0b1087a573fe9c2d4_3508x2481.jpg) | Main/auxiliary Ethernet and separate power adapter; not a pinout |
| [Joint directions](https://oss-global-cdn.unitree.com/static/f91e1ab0aa7a4808b8d07cf9773d2798_2481x4554.png)           | J1–J6 orientation and sign reference                             |
| [Flange](https://oss-global-cdn.unitree.com/static/b6692a75a8d8436db5c6ac64c2eddec0_840x385.png)                       | End-plane attachment reference                                   |
| [Zero-reference posture](https://oss-global-cdn.unitree.com/static/00cf031d4e43437f86ff8e6bb9cc120a.JPG)               | Manufacturer power-on posture; align J1/J6 marks                 |
| [Singular-pose illustration](https://oss-global-cdn.unitree.com/static/5ce8b91a6dcf4930aab335b158723590.JPG)           | Region to avoid before Cartesian operation                       |

Figures © Unitree Robotics, from the [parameter](https://support.unitree.com/home/en/Z1_developer/param), [installation](https://support.unitree.com/home/en/Z1_developer/install) and [power-preparation](https://support.unitree.com/home/en/Z1_developer/poweron) articles. Source links are retained rather than reproducing a complete diagram collection.

The power-preparation article requires **`z1_ctrl` stopped before energizing** and the defined mechanical zero pose, with J1/J6 marks aligned. It gives one version-specific exception: if version inspection reports **“Arm Version 3-8”**, power-on in another posture is permitted, followed by the prescribed back-to-start operation. That operation moves the arm; it is not a status query or arbitrary-zero calibration. Do not apply the exception to unidentified hardware/firmware. Steady green and one blue flash are the documented power/self-check indications. Insulate unused end-motor24 V conductors; do not infer polarity from black/white color alone. [Power preparation](https://support.unitree.com/home/en/Z1_developer/poweron)

The portal recommends the saved forward pose before Cartesian work to avoid singularity. It also requires qualified commissioning, a clear work envelope, avoidance of wet/dusty conditions and hot surfaces, and an arm-power-off then control-program-off shutdown order. Establish supported posture and an independent physical stopping method before using these stages. [Cautions](https://support.unitree.com/home/en/Z1_developer/z1)

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

| Stack                                                                                                                             | Reviewed revision                          | Integration consequence                                                                                     |
| --------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ | ----------------------------------------------------------------------------------------------------------- |
| [Standalone Z1 SDK](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/README.md)            | `f1af2b42f2a39a5010946e049ad3fe324e2e6f06` | C++14 / pthread CMake project linking an architecture-specific `Z1_SDK` library; optional pybind11 bindings |
| [Standalone controller](https://github.com/unitreerobotics/z1_controller/blob/639bb773bd11b0e8495faf40eadc9e8eb8bc8400/README.md) | `639bb773bd11b0e8495faf40eadc9e8eb8bc8400` | Controller configuration and finite-state interfaces; match firmware with Unitree                           |
| [Z1 ROS integration](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/README.md)           | `d3bafd38fb48e805096da7abb0c19a15b636975d` | ROS 1 Noetic/catkin instructions; bundled SDK/controller form a separate stack                              |

The standalone SDK exposes high-level joint and Cartesian movement, low-level commands, model computations and low-level state. `LowlevelState` provides joint angles, velocities, accelerations, estimated torques, temperature, connection indicators and fault bits. The state header describes `0x01` overcurrent, `0x02` phase leakage, `0x04` winding overtemperature and `0x20` parameter jump; interpret these against the matching firmware, rather than clearing faults blindly. `isMotorConnected` values 1 and 2 record a disconnect or CRC event respectively and are not a simple Boolean healthy flag. [State definitions](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/include/unitree_arm_sdk/message/LowlevelState.h)

**Starting the SDK communication loop is an active operation.** `sendRecv()` sends the current command and receives state; it is not a passive status subscriber. The high-level example calls return-to-start and moves the arm; the low-level example drives joint commands. Neither is a suitable first state-only check. [Exchange contract](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/include/unitree_arm_sdk/control/ctrlComponents.h), [high-level example](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/examples/highcmd_basic.cpp), [low-level example](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/examples/lowcmd_development.cpp)

The standalone controller's checked configuration contains IP `192.168.123.110`, port `8881`, collision `open=N`, threshold `10.0` N·m and load `0.0` kg. The ROS stack has its own `mcu_ip`, `port_to_mcu=8881`, `port_to_sdk=8871`, `collision/open=false` and `cmdCache=false`. These are repository defaults, not observed settings of a delivered robot. Command caching changes what happens after missed SDK messages; collision checking depends on configuration and a correct load model. [Standalone XML](https://github.com/unitreerobotics/z1_controller/blob/639bb773bd11b0e8495faf40eadc9e8eb8bc8400/config/config.xml), [ROS parameters](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/doc/controller.md), [ROS YAML](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/z1_controller/config/config.yaml)

ROS setup requests GCC 7 or newer, Boost, Eigen, urdfdom, MoveIt and Pinocchio **v2.7.0**, with an explicit incompatibility warning for Pinocchio 3.0.0 onward. Its real-arm and Gazebo launch paths are separate. Do not mix this dependency recipe with a newer unrelated robot SDK. The SDK and ROS source LICENSE files are BSD 3-Clause; check separately supplied libraries and model assets before redistribution. [ROS setup](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/doc/setup.md), [ROS usage](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/doc/usage.md), [SDK license](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/LICENSE), [ROS license](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/LICENSE)

### Portal SDK routes and version boundaries <a href="#portal-sdk-routes-and-version-boundaries" id="portal-sdk-routes-and-version-boundaries"></a>

The portal identifies `z1_controller`, `z1_sdk` and the older `unitree_ros` simulation route. Its environment article describes Linux x86 above Ubuntu18.04 with Boost/Eigen, mentions Noetic simulation but links a Melodic tutorial. This historical mixture is not one validated ROS environment. The separate `z1_ros` repository has its own Noetic/Pinocchio recipe and warns against mixing its bundled controller with standalone SDK. [Environment](https://support.unitree.com/home/en/Z1_developer/env), [SDK introduction](https://support.unitree.com/home/en/Z1_developer/sdk_intro)

The controller executable has version inspection (`z1_ctrl -v`), default SDK control and keyboard control with `k`; `sim_ctrl` uses simulation I/O. `unitreeArmTools.py` changes the lower-controller IP through the auxiliary port and requires restart. Configuration is read once at startup. The portal distinguishes robot UDP port **8880** from PC-bound port **8881**. Collision `limitT` compares estimated and feedback torque; end `load` affects feedforward regardless of whether collision checking is enabled. Labels are stored in `savedArmStates.csv`. [SDK introduction](https://support.unitree.com/home/en/Z1_developer/sdk_intro)

The pinned standalone `main.cpp` sets a1/250 s controller interval and uses SDK localhost8072/8071 with a0.002 s command-panel interval. These are distinct from the500 Hz SDK exchange loop and historical300/100 Hz main/auxiliary hardware-port statements. None is a measured rate of a delivered arm. [Controller implementation](https://github.com/unitreerobotics/z1_controller/blob/639bb773bd11b0e8495faf40eadc9e8eb8bc8400/main.cpp)

The SDK model object exposes forward/inverse kinematics, inverse dynamics and spatial Jacobian calculations. High-level examples cover FSM calls (`MoveJ`, `MoveL`, `MoveC`, `backToStart`), directional joint-speed commands and Cartesian twists. Planned high-level trajectories continually update joint `q/qd/gripperQ/gripperW` or Cartesian `twist` while `sendRecv()` sends commands and receives state. Low-level control supplies joint position/velocity, feedforward torque and PD gains. Do not treat a source example or a model calculation as proof of a safe live trajectory. [SDK introduction](https://support.unitree.com/home/en/Z1_developer/sdk_intro)

Gain conventions depend on the stack: the historical portal low-level expression is `25.6*kp*(q_des-q) + 0.0128*kd*(dq_des-dq) + tau_ff`; the ROS controller notes those multipliers were removed. The newly documented SDK2 bridge also uses **unscaled** `kp*(q_des-q)+kd*(dq_des-dq)+tau_ff`. Preserve release/route with the gains rather than multiplying or dividing all Z1 commands by one global constant. [Portal low-level section](https://support.unitree.com/home/en/Z1_developer/sdk_intro), [ROS change](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/doc/controller.md)

The portal SDK2 route uses architecture-specific **`z1_udp_service`** in the controller deploy package. Its example selects namespace `z1`, device192.168.123.110 and localport8881. The portal spells its message types `unitree_go::msg::dds::MotorStates_` / `MotorCmds_`, associated with **`rt/z1/lowstate`** / **`rt/z1/lowcmd`**. That is the portal spelling, not a compilable type declaration at the SDK2 pin reviewed here. **SDK2 commit `b7fec6020eb93d4c059a6edf19905e12a75a8d3d` declares `unitree_go::msg::dds_::MotorStates_` and `unitree_go::msg::dds_::MotorCmds_`**, with a trailing underscore in `dds_`; see the [generated state header](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/MotorStates_.hpp) and [generated command header](https://github.com/unitreerobotics/unitree_sdk2/blob/b7fec6020eb93d4c059a6edf19905e12a75a8d3d/include/unitree/idl/go2/MotorCmds_.hpp). Neither the portal type spelling nor this header comparison verifies compatibility between a deployed Z1 bridge binary, that SDK2 release and installed arm firmware. Starting the service establishes a control bridge; a later state subscriber does not make startup passive. Record the deployed service/firmware pair before adopting this route. This bridge is a model-specific documented option, not evidence that arbitrary SDK2 examples support Z1. [SDK2 bridge details](https://support.unitree.com/home/en/Z1_developer/sdk_intro)

Python bindings come from `arm_python_interface.cpp`; the portal mentions a precompiled Python3.8/x86\_64 `.so`, not a universal Python binary. The `.pyi` adds editor hints without altering runtime behavior. Its Python high-level example moves the arm, and the FastAPI example exposes external control and needs deliberate network/ownership management. [Python interface](https://support.unitree.com/home/en/Z1_developer/sdk_intro)

The changelog lists2.2.5 aarch64 support;2.2.0 Cartesian spatial twists, simplified joint/Cartesian calls, `setWait()` and IP tooling. The2022 entries describe lower-controller-dependent error feedback, gripper detection by motor count, collision/load configuration, RBDL removal, trajectory/teach refinements and reduced singular-region speed. An older non-gripper FAQ recommends a `gripper` XML field, but21 October2022 explicitly removed that field. Do not add it to current configurations or use it instead of confirming the actual dynamics model. Article/change labels are not installed firmware versions. [Changelog](https://support.unitree.com/home/en/Z1_developer/changelog), [FAQ](https://support.unitree.com/home/en/Z1_developer/abnormalities)

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: inspect the six-axis model offline <a href="#first-result-inspect-the-six-axis-model-offline" id="first-result-inspect-the-six-axis-model-offline"></a>

1. Obtain only the [pinned `z1.urdf`](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/z1_controller/config/z1.urdf) as a text file and retain its source revision. Keep hardware disconnected.
2. Save the following original Python program as `inspect_urdf.py`. It uses the standard library and parses XML; it does not import ROS, open a socket or run vendor software.
3. Run `python3 inspect_urdf.py /absolute/path/z1.urdf` with the actual file path.

```python
"""Original offline Z1 model audit. Parse XML only; no ROS or vendor imports."""
import json
import math
import sys
import xml.etree.ElementTree as ET


def inspect(path):
    rows = []
    for joint in ET.parse(path).getroot().findall("joint"):
        if joint.get("type") == "fixed":
            continue
        if joint.get("type") != "revolute" or joint.find("limit") is None:
            raise ValueError("unexpected joint type or missing limit")
        limit = joint.find("limit")
        lo, hi = float(limit.get("lower")), float(limit.get("upper"))
        if not all(math.isfinite(v) for v in (lo, hi)) or lo >= hi:
            raise ValueError("invalid joint limits")
        rows.append({"name": joint.get("name"), "lower_deg": round(math.degrees(lo), 1),
                     "upper_deg": round(math.degrees(hi), 1)})
    if [r["name"] for r in rows] != [f"joint{i}" for i in range(1, 7)]:
        raise ValueError("expected the six joints of the reviewed Z1 URDF")
    return rows


if __name__ == "__main__":
    print(json.dumps(inspect(sys.argv[1]), indent=2))
```

Expected checkpoint: six rows named `joint1` through `joint6`; J2 reports 0.0–170.0°, J4 −87.0–87.0°, and J5 −77.0–77.0°. A missing joint, malformed limit or different model stops the audit. This validates the inspected file's structure and exposes model/product differences; it does not certify calibration or a hardware-safe range.

### Before connecting a real arm <a href="#before-connecting-a-real-arm" id="before-connecting-a-real-arm"></a>

Record AIR/PRO, serial number, controller and firmware versions, standalone versus ROS stack, end effector, base orientation, supply/harness revision, tool mass and center of gravity. Verify the current pinout, zero-reference procedure and independent stopping method with Unitree. Establish exclusive controller ownership and a supported arm posture before any command/receive loop is started or stopped. A software passive/stop state may release holding torque and is not proof of power isolation. Live connection remains blocked in this reference until those commissioning facts are confirmed.

### Documented connection and control progression <a href="#documented-connection-and-control-progression" id="documented-connection-and-control-progression"></a>

The portal's host example is192.168.123.162/24 with arm192.168.123.110. Identify the actual isolated host interface and current device address before changing host settings. The article offers UI, temporary `ifconfig` and persistent interface-file methods; Linux network-manager choice affects which applies. A successful ping proves reachability, not correct firmware, calibration or safe control. Device-IP changes use the auxiliary port/tool, restart and matching controller XML. [Network preparation](https://support.unitree.com/home/en/Z1_developer/poweron)

The real-control order is prepared/mounted arm → verified power/network → matching controller → matching SDK client. The controller may print receive-timeout warnings while waiting for its SDK; that alone is not a full hardware diagnosis. The older simulation sequence uses `unitree_ros` plus `unitree_legged_msgs`, Gazebo `unitree_gazebo z1.launch`, `sim_ctrl`, then the SDK example. The separate `z1_ros` launch recipes belong to a different stack. These are documented stages, not builds/launches performed here. [SDK operation](https://support.unitree.com/home/en/Z1_developer/sdk_operation)

For two standalone arms, the portal gives separate controllers and distinct addresses/ports: second arm192.168.123.111, PC-bound8882 and localhost SDK8074/8073 instead of8072/8071. The `lowcmd_multirobots` example actually moves both J1 joints. Use it as an address/ownership design reference, not first-state discovery; keep each arm's labels, calibration and tool model separate. [Multiple-arm section](https://support.unitree.com/home/en/Z1_developer/sdk_operation)

### Keyboard state, teaching and labels <a href="#keyboard-state-teaching-and-labels" id="keyboard-state-teaching-and-labels"></a>

Keyboard mode is active control. Entering a state, confirming a pose or replaying a label can move the mechanism. [Keyboard article](https://support.unitree.com/home/en/Z1_developer/keyboard)

| Key | State / effect                              | Allowed destination states in the source                                         |
| --- | ------------------------------------------- | -------------------------------------------------------------------------------- |
| `~` | BACKTOSTART: move to initial position       | Passive, joint control                                                           |
| `1` | PASSIVE: no active pose control             | Start, joint, Cartesian, calibration                                             |
| `2` | JOINTCTRL: joint-space speed                | Start, passive, Cartesian, MoveJ/L/C, teach, repeat, save, label-run, trajectory |
| `3` | CARTESIAN: end spatial speed                | Start, passive, joint, MoveJ/L/C, save                                           |
| `4` | MoveJ                                       | Start, passive, joint, Cartesian, MoveL/C, save                                  |
| `5` | MoveL                                       | Start, passive, joint, Cartesian, MoveJ/C, save                                  |
| `6` | MoveC                                       | Start, passive, joint, Cartesian, MoveJ/L, save                                  |
| `7` | TEACH: record a dragged trajectory          | Start, passive, joint                                                            |
| `8` | TEACHREPEAT: execute named trajectory       | Automatically returns to joint                                                   |
| `9` | SAVESTATE: record named joint pose          | Automatically returns to joint                                                   |
| `0` | TOSTATE: move to named joint pose           | Automatically returns to joint                                                   |
| `=` | CALIBRATION: make present pose initial zero | Automatically returns to passive                                                 |

Joint jog pairs are Q/A, W/S, the J3 E/D pair, R/F, T/G and Y/H, with arrows for gripper. **The portal's joint table reverses J3 positive ordering (D/E) relative to the pinned controller (E/D)**; confirm the selected implementation before any directional check. Cartesian pairs correspond to forward/back, right/left, up/down, roll, pitch and yaw. Joint coordinates use a right-hand convention; the figures and actual model must establish sign. [Keyboard article](https://support.unitree.com/home/en/Z1_developer/keyboard), [implementation](https://github.com/unitreerobotics/z1_controller/blob/639bb773bd11b0e8495faf40eadc9e8eb8bc8400/main.cpp)

Move primitives take `[roll,pitch,yaw,x,y,z]`; MoveC needs an intermediate and a final pose. The keyboard interface allows queued poses: a second Enter commits execution, so it is not a harmless confirmation keystroke. The article recommends the saved `forward` pose before Cartesian motion. TEACH starts from joint control, records into a named CSV until returning to joint control, and TEACHREPEAT performs that movement. SAVESTATE records a label in `savedArmStates.csv`; TOSTATE/`labelRun()` moves to it. CALIBRATION changes the reference and must only be applied in the confirmed physical zero pose. [Trajectory and label operations](https://support.unitree.com/home/en/Z1_developer/keyboard)

### Shared B1/Z1 joystick workflow <a href="#shared-b1z1-joystick-workflow" id="shared-b1z1-joystick-workflow"></a>

The joystick article is specific to a **B1 carrying Z1**, not a general Go2/R1 remote map. It requires B1 stopped before arm control. Its main workflow uses L1+L2 to select arm control, R2 joint mode, R1 Cartesian mode, L2+R2 to retain arm pose while suppressing joystick arm input, SELECT to return to origin and R2+X to trigger a preset trajectory from joint mode. Returning to B1 control can leave Z1 actively holding; base and arm ownership are separate. The [joint figure](https://oss-global-cdn.unitree.com/static/81e09b739ee141be85f47fecce6cc961_851x332.png) and [Cartesian figure](https://oss-global-cdn.unitree.com/static/74a5374b035248ef9d753e4e48e33c67_1053x333.png) remain attributed manufacturer references. [Joystick article](https://support.unitree.com/home/en/Z1_developer/joystick)

Passive-state mappings conflict inside the article: its caution says R1+R2, whereas the19 October2022 update says L1+L2 replaced that mapping; a5 January2022 entry describes another prior mapping. Passive can remove support, so confirm the delivered B1/Z1 release before using such shortcuts. Do not test passive by inserting a hand into the powered workspace. The historical speed-adjustment and SELECT/preset changes explain why a single universal joystick recipe is inappropriate. [Joystick history](https://support.unitree.com/home/en/Z1_developer/joystick)

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**SDK exchanges no state.** First check that the controller and SDK belong to the same stack. Compare the delivered configuration with the correct repository's network settings, physical Ethernet port and host interface; confirm no second controller is active. Do not change IP addresses or launch real-arm examples merely to discover a device. [Stack warning](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/README.md)

**The arm shakes or tracks poorly.** The manufacturer warns that low reduction and limited position stiffness can produce error and oscillation without appropriate control. Stop the experiment using the agreed procedure, keep clear of the load and review payload, gains, model, zero reference and command continuity. Increasing gains or disabling limits is not an established recovery. [Performance footnotes](https://www.unitree.com/z1/)

**Collision protection did not stop an operation.** Both reviewed controller configurations default it off. Published collision capability is not evidence of an enabled or safety-rated installation. Resolve configuration and load-model requirements before use; avoid testing by intentional impact. [Configuration](https://github.com/unitreerobotics/z1_controller/blob/639bb773bd11b0e8495faf40eadc9e8eb8bc8400/config/config.xml)

**Why do manual and web numbers disagree?** The undated distributor-hosted manual reports 730 mm, a generic 4.5 kg and PRO 3–5 kg; the current product table reports 740 mm, AIR/PRO 4.3/4.5 kg and PRO ≥3 kg. Its 300/100 Hz main/auxiliary port rates are also distinct from the SDK's 500 Hz exchange interval. No current arm/firmware compatibility matrix was verified. Keep each number attached to its source; request the current manual for the unit.

**Can calibration or “back to start” repair communication?** No. These are state-changing operations. The SDK describes calibration as setting the present pose as a zero reference and back-to-start as arm movement. Preserve calibration records, resolve communications first and use the manufacturer's supervised recovery for the identified revision. [Arm control API](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/include/unitree_arm_sdk/control/unitreeArm.h)

### Portal fault clues and bounded recovery <a href="#portal-fault-clues-and-bounded-recovery" id="portal-fault-clues-and-bounded-recovery"></a>

The portal FAQ associates flashing red with joint-communication abnormality, and heavy payload/long holding with overtemperature protection. It says changing the controlling PC requires an arm power cycle because communication binds after power-on. Support the mechanism and use the approved shutdown/startup sequence; changing hosts is not permission to hot-unplug power. [FAQ](https://support.unitree.com/home/en/Z1_developer/abnormalities)

A J3 jump in drag teaching may indicate a software-limit crossing or a mismatched gripper dynamics model. Stop safely, check model/end-effector, calibration, actual angle and limits. The old FAQ's `gripper` XML remedy is superseded by the changelog removing that item and using motor-count detection; do not blindly restore the obsolete setting. Preserve logs and contact Unitree for persistent thermal/communication/model faults. [FAQ](https://support.unitree.com/home/en/Z1_developer/abnormalities), [changelog](https://support.unitree.com/home/en/Z1_developer/changelog)

The thirteen portal records comprise eleven functional articles plus [Introduction](https://support.unitree.com/home/en/Z1_developer/intro)/[How-to-use](https://support.unitree.com/home/en/Z1_developer/use) directory placeholders. Actual article bodies, rather than directory HTML or empty browser details, informed these procedures. Product, portal, historical manual and ROS model differences remain attached to their sources.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                                                                                                                                                                                                                                                                 | Purpose and exact scope                                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| [Z1 manufacturer page](https://www.unitree.com/z1/)                                                                                                                                                                                                                                      | AIR/PRO comparison, module and joint tables, application images                                                                       |
| [Official Z1 download page](https://www.unitree.com/download/z1/)                                                                                                                                                                                                                        | Observed document/update-log entry points; no usable manual download target in the retrieved HTML                                     |
| [English Z1 developer portal](https://support.unitree.com/home/en/Z1_developer), [controller-linked article](https://support.unitree.com/home/en/Z1_developer/z1)                                                                                                                        | Official development documentation entry points; detailed contents not verified in this review                                        |
| [Unitree-branded Z1 manual via Generation Robots](https://static.generation-robots.com/media/user-manual-z1-unitree-robotics.pdf)                                                                                                                                                        | Eight scans including distributor contact page; historical safety, mounting and wiring illustrations; no visible revision established |
| [Standalone SDK source](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/README.md), [CMake](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/CMakeLists.txt)                                              | Architecture-specific library integration and optional Python binding                                                                 |
| [Standalone controller source](https://github.com/unitreerobotics/z1_controller/blob/639bb773bd11b0e8495faf40eadc9e8eb8bc8400/README.md), [configuration](https://github.com/unitreerobotics/z1_controller/blob/639bb773bd11b0e8495faf40eadc9e8eb8bc8400/config/config.xml)              | Controller branch and network/collision defaults                                                                                      |
| [ROS source and model](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/README.md), [URDF](https://github.com/unitreerobotics/z1_ros/blob/d3bafd38fb48e805096da7abb0c19a15b636975d/z1_controller/config/z1.urdf)                                  | Separate ROS 1 stack and model audit target; not a fabrication drawing                                                                |
| [Model example](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/examples_py/example_model.py), [arm model API](https://github.com/unitreerobotics/z1_sdk/blob/f1af2b42f2a39a5010946e049ad3fe324e2e6f06/include/unitree_arm_sdk/model/ArmModel.h) | Kinematics/dynamics API reference; not executed here                                                                                  |

No independently verified current firmware image, electrical emergency-stop circuit, connector pinout or current manufacturing CAD package was obtained. Do not substitute the ROS URDF for dimensioned mechanical approval or a different arm's firmware.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Product HTML, the named repository files and the distributor-hosted manual were read on 24 November 2026. Manual mounting, port, joint and zero-reference figures on pp. 3–7 were visually checked; links preserve the original attribution instead of republishing the manual. The PDF's file modification metadata is not a manual revision.

Only the original offline XML audit and its negative-input checks were executed. No vendor SDK, build, ROS launch, simulation, firmware operation or hardware test was run. The developer portal returned HTTP 567 to this direct client; browser access elsewhere is known to work, but no complete portal-content review is claimed. This is a bounded engineering reference: current wiring, stop circuit, calibration revision and firmware/controller compatibility remain prerequisites for live commissioning.

**Related documentation:** [Unitree model and development directory](./).
