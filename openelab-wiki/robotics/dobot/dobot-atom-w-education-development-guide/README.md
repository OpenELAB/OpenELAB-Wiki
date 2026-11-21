---
description: >-
  Model-specific ATOM-W Standard and Education development guide, SDK/ROS 2
  simulation setup and humanoid robotics course index.
---

# DOBOT ATOM-W — Education and Development Guide

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (Standard Version shown on the storefront; Education Version SKU requires separate verification) · **Variants:** Standard Version / Education Version · **Robot class:** Wheeled humanoid, not a biped walking robot
{% endhint %}

### Product overview

The DOBOT ATOM-W integrates a mobile wheeled chassis with a humanoid upper body for mobile manipulation, perception, teleoperation, teaching and embodied-AI data collection. This is the **ATOM-W-specific education and engineering entry point**. It is based on DOBOT's _Humanoid Robot Technology and Applications_ course outline **V2.0, 2026-09-15**, then extended with identifiable hardware requirements and manufacturer technical resources.

The uploaded course outline covers **general humanoid robotics**, including _bipedal gait planning_. **ATOM-W does not have bipedal legs**: treat humanlike walking, support/swing phases and legged reinforcement learning as comparative theory or simulation on separately compatible platforms. For the actual ATOM-W, emphasize **wheeled navigation, the torso/arms and mobile manipulation**.

The previously published [DOBOT ATOM Humanoid Robot Quick Start](../dobot-atom-humanoid-robot-quick-start.md) covers different ATOM Max/Standard/Trainer/D models. Do not apply its legged charging, stop or joint-indexing instructions to ATOM-W. An **ATOM-W User Guide V1.0 (2026-08-07)** exists and is the appropriate physical-operation reference.

### Applications

* University instruction in kinematics, dynamics, robot operation, sensors and ROS 2 simulation.
* Wheeled navigation with visual/environmental perception and interactive exhibit guiding.
* Dual-arm manipulation research, including vision-guided grasping and sorting with **compatible hands or grippers**.
* Embodied-data collection and teleoperation with the **Education Version** components.
* Integration research for indoor industrial and service scenarios, subject to site safety assessment.

### Specifications

| Item                                  | Standard Version | Education Version |
| ------------------------------------- | ---------------- | ----------------- |
| ATOM-W wheeled humanoid body          | Included         | Included          |
| Battery                               | 45 Ah            | 45 Ah             |
| Original charger and user manual      | Included         | Included          |
| Dexterous hands                       | Not included     | Two 6-DoF hands   |
| Wrist/hand-mounted depth cameras      | Not included     | Two               |
| VR Quest device                       | Not included     | One               |
| Embodied AI data-collection toolchain | Not included     | Included          |

**Product-listed platform characteristics:** 20 DoF excluding hands (head 2, arms 7 × 2, waist 4), \~1785 × 500 × 500 mm (H × W × D), 600 mm arm reach excluding hands, rated arm payload **3.5 kg per arm**, and platform-listed **±0.05 mm repeat positioning accuracy** under manufacturer conditions. Head perception includes a depth camera and binocular imaging; a microphone and two speakers are listed. Do not treat these headline figures as validated full-system grasping accuracy or guaranteed navigation performance.

