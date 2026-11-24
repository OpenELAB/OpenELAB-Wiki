---
description: >-
  Power MID-360L at 12–27 V, wire its exact M12 interface and configure
  serial-derived networking for cloud/IMU acquisition with the actual SDK2/ROS2
  MID360L target.
---

# Livox MID-360L LiDAR Engineering Guide

{% hint style="info" %}
[**View Livox MID-360L 360° 3D LiDAR for AMR Robots, Autonomous Forklifts and Mapping on OpenELAB**](https://openelab.io/products/livox-mid-360l-3d-lidar?variant=48326284214470)

**Model / option:** LiDAR + Cable + Adapter · **SKU:** `Livox-MID-360L-Kit`
{% endhint %}

## Product overview

### Product and scope <a href="#product-and-scope" id="product-and-scope"></a>

**Livox MID-360L is a low-power 360° 3D LiDAR with a −10° to +34° vertical field, 100,000 first-return points/s and integrated IMU.** The assigned `Livox-MID-360L-Kit` is the **LiDAR + Cable + Adapter** option; the sensor-only `Livox-MID-360L` is separate. This guide retains MID-360L's own canonical page and uses its exact SDK2/Driver2 target, not original MID-360 or MID-360S settings. [Exact IO kit](https://openelab.io/products/livox-mid-360l-3d-lidar), [official specifications](https://www.livoxtech.com/mid-360l/specs).

MID-360L needs **12–27 V**, with 15 V recommended in the manual. A physically fitting Livox cable does not establish compatible power or pin functions: Avia2, for example, uses contacts 11/12 for ground/power, while MID-360L reserves them as output IO.

## Applications

Use MID-360L for AMR perception, warehouse scene capture, low-power mapping and LiDAR/IMU odometry research. Its downward −10° sector helps observe nearer ground-level structure, while its upward field supports surrounding objects. Design the mounting height/pitch around the actual scan envelope and target sizes.

The non-repetitive pattern fills the field over time. Compare a stationary short capture with a longer accumulation before selecting a perception integration window. On a moving robot, retain per-point time and apply a separately verified motion model. The 0.1–0.2 m near-limit region is reference-only; thin or dark near targets can be unreliable. [Manual FOV/scanning and specification notes](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf).

## Specifications

### Hardware and technical documents <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

| Parameter                  | MID-360L                                              |
| -------------------------- | ----------------------------------------------------- |
| Laser / safety             | 905 nm, Class 1 IEC60825-1:2014                       |
| FOV                        | 360° horizontal;−10° to +34° vertical, typical        |
| Range at 100 klux          | 45 m at 10% reflectivity, typical;100 m cutoff        |
| Blind zone                 | 0.1 m;0.1–0.2 m output has no guaranteed precision    |
| Range precision,1σ         | ≤3 cm at 10 m;≤5 cm at 0.2 m,25 °C/80%-target test    |
| Angular precision          | <0.3°,1σ                                              |
| Point / typical frame rate | 100,000 points/s first return /10 Hz                  |
| Ethernet / time            | 100BASE-TX; PTP v2 UDP/IPv4 or GPS UTC+PPS            |
| IMU                        | ICM40609; default 200 Hz output                       |
| Sensor supply              | 12–27 V DC;15 V recommended                           |
| Running / startup power    | 4.2 W /14 W for about 1 s; unit/environment dependent |
| Body / mass                | 65 × 65 × 63 mm;245 g                                 |
| Environment                | −20 to +65 °C operating; IP67 sensor                  |
| Storage                    | −40 to +70 °C in this manual                          |

[Official current specifications](https://www.livoxtech.com/mid-360l/specs), [manual power/storage](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf). A 100 m cutoff is not a 100 m detection guarantee for a dark object. Precision conditions and complete system accuracy are different. Use the actual adapter's rating and allow startup/cable drop; do not size it from 4.2 W alone.

## Hardware and connections

### M12 contacts and cable orientation

MID-360L uses a shielded 12-pin A-code male M12; the recommended female mate is Finecables MA12FAHD12STXXXB14. The manual's sensor/mating-face drawings and splitter table were visually inspected. Match the keyed view and contact numbers rather than viewing the cable from the rear.

| Sensor contact | MID-360L function                                            |
| -------------- | ------------------------------------------------------------ |
| 1,9            | Power +,12–27 V                                              |
| 2,3            | Ground                                                       |
| 4 /5           | Ethernet TX+ /TX−                                            |
| 6 /7           | Ethernet RX+ /RX−                                            |
| 8              | PPS input,3.3 V LVTTL                                        |
| 10             | GPS GPRMC input,3.3 V LVTTL;9600 baud,8 data bits, no parity |
| 11,12          | Reserved 3.3 V LVTTL output IO; leave disconnected           |

[Manual connector definition](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf). Neither GPS input accepts an assumed RS232 signal. Do not drive reserved output pins or borrow an Avia2 pinout. Optional sync leads are not required for first cloud acquisition; leave them insulated. Do not connect a PoE device to the splitter RJ45. The standard bench splitter's exposed branches do not inherit the sensor's IP67 rating.

### Supply, mounting and thermal path

Connect with power off. Keep voltage at the sensor ≥12 V and ≤27 V at all times, including transients. The manual recommends 15 V; verify the included adapter's actual output before energizing. Cold environments and longer cables need additional voltage-drop margin within the 27 V ceiling. Other loads switching off on a shared supply can create overvoltage.

Use the four bottom M3 holes,5 mm deep, with appropriate engagement after bracket thickness. Mount on a flat conductive metal plate ≥3 mm thick, with ≥10,000 mm² exposed area and thermal interface material. Leave ≥10 mm clearance around the sensor and avoid an enclosed heat trap. Keep the bottom shell below 80 °C in extreme conditions; that is a shell limit, not the ambient rating. Maintain ≥60 mm cable bend radius. Tighten only the M12 metal nut to 1.5–2.0 N·m without twisting the cable. [Manual mounting/power/connection](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf).

### Coordinates, tags and time

The IMU origin is **(23.68,−22.05,−43.86) mm** in the cloud frame, with parallel axes. Retain that translation in robot calibration; do not copy the MID-360S offset. The sensor stores extrinsic values but does not itself apply them to outgoing point coordinates. Check where a host driver applies a transform to avoid double correction.

MID-360L's tag groups are model-specific: bits 5–4 describe window contamination, bits 3–2 atmospheric particles and bits 1–0 close-range blooming/dragging, with 0 clean and increasing values lower confidence. Bits 7–6 are reserved. Do not apply original MID-70 return-number semantics. Invalid/out-of-range Cartesian points can be 0,0,0. Timestamps are 64-bit nanoseconds, but correct absolute time still depends on the selected/locked source. PTP here supports UDP/IPv4 Sync,Follow\_up,Delay\_req/resp; it is not automatically gPTP. [Manual output/timing](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf).

## Software and development resources

### Development software and recovery <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

Use the actual `MID360l_config.json` and `rviz_MID360l_launch.py` from the reviewed Driver2. The JSON model key is **`Mid360l`**, not `Mid360s` or `MID360`. SDK2 and Driver2 explicitly support the model. The workflow below uses documented Ubuntu 22.04/ROS2 Humble. Viewer2's documented manual host baseline is Windows 10 x64/Ubuntu 18.04 x64; keep GUI and ROS support claims distinct. [Driver2 README](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md).

| Network setting                         | MID-360L configuration                                          |
| --------------------------------------- | --------------------------------------------------------------- |
| Factory sensor IP                       | `192.168.1.1XX`, where XX is the final two serial-number digits |
| Host commissioning IP                   | 192.168.1.50/24                                                 |
| Sensor command/push/cloud/IMU/log ports | 56100/56200/56300/56400/56500                                   |
| Host defaults                           | 56101/56201/56301/56401/56501                                   |
| Config type/key                         | `lidar_type:8`, model section `Mid360l`                         |
| Shipped JSON example                    | Host `.5`, sensor `.12`; replace with observed endpoints        |

[Actual MID360L configuration](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/MID360l_config.json), [manual factory address](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf). The example's `.12` is not a guaranteed factory IP. Record actual serial/IP and retain the model-specific section. The current download center lists Viewer2 **2.6.2**, MID360L firmware **41.52.00.03**, manual/CAD/FOV and release notes. Firmware is model-specific and unnecessary to obtain a first known-good capture. [Downloads](https://www.livoxtech.com/mid-360l/downloads).

### SDK2 configuration, callbacks and ROS message contracts

For **MID-360L**, keep the exact `MID360l_config.json` model section used above. `lidar_net_info` describes the sensor ports; each `host_net_info` entry describes a receiving host and its ports. Editing the local JSON changes the application's intended endpoints; changing a device's persistent IP requires a separate acknowledged device operation. The SDK README's HAP example is not this model's configuration.

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

Choose the subscriber format before recording. For `CustomMsg`, reconstruct each point from the timebase and its relative offset; preserve the clock type and units supplied by the driver. Keep sensor calibration separate from a host transform and apply each extrinsic exactly once. The generic README's `blind_spot_set` is HAP-only, so do not add it to this configuration to hide near-field artifacts. [Driver2 settings and message fields](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md), [exact model configuration](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/MID360l_config.json).

The manual distinguishes actual states **Sampling, Idle, Ready, Error, Self-check, Startup and Upgrading** from user-selected target modes **Sampling, Idle and Ready**. Idle retains communication while other components are powered down; Ready is prepared to emit, and Sampling is active measurement. During recovery, retain the status/log record, correct supply/thermal/network causes and recheck actual state before resuming acquisition. Do not repeatedly send mode or reboot requests to mask an Error state.

### Series packet framing, clock interpretation and diagnostics

The series protocol **v1.4.12 (21 September 2026)** explicitly covers MID-360, MID-360S and MID-360L. It uses little-endian UDP fields. Discovery is a broadcast query to port **56000**, separate from the 56100 command channel; discovery across an address mismatch does not prove that unicast data can reach the configured host. **MID-360L does not support multicast cloud/IMU output, spherical-coordinate data or gPTP.** Use its documented unicast Cartesian and PTP/GPS paths; the common SDK options do not override these device restrictions.

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

For **MID-360L**, begin with the exact supported time modes listed above. A large nanosecond timestamp does not itself prove UTC or synchronization quality. Observe the selected source in Viewer2 and packet `time_type`, then inspect synchronization/HMS status and offsets. PTP uses a master and the LiDAR as slave; multiple masters or mixed PTP/gPTP traffic can produce a clock problem even while point clouds arrive.

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

The pinned SDK reports this model as device type **41**. Driver2 JSON `lidar_type:8` is a configuration classification, not that discovery device-type byte. Keep these identifiers in their own fields. [SDK device enum](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/include/livox_lidar_def.h).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result with the exact kit

1. Record the MID-360L serial and actual kit cable/adapter labels. Secure the sensor with an unobstructed field and thermal path. Connect the approved splitter with power off; insulate function leads.
2. Set the dedicated host adapter to **192.168.1.50/24**. Determine the factory sensor address from the final two serial digits, then confirm by discovery/ARP. Example: serial ending 42 gives `.142`, not `.42`.
3. Enable the approved supply and open a supporting Viewer2 build. Select the observed MID-360L serial/IP, record firmware, status and time mode, and request Sampling if necessary.
4. Inspect a diffuse target outside the reference-only near zone. Record a short sequence and replay it; check scene orientation and stable geometry before adding robot motion.

**Expected result:** the correct MID-360L reaches Sampling and provides a replayable 360° cloud plus enabled IMU stream. Discovery alone is not a cloud checkpoint. [Manual connection/Viewer](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf).

### Build SDK2 and the actual ROS2 target

On a prepared Ubuntu 22.04/Humble host with compiler/CMake:

```bash
mkdir -p ~/mid360l_dev
cd ~/mid360l_dev
git clone https://github.com/Livox-SDK/Livox-SDK2.git
cd Livox-SDK2
git checkout c0796f04c143143899c87a773d9f6b7136453c0b
mkdir -p build
cd build
cmake ..
make -j2
sudo make install
mkdir -p ~/mid360l_ws/src
cd ~/mid360l_ws/src
git clone https://github.com/Livox-SDK/livox_ros_driver2.git
cd livox_ros_driver2
git checkout 21445540f0d100dc86a7e6df312dd70bbdb4afdf
```

From the Driver2 repository directory, this original local patch prompts for the **observed sensor address** and changes only the JSON endpoints:

```python
import ipaddress
import json
from pathlib import Path

sensor = ipaddress.IPv4Address(input("Observed MID-360L IP: ").strip())
network = ipaddress.IPv4Network("192.168.1.0/24")
if sensor not in network or str(sensor) in {"192.168.1.0", "192.168.1.50", "192.168.1.255"}:
    raise SystemExit("Use the observed distinct sensor address on this commissioning subnet")
p = Path("config/MID360l_config.json")
c = json.loads(p.read_text())
assert "Mid360l" in c and len(c["lidar_configs"]) == 1
for host in c["Mid360l"]["host_net_info"]:
    host["host_ip"] = "192.168.1.50"
c["lidar_configs"][0]["ip"] = str(sensor)
p.write_text(json.dumps(c, indent=2) + "\n")
print("Mid360l endpoints updated locally; sensor configuration was not changed")
```

**Expected result:** the local model-specific config contains the observed sensor and host `.50`; it does not change the device IP. Then:

```bash
source /opt/ros/humble/setup.bash
./build.sh humble
cd ~/mid360l_ws
source install/setup.bash
ros2 launch livox_ros_driver2 rviz_MID360l_launch.py
```

Close Viewer2 before the driver takes ownership. In a second sourced terminal, check:

```bash
ros2 topic list -t
ros2 topic hz /livox/lidar
ros2 topic hz /livox/imu
ros2 topic echo /livox/lidar --once --field header
```

**Expected result:** current cloud/IMU topics and coherent RViz geometry. Match `xfer_format` to PointCloud2 versus CustomMsg before adding a subscriber. Host publication frequency is not the 100,000 points/s acquisition rate. Preserve ring/time and actual sensor-clock policy when preparing motion compensation. [Driver2 build/launch](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md).

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

### FAQs <a href="#faqs" id="faqs"></a>

| Symptom                     | Model-specific checks                                                                                  |
| --------------------------- | ------------------------------------------------------------------------------------------------------ |
| No discovery                | Correct serial-derived `.1XX`, host `.50`, actual changed settings, matched cable and broadcast rules  |
| Repeated startup            | 12 V minimum at sensor,14 W startup, cable loss/cold margin and adapter capability                     |
| Connected, no cloud         | Sampling versus Idle/Ready/Error, actual MID360L target, host destination and competing client         |
| Wrong close-range filtering | MID-360L tag fields and reference-only 0.1–0.2 m region                                                |
| Misaligned motion/IMU       | Actual 23.68/−22.05/−43.86 mm offset, point timing and transform application exactly once              |
| Thermal warning             | Conductive plate, exposed area, clearance and shell temperature; do not enclose without thermal design |

**Can I reuse the original MID-360 page/config?** No. The assigned model has its own power/FOV/point-rate/calibration and exact Driver2 config. Preserve its distinct canonical guide.

**Are pins 11/12 spare power contacts?** No. They are reserved 3.3 V outputs here. Leave them isolated.

Remove loose dust before gently cleaning optics; the manual permits a small amount of isopropyl alcohol on lens tissue for remaining contamination. Store dry within −40 to +70 °C and inspect protected connectors during extended storage. Preserve configuration/logs before recovery. Use only MID360L firmware/release notes and a stable documented update path; do not flash MID360/MID360S files. [Manual maintenance/troubleshooting](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf).

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

| Direct resource                                                                                                                                                                                                                                   | Scope                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------- |
| [MID-360L manual v1.0](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf)                                                                                                      | 29-page source; connector, current power, coordinates, tags, mounting and maintenance |
| [MID-360L downloads](https://www.livoxtech.com/mid-360l/downloads)                                                                                                                                                                                | Product/FOV models, firmware 41.52.00.03, release notes and Viewer2 packages          |
| [Viewer2 Linux 2.6.2](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/Livox%20Viewer%202-%20Linux/Viewer2_2.6.2_Linux.zip)                                                                                                 | Official GUI distribution                                                             |
| [Viewer2 Windows 2.6.2](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/Livox%20Viewer%202%20-%20Windows/Viewer2_2.6.2_Win.zip)                                                                                            | Official GUI distribution                                                             |
| [SDK2](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md)/[MID360L config](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/MID360l_config.json) | Actual supported model/API/network target                                             |

The manufacturer splitter-face and electrical table were visually inspected. Retained figures/files remain below with their original native references.

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed 24 November 2026: exact MID-360L cable +adapter kit, current official manual/specifications/downloads and actual SDK2/Driver2 MID360L config/launch. Original MID360 and MID360S remain separate models/pages.

**SDK/ROS compilation, Viewer/script/live capture execution, firmware updates and physical electrical/thermal/range/timing tests: not run.** The local endpoint patch is original and syntax checked.

* [MID360L official User Manual](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/Mid-360L/UM/20261013/Livox_Mid-360l_User_Manual_en.pdf) — v1.0 2026.09; download revision 13 Oct 2026; 29 pages.
* [MID360L current official specifications](https://www.livoxtech.com/mid-360l/specs) — 24 Nov 2026.
* [MID360L official software/firmware/CAD inventory](https://www.livoxtech.com/mid-360l/downloads) — 24 Nov 2026.
* [Livox SDK2 supported models and build](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md) — commit c0796f04c143143899c87a773d9f6b7136453c0b.
* [Livox Driver2 supported MID360L launch](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [MID360L exact config key and endpoints](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/MID360l_config.json) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [MID360L actual ROS2 launch](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/launch_ROS2/rviz_MID360l_launch.py) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [Exact MID360L cable/adapter kit](https://openelab.io/products/livox-mid-360l-3d-lidar) — 23 Nov catalog plus observed public page 24 Nov.

### Additional established references

* [Livox-MID-360L-Kit](https://openelab.de/products/livox-mid-360l-3d-lidar)
