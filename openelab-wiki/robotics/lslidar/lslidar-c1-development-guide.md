---
description: >-
  Connect LSLiDAR C1 with its correct V 4 Ethernet protocol, power and cable
  boundaries, and publish a one-ring cloud or populated Laser Scan using the
  exact ROS2 driver.
---

# LSLiDAR C1 Mechanical LiDAR Engineering Guide

{% hint style="info" %}
[**View LSLiDAR C1 Single-Line 360-Degree Mechanical LiDAR for Navigation and Obstacle Avoidance on OpenELAB**](https://openelab.io/products/lslidar-c1-mechanical-lidar-sensor?variant=46078296850630)

**Model / option:** Default Title · **SKU:** `LSLiDAR-C1`
{% endhint %}

## Product overview

### Product and scope <a href="#product-and-scope" id="product-and-scope"></a>

**LSLiDAR C1 is a single-line, 360° mechanical Ethernet LiDAR for planar ranging.** The assigned `LSLiDAR-C1` listing contains one sensor; obtain the matched cable and supply required by the actual hardware. It is not SLAMTEC RPLIDAR C1, C1Plus, or a multilayer C16 scanner. The official model sheet specifies 120 m at 70% reflectivity and 100 m at 10%, with separate ±3 cm accuracy and ±1 cm repeatability figures. [Official sheet](https://www.lslidar.com/wp-content/uploads/2024/09/C1.pdf), [exact listing](https://openelab.io/products/lslidar-c1-mechanical-lidar-sensor).

A manufacturer-authored C1 manual v4.0.6 (May 2023), available through a public distributor mirror, provides detailed wiring and protocol information. It has older 150 m and voltage wording that differs from the current sheet; this guide retains those revision boundaries and uses a conservative 12 V commissioning path. [C1 manual](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

## Applications

Use C1 for 2D localization, route mapping and planar obstacle-awareness development. One scan plane cannot establish obstacle height, overhead clearance or a complete ground surface. Choose mounting height/pitch from the obstacles of interest and verify the beam remains clear of the chassis and cable loop.

At a fixed 20,000 single-return points/s, raising the rotation rate reduces azimuth samples per revolution. At 5/10/20 Hz, the documented sampling is 0.09°/0.18°/0.36°. Evaluate update latency and smallest relevant target together. Dual return reports additional echoes; it does not create another vertical layer. [Current product specifications](https://www.lslidar.com/product/c1-single-line-mechanical-lidar/).

## Specifications

### Hardware and technical documents <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

| Parameter                   | Current C1 model sheet                                              |
| --------------------------- | ------------------------------------------------------------------- |
| Principle / channel         | ToF, one channel                                                    |
| Laser / safety              | 905 nm, Class I                                                     |
| Range                       | 120 m at 70%; 100 m at 10% reflectivity                             |
| Range accuracy / precision  | ±3 cm / ±1 cm (1σ); different quantities                            |
| Horizontal / vertical field | 360° / one plane, no multilayer vertical FOV                        |
| Rotation and sampling       | 5 Hz /0.09°; 10 Hz /0.18°; 20 Hz /0.36°                             |
| Point output                | 20,000 points/s single echo; 40,000 points/s dual echo              |
| Link / timing               | 100BASE-TX Ethernet, PPS; manual also documents GNSS/PTP/gPTP modes |
| Supply / typical power      | 9–32 V DC; 7 W at 10 Hz                                             |
| Body / mass                 | Φ102 × H 77.9 mm; about 1050 g                                      |
| Operating / storage         | −20 to +60 °C operating; legacy manual −40 to +85 °C storage        |
| Protection                  | IP67 sensor, with properly assembled connections                    |

[Official one-page sheet](https://www.lslidar.com/wp-content/uploads/2024/09/C1.pdf), [manufacturer-authored manual](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf). The current product page's introductory “±1 cm accuracy” wording is clarified by the sheet: ±1 cm is precision, while accuracy is ±3 cm. The v4.0.6 manual lists 150 m at 70% and some 36 V maximum wording; neither increases the current listing's 120 m or continuous 32 V limits. Use the serial-matched documentation for acceptance testing.

## Hardware and connections

### Sensor connector and harness revisions

The v4.0.6 manual identifies the eight-pin male sensor connector as **L1 02-M12-Z 08 A 118**. Its keyed face drawing and pin table were visually inspected. Do not substitute a similarly shaped eight-pin or another vendor's M12 cable.

| Sensor pin | Function in the manual                                           |
| ---------- | ---------------------------------------------------------------- |
| 1          | VIN; use the current 9–32 V operating boundary                   |
| 2 /3       | Ethernet TD+ /TD−, sensor to host                                |
| 4 /5       | Ethernet RD+ /RD−, host to sensor                                |
| 6          | GPS PPS / external synchronization pulse                         |
| 7          | GPS receive, 9600 baud; manual describes TTL/RS232 compatibility |
| 8          | GND                                                              |

[Manual electrical interface](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf). The adapter-cable and extension-cable tables have differing pair labels/colors. Treat each assembly as its own cross-table; do not combine the sensor-face table with a different cable's color sequence. Use an intact matched harness for first use and obtain the delivered revision drawing before making one.

The optional interface box has another six-pin JST GPS connector: pin 1 PPS input, pin 2 5 V GPS supply output, pins 3/5 ground, pin 4 GPS receive, pin 6 NC. Its PPS input is documented as 3.3–12 V TTL, while the sensor-side table has different electrical wording. Do not transfer the box limit to an unidentified bare terminal. Leave synchronization disconnected for initial acquisition; do not hot-plug either aviation or GPS connections. [Manual connector/box sections](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

### Power and mechanical installation

The detailed manual requires at least **25 W supply capacity**, despite 7 W typical running consumption. Use a matched regulated 12 V bench supply/adapter with startup allowance; verify voltage at the sensor and account for cable loss. The manual specifies ripple below 100 mV peak-to-peak and output accuracy better than 5%. Cold startup and 20 Hz operation can demand more power. Do not use 36 V as a continuous operating target or hot-plug the connector.

Use the exact base drawing for screw sizes and engagement. Provide a rigid conductive bracket and unobstructed optical envelope. The older manual calls for additional heat sinking above 38 °C ambient or prolonged sun exposure; plan thermal performance before enclosure design. The beam's finite divergence also matters: the manual gives 8.7 mrad vertical and 5.7 mrad horizontal, corresponding to approximately 87 × 57 mm footprint at 10 m before other effects. Fine azimuth sample spacing alone does not establish minimum detectable object size. [Manual mounting/light spot/power appendix](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

## Software and development resources

### Exact C1 V4 driver and packet identity <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The official `Lslidar_ROS2_driver` **C1\_V4.0** branch documents Ubuntu 22.04/ROS2 Humble among tested environments. Its generic CX driver supports multiple scanners; actual source identifies C1 from **MSOP byte 1211 =0x01**. C1Plus uses 0x03 and is a different model. The C1 path sets one output ring, so a multilayer default `scan_num:8` or 15 is inappropriate when requesting LaserScan. [Driver README](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/README_en.md), [actual implementation](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/lslidar_driver/src/lslidar_driver.cpp).

| Item                        | C1 V4 baseline                                                          |
| --------------------------- | ----------------------------------------------------------------------- |
| Sensor / factory target     | 192.168.1.200 /192.168.1.102                                            |
| MSOP / DIFOP host ports     | 2368 /2369                                                              |
| Cloud payload / model bytes | 1212 bytes; echo flag 1210, model 1211                                  |
| Echo flags                  | 0x37 strongest; 0x38 last; 0x39 dual                                    |
| DIFOP payload               | 1206 bytes; configuration/status, not cloud                             |
| Driver default cloud        | `lslidar_point_cloud`, frame `laser_link`, under launch namespace `/cx` |
| Optional scan               | `publish_scan:true`, **`scan_num:0` for C1's remapped ring**            |

[Manual protocol/network chapters](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf), [actual parameters](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/lslidar_driver/params/lslidar_cx.yaml). Confirm resolved topic names with ROS introspection rather than assuming an absolute name from a relative YAML value.

The cloud packet retains a legacy multi-slot structure: only one position in each eight-channel group carries the physical C1 measurement. It contains 12 blocks and uses 0.004 m range units. Do not turn the packet's slot count into a claim of 384 independent vertical beams. Per-point azimuth interpolation differs in single/dual mode; timestamps identify packet-end timing, so motion processing needs the documented offsets. GPS, PTP and gPTP configuration/lock are distinct from selecting host versus sensor time in a driver.

### C1 decoding parameters, replay and control-service boundaries

The C1 V4 YAML is a generic CX configuration and needs deliberate adaptation to a single-beam sensor. Keep the YAML namespace aligned with the launched `/cx/lslidar_driver_node`; an otherwise correct parameter under the wrong node name can be ignored.

| Parameter                                | Meaning and C1 consequence                                                                                                          |
| ---------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| `pcl_type:false`                         | Rich XYZIRT output; true selects XYZI and loses ring/time fields                                                                    |
| `use_time_service`                       | Use externally serviced sensor time when enabled; this host choice does not configure or lock GPS/PTP/NTP itself                    |
| `min_range`, `max_range`                 | Software m filters; generic 0.15/200 values do not extend the current C1's qualified 120 m rating                                   |
| `angle_disable_min`, `angle_disable_max` | Integer crop limits in **0.01°**, not degrees; default equal zeros leaves the nominal sector unmasked                               |
| `distance_unit:0.4`                      | CX driver's centimeter scale, equivalent to 0.004 m per range count; do not replace with 0.004 as though the YAML field were meters |
| `horizontal_angle_resolution`            | Example 0.18° at 10 Hz, 0.36° at 20 Hz and 0.09° at 5 Hz; match actual model/firmware scan settings                                 |
| `pcap`, `packet_rate`                    | Offline capture path and replay packet rate. Generic 1695 packets/s is not a measured C1 packet rate                                |
| `add_multicast`, `group_ip`              | Join the actual configured group when supported; a group address in YAML does not change a unicast sensor                           |
| `coordinate_opt`                         | Changes the zero-angle coordinate convention; verify a known target before publishing a robot transform                             |
| `publish_scan`, `scan_num`               | Enable LaserScan and select C1's remapped ring **0**, rather than the multibeam example 8/15                                        |

[Exact YAML](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/lslidar_driver/params/lslidar_cx.yaml), [driver parameter/readme reference](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/README_en.md). For a finite regression capture, close the live consumer, supply the PCAP path, preserve C1 identity/echo mode and matching DIFOP, then compare scene orientation and scan timing. A replay pacing setting must not be reported as the physical scan frequency.

The generic driver exposes time-service, laser, motor, speed and network-setting services. First inspect actual names/types with `ros2 service list -t` and inspect a type with `ros2 interface show`; do not execute the README's `/xx/` placeholders verbatim. `TimeService` takes `time_service_mode` (`gps`, `ptp`, or `ntp`) plus `ntp_ip` for the supported NTP path. `LslidarControl.laser_control` 0/1 disables/enables measurement **while the motor can continue rotating and equipment packets remain**. `MotorControl.motor_control` 0/1 is the separate stop/rotate control. A ROS service's presence does not establish every timing mode on every CX model.

`DataPort.data_port` and `DevPort.dev_port` accept the documented **1025–65535** port range; `DataIp.data_ip` and `DestinationIp.destination_ip` are distinct source/destination settings. Network writes can sever the current connection. Record old values first, use model-matched support, then update the local YAML and restart the driver as the README requires. Treat service acknowledgement and observed resumed measurement as separate checkpoints; none of these writes is needed for the first read-only network diagnosis.

### C1 V4 measurement fields, angles and time

The **manufacturer-authored C1 V4.0.6 manual (May 2023)** is preserved at its existing distributor-hosted PDF URL. It is an older electrical/protocol revision, not a new specification for every current C1. The exact C1\_V4.0 driver provides the additional implementation checks below. MSOP numeric data are **little-endian**; DIFOP/UCWP numeric configuration fields are **big-endian**. Offsets here exclude Ethernet/IP/UDP headers. [Manual chapters 5–8](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

| MSOP area            | Offset / length               | Meaning                                                                          |
| -------------------- | ----------------------------- | -------------------------------------------------------------------------------- |
| Blocks 0–11          | `100 × block`, 100 bytes each | Marker\[2], azimuth u16, 32 × three-byte slots                                   |
| Block marker         | Relative 0 / 2                | Wire bytes `FF EE`                                                               |
| Block azimuth        | Relative 2 / 2                | uint16, 0.01°; reference angle for interpolating slot positions                  |
| Slot n               | Relative `4 + 3n` / 3, n=0–31 | Distance u16 ×0.004 m; intensity u8, 0–255                                       |
| UTC/calendar area    | 1200 / 6                      | GPS-format year since 2000, month/day/hour/minute/second; PTP mode differs below |
| Fractional timestamp | 1206 / 4                      | uint32 ns in the older manual; mode-specific driver decoding below               |
| Echo / model         | 1210 / 1; 1211 / 1            | `0x37` strongest, `0x38` last, `0x39` dual; C1 model `0x01`                      |

Each block contains four legacy eight-slot groups; the old manual identifies **slot 6 of each group** as C1's physical measurement, with the other seven positions zero. Thus the nominal 384 slots in a packet are not 384 independent beams. Use actual nonzero/invalid-return rules and the exact decoder; output ring is 0 for this single physical line. Retain intensity as an instrument field, not a calibrated material reflectance percentage. [Manual pp. 22–26](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

For single echo, unwrap the next block's azimuth and compute the count-domain step `delta = (next − current) mod 36000`. Slot n has angle `(current + delta × n/32) mod 36000`; the physical slots in a block are n=6,14,22,30 in that manual layout. In dual mode, adjacent blocks share their reference azimuth; interpolate using the next **pair's** angle, not the repeated adjacent value. The final block/pair needs a valid adjacent increment from the neighboring packet or the model decoder's documented previous-increment fallback. Treat an implausibly large step as a loss/revision diagnostic rather than interpolating a full revolution across it. [Manual §7.2](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf), [actual interpolation implementation](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/lslidar_driver/src/lslidar_driver.cpp).

C1's physical elevation is 0°. In the manual's y-forward zero-angle convention, `x=r sin(theta), y=r cos(theta), z=0`; the alternative x-forward convention uses `x=r cos(theta), y=−r sin(theta)`. Convert degrees to radians before trigonometry. The actual driver also has its model optical-center/radius correction and `coordinate_opt`; a simple polar expression does not replace that implementation. The manual splits frames at a >180° angle wrap, whereas the pinned driver uses its own near-full-turn crossing threshold. Retain points that cross the boundary within a packet; do not assign a whole packet to one revolution without checking its angles. [Manual §7.3–7.4 and pinned driver](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/lslidar_driver/src/lslidar_driver.cpp).

The manual defines the fractional packet timestamp at the **end of the packed measurement interval**. Its single-return packet spans about 2.4 ms (four groups × 50 µs × 12 blocks), about 416.7 packets/s; dual mode doubles packet rate. For consecutive intact packets with end times Tprevious and Tend, its slot interpolation is `dt=(Tend−Tprevious)/384`, `Tslot(N)=Tend−dt×(384−N)` for one-based N. For paired dual data it uses 192 firing positions, with both returns sharing a position time. A lost packet or clock jump breaks the “consecutive intact” assumption: do not smear the longer interval over one received packet. [Manual chapter 8](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

The **pinned FPGA4 driver** interprets external time according to DIFOP byte 45, rather than treating bytes 1200–1205 as a calendar in every mode:

| Time mode          | Actual driver interpretation                                                                                                                                                                       |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 0 GPS              | Six-byte calendar, year 2000 + byte; little-endian fraction in ns                                                                                                                                  |
| 1 PTP              | Big-endian seconds from bytes 1201–1205, then little-endian ns at 1206–1209; the current implementation stores the seconds result in uint32, so do not advertise unrestricted 40-bit epoch support |
| 2 NTP              | Six-byte calendar; fractional count multiplied by 1000 to ns, i.e. source count in µs                                                                                                              |
| Host time selected | Host reception-time path; this is a timestamp substitution, not proof of sensor synchronization                                                                                                    |

This driver-level mode interpretation differs from the older manual's generic calendar/ns description. Match firmware, received DIFOP and parser before custom decoding. Enabling `use_time_service` does not create a master clock or validate PPS wiring. [Driver time conversion](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/lslidar_driver/src/lslidar_driver.cpp).

### C1 DIFOP and UCWP reference

DIFOP is a **1206-byte read-only status/configuration payload** normally sent once per second. UCWP is a different 1206-byte configuration write, with a different header; its settings take effect immediately according to the old manual. The manufacturer recommends its utility and discourages constructing packets yourself. The tables make captured data understandable; they are not a raw configuration sender. [Manual §§5.2–5.3](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

| DIFOP field                        | Offset / bytes         | Meaning / available scale                                                      |
| ---------------------------------- | ---------------------- | ------------------------------------------------------------------------------ |
| Header                             | 0 / 8                  | `A5 FF 00 5A 11 11 55 55`                                                      |
| Motor speed                        | 8 / 2                  | Big-endian RPM: 300/600/1200 for 5/10/20 Hz                                    |
| Sensor / destination IP            | 10 / 4; 14 / 4         | Ordered IPv4 octets                                                            |
| MAC                                | 18 / 6                 | Read-only device address                                                       |
| Cloud / device ports               | 24 / 2; 26 / 2         | Big-endian uint16                                                              |
| Reserved network area              | 28 / 4                 | Old table reserves it; supported current NTP setter uses it for server IP      |
| Gateway / mask                     | 32 / 4; 36 / 4         | Ordered IPv4 octets                                                            |
| Rotation state                     | 40 / 2                 | 0 rotate, 1 stationary                                                         |
| Reserved / clock                   | 42 / 2; 44 / 2         | Old table 0 GPS, 1 PTP; actual FPGA4 driver also uses 2 NTP                    |
| PPS target angle / reported error  | 46 / 2; 48 / 2         | Target at 0.01°; raw error/valid field has the source ambiguity below          |
| Reserved / UTC                     | 50 / 2; 52 / 6         | UTC calendar status in this table                                              |
| Latitude/longitude block           | 58 / 22                | Preserve the block; this field list does not establish a generic float decoder |
| APD / laser-board temperatures     | 80 / 2; 82 / 2         | Raw monitor fields; exact scaling not provided in this public table            |
| APD / laser high-voltage monitors  | 84 / 2; 86 / 2         | Raw monitor fields; do not label unscaled counts volts                         |
| Third-board temperature / humidity | 88 / 2; 90 / 2         | Raw monitor fields, conversion not established here                            |
| GPS / PPS status                   | 92 / 1; 93 / 1         | Save observed status with clock evidence                                       |
| High-temperature suspension        | 94 / 2                 | Raw status field                                                               |
| Dirty-cover count / alarm / energy | 96 / 1; 97 / 1; 98 / 2 | Separate contamination diagnostics                                             |
| Threshold adjustment               | 100 / 1                | Raw configuration/status value                                                 |
| Input voltage / current            | 101 / 2; 103 / 2       | Raw measured fields; use documented matched utility for engineering units      |
| Runtime                            | 105 / 4                | Raw operating-duration field; unit not specified by this table                 |
| Reserved / tail                    | 109 / 1095; 1204 / 2   | Preserve reserved bytes; tail `0F F0`                                          |

UCWP uses header `AA 00 FF 11 22 22 AA AA` and the same tail `0F F0`. Its defined writable map is motor at 8, network at 10–39, rotation at 40, clock at 44 and PPS target at 46, with bytes 48–1203 reserved. MAC remains read-only. The older sample's clock bytes are big-endian; for example 600 RPM is `02 58`, not a new speed in Hz. PPS target 90° corresponds to 9000 counts. The alignment-error description combines a validity bit with a signed 15-bit field but also claims ±18000 counts, which is not a consistent signed-15-bit range. Preserve the raw word and use the matched utility/firmware definition rather than inventing a sign-extension rule. [Manual configuration/error tables, pp. 28–30](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

### C1 ROS service reference and multisensor operation

Inspect actual names with `ros2 service list -t` and inspect a service type using `ros2 interface show lslidar_msgs/srv/TimeService` before planning a change. The usual namespace is `/cx`, but a renamed launch changes that path. **These are state-changing services**; their presence does not authorize every feature on every CX model or revision.

| Relative service / type                | Request fields                              | Behavior and verification                                                               |
| -------------------------------------- | ------------------------------------------- | --------------------------------------------------------------------------------------- |
| `time_service` / `TimeService`         | `time_service_mode` string; `ntp_ip` string | `gps`; FPGA4 path also `ptp`/`ntp`, with valid NTP IPv4 required for NTP                |
| `lslidar_control` / `LslidarControl`   | `laser_control` integer 0/1                 | Disable/enable measurement; disabling can leave the motor rotating and DIFOP continuing |
| `motor_control` / `MotorControl`       | `motor_control` integer 0/1                 | Stop/rotate motor; a separate operation from laser-output control                       |
| `set_motor_speed` / `MotorSpeed`       | `motor_speed` int32                         | 5/10/20 Hz, not RPM; confirm actual supported scanner rate and matching host resolution |
| `set_data_port` / `DataPort`           | `data_port` integer                         | Cloud destination port, 1025–65535                                                      |
| `set_dev_port` / `DevPort`             | `dev_port` integer                          | DIFOP destination port, 1025–65535                                                      |
| `set_data_ip` / `DataIp`               | `data_ip` string                            | Sensor source IPv4; not the host target                                                 |
| `set_destination_ip` / `DestinationIp` | `destination_ip` string                     | Host destination IPv4; wrong setting can make data disappear                            |

In the inspected implementation, the Boolean `result` can be set **before sending the UDP configuration**, so it is not a verified sensor ACK/readback. Record old values, perform one supported change, re-read actual DIFOP and observe resumed valid MSOP. After a sensor port/IP change, update local YAML and restart the driver as documented. Preserve the old network path/configuration for recovery. If a delivered device rejects a mode, do not edit raw bytes until an unsupported service appears to succeed. [Service reference](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/README_en.md), [actual service handlers](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/lslidar_driver/src/lslidar_driver.cpp).

For multicast, retain a normal unicast IPv4 on the host interface, configure the actual sensor destination group through supported tools, and enable `add_multicast`/`group_ip` for that same group and interface. Do not assign a multicast group as the host's ordinary interface address merely because the old manual labels the group “computer IP.” A YAML group does not change the sensor's destination. When using more than one scanner:

1. Establish one working C1 first and record source IP, MSOP/DIFOP ports, return mode and clock configuration.
2. Give each sensor/receiver configuration an unambiguous input path: unique source addresses, appropriate destination ports/adapters and explicit namespaces. A second namespace alone does not separate two identical UDP sources arriving at one socket.
3. Use the official double/four-device launch patterns with matching per-node YAML. Keep each node name/namespace aligned with its parameter block, independent cloud topic/frame and measured mounting transform.
4. Capture and inspect each source separately before merging clouds. Confirm no duplicate IP, unintended broadcast receiver or mismatched DIFOP profile; compare per-source rates and clock status.

**Expected result:** each namespaced node publishes only its intended sensor's scan/cloud, with distinct frames and consistent timestamps. Host multicast routing must be scoped to the intended interface; a broad route change is not a generic fix for an incorrect group or destination. [Official driver multicast/multiple-device configuration](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/README_en.md).

### C1 recording, exports and supported timing inputs

The older Windows client supports live reception, packet recording/replay, point tables and CSV export. Configure data/equipment ports, receive a known scene and save both raw data and the displayed state. A CSV row is a processed point, while raw packets preserve the return/timing/configuration fields needed to re-evaluate a decoder. Close other processes owning the same UDP ports; the client documents exclusive-port failures. If packets arrive but graphics do not update, check the model/profile, application-specific firewall rule and graphics adapter before changing the sensor.

For matched PCAP replay, set the YAML `pcap` path and C1-appropriate packet rate (about 416.7/s single, twice that dual under the old profile), retaining DIFOP and actual model byte. Compare one finite capture's angle wrap, return flags and timestamp continuity. Do not take generic YAML 1695 packets/s or 200 m maximum filter as the C1's physical rate/range. [Manual §4.1 and driver replay parameters](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

For GPS, the old manual documents separate TTL and RS232 receiving-interface versions, 9600 baud/8N1, PPS High longer than 1 ms and GPRMC time/date information. Its RS232-version PPS input range is 3–15 V, while the optional box and other interface tables have their own limits. **Identify the delivered electrical version first**; the values are not interchangeable terminal ratings. The manual describes gPTP separately, while the inspected ROS service accepts the supported `ptp` mode without independently exposing a profile/transport selector. Obtain the firmware's exact profile and master requirements rather than assuming a service string chooses IEEE 802.1AS. Raw PPS without a valid date source does not establish UTC. [Manual timing chapter 6](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result on the matched assembly

1. Check the label for C1 hardware/protocol revision, obtain the matching harness and ≥25 W approved supply, and secure the sensor on a conductive bracket. Remove optical shipping film. Connect with power off; leave GPS/sync insulated.
2. Configure a dedicated host adapter to **192.168.1.102/24**. The factory sensor address is `.200`; observe actual ARP traffic if previous settings are unknown.
3. Enable the approved power path and capture Ethernet traffic. Confirm cloud UDP 2368 and device UDP 2369 before running a decoder.
4. Open the manufacturer-supplied C1 Windows client for the applicable revision. Record device/network/return/time settings, display a fixed target and save a capture for replay. Do not change IP or time settings just to obtain the first frame.

**Expected result:** a coherent planar 360° scene from the identified C1, with a saved capture and known settings. The current one-page sheet alone does not establish compatibility with every older client; use the delivered revision's client or the verified V 4 ROS path below. [Manual Windows/connection sections](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

### Original read-only C1 packet check

Close other receivers. This Python 3 program listens eight seconds on the cloud destination port and checks the actual C1 V4 identity bytes. It sends nothing:

```python
import collections
import socket
import time

shapes = collections.Counter()
recognized = 0
with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as sock:
    sock.bind(("192.168.1.102", 2368))
    sock.settimeout(0.2)
    end = time.monotonic() + 8
    while time.monotonic() < end:
        try:
            data, peer = sock.recvfrom(65535)
        except socket.timeout:
            continue
        shapes[(peer[0], len(data))] += 1
        if len(data) == 1212 and data[1211] == 0x01:
            recognized += 1
            if recognized == 1:
                print("C1 source", peer, "echo flag", hex(data[1210]),
                      "first block bytes", data[:4].hex())
print("shapes", dict(shapes), "C1-shaped packets", recognized)
if not recognized:
    raise SystemExit("No C1 V4-shaped payload: verify actual model, revision and endpoints")
```

**Expected result:** C1-shaped packets and an expected echo flag. This is not a complete checksum/geometry/timestamp validation; a different model byte is a reason to stop and check the model rather than force it into C1 decoding.

### Pinned ROS2 Humble workflow

Use a fresh Ubuntu 22.04/Humble workspace with colcon, PCL ROS/conversions, pluginlib, Boost and libpcap development dependencies:

```bash
mkdir -p ~/c1_ws/src
cd ~/c1_ws/src
git clone --branch C1_V4.0 https://github.com/Lslidar/Lslidar_ROS2_driver.git
cd Lslidar_ROS2_driver
git checkout 943799a978f749ff31c51c952419858315ebd994
```

Edit `lslidar_driver/params/lslidar_cx.yaml`: retain actual `device_ip`, ports 2368/2369, `distance_unit:0.4` (the driver's centimeter-based factor), frame `laser_link` and the intended range filters. Set `horizontal_angle_resolution` to 0.09/0.18/0.36 for actual 5/10/20 Hz. Use `publish_scan:true` and `scan_num:0` if a planar LaserScan is required. Keep `use_time_service:false` for an initial host-time bench check unless external timing has been configured and verified. The generic 200 m filter maximum is not C1's specified range.

```bash
cd ~/c1_ws
source /opt/ros/humble/setup.bash
colcon build
source install/setup.bash
ros2 launch lslidar_driver lslidar_cx_rviz_launch.py
```

In a second sourced terminal, use `ros2 topic list -t` to find the actual namespaced cloud and scan topics. Check the cloud/scan rate with `ros2 topic hz` and inspect headers. **Expected result:** one-ring planar cloud, and a populated LaserScan if enabled with ring 0. For PCAP replay, set the YAML's actual `pcap` path and a model/mode-appropriate `packet_rate`; the shipped 1695 value is a generic CX example, not C1's roughly 416.7 single-return packets/s. [Driver parameters and replay](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/README_en.md).

## Troubleshooting and FAQs

### FAQs <a href="#faqs" id="faqs"></a>

| Symptom                          | C1-specific checks                                                                                |
| -------------------------------- | ------------------------------------------------------------------------------------------------- |
| No startup / repeated restart    | ≥25 W supply capacity, cable loss, connector polarity, cold/20 Hz demand                          |
| Cloud absent, status present     | MSOP 2368 versus DIFOP2 369, actual host target, client ownership and scoped firewall rules       |
| Cloud works, LaserScan empty     | `publish_scan:true`, **`scan_num:0`**, resolved namespace and actual message type                 |
| Wrong model / distorted geometry | C1 byte 0x01, V 4 branch, range factor, actual return mode and azimuth interpolation              |
| Bad time or fusion               | Current time mode/lock, packet-end timestamp and point offsets; host-time option is not GNSS lock |
| Sparse small objects             | One plane, beam footprint, angular sampling, reflectivity and chosen rotation rate                |

**Does ±1 cm describe absolute accuracy?** The current sheet separates ±3 cm accuracy from ±1 cm standard-deviation precision.

**Can I reuse an extension cable's colors for the default adapter?** No. The manual has different assembly tables; use exact connector contacts and the matched cable drawing.

Save captures/configuration before any reset or network change. The ROS repository exposes laser, motor, speed, time and network services; these write sensor state and are not passive diagnostics. Use only revision-matched commands after reading their request definitions. For maintenance, follow the C1 manual's own approved cleaning process and keep grit from scratching the cover; another manufacturer's solvent policy is not transferable. Store dry, protect optics/cables and use original protective packaging. [Manual maintenance and power appendices](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

### C1 optical maintenance and storage

The V4.0.6 manual recommends ventilated, dry storage at **23±5 °C and 30–70% RH**, within its −40 to +85 °C absolute storage range, and original protective transport packaging. Use clean powder-free gloves during installation and retain the base's heat-transfer path.

For this manual's optical material, remove loose contamination gently with clean air or a dust-free cloth. It permits **99% ethanol for stubborn contamination**, in a ventilated area away from ignition: soften the stain, wipe gently with a clean damp dust-free cloth, replace a contaminated cloth and remove remaining liquid with a fresh one. This is model/revision-specific guidance; it does **not** authorize ethanol on JT128's polycarbonate cover or another sensor. Keep connectors dry and never operate with damaged housing. Current delivered-material instructions take precedence if the optical cover has changed. [C1 manual Appendix A](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf).

## Downloads and technical documents

| Resource                                                                                                                                                                    | Exact scope                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Current C1 official sheet](https://www.lslidar.com/wp-content/uploads/2024/09/C1.pdf)                                                                                      | 120 m/100 m conditions, accuracy versus precision and current electrical/environmental limits                 |
| [Current C1 manufacturer page](https://www.lslidar.com/product/c1-single-line-mechanical-lidar/)                                                                            | Model identity and application context                                                                        |
| [Manufacturer C1 manual v4.0.6, public mirror](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf) | 50 pages; wiring, client, protocol, time, coordinates, maintenance; older range/voltage differences disclosed |
| [Official C1 V4 ROS2 branch](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/README_en.md)                                     | Pinned model detection, Humble build, parameters and services                                                 |
| [C1 V4 ROS1 branch](https://github.com/Lslidar/Lslidar_ROS1_driver/tree/C1_V4.0)                                                                                            | Separate ROS1 integration reference                                                                           |

The sensor connector face and table were visually inspected. The manufacturer-authored mirrored manual is identified as such; its distribution location is not represented as the current official download center.

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed 24 November 2026: current official C1 page/sheet, manufacturer-authored v4.0.6 manual, exact store selection and actual C1 V4 driver/parameters/model detection. Older 150 m and 36 V wording is kept separate from the current 120 m and 9–32 V scope.

**Driver compilation, Windows/ROS execution, packet-check execution, configuration/firmware writes and physical power/range/timing tests: not run.** The packet identity check is original and syntax checked.

* [Current LSLiDAR C1 official sheet](https://www.lslidar.com/wp-content/uploads/2024/09/C1.pdf) — manufacturer 2024 PDF.
* [Current C1 official product page](https://www.lslidar.com/product/c1-single-line-mechanical-lidar/) — 24 Nov 2026.
* [Manufacturer-authored C1 user manual, public distributor mirror](https://gehtmarketplace.com/public/uploads/listings/d1e6c0859bf8f3b2470d68bb95c4a924/a5d75cb8e2cc56c3c8218ad41e59feca-0.pdf) — v4.0.6 May 2023; 50 pages.
* [LSLiDAR C1 V4 ROS2 branch](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/README_en.md) — commit 943799a978f749ff31c51c952419858315ebd994.
* [C1 model byte and scan-ring implementation](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/lslidar_driver/src/lslidar_driver.cpp) — commit 943799a978f749ff31c51c952419858315ebd994.
* [Actual generic CX parameter defaults](https://github.com/Lslidar/Lslidar_ROS2_driver/blob/943799a978f749ff31c51c952419858315ebd994/lslidar_driver/params/lslidar_cx.yaml) — commit 943799a978f749ff31c51c952419858315ebd994.
* [Exact C1 sensor-only listing](https://openelab.io/products/lslidar-c1-mechanical-lidar-sensor) — 23 Nov catalog plus observed public page 24 Nov.
