---
description: >-
  Wire and power Livox MID-360S sensor and kit options, configure exact S-model
  ROS2 networking, capture points/IMU and diagnose timing, thermal and
  near-range limits.
---

# Livox MID-360S 3D LiDAR Sensor Engineering Guide

{% hint style="info" %}
[**View Livox MID‑360 S 360‑Degree 3D LiDAR Sensor with ROS2 Support for Robotics and SLAM (DJI Ecosystem) on OpenELAB**](https://openelab.io/products/livox-mid360?variant=46527758041286)

**Model / option:** MID-360S-Kit · **SKU:** `Livox-MID-360S-Kit`

[**View Livox MID‑360 S 360‑Degree 3D LiDAR Sensor with ROS2 Support for Robotics and SLAM (DJI Ecosystem) on OpenELAB**](https://openelab.io/products/livox-mid360?variant=45625733185734)

**Model / option:** MID-360S · **SKU:** `Livox-MID-360S`
{% endhint %}

## Product overview

**Livox MID-360S is a 100BASE-TX Ethernet 3D LiDAR with a built-in six-axis IMU.** This guide commissions the exact S model, captures a live point cloud and brings its point/IMU streams into ROS2. It covers both `Livox-MID-360S` and `Livox-MID-360S-Kit`; the sensor and firmware target are the same.

| Sold option          | Included items that change setup                                                                              |
| -------------------- | ------------------------------------------------------------------------------------------------------------- |
| MID-360S sensor-only | Sensor, cleaning cloth, hex screwdriver and M3 screw package; obtain a compatible cable and supply separately |
| MID-360S-Kit         | The same sensor/accessories plus a 1.5 m one-to-three splitter cable and power adapter                        |

[Exact OpenELAB package list](https://openelab.io/products/livox-mid360). Original MID-360, MID-360L and MID-360S are distinct hardware/firmware choices. Use the S-specific launch/configuration, not a renamed older config. [MID-360S manual](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf), [driver model support](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md).

### Quick Summary <a href="#quick-summary" id="quick-summary"></a>

The sensor-only and combined kit use the same MID-360S firmware and data format. The combined kit adds the 1.5 m splitter and power adapter; the sensor-only option needs those separately. For development, Viewer2 establishes identity/capture, SDK2 supplies the native communication layer, and ROS Driver2 publishes cloud and IMU messages. A community SLAM project is a subsequent integration, not part of basic sensor discovery.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

## Applications

Use MID-360S for mobile-robot mapping, obstacle-perception research and LiDAR-inertial odometry. Its non-repetitive pattern fills more of the field of view over a longer integration interval. A denser static accumulation is useful for a room survey, while accumulation on a moving robot needs time alignment and motion compensation.

A useful first integration project is a stationary room capture with one measured planar target, followed by a short repeatable route. Compare wall thickness, time continuity and endpoint alignment before tuning a SLAM algorithm. The sensor provides measurements; object classification, planning and verified stopping belong to the host/system.

Do not treat the 0.1 m blind-zone specification as guaranteed precision at 10 cm. Glass, thin dark objects and water can produce missing or misleading returns. Keep the optical window and full viewing envelope clear of the robot body, including transparent covers. [Official range conditions](https://www.livoxtech.com/mid-360s/specs).

### Run mapping or localization <a href="#run-mapping-or-localization" id="run-mapping-or-localization"></a>

Use a recorded cloud/IMU baseline before evaluating FAST-LIO, MOLA or LIO-SAM adaptations. Check the chosen project's actual sensor-message support, clock assumptions and extrinsic direction; a MID-360 example does not automatically support every S-model message setting. Compare a stationary map, a slow turn and the same route after returning to the start before tuning filters for a moving robot.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

### Project References and Application Ideas <a href="#project-references-and-application-ideas" id="project-references-and-application-ideas"></a>

The community project links below are retained application references. Their MID-360 naming does not establish MID-360S firmware/message compatibility; check the exact project release before integration. The supported S-model first-result path remains the pinned Livox driver procedure in this guide.

* [Livox ROS Driver 2](https://github.com/Livox-SDK/livox_ros_driver2): official ROS/ROS2 integration starting point.
* [MOLA MID-360 example](https://github.com/Whan000/MOLA-SLAM): ROS2 Humble MID-360 mapping/localization example.
* [fast\_lio\_tinker](https://github.com/tinkerfuroc/fast_lio_tinker): FAST-LIO2-oriented MID-360 mobile robot workflow.
* [LIO-SAM-MID360](https://github.com/nkymzsy/LIO-SAM-MID360): LIO-SAM adaptation for Livox MID360-style data.
* [CMU mecanum autonomy stack](https://github.com/jizhang-cmu/autonomy_stack_mecanum_wheel_platform): ROS2 autonomy platform referencing Livox Mid-360 integration.
* Application ideas: AMR navigation, forklift perception, warehouse mapping, service robot localization, outdoor robot obstacle detection, and research-grade LiDAR-inertial odometry.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

## Specifications

| Parameter              | MID-360S value and condition                                                    |
| ---------------------- | ------------------------------------------------------------------------------- |
| Optical / safety       | 905 nm; Class 1 under IEC60825-1:2014, intact product                           |
| FOV                    | 360° horizontal, typically −7° to +52° vertical                                 |
| Detection range        | 40 m at 10% reflectivity under 100 klx;100 m cut-off is a different limit       |
| Near range             | 0.1 m blind zone;0.1–0.2 m data is reference-only, without guaranteed precision |
| Range precision,1σ     | ≤2 cm at 10 m;≤4 cm at 0.2 m,25 °C and 80% reflectivity targets                 |
| Angular precision,1σ   | <0.15°                                                                          |
| Point/frame rate       | 200,000 points/s first return;10 Hz typical frame rate                          |
| Interface              | 100BASE-TX Ethernet/UDP; not a PoE inlet                                        |
| Timing / IMU           | PTP v2 or external GPS/PPS; ICM40609,200 Hz IMU output default                  |
| Supply / typical power | 9–27 V DC,12 V recommended;6.5 W normal operation                               |
| Body / mass            | 65 × 65 × 60 mm nominal;265 g                                                   |
| Environment            | −20 to 55 °C operating; IP67 sensor/approved mated connection scope             |

[Official specifications and test notes](https://www.livoxtech.com/mid-360s/specs), [manual §§3.2,3.5](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf). The manufacturer lists sample/temperature/reflectivity conditions; do not compare its 100 m cut-off with another sensor's dark-target range.

| Power event  | Manual condition                             |
| ------------ | -------------------------------------------- |
| Self-heating | −20 to 0 °C: up to 14 W, up to 10 minutes    |
| Startup      | 0–35 °C: approximately 18 W for 8 seconds    |
| Warm startup | Above 35 °C: approximately 9 W for 8 seconds |

These are design-reference values, not a guarantee that every unit has identical peaks. Supply and cable design must keep the voltage **at the sensor** within 9–27 V throughout startup and load transients. [Manual §3.2](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf).

### MID-360S vs MID-360 <a href="#mid-360s-vs-mid-360" id="mid-360s-vs-mid-360"></a>

MID-360 and MID-360S share the nominal 65 × 65 × 60 mm envelope, 265 g mass, 200,000 first-return points/s and 100BASE-TX interface in their references. They remain different firmware/configuration targets: this guide uses `Mid360s`, `MID360s_config.json` and the S-specific launch files. The S specification gives 40 m at 10% reflectivity and a separate 100 m cutoff; an older MID-360 80%-target range must not be substituted for that condition.

| Original comparison field    | MID-360                                       | MID-360S                                                        |
| ---------------------------- | --------------------------------------------- | --------------------------------------------------------------- |
| Field of view                | 360° H, −7° to +52° V                         | Same typical angular span                                       |
| Reflectivity-qualified range | 40 m at 10%; 70 m at 80%, 100 klx             | 40 m at 10%, 100 klx; separate 100 m cutoff                     |
| Blind zone                   | 0.1 m; 0.1–0.2 m reference only               | Same near-zone qualification                                    |
| Point rate / frame rate      | 200,000 first-return points/s / 10 Hz typical | Same                                                            |
| Data / synchronization       | 100BASE-TX; PTPv2 or external GPS             | Same interface families; exact S config remains separate        |
| IMU                          | ICM40609                                      | ICM40609                                                        |
| Supply / normal consumption  | 9–27 V / 6.5 W                                | 9–27 V / 6.5 W; S startup cases listed separately above         |
| Size / mass / protection     | 65 × 65 × 60 mm / 265 g / IP67                | Same nominal values; use the S-specific cable-clearance drawing |

[Original MID-360 official specifications](https://www.livoxtech.com/mid-360/specs), [MID-360S specifications](https://www.livoxtech.com/mid-360s/specs). These shared nominal values do not establish interchangeable firmware or a common mechanical connector offset.

The old store note described the S connector as 2 mm recessed and 3 mm higher than MID-360. That comparison has not been established by a revision-matched dimension overlay here; use the exact S CAD/FOV model and measured cable clearance rather than treating the old comparison as a machining tolerance. The older 905 g reseller mass is superseded by the manufacturer's 265 g sensor mass.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

## Hardware and connections

### Power-off wiring and connector orientation <a href="#hardware-integration" id="hardware-integration"></a>

Use the keyed **M12 A-code 12-pin male sensor connector** and its matching shielded female cable. The manual names Finecables MA12FAHD12STXXXB14 as a recommended female connector. Interpret pin numbers from the **sensor-side male face drawing** in manual pages 8–9; the mating female view is mirrored. Never derive numbering from a wire's position in a photograph.

| Sensor pin | Function          | Electrical boundary                          |
| ---------- | ----------------- | -------------------------------------------- |
| 1,9        | Power +           | 9–27 V DC                                    |
| 2,3        | Ground            | Supply return/reference                      |
| 4,5        | Ethernet TX+, TX− | Ethernet differential pair                   |
| 6,7        | Ethernet RX+, RX− | Ethernet differential pair                   |
| 8          | PPS input         | 3.3 V LVTTL                                  |
| 10         | GPS serial input  | 3.3 V LVTTL;9600 baud,8 data bits, no parity |
| 11,12      | Reserved outputs  | 3.3 V LVTTL; leave unused in this first test |

[MID-360S connector table and face drawings, pp 8–9](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf). High-voltage power pins and 3.3 V timing pins share one connector, so continuity/polarity must be checked with all sources disconnected. Do not connect a PoE device to the splitter's RJ45. Insulate unused function leads individually.

Align the key, insert straight and turn the metal coupling nut rather than twisting the cable. The manual specifies 1.5–2.0 N·m for this coupling; this is **not** a mounting-screw torque. Keep cable bend radius at least 60 mm and provide strain relief. The splitter is a commissioning/debug accessory; design a suitably protected production harness for the intended environment. [Manual §§1.2,3.3](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf).

### Mounting and thermal path

Use the bottom mounting face and four M3 holes,5 mm deep. Select screw length from actual bracket thickness so it cannot bottom out. Leave at least 10 mm airflow clearance. The manual recommends a flat metal mounting plate at least 3 mm thick with at least 10,000 mm² exposed to air. Do not put extra payload on the sensor. Inverted installation requires at least 0.5 m between mounting surface and ground. Verify these dimensions against the original drawing/CAD rather than scaling an image. [Manual pp 15–16](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf).

### Frames, timing and point interpretation <a href="#measure-the-extrinsics" id="measure-the-extrinsics"></a>

Publish a measured transform from the sensor's documented coordinate origin to the robot base; a frame name is not an extrinsic calibration. The manual places the IMU at `(11.0,23.29,−44.12)mm` in the point-cloud frame and states that its axes align with that frame. Its stored extrinsic parameters are stored metadata, not automatically applied point corrections.

PTP v2 here uses UDP/IPv4 timing; GPS timing needs an external PPS plus time message, not an internal navigation receiver. Confirm lock/status and monotonic timestamps before fusion. Returns beyond range can be encoded at zero coordinates. Reflectivity 0–150 represents the manufacturer's diffuse-return scale,151–255 retroreflective behavior; nearby intensity is not a calibrated material measurement. Two-bit tag groups describe other noise, atmospheric particles and dragging noise; preserve the raw tag before choosing a filter. [Manual §§3.4–3.5](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf).

## Software and development resources

### Pinned software paths <a href="#software-workflow" id="software-workflow"></a>

The reviewed Livox ROS Driver2 source explicitly contains `MID360s_config.json` and `rviz_MID360s_launch.py`. Use that S-specific support. The example below targets **Ubuntu 22.04 / ROS2 Humble**, a documented pairing. The source also documents ROS1 and Foxy/Jazzy paths; a different ROS distribution needs its corresponding build target. [Driver README](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md).

| Component                | Role                                                                                   |
| ------------------------ | -------------------------------------------------------------------------------------- |
| Livox Viewer2            | Device identity/status, sampling, live visualization, capture/replay and configuration |
| Livox SDK2               | C/C++ communication; do not substitute the first-generation Livox SDK                  |
| Livox ROS Driver2        | ROS/ROS2 point-cloud and IMU publication                                               |
| `MID360s_config.json`    | Model key `Mid360s`, lidar\_type8, device/host addresses and fixed device UDP ports    |
| `rviz_MID360s_launch.py` | PointCloud2 output, frame `livox_frame`,10 Hz publication in the reviewed launch       |
| `msg_MID360s_launch.py`  | Livox custom message path for software that needs that format                          |

PointCloud2 and Livox CustomMsg are different APIs. A SLAM package requiring per-point time/tag/line fields must consume a compatible message; changing a topic name does not convert the format. The official driver is presented as a development/debugging tool, not an unmodified production certification. [Message definitions](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md), [S launch](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/launch_ROS2/rviz_MID360s_launch.py).

Viewer2.5.9 packages and firmware 35.01.0113 are listed on the reviewed S download page. Treat the firmware as an exact model-specific file. Record the received firmware before deciding whether an update is necessary; normal first capture does not require flashing. [Official downloads](https://www.livoxtech.com/mid-360s/downloads).

### SDK2 configuration, callbacks and ROS message contracts

For **MID-360S**, keep the exact `MID360s_config.json` model section used above. `lidar_net_info` describes the sensor ports; each `host_net_info` entry describes a receiving host and its ports. Editing the local JSON changes the application's intended endpoints; changing a device's persistent IP requires a separate acknowledged device operation. The SDK README's HAP example is not this model's configuration.

| Setting / API                                                      | Input and resulting behavior                                                                                   |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- |
| `LivoxLidarSdkInit(path, host_ip, log_cfg_info)`                   | Opens a model-matched JSON configuration; returns a Boolean initialization result                              |
| `SetLivoxLidarInfoChangeCallback`                                  | Callback receives device handle and identity information; use the discovered handle for subsequent operations  |
| `SetLivoxLidarPointCloudCallBack` / `SetLivoxLidarImuDataCallback` | Separate callbacks receive handle, device type, packet pointer and caller context; neither is a ROS message    |
| `LivoxLidarSdkStart()` / `LivoxLidarSdkUninit()`                   | Start the SDK scanning routine; release SDK resources on shutdown                                              |
| `QueryLivoxLidarInternalInfo`                                      | Requests internal information asynchronously; preserve transport status and returned diagnostic information    |
| `SetLivoxLidarWorkMode`                                            | Requests a target mode asynchronously; inspect callback status/response and the subsequent actual device state |
| `lidar_log_enable`, `lidar_log_cache_size_MB`, `lidar_log_path`    | Firmware-log capture switch, size budget in MB and destination; SDK logger example uses true, 500 MB and `./`  |

The API's immediate `livox_status` and its later callback are different checkpoints. Negative statuses include timeout (−4), unsupported operation (−3) and disconnected device (−2). A successful call does not prove the hardware reached Sampling. Generic API declarations also cover capabilities of other Livox models; they do not establish that this model implements every scan/FOV/IO option. Copy needed packet data into an application-owned bounded queue before slow processing rather than retaining an unowned callback pointer. That queue recommendation is an integration procedure, not a manufacturer latency guarantee. [Pinned API](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/include/livox_lidar_api.h), [types/statuses](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/include/livox_lidar_def.h), [configuration/logger](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md).

| Driver2 launch setting  | Supported meaning / consumer consequence                                                                                                       |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `publish_freq`          | Host cloud publication frequency, recommended examples 5, 10, 20 or 50 Hz, maximum 100 Hz; it does not change the sensor's physical point rate |
| `multi_topic:0` / `1`   | Shared cloud topic / independent topic per LiDAR; confirm resolved names with `ros2 topic list -t`                                             |
| `xfer_format:0`         | Livox `PointCloud2`: XYZ in m, reflectivity/intensity 0–255, tag, line and per-point timestamp                                                 |
| `xfer_format:1`         | `CustomMsg`: header, first-point `timebase`, `point_num`, `lidar_id`, then points containing `offset_time`, XYZ, reflectivity, tag and line    |
| `xfer_format:2`         | Generic PCL XYZI output is documented for ROS1 only; it removes the richer timing/tag/line contract                                            |
| `pcl_data_type:1` / `2` | Device Cartesian 32-bit mm / 16-bit cm coordinates; changing resolution changes the wire payload, not just a visualization setting             |

Choose the subscriber format before recording. For `CustomMsg`, reconstruct each point from the timebase and its relative offset; preserve the clock type and units supplied by the driver. Keep sensor calibration separate from a host transform and apply each extrinsic exactly once. The generic README's `blind_spot_set` is HAP-only, so do not add it to this configuration to hide near-field artifacts. [Driver2 settings and message fields](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md), [exact model configuration](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/MID360s_config.json).

The manual distinguishes actual states **Sampling, Idle, Ready, Error, Self-check, Startup and Upgrading** from user-selected target modes **Sampling, Idle and Ready**. Idle retains communication while other components are powered down; Ready is prepared to emit, and Sampling is active measurement. During recovery, retain the status/log record, correct supply/thermal/network causes and recheck actual state before resuming acquisition. Do not repeatedly send mode or reboot requests to mask an Error state.

### Series packet framing, clock interpretation and diagnostics

The series protocol **v1.4.12 (21 September 2026)** explicitly covers MID-360, MID-360S and MID-360L. It uses little-endian UDP fields. Discovery is a broadcast query to port **56000**, separate from the 56100 command channel; discovery across an address mismatch does not prove that unicast data can reach the configured host. MID-360S can use the series protocol, but its manual/tag interpretation and exact `Mid360s` configuration remain authoritative. The original MID-360 mechanical or firmware files are not interchangeable.

| Packet field                         | Byte offset / size | Interpretation                                                                                                                                                |
| ------------------------------------ | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `length`, `time_interval`, `dot_num` | 1/2, 3/2, 5/2      | Whole UDP length, first-to-last sample span in 0.1 µs, number of samples                                                                                      |
| `udp_cnt`, `frame_cnt`               | 7/2, 9/1           | Packet/frame counters; frame count is invalid for non-repetitive scanning                                                                                     |
| `data_type`, `time_type`             | 10/1, 11/1         | Decode payload and clock policy before interpreting data                                                                                                      |
| CRC32                                | 24/4               | Check timestamp plus data, using the protocol CRC definition                                                                                                  |
| First-point timestamp                | 28/8               | uint64 nanoseconds; time type 0 is boot-relative, 1 PTP/gPTP source, 2 GPS                                                                                    |
| Data                                 | 36 onward          | Type 0: gyro rad/s then acceleration g; type 1: XYZ int32 mm + reflectivity + tag (14 bytes/point); type 2: XYZ int16 cm + reflectivity + tag (8 bytes/point) |

Check the declared length, data type, sample count and CRC before indexing a packet. For N equally spaced samples where N>1, the protocol describes the time of sample i as first-point time + i × (`time_interval` × 100 ns)/(N−1); preserve the integer-time precision needed by the consumer. Do not apply the point-cloud interpolation rule to an arbitrary IMU packet or assume raw acceleration g is already ROS m/s². The protocol lists 96 samples for its single-return cloud profiles; use the actual count and model/firmware contract rather than hard-code a size for every SDK-supported Livox device. [Protocol framing/data/timestamps](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/livox_eth_protocol_mid360.html#point-cloud-imu-data-protocol).

Control packets have **0xAA** start, 24-byte command header, sequence-matched request/ACK, CRC16 over the first 18 header bytes and a separate data CRC32. Important command families are discovery **0x0000**, parameter configure/query/push **0x0100/0x0101/0x0102**, reboot/reset/GPS-time **0x0200–0x0202**, log collection **0x0300–0x0303**, and staged upgrade **0x0400–0x0403**. Prefer SDK calls for these transactions. Configuration writes, factory reset and upgrades are state-changing recovery tools, not passive connectivity tests. [Control/return-code/CRC definitions](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/livox_eth_protocol_mid360.html#control-command).

HMS diagnostics encode a 32-bit value as abnormal ID in bits 31–16 and severity in bits 7–0 (middle byte reserved). Severity 1/2/3/4 means informational/warning/error/fatal. For example, **0x01020002** identifies ID 0x0102, a thermal warning. Time IDs **0x0402–0x0409** distinguish PTP interruption, unsupported PTP version, PPS/GPS problems and weak synchronization; **0x040A** reports mixed PTP/gPTP signals. Preserve the full code, clock status and network capture rather than treating all timestamp faults as packet loss. MID-360L additionally documents **0x021C** for code-disk contamination/abnormal rotation; unresolved cases require manufacturer inspection. A diagnostic catalog containing another model's ID does not mean that ID occurs on this model. [Official HMS format and actions](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/hms_code_mid360.html).

### Clock commissioning and log-based recovery

For **MID-360S**, begin with the exact supported time modes listed above. A large nanosecond timestamp does not itself prove UTC or synchronization quality. Observe the selected source in Viewer2 and packet `time_type`, then inspect synchronization/HMS status and offsets. PTP uses a master and the LiDAR as slave; multiple masters or mixed PTP/gPTP traffic can produce a clock problem even while point clouds arrive.

Before configuring a Linux PTP master, use the read-only capability check **`ethtool -T INTERFACE`** with the actual dedicated adapter. The common Livox guide distinguishes software/hardware timestamp capability and documents a **linuxptp 3.1.1** example. Select the correct UDP/IPv4 or supported Layer-2 profile; do not copy an automotive gPTP configuration onto a model that excludes gPTP. Starting a master or synchronizing host hardware/system clocks changes the network/host timing environment, so use a deliberate isolated setup and retain the previous time service. [Official synchronization methods and capabilities](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/common/time_sync.html).

For GPS, check both **PPS electrical/timing requirements in this model's manual** and the absolute-time message path. The common guide recommends **9600 baud, 8 data bits, no parity**, valid GPRMC/GNRMC and stable fix; its UART example is specifically MID-360 and does not license another model's connector pin mapping. Hardware PPS plus software timestamp delivery is a different route from direct UART, with host delay considerations. Model manuals may specify stricter pulse widths than the common guide; preserve the model-specific range instead of relaxing it to the common minimum.

SDK2 logging is separately controlled by `lidar_log_enable`, `lidar_log_cache_size_MB` and `lidar_log_path`, with README defaults **true, 500 MB and current directory**. Choose a writable location with sufficient space before enabling unattended logging. Save actual serial/firmware, clock source, status/HMS, addresses and a short cloud/IMU capture together; SDK initialization success is not proof that each data channel or time source is working. Firmware upgrades stop acquisition and require the exact model image; retain settings/logs and a known-good recording before using the documented update tool. Do not use reset or a cross-model firmware image as an IP-discovery shortcut. [SDK2 logger/upgrade behavior](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md).

### MID-360 series payload and parameter reference

For the **v1.4.12 series protocol**, the complete measurement prefix is: version u8 at 0; length u16 at 1; time interval u16 at 3; point count u16 at 5; packet counter u16 at 7; frame counter u8 at 9; data type u8 at 10; time type u8 at 11; reserved\[12] at 12; CRC32 at 24; timestamp u64 at 28; payload at 36. Version is currently 0. This is a byte layout, not a C structure whose compiler padding can be assumed. The frame counter is not meaningful for a non-repetitive scan. [Series protocol measurement tables](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/livox_eth_protocol_mid360.html#point-cloud-imu-data-protocol).

| Data type                    | Relative payload fields                                         | Units / model boundary                                                                                  |
| ---------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| 0, IMU                       | gyro XYZ float32 at 0/4/8; acceleration XYZ float32 at 12/16/20 | rad/s and g; multiply acceleration by 9.80665 for m/s² if not already converted by the receiving driver |
| 1, high-resolution Cartesian | XYZ int32 at 0/4/8; reflectivity u8 at 12; tag u8 at 13         | mm → m by 0.001; 14 bytes per sample                                                                    |
| 2, compact Cartesian         | XYZ int16 at 0/2/4; reflectivity/tag u8 at 6/7                  | 10 mm → m by 0.01; 8 bytes per sample                                                                   |
| 3, spherical                 | depth u32 at 0; theta/phi u16 at 4/6; reflectivity/tag at 8/9   | depth mm, zenith/azimuth 0.01°; 10 bytes; **not supported by MID-360L**                                 |

For a spherical record, `x=r sin(theta) cos(phi)`, `y=r sin(theta) sin(phi)`, `z=r cos(theta)` after converting angles to radians; retain the sensor frame and zero-range invalid-point policy. Type 1 and type 2 have different coordinate quantization; integer truncation is not improved precision. Preserve each record's raw tag: bits 7–6 reserved, 5–4 other confidence, 3–2 rain/fog/dust confidence, 1–0 adhesion between adjacent surfaces. For each two-bit confidence field, 0/1/2/3 means high/medium/low/reserved. Filtering is an application decision, not a change to the reported measurement. Keep the exact model manual's interpretation beside this series-level definition. [Data types and tag fields](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/livox_eth_protocol_mid360.html#tag-information).

The following table covers the series protocol's **published configurable keys**. `RW` means that a configuration command is documented; it does not mean every firmware implements every value. Query actual support and state first. Original MID-360 IO descriptions and generic FOV limits must not override this guide's S/L connector and physical FOV.

| Key / name                           | Value bytes / representation | Settings and engineering consequence                                                                                            |
| ------------------------------------ | ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `0x0000 pcl_data_type`               | 1, u8                        | 1 Cartesian int32, 2 Cartesian int16, 3 spherical except L                                                                      |
| `0x0001 pattern_mode`                | 1, u8                        | 0 non-repetitive; 1 repetitive and 2 low-rate repetitive are marked unsupported in this revision                                |
| `0x0004 lidar_ipcfg`                 | 12, octets                   | Sensor IPv4\[4], mask\[4], gateway\[4]; changing it can disconnect the current session                                          |
| `0x0005 state_info_host_ipcfg`       | 8                            | Destination IPv4\[4], destination port u16, source port u16                                                                     |
| `0x0006 pointcloud_host_ipcfg`       | 8                            | Same field structure, cloud output endpoint                                                                                     |
| `0x0007 imu_host_ipcfg`              | 8                            | Same field structure, independent IMU endpoint                                                                                  |
| `0x0012 install_attitude`            | 24                           | roll/pitch/yaw float32 in degrees; x/y/z int32 in mm; stored installation metadata, not automatic point transformation          |
| `0x0015 fov_cfg0`, `0x0016 fov_cfg1` | 20 each                      | Four int32 angle endpoints (yaw start/stop, pitch start/stop), plus reserved u32; two regions need separate enable bits         |
| `0x0017 fov_cfg_en`                  | 1, u8                        | Bits 0/1 enable regions 0/1; disabled regions are not activated merely by storing endpoints                                     |
| `0x0018 detect_mode`                 | 1, u8                        | 0 normal, 1 sensitive; sensitivity may increase noise while improving dark/bright surface detection                             |
| `0x0019 func_io_cfg`                 | 4, u8\[4]                    | Generic IN0/IN1/OUT0/OUT1 function slots; **S/L reserved outputs stay reserved under their own manuals**                        |
| `0x001A work_tgt_mode`               | 1, u8                        | 1 Sampling, 2 Idle, 9 Ready; Error/Self-check/Startup are observed states, not target requests                                  |
| `0x001C imu_data_en`                 | 1, u8                        | 0 off, 1 on; destination and receiving software must also be correct                                                            |
| `0x0021 speed_mode`                  | 1, u8                        | 0 normal, 1 S low-speed, 2 L high-speed; do not transfer the model-specific setting                                             |
| `0x0026 time_filter`                 | 1, u8                        | Default 0: time rollback may interrupt cloud; 1 strengthens GPS abnormal-time filtering; does not establish external clock lock |
| `0x0029 pc_freq_mod`                 | 1, u8, L only                | 0/1/2 = 80k/50k/100k points/s; sensor output profile, distinct from ROS publish frequency                                       |
| `0x002B imu_sensor_cfg`              | 3, u8\[3]                    | Output-rate code, acceleration-range code, gyro-range code as below                                                             |

The series FOV table states yaw endpoints in \[0°, 360°) and a generic pitch interval (−10°, 60°). The **received model's physical FOV further restricts that interval**. Outside an enabled region, the protocol retains placeholder points with zero distance and reflectivity 60 to preserve timing; do not mistake them for a reflective object at the origin. For generic IO, input function 0 represents PPS/GPS and output values 0/1/2 mean inactive/follow-input/zone output. The source's pin-number explanation belongs to original MID-360; this guide does not authorize wiring reserved S/L contacts as those outputs. [Parameter key definitions and restrictions](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/livox_eth_protocol_mid360.html#cmd-detials).

| IMU configuration byte  | Code → value                                                          |
| ----------------------- | --------------------------------------------------------------------- |
| Output rate             | 0 → 200 Hz; 1 → 500 Hz; 2 → 100 Hz; 3 → 50 Hz                         |
| Acceleration full scale | 0/1/2/3 → ±4/±8/±16/±32 g                                             |
| Gyro full scale         | 0/1/2/3/4/5/6/7 → ±2000/±1000/±500/±250/±125/±62.5/±31.25/±15.625 °/s |

| Read-only key                                    | Bytes / type          | Interpretation                                                                                                                  |
| ------------------------------------------------ | --------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| `0x8000 sn`, `0x8001 product_info`               | 16 / 64, byte strings | NUL-padded identity and product information; bound string reads to field length                                                 |
| `0x8002/0x8003/0x8004`                           | 4 each                | Application/loader/hardware versions, four version octets                                                                       |
| `0x8005 mac`                                     | 6                     | Device MAC; not a writable replacement address                                                                                  |
| `0x8006 cur_work_state`                          | 1, u8                 | Sampling 1, Idle 2, Error 4, Self-check 5, Startup 6, Upgrading 8, Ready 9                                                      |
| `0x8007 core_temp`                               | 4, int32              | 0.01 °C per count                                                                                                               |
| `0x8008 powerup_cnt`                             | 4, u32                | Restart counter; useful when diagnosing intermittent supply                                                                     |
| `0x8009 local_time_now`, `0x800A last_sync_time` | 8 each, u64           | Device time and last master/PPS reference; compare within the documented clock domain                                           |
| `0x800B time_offset`                             | 8, int64              | Device time minus master time, ns; sign matters                                                                                 |
| `0x800C time_sync_type`                          | 1, u8                 | 0 none, 1 PTP, 2 GPS in the status table; packet type 1 combines network synchronization                                        |
| `0x800E lidar_diag_status`                       | 2, u16                | Nibbles 0–3 system, 4–7 scanning, 8–11 ranging, 12–15 communication; nibble values 0 normal, 1 warning, 2 error, 3 safety error |
| `0x8010 FW_TYPE`                                 | 1, u8                 | 0 loader, 1 application image                                                                                                   |
| `0x8011 hms_code`                                | 32, u32\[8]           | Up to eight nonzero diagnostic codes; preserve all codes and severity, not only the first                                       |

A useful query set is serial, firmware, current state, core temperature, synchronization offset/type and all HMS entries. Read before changing settings, preserve the reply, and query again after an acknowledged change or supported reboot. This distinguishes a transport success from the intended state actually being reached. [Series read-only key table](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/livox_eth_protocol_mid360.html#cmd-detials).

### UDP command fields, replies and CRC reference

The following is a development reference for the exact protocol revision identified above, not a startup command list. Offsets are measured from the beginning of the **UDP payload**, excluding Ethernet/IP/UDP headers. Integer fields are little-endian; IPv4 fields remain four ordered address octets.

| Control header field     | Offset / bytes | Type and interpretation                                                  |
| ------------------------ | -------------- | ------------------------------------------------------------------------ |
| Start / protocol version | 0 / 1; 1 / 1   | uint8: `0xAA`; command version 0                                         |
| Total length             | 2 / 2          | uint16, header plus data, maximum 1400 bytes                             |
| Sequence                 | 4 / 4          | uint32; match ACK to the outstanding request, not just to its command ID |
| Command ID               | 8 / 2          | uint16; functions listed below                                           |
| Request or ACK           | 10 / 1         | uint8: 0 request, 1 acknowledgment                                       |
| Sender                   | 11 / 1         | uint8: 0 host, 1 LiDAR                                                   |
| Reserved                 | 12 / 6         | Preserve; do not assign application flags                                |
| Header CRC16             | 18 / 2         | CRC-16/CCITT-FALSE over bytes 0–17                                       |
| Data CRC32               | 20 / 4         | CRC-32 over bytes 24 through end; zero when data is empty                |
| Command data             | 24 onward      | Command-specific body                                                    |

CRC-16/CCITT-FALSE uses polynomial `0x1021`, initial `0xFFFF`, no reflection and final XOR 0. CRC-32 uses polynomial `0x04C11DB7`, initial/final XOR `0xFFFFFFFF`, with input/output reflection; this is the conventional CRC-32 implemented by Python's `zlib.crc32`. Measurement packets use that CRC32 over **timestamp plus data**, beginning at byte 28, rather than over their whole header. Check the received length and CRC before trusting counts or offsets. [MID-360 series protocol, CRC/control sections](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/livox_eth_protocol_mid360.html), [Avia 2 protocol, CRC/control sections](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/livox_eth_protocol_avia2.html).

| Command                   | Request data, relative to command-data byte 0                                                                                                | Response / operating consequence                                                                                                  |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `0x0000` discovery        | Empty; broadcast to 56000                                                                                                                    | ACK: result u8, device type u8, serial\[16], IPv4\[4], command port u16 at offsets 0/1/2/18/22                                    |
| `0x0100` configure        | count u16, reserved u16, then count TLV entries                                                                                              | ACK result u8 + failed key u16; a submitted request is not proof of application                                                   |
| `0x0101` inquire          | count u16, reserved u16, then count u16 keys                                                                                                 | ACK result u8, returned count u16, then TLVs at byte 3                                                                            |
| `0x0102` information push | Device sends count u16, reserved u16, then TLVs at byte 4                                                                                    | Unsolicited status/configuration; distinguish it from an inquiry ACK                                                              |
| `0x0200` reboot           | delay u16, milliseconds                                                                                                                      | Result u8; acquisition is interrupted                                                                                             |
| `0x0201` factory reset    | Reserved serial field\[16]                                                                                                                   | Result u8; success is followed by an immediate reboot                                                                             |
| `0x0202` GPS time         | type u8 = 2, time u64 at byte 1                                                                                                              | Time is nanoseconds at the last PPS rising edge; result u8                                                                        |
| `0x0300` log push         | type/index/file-count/flags u8 at 0–3; Unix seconds u32 at 4; reserved u16 at 8; transfer index u32 at 10; data length u16 at 14; data at 16 | Host ACK: result/type/index at 0/1/2 and transfer index u32 at 3; flags request ACK, create-file and finish-file using bits 0/1/2 |
| `0x0301` log collection   | type u8, enable u8                                                                                                                           | Type 0 real-time, 3 flash; enable 0/1; result u8                                                                                  |
| `0x0302` log clock        | Unix seconds u32                                                                                                                             | Result u8; log naming clock is distinct from point timing                                                                         |
| `0x0303` debug raw output | enable u8, host IPv4\[4], port u16, reserved u16                                                                                             | Result u8; changes traffic/load and destination                                                                                   |
| `0x0400` begin upgrade    | firmware type u8, encryption u8, image length u32, device type u8                                                                            | Result u8; select the exact device package through the supported updater                                                          |
| `0x0401` image chunk      | offset u32, length u32, encryption u8, reserved\[3], bytes                                                                                   | ACK result u8, received offset u32, received length u32                                                                           |
| `0x0402` finish upload    | checksum type u8, checksum length u8, checksum bytes                                                                                         | Result u8; upload completion is not successful firmware boot                                                                      |
| `0x0403` upgrade state    | Empty                                                                                                                                        | Result u8 and progress u8, 0–100                                                                                                  |

A TLV consists of **key u16, value length u16, then exactly that many value bytes**. Advance by `4 + length`, validate against the packet end and distinguish unknown keys from malformed entries. Log timestamps use Unix **seconds**; measurement timestamps use **nanoseconds**. Upgrade firmware-type codes are package/LiDAR/other = 0/1/2; encryption codes 0–4 represent none/AES128/AES256/DES/3DES, but the matching signed manufacturer package determines what is valid. The older series upgrade example identifies original MID-360 as type 9; **do not reuse that number for S or L**. Avia 2's own protocol identifies type 40. These fields explain the protocol; they do not replace an exact-model supported update package. [Official command payloads and return codes](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/livox_eth_protocol_mid360.html), [Avia 2 command details](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/livox_eth_protocol_avia2.html).

| Device return code       | Meaning / response                                                                             |
| ------------------------ | ---------------------------------------------------------------------------------------------- |
| `0x00` / `0x01`          | Success / failure; retain the full reply                                                       |
| `0x02` / `0x03`          | Current state disallows the operation / value outside range; correct the cause before retrying |
| `0x20` / `0x21`          | Unsupported parameter / restart needed for effect; do not silently claim an immediate change   |
| `0x22` / `0x23` / `0x24` | Read-only key / invalid length or oversized reply / key-count mismatch                         |
| `0x30` / `0x31`          | Firmware public-key signature / digest failure; obtain the correct intact package              |
| `0x32` / `0x33` / `0x34` | Wrong firmware type / image length outside range / flash erasure in progress                   |

These are **device** codes. SDK `livox_status` values such as timeout −4 or disconnected −2 describe a different layer. In a direct SDK application, `QueryLivoxLidarFirmwareVer` and `QueryLivoxLidarInternalInfo` accept an observed device handle and a `QueryLivoxLidarInternalInfoCallback`. First check the function's immediate return, then check callback status, non-null response, `ret_code`, `param_num` and bounded TLVs; never dereference a timed-out response. Queries do not require a work-mode, IP, reset or firmware write. An SDK initialization/configuration may separately configure streams, so use an already reviewed, model-matched session rather than calling an arbitrary quick-start executable and calling it passive. [API and response definitions](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/include/livox_lidar_api.h), [SDK structures](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/include/livox_lidar_def.h).

For additional observers, `LivoxLidarAddPointCloudObserver` returns an observer ID that must be passed to `LivoxLidarRemovePointCloudObserver`; the command observer has its own add/remove pair. Keep callback work bounded, copy needed data before returning and remove observers before destroying their context. Reconfiguration and firmware updates belong after a known-good capture: record serial/version/configuration, stop downstream consumers, verify the exact package and uninterrupted power/network, use the supported updater, wait for its reported completion/reboot, then re-read version/state and compare a new static capture. A rejected signature/type is a reason to stop and obtain the correct file, not to bypass validation. [SDK callbacks and upgrade API](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/include/livox_lidar_api.h).

The pinned SDK reports this model as device type **35**. Driver2 JSON `lidar_type:8` is a configuration classification, not that discovery device-type byte. Keep these identifiers in their own fields. [SDK device enum](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/include/livox_lidar_def.h).

## Getting started

### First point cloud in Viewer2 <a href="#getting-started-first-point-cloud-capture" id="getting-started-first-point-cloud-capture"></a>

1. Inventory the exact S sensor and selected kit. Secure it with an open FOV and connect the matched cable **with power off**. Check supply polarity,9–27 V operating range and startup capacity before energizing.
2. On the dedicated wired host adapter, configure `192.168.1.50/24`; do not replace the address of a remote-management interface. Factory sensor IP is `192.168.1.1XX`, where `XX` is the serial number's final two digits. Confirm the actual address and avoid duplicates.
3. Connect the cable RJ45 to a non-PoE data path, then power the matched supply. Leave timing leads unconnected/insulated for this initial test.
4. Extract the official Viewer2 package. On Windows run its executable; on the documented Ubuntu build run `./livox_viewer_2.sh` from the extracted directory. Select the discovered serial number, inspect hardware/firmware and state, then select Sampling if required.
5. Inspect a changing cloud and capture a short stationary sequence. Record sensor IP, serial, firmware, Viewer build, host adapter and supply. Return to playback and confirm it opens before adding ROS.

**Expected result:** the identified S device reaches Sampling and produces current point-cloud frames. Discovery alone does not establish measurement quality. On failure, first inspect address/subnet and supply; then look for UDP packets and competing Viewer/SDK connections. Permit the application/necessary ports on the isolated sensor interface rather than disabling the host firewall globally. [Manual §§3.3,3.6–3.7](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf).

### Build the supported ROS2 path <a href="#install-the-software" id="install-the-software"></a>

Prerequisite: an installed ROS2 Humble desktop environment on Ubuntu 22.04, CMake/compiler/colcon, and the working Viewer checkpoint. Close Viewer before starting another controller. The commands below install SDK2 under `/usr/local`; use a new project directory, not an existing production workspace.

```bash
mkdir -p ~/mid360s_dev
cd ~/mid360s_dev
git clone https://github.com/Livox-SDK/Livox-SDK2.git
cd Livox-SDK2
git checkout c0796f04c143143899c87a773d9f6b7136453c0b
cmake -S . -B build
cmake --build build --parallel 2
sudo cmake --install build
cd ~/mid360s_dev
git clone https://github.com/Livox-SDK/livox_ros_driver2.git ws/src/livox_ros_driver2
cd ws/src/livox_ros_driver2
git checkout 21445540f0d100dc86a7e6df312dd70bbdb4afdf
```

Before building, edit `config/MID360s_config.json`. Keep device-side ports 56100/56200/56300/56400/56500 and the S model key/type. Set the host address to your **actual** wired address and `lidar_configs[0].ip` to the observed sensor, not the repository's example `192.168.1.12`. The host command/push/point/IMU/log ports are 56101/56201/56301/56401/56501 in this template. [Actual S config](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/MID360s_config.json).

This original script makes a timestamped backup and changes only the two addresses. Run it from the driver source directory as `python3 set_mid360s_ip.py ACTUAL_SENSOR_IP ACTUAL_HOST_IP`:

```python
import ipaddress
import json
from pathlib import Path
import sys
import time

sensor_ip = str(ipaddress.IPv4Address(sys.argv[1]))
host_ip = str(ipaddress.IPv4Address(sys.argv[2]))
path = Path("config/MID360s_config.json")
original = path.read_bytes()
config = json.loads(original)
if config["lidar_summary_info"]["lidar_type"] != 8 or "Mid360s" not in config:
    raise SystemExit("Not the reviewed MID-360S configuration")
if len(config["lidar_configs"]) != 1:
    raise SystemExit("Use a separately reviewed multi-sensor configuration")
backup = path.with_name(path.name + "." + str(time.time_ns()) + ".bak")
backup.write_bytes(original)
config["Mid360s"]["host_net_info"][0]["host_ip"] = host_ip
config["lidar_configs"][0]["ip"] = sensor_ip
path.write_text(json.dumps(config, indent=2) + "\n")
print("Saved", path, "backup", backup, "sensor", sensor_ip, "host", host_ip)
```

Build and launch from a fresh Humble-sourced terminal:

```bash
cd ~/mid360s_dev/ws/src/livox_ros_driver2
source /opt/ros/humble/setup.bash
./build.sh humble
cd ~/mid360s_dev/ws
source install/setup.bash
ros2 launch livox_ros_driver2 rviz_MID360s_launch.py
```

In a second sourced terminal inspect:

```bash
ros2 topic list -t
ros2 topic info /livox/lidar --verbose
ros2 topic hz /livox/lidar
ros2 topic hz /livox/imu
```

**Expected result:** PointCloud2 on `/livox/lidar`, IMU on `/livox/imu`, changing header stamps and a cloud visible in frame `livox_frame`. A 10 Hz cloud publication setting and a 200 Hz sensor IMU stream are different quantities. Topic tools themselves can perturb observed rate; save a short record and inspect timestamps before inferring sensor loss. Config changes after installation may require rebuilding/reinstalling the updated config. [Driver publish paths](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/src/lddc.cpp).

### A repeatable capture check <a href="#connection-and-first-result" id="connection-and-first-result"></a>

Keep the sensor fixed. Capture one empty-scene interval and one interval with a broad matte target at a measured distance above 0.2 m. Compare point distribution, timestamps and returns from a consistent region rather than cherry-picking a single point. A slower host can create backlog without changing the physical scan rate; compare live capture with replay on the same host. Only after stable reception should a measured base transform, time synchronization and motion-compensated SLAM be added.

### Prerequisites <a href="#prerequisites" id="prerequisites"></a>

Prepare the exact S sensor, matched M12 splitter and regulated 9–27 V supply, a dedicated wired Ethernet adapter and an S-compatible Viewer2 package. Set aside an unoccluded stationary scene and close other acquisition applications. Cold self-heating and startup demand are higher than 6.5 W normal consumption; size the supply using the power-event table rather than that typical number alone.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

### Bench test the sensor <a href="#bench-test-the-sensor" id="bench-test-the-sensor"></a>

In Viewer2, record the discovered S-model serial, actual firmware and sensor/host addresses, then enable Sampling and save a short static capture. Check the IMU stream separately from the cloud. A device appearing in discovery without point output can still be in a non-sampling state or have the wrong destination network setting.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

### Verify the data flow <a href="#verify-the-data-flow" id="verify-the-data-flow"></a>

After launching the S-specific ROS2 target, inspect `/livox/lidar` and `/livox/imu`, their types and header timestamps. `PointCloud2` is different from Livox `CustomMsg`: a consumer needing per-point offset time, line and tag must use a compatible published format. Confirm the configured publication rate and frame name, then retain the matching configuration with the bag.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

### Engineering Setup Checklist <a href="#engineering-setup-checklist" id="engineering-setup-checklist"></a>

* Confirm variant: MID-360S or MID-360.
* Download the correct manual, release notes, firmware, CAD model, and FOV model.
* Design the mount and verify FOV clearance in CAD.
* Bench test with Livox Viewer 2 before installing on the robot.
* Install Livox SDK2 or Livox ROS Driver 2.
* Configure static IP/network routing and publish accurate TF/extrinsic transforms.
* Validate timestamps before running SLAM.
* Record firmware, driver version, ROS distribution, and SLAM package versions.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

### Original offline packet and query-reply inspection

This Python 3 program reads **one exported UDP payload**, not a complete Ethernet frame or PCAP file. In Wireshark, select the intended UDP datagram and export its UDP payload bytes as binary, retaining the original PCAP separately. It opens no network socket and sends no device command. Use `mid360s`, `mid360l` or `avia2` for the actual model; the explicit argument prevents accidental Avia/MID timing-format substitution.

Save as `livox_payload_inspect.py`:

```python
import binascii
import pathlib
import struct
import sys
import zlib

model, filename = sys.argv[1:3]
if model not in {"mid360s", "mid360l", "avia2"}:
    raise SystemExit("Choose mid360s, mid360l or avia2")
b = pathlib.Path(filename).read_bytes()
if len(b) < 24:
    raise SystemExit("Truncated payload")

def crc32(data):
    return zlib.crc32(data) & 0xffffffff

def show_value(key, value):
    answer = value.hex()
    if key == 0x8000:
        answer = value.split(b"\0", 1)[0].decode("ascii", errors="replace")
    elif key in (0x8002, 0x8003, 0x8004) and len(value) == 4:
        answer = ".".join(str(v) for v in value)
    elif key == 0x8006 and len(value) == 1:
        answer = {1: "Sampling", 2: "Idle", 4: "Error", 5: "Self-check",
                  6: "Startup", 8: "Upgrading", 9: "Ready"}.get(value[0], "unknown")
    elif key == 0x8007 and len(value) == 4:
        answer = str(struct.unpack("<i", value)[0] / 100) + " degC"
    elif key == 0x800b and len(value) == 8:
        answer = str(struct.unpack("<q", value)[0]) + " ns device-minus-master"
    elif key in (0x8011, 0x0811) and len(value) % 4 == 0:
        answer = [hex(v[0]) for v in struct.iter_unpack("<I", value)]
    print(hex(key), len(value), answer)

if b[0] == 0xaa:
    version, length = b[1], struct.unpack_from("<H", b, 2)[0]
    if version != 0 or length != len(b) or length > 1400:
        raise SystemExit("Invalid command version/length")
    if binascii.crc_hqx(b[:18], 0xffff) != struct.unpack_from("<H", b, 18)[0]:
        raise SystemExit("Command header CRC16 failed")
    if crc32(b[24:]) != struct.unpack_from("<I", b, 20)[0]:
        raise SystemExit("Command data CRC32 failed")
    seq, cmd = struct.unpack_from("<IH", b, 4)
    print("command", hex(cmd), "sequence", seq, "kind", b[10], "sender", b[11])
    data = b[24:]
    if cmd == 0x0101 and b[10] == 1:
        if len(data) < 3:
            raise SystemExit("Truncated inquiry ACK")
        result, count = struct.unpack_from("<BH", data)
        print("device result", hex(result), "returned keys", count)
        if result == 0:
            offset = 3
            for _ in range(count):
                if offset + 4 > len(data):
                    raise SystemExit("Truncated TLV header")
                key, size = struct.unpack_from("<HH", data, offset)
                offset += 4
                if offset + size > len(data):
                    raise SystemExit("Truncated TLV value")
                show_value(key, data[offset:offset + size])
                offset += size
            if offset != len(data):
                print("trailing bytes", len(data) - offset)
else:
    if len(b) < 36:
        raise SystemExit("Truncated measurement prefix")
    version = 1 if model == "avia2" else 0
    if b[0] != version or struct.unpack_from("<H", b, 1)[0] != len(b):
        raise SystemExit("Measurement version/length does not match model")
    if crc32(b[28:]) != struct.unpack_from("<I", b, 24)[0]:
        raise SystemExit("Measurement timestamp/data CRC32 failed")
    count, counter = struct.unpack_from("<HH", b, 5)
    kind, clock = b[10], b[11]
    stamp = struct.unpack_from("<Q", b, 28)[0]
    sizes = {0: 24, 1: 14, 17: 28} if model == "avia2" else {0: 24, 1: 14, 2: 8, 3: 10}
    if kind not in sizes or (model == "mid360l" and kind == 3):
        raise SystemExit("Unsupported payload type for selected model")
    if 36 + count * sizes[kind] != len(b):
        raise SystemExit("Declared count/stride does not match datagram")
    print("type", kind, "count", count, "UDP counter", counter,
          "clock", clock, "timestamp ns", stamp)
    if model != "avia2" and count > 1 and kind != 0:
        span_ns = struct.unpack_from("<H", b, 3)[0] * 100
        print("first/last point ns", stamp, stamp + span_ns)
    if count and kind in (1, 17):
        xyz = struct.unpack_from("<iii", b, 36)
        print("first XYZ m", tuple(v / 1000 for v in xyz), "raw tag", b[49])
    elif count and kind == 0:
        imu = struct.unpack_from("<6f", b, 36)
        print("gyro rad/s", imu[:3], "accel g", imu[3:])
```

1. Export a known measurement payload and a separate successful `0x0101` inquiry ACK from the **same identified model**. Exporting only the UDP data, not the surrounding headers, is essential.
2. Run `python3 livox_payload_inspect.py MODEL measurement.bin`, replacing `MODEL` with the applicable value above. Run it again on `inquiry-ack.bin`.
3. Compare length/type/counter/clock and the decoded identity with the capture. Keep failures as evidence rather than deleting CRC checks or changing the model argument until a packet passes.

**Expected result:** the program either prints CRC-validated packet fields and the returned key values, or stops with a specific framing/model/CRC/count error. Avia 2 never prints an invented MID-360 point-time interval. This is an original offline inspection example; execution, SDK compilation and sensor testing have not been performed here. The accepted HMS key `0x0811` is printed only if actually observed: the Avia 2 web table uses that spelling, whereas the pinned SDK and series table use `0x8011`. Neither spelling is sent to a sensor by this program. [Protocol data/command tables](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/livox_eth_protocol_mid360.html), [Avia 2 model contract](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/livox_eth_protocol_avia2.html).

## Troubleshooting and FAQs

### FAQ <a href="#faq" id="faq"></a>

| Symptom                              | Ordered diagnosis and supported recovery                                                                                                                                       |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| No device found                      | Measure/check supply at the sensor, keyed cable and Ethernet link; verify host subnet and actual serial-derived address; allow broadcasts/UDP on the sensor interface          |
| Discovery works, no points           | Check Sampling versus Idle/Ready/Error state, competing Viewer/SDK client and correct host target address; inspect packets before changing a decoder                           |
| ROS sees no S device                 | S-specific type 8/config/model key, correct sensor IP, installed config path and exact launch; the shipped example addresses are not auto-discovery                            |
| Cloud is denser only after waiting   | Expected non-repetitive accumulation; distinguish an integration window from a single frame                                                                                    |
| Missing close dark/thin target       | Reference-only 0.1–0.2 m zone and target limitations; assess geometry/reflectivity before changing filters                                                                     |
| IMU appears displaced                | Use the documented sensor/IMU origin relationship, measured robot transform and expected axis convention; a zero extrinsic template is not calibration                         |
| Time jumps or fusion smears          | Check PTP/GPS mode/status, master time, packet timestamps and host backlog; do not substitute host receive time silently                                                       |
| Thermal warning / repeated startup   | Inspect metal thermal path, airflow, housing temperature and supply startup headroom; do not operate through persistent error status                                           |
| Water spots or dust create artifacts | Power down, remove loose particles with clean air first, then use lens tissue and small amount of isopropyl alcohol as documented; do not wipe abrasive dirt across the window |

For normal recovery, close the owning application, save logs/configuration and restart the sensor/Viewer after wiring and supply checks. Firmware upgrade is a separate procedure: obtain the exact S package/release notes, maintain power/network and preserve configuration. Never use MID-360 or MID-360L firmware as a trial fix. Store dry at −40 to 70 °C; inspect stored connectors and protect the sensor in transit. [Manual §§4–5](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf).

### Best Practices and Limitations <a href="#best-practices-and-limitations" id="best-practices-and-limitations"></a>

* Mount high enough to avoid chassis occlusion while preserving near-field obstacle detection.
* Protect the optical window from dust, water spots, fingerprints, and impact.
* Use stable power and robust Ethernet strain relief on mobile platforms.
* Validate dark, glossy, glass, thin, and low-reflectivity obstacles in the real operating environment.
* Do not rely on SLAM alone for functional safety; safety-rated robot functions require system-level safety design.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

### MID-360 series diagnostic actions and timing acceptance

The published HMS list contains the following abnormal-ID groups. Combine each ID with the code's actual severity; the same scanning group can report recoverable and fatal states. IDs specifically labeled S or L do not establish that another model implements them.

| Abnormal ID / level                     | Interpretation and ordered response                                                                     |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `0x0102`, `0x0103`, warning             | Elevated ambient temperature: inspect ambient and heat-transfer path before increasing runtime          |
| `0x0104`, warning                       | Contaminated optical window: clean using the exact model procedure, then compare the same scene         |
| `0x0105`, warning                       | Upgrade failure: save updater/version/log evidence and follow exact-package recovery                    |
| `0x0111`, `0x0112`, fatal               | Internal temperature abnormal: correct thermal conditions; do not repeatedly request Sampling           |
| `0x0113`, fatal                         | IMU stopped: retain logs and use the supported restart/service route                                    |
| `0x0114` error / `0x0115` fatal         | High ambient / temperature limit exceeded with stopped operation                                        |
| `0x0116`, fatal                         | External voltage abnormal: measure the correct sensor supply under load before retrying                 |
| `0x0117` / `0x0118`, fatal              | Parameter abnormality / damaged internal components; preserve evidence and escalate persistent faults   |
| `0x0201`, warning                       | Scan-module heating: wait for readiness; do not confuse warm-up with a network outage                   |
| `0x0210–0x0219`, error or fatal         | Scan module recovering or failed: observe progress; persistent errors need supported restart/service    |
| `0x021C`, warning, L-specific           | Code disk contamination/abnormal speed; unresolved after supported recovery requires factory inspection |
| `0x0304`, warning                       | Ranging/TIA DC abnormality: retain capture and status; use supported recovery                           |
| `0x0401`, warning, S-specific           | Link recovered after link-down: check cable/converter/interface history                                 |
| `0x0402` / `0x0403`, warning            | PTP stopped/excessive time difference / unsupported PTPv2.1 source                                      |
| `0x0404` / `0x0405` / `0x0406`, warning | PPS abnormal / synchronization exception / low synchronization accuracy                                 |
| `0x0407` / `0x0408` / `0x0409`, warning | Missing GPS / missing PPS / abnormal GPS information                                                    |
| `0x040A`, warning                       | PTP and gPTP present together; fix topology instead of changing point decoding                          |

[Official MID-360/S/L HMS table](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/mid360/hms_code_mid360.html).

For an isolated **PTP UDP/IPv4** commissioning check after the initial cloud works:

1. Record the current clock source and network configuration. Choose the dedicated wired adapter and use `ethtool -T ACTUAL_INTERFACE` to check hardware/software transmit and receive timestamp capabilities. A graphics display of moving points is not a clock test.
2. Use the documented Linuxptp master configuration on the isolated sensor network; the common Livox example invokes `sudo ptp4l -i ACTUAL_INTERFACE -l 6 -m`. This changes the timing environment and belongs only on a deliberately selected master. Do not start a second competing master. The source's gPTP automotive configuration is a different profile and is **not supported by MID-360L**.
3. Inspect Sync/Follow\_Up/Delay traffic, Viewer2 sync status, packet clock type and queried time offset/HMS. Establish a stable master and acceptable offset for the application before trusting motion compensation; receipt of a single Sync packet only proves that traffic exists.
4. Record the clock configuration with cloud/IMU data and compare monotonic sensor timestamps. If the master disappears, inspect the reported state and offset rather than declaring holdover externally synchronized. Restore the previous time service when ending an isolated commissioning session.

**Expected result:** a consistent supported clock source, stable device/master relationship and no unresolved timing HMS warning; no numerical synchronization accuracy is claimed without measurement. The manufacturer's common tutorial includes `phc2sys` for changing clock relationships, but that host-clock operation is separate from proving sensor lock and is not required for this readback procedure. [Livox Linuxptp and GPS tutorial](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/common/time_sync.html).

For extended storage, keep the S/L device within its documented dry −40 to +70 °C storage envelope, protect connectors and use clean cushioned packaging for transport. If unused for more than three months, inspect the sensor and connectors regularly for abnormalities. Remove loose dust with clean air before gently using lens tissue; a small amount of isopropyl alcohol is permitted by these exact manuals for remaining stains. That permission does not apply to every other LiDAR's optical material. Keep electrical interfaces dry before the next power-up. [MID-360S manual, storage/maintenance](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf), [MID-360L manual, storage/maintenance](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf).

## Downloads and technical documents

### Official Downloads and Resources <a href="#official-downloads-and-resources" id="official-downloads-and-resources"></a>

The manual's original connector, coordinate and dimension drawings remain authoritative. They were inspected for this guide; follow the direct PDF instead of reconstructing dimensions from a render. Existing file attachments below remain available.

| Resource                                                                                                                       | Exact scope and purpose                                                           |
| ------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------- |
| [MID-360S manual](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf) | v1.0,2026.04; connector, power events, data/state and maintenance                 |
| [Official S download center](https://www.livoxtech.com/mid-360s/downloads)                                                     | Manual, product information, sensor/FOV/splitter CAD, Viewer and exact S firmware |
| [Pinned SDK2](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md)                 | Build, C/C++ API and quick-start samples                                          |
| [Pinned ROS Driver2](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md)   | ROS1/ROS2 model-specific launch and message formats                               |

Use the current download center for the original STP and binary URLs; exact observed direct links are retained in this guide's established references. The manual is copyrighted by Livox and is linked for operation; this guide adds original procedures rather than reproducing its prose.

### Original document attachments

{% file src="../../.gitbook/assets/Livox MID-360S KCC Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S ROHS Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S SVHC Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S_CB Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S_CE Certification Certificate.pdf" %}

{% file src="../../.gitbook/assets/Livox MID-360S_FCC Certification Certificate.pdf" %}

### MID-360 Original Variant Resources <a href="#mid-360-original-variant-resources" id="mid-360-original-variant-resources"></a>

If you buy the original MID-360 variant, use the [Livox MID-360 downloads page](https://www.livoxtech.com/mid-360/downloads) for its firmware, quick-start guide, sample data, Viewer packages, and CAD. Do not flash MID-360S firmware onto MID-360 hardware unless Livox explicitly confirms compatibility.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

### Download Center <a href="#download-center" id="download-center"></a>

The S download center separates the user manual, product information, sensor CAD, FOV model, splitter CAD, Viewer2 packages and firmware/release notes. Use the concrete resource table in this section to choose the file type; firmware 35.01.0113 and Viewer2 2.5.9 are the reviewed S downloads, not MID-360L files.

[Model-specific source](https://www.livoxtech.com/mid-360s/downloads).

## References and validation

### Source Notes <a href="#source-notes" id="source-notes"></a>

Reviewed **24 November 2026**: the exact two store options, MID-360S manual/specifications/download list and pinned SDK/ROS sources. Sensor-side connector and dimension pages were visually inspected. The address-editing example is original.

**SDK/ROS compilation, Viewer execution, firmware updates, power measurements and physical point/IMU tests were not run.** Syntax checks validate the displayed code's syntax only. Range, precision and rates above are manufacturer-reported under their stated conditions.

* [MID-360S User Manual](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/UM/Livox_Mid-360s_User_Manual_en.pdf) — v1.0,2026.04; published download listing 2026-06-01.
* [MID-360S specifications and test conditions](https://www.livoxtech.com/mid-360s/specs) — current 24 Nov 2026.
* [MID-360S official download inventory](https://www.livoxtech.com/mid-360s/downloads) — current 24 Nov 2026.
* [Livox SDK2 build and API entry points](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md) — commit c0796f04c143143899c87a773d9f6b7136453c0b.
* [Livox ROS Driver2 supported models, platforms and data types](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [S-specific type 8 network configuration](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/MID360s_config.json) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [S-specific PointCloud2 ROS2 launch](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/launch_ROS2/rviz_MID360s_launch.py) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [Point/IMU topic publication](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/src/lddc.cpp) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [OpenELAB S sensor/kit exact SKU and BOM](https://openelab.io/products/livox-mid360) — 23 Nov catalog; public page read 24 Nov 2026.

### Additional established references

* [Product Information PDF](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/PI/Livox_Mid-360s_Product_Information.pdf)
* [MID-360S STP model](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/Mid-360S%203D%20Model/mid-360S.stp)
* [MID-360S FOV STP model](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/Mid-360S%20FOV%E6%95%B0%E6%A8%A1/mid-360s_fov.stp)
* [Splitter cable STP](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Download/Livox%20%E8%88%AA%E6%8F%92%E4%B8%80%E5%88%86%E4%B8%89%E7%BA%BF.stp)
* [Windows](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/Livox%20Viewer%202%20-%20Windows/Viewer2_2.5.9_Windows.zip)
* [Ubuntu](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360S/Livox%20Viewer%202-%20Ubuntu/Viewer2_2.5.9_Linux.zip)
* [Livox MID-360 downloads page](https://www.livoxtech.com/mid-360/downloads)
* [MOLA MID-360 example](https://github.com/Whan000/MOLA-SLAM)
* [fast\_lio\_tinker](https://github.com/tinkerfuroc/fast_lio_tinker)
* [LIO-SAM-MID360](https://github.com/nkymzsy/LIO-SAM-MID360)
* [CMU mecanum autonomy stack](https://github.com/jizhang-cmu/autonomy_stack_mecanum_wheel_platform)

### Supporting resource links

* [Livox SDK2](https://github.com/Livox-SDK/Livox-SDK2)
* [Livox MID-360S product page](https://www.livoxtech.com/mid-360s)
