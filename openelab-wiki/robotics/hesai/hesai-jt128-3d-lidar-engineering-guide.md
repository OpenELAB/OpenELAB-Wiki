---
description: >-
  Power and wire JT128, correct its 95° vertical-FOV interpretation, apply
  per-device calibration and firing times, and acquire cloud data with Hesai
  SDK2/ROS2.
---

# Hesai JT128 3D LiDAR Engineering Guide

{% hint style="info" %}
[**View Hesai JT128 128-Channel 3D LiDAR for Robotics & AMR on OpenELAB**](https://openelab.io/products/hesai-jt128-3d-lidar-avg?variant=45449425256646)

**Model / option:** Default Title · **SKU:** `HESAI-JT128`
{% endhint %}

## Product overview

### Hesai JT128 3D LiDAR Engineering Guide <a href="#hesai-jt128-3d-lidar-engineering-guide" id="hesai-jt128-3d-lidar-engineering-guide"></a>

**Hesai JT128 is a 128-channel mechanical 3D LiDAR with 360° azimuth and 95° projected vertical FOV, from −4.4° to +90.5°.** This guide covers `HESAI-JT128`, whose store package includes the sensor, power supply and cable. The older “189° vertical” promotional wording is not the model-specific manual's vertical specification. Use the serial-matched correction file and actual JT128-capable SDK. [Manual J01-en-260330](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf), [exact package](https://openelab.io/products/hesai-jt128-3d-lidar-avg).

The useful commissioning outcome is a calibrated, recorded point cloud with known return mode and clock status. A spinning head, valid ping or millions-of-points headline alone does not establish that outcome.

### Quick Summary <a href="#quick-summary" id="quick-summary"></a>

The supplied JT128 package contains the 128-channel sensor, power supply and cable. Commission at the documented 10 Hz baseline, preserve the delivered angle correction and JT128 firing-time tables, and record the return mode. The default dual-return configuration has a larger data rate than single-return operation; logging and network design must include that selected mode.

[Model-specific source](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

## Applications

JT128 suits compact mobile-robot perception, mapping and scene capture requiring forward and overhead coverage. Its vertical channels are **not uniformly distributed**. Mounting height and nearest useful ground intersection should be evaluated from the actual angle table, not a 95°/128 equally spaced model.

For a stationary first test, place a diffuse target at a measured distance and keep a vertical wall plus overhead structure in view. Compare single and dual returns in separately recorded runs. Dual mode provides alternative echoes and doubles return throughput; it does not double the mechanical frame rate. A moving platform needs actual firing-time correction and optical-center treatment before assessing wall thickness or SLAM quality. [Manual channel/return/timing sections](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### Run robot tests <a href="#run-robot-tests" id="run-robot-tests"></a>

After static capture/replay is coherent, check the measured sensor-to-base transform and collect a low-speed turn, ramp and return-to-start sequence under controlled robot operation. Compare timestamp domain/lock and packet continuity during motion. These are proposed commissioning checks; no physical robot or LiDAR test was executed for this guide.

[Model-specific source](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### Project References and Application Ideas <a href="#project-references-and-application-ideas" id="project-references-and-application-ideas"></a>

* [HesaiLidar SDK 2.0](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0): official SDK supporting JT128, online LiDAR parsing, PCAP parsing, point cloud visualization, PCD export, GPU acceleration, and packet-loss analysis.
* [HesaiLidar ROS 2.0](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0): official ROS/ROS2 driver supporting JT128; a practical starting point for RViz, mapping, navigation, and robot autonomy stacks.
* [Agtonomy autonomous farming reference](https://www.hesaitech.com/hesais-jt-series-3d-lidar-revolutionizes-the-future-of-autonomous-farming/): Hesai states that Agtonomy integrates JT128 LiDAR with autonomous farming robots for fleet monitoring and task automation.
* [Thoro.ai smart logistics reference](https://www.hesaitech.com/hesai-powers-safety-certified-ai-autonomy-for-smart-logistics-with-3d-lidar-at-modex-2026/): Hesai describes JT128 integration with Thoro.ai autonomy software for autonomous mobile robots.
* [Hesai JT Series launch reference](https://www.hesaitech.com/hesai-unveils-mini-hyper-hemispherical-3d-lidar-series-for-robotics-at-ces-hesai/): Hesai positions JT128 for robotics applications including autonomous agriculture and high-coverage robot perception.
* Application ideas: AGV/AMR navigation, pallet and rack perception, autonomous lawn and farm robots, robot docking, indoor/outdoor SLAM, smart logistics, 3D obstacle maps, and multi-sensor robot perception.

[Model-specific source](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

## Specifications

### Key Specifications <a href="#key-specifications" id="key-specifications"></a>

| Parameter                     | JT128, J01-en-260330                                                                      |
| ----------------------------- | ----------------------------------------------------------------------------------------- |
| Laser / protection            | 905 nm, Class 1; IP6K7                                                                    |
| Channels / FOV                | 128; 360° azimuth;95° projected vertical,−4.4° to +90.5°                                  |
| Instrumented /10% range       | 0–60 m /40 m at 10% reflectivity, all channels                                            |
| Typical accuracy / precision  | ±3 cm average error /2 cm standard deviation; conditions apply                            |
| Frame rate / azimuth sampling | 10 Hz: 0.4°;20 Hz: 0.8°                                                                   |
| Vertical resolution           | 0.74° average; not uniform per-channel spacing                                            |
| Return modes                  | Single first/strongest/last; dual last +strongest(default), last +first, first +strongest |
| Valid return rate             | 1,152,000/s single;2,304,000/s dual                                                       |
| Cloud data rate               | 41.15 Mbps single;82.30 Mbps dual                                                         |
| Interface                     | 100BASE-TX Ethernet/UDP; PTC control via TCP                                              |
| Rated sensor voltage          | 9–32 V DC at connector                                                                    |
| Typical consumption           | 9.5 W at 25 °C,10 Hz; excludes accessories                                                |
| Required supply capacity      | At least 2.6 A and 30 W; power-up/cable drop still matter                                 |
| Body / mass                   | H 73.05 mm, base Φ62.50 mm;<250 g                                                         |
| Temperature                   | −20 to +65 °C ambient operating;−40 to +85 °C storage                                     |
| Clock sources                 | GNSS/PTP: 1588v2, 802.1AS, 802.1AS Automotive                                             |

[Manual specifications/footnotes](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf). Instrumented 0 m is not a statement of guaranteed zero-distance measurement. Precision and accuracy vary with target, range and temperature. At 20 Hz sampling becomes 0.8°; it is not 10 Hz's angular sampling at twice the update rate.

### FOV Note: Product Page vs Manual <a href="#fov-note-product-page-vs-manual" id="fov-note-product-page-vs-manual"></a>

The product-family promotion says 360° × 189° hyper-hemispherical coverage, while the exact JT128 J01 specification defines a **95° projected vertical span, −4.4° to +90.5°**. These are different geometric descriptions. Use the model's projected angles, CAD and optical-origin definition for occlusion planning; a protective window or bracket cannot be approved from the promotional number alone.

[Model-specific source](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

## Hardware and connections

### Eight-pin M8 and splitter boundaries

JT128 uses a Signal Electronics M8 male socket. Align the key to the official **front view** in §2.2 and follow the connector-numbered cross-table in §2.3.1. Power off before mating/unmating; the documented coupling-nut torque is 0.4 N·m. Do not pull on cable conductors or force a damaged connector. The face drawing and cross-table were visually inspected.

| CNN1 sensor pin | Function          | Reference harness branch              |
| --------------- | ----------------- | ------------------------------------- |
| 6               | Power +,9–32 V    | CNN2 power pin 1                      |
| 1               | GND               | CNN2 pin 2 and GNSS reference         |
| 8               | GNSS PPS          | 3.3 V input, rising edge ≤500 ns      |
| 7               | GNSS NMEA         | RS232 input,−13 to +13 V; GPRMC/GNRMC |
| 4 /5            | Ethernet TX+ /TX− | RJ45 pins 1/2                         |
| 3 /2            | Ethernet RX+ /RX− | RJ45 pins 3/6                         |

[Official pin cross-table](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf). Harness colors change between branches; for example, sensor power is red but the power-branch positive is blue. Use contact numbers and assembly labels, not a generic red-wire rule. Leave optional GNSS branches insulated for first capture. PPS is 3.3 V while NMEA is RS232; they are not interchangeable logic interfaces.

GNSS PPS is 1 s±50 μs, rising-edge to rising-edge. Pulse width is ≥1 ms with 10–100 ms recommended. NMEA must start after the current PPS rising edge, end after its falling edge, and finish at least 100 ms before the next rising edge. Match actual receiver timing and supported message format before claiming lock. PTP needs no external PPS cable. [Manual GNSS/timesync](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### Supply, mechanics and power cycling <a href="#hardware-integration-notes" id="hardware-integration-notes"></a>

Use the matched supply with ≥30 W capacity. Keep 9–32 V **at the sensor**, including cable loss and overshoot. The manual's 26 AWG example estimates 3.55 V loss for 10 m at a 12 V source, which would violate the 9 V minimum. Longer cables require a deliberately engineered supply/cable arrangement; do not cure undervoltage by approaching 32 V without transient margin.

Before startup, the input must remain below 1 V for>50 ms; the ramp must reach 90% of target in<500 ms. After shutdown, keep below 1 V for ≥50 ms before another startup. Cold starts below 0 °C and 20 Hz operation draw more than the 9.5 W typical figure. [Manual Appendix C](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

Use the actual exterior/bottom drawings and properly grounded conductive bracket where practical; the manual alternatively recommends well-grounded shielded Ethernet for platforms lacking chassis grounding. Its generic torque table lists M2 through M6 and is **not** a statement that all those thread sizes exist on this body. Select actual mounting holes/engagement from the JT128 drawing. Keep optical window and rotation envelope clear, allow strain relief and ≥5 × cable OD bend radius. Cable OD is 5.50±0.20 mm. [Manual setup](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### Validate calibration <a href="#validate-calibration" id="validate-calibration"></a>

Select the angle correction delivered for this serial and the JT128-specific firing-time data; a public default CSV is a reference, not evidence of that unit's calibration. Use a measured planar target to examine shape and compare the same capture with optical-center correction explicitly recorded. On moving data, keep each block/channel's firing offset instead of using array index as firing order.

[Model-specific source](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

## Software and development resources

### Software Workflow <a href="#software-workflow" id="software-workflow"></a>

#### Exact protocol, calibration and timing <a href="#network-data-and-timing" id="network-data-and-timing"></a>

Current Hesai SDK2 and ROS2 source explicitly support JT128. The reviewed ROS driver commit pins its SDK submodule to **357ff14c0b4486d21ac0de0b218e34546276cacb**; use that recursive checkout for the workflow below. The actual UDP 1.4 parser contains JT128 optical-center and firing-time handling. An independently cloned SDK HEAD is a separate version. [ROS README](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0/blob/3d54078a3d770004ef30ec2cacc26673f4172b22/README.md), [SDK README](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0/blob/fbcd94a1efb7af0133f9512e14afdde85e5bc06b/README.md).

| Setting /stream          | JT128 baseline                                                       |
| ------------------------ | -------------------------------------------------------------------- |
| Factory sensor /mask     | 192.168.1.201 /255.255.255.0                                         |
| Cloud destination        | 255.255.255.255 broadcast; UDP 2368, source port 10000               |
| Fault destination /PTC   | UDP 2369 /TCP 9347                                                   |
| Normal cloud UDP payload | 1100 bytes; EE FF, protocol 1.4; flags affect fields                 |
| Distance units           | 4 mm, declared in header; multi-byte values little-endian            |
| Default clock            | PTP, 1588v2, UDP/IP, domain 0; verify Tracking/Locked/Frozen/FreeRun |
| Default mechanical state | 600 RPM(10 Hz), InOperation                                          |

[Manual data/parameter sections](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf). The pinned SDK tests confidence with header mask `0x10`, IMU with `0x02` and weight factor with `0x20`. The J01 manual table labels those bits differently; verify the delivered firmware/protocol against the SDK before custom parsing. The confidence flag changes the point layout; do not apply a fixed 4-byte point stride without reading it. Dual-return adjacent blocks share an azimuth. Full per-point time needs block and nonuniform channel firing offsets; channel index is not firing order. The 32-bit microsecond component alone is not absolute UTC.

Use the **delivered per-device angle correction file**. The public default angle CSV and repository example are useful references, not a replacement for serial-matched calibration. Retain the JT128-specific firetime table for moving-platform work. Optical-center correction is a separate SDK option; do not assume a generic radial-to XYZ conversion already performs it. [Manual Appendices A/B/D](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

PandarView 2 handles live cloud/capture/replay; LidarUtilities handles read status, configuration and upgrade. The complete PTCAPI and diagnostic/fault definitions are supplied through manufacturer support. First acquisition needs no handcrafted PTC writes or fault-byte interpretation.

### JT128 live, replay and calibration configuration contracts

The ROS driver's pinned `config.yaml` separates **source selection**, source-specific settings and common parser/publication options. Preserve the JT128 angle/firetime files alongside each recording; changing source type does not make an arbitrary calibration valid.

| Configuration key                                              | Input / result                                                                                                                                              |
| -------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `source_type`                                                  | 1 live UDP; 2 PCAP; 3 ROS packet bag; 4 serial. The serial block's JT16 example does not establish JT128 serial support                                     |
| `lidar_udp_type.device_ip_address`, `udp_port`, `ptc_port`     | Select the actual sensor, cloud destination port and PTC endpoint; baseline `.201`, 2368 and 9347                                                           |
| `use_ptc_connected`                                            | Enable the PTC connection; when unavailable, supply actual local calibration and observe startup errors rather than assume successful device retrieval      |
| `correction_file_path`, `firetimes_path`                       | Per-device geometry and JT128 firing-time corrections, set separately in the chosen live/PCAP/bag source block                                              |
| `recv_point_cloud_timeout`, `ptc_connect_timeout`              | Receive and connection timeout settings; shipped −1 values need deliberate treatment in an unattended application                                           |
| `standby_mode`, `speed`                                        | Shipped −1 leaves these controls unset; 0/1 standby mode means operation/standby. Do not introduce a speed or mode write merely to read cloud data          |
| `use_timestamp_type`                                           | 0 point-cloud device time; 1 receive time. Host receive time includes transport/scheduling delay                                                            |
| `pcap_play_synchronization`, `pcap_play_in_loop`, `play_rate_` | PCAP timing, repeat and playback multiplier; one finite comparison uses synchronized playback, loop false and rate 1.0                                      |
| `enable_packet_loss_tool`                                      | Enables the SDK counter diagnostic and `/lidar_packets_loss` publication configured by the ROS block; loss statistics do not validate optical accuracy      |
| `distance_correction_flag`, `transform_flag`                   | Optical-center correction and host coordinate transform are independent; the default false values must not be silently replaced by unrelated model settings |
| `device_udp_src_port`                                          | Optional source-port selection for a multi-sensor capture; 0 leaves the filter unset. Match actual capture evidence before restricting traffic              |
| `fov_start`, `fov_end`                                         | Default −1/−1 preserves decoder behavior; filtering is a host acceptance window, not a changed optical field                                                |
| `send_packet_ros`, `send_point_cloud_ros`, `send_imu_ros`      | Independent raw/cloud/IMU publications. An enabled IMU publisher does not prove that the delivered JT128 sends compatible IMU packets                       |

[Exact ROS configuration](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0/blob/3d54078a3d770004ef30ec2cacc26673f4172b22/config/config.yaml). The configuration file includes options for many Hesai devices; its Pandar128 frame-azimuth note and XT correction parameters are not JT128 capabilities.

A repeatable engineering comparison is: capture live UDP including the intended device stream; save serial/firmware, exact SDK submodule revision and calibration files; copy the configuration and select `source_type:2`; set its `pcap_type` file paths; then verify replay counters, cloud orientation and per-point time against the original capture. Use packet-bag input only with the matching packet message and source type 3. PTC request submission and an ACK must be evaluated separately; prefer the matching SDK API and its returned error over constructing undocumented TCP commands. The complete manufacturer PTC/diagnostic definitions remain a separately requested resource, as stated above.

### JT128 UDP 1.4 field reference

For **JT128 manual J01-en-260330**, multibyte measurement values are little-endian. The normal documented 1100-byte UDP payload is the profile below. Ethernet/IP/UDP headers and Ethernet FCS are **outside** these offsets. A flags-dependent packet from a different firmware can have a different channel stride and tail position; validate it against the matched SDK before using absolute offsets. [Manual §3, printed pp. 37–47](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

| Field                     | UDP offset / bytes in the documented profile | Type / interpretation                                                   |
| ------------------------- | -------------------------------------------- | ----------------------------------------------------------------------- |
| Pre-header                | 0 / 6                                        | `EE FF`, protocol major/minor 1/4, reserved\[2]                         |
| Channel and block counts  | 6 / 1; 7 / 1                                 | uint8: 128 channels, 2 blocks                                           |
| Reserved / distance unit  | 8 / 1; 9 / 1                                 | Unit byte 4 means 4 mm per range count                                  |
| Return count / flags      | 10 / 1; 11 / 1                               | One or two returns; inspect actual feature bits before selecting stride |
| Block 1 azimuth           | 12 / 2                                       | uint16, 0.01°                                                           |
| Block 1 channel records   | 14 / 512                                     | 128 × 4 bytes in this manual profile                                    |
| Block 2 azimuth / records | 526 / 2; 528 / 512                           | Same layout as block 1                                                  |
| Body CRC                  | 1040 / 4                                     | CRC-32/MPEG-2 over the Body; different from reflected Ethernet CRC32    |
| Reserved tail area        | 1044 / 11                                    | Leave uninterpreted in the manual profile                               |
| Working / return modes    | 1055 / 1; 1056 / 1                           | Working 0 operation, 1 standby; return codes below                      |
| Motor speed               | 1057 / 2                                     | uint16, 0.1 RPM; Hz = raw / 600                                         |
| UTC date/time             | 1059 / 6                                     | Year since 1900, month, day, hour, minute, second                       |
| UTC fractional time       | 1065 / 4                                     | uint32 microseconds, 0–999999                                           |
| Factory / UDP sequence    | 1069 / 1; 1070 / 4                           | `0x42`; uint32 sequence counter                                         |
| IMU                       | 1074 / 22                                    | Fields below                                                            |
| Tail CRC                  | 1096 / 4                                     | CRC-32/MPEG-2 over the Tail                                             |

Each four-byte channel record contains distance u16, reflectivity u8 and confidence u8. Range in metres is `distance × DisUnit / 1000`; do not hard-code 4 mm without checking the header. In this manual, reflectivity 0–255 is a linear percent-scale field, **not Livox's diffuse/retroreflective split**. The confidence byte uses bits 7–6 for cover contamination level 0–3 and bits 5–0 for discrete-noise likelihood 0–63, increasing with contamination/noise. The manual calls this field WeightFactor in PandarView 2. **The manual's confidence-present bit 5 disagrees with the inspected SDK's confidence mask `0x10`, while that SDK separately supports a weight-factor bit.** Keep these contracts versioned; do not append a byte twice or overwrite the original flag. [Manual Body/flags, pp. 40–43](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf), [SDK UDP 1.4 structures](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0/blob/fbcd94a1efb7af0133f9512e14afdde85e5bc06b/libhesai/UdpProtocol/udp_protocol_v1_4.h).

| Return code            | Meaning / adjacent blocks in dual mode                                                                |
| ---------------------- | ----------------------------------------------------------------------------------------------------- |
| `0x33`, `0x37`, `0x38` | First, strongest, last single return                                                                  |
| `0x39`                 | Last then strongest, default; if last is strongest, the second block instead carries second strongest |
| `0x3B`                 | Last then first; a sole return can be repeated in both blocks                                         |
| `0x3C`                 | First then strongest; if first is strongest, the second block instead carries second strongest        |

Dual blocks share an azimuth and firing event. They are not two independently timed revolutions. The generic SDK also defines other return codes for other devices; those declarations do not add JT128 return modes to this manual. [Manual pp. 41, 44](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

| IMU field               | Relative offset / bytes  | Conversion                                                                                                                                              |
| ----------------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Temperature             | 0 / 2, int16             | ×0.01 °C                                                                                                                                                |
| Acceleration factor     | 2 / 2, uint16            | ×0.001 mg; nominal value 122 gives 0.122 mg/count                                                                                                       |
| Angular-velocity factor | 4 / 2, uint16            | ×0.01 mdps; nominal 3049 gives 30.49 mdps/count                                                                                                         |
| Reserved                | 6 / 4                    | J01 marks reserved; the SDK names this field an IMU timestamp and scales it by 25. That additional timing contract needs delivered-version confirmation |
| Acceleration XYZ        | 10/12/14 / 2 each, int16 | Multiply by reported acceleration factor; convert mg to g by 0.001, then to m/s² by 9.80665                                                             |
| Angular velocity XYZ    | 16/18/20 / 2 each, int16 | Multiply by reported angular factor; mdps → °/s by 0.001, then rad/s by π/180                                                                           |

J01 lists acceleration ranges ±2/4/8/16 g, default ±4 g, and gyro ranges ±125/1000/2000 °/s, default ±1000 °/s. It references a PTC range-setting command, but the full supported request/response schema is not in this public manual. Use the matching manufacturer API rather than constructing a command from the command number alone. Changing range must not silently change an application's interpretation of already recorded samples. [Manual pp. 45–47](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### JT128 calibration, per-point time and optical center

A unit's angle CSV begins with `EEFF,1,1`, then `Channel,Elevation,Azimuth`, one row per channel 1–128, and a final SHA-256 checksum line. Angle values are degrees. Preserve the file byte-for-byte and its checksum; do not edit it to resemble a nominal evenly spaced 0.74° pattern. Obtain the serial-matched file from shipment, PandarView 2 export or the supported PTC `0x05` retrieval documented by Hesai. A command number alone is not a complete TCP API implementation. The manual's nominal per-channel angular/range table is useful for design, while the delivered correction file is the calibration source for decoding. [Appendix A, pp. 65–73](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

Construct packet reference time `t0` from UTC calendar seconds plus fractional microseconds. Reject invalid month/day/second fields and fractions ≥1000000; using only the four fractional bytes loses the date and second rollover. With time in µs, J01 defines:

* Single return: block 1 starts at `t0 − 111.111 − 1888`; block 2 at `t0 − 1888`.
* Dual return: both blocks start at `t0 − 1888`.
* Channel n fires at its block start plus the channel-specific offset below.

Clock source matters: initial GNSS/PTP unlock can use a virtual calendar; after loss, GNSS unlock or PTP Frozen drifts from the last synchronized time. PTP Tracking/Locked follows the master, and its UTC offset must be verified. For GNSS, PPS controls the second boundary and NMEA provides calendar information; PTP does not use the PPS wire. [Appendix B, pp. 74–78](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

For azimuth deskew, combine the block azimuth, per-channel horizontal correction and angle traversed during its firing offset. Convert RPM to degrees/s with ×6 before multiplying by seconds; retain the source-defined rotation sign. A fixed step per channel is wrong because channel number is not firing order.

The manual's optical-center correction adds the **rotating optical-center position** A to the measured point relative to that center: `x = Ax + r cos(elevation) sin(azimuth)`, `y = Ay + r cos(elevation) cos(azimuth)`, `z = Az + r sin(elevation)`. Angles must be radians in the computation. The inspected JT128 SDK uses a zero-position optical-center parameter `(−0.0076, 0.01367, 0.01274) m`; its actual parser handles the model's rotation/correction. This is separate from robot extrinsics and IMU-origin translation. Do not add a fixed zero-position XY offset to every point regardless of scanner angle. If deriving spherical output after correction, use quadrant-preserving `atan2(x,y)` and handle zero range; the manual's printed `arctan(x/y)` does not preserve all quadrants. [Manual §1.4 Figure 5 and Appendix D, pp. 15, 82–84](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf), [JT128 optical-center implementation](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0/blob/fbcd94a1efb7af0133f9512e14afdde85e5bc06b/libhesai/UdpParser/include/udp1_4_parser.h).

#### J01 channel firing offsets

Each cell is **channel: offset in µs**, measured from its block start. These factual values transcribe Appendix B.4; they are not measured results from this guide.

| Channels 1–8 of row |            |            |            |            |            |            |            |
| ------------------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| 1: 95.18            | 2: 23.24   | 3: 98.22   | 4: 20.2    | 5: 101.26  | 6: 17.16   | 7: 104.3   | 8: 14.12   |
| 9: 77.28            | 10: 92.14  | 11: 74.24  | 12: 89.1   | 13: 71.2   | 14: 86.06  | 15: 68.16  | 16: 83.02  |
| 17: 50.26           | 18: 11.08  | 19: 47.22  | 20: 8.04   | 21: 44.18  | 22: 5      | 23: 41.14  | 24: 1.96   |
| 25: 65.12           | 26: 105.82 | 27: 62.08  | 28: 102.78 | 29: 59.04  | 30: 99.74  | 31: 56     | 32: 96.7   |
| 33: 38.1            | 34: 24.76  | 35: 35.06  | 36: 21.72  | 37: 32.02  | 38: 18.68  | 39: 28.98  | 40: 15.64  |
| 41: 78.8            | 42: 93.66  | 43: 75.76  | 44: 90.62  | 45: 72.72  | 46: 87.58  | 47: 69.68  | 48: 84.54  |
| 49: 51.78           | 50: 12.6   | 51: 48.74  | 52: 9.56   | 53: 45.7   | 54: 6.52   | 55: 42.66  | 56: 3.48   |
| 57: 66.64           | 58: 103.54 | 59: 63.6   | 60: 100.5  | 61: 60.56  | 62: 97.46  | 63: 57.52  | 64: 94.42  |
| 65: 39.62           | 66: 22.48  | 67: 36.58  | 68: 19.44  | 69: 33.54  | 70: 16.4   | 71: 30.5   | 72: 13.36  |
| 73: 76.52           | 74: 91.38  | 75: 73.48  | 76: 88.34  | 77: 70.44  | 78: 85.3   | 79: 67.4   | 80: 82.26  |
| 81: 49.5            | 82: 10.32  | 83: 46.46  | 84: 7.28   | 85: 43.42  | 86: 4.24   | 87: 40.38  | 88: 1.2    |
| 89: 64.36           | 90: 105.06 | 91: 61.32  | 92: 102.02 | 93: 58.28  | 94: 98.98  | 95: 55.24  | 96: 95.94  |
| 97: 37.34           | 98: 24     | 99: 34.3   | 100: 20.96 | 101: 31.26 | 102: 17.92 | 103: 28.22 | 104: 14.88 |
| 105: 78.04          | 106: 92.9  | 107: 75    | 108: 89.86 | 109: 71.96 | 110: 86.82 | 111: 68.92 | 112: 83.78 |
| 113: 51.02          | 114: 11.84 | 115: 47.98 | 116: 8.8   | 117: 44.94 | 118: 5.76  | 119: 41.9  | 120: 2.72  |
| 121: 65.88          | 122: 62.84 | 123: 59.8  | 124: 56.76 | 125: 38.86 | 126: 35.82 | 127: 32.78 | 128: 29.74 |

Use this timing table only with the named J01 profile or a validated matching firetime file; a later firmware can require a different timing contract. [Original Appendix B.4](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### JT128 parameter, state and clock settings

This table explains **J01's documented settings**, not a list of commands to send during first acquisition. J01 p. 51 introduces API access but also says users cannot read/write that section's parameters. That wording does not establish which controls are enabled on a delivered firmware. Confirm the matching LidarUtilities/PTC package and permission/capability before a write; no proprietary TCP payload is inferred here. [Manual chapter 4, pp. 51–59](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

| Setting / status       | Documented options, units and behavior                                                                                                                              |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Source network         | Sensor UDP/PTC IPv4 `.201`, mask `255.255.255.0`, gateway `.1` on factory `192.168.1.x`; query observed settings before changing host addressing                    |
| Destination network    | Broadcast `255.255.255.255`, cloud UDP 2368, fault UDP 2369; fault packets are not point records                                                                    |
| Azimuth FOV            | One interval, default, or 1–5 intervals; endpoints resolved to 0.1°, start ≠ end                                                                                    |
| Wrapped FOV            | Start > end denotes \[start,360°) ∪ \[0°,end); for this case start cannot be 360° and end cannot be 0°                                                              |
| Returns                | First/strongest/last single; last+strongest default, last+first, first+strongest dual                                                                               |
| Spin rate              | 600 / 1200 RPM = 10 / 20 Hz; rate changes are not host replay pacing                                                                                                |
| Sync Angle             | \[0°,360°): scanner azimuth at each whole-second reference; multiple sensors need the same source and angle for phase lock                                          |
| Angle-based trigger    | Default; one firing every 0.4° at 10 Hz or 0.8° at 20 Hz                                                                                                            |
| Time-based trigger     | One firing every 111.111 µs; distinguish from angular triggering during speed variations                                                                            |
| Reset All Settings     | Resets chapter 4.2 functional settings; not a promise to restore every IP/network field                                                                             |
| Restart                | Restarts the unit and increments Start-Up Times                                                                                                                     |
| In Operation / Standby | Default operation; Standby stops motor and laser firing                                                                                                             |
| Clock source           | PTP default or GNSS; PTP does not require/use a separate PPS signal                                                                                                 |
| PTP profile            | IEEE 1588v2 default; 802.1AS; 802.1AS Automotive                                                                                                                    |
| PTP domain / transport | Domain 0–127, default 0; UDP/IP default or L2                                                                                                                       |
| PTP lock threshold     | Integer 1–1000 µs, default 100; threshold, not a measured accuracy guarantee                                                                                        |
| PTP Free Run           | No selected master; initial virtual time may be present                                                                                                             |
| PTP Tracking           | Following a master but absolute offset exceeds lock threshold                                                                                                       |
| PTP Locked             | Absolute offset within configured threshold                                                                                                                         |
| PTP Frozen             | Master lost; holdover time can drift, so not current external lock                                                                                                  |
| Identity               | SN, hardware PN/configuration and MAC; obtain per-unit angle correction with Get File where supported                                                               |
| Statistics             | Start-Up Times, System Uptime and Total Operation Time; save before diagnosing repeated resets                                                                      |
| Upgrade                | Exact firmware/software package and supported updater; save configuration/calibration/version first, then verify identity/version and static cloud after completion |

At a whole-second boundary, Sync Angle follows GNSS PPS when locked, the PTP master when Tracking/Locked, and an internal 1 Hz reference in PTP Frozen/Free Run. Thus two sensors can have equal configured angles without being externally synchronized. Preserve state and offset evidence with each recording. [Manual pp. 55–59 and Appendix B](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

For host integration, the ROS configuration's `host_ip_address` and `fault_message_port` are separate from `device_ip_address` and cloud `udp_port`. `device_fault_port` can restrict fault source traffic separately from `device_udp_src_port`. The generic `ptc_mode` selects TCP 0 or TCP-SSL 1; certificate/key/CA paths belong only to a firmware and SDK combination actually supporting that secure transport. `channel_fov_filter_path` and `multi_fov_filter_ranges` are host filters; they do not rewrite the LiDAR's configured emission field. Parser thread count, GPU selection and output frame grouping need host performance validation, not a generic hardware speed claim. [Pinned ROS configuration](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0/blob/3d54078a3d770004ef30ec2cacc26673f4172b22/config/config.yaml).

### Reproduce a calibrated JT128 capture offline

1. Save the original PCAP, serial/PN/firmware, exact driver and SDK submodule commits, angle CSV, firetime file and live configuration. Include fault traffic if the purpose is fault analysis; a cloud-only file cannot reconstruct an absent fault stream.
2. Copy the configuration. Set `source_type:2`, provide absolute `pcap_type.pcap_path`, `correction_file_path` and `firetimes_path`. Keep synchronized playback true, loop false and `play_rate_:1.0` for one finite comparison. Preserve the live timestamp policy: `use_timestamp_type:0` selects device time; 1 substitutes reception time.
3. Start the already built, version-matched driver through its documented launch, inspect actual cloud/IMU/packet-loss topics and compare the same static surfaces with the live dataset. Do not add `speed` or `standby_mode` writes to a replay configuration. Packet-bag input uses source 3 and matching raw packet messages, not arbitrary PointCloud2 messages.
4. Record optical-center correction, host transform, FOV/return filters and the calibration identifiers with the result. Apply robot extrinsics once. A point cloud can look plausible while carrying the wrong firing times or origin.

**Expected result:** finite playback produces a consistent cloud with the retained calibration and time contract, and any sequence gaps remain visible rather than being hidden by infinite looping. A packet-loss counter does not prove measurement accuracy. Driver compilation, replay and hardware operation are not run here. The complete manufacturer PTC and fault-message ICD remain unavailable in the reviewed public package; their byte-level command/diagnostic schemas are not invented. [ROS source selection/configuration](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0/blob/3d54078a3d770004ef30ec2cacc26673f4172b22/README.md).

## Getting started

### First result with the supplied assembly <a href="#visualize-first" id="visualize-first"></a>

1. Record hardware PN, serial, cable and supply. Remove the optical shipping cover, mount securely and connect the intact splitter with power off. Keep GNSS branches insulated.
2. Configure a dedicated host adapter to **192.168.1.100/24**. This is a valid host choice, distinct from factory `.201`; use actual observed network settings if the device was changed. Start without VLAN unless the received configuration requires one.
3. Enable the approved supply and observe Ethernet link. Use Wireshark ARP/UDP to confirm `.201` traffic and cloud 2368. Close competing clients.
4. Open a JT128-capable PandarView 2 build, load the unit's angle correction file, and inspect a measured stationary target. Record serial, firmware, return mode, RPM and PTP status using LidarUtilities/read-only device information.
5. Save a short capture, replay it with the same calibration and compare geometry. Change 10/20 Hz or return mode only in separately recorded experiments.

**Expected result:** a calibrated updating cloud with correct hemispherical orientation and a replayable recording. No PTP master on the bench can mean FreeRun; do not label that UTC-synchronized. [Manual setup/tools](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### Original read-only header and range check <a href="#monitor-packet-loss" id="monitor-packet-loss"></a>

Close viewer/driver first. This Python 3 example listens for 8 seconds on cloud 2368, sends nothing and prints the first declared range. It does not apply angle or optical correction, and is not a full SDK replacement.

```python
import collections
import socket
import time

shapes = collections.Counter()
accepted = 0
with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as sock:
    sock.bind(("0.0.0.0", 2368))
    sock.settimeout(0.2)
    end = time.monotonic() + 8
    while time.monotonic() < end:
        try:
            data, peer = sock.recvfrom(65535)
        except socket.timeout:
            continue
        shapes[(peer[0], len(data))] += 1
        if len(data) < 17 or data[:4] != bytes.fromhex("ee ff 01 04"):
            continue
        if data[6] != 128 or data[7] != 2:
            continue
        accepted += 1
        if accepted == 1:
            azimuth = int.from_bytes(data[12:14], "little") * 0.01
            raw_range = int.from_bytes(data[14:16], "little")
            print("source", peer, "channels", data[6], "returns", data[10])
            print("first block azimuth deg", azimuth,
                  "uncorrected first range m", raw_range * data[9] / 1000)
            print("SDK confidence flag set", bool(data[11] & 0x10))
print("packet shapes", dict(shapes), "recognized JT128-shape packets", accepted)
if not accepted:
    raise SystemExit("No matching packet; check actual model, port and protocol revision")
```

**Expected result:** sustained recognized packets from the observed sensor, typically 1100-byte payloads, and a range in meters using the packet's declared unit. This check does not validate CRC, interpret fault messages or prove useful range accuracy.

### ROS2 Humble publisher <a href="#integrate-sdk-or-ros" id="integrate-sdk-or-ros"></a>

Use Ubuntu 22.04/Humble, compiler, colcon, Boost/yaml-cpp and the dependencies resolved by the actual package. Create a new workspace:

```bash
mkdir -p ~/jt128_ws/src
cd ~/jt128_ws/src
git clone https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0.git
cd HesaiLidar_ROS_2.0
git checkout 3d54078a3d770004ef30ec2cacc26673f4172b22
git submodule update --init --recursive
source /opt/ros/humble/setup.bash
cd ~/jt128_ws
rosdep install --from-paths src --ignore-src -r -y
```

Before building, edit `src/HesaiLidar_ROS_2.0/config/config.yaml`:

* `source_type:1`,`use_gpu:false`,`device_ip_address:192.168.1.201`,`udp_port:2368`,`ptc_port:9347`.
* Keep `standby_mode:-1` and `speed:-1` so first startup does not request mode/RPM changes.
* Use per-device `correction_file_path` and the exact JT128 `firetimes_path`; if using PTC calibration retrieval, confirm that retrieval succeeds and corresponds to this serial. Do not leave"Your...path"example text in usable settings.
* Preserve `ros_frame_id:hesai_lidar` and cloud topic `/lidar_points`; choose `distance_correction_flag` deliberately for the actual optical center policy.

```bash
cd ~/jt128_ws
source /opt/ros/humble/setup.bash
colcon build --symlink-install
source install/local_setup.bash
ros2 launch hesai_ros_driver start.py
```

In another sourced terminal, use `ros2 topic hz /lidar_points` and `ros2 topic echo /lidar_points --once --field header`. **Expected result:** nonempty PointCloud2 publications and coherent geometry. A cloud without the correct calibration is not an accepted result. For offline PCAP, set `source_type:2`, the actual `pcap_path`, angle/fire time files and deliberate replay rate; preserve them with the capture. [ROS configuration/build](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0/blob/3d54078a3d770004ef30ec2cacc26673f4172b22/README.md).

### Bench network setup <a href="#bench-network-setup" id="bench-network-setup"></a>

With the sensor at factory address 192.168.1.201, choose a unique host on 192.168.1.0/24, avoiding .0/.255 and the existing sensor/gateway addresses. Inspect ARP and UDP 2368/2369 on that adapter; configure only the necessary local firewall rules. Do not disable the host firewall as a generic setup step. A successful ping establishes reachability, not a decoded/calibrated cloud.

[Model-specific source](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### Save known-good configuration <a href="#save-known-good-configuration" id="save-known-good-configuration"></a>

Save a static PCAP together with serial/firmware, return mode, frame rate, cloud destination, correction-file identity, firetime file and PTP/GNSS status. Keep PandarView and the ROS receiver separate so only the intended acquisition path owns the port. Replay that same capture before changing a decoder or point filter.

[Model-specific source](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### Engineering Setup Checklist <a href="#engineering-setup-checklist" id="engineering-setup-checklist"></a>

* Download the JT128 user manual, 3D model, angle correction file, PandarView 2, LidarUtilities, SDK 2.0, and ROS 2.0 driver.
* Design the mechanical mount around the 62.50 mm bottom diameter, 73.05 mm height, connector routing, exposed optical window, grounding, and thermal constraints.
* Provide DC 9 to 32 V power with at least 30 W capacity at the LiDAR connector.
* Use dedicated or well-managed 100Base-TX Ethernet for the 41.15 to 82.30 Mbps point cloud stream.
* Set host IP to the correct 192.168.1.x address and verify UDP reception on 2368 and fault messages on 2369.
* Load or reference the correct JT128 angle correction file before evaluating geometry.
* Confirm return mode and frame rate in both device configuration and driver configuration.
* Verify timestamps with GNSS or PTP before multi-sensor fusion.
* Run packet-loss, vibration, thermal, and weather/environment tests before production deployment.

[Model-specific source](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

## Troubleshooting and FAQs

### FAQ <a href="#faq" id="faq"></a>

| Symptom                    | Diagnosis/recovery                                                                             |
| -------------------------- | ---------------------------------------------------------------------------------------------- |
| No motor                   | Supply/cable voltage, connector, InOperation versus Standby;≥30 W capacity                     |
| Motor but no UDP           | Actual destination, VLAN, host adapter, link and correct firmware; capture before filtering    |
| Packets but no PandarView  | Cloud 2368 versus fault 2369, supported viewer, scoped firewall access and calibration         |
| Distorted/misaligned cloud | Serial-matched angle file, JT128 parser, optical center, nonuniform firing time, return mode   |
| Loss in dual mode          | 82.30 Mbps stream on 100BASE-TX, host CPU/NIC/capture load; direct link before complex network |
| No PTP lock                | Actual profile, domain, transport/master; Frozen means holdover/drift, not current lock        |
| Repeated cold boots        | Atleast 30 W, startup waveform, cable loss and minimum off time                                |

**Is 189° the vertical FOV?** The current model manual specifies 95° projected vertical FOV; do not double its hemispherical description.

**May I clean it with alcohol as with another brand?** No. The JT128 polycarbonate cover instructions prohibit organic cleaners, including alcohol. Power off, use water/mild soap or approved solvent-free pH-neutral cleaner, soften stubborn contamination and rinse. Do not dry-wipe, abrade, wax or scrape ice. [Manual maintenance](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

Read current PN/firmware/status and save captures before factory resets or updates. ResetAllSettings has a specific documented scope; do not assume it restores every address. Obtain exact firmware/PTC/diagnostic instructions from Hesai. Do not send guessed control payloads.

### Best Practices and Limitations <a href="#best-practices-and-limitations" id="best-practices-and-limitations"></a>

* **Do not treat JT128 as a complete safety system by itself.** It can support navigation and obstacle perception, but safety-rated functions require system-level safety analysis, redundancy, and certified hardware where required.
* **Account for network throughput.** Dual-return operation can reach 82.30 Mbps of point cloud data before ROS overhead, logging, or visualization load.
* **Validate near-field blind spots and robot body occlusions.** The compact hemispherical design is strong for embedded robotics, but every enclosure and bracket changes usable coverage.
* **Use the angle correction file.** Incorrect or missing correction data can make mapping, localization, and obstacle geometry appear wrong.
* **Test material edge cases.** Glass, dark rubber, polished metal, rain, fog, dust, and low-angle sunlight can affect point cloud quality.
* **Plan for serviceability.** Keep the lens accessible for cleaning and the network/power connectors accessible for diagnostics.

[Model-specific source](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

### Cable loss, storage and cleaning checks

J01's cable-loss example for **26 AWG at 10 Hz and 23±5 °C** is useful for separating source voltage from sensor-terminal voltage:

| Cable length | Drop at 12 V source | Drop at 24 V source | Drop at 32 V source |
| ------------ | ------------------- | ------------------- | ------------------- |
| 2 m          | 0.52 V              | 0.25 V              | 0.19 V              |
| 5 m          | 1.42 V              | 0.64 V              | 0.48 V              |
| 10 m         | 3.55 V              | 1.32 V              | 0.97 V              |

For example, the listed 10 m/12 V case gives about **8.45 V at the sensor**, below its 9 V minimum; a power adapter labeled 12 V is therefore insufficient evidence of compliant operation. The manual's recommendation for longer runs is a higher source voltage with terminal measurements, while staying below 32 V including overshoot. Cold startup below 0 °C can remain around 15 W temporarily, and 20 Hz consumes more than the typical condition; the manual recommends at least 30 W supply capability for these cases. Preserve the stated power-up/down timing: below 1 V for more than 50 ms before ramp-up, rise to 90% of design voltage within 500 ms, and at least 50 ms below 1 V before repowering. [Appendix C, pp. 79–81](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

Recommended storage is dry/ventilated, **23±5 °C and 30–70% RH**, distinct from absolute storage-temperature limits. Keep the polycarbonate cover free from protective film/wax. After prolonged hot sun exposure, let it cool before cleaning; do not use an ice scraper or pressure washer for frozen contamination. Power off, soften contamination with room-temperature water or mild soap/approved solvent-free pH-neutral cleaner, use a soft damp sponge or microfiber cloth, rinse and remove residual liquid. Do not dry-wipe or use alcohol/organic cleaners. The manufacturer's mild-soap reference is no more than two tablespoons per quart or litre; cleaning-agent compatibility matters more than borrowing another brand's optics recipe. [Manual maintenance, pp. 60–61 and storage notice p. 4](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf).

## Downloads and technical documents

### Official Downloads and Resources <a href="#official-downloads-and-resources" id="official-downloads-and-resources"></a>

| Direct resource                                                                                                                                                                                                                                   | Purpose                                                                                           |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| [JT128 manual J01-en-260330](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf)                                                                                                                            | 90-page public manual; connector cross-table, power appendix, protocol, timing and optical center |
| [JT128 3D model](https://www.hesaitech.com/wp-content/uploads/2025/09/JT128-3D-Model.zip)                                                                                                                                                         | Mechanical integration                                                                            |
| [Public default angle CSV](https://www.hesaitech.com/wp-content/uploads/2026/05/JT128_default_angle.csv)                                                                                                                                          | Reference table; unit-specific file takes precedence                                              |
| [JT128 download section](https://www.hesaitech.com/downloads/#jt128)                                                                                                                                                                              | PandarView 2, LidarUtilities Windows/Ubuntu 20/22, manuals and current resources                  |
| [SDK2](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0/blob/fbcd94a1efb7af0133f9512e14afdde85e5bc06b/README.md)/[ROS driver](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0/blob/3d54078a3d770004ef30ec2cacc26673f4172b22/README.md) | Actual JT128 support, live/replay, coordinate/PCD and timing interfaces                           |

The manufacturer M8 face and CNN1-to-splitter cross-table were visually inspected. Native figures/files are retained below; manufacturer attribution and rights remain with the original resources.

## References and validation

### Source Notes <a href="#source-notes" id="source-notes"></a>

Reviewed 24 November 2026: full JT128 manual J01-en-260330, actual SDK2/ROS driver JT128 support and pinned submodule protocol source, exact store package and current manufacturer resource links. Channel calibration, firing time and optical-center requirements are separate from basic packet recognition.

**SDK/ROS build, GUI/live packet/script execution, firmware update, power/range/timing and physical tests: not run.** The header check is original and syntax checked.

* [Hesai JT128 User Manual](https://www.hesaitech.com/wp-content/uploads/2026/04/JT128_User_Manual_J01-en-260330.pdf) — J01-en-260330; 90 pages; C 0 public.
* [Hesai ROS driver supported JT128 and build](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0/blob/3d54078a3d770004ef30ec2cacc26673f4172b22/README.md) — commit 3d54078a3d770004ef30ec2cacc26673f4172b22.
* [Hesai SDK2 model/compiler/application documentation](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0/blob/fbcd94a1efb7af0133f9512e14afdde85e5bc06b/README.md) — commit fbcd94a1efb7af0133f9512e14afdde85e5bc06b.
* [Actual Hesai ROS live/replay configuration](https://github.com/HesaiTechnology/HesaiLidar_ROS_2.0/blob/3d54078a3d770004ef30ec2cacc26673f4172b22/config/config.yaml) — commit 3d54078a3d770004ef30ec2cacc26673f4172b22.
* [ROS-pinned JT128 UDP 1.4 decoder](https://github.com/HesaiTechnology/HesaiLidar_SDK_2.0/blob/357ff14c0b4486d21ac0de0b218e34546276cacb/libhesai/UdpParser/include/udp1_4_parser.h) — 357ff14c0b4486d21ac0de0b218e34546276cacb.
* [Exact JT128 sensor/power/cable selection](https://openelab.io/products/hesai-jt128-3d-lidar-avg) — 23 Nov catalog plus observed public page 24 Nov.

### Additional established references

* [Hesai JT128 official page](https://www.hesaitech.com/product/jt128/)
* [PandarView Windows V 2.1.7](https://www.hesaitech.com/wp-content/uploads/2025/01/PandarView_Release_Win64_V2.1.7.zip)
* [PandarView Ubuntu V 2.1.7](https://www.hesaitech.com/wp-content/uploads/2025/01/PandarView2_Release_Ubuntu_V2.1.7.zip)
* [PandarView 2 User Manual PDF](https://www.hesaitech.com/wp-content/uploads/2025/08/PandarView2_User_Manual_PV2-en-250810.pdf)
* [Windows package](https://www.hesaitech.com/wp-content/uploads/2025/09/LidarUtilities_Sample_JT128_3.0.5_65677db_windows7.zip)
* [Ubuntu 20 package](https://www.hesaitech.com/wp-content/uploads/2025/09/LidarUtilities_Sample_JT128_3.0.5_65677db_ubuntu20.zip)
* [Ubuntu 22 package](https://www.hesaitech.com/wp-content/uploads/2025/09/LidarUtilities_Sample_JT128_3.0.5_65677db_ubuntu22.zip)
* [Agtonomy autonomous farming reference](https://www.hesaitech.com/hesais-jt-series-3d-lidar-revolutionizes-the-future-of-autonomous-farming/)
* [Thoro.ai smart logistics reference](https://www.hesaitech.com/hesai-powers-safety-certified-ai-autonomy-for-smart-logistics-with-3d-lidar-at-modex-2026/)
* [Hesai JT Series launch reference](https://www.hesaitech.com/hesai-unveils-mini-hyper-hemispherical-3d-lidar-series-for-robotics-at-ces-hesai/)
* [Hesai JT128 product page](https://www.hesaitech.com/product/jt128/)
