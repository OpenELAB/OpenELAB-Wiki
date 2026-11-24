---
description: >-
  Connect Unitree L2 with separate 12 V power and data-only UART, understand
  90°/96° scan modes, and use its exact SDK2/Foxy workflow while reconciling the
  current store SKU.
---

# Unitree L2 4D LiDAR Engineering Guide

{% hint style="info" %}
[**Historical OpenELAB listing — current listing unverified/404**](https://openelab.io/products/unitree-l2-4dlidar-navigation-obstacle-avoidance-slam-360-depth-scan)

**Model / option:** Assigned historical L2 package; current store match unresolved · **SKU:** `Unitree-L24DLiDAR`
{% endhint %}

## Product overview

### Unitree L2 4D LiDAR Engineering Guide <a href="#unitree-l2-4d-lidar-engineering-guide" id="unitree-l2-4d-lidar-engineering-guide"></a>

**Unitree L2 is a compact non-repetitive 3D LiDAR with an integrated IMU, Ethernet UDP and selectable TTL UART.** Its standard 3D field is 360° × 90°; negative-angle mode extends it to 360° × 96°. “4D” denotes 3D position plus grayscale, not a direct Doppler-velocity channel. [Official L2 manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf), [current product](https://www.unitree.com/L2/).

This guide retains the established OpenELAB URL and assigned `Unitree-L24DLiDAR` reference. That SKU is absent from the current supplied catalog, and the established store URL returned 404 during direct verification, although an older indexed copy is readable. Confirm the current exact listing/package before procurement; no substitute store handle or variant ID is invented.

### Quick Summary <a href="#quick-summary" id="quick-summary"></a>

L2 supplies non-repetitive depth plus reflectivity and an IMU through one selected output path, Ethernet UDP or TTL UART. Default mode 0 is standard 3D with IMU enabled, Ethernet and automatic startup; serial example mode 8 changes the interface bit. The current exact OpenELAB listing/package remains unresolved, so the historical URL is preserved without inventing an in-stock or included-accessory claim.

[Model-specific source](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf).

## Applications

L2 is useful for compact robot scene capture, LiDAR/IMU odometry and mobile mapping research. Its two-axis rotating mirror produces nonuniform point density and acquisition timing. A rendered dense wall accumulated over time is different from an instantaneous uniformly sampled frame.

Start with a fixed sensor on its supplied rubber pad or a suitable mount. Verify cloud and IMU streams before adding Point-LIO. The official Point-LIO adaptation can use L2 plus its integrated IMU, but that does not guarantee drift-free maps or external position truth. Preserve scan timing, frame transforms and dataset configuration when evaluating motion. [SDK2](https://github.com/unitreerobotics/unilidar_sdk2), [official Point-LIO adaptation](https://github.com/unitreerobotics/point_lio_unilidar).

### Project References and Application Ideas <a href="#project-references-and-application-ideas" id="project-references-and-application-ideas"></a>

* [Unitree Unilidar SDK2](https://github.com/unitreerobotics/unilidar_sdk2): official SDK with C++ interfaces plus ROS and ROS2 packages for parsing and publishing Unitree L2 point cloud and IMU data.
* [Unitree point\_lio\_unilidar](https://github.com/unitreerobotics/point_lio_unilidar): official adaptation of Point-LIO for Unitree L1 and L2, with L2 video demos and sample data workflow.
* [point\_lio\_ros2 with Unitree L1/L2 support](https://github.com/dfloreaa/point_lio_ros2): community ROS2 port for engineers building ROS2-first LiDAR-inertial odometry stacks.
* [unilidar\_fastlio\_ros2](https://github.com/newkillerwhale/unilidar_fastlio_ros2): community ROS2 FAST-LIO-style integration for Unitree LiDAR.
* [Unitree Go2 L2 application reference](https://www.unitree.com/go2/): the current manufacturer page explicitly names L2 with 360° × 96° coverage and a 0.05 m minimum detection distance. This is a manufacturer platform description; inspect the actual delivered robot before using it as a bill of materials.
* Application ideas: indoor AMR localization, warehouse obstacle perception, quadruped mapping, service robot navigation, autonomous cleaning robot perception, educational SLAM labs, and low-speed outdoor survey robots.

[Model-specific source](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf).

## Specifications

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

## Hardware and connections

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

## Software and development resources

### SDK/API and mode boundaries <a href="#software-workflow" id="software-workflow"></a>

Use **unitreerobotics/unilidar\_sdk2**, not the L1 SDK. The reviewed repository's validated ROS environments are Ubuntu 20.04/ROS Noetic/PCL 1.10 and Ubuntu 20.04/ROS2 Foxy/PCL 1.10. Its ROS2 package exists, but a Humble/Jazzy build is not established by those examples. CMake uses C++17 and architecture-specific `libunilidar_sdk2.a`; confirm the provided library matches host architecture/ABI. [README/CMake](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/README.md).

| Mode bit | 0                   | 1                           |
| -------- | ------------------- | --------------------------- |
| 0        | Standard FOV        | Expanded/negative-angle FOV |
| 1        | 3D                  | 2D                          |
| 2        | IMU enabled         | IMU disabled                |
| 3        | Ethernet            | Serial                      |
| 4        | Power-on auto start | Wait for start command      |

Default work mode 0 selects standard 3D, IMU enabled, Ethernet and auto start. Serial example mode 8 changes only the interface bit. These are sensor-control settings; record existing values before writing. [Actual SDK mode table](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/README.md).

The factory UDP endpoints are sensor **192.168.1.62: 6101**, host **192.168.1.2: 6201**. Source and destination ports are not interchangeable. The actual ROS2 launch sets `initialize_type:2`,`work_mode:0`,`use_system_timestamp:true`,`cloud_scan_num:18`, cloud topic `unilidar/cloud`, IMU topic `unilidar/imu` and separate frames `unilidar_lidar`/`unilidar_imu`. [Actual launch](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_ros2/src/unitree_lidar_ros2/launch/launch.py).

**The official UDP sample is not read-only:** it starts rotation, sets work mode 0 and resets the LiDAR before reading. Do not present it as a passive diagnostic. The ROS node also configures modes; use it only after the stationary identification/capture checkpoint.

### L2 reader API, packet families and status outputs

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

### Viewer controls, versioned defaults and unknown-IP recovery

The **Unilidar2 Viewer v1.0 (November2024)** is a Windows64-bit tool distinct from the SDK mode table. Select the actual local adapter for **Open UDP Port**, or the enumerated supplied converter's COM port for **Open Serial Port**. Network and serial are alternative cloud-output modes, not simultaneous streams. Read **GetVersion** and **Synchronous** (parameter readback) before changing anything.

| Viewer control           | Behavior and verification                                                                                                                  |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| Point cloud count        | Display accumulation **500 ms / 1 / 2 / 4 s**; a longer display is not a higher sensor frame rate                                          |
| Normal / NEGA            | Standard versus expanded negative-angle FOV; expanded angles have reduced far-range capability                                             |
| 3D/2D                    | Measurement mode; match packet family/consumer                                                                                             |
| IMU Display Enable       | Enables attitude-following display; the view can no longer be dragged in the same way                                                      |
| Gray Enable              | Grayscale/intensity output setting, not a new RGB camera stream                                                                            |
| SELF START / CMD START   | Automatic acquisition after power or wait-in-standby for an explicit acquisition command                                                   |
| Normal / Standby         | Immediate acquisition-state controls; do not use a reset as a discovery query                                                              |
| SetMode / Restart        | Submit mode changes, require successful response, then restart for documented settings to take effect                                      |
| Config Setting / Change  | Separate sensor IP/port/gateway/mask from receiving-host IP/port; submit Change, require success and restart                               |
| Restore Factory Defaults | The manual describes restoring **network/IP parameters** to `.62:6101` and target `.2:6201`; do not claim a full optical calibration reset |

The old Viewer manual defaults to **NEGA, IMU display disabled, 3D, Ethernet, self-start and grayscale on**. The pinned SDK sample instead chooses **mode0: normal FOV, IMU enabled, 3D/Ethernet/self-start**. Those are version/workflow differences, not one combined factory guarantee. Read the delivered device's configuration and keep its firmware/Viewer versions with the record.

For an unknown IP, inspect the isolated network passively first. The manufacturer Viewer describes recovery through its **supplied serial converter**: open the supported serial connection, read current parameters, enter the intended network values in **Config Setting**, choose **Change**, confirm success and **Restart**, then reconnect at the recorded new address and reread version/parameters. Opening serial control does not imply that an Ethernet-mode sensor already streams cloud over serial. Use SetMode only when intentionally changing the output transport. The exact store/harness gap above remains unresolved, so this is a manufacturer-supported reference procedure for an already identified complete L2 assembly, not a guessed wiring instruction. [Official Viewer manual](https://www.unitree.com/download).

Viewer **Lidar Info** shows `dirty_index`, `packet_lost_up/down`, motor fields and APD/laser/IMU values. The text labels `imu_temperature` in volts and motor `*_rotation_period` fields in RPM despite the SDK calling them periods. Treat those conflicting labels as unverified scale/unit descriptions; retain raw values and trend against an actual manufacturer definition, rather than convert them to a fabricated absolute temperature or RPM. APD/laser voltage fields and the cleanliness/loss trends remain useful diagnostic observations. The IMU window exposes quaternion Q1–Q4 and XYZ acceleration/gyro; do not infer quaternion component order or physical units from window labels alone. [Viewer v1.0 status/control reference](https://www.unitree.com/download), [pinned raw state structures](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/include/unitree_lidar_protocol.h).

### Original direct-reader checkpoint without explicit device writes

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

## Getting started

### Stationary first result

1. Confirm the received sensor is L2 and verify its actual package separately from the unresolved store listing. Use the manufacturer's matched 12 V supply, cable and adapter. Place it on a level stable surface with rotation/optics clear.
2. With power off, connect the supply and Ethernet branch. Set the dedicated host adapter to **192.168.1.2/24**, distinct from sensor `.62`. Leave the serial adapter unused for the first Ethernet path.
3. Energize the approved assembly. Allow self-heating to finish if applicable; record actual mode/status before trying a reset. Use the Windows 64-bit Unilidar 2 viewer, select Ethernet connection and verify the actual device/firmware.
4. Display a stationary scene and enable IMU display. Record observed standard versus negative-angle and 3D versus 2D modes. Keep the sensor stationary while assessing initial geometry.

**Expected result:** current cloud and IMU/status data from the identified L2. A delayed cloud during self-heating or standby needs status diagnosis before any mode write. [Device manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf), [Unilidar 2 manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf).

### Original passive UDP counter

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

### Build the documented SDK and ROS2 Foxy path

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

## Troubleshooting and FAQs

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

**Is 2D mode a 360° scanner?** The manual specifies 180° or 192° in 2D mode;360° is the circumferential 3D scan envelope.

Preserve configuration/version records before changing interface or IP. The SDK provides separate `set_to_serial_mode`,`set_to_udp_mode` and `set_ip_address` examples; they write settings and can make the old path disappear. Do not run them as discovery utilities. Clean optics with the model's documented procedure, avoid abrasion and protect exposed interfaces from water. Firmware/recovery requires the exact L2 package and manufacturer instructions.

### Best Practices and Limitations <a href="#best-practices-and-limitations" id="best-practices-and-limitations"></a>

* **Do not treat 4D LiDAR as a safety-rated scanner.** It can support navigation and obstacle avoidance, but safety functions require system-level safety design and compliance validation.
* **Watch motion distortion.** The L2 is well suited to low-speed mobile robots; fast rotations, aggressive vibration, and high-speed vehicles need extra validation.
* **Validate material edge cases.** Test glass, glossy black objects, thin table legs, reflective metal, dark fabric, strong sunlight, fog, dust, and low obstacles.
* **Keep the window clean.** Optical contamination directly affects point cloud quality.
* **Plan for heat.** Add airflow and avoid enclosing the sensor in a sealed hot compartment.
* **Synchronize correctly.** LiDAR-inertial odometry quality depends on accurate timing, IMU settings, and extrinsic calibration.

[Model-specific source](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf).

## Downloads and technical documents

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

## References and validation

### Source Notes <a href="#source-notes" id="source-notes"></a>

Reviewed 24 November 2026: full L2 device/viewer manuals, current official product/downloads and actual SDK2 API, sample mode/reset behavior, ROS2 launch and documented Foxy baseline. The current catalog search found no exact `Unitree-L24DLiDAR`; the existing OpenELAB product URL returned 404 through direct web verification, while an older indexed copy was readable. This is the remaining publication blocker.

**Compilation, viewer/ROS/sample execution, UDP counter execution, mode/IP/firmware writes and physical tests: not run.** The original passive counter is syntax checked. Structural checking correctly flags the unresolved store match; it is retained as a bounded draft rather than marking that claim verified.

* [Unitree L2 official User Manual](https://oss-global-cdn.unitree.com/static/Unitree%204D%20LiDAR%20L2%20User%20Manual.pdf) — 2024 manual 18 pages.
* [Unilidar 2 official viewer manual](https://oss-global-cdn.unitree.com/static/Unilidar%202%20User%20Manual.pdf) — 2024 manual 11 pages.
* [Unitree L2 SDK2 documented workflows](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/README.md) — commit 0e3c51f512e6b8ff60b8c32f160b412cb48445c2.
* [UDP sample start/mode/reset side effects](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_sdk/examples/example_lidar_udp.cpp) — commit 0e3c51f512e6b8ff60b8c32f160b412cb48445c2.
* [L2 ROS2 exact launch](https://github.com/unitreerobotics/unilidar_sdk2/blob/0e3c51f512e6b8ff60b8c32f160b412cb48445c2/unitree_lidar_ros2/src/unitree_lidar_ros2/launch/launch.py) — commit 0e3c51f512e6b8ff60b8c32f160b412cb48445c2.
* [Current L2 official product](https://www.unitree.com/L2/) — 24 Nov 2026.
* [Current L2 official downloads](https://www.unitree.com/mobile/download/L2/) — 24 Nov 2026.
* [Exact L2 store mapping gap](https://openelab.io/products/unitree-l2-4dlidar-navigation-obstacle-avoidance-slam-360-depth-scan) — catalog 23 Nov/direct web 40424 Nov.

### Additional established references

* [Unilidar 2 V 1.21 Windows](https://oss-global-cdn.unitree.com/static/Unilidar_2_V1.21.exe)
* [unilidar\_sdk 2-2.0.4.zip](https://oss-global-cdn.unitree.com/static/unilidar_sdk2-2.0.4.zip)
* [point\_lio\_unilidar-2.0.2.zip](https://oss-global-cdn.unitree.com/static/point_lio_unilidar-2.0.2.zip)
* [L2 Indoor Point Cloud Data.bag](https://oss-global-cdn.unitree.com/static/L2%20Indoor%20Point%20Cloud%20Data.bag)
* [L2 Park Point Cloud Data.bag](https://oss-global-cdn.unitree.com/static/L2%20Park%20Point%20Cloud%20Data.bag)
* [point\_lio\_ros 2 with Unitree L1/L2 support](https://github.com/dfloreaa/point_lio_ros2)
* [unilidar\_fastlio\_ros 2](https://github.com/newkillerwhale/unilidar_fastlio_ros2)
* [Unitree Go 2 L2 mapping reference](https://www.unitree.com/go2/)
* [point\_lio\_ros 2](https://github.com/dfloreaa/point_lio_ros2)
