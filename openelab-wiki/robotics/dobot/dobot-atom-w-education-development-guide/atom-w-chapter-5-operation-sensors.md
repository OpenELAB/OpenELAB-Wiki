---
description: >-
  DOBOT ATOM-W education chapter with model-specific hardware scope, practical
  workflow, validation checkpoints and source links.
---

# Chapter 5 — ATOM-W Operation and Sensor Practice

{% hint style="info" %}
[**View DOBOT ATOM-W Wheeled Humanoid on OpenELAB**](https://openelab.io/products/dobot-atom-w-wheeled-humanoid)

**Model:** DOBOT ATOM-W · **SKU:** `DOBOT-1200000545` (Standard Version verified; Education SKU pending) · **Versions:** Standard / Education · **Platform:** wheeled humanoid
{% endhint %}

[ATOM-W course index](./) · [ATOM-W physical-operation guide](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) · [Official ROS 2 package](https://github.com/Dobot-Arm/dobot_atom_ros2)

### Product overview

**Chapter 5: Fundamentals of Humanoid Robot Practice** follows **5.1 Familiarization and Basic Operation**, **5.2 Robot Components and Assembly Practice**, and **5.3 Robot Sensor Practice**. This is the **hardware onboarding and read-only commissioning chapter** for ATOM-W, not a request to disassemble, recalibrate or actuate motors.

### Applications

* Establishing an operator's verified startup, shutdown, charging and emergency-stop checklist.
* Recognizing the two-computer ATOM-W architecture and developer access boundaries.
* Inspecting robot joint state, diagnostics, camera, IMU and AMR/LiDAR telemetry without motion.
* Recording the installed accessories and commissioning outcome for subsequent experiments.

### Specifications

| System item                  | ATOM-W-specific detail                                                                                                                                      |
| ---------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Control/developer computers  | Manufacturer manual identifies **PC1 192.168.8.234** (reserved for robot control) and **PC2 192.168.8.13** (authorized development)                         |
| External development network | 192.168.8.0/24 shown in official SDK; actual host IP must not collide                                                                                       |
| Battery supplied             | 45 Ah pack and matching original charger                                                                                                                    |
| Remote                       | ATOM-W user guide describes Logitech F710, **X-mode**, MODE indicator off                                                                                   |
| Stop operations              | User guide describes **LB + A** to damp upper body, lock brakes and gradually stop chassis; chassis emergency stop must be separately identified and tested |
| Read-only diagnostics        | ROS 2 `upper\_state\_reader`, `lower\_state\_reader`, `main\_nodes\_state\_reader`                                                                          |
| Optional hands               | Education Version includes two 6-DoF dexterous hands; Standard does not                                                                                     |

Read all state/stop instructions against [ATOM-W User Guide V1.0](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html), not the other ATOM-Max quick start.

### Hardware and connections

1. Do a visual inspection: chassis, wheels, E-stop, controller, power, arms, attached hands/grippers, cameras and cabling. Keep covers closed and use only approved connectors.
2. Verify the real controller's F710 mode and the physical stop functions with a qualified operator. Do **not** assume the remote used for Atom Max controls ATOM-W identically.
3. Charge with the original unit in the user manual's prescribed state. Never connect a bench supply directly to the robot battery or exposed GPIO.
4. Keep people and loose items clear of the robot. The wheeled chassis can move while the arms extend.
5. Use the authorized external network and **developer PC2**, not arbitrary remote access to PC1. Record permitted IPs without publishing credentials.

### Software and development resources

| Resource                                                                                                                                          | Role                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| [ATOM-W V1.0 manual](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html)                                                                 | Power, charging, remote, AMR, E-stop, connectors and troubleshooting |
| [C++ SDK README](https://github.com/Dobot-Arm/dobot_atom_sdk)                                                                                     | Ubuntu 20.04, GCC 9.4, CMake/make, Ethernet & CycloneDDS             |
| [ROS 2 state-read examples](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_control_examples/README.md)                               | Known read-only programs                                             |
| [SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf) | Model-specific RPC/DDS and joint order                               |

**Do not run** `rpc\_test`, `bridge\_test`, any joint-command publisher or hand grasp controller as the first onboarding step. They can produce physical motion.

### Getting started

#### Task 1 — Safe startup inventory

Follow the **exact user guide's** startup procedure and have the operator verify the emergency-stop and brake functions. Log actual: SKU/edition, battery status, firmware, PC1/PC2 addresses, controller model and software revision. Do not improvise a power-on key sequence.

#### Task 2 — First working result: reachability and read-only status

With the operator supervising an idle robot and an approved development Ethernet connection:

```bash
ip addr show
ping -c 3 192.168.8.234
```

**Expected result:** the machine identifies the correct Ethernet interface and (if the documented default is active) receives ICMP replies from the control network. This is a **network test**, not proof that motor control is ready.

If ROS 2, the correct middleware network and the manufacturer bridge are already configured, run:

```bash
source /opt/ros/humble/setup.bash
source ~/atom_ros2_ws/install/setup.bash
ros2 topic list
ros2 run atom_control_examples upper_state_reader
```

**Expected result:** the official reader prints available upper-body joint/diagnostic messages, if the corresponding state publisher is available. Stop with Ctrl+C. Record actual topic type and timestamps; do not presume that ROS 2 setup on an unrelated legged ATOM version will discover this W model automatically.

#### Task 3 — Sensor inspection, not motion

Using discovered, **verified** topics, test one head camera frame, one IMU/state message, one AMR/LiDAR status and (Education only) one wrist camera/hand status. Save sensor type, calibration reference and results. Never invent a generic `/camera/depth` or `/scan` name as a guaranteed installed topic.

### Troubleshooting and FAQs

**PC1 responds but DDS topics are missing:** ping confirms only IP reachability. Check PC2 permissions, current robot/bridge middleware, DDS interface and ROS domain without changing reserved control software.

**The remote cannot move the chassis:** confirm Logitech F710 **X** switch and MODE light per the ATOM-W guide, battery state, authority and alarm. Don't bypass a stop or brake state.

**A hand reader shows no data:** confirm an actual compatible hand is installed; Standard box contents do not include dexterous hands.

**Can students practice assembly?** Only the externally accessible, manufacturer-approved mounting tasks; internal actuators and high-current connections are not a beginner disassembly exercise.

### Downloads and technical documents

* [ATOM-W User Guide V1.0](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) — model-specific operation and safety.
* [Official ROS 2 read-only examples](https://github.com/Dobot-Arm/dobot_atom_ros2/blob/main/atom_control_examples/README.md).
* [C++ Atom SDK](https://github.com/Dobot-Arm/dobot_atom_sdk).
* [ATOM SDK V2.1](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).

**Student deliverable:** signed safety checklist, device/accessory inventory, network/status log and read-only sensor checklist.

### References and validation

* DOBOT, _Humanoid Robot Technology and Applications_, Tutorial Guide V2.0 (2026-09-15), supplied source; chapter mapping as listed above.
* [OpenELAB, ATOM-W product/edition configuration](https://openelab.io/products/dobot-atom-w-wheeled-humanoid), reviewed 2026-11-21.
* [DOBOT, ATOM-W Wheeled Humanoid Robot User Guide V1.0, 2026-08-07](https://www.manualslib.com/manual/4681300/Dobot-Atom-W.html) (manufacturer document mirrored by a third party).
* [DOBOT, ATOM SDK Application Development Guide V2.1, 2026-08-26](https://a.storyblok.com/f/298593/x/ad7c499105/dobot-atom-series-humanoid-robot-sdk-application-development-guide_v2-1_20260826_en.pdf).
* [Official Atom C++ SDK](https://github.com/Dobot-Arm/dobot_atom_sdk) and [ROS 2 source](https://github.com/Dobot-Arm/dobot_atom_ros2), reviewed 2026-11-21.

**Source review:** completed for documentation draft. **Software execution:** not run. **Hardware validation:** not run. Real ATOM-W trials require a confirmed firmware, installed edition and a supervised, manufacturer-compliant safety procedure.
