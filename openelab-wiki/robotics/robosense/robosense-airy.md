---
description: >-
  Commission RoboSense Airy 96 sensor and kit, wire its 11-pin
  power/Ethernet/sync interface, verify UDP/cloud/IMU data and configure the
  exact RSAIRY ROS2 driver.
layout:
  width: default
  title:
    visible: false
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: true
  tags:
    visible: true
  actions:
    visible: true
  anchors:
    visible: true
---

# Robosense Airy

{% hint style="info" %}
[**View RoboSense Airy 96-Channel Hemispherical Digital LiDAR for Robotics on OpenELAB**](https://openelab.io/products/robosense-airy-96-channel-hemispherical-digital-lidar?variant=45547585208518)

**Model / option:** LiDAR with Sensor Kit · **SKU:** `RS-Airy96-kit`

[**View RoboSense Airy 96-Channel Hemispherical Digital LiDAR for Robotics on OpenELAB**](https://openelab.io/products/robosense-airy-96-channel-hemispherical-digital-lidar?variant=45547585175750)

**Model / option:** Only LiDAR · **SKU:** `RS-Airy96`
{% endhint %}

## Product overview

### RoboSense Airy 96 <a href="#robosense-airy" id="robosense-airy"></a>

**RoboSense Airy 96 is a rotating 3D LiDAR with a hemispherical 0–90° vertical field of view, conventional 100BASE-TX Ethernet and integrated IMU.** The goal here is a live, correctly decoded point cloud with separate evidence for networking, calibration, time and IMU data.

| Exact SKU       | Sold scope                                                                       |
| --------------- | -------------------------------------------------------------------------------- |
| `RS-Airy96`     | Airy 96 sensor-only                                                              |
| `RS-Airy96-kit` | Airy 96 plus power adapter/cord, aviation cable, RJ45 cable and listed fasteners |

The store also offers an accessory-only kit; it is not an additional sensor. Verify the received adapter/harness labels before wiring. Airy Lite and other channel configurations have separate decoders/specifications. [Exact store options and packing list](https://openelab.io/products/robosense-airy-96-channel-hemispherical-digital-lidar), [Airy manual](https://robosense-robotics.github.io/product-manual/en/Airy/).

## Applications

### Description and sensing tasks <a href="#description" id="description"></a>

Airy's upward hemisphere can supply nearby three-dimensional structure for AMRs, legged robots and indoor/outdoor SLAM. Mounting determines whether the useful coverage sees surrounding obstacles, overhangs or mostly the robot body. Establish the sensor-frame orientation on the bench before choosing a robot transform.

For a useful integration experiment, place a vertical board at a measured distance and record a stationary cloud in strongest-return mode. Compare geometry at different heights, then add one small controlled platform motion with synchronized IMU. Save the raw capture and calibration so later filter changes can be evaluated on the same scene.

The 60 m headline is not a 30 m dark-target guarantee across the whole hemisphere. Appendix D specifies channel-dependent ranging/offset behavior. Thin, wet or low-reflectivity objects need application-specific checks. Detection and navigation software require their own system validation; ingress and laser classifications do not certify the whole robot. [Manual §§2.3–2.5 and Appendix D](https://robosense-robotics.github.io/product-manual/en/Airy/).

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter             | Airy 96 scope                                                                              |
| --------------------- | ------------------------------------------------------------------------------------------ |
| Channels / wavelength | 96 /940 nm                                                                                 |
| FOV                   | 0–360° horizontal;0–90° vertical                                                           |
| Range / blind zone    | 60 m listed range;30 m at 10% NIST target;0.1 m blind zone                                 |
| Typical accuracy      | 1.5 cm,1σ; conditions in manufacturer specification notes                                  |
| Angular sampling      | 0.4° horizontal;0.947° vertical                                                            |
| Rotation / frame rate | 600 rpm /10 Hz                                                                             |
| Point output          | 856,320 points/s in current 96-channel specification; do not import 192-channel throughput |
| Data link             | 100BASE-TX Ethernet, UDP                                                                   |
| Supply / power        | 9–32 V DC /8 W typical                                                                     |
| Size / mass           | Base diameter 60 mm × height 63 mm;230±20 g sensor body                                    |
| Environment           | −40 to 60 °C operating;−40 to 85 °C storage; IP67/IP6K9K as specified                      |
| Synchronization       | GPS, PTP, gPTP; external master/source required                                            |

[Current Airy 96 manual §2.4](https://robosense-robotics.github.io/product-manual/en/Airy/#24-specifications1). Typical consumption is not the power supply's startup/current-limit rating. The manual's optional adapter is 12 V/3.34 A,40 W; confirm the supplied kit adapter rather than assuming every package contains that exact revision.

| Factory network / packet | Default                                           |
| ------------------------ | ------------------------------------------------- |
| Sensor / destination     | 192.168.1.200 /192.168.1.102; mask 255.255.255.0  |
| MSOP / DIFOP / IMU ports | 6699 /7788 /6688                                  |
| MSOP / DIFOP length      | 1248 /1248 bytes UDP payload                      |
| MSOP header / device ID  | `55 aa 05 5a`; type 0x31, model 0x02 for 96 beams |
| IMU length / header      | 51 bytes /`aa 55 5a 05`                           |

[Manual §§3.4,4.4](https://robosense-robotics.github.io/product-manual/en/Airy/). Packet reception and correct packet length are transport checks, not proof that channel angles, time and calibration have been applied.

## Hardware and connections

### Connector, power and sync are different electrical domains <a href="#interface-description" id="interface-description"></a>

Use the keyed 11-pin aviation connection with the matching Airy harness. Read pin numbers from the exact connector-face drawing in §3.3.1; the mating view reverses apparent order. The locating slot and pin 1 marker are explicit in the original figure. Connect or service the harness with power removed.

#### Aviation plug interface and definitions <a href="#aviation-plug-interface-and-definitions" id="aviation-plug-interface-and-definitions"></a>

| Airy sensor pin | Signal                   |
| --------------- | ------------------------ |
| 1 /2            | Ethernet RX+ /RX−        |
| 3 /4            | Ethernet TX+ /TX−        |
| 5 /8            | GND                      |
| 6 /7            | VIN,9–32 V supply domain |
| 9               | GPS PPS input            |
| 10              | SYNC\_OUT1               |
| 11              | GPS GPRMC input          |

[Exact connector table and face](https://robosense-robotics.github.io/product-manual/en/Airy/#331-aviation-plug-interface-and-definitions). On the documented splitter, Ethernet routes to RJ45 pins 1/2/3/6 and the supply branch uses the DC5.5 × 2.1 interface. Use the matched labeled adapter; do not inject power into Ethernet pairs.

For external GPS timing, this manual specifies **RS232 GPRMC**,9600 baud 8N1, and a **3.0–15.0 V positive PPS signal**. This is not the MID-360S 3.3 V LVTTL timing interface. Use a compatible timing source/level interface and common reference, inspect its output before connecting and leave the timing branch insulated for the first network test. The manual gives 20–200 ms PPS width and a specific GPRMC timing window; use that complete diagram when implementing GPS synchronization. [Manual §2.5.5](https://robosense-robotics.github.io/product-manual/en/Airy/#255-time-synchronization-method).

The housing and PCB share ground in the current Airy design. Review chassis bonding/isolation when mounting on a floating robot chassis; avoid making an accidental return path through a metal bracket. [Manual §3.3.3](https://robosense-robotics.github.io/product-manual/en/Airy/#333-power-interface).

### Mechanical and thermal integration <a href="#mechanical-installation" id="mechanical-installation"></a>

The current online manual specifies three M3 base screws with 4.5 mm protrusion,13±1 kgf·cm tightening torque, base flatness better than 0.15 mm and two 3 mm locating pins protruding 3 mm. Keep more than 2 cm cable slack, avoid clamping between top/bottom surfaces and provide a conductive thermal bracket. Bracket first modal frequency should exceed 50 Hz; thermal conductivity guidance is>50 W/(m·K). These values belong to the matching drawing/revision. Older retained drawings/text can have different locating-pin/tolerance callouts; obtain the drawing matched to the received serial before fabrication.

The store lists M4 fasteners in the accessory package; that does **not** authorize inserting M4 into the sensor's documented M3 holes. Check each fastener's intended location and engagement. [Current mechanical section](https://robosense-robotics.github.io/product-manual/en/Airy/#32-mechanical-installation), [store packing list](https://openelab.io/products/robosense-airy-96-channel-hemispherical-digital-lidar).

#### Interface cable (optional) <a href="#interfacecable-optional" id="interfacecable-optional"></a>

The documented Airy splitter has **A = 11-pin sensor plug**, **B = two-contact DC power**, **C = RJ45 Ethernet** and **D = four-contact timing**. Its current manual routing is below; the connector-face drawing determines contact numbering. The two VIN contacts share B1 and both return contacts share B2. Do not identify a power or GPS wire from color alone.

| A contact / signal | Conductor            | B power contact | C RJ45 contact | D timing contact / current color |
| ------------------ | -------------------- | --------------- | -------------- | -------------------------------- |
| 1 RX+              | 26 AWG, orange-white | —               | 1              | —                                |
| 2 RX−              | 26 AWG, orange       | —               | 2              | —                                |
| 3 TX+              | 26 AWG, green-white  | —               | 3              | —                                |
| 4 TX−              | 26 AWG, green        | —               | 6              | —                                |
| 5 GND              | 26 AWG, black        | 2               | —              | —                                |
| 6 VIN              | 26 AWG, red          | 1               | —              | —                                |
| 7 VIN              | 26 AWG, red          | 1               | —              | —                                |
| 8 GND              | 26 AWG, black        | 2               | —              | 4, black                         |
| 9 GPS PPS          | 30 AWG, purple       | —               | —              | 3, purple                        |
| 10 SYNC\_OUT1      | 30 AWG, blue         | —               | —              | 2, blue                          |
| 11 GPS GPRMC       | 30 AWG, yellow       | —               | —              | 1, yellow                        |

[Current manual §3.3.2](https://robosense-robotics.github.io/product-manual/en/Airy/#332-interface-cable-optional). The older wiki's yellow VIN, white ground and brown GPS conductor colors differ from this current harness table. Those color assignments are superseded for the current documented cable; retain the delivered assembly's label and continuity record rather than treating either color set as a universal pinout. The sensor-plug table and splitter table also give different wire gauges for some contacts; the table above describes the **splitter conductors**, not a wire-gauge requirement for a replacement sensor connector.

The installation manual recommends aluminum alloy thicker than **4 mm** or galvanized steel thicker than **2 mm**, stiffening ribs, and avoidance of sharp notches/corners below **0.3 mm** that concentrate stress. Verify bracket strength by simulation and evaluate its first structural mode above **50 Hz**. Use a conductive contact path and fins aligned with airflow; covering the base/top with insulating material defeats that heat path. These material thicknesses are design guidance, not a substitute for checking the actual bracket loads. [Mechanical requirements §3.2](https://robosense-robotics.github.io/product-manual/en/Airy/#32-mechanical-installation).

The old installation text gave 0.2 mm mounting flatness, 4–5 mm screw protrusion and Φ4 mm locating pins up to 4 mm high. The current manual instead specifies **<0.15 mm flatness, 4.5 mm protrusion and Φ3 mm pins protruding 3 mm**. Those current values control this guide; do not combine the old locating geometry with the current drawing.

### Calibration, return selection and timestamps

Use the device's DIFOP angle tables and IMU calibration, not a hand-generated evenly spaced 96-line model. The coordinate origin is at the center of the base; measure its transform into the robot. Retain ring and per-point time when the downstream algorithm needs them.

Current web controls offer strongest(default), first and last return. Do not infer simultaneous dual-return throughput from a different Airy release. Phase lock selects the rotational angle at a whole-second boundary,0–360°; it is not the same as point-cloud frame splitting or a calibrated camera trigger delay.

Select the intended GPS/PTP/gPTP mode and verify the diagnostics page reports lock. The current UI exposes PTP transport/delay/domain and lock thresholds; match the master instead of assuming every 1588 source interworks. Clock lock does not prove the master has correct UTC. [Manual §§2.5,4.1, Appendices A/C](https://robosense-robotics.github.io/product-manual/en/Airy/).

### Manufacturer drawings and retained diagrams <a href="#structural-drawing" id="structural-drawing"></a>

![Official Airy dimensioned structural drawing showing base M3 holes, locating features and optical-center offsets](https://robosense-robotics.github.io/product-manual/assets/airy-en/E.jpg)

RoboSense, current Airy manual Appendix E. This inspected drawing identifies three M3-P0.5-6H base holes with 4.5 mm minimum thread depth, a 60 mm nominal base diameter and the locating-feature sections. Use the complete toleranced drawing, not the nominal cylindrical envelope, when checking a bracket. The original wiki's native drawings below remain available for revision comparison.

<figure><img src="../../.gitbook/assets/image (345).png" alt="RoboSense Airy 96-Channel Hemispherical Digital LiDAR for Robotics manufacturer illustration from Mechanical Installation"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (346).png" alt="RoboSense Airy 96-Channel Hemispherical Digital LiDAR for Robotics manufacturer illustration from Mechanical Installation"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (348).png" alt="RoboSense Airy 96-Channel Hemispherical Digital LiDAR for Robotics manufacturer illustration from Aviation Plug Interface and Definitions"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (349).png" alt="RoboSense Airy 96-Channel Hemispherical Digital LiDAR for Robotics manufacturer illustration from InterfaceCable(Optional)"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (341).png" alt="RoboSense Airy 96-Channel Hemispherical Digital LiDAR for Robotics manufacturer illustration from Structural Drawing"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (343).png" alt="RoboSense Airy 96-Channel Hemispherical Digital LiDAR for Robotics manufacturer illustration from Structural Drawing"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (344).png" alt="RoboSense Airy 96-Channel Hemispherical Digital LiDAR for Robotics manufacturer illustration from Structural Drawing"><figcaption></figcaption></figure>

_Manufacturer drawings retained from this guide. Use the stated model/revision and the original manual when interpreting connector views and dimensions._

## Software and development resources

### Model-specific ROS2 target

The pinned SDK and its pinned decoder submodule both support **RSAIRY**. The code examples below target documented Ubuntu 22.04/ROS2 Humble. Dependencies include PCL,`yaml-cpp`≥0.5.2 and `libpcap`≥1.7.4. ROS2 also needs the official `rslidar_msg` package. A source ZIP without the decoder submodule is incomplete. [SDK README](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md).

| Setting                  | Airy 96 first-run value / purpose                                   |
| ------------------------ | ------------------------------------------------------------------- |
| `common.msg_source`      | 1 for live packets;3 for PCAP replay                                |
| `driver.lidar_type`      | `RSAIRY`, not the generic shipped `RSM1`                            |
| `msop_port`,`difop_port` | 6699,7788 unless the device was changed                             |
| `imu_port`               | 6688 when IMU parsing is built/enabled;0 disables it                |
| `min_distance`           | Review 0.2 m shipped filter; it can remove valid near-range returns |
| `use_lidar_clock`        | True only with a deliberate sensor-clock policy                     |
| `POINT_TYPE`             | Default XYZI; edit to XYZIRT when ring/time fields are required     |

IMU parsing is an explicit CMake option,`ENABLE_IMU_DATA_PARSE=ON`. Setting the UDP port alone does not compile that feature. The reviewed CMake file sets `POINT_TYPE` directly; change its documented line when selecting XYZIRT rather than assuming an unrelated launch argument changes the point structure. [Actual CMake](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/CMakeLists.txt), [configuration](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml).

RSView provides live display, PCAP recording/replay and table/CSV export; the manual notes LAS export from 3.1.3. It accepts PCAP, not PCAPNG. Firmware packages are obtained for the exact serial/revision; they are not bundled with an SDK source checkout. [Airy manual §4.3 and Appendix A](https://robosense-robotics.github.io/product-manual/en/Airy/).

### SDK configuration, recording and replay behavior

The pinned SDK uses one shared `common` block and one `lidar` list entry per sensor. For **Airy 96**, keep **`lidar_type:RSAIRY`** and the model-specific network/packet revision above. The receive-port baseline is **6699/7788/6688**; these are not permission to transfer a cable, wake signal or decoder from a similar model.

| Parameter                                          | Input / behavior to verify                                                                                                                              |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `common.msg_source`                                | 1 live UDP, 2 ROS packet messages, 3 PCAP; 0 is unused                                                                                                  |
| `send_point_cloud_ros` / `send_packet_ros`         | Enable decoded `PointCloud2` / raw packet publication independently; packet bags preserve the input needed for later decoder comparisons                |
| `min_distance`, `max_distance`                     | Software acceptance bounds in m; generic 0.2 m minimum may hide usable nearer points, while a large maximum never extends the product's optical rating  |
| `use_lidar_clock`                                  | true uses device time, false host time; neither selection itself locks GPS/PTP                                                                          |
| `dense_points`                                     | true removes NaNs; false retains invalid placeholders, affecting organized cloud indexing                                                               |
| `wait_for_difop`                                   | Hidden default true waits for configuration/calibration; disabling it can produce premature or incorrect geometry rather than fix a missing DIFOP route |
| `host_address`, `group_address`                    | Bind an intended host address and join the intended multicast group; only configure multicast if the actual model/network supports it                   |
| `pcap_path`, `pcap_repeat`, `pcap_rate`            | Absolute capture path, loop control and replay multiplier; use repeat false and rate 1.0 for a finite diagnostic pass                                   |
| `use_vlan`, `user_layer_bytes`, `tail_layer_bytes` | Strip a captured VLAN layer or known UDP wrapper lengths; leave wrapper counts zero for ordinary sensor packets                                         |
| ROS frame/topics                                   | `ros_frame_id`, packet receive/send and cloud topic names are independently configured; distinct sensors need unambiguous frames/topics                 |

These are host decoding/publication settings, not persistent device writes. The parameter prose and shipped examples disagree about the default `ts_first_point`; set it explicitly when the mechanical decoder uses first-versus-last point cloud stamping and verify against the selected decoder. `ros_send_by_rows` only applies to mechanical models with `dense_points:false`; it is not an extra MEMS channel setting. Preserve YAML indentation. [Explicit parameters](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/intro/02_parameter_intro.md), [hidden parameters](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/intro/03_hiding_parameters_intro.md).

For a reproducible replay, record **both MSOP and calibration DIFOP**, retain any enabled IMU stream and save the exact YAML/firmware/serial with the capture. Start a separate replay configuration with `msg_source:3`, the same decoder/ports, a real `pcap_path`, `pcap_repeat:false` and `pcap_rate:1.0`; verify that the cloud terminates at the end and has the same geometry as the live baseline. A ROS packet bag instead uses `msg_source:2` and the configured packet topic. Do not simultaneously bind a live receiver and replay consumer to an assumed shared socket. The documented PCAP path does **not support distinguishing multiple LiDARs using identical ports solely by different source IPs**; separate captures or ports before combining them. [Packet bag workflow](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/11_how_to_record_replay_packet_rosbag_CN.md), [advanced PCAP handling](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/09_pcap_file_advanced_topics.md).

Host XYZ/roll/pitch/yaw transforms require Eigen and compilation with **`ENABLE_TRANSFORM=ON`** before their configured values take effect. Keep them zero for the native-frame check; if enabled, publish a consistent frame and avoid applying the same extrinsic in TF again. Do not confuse a host coordinate transform with per-device optical calibration or a device's phase-lock setting. [Transform build and parameters](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/10_how_to_use_coordinate_transformation.md).

### Airy packet layout, per-channel timing and IMU units

The reviewed Airy measurement profile has a **42-byte header, eight 148-byte blocks, six-byte tail and 16 reserved bytes**, totaling the stated **1248-byte UDP payload**. The manual's tail paragraph omits those final reserved bytes; the pinned `RSAIRYMsopPkt` includes them explicitly. Its two-block pairing carries channels 1–48 then 49–96 at the same column azimuth. A channel contributes two range bytes and one reflectivity byte; use **`raw & 0x3FFF` × 0.005 m**, preserving the upper two feature bits. Treating all 16 bits as range or each 48-channel block as a full 96-channel column yields incorrect data.

The header time begins at offset 20 with six seconds bytes and four microseconds bytes. Each block also contains a big-endian 0.01° azimuth and `FF EE` flag. The native decoder applies per-channel angle/time calibration, lens-center offsets and its coordinate handedness; a generic XYZ conversion can look plausible while losing those corrections. [Manual §4.4 and Appendix D](https://robosense-robotics.github.io/product-manual/en/Airy/), [actual packed structures and decoding](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSAIRY.hpp).

| DIFOP offset / bytes              | Readback and interpretation                                                                                             |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| 8/2; 10/4; 14/4; 18/6; 24/2; 28/2 | Motor setpoint, source/target IPv4, MAC and MSOP/DIFOP ports                                                            |
| 40/5, 45/5, 50/5, 55/5            | Mainboard, baseboard, application and motor firmware identifiers                                                        |
| 292/6; 300/1                      | Serial and return mode                                                                                                  |
| 301/1, 302/1; 303/10              | Selected sync method, success state and seconds/microseconds time                                                       |
| 373/2                             | Real-time motor field; the appendix example has inconsistent arithmetic, so retain raw value and compare diagnostic RPM |
| 468/288, 756/288                  | 96 vertical/horizontal angle entries; sign byte then two-byte magnitude at 0.01°                                        |
| 1044/2, 1066/2, 1068/2; 1080/2    | Mainboard/device/baseboard voltages in raw/100 V, transmit temperature raw/100 °C                                       |
| 1092/28                           | IMU-to-cloud quaternion qx/qy/qz/qw and XYZ IEEE754 float32 transform                                                   |

These appendix numerical values use big-endian conversion. Sync mode **0/1/2/3/4** means GPS/E2E-L4/P2P/gPTP/E2E-L2; success state **0/1** means unlocked/locked. Firmware, selected mode and successful lock are separate facts to retain with a capture. [DIFOP and Appendix C definitions](https://robosense-robotics.github.io/product-manual/en/Airy/).

Appendix D's complete grouped firing offsets (µs) are: **channels 1–8: 0; 9–16: 5.712; 17–24: 12.376; 25–32: 19.040; 33–40: 25.704; 41–48: 33.320; 49–56: 41.888; 57–64: 50.456; 65–72: 59.024; 73–80: 70.448; 81–88: 81.872; 89–96: 93.296**. Its range table gives 30 m at a 10% target for channels 1–68 and 20 m for 69–96, with 60 m maximum throughout. The nominal angles run from −0.07° to 89.4°; use per-device DIFOP angles for reconstruction, not that nominal table as replacement calibration.

**Airy IMU has a unit boundary in the pinned software.** The 51-byte stream begins `AA 55 5A 05`, with time at 4, signed raw acceleration XYZ at 14/18/22 and gyro at 26/30/34. The manual converts acceleration as `raw × selected_g_range / 32768` in **g** and angular rate as `raw × selected_dps_range / 32768 × π/180` in rad/s. Its selector bytes at 42/43/44 identify output rate, accelerometer range and gyro range; rate codes 0–4 mean 25/50/100/200/1000 Hz. The decoder implements that g-scale acceleration, while this pinned SDK's ROS publisher forwards its acceleration fields without multiplying by **9.80665**. Therefore, do not assume the resulting Airy `sensor_msgs/Imu` acceleration already has ROS SI units. [Airy decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSAIRY.hpp), [ROS publisher](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/src/source/source_pointcloud_ros.hpp).

Before inertial fusion, examine a stationary gravity norm and confirm whether the selected path yields approximately **1 g** or **9.80665 m/s²**, while accounting for mounting and bias. Convert g to m/s² exactly once in a reviewed adapter or corrected driver, retain the original bag, and repeat the gravity check before estimating motion. This source-derived issue does not prevent the cloud-only checkpoint, but IMU fusion is not commissioned by merely seeing a topic. No gravity or driver test was run here. Do not transfer this raw-scale conversion to Airy Lite/Fairy profiles, whose decoder fields differ.

### Native driver API and callback backpressure

A native C++ integration uses the pinned `LidarDriver<PointCloud>` API: register the free-cloud/completed-cloud callbacks and exception callback, populate `RSDriverParam` with this model's decoder/input settings, check `init()` and `start()` Boolean results, then call `stop()` to join the acquisition threads. `regPacketCallback` exposes packets separately from decoded clouds, while `getTemperature`, `getDeviceInfo` and `getDeviceStatus` return a Boolean indicating whether the requested information is available. A valid API method does not mean every model populates every field. [Public native API](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/api/lidar_driver.hpp).

The user's callbacks execute on the driver's decoding thread. Queue the completed cloud for a separate processing thread and recycle buffers after consumption; avoid mapping, file compression or slow network calls inside the callback. The documented consequence of blocking is **`ERRCODE_PKTBUFOVERFLOW` and discarded packets**, which can resemble a bad Ethernet link. Separate link/capture loss from application backlog before changing the sensor's power or calibration. Native `decodePacket` can consume an externally supplied packet source, but still needs the correct model framing and calibration. libpcap is needed for native PCAP input, Eigen for internal transforms, and PCL/Boost for the optional visualization tool; they are not all intrinsic requirements of every receive-only application. [Thread ownership and buffer queues](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/doc/intro/03_thread_model.md), [native dependencies and demo build options](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/README.md).

### Web controls, synchronization thresholds and upgrade verification

Use the delivered **Airy 96** firmware's web interface on the isolated sensor network. Record the current page/settings first. The manual's **General Setting**, **Performance Setting**, **Angle Pulse Setting**, **Diagnostic** and **System** pages perform different roles; the following values are the reviewed manual profile, not a universal future firmware default.

| Control group            | Documented inputs and behavior                                                                                                                                             |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Network                  | Device and target on the same subnet; default unicast target `.102`; `255.255.255.255` is broadcast. MSOP/DIFOP ports **1025–65535**, and they must differ                 |
| Return / operation       | Select the exact supported return mode above; High Performance is default, Standby stops motor and transmitter                                                             |
| Time source              | GPS, PTP E2E-L4, P2P, gPTP or E2E-L2; match master transport/profile/domain                                                                                                |
| PTP domain / peer delay  | Domain **0–127**; Respond To PeerDelayRequest off by default; do not change it without the intended network role                                                           |
| Leap-second option       | No Leap Second off by default; retain the clock source's expected timescale                                                                                                |
| Master loss              | Timeout **1–255 s**, default **5 s**, before leaving synchronized state                                                                                                    |
| Lock / unlock hysteresis | Both thresholds **1–255 ms**; lock default **1 ms**, unlock **20 ms**. A locked icon is not a sub-microsecond accuracy claim                                               |
| Phase lock               | Rotor reference angle **0–360°**, distinct from where the host splits a frame                                                                                              |
| IMU                      | Control on by default; actual port **1025–65535**; output **25/50/100/200 Hz**, default 200 Hz; ±2/4/8/16 g and ±250/500/1000/2000 degrees/s, defaults ±4 g/±500 degrees/s |
| Performance              | Reflectivity Enhancement off by default; Trail Filter **1–5, default 4**; frame-start/gap angle **0–360°**                                                                 |

Airy additionally exposes rain/blockage detection distance **30/20/10 cm (30 cm default)**, blockage sensitivity high/medium/low (high default), **Dead Zone 10cm Enable** on by default, an optional **channels 81/85/89/93** switch off by default and **Gap Filling Enable** off by default. These alter which near/noise/channel/gap points appear; retain their exact settings with a baseline PCAP and do not call filled points new direct laser observations.

Angle Pulse uses **SYNC OUT1**, an enable switch, integer start angle, pulse width and a step entered to one decimal place. **Mode 1 increases the first pulse width by 25%; Mode 2 does not**; this manual defaults to **Mode 1**. The pulse-output setup is not a GPS input setting or proof of PTP lock. The manual does not establish a universal safe electrical load/range for an arbitrary attached receiver, so retain the model-specific signal limits and do not connect a guessed trigger circuit. Click **Save** and require the successful response, then reread settings; a typed value alone is not confirmed applied. [Exact manual Appendix A2](https://robosense-robotics.github.io/product-manual/en/Airy/#a2-product-parameter-setting).

The Diagnostic page refreshes about every **5 s** and exposes voltage/current, device temperature, RPM, rotor phase, laser on/off, PPS/GPRMC state, sync mode/time/Lock, startup count and accumulated running time. Red voltage/current should first be interpreted against Standby versus active state. Check a readback, then correlate with the packet status/capture; do not mistake the slow page refresh for a missing 10 Hz cloud. [Diagnostic page](https://robosense-robotics.github.io/product-manual/en/Airy/#a3-product-diagnosticsoperational-status).

Firmware recovery is component-specific. Obtain a package for the exact model, board revision and serial; preserve settings/calibration and establish stable power first. In **System**, choose the supplied **ZIP**, verify the shown filename and select its matching application/mainboard/baseboard action. The manual names component payloads `.hs_fs`, `.bin` and `.bit` respectively; these internal suffixes are not instructions to upload an unrelated raw file or repackage firmware. The public instructions do not establish a mandatory cross-component flashing order or an emergency bootloader procedure. After the supported operation, reread each affected version and recheck cloud/calibration/time; on failure save the error and use manufacturer-directed recovery rather than repeat another board's image. [Official upgrade requirements](https://robosense-robotics.github.io/product-manual/en/Airy/#a4-product-firmware-upgrade).

### Airy channel groups and complete IMU selector map

Appendix D's 96 channels are not a single uniformly timed fan. The following compact grouping retains all emission offsets; nominal optical angles in the appendix range from **−0.07° for channel 1 to 89.4° for channel 96**, while the product FOV is specified nominally as 0–90°. Use the delivered DIFOP angle corrections for geometry.

| One-based channels    | Emission offset, µs      | 10%-target ranging band |
| --------------------- | ------------------------ | ----------------------- |
| 1–8 / 9–16 / 17–24    | 0 / 5.712 / 12.376       | 30 m                    |
| 25–32 / 33–40 / 41–48 | 19.040 / 25.704 / 33.320 | 30 m                    |
| 49–56 / 57–64         | 41.888 / 50.456          | 30 m                    |
| 65–68 / 69–72         | 59.024 for both          | 30 m / 20 m             |
| 73–80 / 81–88 / 89–96 | 70.448 / 81.872 / 93.296 | 20 m                    |

The appendix lists **60 m farthest ranging** for every channel, a different condition from the 10%-target bands above. Neither value makes dark/oblique/occluded objects guaranteed detections. Appendix C10 says **0x0128 converts to 600**, although that integer is **296**. Preserve this raw real-time field and compare diagnostic-page RPM instead of inventing a scale. The separate motor setpoint in Appendix C1 encodes **600 RPM as 0x0258**. Airy Lite’s 0.1 RPM/count scale must not be transferred to Airy96. [Appendices C10/D](https://robosense-robotics.github.io/product-manual/en/Airy/).

The 51-byte Airy IMU layout is **magic 0–3; timestamp 4–13; acceleration XYZ 14/18/22; gyro XYZ 26/30/34; signed temperature 38–41 at 0.01 °C; ODR 42; acceleration FSR 43; gyro FSR 44; uint32 counter 45–48; tail 49–50 (`F0 0F`)**. ODR codes **0/1/2/3/4** mean **25/50/100/200/1000 Hz** in the packet definition; the reviewed web UI only lists through 200 Hz, so the packet enum alone is not a command to enable 1000 Hz. Acceleration FSR codes 0–3 mean ±2/4/8/16 g and gyro codes 0–3 mean ±250/500/1000/2000 degrees/s. Raw gyro × FSR/32768 × π/180 yields rad/s; **do not apply a second degrees-to-radians conversion** to the pinned decoder's gyro output. Acceleration's separate g-versus-SI boundary is described above. [Manual IMU table and decoder](https://robosense-robotics.github.io/product-manual/en/Airy/#444-imu-data-stream-output-protocol), [actual conversion](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSAIRY.hpp).

### Airy model and return discriminators

The manual's measurement-header table places **`lidar_type:0x31` at byte31** and **`lidar_model:0x02` at byte32 for 96 beams**, after timestamp bytes20–29. Its counter region begins at12 and the remaining labeled regions are reserved in that manual. The pinned decoder defines additional header fields, including measurement/echo discriminator bytes16/17; retain its exact structure rather than infer reserved-byte meanings from another firmware table.

DIFOP **byte300 values0/1/2** select strongest/first/last in the reviewed Airy manual. That current UI does not offer simultaneous dual return; the decoder's wider family support alone is not evidence that this sold Airy revision supports a dual throughput claim. Reflectivity is the manufacturer's calibrated **1–255 proprietary scale**, not a literal 0–255% reflectance measurement. Compare target material, range and incidence together before using intensity as a classifier. [Manual §§2.5.2–2.5.3/4.4](https://robosense-robotics.github.io/product-manual/en/Airy/), [pinned header/echo interpretation](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSAIRY.hpp).

## Getting started

### First result: identity, packets and cloud <a href="#getting-started-verify-a-live-point-cloud" id="getting-started-verify-a-live-point-cloud"></a>

1. Inspect the actual sensor/kit, power adapter and labeled Airy cable. Mount with an open optical window and connect power-off. Leave sync/trigger leads disconnected and insulated.
2. Configure the dedicated host Ethernet adapter as `192.168.1.102/24`, matching the factory unicast destination. Do not duplicate the sensor's `.200` address. Energize the approved power path and confirm the physical Ethernet link.
3. Open `http://192.168.1.200` on that sensor network. Record model, serial, board/app/motor firmware versions and current network settings before changing anything. Read diagnostics for voltage, temperature, RPM and mode.
4. Open a manufacturer-compatible RSView build, choose the Airy profile and receive live data on 6699/7788. Observe a measured board/wall, then save a short **PCAP** and replay it. Avoid changing firmware or factory defaults merely to obtain the first frame.

**Expected result:** the identified Airy 96 presents a current device-status page and a coherent updating hemispherical cloud; a recorded sequence replays with the same geometry. The default sensor/destination/ports are documented, not assumed to survive previous reconfiguration. Use Wireshark ARP/UDP capture to discover an unknown address without resetting it. [Manual §§3.4,4.2–4.3](https://robosense-robotics.github.io/product-manual/en/Airy/).

### Original read-only UDP inventory

Close RSView and any ROS driver first so they do not compete for UDP ports. Save this original program as `airy_packet_check.py`; run `python3 airy_packet_check.py 192.168.1.102`. It receives for 8 seconds and sends no control command. These are the factory destination ports; adjust only after recording the actual configuration.

```python
import collections
import selectors
import socket
import sys
import time

host = sys.argv[1]
specs = {6699: (1248, bytes.fromhex("55 aa 05 5a")),
         7788: (1248, bytes.fromhex("a5 ff 00 5a 11 11 55 55")),
         6688: (51, bytes.fromhex("aa 55 5a 05"))}
counts = collections.Counter()
bad = collections.Counter()
selector = selectors.DefaultSelector()
sockets = []
try:
    for port in specs:
        sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        sockets.append(sock)
        sock.bind((host, port))
        sock.setblocking(False)
        selector.register(sock, selectors.EVENT_READ, port)
    start = time.monotonic()
    while time.monotonic() - start < 8.0:
        for key, _ in selector.select(0.2):
            data, peer = key.fileobj.recvfrom(65535)
            port = key.data
            length, prefix = specs[port]
            counts[port] += 1
            if len(data) != length or not data.startswith(prefix):
                bad[port] += 1
            if counts[port] == 1:
                print("first", port, "source", peer,
                      "bytes", len(data), "head", data[:8].hex())
    elapsed = time.monotonic() - start
    for port in specs:
        print(port, "packets", counts[port], "per_second",
              round(counts[port] / elapsed, 1), "unexpected", bad[port])
finally:
    selector.close()
    for sock in sockets:
        sock.close()
```

**Expected result:** sustained MSOP and occasional DIFOP packets with the documented length/header; IMU traffic appears only when enabled. The manual's nominal MSOP interval is about 444.44 µs and DIFOP about 1 s, but the script's counts are host reception observations, not a precision rate measurement. An unexpected header/length is a reason to check the actual model/protocol revision before decoding. Zero packets does not prove that the sensor failed. [Packet definitions](https://robosense-robotics.github.io/product-manual/en/Airy/#44-communication-protocols).

### Build and start the ROS2 publisher

Prerequisites: ROS2 Humble desktop on Ubuntu 22.04, compiler, colcon, PCL, yaml-cpp/libpcap development packages and working live/capture checkpoint. Use a new workspace:

```bash
mkdir -p ~/airy_ws/src
cd ~/airy_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_sdk.git
cd rslidar_sdk
git checkout 8b4b4b7ff910799260347821084c59e1c73d50d5
git submodule update --init --recursive
cd ~/airy_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_msg.git
```

In `rslidar_sdk/config/config.yaml`, set the Airy entries described above. Keep `send_point_cloud_ros:true`, frame `rslidar` and output `/rslidar_points`. For IMU, set port 6688 and enable parsing at build time. If the point consumer requires time/ring, change the CMake `set(POINT_TYPE ...)` line to `XYZIRT` before building.

```bash
source /opt/ros/humble/setup.bash
cd ~/airy_ws
colcon build --cmake-args -DENABLE_IMU_DATA_PARSE=ON
source install/setup.bash
ros2 launch rslidar_sdk start.py
```

In another sourced terminal inspect `ros2 topic info /rslidar_points --verbose`, `ros2 topic hz /rslidar_points` and `ros2 topic echo /rslidar_imu_data --once`. Set RViz's fixed frame to the emitted sensor frame for the bench test. Check actual message fields before connecting a time-sensitive consumer.

**Expected result:** a continuous PointCloud2 stream around the configured 10 Hz frame rate and separate IMU messages when enabled. A visually stable stationary scene and advancing timestamps are required before calibration/SLAM. This is a source-backed build procedure; compilation and hardware execution were not performed. [Live setup](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/06_how_to_decode_online_lidar.md).

### Controlled configuration experiments

Change one web parameter per recorded capture: return mode, frame-start angle, near-zone/performance filter or IMU output range/rate. Save the original values and use a fixed scene. Compare retained points, geometry, time and noise rather than choosing the visually densest rendering. In particular, channel enable/gap-filling options and the decoder's near-distance filter can change an apparent blind region.

For PCAP replay use `msg_source:3`, the capture's exact ports/type and an existing PCAP path; set `pcap_repeat:false` for a finite diagnostic pass. Reproduction needs the capture plus DIFOP/calibration, source commit, config and frame transform, not just exported XYZ points. [Replay procedure](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/08_how_to_decode_pcap_file.md).

## Troubleshooting and FAQs

| Symptom                          | Model-specific checks                                                                                                                  |
| -------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| Motor/link absent                | Correct 9–32 V power and adapter rating, matched harness, connector seating; inspect damaged cable before changing software            |
| Web page works but no cloud      | Actual destination `.102`, MSOP/DIFOP ports, firewall/interface, High Performance versus Standby and application port ownership        |
| Packets but bad geometry         | Select RSAIRY, correct 96-channel firmware, received DIFOP angle tables and optical offsets; do not use generic uniformly spaced beams |
| No IMU in ROS2                   | Device IMU output/rate and port,`imu_port` config and `ENABLE_IMU_DATA_PARSE`; raw 51-byte traffic alone does not enable SDK parsing   |
| Near returns missing             | Driver 0.2 m filter versus 0.1 m hardware blind zone, web near-zone setting and target material                                        |
| Rotating display gap             | Check frame splitting/start angle before calling it a dead channel; the vendor describes a frame-boundary display gap as normal        |
| Clock unlocked                   | Exact sync mode/transport/domain, master health, hardware-timestamp support for gPTP or correct RS232/PPS levels/wiring                |
| ROS2 rate lower than packet rate | Different units: packet rate is not frame rate; inspect packet loss, DDS/host load and official Humble frame-rate guidance             |
| Overheating                      | Conductive base/bracket, airflow and diagnostics; do not wrap the heat path in insulating material                                     |

Firmware recovery is a separate web **System** operation using the manufacturer-provided, model/revision-matched ZIP package. Save versions and settings, keep power/network stable and use the corresponding board/app upgrade control. Do not rename another model's binary or infer which package fits from a suffix. The manual's package-name examples are not a universal flash map. [Appendix A.4](https://robosense-robotics.github.io/product-manual/en/Airy/#a4-product-firmware-upgrade).

Clean with the documented optical-cleaning method after removing loose contamination; never disassemble the optical enclosure. Protect the window/connectors during dry storage and transport. [Manual §§5–6](https://robosense-robotics.github.io/product-manual/en/Airy/).

### Storage, transport and cleaning <a href="#storage" id="storage"></a>

Store Airy indoors in dry, normal-temperature conditions, protected from corrosion, impacts and environments beyond the connector/enclosure protection rating. The specification's **−40 to +85 °C storage interval** is an outer environmental limit, not a recommendation for routine warehouse storage. Inspect the sensor, connectors and packaging at least every **three months**. Use shock- and moisture-protective packaging, preferably the original, and inspect for transport damage before the next powered check. [Manual §§6.1–6.2](https://robosense-robotics.github.io/product-manual/en/Airy/#62-storage).

For cleaning, use a clean dust-free cloth and the manufacturer's permitted neutral solution. Rinse loose mud/grit away before wiping; warm soapy water provides lubrication, followed by clean-water rinsing and a dry dust-free cloth. The manual permits 99% ethanol for remaining residue. Avoid scratching the optical cover or applying another model's solvent policy. This storage/cleaning procedure is separate from web firmware recovery. [Manual §6.3](https://robosense-robotics.github.io/product-manual/en/Airy/#63-product-cleaning).

## Downloads and technical documents

| Resource                                                                                                                      | Scope                                                                                             |
| ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| [Current Airy manual](https://robosense-robotics.github.io/product-manual/en/Airy/)                                           | Sections 1–7, web settings/diagnostics/upgrade, packet/calibration tables and structural drawings |
| [ROS2 SDK snapshot](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md)   | Supported model, build, live/replay configuration and advanced topics                             |
| [Decoder core snapshot](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/README.md) | C++ integration and packet decoding; matching submodule commit                                    |
| [RoboSense downloads](https://www.robosense.ai/en/resources)                                                                  | RSView, exact manual/CAD/firmware access; some files need manufacturer request                    |

Original attached manual, CAD and certification files remain below. Their presence is not a claim of certification for an assembled robot. The current connector face was visually inspected; use the original drawing for mating orientation and fabrication.

### Product link and exact options <a href="#product-link" id="product-link"></a>

The [sensor-only RS-Airy96 option](https://openelab.io/products/robosense-airy-96-channel-hemispherical-digital-lidar?variant=45547585175750) and [RS-Airy96-kit combined option](https://openelab.io/products/robosense-airy-96-channel-hemispherical-digital-lidar?variant=45547585208518) share the 96-channel sensor. The combined option supplies the listed power/network accessories; an accessory-only kit is not a second LiDAR.

### Documents <a href="#documents" id="documents"></a>

The existing attachments have the following verified native-file names. The Airy Lite file is a **different-model reference** and must not supply Airy 96 electrical or protocol values.

| Attachment                                                                   | Verified filename / format                       | Use and model boundary                                                                                           |
| ---------------------------------------------------------------------------- | ------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------- |
| [Airy manual](<../../.gitbook/assets/Airy User Guide.pdf>)                   | `Airy User Guide.pdf`, PDF, 3,175,761 bytes      | Retained Airy manual; compare revision-sensitive mounting and harness details with the current online manual     |
| [Related Airy Lite manual](<../../.gitbook/assets/Airy Lite User Guide.pdf>) | `Airy Lite User Guide.pdf`, PDF, 3,855,178 bytes | Airy Lite only; retained historical attachment, not an Airy 96 alias                                             |
| [Certification archive](../../.gitbook/assets/Airy_Certification.zip)        | `Airy_Certification.zip`, ZIP, 21,640,158 bytes  | Original manufacturer certification package; assess each certificate's actual scope before making a system claim |

{% file src="../../.gitbook/assets/Airy User Guide.pdf" %}

{% file src="../../.gitbook/assets/Airy Lite User Guide.pdf" %}

{% file src="../../.gitbook/assets/Airy_Certification.zip" %}

### 3D model <a href="#id-3d-model" id="id-3d-model"></a>

[Download the retained Airy CAD archive](<../../.gitbook/assets/Robosesne Airy 3D model.zip>): **`Robosesne Airy 3D model.zip`**, ZIP, **2,484,057 bytes**. The filename spelling is preserved from the attachment. Use it for the sensor enclosure and connector clearance, and compare its revision with the dimensioned [Appendix E drawing](https://robosense-robotics.github.io/product-manual/assets/airy-en/E.jpg). Archive metadata is verified; the internal CAD model has not been opened or dimensionally tested here.

{% file src="../../.gitbook/assets/Robosesne Airy 3D model.zip" %}

## References and validation

Reviewed **24 November 2026**: exact sensor/combined-kit options, current Airy 96 manual and the pinned ROS SDK/decoder code. The UDP inventory is an original bounded read-only program. Numerical definitions and default parameters remain beside their sources.

**ROS/SDK compilation, RSView execution, firmware upgrade, voltage/thermal tests and physical cloud/IMU validation: not run.** Code syntax and declared-evidence checks do not establish hardware behavior.

* [Airy 96 complete online manual](https://robosense-robotics.github.io/product-manual/en/Airy/) — current 24 Nov 2026; 96-channel spec and appendices read.
* [RoboSense ROS/ROS2 SDK build and supported sensors](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [RoboSense packet decoder core and model support](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/README.md) — commit 897b14d3bdb6186a75df27ba51b65b5bd5557723.
* [Actual Airy/live/replay/IMU configuration keys](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [IMU parse and point-type build switches](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/CMakeLists.txt) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [Live ROS publisher procedure](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/06_how_to_decode_online_lidar.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [PCAP replay procedure](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/08_how_to_decode_pcap_file.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [Exact Airy 96 sensor and combined-kit BOM](https://openelab.io/products/robosense-airy-96-channel-hemispherical-digital-lidar) — 23 Nov catalog; public page read 24 Nov 2026.

### Additional established references

* [RoboSense rs\_driver repository](https://github.com/RoboSense-LiDAR/rs_driver) — current repository navigation; use the pinned decoder commit above for the reproducible workflow.
* [rs LiDAR SDK](https://github.com/RoboSense-LiDAR/rsLiDAR_sdk)
