---
description: >-
  Commission the JetRover Developer Orin Nano SUPER 8 GB Mecanum kit, inspect
  power, ROS 2 topics, camera/arm calibration and navigation recovery.
---

# Hiwonder JetRover Orin Nano SUPER: Mecanum ROS 2 sensors and navigation

{% hint style="info" %}
[**JetRover Developer / Orin Nano SUPER 8 GB / Mecanum on OpenELAB — SKU Hiwonder-21030861**](https://openelab.io/products/hiwonder-jetrover-ai-car?variant=46077641294022)
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

![JetRover — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-21.png)

_Existing OpenELAB product illustration retained for model context; option contents and electrical connections are identified by the tables and diagrams below._

This JetRover configuration is the **Developer Kit with Orin Nano SUPER 8 GB and Mecanum chassis**. It includes the six-servo arm/gripper, depth camera, **SLAMTEC A1** LiDAR, 7-inch display and a six-microphone array expansion pack. The microphone requires installation. The Ultimate kit's G4 LiDAR and the Ackermann/Tank chassis are different options. [Exact store SKU](https://openelab.io/products/hiwonder-jetrover-ai-car?variant=46077641294022), [official quick-start](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html).

JetRover has both ROS 1 and ROS 2 materials. Use the supplied image and record its environment before modifying packages. The ROS 2 workflow below targets the documented Humble lane; ROS 1 uses different workspace/package names and commands. A product family supporting both does not make a ROS 1 package a ROS 2 executable.

### Other established purchasing options <a href="#models-and-purchasing-options" id="models-and-purchasing-options"></a>

This canonical page also retains the following catalogued family options. The detailed first-run workflow above/below is for the exact host/kit variants in the opening callout; select the matching host image and kit-specific hardware for other options. A controller-excluded option needs that separately supplied host. A ROSOrin base is distinct from ROSOrin Pro with an arm.

| SKU                  | Established option                                                   |
| -------------------- | -------------------------------------------------------------------- |
| `Hiwonder-21030590`  | Standard Kit / Without Controller / Mecanum Chassis                  |
| `Hiwonder-21030552`  | Standard Kit / Without Controller / Ackerman Chassis                 |
| `Hiwonder-21030628`  | Standard Kit / Without Controller / Tank Chassis                     |
| `Hiwonder-21030591`  | Standard Kit / With Raspberry Pi 5(8 GB) / Mecanum Chassis           |
| `Hiwonder-21030586`  | Standard Kit / With Raspberry Pi 5(8 GB) / Ackerman Chassis          |
| `Hiwonder-21030629`  | Standard Kit / With Raspberry Pi 5(8 GB) / Tank Chassis              |
| `Hiwonder-21030592`  | Standard Kit / With Jetson Nano(4 GB) / Mecanum Chassis              |
| `Hiwonder-21030587`  | Standard Kit / With Jetson Nano(4 GB) / Ackerman Chassis             |
| `Hiwonder-21030630`  | Standard Kit / With Jetson Nano(4 GB) / Tank Chassis                 |
| `Hiwonder-21030593`  | Standard Kit / With Jetson Orin Nano Super(4 GB) / Mecanum Chassis   |
| `Hiwonder-21030588`  | Standard Kit / With Jetson Orin Nano Super(4 GB) / Ackerman Chassis  |
| `Hiwonder-21030631`  | Standard Kit / With Jetson Orin Nano Super(4 GB) / Tank Chassis      |
| `Hiwonder-21030594`  | Standard Kit / With Jetson Orin Nano Super(8 GB) / Mecanum Chassis   |
| `Hiwonder-21030589`  | Standard Kit / With Jetson Orin Nano Super(8 GB) / Ackerman Chassis  |
| `Hiwonder-21030632`  | Standard Kit / With Jetson Orin Nano Super(8 GB) / Tank Chassis      |
| `Hiwonder-21030595`  | Standard Kit / With Jetson Orin NX Super(8 GB) / Mecanum Chassis     |
| `Hiwonder-21031590`  | Standard Kit / With Jetson Orin NX Super(8 GB) / Ackerman Chassis    |
| `Hiwonder-21030633`  | Standard Kit / With Jetson Orin NX Super(8 GB) / Tank Chassis        |
| `Hiwonder-21030596`  | Standard Kit / With Jetson Orin NX Super(16 GB) / Mecanum Chassis    |
| `Hiwonder-21031591`  | Standard Kit / With Jetson Orin NX Super(16 GB) / Ackerman Chassis   |
| `Hiwonder-21030634`  | Standard Kit / With Jetson Orin NX Super(16 GB) / Tank Chassis       |
| `Hiwonder-21030597`  | Advanced Kit / Without Controller / Mecanum Chassis                  |
| `Hiwonder-21030559`  | Advanced Kit / Without Controller / Ackerman Chassis                 |
| `Hiwonder-21030635`  | Advanced Kit / Without Controller / Tank Chassis                     |
| `Hiwonder-21030598`  | Advanced Kit / With Raspberry Pi 5(8 GB) / Mecanum Chassis           |
| `Hiwonder-21030560`  | Advanced Kit / With Raspberry Pi 5(8 GB) / Ackerman Chassis          |
| `Hiwonder-21030636`  | Advanced Kit / With Raspberry Pi 5(8 GB) / Tank Chassis              |
| `Hiwonder-21030599`  | Advanced Kit / With Jetson Nano(4 GB) / Mecanum Chassis              |
| `Hiwonder-21030561`  | Advanced Kit / With Jetson Nano(4 GB) / Ackerman Chassis             |
| `Hiwonder-21030637`  | Advanced Kit / With Jetson Nano(4 GB) / Tank Chassis                 |
| `Hiwonder-21030600`  | Advanced Kit / With Jetson Orin Nano Super(4 GB) / Mecanum Chassis   |
| `Hiwonder-21030344`  | Advanced Kit / With Jetson Orin Nano Super(4 GB) / Ackerman Chassis  |
| `Hiwonder-21030638`  | Advanced Kit / With Jetson Orin Nano Super(4 GB) / Tank Chassis      |
| `Hiwonder-21030601`  | Advanced Kit / With Jetson Orin Nano Super(8 GB) / Mecanum Chassis   |
| `Hiwonder-21030562`  | Advanced Kit / With Jetson Orin Nano Super(8 GB) / Ackerman Chassis  |
| `Hiwonder-21030639`  | Advanced Kit / With Jetson Orin Nano Super(8 GB) / Tank Chassis      |
| `Hiwonder-21030602`  | Advanced Kit / With Jetson Orin NX Super(8 GB) / Mecanum Chassis     |
| `Hiwonder-21030563`  | Advanced Kit / With Jetson Orin NX Super(8 GB) / Ackerman Chassis    |
| `Hiwonder-21030640`  | Advanced Kit / With Jetson Orin NX Super(8 GB) / Tank Chassis        |
| `Hiwonder-21030603`  | Advanced Kit / With Jetson Orin NX Super(16 GB) / Mecanum Chassis    |
| `Hiwonder-21030564`  | Advanced Kit / With Jetson Orin NX Super(16 GB) / Ackerman Chassis   |
| `Hiwonder-21030641`  | Advanced Kit / With Jetson Orin NX Super(16 GB) / Tank Chassis       |
| `Hiwonder-21030860`  | Developer Kit / Without Controller / Mecanum Chassis                 |
| `Hiwonder-21031857`  | Developer Kit / Without Controller / Ackerman Chassis                |
| `Hiwonder-21031858`  | Developer Kit / Without Controller / Tank Chassis                    |
| `Hiwonder-21031943`  | Developer Kit / With Raspberry Pi 5(8 GB) / Mecanum Chassis          |
| `Hiwonder-210318571` | Developer Kit / With Raspberry Pi 5(8 GB) / Ackerman Chassis         |
| `Hiwonder-210318580` | Developer Kit / With Raspberry Pi 5(8 GB) / Tank Chassis             |
| `Hiwonder-21031607`  | Developer Kit / With Jetson Nano(4 GB) / Mecanum Chassis             |
| `Hiwonder-210318572` | Developer Kit / With Jetson Nano(4 GB) / Ackerman Chassis            |
| `Hiwonder-21032067`  | Developer Kit / With Jetson Nano(4 GB) / Tank Chassis                |
| `Hiwonder-21031229`  | Developer Kit / With Jetson Orin Nano Super(4 GB) / Mecanum Chassis  |
| `Hiwonder-210318573` | Developer Kit / With Jetson Orin Nano Super(4 GB) / Ackerman Chassis |
| `Hiwonder-210318581` | Developer Kit / With Jetson Orin Nano Super(4 GB) / Tank Chassis     |
| `Hiwonder-21030861`  | Developer Kit / With Jetson Orin Nano Super(8 GB) / Mecanum Chassis  |
| `Hiwonder-210318574` | Developer Kit / With Jetson Orin Nano Super(8 GB) / Ackerman Chassis |
| `Hiwonder-21032066`  | Developer Kit / With Jetson Orin Nano Super(8 GB) / Tank Chassis     |
| `Hiwonder-210320540` | Developer Kit / With Jetson Orin NX Super(8 GB) / Mecanum Chassis    |
| `Hiwonder-210318575` | Developer Kit / With Jetson Orin NX Super(8 GB) / Ackerman Chassis   |
| `Hiwonder-210318582` | Developer Kit / With Jetson Orin NX Super(8 GB) / Tank Chassis       |
| `Hiwonder-21032054`  | Developer Kit / With Jetson Orin NX Super(16 GB) / Mecanum Chassis   |
| `Hiwonder-210318576` | Developer Kit / With Jetson Orin NX Super(16 GB) / Ackerman Chassis  |
| `Hiwonder-210318583` | Developer Kit / With Jetson Orin NX Super(16 GB) / Tank Chassis      |
| `Hiwonder-21030609`  | Ultimate Kit / Without Controller / Mecanum Chassis                  |
| `Hiwonder-21030572`  | Ultimate Kit / Without Controller / Ackerman Chassis                 |
| `Hiwonder-21030647`  | Ultimate Kit / Without Controller / Tank Chassis                     |
| `Hiwonder-21030610`  | Ultimate Kit / With Raspberry Pi 5(8 GB) / Mecanum Chassis           |
| `Hiwonder-21030573`  | Ultimate Kit / With Raspberry Pi 5(8 GB) / Ackerman Chassis          |
| `Hiwonder-21030648`  | Ultimate Kit / With Raspberry Pi 5(8 GB) / Tank Chassis              |
| `Hiwonder-21030611`  | Ultimate Kit / With Jetson Nano(4 GB) / Mecanum Chassis              |
| `Hiwonder-21030574`  | Ultimate Kit / With Jetson Nano(4 GB) / Ackerman Chassis             |
| `Hiwonder-21030649`  | Ultimate Kit / With Jetson Nano(4 GB) / Tank Chassis                 |
| `Hiwonder-21030612`  | Ultimate Kit / With Jetson Orin Nano Super(4 GB) / Mecanum Chassis   |
| `Hiwonder-21030575`  | Ultimate Kit / With Jetson Orin Nano Super(4 GB) / Ackerman Chassis  |
| `Hiwonder-21030650`  | Ultimate Kit / With Jetson Orin Nano Super(4 GB) / Tank Chassis      |
| `Hiwonder-21030354`  | Ultimate Kit / With Jetson Orin Nano Super(8 GB) / Mecanum Chassis   |
| `Hiwonder-21030391`  | Ultimate Kit / With Jetson Orin Nano Super(8 GB) / Ackerman Chassis  |
| `Hiwonder-21030651`  | Ultimate Kit / With Jetson Orin Nano Super(8 GB) / Tank Chassis      |
| `Hiwonder-21030613`  | Ultimate Kit / With Jetson Orin NX Super(8 GB) / Mecanum Chassis     |
| `Hiwonder-21030576`  | Ultimate Kit / With Jetson Orin NX Super(8 GB) / Ackerman Chassis    |
| `Hiwonder-21030652`  | Ultimate Kit / With Jetson Orin NX Super(8 GB) / Tank Chassis        |
| `Hiwonder-21030614`  | Ultimate Kit / With Jetson Orin NX Super(16 GB) / Mecanum Chassis    |
| `Hiwonder-21030363`  | Ultimate Kit / With Jetson Orin NX Super(16 GB) / Ackerman Chassis   |
| `Hiwonder-21030653`  | Ultimate Kit / With Jetson Orin NX Super(16 GB) / Tank Chassis       |

[OpenELAB family options](https://openelab.io/products/hiwonder-jetrover-ai-car).

## Applications <a href="#applications" id="applications"></a>

Use the Mecanum variant for lateral/diagonal motion, encoder/IMU calibration, 2D/3D mapping, navigation and visual mobile manipulation. First establish stable battery power, correct chassis configuration, sensor receipt and one command owner. Then verify short floor motions, a small map and a stationary pick before combining navigation with transport.

The arm-mounted camera changes pose when the arm moves. Keep the camera-to-arm calibration, arm joint state and TF consistent; a grasp inferred from an old camera pose can be wrong even when its image detection is correct. Autonomous driving, bridge crossing and fall-prevention lessons require their specified scenes and sensors; they do not establish general obstacle/edge safety.

## Specifications <a href="#specifications" id="specifications"></a>

| Item              | Assigned configuration                                                                                           |
| ----------------- | ---------------------------------------------------------------------------------------------------------------- |
| SKU / option      | Hiwonder-21030861; Developer / Orin Nano SUPER 8 GB / Mecanum                                                    |
| Main controller   | Orin Nano SUPER 8 GB; matched JetRover image                                                                     |
| Chassis           | JetRover M1 Mecanum; about 324 × 260 × 659 mm; about 4.7 kg reference                                            |
| Arm               | 6DOF bus-servo arm/gripper assembly                                                                              |
| LiDAR             | SLAMTEC A1 for Developer; G4 is Ultimate's upgrade                                                               |
| Depth camera      | Dabai depth-camera branch in robot configuration; verify delivered camera revision                               |
| Display / voice   | 7-inch touch display and six-microphone array expansion packs                                                    |
| Battery           | 11.1 V 6000 mAh lithium pack; 12.6 V charging voltage                                                            |
| Host power        | Orin Nano/NX requires the documented12 V path; not the older Nano/Pi 5 V host output                             |
| Lower controller  | STM32 robot controller; motor/servo/IMU/power feedback and RRC serial transport                                  |
| Encoder reference | Store lists 1024-line AB quadrature feedback; do not infer the software's counts-per-wheel-revolution convention |
| Software lanes    | Ubuntu 22.04/ROS 2 Humble or matched legacy ROS 1 setup; inspect installed image                                 |

Store dimensions/mass are configuration references, not mechanical clearance guarantees. Arm pose, display angle and accessories change the swept envelope. No universal object payload or bare-UART logic rating is inferred from a servo label. [Specifications](https://openelab.io/products/hiwonder-jetrover-ai-car), [power/serial manual](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html#_1-10-ros-usage-instruction).

### Select the exact machine and sensor types

The supplied configuration tool offers camera `Dabai/usb_cam`, LiDAR `A1/A2/G4/S2L/LD14P` and machine `JetRover_Mecanum/JetRover_Acker/JetRover_Tank`. For this SKU, the chassis is **JetRover\_Mecanum** and the supplied LiDAR is **A1**. Choose the actual installed depth-camera branch, not monocular `usb_cam` merely because a color view appears. Keep the ASR language/device setting consistent with the installed microphone. [Configuration reference](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html).

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

![Hiwonder JetRover Orin Nano numbered port photograph](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/assets/image28.I9uMtQvX.webp)

Official Hiwonder Orin photograph, visually inspected. Callouts identify1 host DC power, 2 display DP, 3 depth camera, 4 USB hub, 5 STM32 communication, 6 display power, 7 LiDAR, 8/9 reserved expansion and 10 microphone. Callouts are not pin numbers. Retain these cable roles while diagnosing one subsystem at a time. [Orin wiring table](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html#_1-2-hardware-installation-and-setup).

The display needs both video and its documented C-TOUCH power/touch connection; a working picture alone does not validate touch input. Install the six-microphone expansion using its supplied bracket/cable before voice configuration. Keep camera and servo cables slack through the arm sweep and away from Mecanum rollers.

Use the battery/charging connection on the robot, not the Jetson host's DC jack. Charge with power off and the supplied charger, observing red-to-green completion. The lower-board hardware may advertise a 9–24 V input capability, but that does **not** authorize24 V on this assembled robot: the fitted pack, host regulators, servos and wiring must all match. Retain the factory11.1 V pack and 12.6 V charging arrangement. [Power and controller guidance](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html).

The communication path uses a UART-to-USB circuit and Hiwonder's **RRC** frames: header `AA55`, function byte, length byte, payload, CRC byte. Multibyte payload fields in the illustrated servo response are little-endian. Do not treat a data cable as direct TTL wiring or replay an unverified packet against the arm. The current protocol implementation is the authority for CRC, functions and response interpretation.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

Inspect the supplied system before changing it:

```bash
cat /etc/os-release
printenv ROS_DISTRO ROS_DOMAIN_ID need_compile
ls -ld ~/ros2_ws ~/JetRover_ws ~/ros_ws
ros2 node list
ros2 topic list -t
ros2 pkg prefix controller
```

Use the ROS 2 commands only when that environment is active. The manual shows legacy workspaces with `devel` and `hiwonder_*` packages, while ROS 2 uses `ros2_ws/install` and `app`, `example`, `interfaces`, `slam`, `navigation`, `peripherals`, `driver`, `simulations` and calibration packages. A missing legacy directory is not itself an error on the ROS 2 image. [Software architecture](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html).

The app/gamepad bringup owns motors, serial communication and cameras. Before a standalone lesson, stop the robot, then use the image's documented app stop procedure. ROS 2 lessons use `~/.stop_ros.sh` and/or `sudo systemctl stop start_app_node.service`; restore the corresponding service after custom nodes terminate. Verify the service exists rather than substituting a ROS 1 launcher. Do not leave autonomous navigation and a second teleoperator publishing simultaneously.

## Getting started <a href="#getting-started" id="getting-started"></a>

### 1. First camera/display result

1. Inspect arm/chassis assembly, pack connection and cable routing with power off. Put the robot on a clear level floor and leave room for its startup posture.
2. Boot and wait for the ready beep. A flashing network LED can precede completed ROS bringup. The A1 should rotate after initialization; a G4 startup pattern belongs to the Ultimate option.
3. Join the `HW…` hotspot with password `hiwonder`, open WonderAi and select **Advanced → JetRover(Mecanum)**. Stay connected when warned that the hotspot has no internet.
4. Open Robot Control and confirm a changing camera view without commanding the chassis/arm. On the display, test one harmless desktop icon to distinguish video from touch operation.
5. Connect NoMachine to `192.168.149.1` using the Orin account `ubuntu`/`ubuntu`. Record ROS distribution, system version and robot configuration. Change default credentials before shared-network operation.

\*\*Expected result: \*\* correct Mecanum model, live image, responsive display/touch and reachable Orin desktop. If one path fails, diagnose it separately; camera success does not prove A1 or arm communication. [Connection and startup](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html).

### 2. Read sensor feedback before motion

In the supplied ROS 2 terminal, inspect `ros2 topic list -t`. Select the actual LaserScan and Image topics, then use `ros2 topic info TOPIC --verbose` with the observed topic name to check publisher and QoS. Read a single scan/image header rather than streaming full image arrays into a terminal. In RViz, use the message's frame, then confirm a stationary cardboard target changes the expected scan sector. View color and depth separately; invalid near pixels do not constitute a measured obstacle distance.

The chassis course documents `/odom_raw`, `/imu` and `/controller/cmd_vel`. Start the matching feedback/driver bringup only if it is not already running. With the robot physically stationary, record odometry over10–15 seconds; then compare a short forward move, lateral move and rotation with a floor reference. Correct motor direction, Mecanum roller orientation and chassis selection before changing linear/angular scale. [Motion/IMU/odometry course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/2.Motion_Control_Course.html).

### 3. Original offline RRC frame-boundary inspection

This example analyzes a copied **receive-log byte sequence** without opening a serial port or sending anything. Save as `rrc_inspect.py` and run `python3 rrc_inspect.py 'aa 55 35 05 05 05 00 41 03 00'`. The function/CRC in this synthetic input are illustrative; the final00 is deliberately **not claimed as a valid CRC**. Use an actual receive capture for diagnosis.

```python
import sys

raw = bytes.fromhex(sys.argv[1])
i = 0
frames = 0
while i < len(raw):
    start = raw.find(b'\xaa\x55', i)
    if start < 0:
        break
    if len(raw) - start < 5:
        print('incomplete header at', start)
        break
    function = raw[start + 2]
    length = raw[start + 3]
    end = start + 5 + length
    if end > len(raw):
        print('truncated frame at', start, 'need_bytes=', end - len(raw))
        break
    payload = raw[start + 4:end - 1]
    print('offset=', start, 'function=', hex(function),
          'payload_bytes=', length, 'payload=', payload.hex(' '),
          'crc_byte=', hex(raw[end - 1]), 'CRC_NOT_VALIDATED')
    frames += 1
    i = end
print('candidate_frames=', frames)
```

\*\*Expected result: \*\* one candidate frame with a 5-byte payload and an explicit unvalidated-CRC label. Remove the last byte to see a truncation report. This separates framing/truncation from semantic/CRC verification and does not establish that a frame is safe to replay. Use the matched SDK's CRC/function definitions for a real decoder. [Protocol layout](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html#_1-10-2-ros-serial-port-communication).

### 4. Map and navigate a short route

After manual stop behavior and sensor frames pass, stop competing app control and launch the ROS 2 course sequence in separate terminals:

```bash
ros2 launch slam slam.launch.py
ros2 launch slam rviz_slam.launch.py
ros2 launch peripherals teleop_key_control.launch.py
```

Drive a small closed loop and examine wall overlap, pose continuity and scanner clearance. Save with the course's map-saving procedure under a new name; retain image/YAML together. Confirm the image path, resolution and origin before navigation. Use `ros2 launch navigation navigation.launch.py map:=map_01` only after a matching `map_01` exists, then open `navigation rviz_navigation.launch.py`. Initialize pose, align laser/map walls and choose one nearby free-space goal.

\*\*Expected result: \*\* a plausible planned path and completed goal without oscillation or contact. The arm/display must fit the route as well as the chassis. RTAB-Map uses its own launch/database path; do not run it and 2D localization as competing authorities. [Mapping/navigation](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/4.Mapping_Navigation_Course.html).

### 5. Arm, vision, voice and simulation progression

| Official topic family                                                  | How to obtain a useful bounded result                                                                                                                                                          |
| ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arm control/calibration                                                | Back up deviations and hand-eye/position calibration; verify servo IDs, neutral posture and tool reach with an unloaded small move before a light block                                        |
| Color/hand tracking, sorting, waste classification, line cleanup       | Inspect detection overlays and coordinate conversion first; calibrate in the actual lighting/table setup before enabling an action                                                             |
| 3D picking, fall prevention, bridge crossing, object tracking/grasping | Check valid depth, units, registration and current arm/camera pose. Do not assume every depth pixel is a valid foothold or grasp                                                               |
| LiDAR avoidance/following/guarding                                     | Validate A1 scan first; the ROS 2 course uses `/lidar_controller/enter` and `/lidar_controller/set_running`, with 0 stop and 1/2/3 behavior selection. Verify actual services before actuation |
| OpenCV and machine learning                                            | Fix camera exposure/geometry; test masks, tags and inference outputs separately from motor commands; record model/runtime versions                                                             |
| Six-microphone voice                                                   | Install the Developer array, select its supported configuration and test recognition/audio before enabling motion commands; language/firmware must match                                       |
| MoveIt/Gazebo/URDF                                                     | Check the Mecanum/arm model, frames and collision geometry in simulation; keep the physical bridge stopped until the real mount and limits are verified                                        |
| Large models                                                           | Configure provider/local model independently of ROS bringup. Test responses without physical tools, then inspect permitted action functions, map names and stop/cancel behavior                |

The exact launch names belong to the current image's package set. [Arm course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html), [LiDAR](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/3.Lidar_Course.html), [OpenCV](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/5.ROS+OpenCV_Course.html), [machine learning](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/6.ROS+Machine_Learning_Course.html), [simulation](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/8.MoveIt_Gazebo_Simulation.html), [voice](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/9.Voice_Control_Course.html).

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

| Symptom                           | Diagnostic                                                                                                         |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| No boot or motor-load resets      | Check charged pack, correct host12 V path, cable retention and mechanical stalls before reinstalling ROS           |
| Screen visible but touch fails    | Check C-TOUCH data/power connection separately from DP/video                                                       |
| Wrong motion or no lateral motion | Verify `JetRover_Mecanum`, wheel orientation and motor/encoder assignment; Ackermann/Tank parameters are different |
| Scanner not publishing            | Confirm A1 selection, USB enumeration, power and one driver owner; G4 settings are not a Developer upgrade         |
| Camera visible but grasp misses   | Check depth/registration, current arm pose, hand-eye offset, target height and gripper alignment                   |
| Import/package missing            | Distinguish ROS 1 `hiwonder_*`/devel from ROS 2 `ros2_ws/install`; source the matching environment                 |
| App lost after development        | End standalone owners and restore the image's documented startup service                                           |

**Can an Ultimate image be used unchanged?** Not without checking scanner and kit configuration. The assigned Developer has A1, while Ultimate has G4.

**How do I recover?** Back up maps, calibration, robot configuration, network and voice settings. Restore the exact Orin Nano SUPER image from the official resources only after identifying the target SSD/card. Restore lower-controller firmware separately if it was altered. Full board input capability does not establish safe assembled-robot voltage.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                          | Official destination                                                                                                   |
| --------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Full manual and RRC protocol      | [Quick-start/manual](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html)    |
| Images, source and hardware files | [JetRover Resources](https://drive.google.com/drive/folders/1vr9opcQeVnQY6R7BgDco-8LP2xWboiwR?usp=sharing)             |
| Firmware download tools           | [Official tool folder](https://drive.google.com/drive/folders/1RzDiZqcR_29F8EAGOym4mc0ZHRiTKtKU?usp=sharing)           |
| Image writer                      | [Official image-writing tool](https://drive.google.com/drive/folders/1k4gIGDWEmgu7HhTDvxbNj5_nOkqB-_tN?usp=sharing)    |
| Remote access                     | [NoMachine/MobaXterm](https://drive.google.com/drive/folders/198a6cQdzJ2gbj5ZP0_yByOO8D1fSK4gt?usp=sharing)            |
| Simulation VM                     | [Official VM resources](https://drive.google.com/drive/folders/18tzfLt9Dtzy2C_jYPdtwrijrjSwNjLc-?usp=sharing)          |
| Voice                             | [Voice recognition materials](https://drive.google.com/drive/folders/1ulzsl1SCcD38hx4lNaDriItl90PRpeRo?usp=sharing)    |
| Mapping files                     | [Make a Map & Map\_nav](https://drive.google.com/drive/folders/14qPgstAi2agv1oakEjxmZ-YGKj8C8FNB?usp=sharing)          |
| All download entries              | [Current resource index](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/resources_download.html) |

Some navigation/sidebar links omit `docs/` and return404; the linked article paths above were actually retrieved. Individual image/firmware/CAD archive releases were not exhaustively inspected, so no unverified checksum or mechanical revision is asserted.

### Additional established resources

These established links supplement the model-specific resources above. Retain the matching model, host and revision when selecting a download.

* [manufacturer product data](https://www.hiwonder.com/products/jetrover)

## JetRover Orin engineering reference <a href="#jetrover-full-reference" id="jetrover-full-reference"></a>

This reference applies to **SKU `Hiwonder-21030861`: Developer Kit / Jetson Orin Nano SUPER 8 GB / Mecanum chassis**. Its catalogued equipment includes the arm, Dabai depth-camera configuration, **A1 LiDAR**, display and a six-microphone expansion pack requiring installation. G4, Ackermann and tracked configurations are different options. Course descriptions of them are retained as comparisons, not as an instruction to change the ordered robot's hardware. [Exact option](https://openelab.io/products/hiwonder-jetrover-ai-car?variant=46077641294022), [official Orin quick-start](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html).

The public course branch is `jetson-orin-nano`; its articles contain both current ROS 2 and older ROS 1 material. The reference below names the lane for each workflow and calls out source inconsistencies rather than silently combining them. Article content was reviewed on 24 November 2026. No physical robot or installed image was exercised.

## Image, configuration and network reference <a href="#jetrover-reference-host" id="jetrover-reference-host"></a>

### Separate Orin, legacy Nano and workstation lanes <a href="#jetrover-reference-lanes" id="jetrover-reference-lanes"></a>

| Lane                    | Recognizing it                                                                                        | Use                                                                                       |
| ----------------------- | ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| Assigned Orin Nano      | Ubuntu 22.04/ROS 2 Humble course lane; `~/ros2_ws`, `install`, ROS 2 message/service syntax           | Physical Developer Mecanum robot                                                          |
| Older Jetson Nano ROS 1 | `hiwonder_*` packages, `roslaunch`, catkin `devel`; source text alternates `JetRover_ws` and `ros_ws` | Only its matched older host/image; not the assigned Orin environment                      |
| Older Nano Docker ROS 2 | Separate container with `ros2_ws`, possible `noetic_ws` bridge and shared directory                   | Container-specific setup; those directories do not prove native Orin requires that bridge |
| Simulation VM           | Supplied workstation Ubuntu/ROS image, virtual hardware and ROS packages                              | URDF, Gazebo and MoveIt work without a live serial bridge                                 |
| Voice-programming VM    | Microphone-array workspace and architecture-specific libraries                                        | Provisioning/test environment; x64 libraries must not be copied blindly into AArch64 Orin |

Use the official repository's **`Jetson_Orin_ros2`** branch for source inspection. The reviewed commit is `ef9653885a19a667d0b1642ce67255c555823482`. Its README's generic tracked-robot description is not evidence that this ordered Mecanum kit is tracked. Record the installed image and package paths before replacing anything. [Pinned Orin source](https://github.com/Hiwonder/JetRover/tree/ef9653885a19a667d0b1642ce67255c555823482), [software layout and lane notes](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html#_1-10-3-system-software-framework).

```bash
cat /etc/os-release
uname -m
printenv ROS_VERSION ROS_DISTRO ROS_DOMAIN_ID MACHINE_TYPE need_compile HOST MASTER
ros2 pkg prefix controller
ros2 pkg prefix peripherals
ros2 topic list -t
ros2 node list
```

**Expected result:** the intended ROS 2 graph and installed package directories on an AArch64 host. A missing package or mixed `devel`/`install` overlay should be resolved before launching a control node. The source separates `app`, `example`, `interfaces`, `driver`, `peripherals`, `calibration`, `slam`, `navigation`, `xf_mic_asr_offline` and `simulations`; those directories are not interchangeable firmware images.

### Configure the actual hardware, then establish one command owner <a href="#jetrover-reference-configuration" id="jetrover-reference-configuration"></a>

The desktop version tool exposes **Depth Camera** (`Dabai`/`usb_cam`), **LiDAR** (`A1/A2/G4/S2L/LD14P`), **Machine** (`JetRover_Mecanum`, `JetRover_Acker`, `JetRover_Tank`) and **ASR language**. A factory-complete kit should already be configured. After image restoration or an actual hardware change, confirm the exact options, then follow **Save → Apply → Quit** and wait for the restart/ready indication. This SKU needs **JetRover\_Mecanum and A1**, not the source's illustrated/default G4. A monocular color picture does not verify a working depth-camera configuration. [Configuration tool](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html#_1-6-7-robot-version-configuration-tool-instruction).

Before any chassis, arm, navigation, following, voice or AI course:

1. Park on a clear level floor, remove carried objects and leave the full arm/display/antenna swept volume clear. Keep physical stop/power control accessible.
2. End the previous autonomous task and confirm actual rest. Stop phone/gamepad command owners and `start_app_node.service` before starting an independent lesson.
3. Inspect the command topic and its publishers. Select one motion controller, one serial owner and one camera owner for the experiment. Avoid simultaneous phone, navigation, tracking and model-tool dispatch.
4. Treat initialization and `debug:=true` as potentially moving operations. Arm debug code can run `pick_debug` and `pick_init` action groups automatically.
5. Stop the behavior explicitly and verify the physical robot is stationary before process exit or restoring the app service.

```bash
sudo systemctl stop start_app_node.service
ros2 topic info /controller/cmd_vel --verbose
# Restore only after standalone action/driver owners have stopped:
sudo systemctl restart start_app_node.service
```

The controller subscribes to Twist commands. Closing a publisher terminal can leave the last command active; the motion FAQ itself warns about this. A normal zero request, after resolving competing owners, uses valid ROS 2 YAML:

```bash
ros2 topic pub --once /controller/cmd_vel geometry_msgs/msg/Twist \
  '{linear: {x: 0.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.0}}'
```

Verify that the robot stops. This is not a safety-rated stop and cannot overcome a second active publisher, a failed controller or disconnected transport. The course's ROS 1 `/hiwonder_controller/cmd_vel` FAQ fragment is not the correct ROS 2 remedy. [Motion ownership, command interface and FAQ](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/2.Motion_Control_Course.html#_2-7-robot-speed-control).

### Access, power and recovery checkpoints <a href="#jetrover-reference-network-recovery" id="jetrover-reference-network-recovery"></a>

The default hotspot starts with `HW`, uses password `hiwonder`, and provides the robot desktop at `192.168.149.1`. The assigned Orin account is `ubuntu`/`ubuntu`; older Nano credentials belong to a different lane. Wait for the ready beep rather than assuming a flashing network LED means ROS bringup has finished. For the app choose the Mecanum model; on a LAN use the assigned reachable address, not the AP address. A hotspot with no internet is normal; cloud AI still needs a separate working internet route.

Keep the display's video and touch/data paths separate when troubleshooting. A working DP picture does not establish touch operation. Use the actual Orin wiring figure and factory harness. The robot pack is 11.1 V/6000 mAh with a matched 12.6 V charger; charge only while switched off. The manual warns against connecting that charger to the Jetson DC input and reports a low-battery alarm below 10 V. The lower STM32 board's 9–24 V capability does not approve that full range for the assembled robot. The manual distinguishes the **Orin 12 V host path** from older Nano/Pi 5 V wiring. [Power, wiring and startup](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html).

Before image replacement, save maps/YAML, calibration, machine/scanner/camera selections, arm deviations and action files, network settings and the matched speech-resource/APPID configuration. Shut down and disconnect power, identify the actual boot SSD/card, and obtain the exact Orin Nano image. In the manufacturer's Windows writer workflow, select the extracted image and the correct physical target, write and wait for completion. Verify the drive identity before any formatting or erasure. After writing, cancel operating-system prompts to format Linux partitions. Reinsert the medium with power off, boot, recheck the version tool and perform passive feedback checks before driving. An image write and an STM32 firmware write are separate recoveries; neither repairs a reversed or incorrectly routed power connection. [Image-writing course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html#_1-12-system-image-flashing).

## STM32 responsibilities, RRC protocol and SDK <a href="#jetrover-reference-mcu" id="jetrover-reference-mcu"></a>

### Lower-controller execution and firmware scope <a href="#jetrover-reference-stm32" id="jetrover-reference-stm32"></a>

The STM32/FreeRTOS layer handles motor speed PID, encoder/IMU acquisition, peripheral control and host communication. Encoder feedback closes the motor speed loop; the host computes body/wheel commands using the selected chassis model. Mecanum needs four drive motors; the alternate tank/Ackermann examples use a different drive/steering arrangement. The course's sentence calling tracked drive omnidirectional is incorrect: a conventional tracked chassis does not have independent lateral translation. [MCU control process and kinematic scope](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html#_1-11-stm32-source-code-development).

The documented MCU development tool is Keil 5. Select the matched project/processor, enable the required output file, build and inspect both errors and warnings. A warning can expose a real size/type/initialization problem; do not ignore all warnings merely because the source says they may be ignored. Save the original binary and configuration before altering a factory controller.

The USB ISP example uses **ATK-XISP at 115200 baud** and a board-specific HEX file; it illustrates run-after-programming, verify and a full-chip erase option. Full-chip erase can destroy existing controller state. Do not enable it or use a screenshot's COM port as a discovery test. The older manual names `RRC_20240702.hex`; that filename is a documented historical example, not a requirement to downgrade the supplied board. Confirm exact board/bootloader/firmware compatibility, the physical serial port and a recovery path before programming. SWD is a separate low-level debug path requiring the correct board pinout and logic reference. [MCU build/download procedure](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html#_1-11-6-project-compilation).

### Runtime frame format and function map <a href="#jetrover-reference-rrc-frame" id="jetrover-reference-rrc-frame"></a>

The pinned **JetRover Orin SDK** opens `/dev/rrc` at **1,000,000 baud**. That is runtime controller transport, not the 115200-baud ISP writer and not the servo UART. Its actual transmitter/receiver agree on:

| Bytes             | Meaning                                                  |
| ----------------- | -------------------------------------------------------- |
| `AA 55`           | Header                                                   |
| One unsigned byte | Function                                                 |
| One unsigned byte | Payload length only                                      |
| Length bytes      | Function-specific payload                                |
| One byte          | CRC-8 over function, length and payload; header excluded |

Its CRC table is equivalent to a reflected polynomial-`0x8C` loop starting at zero. An older SDK comment lists a different order; follow the implementation, not that comment. The quick-start's little-endian note also confuses a 32-bit description with a two-byte example. Decode each actual declared type/width explicitly. [Pinned SDK implementation](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/ros_robot_controller/ros_robot_controller/ros_robot_controller_sdk.py), [manual transport examples](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/1.Quick_Start_Guide.html#_1-10-2-ros-serial-port-communication).

| Function | Controller family | Encoding/API observations                                                                                                                |
| -------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------- |
| `00`     | System            | Battery report subcommand `04` + raw LE `u16`; SDK comment “mAh” is not a voltage unit                                                   |
| `01`     | LED               | ID `u8`, on/off times `u16` milliseconds, repeats `u16`                                                                                  |
| `02`     | Buzzer            | Frequency and on/off/repeat fields packed as LE `u16`                                                                                    |
| `03`     | Motor             | Speed subcommand `01`, count, repeated zero-based motor index + LE float rps; SDK input IDs are one-based                                |
| `04`     | PWM servo         | JetRover position subcommand `01`, duration `u16`, count and repeated ID/position pairs; this differs from the newer ROSOrin SDK packing |
| `05`     | Bus servo         | Addressed position, stop, ID, offset, limits and status/readback                                                                         |
| `06`     | Buttons           | ID and event code; click/long-press/release are distinct                                                                                 |
| `07`     | IMU               | Six LE floats: ax, ay, az, gx, gy, gz; apply the matched ROS conversion for physical units                                               |
| `08`     | Gamepad           | Button mask, hat and signed axes before SDK normalization                                                                                |
| `09`     | SBUS              | Sixteen signed channels plus channel-17/18, signal-loss and failsafe flags                                                               |
| `0A`     | OLED              | Line/text-length/text bytes; inspect UTF-8 length handling for non-ASCII strings                                                         |

Motor rps is not chassis m/s. In particular, passing `0.1` from a Twist directly as `set_motor_speed` produces a different physical quantity. The SDK creates its serial port and receive thread, so even constructing a `Board` object is not an offline parser operation. Keep the installed ROS hardware node as the sole serial owner during normal development.

**Python SDK inputs are not raw wire units.** In the pinned JetRover SDK, the public methods below convert seconds to integer milliseconds before transmission:

| Python method                                    | Caller supplies                                        | Packing performed by this SDK                                                                    |
| ------------------------------------------------ | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| `set_led(on_time, off_time, repeat=1, led_id=1)` | On/off **seconds**, repeat count and LED ID            | `int(time*1000)`; ID `u8`, two LE `u16` millisecond fields, repeat `u16`                         |
| `set_buzzer(freq, on_time, off_time, repeat=1)`  | Frequency Hz, on/off **seconds**, repeat count         | Frequency and converted millisecond/count fields as LE `u16`                                     |
| `set_motor_speed(speeds)`                        | Pairs of **one-based motor ID and revolutions/second** | Subcommand/count; ID minus one as `u8`, speed as LE float                                        |
| `pwm_servo_set_position(duration, positions)`    | Duration **seconds**; ID/raw-position pairs            | `int(duration*1000)` split into two millisecond bytes, then count and ID/LE `u16` position pairs |
| `bus_servo_set_position(duration, positions)`    | Duration **seconds**; ID/raw-position pairs            | Same duration conversion and pair packing, inside function `05`                                  |

Thus a requested 100 ms interval is **0.1 seconds** at these Python interfaces, not `100`. A raw frame's `100` millisecond field is a different representation. The two servo methods mask duration into its low 16 bits; they do not enforce a physically suitable duration. Validate finite, nonnegative inputs and representable integer milliseconds before packing; 65535 ms is a field-capacity boundary, not an approved motion time. LED/buzzer packing can instead reject an out-of-range unsigned value. These SDK facts alone do **not** establish the units or validation of every ROS message named `duration`: trace the installed message and its callback separately. [Pinned SDK methods and conversion](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/ros_robot_controller/ros_robot_controller/ros_robot_controller_sdk.py).

### Bus-servo commands and typed replies <a href="#jetrover-reference-servo-protocol" id="jetrover-reference-servo-protocol"></a>

Within function `05`, the reviewed SDK uses this map:

| Operation                                   | Subcommand / payload after it                                                                                      |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Set positions                               | `01`, duration LE `u16` ms, count, then ID `u8` + position LE `u16` pairs                                          |
| Stop selected servos                        | `03`, count, IDs                                                                                                   |
| Read position / input voltage / temperature | `05` / `07` / `09`, servo ID                                                                                       |
| Read torque state                           | `0D`, servo ID                                                                                                     |
| Torque setting                              | SDK true selects `0B`, false `0C`, followed by ID; verify the installed controller/servo behavior before unloading |
| Set/read ID                                 | `10` old ID/new ID; `12` ID                                                                                        |
| Set/read/save offset                        | `20` ID + signed offset; `22` ID; `24` ID                                                                          |
| Set/read angle limits                       | `30` ID + two LE `u16`; `32` ID                                                                                    |
| Set/read voltage limits                     | `34` ID + two LE `u16`; `36` ID                                                                                    |
| Set/read temperature limit                  | `38` ID + signed byte; `3A` ID                                                                                     |

A typed read reply contains ID, subcommand, signed status and result. For position the format is ID `u8`, subcommand `u8`, status `i8`, position LE `i16`; voltage uses `u16`, temperature `u8`. Zero status succeeds; −1 fails. Validate the ID/subcommand, payload length and CRC before using a result. A CRC-valid failure packet must not become a valid negative position. The manual's example `05 05 00 41 03` is raw position **833** for servo 5; its “30°” wording does not establish a universal servo-angle conversion.

Do not broadcast ID changes to an assembled chain. Save offsets only after mechanical verification and retain a backup; they persist beyond a transient position command. The SDK's servo read helper blocks on a receive queue, so add an application-level deadline and keep it out of time-critical callbacks. [Exact JetRover bus-servo source](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/ros_robot_controller/ros_robot_controller/ros_robot_controller_sdk.py).

### ROS interfaces and solver requests <a href="#jetrover-reference-ros-api" id="jetrover-reference-ros-api"></a>

The following contract is from **JetRover commit `ef9653885a19a667d0b1642ce67255c555823482`**, not the ROSOrin or ROSpider controller. Names without a leading slash are the source's relative names; resolve namespaces/remappings in the installed graph.

| Interface                         | Direction/type                                           | Units and actual pinned behavior                                                                                                                       |
| --------------------------------- | -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `cmd_vel`                         | Input, `geometry_msgs/msg/Twist`, `app_cmd_vel_callback` | Clamps linear x/y independently to **±0.2 m/s** and angular z to **±0.5 rad/s**, then calls the direct callback                                        |
| `controller/cmd_vel`              | Input, `Twist`, `cmd_vel_callback`                       | Linear x/y m/s, angular z rad/s; **bypasses those particular app clamps**. This does not prove the absence of every lower-layer limit.                 |
| `ros_robot_controller/set_motor`  | Output, `ros_robot_controller_msgs/msg/MotorsState`      | Per-motor ID and **rps**, after chassis kinematics and mounting sign conversion                                                                        |
| `odom_raw`                        | Output, `nav_msgs/msg/Odometry`                          | Pose in meters/radians, twist in m/s and rad/s; integrates stored **commanded** velocity in this implementation, not measured encoder speed            |
| `set_odom` / `set_pose`           | Input `Pose2D` / output `PoseWithCovarianceStamped`      | Reference-setting path; it is not evidence of an external position measurement                                                                         |
| `controller/load_calibrate_param` | Service, `std_srvs/srv/Trigger`                          | Attempts to reload correction factors; verify the actual parameter names and logged/read-back factors before treating a call as successful calibration |

The app clamps are per component, not a proven vector-speed or stopping envelope. Publishers to `/controller/cmd_vel`, including the voice/model examples below, do not pass through `app_cmd_vel_callback`. `/imu` is `sensor_msgs/msg/Imu`; fused odometry and its sensor inputs are a separate estimator contract. Topic direction must follow `create_subscription`/`create_publisher` and the live graph, because several course paragraphs label both as “publishing.” [Pinned controller inputs, outputs and callbacks](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/controller/controller/odom_publisher_node.py).

For the arm, the `kinematics` node provides `set_pose_target` (`kinematics_msgs/srv/SetRobotPose`), current pose, FK, link and joint-range services. A pose request uses a position array in **meters**, pitch and pitch search range in **degrees**, and a search resolution in degrees. The reply contains success, target/current pulse arrays, RPY and a minimum-variation measure. The helper `kinematics_control.set_pose_target` only builds a request; it does not send it or actuate a joint. `SetJointValue` takes five joint values in the documented pulse/controller scale and returns an FK pose/solution flag.

**`success` is not an IK-solution validity flag here.** The pinned `set_pose_target` returns `[True, [], [], [], 0.0]` when it has no IK solutions or no current servo state, and its service callback sets `success=True` unconditionally. Require nonempty target/current arrays of the expected **five pose joints**, matching ID/order and fresh state; validate array shapes, finite values, RPY, joint/mechanical limits and the planned scene/path before any separate actuation. The wrapper clamps candidate pulses to 0–1000; that clamp does not certify collision clearance or the achieved Cartesian pose. `min_variation` ranks pulse changes, not collision-free trajectories. For FK and current-pose replies, inspect the separate **`solution`** flag as well as `success` and finite pose data: the wrapper can return `success=True, solution=False` with a default pose. Do not use that default as a measured endpoint. [Pinned IK/FK reply implementation](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/kinematics/kinematics/search_kinematics_solutions_node.py).

Keep the two position-message families separate: lower-controller `ros_robot_controller_msgs/ServosPosition` contains duration and positions; higher-level `servo_controller_msgs/ServosPosition` additionally carries `position_unit`. Inspect the installed interface, callback and accepted unit string before commanding it. Solver `.so` binaries remain opaque: readable wrappers and service definitions do not establish their internal correctness or installed ABI. [Pinned IK helper](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/kinematics/kinematics/kinematics_control.py), [service definitions](https://github.com/Hiwonder/JetRover/tree/ef9653885a19a667d0b1642ce67255c555823482/src/driver/kinematics_msgs/srv).

Five pose-joint values and a separate gripper are exposed by this interface. The course's “6DOF” label does not establish six independently controllable Cartesian pose coordinates or compatibility with a generic six-joint industrial-arm solver.

## Chassis models and measured calibration <a href="#jetrover-reference-motion" id="jetrover-reference-motion"></a>

### Mecanum, Ackermann and tank are different kinematics <a href="#jetrover-reference-kinematics" id="jetrover-reference-kinematics"></a>

The assigned Mecanum model can command x/y translation and yaw independently. In the course's top-view numbering, motors 1/2 are left front/rear and 3/4 right front/rear. With `k=(wheelbase+track_width)/2`, the wheel linear-speed combination is `x−y−kω`, `x+y−kω`, `x+y+kω`, `x−y+kω`; divide by wheel circumference for rps, then reverse right-side motor signs for mounting. Confirm the physical wiring and rollers before changing those signs.

The Mecanum class defaults are **0.216 m wheelbase, 0.195 m track and 0.097 m diameter**. The pinned controller separately assigns Python constants `wheel_diameter_mecanum=0.097` and `wheel_diameter_tank=0.052` and passes dimensions to its constructors; these are **not declared runtime ROS wheel-diameter parameters** in that node. Its Ackermann constructor is also explicitly passed 0.216/0.195/0.097 m, so the course's alternate class defaults of 0.213/0.222/0.101 m do not describe that instantiated object. Measure the received geometry and inspect the installed implementation before modifying either. The pinned controller reads `MACHINE_TYPE` from the environment for its branch; a similarly named declared ROS parameter alone does not prove a branch change. Ackermann uses a steering servo and cannot perform arbitrary Mecanum strafing or normal in-place yaw at zero forward speed. A tracked model turns through left/right speed difference and slip; it cannot strafe. The `linear_correction_factor_tank=0.52` illustration is not the Mecanum calibration factor. [Pinned constructor and branch selection](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/controller/controller/odom_publisher_node.py), [Mecanum class](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/controller/controller/mecanum.py), [course kinematics](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/2.Motion_Control_Course.html).

Physical conversion requires the relevant chassis hardware, routing, motor/steering connections and machine configuration. Keep power disconnected during mechanical work. After an actual conversion, repeat wheel-direction, sensor-pose, clearance and calibration checks; changing `MACHINE_TYPE` alone does not turn one chassis into another. For this ordered kit, keep the Mecanum lane unless a separately verified conversion is intended.

### IMU bias, linear scale and angular scale <a href="#jetrover-reference-calibration" id="jetrover-reference-calibration"></a>

Preserve the factory calibration unless measurements show a repeatable error. Back up `calibration/config/imu_calib.yaml` and `driver/controller/config/calibrate_params.yaml`. The documented six-orientation IMU calibration starts `ros_robot_controller ros_robot_controller.launch.py` and `imu_calib do_calib`, remapping `imu` to `/ros_robot_controller/imu_raw` and writing the output file. Stabilize the supported robot in each indicated ±X/±Y/±Z pose before recording; protect the arm/display while changing orientation. Inspect the result with `peripherals imu_view.launch.py` and compare physical/display tilt directions.

The angular test is a marked **360°** turn using `calibration angular_calib.launch.py`; the linear test is **1 m** using `linear_calib.launch.py`, with illustrated linear speed 0.2 m/s. The angular GUI calls its example speed “0.15 m/s”; do not silently interpret that inconsistent label as a verified angular unit. Read the installed parameter declaration. Set the applicable factor to 1.0 before a fresh test, measure physical travel and adjust in small 0.01 steps as the course describes, then save/reload the actual controller's `linear_correction_factor` and `angular_correction_factor`. The text misspells the latter in places; use the installed YAML key.

The source's linear-calibration introduction accidentally discusses angular calibration and Ackermann. It does not exempt this Mecanum robot from a measured straight-line test. Verify motor/encoder sign, wheel slip and machine selection before tuning factors. A 1 m straight result does not establish strafe scale or yaw accuracy; measure those separately. [Calibration sections](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/2.Motion_Control_Course.html#_2-5-imu-linear-velocity-and-angular-velocity-calibration).

In the pinned node, `linear_factor` scales published odometry x/y and `angular_factor` scales integrated yaw. Multiplications of incoming command velocity by those factors are **commented out**; they do not rescale the outgoing motor demands in this path. The reload handler looks up `~linear_correction_factor`/`~angular_correction_factor`, while initialization declares the names without `~`. Verify the delivered node's parameter lookup and observed factors; the existence of a Trigger service is not proof that the saved factors loaded. Keep measured physical distance/heading, commanded motion and reported pose as three separate observations. [Actual correction/reload implementation](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/controller/controller/odom_publisher_node.py).

### Feedback and conservative first motion <a href="#jetrover-reference-feedback" id="jetrover-reference-feedback"></a>

The course starts `peripherals imu_filter.launch.py` for filtered IMU and `controller odom_publisher.launch.py` for raw odometry, with the lower controller available. `controller controller.launch.py` can include those components and the EKF; avoid duplicate bringup. **This pinned `/odom_raw` path is commanded-motion dead reckoning.** `cmd_vel_callback` stores the requested linear/angular velocity; `cal_odom_fun` integrates those stored values with elapsed time and publishes pose/twist. It does not obtain encoder-derived wheel velocity for that calculation. A commanded but physically stalled robot can therefore advance its raw pose; a lifted-wheel/slip test cannot turn this into a measured-travel result. A command left stored can also continue the integration until changed—do not infer a freshness watchdog from this loop.

The MCU's encoder/PID speed loop is a separate feedback path. Fused odometry or external map localization must be assessed from their actual inputs and implementation, not inferred from this host topic's name or covariance. Inspect the installed image before describing a different version as measured wheel odometry. For a first diagnostic record, compare command, raw pose, timestamp/frame, physical travel and independent IMU/scan evidence. The pinned node's own TF broadcaster calls are commented out; publishing `Odometry` alone does not establish an `odom → base` TF publisher. Fusion can improve an estimate when it has valid independent inputs; it does not manufacture an external absolute reference. [Pinned raw-odometry calculation and disabled broadcaster](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/driver/controller/controller/odom_publisher_node.py).

Use a clear floor and slight gamepad deflection for the first measured forward, lateral and yaw checks. Establish release/START stopping before increasing speed. The course's 0.3 m/s example and ±0.6 m/s suggestion are examples, not a required initial setting or a guarantee for every load. A source description calls an x-only command “diagonal”; with y=0 it is forward motion. If the observed direction disagrees, stop and inspect configuration rather than adding a compensating navigation offset.

## A1 LiDAR and reactive control <a href="#jetrover-reference-lidar" id="jetrover-reference-lidar"></a>

The LiDAR lesson says an image may default to G4; this Developer SKU supplies **A1**. Confirm the label and version-tool selection before interpreting a serial device failure. First inspect LaserScan on a stationary robot in RViz, including frame, angular increment, timestamp and valid ranges. A1 rotation and USB enumeration do not prove a correctly decoded scan. Test a cardboard target at known positions without enabling following.

After stopping the app owner, the documented launch is `app lidar_node.launch.py debug:=true`. The article alternates `/lidar_app/enter` and `/lidar_controller/enter`, while its behavior selection uses `/lidar_controller/set_running`. This is an actual source namespace inconsistency. Use `ros2 service list -t` and `ros2 service type` to identify the installed service; do not blindly call both enter services or substitute a Pro namespace.

| Behavior  | `SetInt64` selector in the course | What can move                                                                      |
| --------- | --------------------------------- | ---------------------------------------------------------------------------------- |
| Stop      | `data: 0`                         | Ends the selected behavior; verify actual rest                                     |
| Avoidance | `data: 1`                         | Forward drive and obstacle-avoidance turns                                         |
| Following | `data: 2`                         | Approach/retreat/turn to follow the forward target; illustrated stand-off is 35 cm |
| Guarding  | `data: 3`                         | Rotation to face a nearby target; course excludes Ackermann guarding               |

The enter type is `std_srvs/srv/Trigger`, and selection is `interfaces/srv/SetInt64`. Establish stop first, then one mode in an open scene, with no navigation/teleoperation publisher active. The 35 cm following target is a demonstration reference, not a complete braking/clearance specification. Missing returns and blind sectors are not certified free space. [Exact LiDAR course and namespace examples](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/3.Lidar_Course.html).

## Camera, URDF and navigation <a href="#jetrover-reference-navigation" id="jetrover-reference-navigation"></a>

### Dabai data and coordinate checks <a href="#jetrover-reference-depth" id="jetrover-reference-depth"></a>

The assigned robot uses the course's **Dabai** depth-camera lane. A ROSOrin Aurora driver or its USB/profile table is not a substitute. Start `peripherals depth_camera.launch.py` only after other camera owners stop. `usb_cam.launch.py` is the distinct monocular path. View color, depth, CameraInfo and point cloud separately; verify stream encoding, scale, registration and timestamps before computing distances.

For valid registered data, camera projection uses `X=(u−cx)Z/fx`, `Y=(v−cy)Z/fy`. Convert depth to meters according to the actual encoding/driver. RGB-to-depth registration and camera-to-arm calibration are different transforms. Moving the arm changes the camera pose, so use current endpoint/joint state and timestamps. A plausible image center with invalid depth is not a valid 3D target. The arm course's generic camera table and fixed transforms describe examples, not a new calibration for the actual mounted camera. [3D course data flow](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-3d-vision-vision-application).

URDF/Xacro separates meshes, collision shapes, inertias and joint/frame relationships. The JetRover model includes chassis, A1/G4 alternatives, IMU, depth camera, arm, gripper and transmissions. Select the Mecanum/A1 version and verify the camera/scanner poses; a visual mesh alone does not establish collision clearance. For rotary joints, effort is N·m and velocity rad/s; linear joint limits use meters, N and m/s. Some source tables incorrectly generalize linear units to every joint. [Model files and frame explanations](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/4.Mapping_Navigation_Course.html#_4-1-mapping).

### 2D SLAM, save/reload and initial pose <a href="#jetrover-reference-slam2d" id="jetrover-reference-slam2d"></a>

1. Confirm scanner, wheel/IMU direction, robot model and battery. Stop competing command owners and clear the route.
2. Launch `slam slam.launch.py`, `slam rviz_slam.launch.py` and the chosen manual controller in separate terminals. The course uses `peripherals teleop_key_control.launch.py`; W/S can latch continuing motion, so establish stop behavior first.
3. Map a small loop, revisit features and inspect wall overlap/pose jumps. Distinguish slipped wheels or a bad scanner transform from a SLAM parameter issue.
4. Save a new name in the configured map directory. Inspect the YAML/image pair and reopen the result before navigation.
5. Stop manual motion, then shut mapping down cleanly.

```bash
cd ~/ros2_ws/src/slam/maps
ros2 run nav2_map_server map_saver_cli -f jetrover_room \
  --ros-args -p map_subscribe_transient_local:=true
```

**Expected result:** a coherent occupancy grid plus `jetrover_room.yaml` and its referenced image. Resolution, origin and image path must remain together; an image copied without its YAML can silently change map interpretation. Do not overwrite a trusted map with a failed test. The quick desktop mapping path and its default names are separate from a deliberately versioned map. [SLAM operations](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/4.Mapping_Navigation_Course.html#_4-1-4-slam-toolbox-mapping-algorithm).

For navigation, use `navigation navigation.launch.py map:=jetrover_room` with `navigation rviz_navigation.launch.py`. Set the actual initial pose using **2D Pose Estimate**, align scan and map walls, then choose one nearby reachable goal. AMCL's pose particles, global occupancy map and rolling costmaps have different roles; a drawn global path does not verify local obstacle clearance. The arm/display must fit through the passage, not merely the base rectangle.

**Localization pipeline.** AMCL localizes against an existing occupancy map; it does not create that map. Each particle is a possible robot pose. Odometry predicts the particle motion, the measured scan is compared with the map to update weights, and resampling favors better-supported hypotheses. Adaptive/KLD sampling changes the required particle population as uncertainty changes; it is not an unconditional accuracy gain. Set the initial pose and orientation, then inspect scan/map alignment and particle convergence before sending a goal. A particle cloud that spreads or jumps calls for map identity, scan timing, odometry and sensor-transform checks before increasing planner speed. In particular, the commanded-motion `/odom_raw` described above can disagree with real travel under a stall. [AMCL stages and initial pose](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/4.Mapping_Navigation_Course.html#_4-2-2-amcl-adaptive-monte-carlo-positioning).

The course separates global `map → odom` correction, continuous local `odom → base_footprint` motion and fixed base-to-sensor transforms from the robot description. The installed estimator/TF publishers must actually provide this chain; the pinned raw publisher alone does not broadcast it. A correct range in a scanner frame becomes a useful obstacle only after the scanner-to-base transform and timestamp are right. Give each dynamic transform one owner. A duplicated `map → odom` publisher or an incorrect sensor pose can look like a localization/planning defect.

| Costmap stage discussed by the course | Input and operational role                                              | Useful observation                                                                         |
| ------------------------------------- | ----------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Static layer                          | Saved occupancy map establishes persistent walls/free/unknown regions   | Correct image, YAML origin/resolution and map frame; unknown is not automatically clear    |
| Obstacle layer                        | Current range observations mark obstacles and clear along observed rays | A moved test prop appears/disappears consistently; stale scans must not clear unseen space |
| Voxel layer                           | Height-aware 3D observations contribute marking/clearing                | Correct sensor height/frame and supported height range; a floor return is not a wall       |
| Inflation layer                       | Expands obstacle cost around occupied cells                             | Footprint and clearance account for arm/display/carried object, not only bare-base width   |

These are the roles of the layered-costmap material, not a claim that every layer is enabled in this image. The global route supplies a map-scale reference. The local planner/controller uses current pose/velocity, nearby obstacle costs, footprint and motion limits to produce a short-horizon velocity command. **DWA** samples feasible linear/angular velocities, simulates short trajectories, rejects collisions and scores remaining candidates. **TEB** adjusts a sequence of poses and time intervals under obstacle, smoothness and kinematic/dynamic constraints. A global path with no executable local trajectory often points to footprint/inflation, stale transforms, local obstacles or inconsistent motion limits rather than a missing map. [Costmaps and global/local roles](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/4.Mapping_Navigation_Course.html#_4-2-2-amcl-adaptive-monte-carlo-positioning), [DWA and TEB](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/4.Mapping_Navigation_Course.html#_4-2-3-local-path-planning).

The course exposes map, namespace/master/robot and planner options through its wrappers and loads `navigation/config/nav2_params.yaml`. Its algorithm discussion also names historical ROS 1 `move_base`, `costmap_2d` and planner interfaces. Inspect the installed `--show-args`, Nav2 plugin configuration, subscribed inputs and command topic before changing `use_teb` or copying a ROS 1 parameter. A conceptual algorithm description does not select an installed binary. In the waypoint panel, **Start Nav Through Poses** and **Start Waypoint Following** are different actions; inspect their goal/heading behavior in the installed interface. Cancel navigation before transferring command ownership. [Navigation and waypoint course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/4.Mapping_Navigation_Course.html#_4-2-navigation).

### RTAB-Map 3D mapping and navigation <a href="#jetrover-reference-rtab" id="jetrover-reference-rtab"></a>

The RGB-D path uses `slam rtabmap_slam.launch.py` with `rviz_rtabmap.launch.py`, and later `navigation rtabmap_navigation.launch.py` with `rviz_rtabmap_navigation.launch.py`. Check RGB/depth synchronization, calibration, odometry and TF before evaluating mapping. A stationary blank wall or repeated texture can be a poor visual reference even when a depth image is present.

Preserve the database generated on clean shutdown and the matching configuration. A 2D occupancy image alone does not contain the RGB-D graph/database. Do not let both an AMCL stack and a second RGB-D localization stack own the same map-to-odom transform. Prove a short mapped return path before adding arm transport or language-selected destinations. [RTAB mapping/navigation sections](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/4.Mapping_Navigation_Course.html).

## OpenCV color, QR and line-following courses <a href="#jetrover-reference-opencv" id="jetrover-reference-opencv"></a>

### LAB calibration and stationary recognition <a href="#jetrover-reference-lab" id="jetrover-reference-lab"></a>

Stop the app owner, start the actual camera wrapper and open `python3 /home/ubuntu/software/lab_tool/main.py`. The three LAB channels use **0–255** values in the course's range table. One instruction instead says to initialize maxima to 225; that is not the full channel range. Use the displayed mask and saved values rather than treating 225 as an encoding limit.

Select the target color, begin with broad thresholds and narrow the relevant chromatic channel until the target is white and unrelated regions black. Adjust brightness and the remaining channel under the actual lighting. Check multiple positions along the planned route, shadowed regions and same-colored backgrounds before saving. Add a new named color through the tool, save it and then confirm that the intended behavior accepts that name. A saved threshold does not automatically add a new detector class or a new sorting action.

The stationary color demo is `~/ros2_ws/src/example/example/color_detect/color_detect_demo.py`. It uses image conversion, thresholding, morphology, contour analysis and a displayed result. Verify the mask and selected contour before using its center/size. A correctly identified center with a wrong physical pick point calls for geometric calibration, not arbitrary threshold changes. [Color calibration and detection](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/5.ROS+OpenCV_Course.html#_5-1-color-threshold-adjustment).

### QR generation/decoding and closed-loop line following <a href="#jetrover-reference-qr-line" id="jetrover-reference-qr-line"></a>

Use `qrcode_creater.py` and `qrcode_detecter.py` under `example/example/qrcode` with a known harmless payload. Compare decoded text exactly and test focus, angle, contrast and the quiet border. The observed filenames contain those spellings. Decoded content is data; do not execute it as a shell command or dispatch it directly as a robot action.

Line following combines a LAB mask, lane ROI, image-center error and motion control. Prepare the course's high-contrast line without competing colored objects. Inspect the debug image and choose the line before enabling travel. The documented ROS 2 interface is:

```bash
ros2 launch app line_following_node.launch.py debug:=true
ros2 service call /line_following/enter std_srvs/srv/Trigger '{}'
# Enable only after the course clearance/ownership checks:
ros2 service call /line_following/set_running std_srvs/srv/SetBool '{data: true}'
```

The closing paragraph repeats an `enter` call rather than a distinct stop. Inspect the installed `set_running` interface, select false where supported, and verify a zero chassis command and physical rest before process exit. An initialization response is not stop feedback. If steering oscillates, separate bad mask/ROI, camera pose, controller gain and wheel calibration instead of changing all four together. [QR and line-following lessons](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/5.ROS+OpenCV_Course.html).

## Machine learning, MediaPipe and staged driving <a href="#jetrover-reference-learning" id="jetrover-reference-learning"></a>

### YOLOv5 and TensorRT belong to the matched image <a href="#jetrover-reference-yolo" id="jetrover-reference-yolo"></a>

The JetRover chapter names **YOLOv5**, introduces learning types and common frameworks, and explains GPU/TensorRT acceleration. This is not the ROSOrin Pro course's newer model-name lane. The practical detector path is `~/ros2_ws/src/example/example/yolov5_detect`; the debugging workflow runs `python3 yolov5_trt.py`. Inspect the actual weight/engine file, custom libraries, class ordering and preprocessing before replacing it. A TensorRT engine from another Jetson/CUDA/TensorRT environment is not automatically portable.

Treat model architecture, exported engine, input resolution, pixel normalization, class list, confidence threshold and postprocessing as one versioned deployment. Test saved images and the live stationary stream before exposing detections to motion. The chapter's description of anchors/prior/predicted boxes is conceptual and does not define a training API. It does not establish that YOLO11 or YOLO26 weights fit the YOLOv5 loader. FP32, FP16 and INT8 have different numerical/optimization behavior; INT8 needs the appropriate calibrated/quantized model path. No measured inference rate or guaranteed memory budget is asserted for the 8 GB host. [Learning/TensorRT chapter](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/6.ROS+Machine_Learning_Course.html#_6-2-machine-learning-application).

For detector debugging, the source points to `conf_thresh`; lower thresholds can increase false triggers as well as recover missed cards. Change one variable at a time and compare a fixed validation set. Preserve the working factory engine/environment before upgrades. A missing CUDA/plugin dependency should be diagnosed from the actual load error rather than repaired by installing unrelated framework versions.

### Image-only and moving human-interaction lessons <a href="#jetrover-reference-mediapipe" id="jetrover-reference-mediapipe"></a>

The image-only scripts are under `example/example/mediapipe_example`. Start the correct depth or monocular camera once, then one experiment. The later body controllers can move the chassis even if their names sound observational.

| Lesson                        | Script/launch from the course            | Useful first result                                                                         |
| ----------------------------- | ---------------------------------------- | ------------------------------------------------------------------------------------------- |
| Background segmentation       | `self_segmentation.py`                   | Stable foreground mask/replaced background under actual lighting                            |
| Objectron                     | `objectron.py`                           | Supported object receives an oriented box; not arbitrary-object metrology                   |
| Face detection                | `face_detect.py`                         | Bounding region follows a face; no identity/authentication implication                      |
| Face mesh                     | `face_mesh.py`                           | Facial landmarks, with expected losses under occlusion                                      |
| Hand keypoints                | `hand.py`                                | Hand landmarks/connections track the visible hand                                           |
| Body keypoints                | `pose.py`                                | Visible body skeleton before any gesture mapping                                            |
| Fingertip trajectory          | `hand_gesture.py`                        | Index-finger trace and open-hand clearing behavior                                          |
| Posture control               | `example body_control.launch.py`         | Recognized pose triggers the configured turn/translation, with clear floor and stop path    |
| Human tracking                | `example body_track.launch.py`           | Body center/depth feeds approach/retreat; course target separation is about 3 m             |
| Body plus clothing color      | `example body_and_rgb_control.launch.py` | Calibrate the intended person before recognizing driving gestures                           |
| Falling-posture demonstration | `example fall_down_detect.launch.py`     | Alarm and programmed robot response; do not treat it as an inert display or medical monitor |

The human-following implementation also uses learned body detection/depth and separate distance/angular PID terms. Landmark display, target association, valid depth and physical motion are different checkpoints. Test lost detection and depth holes while prepared to stop. Increasing PID gain is not an enforced speed cap and can worsen overshoot. Similar clothing, an incomplete body image or outdoor illumination can defeat the staged examples. [Human-interaction lessons](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/6.ROS+Machine_Learning_Course.html#_6-3-mediapipe-man-robot-interaction).

### Driving-scene preparation and decision debugging <a href="#jetrover-reference-driving" id="jetrover-reference-driving"></a>

Use the supplied indoor course props and camera pose, not an uncontrolled public road. First test `example self_driving.launch.py only_line_follow:=true` in a clear staged area. Full `self_driving.launch.py` adds sign/light/turn/parking decisions. The debugging chapter still contains `roslaunch hiwonder_peripherals depth_cam.launch`; that is a ROS 1 fragment. For the assigned lane use the installed ROS 2 camera wrapper instead.

| Course stage      | Data/parameters to examine                                          | Acceptance before adding the next stage                                     |
| ----------------- | ------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Lane keeping      | Yellow LAB mask, ROI and `lane_x` center reference                  | Correct center across different sections of the course, not one tuned patch |
| Sign detection    | YOLOv5 engine/classes and `conf_thresh`                             | Correct card class with acceptable false positives                          |
| Light recognition | Color segmentation and scene placement                              | Stop/proceed decisions agree with the actual staged light                   |
| Turning decisions | Lane geometry and route/sign state                                  | Correct turn direction and room for the complete chassis/arm sweep          |
| Parking           | Marker detection and programmed maneuver                            | A clear parking bay and measured stop, not just a recognized marker         |
| Combined route    | State transitions, stale/lost target handling and command ownership | Every earlier feature and its stop works independently                      |

The article suggests small `lane_x` adjustments of approximately ±3 image-coordinate values. That is an example tuning range, not a wheel geometry parameter. If the mask is correct but motion is wrong, revisit calibration/kinematics. If motion is correct but a turn triggers at the wrong time, inspect the detector/state logic. Store each changed configuration and the test scene so the result is repeatable. [Driving preparation, debugging and integrated course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/6.ROS+Machine_Learning_Course.html#_6-4-autonomous-driving-debugging-lesson).

## Arm hardware, action groups and deviations <a href="#jetrover-reference-arm" id="jetrover-reference-arm"></a>

### Servo identities and a material specification conflict <a href="#jetrover-reference-arm-hardware" id="jetrover-reference-arm-hardware"></a>

The arm chapter describes three body HTD-35H servos, an HTS-20H pan servo, an HTS-21H gripper and an HTD-35H wrist. Confirm the delivered labels. The functional IDs are **1 pan, 2/3/4 main joints, 5 wrist and 10 gripper**. Its half-duplex servo UART runs at **115200 baud**; GND/VIN/SIG is the documented three-wire function set, not permission for a direct GPIO connection.

![Hiwonder JetRover Mecanum arm illustration showing pan ID 1, joints 2 through 5 and gripper ID 10](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/assets/image11.CVYPX4oe.webp)

_Hiwonder official servo-ID illustration, visually inspected. It establishes the course's ID placement, not the installed robot's calibration or a safe commanded pose._ [_Figure source_](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-1-8-robot-arm-deviation-adjustment)_._

The HTD-35H specification table gives 9–12.6 V, 0.18 s/60° at 11.1 V, 0.2° reference precision and 0–1000 controller units for 0–240°. It also prints **3.5 kg·cm** torque while the same page calls it **35 KG** in prose. Those statements conflict; do not select a lifting load or current limit from either label. No arm payload is derived from a servo torque claim. Other actuators in the assembly have their own ratings and travel. [Arm hardware and servo table](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-1-2-htd-35h-serial-bus-servo-instructions).

The chapter's separate assembly table lists a **410 mm span** and **500 g gripping/transport reference**. Preserve those as manufacturer table values with their scene/load limitations; they neither resolve the contradictory servo-torque labels nor approve 500 g at every extension, acceleration or mobile posture. [Assembly specification table](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-1-1-get-to-know-robotic-arm).

### Editing, joining, importing and running actions <a href="#jetrover-reference-actions" id="jetrover-reference-actions"></a>

Stop the app/serial owner, clear the arm sweep and lower/reroute the antenna as the course instructs so the arm cannot strike it. Start the desktop arm tool or `python3 main.py` from `~/software/arm_pc`. The course's action path sometimes appears as `/ubuntu/...`; resolve it to the real installed user's `software/arm_pc/ActionGroups` directory before copying files.

An action group stores timed joint-position rows. Read the existing pose/deviations and back up factory groups first. Select one row and run it before enabling a whole sequence; keep Loop off. “Reset servo” moves joints toward their center, while Manual/unload can remove holding torque, so support the mechanism before either action. A neutral numeric value is not guaranteed to be collision-free with the camera, antenna or display.

To author a pick, separate approach, pregrasp, gripper closure, lift, transit, place and retreat. The course illustrates 2000 ms approach/lift rows and 200/500 ms transition/grip rows, but its joint values and times describe that scene. Choose timings that avoid abrupt loaded moves on the actual robot. Save under a new no-space name. Joining files concatenates them; inspect the boundary between the last pose of one and the first of the next. Exporting/importing `.d6a` data does not transfer the original arm's deviation calibration, load clearance or camera mount. [Action editing/integration/import lessons](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-1-basic-control).

### Deviation is not target position <a href="#jetrover-reference-arm-calibration" id="jetrover-reference-arm-calibration"></a>

Preserve factory deviations on a correctly aligned new arm. Recalibrate only for a measured problem. Record current values, read deviations in the tool and compare the actual arm with the manufacturer's neutral-position figure. IDs 1–5 should meet the indicated vertical alignment, and the gripper reference opening is 2–3 cm. Correct the deviation slider, not a live-position slider, then download/save and recheck. The example's −18-to-2 correction is not a setting for all Servo 3 units.

The software's deviation range is −125 to +125 and its gripper recommendation is 200–700 position units. Do not force the gripper through a mechanical stop to reach a generic 0–1000 servo endpoint. A frozen “read deviation” operation often means another process still owns the serial connection. Diagnose that contention before writing offsets repeatedly. [Deviation procedure and FAQ](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-1-8-robot-arm-deviation-adjustment).

## 2D manipulation and navigation transport <a href="#jetrover-reference-manipulation2d" id="jetrover-reference-manipulation2d"></a>

### Required sequence from detection to a physical grasp <a href="#jetrover-reference-grasp-stages" id="jetrover-reference-grasp-stages"></a>

Use one camera and one command owner. Fix camera pose, table height, lighting and the target, then validate detection, table/depth geometry, arm-frame conversion, IK, approach path, gripper contact and retreat separately. Start with a light supplied block and a stationary base. **Debug launches may move the arm:** the color-sorting source runs `pick_debug`, waits and then runs `pick_init`. Clear and support the mechanism before launch, not only before a later start button.

| JetRover 2D lesson              | `example` launch                                 | On-page development checkpoint                                         |
| ------------------------------- | ------------------------------------------------ | ---------------------------------------------------------------------- |
| Hand tracking                   | `hand_track_node.launch.py`                      | Stable hand location/target loss behavior before physical following    |
| Color sorting                   | `color_sorting_node.launch.py debug:=true`       | Selected target/ROI, calibrated table and correct grasp/place actions  |
| Color tracking                  | `color_track_node.launch.py`                     | Image-center error maps to a reachable arm target without oscillation  |
| Line-following obstacle removal | `line_follow_clean_node.launch.py`, debug option | Line/colored-block detection and LiDAR agree before a clearing action  |
| Waste-card sorting              | `garbage_classification.launch.py debug:=true`   | Detector labels map to the intended demonstration action/category      |
| Navigation and transport        | `navigation_transport.launch.py map:=map_01`     | Correct map/pose, tested route and independently calibrated pick/place |

Sorting uses `config/color_sorting_roi.yaml`; line cleanup uses `line_follow_clean_roi.yaml`; waste-card sorting uses `garbage_classification_roi.yaml`. The sorting debug code illustrates different image ROIs for `Dabai` and other camera types. An ROI is in image coordinates and depends on resolution and mount; do not copy the other camera's rectangle. The source sends color-detection parameters and a circle ROI before starting the pick loop. Validate that the saved ROI still contains the real grasp region and that no same-colored object wins detection elsewhere. [2D vision algorithms and parameters](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-2-2d-vision-vision-application).

### Fixed-point transport adds a second state machine <a href="#jetrover-reference-transport" id="jetrover-reference-transport"></a>

Create and verify a map first. Initialize the robot's actual map pose and test a nearby goal, then calibrate picking with `example automatic_pick.launch.py debug:=true`. The normal transport wrapper starts automatic picking and navigation; its source includes `map_frame`, `nav_goal`, `master_name`, `robot_name`, `debug`, `broadcast`, `place_without_color` and `place_position`. Discover the actual installed arguments with `--show-args` before supplying them.

The course states that a picked block is normally placed after reaching the next goal, while `place_without_color:=false` requests the color/target-dependent placing path. Choose and test that behavior explicitly; arriving at a navigation pose is not evidence that the gripper released the object. Keep map coordinates, target color, pickup/posture calibration and action completion feedback together. The wrapper's 10-second delayed navigation startup is not proof that every sensor/arm is ready. [Fixed-point transport and launch analysis](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-2-6-fixed-point-navigation).

## Depth-based mobility, tracking and grasping <a href="#jetrover-reference-manipulation3d" id="jetrover-reference-manipulation3d"></a>

| Lesson                             | Launch in `example`                     | Configuration and interpretation                                                                          |
| ---------------------------------- | --------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Edge/fall-prevention demonstration | `prevent_falling.launch.py debug:=true` | Calibrates a ground reference in `plane_distance.yaml`                                                    |
| Narrow-bridge demonstration        | `cross_bridge.launch.py debug:=true`    | Calibrates its scene in `bridge_plane_distance.yaml`                                                      |
| Object following                   | `track_object.launch.py`                | Point-cloud/depth target drives base PID; test invalid depth/target loss                                  |
| Tracking and gripping              | `track_and_grab.launch.py`              | Image target, valid depth, current arm endpoint, hand-eye transform and IK                                |
| Object classification              | `object_classification.launch.py`       | Shape/color/depth selection and pick/place path; source loads `object_classification_plane_distance.yaml` |

These five launches include camera/controller dependencies; do not start duplicate hardware owners. Stop app auto-start first, inspect the installed launch arguments and clear/support the **arm as well as the base**. The examples publish initialization servo positions before normal processing, and classification calls `goto_default()` before testing its `start` parameter. `start=False` is therefore not a no-motion launch guarantee. They wait for controller readiness and the camera's `/depth_cam/set_ldp_enable` service (`std_srvs/srv/SetBool`) and request `data=False` in initialization. Inspect that actual camera service/response rather than substituting another driver's similarly named control. Source `~/init_finish` services acknowledge node initialization, not a safe physical scene. [Initialization and dependencies, §§7.3.1–7.3.5](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-3d-vision-vision-application).

Run ground/bridge debug calibration after a change in placement/camera geometry. Begin on a level surface with no real drop. Depth holes, reflective objects, incorrect camera angle or stale references can corrupt the decision. These lessons are not independent safety systems. Source/static review has not verified a motion stop, so repeated Ctrl+C, an advertised service or a readiness response is not an established emergency stop. Keep a separate tested ownership/zero/physical-stop path for later controlled trials.

For 3D picking, validate the depth encoding before any `/1000` conversion; confirm RGB/depth registration, intrinsics and a current arm pose. Then transform the metric camera point into the arm/world reference using the **full** calibrated rotation/translation matrix. The chapter's hardcoded hand-to-camera matrix and directional pick offsets belong to its illustrated mount. Copying only an offset, or importing another robot's matrix, can create a plausible but wrong point. Separate a good detector from a wrong coordinate transform when diagnosing a missed grasp. [3D vision course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-3d-vision-vision-application).

### Ground and bridge reference calibration <a href="#jetrover-reference-depth-ground-bridge" id="jetrover-reference-depth-ground-bridge"></a>

Both examples subscribe to `/depth_cam/depth/image_raw` as `sensor_msgs/msg/Image`, interpret the buffer as `uint16`, discard zero/out-of-range ROI samples and divide their mean by 1000 to obtain **meters**. Verify that interpretation against the installed Dabai encoding. Their small pixel ROIs and initialization poses are scene-specific. Do not transfer the pixels to another resolution/mount.

| Lesson         | Calibration input → saved output                                                                                                                                             | Normal policy in the displayed program                                                                                                                                                                                                                         |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Edge detection | `prevent_falling.launch.py debug:=true`; after **more than 50 frames** with non-NaN left/center/right means, average those three distances into `config/plane_distance.yaml` | Compare each ROI with the reference at **0.02 m** difference. A difference commands **0.8 rad/s** yaw, with illustrated 0.3 s turn / 0.2 s pause timing; an accepted flat view permits **0.2 m/s** forward motion.                                             |
| Bridge         | `cross_bridge.launch.py debug:=true`; after more than 50 frames with a non-NaN center mean, save that center distance to `config/bridge_plane_distance.yaml`                 | Uses left/right sampling shifted outward after calibration, 0.02 m comparisons, and illustrated yaw corrections of ±0.2 or ±1.0 rad/s with 0.2 m/s forward demand; when all three regions differ, publishes a zero Twist. Ackermann is excluded by the lesson. |

**Acceptance procedure:** hold the factory camera/arm geometry fixed over a broad flat test surface, inspect the displayed ROI positions and logged distances, back up the prior YAML, and verify the new `plane_distance` is plausible in meters. Restart without debug only after confirming the saved reference and a supported, clear test area. The debug flag switches itself off after saving; the same process can then enter its motion policy. Debug is not a permanent stationary calibration mode. The bridge's claim of “altitude adjustment” does not establish an active suspension—the shown policy commands planar base motion.

An empty valid-pixel set can produce NaN; the normal loop replaces NaN with zero and passes it to the policy. That may provoke a turn or stop according to the branch, not a certified invalid-depth fail-safe. A queue timeout continues waiting without necessarily publishing a new zero. Original acceptance work must therefore include stale-frame/invalid-depth detection and an independently verified stop before any real ledge or narrow bridge. **No real-drop test was run for this appendix.** [Edge algorithm/calibration](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-1-edge-detection), [bridge branches/calibration](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-2-cross-the-single-plank-bridge).

### Point-cloud following: synchronized inputs and command output <a href="#jetrover-reference-depth-following" id="jetrover-reference-depth-following"></a>

`track_object.launch.py` uses `/depth_cam/rgb/image_raw` and `/depth_cam/depth/image_raw` (`Image`) plus `/depth_cam/depth/camera_info` (`CameraInfo`). The shown `ApproximateTimeSynchronizer` has **queue size 3 and slop 0.02 s**. RGB/depth are downsampled by **4** (illustrated 640×480 → 160×120), with corresponding intrinsics divided by four. The RGBD-to-point-cloud path crops a configured volume, removes a fitted plane and rotates the display cloud before selecting a target point. Code calls `segment_plane(distance_threshold=0.05, ransac_n=10, num_iterations=50)`; for a metric cloud **0.05 is 5 cm**, not the comment's “4 mm.” Inspect depth scaling and the cloud before tuning that threshold.

The example has `stop_distance=0.4` m, a lateral reference `x_stop=-0.1` in its processed-cloud convention, PID gains **(1.5,0,0)** for x/y and **(3,0,0)** for yaw. In its Mecanum branch it generates x/y translation and bounds each displayed linear demand to ±0.3 m/s; the alternate angular branch bounds yaw to ±1 rad/s. These are local example constants and coordinate conventions, not a verified whole-robot safety envelope. The node publishes directly to `/controller/cmd_vel`, bypassing the app-input clamps described above.

**Procedure/output:** with motion physically contained, first check synchronized timestamps, scaled intrinsics, cropped cloud and a known prop. Confirm which point is selected, its distance and the direction of the resulting command before floor operation. An empty point cloud publishes zero; a **two-second queue timeout simply continues** the shown loop, so loss of incoming clouds is not equivalent to the empty-cloud stop. Require a freshness/target-loss stop in the installed controller path before enabling following. The lesson excludes Ackermann and does not establish identity tracking of a person. [Object tracking inputs, PID and loss branches](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-3-object-tracking).

### Color tracking and gripping: service state and geometry <a href="#jetrover-reference-depth-gripping" id="jetrover-reference-depth-gripping"></a>

`track_and_grab.launch.py` supplies `color` and `start`. Its RGB/depth/CameraInfo synchronization uses queue **3**, slop **0.02 s**; a nearby comment says 0.03 s, but the constructor argument is 0.02. It reads `/home/ubuntu/software/lab_tool/lab_config.yaml`, selects `lab/Stereo/<color>`, downsamples color processing by two, filters small contours and chooses the qualifying leftmost contour in the shown tracker. This is a color/contour selection rule, not a general object-category detector.

| Private service in the example | Type / actual state effect                                                                                                                                     |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `~/set_color`                  | `interfaces/srv/SetString`, request `data` is one color string; creates the color tracker and **sets start=True**                                              |
| `~/start`                      | `std_srvs/srv/Trigger`; sets start=True                                                                                                                        |
| `~/stop`                       | Advertised as `Trigger` in initialization; the displayed course excerpt does not show its callback body, so do not infer that it cancels a running pick thread |

Resolve `~` against the actual node/namespace and check service types before a call. **Setting a color is an enabling operation**, not just configuration. A false launch `start` still permits the initialization arm pose; do not infer stationary launch from that parameter. [Service definitions](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/interfaces/srv/SetString.srv), [tracking/gripping node](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-4-tracking-and-gripping).

The tracker uses image-center yaw/pitch PID; after a sufficiently stable pose for **more than 2 s**, it averages a clipped **10×10-pixel** depth neighborhood using raw samples between 0 and 10000, then converts by `/1000`. The example adds two separate **0.015 m** compensations, subtracts **0.01 m** from camera x, and combines current FK endpoint with a hardcoded hand-to-camera transform. Those are mount/object-specific values. Inspect valid depth, transform calibration and the FK `solution`/IK array checks described earlier before accepting a pick. No detection resets its stability timer; invalid/NaN depth can return from the displayed processing function rather than recover a complete task. Do not treat that return as a guaranteed zero/arm abort.

Once accepted, a separate pick thread executes staged approach, closure, a **0.03 m** lift and fixed example placement poses. Observable success requires actual grip, clearance, lift and release, not just nonempty IK pulses. Changing a start flag or acknowledging a service does not prove this sleeping worker stopped. Keep initial acceptance to detection/depth/geometry review until reachable poses, loss handling and worker cancellation are verified on the installed program; fixed destination joints are not portable calibration. [Depth-to-arm calculation and pick thread](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-4-tracking-and-gripping).

### Shape/color classification: configuration, services and known source limits <a href="#jetrover-reference-depth-classification" id="jetrover-reference-depth-classification"></a>

The classification wrapper loads `config/object_classification_plane_distance.yaml` and passes **`category`, `start`, `debug`**. Its synchronized topics and queue/slop are the same RGB/depth/CameraInfo inputs above. Inspect the installed wrapper's actual values; constructor `self.start=False` is not proof of the launch default. Initialization disables the camera LDP setting and calls `goto_default()` before the start test, issuing an arm pose and computing its endpoint. The example's FK reply must still pass `solution`/pose checks.

| Service       | Type and input → state/output                                                                                                                                                          |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `~/start`     | `Trigger` → sets `start=True`, returns success/message                                                                                                                                 |
| `~/stop`      | `Trigger` → clears start, shape/color selection, moving/count/target history; returns success/message. It does not join or demonstrate cancellation of an already running move thread. |
| `~/set_shape` | `interfaces/srv/SetStringList`, `string[] data` → clears color selection, stores the shape list and **starts** processing                                                              |
| `~/set_color` | `interfaces/srv/SetStringList`, `string[] data` → clears shape selection, stores the color list and **starts** processing                                                              |

Shape examples are `sphere`, `cuboid`, `cylinder`; the launch's other category branch proposes red/green/blue. The printed color-start branch uses **`SetStringListi.Request()`**, whereas the defined service type is `SetStringList`. Treat that spelling as a source defect to reconcile with the installed file, not an additional message type. Also, the displayed `color_comparison` returns only **red, blue or None**, and repeats one blue-channel comparison. A selectable green string is not evidence of a working green classification/placement route. [Exact list service](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/interfaces/srv/SetStringList.srv), [classification callbacks and branches](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-5-object-classification).

**Calibration differs from the ground/bridge files:** debug takes the minimum scene distance for more than 50 frames and saves `int(min_dist)` as `plane_distance`—**raw depth millimeters in this example**, not the earlier meter-valued mean. Back up the YAML, use the actual empty reference plane/ROI, inspect logged raw values and verify the saved file before selecting a target. The normal depth mask removes values beyond `plane_distance-10` and `min_dist+40`; the latter is **40 raw millimeters**, despite a comment saying 15 mm. Zero samples are replaced in the search array, but that substitution does not prove an all-invalid frame will be rejected safely.

The program forms depth contours, approximates their boundaries, uses rectangle/aspect and threshold heuristics, and filters by the selected shape/color. The displayed scene gate requires `min_dist <= 300` raw millimeters, ignores contour area below 300 pixels² and uses `approxPolyDP` at **0.035 × perimeter**; these thresholds belong to its tabletop view. It initially chooses minimum depth among eligible detections, then seeks a stable target across frames; it is not selecting the first arbitrary RGB blob. Its displayed “depth standard deviation” calculation is actually `np.nanstd(mask)`, not a dispersion calculation on valid depth pixels. Do not promote that label into a validated 3D shape estimator. Acceptance requires inspecting the selected contour, metric target, current endpoint and complete IK result before a separate movement.

The shown stable-position gate compares an x/y displacement measure to **0.005 m** over more than five updates. A move thread then picks and routes shapes to example `target_1`/`target_2`/`target_3` action groups, or the implemented color branch, before returning to its reference pose. Those action files, ROI, hand-eye transform, pick offsets and destinations must match the installed scene. A `stop` response or reset of `moving` does not prove that this worker cannot still issue subsequent servo commands. First verify classification without starting a pick, then validate one supported light prop and the cancellation/clearance path in a contained setup. No upstream program or physical classification/grasp was run in preparing this reference. [Selection, stability, calibration and move sequence](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/7.Robot_Arm_Control_Course.html#_7-3-5-object-classification).

## MoveIt 2, Gazebo and workstation configuration <a href="#jetrover-reference-simulation" id="jetrover-reference-simulation"></a>

### Workstation import, robot model and planning scene <a href="#jetrover-reference-moveit" id="jetrover-reference-moveit"></a>

The course provides a VM installation/import workflow, feature package import and workspace build. Confirm the supplied Ubuntu/ROS architecture and enough VM RAM/disk before building. A workstation VM's account, IP and compiler are not the robot's native environment. Use its actual network settings and the correct `jetrover_description` URDF/Xacro. Inspect joint names, axes, origin transforms, inertias, limits, collision geometry and Mecanum/A1 sensor selection before planning.

The MoveIt setup-assistant lesson covers self-collision configuration, virtual joint, planning group/end effector, named states and controllers. Do not remove collision pairs merely to make a difficult plan succeed. A gripper mesh, carried object and arm/base clearance must be represented consistently.

Launch `hiwonder_moveit_config demo.launch.py` for the illustrated interface. The course then covers a chosen target, random poses, Cartesian paths, collision detection, scene objects and trajectory planning. Inspect the start state, path and completion/fraction before execution. A random target or partially planned Cartesian path is unsuitable for initial physical commissioning. Scene objects need the right frame and dimensions; a visually displaced collision box protects the wrong space. [MoveIt/URDF course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/8.MoveIt_Gazebo_Simulation.html#_8-3-moveit2-simulation).

### Physical synchronization and simulated SLAM/navigation <a href="#jetrover-reference-gazebo" id="jetrover-reference-gazebo"></a>

Physical synchronization starts the actual lower-controller and `servo_controller` bridges. Keep those stopped during simulation-only exercises. Before activating them, verify the actual six IDs, neutral deviations, accepted units, current joint state, collision model, command ownership and physical stop. A planned target in the display is not authorization to send an unchecked pose to a real arm.

Gazebo exercises cover GUI/world interaction, Xacro visualization, hardware simulation, mapping, navigation and integration with MoveIt. The source launches `robot_gazebo worlds.launch.py moveit_unite:=true`, `room_worlds.launch.py`, `slam.launch.py` and `ros2 run robot_gazebo teleop_key_control`. Save simulation maps under `robot_gazebo/maps`, separately from real maps. For navigation it uses `room_worlds.launch.py nav:=true` and `robot_gazebo navigation.launch.py map:=map_01`. Combined planning uses `hiwonder_moveit_config demo.launch.py use_sim_time:=true use_gazebo:=true`.

Confirm `/clock` and simulation-time settings across the entire simulated graph, and make sure physical serial drivers are not receiving those commands. A simulated route validates only that model/scene/controller combination; it does not test real friction, scanner blind spots, payload or hardware latency. [Gazebo and integration lessons](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/8.MoveIt_Gazebo_Simulation.html#_8-4-gazebo-simulation).

## Six-microphone hardware and speech provisioning <a href="#jetrover-reference-voice-hardware" id="jetrover-reference-voice-hardware"></a>

### Front end, USB audio and serial recognition are separate <a href="#jetrover-reference-r818" id="jetrover-reference-r818"></a>

Install the Developer kit's microphone expansion according to its keyed wiring figure before testing voice. The R818 front end exposes separate **serial**, **reference/echo-cancellation**, **microphone-array**, **independent power** and **UAC audio** connections. A UAC audio device and a recognition serial port perform different jobs. Do not force the array ribbon or confuse the echo reference with a speaker output.

| Source component             | Numerical reference                                     | Scope                                                                   |
| ---------------------------- | ------------------------------------------------------- | ----------------------------------------------------------------------- |
| R818 board supply            | 4.75–5.25 V, nominal 5 V                                | Board supply range, not a raw Jetson I/O rating                         |
| R818 current                 | 250 mA minimum, 300 mA typical, 400 mA maximum in table | Component reference; not the whole voice/robot power budget             |
| R818 temperature             | −20 to +70 °C                                           | Does not override the robot/host operating range                        |
| Microphone element reference | Nominal 3.3 V, 0.8 mA typical, 10 mA maximum            | Element table, not an instruction to power the complete array from GPIO |
| Acoustic reference           | 65 dB SNR in component table                            | Manufacturer specification, not an observed recognition result          |

Test USB enumeration, capture, playback and recognition separately. The sound-card course distinguishes USB and left/right output ports; verify actual device routing before changing ASR configuration. A successful audio playback does not prove wake-word recognition, and a recognized wake word does not prove that navigation maps or arm actions are ready. [R818, array and sound-card course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/9.Voice_Control_Course.html#_9-1-voice-control-basic-lesson-ring-microphone-array).

### Licensed resources, wake words and architecture <a href="#jetrover-reference-speech-resources" id="jetrover-reference-speech-resources"></a>

The source's standalone microphone configuration uses a VM, imports `xf_mic_asr_offline` and message packages, builds the workspace, sets udev access and installs architecture-specific libraries. Its explicit `lib/x64` example is for that workstation architecture. Do not copy it into native AArch64 Orin. Preserve the robot's working factory libraries and inspect the actual ELF architecture/dependencies before replacement. Broad writable permissions or removal of unrelated system services are not a default fix for a recognition problem.

Offline command recognition requires the account-specific **`common.jet` resource and matching APPID** from the named iFLYTEK service. The course explains account/resource acquisition; it does not supply a valid universal ID. Back up the existing pair and install a matched release. Changing only the APPID or only the resource can break initialization even though USB audio still works.

The wake-word provisioning example contains both `enable_seting` and `enable_setting` spellings in different sections. Inspect the installed `mic_init.launch.py` arguments with `--show-args` and the matched package before invoking a provisioning operation. Normal recognition uses `mic_init.launch.py`, and the documented sound-source angle topic is `/awake_node/angle`; confirm its actual type in the graph. Wake-word programming can alter the microphone module's persistent configuration, so keep it separate from a read-only audio test.

The default English wake phrase is “hello hiwonder”. Chinese/English selection uses the desktop tool and matching resources, followed by the documented restart. Do not assume that changing a language menu alone supplies missing acoustic resources or firmware. No microphone serial baud rate or pin-level logic compatibility is inferred from an unrelated controller's 115200-baud example. [Resource/APPID and language lessons](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/9.Voice_Control_Course.html).

## Voice-controlled JetRover behaviors <a href="#jetrover-reference-voice-actions" id="jetrover-reference-voice-actions"></a>

The following launches are in `xf_mic_asr_offline`. Configure the actual six-microphone lane, verify recognition/audio without action dispatch and stop competing control owners first.

| Function                  | Launch                                                       | Required scene/data                                                |
| ------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------ |
| Chassis commands          | `voice_control_move.launch.py`                               | Clear floor, direction/stop checks and one motion owner            |
| Arm actions               | `voice_control_arm.launch.py`                                | Correct IDs/deviations/action groups and clear sweep               |
| Color recognition         | `voice_control_color_detect.launch.py`                       | Saved LAB thresholds and a stationary test prop                    |
| Color tracking            | `voice_control_color_track.launch.py`                        | Stable target and tested target-loss behavior                      |
| Color sorting             | `voice_control_color_sorting.launch.py debug:=true`          | Same ROI, arm and table calibration as ordinary sorting            |
| Waste-card sorting        | `voice_control_garbage_classification.launch.py debug:=true` | Verified class-to-category/action map and safe demonstration cards |
| Named-point navigation    | `voice_control_navigation.launch.py map:=map_01`             | Matching saved map and verified A/B/C/origin coordinates           |
| Navigation plus transport | `voice_control_navigation_transport.launch.py map:=map_01`   | Route, pickup and placement separately validated                   |

The recognized direction phrases select moving actions; they are not harmless speech-output tests. A wake acknowledgement, decoded text, action acceptance and completed motion are distinct states to observe. For a failed task, inspect the last completed state rather than repeating a movement command. The source's waste categories and printed cards are staged recognition examples, not general guidance for handling hazardous objects. [Voice action course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/9.Voice_Control_Course.html#_9-3-voice-interaction-application).

**Actual movement-node contract (§9.3.2).** Its wrapper includes controller, LiDAR and microphone initialization. The node waits for `/asr_node/init_finish` (`Trigger`), subscribes to **`/asr_node/voice_words` (`std_msgs/msg/String`)**, **`/awake_node/angle` (`std_msgs/msg/Int32`, used as degrees)** and **`/scan_raw` (`sensor_msgs/msg/LaserScan`, best-effort QoS)**, and publishes `Twist` directly to **`/controller/cmd_vel`**. It initially sends a zero Twist and plays its running acknowledgement. Topic names, scanner selection and actual readiness must match the installed image. The following are the displayed **Mecanum examples**, not universal speed, braking or motion-duration limits:

| Recognized input/state        | Program action                                                                                        | Completion/limitation                                                                                                                                                |
| ----------------------------- | ----------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Wake phrase → acknowledgement | Say “hello hiwonder,” wait for “I'm here,” then issue one phrase                                      | The instructions request a wake before each command; a log mentions a 15 s wake window, which is image-specific behavior to check, not a guaranteed command deadline |
| `go forward` / `go backward`  | Plays feedback and publishes x = **+0.2 / −0.2 m/s**, with an illustrated **2 s** deadline            | Main loop publishes zero when the deadline expires; this is timed command execution, not distance feedback                                                           |
| `turn left` / `turn right`    | Publishes z = **+0.8 / −0.8 rad/s** for the illustrated **2 s**                                       | Direct controller input bypasses the app's ±0.5 rad/s clamp. Ackermann uses a different forward/turn branch, not these in-place commands.                            |
| `come here`                   | First turns toward the microphone angle; on turn completion it sends zero and enables LiDAR following | Follows the **nearest valid range target** in its forward sector, not an identified speaker/person                                                                   |
| New sound-source angle        | Angle callback sets `start_follow=False` and publishes zero                                           | It does not clear every pending transition flag; a callback outcome is not an independently verified emergency stop                                                  |

The come-here example uses **0.4 m** stand-off, a 90° follow sector and 3 m threshold, with distance/yaw PID and illustrated speed constants. For A1 it uses the non-G4 scan indexing/sign branch. It filters zero/nonfinite scan samples and controls range/bearing to the selected nearest return; an empty valid set leaves the zero-initialized Twist in that callback. Nearby furniture or another person can become the target. Its counter ends following after ten zero-demand updates; the displayed callback does not reset that counter on every intervening moving update, so this is not a proven consecutive dwell test. None of this is global navigation, human identity tracking or proof of stopping distance.

**Procedure:** verify recognition and microphone angle without movement dispatch; then, only in a contained direction/stop check, observe recognized phrase → audio acknowledgement → actual command → deadline-zero/verified rest. Wait for one action to complete before another. The ordinary speech callback's sleep status is principally an audio/status path, and come-here can remain in following after the initial timed turn. Do not use a wake/sleep phrase as the sole stop path. Shut down the behavior and confirm command ownership/zero before returning to navigation or arm transport. The map, arm, ROI and action-group prerequisites in the other voice rows remain independent requirements. [Voice movement initialization, callbacks and timed/following states](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/9.Voice_Control_Course.html#_9-3-2-voice-controlled-car-movement).

## Cloud language, speech and vision models <a href="#jetrover-reference-models" id="jetrover-reference-models"></a>

### Validate model I/O before enabling robot tools <a href="#jetrover-reference-model-basics" id="jetrover-reference-model-basics"></a>

The large-model course separates LLM text/semantic interpretation/emotion labels, speech recognition/synthesis, visual understanding/detection/OCR and multimodal/agent interaction. Begin with the supplied `~/large_models` scripts while physical robot action nodes are stopped. The documented examples include `openai_llm_demo.py`, `openai_llm_nlu_demo.py`, `openai_llm_er_demo.py`, `wakeup_demo.py`, `openai_asr_demo.py`, `openai_tts_demo.py`, `openai_vllm_understand.py`, `qwen_vllm_detect_demo.py`, `openai_vllm_ocr.py` and `openai_agent_demo.py`. The conversation demo is spelled `openai_interaciton_demo.py` in the source; inspect the delivered filename.

The standalone demos use `~/large_models/config.py`, including `llm_api_key` and `vllm_api_key`. The ROS integration has a separate configuration under the `large_models` ROS package. Do not edit a standalone file and assume a ROS node reads it. Select the actual provider/backend and microphone/ASR mode, provide a working internet route and keep private keys out of published logs/screenshots. A provider name or model shown in a source screenshot is not current entitlement or availability verification.

Test intelligible capture → transcript → parsed model result → TTS playback, then a fresh-image interpretation/OCR test. The result should agree with a known prop or document. A fluent response, confidence phrase or emotion label is not proof of correct perception. The course contains broad Python package upgrades and host-specific speech wrappers; preserve the factory environment and its CUDA/Python ABI rather than applying every install command to the robot. [Large-model basic course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/10.Large_AI_Model_Courses_checked.html#_10-1-large-models-basic-courses).

### Multimodal control and embodied tasks <a href="#jetrover-reference-model-actions" id="jetrover-reference-model-actions"></a>

| JetRover model application | `large_models_examples` launch                    | Prerequisite/result boundary                                                                                                                                  |
| -------------------------- | ------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Voice movement             | `llm_control_move.launch.py`                      | Source uses `eval` and delayed interruption; physical dispatch is excluded from initial commissioning until the safeguards below are implemented and verified |
| Autonomous visual patrol   | `llm_visual_patrol.launch.py`                     | Correct line mask and state transition before motion                                                                                                          |
| Color following            | `llm_color_track.launch.py`                       | Selected target, depth/tracking validity and loss stop                                                                                                        |
| Real-time scene detection  | `vllm_with_camera.launch.py`                      | Fresh image and checked interpretation                                                                                                                        |
| Vision tracking            | `vllm_track.launch.py`                            | Correct object selection before a controller is allowed to follow                                                                                             |
| Smart-home assistant       | `vllm_navigation.launch.py map:=map_01`           | Verified location-name/map-coordinate dictionary and navigation completion                                                                                    |
| Intelligent transport      | `vllm_navigation_transport.launch.py map:=map_01` | Map/pose and explicit pick/place calibration, with completed-state feedback                                                                                   |

**Actual model I/O and runner behavior.** The voice-movement prompt asks for an object with `action` (ordered **`[x,y,z,t]` numeric rows**) and a `response` string. Here x/y are **m/s**, z is **rad/s** and t is **seconds**. The prompt suggests x/y/z within ±1 and a final `[0,0,0,0]` row; those are prompt instructions, not runtime validation or safe whole-robot limits. Its own wording also calls actions strings in one place, a clockwise example uses **positive z** despite the stated negative-clockwise convention, and one Chinese stop example contains five values. Do not copy those inconsistent examples as an accepted schema or direction calibration. [Course prompt and process](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/10.Large_AI_Model_Courses_checked.html#_10-2-1-voice-control-with-multimodal-large-model).

| Pinned movement-node connection                                            | Actual function                                                                                         |
| -------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `agent_process/result`, `String` input                                     | Model result text stored for the processing thread                                                      |
| `vocal_detect/wakeup`, `Bool` input                                        | Callback sets an interrupt flag when a result is pending; it does not interrupt the current sleep       |
| `tts_node/play_finish`, `Bool` input; `tts_node/tts_text`, `String` output | Audio-completion callback and speech response channel, separate from movement completion                |
| `agent_process/set_model` / `agent_process/set_prompt` services            | Install selected LLM/provider settings and prompt; successful configuration does not validate an action |
| `vocal_detect/enable_wakeup`, `SetBool` service                            | Re-enables wakeup from the audio callback                                                               |
| `/controller/cmd_vel`, `Twist` output                                      | Direct motion command path, bypassing the controller's app-input clamps                                 |

The pinned **`llm_control_move.py` at commit `ef9653885a19a667d0b1642ce67255c555823482`** checks whether the result text contains the substring `action`, slices from the first `{` through the first `}`, and passes that substring to **Python `eval`**. This evaluates an untrusted expression; it is not strict JSON parsing or a data-only boundary. It then takes each row's first three values through `float`, publishes a Twist, calls **`time.sleep(i[3])`**, and only **after that sleep** checks the interrupt flag. No schema, finite/range, duration or sequence-length validation is established by that shown path. A long duration delays this interrupt check; malformed rows/durations or evaluation errors have no guaranteed terminal-zero cleanup in this processing loop. The model-supplied final zero is not an independently enforced stop. No malicious output or upstream parser was executed for this appendix. [Exact pinned parser, publication and interruption sequence](https://raw.githubusercontent.com/Hiwonder/JetRover/ef9653885a19a667d0b1642ce67255c555823482/src/large_models_examples/large_models_examples/llm_control_move.py).

The pinned audio callback reuses its incoming `msg` variable for a new `SetBool.Request(data=True)` and stores that request's value as `play_audio_finish`. That flag therefore does not independently prove the incoming playback-completion value or physical action completion. The process separately clears its audio/action flags; the flat course excerpt's layout is not a substitute for the pinned file's indentation. Observe received result, proposed data, speech and physical command completion as separate states.

**Required hardening, not a description of the supplied implementation:** keep this model-motion dispatch outside initial physical commissioning until `eval` is replaced by strict data parsing, each action has exactly four finite numeric fields with explicit speed/duration/total-time/count bounds, allowed actions/scene and command ownership are enforced, and every error/completion/cancellation path sends a terminal zero through an interruptible, verified stop path. Do not start the unmodified launch merely to obtain a “dry run”—its wrapper includes the controller and the runner has a direct publisher. Review model output with physical action nodes stopped or through a separately verified non-actuating capture path; no built-in dispatch-disable switch is established here. Prompt limits alone enforce none of these controls. Unknown actions, stale images and unreachable destinations must fail before physical commands. These are proposed acceptance requirements; neither hardening nor hardware behavior was implemented or tested in this documentation task.

The transport course calibrates pickup and placement separately with `large_models_examples automatic_pick.launch.py debug:=pick` and `debug:=place`. These launches can move the arm and require full clearance. Map construction follows the ordinary mapping course. After initial-pose alignment, verify named locations in the installed `large_models_examples/navigation_transport/vllm_navigation_transport.py` and the corresponding map revision. The source listens to navigation/action/audio completion states; a model response is not the same as `navigation_controller/reach_goal`, completed pickup or completed speech. Wait for the actual stage result before advancing or retrying.

The reviewed JetRover chapter does not establish the ROSOrin Pro OpenClaw deployment or that platform's offline Ollama model configuration for this image. Those are not silently added as supported JetRover software. [Multimodal/embodied/transport course](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/10.Large_AI_Model_Courses_checked.html).

## Original offline RRC integrity and servo-status check <a href="#jetrover-reference-offline-check" id="jetrover-reference-offline-check"></a>

This original example validates a **single copied receive frame**, without opening a serial port. The default is generated synthetic data with a valid CRC: servo 5 reports raw position 833 successfully. It is not an observed measurement or a command to replay.

```python
import json
import struct
import sys

def crc8(data):
    result = 0
    for octet in data:
        result ^= octet
        for _ in range(8):
            result = (result >> 1) ^ (0x8C if result & 1 else 0)
    return result

def inspect_frame(frame):
    if len(frame) < 5 or frame[:2] != b'\xaa\x55':
        raise ValueError('missing RRC header or incomplete frame')
    function, size = frame[2], frame[3]
    if len(frame) != size + 5:
        raise ValueError('length mismatch: supply exactly one complete frame')
    if crc8(frame[2:-1]) != frame[-1]:
        raise ValueError('CRC mismatch')
    payload = frame[4:-1]
    result = {'function': function, 'payload': payload.hex(' '), 'crc': 'valid'}
    if function == 5 and size == 5 and payload[1] == 5:
        servo, command, status, position = struct.unpack('<BBbh', payload)
        result.update(servo_id=servo, status=status)
        if status == 0:
            result['position_units'] = position
        else:
            result['error'] = 'servo_read_failed'
    return result

if __name__ == '__main__':
    if len(sys.argv) > 1:
        packet = bytes.fromhex(sys.argv[1])
    else:
        body = bytes.fromhex('05 05 05 05 00 41 03')
        packet = b'\xaa\x55' + body + bytes([crc8(body)])
    try:
        print(json.dumps(inspect_frame(packet), sort_keys=True))
    except ValueError as error:
        raise SystemExit(str(error))
```

Save as `jetrover_rrc_review.py` and run `python3 jetrover_rrc_review.py`. **Expected result:** a CRC-valid synthetic record with function 5, servo ID 5, status 0 and `position_units` 833. A bad checksum or truncated input is rejected. For a valid failure report the status is retained and no position is reported as successful. Unknown function/payload combinations remain raw rather than being decoded as a servo reply. This verifies protocol arithmetic only; it does not qualify hardware, units, origin, timing or replay safety.

## Downloads, troubleshooting and validation boundaries <a href="#jetrover-reference-resources" id="jetrover-reference-resources"></a>

| Material                                       | Official destination and selection rule                                                                                                                                    |
| ---------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Robot images, hardware/source and course files | [JetRover resource collection](https://drive.google.com/drive/folders/1vr9opcQeVnQY6R7BgDco-8LP2xWboiwR?usp=sharing); select the Orin Nano/Mecanum/A1 equipment lane       |
| Inspectable Orin ROS 2 source                  | [Pinned repository](https://github.com/Hiwonder/JetRover/tree/ef9653885a19a667d0b1642ce67255c555823482); do not select the older Nano ROS 1 branch by default              |
| Image-writing tools                            | [Official image tool folder](https://drive.google.com/drive/folders/1k4gIGDWEmgu7HhTDvxbNj5_nOkqB-_tN?usp=sharing); archive contents/checksums not verified here           |
| STM32 programming tools                        | [Official firmware tool folder](https://drive.google.com/drive/folders/1RzDiZqcR_29F8EAGOym4mc0ZHRiTKtKU?usp=sharing); exact board/HEX match required                      |
| Remote access                                  | [NoMachine/MobaXterm collection](https://drive.google.com/drive/folders/198a6cQdzJ2gbj5ZP0_yByOO8D1fSK4gt?usp=sharing)                                                     |
| Simulation/voice workstation                   | [VM collection](https://drive.google.com/drive/folders/18tzfLt9Dtzy2C_jYPdtwrijrjSwNjLc-?usp=sharing); verify architecture and ROS lane                                    |
| Voice recognition materials                    | [Official voice collection](https://drive.google.com/drive/folders/1ulzsl1SCcD38hx4lNaDriItl90PRpeRo?usp=sharing); licensed speech resource/APPID remains account-specific |
| Mapping supplementary files                    | [Make a Map and Map\_nav](https://drive.google.com/drive/folders/14qPgstAi2agv1oakEjxmZ-YGKj8C8FNB?usp=sharing); not a replacement for the robot's actual room map         |
| All linked resource entries                    | [Official appendix](https://wiki.hiwonder.com/projects/JetRover/en/jetson-orin-nano/docs/resources_download.html)                                                          |

These are observed manufacturer destinations, not certification of every archive inside a folder. Record the downloaded filename, model/host revision and hash before using an image, firmware binary, CAD file or executable. Account-gated/download-only materials remain a specific access limit. Manufacturer diagrams, code and binaries retain their rights; this reference supplies original explanations rather than a wholesale course copy.

The official appendix explicitly asks owners to request the system image/source package from Hiwonder with an order number. No request was sent in this review. The public Orin GitHub tree is readable but does not establish the supplier image's exact release/checksum. The Drive collection and voice-material links were inaccessible through the research browser, so individual images, hardware archives, firmware tools and licensed speech packages were not downloaded or tested here.

| Symptom                                  | Separate the following causes before changing firmware                                        |
| ---------------------------------------- | --------------------------------------------------------------------------------------------- |
| A1 spins but navigation is empty         | Actual A1 selection, one driver owner, decoded LaserScan, timestamps and TF                   |
| Screen works, touch does not             | Display video versus touch/data cabling and device enumeration                                |
| Robot does not strafe                    | Mecanum selection, rollers/motor assignments, command y value and encoder signs               |
| Map bends or walls duplicate             | Wheel slip/scale, scanner pose, timing and localization ownership                             |
| Color center is correct but grasp misses | Table/depth scale, registration, current endpoint, hand-eye geometry, IK and gripper offset   |
| Voice wakes but command fails            | Resource/APPID, language, command recognition, active action node and correct map/action file |
| Model talks but transport stalls         | Parsed tool request versus navigation, pick/place and audio completion states                 |
| App disappears after development         | Standalone owners still running, then factory service state                                   |
| Motor-load resets/beeping                | Pack charge, matched host power, connectors and mechanical stalls before ROS tuning           |

No ROS build, simulation run, firmware flash, physical drive, arm calibration or grasp was executed in this review. Local syntax/CRC checks do not constitute hardware validation. The source inconsistencies and blocked substitutions identified above remain visible so an engineer can choose the matching image and verify one stage at a time.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed the exact Developer/Nano SUPER 8 GB/Mecanum catalog variant, official manual, ROS 2 course interfaces and resource links. The Orin port photograph was visually inspected. The original offline packet inspector passed syntax parsing and does not open hardware.

No system installation, ROS build, CRC/hardware transport validation, drive, calibration or grasp was run. Sensor/display/voice checks above describe expected user checkpoints, not observed test outcomes. Related [ROSOrin Pro](https://wiki.openelab.io/robotics/hiwonder/hiwonder-rosorin-pro-development-guide) uses a different mechanical/sensor package.
