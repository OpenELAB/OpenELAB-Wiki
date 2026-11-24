---
description: >-
  Commission the NX SUPER 16 GB ROSpider with power/port checks, passive ROS 2
  observation, gait ownership, SLAM, depth vision and arm-development
  procedures.
---

# Hiwonder ROSpider Ultimate NX SUPER: gait, sensors and ROS 2 commissioning

{% hint style="info" %}
[**Hiwonder ROSpider Ultimate / Orin NX SUPER 16 GB on OpenELAB — SKU Hiwonder-21060103**](https://openelab.io/products/rospider-ros2?variant=46120279376070)
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

![ROSpider — product image supplied by OpenELAB](../../.gitbook/assets/hiwonder-95.png)

_Existing OpenELAB product illustration retained for model context; option contents and electrical connections are identified by the tables and diagrams below._

ROSpider is a ROS 2 hexapod with 18 leg joints and a six-servo arm/gripper assembly. The assigned **Ultimate Kit / Jetson Orin NX SUPER 16 GB** combines the walking body, LiDAR, Aurora930 Pro depth camera and six-microphone array. Its delivered environment is Ubuntu 22.04.5/ROS 2 Humble. This page starts with the factory posture, network connection and observation of sensor streams, then develops gait, mapping and grasping tasks. [Exact store configuration](https://openelab.io/products/rospider-ros2?variant=46120279376070), [official user manual](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html).

The documentation URL contains “jetson-orin-nano-version”, but its manual explicitly covers **Orin Nano and Orin NX connections**. This does not make a Nano image or a Raspberry Pi power lead interchangeable with the NX. Starter/Standard/Advanced packing lists are comparison references; this SKU uses the Ultimate sensor/voice package.

### Other established purchasing options <a href="#models-and-purchasing-options" id="models-and-purchasing-options"></a>

This canonical page also retains the following catalogued family options. The detailed first-run workflow above/below is for the exact host/kit variants in the opening callout; select the matching host image and kit-specific hardware for other options. A controller-excluded option needs that separately supplied host.

| SKU                 | Established option                               |
| ------------------- | ------------------------------------------------ |
| `Hiwonder-21060093` | Starter Kit / Without Controller                 |
| `Hiwonder-21060095` | Starter Kit / With Raspberry Pi 5(8 GB)          |
| `Hiwonder-21060109` | Starter Kit / With Jetson Nano(4 GB)             |
| `Hiwonder-21060107` | Starter Kit / With Jetson Orin Nano Super(8 GB)  |
| `Hiwonder-21060108` | Starter Kit / With Jetson Orin NX Super(8 GB)    |
| `Hiwonder-21060094` | Starter Kit / With Jetson Orin NX Super(16 GB)   |
| `Hiwonder-21060096` | Standard Kit / Without Controller                |
| `Hiwonder-21060098` | Standard Kit / With Raspberry Pi 5(8 GB)         |
| `Hiwonder-21060114` | Standard Kit / With Jetson Nano(4 GB)            |
| `Hiwonder-21060112` | Standard Kit / With Jetson Orin Nano Super(8 GB) |
| `Hiwonder-21060113` | Standard Kit / With Jetson Orin NX Super(8 GB)   |
| `Hiwonder-21060097` | Standard Kit / With Jetson Orin NX Super(16 GB)  |
| `Hiwonder-21060119` | Advanced Kit / Without Controller                |
| `Hiwonder-21060101` | Advanced Kit / With Raspberry Pi 5(8 GB)         |
| `Hiwonder-21060099` | Advanced Kit / With Jetson Nano(4 GB)            |
| `Hiwonder-21060117` | Advanced Kit / With Jetson Orin Nano Super(8 GB) |
| `Hiwonder-21060118` | Advanced Kit / With Jetson Orin NX Super(8 GB)   |
| `Hiwonder-21060100` | Advanced Kit / With Jetson Orin NX Super(16 GB)  |
| `Hiwonder-21060124` | Ultimate Kit / Without Controller                |
| `Hiwonder-21060104` | Ultimate Kit / With Raspberry Pi 5(8 GB)         |
| `Hiwonder-21060102` | Ultimate Kit / With Jetson Nano(4 GB)            |
| `Hiwonder-21060122` | Ultimate Kit / With Jetson Orin Nano Super(8 GB) |
| `Hiwonder-21060123` | Ultimate Kit / With Jetson Orin NX Super(8 GB)   |
| `Hiwonder-21060103` | Ultimate Kit / With Jetson Orin NX Super(16 GB)  |

[OpenELAB family options](https://openelab.io/products/rospider-ros2).

## Applications <a href="#applications" id="applications"></a>

Use ROSpider to investigate tripod/ripple walking, posture and center-of-mass control, visual target interaction, LiDAR mapping and mobile manipulation. A good first experiment logs scan/camera streams while the body remains stationary. A second experiment compares a short straight walk with a fixed visual reference; a third maps a small level area before attempting a transport task.

Legged movement periodically changes body height and attitude. Camera and LiDAR frames must remain consistent with that motion. A visually convincing map can still conceal a wrong transform or stale sensor stream; validate stationary geometry and timestamps before tuning navigation. Bridge crossing and fall-prevention demonstrations require their specific depth-camera setup and do not establish general edge detection. [Motion](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/2_Motion_Control_Course.html), [3D applications](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/8_Robotic_Arm_Vision_Applications.html).

## Specifications <a href="#specifications" id="specifications"></a>

| Item                        | Exact-model reference                                                                                 |
| --------------------------- | ----------------------------------------------------------------------------------------------------- |
| Controller option           | Jetson Orin NX SUPER 16 GB; use its matched robot image                                               |
| Software                    | Ubuntu 22.04.5 LTS; ROS 2 Humble; Python/C/C++ learning paths                                         |
| Body/arm                    | 18 DOF walking body; 6-servo arm/gripper assembly; 24 smart bus servos total                          |
| Servo families              | HX-12H, HTS-20H, HX-35H; do not substitute one voltage/torque specification for all three             |
| Lower controller            | STM32F407VET6; QMI8658 IMU; PWM and serial-bus servo control                                          |
| Battery                     | 11.1 V, 6000 mAh, 3C lithium pack; manufacturer/store runtime reference up to 60 min varies with load |
| Charger                     | 12.6 V 2 A; DC 5.5 × 2.5 mm connector                                                                 |
| Depth camera                | Aurora930 Pro; USB 2.0; 40 mm stereo baseline; 30–300 cm working distance                             |
| Camera output               | Depth 640 × 400 or 320 × 240 at 5–15 fps; Raw16 depth; NV12 color; Raw8 IR                            |
| Camera supply               | 5 V ±10%, 1.5 A interface rating; stated average consumption below 1.6 W                              |
| Depth reference             | 8 mm accuracy at 1 m; 3 mm precision at 0.5 m / 7 mm at 1 m; not independently measured               |
| Camera light/environment    | 3–6000 lux;−10 to 55 °C; avoid treating these as whole-robot limits                                   |
| Voice                       | Ultimate six-channel array; select `xf`, not WonderEcho Pro                                           |
| App walking settings        | Step amplitude 10–60; speed 10–100 in app units, not m/s                                              |
| App LiDAR behavior settings | Detection 0.5–1.5 m; movement 0.02–0.1 m/s                                                            |

[Hardware and camera tables](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html#_1-8-hardware-introduction), [exact kit/battery](https://openelab.io/products/rospider-ros2). A servo's torque-class designation is not a payload rating. No verified universal arm payload or bare-UART voltage rating was established in the public robot manual; retain the supplied servos/harness and start with the supplied light props.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Keep host, servo and charging paths distinct

![Hiwonder ROSpider STM32 board numbered connector photograph](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/assets/image150.nxEdQhSY.webp)

Official Hiwonder connector photograph, visually inspected for this guide. Its numbers are illustration callouts. **1** is 5 V output for Pi/older Nano hosts; **2** is the controller UART communication port; **3** serves the Orin Nano/NX supply and arm-servo connections; **4** is the wireless-controller USB receiver; **5** is 12.6 V charging input; **6** is battery input; **7** is the power switch. The photograph shows dedicated paths rather than seven interchangeable connectors. Do not use the Pi 5 V output to power this NX. [Manual port table](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html#_1-2-assembly-and-wiring).

The host's camera USB port, STM32 communication port and microphone port have separate assignments in the Orin diagram. Preserve those assignments while diagnosing; moving several cables at once makes enumeration failures difficult to isolate. The UART communicates using Hiwonder's RRC protocol, not the Yahboom micro-ROS interface. Do not send another vendor's serial frame or power a servo through a host USB port.

### Charging and initial posture

With the robot off, verify the pack connection beneath the bottom metal cover. Charge through the marked port with the supplied 12.6 V 2 A charger: red indicates charging, green completion. Disconnect after charging. Put the robot on a **level floor in the illustrated initial leg/arm posture** before switching on. The robot resets its posture during boot; placing it folded against a leg, tool or table can stall a servo. Keep hands out of the joint sweep and do not force powered joints. [Charging and boot sequence](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html#_1-3-basic-robot-usage).

A blue flashing network LED appears before ROS startup completes. Wait for the short buzzer indication and completed posture reset. Watch for sustained shaking, heat, noise or blocked joints; end the behavior and remove power if a servo remains stalled. A raised chassis stand must support the whole robot without obstructing leg reset; an arbitrary wheel-robot test stand is inappropriate for a hexapod.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

The delivered `~/ros2_ws` contains `src`, `install`, `build`, `logs` and reference commands. Principal packages include `app`, `example`, `interfaces`, `slam`, `navigation`, `peripherals`, `simulations` and the `driver` controller/kinematics packages. The manufacturer also lists `third_party_ros2`, `large_models` and `wifi_manager`. Inspect the actual image rather than installing a similarly named generic ROS package. [Software architecture](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html#_1-7-system-software-architecture).

The app/autostart service owns the controller at boot. For a standalone development session, the documented targeted stop is:

```bash
sudo systemctl stop start_app_node.service
```

This stops the app service; `~/.stop_ros.sh` is the broader documented script that stops ROS nodes. Do not stop the only active controller while the robot is walking. Return it to a stable stance first. At the end, restore app/gamepad operation with:

```bash
sudo systemctl restart start_app_node.service
```

Before commands, record `cat /etc/os-release`, `printenv ROS_DISTRO ROS_DOMAIN_ID need_compile`, `ros2 pkg prefix controller` and `ros2 node list`. Lessons branch on `need_compile`: installed-package lookup and source-path execution are different modes. The public wiki does not identify one image checksum/JetPack release for every NX shipment. Save the delivered image/version and obtain the matching recovery image through the [official appendix](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/Appendix.html).

## Getting started <a href="#getting-started" id="getting-started"></a>

### 1. Establish network and a live camera result

1. Complete the posture/power checks and wait for startup. Join the factory `WN…` hotspot with password `12345678`; retain the connection when the computer reports no internet.
2. Open WonderAi, select **ROSpider**, add **Direct Connection** and choose the discovered robot. On iOS, wait for the Wi-Fi icon before returning to discovery.
3. Open Robot Control and inspect the camera view without dragging movement or arm sliders. Place a tag or colored block in view, then remove it. Confirm that the view changes live.
4. For development, use NoMachine at `192.168.149.1` with the published Jetson account `ubuntu`/`ubuntu`. Alternatively use SSH at the same address. Change initial credentials before shared-network operation.
5. If Wi-Fi fails, the Jetson Type-C data connection can expose `192.168.55.1` after the documented host NDIS setup. This is a network/data connection, not the robot's charging port.

**Expected result:** a stable remote session and a camera image that responds immediately to a moving prop. A frozen last frame is a failed checkpoint. The robot should remain stationary throughout. [Networking/app/remote access](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html#_1-4-development-environment-setup).

### 2. Original read-only ROS sensor receipt report

Save `rospider_observe.py` on the NX and run `python3 rospider_observe.py` in the supplied ROS environment while the factory nodes run. This discovers the image's actual **LaserScan** and **Image** topics instead of guessing names. It keeps subscriptions alive, receives for 15 seconds and reports receipt/frame/encoding. It never publishes servo or gait commands.

```python
import time
import rclpy
from rclpy.qos import qos_profile_sensor_data
from sensor_msgs.msg import Image, LaserScan

rclpy.init()
node = rclpy.create_node('rospider_sensor_receipt')
subscriptions = []
counts = {}
last = {}
try:
    end = time.monotonic() + 3
    while time.monotonic() < end:
        rclpy.spin_once(node, timeout_sec=0.1)
    kinds = {'sensor_msgs/msg/Image': Image,
             'sensor_msgs/msg/LaserScan': LaserScan}
    def record(name, message):
        counts[name] = counts.get(name, 0) + 1
        last[name] = message
    for name, types in node.get_topic_names_and_types():
        match = next((t for t in types if t in kinds), None)
        if match:
            counts[name] = 0
            subscriptions.append(node.create_subscription(
                kinds[match], name,
                lambda message, key=name: record(key, message),
                qos_profile_sensor_data))
    end = time.monotonic() + 15
    while time.monotonic() < end:
        rclpy.spin_once(node, timeout_sec=0.2)
    for name in sorted(counts):
        message = last.get(name)
        details = 'NO DATA'
        if isinstance(message, Image):
            details = f'{message.width}x{message.height} {message.encoding}'
        elif isinstance(message, LaserScan):
            details = f'{len(message.ranges)} rays frame={message.header.frame_id}'
        print(name, counts[name], details)
    if not subscriptions or not any(counts.values()):
        raise SystemExit('No sensor messages: inspect bringup and ROS domain')
finally:
    node.destroy_node()
    rclpy.shutdown()
```

**Expected result:** image/scan topics with nonzero message counts. It is possible for other transports to expose compressed images only; in that case inspect `ros2 topic list -t` and the camera driver rather than treating absent raw images as a hardware fault. Confirm separate color and depth streams for Aurora, with dimensions/encoding consistent with its configuration. The report proves receipt during the interval, not depth accuracy or correct TF.

### 3. Walking and coordinate checks

Once the stationary checks pass, close all competing app modes and use the wireless controller for one short step sequence on a clear floor. **START stops/resets posture**; SELECT+START toggles body/arm mode, indicated by one/two beeps. Left joystick commands tripod translations; directional controls and the opposite joystick also affect gait, turning and body height. Verify the stop/reset action before any autonomous task. [Controller table](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html#_1-3-5-wireless-controller-remote-control).

The motion lessons describe stride in millimeters, step height in millimeters and duration in seconds. The article repeats a gait filename and contains inconsistent direction/rotation comments; the detailed source reference below resolves gait 1/2 and the degree-to-radian conversion in the published examples. Do not copy a detached `traveling()` signature as a motion contract. Inspect the **installed**`ControllerClient.traveling` implementation and the matched example before altering gait, angle or step count. A zero step count can mean continuous walking. Use finite steps and the verified stop behavior when developing. [Motion course and embedded source](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/2_Motion_Control_Course.html).

### 4. LiDAR, SLAM and navigation

The dedicated LiDAR lesson uses `ros2 launch app lidar_node.launch.py debug:=true`. Its enter service and set-running values select avoidance 1, following 2, guarding 3 and behavior-off 0. Entering a behavior is an **actuation** step: validate scan receipt first, then one mode in a clear area. In the pinned source, data 0 also sends `traveling(gait=-2, time=1, steps=0)`, which requests a **one-second leg reset to `DEFAULT_POSE`**. Clear the leg sweep and allow that posture transition to complete before changing modes; this is not a motionless stop or torque-off. Check the installed version before using the service. Do not treat the app's detection threshold as a sensor's absolute maximum range. [LiDAR course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/3_LiDAR_Course.html), [LiDAR callback](https://github.com/Hiwonder/ROSpider/blob/490080f9bb03e702ba87c843c730c6866877cc17/src/app/app/lidar_controller.py), [posture-reset implementation](https://github.com/Hiwonder/ROSpider/blob/490080f9bb03e702ba87c843c730c6866877cc17/src/driver/controller/controller/move_controller.py).

For first mapping, stop the app owner in a stable stance, then launch the documented sequence in separate terminals:

```bash
ros2 launch slam slam.launch.py
ros2 launch slam rviz_slam.launch.py
ros2 launch peripherals teleop_key_control.launch.py
```

Drive a small closed loop, monitoring the live scan and wall overlap. Keep enough clearance for all six legs. Save into a **new named map**, preserving previous work:

```bash
cd ~/ros2_ws/src/slam/maps
ros2 run nav2_map_server map_saver_cli -f map_01 --ros-args -p map_subscribe_transient_local:=true
```

**Expected result:** a map image and YAML with valid resolution/origin and an existing image path. Back up both. The quick desktop shortcuts can overwrite the previously saved map; named command-line maps are easier to reproduce. Launch the matching navigation workflow, initialize pose in RViz, align laser walls to map walls and send one nearby clear goal. RTAB-Map has separate SLAM/navigation launch files and databases; do not mix its saved representation with a 2D map-only procedure. [Mapping/navigation course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/5_Mapping_and_Navigation_Course.html).

### 5. Develop the remaining course families deliberately

| Official topic family                                                                  | Original engineering progression                                                                                                                                                         |
| -------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gaits, translation, turning, speed, height, trunk twist and self-balance               | Change one parameter per run; measure actual path and body attitude. Calibrate IMU on a stationary level support before diagnosing balance gains                                         |
| PC action editor/custom app controls                                                   | Read factory servo deviations first; save a separate action name; test one supported posture before a multi-frame group. A reset-to-reference button moves servos                        |
| Forward/inverse kinematics and body center of mass                                     | Confirm leg numbering, body coordinate frame and units; compare a small pose change with predicted foot movement before walking                                                          |
| Color thresholds, recognition, tags, AR, color/tag coordinates, KCF and line following | Fix exposure/lighting, inspect overlays and calibrate color masks before letting perception command a leg or arm                                                                         |
| Machine learning/MediaPipe                                                             | Validate classification or landmarks against a fixed scene; confirm latency on NX before adding a motion response                                                                        |
| Arm servo deviation and 2D tracking/kicking/transport                                  | Factory deviation is already calibrated. Back up existing values; use the illustrated perpendicular-arm/gripper reference only if correction is needed                                   |
| 3D fall prevention, bridge crossing, grasping, shape/volume                            | Confirm valid depth and camera-to-body transform with a measured stationary prop. Glass, dark surfaces and near-range invalid pixels must not become valid footholds or grasp points     |
| Six-mic voice                                                                          | Set microphone type `xf`, Save then Apply. Confirm wake-word/recognition output before enabling `xf_mic_asr_offline voice_control_move.launch.py`                                        |
| MoveIt2/Gazebo/URDF                                                                    | Check model joint names and collision geometry in simulation; keep physical bridge/control nodes stopped during simulation-only work                                                     |
| Large-model basic/multimodal/embodied tasks                                            | Configure providers privately, test language/vision without tools, then inspect navigation/grasp action functions. Map names, camera calibration and stop ownership remain prerequisites |

Each course includes its own start/stop services and dependencies; launching all demonstrations together creates camera, serial and command conflicts. [Vision](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/6_ROS+OpenCV_Course.html), [machine learning](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/7_ROS+Machine_Learning_Course.html), [arm vision](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/8_Robotic_Arm_Vision_Applications.html), [voice](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/9_Voice_Control_Course.html), [simulation](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/10_Movelt_&_Gazebo_Simulation.html), [AI models](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/11_Large_AI_Model_Course.html).

### ROSpider control architecture and course workflows

The following reference applies to the **ROSpider Ultimate Orin NX SUPER 16 GB** robot and its delivered ROS 2 workspace. It expands the manufacturer's motion, sensing, vision, learning, manipulation, speech and simulation lessons into working engineering stages. A lesson that initializes a posture, follows a target or plays an action group can move the robot as soon as it starts; a name such as “recognition” does not mean it is observation-only. Retain the stationary first-result procedure above before beginning these activities.

#### Runtime ownership, packages and units

The robot separates the STM32/RRC transport, ROS servo/chassis control, hexapod kinematics, sensor drivers and application nodes. `controller` provides body/leg/action interfaces; `ros_robot_controller` carries lower-controller commands and feedback; `peripherals` starts sensors; `app` provides stateful phone/vision behaviors; `example` contains individual lessons. `arm_kinematics` solves arm targets, while `slam`, `navigation`, simulation and `large_models` packages add further layers. An application can include the controller and camera launch files itself. Starting the factory bringup and a second complete lesson simultaneously can create competing owners.

Before a standalone lesson, stop the active behavior through its own stop control, establish a stable resting posture and use the supplied `~/.stop_ros.sh` ownership handoff. Keep a second terminal available for the documented stop service. Inspect `ros2 node list`, `ros2 topic list -t` and `ros2 service list -t` before issuing a command. Many launch files select installed packages when `need_compile=True`, otherwise `/home/ubuntu/ros2_ws/src/...`; record `ros2 pkg prefix` and `printenv need_compile` so an edit is made to the code actually being launched. Ending a viewer does not stop an application publishing velocity or servo messages.

The public [ROSpider source snapshot `490080f9bb03e702ba87c843c730c6866877cc17`](https://github.com/Hiwonder/ROSpider/tree/490080f9bb03e702ba87c843c730c6866877cc17) exposes the interfaces below. Compare them with the delivered image before a new controller application: the published lessons and repository are related references, not a guarantee that every factory image contains the same revision.

| Interface                                           | Payload / role                                                                                                       | Practical boundary                                                                                                        |
| --------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `controller/traveling`                              | `kinematics_msgs/msg/Traveling`: gait, stride, height, direction, rotation, time, steps, relative\_height, interrupt | Body gait command, not a raw servo position                                                                               |
| `controller/cmd_vel`                                | `geometry_msgs/msg/Twist`                                                                                            | Translational velocity in m/s and yaw rate in rad/s; the checked controller clamps x to ±0.12, y to ±0.10 and yaw to ±0.6 |
| `controller/set_leg_absolute`, `set_leg_relatively` | `LegPosition`: leg ID, xyz, duration                                                                                 | Absolute foot point versus displacement from the current foot point are different operations                              |
| `controller/set_pose_1`                             | `kinematics_msgs/srv/SetPose1`: named pose and duration                                                              | Built-in posture selection can move every leg                                                                             |
| `controller/pose_transform_euler`, `set_pose_euler` | Body transformation / pose messages                                                                                  | Preserve the specific API's angle convention and incremental-versus-absolute meaning                                      |
| `controller/run_actionset`                          | `interfaces/msg/RunActionSet`                                                                                        | Selects a stored action, repetition and path behavior; it is not a passive file listing                                   |
| `/controller_manager/init_finish`                   | `std_srvs/srv/Trigger` readiness endpoint used by lessons                                                            | Service presence/readiness is distinct from a valid physical posture                                                      |

The velocity clamps are implementation ceilings, not recommended test speeds or a certified stop distance. The `ControllerClient` constructor waits for a controller pose service; creating it is not a bounded offline calculation. Use interface inspection and the existing passive observer first. [Controller client and callbacks](https://github.com/Hiwonder/ROSpider/tree/490080f9bb03e702ba87c843c730c6866877cc17/src/driver/controller/controller).

#### Gaits, translation, turning and speed experiments

Tripod walking alternates two three-leg support groups; ripple walking distributes the stepping sequence over the legs. In the checked source, **gait 1 is ripple, gait 2 tripod and gait 0 requests stopping**. The wiki's ripple paragraph repeats a tripod filename; the repository has separate `ripple_gait.launch.py` and `tripod_gait.launch.py`. Inspect the installed launch file before running it rather than changing a parameter to fit a copied label.

| Parameter / lesson        | Source behavior                                                                                                         | How to check it                                                                                                   |
| ------------------------- | ----------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| `stride`, `height`        | Foot stride/lift quantities in mm; lesson comments illustrate stride 0–65 and lift 0–50                                 | These are lesson ranges, not universal limits for every body posture or payload                                   |
| `time` / lesson `period`  | Step duration in seconds                                                                                                | A shorter period increases motion demand; it is not a direct m/s setting                                          |
| `steps`                   | Positive finite count; **0 means continuous**                                                                           | Use a bounded count in a new program and a separate stop path                                                     |
| `direction`               | Actual examples convert human-readable degrees with `math.radians(...)` before publishing                               | Do not copy 90 directly because a nearby comment says degrees                                                     |
| `rotation`                | Passed into the gait generator without a degree conversion; the source and translated comments disagree on turn wording | Establish sign with a small supervised test of the exact version; do not infer a safe yaw target from the comment |
| `relative_height`         | Generator can interpret lift as a percentage of body height rather than absolute mm                                     | Retain the flag with recorded parameters; changing it changes the meaning of the same number                      |
| `speed_control.launch.py` | Exposes `period` and `stride`; source defaults 1 and 15                                                                 | Log both values and compare actual displacement over a marked distance                                            |

The source examples `forward_and_rorate`, `left_and_right`, `diagonally`, `broken_line_walk` and `square_walk` combine straight, lateral, diagonal and segmented paths. The misspelling **`forward_and_rorate.launch.py`** is the actual resource name. The diagonal launch parameter is in degrees and its Python node converts to radians; the lower gait API does not perform that conversion for the caller.

For a first gait comparison, use the same level, high-friction clear surface, unloaded arm posture, battery state and conservative stride/period. Run one supplied lesson at a time, record the actual first leg/group movement and confirm its explicit stop completes. Compare distance, heading drift and body oscillation, then change one parameter. A square returning near its start tests accumulated gait/odometry error; it does not prove accurate localization. The supplied examples often run continuously for about five seconds before sending gait 0, so they are subsequent motion demonstrations rather than initial communication checks. [Motion course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/2_Motion_Control_Course.html), [actual body-control examples](https://github.com/Hiwonder/ROSpider/tree/490080f9bb03e702ba87c843c730c6866877cc17/src/example/example/body_control).

#### OLED text and controller readiness

The OLED lesson publishes `ros_robot_controller_msgs/msg/OLEDState` on `/ros_robot_controller/set_oled`. `index` selects a displayed line and `text` supplies its string. After its controller-readiness wait, the supplied example writes line 1 as `Hello word` and line 2 as `Hello Hiwonder`, separated by 0.2 s. These are the source's actual strings; a missing “l” in the first is not a display fault. The launch is `ros2 launch example oled.launch.py`, after the normal ownership handoff. That launch also includes the controller, so treat it as a controller-starting lesson rather than an independent USB display test. [OLED lesson](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/2_Motion_Control_Course.html#_2-10-oled-display), [actual publisher](https://github.com/Hiwonder/ROSpider/blob/490080f9bb03e702ba87c843c730c6866877cc17/src/example/example/body_control/include/oled.py).

A useful debugging order is: confirm the controller readiness service exists, inspect the topic type and subscriber count, then check whether a separate status node rewrites the same line. A string published before the display subscriber is ready can be lost; a successful publish command is not a display acknowledgement. Keep robot IP/battery status available through another interface when experimenting with those lines. Text rendering does not verify the servo bus or sensor stream.

#### Foot coordinates, inverse kinematics and body posture

The six foot points are defined in a body-centered frame and listed counterclockwise. The published reference geometry includes `X1=93.60`, `Y1=50.805`, `X2=0`, `Y2=73.535`, `INITIAL_X=70`, `INITIAL_Y=110` and ordinary body height `70` mm; the mapping posture uses a separate `95` mm height and the manual also lists `SLAM_HEIGHT=100`. These identify different named/reference configurations. Do not combine them into a new “corrected” height without checking the installed `build_in_pose` definitions and the current application.

A leg IK calculation converts a desired foot point into three joint angles and then controller position units. A reachable point for one leg does not prove the other five feet preserve support or that the body/arm clears the floor. `body_ik.launch.py` demonstrates leg motion, not only calculation. The documentation uses an older `set_leg_position` call while the current public client exposes absolute and relative leg messages; inspect the installed API rather than substituting a method name.

`transform_pose_euler(translate, axis, euler, duration, degrees=True)` in the lower step controller accepts body translation in mm, an explicit Euler axis sequence, corresponding angles and duration in seconds. `degrees=True` means degrees; `False` means radians. Axis order is material: `xyz` and `yxz` do not generally produce the same orientation. The higher `ControllerClient.pose_transform_euler(...)` does not expose the same complete argument list, so a lower-controller example cannot simply be pasted into that client.

The height, posture, wave and body-circle lessons use `height_adjustment.launch.py`, `posture_adjustment.launch.py`, `body_wave.launch.py` and `body_circle.launch.py`. The height example increments body z over repeated steps; total excursion is the increment multiplied by the count, not just the single increment. Preserve the starting named pose and reverse path, and check foot reach and cable clearance before changing either. The manual's illustrative rise/fall envelope belongs to its stated initial posture, not an arbitrary tilted or loaded configuration. Body-wave amplitude and circle radius are trajectory parameters; tune them only after a static pose is stable. [Coordinate and posture sections](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/2_Motion_Control_Course.html#_2-16-establishment-of-hexapod-robot-coordinate-system).

#### Action editor, servo offsets and app custom actions

The desktop editor starts from `~/software/actionset_editor` with `python3 main.py`. Its servo sliders use raw **0–1000** position units, action duration is **milliseconds**, and the displayed deviation adjustment range is **−125 to +125**. Those three quantities have different meanings. The Read Deviation operation unlocks the offset editor; Save Deviation writes calibration. “All 500” changes target values and is not a calibration procedure or a harmless reset.

For an original action, first save the existing action group and deviations. With the robot supported as the manual illustrates, load a known stable pose, choose a deliberately slow frame duration, make one small joint change and read/record all relevant joints into a frame. Add a return frame, run once with looping disabled, then save under a new English filename. Run Selected Frame is different from Run Whole Group; app assignment should point to the tested saved filename, not an unsaved row. The manual stores editor files in `/home/ubuntu/software/actionset_editor/ActionGroups`; retain that image-specific path with exported files.

To join groups, open the first file, use Integrate File for the second, inspect the boundary poses and timing, then save a new combined group. The last pose of group A and first pose of B may be far apart even when each group is independently valid. Do not use Delete All as a way to clear only the current editor view. Manual Programming removes holding torque; support the legs and arm before using it, read the manually placed position and re-establish support before enabling.

Factory calibration is already supplied. Recalibrate only when an identified mechanical deviation impairs the documented posture. For arm calibration the manual requires the arm upright, the specified horn centers aligned, the gripper approximately **2–3 cm open**, and the other illustrated reference checks. Match the physical ID diagram before editing any offset; a gait mistake, wrong model or invalid camera transform is not repaired by arbitrary servo offsets. [Action editing and custom controls](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/2_Motion_Control_Course.html#_2-11-host-computer-function-description), [arm calibration](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/8_Robotic_Arm_Vision_Applications.html#_8-1-servo-deviation-calibration).

#### IMU calibration and self-balancing

IMU calibration and servo deviation calibration are separate. Save `~/ros2_ws/src/peripherals/config/imu_calib.yaml` first. The course starts the lower-controller feedback node, then collects the six prescribed IMU orientations. Move the whole supported, non-walking robot only as shown in the manufacturer's orientation diagrams; do not roll an actively walking or gripping mechanism to satisfy a terminal prompt.

```bash
ros2 launch ros_robot_controller ros_robot_controller.launch.py
# In a second terminal, after the robot is supported and the source is confirmed:
ros2 run imu_calib do_calib --ros-args -r imu:=/ros_robot_controller/imu_raw --param output_file:=/home/ubuntu/ros2_ws/src/peripherals/config/imu_calib.yaml
```

Wait for the first IMU message, hold each requested orientation still, and accept the sample only after settling. The expected result is a newly written calibration YAML and stable orientation in `ros2 launch peripherals imu_view.launch.py`; a command returning immediately without samples is not success. Check axis orientation, stream freshness and the actual loaded YAML before retuning control gains.

`ros2 launch app self_balancing_node.launch.py debug:=true` is an actuating application: it consumes orientation and adjusts body/leg posture to compensate for tilt. Begin on a stable level support, inspect the zero/axes first and compare a small known tilt with the displayed direction. If correction increases the tilt, stop and resolve axes, mounting/calibration and the installed controller version. A self-balancing demonstration does not establish fall protection. [IMU and self-balancing lessons](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/2_Motion_Control_Course.html#_2-15-imu-calibration).

### ROSpider sensing, mapping and navigation reference

#### Camera ownership, RGB/depth registration and calibration

The camera course links to a separate **Aurora930 Pro** manual; its short parent page contains no complete camera installation procedure. On the robot, use `ros2 launch peripherals depth_camera.launch.py` only after handing over the existing camera owner. Inspect actual RGB, depth and CameraInfo topics and changing timestamps. The ROSpider vision examples use `/depth_cam/rgb/image_raw` and `/depth_cam/rgb/camera_info`; depth processing additionally needs the corresponding depth stream and calibration/TF from this image.

The [Aurora camera manual](https://wiki.hiwonder.com/projects/Aurora930-Pro/en/latest/docs/1.Introduction_to_Depth_Camera.html) identifies structured-light depth, a 40 mm baseline, a 30–300 cm working interval and USB 2.0. RGB/depth/IR formats and resolution/FPS must be obtained from the active driver; a color-looking depth visualization is not a metric depth array. For a known stationary target, compare its RGB pixel, a valid local depth patch, camera intrinsics and the camera-to-arm transform. Reject zero/invalid depths and stale or unmatched frames before converting a pixel into a robot coordinate.

The [standalone camera ROS instructions](https://wiki.hiwonder.com/projects/Aurora930-Pro/en/latest/docs/2.Configuration_and_Usage_in_ROS.html) describe separate ROS 1 Melodic and ROS 2 Humble **x86\_64** packages. That x86 SDK is not the Jetson arm64 binary. Their ROS 2 workspace build uses `colcon build --cmake-args -DSTREAM_SDK_TYPE=AURORA930`, then `aurora930_launch.py` and `viewer930_launch.py` in `deptrum-ros-driver-aurora930`. Keep that PC/VM path separate from the robot's `peripherals` wrapper. USB passthrough and udev permissions are PC-driver checks, not reasons to replace a working robot image. The linked monocular USB-camera resource is a Drive folder; a full independent archive/version audit was not established here, and a monocular image alone supplies no metric depth.

#### LiDAR modes and service lifecycle

LiDAR contributes a horizontal scan. An obstacle must intersect that plane to be observed; a low object, table edge or drop below the beam cannot be assumed detected. Start with a stationary scan/TF check and compare a known obstacle's bearing/distance before enabling movement.

After the ownership handoff, the course starts `ros2 launch app lidar_node.launch.py debug:=true`. It then calls `/lidar_app/enter` with `std_srvs/srv/Trigger` to subscribe/initialize, and `/lidar_app/set_running` with `interfaces/srv/SetInt64` to select a behavior:

| Data | Behavior                                     | Observable output / diagnostic                                                                                                                                                |
| ---- | -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0    | Disable behavior and request a posture reset | Pinned source requests `DEFAULT_POSE` over 1 s; clear the leg sweep and wait for the reset to complete before closing the launch. This is not torque-off or a motionless stop |
| 1    | Obstacle avoidance                           | Robot changes direction around an object intersecting the scan plane                                                                                                          |
| 2    | Following                                    | Robot changes position to maintain its configured range from the selected obstacle                                                                                            |
| 3    | Guarding                                     | Robot turns to face the detected obstacle                                                                                                                                     |

These are active motion modes. For a subsequent supervised trial, enter the application, select one mode and use one broad stationary target. Before sending data 0, clear the leg sweep: the pinned callback sends `traveling(gait=-2, time=1, steps=0)`, and the controller resets the legs to `DEFAULT_POSE` over one second. Verify completion of that active posture transition before exiting; data 0 does not release torque or promise motionless stopping. Compare the installed callbacks before use. [LiDAR callback](https://github.com/Hiwonder/ROSpider/blob/490080f9bb03e702ba87c843c730c6866877cc17/src/app/app/lidar_controller.py), [gait −2 reset](https://github.com/Hiwonder/ROSpider/blob/490080f9bb03e702ba87c843c730c6866877cc17/src/driver/controller/controller/move_controller.py). If `/enter` succeeds but the robot reacts to the wrong side, inspect scan angle conventions and the laser-to-base transform before changing gains. Following the nearest scan object is not identifying a particular person. [LiDAR course and exact calls](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/3_LiDAR_Course.html).

#### 2D SLAM, saved maps, AMCL and Nav2

The 2D mapping path combines LaserScan with odometry and TF. `slam_toolbox` estimates a pose graph and occupancy grid; a saved PGM/YAML occupancy map and a serialized pose graph are different artifacts. Leg slip or an incorrect body/laser transform can bend walls even when every scan looks individually plausible.

1. Use the known factory sensor/controller configuration and a stable mapping posture. Confirm fresh scan, odometry and a connected `odom → base` chain before mapping.
2. Start `ros2 launch slam slam.launch.py`; on the visualization host start `ros2 launch slam rviz_slam.launch.py`. Check the displayed fixed frame and scan alignment before teleoperation.
3. The supplied keyboard node is `ros2 launch peripherals teleop_key_control.launch.py`. Make short, slow translations/turns around textured, static geometry; close a loop and compare the revisited wall locations. Pause to let the estimator catch up rather than driving faster through a delayed map.
4. Save a distinct map name. The manufacturer's command runs in `~/ros2_ws/src/slam/maps`:

```bash
ros2 run nav2_map_server map_saver_cli -f map_01 --ros-args -p map_subscribe_transient_local:=true
```

The expected result is both a map image and YAML referencing that image. Reopen them before deleting or overwriting anything. For navigation use `ros2 launch navigation navigation.launch.py map:=map_01` and `ros2 launch navigation rviz_navigation.launch.py`. Seed the actual robot pose with **2D Pose Estimate**, compare live scan against known walls, then choose one nearby goal. The initial pose tool localizes; a goal tool requests motion. A stale map origin is not repaired by clicking farther-away goals.

AMCL maintains a distribution of plausible poses on a known map. The global planner uses the map/costmap to propose a route; the local controller reacts to nearby obstacles and the current state. The course discusses A\* and dynamic-window planning as concepts; inspect the actual `nav2_params.yaml` plugin names and velocity/footprint settings before claiming that a particular plugin is running. If the global route looks reasonable but movement oscillates, check localization, scan freshness, footprint and actual commanded/achieved velocity before changing global-planner settings. Record cancellation and stopping behavior before multi-goal operation. [Mapping and navigation course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/5_Mapping_and_Navigation_Course.html).

#### RTAB-Map visual mapping and navigation

The 3D path adds RGB/depth and visual features. Use `ros2 launch slam rtabmap_slam.launch.py` with `ros2 launch slam rviz_rtabmap.launch.py`; the supplied navigation pair is `ros2 launch navigation rtabmap_navigation.launch.py` and `ros2 launch navigation rviz_rtabmap_navigation.launch.py`. Preserve the mapping database with the associated camera calibration, frame tree and robot configuration instead of treating a 2D map filename as the entire 3D state.

First inspect a stationary point cloud and registered imagery. Walk a small loop with visible features, then require the return view to localize consistently. Textureless walls, glare, moving foregrounds, depth holes and timestamp mismatch can break visual odometry without a network failure. A successful RViz cloud does not establish successful loop closure. Return to the camera/TF checkpoints if depth appears scaled or offset; do not retune navigation around a distorted reconstruction. [RTAB-VSLAM chapter](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/5_Mapping_and_Navigation_Course.html#_5-1-3-rtab-vslam-3d-mapping).

### ROSpider vision, machine learning and manipulation reference

#### LAB thresholds and the shared color detector

The color pipeline downsamples/blurs RGB, converts to LAB, thresholds a selected color and applies opening/closing before selecting a contour. Thresholding, contour quality and motion control are separate stages. Start the camera and `python3 ~/software/lab_tool/main.py`; adjust the selected color while looking at its binary mask under the actual illumination, then save the configuration. Keep the old `~/software/lab_tool/lab_config.yaml` so a new lighting setup has a rollback.

The shared detector publishes `interfaces/msg/ColorsInfo` on `/color_detect/color_info` and an annotated image on `/color_detect/image_result`. Consumers configure detection/ROI through `/color_detect/set_param` and related ROI services. A detected color center is an image measurement, not automatically a point in the arm or map frame. Observe the mask and contour against one target before enabling a consumer. Remove competing target-colored objects during a controlled trial; if glare fragments the contour, change illumination/thresholds before increasing a tracking gain. [OpenCV course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/6_ROS+OpenCV_Course.html).

| Activity / launch                                | Architecture and input                                             | Expected result, parameters and failure isolation                                                                                                                   |
| ------------------------------------------------ | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `example color_recognition_node.launch.py`       | Shared LAB detector plus a recognition consumer                    | Annotated object/color and buzzer; the supplied lesson can also actuate arm servos for recognized colors, so it is not a passive detector                           |
| `example color_position.launch.py color:=red`    | Selects a color and reports its contour location                   | Compare image coordinate movement with a known target; inspect the actual executable because copied outcome prose repeats recognition behavior                      |
| `app object_tracking_node.launch.py debug:=true` | Image/color selection, PID/control output to `/controller/cmd_vel` | Enter `/object_tracking/enter`, select the target in the view, then deliberately enable `/object_tracking/set_running`; movement is a separate stage from selection |
| `app line_following_node.launch.py debug:=true`  | LAB mask/weighted line ROIs plus LiDAR checks and velocity output  | Enter and enable `/line_following`; confirm the selected line mask and obstacle threshold before a clear-floor run                                                  |
| `example kcf.launch.py`                          | User-selected image ROI initializes a KCF tracker                  | Box follows appearance; a drifting box is not object identity. Select a distinctive target, then stop/reselect after occlusion                                      |

For the stateful tracking and line applications, `/set_running` uses `std_srvs/srv/SetBool`. In the pinned **object-tracking** callback, **false** publishes a zero `Twist` and then `traveling(gait=-2, time=1, steps=0)`. In the **line-following** callback, that zero velocity plus posture reset occurs on **every call, including true**. Gait −2 requests a one-second leg transition to `DEFAULT_POSE`: clear the leg sweep before disabling tracking or enabling/disabling line following, and allow the reset to complete. These services are not torque-off or motionless-stop controls. Check the installed callback, service type with `ros2 service type`, and fields with `ros2 interface show` before use. The line code combines color tracking with `/scan` and a stop threshold; a narrow camera ROI or missing scan should be diagnosed before changing steering gain. [Tracking callback](https://github.com/Hiwonder/ROSpider/blob/490080f9bb03e702ba87c843c730c6866877cc17/src/app/app/object_tracking.py), [line-following callback](https://github.com/Hiwonder/ROSpider/blob/490080f9bb03e702ba87c843c730c6866877cc17/src/app/app/line_following.py), [posture-reset implementation](https://github.com/Hiwonder/ROSpider/blob/490080f9bb03e702ba87c843c730c6866877cc17/src/driver/controller/controller/move_controller.py).

#### AprilTags, pose estimation and AR

`example apriltag_recognition.launch.py` consumes RGB and CameraInfo, detects a tag and publishes `ApriltagsInfo` plus an annotated image. `example ar.launch.py` projects graphics using that estimated pose; it does not create a measured 3D object. `example apriltag_position.launch.py` reports a tag position, while `example apriltag_track.launch.py` adds physical following. The tracking lesson targets tag 1 in its documented demonstration; verify the installed target-ID selection rather than expecting every printed tag to be followed.

Use a flat, known-size tag from the intended family, measured in the units expected by the installed detector. Confirm ID/corners at rest, then check pose consistency while moving the tag a known small distance. Incorrect tag size scales the translation estimate; wrong camera intrinsics or distorted corners corrupt pose even when the ID is correct. Verify tag pose before arm/chassis motion. Compare the detector's camera frame to base/map frames explicitly. If AR overlays jitter while ID remains stable, inspect illumination, tag flatness, intrinsics and distance rather than servo offsets. [AprilTag recognition, AR, positioning and tracking](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/6_ROS+OpenCV_Course.html#_6-3-apriltag-tag-recognition).

#### Dataset collection, YOLO training and TensorRT

The learning course includes model/framework concepts, GPU acceleration, TensorRT, image collection/annotation, conversion, training/export and waste classification. Its references to particular YOLO versions are tutorial/software revisions, not a reason to replace the robot's working CUDA/JetPack environment.

For a custom detector, start the camera and the supplied `~/software/collect_picture/main.py`, collect the intended object against several backgrounds and separate evaluation images from training images. Use `~/software/roLabelImg/roLabelImg.py` to annotate the correct object/class. The course's `~/third_party/yolo/xml2yolo_obb.py` converts its XML/rotated-box dataset; retain the label schema and class-order YAML with the weights. A rotated-box conversion is not interchangeable with ordinary axis-aligned labels merely because both are text files.

The published training illustration uses 640-pixel input, batch 16 and 300 epochs. Those are example settings, not a memory guarantee for this robot or a requirement to train onboard. Confirm the actual script's options and a small training/evaluation run before a long job. Export using the matching YOLO/TensorRT environment, then retain GPU/runtime/precision/input-shape information with the `.engine`; a serialized engine is not universally portable across JetPack or GPU generations.

The wiki writes `yolo_detect.launch.launch.py` in one command; the reviewed repository contains **`yolo_detect.launch.py`**. Confirm installed launch files before use. `garbage_classification.launch.py` is a subsequent robot application, not merely an offline accuracy evaluator. Require correct labels and timestamps on recorded/stationary images before allowing those labels to select physical actions. Diagnose class-order errors, preprocessing shape, engine/runtime mismatch and latency independently. [Learning/data/export course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/7_ROS+Machine_Learning_Course.html), [published detector resources](https://github.com/Hiwonder/ROSpider/tree/490080f9bb03e702ba87c843c730c6866877cc17/src/example/example/yolo_detect).

#### Reproducible detector data and export workflow

Keep a project directory containing the photographs, annotation files, `data.yaml`, class list, training settings, weights and exported engine. Split by capture session or scene so adjacent frames of the same object do not inflate evaluation accuracy. In the supplied workflow, XML annotations are converted using:

```bash
python3 ~/third_party/yolo/xml2yolo_obb.py --data ~/my_data --yaml ~/my_data/data.yaml
```

**Expected result:** converted labels whose class IDs and rotated-box geometry agree with the dataset YAML. Open several converted samples before training; the number of coordinates per label must match the selected detector task. The manual's training command is a revision-specific example, `python3 ~/third_party/yolo/train.py --img 640 --weights yolo26n.pt --data /home/ubuntu/my_data/data.yaml --batch 16 --epochs 300`. Check that exact script and weight file exist before using it. Training memory demand depends on batch, image shape, model and installed runtime; reduce the workload only through the script's documented options, retaining the resulting experiment record. [Dataset/conversion/training course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/7_ROS+Machine_Learning_Course.html#_7-2-6-data-format-conversion).

The export example runs `python3 export.py --weights best.pt --include engine --imgsz 640 --device 0` from its matched training/export directory. Confirm the resulting file's input shape and precision and evaluate it on held-out images before robot integration. In the inspected ROS launch, `camera_topic` selects the image input and `conf` defaults to 0.6. `model_name` is a **selector**: names containing `garbage` choose `best_garbage_26.engine` with the oriented-box task; `traffic` chooses its traffic engine/class list; other names choose `yolo26n.engine` and the general detector class list. It does not automatically load an arbitrary `best.engine` merely because `model_name:=best` was supplied. Custom integration must explicitly match the node's `engine`, `classes` and `task` parameters to the exported artifact. [Inspected launch selection](https://github.com/Hiwonder/ROSpider/blob/490080f9bb03e702ba87c843c730c6866877cc17/src/example/example/yolo_detect/yolo_detect.launch.py).

A boxed object with the wrong label usually calls for a class-order/preprocessing check before retraining. An engine-deserialization error calls for runtime/GPU/version inspection. Correct boxes with delayed motion call for end-to-end timestamp/latency inspection. These failures occur at different layers; preserve an image and parameter record for each test rather than changing the model, controller and thresholds together.

#### MediaPipe hand, face and body applications

| Lesson                        | Input / processing                                  | Output and operating check                                                                                                |
| ----------------------------- | --------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `finger_trajectory.launch.py` | Hand landmarks and fingertip point history          | Drawn path/trajectory interpretation; check landmark continuity before classifying a gesture                              |
| `hand_detect.launch.py`       | Hand detector and geometric finger relationships    | Recognized hand/gesture overlay; verify the label across several poses and distances                                      |
| `hand_gesture.launch.py`      | Landmark-derived finger angles select robot actions | Inspect the selected action mapping first; it can move the robot after recognition                                        |
| `face_track.launch.py`        | Face-center error drives arm/pan-tilt motion        | Target face/keypoints plus tracking; an annotated face is distinct from correct physical direction                        |
| `pose_control.launch.py`      | Human body landmarks and geometric posture gates    | Documented raised-arms preparation, horizontal-arms imitation and crossed-arms exit; front legs can move during imitation |

Use a single well-lit subject, keep the entire required hand/body region in frame and verify the label/landmark overlay before coupling it to an action. Gesture confidence is not an electrical stop function. If tracking oscillates, distinguish missed detections and processing delay from controller gain; increasing gain cannot repair an intermittently lost target. Body imitation maps a detected human pose into a limited robot motion, not a full human skeletal reconstruction. [MediaPipe course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/7_ROS+Machine_Learning_Course.html#_7-3-mediapipe-human-robot-interaction).

#### Arm tracking, kicking, navigation transport and 3D tasks

The arm vision lessons combine the color detector, servo publisher and `/arm_kinematics` services. Their example arm IDs are **19–24**, separate from leg numbering. Preserve the exact servo model/ID map and reference pose; do not treat a raw position value as degrees or reuse a leg ID as an arm joint.

| Workflow                                                                                 | Essential processing and configuration                                                     | Expected checkpoint / recovery                                                                                                       |
| ---------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| `color_track_node.launch.py`                                                             | Color-center PID plus arm IK/servo commands                                                | Arm follows a selected color after controller and arm-kinematics readiness; inspect correct color/center before tuning PID           |
| `app intelligent_kick_node.launch.py debug:=true`                                        | Color selection, chassis approach and kick state machine                                   | Enter `/intelligent_kick`, choose the target, then enable its SetBool running service; use one light ball in a clear level test area |
| `automatic_pick.launch.py debug:=pick` then `navigation_transport.launch.py map:=map_01` | Calibrated pick/place offsets, map localization, navigation goal and arm action sequencing | Validate pick in place, destination pose and place independently before a complete transport cycle                                   |
| `track_and_grab.launch.py`                                                               | Color/RGB selection, valid local depth patch, camera-to-arm transform and IK               | First compare computed 3D target with a stationary known object; only then execute an unloaded approach                              |
| `object_classification.launch.py debug:=true`                                            | Calibrated support-plane depth, shape/color classification and grasp/place actions         | Save `config/object_classification_plane_distance.yaml`; confirm plane/shape labels with a single object before sorting              |
| `object_volume_measurement.launch.py debug:=true`                                        | Depth-derived dimensions and geometric volume model                                        | Check a measured cuboid/sphere/cylinder independently; result is an estimate, not a metrology certification                          |

The grasping source averages valid depth pixels around a selected center and converts millimeters to meters. A window with no valid pixels must be treated as missing measurement, not a zero-distance target. It includes an illustrative 1 cm RGB/depth/frame correction; do not transplant that as a universal camera calibration. Check extrinsics, depth registration, gripper TCP and offsets on the actual assembly.

Navigation transport passes map-frame destination data through a `SetPose2D` service and uses `/automatic_pick/pick` and `/automatic_pick/place` triggers. Its destination x/y are meters; the documented named-location configuration stores roll/pitch/yaw in degrees before quaternion conversion. Record the map name/origin with each location. A grasp offset is in the pick geometry; moving a navigation waypoint is a different correction. With a monocular camera, the manufacturer changes an action group because metric depth is absent; that branch does not inherit the RGB-D solver's spatial accuracy. [Arm/3D course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/8_Robotic_Arm_Vision_Applications.html).

#### Depth-based fall prevention and bridge crossing

`prevent_falling.launch.py` and `cross_bridge.launch.py` compare depth regions with a calibrated surface/bridge baseline and can move autonomously. The manufacturer requires a **`debug:=true` calibration on initial setup or relocation**, then the ordinary launch reuses that location's baseline. A changed camera angle, body height, surface or bridge geometry invalidates that assumption.

Validate the image regions and valid-depth behavior on a broad, level, protected test surface first. Confirm the expected stop/turn output before any edge-like test fixture; do not use an actual unprotected drop to prove the function. Glare, dark surfaces, holes in depth and a tilted camera can resemble a discontinuity. Keep unknown depth distinct from known flat ground. These educational applications do not establish reliable cliff detection, balance margin or fall protection for arbitrary terrain. [Depth terrain lessons](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/8_Robotic_Arm_Vision_Applications.html#_8-5-3d-vision-fall-prevention).

### ROSpider voice, model applications and simulation reference

#### Six-microphone speech resources and deterministic movement

The assigned Ultimate kit includes the six-microphone path. The offline speech lesson uses `xf_mic_asr_offline`; its language/wake resources and application ID must match the installed package. Preserve the original `common.jet` and launch configuration before replacing them. The course copies a provider-issued `common.jet` into `~/ros2_ws/src/xf_mic_asr_offline/config/msc/res/asr/` and sets the matching APPID in `launch/mic_init.launch.py`. Account eligibility, service term and resource availability are provider-side conditions; the robot does not make an expired or unsupported resource valid.

Start `ros2 launch xf_mic_asr_offline voice_control_move.launch.py` only after camera/controller ownership is clear and the robot is in a suitable motion area. The launch includes controller, LiDAR and microphone initialization, then maps recognized words into movement behavior. First verify wake indication and recognized text while prepared to stop, then use one short supported command and its stop command. If words are correct but motion is wrong, inspect the action/velocity mapping; if no words arrive, inspect microphone selection, audio device, language/resource/APPID and wake configuration before changing gait code. [Voice course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/9_Voice_Control_Course.html).

For the six-microphone version, the public course changes recognition language in the desktop **Tool**: select the intended language, **Save → Apply → Quit**, then restart as instructed. Its default English wake phrase is “Hello Hiwonder.” WonderEcho Pro instead requires its matching language firmware; that flashing branch is not a six-microphone update procedure. Attach the array with the supplied bracket/cable routing and the manual's four M4 fasteners, keeping the connector and microphone openings unobstructed. [Mounting and language selection](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/9_Voice_Control_Course.html#_9-1-voice-device-installation).

#### LLM, ASR, TTS, VLM and embodied actions

The course distinguishes text-model calls, speech recognition, speech synthesis, image understanding/OCR, structured detections and tool-driven robot applications. Keep these stages separate. Test a text reply, a saved audio result and an annotated static image without robot tools before allowing a model result to select movement. Source example model IDs/endpoints are revision-specific; confirm provider availability and keep keys private rather than publishing the example configuration.

On the delivered ROS stack the configuration lives at `~/ros2_ws/src/large_models/large_models/large_models/config.py`. Set the microphone type to **`xf` for the six-microphone array**; `WonderEcho Pro` is a different hardware lane. Save/apply through the model configuration tool and record the selected module. An ASR transcription, an LLM action string and a successful motion-service response are separate checkpoints.

| ROS application                                   | Function and dependencies                                                                  | Before executing it                                                                                  |
| ------------------------------------------------- | ------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| `llm_control_move.launch.py`                      | Voice/model result → supported movement action; wake/TTS state coordinates the turn-taking | Verify recognized action and controller owner; unknown output must not become an arbitrary command   |
| `llm_visual_patrol.launch.py`                     | Language selects an existing line-following behavior                                       | Calibrate the line detector and test its stop path independently                                     |
| `llm_color_track.launch.py`                       | Language selects the color/object-tracking behavior                                        | Verify LAB selection and physical tracking direction first                                           |
| `vllm_with_camera.launch.py`                      | Camera frame plus prompt → recognition/description result                                  | Confirm current frame/topic and expected stationary target; network delay is not current sensor time |
| `vllm_track.launch.py`                            | Model visual result drives tracking commands                                               | Validate bounding box/target identity and reject stale results before coupling to motion             |
| `vllm_navigation.launch.py map:=map_01`           | Named places → map-frame navigation goals                                                  | Re-localize on that map and check each named destination numerically                                 |
| `vllm_navigation_transport.launch.py map:=map_01` | Navigation plus calibrated `automatic_pick` sequence                                       | Verify grasp/place and route separately; model interpretation does not calibrate the arm             |

The source connects `agent_process/result`, wakeup and `tts_node/play_finish` state, and exposes model/prompt configuration services. Interrupt behavior is an explicit parameter in several examples, not a universal cancel guarantee. A cloud timeout, wrong microphone version, stale image, navigation failure and arm calibration failure should produce different diagnostic records. Inspect logs without exposing API keys. Record map origin and target units—meters for destination x/y, documented degrees for named-location angles—before letting a natural-language name select a waypoint. [Complete large-model course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/11_Large_AI_Model_Course.html).

#### Standalone model lessons: text, speech, images and tools

The basic examples live under `~/large_models`, separate from the ROS workspace's `large_models` package. Their `config.py` and microphone-port selection must match that standalone copy. Retain the vendor-provided dependencies and inspect them before installing a newer package: an API-compatible-looking client does not establish that the manufacturer's speech wrapper supports a current provider endpoint. The named files below are the course's revision-specific entry points, not a claim that every cloud service/model was exercised during this review. [Basic-model course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/11_Large_AI_Model_Course.html#_11-1-large-models-basic-courses).

| Entry point / task           | Input → output                                            | Meaningful acceptance and settings                                                                                                                                                                |
| ---------------------------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `openai_llm_demo.py`         | Prompt → generated text                                   | Read the configured provider/model, submit a small factual prompt and retain the returned text/error; no robot controller is needed                                                               |
| `openai_llm_nlu_demo.py`     | Passage → summary                                         | Compare the summary against the supplied passage; omitted or invented claims are distinct from an API transport failure                                                                           |
| `openai_llm_er_demo.py`      | Written emotional expression → text response              | This illustrates interpreting language; it does not measure a person's physiological or psychological state                                                                                       |
| `wakeup_demo.py`             | Selected microphone/serial wake device → wake event       | Match the physical device and port, then confirm one wake indication before adding ASR                                                                                                            |
| `openai_asr_demo.py`         | Captured speech → transcript                              | The shown wrapper sets language `en`, threshold 0.2, prefix padding 300 ms and silence duration 800 ms; these are tutorial wrapper settings, not verified settings for every current provider API |
| `openai_tts_demo.py`         | Text → audio file/playback                                | Confirm a new file in `~/large_models/resources/audio/`, then playback/output-device selection independently                                                                                      |
| `openai_interaciton_demo.py` | Wake → ASR → text model → TTS                             | The spelling `interaciton` is the documented filename; identify where a turn stops before changing microphone and model settings together                                                         |
| `qwen_vllm_detect_demo.py`   | Saved picture plus prompt → located objects/boxes         | Verify image dimensions, bounding-box coordinate convention and actual object identities on the retained picture                                                                                  |
| `openai_vllm_understand.py`  | Saved picture → scene description                         | Keep image and prompt with the output; a plausible description is not proof of current sensor state                                                                                               |
| `openai_vllm_ocr.py`         | Saved text-bearing picture → extracted text               | Compare exact characters against the image before using them as a label or destination                                                                                                            |
| `openai_agent_demo.py`       | Speech/task prompt → structured function/action selection | Inspect generated fields and allow only documented tools; the agent example can request movement and is not a passive chat test                                                                   |

Run a present, matched example from `~/large_models` using `python3` and its exact filename. First establish a small text-only response, then a saved image response, then audio; only afterward enable a robot tool. For image lessons, the working directory matters because source paths such as `./resources/pictures/ocr.jpeg` are relative. A file-not-found error is not a failed visual model. Replace a picture path and inspect its dimensions before invoking the provider; retain one test image and expected visible labels as a regression checkpoint.

For ASR/TTS, check microphone capture and speaker playback separately. A wake word with no transcript suggests capture/VAD/service configuration; a correct transcript with no audible reply suggests TTS/output-device or playback state. Avoid logging credentials when recording a service error. The tutorial's function-call example introduces machine-readable action selection; production code still needs schema validation, known action names, numeric bounds and a stop path before dispatch. Model text must never be evaluated as Python or shell code. This is an engineering control boundary, not a claim that the educational source implements every safeguard.

For the ROS applications in the preceding table, the complete command form is `ros2 launch large_models_examples <listed-launch-file>`, followed by the documented arguments such as `map:=map_01`. Check readiness in sequence: microphone/wake state, transcript, `agent_process/result`, selected application, then controller response. The smart-home assistant lesson uses named map locations through `vllm_navigation`; it is navigation to configured places, not proof of compatibility with an arbitrary external home-automation hub. For intelligent transport, use the `large_models_examples automatic_pick.launch.py` pick/place debug branches belonging to that workflow, calibrate each stage and only then run `vllm_navigation_transport.launch.py` on the saved map. Do not substitute the similarly named `example` package's pick node without checking its service/configuration contract. [Embodied application lessons](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/11_Large_AI_Model_Course.html#_11-3-embodied-ai-applications).

#### URDF, MoveIt 2, Gazebo and physical synchronization

The simulation course imports a manufacturer VM/workspace, then separates description, planning and real-robot synchronization. On a virtual machine, `robot_moveit_config demo.launch.py` provides a planning scene; `robot_gazebo worlds.launch.py` provides the Gazebo environment. Match the robot URDF/Xacro joint names, limits, mesh scale and arm/tool geometry before comparing a plan with the physical robot. A URDF visual mesh is separate from collision geometry and inertial properties.

The documented VM import opens the supplied virtual-machine artifact in VMware, selects a storage directory and waits for import. The lesson chooses a bridged network adapter and disables accelerated 3D graphics in that VM's display settings. Treat those as settings for the supplied image, not a universal host GPU recommendation. Verify the archive provenance and keep its `.typerc` configuration with the workspace. After placing the supplied `simulations` package under `~/ros2_ws/src`, the documented build is:

```bash
cd ~/ros2_ws
colcon build --symlink-install
source ~/ros2_ws/install/setup.bash
```

**Expected result:** the simulation packages build successfully and their launch files are discoverable in that terminal. This command was not executed here; the source/image archive and host graphics compatibility remain conditions to check on the intended machine. Inspect the supplied `.typerc` before sourcing it. For isolated simulation, keep its domain separate from the robot; for deliberate physical synchronization, set the two actual `ROS_DOMAIN_ID` values equal and verify both machines are on the same reachable subnet. The course's domain value 10 is an example, not a model identity. [VM/workspace setup](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/10_Movelt_&_Gazebo_Simulation.html#_10-2-configuration).

For MoveIt, first inspect the current state, choose a nearby reachable target, plan without execution and examine every intermediate joint posture and the planning-scene obstacles. Add the actual table/tool or other collision objects before relying on collision checking. An Allowed Collision Matrix entry can disable checking for a pair; it is not proof the physical pair cannot collide. Joint goals, Cartesian waypoints and random targets exercise different reachability/path constraints. A displayed successful plan does not qualify payload, foot support, cable clearance or a real stop.

Physical synchronization additionally requires the VM and robot to share network reachability and `ROS_DOMAIN_ID`, and a correctly configured controller/trajectory path. The manufacturer's sequence starts `controller controller.launch.py` on the robot and the MoveIt demo on the VM; that crosses from visualization into possible actuation. Keep simulated tests on a separate domain while establishing geometry, then deliberately connect the verified real controller only in a cleared workcell. Incorrect state feedback or a mismatched joint order must be fixed before Execute; do not “test” it with a large random pose. [MoveIt/Gazebo course](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/10_Movelt_&_Gazebo_Simulation.html).

#### NX system-image recovery and preserved robot data

For this assigned Orin NX kit, the manual's recovery medium is an **M.2 NVMe SSD**, accessed through an appropriate external enclosure/programmer. The microSD branch is for the older Jetson Nano and Raspberry Pi options; it is not the NX workflow. The manufacturer describes Windows 10 with DiskGenius and Win32DiskImager. Obtain the exact host/robot image through the order-number resource channel before removing the working SSD. No NX image checksum was publicly established in this review. [Recovery preparation and image writing](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html#_1-9-image-burning).

1. While the existing system is reachable, save the software version, network settings, `.typerc`, calibration YAMLs, servo deviations/action groups, maps/RTAB-Map database, model artifacts and microphone configuration. Verify the backup can be opened on another machine.
2. Shut down and disconnect robot power before removing the SSD. Record its label/capacity and identify that same device in the enclosure; compare the destination capacity and drive letter in Windows. Prefer a spare matching medium so the original remains available.
3. Extract the matched image to a path containing only ASCII characters. Read the image/tool instructions and identify its required capacity before any write.
4. The manual describes deleting old partitions with DiskGenius when initialization is required, and explicitly permits skipping that step on a new unpartitioned medium. Partition deletion erases that destination; do not apply it to an unidentified disk or the only copy of robot data.
5. In Win32DiskImager, choose the uncompressed image with the folder control, choose the verified target under **Device**, then use **Write** only after those identities match. The documented completion indication is **Write Successful**. Cancel Windows prompts to format Linux partitions afterward.
6. With power disconnected, reinstall the SSD, restore the intended starting posture and boot. Recheck the version/host configuration, network and passive sensor result before restoring custom behavior. Copy back only configuration compatible with that image; a saved calibration from a different camera mount is not automatically valid.

**Expected result:** a matched system boots and reaches the same stationary first-result checkpoint. A write-complete dialog alone does not validate the image, controller firmware, sensor assignment or restored calibration. If writing fails, inspect storage identity/capacity, enclosure connection and the image/tool error before repeating; a disk-format prompt after a successful Linux image write is not a request to erase it.

#### Cross-course diagnostic sequence

For a combined task, preserve a record at each boundary: current sensor timestamp/encoding → detector label/coordinates → frame transform and units → reachable kinematic target → selected controller/action → observed stopped result. If a color task fails, inspect its mask before retraining a model. If a model labels correctly but grasping misses, inspect depth/TF/TCP before changing prompts. If a goal is correct but the robot drifts, inspect localization and gait/odometry before rewriting the application. Keep the working image, calibration YAMLs, maps/database, action groups and model/runtime revisions together so recovery restores a coherent system.

The procedures and parameter interpretations in this reference are source-reviewed. No launch, calibration, model training, SDK compilation or physical experiment was performed for this guide. Provider-account screens, linked video demonstrations and gated image/source archives are references rather than observed execution results.

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

| Failure                                        | Check and recovery                                                                                              |
| ---------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Network LED flashes but app is not ready       | Wait for full ROS boot and buzzer/posture completion; network initialization finishes earlier                   |
| Hotspot absent                                 | Check host boot via Jetson Type-C network path before resetting Wi-Fi; inspect `wifi_manager` configuration     |
| Remote desktop works, standalone example fails | Check sourced ROS environment, `need_compile`, package prefix and ownership of `start_app_node.service`         |
| No scan/depth messages                         | Inspect cable enumeration and one driver at a time; compare local ROS topics before remote networking           |
| Servo buzzes or leg does not support body      | Stop; inspect initial posture, blocked linkage, power and servo ID before adjusting gait or deviation           |
| Mapping drifts during a walk                   | Check IMU, posture/TF and gait repeatability on a level floor; do not use a wheeled odometry correction blindly |
| Voice hardware present but silent              | Confirm Ultimate six-mic `xf` configuration and audio devices; WonderEcho Pro is a different branch             |
| App stops after development                    | End custom nodes and restart the documented service; do not start duplicate controller processes                |

**Is calibration required out of the box?** The manual states factory servo deviations are set. Read and back up them before any correction; wrong neutral positions can cause contact or stall.

**Does Ubuntu recovery restore calibration and maps?** A factory image can replace local files. Back up workspace configuration, maps, servo deviations, network and microphone settings first. Obtain the exact NX image rather than formatting an SSD during troubleshooting. [Image recovery and maintenance](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html#_1-9-image-burning).

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

| Resource                                    | Official destination                                                                                                                                                                                         |
| ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Complete robot manual/courses               | [ROSpider wiki](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html)                                                                                    |
| System image and full robot source          | [Appendix access instructions](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/Appendix.html): request using the order number; no verified public NX image checksum was exposed |
| Resource archive                            | [ROSpider Resources](https://drive.google.com/drive/folders/1QyAc-yD6L8jeZ0Vc2YKaD2uVBy3EqQrz?usp=sharing)                                                                                                   |
| Hardware/servo/microphone files             | [Official Hardware Materials folder](https://drive.google.com/drive/folders/1SHBySUxUyhu8klCVsFCp_3jWskAuYuTP?usp=sharing)                                                                                   |
| Power/socket diagram                        | [User manual port descriptions](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/1_ROSpider_User_Manual.html#_1-2-2-port-descriptions-key-focus)                                 |
| Camera-specific material                    | [Aurora930 Pro wiki](https://wiki.hiwonder.com/projects/Aurora930-Pro/en/latest/index.html)                                                                                                                  |
| Kinematics, RRC implementation and examples | [Motion course embedded source](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/2_Motion_Control_Course.html); full installed driver in matched robot image                     |
| CAD/URDF/simulation                         | [Simulation chapter](https://wiki.hiwonder.com/projects/ROSpider/en/jetson-orin-nano-version/docs/10_Movelt_&_Gazebo_Simulation.html); resource archive above for supplied model assets                      |

### Additional established resources

These established links supplement the model-specific resources above. Retain the matching model, host and revision when selecting a download.

* [manufacturer product data](https://www.hiwonder.com/products/rospider)
* [Official source repository — match branch and host](https://github.com/Hiwonder/ROSpider)

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

The exact catalog option, public manufacturer manual and substantive motion, sensing, mapping, vision, learning, arm, voice, model-application and simulation course content were reviewed and explained on-page. Critical power, host/STM32 routing, boot, network, app ownership, motion-source interfaces and mapping commands were source-reviewed; the numbered controller photograph was visually inspected. The public ROSpider repository was additionally reviewed at the stated commit. Matched system-image archives remain manufacturer-access resources; they were not booted or represented as compiled.

The original observation script passed syntax parsing only. No robot boot, SDK build, serial exchange, sensor accuracy check, calibration or walking test was run. This guide records commissioning checkpoints rather than claiming hardware outcomes. For the different Raspberry Pi hexapod, use [SpiderPi Pro](https://wiki.openelab.io/robotics/hiwonder/hiwonder-spiderpi-pro-development-guide); its app, software and power assumptions differ.
