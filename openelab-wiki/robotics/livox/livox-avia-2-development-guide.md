---
description: >-
  Wire fan-equipped Livox Avia2 safely, compare Normal and Focus scanning, and
  acquire cloud/IMU data with the exact SDK2 and ROS2 Avia2 configuration.
---

# Livox Avia 2 With-Fan LiDAR Engineering Guide

{% hint style="info" %}
[**View Livox AVIA 2 1535 nm Fiber Laser LiDAR with Fan on OpenELAB**](https://openelab.io/products/livox-avia2-fiber-laser-lidar?variant=46030720630982)

**Model / option:** Default Title · **SKU:** `Livox-AVIA2`
{% endhint %}

## Product overview

### Product and applications <a href="#product-and-applications" id="product-and-applications"></a>

**Livox Avia 2 is a 1535 nm fiber-laser LiDAR with selectable wide-field Normal and narrow-field Focus scanning.** This guide covers the fan-equipped `Livox-AVIA2` option, not original Avia or Avia 2 NF. Normal provides an 80° × 80° field; Focus concentrates acquisition into 15° × 15°. A built-in IMU and Ethernet/UDP output support timestamped scene capture with Livox SDK2 and the actual Avia2 Driver2 target. [Official specifications](https://www.livoxtech.com/avia-2/specs).

The included fan, its airflow clearances and approximately 50 W steady demand materially affect installation. A MID-360 power adapter, cable pinout or launch file is not a substitute. Verify whether the matched Avia 2 breakout cable and adequately rated supply are included in the received package before commissioning.

## Applications

### Select the field before designing the task

Use Normal for forward perception, terrain/structure capture and broad target search. Use Focus for a known distant region, after checking alignment with a stationary scene. Its smaller field can miss hazards that remain visible in Normal. Compare modes with the sensor and target fixed; record range, reflectivity, illumination, integration window and mode together.

Non-repetitive scanning fills the field over time. Longer accumulation improves apparent coverage on a stationary structure but creates motion distortion on a moving carrier. Use per-point timing and a separately validated motion model for fusion. The 5 m blind zone makes this sensor unsuitable as the sole near-field obstacle detector. A long-range specification does not extend to all FOV positions, weather or targets. [Manual effective FOV/scanning/challenging scenarios](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf).

## Specifications

### Key specifications <a href="#key-specifications" id="key-specifications"></a>

| Parameter                         | Fan-equipped Avia 2                                                                     |
| --------------------------------- | --------------------------------------------------------------------------------------- |
| Laser                             | 1535 nm; Class 1, IEC60825-1:2014                                                       |
| Normal FOV / point rate           | 80° × 80° / 350,000 points/s                                                            |
| Focus FOV / point rate            | 15° × 15° / 100,000 points/s                                                            |
| Detection at 100 klx              | Normal: 400 m at 5%; Focus: ≥800 m at 10% reflectivity                                  |
| Stated maximum detection          | Normal 400 m; Focus 1000 m; not a target-independent guarantee                          |
| Blind zone                        | 5 m at 80% reflectivity                                                                 |
| Center range accuracy / precision | 5–400 m: ≤5 cm / ≤4 cm (1σ); 400–700 m: ≤10 cm / ≤6 cm (1σ)                             |
| Angular precision                 | ≤0.02° (1σ)                                                                             |
| Returns                           | Single strongest, single first, dual                                                    |
| IMU                               | ICM40609D, 6-axis; default 200 Hz output                                                |
| Interface / time                  | 100 Mbps Ethernet/UDP; GPS PPS+GPRMC, PTP, NTP                                          |
| Supply                            | 9–27 V DC at sensor, including transients                                               |
| Power                             | 55 W startup; 50 W regular steady state; 45 W low-temperature steady state with fan off |
| Body with fan / mass              | 146 × 113 × 139 mm (±0.5 mm); ≤1.8 kg                                                   |
| Body without fan / mass           | 146 × 113 × 103 mm; ≤1.5 kg; dimensional comparison, not permission to remove it        |
| Environment                       | −20 to +65 °C operating; −40 to +85 °C storage; sensor IP66                             |

[Official specification conditions](https://www.livoxtech.com/avia-2/specs), [manual §§3/5](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf). The range-precision test conditions are controlled, center-field and temperature/target dependent. At ambient above 50 °C with frequent restarts, Livox recommends individual continuous periods no longer than five minutes. Do not treat the upper operating-temperature number as an unrestricted restart policy.

## Hardware and connections

### M12 wiring and connector orientation

The sensor uses a 12-pin A-code **male** M12. The manual recommends Finecables MA12FAHD12STXXXB14 as the mating female. Use the male face drawing on p 8 and the separately drawn female harness face on p 9; they are opposite mating views. Do not count pins from an arbitrary cable photograph.

| Sensor pin(s) | Avia 2 function    | Boundary                                             |
| ------------- | ------------------ | ---------------------------------------------------- |
| 1, 9, 12      | Power +            | 9–27 V DC; all three are supply contacts             |
| 2, 3, 11      | Ground             | Supply and synchronization reference                 |
| 4 / 5         | Ethernet TX+ / TX− | Differential Ethernet pair                           |
| 6 / 7         | Ethernet RX+ / RX− | Differential Ethernet pair                           |
| 8             | PPS\_IN            | 3.3 V LVTTL input                                    |
| 10            | GPS\_IN            | 3.3 V LVTTL, GPRMC 9600 baud, 8 data bits, no parity |

[Manual connector table and face drawings, pp 8–9](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf). Pins 11/12 are **ground/power** here, not the reserved contacts of smaller Livox models. Leave optional synchronization branches insulated during initial acquisition. Neither sync input accepts an assumed RS232 voltage. Use the matched 1.5 m Avia 2 one-to-three cable for bench evaluation; its exposed branches are not an IP66 field harness.

### Power and mounting

Choose an approved supply delivering **more than 55 W**, with cable drop and startup current allowed for. At 12 V, 55 W corresponds to about 4.6 A before losses; this calculation is a sizing check, not a measured transient or fuse recommendation. Do not hot-plug the sensor. Connect while de-energized, verify polarity, then enable the supply. Keep the sensor input within 9–27 V at all times. Shared loads switching off can create harmful overvoltage. [Manual external power](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf).

Use the dimensioned M2.5 mounting holes, 4 mm deep, and a conductive metal mounting plate at least 3 mm thick. Leave at least 10 mm around the body and 30 mm at inlet/outlet sides. Do not obstruct cooling with a weather enclosure or attach an extra payload to the housing. Tighten the M12 metal nut to the documented 1.5–2.0 N·m without twisting the cable. [Manual installation/connection](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf).

### Frames, output and modes

Cloud coordinates and IMU axes have the same orientation; IMU origin in the cloud frame is **(−56.3149, 36.7201, −29.7031) mm**. A translation is still needed before treating IMU samples as coincident with the optical frame. Point fields include coordinates, received intensity, tag and a 64-bit nanosecond timestamp. Invalid/out-of-range points can have zero coordinates. The manual marks the tag reserved; do not borrow another model's bit filter. [Manual coordinates/output](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf).

Idle, Ready and Sampling are requested modes; Startup, Self-check, Error and Upgrading describe observed states. The manual contains both an Idle default statement and a power-on output statement: read the actual current state, then deliberately request Sampling through Viewer2/SDK2. Merely discovering an IP is not proof of cloud acquisition.

## Software and development resources

Use the reviewed **Livox SDK2** and **livox\_ros\_driver2**, whose repository contains `config/AVIA2_config.json` and `rviz_AVIA2_launch.py`. Original Avia's first-generation SDK target is a different product. The current Driver2 README documents Ubuntu 22.04 / ROS2 Humble among its targets; Viewer2's manual baseline is Windows 10 64-bit or Ubuntu 18.04 64-bit. Keep GUI and ROS host support claims separate. [Driver2 README](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md), [SDK2 README](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md).

The actual Avia2 config uses model key `Avia2`, `lidar_type: 8`, sensor command/push/point/IMU/log ports **56100/56200/56300/56400/56500** and corresponding host defaults ending **101/201/301/401/501**. Its example `.12` sensor and `.5` host addresses are placeholders, not the manual's factory `.4` sensor address. Retain the Avia2 model section while replacing the two real endpoints. [Exact configuration](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/AVIA2_config.json).

Download center inventory reviewed: Viewer2 2.6.0 Windows/Linux, fan and NF manuals/CAD/FOV models, breakout cable model and **AVIA 2 firmware 40.01.0506** release notes dated 2026-09-10. Do not flash NF or another family's firmware. An update is not necessary to establish the initial data checkpoint. [Download center](https://www.livoxtech.com/avia-2/downloads).

### SDK2 configuration, callbacks and ROS message contracts

For **Avia2**, keep the exact `AVIA2_config.json` model section used above. `lidar_net_info` describes the sensor ports; each `host_net_info` entry describes a receiving host and its ports. Editing the local JSON changes the application's intended endpoints; changing a device's persistent IP requires a separate acknowledged device operation. The SDK README's HAP example is not this model's configuration.

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

| Driver2 launch setting   | Supported meaning / consumer consequence                                                                                                       |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `publish_freq`           | Host cloud publication frequency, recommended examples 5, 10, 20 or 50 Hz, maximum 100 Hz; it does not change the sensor's physical point rate |
| `multi_topic:0` / `1`    | Shared cloud topic / independent topic per LiDAR; confirm resolved names with `ros2 topic list -t`                                             |
| `xfer_format:0`          | Livox `PointCloud2`: XYZ in m, reflectivity/intensity 0–255, tag, line and per-point timestamp                                                 |
| `xfer_format:1`          | `CustomMsg`: header, first-point `timebase`, `point_num`, `lidar_id`, then points containing `offset_time`, XYZ, reflectivity, tag and line    |
| `xfer_format:2`          | Generic PCL XYZI output is documented for ROS1 only; it removes the richer timing/tag/line contract                                            |
| `pcl_data_type:1` / `17` | Avia2 single / dual Cartesian records with int32 mm coordinates; generic int16/spherical modes are not supported by its protocol               |

Choose the subscriber format before recording. For `CustomMsg`, reconstruct each point from the timebase and its relative offset; preserve the clock type and units supplied by the driver. Keep sensor calibration separate from a host transform and apply each extrinsic exactly once. The generic README's `blind_spot_set` is HAP-only, so do not add it to this configuration to hide near-field artifacts. [Driver2 settings and message fields](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md), [exact model configuration](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/AVIA2_config.json).

The manual distinguishes actual states **Sampling, Idle, Ready, Error, Self-check, Startup and Upgrading** from user-selected target modes **Sampling, Idle and Ready**. Idle retains communication while other components are powered down; Ready is prepared to emit, and Sampling is active measurement. During recovery, retain the status/log record, correct supply/thermal/network causes and recheck actual state before resuming acquisition. Do not repeatedly send mode or reboot requests to mask an Error state.

### Avia2 protocol, frame timing and parameter keys

The official **Avia2-only protocol v1.0, 30 July 2026**, is distinct from the MID-360 series protocol. Its little-endian measurement header has **version 1** and data at byte **36**. Whole-payload length is at 1 (2 bytes), sample count at 5 (2), UDP counter at 7 (2), type/time source at 10/11, CRC32 at 24 (4) and nanosecond timestamp at 28 (8). **Bytes 3–4 are reserved**, not MID-360's `time_interval`. The frame counter at 9 is not enabled.

Avia2 groups measurements into **100 ms frames whose packets share one timestamp**. Do not apply the MID-360 packet's first-to-last equal-spacing interpolation formula to Avia2. Preserve the actual per-point timing produced by the Avia2-compatible SDK/Driver2 and verify its clock contract before deskew. The available measurement types are **0 IMU, 1 single Cartesian return and 17 (`0x11`) dual Cartesian returns**. A single point is 14 bytes: XYZ int32 mm, intensity and currently unused tag. A dual record is 28 bytes with two such echoes. Spherical/int16 modes offered by generic SDK APIs are not documented Avia2 formats. Raw IMU gyro is rad/s and acceleration g; confirm the selected host conversion before fusion. [Exact Avia2 framing/types/timestamps](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/livox_eth_protocol_avia2.html#point-cloud-imu-data-protocol).

| Avia2 parameter key       | Documented value / behavior                                                                                                    |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `0x0000 pcl_data_type`    | `0x01` single Cartesian / `0x11` dual Cartesian                                                                                |
| `0x0004 lidar_ipcfg`      | Twelve bytes for device IPv4, mask and gateway; not the host destination                                                       |
| `0x0005/0x0006/0x0007`    | State/cloud/IMU host-destination configuration, separate from changing sensor IPv4                                             |
| `0x001C imu_data_en`      | 0 disable / 1 enable IMU push                                                                                                  |
| `0x0022 fov_mode`         | 0 Focus; 1/2/3 Normal with 350k/300k/250k points/s profiles                                                                    |
| `0x0024 echo_mode`        | 0 intensity sorting/strongest single echo; 1 time sorting/first single echo                                                    |
| `0x0025 NTP_server_ip`    | Four-byte NTP server address                                                                                                   |
| `0x0027 ITO_ctrl`         | 0 glass heat off; 1 forced heat; 2 thermostatic automatic control                                                              |
| `0x0028 fog_noise_filter` | 0 off, 1 rain filtering, 2 fog filtering                                                                                       |
| Read-only identity/health | Serial `0x8000`, app/loader versions `0x8002/0x8003`, state `0x8006`, core temperature `0x8007` in 0.01 °C and diagnostic list |

These are protocol settings, not a recommendation to write a complete key list on startup. A parameter request **0x0100** returns a result plus the first failed key; query **0x0101** and pushed information **0x0102** use key/length/value records. Check ACK sequence, SDK transport status and device return code before treating a setting as applied. Keep factory reset/reboot (**0x0201/0x0200**), raw debug collection and staged upgrade (**0x0400–0x0403**) out of a first capture; they can reboot or interrupt data. The 24-byte control header uses **0xAA**, header CRC16 and separate data CRC32. [Control/key/return/CRC reference](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/livox_eth_protocol_avia2.html).

Time type **0/1/2/5** means boot-relative/PTP or gPTP/GPS/NTP. The official protocol limits GPS dates to **2000–2037**, excludes IEEE 1588v2.1 and discourages mixed PTP/gPTP masters. NTP is a lower-accuracy software option, not equivalent to hardware-timestamped PTP. HMS uses the model-specific code table and severity, preserving the full code with power, temperature and synchronization evidence before requesting recovery. [Avia2 time methods](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/avia2.html#supported-time-synchronization-methods), [Avia2 HMS codes](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/hms_code_avia2.html).

### Clock commissioning and log-based recovery

For **Avia2**, begin with the exact supported time modes listed above. A large nanosecond timestamp does not itself prove UTC or synchronization quality. Observe the selected source in Viewer2 and packet `time_type`, then inspect synchronization/HMS status and offsets. PTP uses a master and the LiDAR as slave; multiple masters or mixed PTP/gPTP traffic can produce a clock problem even while point clouds arrive.

Before configuring a Linux PTP master, use the read-only capability check **`ethtool -T INTERFACE`** with the actual dedicated adapter. The common Livox guide distinguishes software/hardware timestamp capability and documents a **linuxptp 3.1.1** example. Select the correct UDP/IPv4 or supported Layer-2 profile; do not copy an automotive gPTP configuration onto a model that excludes gPTP. Starting a master or synchronizing host hardware/system clocks changes the network/host timing environment, so use a deliberate isolated setup and retain the previous time service. [Official synchronization methods and capabilities](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/common/time_sync.html).

For GPS, check both **PPS electrical/timing requirements in this model's manual** and the absolute-time message path. The common guide recommends **9600 baud, 8 data bits, no parity**, valid GPRMC/GNRMC and stable fix; its UART example is specifically MID-360 and does not license another model's connector pin mapping. Hardware PPS plus software timestamp delivery is a different route from direct UART, with host delay considerations. Model manuals may specify stricter pulse widths than the common guide; preserve the model-specific range instead of relaxing it to the common minimum.

SDK2 logging is separately controlled by `lidar_log_enable`, `lidar_log_cache_size_MB` and `lidar_log_path`, with README defaults **true, 500 MB and current directory**. Choose a writable location with sufficient space before enabling unattended logging. Save actual serial/firmware, clock source, status/HMS, addresses and a short cloud/IMU capture together; SDK initialization success is not proof that each data channel or time source is working. Firmware upgrades stop acquisition and require the exact model image; retain settings/logs and a known-good recording before using the documented update tool. Do not use reset or a cross-model firmware image as an IP-discovery shortcut. [SDK2 logger/upgrade behavior](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md).

### Avia 2 complete payload and setting reference

The **Avia 2 v1.0 protocol (30 July 2026)** defines measurement offsets independently of the MID-360 family. Use version 1 at byte 0; length u16 at 1; reserved\[2] at 3; sample count u16 at 5; packet counter u16 at 7; currently unused frame counter u8 at 9; data/time types at 10/11; reserved\[12] at 12; CRC32 at 24; timestamp u64 at 28; data at 36. All multibyte values are little-endian. The packet counter resets at a frame boundary, but the frame-counter field itself is not enabled. **Every packet in a 100 ms frame shares its timestamp**; it is not a measurement-by-measurement time interval. [Avia 2 measurement protocol](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/livox_eth_protocol_avia2.html#point-cloud-imu-data-protocol).

| Data type                 | Offsets within each payload record                                             | Units / interpretation                                                           |
| ------------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| 0 IMU, 24 bytes           | float32 gyro XYZ at 0/4/8; float32 acceleration XYZ at 12/16/20                | rad/s; g. For an SI consumer, convert acceleration to m/s² exactly once          |
| 1 single return, 14 bytes | int32 XYZ at 0/4/8; uint8 intensity at 12; uint8 tag at 13                     | XYZ in mm, intensity raw byte; tag is not enabled                                |
| 17 dual return, 28 bytes  | First 14-byte echo at 0, second at 14: XYZ at 14/18/22, intensity/tag at 26/27 | Two echoes for a measurement; neither tag is an enabled MID-360 confidence field |

The protocol does not provide a MID-360-style per-packet `time_interval`. A raw developer cannot derive validated individual firing times merely by dividing 100 ms by a packet count: packet loss, return grouping and scan mode make that assumption unreliable. Use the Avia 2-compatible driver and retain its exact timing implementation/version for deskew; the public protocol's shared-frame timestamp is the bound on a custom parser. [Data/timestamp source](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/livox_eth_protocol_avia2.html).

| Configurable key               | Value length / type | Accepted meaning in Avia 2 v1.0                                                                                                |
| ------------------------------ | ------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `0x0000 pcl_data_type`         | 1 / u8              | 1 single Cartesian, 17 dual Cartesian; no compact-int16 or spherical mode                                                      |
| `0x0004 lidar_ipcfg`           | 12 / octets         | Device IP, mask and gateway, four bytes each                                                                                   |
| `0x0005 state_info_host_ipcfg` | 8                   | Destination IP\[4], destination port u16, **reserved u16**, not a writable source port                                         |
| `0x0006 pointcloud_host_ipcfg` | 8                   | Same layout for cloud destination                                                                                              |
| `0x0007 imu_host_ipcfg`        | 8                   | Same layout for IMU destination                                                                                                |
| `0x001A work_tgt_mode`         | 1 / u8              | Sampling 1, Idle 2, Ready 9                                                                                                    |
| `0x001C imu_data_en`           | 1 / u8              | Disable 0, enable 1; independent of a host ROS publisher being enabled                                                         |
| `0x0022 fov_mode`              | 1 / u8              | 0 Focus; 1 Normal 350k; 2 Normal 300k; 3 Normal 250k points/s                                                                  |
| `0x0024 echo_mode`             | 1 / u8              | 0 sort by intensity, strongest single echo; 1 sort by time, first single echo. Data type separately selects single/dual format |
| `0x0025 NTP_server_ip`         | 4 / octets          | IPv4 of the NTP time server                                                                                                    |
| `0x0027 ITO_ctrl`              | 1 / u8              | Window heat: 0 disabled, 1 forced on, 2 thermostatic automatic                                                                 |
| `0x0028 fog_noise_filter`      | 1 / u8              | 0 disabled, 1 rain filtering, 2 fog filtering; record before comparing datasets                                                |

The exact corresponding SDK functions include `SetLivoxLidarFovMode`, `SetLivoxLidarEchoMode`, `SetNTPServerIp`, `SetLivoxLidarITOCtrlMode` and `SetLidarFogNoiseFilterMode`; the pinned header marks these as **Avia 2** functions. Do not substitute generic `FovCfg` ROI setters or S/L IMU-range/time-filter settings. Changing Normal/Focus or filtering changes the data experiment; retain the original setting and verify the acknowledged result before recording a comparison. [Official parameter table](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/livox_eth_protocol_avia2.html#cmd-details), [actual SDK declarations and applicability](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/include/livox_lidar_api.h).

| Read-only key                                 | Value length / interpretation                                                                                                     |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `0x8000 sn`                                   | 16-byte NUL-padded serial                                                                                                         |
| `0x8002 version_app`, `0x8003 version_loader` | Four version octets each                                                                                                          |
| `0x8006 cur_work_state`                       | u8: Sampling 1, Idle 2, Error 4, Self-check 5, Startup 6, Ready 9; firmware upgrade remains a distinct manual-described operation |
| `0x8007 core_temp`                            | int32, 0.01 °C                                                                                                                    |
| `0x8010 FW_TYPE`                              | u8: 0 loader, 1 application                                                                                                       |
| HMS list                                      | 32 bytes, eight uint32 codes; web table prints **`0x0811`**, while the pinned SDK key enum uses **`0x8011`**                      |

The HMS-key spelling is a source discrepancy. Use the supported SDK query/observed reply and preserve its actual key; do not send a guessed alternate key simply because one source transposes its digits. The pinned SDK identifies Avia 2 as device type **40**, while Driver2's configuration-level `lidar_type:8` serves a different configuration role. They must not be substituted for each other. [Protocol status keys](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/livox_eth_protocol_avia2.html), [SDK model/key definitions](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/include/livox_lidar_def.h).

### Avia 2 fault interpretation and controlled recovery

HMS severity is carried separately from the abnormal ID in the full 32-bit code: preserve the full value, not only the ID. The following groups cover the publicly documented Avia 2 HMS catalog; they are diagnostic categories, not a substitute for matching the delivered firmware's report.

| Abnormal ID / level                      | Meaning and next check                                                                                                                         |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `0x0106`, warning                        | Fan-speed concern: inspect unobstructed fan/filter/airflow; do not apply a fan diagnosis to an NF model by assumption                          |
| `0x0210`, warning                        | Scan speed changing: wait for stabilization before comparing density/rate                                                                      |
| `0x0211–0x021B`, fatal                   | Scan-module fault: retain logs; if persistent, follow supported restart/service procedure                                                      |
| `0x0310–0x0312`, warning                 | Internal overtemperature: supply a valid cooling path and check ambient/airflow                                                                |
| `0x0313` warning / `0x0314` fatal        | Optical-power margin concern/abnormality: respect the manufacturer's optical operating limits and obtain support if persistent                 |
| `0x0315`, warning                        | Possible ranging-module abnormality: record conditions and use supported restart/support route                                                 |
| `0x0316` warning / `0x0317–0x0318` fatal | Excessively reflective test environment: remove the exposure source before a supported restart; repeated retries in the same scene risk damage |
| `0x0402`, warning                        | PTP stopped or time difference excessive: check the selected master and traffic                                                                |
| `0x0403`, warning                        | Unsupported PTP 1588v2.1: use the documented v2.0 source                                                                                       |
| `0x0404`, warning                        | PPS synchronization abnormal: inspect both electrical PPS and absolute-time path                                                               |
| `0x0407` / `0x0408` / `0x0409`, warning  | Missing GPS / missing PPS / invalid GPS information; distinguish the failing input                                                             |
| `0x040A`, warning                        | Multiple synchronization methods present: select one valid source/topology                                                                     |

For NTP, configure the actual server through the model-supported setting, allow UDP 123 on the intended network and confirm packet time type **5** and stable behavior; millisecond-class NTP is not equivalent to a hardware-timestamped PTP setup. For GPS, retain dates in the documented 2000–2037 interval and check the exact manual's PPS voltage/timing before wiring. PTP/gPTP mixed-master and v2.1 limitations still apply. [Avia 2 HMS catalog](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/hms_code_avia2.html), [official timing methods](https://livox-wiki-en.readthedocs.io/en/latest/tutorials/new_product/avia2/avia2.html).

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

## Getting started

### First result with Viewer2 <a href="#getting-started-acquire-a-live-cloud" id="getting-started-acquire-a-live-cloud"></a>

1. Secure the fan-equipped sensor on its thermal plate. Keep the beam away from another LiDAR and strong retroreflectors. Remove the shipping protection, check unobstructed optics/airflow and use the correct de-energized cable/supply assembly.
2. Set a dedicated host Ethernet adapter to **192.168.1.50/24**. Factory Avia2 is **192.168.1.4/24**, gateway `.1`; do not derive this address from the serial number. Connect directly for first use, with only one factory-addressed sensor present.
3. Enable the approved power. Open the platform-matched Viewer2 package, select the discovered device and record serial, firmware, actual IP, working status and mode.
4. Select Sampling if required, then Normal mode. Place a diffuse stationary target beyond the 5 m blind zone. Confirm an updating 80° × 80° region, record a short sequence and replay it.
5. With the same mounting, select Focus and repeat. Confirm the smaller forward region; do not interpret missing side objects as a network fault. Restore the intended mode and save the configuration record.

**Expected result:** the correct serial reaches Sampling, both mode captures replay, and the change in field is visible without moving the target. No range or timing accuracy has been certified by this procedure. [Manual connection/Viewer/modes](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf).

### Pinned ROS2 Humble acquisition

Use a clean Ubuntu 22.04/ROS2 Humble environment with a compiler and CMake installed. These commands install the reviewed SDK2 library and build Driver2; they have not been executed in this review.

```bash
mkdir -p ~/avia2_dev
cd ~/avia2_dev
git clone https://github.com/Livox-SDK/Livox-SDK2.git
cd Livox-SDK2
git checkout c0796f04c143143899c87a773d9f6b7136453c0b
mkdir -p build
cd build
cmake ..
make -j2
sudo make install
mkdir -p ~/avia2_ws/src
cd ~/avia2_ws/src
git clone https://github.com/Livox-SDK/livox_ros_driver2.git
cd livox_ros_driver2
git checkout 21445540f0d100dc86a7e6df312dd70bbdb4afdf
```

Edit the Avia2 configuration in the source before building. From that repository directory, this original patch verifies the expected model key and changes only host/sensor endpoints:

```python
import json
from pathlib import Path
p = Path("config/AVIA2_config.json")
c = json.loads(p.read_text())
assert "Avia2" in c and len(c["lidar_configs"]) == 1
for host in c["Avia2"]["host_net_info"]:
    host["host_ip"] = "192.168.1.50"
c["lidar_configs"][0]["ip"] = "192.168.1.4"
p.write_text(json.dumps(c, indent=2) + "\n")
print("Avia2 sensor", c["lidar_configs"][0]["ip"], "host 192.168.1.50")
```

Use the **observed** sensor IP if it was changed previously. The patch changes a local driver file, not the sensor's network settings. Then:

```bash
source /opt/ros/humble/setup.bash
./build.sh humble
cd ~/avia2_ws
source install/setup.bash
ros2 launch livox_ros_driver2 rviz_AVIA2_launch.py
```

Close Viewer2 before taking ownership with the driver. In a second sourced terminal:

```bash
source /opt/ros/humble/setup.bash
source ~/avia2_ws/install/setup.bash
ros2 topic list -t
ros2 topic hz /livox/lidar
ros2 topic hz /livox/imu
```

**Expected result:** the actual Avia2 launch publishes cloud and IMU topics, with a nonempty scene in RViz. The host publication rate is configurable and is not the 350 k points/s acquisition rate. Match `xfer_format` to PointCloud2 versus Livox CustomMsg before subscribing. If discovery works but the cloud is absent, inspect current Sampling state and the configured host destination before changing firmware. [Driver2 build/launch](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md).

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

### Troubleshooting <a href="#troubleshooting" id="troubleshooting"></a>

| Observation                            | Diagnosis and recovery                                                                                                                                       |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| No link/discovery                      | Correct matched M12 harness, power at sensor, host `.50/24`, actual sensor `.4` or recorded changed address, dedicated adapter and scoped firewall rules     |
| Boot loop or startup error             | Supply capability above 55 W, voltage drop/transients, thermal plate and airflow; do not hot-swap to probe                                                   |
| Device present, no points              | Idle/Ready versus Sampling, wrong client ownership or destination IP; inspect status and SDK2 Avia2 target                                                   |
| Near objects missing                   | 5 m blind zone; use an additional validated near-field sensor                                                                                                |
| Focus loses scene coverage             | Expected 15° × 15° region; verify alignment and restore Normal if broad coverage is required                                                                 |
| Shutdown/error after bright reflection | Eliminate direct retroreflector/other LiDAR exposure; manual identifies 0x03160002, 0x03170004, 0x03180004; correct exposure before a controlled power cycle |
| Good cloud, poor fusion                | Per-point time, actual time-source lock, IMU translation/axes, motion during non-repetitive accumulation and return-mode assumptions                         |
| Thermal instability                    | Inspect inlet/outlet filters, mounting conduction and clearances; high-temperature restart policy also applies                                               |

**Can I use a MID-360S cable?** Not based on its fitting alone: Avia2 pins 11/12 carry ground/power. Use an explicitly compatible Avia2 assembly.

**Does Class 1 allow photographing the beam?** The manufacturer specifically warns against photographing the operating LiDAR because of camera-sensor damage risk. Keep imaging sensors outside direct emission paths.

For cleaning, remove loose dust with air before gently cleaning the window; inspect and clean airflow filters during prolonged outdoor use. Store dry, protected and within −40 to +85 °C. Preserve logs/captures/configuration before recovery; use only exact AVIA 2 firmware and release notes if a support-directed update is needed. [Manual maintenance/troubleshooting](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf).

## Downloads and technical documents

### Technical documents and software <a href="#technical-documents-and-software" id="technical-documents-and-software"></a>

| Direct resource                                                                                                                                                                                                             | Use                                                                            |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [Avia2 manual v1.0, July 2026](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf)                                                                                | Pin faces/table, mounting, power, modes, coordinate offset and maintenance     |
| [Viewer2 Linux 2.6.0](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/Livox%20Viewer2%20Linux/Viewer2_2.6.0_Linux.zip)                                                                                 | Platform-matched GUI distribution                                              |
| [Viewer2 Windows 2.6.0](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/Livox%20Viewer2%20Windows/Viewer2_2.6.0_Win.zip)                                                                               | Windows GUI distribution                                                       |
| [Official download center](https://www.livoxtech.com/avia-2/downloads)                                                                                                                                                      | Exact fan-equipped CAD/FOV and breakout models; NF resources listed separately |
| [SDK2](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md) / [Driver2](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md) | Pinned acquisition source and exact model launch                               |

The original male/female connector drawings and electrical table were visually inspected. Retained native figures/attachments remain below; they should be interpreted using their own model/revision captions.

### Related development guides

* [Livox](./)

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed 24 November 2026: exact `Livox-AVIA2` fan option, official manual v1.0 (2026.07), current specs/download inventory and the actual Avia2 SDK2/Driver2 configuration and launches.

**Software installation/compilation, Viewer execution, live cloud/IMU capture, firmware update and electrical/thermal/range measurements: not run.** The local JSON patch is original and syntax checked; the first-result procedures are source-reviewed instructions, not reported hardware results.

* [Avia2 fan-equipped official User Manual](https://terra-1-g.djicdn.com/65c028cd298f4669a7f0e40e50ba1131/avia-2/UM/Livox_Avia_2_User_Manual_v1.0_en.pdf) — v1.0 2026.07,32 pages read.
* [Avia2 official specifications](https://www.livoxtech.com/avia-2/specs) — current 24 Nov 2026.
* [Avia2 official downloads inventory](https://www.livoxtech.com/avia-2/downloads) — current 24 Nov 2026.
* [Livox SDK2 build and supported models](https://github.com/Livox-SDK/Livox-SDK2/blob/c0796f04c143143899c87a773d9f6b7136453c0b/README.md) — commit c0796f04c143143899c87a773d9f6b7136453c0b.
* [Livox ROS Driver2 build and Avia2 launches](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/README.md) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [Avia2 exact network configuration](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/config/AVIA2_config.json) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [Avia2 ROS2 launch](https://github.com/Livox-SDK/livox_ros_driver2/blob/21445540f0d100dc86a7e6df312dd70bbdb4afdf/launch_ROS2/rviz_AVIA2_launch.py) — commit 21445540f0d100dc86a7e6df312dd70bbdb4afdf.
* [Exact Avia2 fan-equipped store option](https://openelab.io/products/livox-avia2-fiber-laser-lidar) — 23 Nov catalog plus public page read 24 Nov 2026.

### Additional established references

* [Product at OpenELAB](https://openelab.de/products/livox-avia2-lidar-luefter)
* [Avia 2 FAQ](https://www.livoxtech.com/avia-2/faq)

### Supporting resource links

* [Official Livox SDK2 repository; check explicit model support](https://github.com/Livox-SDK/Livox-SDK2)
* [Avia 2 application and operating notes](https://www.livoxtech.com/avia-2)
