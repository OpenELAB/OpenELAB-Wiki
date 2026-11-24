---
description: >-
  Compare the actual H1-2 AVP and H1 Kinect workflows, inspect pinned
  teleoperation sources, and separate tracking, video, hands and robot-control
  compatibility.
---

# Unitree teleoperation: AVP, Kinect and model compatibility

{% hint style="info" %}
**Shared development guide: Unitree teleoperation.** This is a task reference, not another robot, hand SKU or developer entitlement. Use the [canonical SDK2 state guide](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development), [ROS2 integration guide](https://wiki.openelab.io/robotics/unitree/unitree-ros2-integration) and [G1 model guide](https://wiki.openelab.io/robotics/unitree/unitree-g1-standard-edu-development-guide) for their respective scope. The first result below uses public source inspection only.
{% endhint %}

Unitree's two English teleoperation articles document different systems: Apple Vision Pro wrist/hand tracking for **H1-2's two seven-joint arms**, and Azure Kinect body tracking primarily for **H1's two four-joint arms**. Tracking, inverse kinematics, joint commands, hand control and video streaming are separate contracts. A visible avatar or camera stream does not establish safe or compatible robot control. [Apple Vision Pro article](https://support.unitree.com/home/en/Teleoperation/avp_teleoperate), [Kinect article](https://support.unitree.com/home/en/Teleoperation/kinect_teleoperate)

## Product overview <a href="#product-overview" id="product-overview"></a>

The Apple Vision Pro article uses TeleVision to obtain wrist/hand information, Pinocchio and CasADi for inverse kinematics (IK), Meshcat for debugging, a Python DDS wrapper for H1-2 communication and separate hand/image services on PC2. IK converts an end-effector pose into joint targets; it does not itself establish collision avoidance or physical joint-limit enforcement.

The Kinect article converts tracked skeletal angles into H1 shoulder pitch/roll/yaw and elbow pitch targets. It includes MuJoCo visualization and a posture detector for enable/disable intent. Torso rotation and hand open/close tracking are described as unstable and disabled. Seven-joint arm retargeting is not established by that eight-joint example. Its G1 macro discussion explicitly adds a **simulation** configuration, not an automatic physical G1 qualification. [Kinect scope and FAQ](https://support.unitree.com/home/en/Teleoperation/kinect_teleoperate)

### Historical article versus current repository <a href="#historical-article-versus-current-repository" id="historical-article-versus-current-repository"></a>

The inspected repository commits are `avp_teleoperate` **`7e5026e4732cf166bcd1210d7958a75575d5fc95`** and `kinect_teleoperate` **`c520506d44dceeea3391b924fe1876d092a42e22`**. The AVP repository has evolved into the XR teleoperation workflow: its current README says v1.6, introduces newer arm/end-effector choices and replaces the original temporary DDS wrapper with `unitree_sdk2_python`. Its initial run/record keys and image system differ from the old article. Do not combine the old installation and startup sequence with current main. [Pinned XR/AVP README](https://github.com/unitreerobotics/avp_teleoperate/blob/7e5026e4732cf166bcd1210d7958a75575d5fc95/README.md), [pinned Kinect README](https://github.com/unitreerobotics/kinect_teleoperate/blob/c520506d44dceeea3391b924fe1876d092a42e22/README.md)

## Applications <a href="#applications" id="applications"></a>

* **Retargeting design:** document source/body frames, left/right assignment, wrist versus joint targets, model revision and supported joint subset before discussing gains or control.
* **Human demonstration and data collection:** keep episodes associated with exact robot/hand/model, software commit, calibration, frame timestamps and tracking validity. A recording switch is not a stop mechanism.
* **Vision troubleshooting:** distinguish image acquisition, transport and display from the motion-command path. The original AVP image client is an image-service diagnostic, not the teleoperation client.
* **Offline compatibility review:** compare article generation, repository generation, target robot, hand service and communication binding without enabling any robot control.

No source here makes a different robot's URDF, IK solver or joint map interchangeable. H2/H2-X, R1 variants, G1+, locked-waist G1 variants and third-party hands require their own confirmed model/configuration contract; a current CLI choice or catalog entry alone does not qualify a delivered unit.

## Specifications <a href="#specifications" id="specifications"></a>

| Layer              | AVP article baseline                                                               | Kinect article baseline                                                                                     |
| ------------------ | ---------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Robot/joint target | H1-2, 7 joints per arm                                                             | H1, 4 joints per arm; total 8                                                                               |
| Host               | x86\_64; Ubuntu 20.04 or 22.04 reported                                            | x86\_64; Ubuntu 20.04 reported                                                                              |
| Tracking device    | Apple Vision Pro and USB binocular camera for robot view                           | Azure Kinect DK with USB 3.0, sensor and body-tracking SDKs                                                 |
| Environment        | Python 3.8 `tv`; Pinocchio **3.1.0**, CasADi, Meshcat; TeleVision requirements     | Sensor SDK **1.4.1**, Body Tracking **1.1.2**, MuJoCo **3.1.5**, CMake/Ninja/Eigen3                         |
| Article transport  | Temporary Python `unitree_dds_wrapper`; image service port 5555; XR HTTPS/WSS 8012 | Retargeting/controller source plus MuJoCo/Kinect render loops; exact physical command path must be reviewed |
| Intent activation  | Old article waits for an `s` start signal after pose alignment                     | Posture detector toggles `START.`/`END.` after a sustained gesture                                          |

[AVP prerequisites, hardware and startup](https://support.unitree.com/home/en/Teleoperation/avp_teleoperate), [Kinect prerequisites, hardware and startup](https://support.unitree.com/home/en/Teleoperation/kinect_teleoperate). These are observed historical requirements, not current download recommendations or a complete firmware matrix. Kinect's published test firmware is RGB 1.6.110, depth 1.6.80, depth configuration 6109.7 and audio 1.6.14. Its query and update operations are distinct; no firmware update is part of this guide.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

For AVP, the article places an ordinary driver-free binocular USB camera on the robot so the operator can view the workspace; camera mounting, field of view and OpenCV acquisition parameters must be matched. It places arm/hand services and the image server on H1-2 PC2, while the host solves IK and receives tracking. A different camera is only a potential video replacement, not a replacement body-tracking or calibration contract.

For Kinect, the source requires a horizontal, unobstructed camera placement with the person's skeleton in view and describes a position behind the H1 from which the operator can observe it. When multiple people are visible, the example tracks the nearest person. That policy can change control identity unintentionally; an application should explicitly reject an unexpected subject switch. Orbbec replacement is suggested theoretically, not validated as a drop-in SDK substitute. [Hardware/FAQ sections](https://support.unitree.com/home/en/Teleoperation/kinect_teleoperate)

Neither article supplies a complete power/pinout/approved charger or current stop contract for every named robot. Use the exact model manual and approved mechanical protection before any later physical work. The sources warn about arm-to-arm and person/environment collision, hot joints, startup pose mismatch and shutting down after use. A seated/suspended demonstration does not prove a safe hold. Tracking loss, gesture `END.`, closing a window, terminating Python and an effective hardware emergency stop are different events; no equivalent outcome is guaranteed here.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### AVP article's complete software path <a href="#avp-articles-complete-software-path" id="avp-articles-complete-software-path"></a>

1. **IK environment:** the article installs Pinocchio before TeleVision, requires 3.1.0 and warns that a differently sourced installation/order can break the environment. CasADi solves optimization; Meshcat is a debugging display. Preserve the environment rather than blindly mixing current package versions.
2. **Original communication binding:** `unitree_dds_wrapper` connects the host to H1-2 PC2. The pinned wrapper README uses publisher/subscriber abstractions and an `rt/test_dds` publish loop; it is not a passive test or a universal robot compatibility guarantee. [Pinned wrapper](https://github.com/unitreerobotics/unitree_dds_wrapper/blob/369808ab6f9f24e3c0a8fc39c764472c1ac54a25/README.md)
3. **TeleVision and Isaac Gym:** the old article installs repository requirements and Isaac Gym Preview 4 for environment testing. This differs from the current XR README's Isaac Lab simulation path.
4. **Trust and browser setup:** the article uses mkcert, a certificate matching the actual host address, a trusted root on AVP, Safari WebXR feature flags and port 8012 HTTPS/WSS. A certificate for the example `192.168.123.2` does not validate another host. Keep private keys private; transfer only the intended trust certificate. Shell installers, certificate trust changes and firewall changes are separate setup actions, not necessary for the source-inspection first result.
5. **Services:** the hand package/service is separate from arm control; its example continuously opens/closes fingers and is **actuation**, not a status check. `image_server.py` on PC2 and `image_client.py` on the host validate image transport, with camera/port settings checked separately. The main `teleop_hand_and_arm.py` can command arms and lock other joints; it is not read-only. [Article services/code directory](https://support.unitree.com/home/en/Teleoperation/avp_teleoperate)

### Kinect article's complete software path <a href="#kinect-articles-complete-software-path" id="kinect-articles-complete-software-path"></a>

The sensor packages and development headers precede the body-tracking packages; the article also names libxi, libxinerama, libxcursor and libsoundio dependencies and udev access rules. `k4aviewer` checks imagery, whereas `k4abt_simple_3d_viewer` checks skeleton tracking, with `h` showing help. The example links its bundled MuJoCo 3.1.5/model resources and uses CMake/Ninja plus Eigen3. Installing an unpinned current `mujoco` Python package for viewing would not establish equivalence with that bundled C++ library. [Kinect environment sections](https://support.unitree.com/home/en/Teleoperation/kinect_teleoperate)

Its source directory separates `jointRetargeting.hpp` (mapping), `math_tool.hpp` (filter/quaternion helpers), `StartEndPoseDetector.hpp` (intent detection) and `main.cpp` (integration/render/control). The wake-up gesture is a source-specific toggle; `ESC`, `h`, `b` and `k` are interface controls. An `END.` message is not a verified physical stop. [Pinned implementation](https://github.com/unitreerobotics/kinect_teleoperate/blob/c520506d44dceeea3391b924fe1876d092a42e22/src/kinect_teleoperate_robot/main.cpp), [gesture detector](https://github.com/unitreerobotics/kinect_teleoperate/blob/c520506d44dceeea3391b924fe1876d092a42e22/src/kinect_teleoperate_robot/include/StartEndPoseDetector.hpp)

### Current XR interface: a separate baseline <a href="#current-xr-interface-a-separate-baseline" id="current-xr-interface-a-separate-baseline"></a>

The pinned current AVP/XR README exposes `--frequency` (default 30), `--input-mode`, `--display-mode`, `--arm`, `--ee`, `--img-server-ip` and `--network-interface`. Mode flags include `--sim`, `--motion`, `--headless`, `--ipc`, `--record` and task metadata/directory fields. The arm choices include G1\_29/G1\_23/H1\_2/H1/H2/R1\_A5/R1\_A7; they are configuration names, not a complete hardware entitlement matrix. Its image default is `.164`, unlike the old article's host example.

The current text uses teleimager/televuer services, official SDK2 Python, a different run/record state machine and optional Inspire/BrainCo/Dex1/Dex3 hand paths. Its internally wired Dex1 case uses motor indices 31 and 33 and explicitly does not support simultaneous `--motion`; this must not be generalized to external grippers or another robot. The current `--motion` option can permit locomotion and has mode restrictions. **Do not add it to a simulator or “test” command by habit.** [Pinned current parameter/state sections](https://github.com/unitreerobotics/avp_teleoperate/blob/7e5026e4732cf166bcd1210d7958a75575d5fc95/README.md)

Repository root licenses read: current AVP/XR Apache-2.0; Kinect and DDS wrapper BSD-3-Clause. Third-party tracking, assets and binary dependencies have separate terms. This guide links the implementations and supplies original interpretation.

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result: a robot-free teleoperation compatibility record <a href="#first-result-a-robot-free-teleoperation-compatibility-record" id="first-result-a-robot-free-teleoperation-compatibility-record"></a>

Prerequisites: a browser only. No headset, camera, robot, DDS network or package installation is required.

1. Open the [AVP article](https://support.unitree.com/home/en/Teleoperation/avp_teleoperate), locate H1-2, two seven-joint arms, Pinocchio 3.1.0 and the temporary DDS wrapper. Record these as the **article generation**.
2. Open the [pinned current AVP/XR README](https://github.com/unitreerobotics/avp_teleoperate/blob/7e5026e4732cf166bcd1210d7958a75575d5fc95/README.md), locate the migration to SDK2 Python, `--arm`, `--sim`, `--motion` and the state diagram. Record these as a **different repository generation**; do not combine activation keys.
3. Open the [Kinect article](https://support.unitree.com/home/en/Teleoperation/kinect_teleoperate), find H1's eight-joint scope, the nearest-person behavior and G1's simulation macro note. Then locate the pinned [gesture detector](https://github.com/unitreerobotics/kinect_teleoperate/blob/c520506d44dceeea3391b924fe1876d092a42e22/src/kinect_teleoperate_robot/include/StartEndPoseDetector.hpp) and [main integration file](https://github.com/unitreerobotics/kinect_teleoperate/blob/c520506d44dceeea3391b924fe1876d092a42e22/src/kinect_teleoperate_robot/main.cpp). Classify these as active control logic, not passive camera utilities.
4. Write a record with `article`, `repository commit`, `robot/arm subset`, `hand`, `tracking identity`, `IK/model revision`, `transport`, `activation generation` and `unresolved physical stop contract`.

**Expected result:** two clearly separated teleoperation designs and an explicit article/current-source mismatch for AVP. If the article and repository instructions differ, use the pinned file's contents for that file while keeping the historical article scope; obtain a complete matched baseline before installation. No tracking or robot connection is established by this result.

For a later offline tracking replay, an original engineering acceptance gate should require two fresh monotonic frames from the same selected subject, valid finite transforms, consistent handedness/frame convention and a continuous startup pose. Reject missing/stale frames, subject swaps and discontinuities; retain the reason with the episode. These checks improve diagnosis but do not replace physical collision/stop qualification.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

**Video works but arms or hands do not.** Check image, arm and hand paths separately. Confirm model/hand selection and service generation first. The old article recommends a hand-opening example, but that is an actuator test and is not an authorized read-only diagnostic here.

**Browser connection fails.** Check the actual host address against the certificate subject, trust installation, WebXR support, HTTPS/WSS scheme and chosen port. Do not copy an example private key or expose a service simply to remove a certificate error. Current XR WebRTC/image-service settings differ from the old 8012/5555 arrangement.

**`Callable`/typing error appears.** The old AVP FAQ suggests removing the external `typing` package. First establish the Python environment and package provenance; do not treat this historical remedy as a universal dependency fix.

**The wrong person or wrong arm moves in a replay.** Inspect subject identity, left/right convention, quaternion ordering, coordinate transforms and model map before any physical test. Kinect's nearest-person selection and lack of stable seven-joint tracking are material limits.

**Can another humanoid use the same program?** The AVP article explicitly requires changes including URDF, IK and joint mapping. Kinect's G1 addition is described as simulation. Current source options are separate evidence, with delivered hardware/firmware and hand support still needing qualification.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

### Complete two-article functional index <a href="#complete-two-article-functional-index" id="complete-two-article-functional-index"></a>

| Article and revision                                                                                      | Sections retained in this guide                                                                                                                                                                          | Original visual/resources                                                                                                                                                                                                         |
| --------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Apple Vision Pro](https://support.unitree.com/home/en/Teleoperation/avp_teleoperate), updated 2026-07-20 | H1-2 scope; IK/toolchain/order; wrapper; TeleVision/Isaac Gym; certificates/WebXR; hardware/placement; hand and image services; activation; code directory; heat/collision/shutdown notes; all four FAQs | [AVP WebXR settings figure](https://doc-cdn.unitree.com/static/2024/8/8/c38970cd2ac84f84ac8ba18905634f4f.PNG); article also links demos, hardware and dexterous-hand resources                                                    |
| [Kinect](https://support.unitree.com/home/en/Teleoperation/kinect_teleoperate), updated 2024-08-17        | H1 joint subset; sensor/body SDK/udev; viewers/firmware; MuJoCo/build; hardware/placement; control/render startup; gesture toggle; source layout; notes; all four FAQs                                   | [Joint/scene visualization](https://oss-global-cdn.unitree.com/static/681684ac9f2e42ba896b9ea1b1edc754_2386x912.png); [gesture figure](https://doc-cdn.unitree.com/static/2024/8/13/9440eece6f3f421a9d7f93d906f6edd5_465x828.png) |

Additional pinned resources: [current XR README](https://github.com/unitreerobotics/avp_teleoperate/blob/7e5026e4732cf166bcd1210d7958a75575d5fc95/README.md), [Kinect README](https://github.com/unitreerobotics/kinect_teleoperate/blob/c520506d44dceeea3391b924fe1876d092a42e22/README.md), [DDS wrapper](https://github.com/unitreerobotics/unitree_dds_wrapper/blob/369808ab6f9f24e3c0a8fc39c764472c1ac54a25/README.md), [SDK2 state guide](https://wiki.openelab.io/robotics/unitree/unitree-sdk2-state-development), [ROS2 guide](https://wiki.openelab.io/robotics/unitree/unitree-ros2-integration), [G1 model guide](https://wiki.openelab.io/robotics/unitree/unitree-g1-standard-edu-development-guide). Visual links point to selected original figures; the full original resource context remains in each article. No complete manual, video or vendor source is republished here.

### Original figure and media link index <a href="#original-figure-and-media-link-index" id="original-figure-and-media-link-index"></a>

These are links to the original article resources, not newly measured results or reproduced manuals. All linked media retain their source context.

<details>

<summary>Apple Vision Pro Teleoperation — 8 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2024/8/5/7c274f1ec3e94eeb84646b1e3be198ca.mp4) · [Resource 2](https://doc-cdn.unitree.com/static/2024/8/5/bffc6668591446cc8a05c8fffc7dc3f8.mp4) · [Resource 3](https://oss-global-cdn.unitree.com/static/d079e884c3074e8495f81e78c9586f7f_2556x1179.jpg) · [Resource 4](https://doc-cdn.unitree.com/static/2024/7/25/906bba699e404bf5958c94ee2c80446c_1018x603.png) · [Resource 5](https://doc-cdn.unitree.com/static/2024/4/1/9ee12fb5d2f240cd97a2cd95e81799f3_508x330.png) · [Resource 6](https://gw.alicdn.com/imgextra/i4/3411868585/O1CN01km1zwx2DHyzkvFZ1q_!!3411868585.jpg) · [Resource 7](https://doc-cdn.unitree.com/static/2024/8/8/cbd90f1b20674a8999d3752de0373ac2.PNG) · [Resource 8](https://doc-cdn.unitree.com/static/2024/8/8/c38970cd2ac84f84ac8ba18905634f4f.PNG)

</details>

<details>

<summary>Kinect Teleoperate — 9 source figures/media</summary>

[Resource 1](https://doc-cdn.unitree.com/static/2024/8/13/98ca3f9539684ce3bcd4b4d362aac8fd.mp4) · [Resource 2](https://oss-global-cdn.unitree.com/static/b664417592fc49dd9a5c875e2cd82e7a_1691x1041.png) · [Resource 3](https://oss-global-cdn.unitree.com/static/ad01fc07be9a4607a2285614327fc7d3_1028x972.png) · [Resource 4](https://doc-cdn.unitree.com/static/2024/7/25/b3b26e125996448ea8e850e8516689de_1726x1015.png) · [Resource 5](https://doc-cdn.unitree.com/static/2024/6/18/35febba7f3524463ab8b4b7305d7bffd_2000x2000.png) · [Resource 6](https://doc-cdn.unitree.com/static/2024/7/29/1618750fea5743f4b0c07ad24cf4d310_4608x3072.png) · [Resource 7](https://oss-global-cdn.unitree.com/static/681684ac9f2e42ba896b9ea1b1edc754_2386x912.png) · [Resource 8](https://doc-cdn.unitree.com/static/2024/8/13/9440eece6f3f421a9d7f93d906f6edd5_465x828.png) · [Resource 9](https://doc-cdn.unitree.com/static/2024/8/13/86d82ea9c931476f8db6966708d32c00_511x856.png)

</details>

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed **2026-11-24** against both actual English article bodies and the pinned resources above. Article update dates do not identify a robot firmware or guarantee a repository match. Hardware support outside the explicitly described configurations remains a gap.

**Validation:** source inspection only; headset/camera/SDK installation, vendor builds/execution, simulators, DDS/ROS and physical robot/hand motion **not run**. Source-bounded draft: any future simulator work must use an isolated host/interface/domain with no real-robot bridge, and physical deployment needs exact model/hand/firmware/manual and stop qualification.

**Related documentation:** [Unitree model and development directory](./).