Reference: [exact ATOM-W storefront, configurations and specifications](https://openelab.io/products/dobot-atom-w-wheeled-humanoid). Document the physically installed hand manufacturer/variant and depth-camera model on your actual robot.

### Hardware and connections

1. Identify **ATOM-W**, Standard versus Education, full system serial, installed base/controller, wrist sensors and hand or gripper part numbers. Verify actual contents against the packing list; do not assume a standard robot can grasp.
2. Use the original 45 Ah battery, charger, charging procedure and safety labels. Do not invent a supply voltage, custom GPIO pinout, wiring diagram or arm-flange dimensions; use the **ATOM-W V1.0 user guide** for exact interface drawings.
3. For manufacturer development networking, the manuals show the **192.168.8.0/24** network, with **PC1 192.168.8.234** and developer-accessible **PC2 192.168.8.13**. PC1 is reserved for control programs and is not an unrestricted user workstation. Verify these on the delivered firmware before use.
4. Keep the robot and its wheels stationary for first SDK and state-reading lessons. The manual discusses a **Logitech F710** controller in X-mode, the chassis emergency-stop devices and remote **LB + A** to decelerate/stop the chassis while damping the upper body; verify the delivered controller and its stop function before any actuation.
5. Clear a large indoor work envelope, isolate bystanders and account for both **chassis motion** and **arm reach**. Grasping or navigation code is **not safety-rated** by this curriculum.

### Software and development resources

| Stack                          | Actual documentation                                                                                                                                                                        | Model-scope note                                                                                                                               |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| C++ Atom SDK                   | [DOBOT-Arm/dobot\_atom\_sdk](https://github.com/Dobot-Arm/dobot_atom_sdk)                                                                                                                   | README specifies Ubuntu 20.04, GCC 9.4; sample binaries rpc\_test, bridge\_test, record\_joint. **rpc\_test and bridge\_test can move motors** |
| Official SDK application guide | [ATOM Series SDK Development Guide V2.1, 2026-08-26](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) | Explicit **ATOM\_W** joint and network scope; identify actual firmware revision                                                                |
| ROS 2 package                  | [DOBOT-Arm/dobot\_atom\_ros2](https://github.com/Dobot-Arm/dobot_atom_ros2)                                                                                                                 | Ubuntu 22.04 / Humble or Ubuntu 20.04 / Foxy listed; includes **ATOM W-P3 Gazebo** and separate **ATOM P2** legged simulation                  |
| ATOM-W Gazebo                  | [atom\_gazebo README](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md)                                                                                         | W-P3 wheeled model; sim outputs are **not hardware validation**                                                                                |
| Reinforcement learning         | [embodied-dobot/atom-locomotion-training](https://github.com/embodied-dobot/atom-locomotion-training)                                                                                       | Explicit **ATOM P2/P3 legged** tasks; **not ATOM-W-compatible walking instructions**                                                           |

The C++ SDK and ROS 2 repository have different documented build environments. Do not claim that a single machine image, URDF, message definition or DDS configuration is verified for every ATOM-W firmware revision.

### Getting started

#### First result A — wheeled humanoid in simulation (no physical robot required)

On an Ubuntu 22.04 computer with **ROS 2 Humble, Gazebo Classic ROS integration and colcon** installed per the [official ROS 2 README](https://github.com/Dobot-Arm/dobot_atom_ros2):

```bash
mkdir -p ~/atom_ros2_ws/src
cd ~/atom_ros2_ws/src
git clone https://github.com/Dobot-Arm/dobot_atom_ros2.git
cd ~/atom_ros2_ws
rosdep install --from-paths src --ignore-src -r -y
colcon build
source /opt/ros/humble/setup.bash
source install/setup.bash
ros2 launch atom_gazebo atom_gazebo.launch.py
```

**Expected result:** the repository's **Atom W-P3** model loads in Gazebo. Record the loaded links/joints, controllers and any warnings. This is a documented command to reproduce, **not a claim that it was run**. If the model or controller fails, check the exact package dependencies listed in [atom\_gazebo README](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md), ROS environment, Gazebo installation, controller names and build log.

#### First result B — robot development link and SDK compilation (no motion request)

After checking the actual ATOM-W network and safety/manual prerequisites:

```bash
ip addr show
ping -c 3 192.168.8.234
git clone https://github.com/Dobot-Arm/dobot_atom_sdk.git
cd dobot_atom_sdk
mkdir -p build
cd build
cmake ..
make
```

**Expected result:** a successful network response (if the manufacturer default is active) and compiled example binaries, including **rpc\_test**, **bridge\_test** and **record\_joint**. Compilation does not prove robot compatibility. **Do not run rpc\_test or bridge\_test for the first communication check**: the manufacturer warns that those samples issue motion commands, and the low-level bridge requires a separately verified debug state. For read-only robot state, proceed to Chapter 5's verified topic-reader workflow.

### Curriculum — eight chapters and three application projects

| Learning sequence | Tutorial                                                                                | Scope                                                    |
| ----------------- | --------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| Chapter 1         | [Introduction and ATOM-W architecture](atom-w-chapter-1-humanoid-architecture.md)       | Humanoid foundations; wheeled versus bipedal             |
| Chapter 2         | [Perception systems](atom-w-chapter-2-perception-systems.md)                            | RGB, depth, LiDAR, joint/IMU and human perception        |
| Chapter 3         | [Kinematics, dynamics and motion planning](atom-w-chapter-3-motion-control-planning.md) | 7-DoF arms, wheeled motion and biped gait theory         |
| Chapter 4         | [Embodied data acquisition](atom-w-chapter-4-data-acquisition.md)                       | Synchronized recording and datasets                      |
| Chapter 5         | [Robot operation and sensors](atom-w-chapter-5-operation-sensors.md)                    | Remote, hardware safety, PC1/PC2 and read-only telemetry |
| Chapter 6         | [Perception and voice interaction](atom-w-chapter-6-human-robot-interaction.md)         | Vision, ASR/TTS planning and command gating              |
| Chapter 7         | [Kinematics simulation and teleoperation](atom-w-chapter-7-kinematics-teleoperation.md) | W-P3 Gazebo, IK and supervised retargeting               |
| Chapter 8         | [Integrated project architecture](atom-w-chapter-8-integrated-projects/)                | Interface contracts, authorization and evaluation        |

#### Three independent Chapter 8 application projects

1. [**8.1 ATOM-W Exhibition Guide**](atom-w-chapter-8-integrated-projects/atom-w-application-exhibition-guide.md) — human detection, explanations, Q\&A and guided wheeled navigation.
2. [**8.2 ATOM-W Vision-Based Grasping**](atom-w-chapter-8-integrated-projects/atom-w-application-vision-grasping.md) — camera calibration, 3D target location, IK and installed hand/gripper requirements.
3. [**8.3 ATOM-W Automotive Parts Sorting**](atom-w-chapter-8-integrated-projects/atom-w-application-parts-sorting.md) — part recognition, calibrated localization, simulated picks and sorting evaluation.

The structure follows the course's eight chapters and three final projects. Each page gives prerequisites, a software/simulation checkpoint, expected result and a documented boundary before physical actuation.

### Troubleshooting and FAQs

**How is ATOM-W different from ATOM Max/Standard?** ATOM-W has a wheeled mobile base. Avoid reusing legged robot control states, leg joint mapping, charging or stop procedures from the separate ATOM Max user manual.

**Why is the hand state topic unavailable?** The **Standard Version does not include dexterous hands**; confirm the installed end-effector and SDK type. Education Version hands must also be commissioned and mapped to the correct device.

**A ROS 2 subscriber sees no data:** verify the intended live robot versus simulation mode, correct ROS 2/SDK version, chosen Ethernet interface and CycloneDDS settings. Success in Gazebo does not establish a live hardware connection.

**Does this course provide an autonomous grasp/sort program?** No. The uploaded document is a **course outline**. The linked application tutorials provide an incremental implementation and test plan, not a claimed finished integrated system.

### Downloads and technical documents

| Resource                                                 | Use                                                                          | Source                                                                                                                                                  |
| -------------------------------------------------------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| ATOM-W User Guide V1.0 (2026-08-07)                      | Physical safety, charging, remote, PC1/PC2, AMR setup, mechanical interfaces | [Manufacturer-authored manual mirrored at ManualsLib](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html)                                      |
| ATOM SDK Application Development Guide V2.1 (2026-08-26) | Model-specific joints, RPC/DDS, networking and examples                      | [DOBOT document](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) |
| DOBOT C++ Atom SDK                                       | Compiling example clients and protocol types                                 | [GitHub](https://github.com/Dobot-Arm/dobot_atom_sdk)                                                                                                   |
| DOBOT Atom ROS 2                                         | Robot description, W-P3 sim, state readers                                   | [GitHub](https://github.com/Dobot-Arm/dobot_atom_ros2)                                                                                                  |
| Atom W-P3 simulation documentation                       | Launch and Gazebo dependencies                                               | [Official subpage](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_gazebo/README.md)                                                        |
| ATOM-W product brochure                                  | Specifications and variants                                                  | [OpenELAB product/download tab](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)                                                             |

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, Tutorial Guide V2.0 (2026-09-15), uploaded by OpenELAB.
* [OpenELAB exact ATOM-W listing](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* DOBOT, _ATOM-W Wheeled Humanoid Robot User Guide_ V1.0 (2026-08-07), mirror linked above.
* DOBOT, _ATOM Series SDK Application Development Guide_ V2.1 (2026-08-26), ATOM\_W sections.
* [Official DOBOT Atom SDK](https://github.com/Dobot-Arm/dobot_atom_sdk), [Atom ROS 2](https://github.com/Dobot-Arm/dobot_atom_ros2), and [ATOM Learning](https://github.com/embodied-dobot/atom-locomotion-training), reviewed 2026-11-21.

**Document review:** completed for this draft. **Software execution:** not run. **Hardware validation:** not run. **Outstanding:** Education Version SKU, exact hand model and calibration, firmware/SDK pairing, actual ROS 2 joint/frame mapping, safe limits and site risk assessment. Verify source document figures and actual hardware revision before electrical or motion integration.
