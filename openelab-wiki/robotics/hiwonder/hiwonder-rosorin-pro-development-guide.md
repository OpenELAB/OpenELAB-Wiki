---
description: >-
  Resolve the NX SUPER 16 GB Pro and Nano SUPER 8 GB Standard kits, commission
  chassis/sensors and develop navigation with model-specific arm differences.
---

# Hiwonder ROSOrin Pro and ROSOrin: exact NX/Nano ROS 2 development paths

{% hint style="info" %}
[**ROSOrin Pro Ultimate / Orin NX SUPER 16 GB — SKU Hiwonder-21031913**](https://openelab.io/products/hiwonder-rosorin-pro-smart-car?variant=45954062024902) · [**ROSOrin Standard / Orin Nano SUPER 8 GB — SKU Hiwonder-21031729**](https://openelab.io/products/hiwonder-rosorin-smart-car?variant=46066583011526)
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

![ROSOrin and ROSOrin Pro — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-7.webp)

_Existing OpenELAB product illustration retained for model context; option contents and electrical connections are identified by the tables and diagrams below._

This canonical guide covers two explicitly different ROSOrin configurations: a **Pro mobile manipulator with NX SUPER 16 GB** and a **Standard mobile chassis with Nano SUPER 8 GB**. Both use Mecanum mobility, LiDAR and depth vision, but only the assigned Pro has the six-servo arm and Ultimate display. Use the variant table below before choosing a system image, hardware diagram or arm example. [Pro option](https://openelab.io/products/hiwonder-rosorin-pro-smart-car?variant=45954062024902), [Standard option](https://openelab.io/products/hiwonder-rosorin-smart-car?variant=46066583011526).

The Orin software path uses the manufacturer's Ubuntu 22.04/ROS 2 Humble environment. Older Jetson Nano/Melodic and Pi 5 Docker lessons are separate lanes. This guide first establishes power, image identity and passive sensor feedback, then develops chassis calibration, SLAM and model-specific manipulation. [Pro manual](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html), [Standard Orin manual](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/1_ROSOrin_User_Manual.html).

### Other established purchasing options <a href="#models-and-purchasing-options" id="models-and-purchasing-options"></a>

This canonical page also retains the following catalogued family options. The detailed first-run workflow above/below is for the exact host/kit variants in the opening callout; select the matching host image and kit-specific hardware for other options. A controller-excluded option needs that separately supplied host. A ROSOrin base is distinct from ROSOrin Pro with an arm.

| SKU                 | Established option                                                                                                                         |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `Hiwonder-21031863` | Standard Kit / Without ROS Controller — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                    |
| `Hiwonder-21031864` | Standard Kit / With Raspberry Pi 5(8 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                 |
| `Hiwonder-21031872` | Standard Kit / With Raspberry Pi 5(16 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                |
| `Hiwonder-21031865` | Standard Kit / With Jetson Nano(4 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                    |
| `Hiwonder-21031866` | Standard Kit / With Jetson Orin Nano Super(8 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                         |
| `Hiwonder-21031867` | Standard Kit / With Jetson Orin NX Super(8 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                           |
| `Hiwonder-21031868` | Standard Kit / With Jetson Orin NX Super(16 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                          |
| `Hiwonder-21031873` | Advanced Kit / Without ROS Controller — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                    |
| `Hiwonder-21031874` | Advanced Kit / With Raspberry Pi 5(8 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                 |
| `Hiwonder-21031875` | Advanced Kit / With Raspberry Pi 5(16 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                |
| `Hiwonder-21031876` | Advanced Kit / With Jetson Nano(4 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                    |
| `Hiwonder-21031877` | Advanced Kit / With Jetson Orin Nano Super(8 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                         |
| `Hiwonder-21031878` | Advanced Kit / With Jetson Orin NX Super(8 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                           |
| `Hiwonder-21031911` | Advanced Kit / With Jetson Orin NX Super(16 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                          |
| `Hiwonder-21031885` | Ultimate Kit / Without ROS Controller — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                    |
| `Hiwonder-21031886` | Ultimate Kit / With Raspberry Pi 5(8 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                 |
| `Hiwonder-21031887` | Ultimate Kit / With Raspberry Pi 5(16 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                |
| `Hiwonder-21031888` | Ultimate Kit / With Jetson Nano(4 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                                    |
| `Hiwonder-21031889` | Ultimate Kit / With Jetson Orin Nano Super(8 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                         |
| `Hiwonder-21031890` | Ultimate Kit / With Jetson Orin NX Super(8 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                           |
| `Hiwonder-21031913` | Ultimate Kit / With Jetson Orin NX Super(16 GB) — Hiwonder ROSOrin Pro ROS 2 Robot Kit with 6DOF Arm & LiDAR SLAM                          |
| `Hiwonder-21031708` | Starter Kit / Without Controller — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options                 |
| `Hiwonder-21031709` | Starter Kit / With Raspberry Pi 5(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options          |
| `Hiwonder-21031710` | Starter Kit / With Jetson Nano(4 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options             |
| `Hiwonder-21031711` | Starter Kit / With Jetson Orin Nano Super(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options  |
| `Hiwonder-21031712` | Starter Kit / With Jetson Orin NX Super(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options    |
| `Hiwonder-21031726` | Standard Kit / Without Controller — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options                |
| `Hiwonder-21031727` | Standard Kit / With Raspberry Pi 5(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options         |
| `Hiwonder-21031728` | Standard Kit / With Jetson Nano(4 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options            |
| `Hiwonder-21031729` | Standard Kit / With Jetson Orin Nano Super(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options |
| `Hiwonder-21031730` | Standard Kit / With Jetson Orin NX Super(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options   |
| `Hiwonder-21031738` | Advanced Kit / Without Controller — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options                |
| `Hiwonder-21031739` | Advanced Kit / With Raspberry Pi 5(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options         |
| `Hiwonder-21031740` | Advanced Kit / With Jetson Nano(4 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options            |
| `Hiwonder-21031741` | Advanced Kit / With Jetson Orin Nano Super(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options |
| `Hiwonder-21031742` | Advanced Kit / With Jetson Orin NX Super(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options   |
| `Hiwonder-21031754` | Ultimate Kit / Without Controller — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options                |
| `Hiwonder-21031825` | Ultimate Kit / With Raspberry Pi 5(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options         |
| `Hiwonder-21031755` | Ultimate Kit / With Jetson Nano(4 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options            |
| `Hiwonder-21031756` | Ultimate Kit / With Jetson Orin Nano Super(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options |
| `Hiwonder-21031757` | Ultimate Kit / With Jetson Orin NX Super(8 GB) — Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options   |

[OpenELAB family options](https://openelab.io/products/hiwonder-rosorin-pro-smart-car).

## Applications <a href="#applications" id="applications"></a>

Use either kit for Mecanum kinematics, encoder/IMU fusion, 2D/3D mapping, waypoint navigation, visual tracking and voice/model integration. Use the Pro for stationary grasping, mobile transport and MoveIt2 experiments. A Standard-kit navigation result does not establish a Pro's clearance: its upright arm and display change swept volume, mass distribution and camera mounting.

A useful development sequence is stationary sensor logging, a measured straight/lateral/rotation test, a small saved map, a nearby navigation goal and finally a Pro-only light-object task. Keep app/gamepad, navigation and model-driven controllers mutually exclusive during physical tests.

## Specifications <a href="#specifications" id="specifications"></a>

| Feature                     | Pro Ultimate, 21031913                   | ROSOrin Standard, 21031729                                             |
| --------------------------- | ---------------------------------------- | ---------------------------------------------------------------------- |
| Exact controller            | Orin NX SUPER 16 GB                      | Orin Nano SUPER 8 GB                                                   |
| Store variant               | 45954062024902                           | 46066583011526                                                         |
| Base                        | Mecanum chassis with swing suspension    | Mecanum chassis                                                        |
| Arm                         | 6DOF arm/gripper assembly                | No arm in this configuration                                           |
| Vision                      | Aurora930 Pro depth camera               | Aurora930 Pro depth camera                                             |
| Audio                       | WonderEcho Pro                           | WonderEcho Pro                                                         |
| Display                     | 7-inch LCD included                      | Do not assume Pro Ultimate LCD                                         |
| Chassis conversion hardware | Use Pro's supplied mechanics             | Standard does **not** include Advanced/Ultimate3-in-1 conversion parts |
| LiDAR reference             | Current Pro listing: COIN-D6 ToF         | Standard listing: STL-19P D500 ToF                                     |
| Battery                     | 11.1 V 6000 mAh 3C lithium pack          | 11.1 V 6000 mAh 3C lithium pack                                        |
| Charge                      | 12.6 V matched charger; robot off        | Same voltage; use supplied charger                                     |
| Storage reference           | Record installed NX storage/image        | 128 GB SSD listed for Orin options                                     |
| Size/mass reference         | Ultimate284 × 212 × 544 mm; about 3.6 kg | Mecanum277 × 212 × 166 mm; about 2.66 kg                               |

These are model/configuration references; inspect the actual scanner label before selecting its driver. Do not load the Pro's COIN-D6 settings merely because a Standard robot has a similar USB plug. Vendor payload/dimension figures vary across revisions; no unsupported Pro lifting capacity is asserted here. [Exact Pro hardware](https://openelab.io/products/hiwonder-rosorin-pro-smart-car), [Standard hardware and tiers](https://openelab.io/products/hiwonder-rosorin-smart-car).

| Component reference | Documented numerical details                                                                           |
| ------------------- | ------------------------------------------------------------------------------------------------------ |
| Pro520 motor        | 12 V; 1: 90 gearing; 110rpm no-load/85rpm rated; 2.6 kg·cm rated/15 kg·cm stall; 3.2 A stall reference |
| Motor encoder       | AB quadrature; 11-line magnetic ring; 3.3–5 V encoder supply reference; PH2.0-6pin                     |
| Pro HX-12H servo    | 9–12.6 V; 0–1000 controller units correspond to 0–240°; 5264-3pin UART; 1.3 A stall reference          |
| Depth camera        | Aurora930 Pro; 40 mm baseline; 30–300 cm working range; 640 × 400 or 320 × 240 depth at 5–15fps        |
| Camera electrical   | USB2.0; 5 V±10%, 1.5 A interface rating; do not confuse with arm supply                                |
| Low-voltage warning | Recharge below 10 V; stop the robot before charging                                                    |

The servo table describes HX-12H; the Pro store separately identifies the gripper as HTS-21H. Do not assign one servo's voltage/current/torque to every actuator or treat stall torque as object payload. [Pro component manual](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html#_1-10-hardware-introduction).

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Follow each host's actual wiring

![Hiwonder ROSOrin Pro Orin Nano/NX numbered host port diagram](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/assets/image223.BX3JrMwe.webp)

Official Pro Orin port photograph, visually checked. It identifies **1** host power, **2** DP, **3** USB hub, **4** display, **5** STM32 communication, **6** voice box, **7** LiDAR, **8/9** reserved expansion and **10** depth camera. Numbers are photograph callouts, not electrical pin numbers. This diagram belongs to the **Pro**; the Standard has its own controller diagram and fewer attached devices. [Pro Orin wiring](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html#_1-2-5-2-jetson-orin-nano-orin-nx-wiring).

The battery enters the lower controller/power distribution assembly; use its matched host supply harness. Do not connect the 12.6 V charger directly to the Jetson DC input. The manual explicitly prohibits charging while the robot is on. Check polarity and keyed pack connection beneath the bottom cover with power off. Keep motor encoder plugs, power plugs and bus-servo plugs in their respective sockets.

The lower controller is STM32F407VET6-based; the Standard manual lists 168 MHz, 512 KB flash, 192 KB SRAM, four encoder-motor channels and 5 V host outputs up to 5 A. Those are board capabilities, not permission to supply this Orin through an arbitrary 5 V rail. IMU revisions differ in descriptions; identify the installed controller rather than combining an MPU6050 table with a QMI8658 driver. [Standard hardware](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/1_ROSOrin_User_Manual.html#_1-11-hardware-introduction).

### Sensor logic and connector viewpoint

The Pro's published four-pin LiDAR table is **Tx, Rx, GND, VCC** in its numbered drawing, with 0–3.3 V serial signals and 4.5–5.5 V supply. This belongs to that scanner connector, not to every robot UART or GPIO. Use the manufacturer's drawing viewpoint and actual scanner revision before repinning. The OLED I2C module has GND, 5 V, SDA, SCL; a 5 V module supply does not prove5 V-safe logic at a Jetson pin. Retain the original hub/adapters and cable orientation. [Pro LiDAR/OLED tables](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html#_1-10-hardware-introduction).

For Pro, check arm mounting, cable slack and gripper clearance at boot. The Standard page's pan-tilt/camera controls are not an arm API. Never execute a Pro servo-neutral or grasping routine on a model selected only by a similar product name.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

Both Orin branches use the delivered `~/ros2_ws`. Inspect `ros2 pkg prefix controller`, `ros2 pkg prefix peripherals`, `ros2 node list`, `ros2 topic list -t`, `cat /etc/os-release` and `printenv ROS_DISTRO ROS_DOMAIN_ID need_compile` before updates. Record the host's JetPack/BSP and image release, because a generic Ubuntu version does not qualify every camera/CUDA dependency.

The app autostart service is a command owner. With the robot stopped, the documented development transition is `sudo systemctl stop start_app_node.service`. After custom nodes terminate, restore `sudo systemctl restart start_app_node.service`. `~/.stop_ros.sh` is broader and stops ROS nodes. Do not run app driving, keyboard driving and autonomous navigation together. [Pro architecture](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html), [Standard architecture](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/1_ROSOrin_User_Manual.html).

| Interface                     | Purpose and check                                                                    |
| ----------------------------- | ------------------------------------------------------------------------------------ |
| `/controller/cmd_vel`         | Chassis Twist command; inspect actual subscriber/type before publishing              |
| `/odom_raw`                   | Encoder-derived odometry; verify frame names and stationary drift                    |
| `/imu`                        | Filtered IMU in the chassis course; raw input can be `/ros_robot_controller/imu_raw` |
| LiDAR scan/camera topics      | Discover names/types from the delivered graph rather than assuming a scanner driver  |
| Pro arm controller/kinematics | Additional services/messages in Pro image; absent from Standard is expected          |

The official chassis lesson contains a malformed abbreviated Twist type/layout in a command example. Use the installed interface definition (`geometry_msgs/msg/Twist`) and a properly structured message; the first example below is observation-only and avoids that command entirely. [Pro chassis course](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/2_Chassis_Motion_Control_Course.html).

## Getting started <a href="#getting-started" id="getting-started"></a>

### 1. First live result and environment identity

1. Charge while switched off. Place the robot on a clear level floor; Pro's arm must have an unobstructed reset sweep. Start the robot and wait for the short ready beep, not merely the flashing network LED.
2. Join the factory `HW…` hotspot with password `hiwonder`. Select the exact model in WonderAi: ROSOrin Pro for 21031913, ROSOrin for 21031729.
3. Open Robot Control and confirm a live image by moving a prop. Keep motion/arm controls untouched for this checkpoint.
4. On the computer, connect NoMachine to `192.168.149.1`. The Orin NX/Nano initial account is `ubuntu`/`ubuntu`; older Nano's `hiwonder` account is a different branch. Use the assigned LAN IP after changing network mode.
5. Record the environment and package checks above. Confirm the selected robot/scanner/camera/microphone configuration in the supplied configuration utility before launching a new driver.

\*\*Expected result: \*\* correct model shown in the app, changing camera image, reachable Orin desktop and readable ROS packages. Change factory credentials before shared-network use. [Pro remote access](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html#_1-7-development-environment-setup), [Standard manual](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/1_ROSOrin_User_Manual.html).

### 2. Original stationary odometry/IMU check

Run this on either assigned Orin image while the relevant factory feedback nodes are running. Save as `rosorin_stationary.py`, then `python3 rosorin_stationary.py`. If feedback nodes are absent, first enter a stopped development session and launch the **installed** documented controller/odometry and IMU bringup once. Inspect the actual graph rather than creating duplicate hardware owners.

```python
import math
import time
import rclpy
from rclpy.qos import qos_profile_sensor_data
from nav_msgs.msg import Odometry
from sensor_msgs.msg import Imu

rclpy.init()
node = rclpy.create_node('rosorin_stationary_check')
positions = []
imu_count = 0

def odometry(msg):
    p = msg.pose.pose.position
    if math.isfinite(p.x) and math.isfinite(p.y):
        positions.append((p.x, p.y))

def inertial(msg):
    global imu_count
    a = msg.linear_acceleration
    if all(math.isfinite(v) for v in [a.x, a.y, a.z]):
        imu_count += 1

subs = [node.create_subscription(Odometry, '/odom_raw', odometry,
                                 qos_profile_sensor_data),
        node.create_subscription(Imu, '/imu', inertial,
                                 qos_profile_sensor_data)]
try:
    end = time.monotonic() + 15
    while time.monotonic() < end:
        rclpy.spin_once(node, timeout_sec=0.2)
    print('odometry_samples=', len(positions), 'imu_samples=', imu_count)
    if len(positions) < 2 or imu_count == 0:
        raise SystemExit('INCOMPLETE: inspect topics, namespace and bringup')
    x0, y0 = positions[0]
    excursion = max(math.hypot(x-x0, y-y0) for x, y in positions)
    print('stationary_xy_excursion_m=', round(excursion, 6))
finally:
    node.destroy_node()
    rclpy.shutdown()
```

\*\*Expected result: \*\* nonzero finite feedback and a small reported stationary XY excursion. No universal pass threshold is invented: record the value and compare repeat runs with the robot physically stationary. A nonzero count does not validate encoder scale, IMU mounting or absolute navigation accuracy. If the actual image namespaces these topics, replace the names only after checking `ros2 topic list -t`.

### 3. Chassis calibration and a short floor test

Verify wheel orientation and motor/encoder assignments first. With one operator at START/stop, make separate short forward, lateral and rotation moves using the supplied gamepad. Check that release/stop behavior is predictable before trying a keyboard latch. The manual's keyboard mode can continue moving after a short key press; it should not be treated as hold-to-run control.

The chassis course separates IMU calibration, linear scale and angular scale. Back up `~/ros2_ws/src/calibration/config/imu_calib.yaml` before using its calibration tool. Keep the robot stationary for IMU bias acquisition, then compare commanded motion with measured floor distance/yaw. Use `calibration linear_calib.launch.py` and `angular_calib.launch.py` only after inspecting their parameters and clearing the motion area. Do not use scale tuning to hide reversed wheels or an incorrect chassis model. [Pro chassis](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/2_Chassis_Motion_Control_Course.html), [Standard chassis](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/2_Chassis_Motion_Control_Course.html).

### 4. Build and preserve a map

Stop app control while stationary, then use separate terminals:

```bash
ros2 launch slam slam.launch.py
ros2 launch slam rviz_slam.launch.py
ros2 launch peripherals teleop_key_control.launch.py
```

Drive a short closed loop in a level room, watching whether scan walls overlap and the pose moves in the physical direction. Save under a new name with the course's map-saving workflow; keep image/YAML together and verify resolution, origin and image path. The quick desktop experience can replace a prior map, so retain copies before making another.

For ordinary navigation, the matched course uses `ros2 launch navigation navigation.launch.py map:=map_01` and `ros2 launch navigation rviz_navigation.launch.py`. Confirm that `map_01` exists in that image's configured map directory. Initialize pose with 2D Pose Estimate, align scan/map walls and request one nearby unobstructed goal. \*\*Expected result: \*\* a sensible path, controlled travel and a completed goal. A Pro must clear obstacles with the arm/display as well as the base.

RTAB-Map uses separate launches/databases; road-network routing also needs its waypoint/route data. Do not combine two localization authorities or assume a 2D map image contains all3D/route information. [Pro mapping](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/5_Mapping_&_Navigation_Course.html), [Standard mapping](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/5_Mapping_&_Navigation_Course.html).

### 5. Pro arm and the remaining official courses

\*\*Pro only: \*\* back up servo deviations, position/hand-eye calibration and action files before adjustments. Establish a fixed camera/table setup, validate segmentation and target coordinates, then test an unloaded small arm movement. Start with a supplied light block. The gripper servo differs from arm joints; verify ID, range and neutral posture before issuing any position list. A Standard image is not upgraded into a mobile manipulator by installing the Pro launch name. [Pro arm course](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/8_Robotic_Arm_Motion_Control.html).

| Topic family                                                                  | Prerequisites and meaningful result                                                                                                                                                                      |
| ----------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Camera basics and LiDAR avoidance/following/guarding                          | Confirm live streams and correct sensor model first; test one behavior and its stop service at a time                                                                                                    |
| Color thresholds, tags/AR, coordinates, KCF, face tracking and line following | Inspect overlays with motion inactive; calibrate masks and frames before linking detections to chassis/arm                                                                                               |
| Machine learning/MediaPipe/YOLO                                               | Verify model/dependency version in the delivered image; record latency on the selected Nano/NX without promising identical throughput                                                                    |
| Pro 2D/3D grasping and mobile transport                                       | Separate color recognition, depth validity, hand-eye geometry, IK and gripper contact; test each before a combined route                                                                                 |
| Voice                                                                         | Both assigned kits use WonderEcho Pro; configure that device rather than the six-mic Ultimate option of another ROSOrin tier                                                                             |
| Gazebo/URDF and Pro MoveIt2                                                   | Validate joint names, frames and collision geometry in simulation; do not start a physical bridge during simulation-only planning                                                                        |
| Group control                                                                 | Distinct names/namespaces and one owner per chassis; test an individual robot before group broadcast                                                                                                     |
| Large models and Pro OpenClaw                                                 | Test provider/audio/image responses without robot tools first; then inspect action functions, maps and timeouts. OpenClaw requires its supported ROS 2 image and does not make every local model fit8 GB |

Use each model's official topic index for exact launches: [Pro courses](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html), [Standard courses](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/1_ROSOrin_User_Manual.html). On-device AI, cloud inference and conventional local ROS behavior are separate dependencies.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

| Symptom                                       | Diagnosis before changing firmware                                                            |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Beeping below 10 V or resets under motor load | Stop and charge with robot off; inspect pack/cables before ROS tuning                         |
| Camera works but LiDAR/navigation does not    | Check exact scanner label, driver selection, serial enumeration, scan timestamps and TF       |
| Local feedback works but remote RViz is empty | Compare ROS domain, namespace, LAN and clock; confirm local graph first                       |
| Chassis drifts/strafe is wrong                | Verify Mecanum rollers, encoder sign, motor assignment, then scale/IMU calibration            |
| Pro arm misses a visible block                | Check camera registration, offset/table height, servo deviation, reach and gripper separately |
| Standard has no arm package                   | Expected for this model; use its chassis/camera workflows                                     |
| Model voice is silent                         | Check WonderEcho Pro selection, USB audio route, firmware and provider/network requirements   |
| App unavailable after custom code             | Stop custom owners and restart `start_app_node.service`                                       |

**Can the Standard switch to Ackermann?** Its ordered Standard kit does not include the conversion hardware shown for Advanced/Ultimate. Mechanical conversion also requires matching kinematic/driver configuration.

**Which image should I restore?** The exact model/controller image. Back up maps, calibration, robot/sensor selections, network and API configuration. Obtain matching NX Pro or Nano Standard resources; inspect the target disk before writing. An image replacement can erase custom calibration and does not repair reversed power wiring.

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                               | Verified manufacturer destination                                                                                                                                                       |
| -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pro full manual/power/component tables | [ROSOrin Pro manual](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html)                                                                      |
| Standard exact Orin manual             | [ROSOrin Jetson/Orin manual](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/1_ROSOrin_User_Manual.html)                                                    |
| Pro image/source/hardware collection   | [ROSOrin Pro Resources](https://drive.google.com/drive/folders/1MnJEjFJ0unkbC2EDJeqvwFycdHSjqqf4?usp=sharing)                                                                           |
| Pro applications and source inspection | [Hiwonder/ROSOrin-Pro](https://github.com/Hiwonder/ROSOrin-Pro); match release to delivered image                                                                                       |
| App/remote tools                       | [Pro appendix direct downloads](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/Appendix.html)                                                                            |
| Controller firmware tool               | [ATK-XISP folder](https://drive.google.com/drive/folders/1lAfcomXygNwiigQVlA9EgW3Txlp4Nkhs?usp=sharing); not a reason to flash on first boot                                            |
| Standard hardware/image links          | [Standard manual resources and recovery](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/1_ROSOrin_User_Manual.html); use its observed model-specific links |
| Schematics/mechanical/SDK examples     | Each model's hardware materials and embedded chassis/control examples; no unverified common CAD or firmware binary is substituted                                                       |

Individual archive versions/checksums were not exhaustively inspected. Use the matching resource release and save its filename/hash before changes.

### Additional established resources

These established links supplement the model-specific resources above. The Raspberry Pi ROSOrin link is a host-specific reference, not the image for either assigned Jetson variant. Retain the matching model, host and revision when selecting a download.

* [manufacturer product data](https://www.hiwonder.com/products/rosorin-pro)
* [ROSOrin base manual — controller and chassis branches](https://wiki.hiwonder.com/projects/ROSOrin/en/raspberry-pi-version/docs/1_ROSOrin_User_Manual.html)
* [Manufacturer Hiwonder ROSOrin ROS 2 AI Mecanum Robot Car with SLAM, LLM Vision & Jetson/RPi5 Options specifications and option drawings](https://www.hiwonder.com/products/rosorin)

## ROSOrin Pro and ROSOrin engineering reference <a href="#rosorin-full-reference" id="rosorin-full-reference"></a>

This reference follows the official ROSOrin Pro courses and the separate ROSOrin Orin courses. It applies to **Pro Ultimate / Orin NX SUPER 16 GB, SKU `Hiwonder-21031913`**, and **ROSOrin Standard / Orin Nano SUPER 8 GB, SKU `Hiwonder-21031729`**. The Standard configuration has no manipulator; arm, grasping, mobile transport and Pro OpenClaw procedures below are marked accordingly. The supplied Mecanum configurations are the starting point. Describing an Ackermann or tracked algorithm does not establish that conversion hardware is included.

The source articles are moving web documents reviewed on 24 November 2026. Package names and illustrated parameters identify the documented image, rather than a promise that every previously shipped image contains them. Keep the delivered image, controller firmware, calibration and model files together. [Pro course manual](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html), [Standard Orin course manual](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/1_ROSOrin_User_Manual.html).

## Host images, configuration and command ownership <a href="#rosorin-reference-host" id="rosorin-reference-host"></a>

### Choose a complete software lane <a href="#rosorin-reference-lanes" id="rosorin-reference-lanes"></a>

| Lane                   | Environment and files                                               | Scope                                                                                       |
| ---------------------- | ------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| Assigned NX Pro        | Orin NX, Ubuntu 22.04, ROS 2 Humble; `~/ros2_ws`, `install` overlay | Pro hardware, six-servo arm, Aurora camera, WonderEcho Pro and Ultimate display             |
| Assigned Nano Standard | Orin Nano, Ubuntu 22.04, ROS 2 Humble; its own `~/ros2_ws`          | Base, camera and sensors; do not install an arm launch as a substitute for missing hardware |
| Older Jetson Nano      | Its matching image and ROS 1 or Docker materials                    | Different processor generation, account and package layout; not an Orin recovery image      |
| Raspberry Pi 5         | Separate Debian/container instructions and wiring                   | Does not inherit Jetson CUDA, USB gadget networking or an Orin image                        |
| Simulation workstation | Supplied ROS 2 virtual-machine packages                             | A distinct computer; simulation success does not confirm the robot's hardware interfaces    |

For the Pro source repository, the observed `orin-nx` commit is `6c2a621fe628cc4928c48fc11d8d982594d471eb`; `orin-nano` is a separate branch. The repository's default `jetson-nano` branch is not the assigned NX software path. Standard ROSOrin has a separate repository and `ROS2` branch. Use these as inspectable source references, not instructions to overwrite an existing factory workspace. [Pro NX source tree](https://github.com/Hiwonder/ROSOrin-Pro/tree/6c2a621fe628cc4928c48fc11d8d982594d471eb), [Standard ROS 2 source tree](https://github.com/Hiwonder/ROSOrin/tree/52b5af20893836e4faff6d27ad5660376b36a036).

Before changing software, record the following in the robot's own maintenance log:

```bash
cat /etc/os-release
uname -m
printenv ROS_VERSION ROS_DISTRO ROS_DOMAIN_ID MACHINE_TYPE need_compile HOST MASTER
ros2 pkg prefix controller
ros2 pkg prefix ros_robot_controller
ros2 topic list -t
ros2 node list
```

**Expected result:** an AArch64 Orin system, the intended ROS 2 environment and installed package paths consistent with the supplied workspace. A missing variable is a reason to inspect the installed startup configuration, not to assign a guessed value. The source uses `need_compile` to choose installed package shares or source directories; a stale overlay can therefore select different launch/configuration files from the ones being edited.

The workspace separates `driver` for controller/kinematics/servos, `peripherals` for device bringup, `app` for phone behaviors, `calibration`, `slam`, `navigation`, `example`, `interfaces`, `xf_mic_asr_offline`, `large_models`, `large_models_examples` and `simulations`. `build`, `install` and logs are generated artifacts; back up the editable configuration and action files in addition to the image. [Pro software directory descriptions](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html#_1-12-system-software-architecture).

### Stop competing publishers before any moving course <a href="#rosorin-reference-ownership" id="rosorin-reference-ownership"></a>

1. Park on a level, clear floor. For Pro, clear the entire arm reset sweep, gripper and display, and remove any carried object. Keep a tested physical stop/power control reachable.
2. End phone, gamepad, navigation, tracking, voice and AI actions. With the robot stopped, stop `start_app_node.service` before a standalone lesson.
3. Inspect `/controller/cmd_vel` with `ros2 topic info /controller/cmd_vel --verbose`. Confirm its message type, command publishers and controller subscriber. One selected behavior should own motion. A zero command from one publisher cannot safely arbitrate against another publisher repeatedly sending nonzero commands.
4. Launch the selected course once. Do not launch a second serial controller or camera driver on the same device.
5. Stop the behavior through its stop service or a zero chassis command, verify actual rest, then terminate its processes. Only afterwards restore the app service.

```bash
sudo systemctl stop start_app_node.service
ros2 topic info /controller/cmd_vel --verbose
# After the standalone behavior has stopped and exited:
sudo systemctl restart start_app_node.service
```

These service changes are for the supplied image. `~/.stop_ros.sh` is a broader process cleanup tool; inspect its scope before using it and do not treat process termination as a guaranteed motor stop. Several course examples explicitly retain a commanded velocity after their terminal exits. [Chassis speed-control and stop notes](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/2_Chassis_Motion_Control_Course.html#_2-1-5-robot-speed-control).

### Network, remote access and image recovery <a href="#rosorin-reference-network-recovery" id="rosorin-reference-network-recovery"></a>

The factory `HW…` access point uses password `hiwonder`; NoMachine normally reaches `192.168.149.1`, with `ubuntu`/`ubuntu` for the assigned Orin hosts. The blinking blue network indicator can appear before ROS initialization; wait for the ready beep. A steady indicator may mean the robot has joined a LAN. The documented KEY1 hold is 5–10 seconds to return to AP behavior; verify the actual board and button before applying that recovery. On a LAN, discover the assigned address and keep the computer on a reachable network. AP association alone does not give cloud AI internet access; the course uses STA networking or an Ethernet uplink. [Pro startup and remote connection](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html#_1-7-development-environment-setup).

Jetson's USB network path uses the host's data port and `192.168.55.1`, after the computer recognizes its NDIS network device. This is a network connection, not a charger connection. The manufacturer explicitly excludes Pi 5 from this procedure. NoMachine is the desktop path, MobaXterm supplies SSH/file transfer, and VNC is an alternative desktop implementation; diagnose authentication, routing and display service separately.

The assigned robot uses an 11.1 V pack and 12.6 V matched charger. Charge with the robot switched off; never insert that charger into a Jetson host's DC socket. The lower controller's broader input specification does not approve arbitrary assembled-robot supply voltages. A charger indicator that is green with no battery attached is not evidence of a charged pack.

For recovery, first preserve maps and their YAML files, sensor/machine selections, Wi-Fi settings, arm deviations, action groups, color thresholds, camera/hand-eye parameters and private provider configuration. Shut down, disconnect power and identify the actual boot medium. The Pro manual's Orin procedure uses an SSD and a separately prepared SSD writer; its older Nano/Pi examples use SD media. Obtain the exact model/host image and check the destination drive's capacity and identity before writing it. The documented Windows sequence is select the extracted image in Win32DiskImager, select the correct device, write, and wait for completion. Multiple resulting partitions are expected: cancel Windows prompts to format them. Reinsert the medium only with power off. This guide does not supply an unverified image checksum or automate disk erasure. Restore MCU firmware separately only when its board/model match is established. [Pro image recovery](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/1_ROSOrin_Pro_User_Manual.html#_1-13-image-flashing).

## MCU transport, feedback and application APIs <a href="#rosorin-reference-mcu" id="rosorin-reference-mcu"></a>

### Separate three different interfaces <a href="#rosorin-reference-serial-layers" id="rosorin-reference-serial-layers"></a>

The Orin-to-STM32 connection carries framed **RRC** messages. The controller then drives encoder motors and half-duplex serial bus servos. The ROS topic API is a third layer. A servo's UART setting is not the USB controller baud rate, and neither gives permission to connect a Jetson GPIO directly to the servo signal wire.

The pinned Pro NX and Standard SDKs open `/dev/rrc` at **1,000,000 baud**, with reception initially disabled. Both SDKs transmit fields in this order:

| Offset    | Field    | Interpretation                                                     |
| --------- | -------- | ------------------------------------------------------------------ |
| 0–1       | `AA 55`  | Synchronization bytes                                              |
| 2         | Function | Unsigned 8-bit controller function                                 |
| 3         | Length   | Number of payload bytes; excludes header, function, length and CRC |
| 4 onward  | Payload  | Function-specific, little-endian for the typed fields below        |
| Last byte | CRC-8    | Covers function, length and payload; header excluded               |

The actual `buf_write` and receive state machine establish this order; an older comment lists length before function and is not the implementation. The SDK CRC table is equivalent to an initial-zero reflected CRC-8 loop with polynomial `0x8C`. A valid checksum establishes transport integrity, not that a command matches the attached mechanism. [Pro NX SDK](https://raw.githubusercontent.com/Hiwonder/ROSOrin-Pro/6c2a621fe628cc4928c48fc11d8d982594d471eb/ROS2/src_ros2/src/driver/ros_robot_controller/ros_robot_controller/ros_robot_controller_sdk.py), [Standard SDK](https://raw.githubusercontent.com/Hiwonder/ROSOrin/52b5af20893836e4faff6d27ad5660376b36a036/src_ros2/src/driver/ros_robot_controller/ros_robot_controller/ros_robot_controller_sdk.py).

| Function | SDK family | Important field distinctions                                                                                                                                     |
| -------- | ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `00`     | System     | Battery feedback uses subcommand `04` plus an unsigned LE 16-bit raw value; do not accept the SDK comment's incorrect “mAh voltage” unit                         |
| `01`     | LED        | LED ID `u8`, on/off times `u16` milliseconds, repeat count `u16`                                                                                                 |
| `02`     | Buzzer     | Frequency `u16`, on/off milliseconds `u16`, repeat count `u16`                                                                                                   |
| `03`     | Motor      | Speed subcommand `01`, motor count, then wire index `u8` and LE float rps for each motor                                                                         |
| `04`     | PWM servo  | A separate servo type. These two pinned ROSOrin SDKs use subcommand `03`, LE duration and ID/position pairs, not JetRover's count-bearing subcommand `01` format |
| `05`     | Bus servo  | Subcommands for position, stop, ID, offset, limits and readback; not raw bytes sent straight to a servo                                                          |
| `06`     | Keys       | Key ID and event flags; press, release, click and long press differ                                                                                              |
| `07`     | IMU        | Six LE floats in acceleration-x/y/z, gyro-x/y/z order; get physical units from the matched ROS conversion layer                                                  |
| `08`     | Gamepad    | Raw button/hat/axis report, normalized by the SDK                                                                                                                |
| `09`     | SBUS       | Sixteen signed channel values and separate channel-17/18, lost-signal and failsafe flags                                                                         |
| `0A`     | OLED       | Line, text length and encoded text; multibyte text needs particular care because the SDK counts Python characters before UTF-8 encoding                          |

The motor SDK accepts IDs 1–4 but subtracts one when packing the wire index. Wheel speed is rotations per second, not PWM duty, rpm or chassis m/s. Do not bypass kinematics by passing a Twist linear speed as motor rps. A raw battery value requires the installed node's scale before labeling it V; preserve the raw value when inspecting a capture.

### Bus-servo command/readback reference <a href="#rosorin-reference-bus-servo-api" id="rosorin-reference-bus-servo-api"></a>

The following are the pinned controller SDK's bus-servo subcommands, all within RRC function `05`. They are useful for interpreting logs and porting a driver; use the installed ROS controller for normal operation.

| Operation                             | Subcommand / fields after it                                                                                                |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Position                              | `01`, duration `u16` milliseconds, count `u8`, repeated servo ID `u8` + position `u16`                                      |
| Stop selected servos                  | `03`, count and ID list                                                                                                     |
| Read position / voltage / temperature | Request `05` / `07` / `09`, then servo ID                                                                                   |
| Torque control                        | SDK `bus_servo_enable_torque`: true sends `0B`, false sends `0C`, followed by ID; unloading can let an unsupported arm fall |
| Set / read ID                         | `10` old ID + new ID; read `12` + ID                                                                                        |
| Set / read / persist offset           | `20` ID + signed 8-bit offset; `22` ID; `24` ID                                                                             |
| Set / read angle limits               | `30` ID + two LE `u16`; read `32` ID                                                                                        |
| Set / read voltage limits             | `34` ID + two LE `u16`; read `36` ID                                                                                        |
| Set / read temperature limit          | `38` ID + signed byte; read `3A` ID                                                                                         |
| Read torque state                     | `0D` ID                                                                                                                     |

Readback begins with servo ID, echoed subcommand and signed success byte: **0 succeeds; −1 fails**. Position uses a signed LE 16-bit result in the read method, voltage an unsigned LE 16-bit result, and temperature an unsigned byte. Check the frame function, requested ID, subcommand, status, length and CRC before decoding. Do not broadcast an ID change to an assembled six-servo chain. Saving an offset is a persistent configuration change, unlike merely moving a joint. The SDK's servo read routine waits on a queue without a call-level deadline, so an application should bound the wait and avoid blocking a ROS control callback indefinitely. [Pinned bus-servo methods](https://raw.githubusercontent.com/Hiwonder/ROSOrin-Pro/6c2a621fe628cc4928c48fc11d8d982594d471eb/ROS2/src_ros2/src/driver/ros_robot_controller/ros_robot_controller/ros_robot_controller_sdk.py).

### ROS graph boundaries <a href="#rosorin-reference-ros-api" id="rosorin-reference-ros-api"></a>

| Interface observed in the courses/source                    | Role and units                                                                                  |
| ----------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| `/controller/cmd_vel`, `geometry_msgs/msg/Twist`            | Body-frame x/y m/s and z rad/s, interpreted by the selected kinematics                          |
| `/odom_raw`, `nav_msgs/msg/Odometry`                        | Raw wheel-odometry pose/twist; separate from fused output                                       |
| `/imu`, `sensor_msgs/msg/Imu`                               | Filtered IMU; raw source is `/ros_robot_controller/imu_raw`                                     |
| `ros_robot_controller/set_motor`, `MotorsState`             | Per-motor speed command; additional slash/namespace resolution depends on node placement        |
| Pro controller's `ros_robot_controller/pwm_servo/set_state` | PWM-servo state command in the illustrated controller; not the six-joint bus-arm position topic |
| `controller/load_calibrate_param`, `std_srvs/srv/Trigger`   | Reload motion calibration parameters                                                            |
| `set_odom`, `geometry_msgs/msg/Pose2D`                      | Reset/set odometry reference; not a passive sensor read                                         |
| `~/init_finish`, `std_srvs/srv/Trigger`                     | Node-private initialization status                                                              |

Some source analysis paragraphs say “publish” while the code creates a subscription. Read the code/interface definition and inspect the live graph before choosing a direction. Resolve namespaces and message definitions with `ros2 topic info`, `ros2 service type` and `ros2 interface show`; do not infer an arm topic from a chassis callback. [Chassis implementation and interfaces](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/2_Chassis_Motion_Control_Course.html#_2-1-5-5-program-analysis).

## Mecanum motion and calibration <a href="#rosorin-reference-motion" id="rosorin-reference-motion"></a>

### Wheel geometry, signs and units <a href="#rosorin-reference-kinematics" id="rosorin-reference-kinematics"></a>

The documented Mecanum model numbers motors 1/2 on the left front/rear and 3/4 on the right front/rear in the diagram, with x forward and y left. Let `k = (wheelbase + track_width)/2`. Its wheel linear speeds are `x − y − kω`, `x + y − kω`, `x + y + kω`, `x − y + kω`; conversion to motor rps divides by `π × wheel_diameter`, then reverses the right-hand motors' signs for their physical mounting. Preserve that numbering/viewpoint when comparing logs.

The Pro course's controller instantiates **0.17706 m wheelbase, 0.17165 m track and 0.08 m Mecanum wheel diameter**. The same article also contains a generic class default of `0.0065 m` and unrelated Ackermann steering notes. They are inconsistent with that instantiated model and must not become measured Pro geometry. Read the installed configuration, measure the actual robot and calibrate its scale; do not transfer a JetRover wheel diameter. The Standard branch has its own controller/configuration. [Pro Mecanum source analysis](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/2_Chassis_Motion_Control_Course.html#_2-2-2-mecanum-chassis), [Standard chassis course](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/2_Chassis_Motion_Control_Course.html).

### IMU bias and odometry scale are separate calibrations <a href="#rosorin-reference-calibration" id="rosorin-reference-calibration"></a>

Factory calibration should be retained unless measurements show a problem. Back up `~/ros2_ws/src/calibration/config/imu_calib.yaml` and `~/ros2_ws/src/driver/controller/config/calibrate_params.yaml` first. The documented IMU procedure starts the lower controller and then:

```bash
ros2 run imu_calib do_calib --ros-args \
  -r imu:=/ros_robot_controller/imu_raw \
  --param output_file:=/home/ubuntu/ros2_ws/src/calibration/config/imu_calib.yaml
```

Follow the six positive/negative axis orientations shown by the manufacturer, stabilizing the robot before each acquisition. Support the Pro's arm and secure its hardware; do not balance a powered mobile manipulator precariously to reproduce a diagram. Inspect orientation with `ros2 launch peripherals imu_view.launch.py`. **Expected result:** the displayed attitude follows the actual tilt direction. A successful write does not establish wheel scale or yaw accuracy. [IMU procedure and orientation figures](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/2_Chassis_Motion_Control_Course.html#_2-1-1-imu-calibration).

For linear calibration, mark a measured 1 m course with runout room, set the applicable correction factor to 1.0 and launch `calibration linear_calib.launch.py` with the controller. Its illustrated `test_distance` is 1 m and speed 0.2 m/s. For angular calibration, mark the initial heading and use `angular_calib.launch.py`; the illustrated test is 360°. The article calls its speed “0.15 m/s” even in the angular panel: inspect the installed parameter type/units rather than converting that label into a yaw rate. Smaller tolerance can increase end-point oscillation. The course adjusts the GUI scale in 0.01 steps, then saves the resulting linear/angular factor in the controller YAML. A screenshot misspells `angular_correctqion_factor`; the actual controller parameter is `angular_correction_factor`.

Measure each run physically. Reversed wheels, a wrong machine selection, loose hubs and slipping rollers must be corrected before tuning factors. Compare forward and reverse motion, lateral motion and yaw separately. Encoder odometry accumulates error; IMU fusion cannot restore an absolute position after slip without an external reference. [Linear/angular calibration](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/2_Chassis_Motion_Control_Course.html#_2-1-motion-control).

### Observe feedback, then command a deliberately bounded move <a href="#rosorin-reference-motion-test" id="rosorin-reference-motion-test"></a>

With competing owners stopped, the documented feedback paths are `ros_robot_controller ros_robot_controller.launch.py`, `peripherals imu_filter.launch.py` and `controller odom_publisher.launch.py`. Do not run them a second time if the selected `controller.launch.py` already includes them and its EKF. Confirm `/imu` and `/odom_raw` types, rates, timestamps and frames while stationary, then compare signs during a manually controlled short floor move.

The velocity article's flattened Twist example is not valid structured ROS 2 YAML. After establishing a single command owner, a zero command with an explicit message type is:

```bash
ros2 topic pub --once /controller/cmd_vel geometry_msgs/msg/Twist \
  '{linear: {x: 0.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.0}}'
```

For a first physical move, use the tested gamepad with a slight deflection and release/START stop, or a bounded application that publishes zero on timeout and interruption. The course's 0.3 m/s demonstration and suggested ±0.6 m/s range are not mandatory commissioning speeds. Reserve enough space for stopping and verify that a nonzero command has actually ended before closing the terminal. A zero velocity request cannot guarantee stopping after power/communications failure.

## LiDAR observation and reactive behaviors <a href="#rosorin-reference-lidar" id="rosorin-reference-lidar"></a>

The Pro listing and Standard listing can specify different scanner models. Read the label and select the matching driver in the supplied tool; a USB connector does not establish protocol compatibility. First inspect `sensor_msgs/msg/LaserScan`, `angle_min`, `angle_increment`, timestamp and scan frame in RViz. Rotate a cardboard target around the stationary robot and confirm the scan sector and distance change in the expected direction. Missing or invalid returns are not verified free space.

The Pro course uses the following behavior interface after `ros2 launch app lidar_node.launch.py debug:=true`:

| Step   | Exact course interface                              | Effect                                                  |
| ------ | --------------------------------------------------- | ------------------------------------------------------- |
| Enter  | `/lidar_app/enter`, `std_srvs/srv/Trigger`          | Initialize the feature                                  |
| Select | `/lidar_app/set_running`, `interfaces/srv/SetInt64` | 1 avoidance, 2 following, 3 guarding                    |
| Stop   | Same `set_running` service with `data: 0`           | Stop the selected reactive behavior before process exit |

Avoidance can drive forward and turn; following can drive forward or reverse; guarding rotates to face a target. Each therefore needs a clear base/arm sweep even if the name sounds observational. Test stop first, then one mode, with no navigation or teleoperator active. **Expected result:** scan changes correlate with the selected behavior and `data: 0` returns the robot to rest. Confirm the actual service names in the installed Standard graph before applying the Pro prefix; model/course revisions need not expose identical namespaces. These are educational reactive controllers, not a certified obstacle or cliff safety system. [Pro LiDAR course](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/3_LiDAR_Course.html), [Standard LiDAR course](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/3_LiDAR_Course.html).

The Standard article capitalizes `LiDAR_node.launch.py` and `/LiDAR_app`, but the separately reviewed Standard repository actually contains lowercase `lidar_node.launch.py` and instantiates `lidar_app`. Linux/ROS names are case-sensitive. Use the installed package/graph to resolve that documentation error. In the pinned Standard node, `~/set_param` takes `interfaces/srv/SetFloat64List` with **\[threshold meters, scan angle degrees, speed]**. Its checks accept threshold 0.3–1.5 m, angle 0–90°, and positive speed without an explicit upper-speed check. Those checks are not complete robot safety limits. The node's initial threshold is 0.6 m; do not substitute JetRover's prose stand-off. The valid-setting handler also does not explicitly set the response success field, so an empty/default response is not a reliable confirmation of applied configuration. Inspect the matched runtime before automating this write. [Exact Standard controller](https://raw.githubusercontent.com/Hiwonder/ROSOrin/52b5af20893836e4faff6d27ad5660376b36a036/src_ros2/src/app/app/lidar_controller.py).

## Camera data, depth geometry and standalone tools <a href="#rosorin-reference-depth" id="rosorin-reference-depth"></a>

Both assigned ROSOrin options identify **Aurora930 Pro**. The camera course delegates to the separate Aurora manual. Its unambiguous module specifications include 40 mm baseline, USB 2.0, 30–300 cm working distance, 5 V ±10% supply and a 1.5 A interface rating. Published accuracy is 8 mm at 1 m; precision is separately listed as 3 mm at 0.5 m and 7 mm at 1 m. These are manufacturer reference conditions, not measured results from these robots. Depth profiles are listed at 640 × 400 or 320 × 240, 5–15 fps. The source's merged format/laser-safety cells are not a reliable one-to-one stream-format table; discover each installed ROS message encoding rather than assigning NV12 or raw-8 to the depth topic. [Aurora module manual](https://wiki.hiwonder.com/projects/Aurora930-Pro/en/latest/docs/1.Introduction_to_Depth_Camera.html).

Start the factory `peripherals depth_camera.launch.py` only after ensuring that another camera owner is stopped. In RViz inspect RGB, depth, CameraInfo and point cloud separately. Check the depth encoding and scale, frame IDs, RGB/depth registration and valid range before computing a metric point. For a calibrated pinhole model, `X=(u−cx)Z/fx`, `Y=(v−cy)Z/fy`, `Z=depth`; this requires intrinsics for that stream and depth already converted into meters. An invalid depth or RGB pixel without registration cannot produce a valid grasp target. Arm movement changes the camera pose; use current joint state and the matched hand-eye transform.

The separate camera workbench is an **x86\_64 VM** lane, not the robot's AArch64 installation. Its ROS 1 example is Ubuntu 18.04/Melodic with `catkin_make -DSTREAM_SDK_TYPE=AURORA930`; the ROS 2 example is Ubuntu 22.04/Humble with `colcon build --cmake-args -DSTREAM_SDK_TYPE=AURORA930`. It names ROS 2 archive revision `0.2.10` and a bundled x86\_64 stream SDK `v1.1.19-18.04`. Use USB passthrough to attach the camera to one VM and confirm the matching udev rules. Do not copy those x86\_64 libraries into Orin. The standalone ROS 2 launches are `deptrum-ros-driver-aurora930 aurora930_launch.py` and `viewer930_launch.py`; they are alternatives to, not companions for, the robot's factory wrapper. The ROS 1 launch pair is `driver_aurora930.launch` / `viewer_aurora930.launch`. The article has `ro1`/`ros1` filename inconsistencies, so select the actual extracted archive, not a guessed spelling. [Camera ROS workbench](https://wiki.hiwonder.com/projects/Aurora930-Pro/en/latest/docs/2.Configuration_and_Usage_in_ROS.html).

For an independent Windows check, the manufacturer names `deptrum-scope-windows-amd64-v3.6.45.zip`, the included WinUSB installer and `DeptrumScope.exe`. A missing runtime DLL calls for the matching x64 Visual C++ redistributable, not an Orin driver change. Verify color, IR, depth and point-cloud displays individually, then disconnect the workbench before reconnecting the robot. Archive contents/checksums remain subject to access to the manufacturer's download collection. [Windows camera tool](https://wiki.hiwonder.com/projects/Aurora930-Pro/en/latest/docs/3.Configuration_and_Usage_in_Windows.html).

## Mapping, localization and navigation reference <a href="#rosorin-reference-navigation" id="rosorin-reference-navigation"></a>

### URDF/Xacro, frames and collision geometry <a href="#rosorin-reference-urdf" id="rosorin-reference-urdf"></a>

URDF describes links, joints, inertial properties, visual meshes and collision geometry. Xacro adds reusable macros and parameters before generating that model. Keep `origin xyz/rpy`, joint axis and parent/child relationships consistent with physical sensor mounting. Revolute limits use radians, effort is torque in N·m for a rotary joint and force in N for a prismatic joint, and velocity uses rad/s or m/s respectively; some course tables incorrectly generalize the linear units. A display mesh does not automatically provide a useful collision model.

The mapping article points to `simulations/rosorin_description/urdf`, while the simulation workstation examples use `rosorin_description/urdf` directly. Inspect the installed package path. Use the correct Pro or Standard model; the Pro arm and display enlarge the swept envelope and alter the camera transform. In RViz inspect the complete tree from map/odom through the base to scanner and camera. Do not allow two publishers to define the same dynamic localization transform. [Model and mapping course](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/5_Mapping_&_Navigation_Course.html#_5-1-mapping-tutorial).

### A complete 2D mapping and save cycle <a href="#rosorin-reference-slam2d" id="rosorin-reference-slam2d"></a>

1. Check battery, scan, IMU/odometry direction and the selected robot model. Clear the route and stop other command owners.
2. In separate terminals launch `slam slam.launch.py`, `slam rviz_slam.launch.py` and the chosen teleoperator. `peripherals teleop_key_control.launch.py` can latch forward/reverse motion after a short W/S press; establish its stop behavior before approaching a wall.
3. Drive slowly through a short loop, revisiting visible features. Inspect wall overlap, loop closure and abrupt pose jumps. Slippage or an incorrect scanner transform should be repaired before changing SLAM parameters.
4. Save to a new map name, keeping the image and YAML together. The corrected ROS 2 command below removes the stray trailing Markdown `**` in the Pro article.
5. Stop motion, terminate the mapping nodes cleanly and confirm the saved YAML's image path, resolution and origin. Reopen a saved map before trusting it for a navigation task.

```bash
cd ~/ros2_ws/src/slam/maps
ros2 run nav2_map_server map_saver_cli -f room_reference \
  --ros-args -p map_subscribe_transient_local:=true
```

**Expected result:** a coherent occupancy grid and readable `room_reference.yaml` plus its referenced image. The illustration's `map_01` is a filename choice, not a reserved map. Back up an existing file before reusing its name. `slam/config/slam.yaml` configures the documented slam\_toolbox path. The course explains scan matching, pose estimation and loop closure through Karto-related concepts; that background does not make an old ROS 1 launch compatible with the current ROS 2 wrapper. [SLAM operations and save command](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/5_Mapping_&_Navigation_Course.html#_5-1-4-slam-toolbox-mapping-algorithm).

### Nav2 configuration, AMCL and waypoint behavior <a href="#rosorin-reference-nav2" id="rosorin-reference-nav2"></a>

Launch `navigation navigation.launch.py map:=room_reference` and `navigation rviz_navigation.launch.py` only after that map exists in the configured directory. Use **2D Pose Estimate** to place the robot at its actual map pose and heading. The laser walls should align with map walls before sending a nearby goal. AMCL maintains a particle distribution over pose; a sharply wrong initial pose can converge to the wrong part of a repetitive room. Distinguish the global map from the rolling local costmap and from live raw scans.

The documented wrapper exposes `sim`, `map`, `robot_name`, `master_name` and `use_teb`; it passes a map YAML and `navigation/config/nav2_params.yaml` to bringup. It also uses namespaces and delays navigation startup by 10 seconds after base bringup. That delay is not proof that every sensor is ready. Inspect the actual launch arguments with `--show-args`, then inspect lifecycle state, transforms and timestamp freshness before sending a goal. The course discusses both DWA-style velocity sampling and TEB trajectory optimization; choose only a planner present in the installed image. Do not infer that a ROS 1 planner plugin is a ROS 2 binary merely from a conceptual description.

For multiple goals, **Start Nav Through Poses** and **Start Waypoint Following** have different pose/waypoint semantics in the illustrated RViz panel. Test one goal first, then a short route with space for recovery maneuvers. Cancel a goal before transferring command ownership. A correctly drawn global path can still fail at a narrow door if the local footprint omits the Pro's arm/display. [Navigation lessons and launch analysis](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/5_Mapping_&_Navigation_Course.html#_5-2-navigation-tutorial).

### RGB-D SLAM and road-network routing <a href="#rosorin-reference-rtab-road" id="rosorin-reference-rtab-road"></a>

RTAB-Map uses synchronized RGB/depth, calibration, transforms and odometry. The documented pair is `slam rtabmap_slam.launch.py` and `slam rviz_rtabmap.launch.py`. It saves its database on clean shutdown; preserve that database and configuration, rather than assuming the 2D map-saver image contains all 3D information. Navigation uses `navigation rtabmap_navigation.launch.py` with `rviz_rtabmap_navigation.launch.py`. Do not run 2D AMCL and a second RGB-D localization authority over the same transform simultaneously.

The Pro route-planning course adds `large_models_examples/road_network/road_network_builder.py` to construct route data, then `large_models_examples road_network.launch.py` to execute it. `/request_waypoint` is a `std_msgs/msg/Int32` waypoint-ID request. Map coordinates, node IDs, graph connectivity and any scene-name mapping must refer to the same map revision. First inspect the graph and request one nearby verified waypoint; a valid integer alone does not establish a traversable route. Preserve the route file separately from occupancy images and RTAB databases. This course is not assumed present in every Standard image. [RGB-D mapping and route planning](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/5_Mapping_&_Navigation_Course.html).

## OpenCV perception before closed-loop control <a href="#rosorin-reference-opencv" id="rosorin-reference-opencv"></a>

### LAB thresholds, color recognition and QR codes <a href="#rosorin-reference-lab-qr" id="rosorin-reference-lab-qr"></a>

Use the actual operating illumination and camera pose. After stopping competing owners, the course starts `peripherals depth_camera.launch.py` and `python3 /home/ubuntu/software/lab_tool/main.py`. Its LAB tool represents L, A and B as 0–255 channel values. Start with a broad interval, then tighten the chromatic interval around the target and adjust brightness/background rejection. The target should be white in the binary mask and the background black. Save a named color only after trying several positions and shadows; otherwise a change in lighting can become a false motion command. Adding a color in the tool does not automatically add that name to every application's accepted-color list.

The color demonstration is `example/example/color_detect/color_detect_demo.py`. Its pipeline separates image receipt, color conversion, thresholding, morphology, contour selection and annotation. Check the mask and chosen contour before evaluating the reported center/size. A large same-colored background can win contour selection even when the intended block is visible. If a later grasp is wrong but the annotated center is right, diagnose geometry/calibration rather than changing a good color threshold.

The QR scripts are `example/example/qrcode/qrcode_creater.py` and `qrcode_detecter.py`; preserve those observed spellings. Generate a known harmless string, show the printed or displayed code to the stationary camera and compare the decoded text exactly. Contrast, quiet border, focus and angle affect decoding. A decoded QR string is data, not a shell command or permission to move. These paths are documented in both assigned ROSOrin course lanes. [Pro OpenCV course](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/6_ROS+OpenCV_Course.html), [Standard OpenCV course](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/6_ROS+OpenCV_Course.html).

### Line following and Pro AR overlays <a href="#rosorin-reference-line-ar" id="rosorin-reference-line-ar"></a>

Line following combines a color mask, regions of interest and the line-center error with a steering controller. The supplied scene uses a contrasting line without competing same-colored objects. First inspect the debug image while stationary; a controller cannot compensate for a missing mask or a line outside the ROI. The documented ROS 2 sequence is:

```bash
ros2 launch app line_following_node.launch.py debug:=true
ros2 service call /line_following/enter std_srvs/srv/Trigger '{}'
# This enables physical line following only after the motion-area checks:
ros2 service call /line_following/set_running std_srvs/srv/SetBool '{data: true}'
```

Select the line in the displayed image as the course instructs. To stop, inspect the installed `set_running` service and use its false setting where supported, then issue/verify a zero chassis command before closing the node. The source's closing example repeats `enter`; an initialization call is not independent proof of a stop.

The Pro AR exercise launches `example ar_detect.launch.py`, detects `tag36h11` AprilTags and selects an overlay through `/ar_detect/set_model` (`interfaces/srv/SetString`, illustrated value `bicycle`). Its expected result is tag ID/corners/axes and the selected virtual model in the image. The result is visual registration, not a navigation goal or measured grasp coordinate. Check CameraInfo and tag definition before interpreting pose. The assigned Standard OpenCV chapter does not contain this Pro AR lesson. [Line following and AR sections](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/6_ROS+OpenCV_Course.html).

## MediaPipe and learned perception <a href="#rosorin-reference-learning" id="rosorin-reference-learning"></a>

### What each MediaPipe experiment actually demonstrates <a href="#rosorin-reference-mediapipe" id="rosorin-reference-mediapipe"></a>

The image-only scripts below live under `~/ros2_ws/src/example/example/mediapipe_example`. Start one camera owner and one experiment at a time. A detected landmark is normally an image/model coordinate; it is not automatically a metric depth measurement. Begin by moving a prop or person while the chassis remains stopped.

| Experiment                    | Documented script or launch              | Observable result and boundary                                                                                                          |
| ----------------------------- | ---------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| Background segmentation       | `self_segmentation.py`                   | Foreground/background mask and replacement background; inspect boundary errors rather than relying on the article's hand/body wording   |
| Objectron 3D detection        | `objectron.py`                           | Oriented model box for the supported cup, shoe, chair or camera classes; not arbitrary-object metric reconstruction                     |
| Face detection                | `face_detect.py`                         | Face bounding region; no identity authentication implied                                                                                |
| Face mesh                     | `face_mesh.py`                           | Dense facial landmarks; model coordinates need calibration for robot geometry                                                           |
| Hand keypoints                | `hand.py`                                | Hand landmarks and connections; occlusion can corrupt gesture classification                                                            |
| Body keypoints                | `pose.py`                                | Body skeleton; check the full body is visible                                                                                           |
| Fingertip trajectory          | `hand_gesture.py`                        | Index-finger gesture records a trace; open-hand gesture clears it                                                                       |
| Body gesture driving          | `example body_control.launch.py`         | Left/right arm gestures turn; left/right leg gestures request forward/reverse movement; clear the floor first                           |
| Human following               | `example body_track.launch.py`           | Uses body center and depth to adjust approach/retreat; the illustrated target separation is about 3 m, not a guaranteed safety distance |
| Body/color association        | `example body_and_rgb_control.launch.py` | Hands-on-hips calibration records body/clothing appearance before gestures; similar clothing and occlusion can defeat selection         |
| Falling-posture demonstration | `example fall_down_detect.launch.py`     | Low body height triggers an alarm and forward/reverse robot motion; this is itself a moving experiment, not a medical fall detector     |

For following, the course points to `body_control/include/body_track.py` and separate distance/angular PID objects. Increasing a proportional gain does not establish a safe speed limit and can increase overshoot. Check target loss, depth validity, command saturation and stop behavior before changing gains. For every moving experiment, test a lost target while ready to stop; do not assume a detector exception publishes zero. The Standard course covers the same experiment families, but use its own image and dependency set. [Pro learning course](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/7_ROS+Machine_Learning_Course.html#_7-1-mediapipe-human-robot-interaction), [Standard learning course](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/7_ROS+Machine_Learning_Course.html).

### Dataset, training and TensorRT deployment <a href="#rosorin-reference-training" id="rosorin-reference-training"></a>

The course distinguishes supervised/unsupervised/reinforcement learning and introduces PyTorch, TensorFlow, PaddlePaddle and MXNet. Those are background comparisons, not a requirement to install all four frameworks on an 8 GB robot. The practical model path depends on the supplied CUDA, TensorRT, Python environment and model architecture.

There is a material version inconsistency in the Pro article: current headings/prose name **YOLO26**, while the actual commands still use `~/third_party/yolo/yolov11`, `yolo11n.pt`/`yolo11s.pt`, `yolov11_detect_demo.launch.py` and `example/yolov11_detect`. Treat those as the documented command lane, not proof that YOLO26 weights work in the same loader. Read the installed launch/model metadata before exporting or replacing an engine. [Exact training/inference article](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/7_ROS+Machine_Learning_Course.html#_7-3-machine-learning-application).

An auditable training workflow is:

1. Collect representative frames with `~/software/collect_picture/main.py`. Include backgrounds and hard negatives, keep lighting variations and separate training/validation scenes.
2. Annotate with `~/software/labelImg/labelImg.py`; maintain one ordered class list. Confirm that every box tightly encloses the intended object and uses the same class spelling.
3. Convert using the documented `xml2yolo.py --data ~/my_data --yaml ~/my_data/data.yaml`. Check image/label correspondence and class IDs before a long run. A later example misspells `my_data` as `my_date`; inspect the real directory rather than creating a second empty dataset.
4. Record architecture, weights, dataset YAML and training arguments. The illustrated training settings are image size 640, batch 8 and 300 epochs; they are example workload settings, not guaranteed to fit Nano memory.
5. Evaluate on held-out images before exporting. The illustrated export requests GPU 0, FP16 and input shape 480 × 640. Keep preprocessing, class order and postprocessing with the engine.
6. Rebuild a TensorRT engine for the target Jetson/TensorRT environment when compatibility requires it. An engine copied from another GPU/software release is not a portable checkpoint.
7. Test saved images, then a stationary live camera, then the downstream robot behavior. Record missed detections and latency under the actual NX/Nano load; no benchmark is asserted here.

FP32/FP16/INT8 refer to numerical representation and optimization tradeoffs; INT8 additionally requires an appropriate calibration/quantization path. The article's failed-training FAQ deletes/recreates a swapfile. First inspect memory, storage, logs and batch size; do not remove an active system swapfile as a generic repair. Preserve the factory deep-learning environment rather than applying broad unpinned `pip -U` changes.

### Autonomous-driving experiment progression <a href="#rosorin-reference-driving" id="rosorin-reference-driving"></a>

`example self_driving.launch.py` combines several tasks. Validate their observations separately before a combined route:

| Stage             | Data/decision                                             | Check before motion                                                    |
| ----------------- | --------------------------------------------------------- | ---------------------------------------------------------------------- |
| Lane keeping      | LAB mask, morphology and lane ROI determine lateral error | Correct lane center under the installed camera pose                    |
| Traffic signs     | Detector class/confidence selects an action               | Correct class list/engine and suppression of distant or spurious cards |
| Traffic lights    | Color/position logic controls stop/proceed                | Actual red/green props and exposure do not cross-trigger               |
| Turning decisions | Recognized route/sign context changes steering behavior   | Intersection geometry, turn direction and available runout             |
| Parking           | Parking marker detection triggers the programmed maneuver | Entire parking sweep, including Pro arm/display, remains clear         |
| Combined course   | State transitions link perception and motion              | Each earlier stage and its stop/recovery works independently           |

These are indoor staged demonstrations. They do not establish public-road driving, a traffic-law implementation or pedestrian safety. If lane masks work but decisions are wrong, examine class/state transitions; if perception is correct but motion is wrong, return to chassis configuration and command ownership. [Driving lessons](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/7_ROS+Machine_Learning_Course.html#_7-4-autonomous-driving).

## Pro arm control, action files and calibration <a href="#rosorin-reference-arm" id="rosorin-reference-arm"></a>

### Actuators, IDs and saved action semantics <a href="#rosorin-reference-arm-ids" id="rosorin-reference-arm-ids"></a>

This entire arm section is **Pro only**. The official course identifies HX-12H arm/pan-tilt servos and an HTS-21H gripper. The six addressed actuators are **1 pan/rotation, 2/3/4 arm joints, 5 wrist and 10 gripper**. They are not IDs 1–6. The half-duplex bus connector is GND, VIN and SIG in the manufacturer's view; use the keyed harness. The course's 115200-baud servo link differs from the 1 Mbaud RRC host link.

![Hiwonder ROSOrin Pro arm photograph identifying servo IDs 1, 2, 3, 4, 5 and gripper 10](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/assets/image8.B79yXju0.webp)

_Hiwonder official arm-ID figure, visually inspected against the listed IDs. The depicted posture is identification context, not a requested startup pose._ [_Figure source_](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/8_Robotic_Arm_Motion_Control.html#_8-2-2-adjustment-steps)_._

The arm chapter publishes a 410 mm span, an effective grasping radius up to 30 cm and a 500 g reference payload. These are chapter-level references, not a guarantee at every extension, speed, gripper or mobile pose. Its table also includes a generic 1920 × 1080/60 fps vision-camera entry, while this assigned robot identifies an Aurora depth camera. That generic entry does not replace the Aurora profiles above. The 0–1000 servo position scale represents the documented 0–240° servo range, not radians and not the ROS joint's collision-free range. [Arm hardware and ID diagrams](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/8_Robotic_Arm_Motion_Control.html#_8-1-basic-robotic-arm-control).

The desktop arm tool can be started from its icon or from `~/software/arm_pc` with `python3 main.py`. Stop the app owner first. The editor stores timed position rows in `.d6a` action groups under `~/software/arm_pc/ActionGroups`; some prose omits `/home/` in that path, so confirm the installed directory. Read the current pose/deviations before edits. Select and run one row before running the full sequence; keep Loop off during commissioning. Joining files concatenates their rows, so inspect the transition from the last pose of the first file to the first pose of the next. Export/import preserves a file, not its calibration or mechanical suitability for another arm.

Manual/unload mode relaxes joints for pose design; support the arm before releasing torque. Reset-to-500 is a commanded movement, not a read-only initialization. The course illustrates 2000 ms approach/lift rows and shorter transition/grip rows; design durations for the actual path and load instead of copying the example's joint values. Keep action names without spaces as required by the tool, save a new file and retain the original factory group.

### Deviation, neutral geometry and gripper travel <a href="#rosorin-reference-arm-calibration" id="rosorin-reference-arm-calibration"></a>

Factory deviations should remain unchanged on a correctly aligned new robot. If a measured error warrants adjustment, back up the current values, stop other serial owners, read deviations and compare against the manufacturer's neutral-position figure. IDs 1–5 should meet the indicated vertical alignment; the gripper's center reference is a 2–3 cm opening. Adjust the **deviation** slider, not an unrelated live-position slider, then download/save that deviation and recheck the neutral pose. The illustrated correction from −18 to 2 is one servo's example, not a reusable offset.

The UI deviation range is −125 to +125. The course recommends a gripper working position range of 200–700; do not force its mechanical stops to reach the full generic 0–1000 range. A freeze while reading deviations commonly indicates two programs contending for the serial connection. Diagnose ownership before repeatedly rebooting or writing offsets. [Deviation procedure and FAQ](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/8_Robotic_Arm_Motion_Control.html#_8-2-robotic-arm-deviation-adjustment).

### IK requests are not joint commands <a href="#rosorin-reference-ik-api" id="rosorin-reference-ik-api"></a>

The pinned Pro source exposes the following services under the `kinematics` node. Its mathematical solver libraries are supplied as `.so` files in the observed tree; do not describe an unread binary as reviewed solver source.

| Service / type                                          | Request and response meaning                                                                                                                                                  |
| ------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `~/set_pose_target`, `kinematics_msgs/srv/SetRobotPose` | Request: `position` in meters, `pitch`/`pitch_range` in degrees, search `resolution` in degrees. Response: `success`, target `pulse`, `current_pulse`, `rpy`, `min_variation` |
| `~/set_joint_value_target`, `SetJointValue`             | Five joint position values in the documented pulse/controller scale; returns FK pose plus success/solution flags                                                              |
| `~/get_current_pose`, `GetRobotPose`                    | Returns current pose with success/solution flags                                                                                                                              |
| `~/get_link` / `~/set_link`                             | Read/change link geometry; changing it affects all subsequent solutions                                                                                                       |
| `~/get_joint_range` / `~/set_joint_range`               | Read/change solver joint limits; not a substitute for physical limits/collision checking                                                                                      |

The helper `set_pose_target()` constructs a request; it does not itself send that request or move the robot. A successful IK service result still needs range, collision and path checks before a separate servo command. Two similarly named `ServosPosition` messages are distinct: the lower `ros_robot_controller_msgs` message contains duration and position entries, while `servo_controller_msgs` additionally contains `position_unit`. Inspect the actual subscriber type and the unit string accepted by that installed controller. Do not reinterpret degrees, radians, servo units or milliseconds/seconds by name alone. [Pinned request helper](https://raw.githubusercontent.com/Hiwonder/ROSOrin-Pro/6c2a621fe628cc4928c48fc11d8d982594d471eb/ROS2/src_ros2/src/driver/kinematics/kinematics/kinematics_control.py), [service definitions](https://github.com/Hiwonder/ROSOrin-Pro/tree/6c2a621fe628cc4928c48fc11d8d982594d471eb/ROS2/src_ros2/src/driver/kinematics_msgs/srv).

The practical interface addresses five pose joints plus the separate gripper. Although the product/course calls the assembly “6DOF”, that label does not establish six independently controllable Cartesian pose coordinates. Plan within the actual solver's position/pitch and joint constraints rather than treating this as a generic six-revolute-joint industrial arm.

## Pro 2D and 3D manipulation experiments <a href="#rosorin-reference-manipulation" id="rosorin-reference-manipulation"></a>

### A staged perception-to-grasp procedure <a href="#rosorin-reference-grasp-stages" id="rosorin-reference-grasp-stages"></a>

First establish the action tool, camera stream, color/detector output and current arm pose independently. Fix the table height, lighting, camera mount and target size. Back up ROI/hand-eye/offset files before calibration. For a first grasp, use a light supplied block at a reachable position, with the base stationary and no navigation owner. Validate these stages in order: detected object → valid depth or calibrated table-plane position → camera-frame point → arm-frame point → IK solution → collision-free approach → gripper closure → lift → place. A classification label or an IK solution alone is not proof of a safe pick.

**A debug launch can already move the arm.** The sorting debug initialization runs `pick_debug` and `pick_init` action groups. Clear the arm sweep before launching it; `debug:=true` is not an actuator-disable switch.

| Pro 2D lesson                        | Exact launch in package `example`                                                                         | Technical checkpoint                                                                                                                         |
| ------------------------------------ | --------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Hand following                       | `hand_track_node.launch.py`                                                                               | MediaPipe hand location changes the arm aim; detection loss must not leave an uncontrolled continuing action                                 |
| Color sorting                        | `color_sorting_node.launch.py debug:=true`                                                                | Inspect the selected contour/ROI and table calibration before enabling the grasp/place sequence; ROI file is `config/color_sorting_roi.yaml` |
| Color tracking                       | `color_track_node.launch.py`                                                                              | Image-center error feeds tracking/IK; a tracking overlay and a physical reachable target are separate checks                                 |
| Line following with obstacle removal | `line_follow_clean_node.launch.py`, debug option available                                                | Line/colored-object ROI plus LiDAR determine base behavior and the action group that clears a block; inspect `line_follow_clean_roi.yaml`    |
| Waste-card sorting                   | `garbage_classification.launch.py debug:=true`                                                            | Detector class maps to a waste group/action; validate the class mapping and `garbage_classification_roi.yaml` before grasping                |
| Fixed-point transport                | `navigation_transport.launch.py map:=map_01`; `automatic_pick.launch.py debug:=true` for pick calibration | Requires a saved matching map, verified navigation pose and separate pick/place calibration                                                  |

The current waste chapter names YOLO26 while adjacent training commands use YOLO11 artifacts. Check the installed detector/class list; do not assume either name establishes engine compatibility. Printed waste cards are demonstration labels. Their categories are not a general waste-handling policy or permission to pick hazardous objects. [Pro 2D vision course](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/8_Robotic_Arm_Motion_Control.html#_8-3-2d-vision).

### Fixed-point transport: calibrate pickup and verify placement separately <a href="#rosorin-reference-transport-calibration" id="rosorin-reference-transport-calibration"></a>

This Pro lesson combines a previously saved map, navigation, color alignment and arm actions. Finish the individual navigation and grasp checkpoints before combining them. **`debug:=true` moves the arm during initialization**: the pinned NX program runs `navigation_pick_debug`, waits, then runs `navigation_pick_init`. Clear the complete arm/gripper sweep, keep one command owner and a physical stop, and use a fixture rather than reaching into an automatically moving gripper. If positioning the block requires entering the sweep, stop and isolate power before adjusting it. [Course calibration steps](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/8_Robotic_Arm_Motion_Control.html#_8-3-6-fixed-point-navigation-and-transport).

1. Stop the app service and competing moving behaviors as described above. Confirm the intended camera and saved LAB color thresholds with the stationary block. Before calibration, preserve the current ROS 2 YAML and inspect the package lane:

```bash
ros2 pkg prefix example
printenv need_compile
cp -p /home/ubuntu/ros2_ws/src/example/config/automatic_pick_roi.yaml "/home/ubuntu/ros2_ws/src/example/config/automatic_pick_roi.yaml.before-$(date +%Y%m%d-%H%M%S)"
```

2. The **pinned `orin-nx` implementation** writes `/home/ubuntu/ros2_ws/src/example/config/automatic_pick_roi.yaml`. The article's `/home/ros_ws/src/hiwonder_example/config/automatic_pick_rol.yaml` is an obsolete/mismatched path and filename; do not create that path to satisfy the prose. The launch reads either the installed `example` package share (`need_compile=True`) or the source package (`False`). Check which YAML the active overlay actually loads: a successful source-file write does not automatically update a copied installed YAML. [Actual NX write path and debug logic](https://raw.githubusercontent.com/Hiwonder/ROSOrin-Pro/6c2a621fe628cc4928c48fc11d8d982594d471eb/ROS2/src_ros2/src/example/example/navigation_transport/automatic_pick.py), [launch parameter source](https://raw.githubusercontent.com/Hiwonder/ROSOrin-Pro/6c2a621fe628cc4928c48fc11d8d982594d471eb/ROS2/src_ros2/src/example/example/navigation_transport/automatic_pick.launch.py).
3. With the chassis and arm area clear, run the calibration once:

```bash
ros2 launch example automatic_pick.launch.py debug:=true
```

4. The lesson acquires the colored block centered at the demonstrated gripper pickup pose, then resets/repositions the arm. Watch the image and terminal `x_y` coordinates from outside the motion area. The manual describes a completion indication; the pinned code's actual save condition is its debug-frame counter exceeding ten, after which it writes the pickup coordinate and clears debug. It does **not** establish ten independently validated successful block detections. A log line alone is therefore insufficient: confirm that the recorded center belongs to the visible target, not a failed/no-target result.
5. Stop the calibration behavior and verify physical rest before inspecting or adjusting the target. Read the saved arrays without changing them:

```bash
python3 - <<'CHECK_ROI'
from pathlib import Path
import yaml
path = Path('/home/ubuntu/ros2_ws/src/example/config/automatic_pick_roi.yaml')
parameters = yaml.safe_load(path.read_text())['/**']['ros__parameters']
for key in ('pick_stop_pixel_coordinate', 'place_stop_pixel_coordinate'):
    value = parameters[key]
    if not isinstance(value, list) or len(value) != 2:
        raise SystemExit('Expected an [x, y] pair for ' + key)
    print(key, value)
CHECK_ROI
```

The automatic procedure saves **only `pick_stop_pixel_coordinate`**, under `/**/ros__parameters`. `place_stop_pixel_coordinate` is a separate array used by the placement alignment path. Do not replace both with the newly acquired pickup center or treat the repository's example pixels as a universal camera calibration. The source interprets the first value as image x and the second as image y; the manual's left/right and closer/farther adjustment descriptions apply to its illustrated camera mounting. Verify the direction with the actual image before a small manual change. [Exact two-key YAML](https://raw.githubusercontent.com/Hiwonder/ROSOrin-Pro/6c2a621fe628cc4928c48fc11d8d982594d471eb/ROS2/src_ros2/src/example/config/automatic_pick_roi.yaml).

6. If the launch consumes an installed copy, rebuild/install through that workspace's normal package procedure, source the resulting overlay and restart the behavior so it loads the reviewed values. Compare active parameters using the observed node name/namespace from `ros2 node list`; do not assume another running node or an old terminal has reloaded the file. Keep the backup until a complete controlled pickup/placement cycle succeeds.
7. Start the combined task with the already verified map. The default **`place_without_color:=true`** places at the preset navigation destination without requiring a detected placement-color marker. For color-guided placement, deliberately select **false** and provide the source's red placement target:

```bash
ros2 launch example navigation_transport.launch.py map:=map_01 place_without_color:=false
```

Only use `map_01` if it is the intended saved map. Confirm localization with **2D Pose Estimate** before requesting a destination; do not tune pickup pixels to compensate for a wrong map pose. First verify approach/pickup, then the separate placement alignment and release. If color-guided placement is inaccurate, adjust **placement** coordinates with a clear stage and a backed-up file; rerunning pickup debug does not calibrate placement. The article describes one pick/place cycle per feature launch, so inspect completion before deliberately restarting for another cycle.

**Expected result:** the source YAML contains a verified pickup `[x,y]`, the placement pair remains separately controlled, the active launch reads the intended file, and placement follows the selected color/no-color mode. Missing target pixels, a stale installed YAML, wrong localization or an absent red marker in color-guided mode are different failure causes. No calibration, motion or transport cycle was run here. [Pickup-only persistence and transport behavior](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/8_Robotic_Arm_Motion_Control.html#_8-3-6-fixed-point-navigation-and-transport).

### Depth-plane calibration, object tracking and classification <a href="#rosorin-reference-depth-applications" id="rosorin-reference-depth-applications"></a>

| Pro 3D lesson                 | Launch in `example`                     | Calibration/data dependency                                                                           |
| ----------------------------- | --------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Fall-prevention demonstration | `prevent_falling.launch.py debug:=true` | Ground reference in `plane_distance.yaml`; recalibrate after changing placement/camera geometry       |
| Narrow-bridge demonstration   | `cross_bridge.launch.py debug:=true`    | Scene reference in `bridge_plane_distance.yaml`; inspect the debug measurement before enabling travel |
| Object following              | `track_object.launch.py`                | Point-cloud/depth target and PID determine base motion; require valid depth and target-loss stop      |
| Tracking and grasping         | `track_and_grab.launch.py`              | RGB target plus depth, hand-eye transform, current endpoint and IK                                    |
| Shape/color classification    | `object_classification.launch.py`       | Depth/geometry filtering, classification, offset correction and a corresponding pick/place path       |

These first two are demonstrations of depth-dependent decisions, not independent protective systems. Start on a level test surface with no real drop. A missing/reflective depth patch can resemble an edge, and a stale plane reference can make a safe surface look wrong or vice versa. Do not validate them by deliberately driving toward an unguarded fall.

The source's 3D grasping transform includes translation components **−0.101, +0.011 and +0.045 m** within a full rotation/translation matrix; a classification example additionally subtracts 0.01 m from a camera coordinate and applies directional pick offsets. These numbers describe that example's mounted geometry. Preserve the matrix order and measure the actual assembly rather than copying only its translation. The code converts its depth sample with `/1000` before the pinhole calculation; validate that this matches the installed depth units. A mounted camera, arm endpoint and world/arm frame must be evaluated at the same robot pose. [Pro 3D algorithms and calibration files](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/8_Robotic_Arm_Motion_Control.html#_8-4-3d-vision).

## Simulation, MoveIt 2 and physical synchronization <a href="#rosorin-reference-simulation" id="rosorin-reference-simulation"></a>

The workstation VM is separate from the **assigned Pro Ultimate / Orin NX Super 16GB robot**. Its image, simulation packages and ROS environment are not an NX SSD recovery image. The Standard Nano Super course is chassis/Gazebo focused; it does not establish an arm or MoveIt installation on the assigned Standard kit. Use the supplied workstation resources for this chapter and keep robot-specific controller binaries in their own host lane. [Pro simulation course](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html), [Standard Gazebo course](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/9_Gazebo_Simulation.html).

### Prepare the VM, workspace overlay and domain <a href="#rosorin-reference-simulation-setup" id="rosorin-reference-simulation-setup"></a>

1. Obtain the manufacturer's **Resources/1 Virtual Machine Software**, **Resources/2 Virtual Machine Image** and **Resources/3 Package Files** listed in the course. Install the compatible workstation software under its applicable license, use **Open a Virtual Machine**, select the supplied VM file and choose an import location with enough free space. These externally hosted archives have not been opened or executed for this guide; inspect their actual filenames/content before following the package steps below.
2. In the imported VM's settings, choose **Network Adapter → Bridged** for the course's later two-computer workflow. Its display instructions uncheck **Accelerate 3D graphics**. Those are this VM's source settings, not a claim that every hypervisor/GPU behaves identically. For the initial simulation-only exercises, keep the **physical robot powered off**, disconnect the VM's virtual network adapter and leave the physical-controller/servo bridges stopped. Matching a robot's domain later must be a deliberate transition.
3. Inside the VM, open a terminal and inspect `cat /etc/os-release`, `uname -m` and `printenv ROS_DISTRO ROS_VERSION`. Use the supplied VM's ROS 2 environment; do not replace it with an AArch64 robot overlay or assume that an unrelated ROS release has the same Gazebo plugins. Copy the course's `simulations.zip` and `.typerc` to the VM home directory. Inspect the archive before extraction:

```bash
unzip -l ~/simulations.zip
mkdir -p ~/ros2_ws/src
ls -ld ~/ros2_ws/src/simulations ~/ros2_ws/.typerc
```

If either destination already exists, preserve it before continuing; the `ls` errors on absent paths are expected on a fresh VM. The article expects a top-level `simulations` directory, but the individual downloaded archive was not inspected here. If its listing differs, resolve that package layout rather than nesting another workspace blindly. On a fresh destination, extract/build the supplied packages:

```bash
test ! -e ~/ros2_ws/src/simulations && unzip ~/simulations.zip -d ~/ros2_ws/src
cp -n ~/.typerc ~/ros2_ws/.typerc
cd ~/ros2_ws
colcon list
colcon build --symlink-install
source ~/ros2_ws/install/setup.bash
source ~/ros2_ws/.typerc
ros2 pkg prefix hiwonder_moveit_config
ros2 pkg prefix robot_gazebo
printenv ROS_DISTRO ROS_DOMAIN_ID
```

4. Stop if extraction or compilation fails. `colcon list` should identify the imported packages, and the two prefix queries should resolve this VM's workspace rather than an unrelated installation. A populated source directory alone is not a built overlay. The `cp -n` keeps an existing workspace `.typerc`; compare it with the supplied file rather than silently overwriting either configuration.
5. After successful loading, inspect `~/.bashrc`. If the following two source lines are absent, add them **once**, in this order: `source ~/ros2_ws/install/setup.bash`, then `source ~/ros2_ws/.typerc`. Open a new terminal and repeat the prefix/environment checks. Repeatedly appending the lines can cause confusing overlay precedence; editing a source file does not change an already-running node's environment.
6. For a later networked session, first restore the VM adapter and connect the robot and VM host to the intended router/LAN. The course prefers a common wired router or STA LAN over the robot AP route. Read actual addresses with `ip -brief address` on each computer; `192.168.11.x` in the course is an example subnet. Read the robot's actual `ROS_DOMAIN_ID`, open `gedit ~/ros2_ws/.typerc` **on the VM**, and set its existing domain assignment to that same value. The lesson's **10** is an example, not a required device identity. Save, open fresh terminals on both sides and compare `printenv ROS_DOMAIN_ID` before starting any joint session. Equal domains do not repair different subnets, blocked DDS discovery or a stale sourced overlay.

**Expected result:** a fresh VM terminal resolves the intended simulation packages and deliberate domain setting. Simulation-only planning remains isolated from powered hardware. For networked use, equal domains and reachable addresses are prerequisites; verify the actual graph and command recipients before enabling a bridge. Neither a successful VM import nor a package-prefix result proves physical synchronization. [VM settings and package/build procedure](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html#_9-2-configuration).

### Inspect and back up the existing MoveIt configuration <a href="#rosorin-reference-moveit-configuration" id="rosorin-reference-moveit-configuration"></a>

The course says the factory configuration is already supplied and normally needs no regeneration. Before experimenting:

1. In the sourced VM workspace, run `colcon list` and locate the **source path** for `hiwonder_moveit_config`. The course illustrates `/home/ubuntu/ros2_ws/src/hiwonder_moveit_config`; an imported package tree may put it below `simulations`. Select the path actually listed, not an installed `share` copy from a different overlay.
2. Using the VM file manager, copy the **entire package directory outside `~/ros2_ws/src`**, for example into a dated backup directory under the home directory. Keep the original package name inside that backup and record the active package prefix. A duplicate package left inside the source workspace can itself break a subsequent build. Retain referenced URDF/Xacro/meshes if they live in a separate description package.
3. Launch the assistant from the same sourced environment:

```bash
ros2 launch moveit_setup_assistant setup_assistant.launch.py
```

4. Select **Edit Existing MoveIt Configuration Package → Browse**, choose the observed source directory, then **Load Files**. Wait for loading to reach 100% and for the expected robot/arm model to appear. Failure to load is a package/path/description checkpoint; do not create a new generic arm to bypass it.
5. Inspect the **Self-Collisions** matrix, **Virtual Joints**, **Planning Groups**, **Robot Poses**, **Passive Joints**, **ROS 2 Controllers** and **ros2\_control URDF Modifications**. The course's virtual connection is `base_footprint` to `world_frame`; retain its intended frame relationship. Its self-collision sampling default is **10,000** configurations. Disabled pairs need a geometric justification: the matrix is not a way to suppress an arm–camera collision. Preserve the `arm` group, named `home`/`p1` states and controller/joint correspondence unless a specific model change requires revision.
6. For inspection only, close without generating files. For a deliberate edit, first verify **Configuration Files**' destination, then use **Generate Package** and review the differences against the backup. Rebuild the affected workspace and source its install setup in a new terminal before testing; a running RViz session does not automatically consume regenerated source files. Restore the backed-up configuration and rebuild if the model/group/controllers no longer match.

**Expected result:** the existing model and planning group load without changing factory files during inspection. After an intentional change, the selected source package, generated files and resolved overlay all agree. Generation is an overwrite operation, not a reversible preview inside the assistant. [Exact existing-package and backup workflow](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html#_9-4-2-moveit2-configuration).

### Pro target and random-valid planning exercises <a href="#rosorin-reference-moveit" id="rosorin-reference-moveit"></a>

Keep the robot powered off and physical bridges absent for these exercises. Start the source-supported interface on the isolated VM:

```bash
ros2 launch hiwonder_moveit_config demo.launch.py
```

1. In RViz, open **MotionPlanning → Planning** and choose planning group **arm**. Use **current** for the starting state. Confirm that the displayed model contains the base, camera and gripper collision geometry before choosing a target.
2. Move the end-effector interactive marker a small, reachable distance, or open **Joints** and adjust one joint slider. Read the displayed reference frame and axis labels. The manufacturer's screenshot uses green for its x/left direction, red for y/forward and blue for z/up; color alone is not a portable frame definition. A goal marker is a requested state, not measured hardware feedback.
3. Inspect the goal: the course displays a valid goal in orange and a colliding goal in red. Move a red target away from the camera/base rather than disabling collision pairs. Return to **Planning** and choose **Plan**; inspect the preview before any **Execute** operation.
4. To reproduce the random lesson, open **Goal State** and select **random valid**. It chooses a collision-valid goal rather than unrestricted **random**. Other choices have distinct meanings: **current** keeps the current pose, **same as start** removes the move, **previous** restores the previous goal, and **home**/**p1** are configured named states. Click **Plan** again and inspect the entire route. A valid endpoint does not by itself establish that a route has been found.
5. Only in the verified isolated simulation may **Execute** send the inspected result to its simulation controller. Keep **Plan & Execute** unused during this first inspection exercise because it combines the two decisions. If execution has no simulation controller, investigate that interface rather than starting a physical bridge to make the button work.

**Expected result:** the requested target changes while the start state remains understood, and planning either produces an inspectable trajectory or a clear failure. No fixed random pose or planning-success guarantee is implied. After simulation execution, the model should reach the planned goal under the configured simulation controller; a preview animation alone is not controller execution. [Target control](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html#_9-4-3-moveit2-control), [random/named choices](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html#_9-4-4-moveit2-random-motion).

### Cartesian motion and incomplete-path diagnosis <a href="#rosorin-reference-moveit-cartesian" id="rosorin-reference-moveit-cartesian"></a>

1. Begin from the known, collision-valid simulated state above. In **Planning**, enable **Use Cartesian Path** and retain the `arm` group.
2. Translate the end-effector marker by a small amount within its reachable workspace, initially preserving orientation. The task now asks for a straight end-effector displacement; ordinary joint-space planning can take a curved tool route between the same endpoints.
3. Select **Plan** and inspect the end-effector route, start state and reported planning result. If the path fails or is only partial, reduce the displacement, move away from a joint limit/singular pose and recheck collision geometry. Do not interpret reaching a partial endpoint as completing the requested Cartesian move.
4. In the isolated simulation, execute only a complete accepted route. Clear **Use Cartesian Path** before comparing an ordinary joint-space plan to the same target, keeping the changed planning mode in the record.

**Expected result:** a feasible Cartesian request produces the requested straight tool route under that model's constraints, or the interface reports failure. The lesson does not supply a numeric success fraction or universal reachable XYZ target, so this reference does not invent one. A path drawn through missing collision geometry remains an invalid environment model. [Cartesian control and failure behavior](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html#_9-4-5-moveit2-cartesian-path-planning).

### Publish scene objects and test collision-aware planning <a href="#rosorin-reference-moveit-scene" id="rosorin-reference-moveit-scene"></a>

1. Choose a reachable goal with a clear start state, then open **Scene Objects**. Select **Box**, enter its dimensions in **metres**, and press **+**. The course initially creates the object near the robot center; move it before using it as a test obstacle. A **Sphere** and its scale slider provide the alternate collision lesson.
2. Use **Position**, **Rotation** and **Scale** or the object's interactive controls to place a modest obstacle between start and goal without intersecting the initial robot state. Check the planning frame and camera/base clearance; do not equate a marker in the display with an object accepted by the planner.
3. Select **Publish** after editing. This is the course's explicit scene-design step that submits the object to the planning scene; merely showing a box is insufficient. Confirm the object remains in the scene and that its final pose/size are the intended ones.
4. Return to **Planning**, enable **Collision-aware IK**, then choose **Plan**. Inspect every link along the preview, including the gripper/camera and any carried-object model. A detour is one valid outcome; a planning failure is also reasonable when the box blocks all feasible motion. Do not promise that the planner must find the illustrated detour.
5. Move/resize the object, **Publish** again and replan. Compare the two results. If the trajectory appears unchanged through an intersecting box, check publication, active scene/frame, collision geometry and allowed-collision entries before adjusting a planner. To remove the test obstruction, remove it in the scene editor and publish the updated scene before replanning.

**Expected result:** the published object affects collision checking: the accepted route avoids the object or planning fails. An orange endpoint, a displayed but unpublished object, or **Collision-aware IK** alone does not certify the complete path. The allowed-collision matrix's permitted pairs bypass those checks; inspect it rather than assuming every pair is checked. [Primitive/collision exercise](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html#_9-4-6-moveit2-collision-detection), [scene editing and Publish](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html#_9-4-7-moveit2-scene-design).

### Inspect the trajectory trail before simulation execution <a href="#rosorin-reference-moveit-trail" id="rosorin-reference-moveit-trail"></a>

1. With the selected start, goal and published scene still active, expand **Displays → MotionPlanning → Planned Path** and enable **Show Trail**.
2. Use **Plan** in the Planning tab. Inspect the intermediate arm poses as well as the endpoints. If the start state, object pose or goal changes after planning, discard that plan and generate a fresh one.
3. After accepting the route, uncheck **Show Trail** for a clear execution view and use **Execute** only with the isolated simulation controller. Compare the final model state with the goal; a trail is a visualization of a computed path, not a record of an actual arm run.
4. Stop the application with Ctrl+C in its terminal after the simulated motion finishes. If the interface is unresponsive, inspect its process/controller state; do not treat closing RViz as an emergency physical stop.

The course describes OMPL as the default and also names CHOMP in the supplied software. Its discussion of Pilz, STOMP and SBPL is background, not proof that those plugins are installed/configured in this package. Keep the actual planner selection, start/goal/scene and result with any comparison. **Expected result:** intermediate states can be inspected before a separate simulated execution; a rejected or failed plan is not executed. [Show Trail → Plan → Execute sequence](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html#_9-4-8-moveit2-trajectory-planning).

### Physical synchronization is a separate commissioning stage <a href="#rosorin-reference-moveit-synchronization" id="rosorin-reference-moveit-synchronization"></a>

The source's hardware lane stops `start_app_node.service` **on the robot**, starts `ros_robot_controller ros_robot_controller.launch.py` there, then starts `servo_controller servo_controller.launch.py` **on the VM** and launches MoveIt. These services can connect the planning interface to real servos; they are deliberately absent from the simulation-only procedures above. The article warns that the real arm can lag the displayed model. A faster animation is not proof that hardware reached a waypoint.

Before that separately commissioned stage, verify the matched subnet/domain/overlay, IDs **1/2/3/4/5/10**, stored neutral deviations, position units, current-state feedback, collision geometry and single command owner. Clear the entire arm/gripper/antenna sweep and establish a physical stop. Begin with a deliberately small reviewed target rather than random execution. A software collision model does not measure servo torque, payload stability or an obstacle missing from the scene. No physical synchronization, simulator launch, workspace build or model accuracy test was run for this reference. [Source host roles and synchronization prerequisites](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/9_MoveIt_and_Gazebo_Simulation.html#_9-4-9-synchronized-simulation-and-physical-arm-control).

### Gazebo worlds, SLAM and Nav2 <a href="#rosorin-reference-gazebo" id="rosorin-reference-gazebo"></a>

The course uses `robot_gazebo worlds.launch.py` for the model/world and `room_worlds.launch.py` for a room. Mapping uses `robot_gazebo slam.launch.py` and `ros2 run robot_gazebo teleop_key_control`; save the simulation map in `robot_gazebo/maps`, keeping it distinct from a real-room map. Navigation uses `room_worlds.launch.py nav:=true` with `robot_gazebo navigation.launch.py map:=map_01`. Check `/clock` and use simulation time consistently throughout the simulated graph.

For combined Pro Gazebo/MoveIt simulation, the documented options are `worlds.launch.py moveit_unite:=true` and `hiwonder_moveit_config demo.launch.py use_sim_time:=true use_gazebo:=true`. Confirm that simulation controllers, rather than physical serial drivers, are the command recipients. A valid simulated path verifies the model/controller configuration under that simulation; it does not measure physical traction, servo load, depth accuracy or communication reliability.

## Voice hardware, offline resources and robot actions <a href="#rosorin-reference-voice" id="rosorin-reference-voice"></a>

### Assigned WonderEcho Pro and the optional six-microphone lane <a href="#rosorin-reference-audio" id="rosorin-reference-audio"></a>

The two assigned configurations identify **WonderEcho Pro**. The Pro course specifies a USB 2.0 CI1302 voice device, 5 V supply and speaker drive reference 3 W/channel at 4 Ω. Test audio without robot actions first: `arecord -l` identifies the capture device; then select the actual card/device rather than assuming the example's `hw:0,0` is permanent. The example format is signed 16-bit little-endian, 16 kHz and two channels. Record a short sample and play it back, checking both capture and output routing. Audio enumeration is not successful wake-word recognition. [Pro voice hardware and audio tests](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/10_Voice_Control_Course.html#_10-1-wonderecho-pro-overview).

The Standard course also documents an optional six-microphone array. That is a separate hardware/licensing lane, not the assigned WonderEcho. Its offline resources include an application-specific `common.jet` and APPID, with the course naming `xf_mic_asr_offline/config/msc/res/asr` and `mic_init.launch.py`. Back up the matched resource/ID pair before replacing it. Availability of public instructions does not supply a valid licensed speech resource or an account ID. Do not install an x86 VM library in the AArch64 robot or use broad world-writable permission changes from a workbench example as a repair. [Standard voice-resource procedure](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/8_Voice_Control_Course.html).

Changing a WonderEcho wake word can require matching module firmware as well as desktop language selection. The source names CI1302 and an example file `CI1302-English-SingleMic_V00916_UART0_115200_2M.bin`, with PACK\_UPDATE\_TOOL and module RST entry into flashing mode. That is a **voice-module** operation, separate from STM32 or SSD recovery. Verify the physical module, exact firmware and USB serial port first; do not flash merely because a speaker is silent. The module binary/tool archives are externally hosted resources, not binaries validated by this guide.

### Voice-controlled feature families <a href="#rosorin-reference-voice-actions" id="rosorin-reference-voice-actions"></a>

All launches below belong to `xf_mic_asr_offline`. Wait for recognition initialization, test a harmless recognition/output response, then allow one action family with a clear scene and stop path.

| Course function                        | Launch                                                       | Prerequisites/result                                                                       |
| -------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------------ |
| Chassis movement, both assigned robots | `voice_control_move.launch.py`                               | Recognized forward/back/left/right command selects base motion; confirm direction and stop |
| Pro arm                                | `voice_control_arm.launch.py`                                | Verified arm IDs/action groups and clear reset sweep                                       |
| Color recognition                      | `voice_control_color_detect.launch.py`                       | Saved LAB thresholds; compare spoken result with a stationary colored prop                 |
| Pro color tracking                     | `voice_control_color_track.launch.py`                        | Valid tracking target and safe arm/base envelope                                           |
| Pro color sorting                      | `voice_control_color_sorting.launch.py debug:=true`          | Same color ROI/grasp calibration as the non-voice sorting lesson                           |
| Pro waste sorting                      | `voice_control_garbage_classification.launch.py debug:=true` | Correct detector class mapping and pick/place calibration                                  |
| Named-point navigation                 | `voice_control_navigation.launch.py map:=map_01`             | Matching saved map, initialized pose and verified A/B/C/origin coordinates                 |
| Pro navigation/transport               | `voice_control_navigation_transport.launch.py map:=map_01`   | Each waypoint and each stationary pick/place already tested separately                     |

The Standard voice chapter covers movement, color recognition and named-point navigation; Pro-only launches are not assumed installed there. Wake-word language, microphone selection, offline grammar/resource and action-node state are different diagnostic layers. A recognized phrase is not evidence that the map or target coordinates are correct. Reject an ambiguous command instead of repeatedly moving until the spoken result appears. [Pro voice functions](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/10_Voice_Control_Course.html#_10-2-voice-control-features).

## Multi-robot network and group control <a href="#rosorin-reference-group" id="rosorin-reference-group"></a>

The group-control course uses one leader and followers. Configure a unique name/namespace for every robot and a common reachable network. In its example, the leader's hotspot is `HW-123`, the follower selects LAN mode 2 and joins that hotspot; these are example values to replace consistently. The source edits `wifi_manager/wifi_conf.py` and requires a reboot after network changes. A follower that cannot find the configured network may fall back to AP mode after three search attempts without rewriting its saved LAN configuration; it can therefore repeat the failure on the next boot.

The ROS environment file is `~/ros2_ws/.typerc`, with example leader `robot_1` and follower `robot_2`; inspect HOST/MASTER and the sourced shell configuration on both machines. Compare clocks before starting the controllers. The course's `date -s` value is an old example timestamp, not a time to copy. Synchronize to the actual current reference and verify the measured difference. Matching clocks do not fix duplicate namespaces or blocked discovery traffic.

The leader runs `multi multi_controller.launch.py`, the course's `ros2_ws/src/multi/launch/joystick_control_multi.py` and `joy joy_node`. Followers run `multi multi_controller.launch.py`. Stop factory app owners on **every** robot first, prove each individual stop, then start the group with large separation. START is the illustrated stop/reset control. Lateral joystick motion applies to Mecanum; a source table's “differential” wording does not give a two-wheel chassis lateral mobility. **Expected result:** commands reach the intended named robots with consistent direction and stopping, without unintended cross-control. [Pro group course](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/11_Group_Control.html), [Standard group course](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/11_Group_Control.html).

## Large-model foundations and staged integration <a href="#rosorin-reference-large-models" id="rosorin-reference-large-models"></a>

### Text, speech, vision and multimodal checkpoints <a href="#rosorin-reference-model-basics" id="rosorin-reference-model-basics"></a>

The courses distinguish text completion/structured interpretation, speech recognition/synthesis, image understanding/detection/OCR and multimodal interaction. Begin with the supplied `~/large_models` demos while robot action nodes are stopped. The documented scripts include `openai_llm_demo.py`, `openai_llm_nlu_demo.py`, `openai_llm_er_demo.py`, `wakeup_demo.py`, `openai_asr_demo.py`, `openai_tts_demo.py`, `openai_vllm_understand.py`, `openai_vllm_ocr.py` and `openai_agent_demo.py`. The conversation filename is spelled `openai_interaciton_demo.py` in the course; inspect the installed file before invoking it.

Check each layer independently: microphone yields intelligible audio, ASR yields the intended text, model output parses into the expected structure, TTS yields audible output, and image interpretation refers to the actual captured scene. A fluent answer or emotion label is not proof of perception accuracy or motion feasibility. Cloud tests need internet access, an available provider/model and the matching account entitlement. Do not print private keys into logs or copy them into action files.

The robot integration course places provider configuration at `~/ros2_ws/src/large_models/large_models/large_models/config.py`; standalone demo configuration may be elsewhere in the delivered package. Configure the actual selected provider/backend and microphone/ASR mode. The course includes broad `pip` installation/upgrade commands; preserve the factory image's CUDA/Python dependencies and inspect its requirements instead of replacing them blindly. [Pro large-model foundations and configuration](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/12_Large_AI_Model_Courses.html), [Standard large-model course](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/10_Large_AI_Model_Courses.html).

### ROS action families and map coordinates <a href="#rosorin-reference-model-actions" id="rosorin-reference-model-actions"></a>

| Function family                  | Package `large_models_examples` launch                            | Development boundary                                                                            |
| -------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| Voice-to-motion                  | `llm_control_move.launch.py`                                      | Validate structured x/y m/s, yaw rad/s and duration before any Twist publication                |
| Visual patrol/line following     | `llm_visual_patrol.launch.py`                                     | Require a valid line mask and known behavior transition, not just model text                    |
| Color tracking                   | `llm_color_track.launch.py`                                       | Require a valid selected color, target-loss stop and clear following area                       |
| Real-time image interpretation   | `vllm_with_camera.launch.py`                                      | Compare response with current image; a stale answer must not become a current obstacle decision |
| Language-guided vision tracking  | `vllm_track.launch.py`                                            | Object selection and tracking/actuation are separate states                                     |
| Smart-home navigation            | `vllm_navigation.launch.py map:=map_01`                           | Location-name mapping in `vllm_navigation.py` must match the actual saved map                   |
| Comprehensive Pro task execution | `llm_control_progress.launch.py`, optional `function:=navigation` | Staged tool/action sequence, with Pro pick/place and navigation calibrated independently        |

For named locations, record the map name/revision and actual coordinates, then verify one nearby goal in RViz. The comprehensive Pro example stores scene locations in `function_calling/llm_control.py`; its five-element representation is x/y in meters and roll/pitch/yaw in degrees. That representation differs from a ROS quaternion and must not be pasted into a quaternion field. Changing the map can invalidate all saved scene locations even when the filename stays the same.

The course prompts allow comparatively large velocity/time requests. A prompt is not an enforced controller limit. A robot application should validate finite numeric fields, allowed actions, maximum duration/speed, current command ownership and cancellation before dispatch, and refuse unknown tools or unreachable targets. These are engineering requirements added here; no claim is made that the unmodified supplied examples enforce them. Test structured outputs with physical action dispatch disabled before enabling tools. Pro transport examples must not be offered as actions on the Standard base. [Pro multimodal/embodied/comprehensive applications](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/12_Large_AI_Model_Courses.html#_12-2-multimodal-large-model-applications).

### Offline models are a separate deployment <a href="#rosorin-reference-offline-models" id="rosorin-reference-offline-models"></a>

The offline lane has **three separate roles**: a Sherpa-ONNX microphone recognizer, a streaming ASR server for the recording client, and Ollama for local language-model requests. Starting Ollama does not start the ASR server. The course's recording overview mentions an emotion/Ollama workflow, but its actual commands and embedded server implement speech recognition; follow that inspected interface rather than that mismatched introductory paragraph. The illustrated language model is `qwen3:1.7b`; its presence is not a measured memory, latency or throughput guarantee for either the Standard Nano 8GB or Pro NX 16GB.

Use the model/voice resources delivered for the installed release. The Pro course illustrates **`sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30`** with `encoder.int8.onnx`, **`decoder.onnx`**, `joiner.int8.onnx` and `tokens.txt`. The decoder filename is not automatically an `.int8` variant merely because the folder says int8. Do not mix a newer encoder with older decoder/tokens. These asset binaries and the installed ASR runtime were not executed or performance-tested here. [Offline preparation and examples](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/12_Large_AI_Model_Courses.html#_12-5-offline-large-ai-model-applications).

### First offline transcript directly from the microphone <a href="#rosorin-reference-offline-microphone" id="rosorin-reference-offline-microphone"></a>

1. Stop competing app/voice behaviors, leave moving robot tools disabled and inspect `arecord -l`. Select the actual USB input/output in the robot's Sound settings; the course's `Analog Input-XFM-DP-V0.0.18` and `Speakers-USB Audio Device` are observed labels, not a permanent ALSA card number. Confirm a short capture/playback as described in the audio section before diagnosing ASR.
2. In a terminal on the **robot host**, check the matching four assets and supplied microphone script. The following check reads file existence only; it does not validate model contents or obtain missing downloads:

```bash
cd ~/third_party/sherpa-onnx
python3 - <<'CHECK_ASR'
from pathlib import Path
root = Path('sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30')
paths = [root / name for name in
         ('encoder.int8.onnx', 'decoder.onnx', 'joiner.int8.onnx', 'tokens.txt')]
paths.append(Path('python-api-examples/speech-recognition-from-microphone-with-endpoint-detection.py'))
missing = [str(path) for path in paths if not path.is_file()]
if missing:
    raise SystemExit('Missing installed ASR files: ' + ', '.join(missing))
print('Matched asset filenames and microphone script are present')
CHECK_ASR
```

3. From that same directory, start the direct recognizer with explicit component paths:

```bash
python3 python-api-examples/speech-recognition-from-microphone-with-endpoint-detection.py \
  --encoder ./sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30/encoder.int8.onnx \
  --decoder ./sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30/decoder.onnx \
  --joiner ./sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30/joiner.int8.onnx \
  --tokens ./sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30/tokens.txt
```

4. Wait for the input-ready indication, speak a short utterance appropriate to this Chinese model and pause for endpoint detection. The article describes 100ms audio chunks and intermediate text followed by a completed recognition segment. Stop this microphone-owning process before starting the separate recording-client exercise.

**Expected result:** the terminal produces text corresponding to the spoken test utterance; silence or an empty transcript is a failure checkpoint, not permission to start a robot action. If files/imports fail, resolve the installed release/environment. If recording works but recognition does not, inspect model/language/recognizer errors; if recording itself is silent, correct capture routing first. No microphone inference or accuracy test was run here. [Direct microphone command, audio routing and expected text](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/12_Large_AI_Model_Courses.html#_12-5-2-1-speech-to-text-test).

### Recording client: start the separate streaming ASR server <a href="#rosorin-reference-offline-asr-server" id="rosorin-reference-offline-asr-server"></a>

1. Keep the direct recognizer stopped so it does not compete for capture. In terminal A on the robot host, work from **the home directory**: the article's server paths are relative to it. Verify that `~/third_party/sherpa-onnx/python-api-examples/streaming_server.py` and its `web` directory exist, as well as the four checked model files. Start the installed server with an explicit web root and port:

```bash
cd ~
python3 third_party/sherpa-onnx/python-api-examples/streaming_server.py \
  --tokens third_party/sherpa-onnx/sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30/tokens.txt \
  --encoder third_party/sherpa-onnx/sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30/encoder.int8.onnx \
  --decoder third_party/sherpa-onnx/sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30/decoder.onnx \
  --joiner third_party/sherpa-onnx/sherpa-onnx-streaming-zipformer-zh-xlarge-int8-2025-06-30/joiner.int8.onnx \
  --doc-root third_party/sherpa-onnx/python-api-examples/web \
  --port 6006
```

2. Keep that terminal open. The embedded server parser defaults to **6006** and checks that the document-root directory exists. It receives audio over a WebSocket interface, performs recognition and returns text/segment results. Confirm model-loading/listening output; if the port is already occupied, identify the existing process instead of starting duplicate servers. The source binds the server's network listener without restricting it to loopback; use the intended robot network and its reviewed access policy. If the installed recording client's ASR endpoint was changed, reconcile its host/port with this actual server rather than assuming a different release's client defaults.
3. In terminal B, start the **separate** client from its own directory so its relative resource paths resolve:

```bash
cd ~/large_models
python3 offline_asr_demo.py
```

4. Wait for **Recording…**, speak the short test utterance, then inspect the transcript. The source client passes `./resources/audio/test_recording.wav` to `speech.OfflineRealTimeASR`; check the recording separately after it has been written:

```bash
ls -l ~/large_models/resources/audio/test_recording.wav
aplay ~/large_models/resources/audio/test_recording.wav
```

5. Stop the recording client, then the server with Ctrl+C when finished. Preserve a useful sample and the model/runtime versions before changing settings. To use the robot's offline action lane later, select **ASR Mode → offline**, use **Save**, require **Save Success**, then reopen/inspect that setting. That backend selection does not itself start all required services or validate a moving tool.

**Expected result:** terminal A remains the ASR service; terminal B reports recording and recognized text; the WAV exists and playback contains the test speech. A server connection failure with a good WAV points to the ASR endpoint/runtime/model path; a missing or silent WAV points first to the client/capture path. Ollama can subsequently be tested for a local text response and the separate `offline_tts_demo.py`, `offline_llm_demo.py`, `offline_llm_nlu_demo.py` and `offline_llm_er_demo.py` exercises, but it is not a remedy for an absent speech server. Some reused offline action paragraphs still say “cloud”; inspect the selected configuration/network dependencies before claiming an entirely disconnected application. [Recording/server/client and WAV procedure](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/12_Large_AI_Model_Courses.html#_12-5-2-6-recording-test), [backend Save procedure](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/12_Large_AI_Model_Courses.html#_12-5-1-preparation). No server, client, model, robot action or hardware test was run here.

## Pro OpenClaw applications <a href="#rosorin-reference-openclaw" id="rosorin-reference-openclaw"></a>

This course is **Pro-specific** and requires its matched `openclaw_controller` package/resource bundle. It is not established for the assigned Standard base. The official deployment archive includes scripts that replace workspace identity/memory/skills files and create backups. Inspect those changes and retain the current robot configuration before deployment; do not automatically answer yes to every prompt. The archive and its deployment script were not executed in this review.

### Base, arm, camera and grasp service boundaries <a href="#rosorin-reference-openclaw-services" id="rosorin-reference-openclaw-services"></a>

After a verified deployment, the documented build selects `openclaw_controller` in the existing ROS 2 workspace. Configure the local gateway/backend using the installed OpenClaw configuration interface, then test a text-only interaction before giving it robot tools. The source runs `robot_base_control.launch.py`, `openclaw gateway run` and `openclaw tui` in separate terminals. These have different roles: ROS execution, model/tool gateway and operator interface. Closing a TUI is not proof of a stopped chassis or arm.

| Pro feature                        | Source interface                                                                                      | Required checkpoint                                                   |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Base movement / arm movement       | `robot_base_control.launch.py` plus the corresponding permitted tool                                  | Inspect the generated action and active command owner before dispatch |
| Camera analysis                    | Camera tool in the same course                                                                        | Confirm the answer refers to a fresh image without moving             |
| Color grasping                     | `/claw_track_and_grab/start`, `/set_color`, `/start_pick`, `/place`, `/init_pose`, `/pick_status`     | Check service types, target/depth alignment and explicit pick state   |
| Arbitrary-object tracking/grasping | `robot_base_control.launch.py track_method:=obj_track object_track_debug:=true enable_tracking:=true` | Select the object ROI, confirm track/depth, then permit the pick      |

The color service is `interfaces/srv/SetString`; the listed start/pick/place/init/status calls use `std_srvs/srv/Trigger`. A status query is different from a pick trigger. The names in the table abbreviate the shared `/claw_track_and_grab` prefix for readability. Follow the manual's staged sequence—start, select color/ROI, align, pick, inspect status, place and return to a clear pose—rather than repeatedly submitting a natural-language command when one stage fails. [OpenClaw basic/grasp applications](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/13_OpenClaw_Practical_Tutorial.html).

### Home, community and factory scenes <a href="#rosorin-reference-openclaw-scenes" id="rosorin-reference-openclaw-scenes"></a>

Home navigation uses `navigation_manager.launch.py` and `config/navigation_position.yaml`, where the course edits x, y and yaw for named locations. Verify the unit convention in the installed loader before entering a ROS quaternion or degree value. Community/factory applications use `smart_scene_navigation.launch.py navigation_mode:=smart_community` or `smart_factory` and their respective YAML files. Their scene IDs must agree with the road-network waypoint IDs; names alone do not locate an object.

The AprilTag interaction course separately starts `apriltag_control_node.launch.py`. Debug mode selection uses `/apriltag_control_node/set_debug_mode` (`SetString`) with illustrated modes `pick_exp` or `pick_basket`. Its pick/place/debug/init/clear-target Trigger services are distinct actions: `debug_pick_exp`, `place_exp`, `debug_pick_basket`, `debug_place_basket`, `pick_exp`, `pick_basket`, `place_basket`, `init_pose` and `clear_target`. Test a stationary tag/pose and an unloaded action before combining those actions with navigation. `/request_waypoint` remains an integer graph request; a scene pipeline must wait for actual navigation/action completion before issuing the next motion. A model response is not completion feedback. [OpenClaw comprehensive scenes and debug steps](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/13_OpenClaw_Practical_Tutorial.html#_13-4-openclaw-comprehensive-applications).

## Original offline RRC capture decoder <a href="#rosorin-reference-offline-decoder" id="rosorin-reference-offline-decoder"></a>

This original example reads only a supplied hexadecimal string. It opens no serial port and sends no commands. Its default is a **synthetic** successful bus-servo-position report, corresponding to raw position 833 for servo 5, not an observed robot measurement or a claim that 833 means a particular angle. CRC is checked against the pinned SDK's actual algorithm.

```python
import json
import struct
import sys

def crc8(data):
    value = 0
    for octet in data:
        value ^= octet
        for _ in range(8):
            value = (value >> 1) ^ (0x8C if value & 1 else 0)
    return value

def decode(raw):
    cursor = 0
    while cursor < len(raw):
        start = raw.find(b'\xaa\x55', cursor)
        if start < 0:
            return
        if start + 4 > len(raw):
            yield {'offset': start, 'error': 'truncated_header'}
            return
        function, size = raw[start + 2:start + 4]
        end = start + size + 5
        if end > len(raw):
            yield {'offset': start, 'error': 'truncated_frame',
                   'missing_bytes': end - len(raw)}
            return
        if crc8(raw[start + 2:end - 1]) != raw[end - 1]:
            yield {'offset': start, 'error': 'bad_crc'}
            cursor = start + 1
            continue
        payload = raw[start + 4:end - 1]
        item = {'offset': start, 'function': function,
                'payload': payload.hex(' '), 'crc': 'valid'}
        if function == 5 and size == 5 and payload[1] == 5:
            servo, command, status, position = struct.unpack('<BBbh', payload)
            item.update(servo_id=servo, status=status)
            if status == 0:
                item['position_units'] = position
        yield item
        cursor = end

if __name__ == '__main__':
    if len(sys.argv) > 1:
        data = bytes.fromhex(sys.argv[1])
    else:
        content = bytes.fromhex('05 05 05 05 00 41 03')
        data = b'\xaa\x55' + content + bytes([crc8(content)])
    for record in decode(data):
        print(json.dumps(record, sort_keys=True))
```

Save as `rrc_capture_review.py` and run `python3 rrc_capture_review.py`. **Expected result:** one CRC-valid synthetic function-5 record with servo ID 5, success status 0 and `position_units` 833. Supply a copied capture as a quoted hex argument to inspect real logs; changing the final byte should produce `bad_crc`, while removing it reports truncation. Unknown functions remain raw records instead of being decoded with another model's schema. This parser does not establish electrical compatibility, authentication, timestamps or replay safety.

## Course resources, diagnostics and validation <a href="#rosorin-reference-resources" id="rosorin-reference-resources"></a>

| Resource                                                        | Official destination and access boundary                                                                                                                                                                                                                |
| --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Pro images, hardware/controller materials, actions and examples | [ROSOrin Pro resource collection](https://drive.google.com/drive/folders/1MnJEjFJ0unkbC2EDJeqvwFycdHSjqqf4?usp=sharing); select NX/Pro release, not a screenshot filename                                                                               |
| Pro STM32/controller documentation                              | [Controller files](https://drive.google.com/drive/folders/1ITrr0a_EAi3al5hOrIHmCNFlZunjZ0LM?usp=sharing); schematic/protocol archive versions not independently established by a folder title                                                           |
| Pro course/application source                                   | [Pinned NX repository](https://github.com/Hiwonder/ROSOrin-Pro/tree/6c2a621fe628cc4928c48fc11d8d982594d471eb); inspect its README/rights and installed-image correspondence                                                                             |
| Standard source                                                 | [Pinned ROS 2 repository](https://github.com/Hiwonder/ROSOrin/tree/52b5af20893836e4faff6d27ad5660376b36a036); not a Pro image or arm hardware grant                                                                                                     |
| Standard factory image/source collection                        | [ROSOrin resources](https://drive.google.com/drive/folders/1CdWc8_aKkCjF3wer7S64FABitaiRAc5v?usp=sharing); choose the Nano SUPER Standard release                                                                                                       |
| Aurora workbench/driver downloads                               | [Aurora appendix](https://wiki.hiwonder.com/projects/Aurora930-Pro/en/latest/docs/Appendix.html); x86\_64 VM and Windows packages are separate from Orin                                                                                                |
| Pro simulation VM / packages                                    | [VM image](https://drive.google.com/drive/folders/1ngAhp5uh3av6Iiuy06FemK0FR52-JVf7?usp=sharing), [feature packages](https://drive.google.com/drive/folders/1sq3698U-EX7a4gbjmGnwYbptlJ3B8aMM?usp=sharing)                                              |
| Voice-module firmware/tool                                      | [Firmware tool](https://drive.google.com/drive/folders/1EJkwyTzH41VwMuQcJhn7kSNYjEHCFM4d?usp=sharing), [WonderEcho materials](https://drive.google.com/drive/folders/1cac3Lk0PsyjmU1LoKvBltH8ixRmQJYwj?usp=sharing); exact binary must match the module |
| Pro OpenClaw bundle                                             | [Official course resource](https://drive.google.com/drive/folders/1qifIfVWgClXfVTf3ef_MZhHRNiiKLGat?usp=sharing); deployment/archive contents were not executed or certified                                                                            |
| Speech-resource licensing                                       | [iFLYTEK resource service](https://www.xfyun.cn/); account-specific offline resources/APPID are not supplied by these instructions                                                                                                                      |
| App, remote tools and flashing-tool index                       | [Pro appendix](https://wiki.hiwonder.com/projects/rosorin-pro/en/latest/docs/Appendix.html), [Standard appendix](https://wiki.hiwonder.com/projects/ROSOrin/en/jetson-orin-nano-version/docs/resources_download.html)                                   |

Folder links are resource destinations, not verified hashes of every image, CAD file or executable inside them. Obtain and record the matching filename/revision/hash before recovery or firmware replacement; unavailable/account-gated archives remain an explicit limit. Manufacturer diagrams and binaries retain their original rights. The course explanations and offline decoder here are original; long vendor programs are linked rather than reproduced.

Both official appendices explicitly direct owners to request the system image/source package from Hiwonder with an order number. No supplier request was sent in this review. Public GitHub source is independently readable, but it does not establish a checksum or completeness for that supplier-delivered factory image. The Drive collection links were not accessible through the research browser; individual disk images, CAD archives, voice binaries and the OpenClaw deployment archive therefore remain uninspected downloads rather than tested resources.

For a drifting map, check wheel/scanner frame and odometry sign before changing planner tolerances. For a bad grasp, separate detection, depth units, hand-eye transform, IK and gripper alignment. For silent voice, separate USB audio, wake-word firmware, selected ASR resource and provider connectivity. For a stalled model task, inspect its last completed state and stop command ownership before retrying. For an app that no longer connects after a lesson, stop the lesson's owners before restarting the factory app service.

The procedures describe expected user results. No ROS build, simulator session, firmware flash, robot drive, calibration or grasp was executed in this review. Local parser/syntax validation, where recorded, is not hardware validation.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

Reviewed the exact two store variants, both official Orin manuals, embedded chassis/navigation interfaces and Pro hardware/arm sources. The Pro Orin wiring photograph was visually inspected. Sensor-model, arm, display, host and software-lane differences are explicit. Existing canonical page identity is retained.

The original stationary observer passed Python syntax parsing. No ROS build, robot connection, IMU calibration, flashing, driving, grasping or simulation execution was run. For other mobile manipulators, compare [JetRover](https://wiki.openelab.io/robotics/hiwonder/hiwonder-jetrover-development-guide) and [LanderPi](https://wiki.openelab.io/robotics/hiwonder/hiwonder-landerpi-development-guide), using their own power and controller paths.
