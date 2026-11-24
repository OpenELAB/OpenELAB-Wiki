---
description: >-
  Commission RS-EMX automotive Ethernet and wakeup, read device status,
  distinguish DIFOP1 from DIFOP2 calibration and configure the RSEMX ROS2 cloud
  pipeline.
---

# Robosense EMX

{% hint style="info" %}
[**View RoboSense EMX 192-Beam Automotive Digital LiDAR for ADAS on OpenELAB**](https://openelab.io/products/robosense-emx-192-beam-automotive?variant=45731804414150)

**Model / option:** Only LiDAR · **SKU:** `RS-EMX`
{% endhint %}

## Product overview

### Robosense EMX 192-Beam Automotive-Grade Digital LiDAR Engineering Guide <a href="#robosense-emx-192-beam-automotive-grade-digital-lidar-engineering-guide" id="robosense-emx-192-beam-automotive-grade-digital-lidar-engineering-guide"></a>

**RoboSense EMX is a 192-beam forward digital LiDAR with 1000BASE-T1 automotive Ethernet.** This page covers sensor-only `RS-EMX`; it needs an approved automotive-Ethernet/power/wakeup harness and conversion box before a normal gigabit-Ethernet host. The separate 8 m accessory option and combined kit are not included merely by selecting this SKU. [Store option/BOM](https://openelab.io/products/robosense-emx-192-beam-automotive).

This guide separates the **documented 200 m/120°/10 Hz manual profile** from newer EMX platform maxima and makes the distinction between DIFOP1 status and DIFOP2 calibration explicit. The first result is read-only device/network status, followed by a cloud only after the exact packet/calibration path is established. [EMX integration manual](https://robosense-robotics.github.io/product-manual/en/EMX/), [current decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSEMX.hpp).

## Applications

### Overview <a href="#overview" id="overview"></a>

Use EMX for forward-perception research, road-scene collection and camera-LiDAR fusion. It is a sector sensor, not an omnidirectional robot scanner. A 1.5 m reference blind zone changes near-field coverage planning and may require complementary sensors.

For a useful integration study, record one static road-like scene with known target positions. Keep raw packets, firmware, calibration and timing metadata with the capture. Compare geometry and missing-data regions before changing Gaze/ROI or frame-rate settings. A denser ROI is not a uniform full-FOV resolution guarantee.

The sensor supplies measurements to a larger perception/control system. Hardware platform features and an SDK decoder do not establish vehicle-level autonomous-driving or stopping performance.

### Project References And Application Ideas <a href="#project-references-and-application-ideas" id="project-references-and-application-ideas"></a>

* ROS or ROS 2 perception bring-up using RoboSense SDK/driver packages, then publish point clouds into the robot middleware pipeline.
* ADAS or autonomous-driving research datasets that combine EMX point clouds with camera, GNSS/INS, radar, or wheel-odometry data.
* AGV/AMR obstacle detection in warehouses where dense mid-range 3D coverage is more useful than a 2D safety scanner alone.
* Mapping and localization experiments using PCL filters, voxel grids, ground segmentation, ICP/NDT registration, or SLAM pipelines.
* Multi-LiDAR timestamp experiments using PTP/gPTP, with Wireshark and PCAP files used to verify packet timing.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

## Specifications <a href="#specifications" id="specifications"></a>

| Parameter          | EMX manual reference profile                                          |
| ------------------ | --------------------------------------------------------------------- |
| Range / blind zone | 1.5–200 m;200 m at 10% NIST; blind zone ≤1.5 m                        |
| Precision          | ±5 cm,1σ typical under the manual's conditions                        |
| FOV                | 120° H(±60°),20° V(−12° to +8°)                                       |
| Angular sampling   | 0.08° horizontal,0.1° vertical                                        |
| Frame / point rate | 10 Hz /2,880,000 points/s                                             |
| Data path          | 1000BASE-T1, UDP; matched box to ordinary gigabit RJ45                |
| Supply / power     | 9–16 V DC /10 W reference consumption                                 |
| Wakeup             | 0–2 V sleep,7–12 V wakeup high in the referenced manual               |
| Size / mass        | 102.5 mm depth × 110 mm width × 30.4 mm height;500±20 g without cable |
| Environment        | −40 to 85 °C operating;−40 to 105 °C storage; IP67/IP6K9K conditions  |
| Timing             | gPTP default, PTP subject to firmware/profile                         |

[EMX manual §2.3](https://robosense-robotics.github.io/product-manual/en/EMX/#23-specifications). Consumption is not a guaranteed startup-current ceiling. The 12 V example in troubleshooting requires at least 0.833 A; choose the approved adapter with sufficient startup/cable margin rather than designing exactly at that average value.

The newer public platform/listing describes up to 300 m,140° H,20 Hz and a 120 × 80 × 30 mm package. Those maxima and dimensions do not revise the older integration manual automatically. Record the **received unit's** revision and matched drawing/configuration; do not combine the 300 m headline with the manual's 200 m dark-target condition or install it using a different envelope. [Store's revision-scoped platform information](https://openelab.io/products/robosense-emx-192-beam-automotive).

| Packet role   | Reference format / purpose                                                                        |
| ------------- | ------------------------------------------------------------------------------------------------- |
| MSOP          | 812 bytes,6699 default;32-byte header,192 × 4-byte range/intensity/attribute records,12-byte tail |
| DIFOP1        | 256 bytes,7788 default; identity/network, mode, temperature and fault status                      |
| DIFOP2        | 500 bytes in the manual; channel/surface/roll calibration; SDK also handles other versioned sizes |
| Sensor / host | 192.168.1.200 /192.168.1.102, mask 255.255.255.0                                                  |

[Manual §§3.3,4.3](https://robosense-robotics.github.io/product-manual/en/EMX/), [SDK's EMX-specific config note](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml). DIFOP1 and DIFOP2 have different purposes and may use different destination ports.

### Key Features <a href="#key-features" id="key-features"></a>

The manual reference is a 192-line, 120° × 20° sector at 10 Hz and 2.88 million points/s, using 1000BASE-T1 sensor Ethernet. The newer platform's 300 m/140°/20 Hz claims describe a different revision/configuration scope; they are not combined with this manual's 200 m at 10% target, 9–16 V supply and 102.5 × 110 × 30.4 mm envelope. Use the specification comparison above when defining a requirement.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

## Hardware and connections

### Matched automotive connection <a href="#wiring-and-pinout" id="wiring-and-pinout"></a>

Connect power-off through the approved EMX harness and interface box. The sensor is 1000BASE-T1; the box's RJ45 is ordinary gigabit Ethernet. Do not connect a conventional two-pair Ethernet cable directly to the sensor's automotive pair or apply PoE to the power path.

The manual identifies the harness end as TE2387380-1 and gives a separate Appendix A sensor connector-face definition. Use the exact drawing for the actual end; do not treat a mating harness drawing as a sensor-side face.

#### TE connector pin definition <a href="#te-connector-pin-definition" id="te-connector-pin-definition"></a>

| Sensor/TE function | Documented signal                 |
| ------------------ | --------------------------------- |
| 1                  | GND                               |
| 2                  | Wakeup/KL15                       |
| 4                  | Battery +9–16 V supply domain     |
| 3,5,6              | Unused in the reference pin table |
| D1 /D2             | 1000BASE-T1 TRX\_N /TRX\_P        |

The harness table numbers its automotive pair 7/8; the connector-face drawing names the pair D1/D2. Match the exact end/view rather than substituting one numbering system into the other. The harness maps power/wakeup into a Molex 43025-0600 branch and the automotive pair into its specified Amphenol connector. The box's wake switch is the supported commissioning control; the 7–12 V wake input is not a 3.3 V MCU input. [Manual §3.2 and Appendix A](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Mounting, temperature and optical clearance <a href="#mechanical-installation" id="mechanical-installation"></a>

Use the matched dimensioned drawing and a rigid bracket with an effective thermal path. A package's six fasteners do not establish every screw's allowable engagement. Keep the optical sector unobstructed by covers or the vehicle body and leave access for connector latching/strain relief. Check temperature/fault status during a stationary capture before enclosing the sensor. Do not use ingress ratings as permission to alter connector seals or the optical enclosure. [Manual §§2–3,6](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Calibration and the two information streams

DIFOP1 reports device state and network settings; the manual's DIFOP2 contains 192 pitch angles plus optical/surface offsets. A cloud can appear using fallback/default angles even if the proper calibration stream is missing. Therefore a plausible RViz picture is insufficient acceptance for geometry.

The pinned SDK notes **DIFOP2 default 7766 when DIFOP1 and DIFOP2 both exist**. Its EMX decoder selects among multiple DIFOP2 structures by packet length and loads pitch calibration from them. Observe the actual destination ports/lengths first; configure the decoder for that calibration stream rather than listening only to 7788 status. Retain both streams in diagnostic captures. [SDK config](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml), [DIFOP2 parser](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSEMX.hpp).

MSOP range resolution is 5 mm; its 192 records do not contain a generic spinning-LiDAR ring/azimuth layout. Header meanings also evolve across firmware; use the matched decoder and calibration for the actual packet revision. Inspect synchronization mode/lock and master health before fusing a measured sensor-frame transform.

### Manufacturer drawings and retained diagrams

![EMX product structure](<../../.gitbook/assets/product structure.png>)

![EMX mechanical dimensions](<../../.gitbook/assets/mechanical dimensions.png>)

![EMX coordinate system](<../../.gitbook/assets/coordinate system.png>)

![Vehicle Ethernet power harness](<../../.gitbook/assets/vehicle ethernet power harness.png>)

![EMX interface box](<../../.gitbook/assets/interface box.png>)

![TE connector pin definition](<../../.gitbook/assets/te connector pin definition.png>)

![EMX quick connection](<../../.gitbook/assets/quick connection.png>)

_Manufacturer drawings retained from this guide. Use the stated model/revision and the original manual when interpreting connector views and dimensions._

### Hardware Architecture <a href="#hardware-architecture" id="hardware-architecture"></a>

A conventional PC setup has four separate components: the EMX sensor, the approved two-branch automotive/power harness, the active interface box and the Gigabit host connection. The box supplies the sensor power/wakeup path and converts its automotive pair; it is not simply a passive connector adapter. The manual's 10 W at 12 V example is approximately 0.833 A average and is **not a startup-current rating**. Check the adapter's transient capability and voltage at the sensor before accepting a supply.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Vehicle Ethernet Power Harness <a href="#vehicle-ethernet-power-harness" id="vehicle-ethernet-power-harness"></a>

| J1 pin | Definition    | Connected side |
| ------ | ------------- | -------------- |
| 1      | GND           | J3 pin 1       |
| 2      | Wakeup        | J3 pin 6       |
| 3      | Not connected | J3 pin 3       |
| 4      | Battery+      | J3 pin 2       |
| 5      | Not connected | J3 pin 4       |
| 6      | Not connected | J3 pin 5       |
| 7      | 1000BASE-T1 N | J2 pin 1       |
| 8      | 1000BASE-T1 P | J2 pin 2       |

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Interface Box <a href="#interface-box" id="interface-box"></a>

The interface-box connector labels have their own numbering, distinct from J1/J2/J3 on the harness:

| Box interface | Actual part / function                                |
| ------------- | ----------------------------------------------------- |
| J1            | MOLEX 43045-0600, sensor power and wakeup             |
| J2            | Amphenol NTBM11R1U01110T, 1000BASE-T1 automotive link |
| J3            | DC 5.5 × 2.1 mm power input                           |
| J4            | Wakeup control switch                                 |
| J5            | Conventional Gigabit RJ45 host link                   |

A steady green indicator confirms input power at the box. If dark, verify voltage/polarity, cable continuity and seating with appropriate power-off checks. Do not confuse box J3 with harness J3 or treat a lit indicator as proof of calibrated point data.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

## Software and development resources

### RSView Validation <a href="#rsview-validation" id="rsview-validation"></a>

The pinned `rslidar_sdk` and `rs_driver` support **RSEMX**. For a documented Ubuntu 22.04/ROS2 Humble build, install compiler, colcon, PCL, yaml-cpp and libpcap; include `rslidar_msg` and the SDK's exact submodule. The SDK's generic default is RSM1 and is not suitable for EMX.

| Configuration | EMX-specific decision                                                                                      |
| ------------- | ---------------------------------------------------------------------------------------------------------- |
| `lidar_type`  | `RSEMX`                                                                                                    |
| `msop_port`   | Observed MSOP destination,6699 factory                                                                     |
| `difop_port`  | Observed **DIFOP2 calibration** destination; SDK note says 7766 when both streams exist                    |
| Range filter  | Choose for actual sensor/application; the decoder's 300 m limit does not establish delivered optical range |
| Clock         | Deliberate sensor-clock versus host-time policy; verify synchronization first                              |
| Point type    | XYZI default; use the documented XYZIRT selection if per-point time is required                            |

[SDK config/README](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md), [EMX decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSEMX.hpp).

RSView supports live display, PCAP recording/replay and CSV export; the manual notes LAS export from 3.1.3. Use an EMX-compatible configuration/build. An SDK source release contains decoding software, not a universal sensor firmware-recovery image. [Manual §4.2](https://robosense-robotics.github.io/product-manual/en/EMX/#42-rsview-usage).

### Communication Protocol <a href="#communication-protocol" id="communication-protocol"></a>

Preserve **three** data roles, not a generic two-packet assumption: 812-byte MSOP on 6699, 256-byte DIFOP1 status on 7788, and the separate DIFOP2 calibration destination (7766 in the reviewed SDK when both information streams exist). The manual's DIFOP2 reference is 500 bytes, while the decoder supports versioned alternatives. An old table with only 256-byte DIFOP describes status alone; it is not the complete EMX calibration protocol.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### MSOP Packet Notes <a href="#msop-packet-notes" id="msop-packet-notes"></a>

| Field             | Notes                                              |
| ----------------- | -------------------------------------------------- |
| Header ID         | `0x55 0xAA 0x5A 0xA5`                              |
| Packet count      | Starts at 1 for each frame; 1520 packets per frame |
| Return mode       | Double, strongest, last, or nearest echo           |
| Time mode         | Internal timing, PTP, or gPTP                      |
| Timestamp         | Seconds plus microseconds                          |
| LiDAR type        | Default `0x42`                                     |
| Temperature       | Raw value converted as `Temp = Device_Temp - 80`   |
| Point data        | 192 points per packet, 4 bytes each                |
| Radius resolution | 5 mm                                               |
| Intensity         | 0-255                                              |
| Point attribute   | Normal point or noise point                        |

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### DIFOP Packet Notes <a href="#difop-packet-notes" id="difop-packet-notes"></a>

The DIFOP1 status layout and DIFOP2 calibration layout serve different calculations. In the manual's DIFOP1 reference, work mode is byte 51, frame rate 52, wave/return selection 53, time-sync mode/status 89/90, source IP 102–105, MSOP destination IP 116–119, and fault level 233. Status values include Normal 0x0A and fault levels 0x00/0x01/0x02/0x03; retain raw fields alongside the interpreted state.

For the manual's **500-byte DIFOP2** reference:

| Offset / bytes | Calibration field      | Engineering interpretation                                                 |
| -------------- | ---------------------- | -------------------------------------------------------------------------- |
| 0 / 4          | Header `a5 ff 00 ae`   | Separate from DIFOP1 `a5 ff 00 5a`                                         |
| 67 / 1         | Surface count          | Two scan directions/surfaces                                               |
| 68 / 1         | Pixels per VCSEL       | Eight pixels in this profile                                               |
| 69 / 1         | VCSEL count            | 24 per column, 192 pixels                                                  |
| 70 / 24        | VCSEL yaw offsets      | Scale 1/512                                                                |
| 94 / 384       | 192 pixel pitch values | Scale 0.005°; raw range −2416 to 1595; arithmetic gives −12.08° to +7.975° |
| 478 / 4        | Surface pitch offsets  | Separate clockwise/anticlockwise corrections                               |
| 482 / 2        | Roll offset            | Scale 0.01°                                                                |
| 488 / 12       | E2E tail               | Preserve for the actual protocol/CRC implementation                        |

The manual prints a profile endpoint of **+8.08°**, but also gives an upper raw pitch value of **1595** and a scale of **0.005°**. Multiplying those source values gives **+7.975°**, not +8.08°. This is a source arithmetic discrepancy; the printed endpoint is not a verified scaled limit. Preserve the actual calibration values and matched decoder rather than clamping or changing them to either advertised endpoint. [EMX DIFOP2 reference](https://robosense-robotics.github.io/product-manual/en/EMX/#433-device-info-output-protocol-difop).

Do not calculate XYZ from a fictional per-point direction vector: each EMX MSOP record is only range, intensity and attribute. Its direction must first be reconstructed from the matched optical model and DIFOP2 calibration. The old `XYZ = range × direction_vector` expression is meaningful only **after** that direction exists; it is not the EMX wire layout.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### SDK configuration, recording and replay behavior

The pinned SDK uses one shared `common` block and one `lidar` list entry per sensor. For **EMX**, keep **`lidar_type:RSEMX`** and the model-specific network/packet revision above. The receive-port baseline is **6699 plus the observed DIFOP2 calibration port, normally 7766 in this SDK**; these are not permission to transfer a cable, wake signal or decoder from a similar model.

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

### Native driver API and callback backpressure

A native C++ integration uses the pinned `LidarDriver<PointCloud>` API: register the free-cloud/completed-cloud callbacks and exception callback, populate `RSDriverParam` with this model's decoder/input settings, check `init()` and `start()` Boolean results, then call `stop()` to join the acquisition threads. `regPacketCallback` exposes packets separately from decoded clouds, while `getTemperature`, `getDeviceInfo` and `getDeviceStatus` return a Boolean indicating whether the requested information is available. A valid API method does not mean every model populates every field. [Public native API](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/api/lidar_driver.hpp).

The user's callbacks execute on the driver's decoding thread. Queue the completed cloud for a separate processing thread and recycle buffers after consumption; avoid mapping, file compression or slow network calls inside the callback. The documented consequence of blocking is **`ERRCODE_PKTBUFOVERFLOW` and discarded packets**, which can resemble a bad Ethernet link. Separate link/capture loss from application backlog before changing the sensor's power or calibration. Native `decodePacket` can consume an externally supplied packet source, but still needs the correct model framing and calibration. libpcap is needed for native PCAP input, Eigen for internal transforms, and PCL/Boost for the optional visualization tool; they are not all intrinsic requirements of every receive-only application. [Thread ownership and buffer queues](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/doc/intro/03_thread_model.md), [native dependencies and demo build options](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/README.md).

### EMX measurement header and complete DIFOP1 status reference

For the manual profile used here, the **812-byte MSOP** is a **32-byte header + 192 four-byte points + 12 reserved tail bytes**. The header is not a mechanical-scanner azimuth block.

| MSOP offset / bytes | Field and interpretation                                                                        |
| ------------------- | ----------------------------------------------------------------------------------------------- |
| 0/4; 4/2; 6/2       | `55 AA 5A A5`, packet count starting at 1 per frame, UDP protocol version                       |
| 8/1                 | Return: **0 dual, 4 strongest, 5 last, 6 nearest**                                              |
| 9/1                 | Time: **0 internal, 2 PTP, 3 gPTP** in the MSOP header                                          |
| 10/10               | Six seconds bytes plus four microseconds bytes                                                  |
| 20/10; 30/1; 31/1   | Reserved, type **0x42**, temperature **raw−80 °C**                                              |
| 32 onward           | Per point: big-endian 2-byte range × 0.005 m, intensity 0–255, attribute **1 normal / 2 noise** |
| 800/12              | Tail reserved for checking/counting; no undocumented CRC algorithm is asserted                  |

The manual says 1520 MSOP packets per frame for this profile. Retain actual protocol revision and packet sequence when checking loss; do not extend that count to changed scan/return firmware. [Manual Tables 6–8](https://robosense-robotics.github.io/product-manual/en/EMX/#43-communication-protocol).

| DIFOP1 offset / bytes      | Status/configuration meaning                                                                       |
| -------------------------- | -------------------------------------------------------------------------------------------------- |
| 0/4; 24/3; 27/2; 35/16     | `A5 FF 00 5A`, software version, hardware version and customer serial                              |
| 51/1; 52/1                 | Work mode; frame rate **0x0A 10 Hz / 0x14 20 Hz** as documented, subject to actual product profile |
| 53/1; 54/1; 55/1           | Return mode, ROI, calibration state (**0 normal / 1 factory**)                                     |
| 56/1; 57/18                | Window blockage state and level region; no invented subfield decoder                               |
| 89/1; 90/1; 91/10          | Time mode, success state and seconds/microseconds                                                  |
| 101/1                      | PHY role **0 auto / 1 master / 2 slave**, others treated as auto by the table                      |
| 102/4; 106/4; 110/6        | Source IPv4, mask, MAC                                                                             |
| 116/4; 120/2; 122/2        | MSOP destination IPv4 and source/destination ports                                                 |
| 124/4; 128/2; 130/2        | DIFOP1 destination IPv4 and source/destination ports                                               |
| 156/1; 157/1               | Window/FPGA monitor temperatures **raw−100 °C**, distinct from the MSOP raw−80 scale               |
| 229/1; 230/1; 231/2        | LiDAR-function, external-supply and communication fault fields                                     |
| 233/1; 234/2; 236/4; 240/4 | Fault level **0 none / 1 FL1 / 2 FL2 / 3 FL3**, fault ID/value and diagnostic list                 |
| 244/12                     | Opaque E2E region in this manual; retain bytes without inventing checksum/bit semantics            |

Work-mode codes **1/2/3/4/5/6/7/8/10** mean Init/Wait\_Normal/Pre\_Reset/Post\_Reset/Standby/Pre\_Sleep/Post\_Sleep/Fault/Normal. DIFOP time-mode codes **0/1/2/3/4** mean internal/PPS/E2E-L2/gPTP/P2P-L4; time-state **0/1/2** means failed/success/timeout. Do not reuse the MSOP enum at offset 9 for DIFOP offset 89. DIFOP return **0/4/5/6/10/11** means nearest+farthest/strongest/farthest/nearest/histogram/grayscale; the latter source labels are not proof that every firmware exposes those modes to the application.

DIFOP1's status map is separate from **DIFOP2's per-device direction/calibration map** already given above. The modern decoder primarily consumes its matching calibration structure; an observed packet of another revision is not safely parsed by these manual offsets merely because the magic agrees. Record payload lengths/ports/version, preserve reserved and fault bytes and consult the matching device definition when a field differs. [Manual status map and exact decoder](https://robosense-robotics.github.io/product-manual/en/EMX/#433-device-info-output-protocol-difop), [pinned EMX implementation](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSEMX.hpp).

## Getting started

### First result: read device status without changing it <a href="#software-and-setup-workflow" id="software-and-setup-workflow"></a>

1. Confirm the actual EMX revision, approved 9–16 V power/harness/interface box and applicable wakeup specification. For the assigned sensor-only SKU, obtain those accessories before applying power.
2. Wire the intact harness with all sources off. Connect the box's RJ45 to a dedicated gigabit host adapter configured `192.168.1.102/24`; confirm no address conflict.
3. Apply the approved supply and box wake switch. Inspect power and both link stages. If the host was replaced after a successful session, power-cycle the sensor after shutting down safely: the manual describes a static ARP behavior that otherwise retains the former peer.
4. Capture ARP/UDP with Wireshark on the dedicated interface. Record actual source/destination addresses, MSOP 6699, DIFOP1 and any DIFOP2 destination. Do not change settings just to make them match a tutorial.
5. Close receivers that own 7788 and run this original Python 3 status sampler as `emx_status.py`. It reads the 256-byte DIFOP1 layout only and sends nothing:

```python
import ipaddress
import socket
import time

deadline = time.monotonic() + 8.0
seen = 0
with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as receiver:
    receiver.bind(("0.0.0.0", 7788))
    receiver.settimeout(0.25)
    while seen < 3 and time.monotonic() < deadline:
        try:
            data, peer = receiver.recvfrom(65535)
        except socket.timeout:
            continue
        if len(data) != 256 or data[:4] != bytes.fromhex("a5 ff 00 5a"):
            continue
        print("peer", peer[0], "work_mode", hex(data[51]),
              "frame_rate_code", hex(data[52]),
              "sync_mode", data[89], "sync_status", data[90],
              "source_ip", str(ipaddress.IPv4Address(data[102:106])),
              "msop_destination", str(ipaddress.IPv4Address(data[116:120])),
              "fault_level", data[233])
        seen += 1
if not seen:
    raise SystemExit("No reference-layout DIFOP1: inspect actual port/format")
```

**Expected result:** up to three status reports; reference Normal mode is 0x0A and sync status 1 indicates the reported external lock. A status value alone does not certify the master or measurement quality. Different lengths/headers require the actual protocol; the script intentionally ignores them. [DIFOP1 table](https://robosense-robotics.github.io/product-manual/en/EMX/#433-device-info-output-protocol-difop).

### Decode only after calibration reception is established

1. In compatible RSView select the **EMX** configuration supplied for the received firmware. Verify a changing static cloud and save a PCAP including information/calibration traffic. Do not select M1 simply because it shares 6699.
2. Confirm the observed DIFOP2 length/port matches a supported structure in the pinned decoder. If only DIFOP1 status is present, resolve calibration reception before using cloud geometry for mapping.
3. Create a new Humble workspace and build the model-supported SDK:

```bash
mkdir -p ~/emx_ws/src
cd ~/emx_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_sdk.git
cd rslidar_sdk
git checkout 8b4b4b7ff910799260347821084c59e1c73d50d5
git submodule update --init --recursive
cd ~/emx_ws/src
git clone https://github.com/RoboSense-LiDAR/rslidar_msg.git
source /opt/ros/humble/setup.bash
cd ~/emx_ws
colcon build
source install/setup.bash
```

4. Set `src/rslidar_sdk/config/config.yaml` to live `msg_source:1`,`lidar_type:RSEMX`, the observed MSOP/DIFOP2 ports and `send_point_cloud_ros:true`. Retain the actual frame/clock policy. Start `ros2 launch rslidar_sdk start.py`.
5. Inspect `ros2 topic info /rslidar_points --verbose` and `ros2 topic hz /rslidar_points` from another sourced terminal. Confirm calibration was received, advancing timestamps and stable geometry at known target positions; then measure the robot transform.

**Expected result:** correctly calibrated, continuous PointCloud2 frames for the actual mode. Neither successful packet reception nor a default-angle cloud proves that criterion. Keep a finite PCAP replay (`msg_source:3`,`pcap_repeat:false`) as a repeatable regression input. [SDK live/replay workflow](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/doc/howto/06_how_to_decode_online_lidar.md).

### Engineering Setup Checklist <a href="#engineering-setup-checklist" id="engineering-setup-checklist"></a>

1. Identify the actual EMX revision and obtain its approved harness, converter, 9–16 V supply and wakeup path.
2. Use a dedicated `192.168.1.102/24` host for factory `.200`; read actual traffic before changing stored settings.
3. Capture MSOP, DIFOP1 **and DIFOP2** destinations/lengths; preserve calibration with the static PCAP.
4. Select `RSEMX`, configure the observed calibration port and check the resulting geometry before enabling a robot application.
5. Save firmware, decoder commit, clock mode/lock and sensor-to-base transform with the capture.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

## Troubleshooting and FAQs

### Troubleshooting <a href="#troubleshooting" id="troubleshooting"></a>

| Symptom                              | Checks and recovery                                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| Link/power but no points             | Actual power/wakeup and T1 conversion, then ordinary gigabit link, host target/subnet and receiving process              |
| Works with old host, not replacement | Static ARP behavior; retain configuration, shut down and power-cycle sensor for the new peer                             |
| Status arrives, calibration absent   | DIFOP1 on 7788 is not DIFOP2; inspect actual calibration port, packet length and SDK version                             |
| Cloud looks plausible but warped     | Actual DIFOP2 angle loading versus fallback angles, firmware-format match and measured frame transform                   |
| Packets dropped                      | Dedicated link, competing broadcasts/host capacity, socket buffers and capture statistics; frame rate is not packet rate |
| Time unlocked/jumps                  | gPTP/PTP mode and firmware, master health, hardware timing and holdover status                                           |
| Repeated startup                     | Voltage/polarity at sensor, supply current margin, cable drop and approved box; do not exceed 16 V to compensate blindly |
| Unexpected range/FOV/size            | Current delivered revision versus older manual profile; do not combine platform maxima into one operating mode           |

Save captures/versions/settings before recovery. Restart the matched sensor/box only after electrical checks. The reviewed public manual supplies no universal flashing/rescue-pin procedure; use a manufacturer-matched firmware package/instructions if required. Protect the aperture, remove loose contamination before gentle optical cleaning and retain dry, cushioned packaging. [Manual §§5–7](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Best Practices And Limitations <a href="#best-practices-and-limitations" id="best-practices-and-limitations"></a>

Use the revision-matched drawing and optical envelope for brackets, the measured source profile for range/FOV requirements, and a known-good Gigabit link for packet-loss isolation. The manual's 200 m profile and the newer listing's platform maxima are distinct. Keep raw captures before changing Gaze/ROI, timing or return mode; the geometry can look plausible even when calibration reception failed. Public CAD/firmware recovery packages remain resource-access limits, not a reason to substitute another EMX or E1R image.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Cleaning And Maintenance <a href="#cleaning-and-maintenance" id="cleaning-and-maintenance"></a>

Recommended cleaning materials:

* Clean dust-free cloth
* Neutral cleaning solution at moderate temperature, such as soapy water, distilled water, or 99% ethanol

For light dust, lightly wipe the surface with a dust-free cloth moistened with neutral solution, then dry it with a clean cloth. For mud or solid foreign material, rinse with clean water first. Do not wipe mud directly across the protective cover, because it may scratch the surface.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### FAQ <a href="#faq" id="faq"></a>

The answers below distinguish physical connection, transport, status and calibrated geometry. Record the exact firmware/profile when comparing a device with the manual's reference values; an SDK accepting a packet does not establish a different optical specification.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### What is the Robosense EMX used for? <a href="#what-is-the-robosense-emx-used-for" id="what-is-the-robosense-emx-used-for"></a>

It is used for dense 3D perception in ADAS research, robotics, AGV/AMR navigation, mapping, obstacle detection, and point-cloud software development.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### What ports does the EMX use by default? <a href="#what-ports-does-the-emx-use-by-default" id="what-ports-does-the-emx-use-by-default"></a>

Factory MSOP is UDP 6699 and DIFOP1 status is 7788. For the reviewed ROS decoder, DIFOP2 calibration is normally 7766 when both information streams exist. Observe the device's actual destinations and configure `difop_port` for calibration; listening only to 7788 can leave geometry uncalibrated.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### What default IP address should I use during first bring-up? <a href="#what-default-ip-address-should-i-use-during-first-bring-up" id="what-default-ip-address-should-i-use-during-first-bring-up"></a>

Use `192.168.1.200` for the EMX and set the PC to `192.168.1.102/24`, unless the device has already been reconfigured.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Does the EMX need the accessory interface box? <a href="#does-the-emx-need-the-accessory-interface-box" id="does-the-emx-need-the-accessory-interface-box"></a>

For normal PC bench testing, yes. The LiDAR side uses 1000BASE-T1 vehicle Ethernet, while the interface box provides RJ45 Gigabit Ethernet for the host computer.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Why do the range and FOV values differ between sources? <a href="#why-do-the-range-and-fov-values-differ-between-sources" id="why-do-the-range-and-fov-values-differ-between-sources"></a>

The user guide lists 200 m range and 120 deg horizontal FOV, while the OpenELAB product listing mentions 300 m range and 140 deg horizontal FOV. Confirm the exact hardware revision, firmware, and sales specification before using those values in a design requirement.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Can RSView record data? <a href="#can-rsview-record-data" id="can-rsview-record-data"></a>

Yes. RSView can display real-time point clouds, record PCAP data, replay PCAP files, export CSV, and export LAS in RSView 3.1.3 or later.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### What should I check if RSView shows no point cloud? <a href="#what-should-i-check-if-rsview-shows-no-point-cloud" id="what-should-i-check-if-rsview-shows-no-point-cloud"></a>

Check power/wakeup and both physical links, then actual source/destination addresses and local firewall rules. Inspect MSOP and the selected DIFOP2 calibration destination, close competing receivers, and verify RSEMX/model revision support. A status-only capture or missing calibration is not a successful cloud test.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

### Is CAD available for the EMX? <a href="#is-cad-available-for-the-emx" id="is-cad-available-for-the-emx"></a>

The reviewed public manual supplies dimensioned/mechanical illustrations, retained in this guide. A standalone revision-matched public CAD archive was not verified. Use the actual unit's approved CAD/drawing before production bracket design; the dimensions of a newer listing are not a substitute for that model revision.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

## Downloads and technical documents

### Resources <a href="#resources" id="resources"></a>

| Resource                                                                                                                                                   | Exact scope                                                                                                         |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| [EMX manual](https://robosense-robotics.github.io/product-manual/en/EMX/)                                                                                  | Reference electrical/wakeup, interface-box, network,812-byte MSOP, DIFOP1/2, status and optical-maintenance content |
| [TE connector appendix](https://robosense-robotics.github.io/product-manual/en/EMX/#appendix-a-te-connector-pin-definitions)                               | Original sensor-face definition; not interchangeable with mating-harness numbering                                  |
| [RSEMX decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSEMX.hpp) | Versioned calibration structures and actual cloud decode                                                            |
| [ROS2 SDK config](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml)                         | Explicit EMX DIFOP2 port note and model/range settings                                                              |
| [RoboSense resource center](https://www.robosense.ai/en/resources)                                                                                         | Exact received-revision drawings, RSView and firmware access                                                        |

Harness and interface-box drawings were inspected; the established attached diagrams/files remain below. Do not fabricate a custom harness from a connector photograph.

### Does this page include contact email or official support text? <a href="#does-this-page-include-contact-email-or-official-support-text" id="does-this-page-include-contact-email-or-official-support-text"></a>

Use the linked manufacturer resource center for the missing revision-specific CAD, firmware recovery image or detailed fault package. These are identifiable engineering resources to obtain for the actual EMX; generic contact blocks do not establish model compatibility or authorize flashing. The manual and exact decoder sources remain directly linked for the supported read-only/status and cloud paths.

[Model-specific source](https://robosense-robotics.github.io/product-manual/en/EMX/).

## References and validation

### Source Notes <a href="#source-notes" id="source-notes"></a>

Reviewed **24 November 2026**: sensor-only SKU, current store versus manual profile, official EMX interface/protocol documentation and pinned RSEMX/ROS source. The status sampler is original and read-only. Public platform maxima are separated from the reference integration profile.

**Compilation, RSView/ROS execution, power/wakeup measurements, firmware upgrade, calibration reception and physical point-cloud tests: not run.** Expected status/cloud results are acceptance criteria, not observed tests.

* [Complete EMX official integration manual](https://robosense-robotics.github.io/product-manual/en/EMX/) — current 24 Nov 2026; reference 200 m/120 deg/10 Hz profile.
* [ROS2 SDK with RSEMX support](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/README.md) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [EMX MSOP and versioned DIFOP2 decoder](https://github.com/RoboSense-LiDAR/rs_driver/blob/897b14d3bdb6186a75df27ba51b65b5bd5557723/src/rs_driver/driver/decoder/decoder_RSEMX.hpp) — commit 897b14d3bdb6186a75df27ba51b65b5bd5557723.
* [RSEMX and DIFOP2 port/range configuration](https://github.com/RoboSense-LiDAR/rslidar_sdk/blob/8b4b4b7ff910799260347821084c59e1c73d50d5/config/config.yaml) — commit 8b4b4b7ff910799260347821084c59e1c73d50d5.
* [Exact RS-EMX sensor-only and current platform-spec distinction](https://openelab.io/products/robosense-emx-192-beam-automotive) — 23 Nov catalog; public page read 24 Nov 2026.

### Additional established references

* [https://www.generationrobots.com/media/robosense-emx-user-guide.pdf](https://www.generationrobots.com/media/robosense-emx-user-guide.pdf)
* [https://autowarefoundation.github.io/autoware-documentation/](https://autowarefoundation.github.io/autoware-documentation/)
* [https://pointclouds.org/](https://pointclouds.org/)

### Supporting resource links

* [rs driver](https://github.com/RoboSense-LiDAR/rs_driver)
* [rslidar sdk](https://github.com/RoboSense-LiDAR/rslidar_sdk)
