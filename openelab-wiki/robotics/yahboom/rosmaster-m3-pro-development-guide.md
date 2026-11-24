---
description: >-
  Commission the NX SUPER 16 GB M3 Pro with power routing, a passive ROS 2
  sensor check, dual-LiDAR fusion, depth imaging, arm calibration and recovery.
---

# Yahboom ROSMASTER M3 Pro NX SUPER: ROS 2 sensors, arm and navigation

{% hint style="info" %}
[**Yahboom ROSMASTER M3 Pro on OpenELAB — SKU Yahboom-3000200868**](https://openelab.io/products/yahboom-rosmaster-m3-pro-ros2?variant=47069007020230)
{% endhint %}

## Product overview <a href="#product-and-scope" id="product-and-scope"></a>

The ROSMASTER M3 Pro is a ROS 2 mobile manipulator with a Mecanum chassis, six-axis arm, two diagonal LiDARs and an Orbbec depth camera. This guide covers the **Orin NX SUPER 16 GB + 7-inch touchscreen** option, with a 256 GB SSD. Commission its communications and sensor streams first, then the chassis, arm and navigation in separate stages. The ordinary M3, Raspberry Pi package and older Jetson Nano package have different images and execution environments. [Exact store option](https://openelab.io/products/yahboom-rosmaster-m3-pro-ros2?variant=47069007020230), [manufacturer course portal](https://www.yahboom.net/study/ROSMASTER-M3PRO).

The NX image runs Ubuntu 22.04 and ROS 2 Humble on the host. Instructions that first enter the Raspberry Pi/Jetson Nano ROS container do not describe this NX software lane. A micro-ROS agent container can still appear on NX: that bridges the controller to ROS and does not mean all ROS applications run inside it. [ROS-control lesson](https://www.yahboom.net/study/ROSMASTER-M3PRO/15792).

## Applications

Use the platform to study omnidirectional odometry, dual-LiDAR fusion, SLAM, depth-based grasping and coordinated mobile manipulation. A useful project sequence is a sensor health log, a short repeatable chassis course, a saved map and finally a stationary pick-and-place station. This separates mechanical calibration from perception failures.

The current course also covers MediaPipe, YOLO, MoveIt 2, multi-robot operation, language/vision models, OpenClaw, road-network routing and a warehouse sandbox. These build on the same power, serial bridge, transforms and calibration. AI demos can invoke physical actions; inspect their action interface before connecting a model to it. Neither a successful chat reply nor a simulated plan validates a safe real trajectory. [Official repository and complete lessons](https://github.com/YahboomTechnology/ROSMASTER-M3PRO).

## Specifications

| Subsystem                 | Assigned NX SUPER kit                                                                        | Engineering implication                                                                                            |
| ------------------------- | -------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Compute                   | Orin NX SUPER 16 GB; 8-core Cortex-A7 8AE; 1,024 CUDA/32 Tensor cores                        | Record delivered JetPack and power mode; advertised peak inference capacity is not measured application throughput |
| Storage/display           | 256 GB SSD; 7-inch touch display                                                             | Back up the SSD before replacing the system                                                                        |
| Chassis                   | Four 80 mm Mecanum wheels; four encoder-equipped 520 geared motors; rear pendulum suspension | Wheel orientation and encoder direction affect lateral motion and odometry                                         |
| Controller                | STM32H743VGT6; nine-axis IMU; micro-ROS firmware                                             | USB serial bridge must be running before controller ROS topics appear                                              |
| LiDAR                     | Two T-mini Plus ToF scanners, left-rear and right-front                                      | Raw streams are separate; navigation uses fused/filtered data                                                      |
| LiDAR limits              | 0.05–12m; 4,000 ranging samples/s; 6–12 Hz scan rate                                         | Physical 12m capability does not override a shorter merger range setting                                           |
| Depth camera              | Orbbec DaBai DCW2; USB 2.0 Type-C; up to 640 × 400 depth                                     | Manufacturer lesson gives 0.15–5m working range; use objects comfortably outside the near limit                    |
| Arm                       | Six axes; five 15 kg-class and one 6 kg-class bus servo                                      | Servo torque-class labels are not kilogram payload ratings                                                         |
| Arm reference performance | 30 cm grasp radius; up to 410 g object; ±0.5 mm stated precision                             | Reach, posture, calibration and object geometry affect results                                                     |
| Battery                   | 12.6 V, 9,600 mAh pack                                                                       | Use the matching pack and charger; this is not a 5 V robot input                                                   |
| Envelope/mass             | About 276.97 × 212.4 × 571.57 mm with arm upright; 4.12 kg with display                      | Check the arm's swept volume as well as the chassis footprint                                                      |

Values identify the offered configuration, not measurements from this guide. LiDAR angular resolution is listed as 0.54° and ranging accuracy as 20 mm in the sensor lesson. DCW2's stated depth accuracy is below 1% at 1m. [Store specifications](https://openelab.io/products/yahboom-rosmaster-m3-pro-ros2), [LiDAR and camera lessons](https://www.yahboom.net/study/ROSMASTER-M3PRO), [manufacturer PDFs](https://github.com/YahboomTechnology/ROSMASTER-M3PRO).

## Hardware and connections <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

### Power domains and connector identification

The battery enters the controller's **T-type DC12 V input**. The board distributes converted and unconverted supplies. The Orin uses its **DC12 V output** cable; the separate DC5 V and protocol-aware Type-C 5.1 V/5 A outputs serve other host configurations. Do not move the NX power lead to a 5 V output because a Pi tutorial shows it. The charging connection is marked 12.6 V. Read the silkscreen with the board powered off before moving cables. [Controller introduction, pages1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/main/18.Control%20Board%20Course).

The official board photograph identifies the two red 12 V outputs, yellow T-type input, DC5 V output, Type-C 5 V output, charger, power switch and USB communication port. Its numerical labels are illustration callouts, not connector pin numbers. For the controller pin-assignment diagram and physical socket orientation, open **18.Control Board Course → Development environment setup → Introduction to the Control Board**, pages1–5. These manufacturer diagrams are more useful than guessing wire order from wire color. [Attributed Yahboom board diagrams](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/main/18.Control%20Board%20Course).

| Controller connection | Routing and limit to preserve                                                     |
| --------------------- | --------------------------------------------------------------------------------- |
| USB Connect Type-C    | Host data connection and MCU serial flashing; separate from Type-C 5 V **output** |
| Left-rear LiDAR       | UART4, MCU PC10/PC11; raw ROS `/scan0`                                            |
| Right-front LiDAR     | UART5, MCU PC12/PD2; raw ROS `/scan1`                                             |
| Control serial        | USART6, PC6 TX/PC7 RX; not RS-232 voltage signaling                               |
| Debug serial          | UART7, PE8 TX/PE7 RX                                                              |
| USB serial MCU path   | USART1, PA9 TX/PA10 RX                                                            |
| Bus-servo UART        | USART3, PD8 TX/PD9 RX; supply selected by actual socket                           |
| PWM servos            | S1 PB15; S2 PB14; supply switch 5 V or 6.8 V                                      |
| CAN                   | PD0/PD1 MCU peripheral routing; use board CAN connector/transceiver               |
| Motors                | M1 left-front, M2 left-rear, M3 right-front, M4 right-rear                        |

Pin names above are MCU routing, not permission to connect battery voltage or a 5 V peripheral to a bare GPIO. The board has **6.8 V and 12 V bus-servo sockets**; confirm the servo rating and socket marking before reconnecting an arm. No exposed UART logic-voltage rating was established by the reviewed lesson, so retain the factory harness rather than fitting a speculative TTL adapter. [Official controller diagram and pin table](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/main/18.Control%20Board%20Course).

### Mechanical inspection

With power off, check that Mecanum rollers match the assembly video, motor/encoder plugs reach their labeled positions, both scanner windows are unobstructed and the arm cannot fall into a wheel or camera. The arm may initially be torque-free; support it before power changes. A command that restores torque can also move all six joints. Do not use an arbitrary all-90-degree command as a communications test. [Assembly](https://www.yahboom.net/study/ROSMASTER-M3PRO/15770), [manufacturer FAQ](https://www.yahboom.net/study/ROSMASTER-M3PRO/15772).

## Software and development resources <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

### Delivered environment and ROS ownership

The manufacturer publishes its course PDFs in [YahboomTechnology/ROSMASTER-M3PRO](https://github.com/YahboomTechnology/ROSMASTER-M3PRO). Application code is also delivered in the robot image. Lessons refer to both `~/M3Pro_ws` and `~/yahboomcar_ws`; inspect the installed workspace and package location rather than inventing a universal build path.

Record the environment before updates:

```bash
cat /etc/os-release
cat /etc/nv_tegra_release
printenv ROS_DISTRO ROS_DOMAIN_ID
ls -ld ~/M3Pro_ws ~/yahboomcar_ws
ls -l /dev/myserial
ros2 pkg prefix orbbec_camera
ros2 node list
docker ps
```

A missing workspace in this listing is diagnostic, not a reason to create an empty replacement. The supplied shell environment normally sources the image's packages. If `ros2` is missing, source `/opt/ros/humble/setup.bash`, then the **existing** workspace's `install/setup.bash`. Check that package prefixes resolve before launching demos. The factory uses a configurable ROS domain; match the controller, host and remote workstation. For ordinary isolated robots choose separate domains; intentional multi-robot communication instead uses a shared domain plus distinct namespaces. [Configuration lesson](https://www.yahboom.net/study/ROSMASTER-M3PRO/15771), [multi-vehicle course](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/main/17.Multi-vehicle%20Course).

Factory gamepad control can start automatically. On Orin its launcher is `~/joy_control/joy.sh` and desktop autostart entry `~/.config/autostart/joy_control.desktop`. Close the owning control window before another controller publishes commands. Check `ros2 topic info /cmd_vel --verbose`; multiple publishers mean control ownership is not yet settled. Keep one micro-ROS agent: if a `ros-agent` container already exists and `/YB_Node` is visible, starting another agent is unnecessary. [Gamepad quick start](https://www.yahboom.net/study/ROSMASTER-M3PRO/15744), [FAQ](https://www.yahboom.net/study/ROSMASTER-M3PRO/15772).

### Interface map

| Topic              | Type                        | Direction relative to controller |
| ------------------ | --------------------------- | -------------------------------- |
| `/battery`         | `std_msgs/msg/Float32`      | Measured battery volts out       |
| `/imu/data_raw`    | `sensor_msgs/msg/Imu`       | IMU feedback out                 |
| `/odom_raw`        | `nav_msgs/msg/Odometry`     | Raw odometry out                 |
| `/scan0`, `/scan1` | `sensor_msgs/msg/LaserScan` | Two raw LiDAR streams out        |
| `/cmd_vel`         | `geometry_msgs/msg/Twist`   | Chassis command in               |
| `/arm_joint`       | `arm_msgs/msg/ArmJoint`     | Single-servo command in          |
| `/arm6_joints`     | `arm_msgs/msg/ArmJoints`    | Coordinated arm command in       |
| `/beep`            | `std_msgs/msg/UInt16`       | Buzzer command in                |
| `/rgb`             | `std_msgs/msg/ColorRGBA`    | Lighting command in              |

Confirm with `ros2 node info /YB_Node` on the delivered image. One table in the ROS lesson accidentally repeats `/rgb` for the second scanner; the dedicated LiDAR lesson identifies `/scan1`, which the startup check below verifies. [ROS-control lesson](https://www.yahboom.net/study/ROSMASTER-M3PRO/15792), [LiDAR lesson collection](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/main/02.Lidar%20Course).

## Getting started <a href="#getting-started" id="getting-started"></a>

### 1. Reach the NX without starting a new behavior

1. Support the chassis with wheels clear and leave the arm's workspace empty. Connect the installed battery and original host harness, then power on.
2. Read the actual IP from the OLED. Factory AP instructions use SSID `ROSMASTER`, password `12345678` and address `192.168.8.88`; Ethernet can take display priority. Use the displayed address when it differs.
3. Connect from the same network using SSH, for example `ssh jetson@192.168.8.88`. The published initial Orin account is `jetson`, password `yahboom`. Change default credentials before connecting to a shared network.
4. Close the factory gamepad control window, keeping the chassis supported. Run the environment checks above. If the controller node is absent and no agent owns the port, run the supplied `sh ~/start_agent.sh` from the host. Leave that terminal visible.
5. Run `ros2 node info /YB_Node` and verify the table's feedback topics. If the factory script is in another directory, locate the installed file first; do not substitute a micro-ROS transport or baud rate from another robot.

\*\*Expected result: \*\* one agent, a visible controller node, a resolved `/dev/myserial` device and feedback topics. A topic listed without messages is not a successful sensor test. [Login lesson](https://www.yahboom.net/study/ROSMASTER-M3PRO/15745), [ROS control](https://www.yahboom.net/study/ROSMASTER-M3PRO/15792).

### 2. Original 20-second sensor receipt check

Save this original subscriber as `m3_sensor_check.py` on the robot and run `python3 m3_sensor_check.py` in the supplied ROS environment. It never publishes commands and uses sensor-data QoS so best-effort feedback remains readable. It checks receipt and basic plausibility, not calibration accuracy.

```python
import math
import time
import rclpy
from rclpy.qos import qos_profile_sensor_data
from std_msgs.msg import Float32
from sensor_msgs.msg import Imu, LaserScan
from nav_msgs.msg import Odometry

rclpy.init()
node = rclpy.create_node('m3_passive_check')
counts = {}
latest = {}
subs = []

def remember(name, msg):
    counts[name] = counts.get(name, 0) + 1
    latest[name] = msg

for name, kind in [('/battery', Float32), ('/imu/data_raw', Imu),
                   ('/odom_raw', Odometry), ('/scan0', LaserScan),
                   ('/scan1', LaserScan)]:
    subs.append(node.create_subscription(
        kind, name, lambda msg, key=name: remember(key, msg),
        qos_profile_sensor_data))

try:
    deadline = time.monotonic() + 20.0
    while rclpy.ok() and time.monotonic() < deadline:
        rclpy.spin_once(node, timeout_sec=0.2)
    for name in ['/battery', '/imu/data_raw', '/odom_raw', '/scan0', '/scan1']:
        print(name, 'messages=', counts.get(name, 0))
    if '/battery' in latest:
        print('battery_V=', latest['/battery'].data)
    for name in ['/scan0', '/scan1']:
        if name not in latest:
            continue
        scan = latest[name]
        valid = [r for r in scan.ranges if math.isfinite(r)
                 and scan.range_min <= r <= scan.range_max]
        print(name, 'frame=', scan.header.frame_id,
              'valid=', len(valid), '/', len(scan.ranges),
              'nearest_m=', min(valid) if valid else None)
    missing = [name for name in ['/battery', '/imu/data_raw', '/odom_raw',
                                '/scan0', '/scan1'] if not counts.get(name)]
    if missing:
        raise SystemExit('INCOMPLETE: ' + ', '.join(missing))
    print('RECEIVED all five streams; physical accuracy remains unchecked')
finally:
    node.destroy_node()
    rclpy.shutdown()
```

\*\*Expected result: \*\* nonzero counts for all five streams, battery reported in volts and separate scan frame names. Indoor scans should contain finite returns; an empty scene or highly reflective surface can yield invalid samples. Move a cardboard target in front of each scanner while leaving the robot fixed. Only that scanner's corresponding sector should respond. Do not infer that a battery number alone proves the pack can support motor peaks.

### 3. Camera and geometric checks

1. With no existing camera process, start `ros2 launch orbbec_camera dabai_dcw2.launch.py`.
2. Run `ros2 node info /camera/camera`, then `ros2 run rqt_image_view rqt_image_view` in a second terminal. Select `/camera/color/image_raw`, then `/camera/depth/image_raw`.
3. Place a matte box about 0.5–1m away. Confirm that the color silhouette and depth discontinuity refer to the same object. Check the published `Image.encoding` and camera driver units before converting pixels into distance; do not assume all floating-point depth is millimeters.
4. For an independent point-cloud view, run `rviz2`, use `camera_link` as the initial fixed frame and add `/camera/depth/points`. Registered colored data uses `/camera/depth_registered/points`; registration is required before indexing depth by a color-image coordinate.

\*\*Expected result: \*\* live color and depth, stable geometry for the stationary box and no repeated USB disconnects. The official distance demo is `ros2 run yahboom_M3Pro_DepthCam Measure_Distance`; it displays selected-pixel distance. Validate its unit convention against a known distance before using it for grasping. [DCW2 and distance lessons](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/main/03.Depth%20Camera%20Course).

### 4. Chassis, fusion and mapping

After the passive checks, put the robot on an open floor, retain a person at its stop control, start the original gamepad launcher and use START then R2 as instructed by the gamepad lesson. Make brief slow forward, lateral and rotation tests separately. Check that releasing control stops the vehicle. An unexpected sideways direction calls for wheel/motor inspection before odometry tuning. Stop this controller before switching to autonomous navigation. [Gamepad operation](https://www.yahboom.net/study/ROSMASTER-M3PRO/15744).

Fusion and filtering are distinct stages:

```bash
ros2 launch ira_laser_tools merge_multi.launch.py
# Separate terminal, after merger is running:
ros2 launch yahboom_laser_filter laser_filter_node.launch.py
```

The supplied merger transforms `/scan0` and `/scan1` to `base_link`, publishes `/scan_multi` and `/merged_cloud`, and its illustrated range limit is **4m**, not the sensor's12m. The filter produces `/scan` and removes close body returns below 0.18m in its configured angular interval. Inspect both streams in RViz: removing all close obstacles would also hide real hazards. Do not run these standalone nodes twice if a later bringup already launches them. [Dual-LiDAR lesson](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/main/02.Lidar%20Course).

For mapping, the factory course offers Gmapping, Cartographer, slam\_toolbox and RTAB-Map. Use one mapping pipeline at a time. A practical first map is slam\_toolbox: launch `ros2 launch slam_mapping slam_toolbox.launch.py`, drive a short closed loop and watch wall overlap and pose continuity. Save with `ros2 launch slam_mapping save_slamtoolbox_map.launch.py`; confirm files appear in `~/map`. Road-network routing additionally needs a saved pose graph, using the same save launch with `map_type:=posegraph`, and a separately annotated route graph. A grid map alone is insufficient for that workflow. [Mapping and road-network courses](https://github.com/YahboomTechnology/ROSMASTER-M3PRO).

For ordinary Nav2, the course uses `M3Pro_navigation base_bringup.launch.py`, then `navigation2.launch.py` and `nav_rviz.launch.py` in separate terminals. Select the saved map in the installed configuration, initialize **2D Pose Estimate**, check that laser walls align with map walls, then set a nearby **2D Goal Pose** in free space. \*\*Expected result: \*\* a plausible planned path, controlled travel and `Goal succeeded`. Cancel a bad goal before adjusting localization; do not steer against an active planner. [Navigation lesson collection](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/main/02.Lidar%20Course).

### 5. Arm calibration and advanced development

Arm commissioning has two calibrations: servo median alignment and camera-to-grasp offset. Back up the existing calibration first. The Orin median tool is `~/calibrate_arm.py`; it requires exclusive serial access after stopping the agent and makes servos torque-free. Support the arm, use the illustrated L-shaped reference posture and require **all six reported states to equal1** before accepting the calibration. Do not invoke this tool merely to test the port. [Calibration lesson](https://www.yahboom.net/study/ROSMASTER-M3PRO/15767).

Offset calibration launches `M3Pro_demo camera_arm_kin.launch.py` and `M3Pro_demo arm_offset`. It moves the arm to its calibration posture. Place the supplied 4 × 4 × 4 cm block in the onscreen reference region, then accept with Space only after alignment is correct. The lesson stores `arm_kin/param/offset_value.yaml` and rebuilds `arm_kin` in `~/yahboomcar_ws`; verify that this is the actual installed package before rebuilding. Retain the previous YAML for reversal. [Same calibration procedure](https://www.yahboom.net/study/ROSMASTER-M3PRO/15767).

| Official advanced course                                                                                         | Development procedure and useful result                                                                                                                                                                                                                                                     |
| ---------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Arm kinematics, tag/color/shape sorting, KCF tracking, gesture-height sorting, line patrol with obstacle removal | First observe detection overlays with the arm inactive; validate camera coordinates and reach, then enable one bounded pick. Tracking can move both chassis and arm. Keep grasp offsets specific to the target and table                                                                    |
| MediaPipe and depth vision                                                                                       | Start the camera once; verify landmarks/detections on the image before linking them to motion. Distinguish image recognition, depth localization and the grasp controller                                                                                                                   |
| MoveIt2                                                                                                          | Start `ros2 launch test_moveit_config demo.launch.py` for simulation; check joints, collision objects, Cartesian paths and planned trajectories there. `MoveIt_SimToMachine SimulationToMachine` is a separate physical bridge and should remain stopped during simulation-only exploration |
| Multi-robot control                                                                                              | Put cooperating robots in the same domain with distinct namespaces; inspect each robot's topic names before commanding either. A shared unnamespaced `/cmd_vel` can address both                                                                                                            |
| AI model/voice/text, Dify and RAG                                                                                | Configure the selected provider in the image's documented configuration, keep credentials private, test speech/image/text responses without physical tools, then inspect allowed action functions and timeouts                                                                              |
| OpenClaw basic/interaction/development                                                                           | Establish the gateway and chosen interaction channel separately from robot bringup. Check the installed version's configuration and tool schema before using a lesson from a different image                                                                                                |
| OpenClaw embodied tasks and sandbox                                                                              | Supply grid map, pose graph, route graph and location mappings first. `m3pro_bringup car_base.launch.py` and `mcp_service.launch.py` expose physical capabilities; activate only after sensor/stop checks. Visual relocalization needs surveyed marker poses                                |
| MCU, Docker, Linux, OpenCV and ROS foundations                                                                   | Use the delivered controller firmware for ROS exercises. Learn peripheral routing and inspect package/configuration changes on a backup copy; preserve the working robot image as a recovery point                                                                                          |

These pathways explain how to use the full topic families without treating all examples as one launch sequence. Some modern lessons use `m3pro_bringup` while older ones use `M3Pro_demo`; check `ros2 pkg list` on the installed image. The repository contains course PDFs rather than a guaranteed single reproducible source build for every image revision. [All official course files](https://github.com/YahboomTechnology/ROSMASTER-M3PRO).

## Troubleshooting and FAQs <a href="#faqs" id="faqs"></a>

| Symptom                               | Read-only diagnosis before changing configuration                                                                                                                               |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| No `/YB_Node`                         | Check power, USB Connect cable, `/dev/myserial`, agent terminal and existing agent container. Distinguish the power-only Type-C output from USB data                            |
| Node visible but remote topics absent | Compare ROS domain, namespace, network and sourced environment on both hosts; verify local messages first                                                                       |
| Only one LiDAR works                  | Identify `/scan0` versus `/scan1`, inspect the matching left-rear/right-front UART harness and check finite ranges before starting fusion                                       |
| Camera launch fails                   | Inspect USB/HUB seating and existing camera process; use `lsusb` and the launch log before replacing drivers                                                                    |
| Arm initially limp                    | Support it; published FAQ describes torque-free startup. Restoring torque is an actuation step, not a passive status query                                                      |
| Poor grasping                         | Separate servo median, camera registration, grasp offset and object geometry. Do not compensate a bad zero by repeatedly changing vision offsets                                |
| Map rotates or stretches              | Test yaw and linear odometry against measured motion, inspect wheel orientation and TF, then use the corresponding calibration lessons                                          |
| Voice response silent                 | Check NX input/output devices and channel balance. A working microphone does not prove speaker routing                                                                          |
| Battery alarm or resets under load    | Stop motion, inspect measured voltage and pack charge; charge with the matched charger. The lesson's10.3 V diagnostic is not a license to run below the pack's specified cutoff |

**Should I change MCU parameters on the first boot?** No. The factory settings are the starting point. `~/config_robot.py` can change domain, namespace, motor PID, yaw PID, odometry scale and servo median values. It writes configuration and requires stopping the agent first. Back up and alter one verified parameter only. [Parameter lesson](https://www.yahboom.net/study/ROSMASTER-M3PRO/15771).

**Can I replace NX with a Pi and retain the disk?** Use the host-specific image and wiring. Pi's5 V power and ROS container instructions differ from the NX's12 V supply and native ROS environment.

**How do I recover the original system?** Back up robot configuration, arm calibration, maps and credentials; identify the actual SSD by capacity/serial before removal. Follow the Orin-specific image recovery lesson with the matching JetPack/image pair. Its screenshots discuss conflicting preliminary filesystem formats; the key operation is writing the correct complete disk image to the correct target, not copying files into a newly formatted partition. Avoid destructive formatting as an exploratory fix. Restore controller firmware separately only when it has been changed: the course supplies SWD and serial procedures, and warns that standalone peripheral firmware must be replaced by the factory micro-ROS image before ROS operation resumes. [Orin recovery and controller lessons](https://github.com/YahboomTechnology/ROSMASTER-M3PRO).

## Downloads and technical documents

| Resource                                         | Direct manufacturer destination                                                                                                            |
| ------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Complete browsable lessons                       | [M3 Pro study portal](https://www.yahboom.net/study/ROSMASTER-M3PRO)                                                                       |
| PDF course source and ZIP download               | [Official repository](https://github.com/YahboomTechnology/ROSMASTER-M3PRO)                                                                |
| Host system images                               | [Robot\_Image\_System\_File](https://drive.google.com/drive/folders/1KO6mW_tliBEXw0oVb6PpXLsZ8g6EHurF)                                     |
| Robot code and controller firmware               | [Code-Firmware](https://drive.google.com/drive/folders/1Tg8UuTXjvQzF8f8O72lfyZo8z5MkiNBw)                                                  |
| Software tools                                   | [Software\_Tools](https://drive.google.com/drive/folders/1fnwhQVmW4oB7oLPazh77vJIARSOILThW)                                                |
| Drivers                                          | [Firmware\_DriverFile](https://drive.google.com/drive/folders/15FtprICahL6W6JhXMORLcbvPCNeHtNLy)                                           |
| Mechanical models                                | [3D\_Model\_File](https://drive.google.com/drive/folders/1h3XF3F35dB8ZMyHR0PDMXYXPyI2LbfiS)                                                |
| Board photographs, power sockets and MCU routing | [Controller course, introduction PDF pages1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/main/18.Control%20Board%20Course) |

The Drive folders are official portal links. Their individual archives were not installed or exhaustively inspected; match each filename/release to NX SUPER 16 GB before downloading or flashing. Course-file access does not establish redistributable licensing for the complete images.

### Additional established resources

These established links supplement the model-specific resources above. Retain the matching model, host and revision when selecting a download.

* [ROS-control tutorial](https://www.yahboom.net/study/ROSMASTER-M3PRO/15792/)

## Yahboom ROSMASTER M3 Pro NX SUPER 16GB: course and API reference

**Supporting reference for** [**ROSMASTER M3 Pro commissioning and development**](https://wiki.openelab.io/robotics/yahboom/rosmaster-m3-pro-development-guide)**.** Exact purchased option: **NX SUPER16GB + 7-inch display, 256GB SSD**, OpenELAB SKU **Yahboom-3000200868**. [Verified option in the existing guide](https://openelab.io/products/yahboom-rosmaster-m3-pro-ros2?variant=47069007020230).

This appendix turns the manufacturer's course PDFs into an engineering reference: what to connect or configure, what to run, what each result means, and which layer to investigate when it fails. It is original synthesis of the official repository at commit `015d065d61069584532778a7ffa9362deb8e9429`, reviewed on 24 November 2026. The PDFs contain multiple software generations; the commit pins documentation, **not** the installed robot image, controller firmware, Python dependencies or cloud services.

### Read this before choosing a software lane

For this NX option, use the **Orin host, Ubuntu 22.04 / ROS 2 Humble** lane. The manufacturer's Raspberry Pi 5 and original Jetson Nano lane runs ROS inside its `m3pro` container; that is a different host configuration. An Orin can still run a **micro-ROS agent container** and a separate **roadnet container**. These containers have different purposes. Keep a record of the image filename, JetPack release, controller firmware version, workspace and calibration before changing any of them.

The older exercises use `~/yahboomcar_ws` for arm/camera packages and `~/M3Pro_ws` for calibration/navigation. Newer embodied examples use `m3pro_bringup`, `multi_brains_pre` and `~/M3Pro_ws/src/m3pro_bringup/config/common.yaml`; older Dify examples use `multi_brains` and `~/M3Pro_ws/multi_brains_file`. Do not move configuration files between these layouts merely because their purposes sound alike. `ros2 pkg prefix PACKAGE`, the launch file and its loaded YAML identify the actual installed lane. These package names come from the lessons, and their presence on an individual SSD remains to be checked.

All robot commands below are for the supplied Humble environment unless explicitly scoped to a development PC, STM32 project or simulation. Terminals are separate when multiple long-running nodes are needed. Run **one** controller/agent/camera owner at a time. Stop the factory gamepad behavior before another publisher controls `/cmd_vel` or arm joints. Camera and perception demonstrations can also initialize the arm; they are not automatically passive just because their title says “detection.”

**Validation boundary:** the work here inspected sources and performed document/static checks. No ROS build or launch, cloud call, firmware flash, calibration, sensor measurement or physical motion was run. Results described below are manufacturer-expected checkpoints, not observations from a tested robot. Vendor source code is analyzed rather than reproduced wholesale. Embedded photographs and diagrams remain available in the cited original PDFs; selected illustrations were visually checked, not every screenshot in every lesson.

### Interface, units and one reproducible diagnostic chain

Start with the delivered battery/host harness, chassis supported and arm workspace clear. On Orin, gamepad startup uses `sh ~/joy_control/joy.sh`; stop its owning window before manual experiments. `sh ~/start_agent.sh` connects the controller only when an agent is not already running. `docker ps` distinguishes a running `ros-agent` from a missing one. The serial transport in the controller course is `/dev/myserial`, **2,000,000 baud**. It is not the 115,200 baud debug UART or 230,400 baud LiDAR UART.

| Interface                                            | Data contract and diagnostic use                                                                                                                                     |
| ---------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/YB_Node`                                           | Factory controller node; inspect with `ros2 node info /YB_Node` before assuming the factory firmware is active                                                       |
| `/cmd_vel`                                           | `geometry_msgs/msg/Twist`: x/y linear velocity in m/s, z angular velocity in rad/s; explicit zero velocity is the stop command, not merely closing a plotting window |
| `/arm_joint`                                         | `arm_msgs/msg/ArmJoint`: servo `id`, target `joint` in degrees, movement `time` in ms                                                                                |
| `/arm6_joints`                                       | `arm_msgs/msg/ArmJoints`: six degree-valued targets plus `time` in ms; joint 6 is the gripper, not an independent IK orientation axis                                |
| `/beep`                                              | `std_msgs/msg/UInt16`; example firmware distinguishes off, continuous and timed operation                                                                            |
| `/rgb`                                               | `std_msgs/msg/ColorRGBA`; inspect the firmware's interpretation rather than assuming a normalized graphics color contract                                            |
| `/battery`                                           | `std_msgs/msg/Float32`, battery voltage in V, not percentage                                                                                                         |
| `/odom_raw`, `/imu/data_raw`                         | `nav_msgs/msg/Odometry`, `sensor_msgs/msg/Imu`; raw feedback precedes EKF/IMU filtering                                                                              |
| `/scan0`, `/scan1`                                   | `sensor_msgs/msg/LaserScan`; left-rear and right-front scanners respectively, ranges in m, angular fields in rad                                                     |
| `/scan_multi`, `/merged_cloud`, `/scan`              | Merged scan, merged cloud, filtered scan; raw scanner range and merger/filter limits are different                                                                   |
| `/camera/color/image_raw`, `/camera/depth/image_raw` | Color/depth `Image`; inspect encoding, registration and calibration before using a color pixel to query depth                                                        |

A useful diagnostic order is **device → agent → raw topic → frame transform → fused data → task**. First inspect `/dev/myserial`, `/YB_Node` and the raw topics. Then inspect `map → odom → base_footprint/base_link` and camera/laser frames with `ros2 run tf2_ros tf2_echo map base_footprint` for the base pose in map coordinates. Finally inspect the merged scan, depth point cloud, detector overlay or navigation action. A visible topic name with no messages does not establish working data. Remote inspection additionally needs the same LAN, domain, compatible QoS and intended namespace.

The detailed lesson citations below support each layer, including exceptions. The citations point to the pinned PDF revision used for this reference.

![Yahboom ROSMASTER M3 Pro family demonstration with arm, display and Mecanum chassis](https://raw.githubusercontent.com/YahboomTechnology/ROSMASTER-M3PRO/015d065d61069584532778a7ffa9362deb8e9429/ROSMASTER_M3PRO.jpg)

Manufacturer family illustration from the pinned repository; pictured props and assembly do not establish the included contents or fitted host of this exact SKU.

Sources: [M3P-008](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/1.ROS%20control.pdf), [M3P-161](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/6.Install%20and%20start%20the%20microros%20agent/6.Install%20and%20start%20the%20microros%20agent.pdf), [M3P-001](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/1.%20Quick%20start%20handle%20to%20control%20the%20car.pdf).

The repository README calls the scanner placement front-left/rear-right, while the dedicated LiDAR and controller-connector lessons say left-rear/right-front. This appendix follows the dedicated interface lessons and requires physical topic identification on the installed unit. [Dedicated LiDAR source](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/1.Lidar%20introduction%20and%20use.pdf).

### Course navigation

* [00. Configuration, operation, calibration and gripper geometry](rosmaster-m3-pro-development-guide.md#m3-course-00)
* [01. Chassis control, odometry calibration and patrol](rosmaster-m3-pro-development-guide.md#m3-course-01)
* [02. LiDAR, SLAM, localization and mobile manipulation](rosmaster-m3-pro-development-guide.md#m3-course-02)
* [03. Depth camera, learned detection and tracking](rosmaster-m3-pro-development-guide.md#m3-course-03)
* [04. Arm kinematics, geometric grasping and coordinated chassis motion](rosmaster-m3-pro-development-guide.md#m3-course-04)
* [05. Road-network mapping, route graphs and recovery](rosmaster-m3-pro-development-guide.md#m3-course-05)
* [06. OpenClaw gateway, models and workspace configuration](rosmaster-m3-pro-development-guide.md#m3-course-06)
* [07. Browser, terminal, voice and messaging interaction](rosmaster-m3-pro-development-guide.md#m3-course-07)
* [08. OpenClaw robot tools, plugins, skills and memory](rosmaster-m3-pro-development-guide.md#m3-course-08)
* [09. OpenClaw embodied tasks: perception, grasp, placement and navigation](rosmaster-m3-pro-development-guide.md#m3-course-09)
* [10. Scenario sandbox: maps, markers and end-to-end tasks](rosmaster-m3-pro-development-guide.md#m3-course-10)
* [11. AI fundamentals and the legacy multi\_brains architecture](rosmaster-m3-pro-development-guide.md#m3-course-11)
* [12. Dify development, credentials, RAG and independent module tests](rosmaster-m3-pro-development-guide.md#m3-course-12)
* [13. Legacy voice interaction and model-directed behavior](rosmaster-m3-pro-development-guide.md#m3-course-13)
* [14. Legacy text interaction without the speech layer](rosmaster-m3-pro-development-guide.md#m3-course-14)
* [15. MediaPipe and gesture-driven arm applications](rosmaster-m3-pro-development-guide.md#m3-course-15)
* [16. MoveIt2 model configuration and simulation](rosmaster-m3-pro-development-guide.md#m3-course-16)
* [17. Multiple robots and formations](rosmaster-m3-pro-development-guide.md#m3-course-17)
* [18. Control board, STM32 peripherals and micro-ROS firmware](rosmaster-m3-pro-development-guide.md#m3-course-18)
* [19. Docker fundamentals and image-specific boundaries](rosmaster-m3-pro-development-guide.md#m3-course-19)
* [20. OpenCV image-processing foundations](rosmaster-m3-pro-development-guide.md#m3-course-20)
* [21. Orin NX host maintenance and recovery](rosmaster-m3-pro-development-guide.md#m3-course-21)
* [22. Linux support skills used by the robot courses](rosmaster-m3-pro-development-guide.md#m3-course-22)
* [23. ROS 2 foundations for engineers and development agents](rosmaster-m3-pro-development-guide.md#m3-course-23)

### 00. Configuration, operation, calibration and gripper geometry <a href="#m3-course-00" id="m3-course-00"></a>

The factory arm has two independent calibrations: mechanical servo median and camera/grasp offset. Correct the median first; a vision offset cannot repair an incorrectly aligned joint. Preserve the previous values and use the original illustrated posture. For a 30 mm block the manufacturer gives a gripper angle of **134°**, whereas a 40 mm block uses **115°**. Sending the 30 mm setting to the 40 mm block can stall and damage servo 6. The full table spans 0–6.4 cm; use the actual object size, not its color label.

Sources: [M3P-003](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/3.%20Robotic%20Arm%20Calibration.pdf), [M3P-007](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/Precautions%20for%20DIY%20Robotic%20Arm.pdf).

#### 1. Quick start handle to control the car <a href="#m3-m3p-001" id="m3-m3p-001"></a>

Insert the gamepad receiver before startup; press **START**, then **R2** to enable control. Orin restarts the behavior with `sh ~/joy_control/joy.sh`. To disable future autostart reversibly, move `~/.config/autostart/joy_control.desktop` to the home directory; restore that file to re-enable it. The Pi/Nano `Docker_M3Pro.sh` and `uros.desktop` alternatives do not describe this NX host. Check control ownership before restarting a behavior that can move both base and arm.

[M3P-001 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/1.%20Quick%20start%20handle%20to%20control%20the%20car.pdf#page=1).

#### 2. Log in to the car and view the code <a href="#m3-m3p-002" id="m3-m3p-002"></a>

Join factory AP `ROSMASTER` with password `12345678`, read the OLED address and connect over the same LAN. The example AP address is `192.168.8.88`; Ethernet has OLED display priority. Orin's account is `jetson`, initial password `yahboom`; case in a translated account table is inconsistent with the lowercase login example. SSH provides a terminal; VNC supplies GUI windows. The factory AP alone does not provide cloud internet. Switch to a routed Wi-Fi connection, re-read the IP and reconnect. Code is under `/home/jetson`, rather than inside the Pi/Nano application container. The headless Xorg dummy-display alternative disables normal DP output until `xorg.conf.backup_dp` is restored; this screen-equipped SKU normally skips it.

[M3P-002 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/2.%20Log%20in%20to%20the%20car%20and%20view%20the%20code.pdf#page=1).

#### 3. Robotic Arm Calibration <a href="#m3-m3p-003" id="m3-m3p-003"></a>

With the arm supported, stop the agent to release its serial port and run `python3 ~/calibrate_arm.py` on Orin. The script prints the controller version and releases torque. Align all six joints with the straight, closed-gripper L-shaped reference photograph, confirm with `y`, and require **state = 1 for every servo**. A missing firmware printout calls for checking serial ownership before proceeding. Restart `sh ~/start_agent.sh` afterward. For offset calibration, launch `ros2 launch M3Pro_demo camera_arm_kin.launch.py`, then `ros2 run M3Pro_demo arm_offset`; this moves the arm. Place the specified **40 × 40 × 40 mm** block inside the blue target and accept with Space. Data goes to `yahboomcar_ws/src/arm_kin/param/offset_value.yaml`; the older installation requires `colcon build --packages-select arm_kin` from that workspace to install it.

[M3P-003 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/3.%20Robotic%20Arm%20Calibration.pdf#page=1).

#### 4. Enter the Docker (Jetson-Nano and Raspberry Pi 5 users, see here) <a href="#m3-m3p-004" id="m3-m3p-004"></a>

This lesson's `bringup_m3pro`, `exec_m3pro` and `shut_m3pro` are the Raspberry Pi/original Jetson Nano **application container** lane. They are retained as compatibility context, not NX startup commands. In that lane the graphical desktop must be active and USB peripherals should be present before container startup; newly attached devices require restarting it. A documented original-Nano multimodal GUI permission workaround opens and closes RViz/rqt first. It is not evidence that the same workaround is needed on NX.

[M3P-004 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/4.%20Enter%20the%20Docker%20\(Jetson-Nano%20and%20Raspberry%20Pi%205%20users%2C%20see%20here\).pdf#page=1).

#### 6. Modify the firmware parameters of the car control board <a href="#m3-m3p-005" id="m3-m3p-005"></a>

`~/config_robot.py` writes factory-firmware configuration through USB Connect and requires the agent stopped. Functions control ROS domain, namespace, motor PID, IMU yaw PID, linear/angular scale and arm median. The documented domain setting range is **0–100**, and the shell's `ROS_DOMAIN_ID` must agree with the controller. Cooperating multi-robot operation intentionally shares a domain and separates namespaces; unrelated robots can use separate domains. Uncomment only the intended setter, run `python3 ~/config_robot.py` and verify read-back. There is a spelling discrepancy between `set_ros_scale_angular` in this overview and `set_ros_scale_angluar` in the calibration lesson: inspect the installed library before calling either. Do not silently substitute one API spelling.

[M3P-005 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/6.%20Modify%20the%20firmware%20parameters%20of%20the%20car%20control%20board.pdf#page=1).

#### 7. Frequently Asked Questions and Precautions <a href="#m3-m3p-006" id="m3-m3p-006"></a>

For an apparently stuck agent, inspect `docker ps` for an existing `ros-agent` before starting a duplicate. Torque-free arm startup is documented behavior; publishing joint targets restores torque and moves the arm. For silent Orin speech, check selected input/output devices and output-channel balance. Ethernet IP taking precedence over Wi-Fi on the OLED is expected. The Pi/Nano missing-device/container-crash diagnostic uses `/dev` listings and belongs to that alternative host lane, not a reason to rebuild the NX image.

[M3P-006 · official PDF, pp. 1–1](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/7.%20Frequently%20Asked%20Questions%20and%20Precautions.pdf#page=1).

#### Precautions for DIY Robotic Arm <a href="#m3-m3p-007" id="m3-m3p-007"></a>

Choose gripper closure from measured object width: 0, 0.5, 1, 1.5, 2, 2.5, 3, 3.5, 4, 4.5, 5, 5.5 and 6 cm correspond to **180, 176, 168, 160, 152, 143, 134, 125, 115, 105, 95, 80 and 57°**; the final 6–6.4 cm band spans 0–57°. This is the vendor's geometry table, not a measured force or payload specification. Confirm that the block dimensions match the chosen lesson before executing its grasp. Stop a stalled gripper rather than increasing its commanded closing angle.

[M3P-007 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/Precautions%20for%20DIY%20Robotic%20Arm.pdf#page=1).

### 01. Chassis control, odometry calibration and patrol <a href="#m3-course-01" id="m3-course-01"></a>

Calibrate angular and linear odometry against independent physical measurements, not against the same TF data used by the test node. The **360° angular** and **1 m linear** exercises are motion experiments. Reserve an open test area and stop other velocity publishers. A `done` message means the node reached its _odometry_ target; only a measured turn/distance establishes the correction. Save one correction at a time through the controller configuration utility, then restart the agent and repeat the physical check.

Sources: [M3P-011](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/4.Angular%20velocity%20calibration.pdf), [M3P-012](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/5.Line%20velocity%20calibration.pdf).

#### 1.ROS control <a href="#m3-m3p-008" id="m3-m3p-008"></a>

Start one agent, inspect `/YB_Node`, then inspect battery, IMU, odometry and each scan separately. A bounded example publishes `/cmd_vel` with x = **0.1 m/s**; send a separate all-zero `Twist` to stop. Arm command `time` is ms, while chassis angular speed is rad/s. Query each message with `ros2 interface show` before constructing your own publisher. The lesson's published-topic table accidentally labels the right-front scan `/rgb`; the dedicated LiDAR course and actual node inspection establish `/scan1`. Its `ls /dev.myserial` diagnostic is also a typo for the documented `/dev/myserial` device.

[M3P-008 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/1.ROS%20control.pdf#page=1).

#### 2.Handle control <a href="#m3-m3p-009" id="m3-m3p-009"></a>

Check receiver input with `sudo jstest /dev/input/js0`; the illustrated controller has eight axes and fifteen buttons. Start `ros2 launch yahboomcar_ctrl yahboomcar_joy_launch.py` and `ros2 run yahboomcar_ctrl yahboom_joy_M3Pro` in separate terminals only after stopping the autostart instance. Left stick drives forward/back/lateral, right stick rotates; stick presses change speed scales. D-pad and face buttons adjust arm joints; SELECT switches the left shoulder buttons between wrist rotation and gripper. Confirm raw button changes before investigating ROS mappings when no motion occurs.

[M3P-009 · official PDF, pp. 1–12](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/2.Handle%20control.pdf#page=1).

#### 3.Keyboard control <a href="#m3-m3p-010" id="m3-m3p-010"></a>

`ros2 run yahboomcar_ctrl yahboom_keyboard` publishes `/cmd_vel`. `i` moves forward, comma backward, `j/l` rotate, and `u/o/m/.` combine translation and rotation. `t` switches translation between X and Y for the Mecanum base. `q/z` scale both speeds by ±10%; `w/x` change linear only and `e/c` angular only; `s` stops keyboard control. Use the terminal with keyboard focus. Observe `/cmd_vel` separately to distinguish missing key input from a controller/firmware problem; do not leave a second teleop publisher running.

[M3P-010 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/3.Keyboard%20control.pdf#page=1).

#### 4.Angular velocity calibration <a href="#m3-m3p-011" id="m3-m3p-011"></a>

Launch `ros2 launch calibration calibrate_angular.launch.py` and `ros2 run rqt_reconfigure rqt_reconfigure`. Refresh and select `calibrate_angular`; set `test_angle`, `speed`, `tolerance`, `odom_angular_scale_correction`, `base_frame`, `odom_frame`, then enable `start_test`. The demonstration targets 360°. Measure the real heading change, alter the scale and toggle the test off/on after committing the field. Stop the agent before persisting the final value through the installed angular-scale setter in `config_robot.py`. The PDF calls it `set_ros_scale_angluar`; check the actual implementation because the configuration overview uses a different spelling.

[M3P-011 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/4.Angular%20velocity%20calibration.pdf#page=1).

#### 5.Line velocity calibration <a href="#m3-m3p-012" id="m3-m3p-012"></a>

Launch `ros2 launch calibration calibrate_linear.launch.py`, select `calibrate_linear` in rqt\_reconfigure and test a measured **1 m** displacement. `test_distance`, `speed`, `tolerance` and `odom_linear_scale_correction` control the test; `Direction` selects longitudinal/lateral motion for Mecanum. The vendor says to increase the correction if the physical displacement falls short. Commit the field and reset/re-enable `start_test`; wait for `done`, then measure. If TF is initially unavailable, stop and retry after the odometry transform exists. Persist through `set_ros_scale_line` only after stopping the agent, then verify a fresh run.

[M3P-012 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/5.Line%20velocity%20calibration.pdf#page=1).

#### 6.Line patrol automatic driving <a href="#m3-m3p-013" id="m3-m3p-013"></a>

Start `M3Pro_demo camera_arm_kin.launch.py` followed by `ros2 run M3Pro_demo follow_line`. The image outlines the detected line; Space begins driving. A front obstacle pauses travel and sounds the buzzer; removal permits resumption, while lost markings produce `Not Found`. For a new line color, press R and drag an ROI entirely inside the colored tape, then require the reset-success message. This chassis lesson references raw `/scan1` for front obstacles, whereas the later arm-removal version uses fused `/scan`; confirm the installed node graph rather than assuming identical pipelines.

[M3P-013 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/6.Line%20patrol%20automatic%20driving.pdf#page=1).

#### 7.Patrol <a href="#m3-m3p-014" id="m3-m3p-014"></a>

Start `ros2 launch patrol patrol.launch.py` and configure `Patrol` through rqt\_reconfigure. `Command` accepts `LengthTest`, `Circle`, `Square` or `Triangle`; `Switch` enables travel and `Set_loop` repeats it. `Linear`, `Angular`, `Length`, `circle_adjust`, `RotationTolerance` and `RotationScaling` control geometry/speed; `ResponseDist` and `LaserAngle` control obstacle gating. The node measures `odom` to `base_footprint`, using `/scan1` to pause and beep. A `transform not ready` failure is a TF/bringup issue, not a reason to raise motor speed or disable obstacle checks.

[M3P-014 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/01.Chassis%20Control%20Course/7.Patrol.pdf#page=1).

### 02. LiDAR, SLAM, localization and mobile manipulation <a href="#m3-course-02" id="m3-course-02"></a>

The T-mini Plus lesson reports **0.05–12 m** raw range, 4,000 samples/s, nominal 6 Hz scanning adjustable 6–12 Hz, 0.54° angular resolution and 20 mm stated ranging accuracy. These are vendor values, not this robot's measured accuracy. Dual-scan merging deliberately clips the usable output to **4 m**. Inspect raw → merged → filtered data in that order.

A persistent map has several forms. Occupancy `.pgm` plus `.yaml` supports grid-map navigation; Cartographer `.pbstream` stores its serialized trajectory; slam\_toolbox pose-graph files support constrained localization; RTAB-Map uses a `.db` database; road routing adds `.geojson` and semantic location YAML. They are not interchangeable. Preserve the grid origin (x/y in m and yaw in rad), resolution in m/pixel, occupied/free thresholds and the frame names with each saved map.

The older Nav2 PDF shows `DifferentialMotionModel`, zero lateral DWB velocities and different local/global robot radii despite the Mecanum chassis. It also mixes `use_sim_time: True` into an otherwise real-time configuration. Treat that listing as an example to audit against the installed `yahboom_M3Pro.yaml`, not a validated omnidirectional configuration. For a real robot, inspect every node's clock and actual footprint; localization, controller and costmaps must use consistent frames and time. The cited roadnet course uses a different planner/controller generation inside its container.

Sources: [M3P-015](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/1.Lidar%20introduction%20and%20use.pdf), [M3P-024](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/2.Dual%20Lidar%20fusion.pdf), [M3P-031](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/9.Navigation2%20single-point%20navigation%20avoid.pdf).

#### 1.Lidar introduction and use <a href="#m3-m3p-015" id="m3-m3p-015"></a>

With factory firmware and one agent, `ros2 topic echo /scan0` exposes `LaserScan` fields. Validate `frame_id`, angular bounds/increment, range bounds and finite range samples before visualization. RViz uses `laser1_frame` for the right-front `/scan1` example. Move a target past each physical sensor while the base stays fixed to confirm left-rear/right-front assignment. Twelve metres is the raw sensor limit; a shorter merged scan is not automatically a sensor defect. Scan frequency and point-sampling frequency are different quantities.

[M3P-015 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/1.Lidar%20introduction%20and%20use.pdf#page=1).

#### 2.Dual Lidar fusion <a href="#m3-m3p-024" id="m3-m3p-024"></a>

`ros2 launch ira_laser_tools merge_multi.launch.py` loads `ira_laser_tools/config/laserscan_merge.yaml`. Its sources are `/scan0 /scan1`, destination frame `base_link`, outputs `/scan_multi` and `/merged_cloud`, range window **0.05–4.0 m**. Inspect overlapping walls before adding `ros2 launch yahboom_laser_filter laser_filter_node.launch.py` to create `/scan`. The filter suppresses configured close body returns below **0.18 m** within an angular region; it must not be interpreted as protection against all nearby obstacles. Wrong TF extrinsics can create doubled walls that no filter parameter should conceal.

[M3P-024 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/2.Dual%20Lidar%20fusion.pdf#page=1).

#### 3.Lidar obstacle avoidance <a href="#m3-m3p-025" id="m3-m3p-025"></a>

Start `ros2 launch yahboom_M3Pro_laser laser_driver.launch.py`, then `ros2 run yahboom_M3Pro_laser laser_Avoidance`. It uses fused `/scan`, `/JoyState` arbitration and `/cmd_vel`; the shown defaults are linear 0.3 m/s, angular 1 rad/s, LaserAngle 45° and ResponseDist 0.55 m. The prose's 0.825 m gate is **1.5 × ResponseDist**, not a contradictory raw range. More than ten gated returns triggers the example obstacle decision. With no obstacle it drives forward; side obstacles bias turning. The printed source repeats a left-sector condition in its supposed right-sector branch: inspect the installed function and test sectors before using this PDF listing as executable code. Two-dimensional scans do not cover drop-offs or all overhangs.

[M3P-025 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/3.Lidar%20obstacle%20avoidance.pdf#page=1).

#### 4.Lidar tracking <a href="#m3-m3p-026" id="m3-m3p-026"></a>

Start `yahboom_M3Pro_laser laser_driver.launch.py` and `ros2 run yahboom_M3Pro_laser laser_Tracker`. It chooses the closest nonzero return inside **±45°**, turns toward it and regulates separation to **0.55 m**, with a **0.1 m** distance dead band in the shown code. It is nearest-object following, not object-identity tracking: a different closer object can become the target. Watch `minDist` and `minDistID` while moving a single test target. The no-candidate code path returns without a new stop publication in the listing; do not assume target loss proves the chassis has stopped.

[M3P-026 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/4.Lidar%20tracking.pdf#page=1).

#### 5.Lidar guard <a href="#m3-m3p-027" id="m3-m3p-027"></a>

Start `laser_driver.launch.py` and `ros2 run yahboom_M3Pro_laser laser_Warning`. It turns to face the closest object within the configured angular sector and sounds `/beep` when distance is at or below **0.55 m**. Unlike `laser_Tracker`, its normal task is rotation and warning rather than linear distance following. The sample has `LaserAngle: 45°`, `ResponseDist: 0.55 m` and a separate angular PID. Check sector orientation and the buzzer state as the target crosses the threshold; a missing return is not an empty-space guarantee.

[M3P-027 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/5.Lidar%20guard.pdf#page=1).

#### 6.Gmapping-SLAM mapping <a href="#m3-m3p-028" id="m3-m3p-028"></a>

Run `ros2 launch slam_mapping gmapping.launch.py` in the installed legacy mapping lane. Start the associated RViz view, drive a slow closed loop with `yahboom_keyboard` and save using `ros2 launch slam_mapping save_map.launch.py`. Inspect the resulting PGM/YAML and a straight wall for consistency. Configuration is `M3Pro_ws/src/M3Pro_core/slam_gmapping/params/slam_gmapping.yaml`; the older installed-file layout requires rebuilding `slam_gmapping` after edits. Roadnet's CycloneDDS setting has a documented Gmapping grid-save limitation; restore the normal DDS lane when using this mapper.

[M3P-028 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/6.Gmapping-SLAM%20mapping.pdf#page=1).

#### 7.Cartographer-SLAM mapping <a href="#m3-m3p-029" id="m3-m3p-029"></a>

Start `slam_mapping bringup.launch.py`, then `cartographer.launch.py` and one `slam_view.launch.py` visualization. Save the grid with `save_map.launch.py`. For later Cartographer relocalization, additionally call `/finish_trajectory` as `cartographer_ros_msgs/srv/FinishTrajectory` with `trajectory_id: 0`, then `/write_state` as `cartographer_ros_msgs/srv/WriteState` with the actual Orin path such as `/home/jetson/yahboom_map.pbstream`. A PGM alone cannot replace that state. The PDF's final `/slam_gmapping` inspection is a copy/paste inconsistency; inspect Cartographer's actual nodes instead.

[M3P-029 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/7.Cartographer-SLAM%20mapping.pdf#page=1).

#### 8.slam\_toolbox mapping <a href="#m3-m3p-030" id="m3-m3p-030"></a>

`ros2 launch slam_mapping slam_toolbox.launch.py` starts mapping; choose either the remote `slam_view slam_view.launch.py` or onboard `slam_mapping slam_view.launch.py`. Drive slowly, close loops and inspect `/slam_toolbox`, its graph and TF. This older lesson saves a grid through `save_map.launch.py`; the newer roadnet lessons use `save_slamtoolbox_map.launch.py` and can separately save a pose graph. Identify which save launch is installed before promising localization from a grid-only export.

[M3P-030 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/8.slam_toolbox%20mapping.pdf#page=1).

#### 9.Navigation2 single-point navigation avoid <a href="#m3-m3p-031" id="m3-m3p-031"></a>

Start `M3Pro_navigation base_bringup.launch.py`, `navigation2.launch.py` and one `nav_rviz.launch.py` (onboard package `M3Pro_navigation`, remote visualization package `slam_view`). Load the intended map, set **2D Pose Estimate**, and require laser/map wall alignment before a nearby **2D Goal Pose**. The global costmap supports planning and the rolling local costmap supports immediate control. In the older YAML example: local size **3 × 3 m**, resolution **0.05 m/cell**, inflation radius **0.3 m**, controller **5 Hz**, goal tolerances **0.15 m / 0.15 rad**. These are example settings, not safety clearances. Rebuild `M3Pro_navigation` after editing a copied install layout; inspect clocks, lateral-velocity restrictions and footprint before using the listing on a real M3 Pro.

[M3P-031 · official PDF, pp. 1–26](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/9.Navigation2%20single-point%20navigation%20avoid.pdf#page=1).

#### 10.Navigation2 multi-point navigation avoid <a href="#m3-m3p-016" id="m3-m3p-016"></a>

Use the same initialized Nav2 stack as single-goal navigation. Select **Waypoint/Nav Through Pose Mode**, enable MarkerArray, add ordered poses with **Nav2 Goal**, then select **Start Waypoint Following**. Inspect position _and orientation_ of each marker. The GUI sends the sequence to the corresponding Nav2 action; it does not remove the need for valid localization or obstacle costmaps. The example YAML allows continuing after a waypoint failure, so record each waypoint result rather than assuming the last arrival proves every stop completed.

[M3P-016 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/10.Navigation2%20multi-point%20navigation%20avoid.pdf#page=1).

#### 11.Repositioning navigation <a href="#m3-m3p-017" id="m3-m3p-017"></a>

Prepare the Cartographer `.pbstream` first. Start base bringup, `M3Pro_navigation cartographer_localization.launch.py`, then **`navigation_launch.py`**, not the ordinary AMCL-containing launch. The custom launch removes AMCL so that Cartographer owns localization. RViz should show a plausible automatically estimated pose; use 2D Pose Estimate when the initial error is large. Inspect the TF tree if walls do not overlap. Running both localization owners risks conflicting `map → odom` transforms.

[M3P-017 · official PDF, pp. 1–11](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/11.Repositioning%20navigation.pdf#page=1).

#### 12.RTAB-Map mapping <a href="#m3-m3p-018" id="m3-m3p-018"></a>

Start `M3Pro_navigation rtab_bringup.launch.py`, place the arm in the lesson's mapping posture only with a clear workspace, then run `rtabmap_launch rtabmap.launch.py` with color, depth, camera-info and `/odom` inputs. The example uses `frame_id:=base_link`, `approx_sync:=true`, maximum sync interval **0.01 s**, `qos:=2` (best effort), queue sizes **50**, visual/ICP odometry disabled and LiDAR subscription enabled. `--delete_db_on_start` starts a fresh map and destroys the previous working database, so preserve it first. Stop cleanly to save; the text's `/home/yahboom/.ros/rtabmap.db` is a workstation example, whereas the active user's `~/.ros/rtabmap.db` is the relevant file to verify on Orin.

[M3P-018 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/12.RTAB-Map%20mapping.pdf#page=1).

#### 13.RTAB-Map navigation <a href="#m3-m3p-019" id="m3-m3p-019"></a>

Copy the completed `~/.ros/rtabmap.db` to a retained location, then run the RGB-D bringup and RTAB-Map in localization mode using `--Mem/IncrementalMemory false`, the explicit `database_path` and the matching RViz configuration. The Orin example uses `/home/jetson/rtabmap.db`; another example uses `/home/yahboom`, so do not copy that path blindly. Start `nav2_bringup navigation_launch.py` for planning/control. Check that the existing cloud/map loads before sending a goal; accidentally retaining `--delete_db_on_start` would erase the map instead of localizing in it.

[M3P-019 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/13.RTAB-Map%20navigation.pdf#page=1).

#### 14.APP mapping navigation <a href="#m3-m3p-020" id="m3-m3p-020"></a>

The phone mapping workflow starts `slam_mapping app_camera.launch.py` plus one of `app_Gmapping.xml`, `app_Cartographer.xml` or `app_Slam_Toolbox.xml`. Connect the app to the actual robot address and configured compressed-image topic, drive slowly, choose **Save Map**, enter a name and submit. For navigation, start base bringup and `M3Pro_navigation app_Navigation2.xml` with the real saved map YAML. The printed `/root/.../tea.yaml` belongs to a container example. Initialize pose in the app before setting a navigation point; a live camera connection alone does not prove the ROS map/navigation connection works.

[M3P-020 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/14.APP%20mapping%20navigation.pdf#page=1).

#### 15.Machine code handling <a href="#m3-m3p-021" id="m3-m3p-021"></a>

This “machine code handling” lesson means AprilTag-based transport. Bring up `camera_arm_kin`, base bringup, `grasp_transport` and `apriltag_transport_V2`; then start Nav2 with the real map and the supplied navigation-status/rotation helpers. Mode keys select **n** navigation, **r** a search rotation, and **b** return to the recorded origin. The robot searches, approaches and grasps a tag block before transporting it. Verify the initial origin and a complete grasp-status handshake before navigation. The PDF contains split `map_dir:=` syntax and container paths: use installed launch arguments and the Orin map path.

[M3P-021 · official PDF, pp. 1–15](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/15.Machine%20code%20handling.pdf#page=1).

#### 16.Color block transport <a href="#m3-m3p-022" id="m3-m3p-022"></a>

Use `grasp_transport` with `color_transport`, the same map/bringup and `get_nav2_status_V2`. R/G/B/Y selects a block color, C calibrates the selected HSV range, and Space enables grasping. Inspect a reliable color mask before allowing approach; illumination changes can invalidate the stored range. Navigation and manipulation are separate stages with completion feedback. The transport example is not the same as the simpler desktop color sorter: its state includes the map destination and return path, which must remain valid while the object is held.

[M3P-022 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/16.Color%20block%20transport.pdf#page=1).

#### 17.Navigation via Pose-Constrained Visual Relocalization <a href="#m3-m3p-023" id="m3-m3p-023"></a>

Save both slam\_toolbox grid and pose graph. In `common.yaml`, match tag family and measured side length; the illustrated localization configuration is **36h11, 0.048 m**, with `tag.ids`/frames explicitly listed. Run `m3pro_bringup record_tag.launch.py`, record each global tag pose only when laser localization is accurate, and retain `aritag_relocation.yaml`. Start `M3Pro_navigation toolbox_location_nav.launch.py relocation:=True`; the modified Nav2 stack disables AMCL in favor of slam\_toolbox localization. `/control_detection` uses `apriltag_localization/srv/ControlDetection` commands **0 = query status, 1 = enable, 2 = disable** (visually confirmed on PDF p.11); verify the same schema on the installed image. Moving a marker requires re-recording it. Despite mixed “ArUco/AprilTag” wording, family/decoder/physical size must agree; do not use the 0.02 m grasp-marker setting here.

[M3P-023 · official PDF, pp. 1–20](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/02.Lidar%20Course/17.Navigation%20via%20Pose-Constrained%20Visual%20Relocalization.pdf#page=1).

### 03. Depth camera, learned detection and tracking <a href="#m3-course-03" id="m3-course-03"></a>

Use the supplied DCW2 driver, not an arbitrary USB-webcam API. Start `ros2 launch orbbec_camera dabai_dcw2.launch.py` once, then inspect `/camera/camera` and color, depth and infrared topics. The introduction reports a depth resolution up to **640 × 400** and working range **0.15–5 m**. Later algorithms resize images to **640 × 480**; that does not change the native optical calibration. Pixel dimensions, registration, intrinsic matrix and depth units must describe the same image used by a detector.

For depth-to-3D reasoning, the underlying projection is X = (u − cx)Z/fx and Y = (v − cy)Z/fy, with all distances in one unit, followed by the calibrated camera-to-end and end-to-base transforms. This equation is an engineering explanation of the lessons' back-projection. Do not use the hardcoded sample intrinsics as a substitute for the installed camera's calibration. Missing depth, a resized unregistered color ROI or a stale arm pose can create a plausible but wrong grasp location.

Sources: [M3P-032](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/1.Dabai_DCW2%20camera%20introduction/1.Dabai_DCW2%20camera%20introduction.pdf), [M3P-049](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/3.Machine%20code%20ID%20sorting/3.Machine%20code%20ID%20sorting.pdf).

#### 1.Dabai\_DCW2 camera introduction <a href="#m3-m3p-032" id="m3-m3p-032"></a>

Inspect `ros2 node info /camera/camera` after the DCW2 launch. Use `ros2 run rqt_image_view rqt_image_view` to select each published image rather than assuming the displayed RGB stream proves depth/IR works. For RViz, use the camera frame and the actual depth/registered point-cloud topic. Compare a matte target in color, depth and cloud before attaching a grasp task. If launch fails, check USB seating, driver logs and an existing camera owner first; changing intrinsics cannot repair a USB disconnect.

[M3P-032 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/1.Dabai_DCW2%20camera%20introduction/1.Dabai_DCW2%20camera%20introduction.pdf#page=1).

#### 2.Depth pseudo-color image <a href="#m3-m3p-033" id="m3-m3p-033"></a>

After camera startup, `ros2 run yahboom_M3Pro_DepthCam GetDepthColor` subscribes to `/camera/depth/image_raw`, converts to an array and produces a false-color rendering using OpenCV scaling/colormaps. `COLORMAP_JET` or another palette changes visualization, not measured depth. Retain invalid-pixel handling and original depth values for computation. A bright false-color patch is not automatically a nearer object unless the chosen scale and colormap are understood.

[M3P-033 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/2.Depth%20pseudo-color%20image/2.Depth%20pseudo-color%20image.pdf#page=1).

#### 3.Depth camera distance measurement <a href="#m3-m3p-034" id="m3-m3p-034"></a>

Run `ros2 run yahboom_M3Pro_DepthCam Measure_Distance`. Click a valid image region; the selected point becomes black and its distance is displayed at the upper left. The mouse callback supplies image x/y, while array access is row y then column x. The lesson's depth examples divide millimetre-like samples by 1000 for metres, but inspect `Image.encoding` and the actual driver contract before adopting that conversion. Check a known measured distance at several pixels; zero/no-return pixels must not be treated as an object at the lens.

[M3P-034 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/3.Depth%20camera%20distance%20measurement/3.Depth%20camera%20distance%20measurement.pdf#page=1).

#### 4.Wood block volume measurement <a href="#m3-m3p-035" id="m3-m3p-035"></a>

Start `M3Pro_demo camera_arm_kin.launch.py`, then `ros2 run M3Pro_demo estimate_volume`. Present the intended block with clean, near-normal depth, select its image frame and press Space. The program estimates center/vertices in a transformed coordinate system to derive dimensions and volume. It depends on both RGB-D geometry and current arm FK; an attractive contour is not a volume measurement without valid depth at the relevant points. Recheck object/plane segmentation, arm pose and depth availability before adjusting a numeric volume scale.

[M3P-035 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/4.Wood%20block%20volume%20measurement/4.Wood%20block%20volume%20measurement.pdf#page=1).

#### 5.Mediapipe gesture recognition <a href="#m3-m3p-036" id="m3-m3p-036"></a>

Run `M3Pro_demo mediapipe_gesture` after the DCW2 launch. Color landmarks are interpreted as a gesture and mapped into predefined arm-joint commands. Inspect the recognition overlay and prescribed gesture list before allowing motion, keeping other arm publishers stopped. This is a gesture-to-action demonstration, not calibrated 3D hand-pose control. Missed landmarks call for better illumination, framing and supported model files before changing servo limits.

[M3P-036 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/5.Mediapipe%20gesture%20recognition/5.Mediapipe%20gesture%20recognition.pdf#page=1).

#### 6.Edge detection <a href="#m3-m3p-037" id="m3-m3p-037"></a>

`ros2 run yahboom_M3Pro_DepthCam edge_detection` begins stopped; Space toggles the behavior. The example examines the resized depth image at **\[row 240, column 320]** and uses a **0.5 m** threshold after `/1000` conversion: excessive depth is interpreted as an edge, generating `Stop!!!`; otherwise it moves and logs `Moving...`. This single-pixel heuristic can fail on invalid/no-return depth or unexpected camera pitch. Verify the arm's viewing posture and test on a supported platform without a real drop before floor operation; the demo is not a complete drop-off sensor.

[M3P-037 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/6.Edge%20detection/6.Edge%20detection.pdf#page=1).

#### 7.YOLOv8 object detection <a href="#m3-m3p-038" id="m3-m3p-038"></a>

Start `ros2 run yahboom_yolov8 yolov8_detect`, then view `/detect_image` in rqt\_image\_view. The node subscribes to the camera color image, performs inference and publishes annotated detections. Confirm class names, bounding boxes and the model file loaded by the installed example. A detected 2D class does not establish object distance or graspability. If images arrive but detections do not, inspect the model/runtime and preprocessing before rebuilding the camera driver.

[M3P-038 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/7.YOLOv8%20object%20detection/7.YOLOv8%20object%20detection.pdf#page=1).

#### 8.Deep learning object tracking <a href="#m3-m3p-039" id="m3-m3p-039"></a>

Start `yahboom_yolov8 yolov8_deep_track.launch.py`, then `yahboom_yolov8 yolov8_track` as shown by the lesson. Select `/detect_image`; publish an **Int16** target ID to `/tracker_id` (the example uses ID 4). A blue box identifies the selected object. The code subscribes to fused `/scan` and steers/approaches to maintain a documented **1.2 m** separation. One prose line says `/track_id`, but the command and subscription use `/tracker_id`. Object IDs are runtime tracker identities, not necessarily detector class IDs, and the behavior commands both chassis and arm.

[M3P-039 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/8.Deep%20learning%20object%20tracking/8.Deep%20learning%20object%20tracking.pdf#page=1).

#### 9. Transformer Model Tracking Algorithm <a href="#m3-m3p-040" id="m3-m3p-040"></a>

The newer Transformer tracker uses host `m3pro_bringup car_base.launch.py` and `super_tracker.launch.py`. Press C, draw the target ROI, then Enter; low confidence turns the box red and triggers search, with reacquisition when the target returns. Inspect `/tracking_bbox` and `tf2_echo base_link roi_object` for the segmented target-cloud centroid. Cancel with `/cancel_track`, type `smart_tracker/srv/CancelTrack`, empty request. The launch references `~/MODELS/tracker/super_track_sim.onnx` and the vendor's Jammy ARM64 `ros-humble-smart-tracker` package; the PDF is not the model weights or source release. Confirm those assets exist on the image before promising this pipeline.

[M3P-040 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/03.Depth%20Camera%20Course/9.%20Transformer%20Model%20Tracking%20Algorithm/9.%20Transformer%20Model%20Tracking%20Algorithm.pdf#page=1).

### 04. Arm kinematics, geometric grasping and coordinated chassis motion <a href="#m3-course-04" id="m3-course-04"></a>

The arm solver is `arm_kin kin_srv`, node `/kinemarics_arm`, service `/get_kinemarics` (retain the manufacturer's spelling), type `arm_interface/srv/ArmKinemarics`. Requests carry target x/y/z in **m**, roll/pitch/yaw in **rad**, current servo angles in **degrees**, and `kin_name: 'fk'` or `'ik'`. Responses carry joint angles and/or pose. A solver response does not move hardware until a separate joint publisher sends it. Servo 6 closes the gripper; the IK example's orientation solution concerns joints 1–5.

Most legacy grasp exercises share this sequence: launch `M3Pro_demo camera_arm_kin.launch.py`; start `grasp_desktop` for tabletop picks or `grasp` for the tracking variant; start the chosen detector; require its initial current-joint message and computed end pose before Space enables a pick. If that one-time startup pose was missed, restart the detector as the lesson prescribes. The completion handshake uses `grasp_done`, detection/pose messages such as `PosInfo` and `Curjoints`, and arm/chassis command topics. Preserve the exact capitalization seen in the installed interfaces.

A camera pixel first becomes camera-frame geometry, then passes through the calibrated end-to-camera matrix and current arm FK into `base_link`. Legacy listings hardcode sample DCW2 intrinsics and mounting matrices; recalibrate when the camera/mount changes. Distance windows below are the examples' decision bands, expressed alongside the millimetre-valued legacy processing. They are not the arm's general reachable workspace.

Sources: [M3P-041](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/1.Robotic%20arm%20solution/1.Robotic%20arm%20solution.pdf), [M3P-049](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/3.Machine%20code%20ID%20sorting/3.Machine%20code%20ID%20sorting.pdf).

#### 1.Robotic arm solution <a href="#m3-m3p-041" id="m3-m3p-041"></a>

Start `ros2 run arm_kin kin_srv`, inspect the service definition, then request FK for the six supplied angles without publishing motion. The documented all-90° example returns approximately **(0.0314, 0.000209, 0.55175) m** relative to `base_link`. Feed its pose back as an IK request and expect approximately 90° for joints 1–5; joint 6 is excluded from the orientation solution and returns 0 in the example. Compare the end transform in `yahboom_M3Pro_description display_launch.py`. This round trip checks the supplied model numerically; it does not establish the physical robot's median calibration or collision-free reach.

[M3P-041 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/1.Robotic%20arm%20solution/1.Robotic%20arm%20solution.pdf#page=1).

#### 2.Robotic arm chassis linkage control <a href="#m3-m3p-048" id="m3-m3p-048"></a>

Start `arm_kin kin_srv`, then `ros2 run M3Pro_demo M3Pro_Dancing`. A Bool on `/start_dancing` enables the coordinated demonstration: the chassis moves **1 m** while the arm compensates backward; triggering again returns the chassis. The client calls FK for current pose and IK for successive compensating targets while publishing `/cmd_vel` and `/arm6_joints`. This is a whole-body motion test, not a stationary arm demo. Reserve both chassis travel and arm reach, and check odometry calibration before expecting the end point to remain spatially stable.

[M3P-048 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/2.Robotic%20arm%20chassis%20linkage%20control/2.Robotic%20arm%20chassis%20linkage%20control.pdf#page=1).

#### 3.Machine code ID sorting <a href="#m3-m3p-049" id="m3-m3p-049"></a>

Use **30 × 30 × 30 mm** tag blocks, `grasp_desktop` and `M3Pro_demo apriltag_detect`. After receiving current joint/FK state, Space enables ID sorting. The sample directly grasps in the **215–225 mm** target band; outside it, the chassis adjusts first. Tag ID recognition, tag orientation and jaw alignment are separate computations, with `compute_joint5.py` setting the wrist rotation. Verify the selected tag's overlay and pose before enabling a pick; no-detection or stale-FK conditions must not fall back to an assumed object coordinate.

[M3P-049 · official PDF, pp. 1–15](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/3.Machine%20code%20ID%20sorting/3.Machine%20code%20ID%20sorting.pdf#page=1).

#### 4.Sorting height abnormality machine code <a href="#m3-m3p-050" id="m3-m3p-050"></a>

`M3Pro_demo apriltag_list` with `grasp_desktop` removes tall tag blocks using a **4 cm** height threshold. The specified props are **30 × 30 × 30 mm** and **30 × 30 × 60 mm**; Space selects the 60 mm object for removal. A **215–225 mm** approach band is used before the pick. Validate height in the transformed base coordinate system, not simply image-box height. If both blocks appear equally tall, investigate table plane, camera/arm calibration and valid depth before lowering the threshold.

[M3P-050 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/4.Sorting%20height%20abnormality%20machine%20code/4.Sorting%20height%20abnormality%20machine%20code.pdf#page=1).

#### 5.Tracking and gripping machine code <a href="#m3-m3p-051" id="m3-m3p-051"></a>

Start `grasp` and `M3Pro_demo apriltag_follow_2D` for the **40 mm cube**. Space starts tracking; the arm follows the visible tag and the chassis advances if the target is beyond **24 cm** from `base_link`, then grasps/places when inside the example range. This is a dynamic follow-and-pick path, distinct from ID sorting on a table. Move the prop slowly and preserve camera visibility; an accepted tag ID alone does not justify executing a stale 3D pick when tracking is lost.

[M3P-051 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/5.Tracking%20and%20gripping%20machine%20code/5.Tracking%20and%20gripping%20machine%20code.pdf#page=1).

#### 6.Color block color sorting <a href="#m3-m3p-052" id="m3-m3p-052"></a>

Use **30 mm colored cubes**, `grasp_desktop` and `M3Pro_demo color_recognize`. R/G/B/Y selects red/green/blue/yellow; C calibrates the current color, and Space enables sorting. Draw calibration ROIs entirely inside the target color under the working light. Read the detected mask and current end pose before action. Some printed legacy code uses Bool for `/beep`, while the factory controller contract is UInt16: do not copy that publisher type without checking the actual installed node and subscriber.

[M3P-052 · official PDF, pp. 1–11](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/6.Color%20block%20color%20sorting/6.Color%20block%20color%20sorting.pdf#page=1).

#### 7.Sorting height abnormality color block <a href="#m3-m3p-053" id="m3-m3p-053"></a>

`M3Pro_demo color_list` removes color blocks higher than **4 cm**, using the specified 30 mm cubes and 30 × 30 × 60 mm rectangular blocks. It shares the tabletop grasp startup and HSV selection/calibration with color sorting. Inspect the 3D height relative to the tabletop before Space. A colored shadow or a merged contour can produce a wrong candidate despite a plausible hue; recheck segmentation and depth before changing the height threshold or the arm offset.

[M3P-053 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/7.Sorting%20height%20abnormality%20color%20block/7.Sorting%20height%20abnormality%20color%20block.pdf#page=1).

#### 8.Tracking and gripping color block <a href="#m3-m3p-054" id="m3-m3p-054"></a>

Start `grasp` and `M3Pro_demo color_follow` for the **40 mm cube**. Select/calibrate a color and enable tracking in the GUI. The text alternates between **26 cm** and **24 cm** approach/grasp descriptions; use the installed code's branch and calibrated target distance rather than turning that prose into a universal threshold. First verify tracking without approach, then one controlled approach and pick. Retain the correct gripper opening for the 40 mm object instead of the 30 mm sorter setting.

[M3P-054 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/8.Tracking%20and%20gripping%20color%20block/8.Tracking%20and%20gripping%20color%20block.pdf#page=1).

#### 9.Wood block shape sorting <a href="#m3-m3p-055" id="m3-m3p-055"></a>

Start `grasp_desktop` and `M3Pro_demo shape_recognize`; enter **Rectangle**, **Square** or **Cylinder** exactly. The props are respectively 30 × 30 × 60 mm, 30 × 30 × 30 mm and the supplied 30 × 30 mm cylinder. Space enables a pick; the example approaches into **190–210 mm** from the base before lowering the gripper. Compare the contour's shape label and stable depth first. Similar projected rectangles under oblique viewing are a classification issue, not an arm-kinematics issue.

[M3P-055 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/9.Wood%20block%20shape%20sorting/9.Wood%20block%20shape%20sorting.pdf#page=1).

#### 10.KCF tracking and gripping objects <a href="#m3-m3p-042" id="m3-m3p-042"></a>

Use `grasp`, `M3Pro_demo KCF_follow` and `M3Pro_KCF KCF_Tracker_Node`. Select an object within the lesson's **7 cm** size limit and tune the gripper angle for its real width; Space begins tracking. The KCF node publishes image/depth-derived `/pos_xyz`, and `reset_flag`/`grasp_done` coordinate recovery and completion. The described approach band is **240–260 mm**. A KCF rectangle can drift to background after occlusion; reset the ROI and re-establish depth rather than continuing to grasp the last tracked center.

[M3P-042 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/10.KCF%20tracking%20and%20gripping%20objects/10.KCF%20tracking%20and%20gripping%20objects.pdf#page=1).

#### 11.Medipipe gesture ID sorting machine code <a href="#m3-m3p-043" id="m3-m3p-043"></a>

Start `grasp_desktop`, `M3Pro_demo apriltagID_gesture` and `M3Pro_demo mediapipe_detect`. A recognized gesture is published as `GesturetId` and selects the tag ID to sort; the tag detector then computes the grasp pose. Confirm both the hand label and matching tag overlay. The reset handshake uses `reset_gesture` after completion or an absent requested tag; the buzzer can indicate that no requested code was found. Keep gesture recognition separate from assumed tag existence.

[M3P-043 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/11.Medipipe%20gesture%20ID%20sorting%20machine%20code/11.Medipipe%20gesture%20ID%20sorting%20machine%20code.pdf#page=1).

#### 12.Mediapipe gesture height sorting machine code <a href="#m3-m3p-044" id="m3-m3p-044"></a>

Use **30 mm tag blocks**, `grasp_desktop`, `apriltagHeight_gesture` and `mediapipe_detect`. The recognized gesture selects a height threshold; blocks exceeding it are grasped. When no block qualifies, the example performs a “head shake” and returns to its recognition posture. Require the initial FK pose and inspect the chosen gesture/height before motion. This exercise converts a discrete hand gesture into a sorting criterion, not the person's hand elevation into a measured robot-frame height.

[M3P-044 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/12.Mediapipe%20gesture%20height%20sorting%20machine%20code/12.Mediapipe%20gesture%20height%20sorting%20machine%20code.pdf#page=1).

#### 13.Desktop tracking and gripping machine code <a href="#m3-m3p-045" id="m3-m3p-045"></a>

Run `grasp_desktop` and `M3Pro_demo apriltag_track_desktop` with **30 mm tag cubes**. It starts in tracking mode; **M** selects tracking and **Space** enables grasping; press M again before the next tracking cycle. Tracking can move both the arm and chassis as the cube is moved across the table. Require current joint/end-pose initialization, then verify the mode and object geometry before a pick. Avoid assuming that “desktop” fixes the base in place; inspect `/cmd_vel` ownership and keep the chassis path available.

[M3P-045 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/13.Desktop%20tracking%20and%20gripping%20machine%20code/13.Desktop%20tracking%20and%20gripping%20machine%20code.pdf#page=1).

#### 14.3D tracking machine code <a href="#m3-m3p-046" id="m3-m3p-046"></a>

`M3Pro_demo apriltag_follow` tracks a **40 mm tag cube** in 3D after Space. The lesson maintains about **17 cm** camera/gripper-to-target separation for useful depth and uses a **3 cm** change gate in its example update logic; its code also clamps a target-height branch to 0.25 m. These are task-specific algorithm choices, not guaranteed global workspace limits. Move the cube slowly in one axis at a time and observe transformed coordinates before combining motion; tag visibility without valid depth cannot produce reliable 3D following.

[M3P-046 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/14.3D%20tracking%20machine%20code/14.3D%20tracking%20machine%20code.pdf#page=1).

#### 15.Line patrol and obstacle removal <a href="#m3-m3p-047" id="m3-m3p-047"></a>

Start `camera_arm_kin`, `grasp_desktop` and `M3Pro_demo follow_line`. Space enables the line patrol. This version stops at an obstacle, then uses arm detection/grasping to remove a supported prop before resuming; it is more than the chassis course's stop-and-beep demo. R and an in-color ROI recalibrate line HSV, with a reset-success message and `LineFollowHSV.text` shown in the legacy source. Its graph uses fused `/scan`; do not substitute the raw `/scan1` assumption from the earlier exercise. Confirm the obstacle is an intended pickable block and that grasp completion is received before allowing patrol to resume.

[M3P-047 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/15.Line%20patrol%20and%20obstacle%20removal/15.Line%20patrol%20and%20obstacle%20removal.pdf#page=1).

### 05. Road-network mapping, route graphs and recovery <a href="#m3-course-05" id="m3-course-05"></a>

Roadnet is a separate container and middleware lane, not an ordinary Humble Nav2 launch copied onto the host. The host's `~/map` is mounted as `/root/map` in that container. A working route requires the grid map, enough slam\_toolbox pose nodes, an annotated `.geojson` graph and accurate current localization. A graph edge expresses where travel is permitted; it is not a physical guarantee of clear space.

Sources: [M3P-056](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/05.Road%20network%20planning%20and%20navigation/1.%20Introduction%20To%20Road%20Network%20Planning/Introduction%20To%20Road%20Network%20Planning.pdf), [M3P-058](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/05.Road%20network%20planning%20and%20navigation/3.%20Road%20Network%20Annotation/Road%20Network%20Annotation.pdf).

#### Introduction To Road Network Planning <a href="#m3-m3p-056" id="m3-m3p-056"></a>

Use `roadnet start` to start the route container and `roadnet bash` to enter it; `roadnet off` stops it. `roadnet DDS on`, `roadnet DDS status` and `roadnet DDS off` manage the documented CycloneDDS switch; refresh the shell afterward. Use this mode only for roadnet, and preserve the original middleware choice. The manufacturer records a Gmapping grid-save issue while CycloneDDS is active. Container shutdown is a recovery action, not a substitute for checking whether the last robot velocity command was brought to zero.

[M3P-056 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/05.Road%20network%20planning%20and%20navigation/1.%20Introduction%20To%20Road%20Network%20Planning/Introduction%20To%20Road%20Network%20Planning.pdf#page=1).

#### Build A Pose Map <a href="#m3-m3p-057" id="m3-m3p-057"></a>

Start the agent and `slam_mapping slam_toolbox.launch.py`; use teleop to cover the intended operating space. In RViz enable MarkerArray and confirm there are pose nodes in every area that will later be localized. Save a grid with `save_slamtoolbox_map.launch.py` and save the pose graph separately with `map_type:=posegraph`. Default map name is `map`, directory `~/map`; `map_name` overrides it. A visually good grid with sparse pose nodes can still localize poorly in those areas.

[M3P-057 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/05.Road%20network%20planning%20and%20navigation/2.%20Build%20A%20Pose%20Map/Build%20A%20Pose%20Map.pdf#page=1).

#### Road Network Annotation <a href="#m3-m3p-058" id="m3-m3p-058"></a>

Enable the roadnet DDS lane, start host localization with `M3Pro_navigation toolbox_location_nav.launch.py gui:=False`, then enter roadnet and run `road_net_route route_tool.launch.py yaml_filename:=map.yaml`. Use **Publish Point** at `base_footprint` and **Create** to add waypoints, then add directed/bidirectional edges according to actual allowed travel. Reinitialize the pose when scan/map alignment drifts before recording more points. Save the graph and reload it to verify node IDs and edge directions; screen markers that were never saved are not a route file.

[M3P-058 · official PDF, pp. 1–14](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/05.Road%20network%20planning%20and%20navigation/3.%20Road%20Network%20Annotation/Road%20Network%20Annotation.pdf#page=1).

#### Planning And Navigation Between Waypoints <a href="#m3-m3p-059" id="m3-m3p-059"></a>

On the host run `m3pro_bringup car_base.launch.py`; in roadnet start `road_net_route roadnet_nav2.launch.py` with the lesson's RViz configuration. `/road_net_nav_id` accepts `std_msgs/msg/Int16MultiArray` with **\[start ID, destination ID]**, illustrated by `[0,7]`. If the robot begins off the graph, it first joins a nearby edge before following the graph. The bridge converts route goals and a `TwistStamped` velocity path to the chassis `Twist` contract. Tune the container's `nav2_roadnet.yaml`, not the older host YAML. The illustrated local/global footprint is a 0.28 × 0.22 m rectangle plus padding 0.0616 m; verify the real assembly and carried object before adopting it.

[M3P-059 · official PDF, pp. 1–16](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/05.Road%20network%20planning%20and%20navigation/4.%20Planning%20And%20Navigation%20Between%20Waypoints/Planning%20And%20Navigation%20Between%20Waypoints.pdf#page=1).

#### Road Network Navigation In Any Pose <a href="#m3-m3p-060" id="m3-m3p-060"></a>

`/road_net_nav` accepts a `geometry_msgs/msg/PoseStamped` destination: travel follows the graph to the vicinity, then converges on the requested x/y/yaw. Obtain a surveyed example pose with `ros2 run tf2_ros tf2_echo map base_footprint`; positions are m and orientation is a quaternion, not a yaw scalar in its z field. The PDF omits `/msg` in one CLI type and shows placeholder coordinates: resolve the installed type and replace the whole pose with a valid frame-aware value. Test the graph-only goal before adding exact final orientation.

[M3P-060 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/05.Road%20network%20planning%20and%20navigation/5.%20Road%20Network%20Navigation%20In%20Any%20Pose/Road%20Network%20Navigation%20In%20Any%20Pose.pdf#page=1).

#### Path Re-planning <a href="#m3-m3p-061" id="m3-m3p-061"></a>

Add a real alternate edge, save the graph, then navigate between node IDs while observing the costmap. The example obstacle forces retreat to the previous waypoint before replanning; leave that retreat corridor clear. In `RoadNetwork/volumes/code_ws/src/road_net_route/config/nav2_roadnet.yaml`, `route_bridge` shows `COST_THRESHOLD: 60` and `PATH_OBSTACLES_THRESHOLD: 5`. Both gate the count of high-cost path samples. Publish Point queries illustrate free cost 0 and obstacle cores 99–100 in that display; do not confuse these with another costmap encoding. Inspect the actual displayed values and graph connectivity before changing thresholds to force a blocked route through.

[M3P-061 · official PDF, pp. 1–13](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/05.Road%20network%20planning%20and%20navigation/6.%20Path%20Re-planning/Path%20Re-planning.pdf#page=1).

### 06. OpenClaw gateway, models and workspace configuration <a href="#m3-course-06" id="m3-course-06"></a>

These lessons describe the OpenClaw version preinstalled in a particular vendor image; the repository does not pin a universal OpenClaw binary release. Record `openclaw --version` before editing configuration and inspect the installed CLI's help for flags. Provider/model examples in the PDFs are historical examples, not verified current availability, prices or account entitlements. Validate a text-only model response before connecting hardware tools.

Sources: [M3P-068](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/06.OpenClaw%20Basic%20Course/6.%20OpenClaw%20Common%20CLI%20Commands/Open%20Claw%20Common%20CLI%20Commands.pdf).

#### Introduction to Open Claw <a href="#m3-m3p-062" id="m3-m3p-062"></a>

OpenClaw is the self-hosted gateway between chat channels and an agent; the robot's ROS/MCP stack is a separate execution layer. A single gateway can route several channels while retaining sender/session context. Commission it in layers: working gateway, reachable model, one interactive channel, then robot MCP. A connected chat window proves neither the model provider nor the physical tool service works. Keep the gateway on the intended host and record the robot service endpoint separately from the cloud model base URL.

[M3P-062 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/06.OpenClaw%20Basic%20Course/1.%20Introduction%20to%20OpenClaw/Introduction%20to%20Open%20Claw.pdf#page=1).

#### Open Claw Core Concepts <a href="#m3-m3p-063" id="m3-m3p-063"></a>

Distinguish agent reasoning, tools that perform atomic operations, skills that describe a multi-step workflow, sessions that retain conversation context, and memory persisted in files or a retrieval index. The lesson describes daily files under `memory/` and long-lived memory, plus gateway/channel orchestration. When a task behaves differently after a new conversation, compare session state, loaded skill and persistent memory rather than changing the chassis controller. A remembered instruction or location name must still resolve to a valid, current robot/map state.

[M3P-063 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/06.OpenClaw%20Basic%20Course/2.%20OpenClaw%20Core%20Concepts/Open%20Claw%20Core%20Concepts.pdf#page=1).

#### Open Claw API-KEY Configuration <a href="#m3-m3p-064" id="m3-m3p-064"></a>

Use `openclaw onboard` to configure the chosen provider, base URL and your own API credential. `openclaw models list` checks the registered models; `openclaw tui` provides a minimal response test. Match provider region and endpoint to the account; a credential for a different region can fail despite being syntactically valid. For 401/invalid-key errors, inspect provider, endpoint and account quota before troubleshooting ROS. Do not reuse credential-looking strings printed in the PDF. This appendix deliberately omits them.

[M3P-064 · official PDF, pp. 1–12](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/06.OpenClaw%20Basic%20Course/3.%20OpenClaw%20API-KEY%20Configuration/Open%20Claw%20API-KEY%20Configuration.pdf#page=1).

#### Open Claw Switch Models <a href="#m3-m3p-065" id="m3-m3p-065"></a>

`openclaw models set PROVIDER/MODEL` selects the primary model, and `openclaw models status` verifies it. The configuration fields are `agents.defaults.model.primary` and optional allowlist `agents.defaults.models` in `~/.openclaw/openclaw.json`. If the model is absent from the allowlist, choosing it in the TUI may not be sufficient. Two PDFs of this lesson show different CLI edits; the more explicit variant uses a JSON object with `--strict-json --merge`. Inspect the installed CLI before applying that syntax. Preserve the old JSON and verify a response after switching; a successful configuration edit alone does not validate inference.

[M3P-065 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/06.OpenClaw%20Basic%20Course/4.%20OpenClaw%20Switch%20Models/Open%20Claw%20Switch%20Models.pdf#page=1).

#### OpenClaw Switch Models <a href="#m3-m3p-066" id="m3-m3p-066"></a>

`openclaw models set PROVIDER/MODEL` selects the primary model, and `openclaw models status` verifies it. The configuration fields are `agents.defaults.model.primary` and optional allowlist `agents.defaults.models` in `~/.openclaw/openclaw.json`. If the model is absent from the allowlist, choosing it in the TUI may not be sufficient. Two PDFs of this lesson show different CLI edits; the more explicit variant uses a JSON object with `--strict-json --merge`. Inspect the installed CLI before applying that syntax. Preserve the old JSON and verify a response after switching; a successful configuration edit alone does not validate inference.

[M3P-066 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/06.OpenClaw%20Basic%20Course/4.%20OpenClaw%20Switch%20Models/OpenClaw%20Switch%20Models.pdf#page=1).

#### Open Claw System Prompt Words <a href="#m3-m3p-067" id="m3-m3p-067"></a>

OpenClaw workspace files live under `~/.openclaw/workspace`: `AGENTS.md` governs operation, `SOUL.md` behavior, `TOOLS.md` local tool conventions, `USER.md` user context, `MEMORY.md` long-term facts, `HEARTBEAT.md` periodic guidance, and bootstrap/identity files establish the agent. Keep modifications local to the intended agent workspace; restart with `openclaw gateway restart` as the lesson requires. Robot instructions should specify units, coordinate frame, completion checks and failure handling. They do not change MCU limits or make unavailable tools executable.

[M3P-067 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/06.OpenClaw%20Basic%20Course/5.%20OpenClaw%20System%20Prompt%20Words/Open%20Claw%20System%20Prompt%20Words.pdf#page=1).

#### Open Claw Common CLI Commands <a href="#m3-m3p-068" id="m3-m3p-068"></a>

Use `openclaw gateway status` before start/stop/restart; use `models list/status`, `skills list`, `plugins list`, `channels list` and `sessions` to isolate the affected layer. `openclaw logs --follow` reveals ongoing errors; Ctrl+C stops log following, not the gateway. `openclaw configure` revisits setup, while `onboard` is the initial guided configuration. Check `--version` and `--help` before relying on a photographed command. A channel connected successfully with repeated model errors points to provider configuration, not necessarily gateway process health.

[M3P-068 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/06.OpenClaw%20Basic%20Course/6.%20OpenClaw%20Common%20CLI%20Commands/Open%20Claw%20Common%20CLI%20Commands.pdf#page=1).

### 07. Browser, terminal, voice and messaging interaction <a href="#m3-course-07" id="m3-course-07"></a>

The web gateway, robot MCP and audio bridge have separate addresses, credentials and processes. In the newer voice lane, `multi_brains_pre_setting.yaml` is application configuration; ROS node overrides belong in `common.yaml`. Preserve that separation when troubleshooting. The examples' default local tokens/passwords are provisioning examples and should be replaced before exposing the gateway to other machines.

Sources: [M3P-071](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/07.OpenClaw%20Interaction%20Method/3.%20OpenClaw%20Voice%20Dialogue%20Interaction/Voice%20Dialogue%20Interaction.pdf).

#### Webchat Interaction <a href="#m3-m3p-069" id="m3-m3p-069"></a>

Configure `gateway.controlUi.allowedOrigins` in `~/.openclaw/openclaw.json` for the actual web origin(s), including the robot's address and **port 18789**, then restart the gateway. Connect WebChat on the same LAN and use the configured gateway token. If the page does not load, check gateway status, current robot IP and port before changing ROS. An origin rejection after an IP change is resolved by correcting the allowed origin, not disabling all origin checks. A loaded dashboard and a model response are separate checkpoints.

[M3P-069 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/07.OpenClaw%20Interaction%20Method/1.%20OpenClaw%20Webchat%20Interaction/Webchat%20Interaction.pdf#page=1).

#### Tui Interaction <a href="#m3-m3p-070" id="m3-m3p-070"></a>

`openclaw tui` connects an interactive terminal to the gateway. Confirm gateway status and one model with `models list/status` before sending a simple text request. Connection refused/stuck connecting indicates gateway/port trouble; 401 points to provider credentials; a quota error needs the model account checked. The TUI is useful when the browser is inaccessible because it removes the web-origin layer while retaining the same gateway/model. Restart the gateway only after recording the relevant error, so the failure cause is not lost.

[M3P-070 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/07.OpenClaw%20Interaction%20Method/2.%20OpenClaw%20Tui%20Interaction/Tui%20Interaction.pdf#page=1).

#### Voice Dialogue Interaction <a href="#m3-m3p-071" id="m3-m3p-071"></a>

Copy the appropriate hidden English/Chinese example into `M3Pro_ws/src/m3pro_bringup/config/multi_brains_pre_setting.yaml` and configure your own audio-provider credential with `robot_config multi_brains_pre set ...`. Start `m3pro_bringup mcp_service.launch.py`, `multi_brains_pre asr_detect` and `multi_brains_pre openclaw_bridge` in separate terminals for streaming text. `USE_ONLINE_ASR` selects cloud versus local recognition; voice tags `<tts>…</tts>` select the spoken summary. `robot_config voice-tag status/remove` checks/disables tag behavior. ROS parameters `enable_wakeup_voice` and `enable_voice_reply` independently control wake and reply speech; pass the intended `common.yaml` as `--params-file`. This image uses symlink installation for `m3pro_bringup`, so these YAML edits need no rebuild, unlike older copied-package lessons. Missing `.onnx` plus matching `.onnx.json` files break local speech even when microphone capture works.

[M3P-071 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/07.OpenClaw%20Interaction%20Method/3.%20OpenClaw%20Voice%20Dialogue%20Interaction/Voice%20Dialogue%20Interaction.pdf#page=1).

#### WhatsApp Interaction <a href="#m3-m3p-072" id="m3-m3p-072"></a>

The WhatsApp lesson links a device using `openclaw channels login --channel whatsapp`, then a phone's **Linked Devices → Link New Device** QR flow. Restart the gateway and configure the intended allowlisted number before a self-message test. This is account/channel setup, not a robot-control requirement for WebChat or TUI. Check channel status and the recipient/device binding independently of MCP. No WhatsApp pairing, message sending or account change was performed for this appendix.

[M3P-072 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/07.OpenClaw%20Interaction%20Method/4.%20OpenClaw%20WhatsApp%20Interaction/WhatsApp%20Interaction.pdf#page=1).

#### Common Errors And Solutions <a href="#m3-m3p-073" id="m3-m3p-073"></a>

For missing voice configuration, check the exact file path and YAML indentation before replacing packages. Audio-open failures point to the selected microphone and host routing; no speech/timeout can occur with the wrong input or VAD settings. Local TTS needs both model files; online TTS/ASR needs the matching provider credentials and reachable endpoint. A Dify error can mean its app key differs from `DIFY_API_KEY`, not that the robot serial port failed. For robot-side failures, inspect node/topic/service/action availability and TF, then repeat the smallest affected operation.

[M3P-073 · official PDF, pp. 1–19](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/07.OpenClaw%20Interaction%20Method/Common%20Errors%20And%20Solutions.pdf#page=1).

### 08. OpenClaw robot tools, plugins, skills and memory <a href="#m3-course-08" id="m3-course-08"></a>

The newer MCP workflow is **one micro-ROS agent → `m3pro_bringup car_base.launch.py` → `mcp_service.launch.py` → optional `multi_brains_pre openclaw_bridge`**. The robot-control plugin's documented endpoint is **`http://localhost:8000/mcp`**. Verify the installed endpoint and tool schema before remote use; localhost refers to the machine running the client. A tool's schema range is an accepted-input range, not an independently verified hardware rating.

The function summary has an important inconsistency: it labels gripper 180° as open and 0° as closed, while the mechanical gripper-width lesson uses **180° for zero gap**. The fixed-placement chapter also says higher angle closes further. Do not infer gripper direction from the MCP summary. Resolve the installed joint mapping with the actual empty gripper and the controller/geometry documentation before enabling automated closing. This discrepancy remains an explicit hardware-verification boundary.

Sources: [M3P-075](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/1.%20OpenClaw%20connects%20to%20the%20MCP%20interface%20of%20the%20robot/MCP%20Function%20Summary/MCP%20Function%20Summary.pdf), [M3P-007](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/00.Configuration%20and%20Operation%20Guide/Precautions%20for%20DIY%20Robotic%20Arm.pdf).

#### 1. OpenClaw connects to the MCP interface of the robot <a href="#m3-m3p-074" id="m3-m3p-074"></a>

`mcp_service.py` initializes the controller-backed FastMCP server; `mcp_tools/mcp_action.py` registers functions using `@mcp.tool`, Pydantic input fields and timeouts. Request/response dataclasses are in `message/mcp_message.py`. The shown `MoveWithSpeed` tool accepts x/y/z speed fields within ±2.5 and duration in seconds, with a **30 s tool timeout**. Those schema defaults (1.5) are unsuitable as an assumed first-run speed. Start with read-only joint/pose tools and explicit low motion inputs only after chassis checks. Distinguish tool-call timeout, requested motion duration and robot feedback timeout.

[M3P-074 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/1.%20OpenClaw%20connects%20to%20the%20MCP%20interface%20of%20the%20robot/1.%20OpenClaw%20connects%20to%20the%20MCP%20interface%20of%20the%20robot.pdf#page=1).

#### MCP Function Summary <a href="#m3-m3p-075" id="m3-m3p-075"></a>

The summary defines movement, arm, perception, map, waste, speech, tracking and line tools. `Move` takes distance in m plus forward/backward/left/right; `Rotate` takes an angle, whose installed unit must match the CLI/tool description. `ControlSixArmJoint` accepts degree-valued joints with shown limits **\[0,180], \[-5,180], \[-10,180], \[-50,180], \[0,180], \[0,180]** and runtime **0–2000 ms**, default 1500 ms. `Pick` takes image bounding-box corners, while `Place` takes metric coordinates. `GetBbox` returns bbox plus a verification image; `GetPlacePoint` returns a target point plus verification image. Success/failure can return different dataclass/dict shapes, so inspect status before reading image or coordinate fields. The summary's gripper-open/closed polarity conflicts with the mechanical table and is unresolved.

[M3P-075 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/1.%20OpenClaw%20connects%20to%20the%20MCP%20interface%20of%20the%20robot/MCP%20Function%20Summary/MCP%20Function%20Summary.pdf#page=1).

#### 2. Robot CLI Command Tool <a href="#m3-m3p-079" id="m3-m3p-079"></a>

`robot_control list-tools` discovers the installed tools; `robot_control call-tool GetCurrentArmJointAngles` is the lesson's useful first read. CLI flags use kebab case, for example `Move --distance 0.5 --direction forward`; this last example actuates the base. Inspect response status before chaining another tool. The CLI calls the same MCP/controller functions as the agent, providing a way to distinguish model planning from robot execution errors. A successful CLI list proves service discovery, not that a grasp, map or camera is ready.

[M3P-079 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/2.%20Robot%20CLI%20Command%20Tool/2.%20Robot%20CLI%20Command%20Tool.pdf#page=1).

#### CLI\_en <a href="#m3-m3p-080" id="m3-m3p-080"></a>

The CLI reference maps tool parameters to flags: `ControlSingleArmJoint --arm-joint-id ... --angle ... --runtime ...`, `Pick --x1 ... --y1 ... --x2 ... --y2 ...`, and `Place --place-x ... --place-y ... --place-z ...`. `RecordMapLocation` needs a name and symbol; `Navigation` needs the recorded location; `GetBbox`/`GetPlacePoint` use `--query`. `TargetTrack` takes an ROI or cancellation command, while `GetTargetDist` takes a description. Query the installed schema for accepted cancellation values and angle units instead of deriving them from placeholder syntax. These are templates with explicit required inputs, not commands to paste with angle brackets intact.

[M3P-080 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/2.%20Robot%20CLI%20Command%20Tool/CLI%20Command%20Summary/CLI_en.pdf#page=1).

#### 3. Robot control plugin tool <a href="#m3-m3p-081" id="m3-m3p-081"></a>

The `robot-control` OpenClaw plugin wraps an MCP client pointing to `http://localhost:8000/mcp` and exposes robot functions to the agent. Verify it with `openclaw plugins list`, then check the server before issuing a read-only tool. If the CLI succeeds but the agent cannot see tools, inspect plugin loading and endpoint configuration. If both fail, inspect the robot MCP service and underlying ROS interfaces. Do not replace the gateway model key in an attempt to repair an unreachable local MCP endpoint.

[M3P-081 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/3.%20Robot%20control%20plugin%20tool/3.%20Robot%20control%20plugin%20tool.pdf#page=1).

#### 4. Reply bridge plugin tool <a href="#m3-m3p-082" id="m3-m3p-082"></a>

The reply bridge connects agent responses to robot speech through `multi_brains_pre openclaw_bridge`, after `mcp_service.launch.py`. A complete text reply can coexist with a silent bridge when no `<tts>` segment is present or voice reply is disabled. Check bridge logs, the selected local/cloud TTS backend and audio output independently of motion tools. Returning a model answer is not the same as completing an actuator operation; use the tool result to determine task state.

[M3P-082 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/4.%20Reply%20bridge%20plugin%20tool/4.%20Reply%20bridge%20plugin%20tool.pdf#page=1).

#### 5. OpenClaw multimodal vision <a href="#m3-m3p-083" id="m3-m3p-083"></a>

`SeeWhat` captures the current camera image; `GetBbox --query ...` asks the configured multimodal application for a target rectangle; `GetPlacePoint` resolves a relative placement description to a geometric point. Review their returned verification images before action. The plugin's `SeeWhat_channels` and WhatsApp number control where captured images are presented; restart the gateway after configuration changes. A vision-capable model and the correct Dify image workflow are needed for localization, not merely any text model. An absent target must remain a failed localization instead of a fabricated coordinate.

[M3P-083 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/5.%20OpenClaw%20multimodal%20vision/5.%20OpenClaw%20multimodal%20vision.pdf#page=1).

#### 6. OpenClaw chassis control <a href="#m3-m3p-084" id="m3-m3p-084"></a>

`MoveWithSpeed`, `Move` and `Rotate` connect to `set_cmdvel`, odometry-based translation and odometry-based rotation in `action_controller.py`. Specify velocity duration in **seconds**, translation in **metres** and check the installed rotation contract before use. The source repeatedly reads odometry, tests tolerance/timeouts and sends a stop at completion. Confirm separate longitudinal/lateral direction signs on the Mecanum base before combined movement. A time-limited velocity command and a distance-regulated command have different stopping criteria and different sensitivity to wheel slip.

[M3P-084 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/6.%20OpenClaw%20chassis%20control/6.%20OpenClaw%20chassis%20control.pdf#page=1).

#### 7. OpenClaw robotic arm control <a href="#m3-m3p-085" id="m3-m3p-085"></a>

Use `GetCurrentArmJointAngles`/`GetEndEffectorPose` before an arm command. Six-joint and single-joint tools publish the factory message types; `runtime` is **milliseconds**, not an angular rate. `AdjustCameraView` applies incremental degree changes (the summary recommends 5–10° steps) and returns a new view; `InitArmPose` moves to the configured initial posture in `common.yaml`. Query actual joint limits and gripper polarity before physical use; the per-joint schema and mechanical width table must agree with the installed mapping.

[M3P-085 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/7.%20OpenClaw%20robotic%20arm%20control/7.%20OpenClaw%20robotic%20arm%20control.pdf#page=1).

#### 8. OpenClaw skills development <a href="#m3-m3p-086" id="m3-m3p-086"></a>

A robot skill is a workflow under `~/.openclaw/workspace/skills/NAME/SKILL.md`, with metadata and executable-tool guidance. The five factory skills cover pick/place, waste sorting, navigation, vision and combined tasks. For a new workflow define tools, frames, input units, success criteria, bounded retries and recovery; restart the gateway and enable it in Agent Skills. For example, a stock check should capture a fresh image, resolve a target, inspect the verification image and report absence before attempting replenishment. A skill file orchestrates tools; it does not create a detector, a map or a physical capability that the robot lacks.

[M3P-086 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/8.%20OpenClaw%20skills%20development/8.%20OpenClaw%20skills%20development.pdf#page=1).

#### 9. OpenClaw timed tasks <a href="#m3-m3p-087" id="m3-m3p-087"></a>

The timing lesson creates scheduled robot work through OpenClaw and reviews it in WebChat's **Scheduled Tasks** list. Start MCP and optional speech bridge first; inspect schedule details, task description, next execution and enable state. Test the task manually in its intended environment before enabling recurrence. The lesson is scheduling orchestration, not a continuously monitored safety system. No recurring job was created here; successful schedule creation would not establish successful physical execution or recovery after a disconnected sensor.

[M3P-087 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/9.%20OpenClaw%20timed%20tasks/9.%20OpenClaw%20timed%20tasks.pdf#page=1).

#### 10. OpenClaw multi-agent intelligent agent <a href="#m3-m3p-076" id="m3-m3p-076"></a>

`openclaw agents add AGENT_ID` creates an isolated workspace and session history; `openclaw agents list --bindings` shows routing, and `channels status --probe` checks the channel. Put agent-specific guidance in its own workspace rather than modifying the main agent's files accidentally. Restart the gateway after binding changes and confirm which agent receives a harmless test request. Separate agent memory does not imply separate robots: if multiple agents share the same robot-control endpoint, they still need one physical command owner.

[M3P-076 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/10.%20OpenClaw%20multi-agent%20intelligent%20agent/10.%20OpenClaw%20multi-agent%20intelligent%20agent.pdf#page=1).

#### 11. OpenClaw active interaction <a href="#m3-m3p-077" id="m3-m3p-077"></a>

The active-interaction lesson implements exception-handling skills, such as material shortage. A skill detects an observed condition, presents supported alternatives and follows the selected recovery. It depends on working perception/tools; the example does not add real industrial temperature/gas sensors or validated emergency procedures. Define a concrete observation and completion check rather than scheduling vague perpetual “monitoring.” A useful adaptation is to report the missing block, ask for the intended source, then re-observe before retrying a pick; do not invent stock or move blindly after a failed detection.

[M3P-077 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/11.%20OpenClaw%20active%20interaction/11.%20OpenClaw%20active%20interaction.pdf#page=1).

#### 12. OpenClaw vector memory <a href="#m3-m3p-078" id="m3-m3p-078"></a>

Vector memory uses `agents.defaults.memorySearch.provider`, `remote.baseUrl`, `model` and `remote.apiKey` in OpenClaw configuration. The lesson's OpenRouter/OpenAI-compatible embedding model is an example; it must be supported by the chosen endpoint. After gateway restart, run `openclaw memory status --deep`, build the index with `memory index --force` and query a known phrase with `memory search`. A chat model credential does not automatically grant an embedding model. Verify indexed memory and returned passage before relying on a remembered location; current map poses still come from robot localization.

[M3P-078 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/12.%20OpenClaw%20vector%20memory/12.%20OpenClaw%20vector%20memory.pdf#page=1).

#### Summary of Common Errors and Solutions <a href="#m3-m3p-088" id="m3-m3p-088"></a>

Separate configuration/model errors from robot execution errors. A missing YAML path or parser error is repaired in the correct image lane; speech failures need the actual model/audio files and provider. `GetBoxCenter: no valid data` indicates inadequate depth/target geometry, not a reason to invent a point. Inspect topics, services, actions and TF for the failing tool, then test that tool directly through the CLI. Preserve the original failed response and verification image to distinguish absent target, stale image and out-of-reach position.

[M3P-088 · official PDF, pp. 1–18](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/08.OpenClaw%20Development/Summary%20of%20Common%20Errors%20and%20Solutions.pdf#page=1).

### 09. OpenClaw embodied tasks: perception, grasp, placement and navigation <a href="#m3-course-09" id="m3-course-09"></a>

For these newer tasks start one agent, `m3pro_bringup car_base.launch.py`, `mcp_service.launch.py` and optional speech bridge. Navigation tasks also require roadnet, the correct DDS lane and surveyed map locations. Keep `common.yaml` from this image with the robot; the positional offsets here are not replacements for the older `arm_kin/param/offset_value.yaml` calibration.

A robust closed loop is **fresh observation → verified target/pose → reachable approach → one action → fresh verification**. It is an engineering adaptation of the source workflows. If the target or depth disappears, reacquire it; a natural-language model cannot supply missing depth. Sample offsets are hypotheses to check in millimetre-scale increments, never hardware test results.

Sources: [M3P-090](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/2.%20OpenClaw%20robotic%20arm%20tracking%20and%20grasping/OpenClaw%20Robotic%20Arm%20Tracking%20And%20Grasping.pdf).

#### 1. OpenClaw target tracking <a href="#m3-m3p-089" id="m3-m3p-089"></a>

`GetBbox` supplies the initial ROI to `TargetTrack`; cancellation stops the tracking thread and calls the underlying cancel service. The source rejects tracking data older than **0.5 s**, computes image-center errors relative to **(320,240)** and pauses low-confidence updates; the code gate is **0.08**, while narrative text mentions resuming above 0.1. In `common.yaml`, `gaze_threshold: 55.0` is in pixels and `gaze_step: 2` in joint-angle steps. Check ROI scale against the actual image size before tuning. A red/lost target must not continue to drive the arm from a stale box.

[M3P-089 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/1.%20OpenClaw%20target%20tracking/1.%20OpenClaw%20target%20tracking.pdf#page=1).

#### OpenClaw Robotic Arm Tracking And Grasping <a href="#m3-m3p-090" id="m3-m3p-090"></a>

`Pick` initializes tracker ROI, estimates a 3D grasp point, adjusts the chassis until reachable, re-estimates and performs the grasp. The shown `grasp_distance` is `[0.265,0,0]`; `grasp_offset` is **\[0.015,0.015,-0.03,2.0]**, whose xyz entries are m and final pitch is rad. `enable_auto_back: True` adds a **0.13 m** retreat after grasp, so the rear path must also be available. The geometric helper can fail when most target depth is missing; inspect actual/estimated centers instead of compensating with a large offset. Change one offset at a time, restart/reload as required by the installed node and re-observe a known block.

[M3P-090 · official PDF, pp. 1–12](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/2.%20OpenClaw%20robotic%20arm%20tracking%20and%20grasping/OpenClaw%20Robotic%20Arm%20Tracking%20And%20Grasping.pdf#page=1).

#### 3. OpenClaw robotic arm fixed-point placement <a href="#m3-m3p-091" id="m3-m3p-091"></a>

`GetPlacePoint(query)` captures an image, resolves the described placement and returns a verified 3D point; **(-1,-1)** indicates no visual target. `Place(place_x,place_y,place_z)` superimposes `place_offset`, and its shown solver path negates Y as part of coordinate conversion. The example offset is **\[-0.01,0,0.05,1.3]** (m,m,m,rad); its positive z adds release clearance. `place_distance` is shown as `[0.39,0,0.45,0.25]`, describing preferred position/reach checks, not a universal workspace box. If unreachable, the chassis adjustment tool changes the viewpoint, so acquire/verify the point again before release.

[M3P-091 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/3.%20OpenClaw%20robotic%20arm%20fixed-point%20placement/3.%20OpenClaw%20robotic%20arm%20fixed-point%20placement.pdf#page=1).

#### OpenClaw Garbage Sorting <a href="#m3-m3p-092" id="m3-m3p-092"></a>

`GetWasteRecognitionResults` temporarily enables the waste detector, waits for initial results and returns names, confidence, center/geometry and count; then `GraspWaste` and `PlaceWaste` perform the selected manipulation. The native service is `/waste_enable_srv`, type `waste_classify_msg/srv/WasteEnable`, and the example result topic is spelled `/waste_detecttions`. Inspect the installed service schema for operation codes before calling it. `waste_grasp_offset` is **\[0,0.015,-0.02,1.57]**; `waste_grasp_distance` is **\[0.24,0.09]**. The detector example uses confidence **0.1**, maximum **20** detections and **240 s** automatic shutdown. These low thresholds suit a controlled demonstration and require overlay inspection before a physical pick.

[M3P-092 · official PDF, pp. 1–17](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/4.%20OpenClaw%20garbage%20sorting/OpenClaw%20Garbage%20Sorting.pdf#page=1).

#### OpenClaw Slam Mapping And Navigation <a href="#m3-m3p-093" id="m3-m3p-093"></a>

Build grid, pose graph and road graph first; enable `car_base.launch.py relocation:=True`, roadnet navigation and MCP. Record locations with `robot_control call-tool RecordMapLocation --name ... --symbol ...`, then inspect `m3pro_bringup/config/map_mapping.yaml`; `Navigation(location)` fails if that location is absent. The default **0.8 m** threshold chooses ordinary Nav2 for a near destination and roadnet for a farther one. After travel it can perform visual relocalization and precise adjustment. Sample precision settings are max **0.1 m/s**, **0.5 rad/s**, target tolerances **0.01 m / 0.05 rad** and a 10 Hz adjustment loop. These are controller settings, not demonstrated arrival accuracy. Repeated timeout calls for TF/localization and reachability checks before more aggressive PID.

[M3P-093 · official PDF, pp. 1–13](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/5.%20OpenClaw%20slam%20mapping%20and%20navigation/OpenClaw%20Slam%20Mapping%20And%20Navigation.pdf#page=1).

#### OpenClaw Navigation Transfer <a href="#m3-m3p-094" id="m3-m3p-094"></a>

Navigation transfer composes target pick, map navigation and placement. Prepare each source/destination mapping and each individual operation first, then request one short transfer. Verify the object is actually held before departing and the destination is still suitable before releasing. The lesson reuses the grasp/placement parameters and navigation functions; it does not introduce a separate transport controller. Preserve the configured automatic backward move and carried-object footprint when judging approach/retreat clearance.

[M3P-094 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/6.%20OpenClaw%20navigation%20transfer/OpenClaw%20Navigation%20Transfer.pdf#page=1).

#### OpenClaw Machine Code Clip <a href="#m3-m3p-095" id="m3-m3p-095"></a>

`GetAprilTagIDs` returns visible tag IDs plus pose/orientation; `GraspArUcoTarget --target-id ...` selects one, approaches, photographs again and grasps. The current common-service parameter is `apriltag_size: 0.02` m, different from the localization marker's **0.048 m**. A wrong tag size scales metric pose despite a correct ID. The examples mix “ArUco” and AprilTag terminology; match detector family and actual printed code, not the English noun alone. This grasp reuses `grasp_offset` and optional 0.13 m auto-retreat. A failed pose lookup must stay a failure rather than substituting the first visible tag.

[M3P-095 · official PDF, pp. 1–11](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/7.%20OpenClaw%20machine%20code%20clip/OpenClaw%20Machine%20Code%20Clip.pdf#page=1).

#### OpenClaw Color Line Patrol <a href="#m3-m3p-096" id="m3-m3p-096"></a>

`FollowLine(color)` starts/monitors the supported colored-line behavior and rejects unknown color names. Use `ros2 launch m3pro_bringup colorSelect.launch.py` for its HSV calibration: select the intended color area, inspect the mask and press Space to write the calibrated values. Stop calibration before starting the run. This newer color workflow is distinct from the legacy R/ROI `follow_line` interface. Verify color under operating illumination and check obstacle/line-loss behavior before allowing an unattended route; a verbal “follow red” instruction does not establish a usable red mask.

[M3P-096 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/8.%20OpenClaw%20color%20line%20patrol/OpenClaw%20Color%20Line%20Patrol.pdf#page=1).

#### OpenClaw Visual Distance Measurement <a href="#m3-m3p-097" id="m3-m3p-097"></a>

`GetTargetDist(query)` combines a natural-language target description with fresh visual localization and depth/pose service data, returning distance information rather than a raw pixel radius. Confirm which target is shown in its verification image and the returned frame/unit contract before using the value for motion. The helper waits for its pose service, so a timeout is not zero distance. Missing depth or a target outside the current view requires a new observation/view adjustment, not an invented estimate from the language model.

[M3P-097 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/9.%20OpenClaw%20visual%20distance%20measurement/OpenClaw%20Visual%20Distance%20Measurement.pdf#page=1).

#### Summary of Common Errors and Solutions <a href="#m3-m3p-098" id="m3-m3p-098"></a>

When an embodied task fails, reproduce its smallest tool call. For no image, inspect camera ownership/topics; for no depth, inspect target surface and lighting; for unreachable arm, inspect the base-frame pose and offsets; for navigation failure, inspect surveyed mapping, TF and route connectivity. The source's common errors also cover YAML paths, unsupported language/provider and cloud quota/timeout. Do not reset the controller firmware to repair a provider authentication error or retrain a model to repair a disconnected camera.

[M3P-098 · official PDF, pp. 1–18](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/09.OpenClaw%20Embodied%20intelligent%20application/Summary%20of%20Common%20Errors%20and%20Solutions.pdf#page=1).

### 10. Scenario sandbox: maps, markers and end-to-end tasks <a href="#m3-course-10" id="m3-course-10"></a>

The sandbox is an optional set of props and a controlled environment, not a guaranteed included SKU component. The original map drawing is preserved in its cited PDF; it shows lanes, storage/sorting zones, parking and bin positions. Its sample names and positions are examples. Survey the assembled scene rather than importing coordinates from an illustration.

Sources: [M3P-099](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/10.OpenClaw%20scenario%20sandbox/1.%20Map%20description%20and%20prop%20placement/Map%20Description%20And%20Prop%20Placement.pdf).

#### Map Description And Prop Placement <a href="#m3-m3p-099" id="m3-m3p-099"></a>

Place the supplied shelves/pallets, blue placement pads, bins, tag props and color blocks according to the chosen scene. The source drawing labels shelf areas, parking P1/P2, cargo storage/sorting and waste sorting; names may be changed. Keep the physical zones distinct from semantic location names that will later be recorded. Inspect the four-page original for the actual prop layout; no dimensioned manufacturing drawing or surveyed coordinates can be derived from its picture. Record the real arrangement before mapping.

[M3P-099 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/10.OpenClaw%20scenario%20sandbox/1.%20Map%20description%20and%20prop%20placement/Map%20Description%20And%20Prop%20Placement.pdf#page=1).

#### Build Sand Table Map <a href="#m3-m3p-100" id="m3-m3p-100"></a>

Map the assembled scene with slam\_toolbox, inspect pose-node density, save both grid and pose graph, then annotate road nodes/edges through `road_net_route route_tool.launch.py`. The sandbox uses the same `~/map`/`/root/map` mount as the road course. Recheck laser alignment before creating each waypoint. Save/reload the route graph before defining task locations; otherwise a route can look correct on screen yet be absent from disk when the container restarts.

[M3P-100 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/10.OpenClaw%20scenario%20sandbox/2.%20Build%20sand%20table%20map/Build%20Sand%20Table%20Map.pdf#page=1).

#### Visual Relocation Markers <a href="#m3-m3p-101" id="m3-m3p-101"></a>

Set the physical marker side length in `m3pro_bringup/config/common.yaml`; the sample localization tags use **0.048 m**. Start `m3pro_bringup record_tag.launch.py`, verify accurate laser localization, select the visible tag ID and save its map pose. Inspect `aritag_relocation.yaml` after recording. Moved tags require re-surveying; recording a tag while the robot's pose is wrong bakes that error into later “correction.” The PDF uses both `apriltag_relocation` and `aritag_relocation` in prose; use the actual launch-loaded filename.

[M3P-101 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/10.OpenClaw%20scenario%20sandbox/3.%20Visual%20relocation%20markers/Visual%20Relocation%20Markers.pdf#page=1).

#### Map Mapping Markers <a href="#m3-m3p-102" id="m3-m3p-102"></a>

With roadnet, localization and MCP running, move to each intended task location and record its name/symbol using the robot mapping tool. Inspect `M3Pro_ws/src/m3pro_bringup/config/map_mapping.yaml` for all required entries and normalized quaternions. The semantic mapping must agree with the task prompts and physical scene. Tag survey files and semantic destination files solve different problems; an accurate tag does not automatically create a location called “shipping area.”

[M3P-102 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/10.OpenClaw%20scenario%20sandbox/4.%20Map%20mapping%20markers/Map%20Mapping%20Markers.pdf#page=1).

#### OpenClaw Scenario Sandbox Comprehensive Case <a href="#m3-m3p-103" id="m3-m3p-103"></a>

Start the configured agent, `car_base.launch.py relocation:=True`, MCP, roadnet navigation and optional `asr_detect`/`openclaw_bridge`. Execute one complete pick–transport–place task in the controlled sandbox. Inspect each tool result and updated scene before proceeding to the next phase. A combined task depends on the saved maps, graph, surveyed tags, named destinations and valid object geometry; initialize those independently before attributing a failed task to the language model. This appendix did not assemble props or run the demonstration.

[M3P-103 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/10.OpenClaw%20scenario%20sandbox/5.%20OpenClaw%20scenario%20sandbox%20comprehensive%20case/OpenClaw%20Scenario%20Sandbox%20Comprehensive%20Case.pdf#page=1).

### 11. AI fundamentals and the legacy multi\_brains architecture <a href="#m3-course-11" id="m3-course-11"></a>

The legacy `multi_brains` tutorials and newer OpenClaw/`multi_brains_pre` tutorials are parallel application generations. Both use ROS beneath model orchestration, but their configuration paths, APIs and launch files differ. Use concepts from the foundations without replacing one generation's running files with the other's examples.

Sources: [M3P-108](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/11.AI%20Model%20Basics/4.Embodied%20intelligent%20functions%20core%20source%20code/Embodied%20intelligent%20functions%20core%20source%20code.pdf).

#### 1.AI large model types and principles <a href="#m3-m3p-104" id="m3-m3p-104"></a>

The foundation distinguishes text generation, vision/multimodal and speech models. Choose the model by the required input/output: text instructions alone do not accept a camera image; speech recognition outputs text; speech synthesis consumes response text. For a robot pipeline record the chosen model, provider endpoint and region separately for ASR, decision/vision and TTS. The course's model names and provider feature claims are examples, not a benchmark or current-service guarantee. A useful initial check is one non-motion input/output per model before enabling robot actions.

[M3P-104 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/11.AI%20Model%20Basics/1.AI%20large%20model%20types%20and%20principles/1.AI%20large%20model%20types%20and%20principles.pdf#page=1).

#### 2.RAG retrieval enhancement and model training samples <a href="#m3-m3p-105" id="m3-m3p-105"></a>

RAG retrieves task/domain examples into the prompt at inference time; fine-tuning changes a model using training samples. The lesson connects both to reducing unsupported output, but neither guarantees factual or safe robot decisions. Build examples from observable inputs, allowed actions and completion/failure outputs, and include negative cases such as absent target or unavailable route. Test retrieval independently: the correct example should appear for a known query before letting the planner use it to select hardware tools.

[M3P-105 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/11.AI%20Model%20Basics/2.RAG%20retrieval%20enhancement%20and%20model%20training%20samples/2.RAG%20retrieval%20enhancement%20and%20model%20training%20samples.pdf#page=1).

#### 3.Embodied intelligent robot system architecture <a href="#m3-m3p-106" id="m3-m3p-106"></a>

The two architecture PDFs explain hierarchical inference: task understanding/decision is separated from action conversion, with visual/speech services and feedback closing the loop. The `multi_brains` framework adds routing and RAG rather than training an on-device end-to-end VLA model. Identify which layer produced an error: recognized text, decision plan, translated action or physical feedback. Cloud inference does not remove the need for the local ROS controller, and NX compute specifications do not imply the cloud model runs locally. Both PDFs are mapped here as overlapping versions, not separate required installations.

[M3P-106 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/11.AI%20Model%20Basics/3.Embodied%20intelligent%20robot%20system%20architecture/3.Embodied%20intelligent%20robot%20system%20architecture.pdf#page=1).

#### Embodied intelligent robot system architecture <a href="#m3-m3p-107" id="m3-m3p-107"></a>

The two architecture PDFs explain hierarchical inference: task understanding/decision is separated from action conversion, with visual/speech services and feedback closing the loop. The `multi_brains` framework adds routing and RAG rather than training an on-device end-to-end VLA model. Identify which layer produced an error: recognized text, decision plan, translated action or physical feedback. Cloud inference does not remove the need for the local ROS controller, and NX compute specifications do not imply the cloud model runs locally. Both PDFs are mapped here as overlapping versions, not separate required installations.

[M3P-107 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/11.AI%20Model%20Basics/3.Embodied%20intelligent%20robot%20system%20architecture/Embodied%20intelligent%20robot%20system%20architecture.pdf#page=1).

#### Embodied intelligent functions core source code <a href="#m3-m3p-108" id="m3-m3p-108"></a>

`asr_detect.py` captures speech with VAD, `model_service.py` consumes a request queue and calls Dify, and `action_service.py` executes translated actions and feeds results back. The VAD text describes a silence-frame threshold, but its “90 frames ≈1.5 s” timing must be checked against the actual frame size/sample rate rather than copied as a universal timeout. Wake events interrupt recording/playback; movement loops check interruption flags. Grasp subprocesses require process-tree cleanup and reset of their completion future, not only stopping the top-level chat. Inspect interruption at each layer before assuming a second wake word stopped every actuator.

[M3P-108 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/11.AI%20Model%20Basics/4.Embodied%20intelligent%20functions%20core%20source%20code/Embodied%20intelligent%20functions%20core%20source%20code.pdf#page=1).

### 12. Dify development, credentials, RAG and independent module tests <a href="#m3-course-12" id="m3-course-12"></a>

Dify application keys and upstream model-provider keys are different credentials. A working model-provider test does not prove the robot's application key, DSL workflow or image upload works. The examples supplied beside the PDFs include spreadsheets and workflow YAML; their exact files/hashes are recorded as supplementary resources. They were inspected as document resources, not imported into a running service.

Sources: [M3P-110](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/02.%20Configuring%20API-KEY/Configuring%20API-KEY.pdf).

#### Register a model service account <a href="#m3-m3p-109" id="m3-m3p-109"></a>

Create an account with the chosen provider and obtain your own API key in the appropriate region. The source uses Alibaba Model Studio as an example and distinguishes international and mainland services; free quotas are account/time dependent and are not reproduced as current entitlements. Keep credentials out of screenshots and prompts. A key should be validated with the minimal provider/Dify test before any robot behavior, with provider name, endpoint and region recorded in the deployment notes.

[M3P-109 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/01.Register%20a%20model%20service%20provider%20account/Register%20a%20model%20service%20account.pdf#page=1).

#### Configuring API-KEY <a href="#m3-m3p-110" id="m3-m3p-110"></a>

Use the image's Dify service access procedure under `~/M3Pro_ws/multi_brains_file`. In Dify Settings → Model Provider, configure the chosen provider, its international/account selection and your key. Open the supplied **TEST\_API** app, select the intended model and send a harmless question; an actual response verifies that integration layer. The legacy `ALIYUN_API_KEY` voice setting is a separate configuration from the Dify app key. Do not use a model key in the robot's `DIFY_API_KEY` field.

[M3P-110 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/02.%20Configuring%20API-KEY/Configuring%20API-KEY.pdf#page=1).

#### 3. Introduction to Dify <a href="#m3-m3p-111" id="m3-m3p-111"></a>

Dify provides application orchestration, model-provider plugins and knowledge retrieval. Establish the application's input variables, selected model and output contract before binding it to a robot. A chatbot, a retrieval-enabled chatbot and a multi-node workflow are distinct app types; their API behavior should be tested separately. The lesson introduces deployment choices rather than a single reproducible installer for this pinned repository, so retain the supplied image's working Dify setup as the baseline.

[M3P-111 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/03.%20Introduction%20to%20Dify/3.%20Introduction%20to%20Dify.pdf#page=1).

#### Basic Dify Features <a href="#m3-m3p-112" id="m3-m3p-112"></a>

In Plugins → Explore Marketplace → Models, install/configure the selected provider integration, then choose it in the application. Review the app prompt, model parameters and account settings. Publish the intended revision to make the runtime/API reflect editor changes. If the editor preview works but the robot does not, check the published app, its own API key and base URL before changing the provider plugin or robot firmware.

[M3P-112 · official PDF, pp. 1–12](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/04.%20Basic%20Dify%20Features/Basic%20Dify%20Features.pdf#page=1).

#### AI Large Model Development - chatbot <a href="#m3-m3p-113" id="m3-m3p-113"></a>

Create a **Chat Assistant** from blank, write a role/task prompt, select the model and test in the preview. For image questions use a multimodal model and enable vision explicitly. Publish, then test the public app/API against the same example input; editor-only changes are not a deployment check. A useful original test asks the app to describe a stationary colored block and explicitly report absence when the image contains none, without attaching motion tools.

[M3P-113 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/05.%20AI%20Large%20Model%20Development%20-%20chatbot/AI%20Large%20Model%20Development%20-%20chatbot.pdf#page=1).

#### Deploy the RAG knowledge base <a href="#m3-m3p-114" id="m3-m3p-114"></a>

Create a Dify Knowledge base, import the intended file and preview chunk boundaries before indexing. The example contrasts economical indexing with a higher-quality embedding/reranking workflow, which needs appropriate configured models and credentials. Inspect at least one query's retrieved chunk after indexing. Store action examples with target conditions and failure cases together so retrieval does not detach a motion instruction from its prerequisites. Uploading a spreadsheet is not enough to prove its rows became useful retrieval units.

[M3P-114 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/06.%20Deploy%20the%20RAG%20knowledge%20base/Deploy%20the%20RAG%20knowledge%20base.pdf#page=1).

#### RAG knowledge base + chatbot <a href="#m3-m3p-115" id="m3-m3p-115"></a>

Attach the intended knowledge base through the chatbot's **Knowledge → Add**, select its model and test questions whose answers depend on a supplied example. The included fabricated-author text is a retrieval teaching sample, not a factual authority to republish as real biography. Compare an answer with the retrieved source passage and test an unanswerable question. For robot task examples, a useful response should preserve allowed action names/units and state when required scene evidence is absent.

[M3P-115 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/07.%20RAG%20knowledge%20base%20%2B%20chatbot/RAG%20knowledge%20base%20%2B%20chatbot.pdf#page=1).

#### AI agent workflow <a href="#m3-m3p-116" id="m3-m3p-116"></a>

Import the supplied `Complex agent.yml` DSL in Dify Studio, select actual available models and inspect the question-classifier branches for math, physics and other inputs. Preview each branch, then publish the version intended for API use. The neighboring Yahboom English/Chinese workflow files are separate examples, not automatically compatible replacements. Before using an imported workflow with a robot, verify required input variables, structured output and image-handling behavior; a successfully imported file only proves the DSL parsed.

[M3P-116 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/08.%20AI%20agent%20workflow/AI%20agent%20workflow.pdf#page=1).

#### Custom wake-up response <a href="#m3-m3p-117" id="m3-m3p-117"></a>

The custom wake response uses configured TTS to generate audio and stores language-specific wake files under the legacy `multi_brains/system_vioce/.../wakeup` tree; preserve the vendor's `vioce` spelling when locating it. Configure the voice provider/model before synthesis, then audition the file and back up the original response before replacing it. This changes the reply after wake detection, not the recognizer's wake-word acoustic model. Do not assume modifying an audio clip changes “Hello yahboom” recognition.

[M3P-117 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/09.%20Custom%20wake-up%20response/Custom%20wake-up%20response.pdf#page=1).

#### 10. Core module testing tools <a href="#m3-m3p-118" id="m3-m3p-118"></a>

From `~/M3Pro_ws/src/multi_brains/test`, run the installed module-specific tests individually: `test_PiperTTS.py`, `test_SenseVoiceSmall.py`, `test_dify_connection.py`, and the matching Tongyi/Baidu/iFlytek ASR/TTS scripts. Local tests separate model-file/audio failures from network/provider errors. Validate one Chinese/English case as appropriate, record the actual response/error and confirm the intended speaker/microphone. No such tests were run here; the appendix's syntax/document checks are not substitutes for them.

[M3P-118 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/12.AI%20Model%20Development/10.%20Core%20module%20testing%20tools/10.%20Core%20module%20testing%20tools.pdf#page=1).

### 13. Legacy voice interaction and model-directed behavior <a href="#m3-course-13" id="m3-course-13"></a>

In this lane use `ros2 launch multi_brains llm_agent_control.launch.py` (the image may also provide `multi_brains` as a shortcut). Wake with **“Hello yahboom”**, wait for its recording cue, speak, and inspect recognized text, decision, action list and final feedback separately. Noisy or missing speech should be resolved before task execution. A second wake can interrupt the conversation/action flow; confirm actual motion has stopped rather than relying on the speech interruption alone.

Sources: [M3P-119](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/13.AI%20Model%20-%20Voice%20Version/1.Semantic%20understand%20and%20command%20follow/Semantic%20understand%20and%20command%20follow.pdf).

#### Semantic understand and command follow <a href="#m3-m3p-119" id="m3-m3p-119"></a>

After starting the legacy agent, test a short semantic command with a clear numeric distance/direction and inspect its translated action list before motion. The example demonstrates conversion to `set_cmdvel`-style calls whose duration/speed are different from an odometry distance target. Verify units and behavior in the installed action implementation. If ASR transcribes a wrong distance, correct the voice input and discard that plan; do not tune motor PID to compensate for a recognition error.

[M3P-119 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/13.AI%20Model%20-%20Voice%20Version/1.Semantic%20understand%20and%20command%20follow/Semantic%20understand%20and%20command%20follow.pdf#page=1).

#### Multimodal visual understand <a href="#m3-m3p-120" id="m3-m3p-120"></a>

Visual understanding saves a fresh camera image through the action-service `seewhat` helper and asks the model service to interpret it. Begin with a description-only prompt about visible objects. The task retains conversation history until the user ends the current task; use an explicit “end current task” to clear stale assumptions before changing the scene. A remembered blue block is not proof it remains visible. Confirm the image used in a response before extending the prompt to nodding, tracking or grasping.

[M3P-120 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/13.AI%20Model%20-%20Voice%20Version/2.Multimodal%20visual%20understand/Multimodal%20visual%20understand.pdf#page=1).

#### Multimodal visual understand+SLAM navigation <a href="#m3-m3p-121" id="m3-m3p-121"></a>

Start the ordinary Nav2 base/navigation/RViz stack and initialize the pose before enabling the voice navigation task. Survey each named destination with `tf2_echo map base_footprint` and record position/quaternion in **`~/M3Pro_ws/multi_brains_file/map_mapping.yaml`**. Update the Dify model's place/symbol mapping consistently. The legacy file differs from the newer `m3pro_bringup/config/map_mapping.yaml`. Test one nearby named destination, check arrival feedback and return path, then add visual questions at the stop.

[M3P-121 · official PDF, pp. 1–14](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/13.AI%20Model%20-%20Voice%20Version/4.Multimodal%20visual%20understand%2BSLAM%20navigation/Multimodal%20visual%20understand%2BSLAM%20navigation.pdf#page=1).

#### Robotic arm gripping+Multimodal visual understand+SLAM navigation <a href="#m3-m3p-122" id="m3-m3p-122"></a>

Combine the initialized voice agent, grasp behavior and Nav2 only after each works independently. A transfer plan should observe the object, locate it, pick, verify holding, navigate to a surveyed destination and release. The source adds arm-grasp functions to the action server; starting Nav2 alone does not expose them to the model. Keep the camera/arm launch ownership consistent and inspect action completion at every phase. Neither a fluent narrated plan nor successful navigation proves the object was grasped.

[M3P-122 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/13.AI%20Model%20-%20Voice%20Version/5.Robotic%20arm%20gripping%2BMultimodal%20visual%20understand%2BSLAM%20navigation/Robotic%20arm%20gripping%2BMultimodal%20visual%20understand%2BSLAM%20navigation.pdf#page=1).

#### Intention estimation <a href="#m3-m3p-123" id="m3-m3p-123"></a>

Intent estimation uses the supplied **Intent mapping.xlsx** examples in Dify RAG to associate contextual requests with explicit supported tasks. Customize the mapping, index it, then test both intended phrases and ambiguous counterexamples. Named places still require valid map poses; a semantic association cannot invent a destination. Keep task memory bounded with the documented end-task command. This is retrieval-based interpretation of user intent, not evidence that the robot can infer an unspoken physical requirement reliably.

[M3P-123 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/13.AI%20Model%20-%20Voice%20Version/6.Intention%20estimation/Intention%20estimation.pdf#page=1).

### 14. Legacy text interaction without the speech layer <a href="#m3-course-14" id="m3-course-14"></a>

Launch `multi_brains llm_agent_control.launch.py text_chat_mode:=True`, then `ros2 run text_chat text_chat` on the intended local/remote ROS environment. Text mode is useful for isolating model/task failures from ASR/TTS. It retains the same hardware-action risks and map/vision prerequisites as the voice lane.

Sources: [M3P-124](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/14.AI%20Model%20-%20Text%20Version/1.Semantic%20understand%20and%20command%20follow/Semantic%20understand%20and%20command%20follow.pdf).

#### Semantic understand and command follow <a href="#m3-m3p-124" id="m3-m3p-124"></a>

Type one explicit semantic command in `text_chat`, then inspect decision text, translated action and feedback. Text mode bypasses the microphone and wake-word step but still calls the same model/action service. Use a no-motion question first to establish model connectivity. When a motion command is intended, compare its numeric values with the actual translated call before relying on the result. A response printed by the chat client does not establish the controller received or completed it.

[M3P-124 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/14.AI%20Model%20-%20Text%20Version/1.Semantic%20understand%20and%20command%20follow/Semantic%20understand%20and%20command%20follow.pdf#page=1).

#### Multimodal visual understand <a href="#m3-m3p-125" id="m3-m3p-125"></a>

Use text mode to request a fresh scene description or verify the presence of a specified object. The same `seewhat` image capture/model-service flow is used as in voice mode. End the current task before testing a changed scene so a previous object description is not mistaken for a new observation. Distinguish multimodal model input failures from camera-topic failures by inspecting the captured image and the model response separately.

[M3P-125 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/14.AI%20Model%20-%20Text%20Version/2.Multimodal%20visual%20understand/Multimodal%20visual%20understand.pdf#page=1).

#### Multimodal visual understand+SLAM navigation <a href="#m3-m3p-126" id="m3-m3p-126"></a>

Prepare Nav2, initialize pose, survey named destinations and synchronize the **legacy** map-mapping YAML with the Dify prompt/RAG configuration. Request a nearby named location in `text_chat`; verify the selected coordinates and result, then add a visual inspection at arrival. This removes speech recognition from the diagnostic chain while retaining map/frame accuracy requirements. If a location is missing, add a measured mapping rather than letting the model invent x/y coordinates.

[M3P-126 · official PDF, pp. 1–11](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/14.AI%20Model%20-%20Text%20Version/4.Multimodal%20visual%20understand%2BSLAM%20navigation/Multimodal%20visual%20understand%2BSLAM%20navigation.pdf#page=1).

#### Intention estimation <a href="#m3-m3p-127" id="m3-m3p-127"></a>

Import/customize the intent-mapping examples, verify retrieval, then test paraphrases in text mode against explicit supported tasks. The PDF prints a launch command truncated after `text_chat_mode`; the complete command elsewhere in the same lesson is `text_chat_mode:=True`. Use the complete form. Confirm map initialization before an inferred navigation action, and test ambiguous requests that should request clarification or report a missing mapping instead of choosing an arbitrary destination.

[M3P-127 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/14.AI%20Model%20-%20Text%20Version/6.Intention%20estimation/Intention%20estimation.pdf#page=1).

### 15. MediaPipe and gesture-driven arm applications <a href="#m3-course-15" id="m3-course-15"></a>

All these examples start the DCW2 driver once and subscribe to `/camera/color/image_raw` through CvBridge. The ROS executable names are case-sensitive and do **not** match lesson numbers consistently. The installed examples use legacy `mp.solutions` APIs; the source commit does not guarantee that a newly installed MediaPipe release still contains each module. Some examples initialize `/arm6_joints` even when their main output is a visualization. Inspect startup posture before running them with the arm free to move.

Sources: [M3P-128](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/1.Hand%20detection/1.Hand%20detection.pdf).

#### 1.Hand detection <a href="#m3-m3p-128" id="m3-m3p-128"></a>

Run `ros2 run yahboomcar_mediapipe 01_HandDetector`. `mp.solutions.hands.Hands` extracts landmarks, with the example allowing two hands and detection/tracking confidence **0.5**. `pubHandsPoint(frame, draw=...)` returns annotated or clean views; `multi_hand_landmarks` must be present before indexing. Check BGR-to-RGB conversion and image receipt when landmarks are absent. The visualized joint points are image coordinates/relative landmarks, not calibrated hand positions in `base_link`.

[M3P-128 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/1.Hand%20detection/1.Hand%20detection.pdf#page=1).

#### 2.Posture detection <a href="#m3-m3p-135" id="m3-m3p-135"></a>

`yahboomcar_mediapipe 02_PoseDetector` uses the pose solution with smoothing and sample confidence **0.5**. `pubPosePoint` reads `pose_landmarks` and draws the body connections on an image. Keep the whole relevant body region inside the camera view and compare stable points before using a derived angle. A missed person detection should return no pose, not reuse the previous frame's joints. This lesson provides a visualization foundation, not a robot-human collision model.

[M3P-135 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/2.Posture%20detection/2.Posture%20detection.pdf#page=1).

#### 3.Overall detection <a href="#m3-m3p-136" id="m3-m3p-136"></a>

`yahboomcar_mediapipe 03_Holistic` combines face, pose and hand landmarks through `mp.solutions.holistic`. The helper checks each landmark group separately, so a visible face with no hands is a valid partial result. Inspect each group rather than assuming one successful detection proves all three. Smoothing and detection/tracking thresholds affect continuity; preserve the source's input color convention. Its holistic overlay is not a unified metric 3D reconstruction of a person.

[M3P-136 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/3.Overall%20detection/3.Overall%20detection.pdf#page=1).

#### 4.Facial Landmark Detection <a href="#m3-m3p-137" id="m3-m3p-137"></a>

`yahboomcar_mediapipe 04_FaceMesh` uses `FaceMesh`, allows two faces in the shown constructor and draws `FACEMESH_CONTOURS`. `multi_face_landmarks` can be empty or contain multiple faces; explicitly choose the intended one before deriving a control signal. The `draw` switch controls annotation, not inference. A dense mesh is a different output from the simpler face-detection box used by the next exercise.

[M3P-137 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/4.Facial%20Landmark%20Detection/4.Facial%20Landmark%20Detection.pdf#page=1).

#### 5.Face detection <a href="#m3-m3p-138" id="m3-m3p-138"></a>

`yahboomcar_mediapipe 07_FaceDetection` draws face boxes and detector scores using the MediaPipe face detector. Review each box against the image and use its confidence as an inference score, not a probability of identity or permission. This task detects faces rather than recognizing a named person. If a face mesh works but this example does not, inspect its separate detector setup and confidence configuration before changing the camera.

[M3P-138 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/5.Face%20detection/5.Face%20detection.pdf#page=1).

#### 6.Face special effects <a href="#m3-m3p-139" id="m3-m3p-139"></a>

Despite the course grouping, `yahboomcar_mediapipe 06_FaceLandmarks` uses **dlib's 68-point predictor** for eye/lip/eyebrow effects. The `shape_predictor` data file must exist at the path loaded by the node. `prettify_face` and `get_lmList` choose the facial regions and overlay effects. A missing predictor is a model-resource failure, not missing MediaPipe landmarks. Preserve the gray-image/predictor coordinate convention before drawing on the color frame.

[M3P-139 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/6.Face%20special%20effects/6.Face%20special%20effects.pdf#page=1).

#### 7.3D object recognition <a href="#m3-m3p-140" id="m3-m3p-140"></a>

`yahboomcar_mediapipe 08_Objectron` defaults to a shoe category; **F** cycles supported object models (the lesson illustrates a mug). It draws a category-specific 3D box from Objectron output. This legacy dependency may be absent from an arbitrary modern MediaPipe installation, so inspect the supplied image/model package rather than upgrading indiscriminately. A wireframe result is a model estimate, not a depth-calibrated block pose ready for arm grasping.

[M3P-140 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/7.3D%20object%20recognition/7.3D%20object%20recognition.pdf#page=1).

#### 8.Brush <a href="#m3-m3p-141" id="m3-m3p-141"></a>

`yahboomcar_mediapipe 09_VirtualPaint` renders a **640 × 480** canvas using hand landmarks. Joining index/middle fingers enters color selection; separating them draws. The palette includes red/green/blue/yellow and black as eraser; the shown brush/eraser widths are **5/100 pixels**, with a top selection band. Verify the fingertip IDs and mode transitions before interpreting missing lines as a camera issue. This is image-space drawing, independent of any robot path.

[M3P-141 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/8.Brush/8.Brush.pdf#page=1).

#### 9.Finger control <a href="#m3-m3p-142" id="m3-m3p-142"></a>

`yahboomcar_mediapipe 10_HandCtrl` derives the angle between thumb tip, wrist and index tip, using landmark IDs **4, 0, 8**, to vary an image-processing effect. **F** changes the effect. The helper first checks detected landmark availability; keep that guard when adapting the code. An angle change affects visualization here, not the gripper; the separate `13_FingerCtrl` example adds arm actuation.

[M3P-142 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/9.Finger%20control/9.Finger%20control.pdf#page=1).

#### 10.Palm target positioning <a href="#m3-m3p-129" id="m3-m3p-129"></a>

`yahboomcar_mediapipe 12_FindHand` uses the vendor `HandDetector` helper, returning landmark list and hand bbox. It computes palm target x/y from the box center and prints `index X/Y`. Inspect a single hand moving horizontally and vertically to establish the image-axis directions. This is a 2D target point; without depth/registration and transforms it must not be used as a metric grasp target.

[M3P-129 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/10.Palm%20target%20positioning/10.Palm%20target%20positioning.pdf#page=1).

#### 11.Fingertip trajectory recognition <a href="#m3-m3p-130" id="m3-m3p-130"></a>

The fingertip-trajectory PDF prints an executable with an apparent whitespace typo, `15_ FingerTrajectory`. Inspect `ros2 pkg executables yahboomcar_mediapipe` for the actual entry point before running it. Begin with an open five-finger hand, draw using the single-index-finger gesture, then open the hand again to finish/recognize the trajectory. Landmark **8** is the index fingertip in the source. Check the displayed path and state transitions before changing the recognizer; this exercise produces an image trajectory rather than an arm motion.

[M3P-130 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/11.Fingertip%20trajectory%20recognition/11.Fingertip%20trajectory%20recognition.pdf#page=1).

#### 12.Fingertip gesture control robotic arm <a href="#m3-m3p-131" id="m3-m3p-131"></a>

`yahboomcar_mediapipe 14_FingerAction` uses the same five-fingers → one-finger drawing → five-fingers completion sequence, then maps the recognized trajectory to a predefined arm action. Inspect the recognized class before motion and leave the complete action envelope clear. The class's arm movement methods are separate from the gesture/trajectory detector. Recognition of a square-like trace does not mean an arbitrary continuous hand path is converted into collision-checked Cartesian arm motion.

[M3P-131 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/12.Fingertip%20gesture%20control%20robotic%20arm/12.Fingertip%20gesture%20control%20robotic%20arm.pdf#page=1).

#### 13.Gesture grabbing and releasing objects <a href="#m3-m3p-132" id="m3-m3p-132"></a>

`yahboomcar_mediapipe 16_GestureGrasp` maps **Yes** to a predefined forward pick and **OK** to placing at the predefined upper-left position. The task does not locate an arbitrary object with depth first; put the correct prop at the known grasp location and match jaw opening. Inspect the recognized label before leaving the hand gesture in view, and stop with Ctrl+C when finished. Repeated gestures must not be treated as proof the object was successfully held.

[M3P-132 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/13.Gesture%20grabbing%20and%20releasing%20objects/13.Gesture%20grabbing%20and%20releasing%20objects.pdf#page=1).

#### 14.Finger control robotic arm <a href="#m3-m3p-133" id="m3-m3p-133"></a>

`yahboomcar_mediapipe 13_FingerCtrl` maps the thumb–wrist–index angle to servo 6. The printed code lower-bounds the input angle at **2°**, then computes **360 / angle** as the target gripper angle, publishing `ArmJoint`. This inverse relationship is a demonstration mapping, not a force sensor. Begin with an empty gripper and apply the mechanical-width limits for any object; a hand gesture cannot justify commanding excessive closure on a larger block.

[M3P-133 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/14.Finger%20control%20robotic%20arm/14.Finger%20control%20robotic%20arm.pdf#page=1).

#### 15.Medipipe gesture control robotic arm action group <a href="#m3-m3p-134" id="m3-m3p-134"></a>

`M3Pro_demo Gesture_Moving` recognizes an action-group gesture and requires **Space for each execution**. Yes selects dance; OK head shake; downward thumb kneeling; one finger nod; Rock an upward/stretch shake; five fingers clapping. The action thread publishes joint targets and returns to the initial pose. Review the label and keep the action envelope clear before Space. This explicit trigger differs from the continuous `13_FingerCtrl` mapping and should not be removed casually in an adaptation.

[M3P-134 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/15.Mediapipe%20Visual%20Course/15.Medipipe%20gesture%20control%20robotic%20arm%20action%20group/15.Medipipe%20gesture%20control%20robotic%20arm%20action%20group.pdf#page=1).

### 16. MoveIt2 model configuration and simulation <a href="#m3-course-16" id="m3-course-16"></a>

Use the supplied ROS 2/MoveIt2 development environment and model. `ros2 launch test_moveit_config demo.launch.py` opens the planner/scene; expected readiness text is “You can start planning now!” The planning group is `arm_group`. Keep `MoveIt_SimToMachine SimulationToMachine` **stopped** for simulation-only work. A successful path in a URDF/scene is not a physical collision test, and joint values in MoveIt are generally radians while the vendor servo message uses degrees.

Sources: [M3P-143](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/1.MovelT2%20configuration/1.MovelT2%20configuration.pdf), [M3P-144](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/2.MovelT2%20simulation-reality%20linkage/2.MovelT2%20simulation-reality%20linkage.pdf).

#### 1.MovelT2 configuration <a href="#m3-m3p-143" id="m3-m3p-143"></a>

Use MoveIt Setup Assistant on the exact arm URDF to generate collision matrix, virtual joint, planning group, named states, end-effector/controller configuration and the `test_moveit_config` package. Build that package and start `demo.launch.py`; verify expected joints and planning frame before planning. The PDF's `ros-<distro>-moveit` install string is a template, not a literal command. Confirm the actual Humble package/environment rather than installing a different ROS distribution over the robot image.

[M3P-143 · official PDF, pp. 1–27](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/1.MovelT2%20configuration/1.MovelT2%20configuration.pdf#page=1).

#### 2.MovelT2 simulation-reality linkage <a href="#m3-m3p-144" id="m3-m3p-144"></a>

`ros2 run MoveIt_SimToMachine SimulationToMachine` is the physical bridge. The source converts planned/model joint data into `ArmJoints`, including the servo mapping, and publishes to the controller. In RViz choose `arm_group`, named start/goal states such as up/init and inspect **Plan** before **Plan\&Execute**. With the bridge active, execution can move the real arm. Verify median alignment, signs, units and model pose agreement before enabling it; a working simulation does not validate that mapping.

[M3P-144 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/2.MovelT2%20simulation-reality%20linkage/2.MovelT2%20simulation-reality%20linkage.pdf#page=1).

#### 3.Random movement <a href="#m3-m3p-145" id="m3-m3p-145"></a>

`ros2 run MoveIt_demo random_move` generates random targets using the MoveGroupInterface. The example sets up to **10 planning attempts** and **5 s** planning time. Confirm trajectory validity in simulation and inspect whether the target is reachable/collision-free before execution. Randomness makes this unsuitable as a physical first-result test. A failed plan is a valid outcome for an unreachable sampled state and should not be bypassed by forcing the returned trajectory.

[M3P-145 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/3.Random%20movement/3.Random%20movement.pdf#page=1).

#### 4.Forward kinematics design <a href="#m3-m3p-146" id="m3-m3p-146"></a>

`MoveIt_demo set_target_joints` demonstrates forward use of specified joint targets through MoveGroupInterface: set a joint vector, plan, check the plan result, then execute in simulation. Match the vector order to the planning group's active joints and use the model's angular units. Compare the resulting end pose in RViz; this develops joint-space control rather than solving a requested Cartesian pose. Keep the gripper separate from the five-axis arm IK where the model requires it.

[M3P-146 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/4.Forward%20kinematics%20design/4.Forward%20kinematics%20design.pdf#page=1).

#### 5.Inverse kinematics design <a href="#m3-m3p-147" id="m3-m3p-147"></a>

`MoveIt_demo set_target_position` supplies a desired end-effector pose and asks the configured IK/planner for joints and a path. The PDF's introductory sentence mislabels this as forward kinematics; the operation is inverse kinematics. Check planning frame, end-effector link, position units and normalized orientation before planning. An out-of-reach pose or unsupported orientation should fail planning rather than be “fixed” with arbitrary offsets in the physical servo publisher.

[M3P-147 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/5.Inverse%20kinematics%20design/5.Inverse%20kinematics%20design.pdf#page=1).

#### 6.Cartesian path <a href="#m3-m3p-148" id="m3-m3p-148"></a>

`MoveIt_demo cartesian_path` defines end-effector waypoints, computes a Cartesian path and displays the planned trajectory. Inspect the returned completion fraction and the entire path, not only the endpoint. Interpolation step/jump thresholds affect reachability and continuity, so retain the installed example's explicit settings rather than assuming every waypoint sequence is executable. A partial path must not be described as reaching the final requested pose.

[M3P-148 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/6.Cartesian%20path/6.Cartesian%20path.pdf#page=1).

#### 7.Trajectory planning <a href="#m3-m3p-149" id="m3-m3p-149"></a>

`MoveIt_demo multi_track_motion` plans and displays a multi-stage trajectory. Add the RViz trajectory display and select its actual topic, then inspect segment order and continuity before executing. Named states, current state and path visualization must refer to the same robot model. If nothing appears, check the display topic and planning result before enabling the hardware bridge; a missing overlay is not evidence the physical joint targets are safe.

[M3P-149 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/7.Trajectory%20planning/7.Trajectory%20planning.pdf#page=1).

#### 8.Collision detection <a href="#m3-m3p-150" id="m3-m3p-150"></a>

`MoveIt_demo obstacle_avoidance` adds a collision object through PlanningSceneInterface and plans around it. The source names the example object `box1`; its frame, geometry and pose must match the planning scene. Confirm the obstacle is visible and included in collision checking before comparing plans. A scene object does not represent a real obstacle until it has been registered to the actual robot/world frame.

[M3P-150 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/8.Collision%20detection/8.Collision%20detection.pdf#page=1).

#### 9.Scene design <a href="#m3-m3p-151" id="m3-m3p-151"></a>

`MoveIt_demo set_scene` demonstrates adding a saved scene/obstacle set; use the RViz scene controls to load and **Publish** it before planning. The example then plans toward a named initial posture while respecting the scene geometry. A loaded but unpublished object can appear in an editor without affecting the planning server. Save the scene and model revision together; collision geometry in a different frame or stale model can create a false clearance.

[M3P-151 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/16.MoveIt2%20Simulation%20Course/9.Scene%20design/9.Scene%20design.pdf#page=1).

### 17. Multiple robots and formations <a href="#m3-course-17" id="m3-course-17"></a>

These exercises require additional compatible robots; they do not describe extra hardware included in this NX SKU. Intentionally cooperating robots share a domain but use distinct namespaces such as `robot1`, `robot2` and `robot3`. Inspect both topic names and TF prefixes; namespace alone does not automatically fix every hardcoded absolute topic or frame in an application.

Sources: [M3P-152](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/17.Multi-vehicle%20Course/1.Multi-vehicle%20chassis%20control/1.Multi-vehicle%20chassis%20control.pdf).

#### 1.Multi-vehicle chassis control <a href="#m3-m3p-152" id="m3-m3p-152"></a>

Stop each agent and set the controller namespace through its installed configuration utility, while keeping the ROS domain equal on robots/workstation. Restart agents and verify distinct nodes/topics with `ros2 node list`. Start the keyboard controller remapped to the intended namespace, and confirm its output before any wheel motion. Do not assume an unqualified `/cmd_vel` addresses only one robot in a shared domain. Keep a table of hostname/IP, namespace and robot identity during testing.

[M3P-152 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/17.Multi-vehicle%20Course/1.Multi-vehicle%20chassis%20control/1.Multi-vehicle%20chassis%20control.pdf#page=1).

#### 2.Multi-vehicle robotic arm control <a href="#m3-m3p-153" id="m3-m3p-153"></a>

Use each robot's namespace with the joystick receiver/control nodes (`joy joy_node` and `yahboomcar_ctrl yahboom_joy_M3Pro` in the lesson). START wakes and R2 unlocks; brief button presses increment servo targets. Confirm raw joystick input, publisher namespace and arm subscriber on the intended robot first. Two vehicles receiving the same unqualified arm topic is a routing failure, not a servo calibration problem.

[M3P-153 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/17.Multi-vehicle%20Course/2.Multi-vehicle%20robotic%20arm%20control/2.Multi-vehicle%20robotic%20arm%20control.pdf#page=1).

#### 3.Multi-vehicle navigation <a href="#m3-m3p-154" id="m3-m3p-154"></a>

Bring up each vehicle through `yahboom_multi yahboom_bringup_multi.xml robot_name:=robot1` (and robot2), start the common map/visualizer and each robot's dedicated AMCL/navigation launches. Initialize both poses separately and inspect the prefixed TF trees before goals. The source splits `robot_name:=` across whitespace in one command; use a valid launch argument without that split. Shared map coordinates are useful only when both localizations refer to the same physical map.

[M3P-154 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/17.Multi-vehicle%20Course/3.Multi-vehicle%20navigation/3.Multi-vehicle%20navigation.pdf#page=1).

#### 4.Multi-vehicle formation <a href="#m3-m3p-155" id="m3-m3p-155"></a>

The formation demo uses **three robots**, each with base, AMCL and navigation, then `yahboom_multi_tf pub_follower_goal` and `get_follower_point`. The example follower points are offsets of **0.3 m / 0.6 m** behind or laterally from the leader depending on formation mode. These are goal offsets, not collision clearances or proven tracking accuracy. Verify every follower goal in the shared map and reserve enough turning space; the source explicitly notes poor planning in a narrow environment.

[M3P-155 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/17.Multi-vehicle%20Course/4.Multi-vehicle%20formation/4.Multi-vehicle%20formation.pdf#page=1).

### 18. Control board, STM32 peripherals and micro-ROS firmware <a href="#m3-course-18" id="m3-course-18"></a>

The illustrated board is **YB-ERF02-01.0**. USB **Connect** is host data/programming; the Type-C power output is a separate port, specified **5.1 V / 5 A** for the Raspberry Pi power protocol. Orin uses the board's **12 V DC output**, not that Pi output. The board has separate 6.8 V and 12 V serial-servo connectors and a selectable 5/6.8 V PWM-servo supply. Match the actual fitted servo and connector; identical-looking plugs do not imply identical voltage.

Standalone `Board_Samples/STM32_Samples/...` and micro-ROS teaching firmware **replace** the factory controller firmware. Back up configuration and retain the correct factory HEX before experimenting; restore it before resuming factory `/YB_Node` operation. In the standalone examples, USB serial debug is usually **115,200 baud**; micro-ROS transport is **2 Mbaud**, and its separate debug output moves to UART7. Do not attach a serial monitor and agent to the same transport simultaneously.

There is a capacity inconsistency: the IDE setup selects **STM32H743VGT6**, while the Flash lesson assumes a **2 MB / two-bank** map ending at `0x081FFFFF`. Verify the actual fitted MCU and flash capacity in the programmer before using any sector/address example. The PDF repository alone cannot resolve the installed marking. Board routing and photographs are preserved in the introduction PDF; only those observed diagrams, not a newly inferred pinout, should guide a harness.

Sources: [M3P-156](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/1.Introduction%20to%20the%20Control%20Board/1.Introduction%20to%20the%20Control%20Board.pdf), [M3P-157](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/2.Set%20up%20the%20STM32CUBEIDE%20development%20environment/2.Set%20up%20the%20STM32CUBEIDE%20development%20environment.pdf), [M3P-167](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/13.Flash%20access%20data/13.Flash%20access%20data.pdf).

#### 1.Introduction to the Control Board <a href="#m3-m3p-156" id="m3-m3p-156"></a>

Identify the labelled front/back connectors from the original board photographs: left-rear LiDAR is UART4, right-front UART5, debug UART7, external control UART6, with separate SWD, CAN, SBUS, OLED, motors and servo rails. Power the board at its T-type input using the intended pack/harness; the controller's host USB link alone does not power motor/servo loads. For no movement, distinguish a missing battery/motor rail from a working USB logic link. Verify port labels and the actual voltage before connecting a replacement host or servo.

[M3P-156 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/1.Introduction%20to%20the%20Control%20Board/1.Introduction%20to%20the%20Control%20Board.pdf#page=1).

#### 2.Set up the STM32CUBEIDE development environment <a href="#m3-m3p-157" id="m3-m3p-157"></a>

The example uses STM32CubeIDE **1.19.0** on Windows 10 and creates a project for the stated STM32H743VGT6. Set the intended clock/peripherals in CubeMX, configure PC13 as an output named LED\_MCU, generate code and build. Zero compile errors/warnings is the IDE checkpoint, not a flashed/working board. Preserve the manufacturer's project configuration rather than regenerating it over a factory project without checking lost user sections and library settings.

[M3P-157 · official PDF, pp. 1–12](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/2.Set%20up%20the%20STM32CUBEIDE%20development%20environment/2.Set%20up%20the%20STM32CUBEIDE%20development%20environment.pdf#page=1).

#### 3.Burning STM32 firmware using SWD <a href="#m3-m3p-158" id="m3-m3p-158"></a>

For SWD programming connect the ST-LINK to the board's labelled SWD interface and power it as the lesson shows. In CubeIDE select the project, build, choose ST-LINK/SWD and program. For an existing HEX use STM32CubeProgrammer in ST-LINK/SWD mode, **Connect**, choose the exact HEX and **Start Programming**, then inspect completion. Select the correct target/voltage/firmware before writing; this is a firmware replacement workflow, not a harmless connectivity check.

[M3P-158 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/3.Burning%20STM32%20firmware%20using%20SWD/3.Burning%20STM32%20firmware%20using%20SWD.pdf#page=1).

#### 4.Burning STM32 firmware using serial port <a href="#m3-m3p-159" id="m3-m3p-159"></a>

Serial programming uses USB Connect, the CP210x driver and STM32CubeProgrammer **UART** mode. The screenshot shows **115200 baud, even parity, 8 data bits, 1 stop bit, no flow control, RTS Low and DTR Low**; select the observed COM port and verify these in the installed programmer, then hold BOOT, press/release RESET, then release BOOT to enter the bootloader. Connect, browse the correct HEX, program and inspect success before resetting into application mode. These bootloader settings differ from the runtime 2 Mbaud transport and from the standalone 8N1 debug UART. Restore factory firmware and its configuration before normal ROS use.

[M3P-159 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/4.Burning%20STM32%20firmware%20using%20serial%20port/4.Burning%20STM32%20firmware%20using%20serial%20port.pdf#page=1).

#### 5.Compile the microros driver library <a href="#m3-m3p-160" id="m3-m3p-160"></a>

Compile the static micro-ROS library on Ubuntu 22.04/Humble with the ARM cross-compiler and `micro_ros_setup` Humble branch. Create a `generate_lib` firmware workspace, configure `toolchain.cmake` and metadata, then build using the exact toolchain/metadata paths. The example limits are **1 node, 10 publishers, 10 subscriptions, 1 service, 1 client, history 10**, with custom transport. Increasing application entities beyond those compiled limits requires rebuilding the library as well as the MCU project. Retain compiler/branch/options with the generated headers/library; this PDF does not pin every transitive download. The build invocation passes both `firmware/toolchain.cmake` and `firmware/colcon.meta` to `micro_ros_setup build_firmware.sh`. After building, retain the generated headers and `libmicroros.a`, apply the documented include-directory layout correction, then add include/library paths and link name `microros` in CubeIDE. The long downloaded toolchain is not reproduced as a guessed one-line build.

[M3P-160 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/5.Compile%20the%20microros%20driver%20library/5.Compile%20the%20microros%20driver%20library.pdf#page=1).

#### 6.Install and start the microros agent <a href="#m3-m3p-161" id="m3-m3p-161"></a>

The course gives both Docker and source-built Humble agents. The serial invocation uses `/dev/myserial`, **2000000 baud** and verbosity 4; the Docker form mounts `/dev` and shared memory and uses host networking. Start only one instance. The source route builds `micro_ros_setup`, creates/builds the agent workspace and sources its install before `ros2 run micro_ros_agent micro_ros_agent serial --dev /dev/myserial -b 2000000 -v4`. Verify the MCU node appears; a running agent process alone does not prove transport success. Do not replace this transport with the generic Docker chapter's UDP example.

[M3P-161 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/6.Install%20and%20start%20the%20microros%20agent/6.Install%20and%20start%20the%20microros%20agent.pdf#page=1).

#### 7.Import Project <a href="#m3-m3p-162" id="m3-m3p-162"></a>

Import an existing supplied project into the chosen CubeIDE workspace using the project-import flow, select the intended project and build it before flashing. Inspect its MCU target, include paths, generated startup/linker files and required library assets rather than creating an empty project with the same name. A successful import only establishes IDE discovery. If build fails on the micro-ROS archive, compare the generated library architecture/toolchain with the project before editing hardware peripheral pins.

[M3P-162 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/1.Development%20environment%20setup/7.Import%20Project/7.Import%20Project.pdf#page=1).

#### 1.Turn on the LED light <a href="#m3-m3p-163" id="m3-m3p-163"></a>

Build `Board_Samples/STM32_Samples/Led`, flash the standalone image and observe PC13/LED\_MCU toggling through `HAL_GPIO_TogglePin`. GPIO output mode and board LED polarity must match the source configuration. This is the smallest MCU-only checkpoint, independent of the ROS agent. If flashing succeeds but the LED never changes, check that the MCU left bootloader/reset state and the selected GPIO/clock match the fitted board before reconnecting motor loads.

[M3P-163 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/1.Turn%20on%20the%20LED%20light/1.Turn%20on%20the%20LED%20light.pdf#page=1).

#### 2.Button functions <a href="#m3-m3p-173" id="m3-m3p-173"></a>

The Key sample reads **KEY1 on PC15**, configured input pull-up, and controls **LED\_ROS on PC14**. Verify released/pressed states and the debounced application behavior before adding a button-triggered action. A pull-up means the pressed electrical state can be low; do not reverse the meaning based only on an LED's active level. Keep this standalone project separate from the factory firmware's own button semantics.

[M3P-173 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/2.Button%20functions/2.Button%20functions.pdf#page=1).

#### 3.Drive the buzzer <a href="#m3-m3p-174" id="m3-m3p-174"></a>

The Beep sample drives the active buzzer on **PE5**, with KEY1 as an input. Build/flash the example, observe the intended on/off behavior and ensure it ends off. A continuously sounding low-voltage alarm in factory firmware has a different cause from the standalone GPIO test. Check the active-buzzer circuit and supply rather than applying an audio PWM assumption from a passive speaker.

[M3P-174 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/3.Drive%20the%20buzzer/3.Drive%20the%20buzzer.pdf#page=1).

#### 4.Serial communication <a href="#m3-m3p-175" id="m3-m3p-175"></a>

The Uart sample uses USART1, **PA9 TX / PA10 RX**, **115200 baud, 8 data bits, 1 stop bit, no parity**. The receive interrupt echoes a byte and rearms reception; printf is redirected through the same UART. Use USB Connect and the CP210x serial port, send a known short string and compare the echo. Seeing one byte and then silence suggests the receive path was not rearmed, not necessarily a bad physical cable.

[M3P-175 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/4.Serial%20communication/4.Serial%20communication.pdf#page=1).

#### 5.Battery voltage detection <a href="#m3-m3p-176" id="m3-m3p-176"></a>

The Adc sample reads battery sense on **PC0 / ADC1\_INP10**, with **12-bit** conversion. Its formula is `ADC_count × 3.30 / 4096 × 4.03` V, accounting for the divider. Compare the reported pack value with an independent voltage measurement before treating it as calibrated. The battery must be connected; a USB-powered MCU alone does not provide the voltage being measured. This circuit is a voltage indicator, not a battery state-of-charge or load-capacity test.

[M3P-176 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/5.Battery%20voltage%20detection/5.Battery%20voltage%20detection.pdf#page=1).

#### 6.Driving PWM Servo <a href="#m3-m3p-177" id="m3-m3p-177"></a>

The Pwm\_Servo sample uses **TIM12**, S1 on **PB15/channel 2** and S2 on **PB14/channel 1**. At the stated 240 MHz timer clock, prescaler 239 and period 19999 produce **50 Hz** pulses. Connect brown to GND, red to the selected supply and yellow to signal only for a compatible servo. The jumper selects **5 or 6.8 V**. `PwmServo_Set_Angle` maps targets into pulse widths; verify the servo's mechanical range before its sample 0/180° alternation.

[M3P-177 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/6.Driving%20PWM%20Servo/6.Driving%20PWM%20Servo.pdf#page=1).

#### 7.Drive motor <a href="#m3-m3p-178" id="m3-m3p-178"></a>

The Motor sample directly drives the four motor outputs using TIM1/TIM8 PWM. The example TIM1 clock, prescaler 4 and period 1999 calculate **24 kHz**; this is switching frequency, not motor-control update rate. `Motor_Set_Pwm` applies sign, dead-zone compensation and limits; `Motor_Stop` distinguishes coast/stop from brake. Motors can start immediately after flashing, so support the chassis before connecting the battery. Verify each motor ID/direction separately before using a Mecanum combination.

[M3P-178 · official PDF, pp. 1–13](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/7.Drive%20motor/7.Drive%20motor.pdf#page=1).

#### 8.Read motor encoder data <a href="#m3-m3p-179" id="m3-m3p-179"></a>

The Encoder sample configures TIM2/3/4/5 as quadrature counters, uniformly using **0–65535** despite different timer widths. Read signed count deltas and handle wraparound before calculating speed. Compare a manually rotated wheel's sign and change on each channel to the source's HxA/HxB wiring diagram. A motor turning with zero counts points to encoder supply/signal routing, whereas negative feedback from a positive command may be a direction/sign mismatch.

[M3P-179 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/8.Read%20motor%20encoder%20data/8.Read%20motor%20encoder%20data.pdf#page=1).

#### 9.PID control of motor speed <a href="#m3-m3p-180" id="m3-m3p-180"></a>

The PID sample converts encoder changes into motor feedback and updates per-motor PID toward targets through `PID_Set_Motor_Target` / `Motion_Set_Speed`. The sample passes **300** to each target; inspect the implementation's speed units instead of assuming these values are m/s or raw PWM. Clear accumulated control state with the relevant reset function when stopping/restarting. Tune only after direction and encoder feedback work; a feedback sign error can make a nominal PID amplify the error.

[M3P-180 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/9.PID%20control%20of%20motor%20speed/9.PID%20control%20of%20motor%20speed.pdf#page=1).

#### 10.Robot kinematics analysis theory <a href="#m3-m3p-164" id="m3-m3p-164"></a>

The kinematics lesson relates body X/Y/yaw to individual Mecanum wheel speeds and reconstructs chassis motion from wheel feedback. Use the actual wheel positions, roller orientation and motor sign conventions in its diagram. Test forward, lateral and yaw components separately, then their combinations. Encoder counts become metric motion only after wheel/reduction/geometry conversion and timing; do not equate PWM duty or counts with body velocity. Validate those conventions before odometry scale calibration.

[M3P-164 · official PDF, pp. 1–14](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/10.Robot%20kinematics%20analysis%20theory/10.Robot%20kinematics%20analysis%20theory.pdf#page=1).

#### 11.Read IMU data <a href="#m3-m3p-165" id="m3-m3p-165"></a>

The Read\_IMU sample communicates with **ICM20948 over SPI2** and reads accelerometer, gyro and magnetometer data. The shown gyro setting is **±2000 dps** with scale **16.4 LSB/(°/s)**; magnetometer conversion shows **0.15** per raw unit in the manufacturer's routine. Keep the matching selected scale when converting raw values. Inspect stationary biases and axis response before fusion; these raw units are not automatically the ROS `Imu` SI contract. Preserve the sample's initialization/bias steps and distinguish raw counts from converted data.

[M3P-165 · official PDF, pp. 1–12](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/11.Read%20IMU%20data/11.Read%20IMU%20data.pdf#page=1).

#### 12.Read Lidar data <a href="#m3-m3p-166" id="m3-m3p-166"></a>

Read\_Lidar uses **UART4 PC10 TX / PC11 RX**, **230400 baud, 8N1** and receive DMA. The routine accumulates protocol bytes, parses a complete T-mini Plus frame and reports the 0° distance about every **200 ms** over the separate **115200 baud** debug link. A bad parsed value can result from frame/checksum or DMA-buffer handling even when bytes arrive. Do not change the host micro-ROS baud to 230400: that number belongs to the internal scanner UART.

[M3P-166 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/12.Read%20Lidar%20data/12.Read%20Lidar%20data.pdf#page=1).

#### 13.Flash access data <a href="#m3-m3p-167" id="m3-m3p-167"></a>

The Flash sample changes stored data with KEY1 and verifies it across reset, teaching erase-before-write and sector-address handling. Its printed map assumes **two 1 MB banks / 128 KB sectors**, which conflicts with the chip-capacity identification elsewhere; resolve the fitted device before selecting a sector. Keep data sectors out of linked program storage and retain a recovery image. A successful write/read in RAM is not persistence; reset/power-cycle and re-read after a controlled test.

[M3P-167 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/13.Flash%20access%20data/13.Flash%20access%20data.pdf#page=1).

#### 14.Driving OLED Displays <a href="#m3-m3p-168" id="m3-m3p-168"></a>

The OLED example targets a **0.91-inch I2C** display through software I2C, **PB10 SCL / PB11 SDA**. It initializes the SSD1306-style display, updates a frame buffer and writes it over the bus. Align GND/VCC/SCL/SDA according to the original connector diagram. For a blank display, check supply and acknowledged address before text drawing routines. Two parallel connector rows have the same function; they are not distinct controllers.

[M3P-168 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/14.Driving%20OLED%20Displays/14.Driving%20OLED%20Displays.pdf#page=1).

#### 15.Driving RGB light strip <a href="#m3-m3p-169" id="m3-m3p-169"></a>

The RGB sample encodes WS2812 bits via **SPI4 + DMA**, shown at **3.75 MHz**. Encoded one/zero symbols are **0x0E / 0x08**, with GRB ordering, eight LEDs and a reset interval. `RGB_Set_Color` updates the buffer; `RGB_Update` transmits it. A correctly updated software color is invisible until transmission completes. Preserve timing and byte order when adapting the routine; standard SPI slave-register assumptions do not apply to this waveform-encoded strip.

[M3P-169 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/15.Driving%20RGB%20light%20strip/15.Driving%20RGB%20light%20strip.pdf#page=1).

#### 16.SBUS model aircraft remote control <a href="#m3-m3p-170" id="m3-m3p-170"></a>

The SBUS sample connects GND, **5 V** and SBUS signal to the labelled receiver port. USART2 is configured **100000 baud**, **9-bit word setting with even parity**, **2 stop bits** in the STM32 HAL, and the parser unpacks 11-bit channel fields. Verify decoded neutral/endpoints and frame flags before mapping channels to motors. This optional model-aircraft receiver is distinct from the host USB gamepad; its serial framing must not be copied onto the micro-ROS port.

[M3P-170 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/16.SBUS%20model%20aircraft%20remote%20control/16.SBUS%20model%20aircraft%20remote%20control.pdf#page=1).

#### 17.USB controller remote control <a href="#m3-m3p-171" id="m3-m3p-171"></a>

The USB\_Host sample handles a gamepad receiver directly on the MCU USB host interface and reads HID reports through `USBH_HID_EventCallback`. It compares reports and throttles repeated sends before updating application controls. Check that USB enumerates and raw reports change before binding axes to motors/servos. This firmware is separate from the ROS host's `/dev/input/js0` joystick stack; successful enumeration in one does not establish the other is running.

[M3P-171 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/17.USB%20controller%20remote%20control/17.USB%20controller%20remote%20control.pdf#page=1).

#### 18.CAN bus communication <a href="#m3-m3p-172" id="m3-m3p-172"></a>

The CAN sample initializes FDCAN at **1000 kbit/s**, configures accepted frames/notifications and demonstrates an **8-byte** payload with a standard 11-bit identifier (example **0x000B**). Receive FIFO callbacks retrieve headers and data; transmit uses `HAL_FDCAN_AddMessageToTxFifoQ`. Match the actual bus bit timing, physical transceiver wiring and termination with the peer before sending. This example is bus communication, not an identified robot motor command protocol for arbitrary CAN devices.

[M3P-172 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/18.CAN%20bus%20communication/18.CAN%20bus%20communication.pdf#page=1).

#### 1.Post a topic <a href="#m3-m3p-181" id="m3-m3p-181"></a>

The Publisher sample initializes allocator/support/domain, custom serial transport, `/YB_Example_Node`, an Int32 publisher and a timer/executor. Start the 2 Mbaud agent, then inspect `/int32_publisher` with `ros2 topic echo` and `hz`; expect changing counter data. MCU debug output is on UART7 at 115200, not the agent port. Missing messages with a visible node calls for checking timer/executor registration and spin, not only recreating the publisher.

[M3P-181 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/3.Control%20board%20micro_ros%20basic%20routine/1.Post%20a%20topic/1.Post%20a%20topic.pdf#page=1).

#### 2.Subscribe to a topic <a href="#m3-m3p-182" id="m3-m3p-182"></a>

The Subscriber sample registers `/int32_subscriber` and its callback with the rclc executor. After agent discovery, publish `std_msgs/msg/Int32` with **data: 100** once and inspect the debug callback result. Message type and domain must match. A node appearing in discovery does not prove the subscription callback is being spun. Preserve static-message memory lifetime; do not point a callback at a temporary object that expires before execution.

[M3P-182 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/3.Control%20board%20micro_ros%20basic%20routine/2.Subscribe%20to%20a%20topic/2.Subscribe%20to%20a%20topic.pdf#page=1).

#### 3.Multi-topic subscription and publishing <a href="#m3-m3p-183" id="m3-m3p-183"></a>

The multi-topic sample exposes `/subscriber_1`, `/subscriber_2`, `/subscriber_3` and corresponding `/int32_publisher_1` through `_3`. The lesson tests inputs **123/456/789**, with each publisher driven by a separately registered timer. Check each topic's count/rate rather than treating one working channel as proof of all handles. The rclc executor capacity and compiled micro-ROS entity limits must accommodate all subscriptions and timers; adding a handle only in application code is insufficient when the static library limits are exceeded.

[M3P-183 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/3.Control%20board%20micro_ros%20basic%20routine/3.Multi-topic%20subscription%20and%20publishing/3.Multi-topic%20subscription%20and%20publishing.pdf#page=1).

#### 4.Subscribe to the buzzer topic <a href="#m3-m3p-184" id="m3-m3p-184"></a>

The buzzer subscriber accepts **UInt16** on `/beep`: the source demonstrates **1** for on, **0** for off and **300** for a timed pulse. Confirm the callback's time interpretation in the installed sample before treating a nonzero value as a generic bool. Run with the teaching firmware and verify the buzzer returns off. It is a useful non-motion micro-ROS command checkpoint but still different from merely subscribing to feedback.

[M3P-184 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/3.Control%20board%20micro_ros%20basic%20routine/4.Subscribe%20to%20the%20buzzer%20topic/4.Subscribe%20to%20the%20buzzer%20topic.pdf#page=1).

#### 5.Subscribe to the bus servo topic <a href="#m3-m3p-185" id="m3-m3p-185"></a>

The bus-servo subscriber receives `arm_msgs/msg/ArmJoint` on `/arm_joint`. The example commands **ID 1, 60°/120°, time 1000 ms**; the servo rail requires the battery. Verify the correct bus/servo ID and supported range before a move. A functioning ROS subscriber with no torque can mean the servo power rail is absent. Restore the factory image after the teaching firmware experiment before interpreting all-six-joint behavior.

[M3P-185 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/3.Control%20board%20micro_ros%20basic%20routine/5.Subscribe%20to%20the%20bus%20servo%20topic/5.Subscribe%20to%20the%20bus%20servo%20topic.pdf#page=1).

#### 6.Subscribe to the rate control topic <a href="#m3-m3p-186" id="m3-m3p-186"></a>

The rate-control subscriber maps `/cmd_vel` `Twist` into chassis inverse kinematics. The PDF's examples include **0.5 m/s** forward and **1.5 rad/s** yaw followed by a separate all-zero command; they are demonstration targets, not first-run recommendations. Support the chassis and verify signs/stop behavior before floor operation. This firmware's node is the teaching node; absence of the factory `/YB_Node` is expected until factory firmware is restored.

[M3P-186 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/3.Control%20board%20micro_ros%20basic%20routine/6.Subscribe%20to%20the%20rate%20control%20topic/6.Subscribe%20to%20the%20rate%20control%20topic.pdf#page=1).

#### 7.Release Speed Topic <a href="#m3-m3p-187" id="m3-m3p-187"></a>

The “Release Speed Topic” sample publishes `/odom_raw` as `nav_msgs/msg/Odometry`, integrating body velocities over elapsed time while accepting `/cmd_vel`. The timer constant is **50 ms**, giving a nominal **20 Hz** publication opportunity; measured `ros2 topic hz` is still required. Check frame IDs, timestamps and twist/pose fields separately. Velocity-derived integration drifts and is not ground truth; use it as the raw input to the host odometry/fusion chain.

[M3P-187 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/3.Control%20board%20micro_ros%20basic%20routine/7.Release%20Speed%20Topic/7.Release%20Speed%20Topic.pdf#page=1).

#### 8.Publish IMU data topic <a href="#m3-m3p-188" id="m3-m3p-188"></a>

The IMU sample publishes `/imu/data_raw` and `/imu/mag`, setting `imu_frame` and a timer of **40 ms** (nominal **25 Hz**). Convert acceleration/angular velocity/magnetic fields to the actual ROS message units before publication; do not publish raw ADC/IMU counts as SI data. Inspect stationary values and timestamp continuity with topic echo/hz. These nominal timers describe the sample code, not measured throughput of the factory firmware.

[M3P-188 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/3.Control%20board%20micro_ros%20basic%20routine/8.Publish%20IMU%20data%20topic/8.Publish%20IMU%20data%20topic.pdf#page=1).

#### 9.Publish radar data topic <a href="#m3-m3p-189" id="m3-m3p-189"></a>

The single-LiDAR micro-ROS sample publishes `/scan` in `laser_frame`, with **666** sample slots, **0.541°** angular interval and a **140 ms** timer. Validate angle indexing, invalid returns, units and array bounds before visualization. This teaching `/scan` is a raw single-sensor output; the factory dual-LiDAR application uses `/scan0` and `/scan1` before merging/filtering to another `/scan`. Do not run a raw teaching publisher and factory filter on the same topic name.

[M3P-189 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/3.Control%20board%20micro_ros%20basic%20routine/9.Publish%20radar%20data%20topic/9.Publish%20radar%20data%20topic.pdf#page=1).

### 19. Docker fundamentals and image-specific boundaries <a href="#m3-course-19" id="m3-course-19"></a>

These are general Docker lessons with older **Ubuntu 20.04 / ROS Foxy** workstation examples and Docker **20.10.21+** mentioned in their prerequisites. They explain mechanisms; they are not an instruction to replace NX's native Humble image. The control-board agent chapter's serial **2 Mbaud** transport is the factory reference; this generic Docker collection also shows an unrelated UDP4 agent example on port 8888. Do not combine them without matching the firmware transport.

Sources: [M3P-190](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/19.Docker%20Course/1.Docker%20overview%20and%20docker%20installation/1%E3%80%81Docker%20overview%20and%20docker%20installation.pdf), [M3P-194](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/19.Docker%20Course/5.Enter%20the%20bot's%20docker%20container/5%E3%80%81Enter%20the%20bot's%20docker%20container.pdf).

#### 1、Docker overview and docker installation <a href="#m3-m3p-190" id="m3-m3p-190"></a>

The overview distinguishes client, daemon, image and container. Verify an existing Docker installation with `docker version` and a deliberately selected test image before considering installation. The PDF's piped convenience installer is historical setup guidance, not a required step on the preconfigured robot. A successful hello-world validates container execution, not USB, GPU, ROS networking or robot access.

[M3P-190 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/19.Docker%20Course/1.Docker%20overview%20and%20docker%20installation/1%E3%80%81Docker%20overview%20and%20docker%20installation.pdf#page=1).

#### 2、Common commands for docker image containers <a href="#m3-m3p-191" id="m3-m3p-191"></a>

Use `docker images`, `docker ps -a`, `docker start/stop`, logs and `docker exec -it CONTAINER bash` to distinguish a missing image, stopped container and failed process. `exec` adds a shell to an existing container; `attach` joins its main process and has different exit effects. Inspect the exact target before deletion. The source's bulk-remove examples are not useful robot recovery defaults because they can remove the agent, roadnet or stored environment.

[M3P-191 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/19.Docker%20Course/2.Common%20commands%20for%20docker%20image%20containers/2%E3%80%81Common%20commands%20for%20docker%20image%20containers.pdf#page=1).

#### 3、Docker images deeply understand and publish images <a href="#m3-m3p-192" id="m3-m3p-192"></a>

A Dockerfile and `docker build -f ... -t NAME:TAG .` describe a repeatable image; `docker commit` captures a running container's filesystem changes but not its external mounted data. Record base-image version, build context and robot-specific configuration. Build/test locally before any registry push. The source's Foxy image/tag examples are not NX Humble compatibility evidence, and no image was built or published here.

[M3P-192 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/19.Docker%20Course/3.Docker%20images%20deeply%20understand%20and%20publish%20images/3%E3%80%81Docker%20images%20deeply%20understand%20and%20publish%20images.pdf#page=1).

#### 4、Docker hardware interaction and data processing <a href="#m3-m3p-193" id="m3-m3p-193"></a>

`--device` exposes a chosen device, `-v HOST:CONTAINER` binds a directory and `docker cp` copies data. Graphical programs also need the intended X/display access; sharing a file does not provide GUI permission. Verify device names and mounts with inspection before adding privileges. Maps/calibration on a host bind mount persist differently from files only in a disposable container. Do not replace a read-only configuration mount with a broad writable host mount to repair an unrelated application error.

[M3P-193 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/19.Docker%20Course/4.Docker%20hardware%20interaction%20and%20data%20processing/4%E3%80%81Docker%20hardware%20interaction%20and%20data%20processing.pdf#page=1).

#### 5、Enter the bot's docker container <a href="#m3-m3p-194" id="m3-m3p-194"></a>

This generic container-entry lesson includes a **UDP4 port 8888** micro-ROS example, unlike the M3 Pro control-board chapter's factory **serial /dev/myserial at 2 Mbaud**. Identify which firmware/project is being taught before starting an agent. Inspect a running container and `/YB_Node` rather than launching a second one. For the Pi/original Nano application container, follow the model configuration lesson; Orin's application ROS remains native.

[M3P-194 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/19.Docker%20Course/5.Enter%20the%20bot's%20docker%20container/5%E3%80%81Enter%20the%20bot's%20docker%20container.pdf#page=1).

#### 6、Robot development environment construction in Docker <a href="#m3-m3p-195" id="m3-m3p-195"></a>

The development workflow uses SSH/remote editing or Jupyter to inspect files inside the chosen robot/container environment. Bind the intended workspace, select the correct interpreter/ROS shell and verify where edits are saved before building. A browser on port 8888 is the Jupyter example, not the OpenClaw gateway or MCP endpoint. Confirm a changed source/configuration is actually the one installed by the running package; editing an unused checkout will not change the robot.

[M3P-195 · official PDF, pp. 1–16](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/19.Docker%20Course/6.Robot%20development%20environment%20construction%20in%20Docker/6%E3%80%81Robot%20development%20environment%20construction%20in%20Docker.pdf#page=1).

### 20. OpenCV image-processing foundations <a href="#m3-course-20" id="m3-course-20"></a>

These lessons use Python OpenCV/NumPy on images, not a new camera driver. OpenCV color arrays are normally **BGR**, while MediaPipe expects RGB and ROS image encodings are explicit. Array indices are **\[row y, column x]**; image sizes passed to many OpenCV functions are **(width,height)**. Several printed snippets mix width/height, include malformed quotes or legacy constant prefixes. The following explains the intended APIs without reproducing those broken listings as runnable programs.

Sources: [M3P-205](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/2.%20Image%20reading%20and%20display/1.%20Introduction%20to%20Open%20Source%20CV.pdf).

#### 1. Introduction to Open Source CV <a href="#m3-m3p-196" id="m3-m3p-196"></a>

OpenCV supplies image loading, transforms, filtering and annotation; NumPy supplies the array representation used by the remaining lessons. Check `import cv2` in the intended Python/ROS environment before installing another copy. Mixing system and pip OpenCV can change GUI and ABI behavior. A successful import only establishes the library, not that the ROS camera or a GUI display works.

[M3P-196 · official PDF, pp. 1–1](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/1.%20Introduction%20to%20Open%20Source%20CV/1.%20Introduction%20to%20Open%20Source%20CV.pdf#page=1).

#### 2. Image reading and display <a href="#m3-m3p-205" id="m3-m3p-205"></a>

`cv2.imread(PATH, flag)` returns image data: color flag 1, grayscale 0 and unchanged -1 preserve the intended channels. Check for a failed/None result before accessing shape. `imshow` needs a GUI event loop with `waitKey`; the notebook example instead JPEG-encodes an image for display. Convert BGR to RGB for RGB-oriented viewers rather than interpreting swapped red/blue as a camera fault.

[M3P-205 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/2.%20Image%20reading%20and%20display/1.%20Introduction%20to%20Open%20Source%20CV.pdf#page=1).

#### 3. Image writing <a href="#m3-m3p-206" id="m3-m3p-206"></a>

`cv2.imwrite(OUTPUT_PATH, image)` saves the processed array. Check its boolean result and reopen the output to verify shape/content. The notebook cannot always execute native `imshow`; the source recommends running a `.py` in a graphical terminal for that method. A file existing does not establish that the intended image/color encoding was written.

[M3P-206 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/3.%20Image%20writing/3.%20Image%20writing.pdf#page=1).

#### 4. Image quality <a href="#m3-m3p-207" id="m3-m3p-207"></a>

`IMWRITE_JPEG_QUALITY` uses a **0–100** quality scale; PNG compression uses **0–9**. JPEG is lossy, so changing quality changes image content; PNG compression trades CPU/storage while preserving pixels. The PDF sometimes uses obsolete `CV_IMWRITE_*` names; check the installed constants. Preserve the uncompressed/raw depth representation for measurement rather than passing depth through a lossy JPEG workflow.

[M3P-207 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/4.%20Image%20quality/4.%20Image%20quality.pdf#page=1).

#### 5. Pixel Operation <a href="#m3-m3p-208" id="m3-m3p-208"></a>

Access a BGR pixel with `image[y,x]` or a channel with `image[y,x,c]`, then inspect dtype/range before writing it. A NumPy color image is generally height × width × channels; indexing x/y in reverse can silently return a different pixel. Use a known small patch to verify channel ordering before adapting the operation to segmentation or overlay code.

[M3P-208 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/5.%20Pixel%20Operation/5.%20Pixel%20Operation.pdf#page=1).

#### 6. Image zoom <a href="#m3-m3p-209" id="m3-m3p-209"></a>

`cv2.resize(image, (new_width,new_height), interpolation=...)` changes image dimensions; alternatively use fx/fy with a zero size. Nearest-neighbor preserves label values while other interpolation choices smooth normal color images. Scaling an image used for metric geometry requires corresponding intrinsic-coordinate handling. Resizing depth and color to equal dimensions alone does not register their viewpoints.

[M3P-209 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/6.%20Image%20zoom/6.%20Image%20zoom.pdf#page=1).

#### 7. Image cutting <a href="#m3-m3p-210" id="m3-m3p-210"></a>

Crop using NumPy slicing `image[y0:y1,x0:x1]`; endpoints are exclusive. Keep the crop origin with the ROI so detector points can be translated back to full-image coordinates. A crop may be a view of the original array; explicitly copy when editing it independently. A cropped center without its origin cannot be directly passed to the full-frame depth/grasp helper.

[M3P-210 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/7.%20Image%20cutting/7.%20Image%20cutting.pdf#page=1).

#### 8. Image translation <a href="#m3-m3p-211" id="m3-m3p-211"></a>

Translation uses a **2 × 3** affine matrix with x/y pixel shifts and `cv2.warpAffine`. The destination size is width/height, even when array shape is height/width; the source's mixed variable names need correction on a non-square test image. Inspect border fill and target bounds. A translated visual annotation does not update the camera's intrinsic model or physical extrinsic transform.

[M3P-211 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/8.%20Image%20translation/8.%20Image%20translation.pdf#page=1).

#### 9. Image Mirroring <a href="#m3-m3p-212" id="m3-m3p-212"></a>

The mirroring example reverses the appropriate NumPy row/column order to flip the image. Keep track of whether horizontal, vertical or both axes were reversed before interpreting landmark x/y. Test with an asymmetric image containing a readable label. A mirrored preview may be comfortable for a user, but its coordinates must be unmirrored before comparison with raw depth or robot-frame geometry.

[M3P-212 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/9.%20Image%20Mirroring/9.%20Image%20Mirroring.pdf#page=1).

#### 10. Affine Transformation <a href="#m3-m3p-197" id="m3-m3p-197"></a>

`cv2.getAffineTransform` derives a 2 × 3 matrix from **three corresponding non-collinear points**, then `warpAffine` resamples the source into the chosen output size. Check point order and inspect a known marker after transformation. Affine pixel alignment handles a planar image transform, not general RGB-D registration or a robot camera-to-base calibration.

[M3P-197 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/10.%20Affine%20Transformation/10.%20Affine%20Transformation.pdf#page=1).

#### 11. Image Rotation <a href="#m3-m3p-198" id="m3-m3p-198"></a>

`cv2.getRotationMatrix2D((cx,cy), angle, scale)` returns a 2 × 3 rotation/scale matrix; use `warpAffine` with the intended canvas size. The source's swapped center/destination dimensions and malformed image filename are not reliable copy-paste code. Verify a non-square image and account for clipping when the rotated content exceeds the canvas. This angle is in degrees, unlike robot roll/pitch/yaw in rad.

[M3P-198 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/11.%20Image%20Rotation/11.%20Image%20Rotation.pdf#page=1).

#### 13. Grayscale processing <a href="#m3-m3p-199" id="m3-m3p-199"></a>

`cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)` converts a BGR image into grayscale; `imread(...,0)` loads grayscale directly. The result has one channel, so downstream code must not index three color components. Compare expected brightness/shape before thresholding. Converting grayscale for display is different from reconstructing lost color information.

[M3P-199 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/13.%20Grayscale%20processing/13.%20Grayscale%20processing.pdf#page=1).

#### 14. Image Binarization <a href="#m3-m3p-200" id="m3-m3p-200"></a>

`cv2.threshold(src, threshold, maxValue, type)` returns the used threshold and output image. Binary/binary-inverse, truncation and to-zero modes preserve/set different values; inspect a grayscale ramp to verify the chosen polarity. Do not copy the PDF's inconsistent prose about to-zero behavior without comparing the output. Tune thresholds on representative lighting, not a single promotional image.

[M3P-200 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/14.%20Image%20Binarization/14.%20Image%20Binarization.pdf#page=1).

#### 15. Edge Detection <a href="#m3-m3p-201" id="m3-m3p-201"></a>

The edge lesson shows grayscale conversion, a **3 × 3** Gaussian blur and Canny edges. Keep the input actually connected to the intended preprocessing; the printed example computes blur but calls `Canny` on another array. Inspect noise and contours while changing the low/high thresholds. A strong image edge is not necessarily the physical edge/drop-off detected by the depth-camera driving exercise.

[M3P-201 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/15.%20Edge%20Detection/15.%20Edge%20Detection.pdf#page=1).

#### 16. Line drawing <a href="#m3-m3p-202" id="m3-m3p-202"></a>

`cv2.line` draws between integer image points using BGR color, thickness and optional anti-aliasing (`LINE_AA`). Verify x/y and use a copy when annotations must not modify the array fed to inference. Pixel thickness is a display choice, not physical line width. Test an overlay against a known marker before using it to diagnose target alignment.

[M3P-202 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/16.%20Line%20drawing/16.%20Line%20drawing.pdf#page=1).

#### 17. Rectangle and circle drawing <a href="#m3-m3p-203" id="m3-m3p-203"></a>

`rectangle`, `circle`, `ellipse` and `polylines` annotate regions, using the API's point/axes/radius conventions and negative thickness/`FILLED` for filling. A circle radius is in pixels; ellipse axes are not a robot-frame dimension. Keep detector coordinates clipped to the image and inspect the original image beneath an outline before trusting a region selection.

[M3P-203 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/17.%20Rectangle%20and%20circle%20drawing/17.%20Rectangle%20and%20circle%20drawing.pdf#page=1).

#### 18. Drawing text and pictures <a href="#m3-m3p-204" id="m3-m3p-204"></a>

`cv2.putText` takes the text baseline origin, font, scale, BGR color and thickness; the example combines it with a rectangle. Standard Hershey text is limited compared with full Unicode rendering. Preserve captions that identify units and frame near a diagnostic number, such as “depth m” versus “servo deg.” An overlay label must reflect measured/returned data rather than a fabricated fixed success string.

[M3P-204 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/20.Image%20Processing%20Basics%20Course/18.%20Drawing%20text%20and%20pictures/18.%20Drawing%20text%20and%20pictures.pdf#page=1).

### 21. Orin NX host maintenance and recovery <a href="#m3-course-21" id="m3-course-21"></a>

Only the **Jetson Orin Nano\_NX** branch below is a host-maintenance candidate for this SKU. The **28** Raspberry Pi/original Nano PDFs are explicitly excluded from NX recovery and listed by host in the alternative-host table below. The course branch covers both Orin Nano and NX; its image filenames, disk offsets, power modes and capacities are not automatically the exact NX SUPER16GB configuration.

Sources: [M3P-227](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/2.Restore%20the%20factory%20image%20system/2.%20Restore%20the%20factory%20image%20system.pdf).

#### 1.Jetson Orin board introduction <a href="#m3-m3p-225" id="m3-m3p-225"></a>

Identify the actual Orin module/carrier, SSD and connectors against the original introduction diagram before changing host wiring. “Orin Nano/NX” is a family branch rather than evidence every photograph is the purchased NX SUPER16GB assembly. Retain installed JetPack/image identifiers and the 12 V host harness described in the controller course. Do not transfer original Jetson Nano or Raspberry Pi boot-media/power assumptions to this host.

[M3P-225 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/1.Jetson%20Orin%20board%20introduction/1.Jetson%20Orin%20board%20introduction.pdf#page=1).

#### 2. Restore the factory image system <a href="#m3-m3p-227" id="m3-m3p-227"></a>

The recovery lesson writes a complete manufacturer disk image to an SSD using a PC and SSD enclosure, then reinstalls it in the Orin. Choose the exact NX/JetPack image from the official resource folder and independently identify the target drive by model/capacity before writing. Its preliminary format instructions conflict (exFAT versus NTFS); neither filesystem wording establishes the correct image or target. Keep maps, calibration and configuration backed up separately. No SSD was removed, formatted or flashed for this reference.

[M3P-227 · official PDF, pp. 1–13](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/2.Restore%20the%20factory%20image%20system/2.%20Restore%20the%20factory%20image%20system.pdf#page=1).

#### 3.Backup SSD system <a href="#m3-m3p-228" id="m3-m3p-228"></a>

On an Ubuntu backup PC, attach the SSD through an enclosure and inspect its partition table before any resizing. The lesson shrinks/inspects partitions and copies a calculated byte/sector extent into an image using dd; `/dev/sdb`, image name and `count=41822208` are examples for the author's disk. Never reuse that count or device path for an unidentified 256 GB NX SSD. Preserve all required partitions and verify a backup's size/content before relying on it for recovery; a copied root directory is not a complete bootable disk image.

[M3P-228 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/3.Backup%20SSD%20system/3.Backup%20SSD%20system.pdf#page=1).

#### 4.SSD expansion <a href="#m3-m3p-229" id="m3-m3p-229"></a>

When a restored image exposes less storage than the physical SSD, the source uses GParted to inspect and expand the relevant partition into available unallocated space. Identify the correct disk/partition and retain a backup before resizing. Confirm the resulting partition and filesystem sizes with the host tools afterward. A larger partition does not prove the operating system or robot configuration survived; test a normal boot and retained data separately.

[M3P-229 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/4.SSD%20expansion/4.SSD%20expansion.pdf#page=1).

#### 5.Network configuration <a href="#m3-m3p-230" id="m3-m3p-230"></a>

Use the Ubuntu 22.04 network GUI for client Wi-Fi/hotspot configuration and inspect the actual address (`ifconfig` in the lesson). A hotspot provides a local network unless upstream internet sharing exists; cloud models additionally require routed access. After switching networks, reconnect SSH/VNC to the new address and keep the controller/workstation in the intended ROS domain. OLED Ethernet priority can make the displayed address differ from the Wi-Fi address.

[M3P-230 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/5.Network%20configuration/5.Network%20configuration.pdf#page=1).

#### SSH remote login <a href="#m3-m3p-231" id="m3-m3p-231"></a>

SSH into the actual displayed robot IP using the Orin account, accepting a first host-key association only after identifying the device. A shell session is sufficient for ROS CLI/configuration but does not itself supply camera/RViz desktop windows. If login works yet remote ROS discovery fails, investigate DDS/domain/network separately. If the IP changed after switching Wi-Fi, reconnect to that new address before editing credentials or reinstalling SSH.

[M3P-231 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/6.SSH%20remote%20login/SSH%20remote%20login.pdf#page=1).

#### VNC remote control <a href="#m3-m3p-232" id="m3-m3p-232"></a>

The Orin lesson uses Ubuntu 22.04's screen-sharing/remote desktop setup and an optional locked-desktop extension, not the original Nano's Vino recipe. Ensure the intended local session/display is available; the manufacturer allows only one Orin remote desktop connection at a time. For a screen-equipped kit use its working display path. The separate headless Xorg workaround changes DP behavior and should not be applied merely to repair an incorrect VNC address.

[M3P-232 · official PDF, pp. 1–17](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/7.VNC%20remote%20control/VNC%20remote%20control.pdf#page=1).

#### Remote file transfer <a href="#m3-m3p-233" id="m3-m3p-233"></a>

Use an SSH-capable file-transfer client to copy a known small file to the intended `/home/jetson` directory and compare size/content before moving maps or models. Confirm direction: download preserves a robot file locally; upload changes the robot copy. A successful copy into a home directory does not update a package's installed share directory. Back up YAML before replacing it and preserve line endings/permissions for scripts.

[M3P-233 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/8.Remote%20file%20transfer/Remote%20file%20transfer.pdf#page=1).

#### Jtop tool <a href="#m3-m3p-234" id="m3-m3p-234"></a>

`jtop` (jetson-stats) shows host load, memory, power/thermal status and performance configuration. The PDF's `nvpmodel -m 2` and `jetson_clocks` are board/image-specific tuning examples; power-mode number 2 is **not** a universal NX SUPER mode. Inspect the installed mode definitions and thermal/power setup before changing performance. Compare inference CPU/GPU/memory use in a controlled workload; do not report the course's settings as measured performance.

[M3P-234 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/9.Jtop%20tool/Jtop%20tool.pdf#page=1).

#### Exchange space expansion <a href="#m3-m3p-226" id="m3-m3p-226"></a>

The swap lesson disables nvzramconfig and creates an **8 GB** swap file with fallocate/mkswap/swapon, then describes persistence. Inspect existing swap/memory pressure and available SSD space before adopting it. Swap can reduce out-of-memory failure but does not increase GPU memory or guarantee model compatibility. Preserve the original configuration so it can be restored; performance under swap needs actual workload measurement and was not tested here.

[M3P-226 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Orin%20Nano_NX/10.Exchange%20space%20expansion/Exchange%20space%20expansion.pdf#page=1).

### 22. Linux support skills used by the robot courses <a href="#m3-course-22" id="m3-course-22"></a>

These are general administration exercises. Prefer the model/Orin-specific instructions for power, camera, firmware, VNC and image recovery. Several generic lessons use an older robot library, original-Nano peripherals or Raspberry Pi files; those examples do not establish compatibility with this NX SKU.

Sources: [M3P-252](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/10.Driver%20library%20and%20communication/10.Driver%20library%20and%20communication.pdf).

#### 1.Introduction to Linux system <a href="#m3-m3p-251" id="m3-m3p-251"></a>

The Linux introduction distinguishes distributions and roles. On a robot, record the actual distribution/release and architecture before selecting a package or binary. A Linux-compatible application is not automatically compatible with Jetson's ARM64 GPU/runtime stack. Use the supplied Ubuntu/Humble image as the baseline rather than replacing it because another distribution appears in the overview.

[M3P-251 · official PDF, pp. 1–1](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/1.Introduction%20to%20Linux%20system/1.Introduction%20to%20Linux%20system.pdf#page=1).

#### 2.Ubuntu file system <a href="#m3-m3p-257" id="m3-m3p-257"></a>

Understand `/home`, `/etc`, `/dev`, `/tmp` and system paths before editing a robot configuration. Source workspaces, installed packages and device files have different lifetimes/purposes. `~` resolves to the active user's home, so it differs between the NX `jetson` shell and a root container. A path copied with `/root` can silently target the wrong environment on a native Orin terminal.

[M3P-257 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/2.Ubuntu%20file%20system/2.Ubuntu%20file%20system.pdf#page=1).

#### 3.Ubuntu common commands <a href="#m3-m3p-258" id="m3-m3p-258"></a>

Use pwd/listing/copy/move/permissions and system-information commands to identify the current working directory, files and host resources. `uname -a`, `df -h`, CPU/memory inspection and network status help attach an actual environment to an error report. Replace placeholder usernames/paths. Broad `chmod 777`, root-password changes and recursive deletions in the teaching catalogue are not required fixes for ordinary robot package errors.

[M3P-258 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/3.Ubuntu%20common%20commands/3.Ubuntu%20common%20commands.pdf#page=1).

#### 4.Ubuntu common editors <a href="#m3-m3p-259" id="m3-m3p-259"></a>

Edit a backed-up configuration with the intended text editor, preserve indentation/encoding and inspect the saved diff. In Nano save/exit with its displayed shortcuts; in Vim distinguish editing from command mode. A YAML file can look readable yet parse differently after tabs or changed nesting. Verify the installed node loaded the edited file before repeating an operation.

[M3P-259 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/4.Ubuntu%20common%20editors/4.Ubuntu%20common%20editors.pdf#page=1).

#### 5.Ubuntu software operation commands <a href="#m3-m3p-260" id="m3-m3p-260"></a>

Distinguish apt index refresh, install, reinstall, remove and dependency-repair operations. Record the package/version and observed error before changing it. The lesson's general upgrade/dist-upgrade commands are not a model-specific recommendation to replace the Jetson software stack. A repaired package database does not verify GPU, camera or ROS runtime compatibility; repeat only the minimal affected software check afterward.

[M3P-260 · official PDF, pp. 1–1](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/5.Ubuntu%20software%20operation%20commands/5.Ubuntu%20software%20operation%20commands.pdf#page=1).

#### 6.Virtual machine installation <a href="#m3-m3p-261" id="m3-m3p-261"></a>

The supplied virtual-machine exercise prepares a separate desktop learning environment, with an Ubuntu 20.04 image mentioned in the PDF. It is not the NX operating system. Verify VM network attachment, keyboard/GUI and ROS distribution before remote robot exercises. File/USB sharing with the VM can affect which host sees a receiver/programmer, so identify device ownership before troubleshooting the robot.

[M3P-261 · official PDF, pp. 1–11](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/6.Virtual%20machine%20installation/6.Virtual%20machine%20installation.pdf#page=1).

#### 7.SSH remote control <a href="#m3-m3p-262" id="m3-m3p-262"></a>

SSH and scp use explicit username, address and source/destination paths. Test a harmless file copy before transferring a model or map; use `-r` only for an intended directory. The PDF's IPs and `/home/yahboom` paths are examples. SSH success does not imply DDS multicast/discovery success, and a CLI login does not start a graphical desktop.

[M3P-262 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/7.SSH%20remote%20control/7.SSH%20remote%20control.pdf#page=1).

#### 8.VNC remote control <a href="#m3-m3p-263" id="m3-m3p-263"></a>

VNC provides the desktop required by image/parameter GUIs. The generic lesson includes `xrandr` and Raspberry Pi `/boot/firmware/config.txt` examples; the latter is outside the NX host lane. Apply the Orin-specific screen-sharing lesson instead. If an image window is absent, first check the session/display connection rather than applying a Pi boot configuration to the Jetson.

[M3P-263 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/8.VNC%20remote%20control/8.VNC%20remote%20control.pdf#page=1).

#### 9.Transfer files remotely <a href="#m3-m3p-264" id="m3-m3p-264"></a>

Remote file-transfer tools present local and robot directories separately. Confirm which side is selected, the destination path and overwrite decision. Back up the previous file and verify a small transferred file's size/content first. Transferring source code does not compile/install it, and copying calibration into an unused folder does not change the active robot.

[M3P-264 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/9.Transfer%20files%20remotely/9.Transfer%20files%20remotely.pdf#page=1).

#### 10.Driver library and communication <a href="#m3-m3p-252" id="m3-m3p-252"></a>

This generic driver-library lesson installs pyserial and an older **MutoLib** sample. Treat it as an example of Python driver packaging/serial ownership, not the M3 Pro's factory ROS SDK. Verify the actual installed library, device and interpreter before importing it. A second Python serial library opening `/dev/myserial` will conflict with the agent even if both installations are otherwise correct.

[M3P-252 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/10.Driver%20library%20and%20communication/10.Driver%20library%20and%20communication.pdf#page=1).

#### 11.Static IP and hotspot mode <a href="#m3-m3p-253" id="m3-m3p-253"></a>

Choose DHCP/static IP/hotspot mode according to the real network, avoiding an address collision. Keep robot and workstation reachable and match ROS domain after updating shell configuration. A static IP does not provide internet by itself. Record both Ethernet and Wi-Fi addresses, remembering the OLED's priority, before changing application base URLs that refer to the robot.

[M3P-253 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/11.Static%20IP%20and%20hotspot%20mode/11.Static%20IP%20and%20hotspot%20mode.pdf#page=1).

#### 12.Bind device ID <a href="#m3-m3p-254" id="m3-m3p-254"></a>

Device binding uses observed USB identifiers and udev rules to give stable names. Inspect `lsusb` and the actual device attributes before writing a rule; a rule copied for rplidar is not evidence for the factory M3 Pro controller. Reload/trigger udev deliberately, reconnect and verify the symlink points at the intended device. Match serial number when identical adapters need distinction; broad vendor/product matching can bind the wrong port.

[M3P-254 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/12.Bind%20device%20ID/12.Bind%20device%20ID.pdf#page=1).

#### 13.Capacity expansion and resource allocation <a href="#m3-m3p-255" id="m3-m3p-255"></a>

Inspect filesystem capacity with `df -h` and partitions with the appropriate disk tool before expanding storage. Use the Orin SSD-specific workflow for this host. Do not confuse free space in a container with free space on the backing SSD or a mounted map directory. A larger filesystem fixes capacity only; it does not fix memory exhaustion or camera USB errors.

[M3P-255 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/13.Capacity%20expansion%20and%20resource%20allocation/13.Capacity%20expansion%20and%20resource%20allocation.pdf#page=1).

#### 16.sudo free password <a href="#m3-m3p-256" id="m3-m3p-256"></a>

The passwordless-sudo lesson uses `visudo` to edit sudoers with syntax validation. It is general administration, not a dependency for ROS topics or normal robot control. Before adapting it, identify the exact command/user requirement rather than granting broad unconditional access. A corrected sudo rule changes privileges, not device-driver behavior or a missing package.

[M3P-256 · official PDF, pp. 1–1](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/22.Linux%20System%20Course/16.sudo%20free%20password/16.sudo%20free%20password.pdf#page=1).

### 23. ROS 2 foundations for engineers and development agents <a href="#m3-course-23" id="m3-course-23"></a>

These examples build small independent packages before touching the robot. Use the **Ubuntu 22.04 / Humble** environment for this NX. Create teaching workspaces separately from the factory `M3Pro_ws`/`yahboomcar_ws`, source the intended overlay in every terminal and inspect which package prefix resolves. A source build, ROS execution and physical robot validation are three separate checkpoints.

Sources: [M3P-276](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/2.ROS2%20install%20Humble/2.ROS2%20install%20Humble.pdf), [M3P-283](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/4.ROS2%20workspace/4.ROS2%20workspace.pdf).

#### 1.Introduction to ROS2 <a href="#m3-m3p-265" id="m3-m3p-265"></a>

ROS 2 separates nodes, typed communication and middleware; it is not an operating system or a motor driver. Topics stream data, services return a request/response, actions add feedback/cancellation for longer work. Choose the interface by the operation: raw scans suit topics, a pose query suits a service and a navigation task suits an action. A discovered endpoint establishes only graph membership, not valid sensor content or successful actuation.

[M3P-265 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/1.Introduction%20to%20ROS2/1.Introduction%20to%20ROS2.pdf#page=1).

#### 2.ROS2 install Humble <a href="#m3-m3p-276" id="m3-m3p-276"></a>

The installation lesson supports **Ubuntu 22.04 / ROS 2 Humble**, establishes locale/repository prerequisites, installs desktop/colcon and sources `/opt/ros/humble/setup.bash`. On the preinstalled NX begin by checking the environment instead of reinstalling. Use `demo_nodes_cpp talker` and `listener`, then turtlesim, as independent software checks. The PDF has a capitalized `apt Update` typo and historical key/repository instructions; verify package-source setup before a new installation rather than reproducing it blindly.

[M3P-276 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/2.ROS2%20install%20Humble/2.ROS2%20install%20Humble.pdf#page=1).

#### 3.ROS2 development environment <a href="#m3-m3p-282" id="m3-m3p-282"></a>

The development tools lesson introduces multiple terminals, editor and Git. Use Git status/diff to inspect a calibration/configuration edit and commit a known working state before broader changes. Record the repository commit and actual runtime package separately. A checked-out PDF repository does not install ROS executables; this distinction matters when a course refers to source files delivered only inside the factory image.

[M3P-282 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/3.ROS2%20development%20environment/3.ROS2%20development%20environment.pdf#page=1).

#### 4.ROS2 workspace <a href="#m3-m3p-283" id="m3-m3p-283"></a>

Create a workspace with a `src` directory, build with colcon and source `install/setup.bash`. The generated `build`, `install` and `log` directories serve different purposes; edit source, not a copied installed file unless intentionally testing that copy. A new terminal needs the same overlay. `ros2 pkg prefix` confirms which installation takes precedence when both a factory workspace and a learning workspace contain similar package names.

[M3P-283 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/4.ROS2%20workspace/4.ROS2%20workspace.pdf#page=1).

#### 5.ROS2 function package <a href="#m3-m3p-284" id="m3-m3p-284"></a>

Use `ros2 pkg create` with **ament\_cmake** for the C++ example or **ament\_python** with rclpy for Python. Declare dependencies, install executable entry points/resources and build only the intended package when appropriate. A Python file in `src` is not automatically a `ros2 run` executable. For “No executable found,” inspect entry-point/install configuration and source the new overlay before editing the node logic.

[M3P-284 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/5.ROS2%20function%20package/5.ROS2%20function%20package.pdf#page=1).

#### 6.ROS2 node <a href="#m3-m3p-285" id="m3-m3p-285"></a>

The hello-world Python node initializes rclpy, creates a Node, spins while active and destroys/shuts down cleanly. Build `pkg_helloworld_py`, source its overlay and run the installed `helloworld` entry point. The PDF's `ment_python` spelling is a typo; the preceding package lesson specifies `ament_python`. Confirm a repeated node log before adding publishers or robot connections; this isolates packaging and executor setup from hardware.

[M3P-285 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/6.ROS2%20node/6.ROS2%20node.pdf#page=1).

#### 7.ROS2 topic communication <a href="#m3-m3p-286" id="m3-m3p-286"></a>

`pkg_topic publisher_demo` publishes `std_msgs/msg/String` on `/topic_demo`; `subscriber_demo` consumes it through `create_subscription`. A timer drives repeated publication. Inspect topic type/rate/content, then verify the callback receives matching data. Type, name and QoS must all agree; two similarly named topics do not connect automatically. Keep subscriptions/publishers alive and let the executor spin, otherwise discovery may occur without useful callbacks.

[M3P-286 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/7.ROS2%20topic%20communication/7.ROS2%20topic%20communication.pdf#page=1).

#### 8.ROS2 service communication <a href="#m3-m3p-287" id="m3-m3p-287"></a>

The service example creates `/add_two_ints` using `example_interfaces/srv/AddTwoInts`. With `pkg_service server_demo` running, call it with **a: 1, b: 4** and expect sum 5; the client waits for availability and handles the response future. This is a useful non-robot request/response checkpoint. A service listed in the graph but timing out may have an unspun server or blocked callback, not merely a network fault.

[M3P-287 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/8.ROS2%20service%20communication/8.ROS2%20service%20communication.pdf#page=1).

#### 9.ROS2 action communication <a href="#m3-m3p-288" id="m3-m3p-288"></a>

Define `pkg_interfaces/action/Progress`, build/source it, then run `pkg_action action_server_demo` and send `/get_sum` a goal **num: 10**. Inspect feedback while calculation progresses and distinguish accepted, completed, canceled and failed results. The client/server action APIs are `rclpy.action.ActionClient/ActionServer`. Model a long robot operation with explicit feedback/cancel behavior rather than reporting success immediately when its initial request is accepted.

[M3P-288 · official PDF, pp. 1–9](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/9.ROS2%20action%20communication/9.ROS2%20action%20communication.pdf#page=1).

#### 10.ROS2 custom interface message <a href="#m3-m3p-266" id="m3-m3p-266"></a>

Custom messages/services live in the interface package and require rosidl generation, package dependencies and rebuilding before Python/C++ clients can import them. The course exposes `pkg_interfaces/msg/Person` and `srv/Add`; inspect each with `ros2 interface show`. Source the rebuilt overlay in both terminals. A stale installed interface can make a valid-looking publisher incompatible with another host using a newer field layout.

[M3P-266 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/10.ROS2%20custom%20interface%20message/10.ROS2%20custom%20interface%20message.pdf#page=1).

#### 11.ROS2 parameter service case <a href="#m3-m3p-267" id="m3-m3p-267"></a>

Use `ros2 param list/describe/get/set`, then dump/load parameters for the intended node. The turtlesim example changes `background_b` to **10**; the custom node declares `robot_name`. Parameters are typed and belong to a specific node name, which may differ from its executable. Save YAML once intentionally rather than repeatedly appending dumps into a malformed file. Verify read-back and the node's behavior; not every parameter is dynamically applied merely because it was accepted.

[M3P-267 · official PDF, pp. 1–5](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/11.ROS2%20parameter%20service%20case/11.ROS2%20parameter%20service%20case.pdf#page=1).

#### 12.ROS2 meta-function package <a href="#m3-m3p-268" id="m3-m3p-268"></a>

A metapackage groups related packages/dependencies without containing the entire implementation. Create/build the supplied `pkg_metapackage` and inspect its manifest's dependencies. Installing it is useful for assembling a software set, but it does not prove each component's runtime configuration or hardware compatibility. Avoid adding source code to a metapackage just to hide missing dependencies in a robot build.

[M3P-268 · official PDF, pp. 1–2](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/12.ROS2%20meta-function%20package/12.ROS2%20meta-function%20package.pdf#page=1).

#### 13.ROS2 distributed communication <a href="#m3-m3p-269" id="m3-m3p-269"></a>

Test distributed discovery with `demo_nodes_py talker` on one host and `listener` on another. Keep hosts reachable, use the same intended `ROS_DOMAIN_ID` and refresh changed shell variables before launching nodes. Verify local talker/listener first; remote-only failure points to network/DDS configuration. Namespaces distinguish cooperating robots, whereas unrelated domains isolate discovery. SSH connectivity alone does not prove ROS discovery or topic delivery.

[M3P-269 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/13.ROS2%20distributed%20communication/13.ROS2%20distributed%20communication.pdf#page=1).

#### 14.ROS2 DDS <a href="#m3-m3p-270" id="m3-m3p-270"></a>

DDS QoS governs reliability/history and endpoint matching. The source demonstrates reliable versus best-effort publisher/subscriber combinations; a reliable-only subscriber may not match a best-effort sensor publisher. Inspect endpoint QoS before concluding a silent sensor failed. Choose history depth and reliability for the data/task rather than globally forcing reliability. The route container's middleware switch and QoS policies are separate configuration dimensions.

[M3P-270 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/14.ROS2%20DDS/14.ROS2%20DDS.pdf#page=1).

#### 15.ROS2 time related API <a href="#m3-m3p-271" id="m3-m3p-271"></a>

Use the node's clock, durations, timers and rate APIs deliberately. The course's `learning_time` programs illustrate rate, timer, current clock and duration separately. A loop sleeping for wall time is different from a ROS timer using simulation time. With `use_sim_time` enabled, `/clock` must exist and advance; mixed clocks explain stale transforms even when sensor bytes are arriving.

[M3P-271 · official PDF, pp. 1–10](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/15.ROS2%20time%20related%20API/15.ROS2%20time%20related%20API.pdf#page=1).

#### 16.ROS2 common command tools <a href="#m3-m3p-272" id="m3-m3p-272"></a>

Use `ros2 pkg executables`, `node info`, `topic type/info/hz`, `interface show`, `service list/call` and `action list/send_goal` to inspect the actual system before constructing a command. The PDF's `ros2 interface call` is not the service-call pattern demonstrated elsewhere; use `ros2 service call` with the observed type. Preserve exact message fields, including case, and substitute valid YAML for placeholders.

[M3P-272 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/16.ROS2%20common%20command%20tools/16.ROS2%20common%20command%20tools.pdf#page=1).

#### 17.ROS2 rviz2 use <a href="#m3-m3p-273" id="m3-m3p-273"></a>

RViz displays ROS data in a chosen fixed frame; a wrong/missing frame can hide a valid scan or cloud. Add the intended topic/display and inspect status before reinstalling its producer. The lesson also installs a TurtleBot3/Gazebo example: it teaches visualization and is not the M3 Pro's URDF/controller configuration. An RViz model moving from joint states does not itself establish a physical robot is connected.

[M3P-273 · official PDF, pp. 1–7](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/17.ROS2%20rviz2%20use/17.ROS2%20rviz2%20use.pdf#page=1).

#### 18.ROS2 rqt toolbox <a href="#m3-m3p-274" id="m3-m3p-274"></a>

rqt provides graph, topic, image and parameter views. Use the graph to identify actual publishers/subscribers, refresh it after bringup and inspect the relevant topic before motion. rqt\_reconfigure requires the selected node's dynamic parameter support; an empty pane can be a missing/undiscovered node rather than a wrong calibration value. Keep visualization tools separate from command ownership so closing one does not falsely imply the robot controller stopped.

[M3P-274 · official PDF, pp. 1–4](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/18.ROS2%20rqt%20toolbox/18.ROS2%20rqt%20toolbox.pdf#page=1).

#### 19.ROS2 Launch startup file configuration <a href="#m3-m3p-275" id="m3-m3p-275"></a>

The `learn_launch` examples progress through single/multiple nodes, names/remaps, included launch files, namespaces and Python/XML/YAML formats. Install launch resources through the package's build/setup rules so `ros2 launch` can find them. Test argument values and node names in a learning workspace before applying the pattern to robot bringup. A namespace on a launch group does not rewrite every hardcoded absolute topic/frame automatically.

[M3P-275 · official PDF, pp. 1–17](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/19.ROS2%20Launch%20startup%20file%20configuration/19.ROS2%20Launch%20startup%20file%20configuration.pdf#page=1).

#### 20.ROS2 recording and playback tool <a href="#m3-m3p-277" id="m3-m3p-277"></a>

`ros2 bag record -o NAME TOPIC...` records selected data; `bag info` checks topic/types/counts; `bag play` replays it with optional rate, loop or topic selection. Use an explicit sensor/topic list instead of `-a` when physical command topics could be captured. Replaying `/cmd_vel` or arm commands on a connected robot can actuate it; isolate the domain or omit them for offline analysis. Bag playback reproduces messages, not the physical truth of the original measurement.

[M3P-277 · official PDF, pp. 1–3](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/20.ROS2%20recording%20and%20playback%20tool/20.ROS2%20recording%20and%20playback%20tool.pdf#page=1).

#### 21.ROS2 URDF model <a href="#m3-m3p-278" id="m3-m3p-278"></a>

URDF describes rigid links and joints. Keep `visual`, `collision` and `inertial` roles distinct; a detailed mesh may be replaced by simpler collision geometry without changing its visible appearance. Joint `parent`, `child`, `origin`, `axis` and `limit` define the kinematic relation, with fixed/revolute/continuous/prismatic types having different constraints. The generic example builds `yahboomcar_description` and launches `display.launch.py`; it is not proof of the exact M3 Pro model. Inspect the real package's joints and frames before using it with MoveIt or camera-to-base geometry.

[M3P-278 · official PDF, pp. 1–8](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/21.ROS2%20URDF%20model/21.ROS2%20URDF%20model.pdf#page=1).

#### 22.ROS2 Gazebo simulation platform <a href="#m3-m3p-279" id="m3-m3p-279"></a>

The Gazebo course creates a simple `myrobot` URDF and `bringup_model.launch.py`, installs/loads the simulation model and inspects exposed ROS nodes/services. Match the simulator/plugin generation to the installed Humble environment; classic Gazebo and newer ros-gz examples are not interchangeable merely because both render a robot. This teaching model is not the exact M3 Pro arm/chassis. Use its simulated topics as a software exercise before any real hardware bridge.

[M3P-279 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/22.ROS2%20Gazebo%20simulation%20platform/22.ROS2%20Gazebo%20simulation%20platform.pdf#page=1).

#### 23.ROS2 TF2 coordinate transformation <a href="#m3-m3p-280" id="m3-m3p-280"></a>

Use `tf2_echo map base_footprint` to inspect the base pose in the map, and choose frame order deliberately for another computation and rqt\_tf\_tree to inspect parent/child connectivity. The course shows static and dynamic broadcasters plus a buffered listener. Define each frame's parent once, include timestamp and normalized quaternion, and handle lookup/connectivity/extrapolation errors. For grasping, transform depth geometry from camera to base using the current arm pose; a stale transform can be numerically valid yet physically wrong. Check time, direction and units before adding an empirical offset.

[M3P-280 · official PDF, pp. 1–14](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/23.ROS2%20TF2%20coordinate%20transformation/23.ROS2%20TF2%20coordinate%20transformation.pdf#page=1).

#### 23.ROS2 TF2 coordinate transformation <a href="#m3-m3p-281" id="m3-m3p-281"></a>

The included transform-library paper explains a time-buffered coordinate tree and interpolation for robotics systems. Apply the concept by keeping sensor measurements timestamped and requesting a transform for the relevant time, rather than treating all frames as static. A connected TF tree is necessary but does not verify measured extrinsics, axis orientation or latency. This background reading supports TF reasoning; it is not a current API reference or a license to copy the paper's figures/code wholesale.

[M3P-281 · official PDF, pp. 1–6](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/23.ROS%20Basic%20Course/23.ROS2%20TF2%20coordinate%20transformation/tfThe%20transform%20library.pdf#page=1).

### Original integration examples and a failure-driven workflow

#### Non-motion FK/IK round trip

**Host:** installed Orin / Humble environment with `arm_kin` and `arm_interface` available. This example calls the solver and prints a mathematical pose; it does not publish joint targets. Keep physical publishers/bridges stopped if the aim is a numerical check.

```bash
# Terminal 1: solver only
ros2 run arm_kin kin_srv
# Terminal 2: inspect the installed contract
ros2 interface show arm_interface/srv/ArmKinemarics
# Numerical FK query, deliberately separate from any arm6_joints publisher
ros2 service call /get_kinemarics arm_interface/srv/ArmKinemarics "{cur_joint1: 90.0, cur_joint2: 90.0, cur_joint3: 90.0, cur_joint4: 90.0, cur_joint5: 90.0, cur_joint6: 90.0, kin_name: 'fk'}"
```

Expected vendor-model result is approximately x = 0.0314 m, y = 0.000209 m and z = 0.55175 m. Use the **full returned pose**, including radian-valued orientation, for an IK request; compare only the five solved arm joints and handle the gripper independently. Record the exact package/model revision with the result. This round trip has not been executed here. Sources: [M3P-041](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/04.Robotic%20Arm%20and%203D%20Space%20Gripping%20Course/1.Robotic%20arm%20solution/1.Robotic%20arm%20solution.pdf).

#### Original calibration arithmetic, independent of hardware access

The following Python illustrates the controller course's conversions without opening devices or importing ROS. Inputs are illustrative, not measurements from an M3 Pro.

```python
# Original offline calculation example; no robot connection or motion.
def battery_volts(adc_count):
    if not isinstance(adc_count, int) or not 0 <= adc_count <= 4095:
        raise ValueError('expected a 12-bit ADC count')
    return adc_count * (3.30 / 4096) * 4.03

servo_pwm_hz = 240_000_000 / (239 + 1) / (19999 + 1)
motor_pwm_hz = 240_000_000 / (4 + 1) / (1999 + 1)
print(round(battery_volts(3600), 3), 'V, illustrative count only')
print(servo_pwm_hz, motor_pwm_hz, 'Hz')
```

Expected arithmetic: **11.689 V**, **50 Hz**, **24,000 Hz**. The ADC divider/reference are manufacturer example constants, not an independently calibrated voltmeter. Timer calculations use the clock stated in the source; changing the clock tree changes the output. Sources: [M3P-176](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/5.Battery%20voltage%20detection/5.Battery%20voltage%20detection.pdf), [M3P-177](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/6.Driving%20PWM%20Servo/6.Driving%20PWM%20Servo.pdf), [M3P-178](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/18.Control%20Board%20Course/2.Control%20board%20STM32%20basic%20routine/7.Drive%20motor/7.Drive%20motor.pdf). This small offline example is the only executable calculation checked here; it is not firmware compilation or hardware validation.

#### A development log that preserves the right distinctions

For one new grasp task, record: exact SKU/host image; active ROS workspace/package prefix; controller version; camera intrinsic/registration source; marker physical size/family; servo median record; grasp YAML and its hash; model/provider region; fresh target verification image; requested and returned pose; action status; and measured outcome. A practical first task is a single correctly sized stationary block, a short verified approach and one pick. Repeat at multiple table positions only after the first result matches geometry.

A useful fault order is:

1. **No controller node:** check battery/USB Connect, stable serial name, one agent and domain. Restore factory firmware if a teaching image was left installed.
2. **No valid depth:** check camera process ownership, USB connection, encoding, optical working distance and surface/lighting before altering grasp offsets.
3. **Correct detector, wrong metric target:** check image resize/registration, intrinsics, physical tag size, current FK and transform time/direction.
4. **Correct target, wrong arm pose:** separate servo median, degree/radian conversion, gripper width, kinematic model and camera/grasp offset.
5. **Correct local motion, poor map:** independently measure linear/yaw odometry, inspect TF and clock, then remap slowly with loop closure.
6. **Correct map, failed navigation:** check localization owner, active map/pose-graph/database, footprint/costmap and route connectivity; inspect the action's failure status.
7. **Correct CLI tool, failed AI task:** check selected agent, plugin/tool exposure, model/region and returned structured values. A fluent response is not a completed action.

### Original images, downloads and remaining boundaries

![Yahboom's ROSMASTER M3 Pro demonstration with arm, display, Mecanum chassis and colored blocks; promotional family illustration, not proof of the exact installed host revision](https://raw.githubusercontent.com/YahboomTechnology/ROSMASTER-M3PRO/015d065d61069584532778a7ffa9362deb8e9429/ROSMASTER_M3PRO.jpg)

The original repository illustration above is preserved by its pinned observed path. Important embedded figures remain in the original PDFs: controller connector photograph (section 18 introduction p.1), servo-median posture (section 00 calibration p.2), T-mini performance table (section 02 introduction p.1), sandbox floor/prop drawing (section 10 introduction pp.1–4) and UART programmer settings (section 18 serial flashing p.2). They were inspected as source images. These are not replacement electrical schematics, measured drawings or newly licensed image assets.

| Resource                                                                                                                                                                                                                                                      | Purpose and access boundary                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| [Official M3 Pro study portal](https://www.yahboom.net/study/ROSMASTER-M3PRO)                                                                                                                                                                                 | Manufacturer navigation; all course citations here are pinned to the locally reviewed repository revision                    |
| [Pinned official course repository](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/tree/015d065d61069584532778a7ffa9362deb8e9429)                                                                                                                       | Original PDFs, example RAG spreadsheets, Dify DSL files and family photograph                                                |
| [Repository annex download folder](https://drive.google.com/drive/folders/13q6tB7duof3cQem1WR-J-hb1EEhl9ZX0)                                                                                                                                                  | Observed `Annex_Download_Link.txt` destination; individual archives, versions, licenses and availability not checked here    |
| [Host images](https://drive.google.com/drive/folders/1KO6mW_tliBEXw0oVb6PpXLsZ8g6EHurF)                                                                                                                                                                       | Official portal resource retained from the existing guide; exact NX SUPER/JetPack archive must be identified before recovery |
| [Code / factory firmware](https://drive.google.com/drive/folders/1Tg8UuTXjvQzF8f8O72lfyZo8z5MkiNBw)                                                                                                                                                           | Working-image source/firmware resources; archive content not installed or fully read during source review                    |
| [Tools](https://drive.google.com/drive/folders/1fnwhQVmW4oB7oLPazh77vJIARSOILThW), [drivers](https://drive.google.com/drive/folders/15FtprICahL6W6JhXMORLcbvPCNeHtNLy), [3D models](https://drive.google.com/drive/folders/1h3XF3F35dB8ZMyHR0PDMXYXPyI2LbfiS) | Retained manufacturer destinations; downloaded assets/licensing/mechanical fit not validated                                 |

**Scope limits:** all 288 PDFs are inventoried; 260 receive substantive lesson synthesis, including explicitly marked compatibility-only, theory and optional multi-robot/sandbox exercises. The 28 original-Nano/Pi host PDFs are excluded from NX maintenance; their host boundaries are summarized in the alternative-host table below. Shared fundamentals with a non-NX example are interpreted as concepts and explicitly bounded, rather than presented as NX installation commands. Numbering gaps in the source are retained rather than filled with invented courses.

This is a course-level engineering synthesis, not a complete reproduction of vendor code, slide screenshots or manuals. All applicable extracted page text was processed; review concentrated on substantive narrative, operation, configuration, API and failure passages. Detailed code listings were analyzed for interfaces/parameters, not reproduced or exhaustively compiled. Only selected image-dependent facts were visually checked; remaining screenshot-specific details stay in the linked originals and must not be called visually verified. Cloud/provider state, runtime package versions, exact firmware archive selection, fitted MCU flash capacity and the conflicting MCP gripper polarity remain unresolved until checked on the actual system. No claim of software/hardware readiness or measured precision follows from document coverage.

#### Alternative-host sources excluded from NX maintenance <a href="#m3-excluded-hosts" id="m3-excluded-hosts"></a>

These exact documents remain accessible but are not offered as NX commissioning procedures. Each is listed with its appropriate host scope.

* [21.Main Control Course/Jetson Nano B01/1. Introduction to the Jetson Nano B01 SUB Board/1. Introduction to the Jetson Nano B01 SUB Board.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/1.%20Introduction%20to%20the%20Jetson%20Nano%20B01%20SUB%20Board/1.%20Introduction%20to%20the%20Jetson%20Nano%20B01%20SUB%20Board.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/2. Burn the system image/2. Burn the system image.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/2.%20Burn%20the%20system%20image/2.%20Burn%20the%20system%20image.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/3. Re-read the memory card or USB drive that has been burned/3. Re-read the memory card or USB drive that has been burned.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/3.%20Re-read%20the%20memory%20card%20or%20USB%20drive%20that%20has%20been%20burned/3.%20Re-read%20the%20memory%20card%20or%20USB%20drive%20that%20has%20been%20burned.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/4. Startup system/4. Startup system.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/4.%20Startup%20system/4.%20Startup%20system.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/5. Jetson Nano B01 System and Desktop Introduction/5. Jetson Nano B01 System and Desktop Introduction.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/5.%20Jetson%20Nano%20B01%20System%20and%20Desktop%20Introduction/5.%20Jetson%20Nano%20B01%20System%20and%20Desktop%20Introduction.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/6. Memory card or USB flash drive expansion/6. Memory card or USB flash drive expansion.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/6.%20Memory%20card%20or%20USB%20flash%20drive%20expansion/6.%20Memory%20card%20or%20USB%20flash%20drive%20expansion.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/7. Network Configuration/7. Network Configuration.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/7.%20Network%20Configuration/7.%20Network%20Configuration.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/8. SSH remote login & file transfer/8. SSH remote login & file transfer.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/8.%20SSH%20remote%20login%20%26%20file%20transfer/8.%20SSH%20remote%20login%20%26%20file%20transfer.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/9. VNC Remote Login/9. VNC Remote Login.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/9.%20VNC%20Remote%20Login/9.%20VNC%20Remote%20Login.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/10. Jetson Nano B01 system backup/10. Jetson Nano B01 system backup.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/10.%20Jetson%20Nano%20B01%20system%20backup/10.%20Jetson%20Nano%20B01%20system%20backup.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/11. Jetson Nano Swap space increased/11. Jetson Nano Swap space increased.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/11.%20Jetson%20Nano%20Swap%20space%20increased/11.%20Jetson%20Nano%20Swap%20space%20increased.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Jetson Nano B01/12. Installation and use of Jtop/12. Installation and use of Jtop.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Jetson%20Nano%20B01/12.%20Installation%20and%20use%20of%20Jtop/12.%20Installation%20and%20use%20of%20Jtop.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/1. Introduction to Raspberry PI 5/1. Introduction to Raspberry PI 5.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/1.%20Introduction%20to%20Raspberry%20PI%205/1.%20Introduction%20to%20Raspberry%20PI%205.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/2. Raspberry PI system installation and backup/2. Raspberry PI system installation and backup.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/2.%20Raspberry%20PI%20system%20installation%20and%20backup/2.%20Raspberry%20PI%20system%20installation%20and%20backup.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/3. Powering the Raspberry PI 5/3. Powering the Raspberry PI 5.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/3.%20Powering%20the%20Raspberry%20PI%205/3.%20Powering%20the%20Raspberry%20PI%205.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/4. Startup of Raspberry PI 5/4.Startup of Raspberry PI 5.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/4.%20Startup%20of%20Raspberry%20PI%205/4.Startup%20of%20Raspberry%20PI%205.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/5. Update and upgrade operating system/Update and upgrade operating system.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/5.%20Update%20and%20upgrade%20operating%20system/Update%20and%20upgrade%20operating%20system.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/6. Introduction to raspi-config tool/Introduction to raspi-config tool.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/6.%20Introduction%20to%20raspi-config%20tool/Introduction%20to%20raspi-config%20tool.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/7. config.txt file description/config.txt file description.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/7.%20config.txt%20file%20description/config.txt%20file%20description.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/8. Network Configuration/Network Configuration.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/8.%20Network%20Configuration/Network%20Configuration.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/9. remote access/remote access.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/9.%20remote%20access/remote%20access.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/10. Transfer files remotely/Transfer files remotely.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/10.%20Transfer%20files%20remotely/Transfer%20files%20remotely.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/11. Set display resolution and rotation/Set display resolution and rotation.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/11.%20Set%20display%20resolution%20and%20rotation/Set%20display%20resolution%20and%20rotation.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/12. Set screen to sleep/Set screen to sleep.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/12.%20Set%20screen%20to%20sleep/Set%20screen%20to%20sleep.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/13. Play audio and video/Play audio and video.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/13.%20Play%20audio%20and%20video/Play%20audio%20and%20video.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/14. Using USB camera/Using USB camera.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/14.%20Using%20USB%20camera/Using%20USB%20camera.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/15. Using MIPI camera/Using MIPI camera.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/15.%20Using%20MIPI%20camera/Using%20MIPI%20camera.pdf) — original Nano/Pi host lane, excluded from NX.
* [21.Main Control Course/Raspberry Pi/16. Get real-time temperature of Raspberry Pi/Get real-time temperature of Raspberry Pi.pdf](https://github.com/YahboomTechnology/ROSMASTER-M3PRO/blob/015d065d61069584532778a7ffa9362deb8e9429/21.Main%20Control%20Course/Raspberry%20Pi/16.%20Get%20real-time%20temperature%20of%20Raspberry%20Pi/Get%20real-time%20temperature%20of%20Raspberry%20Pi.pdf) — original Nano/Pi host lane, excluded from NX.

## References and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

This guide was checked against the exact OpenELAB catalog option, the live Yahboom study portal and the locally retrieved manufacturer PDF repository. The board's connector photograph and MCU routing diagram were visually inspected. Original procedures separate observation from actuation and resolve the documented scanner-table inconsistency.

The Python subscriber was syntax-parsed. No ROS package build, image flash, physical connection, sensor measurement, calibration or robot motion was performed. Peak compute, runtime, payload and precision figures are manufacturer/store claims, not independent test results. Retain the robot's actual image, firmware and package revisions with any project log. Related [Yahboom robot guides](https://wiki.openelab.io/robotics/yahboom) provide discovery; use this page's exact M3 Pro option for configuration decisions.
