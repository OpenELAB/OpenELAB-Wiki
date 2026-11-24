---
description: >-
  Connect D800/STL-27L with 5 V power and 921600-baud UART, verify CRC-valid
  planar data, and publish the exact STL27L ROS2 scan with a measured robot
  transform.
---

# LDROBOT D800 and STL-27L Engineering Guide

{% hint style="info" %}
[**View LDROBOT D800 LiDAR Developer Kit and STL-27L 25 m DTOF Sensor on OpenELAB**](https://openelab.io/products/ldrobot-d800-dtof-lidar-kit?variant=47176990654662)

**Model / option:** LDROBOT D800 Kit · **SKU:** `LDROBOT-D800`
{% endhint %}

## Product overview

### Product and scope <a href="#product-and-scope" id="product-and-scope"></a>

**LDROBOT D800 is a development kit built around the STL-27L 360° planar DTOF LiDAR.** The assigned `LDROBOT-D800` kit includes the STL-27L sensor, USB adapter board, USB cable and sensor cable. The `LDROBOT-STL-27L` option is the sensor without those kit accessories. This guide covers the D800 row while keeping that distinction explicit. [Exact kit/sensor options](https://openelab.io/products/ldrobot-d800-dtof-lidar-kit).

The sensor streams one-way UART at **921600 baud, 8N1** and needs **5 V nominal power within 4.5–5.5 V**. Its native scan is a 2D plane, not a 3D height cloud. Use the actual STL27L launch in the manufacturer's `ldlidar_stl_ros2` repository; LD06/LD19 examples have different serial settings. [Manufacturer development manual](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf), [actual driver](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/README.md).

## Applications

D800 supports planar mapping, scan matching and obstacle-awareness research where a 25 m reflectivity-qualified range and fine angular sampling are useful. Mount so the scan plane intersects the intended obstacles and remains clear of the chassis. A single plane can miss an overhang or a low obstacle outside that plane.

The sensor's 21600 measurements/s at 10 Hz yield about 2160 samples per revolution, consistent with roughly 0.167° angular sampling. That calculation does not establish a minimum detectable object size or a 25 m range for every surface. The datasheet qualifies 25 m at 80% reflectivity and 10 m at 4% reflectivity. Its glass-wall detection description is limited to near-normal incidence (about±5°); do not make glass detection a universal navigation assumption. [Manufacturer datasheet](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Datasheet.pdf).

## Specifications

### Hardware and technical documents <a href="#hardware-and-technical-documents" id="hardware-and-technical-documents"></a>

| Parameter             | STL-27L used in D800                                                                         |
| --------------------- | -------------------------------------------------------------------------------------------- |
| Ranging / scan        | DTOF;360° in one plane                                                                       |
| Range conditions      | 0.03–25 m at 80% target;0.03–10 m at 4%                                                      |
| Measurement frequency | 21600 measurements/s                                                                         |
| Rotation              | 10 Hz typical;6–13 Hz external-control range                                                 |
| Angular sampling      | 0.167° at 10 Hz                                                                              |
| Stated range bands    | ±15 mm at 0.03–2 m, STD 5 mm;±20 mm at 2–8 m, STD 15 mm;±30 mm beyond 8 m, STD 25 mm         |
| Power                 | 4.5–5.5 V,5 V nominal                                                                        |
| Current               | 290 m A typical working;540 m A typical startup in datasheet, provisional qualifier retained |
| Data                  | One-way UART,921600 baud,8 data bits,1 stop bit, no parity/flow control                      |
| Optical / light       | 905 nm typical; Class 1; up to 60 klux stated ambient-light test                             |
| Body                  | 54.00 × 46.29 × 34.80 mm                                                                     |
| Temperature           | −10 to +50 °C operating;−30 to +70 °C storage                                                |
| Protection            | IP5X dust rating in datasheet; no water-protection claim inferred                            |

[Datasheet v0.3](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Datasheet.pdf), [development manual v0.2](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf). The datasheet's final accuracy-explanation paragraph conflicts with its own band table. Preserve the stated bands rather than deriving a stricter error guarantee from that paragraph. Current figures are typical with provisional notation, not maximum supply-current limits; allow startup margin and verify the actual kit adapter/power path. The datasheet does not finalize mass, so a retailer's 45 g value is not presented as a newly verified manufacturer mass.

## Hardware and connections

### Four-pin interface and electrical revision

The manufacturer drawing shows the **ZH 1.5 T-4 P,1.5 mm connector**, with contact numbers 1–4 referenced to its illustrated front view. The figure/table were visually inspected. Do not infer numbering from the cable's rear or a different connector latch orientation.

| Pin | Signal    | Connection / boundary                                               |
| --- | --------- | ------------------------------------------------------------------- |
| 1   | TX output | Sensor data to host UART RX;3.3 V nominal logic                     |
| 2   | PWM input | Ground for internal speed regulation;3.3 V nominal external control |
| 3   | GND       | Supply and host signal reference                                    |
| 4   | P5V       | 4.5–5.5 V supply,5 V nominal                                        |

[Development manual interface](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf). Its older table gives 3.5 V TX maximum/3.3 V PWM maximum; the updated datasheet v0.3 lists 3.6 V maximum interface levels. Use the **matched kit adapter/3.3 V logic** rather than applying 5 V UART or RS232 levels. The 5 V supply rating is not a logic-input rating.

For internal regulation,**PWM must be grounded**; do not leave it floating. The development manual says 10±0.1 Hz regulation is reached within about 3 s. Optional external control uses 20–50 kHz PWM,30 kHz recommended, and a duty cycle strictly between 45% and 55% for at least 100 ms to enter external-control mode. Once entered, it remains externally controlled until power cycling. Speed then needs feedback from packet-reported angular speed; fixed duty is not a calibrated RPM command. Leave that path out of first commissioning.

### Power, mounting and frames

Use the supplied D800 adapter/cable assembly and a host USB power path that can support startup current without dropping below 4.5 V. Avoid simultaneous unrelated 5 V feeds unless the actual adapter design explicitly permits them. Keep the rotating head and optical window clear; do not restrain the mechanism or use the optical cover as a bracket contact.

The native measurement convention is **clockwise increasing angle**, zero toward the front, with origin at the rotating ranging unit. The official ROS launch supplies a demonstration `base_link`→`base_laser` transform with 0.18 m height. That is sample geometry, not a measured robot installation: replace it with the real mount transform and prevent duplicate static publishers. [Manual coordinate/kit sections](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf), [exact launch](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/launch/stl27l.launch.py).

## Software and development resources

### Choose the model-specific software <a href="#development-software-and-recovery" id="development-software-and-recovery"></a>

The manufacturer `ldlidar_stl_ros2` README explicitly lists LD06, LD19 and STL-27L and documents Ubuntu 20.04/ROS2 Foxy or later as its evaluation baseline. The exact `stl27l.launch.py` sets **`product_name:LDLiDAR_STL27L`**,921600 baud,`laser_scan_dir:false`, topic `scan`, frame `base_laser` and angle cropping disabled. Do not use the README's illustrative LD06 serial example (230400 baud) snippet for D800. [Actual STL27L launch](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/launch/stl27l.launch.py).

The older manual links the manufacturer's STL SDK/ROS1/ROS2 and Windows `LdsPointCloudViewer`. The currently reviewed ROS2 code is an exact model-support source; the separately named `ldlidar_sdk` repository should not be assumed compatible merely because it belongs to the same organization. [Manufacturer model support](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/README.md).

### Serial packet essentials

Each normal packet is 47 bytes: header `0x54`, type/count `0x2C`, speed, start angle,12 distance/intensity samples, end angle, timestamp and CRC8. Multi-byte values are little-endian; distance is mm, angles 0.01°, speed degrees/s. The 16-bit timestamp is milliseconds and wraps around 30000; it is not UTC. Interpolate angles across the 0° wrap using modular arithmetic. CRC uses polynomial 0x4D with initial 0; the original example below computes it without copying the manual's lookup table. [Manual protocol](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf).

### STL27L ROS scan geometry, crop behavior and mounting transform

The model launch publishes a standard LaserScan rather than a 3D cloud. `laser_scan_dir:false` is clockwise, true counterclockwise. The crop feature is disabled by default; when enabled, points within the inclusive **\[angle\_crop\_min, angle\_crop\_max]** interval, in degrees, have **both range and intensity set to 0**. That is masked data, not a new measured zero-distance obstacle. Record the actual crop policy before feeding the scan into a consumer that distinguishes invalid, zero and infinite range.

`port_name` must refer to the enumerated serial adapter carrying this sensor's TTL output, with **921600 baud** and exact `LDLiDAR_STL27L` product selection. `topic_name:scan` and `frame_id:base_laser` are independent of the serial device name. The stock launch also publishes **base\_link → base\_laser translation (0, 0, 0.18) m with zero rotation**. That 18 cm height is an example mounting transform, not a dimension of D800 or a calibration for the user's robot. Replace it with the measured installation or omit that example broadcaster when the robot description already supplies the transform. Two different publishers for the same transform can make a correct scan appear unstable. [Pinned STL27L launch and parameter comments](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/launch/stl27l.launch.py).

For packet-level timing, distinguish the measured motor angular speed in degrees/s from the driver publication rate. Convert speed/360 to revolutions/s and check scan angle/time increments in the actual LaserScan. A stream with a valid CRC can still have gaps after host overruns; retain packet timestamps and sample counts as well as CRC failures. The original decoder below is a transport diagnostic and does not duplicate the manufacturer's model-specific filtering/geometry implementation. Keep the actual STL27L driver for the ROS integration and compare a stationary round-trip capture before adding navigation.

### STL-27L complete serial record and scan reconstruction

The documented **47-byte STL-27L** measurement packet is independent of its D800 kit adapter. Numeric fields are little-endian. Decode the entire record only after length/header and CRC are valid. [STL-27L development manual §§3–4](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf).

| Field            | Byte offset / length | Unit / interpretation                                               |
| ---------------- | -------------------- | ------------------------------------------------------------------- |
| Header           | 0 / 1                | `0x54`                                                              |
| Version/count    | 1 / 1                | `0x2C`; low five bits give 12 samples, upper bits version/type      |
| Motor speed      | 2 / 2, u16           | Degrees/s; divide by 360 for revolutions/s                          |
| Start angle      | 4 / 2, u16           | 0.01°, first sample                                                 |
| Sample i, i=0–11 | `6+3i` / 3           | Distance u16 in mm, intensity/confidence u8 at `8+3i`               |
| End angle        | 42 / 2, u16          | 0.01°, last sample                                                  |
| Device timestamp | 44 / 2, u16          | Milliseconds, wraps at the documented 30000 ms cycle; not Unix time |
| CRC8             | 46 / 1               | Polynomial `0x4D`, initial 0, over bytes 0–45                       |

For n=12 samples, compute `span=(end−start) mod 36000` in 0.01° counts, then `angle_i=(start+i×span/11) mod 36000`. Use floating-point division if retaining sub-count interpolation; do not interpolate linearly from 359° down to 1° through 180°. Convert each associated range with `range_m=distance/1000`, retaining its own intensity byte. A zero/weak return requires the model's validity/filtering policy; CRC only establishes transport integrity. The angular span should be compatible with speed and the measurement rate, so implausibly large spans are a useful corruption/loss/version diagnostic. [Measurement analysis and example](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf).

A whole scan is assembled at a zero-angle crossing, not at an arbitrary 47-byte boundary. The inspected driver waits for a crossing from above 340° to below 20°, rejects excessive frame duration/count, optionally applies its model filter and sorts by timestamp. Initial partial frames can be discarded before the first complete scan. Preserve raw packets when evaluating that policy; changing filters changes the dataset. [Actual STL decoder and frame assembly](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/ldlidar_driver/src/dataprocess/lipkg.cpp).

**Raw sensor time and SDK point time differ.** In this pinned implementation, each `PointData.stamp` comes from the application's registered host-time callback, interpolated between successive packet-reception timestamps. The raw device millisecond counter is stored separately; it is not automatically synchronized UTC. The source's angle-step expression also performs integer division before converting to floating point, so its exact quantization can differ slightly from the full-precision expression above. A stationary CRC-valid scan does not validate moving-platform time accuracy. Avoid host-clock jumps during a timing-sensitive run and record which clock supplied point timestamps. [Timestamp/angle implementation](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/ldlidar_driver/src/dataprocess/lipkg.cpp).

### Bundled C++ driver API and Linux development scope

The model-confirmed public API is bundled in **`ldlidar_stl_ros2` at bf668a8…**, even though the older manual says a standalone SDK is obtained through FAE. It does not establish compatibility of a different repository named `ldlidar_sdk`. The bundled code is MIT-licensed with its notices and model-use scope; retain the repository license/notices when redistributing or adapting it. Its Linux serial implementation includes Linux-specific `termios` definitions, so the ROS evaluation target does not prove native macOS/Windows compilation. [Actual API header](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/ldlidar_driver/include/core/ldlidar_driver.h), [original build source](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/CMakeLists.txt).

| API                              | Arguments / result and required handling                                                                   |
| -------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| `RegisterGetTimestampFunctional` | Register `uint64_t` nanosecond clock callback **before Start**; missing callback makes initialization fail |
| `Start`                          | `LDType::STL_27L`, observed serial path, **921600**, `COMM_SERIAL_MODE`; Boolean host communication result |
| `WaitLidarCommConnect`           | Timeout in ms; waits for valid incoming communication, not a calibrated measurement                        |
| `GetLaserScanData`               | `Points2D&` or `LaserScan&`, timeout ms, default 1000; handle returned status explicitly                   |
| `GetLidarScanFreq`               | Boolean result and output double in Hz                                                                     |
| `EnableFilterAlgorithnmProcess`  | Boolean model-filter switch; exact API spelling includes `Algorithnm`                                      |
| `GetLidarSdkVersionNumber`       | Record bundled SDK version with configuration/data                                                         |
| `Stop`                           | Closes host serial/network handles; **does not establish that the separately powered motor stops**         |

`LidarStatus::NORMAL` means a new scan was returned; `DATA_WAIT` means not ready yet, `DATA_TIME_OUT` means no new scan within the requested interval, `ERROR` is the device/driver error path, and `STOP` means the host driver is not started. A wait is not an empty valid scan. `PointData` holds angle in degrees, distance in mm, intensity 0–255 and host-clock stamp in ns. Its x/y members are not a promise that every parsing path fills Cartesian coordinates; calculate them under the intended coordinate convention or use the reviewed ROS conversion. `LaserScan.stamp` is the first returned point's stamp in the implementation. The advertised `GetLidarErrorCode` line is commented out in this header, so it is not a callable public error API. [Types/statuses](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/ldlidar_driver/include/core/ldlidar_datatype.h), [actual lifecycle/status implementation](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/ldlidar_driver/src/core/ldlidar_driver.cpp).

## Getting started <a href="#getting-started" id="getting-started"></a>

### First result using the kit

1. Confirm the received sensor is STL-27L and the D800 kit includes its correct adapter/cables. With power off, connect the intact sensor cable and USB adapter. Keep PWM in the documented grounded/internal-control condition.
2. Place the sensor level with an unobstructed scan plane. Connect USB and allow rotation to stabilize. On Windows, install the adapter's correct CP210x VCP driver if required; record the actual COM port rather than assuming COM3.
3. Open the manufacturer's supporting LdsPointCloudViewer package, select the actual port and STL-27L/921600 8N1 settings. Start reception and compare a measured diffuse target's range with the planar display.
4. Save a short recording/capture in the viewer's supported format and replay it. Check clockwise/raw orientation versus the viewer's display convention before adding robot transforms.

**Expected result:** an updating 360° planar scan at about 10 Hz with reasonable target geometry. A spinning motor without valid serial packets is not a first-result pass. [Manual kit/Windows workflow](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf).

### Original CRC-checked serial receiver

On Linux, identify the adapter first with `ls -l /dev/serial/by-id/`. Use the actual stable path and appropriate serial-group access. Install pyserial in a dedicated environment if it is not available; close Viewer/ROS before opening the port. Save this original program as `stl27l_check.py` and run `python3 stl27l_check.py ACTUAL_SERIAL_PATH`:

```python
import collections
import struct
import sys
import time
import serial

def crc8(data):
    crc = 0
    for byte in data:
        crc ^= byte
        for _ in range(8):
            crc = ((crc << 1) ^ 0x4D) & 0xFF if crc & 0x80 else (crc << 1) & 0xFF
    return crc

buffer = bytearray()
counts = collections.Counter()
with serial.Serial(sys.argv[1], 921600, bytesize=8, parity="N", stopbits=1,
                   timeout=0.1, xonxoff=False, rtscts=False, dsrdtr=False) as port:
    finish = time.monotonic() + 8
    while time.monotonic() < finish:
        buffer.extend(port.read(2048))
        while True:
            start = buffer.find(b"\x54\x2c")
            if start < 0:
                buffer[:] = buffer[-1:]
                break
            del buffer[:start]
            if len(buffer) < 47:
                break
            packet = bytes(buffer[:47])
            if crc8(packet[:-1]) != packet[-1]:
                counts["bad_crc"] += 1
                del buffer[0]
                continue
            del buffer[:47]
            counts["valid"] += 1
            speed, first = struct.unpack_from("<HH", packet, 2)
            last, stamp_ms = struct.unpack_from("<HH", packet, 42)
            span = (last - first) % 36000
            ranges = [struct.unpack_from("<H", packet, 6 + 3*i)[0] / 1000
                      for i in range(12)]
            if counts["valid"] == 1 or counts["valid"] % 1000 == 0:
                print("valid", counts["valid"], "rotation Hz", round(speed / 360, 3),
                      "start deg", first / 100, "span deg", span / 100,
                      "first range m", ranges[0], "device ms", stamp_ms)
print(dict(counts))
if not counts["valid"]:
    raise SystemExit("No CRC-valid frames: check port, 921600 baud, power and TX wiring")
```

**Expected result:** CRC-valid counts increase, reported rotation approaches 10 Hz in internal mode, and ranges are printed in meters. The program sends no sensor commands and does not drive PWM. Zero distance/intensity or weak returns need scene interpretation; this transport check does not certify accuracy or external timing.

### ROS2 Foxy first scan

Use the documented Ubuntu 20.04/Foxy environment with colcon, ROS sensor/tf/RViz dependencies and compiler. On the actual Linux USB adapter, grant access through the host's appropriate serial group or reviewed udev rule, then reconnect/log in as required. The README's blanket `chmod777` is not needed as a persistent integration design.

```bash
mkdir -p ~/d800_ws/src
cd ~/d800_ws/src
git clone https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2.git
cd ldlidar_stl_ros2
git checkout bf668a89baf722a787dadc442860dcbf33a82f5a
```

Edit `launch/stl27l.launch.py` to the observed `port_name`; retain `LDLiDAR_STL27L` and 921600. Review/replace the 0.18 m demonstration static transform with the measured mount, or use only one correct existing robot TF publisher. Then:

```bash
cd ~/d800_ws
source /opt/ros/foxy/setup.bash
colcon build
source install/setup.bash
ros2 launch ldlidar_stl_ros2 viewer_stl27l.launch.py
```

In a second sourced terminal, use `ros2 topic hz /scan` and `ros2 topic echo /scan --once --field header`. **Expected result:** `sensor_msgs/msg/LaserScan` in `base_laser`, approximately 10 Hz, and correct scene orientation. Verify actual scan direction and TF before feeding SLAM; the launch's direction flag is a software convention, not a new motor-direction specification. [Driver and viewer launch](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/README.md).

### Original non-ROS STL-27L read-scan example

Use Linux with a C++14 compiler, CMake and pthread support, the exact pinned public source already obtained above, the matched TTL/USB adapter and observed serial path. **The sensor rotates while powered in internal mode; keep the head clear and PWM correctly grounded.** This program opens the host receiver and reads scans; it sends no motor/PWM command. Its timestamp callback deliberately uses a monotonic host clock with an unspecified epoch, not UTC or ROS wall time.

Save as `stl27l_read.cpp`:

```cpp
#include "ldlidar_driver.h"
#include <chrono>
#include <cstdint>
#include <iostream>
#include <thread>

static uint64_t monotonic_ns() {
  return static_cast<uint64_t>(std::chrono::duration_cast<std::chrono::nanoseconds>(
      std::chrono::steady_clock::now().time_since_epoch()).count());
}

int main(int argc, char** argv) {
  if (argc != 2) { std::cerr << "Usage: stl27l_read ACTUAL_SERIAL_PATH\n"; return 2; }
  ldlidar::LDLidarDriver driver;
  driver.RegisterGetTimestampFunctional(monotonic_ns);
  driver.EnableFilterAlgorithnmProcess(true);
  if (!driver.Start(ldlidar::LDType::STL_27L, argv[1], 921600,
                    ldlidar::COMM_SERIAL_MODE)) return 3;
  if (!driver.WaitLidarCommConnect(3000)) {
    driver.Stop();
    std::cerr << "No valid communication within 3000 ms\n";
    return 4;
  }
  const auto end = std::chrono::steady_clock::now() + std::chrono::seconds(8);
  unsigned scans = 0;
  while (std::chrono::steady_clock::now() < end) {
    ldlidar::Points2D points;
    auto status = driver.GetLaserScanData(points, 1000);
    if (status == ldlidar::LidarStatus::NORMAL) {
      ++scans;
      double hz = 0;
      bool have_hz = driver.GetLidarScanFreq(hz);
      std::cout << "scan=" << scans << " points=" << points.size();
      if (have_hz) std::cout << " rotation_hz=" << hz;
      if (!points.empty())
        std::cout << " first_angle_deg=" << points.front().angle
                  << " range_m=" << points.front().distance / 1000.0
                  << " host_monotonic_ns=" << points.front().stamp;
      std::cout << '\n';
    } else if (status != ldlidar::LidarStatus::DATA_WAIT) {
      std::cerr << "driver status=" << static_cast<int>(status) << '\n';
      break;
    }
    std::this_thread::sleep_for(std::chrono::milliseconds(1));
  }
  driver.Stop();
  return scans ? 0 : 5;
}
```

In the same project directory, the following original CMake file builds the **same six bundled driver-source groups** used by the official package, with no ROS wrapper or installation step:

```cmake
cmake_minimum_required(VERSION 3.5)
project(stl27l_read LANGUAGES CXX)
if(NOT CMAKE_SYSTEM_NAME STREQUAL "Linux")
  message(FATAL_ERROR "This driver uses Linux serial headers")
endif()
set(CMAKE_CXX_STANDARD 14)
set(CMAKE_CXX_STANDARD_REQUIRED ON)
set(D800_DRIVER_ROOT "" CACHE PATH "Pinned checkout's ldlidar_driver directory")
if(NOT EXISTS "${D800_DRIVER_ROOT}/include/core/ldlidar_driver.h")
  message(FATAL_ERROR "Set D800_DRIVER_ROOT to the actual bundled driver")
endif()
add_executable(stl27l_read stl27l_read.cpp)
foreach(group core dataprocess filter logger networkcom serialcom)
  target_include_directories(stl27l_read PRIVATE "${D800_DRIVER_ROOT}/include/${group}")
  file(GLOB group_sources "${D800_DRIVER_ROOT}/src/${group}/*.cpp")
  target_sources(stl27l_read PRIVATE ${group_sources})
endforeach()
target_link_libraries(stl27l_read PRIVATE pthread)
```

1. Save that file as `CMakeLists.txt`. Set `D800_DRIVER_PATH` to the actual `ldlidar_driver` directory inside the pinned checkout; do not point it at an unrelated standalone SDK.
2. Build locally and start the finite receiver, using the actual enumerated serial device and normal reviewed serial-group permissions:

```bash
cmake -S . -B build -DD800_DRIVER_ROOT="$D800_DRIVER_PATH"
cmake --build build --parallel 2
./build/stl27l_read ACTUAL_SERIAL_PATH
```

3. Compare reported rotation, complete-scan point counts and a known static target with the earlier CRC receiver. Record filter setting and the monotonic-clock timestamp convention with the output.

**Expected result:** increasing scan numbers with nonempty scans and rotation near 10 Hz after stabilization. DATA\_WAIT can occur between complete scans; timeout/no scans calls for power/baud/path/CRC diagnosis. Closing the receiver releases the host port; isolate sensor power separately before touching the head. This example and build configuration are source reviewed; Linux linking/execution and hardware tests are not run. The public code has Linux-only headers, so local macOS checks do not establish a Linux build result. [Bundled source/build groups](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/CMakeLists.txt).

## Troubleshooting and FAQs

### FAQs <a href="#faqs" id="faqs"></a>

| Symptom                             | Checks and supported recovery                                                                     |
| ----------------------------------- | ------------------------------------------------------------------------------------------------- |
| Motor does not stabilize            | Power at 4.5–5.5 V, startup allowance, PWM grounded, rotation free                                |
| Motor turns, no serial frames       | Actual port,921600 8N1, sensor TX to host RX, ground and supporting adapter                       |
| Many CRC failures                   | Cable/ground quality, correct logic—not RS232/5 V—and only one port owner                         |
| Large angular jump near 0°          | Use modular interpolation of start/end angles; do not subtract without wrap                       |
| Timestamp jumps every 30 s          | Expected device-ms counter wrap, not UTC reset; maintain host timing policy separately            |
| ROS scan mirrored/rotated           | Exact STL27L direction flag, native clockwise convention and real mount TF                        |
| Speed remains externally controlled | PWM entry is latched until power cycle; remove external control and restore ground before restart |

**Is the D800 kit the same as a bare STL-27L purchase?** The sensor is the same listed platform; D800 adds USB adapter/cables. The actual received accessories still require inspection.

**Does“glass detection”make all transparent obstacles visible?** No. The data sheet states a narrow incidence condition; evaluate actual materials and geometry.

Remove loose contamination before gentle optical cleaning, and keep the rotating/optical assembly unobstructed. No writable UART command or field-flashing procedure is established by this one-way protocol. Do not send another model's motor/firmware commands. Use manufacturer support for persistent fault recovery and preserve valid/raw captures. [Datasheet/manual](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf).

### Windows viewer counters and reproducible data checks

Use the manufacturer's [LdsPointCloudViewer release page](https://github.com/ldrobotSensorTeam/ld_desktop_tool/releases) linked by the manual. Select the actual CP210x adapter's COM port, exact STL-27L model and 921600-baud path before starting display. The evaluation tool reports **Speed** in Hz, **Rate** as its packet-resolution/reception indicator and **Valid** as valid points per revolution. Compare them together: a stable motor-speed display does not prove complete serial reception, and a high valid-point count does not prove absolute range accuracy. Save the exact tool/model settings and retain raw packets for repeatable analysis. [Development-kit instructions §5.1](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf).

For recovery, close the other program owning the serial port, check sensor-terminal 5 V supply and common reference, verify 921600 8N1 and the exact product selector, then inspect CRC-valid raw frames. Reconnect/restart the host receiver only after the electrical/port checks. Repeated power cycles also reset the latched external-PWM mode to internal regulation, but they are not a substitute for a correctly grounded internal-control PWM input. Clean/protect the optical cover using the received model's care instructions and prevent liquids from entering the USB/TTL adapter; the sensor's protection claim does not automatically cover the evaluation electronics. No unsupported optical solvent or firmware/recovery command is prescribed.

## Downloads and technical documents

| Resource                                                                                                                                  | Purpose                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| [STL-27L development manual v0.2](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf)            | 19-page manufacturer-authored PDF, hosted by its distributor; pinout, UART, CRC, coordinates and kit workflows |
| [STL-27L datasheet v0.3](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Datasheet.pdf)                              | 10-page manufacturer-authored PDF; range conditions, electrical updates, dimensions and limits                 |
| [Official STL ROS2 source](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/README.md) | Exact model support and launch                                                                                 |
| [LDROBOT desktop release v3.0.5](https://github.com/ldrobotSensorTeam/ld_desktop_tool/releases/tag/v3.0.5)                                | Viewer/adapter evaluation resources                                                                            |
| [Silicon Labs VCP driver](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)                                               | CP210x host driver when matched to adapter                                                                     |

The store-linked Waveshare integration page returned 403 during review; the manufacturer-authored manuals above and actual LDROBOT driver provide the verified technical path. Their provenance is explicit rather than presenting a distributor mirror as an LDROBOT doc-center URL.

## References and validation

### Sources and validation <a href="#sources-and-validation" id="sources-and-validation"></a>

Reviewed 24 November 2026: exact D800 kit-versus-sensor catalog selection, full manufacturer-authored STL-27L datasheet/development manuals and actual manufacturer STL27L ROS2 launch/decoder. Electrical revision differences, provisional typical current and accuracy-wording conflict are bounded explicitly.

**ROS build, viewer/serial receiver execution, PWM driving, firmware changes and physical power/range/motion tests: not run.** The CRC receiver is original and syntax checked; its expected results are instructions, not reported bench measurements.

* [Manufacturer STL27L development manual, distributor-hosted PDF](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Development_Manual.pdf) — v0.2 Aug 2022; 19 pages.
* [Manufacturer STL27L datasheet, distributor-hosted PDF](https://raw.githubusercontent.com/May-DFRobot/DFRobot/master/SEN0589_Datasheet.pdf) — v0.3 Oct 2022; 10 pages.
* [LDROBOT STL27L ROS2 supported models](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/README.md) — commit bf668a89baf722a787dadc442860dcbf33a82f5a.
* [STL27L exact baud/model/direction/demo TF](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/launch/stl27l.launch.py) — commit bf668a89baf722a787dadc442860dcbf33a82f5a.
* [LDROBOT STL parser/CRC processing](https://github.com/ldrobotSensorTeam/ldlidar_stl_ros2/blob/bf668a89baf722a787dadc442860dcbf33a82f5a/ldlidar_driver/src/dataprocess/lipkg.cpp) — commit bf668a89baf722a787dadc442860dcbf33a82f5a.
* [Exact D800 kit versus STL27L sensor](https://openelab.io/products/ldrobot-d800-dtof-lidar-kit) — 23 Nov catalog plus observed public page 24 Nov.

### Additional established references

* [Manufacturer STL-27L sensor catalogue](https://www.ldrobot.com/sensors)
* [Official generic SDK support table](https://github.com/ldrobotSensorTeam/ldlidar_sdk)
