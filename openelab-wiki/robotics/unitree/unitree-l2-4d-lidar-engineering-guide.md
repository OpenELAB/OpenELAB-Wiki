---
description: >-
  Connect L2 with separate 12 V power and data-only UART; reconcile mode
  defaults, calibrated packets, timestamps and pinned SDK2 while retaining the
  historical SKU gap.
---

# Unitree L2 4D LiDAR Engineering Guide

{% hint style="info" %}
[**Historical OpenELAB listing — exact current SKU remains unlisted**](https://openelab.io/products/unitree-l2-4dlidar-navigation-obstacle-avoidance-slam-360-depth-scan)

**Model / option:** Assigned historical L2 package; current store match unresolved · **Historical SKU:** `Unitree-L24DLiDAR` (absent from the current observed catalog). Current SKU/store-match fields remain `null`; this is not a replacement package.
{% endhint %}

## Product overview <a href="#product-overview" id="product-overview"></a>

### Unitree L2 4D LiDAR Engineering Guide <a href="#unitree-l2-4d-lidar-engineering-guide" id="unitree-l2-4d-lidar-engineering-guide"></a>

**Unitree L2 is a compact non-repetitive 3D LiDAR with an integrated IMU, Ethernet UDP and selectable TTL UART.** Its standard 3D field is 360° × 90°; negative-angle mode extends it to 360° × 96°. “4D” denotes 3D position plus grayscale, not a direct Doppler-velocity channel. [Official L2 manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf), [current product](https://www.unitree.com/L2/).

This guide retains the established OpenELAB URL and assigned `Unitree-L24DLiDAR` reference. That SKU is absent from the current complete observed catalog. Earlier verification recorded a 404 for the established URL; the latest separate product-JSON request returned 429 (rate limited), which does not establish its current page status. The actual existing CMS Markdown is preserved as the update baseline. Confirm the current exact listing/package before procurement; no substitute store handle or variant ID is invented.

### Quick Summary <a href="#quick-summary" id="quick-summary"></a>

L2 supplies non-repetitive depth plus reflectivity and an IMU through one selected output path, Ethernet UDP or TTL UART. **SDK mode value 0** means standard 3D with IMU enabled, Ethernet and automatic startup; serial example mode 8 changes the interface bit. That bit interpretation is not a universal delivered factory default: the device manual, portal and Viewer disagree about initial NEGA and IMU settings. The current exact OpenELAB listing/package remains unresolved, so the historical URL is preserved without inventing an in-stock or included-accessory claim.

[Model-specific source](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf).

## Applications <a href="#applications" id="applications"></a>

L2 is useful for compact robot scene capture, LiDAR/IMU odometry and mobile mapping research. Its two-axis rotating mirror produces nonuniform point density and acquisition timing. A rendered dense wall accumulated over time is different from an instantaneous uniformly sampled frame.

Start with a fixed sensor on its supplied rubber pad or a suitable mount. Verify the cloud and status first, and IMU only if actually enabled; obtain a deliberate configuration decision before enabling it for Point-LIO. The official Point-LIO adaptation can use L2 plus its integrated IMU, but that does not guarantee drift-free maps or external position truth. Preserve scan timing, frame transforms and dataset configuration when evaluating motion. [SDK2](https://github.com/unitreerobotics/unilidar_sdk2), [official Point-LIO adaptation](https://github.com/unitreerobotics/point_lio_unilidar).

### Project References and Application Ideas <a href="#project-references-and-application-ideas" id="project-references-and-application-ideas"></a>

* [Unitree Unilidar SDK2](https://github.com/unitreerobotics/unilidar_sdk2): official SDK with C++ interfaces plus ROS and ROS2 packages for parsing and publishing Unitree L2 point cloud and IMU data.
* [Unitree point\_lio\_unilidar](https://github.com/unitreerobotics/point_lio_unilidar): official adaptation of Point-LIO for Unitree L1 and L2, with L2 video demos and sample data workflow.
* [point\_lio\_ros2 with Unitree L1/L2 support](https://github.com/dfloreaa/point_lio_ros2): community ROS2 port for engineers building ROS2-first LiDAR-inertial odometry stacks.
* [unilidar\_fastlio\_ros2](https://github.com/newkillerwhale/unilidar_fastlio_ros2): community ROS2 FAST-LIO-style integration for Unitree LiDAR.
* [Unitree Go2 L2 application reference](https://www.unitree.com/go2/): the current manufacturer page explicitly names L2 with 360° × 96° coverage and a 0.05 m minimum detection distance. This is a manufacturer platform description; inspect the actual delivered robot before using it as a bill of materials.
* Application ideas: indoor AMR localization, warehouse obstacle perception, quadruped mapping, service robot navigation, autonomous cleaning robot perception, educational SLAM labs, and low-speed outdoor survey robots.

[Model-specific source](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf).

## Specifications <a href="#specifications" id="specifications"></a>

### Key Specifications <a href="#key-specifications" id="key-specifications"></a>

| Parameter                    | L2 manual/current model scope                                                              |
| ---------------------------- | ------------------------------------------------------------------------------------------ |
| Laser / safety               | 905 nm, Class 1 IEC60825-1:2014                                                            |
| 3D FOV                       | 360° × 90° standard;360° × 96° negative-angle mode                                         |
| 2D FOV                       | 180° standard;192° negative-angle mode; not 360° planar scan                               |
| Reflectivity-qualified range | 30 m at 90%;15 m at 10%                                                                    |
| Near blind zone              | 0.05 m; near-limit output is reference-only without guaranteed accuracy                    |
| Point rates                  | 128,000 samples/s;64,000 effective points/s                                                |
| Scan frequencies             | 5.55 Hz circumferential;216 Hz vertical                                                    |
| Range accuracy / resolution  | ≤2 cm under stated 25 °C/90%-target/15 m test;4.5 mm resolution                            |
| IMU                          | 3-axis gyro +accelerometer;1 kHz sampling,500 Hz reporting                                 |
| Interfaces                   | Ethernet UDP or TTL UART, one output method selected at a time                             |
| UART rate                    | 4,000,000 baud                                                                             |
| Supply / power               | 12 V DC;10 W typical at 25 °C; self-heating peak 13 W                                      |
| Environment                  | −10 to +50 °C operating;−20 to +60 °C storage; IP54 with installation-dependent protection |
| Body / mass                  | 75 × 75 × 65 mm;230 g                                                                      |

[Official 18-page manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf). The current product page emphasizes 96° coverage; the manual and SDK explain its optional mode. The SDK's 180°/192° mode labels refer to the scan mechanism/2D coverage, not a halving of the 3D circumferential field. Do not turn the software `range_max:100` acceptance filter into a 100 m product claim.

## Hardware and connections <a href="#hardware-and-connections" id="hardware-and-connections"></a>

### Power and three cable branches <a href="#interface-and-network-details" id="interface-and-network-details"></a>

The manual specifies 12 V DC and the supplied adapter path. It does not establish an arbitrary 9–32 V input envelope. During self-heating, especially within the documented −10 to +30 °C environment, the sensor can delay point output while warming and reach 13 W. Choose the approved supply/cable with that demand allowed for.

| Branch                   | Documented connection                                           |
| ------------------------ | --------------------------------------------------------------- |
| DC power                 | Dedicated positive/negative supply branch; matched 12 V adapter |
| RJ45                     | Pins 1/2 Ethernet TX+/TX−;3/6 RX+/RX−                           |
| GH 1.25-4 Y serial pin 1 | Unused; do not inject power                                     |
| Serial pin 2             | UART\_GND, pink reference wire                                  |
| Serial pin 3             | SensorUART\_RX, white; host TX goes here                        |
| Serial pin 4             | SensorUART\_TX, brown; host RX goes here                        |

[Manual interface table, p 5](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf). The four-pin serial plug **does not power the LiDAR**. The source identifies TTL but does not specify a verified absolute UART input-voltage limit; use the supplied converter rather than an assumed 5 V or RS232 adapter. The manual's prose and power-connector table disagree slightly on barrel size(3.5 versus 3.4 mm); use the matched assembly and do not force a nominally similar plug. The interface table was visually inspected, but no custom cable-face numbering is inferred without the actual connector drawing.

### Mount and frame definition <a href="#hardware-integration-notes" id="hardware-integration-notes"></a>

Keep the optical field and rotating assembly clear. The bottom mechanical drawing shows M3 mounting holes with 6 mm depth; allow for bracket thickness and avoid bottoming screws. Remove shipping protection before use. Do not restrain the rotating mechanism by hand: the manual says it may automatically resume when an obstruction is removed. Power down before clearing a mechanical obstruction.

Cloud origin is the center of the bottom mounting surface;+X points opposite the cable outlet,+Y is 90° counterclockwise from +X and +Z is normal to the bottom. SDK2 gives the IMU origin in the cloud frame as **(−0.007698,−0.014655,0.00667) m**, with parallel axes. Keep translation and rotation direction explicit in the robot transform. [SDK frame definition](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/README.md).

The manual recommends keeping the bottom cover below 85 °C with suitable heat dissipation; this is not an 85 °C ambient operating rating. Sensor IP54 does not waterproof an exposed adapter or connector assembly.

## Software and development resources <a href="#software-and-development-resources" id="software-and-development-resources"></a>

### SDK/API and mode boundaries <a href="#software-workflow" id="software-workflow"></a>

Use **unitreerobotics/unilidar\_sdk2**, not the L1 SDK. The reviewed repository's validated ROS environments are Ubuntu 20.04/ROS Noetic/PCL 1.10 and Ubuntu 20.04/ROS2 Foxy/PCL 1.10. Its ROS2 package exists, but a Humble/Jazzy build is not established by those examples. CMake uses C++17 and architecture-specific `libunilidar_sdk2.a`; confirm the provided library matches host architecture/ABI. [README/CMake](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/README.md).

| Mode bit | 0                   | 1                           |
| -------- | ------------------- | --------------------------- |
| 0        | Standard FOV        | Expanded/negative-angle FOV |
| 1        | 3D                  | 2D                          |
| 2        | IMU enabled         | IMU disabled                |
| 3        | Ethernet            | Serial                      |
| 4        | Power-on auto start | Wait for start command      |

Work-mode **value** 0 selects standard 3D, IMU enabled, Ethernet and auto start; it must not be assumed to be the factory value of every delivered unit. Serial example mode 8 changes only the interface bit. These are sensor-control settings; record existing values before writing. [Actual SDK mode table](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/README.md).

The factory UDP endpoints are sensor **192.168.1.62: 6101**, host **192.168.1.2: 6201**. Source and destination ports are not interchangeable. The actual ROS2 launch sets `initialize_type:2`,`work_mode:0`,`use_system_timestamp:true`,`cloud_scan_num:18`, cloud topic `unilidar/cloud`, IMU topic `unilidar/imu` and separate frames `unilidar_lidar`/`unilidar_imu`. [Actual launch](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_ros2/src/unitree_lidar_ros2/launch/launch.py).

**The official UDP sample is not read-only:** it starts rotation, sets work mode 0 and resets the LiDAR before reading. Do not present it as a passive diagnostic. The ROS node also configures modes; use it only after the stationary identification/capture checkpoint.

### L2 reader API, packet families and status outputs <a href="#l2-reader-api-packet-families-and-status-outputs" id="l2-reader-api-packet-families-and-status-outputs"></a>

The SDK reader separates transport setup from parsing and device control. `initializeSerial` defaults to `/dev/ttyACM0`, **4,000,000 baud**, 18 scan lines and host timestamps; `initializeUDP` defaults to the sensor/host endpoints above with the same scan aggregation. `range_min`/`range_max` are software filters, whose generic 0/100 m values do not replace the product's qualified range. Check the initialization result before polling `runParse()` and dispatching on the returned packet-type ID.

| SDK packet type | Input/output contract                                                                                                  |
| --------------- | ---------------------------------------------------------------------------------------------------------------------- |
| 102 / 103       | 3D-line / 2D point data, respectively; valid sample count, scan timing, ranges and intensities                         |
| 104             | IMU data containing quaternion, angular velocity and linear acceleration; confirm axis/clock conventions before fusion |
| 105 / 106       | Version record / seconds-and-nanoseconds timestamp                                                                     |
| 101             | ACK: original packet type, command type/value and execution status                                                     |
| 107 / 108 / 109 | Work-mode / IPv4 and ports / MAC configuration transactions; these change device setup                                 |

The protocol header is **12 bytes** with magic `55 AA 05 0A`, 32-bit packet type and declared whole-packet size. Its 12-byte tail contains CRC32, an acknowledgement check field, reserve and `00 FF`. Data records include sequence, payload size and seconds/nanoseconds. Preserve those fields for continuity diagnostics. The source header has inconsistent byte-count comments for some structures, so **use the declared packet length and pinned parser**, not the comments as an independent wire-size specification. [Actual protocol definitions](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/include/unitree_lidar_protocol.h).

The point-data record supplies per-line angle/timing, per-device calibration and inside-state fields: upper/lower motor periods, contamination index, upper/lower packet-loss indicators and APD/laser/IMU temperatures or voltages. These are diagnostics to record, not physical SI values to invent from field names without the appropriate revision definition. The 3D structure reserves arrays for 300 ranges/intensities; 2D reserves 1800. Use `point_num` rather than assume every array element is valid.

ACK status **1/2/3/4/5** means success/CRC error/header error/block error/data-not-ready. Mode/IP setters and rotation controls return `void` in the public C++ interface, so a call returning to the program is not proof of device acceptance. Inspect the corresponding parsed ACK and subsequent state/data. `syncLidarTimeStamp`, `setLidarWorkMode`, IP/MAC setters and reset/start/standby operations are state-changing; keep them out of a passive receive-only check. `getBufferCachedSize`/`getBufferReadSize` help distinguish a growing receive backlog from no incoming traffic. [Reader API](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/include/unitree_lidar_sdk.h).

These manufacturer development details do not resolve the exact OpenELAB SKU/store-match gap or authorize an unverified harness; physical commissioning remains bounded as described in the opening and hardware sections.

### Viewer controls, versioned defaults and unknown-IP recovery <a href="#viewer-controls-versioned-defaults-and-unknown-ip-recovery" id="viewer-controls-versioned-defaults-and-unknown-ip-recovery"></a>

The **Unilidar2 Viewer v1.0 (November2024)** is a Windows64-bit tool distinct from the SDK mode table. Select the actual local adapter for **Open UDP Port**, or the enumerated supplied converter's COM port for **Open Serial Port**. Network and serial are alternative cloud-output modes, not simultaneous streams. Read **GetVersion** and **Synchronous** (parameter readback) before changing anything.

| Viewer control           | Behavior and verification                                                                                                                                                    |
| ------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Point cloud count        | Display accumulation **500 ms / 1 / 2 / 4 s**; a longer display is not a higher sensor frame rate                                                                            |
| Normal / NEGA            | Standard versus expanded negative-angle FOV; expanded angles have reduced far-range capability                                                                               |
| 3D/2D                    | Measurement mode; match packet family/consumer                                                                                                                               |
| IMU Display Enable       | Viewer documents SetMode and Restart for this setting; it can enable IMU output as well as attitude-following display. Treat it as a device setting, not a passive UI toggle |
| Gray Enable              | Grayscale/intensity output setting, not a new RGB camera stream                                                                                                              |
| SELF START / CMD START   | Automatic acquisition after power or wait-in-standby for an explicit acquisition command                                                                                     |
| Normal / Standby         | Immediate acquisition-state controls; do not use a reset as a discovery query                                                                                                |
| SetMode / Restart        | Submit mode changes, require successful response, then restart for documented settings to take effect                                                                        |
| Config Setting / Change  | Separate sensor IP/port/gateway/mask from receiving-host IP/port; submit Change, require success and restart                                                                 |
| Restore Factory Defaults | The manual describes restoring **network/IP parameters** to `.62:6101` and target `.2:6201`; do not claim a full optical calibration reset                                   |

**Factory-default evidence conflicts even within the device manual.** The October 2024 V1.1 manual's introduction (PDF page 4 / printed page 2), current About L2 portal article, and November 2024 Viewer manual specify **NEGA, IMU disabled, 3D, Ethernet, self-start and grayscale on**. The same device manual's later mode section (PDF page 13 / printed page 11), preparation/development portal text, and SDK mode-0 description instead give normal-angle behavior; SDK mode 0 also enables IMU. These are unresolved revision/documentation differences, not one combined factory guarantee. Read back the delivered device configuration, record firmware/Viewer/hardware identity, and verify each actually received packet family. Do not automatically write mode 0 or enable IMU merely to make a first-result example succeed.

For an unknown IP, inspect the isolated network passively first. The manufacturer Viewer describes recovery through its **supplied serial converter**: open the supported serial connection, read current parameters, enter the intended network values in **Config Setting**, choose **Change**, confirm success and **Restart**, then reconnect at the recorded new address and reread version/parameters. Opening serial control does not imply that an Ethernet-mode sensor already streams cloud over serial. Use SetMode only when intentionally changing the output transport. The exact store/harness gap above remains unresolved, so this is a manufacturer-supported reference procedure for an already identified complete L2 assembly, not a guessed wiring instruction. [Official Viewer manual](https://www.unitree.com/download).

Viewer **Lidar Info** shows `dirty_index`, `packet_lost_up/down`, motor fields and APD/laser/IMU values. The text labels `imu_temperature` in volts and motor `*_rotation_period` fields in RPM despite the SDK calling them periods. Treat those conflicting labels as unverified scale/unit descriptions; retain raw values and trend against an actual manufacturer definition, rather than convert them to a fabricated absolute temperature or RPM. APD/laser voltage fields and the cleanliness/loss trends remain useful diagnostic observations. The IMU window exposes quaternion Q1–Q4 and XYZ acceleration/gyro; do not infer quaternion component order or physical units from window labels alone. [Viewer v1.0 status/control reference](https://www.unitree.com/download), [pinned raw state structures](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/include/unitree_lidar_protocol.h).

### Verified packet layouts, calibration and integrity <a href="#verified-packet-layouts-calibration-and-integrity" id="verified-packet-layouts-calibration-and-integrity"></a>

The actual [pinned protocol declarations](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/include/unitree_lidar_protocol.h) and [public conversion utilities](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/include/unitree_lidar_utilities.h) allow a more precise contract than stale prose byte counts. Header fields are `header[4]`, uint32 packet type, uint32 **whole-packet** length; tail fields are uint32 CRC, uint32 `msg_type_check`, two reserved bytes and `00 FF`. Serialize/parse explicitly for the matching wire format rather than transmitting a native compiler structure with assumed padding or endianness.

| Packet type              | Whole bytes from pinned field layout | Contents / boundary                                                                                                                                                           |
| ------------------------ | ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 100 user control         | 32                                   | Two uint32 command/value fields; explicit device action                                                                                                                       |
| 101 ACK                  | 40                                   | Original packet type, command type/value, status; success must be observed                                                                                                    |
| 102 3D line              | **1044**                             | 16-byte data info, 36-byte inside state, 32-byte calibration, 32 bytes line float fields, uint32 point count, 300 uint16 ranges and 300 byte intensities, plus 24 header/tail |
| 103 2D line              | **5536**                             | Same information/state/calibration; six line floats, point count, 1800 uint16 ranges and 1800 byte intensities, plus header/tail                                              |
| 104 IMU                  | **80**                               | 16-byte data info, ten floats for quaternion/angular/linear arrays, plus header/tail                                                                                          |
| 105 version              | **104**                              | Hardware/software code fields, name/date/reserved fields; not an update image                                                                                                 |
| 106 time synchronization | **32**                               | uint32 seconds + uint32 nanoseconds, plus header/tail; a command is not passive                                                                                               |
| 107 work mode            | **28**                               | One uint32 bit field; bits 5–31 reserved at this pin                                                                                                                          |
| 108 IPv4/ports           | **44**                               | Four IPv4 arrays and two uint16 ports; changes can remove the old transport path                                                                                              |
| 109 MAC                  | **32**                               | Six MAC bytes and two reserved bytes                                                                                                                                          |

These are **layout calculations at the reviewed source pin**, not hardware-capture measurements or a promise about every firmware. The [developer chapter](https://support.unitree.com/home/en/L2_SDK/L2_develope) summary agrees with several values, but its 3D prose says 1032 and gives obsolete 12-byte information/28-byte state blocks. The public header also retains inconsistent comments such as 1036/5528/156/40. Work-mode and MAC prose sizes conflict too. Validate the declared whole length, known packet family, actual buffer extent, CRC and model/firmware before decoding; do not resolve conflicts by copying a convenient comment.

`DataInfo` contains uint32 sequence, uint32 payload size, and seconds/nanoseconds. Sequence storage is 32-bit; a portal “maximum 1024” description is not an independently verified universal wrap rule. **3D capacity 300 and 2D capacity 1800 are reserved array sizes, not guaranteed valid counts**: reject point counts outside capacity or available bytes. Raw zero range is invalid. The public conversion performs packet calibration and range filtering; fixed-capacity casts without bounds checks are unsuitable for untrusted input.

The calibration block carries `a_axis_dist`, `b_axis_dist` (meters), four optical angle terms (radians), `range_bias` (millimeters), and `range_scale`. The public range equation is `range_scale * (raw_range + range_bias)` followed by its full optical projection and both packet/user range gates. Angles and calibrated optical axes are not a generic spherical sensor convention. At this exact pin, **`parseFromPacketPointCloud2D` produces `x = 0`, `y = cos(alpha) * range`, and `z = sin(alpha) * range + a_axis_dist`**. Its output is therefore in the SDK's **Y–Z plane**, with the stated calibration offset; it is **not automatically an X–Y horizontal `LaserScan`**. A downstream planar consumer needs an explicitly defined mounting/frame transform and scan-angle convention. Do not guess a physical mounting direction or invert axes merely because 2D mode is selected. No complete third-party decoder was hardware-validated here.

CRC uses the public reflected polynomial `0xEDB88320`, initial `0xFFFFFFFF` and final complement over header+data, excluding the tail; do not treat a magic prefix alone as integrity. Tail type-check/reserved fields and ACK status still require the matching firmware contract. The available ACK meanings are 1 success, 2 CRC error, 3 header error, 4 block error, 5 waiting/not-ready. Avoid interpreting “a setter returned” as acceptance because several control APIs return void.

### Clock, transport and operating-state detail <a href="#clock-transport-and-operating-state-detail" id="clock-transport-and-operating-state-detail"></a>

The public converter's device-time path uses packet seconds plus nanoseconds × `1e-9`. Its host-time cloud start is **host CLOCK\_REALTIME now minus scan period**; each point's `time` progresses by `time_increment`. A wall clock can jump. Software synchronization and communication-delay estimates are not proof of exposure accuracy, PTP, PPS or external discipline. Preserve the chosen clock policy and relative point times for deskewing. `range_max:100` and 18-line aggregation are generic processing parameters, not a 100 m rated range or 18 optical channels.

The portal specifies serial **4 Mbaud, 8 data bits, no parity, 1 stop bit**. It warns that a floating host TX input can cause spurious control/error responses; use the matched converter rather than invent pull resistors or logic-voltage limits. If several L2 units are installed, the portal warns about duplicate default MAC addresses: inventory actual MAC/IP identities and use the approved configuration path deliberately before sharing a subnet. Never change all devices together as a discovery step. [Development and mode/protocol chapter](https://support.unitree.com/home/en/L2_SDK/L2_develope).

Standby is specified as <1 W with both motors, LED, IMU output and IMU thermostat disabled. A temporarily obstructed mechanism may auto-resume when the obstruction clears; it is not isolated. Normal-angle uses a six-segment ring, NEGA a three-segment ring and 2D a slow blink; L2 LED patterns are not configurable like L1's 45-byte command mask. A small directly overhead deficient angular region is described as a normal correction effect; distinguish that from a blocked window or failed scan. The optical density remains nonuniform. [Preparation](https://support.unitree.com/home/en/L2_SDK/L2_Overview_Use), [installation](https://support.unitree.com/home/en/L2_SDK/L2_Overview_install).

The four positioning slots can help register a bracket; their presence does not establish a measured repeatability tolerance. For mounting, use four M3 holes 6 mm deep and leave airflow; the body must not carry extra load. Any-orientation mounting still needs orientation-specific external water protection. Cleaning uses gentle clean-cloth wiping, with a little alcohol for remaining stains; avoid abrasion and additional window glass. Store dry, ventilated and dust-free at −20 to +60 °C, away from corrosive/flammable material, and secure cushioned transport against impact/vibration/friction. Inspect long-stored units before use. The FAQ's nominal 12 V/1 A statement must be read together with the specified 13 W warm-up peak; use the matched approved supply with adequate transient capacity, not an assumed universal 12 W ceiling.

### Original direct-reader checkpoint without explicit device writes <a href="#original-direct-reader-checkpoint-without-explicit-device-writes" id="original-direct-reader-checkpoint-without-explicit-device-writes"></a>

For an already identified, correctly powered L2 assembly in the intended Ethernet mode, the following original C++17 program replaces the official sample's start/mode/reset sequence with a short receive/parser loop. It makes **no explicit rotation, reset, mode, IP/MAC or clock-setting API call**. Initialization still uses the supplied opaque static library, so this is not a certification that its internals never transmit; use the earlier socket-only capture for a strictly passive network observation.

Save as `l2_receive_check.cpp` and build in the documented SDK environment using the repository's matching headers, architecture-specific static library and CMake/link requirements. This review does not establish an alternative ABI/library platform.

```cpp
#include <chrono>
#include <ctime>
#include <iostream>
#include <thread>
#include "unitree_lidar_sdk.h"

int main() {
  using namespace unilidar_sdk2;
  UnitreeLidarReader* reader = createUnitreeLidarReader();
  if (!reader) return 1;
  // Keep the already-observed endpoints; false requests device time.
  if (reader->initializeUDP(6101, "192.168.1.62", 6201,
                            "192.168.1.2", 18, false) != 0) {
    std::cerr << "Reader initialization failed\n";
    return 2;
  }
  const auto finish = std::chrono::steady_clock::now()
                    + std::chrono::seconds(8);
  unsigned clouds = 0, imus = 0;
  while (std::chrono::steady_clock::now() < finish) {
    const int kind = reader->runParse();
    if (kind == LIDAR_POINT_DATA_PACKET_TYPE) {
      PointCloudUnitree cloud;
      if (reader->getPointCloud(cloud)) {
        ++clouds;
        if (clouds == 1)
          std::cout << "cloud stamp " << cloud.stamp
                    << " points " << cloud.points.size()
                    << " rings " << cloud.ringNum << '\n';
      }
    } else if (kind == LIDAR_IMU_DATA_PACKET_TYPE) {
      LidarImuData imu;
      if (reader->getImuData(imu)) ++imus;
    }
    std::this_thread::sleep_for(std::chrono::milliseconds(1));
  }
  std::cout << "clouds " << clouds << " imu records " << imus << '\n';
  reader->clearBuffer();
  reader->closeUDP();
  return clouds ? 0 : 3;
}
```

**Expected result:** nonzero completed cloud count in the already-active 3D stream; IMU count depends on the actual mode. A zero count can mean standby, serial/2D mode, endpoint mismatch, unavailable calibration/library support or no data, rather than a reason to issue reset automatically. The sample intentionally does not start a standby sensor.

`PointCloudUnitree.stamp` is the cloud start time and each `PointUnitree.time` is a relative point time; `ring` and `ringNum` describe the SDK's assembled scan representation, not a claim of a fixed multibeam optical array. With host time, the public single-line converter sets cloud start to host time minus scan period; with device time it uses packet seconds+nanoseconds. `cloud_scan_num:18` controls aggregation of raw scan lines; it is not a device laser-channel count. Keep the selected clock, aggregation and ranges with each recording. `getVersionOfSDK/LidarFirmware/LidarHardware`, `getTimeDelay` (seconds) and `getDirtyPercentage` (removed dirty-point percentage) are read getters; check their Boolean availability result. [Reader API](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/include/unitree_lidar_sdk.h), [actual cloud structures and public conversion](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/include/unitree_lidar_utilities.h).

The protocol's **type100** is the user-command family. Public `USER_CMD_*` codes use **1 reset, 2 standby (value0 start/value1 standby), 3 version, 4 latency, 5 configuration reset, 6 configuration get, 7 auto-standby**; these are distinct from the separate legacy `CMD_*` namespace and not raw UDP commands to guess. The IMU structure contains four quaternion and three angular/three linear float values. Its header alone does not establish quaternion component order, timestamp synchronization quality or every physical scale; use the model-matched implementation/documentation before a fusion consumer. No SDK linking, binary execution or physical acquisition was performed for this example.

## Getting started <a href="#getting-started" id="getting-started"></a>

### Stationary first result <a href="#stationary-first-result" id="stationary-first-result"></a>

1. Confirm the received sensor is L2 and verify its actual package separately from the unresolved store listing. Use the manufacturer's matched 12 V supply, cable and adapter. Place it on a level stable surface with rotation/optics clear.
2. With power off, connect the supply and Ethernet branch. Set the dedicated host adapter to **192.168.1.2/24**, distinct from sensor `.62`. Leave the serial adapter unused for the first Ethernet path.
3. Energize the approved assembly. Allow self-heating to finish if applicable; record actual mode/status before trying a reset. Use the Windows 64-bit Unilidar 2 viewer, select Ethernet connection and verify the actual device/firmware.
4. Display a stationary scene and read status/version/configuration. Record observed standard versus negative-angle and 3D versus 2D modes. Inspect IMU only if already enabled; **do not select IMU Enable/SetMode/Restart during the observation checkpoint**. Keep the sensor stationary while assessing initial geometry.

**Expected result:** current cloud/status data from the identified L2 in its already active output mode; IMU records are conditional on the actual stored setting. A delayed cloud during self-heating or standby needs status diagnosis before any mode write. [Device manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf), [Unilidar 2 manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf).

### Original passive UDP counter <a href="#original-passive-udp-counter" id="original-passive-udp-counter"></a>

Close viewer/driver to avoid binding conflicts. This program listens only on the documented host endpoint for 8 seconds and sends nothing:

```python
import collections
import socket
import time

shapes = collections.Counter()
with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as sock:
    sock.bind(("192.168.1.2", 6201))
    sock.settimeout(0.2)
    end = time.monotonic() + 8
    while time.monotonic() < end:
        try:
            payload, peer = sock.recvfrom(65535)
        except socket.timeout:
            continue
        shapes[(peer[0], peer[1], len(payload))] += 1
for shape, count in shapes.most_common():
    print("source IP/port/payload bytes", shape, "packets", count)
if not shapes:
    raise SystemExit("No UDP: inspect actual mode, host destination, power and warm-up state")
```

**Expected result:** packets from the observed sensor, typically source port 6101, to host 6201. Counts are transport evidence, not decoded point validity. Do not use an arbitrary first byte as a protocol/model identifier.

### Build the documented SDK and ROS2 Foxy path <a href="#build-the-documented-sdk-and-ros2-foxy-path" id="build-the-documented-sdk-and-ros2-foxy-path"></a>

On the documented Ubuntu 20.04/Foxy/PCL 1.10 environment, with matching architecture library and build tools:

```bash
mkdir -p ~/l2_dev
cd ~/l2_dev
git clone https://github.com/unitreerobotics/unilidar_sdk2.git
cd unilidar_sdk2
git checkout 0e3c51f512e6b8ff60b8c32f160b412cb48445c2
cd unitree_lidar_sdk
mkdir -p build
cd build
cmake ..
make -j2
```

This builds samples without running them. Review `examples/example_lidar_udp.cpp` before deliberately running `../bin/example_lidar_udp`: the start/mode/reset actions described above affect the stationary sensor. Expected application output includes initialization/version reports and parsed cloud/IMU messages; those are manufacturer example expectations, not results obtained here.

For the repository's ROS2 workspace:

```bash
cd ~/l2_dev/unilidar_sdk2/unitree_lidar_ros2
source /opt/ros/foxy/setup.bash
colcon build
source install/setup.bash
ros2 launch unitree_lidar_ros2 launch.py
```

Inspect the actual launch's Ethernet addresses, work mode and timestamp policy before starting. In another sourced terminal, check `ros2 topic hz /unilidar/cloud` and `ros2 topic hz /unilidar/imu`. **Expected result:** cloud and IMU publications in their separate documented frames. `cloud_scan_num:18` groups vertical scans; it is not 18 physical channels. Host/system timestamps do not establish an externally disciplined sensor clock. [SDK ROS2 workflow](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/README.md).

### Engineering Setup Checklist <a href="#engineering-setup-checklist" id="engineering-setup-checklist"></a>

1. Read the L2 label and inventory its 12 V supply/converter, output cable and exact host-library architecture.
2. Start on a stationary mount with the optical mechanism clear; record the selected Ethernet/UART mode and factory endpoint settings.
3. Observe passive traffic before running SDK examples that rotate, configure and reset the sensor.
4. Verify cloud and IMU frame origins, timestamp source and the measured base transform, then save a repeatable capture.
5. Evaluate the supported ROS2 Foxy or ROS1 Noetic path before adapting another distribution. Keep work mode, SDK/firmware and processing parameters with recordings.

[Model-specific source](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf).

## Troubleshooting and FAQs <a href="#troubleshooting-and-faqs" id="troubleshooting-and-faqs"></a>

### FAQ <a href="#faq" id="faq"></a>

| Observation                        | Model-specific diagnosis                                                                                    |
| ---------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| No cloud after power-on            | Self-heating, standby/auto start setting, supply at 12 V and actual selected Ethernet/serial mode           |
| Serial port visible, no data       | 4,000,000 baud, matched converter, sensor TX to host RX, common reference and selected serial mode          |
| UDP counter zero                   | Host `.2`, sensor `.62`, host port 6201, actual stored settings, one client and scoped firewall rules       |
| SDK link/build failure             | Correct architecture static library, C++17, actual ABI and documented ROS/PCL environment                   |
| Missing lower 6°                   | Standard 90° versus negative-angle 96° mode; not necessarily data loss                                      |
| Poor SLAM geometry                 | Timing, IMU translation, axis convention, non-repetitive scan motion and downstream Point-LIO configuration |
| Rotation resumes after obstruction | Documented interference recovery; power off before clearing obstruction                                     |

**Can I power it through the 4-pin plug?** No. It is a data-only UART branch; power uses the separate DC branch.

**Is 2D mode a 360° scanner?** The manual specifies 180° or 192° in 2D mode;360° is the circumferential 3D scan envelope. The pinned SDK 2D helper emits an x=0 Y–Z-plane cloud, so an X–Y planar consumer additionally needs a defined mounting/frame conversion; selecting 2D does not supply that conversion.

Preserve configuration/version records before changing interface or IP. The SDK provides separate `set_to_serial_mode`,`set_to_udp_mode` and `set_ip_address` examples; they write settings and can make the old path disappear. Do not run them as discovery utilities. Clean optics with the model's documented procedure, avoid abrasion and protect exposed interfaces from water. Firmware/recovery requires the exact L2 package and manufacturer instructions.

### Best Practices and Limitations <a href="#best-practices-and-limitations" id="best-practices-and-limitations"></a>

* **Do not treat 4D LiDAR as a safety-rated scanner.** It can support navigation and obstacle avoidance, but safety functions require system-level safety design and compliance validation.
* **Watch motion distortion.** The L2 is well suited to low-speed mobile robots; fast rotations, aggressive vibration, and high-speed vehicles need extra validation.
* **Validate material edge cases.** Test glass, glossy black objects, thin table legs, reflective metal, dark fabric, strong sunlight, fog, dust, and low obstacles.
* **Keep the window clean.** Optical contamination directly affects point cloud quality.
* **Plan for heat.** Add airflow and avoid enclosing the sensor in a sealed hot compartment.
* **Synchronize correctly.** LiDAR-inertial odometry quality depends on accurate timing, IMU settings, and extrinsic calibration.

[Model-specific source](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf).

## Downloads and technical documents <a href="#downloads-and-technical-documents" id="downloads-and-technical-documents"></a>

### Official Downloads and Resources <a href="#official-downloads-and-resources" id="official-downloads-and-resources"></a>

| Resource                                                                                                                  | Purpose                                                                                      |
| ------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| [L2 device manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf)               | 18-page manufacturer manual, power/wiring, FOV modes, mechanical drawing and troubleshooting |
| [Unilidar 2 viewer manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf)                    | Windows 64-bit connection, device controls and display                                       |
| [L2 downloads](https://www.unitree.com/mobile/download/L2/)                                                               | Viewer, SDK zip, CAD and recorded cloud data                                                 |
| [L2 STEP model](https://oss-global-cdn.unitree.com/static/L2%203D%20Model.STEP)                                           | Mechanical/frame integration                                                                 |
| [Unilidar SDK2](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/README.md) | Pinned C++/ROS1/ROS2 sources and protocol headers                                            |
| [Official Point-LIO adaptation](https://github.com/unitreerobotics/point_lio_unilidar)                                    | Separate LiDAR/IMU algorithm workflow                                                        |

The existing native images/anchors and historical store/reference links remain retained. No alternate store URL or product variant is asserted while the current SKU mapping remains unresolved.

## References and validation <a href="#references-and-validation" id="references-and-validation"></a>

### Source Notes <a href="#source-notes" id="source-notes"></a>

Reviewed 24 November 2026: full L2 device/viewer manuals, current official product/downloads and actual SDK2 API, sample mode/reset behavior, ROS2 launch and documented Foxy baseline. The current complete catalog contains no exact `Unitree-L24DLiDAR`. Earlier verification recorded a historical-page 404; the latest separate product-JSON request was 429, not evidence of a new 404 or a successful live store match. The historical Top200 SKU/store gap remains named. Publication may retain this as a manufacturer-reference update under the authorized unlisted-model policy; it must not relabel a different package as L2.

**Compilation, viewer/ROS/sample execution, live UDP counter execution, mode/IP/firmware writes and physical tests: not run.** The original passive counter receives only, and is checked offline with fake sockets. No vendor code was imported or executed. The unresolved retail match remains explicit rather than marking that claim verified. Actual accessible official portal article assets were read for this update; older direct frontend HTTP failures do not describe current article-source access.

* [Unitree L2 official User Manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf) — 2024 manual 18 pages.
* [Unilidar 2 official viewer manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf) — 2024 manual 11 pages.
* [Unitree L2 SDK2 documented workflows](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/README.md) — commit 0e3c51f512e6b8ff60b8c32f160b412cb48445c2.
* [UDP sample start/mode/reset side effects](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/examples/example_lidar_udp.cpp) — commit 0e3c51f512e6b8ff60b8c32f160b412cb48445c2.
* [L2 ROS2 exact launch](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_ros2/src/unitree_lidar_ros2/launch/launch.py) — commit 0e3c51f512e6b8ff60b8c32f160b412cb48445c2.
* [Current L2 official product](https://www.unitree.com/L2/) — 24 Nov 2026.
* [Current L2 official downloads](https://www.unitree.com/mobile/download/L2/) — 24 Nov 2026.
* [Exact L2 store mapping gap](https://openelab.io/products/unitree-l2-4dlidar-navigation-obstacle-avoidance-slam-360-depth-scan) — current catalog has no match; prior 404 and latest 429 are separate observations.

### Additional established references <a href="#additional-established-references" id="additional-established-references"></a>

These historical resource links are retained for continuity. Links without a source-read entry in this update are listed references, not a claim of current binary compatibility, successful download, or execution.

* [Unilidar 2 V 1.21 Windows](https://oss-global-cdn.unitree.com/static/Unilidar_2_V1.21.exe)
* [unilidar\_sdk 2-2.0.4.zip](https://oss-global-cdn.unitree.com/static/unilidar_sdk2-2.0.4.zip)
* [point\_lio\_unilidar-2.0.2.zip](https://oss-global-cdn.unitree.com/static/point_lio_unilidar-2.0.2.zip)
* [L2 Indoor Point Cloud Data.bag](https://oss-global-cdn.unitree.com/static/L2%20Indoor%20Point%20Cloud%20Data.bag)
* [L2 Park Point Cloud Data.bag](https://oss-global-cdn.unitree.com/static/L2%20Park%20Point%20Cloud%20Data.bag)
* [point\_lio\_ros 2 with Unitree L1/L2 support](https://github.com/dfloreaa/point_lio_ros2)
* [unilidar\_fastlio\_ros 2](https://github.com/newkillerwhale/unilidar_fastlio_ros2)
* [Unitree Go 2 L2 mapping reference](https://www.unitree.com/go2/)
* [point\_lio\_ros 2](https://github.com/dfloreaa/point_lio_ros2)

### Complete official article coverage <a href="#complete-official-article-coverage" id="complete-official-article-coverage"></a>

Each row records substantive functional coverage, not a claim that a link alone was reviewed. Full source heading/line ranges and hashes are retained with the draft. Empty category nodes are explicitly distinguished from technical content.

| Actual official article                                                                | Source sections read                                                                                                                                                                                                                                                                                                                                                            | Original engineering coverage / boundary                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| -------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [About L2](https://support.unitree.com/home/en/L2_SDK/L2_introduce)                    | Introduction; Working principle; Component Description; Storage, transportation and maintenance; Storage; Transportation; Maintenance; SDK and related materials download address                                                                                                                                                                                               | L2 combines rotating-mirror 3D position and grayscale with an IMU, selected Ethernet/UART output and optional 2D scan. Component/default descriptions conflict with later preparation: NEGA and IMU defaults need readback. Dry ventilated storage, impact-protected transport and gentle optical maintenance remain distinct from operation. Raw data still needs application processing/storage.                                                                                                                                                                                                                                                                                                               |
| [Product overview](https://support.unitree.com/home/en/L2_SDK/L2_Overview)             | (empty category)                                                                                                                                                                                                                                                                                                                                                                | Empty category node: actual200 response has zero functional content. Child chapters, not this node, carry the technical evidence.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| [Parameter specification](https://support.unitree.com/home/en/L2_SDK/L2_Overview_DATA) | Unitree 4D LiDAR                                                                                                                                                                                                                                                                                                                                                                | Separate 360×90°/96° 3D from 180°/192° 2D. Qualified ranges are 30/15 m at 90/10% reflectivity; 0.05 m accuracy is excluded. 128,000 samples vs64,000 effective points, 5.55/216 Hz scans and 500 Hz IMU are different quantities. Plan matched 12 V supply for 13 W warm-up as well as 10 W typical, and keep case-bottom≤85 °C within ambient−10..50 °C.                                                                                                                                                                                                                                                                                                                                                       |
| [Interface definition](https://support.unitree.com/home/en/L2_SDK/L2_Overview_Link)    | Interface definition; One outlet with three cables                                                                                                                                                                                                                                                                                                                              | Three branches are separate DC supply, RJ45 Ethernet and data-only GH1.25 UART. Serial pin1 unused, pin2 ground pink, pin3 sensor RX white, pin4 TX brown; RJ45 1/2 transmit and3/6 receive. Prose/table barrel dimensions disagree; matched approved adapter takes priority over guessed connector fit.                                                                                                                                                                                                                                                                                                                                                                                                         |
| [L2 installation](https://support.unitree.com/home/en/L2_SDK/L2_Overview_install)      | L2 Installation; Installation Dimensions; Effective field of view (FOV) range; Installation precautions                                                                                                                                                                                                                                                                         | Four M3 holes 6 mm deep support the sensor only; retain cooling and clear optics, including orientation-specific external water protection. Expanded lower six degrees have shorter far range. Density is nonuniform and a small overhead correction gap is documented. An added transparent pane still changes optical performance.                                                                                                                                                                                                                                                                                                                                                                             |
| [Preparation before use](https://support.unitree.com/home/en/L2_SDK/L2_Overview_Use)   | Preparation before use; UART TTL connection; ENET UDP connection; Coordinate system; Point cloud data; Working status and working mode; Working status description; Working mode description; LED mode; Unilidar SDK 2; Unilidar 2                                                                                                                                              | UART requires its matched converter and separate supply; Ethernet uses .62:6101 to host .2:6201 with unique addresses. Bottom-center cloud and parallel-axis IMU frames require explicit extrinsics. One cloud transport is selected. Standby disables motors/IMU/thermostat; obstruction can auto-resume. 2D/NEGA/start behavior is stored configuration; ring patterns identify modes but are not L1-style programmable LEDs.                                                                                                                                                                                                                                                                                  |
| [Use of L2](https://support.unitree.com/home/en/L2_SDK/L2_Use)                         | (empty category)                                                                                                                                                                                                                                                                                                                                                                | Empty category node: actual200 response has zero functional content. Child chapters, not this node, carry the technical evidence.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| [L2 Development Guide](https://support.unitree.com/home/en/L2_SDK/L2_develope)         | L2 Development Guide; Preface; Glossary; Overview; Development method; Mode Introduction; Communication protocol details; Data packet protocol format; LidarPointDataPacket; Lidar2DPointDataPacket; LidarImuDataPacket; LidarAckDataPacket; LidarVersionDataPacket; LidarWorkModeConfigPacket; LidarIpAddressConfigPacket; LidarMacAddressConfigPacket; LidarUserCtrlCmdPacket | DataInfo, InsideState and calibration describe packet metadata, status and optical corrections. Choose SDK or a validated complete raw parser, not a struct-comment cast. Types100–109 cover user command, ACK,3D,2D,IMU,version,time,mode,IP,MAC; whole-length/CRC/tail checks and point-count bounds are mandatory. The pinned 2D helper uses x=0, y=cos(alpha)\*range, z=sin(alpha)\*range+a\_axis\_dist: a Y–Z-plane cloud requiring explicit mounting/frame conversion for an X–Y planar consumer. Summary/prose/header size comments conflict: use actual pinned field layouts and firmware validation. Mode bits and ACK status govern state writes; software clock sync is not external time discipline. |
| [Unilidar 2](https://support.unitree.com/home/en/L2_SDK/L2_unilidar2)                  | Unilidar 2 PC User Manual; Unilidar 2 Introduction; Get Started; Interface Introduction; Point cloud display interface description; Device management interface description; Output mode setting; Lidar Info module; Work Mode Module; Config Setting module; Get version information; IMU data                                                                                 | Windows64 Viewer uses the actual local UDP adapter or matched converter COM. GetVersion and Synchronous provide identity/readback. Persistence and camera controls differ from SetMode/Restart output settings. IMU Enable can be a device write. Network Change/Restart and network-only factory defaults need recorded endpoints; serial can recover unknown IP without assuming serial cloud is already selected. Retain raw diagnostic values where RPM/temperature unit labels conflict.                                                                                                                                                                                                                    |
| [Unilidar SDK2](https://support.unitree.com/home/en/L2_SDK/L2_Use_unilidarsdk)         | Unilidar SDK2; Introduction; Coordinate system definition; How to use C++ SDK; Compile; Configure working mode; Run using the network port; Run using the serial port                                                                                                                                                                                                           | Pinned SDK2 uses its own namespace, calibration-aware cloud and IMU getters and separate serial/UDP initialization. Cloud origin and exact IMU offset are defined; 18 scans aggregate lines. Sample mode0 and serialmode8 are values, not universal factory guarantees. Official samples configure/start/reset; source-inspect writes before deliberate execution and verify architecture/ABI before a build.                                                                                                                                                                                                                                                                                                    |
| [Unilidar SDK2 Ros](https://support.unitree.com/home/en/L2_SDK/L2_Use_unilidar_ros)    | Unilidar SDK2 ROS; Dependencies; Configuration; Compile; Run                                                                                                                                                                                                                                                                                                                    | Noetic/PCL1.10/Ubuntu20.04 is a documented reference. Configure actual source/destination endpoints or serial path, work mode and clock policy; catkin-build the actual workspace and source before run.launch. Two topics/frames remain separate and launching can configure the device.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| [Unilidar SDK2 Ros2](https://support.unitree.com/home/en/L2_SDK/L2_Use_unilidar_ros2)  | Unildar SDK2 ROS2; Dependencies; Configuration; Compile; Run                                                                                                                                                                                                                                                                                                                    | Foxy/PCL1.10/Ubuntu20.04 reference uses actual colcon workspace and launch.py. Inspect initialize\_type2, work\_mode0, system timestamps, filters, scan aggregation and cloud/IMU frames; RViz and node startup are active software, not passive transport observation.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| [FAQ](https://support.unitree.com/home/en/L2_SDK/L2_FAQ)                               | Troubleshooting                                                                                                                                                                                                                                                                                                                                                                 | Diagnose selected transport, separate power, exact endpoint/port ownership and host network before reset. Serial control can recover an unknown address through approved configuration/save/restart. A 12 V/1 A nominal FAQ line must be reconciled with13 W warm-up. Mechanical interference auto-recovery requires power isolation before intervention.                                                                                                                                                                                                                                                                                                                                                        |

### Complete accessible PDF functional index <a href="#complete-accessible-pdf-functional-index" id="complete-accessible-pdf-functional-index"></a>

PDF page numbers below count from the cover; printed numbering may differ. These are original functional summaries, not a reproduced transcript or manual bundle.

| Official document                                                                                                    | PDF pages | Functional coverage                                                                                                                                                           |
| -------------------------------------------------------------------------------------------------------------------- | --------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=1)  | 1         | Cover identifies L2 user manualv1.1,October2024.                                                                                                                              |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=2)  | 2         | Download page links manual,Viewer and SDK; the old generic SDK repository link must not replace actual L2 SDK2 identity.                                                      |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=3)  | 3         | Contents locates product,interface,installation,use,maintenance,troubleshooting and qualified specifications.                                                                 |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=4)  | 4         | Introduction establishes rates/FOV and factoryNEGA/IMU-disabled defaults, conflicting with later normal-angle section; original page visually checked.                        |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=5)  | 5         | Time-of-flight laser/mirror/two-motor principle and separate power with Ethernet or matched serial adapter; described provided kit is not a current retail packing guarantee. |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=6)  | 6         | Component drawing identifies optical window,outlet,four positioning slots and fourM3 mounting holes; slots improve bracket registration,not a verified tolerance guarantee.   |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=7)  | 7         | Original cable table visually confirms separate supply,RJ45 and data-only UART; barrel3.4/3.5 discrepancy retained.                                                           |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=8)  | 8         | 360×90°/96° FOV; expanded lower6° loses far range; field density is nonuniform.                                                                                               |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=9)  | 9         | Optics/airflow/no added glass,any-orientation mount,body self-load only and water protection requirements.                                                                    |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=10) | 10        | Original fourM3 depth6 mm mechanical drawing and orientation-specific protection visually checked.                                                                            |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=11) | 11        | Matched serial adapter or Ethernet topology; exact.62:6101 to.2:6201 defaults and stable rubber-pad setup.                                                                    |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=12) | 12        | Bottom-center cloud axes and parallel IMU axes; one cloud transport,raw range/angle/intensity/IMU/status roles.                                                               |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=13) | 13        | Standby stops motors/IMU/thermostat;interference auto-resume;3D/2D/NEGA/self-start settings conflict with earlier defaults.                                                   |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=14) | 14        | Nonconfigurable LED state patterns,Windows64 Viewer and SDK2 parsing/configuration roles.                                                                                     |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=15) | 15        | Dry ventilated storage,cushioned secure transport,regular inspection and gentle cloth/alcohol optical maintenance.                                                            |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=16) | 16        | Transport/power/endpoint/port diagnostics and unknown-IP serial recovery;12 V1 A FAQ read with13 W warm-up demand.                                                            |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=17) | 17        | Qualified optical/range/point/scan/IMU/interface rates and environmental values;2D angle differs from3D circumference.                                                        |
| [unitree-l2-manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf#page=18) | 18        | Power/body/IP/temperature table and footnotes;self-heating delays cloud until ready,13 W peak,case-bottom≤85 °C.                                                              |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=1)           | 1         | Cover identifies Unilidar2 Viewer v1.0,November2024.                                                                                                                          |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=2)           | 2         | Contents separates connection,display,modes,status,version and IMU.                                                                                                           |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=3)           | 3         | Windows64 graphics/serial converter plus separate12 V supply topology.                                                                                                        |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=4)           | 4         | Ethernet endpoints and stable rubber-pad setup;management and point display are separate panes.                                                                               |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=5)           | 5         | Mouse/arrow/zoom controls and IMU-follow behavior are display functions.                                                                                                      |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=6)           | 6         | Device-management figure organizes connection/status/mode/network controls.                                                                                                   |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=7)           | 7         | UDP/serial output selection needs SetMode,successful response and Restart;actual host adapter/COM selection.                                                                  |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=8)           | 8         | Unknown-IP serial configuration and raw diagnostic units;NEGA/IMU-disable defaults conflict with SDKmode0.                                                                    |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=9)           | 9         | Self/cmd-start,gray,normal/standby,SetMode/Restart,Synchronous and network Change/default controls have different effects.                                                    |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=10)          | 10        | GetVersion verifies identity;IMU quaternion/acceleration/gyro labels alone do not settle ordering/units.                                                                      |
| [unitree-viewer-manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf#page=11)          | 11        | Update/source notices point to official downloads;no firmware image/recovery guarantee.                                                                                       |

**Related documentation:** [Unitree model and development directory](./).
